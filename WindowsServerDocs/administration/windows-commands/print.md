---
title: print
description: '\* * * *에 대 한 Windows 명령 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa2325d5-a993-4ed3-b996-255165452db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36966d8d3beb032ee0dcee50d9bd5bc0111bf4f5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837376"
---
# <a name="print"></a>print



텍스트 파일을 프린터로 보냅니다.

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
Print [/d:<PrinterName>] [<Drive>:][<Path>]<FileName>[ ...]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|/d:\<PrinterName >|작업을 인쇄 하려는 프린터를 지정 합니다. 로컬로 연결 된 프린터로 인쇄 하려면 프린터가 연결 된 컴퓨터의 포트를 지정 합니다.</br>-병렬 포트의 유효한 값은 LPT1, LPT2 및 LPT3입니다.</br>-직렬 포트에 대 한 유효한 값은 COM1, COM2, COM3 및 COM4입니다.</br>해당 큐 이름을 사용 하 여 네트워크 프린터를 지정할 수도 있습니다 (\\\\*ServerName*\*PrinterName *). 프린터를 지정 하지 않으면 기본적으로 인쇄 작업이 LPT1에 전송 됩니다.|
|\<드라이브 >:|인쇄 하려는 파일이 있는 논리적 또는 물리적 드라이브를 지정 합니다. 인쇄 하려는 파일이 현재 드라이브에 있는 경우에는이 매개 변수가 필요 하지 않습니다.|
|\<경로 >|인쇄 하려는 파일의 위치를 지정 합니다. 인쇄 하려는 파일이 현재 디렉터리에 있는 경우에는이 매개 변수가 필요 하지 않습니다.|
|\<파일 이름 > [...]|필수입니다. 인쇄 하려는 파일을 지정 합니다. 하나의 명령에 여러 파일을 포함할 수 있습니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="remarks"></a>주의

-   파일은 로컬 컴퓨터의 직렬 또는 병렬 포트에 연결 된 프린터로 보낼 경우 백그라운드에서 인쇄할 수 있습니다.
-   명령 프롬프트에서 **모드** 명령을 사용 하 여 여러 구성 작업을 수행할 수 있습니다.

    에 대 한 자세한 내용은 [모드](mode.md) 를 참조 하세요.  
    -   병렬 포트에 연결 된 프린터 구성
    -   직렬 포트에 연결 된 프린터 구성
    -   프린터 상태 표시
    -   코드 페이지 전환에 대 한 프린터 준비

## <a name="examples"></a><a name=BKMK_examples></a>예와

현재 디렉터리에 있는 파일을 로컬 컴퓨터의 LPT2에 연결 된 프린터로 보내려면 다음을 입력 합니다.
```
print /d:lpt2 report.txt
```
C:\Accounting 디렉터리의 Printer1 파일을 CopyRoom 서버 \\의 print \\큐에 보내려면 다음을 입력 합니다.
```
print /d:\\copyroom\printer1 c:\accounting\report.txt 
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)

[인쇄 명령 참조](print-command-reference.md)

[모드](mode.md)