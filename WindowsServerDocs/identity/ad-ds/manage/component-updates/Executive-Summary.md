---
ms.assetid: 85ca191c-0cc7-4453-a72c-42060ddf2ea2
title: "요약"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: c218a4d66e8208cf627bc93be50bf11ea2fbf862
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2017
---
# <a name="executive-summary"></a>요약

>적용 대상: Windows Server 2012

>[!IMPORTANT] 
>이 문서 2013에서 작성 하 고 기록 용도로 제공 됩니다.  현재이 설명서를 검토 하는 것 및는 변경 될 수 있습니다.  현재 모범 사례를 반영 하지 않을 수 있습니다.

정보 it 인프라와 없음 조직 공격에 영향을 받지 이지만 적절 한 정책을, 프로세스 및 컨트롤은 구현 핵심 부분의 조직 컴퓨팅 인프라를 보호 하기 위해 경우 위반 이벤트 컴퓨팅 환경 소매 손상으로 성장 하 않도록 하려면 것일 수 있습니다.  
  
이 요약 조직 Active Directory 설치 보안이 향상에 도움이 되는 추천을 포함 문서의 콘텐츠 요약 독립 실행형 문서로 유용 하 게 것입니다. 이러한 권장을 구현 하 여 조직의 파악 하 고 보안 활동 우선 순위를 정하는, 주요 조직의 컴퓨팅 인프라 부분의 보호 크게 중요 한 구성 요소는 IT 환경에 대 한 성공 공격의 가능성을 줄이기 컨트롤을 만들 수 됩니다.  
  
이 문서에서는 Active Directory 및 대책을 하든지에 대 한 가장 일반적인 공격, 있지만 완료 손상이 발생할 경우 복구를 위한 권장 포함 됩니다. 전체 Active Directory에 발생 한 경우 복구만 있는지 방법은 발생 하기 전에 손상에 대 한 준비가 것입니다.  
  
이 문서의 주요 부분은 다음과 같습니다.  
  
-   손상 수단  
  
-   Active Directory 공격 줄이기  
  
-   침입 Active Directory를 모니터링합니다.  
  
-   손상에 대 한 계획  
  
## <a name="avenues-to-compromise"></a>손상 수단  
이 섹션 일부 고객의 인프라 손상 공격자에서 사용 하는 가장 일반적으로 사용된 취약성에 대 한 정보를 제공 합니다. 문제와 처음 고객의 인프라를 관통, 추가 시스템 손상 전파 및 결국 Active Directory 및 도메인 컨트롤러의 조직의 숲을 완전히 제어할 얻을 수를 조정할를 사용 하는 방법의 일반적인 범주 포함 됩니다. 각 유형의의 없는 취약성 직접 Active Directory를 대상으로 사용 되지 않는 문제를 해결 하기 위해에 대 한 자세한 내용은 제공 되지 않습니다. 그러나 각 형식의 취약성에 대 한 대책 개발 하 고 공격 조직의 줄이기를 사용 하 여 자세한 정보 링크를 제공 했습니다.  
  
포함 된 다음 주제는 다음과 같습니다.  
  
-   **초기 위반 대상** -대부분 정보 보안 위반 소량의 조직의 infrastructure 자주 하나 또는 두 개의 시스템의 손상 된 한 번에 시작 됩니다. 이러한 초기 이벤트 또는 네트워크로 진입점 취약점을 아니었습니다 되지만 수리 되었을 수를 이용 종종 있습니다. 일반적으로 나타나는 문제는 다음과 같습니다.  
  
    -   바이러스 백신 및 맬웨어 방지 배포 차이  
  
    -   불완전 패치  
  
    -   오래 응용 프로그램 및 운영 체제  
  
    -   잘못 구성  
  
    -   보안 응용 프로그램 개발 방법 부족  
  
