---
title: Mac에서 원격 데스크톱에 대 한 새로운 기능
description: Mac에 대 한 원격 데스크톱 클라이언트에 최근 변경 사항에 알아보기
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 03/06/2019
ms.localizationpriority: medium
ms.openlocfilehash: 11da8bc333da7f44b2732266837d2df216142f85
ms.sourcegitcommit: 971f6538e8d89af84ef50fc8aab2188bdf6f47cb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2019
ms.locfileid: "9279124"
---
# <a name="whats-new-for-the-remote-desktop-client-on-macos"></a>MacOS에서 원격 데스크톱 클라이언트에 대 한 새로운?

[MacOS에 대 한 원격 데스크톱 클라이언트](remote-desktop-mac.md), 새로운 기능을 추가 하 고 문제를 해결 정기적으로 업데이트 합니다. 아래 최신 업데이트를 확인 합니다.

문제가 발생 하는 경우 항상 통해 연락할 수 있습니다 us **gt_ 문제 보고서는 데 도움이 됩니다**.

## <a name="updates-for-version-10210"></a>10.2.10 버전에 대 한 업데이트
*게시 날짜: 3/30/2019*

- 이 릴리스에서 최근 macOS 10.14.4 업데이트로 인해 불안정을 해결 했습니다. NVIDIA 하드웨어를 사용 하는 서버에 의해 인코딩됩니다 AVC 코덱 데이터를 디코딩할 때 나타나는 mispaints 해결 합니다.

## <a name="updates-for-version-1029"></a>10.2.9 버전에 대 한 업데이트
*게시 날짜: 3/6/2019*

- 서버 리디렉션 때 발생할 수 있는 RD 게이트웨이 연결 문제를 해결 하는 것이 릴리스에서 배치 합니다.
- 또한 주소가 지정 하는 10.2.8 인해 발생 하는 RD 게이트웨이 회귀 업데이트 합니다.

## <a name="updates-for-version-1028"></a>10.2.8 버전에 대 한 업데이트
*게시 날짜: 3/1/2019*

- RD 게이트웨이 사용할 때 표시 되는 연결 문제를 해결 합니다.
- 연결할 때 표시 된 경고를 잘못 된 인증서를 고정된 합니다.
- 어디에서 메뉴 모음과 dock 불필요 하 게 숨기 원격 앱을 시작할 때 경우에 따라 해결 방법입니다.
- 주소 충돌 하는 일부 사용자 시키는 된 정지 클립보드 리디렉션 코드를 수정 합니다.
- 연결 센터 스크롤해야 불필요 하 게 연결을 시작할 때 발생 하는 버그가 수정 합니다.

## <a name="updates-for-version-1027"></a>10.2.7 버전에 대 한 업데이트
*게시 날짜: 2/6/2019*

- 이 릴리스에서 AVC444 모드를 사용 하 여 때 나타나는 그래픽 mispaints (서버 인코딩 문제로 인해) 해결 했습니다.

## <a name="updates-for-version-1026"></a>10.2.6 버전에 대 한 업데이트
*게시 날짜: 1/28/2019*

- 현재 버전의 Windows 10에 연결할 때 사용할 수 있습니다 (420 및 444) AVC 코덱에 대 한 지원이 추가 되었습니다.
- 창 모드에 맞게에서 창 새로 고침 지금 바로 뒤에 나오는 올바른 보간 수준에서 해당 콘텐츠를 위해 크기 조정 렌더링 됩니다.
- 일부 사용자에 대 한 중복 피드 헤더를 발생 시킨 레이아웃 버그를 수정 합니다.
- 응용 프로그램 기본 설정 UI를 정리 합니다.
- 추가/편집 데스크톱 UI 세련 합니다.
- 많은 조정 및 조정 데스크톱 및 피드 연결 센터 타일 및 목록 보기를 완료 했습니다.

>[!NOTE]
>버그가 macOS 10.14.0 및 10.14.1 ".com.microsoft.rdc.application-data_SUPPORT/_EXTERNAL_DATA"을 초래할 수 있는 폴더 (여러 번 ~/Library 폴더 내에 중첩 된)에 많은 양의 디스크 공간을 사용 하도록 합니다. 이 문제를 해결 하려면 폴더 콘텐츠를 삭제 하 고 macOS 10.14.2로 업그레이드 합니다. Note 폴더의 내용을 삭제의 부작용은 책갈피에 할당 된 스냅숏 이미지는 삭제 됩니다. 원격 PC에 다시 연결할 때 이러한 이미지를 다시 생성 됩니다.

