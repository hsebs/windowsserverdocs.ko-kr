---
title: 소프트웨어 제한 정책 관리
description: Windows Server 보안
ms.prod: windows-server
ms.technology: security-software-restriction-policies
ms.topic: article
ms.assetid: 8cc22093-67d1-47b6-9ddd-4569b6761ce9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 88e745b6951ab27f22cc412ee63f792d30775d14
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855116"
---
# <a name="administer-software-restriction-policies"></a>소프트웨어 제한 정책 관리

>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

IT 전문가를 위한이 항목에는 Windows Server 2008 및 Windows Vista부터 SRP (소프트웨어 제한 정책)를 사용 하 여 응용 프로그램 제어 정책을 관리 하는 절차가 포함 되어 있습니다.

## <a name="introduction"></a>소개
SRP(소프트웨어 제한 정책)는 도메인의 컴퓨터에서 실행 중인 소프트웨어 프로그램을 식별하고, 실행할 해당 프로그램의 기능을 제어하는 그룹 정책 기반 기능입니다. 소프트웨어 제한 정책을 사용하면 명확하게 식별된 애플리케이션만 실행할 수 있도록 고도로 제한된 컴퓨터 구성을 만들 수 있습니다. 이러한 기능은 Microsoft Active Directory Domain Services 및 그룹 정책와 통합 되어 있지만 독립 실행형 컴퓨터 에서도 구성할 수 있습니다. SRP에 대 한 자세한 내용은 [소프트웨어 제한 정책](software-restriction-policies.md)을 참조 하십시오.

Windows Server 2008 R2 및 Windows 7 부터는 응용 프로그램 제어 전략의 일부에 대 한 SRP를 사용 하거나 사용 하지 않고 Windows AppLocker를 사용할 수 있습니다.

이 항목에는 다음 내용이 포함 되어 있습니다.

