---
title: 'ksetup: addkdc'
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98bfc23a-14c4-401c-bcb3-9903c5cdde64
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 76d592e4f1c32305d6f939a66a6ad42cd582b032
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724762"
---
# <a name="ksetupaddkdc"></a>ksetup: addkdc



지정 된 Kerberos 영역에 대 한 키 배포 센터 (KDC) 주소를 추가 합니다.

## <a name="syntax"></a>구문

```
ksetup /addkdc <RealmName> [<KDCName>] 
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<RealmName>|영역 이름은 CORP와 같은 대문자 DNS 이름으로 명시 됩니다. CONTOSO.COM는 **ksetup** 가 실행 될 때 기본 영역으로 나열 됩니다. 이 영역에서 다른 KDC를 추가 하려고 합니다.|
|\<KDCName>|KDC 이름은 대/소문자를 구분 하는 정규화 된 도메인 이름 (예: mitkdc.microsoft.com)으로 명시 됩니다. KDC 이름이 생략 되 면 DNS는 Kdc를 찾습니다.|

## <a name="remarks"></a>설명

이러한 매핑은 **HKEY_LOCAL_MACHINE \system\currentcontrolset\control\lsa\kerberos\domains**의 레지스트리에 저장 됩니다. Kerberos 영역 구성 데이터를 여러 컴퓨터에 배포 하려면 개별 컴퓨터에서 명시적으로 **ksetup** 를 사용 하는 대신 보안 구성 템플릿 스냅인 및 정책 배포를 사용 합니다.

새 영역 설정을 사용 하려면 먼저 컴퓨터를 다시 시작 해야 합니다.

컴퓨터의 기본 영역 이름을 확인 하거나이 명령이 의도 한 대로 작동 하는지 확인 하려면 명령 프롬프트에서 **ksetup** 를 실행 하 고 추가 된 KDC의 출력을 확인 합니다.

## <a name="examples"></a>예

비 Windows KDC 서버 및 워크스테이션에서 사용 해야 하는 영역을 구성 합니다.
```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```
이전 명령과 같은 컴퓨터의 명령줄에서 Ksetup 도구를 실행 하 여 로컬 컴퓨터 계정 암호 를%로 p@sswrd1설정 합니다. 그런 다음 컴퓨터를 다시 시작합니다.
```
Ksetup /setcomputerpassword p@sswrd1%
```

## <a name="additional-references"></a>추가 참조

-   [Ksetup](ksetup.md)
-   [Ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)
-   - [명령줄 구문 키](command-line-syntax-key.md)