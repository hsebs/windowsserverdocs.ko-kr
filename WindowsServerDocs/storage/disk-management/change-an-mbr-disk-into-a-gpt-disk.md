---
title: MBR(마스터 부트 레코드)을 GPT(GUID 파티션 테이블) 디스크로 변경
description: MBR(마스터 부트 레코드)을 GPT(GUID 파티션 테이블) 디스크로 변경하는 방법을 설명합니다.
ms.date: 06/07/2019
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 6bd97802fbef342520e92a857a1a53acf3e8d7a3
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2020
ms.locfileid: "71385942"
---
# <a name="convert-an-mbr-disk-into-a-gpt-disk"></a>MBR 디스크를 GPT 디스크로 변환

> **적용 대상:** Windows 10, Windows 8.1, Windows Server(반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

MBR(마스터 부트 레코드) 디스크는 표준 BIOS 파티션 테이블을 사용합니다. GPT(GUID 파티션 테이블) 디스크는 UEFI(Unified Extensible Firmware Interface)를 사용합니다. GPT 디스크의 한 가지 장점은 각 디스크에 4개 이상의 파티션을 보유할 수 있다는 점입니다. 2TB(테라바이트)보다 큰 디스크에 대해서는 GPT가 필요합니다.

디스크에 어떠한 파티션 또는 볼륨도 포함되어 있지 않는 한 디스크를 MBR에서 GPT 파티션 스타일로 변경할 수 있습니다.

> [!NOTE]
> 디스크를 변환하기 전에 모든 데이터를 백업하고 디스크에 액세스하는 모든 프로그램을 닫습니다.

> [!NOTE]
> **Backup Operators** 또는 **Administrators** 그룹의 구성원이어야 이 단계를 완료할 수 있습니다.

## <a name="converting-using-the-windows-interface"></a>Windows 인터페이스를 사용하여 변환

1.  GPT 디스크로 변환하고자 하는 기본 MBR 디스크의 모든 데이터를 백업 또는 이동합니다.

2.  디스크에 파티션 또는 볼륨이 포함된 경우 각각을 마우스 오른쪽 단추로 클릭한 다음, **파티션 삭제** 또는 **볼륨 삭제**를 클릭합니다.

3.  GPT 디스크로 변경하고자 하는 MBR 디스크를 마우스 오른쪽 단추로 클릭한 다음, **GPT 디스크로 변환**을 클릭합니다.

## <a name="converting-using-a-command-line"></a>명령줄을 사용하여 변환

빈 MBR 디스크를 GPT 디스크로 변환하려면 다음 단계를 사용합니다. MBR2GPT.EXE 도구를 사용할 수도 있지만 약간 복잡합니다. 자세한 내용은 [MBR 파티션을 GPT로 변환](https://docs.microsoft.com/windows/deployment/mbr-to-gpt)을 참조하세요.

1.  GPT 디스크로 변환하고자 하는 기본 MBR 디스크의 모든 데이터를 백업 또는 이동합니다.

2.  **명령 프롬프트**를 마우스 오른쪽 단추로 클릭한 다음, **관리자 권한으로 실행**을 선택하여 관리자 권한 명령 프롬프트를 엽니다.

3. `diskpart`을(를) 입력합니다. 디스크에 파티션이나 볼륨이 없는 경우 6단계까지 건너뜁니다.

4.  **DISKPART** 프롬프트에서 `list disk`을(를) 입력합니다. 변환하려는 디스크 번호를 기록해 둡니다.

5.  **DISKPART** 프롬프트에서 `select disk <disknumber>`을(를) 입력합니다.

6.  **DISKPART** 프롬프트에서 `clean`을(를) 입력합니다.

    > [!NOTE]
    > **clean** 명령을 실행하면 디스크의 모든 파티션 또는 볼륨이 삭제됩니다.

7.  **DISKPART** 프롬프트에서 `convert gpt`을(를) 입력합니다.

| Value  | 설명  |
| ----- | ---- |
| **list disk** | 디스크의 목록과 크기, 사용 가능한 공간 크기, 기본 또는 동적 디스크 여부, 디스크의 MBR(마스터 부트 레코드) 또는 GPT(GUID 파티션 테이블) 파티션 스타일 사용 여부 등 정보를 표시합니다. 별표(*)가 표시된 디스크는 포커스가 설정됩니다. |
| **select disk** *disknumber* | 디스크 번호가 *disknumber*인 지정된 디스크를 선택하고 포커스를 설정합니다. |
| **clean** | 포커스가 설정된 디스크에서 모든 파티션 또는 볼륨을 삭제합니다.  |
| **convert gpt**| MBR(마스터 부트 레코드) 파티션 스타일의 비어 있는 기본 디스크를 GPT(GUID 파티션 테이블) 파티션 스타일의 기본 디스크로 변환합니다. |

## <a name="see-also"></a>참고 항목

-   [명령줄 구문 표기법](https://technet.microsoft.com/library/cc742449(v=ws.11).aspx)