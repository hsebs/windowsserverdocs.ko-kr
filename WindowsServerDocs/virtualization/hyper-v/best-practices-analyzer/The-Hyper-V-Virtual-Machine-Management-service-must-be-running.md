---
title: Hyper-v 가상 컴퓨터 관리 서비스가 실행 되어야 합니다.
description: 이 모범 사례 분석기 규칙에서 보고 한 문제를 해결 하는 지침을 제공 합니다.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: f44d6887-6458-4438-9d93-574587e3f7d1
author: kbdazure
ms.date: 10/03/2016
ms.openlocfilehash: 50f101f9dad824e13fa5827175cc1c944a96a91b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859326"
---
# <a name="the-hyper-v-virtual-machine-management-service-must-be-running"></a>Hyper-v 가상 컴퓨터 관리 서비스가 실행 되어야 합니다.

>적용 대상: Windows Server 2016
  
모범 사례 및 검사에 대한 자세한 내용은 [모범 사례 분석기](https://go.microsoft.com/fwlink/?LinkId=122786)를 참조하세요.  
  
|속성|세부 정보|  
|-|-|  
|**운영 체제**|Windows Server 2016|  
|**제품/기능**|Hyper-V|  
|**등급**|오류|  
|**범주**|필수 조건|  

다음 섹션에서는 기울임꼴이이 문제에 대 한 모범 사례 분석기 도구에 표시 되는 UI 텍스트를 나타냅니다.

## <a name="issue"></a>문제  
  
*가상 컴퓨터를 관리 하는 데 필요한 서비스가 실행 되 고 있지 않습니다.*  
  
## <a name="impact"></a>영향  
  
*가상 컴퓨터 관리 작업을 수행할 수 없습니다.*  
  
가상 컴퓨터를 실행 하는 계속 실행 됩니다. 그러나 가상 컴퓨터를 관리 하거나 만들거나 서비스가 실행 될 때까지를 삭제할 수 없습니다.  
  
## <a name="resolution"></a>해상도  
  
*서비스 스냅인 또는 Sc config 명령줄 도구를 사용 하 여 자동으로 시작 되도록 서비스를 다시 구성 합니다.*  
  
> [!TIP]  
> 데스크톱 응용 프로그램에서 서비스를 찾을 수 없습니다 또는 명령줄 도구는 서비스가 존재 하지 않으면 Hyper-v 관리 도구 것을 보고 하는 경우 설치 되지 않습니다. 그리고 시작 메뉴에서 Hyper-v MMC 콘솔을 볼 수 없는 경우에는 Hyper-v 관리 도구를 설치 해야 합니다.

Hyper-v 관리 도구를 설치 하려면:  
>   
> - Windows server에서는 서버 관리자를 열고 역할 및 기능 추가 마법사를 사용 합니다. 자세한 내용은 다음을 참조 하십시오. [Windows Server 2016에 Hyper-v 역할을 설치](../get-started/Install-the-Hyper-V-role-on-Windows-Server.md)합니다.  PowerShell을 사용 하 여 도구 (`Install-WindowsFeature -Name Hyper-V-Tools, Hyper-V-PowerShell`)를 설치할 수도 있습니다. 
> - Windows에서 바탕 화면에서 입력을 시작 **프로그램**, 클릭 **프로그램 및 기능** (제어판) > **Windows 기능 설정 또는 해제** > **Hyper-v** > **Hyper-v 관리 도구**합니다. 그런 다음 **확인**을 클릭합니다.  
  
### <a name="to-reconfigure-the-service-to-start-automatically-using-the-services-desktop-app"></a>서비스 데스크톱 응용 프로그램을 사용 하 여 자동으로 시작 되도록 서비스를 다시 구성 하려면  
  
1.  서비스 데스크톱 응용 프로그램을 엽니다. (클릭 **시작**, 클릭는 **검색 시작** 상자에 입력 합니다 **services.msc**, 한 다음 ENTER를 누릅니다.)  
  
2.  세부 정보 창에서 마우스 오른쪽 단추로 클릭 **Hyper-v 가상 컴퓨터 관리**, 를 클릭 하 고 **속성**합니다.  
  
3.  에 **일반** 탭 **시작** 입력, 클릭 **자동**합니다.  
  
4.  서비스를 시작 하려면 **시작**합니다.  
  
### <a name="to-reconfigure-the-service-to-start-automatically-using-sc-config"></a>SC Config를 사용 하 여 자동으로 시작 되도록 서비스를 다시 구성 하려면  
  
1.  Windows PowerShell을 엽니다. (바탕 화면에서 클릭 **시작** 입력을 시작 하 고 **Windows PowerShell**.)  
  
2.  마우스 오른쪽 단추로 클릭 **Windows PowerShell** 클릭 **관리자 권한으로 실행**합니다.  
  
3.  서비스를 다시 구성 하려면 다음을 입력 합니다.  
  
    ```  
    sc config vmms start=auto  
    ```  
  
4.  서비스를 시작 하려면 다음을 입력 합니다.  
  
    ```  
    sc start vmms  
    ```  
  
서비스가 이미 자동으로 시작 되도록 구성 되어 있고 서비스를 다시 시작 해야 하는 경우 Hyper-v 관리자 또는 위에 표시 된 sc start vmms 명령에서 수행할 수 있습니다.  
  
#### <a name="to-restart-the-service-from-hyper-v-manager"></a>Hyper-v 관리자에서 서비스를 다시 시작  
  
1.  Hyper-V 관리자를 엽니다. **시작**을 클릭하고 **관리 도구**를 가리킨 다음 **Hyper-V 관리자**를 클릭합니다.  
  
2.  탐색 창에서 선택 되어 있지 않은 경우 서버 이름을 클릭 합니다.  
  
3.  에 **작업** 창에서 클릭 **서비스 시작**합니다.  
  


