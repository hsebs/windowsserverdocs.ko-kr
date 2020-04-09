---
title: winsat mfmedia
description: 미디어 파운데이션 프레임 워크를 사용 하 여 비디오 디코딩 (재생)의 성능을 측정 하는 winsat mfmedia Windows 명령입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 09a3b3dd-f746-4e6e-b684-76a9bde0c78d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed3759c741b6f168bc67e8aef3e0b817595cfe4e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829066"
---
# <a name="winsat-mfmedia"></a>winsat mfmedia



비디오 디코딩 (재생) 미디어 파운데이션 프레임 워크를 사용 하 여 성능을 측정 합니다.

이 명령을 사용하는 방법의 예는 [예](#BKMK_examples)를 참조하세요.

## <a name="syntax"></a>구문

```
winsat mfmedia <parameters>
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|----------|-----------|
|-입력 \<파일 이름 >|필수: 비디오 클립을 재생 하거나 인코딩할 수를 포함 하는 파일을 지정 합니다. 미디어 파운데이션 렌더링 될 수 있는 모든 형식에는 파일 수 있습니다.|
|-dumpgraph|필터 그래프 평가 시작 하기 전에 GraphEdit 호환 파일에 저장 해야 지정 합니다.|
|-ns|필터 그래프는 입력된 파일의 일반 재생 시 속도로 실행 되도록 지정 합니다. 기본적으로 필터 그래프는 프레젠테이션 번 무시 하 고 최대한 빠른 속도로 실행 됩니다.|
|-재생|실행의 평가 모드 앤 플레이에 지정 된 파일에서 오디오 콘텐츠를 제공 된 모든 디코딩 **-입력** 기본 DirectSound 장치를 사용 합니다. 오디오 재생은 기본적으로 비활성화 됩니다.|
|-nopmp|Media Foundation 보호 된 미디어 파이프라인 (MFPMP)를 사용 하지 않게 프로세스 평가 하는 중입니다.|
|-pmp|항상 활용는 MFPMP 프로세스 평가 하는 중입니다.</br>참고: **-pmp** 또는 **-nopmp** 를 지정 하지 않으면 필요한 경우에만 MFPMP가 사용 됩니다.|
|-v|상태 및 진행률 정보를 포함 하 여 STDOUT로 자세한 출력을 보냅니다. 모든 오류는 명령 창에도 기록 됩니다.|
|-xml \<파일 이름 >|지정 된 XML 파일로 평가의 출력을 저장 합니다. 지정 된 파일이 있으면 덮어씁니다.|
|-idiskinfo|실제 볼륨과 논리 디스크에 대 한 정보를 XML 출력의 **\<SystemConfig >** 섹션의 일부로 저장 합니다.|
|-iguid|XML 출력 파일의 전역 고유 식별자 (GUID)를 만듭니다.|
|-참고 참고 텍스트|XML 출력 파일의 **\<note >** 섹션에 메모 텍스트를 추가 합니다.|
|-icn|XML 출력 파일에 로컬 컴퓨터 이름을 포함 합니다.|
|-eef|XML 출력 파일에 대 한 추가 시스템 정보를 열거 합니다.|

## <a name="examples"></a><a name=BKMK_examples></a>예와

- 동안 사용 되는 입력된 파일과 함께 평가 실행 하는 다음 예제는 **winsat 정식** 는 Media Foundation 보호 된 미디어 파이프라인 (MFPMP), 여기서 c:\windows는 Windows 폴더의 위치는 컴퓨터에서 사용 하지 않고 평가 합니다.  
  ```
  winsat mfmedia -input c:\windows\performance\winsat\winsat.wmv -nopmp
  ```

## <a name="remarks"></a>주의

-   로컬 Administrators 그룹 또는 이와 동등한 그룹의 구성원은 사용 하는 데 필요한 최소 **winsat**합니다. 이 명령은 관리자 권한 명령 프롬프트 창에서 실행 되어야 합니다.
-   관리자 권한 명령 프롬프트 창을 열려면 클릭 **시작**, 클릭 **액세서리**, 를 마우스 오른쪽 단추로 클릭 **명령 프롬프트**, 클릭 하 고 **관리자 권한으로 실행**합니다.

## <a name="additional-references"></a>추가 참조

