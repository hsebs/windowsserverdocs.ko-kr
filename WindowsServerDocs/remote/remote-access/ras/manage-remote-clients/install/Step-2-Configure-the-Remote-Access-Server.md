---
title: 2 단계 원격 액세스 서버를 구성 합니다.
description: 이 항목은 Windows Server 2016에서 원격으로 DirectAccess 클라이언트 관리 가이드의 일부입니다.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: c0257b98-5633-4264-9df6-b6ffae80592c
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 7fce9eff4376e2d292622fe3a29fc8b391ad3bab
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859186"
---
# <a name="step-2-configure-the-remote-access-server"></a>2 단계 원격 액세스 서버를 구성 합니다.

>적용 대상: Windows Server(반기 채널), Windows Server 2016

이 항목에서는 DirectAccess 클라이언트의 원격 관리에 필요한 클라이언트 및 서버 설정을 구성 하는 방법에 설명 합니다. 에 설명 된 계획 단계를 완료 한 배포 단계를 시작 하기 전에 확인 [2 단계 원격 액세스 배포 계획](../plan/Step-2-Plan-the-Remote-Access-Deployment.md)합니다.  
  
|작업|설명|  
|----|--------|  
|원격 액세스 역할 설치|원격 액세스 역할을 설치합니다.|  
|배포 유형 구성|배포 유형을 DirectAccess 및 VPN, DirectAccess만 또는 VPN만으로 구성합니다.|  
|DirectAccess 클라이언트 구성|DirectAccess 클라이언트가 포함된 보안 그룹으로 원격 액세스 서버를 구성합니다.|  
|원격 액세스 서버 구성|원격 액세스 서버 설정을 구성 합니다.|  
|인프라 서버 구성|조직에서 사용되는 인프라 서버를 구성합니다.|  
|애플리케이션 서버 구성|인증 및 암호화를 요구 하도록 애플리케이션 서버를 구성 합니다.|  
|구성 요약 및 대체 GPO|원격 액세스 구성 요약을 확인하고 필요한 경우 GPO를 수정합니다.|  
  
