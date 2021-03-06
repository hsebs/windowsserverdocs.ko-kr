---
title: MultiPoint 서비스에서 디스크 보호 구성
description: MultiPoint 서비스에 대 한 디스크 보호를 설정 하는 방법 알아보기
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: bd9bf5b9-e481-499b-9c15-7ee5a4f470c4
author: evaseydl
manager: scottman
ms.author: evas
ms.date: 08/04/2016
ms.openlocfilehash: eee4fc1b80ff57ee1ab5ee683d82c06fbe36b549
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854086"
---
# <a name="configure-disk-protection"></a>디스크 보호를 구성 합니다.
Multipoint 서비스에서 디스크 보호를 사용 하 여 의도 하지 않은 업데이트 로부터 시스템 볼륨을 보호 하 고, 디스크 보호가 활성 상태인 동안 Windows 업데이트를 보존 하도록 예약 하 고, 디스크 보호를 일시적으로 사용 하지 않도록 설정 하 고, 디스크 보호를 제거할 수 있습니다.  
  
MultiPoint 서비스에서 디스크 보호를 사용 하도록 설정 하면 시스템 볼륨 (Windows가 설치 된 드라이브, 일반적으로 C:)을 보호할 수 있습니다. 원치 않는 변경 내용 으로부터 디스크 보호를 사용 하도록 설정 하면 시스템 볼륨에 대 한 변경 내용이 임시 위치에 저장 되므로 컴퓨터를 다시 시작 하기만 하면 시스템이 자동으로 알려진 이전 상태로 돌아갑니다.  
  
관리자는 디스크 보호를 일시적으로 사용 하지 않도록 설정 하 여 소프트웨어를 쉽게 설치 하거나 구성을 변경할 수 있습니다. Windows 업데이트 및 맬웨어 방지 정의를 사용 하 여 시스템을 최신 상태로 유지 하기 위해 디스크 보호는 유지 관리 기간을 예약 하 여 업데이트를 다운로드 하 고 설치 합니다. 또한 관리자는 유지 관리 기간 동안 실행 되는 사용자 지정 스크립트를 제공 하 여 Windows 업데이트 이상의 유지 관리 요구 사항을 수용할 수 있습니다.  
  
## <a name="enable-disk-protection"></a>디스크 보호를 사용 하도록 설정  
디스크 보호를 사용 하도록 설정 하기 전에 모든 응용 프로그램 및 드라이버가 설치 되어 있고 최신 상태 인지 확인 하 고 사용자 프로필을 보호 되지 않는 볼륨으로 이동 해야 합니다. 디스크 보호를 사용 하도록 설정한 후 수동으로 업데이트 해야 하는 경우 디스크 보호를 일시적으로 사용 하지 않도록 설정할 수 있습니다. 그러나 디스크 보호를 설정 하기 전에 시스템을 이상적인 상태로 전환 하는 것이 가장 쉽습니다.  
  
 
1.  MultiPoint 서비스를 실행 하는 서버에 관리자로 로그온 합니다.  
  
2.  디스크 보호를 사용 하도록 설정 하기 전에:  
  
    -   MultiPoint 서비스 시스템이 정확한 상태를 유지 하려는 상태 인지 확인 합니다. 예를 들어 설치 된 소프트웨어, 시스템 설정 및 업데이트가 올바른지 확인 합니다.  
  
    -   보호 되지 않는 볼륨으로 사용자 프로필을 이동 하거나 [MultiPoint 서비스에서 파일 공유 사용](Enable-file-sharing-in-MultiPoint-services.md)에 설명 된 대로 시스템 볼륨에서 공유 파일 위치를 설정 합니다.  
  
3.  **시작** 화면이 열리면서 **다중 포인트 관리자**합니다.  
  
4.  **홈** 탭을 클릭 하 고 **디스크 보호 사용**을 클릭 한 다음 **확인**을 클릭 합니다.  
  
디스크 보호를 처음 사용 하는 경우 드라이버를 설치 하 고 시스템 볼륨에 캐시 파일을 만들어 시스템을 준비 합니다. 디스크 보호를 활성화 하는 동안 캐시 파일에는 시스템 볼륨에 대 한 변경 내용이 임시로 저장 됩니다. 시스템 업데이트는 캐시 파일에 저장 되므로 캐시 파일 외부에 있는 볼륨의 보호 된 콘텐츠를 변경 하지 않습니다. 시스템이 시작 될 때마다 캐시 파일이 다시 설정 되어 이전 시스템이 시작 된 이후에 저장 된 변경 내용이 모두 삭제 됩니다. 따라서 시스템은 항상 디스크 보호를 사용 하도록 설정한 경우와 동일한 상태로 시작 됩니다.  
  
