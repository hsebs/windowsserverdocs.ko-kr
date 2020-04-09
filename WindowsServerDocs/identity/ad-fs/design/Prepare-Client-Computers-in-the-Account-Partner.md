---
ms.assetid: cea6011d-3753-4b95-aaa5-38d4e97d6e42
title: 계정 파트너에서 클라이언트 컴퓨터 준비
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 014524c78312c6fcd478b40ec47e212a194b0531
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858596"
---
# <a name="prepare-client-computers-in-the-account-partner"></a>계정 파트너에서 클라이언트 컴퓨터 준비

계정 파트너 조직의 관리자가 페더레이션 응용 프로그램에 대 한 Active Directory Federation Services \(\) AD FS에 대 한 액세스를 위해 클라이언트 컴퓨터를 준비 하는 가장 쉬운 방법은 그룹 정책를 사용 하는 것입니다. 그룹 정책은 페더레이션 애플리케이션에 액세스하는 데 사용하는 모든 클라이언트 컴퓨터에 페더레이션에 필요한 특정 인증서 및 설정을 푸시하는 편리한 방법을 제공합니다.  
  
클라이언트 컴퓨터가 인증서 프롬프트 또는 신뢰할 수 있는 사이트 관련 프롬프트 없이 페더레이션 응용 프로그램에 원활 하 게 액세스할 수 있도록 조직에 광범위 하 게 AD FS를 배포 하기 전에 먼저 각 클라이언트 컴퓨터를 준비 하는 것이 좋습니다. 다음 작업이 자동으로 수행되도록 그룹 정책 사용을 고려해 보세요.  
  
-   각 클라이언트 컴퓨터에서 계정 페더레이션 서버를 신뢰 하도록 Internet Explorer를 구성 합니다.  
  
    자세한 내용은 [Configure Client Computers to Trust the Account Federation Server](../../ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md)를 참조하세요.  
  
-   적절 한 계정 페더레이션 서버, 리소스 페더레이션 서버 및 웹 서버 SSL(Secure Sockets Layer) \(SSL\) 인증서 \(또는 각 클라이언트 컴퓨터의 신뢰할 수 있는 루트\)에 연결 된 동등한 인증서를 설치 합니다.  
  
    자세한 내용은 [그룹 정책를 사용 하 여 클라이언트 컴퓨터에 인증서 배포](../../ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md)를 참조 하세요.  
  

## <a name="see-also"></a>참고 항목
[Windows Server 2012의 AD FS 디자인 가이드](AD-FS-Design-Guide-in-Windows-Server-2012.md)
