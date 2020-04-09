---
title: 7 단계 2-APP1 설치 및 구성
description: 이 항목은 테스트 랩 가이드-Windows Server 2016에 대 한 DirectAccess 멀티 사이트 배포 시연의 일부입니다.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 1cc0abc6-be4d-4cbe-bd0c-cc448bf294f6
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 8b6f5438498349e7d02fd6c9122d300e55fe2517
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861556"
---
# <a name="step-7-install-and-configure-2-app1"></a>7 단계 2-APP1 설치 및 구성

>적용 대상: Windows Server(반기 채널), Windows Server 2016

2-APP1는 웹 및 파일 공유 서비스를 제공 합니다. 2-APP1 구성은 다음과 같이 구성 됩니다.  
  
- 2-APP1에 운영 체제 설치  
  
- TCP/IP 속성을 구성합니다.  
  
- 조인 2-APP1 to the CORP2 domain  
  
- 2-APP1에 웹 서버 (IIS) 역할을 설치 합니다.  
  
- 2-APP1에서 공유 폴더 만들기 
  
## <a name="install-the-operating-system-on-2-app1"></a><a name="bkmk_InstallOS"></a>2-APP1에 운영 체제 설치  
먼저 Windows Server 2016, Windows Server 2012 R2 또는 Windows Server 2012를 설치 합니다.  
  
#### <a name="to-install-the-operating-system-on-2-app1"></a>2-APP1에 운영 체제를 설치 하려면  
  
1.  Windows Server 2016, Windows Server 2012 R2 또는 Windows Server 2012 (전체 설치) 설치를 시작 합니다.  
  
2.  지침에 따라 설치를 완료하고 로컬 관리자 계정에 강력한 암호를 지정합니다. 로컬 관리자 계정을 사용하여 로그온합니다.  
  
3.  APP1를 인터넷에 액세스할 수 있는 네트워크에 연결 하 고 Windows 업데이트를 실행 하 여 Windows Server 2016, Windows Server 2012 R2 또는 Windows Server 2012의 최신 업데이트를 설치한 다음 인터넷에서 연결을 끊습니다.  
  
4.  2-APP1을 2-Corpnet 서브넷에 연결 합니다.  
  
## <a name="configure-tcpip-properties"></a><a name="bkmk_TCP"></a>TCP/IP 속성 구성  
2-APP1에서 TCP/IP 속성을 구성 합니다.  
  
#### <a name="to-configure-tcpip-properties"></a>TCP/IP 속성을 구성하려면  
  
1.  서버 관리자 콘솔에서 **로컬 서버**를 클릭 한 다음 **속성** 영역에서 **유선 이더넷 연결**옆에 있는 링크를 클릭 합니다.  
  
2.  **네트워크 연결** 창에서 **유선 이더넷 연결**을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.  
  
3.  **Internet Protocol Version 4(TCP/IPv4)** 를 클릭하고 **속성**을 클릭합니다.  
  
4.  **다음 IP 주소 사용**을 클릭합니다. **IP 주소**에 **10.2.0.3**를 입력 합니다. **서브넷 마스크**에 **255.255.255.0**을 입력합니다. **기본 게이트웨이에서** **10.2.0.254**를 입력 합니다.  
  
5.  **다음 DNS 서버 주소 사용**을 클릭합니다. **기본 설정 DNS 서버**에 **10.2.0.1**를 입력 합니다.  
  
6.  **고급**을 클릭 한 다음 **DNS** 탭을 클릭 합니다. **이 연결에 대 한 DNS 접미사**에 **corp2.corp.contoso.com**를 입력 하 고 **확인** 을 두 번 클릭 합니다.  
  
7.  **인터넷 프로토콜 버전 6(TCP/IPv6)** , **속성**을 차례로 클릭합니다.  
  
8.  **다음 IPv6 주소 사용을**클릭 합니다. **IPv6 주소**에 **2001: db8:2:: 3**을 입력 합니다. **서브넷 접두사 길이**에 **64**을 입력 합니다. **기본 게이트웨이에서** **2001: db8:2:: fe**를 입력 합니다. **다음 dns 서버 주소 사용**을 클릭 하 고 **기본 설정 dns 서버**에 **2001: db8:2:: 1**을 입력 합니다.  
  
9. **고급**을 클릭하고 **DNS** 탭을 클릭합니다.  
  
10. **이 연결에 대 한 DNS 접미사**에 **corp2.corp.contoso.com**를 입력 한 다음 **확인** 을 두 번 클릭 합니다.  
  
11. **유선 이더넷 연결 속성** 대화 상자에서 **닫기**를 클릭 합니다.  
  
12. **네트워크 연결** 창을 닫습니다.  
  
## <a name="join-2-app1-to-the-corp2-domain"></a><a name="bkmk_JoinDomain"></a>조인 2-APP1 to the CORP2 domain  
2-APP1을 corp2.corp.contoso.com 도메인에 가입 시킵니다.  
  
