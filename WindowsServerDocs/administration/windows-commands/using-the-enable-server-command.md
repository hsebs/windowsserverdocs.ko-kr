---
title: 사용-서버
description: Windows 배포 서비스에 대 한 모든 서비스를 사용 하도록 설정 하는 enable Server에 대 한 참조 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf7bf57c0784fa16719b9f77da50212bca0ef850
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720929"
---
# <a name="enable-server"></a>사용-서버

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Windows 배포 서비스에 대 한 모든 서비스를 활성화 합니다.

## <a name="syntax"></a>구문
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
### <a name="parameters"></a>매개 변수
|매개 변수|설명|
|-------|--------|
|[/ 서버:<Server name>]|서버 이름을 지정합니다. 이 NetBIOS 이름 또는 정규화 된 도메인 이름 (FQDN) 수 있습니다. 서버 이름이 없는 지정 하는 경우 로컬 서버 사용 됩니다.|
## <a name="examples"></a>예
서버에서 서비스를 사용 하려면 다음 중 하나를 실행 합니다.
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>추가 참조
- [명령줄 구문 키](command-line-syntax-key.md)
[안 함](using-the-disable-server-command.md)
-서버 명령을 사용 하 여[get](using-the-get-server-command.md)
서버 명령을 사용 하 여[Initialize](using-the-initialize-server-command.md)

서버 명령을 사용 하 여 다음 명령을 사용[합니다. 서버](subcommand-set-server.md)하위 명령:[시작-](subcommand-start-server.md)
서버 하위 명령: 서버[중지](subcommand-stop-server.md)
[초기화 서버 옵션](the-uninitialize-server-option.md)
