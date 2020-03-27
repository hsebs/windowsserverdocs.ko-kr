---
title: RAS 게이트웨이 배포 아키텍처
description: 이 항목을 사용 하 여 RAS 게이트웨이 풀, 반영자 라우팅, 개별 테 넌 트에 대해 여러 게이트웨이 배포를 비롯 하 여 Windows Server 2016에 RAS 게이트웨이의 RAS 게이트웨이를 배포 하는 방법을 알아볼 수 있습니다.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d46e4e91-ece0-41da-a812-af8ab153edc4
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 91d8081261d3cbc5e2da61cc2b5a9737e76a0dc7
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309801"
---
# <a name="ras-gateway-deployment-architecture"></a>RAS 게이트웨이 배포 아키텍처

>적용 대상: Windows Server(반기 채널), Windows Server 2016

이 항목을 사용 하 여 RAS 게이트웨이 풀을 비롯 한 RAS 게이트웨이의 CSP (클라우드 서비스 공급자) 배포에 대해 알아보고, 반영자을 라우팅하고, 개별 테 넌 트에 대해 여러 게이트웨이를 배포할 수 있습니다.  
  
다음 섹션에서는 게이트웨이 배포 디자인에서 이러한 기능을 사용 하는 방법을 이해할 수 있도록 몇 가지 RAS Gateway 새 기능에 대 한 간략 한 개요를 제공 합니다.  
  
또한 새 테 넌 트 추가 프로세스, 경로 동기화 및 데이터 평면 라우팅, 게이트웨이 및 경로 리플렉터 장애 조치 (failover) 등의 정보를 포함 하는 배포 예가 제공 됩니다.  
  
