---
title: 하위 명령 시작-네임 스페이스
description: 예약 된 캐스트 네임 스페이스를 시작 하는 하위 명령 시작-네임 스페이스에 대 한 참조 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2dd1c11e-6ab7-4129-9e3a-3f80e0ba59c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1562fcb6c61533fcc9994e9011bf7d61154c06f7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721664"
---
# <a name="subcommand-start-namespace"></a>하위 명령: 시작-네임 스페이스

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

예약 된 캐스트 네임 스페이스를 시작 합니다.

## <a name="syntax"></a>구문
```
wdsutil /start-Namespace /Namespace:<Namespace name[/Server:<Server name>]
```
### <a name="parameters"></a>매개 변수

|          매개 변수          |                                                                                                                                                                                             설명                                                                                                                                                                                             |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Namespace: <네임 스페이스 이름| 네임스페이스의 이름을 지정합니다. Note 이름, 이것이 하 고 고유 해야 합니다.<p>-   **배포 서버**: 네임 스페이스 이름에 대 한 구문은/Namspace: WDS<Image group>/<Image name>/<Index>:입니다. 예를 들어: **WDS:ImageGroup1/install.wim/1**<br />-   **전송 서버**:이 이름은 서버에서 만들 때 네임 스페이스에 지정 된 이름과 일치 해야 합니다. |
|   [/ 서버:<Server name>]   |                                                                                                           서버 이름을 지정합니다. 이 NetBIOS 이름 또는 정규화 된 도메인 이름 (FQDN) 수 있습니다. 서버 이름이 없는 지정 하는 경우 로컬 서버 사용 됩니다.                                                                                                           |

## <a name="examples"></a>예
네임 스페이스를 시작 하려면 다음 중 하나를 입력 합니다.
```
wdsutil /start-Namespace /Namespace:Custom Auto 1
wdsutil /start-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1
```
## <a name="additional-references"></a>추가 참조
- [명령줄 구문 키](command-line-syntax-key.md)
를 사용 하 여[get allnamespaces](using-the-get-allnamespaces-command.md)
명령을 사용 하 여[새 네임](using-the-new-namespace-command.md)
스페이스 명령을 사용 하 여[제거 네임 스페이스](using-the-remove-namespace-command.md) 명령을 사용 하 여
