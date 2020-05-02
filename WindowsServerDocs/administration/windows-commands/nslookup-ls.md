---
title: nslookup ls
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f15f06fe-67e7-41a9-93b5-192ab14ab380
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8357208406c0fca5d68da419baa2092d94fa9ec9
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723701"
---
# <a name="nslookup-ls"></a>nslookup ls

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

도메인 이름 시스템 (DNS) 도메인에 대 한 정보를 나열합니다.
## <a name="syntax"></a>구문
```
ls [<Option>] <DNSDomain> [{[>] <FileName>|[>>] <FileName>}]
```
### <a name="parameters"></a>매개 변수

|    매개 변수    |                                                                                                                                                                                                                                                                                                               설명                                                                                                                                                                                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <Option>     | 다음 표에서 사용할 수 있는 옵션을 나열합니다.<p>--t: 지정 된 형식의 모든 레코드를 나열 합니다. 에 대 한 설명은 <querytype>추가 참조에서 **setquerytype** 를 참조 하세요.<br />--a: DNS 도메인에 있는 컴퓨터의 별칭을 나열 합니다. 이 매개 변수는에 대 한 동의어 **-t CNAME**<br />--d: DNS 도메인에 대 한 모든 레코드를 나열 합니다. 이 매개 변수는에 대 한 동의어 **-t ANY**<br />--h: DNS 도메인에 대 한 CPU 및 운영 체제 정보를 나열 합니다. 이 매개 변수는에 대 한 동의어 **-t HINFO**<br />--s: DNS 도메인에 있는 컴퓨터의 잘 알려진 서비스를 나열 합니다. 이 매개 변수는에 대 한 동의어 **-t WKS**합니다. |
|   <DNSDomain>   |                                                                                                                                                                                                                                                                                         정보를 표시할 수 있는 DNS 도메인을 지정 합니다.                                                                                                                                                                                                                                                                                         |
|   <FileName>    |                                                                                                                                                                                                                                 출력을 저장 하는 파일 이름을 지정 합니다. 보다 큼 (>) 및 이중 사용할 수 있습니다 보다 큰 (>>) 문자를 일반적인 방법으로 출력을 리디렉션합니다.                                                                                                                                                                                                                                  |
| {도움말 및 #124;?} |                                                                                                                                                                                                                                                                                          간단한 요약이 표시 되며 **nslookup** 하위 명령입니다.                                                                                                                                                                                                                                                                                           |

## <a name="remarks"></a>설명
- 기본 출력 포함 컴퓨터 이름과 IP 주소입니다. 출력 파일을 서버에서 받은 모든 50 개의 레코드에 대 한 해시 표시가 인쇄 됩니다.
  ## <a name="additional-references"></a>추가 참조
  - [명령줄 구문 키](command-line-syntax-key.md)
  [nslookup querytype 설정](nslookup-set-querytype.md)
