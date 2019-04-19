---
ms.assetid: d1953097-63ea-4a0e-b860-2f3b7c175c41
title: Windows 시간 서비스의 작동 방식
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: networking
ms.openlocfilehash: c9ab52229c2a16d6ae6b0b2733c52e53a25cfa44
ms.sourcegitcommit: fb4e2ace2e0a29e0f6b028f1cb945cab6aa6ee2c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2018
---
# <a name="how-the-windows-time-service-works"></a>Windows 시간 서비스의 작동 방식

>적용 대상: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

**이 섹션에서**  
  
-   [Windows 서비스 아키텍처 시간](#w2k3tr_times_how_rrfo)  
  
-   [Windows 서비스 시간 프로토콜 시간](#w2k3tr_times_how_ekoc)  
  
-   [Windows 서비스 프로세스와 상호 작용 시간](#w2k3tr_times_how_izcr)  
  
-   [Windows 시간이 서비스에서 사용 되는 네트워크 포트](#w2k3tr_times_how_ydum)  
  
> [!NOTE]  
> 이 항목에서는 Windows 시간 서비스 (W32Time)의 작동 방식만 설명 합니다. Windows 시간 서비스를 구성 하는 방법에 대 한 정보에 대 한 섹션의 항목의 목록을 보려면 [Windows 시간 서비스 구성 정보를 찾을 위치](https://technet.microsoft.com/library/cc773061.aspx)합니다.  
  
> [!NOTE]  
> Windows Server 2003 및 Windows 2000 Server, 디렉터리 서비스 Active Directory 디렉터리 서비스를 이라고 합니다. Windows Server 2008 및 이후 버전에서 디렉터리 서비스 Active Directory 도메인 서비스 (AD DS) 라고 합니다. 이 항목의 나머지 부분 AD DS을 의미 하지만 정보 Active Directory에 적용 됩니다.  
  
Windows 시간 서비스 정확한 구현 네트워크 시간 Protocol (NTP)의 하지는 않지만 네트워크를 통해 컴퓨터에 시계 최대한 정확 하 게 되도록 NTP 사양에 정의 된 알고리즘 복잡 한 제품군을 사용 합니다. 이 가장 좋습니다 AD DS 도메인에 있는 모든 컴퓨터 시계 신뢰할 수 있는 컴퓨터의 시간과 동기화 됩니다. 여러 가지 요소 시간 동기화 네트워크에 영향을 줄 수 있습니다. 자주는 다음과 같은 요인 AD ds에서 동기화 정확도 영향을:  
  
-   네트워크 상태  
  
-   컴퓨터의 하드웨어 시계 정확도  
  
-   Windows 시간 서비스를 사용할 수 있는 CPU 및 네트워크 리소스의 양  
  
> [!IMPORTANT]  
> Windows Server 2016 전에 W32Time 서비스 시간 응용 프로그램 요구를 충족 되도록 디자인 되지 않았습니다.  그러나 Windows Server 2016 업데이트 이제 수 있도록 1ms 위한 솔루션을 구현 도메인에 정확도 합니다.  See [Windows 2016 Accurate Time](accurate-time.md) and  [Support boundary to configure the Windows Time service for high-accuracy environments](https://go.microsoft.com/fwlink/?LinkID=179459) for more information.  
  
도메인에 가입 하지 않은 시간 덜 자주 동기화 하는 컴퓨터 time.windows.com와 동기화 하는 기본적으로 구성 됩니다. 따라서 시간 정확도 일시적인 하는 컴퓨터 또는 네트워크 연결을 보장할 수 없기 합니다.  
  
AD DS 숲은 미리 시간 동기화 계층입니다. Windows 시간 서비스 시간 위에 가장 정확한 참조 시계와 계층 내 컴퓨터 간에 동기화합니다. 를 컴퓨터에 둘 이상의 시간 소스 구성 된 경우 Windows 시간 NTP 알고리즘을 사용 하 여 해당 시간 원본와 동기화 하는 컴퓨터의 기능에 따라 구성 된 출처의 좋은 시간 소스를 선택 합니다. Windows 시간 서비스 네트워크 동기화 방송을 또는 멀티 캐스트 피어에서 지원 하지 않습니다. 이러한 NTP 기능에 대 한 자세한 내용은 참조 IETF RFC 데이터베이스에 RFC 1305 합니다.  
  
Windows 시간 서비스가 실행 되는 모든 컴퓨터 서비스를 사용 하는 가장 정확한 시간을 유지 합니다. 컴퓨터가 도메인에 속한 하는 클라이언트 역할을 시간 기본적으로, 따라서 대부분의 경우 필요 없는 Windows 시간 서비스 구성할 수 있습니다. 그러나 Windows 시간 서비스 참조 지정 된 시간 소스에서 시간을 요청 하 구성할 수 있습니다 및 시간 클라이언트에 게 제공할 수도 있습니다.
  
정도 컴퓨터 사용 시간이 정확 하 게 되는 계층을 라고 합니다. (예: 하드웨어 시계) 네트워크에서 가장 정확한 시간 원본 최저 계층 수준 또는 하나 계층을 차지합니다. 이 정확한 시간 소스 참조 시계를 라고 합니다. 참조 시계에서 직접 시간을 획득 하는 NTP 서버 참조 시계 하는 보다 높은 한 수준 계층을 차지 합니다. 리소스 NTP 서버에서 시간을 획득 하는 두 단계 참조 시계 떨어진 및 따라서 있는 2 계층 가장 정확한 시간 원본 보다 높은 차지 등에 됩니다. 컴퓨터의 계층 숫자로 증가 함에 따라 해당 시스템 클록의 시간을 될 수 있습니다 덜 정확 하 게 됩니다. 따라서 계층 수준의 된 컴퓨터는 가장 정확한 시간 원본과 해당 컴퓨터 동기화 되는 방법을 자세히 표시 됩니다.  
  
W32Time 관리자 시간 샘플을 받으면 사용 특별 한 알고리즘 NTP에서 시간 예제는 사용할 수 있도록 가장 적합 한 결정을 합니다. 또한 시간 서비스 구성 된 시간 출처 중 어느 것이 가장 정확한 확인 하려면 알고리즘 다른 집합을 사용 합니다. 시간 서비스는 시간이 샘플 가장 적합 한 결정가, 올바른 시간 쪽 수렴 디바이스인 로컬 클럭 속도 조정 위의 조건에 따라 합니다. 로컬 시간과 (시간 기울이기) 선택한 시간 범위 정확 하 게 샘플 시간 차이점 너무 커서 로컬 클럭 속도 조정 하 여 해결할 수 없는 경우 시간 서비스 로컬 시계 올바른 시간을 설정 합니다. 직접 시계 시간 변경 또는 클럭 속도이 조정 시계 분야 라고 합니다.  
  
## <a name="w2k3tr_times_how_rrfo"></a>Windows 서비스 아키텍처 시간  
Windows 시간 서비스 다음과 같은 구성 요소 이루어져 있습니다.  
  
-   서비스를 제어 관리자  
  
-   Windows 서비스 관리자 시간  
  
-   시계 분야  
  
-   시간 공급자  
  
다음 그림은 Windows 시간 서비스의 아키텍처 합니다.  
  
**Windows 서비스 아키텍처 시간**  
  
![Windows 시간](media/How-the-Windows-Time-Service-Works/trnt_sec_arcc.gif)  
  
시작 및 중지 Windows 시간 서비스에 대 한 서비스를 제어 관리자는 합니다. Windows 시간 서비스 관리자는 운영 체제에 포함 된 NTP 시간 공급자의 작업을 시작 합니다. Windows 시간 서비스 관리자 모든 시간 샘플 병합 하 고 Windows 시간 서비스의 모든 기능을 제어할 수 있습니다. 이외에 현재 시스템 상태에 대 한 정보는 현재 시간 소스 또는 마지막 시간 시스템 클록와 같은 업데이트를 제공 하는 Windows 시간 서비스 관리자는 또한 이벤트 로그에 이벤트를 만들기 위한 합니다.  
  
시간 동기화 프로세스 단계는 다음과 같습니다.  
  
-   공급자 요청을 입력 하 고 구성 된 NTP 시간 출처에서 시간 샘플을 받습니다.  
  
-   이 시간 샘플 Windows 시간 서비스 관리자에를 모두 샘플을 수집 하 고 시계 분야 하위를 전달 하는 전달 됩니다.  
  
-   시계 분야 하위에 가장 적합 한 시간 샘플 선택 NTP 알고리즘 적용 됩니다.  
  
-   시계 분야 하위 클럭 속도 조정 하거나 직접 시간 변경 하는 가장 정확한 시간 시스템 클록 시간을 조정 합니다.  
  
컴퓨터를 시간 서버도 지정 하는 경우이 과정에서 언제 든 지 동기화 시간을 요청 하는 컴퓨터에 로그온 할 때를 보낼 수 있습니다.  
  
## <a name="w2k3tr_times_how_ekoc"></a>Windows 서비스 시간 프로토콜 시간  

시간 프로토콜 정도 두 컴퓨터 결정 시계 동기화 됩니다. 시간 프로토콜 최상의 사용할 수 있는 시간 정보를 확인 하 고 일관 된 시간은 별도 시스템에 유지 되도록 시계 수렴 담당 합니다.  
  
Windows 시간 서비스 네트워크 시간 Protocol (NTP)를 사용 하 여 네트워크를 통해 시간이 동기화 할 수 있도록 합니다. NTP 시계 동기화 하는 데 필요한 분야 알고리즘을 포함 하는 인터넷 프로토콜 시간입니다. NTP은 더 정확 하 게 시간 프로토콜 보다는 네트워크 시간 (SNTP 프로토콜), Windows의 일부 버전에 사용 되는 그러나 W32Time SNTP Windows 2000 등의 시간 SNTP 기반 서비스를 실행 하는 컴퓨터 이전 버전과 호환성을 지원 하기 위해 계속 합니다.  
  
### <a name="network-time-protocol"></a>네트워크 시간이 프로토콜  
네트워크 시간 (NTP Protocol)을 기본 설정 동기화 프로토콜 운영 체제에 Windows 시간 서비스에서 사용 시간을 합니다. NTP 장애 조치, 확장성 시간 프로토콜 이며 컴퓨터 시계 지정 된 시간 참조를 사용 하 여 동기화 하는 데 가장 자주 사용 하는 프로토콜 합니다.  
  
NTP 시간 동기화 일정 시간을 통해 수행와 네트워크를 통해 전송 NTP 패킷 포함 됩니다. NTP 패킷을 동기화 시간에에서는 클라이언트와 참여 서버에서 시간 샘플이 포함 타임 스탬프 포함 되어 있습니다.  
  
NTP을 사용 하는 가장 정확한 시간 정의 참조 시계를 사용 하 고 해당 참조 시계를 네트워크의 모든 시계를 동기화 합니다. NTP 범용 표준으로 세계시 (협정)를 사용 하는 현재 시간에 대 한 합니다. 표준 시간대 독립적인 UTC 이며 NTP 표준 시간대 설정과 관계 없이 전 세계의 어디서 나 사용 가능 합니다.  
  
#### <a name="ntp-algorithms"></a>NTP 알고리즘  
두 개의 알고리즘, 시계 필터링 알고리즘을 및 선택 시계 알고리즘을 결정 하는 데 가장 적합 한 시간 샘플 Windows 시간 서비스를 지원 하기 위해 NTP 포함 되어 있습니다. 시계 필터링 알고리즘 쿼리 시간 소스에서 수신 하 고 각 소스에서 최상의 시간 샘플 결정 하는 시간 샘플 조사 하도록 설계 되었습니다. 시계 선택 알고리즘 네트워크에서 가장 정확한 시간 서버를 확인합니다. 이 정보는 컴퓨터의 로컬 시간 동안 보상 네트워크 대기 하 고 컴퓨터 시계 부정확 인해 오류에 대 한 수정 수집 된 정보를 사용 하 고 시계 분야 알고리즘을 전달 됩니다.  
  
NTP 알고리즘 조건 경량 일반 네트워크 및 서버 로드 중에서 가장 정확한 됩니다. 네트워크 교통 시간 고려 하는 모든 알고리즘을와 마찬가지로 NTP 알고리즘 익스트림 네트워크 혼잡의 조건 잘못 수행할 수 있습니다. IETF RFC 데이터베이스에 RFC 1305 NTP 알고리즘에 대 한 자세한 내용은 참조 합니다.  
  
#### <a name="ntp-time-provider"></a>NTP 시간 공급자  
Windows 시간 서비스는 다양 한 하드웨어 디바이스와 시간 프로토콜을 지원할 수 있는 전체 시간 동기화 패키지. 이 기능을 사용 하도록 설정 하는 서비스 방식 시간 공급자 사용 합니다. 시간 공급자는 하거나 얻는 정확 하 게 타임 스탬프 (네트워크 또는에서 하드웨어)에 대 한 또는 다른 컴퓨터에 타임 스탬프 해당 네트워크를 통해 제공 하기 위해 해야 합니다.  
  
NTP 공급자는 운영 체제에 포함 된 표준시 공급자 합니다. NTP 공급자 NTP 클라이언트 및 서버에 대 한 3 버전으로 지정 된 표준 하 게 SNTP 클라이언트 및 서버 이전 버전과 호환성 다른 SNTP 클라이언트와 Windows 2000에 대 한와 상호 작용할 수 있습니다. Windows 시간 서비스에서 NTP 공급자는 다음과 같은 두 가지 부분이 이루어져 있습니다.  
  
-   **NtpServer 출력 공급자 합니다.** 네트워크에 대 한 클라이언트 시간 요청에 응답 하는 시간 서버입니다.  
  
-   **NtpClient 입력된 공급자 합니다.** 이 하드웨어 디바이스 또는 NTP 서버를 다른 소스에서 시간 정보를 가져오고 로컬 시계 동기화 하는 데 도움이 되는 시간 샘플 돌아갈 수 있는 시간 클라이언트 합니다.  
  
이러한 두 가지 공급자의 실제 작업은 밀접 있지만 시간 서비스 독립 표시 됩니다. Windows 2000 Server, Windows 컴퓨터가 네트워크에 연결 되어 있을 때 시작을 NTP 클라이언트로 구성 되어 있습니다. 또한 Windows 시간을 실행 하는 컴퓨터 서비스만 시간 기본적으로 수동으로 지정 된 시간 소스 또는 도메인 컨트롤러 동기화를 시도 합니다. 원하는 시간 공급자 시간 소스 안전한를 자동으로 사용할 수 있기 때문에입니다.  
  
#### <a name="ntp-security"></a>NTP 보안  

AD DS 숲, 내 Windows 시간 서비스는 표준 도메인 보안 기능 시간 데이터 인증 적용 하기 위해 사용 합니다. NTP 패킷 도메인 회원 컴퓨터와 시간 서버 역할을 하는 로컬 도메인 컨트롤러 전송 된 보안 키 인증 공유를 기반으로 합니다. Windows 시간 서비스 컴퓨터의 Kerberos 세션 키를 사용 하 여 네트워크를 통해 전송 NTP 패킷을에 인증된 서명을 만들 수 있습니다. 네트워크 로그온 보안 채널 내부 NTP 패킷은 전송 되지 않습니다. 대신 도메인 계층 있는 도메인 컨트롤러에서 시간을 요청 하는 컴퓨터를 Windows 시간 서비스 시간 인증을 해야 합니다. 도메인 컨트롤러 Netlogon 서비스에서 세션 키가 있는 인증 된 64 비트 값 형태의 필요한 정보를 반환 합니다. 반환된 NTP 패킷 컴퓨터의 세션 키 서명 되지 않았습니다 또는 올바르게 서명 되었는지 시간 거부 됩니다. 이러한 모든 인증 오류 이벤트 로그에 기록 됩니다. 이런 방법이으로 Windows 시간 서비스는 광고 DS 숲 속의 NTP 데이터에 대 한 보안을 제공합니다.  
  
일반적으로 Windows 시간 클라이언트 동일한 도메인에 있는 도메인 컨트롤러에서 동기화에 대 한 정확한 시간을 자동으로 가져옵니다. 숲, 자녀가 도메인 도메인 컨트롤러 시간 자신의 부모 도메인 도메인 컨트롤러에서에서을 동기화 합니다. 시간 서버에서 시간을 요청 하는 클라이언트 인증된 NTP 패킷 돌아오면 패킷이 정의 된 대로만 도메인 간 신뢰 계정을 Kerberos 세션 키를 사용 하 여 서명 됩니다. 도메인 간 신뢰 계정은 새로운 광고 DS 도메인 가입 숲, Netlogon 서비스 관리 세션 키 때 만들어집니다. 이런 방법으로 숲 루트 도메인 안정적으로 구성 되어 있는 도메인 컨트롤러 인증 된 시간 소스 부모 및 자녀 도메인에 있는 도메인 컨트롤러의 모든 및 간접 도메인 밤나무에 있는 모든 컴퓨터에 대 한 됩니다.  
  
Windows 시간 서비스 숲 사이 작동 하도록 구성할 수 있습니다 하지만 것이 중요이 구성은 안전 하지 않습니다. 예를 들어, ntp 다른 숲에서 사용할 수 있습니다. 그러나 해당 컴퓨터 다른 숲 속의 이기 때문에 인증 NTP 패킷 로그인 하는 없는 Kerberos 세션 키가 있습니다. 클라이언트 정확한 시간 동기화 다른 숲 속의 컴퓨터에서를 얻으려면 네트워크 해당 컴퓨터에 액세스할 수 있어야 하 고 다른 숲 속에 있는 특정 시간 소스를 사용 하 여 시간 서비스를 구성 합니다. 클라이언트 수동으로 자체 도메인 계층 외 NTP 서버에서 구성에 대 한 액세스, 전송는 클라이언트와 시간 서버 NTP 패킷을 인증 되지 않은 및 따라서 보안 되지 않습니다. 숲 신뢰 구현 사용 하더라도 Windows 시간 서비스 안전 하지 않습니다 숲 간에. 네트워크 로그온 보안 채널 인증 메커니즘 Windows 시간 서비스에 대 한 인 숲 간 인증 지원 되지 않습니다.  
  
#### <a name="hardware-devices-that-are-supported-by-the-windows-time-service"></a>Windows 시간 서비스에서 지원 되는 하드웨어 디바이스  
GPS 등 하드웨어 기반 시계 또는 라디오 시계 매우 정확 하 게 참조 시계 디바이스 자주 사용 됩니다. 기본적으로 Windows 시간 서비스 NTP 시간이 공급자가 하드웨어 디바이스를 컴퓨터에 직접 연결을 지원 하지, 이러한 종류의 연결을 지 원하는 독립 시간 소프트웨어 공급자를 만들 수는 있지만 합니다. 이러한 유형의 함께 Windows 시간 서비스 공급자 안정적이 고 안정적인 시간 참조를 제공할 수 있습니다.  
  
글로벌 Positioning System (GPS) 수신기 cesium 시계 등 하드웨어 디바이스 정확한 최신 시간 시간 정확도 정의 얻는 표준에 따라 제공 합니다. 매우 안정적 cesium 시계 온도, 압력, 또는 습도 같은 요인 영향을 받지 않습니다 있지만 부담이 수도 있습니다. GPS 수신기 훨씬 저렴 하 게 작동 이며 정확한 참조 시계 이기도 합니다. GPS 수신기 cesium 시계에서 시간을 얻게 위성에서 자녀가 시간을 받습니다. 독립 시간 공급자를 사용 하지 않고 Windows 시간 서버 전화나 인터넷을 사용 하 여 하드웨어 디바이스에 연결 되는 외부 NTP 서버에 연결 하 여 자녀가 시간을 얻을 수 있습니다. 조직 미국 해 관측 등 매우 안정적 참조 시계가에 연결 되어 있는 NTP 서버를 제공 합니다.  
  
네트워크에서 NTP 서버 많은 GPS 수신기 및 기타 시간 장치 작동할 수 있습니다. 것도 역할을 하는 네트워크에 NTP 서버 하는 경우에 이러한 외부 하드웨어 디바이스에서 시간을 동기화 하 여 광고 DS 숲을 구성할 수 있습니다. 이렇게 하기 위해 GPS 장치에서 제공 NTP 서버와 동기화 하 여 숲 루트에서 (PDC) 에뮬레이터 주 도메인 컨트롤러 역할 도메인 컨트롤러를 구성 합니다. 이렇게 하기 위해 참조 [Windows 시간 서비스 숲 루트 도메인 PDC 에뮬레이터 구성](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731191%28v=ws.10%29)합니다.  
  
### <a name="simple-network-time-protocol"></a>단순 네트워크 시간이 프로토콜  
네트워크 시간 (SNTP 프로토콜)는 간단한 시간 프로토콜 서버와 클라이언트의 NTP 제공 정확도 필요 하지 않은 것입니다. SNTP 더 기본적인 버전 ntp, Windows 2000에 사용 되는 기본 시간 프로토콜입니다. 두 개의 프로토콜은 SNTP 및 NTP 네트워크 패킷 형식 동일한 되므로 상호 운용성 합니다. 두 기본 차이점은 SNTP 오류 관리와 NTP를 제공 하는 복잡 한 필터링 시스템 되어 있지 않습니다. 단순 네트워크 시간이 프로토콜에 대 한 자세한 내용은 RFC 1769 IETF RFC 데이터베이스에 표시 됩니다.  
  
### <a name="time-protocol-interoperability"></a>프로토콜 상호 운용성 시간  
Windows 2000에 사용 되는 SNTP 프로토콜은 Windows XP 및 Windows Server 2003 NTP 프로토콜와 상호 작용 하기 때문에 Windows 2000, Windows XP 및 Windows Server 2003을 실행 하는 컴퓨터의 혼합된 환경에서 Windows 시간 서비스 작동할 수 있습니다.  
  
서버 해상도 TimeServ, 라는 시간 서비스 요구 사항 네트워크를 통해 시간이 동기화 합니다. TimeServ은으로 사용할 수 있는 추가 기능의 일부로 *Microsoft Windows NT 4.0 리소스 키트* 수준을 시간 동기화 Windows Server 2003에 필요한의 안정성을 제공 하지 않습니다.  
  
시간 Windows 2000 또는 Windows Server 2003, 실행 중인 컴퓨터와 동기화 할 수 있습니다 때문에 요구 사항을 실행 하는 컴퓨터와 상호 작용할 수 Windows 시간 서비스 그러나 Windows 2000 또는 Windows Server 2003을 실행 하는 컴퓨터 요구 사항 시간 서버를 자동으로 검색 하지 않습니다. 예를 들어 도메인 계층 기반 도메인을 사용 하 여 시간 동기화 하도록 구성 된 경우 동기화 하 고 원하는 시간을 요구 사항 도메인 컨트롤러 동기화 하도록 도메인 계층 컴퓨터, 요구 사항 도메인 컨트롤러 관련 동기화 하도록 직접 해당 컴퓨터를 구성 해야 할 합니다.  
  
요구 사항 시간 동기화 Windows 시간 서비스 사용 하 여 보다 간단 메커니즘을 사용합니다. 따라서 네트워크를 통해 정확한 시간 동기화 되도록 것이 좋습니다 Windows 2000 또는 Windows Server 2003 요구 사항 도메인 컨트롤러를 업그레이드 합니다.  
  
## <a name="w2k3tr_times_how_izcr"></a>Windows 서비스 프로세스와 상호 작용 시간  

Windows 시간 서비스 네트워크의 컴퓨터에 시계 동기화 하도록 설계 되었습니다. 시간 수렴 라고도 네트워크 시간 동기화 프로세스 네트워크를 통해 더 정확 하 게 시간 서버에서 컴퓨터 액세스 때마다 발생 합니다. 시간 수렴은 권한 서버 NTP 패킷의 형태로 클라이언트 컴퓨터에 현재 시간을 제공 하는 프로세스는 포함 됩니다. 패킷을 내에서 제공 하는 정보에 게는 컴퓨터의 현재 시간을 더 정확 하 게 서버와 동기화 하는 조정 필요한 지 여부를 나타냅니다.  
  
시간 수렴 과정의 일환으로, 도메인 회원 시간 같은 도메인에 있는 모든 도메인 컨트롤러 동기화 하려고 합니다. 컴퓨터가 도메인 컨트롤러 경우 더욱 신뢰할 수 있는 도메인 컨트롤러와 동기화 하도록 시도 합니다.  
  
컴퓨터가 도메인에 가입 하지 않은 또는 Windows XP Home 버전을 실행 하는 컴퓨터 도메인 계층와 동기화 하지 마십시오 하지만 time.windows.com에서 시간을 얻을 수 기본적으로 구성 됩니다.  
  
Windows Server 2003 권한으로 실행 하는 컴퓨터를 설정 하려면 컴퓨터 확보할 신뢰할 수 있는 시간을 설정 해야 합니다. 기본적으로 Windows Server 2003 도메인에 설치 되어 있는 도메인 컨트롤러 첫 번째 신뢰할 수 있는 시간 소스를 자동으로 구성 됩니다. 신뢰할 수 있는 컴퓨터에서 도메인 때문 도메인 계층 대신 외부 시간 소스를 사용 하 여 동기화 하도록 설정 해야 합니다. 또한 기본적으로 모든 Windows Server 2003 도메인 구성원 도메인 계층와 동기화 하도록 구성 됩니다.  
  
Windows Server 2003 네트워크 설정한 후에 동기화 다음 옵션 중 하나를 사용 하 여 Windows 시간 서비스를 구성할 수 있습니다.  
  
-   도메인 계층 기반 동기화  
  
-   동기화 수동으로 지정 소스  
  
-   모든 사용 가능한 동기화 메커니즘  
  
-   동기화 하지 않습니다.  
  
각각의 동기화 형식을 다음 섹션에 설명 되어 있습니다.  
  
### <a name="domain-hierarchy-based-synchronization"></a>도메인 계층 기반 동기화  

동기화 도메인 계층을 기반으로 하는 광고 DS 도메인 계층을 사용 하 여 시간을 동기화 할 신뢰할 수 있는 소스를 찾을 수 있습니다. 도메인 계층에 따라, Windows 시간 서비스의 각 시간 서버 정확도 결정 합니다. Windows Server 2003 숲 주 도메인 컨트롤러 (PDC) 에뮬레이터 operations 마스터 역할을 숲 루트 도메인에 있는 컴퓨터 신뢰할 수 있는 시간 다른 소스 구성 하지 않은 경우 최상의 시간 원본의 위치를 보유 합니다. 다음 그림은 컴퓨터에서 도메인 계층 간 동기화의 경로 합니다.  
  
**광고 DS 계층 시간 동기화**  
  
![Windows 시간](media/How-the-Windows-Time-Service-Works/trnt_ntw_adhc.gif)  
  
#### <a name="reliable-time-source-configuration"></a>신뢰할 수 있는 시간 소스 구성  
신뢰할 수 있는 시간을 확보할 하도록 구성 된 컴퓨터 시간 서비스의 루트도 식별 됩니다. 시간 서비스의 루트 도메인에 대 한 권한 있는 서버 이며 외부 NTP 서버 이나 하드웨어 디바이스에서 시간을 검색 일반적으로 구성 됩니다. 시간 서버 시간이 도메인 계층 전체 전송 되는 방식을 최적화 하기 위해 신뢰할 수 있는 시간 원본으로 구성할 수 있습니다. 도메인 컨트롤러 신뢰할 수 있는 시간을 확보할으로 구성 된, Netlogon 서비스 네트워크에 로그온 할 때 신뢰할 수 있는 시간 원본으로 도메인 컨트롤러를 알립니다. 다른 도메인 컨트롤러와 동기화 하도록 시간 소스를 찾을 때 선택한 신뢰할 수 있는 원본 먼저 사용 가능한 경우 합니다.  
  
#### <a name="time-source-selection"></a>시간 소스 선택  
시간 소스 선택 프로세스 두 가지 문제는 네트워크에 만들 수 있습니다.:  
  
-   추가 동기화 주기 합니다.  
  
-   네트워크 교통에서 볼륨 증가 합니다.  
  
주기 동기화 네트워크에 있는 시간 사이 그룹 도메인 컨트롤러의 일관성을 유지 하 고 동시 다른 신뢰할 수 있는 시간 기기 동기화 지속적으로 없이 서로 공유 때 발생 합니다. 이러한 유형의 문제를 방지 하는 Windows 시간 서비스 시간 소스 선택 알고리즘 설계 되었습니다.  
  
컴퓨터와 동기화 하도록 시간 소스를 식별 하기 위해 다음 방법 중 하나를 사용 합니다.  
  
-   컴퓨터가 도메인의 회원 경우 지정 된 시간 원본와 동기화 하도록 설정 해야 합니다.  
  
-   컴퓨터가 구성원 서버 또는 기본적으로 도메인 워크스테이션 AD DS 계층을 따릅니다 하 고 해당 표준 Windows 시간 서비스에서 현재 실행 중인 로컬 도메인에 있는 도메인 컨트롤러와 동기화 합니다.  
  
컴퓨터가 도메인 컨트롤러를 하면 최장 6 쿼리와 동기화 하도록 다른 도메인 컨트롤러를 찾을 수 있습니다. 특정 위치 도메인 컨트롤러의 종류와 같은 특정 특성으로 한 번 소스를 확인 하도록 설계 된 각 쿼리의 신뢰할 수 있는 시간 소스는 여부 하 고 있습니다. 또한 시간 소스 같은 제한 준수 해야 합니다.  
  
-   신뢰할 수 있는 시간 소스 부모 도메인에 도메인 컨트롤러 동기화 할 수 있습니다.  
  
-   PDC 에뮬레이터 고유한 도메인 신뢰할 수 있는 시간 소스 또는 부모 도메인에 있는 도메인 컨트롤러 동기화 할 수 있습니다.  
  
도메인 컨트롤러 쿼리 하는 도메인 컨트롤러의 종류와 동기화 할 수 없는 경우 쿼리 하지 이루어집니다. 도메인 컨트롤러 어떤 종류의 컴퓨터 쿼리 하기 전에에서 시간을 받을 수 있는 것을 알고 있습니다. 예를 들어, PDC 현지 에뮬레이터 도메인 컨트롤러 자체적으로 동기화 하지 하려고 때문에 세 또는 6 쿼리 번호로 시도 하지 않습니다.  
  
다음 표에 쿼리 도메인 컨트롤러에서 시간 원본과 쿼리 사항이 순서를 찾을 수 있습니다.  
  
**도메인 컨트롤러 시간 원본 쿼리**  
  
|쿼리 번호|도메인 컨트롤러|위치|안정성 시간 소스의|  
|----------------|---------------------|------------|------------------------------|  
|1|부모 도메인 컨트롤러|사이트에서|선호를 신뢰할 수 있는 시간 소스 하지만와 동기화 할 수 시간을 신뢰할 수 없는 출처 모두 사용할 수 있는 경우 합니다.|  
|2|로컬 도메인 컨트롤러|사이트에서|신뢰할 수 있는 시간 소스 동기화만 합니다.|  
|3|로컬 PDC 에뮬레이터|사이트에서|적용 되지 않습니다.<br /><br />자신과 동기화 하는 도메인 컨트롤러 시도 하지 않습니다.|  
|4|부모 도메인 컨트롤러|사이트 제한|선호를 신뢰할 수 있는 시간 소스 하지만와 동기화 할 수 시간을 신뢰할 수 없는 출처 모두 사용할 수 있는 경우 합니다.|  
|5|로컬 도메인 컨트롤러|사이트 제한|신뢰할 수 있는 시간 소스 동기화만 합니다.|  
|6|로컬 PDC 에뮬레이터|사이트 제한|적용 되지 않습니다.<br /><br />자신과 동기화 하는 도메인 컨트롤러 시도 하지 않습니다.|  
  
**노트**  
  
-   컴퓨터의 하지 자체적으로 동기화 됩니다. 동기화 하려는 컴퓨터 PDC 현지 에뮬레이터를 쿼리 3 또는 6 시도 하지 않습니다.  
  
각 쿼리 시간 원본으로 사용할 수 있는 도메인 컨트롤러 목록이 반환 됩니다. Windows 시간 할당은 각 도메인 컨트롤러 안정성과 도메인 컨트롤러의 위치에 따라 점수를 묻습니다. 다음 표에서 Windows 시간 각 유형의 도메인 컨트롤러에 할당 점수 보여 줍니다.  
  
**점수 결정**  
  
|도메인 컨트롤러의 상태|점수|  
|----------------------------|---------|  
|동일한 사이트의 설치 되어 있는 도메인 컨트롤러|8|  
|신뢰할 수 있는 시간 소스 것으로 표시 되는 도메인 컨트롤러|4|  
|부모 도메인에 있는 도메인 컨트롤러|2|  
|PDC 에뮬레이터가 도메인 컨트롤러|1|  
  
Windows 시간 서비스 최상의 가능한 점수가 도메인 컨트롤러 식별가 하도록 결정을 더 쿼리가 없는 수 있습니다. 시간 서비스에서 할당 점수는 누적 같은 사이트에 있는 PDC 에뮬레이터-9 점수를 받습니다.  
  
외부 원본와 동기화 하도록 루트 시간 서비스의 구성 되어 있지 않으면, 컴퓨터의 내부 하드웨어 시계는 시간을 관리 합니다.  
  
### <a name="manually-specified-synchronization"></a>수동으로 지정 동기화  
동기화 수동으로 지정 단일 피어 또는 컴퓨터 얻는 시간 피어 목록이 지정할 수 있습니다. 컴퓨터가 도메인의 회원 경우 것 수동으로 구성 해야 지정 된 시간 원본와 동기화 하도록 합니다. 를 도메인의 회원은 도메인 계층에서 동기화 하는 기본적으로 구성 된 컴퓨터 수동으로 지정 동기화는 도메인의 숲 루트 또는 컴퓨터가 도메인에 가입 하지 않은 가장 유용 합니다. 신뢰할 수 있는 시간을 제공 수동으로 도메인에 대 한 권한 컴퓨터와 동기화 하도록 외부 NTP 서버를 지정 합니다. 그러나 하드웨어 시계와 동기화 하도록 도메인에 대 한 권한 있는 컴퓨터를 구성 하는 가장 정확한, 보안 시간 도메인을 제공 하기 위해 더 나은 솔루션 실제로입니다.  
  
특정 시간 공급자는을 위해 작성 하 고 공격을 받기 따라서는 하지 않으면 수동으로 지정 된 시간 소스 인증 되지 않습니다. 또한 인증 도메인 컨트롤러를 사용 하지 않고 수동으로 지정 소스는 컴퓨터 동기화, 두 컴퓨터에 실패 Kerberos 인증 발생 동기화 되지 않은 상태로 수 있습니다. 인쇄 또는 공유 파일 등 실패 하는 네트워크 인증을 요구 다른 작업 않을 수 있습니다. 경우에 숲 루트를 외부 원본와 동기화 하도록 구성 숲 내에서 다른 모든 컴퓨터 재생 공격 어렵게, 서로 동기화 남아 있습니다.  
  
### <a name="all-available-synchronization-mechanisms"></a>모든 사용 가능한 동기화 메커니즘  

"모든 사용 가능한 동기화 메커니즘" 옵션은 사용자가 네트워크에 대 한 가장 중요 한 동기화 방법입니다. 이 방법을 도메인 계층와 동기화 할 수 있습니다 한 대안을 제공할 수 도메인 계층 구성에 따라 사용할 수 없는 경우 원본 시간 합니다. 클라이언트 시간 도메인 계층을 동기화 할 수 없는 경우 시간 원본 자동으로 변경 하 여 지정 된 시간 소스는 **NtpServer** 설정 합니다. 이 방법은 동기화 정확한 시간 클라이언트를 제공 하는 가장 많이 것입니다.  

### <a name="stopping-time-synchronization"></a>시간 동기화 중지  
일부 경우에 컴퓨터에서 동기화 된 시간을 중지 하려면 할 수 있습니다. 예를 들어, 컴퓨터 wan 전화 접속 연결을 사용 하 여 인터넷 시간 소스의 또는 다른 웹 사이트에서 동기화 하려고 하는 경우 비용 전화 요금이 부과 수 있는 것입니다. 컴퓨터에서 동기화를 비활성화 하면 컴퓨터를 전화 접속 연결을 통해 시간 소스에 액세스 하려고 할 때 되지 않습니다.  
  
이벤트 로그에서 오류를 생성 하지 않으려면 동기화를 비활성화할 수도 있습니다. 컴퓨터에서 동기화를 사용할 수 있는 시간 원본과 하려고 할 때마다 이벤트 로그에 오류가 발생 합니다. 시간 소스 예약된 유지 관리에 대 한 네트워크 오프 라인 상태일 클라이언트 다른 소스 로부터 동기화를 다시 구성 하지 않으려는 경우 시간 서버를 사용할 수 없을 때 동기화 시도 하 않도록 클라이언트에서 동기화를 비활성화할 수 있습니다.  
  
동기화 네트워크 루트로 지정 된 컴퓨터에서 동기화를 사용 하지 않도록 설정 하려면 유용 합니다. 이 루트 컴퓨터의 로컬 시계를 신뢰를 나타냅니다. 동기화 계층 루트 하도록 설정 하지 않은 경우 **NoSync** 클라이언트 다른 시간 원본와 동기화 할 수 없는 경우이 컴퓨터의 시간 신뢰할 수 없으므로 보내 패킷 동의 하지 않으면 하 고 있습니다.  
  
경우에 다른 시간 기기 동기화 되지 않은 경우에 클라이언트에서 신뢰할 수 있는 서버는 신뢰할 수 있는 시간 서버로 클라이언트에서 식별 된 것입니다.  
  
### <a name="disabling-the-windows-time-service"></a>Windows 시간 서비스를 사용 하지 않도록 설정  
(W32Time) Windows 시간 서비스는 완전히 비활성화할 수 있습니다. NTP 사용 하는 제 시간 동기화 제품 하기로 Windows 시간 서비스를 사용 하지 않도록 설정 해야 합니다. 사용자 데이터 그램 Protocol (UDP) 포트 123에 액세스 해야 하는 모든 NTP 서버 포트 123 남아 Windows 시간에 의해 예약 된 Windows 시간 서비스 Windows Server 2003 운영 체제에서 실행 중인,으로 때문입니다.  
  
## <a name="w2k3tr_times_how_ydum"></a>Windows 시간이 서비스에서 사용 되는 네트워크 포트  
신뢰할 수 있는 시간 소스를 식별, 시간 정보 및 다른 컴퓨터를 표준 정보를 제공 하는 네트워크에 Windows 시간 서비스 통신 합니다. NTP 및 SNTP Rfc에 정의 된 대로이 통신을 수행 합니다.  
  
**Windows 시간 서비스에 대 한 포트 할당**  
  
|서비스 이름|UDP|TCP|  
|----------------|-------|-------|  
|NTP|123|해당 없음|  
|SNTP|123|해당 없음|  
  
## <a name="see-also"></a>참조 하십시오  
[Windows 시간이 서비스 기술 참조](https://technet.microsoft.com/library/cc773061.aspx)  
[Windows 서비스 도구 시간 및 설정](Windows-Time-Service-Tools-and-Settings.md)  
[Microsoft 기술 자료 문서 902229](https://go.microsoft.com/fwlink/?LinkId=186066)  
  

