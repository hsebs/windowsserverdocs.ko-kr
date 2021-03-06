---
ms.assetid: 19feca0e-a6d0-4d27-93b0-cb44f8c26484
title: OU의 사용자 계정 및 리소스 OU 관리 위임
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 3043aaf79b2c0894fffe2f896a235ad519222e05
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80822746"
---
# <a name="delegating-administration-of-account-ous-and-resource-ous"></a>OU의 사용자 계정 및 리소스 OU 관리 위임

>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

계정 Ou (조직 단위)는 사용자, 그룹 및 컴퓨터 개체를 포함 합니다. 리소스 Ou 리소스 및 해당 리소스를 관리 하는 일을 담당 하는 계정을 포함 합니다. 포리스트 소유자는 이러한 개체 및 리소스를 관리 하는 OU 구조를 만들고 해당 구조 제어 OU 소유자에 게 위임 합니다.  
  
## <a name="delegating-administration-of-account-ous"></a>계정 Ou 관리 위임  
만들고 사용자, 그룹 및 컴퓨터 개체를 수정 하는 경우 데이터 관리자에 게 계정 OU 구조를 위임 합니다. 계정 OU 구조 하지 독립적으로 제어할 수 있어야 하는 각 계정 유형에 대 한 Ou의 하위 트리에입니다. 예를 들어, OU 소유자 사용자, 컴퓨터, 그룹에 대 한 계정을 OU 및 서비스 계정에 자식 Ou를 통해 다양 한 데이터 관리자에 게 특정 컨트롤을 위임할 수 있습니다.  
  
다음 그림에서는 계정 OU 구조에의 한 가지 예를 보여 줍니다.  
  
![관리 위임](media/Delegating-Administration-of-Account-OUs-and-Resource-OUs/66d38fbe-e8eb-42d7-abab-9526243bf6d9.gif)  
  
다음 표에 나열 하 고 계정 OU 구조에서에서 만들 수 있는 가능한 자식 Ou에 설명 합니다.  
  
|OU|용도|  
|------|-----------|  
|Users|관리자가 아닌 직원에 대 한 사용자 계정을 포함합니다.|  
|서비스 계정|네트워크 리소스에 액세스 해야 하는 일부 서비스는 사용자 계정으로 실행 합니다. 이 OU 사용자 OU에에서 포함 된 사용자 계정에서 별도 서비스 사용자 계정에 만들어집니다. 또한 다른 종류의 사용자 계정 별도 Ou에 배치 하는 특정 관리 요구 사항에 따라이 관리할 수 있습니다.|  
|컴퓨터|도메인 컨트롤러가 아닌 컴퓨터에 대 한 계정을 포함합니다.|  
|그룹|별도로 관리 하는 관리 그룹을 제외 하 고 모든 종류의 그룹을 포함 합니다.|  
|관리자|일반 사용자에서 별도로 관리 될 수 있도록 하려면 데이터 관리자는 계정 OU 구조에에서 대 한 사용자 및 그룹 계정을 포함 합니다. 관리 권한이 있는 사용자 및 그룹에 변경 내용을 추적할 수 있도록이 OU에 대 한 감사를 사용 하도록 설정 합니다.|  
  
다음 그림에서는 계정 OU 구조에 대 한 관리 그룹 디자인의 한 가지 예를 보여 줍니다.  
  
![관리 위임](media/Delegating-Administration-of-Account-OUs-and-Resource-OUs/be2cd2d2-6956-429c-a53a-369e6fe40b2b.gif)  
  
이 자식 Ou를 관리 하는 그룹 관리를 담당 하는 개체의 특정 클래스에 대해서만 모든 권한을 부여 됩니다.  
  
