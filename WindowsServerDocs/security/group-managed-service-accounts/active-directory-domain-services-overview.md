---
title: Active Directory 도메인 서비스 개요
description: Windows Server 보안
ms.prod: windows-server
ms.technology: security-auditing
ms.topic: article
ms.assetid: 6cfe9479-5d17-41d5-939a-891e5233fdca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 73272086b176fa8fb086063ff3d4249a02b016b2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857026"
---
# <a name="active-directory-domain-services-overview"></a>Active Directory 도메인 서비스 개요

>적용 대상: Windows Server(반기 채널), Windows Server 2016
  
디렉터리는 네트워크의 개체에 대 한 정보를 저장 하는 계층 구조입니다. Active Directory Domain Services (AD DS)와 같은 디렉터리 서비스는 디렉터리 데이터를 저장 하 고이 데이터를 네트워크 사용자 및 관리자가 사용할 수 있도록 하는 방법을 제공 합니다. 예를 들어 AD DS은 이름, 암호, 전화 번호 등의 사용자 계정에 대 한 정보를 저장 하 고, 동일한 네트워크에 있는 다른 권한 있는 사용자가이 정보에 액세스할 수 있도록 합니다.  
  
Active Directory는 네트워크의 개체에 대한 정보를 저장하고 관리자 및 사용자가 이러한 정보를 쉽게 찾아서 사용할 수 있게 해줍니다. Active Directory는 논리적이고 계층적인 디렉터리 정보 구성을 위한 기초로 구조화된 데이터 저장소를 사용합니다.  
  
이 데이터 저장소 (디렉터리 라고도 함)에는 Active Directory 개체에 대 한 정보가 포함 되어 있습니다. 일반적으로 이러한 개체에는 서버, 볼륨, 프린터, 네트워크 사용자 및 컴퓨터 계정 등의 공유 리소스가 포함 됩니다. Active Directory 데이터 저장소에 대 한 자세한 내용은 [디렉터리 데이터 저장소](https://technet.microsoft.com/library/cc736627(v=ws.10).aspx)를 참조 하세요.  
  
보안은 디렉터리의 개체에 대 한 로그온 인증 및 액세스 제어를 통해 Active Directory와 통합 됩니다. 관리자는 단일 네트워크 로그온을 통해 네트워크에서 디렉터리 데이터 및 조직을 관리할 수 있으며, 권한 있는 네트워크 사용자는 네트워크의 모든 위치에서 리소스에 액세스할 수 있습니다. 정책 기반 관리를 사용하면 가장 복잡한 네트워크조차 쉽게 관리할 수 있습니다. Active Directory 보안에 대 한 자세한 내용은 보안 개요를 참조 하세요.  
  
Active Directory에도 다음이 포함 됩니다.  
* 디렉터리에 포함 된 개체 및 특성의 클래스, 이러한 개체의 인스턴스에 대 한 제약 조건 및 제한 및 이름의 형식을 정의 하는 규칙 집합 ( **스키마**)입니다. 스키마에 대 한 자세한 내용은 스키마를 참조 하십시오.  
  
  
* 디렉터리의 모든 개체에 대 한 정보를 포함 하는 **글로벌 카탈로그** 입니다. 이를 통해 사용자와 관리자는 디렉터리의 어떤 도메인에 실제로 데이터가 포함 되는지에 관계 없이 디렉터리 정보를 찾을 수 있습니다. 글로벌 카탈로그에 대 한 자세한 내용은 글로벌 카탈로그의 역할을 참조 하세요.  
  
  
* 네트워크 사용자 또는 응용 프로그램에서 개체와 해당 속성을 게시 하 고 찾을 수 있도록 하는 **쿼리 및 인덱스 메커니즘**입니다. 디렉터리를 쿼리 하는 방법에 대 한 자세한 내용은 디렉터리 정보 찾기를 참조 하세요.  
  
  
* 네트워크를 통해 디렉터리 데이터를 배포 하는 **복제 서비스** 입니다. 도메인의 모든 도메인 컨트롤러는 복제에 참여 하 고 해당 도메인에 대 한 모든 디렉터리 정보의 전체 복사본을 포함 합니다. 디렉터리 데이터에 대한 변경 내용은 모두 도메인의 모든 도메인 컨트롤러에 복제됩니다. Active Directory 복제에 대 한 자세한 내용은 복제 개요를 참조 하세요.  
  
## <a name="understanding-active-directory"></a>Active Directory 이해  
 이 섹션에서는 핵심 Active Directory 개념에 대 한 링크를 제공 합니다.  
   
* [Active Directory 구조 및 저장소 기술](https://technet.microsoft.com/library/cc759186(v=ws.10).aspx)  
* [도메인 컨트롤러 역할](https://technet.microsoft.com/library/cc786438(v=ws.10).aspx)   
* Active Directory 스키마   
* [트러스트 이해](https://technet.microsoft.com/library/cc771294(v=ws.10).aspx)   
* [Active Directory 복제 기술](https://technet.microsoft.com/library/cc786438(v=ws.10).aspx)   
* [Active Directory 검색 및 게시 기술](https://technet.microsoft.com/library/cc775686(v=ws.10).aspx)   
* DNS 및 그룹 정책 상호 운용   
* [스키마 이해](https://technet.microsoft.com/library/cc759402(v=ws.10).aspx)   
  
Active Directory 개념에 대 한 자세한 목록은 [Active Directory 이해](https://technet.microsoft.com/library/cc781408(v=ws.10).aspx)를 참조 하세요.   

