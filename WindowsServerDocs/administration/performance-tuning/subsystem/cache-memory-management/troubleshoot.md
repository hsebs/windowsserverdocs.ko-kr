---
title: 캐시 및 메모리 관리자 성능 문제 해결
description: Windows Server 16의 캐시 및 메모리 관리자 성능 문제 해결
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: pavel; atales
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 0b01808564cfaf1eaedf30a66c774e2228205847
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851656"
---
# <a name="troubleshoot-cache-and-memory-manager-performance-issues"></a>캐시 및 메모리 관리자 성능 문제 해결

Windows Server 2012 이전에는 사용 가능한 메모리가 특정 워크 로드에서 거의 고갈 될 때까지 시스템 파일 캐시가 증가 하는 두 가지 주요 잠재적인 문제가 발생 했습니다. 이러한 상황에서 시스템이 느려지는 경우 서버가 이러한 문제 중 하나에 직면 하 고 있는지 여부를 확인할 수 있습니다.


## <a name="counters-to-monitor"></a>모니터링할 카운터

-   메모리\\장기 평균 대기 캐시 수명 &lt; 1800 초

-   메모리\\사용 가능한 Mb가 부족 합니다.

-   메모리\\시스템 캐시 상주 바이트

메모리\\사용 가능한 Mb가 적고 메모리\\시스템 캐시 상주 바이트가 실제 메모리의 상당 부분을 차지 하 고 있는 경우,이 [지도](https://technet.microsoft.com/sysinternals/ff700229.aspx) 를 사용 하 여 캐시가 사용 되 고 있는지 확인할 수 있습니다.

## <a name="system-file-cache-contains-ntfs-metafile-data-structures"></a>시스템 파일 캐시에 NTFS 메타 파일 데이터 구조가 포함 되어 있습니다.


이 문제는 다음 그림에 표시 된 것 처럼 중요 한 맵 출력의 매우 많은 활성 메타 파일 페이지에 표시 됩니다. 이 문제는 수백만 개의 파일이 액세스 되는 사용량이 많은 서버에서 관찰 되어 NTFS 메타 파일 데이터가 캐시에서 해제 되지 않는 경우에 발생할 수 있습니다.

![지도 보기](../../media/perftune-guide-rammap.png)

*DynCache* tool에서 완화할 때 사용 되는 문제입니다. Windows Server 2012 +에서는 아키텍처가 다시 디자인 되었으며이 문제가 더 이상 존재 하지 않습니다.

## <a name="system-file-cache-contains-memory-mapped-files"></a>시스템 파일 캐시에 메모리 매핑된 파일이 포함 되어 있습니다.


이 문제는 다양 한 맵 출력에서 매우 많은 활성 매핑된 파일 페이지로 표시 됩니다. 이는 일반적으로 서버에서 일부 응용 프로그램이 파일\_플래그를 사용 하 여 [CreateFile](https://msdn.microsoft.com/library/windows/desktop/aa363858.aspx) API를 사용 하 여 많은 수의 큰 파일을 여는\_임의의\_액세스 플래그가 설정 되었음을 나타냅니다.

이 문제는 기술 자료 문서 [2549369](https://support.microsoft.com/default.aspx?scid=kb;en-US;2549369)에 자세히 설명 되어 있습니다. 파일\_플래그\_임의\_액세스 플래그는 캐시 관리자가 메모리에서 파일의 매핑된 뷰를 가능한 한 오랫동안 유지 하는 힌트입니다 (메모리 관리자가 메모리 부족 상태를 신호 하지 않을 때까지). 동시에이 플래그는 캐시 관리자에 게 파일 데이터의 프리페치를 사용 하지 않도록 지시 합니다.

이 상황은 Windows Server 2012 +의 향상 된 기능을 사용 하 여 일부 범위로 완화 되었지만 파일\_플래그\_임의의\_액세스를 사용 하지 않고 응용 프로그램 공급 업체에서 주로 문제를 해결 해야 합니다. 앱 공급 업체에 대 한 대체 솔루션은 파일에 액세스할 때 낮은 메모리 우선 순위를 사용 하는 것입니다. 이는 [Setthreadinformation](https://msdn.microsoft.com/library/windows/desktop/hh448390.aspx) API를 사용 하 여 구현할 수 있습니다. 낮은 메모리 우선 순위로 액세스 되는 페이지는 작업 집합에서 보다 적극적으로 제거 됩니다.

Windows Server 2016 이상에서 시작 하는 캐시 관리자는 트리밍 결정을 내릴 때 FILE_FLAG_RANDOM_ACCESS를 무시 하 여이를 완화 하므로 FILE_FLAG_RANDOM_ACCESS 플래그 없이 열린 다른 파일 처럼 처리 됩니다. 캐시 관리자는 여전히이 플래그를 사용 하 여 파일 데이터의 프리페치를 해제 합니다. 이 플래그를 사용 하 여 많은 수의 파일을 열고 진정한 임의 방식으로 액세스 하는 경우에도 시스템 캐시를 계속 사용할 수 있습니다. 응용 프로그램에서 사용 하지 FILE_FLAG_RANDOM_ACCESS 하는 것이 좋습니다.
