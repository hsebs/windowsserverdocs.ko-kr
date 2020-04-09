---
ms.assetid: 6a852428-c1ec-4703-b3b3-a4bfdf8cbb9d
title: Windows Server 2016에 Active Directory Domain Services의 새로운 기능
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/07/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: a82f45772e5e35afffc632de2b40c02c75b5e5e4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856286"
---
# <a name="whats-new-in-active-directory-domain-services-for-windows-server-2016"></a>Active Directory 도메인 서비스에 대 한 Windows Server 2016의 새로운 기능

>적용 대상: Windows Server 2016

Active Directory 도메인 서비스 (AD DS)에서 다음과 같은 새로운 기능이 Active Directory 환경 보안을 유지 하 고 클라우드 전용 배포 및 하이브리드 배포, 여기서 클라우드에서 호스팅되는 일부 애플리케이션 및 서비스 하 고 온-프레미스에서 호스팅되는 다른 사용자로 마이그레이션할 수 있도록 지원 하는 조직 위한 능력을 개선 합니다. 다음과 같은 향상 된 기능  
  
- [권한 있는 액세스 관리](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services)  
  
- [Azure Active Directory Join을 통해 클라우드 기능을 Windows 10 장치로 확장](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-overview/)
  
- [도메인에 가입 된 장치를 Windows 10 용 Azure AD 환경에 연결](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/)
  
- [조직에서 Microsoft Passport for Work 사용](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-passport-deployment/)
  
- [FRS (파일 복제 서비스) 및 Windows Server 2003 기능 수준 사용 중단](ad-ds/active-directory-functional-levels.md)  
  
## <a name="privileged-access-management"></a>권한 있는 액세스 관리

권한 있는 액세스 관리 (PAM) 보안을 완화 하 여 발생 하는 Active Directory 환경에 대 한 문제 이러한 해시를 패스, 창 피싱 및 이와 유사한 종류의 공격 도난 기술을 자격 증명입니다. MIM Microsoft Identity Manager ()를 사용 하 여 구성 된 새로운 관리 액세스 솔루션을 제공 합니다. PAM 도입 되었습니다.  
  
- 새 요새 Active Directory 포리스트에 있는 MIM으로 프로 비전 됩니다. 요새 포리스트는 기존 포리스트에 한 특별 한 PAM 트러스트 합니다. 권한이 있는 소수의 계정 사용에 대 한 기존 포리스트 로부터 격리 및 악의적인 활동의 사용 가능한 것으로 알려진 새 Active Directory 환경을 제공 합니다.  
  
- 승인 요청을 기반으로 하는 새 워크플로 함께 관리 권한을 요청할 MIM에서 새로운 프로세스입니다.  
  
- 새 섀도 보안 주체 (그룹) 프로 비전 되는 요새 포리스트의 MIM에서 관리자 권한 요청에 응답 합니다. 그림자 보안 주체에 기존 포리스트에 있는 관리 그룹의 SID를 참조 하는 특성이 있습니다. 이렇게 하면 모든 액세스 제어 목록 (Acl)을 변경 하지 않고 기존 포리스트에 있는 리소스에 액세스 하는 섀도 그룹.  
  
- 만료 되는 기능 시간 제한이 섀도 그룹 멤버 자격을 연결 합니다. 사용자 관리 작업을 수행 하는 데 필요한 충분 한 시간에 대 한 그룹에 추가할 수 있습니다. 시간 범위 구성원은 Kerberos 티켓 수명을로 전파 되는 활성 시간 (TTL) 값으로 표현 됩니다.  
  
    > [!NOTE]  
    > 만료 링크는 연결 된 모든 특성에서 사용할 수 있습니다. 하지만 멤버/memberOf 연결 된 특성 그룹 및 사용자 간의 관계는 유일한 예 PAM 같은 완전 한 솔루션 만료 링크 기능을 사용 하도록 미리 구성 합니다.  
  
- KDC 향상 된 기능에서 가능한 활성 시간 (TTL) 최소값인 사용자 관리 그룹에 여러 개의 시간 범위 구성원 자격에 있는 경우에서 Kerberos 티켓 수명을 제한 하려면 Active Directory 도메인 컨트롤러에 빌드됩니다. 예를 들어 Kerberos 티켓 부여 티켓 (TGT) 수명 시간이 로그온 할 때 시간 제한 그룹 A를에 추가 된 경우 하기만 하면 그룹 a 다른 시간 제한 그룹 B는 그룹 A 보다 낮은 TTL의 구성원 인 경우 다음 TGT 수명을 크거나 2. 그룹에 남아 있는 시간  
  
- 쉽게 새 모니터링 기능에는 액세스를 요청한 사용자, 액세스 권한 부여 되었는지와 어떤 활동이 수행 된 식별 합니다.  

### <a name="requirements-for-privileged-access-management"></a>권한 있는 액세스 관리를 위한 요구 사항
  
- Microsoft ID 관리자  
  
- Active Directory 포리스트 기능 수준을 Windows Server 2012 R2 이상.  
  
## <a name="azure-ad-join"></a>Azure AD 조인

Azure Active Directory 조인을 회사 및 개인 디바이스에 대 한 향상 된 기능을 통해 엔터프라이즈, 비즈니스 및 EDU 고객-identity 환경을 향상 시킵니다.  
  
이점:  
  