-   **매력적인 계정 자격 증명 도용의** -공격자 처음 네트워크에서 컴퓨터에 액세스 권한을된 갖게을 무료로 사용할 수 있는 도구를 사용 하 여 로그인 한 다른 계정과 세션에서 자격 증명을 추출 자격 증명 도용의 공격 들입니다.   
    이 섹션에 포함 되는 다음과 같습니다.  
  
    -   **손상 될 가능성이 증가 하는 활동** -자격 증명 도용의 대상 권한이 높은 도메인 계정 및 "매우 중요 한 사람이"는 일반적으로 (VIP) 계정 것이 중요 관리자 자격 증명 도용의 공격 성공 가능성 증가 하는 활동을 인식 될 수 있습니다. 이러한 작업은 다음과 같습니다.  
  
        -   권한이 계정 사용 하는 비보안된 컴퓨터에 로그인  
  
        -   매우 권한 계정 사용 하 여 인터넷을 검색  
  
        -   시스템 전반에서 로컬 권한이 있는 계정 같은 자격 증명으로 구성  
  
        -   Overpopulation 및 도메인 권한이 있는 그룹 많이  
  
        -   도메인 컨트롤러의 보안 부족 관리 합니다.  
  
    -   **상승할 및 전파 권한** -특정 계정, 서버 및 인프라 구성 요소에 대 한 Active Directory 공격의 기본 대상은 일반적으로 합니다. 이러한 계정을 다음과 같습니다.  
  
        -   영구적으로 권한이 있는 계정  
  
        -   VIP 계정  
  
        -   "권한 연결" Active Directory 계정  
  
        -   도메인 컨트롤러  
  
        -   신원을, 액세스 및 구성 관리 공개 키 인프라 (PKI) 서버, 관리 서버 시스템 등에 영향을 주는 다른 infrastructure 서비스  
  
## <a name="reducing-the-active-directory-attack-surface"></a>Active Directory 공격 줄이기  
이 섹션의 Active Directory 설치 하든지을 기술 컨트롤 중점적 합니다. 이 섹션에 포함 된 다음 주제는 다음과 같습니다.  
  
-   **권한이 있는 계정 및 Active Directory에 그룹** 최고 권한이 있는 계정 및 그룹 Active Directory와 권한이 있는 계정 보호 메커니즘 섹션에 설명 합니다. 내 Active Directory 세 가지 기본 제공 그룹은 다양 한 추가 그룹과 계정 보호도 해야 하지만 (엔터프라이즈 관리, 도메인 관리자 및 관리자) 디렉터리에 최고 권한 그룹입니다.  
  
-   **구현 최소 권한 관리 모델** 섹션의 사용 권한 매우 위험 식별 중점적 계정 일상적인 관리 선물에 대 한 뿐만 아니라 위험 줄이기 위해 추천을 제공 하는 것입니다.  
  
권한 과도 하 게 손상 된 환경에서 Active Directory에 발견 되지 않습니다. 조직에서 꼭 필요한 것 보다 더 많은 권한을 부여를 개발 하는 경우 일반적으로 인프라 전체의 있습니다.  
  
-   Active Directory에  
  
-   구성원 서버의  
  
-   워크스테이션  
  
-   응용 프로그램에서  
  
-   데이터 저장소  
  
-   **안전 하 게 관리 호스트 구현** Active Directory와 연결 된 시스템의 관리를 지원 하도록 구성 된 컴퓨터 안전 하 게 관리 호스트에 설명 합니다. 이러한 호스트는 관리 기능을 최선을 다하고 있으며 메일 응용 프로그램, 웹 브라우저 생산성 소프트웨어 (예: Microsoft Office) 등 소프트웨어를 실행 하지 않습니다.  
  
이 섹션에 포함 되는 다음과 같습니다.  
  
-   **보안을 유지 관리 호스트 만들기 위한 원칙** -일반 원칙 점을 명심에서 해야 하는 다음과 같습니다.  
  
    -   신뢰할 수 없는 호스트에서 신뢰할 수 있는 시스템을 관리할 하지 않습니다.  
  
    -   권한 있는 활동을 수행 하는 경우 단일 인증 비율에 의존 하지 않습니다.  
  
    -   디자인 및 관리 호스트 안전한 구현 하는 경우에 물리적 보안 반드시.  
  
-   **도메인 컨트롤러 공격 으로부터 보호할** -악의적인 사용자 도메인 컨트롤러에 대 한 액세스 권한이 가진된 획득 하면, 해당 사용자 수를 수정, 손상, 있으며 Active Directory 데이터베이스를 삭제 하 고 시스템 및 계정 관리 Active Directory 하는 모든 확장 하 여 합니다.  
  
이 섹션에 포함 된 다음 주제는 다음과 같습니다.  
  
-   **도메인 컨트롤러에 대 한 보안 물리적** -물리적 보안 센터, 지사에서 및 멀리 떨어진 장소의 도메인 컨트롤러를 제공 하는 권장 포함 되어 있습니다.  
  
-   **도메인 컨트롤러 운영 체제** -보안 도메인 컨트롤러 운영 체제에 대 한 추천을 포함 합니다.  
  
