---
title: BranchCache 해시 게시 그룹 정책 개체 만들기
description: 이 항목은 일부는 BranchCache 배포 가이드에 대 한 Windows Server 2016, 지사에 WAN 대역폭 사용량을 최적화 하기 위해 분산 및 호스트 캐시 모드로 BranchCache를 배포 하는 방법을 보여 주는
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: c3d33bed-83ef-4eb8-acf9-0719ecb4a931
ms.author: lizross
author: eross-msft
ms.openlocfilehash: e546705d022bbac2588ace5b3e2c6c807c96da63
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319304"
---
# <a name="create-the-branchcache-hash-publication-group-policy-object"></a>BranchCache 해시 게시 그룹 정책 개체 만들기

>적용 대상: Windows Server(반기 채널), Windows Server 2016

그룹 정책 개체 (GPO)의 BranchCache 해시 게시를 만들려면이 절차를 사용할 수 있습니다.  
  
이 절차를 수행하려면 최소한 **Domain Admins** 그룹의 구성원이거나 이와 동등한 자격이 필요합니다.  
  
> [!NOTE]  
> 이 절차를 수행 하기 전에 BranchCache 파일 서버 조직 구성 단위를 만들고 파일 서버 OU로 이동 합니다. 자세한 내용은 참조 [도메인 구성원 파일 서버에 대 한 해시 게시 활성화](../../branchcache/deploy/Enable-Hash-Publication-for-Domain-Member-File-Servers.md)합니다.  
  
### <a name="to-create-the-branchcache-hash-publication-group-policy-object"></a>그룹 정책 개체의 BranchCache 해시 게시를 만들려면  
  
1.  Windows PowerShell을 열고 **mmc**를 입력한 후 Enter 키를 누릅니다. MMC(Microsoft Management Console)가 열립니다.  
  
2.  MMC의 **파일** 메뉴에서 **스냅인 추가/제거**를 클릭합니다. **추가 / 제거 스냅인** 대화 상자가 열립니다.  
  
3.  **추가 / 제거 스냅인**,  **사용 가능한 스냅인**, 두 번 클릭 **그룹 정책 관리**, 를 클릭 하 고 **확인**합니다.  
  
4.  그룹 정책 관리 MMC에서 이전에 만든 OU의 BranchCache 파일 서버에 경로 확장 합니다. 포리스트 example.com 라고 하 고 도메인의 이름을 example1.com OU BranchCache 파일 서버 이름이 인 경우 예를 들어 다음 경로 확장: **그룹 정책 관리**, **포리스트: example.com**, **도메인**, **example1.com**, **BranchCache 파일 서버**합니다.  
  
5.  마우스 오른쪽 단추로 클릭 **BranchCache 파일 서버**, 를 클릭 하 고 **이 도메인에서 GPO를 만들고 여기에 연결**합니다. **새 GPO** 대화 상자가 열립니다. **이름**, 새 GPO의 이름을 입력 합니다. 예를 들어 개체 BranchCache 해시 게시 이름을 지정 하려는 경우 입력 **BranchCache 해시 게시**합니다. **확인**을 클릭합니다.  
  


