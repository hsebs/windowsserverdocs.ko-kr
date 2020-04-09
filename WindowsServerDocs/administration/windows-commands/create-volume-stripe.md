---
title: 볼륨 스트라이프 만들기
description: 두 개 이상의 지정 된 동적 디스크를 사용 하 여 스트라이프 볼륨을 만드는 볼륨 스트라이프 만들기에 대 한 Windows 명령 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 20dce735-5f7c-4f83-a580-d087e2913a00
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8123d2b5852f606398e3be7161ef0341698b7fb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846906"
---
# <a name="create-volume-stripe"></a>볼륨 스트라이프 만들기

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

두 개 이상의 지정 된 동적 디스크를 사용 하 여 스트라이프 볼륨을 만듭니다.  
  
> [!IMPORTANT]  
> Windows Vista의 경우이 DiskPart 명령은 Windows Vista Ultimate, Windows Vista Enterprise 및 Windows Vista Business edition 에서만 사용할 수 있습니다.

## <a name="syntax"></a>구문  
  
```  
create volume stripe [size=<n>] disk=<n>,<n>[,<n>,...] [align=<n>] [noerr]  
```  
  
### <a name="parameters"></a>매개 변수  
  
|         매개 변수         |                                                                                                                            설명                                                                                                                            |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         크기\=<n>         |             메가바이트 단위로 디스크 공간의 크기 \(MB\), 각 디스크에 볼륨이 차지할입니다. 크기를 지정 하는 경우 새 볼륨 남은 공간 가장 작은 디스크 및 각 후속 디스크에 같은 크기의 공간을 차지 합니다.             |
| disk\=<n>,<n>\[<n>,...\] |                                  동적 디스크는 스트라이프 볼륨 생성 됩니다. 스트라이프 볼륨을 만들려면 두 개 이상의 동적 디스크가 필요 합니다. **\=<n>크기** 에 해당 하는 공간의 크기는 각 디스크에 할당 됩니다.                                   |
|        \=<n> 맞춤         | 모든 볼륨 범위에 있는 가장 가까운 맞춤 경계선을 맞춥니다. 일반적으로 하드웨어 RAID 논리 단위 번호와 사용 \(LUN\) 성능을 향상 시키기 위해 배열입니다. *n* 는 킬로바이트의 수는 \(KB\) 가장 가까운 맞춤 경계선을 디스크의 시작 부분에서. |
|           noerr           |                               스크립팅 전용입니다. 오류가 발생 하면 오류가 발생 하지 않은 경우에 따라 명령을 처리 하도록 DiskPart 계속 합니다. 이 매개 변수를 크기는 오류 코드를 수행 합니다.                                |
  
## <a name="remarks"></a>주의  
  
-   볼륨을 만든 후 포커스는 자동으로 새 볼륨으로 이동 합니다.  
  
## <a name="examples"></a><a name=BKMK_examples></a>예와  
1과 2를 디스크에 크기가 1000 메가바이트 스트라이프 볼륨을 만들려면 다음을 입력 합니다.  
  
```  
create volume stripe size=1000 disk=1,2  
```  
  
## <a name="additional-references"></a>추가 참조  
- [명령줄 구문 키](command-line-syntax-key.md)  
  

  

