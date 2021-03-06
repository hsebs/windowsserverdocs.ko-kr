---
title: 서버 백업 설정 및 사용자 지정
description: Windows Server Essentials를 사용 하는 방법을 설명 합니다.
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 441c2d6c-435a-42cb-90f2-6d680d279d34
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 364ba61d42fcb2ae5bc4f91a71083b880eb36ab8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852626"
---
# <a name="set-up-or-customize-server-backup"></a>서버 백업 설정 및 사용자 지정

>적용 대상: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
  
 서버 백업은 설치 중에 자동으로 구성되지 않습니다. 매일 백업을 예약하여 서버와 해당 데이터를 자동으로 보호해야 합니다. 대부분 조직에서는 며칠 동안 생성된 데이터가 손실되면 안 되므로 매일 백업 계획을 유지 관리하는 것이 좋습니다.  
  
 다음 섹션을 참조하여 서버 백업을 설정하거나 사용자 지정하세요.  
  
-   [서버 백업 설정&reg; 설정 또는 변경](Set-up-or-customize-server-backup.md#BKMK_1)
  
-   [서버 백업 일정](Set-up-or-customize-server-backup.md#BKMK_2)  
  
-   [대상 드라이브 백업](Set-up-or-customize-server-backup.md#BKMK_Target)  
  
-   [백업할 항목](Set-up-or-customize-server-backup.md#BKMK_4)  
  
##  <a name="set-up-or-change-server-backup-settings"></a><a name="BKMK_1"></a>서버 백업 설정 변경 또는 변경  
  
#### <a name="to-set-up-or-change-server-backup-settings"></a>서버 백업 설정을 지정 또는 변경하려면  
  
1.  **대시보드**를 열고 **장치** 탭을 클릭합니다.  
  
2.  목록 뷰에서 서버를 클릭하여 선택합니다.  
  
3.  작업 창에서 **서버에 대한 백업 설정**을 클릭합니다.  
  
    > [!NOTE]
    >  기존 백업 설정을 변경하려면 **서버에 대한 백업 사용자 지정**을 클릭합니다.  
  
4.  마법사의 지시를 따릅니다.  
  
    > [!NOTE]
    >  외부 하드 드라이브를 서버에 연결하기 전에 마법사를 시작하는 경우 하드 드라이브를 연결한 후 **백업 대상을 선택합니다.** 페이지에서 **목록 새로 고침**을 클릭합니다.  
  
> [!NOTE]
>  Windows Server Essentials의 기본 설치에서 서버는 매주 한 번 조각 모음을 자동으로 수행 하도록 구성 됩니다. 따라서 타사 이미징 소프트웨어를 사용할 경우 기본 백업보다 큰 백업이 만들어질 수 있습니다. 서버에서 정기적으로 조각 모음을 수행할 필요가 없으면 다음 단계에 따라 조각 모음 일정을 끌 수 있습니다.  
> 
> 1. Windows 키 +W를 눌러 **검색**을 엽니다.  
>    2. 검색 텍스트 상자에 **Defragment**를 입력합니다.  
>    3. 결과 섹션에서 **드라이브 조각 모음 및 최적화**를 클릭합니다.  
>    4. **드라이브 최적화** 페이지에서 드라이브를 선택하고 **설정 변경**을 클릭합니다.  
>    5. **최적화 일정** 창에서 **예약 실행(권장)** 확인란을 선택 취소한 후 **확인**을 클릭하여 변경 내용을 저장합니다.  
  
##  <a name="server-backup-schedule"></a><a name="BKMK_2"></a>서버 백업 일정  
 서버 백업 설정 마법사 또는 서버 백업 사용자 지정 마법사를 사용할 경우 하루 중에 여러 번 서버 데이터를 백업하도록 선택할 수 있습니다. 마법사는 증분 기반 백업을 예약하기 때문에 백업이 신속하게 실행되고 서버 성능이 크게 영향을 받지 않습니다. 기본적으로 마법사는 매일 오후 12:00 및 오후 11:00에 실행되도록 백업을 예약합니다. 그러나 조직의 요구에 따라 백업 일정을 조정할 수 있습니다. 때때로 백업 계획의 유효성을 평가하고 필요에 따라 계획을 변경해야 합니다.  
  
##  <a name="backup-target-drive"></a><a name="BKMK_Target"></a>대상 드라이브 백업  
 백업에 여러 외부 스토리지 드라이브를 사용하고 온사이트 및 오프사이트 스토리지 위치 사이에서 드라이브를 순환할 수 있습니다. 이렇게 하면 하드웨어 온사이트에 물리적 손상이 발생할 경우 데이터를 복구하는 데 도움이 되므로 재해 대비 계획을 향상할 수 있습니다.  
  
 서버 백업을 위한 스토리지 드라이브를 선택할 때 다음을 고려하세요.  
  
-   데이터를 저장할 충분한 공간이 있는 드라이브를 선택합니다. 스토리지 드라이브에는 백업할 데이터 스토리지 용량의 2.5배 이상이 포함되어야 합니다. 또한 드라이브는 향후 서버 데이터 증가를 수용할 만큼 충분히 커야 합니다.  
  
-   외부 스토리지 드라이브를 사용하는 경우 드라이브가 비어 있거나 필요하지 않은 데이터만 포함하고 있는지 확인합니다.  
  
    > [!CAUTION]
    >  서버 백업 설정 마법사에서는 백업을 위해 스토리지 드라이브를 구성할 때 해당 드라이브를 포맷합니다.  
  
-   백업 대상 드라이브에 오프라인 드라이브가 포함된 경우 백업 구성에 실패합니다. 구성을 완료하려면 백업 대상을 선택할 때 확인란을 선택 취소하여 오프라인 상태인 드라이브를 제외합니다.  
  
-   백업 대상으로 이전 백업을 포함하는 드라이브를 선택하는 경우 이전 백업을 유지할지 여부를 선택할 수 있습니다. 백업을 유지하면 드라이브가 포맷되지 않습니다.  
  
-   외부 저장소 드라이브 제조업체의 웹 사이트를 방문 하 여 Windows Server Essentials를 실행 하는 컴퓨터에서 백업 드라이브가 지원 되는지 확인 해야 합니다.  
  
-   드라이브는 EFI(Extensible Firmware Interface) 시스템 파티션을 포함할 수 없습니다. USB 드라이브에 EFI 파티션이 있는 경우 디스크가 시동 디스크라고 가정합니다. 디스크의 데이터가 필요 하지 않은 경우 디스크를 다시 포맷 하 여 백업에 사용할 수 있습니다.  
  
    > [!CAUTION]
    >  디스크를 다시 포맷할 경우 모든 데이터가 삭제됩니다.  
  
    #### <a name="to-remove-an-efi-system-partition-from-a-usb-disk"></a>USB 디스크에서 EFI 시스템 파티션을 제거하려면  
  
    1.  제어판에서 **시스템 및 보안**을 엽니다.  
  
    2.  **관리 도구**에서 **하드 디스크 파티션 만들기 및 포맷**을 클릭합니다.  
  
    3.  USB 디스크에 있는 모든 볼륨을 삭제하거나 EFI 파티션만 삭제합니다. 서버 백업 설정 마법사가 모든 볼륨을 삭제합니다.  
  
-   드라이브는 공유 서버 폴더를 포함할 수 없습니다. 디스크를 백업 대상 드라이브로 사용하려면 먼저 모든 공유 서버 폴더에서 공유를 중지해야 합니다. 대시보드 또는 파일 탐색기에서 공유를 중지할 수 있습니다.  
  
    #### <a name="to-stop-sharing-on-a-server-folder-from-the-dashboard"></a>대시보드에서 서버 폴더에 대한 공유를 중지하려면  
  
    1.  대시보드에서 **저장소**를 클릭한 후 **서버 폴더**를 클릭합니다.  
  
    2.  공유를 중지하려는 폴더를 선택한 후 작업 창에서 **중지**를 클릭합니다.  
  
> [!NOTE]
>  백업 드라이브에 공간이 부족 하 여 백업에 실패 한 경우 백업 대상 드라이브의 드라이브 문자가 Windows Server Essentials 데이터베이스에서 제거 되 고 대시보드에 드라이브가 표시 되지 않습니다. 이후 백업에서 이 드라이브를 사용하려는 경우에는 네이티브 도구를 사용하여 드라이브 문자를 다시 할당해야 합니다.  
> 
>  **기존 볼륨의 드라이브 문자를 다시 할당 하려면**  
> 
> 1. 제어판에서 **시스템 및 보안**을 엽니다.  
>    2. **관리 도구**에서 **하드 디스크 파티션 만들기 및 포맷**을 클릭합니다.  
>    3. 드라이브를 마우스 오른쪽 단추로 클릭하고 **드라이브 문자 및 경로 변경**을 클릭합니다.  
>    4. **추가**를 클릭합니다.  
>    5. 드라이브 문자 또는 경로 추가 대화 상자에서 할당할 드라이브 문자를 선택합니다. 동일한 드라이브 문자를 다시 할당할 수 있습니다. 그런 다음 **확인을**클릭 합니다.  
> 
>    드라이브가 즉시 대시보드에 나타납니다.  
  
##  <a name="items-to-be-backed-up"></a><a name="BKMK_4"></a>백업할 항목  
 서버에 있는 모든 드라이브, 파일 및 폴더를 백업하도록 선택하거나, 백업할 개별 드라이브, 파일 또는 폴더 백업을 선택할 수 있습니다.  
  
 드라이브를 추가 또는 제거하거나, 공유 파일 및 폴더를 추가 또는 제거할 때 서버 백업 구성을 다시 방문하여 이러한 항목이 백업 구성에 추가되었거나 백업 구성에서 제거되었는지 확인해야 합니다. 백업을 위해 항목을 추가하거나 제거하려면 다음의 하나를 수행합니다.  
  
- 데이터 드라이브를 서버 백업에 포함하려면 옆에 있는 확인란을 선택합니다.  
  
- 데이터 드라이브를 서버 백업에서 제외하려면 옆에 있는 확인란을 선택 취소합니다.  
  
  > [!NOTE]
  >  백업에서 **운영 체제** 항목을 제외하려면 먼저 **시스템 백업(권장)** 확인란을 선택 취소해야 합니다.  
  
  서버 백업에 사용되는 서버 스토리지 크기를 최소화하려면 중요하거나 특히 중요하다고 간주되지 않는 파일이 포함된 모든 폴더를 제외할 수 있습니다.  
  
  예를 들어 많은 하드 드라이브 공간을 사용하는 녹화된 TV 프로그램이 포함된 폴더가 있을 수 있습니다. 일반적으로 이러한 프로그램을 시청한 이후에는 삭제하므로 이러한 파일을 백업하지 않도록 선택할 수 있습니다. 또는 유지하지 않으려는 임시 파일이 포함된 폴더가 있을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
  
-   [서버 백업 관리](Manage-Server-Backup-in-Windows-Server-Essentials.md)  
  
-   [백업 및 복원 관리](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials 관리](Manage-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials 사용](../use/Use-Windows-Server-Essentials.md)
