---
title: add
description: 섀도 복사할 볼륨 집합에 볼륨을 추가 하거나 별칭 환경에 별칭을 추가 하는 **추가**에 대 한 Windows 명령 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 47efce7a-86d2-4872-ae31-baa108757afd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9895082cc10223fd08cff6916c20c3af5613e947
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851346"
---
# <a name="add"></a>add

볼륨 섀도 복사 되는 볼륨의 집합에 추가 하거나 별칭 환경에 별칭을 추가 합니다. 하위 없이 사용 하는 경우 **추가** 현재 볼륨 및 별칭을 나열 합니다.

> [!NOTE]
> 섀도 복사본이 만들어질 때까지 별칭 별칭 환경에 추가 되지 않습니다. 사용 하 여 즉시 수행 해야 하는 별칭을 추가 해야 **별칭 추가**합니다.

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
add 
add volume <Volume> [provider <ProviderID>] 
add alias <AliasName> <AliasValue>
```

## <a name="add-subcommands"></a>하위 명령 추가

| 하위 명령 | 설명 |
| ---------- | ----------- |
| 볼륨 | 볼륨의 섀도 복사본을 설정 하려면 되 섀도 복사 되는 볼륨의 집합에 추가 합니다. 참조 [볼륨 추가](add-volume.md) 구문 및 매개 변수입니다. |
| 별칭 | 별칭 환경에 지정 된 이름과 값을 추가합니다. 참조 [추가 별칭](add-alias.md) 구문 및 매개 변수입니다. |
| `/?` | 명령줄에서 도움말을 표시 합니다. |

## <a name="examples"></a><a name=BKMK_examples></a>예와

추가 볼륨 및 현재 환경에 있는 별칭을 표시 하려면 다음을 입력 합니다.

```
add
```

다음과 같은 출력을 섀도 복사 설정 하려면 C 드라이브 추가 되어 있는지를 보여 줍니다.

```
Volume c: alias System1    GUID \\?\Volume{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}\
1 volume in Shadow Copy Set.
No Diskshadow aliases in the environment.
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)