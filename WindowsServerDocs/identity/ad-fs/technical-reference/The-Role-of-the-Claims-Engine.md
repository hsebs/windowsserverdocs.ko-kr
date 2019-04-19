---
ms.assetid: 8b15d44e-e4e6-4510-aa91-cc7ec7161b0a
title: "클레임 엔진 역할"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 930b6f8034f17d8902104419042f944b82e90b4f
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2017
---
>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

# <a name="the-role-of-the-claims-engine"></a>클레임 엔진 역할
최고 수준의 Active Directory Federation Services \(AD FS\) 클레임 엔진은 rule\ 기반 엔진 전담 Federation 서비스에 대 한 청구 요청을 처리 하는입니다. 클레임 엔진 모든 구성한 경우 연결 된 보안 관계 각 규칙 집합을 실행 하 고 클레임 파이프라인 출력 결과 통해 전달 담당 하는 Federation 서비스 내의 단독 엔터티입니다.  
  
클레임 파이프라인은의 더 많은 논리 개념 동안 end\ to\ 엔드 프로세스 흐르는 대 한 주장 클레임 규칙은 실제 관리 요소 클레임 규칙 실행 프로세스 동안 클레임 흐름을 사용자 지정 하는 데 사용할 수 있는 합니다. 파이프라인 프로세스에 대 한 자세한 내용은 참조 [클레임 파이프라인 The 역할](The-Role-of-the-Claims-Pipeline.md)합니다.  
  
다음 그림에서는 수신 클레임 \(acceptance rules\) 수락 하는 작업에에서 표시 된 대로 클레임 승인 요청 \(authorization rules\) 고 발급 보내는 클레임 모든 조직에서 연결 된 보안 관계 클레임 규칙을 통해 \(issuance rules\) 클레임 엔진에서 실행 됩니다.  
  
![광고 FS 역할](media/adfs2_enginepipeline.gif)  
  
## <a name="claim-rules-execution-process"></a>클레임은 규칙 실행 프로세스  
구성 하는 경우 청구 공급자 신뢰 또는 당사자 신뢰 클레임 규칙 조직, 해당 신뢰 행위에 대 한 청구 규칙 set\(s\) 들어오는 청구에 대 한 키퍼도 클레임 엔진 필요한 논리를 발급 주장 하는 클레임을 실행할 것인지 결정 클레임 규칙의 적용을 호출 하 여 합니다.  
  
다음 섹션에서는 엔진에서 클레임 규칙 실행 프로세스를 통해 클레임 흐름 하는 동안 발생 하는 단계에 설명 합니다. 각 단계 아래에 설명 된 대로 발생 청구 파이프라인 프로세스에 설명 된 각 단계에 있습니다. 이러한 단계는 다음과 같습니다.  
  
-   1 단계 – 초기화  
  
-   2 단계-실행  
  
-   3 단계-실행 결과  
  
파이프라인 프로세스에 대 한 자세한 내용은 참조 [클레임 파이프라인 The 역할](The-Role-of-the-Claims-Pipeline.md)합니다.  
  
### <a name="step-1--initialization"></a>1 단계 – 초기화  
클레임 엔진을 첫 번째 추가 하 여 수신 클레임 수락 클레임 규칙 실행 프로세스의 첫 번째 단계에서는 *입력 개인 설정*합니다. 입력된 클레임 집합은 일시적으로으로 필요한 프로세스 검색 하기 위해 사용할 수 있도록 해당 데이터가 필요 데이터를 저장 하는 데 사용 하는 메모리의 캐시 유사 합니다. 입력된 클레임 설정 데이터 규칙 실행 완료 된 후 삭제 됩니다.  
  
#### <a name="adding-a-claim-to-the-input-claim-set-for-a-rule-set"></a>클레임 입력 클레임 규칙 집합에 대 한 설정 추가  
입력된 청구 집합 관련 된 청구 규칙 집합 논리를 처리 하는 동안 클레임 데이터 메모리에 일시적으로 저장 하는 데 필요한 경우 클레임 엔진에서 작성 됩니다. 클레임 엔진 모든 들어오는 클레임 첫 번째 규칙 규칙 집합에 검색할 수 입력된 클레임 집합을 복사 합니다.  
  
예를 들어 A 클레임 읽고 클레임 엔진 그림 아래에서 들어오는에서 B 주장 입력된 클레임 집합에 복사 합니다. 클레임 입력된 설정에는 후 클레임 엔진을 검색 하 고 첫 번째 청구 규칙 집합에 규칙에서 논리가 입력으로 클레임 A 하 고 B 처리 합니다.  
  
![광고 FS 역할](media/adfs2_context1.gif)  
  
