---
ms.assetid: 475e34f9-9399-43f4-a840-9dd77258e11a
title: "클레임으로 보내기 그룹 구성원에 규칙 만들기"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: d4fb03de9de2dcca36b18ce089db11ed599de820
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2017
---
# <a name="create-a-rule-to-send-group-membership-as-a-claim"></a>클레임으로 보내기 그룹 구성원에 규칙 만들기

>적용 대상: Windows Server 2016, Windows Server 2012 r 2

보내기 그룹 구성원 Active Directory Federation Services \(AD FS\) 클레임 규칙 템플릿으로 사용 하는 수 있도록 클레임 파일로 보낼 Active Directory 보안 그룹 선택할 수 규칙을 만들 수 있습니다. 선택한 그룹에 따라이 규칙에서 하나의 클레임 에서만 발생 합니다. 예를 들어, 사용자가 도메인 관리자 보안 그룹의 회원 그룹 클레임 관리자 값을 보낼 규칙을 만들려면이 규칙 템플릿을 사용할 수 있습니다. 이 규칙 로컬 Active Directory 도메인에 있는 사용자에 대해서만 사용 해야 합니다.  
  
다음 절차 규칙을 만들려면 클레임 AD FS 관리 snap\에서 사용할 수 있습니다.  
  
회원 **관리자**, 로컬 컴퓨터에서 해당 하는이 절차를 수행 하는 데 필요한 최소 또는 합니다.  해당 계정을 사용에 대 한 세부 정보를 검토 및 그룹 구성원에 [로컬와 도메인 기본 그룹](https://go.microsoft.com/fwlink/?LinkId=83477)합니다.   

## <a name="to-create-a-rule-to-send-group-membership-as-a-claim-on-a-relying-party-trust-in-windows-server-2016"></a>그룹 구성원에 의존 파티 신뢰 Windows Server 2016에 클레임 파일로 보낼 규칙을 만들려면 

1.  서버 관리자 클릭 **도구**를 선택한 다음 **AD FS 관리**합니다.  
  
2.  콘솔 트리에서 **ADFS**, 클릭 **파티 신뢰 의존**합니다. 
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)  
  
3.  선택한 신뢰 Right\ 클릭 하 고 다음 클릭 **클레임 발급 정책 편집**합니다.
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG)   
  
4.  에 **클레임 발급 정책 편집** 대화 상자의 **발급 변환 규칙** 클릭 **규칙 추가** 규칙 마법사를 시작 합니다. 
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG)    

5.  에 **규칙 템플릿 선택** 페이지의 **클레임 규칙 서식**선택 **클레임으로 그룹 구성원 보내기** 목록에서 **다음**합니다.  
![규칙 만들기](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group3.PNG)      

6.   에 **구성 규칙** 페이지에서 **클레임 규칙 이름** 이 규칙의 표시 이름을 입력 **사용자의 그룹** 클릭 **찾아보기** 선택한 그룹에서 **보내는 클레임 유형** 원하는 클레임 유형을 선택 선택한 다음 **발신 주장 유형** 값을 입력 합니다.
![규칙 만들기](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group4.PNG)   

7.  클릭 하 고 **완료** 단추.  
  
8.  **편집 클레임 규칙** 대화 상자를 클릭 **확인** 규칙을 저장 해야 합니다.
  
## <a name="to-create-a-rule-to-to-send-group-membership-as-a-claim-on-a-claims-provider-trust-in-windows-server-2016"></a>Windows Server 2016에 클레임 공급자 신뢰에 클레임으로 그룹 구성원을 보낼 수에 규칙을 만들려면 
  
1.  서버 관리자 클릭 **도구**를 선택한 다음 **AD FS 관리**합니다.  
  
2.  콘솔 트리에서 **ADFS**, 클릭 **클레임 공급자 신뢰**합니다. 
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG)  
  
