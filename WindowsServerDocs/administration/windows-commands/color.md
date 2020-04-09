---
title: 색
description: 현재 세션에 대 한 명령 프롬프트 창의 전경색과 배경색을 변경 하는 Windows 명령 항목의 색입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f5b67131-d196-45ec-a3f9-b5d9f091fd86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0e89c20d90a3b812fa67b597c4c205d34e725785
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847486"
---
# <a name="color"></a>색

현재 세션에 대 한 명령 프롬프트 창에서 전경색 및 배경색을 변경 합니다. 매개 변수 없이 사용 하는 경우 **색** 기본 명령 프롬프트 창 전경색 및 배경색을 복원 합니다.

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
color [[<B>]<F>]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<B >|배경색을 지정합니다.|
|\<F >|전경색을 지정합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="remarks"></a>주의

-   다음 표에는 *B* 및 *F*의 값으로 사용할 수 있는 유효한 16 진수가 나와 있습니다.

|값|색|
|-----|-----|
|0|검정|
|1|파랑|
|2|녹색|
|3|Aqua|
|4|빨강|
|5|Purple|
|6|Yellow|
|7|하얀|
|8|회색|
|9|연한 파랑|
|A|연한 녹색|
|B|연한 바다색|
|C|연한 빨간색|
|D|연한 자주색|
|E|밝은 노랑|
|F|밝은 백서|
    
-   *B* 와 *F*사이에 공백 문자를 사용 하지 마십시오.
-   16 진수를 하나만 지정 하는 경우 해당 색은 전경색으로 사용 되 고 배경색은 기본 색으로 설정 됩니다.
-   기본 명령 프롬프트 창 색을 설정 하려면 명령 프롬프트 창의 왼쪽 위 모퉁이를 클릭 하 고 **기본값**, **색** 탭을 차례로 클릭 한 다음 **화면 텍스트** 및 **화면 배경에**사용할 색을 클릭 합니다.
-   *B* 와 *F* 가 동일 하면 **color** 명령에서 ERRORLEVEL을 1로 설정 하 고 전경색 또는 배경색을 변경 하지 않습니다.

## <a name="examples"></a><a name=BKMK_examples></a>예와

명령 프롬프트 창의 배경색을 회색으로 변경 하 고 전경색을 빨강으로 변경 하려면 다음을 입력 합니다.
```
color 84
```
명령 프롬프트 창의 전경색을 연한 노랑으로 변경 하려면 다음을 입력 합니다.
```
color e
```

> [!NOTE]
> 이 예제에서는 하나의 16 진수가 지정 되어 있으므로 배경은 기본 색으로 설정 됩니다.

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)