-   **보안 도메인 컨트롤러의 구성** -네이티브 및 무료로 사용할 수 있는 구성 도구 및 설정 보안 구성 기준 그룹 정책 개체 (Gpo) 이후 적용 될 수 있는 도메인 컨트롤러에 대 한 만드는 사용할 수 있습니다.  
  
## <a name="monitoring-active-directory-for-signs-of-compromise"></a>침입 Active Directory를 모니터링합니다.  
이 섹션 레거시 감사 범주 및 감사 정책 하위 범주 (도입 된 Windows Vista 및 Windows Server 2008), 고급 감사 정책 (Windows Server 2008 R2에 도입)에 대 한 정보를 제공 합니다. 제공 이벤트에 대 한 정보 이며 개체를 모니터링 하는 환경 및 포괄적인 감사 정책에 대 한 Active Directory 만드는 데 사용할 수 있는 몇 가지 추가 참조 손상 하려고를 나타낼 수 있습니다.  
  
이 섹션에 포함 된 다음 주제는 다음과 같습니다.  
  
-   **Windows 감사 정책** -Windows 보안 이벤트 로그 있는 범주 및 하위 범주 보안 이벤트를 결정 하는 추적 하 여 녹화 합니다.  
  
-   **추천 정책을 감사할** -감사 권장 감사 워크스테이션 및 중요 한 서버를 사용 하 여 Microsoft, 미국 하 고 조직에 대해 보다 적극적인 추천을 제공 하는 정책 설정, Windows 기본 감사 정책 설정에 설명 합니다.  
  
## <a name="planning-for-compromise"></a>손상에 대 한 계획  
이 섹션 조직 발생 하기 전에 손상에 대 한 준비 하는 데 도움이 되는 추천, 공격자가 디렉터리의 전체 손상을 높일 수 있는 경우에 대 한 응답 및 복구 지침이 제공 하 고 전체 위반, 발생 하기 전에 손상 이벤트를 검색할 수 있는 구현 컨트롤이 포함 되어 있습니다. 이 섹션에 포함 된 다음 주제는 다음과 같습니다.  
  
-   **방법을 보아야** -원칙 및 지침 조직에는 자녀가 가장 중요 한 자산 배치할 수 보안 환경을 만드는 데 포함 되어 있습니다. 이러한 지침은 다음과 같습니다.  
  
    -   신원 파악이 가능한 원칙 분리 및 중요 한 자산 보호  
  
    -   제한 된 위험 기반 마이그레이션을 계획을 정의  
  
    -   필요한 경우 "nonmigratory" 마이그레이션을 활용  
  
    -   "창의적인 소멸" 구현  
  
    -   기존 시스템 및 응용 프로그램을 차단  
  
    -   최종 사용자에 대 한 보안을 간소화  
  
-   **더 많은 보안 환경을 유지** -효과적인 보안 뿐 아니라 효과적인 수명 주기 관리 개발 하는 데 사용 하는 지침이 사용 고급 권장 사항을 포함 합니다. 이 섹션에 포함 된 다음 주제는 다음과 같습니다.  
  
    -   **비즈니스 중심 보안 관행에 대 한 Active Directory 만들기** -효과적으로 관리 하는 사용자, 데이터, 응용 프로그램 및 Active Directory 관리 하는 시스템의 수명 주기이 원칙을 따릅니다.  
  
        -   **비즈니스 소유권 Active Directory 데이터에 할당** -인프라 구성 요소를의 소유권을 지정 IT; 데이터에 대 한 Active Directory Domain Services (AD DS) 예를 들어, 비즈니스를 지원 하기 위해 새로운 직원 새로운 응용 프로그램 및 지정된 비즈니스 단위 새 정보 저장소에 추가 되는 하거나 사용자의 데이터에 연결 해야 합니다.  
  
        -   **수명 주기 관리 Business-Driven 구현** -Active Directory에 데이터에 대 한 수명 주기 관리 구현 해야 합니다.  
  
        -   **모든 Active Directory 데이터 분류** -비즈니스 소유자 분류 Active Directory에 데이터를 제공 해야 합니다. 내 데이터 분류 모델 다음 Active Directory 데이터에 대 한 분류 포함 해야 합니다.  
  
            -   **시스템** -분류 채우기 서버 운영 체제의 역할을 및 IT에서 실행 되는 응용 프로그램 및 비즈니스 소유자 기록 합니다.  
  
            -   **응용 프로그램** -기능과 사용자 기반 운영 체제 하 여 응용 프로그램을 분류 됩니다.  
  
            -   **사용자가** -태그가 지정 하 고 모니터링 공격자가 대상으로 지정 될 가능성이 Active Directory 설치에서 계정 해야 합니다.  
  
