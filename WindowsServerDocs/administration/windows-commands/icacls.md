---
title: icacls
description: '\* * * *에 대 한 Windows 명령 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 403edfcc-328a-479d-b641-80c290ccf73e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/21/2018
ms.openlocfilehash: 59d10b9ed681b7e0af120798dde9f200182d67d3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842266"
---
# <a name="icacls"></a>icacls

지정된 파일의 DACL(임의 액세스 제어 목록)을 표시 또는 수정하고 저장한 DACL을 지정된 디렉터리의 파일에 적용합니다.

이 명령을 사용하는 방법의 예는 [예](#examples)를 참조하세요.

## <a name="syntax"></a>구문

```
icacls <FileName> [/grant[:r] <Sid>:<Perm>[...]] [/deny <Sid>:<Perm>[...]] [/remove[:g|:d]] <Sid>[...]] [/t] [/c] [/l] [/q] [/setintegritylevel <Level>:<Policy>[...]]
icacls <Directory> [/substitute <SidOld> <SidNew> [...]] [/restore <ACLfile> [/c] [/l] [/q]]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|\<파일 이름 >|Dacl을 표시 하려는 파일을 지정 합니다.|
|\<Directory >|Dacl을 표시 하려는 디렉터리를 지정 합니다.|
|/t|현재 디렉터리 및 하위 디렉터리에서 지정 된 모든 파일에 작업을 수행합니다.|
|/c|파일 오류 불구 하 고 작업을 계속 합니다. 오류 메시지가 계속 표시 됩니다.|
|/l|대상 및 기호화 된 링크에 대 한 작업을 수행합니다.|
|/q|성공 메시지를 표시 하지 않습니다.|
|[/save \<ACLfile > [/t] [/c] [/l] [/q]]|Dacl에 일치 하는 모든 파일에 대 한 저장 *ACLfile* 나중에 사용할 수 있는 **/복원**합니다.|
|[/setowner \<Username > [/t] [/c] [/l] [/q]]|지정된 된 사용자에 일치 하는 모든 파일의 소유자를 변경합니다.|
|[/findsid \<Sid > [/t] [/c] [/l] [/q]]|지정된 된 보안 식별자 (SID)를 명시적으로 언급 하는 DACL을 포함 하는 일치 하는 모든 파일을 찾습니다.|
|[/ 확인 [/t] [/c] [/l] [/q]]|정식 하지 않거나 길이 ACE (액세스 제어 항목) 수와 일치 하지 않는 Acl 사용 하 여 모든 파일을 찾습니다.|
|[/reset [/t] [/c] [/l] [/q]]|기본값은 대체 Acl 일치 하는 모든 파일에 대 한 Acl을 상속합니다.|
|[/grant [: r] \<Sid >:<Perm>[...]]|사용자 액세스 권한을 지정 하는 권한을 부여 합니다. 사용 권한을 이전에 부여 된 명시적 사용 권한을 바꿉니다.</br>없이 **: r**, 이전에 명시적 사용 권한 부여에 추가 됩니다.|
|[/거부 \<Sid >:<Perm>[...]]|명시적으로 지정 된 사용자 액세스 권한을 거부합니다. 명시적 거부 ACE 명시 된 사용 권한에 대해 추가 되 고 모든 명시적 권한 부여에 동일한 사용 권한이 제거 됩니다.|
|[/remove [: g\|:d]] \<Sid > [...]] /t /c /l /q|DACL에서 지정된 된 SID의 모든 항목을 제거합니다.</br>**: g** 지정 된 SID에 대 한 권한 부여의 모든 항목을 제거 합니다.</br>**: d** 거부 된 권한 지정 된 sid의 모든 항목을 제거 합니다.|
|[/setintegritylevel [(CI) (OI)]\<Level >:<Policy>[...]]|일치 하는 모든 파일에는 무결성 ACE를 명시적으로 추가합니다. *수준* 로 지정 됩니다.</br>-   **L**[ow]</br>-   **M**[e um]</br>-   **H**[igh]</br>ACE 무결성에 대 한 상속 옵션은 수준 전후의 디렉터리에만 적용 됩니다.|
|[/대체 \<SidOld > <SidNew> [...]]|기존 SID를 바꿉니다 (*SidOld*) 한 새 sid (*SidNew*). 필요는 *디렉터리* 매개 변수입니다.|
|/restore \<ACLfile > [/c] [/l] [/q]|저장 된 Dacl 적용 *ACLfile* 지정된 된 디렉터리의 파일에 있습니다. 필요는 *디렉터리* 매개 변수입니다.|
|/inheritancelevel: [e\|d\|r]|상속 수준을 설정 합니다. <br>  **e** -enheritance 사용 <br>**d** -상속을 사용 하지 않도록 설정 하 고 ace를 복사 합니다. <br>**r** -상속 된 모든 ace를 제거 합니다.

## <a name="remarks"></a>주의

-   Sid는 숫자 또는 친숙 한 이름 형식을 사용할 수 있습니다. 숫자 형식을 사용 하는 경우에는 와일드 카드 문자 **&#42;** 를 SID의 시작 부분으로 접사.
-   **icacls** 설명 된 대로 항목 ACE의 정식 순서를 유지 합니다.  
    -   명시적 거부
    -   명시적 권한 부여
    -   상속 된 거부
    -   상속 된 권한 부여
-   *권한* 은 다음 형식 중 하나에 지정 될 수 있는 권한을 마스크:  
    -   단순한 권한 시퀀스:

        **F** (모든 권한)

        **M** (수정 액세스)

        **RX** (읽기 및 실행 권한)

        **R** (읽기 전용 액세스)

        **W** (쓰기 전용 액세스)
    -   특정 권한 괄호 안에 쉼표로 구분 된 목록:

        **D** (삭제)

        **RC** (컨트롤 읽기)

        **WDAC** (DAC 쓰기)

        **WO** (쓰기 소유자)

        **S** (동기화)

        **AS** (시스템 보안 액세스)

        **MA** (최대 허용)

        **GR** (일반 읽기)

        **GW** (일반 쓰기)

        **GE** (일반 실행)

        **GA** (모든 일반)

        **RD** (데이터/목록 디렉터리 읽기)

        **WD** (파일 데이터/추가 쓰기)

        **AD** (추가 데이터/추가 하위 디렉터리)

        **팅** (확장된 특성 읽기)

        **재가동** (확장 된 특성을 작성 합니다.)

        **X** (실행/트래버스)

        **DC** (자식 삭제 됨)

        **RA** (특성 읽기)

        **WA** (특성을 작성 합니다.)
-   권한 상속 하거나 전 *권한* 하 고, 폼에는 디렉터리에만 적용 됩니다.

    **(OI)** : 개체 상속

    **(CI)** : 컨테이너 상속

    **(IO)** : 상속만 해당

    **(NP)** : 전파 되지 않습니다 상속

## <a name="examples"></a>예

모든 파일에 대 한 Dacl는 C:\Windows 디렉터리 및 하위 디렉터리를 ACLFile 파일을 저장 하려면 다음을 입력 합니다.

```
icacls c:\windows\* /save aclfile /t
```

C:\Windows 디렉터리 및 하위 디렉터리에 있는 ACLFile 내의 모든 파일에 대 한 Dacl을 복원 하려면 다음을 입력 합니다.

```
icacls c:\windows\ /restore aclfile
```

사용자에 게 이름이 Test1 인 파일에 대 한 DAC 삭제 및 쓰기 권한을 부여 하려면 다음을 입력 합니다.

```
icacls test1 /grant User1:(d,wdac)
```

이름이 Test2 인 파일에 대 한 SID S-1-1-0 Delete 및 Write DAC 권한으로 정의한 사용자를 부여 하려면 다음을 입력 합니다.

```
icacls test2 /grant *S-1-1-0:(d,wdac)
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)
