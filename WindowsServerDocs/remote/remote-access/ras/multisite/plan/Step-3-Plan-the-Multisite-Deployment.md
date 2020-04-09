---
title: 3 단계 멀티 사이트 배포 계획
description: 이 항목은 Windows Server 2016에서 멀티 사이트 배포에서 여러 원격 액세스 서버 배포 가이드의 일부입니다.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: e5ea9d22-a503-4ed4-96b3-0ee2ccf4fd17
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 97705e3d6f5a4300c32ec98cc59e849862381607
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858326"
---
# <a name="step-3-plan-the-multisite-deployment"></a>3 단계 멀티 사이트 배포 계획

>적용 대상: Windows Server(반기 채널), Windows Server 2016

멀티 사이트 인프라를 계획 한 후에는 추가 인증서 요구 사항을 계획 하 고, 클라이언트 컴퓨터에서 진입점을 선택 하 고, 배포에 할당 된 IPv6 주소를 계획 합니다.  

다음 섹션에서는 자세한 계획 정보를 제공 합니다.
  
## <a name="31-plan-ip-https-certificates"></a><a name="bkmk_3_1_IPHTTPS"></a>3.1 IP-HTTPS 인증서 요금제  
진입점을 구성할 때 특정 ConnectTo 주소를 사용 하 여 각 진입점을 구성 합니다. 각 진입점에 대 한 IP-HTTPS 인증서가 ConnectTo 주소와 일치 해야 합니다. 인증서를 가져올 때 다음 사항에 유의 하세요.  
  
-   멀티 사이트 배포에서는 자체 서명된 인증서를 사용할 수 없습니다.  
  
-   CRL을 항상 사용할 수 있도록 공용 CA를 사용하는 것이 좋습니다.  
  
-   주체 필드에 원격 액세스 서버 외부 어댑터의 IPv4 주소 (ConnectTo 주소가 DNS 이름이 아닌 IP 주소로 지정 된 경우)를 지정 하거나 IP-HTTPS URL의 FQDN을 지정 합니다.  
  
-   인증서의 일반 이름은 IP-HTTPS 웹 사이트의 이름과 일치 해야 합니다. ConnectTo DNS 이름과 일치 하는 와일드 카드 URL 사용도 지원 됩니다.  
  
-   IP-HTTPS 인증서는 주체 이름에 와일드 카드를 사용할 수 있습니다. 모든 진입점에 동일한 와일드 카드 인증서를 사용할 수 있습니다.  
  
-   확장된 키 사용 필드의 경우 서버 인증 OID(개체 식별자)를 사용합니다.  
  
-   멀티 사이트 배포에서 Windows 7을 실행 하는 클라이언트 컴퓨터를 지원 하는 경우 CRL 배포 지점 필드에서 인터넷에 연결 된 DirectAccess 클라이언트에서 액세스할 수 있는 CRL 배포 지점을 지정 합니다. Windows 8을 실행 하는 클라이언트에는이 기능이 필요 하지 않습니다. 기본적으로 이러한 클라이언트에서는 IP-HTTPS에 대해 CRL 해지 확인이 사용 되지 않습니다.  
  
-   IP-HTTPS 인증서에 프라이빗 키가 있어야 합니다.  
  
-   IP-HTTPS 인증서는 사용자가 아닌 컴퓨터의 개인 저장소로 직접 가져와야 합니다.  
  
## <a name="32-plan-the-network-location-server"></a><a name="bkmk_3_2_NLS"></a>3.2 네트워크 위치 서버 계획  
네트워크 위치 서버 웹 사이트는 원격 액세스 서버 또는 조직의 다른 서버에서 호스팅될 수 있습니다. 원격 액세스 서버에서 네트워크 위치 서버를 호스트 하는 경우 원격 액세스를 배포할 때 웹 사이트가 자동으로 만들어집니다. 조직에서 Windows 운영 체제를 실행 하는 다른 서버에서 네트워크 위치 서버를 호스트 하는 경우 웹 사이트를 만들기 위해 인터넷 정보 서비스 (IIS)가 설치 되어 있는지 확인 해야 합니다.  
  
### <a name="321-certificate-requirements-for-the-network-location-server"></a>네트워크 위치 서버에 대 한 인증서 요구 사항 3.2.1  
네트워크 위치 서버 웹 사이트에서 인증서 배포에 대 한 다음 요구 사항을 충족 하는지 확인 합니다.  
  
