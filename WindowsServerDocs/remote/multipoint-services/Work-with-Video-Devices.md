---
title: 비디오 장치 작업
description: 비디오 모니터와 프로젝터가 MultiPoint 서비스의 스테이션에서 작동 하는 방식 알아보기
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 2f7f5a97-efd2-4184-8ad3-cf029d615eab
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 6b967d4523058fe1dfcb086e5918f84257bd51bf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80820446"
---
# <a name="work-with-video-devices"></a>비디오 장치 작업
모니터, 프로젝터 등의 비디오 장치가 MultiPoint 서비스 시스템의 컴퓨터나 MultiPoint 서비스 *스테이션*에 연결된 경우 어떻게 작동하는지 알아봅니다.  
  
## <a name="working-with-video-monitors"></a>비디오 모니터 작업  
MultiPoint 서비스 시스템 하드웨어에 따라 다음과 같이 두 가지 방법으로 비디오 모니터를 연결할 수 있습니다.  
  
-   에 대 한 *USB 허브 기반 시스템*, 다음 그림에 나와 있는 것 처럼 컴퓨터에서 열려 있는 비디오 포트에 비디오 모니터 케이블을 연결 합니다.  
  
    ![USB 허브 기반 시스템에 대한 동영상 연결 이미지](./media/WMSVideoConnection.gif)  
  
-   에 대 한 *다기능 허브 기반 시스템* 비디오 지원이 기본 제공 되는 비디오 포트 다기능 허브에 비디오 모니터 케이블을 연결 합니다.  
  
    ![다기능 허브 및 동영상 연결 이미지](./media/WMSMultifunctionHubVideoConnection.gif)  
  
자세한 내용은 [스테이션 설치](Set-Up-a-Station.md) 항목을 참조하세요.  
  
## <a name="working-with-video-projectors"></a>비디오 프로젝터 작업  
예를 들어 랩 환경에서 다른 사용자가 볼 수 있도록 큰 이미지를 표시하려는 경우 MultiPoint 서비스 시스템에 비디오 프로젝터를 연결할 수 있습니다. 모두 USB 허브 기반 및 다기능 허브 기반의 스테이션에 대 한 두 가지 옵션이 있습니다 프로젝터 스테이션에 연결 합니다.  
  
-   모니터를 프로젝터로 바꾼 후 다음 그림과 같이 프로젝터를 해당 스테이션의 디스플레이 디바이스로 사용합니다.  
  
    ![컴퓨터에 연결된 프로젝터 이미지](./media/WMSVideoProjectorConnection.gif)  
  
-   프로젝터와 모니터를 모두 스테이션의 비디오 포트에 연결 하는 비디오 분할자 장치를 가져옵니다.  
  
    MultiPoint 서비스는 두 디스플레이 디바이스에 모두 동일한 이미지를 표시합니다. 프로젝션하지 않을 경우에는 프로젝터를 끄고 비디오 모니터만 사용할 수 있습니다.  
  
두 옵션 중 하나를 사용할 경우 다음 사항에 유의하세요.  
  
-   비디오 디스플레이 연결 시, MultiPoint 서비스에서 새 디스플레이를 올바르게 인식할 수 있도록 *스테이션을 다시 연결*해야 할 수 있습니다. 스테이션의 비디오 디스플레이 장치에 표시 되는 지침을 따릅니다.  
  
-   DVI와 VGA 플러그 간에 변환하려면 어댑터 또는 변환기 디바이스를 가져와야 할 수 있습니다.  
  
-   "Y" 분할기 케이블을 사용 하면 두 비디오 장치의 비디오 품질이 떨어질 수 있습니다.  
  
-   "Y" 분할기 케이블을 통해 프로젝터와 모니터를 모두 사용 하는 경우 MultiPoint 서비스는 두 장치의 화면 해상도를 가장 낮은 장치 중 가장 낮은 해상도 (일반적으로 프로젝터)로 조정 합니다.  
  
-   MultiPoint 서비스는 여러 모니터에서 단일 스테이션 표시를 확장 하는 기능을 지원 하지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
[스테이션 하드웨어 관리](Manage-Station-Hardware.md)  
[스테이션 설치](Set-Up-a-Station.md) 