OU 구조 내에서 제어를 위임 하는 데 사용할 수 있는 그룹의 형식은 기반으로 계정이 있는 위치를 관리 하는 OU 구조를 기준으로 합니다. 관리자 사용자 계정 및 OU 구조 단일 도메인에 있으면 그룹을 위임에 대해 사용할 수 있도록 만드는 전역 그룹 이어야 합니다. 조직에서는 자신의 사용자 계정을 관리 하는 둘 이상의 지리적 지역에 존재 하는 부서, 계정 둘 이상의 도메인의 Ou 관리를 담당 하는 데이터 관리자의 그룹을 할 수 있습니다. 모든 데이터 관리자 계정은 단일 도메인에 존재 하는 경우 제어를 위임 해야 하는 여러 도메인에 대 한 OU 구조가 글로벌 그룹의 관리 계정 멤버를 확인 하 고이 글로벌 그룹을 각 도메인의 OU 구조 제어 위임. 여러 도메인의 OU 구조 제어를 위임 하는 데이터 관리자 계정을 제공, 유니버설 그룹을 사용 해야 합니다. 유니버설 그룹에는 서로 다른 도메인의 사용자가 포함 될 수 고 따라서 여러 도메인에 대 한 제어를 위임 하려면 사용할 수 있습니다.  
  
## <a name="delegating-administration-of-resource-ous"></a>리소스 Ou 관리 위임  
리소스 Ou 리소스에 대 한 액세스를 관리 하는 데 사용 됩니다. 리소스 OU 소유자 파일 공유, 데이터베이스 및 프린터와 같은 리소스를 포함 하는 도메인에 가입 된 서버에 대 한 컴퓨터 계정을 만듭니다. 또한 리소스 OU 소유자는 해당 리소스에 대 한 액세스를 제어 하는 그룹을 만듭니다.  
  
다음 그림 리소스 OU에 대 한 두 가지 가능한 위치를 보여 줍니다.  
  
![관리 위임](media/Delegating-Administration-of-Account-OUs-and-Resource-OUs/6667a5ce-34d6-48a9-9974-b823ba70e2af.gif)  
  
리소스 OU를 자식 OU 관리 계층 구조에서 해당 계정 OU의 OU 또는 도메인 루트 아래에 있을 수 있습니다. 리소스 Ou 표준 자식 Ou를 갖지 않습니다. 컴퓨터 및 그룹 리소스 OU에 직접 배치 됩니다.  
  
리소스 OU 소유자 OU 내에서 개체를 소유 하지만 OU 컨테이너 자체를 소유 하지 않습니다. 리소스 OU 소유자 관리 컴퓨터 및 그룹 개체입니다. OU 내에서 개체의 다른 클래스를 만들 수 및 자식 Ou를 만들 수 있습니다.  
  
> [!NOTE]  
> 작성자나 소유자 개체의 부모 컨테이너에서 상속 된 사용 권한에 관계 없이 개체에 대 한 액세스 제어 목록 (ACL)을 설정 하는 기능을 있습니다. 리소스 OU 소유자 수를 다시 설정 하는 OU에 대 한 ACL 해당 소유자의 사용자를 포함 한 OU를 개체의 모든 클래스를 만들 수 있습니다. 이러한 이유로 리소스 OU 소유자 Ou 만들기를 허용 되지 않습니다.  
  
각 리소스 도메인의 OU에 대 한 글로벌 그룹을 나타내는 OU의 콘텐츠 관리를 담당 하는 데이터 관리자를 만듭니다. 이 그룹에는 OU에 그룹 및 컴퓨터 개체에 대해 하지만 OU 컨테이너 자체를 통해서는 하는 모든 권한을 가집니다.  
  
다음 그림에는 리소스 OU에 대 한 관리 그룹 설계를 보여 줍니다.  
  
![관리 위임](media/Delegating-Administration-of-Account-OUs-and-Resource-OUs/8a3f7714-a3bf-43f7-b999-6070543248b0.gif)  
  
리소스 OU에 컴퓨터 계정을 배치 계정 개체에 대 한 OU 소유자 제어를 제공 하지만 OU 소유자 컴퓨터의 관리자를 확인 하지 않습니다. Active Directory 도메인에서 Domain Admins 그룹, 기본적으로에 배치 됩니다 모든 컴퓨터에서 로컬 관리자 그룹. 즉, 서비스 관리자가 해당 컴퓨터에 대 한 제어 합니다. 리소스 OU 소유자가 Ou에 컴퓨터에 대 한 관리 제어를 필요로 하는 경우 포리스트 소유자 해당 OU의 컴퓨터에 Administrators 그룹의 구성원 리소스 OU 소유자를 확인 하는 제한 된 그룹 그룹 정책을 적용할 수 있습니다.  
  