-   HTTPS 서버 인증서가 필요 합니다.  
  
-   네트워크 위치 서버가 원격 액세스 서버에 있고 단일 원격 액세스 서버를 배포할 때 자체 서명 된 인증서를 사용 하도록 선택한 경우 내부 CA에서 발급 한 인증서를 사용 하도록 단일 서버 배포를 다시 구성 해야 합니다.  
  
-   DirectAccess 클라이언트 컴퓨터가 네트워크 위치 서버 웹 사이트에 서버 인증서를 발급한 CA를 신뢰해야 합니다.  
  
-   내부 네트워크의 DirectAccess 클라이언트 컴퓨터에서 네트워크 위치 서버 웹 사이트의 이름을 확인할 수 있어야 합니다.  
  
-   네트워크 위치 서버 웹 사이트는 내부 네트워크의 컴퓨터에서 항상 사용 가능 해야 합니다.  
  
-   인터넷의 DirectAccess 클라이언트 컴퓨터에서 네트워크 위치 서버에 액세스할 수 없어야 합니다.  
  
-   CRL (인증서 해지 목록)에 대해 서버 인증서를 확인 해야 합니다.  
  
-   네트워크 위치 서버가 원격 액세스 서버에서 호스트 되는 경우에는 와일드 카드 인증서가 지원 되지 않습니다.  
  
네트워크 위치 서버에 사용할 웹 사이트 인증서를 가져올 때 다음 사항에 유의 하십시오.  
  
1.  주체 필드에 네트워크 위치 서버의 인트라넷 인터페이스 IP 주소 또는 네트워크 위치 URL의 FQDN을 지정합니다. 네트워크 위치 서버가 원격 액세스 서버에서 호스트 되는 경우 IP 주소를 지정 하면 안 됩니다. 네트워크 위치 서버는 모든 진입점에 대해 동일한 주체 이름을 사용 해야 하며 모든 진입점에 동일한 IP 주소가 있는 것은 아닙니다.  
  
2.  확장된 키 사용 필드의 경우 서버 인증 OID를 사용합니다.  
  
3.  CRL 배포 지점 필드의 경우 인트라넷에 연결 된 DirectAccess 클라이언트에서 액세스할 수 있는 CRL 배포 지점을 사용 합니다.  
  
### <a name="322dns-for-the-network-location-server"></a>네트워크 위치 서버에 대 한 3.2.2 DNS  
원격 액세스 서버에서 네트워크 위치 서버를 호스트 하는 경우 배포의 모든 진입점에 대 한 네트워크 위치 서버 웹 사이트에 대 한 DNS 항목을 추가 해야 합니다. 유의 사항은 다음과 같습니다.  
  
-   멀티 사이트 배포에 있는 첫 번째 네트워크 위치 서버 인증서의 주체 이름은 모든 진입점에 대 한 네트워크 위치 서버 URL로 사용 되므로 주체 이름과 네트워크 위치 서버 URL은의 컴퓨터 이름과 같을 수 없습니다. 배포의 첫 번째 원격 액세스 서버입니다. 네트워크 위치 서버 전용 FQDN 이어야 합니다.  
  
-   네트워크 위치 서버 트래픽에 의해 제공 되는 서비스는 DNS를 사용 하 여 진입점 간에 분산 되므로 진입점의 내부 IP 주소를 사용 하 여 구성 된 각 진입점에 대해 동일한 URL을 가진 DNS 항목이 있어야 합니다.  
  
-   모든 진입점은 네트워크 위치 서버 URL과 일치 하는 동일한 주체 이름으로 네트워크 위치 서버 인증서를 사용 하 여 구성 해야 합니다.  
  
-   진입점을 추가 하기 전에 진입점에 대 한 네트워크 위치 서버 인프라 (DNS 및 인증서 설정)를 만들어야 합니다.  
  
## <a name="33-plan-the-ipsec-root-certificate-for-all-remote-access-servers"></a><a name="bkmk_3_3_IPsec"></a>3.3 모든 원격 액세스 서버에 대 한 IPsec 루트 인증서 계획  
멀티 사이트 배포에서 IPsec 클라이언트 인증을 계획할 때 다음 사항에 유의 하세요.  
  
