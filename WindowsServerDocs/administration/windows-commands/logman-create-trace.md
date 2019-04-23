---
title: logman 추적 만들기
description: '에 대 한 Windows 명령을 항목 * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b4dfecd-6f56-4c51-b622-c2054b4aabd7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 065c5bfc9278d4e7deef453ee8bd3e20296d3a56
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832284"
---
# <a name="logman-create-trace"></a>logman 추적 만들기

>적용 대상: Windows Server (반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

이벤트 추적 데이터 수집기를 만듭니다.  
  
## <a name="syntax"></a>구문  
```  
logman create trace <[-n] <name>> [options]  
```  
## <a name="parameters"></a>매개 변수  
|매개 변수|설명|  
|-------|--------|  
|/?|도움말 상황에 맞는 표시 합니다.|  
|-s <computer name>|지정된 된 원격 컴퓨터에서 명령을 수행 합니다.|  
|-config <value>|명령 옵션을 포함 하는 설정 파일을 지정 합니다.|  
|-ets|이벤트 추적 세션 명령을 저장 하거나 예약 하지 않고 직접 보냅니다.|  
|[-n] <name>|대상 개체의 이름입니다.|  
|-f < bin & #124, bincirc & #124, csv 및 #124; tsv & #124, sql >|데이터 수집기에 대 한 로그 형식을 지정합니다.|  
|-[-u < 사용자 [password] >|사용자 계정으로 실행을 지정합니다. 입력 한 * 암호에 대 한 프롬프트를 생성 하는 암호에 대 한 합니다. 암호 프롬프트에서 입력할 때 암호 표시 되지 않습니다.|  
|-m < [시작] [stop] [[시작] [stop] [...]] >|수동 시작 변경 하거나 예약된 된 시작 또는 끝 시간 대신 중지 합니다.|  
|-rf < [[hh:] mm:] ss >|지정 된 기간에 대 한 데이터 수집기를 실행 합니다.|  
|-b < M/d/yyyy h:mm: ss [AM (& a) #124; PM] >|지정된 된 시간에 데이터 수집을 시작 합니다.|  
|-e < M/d/yyyy h:mm: ss [AM (& a) #124; PM] >|지정된 된 시간에 대 한 데이터 수집을 종료 합니다.|  
|-o < 경로 & #124; dsn! 로그 >|SQL 데이터베이스에 출력 로그 파일 또는 DSN 및 로그 설정 이름을 지정 합니다.|  
|-[-]r|지정 된 시작 및 종료 시간에 매일 데이터 수집기를 반복 합니다.|  
|-[-]a|기존 로그 파일을 추가 합니다.|  
|-[-] ow|기존 로그 파일을 덮어씁니다.|  
|-[-v < nnnnnn & #124; mmddhhmm >|파일 버전 정보를 로그 파일 이름 끝에 연결 합니다.|  
|-[-]rc <task>|지정 된 명령을 실행 될 때마다 로그가 닫힙니다.|  
|-[-] 최대 <value>|최대 로그 파일 크기 (mb) 또는 SQL 로그에 대 한 레코드의 최대 수입니다.|  
|-[-] cnf < [[hh:] mm:] ss >|시간을 지정 하면 지정 된 시간이 경과 하는 경우 새 파일을 만듭니다. 시간을 지정 하지 않으면, 최대 크기를 초과 하는 경우 새 파일을 만듭니다.|  
|-y|메시지를 표시 하지 않고 모든 질문에 예로 답변 합니다.|  
|-ct < 성능 & #124, 시스템 및 #124, 주기 >|이벤트 추적 세션 클록 유형을 지정합니다.|  
|-ln < logger_name >|이벤트 추적 세션에 대해로 거 이름을 지정합니다.|  
|ft < [[hh:] mm:] ss >|이벤트 추적 세션의 플러시 타이머를 지정합니다.|  
|-[-p < 공급자 [플래그 [수준]] >|사용할 수 있도록 단일 이벤트 추적 공급자를 지정 합니다.|  
|-pf <filename>|사용할 수 있도록 여러 이벤트 추적 공급자를 나열 하는 파일을 지정 합니다. 파일에는 줄당 하나의 공급자를 포함 하는 텍스트 파일 이어야 합니다.|  
|-[-] rt|실시간 모드에서 이벤트 추적 세션을 실행 합니다.|  
|-[-] ul|사용자 모드에서 이벤트 추적 세션을 실행 합니다.|  
|-bs <value>|이벤트 추적 세션 버퍼 크기 (kb)를 지정 합니다.|  
|-nb <min max>|이벤트 추적 세션 버퍼의 수를 지정합니다.|  
|-< globalsequence & #124 localsequence & #124; pagedmemory > 모드|이벤트 추적 세션으로 거 모드를 지정합니다.<br /><br />**Globalsequence** 이벤트 추적 프로그램 받는 모든 이벤트는 추적에 관계 없이 세션 이벤트를 수신 하는 시퀀스 번호를 추가 하도록 지정 합니다.<br /><br />**Localsequence** 추가 하도록 지정 된 이벤트는 특정 추적 세션에서 수신 된 이벤트에 대 한 시퀀스 번호입니다. 경우는 **localsequence** 옵션을 사용 하는 경우 중복 시퀀스 번호가 모든 세션에 걸쳐 있을 수 있지만 각 추적 세션 내에서 설치 됩니다.<br /><br />**Pagedmemory** 이벤트 추적 프로그램의 기본 메모리 비페이징 풀 보다는 페이징된 메모리 버퍼 할당에 대 한 사용을 지정 합니다.|  
## <a name="remarks"></a>설명  
[-] 나열 되는 위치는 추가 된-옵션을 부정 합니다.  
## <a name="BKMK_examples"></a>예제  
다음 예제에서는 이벤트 추적 데이터 수집기의 크기 보다 작은 16 비트 및 256 개 이하의 버퍼 없음, 각 버퍼 64 kb를 사용 하 여 trace_log 라는 만들고 위치 c:\logfile에 대 한 결과 출력 합니다.  
```  
logman create trace trace_log -nb 16 256 -bs 64 -o c:\logfile  
```  
#### <a name="additional-references"></a>추가 참조  
[logman](logman.md)  