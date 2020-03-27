---
title: 6 단계 NAT 장치 뒤에서 DirectAccess 클라이언트 연결 테스트
description: 이 항목은 테스트 랩 가이드-windows Server 2016 용 Windows NLB를 사용 하는 클러스터의 DirectAccess 시연에 포함 되어 있습니다.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aded2881-99ed-4f18-868b-b765ab926597
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 82e9720bc09593ea7b8d7af4b2102ac3e3ba3e3d
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314708"
---
# <a name="step-6-test-directaccess-client-connectivity-from-behind-a-nat-device"></a>6 단계 NAT 장치 뒤에서 DirectAccess 클라이언트 연결 테스트

>적용 대상: Windows Server(반기 채널), Windows Server 2016

DirectAccess 클라이언트는 NAT 장치 또는 웹 프록시 서버 뒤에서 인터넷에 연결된 경우 Teredo 또는 IP-HTTPS를 사용하여 원격 액세스 서버에 연결합니다. 

NAT 장치에서 원격 액세스 서버의 공용 IP 주소에 아웃 바운드 UDP 포트 3544을 사용 하도록 설정 하면 Teredo가 사용 됩니다. Teredo 액세스를 사용할 수 없는 경우 DirectAccess 클라이언트는 기존 SSL 포트를 통해 방화벽이나 웹 프록시 서버에 액세스할 수 있도록 하는 IP-HTTPS(아웃바운드 TCP 포트 443 사용)로 대체합니다. 

웹 프록시 인증이 필요한 경우에는 IP-HTTPS 연결에 실패합니다. 또한 웹 프록시에서 아웃바운드 SSL 검사를 수행하는 경우에도 IP-HTTPS 연결에 실패합니다. HTTPS 세션은 원격 액세스 서버가 아니라 웹 프록시에서 종료되기 때문입니다. 이 섹션에서는 이전 섹션에서 6to4 연결을 사용하여 연결할 때 수행한 동일한 테스트를 수행합니다.  
  
다음 절차는 두 클라이언트 컴퓨터 모두에서 수행됩니다.  
  
1. Teredo 연결을 테스트 합니다. 첫 번째 테스트 집합은 DirectAccess 클라이언트가 Teredo를 사용 하도록 구성 된 경우에 수행 됩니다. NAT 장치에서 UDP 포트 3544에 대한 아웃바운드 액세스를 허용하는 경우에는 이 설정이 자동으로 구성됩니다.  
  
2. IP-HTTPS 연결을 테스트 합니다. 두 번째 테스트 집합은 DirectAccess 클라이언트가 IP-HTTPS를 사용 하도록 구성 된 경우에 수행 됩니다. IP-HTTPS 연결을 확인하려면 클라이언트에서 Teredo를 사용하지 않도록 설정해야 합니다.  
  
> [!TIP]  
> 이러한 절차를 수행 하기 전에 Internet Explorer 캐시를 지워 연결을 테스트 하 고 캐시에서 웹 사이트 페이지를 검색 하지 않도록 하는 것이 좋습니다.  
  
## <a name="prerequisites"></a>필수 조건

이러한 테스트를 수행하기 전에 CLIENT1을 인터넷 스위치에서 분리하여 Homenet 스위치에 연결합니다. 현재 네트워크를 정의할 네트워크 유형을 묻는 메시지가 표시되면 **홈 네트워크**를 선택합니다.  
  
EDGE1 및 EDGE2를 시작합니다(아직 실행하지 않은 경우).  
  
## <a name="test-teredo-connectivity"></a>Teredo 연결 테스트  
  
1. CLIENT1에서 관리자 권한 Windows PowerShell 창을 열고 **ipconfig/all** 을 입력 한 다음 enter 키를 누릅니다.  
  
2. ipconfig 명령의 출력을 검사합니다.  
  
   이제 CLIENT1이 NAT 장치 뒤에서 인터넷에 연결되고 프라이빗 IPv4 주소가 할당됩니다. DirectAccess 클라이언트가 NAT 장치 뒤에 있고 프라이빗 IPv4 주소가 할당된 경우 기본 설정 IPv6 전환 기술은 Teredo입니다. ipconfig 명령의 출력을 확인하는 경우 Teredo 주소와 일치하도록 2001:로 시작하는 IP 주소를 사용하여 터널 어댑터 Teredo 터널링 의사(pseudo)-인터페이스 섹션을 검토한 다음 Microsoft Teredo 터널링 어댑터에 대한 설명을 검토합니다. Teredo 섹션이 표시되지 않으면 **netsh interface Teredo set state enterpriseclient** 명령을 사용하여 Teredo를 사용하도록 설정한 후 ipconfig 명령을 다시 실행합니다. Teredo 터널 어댑터에 대해 나열된 기본 게이트웨이는 표시되지 않습니다.  
  
3. Windows PowerShell 창에서 **ipconfig/flushdns** 를 입력 하 고 enter 키를 누릅니다.  
  
   그러면 클라이언트 컴퓨터가 인터넷에 연결된 이후 클라이언트 DNS 캐시에 남아 있을 수 있는 이름 확인 항목이 플러시됩니다.  
  
