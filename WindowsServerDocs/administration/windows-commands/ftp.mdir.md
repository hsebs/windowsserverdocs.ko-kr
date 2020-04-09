---
title: ftp mdir
description: '\* * * *에 대 한 Windows 명령 항목'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: afb024d063761f1e817f02fdd7301376dd167846
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842716"
---
# <a name="ftp-mdir"></a>ftp: mdir

>적용 대상: Windows Server(반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

원격 디렉터리에서 파일 및 하위 디렉터리의 디렉터리 목록을 표시 합니다.   
## <a name="syntax"></a>구문  
```  
mdir <remoteFile>[ ] <LocalFile>  
```  
#### <a name="parameters"></a>매개 변수  

|  매개 변수   |                               설명                                |
|--------------|--------------------------------------------------------------------------|
| <remoteFile> |   목록을 보려는 디렉터리 또는 파일을 지정 합니다.   |
| <LocalFile>  | 목록을 저장할 로컬 파일을 지정 합니다. 필수 매개 변수입니다. |

## <a name="remarks"></a>주의  
- **Mdir** 를 사용 하 여 여러 파일을 지정할 수 있습니다.  
- *Remotefile* 지정  
  원격 컴퓨터에서 현재 작업 디렉터리를 사용 하려면 하이픈 ( **-** )을 입력 합니다.  
- *Localfile* 지정  
  화면에 목록을 표시 하려면 하이픈 ( **-** )을 입력 합니다.  
  ## <a name="examples"></a><a name=BKMK_Examples></a>예와  
  화면에 **dir1** 및 **dir2** 의 디렉터리 목록을 표시 합니다.  
  ```  
  mdir dir1 dir2 -  
  ```  
  **Dir1** 및 **dir2** 의 결합 된 디렉터리 목록을 파일 이름 .txt 라는 로컬 파일에 저장 합니다 **.**  
  ```  
  mdir dir1 dir2 dirlist.txt  
  ```  
  ## <a name="additional-references"></a>추가 참조  
- - [명령줄 구문 키](command-line-syntax-key.md)  