1.  단일 원격 액세스 서버를 설정할 때 컴퓨터 인증에 기본 제공 Kerberos 프록시를 사용 하도록 선택한 경우에는 Kerberos 프록시가 멀티 사이트에 대해 지원 되지 않으므로 내부 CA에서 발급 한 컴퓨터 인증서를 사용 하도록 설정을 변경 해야 합니다. 배포가.  
  
2.  자체 서명 된 인증서를 사용 하는 경우 내부 CA에서 발급 한 인증서를 사용 하도록 단일 서버 배포를 다시 구성 해야 합니다.  
  
3.  클라이언트 인증 중에 IPsec 인증이 성공 하려면 모든 원격 액세스 서버에 IPsec 루트 또는 중간 CA에서 발급 한 인증서와 향상 된 키 사용을 위한 클라이언트 인증 OID가 있어야 합니다.  
  
4.  동일한 IPsec 루트 또는 중간 인증서를 멀티 사이트 배포의 모든 원격 액세스 서버에 설치 해야 합니다.  
  
## <a name="34-plan-global-server-load-balancing"></a><a name="bkmk_3_4_GSLB"></a>3.4 글로벌 서버 부하 분산 계획  
멀티 사이트 배포에서는 글로벌 서버 부하 분산 장치를 추가로 구성할 수 있습니다. 배포에서 진입점 간에 트래픽 부하를 분산 시킬 수 있으므로 글로벌 서버 부하 분산 장치는 조직에 유용 하 게 사용할 수 있습니다.  가장 가까운 진입점의 진입점 정보를 DirectAccess 클라이언트에 제공 하도록 전역 서버 부하 분산 장치를 구성할 수 있습니다. 프로세스는 다음과 같이 작동 합니다.  
  
1.  Windows 10 또는 Windows 8을 실행 하는 클라이언트 컴퓨터에는 각각 진입점과 연결 된 글로벌 서버 부하 분산 장치 IP 주소 목록이 있습니다.  
  
2.  Windows 10 또는 Windows 8 클라이언트 컴퓨터에서 공용 DNS의 글로벌 서버 부하 분산 장치 FQDN을 IP 주소로 확인 하려고 합니다. 확인 된 IP 주소가 진입점의 전역 서버 부하 분산 장치 IP 주소로 표시 되는 경우 클라이언트 컴퓨터는 자동으로 해당 진입점을 선택 하 고 IP-HTTPS URL (ConnectTo 주소) 또는 Teredo 서버 IP 주소에 연결 합니다. 클라이언트 컴퓨터가 전역 서버 부하 분산 장치 IP 주소에 연결을 시도 하지 않기 때문에 글로벌 서버 부하 분산 장치의 IP 주소는 진입점의 Teredo 서버 주소 또는 ConnectTo 주소와 동일할 필요가 없습니다.  
  
3.  클라이언트 컴퓨터가 웹 프록시 뒤에 있거나 DNS 확인을 사용할 수 없는 경우 또는 전역 서버 부하 분산 장치 FQDN이 구성 된 글로벌 서버 부하 분산 장치 IP 주소로 확인 되지 않는 경우에는 HTTPS 프로브를 사용 하 여 진입점이 자동으로 선택 됩니다. 모든 진입점의 IP-HTTPS Url입니다. 클라이언트는 먼저 응답 하는 서버에 연결 됩니다.  
  
