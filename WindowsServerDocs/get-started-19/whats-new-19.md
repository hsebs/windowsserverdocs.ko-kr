---
title: Windows Server 2019의 새로운 기능
description: 데스크톱 경험, 스토리지 마이그레이션 서비스, 시스템 인사이트, Azure 네트워크 어댑터를 포함한 Windows Server 2019의 새로운 기능, 스토리지 공간 다이렉트의 개선 사항 및 기타 변경에 대한 개요입니다.
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
author: jasongerend
ms.author: jgerend
ms.localizationpriority: high
ms.date: 06/04/2019
ms.openlocfilehash: 47269fbfac6aea3fe46513ad67d2cfa2f0c9b78e
ms.sourcegitcommit: 3c3dfee8ada0083f97a58997d22d218a5d73b9c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80639924"
---
# <a name="whats-new-in-windows-server-2019"></a>Windows Server 2019의 새로운 기능

> 적용 대상: 시작

이 항목에서는 Windows Server 2019의 새로운 기능 몇 가지를 설명합니다. Windows Server 2019는 Windows Server 2016의 강력한 파운데이션을 기반으로 빌드되고 다음 네 가지 주요 테마를 여러 방면으로 혁신합니다. 하이브리드 클라우드, 보안, 애플리케이션 플랫폼 및 하이퍼 컨버지드 인프라(HCI)

Windows Server 반기 채널 릴리스의 새로운 기능을 알아보려면 [Windows Server의 새로운 기능](../get-started/whats-new-in-windows-server.md)을 참조하세요.

## <a name="general"></a>일반

### <a name="windows-admin-center"></a>Windows Admin Center

Windows Admin Center는 서버, 클러스터, 하이퍼 컨버지드 인프라 및 Windows 10 PC를 관리하기 위해 로컬로 배포된 브라우저 기반 애플리케이션입니다. Windows 이외의 추가 비용 없이 제공되며 프로덕션 환경에서 사용할 준비가 되었습니다.

Windows Server 2019 뿐만 아니라 Windows 10과 Windows 및 Windows Server의 이전 버전에 Windows Admin Center를 설치하고, Windows Server 2008 R2 이상을 실행하는 서버 및 클러스터를 관리하는 데 사용할 수 있습니다.

자세한 내용은 [Windows Admin Center](../manage/windows-admin-center/understand/windows-admin-center.md)를 참조하세요.

### <a name="desktop-experience"></a>데스크톱 환경

Windows Server 2019는 장기 서비스 채널(LTSC) 릴리스이므로 <b>데스크톱 환경</b>이 포함되어 있습니다. (반기 채널\(SAC\) 릴리스는 디자인에서 데스크톱 환경을 포함하지 않으며, Server Core 및 Nano Server 컨테이너 이미지 릴리스에만 해당됩니다.) Windows Server 2016과 마찬가지로 운영 체제 설치 도중 Server Core 설치 또는 데스크톱 환경 포함 서버 설치 중에서 선택할 수 있습니다.

### <a name="system-insights"></a>시스템 인사이트

시스템 인사이트는 Windows Server 2019의 새 기능으로 Windows Server에 기본적인 로컬 예측 분석 기능을 제공합니다. 기계 학습 모델의 지원을 받는 이러한 예측 기능은 성능 카운터 및 이벤트와 같은 Windows Server 시스템 데이터를 로컬 방식으로 분석하여 서버의 작동에 대한 인사이트를 제공하고, Windows Server 배포 문제를 효과적으로 관리하는 데 필요한 운영 비용을 줄이도록 도와줍니다.

## <a name="hybrid-cloud"></a>하이브리드 클라우드

### <a name="server-core-app-compatibility-feature-on-demand"></a>Server Core 앱 호환성 FOD(Feature on Demand)

