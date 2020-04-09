---
title: 가상 컴퓨터는 SR-IOV를 사용 하도록 구성 된 경우 가상 함수 드라이버 올바르게 작동 하는지 확인 하십시오.
description: 이 모범 사례 분석기 규칙에 대 한 텍스트의 온라인 버전입니다.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: d21e4b93-29bf-423a-a635-71c6d48dc49e
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 282187d4d5a1243a14c3a0bdaa3088fe1f134bef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861926"
---
# <a name="ensure-that-the-virtual-function-driver-operates-correctly-when-a-virtual-machine-is-configured-to-use-sr-iov"></a>가상 컴퓨터는 SR-IOV를 사용 하도록 구성 된 경우 가상 함수 드라이버 올바르게 작동 하는지 확인 하십시오.

>적용 대상: Windows Server 2016

모범 사례 분석기 및 검사에 대한 자세한 내용은 [모범 사례 분석기 검사 실행 및 검사 결과 관리](https://go.microsoft.com/fwlink/p/?LinkID=223177)를 참조하세요.  
  
|속성|세부 정보|  
|-|-|  
|**운영 체제**|Windows Server 2016|  
|**제품/기능**|Hyper-V|  
|**등급**|경고|  
|**범주**|구성|  
  
다음 섹션에서는 기울임꼴이이 문제에 대 한 모범 사례 분석기 도구에 표시 되는 UI 텍스트를 나타냅니다.  
  
## <a name="issue"></a>문제  
*가상 함수 드라이버가 하나 이상의 가상 컴퓨터의 게스트 운영 체제에서 제대로 작동 하지 않습니다.*  
  
## <a name="impact"></a>영향  
*다음 가상 머신에서는 네트워크 성능이 최적이 아닙니다.*  
  
가상 컴퓨터 \<목록 >  
  
## <a name="resolution"></a>해상도  
*게스트 운영 체제에서 다음을 수행 합니다. 적절 한 드라이버가 설치 되어 있고 모든 네트워킹 장치를 사용할 수 있는지 확인 하 고 오류 또는 경고에 대 한 이벤트 로그를 확인 합니다.*  
  


