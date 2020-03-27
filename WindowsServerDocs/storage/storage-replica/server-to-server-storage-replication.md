---
title: 서버 간 저장소 복제
description: Windows 관리 센터 및 PowerShell을 포함 하 여 Windows Server에서 서버 간 복제를 위해 저장소 복제본을 설정 하 고 사용 하는 방법입니다.
ms.prod: windows-server
manager: siroy
ms.author: nedpyle
ms.technology: storage-replica
ms.topic: get-started-article
author: nedpyle
ms.date: 03/26/2020
ms.assetid: 61881b52-ee6a-4c8e-85d3-702ab8a2bd8c
ms.openlocfilehash: 9873378d62ccc7b53dcc6fc629651df2aa1c6708
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80308114"
---
# <a name="server-to-server-storage-replication-with-storage-replica"></a>저장소 복제본을 사용 하 여 서버 간 저장소 복제

> 적용 대상: Windows Server 2019, Windows Server 2016, Windows Server(반기 채널)

저장소 복제본을 사용하여 두 서버에서 데이터가 동기화되도록 구성할 수 있으며 따라서 각각 동일한 볼륨의 동일한 복사본을 포함합니다. 이 항목에서는 이 서버 간 복제 구성에 관한 배경 정보와 환경을 설정 및 관리하는 방법을 제공합니다.

저장소 복제본을 관리 하려면 [Windows 관리 센터](../../manage/windows-admin-center/overview.md) 또는 PowerShell을 사용할 수 있습니다.