원격 액세스를 지 원하는 글로벌 서버 부하 분산 장치의 목록은 [Microsoft 서버 및 클라우드 플랫폼](https://www.microsoft.com/server-cloud/)에서 파트너 찾기 페이지로 이동 합니다.  
  
## <a name="35-plan-directaccess-client-entry-point-selection"></a><a name="bkmk_3_5_EP_Selection"></a>3.5 DirectAccess 클라이언트 진입점 선택 계획  
멀티 사이트 배포를 구성 하는 경우 기본적으로 Windows 10 및 Windows 8 클라이언트 컴퓨터는 배포의 모든 진입점에 연결 하 고 선택 항목에 따라 단일 진입점에 자동으로 연결 하는 데 필요한 정보를 사용 하 여 구성 됩니다. 알고리즘과. Windows 10 및 Windows 8 클라이언트 컴퓨터에서 연결할 진입점을 수동으로 선택할 수 있도록 배포를 구성할 수도 있습니다. Windows 10 또는 Windows 8 클라이언트 컴퓨터가 현재 미국 진입점에 연결 되어 있고 자동 진입점 선택이 사용 하도록 설정 된 경우 몇 분 후에 클라이언트 컴퓨터에서 연결을 시도할 수 있습니다. 유럽 진입 지점을 통해. 자동 진입점 선택을 사용 하는 것이 좋습니다. 그러나 수동으로 진입점 선택을 허용 하면 최종 사용자가 현재 네트워크 상태에 따라 다른 진입점에 연결할 수 있습니다. 예를 들어 컴퓨터를 미국 진입점에 연결 하 고 내부 네트워크에 대 한 연결이 예상 보다 훨씬 느립니다. 이 경우 최종 사용자는 수동으로 유럽 진입점에 연결 하 여 내부 네트워크에 대 한 연결을 향상 시킬 수 있습니다.  
  
> [!NOTE]  
> 최종 사용자가 진입점을 수동으로 선택 하면 클라이언트 컴퓨터는 자동 진입점 선택으로 되돌리지 않습니다. 즉, 수동으로 선택한 진입점을 연결할 수 없게 되 면 최종 사용자가 자동 진입점 선택으로 되돌리거나 다른 진입점을 수동으로 선택 해야 합니다.  
  
 Windows 7 클라이언트 컴퓨터는 멀티 사이트 배포에서 단일 진입점에 연결 하는 데 필요한 정보로 구성 됩니다. 여러 진입점에 대 한 정보를 동시에 저장할 수 없습니다. 예를 들어 Windows 7 클라이언트 컴퓨터는 미국 진입점에 연결 하도록 구성할 수 있지만 유럽 진입점에는 연결 하지 않을 수 있습니다. 미국 진입점에 연결할 수 없는 경우에는 진입점에 연결할 수 있을 때까지 Windows 7 클라이언트 컴퓨터가 내부 네트워크에 대 한 연결을 잃게 됩니다. 최종 사용자는 유럽 진입점에 대 한 연결 시도를 변경할 수 없습니다.  
  
## <a name="36-plan-prefixes-and-routing"></a><a name="bkmk_3_6_IPv6"></a>3.6 계획 접두사 및 라우팅  
  
### <a name="internal-ipv6-prefix"></a>내부 IPv6 접두사  
단일 원격 액세스 서버를 배포 하는 동안 내부 네트워크 IPv6 접두사는 멀티 사이트 배포에서 다음 사항을 확인 합니다.  
  
1.  단일 서버 원격 액세스 배포를 구성할 때 Active Directory 사이트를 모두 포함 한 경우 내부 네트워크 IPv6 접두사는 원격 액세스 관리 콘솔에 이미 정의 되어 있습니다.  
  
2.  멀티 사이트 배포에 대 한 추가 Active Directory 사이트를 만드는 경우 추가 사이트에 대 한 새 IPv6 접두사를 계획 하 고 원격 액세스에서 정의 해야 합니다. I p v 6이 내부 회사 네트워크에 배포 된 경우에는 원격 액세스 관리 콘솔 또는 PowerShell cmdlet을 사용 하 여 IPv6 접두사를 구성할 수 있습니다.  
  
### <a name="ipv6-prefix-for-directaccess-client-computers-ip-https-prefix"></a>DirectAccess 클라이언트 컴퓨터에 대 한 IPv6 접두사 (IP-HTTPS 접두사)  
  
1.  IPv6이 내부 회사 네트워크에 배포 된 경우 배포의 추가 진입점에서 DirectAccess 클라이언트 컴퓨터에 할당할 IPv6 접두사를 계획 해야 합니다.  
  
2.  각 진입점의 DirectAccess 클라이언트 컴퓨터에 할당할 IPv6 접두사가 서로 다르며 IPv6 접두사에 중복 되지 않았는지 확인 합니다.  
  
3.  IPv6이 회사 네트워크에 배포 되지 않은 경우 진입점을 추가할 때 각 진입점에 대 한 IP-HTTPS 접두사가 자동으로 선택 됩니다.  
  
### <a name="ipv6-prefix-for-vpn-clients"></a>VPN 클라이언트의 IPv6 접두사  
단일 원격 액세스 서버에 VPN을 배포한 경우 다음을 참고 하십시오.  
  
1.  진입점에 IPv6 VPN 접두사를 추가 하는 것은 회사 네트워크에 대 한 VPN 클라이언트 IPv6 연결을 허용 하려는 경우에만 필요 합니다.  
  
2.  VPN 접두사는 원격 액세스 관리 콘솔 또는 PowerShell cmdlet을 사용 하 여 진입점에만 구성할 수 있으며, IPv6이 내부 회사 네트워크에 배포 된 경우에는 진입점에서 VPN을 사용 하도록 설정할 수 있습니다.  
  
3.  VPN 접두사는 각 진입점에서 고유 해야 하며 다른 VPN 또는 IP-HTTPS 접두사와 겹치면 안 됩니다.  
  
4.  IPv6이 회사 네트워크에 배포 되지 않은 경우 진입점에 연결 하는 VPN 클라이언트에는 IPv6 주소가 할당 되지 않습니다.  
  
### <a name="routing"></a>라우팅  
멀티 사이트 배포에서 대칭 라우팅은 Teredo 및 ip-https를 사용 하 여 적용 됩니다. 회사 네트워크에 i p v 6을 배포할 때 다음 사항에 유의 하십시오.  
  
1. 각 진입점의 Teredo 및 IP-HTTPS 접두사는 회사 네트워크에서 연결 된 원격 액세스 서버로 라우팅할 수 있어야 합니다.  
  
2. 회사 네트워크 라우팅 인프라에서 경로를 구성 해야 합니다.  
  
3. 각 진입점에 대해 내부 네트워크에 1 ~ 3 개의 경로가 있어야 합니다.  
  
   1. IP-HTTPS 접두사-이 접두사는 관리자가 진입점 추가 마법사에서 선택 합니다.  
  
   2. VPN IPv6 접두사 (선택 사항). 진입점에 VPN을 사용 하도록 설정한 후이 접두사를 선택할 수 있습니다.  
  
   3. Teredo 접두사 (선택 사항). 이 접두사는 원격 액세스 서버가 외부 어댑터에서 두 개의 연속 된 공용 IPv4 주소로 구성 된 경우에만 해당 됩니다. 접두사는 주소 쌍의 첫 번째 공용 IPv4 주소를 기반으로 합니다. 예를 들어 외부 주소는 다음과 같습니다.  
  
      1. www\.xxx. yyy. zzz  
  
      2. www\.xxx. yyy. zzz + 1  
  
      그런 다음 구성 하는 Teredo 접두사는 2001:0: WWXX: YYZZ::/64입니다. 여기서 WWXX: YYZZ은 IPv4 주소 www\.xxx. yyy. zzz의 16 진수 표현입니다.  
  
      다음 스크립트를 사용 하 여 Teredo 접두사를 계산할 수 있습니다.  
  
      ```  
      $TeredoIPv4 = (Get-NetTeredoConfiguration).ServerName # Use for a Remote Access server that is already configured  
      $TeredoIPv4 = "20.0.0.1" # Use for an IPv4 address  
  
          [Byte[]] $TeredoServerAddressBytes = `  
          [System.Net.IPAddress]::Parse("2001::").GetAddressBytes()[0..3] + `  
          [System.Net.IPAddress]::Parse($TeredoIPv4).GetAddressBytes() + `  
          [System.Net.IPAddress]::Parse("::").GetAddressBytes()[0..7]  
  
      Write-Host "The server's Teredo prefix is $([System.Net.IPAddress]$TeredoServerAddressBytes)/64"  
      ```  
  
   4. 위의 모든 경로는 원격 액세스 서버의 내부 어댑터 또는 부하 분산 된 진입점에 대 한 내부 VIP (가상 IP) 주소에 대 한 IPv6 주소로 라우팅해야 합니다.  
  
> [!NOTE]  
> I p v 6이 회사 네트워크에 배포 되 고 원격 액세스 서버 관리가 DirectAccess를 통해 원격으로 수행 되는 경우, 다른 모든 진입점의 Teredo 및 IP-HTTPS 접두사에 대 한 경로를 각 원격 액세스 서버에 추가 해야 트래픽이 내부 네트워크에 전달 됩니다.  
  
### <a name="active-directory-site-specific-ipv6-prefixes"></a>Active Directory 사이트 관련 IPv6 접두사  
Windows 10 또는 Windows 8을 실행 하는 클라이언트 컴퓨터가 진입점에 연결 된 경우 클라이언트 컴퓨터는 진입점의 Active Directory 사이트에 즉시 연결 되며 진입점과 연결 된 IPv6 접두사로 구성 됩니다. 클라이언트 컴퓨터는 진입점에 연결할 때 우선 순위가 더 높은 IPv6 접두사 정책 테이블에서 동적으로 구성 되기 때문에 이러한 IPv6 접두사를 사용 하 여 리소스에 연결 하는 것이 기본 설정입니다.  
  
조직에서 사이트 관련 IPv6 접두사와 함께 Active Directory 토폴로지를 사용 하는 경우 (예: 내부 리소스 FQDN app.corp.com 각 위치의 사이트별 IP 주소를 사용 하 여 북아메리카와 유럽 모두에서 호스트 됨)에 의해 구성 되지 않습니다. 원격 액세스 콘솔을 사용 하는 기본 및 사이트별 IPv6 접두사는 각 진입점에 대해 구성 되지 않습니다. 이 선택적 시나리오를 사용 하도록 설정 하려는 경우 특정 진입점에 연결 하는 클라이언트 컴퓨터에서 선호 하는 특정 IPv6 접두사를 사용 하 여 각 진입점을 구성 해야 합니다. 이렇게 하려면 다음과 같이 합니다.  
  
1.  Windows 10 또는 Windows 8 클라이언트 컴퓨터에 사용 되는 각 GPO에 대해 DAEntryPointTableItem PowerShell cmdlet을 실행 합니다.  
  
2.  Cmdlet에 대 한 EntryPointRange 매개 변수를 사이트 관련 IPv6 접두사로 설정 합니다. 예를 들어, 사이트 관련 접두사 2001: db8:1: 1::/64 및 2001: db: 1:2::/64를 유럽 이라는 진입점에 추가 하려면 다음을 실행 합니다.  
  
    ```  
    $entryPointName = "Europe"  
    $prefixesToAdd = @("2001:db8:1:1::/64", "2001:db8:1:2::/64")  
    $clientGpos = (Get-DAClient).GpoName  
    $clientGpos | % { Get-DAEntryPointTableItem -EntryPointName $entryPointName -PolicyStore $_ | %{ Set-DAEntryPointTableItem -PolicyStore $_.PolicyStore -EntryPointName $_.EntryPointName -EntryPointRange ($_.EntryPointRange) + $prefixesToAdd}}  
    ```  
  
3.  EntryPointRange 매개 변수를 수정할 때는 IPsec 터널 끝점 및 DNS64 주소에 속하는 기존 128 비트 접두사를 제거 하지 않아야 합니다.  
  
## <a name="37-plan-the-transition-to-ipv6-when-multisite-remote-access-is-deployed"></a><a name="bkmk_3_7_TransitionIPv6"></a>3.7 멀티 사이트 원격 액세스를 배포할 때 i p v 6으로의 전환 계획  
많은 조직에서는 회사 네트워크에서 IPv4 프로토콜을 사용 합니다. 사용 가능한 IPv4 접두사가 고갈 되 면 많은 조직에서 IPv4 전용에서 IPv6 전용 네트워크로의 전환을 수행 합니다.  
  
이러한 전환은 다음과 같은 두 단계로 수행 될 가능성이 높습니다.  
  
1.  IPv4 전용에서 IPv6 + IPv4 회사 네트워크로  
  
2.  IPv6 + IPv4에서 IPv6 전용 회사 네트워크로  
  
각 파트에서 전환은 단계별로 수행 될 수 있습니다. 각 단계에서 네트워크의 서브넷 하나만 새 네트워크 구성으로 변경 될 수 있습니다. 따라서 DirectAccess 멀티 사이트 배포는 하이브리드 배포를 지원 하기 위해 필요 합니다. 예를 들어 일부 진입점은 IPv4 전용 서브넷에 속하고 다른 항목은 IPv6 + IPv4 서브넷에 속합니다. 또한 전환 프로세스 중의 구성 변경은 DirectAccess를 통해 클라이언트 연결을 중단 해서는 안 됩니다.  
  
### <a name="transition-from-an-ipv4-only-to-an-ipv6ipv4-corporate-network"></a><a name="TransitionIPv4toMixed"></a>IPv4 전용에서 IPv6 + IPv4 회사 네트워크로 전환  
IPv4 전용 회사 네트워크에 IPv6 주소를 추가 하는 경우 이미 배포 된 DirectAccess 서버에 IPv6 주소를 추가 하는 것이 좋습니다. 또한 IPv4 및 IPv6 주소를 모두 사용 하 여 부하 분산 된 클러스터에 진입점 또는 노드를 DirectAccess 배포에 추가 하려고 할 수 있습니다.  
  
원격 액세스를 사용 하면 ipv4 주소와 IPv6 주소가 둘 다 있는 서버를 원래 IPv4 주소로만 구성 된 배포에 추가할 수 있습니다. 이러한 서버는 IPv4 전용 서버로 추가 되 고 IPv6 주소는 DirectAccess에서 무시 됩니다. 따라서 조직에서는 이러한 새 서버에 대 한 기본 IPv6 연결의 이점을 활용할 수 없습니다.  
  
IPv6 + IPv4 배포에 대 한 배포를 변환 하 고 기본 IPv6 기능을 활용 하려면 DirectAccess를 다시 설치 해야 합니다. 다시 설치 전체에서 클라이언트 연결을 유지 하려면 IPv4 전용에서 이중 DirectAccess 배포를 사용 하는 IPv6 전용 배포로 전환을 참조 하세요.  
  
> [!NOTE]  
> Ipv4 전용 네트워크와 마찬가지로 혼합 된 IPv4 + IPv6 네트워크에서 클라이언트 DNS 요청을 확인 하는 데 사용 되는 DNS 서버의 주소는 원격 액세스 서버 자체에 배포 되 고 회사 DNS가 아닌 구성 된 DNS64를 사용 하 여 구성 해야 합니다.  
  
### <a name="transition-from-an-ipv6ipv4-to-an-ipv6-only-corporate-network"></a><a name="TransitionMixedtoIPv6"></a>IPv6 + IPv4에서 IPv6 전용 회사 네트워크로 전환  
DirectAccess를 사용 하면 배포의 첫 번째 원격 액세스 서버에서 원래 IPv4 및 IPv6 주소 또는 IPv6 주소만 모두 사용 하는 경우에만 IPv6 전용 진입점을 추가할 수 있습니다. 즉, DirectAccess를 다시 설치 하지 않고 단일 단계에서 IPv4 전용 네트워크에서 IPv6 전용 네트워크로 전환할 수 없습니다. IPv4 전용 네트워크에서 IPv6 전용 네트워크로 직접 전환 하려면 IPv4 전용에서 이중 DirectAccess 배포를 사용 하는 IPv6 전용 배포로 전환을 참조 하세요.  
  
IPv4 전용 배포에서 IPv6 + IPv4 배포로의 전환을 완료 한 후에는 IPv6 전용 네트워크로 전환할 수 있습니다. 그리고 전환 후에 다음을 확인 합니다.  
  
-   회사 네트워크에 IPv4 전용 백 엔드 서버가 남아 있는 경우에는 IPv6 전용 진입점을 통해 연결 하는 클라이언트에 연결할 수 없습니다.  
  
-   IPv6 전용 진입점을 IPv4 + IPv6 배포에 추가 하는 경우 새 서버에서 DNS64 및 NAT64를 사용 하도록 설정 되지 않습니다. 이러한 진입점에 연결 하는 클라이언트는 회사 DNS 서버를 사용 하도록 자동으로 구성 됩니다.  
  
-   배포 된 서버에서 IPv4 주소를 삭제 해야 하는 경우에는 DirectAccess 배포에서 서버를 제거 하 고 해당 IPv4 회사 네트워크 주소를 제거한 다음 배포에 다시 추가 해야 합니다.  
  
회사 네트워크에 대 한 클라이언트 연결을 지원 하려면 회사 DNS에서 IPv6 주소로 네트워크 위치 서버를 확인할 수 있는지 확인 해야 합니다. 또한 IPv4 주소를 추가로 설정할 수 있지만 반드시 필요한 것은 아닙니다.  
  
### <a name="transition-from-an-ipv4-only-to-an-ipv6-only-deployment-using-dual-directaccess-deployments"></a><a name="DualDeployment"></a>이중 DirectAccess 배포를 사용 하 여 IPv4 전용에서 IPv6 전용 배포로 전환  
DirectAccess 배포를 다시 설치 하지 않으면 IPv4 전용에서 IPv6 전용 회사 네트워크로 전환할 수 없습니다. 전환 하는 동안 클라이언트 연결을 유지 하기 위해 다른 DirectAccess 배포를 사용할 수 있습니다. 이중 배포는 첫 번째 전환 단계가 완료 될 때 (ipv4 + IPv6으로 업그레이드 된 IPv4 전용 네트워크), IPv6 전용 회사 네트워크로의 이후 전환을 준비 하려는 경우에 필요 합니다. 기본 IPv6 연결 혜택을 활용 orto. 이중 배포는 다음과 같은 일반적인 단계에서 설명 합니다.  
  
1.  두 번째 DirectAccess 배포를 설치 합니다. 새 서버에 DirectAccess를 설치 하거나 첫 번째 배포에서 서버를 제거 하 고 두 번째 배포에 사용할 수 있습니다.  
  
    > [!NOTE]  
    > 현재 서비스와 함께 추가 DirectAccess 배포를 설치 하는 경우 두 진입점이 동일한 클라이언트 접두사를 공유 하지 않는지 확인 합니다.  
    >   
    > 시작 마법사 또는 cmdlet `Install-RemoteAccess`를 사용 하 여 DirectAccess를 설치 하는 경우 원격 액세스는 배포의 첫 번째 진입점에 대 한 클라이언트 접두사를 자동으로 < IPv6 서브넷\_접두사 >: 1000::/64로 설정 합니다. 필요한 경우 접두사를 변경 해야 합니다.  
  
2.  첫 번째 배포에서 선택한 클라이언트 보안 그룹을 제거 합니다.  
  
3.  클라이언트 보안 그룹을 두 번째 배포에 추가 합니다.  
  
    > [!IMPORTANT]  
    > 프로세스 전체에서 클라이언트 연결을 유지 하려면 첫 번째 배포에서 제거한 후 즉시 두 번째 배포에 보안 그룹을 추가 해야 합니다. 이렇게 하면 클라이언트가 두 대 또는 0 개의 DirectAccess Gpo로 업데이트 되지 않습니다. 클라이언트는 클라이언트 GPO를 검색 하 고 업데이트 한 후 두 번째 배포를 사용 하 여 시작 합니다.  
  
4.  선택 사항: 첫 번째 배포에서 DirectAccess 진입점을 제거 하 고 두 번째 배포에 새 진입점으로 해당 서버를 추가 합니다.  
  
전환을 완료 한 후에는 첫 번째 DirectAccess 배포를 제거할 수 있습니다. 을 제거 하면 다음과 같은 문제가 발생할 수 있습니다.  
  
-   모바일 컴퓨터의 클라이언트만 지원 하도록 배포가 구성 된 경우 WMI 필터가 삭제 됩니다. 두 번째 배포의 클라이언트 보안 그룹에 데스크톱 컴퓨터를 포함 하는 경우에는 DirectAccess 클라이언트 GPO가 데스크톱 컴퓨터를 필터링 하지 않고 문제를 일으킬 수 있습니다. 모바일 컴퓨터 필터가 필요한 경우 [GPO에 대 한 WMI 필터 만들기](https://technet.microsoft.com/library/cc947846.aspx)의 지침에 따라 컴퓨터를 다시 만듭니다.  
  
-   두 배포가 원래 동일한 Active Directory 도메인에 생성 된 경우 localhost를 가리키는 DNS 프로브 항목이 삭제 되 고 클라이언트 연결 문제가 발생할 수 있습니다. 예를 들어 클라이언트는 Teredo가 아닌 IP-HTTPS를 사용 하 여 연결 하거나 DirectAccess 멀티 사이트 진입점 간을 전환할 수 있습니다. 이 경우 회사 DNS에 다음 DNS 항목을 추가 해야 합니다.  
  
    -   영역: 도메인 이름  
  
    -   이름: directaccess-Directaccess-corpconnectivityhost  
  
    -   IP 주소::: 1  
  
    -   형식: AAAA  
  
  
  


