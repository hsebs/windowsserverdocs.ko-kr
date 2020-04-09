---
title: nslookup set srchlist
description: '\* * * *에 대 한 Windows 명령 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbeb09501474ade670147a6021abd2bb25291d71
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838286"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

기본 DNS (Domain Name System) 도메인 이름 및 검색 목록을 변경 합니다.

## <a name="syntax"></a>구문
```
Set srchlist=<DomainName>[/...]
```
### <a name="parameters"></a>매개 변수

|    매개 변수    |                                                                                        설명                                                                                        |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <DomainName>   | 기본 DNS 도메인 및 검색 목록에 대 한 새 이름을 지정합니다. 기본 도메인 이름 값은 호스트 이름을 기반으로 합니다. 최대 6 개의 이름 슬래시 (/) 구분 하 여 지정할 수 있습니다. |
| {도움말 및 #124;?} |                                                                   간단한 요약이 표시 되며 **nslookup** 하위 명령입니다.                                                                   |

## <a name="remarks"></a>주의
- **srchlist 설정**명령을 사용 하면 재정의 기본 DNS 도메인 이름 및 검색 목록에는 **집합 도메인** 명령입니다. 사용 하는 **모두 설정** 목록을 표시 하는 명령입니다.
  ## <a name="examples"></a><a name=BKMK_examples></a>예와
  다음 예제에서는 mfg.widgets.com, 이름 3 개를 검색 목록에 DNS 도메인을 설정합니다.
  ```
  set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
  ```
  ## <a name="additional-references"></a>추가 참조
  - [명령줄 구문 키](command-line-syntax-key.md)
  [nslookup set domain](nslookup-set-domain.md)
  nslookup set [all](nslookup-set-all.md)
