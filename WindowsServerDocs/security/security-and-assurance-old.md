---
title: 보안 및 보증
description: Windows Server 2016의 보안 개요
ms.prod: windows-server
ms.technology: techgroup-security
ms.topic: article
ms.date: 07/27/2018
ms.assetid: b886b2fd-3567-4f0a-8aa3-4ba7923d2d21
author: coreyp-at-msft
ms.author: coreyp
ms.localizationpriority: medium
ms.openlocfilehash: ec389fab792ecc714684ff5f8976845b5cea05ba
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859336"
---
# <a name="security-and-assurance-in-windows-server"></a>Windows Server의 보안 및 보증 

>적용 대상: Windows Server(반기 채널), Windows Server 2016

>[!TIP]
> 이전 버전의 Windows Server에 대한 자세한 내용이 궁금하십니까? docs.microsoft.com에서 다른 [Windows Server 라이브러리](/previous-versions/windows/)를 확인할 수 있습니다. 또한 특정 정보에 대해 [이 사이트를 검색](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions)할 수 있습니다.

<img src="../media/landing-icons/security.png" style='float:left; padding:.5em;' alt="Icon representing a lock"> 운영 체제에 기본 제공되는 새로운 보호 계층을 사용하여 보안 위반에 대한 보안을 강화할 수 있습니다. 악의적인 공격을 차단하고 가상 컴퓨터, 애플리케이션 및 데이터의 보안을 강화합니다.


### <a name="windows-server-security-blog-post"></a>[Windows Server 보안 블로그 게시물](https://blogs.technet.microsoft.com/windowsserver/2016/04/25/ten-reasons-youll-love-windows-server-2016-8-security/)
Windows Server 보안 팀이 작성한 이 블로그 게시물은 호스팅 및 하이브리드 클라우드 환경에 대한 보안을 강화하는 Windows Server의 다양 한 개선 사항에 대해 다룹니다.

### <a name="datacenter-and-private-cloud-security-blog"></a>[데이터 센터 및 사설 클라우드 보안 블로그](https://blogs.technet.microsoft.com/datacentersecurity/)
Microsoft 데이터 센터 및 프라이빗 클라우드 보안 팀의 기술 콘텐츠를 제공하는 중앙 블로그 사이트입니다.                                    

### <a name="addressing-emerging-threats-and-landscape-shifts"></a>[새로운 위협 및 가로 변화 해결](https://www.youtube.com/watch?v=B5JMYxYWx1k&feature=youtu.be)
이 6분짜리 비디오에서는 Anders Vinberg가 Microsoft의 보안 및 보증 전략에 대한 개요를 제공하고 보안과 관련된 산업 동향 및 환경 변화를 논의합니다. 그런 다음 기본 패브릭에서 워크로드를 보호하고 권한 있는 계정의 직접적인 공격으로부터 보호하려는 Microsoft의 핵심 이니셔티브를 강조합니다. 마지막으로 위반이 발생한 경우 새로운 감지 및 포렌식 기능을 통해 위협을 보다 효과적으로 식별할 수 있는 방법을 설명합니다.

### <a name="protecting-your-datacenter-and-cloud-from-emerging-threats-blog-post"></a>[새로운 위협 으로부터 데이터 센터 및 클라우드 보호 블로그 게시물](https://blogs.technet.com/b/windowsserver/archive/2015/11/18/protecting-your-datacenter-and-cloud-november-update.aspx)
이 블로그 게시물에서는 Microsoft 기술을 사용하여 새로운 위협으로부터 데이터 센터 및 클라우드 투자를 보호하는 방법을 설명합니다.                   

### <a name="security-and-assurance-overview-session-at-ignite"></a>[Ignite의 보안 및 보증 개요 세션](https://channel9.msdn.com/events/ignite/2015/brk2482)
이 Ignite 세션에서는 영구 위협, 내부자 위반, 조직적인 사이버 범죄 침해, 구성 된 사이버 및 Microsoft 클라우드 플랫폼(온-프레미스 및 Azure와 연결된 서비스) 보안을 다룹니다. 여기에는 워크로드, 대기업 테넌트 및 서비스 공급자 보안에 대한 시나리오가 포함되어 있습니다.                                                                   

## <a name="secure-virtualization-with-shielded-vms"></a>보호된 VM으로 보안된 가상화

### <a name="shielded-vm-in-channel-9"></a>[Channel 9에서 보호된 VM](https://channel9.msdn.com/Shows/Mechanics/Introduction-to-Shielded-Virtual-Machines-in-Windows-Server-2016)
보호된 VM 기술 및 혜택을 안내합니다.                           

