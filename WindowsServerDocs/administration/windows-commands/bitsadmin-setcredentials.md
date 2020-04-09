---
title: bitsadmin setcredentials
description: 작업에 자격 증명을 추가 하는 bitsadmin setcredentials에 대 한 Windows 명령 항목입니다.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3cd099a4-9e85-46d8-8527-edb6dfab7f97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 918bda93407e029cedaaf5eab937d1bb23dc3c4c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849646"
---
# <a name="bitsadmin-setcredentials"></a>bitsadmin setcredentials

작업에 자격 증명을 추가 합니다.

**BITS 1.2 및 이전 버전**: 지원 되지 않습니다.

## <a name="syntax"></a>구문

```
bitsadmin /SetCredentials <Job> <Target> <Scheme> <Username> <Password>
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------|-----------|
|작업|작업의 표시 이름 또는 GUID|
|대상|서버 또는 프록시|
|Scheme|다음 중 하나</br>-BASIC-사용자 이름과 암호가 일반 텍스트로 서버나 프록시로 전송 되는 인증 체계입니다.</br>-다이제스트-챌린지에 대해 서버 지정 데이터 문자열을 사용 하는 챌린지-응답 인증 체계입니다.</br>-NTLM-Windows 네트워크 환경에서 인증을 위해 사용자의 자격 증명을 사용 하는 챌린지-응답 인증 체계입니다.</br>-NEGOTIATE (단순 및 보호 된 협상 프로토콜 (Snego)이 라고도 함)는 인증에 사용할 체계를 결정 하기 위해 서버 또는 프록시와 협상 하는 챌린지-응답 인증 체계입니다. 이러한 예로는 Kerberos 프로토콜 및 NTLM이 있습니다.</br>-PASSPORT-Microsoft에서 제공 하는 중앙 집중식 인증 서비스로, 구성원 사이트에 대 한 단일 로그온을 제공 합니다.|
|Username|제공 된 자격 증명의 이름입니다.|
|Password|제공 된 *사용자 이름과* 연결 된 암호입니다.|

## <a name="examples"></a><a name=BKMK_examples></a>예와

다음 예에서는 이름이 *Mydownloadjob*인 작업에 자격 증명을 추가 합니다.
```
C:\>bitsadmin /RemoveCredentials myDownloadJob SERVER BASIC Edward Password20
```

## <a name="additional-references"></a>추가 참조

- [명령줄 구문 키](command-line-syntax-key.md)