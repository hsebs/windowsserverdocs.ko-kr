---
title: mode
description: '* * * *에 대 한 참조 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b59b04f2-b41d-42df-b5be-19c3721445b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2bd7875687aa112c500a966e0ebbcb5af142eb83
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723952"
---
# <a name="mode"></a>mode



시스템 상태를 표시 하 고, 시스템 설정을 변경 또는 포트 또는 디바이스를 다시 구성 합니다. 매개 변수 없이 사용 하는 경우 **모드** 콘솔 및 사용 가능한 COM 디바이스 제어할 수 있는 모든 특성을 표시 합니다.

사용할 수 있습니다 **모드** 다음 작업을 수행할-각 작업에서 다른 구문을 사용 합니다.
-   [직렬 통신 포트를 구성 하려면](#BKMK_1)
-   [단일 디바이스 또는 모든 디바이스의 상태를 표시 하려면](#BKMK_2)
-   [직렬 통신 포트에 병렬 포트에서 출력을 리디렉션하려면](#BKMK_3)
-   [를 선택 하려면 새로 고침 또는 콘솔에 대 한 코드 페이지 번호를 표시 합니다.](#BKMK_4)
-   [명령 프롬프트 화면 버퍼의 크기를 변경 하려면](#BKMK_5)
-   [키보드 입력 속도 설정 하려면](#BKMK_6)

## <a name="to-configure-a-serial-communications-port"></a><a name=BKMK_1></a>직렬 통신 포트를 구성 하려면

### <a name="syntax"></a>구문

```
mode com<M>[:] [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [to={on|off}] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]
```

#### <a name="parameters"></a>매개 변수

|  매개 변수  |                                                                                                                                                                                     설명                                                                                                                                                                                     |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Com\<M> [:]  |                                                                                                                                                      Async Prncnfg.vbshronous 통신 포트 번호를 지정합니다.                                                                                                                                                      |
|  보드 =\<B>  | 비트 / 초 전송 속도 지정합니다. 다음 표에서에 대 한 유효한 약어 *B* 와 해당 관련된 속도입니다.</br>-   **11** = 110 전송</br>-   **15** = 150 전송</br>-   **30** = 300 전송</br>-   **60** = 600 전송</br>-   **12** = 1200 전송</br>-   **24** = 2400 전송</br>-   **48** = 4800 전송</br>-   **96** = 9600 전송</br>-   **19** = 19200 전송 |
| 패리티 =\<P> |                              시스템 전송 오류를 검사 패리티 비트를 사용 하는 방법을 지정 합니다. 다음 표에서는 *P*의 유효한 값을 보여 줍니다. 기본값은 **e**입니다. 일부 컴퓨터는 값을 지 원하는 **m** 및 **s**합니다.</br>-   **n** = 없음</br>-   **e** = 짝수</br>-   **o** = 홀수</br>-   **m** = 표시</br>-   **s** = 공간                              |
|  data =\<D>  |                                                                                                    문자에서 데이터 비트의 수를 지정합니다. 유효한 값에 대 한 **d** 범위는 5-8입니다. 기본값은 7입니다. 일부 컴퓨터 5 및 6 값을 지원 합니다.                                                                                                     |
|  중지 =\<S>  |                                                                                  끝 문자를 정의 하는 정지 비트의 수를 지정 합니다. 1, 1.5 또는 2입니다. 전송 속도 110 인 경우 기본값은 2입니다. 그렇지 않은 경우 기본값은 1입니다. 일부 컴퓨터에서 값 1.5를 지원합니다.                                                                                   |
|   to = {on    |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|   xon = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|  odsr = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|  octs = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|   dtr = {on   |                                                                                                                                                                                         끄기                                                                                                                                                                                         |
|   rts = {on   |                                                                                                                                                                                         끄기                                                                                                                                                                                         |
|  idsr = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|     /?      |                                                                                                                                                                        명령 프롬프트에 도움말을 표시합니다.                                                                                                                                                                         |

## <a name="to-display-the-status-of-all-devices-or-of-a-single-device"></a><a name=BKMK_2></a>단일 디바이스 또는 모든 디바이스의 상태를 표시 하려면

### <a name="syntax"></a>구문

```
mode [<Device>] [/status]
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<장치>|상태를 표시 하려는 디바이스의 이름을 지정 합니다.|
|/status|리디렉션된 모든 병렬 프린터의 상태를 요청 합니다. 로 간략하게 작성할 수는 **/status** 명령줄 옵션을 **/sta**합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

### <a name="remarks"></a>설명

매개 변수 없이 사용 하는 경우 **모드** 시스템에 설치 된 모든 디바이스의 상태를 표시 합니다.

## <a name="to-redirect-output-from-a-parallel-port-to-a-serial-communications-port"></a><a name=BKMK_3></a>직렬 통신 포트에 병렬 포트에서 출력을 리디렉션하려면

### <a name="syntax"></a>구문

```
mode lpt<N>[:]=com<M>[:]
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|lpt\<N> [:]|필수 사항입니다. 병렬 포트를 지정합니다. 유효한 값에 대 한 *N* 범위는 1-3입니다.|
|com\<M> [:]|필수 사항입니다. 직렬 포트를 지정합니다. 유효한 값에 대 한 *M* 범위는 1 ~ 4입니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

### <a name="remarks"></a>설명

인쇄를 리디렉션할 Administrators 그룹의 구성원 이어야 합니다.

### <a name="examples"></a>예

병렬 프린터 출력을 직렬 프린터로 보낼 수 있도록 시스템을 설정 하려면 사용 해야는 **모드** 명령을 두 번입니다. 처음으로 사용 하 여 **모드** 직렬 포트를 구성 합니다. 두 번 사용 하 여 **모드** 병렬 프린터 출력의 첫 번째에서 지정 된 직렬 포트를 리디렉션하려면 **모드** 명령입니다.

예를 들어, 4, 800 보드 짝수 패리티 직렬 프린터가 작동 하는 경우 COM1 포트 (컴퓨터에 첫 번째 직렬 연결)에 연결 되어 입력.
```
mode com1 48,e,,,b
mode lpt1=com1
```
COM1, l p t 1에서 병렬 프린터 출력을 리디렉션할 경우 l p t 1을 사용 하 여 파일을 인쇄 하려면 않겠다고 결정 한 다음, 파일을 인쇄 하기 전에 다음 명령을 입력 합니다.
```
mode lpt1
```
이 명령은 c o m 1에 p t 1에서 파일을 리디렉션할 수 없습니다.

## <a name="to-select-refresh-or-display-the-numbers-of-the-code-pages-for-the-console"></a><a name=BKMK_4></a>를 선택 하려면 새로 고침 또는 콘솔에 대 한 코드 페이지 번호를 표시 합니다.

### <a name="syntax"></a>구문

```
mode <Device> codepage select=<YYY>
mode <Device> codepage [/status]
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<장치>|필수 사항입니다. 코드 페이지를 선택 하려는 디바이스를 지정 합니다. 디바이스에만 유효한 이름인 CON 합니다.|
|코드 페이지 선택 =|필수 사항입니다. 지정된 된 디바이스를 사용 하는 코드 페이지를 지정 합니다. **코드 페이지** 의 약어를 **cp** **sel**으로 **선택할** 수 있습니다.|
|\<YYY>|필수 사항입니다. 선택 하는 코드 페이지의 수를 지정 합니다. 다음 목록에 표시 된 각 코드 지원 되는 페이지와 국가/지역 또는 언어입니다.</br>437: United States</br>850: 다국어 (라틴어 I)</br>852: 슬라브어 (라틴어 II)</br>855: 키릴 자모 (러시아어)</br>857: 터키어</br>860: 포르투갈어</br>861: 아이슬란드어</br>863: 캐나다-프랑스어</br>865: 북유럽어</br>866: 러시아어</br>869: 현대 그리스어|
|codepage|필수 사항입니다. 표시 된 코드의 숫자 페이지입니다 (있는 경우) 지정된 된 디바이스에 대해 선택한.|
|/status|지정된 된 디바이스에 대해 선택한 현재 코드 페이지의 번호를 표시 합니다. 축약할 수 **/status** 에 **/sta**합니다. 지정 하는 여부 **/status**, **모드 코드 페이지** 의 지정된 된 디바이스에 대해 선택한 코드 페이지 번호를 표시 합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="to-change-the-size-of-the-command-prompt-screen-buffer"></a><a name=BKMK_5></a>명령 프롬프트 화면 버퍼의 크기를 변경 하려면

### <a name="syntax"></a>구문

```
mode con[:] [cols=<C>] [lines=<N>]
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|con [:]|필수 사항입니다. 명령 프롬프트 창에 변경 내용을 적용 된다는 것을 나타냅니다.|
|cols =\<C>|명령 프롬프트 화면 버퍼에서 열 수를 지정합니다.|
|줄 =\<N>|명령 프롬프트 화면 버퍼에서 줄의 수를 지정합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="to-set-the-keyboard-typematic-rate"></a><a name=BKMK_6></a>키보드 입력 속도 설정 하려면

### <a name="syntax"></a>구문

```
mode con[:] [rate=<R> delay=<D>]
```

#### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|con [:]|필수 사항입니다. 키보드를 참조 합니다.|
|rate =\<R>|키를 누르고 있을 때 화면에 문자가 반복 되는 속도 지정 합니다.|
|delay =\<D>|키를 눌러 문자 출력 되풀이 전에 키를 누른 후에 걸리는 시간을 지정 합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

### <a name="remarks"></a>설명

- 입력 속도 해당 문자에 대 한 키를 누르고 있을 때 문자 반복 하는 속도입니다. 입력 속도 두 가지 구성 요소, 속도 및 지연 합니다. 일부 키보드에는이 명령을 인식 하지 못합니다.
- 사용 하 여 **속도 =**<em>R</em>

  유효한 값은 1부터 32입니다. 이러한 값은 초당 약 2-30 자가 하입니다. 기본값은 IBM AT 호환 키보드에 대 한 20 및 21 IBM PS/2 호환 키보드에 대 한 속도 설정 하는 경우 지연을 설정 해야 합니다.
- **Delay**=*D* 사용

  유효한 값에 대 한 *D* 는 1, 2, 3 및 4 (0.25, 나타내는 0.50, 0.75, 1 초)입니다. 기본값은 2입니다. 지연 시간을 설정 하는 경우 속도 설정 해야 합니다.

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)