-   [소프트웨어 제한 정책을 열려면](#BKMK_Open_SRP)

-   [새 소프트웨어 제한 정책을 만들려면](#BKMK_Create_SRP)

-   [지정 된 파일 형식을 추가 하거나 삭제 하려면](#BKMK_Add_Del)

-   [소프트웨어 제한 정책이 로컬 관리자에 게 적용 되지 않도록 하려면](#BKMK_Prevent_Admin)

-   [소프트웨어 제한 정책의 기본 보안 수준을 변경 하려면](#BKMK_Sec_Lvl)

-   [Dll에 소프트웨어 제한 정책을 적용 하려면](#BKMK_Apply_SRP_DLLs)

SRP를 사용 하 여 특정 작업을 수행 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

-   [소프트웨어 제한 정책에 대 한 허용-거부 목록 및 응용 프로그램 인벤토리 결정](determine-allow-deny-list-and-application-inventory-for-software-restriction-policies.md)

-   [소프트웨어 제한 정책 규칙 사용](work-with-software-restriction-policies-rules.md)

-   [소프트웨어 제한 정책을 사용 하 여 전자 메일 바이러스 로부터 컴퓨터를 보호 합니다.](use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus.md)

## <a name="to-open-software-restriction-policies"></a><a name="BKMK_Open_SRP"></a>소프트웨어 제한 정책을 열려면

-   [로컬 컴퓨터의 경우](#BKMK_1)

-   [도메인, 사이트 또는 조직 구성 단위의 경우 도메인에 가입 된 워크스테이션 또는 구성원 서버에 있는 경우](#BKMK_2)

-   [도메인 또는 조직 구성 단위에 대해, 원격 서버 관리 도구 설치 된 도메인 컨트롤러 또는 워크스테이션에 있습니다.](#BKMK_3)

-   [사이트의 경우, 원격 서버 관리 도구 설치 된 도메인 컨트롤러 또는 워크스테이션에 있습니다.](#BKMK_4)

### <a name="for-your-local-computer"></a><a name="BKMK_1"></a>로컬 컴퓨터의 경우

1.  로컬 보안 설정을 엽니다.

2.  콘솔 트리에서 **소프트웨어 제한 정책**을 클릭 합니다.

    **위치?**

    -   보안 설정/소프트웨어 제한 정책

> [!NOTE]
> 이 절차를 수행하려면 로컬 컴퓨터에서 Administrators 그룹의 멤버이거나 적절한 권한을 위임 받아야 합니다.

### <a name="for-a-domain-site-or-organizational-unit-and-you-are-on-a-member-server-or-on-a-workstation-that-is-joined-to-a-domain"></a><a name="BKMK_2"></a>도메인, 사이트 또는 조직 구성 단위의 경우 도메인에 가입 된 워크스테이션 또는 구성원 서버에 있는 경우

1.  MMC(Microsoft Management Console)를 엽니다.

2.  **파일** 메뉴에서 **스냅인 추가/제거**를 클릭 한 다음 **추가**를 클릭 합니다.

3.  **로컬 그룹 정책 개체 편집기**를 클릭하고 **추가**를 클릭합니다.

4.  **그룹 정책 개체 선택**에서 **찾아보기**를 클릭합니다.

5.  **그룹 정책 개체 찾아보기**에서 해당 도메인, 사이트 또는 조직 구성 단위에 있는 그룹 정책 개체 (GPO)를 선택 하거나 새 개체 (GPO)를 만든 후 **마침**을 클릭 합니다.

6.  **닫기**, **확인**을 차례로 클릭합니다.

7.  콘솔 트리에서 **소프트웨어 제한 정책**을 클릭 합니다.

    **위치?**

    -   *그룹 정책 개체* [*ComputerName*] 정책/컴퓨터 구성 또는

        사용자 구성/w i n d o w s 설정/보안 설정/소프트웨어 제한 정책

> [!NOTE]
> 이 절차를 수행 하려면 Domain Admins 그룹의 구성원 이어야 합니다.

### <a name="for-a-domain-or-organizational-unit-and-you-are-on-a-domain-controller-or-on-a-workstation-that-has-the-remote-server-administration-tools-installed"></a><a name="BKMK_3"></a>도메인 또는 조직 구성 단위에 대해, 원격 서버 관리 도구 설치 된 도메인 컨트롤러 또는 워크스테이션에 있습니다.

1.  그룹 정책 관리 콘솔를 엽니다.

2.  콘솔 트리에서 소프트웨어 제한 정책을 열려는 GPO (그룹 정책 개체)를 마우스 오른쪽 단추로 클릭 합니다.

3.  **편집**을 클릭하여 편집할 GPO를 엽니다. **새로 만들기**를 클릭하여 새 GPO를 만든 다음 **편집**을 클릭할 수도 있습니다.

4.  콘솔 트리에서 **소프트웨어 제한 정책**을 클릭 합니다.

    **위치?**

    -   *그룹 정책 개체* [*ComputerName*] 정책/컴퓨터 구성 또는

        사용자 구성/w i n d o w s 설정/보안 설정/소프트웨어 제한 정책

> [!NOTE]
> 이 절차를 수행 하려면 Domain Admins 그룹의 구성원 이어야 합니다.

### <a name="for-a-site-and-you-are-on-a-domain-controller-or-on-a-workstation-that-has-the-remote-server-administration-tools-installed"></a><a name="BKMK_4"></a>사이트의 경우, 원격 서버 관리 도구 설치 된 도메인 컨트롤러 또는 워크스테이션에 있습니다.

1.  그룹 정책 관리 콘솔를 엽니다.

2.  콘솔 트리에서 그룹 정책 설정 하려는 사이트를 마우스 오른쪽 단추로 클릭 합니다.

    **위치?**

    -   Active Directory 사이트 및 서비스 [*Domain_Controller_Name. Domain_Name*]/Sites/Site

3.  **그룹 정책 개체 링크** 의 항목을 클릭 하 여 기존 그룹 정책 개체 (GPO)를 선택한 다음 **편집**을 클릭 합니다. **새로 만들기**를 클릭하여 새 GPO를 만든 다음 **편집**을 클릭할 수도 있습니다.

4.  콘솔 트리에서 **소프트웨어 제한 정책**을 클릭 합니다.

    **위치**

    -   *그룹 정책 개체* [*ComputerName*] 정책/컴퓨터 구성 또는

        사용자 구성/w i n d o w s 설정/보안 설정/소프트웨어 제한 정책

> [!NOTE]
> -   이 절차를 수행하려면 로컬 컴퓨터에서 Administrators 그룹의 멤버이거나 적절한 권한을 위임 받아야 합니다. 컴퓨터가 도메인에 가입된 경우 Domain Admins 그룹의 멤버가 이 절차를 수행할 수 있습니다.
> -   컴퓨터에 적용 되는 정책 설정을 설정 하려면 사용자가 로그온 하는 사용자에 관계 없이 **컴퓨터 구성**을 클릭 합니다.
> -   사용자가 로그온 하는 컴퓨터에 관계 없이 사용자에 게 적용 되는 정책 설정을 설정 하려면 **사용자 구성**을 클릭 합니다.

## <a name="to-create-new-software-restriction-policies"></a><a name="BKMK_Create_SRP"></a>새 소프트웨어 제한 정책을 만들려면

1.  소프트웨어 제한 정책을 엽니다.

2.  **작업** 메뉴에서 **새 소프트웨어 제한 정책**을 클릭합니다.

> [!WARNING]
> -   사용자 환경에 따라 이 절차를 수행하는 데 서로 다른 관리 자격 증명 필요합니다.
> 
>     -   로컬 컴퓨터에 대 한 새 소프트웨어 제한 정책을 만드는 경우:이 절차를 완료 하려면 최소한 로컬 **Administrators** 그룹의 구성원 이거나이에 해당 하는 권한이 있어야 합니다.
>     -   도메인에 가입된 컴퓨터에 대한 새 소프트웨어 제한 정책을 만들 경우 Domain Admins 그룹의 구성원이 이 절차를 수행할 수 있습니다.
> -   소프트웨어 제한 정책이 GPO(그룹 정책 개체)에 대해 생성된 경우 **새 소프트웨어 제한 정책** 명령이 **작업** 메뉴에 나타나지 않습니다. 콘솔 트리에서 GPO에 적용되는 소프트웨어 제한 정책을 삭제하려면 **소프트웨어 제한 정책**을 마우스 오른쪽 단추로 클릭하고 **소프트웨어 제한 정책 삭제**를 클릭합니다. GPO에 대 한 소프트웨어 제한 정책을 삭제 하면 해당 GPO에 대 한 모든 소프트웨어 제한 정책 규칙도 삭제 됩니다. 소프트웨어 제한 정책을 삭제했으면 해당 GPO에 대한 새 소프트웨어 제한 정책을 만들 수 있습니다.

## <a name="to-add-or-delete-a-designated-file-type"></a><a name="BKMK_Add_Del"></a>지정 된 파일 형식을 추가 하거나 삭제 하려면

1.  소프트웨어 제한 정책을 엽니다.

2.  세부 정보 창에서 **지정된 파일 형식**을 두 번 클릭합니다.

3.  다음 작업 중 하나를 수행합니다.

    -   파일 형식을 추가하려면 **파일 이름 확장명**에서 파일 이름 확장명을 입력하고 **추가**를 클릭합니다.

    -   파일 형식을 삭제하려면 **지정된 파일 형식**에서 파일 형식을 클릭한 후 **제거**를 클릭합니다.

> [!NOTE]
> -   지정한 파일 형식을 추가하거나 삭제하는 환경에 따라 이 절차를 수행하는 데 서로 다른 관리 자격 증명이 필요합니다.
> 
>     -   로컬 컴퓨터에 대해 지정 된 파일 형식을 추가 하거나 삭제 하는 경우이 절차를 완료 하려면 최소한 로컬 **Administrators** 그룹의 구성원 이거나 이와 동등한 자격이 있어야 합니다.
>     -   도메인에 가입된 컴퓨터에 대한 새 소프트웨어 제한 정책을 만들 경우 Domain Admins 그룹의 구성원이 이 절차를 수행할 수 있습니다.
> -   아직 이와 같이 적용하지 않은 경우 GPO(그룹 정책 개체)에 대해 새 소프트웨어 제한 정책 설정을 만들어야 할 수 있습니다.
> -   지정 된 파일 형식 목록은 컴퓨터 구성 및 GPO에 대 한 사용자 구성 모두에 대 한 모든 규칙에서 공유 됩니다.

## <a name="to-prevent-software-restriction-policies-from-applying-to-local-administrators"></a><a name="BKMK_Prevent_Admin"></a>소프트웨어 제한 정책이 로컬 관리자에 게 적용 되지 않도록 하려면

1.  소프트웨어 제한 정책을 엽니다.

2.  세부 정보 창에서 **적용**을 두 번 클릭합니다.

3.  **다음 사용자에게 소프트웨어 제한 정책 적용** 아래에서 **로컬 관리자 제외한 모든 사용자**를 클릭합니다.

> [!WARNING]
> -   로컬 **관리자** 그룹의 멤버십 또는 이에 상당하는 멤버십은 이 절차를 완료하기 위해 필요한 최소 기준입니다.
> -   아직 이와 같이 적용하지 않은 경우 GPO(그룹 정책 개체)에 대해 새 소프트웨어 제한 정책 설정을 만들어야 할 수 있습니다.
> -   일반적으로 사용자가 사용자 조직의 컴퓨터에서 로컬 관리자 그룹의 구성원인 경우 이 옵션이 필요하지 않을 수도 있습니다.
> -   로컬 컴퓨터에 대한 소프트웨어 제한 정책 설정을 정의하는 경우 이 절차를 통해 로컬 관리자가 적용된 소프트웨어 제한 정책을 적용하지 못하도록 방지합니다. 네트워크에 대 한 소프트웨어 제한 정책 설정을 정의 하는 경우 그룹 정책를 통해 보안 그룹의 멤버 자격에 따라 사용자 정책 설정을 필터링 합니다.

## <a name="to-change-the-default-security-level-of-software-restriction-policies"></a><a name="BKMK_Sec_Lvl"></a>소프트웨어 제한 정책의 기본 보안 수준을 변경 하려면

1.  소프트웨어 제한 정책을 엽니다.

2.  세부 정보 창에서 **보안 수준**을 두 번 클릭합니다.

3.  기본값으로 설정하려는 보안 정책을 마우스 오른쪽 단추로 클릭한 다음 **기본값으로 설정**을 클릭합니다.

> [!CAUTION]
> 특정 디렉터리에서 기본 보안 수준을 **허용 안 함**으로 설정하면 운영 체제에 부정적인 영향을 미칠 수 있습니다.

> [!NOTE]
> -   소프트웨어 제한 정책의 기본 보안 수준을 변경하는 환경에 따라 이 절차를 수행하는 데 서로 다른 관리 자격 증명이 필요합니다.
> -   아직 이와 같이 적용하지 않은 경우 이 GPO(그룹 정책 개체)에 대한 새 소프트웨어 제한 정책 설정을 만들어야 할 수 있습니다.
> -   세부 정보 창에서 현재 기본 보안 수준이 검정색 원 안에 확인 표시가 있는 상태로 표시됩니다. 현재 기본 보안 수준을 마우스 오른쪽 단추로 클릭하면 **기본값으로 설정** 명령이 메뉴에 표시되지 않습니다.
> -   소프트웨어 제한 정책 규칙은 기본 보안 수준에 대 한 예외를 지정 하기 위해 생성 됩니다. 기본 보안 수준이 **무제한**으로 설정되면 규칙을 통해 실행이 허용되지 않는 소프트웨어를 지정할 수 있습니다. 기본 보안 수준이 **허용 안 함**으로 설정되면 규칙을 통해 실행이 허용되는 소프트웨어를 지정할 수 있습니다.
> -   설치 시 시스템에 있는 모든 파일에 대한 소프트웨어 제한 정책의 기본 보안 수준은 **무제한**으로 설정됩니다.

## <a name="to-apply-software-restriction-policies-to-dlls"></a><a name="BKMK_Apply_SRP_DLLs"></a>Dll에 소프트웨어 제한 정책을 적용 하려면

1.  소프트웨어 제한 정책을 엽니다.

2.  세부 정보 창에서 **적용**을 두 번 클릭합니다.

3.  **소프트웨어 제한 정책을 다음에 적용** 아래에서 **모든 소프트웨어 파일**을 클릭합니다.

> [!NOTE]
> -   이 절차를 수행하려면 로컬 컴퓨터에서 Administrators 그룹의 멤버이거나 적절한 권한을 위임 받아야 합니다. 컴퓨터가 도메인에 가입된 경우 Domain Admins 그룹의 멤버가 이 절차를 수행할 수 있습니다.
> -   기본적으로 소프트웨어 제한 정책에서는 DLL(동적 연결 라이브러리)을 검사하지 않습니다. DLL을 검사하면 DLL을 로드할 때마다 소프트웨어 제한 정책이 평가되어야 하므로 시스템 성능이 저하될 수 있습니다. 그러나 DLL을 대상으로 하는 바이러스 수신이 염려될 경우 DLL을 검사하도록 결정할 수도 있습니다. 기본 보안 수준이 **허용 안 함**으로 설정 되어 있고 dll 검사를 사용 하도록 설정한 경우에는 각 dll을 실행할 수 있도록 하는 소프트웨어 제한 정책 규칙을 만들어야 합니다.