### <a name="shielded-vm-demo"></a>[보호된 VM 데모](https://www.youtube.com/watch?v=xip5Qtk-7d8)
이 4분짜리 비디오에서는 보호된 VM의 가치 및 보호된 VM과 보호되지 않은 VM의 차이점을 설명합니다.                                   

### <a name="shielded-virtual-machines-in-windows-server-video-walkthrough"></a>[Windows Server의 보호된 Virtual Machine 비디오 연습](http://microsoft-cloud.cloudguides.com/Guides/Shielded Virtual Machines in Windows Server.htm)
이 비디오 연습에서는 호스트 보호 서비스가 Hyper-V 호스트 관리자의 무단 액세스로부터 중요한 데이터를 보호할 수 있도록 보호된 가상 컴퓨터를 지원하는 방식을 보여 줍니다.

### <a name="harden-the-fabric-protecting-tenant-secrets-in-hyper-v-ignite-video"></a>[패브릭 강화: Hyper-v에서 테 넌 트 비밀 보호 (Ignite 비디오)](https://channel9.msdn.com/events/ignite/2015/brk3457)

이 Ignite 프레젠테이션은 보호된 VM을 사용하도록 설정하기 위해 Hyper-V Virtual Machine Manager, 새 호스트 보호 서비스 서버 역할에서 개선된 사항에 대해 논의합니다.                

### <a name="guarded-fabric-deployment-guide"></a>[보호된 패브릭 배포 가이드](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-deploying-hgs-overview)
이 가이드에서는 보호된 패브릭 호스트 및 보호된 VM용 Windows Server 및 System Center Virtual Machine Manager의 설치 및 유효성 검사 정보를 제공합니다.

### <a name="shielded-vm-and-guarded-fabric-in-branch-offices"></a>[지사의 보호된 VM 및 보호된 패브릭](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-manage-branch-office)
이 가이드는 HGS에 대해 Hyper-V 호스트의 연결이 제한된 시간이 있을 수 있는 지사 및 기타 원격 시나리오에서 보호된 가상 컴퓨터를 실행하는 모범 사례를 제공합니다.

### <a name="shielded-vm-and-guarded-fabric-troubleshooting-guide"></a>[보호된 VM 및 보호된 패브릭 문제 해결 가이드](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-overview)
이 가이드에서는 보호된 VM 환경에서 발생할 수 있는 문제를 해결하는 방법에 대한 정보를 제공합니다.

### <a name="shielded-vm-article"></a>[보호된 VM 문서](http://windowsitpro.com/hyper-v/super-secure-hyper-v-environments-shielded-vms-2016)
이 백서에서는 보호된 VM이 전반적인 보안을 강화하여 변조를 방지하는 방법에 대한 개요를 제공합니다.                                         

## <a name="privileged-access-management"></a>권한 있는 액세스 관리
### <a name="securing-privileged-access"></a>[권한 있는 액세스 보안](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access)
권한 있는 액세스를 보호하는 방법에 대한 로드맵 이 로드맵은 서버 보안 팀, Microsoft IT, Azure 팀 및 Microsoft Consulting Services의 모든 전문 기술을 집약하여 작성되었습니다.                           

### <a name="just-in-time-administration-with-microsoft-identity-manager"></a>[Microsoft Identity Manager를 사용한 JIT(Just in Time) 관리](https://technet.microsoft.com/library/mt150258.aspx)
이 문서에서는 JIT(Just In Time) 권한 있는 액세스 관리 지원을 비롯하여 Microsoft Identity Manager에 포함된 기능을 설명합니다.                                                                    

### <a name="protecting-windows-and-microsoft-azure-active-directory-with-privileged-access-management"></a>[권한 있는 액세스 관리로 Windows 및 Microsoft Azure Active Directory 보호](https://channel9.msdn.com/events/ignite/2015/brk3873)
이 Ignite 프레젠테이션에서는 보다 강력한 인증을 통해 관리자 액세스의 위험을 해결하고 Just in Time 및 JEA(Just Enough Administration)를 사용하여 액세스를 관리하기 위해 이루어진 Windows Server, PowerShell, Active Directory, Identity Manager 및 Azure Active Directory에 대한 Microsoft의 투자 및 전략을 다룹니다.

