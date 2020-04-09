---
ms.assetid: 10d6723e-c857-43da-9d2d-acb5641d3da8
title: 도메인에 컴퓨터 가입
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 174f585f3e156fc8e068b9300fc90a20a67869cf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855356"
---
# <a name="join-a-computer-to-a-domain"></a>도메인에 컴퓨터 가입

Active Directory Federation Services \(AD FS\) 작동 하려면 페더레이션 서버 역할을 하는 각 컴퓨터가 도메인에 가입 되어 있어야 합니다. 페더레이션 서버 프록시는 도메인에 가입할 수 있지만 반드시 그럴 필요는 없습니다.  
  
웹 서버가 클레임\-인식 응용 프로그램만 호스트 하는 경우 웹 서버를 도메인에 가입 시킬 필요가 없습니다.  
  
이 절차를 완료하려면 최소한 로컬 컴퓨터의 **Administrators** 구성원 자격 또는 동급의 권한이 필요합니다.  적절 한 계정을 사용 하는 방법에 대 한 세부 정보를 검토 하 고 그룹 구성원 자격 [로컬 및 도메인 기본 그룹](https://go.microsoft.com/fwlink/?LinkId=83477)합니다.   
  
### <a name="to-join-a-computer-to-a-domain"></a>도메인에 컴퓨터를 가입 시키려면  
  
1.  **시작** 화면에서 **제어판**을 입력 한 다음 enter 키를 누릅니다.  
  
2.  **시스템 및 보안**으로 이동 하 고 **시스템**을 클릭 합니다.  
  
3.  **컴퓨터 이름, 도메인 및 작업 그룹 설정**에서 **설정 변경**을 클릭합니다.  
  
4.  **컴퓨터 이름** 탭에서 **변경**을 클릭합니다.  
  
5.  **소속 그룹**아래에서 **도메인**을 클릭 하 고이 컴퓨터를 가입 시킬 도메인의 이름을 입력 한 다음 **확인**을 클릭 합니다.  
  
6.  **확인**을 클릭한 다음 컴퓨터를 다시 시작합니다.  
  
## <a name="additional-references"></a>추가 참조  
[검사 목록: 페더레이션 서버 설정](Checklist--Setting-Up-a-Federation-Server.md)  
  
[검사 목록: 페더레이션 서버 프록시 설정](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  

