---
title: prompt
description: 명령 프롬프트를 사용자 지정 하는 방법을 알아봅니다.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d98e965-02eb-46ad-9d0a-5dc44830373e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 320e12fd30deda30ccc0da1ad6e5bea6f9a19d8a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818444"
---
# <a name="prompt"></a>prompt



Cmd.exe 명령 프롬프트를 변경합니다. 매개 변수 없이 사용 하는 경우 **프롬프트** 명령 프롬프트는 현재 드라이브 문자와 디렉터리를 보다 큼 기호 뒤의 기본 설정으로 다시 설정 (**>**).

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
prompt [<Text>]
```

## <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<텍스트 >|텍스트 및 명령 프롬프트에 포함 하려는 정보를 지정 합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="remarks"></a>설명

현재 디렉터리, 시간 및 날짜 및 Microsoft Windows 버전 번호의 이름으로 이러한 정보를 포함 하 여 원하는 텍스트를 표시 하려면 명령 프롬프트를 사용자 지정할 수 있습니다.

다음 표에서 대신, 또는 외에 하나 이상의 문자 문자열에 포함할 수 있는 문자 조합을 *텍스트* 매개 변수입니다. 목록에는 텍스트 또는 문자 조합이 각 명령 프롬프트에 추가 하는 정보에 대 한 간단한 설명은 포함 되어 있습니다.  
|문자|설명|
|---------|-----------|
|$q|= (등호)|
|$$|$(달러 기호)|
|$t|현재 시간|
|$d|현재 날짜|
|$p|현재 드라이브 및 경로|
|$v|Windows 버전 번호|
|$n|현재 드라이브|
|$g|> (보다 큼 기호)|
|$l|< (보다 작음 부호)|
|$b|| (파이프)|
|$_|입력 줄 바꿈|
|$e|ANSI 이스케이프 코드 (27)|
|$h|백스페이스 (명령줄에 작성 된 문자)|
|$는|& (앰퍼샌드)|
|$c|((왼쪽된 괄호)|
|$f|) (오른쪽 괄호)|
|$s|공간|

명령 확장을 사용 하는 경우 (기본값)는 **프롬프트** 명령이 다음 형식 지정 문자를 지원 합니다.  

|문자|설명|
|---------|-----------|
|$+|0 개 이상의 더하기 기호 (**+**)의 깊이 따라 문자는 **pushd** 디렉터리 스택 (수준 푸시되 각각에 대해 1 자).|
|$m|현재 드라이브를 네트워크 드라이브로 없는 경우 현재 드라이브 문자 또는 빈 문자열와 연결 된 원격 이름입니다.|

포함 하는 경우는 **$p** 문자 텍스트 매개 변수에서 디스크를 각 명령 (현재 드라이브와 경로 결정)를 입력 한 후 읽습니다. 이 특히 플로피 디스크 드라이브에 대 한 시간이 걸릴 수 있습니다.

## <a name="BKMK_examples"></a>예제

첫 번째 줄 및 보다 큼 다음 줄에서 기호에 현재 날짜 및 시간으로 두 줄 명령 프롬프트를 설정 하려면 다음을 입력 합니다.
```
prompt $d$s$s$t$_$g 
```
프롬프트는 날짜와 시간을 현재 다음과 같이 변경 합니다.
```
Fri 06/01/2007  13:53:28.91
>
```
화살표를 표시 하려면 명령 프롬프트를 설정 하려면 (`-->`), 유형:
```
prompt --$g
```
명령 프롬프트를 기본 설정 (현재 드라이브 및 경로 보다 큼 기호)를 수동으로 변경 하려면 다음을 입력 합니다.
```
prompt $p$g
```

#### <a name="additional-references"></a>추가 참조

[명령줄 구문 키](command-line-syntax-key.md)