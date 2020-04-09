---
title: 논리적 파티션 만들기
description: 기존 확장 파티션에 논리 파티션을 만드는 create partition logical에 대 한 Windows 명령 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f59b79a-d690-4d0e-ad38-40df5a0ce38e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b16c161bf12476eee9d3959e5f313fd844ff3519
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847066"
---
# <a name="create-partition-logical"></a>논리적 파티션 만들기

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

기존 확장 파티션의 논리 파티션을 만듭니다. MBR (마스터 부트 레코드) 디스크에만이 명령을 사용할 수 있습니다.

## <a name="syntax"></a>구문  
  
```  
create partition logical [size=<n>] [offset=<n>] [align=<n>] [noerr]  
```  
  
### <a name="parameters"></a>매개 변수  
  
|  매개 변수  |                                                                                                                                                                                                                       설명                                                                                                                                                                                                                        |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  크기\=<n>  |                                                                                                              (메가바이트 단위)는 논리 파티션에의 크기를 지정 \(MB\), 확장 된 파티션을 보다 작은 해야 합니다. 크기를 지정 하는 경우 파티션을 확장 파티션의 가능한 공간이 없을 때까지 계속 합니다.                                                                                                               |
| 오프셋\=<n> | (킬로바이트)에서 오프셋을 지정 \(KB\), 파티션을 만들 때에 있습니다. 오프셋 반올림을 완전히 사용 되는 모든 실린더 크기를 채웁니다. 오프셋이, 파티션은 저장 하는 데 충분히 큰 첫 번째 디스크에에서 배치 됩니다. 파티션은 **size\=<n>** 에 지정 된 수 만큼 길이가 깁니다. 논리 파티션에 대 한 크기를 지정 하면 확장된 파티션의 보다 작아야 합니다. |
| \=<n> 맞춤  |                                                                                     모든 볼륨 또는 파티션 범위에 있는 가장 가까운 맞춤 경계선을 맞춥니다. 일반적으로 하드웨어 RAID 논리 단위 번호와 사용 \(LUN\) 성능을 향상 시키기 위해 배열입니다.  <n>은 디스크의 처음부터 가장 가까운 맞춤 경계로 kb \(KB\) 수입니다.                                                                                      |
|    noerr    |                                                                                                                           스크립팅 전용입니다. 오류가 발생 하면 오류가 발생 하지 않은 경우에 따라 명령을 처리 하도록 DiskPart 계속 합니다. 이 매개 변수를 크기는 오류 코드를 수행 합니다.                                                                                                                           |
  
## <a name="remarks"></a>주의  
  
-   **size** 및 **offset** 매개 변수를 지정 하지 않으면 논리 파티션이 확장 파티션에서 사용 가능한 가장 큰 디스크 범위에 생성 됩니다.  
  
-   파티션이 만들어지면 포커스는 자동으로 새 논리 파티션으로 이동 합니다.  
  
-   이 작업을 수행 하려면 기본 MBR 디스크를 선택 해야 합니다. 사용 된 **디스크 선택** 디스크를 선택 하 고 포커스를 이동 하는 명령입니다.  
  
## <a name="examples"></a><a name=BKMK_examples></a>예와  
선택된 된 디스크의 확장 파티션의 크기를 메가바이트 1000 논리적 파티션을 만들려면 다음을 입력 합니다.  
  
```  
create partition logical size=1000  
```  
  
## <a name="additional-references"></a>추가 참조  
- [명령줄 구문 키](command-line-syntax-key.md)  
  

  

