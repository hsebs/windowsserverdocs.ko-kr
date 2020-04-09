---
ms.assetid: 3095e6a7-b562-4c6a-bf29-13b32c133cac
title: AD FS용 SSL 인증서 등록
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 6f7af40f23c3fa3bd0a31ecb74b11013133a4b32
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855436"
---
# <a name="enroll-an-ssl-certificate-for-ad-fs"></a>AD FS용 SSL 인증서 등록

Active Directory Federation Services \(AD FS\)에는 페더레이션 서버 팜의 각 페더레이션 서버에서 SSL \(서버 인증\) 보안 소켓 계층에 대 한 인증서가 필요 합니다. 팜의 각 페더레이션 서버에서 동일한 인증서를 사용할 수 있습니다. 인증서와 해당 개인 키를 모두 사용할 수 있어야 합니다. 예를 들어 .pfx 파일에 인증서와 해당 프라이빗 키가 있는 경우 AD FS(Active Directory Federation Services) 구성 마법사에 직접 파일을 가져올 수 있습니다. 이 SSL 인증서는 다음 항목을 포함해야 합니다.  
  
1.  주체 이름과 주체 대체 이름에는 fs.contoso.com와 같은 페더레이션 서비스 이름이 포함 되어야 합니다.  
  
2.  주체 대체 이름에는 **enterpriseregistration** 값을 포함 해야 하며, 그 뒤에 사용자 계정 이름 \(UPN\) 접미사 (예: **enterpriseregistration.corp.contoso.com**)가 있어야 합니다.  
  
    > [!WARNING]  
    > Workplace Join에 대 한 장치 등록 서비스 \(DRS\)를 사용 하도록 설정 하려는 경우 주체 대체 이름을 지정 합니다.  
  
> [!IMPORTANT]  
> 조직에서 여러 UPN 접미사를 사용 하는 경우 DRS를 사용 하도록 설정 하려는 경우 SSL 인증서에는 각 접미사에 대 한 주체 대체 이름 항목이 포함 되어야 합니다.  
  
## <a name="see-also"></a>참고 항목
[AD FS 배포](../../ad-fs/AD-FS-Deployment.md)  

[Windows Server 2012 R2 AD FS 배포 가이드](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[페더레이션 서버 팜 배포](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
  

