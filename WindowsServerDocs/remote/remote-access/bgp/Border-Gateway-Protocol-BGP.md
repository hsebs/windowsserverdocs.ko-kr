---
title: BGP(경계 게이트웨이 프로토콜)
description: 이 항목을 사용 하 여 BGP 지원 배포 토폴로지 및 BGP 기능 및 기능을 포함 하 여 Windows Server 2016의 BGP (Border Gateway Protocol)를 이해할 수 있습니다.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78cc2ce3-a48e-45db-b402-e480b493fab1
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 3e04c732cbacb182731717215a4cf99cf3cc1f76
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309298"
---
# <a name="border-gateway-protocol-bgp"></a>BGP(경계 게이트웨이 프로토콜)

>적용 대상: Windows Server(반기 채널), Windows Server 2016

이 항목을 통해 지원 배포 토폴로지와 BGP 기능 및 특성을 포함하여 BGP(경계 게이트웨이 프로토콜)에 대해 이해할 수 있습니다.  
  
> [!NOTE]  
> 이 항목 외에 다음 BGP 설명서를 사용할 수 있습니다.  
>   
> -   [BGP Windows PowerShell 명령 참조](../../remote-access/bgp/BGP-Windows-PowerShell-Command-Reference.md)  
  
이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
-   [BGP 지원 배포 토폴로지](#bkmk_top)  
  
-   [BGP 기능](#bkmk_features)  
  
Windows Server 2016 원격 액세스 서비스에 구성 된 경우 \(RAS\) 다중 테 넌 트 모드로 게이트웨이 프로토콜 BGP (Border Gateway) 기능을 제공 된 테 넌 트의 VM 네트워크와 해당 원격 사이트 간의 네트워크 트래픽 라우팅을 관리할 수 있습니다. 단일 테 넌 트 RAS 게이트웨이 배포 하 고 로컬 영역 네트워크로 원격 액세스를 배포 하는 경우 BGP를 사용할 수도 있습니다 \(LAN\) 라우터 합니다.  
  
BGP는 동적 라우팅 프로토콜이기 때문에 라우터에서 수동으로 경로를 구성할 필요성이 줄어들고 사이트 간 VPN 연결을 사용하여 연결된 사이트 간 경로를 자동으로 알아냅니다.  
  
BGP 경로 사용 하려면 설치 해야는 **원격 액세스 서비스 \(RAS\)** 및/또는 **라우팅** 컴퓨터 또는 가상 컴퓨터에 원격 액세스 서버 역할의 역할 서비스 \(VM\) -사용 하면 시스템의 종류는 다중 테 넌 트 배포 보유 여부에 따라 달라 집니다.  
  
-   다중 테 넌 트 배포에 대 한 하나 이상의 Vm에 RAS 게이트웨이 설치 하는 것이 좋습니다. 사용 하 여 여러 Vm의 고가용성을 제공 합니다. RAS 게이트웨이 여러 테 넌 트의 여러 연결을 처리할 수 하 고 Hyper-v 호스트 및 실제로 게이트웨이로 구성 된 VM을 구성 합니다. Exchange 테 넌 트 및 클라우드 서비스 공급자에는 다중 테 넌 트 BGP 라우터이 게이트웨이가 사이트 간 VPN 연결을 사용 하도록 구성 된 \(CSP\) 서브넷 경로입니다.  
  
-   단일 테 넌 트 가장자리 게이트웨이 배포 또는 LAN 라우터 배포에 대 한 물리적 컴퓨터 또는 VM에서 RAS 게이트웨이 설치할 수 있습니다.  
  
> [!IMPORTANT]  
> RAS 게이트웨이 설치 하는 경우 BGP를 사용 하 여 각 테 넌 트에 대 한 사용 되는지 여부를 지정 해야는 **사용 RemoteAccessRoutingDomain** 으로 Windows PowerShell 명령을 **형식** 매개 변수 값의 **모든**합니다. 원격 액세스 다중 테 넌 트 기능 없이 BGP 사용이 가능한 LAN 라우터를 설치 하려면 명령을 사용할 수 있습니다 **설치-원격 액세스-함 RoutingOnly**합니다.  
>   
> 다음 예제 코드에 RAS 모든 RAS 기능을 사용 하 여 다중 모드에서 설치 하는 방법을 보여 줍니다 (지점-사이트 VPN, 사이트 간 VPN 및 BGP 라우팅) 두 명의 테 넌 트를 Contoso 및 Fabrikam에 사용할 수 있습니다.  
  
```  
$Contoso_RoutingDomain = "ContosoTenant"  
$Fabrikam_RoutingDomain = "FabrikamTenant"  
  
Install-RemoteAccess -MultiTenancy  
  
Enable-RemoteAccessRoutingDomain -Name $Contoso_RoutingDomain -Type All -PassThru  
Enable-RemoteAccessRoutingDomain -Name $Fabrikam_RoutingDomain -Type All -PassThru  
```  
  
## <a name="bgp-supported-deployment-topologies"></a><a name="bkmk_top"></a>BGP 지원 배포 토폴로지  
아래에는 엔터프라이즈 사이트가 CSP(클라우드 서비스 공급자) 데이터 센터에 연결되는 지원 배포 토폴로지가 나열되어 있습니다.  
  
모든 시나리오에서 CSP 게이트웨이 가장자리에는 Windows Server 2016 RAS 게이트웨이입니다. 여러 테 넌 트의 여러 연결을 처리할 수 있는 RAS 게이트웨이 Hyper-v 호스트 및 실제로 게이트웨이로 구성 된 VM으로 구성 됩니다. 이 에지 게이트웨이를 사이트 간 VPN 연결을 통해 다중 테넌트 BGP 라우터로 구성하여 엔터프라이즈 및 CSP 서브넷 경로를 교환합니다.  
  
테넌트는 S2S(사이트 간) VPN 연결을 사용하여 CSP 데이터 센터의 해당 리소스에 연결됩니다. 또한 BGP 라우팅 프로토콜이 엔터프라이즈 및 CSP 게이트웨이 간의 동적 라우팅 정보 교환을 위해 배포됩니다.  
  
다음 배포 토폴로지를 지원합니다.  
  
-   [엔터프라이즈 사이트에 지에서 BGP를 사용 하는 RAS VPN 사이트 간 게이트웨이](#bkmk_top1)  
  
-   [엔터프라이즈 사이트에 지에서 BGP를 사용 하는 타사 게이트웨이](#bkmk_top2)  
  
-   [타사 게이트웨이를 사용 하는 여러 엔터프라이즈 사이트](#bkmk_top3)  
  
-   [BGP 및 VPN에 대 한 별도의 종료 위치](#bkmk_top4)  
  
다음 섹션에는 각 BGP 지원 토폴로지에 대한 추가 정보가 포함되어 있습니다.  
  
### <a name="ras-vpn-site-to-site-gateway-with-bgp-at-enterprise-site-edge"></a><a name="bkmk_top1"></a>엔터프라이즈 사이트에 지에서 BGP를 사용 하는 RAS VPN 사이트 간 게이트웨이  
이 토폴로지는 CSP에 연결된 엔터프라이즈 사이트를 보여 줍니다. Windows Server 2016 RAS 게이트웨이 CSP와에 지 방화벽 디바이스 VPN 사이트 간 연결에 대해 구성, 엔터프라이즈 라우팅 토폴로지는 내부 라우터를 포함 됩니다. RAS 게이트웨이 S2S VPN 및 BGP 연결을 종료합니다.  
  
![RAS VPN 사이트 간 게이트웨이](../../media/Border-Gateway-Protocol-BGP/bgp_01.jpg)  
  
두 사이트는 별도의 AS(자치 시스템)의 BGP 사용 라우터 간에 정보를 전송할 수 있는 eBGP(External Border Gateway Protocol)를 사용하여 연결됩니다. 이렇게 하려면 엔터프라이즈와 CSP 둘 다 고유한 ASN(자치 시스템 번호)이 있어야 하는데 이는 BGP 프로토콜에 필수적인 매개 변수입니다.  
  
이 시나리오에서는 BGP가 다음과 같은 방식으로 작동합니다.  
  
-   엔터프라이즈 사이트 에지 디바이스는 BGP를 사용하여 클라우드에 호스트된 가상화된 서브넷 경로(10.2.1.0/24)를 알아냅니다. 또한이 디바이스는 온-프레미스 서브넷에 대 한 경로가 (10.1.1.0/24) CSP RAS 테 넌 트 게이트웨이 알립니다.  
  
-   고객 에지 라우터가 다음 메커니즘 중 하나를 통해 온-프레미스 내부 경로를 알아냅니다.  
  
    -   에지 디바이스가 내부 라우터를 사용하여 BGP를 실행하고 내부 경로를 알아냅니다(이 경우, 10.1.1.0/24). 한편 내부 라우터가 에지 디바이스에서 외부 경로(예: 10.2.1.0/24)를 알아내면 내부 라우터는 OSPF(최단 경로 우선 프로토콜) 또는 RIP(Routing Information Protocol) 같은 IGP(내부 게이트웨이 프로토콜)를 사용하여 이러한 경로를 다른 온-프레미스 라우터에 배포해야 합니다.  
  
    -   에지 디바이스는 BGP를 사용하여 알림 경로를 선택하도록 고정 경로 또는 인터페이스로 구성될 수 있습니다. 또한 에지 디바이스는 IGP를 사용하여 외부 경로를 다른 온-프레미스 라우터에 배포합니다.  
  
### <a name="third-party-gateway-with-bgp-at-enterprise-site-edge"></a><a name="bkmk_top2"></a>엔터프라이즈 사이트에 지에서 BGP를 사용 하는 타사 게이트웨이  
이 토폴로지는 타사 에지 라우터를 사용하여 CSP에 연결하는 엔터프라이즈 사이트를 보여 줍니다. 에지 라우터는 사이트 간 VPN 게이트웨이 역할도 합니다.  
  
![엔터프라이즈 사이트 에지에서 BGP를 사용하는 타사 게이트웨이](../../media/Border-Gateway-Protocol-BGP/bgp_02.jpg)  
  
엔터프라이즈 에지 라우터가 다음 메커니즘 중 하나를 통해 온-프레미스 내부 경로를 알아냅니다.  
  
-   에지 디바이스가 내부 라우터를 사용하여 BGP를 실행하고 내부 경로를 알아냅니다(이 경우, 10.1.1.0/24).  
  
-   에지 디바이스가 IGP(내부 게이트웨이 프로토콜)를 구현하고 내부 라우팅에 직접 참여합니다.  
  
### <a name="multiple-enterprise-sites-connecting-to-csp-cloud-datacenter"></a><a name="bkmk_top3"></a>CSP 클라우드 데이터 센터에 연결 하는 여러 엔터프라이즈 사이트  
이 토폴로지는 타사 게이트웨이를 사용하여 CSP에 연결하는 다중 엔터프라이즈 사이트를 보여 줍니다. 타사 에지 디바이스는 사이트 간 VPN 게이트웨이 및 BGP 라우터 역할을 합니다.  
  
![CSP를 연결 하는 여러 개의 엔터프라이즈 사이트 데이터 센터를 클라우드](../../media/Border-Gateway-Protocol-BGP/bgp_03.jpg)  
  
고객 에지 라우터는 다음 메커니즘 중 하나를 통해 온-프레미스 내부 경로를 알아냅니다.  
  
-   에지 디바이스가 내부 라우터를 사용하여 BGP를 실행하고 내부 경로를 알아냅니다(이 경우, 10.1.1.0/24).  
  
-   에지 디바이스가 IGP(내부 게이트웨이 프로토콜)를 구현하고 내부 라우팅에 직접 참여합니다.  
  
각 엔터프라이즈 사이트는 직접 eBGP를 연결하여 다른 사이트에서 경로를 알아냅니다.  
  
각 엔터프라이즈 사이트는 직접 및 다른 엔터프라이즈 사이트를 사용하여 호스트된 네트워크 경로를 알아내지만 경로의 비용에 따라 최적의 경로를 선택합니다.  
  
엔터프라이즈 사이트 1의 BGP 라우터 수 없는 경우 엔터프라이즈 사이트 2 BGP 라우터 연결에 실패 했기 때문에, 사이트 1 BGP 라우터는 동적으로 CSP BGP 라우터에서 사이트 2 엔터프라이즈 네트워크에 경로 알아보려면 시작 하 고 트래픽을 CSP의 Windows Server BGP 라우터를 통해 사이트 2로 변경 사이트 1에서 원활 하 게 됩니다.  
  
### <a name="separate-termination-points-for-bgp-and-vpn"></a><a name="bkmk_top4"></a>BGP 및 VPN에 대 한 별도의 종료 위치  
이 토폴로지는 두 개의 서로 다른 라우터를 BGP 및 사이트 간 VPN 엔드포인트으로 사용하는 엔터프라이즈를 보여 줍니다. BGP는 내부 라우터에서 종료 되는 동안 Windows Server 2016 RAS 게이트웨이에서 사이트 간 VPN은 종료 됩니다. 연결 CSP 측면에 CSP RAS 게이트웨이에 BGP와 VPN 연결을 종료합니다. 이 구성에서 내부 타사 라우터 하드웨어는 IGP 경로를 BGP에 재배포하는 것뿐만 아니라 BGP 경로를 IGP에 재배포하는 것도 지원해야 합니다.  
  
![BGP 및 VPN에 대한 별도의 종료 지점](../../media/Border-Gateway-Protocol-BGP/bgp_04.jpg)  
  
내부 라우터는 다음 메커니즘 중 하나를 통해 엔터프라이즈 경로를 알아냅니다.  
  
-   BGP  
  
-   OSPF 또는 RIP와 같은 IGP(내부 게이트웨이 프로토콜)  
  
-   고정 경로 구성  
  
IGP가 엔터프라이즈 사이트에서 사용되는 경우 내부 라우터는 CSP 가상 네트워크 및 로컬 엔터프라이즈 서브넷 간의 서브넷 연결을 유지하기 위해 IGP 경로를 BGP에 재배포해야 할 뿐만 아니라 BGP 경로를 IGP 경로에 재배포해야 합니다.  
  
이 배포와 엔터프라이즈 RAS 게이트웨이 CSP 게이트웨이로 경로 가진 엔터프라이즈 RAS 게이트웨이 제공 하는 CSP RAS 게이트웨이 사이트 간 VPN 연결을가지고 있습니다. 그런 다음 기업 내부 라우터 iBGP 엔터프라이즈 RAS 게이트웨이를 사용 하 여이 경로 CSP 게이트웨이를 알아냅니다. 이 때문에 기업 내부 라우터는 다음 CSP RAS 게이트웨이 BGP 라우터와 피어 링 세션을 설정할 수 있습니다.  
  
이 지점에서 엔터프라이즈 내부 라우터 및 CSP RAS 게이트웨이 라우팅 정보를 교환 합니다. 및 엔터프라이즈 RAS BGP 라우터를 물리적으로 네트워크 사이 패킷을 라우팅할 엔터프라이즈 경로 및 CSP 경로 학습 합니다.  
  
## <a name="bgp-features"></a><a name="bkmk_features"></a>BGP 기능  
RAS 게이트웨이 BGP 라우터의 기능은 다음과가 같습니다.  
  
**원격 액세스 역할 서비스와 BGP 라우팅**합니다. 이제 설치할 수는 **라우팅** 설치 하지 않고 원격 액세스 서버 역할의 역할 서비스는 **원격 액세스 서비스 (RAS)** BGP LAN 라우터 원격 액세스를 사용 하려는 경우 역할 서비스.  BGP 라우터 메모리 사용 공간이 줄어들고만 BGP 동적 라우팅에 필요한 구성 요소를 설치 합니다. 라우팅 역할 서비스는 BGP 라우터 VM이 필요한 경우에 DirectAccess 또는 VPN을 사용 하 여 필요 하지 않을 때 유용 합니다. 또한 원격 액세스를 사용 하 여 BGP 사용 하 여 LAN 라우터를 사용 하면 BGP의 내부 네트워크에서 동적 라우팅 장점은 있습니다.  
  
**BGP 통계(메시지 카운터, 경로 카운터)** . BGP 라우터는 필요한 경우 **Get BgpStatistics** Windows PowerShell 명령을 사용하여 메시지 및 경로 통계 표시를 지원합니다.  
  
**ECMP(Equal Cost Multi Path Routing) 지원**. BGP 라우터는 ECMP를 지원하므로 BGP 라우팅 테이블 및 스택으로 배관된 둘 이상의 같은 비용 경로를 가질 수 있습니다. ECMP를 사용하도록 설정된 상태에서 데이터 패킷 전송을 위한 BGP 라우터의 경로 선택은 임의적입니다.  
  
**HoldTime 구성**. BGP 라우터는 네트워크 요구 사항에 따라 HoldTimer 값의 구성을 지원합니다. 이 타이머는 타사 디바이스와 상호 운용성을 조정하거나 BGP 피어링 세션 시간 제한에 맞게 특정한 최대 시간을 유지하기 위해 동적으로 변경될 수 있습니다.  
  
**내부 BGP 및 외부 BGP 지원**. BGP 라우터는 iBGP 및 eBGP 피어링을 지원합니다. 어느 것을 구성하든지 적절한 ASN이 로컬 및 원격 BGP 라우터에 할당되도록 해야 합니다. 네 가지 BGP 배포 토폴로지 모두 eBGP 피어링을 사용하고 네 번째 토폴로지는 iBGP 피어링도 사용합니다.  
  
**타사 솔루션과의 상호 운용성**. BGP 라우터는 최신 BGP 버전 4 사양을 기반으로 하며 대부분의 주요 타사 BGP 라우팅 디바이스와의 상호 운용성에 대해 테스트되었습니다. 자세한 내용은 RFC(Request for Comments) 4271, [BGP-4(경계 게이트웨이 프로토콜 4)](https://tools.ietf.org/html/rfc4271)를 참조하세요.  
  
**IPv4 및 IPv6 전송 피어링 지원**. BGP 라우터는 IPv4 및 IPv6 피어링 둘 다 지원합니다. 그러나 BGP 라우터의 IPv4 주소로 BGP 식별자를 구성해야 합니다. 모든 BGP 라우터 배포 토폴로지에 대해 두 피어링 형식(IPV4/IPv6) 중 하나를 사용할 수 있습니다.  
  
**IPv4 및 IPv6 유니캐스트 경로 학습 및 알림 기능(멀티 프로토콜 네트워크 계층 연결 가능성 정보 [NLRI])** . 어떤 전송을 사용하든지 세션을 설정하는 동안 다른 BGP 라우터에서 적절한 기능이 알려지면 BGP 라우터는 IPv4 및 IPv6 경로를 교환할 수 있습니다. IPv6 라우팅을 구성하려면 매개 변수 IPv6Routing을 사용하도록 설정해야 하고 로컬 전역 IPv6 주소를 라우터 수준에서 구성해야 합니다.  
  
**혼합 모드 및 수동 모드 피어링**. 들어오는 요청에 응답 하지만 여기서 BGP 라우터 및 역할을 초기자 응답자--두 혼합된 모드 또는 passive 모드, 여기서 BGP 라우터는 피어 링을 시작 하지 않고에서 BGP 피어 링 세션을 구성할 수 있습니다. 혼합 모드가 기본값이며 BGP 피어링에 권장됩니다. 디버깅 또는 진단 목적으로 수동 모드를 사용하려 하지 않는다면 혼합 모드를 사용하는 것이 좋습니다. 모든 BGP 라우터 배포 토폴로지에서 오류 이벤트가 발생하는 경우 자동으로 다시 시작하게 하려면 혼합 모드 피어링이 필요합니다.  
  
**경로 특성 재작성 기능**. BGP 라우팅 정책(다음 홉, MED, Local-Pref 및 커뮤니티)을 사용하여 BGP 라우터 수신 및 송신 경로 알림에서 다음 특성을 추가, 수정 또는 제거할 수 있습니다.  
  
**경로 필터링**. BGP 라우터는 접두사, ASN 범위, 커뮤니티 및 다음 홉 같은 다중 경로 특성에 따라 필터링 수신 또는 송신 경로 알림을 지원합니다.  
  
**경로 Reflector (RR) 및 RR 클라이언트**합니다. BGP 라우터 경로-Reflector 및 RR 클라이언트 역할도 할 수 있습니다. 복잡 한 토폴로지 RR RR 클러스터를 형성 하 여 네트워크를 단순화할 수에 유용 합니다.  
  
**경로-새로 고침 지원**. BGP 라우터는 경로-새로 고침을 지원하고 기본적으로 이 기능을 피어링에 알립니다. 경로-새로 고침을 피어에 대 한 라우팅 정책 변경 내용과 비슷한 이벤트의 라우팅 테이블에 맞게 업데이트를 보낼 수 있을 뿐만 아니라 경로 새로 고침 메시지를 통해 피어를 요청할 때 경로 업데이트의 새로운 집합을 전송 수는 있습니다. 이 통해 변경 하거나는 피어 링을 다시 시작할 필요 없이 Windows Server 2016의 BGP 라우팅 정책을 업데이트 하는 시나리오입니다.  
  
**고정 경로 구성 지원**. **Add-BgpCustomRoute** Windows PowerShell 명령을 사용하여 BGP 라우터에서 고정 경로 또는 인터페이스를 구성할 수 있습니다. 구성하는 고정 경로는 경로를 선택해야 하는 인터페이스의 접두사 또는 이름이 될 수 있습니다. 그러나 확인이 가능한 다음 홉을 가진 경로만 BGP 라우팅 테이블로 배관되고 피어에 알려집니다.  
  
**전송 라우팅 지원**. BGP 라우터 전송 iBGP 연결에 iBGP, eBGP 연결에 iBGP 물론 eBGP eBGP 연결에 대 한 라우팅을 지원 합니다.  
  
**플랩이 빨라져 라우팅할**합니다. Windows Server 2016에서 BGP 라우팅 경로 플랩이 빨라져 플랩이 빨라져 경로 대 한 지원을 제공합니다. 예를 들어 때 경로 지속적으로 알려 졌는 있으며 인출한, 떨어지거나, 라우팅 테이블을 만드는 구성할 수 있습니다 하는 경로에 감소 가중치를 할당 하 고 플랩을-에 대 한 모니터링 적절 하 게 표시 하지 않는 BGP 라우터 또는 취소-필요에 따라 표시 합니다. 그러면 안정적인 라우팅 테이블을 유지 관리 인력과 BGP 라우터에 의해 처리 됩니다.  
  
**집계 경로**합니다. 경로 집계 BGP 라우터를 더 세밀 하 게 경로 알림을 피어에 대 한 요약 또는 집계 라우팅을 바꾸려면 집계 경로 구성 하는 기능을 제공 합니다. 이 인해 더 적은 네트워크에서 전송 되는 알림 메시지를 라우팅할 수 있습니다.  
  
> [!NOTE]  
> System Center RAS 게이트웨이 Windows Server 게이트웨이 이름이 됩니다.  
  

  