3.  선택한 신뢰 Right\ 클릭 하 고 다음 클릭 **편집 클레임 규칙**합니다.
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG)   
  
4.  에 **편집 클레임 규칙** 대화 상자의 **수용 변환 규칙** 클릭 **규칙 추가** 규칙 마법사를 시작 합니다.
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG)    

5.  에 **규칙 템플릿 선택** 페이지의 **클레임 규칙 서식**선택 **클레임으로 그룹 구성원 보내기** 목록에서 **다음**합니다.  
![규칙 만들기](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group3.PNG)     

6.   에 **구성 규칙** 페이지에서 **클레임 규칙 이름** 이 규칙의 표시 이름을 입력 **사용자의 그룹** 클릭 **찾아보기** 선택한 그룹에서 **보내는 클레임 유형** 원하는 클레임 유형을 선택 선택한 다음 **발신 주장 유형** 값을 입력 합니다. 
![규칙 만들기](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group4.PNG)      

7.  클릭 하 고 **완료** 단추.  
  
8.  **편집 클레임 규칙** 대화 상자를 클릭 **확인** 규칙을 저장 해야 합니다.  




  
## <a name="to-create-a-rule-to-send-group-membership-as-a-claim-in-windows-server-2012-r2"></a>Windows Server 2012 r 2에서 클레임으로 그룹 구성원을 보내려면 규칙을 만들려면 
  
1.  서버 관리자 클릭 **도구**를 선택한 다음 **AD FS 관리**합니다.  
  
2.  콘솔 트리에서 아래에서 **광고 FS\\Trust 관계**, 클릭 **클레임 공급자 신뢰** 또는 **의존 파티 신뢰**, 클릭 한 다음이 규칙 만들려는 목록에 특정 신뢰 하 고 합니다.  
  
3.  선택한 신뢰 Right\ 클릭 하 고 다음 클릭 **편집 클레임 규칙**합니다.
![규칙 만들기](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG)  
  
4.  에 **클레임 규칙 편집** 대화 상자에서 하나 다음 탭, 보안 편집 하는 및 규칙을 설정에 따라를 만들려면이 규칙을 선택한 다음 **규칙 추가** 해당 규칙 집합와 연결 된 규칙 마법사를 시작 합니다.  
  
    -   **승인 변환 규칙**  
  
    -   **발급 변환 규칙**  
  
    -   **발급 승인 규칙**  
  
    -   **위임 인증 규칙**  
![규칙 만들기](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG)
    
5.  에 **규칙 템플릿 선택** 페이지의 **클레임 규칙 서식**선택 **클레임으로 그룹 구성원 보내기** 목록에서 **다음**합니다.  
![규칙 만들기](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group1.PNG)

6.  에 **구성 규칙** 페이지에서 **클레임 규칙 이름** 이 규칙의 표시 이름을 입력 **사용자의 그룹** 클릭 **찾아보기** 선택한 그룹에서 **보내는 클레임 유형** 원하는 클레임 유형을 선택 선택한 다음 **발신 주장 유형** 값을 입력 합니다.  
![규칙 만들기](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group2.PNG)  

7.  클릭 **완료**합니다.  
  
8.  **편집 클레임 규칙** 대화 상자를 클릭 **확인** 규칙을 저장 해야 합니다.  



## <a name="additional-references"></a>추가 참조 
[클레임은 규칙 구성](Configure-Claim-Rules.md)  
 
[검사: 신뢰 파티 보안에 대 한 청구 규칙 만들기](https://technet.microsoft.com/library/ee913578.aspx)  

[청구 공급자에 대 한 청구 규칙 만들기 신뢰 검사:](https://technet.microsoft.com/library/ee913564.aspx)  
  
[승인 클레임 규칙을 사용 하는 경우](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)  

[클레임 역할](../../ad-fs/technical-reference/The-Role-of-Claims.md)  
  
[클레임은 규칙의 역할](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md) 