## <a name="updates-for-version-1024"></a>10.2.4 버전에 대 한 업데이트
*게시 날짜: 12/18/2018*

- MacOS Mojave 10.14 어둠 모드 지원을 추가 했습니다.
- 이제 Microsoft 원격 데스크톱 8에서 가져올 수 있는 옵션이 비어 있는 경우 연결 중앙에 표시 됩니다.
- 폴더 리디렉션 일부 타사 엔터프라이즈 응용 프로그램 호환성을 해결 합니다.
- 여기서 사용자 된 오류가 발생 한 0x30000069 원격 데스크톱 게이트웨이 보안으로 인해 프로토콜 대체 문제 문제를 해결 합니다.
- 창 모드를 사용 하 여 발생 하는 일부 사용자가 고정된 점진적 렌더링 문제 들어갑니다.
- 버그를 방해 하는 고정 파일 복사 및 붙여넣기에서 최신 버전의 파일을 복사 합니다.
- 작은 스크롤 델타에 대 한 스크롤 마우스 기반 향상 되었습니다.

## <a name="updates-for-version-1023"></a>10.2.3 버전에 대 한 업데이트
*게시 날짜: 11/06/2018*

- 원격 앱 시나리오에 대 한 "remoteapplicationcmdline" RDP 파일 설정에 대 한 지원이 추가 되었습니다.
- 세션 창의 제목 RDP 파일 (및 서버 이름)의 이름을 포함 RDP 파일에서 시작 합니다.
- 보고 된 RD 게이트웨이 성능 문제를 해결 합니다.
- 고정된 보고 된 RD 게이트웨이 충돌합니다.
- RD 게이트웨이 통해 연결할 때 연결 중단는 여기서 문제 해결 되었습니다.
- 전체 화면에서 메뉴 모음과 dock 지능적으로 숨김으로써 원격 앱의 더 나은 처리 합니다.
- 시작 된 후 원격 앱 숨겨진 남아 시나리오를 고정 합니다.
- 사용 하지 않도록 설정 하는 하드웨어 가속을 사용 하 여 "창에 맞추기"를 사용 하는 경우 느린 렌더링 업데이트를 처리 합니다.
- 클라이언트가 시작 될 때 잘못 된 권한으로 인 한 데이터베이스 만들기 오류를 처리 합니다. 
- 문제 해결 클라이언트 있던 시작 시 일관 되 게 충돌이 발생 하 고 일부 사용자에 대 한 시작 되지 않습니다.
- 여기서 연결 올바르게 가져온 하지 원격 데스크톱 8에서 전체 화면으로 시나리오를 수정 합니다.

## <a name="updates-for-version-1022"></a>10.2.2 버전에 대 한 업데이트
*게시 날짜: 10/09/2018*

