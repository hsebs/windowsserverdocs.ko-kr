---
title: autoconv
description: 파일 할당 테이블 (Fat) 및 Fat32 볼륨을 NTFS 파일 시스템으로 변환 하는 autoconv command에 대 한 참조 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ea8f55270435c6632be2e527569b4a4b4ca81136
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718780"
---
# <a name="autoconv"></a>autoconv

> 적용 대상: Windows Server (반기 채널), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

파일 할당 테이블 (Fat) 및 Fat32 볼륨을 NTFS 파일 시스템으로 변환 하 고, 기존 파일 및 디렉터리는 **autochk** 를 실행 한 후에도 그대로 유지 됩니다. NTFS 파일 시스템으로 변환 된 볼륨은 Fat 또는 Fat32로 다시 변환할 수 없습니다.

> [!IMPORTANT]
> 명령줄에서 **autoconv** 를 실행할 수 없습니다. 이는 **convert.exe**를 통해 설정 되는 경우 시작할 때만 실행할 수 있습니다.

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)

- [autochk 명령](autochk.md)

- [convert 명령](convert.md)
