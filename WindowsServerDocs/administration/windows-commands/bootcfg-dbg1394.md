---
title: bootcfg dbg1394
description: 지정 된 운영 체제 항목에 대해 1394 포트 디버깅을 구성 하는 bootcfg dbg1394에 대 한 Windows 명령 항목
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 35724697-90dd-4dbe-85b0-337fbd369dcc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d49e0a39cd021f093ca68bf97963dc35c3b53ad4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848676"
---
# <a name="bootcfg-dbg1394"></a>bootcfg dbg1394

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

지정된 된 운영 체제 항목에 대 한 1394 포트 디버깅을 구성 합니다.

## <a name="syntax"></a>구문
```
bootcfg /dbg1394 {ON | OFF}[/s <computer> [/u <Domain>\<User> /p <Password>]] [/ch <Channel>] /id <OSEntryLineNum>
```
### <a name="parameters"></a>매개 변수

|      매개 변수       |                                                                                                                                           설명                                                                                                                                            |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   {ON & #124; OFF}    | 1394 포트 디버깅에 대 한 값을 지정합니다.<p>-   **ON** -지정 된 <OSEntryLineNum>에/dbg1394 옵션을 추가 하 여 원격 디버깅 지원을 사용 하도록 설정 합니다.<br />-   **OFF** -지정 된 <OSEntryLineNum>에서/dbg1394 옵션을 제거 하 여 원격 디버깅 지원을 사용 하지 않도록 설정 합니다. |
|    /s <computer>     |                                                                                        이름 또는 원격 컴퓨터의 IP 주소를 지정 합니다 (백슬래시를 사용 하지 않습니다). 기본값은 로컬 컴퓨터입니다.                                                                                        |
| /u <Domain>\\<User>  |                                               <User> 또는 <Domain>\\<User>에 지정 된 사용자의 계정 권한으로 명령을 실행 합니다. 기본값은 현재 로그온 된 명령을 실행 하는 컴퓨터에서 사용자의 사용 권한.                                               |
|    /p <Password>     |                                                                                                      에 지정 된 사용자 계정의 암호를 지정 된 **/u** 매개 변수입니다.                                                                                                       |
|     /ch 채널      |                                                           디버깅에 사용할 채널을 지정 합니다. 유효한 값은 1에서 64 사이의 정수입니다. 1394 포트 디버깅을 사용 하지 않도록 설정 하는 경우 **/ch** <Channel> 매개 변수를 사용 하지 마세요.                                                           |
| /id <OSEntryLineNum> |                                  1394 포트 디버깅 옵션 추가 되는 Boot.ini 파일의 [운영 체제] 섹션에 운영 체제 항목 줄 번호를 지정 합니다. [운영 체제] 섹션 헤더 후 첫 번째 줄은 1입니다.                                  |
|          /?          |                                                                                                                               명령 프롬프트에 도움말을 표시합니다.                                                                                                                               |

## <a name="examples"></a><a name=BKMK_examples></a>예와
다음 예제에서는 사용 하는 방법을 보여는 **bootcfg /dbg1394**명령:
```
bootcfg /dbg1394 /id 2 
bootcfg /dbg1394 on /ch 1 /id 3 
bootcfg /dbg1394 edit /ch 8 /id 2 
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```
## <a name="additional-references"></a>추가 참조
- [명령줄 구문 키](command-line-syntax-key.md)