- 지 원하는 새 연결 센터 끌어서 놓기, 데스크톱, 목록 보기 모드, 열 기반 정렬 및 간단한 그룹 관리의 크기를 조정할 수 열 수동 배치 합니다.
- 연결 센터 이제 기억 마지막 활성 피벗 (데스크톱 또는 피드) 때 앱을 닫으면 합니다.
- UI와 흐름을 확인 하는 자격 증명 전체적으로 개선 합니다.
- RD 게이트웨이 피드백 이제 연결 상태 UI의 일부입니다.
- 버전 8 클라이언트에서 설정 가져오기 향상 되었습니다.
- RDP 파일을 가리키는 RemoteApp 끝점 이제 연결 센터로 가져올 수 있습니다.
- 단일 모니터 원격 데스크톱 시나리오에 대 한 망막 디스플레이 최적화 합니다.
- (흐린 영향)는 그래픽 보간 수준을 지정 하는 것에 대 한 지원을 망막 최적화를 사용 하지 않음.
- Windows 2000에 대 한 연결을 사용 하도록 설정 하려면 256 색 지원 합니다.
- Windows 7, Windows Server 2008 R2 연결할 때 화면 오른쪽 및 아래쪽 가장자리 클리핑 및 이전 버전을 고정 합니다.
- 파일을 첨부 파일로 추가 이제 Outlook (원격 세션에서 실행)로 로컬 파일을 복사 합니다.
- 네트워크 공유에서 파일 생성 된 경우 지 기반 파일 전송 저하 된는 문제가 해결 되었습니다.
- (원격 세션에서 실행) Excel로 리디렉션된 폴더에 있는 파일을 저장할 때 응답을 유발 하는 버그를 해결 합니다.
- 공간이 리디렉션된 폴더에 대 한 보고를 유발 하는 문제를 해결 합니다.
- MacOS 10.14에 너무 많은 디스크 저장소를 사용 하도록 미리 보기를 발생 시킨 버그를 해결 합니다.
- RD 게이트웨이 장치 리디렉션 정책을 적용 하기 위한 지원이 추가 되었습니다.
- RD 게이트웨이 사용 하 여 연결에서 연결을 해제할 때 세션 창을 닫는 못하도록 하는 문제가 해결 되었습니다.
- 네트워크 수준 인증 (NLA) 서버에 의해 적용 하지 않으며, 경우 하면 이제 라우팅될 로그인 화면에 암호 만료 된 경우.
- 때 표시 되는 성능 문제를 해결 많은 양의 데이터 네트워크를 통해 전송 되 고 있습니다.
- 스마트 카드 리디렉션 해결합니다.
- 지원 "EnableCredSspSupport" 및 "인증 수준은"의 모든 가능한 값에 대 한 RDP 파일 설정 ClientSettings.EnforceCredSSPSupport 사용자 기본 키 (com.microsoft.rdc.macos 도메인)에서 0으로 설정 합니다.
- NLA 하지 협상할 때 "에 대 한 자격 증명으로 클라이언트에서 확인" RDP 파일 설정에 대 한 지원 합니다.
- 스마트 카드 리디렉션 NLA 협상 되지 Winlogon 프롬프트를 통해 스마트 카드 기반 로그인에 대 한 지원 합니다.
- URL에는 공백이 포함 된 리소스 피드 다운로드를 방해 하는 문제가 해결 되었습니다.

## <a name="updates-for-version-1021"></a>10.2.1 버전에 대 한 업데이트
*게시 날짜: 08/06/2018*

- 활성화 된 연결을 Azure Active Directory (AAD) 가입 Pc입니다. 에 연결 하는 AAD에 가입 PC, 사용자 이름 다음 형식 중 하나에 있어야 합니다.: "AzureAD\user" 또는 "AzureAD\user@domain"입니다.
- 원격 세션에서 스마트 카드의 사용에 영향을 주는 일부 버그를 해결 합니다.

## <a name="updates-for-version-1020"></a>10.2.0 버전에 대 한 업데이트
*게시 날짜: 07/24/2018*

