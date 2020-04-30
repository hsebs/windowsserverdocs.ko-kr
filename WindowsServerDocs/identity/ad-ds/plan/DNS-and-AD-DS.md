---
ms.assetid: c32606b4-2ee2-4df3-a704-8ac6723e188f
title: DNS 및 AD DS
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 817c6ca168e33df1a0c59e151a303c4259313743
ms.sourcegitcommit: 11421f4005f9f3a3f6c0db95b1836d0f765a9fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81624301"
---
# <a name="dns-and-ad-ds"></a>DNS 및 AD DS

> 적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Active Directory Domain Services (AD DS)는 DNS (Domain Name System) 이름 확인 서비스를 사용 하 여 클라이언트에서 도메인 컨트롤러를 찾을 수 있도록 하 고 디렉터리 서비스를 호스트 하는 도메인 컨트롤러에서 서로 통신 하도록 합니다.

AD DS Active Directory 네임 스페이스를 기존 DNS 네임 스페이스로 쉽게 통합할 수 있습니다. Active Directory 통합 DNS 영역과 같은 기능을 사용 하면 보조 영역을 설정 하 고 영역 전송을 구성할 필요 없이 DNS를 보다 쉽게 배포할 수 있습니다.

DNS에서 AD DS를 지 원하는 방법에 대 한 자세한 내용은 [Active Directory 기술 참조에 대 한 Dns 지원](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781627(v=ws.10))섹션을 참조 하세요.

> [!NOTE]
> AD DS 도메인 이름이 클라이언트에서 사용 하는 주 DNS 접미사와 다른 연결 되지 않은 네임 스페이스를 구현 하는 경우 AD DS DNS와의 통합이 더 복잡 합니다. 자세한 내용은 [비연속 네임 스페이스](Disjoint-Namespace.md)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

- [도메인 컨트롤러 위치](Domain-Controller-Location.md)
- [Active Directory 통합 DNS 영역](Active-Directory-Integrated-DNS-Zones.md)
- [컴퓨터 이름 지정](Computer-Naming.md)
- [연결되지 않은 네임 스페이스](Disjoint-Namespace.md)
