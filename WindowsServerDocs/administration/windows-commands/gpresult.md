---
title: gpresult
description: '\* * * *에 대 한 Windows 명령 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dfaa3adf-2c83-486c-86d6-23f93c5c883c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 480599a4040ab1fdcc3842cdb0eaa8c35afa873c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842466"
---
# <a name="gpresult"></a>gpresult

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

원격 사용자 및 컴퓨터에 대 한 설정의 RSoP (정책 결과) 정보를 표시합니다.
방화벽을 통해 원격으로 대상된 컴퓨터에 대 한 RSoP 보고를 사용 하려면 포트에서 인바운드 네트워크 트래픽을 허용 하는 방화벽 규칙이 있어야 합니다.

## <a name="syntax"></a>구문

```
gpresult [/s <system> [/u <USERNAME> [/p [<PASSWOrd>]]]] [/user [<TARGETDOMAIN>\]<TARGETUSER>] [/scope {user | computer}] {/r | /v | /z | [/x | /h] <FILENAME> [/f] | /?}
```

### <a name="parameters"></a>매개 변수

> [!NOTE]
> 사용 하는 경우를 제외 하 고 **/?** , 중 하나는 출력 옵션을 포함 해야 **/r**, **/v**, **/z**, **/x**, 또는 **/h**합니다.

|                매개 변수                 |                                                                                                     설명                                                                                                      |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              /s \<시스템\>               |                                                  이름 또는 원격 컴퓨터의 IP 주소를 지정합니다. 백슬래시를 사용 하지 마십시오. 기본값은 로컬 컴퓨터입니다.                                                   |
|             /u \<사용자 이름\>              |                                지정된 된 사용자의 자격 증명을 사용 하 여 명령을 실행 합니다. 기본 사용자는 사용자가 명령을 실행 하는 컴퓨터에 로그온입니다.                                 |
|            /p [\<암호\>]             |            제공 되는 사용자 계정의 암호를 지정 된 **/u** 매개 변수. 경우 **/p** 를 생략 하면 **gpresult** 암호를 묻는 메시지를 표시 합니다. **/p** 함께 사용할 수 없습니다 **/x** 또는 **/h**합니다.            |
| /user [\<TARGETDOMAIN\>\\]\<TARGETDOMAIN\> |                                                                            RSoP 데이터 표시 하는 원격 사용자를 지정 합니다.                                                                             |
|      {사용자 & #124; 컴퓨터} / 범위       |                                사용자 또는 컴퓨터에 대 한 RSoP 데이터를 표시합니다. 경우 **/범위** 를 생략 하면 **gpresult** 사용자와 컴퓨터 모두에 대 한 RSoP 데이터를 표시 합니다.                                 |
|        [/x &#124; /h] <FILENAME>         | XML에서 보고서를 저장 ( **/x**) 또는 HTML ( **/h**) 위치에서 지정 된 파일 이름을 사용 하 여 형식은 *FILENAME* 매개 변수입니다. 함께 사용할 수 없습니다 **/u**, **/p**, **/r**, **/v**, 또는 **/z**합니다. |
|                    /f                    |                                                           **gpresult** 가 **/x** 또는 **/h** 옵션에 지정 된 파일 이름을 덮어쓰도록 합니다.                                                           |
|                    /r                    |                                                                                             RSoP 요약 데이터를 표시합니다.                                                                                              |
|                    /v                    |                                                    자세한 정책 정보를 표시합니다. 1의 우선 순위가 적용 된 자세한 설정이 포함 됩니다.                                                    |
|                    /z                    |                                     그룹 정책에 대 한 사용 가능한 모든 정보를 표시합니다. 이 1 및 더 높은 우선 순위가 적용 되는 자세한 설정이 포함 됩니다.                                      |
|                    /?                    |                                                                                         명령 프롬프트에 도움말을 표시합니다.                                                                                         |

## <a name="remarks"></a>주의
- 그룹 정책은를 정의 하 고 조직에서 사용자 및 컴퓨터에 대 한 프로그램, 네트워크 리소스 및 운영 체제가 작동 하는 방법을 제어 하는 주요 관리 도구입니다. Active directory 환경에서 그룹 정책는 사이트, 도메인 또는 조직 구성 단위의 구성원 자격에 따라 사용자 또는 컴퓨터에 적용 됩니다.
- 모든 컴퓨터 또는 사용자에 게 겹치는 정책 설정을 적용할 수, 있으므로 사용자가 로그온 할 때 그룹 정책 기능 정책 설정의 결과 집합을 생성 합니다. **gpresult** 사용자가 로그온 할 때 지정 된 사용자에 대해 컴퓨터에 적용 된 정책 설정의 결과 집합을 표시 합니다.
- 때문에 **/v** 및 **/z** 많은 생성의 정보를 유용 텍스트 파일에 출력을 리디렉션할 수 (예를 들어 **gpresult/z > policy.txt**).
- **gpresult** 명령은 Windows Server 2012, Windows Server 2008 R2, Windows server 2008, Windows 8, Windows 7 및 Windows Vista에서 사용할 수 있습니다.
  ## <a name="examples"></a>예
  다음 예에서는 원격 사용자에 대 한 RSoP 데이터를 검색 **targetusername** 컴퓨터의 **srvmain**, 만 사용자에 대 한 RSoP 데이터를 표시 합니다. 명령은 사용자 **maindom\hiropln**의 자격 증명을 사용 하 여 실행 되 고 <strong>p@ssW23</strong> 은 해당 사용자의 암호로 입력 됩니다.

  ```
  gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /user targetusername /scope user /r
  ```
  
다음 예제에서는 원격 사용자에 대 한 그룹 정책에 대 한 사용 가능한 모든 정보를 저장 **targetusername** 컴퓨터의 **srvmain** 라는 파일에 **policy.txt**합니다. 데이터가 없는 컴퓨터에 대 한 포함 되어 있습니다. 명령은 사용자 **maindom\hiropln**의 자격 증명을 사용 하 여 실행 되 고 <strong>p@ssW23</strong> 은 해당 사용자의 암호로 입력 됩니다.

  ```
  gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /user targetusername /z > policy.txt
  ```
  
다음 예제에서는 컴퓨터에 대 한 RSoP 데이터를 표시 **srvmain** 및 로그온 한 사용자. 데이터는 사용자와 컴퓨터 모두에 대 한 포함 됩니다. 명령은 사용자 **maindom\hiropln**의 자격 증명을 사용 하 여 실행 되 고 <strong>p@ssW23</strong> 은 해당 사용자의 암호로 입력 됩니다.

  ```
  gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /r
  ```
  
## <a name="additional-references"></a>추가 참조
- [그룹 정책 TechCenter](https://go.microsoft.com/fwlink/?LinkID=145531)

- - [명령줄 구문 키](command-line-syntax-key.md)
