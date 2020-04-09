---
title: bitsadmin getproxylist-지정 된 작업에 대 한 프록시 목록을 검색 합니다.
description: 지정 된 작업에 대 한 프록시 목록을 검색 하는 **bitsadmin getproxylist**에 대 한 Windows 명령 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0c0d26fb074bd1b792caa7fe2ce8fd31b64365e2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850526"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

지정 된 작업에 사용할 쉼표로 구분 된 프록시 서버 목록을 검색 합니다.

## <a name="syntax"></a>구문

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>매개 변수

| 매개 변수 | 설명 |
| -------------- | -------------- |
| 제출 | 작업의 표시 이름 또는 GUID입니다. |

## <a name="examples"></a><a name=BKMK_examples></a>예와

다음 예제에서는 명명 된 작업에 대 한 프록시 목록을 검색 *myDownloadJob*합니다.

```
C:\>bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)