---
title: DriverGroup 복사
description: 필터, 드라이버 패키지 및 사용/사용 안 함 상태를 포함 하 여 서버의 기존 드라이버 그룹을 복제 하는 복사 DriverGroup에 대 한 참조 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0aaf6fa5-8b5b-4a1e-ae9b-8b5c6d89f571
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dc157e9ef6d07a45efe2a19221fb3a046b2f65c1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721009"
---
# <a name="copy-drivergroup"></a>DriverGroup 복사

기존 드라이버 그룹 필터, 드라이버 패키지 및 사용/사용 안 함 상태를 포함 하 여 서버에 복제 합니다.

## <a name="syntax"></a>구문

```
WDSUTIL /Copy-DriverGroup [/Server:<Server name>] /DriverGroup:<Source Group Name> /GroupName:<New Group Name>
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|[/Server:\<서버 이름>]|서버 이름을 지정합니다. 이 NetBIOS 이름이 나 FQDN 수 있습니다. 서버 이름을 지정 하지, 로컬 서버가 사용 됩니다.|
|/DriverGroup:\<원본 그룹 이름>|원본 드라이버 그룹의 이름을 지정합니다.|
|/GroupName:\<새 그룹 이름>|새 드라이버 그룹의 이름을 지정합니다.|

## <a name="examples"></a>예

드라이버 그룹을 복사 하려면 다음 중 하나를 입력 합니다.
```
WDSUTIL /Copy-DriverGroup /Server:MyWdsServer /DriverGroup:PrinterDrivers /GroupName:X86PrinterDrivers
```
```
WDSUTIL /Copy-DriverGroup /DriverGroup:PrinterDrivers /GroupName:ColorPrinterDrivers
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)