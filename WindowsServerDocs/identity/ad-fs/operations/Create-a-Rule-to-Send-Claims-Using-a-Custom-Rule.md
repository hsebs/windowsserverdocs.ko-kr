---
ms.assetid: 38eb3726-e97b-484e-9926-67e8a046b0c5
title: 사용자 지정 규칙을 사용하여 클레임을 보내도록 규칙 만들기
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 81a1fbbd703a5d452c437b089b822e227f55af82
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816696"
---
# <a name="create-a-rule-to-send-claims-using-a-custom-rule"></a>사용자 지정 규칙을 사용하여 클레임을 보내도록 규칙 만들기


Active Directory Federation Services (AD FS)에서 **사용자 지정 규칙 템플릿을 사용 하 여 클레임 보내기** 를 사용 하 여 표준 규칙 템플릿이 조직의 요구 사항을 충족 하지 않는 상황에 대 한 사용자 지정 클레임 규칙을 만들 수 있습니다. 사용자 지정 클레임 규칙 클레임 규칙 언어 작성 되 고 그런 다음에 복사 해야는 **사용자 지정 규칙** 텍스트 상자는 규칙 집합에서 사용할 수 있습니다. 고급 규칙에 대 한 구문을 구성 하는 방법에 대 한 정보를 참조 하십시오. [클레임 규칙 언어의 역할](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)합니다.  
  
다음 절차를 사용 하 여 AD FS 관리 스냅인을 사용 하 여 클레임 규칙을 만들 수 있습니다\-에 있습니다.  
  