이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
-   [RAS 게이트웨이 새 기능을 사용 하 여 배포 디자인](#bkmk_new)  
  
-   [배포 예](#bkmk_example)  
  
-   [새 테 넌 트 및 CA (고객 주소) 공간 EBGP 피어 링 추가](#bkmk_tenant)  
  
-   [경로 동기화 및 데이터 평면 라우팅](#bkmk_route)  
  
-   [네트워크 컨트롤러가 RAS 게이트웨이 및 경로 리플렉터 장애 조치 (Failover)에 응답 하는 방법](#bkmk_failover)  
  
-   [새 RAS 게이트웨이 기능 사용의 이점](#bkmk_advantages)  
  
## <a name="using-ras-gateway-new-features-to-design-your--deployment"></a><a name="bkmk_new"></a>RAS 게이트웨이 새 기능을 사용 하 여 배포 디자인  
RAS Gateway에는 데이터 센터에서 게이트웨이 인프라를 배포 하는 방법을 변경 하 고 개선 하는 여러 가지 새로운 기능이 포함 되어 있습니다.  
  
### <a name="bgp-route-reflector"></a>BGP 경로 리플렉터  
이제 BGP (Border Gateway Protocol) 경로 리플렉터 기능이 RAS 게이트웨이에 포함 되어 있으며, 라우터 간 경로 동기화에 일반적으로 필요한 BGP 전체 메시 토폴로지에 대 한 대안을 제공 합니다. 풀 메시 동기화를 수행 하면 모든 BGP 라우터 라우팅 토폴로지에 있는 다른 모든 라우터 연결 해야 합니다. 그러나 경로 리플렉터를 사용 하는 경우 경로 리플렉터는 BGP 경로 리플렉터 클라이언트 라고 하는 다른 모든 라우터와 연결 하 여 경로 동기화를 간소화 하 고 네트워크 트래픽을 줄이는 유일한 라우터입니다. 경로 Reflector 모든 경로 학습 최상의 경로 계산 하 고 최상의 경로 BGP 클라이언트를 다시 배포 합니다.  
  
자세한 내용은 [RAS 게이트웨이의 새로운 기능](../../../sdn/technologies/network-function-virtualization/What-s-New-in-RAS-Gateway.md)을 참조 하세요.  
  
### <a name="gateway-pools"></a><a name="bkmk_pools"></a>게이트웨이 풀  
Windows Server 2016에서는 여러 유형의 게이트웨이 풀을 여러 개 만들 수 있습니다. 게이트웨이 풀 RAS 게이트웨이의 여러 인스턴스를 포함 하 고 실제 및 가상 네트워크 간에 네트워크 트래픽을 라우팅합니다.  
  
자세한 내용은 [Ras 게이트웨이의 새로운 기능](../../../sdn/technologies/network-function-virtualization/What-s-New-in-RAS-Gateway.md) 및 [ras 게이트웨이 고가용성](../../../sdn/technologies/network-function-virtualization/RAS-Gateway-High-Availability.md)을 참조 하세요.  
  
### <a name="gateway-pool-scalability"></a><a name="bkmk_gps"></a>게이트웨이 풀 확장성  
쉽게 확장할 수 있습니다 게이트웨이 풀 위로 또는 아래로 추가 하거나 풀에서 게이트웨이 Vm을 제거 합니다. 게이트웨이 추가 또는 제거는 풀에서 제공 되는 서비스를 방해 하지 않도록 합니다. 또한 추가 및 게이트웨이 전체 풀을 제거할 수 있습니다.  
  
자세한 내용은 [Ras 게이트웨이의 새로운 기능](../../../sdn/technologies/network-function-virtualization/What-s-New-in-RAS-Gateway.md) 및 [ras 게이트웨이 고가용성](../../../sdn/technologies/network-function-virtualization/RAS-Gateway-High-Availability.md)을 참조 하세요.  
  
### <a name="mn-gateway-pool-redundancy"></a><a name="bkmk_m"></a>M + N 게이트웨이 풀 중복성  
모든 게이트웨이 풀은 M + N 중복입니다. 즉, ' N ' 개의 활성 게이트웨이 Vm이 대기 게이트웨이 Vm의 ' N ' 개를 백업 합니다. M + N 중복 RAS 게이트웨이 배포할 때 필요한 안정성 수준을 결정 하는 데 더 많은 융통성을 제공 합니다.  
  
자세한 내용은 [Ras 게이트웨이의 새로운 기능](../../../sdn/technologies/network-function-virtualization/What-s-New-in-RAS-Gateway.md) 및 [ras 게이트웨이 고가용성](../../../sdn/technologies/network-function-virtualization/RAS-Gateway-High-Availability.md)을 참조 하세요.  
  
## <a name="example-deployment"></a><a name="bkmk_example"></a>배포 예  
다음 그림에서는 두 테 넌 트, Contoso 및 Woodgrove와 Fabrikam CSP 데이터 센터 간에 구성 된 사이트 간 VPN 연결을 통해 eBGP 피어 링을 사용 하는 예제를 제공 합니다.  
  
![사이트 간 VPN을 통한 eBGP 피어 링](../../../media/RAS-Gateway-Deployment-Architecture/ras_gateway_architecture.png)  
  
이 예에서 Contoso는 추가 게이트웨이 대역폭이 필요 하며, 게이트웨이 인프라 디자인 결정에 따라 GW2 대신 GW3에서 Contoso 로스앤젤레스 사이트를 종료 합니다. 이로 인해 서로 다른 사이트의 Contoso VPN 연결은 서로 다른 두 게이트웨이의 CSP 데이터 센터에서 종료 됩니다.  
  
GW2 및 GW3 게이트웨이는 모두 CSP가 Contoso 및 Woodgrove 테 넌 트를 인프라에 추가 했을 때 네트워크 컨트롤러에서 구성 하는 첫 번째 RAS 게이트웨이입니다. 이 때문에 이러한 두 게이트웨이는 이러한 해당 고객 (테 넌 트)의 경로 반영자 구성 됩니다. GW2는 Contoso 경로 리플렉터이 고 GW3는 Woodgrove 경로 리플렉터 이며, Contoso 로스앤젤레스 본부 사이트와 VPN 연결을 위한 CSP RAS 게이트웨이 종료 지점이 될 수도 있습니다.  
  
> [!NOTE]  
> 한 RAS 게이트웨이는 각 테 넌 트의 대역폭 요구 사항에 따라 최대 100 개의 다른 테 넌 트에 대해 가상 및 실제 네트워크 트래픽을 라우팅할 수 있습니다.  
  
경로 반영자 GW2는 Contoso CA 공간 경로를 네트워크 컨트롤러로 보내고 GW3는 Woodgrove CA 공간 경로를 네트워크 컨트롤러로 보냅니다.  
  
네트워크 컨트롤러는 Hyper-v 네트워크 가상화 정책을 Contoso 및 Woodgrove 가상 네트워크에 푸시하여 ras 게이트웨이 및 소프트웨어 부하 분산으로 구성 된 멀티플렉서 (MUXes)에 대 한 부하 분산 정책에 대 한 RAS 정책을 푸시합니다. pool.  
  
## <a name="adding-new-tenants-and-customer-address-ca-space-ebgp-peering"></a><a name="bkmk_tenant"></a>새 테 넌 트 및 CA (고객 주소) 공간 eBGP 피어 링 추가  
새 고객을 서명 하 고 고객을 데이터 센터에 새 테 넌 트로 추가 하는 경우 다음 프로세스를 사용할 수 있습니다 .이 프로세스는 대부분 네트워크 컨트롤러 및 RAS 게이트웨이 eBGP 라우터에 의해 자동으로 수행 됩니다.  
  
1.  테 넌 트의 요구 사항에 따라 새 가상 네트워크 및 워크 로드를 프로 비전 합니다.  
  
2.  필요한 경우 원격 테 넌 트 엔터프라이즈 사이트와 데이터 센터의 가상 네트워크 간 원격 연결을 구성 합니다. 테 넌 트에 대해 사이트 간 VPN 연결을 배포 하는 경우 네트워크 컨트롤러는 사용 가능한 게이트웨이 풀에서 사용할 수 있는 RAS 게이트웨이 VM을 자동으로 선택 하 고 연결을 구성 합니다.  
  
3.  새 테 넌 트에 대 한 RAS 게이트웨이 VM을 구성 하는 동안 네트워크 컨트롤러는 RAS 게이트웨이를 BGP 라우터로 구성 하 고 테 넌 트의 경로 리플렉터로 지정 합니다. 이는 RAS 게이트웨이가 게이트웨이 역할을 하거나 다른 테 넌 트에 대해 게이트웨이 및 경로 리플렉터로 제공 되는 경우에도 마찬가지입니다.  
  
4.  네트워크 컨트롤러는 정적으로 구성 된 네트워크 또는 동적 BGP 라우팅을 사용 하도록 구성 되었는지 여부에 따라 RAS 게이트웨이 VM 및 경로 리플렉터에서 해당 하는 고정 경로, BGP 환경 또는 둘 다를 구성 합니다.  
  
    > [!NOTE]  
    > -   네트워크 컨트롤러에서 테 넌 트에 대 한 RAS 게이트웨이 및 경로 리플렉터를 구성한 후 동일한 테 넌 트에 새 사이트 간 VPN 연결이 필요한 경우 네트워크 컨트롤러는이 RAS 게이트웨이 VM에서 사용 가능한 용량을 확인 합니다. 원본 게이트웨이가 필요한 용량을 서비스 할 수 있는 경우 동일한 RAS 게이트웨이 VM에도 새 네트워크 연결이 구성 됩니다. RAS 게이트웨이 VM이 추가 용량을 처리할 수 없는 경우 네트워크 컨트롤러는 사용 가능한 새 RAS 게이트웨이 VM을 선택 하 고 여기에 새 연결을 구성 합니다. 테 넌 트와 연결 된이 새 RAS 게이트웨이 VM은 원래 테 넌 트 RAS 게이트웨이 경로 리플렉터의 경로 리플렉터 클라이언트가 됩니다.  
    > -   RAS 게이트웨이 풀이 SLBs (소프트웨어 부하 분산 장치) 뒤에 있기 때문에 테 넌 트의 사이트 간 VPN 주소는 각각 가상 IP 주소 (VIP) 라고 하는 단일 공용 IP 주소를 사용 합니다 .이 IP 주소는 SLBs로 변환 됩니다. 엔터프라이즈 테 넌 트의 트래픽을 라우팅하는 RAS 게이트웨이의 동적 IP 주소 (DIP)입니다. SLB에의 한 공용-개인 IP 주소 매핑은 엔터프라이즈 사이트와 CSP RAS 게이트웨이 및 경로 반영자 간에 사이트 간 VPN 터널이 올바르게 설정 되어 있는지 확인 합니다.  
    >   
    >     SLB, Vip 및 Dip에 대 한 자세한 내용은 [SDN에 대 한 소프트웨어 &#40;부하&#41; 분산 slb](../../../sdn/technologies/network-function-virtualization/Software-Load-Balancing--SLB--for-SDN.md)를 참조 하세요.  
  
5.  엔터프라이즈 사이트와 CSP 데이터 센터 간의 사이트 간 VPN 터널이 새 테 넌 트에 대해 설정 된 후 터널에 연결 된 고정 경로는 터널의 엔터프라이즈 및 CSP 측 모두에서 자동으로 프로 비전 됩니다. .  
  
6.  CA 공간 BGP 라우팅을 사용 하면 엔터프라이즈 사이트와 CSP RAS 게이트웨이 경로 리플렉터 간의 eBGP 피어 링도 설정 됩니다.  
  
## <a name="route-synchronization-and-data-plane-routing"></a><a name="bkmk_route"></a>경로 동기화 및 데이터 평면 라우팅  
엔터프라이즈 사이트와 CSP RAS 게이트웨이 경로 리플렉터 사이에서 eBGP 피어 링이 설정 되 면 경로 리플렉터는 동적 BGP 라우팅을 사용 하 여 모든 엔터프라이즈 경로를 학습 합니다. 경로 리플렉터는 모든 경로 리플렉터 클라이언트 간에 이러한 경로를 동기화 하므로 모두 동일한 경로 집합을 사용 하 여 구성 됩니다.  
  
경로 리플렉터는 또한 경로 동기화를 사용 하 여 이러한 통합 경로를 네트워크 컨트롤러에 업데이트 합니다. 그런 다음 네트워크 컨트롤러는 경로를 Hyper-v 네트워크 가상화 정책으로 변환 하 고 패브릭 네트워크를 구성 하 여 종단 간 데이터 경로 라우팅이 프로 비전 되도록 합니다. 이 프로세스를 통해 테 넌 트 엔터프라이즈 사이트에서 테 넌 트 가상 네트워크에 액세스할 수 있습니다.  
  
데이터 평면 라우팅의 경우, 이제 모든 참여 하는 RAS 게이트웨이 Vm에서 필요한 경로를 사용할 수 있기 때문에 RAS 게이트웨이 Vm에 도달 하는 패킷이 테 넌 트의 가상 네트워크로 직접 라우팅됩니다.  
  
마찬가지로, Hyper-v 네트워크 가상화 정책을 사용 하는 경우 테 넌 트 가상 네트워크는 패킷을 RAS 게이트웨이 Vm (경로 리플렉터에 대해 몰라도 안 함)으로 라우팅 한 다음 사이트 간 VPN 터널을 통해 엔터프라이즈 사이트에 라우팅합니다. .  
  
또한. 테 넌 트 가상 네트워크에서 원격 테 넌 트 엔터프라이즈 사이트로의 트래픽을 반환 하면 DSR (Direct Server Return) 이라는 프로세스 인 SLBs가 무시 됩니다.  
  
## <a name="how-network-controller-responds-to-ras-gateway-and-route-reflector-failover"></a><a name="bkmk_failover"></a>네트워크 컨트롤러가 RAS 게이트웨이 및 경로 리플렉터 장애 조치 (Failover)에 응답 하는 방법  
다음은 두 가지 구성에서 Vm에 대 한 장애 조치 (failover)를 처리 하는 방법에 대 한 정보를 포함 하는 RAS 게이트웨이 경로 리플렉터 클라이언트 및 RAS 게이트웨이 경로 반영자에 대 한 두 가지 가능한 장애 조치 시나리오  
  
### <a name="vm-failure-of-a-ras-gateway-bgp-route-reflector-client"></a>RAS 게이트웨이 BGP 경로 리플렉터 클라이언트의 VM 오류  
네트워크 컨트롤러는 RAS 게이트웨이 경로 리플렉터 클라이언트에 오류가 발생 하는 경우 다음 작업을 수행 합니다.  
  
> [!NOTE]  
> RAS 게이트웨이가 테 넌 트의 BGP 인프라에 대 한 경로 리플렉터가 아닌 경우이는 테 넌 트의 BGP 인프라에 있는 경로 리플렉터 클라이언트입니다.  
  
-   네트워크 컨트롤러는 사용 가능한 대기 RAS 게이트웨이 VM을 선택 하 고 실패 한 RAS 게이트웨이 VM의 구성으로 새 RAS 게이트웨이 VM을 프로 비전 합니다.  
  
-   네트워크 컨트롤러는 해당 SLB 구성을 업데이트 하 여 테 넌 트 사이트에서 실패 한 RAS 게이트웨이로의 사이트 간 VPN 터널이 새 RAS 게이트웨이로 올바르게 설정 되었는지 확인 합니다.  
  
-   네트워크 컨트롤러가 새 게이트웨이에서 BGP 경로 리플렉터 클라이언트를 구성 합니다.  
  
-   네트워크 컨트롤러가 새 RAS 게이트웨이 BGP 경로 리플렉터 클라이언트를 활성으로 구성 합니다. RAS 게이트웨이는 즉시 테 넌 트의 경로 리플렉터로 피어 링을 시작 하 여 라우팅 정보를 공유 하 고 해당 엔터프라이즈 사이트에 대해 eBGP 피어 링을 사용 하도록 설정 합니다.  
  
### <a name="vm-failure-for-a-ras-gateway-bgp-route-reflector"></a>RAS 게이트웨이 BGP 경로 리플렉터에 대 한 VM 오류  
네트워크 컨트롤러는 RAS 게이트웨이 BGP 경로 리플렉터에 오류가 발생 하는 경우 다음 작업을 수행 합니다.  
  
-   네트워크 컨트롤러는 사용 가능한 대기 RAS 게이트웨이 VM을 선택 하 고 실패 한 RAS 게이트웨이 VM의 구성으로 새 RAS 게이트웨이 VM을 프로 비전 합니다.  
  
-   네트워크 컨트롤러는 새 RAS 게이트웨이 VM에서 경로 리플렉터를 구성 하 고 새 VM에 오류가 발생 한 VM에서 사용한 것과 동일한 IP 주소를 할당 하 여 VM 오류에도 불구 하 고 경로 무결성을 제공 합니다.  
  
-   네트워크 컨트롤러는 해당 SLB 구성을 업데이트 하 여 테 넌 트 사이트에서 실패 한 RAS 게이트웨이로의 사이트 간 VPN 터널이 새 RAS 게이트웨이로 올바르게 설정 되었는지 확인 합니다.  
  
-   네트워크 컨트롤러가 새 RAS 게이트웨이 BGP 경로 리플렉터 VM을 활성으로 구성 합니다.  
  
-   경로 리플렉터는 즉시 활성화 됩니다. 엔터프라이즈에 대 한 사이트 간 VPN 터널이 설정 되 고 경로 리플렉터는 eBGP 피어 링을 사용 하 고 엔터프라이즈 사이트 라우터를 사용 하 여 경로를 교환 합니다.  
  
-   BGP 경로를 선택 하면 RAS 게이트웨이 BGP 경로 리플렉터는 데이터 센터에서 테 넌 트 경로 리플렉터 클라이언트를 업데이트 하 고, 네트워크 컨트롤러와 경로를 동기화 하 여 테 넌 트 트래픽에 대해 종단 간 데이터 경로를 사용할 수 있도록 합니다.  
  
## <a name="advantages-of-using-new-ras-gateway-features"></a><a name="bkmk_advantages"></a>새 RAS 게이트웨이 기능 사용의 이점  
다음은 RAS 게이트웨이 배포를 설계할 때 이러한 새로운 RAS 게이트웨이 기능을 사용 하는 몇 가지 이점입니다.  
  
**RAS 게이트웨이 확장성**  
  
Ras 게이트웨이 풀에 필요한 만큼의 RAS 게이트웨이 Vm을 추가할 수 있으므로, RAS 게이트웨이 배포를 쉽게 확장 하 여 성능 및 용량을 최적화할 수 있습니다. 풀에 Vm을 추가 하는 경우 이러한 RAS 게이트웨이를 모든 종류 (IKEv2, L3, GRE)의 사이트 간 VPN 연결로 구성 하 여 중단 시간 없이 용량 병목 현상을 제거할 수 있습니다.  
  
**간소화 된 엔터프라이즈 사이트 게이트웨이 관리**  
  
테 넌 트에 여러 엔터프라이즈 사이트가 있는 경우 테 넌 트는 하나의 원격 사이트 간 VPN IP 주소 및 단일 원격 인접 IP 주소 (해당 테 넌 트의 CSP 데이터 센터 RAS 게이트웨이 BGP 경로 리플렉터 VIP)를 사용 하 여 모든 사이트를 구성할 수 있습니다. 이렇게 하면 테 넌 트에 대 한 게이트웨이 관리가 간단해 집니다.  
  
**게이트웨이 실패의 빠른 수정**  
  
빠른 장애 조치 (failover) 응답을 보장 하기 위해 edge 경로와 제어 라우터 간에 BGP Keepalive 매개 변수 시간을 10 초 보다 작거나 같은 짧은 시간 간격으로 구성할 수 있습니다. 이 짧은 연결 유지 간격으로 RAS 게이트웨이 BGP edge 라우터가 실패 하면 오류가 빠르게 검색 되 고 네트워크 컨트롤러가 이전 섹션에서 제공 하는 단계를 따릅니다. 이러한 이점을 활용 하면 BFD (양방향 전달 검색) 프로토콜과 같은 별도의 오류 검색 프로토콜이 필요 하지 않을 수 있습니다.  
  
 
  


