---
title: 수입
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 569d986c57ae8b3d7253c050146ac0583c7c92df
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724842"
---
# <a name="import"></a>수입



로컬 컴퓨터의 디스크 그룹에 외부 디스크 그룹을 가져옵니다.

## <a name="syntax"></a>구문

```
import [noerr]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|noerr|스크립팅 전용입니다. 오류가 발생 하면 오류가 발생 하지 않은 경우에 따라 명령을 처리 하도록 DiskPart 계속 합니다. 이 매개 변수를 크기는 오류 코드를 수행 합니다.|

## <a name="remarks"></a>설명

-   Import 명령 포커스가 있는 디스크와 동일한 그룹에 있는 모든 디스크를 가져옵니다.
-   이 작업이 성공 하기 위해 외부 디스크 그룹에서 동적 디스크를 선택 해야 합니다. 사용 된 **디스크 선택** 디스크를 선택 하 고 포커스를 이동 하는 명령입니다.

## <a name="examples"></a>예

로컬 컴퓨터의 디스크 그룹에 포커스가 있는 디스크와 같은 디스크 그룹에 있는 모든 디스크를 가져오려면 다음을 입력 합니다.
```
import
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)