4. Windows PowerShell 창에서 **get-dnsclientnrptpolicy** 를 입력 하 고 enter 키를 누릅니다.  
  
   NRPT(이름 확인 정책 테이블)에 대한 현재 설정이 출력에 표시됩니다. 이러한 설정은 원격 액세스 DNS 서버에서 IPv6 주소 2001:db8:1::2를 사용하여 .corp.contoso.com에 대한 모든 연결을 확인해야 함을 나타냅니다. 또한 nls.corp.contoso.com이라는 이름에 대한 예외가 있음을 나타내는 NRPT 항목을 확인합니다. 예외 목록에 있는 이름에는 원격 액세스 DNS 서버에서 응답하지 않습니다. 원격 액세스 DNS 서버 IP 주소(이 예제의 경우 2001:db8:1::2)를 ping하여 원격 액세스 서버에 대한 연결을 확인할 수 있습니다.  
  
5. Windows PowerShell 창에서 **ping app1** 을 입력 하 고 enter 키를 누릅니다. IPv6 주소 APP1, 2001:db8:1::3의 응답이 표시됩니다.  
  
6. Windows PowerShell 창에서 **ping app2** 을 입력 하 고 enter 키를 누릅니다. EDGE1에서 APP2에 할당한 NAT64 주소(이 예제의 경우 fdc9:9f4e:eb1b:7777::a00:4)의 응답이 표시됩니다.  
  
7. 다음 절차를 수행 하려면 Windows PowerShell 창을 열어 둡니다.  
  
8. Internet Explorer를 열고 Internet Explorer 주소 표시줄에 **https://app1/** 를 입력 한 다음 enter 키를 누릅니다. APP1의 기본 IIS 웹 사이트가 표시됩니다.  
  
9. Internet Explorer 주소 표시줄에 **https://app2/** 를 입력 하 고 enter 키를 누릅니다. APP2의 기본 IIS 웹 사이트가 표시됩니다.  
  
10. **시작** 화면에서<strong>\\\App2\Files</strong>를 입력 한 다음 enter 키를 누릅니다. 새 텍스트 문서 파일을 두 번 클릭합니다. 이는 SMB를 사용하여 IPv4 전용 호스트의 리소스를 가져오는 IPv4 전용 서버에 연결할 수 있음을 보여 줍니다.  
  
## <a name="test-ip-https-connectivity"></a>IP-HTTPS 연결 테스트  
  
1. 관리자 권한 Windows PowerShell 창을 열고 **netsh interface teredo set state disabled** 를 입력 한 다음 enter 키를 누릅니다. 그러면 클라이언트 컴퓨터에서 Teredo가 사용하지 않도록 설정되고, 자체적으로 IP-HTTPS를 사용하도록 구성할 수 있게 됩니다. 명령이 완료되면 **확인** 응답이 나타납니다.  
  
2. Windows PowerShell 창에서 **ipconfig/all** 을 입력 하 고 enter 키를 누릅니다.  
  
3. ipconfig 명령의 출력을 검사합니다. 이제 이 컴퓨터가 NAT 장치 뒤에서 인터넷에 연결되고 프라이빗 IPv4 주소가 할당됩니다. Teredo가 사용하지 않도록 설정되고 DirectAccess 클라이언트가 IP-HTTPS로 대체합니다. ipconfig 명령의 출력을 확인하는 경우 DirectAccess를 설정할 때 구성된 접두사에 따른 IP-HTTPS 주소와 일치하도록 2001:db8:1:100로 시작하는 IP 주소를 사용하여 터널 어댑터 iphttpsinterface 섹션을 검토합니다. IP-HTTPS 터널 어댑터에 대해 나열된 기본 게이트웨이는 표시되지 않습니다.  
  
4. Windows PowerShell 창에서 **ipconfig/flushdns** 를 입력 하 고 enter 키를 누릅니다. 그러면 클라이언트 컴퓨터가 corpnet에 연결된 이후 클라이언트 DNS 캐시에 남아 있을 수 있는 이름 확인 항목이 플러시됩니다.  
  
5. Windows PowerShell 창에서 **ping app1** 을 입력 하 고 enter 키를 누릅니다. IPv6 주소 APP1, 2001:db8:1::3의 응답이 표시됩니다.  
  
6. Windows PowerShell 창에서 **ping app2** 을 입력 하 고 enter 키를 누릅니다. EDGE1에서 APP2에 할당한 NAT64 주소(이 예제의 경우 fdc9:9f4e:eb1b:7777::a00:4)의 응답이 표시됩니다.  
  
7. Internet Explorer를 열고 Internet Explorer 주소 표시줄에 **https://app1/** 를 입력 한 다음 enter 키를 누릅니다. APP1의 기본 IIS 사이트가 표시됩니다.  
  
8. Internet Explorer 주소 표시줄에 **https://app2/** 를 입력 하 고 enter 키를 누릅니다. APP2의 기본 IIS 웹 사이트가 표시됩니다.  
  
9. **시작** 화면에서<strong>\\\App2\Files</strong>를 입력 한 다음 enter 키를 누릅니다. 새 텍스트 문서 파일을 두 번 클릭합니다. 이는 SMB를 사용하여 IPv4 전용 호스트의 리소스를 가져오는 IPv4 전용 서버에 연결할 수 있음을 보여 줍니다.