### <a name="just-enough-administration-article"></a>[JEA(Just Enough Administration) 문서](https://aka.ms/JEA)
이 문서에서는 운영자가 특정 작업을 수행하는 데 필요한 범위에서만 액세스할 수 있도록 제한하여 조직에서 위험을 낮추도록 설계된 PowerShell 도구 키트인 Just Enough Administration의 비전과 기술 정보를 설명합니다.

### <a name="just-enough-administration-demo-video"></a>[JEA(Just Enough Administration) 데모 비디오](https://www.youtube.com/watch?v=xnBrbkY9P20)
JEA(Just Enough Administration) 데모 연습입니다.                                                                                                                  
## <a name="credential-protection"></a>자격 증명 보호

### <a name="protect-derived-domain-credentials-with-credential-guard"></a>[Credential Guard를 사용하여 파생된 도메인 자격 증명 보호](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)
Credential Guard는 가상화 기반 보안을 사용하여 권한 있는 시스템 소프트웨어만 액세스할 수 있도록 암호를 격리합니다. 이 암호에 대한 무단 액세스가 일어나면 Pass-the-Hash 또는 Pass-The-Ticket 같은 자격 증명 도난 공격이 발생할 수 있습니다. Credential Guard에서는 NTLM 암호 해시 및 Kerberos 허용 티켓을 보호하여 이러한 공격을 방지합니다.

### <a name="protect-remote-desktop-credentials-with-remote-credential-guard"></a>[원격 Credential Guard를 사용하여 원격 데스크톱 자격 증명 보호](https://docs.microsoft.com/windows/security/identity-protection/remote-credential-guard)
원격 Credential Guard를 사용하면 연결을 요청하는 디바이스로 Kerberos 요청을 다시 리디렉션하여 원격 데스크톱 연결을 통해 자격 증명을 보호할 수 있습니다. 또한 원격 데스크톱 세션에 대한 Single Sign On을 제공합니다.                                                                                                        |
### <a name="credential-guard-demo-video"></a>[Credential Guard 데모 비디오](https://www.youtube.com/watch?v=eUpKOGSl7yk)
이 5분짜리 비디오는 Credential Guard 및 원격 Credential Guard 데모를 보여줍니다.         

## <a name="hardening-the-os-and-applications"></a>OS 및 애플리케이션 보안 강화
### <a name="windows-defender-application-control-wdac-deployment-guide"></a>[Windows Defender Application Control(WDAC) 배포 가이드](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)
WDAC는 기업이 자신의 환경에서 응용 프로그램이 실행하는 것을 제어하도록 돕고 Windows 10을을 실행하는 것 이외에 특정 하드웨어 또는 소프트웨어 요구 사항이 없는 구성 가능한 코드 무결성(CI) 정책입니다.

### <a name="device-guard-demo-video"></a>[Device Guard 데모 비디오](https://www.youtube.com/watch?v=F-pTkesjkhI)
Device Guard는 WDAC와 하이퍼바이저 보호 코드 무결성(HVCI)의 결합입니다. 이 7분짜리 비디오는 Device Guard를 소개하고 이를 Windows Server에서 사용하는 방법을 보여줍니다.

### <a name="transport-layer-security-registry-settings"></a>[전송 계층 보안 레지스트리 설정](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings)
전송 계층 보안(TLS) 프로토콜 및 SSL(Secure Sockets Layer) 프로토콜의 Windows 구현에 대해 지원되는 레지스트리 설정 정보입니다.

### <a name="control-flow-guard"></a>[제어 흐름 보호](https://docs.microsoft.com/windows/desktop/SecBP/control-flow-guard)
제어 흐름 보호는 특정 등급의 메모리 손상 공격에 대해 기본 보호 기능을 제공합니다.

### <a name="windows-defender"></a>[Windows Defender](https://technet.microsoft.com/windows-server-docs/security/windows-defender/windows-defender-overview-windows-server)
Windows Defender는 알려진 맬웨어를 차단하는 활성 감지 기능을 제공합니다. Windows Defender는 기본적으로 켜져 있으며 Windows Server의 다양한 서버 역할을 지원하도록 최적화됩니다.

## <a name="detecting-and-responding-to-threats"></a>위협 감지 및 대응
### <a name="security-threat-analysis-using-microsoft-operations-management-suite"></a>[Microsoft Operations Management Suite를 사용한 보안 위협 분석](https://channel9.msdn.com/events/ignite/2015/brk3464)
이 Ignite 프레젠테이션에서는 Operational Insights를 사용하여 보안 위협 분석을 수행하는 방법을 설명합니다.