모든 규칙 클레임 규칙 집합에 동일한 입력된 청구 집합을 공유 합니다. 각 규칙 해당 설정에는 설정의 모든 이후 규칙 영향을 공유 입력된 클레임 설정에 추가할 수 있습니다.  
  
### <a name="step-2--execution"></a>2 단계-실행  
이 단계는 클레임 규칙 프로세스 클레임 규칙 클레임 엔진 시간을 단계별로 모든 규칙 하나 특정 규칙 설정 내에서 한 번에 때 처리 됩니다. 규칙 설정 내에서 각 규칙만 한 번 실행 되 고 나타나는 위쪽에서 아래로 클레임 규칙 편집 대화 상자에서 snap\ AD FS 관리에서에 표시 된 대로 순서 대로 실행 됩니다. 클레임은 규칙 규칙의 위쪽에 설정 된 먼저 처리 되 고 모든 규칙 실행 될 때까지 다음 규칙 처리 됩니다.  
  
클레임 규칙 언어에 정의 된 대로 클레임 규칙 이루어져 두 부분을 조건 및 발급 문의 합니다. 입력에서 데이터를 사용 하 여 조건 일부 주장 규칙 내에 지정 된 조건을 입력에 포함 된 청구에 대 한 마찬가지 있는지 여부를 확인 하려면 설정 청구 엔진 첫 번째 프로세스 주장 설정 \ (규칙의 상태와 일치 하는 클레임 라고 일치 하는 claims\). 일치 하는 클레임 발견 되 면 일치 하는 클레임 각 설정에 대 한 규칙의 발급 문을 클레임 엔진에서 실행 됩니다. 규칙의 발급 문을 클레임 일치 하는 다음 작업 중 하나를 수행할 수 있습니다.  
  
1.  일치 하는 클레임 출력 클레임 집합에 복사  
  
2.  클레임 필드 변환 하 고 새 클레임 중 하나에 입력된 클레임 설정 하면 만들거나 평가 및 출력 주장 설정 합니다.  
  
3.  새 claim\(s\) 중 하나에 입력된 클레임 설정 하면 만들거나 주장 설정에서 입력 및 출력 특성 스토어에서 더 많은 정보를 찾는 일치 하는 claim\(s\) 키로 사용 합니다.  
  
#### <a name="adding-a-claim-to-the-output-claim-set-for-a-rule-set"></a>클레임 출력 클레임 규칙 집합에 대 한 설정 추가  
*출력 주장 설정* 메모리에 저장 처음 비어 있는 클레임 엔진만 실행 프로세스를 완료 한 후 설정 출력 클레임에 있는 클레임 반환 때문에 중요 한 위치입니다. 즉, 입력된 클레임에만 있는 클레임 설정 하 고 출력 청구 집합에 없는 경우 무시 됩니다 시간을 보내는 클레임 최종 집합이 계산 제공 합니다.  
  
#### <a name="adding-a-claim-to-both-claim-sets-for-a-rule-set"></a>모두 클레임 집합을 클레임 규칙 집합에 대 한 추가  
규칙을 처리 하는 주장 설정 또는 설정 주장 모두 입력에 및 규칙의 발급 취급 방침에서 사용 되는 정책에 따라 클레임 설정 출력 입력에 추가 하거나 클레임은입니다. 클레임은 규칙 언어 중 하나에 따라 이러한 문을 가리킵니다 *추가* 또는 *문제*합니다.  
  
하는 경우는 *추가* 문을 사용 클레임 입력된 청구 집합에만에 추가 되 고 클레임 실행 목적 으로만 있 및 실행 완료 되 면 존재 작동이 중단 됩니다. 하는 경우는 *문제* 문을 사용 클레임 입력된 클레임 일련 및 출력 클레임 설정에 추가 되 고 클레임 출력 클레임 실행 완료 되 면 설정에서 반환 됩니다. 이 취급 방침에 대 한 자세한 내용은 참조 [클레임 규칙 언어의 The 역할](The-Role-of-the-Claim-Rule-Language.md)합니다.  
  
규칙 집합 내 규칙의 조건이 포함 입력된 청구 집합에 클레임와 일치 하지 않는 경우 규칙의 발급 문을 일부 무시 되 고 출력 클레임 설정 하거나 입력된 클레임 집합 어떠한 보증도 따라서 추가 됩니다. 다음 그림와 해당 단계 표시 변환 규칙 클레임 엔진에서 실행 하는 경우:  
  
![광고 FS 역할](media/adfs2_context2.gif)  
  
1.  들어오는 클레임 클레임 엔진에서 설정 입력된 클레임에 추가 됩니다.  
  
2.  첫 번째 규칙 실행 되 면 해당 시점 입력에만 클레임 주장 설정에서에서는 B 클레임 보 고 조건부 부분 규칙 1 규칙 논리 처리 합니다.  
  
