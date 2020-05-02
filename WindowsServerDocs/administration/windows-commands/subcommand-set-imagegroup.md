---
title: 하위 명령 집합-ImageGroup
description: 이미지 그룹의 특성을 변경 하는 하위 명령 ImageGroup에 대 한 참조 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 429a8fee5b0236d264eb421f110219a1bc037368
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721704"
---
# <a name="subcommand-set-imagegroup"></a>하위 명령: 집합 ImageGroup

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

이미지 그룹의 특성을 변경 합니다.

## <a name="syntax"></a>구문
```
wdsutil [Options] /Set-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
### <a name="parameters"></a>매개 변수
|매개 변수|설명|
|-------|--------|
mediaGroup:<Image group name>|이미지 그룹의 이름을 지정합니다.|
|[/ 서버:<Server name>]|서버 이름을 지정합니다. 이 NetBIOS 이름 또는 정규화 된 도메인 이름 (FQDN) 수 있습니다. 지정 하지 않으면 로컬 서버가 사용 됩니다.|
|[/Name:<New image group name>]|이미지 그룹의 새 이름을 지정합니다.|
|[/ 보안:<SDDL>]|보안 설명자 정의 언어 (SDDL) 형식에서 이미지 그룹의 새 보안 설명자를 지정합니다.|
## <a name="examples"></a>예
이미지 그룹에 대 한 이름을 설정 하려면 다음을 입력 합니다.
```
wdsutil /Set-ImageGroumediaGroup:ImageGroup1 /Name:New Image Group Name
```
이미지 그룹에 대 한 다양 한 설정을 지정 하려면 다음을 입력 합니다.
```
wdsutil /verbose /Set-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /Name:New Image Group Name 
/Security:O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)
```
## <a name="additional-references"></a>추가 참조
- [명령줄 구문 키](command-line-syntax-key.md)
[ImageGroup](using-the-add-imagegroup-command.md)
명령을 사용 하 여 ImageGroup 명령을 사용 하 여[AllImageGroups](using-the-get-allimagegroups-command.md)
명령을 사용 하 여[Using the get-ImageGroup Command](using-the-get-imagegroup-command.md)
명령을 사용 하 여[ImageGroup](using-the-remove-imagegroup-command.md) 명령을 사용 합니다.
