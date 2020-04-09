---
title: chcp
description: Windows 명령 항목을 참조 하세요 .이 항목은 활성 콘솔 코드 페이지를 변경 합니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dc7b1c71-7b80-443d-9cf1-9bcf305aa1fd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e644cf8544d135c5d21c344b0fd0a3364c7f89c1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847946"
---
# <a name="chcp"></a>chcp

활성 콘솔 코드 페이지를 변경합니다. 매개 변수 없이 사용 하는 경우 **chcp** 활성 콘솔 코드 페이지의 수를 표시 합니다.

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
chcp [<NNN>]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<NNN >|코드 페이지를 지정합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

다음 표에서 각 지원 되는 코드 페이지와 국가/지역 또는 언어를 나열합니다.

|코드 페이지|국가/지역 또는 언어|
|---------|--------------------------|
|437|미국|
|850|다국어 (라틴어 I)|
|852|슬라브어 (라틴어 II)|
|855|키릴 자모 (러시아어)|
|857|터키어|
|860|포르투갈어|
|861|아이슬란드어|
|863|프랑스어 (캐나다)|
|865|북유럽|
|866|러시아어|
|869|현대 그리스어|
|936|중국어|

## <a name="remarks"></a>주의

-   Windows와 함께 설치 되어 있는 원래 장비 제조업체 (OEM) 코드 페이지만 래스터 글꼴을 사용 하는 명령 프롬프트 창에 제대로 나타납니다. 트루타입 글꼴을 사용 하는 명령 프롬프트 창을 전체 화면 모드에 있거나 다른 코드 페이지가 제대로 표시 합니다.
-   코드 페이지 (MS-DOS)에서 같이 준비 필요가 없습니다.
-   한 후 시작 되는 프로그램 새 코드 페이지 사용 하는 새 코드 페이지를 할당 합니다. 그러나 (Cmd.exe) 제외 하기 전에 시작 하는 프로그램 원본 코드 페이지는 새 코드 페이지 사용을 할당 합니다.

## <a name="examples"></a><a name=BKMK_examples></a>예와

현재 코드 페이지 설정을 보려면 다음을 입력 합니다.
```
chcp
```
다음과 비슷한 메시지가 표시 됩니다.

`Active code page: 437`

활성 코드 페이지를 850 (다국어)로 변경 하려면 다음을 입력 합니다.
```
chcp 850
```
지정한 코드 페이지 유효 하지 않을 경우 다음과 같은 오류 메시지가 나타납니다.

`Invalid code page`

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)
