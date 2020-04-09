---
title: 파일 공유에서 BranchCache 사용(선택 사항)
description: 이 항목은 일부는 BranchCache 배포 가이드에 대 한 Windows Server 2016, 지사에 WAN 대역폭 사용량을 최적화 하기 위해 분산 및 호스트 캐시 모드로 BranchCache를 배포 하는 방법을 보여 주는
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 9c465a9e-c504-44ec-9ebc-4e06ba54db30
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 501fd1b1ac3b0bc7a0767ec57502ba18a8ee76e4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861086"
---
# <a name="enable-branchcache-on-a-file-share-optional"></a>파일 공유에서 BranchCache 사용(선택 사항)

>적용 대상: Windows Server(반기 채널), Windows Server 2016

파일 공유에서 BranchCache를 사용 하도록 설정 하려면이 절차를 사용할 수 있습니다.  
  
> [!IMPORTANT]  
> 값으로 해시 게시 설정을 구성 하는 경우이 절차를 수행할 필요가 없습니다 **모든 공유 폴더에 대 한 해시 게시 허용**합니다.  
  
멤버 자격이 **관리자**, 또는 이와 동등한이 절차를 수행 하는 데 필요한 최소값입니다.  
  
### <a name="to-enable-branchcache-on-a-file-share"></a>파일 공유에서 BranchCache를 사용 하도록 설정 하려면  
  
1.  Windows PowerShell을 열고 **mmc**를 입력한 후 Enter 키를 누릅니다. MMC(Microsoft Management Console)가 열립니다.  
  
2.  MMC의 **파일** 메뉴에서 **스냅인 추가/제거**를 클릭합니다. **추가 / 제거 스냅인** 대화 상자가 열립니다.  
  
3.  **추가 / 제거 스냅인**,  **사용 가능한 스냅인**, 를 두 번 클릭 **공유 폴더**합니다. 로컬 컴퓨터 개체를 선택 하는 공유 폴더 마법사가 열립니다. 원하는 보기를 구성 클릭 **마침**, 를 클릭 하 고 **확인**합니다.  
  
4.  두 번 클릭 **공유 폴더 (로컬)** , 를 클릭 하 고 **공유**합니다.  
  
5.  세부 정보 창에서 공유를 마우스 오른쪽 단추로 클릭 하 고 클릭 **속성**합니다. 공유의 **속성** 대화 상자가 열립니다.  
  
6.  에 **속성** 대화 상자의 **일반** 탭을 클릭 하 여 **오프 라인 설정**합니다. **오프 라인 설정** 대화 상자가 열립니다.  
  
7.  확인 **파일 및 사용자 지정 하는 프로그램이 사용할 수 있는 오프 라인** 을 선택한 다음 클릭 **BranchCache**합니다.  
  
8.  **확인** 을 두 번 클릭합니다.  
  

