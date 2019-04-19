---
ms.assetid: 5ab76733-804d-4f30-bee6-cb672ad5075a
title: "도메인 컨트롤러 배포 문제 해결"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 254209b0da6a7bc0cd5f3880e14a7e5b16822cdd
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2017
---
# <a name="troubleshooting-domain-controller-deployment"></a>도메인 컨트롤러 배포 문제 해결

>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

이 항목에서는 도메인 컨트롤러 구성 및 배포 해결 방법을 자세히 설명에 설명 합니다.  
  
-   [문제 해결 소개](../../ad-ds/deploy/Troubleshooting-Domain-Controller-Deployment.md#BKMK_Intro)  
  
-   [문제 해결 옵션](../../ad-ds/deploy/Troubleshooting-Domain-Controller-Deployment.md#BKMK_Options)  
  
## <a name="BKMK_Intro"></a>문제 해결 소개  
![문제 해결](media/Troubleshooting-Domain-Controller-Deployment/adds_deploy_troubleshooting.png)  
  
## <a name="BKMK_Options"></a>문제 해결 옵션  
  
### <a name="logging-options"></a>로그인 옵션  
기본 제공 되는 도메인 컨트롤러 프로 모션 및 수준 내리기 관련 문제를 해결 하는 데 가장 중요 한 정보입니다. 모든 이러한 로그 활성화 되어 최대 세부 정보 표시 수준에 기본적으로 구성 됩니다.  
  
|단계|로그|  
|---------|-------|  
|서버 관리자 또는 ADDSDeployment Windows PowerShell 작업|-%systemroot%\debug\dcpromoui.log<br /><br />-%systemroot%\debug\dcpromoui*.log|  
|도메인 컨트롤러의 설치 프로 모션|-%systemroot%\debug\dcpromo.log<br /><br />-%systemroot%\debug\dcpromo*.log<br /><br />이벤트 viewer\Windows logs\System<br /><br />이벤트 viewer\Windows logs\Application<br /><br />이벤트 viewer\Applications 및 서비스 logs\Directory 서비스<br /><br />이벤트 viewer\Applications 및 서비스 logs\File 복제 서비스<br /><br />이벤트 viewer\Applications 및 서비스 logs\DFS 복제|  
|숲 또는 도메인 업그레이드|-%systemroot%\debug\adprep\\<datetime>\adprep.log<br /><br />-%systemroot%\debug\adprep\\<datetime>\csv.log<br /><br />-%systemroot%\debug\adprep\\<datetime>\dspecup.log<br /><br />-%systemroot%\debug\adprep\\<datetime>\ldif.log*|  
|서버 관리자 ADDSDeployment Windows PowerShell 배포 엔진|이벤트 viewer\Applications 및 서비스 logs\Microsoft\Windows\DirectoryServices-Deployment\Operational|  
|Windows 서비스|-%systemroot%\Logs\CBS\\*<br /><br />-%systemroot%\servicing\sessions\sessions.xml<br /><br />-%systemroot%\winsxs\poqexec.log<br /><br />-%systemroot%\winsxs\pending.xml|  
  
### <a name="tools-and-commands-for-troubleshooting-domain-controller-configuration"></a>도구 및 도메인 컨트롤러 구성 문제 해결에 대 한 명령  
로그에 설명 되어 있지 문제를 해결 하려면 다음 도구를 사용 하 여 시작 지점으로 다음과 같습니다.  
  
-   Dcdiag.exe  
  
-   Repadmin.exe  
  
-   [AutoRuns.exe](https://technet.microsoft.com/sysinternals/bb963902.aspx)를 작업 관리자 및 MSInfo32.exe  
  
-   [모니터 3.4 네트워크](https://www.microsoft.com/download/en/details.aspx?displaylang=en&id=4865) (또는 제 3 자 네트워크 분석 및 캡처 도구)  
  
### <a name="general-methodology-for-troubleshooting-domain-controller-configuration"></a>일반 방법론 도메인 컨트롤러 구성 문제 해결  
  
1.  간단한 구문을 문제 오류가 발생 했나요?  
  
    1.  잘못 입력 하거나 했나요 인수 ADDSDeployment Windows PowerShell를 제공 하기 위해 잊지? 예를 들어, ADDSDeployment Windows PowerShell를 사용 하는 경우 했는지 필요한 인수 추가 **-도메인 이름** 유효한 이름으로?  
  
    2.  Windows PowerShell 콘솔을 명령줄 제공 구문 분석 실패 이유 정확 하 게 표시 신중 하 게 출력 검사 합니다.  
  
2.  오류 필수 오류 인가요?  
  
    1.  심각한 프로 모션 결과가 표시 하는 데 사용 하는 많은 오류 필수 검사 하 여 이제 수 없습니다.  
  
    2.  필수 오류의 텍스트를 주의 깊게 검토 제어 시나리오는 대부분의 문제를 해결 하기 위해 필요한 지침 제공 합니다.  
  
3.  프로 모션 및 따라서 심각한 오류 인가요?  
  
    1.  결과 신중 하 게 검사: 많은 오류 잘못 된 암호, 네트워크 이름 확인 주요 오프 라인 도메인 컨트롤러 등 간단 하 게 설명 했습니다.  
  
    2.  출력에 표시 된 오류 오류가 발생 하는 이유의 표시가 표시 되도록에서 이전 버전과 호환성이 다음 작업에 대 한 Dcpromoui.log와 dcpromo.log 검사 합니다.  
  
        1.  항상 작업 샘플 로그를 비교  
  
        2.  결과 스키마 확장 하거나 숲 또는 도메인 준비 문제가 있을 경우에 ADPrep 로그에서 오류를 검사 합니다.  
  
        3.  오류에 대 한 위해 배포 이벤트 로그 Dcpromoui.log 세부 없는 또는 예외로 구성 과정에서 인해 임의로 종료 하는 경우에 검사 합니다.  
  
    3.  디렉터리 서비스, 시스템 및 응용 프로그램 이벤트 로그 구성 문제에 대 한 다른 표시기를 검사 합니다. 종종 도메인 컨트롤러 프로 모션 분산된 모든 시스템에 영향을 다른 네트워크 잘못 된 증상 뿐입니다.  
  
    4.  Dcdiag.exe 및 repadmin.exe을 사용 하 여 전체 숲 상태를 확인 하는 도메인 컨트롤러 프로 모션 방지 미세한 구성 오류를 나타냅니다.  
  
    5.  방해 될 수 있는 제 3 자 소프트웨어에 대 한 컴퓨터를 검사 하 AutoRuns.exe, 작업 관리자 또는 MSinfo32.exe 사용 합니다.  
  
        1.  타사 소프트웨어를 제거 (해제 하지 않는 하기만 하면 소프트웨어는 드라이버가 로드 때도).  
  
    6.  네트워크 모니터 3.4 복제 파트너 도메인 컨트롤러 홍보도 네트워크 양면 캡처를 프로 모션 프로세스를 분석 하 실패 하는 컴퓨터에 설치 합니다.  
  
        1.  건강 프로 모션 다음과 같이 및 문제가 이해 하 여 작업 랩 환경에이 비교 합니다.  
  
        2.  이 시점 오류 숲 개체, 기본 비 보안 변경 또는 네트워크와 가능성이 이며이 새로운 도메인 컨트롤러 DNS, 방화벽, 호스트 침입 보호 소프트웨어 또는 기타 외부 요인 구성 오류 정품이 수 있습니다.  
  
### <a name="troubleshooting-specific-problems"></a>특정 문제 해결  
  
#### <a name="events-and-error-messages"></a>이벤트 및 오류 메시지  
도메인 컨트롤러 모션과 수준 항상 내리기 끝 대부분의 프로그램 달리 하 고 작업의 성공 수행 하지 반환 0 코드를 반환 합니다. 도메인 컨트롤러 구성 끝에 있는 코드를 확인 하려면 몇 가지 옵션이 있습니다.  
  
1.  서버 관리자를 사용 하는 경우 자동으로 다시 부팅 되기 전에 10 초 동안 프로 모션 결과 확인 합니다.  
  
2.  ADDSDeployment Windows PowerShell를 사용 하는 경우 자동으로 다시 부팅 되기 전에 10 초 동안 프로 모션 결과 확인 합니다. 또는 하지 않도록 선택할 완료 되 면 자동으로 다시 시작 합니다. 추가 해야는 **형식 목록** 파이프라인 출력 더 쉽게 읽을 수 있습니다. 예를 들어:  
  
    ```  
    Install-addsdomaincontroller <options> -norebootoncompletion:$true | format-list  
  
    ```  
  
    항상에서 표시 되도록 하려면 다시 부팅 필수 유효성 검사 및 확인에서 오류를 진행 하지 마십시오. 예를 들어:  
  
  ![문제 해결](media/Troubleshooting-Domain-Controller-Deployment/ADDS_PSPrereqError.png)  
  
3.  모든 시나리오의 dcpromo.log 및 dcpromoui.log 검사 합니다.  
  
    > [!NOTE]  
    > 아래에 나열 된 오류 중 일부는 더 이상 이상 운영 체제의 운영 체제 및 도메인 컨트롤러 구성 변경으로 인해 합니다. 또한 것을 방지 특정 오류 새로운 ADDSDeployment Windows PowerShell 코드 하지만 dcpromo.exe /unattend 하지 않습니다. 모든 현재 자동화 사용 되지 않는 DCPromo에서 Windows PowerShell ADDSDeployment 전환 하는 또 다른 멋진 이유입니다.  
  
프로 모션 및 수준 내리기 다음 성공을 메시지 코드를 반환합니다.  
  
|오류 코드|설명|노트|  
|--------------|---------------|--------|  
|1|성공 끝내기|여전히 다시 부팅 해야, 플래그 자동으로 다시 시작는이 불과 노트 된 제거|  
|2|성공, 종료, 다시 부팅 해야 합니다.||  
|3|단순한 오류와 성공 끝내기|DNS 위임 경고를 반환 하는 경우 일반적으로 발생 합니다. DNS 위임 구성 되지, 사용:<br /><br />-creatednsdelegation: $false|  
|4|성공 중요 하지 않은 실패와 함께 종료 다시 부팅 해야 합니다.|DNS 위임 경고를 반환 하는 경우 일반적으로 발생 합니다. DNS 위임 구성 되지, 사용:<br /><br />-creatednsdelegation: $false|  
  
프로 모션와 수준 내리기는 다음과 같은 오류 메시지가 코드를 반환합니다. 가 보통 확장 된 오류 메시지가 표시 됩니다. 읽기 항상 주의 하십시오 전체 오류 뿐 아니라 숫자 부분입니다.  
  
|오류 코드|설명|추천된 해결 방법|  
|--------------|---------------|------------------------|  
|11|도메인 컨트롤러 프로 모션이 이미 실행 중인|보다 하나만 도메인 컨트롤러 프로 모션 동일한 대상 컴퓨터에 대 한 동시에 실행 하지 않는|  
|12|사용자 관리자 여야 합니다.|관리자가 그룹 하 고 uac 높이기 되는지 확인 하십시오 기본 제공의 구성원 로그온|  
|13|인증 기관이 설치 되어 있습니다.|또한는 인증 기관으로이 도메인 컨트롤러를 내릴 수 없습니다. 캘리포니아가 실행 하는 경우 신중 하 게 사용-인벤토리 전에 인증서를 제거 하지 않는, 중단 역할을 제거 하면 됩니다. CAs 도메인 컨트롤러에 실행 하지 않는 것이|  
|14|부팅 안전 모드에서 실행|서버를 표준 모드로 부팅|  
|15|역할 변경을 진행 중이거나 다시 부팅 해야 함|프로 모션 하기 전에 (으로 인해 이전 구성 변경) 서버를 다시 시작 해야|  
|16|잘못 된 플랫폼에서 실행|*이 오류가 표시 되지 않을 가능성이*|  
|17|드라이브가 NTFS 5 존재|Windows Server 2012에서이 오류 불가능 ntfs 포맷 캡처하는 필요한 이상|  
|18|Windir에 공간이 부족|% Systemdrive % 볼륨 cleanmgr.exe를 사용 하 여에 공간 확보|  
|19|이름 변경 보류 중인, 다시 부팅 해야 함|서버를 다시 부팅|  
|20|컴퓨터 이름으로 구문이 잘못 되었습니다.|유효한 이름으로 컴퓨터의 이름을 바꿀합니다|  
|21|이 도메인 컨트롤러 역할 FSMO 갖고는 GC, 및/또는 DNS 서버|추가 **-demoteoperationmasterrole** 사용 하는 경우 **-forceremoval**합니다.|  
|22|TCP/IP 설치 되어 있어야 나 작동 하지 않을|컴퓨터에 연결을 구성 하 고 제대로 작동 TCP/IP 확인|  
|23|DNS 클라이언트 먼저 구성 해야 합니다.|도메인에 새 도메인 컨트롤러를 추가 하는 경우 기본 DNS 서버 설정|  
|24|제공 된 자격 증명은 잘못 되거나 누락 된 필요한 요소|사용자 이름 및 암호 올바른지 확인|  
|25|지정 된 도메인 도메인 컨트롤러 찾을 수 없는|DNS 클라이언트 설정을 방화벽 규칙의 유효성을 검사합니다|  
|26|도메인 목록 숲에서 읽을 수 없습니다.|DNS 클라이언트 설정, LDAP 기능, 방화벽 규칙의 유효성을 검사합니다|  
|27|누락 된 도메인 이름|도메인 수준을 높이 거 나 내리기 때 지정|  
|28|잘못 된 도메인 이름|홍보 때 다른, 올바른 DNS 도메인 이름 선택|  
|29|부모 도메인 없습니다.|새 자녀 도메인 또는 밤나무 도메인을 만들 때 지정 부모 도메인 확인|  
|30|숲 속의 하지 도메인|도메인 이름 제공 확인|  
|31|자녀가 도메인 이미 있습니다.|다른 도메인 이름 지정|  
|32|잘못 된 NetBIOS 도메인 이름|유효한 NetBIOS 도메인 이름 지정|  
|33|IFM 파일에 대 한 경로 잘못 되었습니다.|미디어에서 설치 폴더로 여 경로 확인|  
|34|IFM 데이터베이스 잘못 되었습니다.|이 운영 체제와 역할 (동일한 운영 체제 버전, 같은 유형의 RWDC 모양과 RODC-도메인 컨트롤러)에 대 한 정확한 다른 이름에서 설치 미디어를 사용 하 여|  
|35|누락 된 SYSKEY|설치 미디어에서를 암호화 하 고 사용 하 여 유효한 SYSKEY 제공 해야|  
|37|로그 또는 NTDS 데이터베이스에 경로 잘못 되었습니다.|경로 데이터베이스와 로그 고정된 NTFS 볼륨, 하지 드라이브 또는 변경 UNC 경로|  
|38|볼륨 공간이 충분 한 로그 나 NTDS 데이터베이스에 대 한|Cleanmgr.exe를 사용 하 여 공간을 free, 디스크 공간을 더 추가 하 고, 수동으로 불필요 한 데이터를 다른 곳에서 이동 하 여 공간을 선택 취소|  
|39|경로 sysvol 잘못 되었습니다.|고정된 NTFS 볼륨, 하지 드라이브 또는 UNC 경로 경로 SYSVOL 폴더의 변경|  
|40|잘못 된 사이트 이름|존재 하는 사이트 이름을 제공합니다|  
|41|안전 모드에 대 한 암호를 지정.|DSRM 계정에 대 한 암호를 제공, 암호 정책을 구성 된 어떻게 없이 반드시|  
|42|안전 모드 암호 기준을 (프로 모션에만 해당)를 충족 하지 않는|암호 정책을 구성 된 규칙 맞는 DSRM 계정에 대 한 암호를 입력 합니다.|  
|43|관리자 암호 기준을 (수준 내리기만)를 충족 하지 않는|구성 규칙 암호 정책 충족 하는 로컬 관리자 계정에 대 한 암호를 제공 합니다.|  
|44|지정된 된 숲 이름을 잘못 되었습니다.|유효한 숲 루트 DNS 도메인 이름 지정|  
|45|지정 된 이름이 숲 이미 있습니다.|다른 숲 루트 DNS 도메인 이름 선택|  
|46|지정된 된 했던 나무 이름을 잘못 되었습니다.|유효한 밤나무 DNS 도메인 이름 지정|  
|47|지정 된 이름이 밤나무 이미 있습니다.|다른 밤나무 DNS 도메인 이름 선택|  
|48|나무 이름을 숲 구조에 맞지 않는|다른 밤나무 DNS 도메인 이름 선택|  
|49|지정 된 도메인의 존재 하지 않는 경우|입력된 도메인 이름 확인|  
|50|내리기, 동안 마지막 도메인 컨트롤러가 유효 하지, 또는 지정한 된 마지막 도메인 컨트롤러 하지만 사이트가 검색|지정 하지 않은 **도메인에 있는 마지막 도메인 컨트롤러** (**-lastdomaincontrollerindomain**) 하는 경우에 합니다. 사용 하 여 **-ignorelastdcindomainmismatch** 마지막 도메인 컨트롤러 정말 이것이 이며 가상 도메인 컨트롤러 메타 데이터를 무시 하|  
|51|앱 파티션이 도메인 컨트롤러에 있습니다|하도록 지정 **응용 프로그램 파티션을 제거** (**-removeapplicationpartitions**)|  
|52|필요한 명령줄 인수 없습니다 (즉, 응답 파일 사람은 명령줄에서)|*Dcpromo /unattend, 더 이상 사용 되는와 에서만 나타납니다. 오래 된 설명서를 참조*|  
|53|프로 모션/수준 내리기 실패를 컴퓨터가 다시 부팅 해야 정리|확장된 오류와 로그 검사|  
|54|프로 모션/수준 내리기 실패|확장된 오류와 로그 검사|  
|55|사용자가 프로 모션 수준 내리기 취소 됨|확장된 오류와 로그 검사|  
|56|사용자가 취소 되었습니다 프로 모션 수준 내리기를 정리 하려면 컴퓨터를 다시 부팅 해야|확장된 오류와 로그 검사|  
|58|사이트 이름은 RODC 프로 모션 중 지정 해야|사이트에 대 한 RODC 지정 해야, 것은 자동으로 검색 하지는 RWDC 같은 하나|  
|59|이 도메인 컨트롤러를 영역 중 하나에 대 한 마지막 DNS 서버, 내리기 중|이 지정는 **도메인에 있는 마지막 DNS 서버** 하거나 사용 하 여 **-ignorelastdnsserverfordomain**|  
|60|Windows Server 2008 이상을 실행 하는 도메인 컨트롤러에에서 있어야 도메인 RODC을 돕기 위해|하나 이상의 Windows Server 2008 또는 뒷부분 모델 쓸 수 있는 도메인 컨트롤러 홍보|  
|61|기존 도메인 DNS 이미 호스트 하지 않는 dns Active Directory Domain Services 설치할 수 없는|*이 오류가 발생할 수 없습니다.*|  
|62|[DCInstall] 섹션 없는 응답 파일|*Dcpromo /unattend, 더 이상 사용 되는와 에서만 나타납니다. 오래 된 설명서를 참조 하십시오.*|  
|63|Windows server 2003 아래 기능 수준은 숲|숲 기능 수준을 이상 발생 Windows Server 2003 기본 합니다. Windows 2000 및 Windows NT 4.0는 더 이상 지원 되는 운영 체제|  
|64|프로 모션 실패 구성 요소 이진 감지 했기 때문에 실패 했습니다.|AD DS 역할을 설치|  
|65|프로 모션 구성 요소 이진 설치에 실패 때문에 실패 했습니다.|AD DS 역할을 설치|  
|66|프로 모션 실패 운영 체제 감지 했기 때문에 실패 했습니다.|확장된 오류와 로그; 검사 서버 운영 체제 버전을 반환 실패 합니다. 전체적 상태 매우 의심 되는 컴퓨터를 다시 설치 해야 합니다 있더라도|  
|68|복제 파트너가 잘못 되었습니다.|Repadmin.exe 사용 또는 **다운로드-ADReplication\ *** Windows PowerShell 파트너 도메인 컨트롤러 건강 유효성을 검사 하기|  
|69|필요한 포트 이미 다른 일부 프로그램에서 사용 중입니다.|사용 하 여 **netstat.exe anob** 예약 된 AD DS 포트를 잘못 지정 하는 프로세스를 찾을 수|  
|70|숲 루트 도메인 컨트롤러 GC 여야 합니다.|*Dcpromo /unattend, 더 이상 사용 되는와 에서만 나타납니다. 오래 된 설명서를 참조*|  
|71|DNS 서버가 이미 설치 되어 있습니다.|DNS 설치를 지정 하지 않습니다 (**-installDNS**) DNS 서비스 이미 설치 되어 있으면|  
|72|컴퓨터가는 관리자가 아닌 모드로 원격 데스크톱 서비스가 실행|두 개 이상의 관리자가 사용자에 대해 구성 RDS 서버 이기도으로이 도메인 컨트롤러를 홍보 수 없습니다. 최종 사용자에 게를 제거 하거나 응용 프로그램에서 사용 되는 경우 신중 하 게 사용-인벤토리 전에 RDS 중단 하면를 제거 하지 않습니다.|  
|73|지정 된 숲 기능 수준을 잘못 되었습니다.|유효한 숲 기능 수준을 지정합니다|  
|74|지정 된 도메인 기능 수준을 잘못 되었습니다.|유효한 도메인 기능 수준을 지정합니다|  
|75|기본 암호 복제 정책 확인할 수 없습니다.|암호 복제 RODC 정책 있고 액세스할 수 있는지 확인|  
|76|지정 된 복제/복제 되지 않은 보안 그룹 유효 하지 않습니다.|암호 복제 정책 지정 하는 경우 유효한 도메인 및 사용자 계정에 입력 했는지 확인|  
|77|지정 된 인수 잘못 되었습니다.|확장된 오류와 로그 검사|  
|78|Active Directory 숲 검사에 실패|확장된 오류와 로그 검사|  
|79|Rodcprep 수행 하지 않은 속성 RODC는 공유할 수 없습니다|Windows Server 2012를 사용 하 여 숲 준비 하거나 사용 하 여 **adprep.exe /rodcprep**|  
|80|도메인 준비 수행 하지 않은|Windows Server 2012 도메인을 준비 하거나 사용 하 여 사용 하 여 **adprep.exe /domainprep**|  
|81|Forestprep 수행 하지 않은|Windows Server 2012를 사용 하 여 숲 준비 하거나 사용 하 여 **adprep.exe /forestprep**|  
|82|숲 스키마 일치 하지 않습니다.|Windows Server 2012를 사용 하 여 숲 준비 하거나 사용 하 여 **adprep.exe /forestprep**|  
|83|지원 되지 않는 SKU|*이 오류가 표시 되지 않을 가능성이*|  
|84|도메인 컨트롤러 계정 감지할 수 없습니다.|기존 도메인 컨트롤러 올바른 사용자 계정 컨트롤 특성 집합 있는지 확인 합니다.|  
|85|2 단계에 도메인 컨트롤러 계정을 선택 수 없습니다.|"기존 계정을 사용 하 여" 하지만 찾을 수 없는 계정 중 하나를 지정 하거나 계정 조회 하는 동안 오류가 있으면 반환 됩니다. 올바른 RODC 준비 계정 입력 했는지 확인|  
|86|2 단계 프로 모션 실행 해야 합니다.|반환 하는 경우 추가 도메인 컨트롤러 홍보 있지만 기존 계정을 존재 하 고 "허용 다시" 지정 하지 않았습니다.|  
|87|충돌 하는 유형의 도메인 컨트롤러 계정이 있습니다.|빈된 도메인 컨트롤러에 연결 하려고 없는 경우, 홍보 하기 전에 컴퓨터를 이름을 바꿉니다. 빈된 도메인 컨트롤러 계정을 사용 하 여 연결 해야 **-useexistingaccount** 계정 유형에 따라 올바른 고 읽기 전용 또는 쓸 수 인수|  
|88|지정 된 서버 관리 잘못 되었습니다.|잘못 된 계정을 RODC 관리자 위임 지정 했습니다. 유효한 사용자 또는 그룹 지정 된 계정 인지 확인|  
|89|지정된 된 도메인에 대 한 제거 마스터 오프 라인입니다.|사용 하 여 **netdom.exe 쿼리 fsmo** RID 마스터 검색할 수 있습니다. 홍보 된 도메인 컨트롤러에 액세스할 수 있도록 하 고 온라인 상태로|  
|90|도메인 이름 지정 마스터 오프 라인 상태입니다.|사용 하 여 **netdom.exe 쿼리 fsmo** 도메인 이름 지정 마스터 검색할 수 있습니다. 홍보 된 도메인 컨트롤러에 액세스할 수 있도록 하 고 온라인 상태로|  
|91|경우에 과정이 w o w 64을 감지 하지 못했습니다.|*이 오류가 발생할 수 없습니다. 더 이상, 운영 체제는 64 비트*|  
|92|W o w 64 프로세스가 지원 되지 않으면|*이 오류가 발생할 수 없습니다. 더 이상, 운영 체제는 64 비트*|  
|93|도메인 컨트롤러 서비스가 설득력 수준 내리기에 대 한 실행 되지 않으면|AD DS 서비스를 시작|  
|94|로컬 관리자 암호 요구 사항을 충족 하지 않습니다: 빈 나 필요 하지 않음|공백 암호를 입력 하 고 로컬 암호 정책을 암호가 필요한 있는지 확인|  
|95|마지막 Windows Server 2008 또는 라이브 Rodc 존재 되는 도메인의 이후 도메인 컨트롤러 내릴 수 없는|일부 Windows Server 2008 또는 이상 쓸 수 있는 도메인 컨트롤러 내릴 수 전에 모든 Rodc 내리기 먼저 해야|  
|96|DS 바이너리 제거할 수 없습니다.|*Dcpromo /unattend, 더 이상 사용 되는와 에서만 나타납니다. 오래 된 설명서를 참조*|  
|97|숲 기능 수준 보다 높은 버전 자식 도메인 운영 체제의|동일한 또는 숲 기능 수준 보다 높은 자녀 도메인 기능을 제공합니다|  
|98|구성 요소 이진 설치/제거 진행 중입니다.|*Dcpromo /unattend, 더 이상 사용 되는와 에서만 나타납니다. 오래 된 설명서를 참조*|  
|99|숲 기능 수준을 너무 낮습니다 (오류는 Windows Server 2012만)|숲 기능 수준을 이상 발생 기본 Windows Server 2003 합니다. Windows 2000 및 Windows NT 4.0는 더 이상 지원 되는 운영 체제|  
|100|도메인 기능 수준을 너무 낮습니다 (오류는 Windows Server 2012만)|도메인 기능 수준을 이상 발생 기본 Windows Server 2003 합니다. Windows 2000 및 Windows NT 4.0는 더 이상 지원 되는 운영 체제|  
  
#### <a name="knownlikely-issues-and-support-scenarios"></a>가능성이/알려진 문제 및 지원 시나리오  
Windows Server 2012 개발 과정에서 나타납니다 일반적인 문제는 다음과 같습니다. 이러한 문제의 모든 "으로 설계" 되 고 유효한 해결 또는 더 적합 한 기술 처음부터 되지 않도록 합니다. 이러한 동작이 중 상당수는 Windows Server 2008 R2 및 이전 운영 체제에 동일 하지만 AD DS 배포 다시 쓰기 강화 된 감도 문제를 제공 합니다.  
  
|문제|없이 영역으로 실행 DNS 도메인 컨트롤러 내리기 잎|  
|---------|-----------------------------------------------------------------|  
|증상이|여전히 DNS 요청에 응답 하지만 영역 정보가 없는 서버|  
|해상도 및 노트|AD DS 역할을 제거 하는 경우 DNS 서버 역할은 제거 하거나 DNS 서버 서비스를 사용 하지 않도록 설정 수도 있습니다. DNS 클라이언트 보다 자체 다른 서버 가리켜 해야 합니다. Windows PowerShell를 사용 하는 경우 서버 내리기 후 다음을 실행 합니다.<br /><br />코드-제거 windowsfeature dns<br /><br />또는<br /><br />코드-서비스 설정 dns-시작 형식을 사용 안 함<br />Dns 중지 서비스|  
  
|문제|Windows Server 2012 기존 단일 레이블 도메인 홍보 updatetopleveldomain 구성 하지 않는 = 1 또는 allowsinglelabeldnsdomain = 1|  
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------|  
|증상이|기록 동적 DNS 등록 발생 하지 않으면|  
|해상도 및 노트|이 값 Netlogon 및 DNS 그룹 정책을 사용 하 여 설정 합니다. Microsoft은 Windows Server 2008,의 단일 레이블 도메인 만들기 차단 시작 했습니다. 승인 된 DNS 도메인 구조를 변경 하려면 ADMT 또는 도메인 이름 바꾸기 도구를 사용할 수 있습니다.|  
  
|문제|미리 작성, 빈 RODC 계정이 있는 경우 도메인에 있는 마지막 도메인 컨트롤러의 수준 내리기 실패|  
|---------|------------------------------------------------------------------------------------------------------------|  
|증상이|수준 내리기 메시지와 함께 실패합니다.<br /><br />**Dcpromo.General.54**<br /><br />Active Directory Domain Services 디렉터리 파티션에 CN 남은 데이터 전송에 다른 Active Directory 도메인 컨트롤러를 찾을 수 없습니다 CN 스키마 = = 구성 DC corp, DC = DC contoso = com = 합니다.<br /><br />"지정된 도메인 이름 형식은 잘못 되었습니다."|  
|해상도 및 노트|미리 도메인 내리기 하기 전에 RODC 계정을 만든 남은 제거를 사용 하 여 **차례로** 또는 **Ntdsutil.exe 메타 데이터 정리**합니다.|  
  
|문제|자동된 숲 및 도메인 준비 GPPREP 실행 되지 않으면|  
|---------|---------------------------------------------------------------|  
|증상이|결과 설정의 정책 RSOP () 계획 모드, 그룹 정책에 대 한 계획 기능 도메인 간 기존 GP에 대 한 업데이트 파일 시스템 및 Active Directory 사용 권한 필요합니다. Gpprep를 않고도 사용할 수 없습니다 RSOP 계획 도메인.|  
|해상도 및 노트|실행 **adprep.exe /gpprep** 이전에 Windows Server 2003, Windows Server 2008 또는 Windows Server 2008 r 2에 대 한 준비 되지 된 모든 도메인에 대 한 수동으로 합니다. 모든 업그레이드를 되지 도메인 기록 관리자 GPPrep 한 번만 실행 해야 합니다. 사용자 지정 적절 한 권한이 이미 설정한 경우 모든 도메인 컨트롤러에 다시 복제할 모든 SYSVOL 내용을 발생할 수 있으므로 자동 adprep는 실행 되지 않습니다.|  
  
|문제|설치 미디어에서 실패 때 향하게 UNC 경로를 확인 하려면|  
|---------|------------------------------------------------------------------|  
|증상이|오류:<br /><br />코드-미디어 경로 확인할 수 없습니다. "GetDatabaseInfo"와 "2" 인수 통화 예외입니다. 폴더가 잘못 되었습니다.|  
|해상도 및 노트|원격 UNC 경로 하지는 로컬 디스크 IFM 파일을 저장 해야 합니다. 이 의도적 블록 네트워크 중단으로 인해 부분 서버 프로 모션을 수 없습니다.|  
  
|문제|DNS 위임 경고 도메인 컨트롤러 프로 모션 동안 두 번 표시|  
|---------|-------------------------------------------------------------------------|  
|증상이|반환 경고 *두 번* ADDSDeployment Windows PowerShell를 사용 하 여 홍보 하는 경우:<br /><br />코드 – "이 DNS 서버에 대 한 위임 부모 신뢰할 수 있는 영역 찾을 수 없거나 Windows DNS 실행 되지 않는 만들 수 없습니다 서버 합니다. 기존 DNS 인프라와 통합 하는 경우 수동으로 만들어야이 DNS 서버를 위임 도메인 외부에서 신뢰할 수 있는 이름 확인 하도록 부모 영역에 합니다. 그렇지 않으면 작업이 필요 하지 않습니다. "|  
|해상도 및 노트|무시 합니다. ADDSDeployment Windows PowerShell 필수 확인 하는 동안 처음 다음 다시 구성 하는 도메인 컨트롤러의 동안 경고를 표시합니다. DNS 위임 구성 하려면 인수 사용:<br /><br />코드--creatednsdelegation: $false<br /><br />수행 *하지* 이 메시지가 표시 되지 않도록 하려면 필수 검사 건너뛸|  
  
|문제|잘못 된 오류 구성 하는 동안 UPN 또는 도메인 비 자격 증명을 지정 반환|  
|---------|--------------------------------------------------------------------------------------------|  
|증상이|서버 관리자 반환 오류가 발생을 합니다.<br /><br />코드-"DNSOption"와 "6" 인수 통화 예외<br /><br />오류를 반환 ADDSDeployment Windows PowerShell:<br /><br />사용자의 사용 권한 확인 코드-하지 못했습니다. 사용자 계정의 속해 있는 도메인의 이름을 입력 해야 합니다.|  
|해상도 및 노트|유효한 도메인 자격 증명 형식으로 제공 하 고 있는지 확인 **도메인 \ 사용자**합니다.|  
  
|문제|Dism.exe를 사용 하 여 위해 도메인 컨트롤러 역할을 제거 부팅할 서버에 연결|  
|---------|---------------------------------------------------------------------------------------------------|  
|증상이|Dism.exe에 사용 하 여 정상적으로 도메인 컨트롤러 내리기 하기 전에 AD DS 역할을 제거 하는 경우 더 이상 서버 일반적으로 부팅 되 고 오류가 표시 합니다.<br /><br />코드-상태: 0x000000000<br />정보: 오류가 발생 했습니다.|  
|해상도 및 노트|디렉터리 서비스 복구 모드를 사용 하 여에 부팅 *Shift + f 8*합니다. AD DS 역할을 다시를 추가 하 고 도메인 컨트롤러 수준을 강제로 합니다. 또한 시스템 상태 백업에서 복원 합니다. Dism.exe AD DS 역할 제거;를 사용 하지 않음 유틸리티 모르는 도메인 컨트롤러에 있습니다.|  
  
|문제|포리스트의 Win2012를 설정할 때 새로 숲 설치가 실패|  
|---------|--------------------------------------------------------------------|  
|증상이|프로 모션 Windows PowerShell ADDSDeployment 사용 하 여 반환 오류가 발생을 합니다.<br /><br />코드-Test.VerifyDcPromoCore.DCPromo.General.74<br /><br />프로 모션 도메인 컨트롤러 사항 확인 하지 못했습니다. 지정 된 도메인 기능 수준을 잘못 되었습니다.|  
|해상도 및 노트|없이 Win2012의 숲 기능 모드 지정 하지 않은 *도* 도메인 기능 모드 Win2012의 지정 합니다. 오류 하지 않고는 작동 하는 예는 다음과 같습니다.<br /><br />코드--포리스트의 Win2012-domainmode Win2012]|  
  
|||  
|-|-|  
|문제|아무것도 할 표시 되 고 설치 미디어 선택 영역에서의 확인을 클릭|  
|증상이|때 사용자가 지정 경로 IFM 폴더를 클릭 하 고 **확인** 단추 메시지를 반환 되지 않거나 아무것도 할 나타납니다.|  
|해상도 및 노트|**확인** 단추 반환 오류 문제가 있을 경우 합니다. 그렇지 않은 경우는 **다음** 단추 IFM 경로 제공 하는 선택할 수 있습니다. 클릭 해야 **확인** IFM 선택한 경우 계속 진행 합니다.|  
  
|||  
|-|-|  
|문제|서버 관리자와 내리기 피드백 완료 될 때까지 제공 되지 않습니다.|  
|증상이|AD DS 역할 제거한 내리기 도메인 컨트롤러 서버 관리자를 사용 하는 경우 수준 내리기 치거나 실패 될 때까지 자녀에 게 부여 지속적인 피드백이 없으면입니다.|  
|해상도 및 노트|제한이 서버의 관리자입니다. 피드백을 ADDSDeployment Windows PowerShell cmdlet 사용:<br /><br />코드-Uninstall-addsdomaincontroller|  
  
|||  
|-|-|  
|문제|설치 미디어를 확인에서 쓰기 도메인 컨트롤러에 대 한 끌거나 그 반대로 제공 RODC 미디어를 검색 하지 않습니다.|  
|증상이|IFM를 사용 하 고 쓸 수 있는 도메인 컨트롤러에 대 한 RODC 미디어 또는 RODC RWDC 미디어--등 IFM에 잘못 된 미디어를 제공 하는 도메인 컨트롤러 새 사항을 홍보 하기 위한 때 확인 단추 오류를 반환 되지 않습니다. 나중에 프로 모션 오류와 함께 실패합니다.<br /><br />코드-이 기계 도메인 컨트롤러를 구성 하는 동안 오류가 발생 했습니다. <br />Install-From-Media 프로 모션에 Read-Only 지정된 소스 데이터베이스는 허용 되지 않으므로 DC 시작할 수 없습니다. 한 쉽습니다 IFM 프로 모션에 대 한 다른 Rodc에서 데이터베이스에만 사용할 수 있습니다.|  
|해상도 및 노트|확인만 전체 무결성 IFM의 유효성을 검사 합니다. 서버에 잘못 된 IFM 종류를 제공 하지 않습니다. 프로 모션 올바른 미디어를 사용 하 여 다시 시도 하기 전에 서버를 다시 시작 합니다.|  
  
|||  
|-|-|  
|문제|컴퓨터 미리 작성된 된 계정에 RODC 사항을 홍보 하기 위한 실패|  
|증상이|Windows PowerShell ADDSDeployment 사용 하 여 홍보 준비 된 컴퓨터에 계정으로 새로운 RODC 오류를 메시지가 나타납니다.<br /><br />코드-매개 설정 지정 된 이름이 매개 변수를 사용 하 여 확인할 수 없습니다.    <br />인수: ParameterBindingException<br />    + FullyQualifiedErrorId: AmbiguousParameterSet Microsoft.DirectoryServices.Deployment.PowerShell.Commands.Install|  
|해상도 및 노트|이미 RODC 미리 작성된 된 계정에 이미 정의 매개 변수를 제공 하지 않습니다. 이러한 다음과 같습니다.<br /><br />코드--readonlyreplica<br />-installdns<br />-donotconfigureglobalcatalog<br />-sitename<br />-installdns|  
  
|||  
|-|-|  
|문제|아무 것도 선택 취소 하면/선택 "각 대상 서버 자동으로 다시 시작 필요"|  
|증상이|(선택 하거나 선택 하지) 경우 서버 관리자 옵션 **요구 하는 경우 각 대상 서버를 자동으로 다시 시작** whendemoting 역할 제거 통해 도메인 컨트롤러 서버 항상 다시 시작 되 면 선택 관계 합니다.|  
|해상도 및 노트|의도입니다. 수준 내리기 프로세스가이 설정과 관계 없이 서버를 다시 시작 합니다.|  
  
|||  
|-|-|  
|문제|Dcpromo.log "[오류] 2 실패 서버 파일에서 보안을 설정"를 보여 줍니다.|  
|증상이|문제를 않고도 도메인 컨트롤러의 수준 내리기 완료 하지만 dcpromo 로그 살펴보면 오류:<br /><br />2 코드-[오류] 서버 파일에서 보안을 설정 하지 못했습니다.|  
|해상도 및 노트|예상 되 고 코스메틱 오류는, 무시 합니다.|  
  
|||  
|-|-|  
|문제|"Exchange 스키마 충돌 검사를 수행할 수 없습니다" 오류가 발생 하 여 필수 adprep 검사가 실패|  
|증상이|Windows Server 2012 도메인 컨트롤러에 기존 Windows Server 2003, Windows Server 2008 또는 Windows Server 2008 R2 숲 홍보를 하려고 하면 오류가 발생 하 여 필수 검사가 실패 하면:<br /><br />코드-필수 광고 준비에 대 한 검증 실패 했습니다. 도메인에 대 한 Exchange 스키마 충돌 검사를 수행할 수 없습니다 *<domain name>* (예외: RPC 서버를 사용할 수 있는)<br /><br />Adprep.log 오류를 표시 합니다.<br /><br />코드-Adprep 서버에서 데이터를 검색 하지 못했습니다.*<domain controller>*<br /><br />통해 WMI(Windows Management Instrumentation) (WMI).|  
|해상도 및 노트|새 도메인 컨트롤러 WMI DCOM/RPC 프로토콜 기존 도메인 컨트롤러에 대해를 통해 액세스할 수 없습니다. 현재이 대 한 세 개의 원인을 사항이 있습니다.<br /><br />-방화벽 규칙 사용할 수 없게 기존 도메인 컨트롤러<br /><br />-"로그온 as a service" 네트워크 서비스 계정 없거나 기존 도메인 컨트롤러의 (SeServiceLogonRight) 권한<br /><br />NTLM 불가능 도메인 컨트롤러의 보안 정책에 명시 된를 사용 하 여 [NTLM 제한 인증 소개](https://technet.microsoft.com/library/dd560653(WS.10).aspx)|  
  
|||  
|-|-|  
|문제|DNS 경고를 표시 새 AD DS 숲 항상 만들기|  
|증상이|때 새 AD DS 숲 만들고 항상 자체에 대 한 새 도메인 컨트롤러에 DNS 영역 만들기 경고 메시지가 나타납니다.<br /><br />오류 코드 DNS 구성에서 발견 되었습니다. <br />이 컴퓨터에서 사용 하는 DNS 서버 대기 시간 내에 응답 합니다.<br />(오류 코드 0x000005B4 "ERROR_TIMEOUT")|  
|해상도 및 노트|무시 합니다. 이 경고는 기존 DNS 서버 및 영역 가리키도록 원하는 경우 새 숲 루트 도메인의 첫 번째 도메인 컨트롤러에서 의도적 합니다.|  
  
|||  
|-|-|  
|문제|Windows PowerShell-whatif 인수 반환 잘못 DNS 서버 정보|  
|증상이|사용 하는 경우는 **-whatif** 암시적 또는 명시적으로 도메인 컨트롤러를 구성할 때 인수 **-installdns: $true**, 그 결과 프로그램 출력:<br /><br />코드 – "DNS 서버: 없음"|  
|해상도 및 노트|무시 합니다. DNS 설치 되 고 올바르게 구성 되어 있습니다.|  
  
|||  
|-|-|  
|문제|프로 모션을 후 로그온 실패 "저장소가 부족이 명령은 처리할 수 있을 때"|  
|증상이|새 도메인 컨트롤러를 홍보 하 고 다음 로그 오프 한 대화형에 로그인 하려고 하면 오류가 발생을 나타납니다.<br /><br />이 명령을 처리할 수 있을 때 코드-storage 부족 합니다.|  
|해상도 및 노트|도메인 컨트롤러를 프로 모션 오류로 인해 후 다시 부팅 되지 ADDSDeployment Windows PowerShell 인수 지정 때문에 또는 **-norebootoncompletion**합니다. 도메인 컨트롤러를 다시 시작 합니다.|  
  
|||  
|-|-|  
|문제|다음 단추 도메인 컨트롤러 옵션 페이지에서 사용할 수 없으면|  
|증상이|암호를 설정한 경우에 있는 **다음** 단추는 **도메인 컨트롤러 옵션** 서버 관리자의 페이지를 사용할 수 없습니다. 에 나열 된 사이트인는 **사이트 이름** 메뉴 합니다.|  
|해상도 및 노트|여러 AD DS 사이트가 있고 하나 이상 누락 서브넷; 이 향후 도메인 컨트롤러 서브넷 중 하나에 속해 있습니다. 수동으로 서브넷 사이트 이름 드롭다운 메뉴에서 선택 해야 합니다. 또한 DSSITE.MSC 또는 모두 찾으려면 Windows PowerShell 다음 명령 사용 하 여 누락 서브넷 사이트 다음과 같습니다.<br /><br />코드-get adreplicationsite-필터 *-속성 서브넷 & #124; where-object {! $_.subnets eq "\ *"} & #124; 표 서식 이름|  
  
|||  
|-|-|  
|문제|프로 모션 또는 수준 내리기 메시지 "서비스 시작할 수 없습니다"와 함께 실패|  
|증상이|프로 모션, 수준 내리기, 또는 도메인 컨트롤러의 복제 시도 하면 오류가 발생 합니다.<br /><br />코드-서비스를 시작할 수 없는, 하거나 있기 때문에 사용 안 함에 연결 된 장치가 활성화 된"(0x80070422)<br /><br />오류 대화형 수 이벤트를 또는 dcpromoui.log 또는 dcpromo.log 같은 로그에 기록|  
|해상도 및 노트|DS 역할 서버 서비스 (DsRoleSvc)는 사용할 수 없습니다. 이 서비스는 기본적으로 AD DS 역할을 설치 하는 동안 설치 하며 수동 시작 유형으로 설정 합니다. 이 서비스를 비활성화 하지 않습니다. 수동으로 다시 설정 하 고 시작 하 고 필요에 따라 중지 DS 역할 작업을 허용 합니다. 이 동작으로 설계입니다.|  
  
|||  
|-|-|  
|문제|DC 홍보 해야 하는 여전히 서버 관리자에 게 경으십시오|  
|증상이|서버 관리자 배포 후 구성 작업을 계속 표시 도메인 컨트롤러 사용 되지 않는 dcpromo.exe /unattend를 사용 하 여 홍보 또는 Windows Server 2012 기존 Windows Server 2008 R2 도메인 컨트롤러 곳에서 업그레이드 하는 경우 **도메인 컨트롤러이 서버 홍보**합니다.|  
|해상도 및 노트|배포 후 경고 링크를 클릭 하 고 선의의에 게 메시지가 나타나지 것입니다. 이 동작은 코스메틱 및 예상 합니다.|  
  
|||  
|-|-|  
|문제|서버 관리자 배포 스크립트 누락 역할 설치|  
|증상이|도메인 컨트롤러 서버 관리자를 사용 하 여 홍보를 Windows PowerShell 배포 스크립트 저장 포함 되지 않습니다 역할 설치 cmdlet 및 인수 (windowsfeature 설치-이름을 includemanagementtools 광고 도메인-서비스). 역할을 않고도 DC 구성할 수 없습니다.|  
|해상도 및 노트|해당 cmdlet 수동으로 추가 스크립트에 인수 하 고 있습니다. 이 문제는 예상 디자인 하 고 있습니다.|  
  
|||  
|-|-|  
|문제|서버 관리자 배포 스크립트 PS1 이름을 지정 하지 않은|  
|증상이|도메인 컨트롤러 서버 관리자를 사용 하 여 홍보 배포 Windows PowerShell 스크립트를 저장 하는 경우 해당 파일 임의 임시 이름의 및 PS1 파일 아니라 이라고 합니다.|  
|해상도 및 노트|수동으로 파일을 이름을 바꿉니다. 이 문제는 예상 디자인 하 고 있습니다.|  
  
|문제|Dcpromo /unattend 지원 하지 않는 기능 수준 허용|  
|-|-|  
|증상이|다음 샘플 응답 파일 dcpromo /unattend 사용 하는 도메인 컨트롤러 홍보 하는 경우:<br /><br />코드-<br /><br />[DCInstall]<br />새 도메인 = 숲<br /><br />ReplicaOrNewDomain 도메인 =<br /><br />NewDomainDNSName corp.contoso.com =<br /><br />SafeModeAdminPassword =Safepassword@6<br /><br />DomainNetbiosName corp =<br /><br />DNSOnNetwork = 예<br /><br />AutoConfigDNS = 예<br /><br />RebootOnSuccess NoAndNoPromptEither =<br /><br />RebootOnCompletion = 없음<br /><br />*DomainLevel = 0*<br /><br />*ForestLevel = 0*<br /><br />프로 모션 dcpromoui.log에에서는 다음과 같은 오류와 함께 실패합니다.<br /><br />코드-dcpromoui EA4.5B8 0089 13:31:50.783 Enter CArgumentsSpec::ValidateArgument DomainLevel<br /><br />Dcpromoui EA4.5B8 008A 13:31:50.783 DomainLevel에 대 한 값은 0<br /><br />Dcpromoui EA4.5B8 008B 13:31:50.783 종료 코드는 77<br /><br />Dcpromoui EA4.5B8 008 C 13:31:50.783 지정된 인수가 잘못 되었습니다.<br /><br />Dcpromoui EA4.5B8 008 D 13:31:50.783 닫는 로그<br /><br />Dcpromoui EA4.5B8 0032 13:31:50.830 종료 코드는 77<br /><br />0 수준은 Windows 2000에 Windows Server 2012에서 지원 되지 않습니다.|  
|해상도 및 노트|수행 하지 사용 되지 않는 dcpromo /unattend 이해 하 고 사용할 수 있다는 잘못 된 설정을 지정 하려면 이후 실패 합니다. 이 문제는 예상 디자인 하 고 있습니다.|  

|문제|완료 되지 않고 프로 모션 "중단" NTDS 설정을 개체 만들기|  
|-|-|  
|증상이|DC 또는 RODC 복제본을 홍보 하는 경우 프로 모션에 도달 "만들 NTDS 설정을 개체" 하 고 절대 진행 하거나 완료 합니다. 로그도 업데이트를 중지 합니다.|  
|해상도 및 노트|이 기본 제공 되는 도메인 관리자 계정에 일치 하는 암호로 기본 제공 되는 로컬 관리자 계정 자격 증명을 제공 하 여 발생 하는 알려진된 문제가 있습니다. 이 인해 오류가 아래로 핵심 설치 엔진 않는 오류가 아니라 대신 대기 무기한 (준 루프). 이 정상적인 동작-원하지 않는-하지만 동작 합니다.<br /><br />서버를 해결 합니다.<br /><br />1. 재부팅 됩니다.<br /><br />1.에서 광고를 (아직 되지 것입니다 DC 계정) 서버의 회원 컴퓨터 계정 삭제<br /><br />1. 해당 서버에서 강제로 분리 하는 도메인의<br /><br />1. 해당 서버에서 AD DS 역할을 제거 합니다.<br /><br />1입니다. 다시 부팅<br /><br />1. 다시 추가 AD DS 역할 및 reattempt 프로 모션을 항상 제공 하는 보장는 ***domain\admin*** 자격 증명을 DC 모션과 기본 로컬 관리자 계정 뿐 아니라 포맷|  