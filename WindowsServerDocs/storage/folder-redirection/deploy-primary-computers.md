---
title: 폴더 리디렉션 및 로밍 사용자 프로필용 기본 컴퓨터 배포
description: 기본 컴퓨터 지원을 사용하도록 설정하고 폴더 리디렉션 및 로밍 사용자 프로필을 사용하는 사용자의 기본 컴퓨터를 지정하는 방법을 설명합니다.
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 06/06/2019
ms.localizationpriority: medium
ms.openlocfilehash: be2b41cf32e2020422c32415e2d8f4273eb09859
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2020
ms.locfileid: "71394444"
---
# <a name="deploy-primary-computers-for-folder-redirection-and-roaming-user-profiles"></a>폴더 리디렉션 및 로밍 사용자 프로필용 기본 컴퓨터 배포

>적용 대상: Windows 10, Windows 8, Windows 8.1, Windows Server 2019, Windows Server 2016, Windows Server 2012, Windows Server 2012 R2

이 토픽에서는 기본 컴퓨터 지원을 사용하도록 설정하고 사용자의 기본 컴퓨터를 지정하는 방법을 설명합니다. 이렇게 하면 폴더 리디렉션 및 로밍 사용자 프로필을 사용하는 컴퓨터를 제어할 수 있습니다.

> [!IMPORTANT]
> 로밍 사용자 프로필에 기본 컴퓨터 지원을 사용하도록 설정할 때 항상 폴더 리디렉션에도 기본 컴퓨터 지원을 사용하도록 설정해야 합니다. 이렇게 하면 문서와 기타 사용자 파일이 사용자 프로필과 따로 보관되며, 이를 통해 프로필 크기를 작게, 로그인 시간을 빠르게 유지할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

## <a name="software-requirements"></a>소프트웨어 요구 사항

기본 컴퓨터 지원의 요구 사항은 다음과 같습니다.

