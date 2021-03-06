---
title: serverweroptin
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f3c0b0af-cafb-4f09-8b36-5a357ddf392d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3acba57aa012c57c5c6109ed948ce6bb5b28078
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721948"
---
# <a name="serverweroptin"></a>serverweroptin

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

오류 보고를 사용할 수 있습니다.
## <a name="syntax"></a>구문
```
serverweroptin [/query] [/detailed] [/summary]
```
#### <a name="parameters"></a>매개 변수
|매개 변수|설명|
|-------|--------|
|/ 쿼리|현재 설정을 확인 합니다.|
|자세한 /|자세한 보고서를 자동으로 보냅니다.|
|요약 /|요약 보고서를 자동으로 보냅니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|
## <a name="examples"></a>예
현재 설정의 확인 하려면 다음을 입력 합니다.
```
serverweroptin /query
```
자세한 보고서를 자동으로 보내려면 다음을 입력 합니다.
```
serverweroptin /detailed
```
요약 보고서를 자동으로 전송 하려면 다음을 입력합니다
```
serverweroptin /summary
```
## <a name="additional-references"></a>추가 참조
-   - [명령줄 구문 키](command-line-syntax-key.md)

