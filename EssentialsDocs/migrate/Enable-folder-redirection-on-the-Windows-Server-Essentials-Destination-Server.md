---
title: Windows Server Essentials 대상 서버1에서 폴더 리디렉션 사용
description: Windows Server Essentials를 사용 하는 방법을 설명 합니다.
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
H1: Windows Server Essentials 대상 서버에서 폴더 리디렉션 사용
ms.assetid: f67d195e-36f6-495a-8361-6d5faa889441
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2db5bafe1f14dddad253ffdb892f90a040246638
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852596"
---
# <a name="enable-folder-redirection-on-the-windows-server-essentials-destination-server1"></a>Windows Server Essentials 대상 서버1에서 폴더 리디렉션 사용

>적용 대상: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

원본 서버에서 폴더 리디렉션이 사용하도록 설정되어 있으면 이 작업을 수행할 수 있습니다.  
  
 먼저 Windows Server Essentials 대시보드를 사용 하 여 대상 서버에서 폴더 리디렉션을 사용 하도록 설정 합니다. 그런 다음 이전 폴더 리디렉션 그룹 정책 설정을 삭제합니다.  
  
### <a name="to-enable-folder-redirection-on-the-destination-server"></a>대상 서버에서 폴더 리디렉션을 사용하도록 설정하려면  
  
1.  대상 서버에서 Windows Server Essentials 대시보드를 엽니다.  
  
2.  탐색 모음에서 **장치**를 클릭합니다.  
  
3.  **장치 작업** 창에서 **그룹 정책 구현**을 클릭합니다.  
  
4.  **폴더 리디렉션 그룹 정책 사용** 페이지에서 리디렉션할 폴더를 선택하고 **다음**을 클릭합니다.  
  
5.  **보안 정책 설정 사용** 페이지에서 **마침**을 클릭합니다.  
  
### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>이전 폴더 리디렉션 그룹 정책 설정을 삭제하려면  
  
1. 대상 서버에서 **그룹 정책 관리** 관리 도구를 엽니다.  
  
2. **그룹 정책 관리**에서 **포리스트: 해당**<em>networkdomainname</em>, **도메인**을 차례로 확장 하 고 해당 *networkdomainname*을 확장 한 다음 **그룹 정책 개체**를 확장 합니다.  
  
3. 마우스 오른쪽 단추로 클릭 **W7PVP 폴더 리디렉션**을 클릭하고 **삭제**합니다.  
  
4. 경고를 읽고 **예**를 클릭합니다.  
  
5. **그룹 정책 관리**를 닫습니다.  
  
   폴더 리디렉션에 변경 내용을 적용하려면 네트워크 사용자가 컴퓨터에서 로그오프한 다음 다시 로그온해야 합니다. 이렇게 하면 모든 리디렉션된 폴더가 대상 서버로 전송됩니다.
