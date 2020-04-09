---
title: 'ksetup: removerealm'
description: '\* * * *에 대 한 Windows 명령 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1465ce08c0cf45de828683324b29fb2df8d0e893
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841456"
---
# <a name="ksetupremoverealm"></a>ksetup: removerealm



레지스트리에서 지정한 영역에 대 한 모든 정보를 삭제합니다. 이 명령을 사용할 수 있는 방법을의 예 참조 [예제](#BKMK_Examples)합니다.

## <a name="syntax"></a>구문

```
ksetup /removerealm <RealmName>
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<RealmName >|영역 이름은 CORP와 같은 대문자 DNS 이름으로 명시 됩니다. CONTOSO.COM는 **ksetup** 가 실행 될 때 기본 영역으로 나열 됩니다.|

## <a name="remarks"></a>주의

영역 이름은 **HKEY_LOCAL_MACHINE \system\controlset001** 및 **\CurrentControlSet\Control\Lsa\Kerberos**레지스트리의 두 위치에 저장 됩니다.

도메인 컨트롤러에서 기본 영역 이름을 제거할 수 없습니다. DNS 정보를 다시 설정 하 고 제거 하면 도메인 컨트롤러를 사용할 수 없게 될 수 있습니다.

## <a name="examples"></a><a name=BKMK_Examples></a>예와

실수로 로컬 컴퓨터에서 영역 이름을 잘못 된 이름으로 설정 합니다. CONTOSO.COM. 이라는
```
ksetup /setrealm CORP.CONTOSO.CON
```
로컬 컴퓨터에서 잘못 된 영역 이름을 제거 합니다.
```
ksetup /removerealm CORP.CONTOSO.CON
```
**Ksetup** 를 실행 하 여 제거를 확인 하 고 출력을 검토 합니다.

## <a name="additional-references"></a>추가 참조

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   - [명령줄 구문 키](command-line-syntax-key.md)