- **최신 설정을 사용할** 회사 소유 Windows 장치에 있습니다. 산소 Services에는 더 이상 개인 Microsoft 계정 필요 하지 않습니다. 이제 사용자의 기존 회사 계정을 사용 하 여 규정 준수를 보장 합니다. 산소 Services는 온-프레미스 Windows 도메인에 가입한 Pc와, Azure AD 테 넌 트에 "가입" 된 Pc 및 장치 ("클라우드 도메인")에서 작동 합니다. 이러한 설정은 다음과 같습니다.  

   - 로밍 또는 개인 설정, 내게 필요한 옵션 설정 및 자격 증명  
   - 백업 및 복원  
   - 회사 계정을 사용 하 여 Microsoft Store에 액세스  
   - 라이브 타일 및 알림  
  
- 회사 소유 또는 BYOD와 상관 없이 Windows 도메인에 조인할 수 없는 모바일 장치 (휴대폰, phablets)의 **조직 리소스에 액세스** 합니다.  
- **Single Sign On** Office 365 및 기타 조직 앱, 웹 사이트 및 리소스에 있습니다.  
- **BYOD 장치**, 개인 소유 장치에 회사 계정 (온-프레미스 도메인 또는 Azure AD)에서 추가 하 고는 유지할 규정 준수 증명과 조건부 계정 제어 및 장치 상태 같은 새로운 기능을 사용 하는 방법에서 리소스, 앱 및 웹에서 작업 하는 SSO를 이용할 수 있습니다.  
- **MDM 통합** 장치에 MDM (Intune 또는 제 3 자)를 자동으로 등록 하면  
- **"키오스크" 모드를 설정 하 고 공유 장치** 조직에서 여러 사용자에 대 한  
- **개발자 환경을** 기업 및 개인 컨텍스트 공유 프로그래밍 스택을를 모두 제공 하는 앱을 빌드할 수 있습니다.  
- **이미징** 옵션을 사용 하는 첫 실행 경험 동안 직접 회사 소유의 장치를 구성 하 고 사용자가 허용 하는 이미징 중에서 선택할 수 있습니다.  
  
자세한 내용은 [Azure Active Directory의 장치 관리 소개](https://docs.microsoft.com/azure/active-directory/devices/overview)를 참조 하세요.  
  
## <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello

비즈니스용 Windows Hello는 암호를 초과 하는 키 기반 인증 방법으로, 조직 및 소비자입니다. 이 형태의 인증 위반, 도난 및 phish에 안전한 자격 증명에 의존합니다.  
  
사용자는 인증서 또는 비대칭 키 쌍에 연결 된 정보에 대 한 생체 인식 또는 PIN 로그를 사용 하 여, 디바이스에 로그온 합니다. Id 공급자 (IDPs)는 사용자의 공개 키를 Idps에 매핑하여 사용자의 유효성을 검사 하 고 OTP (일회용 암호), 휴대폰 또는 다른 알림 메커니즘을 통해 정보에 대 한 로그를 제공 합니다.  
  
자세한 내용은 [비즈니스용 Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification) 를 참조 하세요.  
  
## <a name="deprecation-of-file-replication-service-frs-and-windows-server-2003-functional-levels"></a>사용 중단의 FRS 파일 복제 서비스 () 및 Windows Server 2003 기능 수준

복제 서비스 FRS (파일) 및 Windows Server 2003 기능 수준 이전 버전의 Windows Server에서 사용 되지 않는, 하지만 반복 되는 Windows Server 2003 운영 체제 더 이상 지원 되지. 결과적으로, Windows Server 2003을 실행 하는 도메인 컨트롤러가 도메인에서 제거 해야 합니다. 도메인 및 포리스트 기능 수준을 발생 이상 환경에 추가 되 고 이전 버전의 Windows Server를 실행 하는 도메인 컨트롤러를 방지 하기 위해 Windows Server 2008입니다.

Windows Server 2008 및 더 높은 도메인 기능 수준에서 서비스 DFS (분산 파일) 복제 도메인 컨트롤러 간에 SYSVOL 폴더 내용을 복제 하는 데 사용 됩니다. Windows Server 2008 도메인 기능 수준 이상의 새 도메인을 만들면 DFS 복제 SYSVOL을 복제 하는 데 자동으로 사용 됩니다. 더 낮은 기능 수준에서 도메인을 만든 경우 FRS를 사용 하 여 SYSVOL에 대 한 DFS 복제에서 마이그레이션할 해야 합니다. 마이그레이션 단계를 수행 하려면 [다음 단계](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640019\(v=ws.10\)) 를 수행 하거나 [저장소 팀 파일 캐비닛 블로그의 간소화 된 단계](https://blogs.technet.com/b/filecab/archive/2014/06/25/streamlined-migration-of-frs-to-dfsr-sysvol.aspx)를 참조할 수 있습니다.  
  
Windows Server 2003 도메인 및 포리스트 기능 수준 계속 지원 될 수 있지만 조직 기능 수준을 Windows Server 2008 (이상으로 가능한 경우)를 발생 시켜야 하 SYSVOL 복제 호환성을 보장 하 고 나중에 지원 합니다. 또한 개 많은 혜택 및 기타 기능이 사용 가능한 더 높은 기능 수준을 더 높은 있습니다. 자세한 내용은 다음 리소스를 참조하세요.  

- [Active Directory Domain Services (AD DS) 기능 수준 이해](ad-ds/active-directory-functional-levels.md)  
- [도메인 기능 수준 올리기](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753104\(v=ws.11\))  
- [포리스트 기능 수준 올리기](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730985\(v=ws.11\))  
