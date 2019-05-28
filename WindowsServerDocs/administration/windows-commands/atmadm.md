---
title: atmadm
description: Windows 명령 항목에 대 한 **atmadm** -모니터 연결 및 atM에서 등록 된 주소 비동기 전송 모드 (atM) 네트워크에서 관리자를 호출 합니다.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37156c2e-c4d4-4fd8-a03d-245fb60bf996
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3a8a8883bad9aa2abdc90d5db5702ef42f46c8a8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831774"
---
# <a name="atmadm"></a>atmadm

>적용 대상: Windows Server (반기 채널), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

모니터 연결 및 atM에서 등록 된 주소에서 비동기 전송 모드 (atM) 네트워크 관리자를 호출 합니다. 사용할 수 있습니다 **atmadm** atM 어댑터에서 들어오고 나가는 호출에 대 한 통계를 표시 합니다. 매개 변수 없이 사용 **atmadm** 활성 atM 연결의 상태를 모니터링 하는 것에 대 한 통계를 표시 합니다. 

## <a name="syntax"></a>구문

```
atmadm [/c][/a][/s]
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-------|--------|
|/c|이 컴퓨터에 설치 하는 atM 네트워크 어댑터에 모든 현재 연결에 대 한 호출 정보를 표시 합니다.|
|/ a|등록 된 atM 네트워크 서비스 액세스 포인트이 컴퓨터에 설치 된 각 어댑터에 대 한 (NSAP) 주소를 표시 합니다.|
|/s|활성 atM 연결의 상태를 모니터링 하는 것에 대 한 통계를 표시 합니다.|
|/?|명령 프롬프트에 도움말을 표시합니다.|

## <a name="remarks"></a>설명

- **atmadm /c** 명령은 다음과 유사한 출력을 생성 합니다.

    ```
    Windows atM call Manager Statistics
    atM Connections on Interface : [009] Olicom atM PCI 155 Adapter
       Connection   VPI/VCI   remote address/
                              Media Parameters (rates in bytes/sec)
       In  PMP SVC    0/193   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 0,Avg 0,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       Out P-P SVC    0/192   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       In  PMP SVC    0/191   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 0,Avg 0,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       Out P-P SVC    0/190   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       In  P-P SVC    0/475   47000580FFE1000000F21A2E180000C110081501
                              Tx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9188
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 9188
       Out PMP SVC    0/194   47000580FFE1000000F21A2E180000C110081501 (0)
                              Tx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9180
                              Rx:UBR,Peak 0,Avg 0,MaxSdu 0
       Out P-P SVC    0/474   4700918100000000613E5BFE010000C110081500
                              Tx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9188
                              Rx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9188
       In  PMP SVC    0/195   47000580FFE1000000F21A2E180000C110081500
                              Tx:UBR,Peak 0,Avg 0,MaxSdu 0
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 9180
    ```
    
    다음 표에서 각 요소에 대 한 설명은 **atmadm /c** 샘플 출력입니다.
    
    |데이터 형식|화면 표시|설명|
    |--------|---------|--------|
    |연결 정보|입/출력|호출의 방향입니다.  **** 다른 장치에서 atM 네트워크 어댑터 하는 것입니다.  **Out** 다른 장치는 atM 네트워크 어댑터에서입니다.|
    ||PMP|지점 호출입니다.|
    ||P-P|지점 간 호출입니다.|
    ||SVC|전환된 된 가상 회로에 연결 되어 있습니다.|
    ||PVC|영구 가상 회로에 연결 되어 있습니다.|
    |VPI/VCI 정보|VPI/VCI|가상 경로 및 들어오거나 나가는 호출의 가상 채널입니다.|
    |원격 주소/미디어 매개 변수|47000580FFE1000000F21A2E180000C110081500|호출 NSAP 주소 **(In)** 또는 호출 **(축소)** atM 장치입니다.|
    ||**Tx**|**Tx** 매개 변수는 다음 세 가지 요소를 포함 합니다.<br /><br />-기본 또는 지정 된 비트 전송률 형식 (UBR, CBR, VBR, 또는 ABR)<br />-기본 또는 회선 속도 지정 합니다.<br />-지정 된 서비스 데이터 (SDU) 단위 크기|
    ||**Rx**|**Rx** 매개 변수는 다음 세 가지 요소를 포함 합니다.<br /><br />-기본 또는 지정 된 비트 전송률 형식 (UBR, CBR, VBR, 또는 ABR)<br />-기본 또는 회선 속도 지정 합니다.<br />-지정 된 SDU 크기|
    
- **atmadm/a** 명령은 다음과 유사한 출력을 생성 합니다.

    ```
    Windows atM call Manager Statistics
    atM addresses for Interface : [009] Olicom atM PCI 155 Adapter
    47000580FFE1000000F21A2E180000C110081500
    ```
    
- **atmadm /s** 명령은 다음과 유사한 출력을 생성 합니다.

    ```
    Windows atM call Manager Statistics
    atM call Manager statistics for Interface : [009] Olicom atM PCI 155 Adapter
    Current active calls                        = 4
    Total successful Incoming calls             = 1332
    Total successful Outgoing calls             = 1297
    Unsuccessful Incoming calls                 = 1
    Unsuccessful Outgoing calls                 = 1
    calls Closed by remote                      = 1302
    calls Closed Locally                        = 1323
    Signaling and ILMI Packets Sent            = 33655
    Signaling and ILMI Packets Received        = 34989
    ```
    
    다음 표에서 각 요소에 대 한 설명은 **atmadm /s** 샘플 출력입니다.
    
    |호출 관리자 통계|설명|
    |-------------|--------|
    |현재 활성 호출|이 컴퓨터에 설치 되어 있는 atM 어댑터에서 현재 활성를 호출 합니다.|
    |성공한 총 들어오는 호출|호출은 현재 atM 네트워크의 다른 장치에서 성공적으로 수신 합니다.|
    |성공한 총 나가는 호출|이 컴퓨터에서이 네트워크에서 다른 atM 장치에 성공적으로 완료를 호출 합니다.|
    |들어오는 호출 실패|이 컴퓨터에 연결에 실패 한 들어오는 호출 합니다.|
    |나가는 호출 실패|네트워크에서 다른 장치에 연결에 실패 한 나가는 호출 합니다.|
    |원격 호출 닫힘|네트워크에서 원격 장치에서 종료를 호출 합니다.|
    |닫힌 로컬로 호출|이 컴퓨터에서 종료를 호출 합니다.|
    |신호 및 ILMI 패킷 전송|통합된 로컬 관리 인터페이스 (ILMI) 보낸 패킷 수 스위치에 연결을 시도 하는이 컴퓨터입니다.|
    |신호 및 ILMI 패킷 받음|AtM 스위치에서 받은 ILMI 패킷 수입니다.|
    
## <a name="BKMK_Examples"></a>예제

이 컴퓨터에 설치 하는 atM 네트워크 어댑터에 모든 현재 연결에 대 한 호출 정보를 표시 하려면 다음을 입력 합니다.

```
atmadm /c
```

이 컴퓨터에 설치 된 각 어댑터에 대해 등록 된 atM 네트워크 서비스 액세스 지점 (NSAP) 주소를 표시 하려면 다음을 입력 합니다.

```
atmadm /a
```

활성 atM 연결의 상태를 모니터링 하는 것에 대 한 통계를 표시 하려면 다음을 입력 합니다.

```
atmadm /s
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)