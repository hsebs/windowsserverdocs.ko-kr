---
title: 2 단계 고급 DirectAccess 서버 구성
description: 이 항목은 Windows Server 2016에 대 한 고급 설정을 사용 하 여 단일 DirectAccess 서버 배포 가이드의 일부입니다.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35afec8e-39a4-463b-839a-3c300ab01174
ms.author: lizross
author: eross-msft
ms.openlocfilehash: bf740143c4d9c855df080addd75fdaeee6a1ceac
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309109"
---
# <a name="step-2-configure-advanced-directaccess-servers"></a>2 단계 고급 DirectAccess 서버 구성

>적용 대상: Windows Server(반기 채널), Windows Server 2016

이 항목에서는 IPv4 및 IPv6 혼합 환경에서 단일 원격 액세스 서버를 사용하는 고급 원격 액세스 배포에 필요한 클라이언트 및 서버 설정을 구성하는 방법에 대해 설명합니다. 에 설명 된 계획 단계를 완료 한 배포 단계를 시작 하기 전에 확인 [고급 DirectAccess 배포 계획](Plan-an-Advanced-DirectAccess-Deployment.md)합니다.  
  
|작업|설명|  
|----|--------|  
|2.1. 원격 액세스 역할 설치|원격 액세스 역할을 설치합니다.|  
|2.2. 배포 유형 구성|배포 유형을 DirectAccess 및 VPN, DirectAccess만 또는 VPN만으로 구성합니다.|  
|[고급 DirectAccess 배포 계획](Plan-an-Advanced-DirectAccess-Deployment.md)|DirectAccess 클라이언트가 포함된 보안 그룹으로 원격 액세스 서버를 구성합니다.|  
|2.4. 원격 액세스 서버 구성|원격 액세스 서버 설정을 구성합니다.|  
|2.5. 인프라 서버 구성|조직에서 사용되는 인프라 서버를 구성합니다.|  
|2.6. 응용 프로그램 서버 구성|인증 및 암호화를 요구하도록 응용 프로그램 서버를 구성합니다.|  
|2.7. 구성 요약 및 대체 GPO|원격 액세스 구성 요약을 확인하고 필요한 경우 GPO를 수정합니다.|  
|2.8. Windows PowerShell을 사용하여 원격 액세스 서버를 구성하는 방법|Windows PowerShell을 사용 하 여 원격 액세스를 구성 합니다.|  
  
