---
title: 액세스 권한
description: 이 항목에서는 Windows Server 2016에 네트워크 정책 서버에 대 한 네트워크 정책 액세스 권한 개요를 제공 합니다.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: d6d1ca5e-bde0-4509-9e14-dc3fa9ff447e
ms.author: pashort
author: shortpatti
ms.openlocfilehash: aeacfaeb159598d2e53bac29fb09ffc3e7739476
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="access-permission"></a>액세스 권한

>적용 대상: Windows Server (세미콜론 연간 채널) Windows Server 2016

에 대 한 액세스 권한을 구성 되어 있는 **개요** 각 네트워크 정책에서 네트워크 NPS 정책 서버 ()을 탭 합니다. 

이 설정을 통해 하거나 조건 및 정책 네트워크 제약 연결 요청 일치 하는 경우 사용자에 대 한 액세스 거부 정책 구성할 수 있습니다. 

액세스 권한 설정을 다음과 같은 효과가 있습니다.

- **액세스 권한을 부여**합니다. 연결 요청 조건 및 정책에서 구성 된 제약와 일치 하는 경우 권한이 부여 됩니다.
- **액세스 거부**합니다. 연결 요청 조건 및 정책에서 구성 된 제약 일치 하는 경우 거부 되었습니다.

액세스 권한이 부여 되거나 거부도의 각 사용자 계정의 전화 속성 구성에 따라 합니다.

>[!NOTE]
>사용자 계정 및 전화 접속 속성 등 자녀가 속성의 Active Directory 사용자 및 컴퓨터 또는 로컬 사용자 및 그룹 Microsoft Management Console \(MMC\) 스냅인, Active Directory 있는지 여부에 따라에서 구성 된&reg; 도메인 서비스 (AD DS)를 설치 합니다.

사용자 계정 설정이 **네트워크 액세스 권한을**, 전화 접속 속성의 사용자 계정에서 구성 된, 재정의 네트워크 정책 사용 권한 설정에 액세스 합니다. 사용자 계정에 대 한 액세스 권한을 네트워크로 설정 된 경우는 **NPS 네트워크 정책을 통해 액세스를 제어** 옵션 네트워크 정책 액세스 권한을 설정을 사용자 액세스할 부여 여부를 결정 합니다.

>[!NOTE]
>Windows Server 2016 년 기본값에서에서 **네트워크 액세스 권한을** AD DS 사용자 계정에 전화 속성은 **NPS 네트워크 정책을 통해 액세스를 제어**합니다.

NPS 연결 요청 구성 된 네트워크 정책에 대 한 평가 하는 경우 다음과 같은 작업을 수행 합니다.

- 첫 번째 정책 조건과 충족 하지 되 면 NPS 다음 정책을 평가 일치 하는 되거나 일치 하는 모든 정책 평가 될 때까지이 프로세스를 계속 합니다.
- 조건 및 정책 제약 일치 하는 경우 NPS 부여 하거나 값 정책에 대 한 액세스 권한을 설정에 따라 액세스 거부 합니다.
- 일치 하지만 제한을 정책에의 조건이 맞지 않는 경우 NPS 연결 요청을 거부 합니다.
- 모든 정책 조건 일치 하지 않는 경우 NPS 연결 요청을 거부 합니다.

## <a name="ignore-user-account-dial-in-properties"></a>사용자 계정에 전화 속성 무시 합니다.

선택 하거나 선택 취소 하 여 사용자 계정 전화 속성 무시 NPS 네트워크 정책 구성할 수 있습니다의 **사용자 계정에 전화 속성 무시** 확인란을는 **개요** 네트워크 정책 탭 합니다. 

일반적으로 NPS 연결 요청을 승인을 수행 하는 경우 전화 접속 속성 어디 값으로 설정 된 네트워크 액세스 권한을 영향을 미칠 수 사용자 네트워크에 연결할 수 있는 권한이 있는지 여부, 사용자 계정의 확인 합니다. 승인 하는 동안 사용자 계정의 전화 속성을 무시 하도록 NPS 구성한 경우 네트워크 정책 설정은 사용자가 네트워크에 액세스 권한이 있는지 여부를 결정 합니다.

사용자 계정의 전화 속성은 다음이 포함 합니다.

- 네트워크 액세스 권한
- 발신자 번호
- 여 전화 옵션
- 고정 IP 주소
- 고정 경로

여러 유형의 NPS 인증과 제공 하는 연결을 지원 하기 위해 사용자 계정이 전화 접속 속성의 처리를 사용 하지 않도록 설정 해야 할 수도 있습니다. 이 전화 접속 속성 특정 필요 하지 않은 시나리오를 지원 하기 위해 수행할 수 있습니다.

예, 발신자 번호, 여 전화, 고정 IP 주소 및 속성 네트워크 액세스 서버에 전화를 거는 하는 클라이언트 위한 고정 경로 \(NAS\), 하지 무선 액세스를 연결 하는 클라이언트 가리킵니다. 이러한 설정의 NPS RADIUS 메시지에서 수신 하는 무선 액세스 포인트 못할을 처리 하기 위해 무선 연결을 끊을 클라이언트 발생할 수 있는 합니다.

NPS 인증 및 사용자에 게 전화 걸기에 및 조직의 네트워크 무선 액세스 포인트를 통해 액세스 권한을 제공 하며 때에 전화 접속 속성 중 전화 접속 연결을 지원 하도록 구성 해야 \ (properties\ 전화 접속 설정) 하 여 무선 연결 또는 \ (으로 전화 접속 properties\ 설정 하지).

NPS 사용 하 여 일부 시나리오에서 사용자 계정에 대 한 처리 전화 접속 속성 수 있도록 \ (전화 in\ 같은) 다른 시나리오에서 처리 전화 접속 속성 사용 하지 않도록 설정 하 고 \ (예: 802.1 무선 및 인증 switch\ X) 합니다.

사용할 수 있습니다 **사용자 계정에 전화 속성 무시** 그룹과 네트워크 정책에 대 한 액세스 권한 설정을 통해 네트워크 액세스 제어 관리할 수 있습니다. 선택 하 고 **사용자 계정에 전화 속성 무시** 확인란, 사용자 계정에 대 한 액세스 권한을 네트워크에서 무시 됩니다.

이 구성에만 단점은 추가로 사용자 계정에 전화 속성 발신자 번호, 여 전화를 고정 IP 주소, 및 고정 경로 사용할 수 없다는입니다.

NPS에 대 한 자세한 내용은 참조 [네트워크 NPS 정책 서버 ()](nps-top.md)합니다.