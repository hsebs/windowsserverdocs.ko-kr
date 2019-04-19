---
title: 이해 클러스터 및 풀 쿼럼
description: 복잡 하는 구체적인 예를 사용 하 여 클러스터 및 풀 쿼럼 이해 합니다.
keywords: 저장소 공간 다이렉트 쿼럼 감시, S2D, 클러스터 쿼럼, 풀 쿼럼 클러스터, 풀
ms.prod: windows-server-threshold
ms.author: adagashe
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 01/18/2019
ms.localizationpriority: medium
ms.openlocfilehash: 24890b191db8bc6934132857e830d4f77c394b02
ms.sourcegitcommit: 28dc7c7f1e44fee7ab2112228af329a9ce0e02ba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2019
ms.locfileid: "9024141"
---
# 이해 클러스터 및 풀 쿼럼

>적용 대상: Windows Server 2019, Windows Server 2016

[Windows Server 장애 조치 클러스터링](../../failover-clustering/failover-clustering-overview.md) 워크 로드에 대 한 고가용성을 제공합니다. 이러한 리소스; 노드가 리소스를 호스트 하는 경우 항상 사용 가능한 것으로 간주 됩니다. 그러나 클러스터 일반적으로 필요 실행 되 고 절반 이상 노드 *쿼럼이*이라고 하는 합니다.

쿼럼 방지 하도록 설계 되었습니다 *브레인* 시나리오는 네트워크에 파티션을 있고 노드의 하위 집합을 서로 통신할 수 없으며 때 발생할 수 있습니다. 노드 워크 로드를 소유 하 고 다양 한 문제를 야기할 수 있는 동일한 디스크에 쓰기를 모두 하위 집합도 발생할 수 있습니다. 하지만 이것은 장애 조치 클러스터링의 개념이 쿼럼 강제로 이러한 그룹을 계속 실행할 이러한 그룹 중 하나에만 온라인 상태를 유지 하므로 노드 중 하나에 사용 하 여 없습니다.

쿼럼 여전히 온라인 상태를 유지 하면서 허용 된 오류 수를 결정 합니다. 쿼럼 여러 서버 동시에 리소스 그룹을 호스트 하 고 동시에 동일한 디스크에 쓰기를 시도 하지 않도록 클러스터 노드의 하위 집합 간의 통신에 문제가 있는 경우 시나리오를 처리 하도록 설계 되었습니다. 이 개념이 쿼럼 함으로써 클러스터 클러스터 서비스를를 하나만 true 특정 리소스 그룹 소유자가 노드의 하위 집합 중 하나에서 중지 새로 고쳐집니다. 노드는 중지 된 노드의 기본 그룹 다시 한 번 통신할 수, 일단 자동으로 클러스터 다시 되며 클러스터 서비스를 시작 합니다.

Windows Server 2016에서 자신의 쿼럼 메커니즘 없는 시스템의 두 가지 구성 요소를 가지 있습니다.

- <strong>클러스터 쿼럼</strong>:이 클러스터 수준에서 작동 하므로 (즉, 노드를 손실 하 고 수를 유지 하는 클러스터)
- <strong>풀 쿼럼</strong>: 저장소 공간 다이렉트를 사용 하면 풀 수준에서 작동 하는이 (즉, 노드 및 드라이브 손실 하 고 수를 유지 하는 풀). 저장소 풀 때문에 다른 쿼럼 메커니즘을가지고 모두 클러스터 및 비 클러스터 시나리오에서 사용 하도록 설계 되었습니다.

## 클러스터 쿼럼 개요

아래 표에 시나리오 당 클러스터 쿼럼 결과의 개요를 제공합니다.

| 서버 노드 | 알아 보려면 하나의 서버 노드 오류 수 있습니다. | 하나의 서버 노드 오류 다음 다른 살아 올 수 있습니다. | 두 가지 동시 서버 노드 오류를 해결 수 있습니다. |
|--------------|-------------------------------------|---------------------------------------------------|----------------------------------------------------|
| 2            | 50/50                               | 아니요                                                | 아니요                                                 |
| 2 + 감시  | 예                                 | 아니요                                                | 아니요                                                 |
| 3            | 예                                 | 50/50                                             | 아니요                                                 |
| 3 + 감시  | 예                                 | 예                                               | 아니요                                                 |
| 4            | 예                                 | 예                                               | 50/50                                              |
| 4 + 감시  | 예                                 | 예                                               | 예                                                |
| 5 이상  | 예                                 | 예                                               | 예                                                |

