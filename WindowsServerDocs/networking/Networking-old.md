---
title: 네트워킹
description: 이 항목에서는 Windows Server 2016에서 사용할 수 있는 소프트웨어 정의 네트워킹 및 네트워크 플랫폼 기술을 개략적으로 살펴봅니다.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.date: 05/08/2018
ms.assetid: daaf6b61-5953-4c2d-b6b8-7c885b552646
manager: dougkim
ms.author: lizross
author: eross-msft
ms.localizationpriority: medium
ms.openlocfilehash: 833f1681af16b4e79a28383462a3471b3bc08f52
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319362"
---
# <a name="networking"></a>네트워킹

>적용 대상: Windows Server(반기 채널), Windows Server 2016

       [!TIP]
        Looking for information about older versions of Windows Server? Check out our other [Windows Server libraries](/previous-versions/windows/) on docs.microsoft.com. You can also [search this site](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions) for specific information.

<img src="../media/landing-icons/network.png" style='float:left; padding:.5em;' alt="Icon depicting two networked computers"> 네트워킹은 소프트웨어 정의 데이터 센터 \(SDDC\) 플랫폼의 기본 부분으로, Windows Server 2016은 조직에 대해 완벽 하 게 실현 된 SDDC 솔루션으로 이동 하는 데 도움이 되는 새롭고 향상 된 소프트웨어 정의 네트워킹 \(SDN\) 기술을 제공 합니다.

네트워크를 소프트웨어 정의 리소스로 관리 하는 경우 한 번에 응용 프로그램의 인프라 요구 사항을 설명 하 고 응용 프로그램이 실행 되는 위치 (온-프레미스 또는 클라우드에서)를 선택할 수 있습니다. 

이러한 일관성 덕분에 이제는 응용 프로그램을 보다 손쉽게 확장할 수 있게 되었습니다. 또한 보안, 성능, 서비스 품질 및 가용성에 대해 안심하면서 어디서나 원활하게 응용 프로그램을 실행할 수 있습니다.

