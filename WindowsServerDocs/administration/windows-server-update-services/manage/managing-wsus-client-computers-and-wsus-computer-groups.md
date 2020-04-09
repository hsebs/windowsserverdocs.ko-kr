---
title: WSUS 클라이언트 컴퓨터 및 WSUS 컴퓨터 그룹 관리
description: WSUS (Windows Server Update Service) 항목-클라이언트 컴퓨터 및 그룹을 관리 하는 방법
ms.prod: windows-server
ms.technology: manage-wsus
ms.topic: article
ms.assetid: 4b1ea915-0f9f-4f0e-8913-a1dd460d07ab
author: coreyp-at-msft
ms.author: coreyp
manager: lizapo
ms.date: 10/16/2017
ms.openlocfilehash: 3ac5a0c09d28de53430ded651b6da92ba92a1f68
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80828629"
---
# <a name="managing-wsus-client-computers-and-wsus-computer-groups"></a>WSUS 클라이언트 컴퓨터 및 WSUS 컴퓨터 그룹 관리

>적용 대상: Windows Server 2019, Windows Server (반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

컴퓨터 노드는 wsus 클라이언트 컴퓨터 및 장치를 관리 하기 위해 WSUS 관리 콘솔에서 중앙 액세스 지점입니다. 이 노드 아래에서 설정 된 여러 그룹 (기본 그룹, 할당 되지 않은 컴퓨터)을 찾을 수 있습니다.

## <a name="managing-client-computers"></a>클라이언트 컴퓨터 관리
**옵션** 아래의 컴퓨터 노드에서 컴퓨터 그룹 중 하나를 선택 하면 해당 그룹 **의 컴퓨터가 세부** 정보 창에 표시 됩니다. 컴퓨터는 여러 그룹에 할당 된 경우에 두 그룹의 목록에 표시 됩니다. 목록에서 컴퓨터를 선택 하는 경우 컴퓨터 및 설치와 같은,에 대 한 업데이트의 상태 또는 특정 컴퓨터에 대 한 업데이트의 검색 상태에 대 한 일반 정보를 포함 하는 해당 속성을 볼 수 있습니다. 상태에 의해 지정 된 컴퓨터 그룹에서 컴퓨터의 목록을 필터링 할 수 있습니다. 기본 표시는 업데이트가 필요한 지 또는 설치 실패; 했던에 대 한 컴퓨터만 그러나 표시 되는 모든 상태에서 필터링 할 수 있습니다. 클릭 **새로 고침** 상태 필터를 변경한 후입니다.

컴퓨터 페이지에서 컴퓨터 그룹을 관리할 수도 있습니다. 여기에는 그룹을 만들고 컴퓨터를 할당 하는 작업이 포함 됩니다. 컴퓨터 그룹을 관리 하는 방법에 대 한 자세한 내용은이 가이드의 다음 섹션에서 컴퓨터 그룹 관리 및 1.5 섹션을 참조 하십시오 [. Wsus 컴퓨터 그룹 계획](../plan/plan-your-wsus-deployment.md#15-plan-wsus-computer-groups) 1 단계: wsus 배포 준비의 wsus 배포 가이드를 참조 하세요.

> [!NOTE]
> 해당 서버에서 관리 하려면 먼저 WSUS 서버를 연결 하도록 클라이언트 컴퓨터를 먼저 구성 해야 합니다. 이 작업을 수행할 때까지 WSUS 서버는 클라이언트 컴퓨터를 인식 하지 못하며 컴퓨터 페이지의 목록에 표시 되지 않습니다. 클라이언트 컴퓨터를 설정 하는 방법에 대 한 자세한 내용은 1.5을 참조 하십시오 [. Wsus 컴퓨터 그룹 계획](../plan/plan-your-wsus-deployment.md#15-plan-wsus-computer-groups) 1 단계: wsus 배포 준비 및 3 단계: Wsus 구성 (wsus 배포 가이드)을 참조 하세요.

## <a name="controlling-when-wsus-client-computers-install-updates"></a>WSUS 클라이언트 컴퓨터에서 업데이트를 설치 하는 시기를 제어 합니다.
다음 두 가지가 있습니다 제어에 WSUS 클라이언트 컴퓨터 업데이트를 설치 합니다.

-   승인 기한이 있는: 마감일은 업데이트가 설치 될 때를 엄격 하 게 적용

-   Windows Update 에이전트를 검색 하 고 업데이트를 설치 하는 경우 WSUS 그룹 정책: 그룹 정책 제어

    자세한 내용은 WSUS 배포 가이드의 [5 단계: 자동 업데이트에 대 한 그룹 정책 설정 구성](../deploy/4-configure-group-policy-settings-for-automatic-updates.md)을 참조 하세요.

## <a name="managing-computer-groups"></a>컴퓨터 그룹 관리
WSUS에서는 클라이언트 컴퓨터 그룹을 대상으로 하는 업데이트가 허용되므로, 특정 컴퓨터에서 항상 올바른 업데이트를 가장 편한 시간에 가져오도록 할 수 있습니다. 예를 들어 재정 팀 같은 한 부서의 모든 컴퓨터에 구성과 관련된 특정한 사항이 있는 경우 이 팀에 알맞은 그룹을 설정하고, 해당 컴퓨터에 필요한 업데이트와 이러한 업데이트가 설치될 시간을 결정한 다음 WSUS 보고서를 사용해 팀의 업데이트를 평가할 수 있습니다.

컴퓨터는 항상 **모든 컴퓨터** 그룹에 할당 되며, 다른 그룹에 할당 될 때까지 할당 되지 **않은 컴퓨터** 그룹에 할당 된 상태로 유지 됩니다. 컴퓨터는 둘 이상의 그룹에 속할 수 있습니다.

컴퓨터 그룹은 계층 구조로 구성될 수 있습니다. 예를 들면 Accounting 그룹 아래에 Payroll 그룹과 Accounts Payable 그룹을 만들 수 있습니다. 상위 그룹에 승인 된 업데이트를 더 높은 그룹 자체 뿐 아니라 하위 그룹에 자동으로 배포 됩니다. 따라서 Accounting 그룹에 대 한 업데이트 1를 승인 하는 경우 업데이트는 Accounting 그룹에 있는 모든 컴퓨터, 급여 그룹에 있는 모든 컴퓨터 및 Accounts Payable 그룹에 있는 모든 컴퓨터에 배포 됩니다.

컴퓨터는 여러 그룹에 할당될 수 있으므로, 한 업데이트가 동일한 컴퓨터에 두 번 이상 승인될 수 있습니다. 하지만 업데이트는 한 번만 배포되며, 충돌은 WSUS 서버에서 확인됩니다. 위의 예를 계속 하기 위해 컴퓨터 a가 급여와 외상 매입금 그룹 모두에 할당 되 고 업데이트 1가 두 그룹 모두에 대해 승인 되 면 한 번만 배포 됩니다.

서버 측 대상 또는 클라이언트 측 대상의 두 가지 방법 중 하나를 사용해 컴퓨터 그룹에 컴퓨터를 할당할 수 있습니다. 서버 쪽 대상을 수동으로 이동 해도 하나 이상의 클라이언트 컴퓨터 한 대의 컴퓨터 그룹에 한 번에 있습니다. 클라이언트 측 대상으로 그룹 정책을 사용 하거나 이전에 만든된 컴퓨터 그룹에 자동으로 추가 되도록 해당 컴퓨터를 사용 하도록 설정 하려면 클라이언트 컴퓨터에서 레지스트리 설정을 편집 합니다. 이 프로세스를 스크립트로 작성 하 고 한 번에 여러 컴퓨터에 배포 될 수 있습니다. **옵션** 페이지의 **컴퓨터** 섹션에서 두 옵션 중 하나를 선택 하 여 WSUS 서버에서 사용할 대상 지정 방법을 지정 해야 합니다.

> [!NOTE]
> WSUS 서버가 복제 모드에서 실행되는 경우에는 해당 서버에 컴퓨터 그룹을 만들 수 없습니다. 복제 서버의 클라이언트에 필요한 모든 컴퓨터 그룹은 WSUS 서버 계층의 루트인 WSUS 서버에서 생성 되어야 합니다. 복제 모드에 대 한 자세한 내용은 [WSUS 복제 모드 실행](running-wsus-replica-mode.md) 및 서버 쪽 및 클라이언트 쪽 대상 지정에 대 한 자세한 내용은 섹션 1.5을 참조 하세요 [. Wsus 컴퓨터 그룹 계획](../plan/plan-your-wsus-deployment.md#15-plan-wsus-computer-groups) 1 단계: wsus 배포 가이드에서 Wsus 배포를 준비 합니다.