### <a name="microsoft-operations-management-suite-oms"></a>[Microsoft Operations Management Suite(OMS)](https://www.microsoft.com/server-cloud/operations-management-suite/overview.aspx)
Microsoft Operations Management Suite(OMS) 보안 및 감사 솔루션은 온-프레미스 및 클라우드 환경의 보안 로그 및 방화벽 이벤트를 처리하여 악의적인 동작을 분석하고 감지합니다.

### <a name="oms-and-windows-server"></a>[OMS 및 Windows Server](https://www.youtube.com/watch?v=_SaDw1dRy2k)
이 3분짜리 비디오는 OMS를 통해 Windows Server에서 차단되는 잠재적인 악성 동작을 어떻게 감지할 수 있는지 보여줍니다.  

### <a name="microsoft-advanced-threat-analytics"></a>[Microsoft Advanced Threat Analytics](https://blogs.technet.com/b/ad/archive/2015/07/22/microsoft-advanced-threat-analytics-coming-next-month.aspx)
이 블로그 게시물에서는 Active Directory 네트워크 트래픽 및 SIEM 데이터를 사용하여 잠재적 위협을 검색하고 경고하는 온-프레미스 제품인 Microsoft Advanced Threat Analytics를 소개합니다.

### <a name="microsoft-advanced-threat-analytics"></a>[Microsoft Advanced Threat Analytics](https://www.youtube.com/watch?v=0nA9FeTRZFw&list=PL8nfc9haGeb5IZGM8HvmRozetHRpBDKSw)
이 3분짜리 비디오에서는 Microsoft가 Windows Server에 어떻게 위협 분석 기능을 추가하는지에 대한 개요를 제공합니다.                                                                                 |

## <a name="network-security"></a>네트워크 보안

### <a name="datacenter-firewall-overview"></a>[데이터 센터 방화벽 개요](https://technet.microsoft.com/library/dn920240.aspx)
이 개요에서는 데이터 센터 방화벽, 네트워크 계층, 5가지 튜플(프로토콜, 원본 및 대상 포트 번호, 원본 및 대상 IP 주소), 상태 저장, 다중 테넌트 방화벽 등을 설명합니다.

### <a name="whats-new-in-dns-in-windows-server"></a>[Windows Server에서 제공되는 DNS의 새로운 기능](https://technet.microsoft.com/windows-server-docs/networking/dns/what-s-new-in-dns-server)
이 개요 항목에서는 DNS의 새로운 기능에 대한 간략한 설명과 함께 자세한 정보를 확인할 수 있는 링크를 제공합니다.                                                                           

## <a name="mapping-security-features-to-compliance-regulations"></a>규정 준수에 보안 기능 매핑

규정 준수는 보안 기능의 중요한 측면입니다. 규정 준수를 달성하는 방법과 신뢰할 수 있는 규정 준수 고문에게 규정 준수가 어떻게 보이는지에 대한 전문가 조언을 제공하고 Windows Server를 평가할 때 사용할 수 있는 초기 매핑을 제공합니다.

-   [Hyper-V 보호된 VM 규정 준수 매핑 백서](https://download.microsoft.com/download/6/D/0/6D06E149-B4C1-4EED-ACD5-DF6066E93CC0/Coalfire_Branded_Hyper_V_Shielded_VMs_Whitepaper_EN_US.pdf)

-   [JEA 및 JIT 규정 준수 매핑 백서](https://download.microsoft.com/download/2/7/A/27A2B5BB-6B52-4482-87C1-DA9D6B6D8C8D/Coalfire_Branded_Privileged_Identity_Manager_Whitepaper_EN_US.pdf)

-   [Device Guard 규정 준수 매핑 백서](https://download.microsoft.com/download/6/9/D/69D9E610-D23C-4F7E-A8CC-D65B87CEB4F8/Coalfire_Branded_Device_Guard_Whitepaper_EN_US.pdf)

-   [Credential Guard 규정 준수 매핑 백서](https://download.microsoft.com/download/8/1/2/812009C9-E4B8-4D4B-AADD-FDC373D0A076/Coalfire_Branded_Credential_Guard_Whitepaper_EN_US.pdf)

-   [Windows Defender 규정 준수 매핑 백서](https://download.microsoft.com/download/C/7/7/C778B7BB-0783-42D7-93A9-B86DFB5A7BAD/Coalfire_Branded_Windows_Defender_Whitepaper_EN_US.pdf)
