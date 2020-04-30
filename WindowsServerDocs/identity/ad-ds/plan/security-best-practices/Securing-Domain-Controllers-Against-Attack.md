---
ms.assetid: ba28bd05-16e6-465f-982b-df49633cfde4
title: 공격으로부터 도메인 컨트롤러 보호
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 06/18/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 24e5290bcb34860a150c8bb015c3b383c00e34b4
ms.sourcegitcommit: 11421f4005f9f3a3f6c0db95b1836d0f765a9fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81623791"
---
# <a name="securing-domain-controllers-against-attack"></a>공격으로부터 도메인 컨트롤러 보호

> 적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

*법률 번호 3: 악의적인 사용자가 컴퓨터에 대 한 물리적 액세스를 제한 하지 않는 경우 더 이상 컴퓨터가 아닙니다.* - [보안의 10 가지 불변 법 (버전 2.0)](https://technet.microsoft.com/security/hh278941.aspx)

도메인 컨트롤러는 기업에서 서버, 워크스테이션, 사용자 및 응용 프로그램을 효과적으로 관리할 수 있는 서비스 및 데이터를 제공 하는 것 외에도 AD DS 데이터베이스에 대 한 물리적 저장소를 제공 합니다. 악의적인 사용자가 도메인 컨트롤러에 대 한 권한 있는 액세스를 얻은 경우 해당 사용자는 AD DS 데이터베이스를 수정, 손상 또는 삭제 하 고, Active Directory로 관리 되는 모든 시스템 및 계정을 확장 하 여 수정할 수 있습니다.

도메인 컨트롤러는 AD DS 데이터베이스에서 데이터를 읽고 쓸 수 있기 때문에, 도메인 컨트롤러의 손상은 알려진 좋은 백업을 사용 하 여 복구 하 고 프로세스의 손상을 허용 하는 간격을 종결 하지 않는 한 Active Directory 포리스트를 신뢰할 수 있는 것으로 간주 하지 않을 수 있음을 의미 합니다.

공격자의 준비, 도구 및 기술에 따라 AD DS 데이터베이스에 대 한 수정 또는 불가능 손상은 며칠 또는 몇 주가 아니라 몇 분 내에 완료할 수 있습니다. 공격자가 Active Directory에 대 한 권한 있는 액세스 권한을 보유 하 고 있는 시간이 아니라, 권한 있는 액세스를 얻을 때 공격자가 순간에 대해 계획 한 시간입니다. 도메인 컨트롤러를 손상 시키면 광범위 한 액세스 전파에 가장 편리 하 게 사용할 수 있는 경로 또는 구성원 서버, 워크스테이션 및 Active Directory의 소멸에 대 한 가장 직접적인 경로가 제공 됩니다. 따라서 도메인 컨트롤러는 일반 Windows 인프라 보다 별도로 보호 해야 합니다.

## <a name="physical-security-for-domain-controllers"></a>도메인 컨트롤러에 대 한 물리적 보안

이 섹션에서는 도메인 컨트롤러를 물리적으로 보호 하는 방법, 도메인 컨트롤러를 물리적 컴퓨터 또는 가상 컴퓨터 인지 여부, 데이터 센터 위치, 지점 및 기본 인프라 컨트롤만 포함 된 원격 위치에 대 한 정보를 제공 합니다.

### <a name="datacenter-domain-controllers"></a>Datacenter 도메인 컨트롤러

#### <a name="physical-domain-controllers"></a>실제 도메인 컨트롤러

데이터 센터에서 실제 도메인 컨트롤러는 일반 서버 채우기와는 별개의 전용 보안 랙 또는 케이지도에 설치 해야 합니다. 가능 하면 신뢰할 수 있는 플랫폼 모듈 (TPM) 칩을 사용 하 여 도메인 컨트롤러를 구성 하 고 도메인 컨트롤러 서버의 모든 볼륨을 BitLocker 드라이브 암호화를 통해 보호 해야 합니다. 일반적으로 BitLocker는 단일 자릿수 비율로 성능 오버 헤드를 추가 하지만 서버에서 디스크를 제거 하더라도 디렉터리가 손상 되지 않도록 보호 합니다. 또한 부팅 파일을 수정 하면 원본 이진 파일을 로드할 수 있도록 서버를 복구 모드로 부팅 하기 때문에 BitLocker를 통해 이러한 공격 으로부터 시스템을 보호할 수 있습니다. 도메인 컨트롤러가 소프트웨어 RAID, 직렬 연결 SCSI, SAN/NAS 저장소 또는 동적 볼륨을 사용 하도록 구성 된 경우 BitLocker를 구현할 수 없으므로 가능 하면 도메인 컨트롤러에서 로컬로 연결 된 저장소 (하드웨어 RAID 유무)를 사용 해야 합니다.

#### <a name="virtual-domain-controllers"></a>가상 도메인 컨트롤러

가상 도메인 컨트롤러를 구현 하는 경우 도메인 컨트롤러가 환경의 다른 가상 컴퓨터와는 다른 실제 호스트에서 실행 되는지 확인 해야 합니다. 타사 가상화 플랫폼을 사용 하는 경우에도 Windows Server 2012 또는 2008 Windows server 2008 r 2의 Hyper-v 서버에 가상 도메인 컨트롤러를 배포 하는 것이 좋습니다 .이는 최소 공격 노출 영역을 제공 하 고 나머지 가상화 호스트를 사용 하 여 관리 하는 대신 호스트 하는 도메인 컨트롤러를 사용 하 여 관리할 수 있습니다. 가상화 인프라 관리를 위해 SCVMM (System Center Virtual Machine Manager)을 구현 하는 경우 도메인 컨트롤러 가상 컴퓨터가 있는 실제 호스트의 관리를 위임 하 고 도메인 컨트롤러를 권한 있는 관리자에 게 위임할 수 있습니다. 저장소 관리자가 가상 컴퓨터 파일에 액세스 하지 못하도록 가상 도메인 컨트롤러의 저장소를 분리 하는 것도 고려해 야 합니다.

### <a name="branch-locations"></a>분기 위치

#### <a name="physical-domain-controllers-in-branches"></a>분기의 실제 도메인 컨트롤러

여러 서버가 상주 하지만 데이터 센터 서버의 보안이 유지 되는 수준에 대해 물리적으로 보호 되지 않는 위치에서 실제 도메인 컨트롤러는 TPM 칩을 사용 하 여 구성 하 고 모든 서버 볼륨에 대해 BitLocker 드라이브 암호화 합니다. 도메인 컨트롤러를 분기 위치의 잠긴 방에 저장할 수 없는 경우 해당 위치에 Rodc를 배포 하는 것이 좋습니다.

#### <a name="virtual-domain-controllers-in-branches"></a>분기의 가상 도메인 컨트롤러

가능 하면 사이트의 다른 가상 컴퓨터와는 다른 실제 호스트의 지점에서 가상 도메인 컨트롤러를 실행 해야 합니다. 가상 도메인 컨트롤러를 나머지 가상 서버 채우기와는 별도의 물리적 호스트에서 실행할 수 없는 지점에서 TPM 칩을 구현 하 고 가상 도메인 컨트롤러를 실행 하는 호스트에서 가능 하면 모든 호스트에서 BitLocker 드라이브 암호화 합니다. 지점의 크기와 실제 호스트의 보안에 따라 분기 위치에 Rodc를 배포 하는 것을 고려해 야 합니다.

### <a name="remote-locations-with-limited-space-and-security"></a>공간이 제한 된 원격 위치 및 보안

인프라에 물리적 서버를 하나만 설치할 수 있는 위치가 포함 되어 있으면 가상화 작업을 실행할 수 있는 서버가 원격 위치에 설치 되어 있어야 하 고 서버에 있는 모든 볼륨을 보호 하도록 BitLocker 드라이브 암호화를 구성 해야 합니다. 서버의 가상 컴퓨터 하나는 RODC를 실행 해야 하며 다른 서버는 호스트에서 별도의 가상 컴퓨터로 실행 됩니다. RODC 배포 계획에 대 한 정보는 [읽기 전용 도메인 컨트롤러 계획 및 배포 가이드](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771744(v=ws.10))에 나와 있습니다. 가상화 된 도메인 컨트롤러를 배포 하 고 보안 하는 방법에 대 한 자세한 내용은 [hyper-v에서 도메인 컨트롤러 실행](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd363553(v=ws.10))을 참조 하세요. Hyper-v를 강화 하 고, 가상 컴퓨터 관리를 위임 하 고, 가상 컴퓨터를 보호 하는 방법에 대 한 자세한 지침은 Microsoft 웹 사이트의 [Hyper-v 보안 가이드](https://www.microsoft.com/download/details.aspx?id=16650) 솔루션 가속기를 참조 하세요.

## <a name="domain-controller-operating-systems"></a>도메인 컨트롤러 운영 체제

조직 내에서 지원 되는 최신 버전의 Windows Server에서 모든 도메인 컨트롤러를 실행 하 고 도메인 컨트롤러 채우기에 기존 운영 체제의 서비스 해제 우선 순위를 지정 해야 합니다. 도메인 컨트롤러를 최신 상태로 유지 하 고 레거시 도메인 컨트롤러를 제거 하 여 레거시 운영 체제를 실행 하는 도메인 컨트롤러가 있는 도메인 이나 포리스트에서 사용 하지 못할 수 있는 새 기능 및 보안을 자주 활용할 수 있습니다. 이전 운영 체제나 서버 역할에서 업그레이드 하지 않고 도메인 컨트롤러를 새로 설치 하 고 승격 시켜야 합니다. 즉, 도메인 컨트롤러의 전체 업그레이드를 수행 하지 않거나 운영 체제가 새로 설치 되지 않은 서버에서 AD DS 설치 마법사를 실행 합니다. 새로 설치 된 도메인 컨트롤러를 구현 하면 레거시 파일 및 설정이 실수로 도메인 컨트롤러에 남아 있지 않으며 일관 되 고 안전한 도메인 컨트롤러 구성이 적용 되는 것을 단순화할 수 있습니다.

## <a name="secure-configuration-of-domain-controllers"></a>도메인 컨트롤러의 보안 구성

Windows에 기본적으로 설치 되는 다양 한 무료 도구를 사용 하 여 이후에 Gpo에서 적용할 수 있는 도메인 컨트롤러에 대 한 초기 보안 구성 기준을 만들 수 있습니다. 이러한 도구는 여기에 설명 되어 있습니다.

### <a name="security-configuration-wizard"></a>보안 구성 마법사

초기 빌드 시 모든 도메인 컨트롤러를 잠가야 합니다. 이는 Windows Server에서 기본적으로 제공 되는 보안 구성 마법사를 사용 하 여 "기본 빌드" 도메인 컨트롤러에서 서비스, 레지스트리, 시스템 및 WFAS 설정을 구성 하는 데 사용할 수 있습니다. 도메인 컨트롤러에 대 한 일관 된 구성을 적용 하기 위해 포리스트의 각 도메인에서 도메인 컨트롤러 OU에 연결할 수 있는 GPO로 설정을 저장 하 고 내보낼 수 있습니다. 도메인에 여러 버전의 Windows 운영 체제를 포함 하는 경우 해당 운영 체제 버전을 실행 하는 도메인 컨트롤러에만 Gpo를 적용 하도록 WMI (WMI(Windows Management Instrumentation)) 필터를 구성할 수 있습니다.

### <a name="microsoft-security-compliance-toolkit"></a>Microsoft 보안 규정 준수 도구 키트

[Microsoft 보안 준수 도구 키트](https://microsoft.com/download/details.aspx?id=55319) 도메인 컨트롤러 설정은 보안 구성 마법사 설정과 함께 사용 하 여 Active Directory의 도메인 컨트롤러 OU에 배포 된 gpo에 의해 배포 및 적용 되는 도메인 컨트롤러에 대 한 포괄적인 구성 기준을 생성할 수 있습니다.

### <a name="rdp-restrictions"></a>RDP 제한

포리스트의 모든 도메인 컨트롤러 Ou에 연결 된 그룹 정책 개체는 권한 있는 사용자 및 시스템 (예: 점프 서버) 에서만 RDP 연결을 허용 하도록 구성 해야 합니다. 이는 사용자 권한 설정 및 WFAS 구성을 조합 하 여 수행할 수 있으며 정책이 일관 되 게 적용 되도록 Gpo에 구현 해야 합니다. 무시 되는 경우 다음 그룹 정책 새로 고침은 시스템을 적절 한 구성으로 되돌립니다.

### <a name="patch-and-configuration-management-for-domain-controllers"></a>도메인 컨트롤러에 대 한 패치 및 구성 관리

직관적 보일 수도 있지만, 일반적인 Windows 인프라와 별도로 도메인 컨트롤러 및 기타 중요 인프라 구성 요소를 패치 하는 것이 좋습니다. 인프라의 모든 컴퓨터에 대해 엔터프라이즈 구성 관리 소프트웨어를 활용 하는 경우 시스템 관리 소프트웨어의 손상으로 해당 소프트웨어에서 관리 하는 모든 인프라 구성 요소를 손상 시키거나 삭제할 수 있습니다. 일반 채우기에서 도메인 컨트롤러에 대 한 패치 및 시스템 관리를 분리 하 여 도메인 컨트롤러에 설치 된 소프트웨어의 양을 줄이는 동시에 해당 관리를 긴밀 하 게 제어할 수 있습니다.

### <a name="blocking-internet-access-for-domain-controllers"></a>도메인 컨트롤러에 대 한 인터넷 액세스 차단

Active Directory 보안 평가의 일부로 수행 되는 확인 중 하나는 도메인 컨트롤러에서 Internet Explorer를 사용 하 고 구성 하는 것입니다. Internet Explorer (또는 다른 웹 브라우저)는 도메인 컨트롤러에서 사용할 수 없지만, 수천 개의 도메인 컨트롤러를 분석 하면 권한 있는 사용자가 Internet Explorer를 사용 하 여 조직의 인트라넷 또는 인터넷을 탐색 하는 수많은 경우가 나타났습니다.

이전에 [손상](../../../ad-ds/plan/security-best-practices/Avenues-to-Compromise.md)된 항목의 "잘못 된 구성" 섹션에서 설명한 것 처럼, 높은 권한의 계정을 사용 하 여 Windows 인프라에서 가장 강력한 컴퓨터 중 하나 (또는 감염 된 인트라넷)에서 인터넷 (또는 감염 된 인트라넷)을 탐색 하면 조직의 보안에 매우 위험을 초래할 수 있습니다. 다운로드 또는 맬웨어 감염 "유틸리티를 다운로드 하 여 드라이브를 통해 실행 하는 경우에는 공격자가 Active Directory 환경을 완전히 손상 또는 제거 하는 데 필요한 모든 항목에 대 한 액세스 권한을 얻을 수 있습니다.

Windows Server 2012, Windows Server 2008 R2, Windows Server 2008 및 현재 버전의 Internet Explorer는 악의적인 다운로드에 대해 다양 한 보호 기능을 제공 합니다. 대부분의 경우 도메인 컨트롤러 및 권한 있는 계정을 사용 하 여 인터넷을 검색 하거나, 도메인 컨트롤러에서 Windows Server 2003을 실행 했거나, 최신 운영 체제 및 브라우저에서 제공 하는 보호를 의도적으로 사용 하지 않도록 설정 했습니다.

도메인 컨트롤러에서 웹 브라우저를 시작 하는 것은 정책 뿐만 아니라 기술 제어와 도메인 컨트롤러에서 인터넷에 액세스 하도록 허용 해서는 안 됩니다. 도메인 컨트롤러를 사이트 간에 복제 해야 하는 경우 사이트 간에 보안 연결을 구현 해야 합니다. 자세한 구성 지침은이 문서의 범위를 벗어나므로 도메인 컨트롤러의 오용 또는 잘못 된 기능을 제한 하는 다양 한 컨트롤을 구현 하 여 이후에 손상 시킬 수 있습니다.

### <a name="perimeter-firewall-restrictions"></a>경계 방화벽 제한

경계 방화벽은 도메인 컨트롤러에서 인터넷으로의 아웃 바운드 연결을 차단 하도록 구성 되어야 합니다. 도메인 컨트롤러는 사이트 경계를 넘어 통신 해야 할 수도 있지만, Microsoft 지원 웹 사이트에서 [Active Directory 도메인 및 트러스트에 대 한 방화벽을 구성 하는 방법](https://support.microsoft.com/kb/179442) 에 제공 된 지침에 따라 사이트 간 통신을 허용 하도록 경계 방화벽을 구성할 수 있습니다.

### <a name="dc-firewall-configurations"></a>DC 방화벽 구성

앞에서 설명한 대로 보안 구성 마법사를 사용 하 여 도메인 컨트롤러에 대 한 고급 보안이 포함 된 Windows 방화벽에 대 한 구성 설정을 캡처해야 합니다. 보안 구성 마법사의 출력을 검토 하 여 방화벽 구성 설정이 조직의 요구 사항을 충족 하는지 확인 한 다음 Gpo를 사용 하 여 구성 설정을 적용 해야 합니다.

### <a name="preventing-web-browsing-from-domain-controllers"></a>도메인 컨트롤러에서 웹 검색 방지

AppLocker 구성, "블랙홀" 프록시 구성 및 WFAS 구성의 조합을 사용 하 여 도메인 컨트롤러가 인터넷에 액세스 하는 것을 방지 하 고 도메인 컨트롤러에서 웹 브라우저를 사용 하지 못하게 할 수 있습니다.