### 클러스터 쿼럼 권장 사항

- 감시는 두 개의 노드가 있는 경우 <strong>필수</strong>.
- 감시는 3 개 또는 4 개의 노드에 있는 경우 <strong>권장</strong>.
- 인터넷에 액세스할 수 있으면 사용 하는 <strong> [클라우드 감시](../../failover-clustering/deploy-cloud-witness.md)</strong>
- 파일 공유 감시를 사용 하 여 다른 컴퓨터 및 파일 공유를 사용 하 여 IT 환경에 있는 경우

## 클러스터 쿼럼 작동 방식

노드가 실패 또는 일부 하위 노드 집합에서 다른 하위 집합을 사용 하 여 연락처를 잃을 때 살아 있는 노드 온라인 상태로 유지 하는 클러스터의 *대부분* 을 구성할 수 있는지 확인 해야 합니다. 확인할 수 없는 것, 오프 라인 됩니다.

하지만 *대부분* 의 개념에만 작동 완전히 노드 클러스터의 총 수 (예: 5 개의 노드 클러스터에 노드가 3 개) 이상한 경우. 무엇 짝수 노드 (예: 4 개의 노드 클러스터)를 사용 하 여 클러스터에 대 한?

두 가지 방법으로 클러스터 *응답의 총* 이상한 만들 수 있습니다.

1. 첫째,는 여분의 표를 사용 하 여 *감시* 를 추가 하 여 *를* 하나 이동할 수 있습니다. 이렇게 하려면 사용자 설정 합니다.
2.  또는 하나의 운 노드 투표 (필요에 따라 자동으로 수행 됨)을 0으로 *아래로* 이동할 수 있습니다.

살아 있는 노드 *대부분*은 성공적으로 확인, 때마다 *대부분* 의 정의 남은 개체 간의 되도록 업데이트 됩니다. 이렇게 하면 한 노드를 다른 차례로, 손실 되 고 등 클러스터 수 있습니다. 이 개념 연속 오류 라고 후 *응답의 총 수* 조정 <strong> *동적 쿼럼*</strong>.  

### 동적 감시

동적 감시 이상한 *응답의 총 수* 있는지 확인 하려면 감시의 응답을 전환 합니다. 홀수 투표 인 경우 미러링 투표가 필요는 없습니다. 투표 짝수 이면 미러링에 응답 합니다. 동적 감시 클러스터 감시 실패로 전달 될 위험을 크게 줄입니다. 클러스터를 클러스터에서 사용할 수 있는 응답 노드의 수에 따라 감시 응답을 사용할지 여부를 결정 합니다.

동적 쿼럼 동적 감시 아래에 설명 된 방식으로 작동 합니다.

### 동적 쿼럼 동작

- 있는 경우는 <strong>도</strong> 수 노드 및 없는 감시, *하나의 노드에 0이 결정을 가져옵니다*. 예를 들어 4 개의 노드 중 세 개만 가져와서 투표, *응답의 총 수* 는 3 및 표를 사용 하 여 두 남은 개체는 대부분 것으로 간주 됩니다.
- 있는 경우는 <strong>이상한</strong> 노드 및 없는 감시, *모두 투표*수 있습니다.
- 있는 경우는 <strong>도</strong> 총 이상한 이므로 노드 *미러링 투표*, 감시의 숫자입니다.
- 있는 경우는 <strong>이상한</strong> 수의 노드 및 감시를 *미러링 응답 하지 않습니다*.

동적 쿼럼 수 동적으로 투표 대부분 손실 되지 않도록 하 고 하나의 노드에 (마지막 남자 순위 라고도 함)를 사용 하 여 실행 하려면 클러스터 노드를 결정 하는 기능이 있습니다. 예를 들어 4 노드 클러스터를 살펴보겠습니다. 해당 쿼럼 필요 세 표 가정 합니다. 