## <a name="summary-of-best-practices-for-securing-active-directory-domain-services"></a>모범 사례에 대 한 Active Directory Domain Services 보안 요약  
다음 표에서 요약 AD DS 설치를 보호 하기 위한이 문서에 제공 되는 추천을 제공 합니다. 몇 가지 유용한 자연에서 전략적 하 고 포괄적인 계획 및 구현 프로젝트; 요구 들이 전략적 및 Active Directory와 관련 된 인프라 특정 구성에 집중 합니다.  
  
관행 높은 우선 순위를 해당 군도 순서로 나열 된, 낮은 숫자 높은 우선 순위를 표시 합니다. 여기서 적용할 수 있는, 가장 좋은 방법은 예방 또는 탐정 기본적에서으로 구분 됩니다. 이러한 모든 권장 철저 하 게 테스트 하 고 해야 조직의 특징과 요구 사항에 대 한 필요에 따라 수정 합니다.  
  
  
|-|-|-|-|  
||**최상의**|**전략적 또는 전략적**|**예방 하거나 탐정**|  
| 1 | 응용 프로그램 패치. | 기술적인 | 예방 |  
| 2 | 운영 체제 패치. | 기술적인 | 예방 |  
| 3 | 배포 및 즉시 바이러스 백신 및 맬웨어 방지 소프트웨어의 모든 시스템와을 제거 하거나 비활성화 모니터 시도 대 한 업데이트입니다. | 기술적인 | 모두 |  
| 4 | 수정 시도 대 한 중요 한 Active Directory 개체와 시도한 손상 나타내는 이벤트에 대 한 Windows 모니터링. | 기술적인 | 탐정 |  
| 5 | 보호 하 고 모니터링 사용자에 게 중요 한 데이터에 액세스할 수 있는 계정 | 기술적인 | 모두 |  
| 6 | 강력한 계정을 무단으로 시스템에서 사용 되지 않도록 방지. | 기술적인 | 예방 |  
| 7 | 매우 권한이 있는 그룹의 영구 구성원 제거. | 기술적인 | 예방 |  
| 8 | 필요할 때 권한이 있는 그룹의 회원 임시 부여할 컨트롤을 구현. | 기술적인 | 예방 |  
| 9 | 안전 하 게 관리 호스트 구현. | 기술적인 | 예방 |  
| 10 | 응용 프로그램 whitelisting 도메인 컨트롤러, 관리 호스트 및 기타 중요 한 시스템에서 사용 하 여. | 기술적인 | 예방 |  
| 11 | 중요 한 자산을 식별 하 고 보안 우선 순위를 지정 및 모니터링. | 기술적인 | 모두 |  
| 12 | 디렉터리의 지원 인프라 및 시스템 도메인에 가입한 관리 하기 위한 최소 권한 역할 기반 액세스 제어 구현. | 전략적 | 예방 |  
| 13 | 기존 시스템 및 응용 프로그램을 분리 합니다. | 기술적인 | 예방 |  
| 14 | 기존 시스템 및 응용 프로그램을 제거 합니다. | 전략적 | 예방 |  
| 15 | 구현 개발 사용자 지정 응용 프로그램에 대 한 수명 주기 프로그램 보안. | 전략적 | 예방 |  
| 16 | 구성 관리 구현 준수 정기적으로 검토 하 고 각 새 하드웨어 또는 소프트웨어 버전을 사용 하 여 설정을 평가. | 전략적 | 예방 |  
| 17 | 중요 한 자산 그대로 숲 엄격한 보안 및 요구 사항은 모니터링 마이그레이션을. | 전략적 | 모두 |  
| 18 | 최종 사용자에 대 한 보안을 간소화. | 전략적 | 예방 |  
| 19 | 사용 된 제어 기능과 보안 통신을 방화벽 호스트 기반. | 기술적인 | 예방 |  
| 20 | 장치 패치. | 기술적인 | 예방 |  
| 21 | IT 자산 업무와 관련 수명 주기 관리 구현. | 전략적 | 해당 없음 |  
| 22 | 만들기 또는 인시던트 복구 계획 업데이트 있습니다. | 전략적 | 해당 없음 |  
  

