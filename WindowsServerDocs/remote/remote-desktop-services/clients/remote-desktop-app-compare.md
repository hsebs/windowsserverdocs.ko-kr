---
title: -원격 데스크톱 클라이언트 앱 비교
description: 지원 되는 특징과 기능에 있어 다른 RD 앱 비교 하는 방법에 대해 알아봅니다.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12efe858-6b76-4e08-9f72-b9603aceb0fc
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/22/2018
ms.localizationpriority: medium
ms.openlocfilehash: 8a80c0330731e0874528c45c518401bc02803450
ms.sourcegitcommit: 22ed786067cf630e956aa60301a95bc7961b7660
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2019
ms.locfileid: "9171228"
---
# 클라이언트 앱 비교

>적용 대상: Windows 10, Windows 8.1, Windows Server 2012 R2, Windows Server 2016

서로 다른 원격 데스크톱 클라이언트 앱이 어떻게 비교 종종 하 라는 메시지가 표시 합니다. 동일한 것은 모두 무엇 인가요? 다음은 이러한 질문에 대답 합니다.

## 리디렉션 지원

다음 표에서 장치 및 기타 리디렉션 원격 데스크톱 연결 앱, 유니버설 앱, 앱 Android, iOS 앱, macOS 앱 및 웹 클라이언트에 대 한 지원을 비교합니다. 이 표는 원격 세션에서 한 번에 액세스할 수 있는 리디렉션 다룹니다. 

경우 하면 개인 데스크톱에 원격를 가지는 세션에 대 한 **추가 설정** 에서 구성할 수 있는 추가 리디렉션 합니다. 원격 데스크톱 또는 앱에는 조직에서 관리 하는 경우 귀하의 관리자를 사용 하도록 설정 하거나 그룹 정책 설정을 통해 리디렉션 사용 안 함 수 있습니다.

### 입력된 리디렉션

