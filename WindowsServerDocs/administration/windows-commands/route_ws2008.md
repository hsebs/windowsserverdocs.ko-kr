---
title: route_ws2008
description: 수정 하 고 로컬 IP 라우팅 테이블에 항목을 표시 하는 방법에 알아봅니다.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afcd666c-0cef-47c2-9bcc-02d202b983b3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 1164767a80b4d7dd24152bc34eda5d88834c1bdb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854824"
---
# <a name="routews2008"></a>route_ws2008

>적용 대상: Windows Server (반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

표시 하 고 로컬 IP 라우팅 테이블에 있는 항목을 수정 합니다. 매개 변수 없이 사용 **경로** 도움말을 표시 합니다.   

## <a name="syntax"></a>구문  
```  
route [/f] [/p] [<Command> [<Destination>] [mask <Netmask>] [<Gateway>] [metric <Metric>]] [if <Interface>]]  
```  

### <a name="parameters"></a>매개 변수  

|매개 변수|설명|  
|-------|--------|  
|/f|호스트 경로 (네트워크 마스크가 255.255.255.255), 루프백 네트워크 경로 (127.0.0.0이 대상 및 네트워크 마스크 255.0.0.0 경로) 또는 멀티 캐스트 경로 하지 않은 모든 항목의 라우팅 테이블을 지웁니다 (대상이 224.0.0.0 240.0.0.0 네트워크 마스크와 경로). 이 명령 (예: 추가, 변경 또는 삭제) 중 하 나와 함께에서 사용 됩니다, 명령을 실행 하기 전에 테이블이 지워집니다.|  
|/p|Add 명령을 사용 하면 지정된 된 경로를 레지스트리에 추가 되 고 TCP/IP 프로토콜을 시작할 때마다 IP 라우팅 테이블을 초기화 하는 데 사용 됩니다. 기본적으로 TCP/IP 프로토콜 시작 될 때 추가 된 경로가 유지 되지 않습니다. 인쇄 명령을 사용 하 여 사용 하는 경우에 영구 경로 목록에 표시 됩니다. 이 매개 변수는 다른 모든 명령에 대해 무시 됩니다. 영구 경로 레지스트리 위치에 저장 된 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\PersistentRoutes**합니다.|  
|\<명령 >|실행할 명령을 지정 합니다. 다음 표에서 유효한 명령 보여 줍니다.<br /><br />-   **추가:** 경로 추가 합니다.<br />-   **변경:** 기존 경로 수정 합니다.<br />-   **삭제:** 경로 또는 경로 삭제 합니다.<br />-   **인쇄:** 경로 또는 경로 인쇄 합니다.|  
|\<대상 >|네트워크 대상 경로 지정합니다. 대상 IP 네트워크 주소 (위치: 네트워크 주소의 호스트 비트는 0으로 설정 함), 호스트 경로 대 한 IP 주소 또는 기본 경로 대 한 0.0.0.0 될 수 있습니다.|  
|마스크 \<네트워크 마스크 >|네트워크 대상 경로 지정합니다. 대상 IP 네트워크 주소 (위치: 네트워크 주소의 호스트 비트는 0으로 설정 함), 호스트 경로 대 한 IP 주소 또는 기본 경로 대 한 0.0.0.0 될 수 있습니다.|  
|\<Gateway>|주소는 네트워크 대상과 서브넷 마스크에 의해 정의 된 집합은 도달할 수 있는 이전 또는 다음 홉 IP 주소를 지정 합니다. 로컬로 연결 된 서브넷 경로 게이트웨이 주소는 서브넷에 연결 하는 인터페이스에 할당 된 IP 주소입니다. 원격 경로 대 한 하나 이상의 라우터를 통해 사용할 수는 게이트웨이 주소는 인접 라우터에 할당 된 IP 주소를 직접 연결할 수 있습니다.|  
|메트릭 \<메트릭 >|가장 근접 하 게 전달 되는 패킷의 대상 주소와 일치 하는 라우팅 테이블에 여러 경로 중에서 선택할 때 사용 되는 경로 대 한 정수 비용 메트릭 (1에서 9999)를 지정 합니다. 가장 낮은 메트릭 가진 경로가 선택 됩니다. 메트릭을 홉 수, 경로, 경로 안정성, 경로 처리량 또는 관리 속성의 속도 반영할 수 있습니다.|  
|경우 \<인터페이스 >|대상에 연결할 수 있는 인터페이스에 대 한 인터페이스 인덱스를 지정 합니다. 인터페이스 및 해당 인터페이스 인덱스는 목록은 route print 명령의 표시를 사용 합니다. 인터페이스 인덱스에 대 한 10 진수 또는 16 진수 값을 사용할 수 있습니다. 16 진수 값 0 x는 16 진수 앞에 있습니다. 경우는 매개 변수를 생략 하는 경우 인터페이스 게이트웨이 주소에서 결정 됩니다.|  
|/?|명령 프롬프트에 도움말을 표시합니다.|  

## <a name="remarks"></a>설명  
-   큰 값은 **메트릭을** 라우팅 테이블의 열은 자동으로 IP 주소, 서브넷 마스크 및 기본 게이트웨이 각 LAN 인터페이스의 구성에 따라 라우팅 테이블에서 경로 대 한 메트릭을 확인 하는 TCP/IP를 허용 하는 결과입니다. 각 인터페이스의 속도 확인 하 고 가장 빠른 인터페이스에서 가장 낮은 메트릭을 가진 경로 만들 수 있도록 각 인터페이스에 대 한 경로의 메트릭을 조정 하는 기본적으로 사용 하는 인터페이스 메트릭의 자동 결정 합니다. 큰 메트릭을 제거 하려면 각 LAN 연결에 대해 TCP/IP 프로토콜의 고급 속성에서 인터페이스 메트릭의 자동 결정을 사용 하지 않도록 설정 합니다.  
-   이름에 사용할 수 있습니다 *대상* 적절 한 항목에 저장 된 로컬 네트워크 파일에 있는 경우는 **systemroot\System32\Drivers\\**등 폴더입니다. 이름에 사용할 수는 *게이트웨이* 에 저장 된 로컬 Hosts 파일의 사용으로 도메인 이름 시스템 (DNS) 쿼리와 같은 표준 호스트 이름 확인 기술을 통해 IP 주소를 확인할 수 있습니다는 **systemroot\system32\drivers\\**등 폴더 및 NetBIOS 이름 확인 합니다.  
-   명령이 **인쇄** 또는 **삭제**서 *게이트웨이* 매개 변수를 생략할 수와 대상 및 게이트웨이에 와일드 카드를 사용할 수 있습니다. *대상* 별표 (*)가 지정 하는 와일드 카드 값을 값일 수 있습니다. 지정 된 대상 별표를 포함 하는 경우 (\*) 또는 물음표 (?)를 와일드 카드 문자로 처리 됩니다만 일치 하는 대상 경로 인쇄 하거나 삭제 합니다. 별표는 문자열에 대응 하 고 물음표는 임의의 단일 문자와 일치 합니다. 예를 들어 10.\*합니다. 1, 192.168.\*, 127.\*, 및 \*224\* 별표 와일드 카드의 유효한 모든 용도 합니다.  
-   대상과 서브넷 마스크 (netmask) 값의 조합이 잘못 사용 하 여 표시 하는 "경로: 잘못 된 게이트웨이 주소 네트워크 마스크" 오류 메시지입니다. 이 오류 메시지가 대상 하나를 포함 하거나 더 많은 비트가 1로 설정 된 해당 서브넷 마스크 비트를 0으로 설정 되어 있는 비트 위치에 나타납니다. 이 문제를 테스트 하려면 이진 표기법을 사용 하 여 대상 및 서브넷 마스크를 표현 합니다. 일련의 대상의 네트워크 주소 할당 및 일련의 대상의 호스트 부분을 나타내는 0 비트를 나타내는 1 비트, 이진 표기법의 서브넷 마스크 구성 됩니다. 대상에 있는 호스트 주소 (서브넷 마스크에 의해 정의 됨) 처럼 대상의 부분에 1로 설정 된 비트가 있는지 확인 하십시오.  
-   합니다 **/p** Windows NT 4.0, Windows 2000, Windows Millennium edition, Windows XP 및 Windows Server 2003에 대 한 경로 명령에 매개 변수는만 지원 합니다. 이 매개 변수에서 지원 하지 않는 **경로** Windows 95 또는 Windows 98에 대 한 도움말입니다.  
-   이 명령은 네트워크 연결에서 네트워크 어댑터의 속성에 구성 요소로 인터넷 프로토콜 (TCP/IP) 프로토콜을 설치 하는 경우에 사용할 수입니다.  

## <a name="BKMK_Examples"></a>예제  
IP 라우팅 테이블의 전체 내용의 표시 하려면 다음을 입력 합니다.  
```  
route print  
```  
경로 10으로 시작 하는 IP 라우팅 테이블에 표시 하려면 다음을 입력 합니다.  
```  
route print 10.*  
```  
192.168.12.1 기본 게이트웨이 주소를 가진 기본 경로 추가 하려면 다음을 입력 합니다.  
```  
route add 0.0.0.0 mask 0.0.0.0 192.168.12.1  
```  
서브넷 마스크는 255.255.0.0과 10.27.0.1 다음 홉 주소를 사용 하 여 대상 10.41.0.0에 경로 추가 하려면 다음을 입력 합니다.  
```  
route add 10.41.0.0 mask 255.255.0.0 10.27.0.1  
```  
서브넷 마스크는 255.255.0.0과 10.27.0.1 다음 홉 주소를 사용 하 여 대상 10.41.0.0에 영구 경로 추가 하려면 다음을 입력 합니다.  
```  
route /p add 10.41.0.0 mask 255.255.0.0 10.27.0.1  
```  
서브넷 마스크는 255.255.0.0: 10.27.0.1 다음 홉 주소 및 7의 비용 메트릭 대상 10.41.0.0에 경로 추가 하려면 다음을 입력 합니다.  
```  
route add 10.41.0.0 mask 255.255.0.0 10.27.0.1 metric 7  
```  
서브넷 마스크는 255.255.0.0 대상 10.41.0.0에 경로 추가 하려면 10.27.0.1, 및 0x3 인터페이스 인덱스를 사용 하 여 다음 홉 주소를 입력 합니다.  
```  
route add 10.41.0.0 mask 255.255.0.0 10.27.0.1 if 0x3  
```  
서브넷 마스크는 255.255.0.0 10.41.0.0 대상에 대 한 경로 삭제 하려면 다음을 입력 합니다.  
```  
route delete 10.41.0.0 mask 255.255.0.0  
```  
모든 경로 IP 라우팅 테이블에서 시작 하는 10을 삭제 하려면 다음을 입력 합니다.  
```  
route delete 10.*  
```  
대상이 10.41.0.0와 서브넷 마스크는 255.255.0.0 경로의 다음 홉 주소를 10.27.0.1에서 10.27.0.25를 변경 하려면 다음을 입력 합니다.  
```  
route change 10.41.0.0 mask 255.255.0.0 10.27.0.25  
```  

## <a name="additional-references"></a>추가 참조  
-   [명령줄 구문 키](command-line-syntax-key.md)  