---
title: Sc delete
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dd40b5eb82def3b3c437cbdb5b60d279529d25a0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722188"
---
# <a name="sc-delete"></a>Sc delete



레지스트리에서 서비스 하위 키를 삭제합니다. 서비스가 실행 중인지 또는 다른 프로세스에서 열린 핸들을 서비스 하는 경우 서비스 삭제 되도록 표시 됩니다.

이 명령을 사용하는 방법의 예는 [예](#examples)를 참조하세요.

## <a name="syntax"></a>구문

```
sc [<ServerName>] delete [<ServiceName>]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<ServerName>|서비스 위치는 원격 서버의 이름을 지정 합니다. 이름은 UNC (범용 명명 규칙) 형식 (예: \\ \\myserver)을 사용 해야 합니다. SC.exe를 로컬로 실행 하려면이 매개 변수를 생략 합니다.|
|\<ServiceName>|반환 된 서비스 이름을 지정는 **getkeyname** 작업 합니다.|
|?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="remarks"></a>설명

사용 하 여 **프로그램 추가 / 제거** 에 **제어판** DHCP, DNS, 또는 다른 기본 제공 운영 체제 서비스를 삭제 합니다. **프로그램 추가 / 제거** 만 서비스에 대 한 레지스트리 하위 키를 제거 하지 것입니다 하지만 하도 서비스를 제거 하 여 모든 바로 가기를 삭제 합니다.

## <a name="examples"></a>예

서비스 하위 키를 삭제 하려면 **NewServ** 로컬 컴퓨터에서 레지스트리를에서 다음 명령을 입력 합니다.
```
sc delete newserv
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)