| 리디렉션 | 원격 데스크톱<br> 연결 | 범용 | Android | iOS | macOS | 웹 클라이언트 |
|-------------|-------------------------------|-----------|---------|-----|-------|------------|
| 키보드    | X                             | X         | X       | X   | X     | X          |
| 마우스       | X                             | X         | X       | X *    | X     | X          |
| 터치       | X                             | X         | X       | X   |       |            |
| 기타       | 펜                           |           |         |     |       |            |
* [IOS 베타 원격 데스크톱 클라이언트에 대 한 지원 되는 입력된 장치 목록](remote-desktop-ios.md#supported-input-devices)을 봅니다.

### 포트 리디렉션   

| 리디렉션 | 원격 데스크톱 <br>연결 | 범용 | Android | iOS | macOS | 웹 클라이언트 |
|-------------|-------------------------------|-----------|---------|-----|-------|------------|
| 직렬 포트 | X                             |           |         |     |       |            |
| USB         | X                             |           |         |     |       |            |

USB 포트 리디렉션 사용 하도록 설정 하면 USB 포트에 연결 된 USB 장치는 자동으로 원격 세션에서 인식 됩니다.

### 다른 리디렉션 (장치 등)



| 리디렉션         | 원격 데스크톱 연결 | 범용   | Android | iOS         | macOS                                    | 웹 클라이언트    |
|---------------------|---------------------------|-------------|---------|-------------|------------------------------------------|---------------|
| 카메라             | X                         |             |         |             |                                          |               |
| 클립보드           | X                         | 텍스트, 이미지 | 텍스트    | 텍스트, 이미지 | X                                        | 텍스트          |
| 로컬 드라이브/저장소 | X                         |             | X       |             | x                                        |               |
| 위치            | X                         |             |         |             |                                          |               |
| 마이크         | X                         |X            |         |             | X                                        |               |
| Printers            | X                         |             |         |             | X (컵에만 해당)                            | PDF 인쇄     |
| 스캐너            | X                         |             |         |             |                                          |               |
| 스마트 카드         | X                         |             |         |             | X (Windows 인증을 지원 되지 않습니다.) |               |
| Speakers            | X                         | X           | X       | X           | X                                        | X (IE) 제외 |

* 프린터 지정에 대 한 macOS 앱 게시자 세터 프린터 드라이버를 기본적으로 지원합니다. 기본 프린터 드라이버를 리디렉션하면 지원 하지 않습니다.

### 지원 되는 RDP 설정
이 표에 Windows 및 HTML 클라이언트와 함께 사용할 수 있는 지원 되는 RDP 파일 설정 목록은 포함 합니다. 플랫폼 열에는 "x"에서 설정이 지원 되는지 나타냅니다. Windows 및 HTML5 클라이언트에 대 한 지원 되는 설정의 전체 목록이 아니며 아닌지 note 하세요. 계속이 표는 Windows 및 HTML5 클라이언트 뿐 아니라 macOS, iOS 및 Android 클라이언트에 대 한 더 지원 되는 RDP 설정을 포함 하도록 업데이트 됩니다.

| RDP 설정                        | 설명            | 값                 | 기본값          | Windows 가상 데스크톱 | Windows | HTML5   |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|:-------:|:-------:|
| 대체 전체 주소: s:value | 대체 이름 또는 원격 컴퓨터의 IP 주소를 지정합니다. | 모든 유효한 이름이 나 예: "10.10.15.15" 원격 컴퓨터의 IP 주소 | | x | x | x |
| 대체 셸: s:value        | RDP와 연결 하는 경우 프로그램이 자동으로 시작 했는지 여부를 결정 합니다. 이 설정은 프로그램 경로 파일 이름 상자 프로그램 탭에서 원격 데스크톱 연결 클라이언트에 해당합니다. 대체는 셸을 지정 하려면, 예를 들어 "" C:\ProgramFiles\Office\word.exe"" 값에 대 한 실행 파일에 유효한 경로 입력 합니다. 또한이 설정은 경로 또는 RemoteApplicationMode 활성화 된 경우 연결 시 시작 되도록 원격 응용 프로그램의 별칭을 결정 합니다. | 예: "C:\ProgramFiles\Office\word.exe" || x | x | x |
| audiocapturemode:i:value | 오디오 입력/출력 리디렉션 활성화 되어 있는지 여부를 나타냅니다. 이 설정은 원격 데스크톱 연결 클라이언트의 원격 오디오 상자에 해당 합니다. | 로컬 장치에서 오디오 캡처 (0) 사용 안 함 (1) 원격 세션에서 오디오 응용 프로그램에 로컬 장치 및 리디렉션에서 오디오 캡처를 사용 합니다. | 0 | x | x | |
| audiomode:i:value | 오디오를 재생 하는 컴퓨터 (즉, 로컬 또는 원격)를 결정 합니다. | (0) (이 컴퓨터에서 재생); 로컬 컴퓨터에서 소리 재생 (1) (원격 컴퓨터에서 재생); 원격 컴퓨터에서 소리를 재생 합니다. ((재생 안 함) 소리를 재생 하지 2) 수행 | 0 | x | x | x |
| 인증 수준: i:value | 서버 인증 수준 설정을 정의합니다. | (0) 서버 인증에 실패 하면 경고 없이 컴퓨터에 연결 (연결 및 경고 하지 않음). (1) 서버 인증에 실패 하는 경우 연결을 설정 하지 않습니다 (연결 하지 않음). (2) 서버 인증에 실패 하는 경우 경고를 표시 하 고 연결 또는 거부 (경고 표시); 연결 허용 (3) 인증 요구 지정 됩니다. | 3 | x | x ||
| 활성화 autoreconnection: i:value | 이 설정은 클라이언트 컴퓨터는 연결이 끊어지면; 원격 컴퓨터에 다시 연결을 시도 자동으로 여부 결정 예: 네트워크 연결이 중단 합니다. 이 설정은 해당 연결이 옵션에서 연결 RDC (원격 데스크톱)에서 고급 탭에 삭제 된 확인란을 선택 하는 경우에 다시 연결 합니다.| (0) 클라이언트 컴퓨터는 자동으로 다시 연결; 하려고 시도 하지 (1) 클라이언트 컴퓨터에 자동으로 다시 연결을 시도합니다| 1 | x | x | x |
| bandwidthautodetect:i:value | 자동 네트워크 유형 검색 활성화 되어 있는지 여부를 결정 합니다. | 사용 안 함 자동 네트워크 유형 검색 (0). (1) 자동 네트워크 유형 감지를 가능케 합니다. | 1 | x | x | x |
| 압축: i:value | 이 설정은 대량 압축 RDP 하 여 로컬 컴퓨터에 전송 될 때 활성화 되어 있는지 여부를 결정 합니다.|사용 안 함 RDP 대량 압축 (0)입니다. (1) RDP 대량 압축을 사용 합니다. | 1 | x | x | x |
| id: i:value 바탕 화면 크기 | 미리 정의 된 옵션 중에서 원격 세션 데스크톱의 크기를 지정합니다. Desktopheight 또는 desktopwidth 지정 된 경우이 설정이 무시 됩니다.| (0) 640 x 480; (1) 800 x 600; (2) 1024 x 768; (3) 1280 x 1024입니다. (4) 1600 x 1200 | 0 | x | x | x |
| desktopheight:i:value | 이 설정은 연결 RDC (원격 데스크톱)를 사용 하 여 연결 하는 경우 원격 컴퓨터에서 해상도 높이 (픽셀)를 결정 합니다. 이 설정은 theDisplay configurationslider RDC에서 theDisplaytab underOptions에서의 선택에 해당 합니다. | 200에서 2048 사이의 숫자 값 | 기본값은 로컬 컴퓨터의 해상도로 설정 | x | x | x |
| desktopwidth:i:value | 이 설정은 연결 RDC (원격 데스크톱)를 사용 하 여 연결 하는 경우 원격 컴퓨터에서 해상도 너비 (픽셀)를 결정 합니다. 이 설정은 theDisplay configurationslider RDC에서 theDisplaytab underOptions에서의 선택에 해당 합니다. | 4096 200에서 숫자 값 | 기본값은 로컬 컴퓨터의 해상도로 설정 | x | x | x |
| disableclipboardredirection:i:value | 이 설정은 클립보드 리디렉션 원격 컴퓨터에 연결할 때 활성화 되어 있는지 여부를 결정 합니다. | 클립보드 리디렉션 (0)이 활성화 됩니다. (1) 클립보드 리디렉션 되어 있지 않은 | x | x | x |
| disableconnectionsharing:i:value | 원격 데스크톱 클라이언트 열려 있는 모든 기존 연결을 다시 RemoteApp 또는 데스크톱을 시작할 때 새 연결을 시작 하는지 여부를 결정합니다 | 모든 기존 세션에 다시 (0) 연결 (1) 새 연결을 시작 합니다. | 0 | x | x | x |
| disableprinterredirection:i:value | 이 설정은 원격 컴퓨터에 연결할 때 프린터 리디렉션 기능이 활성화 되어 있는지 여부를 결정 합니다. | (0) 기능이 프린터 리디렉션 활성화 됩니다. (1) 쉽게 인쇄 프린터 리디렉션을 사용할 수 없습니다. | x | x | x |
| 도메인: s:value | 이 설정은 연결 RDC (원격 데스크톱)를 사용 하 여 원격 컴퓨터에 로그온 하는 사용자 계정 위치한 도메인의 이름을 지정 합니다. 사용자 이름 설정의 값과 함께이 설정의 값은 theGeneraltab underOptionsin RDC theUser nametext 상자에 표시 됩니다. | 예: "CONTOSO"는 유효한 도메인 이름 | 기본 값 없음 | x | x | x |
| drivestoredirect:s:value | 리디렉션된 및 원격 세션에서 사용할 수 있는 클라이언트 컴퓨터에 있는 로컬 디스크 드라이브 수를 결정 합니다. | -지정 된 값 없음 드라이브에 앞서; 리디렉션 안 함 *-; 나중에 연결 된 드라이브를 포함 하 여 모든 디스크 드라이브 리디렉션 DynamicDrives-리디렉션; 나중에 연결 된 모든 드라이브 드라이브 및 하나 이상의 드라이브-에 대 한 레이블 지정 된 드라이브를 이동 합니다.| -지정 된 값 없음 드라이브에 앞서 리디렉션 안 함 | x | x    | |
| enablecredsspsupport:i:value | 이 설정은 결정 RDP 자격 증명 보안 지원 공급자 (CredSSP)을 사용할지 여부 인증에 사용 가능한 경우 합니다. | (0) RDP 운영 체제가 CredSSP;를 지원 하는 경우에, CredSSP를 사용 하지 않습니다. (1) RDP CredSSP 운영 체제 CredSSP 지원 사용 | 1 | x | x | |
| 전체 주소: s:value | 이 설정은 이름 또는에 연결 하려고 하는 원격 컴퓨터의 IP 주소를 지정 합니다. | 올바른 컴퓨터 이름, IPv4 주소 또는 IPv6 주소-연결 하려는 원격 컴퓨터를 지정 합니다. | | x | x | x |
| gatewaycredentialssource:i:value | 지정 하거나 RD 게이트웨이 인증 방법 가져옵니다. | 암호 (NTLM); 묻기 (0) (스마트 카드 1) 사용 합니다. (4) 사용자가 나중에 선택 하도록 허용 | 0 | x | x | x |
| gatewayhostname:s:value | RD 게이트웨이 호스트 이름을 지정합니다. | 올바른 게이트웨이 서버 주소입니다. ||x|x|x|
| gatewayprofileusagemethod:i:value | 기본 RD 게이트웨이 설정을 사용할 것인지 지정 | (0); 관리자에 의해 지정 된 대로 기본 프로필 모드를 사용 하 여 (1) 사용자가 지정한 명시적 설정을 사용 합니다. | 0 | x | x | x |
| gatewayusagemethod:i:value | RD 게이트웨이 서버를 사용 하는 시기를 지정 합니다. | (0) RD 게이트웨이 서버; 사용 하지 않음 (1) 항상 사용 하 여 RD 게이트웨이 서버입니다. (2); RD 세션 호스트에 직접 연결을 수행할 수 없는 경우 RD 게이트웨이 서버 사용 (3) 사용 하 여 기본 RD 게이트웨이 서버 설정 합니다. (RD 게이트웨이 사용으로 서버를 로컬 주소; 사용 안 함 4) 수행 이 속성 값을 설정 하려면 0 또는 4는 효과적으로 해당 하는 이지만 로컬 주소를 무시 하는 옵션을 사용이 속성을 4로 설정 합니다. | | x | x | x |
| networkautodetect:i:value | 자동 네트워크 대역폭 탐지 사용할 것인지 결정 합니다. optionbandwidthautodetectto 설정 차지 하며 withconnection 유형 7를 연결 합니다. | (0) 자동 네트워크 대역폭 감지; 사용 하지 않는 (1) 자동 네트워크 대역폭 검색을 사용 합니다. | 1 | x ||x|
| promptcredentialonce:i:value | 사용자의 자격 증명 저장 되 고 RD 게이트웨이 원격 컴퓨터 모두에 사용 여부를 결정 합니다.|원격 세션 (0); 동일한 자격 증명을 사용 하지 않습니다. (1) 원격 세션 동일한 자격 증명을 사용|1|x|x||
| redirectclipboard:i:value | 이 설정은 리디렉션된 및 원격 세션에서 사용할 수 있는 로컬 컴퓨터에서 클립보드 수 있는지 여부를 결정 합니다. 이 설정은 로컬 Resourcestab underOptionsin RDC theClipboardcheck 상자에 해당 합니다. | (0) 클립보드 로컬 컴퓨터에서 원격 세션에서 사용할 수 없는 (1) 클립보드 로컬 컴퓨터에는 원격 세션에서 사용할 수 있습니다.|1|x|x|x|
| redirectdrives:i:value | 이 설정은 리디렉션된 및 원격 세션에서 사용할 수 있는 클라이언트 컴퓨터에서 드라이브 수 있는지 여부를 결정 합니다. 이 설정을 선택 forDrivesunderMoreon 로컬 Resourcestab underOptionsin RDC에 해당합니다.|(0) 로컬 컴퓨터에서 드라이브는 원격 세션에서 사용할 수 없습니다 (로컬 컴퓨터에서 드라이브 1) 원격 세션에서 사용할 수 있습니다.|0|x|x| |
| redirectprinters:i:value | 이 설정은 리디렉션된 되며 연결 RDC (원격 데스크톱)를 사용 하 여 원격 컴퓨터에 연결할 때 원격 세션에서 사용할 수 있는 클라이언트 컴퓨터에 구성 된 프린터 수 있는지 여부를 결정 합니다. 이 설정은 해당 로컬 Resourcestab underOptionsin RDC thePrinterscheck 상자에서 선택 합니다. | (0)은 로컬 컴퓨터에 프린터를 원격 세션에서 사용할 수 없습니다. (1) 프린터 로컬 컴퓨터에서 원격 세션에서 사용할 수 있습니다.|1|x|x|x|
| redirectsmartcards:i:value | 이 설정은 리디렉션된 및 연결 RDC (원격 데스크톱)를 사용 하 여 원격 컴퓨터에 연결할 때 원격 세션에서 사용할 수 있는 클라이언트 컴퓨터에 스마트 카드 장치 수 있는지 여부를 결정 합니다. 이 설정은 선택 영역에 해당 theSmart cardscheck 상자에서 로컬 Resourcestab underOptionsin RDC underMore 합니다.|(0)는 로컬 컴퓨터에 스마트 카드 장치의 원격 세션에서 사용할 수 없는 (1) 로컬 컴퓨터에 스마트 카드 장치는 원격 세션에서 사용할 수 있습니다.|1|x|x||
| remoteapplicationcmdline:s:value | RemoteApp에 대 한 선택적 명령줄 매개 변수입니다.||x|x|x|
| remoteapplicationexpandcmdline:i:value| 로컬 또는 원격으로 RemoteApp 명령줄 매개 변수에 포함 된 환경 변수 확장할 수 있는지 여부를 결정 합니다.|로컬 컴퓨터의 값 (0) 환경 변수를 확장 해야 (원격 컴퓨터의 값에 원격 컴퓨터에서 1) 환경 변수를 확장 해야||x|x|x|
| remoteapplicationexpandworkingdir | 로컬 또는 원격으로 RemoteApp 작업 디렉터리 매개 변수에 포함 된 환경 변수 확장할 수 있는지 여부를 결정 합니다. | 로컬 컴퓨터의 값 (0) 환경 변수를 확장 해야 (1) 환경 변수는 원격 컴퓨터의 값에 원격 컴퓨터에서 확장 해야 합니다. 참고: RemoteApp 작업 디렉터리 셸 작업 디렉터리 매개 변수를 통해 지정 됩니다.||x|x|x|
|remoteapplicationfile:s:value | 파일을 RemoteApp 하 여 원격 컴퓨터에서 열 수를 지정 합니다. 참고: 로컬 파일을 열 수에 대 한 사용 해야 소스 드라이브에 대 한 드라이브 리디렉션 합니다.||x|x|x|
|remoteapplicationicon:s:value | RemoteApp를 시작 하는 동안 클라이언트 UI에에서 표시 될 아이콘 파일을 지정 합니다. 파일 이름이 없는 지정 하는 경우 클라이언트는 표준 원격 데스크톱 아이콘을 사용 합니다. ".Ico" 파일만 지원 됩니다.||x|x|x|
|remoteapplicationmode:i:value | RemoteApp 연결 RemoteApp 세션 시작 되 고 있는지 여부를 결정 합니다.| (0) RemoteApp 세션; 실행 하지 (1) RemoteApp 세션을 시작 합니다.|1|x|x|x|
|remoteapplicationname:s:value | RemoteApp를 시작 하는 동안 클라이언트 인터페이스에서 RemoteApp의 이름을 지정 합니다.| 예: "Excel 2016"|x|x|x|
|remoteapplicationprogram:s:value | RemoteApp의 별칭 또는 실행 파일 이름을 지정합니다. | 예: "EXCEL" |x|x|x|
|화면 모드 id: i:value | 이 설정은 연결 RDC (원격 데스크톱)를 사용 하 여 원격 컴퓨터에 연결 하는 경우 원격 세션 창 전체 화면을 표시할지 여부를 결정 합니다. 이 설정은 theDisplay configurationslider theDisplaytab underOptionsin RDC에서의 선택에 해당 합니다.|(원격 세션 1)는 창에 표시 됩니다. (2) 원격 세션 전체 화면에 표시 됩니다.|2|x|x|x|
|스마트 크기 조정: i:value | 이 설정은 클라이언트 컴퓨터 클라이언트 컴퓨터의 창 크기에 맞게 원격 컴퓨터에서 콘텐츠를 확장할 수 있는지 여부를 결정 합니다.|(0)의 크기를 조정할 때 클라이언트 창 표시를 확장할 수는 (1) 클라이언트 창 디스플레이 크기를 조정할 때 크기가 조정 됩니다.|0|x|x||
| multimon:i:value 사용 | 이 설정은 연결 RDC (원격 데스크톱)를 사용 하 여 원격 컴퓨터에 연결 하는 경우 다중 모니터 지원을 구성 합니다.|(0) 다중 모니터 지원; 사용 안 함 (1) 다중 모니터 지원을 사용 하도록 설정|0|x|x||
| username:s:value | 이 설정은 연결 RDC (원격 데스크톱)를 사용 하 여 원격 컴퓨터에 로그온 하는 사용자 계정의 이름을 지정 합니다. 도메인 설정의 값과 함께이 설정의 값에 theGeneraltab underOptionsin RDC theUser 이름 상자에 표시 됩니다.| 유효한 사용자 이름입니다. ||x|x|x|
| videoplaybackmode:i:value| 이 설정은 RDP 효율적인 멀티미디어 스트리밍 비디오 재생에 대 한 연결 RDC (원격 데스크톱)을 사용할지 결정 합니다.|(0) RDP 효율적인 멀티미디어 스트리밍; 비디오 재생에 대해 사용 하지 않는 (1) RDP 효율적인 멀티미디어 스트리밍을 사용 가능한 경우 비디오 재생|1|x|x||
| workspaceid:s:value | 이 설정을 포함 하는 RDP 파일와 관련 된 데스크톱 ID와이 설정은 RemoteApp 정의 합니다. | 유효한 RemoteApp 및 데스크톱 연결 ID|x|x||