#### <a name="to-join-2-app1-to-the-corp2-domain"></a>APP1을 CORP2 도메인에 가입 시키려면  
  
1.  서버 관리자 콘솔의 **로컬 서버**에 있는 **속성** 영역에서 **컴퓨터 이름**옆에 있는 링크를 클릭 합니다.  
  
2.  **시스템 속성** 대화 상자의 **컴퓨터 이름** 탭에서 **변경**을 클릭합니다.  
  
3.  **컴퓨터 이름**에 **2-APP1**을 입력 합니다. **소속 그룹**에서 **도메인**을 클릭 하 고 **Corp2.corp.contoso.com**를 입력 한 다음 **확인**을 클릭 합니다.  
  
4.  사용자 이름 및 암호를 입력 하 라는 메시지가 표시 되 면 **관리자** 와 암호를 입력 한 다음 **확인**을 클릭 합니다.  
  
5.  Corp2.corp.contoso.com 도메인을 환영 하는 대화 상자가 표시 되 면 **확인**을 클릭 합니다.  
  
6.  컴퓨터를 다시 시작해야 한다는 메시지가 표시되면 **확인**을 클릭합니다.  
  
7.  **시스템 속성** 대화 상자에서 **닫기**를 클릭합니다.  
  
8.  컴퓨터를 다시 시작할지 묻는 메시지가 표시되면 **지금 다시 시작**을 클릭합니다.  
  
9. 컴퓨터가 다시 시작 되 면 **사용자 전환**을 클릭 한 다음 **기타 사용자** 를 클릭 하 고 관리자 계정을 사용 하 여 CORP2 도메인에 로그온 합니다.  
  
## <a name="install-the-web-server-iis-role-on-2-app1"></a><a name="bkmk_IIS"></a>2-APP1에 웹 서버 (IIS) 역할을 설치 합니다.  
웹 서버를 2 APP1 설정 하려면 웹 서버 (IIS) 역할을 설치 합니다.  
  
#### <a name="to-install-the-web-server-iis-role"></a>웹 서버 (IIS) 역할을 설치 하려면  
  
1.  서버 관리자 콘솔의 **대시보드에서** **역할 및 기능 추가**를 클릭 합니다.  
  
2.  클릭 **다음** 하 여 서버 역할 선택 화면을 세 번  
  
3.  **서버 역할 선택** 페이지에서 **웹 서버 (IIS)** 를 선택 하 고 **다음** 을 네 번 클릭 합니다.  
  
4.  **설치 선택 확인** 페이지에서 **설치**를 클릭합니다.  
  
5.  설치가 완료 되었는지 확인 하 고 **닫기**를 클릭 합니다.  
  
## <a name="create-a-shared-folder-on-2-app1"></a><a name="bkmk_Share"></a>2-APP1에서 공유 폴더 만들기  
APP1의 폴더 내에 공유 폴더와 텍스트 파일을 만듭니다.  
  
#### <a name="to-create-a-shared-folder"></a>공유 폴더를 만들려면  
  
1.  에 **시작** 화면에서 입력**explorer.exe**, 한 다음 ENTER를 누릅니다.  
  
2.  **컴퓨터**를 클릭 한 다음 **로컬 디스크 (C:)** 를 두 번 클릭 합니다.  
  
3.  **새 폴더**를 클릭 하 고 **파일**을 입력 한 다음 enter 키를 누릅니다. **로컬 디스크** 창을 열어 둡니다.  
  
4.  **시작** 화면에서**notepad.exe**를 입력 하 고 **메모장**을 마우스 오른쪽 단추로 클릭 한 다음 **고급**을 클릭 하 고 **관리자 권한으로 실행**을 클릭 합니다.  
  
5.  **제목 없음-메모장** 창에서 **이 파일을 2-APP1에 있는 공유 파일**로 입력 합니다.  
  
6.  **파일**, **저장**을 차례로 클릭 하 고 **컴퓨터**를 클릭 한 다음 **로컬 디스크 (C:)** 를 두 번 클릭 하 고 **파일** 폴더를 두 번 클릭 합니다.  
  
7.  **파일 이름**에 **example .txt**를 입력 한 다음 **저장**을 클릭 합니다. 메모장을 닫습니다.  
  
8.  **로컬 디스크** 창에서 **파일** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **공유**대상을 가리킨 다음 **특정 사용자**를 클릭 합니다.  
  
9. **파일 공유** 대화 상자의 드롭다운 목록에서 **Everyone**을 클릭 한 다음 **추가**를 클릭 합니다. **Everyone**의 **사용 권한 수준** 에서 **읽기/쓰기**를 클릭 합니다.  
  
10. 클릭 **공유**, 를 클릭 하 고 **수행**합니다.  
  
11. **로컬 디스크** 창을 닫습니다.  
  


