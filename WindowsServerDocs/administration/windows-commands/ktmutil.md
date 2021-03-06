---
title: ktmutil
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 53bc56df-f0e5-443b-ab20-bbf8b11d4a9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47b447165ee54e6839bb6338801c6703d818caa8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724520"
---
# <a name="ktmutil"></a>ktmutil



커널 트랜잭션 관리자 유틸리티를 시작합니다. 매개 변수 없이 사용 하는 경우 **ktmutil** 사용할 수 있는 하위 표시 됩니다.



## <a name="syntax"></a>구문

```
ktmutil list tms 
ktmutil list transactions [{TmGuid}]
ktmutil resolve complete {TmGuid} {RmGuid} {EnGuid}
ktmutil resolve commit {TxGuid}
ktmutil resolve rollback {TxGuid}
ktmutil force commit {??Guid}
ktmutil force rollback {??Guid}
ktmutil forget
```

### <a name="parameters"></a>매개 변수

## <a name="remarks"></a>설명

## <a name="examples"></a>예

커밋 GUID 311a9209-03f4-11dc-918f-00188b8f707b 포함 하는 Indoubt 트랜잭션을 강제 하려면 다음을 입력 합니다.
```
ktmutil force commit {311a9209-03f4-11dc-918f-00188b8f707b}
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)