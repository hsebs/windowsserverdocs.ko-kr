---
ms.assetid: a8558c9d-0606-4881-93b2-f2d2716b18e7
title: Windows Server 2012 R2의 AD FS 디자인 가이드
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: e8675c255032bca4623a9649bfc0bcca478008e3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854896"
---
# <a name="ad-fs-design-guide-in-windows-server"></a>Windows Server의 AD FS 디자인 가이드 

Active Directory Federation Services \(AD FS\)\-보안 엔터프라이즈, 페더레이션 파트너 조직 또는 클라우드에서 응용 프로그램에 액세스 하려는 최종 사용자에 게 \(SSO\) 기능에 대해 간소화 된 보안 id 페더레이션 및 웹 single sign AD FS을 제공 합니다.\-  
  
Windows Server&reg; 2012 r 2에서 AD FS에는 id 공급자 역할을 하는 페더레이션 서비스 역할 서비스가 포함 되어 있습니다 .이 서비스 역할 서비스는 사용자가 AD FS\)를 신뢰 하는 응용 프로그램에 보안 토큰을 제공 하 고, 다른 id 공급자의 토큰을 사용한 다음 \(AD FS를 신뢰 하는 응용 프로그램에 보안 토큰을 제공 하도록 인증 \(.\)  
  
이제 Windows Server 2012 R2에서 AD FS에 의해 보안되는 애플리케이션 및 서비스에 대한 엑스트라넷 액세스 권한을 제공하는 기능은 웹 애플리케이션 프록시라는 새 원격 액세스 역할 서비스에서 수행됩니다. 이는 AD FS 페더레이션 서버 프록시가 이 함수를 처리한 이전 버전의 Windows Server에서 시작되었습니다. 웹 응용 프로그램 프록시는 AD FS\-관련 엑스트라넷 시나리오 및 기타 엑스트라넷 시나리오에 대 한 액세스를 제공 하도록 설계 된 서버 역할입니다. 웹 응용 프로그램 프록시에 대 한 자세한 내용은 [웹 응용 프로그램 프록시 연습 가이드](https://technet.microsoft.com/library/dn280944.aspx)를 참조 하세요.  
  
## <a name="about-this-guide"></a>이 가이드 정보  
이 가이드에서는 조직의 요구 사항에 따라 AD FS의 새 배포를 계획 하는 데 도움이 되는 권장 사항을 제공 합니다. 이 가이드는 인프라 전문가 또는 시스템 설계자용으로 작성되었습니다. AD FS 배포를 계획할 때 주요 결정 사항을 강조 표시 합니다. 이 가이드를 읽기 전에 AD FS 기능 수준에서 작동 하는 방식에 대해 잘 알고 있어야 합니다. 자세한 내용은 [Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)를 참조하세요.  
  
## <a name="in-this-guide"></a>설명서의 내용  
  
-   [AD FS 배포 목표 식별](Identify-Your-AD-FS-Deployment-Goals.md)  
  
-   [AD FS 배포 토폴로지 계획](Plan-Your-AD-FS-Deployment-Topology.md)  
  
-   [AD FS 요구 사항](AD-FS-Requirements.md)  
  
  
## <a name="see-also"></a>참고 항목  
[AD FS 디자인](../../ad-fs/AD-FS-Design.md)  
  