Windows 관리 센터에서 저장소 복제본을 사용 하는 개요 비디오는 다음과 같습니다.
> [!video https://www.microsoft.com/videoplayer/embed/3aa09fd4-867b-45e9-953e-064008468c4b?autoplay=false]


## <a name="prerequisites"></a>필수 조건  

* Active Directory Domain Services 포리스트 (Windows Server 2016를 실행할 필요가 없음)  
* Windows Server 2019 또는 Windows Server 2016, Datacenter Edition을 실행 하는 두 대의 서버 Windows Server 2019를 실행 하는 경우 최대 2tb 크기의 단일 볼륨만 복제 하는 경우 Standard Edition을 대신 사용할 수 있습니다.  
* SAS JBOD, 파이버 채널 SAN, iSCSI 대상 또는 로컬 SCSI/SATA 저장소를 사용하는 저장소 집합 2개 저장소에는 HDD 및 SSD 미디어가 혼합되어 있어야 합니다. 각 저장소 집합은 각 서버에만 사용할 수 있으며 공유 액세스는 없습니다.  
* 각 저장소 집합에서 복제된 데이터용과 로그용으로 둘 이상의 가상 디스크를 만들 수 있어야 합니다. 실제 저장소의 섹터 크기는 모든 데이터 디스크의 섹터 크기와 동일해야 합니다. 실제 저장소의 섹터 크기는 모든 로그 디스크의 섹터 크기와 동일해야 합니다.  
* 각 서버에 하나 이상의 동기 복제용 이더넷/TCP 연결(RDMA 권장)   
* 모든 노드 간에 ICMP, SMB(포트 445 및 SMB 다이렉트용 5445) 및 WS-MAN(포트 5985) 양방향 트래픽을 허용하는 적절한 방화벽 및 라우터 규칙  
* 동기 복제를 위해 IO 쓰기 워크로드가 포함된 충분한 대역폭 및 평균 5ms 왕복 대기 시간을 지원하는 서버 간의 네트워크. 비동기 복제에는 대기 시간 권장 구성이 없습니다.<br>
온-프레미스 서버와 Azure Vm 간에 복제 하는 경우 온-프레미스 서버와 Azure Vm 간에 네트워크 링크를 만들어야 합니다. 이렇게 하려면 [Express 경로](#add-azure-vm-expressroute), [사이트 간 vpn 게이트웨이 연결](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)을 사용 하거나 Azure vm에서 VPN 소프트웨어를 설치 하 여 온-프레미스 네트워크에 연결 합니다.
* 복제된 저장소는 Windows 운영 체제 폴더가 포함된 드라이브에 있을 수 없습니다.

> [!IMPORTANT]
>  이 시나리오에서는 각 서버가 서로 다른 물리적 또는 논리적 사이트에 있습니다. 각 서버는 네트워크를 통해 서로 통신할 수 있어야 합니다.  


이러한 요구 사항은 대부분 `Test-SRTopology cmdlet`을 사용하여 확인할 수 있습니다. 하나 이상의 서버에 저장소 복제본 또는 저장소 복제 관리 도구 기능을 설치한 경우 이 도구에 액세스할 수 있습니다. 이 도구를 사용하기 위해 저장소 복제본을 구성할 필요는 없으며 cmdlet을 설치하기만 하면 됩니다. 자세한 내용은 아래 단계에 포함되어 있습니다.  

## <a name="windows-admin-center-requirements"></a>Windows 관리 센터 요구 사항

저장소 복제본과 Windows 관리 센터를 함께 사용 하려면 다음이 필요 합니다.

| System                        | 운영 체제                                            | 소프트웨어가 사용되는 구성 요소     |
|-------------------------------|-------------------------------------------------------------|------------------|
| 서버 2대 <br>(Azure Vm을 포함 한 온-프레미스 하드웨어, Vm 및 클라우드 Vm의 모든 혼합)| Windows Server 2019, Windows Server 2016 또는 Windows Server (반기 채널) | 저장소 복제본  |
| 단일 PC                     | Windows 10                                                  | Windows Admin Center |

> [!NOTE]
> 지금은 서버에서 Windows 관리 센터를 사용 하 여 저장소 복제본을 관리할 수 없습니다.

## <a name="terms"></a>용어  
이 연습에서는 다음 환경을 예로 사용합니다.  

-   이름이 **SR-SRV05**와 **SR-SRV06**인 서버 2개  

-   각각 **Redmond**와 **Bellevue**라는 두 개의 데이터 센터를 나타내는 논리적 “사이트" 쌍  

![빌딩 5의 서버가 빌딩 9의 서버와 복제되는 모습을 보여 주는 다이어그램](media/Server-to-Server-Storage-Replication/Storage_SR_ServertoServer.png)  

**그림 1: 서버 간 복제**  

## <a name="step-1-install-and-configure-windows-admin-center-on-your-pc"></a>1 단계: PC에서 Windows 관리 센터 설치 및 구성

Windows 관리 센터를 사용 하 여 저장소 복제본을 관리 하는 경우 다음 단계를 사용 하 여 저장소 복제본을 관리 하기 위한 PC를 준비 합니다.
1. [Windows 관리 센터](../../manage/windows-admin-center/overview.md)를 다운로드 하 여 설치 합니다.
2. [원격 서버 관리 도구](https://www.microsoft.com/download/details.aspx?id=45520)를 다운로드 하 여 설치 합니다.
    - Windows 10 버전 1809 이상을 사용 하는 경우 주문형 기능에서 "RSAT: Storage Replica Module for Windows PowerShell"을 설치 합니다.
3. **시작** 단추를 선택 하 고 **powershell**을 입력 한 다음 **Windows powershell** 을 마우스 오른쪽 단추로 클릭 하 고 **관리자 권한으로 실행**을 선택 하 여 관리자 권한으로 powershell 세션을 엽니다.
4. 다음 명령을 입력 하 여 로컬 컴퓨터에서 WS 관리 프로토콜을 사용 하도록 설정 하 고 클라이언트에서 원격 관리를 위한 기본 구성을 설정 합니다.

    ```PowerShell
    winrm quickconfig
    ```

5. WinRM 서비스를 사용 하도록 설정 하 고 WinRM 방화벽 예외를 사용 하도록 설정 하려면 **Y** 를 입력 합니다.

## <a name="step-2-provision-operating-system-features-roles-storage-and-network"></a><a name="provision-os"></a>2 단계: 운영 체제, 기능, 역할, 저장소 및 네트워크 프로 비전

1.  Windows server 설치 유형 **(데스크톱 환경)** 을 사용 하 여 두 서버 노드 모두에 windows server를 설치 합니다. 
 
    Express 경로를 통해 네트워크에 연결 된 Azure VM을 사용 하려면 Express 경로를 [통해 네트워크에 연결 된 AZURE Vm 추가](#add-azure-vm-expressroute)를 참조 하세요.
    
    > [!NOTE]
    > Windows 관리 센터 버전 1910부터 Azure에서 자동으로 대상 서버를 구성할 수 있습니다. 이 옵션을 선택 하는 경우 원본 서버에 Windows Server를 설치한 다음 [3 단계: 서버 간 복제 설정](#step-3-set-up-server-to-server-replication)으로 건너뜁니다. 

3.  네트워크 정보를 추가 하 고, Windows 10 관리 PC와 동일한 도메인에 서버를 가입한 다음 (사용 중인 경우) 서버를 다시 시작 합니다.  

    > [!NOTE]
    > 이 시점부터는 항상 모든 서버에서 기본 제공 관리자 그룹의 구성원인 도메인 사용자로 로그온합니다. 그래픽 서버 설치 또는 Windows 10 컴퓨터에서 실행할 때는 항상 PowerShell 및 명령줄 프롬프트를 관리자 권한으로 사용해야 합니다.  

3.  첫 번째 JBOD 저장소 엔클로저, iSCSI 대상, FC SAN 또는 DAS (로컬 고정 디스크) 저장소 집합을 **Redmond**사이트의 서버에 연결 합니다.  

4.  두 번째 저장소 집합을 사이트 **Bellevue**의 서버에 연결 합니다.  

5.  필요에 따라 두 노드 모두에 최신 공급업체 저장소와 엔클로저 펌웨어 및 드라이버, 최신 공급업체 HBA 드라이버, 최신 공급업체 BIOS/UEFI 펌웨어, 최신 공급업체 네트워크 드라이버 및 최신 마더보드 칩셋 드라이버를 설치합니다. 필요에 따라 노드를 다시 시작합니다.  

    > [!NOTE]
    > 공유 저장소 및 네트워킹 하드웨어 구성은 하드웨어 공급업체 설명서를 참조하세요.  

6.  서버의 BIOS/UEFI 설정이 고성능을 지원하는지 확인합니다(예: C-상태 사용 안 함, QPI 속도 설정, NUMA 사용, 가장 높은 메모리 주파수 설정 등). Windows Server의 전원 관리가 고성능으로 설정 되어 있는지 확인 합니다. 필요에 따라 다시 시작합니다.  

7.  다음과 같이 역할을 구성합니다.  

    -   **Windows 관리 센터 메서드**
        1. Windows 관리 센터에서 서버 관리자으로 이동한 후 서버 중 하나를 선택 합니다.
        2. **역할 & 기능**으로 이동 합니다.
        3. **저장소 복제본** > **기능** 을 선택 하 고 **설치**를 클릭 합니다.
        4. 다른 서버에서 반복 합니다.
    -   **서버 관리자 메서드**  

        1.  **ServerManager.exe**를 실행하고 모든 서버 노드를 추가하여 서버 그룹을 만듭니다.  

        2.  각 노드에 **파일 서버** 및 **저장소 복제본** 역할과 기능을 설치하고 다시 시작합니다.  

    -   **Windows PowerShell 방법**  

        SR SRV06 또는 원격 관리 컴퓨터의 Windows PowerShell 콘솔에서 다음 명령을 실행하여 필요한 기능 및 역할을 설치하고 다시 시작합니다.  

        ```powershell  
        $Servers = 'SR-SRV05','SR-SRV06'  

        $Servers | ForEach { Install-WindowsFeature -ComputerName $_ -Name Storage-Replica,FS-FileServer -IncludeManagementTools -restart }  
        ```  

        이러한 단계에 대한 자세한 내용은 [역할, 역할 서비스 또는 기능 설치 또는 제거](../../administration/server-manager/install-or-uninstall-roles-role-services-or-features.md)를 참조하세요.  

8.  다음과 같이 저장소를 구성합니다.  

    > [!IMPORTANT]  
    > -   각 엔클로저에 두 개의 볼륨(데이터용 볼륨과 로그용 볼륨)을 만들어야 합니다.  
    > -   로그 및 데이터 디스크는 MBR이 아니라 GPT로 초기화되어야 합니다.  
    > -   두 개의 데이터 볼륨이 동일한 크기여야 합니다.  
    > -   두 개의 로그 볼륨이 동일한 크기여야 합니다.  
    > -   복제된 데이터 디스크의 섹터 크기가 모두 동일해야 합니다.  
    > -   로그 디스크의 섹터 크기가 모두 동일해야 합니다.  
    > -   로그 볼륨에서 SSD와 같은 플래시 기반 저장소를 사용해야 합니다. 로그 저장소는 데이터 저장소보다 더 빠른 것이 좋습니다. 로그 볼륨은 절대 다른 워크로드에 사용해서는 안 됩니다.
    > -   데이터 디스크에서는 HDD, SSD 또는 계층형 조합을 사용할 수 있으며, 미러링된 공간이나 패리티 공간 또는 RAID 1 또는 10, RAID 5 또는 RAID 50을 사용할 수 있습니다.  
    > -   로그 볼륨은 기본적으로 9GB 이상이어야 하며, 로그 요구 사항에 따라 더 크거나 작아야 할 수도 있습니다.  
    > -   파일 서버 역할은 테스트에 필요한 방화벽 포트를 여는 Test-SRTopology를 작동하는 데에만 필요합니다.
    
    - **JBOD 인클로저:**  

        1.  각 서버에서 해당 사이트의 저장소 엔클로저만 볼 수 있는지, 그리고 SAS 연결이 제대로 구성되어 있는지 확인합니다.  

        2.  Windows PowerShell 또는 서버 관리자를 **사용하여 독립 실행형 서버에서 저장소 공간 배포에** 제공된 [1~3단계에](../storage-spaces/deploy-standalone-storage-spaces.md) 따라 저장소 공간을 사용하는 저장소를 프로비전합니다.  

    - **ISCSI 저장소:**  

        1.  각 클러스터에서 해당 사이트의 저장소 엔클로저만 볼 수 있는지 확인합니다. iSCSI를 사용하는 경우 둘 이상의 단일 네트워크 어댑터를 사용해야 합니다.    

        2.  공급업체 설명서를 사용하여 저장소를 프로비전합니다. Windows 기반 iSCSI 대상을 사용하는 경우 [iSCSI 대상 블록 저장소, 방법](../iscsi/iscsi-target-server.md)을 참조하세요.  

    - **FC SAN 저장소의 경우:**  

        1.  각 서버에서 해당 사이트의 저장소 엔클로저만 볼 수 있는지, 그리고 호스트의 영역을 제대로 설정했는지 확인합니다.   

        2.  공급업체 설명서를 사용하여 저장소를 프로비전합니다.  

    - **로컬 고정 디스크 저장소의 경우:**  

        -   저장소에 시스템 볼륨, 페이지 파일 또는 덤프 파일이 포함 되어 있지 않은지 확인 합니다.  

        -   공급업체 설명서를 사용하여 저장소를 프로비전합니다.  

9. Windows PowerShell을 시작하고 **Test-SRTopology** cmdlet을 사용하여 모든 저장소 복제본 요구 사항을 충족하는지 확인합니다. 장기 실행 성능 평가 모드뿐만 아니라 빠른 테스트를 위해 요구 사항 전용 모드에서 cmdlet을 사용할 수 있습니다.  

    예를 들어 각각 **F:** 및 **G:** 볼륨이 있는 제안된 노드의 유효성을 검사하고 30분 동안 테스트를 실행하려면 다음을 실행합니다.  
        
    ```PowerShell
    MD c:\temp  

    Test-SRTopology -SourceComputerName SR-SRV05 -SourceVolumeName f: -SourceLogVolumeName g: -DestinationComputerName SR-SRV06 -DestinationVolumeName f: -DestinationLogVolumeName g: -DurationInMinutes 30 -ResultPath c:\temp  
    ```

    > [!IMPORTANT]
      > 평가 기간 동안 지정된 원본 볼륨에 쓰기 IO 로드가 없는 테스트 서버를 사용하는 경우 워크로드를 추가하는 것이 좋습니다. 그렇지 않으면 유용한 보고서가 생성되지 않습니다. 실제 숫자와 권장 로그 크기를 확인하기 위해 프로덕션과 유사한 워크로드로 테스트해야 합니다. 또는 테스트하거나 다운로드하는 동안 일부 파일을 원본 볼륨에 복사하고 [DISKSPD](https://gallery.technet.microsoft.com/DiskSpd-a-robust-storage-6cd2f223)를 실행하여 쓰기 IO를 생성합니다. 예를 들어 쓰기 IO 워크로드가 낮은 샘플로 D: 볼륨을 10분 동안 테스트하려면 다음을 실행합니다.  
      >
      > `Diskspd.exe -c1g -d600 -W5 -C5 -b8k -t2 -o2 -r -w5 -i100 -j100 d:\test` 

10. 그림 2에 표시 된 **TestSrTopologyReport** 보고서를 검토 하 여 저장소 복제본 요구 사항을 충족 하는지 확인 합니다.  

    ![토폴로지 보고서를 보여 주는 화면](media/Server-to-Server-Storage-Replication/SRTestSRTopologyReport.png)

    **그림 2: 저장소 복제 토폴로지 보고서**

## <a name="step-3-set-up-server-to-server-replication"></a>3 단계: 서버 간 복제 설정
### <a name="using-windows-admin-center"></a>Windows 관리 센터 사용

1. 원본 서버를 추가 합니다.
    1. **추가** 단추를 선택 합니다.
    2. **서버 연결 추가**를 선택 합니다.
    3. 서버 이름을 입력 한 다음 **제출**을 선택 합니다.
2. **모든 연결** 페이지에서 원본 서버를 선택 합니다.
3. 도구 패널에서 **저장소 복제본** 을 선택 합니다.
4. 새로 **만들기를 선택 하** 여 새 파트너 관계를 만듭니다. 파트너 관계의 대상으로 사용할 새 Azure VM을 만들려면 다음을 수행 합니다.
   
    1. **다른 서버를 사용 하 여 복제** 에서 **새 Azure VM 사용** 을 선택 하 고 **다음**을 선택 합니다. 이 옵션이 표시 되지 않으면 Windows 관리 센터 버전 1910 이상 버전을 사용 하 고 있는지 확인 합니다.
    2. 원본 서버 정보 및 복제 그룹 이름을 지정 하 고 **다음**을 선택 합니다.<br><br>그러면 Windows Server 2019 또는 Windows Server 2016 Azure VM을 마이그레이션 원본의 대상으로 자동으로 선택 하는 프로세스가 시작 됩니다. Storage Migration Service는 원본에 맞게 VM 크기를 권장 하지만 **모든 크기 보기**를 선택 하 여이를 재정의할 수 있습니다. 인벤토리 데이터는 새 Azure VM을 Active Directory 도메인에 가입 하는 것 뿐만 아니라 관리 디스크와 해당 파일 시스템을 자동으로 구성 하는 데 사용 됩니다.
    3. Windows 관리 센터에서 Azure VM을 만든 후 복제 그룹 이름을 제공 하 고 **만들기**를 선택 합니다. 그러면 Windows 관리 센터에서 일반 저장소 복제본 초기 동기화 프로세스를 시작 하 여 데이터 보호를 시작 합니다.
    
    저장소 복제본을 사용 하 여 Azure Vm으로 마이그레이션하는 방법을 보여 주는 비디오는 다음과 같습니다.

    > [!VIDEO https://www.youtube-nocookie.com/embed/_VqD7HjTewQ] 

5. 파트너 관계에 대 한 세부 정보를 제공한 다음 **만들기** 를 선택 합니다 (그림 3 참조). <br>
   8gb 로그 크기와 같은 파트너 관계 정보를 보여주는 새 파트너 관계 화면을 ![합니다.](media/Storage-Replica-UI/Honolulu_SR_Create_Partnership.png)

    **그림 3: 새 파트너 관계 만들기**

> [!NOTE]
> Windows 관리 센터에서 저장소 복제본의 파트너 관계를 제거 해도 복제 그룹 이름이 제거 되지 않습니다.

### <a name="using-windows-powershell"></a>Windows PowerShell 사용

이제 Windows PowerShell을 사용하여 서버 간 복제를 구성합니다. 아래의 모든 단계를 노드에서 직접 수행 하거나 Windows Server 원격 서버 관리 도구이 포함 된 원격 관리 컴퓨터에서 수행 해야 합니다.  

1. 관리자로서 관리자 권한 Powershell 콘솔을 사용해야 합니다.  
2. 원본 및 대상 디스크, 원본 및 대상 로그, 원본 및 대상 노드, 로그 크기 등을 지정하여 서버 간 복제를 구성합니다.  

    ```PowerShell  
    New-SRPartnership -SourceComputerName sr-srv05 -SourceRGName rg01 -SourceVolumeName f: -SourceLogVolumeName g: -DestinationComputerName sr-srv06 -DestinationRGName rg02 -DestinationVolumeName f: -DestinationLogVolumeName g:  
    ```  

   출력:
   ```PowerShell
   DestinationComputerName : SR-SRV06
   DestinationRGName       : rg02
   SourceComputerName      : SR-SRV05
   PSComputerName          :
   ```

    > [!IMPORTANT]
    > 기본 로그 크기는 8GB입니다. `Test-SRTopology` cmdlet의 결과에 따라 값이 더 높거나 낮은 -LogSizeInBytes를 사용할 수도 있습니다.  

2.  복제 원본 및 대상 상태를 가져오려면 다음과 같이 `Get-SRGroup` 및 `Get-SRPartnership`을 사용합니다.  

    ```PowerShell  
    Get-SRGroup  
    Get-SRPartnership  
    (Get-SRGroup).replicas  
    ```
    출력:

    ```PowerShell
    CurrentLsn             : 0
    DataVolume             : F:\
    LastInSyncTime         :
    LastKnownPrimaryLsn    : 1
    LastOutOfSyncTime      :
    NumOfBytesRecovered    : 37731958784
    NumOfBytesRemaining    : 30851203072
    PartitionId            : c3999f10-dbc9-4a8e-8f9c-dd2ee6ef3e9f
    PartitionSize          : 68583161856
    ReplicationMode        : synchronous
    ReplicationStatus      : InitialBlockCopy
    PSComputerName         :
    ```

3.  다음과 같이 복제 진행률을 확인합니다.  

    1.  원본 서버에서 다음 명령을 실행하고 5015, 5002, 5004, 1237, 5001 및 2200 이벤트를 확인합니다.  

        ```PowerShell  
        Get-WinEvent -ProviderName Microsoft-Windows-StorageReplica -max 20  
        ```  

    2.  대상 서버에서 다음 명령을 실행하여 파트너 관계 생성을 표시하는 저장소 복제본 이벤트를 확인합니다. 이 이벤트는 복사한 바이트 수와 걸린 시간을 알려 줍니다. 예:  

        ```PowerShell  
        Get-WinEvent -ProviderName Microsoft-Windows-StorageReplica | Where-Object {$_.ID -eq "1215"} | fl  
        ```
        다음은 몇 가지 출력 예제입니다.
        ```
        TimeCreated  : 4/8/2016 4:12:37 PM  
        ProviderName : Microsoft-Windows-StorageReplica  
        Id           : 1215  
        Message      : Block copy completed for replica.  

        ReplicationGroupName: rg02  
        ReplicationGroupId: {616F1E00-5A68-4447-830F-B0B0EFBD359C}  
        ReplicaName: f:\  
        ReplicaId: {00000000-0000-0000-0000-000000000000}  
        End LSN in bitmap:   
        LogGeneration: {00000000-0000-0000-0000-000000000000}  
        LogFileId: 0  
        CLSFLsn: 0xFFFFFFFF  
        Number of Bytes Recovered: 68583161856  
        Elapsed Time (ms): 117  
        ```  

        > [!NOTE]
        > 저장소 복제본은 대상 볼륨과 해당 드라이브 문자 또는 탑재 지점을 분리합니다. 이것은 정상적인 현상입니다.  

    3.  또는 복제본의 대상 서버 그룹은 복사할 남은 바이트 수를 알려 주며 PowerShell을 통해 쿼리할 수 있습니다. 예를 들면 다음과 같습니다.  

        ```PowerShell  
        (Get-SRGroup).Replicas | Select-Object numofbytesremaining  
        ```  

        진행률 샘플(종료되지 않음):  

        ```PowerShell  
        while($true) {  

         $v = (Get-SRGroup -Name "RG02").replicas | Select-Object numofbytesremaining  
         [System.Console]::Write("Number of bytes remaining: {0}`r", $v.numofbytesremaining)  
         Start-Sleep -s 5  
        }  
        ```  

    4.  대상 서버에서 다음 명령을 실행하고 5009, 1237, 5001, 5015, 5005 및 2200 이벤트를 확인하여 처리 진행률을 이해합니다. 이 시퀀스에서는 오류 경고가 없어야 합니다. 여러 개의 1237 이벤트가 있습니다. 이는 진행률을 나타냅니다.  

        ```PowerShell  
        Get-WinEvent -ProviderName Microsoft-Windows-StorageReplica | FL  
        ```  

## <a name="step-4-manage-replication"></a>4단계: 복제 관리

이제 서버 간 복제된 인프라를 관리하고 운영합니다. 아래의 모든 단계를 노드에서 직접 수행 하거나 Windows Server 원격 서버 관리 도구이 포함 된 원격 관리 컴퓨터에서 수행할 수 있습니다.  

1.  `Get-SRPartnership` 및 `Get-SRGroup`을 사용하여 복제의 현재 원본과 대상 및 해당 상태를 확인합니다.  

2.  복제 성능을 측정하려면 원본 및 대상 노드 모두에서 `Get-Counter` cmdlet을 사용합니다. 카운터 이름은 다음과 같습니다.  

    -   \Storage Replica Partition I/O Statistics(*)\Number of times flush paused  

    -   \Storage Replica Partition I/O Statistics(*)\Number of pending flush I/O  

    -   \Storage Replica Partition I/O Statistics(*)\Number of requests for last log write  

    -   \Storage Replica Partition I/O Statistics(*)\Avg. Flush Queue Length  

    -   \Storage Replica Partition I/O Statistics(*)\Current Flush Queue Length  

    -   \Storage Replica Partition I/O Statistics(*)\Number of Application Write Requests  

    -   \Storage Replica Partition I/O Statistics(*)\Avg. Number of requests per log write  

    -   \Storage Replica Partition I/O Statistics(*)\Avg. App Write Latency  

    -   \Storage Replica Partition I/O Statistics(*)\Avg. App Read Latency  

    -   \Storage Replica Statistics(*)\Target RPO  

    -   \Storage Replica Statistics(*)\Current RPO  

    -   \Storage Replica Statistics(*)\Avg. Log Queue Length  

    -   \Storage Replica Statistics(*)\Current Log Queue Length  

    -   \Storage Replica Statistics(*)\Total Bytes Received  

    -   \Storage Replica Statistics(*)\Total Bytes Sent  

    -   \Storage Replica Statistics(*)\Avg. Network Send Latency  

    -   \Storage Replica Statistics(*)\Replication State  

    -   \Storage Replica Statistics(*)\Avg. Message Round Trip Latency  

    -   \Storage Replica Statistics(*)\Last Recovery Elapsed Time  

    -   \Storage Replica Statistics(*)\Number of Flushed Recovery Transactions  

    -   \Storage Replica Statistics(*)\Number of Recovery Transactions  

    -   \Storage Replica Statistics(*)\Number of Flushed Replication Transactions  

    -   \Storage Replica Statistics(*)\Number of Replication Transactions  

    -   \Storage Replica Statistics(*)\Max Log Sequence Number  

    -   \Storage Replica Statistics(*)\Number of Messages Received  

    -   \Storage Replica Statistics(*)\Number of Messages Sent  

    Windows PowerShell의 성능 카운터에 대한 자세한 내용은 [Get-Counter](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-Counter)를 참조하세요.  

3.  하나의 사이트에서 복제 방향을 이동하려면 `Set-SRPartnership` cmdlet을 사용합니다.  

    ```PowerShell  
    Set-SRPartnership -NewSourceComputerName sr-srv06 -SourceRGName rg02 -DestinationComputerName sr-srv05 -DestinationRGName rg01  
    ```  

    > [!WARNING]  
    > 초기 동기화가 진행 중일 때 Windows Server는 역할 전환을 방지 합니다. 초기 복제를 완료 하기 전에 전환 하려고 하면 데이터가 손실 될 수 있기 때문입니다. 초기 동기화가 완료 될 때까지 방향을 강제로 전환 하지 마세요.  

    이벤트 로그에서 복제 방향이 변경되고 복구 모드가 발생했는지 확인한 다음 조정합니다. 그런 다음 쓰기 IO에서 새 원본 서버가 소유한 저장소에 쓸 수 있습니다. 복제 방향을 변경하면 이전 원본 컴퓨터에서 쓰기 IO가 차단됩니다.  

4.  복제를 제거하려면 각 노드에서 `Get-SRGroup`, `Get-SRPartnership`, `Remove-SRGroup` 및 `Remove-SRPartnership`을 사용합니다. 대상 서버가 아니라 현재 복제 원본에서만 `Remove-SRPartnership` cmdlet을 실행해야 합니다. `Remove-Group`은 두 서버 모두에서 실행합니다. 예를 들어 두 서버에서 모든 복제를 제거하려면 다음을 실행합니다.  

    ```powershell
    Get-SRPartnership  
    Get-SRPartnership | Remove-SRPartnership  
    Get-SRGroup | Remove-SRGroup  
    ```  

## <a name="replacing-dfs-replication-with-storage-replica"></a>DFS 복제를 저장소 복제본으로 바꾸기  
많은 Microsoft 고객이 홈 폴더 및 부서 공유와 같은 구조화되지 않은 사용자 데이터에 대한 재해 복구 솔루션으로 DFS 복제를 배포합니다. DFS 복제는 Windows Server 2003 R2 이상의 모든 운영 체제에서 제공되며, 낮은 대역폭 네트워크에서 작동하므로 여러 노드로 대기 시간이 길고 변화가 낮은 환경에 적합합니다. 그러나 DFS 복제에는 데이터 복제 솔루션으로서 주목할 만한 제한 사항이 있습니다.  
* 사용 중이거나 열려 있는 파일을 복제 하지 않습니다.  
* 동기적으로 복제 되지 않습니다.  
* 비동기 복제 대기 시간은 몇 분, 몇 시간 또는 심지어 며칠이 걸릴 수 있습니다.  
* 전원 중단 후 장시간의 일관성 확인이 필요할 수 있는 데이터베이스를 기반으로 합니다.  
* 일반적으로 다중 마스터로 구성 됩니다 .이는 변경 내용이 양방향으로 전달 될 수 있으므로 새 데이터를 덮어쓸 수 있습니다.  

저장소 복제본에는 이러한 제한 사항이 없습니다. 그러나 일부 환경에서는 유익하지 않을 수 있는 몇 가지 요소가 있습니다.  

* 볼륨 간에 일대일 복제만 허용합니다. 여러 서버 간에 서로 다른 볼륨을 복제할 수 있습니다.  
* 비동기 복제를 지 원하는 반면, 낮은 대역폭, 대기 시간이 높은 네트워크를 위해 설계 되지 않았습니다.  
* 복제가 진행 되는 동안에는 대상의 보호 된 데이터에 대 한 사용자 액세스를 허용 하지 않습니다.  

이러한 것이 차단 요소가 아닌 경우 저장소 복제본을 사용하여 DFS 복제 서버를 이 최신 기술로 대체할 수 있습니다.   
대략적인 프로세스는 다음과 같습니다.  

1. 두 서버에 Windows Server를 설치 하 고 저장소를 구성 합니다. 이는 기존 서버 집합의 업그레이드 또는 새로운 설치를 의미할 수 있습니다.  
2. 복제하려는 모든 데이터가 C: 드라이브가 아닌 하나 이상의 데이터 볼륨에 있는지 확인합니다.   
   a.  시간을 절약하기 위해 백업 또는 파일 복사본을 사용하여 데이터를 다른 서버에 시드할 뿐만 아니라 씬 프로비전 저장소를 사용할 수도 있습니다. DFS 복제와 달리 메타데이터 같은 완벽한 보안 일치가 필요하지 않습니다.  
3. 원본 서버에서 데이터를 공유 하 고 DFS 네임 스페이스를 통해 액세스할 수 있도록 합니다. 이는 서버 이름이 재해 사이트의 서버 이름으로 변경된 경우에도 사용자가 액세스할 수 있도록 하는 데 중요합니다.  
   a.  대상 서버에서 정상 작동 중에 사용할 수 없는 일치하는 공유를 만들 수 있습니다.   
   b.  DFS 네임 스페이스 네임 스페이스에 대상 서버를 추가 하지 마세요. 그렇지 않으면 모든 폴더 대상을 사용 하지 않도록 설정 해야 합니다.  
4. 저장소 복제본 복제를 사용하도록 설정하고 초기 동기화를 완료합니다. 복제는 동기식 또는 비동기식일 수 있습니다.   
   a.  그러나 대상 서버에서 IO 데이터 일관성을 유지하기 위해 동기 복제가 권장됩니다.   
   b.  볼륨 섀도 복사본을 사용하도록 설정하고 VSSADMIN 또는 원하는 다른 도구로 주기적으로 스냅샷을 생성하는 것이 좋습니다. 그러면 응용 프로그램이 해당 데이터 파일을 디스크에 지속적으로 플러시합니다. 재해가 발생한 경우 대상 서버에서 비동기식으로 부분 복제되었을 수 스냅샷에서 파일을 복구할 수 있습니다. 스냅샷은 파일과 함께 복제됩니다.  
5. 재해가 발생할 때까지 정상적으로 작동합니다.  
6. 사용자에게 복제된 볼륨을 표시하는 새 원본으로 대상 서버를 전환합니다.  
7. 동기 복제를 사용하는 경우에는 사용자가 원본 서버의 손실 기간 동안 트랜잭션 보호(복제와 상관없음) 없이 데이터를 기록한 응용 프로그램을 사용하지 않는 한 데이터 복원은 필요 없습니다. 비동기 복제를 사용하는 경우에는 VSS 스냅샷 탑재의 필요성이 더 높지만 응용 프로그램 일치 스냅샷을 위해 모든 상황에서 VSS를 사용하는 것이 좋습니다.  
8. 서버와 해당 공유를 DFS 네임 스페이스 폴더 대상으로 추가 합니다.   
9. 그러면 사용자가 자신의 데이터에 액세스할 수 있습니다.  

   > [!NOTE]
   > 재해 복구 계획은 복잡한 사안이므로 세부 사항에 주의해야 합니다. Runbook을 만들고 매년 라이브 장애 조치(failover) 드릴을 수행하는 것이 좋습니다. 실제 재해가 발생하면 혼란스러운 상황에서 숙련된 직원을 활용하지 못하게 될 수도 있습니다.  

## <a name="adding-an-azure-vm-connected-to-your-network-via-expressroute"></a><a name="add-azure-vm-expressroute"></a>Express 경로를 통해 네트워크에 연결 된 Azure VM 추가

1. [Azure Portal에서 express](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-portal-resource-manager)경로를 만듭니다.<br>Express 경로를 승인한 후에는 리소스 그룹이 구독에 추가 되 고, **리소스 그룹** 으로 이동 하 여이 새 그룹을 볼 수 있습니다. 가상 네트워크 이름을 기록해 둡니다.
Express 경로를 사용 하 여 추가 된 리소스 그룹을 보여 주는 Azure Portal ![](media/Server-to-Server-Storage-Replication/express-route-resource-group.png)
    
    **그림 4: Express 경로와 연결 된 리소스-가상 네트워크 이름을 적어둡니다.**
1. [새 리소스 그룹을 만듭니다](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
1. [네트워크 보안 그룹을 추가](https://docs.microsoft.com/azure/virtual-network/virtual-networks-create-nsg-arm-pportal)합니다. 만들 때 만든 Express 경로와 연결 된 구독 ID를 선택 하 고 방금 만든 리소스 그룹을 선택 합니다.
<br><br>네트워크 보안 그룹에 필요한 인바운드 및 아웃 바운드 보안 규칙을 추가 합니다. 예를 들어 VM에 대 한 원격 데스크톱 액세스를 허용할 수 있습니다.
1. 다음 설정을 사용 하 여 [AZURE VM을 만듭니다](https://docs.microsoft.com/azure/virtual-machines/windows/quick-create-portal) (그림 5에 표시).
    - **공용 IP 주소**: 없음
    - **가상 네트워크**: express 경로를 사용 하 여 추가 된 리소스 그룹에서 기록해 둔 가상 네트워크를 선택 합니다.
    - **네트워크 보안 그룹 (방화벽)** : 이전에 만든 네트워크 보안 그룹을 선택 합니다.
    Express 경로 네트워크 설정을 표시 하는 가상 컴퓨터 만들기 ![**그림 5: express 경로 네트워크 설정을 선택 하는 동안 VM 만들기**](media/Server-to-Server-Storage-Replication/azure-vm-express-route.png)
    
1. VM을 만든 후에는 [2 단계: 운영 체제, 기능, 역할, 저장소 및 네트워크 프로 비전](#provision-os)을 참조 하세요.


## <a name="related-topics"></a>관련 항목  
- [저장소 복제본 개요](storage-replica-overview.md)  
- [공유 저장소를 사용 하 여 확장 클러스터 복제](stretch-cluster-replication-using-shared-storage.md)  
- [클러스터 간 저장소 복제](cluster-to-cluster-storage-replication.md)
- [저장소 복제본: 알려진 문제](storage-replica-known-issues.md)  
- [저장소 복제본: 질문과 대답](storage-replica-frequently-asked-questions.md)
- [Windows Server 2016의 스토리지 공간 다이렉트](../storage-spaces/storage-spaces-direct-overview.md)  
