---
ms.assetid: 963a3d37-d5f1-4153-b8d5-2537038863cb
title: AD FS 보안 계획 및 배포 모범 사례
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: bcddb3cc7534f45f0a84e25a6174648f1e3b82af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858416"
---
# <a name="best-practices-for-secure-planning-and-deployment-of-ad-fs"></a>AD FS 보안 계획 및 배포 모범 사례


이 항목에서는 Active Directory Federation Services (AD FS) 배포를 디자인할 때 보안을 계획 하 고 평가 하는 데 도움이 되는 모범 사례 정보를 제공 합니다. 이 항목은 AD FS 사용의 전반적인 보안에 영향을 주는 고려 사항을 검토 하 고 평가 하는 시작점입니다. 이 항목의 정보는 기존 보안 계획 및 기타 디자인 모범 사례를 보완하고 확장하기 위해 작성되었습니다.  
  
## <a name="core-security-best-practices-for-ad-fs"></a>AD FS에 대한 핵심 보안 모범 사례  
다음 핵심 모범 사례는 디자인 또는 배포의 보안을 개선 하거나 확장 하려는 모든 AD FS 설치에 공통적입니다.  

-   **"계층 0" 시스템으로 AD FS 보안** 

    AD FS은 기본적으로 인증 시스템입니다.  따라서 네트워크의 다른 id 시스템과 같은 "계층 0" 시스템으로 처리 되어야 합니다.  Active Directory 관리 계층 모델에 대 한 자세한 내용은 [Microsoft Docs](https://docs.microsoft.com/windows-server/identity/securing-privileged-access/securing-privileged-access-reference-material) . 


-   **보안 구성 마법사를 사용 하 여 페더레이션 서버 및 페더레이션 서버 프록시 컴퓨터에 AD FS 특정 보안 모범 사례를 적용 합니다.**  
  
    SCW (보안 구성 마법사)는 모든 Windows Server 2008, Windows Server 2008 R2 및 Windows Server 2012 컴퓨터에 미리 설치 되어 제공 되는 도구입니다. 이 도구를 사용하여 설치하는 서버 역할에 따라 서버의 공격 노출을 줄일 수 있는 보안 모범 사례를 적용할 수 있습니다.  
  
    AD FS를 설치할 때 설치 프로그램은 SCW에서 설치 중에 선택하는 특정 AD FS 서버 역할(페더레이션 서버 또는 페더레이션 서버 프록시)에 적용할 보안 정책을 만드는 데 사용할 수 있는 역할 확장 파일을 만듭니다.  
  
    설치된 각 역할 확장 파일은 역할의 유형 및 각 컴퓨터가 구성되는 하위 역할을 나타냅니다. C:WindowsADFSScw 디렉터리에 설치 되는 역할 확장 파일은 다음과 같습니다.  
  
    -   Farm.xml  
  
    -   SQLFarm.xml  
  
    -   StandAlone.xml  
  
    -   Proxy.xml(이 파일은 페더레이션 서버 프록시 역할로 컴퓨터를 구성한 경우에만 제공됨)  
  
    SCW에서 AD FS 역할 확장을 적용하려면 다음 단계를 순서대로 완료합니다.  
  
    1.  AD FS를 설치하고 해당 컴퓨터에 대한 적절한 서버 역할을 선택합니다. 자세한 내용은 AD FS 배포 가이드에서 [페더레이션 서비스 프록시 역할 서비스 설치](../../ad-fs/deployment/Install-the-Federation-Service-Proxy-Role-Service.md) 를 참조 하세요.  
  
    2.  Scwcmd 명령줄 도구를 사용하여 적절한 역할 확장 파일을 등록합니다. 컴퓨터가 구성된 역할에서 이 도구를 사용하는 방법에 대한 자세한 내용은 다음 표를 참조하세요.  
  
    3.  WindowssecurityMsscwLogs 디렉터리에 있는 SCWRegister_log 파일을 검사 하 여 명령이 성공적으로 완료 되었는지 확인 합니다.  
  
    AD FS 기반 SCW 보안 정책을 적용할 각 페더레이션 서버 또는 페더레이션 서버 프록시 컴퓨터에서 이 모든 단계를 수행해야 합니다.  
  
    다음 표에서는 AD FS를 설치한 컴퓨터에서 선택한 AD FS 서버 역할에 따라 적절한 SCW 역할 확장을 등록하는 방법에 대해 설명합니다.  
  
    |AD FS 서버 역할|사용하는 AD FS 구성 데이터베이스|명령 프롬프트에 다음 명령을 입력합니다.|  
    |---------------------|-------------------------------------|---------------------------------------------------|  
    |독립 실행형 페더레이션 서버|Windows Internal Database|`scwcmd register /kbname:ADFS2Standalone /kbfile:"WindowsADFSscwStandAlone.xml"`|  
    |팜에 가입된 페더레이션 서버|Windows Internal Database|`scwcmd register /kbname:ADFS2Standalone /kbfile:"WindowsADFSscwFarm.xml"`|  
    |팜에 가입된 페더레이션 서버|SQL Server|`scwcmd register /kbname:ADFS2Standalone /kbfile:"WindowsADFSscwSQLFarm.xml"`|  
    |페더레이션 서버 프록시|N/A|`scwcmd register /kbname:ADFS2Standalone /kbfile:"WindowsADFSscwProxy.xml"`|  
  
    AD FS에서 사용할 수 있는 데이터베이스에 대한 자세한 내용은 [AD FS 구성 데이터베이스의 역할](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)을 참조하세요.  
  
-   **보안이 매우 중요 한 상황 (예: 키오스크를 사용 하는 경우)에서 토큰 재생 검색을 사용 합니다.**  
    토큰 재생 검색은 페더레이션 서비스에 대 한 토큰 요청을 재생 하려는 모든 시도를 감지 하 고 요청을 취소 하는 AD FS의 기능입니다. 토큰 재생 검색은 기본적으로 사용됩니다. 동일한 토큰을 두 번 이상 사용하지 않는 경우 WS-Federation Passive 프로필과 SAML(Security Assertion Markup Language) WebSSO 프로필 둘 다에서 작동합니다.  
  
    페더레이션 서비스를 시작하면 이행하는 모든 토큰 요청의 캐시가 생성되기 시작합니다. 시간이 지나면서 후속 토큰 요청이 캐시에 추가되면 페더레이션 서비스에 대해 토큰 요청을 여러 번 재생하려는 시도를 검색할 수 있는 기능이 증가합니다. 토큰 재생 검색을 사용하지 않도록 설정한 후 나중에 다시 사용하도록 설정하는 경우 페더레이션 서비스는 재생 캐시가 해당 콘텐츠를 다시 작성할 수 있는 충분한 시간이 경과할 때까지 일정 기간 동안 이전에 사용되었을 수 있는 토큰을 계속 허용합니다. 자세한 내용은 [AD FS 구성 데이터베이스의 역할](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)을 참조하세요.  
  
-   **토큰 암호화를 사용 합니다. 특히 지원 되는 SAML 아티팩트 확인을 사용 하는 경우입니다.**  
  
    토큰 암호화는 AD FS 배포에 대해 시도 될 수 있는 잠재적 MITM (메시지 가로채기 (man-in-the-middle) 공격을 방지 하 고 보안을 강화 하는 것이 좋습니다. 암호화를 사용하면 처리량이 약간 저하되지만 일반적으로 인식할 수 있는 수준은 아니며, 대부분의 배포에서는 강화된 보안 이점이 서버 성능 면에서 소요되는 모든 비용을 능가합니다.  
  
    토큰 암호화를 사용하려면 먼저 신뢰 당사자 트러스트에 대한 암호화 인증서 추가를 설정합니다. 신뢰 당사자 트러스트를 만들 때 또는 그 이후에 암호화 인증서를 구성할 수 있습니다. 나중에 기존 신뢰 당사자 트러스트에 암호화 인증서를 추가 하려면 AD FS 스냅인을 사용 하는 동안 트러스트 속성 내의 **암호화** 탭에서 사용할 인증서를 설정할 수 있습니다. AD FS cmdlet을 사용 하 여 기존 트러스트에 대 한 인증서를 지정 하려면 ClaimsProviderTrust 또는 **하려면 set-relyingpartytrust** Cmdlet의 **Set-ClaimsProviderTrust** certificate 매개 변수를 사용 합니다. 토큰 암호를 해독할 때 사용할 페더레이션 서비스 인증서를 설정 하려면 **ADFSCertificate** cmdlet을 사용 하 고 *certificatetype* 매개 변수에 "`Token-Encryption`"을 지정 합니다. 특정 신뢰 당사자 트러스트에 대해 암호화를 사용하거나 사용하지 않도록 설정하려면 *Set-RelyingPartyTrust* cmdlet의 **EncryptClaims** 매개 변수를 사용하면 됩니다.  
  
-   **인증에 확장 된 보호 활용**  
  
    배포를 안전 하 게 보호 하기 위해 AD FS에서 인증 기능에 대 한 확장 된 보호를 설정 하 고 사용할 수 있습니다. 이 설정은 페더레이션 서버에서 지 원하는 인증에 대 한 확장 된 보호 수준을 지정 합니다.  
  
    인증에 대한 확장된 보호는 공격자가 클라이언트 자격 증명을 가로채 서버로 전달하는 MITM(메시지 가로채기) 공격을 방지하는 데 도움이 됩니다. 이러한 공격은 CBT(채널 바인딩 토큰)를 통해 방지할 수 있으며, CBT는 클라이언트와의 통신을 설정할 때 서버에서 필요로 하거나, 허용하거나, 필요로 하지 않을 수 있습니다.  
  
    확장된 보호 기능을 사용하려면 **ExtendedProtectionTokenCheck** cmdlet에서 **Set-ADFSProperties** 매개 변수를 사용합니다. 이 설정의 가능한 값과 해당 값에서 제공하는 보안 수준은 다음 표에 설명되어 있습니다.  
  
    |매개 변수 값|보안 수준|보호 설정|  
    |-------------------|------------------|----------------------|  
    |필요|서버가 완전히 강화됨|확장된 보호가 적용되며 항상 필요함|  
    |허용|서버가 부분적으로 강화됨|관련된 시스템에 확장된 보호를 지원하기 위한 패치가 적용된 경우 확장된 보호가 적용됨|  
    |없음|서버가 취약함|확장된 보호가 적용되지 않음|  
  
-   **로깅 및 추적을 사용 하는 경우 중요 한 정보의 개인 정보 보호를 확인 합니다.**  
  
    AD FS는 기본적으로 페더레이션 서비스 또는 정상적인 작업의 일부로 PII (개인적으로 식별이 가능한 정보)를 직접 노출 하거나 추적 하지 않습니다. 그러나 AD FS에서 이벤트 로깅 및 디버그 추적 로깅이 사용 되는 경우 일부 클레임 형식을 구성 하는 클레임 정책 및 관련 값에 따라 AD FS 이벤트 또는 추적 로그에 기록 될 수 있는 PII가 포함 될 수 있습니다.  
  
    따라서 AD FS 구성 및 로그 파일에 대 한 액세스 제어를 적용 하는 것이 좋습니다. 이러한 종류의 정보를 표시하지 않으려면 로깅을 해제하거나 다른 사람과 로그를 공유하기 전에 로그에서 PII 또는 중요한 데이터를 필터링해야 합니다.  
  
    다음은 로그 파일 내용이 의도치 않게 노출되는 것을 방지하는 데 도움이 되는 몇 가지 팁입니다.  
  
    -   액세스 해야 하는 신뢰할 수 있는 관리자 에게만 액세스를 제한 하는 ACL (액세스 제어 목록)로 AD FS 이벤트 로그 및 추적 로그 파일을 보호 해야 합니다.  
  
    -   웹 요청을 통해 쉽게 제공될 수 있는 파일 확장명 또는 경로를 사용하여 로그 파일을 복사하거나 보관하지 마세요. 예를 들어 .xml 파일 이름 확장명은 안전한 선택이 아닙니다. 사용 가능한 확장명 목록은 IIS(인터넷 정보 서비스) 관리 가이드에서 확인할 수 있습니다.  
  
    -   로그 파일의 경로를 수정하는 경우 외부 사용자가 웹 브라우저를 통해 액세스하지 못하도록 웹 호스트 가상 루트(vroot) 공용 디렉터리 외부에 있는 로그 파일 위치에 대한 절대 경로를 지정해야 합니다.  

-   **AD FS 엑스트라넷 소프트 잠금 및 AD FS 엑스트라넷 스마트 잠금 보호**  
    
    웹 응용 프로그램 프록시를 통해 제공 되는 잘못 된 (잘못 된) 암호를 사용 하 여 인증 요청 형식으로 공격 하는 경우 AD FS 엑스트라넷 잠금을 사용 하면 AD FS 계정 잠금 으로부터 사용자를 보호할 수 있습니다. AD FS 계정 잠금에서 사용자를 보호 하는 것 외에도 AD FS, 엑스트라넷 잠금은 무작위 암호 추측 공격 으로부터 보호 합니다.  
    
    Windows Server 2012 r 2에서 AD FS에 대 한 엑스트라넷 소프트 잠금 [AD FS 엑스트라넷 소프트 잠금 보호](../../ad-fs/operations/Configure-AD-FS-Extranet-Soft-Lockout-Protection.md)를 참조 하세요.  

     Windows Server 2016의 AD FS에 대 한 엑스트라넷 스마트 잠금 [AD FS 엑스트라넷 스마트 잠금 보호](../../ad-fs/operations/Configure-AD-FS-Extranet-Smart-Lockout-Protection.md)를 참조 하세요.  
  
## <a name="sql-serverspecific-security-best-practices-for-ad-fs"></a>AD FS에 대한 SQL Server 관련 보안 모범 사례  
다음 보안 모범 사례는 Microsoft SQL Server&reg; 나 WID (Windows 내부 데이터베이스)를 사용 하는 것과 관련이 있습니다. 이러한 데이터베이스 기술은 AD FS 디자인 및 배포에서 데이터를 관리 하는 데 사용 됩니다.  
  
> [!NOTE]  
> 이러한 권장 사항은 SQL Server 제품 보안 지침을 대체하는 것이 아니라 확장하는 것입니다. 보안 SQL Server 설치를 계획 하는 방법에 대 한 자세한 내용은 보안 [SQL 설치를 위한 보안 고려 사항](https://go.microsoft.com/fwlink/?LinkID=139831) (https://go.microsoft.com/fwlink/?LinkID=139831)을 참조 하세요.  
  
-   **항상 물리적으로 안전한 네트워크 환경에서 방화벽 뒤에 SQL Server를 배포 합니다.**  
  
    SQL Server 설치를 인터넷에 직접 노출해서는 안 됩니다. 데이터 센터 내에 있는 컴퓨터 에서만 AD FS를 지 원하는 SQL server 설치에 연결할 수 있어야 합니다. 자세한 내용은 [보안 모범 사례 검사 목록](https://go.microsoft.com/fwlink/?LinkID=189229) (https://go.microsoft.com/fwlink/?LinkID=189229)을 참조 하세요.  
  
-   **기본 제공 되는 기본 시스템 서비스 계정을 사용 하는 대신 서비스 계정에서 SQL Server를 실행 합니다.**  
  
    기본적으로 SQL Server는 지원되는 기본 제공 시스템 계정(예: LocalSystem 또는 NetworkService 계정) 중 하나를 사용하도록 설치 및 구성되는 경우가 많습니다. AD FS에 대 한 SQL Server 설치의 보안을 강화 하려면 가능한 경우 별도의 서비스 계정을 사용 하 여 SQL Server 서비스에 액세스 하 고 Active Directory 배포에이 계정의 SPN (보안 주체 이름)을 등록 하 여 Kerberos 인증을 사용 하도록 설정 합니다. 이는 클라이언트와 서버 간의 상호 인증을 지원합니다. 별도 서비스 계정의 SPN을 등록하지 않으면 SQL Server에서 Windows 기반 인증용 NTLM을 사용하므로 클라이언트만 인증됩니다.  
  
-   **SQL Server의 노출 영역을 최소화 합니다.**  
  
    필요한 SQL Server 엔드포인트만 사용합니다. 기본적으로 SQL Server는 제거할 수 없는 단일 기본 제공 TCP 엔드포인트을 제공합니다. AD FS의 경우 Kerberos 인증에이 TCP 끝점을 사용 하도록 설정 해야 합니다. 현재 TCP 끝점을 검토하여 추가 사용자 정의 TCP 포트가 SQL 설치에 추가되었는지 알아보려면 Transact-SQL(T-SQL) 세션에서 "SELECT * FROM sys.tcp_endpoints" 쿼리 문을 사용하면 됩니다. SQL Server 끝점 구성에 대 한 자세한 내용은 [방법: 여러 TCP 포트에서 수신 하도록 데이터베이스 엔진 구성](https://go.microsoft.com/fwlink/?LinkID=189231) (https://go.microsoft.com/fwlink/?LinkID=189231)을 참조 하십시오.  
  
-   **SQL 기반 인증을 사용 하지 마십시오.**  
  
    암호가 네트워크를 통해 일반 텍스트로 전송되거나 구성 설정에 저장되는 것을 방지하려면 SQL Server 설치에서 Windows 인증만 사용합니다. SQL Server 인증은 레거시 인증 모드입니다. SQL Server 인증을 사용할 때는 SQL(Structured Query Language) 로그인 자격 증명(SQL 사용자 이름 및 암호)을 저장하지 않는 것이 좋습니다. 자세한 내용은 [인증 모드](https://go.microsoft.com/fwlink/?LinkID=189232) (https://go.microsoft.com/fwlink/?LinkID=189232)를 참조 하세요.  
  
-   **SQL 설치에서 추가 채널 보안의 필요성을 신중 하 게 평가 합니다.**  
  
    Kerberos 인증을 적용하는 경우에도 SQL Server SSPI(Security Support Provider Interface)는 채널 수준 보안을 제공하지 않습니다. 그러나 서버가 방화벽으로 보호된 네트워크에 안전하게 있는 설치의 경우 SQL 통신을 암호화하지 않아도 됩니다.  
  
    암호화는 보안을 유지하는 데 도움이 되는 중요한 도구이지만 모든 데이터 또는 연결에서 고려할 필요는 없습니다. 암호화를 구현할지 결정할 때 사용자가 데이터에 액세스하는 방법을 고려하세요. 사용자가 공용 네트워크를 통해 데이터에 액세스하는 경우에는 보안을 강화하기 위해 데이터 암호화가 필요할 수 있습니다. 그러나 AD FS의 모든 SQL 데이터 액세스에 보안 인트라넷 구성이 포함 된 경우에는 암호화가 필요 하지 않을 수 있습니다. 또한 암호화의 사용에는 암호, 키 및 인증서에 대한 유지 관리 전략이 포함되어야 합니다.  
  
    SQL 데이터가 네트워크를 통해 확인되거나 변조될 수 있는 문제가 있는 경우에는 IPsec(인터넷 프로토콜 보안) 또는 SSL(Secure Sockets Layer)을 사용하여 SQL 연결의 보안을 강화할 수 있습니다. 그러나 SQL Server 성능에 부정적인 영향을 미칠 수 있으며,이로 인해 일부 상황에서 AD FS 성능이 영향을 주거나 제한 될 수 있습니다. 예를 들어 SQL 기반 특성 저장소에서의 특성 조회가 토큰 발급에 중요 한 경우 토큰 발급의 AD FS 성능이 저하 될 수 있습니다. 더 강력한 경계 보안 구성을 통해 SQL 변조 위협을 보다 효율적으로 제거할 수 있습니다. 예를 들어 SQL Server 설치의 보안을 유지하는 향상된 솔루션은 인터넷 사용자 및 컴퓨터의 액세스를 차단하고 데이터 센터 환경 내의 사용자 또는 컴퓨터만 액세스할 수 있게 합니다.  
  
    자세한 내용은 SQL Server 또는 [SQL Server 암호화](https://go.microsoft.com/fwlink/?LinkID=189233) [에 대 한 연결 암호화](https://go.microsoft.com/fwlink/?LinkID=189234) 를 참조 하세요.  
  
-   **저장 프로시저를 사용 하 여 SQL 저장 데이터를 AD FS 하 여 모든 SQL 기반 조회를 수행 함으로써 안전 하 게 디자인 된 액세스를 구성 합니다.**  
  
    더 나은 서비스 및 데이터 격리를 제공하기 위해 모든 특성 저장소 조회 명령에 대한 저장 프로시저를 만들 수 있습니다. 그런 다음 저장 프로시저 실행 권한을 부여할 데이터베이스 역할을 만들 수 있습니다. 이 데이터베이스 역할에 AD FS Windows 서비스의 서비스 id를 할당 합니다. AD FS Windows 서비스는 특성 조회에 사용 되는 적절 한 저장 프로시저 외에 다른 SQL 문을 실행할 수 없어야 합니다. 이 방식으로 SQL Server 데이터베이스에 대한 액세스를 잠그면 권한 상승 공격의 위험이 줄어듭니다.  
  
## <a name="see-also"></a>참고 항목
[Windows Server 2012의 AD FS 디자인 가이드](AD-FS-Design-Guide-in-Windows-Server-2012.md)
