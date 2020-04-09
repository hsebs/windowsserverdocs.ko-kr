---
title: 제 3 자 확장이 필요한 경우 WFP 가상 스위치 확장을 활성화 해야
description: 이 모범 사례 분석기 규칙에 대 한 텍스트의 온라인 버전입니다.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 8aa8a9a5-e3fa-4c9b-8331-ba5a3de22429
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: d4cc23ce638f7b5ee95f80de067b4ad5b360d118
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859306"
---
# <a name="the-wfp-virtual-switch-extension-should-be-enabled-if-it-is-required-by-third-party-extensions"></a>제 3 자 확장이 필요한 경우 WFP 가상 스위치 확장을 활성화 해야

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
*WFP (Windows 필터링 플랫폼) 가상 스위치 확장을 사용할 수 없습니다.*  
  
## <a name="impact"></a>**식**  
*일부 타사 가상 스위치 확장이 다음 가상 스위치에서 제대로 작동 하지 않을 수 있습니다.*  
  
가상 컴퓨터 \<목록 >  
  
## <a name="resolution"></a>**해결 방법**  
*Windows PowerShell cmdlet VMSwitchExtension를 사용 하 여 타사 확장 프로그램에 필요한 경우 Windows 필터링 플랫폼을 사용 하도록 설정 합니다.*  
  
### <a name="enable-the-windows-filtering-platform-using-windows-powershell"></a>Windows PowerShell을 사용 하 여 Windows 필터링 플랫폼을 사용 하도록 설정  
  
1.  Windows PowerShell을 엽니다. (바탕 화면에서 클릭 **시작** 입력을 시작 하 고 **Windows PowerShell**.)  
  
2.  마우스 오른쪽 단추로 클릭 **Windows PowerShell** 클릭 **관리자 권한으로 실행**합니다.  
  
3.  외부 프로그램 외부 스위치의 이름을 바꾼 후이 명령을 실행 합니다.  
  
```  
Enable-VMSwitchExtension -VMSwitchName External -Name Microsoft Windows Filtering Platform  
```  
  
## <a name="see-also"></a>참고 항목  
[VMSwitchExtension](https://technet.microsoft.com/library/hh848541.aspx)  
  