>[!Note]
> Windows Server를 다운로드하는 방법은 [Windows Server 평가판](https://www.microsoft.com/evalcenter/evaluate-windows-server-technical-preview)을 참조하세요.

Windows Server 2016에는 다음과 같은 새로운 네트워킹 기술을 추가합니다.

- 소프트웨어 정의 네트워킹: 네트워크 컨트롤러 관리, 구성, 모니터링 및 데이터 센터의 가상 및 실제 네트워크 인프라의 문제를 해결 하는 자동화의 프로그래밍 가능한 중앙된 위치를 제공 합니다. 네트워크 컨트롤러를 사용 하면 네트워크 기능 가상화를 사용 하 여 쉽게 가상 컴퓨터를 배포할 수 있습니다 \(Vm\) 소프트웨어 부하 분산을 위해 \(SLB\) 인터넷, 온 프레미스 및 클라우드 리소스 간에 필요한 테 넌 트 연결 옵션을 제공 하 여 테 넌 트 및 RAS 게이트웨이에 대 한 네트워크 트래픽 부하를 최적화할 수 있습니다. Vm과 Hyper-v에 대 한 데이터 센터 방화벽을 관리 네트워크 컨트롤러를 사용할 수도 있습니다 호스트 합니다.

- 기존 네트워크 플랫폼 기술에 대 한 새로운 기능을 사용 하는 네트워크 플랫폼:, 정책을 사용할 수 있습니다 DNS에 DNS 서버가 쿼리에 대 한 응답을 사용자 지정할 수 핸들 원격 직접 메모리 액세스 함을 수렴 된 NIC를 사용 하 여 \(RDMA\) 및 트래픽, 포함 된 팀 구성 스위치를 사용 하 여 이더넷 \(설정\) RDMA Nic에 연결 하는 Hyper-v 가상 스위치를 만들고 IP 주소 관리를 사용 하 \(IPAM\) DHCP 및 IP 주소 뿐만 아니라 DNS 영역 및 서버를 관리할 수 있습니다.

자세한 내용은 [Windows Server 지원 네트워킹 시나리오](windows-server-supported-networking-scenarios.md)를 참조하세요.

다음 섹션에서는 SDN 기술 및 네트워크 플랫폼 기술에 대한 정보를 제공합니다.

## <a name="software-defined-networking-technologies"></a>소프트웨어 정의 네트워킹 기술

### <a name="software-defined-networking-40sdn41"></a>[소프트웨어 정의 네트워킹 &#40;SDN&#41;](sdn/software-defined-networking.md)

Windows Server, System Center 및 Microsoft Azure에서 제공 되는 SDN 기술에 대해 자세히 알아보려면이 항목을 사용할 수 있습니다.

>[!NOTE]
>네트워크 컨트롤러 및 소프트웨어 부하 분산 노드와 같이 SDN 인프라 서버를 실행 하는 Hyper-v 호스트 및 가상 컴퓨터 \(Vm\) Windows Server 2016 Datacenter edition을 설치 해야 합니다. SDN\-제어 된 네트워크에 연결 된 테 넌 트 워크 로드 Vm만 포함 하는 Hyper-v 호스트의 경우 Windows Server 2016 Standard edition을 실행할 수 있습니다.

### <a name="deploy-a-software-defined-network-infrastructure-using-scripts"></a>[스크립트를 사용 하 여 소프트웨어 정의 네트워크 인프라 배포](sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md)
이 가이드에서는 테스트 랩 환경에서 가상 네트워크와 게이트웨이 사용 하 여 네트워크 컨트롤러를 배포 하는 방법을 설명 합니다.

### <a name="network-controller"></a>[네트워크 컨트롤러](sdn/technologies/network-controller/Network-Controller.md)

네트워크 컨트롤러 관리, 구성, 모니터링 및 데이터 센터의 가상 및 실제 네트워크 인프라의 문제를 해결 하는 자동화의 프로그래밍 가능한 중앙된 위치를 제공 합니다.

### <a name="software-load-balancing-40slb41-for-sdn"></a>[SDN에 대 &#40;한&#41; 소프트웨어 부하 분산 SLB](sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn.md)

클라우드 서비스 공급자 \(Csp\) 및 네트워킹 SDN (소프트웨어)에서 Windows Server 2016을 배포 하는 기업 소프트웨어 부하 분산을 사용 하 여 \(SLB\) 테 넌 트 및 테 넌 트 고객 네트워크 트래픽 가상 네트워크 리소스 간에 고르게 분산 시킵니다. Windows Server SLB 높은 가용성과 확장성이 같은 작업을 호스트 하는 여러 서버를 수 있습니다.

### <a name="ras-gateway-for-sdn"></a>[SDN용 RAS 게이트웨이](sdn/technologies/network-function-virtualization/RAS-Gateway-for-SDN.md)

소프트웨어 기반 인 RAS 게이트웨이, 다중 테 넌 트, 경계 게이트웨이 프로토콜 \(BGP\) Windows Server 2016에서 지원 라우터는 클라우드 서비스 공급자를 위한 \(Csp\) 및 Hyper-v 네트워크 가상화를 사용 하 여 여러 테 넌 트 가상 네트워크를 호스팅하는 기업입니다. 

### <a name="network-function-virtualization"></a>[네트워크 기능 가상화](sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md)

정의 된 소프트웨어 데이터 센터에서 네트워크 하드웨어 어플라이언스를 통해 수행 되는 함수 \(부하 분산 장치, 방화벽, 라우터, 스위치 등\) 가상 어플라이언스로 가상화 점점 더 됩니다. 이 "네트워크 기능 가상화" 서버 가상화 및 네트워크 가상화의 자연 스러운 진행 됩니다.

### <a name="datacenter-firewall-overview"></a>[데이터 센터 방화벽 개요](sdn/technologies/network-function-virtualization/Datacenter-Firewall-Overview.md)

데이터 센터 방화벽은 네트워크 계층, 5 개 튜플 (프로토콜, 원본 및 대상 포트 번호, 원본 및 대상 IP 주소) 상태 저장, 다중 테 넌 트 방화벽입니다.

## <a name="networking-technologies"></a><a name="bkmk_networking"></a>네트워킹 기술

다음 표에서 Windows Server 2016의 네트워킹 기술 중 일부에 대 한 링크를 제공합니다.

### <a name="whats-new-in-networking"></a>[네트워킹의 새로운 기능](../networking/What-s-New-in-Networking.md)

다음 섹션에서는 새로운 네트워킹 기술 및 Windows Server 2016의 기존 기술에 대 한 새로운 기능 검색을 사용할 수 있습니다.

### <a name="branchcache"></a>[BranchCache](branchcache/BranchCache.md)

BranchCache는 광역 네트워크 \(WAN\) 대역폭 최적화 기술입니다. 파일을 사용자가 원격 서버의 콘텐츠에 액세스할 때 WAN 대역폭을 최적화 하려면 BranchCache 본사에서 콘텐츠를 가져오며 또는 호스트 된 클라우드 콘텐츠 서버 및 캐시 지점 사무실 위치에서 콘텐츠를 클라이언트 컴퓨터는 WAN을 통해이 아닌 로컬 콘텐츠를 액세스 하는 지사 사무소에 허용 합니다.

### <a name="core-network-guide-for-windows-server-2016"></a>[Windows Server 2016에 대 한 핵심 네트워크 가이드](core-network-guide/core-network-guide-windows-server.md)

핵심 네트워크 가이드를 통해 Windows Server 네트워크를 배포하는 방법을 확인하고 핵심 네트워크 부록 가이드를 통해 배포된 네트워크에 기능을 추가합니다.

### <a name="directaccess"></a>[DirectAccess](../remote/remote-access/directaccess/DirectAccess.md)

DirectAccess는 조직의 네트워크 리소스에 원격 사용자를 연결합니다. 

DirectAccess 설명서는 [원격 액세스](https://docs.microsoft.com/windows-server/remote/) 아래 Windows Server 2016 목차의 [원격 액세스 및 서버 관리](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access) 섹션에 위치해 있습니다. 자세한 내용은 [DirectAccess](../remote/remote-access/directaccess/DirectAccess.md)를 참조하세요.

### <a name="domain-name-system-40dns41"></a>[도메인 이름 시스템 &#40;DNS&#41;](dns/dns-top.md)

Domain Name System \(DNS\) TCP/IP를 구성 하는 프로토콜의 산업 표준 프로토콜 중 하나입니다 설명과 함께 DNS 클라이언트와 DNS 서버 컴퓨터 이름-IP 주소를 컴퓨터 및 사용자 매핑 이름 확인 서비스입니다.

### <a name="dynamic-host-configuration-protocol-40dhcp41"></a>[동적 호스트 구성 프로토콜 &#40;DHCP&#41;](technologies/dhcp/dhcp-top.md)

동적 호스트 구성 프로토콜 \(DHCP\) 는 자동으로 인터넷 프로토콜을 제공 하는 클라이언트/서버 프로토콜 \(IP\) 호스트의 IP 주소 및 다른 관련 서브넷 마스크 및 기본 게이트웨이 등의 구성 정보입니다.

### <a name="hyper-v-network-virtualization"></a>[Hyper-v 네트워크 가상화](sdn/technologies/hyper-v-network-virtualization/Hyper-V-Network-Virtualization.md)

Hyper-v 네트워크 가상화 \(HNV\)를 사용 하면 공유 된 실제 네트워크 인프라를 기반으로 고객 네트워크를 가상화 할 수 있습니다. "" ""

### <a name="hyper-v-virtual-switch"></a>[Hyper-V 가상 스위치](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)

Hyper-V 가상 스위치는 Hyper-V 서버 역할을 설치할 때 Hyper-V 관리자에서 사용할 수 있는 소프트웨어 기반의 계층 2 이더넷 네트워크 스위치입니다. 스위치에는 프로그램 방식으로 관리되며 확장 가능한 기능이 포함되어 있어 가상 시스템을 가상 네트워크와 실제 네트워크에 모두 연결할 수 있습니다. 또한 Hyper-V 가상 스위치를 사용하여 보안, 격리 및 서비스 수준의 정책을 적용할 수 있습니다. 

Hyper-V 가상 스위치 설명서는 Windows Server 2016 목차의 **가상화** 섹션에 위치해 있습니다. 자세한 내용은 참조 [Hyper-v 가상 스위치](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)합니다.

### <a name="ip-address-management-40ipam41"></a>[IP 주소 관리 &#40;IPAM&#41;](technologies/ipam/ipam-top.md)

IP 주소 관리 \(IPAM\)는 엔드투엔드 계획, 배포, 사용 하도록 설정 하는 도구의 통합된 모음인 관리 및 풍부한 사용자 환경을 통해 IP 주소 인프라의 모니터링합니다. IPAM IP 주소 인프라 서버 및 도메인 이름 시스템에 자동으로 검색 \(DNS\) 네트워크 서버에 중앙 인터페이스에서이 관리할 수 있습니다.

### <a name="network-load-balancing"></a>[네트워크 부하 분산](technologies/Network-Load-Balancing.md)

네트워크 로드 균형 조정 \(NLB\) TCP/IP 네트워킹 프로토콜을 사용 하 여 여러 서버로 트래픽을 분산 합니다. NLB 보장을 상태 비저장 SDN 아닌 배포에 대 한 인터넷 정보 서비스를 실행 하는 웹 서버 등의 응용 프로그램 \(IIS\), 부하가 증가 따라 서버를 추가 하 여 확장 가능한 됩니다.

### <a name="high-performance-networking"></a>[고성능 네트워킹](technologies/hpn/hpn-top.md)

Windows Server 2016의 네트워크 오프로드 및 최적화 기술에는 소프트웨어 전용(SO) 기능 및 기술과 소프트웨어 및 하드웨어(SH) 통합 기능 및 기술, 하드웨어 전용(HO) 기능 및 기술이 포함되어 있습니다.

다음과 같은 오프로드 및 최적화 기술 설명서를 사용할 수도 있습니다.

- [수렴 형 NIC (네트워크 인터페이스 카드) 구성 가이드](technologies/conv-nic/cnic-top.md)
- [DCB (데이터 센터 브리징)](technologies/dcb/dcb-top.md)
- [vRSS(가상 수신측 배율)](technologies/vrss/vrss-top.md)


### <a name="network-policy-server"></a>[네트워크 정책 서버](technologies/nps/nps-top.md)

네트워크 정책 서버(NPS)를 사용하면 연결 요청 인증 및 권한 부여를 위해 조직 전체의 네트워크 액세스 정책을 생성하여 적용할 수 있습니다.

### <a name="network-shell-netsh"></a>[Netsh(네트워크 셸)](technologies/netsh/netsh.md)

네트워크 셸 \(netsh\) 네트워킹 유틸리티를 사용 하 여 Windows Server 2016 및 Windows 10에서 네트워킹 기술을 관리할 수 있습니다.

### <a name="network-subsystem-performance-tuning"></a>[네트워크 하위 시스템 성능 튜닝](technologies/network-subsystem/net-sub-performance-top.md)

이 항목에서는 서버 작업에 적합 한 네트워크 어댑터 선택, 네트워크 인터페이스 순서 지정, 네트워크 관련 성능 카운터 및 성능 튜닝 네트워크 어댑터와 관련 네트워킹 기술 (예: RSS\)\(수신 측 크기 조정, \(RSC\)및 기타)에 대 한 정보를 제공 합니다.

### <a name="nic-teaming"></a>[NIC 팀](technologies/nic-teaming/NIC-Teaming.md)

NIC 팀 하나 이상의 소프트웨어 기반 가상 네트워크 어댑터에 실제 이더넷 네트워크 어댑터를 그룹화 할 수 있습니다. 이 가상 네트워크 어댑터에는 빠른 성능과 네트워크 어댑터 오류 발생 시 내결함성을 제공합니다.

### <a name="quality-of-service-qos-policy"></a>[QoS (서비스 품질) 정책](technologies/qos/qos-policy-top.md)

그룹 정책을 통해 설정이 배포되는 QoS 프로필을 생성하여 Active Directory 인프라 전체에서 네트워크 대역폭을 관리하기 위한 중심점으로 QoS 정책을 사용할 수 있습니다.

### <a name="remote-access"></a>[원격 액세스](../remote/remote-access/remote-access.md)

DirectAccess 및 가상 사설망 \(VPN\)와 같은 원격 액세스 기술을 사용 하 여 원격 작업자에 게 내부 네트워크 리소스에 대 한 연결을 제공할 수 있습니다. 또한 로컬 영역 네트워크 \(LAN\) 라우팅 및 웹 응용 프로그램 프록시에 대 한 원격 액세스를 사용할 수 있습니다. 웹 응용 프로그램 프록시는 회사 네트워크 내부의 웹 응용 프로그램에 역방향 프록시 기능을 제공하여 모든 장치의 사용자가 회사 네트워크 권역을 벗어나서도 해당 네트워크에 액세스할 수 있도록 합니다.

원격 액세스 설명서는 Windows Server 2016 목차의 [원격 액세스 및 서버 관리](https://docs.microsoft.com/windows-server/remote/) 섹션에 위치해 있습니다. 자세한 내용은 [원격 액세스](../remote/remote-access/remote-access.md)를 참조하세요.

원격 액세스 서버 역할의 역할 서비스인 웹 응용 프로그램 프록시에 대한 자세한 내용은 [Windows Server 2016의 웹 응용 프로그램 프록시](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server)를 참조하세요.

### <a name="virtual-private-networking-vpn"></a>[VPN(가상 사설망)](../remote/remote-access/vpn/vpn-top.md)

Windows Server 2016에서는 **DirectAccess 및 VPN**이 **원격 액세스** 서버 역할의 역할 서비스로 제공됩니다.

VPN 서버로 원격 액세스를 설치 하는 경우 VPN\) \(VPN (가상 사설망)을 사용 하 여 원격 직원에 게 인터넷을 통해 조직 네트워크에 대 한 연결을 제공 하는 동시에 암호화 된 연결을 통해 정보 보호를 유지 관리할 수 있습니다.

Windows Server 2016 원격 액세스 VPN과 Windows 10 클라이언트 컴퓨터에서는 Always On VPN을 배포할 수 있습니다. Always On VPN을 사용하면 항시 연결되는 원격 VPN 클라이언트를 관리할 수 있으며, VPN에서 회사 네트워크로의 연결을 수동으로 설정 및 해제할 필요가 없다는 점에서 원격 작업자에게 편의를 제공할 수 있습니다.

자세한 내용은 [Windows Server 2016 및 Windows 10을 위한 원격 액세스 Always On VPN 배포 가이드](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy)를 참조하세요.

>[!NOTE]
>VPN 설명서는 [원격 액세스](https://docs.microsoft.com/windows-server/remote/) 아래 Windows Server 2016 목차의 [원격 액세스 및 서버 관리](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access) 섹션에 위치해 있습니다.

VPN에 대한 자세한 내용은 [가상 사설망(VPN)](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/vpn-top)을 참조하세요.

### <a name="windows-container-networking"></a>[Windows 컨테이너 네트워킹](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/container-networking)

Windows 컨테이너 네트워킹을 사용하면 업계 표준 도구 및 워크플로를 통해 Windows 10 및 Windows Server 호스트에서 컨테이너 끝점을 연결하도록 네트워크를 생성 및 관리할 수 있습니다. Windows 컨테이너 네트워크는 사설 플랫 L2와 라우팅된 L3를 포함하여 여러 토폴로지를 지원합니다.

또한\)\(Windows 호스트 네트워킹 서비스와 통신 하는 플러그 인을 통해 Docker, Kubernetes 또는 Windows PowerShell을 사용 하 여 호스트에서 로컬로 만들 수 있는 오버레이도 지원 됩니다. 로컬 에이전트를 통해 각 노드의 HNS와 통신 하 여 더 높은 수준의 오케스트레이션 시스템을 통해 다중\-노드 클러스터 네트워크를 만들고 관리할 수 있습니다.

### <a name="windows-internet-name-service-wins"></a>[WINS(Windows Internet Name Service)](technologies/wins/wins-top.md)

Windows 인터넷 이름 서비스(WINS)는 IP 주소에 NetBIOS 이름을 매핑하는 기존의 컴퓨터 이름 등록 및 확인 서비스입니다. WINS를 사용하기 보다는 DNS를 사용하는 것이 좋습니다.

## <a name="additional-resources"></a>추가 리소스

네트워킹 리소스는 다음 위치에서 사용할 수 있는 Windows Server 2016 보다 이전의 운영 체제.

- Windows Server 2012 및 Windows Server 2012 R2 [네트워킹 개요](https://technet.microsoft.com/library/hh831357.aspx)
- Windows Server 2008 및 Windows Server 2008 R2 [네트워킹](https://technet.microsoft.com/library/cc753940)
- Windows Server 2003 [Windows server 2003/2003 R2 사용 중지 된 콘텐츠](https://www.microsoft.com/download/details.aspx?id=53314)
