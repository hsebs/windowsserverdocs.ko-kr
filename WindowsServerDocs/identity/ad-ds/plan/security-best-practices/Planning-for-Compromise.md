---
ms.assetid: 6f50476c-a1f1-48fb-999b-76c4c3816496
title: 손상 계획
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 5dcbea1ae0bd84ed517644d7c4fde03852bef304
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80821116"
---
# <a name="planning-for-compromise"></a>손상 계획

>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

*법률 번호 1: 오류가 발생할 때까지 잘못 된 것으로 간주 될 수 있습니다.* - [10 가지 불변의 보안 관리 법칙](https://technet.microsoft.com/library/cc722488.aspx)  
  
많은 조직의 재해 복구 계획은 컴퓨팅 서비스의 손실을 초래 하는 지역 재해 또는 오류 로부터 복구 하는 데 중점을 둡니다. 그러나 손상 된 고객으로 작업 하는 경우 의도적인 손상 으로부터 복구 하는 것은 재해 복구 계획에 없다는 것을 발견 하는 경우가 많습니다. 이는 성능 저하로 인해 물리적 경계 (예: 데이터 센터 삭제)가 아닌 논리적 경계 (예: 모든 Active Directory 도메인 또는 모든 서버의 삭제)를 활용 하는 지적 재산 또는 의도적인 소멸을 도용 하는 경우에 특히 그렇습니다. 조직이 손상이 발견 될 때 수행할 초기 작업을 정의 하는 인시던트 대응 계획을 포함할 수 있지만 이러한 계획에서는 전체 컴퓨팅 인프라에 영향을 주는 손상 으로부터 복구 하는 단계를 생략 하기도 합니다.  
  
Active Directory은 사용자, 서버, 워크스테이션 및 응용 프로그램에 대 한 다양 한 id 및 액세스 관리 기능을 제공 하기 때문에 공격자가 대상으로 하는 항상입니다. 공격자가 Active Directory 도메인 또는 도메인 컨트롤러에 대 한 매우 특권 수준의 액세스 권한을 얻을 경우 해당 액세스를 활용 하 여 전체 Active Directory 포리스트를 액세스, 제어 또는 삭제할 수 있습니다.  
  
이 문서에서는 공격 노출 영역을 줄이기 위해 구현할 수 있는 Windows 및 Active Directory에 대 한 가장 일반적인 공격 중 일부에 대해 설명 했지만, Active Directory의 완전 한 손상이 발생할 경우 복구 하는 방법은 손상에 대비 하 여 준비 해야 합니다. 이 섹션에서는이 문서의 이전 섹션 보다 기술 구현에 대 한 세부 정보를 중점적으로 다루고 조직의 중요 한 비즈니스 및 IT 자산을 안전 하 게 보호 하는 포괄적이 고 포괄적인 방법을 만드는 데 사용할 수 있는 고급 권장 사항에 대해 자세히 설명 합니다.  
  
인프라가 공격을 받지 않았거나 resisted 시도 하거나 공격을 succumbed 하 고 완전히 손상 되었는지 여부에 관계 없이 다시 공격 받을 가능성이 있음을 계획 해야 합니다. 공격을 방지 하는 것은 불가능 하지만 심각한 위반 또는 도매 손상을 방지 하는 것이 가능 합니다. 모든 조직은 기존 위험 관리 프로그램을 면밀 하 게 평가 하 고 필요한 사항을 조정 하 여 예방, 감지, 포함 및 복구에 대 한 분산 된 투자를 통해 전반적인 취약점을 줄이는 데 도움을 줍니다.  
  
인프라 및 응용 프로그램을 기반으로 하는 사용자 및 비즈니스에 서비스를 제공 하는 동시에 효과적인 방어를 위해 사용자 환경에서 손상을 방지, 감지 및 포함 하는 novel 방법을 고려 하 여 손상에서 복구 해야 할 수 있습니다. 이 문서의 접근 방법 및 권장 사항은 손상 된 Active Directory 설치를 복구 하는 데 도움이 되지 않을 수 있지만 다음을 보호 하는 데 도움이 될 수 있습니다.  
  
Active Directory 포리스트 복구에 대 한 권장 사항은 [Windows Server 2012: Active Directory 포리스트 복구 계획](https://www.microsoft.com/download/details.aspx?id=16506)에 나와 있습니다. 새 환경이 완전히 손상 되는 것을 방지할 수 있습니다. 하지만 사용할 수 없는 경우에도 사용자 환경을 복구 하 고 제어 하는 도구를 사용할 수 있습니다.  
  
## <a name="rethinking-the-approach"></a>접근 방법 재고  
*법률 번호 8: 네트워크를 방어 하는 어려움은 복잡성에 직접적으로 비례 합니다.* - [10 가지 불변의 보안 관리 법칙](https://technet.microsoft.com/library/cc722488.aspx)  
  
공격자가 운영 체제에 관계 없이 컴퓨터에 대 한 시스템, 관리자, 루트 또는 해당 컴퓨터에 대 한 액세스 권한을 얻은 경우 시스템을 "정리" 하는 데 걸리는 작업량에 관계 없이 해당 컴퓨터를 더 이상 신뢰할 수 없는 것으로 간주 하는 것이 일반적으로 잘 승인 됩니다. Active Directory 다릅니다. 공격자가 도메인 컨트롤러 또는 Active Directory의 높은 권한의 계정에 대 한 권한 있는 액세스 권한을 획득 한 경우 공격자가 수행 하는 모든 수정 사항에 대 한 레코드 또는 알려진 양호한 백업이 없으면 디렉터리를 완전히 신뢰할 수 있는 상태로 복원할 수 없습니다.  
  
공격자가 구성원 서버 또는 워크스테이션을 손상 하 고 변경 하는 경우 컴퓨터는 더 이상 신뢰할 수 없지만 인접 한 손상 되지 않은 서버 및 워크스테이션은 계속 신뢰할 수 있습니다. 한 컴퓨터의 손상으로 인해 모든 컴퓨터가 손상 된 것을 의미 하지는 않습니다.  
  
그러나 Active Directory 도메인에서 모든 도메인 컨트롤러는 동일한 AD DS 데이터베이스의 복제본을 호스팅합니다. 단일 도메인 컨트롤러가 손상 되 고 공격자가 AD DS 데이터베이스를 수정 하는 경우 해당 수정 사항은 도메인의 다른 모든 도메인 컨트롤러에 복제 되 고 수정 되는 파티션에 따라 포리스트를 변경 합니다. 포리스트에 있는 모든 도메인 컨트롤러를 다시 설치 하는 경우에도 AD DS 데이터베이스가 상주 하는 호스트를 다시 설치 하기만 하면 됩니다. Active Directory를 악의적으로 수정 하면 새로 설치 된 도메인 컨트롤러에 몇 년 동안 실행 되는 도메인 컨트롤러에 복제 하는 것 처럼 쉽게 복제할 수 있습니다.  
  
손상 된 환경을 평가 하는 경우 공격자가 처음에 환경을 손상 시킨 후 첫 번째 위반 "이벤트"가 실제로 몇 주, 몇 달 또는 몇 년 후에 트리거되는 것으로 확인 되었습니다. 공격자는 일반적으로 위반이 감지 되기 전에 매우 특권 수준의 계정에 대 한 자격 증명을 얻고 이러한 계정을 활용 하 여 디렉터리, 도메인 컨트롤러, 구성원 서버, 워크스테이션 및 연결 된 비 Windows 시스템을 손상 시킵니다.  
  
이러한 결과는 Verizon의 2012 데이터 위반 조사 보고서에 나와 있는 여러 가지 결과와 일치 합니다.  
  
-   98 외부 에이전트의 데이터 위반 형태소 비율  
  
-   85%의 데이터 위반을 검색 하는 데 몇 주가 걸렸습니다.  
  
-   92%의 인시던트는 타사에서 발견 되었습니다.  
  
-   갖추고 단순 또는 중간 컨트롤을 통해 위반의 97%가 발생 했습니다.  
  
앞에서 설명한 수준으로의 손상은 효과적으로 불가능, 손상 된 모든 시스템의 "평면화 및 다시 빌드"에 대 한 표준 권고는 Active Directory 손상 되거나 파괴 된 경우에만 가능 하거나 가능 하지 않습니다. 알려진 양호한 상태로 복원 하는 경우에도 첫 번째 환경에서 환경을 손상 시킬 수 있는 결함이 제거 되지 않습니다.  
  
인프라의 모든 패싯을 보호 해야 하지만 공격자는 원하는 목표를 달성 하기 위해 방어에서 충분 한 결함을 찾아야 합니다. 사용자 환경이 비교적 간단 하 고 간단 하 고 잘 관리 되는 경우이 문서의 앞부분에서 제공 하는 권장 사항을 구현 하는 것이 간단 합니다.  
  
그러나 이전 보다 크고 크고 복잡 한 환경을 발견 했으므로이 문서의 권장 사항을 구현할 수 없거나 구현할 수 없게 될 가능성이 높습니다. 새로 시작 하 고 공격 및 손상에 대 한 절충 환경을 생성 하는 것 보다는 인프라를 보호 하는 것이 훨씬 어렵습니다. 하지만 앞에서 설명한 것 처럼 전체 Active Directory 포리스트를 다시 작성 하는 데는 많지 않습니다. 이러한 이유로, Active Directory 포리스트를 안전 하 게 보호 하는 데 중점을 두는 방법을 사용 하는 것이 좋습니다.  
  
"손상 된" 모든 항목을 중점적으로 해결 하는 대신 비즈니스 및 인프라에서 가장 중요 한 사항에 따라 우선 순위를 지정 하는 방법을 고려 합니다. 오래 되 고 잘못 구성 된 시스템 및 응용 프로그램으로 채워진 환경을 수정 하는 대신 비즈니스에 가장 중요 한 사용자, 시스템 및 정보를 안전 하 게 이식할 수 있는 새로운 소규모 보안 환경을 만드는 것이 좋습니다.  
  
이 섹션에서는 핵심 비즈니스 인프라를 위한 "생명 보트" 또는 "보안 셀"로 제공 되는 기본적인 AD DS 포리스트를 만들 수 있는 방법을 설명 합니다. 초기 포리스트는 단순히 크기 및 범위가 제한 되는 새로 설치 된 Active Directory 포리스트 이며, 현재 운영 체제, 응용 프로그램 및 [Active Directory 공격 노출 영역 줄이기](../../../ad-ds/plan/security-best-practices/../../../ad-ds/plan/security-best-practices/Reducing-the-Active-Directory-Attack-Surface.md)에 설명 된 원칙을 사용 하 여 구축 됩니다.  
  
새로 빌드된 포리스트에 권장 구성 설정을 구현 하면 보안 설정 및 방법으로 처음부터 새로 작성 된 AD DS 설치를 만들 수 있으며, 기존 시스템 및 응용 프로그램을 지 원하는 문제를 줄일 수 있습니다. 초기 AD DS 설치의 디자인과 구현에 대 한 자세한 지침은이 문서에서 다루지 않지만, 가장 중요 한 자산을 포함할 수 있는 "보안 셀"을 만들려면 몇 가지 일반적인 원칙과 지침을 따라야 합니다. 이러한 지침은 다음과 같습니다.  
  
1.  중요 한 자산을 분리 및 보호 하기 위한 원칙을 식별 합니다.  
  
2.  제한 된 위험 기반 마이그레이션 계획을 정의 합니다.  
  
3.  필요에 따라 "nonmigratory" 마이그레이션을 활용 합니다.  
  
4.  "창작 소멸"을 구현 합니다.  
  
5.  레거시 시스템 및 응용 프로그램을 격리 합니다.  
  
6.  최종 사용자에 대 한 보안을 간소화 합니다.  
  
### <a name="identifying-principles-for-segregating-and-securing-critical-assets"></a>중요 한 자산을 분리 및 보호 하기 위한 원칙 식별  

중요 한 자산을 보관 하기 위해 만드는 초기 환경의 특성은 크게 다를 수 있습니다. 예를 들어, 사용자만 액세스할 수 있는 VIP 사용자 및 중요 데이터만 마이그레이션하는 초기 포리스트를 만들도록 선택할 수 있습니다. VIP 사용자만 마이그레이션하는 것이 아니라 관리 포리스트로 구현 하는 초기 포리스트를 만들 수 있습니다 .이를 통해 [Active Directory 공격 노출 영역을 줄여](../../../ad-ds/plan/security-best-practices/../../../ad-ds/plan/security-best-practices/Reducing-the-Active-Directory-Attack-Surface.md) 초기 포리스트에서 레거시 포리스트를 관리 하는 데 사용할 수 있는 보안 관리 계정 및 호스트를 만들 수 있습니다. 보안 수준이 낮은 포리스트를 분리 하는 것만 목표로 AD CS (Active Directory 인증서 서비스)를 실행 하는 서버와 같은 추가 보안이 필요한 시스템, 권한 있는 계정 및 시스템을 포함 하는 "용도에 맞게 작성 된" 포리스트를 구현할 수 있습니다. 마지막으로, 모든 새 사용자, 시스템, 응용 프로그램 및 데이터에 대 한 사실상 위치가 되는 초기 포리스트를 구현 하 여 더 많은 것을 통해 기존 포리스트를 서비스 해제할 수 있습니다.  
  
초기 포리스트에 소수의 사용자 및 시스템이 포함 되어 있는지 여부에 관계 없이 보다 적극적인 마이그레이션에 대 한 기초를 형성 하는지 여부에 관계 없이 계획에서 다음 원칙을 따라야 합니다.  
  
1.  레거시 포리스트가 손상 된 것으로 가정 합니다.  
  
2.  초기 포리스트를 신뢰 하도록 레거시 환경을 구성할 수 있지만 기존 포리스트를 신뢰 하는 초기 환경을 구성 하지 마십시오.  
  
3.  계정 그룹 멤버 자격, SID 기록 또는 기타 특성을 악의적으로 수정할 수 있는 경우 레거시 포리스트에서 사용자 계정 또는 그룹을 초기 환경으로 마이그레이션하지 마십시오. 대신 "nonmigratory" 방식을 사용 하 여 초기 포리스트를 채웁니다. Nonmigratory 방법은이 단원의 뒷부분에 설명 되어 있습니다.  
  
4.  레거시 포리스트에서 초기 포리스트로 컴퓨터를 마이그레이션하지 마십시오. 초기 포리스트에 새로 설치 된 서버를 구현 하 고, 새로 설치 된 서버에 응용 프로그램을 설치 하 고, 새로 설치 된 시스템으로 응용 프로그램 데이터를 마이그레이션합니다. 파일 서버에서 새로 설치 된 서버에 데이터를 복사 하 고, 새 포리스트의 사용자 및 그룹을 사용 하 여 Acl을 설정한 후 비슷한 방식으로 인쇄 서버를 만듭니다.  
  
5.  초기 포리스트에 레거시 운영 체제 또는 응용 프로그램을 설치 하는 것을 허용 하지 않습니다. 응용 프로그램을 업데이트 하 고 새로 설치할 수 없는 경우 레거시 포리스트에 그대로 두고 응용 프로그램의 기능을 대체 하는 creative 소멸을 고려 합니다.  
  
### <a name="defining-a-limited-risk-based-migration-plan"></a>제한 된 위험 기반 마이그레이션 계획 정의  
제한 된 위험 기반 마이그레이션 계획을 만드는 것은 사용자, 응용 프로그램 및 시스템 중 하나가 손상 된 경우 조직이 노출 되는 위험 수준에 따라 마이그레이션 대상을 식별 하는 것을 의미 합니다. 공격자가 목표로 할 가능성이 가장 높은 계정을 가진 VIP 사용자는 초기 포리스트에 있어야 합니다. 핵심 비즈니스 기능을 제공 하는 응용 프로그램은 초기 포리스트의 새로 빌드된 서버에 설치 해야 하며 매우 중요 한 데이터는 초기 포리스트의 보안 서버로 이동 해야 합니다.  
  
Active Directory 환경에서 업무상 중요 한 사용자, 시스템, 응용 프로그램 및 데이터를 명확 하 게 정리 하지 않은 경우 비즈니스 단위를 사용 하 여 해당 사용자를 식별 합니다. 중요 한 응용 프로그램이 실행 되는 서버 또는 중요 한 데이터가 저장 되는 것 처럼 비즈니스에 필요한 모든 응용 프로그램을 식별 해야 합니다. 조직에서 계속 작동 하는 데 필요한 사용자 및 리소스를 식별 하 여 노력에 집중할 수 있는 자연스럽 게 우선 순위가 지정 된 자산 컬렉션을 만듭니다.  
  
### <a name="leveraging-nonmigratory-migrations"></a>"Nonmigratory" 마이그레이션 활용  
환경이 손상 된 것으로 의심 되는 경우, 손상 된 것으로 의심 되는 경우, 기존 데이터 및 개체를 레거시 Active Directory 설치에서 새로운 항목으로 마이그레이션하지 않는 경우 기술적으로 "마이그레이션하지" 않는 마이그레이션 방법을 고려 하세요.  
  
### <a name="user-accounts"></a>사용자 계정  
한 포리스트에서 다른 포리스트로 마이그레이션하는 기존 Active Directory 마이그레이션하는 사용자 개체에 대 한 SIDHistory (SID 기록) 특성을 사용 하 여 사용자의 SID와 사용자가 레거시 포리스트에 속한 그룹의 Sid를 저장 합니다. 사용자 계정을 새 포리스트로 마이그레이션하고 기존 포리스트의 리소스에 액세스 하는 경우 SID 기록의 Sid를 사용 하 여 사용자가 계정을 마이그레이션하기 전에 액세스 한 리소스에 액세스할 수 있도록 하는 액세스 토큰을 만듭니다.  
  
그러나 SID 기록 유지 관리는 사용자의 액세스 토큰을 현재 및 과거 Sid로 채워 토큰이 너무 많은 환경에서 문제가 발생 한 것으로 입증 되었습니다. 토큰 팽창은 사용자의 액세스 토큰에 저장 해야 하는 Sid 수가 토큰에서 사용 가능한 공간 크기를 사용 하거나 초과 하는 문제입니다.  
  
토큰 크기를 제한 된 범위로 늘릴 수 있지만, 토큰 확장에 대 한 궁극적인 해결 방법은 사용자 계정에 연결 된 Sid의 수를 줄이는 것입니다 .이는 가져가지 그룹 멤버 자격, SID 기록 제거 또는 둘 다의 조합을 사용 하는 것입니다. 토큰에 대 한 자세한 내용은 [Maxtokensize 및 Kerberos 토큰 팽창](https://blogs.technet.com/b/shanecothran/archive/2010/07/16/maxtokensize-and-kerberos-token-bloat.aspx)을 참조 하세요.  
  
SID 기록을 사용 하 여 레거시 환경 (특히 그룹 구성원 자격 및 SID 기록이 손상 될 수 있음)에서 사용자를 마이그레이션하는 대신 SID 기록을 새 포리스트에 포함 하지 않고 "마이그레이션" 하는 메타 디렉터리 응용 프로그램을 활용 하는 것이 좋습니다. 사용자 계정이 새 포리스트에 생성 되 면 메타 디렉터리 응용 프로그램을 사용 하 여 계정을 레거시 포리스트의 해당 계정에 매핑할 수 있습니다.  
  
새 사용자 계정에 레거시 포리스트의 리소스에 대 한 액세스를 제공 하려면 메타 디렉터리 도구를 사용 하 여 사용자의 레거시 계정에 액세스 권한이 부여 된 리소스 그룹을 식별 한 다음 사용자의 새 계정을 해당 그룹에 추가 합니다. 레거시 포리스트의 그룹 전략에 따라 리소스 액세스를 위한 도메인 로컬 그룹을 만들거나 기존 그룹을 도메인 로컬 그룹으로 변환 해야 새 계정을 리소스 그룹에 추가할 수 있습니다. 가장 중요 한 응용 프로그램 및 데이터에 집중 하 고 SID 기록을 사용 하거나 사용 하지 않고 새 환경으로 마이그레이션하는 경우 레거시 환경에서 소요 된 작업량을 제한할 수 있습니다.  
  

  
### <a name="servers-and-workstations"></a>서버 및 워크스테이션  
한 Active Directory 포리스트에서 다른 포리스트로의 기존 마이그레이션에서는 컴퓨터를 마이그레이션하는 것은 사용자, 그룹 및 응용 프로그램을 마이그레이션하는 것과 비교 하 여 비교적 간단 합니다. 컴퓨터 역할에 따라 새 포리스트로 마이그레이션하는 것은 이전 도메인을 disjoining 하 고 새 도메인에 가입 하는 것 처럼 간단할 수 있습니다. 그러나 컴퓨터 계정을 초기 포리스트에 그대로 마이그레이션하는 것은 새 환경을 만드는 목적을 무효화 합니다. 새 포리스트에 대 한 컴퓨터 계정을 마이그레이션 (잠재적으로 손상, 잘못 구성 또는 오래 된) 하는 대신 새 환경에서 서버 및 워크스테이션을 새로 설치 해야 합니다. 레거시 포리스트의 시스템에서 초기 포리스트의 시스템으로 데이터를 마이그레이션할 수 있지만 데이터를 보관 하는 시스템은 마이그레이션할 수 없습니다.  
  
### <a name="applications"></a>응용 프로그램  

응용 프로그램은 한 포리스트에서 다른 포리스트로 마이그레이션하는 데 가장 중요 한 문제를 제공할 수 있지만, "nonmigratory" 마이그레이션의 경우에는 초기 포리스트의 응용 프로그램이 최신, 지원 및 새로 설치 되어야 합니다. 가능 하면 이전 포리스트의 응용 프로그램 인스턴스에서 데이터를 마이그레이션할 수 있습니다. 초기 포리스트에서 응용 프로그램을 "다시 만들 수 없는" 경우에는 다음 섹션에 설명 된 대로 레거시 응용 프로그램의 창의적인 소멸 또는 격리와 같은 접근 방식을 고려해 야 합니다.  
  
### <a name="implementing-creative-destruction"></a>Creative 소멸 구현  
Creative 소멸은 이전 주문을 파괴 하 여 만든 경제 개발을 설명 하는 경제적 용어입니다. 최근 몇 년 동안에는 정보가 정보 기술에 적용 되었습니다. 일반적으로 기존 인프라를 업그레이드 하는 것이 아니라 기존 인프라를 완전히 새로운 방식으로 대체 하는 메커니즘을 나타냅니다. [Gartner Symposium ITXPO](http://www.gartner.com/technology/symposium/orlando/) 2011는 cio와 선임 IT 임원에 게 비용 절감 및 효율성 향상을 위해 주요 테마 중 하나로 창조적 소멸을 제시 했습니다. 보안 향상은 프로세스를 자연스럽 게 증가 시킬 수 있습니다.  

예를 들어 조직은 다양 한 modernity 및 공급 업체 지원과 함께 비슷한 기능을 수행 하는 다양 한 응용 프로그램을 사용 하는 여러 비즈니스 단위로 구성 될 수 있습니다. 지금까지 각 비즈니스 단위의 응용 프로그램을 개별적으로 유지 관리 해야 할 수 있으며, 통합 작업은 가장 적합 한 기능을 제공 하는 응용 프로그램을 파악 하 고 다른 응용 프로그램으로 데이터를 마이그레이션하는 작업으로 구성 됩니다.  
  
오래 된 응용 프로그램 또는 중복 응용 프로그램을 유지 관리 하는 대신 창의적인 소멸에서 완전히 새로운 응용 프로그램을 구현 하 여 이전 버전을 대체 하 고 데이터를 새 응용 프로그램으로 마이그레이션하고 이전 응용 프로그램과 해당 응용 프로그램이 실행 되는 시스템을 서비스 해제 합니다. 경우에 따라 사용자 고유의 인프라에 새 응용 프로그램을 배포 하 여 레거시 응용 프로그램의 창의적인 소멸을 구현할 수 있습니다. 하지만 가능 하면 응용 프로그램을 클라우드 기반 솔루션으로 포팅 하는 것을 고려해 야 합니다.  
  
기존 사내 응용 프로그램을 대체 하기 위해 클라우드 기반 응용 프로그램을 배포 하면 유지 관리 노력과 비용을 줄일 수 있을 뿐 아니라, 공격자가 활용할 수 있는 취약성을 제시 하는 레거시 시스템 및 응용 프로그램을 제거 하 여 조직의 공격 노출 영역을 줄일 수 있습니다. 이 방법은 인프라에서 기존 대상을 동시에 제거 하는 동시에 조직이 원하는 기능을 얻을 수 있는 더 빠른 방법을 제공 합니다. Creative 소멸의 원칙은 모든 IT 자산에 적용 되지 않지만 강력 하 고 안전한 클라우드 기반 응용 프로그램을 동시에 배포 하는 동안 레거시 시스템 및 응용 프로그램을 제거 하는 것이 자주 사용 되는 옵션을 제공 합니다.  
  
### <a name="isolating-legacy-systems-and-applications"></a>레거시 시스템 및 응용 프로그램 격리  
비즈니스에 중요 한 사용자 및 시스템을 초기, 보안 환경으로 마이그레이션하는 것의 자연스럽 게 성장 하는 것은 레거시 포리스트에 더 중요 한 정보 및 시스템이 포함 될 수 있다는 것입니다. 보안 수준이 낮은 환경에서 유지 되는 레거시 시스템 및 응용 프로그램은 손상 위험을 초래할 수 있지만 손상의 심각도도 줄어듭니다. Rehoming 및 현대화는 중요 한 비즈니스 자산을 활용 하 여 기존 설정 및 프로토콜을 수용할 필요 없이 효과적인 관리 및 모니터링을 배포 하는 데 집중할 수 있습니다.  
  
중요 한 데이터를 초기 포리스트로 이동할 때 "main" AD DS 포리스트에서 레거시 시스템 및 응용 프로그램을 추가로 격리 하는 옵션을 평가할 수 있습니다. 독창적인 소멸을 구현 하 여 응용 프로그램 및 해당 응용 프로그램이 실행 되는 서버를 바꿀 수 있지만, 보안 수준이 낮은 시스템과 응용 프로그램의 추가 격리를 고려할 수도 있습니다. 예를 들어, 소수의 사용자가 사용 하지만 LAN 관리자 해시와 같은 레거시 자격 증명을 요구 하는 응용 프로그램은 대체 옵션이 없는 시스템을 지원 하기 위해 만드는 작은 도메인으로 마이그레이션될 수 있습니다.  
  
레거시 설정을 강제로 구현 하는 도메인에서 이러한 시스템을 제거 하면 현재 운영 체제 및 응용 프로그램을 지원 하도록 구성 하 여 도메인의 보안을 강화할 수 있습니다. 하지만 가능 하면 레거시 시스템 및 응용 프로그램을 서비스 해제 하는 것이 좋습니다. 서비스 해제가 레거시 모집단의 작은 세그먼트에만 적합 한 것은 아닙니다 .이를 별도의 도메인 (또는 포리스트)으로 분리 하면 레거시 설치의 나머지 부분에서 증분 기능 향상을 수행할 수 있습니다.  
  
### <a name="simplifying-security-for-end-users"></a>최종 사용자를 위한 보안 간소화  
대부분의 조직에서 조직의 역할 특성으로 인해 가장 중요 한 정보에 액세스 하는 사용자는 종종 복잡 한 액세스 제한 및 제어를 익히는 데 가장 적은 시간이 소요 됩니다. 조직의 모든 사용자에 게 포괄적인 보안 교육 프로그램이 있어야 하지만 투명 하 고 사용자가 준수 하는 원칙을 단순화 하는 컨트롤을 구현 하 여 가능한 한 간단 하 게 보안을 설정 하는 데 집중 해야 합니다.  
  
예를 들어, 보안 워크스테이션을 사용 하 여 중요 한 데이터 및 시스템에 액세스 하는 데 사용 하는 임원 및 기타 Vip가 중요 한 데이터에 액세스 하는 데 다른 장치를 사용할 수 있도록 하는 정책을 정의할 수 있습니다. 이는 사용자가 기억할 수 있는 간단한 원칙 이지만 방법을 적용 하는 데 도움이 되는 여러 백 엔드 컨트롤을 구현할 수 있습니다.  

[인증 메커니즘 보증](https://technet.microsoft.com/library/dd391847(v=WS.10).aspx) 을 사용 하면 사용자가 스마트 카드를 사용 하 여 보안 시스템에 로그온 한 경우에만 중요 한 데이터에 액세스할 수 있으며, IPsec 및 사용자 권한 제한을 사용 하 여 중요 한 데이터 리포지토리에 연결할 수 있는 시스템을 제어할 수 있습니다. [Microsoft 데이터 분류 도구 키트](https://www.microsoft.com/download/details.aspx?id=27123) 를 사용 하 여 강력한 파일 분류 인프라를 구축할 수 있으며, [동적 Access Control](https://blogs.technet.com/b/windowsserver/archive/2012/05/22/introduction-to-windows-server-2012-dynamic-access-control.aspx) 구현 하 여 액세스 시도의 특징에 따라 데이터에 대 한 액세스를 제한 하 고 비즈니스 규칙을 기술 컨트롤로 변환할 수 있습니다.  
  
사용자의 관점에서, 보안 시스템에서 중요 한 데이터에 액세스 하는 것은 "작동" 하 고 보안 되지 않은 시스템에서이 작업을 수행 하려고 시도 하는 것입니다. " 그러나 환경 모니터링 및 관리 측면에서 볼 때 사용자가 중요 한 데이터 및 시스템에 액세스 하는 방법에 식별할 수 있는 패턴을 만들어 비정상적인 액세스 시도를 더 쉽게 검색할 수 있습니다.  
  
사용자가 오랫동안 저항 하는 환경에서 복잡 한 암호를 사용 하는 경우 암호 정책 부족, 특히 VIP 사용자의 경우에는 스마트 카드를 통해 (인증을 강화 하기 위한 추가 기능을 사용 하 여 다양 한 폼 팩터를 사용 하 여) 또는 사용자 컴퓨터의 TPM (신뢰할 수 있는 플랫폼 모듈) 칩에 의해 보호 되는 인증 데이터를 비롯 하 여 인증에 대 한 대체 접근 방식을 고려 합니다. Multi-factor authentication은 컴퓨터가 이미 손상 된 경우 자격 증명 도난 공격을 방지 하지 않지만 사용자에 게 사용 하기 쉬운 인증 컨트롤을 제공 하 여 기존 사용자 이름 및 암호 컨트롤을 사용 하기 어려운 사용자 계정에 보다 강력한 암호를 할당할 수 있습니다.  
