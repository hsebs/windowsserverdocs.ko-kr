---
title: bitsadmin getcreationtime
description: 지정 된 작업에 대 한 생성 시간을 검색 하는 bitsadmin getcreationtime 명령에 대 한 참조 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be409cb5-ce72-41d9-aafa-edd4e230fd14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dc6ca5ad23730e9f57d58e069e0a2daf961930e8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718111"
---
# <a name="bitsadmin-getcreationtime"></a>bitsadmin getcreationtime

지정 된 작업의 만든 시간을 검색 합니다.

## <a name="syntax"></a>구문

```
bitsadmin /getcreationtime <job>
```

### <a name="parameters"></a>매개 변수

| 매개 변수 | 설명 |
| -------------- | -------------- |
| 작업(job) | 작업의 표시 이름 또는 GUID입니다. |

## <a name="examples"></a>예

*Mydownloadjob*이라는 작업을 만든 시간을 검색 하려면 다음을 수행 합니다.

```
bitsadmin /getcreationtime myDownloadJob
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)

- [bitsadmin 명령](bitsadmin.md)
