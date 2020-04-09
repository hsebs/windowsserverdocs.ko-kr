---
title: trEE
description: 트리의 디렉터리 구조 또는 드라이브의 디스크를 그래픽으로 표시 하는 트리에 대 한 Windows 명령 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 345d3192-401e-4a3b-a8ac-36a85c7be79d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 14b9a4dfd5c84b55a32dbc3f6fd7e8a2cc00c7ba
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832676"
---
# <a name="tree"></a>trEE

드라이브에서의 경로 또는 디스크의 디렉터리 구조를 그래픽으로 표시 합니다.

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
tree [<Drive>:][<Path>] [/f] [/a]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<드라이브 >:|디렉터리 구조를 표시 하려는 디스크를 포함 하는 드라이브를 지정 합니다.|
|\<경로 >|디렉터리 구조를 표시 하려는 디렉터리를 지정 합니다.|
|/f|각 디렉터리에 있는 파일의 이름을 표시 합니다.|
|/a|**트리가** 그래픽 문자 대신 텍스트 문자를 사용 하 여 하위 디렉터리를 연결 하는 줄을 표시 하도록 지정 합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="remarks"></a>주의

표시 구조 **트리** 명령 프롬프트에서 지정 하는 매개 변수에 따라 달라 집니다. 드라이브 또는 경로 지정 하지 않으면 **트리** 현재 드라이브의 현재 디렉터리부터 시작 하는 트리 구조를 표시 합니다.

## <a name="examples"></a><a name=BKMK_examples></a>예와

모든 하위 디렉터리의 이름을 현재 드라이브에 디스크를 표시 하려면 다음을 입력 합니다.
```
tree \
```
C 드라이브에 있는 모든 디렉터리에서 파일을 한 번에 한 화면씩 표시 하려면 다음을 입력 합니다.
```
tree c:\ /f | more 
```
C 드라이브에 있는 모든 디렉터리의 목록을 인쇄 하려면 다음을 입력 합니다.
```
tree c:\ /f  prn 
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)