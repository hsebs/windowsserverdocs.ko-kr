---
title: dfsrmig
description: Dfsrmig에 대 한 Windows 명령 항목은 FRS (파일 복제 서비스)에서 분산 파일 시스템 (DFS) 복제로 SYSvol 복제를 마이그레이션하고, 마이그레이션 진행 상황에 대 한 정보를 제공 하 고, 마이그레이션을 지원 하도록 AD DS (active directory 도메인 서비스) 개체를 수정 합니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e1b6a464-6a93-4e66-9969-04f175226d8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d688832169cf216e628fe761f85d708a78103d89
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846166"
---
# <a name="dfsrmig"></a>dfsrmig

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

FRS (파일 복제 서비스)에서 분산 파일 시스템 (DFS) 복제로 SYSvol 복제를 마이그레이션하고, 마이그레이션의 진행 상황에 대 한 정보를 제공 하 고, 마이그레이션을 지원 하기 위해 active directory 도메인 서비스 (AD DS) 개체를 수정 합니다.

이 명령을 사용 하는 방법의 예 참조는 [예제](#BKMK_examples) 이 문서 뒷부분의 섹션입니다.

## <a name="syntax"></a>구문

```
dfsrmig [/SetGlobalState <state> | /GetGlobalState | /GetMigrationState | /createGlobalObjects | 
/deleteRoNtfrsMember [<read_only_domain_controller_name>] | /deleteRoDfsrMember [<read_only_domain_controller_name>] | /?]
```

### <a name="parameters"></a>매개 변수

| 매개 변수 | 설명 | | -----_ | ------ | | /SetGlobalState <state> | 도메인에 대 한 원하는 전역 마이그레이션 상태를 *state*로 지정 된 값에 해당 하는 상태로 설정 합니다.<p>마이그레이션 또는 롤백 프로세스를 진행 하려면 유효한 상태를 순환 하려면이 명령을 사용 합니다. 이 옵션을 사용 하면 시작 하 고 AD DS에 PDC 에뮬레이터에서 전역 마이그레이션 상태를 설정 하 여 마이그레이션 프로세스를 제어할 수 있습니다. PDC 에뮬레이터를 사용할 수 없는 경우이 명령은 실패 합니다.<p>안정 된 상태에만 전역 마이그레이션 상태를 설정할 수 있습니다. 따라서 *상태*에 대 한 유효한 값은 시작 상태에 대해 **0** , 준비 된 상태에 대해 **1** , 리디렉션된 상태에 대해 **2** , 제거 된 상태에 대해 **3** 입니다.<p>제거 된 상태로의 마이그레이션은 취소할 수 없으며, 해당 상태에서 롤백하는 것은 불가능 하므로, SYSvol 복제에 대 한 DFS 복제를 사용 하 여 완전히 committd 인 경우에만 *상태* 에 대해 **3** 값을 사용 합니다. | | /GetGlobalState | PDC 에뮬레이터에서 실행 될 때 AD DS 데이터베이스의 로컬 복사본에서 도메인에 대 한 현재 글로벌 마이그레이션 상태를 검색 합니다.<p>올바른 글로벌 마이그레이션 상태를 설정 하는 확인 하려면이 옵션을 사용 합니다. 안정적인 마이그레이션 상태 전역 마이그레이션 상태를 따라서 될 수 있습니다 결과 하는 **dfsrmig** 명령을 사용 하 여 보고서는 **/GetGlobalState** 옵션으로 설정할 수 상태에 해당는 **/SetGlobalState** 옵션입니다.<p>실행 해야는 **dfsrmig** 명령과 **/GetGlobalState** PDC 에뮬레이터 에서만 옵션입니다. active directory 복제는 글로벌 상태를 도메인의 다른 도메인 컨트롤러에 복제 하지만, PDC 에뮬레이터가 아닌 도메인 컨트롤러에서 **/GetGlobalState** 옵션을 사용 하 여 **dfsrmig** 명령을 실행 하는 경우 복제 대기 시간으로 인해 불일치가 발생할 수 있습니다. PDC 에뮬레이터 아닌 다른 도메인 컨트롤러의 로컬 마이그레이션 상태를 확인 하려면 사용 된 **/GetMigrationState** 옵션을 사용 합니다. | | /GetMigrationState | 도메인의 모든 도메인 컨트롤러에 대 한 현재 로컬 마이그레이션 상태를 검색 하 고 이러한 로컬 상태가 현재 글로벌 마이그레이션 상태와 일치 하는지 여부를 확인 합니다.<p>모든 도메인 컨트롤러가 글로벌 마이그레이션 상태에 도달한 경우를 확인 하려면이 옵션을 사용 합니다. 출력은 **dsfrmig** 명령을 사용 하는 경우는 **/GetMigrationState** 옵션 나타냅니다 여부 현재 전역 상태에 대 한 마이그레이션 완료 되며 현재 글로벌 마이그레이션 상태에 도달 하지 하는 모든 도메인 컨트롤러에 대 한 로컬 마이그레이션 상태를 나열 합니다. 도메인 컨트롤러에 대 한 로컬 마이그레이션 상태는 현재 글로벌 마이그레이션 상태에 도달 하지 하는 도메인 컨트롤러에 대 한 전환 상태를 포함할 수 있습니다. | | /createGlobalObjects | DFS 복제에서 사용 하는 AD DS 전역 개체 및 설정을 만듭니다.<p>정상적인 마이그레이션 프로세스 중에는이 옵션을 사용 하지 않아도 됩니다 .이 옵션은 DFS 복제 서비스가 시작 상태에서 준비 됨 상태로 마이그레이션하는 동안 자동으로 이러한 AD DS 개체 및 설정을 만듭니다. 이 옵션을 사용 하 여 수동으로 다음과 같은 상황에서 이러한 개체 및 설정을 만들려면:<p>-  **마이그레이션하는 동안 새 읽기 전용 도메인 컨트롤러가 승격 됩니다**. DFS 복제 서비스는 시작 상태에서 준비 됨 상태로 마이그레이션하는 동안 DFS 복제에 대 한 AD DS 개체 및 설정을 자동으로 만듭니다. 에 해당 하는 개체는 다음이 전환 후 하지만 제거 상태로 마이그레이션 전에 도메인에 새 읽기 전용 도메인 컨트롤러 승격 됩니다 새로 활성화 된 읽기 전용 도메인 컨트롤러는 AD DS에 복제 및 마이그레이션 일으키는 실패 생성 되지 않습니다.<br />-이 경우 **dfsrmig** 명령을 실행 하 여 **/createGlobalObjects** 옵션을 실행 하면 아직 없는 읽기 전용 도메인 컨트롤러에서 개체를 수동으로 만들 수 있습니다. 이 명령을 실행 개체 및 DFS 복제 서비스에 대 한 설정을 이미 있는 도메인 컨트롤러는 영향을 주지 않습니다.<p>- **DFS 복제 서비스에 대 한 전역 설정이 누락 되었거나 삭제 되었습니다**. 특정 도메인 컨트롤러에 대해 이러한 설정이 누락 된 경우 시작 상태에서 준비 됨 상태로의 마이그레이션은 도메인 컨트롤러에 대 한 전환 준비 상태에서 지연 됩니다. 이 경우 **/createGlobalObjects** 옵션과 함께 **dfsrmig** 명령을 사용 하 여 설정을 수동으로 만들 수 있습니다. **참고:** 때문에 읽기 전용 도메인 컨트롤러에 대 한 DFS 복제 서비스에 대 한 전역 AD DS 설정을 PDC 에뮬레이터에서 만들어지면 이러한 설정은 필요가 복제 된 읽기 전용 도메인 컨트롤러에 PDC 에뮬레이터에서 읽기 전용 도메인 컨트롤러에서 DFS 복제 서비스는 이러한 설정을 사용할 수 있습니다. 활성 i 복제 대기 시간으로 인해이 복제를 수행 하는 데 다소 시간이 걸릴 수 있습니다. | | /deleteRoNtfrsMember [< read_only_domain_controller_name >] | 지정 된 읽기 전용 도메인 컨트롤러에 해당 하는 FRS 복제에 대 한 전역 AD DS 설정을 삭제 하거나 *read_only_domain_controller_name*에 값을 지정 하지 않은 경우 모든 읽기 전용 도메인 컨트롤러에 대 한 frs 복제에 대 한 전역 AD DS 설정을 삭제 합니다.<p>DFS 복제 서비스는 자동으로 이러한 AD DS 설정을 제거 상태로 Redirected 상태에서 마이그레이션하는 동안 삭제 하기 때문에 일반적인 마이그레이션 과정에서이 옵션을 사용할 필요가 없습니다. 읽기 전용 도메인 컨트롤러는 AD DS에서 이러한 설정을 삭제할 수 없으므로 PDC 에뮬레이터는이 작업을 수행 하 고 변경 내용은 active directory 복제에 대 한 적용 가능한 대기 시간 이후에 읽기 전용 도메인 컨트롤러에 복제 됩니다.<p>자동 삭제 읽기 전용 도메인 컨트롤러에 실패 하 고 제거 상태로 Redirected 상태에서 마이그레이션하는 동안 긴 ime에 대 한 읽기 전용 도메인 컨트롤러를 중지 하는 경우에 AD DS 설정을 수동으로 삭제 하려면이 옵션을 사용 합니다. | | /deleteRoDfsrMember [< read_only_domain_controller_name >] | 지정 된 읽기 전용 도메인 컨트롤러에 해당 하는 DFS 복제에 대 한 전역 AD DS 설정을 삭제 하거나 *read_only_domain_controller_name*에 값이 지정 되지 않은 경우 모든 읽기 전용 도메인 컨트롤러에 대 한 DFS 복제에 대 한 전역 AD DS 설정을 삭제 합니다.<p>이 옵션을 사용 하 여 읽기 전용 도메인 컨트롤러에서 자동 삭제가 실패 한 경우에만 AD DS 설정을 수동으로 삭제 하 고, 준비 된 상태에서 시작 상태로 마이그레이션하는 동안 오랜 시간 동안 읽기 전용 도메인 컨트롤러를 정지 합니다. | | /? | 명령 프롬프트에서 도움말을 표시 합니다. 실행 중에 해당 **dfsrmig** 옵션 없이 합니다. |

## <a name="remarks"></a>주의
- DFS 복제 서비스에 대 한 마이그레이션 도구인 dfsrmig는 DFS 복제 서비스와 함께 설치 됩니다.
 새 Windows Server 2008 서버의 경우 컴퓨터를 도메인 컨트롤러로 승격할 때 Dcpromo.exe는 DFS 복제 서비스를 설치 하 고 시작 합니다. 서버를 Windows Server 2003에서 Windows Server 2008로 업그레이드 하는 경우 업그레이드 프로세스에서 DFS 복제 서비스를 설치 하 고 시작 합니다. DFS 복제 서비스를 설치 및 시작 DFS 복제 역할 서비스를 설치할 필요가 없습니다.
- **Dfsrmig** 도구는 windows server 2008 도메인 기능 수준에서 실행 되는 도메인 컨트롤러 에서만 지원 됩니다. FRS에서 DFS 복제로의 SYSvol 마이그레이션은 windows server 2008 도메인 기능 수준에서 작동 하는 도메인 컨트롤러 에서만 가능 하기 때문입니다.
- 실행할 수는 **dfsrmig** 만들거나 AD DS를 조작 하는 작업 하지만 모든 도메인 컨트롤러에서 명령을 개체 (읽기 전용 도메인 컨트롤러)에 없는 읽기 / 쓰기 가능 도메인 컨트롤러에만 허용 됩니다.
- 옵션 없이 **dfsrmig** 를 실행 하면 명령 프롬프트에서 도움말을 표시 합니다.

## <a name="examples"></a><a name=BKMK_examples></a>예와
준비 전역 마이그레이션 상태를 설정 하려면 (**1**)를 마이그레이션 또는 형식 준비 된 상태에서 롤백을 시작 합니다.
 ```
 dfsrmig /SetGlobalState 1
 ```
 전역 마이그레이션 상태를 시작 (**0**)으로 설정 하 고 롤백을 시작 상태로 시작 하려면 다음을 입력 합니다.
 ```
 dfsrmig /SetGlobalState 0
 ```
 전역 마이그레이션 상태를 표시 하려면 다음을 입력 합니다.
 ```
 dfsrmig /GetGlobalState
 ```
 일반적인 출력을 보여 주는이 예제는 **dfsrmig /GetGlobalState** 명령입니다.
 ```
 Current DFSR global state: Prepared 
 Succeeded.
 ```
 모든 도메인 컨트롤러에서 로컬 마이그레이션 상태 전역 마이그레이션 상태 및 로컬 상태 전역 상태가 일치 하지 않는 모든 도메인 컨트롤러에 대 한 로컬 마이그레이션 상태를 일치 하는 여부에 대 한 정보를 표시 하려면 다음을 입력 합니다.
 ```
 dfsrmig /GetMigrationState
 ```
 일반적인 출력을 보여 주는이 예제는 **dfsrmig /GetMigrationState** 모든 도메인 컨트롤러에서 로컬 마이그레이션 상태에는 전역 마이그레이션 상태와 일치 하는 경우 명령입니다.
 ```
 All Domain Controllers have migrated successfully to Global state ( Prepared ).
 Migration has reached a consistent state on all Domain Controllers.
 Succeeded.
 ```
 일반적인 출력을 보여 주는이 예제는 **dfsrmig /GetMigrationState** 일부 도메인 컨트롤러에서 로컬 마이그레이션 상태 전역 마이그레이션 상태를 일치 하지 않을 때 명령입니다.
 ```
  The following Domain Controllers are not in sync with Global state ( Prepared ):
  Domain Controller (Local Migration State)  DC type
  =========
  CONTOSO-DC2 ( start )  ReadOnly DC
  CONTOSO-DC3 ( Preparing )  Writable DC
  Migration has not yet reached a consistent state on all domain controllers
  State information might be stale due to AD latency.
 ```
여기서 해당 설정이 만들어지지 않은 자동으로 마이그레이션하는 동안 도메인 컨트롤러에서 AD DS의 DFS 복제를 사용 하 여 전역 개체 및 설정을 만들거나 이러한 설정이 없는 경우 입력:
```
dfsrmig /createGlobalObjects
```
이러한 설정이 마이그레이션 프로세스에 의해 자동으로 삭제 삭제 되지 않은 경우 contoso-d c 2 라는 읽기 전용 도메인 컨트롤러에 대 한 FRS 복제에 대 한 전역 AD DS 설정을 삭제 하려면 다음을 입력 합니다.
```
dfsrmig /deleteRoNtfrsMember contoso-dc2
```
마이그레이션 프로세스에서 이러한 설정을 자동으로 삭제 되지 않은 경우 모든 읽기 전용 도메인 컨트롤러에 대 한 FRS 복제에 대 한 전역 AD DS 설정을 삭제 하려면 다음을 입력 합니다.
```
dfsrmig /deleteRoNtfrsMember
```
마이그레이션 프로세스에서 이러한 설정을 자동으로 삭제 되지 않은 경우 contoso-d c 2 라는 읽기 전용 도메인 컨트롤러에 대 한 DFS 복제에 대 한 전역 AD DS 설정을 삭제 하려면 다음을 입력 합니다.
```
dfsrmig /deleteRoDfsrMember contoso-dc2
```
마이그레이션 프로세스에서 이러한 설정을 자동으로 삭제 되지 않은 경우 모든 읽기 전용 도메인 컨트롤러에 대 한 DFS 복제에 대 한 전역 AD DS 설정을 삭제 하려면 다음을 입력 합니다.
```
dfsrmig /deleteRoDfsrMember
```
## <a name="additional-references"></a>추가 참조
- [명령줄 구문 키](https://go.microsoft.com/fwlink/?LinkId=122056)

- [SYSvol 마이그레이션 시리즈: 2 부 dfsrmig: SYSvol 마이그레이션 도구](https://go.microsoft.com/fwlink/?LinkID=121757)
