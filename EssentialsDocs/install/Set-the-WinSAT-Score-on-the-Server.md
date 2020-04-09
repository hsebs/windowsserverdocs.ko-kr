---
title: 서버에서 WinSAT 점수 설정
description: Windows Server Essentials를 사용 하는 방법을 설명 합니다.
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 911dc494-0f8f-4723-93d6-2106f914b906
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2f469f902f28642890723552ac460e844281c7b8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80819836"
---
# <a name="set-the-winsat-score-on-the-server"></a>서버에서 WinSAT 점수 설정

>적용 대상: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

비디오 스트리밍 해상도를 최적화 하려면 Windows Server Essentials 운영 체제를 실행 하는 서버에 대 한 WinSAT CPU 점수를 설정 해야 합니다. 이 작업은 WinSAT 점수 정보가 포함된 .xml 파일을 만들고 설치하여 수행합니다.  
  
## <a name="obtain-the-winsat-cpu-score"></a>WinSAT CPU 점수 얻기  
 WinSAT CPU 점수를 검색하고 해당 정보를 운영 체제에서 읽는 WinServerSAT.xml 파일에 넣는 WinServerSAT.exe 프로그램이 OPK와 함께 제공됩니다.  
  
#### <a name="to-obtain-the-winsat-cpu-score"></a>WinSAT CPU 점수를 얻으려면  
  
1. ADK 미디어의 Resources\WinServerSAT\\*를 참조 컴퓨터에 복사 합니다.  
  
2. 참조 컴퓨터에서 관리자 권한으로 명령 프롬프트 창을 엽니다.  
  
3. %ProgramFiles%\Windows Server\Bin\OEM 폴더가 존재하지 않는 경우 다음 명령을 입력하고 Enter 키를 누릅니다.  
  
    **mkdir "%ProgramFiles%\Windows Server\bin\oem 폴더가"**  
  
4. 다음 명령을 입력하고 Enter 키를 누릅니다.  
  
    **WinServerSAT "%ProgramFiles%\Windows Server\Bin\OEM\WinServerSAT.xml"**  
  
   다음 예는 만들어진 WinServerSAT.xml 파일의 XML 내용을 보여줍니다.  
  
```  
  
<?xml version="1.0" encoding="UTF-16"?>  
<WinSAT>  
   <CpuScore description="WinSAT CPU score">WinSAT_Score</CpuScore>  
</WinSAT>  
```  
  
 여기서 *WinSAT_Score*는 서버에서 검색한 값으로 바뀝니다.  
  
> [!IMPORTANT]
>  이미지를 캡처하려면 참조 컴퓨터에서 WinServerSAT.exe, winsat.prx, winsat.wmv 및 WinSATEncode.wmv 파일을 제거해야 합니다.
