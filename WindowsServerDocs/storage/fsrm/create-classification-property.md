---
title: 분류 속성 만들기
description: 이 문서에서는 특정 폴더 또는 볼륨 내 파일에 값을 할당하는 데 사용되는 분류 속성에 대해 설명합니다.
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: d330f896c71cced8e97701af2c1008b3531e065d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394220"
---
# <a name="create-a-classification-property"></a>분류 속성 만들기

> 적용 대상: Windows Server (반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

분류 속성은 특정 폴더 또는 볼륨 내 파일에 값을 할당하는 데 사용됩니다. 필요에 따라 선택할 수 있는 많은 속성 유형이 있습니다. 다음 표는 사용 가능한 속성 유형을 정의합니다.

|속성 | 설명 |
| --- | --- |
| 예/아니요 | **예** 또는 **아니요**가 될 수 있는 부울 속성입니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서 **아니요** 값은 **예**로 재정의됩니다. |
| 날짜-시간 | 간단한 날짜/시간 속성입니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서, 충돌하는 값은 재분류를 방지합니다. |
| Number | 간단한 숫자 속성입니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서, 충돌하는 값은 재분류를 방지합니다. |
| 순서가 지정된 목록 | 고정된 값의 목록입니다. 한 번에 하나의 값만 속성에 할당될 수 있습니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서 목록에서 가장 큰 값이 사용됩니다. |
| 문자열 | 간단한 문자열 속성입니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서, 충돌하는 값은 재분류를 방지합니다. |
| 다중 선택 | 속성에 할당할 수 있는 값 목록입니다. 한 번에 하나 이상의 값을 속성에 할당할 수 있습니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서 목록의 각 값이 사용됩니다. |
| 다중 문자열 | 속성에 할당할 수 있는 문자열 목록입니다. 한 번에 하나 이상의 값을 속성에 할당할 수 있습니다. 분류하는 동안 여러 값을 결합할 때나 파일 콘텐츠에서 목록의 각 값이 사용됩니다. |

<br />

다음 절차는 분류 속성을 만드는 과정을 안내합니다.

## <a name="to-create-a-classification-property"></a>분류 속성을 만들려면

1.  **분류 관리**에서 **분류 속성** 노드를 클릭합니다.

2.  마우스 오른쪽 단추로 **분류 속성**을 클릭하고 **속성 만들기**를 클릭하거나 **작업** 창에서 **속성 만들기**를 선택합니다. 이렇게 하면 **분류 속성 정의** 대화 상자가 열립니다.

3.  **속성 이름** 입력란에 속성의 이름을 입력합니다.

4.  **설명** 텍스트 상자에 속성에 대한 선택적인 설명을 입력합니다.

5.  **속성 유형** 드롭다운 메뉴의 목록에서 속성 유형을 선택합니다.

6.  **확인**을 클릭합니다.

## <a name="see-also"></a>참조

-   [자동 분류 규칙 만들기](create-automatic-classification-rule.md)
-   [분류 관리](classification-management.md)