멤버 자격이 **관리자**, 또는 이와 동등한 로컬 컴퓨터에서 최소한이이 절차를 완료 합니다.  적절 한 계정을 사용 하는 방법에 대 한 세부 정보를 검토 하 고 그룹 구성원 자격 [로컬 및 도메인 기본 그룹](https://go.microsoft.com/fwlink/?LinkId=83477)합니다.



## <a name="to-create-a-rule-to-pass-through-or-filter-an-incoming-claim-on-a-relying-party-trust-in-windows-server-2016"></a>통과 또는 들어오는 클레임을 신뢰 당사자 트러스트 Windows Server 2016에서 필터링 하는 규칙을 만들려면 

1.  서버 관리자에서 클릭 **도구**, 를 선택한 다음 **AD FS 관리**합니다.  
  
2.  콘솔 트리에서 아래 **AD FS**, 클릭 **신뢰 당사자 트러스트**합니다. 
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG) 만들기 ![  
  
3.  오른쪽\-선택한 트러스트를 클릭 한 다음 클릭 **클레임 발급 정책 편집**합니다.
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG) 만들기 ![   
  
4.  에 **클레임 발급 정책 편집** 대화 상자의 **발급 변환 규칙** 클릭 **규칙 추가** 규칙 마법사를 시작 합니다. 
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG) 만들기 ![    

5.  에 **규칙 템플릿 선택** 페이지의 **클레임 규칙 템플릿**, 선택, **사용자 지정 규칙을 사용 하 여 클레임 보내기** 클릭 한 다음 확인 하 고 목록에서 **다음**합니다.  
규칙](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom3.PNG) 만들기 ![   
  
6.  에 **규칙 구성** 페이지의 **클레임 규칙 이름**, 이 규칙에 대 한 표시 이름을 입력 합니다. 아래에서 **사용자 지정 규칙**, 을 입력 하거나이 규칙에 대해 원하는 클레임 규칙 언어 구문에 붙여 넣습니다.  
규칙](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom4.PNG) 만들기 ![     

7.  **마침**을 클릭합니다.  
  
8.  에 **클레임 규칙 편집** 대화 상자를 클릭 **확인** 여 규칙을 저장 합니다.   
  
## <a name="to-create-a-rule-to-pass-through-or-filter-an-incoming-claim-on-a-claims-provider-trust-in-windows-server-2016"></a>통과 또는 Windows Server 2016에서 클레임 공급자 트러스트에 들어오는 클레임을 필터링 하는 규칙을 만들려면 
  
1.  서버 관리자에서 클릭 **도구**, 를 선택한 다음 **AD FS 관리**합니다.  
  
2.  콘솔 트리에서 아래 **AD FS**, 클릭 **클레임 공급자 트러스트**합니다. 
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG) 만들기 ![  
  
3.  오른쪽\-선택한 트러스트를 클릭 한 다음 클릭 **클레임 규칙 편집**합니다.
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG) 만들기 ![   
  
4.  에 **클레임 규칙 편집** 대화 상자의 **수용 변환 규칙** 클릭 **규칙 추가** 규칙 마법사를 시작 합니다.
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG) 만들기 ![    

5.  에 **규칙 템플릿 선택** 페이지의 **클레임 규칙 템플릿**, 선택, **사용자 지정 규칙을 사용 하 여 클레임 보내기** 클릭 한 다음 확인 하 고 목록에서 **다음**합니다.  
규칙](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom3.PNG) 만들기 ![   
  
6.  에 **규칙 구성** 페이지의 **클레임 규칙 이름**, 이 규칙에 대 한 표시 이름을 입력 합니다. 아래에서 **사용자 지정 규칙**, 을 입력 하거나이 규칙에 대해 원하는 클레임 규칙 언어 구문에 붙여 넣습니다.  
규칙](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom4.PNG) 만들기 ![     

7.  **마침**을 클릭합니다.  
  
8.  에 **클레임 규칙 편집** 대화 상자를 클릭 **확인** 여 규칙을 저장 합니다.   

















   
  
## <a name="to-create-a-rule-to-send-claims-by-using-a-custom-claim-in-windows-server-2012-r2"></a>Windows Server 2012 r 2에서 사용자 지정 클레임을 사용 하 여 클레임을 보내도록 규칙을 만들려면 
  
1.  서버 관리자에서 클릭 **도구**, 를 클릭 하 고 **AD FS 관리**합니다.  
  
2.  콘솔 트리에서 **AD FS\\트러스트 관계**, 클릭 **클레임 공급자 트러스트** 또는 **신뢰 당사자 트러스트**, 이 규칙을 만드는 목록에서 특정 트러스트를 클릭 하 고 있습니다.  
  
3.  오른쪽\-선택한 트러스트를 클릭 한 다음 클릭 **클레임 규칙 편집**합니다.  
규칙](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG) 만들기 ![ 
  
4.  에 **클레임 규칙 편집** 대화 상자에서 하나를 선택 했는지에 따라 편집 하는 규칙 수를 설정 하는 신뢰 하는 다음과 같은 탭이이 규칙을 만들고 연결할 클릭 **규칙 추가** 해당 규칙 집합에 연관 된 규칙 마법사를 시작 합니다.  
  
    -   **수락 변환 규칙**  
  
    -   **발급 변환 규칙**  
  
    -   **발급 권한 부여 규칙**  
  
    -   **위임 권한 부여 규칙**  
규칙](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG) 만들기 ![
  
5.  에 **규칙 템플릿 선택** 페이지의 **클레임 규칙 템플릿**, 선택, **사용자 지정 규칙을 사용 하 여 클레임 보내기** 클릭 한 다음 확인 하 고 목록에서 **다음**합니다.  
규칙](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom1.PNG) 만들기 ![   
  
6.  에 **규칙 구성** 페이지의 **클레임 규칙 이름**, 이 규칙에 대 한 표시 이름을 입력 합니다. 아래에서 **사용자 지정 규칙**, 을 입력 하거나이 규칙에 대해 원하는 클레임 규칙 언어 구문에 붙여 넣습니다.  
규칙](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom2.PNG) 만들기 ![     

7.  **마침**을 클릭합니다.  
  
8.  에 **클레임 규칙 편집** 대화 상자를 클릭 **확인** 여 규칙을 저장 합니다.  

## <a name="additional-references"></a>추가 참조 
[클레임 규칙 구성](Configure-Claim-Rules.md)  
 
[검사 목록: 신뢰 당사자 트러스트에 대 한 클레임 규칙 만들기](https://technet.microsoft.com/library/ee913578.aspx)  

[검사 목록: 클레임 공급자 트러스트에 대 한 클레임 규칙 만들기](https://technet.microsoft.com/library/ee913564.aspx)  
  
[권한 부여 클레임 규칙을 사용 하는 경우](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)  

[클레임의 역할](../../ad-fs/technical-reference/The-Role-of-Claims.md)  
  
[클레임 규칙의 역할](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md) 
