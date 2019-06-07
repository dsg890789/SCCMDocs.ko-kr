---
title: CMTrace
titleSuffix: Configuration Manager
description: CMTrace를 사용하여 Configuration Manager에 대한 로그 파일을 보는 방법을 살펴봅니다.
ms.date: 05/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6a4a3290-5228-4871-918a-554aa1c20834
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 332cdf00256ccfbac07b352c22b232edd4ba9363
ms.sourcegitcommit: 7dd42b5a280e64feb69a947dae082fdaf1571272
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66716161"
---
# <a name="cmtrace"></a>CMTrace

*적용 대상: System Center Configuration Manager(현재 분기)*

CMTrace는 [Configuration Manager 도구](/sccm/core/support/tools) 중 하나입니다. 이 도구로 다음 형식을 포함한 로그 파일을 보고 모니터할 수 있습니다.  

- Configuration Manager 또는 CCM(Client Component Manager) 형식의 로그 파일  

- 일반 ASCII 또는 유니코드 텍스트 파일(예: Windows Installer 로그)  

이 도구에서는 강조 표시, 필터링 및 오류 조회를 통해 로그 파일을 분석할 수 있습니다.

1806 버전부터 이제 CMTrace 로그 보기 도구가 Configuration Manager 클라이언트와 함께 자동으로 설치됩니다. 이 도구는 기본적으로 `%WinDir%\CCM\CMTrace.exe`인 클라이언트 설치 디렉터리에 추가됩니다.<!--1357971-->

