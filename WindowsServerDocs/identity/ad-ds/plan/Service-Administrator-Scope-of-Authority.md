---
ms.assetid: da7b6dcf-53ec-4394-88c0-c087d92f3893
title: "관리자 서비스 범위를"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: ba682067b9c7a7b4bf583482abe6470b60b25450
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2017
---
# <a name="service-administrator-scope-of-authority"></a>관리자 서비스 범위를

>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

된 Active Directory 숲 속의 참여 하도록 선택 하면 숲 소유자와 서비스 관리자 신뢰 해야 합니다. 숲 소유자는 선택 및 서비스 관리자; 관리 담당 따라서 숲 소유자 신뢰 하는 경우 신뢰할 수 숲 소유자 관리 하는 서비스 관리자입니다. 이러한 서비스 관리자는 숲에서 모든 리소스에 액세스할 수 있습니다. 이 숲 참여 결정을 하기 전에 숲 소유자 기능 및 서비스 관리자는 사용자의 데이터에 대 한 전체 액세스 이해 중요 합니다. 이 액세스할 수 없습니다.  
  
모든 서비스 관리자에 숲 속의 모든 권한이 모든 데이터와 서비스를 통해 모든 컴퓨터에는 숲 속의 합니다. 서비스 관리자는 다음을 수행 하는 기능이 있습니다.  
  
-   액세스 제어 목록 (Acl)의 개체 오류를 수정 합니다. 이렇게 하면 서비스 관리자 읽기 수정 또는 삭제 이러한 물체에서 설정 Acl와 상관 없이 개체에 있습니다.  
  
-   정상 보안 검사를 무시 하는 도메인 컨트롤러에서 시스템 소프트웨어를 수정 합니다. 이렇게 하면 서비스 관리자 보거나 ACL 개체에 관계 없이 도메인에 있는 개체 조작할 수 있습니다.  
  
-   제한 된 그룹 보안 정책을 사용 하 여 모든 사용자 또는 그룹 관리에 대 한 액세스 도메인에 연결 된 컴퓨터에 권한을 부여 합니다. 이러한 방식으로 서비스 관리자는 컴퓨터 소유자의 의도 관계 없이 도메인에 연결 된 컴퓨터를 제어를 얻을 수 있습니다.  
  
-   암호를 재설정 하거나 사용자를 위한 그룹 구성원을 변경 합니다.  
  
-   도메인 컨트롤러에서 시스템 소프트웨어를 수정 하 여 다른 숲 도메인에 액세스할을 수 있습니다. 서비스 관리자 수 작업 보기 숲 속의 모든 도메인에 영향 또는 조작 숲 구성 데이터, 또는 모든 도메인에 저장 된 데이터를 조작 및 보기 보거나 숲 연결 된 컴퓨터에 저장 된 데이터를 조작 합니다.  
  
이러한 이유로 가입 컴퓨터를 숲을 서비스 관리자 사항이 있는지와 조직 (Ou)는 숲 속의 데이터를 저장 하는 그룹입니다. 참가 숲 그룹에 대 한는 숲 속의 모든 서비스 관리자 신뢰 하도록 선택 해야 합니다. 이 포함 되도록 됩니다.  
  
-   숲 소유자 그룹의 관심사에 행동을 신뢰할 수 있고 그룹에 위해 이유 없습니다.  
  
-   숲 소유자 적절 하 게 도메인 컨트롤러에 물리적 액세스를 제한합니다. 숲에 내 도메인 컨트롤러 서로 격리 수 없습니다. 디렉터리 데이터베이스 하며 이렇게 하면 오프 라인 변경할 보기 숲 속의 된 도메인의 작동을 방해할 또는 숲 속의 곳에 저장 된 데이터를 조작 및 보기 또는 숲 연결 된 컴퓨터에 저장 된 데이터를 조작 단일 도메인 컨트롤러에 액세스할 수 있는 공격자에 대 한 것 같습니다. 이러한 이유로 도메인 컨트롤러에 대 한 액세스 물리적 신뢰할 수 있는 직원 제한 해야 합니다.  
  
-   이해 하 고 서비스 관리자에 시스템의 보안에 영향을 미치지 강제 수 신뢰할 수 있는 잠재적 위험에 동의 합니다.  
  
일부 그룹 공유 인프라에 참여의 공동 작업 하 고 비용 절약 이점이 된 서비스 관리자 오용는 오용 자신의 기관에으로 강제 위험 보다 중요를 결정할 수 있습니다. 이러한 그룹을 숲 공유 하 고 Ou 권한을 위임를 사용 하 여 수 있습니다. 그러나 다른 그룹 수 결과에서 보안 공격 너무 심각 때문에이 위험을 접수 하지 않습니다. 이러한 그룹 별도 숲 필요합니다.  
  

