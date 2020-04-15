---
title: 지원되는 원격 데스크톱 RDP 파일 설정
description: 원격 데스크톱의 RDP 파일 설정에 대해 알아보기
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 05/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: 6af7559f1d74f2af38579ee357507bd1207f63b2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855916"
---
# <a name="supported-remote-desktop-rdp-file-settings"></a>지원되는 원격 데스크톱 RDP 파일 설정

다음 표에는 Windows 및 HTML 클라이언트에서 사용할 수 있는 지원되는 RDP 파일 설정 목록이 나와 있습니다. 플랫폼 열의 "x"는 설정이 지원된다는 것을 나타냅니다. 하지만 이 목록은 Windows 및 HTML5 클라이언트에 지원되는 설정의 전체 목록은 아닙니다. 이 표는 Windows 및 HTML5 클라이언트는 물론 macOS, iOS 및 Android 클라이언트에 지원되는 RDP 설정을 더 많이 포함하도록 계속 업데이트될 예정입니다.

PowerShell을 사용하여 호스트 풀의 RDP 속성을 사용자 지정하는 방법에 대한 자세한 내용은 [이 설명서](https://go.microsoft.com/fwlink/?linkid=2098243&clcid=0x409)를 참조하세요.

| RDP 설정                        | 설명            | 값                 | 기본값          | Windows 가상 데스크톱 | Windows | HTML5   |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|:-------:|:-------:|
| alternate full address:s:value | 원격 컴퓨터의 IP 주소나 대체 이름을 지정합니다. | 원격 컴퓨터의 유효한 이름 또는 IP 주소(예: "10.10.15.15") | | x | x | x |
| alternate shell:s:value        | RDP로 연결할 때 프로그램이 자동으로 시작되는지 여부를 결정합니다. 대체 셸을 지정하려면, 값의 실행 파일에 대한 유효한 경로(예: "C:\ProgramFiles\Office\word.exe")를 입력합니다. 이 설정은 RemoteApplicationMode가 사용되는 경우, 연결 시 시작될 원격 애플리케이션의 경로나 별칭도 결정합니다. | "C:\ProgramFiles\Office\word.exe" || x | x | x |
| audiocapturemode:i:value | 오디오 입출력 리디렉션이 사용되는지 여부를 나타냅니다. | - 0: 로컬 디바이스에서 오디오 캡처를 사용하지 않도록 설정<br>- 1: 로컬 디바이스에서 오디오 캡처를 사용하도록 설정하고 원격 세션에서 오디오 애플리케이션으로 리디렉션 | 0 | x | x | |
| audiomode:i:value | 로컬 또는 원격 머신에서 오디오 재생 여부를 결정합니다. | - 0: 로컬 컴퓨터에서 소리 재생(이 컴퓨터에서 재생)<br>- 1: 원격 컴퓨터에서 소리 재생(원격 컴퓨터에서 재생)<br>- 2: 소리 재생 안 함(재생 안 함) | 0 | x | x | x |
| authentication level:i:value | 서버 인증 수준 설정을 정의합니다. | - 0: 서버 인증에 실패하면 경고 없이 컴퓨터에 연결(연결하고 경고를 표시 안 함)<br>- 1: 서버 인증에 실패하면 연결을 설정하지 않음(연결 안 함)<br>- 2: 서버 인증에 실패하면 경고를 표시하고 연결하거나 연결을 거부하도록 허용(메시지 표시)<br>- 3: 인증 요구 사항이 지정되지 않음 | 3 | x | x ||
| autoreconnection enabled:i:value | 연결이 끊어지면(예: 네트워크 연결이 끊어지는 경우) 클라이언트 컴퓨터가 원격 컴퓨터에 자동으로 다시 연결을 시도할지 여부를 결정합니다. | - 0: 클라이언트 컴퓨터가 자동으로 다시 연결을 시도하지 않음<br>- 1: 클라이언트 컴퓨터가 자동으로 다시 연결을 시도| 1 | x | x | x |
| bandwidthautodetect:i:value | 자동 네트워크 유형 검색을 사용할지 여부를 결정합니다. | - 0: 자동 네트워크 유형 검색을 사용하지 않도록 설정<br>- 1: 자동 네트워크 유형 검색을 사용하도록 설정 | 1 | x | x | x |
| camerastoredirect:s:value | 리디렉션할 카메라를 구성합니다. 이 설정은 리디렉션에 사용하도록 설정된 카메라의 KSCATEGORY_VIDEO_CAMERA 인터페이스 목록을 사용합니다. | - * : 모든 카메라를 리디렉션합니다.<br> - camerastoredirect:s:\\?\usb#vid_0bda&pid_58b0&mi처럼 기호 링크 문자열 앞에 "-"를 추가하여 특정 카메라를 제외할 수 있습니다. | | x | x | |
| compression:i:value | RDP에서 로컬 컴퓨터로 전송할 때 대량 압축을 사용할지 여부를 결정합니다.|- 0: RDP 대량 압축을 사용하지 않도록 설정<br>- 1: RDP 대량 압축을 사용하도록 설정 | 1 | x | x | x |
| desktop size id:i:value | 미리 정의된 옵션 세트 중에서 원격 세션 데스크톱의 크기를 지정합니다. 이 설정은 desktopheight 또는 desktopwidth가 지정된 경우 무시됩니다.| -0: 640×480<br>- 1: 800×600<br>- 2: 1024×768<br>- 3: 1280×1024<br>- 4: 1600×1200 | 0 | x | x | x |
| desktopheight:i:value | 원격 데스크톱 연결을 사용하여 연결할 때 원격 컴퓨터의 해상도 높이(픽셀 단위)를 결정합니다. 이 설정은 RDC의 옵션 아래 디스플레이 탭에 있는 디스플레이 구성 슬라이더의 선택 항목에 해당합니다. | 200에서 2048 사이의 숫자 값 | 기본값은 로컬 컴퓨터의 해상도로 설정됨 | x | x | x |
| desktopwidth:i:value | 원격 데스크톱 연결을 사용하여 연결할 때 원격 컴퓨터의 해상도 너비(픽셀 단위)를 결정합니다. 이 설정은 RDC의 옵션 아래 디스플레이 탭에 있는 디스플레이 구성 슬라이더의 선택 항목에 해당합니다. | 200과 4096 사이의 숫자 값 | 기본값은 로컬 컴퓨터의 해상도로 설정됨 | x | x | x |
| devicestoredirect:s:value | 클라이언트 컴퓨터에서 어떤 디바이스를 리디렉션하고 원격 세션에서 사용할 수 있을지를 결정합니다. | - *: 지원되는 모든 디바이스를 리디렉션(나중에 연결되는 디바이스 포함)<br> - 하나 이상의 디바이스에 유효한 하드웨어 ID | | x | x | x |
| disableconnectionsharing:i:value | RemoteApp 또는 데스크톱이 시작될 때 원격 데스크톱 클라이언트가 열려 있는 기존 연결에 다시 연결할지 아니면 새 연결을 시작할지 결정합니다. | - 0: 기존 세션에 다시 연결<br>- 1: 새 연결 시작 | 0 | x | x | x |
| domain:s:value | 원격 컴퓨터에 로그인할 때 사용할 사용자 계정이 있는 도메인의 이름을 지정합니다. | 유효한 도메인 이름(예: "CONTOSO") | 기본값 없음 | x | x | x |
| drivestoredirect:s:value | 클라이언트 컴퓨터의 로컬 디스크 드라이브 중 어떤 드라이브를 리디렉션하고 원격 세션에서 사용할 수 있을지를 결정합니다. | - 지정된 값 없음: 드라이브를 리디렉션하지 않음<br>- * : 모든 디스크 드라이브를 리디렉션(나중에 연결되는 드라이브 포함)<br>- DynamicDrives: 나중에 연결된 모든 드라이브 리디렉션<br>- 드라이브 및 하나 이상의 드라이브에 대한 레이블(예: "drivestoredirect:s:C:;E:;"): 지정된 드라이브 리디렉션| 지정된 값 없음 : 드라이브를 리디렉션하지 않음 | x | x    | |
| enablecredsspsupport:i:value | 사용 가능한 경우 RDP가 CredSSP(Credential Security Support Provider)를 인증에 사용할지 여부를 결정합니다. | - 0: 운영 체제가 CredSSP를 지원하더라도 RDP가 CredSSP를 사용하지 않음<br>- 1: 운영 체제가 CredSSP를 지원하는 경우 RDP가 CredSSP를 사용 | 1 | x | x | |
| 리디렉션된 비디오 인코딩 capture:i:value | 리디렉션된 비디오의 인코딩을 사용하거나 사용하지 않도록 설정합니다. | - 0: 리디렉션된 비디오를 인코딩하지 않도록 설정<br>- 1: 리디렉션된 비디오를 인코딩하도록 설정 | 1 | x | x | x |
| full address:s:value | 이 설정은 연결할 원격 컴퓨터의 이름이나 IP 주소를 지정합니다. | 유효한 컴퓨터 이름, IPv4 주소 또는 IPv6 주소입니다. | | x | x | x |
| gatewaycredentialssource:i:value | RD 게이트웨이 인증 방법을 지정하거나 검색합니다. | - 0: 암호 요청(NTLM)<br>- 1: 스마트 카드 사용<br>- 4: 사용자가 나중에 선택하도록 허용 | 0 | x | x | x |
| gatewayhostname:s:value | RD 게이트웨이 호스트 이름을 지정합니다. | 유효한 게이트웨이 서버 주소 ||x|x|x|
| gatewayprofileusagemethod:i:value | 기본 RD 게이트웨이 설정을 사용할지 여부를 지정 | - 0: 관리자가 지정한 기본 프로필 모드 사용<br>- 1: 사용자가 지정한 명시적 설정 사용 | 0 | x | x | x |
| gatewayusagemethod:i:value | RD 게이트웨이 서버를 사용하는 경우를 지정 | - 0: RD 게이트웨이 서버를 사용하지 않음<br>- 1: RD 게이트웨이 서버를 항상 사용<br>- 2: RD 세션 호스트에 직접 연결할 수 없는 경우 RD 게이트웨이 서버 사용<br>- 3: 기본 RD 게이트웨이 서버 설정 사용<br>- 4: RD 게이트웨이를 사용하지 않음, 로컬 주소에 대해 서버 무시<br>이 속성 값을 0이나 4로 설정하면 효과가 동일하지만 이 속성을 4로 설정하면 옵션이 로컬 주소를 바이패스할 수 있습니다. | | x | x | x |
| networkautodetect:i:value | 자동 네트워크 대역폭 감지를 사용할지 여부를 결정합니다. bandwidthautodetect 옵션을 설정해야 하며 연결 유형 7과 상관 관계를 지정합니다. | - 0: 자동 네트워크 대역폭 감지를 사용하지 않습니다.<br> - 1: 자동 네트워크 대역폭 감지를 사용합니다. | 1 | x ||x|
| promptcredentialonce:i:value | 사용자 자격 증명을 저장하고 RD 게이트웨이와 원격 컴퓨터 둘 다에 사용할지 여부를 결정합니다.|- 0: 원격 세션에서 동일한 자격 증명을 사용하지 않음<br>- 1: 원격 세션에서 동일한 자격 증명을 사용|1|x|x||
| redirectclipboard:i:value | 클립보드 리디렉션이 사용되는지 여부를 결정합니다. | - 0: 로컬 컴퓨터의 클립보드를 원격 세션에서 사용할 수 없음<br>- 1: 로컬 컴퓨터의 클립보드를 원격 세션에서 사용할 수 있음|1|x|x|x|
| 리디렉션된 비디오 캡처 인코딩 quality:i:value | 인코딩된 비디오의 품질을 제어합니다. | - 0: 고압축 비디오. 동작이 많으면 품질이 떨어질 수 있습니다. <br>- 1: 중간 압축<br>- 2: 그림 품질이 높은 저압축 비디오 | 0 | x | x | x |
| redirectprinters:i:value | 원격 데스크톱 연결을 사용하여 원격 컴퓨터에 연결할 때 클라이언트 컴퓨터에 구성된 프린터가 리디렉션되고 원격 세션에서 사용할 수 있는지 여부를 결정합니다. | - 0: 로컬 컴퓨터의 프린터를 원격 세션에서 사용할 수 없음<br>- 1: 로컬 컴퓨터의 프린터를 원격 세션에서 사용할 수 있음|1|x|x|x|
| redirectsmartcards:i:value | 원격 컴퓨터에 연결할 때 클라이언트 컴퓨터의 스마트 카드 디바이스가 리디렉션되고 원격 세션에서 사용할 수 있는지 여부를 결정합니다. |- 0: 로컬 컴퓨터의 스마트 카드 디바이스를 원격 세션에서 사용할 수 없음<br>- 1: 로컬 컴퓨터의 스마트 카드 디바이스를 원격 세션에서 사용할 수 있음|1|x|x||
| remoteapplicationcmdline:s:value | RemoteApp에 대한 선택적 명령줄 매개 변수입니다.||x|x|x|
| remoteapplicationexpandcmdline:i:value| RemoteApp 명령줄 매개 변수에 포함된 환경 변수를 로컬로 확장할지 아니면 원격으로 확장할지 결정합니다.|- 0: 환경 변수를 로컬 컴퓨터의 값으로 확장해야 함<br>- 1: 환경 변수를 원격 컴퓨터에서 원격 컴퓨터의 값으로 확장해야 함||x|x|x|
| remoteapplicationexpandworkingdir | RemoteApp 작업 디렉터리 매개 변수에 포함된 환경 변수를 로컬로 확장할지 아니면 원격으로 확장할지 결정합니다. | - 0: 환경 변수를 로컬 컴퓨터의 값으로 확장해야 함<br> - 1: 환경 변수를 원격 컴퓨터에서 원격 컴퓨터의 값으로 확장해야 함.<br>RemoteApp 작업 디렉터리는 셸 작업 디렉터리 매개 변수를 통해 지정됩니다.||x|x|x|
|remoteapplicationfile:s:value | RemoteApp이 원격 컴퓨터에서 열 파일을 지정합니다.<br>로컬 파일이 열리도록 하려면, 원본 드라이브에 대한 드라이브 리디렉션도 사용하도록 설정해야 합니다||x|x|x|
|remoteapplicationicon:s:value | RemoteApp을 시작하는 동안 클라이언트 UI에 표시할 아이콘 파일을 지정합니다. 파일 이름을 지정하지 않으면, 클라이언트는 표준 원격 데스크톱 아이콘을 사용합니다. ".ico" 파일만 지원됩니다.||x|x|x|
|remoteapplicationmode:i:value | RemoteApp 연결이 RemoteApp 세션으로 시작될지 여부를 결정합니다.| - 0: RemoteApp 세션을 시작하지 않음<br>- 1: RemoteApp 세션을 시작|1|x|x|x|
|remoteapplicationname:s:value | RemoteApp을 시작하는 동안 클라이언트 인터페이스에서 RemoteApp의 이름을 지정합니다.| 예: "Excel 2016."|x|x|x|
|remoteapplicationprogram:s:value | RemoteApp의 별칭 또는 실행 파일 이름을 지정합니다. | 예: "EXCEL." |x|x|x|
|screen mode id:i:value | 원격 데스크톱 연결을 사용하여 원격 컴퓨터에 연결할 때 원격 세션 창이 전체 화면으로 표시될지 여부를 결정합니다. |- 1: 원격 세션이 창에 나타납니다.<br>- 2: 원격 세션이 전체 화면으로 나타납니다.|2|x|x|x|
|smart sizing:i:value | 클라이언트 컴퓨터가 원격 컴퓨터의 콘텐츠를 클라이언트 컴퓨터의 창 크기에 맞게 조정할 수 있는지 여부를 결정합니다.|- 0: 크기 조정 시 클라이언트 창 디스플레이가 조정되지 않음<br>- 1: 크기 조정 시 클라이언트 창 디스플레이가 조정됨|0|x|x||
| use multimon:i:value | 원격 데스크톱 연결을 사용하여 원격 컴퓨터에 연결할 때 다중 모니터 지원을 구성합니다.|- 0: 다중 모니터 지원을 사용하지 않도록 설정<br>- 1: 다중 모니터 지원을 사용하도록 설정|0|x|x||
| username:s:value | 원격 컴퓨터에 로그인할 때 사용할 사용자 계정의 이름을 지정합니다. | 유효한 사용자 이름 ||x|x|x|
| videoplaybackmode:i:value| 원격 데스크톱 연결에서 RDP 효율적인 멀티미디어 스트리밍을 비디오 재생에 사용할지 여부를 결정합니다.|- 0: RDP 효율적인 멀티미디어 스트리밍을 비디오 재생에 사용하지 않음<br>- 1: 가능한 경우 RDP 효율적인 멀티미디어 스트리밍을 비디오 재생에 사용|1|x|x||
| workspaceid:s:value | 이 설정이 포함된 RDP 파일과 연결된 RemoteApp 및 데스크톱 ID를 정의합니다. | 유효한 RemoteApp 및 데스크톱 연결 ID|x|x||
