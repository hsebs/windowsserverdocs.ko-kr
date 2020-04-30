---
ms.assetid: a91339ef-6ad4-445f-8ecc-a95fbcc04296
title: AD DS 디자인 및 계획
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/07/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 5f88458c8e3f50853229f6f8f9c74fa4b8feba40
ms.sourcegitcommit: 11421f4005f9f3a3f6c0db95b1836d0f765a9fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81624421"
---
# <a name="ad-ds-design-and-planning"></a>AD DS 디자인 및 계획

> 적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

사용자 환경에 Windows Server Active Directory Domain Services (AD DS)를 배포 하 여 AD DS에서 제공 하는 중앙 집중화 된 위임 된 관리 모델 및 SSO (Single Sign-On) 기능을 활용할 수 있습니다. 조직의 배포 작업 및 현재 환경을 확인 한 후 조직의 요구 사항을 충족 하는 AD DS 배포 전략을 만들 수 있습니다.

## <a name="about-this-guide"></a>이 가이드의 내용

이 가이드에서는 조직의 요구 사항 및 만들려는 특정 디자인에 따라 AD DS 배포 전략을 개발 하는 데 도움이 되는 권장 사항을 제공 합니다. 이 가이드는 인프라 전문가 또는 시스템 설계자용으로 작성되었습니다. 이 가이드를 읽기 전에 AD DS 기능 수준에서 작동 하는 방식에 대해 잘 알고 있어야 합니다. 또한 AD DS 배포 전략에 반영 될 조직의 요구 사항에 대해 잘 알고 있어야 합니다.

이 가이드에서는 Windows Server 2008 AD DS 배포의 몇 가지 가능한 시작 위치에 대 한 작업 집합을 설명 합니다. 이 가이드를 통해 사용자 환경에 가장 적합한 배포 전략을 결정할 수 있습니다.

이 가이드에서 제시 하는 전략은 거의 모든 서버 운영 체제 배포에 적합 하지만, 최소 28.8 킬로 비트 (Kbps)의 네트워크 연결을 통해 10만 개 미만의 1000 사용자를 포함 하는 환경에 대해 구체적으로 테스트 되 고 유효성이 검사 되었습니다. 사용자 환경이 이러한 조건을 충족 하지 않는 경우 더 복잡 한 환경에서 AD DS 배포 경험이 있는 컨설팅 회사를 사용 하는 것이 좋습니다.

AD DS 배포 프로세스를 테스트 하는 방법에 대 한 자세한 내용은 [배포 프로세스 테스트 및 확인](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc772722(v=ws.10))문서를 참조 하세요.

## <a name="in-this-guide"></a>이 가이드의 내용

[AD DS 디자인 이해](Understanding-AD-DS-Design.md)

[AD DS 디자인 및 배포 요구 사항 식별](Identifying-Your-AD-DS-Design-and-Deployment-Requirements.md)

[AD DS 배포 전략에 요구 사항 매핑](Mapping-Your-Requirements-to-an-AD-DS-Deployment-Strategy.md)

[Windows Server 2008에 대 한 논리 구조 디자인 AD DS](Designing-the-Logical-Structure.md)

[Windows Server 2008에 대 한 사이트 토폴로지 디자인 AD DS](Designing-the-Site-Topology.md)

[AD DS에 대한 고급 기능 사용](Enabling-Advanced-Features-for-AD-DS.md)

[AD DS 배포 전략 예제 평가](Evaluating-AD-DS-Deployment-Strategy-Examples.md)

[부록 A: 주요 AD DS 용어 검토](Appendix-A--Reviewing-Key-AD-DS-Terms.md)