> [!Note]  
> CMTrace는 .log 파일 확장명을 열도록 Windows에 자동으로 등록되지 않습니다. 자세한 내용은 [파일 연결](#file-associations)을 참조하세요.  



## <a name="usage"></a>용도

**CMTrace.exe**를 실행합니다. 처음 도구를 실행하면 파일 연결을 위한 프롬프트가 표시됩니다. 자세한 내용은 [파일 연결](#file-associations)을 참조하세요.

다음 메뉴에서 대부분의 CMTrace 작업을 수행합니다.
- [File](#file-menu)
- [도구](#tools-menu)


### <a name="file-menu"></a>파일 메뉴

**파일** 메뉴에서는 다음 작업을 사용할 수 있습니다.  
- [열기](#open)
- [서버에서 열기](#open-on-server)
- [인쇄](#print)
- [기본 설정](#preferences)

파일 메뉴에는 최근 8개 파일도 나열됩니다. 파일 메뉴에서 이 항목을 선택하면 로그 중 하나를 신속하게 다시 열 수 있습니다. 

#### <a name="open"></a>열기
로그 파일을 찾아보기 위한 열기 대화 상자를 표시합니다. 

다음 형식의 파일 보기를 필터링합니다. 
- 로그 파일(\*.log)  
- 기존 로그 파일(\*.lo_) 
- 모든 파일(\*.\*)

다음 두 옵션은 기본적으로 선택되지 않습니다.  

- **기존 줄 무시**: 이 옵션을 선택하면 CMTrace가 선택한 로그 파일의 기존 콘텐츠는 무시하고 추가되는 새 줄만 표시합니다. 전체 로그 파일 기록이 필요하지 않을 때는 이 옵션을 사용하여 새 작업만 모니터링합니다.  

- **선택한 파일 병합**: 이 옵션을 사용하도록 선택하고 여러 로그 파일을 선택하면 CMTrace가 선택한 로그를 보기에 병합합니다. 단일 로그 파일처럼 표시됩니다. 병합된 로그는 똑같이 업데이트되며 한 로그 파일인 것처럼 모든 다른 CMTrace 기능을 지원합니다.  


#### <a name="open-on-server"></a>서버에서 열기
표준 찾아보기 대화 상자로 사이트 시스템 컴퓨터의 Configuration Manager 로그 폴더를 찾습니다. 또한 원격 컴퓨터에 대한 네트워크를 탐색할 수도 있습니다.   

탐색할 원격 컴퓨터를 선택하면 CMTrace가 Configuration Manager 공유를 확인합니다. Configuration Manager 로그 파일 공유가 없으면 오류 메시지를 표시합니다.  

탐색 없이 알려진 컴퓨터에 직접 연결하려면 [열기](#open) 작업을 사용합니다. 그런 다음, UNC 형식으로 서버 이름과 공유를 입력합니다.

#### <a name="print"></a>인쇄
표준 Windows 인쇄 대화 상자를 표시합니다. 이 작업은 현재 로그 파일을 프린터로 보냅니다. CMTrace 기본 설정의 인쇄 탭의 설정에 따라 출력 형식을 지정합니다.

#### <a name="preferences"></a>기본 설정
CMTrace의 설정을 구성합니다. 다음 옵션을 사용할 수 있습니다.  

- **일반** 탭  

     - **업데이트 간격**: CMTrace가 로그 파일에 대한 변경 내용을 확인하고 새 줄을 로드하는 간격을 제어합니다. 이 값은 기본적으로 500밀리초입니다.  

     - **강조 표시**: 선택한 로그 줄을 강조 표시할 때 CMTrace가 사용하는 색을 설정합니다. 기본적으로 이 색은 기본 노랑(빨강:  255, 녹색:  255, 파랑:  0)입니다.  

     - **열**: 로그 보기에 표시되는 열과 표시 순서를 구성합니다. 기본적으로 로그 텍스트, 구성 요소, 날짜/시간 및 스레드를 표시합니다.  

- **인쇄** 탭  

     - **열**: 로그 파일을 인쇄할 때 사용하는 열과 표시 순서를 구성합니다. 기본적으로 표시되는 것과 같은 열을 인쇄합니다.  

     - **방향**: 로그 파일을 인쇄할 때 기본 인쇄 방향을 설정합니다. 인쇄 대화 상자에서 이 설정을 재정의합니다. 기본적으로 세로 방향을 사용합니다.  
 
- **고급** 탭  

     - **새로 고침 간격**:  CMTrace가 많은 줄을 로드할 때 지정된 간격으로 로그 보기를 강제 업데이트합니다. 기본적으로 이 옵션은 0 값을 통해 사용하지 않게 설정됩니다.  

        > [!Note]  
        > 일반적으로 **새로 고침 간격**은 수정하지 않습니다. 많은 로그 파일을 열 때 소요되는 시간이 크게 늘어날 수 있습니다. 


### <a name="tools-menu"></a>도구 메뉴
**도구** 메뉴에서는 다음 작업을 사용할 수 있습니다.  
- [찾기](#find)
- [다음 찾기](#find-next)
- [클립보드로 복사](#copy-to-clipboard)
- [강조 표시](#highlight)
- [필터](#filter)
- [오류 조회](#error-lookup)
- [일시 중지](#pause)
- [세부 정보 표시/숨기기](#showhide-details)
- [정보 창 표시/숨기기](#showhide-info-pane)

#### <a name="find"></a>찾기
지정된 텍스트 문자열을 열린 로그 파일에서 검색합니다.  

#### <a name="find-next"></a>다음 찾기
찾기 대화 상자에서 이전에 지정한 대로 다음 일치하는 문자열을 찾습니다.  

#### <a name="copy-to-clipboard"></a>클립보드로 복사
Windows 클립보드에 선택한 줄을 일반 텍스트로 복사합니다. Configuration Manager 및 CCM 로그 파일을 조사할 때는 보기와 같은 순서로 열을 복사합니다. 각 열 탭 문자로 구분합니다. 로그를 이메일 메시지나 다른 문서로 복사할 때 이 작업을 사용합니다.  

#### <a name="highlight"></a>강조 표시
CMTrace가 각 로그 항목의 텍스트를 검색하는 데 사용할 문자열을 입력합니다. 그러면 입력한 문자열과 일치하는 로그 텍스트를 강조 표시합니다.  

- 강조 표시에서는 기본 설정에서 지정한 색을 사용합니다.  

- 강조 표시를 해제하려면 이 필드에서 문자열을 지웁니다.  

- 10진수 또는 16진수를 입력하면 CMTrace가 이 값을 스레드 열과 대조합니다. 이 동작을 통해 상호 작용할 수 있는 다른 스레드를 필터링하지 않고 단일 스레드의 처리를 강조 표시합니다.  

- 문자열의 대/소문자를 비교하려면 **대/소문자 구분** 옵션을 사용하도록 설정합니다.  
 
#### <a name="filter"></a>필터
지정 기준에 따라 로그 줄을 표시하거나 숨깁니다. 표시 여부에 관계없이 4개 열 중 어디에나 필터를 적용합니다. 이 설정은 열린 로그 파일 각각에 적용됩니다. 

예제:
<!--SCCMDocs issue #603-->
- "작업" 또는 "그룹"을 포함하는 입력 텍스트를 **smsts.log**에서 필터링합니다. 
- "대상"을 포함하는 입력 텍스트**를 InventoryAgent.log**에서 필터링합니다.


#### <a name="error-lookup"></a>오류 조회
10진수 또는 16진수로 오류를 입력하거나 붙여 넣어 설명을 표시합니다. 가능한 오류 소스는 Windows, WMI 또는 Winhttp 등입니다.

#### <a name="pause"></a>일시 중지
로그 모니터링을 일시 중단하거나 다시 시작합니다. 이 작업을 사용하는 가능한 원인에는 다음 사용 사례가 있습니다.  

- CMTrace가 로그 파일 정보를 너무 빠르게 표시할 경우  

- 로그 모니터링을 일시 중지할 때 현재 파일이 새 로그로 롤오버되는 경우 CMTrace가 표시하는 정보가 사라지지 않음  

- 로그 파일을 조사하는 도중에 CMTrace가 새 데이터를 표시하지 않게 하려는 경우  

#### <a name="showhide-details"></a>세부 정보 표시/숨기기
로그 텍스트 이외의 모든 열을 표시하거나 숨깁니다. 로그 텍스트 열을 창 너비만큼 확대하기도 합니다. 낮은 디스플레이 해상도의 컴퓨터에서 로그를 볼 때 이 작업을 사용합니다. 로그 텍스트를 자세히 표시합니다.  

> [!Note]   
> 일반 텍스트 파일을 볼 때는 항상 비어 있으므로 CMTrace가 자동으로 세부 정보를 숨깁니다.  
 
#### <a name="showhide-info-pane"></a>정보 창 표시/숨기기
정보 창을 표시하거나 숨깁니다. 낮은 디스플레이 해상도의 컴퓨터에서 로그를 볼 때 이 작업을 사용합니다. 자세한 로깅 세부 정보를 표시합니다.  



## <a name="log-pane"></a>로그 창

로그 창은 CMTrace 창의 맨 위에 있습니다. 로그 파일의 줄을 표시합니다. 

줄을 선택하면 Windows 선택 영역 색 구성표를 사용하여 일시적으로 강조 표시됩니다. 

강조 표시된 줄은 **도구** 메뉴의 **강조 표시** 옵션을 사용하여 정의한 기준과 일치합니다. 강조 표시에서는 **기본 설정**에서 지정한 색을 사용합니다.

CMTrace는 빨강 배경과 노랑 텍스트 색을 사용하여 오류가 있는 줄을 표시합니다. CCM 형식 로그에서 로그 항목에는 항목이 오류임을 나타내는 명시적 형식 값이 있습니다. 다른 로그 형식에서 CMTrace는 각 항목에서 대/소문자를 구분하지 않는 검색을 수행하여 "오류"와 일치하는 모든 텍스트 문자열을 찾습니다.

경고가 있는 줄은 노란 배경을 사용하여 표시합니다. CCM 형식 로그에서 로그 항목에는 항목이 경고임을 나타내는 명시적 형식 값이 있습니다. 다른 로그 형식에서 CMTrace는 각 항목에서 대/소문자를 구분하지 않는 검색을 수행하여 "경고"와 일치하는 모든 텍스트 문자열을 찾습니다.



## <a name="info-pane"></a>정보 창

정보 창은 CMTrace 창의 맨 아래에 있습니다. 이 관리 팩에는 다음과 같은 기능이 포함되어 있습니다.   

- 현재 선택한 로그 항목에 대한 세부 정보  

- 로그 텍스트를 표시하는 텍스트 상자  

- 서식 있는 텍스트를 쉽게 읽을 수 있도록 캐리지 리턴 표시  

- 로그 창에 완전히 표시되지 않는 긴 항목을 읽기 쉽게  

**도구** 메뉴의 **정보 창 표시/숨기기** 옵션으로 정보 창을 표시하거나 숨깁니다. 정보 창이 로그 창의 반 초과를 차지하게 되면 CMTrace가 자동으로 숨깁니다.


### <a name="progress-bar"></a>진행률 표시줄

로그 파일을 처음 열면 CMTrace가 정보 창을 진행률 표시줄로 바꿉니다. 이 진행률은 로드한 기존 파일 콘텐츠의 크기를 표시합니다. 진행률이 100%에 도달하면 CMTrace가 진행률 표시줄을 제거하고 정보 창을 표시합니다. 큰 파일을 로드할 때 이 동작은 로드가 얼마나 긴지를 표시합니다.


### <a name="status-bar"></a>상태 표시줄

Configuration Manager 형식 및 CCM 형식 로그 파일의 경우 상태 표시줄이 선택한 로그 항목의 소요 시간을 표시합니다. 단일 항목을 선택하면 도구가 최초 로그 항목부터 선택된 항목까지의 시간을 표시합니다. 여러 항목을 선택하면 최상위 선택 항목에서 최하위 선택 항목까지의 시간을 계산합니다. CMTrace는 이 정보의 서식을 다음과 같이 지정합니다.

`Elapsed time is <hours>h <minutes>m <seconds>s <milliseconds>ms (<seconds+milliseconds> seconds)`



## <a name="windows-shell-integration"></a>Windows 셸 통합

CMTrace는 [파일 연결](#file-associations) 및 [끌어서 놓기](#drag-and-drop)를 지원합니다.


### <a name="file-associations"></a>파일 연결 

CMTrace는 .log 및 .lo_ 파일 확장자와 스스로를 연결할 수 있습니다. 프로그램을 시작할 때 레지스트리를 검사하여 이 파일 이름 확장명이 이미 연결되었는지 판단합니다. CMTrace에 연결된 파일 이름 확장명이 없으면 파일 이름 확장명을 CMTrace에 연결하라는 프롬프트가 표시됩니다. **이 메시지를 다시 표시 안 함**을 선택하면 CMTrace가 이 컴퓨터에서는 실행할 때마다 이 검사를 건너뜁니다.


### <a name="drag-and-drop"></a>끌어서 놓기

CMTrace는 기본 끌어서 놓기 기능을 지원합니다. Windows 탐색기에서 로그 파일을 끌어서 CMTrace에 놓아 엽니다.



## <a name="other-tips"></a>기타 팁

### <a name="last-directory-registry-key"></a>마지막 디렉터리 레지스트리 키
<!--511280-->
기본적으로 CMTrace는 마지막에 연 로그 위치를 저장합니다. 이 동작은 매번 로그 경로를 기본값으로 사용하는 사이트 서버에서 유용합니다. 

클라이언트에서 처음 실행하면 현재 작업 중인 디렉터리를 기본값으로 사용합니다. 이 위치는 CMTrace에서 저장한 경로이거나 `%userprofile%\Desktop` 같은 경로일 수 있습니다. 

레지스트리 키`HKEY_CURRENT_USER\Software\Microsoft\Trace32`의 **마지막 디렉터리** 값이 이 기본 위치를 제어합니다. 클라이언트에서 이 값을 `%windir%\CCM\Logs`로 설정하면 처음 실행할 때 CMTrace가 클라이언트 로그 위치에서 파일을 엽니다.


## <a name="see-also"></a>참고 항목

[로그 파일](/sccm/core/plan-design/hierarchy/log-files)
