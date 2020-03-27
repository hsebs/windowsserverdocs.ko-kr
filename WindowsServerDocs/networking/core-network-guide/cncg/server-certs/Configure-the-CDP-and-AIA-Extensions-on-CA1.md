---
title: C a 1에서 CDP 및 AIA 확장 구성
description: 이 항목은 서버 배포 인증서 802.1 X 유선 및 무선 배포 가이드의 일부
manager: dougkim
ms.topic: article
ms.assetid: f77a3989-9f92-41ef-92a8-031651dd73a8
ms.prod: windows-server
ms.technology: networking
ms.author: lizross
author: eross-msft
ms.date: 07/26/2018
ms.openlocfilehash: 6434b05d45cf9b8309fac4f6cd5cb5d6d149a7c2
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80318400"
---
# <a name="configure-the-cdp-and-aia-extensions-on-ca1"></a>C a 1에서 CDP 및 AIA 확장 구성

>적용 대상: Windows Server(반기 채널), Windows Server 2016

C a 1에서 인증서 CRL (해지 목록) 배포 지점 (CDP) 및 액세스 AIA (기관 정보) 설정을 구성 하려면이 절차를 사용할 수 있습니다.  
  
이 절차를 수행 하려면 Domain Admins의 구성원 여야 합니다.  
  
#### <a name="to-configure-the-cdp-and-aia-extensions-on-ca1"></a>C a 1에서 CDP 및 AIA 확장을 구성 하려면  
  
1.  서버 관리자에서 **도구**를 클릭한 뒤 **인증 기관**을 클릭합니다.  
  
2.  인증 기관 콘솔 트리에서 마우스 오른쪽 단추로 **corp-c a 1-CA**, 를 클릭 하 고 **속성**합니다.  
  
    > [!NOTE]  
    > CA1 컴퓨터 이름을 하지 않은 도메인 이름은이 예에서 것과 다른 경우 CA 이름은 다릅니다. CA 이름은 형식에서 *도메인*-*CAComputerName*-CA입니다.  
  
3.  **확장** 탭을 클릭 합니다. **확장 선택** 이 **CDP (crl 배포 지점)** 로 설정 되어 있는지 확인 하 고, **사용자가 crl (인증서 해지 목록)을 얻을 수 있는 위치 지정**에서 다음을 수행 합니다.  
  
    1.  항목을 선택 `file://\\<ServerDNSName>\CertEnroll\<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, 를 클릭 하 고 **제거**합니다. **제거 확인**, 클릭 **예**합니다.  
  
    2.  항목을 선택 `http://<ServerDNSName>/CertEnroll/<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, 를 클릭 하 고 **제거**합니다. **제거 확인**, 클릭 **예**합니다.  
  
    3.  경로로 시작 하는 항목을 선택 `ldap:///CN=<CATruncatedName><CRLNameSuffix>,CN=<ServerShortName>`, 를 클릭 하 고 **제거**합니다. **제거 확인**, 클릭 **예**합니다.  
  
4.  **사용자가 인증서 해지 목록 (CRL)을 얻을 수 있는 위치를 지정**, 를 클릭 하 여 **추가**합니다. **위치 추가** 대화 상자가 열립니다.  
  
5.  **위치 추가**,  **위치**, 형식 `http://pki.corp.contoso.com/pki/<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, 를 클릭 하 고 **확인**합니다. CA 속성 대화 상자로 돌아갑니다.  
  
6.  에 **확장** 탭에서 다음 확인란을 선택 합니다.  
  
    -   **Crl에 포함. 클라이언트는이를 사용 하 여 델타 CRL 위치를 찾습니다.**  
  
    -   **발급 된 인증서의 CDP 확장에 포함**  
  
7.  **사용자가 인증서 해지 목록 (CRL)을 얻을 수 있는 위치를 지정**, 를 클릭 하 여 **추가**합니다. **위치 추가** 대화 상자가 열립니다.  
  
8.  **위치 추가**,  **위치**, 형식 `file://\\pki.corp.contoso.com\pki\<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, 를 클릭 하 고 **확인**합니다. CA 속성 대화 상자로 돌아갑니다.  
  
9. 에 **확장** 탭에서 다음 확인란을 선택 합니다.  
  
    -   **이 위치에 Crl 게시**  
  
    -   **이 위치에 델타 Crl을 게시 합니다.**  
  
10. 변경 **확장을 선택** 에 **액세스 AIA (기관 정보)** , 및는 **사용자가 인증서 해지 목록 (CRL)을 얻을 수 있는 위치를 지정**, 다음을 수행 합니다.  
  
    1.  경로로 시작 하는 항목을 선택 `ldap:///CN=<CATruncatedName>,CN=AIA,CN=Public Key Services`, 를 클릭 하 고 **제거**합니다. **제거 확인**, 클릭 **예**합니다.  
  
    2.  항목을 선택 `http://<ServerDNSName>/CertEnroll/<ServerDNSName>_<CaName><CertificateName>.crt`, 를 클릭 하 고 **제거**합니다. **제거 확인**, 클릭 **예**합니다.  
  
    3.  항목을 선택 `file://\\<ServerDNSName>\CertEnroll\<ServerDNSName><CaName><CertificateName>.crt`, 를 클릭 하 고 **제거**합니다. **제거 확인**, 클릭 **예**합니다.  
  
11. **사용자가이 CA에 대 한 인증서를 얻을 수 있는 위치 지정**에서 **추가**를 클릭 합니다. **위치 추가** 대화 상자가 열립니다.  
  
12. **위치 추가**,  **위치**, 형식 `http://pki.corp.contoso.com/pki/<ServerDNSName>_<CaName><CertificateName>.crt`, 를 클릭 하 고 **확인**합니다. CA 속성 대화 상자로 돌아갑니다.  
  
13. 에 **확장** 탭을 **에 발급 된 인증서의 AIA 포함**합니다.  
  
14. 를 Active Directory 인증서 서비스를 다시 시작 하 라는 메시지가 나타나면 클릭 **No**합니다. 나중에 서비스를 다시 시작 됩니다.  
  