3.  터무니 규칙의 상태에 따라 결정 됩니다 A 클레임 입력된 청구 집합에 이므로 \ (클레임 A\ 일치) 모두 입력 개인 설정 하 고 출력 주장 설정 새 C 클레임 추가 됩니다.  
  
4.  2 규칙 이제 A, B 및 C 청구를 사용할 수 \ (입력에 대 한 모든 클레임 set\ 주장)는 논리 처리에 대해 입력으로 합니다.  
  
클레임 변환에 대 한 자세한 내용은 참조 [변환 클레임 규칙을 사용 하는 경우](When-to-Use-a-Transform-Claim-Rule.md)합니다.  
  
### <a name="step-3--execution-result"></a>3 단계-실행 결과  
클레임은 규칙 설정 실행의 마지막 단계 모든 규칙 해당된 규칙 설정 내에서 실행 하 고 최종 청구 집합은 출력 청구 집합에 시작 됩니다. 이 시점 클레임 엔진 규칙 집합 실행 출력으로 설정 출력 클레임 컨텍스트를 반환 합니다. 앞으로 계속에서 클레임 파이프라인 맡습니다 최종 출력이 프로세스의 다음 단계로 이동 하는 것이 있습니다.  
  
## <a name="sending-the-execution-output-to-the-claims-pipeline"></a>클레임 파이프라인 실행 출력 전송  
클레임은 engine 프로세스 규칙 집합에 입력에 대 한 메모리에는 자체 전용된 위치 및 출력 주장 설정 규칙을 설정 합니다. 즉, 입력 및 출력 주장 설정 사용 규칙 하나 설정 하는 별도 입력에서 되며 출력 주장 규칙의 다른 세트에 사용 되는 설정입니다.  
  
Give 규칙 집합에 대 한 전체 프로세스를 실행 한 후 \ (1, 2 및 3\ 단계) 새로 발급된 보내는 클레임 \ (출력 클레임 set\ 콘텐츠) 다음 규칙 클레임 파이프라인 집합에 입력으로 사용 됩니다. 클레임은 예시와 같이 다른 규칙 설정에 대해 입력으로 설정 하나의 규칙 출력에서 진행을 수 있습니다.  
  
![광고 FS 역할](media/adfs2_enginecontexts.gif)  
  
> [!NOTE]  
> 발급 규칙 집합 파이프라인의 중요 한 단계 수도 있지만 위의 그림 나타나지 않습니다 그림을 간소화 하는 용도로 합니다. 발급 규칙 설정 및 클레임 파이프라인에 표시 하는 그림을 참조 하세요. [클레임 파이프라인 The 역할](The-Role-of-the-Claims-Pipeline.md)합니다.  
  
이 경우 수용 규칙 출력 파이프라인 하 여 최종 청구 2 단계 인증 규칙 처리 파이프라인에서을 수락 규칙에서 생성 된 집합을 사용 됩니다. 이제는 전체 청구 규칙 실행 프로세스 \ (1, 2, 3 단계 above\)는 인증 집합에 대 한 다시 실행 됩니다. 이 주기 발급 규칙 설정할 때까지 계속 \ (pipeline\는 최종 단계) 완료 되었습니다.  
  
완성 된 보내는 클레임 발급 규칙 집합에 대 한 엔진에서 반환 된 후 SAML 토큰 패키지 됩니다 및 Federation 서비스는 토큰 클라이언트도 다시 보냅니다.  
  
## <a name="processing-authorization-rules"></a>처리 인증 규칙  
2 단계는 클레임 규칙 실행 프로세스 실행 되는 클레임 규칙 집합 인증 규칙 구성 하는 경우 \ (있는 사용 하는 다른 입력과 수용 또는 발급 rules\ 보다 설정 주장 출력) 다음 토큰 요청 자가 보안 토큰 연합 서비스에서 지정된 당사자 요청 자가 클레임에 따라에 대 한 얻을 수 있는 권한이 있는지 확인 하려면 해당 인증 규칙 실행 됩니다.  
  
문제를 허용 하거나 클레임 여부를 토큰 지정된 당사자에 대 한 얻는 허용 하는 사용자가 있는지 여부에 따라 거부 인증 규칙의 목표가입니다. 다음 그림와 같이 인증 실행 출력 파이프라인은 데 사용 됩니다 발급 규칙 집합 실행 여부를 결정-허용 and\의 존재 여부에 따라 / 또는 클레임 거부-자체 인증 실행 출력 입력 클레임 규칙 집합으로 사용 되지 않습니다.  
  
![광고 FS 역할](media/adfs2_authorization.gif)  
  
청구 인증에 대 한 자세한 내용은 참조 [승인 클레임 규칙을 사용 하는 경우](When-to-Use-an-Authorization-Claim-Rule.md)합니다.  
  
