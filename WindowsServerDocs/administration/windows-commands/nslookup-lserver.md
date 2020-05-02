---
title: nslookup lserver
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b2054c0fd427b41e7d6076258b29ab78d0fb7892
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723672"
---
# <a name="nslookup-lserver"></a>nslookup lserver

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

지정된 된 도메인 이름 시스템 (DNS) 도메인에 기본 서버를 변경합니다.
## <a name="syntax"></a>구문
```
lserver <DNSDomain> 
```
### <a name="parameters"></a>매개 변수

|    매개 변수    |                      설명                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | 기본 서버에 대 한 새 DNS 도메인을 지정합니다.  |
| {도움말 및 #124;?} | 간단한 요약이 표시 되며 **nslookup** 하위 명령입니다. |

## <a name="remarks"></a>설명
- **lserver** 명령은 초기 서버를 사용 하 여 지정된 된 DNS 도메인에 대 한 정보를 조회 합니다. 이 달리는 **서버** 현재의 기본 서버를 사용 하는 명령입니다.
  ## <a name="additional-references"></a>추가 참조
  - [명령줄 구문 키](command-line-syntax-key.md)
  [nslookup 서버](nslookup-server.md)
