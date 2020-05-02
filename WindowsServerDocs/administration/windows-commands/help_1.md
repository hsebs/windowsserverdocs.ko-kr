---
title: 도움말
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6887edfd41895bb151c5aaebb88d8b72198f4dbf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724902"
---
# <a name="help"></a>도움말

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

지정한 명령에 사용할 수 있는 명령 또는 자세한 도움말 정보 목록을 표시합니다.  
  
  
  
## <a name="syntax"></a>구문  
  
```  
help [<command>]  
```  
  
### <a name="parameters"></a>매개 변수  
  
| 매개 변수 |                              설명                              |
|-----------|-----------------------------------------------------------------------|
| <command> | 자세한 도움말 정보를 표시 하는 명령을 지정 합니다. |
  
## <a name="remarks"></a>설명  
  
-   명령을 지정 하지 않으면 가능한 모든 명령이 **도움말** 에 표시 됩니다.  
  
## <a name="examples"></a>예  
DiskPart에서 사용할 수 있는 모든 명령 목록을 표시 하려면 다음을 입력 합니다.  
  
```  
help  
```  
  
사용 하는 방법에 대 한 자세한 도움말 정보를 표시 하는 **파티션을 주 만들** 형식 DiskPart 명령을:  
  
```  
help create partition primary  
```  
  
## <a name="additional-references"></a>추가 참조  
- [명령줄 구문 키](command-line-syntax-key.md)  
  

  