Windows에서는 시스템 페이지 파일, 크래시 덤프 위치 및 이벤트 로그를 포함 하 여 몇 가지 시스템 파일을 업데이트 해야 합니다. 이러한 파일은 디스크 보호를 사용 하는 경우 삭제 되지 않습니다. 이를 위해 처음으로 디스크 보호를 사용 하도록 설정 하 고 해당 파일을 해당 볼륨으로 이동 하면 이름이 지정 된 새 볼륨이 만들어집니다. 해당 파일에 대 한 쓰기는 보호 되지 않으므로 디스크 보호를 사용 하는 경우에도 다시 시작을 통해 유지 됩니다.  
  
## <a name="schedule-software-updates"></a>소프트웨어 업데이트 예약  
Windows 업데이트를 자동으로 설치 하도록 Windows를 구성한 경우에는 디스크 보호에서 구성 된 시간에 이러한 업데이트를 허용 하 고 업데이트를 삭제 하지 않습니다. 예를 들어 Windows 업데이트가 오전 3:00에 대해 예약 된 경우 디스크 보호는 매일 3:00 오전에 업데이트를 확인 합니다. 업데이트를 찾은 경우 MultiPoint 서비스는 일시적으로 디스크 보호를 사용 하지 않도록 설정 하 고, 업데이트를 적용 한 후 디스크 보호를 다시 사용 하도록 설정 합니다.  
   
1.  다중 포인트 관리자에서 **홈** 탭을 표시 하 고 **소프트웨어 업데이트 예약**을 클릭 합니다.  
  
2.  소프트웨어 업데이트 예약 대화 상자에서 **업데이트 위치**를 클릭 하 고 업데이트에 대 한 시간을 선택 합니다 (예: **오전 3:00**).  
  
3.  **Windows 업데이트 실행** 확인란을 선택 합니다.  
  
4.  조직에서 자체 업데이트 스크립트를 실행 하는 경우 **다음 프로그램 실행** 확인란을 선택 하 고 조직의 업데이트 스크립트 위치를 지정 합니다.  
  
5.  업데이트를 실행할 수 있는 최대 시간을 선택 합니다.  
  
6.  **완료 되 면**에서 시스템이 이전 전원 상태로 돌아가거나 업데이트를 적용 한 후 종료 되도록 할지 여부를 선택 합니다.  
  
7.  **확인**을 클릭합니다.  
  
## <a name="temporarily-disable-disk-protection"></a>일시적으로 디스크 보호 사용 안 함  
관리자가 소프트웨어를 설치 하거나, 시스템 설정을 변경 하거나, 시스템 업데이트와 관련 된 기타 유지 관리 작업을 수행 해야 하는 경우 디스크 보호를 일시적으로 사용 하지 않도록 설정할 수 있습니다. 변경한 후에는 디스크 보호를 다시 사용 하도록 설정 합니다. 시스템을 다시 시작 하는 동안 디스크 보호를 사용 하도록 설정 했을 때 시스템의 상태가 유지 됩니다.  
    
1.  다중 포인트 관리자에서 **홈** 탭을 클릭 합니다.  
  
2.  홈 탭에서 **디스크 보호 사용 안 함**을 클릭 한 다음 **확인**을 클릭 합니다.  
  
> [!NOTE]  
> 유지 관리가 완료 된 후에는 디스크 보호를 다시 사용 하도록 설정 해야 합니다. 관리자가 디스크 보호를 명시적으로 다시 사용 하도록 설정할 때까지 시스템은 다시 보호 되지 않습니다.  
  
## <a name="uninstall-disk-protection"></a>디스크 보호 제거  
디스크 보호를 제거 하면 드라이버 및 캐시 파일이 제거 되므로 디스크 보호의 장기 사용을 중지 하려는 경우에만이 작업을 수행 해야 합니다. 단순히 유지 관리를 수행 하거나 보호를 일시적으로 중지 하려는 경우에는 디스크 보호 사용 안 함 작업을 대신 사용 합니다.  
  
사용 하거나 사용 하지 않도록 설정 되어 있는지 여부에 관계 없이 디스크 보호를 제거할 수 있습니다.  
   
1.  다중 포인트 관리자에서 **홈** 탭을 클릭 합니다.  
  
2.  홈 탭에서 **디스크 보호 제거**를 클릭 한 다음 **확인**을 클릭 합니다.  
  
    **확인**을 클릭 하면 컴퓨터가 다시 시작 됩니다. 제거 프로세스를 수행 하려면 드라이버 및 캐시 파일이 제거 되는 동안 여러 번 다시 시작 해야 합니다. D 유지 파티션은 유지 되 고 파일 페이지, 크래시 덤프 위치 및 이벤트 로그 파일은 계속 해 서 d 보존 파티션을 사용 하도록 구성 됩니다.