[Server Core 앱 호환성 FOD(Feature on Demand)](https://docs.microsoft.com/windows-server/get-started-19/install-fod-19)는 Windows Server 데스크톱 환경 그래픽 환경 자체의 추가 없이 Windows Server의 바이너리 및 구성 요소 하위 세트를 데스크톱 환경에 포함함으로써 Windows Server Core 설치의 앱 호환성을 크게 개선합니다.  이를 통해 간소함을 유지하면서 Server Core의 기능 및 호환성을 높입니다.  

이 FOD(Feature on Demand) 옵션은 별도의 ISO에서 사용할 수 있으며 DISM을 사용하여 Windows Server Core 설치 및 이미지에만 추가할 수 있습니다. 

## <a name="security"></a>보안

### <a name="windows-defender-advanced-threat-protection-atp"></a>Windows Defender ATP(Advanced Threat Protection)

ATP의 심층적인 플랫폼 센서와 응답 작업은 메모리 및 커널 수준 공격을 공개하고 악의적인 파일을 제거하고 악의적인 프로세스를 종료시켜 이에 대응합니다.

-   Windows Defender ATP에 대한 자세한 내용은 [Windows Defender ATP 기능 개요](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/overview)를 참조하세요.

-   서버 온보딩에 대한 자세한 내용은 [Windows Defender ATP 서비스에 서버 온보딩](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-server-endpoints-windows-defender-advanced-threat-protection)을 참조하세요.

**Windows Defender ATP Exploit Guard**는 새로운 호스트 침입 방지 기능 세트입니다. Windows Defender Exploit Guard의 4가지 구성 요소는 다양한 공격 벡터에 대해 디바이스를 잠그고 맬웨어 공격에서 일반적으로 사용되는 동작을 차단하면서 보안 위험과 생산성 요구 사항 사이의 균형을 맞출 수 있도록 합니다.

-   [ASR(공격 범위 축소)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard?ocid=cx-blog-mmpc)은 엔터프라이즈에서 의심스러운 악성 파일(예: Office 파일), 스크립트, 측면 이동, 랜섬웨어 동작 및 이메일 기반 위협을 차단하여 머신에서 맬웨어를 방지할 수 있도록 하는 제어 세트입니다.

-   [네트워크 보호](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/network-protection)는 Windows Defender SmartScreen을 통해 디바이스에서 신뢰할 수 없는 호스트/IP 주소에 대한 모든 아웃바운드 프로세스를 차단하여 웹 기반 위협으로부터 엔드포인트를 보호합니다.

-   [제어된 폴더 액세스](https://cloudblogs.microsoft.com/microsoftsecure/2017/10/23/stopping-ransomware-where-it-counts-protecting-your-data-with-controlled-folder-access/?ocid=cx-blog-mmpc?source=mmpc)는 신뢰할 수 없는 프로세스가 보호되는 폴더로 액세스하는 것을 차단하여 랜섬웨어로부터 민감한 데이터를 보호합니다.

-   [Exploit Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/exploit-protection-exploit-guard)은 시스템 및 애플리케이션 보호를 위해 손쉽게 구성할 수 있는 취약성 악용(EMET 대체)에 대한 완화 세트입니다.

[Windows Defender Application Control](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)(CI(코드 무결성) 정책이라고도 함)은 Windows Server 2016에서 릴리스되었습니다.
훌륭한 개념이지만 배포하기 어렵다는 고객 피드백이 있었습니다.
이 문제를 해결하기 위해 모든 Windows 기본 제공 파일 및 SQL Server와 같은 Microsoft 애플리케이션을 허용하고 CI를 우회할 수 있는 알려진 실행 파일을 차단하는 기본 CI 정책을 빌드했습니다. 

### <a name="security-with-software-defined-networking-sdn"></a>SDN(소프트웨어 정의 네트워킹)을 사용한 보안

[SDN을 사용한 보안](https://docs.microsoft.com/windows-server/networking/sdn/security/sdn-security-top)은 고객이 온-프레미스 또는 클라우드에서 서비스 공급 기업으로서 워크로드를 실행하는 데 있어 고객의 신뢰를 높이는 많은 기능을 제공합니다. 

이러한 보안 개선 사항이 Windows Server 2016에 도입된 포괄적 SDN 플랫폼에 통합되어 있습니다.

SDN의 새 기능에 대한 전체 목록은 [Windows Server 2019용 SDN의 새로운 기능](https://docs.microsoft.com/windows-server/networking/sdn/sdn-whats-new)을 참조하세요.

### <a name="shielded-virtual-machines-improvements"></a>보호된 Virtual Machine 개선 사항

- **지점 개선 사항**

    새로운 [대체 HGS](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-manage-branch-office#fallback-configuration) 및 [오프라인 모드](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-manage-branch-office#offline-mode) 기능을 활용하여 호스트 보호 서비스에 대한 지속적 연결을 통해 머신에서 보호된 가상 머신을 실행할 수 있습니다. 대체 HGS를 통해 Hyper-V에 대한 보조 URL 세트를 구성하여 주 HGS 서버에 도달할 수 없는 경우 시도할 수 있습니다.

    오프라인 모드를 사용하여 HGS에 도달할 수 없는 경우에도 VM이 성공적으로 시작되고 호스트의 보안 구성이 변경되지 않는 한 보호된 VM을 계속해서 시작할 수 있습니다.

- **문제 해결 개선 사항**

    VMConnect 고급 세션 모드 및 PowerShell Direct에 대한 지원을 활성화하여 [보호된 가상 머신 문제 해결](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-shielded-vms)이 더욱 쉬워지도록 했습니다. 이러한 도구는 VM에 대한 네트워크 연결이 끊기고 구성을 업데이트하여 액세스를 복원해야 하는 경우 특히 유용합니다. 

    이러한 기능은 구성될 필요가 없고, Windows Server 버전 1803 이상을 실행하는 Hyper-V 호스트에 보호된 VM이 배치되는 경우 자동으로 사용할 수 있습니다.

- **Linux 지원**

    혼합 OS 환경을 실행하는 경우 Windows Server 2019에서 이제 보호된 가상 머신 내 Ubuntu, Red Hat Enterprise Linux 및 SUSE Linux Enterprise Server 실행을 지원합니다.

### <a name="http2-for-a-faster-and-safer-web"></a>더욱 빠르고 안전한 웹을 위한 HTTP/2

- 개선된 연결 결합으로 무중단의 적절히 암호화된 브라우징 환경을 제공합니다.

- 업그레이드된 HTTP/2의 서버 측 암호 그룹 협상으로 연결 오류의 자동 완화와 손쉬운 배포가 가능합니다.

- 기본 TCP 정체 공급 기업을 Cubic으로 변경하여 더 많은 처리량을 제공합니다!

## <a name="storage"></a>스토리지

Windows Server 2019의 스토리지에 대한 변경 사항은 다음과 같습니다. 자세한 내용은 [스토리지의 새로운 기능](../storage/whats-new-in-storage.md)을 참조하세요.

### <a name="storage-migration-service"></a>스토리지 마이그레이션 서비스

스토리지 마이그레이션 서비스는 서버를 Windows Server의 최신 버전으로 쉽게 마이그레이션할 수 있는 새로운 기술입니다. 서버의 데이터를 인벤토리화하는 그래픽 도구를 제공하며, 데이터 및 구성을 최신 서버로 전송한 다음, 선택적으로 이전 서버의 ID를 새로운 서버로 이동하여 앱 및 사용자가 아무 것도 변경할 필요가 없도록 합니다. 자세한 내용은 [스토리지 마이그레이션 서비스](../storage/storage-migration-service/overview.md)를 참조하세요.

### <a name="storage-spaces-direct"></a>직접 스토리지 공간

스토리지 공간 다이렉트의 새로운 기능 목록은 다음과 같습니다. 자세한 내용은 [스토리지 공간 다이렉트의 새로운 기능](../storage/whats-new-in-storage.md#storage-spaces-direct)을 참조하세요. 또한 유효성 검사된 스토리지 공간 다이렉트 시스템 획득에 대한 정보는 [Azure Stack HCI](https://docs.microsoft.com/azure-stack/operator/azure-stack-hci-overview)를 참조하세요.

- **ReFS 볼륨에 대한 중복 제거 및 압축**
- **영구 메모리에 대한 기본 지원**
- **에지에서 2개 노드 하이퍼 컨버지드 인프라에 대한 중첩된 복원력**
- **USB 플래시 드라이브를 감시로 사용하는 2개 서버 클러스터**
- **Windows Admin Center 지원**
- **성능 기록**
- **클러스터당 최대 4PB까지 확장**
- **2배 빠른 미러 가속 패리티**
- **드라이브 대기 시간 아웃라이어 감지**
- **내결함성을 강화하기 위해 수동으로 볼륨의 할당을 구분**

### <a name="storage-replica"></a>스토리지 복제본

스토리지 복제본의 새로운 기능은 다음과 같습니다. 자세한 내용은 [스토리지 복제본의 새로운 기능](../storage/whats-new-in-storage.md#storage-replica)을 참조하세요.

- 스토리지 복제본은 이제 Windows Server 2019 Standard Edition에서 사용할 수 있습니다.
- 테스트 장애 조치(failover)는 복제 또는 백업 데이터의 유효성을 검사하기 위해 대상 스토리지를 탑재하도록 하는 새로운 기능입니다. 자세한 내용은 [스토리지 복제본에 대한 질문과 대답](../storage/storage-replica/storage-replica-frequently-asked-questions.md)을 참조하세요.
- 스토리지 복제본 로그 성능 향상
- Windows Admin Center 지원

## <a name="failover-clustering"></a>장애 조치(failover) 클러스터링

장애 조치(failover) 클러스터링의 새로운 기능 목록입니다. 자세한 내용은 [장애 조치(failover) 클러스터링의 새로운 기능](../failover-clustering/whats-new-in-failover-clustering.md)을 참조하세요.

- **클러스터 세트**
- **Azure 인식 클러스터**
- **도메인 간 클러스터 마이그레이션**
- **USB 감시**
- **클러스터 인프라 개선**
- **클러스터 인식 업데이트에서 스토리지 공간 다이렉트 지원**
- **파일 공유 감시 개선**
- **클러스터 강화**
- **장애 조치(failover) 클러스터는 더 이상 NTLM 인증을 사용하지 않음**

## <a name="application-platform"></a>애플리케이션 플랫폼

### <a name="linux-containers-on-windows"></a>Windows의 Linux 컨테이너

이제 동일한 Docker 데몬을 사용하여 동일한 컨테이너 호스트에서 Windows 및 Linux 기반 컨테이너를 실행할 수 있습니다. 이를 통해 애플리케이션 개발자에게 유연성을 제공하면서 다른 유형의 컨테이너 호스트 환경을 유지할 수 있습니다.

### <a name="built-in-support-for-kubernetes"></a>Kubernetes에 대한 기본 제공 지원

Windows Server 2019에서는 반기 채널 릴리스부터 Windows에서 Kubernetes를 지원하는 데 필요한 컴퓨팅, 네트워킹 및 스토리지 개선을 지속하고 있습니다. 자세한 내용은 이후 Kubernetes 릴리스에서 사용할 수 있습니다.

- Windows Server 2019의 [컨테이너 네트워킹](https://docs.microsoft.com/windows-server/networking/sdn/technologies/containers/container-networking-overview)은 플랫폼 네트워킹 복원력과 컨테이너 네트워킹 플러그 인 지원 향상을 통해 Windows에서 Kubernetes의 사용 편의성을 크게 개선합니다.

- Kubernetes에 배포된 워크로드는 네트워크 보안을 사용하여 포함된 도구를 사용한 Linux 및 Windows 서비스를 모두 보호할 수 있습니다.

### <a name="container-improvements"></a>컨테이너 개선
    
- **통합 ID 개선**

    컨테이너의 Windows 통합 인증을 더욱 간편하고 안정적으로 만들어 Windows Server 이전 버전의 여러 제한 사항을 해결했습니다.

- **더욱 뛰어난 애플리케이션 호환성**

    Windows 기반 애플리케이션 컨테이너화가 쉬워졌습니다. 기존 *windowsservercore* 이미지에 대한 앱 호환성이 증가했습니다. 추가 API 종속성이 포함된 애플리케이션의 경우 *windows*라는 세 번째 기본 이미지가 있습니다.

- **크기 감소 및 성능 증가**

    기본 컨테이너 이미지 다운로드 크기, 디스크 크기 및 시작 시간이 개선되었습니다. 컨테이너 워크플로 속도 증가

- **Windows Admin Center\(미리 보기\)를 사용한 관리 환경**

    컴퓨터에서 실행하는 컨테이너를 확인하고 Windows Admin Center에 대한 새 확장을 사용한 개별 컨테이너 관리가 쉬워졌습니다. [Windows Admin Center 공개 피드](https://docs.microsoft.com/windows-server/manage/windows-admin-center/configure/using-extensions)에서 "컨테이너" 확장을 찾아보세요.

### <a name="encrypted-networks"></a>암호화된 네트워크

[암호화된 네트워크](https://docs.microsoft.com/windows-server/networking/sdn/sdn-whats-new) - 가상 네트워크 암호화는 **암호화 사용**으로 표시된 서브넷 내에서 각각 통신하는 가상 머신 간 가상 네트워크 트래픽의 암호화를 허용합니다. 또한 가상 서브넷의 DTLS(데이터그램 전송 계층 보안)를 활용하여 패킷을 암호화합니다. DTLS는 실제 네트워크에 액세스하는 누군가에 의한 도청, 변조 및 위조를 방지합니다.

### <a name="network-performance-improvements-for-virtual-workloads"></a>가상 워크로드에 대한 네트워크 성능 개선

[가상 워크로드에 대한 네트워크 성능 개선](https://docs.microsoft.com/windows-server/networking/technologies/hpn/hpn-insider-preview)으로 호스트의 지속적인 조정 또는 과잉 프로비저닝 없이 가상 머신에 대한 네트워크 처리량을 극대화합니다. 이를 통해 호스트의 사용 가능한 밀도를 높이면서 운영 및 유지 관리 비용을 절감합니다. 새로운 기능은 다음과 같습니다.

* vSwitch의 수신 세그먼트 통합

* d.VMMQ(동적 가상 머신 큐)

### <a name="low-extra-delay-background-transport"></a>Low Extra Delay Background Transport

LEDBAT(Low Extra Delay Background Transport)는 네트워크가 사용 중이지 않을 때 사용 가능한 전체 대역폭을 소모하면서 사용자 및 애플리케이션에 대한 대역폭을 자동으로 생성하도록 설계된 대기 시간 최적화 네트워크 정체 제어 공급 기업입니다.   
이 기술은 고객 대면 서비스와 관련 대역폭에 영향을 미치지 않으면서 IT 환경에 걸쳐 대용량의 중요 업데이트를 배포하는 데 사용됩니다.

### <a name="windows-time-service"></a>Windows 시간 서비스

[Windows 시간 서비스](https://docs.microsoft.com/windows-server/networking/windows-time-service/insider-preview)에는 UTC 준수 윤초 지원, 새로운 시간 프로토콜(Precision Time Protocol) 및 엔드투엔드 추적성이 포함되어 있습니다.


### <a name="high-performance-sdn-gateways"></a>고성능 SDN 게이트웨이

Windows Server 2019의 [고성능 SDN 게이트웨이](https://docs.microsoft.com/windows-server/networking/sdn/gateway-performance)는 IPsec 및 GRE 연결 성능을 크게 개선하여 더 적은 CPU 활용률로 매우 높은 성능 처리량을 보장합니다.
<br/>

### <a name="new-deployment-ui-and-windows-admin-center-extension-for-sdn"></a>SDN에 대한 새 배포 UI 및 Windows Admin Center 확장

Windows Server 2019의 새 배포 UI 및 Windows Admin Center 확장을 이용하면 어느 사용자든 SDN의 성능을 활용하여 손쉽게 배포, 관리 작업을 수행할 수 있습니다. 

### <a name="persistent-memory-support-for-hyper-v-vms"></a>Hyper-V VM에 대한 영구 메모리 지원

가상 머신에서 높은 처리량과 낮은 대기 시간의 영구 메모리( 스토리지 클래스 메모리)를 활용하기 위해 VM에 직접 프로젝션할 수 있습니다. 이는 데이터베이스 트랜잭션 대기 시간을 크게 단축하고 오류가 발생한 낮은 대기 시간의 메모리 내 데이터베이스의 복구 시간을 줄이는 데 도움이 될 수 있습니다.