> [!NOTE]  
> 이 항목에는 설명된 일부 절차를 자동화하는 데 사용할 수 있는 예제 Windows PowerShell cmdlet이 포함되어 있습니다. 자세한 내용은 참조 [Cmdlet를 사용 하 여](https://go.microsoft.com/fwlink/p/?linkid=230693)합니다.  
  
## <a name="21-install-the-remote-access-role"></a><a name="BKMK_Role"></a>2.1. 원격 액세스 역할 설치  
원격 액세스를 배포하려면 조직에서 원격 액세스 서버로 사용할 서버에 원격 액세스 역할을 설치해야 합니다.  
  
#### <a name="to-install-the-remote-access-role"></a>원격 액세스 역할을 설치하려면  
  
1.  원격 액세스 서버의 서버 관리자 콘솔에는 **대시보드**, 클릭 **역할 및 기능 추가**합니다.  
  
2.  **다음**을 세 번 클릭하여 **서버 역할 선택** 화면으로 이동합니다.  
  
3.  **서버 역할 선택** 페이지에서 **원격 액세스**를 선택하고 **기능 추가**를 클릭한 후 **다음**을 클릭합니다.  
  
4.  **다음**을 5번 클릭합니다.  
  
5.  **설치 선택 확인** 페이지에서 **설치**를 클릭합니다.  
  
6.  **설치 진행률** 페이지에서 설치가 완료되었는지 확인하고 **닫기**를 클릭합니다.  
  
![설치 진행률 성공](../../../media/Step-2-Configuring-DirectAccess-Servers/PowerShellLogoSmall.gif)***<em>Windows PowerShell 해당 명령</em>***  
  
다음 Windows PowerShell cmdlet은 이전 절차와 동일한 기능을 수행합니다. 서식 조건 때문에 각 cmdlet이 여러 줄로 자동 줄 바꿈되어 표시되더라도 한 줄에 입력합니다.  
  
```  
Install-WindowsFeature RemoteAccess -IncludeManagementTools  
```  
  
## <a name="22-configure-the-deployment-type"></a><a name="BKMK_Deploy"></a>2.2. 배포 유형 구성  
원격 액세스 관리 콘솔을 사용하여 세 가지 방법으로 원격 액세스를 배포할 수 있습니다.  
  
-   DirectAccess 및 VPN  
  
-   DirectAccess만  
  
-   VPN만  
  
이 가이드에서는 예제 절차에서 DirectAccess만 배포를 사용합니다.  
  
#### <a name="to-configure-the-deployment-type"></a>배포 유형을 구성하려면  
  
1.  원격 액세스 서버에서 원격 액세스 관리 콘솔을 열고:에 **시작** 화면에서 입력**RAMgmtUI.exe**, 한 다음 ENTER를 누릅니다. **사용자 계정 컨트롤** 대화 상자가 표시되면 원하는 작업이 표시되어 있는지 확인하고 **예**를 클릭합니다.  
  
2.  원격 액세스 관리 콘솔의 가운데 창에서 **원격 액세스 설정 마법사 실행**을 클릭합니다.  
  
3.  **원격 액세스 구성** 대화 상자에서 DirectAccess 및 VPN을 배포할지, DirectAccess만 배포할지 또는 VPN만 배포할지 클릭합니다.  
  
## <a name="23-configure-directaccess-clients"></a><a name="BKMK_Clients"></a>2.3. DirectAccess 클라이언트 구성  
DirectAccess를 사용하여 클라이언트 컴퓨터를 프로비전하려면 클라이언트 컴퓨터가 선택한 보안 그룹에 속해 있어야 합니다. DirectAccess를 구성한 후 해당 보안 그룹의 클라이언트 컴퓨터는 DirectAccess GPO(그룹 정책 개체)를 수신하도록 프로비전됩니다. 클라이언트 액세스 및 원격 관리용 또는 원격 관리 전용으로 DirectAccess를 구성할 수 있는 배포 시나리오를 구성할 수도 있습니다.  
  
#### <a name="to-configure-directaccess-clients"></a>DirectAccess 클라이언트를 구성하려면  
  
1.  원격 액세스 관리 콘솔 중간 창의 **1단계 원격 클라이언트** 영역에서 **구성**을 클릭합니다.  
  
2.  DirectAccess 클라이언트 설치 마법사의 **배포 시나리오** 페이지에서 조직에서 사용할 배포 시나리오(**전체 DirectAccess** 또는 **원격 관리만**)를 클릭하고 **다음**을 클릭합니다.  
  
3.  **그룹 선택** 페이지에서 **추가**를 클릭합니다.  
  
4.  **그룹 선택** 대화 상자에서 DirectAccess 클라이언트 컴퓨터가 포함된 보안 그룹을 선택합니다.  
  
    > [!NOTE]  
    > 보안 그룹이 원격 액세스 서버와 다른 포리스트에 있는 경우 원격 액세스 설치 마법사를 완료 한 후 **작업** 창에서 **관리 서버 새로 고침** 을 클릭 하 여 새 포리스트의 도메인 컨트롤러 및 Configuration Manager 서버를 검색 합니다.  
  
5.  필요한 경우 **이동 컴퓨터에만 DirectAccess 사용** 확인란을 선택하여 이동 컴퓨터에서만 내부 네트워크에 액세스할 수 있도록 허용합니다.  
  
6.  필요한 경우 **강제 터널링 사용** 확인란을 선택하여 모든 클라이언트 트래픽(내부 네트워크 및 인터넷으로의 트래픽)을 원격 액세스 서버를 통해 라우팅합니다.  
  
7.  **다음**을 클릭합니다.  
  
8.  **네트워크 연결 길잡이** 페이지에서 다음을 수행합니다.  
  
    -   테이블에서 내부 네트워크 연결을 확인하는 데 사용할 리소스를 추가합니다. 구성된 리소스가 없는 경우 기본 웹 검색이 자동으로 만들어집니다.  
  
        > [!CAUTION]  
        > 엔터프라이즈 네트워크 연결을 확인하기 위한 웹 검색 위치를 구성하려면 적어도 하나의 HTTP 기반 검색이 구성되어 있어야 합니다. **ping** 검색을 구성하는 것만으로는 부족하며 연결 상태 확인이 부정확할 수 있습니다. **ping**에서는 IPsec이 제외되므로 IPsec 터널이 제대로 설정되었는지 확인할 수 없기 때문입니다.  
  
    -   연결 문제가 발생한 경우 사용자가 정보를 보낼 수 있는 지원 센터 전자 메일 주소를 추가합니다.  
  
    -   DirectAccess 연결 이름을 제공합니다. 이 이름은 사용자가 알림 영역에서 네트워크 아이콘을 클릭하면 네트워크 목록에 나타납니다.  
  
    -   필요한 경우 **DirectAccess 클라이언트가 로컬 이름 확인을 사용하도록 허용** 확인란을 선택합니다.  
  
        > [!NOTE]  
        > 로컬 이름을 확인하는 경우 네트워크 연결 길잡이를 실행하는 사용자는 DirectAccess 클라이언트 컴퓨터에 구성된 DNS 서버를 사용하여 이름을 확인하도록 선택할 수 있습니다.  
  
9. **마침**을 클릭합니다.  
  
## <a name="24-configure-the-remote-access-server"></a><a name="BKMK_Server"></a>2.4. 원격 액세스 서버 구성  
원격 액세스를 배포하려면 올바른 네트워크 어댑터, 클라이언트 컴퓨터에서 연결할 수 있는 원격 액세스 서버의 공용 URL(ConnectTo 주소), 주체가 ConnectTo 주소와 일치하는 IP-HTTPS 인증서, IPv6 설정 및 클라이언트 컴퓨터 인증으로 원격 액세스 서버를 구성해야 합니다.  
  
#### <a name="to-configure-the-remote-access-server"></a>원격 액세스 서버를 구성하려면  
  
1.  원격 액세스 관리 콘솔의 가운데 창에 있는 **2단계 원격 액세스 서버** 영역에서 **구성**을 클릭합니다.  
  
2.  원격 액세스 서버 설치 마법사의 **네트워크 토폴로지** 페이지에서 조직에서 사용할 배포 토폴로지를 클릭합니다. **클라이언트가 원격 액세스 서버에 연결하는 데 사용할 공개 이름 또는 IPv4 주소 입력**에 배포의 공개 이름(이 이름이 IP-HTTPS 인증서의 주체 이름(예: edge1.contoso.com)과 일치)을 입력하고 **다음**을 클릭합니다.  
  
3.  **네트워크 어댑터** 페이지에서 마법사가 배포의 네트워크에 사용되는 네트워크 어댑터를 자동으로 검색합니다. 마법사가 올바른 네트워크 어댑터를 검색하지 못한 경우 수동으로 올바른 어댑터를 선택합니다. 또한 마법사는 마법사의 이전 단계에서 설정한 배포의 공개 이름을 기반으로 IP-HTTPS 인증서를 자동으로 검색합니다. 마법사가 올바른 IP-HTTPS 인증서를 검색하지 못한 경우 **찾아보기**를 클릭하여 올바른 인증서를 수동으로 선택하고 **다음**을 클릭합니다.  
  
4.  **접두사 구성** 페이지(IPv6이 내부 네트워크에 배포된 경우에만 표시됨)에서 마법사가 내부 네트워크에 사용되는 IPv6 설정을 자동으로 검색합니다. 배포에 추가 접두사가 필요한 경우 내부 네트워크의 IPv6 접두사, DirectAccess 클라이언트 컴퓨터에 할당할 IPv6 접두사 및 VPN 클라이언트 컴퓨터에 할당할 IPv6 접두사를 구성합니다.  
  
    > [!NOTE]  
    > 세미콜론으로 구분된 목록(예: 2001:db8:1::/48;2001:db8:2::/48)을 사용하여 여러 내부 IPv6 접두사를 지정할 수 있습니다.  
  
5.  **인증** 페이지에서 다음을 수행합니다.  
  
    -   **사용자 인증**에서 **Active Directory 자격 증명**을 클릭합니다. 2단계 인증을 사용하여 배포를 구성하려면 **2단계 인증**을 클릭합니다. 자세한 내용은 [OTP 인증을 사용하여 원격 액세스 배포](https://technet.microsoft.com/library/hh831379.aspx)를 참조하세요.  
  
    -   멀티 사이트 및 2단계 인증 배포의 경우 컴퓨터 인증서 인증을 사용해야 합니다. **컴퓨터 인증서 사용** 확인란을 선택하여 컴퓨터 인증서 인증을 사용하고 IPsec 루트 인증서를 선택합니다.  
  
    -   DirectAccess를 통해 연결 하도록 Windows 7 클라이언트 컴퓨터를 사용 하도록 설정 하려면 선택은 **DirectAccess를 통해 연결 하도록 클라이언트 컴퓨터를 Windows 7을 사용 하도록 설정** 확인란입니다.  
  
        > [!NOTE]  
        > 또한 이 유형의 배포에서는 컴퓨터 인증서 인증을 사용해야 합니다.  
  
6.  **마침**을 클릭합니다.  
  
## <a name="25-configure-the-infrastructure-servers"></a><a name="BKMK_Infra"></a>2.5. 인프라 서버 구성  
원격 액세스 배포에서 인프라 서버를 구성하려면 네트워크 위치 서버, DNS 설정(DNS 접미사 검색 목록 포함) 및 원격 액세스에서 자동으로 검색되지 않는 관리 서버를 구성해야 합니다.  
  
#### <a name="to-configure-the-infrastructure-servers"></a>인프라 서버를 구성하려면  
  
1.  원격 액세스 관리 콘솔의 가운데 창에 있는 **3단계 인프라 서버** 영역에서 **구성**을 클릭합니다.  
  
2.  인프라 서버 설치 마법사의 **네트워크 위치 서버** 페이지에서 배포에 포함된 네트워크 위치 서버의 위치에 해당하는 옵션을 클릭합니다. 네트워크 위치 서버가 원격 웹 서버에 있으면 계속하기 전에 URL을 입력하고 **유효성 검사**를 클릭합니다. 네트워크 위치 서버가 원격 액세스 서버에 있으면 **찾아보기**를 클릭하여 관련 인증서를 찾은 후 **다음**을 클릭합니다.  
  
3.  **DNS** 페이지의 테이블에 NRPT(이름 확인 정책 테이블) 예외로 적용할 추가 이름 접미사를 입력합니다. 로컬 이름 확인 옵션을 선택하고 **다음**을 클릭합니다.  
  
4.  **DNS 접미사 검색 목록** 페이지에서 원격 액세스 서버가 배포의 모든 도메인 접미사를 자동으로 검색합니다. **추가** 및 **제거** 단추를 사용하여 사용할 도메인 접미사 목록에서 도메인 접미사를 추가 및 제거합니다. 새 도메인 접미사를 추가하려면 **새 접미사**에 접미사를 입력하고 **추가**를 클릭합니다. **다음**을 클릭합니다.  
  
5.  **관리** 페이지에서 자동으로 검색되지 않는 관리 서버를 추가하고 **다음**을 클릭합니다. 원격 액세스는 도메인 컨트롤러 및 Configuration Manager 서버를 자동으로 추가 합니다.  
  
    > [!NOTE]  
    > 서버가 자동으로 추가 되지만 목록에 나타나지 않습니다. 구성을 처음 적용 한 후에는 Configuration Manager 서버가 목록에 표시 됩니다.  
  
6.  **마침**을 클릭합니다.  
  
## <a name="26-configure-application-servers"></a><a name="BKMK_App"></a>2.6. 응용 프로그램 서버 구성  
응용 프로그램 서버 구성은 원격 액세스 배포에서 선택적 작업입니다. 원격 액세스를 사용하면 응용 프로그램 서버 보안 그룹에 포함되었는지 여부에 따라 선택한 응용 프로그램 서버에 대한 인증을 요구할 수 있습니다. 기본적으로 인증을 요구하는 응용 프로그램 서버로의 트래픽은 암호화되기도 하지만 이 트래픽을 암호화하지 인증만 사용하도록 선택할 수 있습니다.  
  
> [!NOTE]  
> 인증을 암호화 하지 않고 Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 r 2를 실행 하는 응용 프로그램 서버 에서만 지원 됩니다.  
  
#### <a name="to-configure-application-servers"></a>응용 프로그램 서버를 구성하려면  
  
1.  원격 액세스 관리 콘솔의 가운데 창에 있는 **4단계 응용 프로그램 서버** 영역에서 **구성**을 클릭합니다.  
  
2.  DirectAccess 응용 프로그램 서버 설치 마법사에서 선택한 응용 프로그램 서버에 대한 인증을 요청하려면 **선택한 응용 프로그램 서버로 인증 확장**을 클릭합니다. **추가**를 클릭하여 응용 프로그램 서버 보안 그룹을 선택합니다.  
  
3.  응용 프로그램 서버 보안 그룹의 서버로만 액세스를 제한하려면 **보안 그룹에 포함된 서버에만 액세스 허용** 확인란을 선택합니다.  
  
4.  암호화 하지 않고 인증을 사용 하려면 트래픽 암호화 안 함을 선택 합니다 **. 인증만 사용** 확인란을 선택 합니다.  
  
5.  **마침**을 클릭합니다.  
  
## <a name="27-configuration-summary-and-alternate-gpos"></a><a name="BKMK_GPO"></a>2.7. 구성 요약 및 대체 GPO  
원격 액세스 구성이 완료되면 **원격 액세스 검토**가 표시됩니다. 다음을 포함하여 이전에 선택한 모든 설정을 검토할 수 있습니다.  
  
1.  **GPO 설정**: DirectAccess 서버 GPO 이름 및 클라이언트 GPO 이름이 나열됩니다. 또한 **GPO 설정** 머리글 옆의 **변경** 링크를 클릭하여 GPO 설정을 수정할 수 있습니다.  
  
2.  **원격 클라이언트**: 보안 그룹, 강제 터널링 상태, 연결 검증 도구, DirectAccess 연결 이름 등의 DirectAccess 클라이언트 구성이 표시됩니다.  
  
3.  **원격 액세스 서버**: 공개 이름/주소, 네트워크 어댑터 구성, 인증서 정보, OTP 정보(구성된 경우) 등의 DirectAccess 구성이 표시됩니다.  
  
4.  **인프라 서버**:이 목록에 네트워크 위치 서버 URL, DirectAccess 클라이언트와 관리 서버 정보를 사용 하는 DNS 접미사입니다.  
  
5.  **애플리케이션 서버**: 특정 애플리케이션 서버에 대한 엔드투엔드 인증 상태 외에 DirectAccess 원격 관리 상태가 표시됩니다.  
  
## <a name="28-how-to-configure-the-remote-access-server-by-using-windows-powershell"></a><a name="BKMK_PS"></a>2.8. Windows PowerShell을 사용하여 원격 액세스 서버를 구성하는 방법  
![Windows PowerShell](../../../media/Step-2-Configuring-DirectAccess-Servers/PowerShellLogoSmall.gif)**Windows powershell 해당 명령**  
  
다음 Windows PowerShell cmdlet은 이전 절차와 동일한 기능을 수행합니다. 서식 조건 때문에 각 cmdlet이 여러 줄로 자동 줄 바꿈되어 표시되더라도 한 줄에 입력합니다.  
  
루트 도메인에만 DirectAccess에 대 한 원격 액세스의 지 토폴로지에서 전체 설치를 수행 하려면 **corp.contoso.com** 다음 매개 변수를 사용 하 고: 서버 GPO: **DirectAccess 서버 설정**, 클라이언트 GPO: DirectAccess Client Settings, 내부 네트워크 어댑터: **Corpnet**, 외부 네트워크 어댑터: **인터넷**, ConnectTto 주소: **edge1. contoso.com**, 및 네트워크 위치 서버: **nls.corp.contoso.com**:  
  
```  
Install-RemoteAccess -Force -PassThru -ServerGpoName 'corp.contoso.com\DirectAccess Server Settings' -ClientGpoName 'corp.contoso.com\DirectAccess Client Settings' -DAInstallType 'FullInstall' -InternetInterface 'Internet' -InternalInterface 'Corpnet' -ConnectToAddress 'edge1.contoso.com' -NlsUrl 'https://nls.corp.contoso.com/'  
```  
  
CORP-APP1-CA라는 인증 기관에서 발급한 IPsec 루트 인증서와 함께 컴퓨터 인증서 인증을 사용하여 원격 액세스 서버를 구성하려면 다음을 실행합니다.  
  
```  
$certs = Get-ChildItem Cert:\LocalMachine\Root  
$IPsecRootCert = $certs | Where-Object {$_.Subject -Match "corp-APP1-CA"}  
Set-DAServer -IPsecRootCertificate $IPsecRootCert  
```  
  
**DirectAccessClients**라는 DirectAccess 클라이언트가 포함된 보안 그룹을 추가하고 기본 Domain Computers 보안 그룹을 제거하려면 다음을 실행합니다.  
  
```  
Add-DAClient -SecurityGroupNameList @('corp.contoso.com\DirectAccessClients')  
Remove-DAClient -SecurityGroupNameList @('corp.contoso.com\Domain Computers')  
```  
  
모든 컴퓨터 (노트북 및 랩톱), 원격 액세스를 사용 하도록 설정 하 고 Windows 7에 대 한 원격 액세스 클라이언트를 사용 하도록 설정 하려면:  
  
```  
Set-DAClient -OnlyRemoteComputers 'Disabled' -Downlevel 'Enabled'  
```  
  
연결 이름 및 웹 검색 URL을 포함하여 DirectAccess 클라이언트 환경을 구성하려면 다음을 실행합니다.  
  
```  
Set-DAClientExperienceConfiguration -FriendlyName 'Contoso DirectAccess Connection' -PreferLocalNamesAllowed $False -PolicyStore 'corp.contoso.com\DirectAccess Client Settings' -CorporateResources @('HTTP:https://directaccess-WebProbeHost.corp.contoso.com')  
```  
  
## <a name="previous-step"></a><a name="BKMK_Links"></a>이전 단계  
  
-   [1 단계: 고급 DirectAccess 인프라 구성](da-adv-configure-s1-infrastructure.md)  
  
## <a name="next-step"></a>다음 단계  
  
-   [3 단계: 배포 확인](Step-3-Verify-the-Deployment.md)  
  