> [!NOTE]  
> 이 항목에는 설명된 일부 절차를 자동화하는 데 사용할 수 있는 예제 Windows PowerShell cmdlet이 포함되어 있습니다. 자세한 내용은 참조 [Cmdlet를 사용 하 여](https://go.microsoft.com/fwlink/p/?linkid=230693)합니다.  
  
## <a name="install-the-remote-access-role"></a><a name="BKMK_Role"></a>원격 액세스 역할 설치  
조직에서은 원격 액세스 서버 역할을 하는 서버에서 원격 액세스 역할을 설치 해야 합니다.  
  
#### <a name="to-install-the-remote-access-role"></a>원격 액세스 역할을 설치하려면  
  
### <a name="to-install-the-remote-access-role-on-directaccess-servers"></a>DirectAccess 서버에 원격 액세스 역할을 설치 하려면  
  
1.  DirectAccess 서버의 서버 관리자 콘솔에는 **대시보드**, 클릭 **역할 및 기능 추가**합니다.  
  
2.  **다음** 을 세 번 클릭하여 서버 역할 선택 화면으로 이동합니다.  
  
3.  에 **서버 역할 선택** 대화 상자에서 **원격 액세스**, 를 클릭 하 고 **다음**합니다.  
  
4.  클릭 **다음** 3 번입니다.  
  
5.  에 **역할 서비스 선택** 대화 상자에서 **DirectAccess 및 VPN (RAS)** 클릭 하 고 **기능 추가**합니다.  
  
6.  선택 **라우팅**, 선택, **웹 응용 프로그램 프록시**, 클릭 **기능 추가**, 를 클릭 하 고 **다음**합니다.  
  
7. **다음**을 클릭한 후 **설치**를 클릭합니다.  
  
8.  **설치 진행률** 대화 상자에서 설치가 정상적으로 완료되었는지 확인하고 **닫기**를 클릭합니다.  
  
![Windows PowerShell](../../../../media/Step-2-Configure-the-Remote-Access-Server/PowerShellLogoSmall.gif)***<em>windows powershell 해당 명령</em>***  
  
다음 Windows PowerShell cmdlet은 이전 절차와 동일한 기능을 수행합니다. 서식 조건 때문에 각 cmdlet이 여러 줄로 자동 줄 바꿈되어 표시되더라도 한 줄에 입력합니다.  
  
```  
Install-WindowsFeature RemoteAccess -IncludeManagementTools  
```  
  
## <a name="configure-the-deployment-type"></a><a name="BKMK_Deploy"></a>배포 유형 구성  
원격 액세스 관리 콘솔에서 원격 액세스를 배포 하는 데 사용할 수 있는 세 가지 옵션이 있습니다.  
  
-   DirectAccess 및 VPN  
  
-   DirectAccess만  
  
-   VPN만  
  
> [!NOTE]  
> 이 가이드에서는 예제 절차에서 DirectAccess만 배포 방법을 사용합니다.  
  
#### <a name="to-configure-the-deployment-type"></a>배포 유형을 구성하려면  
  
1.  원격 액세스 서버에서 원격 액세스 관리 콘솔을 열고:에 **시작** 화면, 형식, 형식 **원격 액세스 관리 콘솔**, 한 다음 ENTER를 누릅니다. **사용자 계정 컨트롤** 대화 상자가 표시되면 원하는 작업이 표시되어 있는지 확인하고 **예**를 클릭합니다.  
  
2.  원격 액세스 관리 콘솔의 가운데 창에서 **원격 액세스 설정 마법사 실행**을 클릭합니다.  
  
3.  에 **원격 액세스 구성** 대화 상자, 선택 DirectAccess 및 VPN, directaccess만 배포할지 또는 VPN만 합니다.  
  
## <a name="configure-directaccess-clients"></a><a name="BKMK_Clients"></a>DirectAccess 클라이언트 구성  
DirectAccess를 사용하여 클라이언트 컴퓨터를 프로비전하려면 클라이언트 컴퓨터가 선택한 보안 그룹에 속해 있어야 합니다. DirectAccess를 구성한 후에 보안 그룹의 클라이언트 컴퓨터 원격 관리를 위한 DirectAccess 그룹 정책 개체 (Gpo)를 수신 하도록 프로 비전 됩니다.  
  
#### <a name="to-configure-directaccess-clients"></a>DirectAccess 클라이언트를 구성하려면  
  
1.  원격 액세스 관리 콘솔 중간 창의 **1단계 원격 클라이언트** 영역에서 **구성**을 클릭합니다.  
  
2.  DirectAccess 클라이언트 설치 마법사에서에 **배포 시나리오** 페이지에서 클릭 **만 원격 관리를 위한 DirectAccess 배포**, 를 클릭 하 고 **다음**합니다.  
  
3.  **그룹 선택** 페이지에서 **추가**를 클릭합니다.  
  
4.  에 **그룹 선택** 대화 상자를 클릭 한 다음 및 DirectAccess 클라이언트 컴퓨터를 포함 하는 보안 그룹을 선택 **다음**합니다.  
  
5.  **네트워크 연결 길잡이** 페이지에서 다음을 수행합니다.  
  
    -   테이블에는 내부 네트워크에 대 한 연결을 확인 하는 데 사용할 리소스를 추가 합니다. 구성된 리소스가 없는 경우 기본 웹 검색이 자동으로 만들어집니다. 엔터프라이즈 네트워크로 연결을 확인 하기 위한 웹 검색 위치를 구성할 때 하나 이상의 HTTP 기반 검색이 구성 되어 있는지 확인 합니다. 충분 하지 않습니다만 ping 프로브를 구성 하 고는 정확 하지 않은 연결 상태 확인 될 수 있습니다. 즉, ping IPsec에서 제외 됩니다. 결과적으로, ping은 IPsec 터널이 제대로 설정 되어 있다고을 확인 하지 않습니다.  
  
    -   연결 문제가 발생한 경우 사용자가 정보를 보낼 수 있는 지원 센터 전자 메일 주소를 추가합니다.  
  
    -   DirectAccess 연결 이름을 제공합니다.  
  
    -   필요한 경우 **DirectAccess 클라이언트가 로컬 이름 확인을 사용하도록 허용** 확인란을 선택합니다.  
  
        > [!NOTE]  
        > 로컬 이름 확인 기능을 사용 하 고 NCA는 실행 중인 사용자는 DirectAccess 클라이언트 컴퓨터에 구성 되어 있는 DNS 서버를 사용 하 여 이름을 확인할 수 있습니다.  
  
6.  **마침**을 클릭합니다.  
  
## <a name="configure-the-remote-access-server"></a><a name="BKMK_Server"></a>원격 액세스 서버 구성  
원격 액세스를 배포 하려면 다음 사용 하 여 원격 액세스 서버 역할을 할 서버를 구성 해야 합니다.  
  
1.  올바른 네트워크 어댑터  
  
2.  클라이언트 컴퓨터 (ConnectTo 주소) 연결할 수는 원격 액세스 서버에 대 한 공용 URL  
  
3.  ConnectTo 주소와 일치 하는 주체는 IP-HTTPS 인증서  
  
4.  IPv6 설정  
  
5.  클라이언트 컴퓨터 인증  
  
#### <a name="to-configure-the-remote-access-server"></a>원격 액세스 서버를 구성하려면  
  
1.  원격 액세스 관리 콘솔의 가운데 창에 있는 **2단계 원격 액세스 서버** 영역에서 **구성**을 클릭합니다.  
  
2.  원격 액세스 서버 설치 마법사의 **네트워크 토폴로지** 페이지에서 조직에서 사용할 배포 토폴로지를 클릭합니다. **클라이언트가 원격 액세스 서버에 연결하는 데 사용할 공개 이름 또는 IPv4 주소 입력**에 배포의 공개 이름(이 이름이 IP-HTTPS 인증서의 주체 이름(예: edge1.contoso.com)과 일치)을 입력하고 **다음**을 클릭합니다.  
  
3.  에 **네트워크 어댑터** 페이지에서 마법사는 자동으로 검색 합니다.  
  
    -   네트워크 배포에 대 한 네트워크 어댑터입니다. 마법사가 올바른 네트워크 어댑터를 검색하지 못한 경우 수동으로 올바른 어댑터를 선택합니다.  
  
    -   IP-HTTPS 인증서입니다. 이 설정은 마법사의 이전 단계에서 설정한 배포에 대 한 공용 이름에 기반 합니다. 마법사가 올바른 IP-HTTPS 인증서를 검색 하는 경우 클릭 **찾아보기** 수동으로 올바른 인증서를 선택 합니다.  
  
4.  **다음**을 클릭합니다.  
  
5.  에 **접두사 구성** (이 페이지는 i p v 6가 내부 네트워크에서 검색 된 경우에 볼 수만) 페이지는 마법사에는 내부 네트워크에 사용 되는 IPv6 설정을 자동으로 검색 합니다. 배포에 추가 접두사가 필요한 경우 내부 네트워크의 IPv6 접두사, DirectAccess 클라이언트 컴퓨터에 할당할 IPv6 접두사 및 VPN 클라이언트 컴퓨터에 할당할 IPv6 접두사를 구성합니다.  
  
6.  **인증** 페이지에서 다음을 수행합니다.  
  
    -   멀티 사이트 및 2단계 인증 배포의 경우 컴퓨터 인증서 인증을 사용해야 합니다. 선택 된 **컴퓨터 인증서를 사용 하 여** 확인란 컴퓨터 인증서 인증을 사용 하 고 IPsec 루트 인증서를 선택 합니다.  
  
    -   DirectAccess를 통해 연결 하려면 Windows 7을 실행 하는 클라이언트 컴퓨터를 설정 하려면 선택은 **DirectAccess를 통해 연결 하도록 클라이언트 컴퓨터를 Windows 7을 사용 하도록 설정** 확인란입니다. 또한 이 유형의 배포에서는 컴퓨터 인증서 인증을 사용해야 합니다.  
  
7.  **마침**을 클릭합니다.  
  
## <a name="configure-the-infrastructure-servers"></a><a name="BKMK_Infra"></a>인프라 서버 구성  
원격 액세스 배포에서 인프라 서버를 구성 하려면 다음을 구성 해야 합니다.  
  
-   네트워크 위치 서버  
  
-   DNS 설정, DNS를 포함 하 여 접미사 검색 목록  
  
-   원격 액세스에서 자동으로 검색 되지 않은 모든 관리 서버  
  
#### <a name="to-configure-the-infrastructure-servers"></a>인프라 서버를 구성하려면  
  
1.  원격 액세스 관리 콘솔의 가운데 창에 있는 **3단계 인프라 서버** 영역에서 **구성**을 클릭합니다.  
  
2.  인프라 서버 설치 마법사의 **네트워크 위치 서버** 페이지에서 배포에 포함된 네트워크 위치 서버의 위치에 해당하는 옵션을 클릭합니다.  
  
    -   네트워크 위치 서버가 원격 웹 서버에 있으면 URL을 입력 하 고 클릭 한 다음 **유효성 검사** 계속 하기 전에 합니다.  
  
    -   네트워크 위치 서버가 원격 액세스 서버에 있으면 **찾아보기**를 클릭하여 관련 인증서를 찾은 후 **다음**을 클릭합니다.  
  
3.  에 **DNS** 페이지 테이블에 입력 추가 이름 접미사 적용 되는 이름 확인 정책 테이블 () nrpt 예외로 합니다. 로컬 이름 확인 옵션을 선택하고 **다음**을 클릭합니다.  
  
4.  에 **DNS 접미사 검색 목록** 페이지에서 원격 액세스 서버 배포의 도메인 접미사를 자동으로 검색 합니다. 사용 하는 **추가** 및 **제거** 단추를 사용 하려는 도메인 접미사 목록을 만듭니다. 새 도메인 접미사를 추가하려면 **새 접미사**에 접미사를 입력하고 **추가**를 클릭합니다. **다음**을 클릭합니다.  
  
5.  에 **관리** 페이지 자동으로 검색 되지 않는 관리 서버를 추가 하 고 클릭 한 다음 **다음**합니다. 원격 액세스는 도메인 컨트롤러 및 Configuration Manager 서버를 자동으로 추가 합니다.  
  
6.  **마침**을 클릭합니다.  
  
## <a name="configure-application-servers"></a><a name="BKMK_App"></a>응용 프로그램 서버 구성  
전체 원격 액세스 배포에서 애플리케이션 서버 구성은 선택적 작업입니다. DirectAccess 클라이언트의 원격 관리를 위해이 시나리오에서는 애플리케이션 서버는 사용 되지 않습니다 하 고이 단계는 활성화 된 것을 나타내기 위해 회색입니다. 클릭 **마침** 구성을 적용 합니다.  
  
## <a name="configuration-summary-and-alternate-gpos"></a><a name="BKMK_GPO"></a>구성 요약 및 대체 Gpo  
원격 액세스 구성이 완료되면 **원격 액세스 검토**가 표시됩니다. 다음을 포함하여 이전에 선택한 모든 설정을 검토할 수 있습니다.  
  
-   **GPO 설정**  
  
    DirectAccess 서버 GPO 이름 및 클라이언트 GPO 이름이 나열 됩니다. 클릭할 수는 **변경** 링크 옆에 **GPO 설정을** GPO 설정을 수정 하는 제목입니다.  
  
-   **원격 클라이언트**  
  
    보안 그룹, 연결 검증 도구, DirectAccess 연결 이름 등의 DirectAccess 클라이언트 구성이 표시 됩니다.  
  
-   **원격 액세스 서버**  
  
    공개 이름 및 주소, 네트워크 어댑터 구성 및 인증서 정보를 포함 하 여 DirectAccess 구성이 표시 됩니다.  
  
-   **인프라 서버**  
  
    이 목록에는 네트워크 위치 서버 URL, DirectAccess 클라이언트에서 사용하는 DNS 접미사 및 관리 서버 정보가 포함됩니다.  
  
## <a name="see-also"></a><a name="BKMK_Links"></a>참고 항목  
  
-   [3 단계: 배포 확인](Step-3-Verify-the-Deployment_2.md)  
  
  


