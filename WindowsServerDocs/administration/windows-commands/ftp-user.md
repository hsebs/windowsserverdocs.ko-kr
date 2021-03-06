---
title: ftp 사용자
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cb4f0f47f23bec312c57266479c261c96535e8cc
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725073"
---
# <a name="ftp-user"></a>ftp: 사용자

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

원격 컴퓨터에 사용자를 지정합니다.   
## <a name="syntax"></a>구문  
```  
user <UserName> [<Password>] [<Account>]  
```  
#### <a name="parameters"></a>매개 변수  

|  매개 변수   |                                                                      설명                                                                      |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <UserName>  |                                          원격 컴퓨터에 로그온 하는 데 사용할 사용자 이름을 지정 합니다.                                           |
| [<Password>] |               암호를 지정 *UserName*합니다. 암호는 지정 하지 않고 필요한 경우  **ftp** 암호를 묻는 메시지를 표시 합니다.               |
| [<Account>]  | 원격 컴퓨터에 로그온 하는 데 사용할 계정을 지정 합니다. 하는 경우는 *계정* 는 지정 하지 않고 필요 하며,  **ftp** 는 계정에 대 한 메시지를 표시 합니다. |

## <a name="examples"></a>예  
User1 Password1 암호로 지정 합니다.  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>추가 참조  
-   - [명령줄 구문 키](command-line-syntax-key.md)  