- GDPR 규정 준수에 대 한 업데이트를 포함된 합니다.
- MicrosoftAccount\username@domain이제는 유효한 사용자 이름으로 허용 됩니다.
- 공유 클립보드 재작성 빨라야 및 더 많은 형식을 지원 합니다.
- 복사 및 붙여넣기 텍스트, 이미지 또는 이제 세션 간에 파일은 로컬 컴퓨터의 클립보드를 무시 합니다.
- (경고 프롬프트를 수락 하면) 하는 경우 신뢰할 수 없는 인증서로 RD 게이트웨이 서버를 통해 연결할 수 있습니다.
- 메탈 하드웨어 가속 지원) (여기서 렌더링 속도 및 배터리 사용을 최적화 이제 사용 됩니다.
- 작동 하려면 몇 가지 하려고 노력 메탈 하드웨어 가속을 사용 하 여 세션 그래픽 선명 하 게 표시 됩니다.
- 닫히는 후 windows 현상을 있는 경우에 따라 제거 합니다.
- 일부 시나리오에서는 RemoteApp 프로그램의 실행을 차단 된 수정 된 버그
- 0x204 오류가 발생 된 RD 게이트웨이 채널 동기화 오류를 해결 합니다.
- 이제 마우스 커서 모양 세션이 나 RemoteApp 창을 벗어날 때 올바르게 업데이트 합니다.
- 데이터 손실을 유발 하는 폴더 리디렉션 버그 수정 때 복사 및 붙여넣기 폴더.
- 폴더 크기의 잘못 된 보고를 발생 시킨 폴더 리디렉션 문제가 해결 되었습니다.
- 로컬 계정을 사용 하는 AAD에 가입 된 컴퓨터에 로그인 하지 못하게 된 성능이 저하를 고정 합니다.
- 세션 창의 내용을 잘릴 수를 유발 하는 수정 된 버그입니다.
- 타원 곡선 비대칭 키를 포함 하는 RD 끝점 인증서에 대 한 지원이 추가 되었습니다.
- 일부 시나리오에서는 관리 되는 리소스의 다운로드 하지 못하게 된 버그를 수정 합니다.
- 고정 된 연결 중앙 클리핑 문제를 해결 합니다.
- 함께 원활 하 게 작동 하는 디스플레이 속성 시트에서 확인란을 수정 합니다.
- 가로 세로 비율 잠금 동적으로 표시 된 변경 적용 될 때 비활성화 되었습니다.
- F5 인프라와의 호환성 문제를 해결 합니다.
- 연결 시 올바른 메시지가 표시 되는지 확인 빈 암호 처리를 업데이트 합니다.
- 고정된 마우스 스크롤 MapInfra Pro와의 호환성 문제입니다.
- Mojave에서 실행할 경우 몇 가지 맞춤 문제 연결 중앙에 고정 합니다.

## <a name="updates-for-version-1018"></a>10.1.8 버전에 대 한 업데이트
*게시 날짜: 05/04/2018*

- 세션 창 크기를 조정 하 여 원격 해상도 변경에 대 한 지원이 추가 되었습니다!
- 원격 리소스 다운로드 피드 고정된 시나리오는 과도 하 게 오랜 시간이 걸립니다.
- CredSSP 암호화 oracle 시정 업데이트 (c v E-2018-0886)와 패치되지 않은 서버에 연결할 때 발생할 수 있는 0x207 오류를 해결 합니다.

## <a name="updates-for-version-1017"></a>10.1.7 버전에 대 한 업데이트
*게시 날짜: 04/05/2018*

- C v E-2018-0886에 설명 된 대로 CredSSP 암호화 oracle 시정 업데이트를 통합 하는 보안 수정을 했습니다.
- 향상 된 RemoteApp 아이콘 및 마우스 커서 렌더링 보고 된 mispaints 해결 하기 위해 합니다.
- RemoteApp windows 연결 센터 뒤에 표시 되는 위치 문제에 설명 합니다.
- 원격 데스크톱 8에서 가져온 후 로컬 리소스를 변경할 때 발생 한 문제를 해결 합니다.
- 이제 데스크톱 타일에 ENTER 키를 눌러 연결을 시작할 수 있습니다.
- 전체 화면 보기에 있을 때 CMD + M 이제 올바르게 매핑됩니다 WIN + M.
- 이제 연결 센터, 기본 설정 및에 대 한 windows CMD + M을 응답합니다.
- 이제 피드 **원격 리소스 추가** 페이지에서 ENTER 키를 눌러 검색을 시작할 수 있습니다.
- 새로 고친 후 새 원격 리소스 피드까지 연결 센터에서 빈 확신이 있는 문제를 해결 합니다.
 
## <a name="updates-for-version-1016"></a>10.1.6 버전에 대 한 업데이트
*게시 날짜: 03/26/2018*

- 여기서 RemoteApp windows 자체 순서는 문제를 해결 합니다.
- 어떤 RemoteApp 창은 해당 부모 창 뒤 문제가 발생 하는 버그를 해결 합니다.
- 일부 RemoteApp 프로그램에 영향을 주는 마우스 포인터 오프셋된 문제를 해결 했습니다.
- 여기서 새 세션 창을 여는 대신 기존 세션을을 포커스를 지정한 새 연결을 시작 하는 문제가 해결 되었습니다.
- 오류 메시지가 나타나 오류 문제를 해결 했으므로-게이트웨이 찾을 수 없으면 올바른 메시지가 이제 표시 됩니다.
- 이제 종료 바로 가기 (⌘ + Q) UI에서 일관 되 게 표시 됩니다.
- "창에 맞게" 모드로 확장 때 이미지 품질을 개선 합니다.
- 원격 세션에 표시 하려면 홈 폴더의 여러 인스턴스를 발생 시킨 회귀를 고정 합니다.
- 기본 아이콘 데스크톱 타일을 업데이트 했습니다.