- Windows Server 2012 스키마 추가 기능이 포함되도록 AD DS(Active Directory Domain Services) 스키마를 업데이트해야 합니다(Windows Server 2012 도메인 컨트롤러를 설치하면 스키마가 자동으로 업데이트됨). AD DS 스키마 업데이트에 대한 자세한 내용은 [Adprep.exe 통합](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh472161(v=ws.11)#adprepexe-integration>) 및 [Adprep.exe 실행](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd464018(v=ws.10)>)을 참조하세요.
- 클라이언트 컴퓨터는 Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 또는 Windows Server 2012를 실행해야 합니다.

> [!TIP]
> 기본 컴퓨터 지원에는 폴더 리디렉션 및/또는 로밍 사용자 프로필이 필요하지만, 이러한 기술을 처음으로 배포하는 경우에는 기본 컴퓨터 지원을 설정한 후 폴더 리디렉션 및 로밍 사용자 프로필을 구성하는 GPO를 사용하도록 설정하는 것이 가장 좋습니다. 그러면 기본 컴퓨터 지원을 사용하기 전에 사용자 데이터가 기본이 아닌 컴퓨터에 복사되는 것이 방지됩니다. 구성 정보는 [폴더 리디렉션 배포](deploy-folder-redirection.md) 및 [로밍 사용자 프로필 배포](deploy-roaming-user-profiles.md)을 참조하세요.

## <a name="step-1-designate-primary-computers-for-users"></a>1단계: 사용자의 기본 컴퓨터 지정

기본 컴퓨터 지원을 배포하는 첫 번째 단계는 각 사용자의 기본 컴퓨터를 지정하는 것입니다. 이렇게 하려면 Active Directory 관리 센터를 사용하여 관련 컴퓨터의 고유 이름을 가져온 다음, **msDs-PrimaryComputer** 특성을 설정합니다.

> [!TIP]
> Windows PowerShell을 사용하여 기본 컴퓨터를 작업하려면 블로그 게시물 [Digging a little deeper into Windows 8 Primary Computer(Windows 8 기본 컴퓨터에 대해 자세히 알아보기)](<https://blogs.technet.microsoft.com/askds/2012/10/23/digging-a-little-deeper-into-windows-8-primary-computer/>)를 참조하세요.

사용자의 기본 컴퓨터를 지정하는 방법은 다음과 같습니다.

1. Active Directory 관리 도구가 설치된 컴퓨터에서 서버 관리자를 엽니다.
2. **도구** 메뉴에서 **Active Directory 관리 센터**를 선택합니다. Active Directory 관리 센터가 표시됩니다.
3. 해당 도메인의 **컴퓨터** 컨테이너로 이동합니다.
4. 기본 컴퓨터로 지정할 컴퓨터를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 선택합니다.
5. 탐색 창에서 **확장**을 선택합니다.
6. **특성 편집기** 탭을 선택하고, **distinguishedName**으로 스크롤하고, **보기**를 선택하고, 나열된 값을 마우스 오른쪽 단추로 클릭하고, **복사**를 선택하고, **확인**을 선택한 다음, **취소**를 선택합니다.
7. 해당 도메인의 **사용자** 컨테이너로 이동하여 컴퓨터를 할당할 사용자를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 선택합니다.
8. 탐색 창에서 **확장**을 선택합니다.
9. **특성 편집기** 탭을 선택하고 **msDs-PrimaryComputer**를 선택한 다음, **편집**을 선택합니다. 다중값 문자열 편집기 대화 상자가 나타납니다.
10. 텍스트 상자를 마우스 오른쪽 단추로 클릭하고, **붙여넣기** **추가** 를 선택하고, **확인** 을 선택한 다음, **확인**을 다시 선택합니다.

## <a name="step-2-optionally-enable-primary-computers-for-folder-redirection-in-group-policy"></a>2단계: 필요한 경우 [그룹 정책]에서 폴더 리디렉션에 기본 컴퓨터를 사용하도록 설정

다음 단계는 필요에 따라 폴더 리디렉션에 기본 컴퓨터 지원을 사용하도록 그룹 정책을 구성하는 것입니다. 이렇게 하면 사용자의 폴더를 사용자의 기본 컴퓨터로 지정된 컴퓨터에서 리디렉션할 수 있지만, 다른 컴퓨터에서는 리디렉션할 수 없습니다. 컴퓨터 단위로 또는 사용자별로 폴더 리디렉션의 기본 컴퓨터를 제어할 수 있습니다.

폴더 리디렉션에 기본 컴퓨터를 사용하도록 설정하는 방법은 다음과 같습니다.

1. [그룹 정책 관리]에서, 폴더 리디렉션 및/또는 로밍 사용자 프로필을 처음 구성할 때 만든 GPO(예: **폴더 리디렉션 설정** 또는 **로밍 사용자 프로필 설정**)를 마우스 오른쪽 단추로 클릭한 다음, **편집**을 선택합니다.
2. 컴퓨터 기반 그룹 정책을 사용하여 기본 컴퓨터 지원을 설정하려면 **컴퓨터 구성**으로 이동합니다. 사용자 기반 그룹 정책의 경우 **사용자 구성**으로 이동합니다.
    - 컴퓨터 기반 그룹 정책은 GPO가 적용되는 모든 컴퓨터에 기본 컴퓨터 처리를 적용하므로 컴퓨터의 모든 사용자에게 영향을 줍니다.
    - 사용자 기반 그룹 정책은 GPO가 적용되는 모든 사용자 계정에 기본 컴퓨터 처리를 적용하므로 사용자가 로그인하는 모든 컴퓨터에 영향을 줍니다.
3. **컴퓨터 구성** 또는 **사용자 구성**에서 **정책**, **관리 템플릿**, **시스템**, **폴더 리디렉션**으로 이동합니다.
4. **기본 컴퓨터에서만 폴더 리디렉션**을 마우스 오른쪽 단추로 클릭한 다음, **편집**을 선택합니다.
5. **사용**을 선택한 다음, **확인**을 선택합니다.

## <a name="step-3-optionally-enable-primary-computers-for-roaming-user-profiles-in-group-policy"></a>3단계: 필요한 경우 [그룹 정책]에서 로밍 사용자 프로필에 기본 컴퓨터를 사용하도록 설정

다음 단계는 필요에 따라 로밍 사용자 프로필에 기본 컴퓨터 지원을 사용하도록 그룹 정책을 구성하는 것입니다. 이렇게 하면 사용자의 프로필을 사용자의 기본 컴퓨터로 지정된 컴퓨터에서 로밍할 수 있지만, 다른 컴퓨터에서는 로밍할 수 없습니다.

로밍 사용자 프로필에 기본 컴퓨터를 사용하도록 설정하는 방법은 다음과 같습니다.

1. 아직 설정하지 않았다면 폴더 리디렉션에 기본 컴퓨터 지원을 사용하도록 설정합니다.<br>이렇게 하면 문서와 기타 사용자 파일이 사용자 프로필과 따로 보관되며, 이를 통해 프로필 크기를 작게, 로그인 시간을 빠르게 유지할 수 있습니다.
2. [그룹 정책 관리]에서, 이전에 만든 GPO(예: **폴더 리디렉션 및 로밍 사용자 프로필 설정**)를 마우스 오른쪽 단추로 클릭한 다음, **편집**을 선택합니다.
3. **컴퓨터 구성**, **정책**, **관리 템플릿**, **시스템**, **사용자 프로필**로 이동합니다.
4. **기본 컴퓨터에만 로밍 프로필 다운로드**를 마우스 오른쪽 단추로 클릭한 다음, **편집**을 선택합니다.
5. **사용**을 선택한 다음, **확인**을 선택합니다.

## <a name="step-4-enable-the-gpo"></a>4단계: GPO를 사용하도록 설정

폴더 리디렉션 및 로밍 사용자 프로필 구성을 마쳤으면 GPO를 사용하도록 설정합니다(아직 설정하지 않은 경우). 이렇게 하면 영향을 받는 사용자 및 컴퓨터에 GPO를 적용할 수 있습니다.

폴더 리디렉션 및/또는 로밍 사용자 프로필 GPO를 사용하도록 설정하는 방법은 다음과 같습니다.

1. [그룹 정책 관리]를 엽니다.
2. 앞에서 만든 GPO를 마우스 오른쪽 단추로 클릭한 다음, **연결 사용**을 선택합니다. 메뉴 항목 옆에 확인란이 표시됩니다.

## <a name="step-5-test-primary-computer-function"></a>5단계: 기본 컴퓨터 기능 테스트

기본 컴퓨터 지원을 테스트하려면 기본 컴퓨터에 로그인하여 폴더와 프로필이 리디렉션되는 것을 확인한 다음, 기본 컴퓨터가 아닌 컴퓨터에 로그인하여 폴더와 프로필이 리디렉션되지 않는 것을 확인합니다.

기본 컴퓨터 기능을 테스트하는 방법은 다음과 같습니다.

1. 폴더 리디렉션 및/또는 로밍 사용자 프로필을 사용하도록 설정한 사용자 계정으로 기본 컴퓨터로 지정된 컴퓨터에 로그인합니다.
2. 사용자 계정이 이전에 컴퓨터에 로그온한 경우에는 관리자 권한으로 Windows PowerShell 세션 또는 명령 프롬프트 창을 열고 다음 명령을 입력한 다음, 최신 그룹 정책 설정이 클라이언트 컴퓨터에 적용되었는지 확인하는 다음 메시지가 표시되면 로그오프합니다.

    ```PowerShell
    Gpupdate /force
    ```

3. 파일 탐색기를 엽니다.
1. 리디렉션된 폴더(예: 문서 라이브러리의 내 문서 폴더)를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 선택합니다.
1. **위치** 탭을 선택하고, 경로가 로컬 경로 대신 본인이 지정한 파일 공유를 표시하는지 확인합니다. 사용자 프로필이 로밍 중인지 확인하려면 **제어판**을 열고 **시스템 및 보안**, **시스템**, **고급 시스템 설정**, **설정**(사용자 프로필 섹션)을 차례로 선택한 다음, **유형** 열에서 **로밍**을 확인합니다.
1. 사용자의 기본 컴퓨터로 지정되지 않은 컴퓨터에 동일한 사용자 계정으로 로그인합니다.
1. 로컬 경로 및 **로컬** 프로필 형식을 검색하는 대신 2~5 단계를 반복합니다.

> [!NOTE]
> 기본 컴퓨터 지원을 사용하도록 설정하기 전에 컴퓨터에서 폴더가 리디렉션된 경우 각 폴더의 폴더 리디렉션 정책 설정에서 **정책이 제거 될 때 로컬 사용자 프로필 위치로 다시 폴더 리디렉션** 설정을 구성하지 않는 한 폴더가 계속 리디렉션됩니다. 마찬가지로, 특정 컴퓨터에서 이전에 로밍하던 프로필은 **형식** 열의 **로밍**에 표시됩니다. 그러나 **상태** 열에는 **로컬**이 표시됩니다.

## <a name="more-information"></a>자세한 정보

- [오프라인 파일을 사용한 폴더 리디렉션 배포](deploy-folder-redirection.md)
- [로밍 사용자 프로필 배포](deploy-roaming-user-profiles.md)
- [폴더 리디렉션, 오프라인 파일 및 로밍 사용자 프로필 개요](folder-redirection-rup-overview.md)
- [Digging a little deeper into Windows 8 Primary Computer(Windows 8 기본 컴퓨터에 대해 자세히 알아보기)](https://blogs.technet.com/b/askds/archive/2012/10/23/digging-a-little-deeper-into-windows-8-primary-computer.aspx)