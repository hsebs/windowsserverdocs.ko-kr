---
ms.assetid: ab97948a-c434-48f2-8313-c1a7a518e5f7
title: 독립 실행형 페더레이션 서버 만들기
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 603786d8553cce20f0b559ba8a91dfc29f760488
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855486"
---
# <a name="create-a-stand-alone-federation-server"></a>독립 실행형 페더레이션 서버 만들기

페더레이션 서비스 역할 서비스를 설치 하 고 컴퓨터에 필요한 인증서를 구성 하 고 나면 컴퓨터가 페더레이션 서버가 되도록 구성할 준비가 된 것입니다. 다음 절차를 사용 하 여 독립 실행형\-단독 페더레이션 서버가 되도록 컴퓨터를 설정할 수 있습니다. 독립\-단독 페더레이션 서버를 만드는 작업은 새 페더레이션 서비스을 만듭니다. AD FS 페더레이션 서버 구성 마법사를 사용 하 여 페더레이션 서버를 만듭니다.  
  
> [!NOTE]  
> \(SSO\) 디자인에서 페더레이션된 웹 Single\-Sign\-의 경우 계정 파트너 조직에 하나 이상의 페더레이션 서버가 있어야 하 고 리소스 파트너 조직의 페더레이션 서버는 하나 이상 있어야 합니다. 자세한 내용은 [페더레이션 서버 배치 위치](https://technet.microsoft.com/library/dd807127.aspx)를 참조하세요.  
  
이 절차를 완료하려면 최소한 로컬 컴퓨터의 **Administrators** 구성원 자격 또는 동급의 권한이 필요합니다.  [로컬 및 도메인 기본 그룹](https://go.microsoft.com/fwlink/?LinkId=83477) 에서 적절 한 계정 및 그룹 구성원 자격 사용에 대 한 세부 정보를 검토 \(http:\/\/go.microsoft.com\/fwlink\/? LinkId\=83477\).   
  
### <a name="to-create-a-stand-alone-federation-server"></a>독립\-단독 페더레이션 서버를 만들려면  
  
1.  AD FS 페더레이션 서버 구성 마법사는 두 가지 방법으로 시작할 수 있습니다. 마법사를 시작하려면 다음 중 하나를 수행합니다.  
  
    -   페더레이션 서비스 역할 서비스 설치가 완료 되 면에서 AD FS 관리 스냅인\-열고 **개요** 페이지 또는 **작업** 창에서 **페더레이션 서버 구성 마법사 AD FS** 링크를 클릭 합니다.  
  
    -   설치 마법사가 완료 되 면 언제 든 지 Windows 탐색기를 열고 **C:\\windows\\ADFS** 폴더로 이동한 후 **fsconfigwizard .exe**를 두 번 클릭\-합니다.  
  
2.  **시작** 페이지에서 **새 페더레이션 서비스 만들기**가 선택되어 있는지 확인하고 **다음**을 클릭합니다.  
  
3.  **독립\-단독 또는 팜 배포 선택** 페이지에서 **독립\-단독 페더레이션 서버**를 클릭 한 후 **다음**을 클릭 합니다.  
  
    > [!IMPORTANT]  
    > AD FS 페더레이션 서버 구성 마법사에서 독립\-단독 페더레이션 서버 옵션을 선택 하면이 페더레이션 서비스와 연결 된 서비스 계정이 자동으로 네트워크 서비스 계정에 할당 됩니다. 네트워크 서비스를 서비스 계정으로 사용 하는 것은 테스트 랩 환경에서 AD FS를 평가 하는 경우에만 권장 됩니다. 독립\-단독 페더레이션 서버 옵션을 사용 하 여 프로덕션 환경에서 페더레이션 서버를 배포 하려는 경우이 새 페더레이션 서비스에 대 한 요청을 처리할 수 있는 더 적절 한 서비스 계정으로이 서비스 계정을 변경 하는 것이 중요 합니다. 서비스 계정을 NETWORK SERVICE 이외의 계정으로 변경 하면 페더레이션 서버가 악의적인 공격에 취약 해질 수 있는 공격 벡터가 완화 됩니다.  
  
4.  **페더레이션 서비스 이름 지정** 페이지에서 표시된 **SSL 인증서**가 올바른지 확인합니다. 그렇지 않은 경우 **SSL 인증서** 목록에서 적절 한 인증서를 선택 합니다.  
  
    이 인증서는 기본 웹 사이트에 대 한 SSL(Secure Sockets Layer) \(SSL\) 설정에서 생성 됩니다. 기본 웹 사이트에 SSL 인증서가 하나만 구성되어 있으면 해당 인증서가 표시되고 사용하도록 자동으로 선택됩니다. 기본 웹 사이트에 대해 여러 SSL 인증서가 구성되어 있으면 모든 인증서가 여기에 나열되므로 원하는 인증서를 선택해야 합니다. 기본 웹 사이트에 대해 구성된 SSL 설정이 없으면 로컬 컴퓨터의 개인 인증서 저장소에서 사용 가능한 인증서가 포함된 목록이 생성됩니다.  
  
    > [!NOTE]  
    > 이 마법사에서는 IIS에 대해 SSL 인증서가 구성된 경우 인증서 무효화를 허용하지 않습니다. 따라서 SSL 인증서에 대한 의도된 이전 IIS 구성이 모두 보존됩니다. 이 제한을 해결 하려면 IIS 관리 콘솔을 사용 하 여 인증서를 제거 하거나 수동으로 다시 구성 하면 됩니다.  
  
5.  선택한 AD FS 데이터베이스가 이미 있으면 **기존 AD FS 구성 데이터베이스가 검색됨** 페이지가 나타납니다. 이 경우 **데이터베이스 삭제**와 **다음**을 차례로 클릭합니다.  
  
    > [!CAUTION]  
    > 이 AD FS 데이터베이스의 데이터가 중요하지 않거나 프로덕션 페더레이션 서버 팜에서 사용되지 않는 것이 확실한 경우에만 이 옵션을 선택합니다.  
  
6.  **설정 적용 준비 완료** 페이지에서 세부 정보를 검토하고 설정이 올바르면 **다음**을 클릭하여 해당 설정으로 AD FS 구성을 시작합니다.  
  
7.  **구성 결과** 페이지에서 결과를 검토합니다. 모든 구성 단계가 완료되면 **닫기**  를 클릭하여 마법사를 종료합니다.  
  
## <a name="additional-references"></a>추가 참조  
[검사 목록: 페더레이션 서버 설정](Checklist--Setting-Up-a-Federation-Server.md)  
  

