---
title: Windows 8 권장된 메모리 양은로 구성 해야
description: 이 모범 사례 분석기 규칙에서 보고 한 문제를 해결 하는 지침을 제공 합니다.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 0c739e7c-4403-4eff-9e69-213ba1ab7336
author: kbdazure
ms.date: 10/03/2016
ms.openlocfilehash: a2c8ddd1e5b0a4f82773f8b0127a61ba34043d94
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861486"
---
# <a name="windows-8-should-be-configured-with-the-recommended-amount-of-memory"></a>Windows 8 권장된 메모리 양은로 구성 해야

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
*Windows 8을 실행 하는 가상 머신은 1gb RAM 권장 크기 보다 더 작은 수준으로 구성 됩니다.*  
  
## <a name="impact"></a>**식**  
*게스트 운영 체제 및 응용 프로그램이 제대로 작동 하지 않을 수 있습니다. 한 번에 여러 응용 프로그램을 실행 하기에 충분 한 메모리가 없을 수 있습니다. 이는 다음과 같은 가상 컴퓨터에 영향을 줍니다.*  
```  
<list of virtual machines>  
```  
## <a name="resolution"></a>**해결 방법**  
*Hyper-v 관리자를 사용 하 여이 가상 컴퓨터에 할당 된 메모리를 1GB 이상으로 늘리십시오.*  
  
### <a name="increase-the-memory-using-hyper-v-manager"></a>Hyper-v 관리자를 사용 하 여 메모리 확보  
  
1.  Hyper-V 관리자를 엽니다. **시작**을 클릭하고 **관리 도구**를 가리킨 다음 **Hyper-V 관리자**를 클릭합니다.  
  
2.  결과 창에서 아래 **가상 컴퓨터**, 구성 하려는 가상 컴퓨터를 선택 합니다. 으로 가상 컴퓨터의 상태를 표시 해야 **오프**합니다. 그렇지 않은 경우 가상 컴퓨터를 마우스 오른쪽 단추로 클릭 하 고 클릭 한 다음 **종료**합니다.  
  
3.  **작업** 창의 가상 컴퓨터 이름에서 **설정**을 클릭합니다.  
  
4.  탐색 창에서 **메모리**합니다.  
  
5.  에 **메모리** 페이지에서 설정 된 **시작 RAM** 최소 1GB를 클릭 한 다음 **확인**합니다.  
  
### <a name="increase-the-memory-using-windows-powershell"></a>Windows PowerShell을 사용 하 여 메모리 확보  
  
1.  Windows PowerShell을 엽니다. (바탕 화면에서 클릭 **시작** 입력을 시작 하 고 **Windows PowerShell**.)  
  
2.  마우스 오른쪽 단추로 클릭 **Windows PowerShell** 클릭 **관리자 권한으로 실행**합니다.  
  
3.  이 명령을 실행 하는 교체 후 \<MyVM > 가상 컴퓨터의 이름으로:  
  
```  
Set-VMMemory <MyVM> -StartupBytes 1GB  
```  
  
## <a name="see-also"></a>참고 항목  
[설정-VMMemory](https://technet.microsoft.com/library/hh848572.aspx)  
  


