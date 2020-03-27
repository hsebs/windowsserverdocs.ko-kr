---
title: Microsoft Online Backup Service 작업 등록 사용자 지정
description: Windows Server Essentials를 사용 하는 방법을 설명 합니다.
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7eafbb3-7728-487e-b287-90bbd6fee7f0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f6e0a499fd149706dc3d7cce21935a7f8b5c5a48
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80311902"
---
# <a name="customize-sign-up-for-microsoft-online-backup-service-task"></a>Microsoft Online Backup Service 작업 등록 사용자 지정

>적용 대상: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

기본적으로 대시보드 **장치** 탭에 있는 **Microsoft Online Backup Service에 등록** 작업은 Microsoft Online Backup Service 웹 사이트를 엽니다. 이 웹 사이트는 서비스에 관한 정보를 제공하고 서비스 가입을 안내하며 필요한 소프트웨어 다운로드를 제공합니다.  
  
 **Microsoft Online Backup Service에 등록** 작업을 두 가지 방식으로 사용자 지정할 수 있습니다.  
  
-   사용자 지정 고객 환경을 나타내는 URL로 기본 웹 사이트 URL을 대체할 수 있습니다. 기본 URL을 대체하려면 레지스트리 편집기를 열고, 레지스트리 키 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\LinkUrl**을 만든 다음 사용자 지정 URL을 키 값으로 할당합니다.  
  
-   작업을 숨길 수 있습니다. 작업을 숨기려면 레지스트리 편집기를 열고 레지스트리 키(**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\OnlineBackupInstalled**)를 만듭니다.  
  
## <a name="see-also"></a>관련 항목  
 [이미지  만들기 및 사용자 지정](Creating-and-Customizing-the-Image.md)  
 [추가 사용자 지정](Additional-Customizations.md)   
 [배포할 이미지를 준비 하는 중](Preparing-the-Image-for-Deployment.md)   
 [사용자 환경 테스트](Testing-the-Customer-Experience.md)