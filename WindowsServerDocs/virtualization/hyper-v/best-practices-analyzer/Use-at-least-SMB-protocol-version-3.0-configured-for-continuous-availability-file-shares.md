---
title: 이상을 사용 SMB 프로토콜 버전 3.0 가상 컴퓨터 파일을 저장 하는 파일 공유에 대 한 지속적인 가용성을 위한 구성
description: 이 모범 사례 분석기 규칙에 대 한 텍스트의 온라인 버전입니다.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: a1fa5cf9-8a48-4f63-bb57-d81e63e77b30
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 18943c6b34ab74206483779db5afa06bbde04874
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854206"
---
# <a name="use-at-least-smb-protocol-version-30-configured-for-continuous-availability-on-file-shares-that-store-files-for-virtual-machines"></a>이상을 사용 SMB 프로토콜 버전 3.0 가상 컴퓨터 파일을 저장 하는 파일 공유에 대 한 지속적인 가용성을 위한 구성

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
*가상 머신 파일 또는 가상 하드 디스크 파일은 SMB 프로토콜 버전 3.0의 지속적인 가용성 기능으로 구성 되지 않은 네트워크 파일 공유에 저장 됩니다.*  
  
## <a name="impact"></a>**식**  
*서버를 사용 하는 가상 컴퓨터의 가용성에 영향을 줄 수 있기 때문에 Microsoft는이 구성을 권장 하지 않습니다. 이는 다음과 같은 가상 컴퓨터에 영향을 줍니다.*  
  
가상 컴퓨터 \<목록 >  
  
## <a name="resolution"></a>**해결 방법**  
다음 작업 중 하나를 수행합니다.  
  
-   지속적인 가용성을 위한 구성 된 SMB 3.0 파일 공유에 파일을 이동 합니다.  
  
-   지속적인 가용성을 제공 하는 현재 파일 공유를 다시 구성 합니다.  
  


