---
title: 인터페이스 포트 프록시에 대한 Netsh 명령
description: Netsh 인터페이스 포트 프록시 명령을 사용하여 IPv4 및 IPv6 네트워크와 애플리케이션 간의 프록시로 작동합니다.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
manager: dougkim
ms.author: lizross
author: eross-msft
ms.date: 08/30/2018
ms.openlocfilehash: e9c4cff4d1424c244857cf75be41d445b299f1f2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853746"
---
# <a name="netsh-interface-portproxy-commands"></a>Netsh 인터페이스 포트 프록시 명령

**Netsh 인터페이스 포트 프록시** 명령을 사용하여 IPv4 및 IPv6 네트워크와 애플리케이션 간의 프록시로 작동합니다. 이러한 명령을 사용하여 다음과 같은 방법으로 프록시 서비스를 설정할 수 있습니다.

-   IPv4로 구성된 컴퓨터 및 애플리케이션 메시지가 다른 IPv4 구성 컴퓨터 및 애플리케이션으로 전송되었습니다.

-   IPv4로 구성된 컴퓨터 및 애플리케이션 메시지가 다른 IPv6 구성 컴퓨터 및 애플리케이션으로 전송되었습니다.

-   IPv6으로 구성된 컴퓨터 및 애플리케이션 메시지가 다른 IPv4 구성 컴퓨터 및 애플리케이션으로 전송되었습니다.

-   IPv6으로 구성된 컴퓨터 및 애플리케이션 메시지가 다른 IPv6 구성 컴퓨터 및 애플리케이션으로 전송되었습니다.

이러한 명령을 사용하여 배치 파일 또는 스크립트를 작성할 때 각 명령은 **netsh interface portproxy**로 시작해야 합니다. 예를 들어, 포트 프록시 서버가 IPv4 포트 및 주소를 서버가 수신하는 IPv4 주소 목록에서 삭제하도록 지정하기 위해 **delete v4tov6** 명령을 사용하는 경우 배치 파일 또는 스크립트는 다음 구문을 사용해야 합니다.

```PowerShell
netsh interface portproxy delete v4tov6listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address| HostName}] [[protocol=]tcp]
```

사용할 수 있는 Netsh 인터페이스 포트 프록시 명령은 다음과 같습니다.

