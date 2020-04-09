---
ms.assetid: 4ae26970-e42e-4e69-887a-b16d2f8d0695
title: 계정 페더레이션 서버를 신뢰 하도록 클라이언트 컴퓨터 구성
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 5022be852ab72f57c90d957cb1111f10e9b03a90
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854946"
---
# <a name="configure-client-computers-to-trust-the-account-federation-server"></a>계정 페더레이션 서버를 신뢰 하도록 클라이언트 컴퓨터 구성

클라이언트 컴퓨터는 Active Directory Federation Services \(AD FS\)를 사용 하 여 페더레이션된 응용 프로그램에 성공적으로 액세스할 수 있도록 먼저 각 클라이언트 컴퓨터에서 Internet Explorer 설정을 구성 해야 합니다. 그러면 브라우저에서 계정 페더레이션 서버를 신뢰할 수 있습니다. 다음 절차 중 하나를 완료 하 여 관리 기본 설정에 따라 수동으로 또는 그룹 정책를 통해이 작업을 수행할 수 있습니다.  
  
## <a name="configuring-internet-explorer-settings-manually"></a>수동으로 Internet Explorer 설정 구성  
다음 절차를 사용 하 여 AD FS 통해 페더레이션을 지원 하도록 각 사용자의 Internet Explorer 설정을 수동으로 구성할 수 있습니다. 여러 사용자가 단일 컴퓨터를 사용 하는 경우 각 사용자 프로필에 대해이 절차를 여러 번 수행 합니다.  
  
이 절차를 수행 하려면 페더레이션 응용 프로그램에 액세스 하는 사용자로 로그온 합니다. 특정 설정\-프로필입니다. 따라서 특정 컴퓨터에 있는 각 프로필에 대해이 설정을 수동으로 추가 해야 합니다.  
  
#### <a name="to-manually-configure-client-computers-to-trust-the-account-federation-server"></a>계정 페더레이션 서버를 신뢰 하도록 클라이언트 컴퓨터를 수동으로 구성 하려면  
  
1.  클라이언트 컴퓨터에서 Internet Explorer를 시작 합니다.  
  
2.  **도구** 메뉴에서 **인터넷 옵션**을 클릭 합니다.  
  
3.  **보안** 탭에서 **로컬 인트라넷** 아이콘을 클릭 한 다음 **사이트**를 클릭 합니다.  
  
4.  **고급**을 클릭 하 고 **이 웹 사이트를 영역에 추가**에서 계정 페더레이션 \(서버의 DNS\) 이름 \(전체 도메인 이름 시스템 (예: https:\/\/fs1.fabrikam.com\)을 입력 한 다음 **추가**를 클릭 합니다.  
  
5.  **확인**을 세 번 클릭합니다.  
  
## <a name="configuring-internet-explorer-settings-by-using-grouppolicy"></a>그룹 정책를 사용 하 여 Internet Explorer 설정 구성  
대부분의 배포의 경우 그룹 정책를 사용 하 여 각 클라이언트 컴퓨터에 적절 한 Internet Explorer 설정을 푸시하는 것이 좋습니다.  
  
이 절차를 완료 하려면 최소한 **Domain admins** 또는 **Enterprise admins**그룹의 구성원 이거나이에 해당 하는 Active Directory Domain Services \(AD DS\) 해야 합니다.  [로컬 및 도메인 기본 그룹](https://go.microsoft.com/fwlink/?LinkId=83477) 에서 적절 한 계정 및 그룹 구성원 자격 사용에 대 한 세부 정보를 검토 \(http:\/\/go.microsoft.com\/fwlink\/? LinkId\=83477\).   
  
#### <a name="to-configure-client-computers-to-trust-the-account-federation-server-by-using-grouppolicy"></a>그룹 정책를 사용 하 여 계정 페더레이션 서버를 신뢰 하도록 클라이언트 컴퓨터를 구성 하려면  
  
1.  계정 파트너 조직의 포리스트에 있는 도메인 컨트롤러에서 **그룹 정책 관리** 스냅인\-를 시작 합니다.  
  
2.  GPO\)\(적절 한 그룹 정책 개체를 찾아서 마우스 오른쪽\-단추로 클릭 한 다음 **편집**을 클릭 합니다.  
  
3.  콘솔 트리에서 **사용자 구성\\기본 설정\\Windows 설정\\Internet Explorer 유지 관리**를 열고 **보안**을 클릭 합니다.  
  
4.  세부 정보 창에서 **보안 영역 및 콘텐츠 등급**을 두 번 클릭\-합니다.  
  
5.  **보안 영역 및 개인 정보**에서 **현재 보안 영역 및 개인 정보 설정 가져오기**를 클릭 한 다음 **설정 수정**을 클릭 합니다.  
  
6.  **로컬 인트라넷**을 클릭 한 다음 **사이트**를 클릭 합니다.  
  
7.  **이 웹 사이트를 영역에 추가**에서 \(계정 페더레이션 서버의 전체 DNS 이름 (예: https:\/\/fs1.fabrikam.com\)을 입력 하 고 **추가**를 클릭 한 다음 **닫기**를 클릭 합니다.  
  
8.  **확인** 을 두 번 클릭 하 여 그룹 정책에 이러한 변경 내용을 적용 합니다.  
  
