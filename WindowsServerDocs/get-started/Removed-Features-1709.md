---
title: Windows Server부터 제거되었거나 교체 예정인 기능(버전 1709)
description: 릴리스에서 제거되었거나 제거될 예정인 기능
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
ms.date: 08/22/2019
author: jasongerend
ms.author: jgerend
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: a74f3c6ec629df7d1cc40199091e84989606a50e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80826686"
---
# <a name="features-removed-or-planned-for-replacement-starting-with-windows-server-version-1709"></a>Windows Server, 버전 1709부터 제거되었거나 교체 예정인 기능

>적용 대상: Windows Server, 버전 1709

다음은 이 릴리스에서 제거되었거나 다음 릴리스에서 교체될 가능성이 고려되기 시작한 Windows Server, 버전 1709 기능의 목록입니다. 상용 환경에서 운영 체제를 업데이트하는 IT 전문가가 참조하시면 유용합니다. **후속 릴리스의 변경 사항에 따라 달라질 수 있으며 일부 영향을 받는 기능이 생략되었을 수 있습니다.** 

> [!TIP]
> - [Windows 참가자 프로그램](https://insider.windows.com)에 가입하여 Windows Server 빌드에 대한 초기 액세스를 얻을 수 있습니다. 이는 변경된 기능을 테스트하는 좋은 방법입니다.
> - 다른 릴리스에 대한 질문이 있습니까? [Windows Server에서 제거되었거나 교체 예정인 기능](../get-started-19/removed-features.md)을 확인하세요.

## <a name="features-removed-from-windows-server-version-1709"></a>Windows Server, 버전 1709에서 제거된 기능

Windows Server, 버전 1709에는 Windows Server 2016에 있는 동일한 기능이 포함되어 있습니다. 하지만 이 릴리스는 Windows Server 2016과는 다른 설치 옵션을 제공합니다.

- 반기 채널 릴리스로서 Windows Server, 버전 1709는 Server Core 설치 옵션만을 제공합니다. 자세한 내용은 [서비스 채널 비교](../get-started-19/servicing-channels-19.md)를 참조하세요.
- 이 릴리스부터 Nano 서버를 설치 가능한 호스트 운영 체제로 사용할 수 없습니다. 대신 Nano 서버는 컨테이너 운영 체제로 이용 가능합니다. [Windows Server, 버전 1709의 Nano 서버 변경 사항](nano-in-semi-annual-channel.md)을 참조하세요.
- 이 릴리스부터 SMB(서버 메시지 블록) 버전 1이 더 이상 기본적으로 설치되지 않습니다. 자세한 내용은 [SMBv1은 Windows 10 Fall Creators Update 및 Windows Server, 버전 1709 이상 버전에서 기본적으로 설치되지 않습니다](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows)를 참조하세요.


## <a name="features-being-considered-for-replacement-starting-with-subsequent-releases"></a>다음 릴리스부터 교체를 고려 중인 기능

다음 기능은 Windows Server, 버전 1709 이후 릴리스부터 교체를 고려 중인 기능입니다. 결국에는 설치된 제품 이미지로부터 완전히 제거되고 다른 기능으로 교체(또는 다른 원본으로부터 설치 가능)되겠지만 이 릴리스에서는 여전히 사용 가능합니다. 단, 특정 기능이 제거된 경우도 있습니다. 이러한 기능에 종속된 애플리케이션, 코드, 사용법을 계속 사용하기 위한 다른 방법 또는 향후 교체를 생각해야 합니다.

이러한 기능의 제안된 교체에 관해 공유할 피드백이 있는 경우 [피드백 허브 앱](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)을 사용할 수 있습니다. 이 앱은 Windows 10에서 실행되지만 이를 사용하여 Windows Server 제품(및 설명서)에 관한 피드백을 보낼 수 있습니다.

### <a name="iis-6-management-compatibility"></a>IIS 6 관리 호환성
교체를 고려 중인 특정 기능은 다음과 같습니다.

- IIS 6 메타베이스 호환성(Web-Metabase)
- IIS 6 관리 콘솔(Web-Lgcy-Mgmt-Console)
- IIS 6 스크립팅 도구(Web-Lgcy-Scripting)
- IIS 6 WMI 호환성(Web-WMI)

IIS 6 기반 메타베이스 스크립트 및 IIS 7 이상에서 사용되는 파일 기반 구성 사이의 에뮬레이션 계층 역할을 하는 IIS 6 메타베이스 호환성 대신 Microsoft.Web.Administration 네임스페이스와 같은 도구를 사용하여 관리 스크립트를 대상 IIS 파일 기반 구성에 직접 마이그레이션을 시작해야 합니다.

또한 IIS 6.0 이하 버전으로부터 마이그레이션을 시작하고, 가장 최신 Windows Server 릴리스에서 항상 사용 가능한 최신 IIS 버전으로 이동해야 합니다.


### <a name="iis-digest-authentication"></a>IIS 다이제스트 인증
이 인증 방법은 교체 계획 중입니다. 대신 클라이언트 인증서 매핑([일대일 클라이언트 인증서 매핑 구성](https://docs.microsoft.com/iis/manage/configuring-security/configuring-one-to-one-client-certificate-mappings) 참조) 또는 Windows 인증([애플리케이션 설정](https://docs.microsoft.com/iis-administration/configuration/appsettings.json) 참조)과 같은 다른 인증 방법을 사용하기 시작해야 합니다.

### <a name="internet-storage-name-service-isns"></a>iSNS(Internet Storage Name Service)
iSNS는 교체 고려 중입니다. SMB(서버 메시지 블록) 기능은 기본적으로 추가 기능과 함께 동일한 기능을 제공합니다. 이 기능에 관한 배경 정보는 [서버 메시지 블록 개요](https://technet.microsoft.com/library/hh831795(v=ws.11).aspx)를 참조하세요.

### <a name="rsaaes-encryption-for-iis"></a>IIS용 RSA/AES 암호화 
상위 암호화 API: CNG(Next Generation)가 이미 사용 가능하기 때문에 이 암호화 방법은 교체 고려 중입니다. CNG 암호화에 대해 자세히 알아보려면 [CNG 정보](https://msdn.microsoft.com/library/windows/desktop/aa375276(v=vs.85).aspx)를 참조하세요.

### <a name="windows-powershell-20"></a>Windows PowerShell 2.0
이 Windows PowerShell 초기 버전은 최근의 여러 버전으로 대체되었습니다. 최적의 기능 및 성능을 위해 Windows PowerShell 5.0 이상으로 마이그레이션하세요. 자세한 내용은 [PowerShell 설명서](https://docs.microsoft.com/powershell/index?view=powershell-5.1)를 참조하세요.