-   [add v4tov4](#add-v4tov4)

-   [add v4tov6](#add-v4tov6)

-   [add v6tov4](#add-v6tov4)

-   [add v6tov6](#add-v6tov6)

-   [delete v4tov4](#delete-v4tov4)

-   [delete v4tov6](#delete-v4tov6)

-   [delete v6tov6](#delete-v6tov6)

-   [reset](#reset)

-   [set v4tov4](#set-v4tov4)

-   [set v4tov6](#set-v4tov6)

-   [setv6tov4](#set-v6tov4)

-   [set v6tov6](#set-v6tov6)

-   [show all](#show-all)

-   [show v4tov4](#show-v4tov4)

-   [show v4tov6](#show-v4tov6)

-   [show v6tov4](#show-v6tov4)

-   [show v6tov6](#show-v6tov6)


## <a name="add-v4tov4"></a>add v4tov4

포트 프록시 서버는 특정 포트와 IPv4 주소로 전송된 메시지를 수신 대기하고 포트 및 IPv4 주소를 매핑하여 별도의 TCP 연결을 설정한 후 받은 메시지를 보냅니다.

### <a name="syntax"></a>구문

```PowerShell
add v4tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName}] [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName}] [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수


|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="add-v4tov6"></a>add v4tov6

포트 프록시 서버는 특정 포트와 IPv4 주소로 전송된 메시지를 수신 대기하고 포트 및 IPv6 주소를 매핑하여 별도의 TCP 연결을 설정한 후 받은 메시지를 보냅니다.

### <a name="syntax"></a>구문

```PowerShell
add v4tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다.  |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="add-v6tov4"></a>add v6tov4

포트 프록시 서버는 특정 포트와 IPv6 주소로 전송된 메시지를 수신 대기하고 포트 및 IPv4 주소를 매핑하여 별도의 TCP 연결을 설정한 후 받은 메시지를 보냅니다.

### <a name="syntax"></a>구문

```PowerShell
add v6tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다.  |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="add-v6tov6"></a>add v6tov6

포트 프록시 서버는 특정 포트와 IPv6 주소로 전송된 메시지를 수신 대기하고 포트 및 IPv6 주소를 매핑하여 별도의 TCP 연결을 설정한 후 받은 메시지를 보냅니다.

### <a name="syntax"></a>구문

```PowerShell
add v6tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다.  |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="delete-v4tov4"></a>delete v4tov4

포트 프록시 서버는 서버에서 수신 대기하는 IPv4 포트 및 주소 목록에서 IPv4 주소를 삭제합니다.

### <a name="syntax"></a>구문

```PowerShell
delete v4tov4 listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    삭제할 IPv4 포트를 지정합니다.                                    |
| **listenaddress** | 삭제할 IPv4 주소를 지정합니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|   **protocol**    |                                      사용할 프로토콜을 지정합니다.                                      |

## <a name="delete-v4tov6"></a>delete v4tov6

포트 프록시 서버는 서버에서 수신 대기하는 IPv4 주소 목록에서 IPv4 포트 및 주소를 삭제합니다.

### <a name="syntax"></a>구문

```PowerShell 
delete v4tov6 listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    삭제할 IPv4 포트를 지정합니다.                                    |
| **listenaddress** | 삭제할 IPv4 주소를 지정합니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|   **protocol**    |                                      사용할 프로토콜을 지정합니다.                                      |

## <a name="delete-v6tov4"></a>delete v6tov4

포트 프록시 서버는 서버에서 수신 대기하는 IPv6 주소 목록에서 IPv6 포트 및 주소를 삭제합니다.

### <a name="syntax"></a>구문

```PowerShell
delete v6tov4 listenport= {Integer | ServiceName} [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    삭제할 IPv6 포트를 지정합니다.                                    |
| **listenaddress** | 삭제할 IPv6 주소를 지정합니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|   **protocol**    |                                      사용할 프로토콜을 지정합니다.                                      |

## <a name="delete-v6tov6"></a>delete v6tov6

포트 프록시 서버는 서버에서 수신 대기하는 IPv6 주소 목록에서 IPv6 주소를 삭제합니다.

### <a name="syntax"></a>구문

```PowerShell
delete v6tov6 listenport= {Integer | ServiceName} [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    삭제할 IPv6 포트를 지정합니다.                                    |
| **listenaddress** | 삭제할 IPv6 주소를 지정합니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|   **protocol**    |                                      사용할 프로토콜을 지정합니다.                                      |

## <a name="reset"></a>reset

IPv6 구성 상태를 다시 설정합니다.

### <a name="syntax"></a>구문

`reset`

## <a name="set-v4tov4"></a>set v4tov4

**add v4tov4** 명령을 사용하여 만든 포트 프록시 서버에서 기존 항목의 매개 변수 값을 수정하거나 포트/주소 쌍을 매핑하는 목록에 새 항목을 추가합니다.

### <a name="syntax"></a>구문

```PowerShell
set v4tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="set-v4tov6"></a>set v4tov6

**add v4tov6** 명령을 사용하여 만든 포트 프록시 서버에서 기존 항목의 매개 변수 값을 수정하거나 포트/주소 쌍을 매핑하는 목록에 새 항목을 추가합니다.

### <a name="syntax"></a>구문

```PowerShell
set v4tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다.  |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="set-v6tov4"></a>set v6tov4

**add v6tov4** 명령을 사용하여 만든 포트 프록시 서버에서 기존 항목의 매개 변수 값을 수정하거나 포트/주소 쌍을 매핑하는 목록에 새 항목을 추가합니다.

### <a name="syntax"></a>구문

```PowerShell
set v6tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           수신 대기할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv4 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|  **connectport**   |       연결할 IPv4 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다.  |
|    **protocol**    |                                                                                  사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="set-v6tov6"></a>set v6tov6

**add v6tov6** 명령을 사용하여 만든 포트 프록시 서버에서 기존 항목의 매개 변수 값을 수정하거나 포트/주소 쌍을 매핑하는 목록에 새 항목을 추가합니다.

### <a name="syntax"></a>구문

```PowerShell 
set v6tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>매개 변수

|                    |                                                                                                                                                                                                    |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                            수신 대기할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다.                                                            |
| **connectaddress** | 연결할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소가 지정되지 않은 경우 기본값은 로컬 컴퓨터입니다.  |
|  **connectport**   |        연결할 IPv6 포트(포트 번호 또는 서비스 이름)를 지정합니다. **connectport**가 지정되지 않은 경우 기본값은 로컬 컴퓨터의 **listenport** 값입니다.        |
| **listenaddress**  | 수신 대기할 IPv6 주소를 지정합니다. 허용되는 값은 IP 주소, 컴퓨터 NetBIOS 이름 또는 컴퓨터 DNS 이름입니다. 주소를 지정하지 않은 경우 기본값은 로컬 컴퓨터입니다. |
|    **protocol**    |                                                                                   사용할 프로토콜을 지정합니다.                                                                                   |

## <a name="show-all"></a>모두 표시

v4tov4, v4tov6, v6tov4 및 v6tov6에 대한 포트/주소 쌍을 포함한 모든 포트 프록시 매개 변수를 표시합니다.

### <a name="syntax"></a>구문

`show all`


## <a name="show-v4tov4"></a>show v4tov4

v4tov4 포트 프록시 매개 변수를 표시합니다.

### <a name="syntax"></a>구문

`show v4tov4`

## <a name="show-v4tov6"></a>show v4tov6

v4tov6 포트 프록시 매개 변수를 표시합니다.

### <a name="syntax"></a>구문

`show v4tov6`

## <a name="show-v6tov4"></a>show v6tov4

v6tov4 포트 프록시 매개 변수를 표시합니다.

### <a name="syntax"></a>구문

`show v6tov4`


## <a name="show-v6tov6"></a>show v6tov6

v6tov6 포트 프록시 매개 변수를 표시합니다.

### <a name="syntax"></a>구문

`show v6tov6`

---
