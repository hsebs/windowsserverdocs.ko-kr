---
title: 무선 액세스 배포 프로세스
description: 이 항목은 Windows Server 2016 네트워킹 가이드 "암호 기반 802.1 X 인증 된 무선 액세스 배포"의 일부입니다.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 2555f238-926e-4b20-9bfb-9774831062da
author: eross-msft
ms.author: lizross
ms.openlocfilehash: 30e3da7e1365585bf9dc5ff34a72a367e1ed28f7
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80318087"
---
# <a name="wireless-access-deployment-process"></a>무선 액세스 배포 프로세스

>적용 대상: Windows Server(반기 채널), Windows Server 2016

무선 액세스를 배포 하는 프로세스이 단계에서 발생 합니다.

## <a name="stage-1--ap-deployment"></a>1 단계 – AP 배포

무선 클라이언트 연결용 Ap를 계획, 배포 및 구성 하 고 NPS를 사용 합니다. 먼저 기본 설정 및 네트워크 종속성을 따라 하면\-네트워크에 설치 하기 전에 무선 Ap에서 설정을 구성 하거나 설치 후 원격으로 구성할 수 있습니다.

## <a name="stage-2--adds-group-configuration"></a>2 단계 – 그룹 구성 AD DS

AD DS에서 하나 이상의 무선 사용자 보안 그룹을 만들어야 합니다.

다음으로, 무선 네트워크에 액세스할 수 있는 사용자를 식별 합니다.

마지막으로 만든 적절 한 무선 사용자 보안 그룹에 사용자를 추가 합니다.

>[!NOTE]
>기본적으로는 **네트워크 액세스 권한** 사용자 계정 전화 접속 속성에서 설정 된 설정으로 구성 된 **NPS 네트워크 정책을 통해 액세스를 제어**합니다. 이 설정을 변경 하려면 특별 한 이유가 없다면 기본값을 유지 하는 것이 좋습니다. 이 옵션을 사용 하면 NPS에 구성 하는 네트워크 정책을 통해 네트워크 액세스를 제어할 수 있습니다.

## <a name="stage-3--group-policy-configuration"></a>3 단계 – 그룹 정책 구성

무선 네트워크 구성 \(IEEE 802.11\) 그룹 정책 관리 편집기 Microsoft Management Console을 사용 하 여 그룹 정책의 정책 확장 \(MMC\)합니다.

도메인을 구성 하려면\-무선 네트워크 정책 설정을 사용 하는 구성원 컴퓨터, 그룹 정책을 적용 해야 합니다. 컴퓨터는 도메인에 가입 먼저, 그룹 정책은 자동으로 적용 됩니다. 그룹 정책를 변경 하는 경우 새 설정이 자동으로 적용 됩니다.

- 이전 버전에서 그룹 정책에 의해\-간격을 결정

- 도메인 사용자가 로그 오프 한 다음 다시 네트워크에 로그온 하는 경우

- 클라이언트 컴퓨터를 다시 시작 하는 도메인에 로그온 하 여

그룹 정책에 명령을 실행 하 여 컴퓨터에 로그온 한 동안 새로 고침을 강제할 수도 **gpupdate** 명령 프롬프트입니다.

## <a name="stage-4--nps-configuration"></a>4 단계 – NPS 구성

NPS에서 구성 마법사를 사용 하 여 무선 액세스 지점은 RADIUS 클라이언트로 추가 하 고 NPS가 연결 요청을 처리할 때 사용 하는 네트워크 정책을 만들 수 있습니다.

마법사를 사용 하 여 네트워크 정책을 만드는 경우 PEAP를 EAP 유형으로 지정 하 고 두 번째 단계에서 만든 무선 사용자 보안 그룹을 지정 합니다.

## <a name="stage-5--deploy-wireless-clients"></a>5 단계 – 무선 클라이언트 배포

클라이언트 컴퓨터를 사용 하 여 네트워크에 연결 합니다.

유선 LAN에 로그온 할 수 있는 도메인 구성원 컴퓨터의 경우, 그룹 정책를 새로 고치면 필요한 무선 구성 설정이 자동으로 적용 됩니다.

무선 네트워크의 설정을 사용 하도록 설정한 경우 \(IEEE 802.11\) 내 컴퓨터가 될 때 자동으로 연결 하는 정책을 무선 네트워크, 무선, 도메인의 범위를 브로드캐스트\-조인 된 컴퓨터는 자동 무선 LAN에 연결을 시도 합니다.

무선 네트워크에 연결 하려면 Windows에서 메시지를 표시 하는 경우 사용자에 게 도메인 사용자 이름 및 암호 자격 증명을 제공 해야 합니다.

무선 액세스 배포를 계획 하려면 참조 [무선 액세스 배포 계획](d-wireless-access-planning.md)합니다.