이 경우 클러스터 라 두 노드를 손실 하는 경우.

![4 개의 클러스터 노드를 보여 주는, 투표 가져옵니다 각각 다이어그램](media/understand-quorum/dynamic-quorum-base.png)

그러나 동적 쿼럼 일에서이 수 없습니다. 이제 쿼럼에 필요한 *응답의 총 수* 는 사용 가능한 노드 수에 따라 결정 됩니다. 따라서 동적 쿼럼 클러스터 노드가 3 개를 손실 하는 경우에를 유지 됩니다.

![각 오류 후 조정 필수 투표 수가 한 번에 하나씩 실패 노드를 사용 하 여 4 개의 클러스터 노드를 보여 주는 다이어그램입니다.](media/understand-quorum/dynamic-quorum-step-through.png)

위의 시나리오는 저장소 공간 다이렉트 사용할 수 없는 일반 클러스터에 적용 됩니다. 단, 저장소 공간 다이렉트를 사용 하면 클러스터 두 노드 장애 지원만 수 있습니다. 이 더에 [풀 쿼럼 섹션](#poolQuorum)에 설명 되어 있습니다.

### 예

#### 두 노드를 감시 없이 합니다. 
한 노드에서 투표 0 이므로 *대부분* 투표 총 밖 결정은 <strong>1 투표</strong>합니다. 응답 비 노드 다운 예기치 않게 되 면는 생존자 1/1 있으며 클러스터 살아 있습니다. 응답 노드 다운 예기치 않게 되는 생존자 0/1 있으며 클러스터 다운 합니다. 정상적으로 응답 노드 전원이, 다른 노드로 전송 되므로 응답 하 고 클러스터 살아 합니다. *<strong>이 때문에 감시를 구성 해야 합니다.</strong>*

![쿼럼 감시 없이 두 노드가 있는 경우 설명](media/understand-quorum/2-node-no-witness.png)

- 하나의 서버 오류 살아 올 수: <strong>50% 기회가</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>아니요</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>아니요</strong>. 

#### 두 노드를 감시로 합니다. 
두 노드 투표, 감시 투표와 *대부분* 은 총 밖 결정 되므로 <strong>세 표</strong>합니다. 두 노드 중 하나가 다운 되 면는 생존자 2/3 있으며 클러스터 살아 있습니다.

![쿼럼 감시를 사용 하 여 노드가 두 경우에서 설명합니다.](media/understand-quorum/2-node-witness.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>아니요</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>아니요</strong>. 

#### 3 개 노드로 없이 감시 합니다.
모든 노드 투표 *대부분* 은 총 밖 결정 되므로 <strong>세 표</strong>합니다. 모든 노드가 다운 되 면, 남은 개체 2/3 되며 클러스터 살아. 클러스터 감시 없이 두 노드가 되 – 시점에 시나리오 1에 있는 것입니다.

![쿼럼 감시 없이 노드가 3 개 있는 경우 설명](media/understand-quorum/3-node-no-witness.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>50% 기회가</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>아니요</strong>. 

#### 감시를 사용 하 여 노드가 3 개입니다.
미러링 처음 응답 하지 않는 하므로 모든 노드 결정 합니다. *대부분* 의 전체에서 결정 됩니다 <strong>세 표</strong>합니다. 하나의 오류 시나리오 2를 다시 감시 –으로 두 개의 노드 클러스터에 있습니다. 따라서 이제 두 노드 및 미러링 결정합니다.

![쿼럼 감시를 사용 하 여 노드가 3 개 있는 경우에 설명합니다.](media/understand-quorum/3-node-witness.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>예</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>아니요</strong>. 

#### 4 개의 노드에 없이 감시
한 노드에서 투표 0 이므로 *대부분* 총 밖 결정은 <strong>세 표</strong>합니다. 하나의 오류 후 클러스터 노드가 3 개 되며 시나리오 3에 있는 것입니다.

![쿼럼 감시 없이 4 개의 노드에 있는 경우 설명](media/understand-quorum/4-node-no-witness.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>예</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>50% 기회가</strong>. 

#### 감시를 사용 하 여 4 개의 노드에 합니다.
모든 노드 표 및 총 밖 *대부분* 은 결정 되므로 감시 투표 <strong>5 투표</strong>합니다. 시도가 실패 한 시나리오 4에 있는 것입니다. 두 개의 동시 오류의 시나리오 2 나타날 때까지 아래로 건너뜁니다.

![쿼럼 감시를 사용 하 여 4 개의 노드에 있는 경우에 설명합니다.](media/understand-quorum/4-node-witness.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>예</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>예</strong>. 

#### 5 개의 노드 32tb 이상.
모든 노드 응답 하거나 하나를 제외한 모든 투표 어떤 이상한 합계. 저장소 공간 다이렉트 처리할 수 없습니다 노드 두 개 이상의 아래로 어쨌든 이므로이 시점에서는 없음 감시 필요한 또는 유용 합니다.

![쿼럼 경우 5 개의 노드를 사용 하 여 및 설명](media/understand-quorum/5-nodes.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>예</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>예</strong>. 

쿼럼의 작동 방식을 이해 하는 이제 쿼럼 목격자의 형식에 대해 살펴보겠습니다.

### 쿼럼 감시 유형

장애 조치 클러스터링은 세 가지 유형의 쿼럼 목격자 지원합니다.

- <strong>[클라우드 감시](../../failover-clustering\deploy-cloud-witness.md) </strong> -클러스터의 모든 노드에서 액세스할 수 있는 azure 저장소 Blob입니다. Witness.log 파일에 있는 클러스터링 정보를 유지 하지만, 클러스터 데이터베이스의 복사본을 저장 하지 않습니다.
- <strong>파일 공유 감시</strong> -Windows Server를 실행 하는 파일 서버에 구성 되어 있는 A SMB 파일 공유 합니다. Witness.log 파일에 있는 클러스터링 정보를 유지 하지만, 클러스터 데이터베이스의 복사본을 저장 하지 않습니다.
- <strong>감시 디스크</strong> -사용 가능한 저장소 클러스터 그룹에 있는 작은 클러스터 디스크 합니다. 이 디스크는 매우 사용할 수 있으며 노드 간에 장애 조치를 수 있습니다. 클러스터 데이터베이스의 복사본을 포함 합니다.  <strong>*저장소 공간 다이렉트를 사용 하 여 디스크 감시 지원 되지 않습니다*</strong>.

## <a id="poolQuorum"></a>풀 쿼럼 개요

방금 클러스터 수준에서 작동 하는 클러스터 쿼럼 기술인 합니다. 이제 (즉, 수 손실 노드 및 드라이브 되 고 없는 풀을 유지)은 풀 수준에서 작동 하는 풀 쿼럼 세부 사항을 살펴보도록 하겠습니다. 저장소 풀 때문에 다른 쿼럼 메커니즘을가지고 모두 클러스터 및 비 클러스터 시나리오에서 사용 하도록 설계 되었습니다.

아래 표에 시나리오 당 풀 쿼럼 결과의 개요를 제공합니다.

| 서버 노드 | 알아 보려면 하나의 서버 노드 오류 수 있습니다. | 하나의 서버 노드 오류 다음 다른 살아 올 수 있습니다. | 두 가지 동시 서버 노드 오류를 해결 수 있습니다. |
|--------------|-------------------------------------|---------------------------------------------------|----------------------------------------------------|
| 2            | 아니요                                  | 아니요                                                | 아니요                                                 |
| 2 + 감시  | 예                                 | 아니요                                                | 아니요                                                 |
| 3            | 예                                 | 아니요                                                | 아니요                                                 |
| 3 + 감시  | 예                                 | 아니요                                                | 아니요                                                 |
| 4            | 예                                 | 아니요                                                | 아니요                                                 |
| 4 + 감시  | 예                                 | 예                                               | 예                                                |
| 5 이상  | 예                                 | 예                                               | 예                                                |

## 풀 쿼럼 작동 방식

드라이브 실패 또는 드라이브의 일부 하위 집합에서 다른 하위 집합을 사용 하 여 연락처를 잃을 때 드라이브 장애와 *대부분* 의 온라인 상태를 유지할 풀 구성 있는지 확인 해야 합니다. 확인할 수 없는 것, 오프 라인 됩니다. 풀은 오프 라인 또는 온라인 쿼럼에 대 한 충분 한 디스크 있는지에 따라 유지 하는 엔터티 (50% + 1). 풀 리소스 소유자 (활성 클러스터 노드) + 1 될 수 있습니다.

하지만 풀 쿼럼 같은 방법으로 클러스터 쿼럼에서 다르게 작동 합니다.

- 풀을 사용 하 여 한 노드에서 클러스터의는 결정권자도 감시로 통과해 절반 드라이브 모음은 (풀 리소스 소유자 인이 노드)
- 풀은 동적 쿼럼이 없습니다.
- 풀 투표 제거의 자체 버전을 구현 하지 않는

### 예

#### 4 개의 노드에 대칭 레이아웃을 사용 합니다. 
각 16 드라이브에 대 한 응답이 및 노드 2가 1 투표 (이므로 풀 리소스 소유자). *대부분* 의 전체에서 결정 됩니다 <strong>16 투표</strong>합니다. 3-4 노드 이동, 남아 있는 하위 집합에 8 드라이브 및 9/16 표는 풀 리소스 소유자가 있습니다. 따라서 풀 살아 합니다.

![풀 쿼럼 1](media/understand-quorum/pool-1.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>예</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>예</strong>. 

#### 4 개의 노드에 대칭 레이아웃 및 드라이브 실패 합니다. 
각 16 드라이브에 대 한 응답이 및 노드 2가 1 투표 (이므로 풀 리소스 소유자). *대부분* 의 전체에서 결정 됩니다 <strong>16 투표</strong>합니다. 첫째, 드라이브 7 이동합니다. 3-4 노드 이동, 남아 있는 하위 집합에 7 개의 드라이브와 8/16 표는 풀 리소스 소유자가 있습니다. 따라서 풀 대부분 없고 이동 합니다.

![풀 쿼럼 2](media/understand-quorum/pool-2.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>아니요</strong>.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>아니요</strong>. 

#### 4 개의 노드에 대칭 레이아웃을 사용 합니다. 
각 24 드라이브에 대 한 응답이 및 노드 2가 1 투표 (이므로 풀 리소스 소유자). *대부분* 의 전체에서 결정 됩니다 <strong>24 투표</strong>합니다. 3-4 노드 이동, 남아 있는 하위 집합에 8 드라이브 및 표 9/24 인 풀 리소스 소유자가 있습니다. 따라서 풀 대부분 없고 이동 합니다.

![풀 쿼럼 3](media/understand-quorum/pool-3.png)

- 하나의 서버 오류 살아 올 수: <strong>예</strong>.
- 하나의 서버 오류 다음 다른 살아 올 수: <strong>종속 </strong>(3-4 두 노드, 아래로 이동 하지만 다른 모든 시나리오를 통과해 수 존속 수 없습니다.
- 한 번에 두 가지 서버 오류를 해결 수: <strong>종속 </strong>(3-4 두 노드, 아래로 이동 하지만 다른 모든 시나리오를 통과해 수 존속 수 없습니다.

### 풀 쿼럼 권장 사항

- 클러스터의 각 노드는 대칭 되었는지 확인 (각 노드에 동일한 수의 드라이브는)
- 노드 장애를 허용 하 고 가상 디스크를 온라인 상태로 유지 수 있도록 3 방향 미러 또는 이중 패리티를 사용 합니다. 자세한 내용은 [볼륨 지침 페이지](plan-volumes.md) 를 참조 하세요.
- 두 노드는 아래쪽, 보다 더 또는 두 개의 노드 및 다른 노드에서 디스크 아래로 경우 볼륨 모든 3 개 자신의 데이터에 액세스할 수 없는 따라서 오프 라인 및 사용할 수 없습니다. 서버를 다시 가져올 또는 볼륨의 모든 데이터에 대 한 대부분의 복원 력을 위해 신속 하 게 디스크를 교체 하는 것이 좋습니다.

## 자세한 정보

- [쿼럼 구성 및 관리](../../failover-clustering/manage-cluster-quorum.md)
- [클라우드 감시 배포](../../failover-clustering/deploy-cloud-witness.md)