---
title: 권한 부여 항목에는 주 서버는 동일한 신뢰 그룹에 속하지 않는 가상 컴퓨터에 대 한 고유한 신뢰 그룹 이름을 사용 해야 합니다.
description: 이 모범 사례 분석기 규칙에 대 한 텍스트의 온라인 버전입니다.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 8827a3a7-9f3c-4f51-826a-8e2ec43e01df
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 22e1a3bdeb40c5440862b4931dda344756cc34a5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857816"
---
# <a name="authorization-entries-should-have-distinct-trust-group-names-for-primary-servers-with-virtual-machines-that-are-not-part-of-the-same-trust-group"></a>권한 부여 항목에는 주 서버는 동일한 신뢰 그룹에 속하지 않는 가상 컴퓨터에 대 한 고유한 신뢰 그룹 이름을 사용 해야 합니다.

>적용 대상: Windows Server 2016

모범 사례 분석기 및 검사에 대한 자세한 내용은 [모범 사례 분석기 검사 실행 및 검사 결과 관리](https://go.microsoft.com/fwlink/p/?LinkID=223177)를 참조하세요.  
  
|속성|세부 정보|  
|-|-|  
|**운영 체제**|Windows Server 2016|  
|**제품/기능**|Hyper-V|  
|**등급**|경고|  
|**범주**|구성|  
  
다음 섹션에서는 기울임꼴이이 문제에 대 한 모범 사례 분석기 도구에 표시 되는 UI 텍스트를 나타냅니다.  
  
## <a name="issue"></a>**문제**  
*서버는 가상 머신과 동일한 복제 태그와 연결 된 권한 부여 목록의 모든 서버에서 복제본 가상 머신에 대 한 복제 요청을 허용 합니다.*  
  
## <a name="impact"></a>**식**  
*다른 권한 부여 항목에 속한 주 서버에서 복제를 허용 하는 가상 컴퓨터의 개인 정보 및 보안에 문제가 있을 수 있습니다. 이는 권한 부여 항목의 \<목록과 같은 권한 부여 항목에 영향을 줍니다 >*  
  
## <a name="resolution"></a>**해결 방법**  
*동일한 보안 그룹에 속하지 않은 가상 컴퓨터가 있는 주 서버에 대 한 권한 부여 항목에서 다른 태그를 사용 합니다. Hyper-v 설정을 수정 하 여 복제 태그를 구성 합니다.*  
  


