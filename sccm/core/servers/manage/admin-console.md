---
title: Configuration Manager 콘솔
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔을 통해 이동에 대해 알아봅니다.
ms.date: 08/16/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 463ce307-59dd-4abd-87b8-42ca9db178d7
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 593a479c713df76d63090749ee45cb89aeb413e4
ms.sourcegitcommit: f7e4ff38d4b4afb49e3bccafa28514be406a9d7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549509"
---
# <a name="using-the-configuration-manager-console"></a>Configuration Manager 콘솔 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

관리자는 Configuration Manager 콘솔을 사용하여 Configuration Manager 환경을 관리합니다. 이 문서에서는 콘솔 탐색의 기본적인 사항을 다룹니다.  


## <a name="connect-to-a-site-server"></a>사이트 서버에 연결

콘솔은 중앙 관리 사이트 서버 또는 기본 사이트 서버에 연결합니다. Configuration Manager 콘솔을 보조 사이트에 연결할 수는 없습니다. [Configuration Manager 콘솔을 설치](/sccm/core/servers/deploy/install/install-consoles)할 수 있습니다. 설치하는 동안 콘솔이 연결하는 사이트 서버의 FQDN(정규화된 도메인 이름)을 지정했습니다.

다른 사이트 서버에 연결하려면 다음 단계를 사용합니다.

1. [리본](#ribbon) 메뉴의 맨 위에 있는 화살표를 선택하고 **새 사이트에 연결**을 선택합니다.  

    ![콘솔을 새 사이트에 연결](media/connect-to-a-new-site.png)  

2. 사이트 서버의 FQDN을 입력합니다. 이전에 사이트 서버에 연결한 경우 드롭다운 목록에서 서버를 선택합니다.  

    ![사이트 연결 창에서 사이트 서버의 FQDN을 입력합니다.](media/site-server-fqdn.png)  

3. **연결**을 선택합니다.  

1810 버전부터 관리자가 Configuration Manager 사이트에 액세스하는 데 필요한 최소 인증 수준을 지정할 수 있습니다. 이 기능은 관리자에게 필요한 수준으로 Windows에 로그인하도록 요구합니다. 자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_auth)을 참조하세요. <!--1357013-->  


## <a name="navigation"></a>탐색

콘솔의 일부 영역은 할당된 보안 역할에 따라 표시되지 않을 수 있습니다. 역할에 대한 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.

### <a name="workspaces"></a>작업 영역

Configuration Manager 콘솔에는 네 가지 **작업 영역**이 있습니다.  

- **자산 및 호환성**  

- **소프트웨어 라이브러리**  

- **모니터링**  

- **관리**  

![바로 가기 메뉴를 사용하는 Configuration Manager 작업 영역](media/configuration-manager-workspaces.png)  

아래쪽 화살표를 선택하고 **탐색 창 옵션**을 선택하여 작업 영역 단추를 다시 정렬합니다. **위로 이동**하거나 **아래로 이동**하도록 항목을 선택합니다. **다시 설정**을 선택하여 기본 단추 순서를 복원합니다.  

![작업 영역을 다시 정렬하기 위한 탐색 창 옵션 창](media/navigation-pane-options.png)  

**단추 수 줄이기**를 선택하여 작업 영역 단추를 최소화합니다. 목록의 마지막 작업 영역이 먼저 최소화됩니다. 최소화된 단추를 선택하고 **단추 수 늘리기**를 선택하면 단추가 원래 크기로 복원됩니다.

![Configuration Manager 콘솔의 최소화된 작업 영역](media/workspace-buttons.png)  

### <a name="nodes"></a>노드

작업 영역은 **노드**의 컬렉션입니다. 노드의 한 예제는 **소프트웨어 라이브러리** 작업 영역의 **소프트웨어 업데이트 그룹** 노드입니다.

노드에 있으면 화살표를 클릭하여 탐색 창을 최소화할 수 있습니다.  

![예제 노드 및 강조 표시된 최소화 화살표](media/software-update-groups-node.png)  

**탐색 모음**을 사용하여 탐색 창을 최소화했을 때 콘솔 주변을 이동할 수 있습니다.  

![Configuration Manager 최소화된 탐색 창](media/minimized-navigation-pane.png)  

콘솔에서 노드는 경우에 따라 폴더로 구성됩니다. 폴더를 선택하면 일반적으로 **탐색 인덱스** 또는 **대시보드**가 표시됩니다.  

![Configuration Manager 소프트웨어 업데이트 탐색 인덱스](media/software-updates-navigation-index.png)  

### <a name="ribbon"></a>리본

리본은 Configuration Manager 콘솔의 맨 위에 있습니다. 리본은 둘 이상의 탭을 가질 수 있으며 오른쪽에 있는 화살표를 사용하여 최소화될 수 있습니다. 리본의 버튼은 노드에 따라 변경합니다. 또한 리본의 단추 대부분은 바로 가기 메뉴에서 사용할 수 있습니다.  

![예제 리본 메뉴, 강조 표시된 여러 탭 및 최소화 화살표](media/ribbon.png)

### <a name="details-pane"></a>세부 정보 창

세부 정보 창을 검토하여 항목에 대한 추가 정보를 가져올 수 있습니다. 세부 정보 창은 하나 이상의 탭을 가질 수 있습니다. 탭은 노드에 따라 달라집니다.  

![Configuration Manager 예제 세부 정보 창](media/details-pane.png)

### <a name="columns"></a>열

열을 추가, 제거, 다시 정렬 및 크기 조정할 수 있습니다. 이러한 작업을 사용하여 원하는 데이터를 표시할 수 있습니다. 사용 가능한 열은 노드에 따라 달라집니다. 보기에서 열을 추가하거나 제거하려면 기존 열 제목을 마우스 오른쪽 단추로 클릭한 후, 항목을 선택합니다. 원하는 위치로 열 제목을 끌어 열을 다시 정렬합니다.  

![Configuration Manager 열 추가](media/add-columns.png)  

열 바로 가기 메뉴의 맨 아래에서 열별로 정렬하거나 그룹화할 수 있습니다. 또한 해당 헤더를 선택하여 열별로 정렬할 수 있습니다.  

![Configuration Manager에서 열별 그룹화](media/column-group-by.png)  


## <a name="bkmk_viewconnected"></a> 최근에 연결된 콘솔 보기

<!--3699367-->
1902 버전부터는 Configuration Manager 콘솔에 대한 가장 최근의 연결을 볼 수 있습니다. 보기에는 활성 연결 및 최근에 연결된 연결이 포함되어 있습니다. 항상 목록에 현재 콘솔 연결이 표시되고 Configuration Manager 콘솔로부터의 연결만 표시됩니다. SMS 공급자에 대한 PowerShell 또는 다른 SDK 기반 연결이 표시되지 않습니다. 사이트는 목록에서 30일 이상된 인스턴스를 제거합니다.

### <a name="prerequisites-to-view-connected-consoles"></a>연결된 콘솔을 보기 위한 필수 구성 요소

- 계정에 **SMS_Site** 개체에 대한 **읽기** 권한이 필요합니다.
- SMS 공급자 서버에 IIS 설치 <!---SCCMDocs-pr issue 1326-->
- SMS 공급자에서 인증서를 사용하도록 설정합니다.<!--SCCMDocs-pr issue 3135--> 다음 옵션 중 하나를 사용합니다.  

    - [향상된 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http) 사용(추천)
    - SMS 공급자 역할을 호스팅하는 서버의 IIS에 있는 443 포트에 PKI 기반 인증서를 수동으로 바인딩  

### <a name="view-connected-consoles"></a>연결된 콘솔 보기

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다.  

2. **보안**을 확장하고 **콘솔 연결** 노드를 선택합니다.  

3. 다음 속성을 사용하여 최근 연결을 봅니다.  

    - 사용자 이름
    - 머신 이름
    - 연결된 사이트 코드
    - 콘솔 버전
    - 마지막으로 연결된 시간: 사용자가 마지막으로 콘솔을 *연* 때

![Configuration Manager 콘솔 연결 보기](media/console-connections.png) 


## <a name="bkmk_notify"></a> Configuration Manager 콘솔 알림

<!--3556016, fka 1318035-->
Configuration Manager 1902 버전부터 콘솔에서 다음 이벤트를 알립니다.

- Configuration Manager 자체에 대한 업데이트를 사용할 수 있는 경우
- 환경에서 수명 주기 및 유지 관리 이벤트가 발생하는 경우

이 알림은 리본 아래의 콘솔 창의 맨 위에 있는 막대입니다. Configuration Manager 업데이트를 사용할 수 있는 경우 이전 환경을 대체합니다. 이러한 콘솔 내 알림은 여전히 중요한 정보를 표시하지만 콘솔에서 작업에 방해가 되지 않습니다. 중요한 알림을 해제할 수 없습니다. 콘솔은 제목 표시줄의 새 알림 영역에서 모든 알림을 표시합니다.

![콘솔의 알림 표시줄 및 플래그](./media/1318035-notify-eval-version-expired.png)

### <a name="configure-a-site-to-show-non-critical-notifications"></a>중요하지 않은 알림을 표시하도록 사이트 구성

사이트의 속성에서 중요하지 않은 알림을 표시하도록 각 사이트를 구성할 수 있습니다.

1. **관리** 작업 영역에서 **사이트 구성**을 펼친 다음 **사이트** 노드를 선택합니다.
1. 중요하지 않은 알림을 구성하려는 사이트를 선택합니다.
1. 리본에서 **속성**을 선택합니다.
1. **경고** 탭에서 **중요하지 않은 사이트 상태 변경에 대한 콘솔 알림 사용** 옵션을 선택합니다.
   - 이 설정을 활성화하는 경우 모든 콘솔 사용자는 중요, 경고 및 정보 알림을 볼 수 있습니다. 이 설정은 기본값으로 사용 가능합니다.  
   - 이 설정을 비활성화하는 경우 콘솔 사용자는 중요한 알림만 볼 수 있습니다.  

대부분의 콘솔 알림은 세션당입니다. 콘솔은 사용자가 실행하는 경우 쿼리를 평가합니다. 알림에서 변경 내용을 보려면 콘솔을 다시 시작합니다. 사용자가 중요하지 않은 알림을 취소하면 여전히 적용 가능한 경우 콘솔을 다시 시작할 때 다시 알립니다.

다음 알림은 5분마다 다시 평가합니다.

- 사이트가 유지 관리 모드에 있습니다.  
- 사이트가 복구 모드에 있습니다.  
- 사이트가 업그레이드 모드에 있습니다.  

알림은 역할 기반 관리의 사용 권한을 따릅니다. 예를 들어 사용자에게 Configuration Manager 업데이트를 볼 권한이 없으면 해당 알림이 표시되지 않습니다.

일부 알림에는 관련된 작업이 있습니다. 예를 들어 콘솔 버전이 사이트 버전과 일치하지 않는 경우 **새 콘솔 버전 설치**를 선택합니다. 이 작업은 콘솔 설치 관리자를 시작합니다.

다음과 같은 알림이 기술 미리 보기 분기에 가장 적합합니다.  

- 평가 버전이 만료 30일 이내에 있습니다(경고). 현재 날짜가 평가판의 만료 날짜로부터 30일 이내에 있습니다.  
- 평가 버전이 만료되었습니다(위험). 현재 날짜가 평가판의 만료 날짜를 지났습니다.  
- 콘솔 버전이 일치하지 않음(위험): 콘솔 버전이 사이트 버전과 일치하지 않습니다.  
- 사이트 업그레이드를 사용할 수 있습니다(경고). 사용 가능한 새 업데이트 패키지가 있습니다.  

자세한 내용 및 문제 해결 도움은 콘솔 컴퓨터의 **SmsAdminUI.log** 파일을 참조하세요. 기본적으로 이 로그 파일은 다음 경로에 있습니다. `C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole\AdminUILog\SmsAdminUI.log`


## <a name="bkmk_doc-dashboard"></a> 콘솔 내 설명서 대시보드

<!--3556019 FKA 1357546-->
Configuration Manager 1902 버전부터 새 **커뮤니티** 작업 영역에 **설명서** 노드가 있습니다. 이 노드는 Configuration Manager 설명서 및 지원 문서에 대한 최신 정보를 포함합니다. 여기에는 다음과 같은 섹션이 포함됩니다.  

### <a name="product-documentation-library"></a>제품 설명서 라이브러리

- **권장**: 수동으로 큐레이팅된 중요한 문서 목록입니다.
- **인기**: 지난달의 가장 인기 있는 문서입니다.
- **최근 업데이트 항목**: 지난달에 수정된 문서입니다.

### <a name="support-articles"></a>지원 문서

- **문제 해결 문서**: Configuration Manager 구성 요소 및 기능의 문제 해결을 지원하기 위한 안내 방식 연습입니다.
- **새로 제공되거나 업데이트된 지원 문서**: 지난 2개월 동안 새로 제공되거나 업데이트된 문서입니다.

### <a name="troubleshooting-connection-errors"></a>연결 문제 해결
**설명서** 노드에 명시적 프록시 구성이 없습니다. **인터넷 옵션** 제어판 애플릿에서 모든 OS 정의 프록시를 사용합니다. 연결 오류가 발생한 후에 다시 시도하려면 **설명서** 노드를 새로 고칩니다.


## <a name="command-line-options"></a>명령줄 옵션

Configuration Manager 콘솔에는 다음과 같은 명령줄 옵션이 있습니다.

|옵션|설명|  
|------------|-----------------|  
|`/sms:debugview=1`|DebugView는 보기를 지정하는 모든 ResultViews에 포함됩니다. DebugView는 원시 속성(이름 및 값)을 표시합니다.|  
|`/sms:NamespaceView=1`|콘솔에 네임스페이스 보기를 표시합니다.|  
|`/sms:ResetSettings`|콘솔은 사용자 유지 연결 및 보기 상태를 무시합니다. 창 크기는 다시 설정되지 않습니다.|  
|`/sms:IgnoreExtensions`|Configuration Manager 확장을 사용하지 않도록 설정합니다.|  
|`/sms:NoRestore`|콘솔은 이전에 유지된 노드 탐색을 무시합니다.|  


## <a name="tips"></a>팁

### <a name="general"></a>일반

#### <a name="role-based-administration-for-folders"></a>폴더의 역할 기반 관리
<!--3600867-->
*(버전 1906에서 도입됨)*

폴더에 보안 범위를 설정할 수 있습니다. 폴더의 개체에 대한 액세스 권한은 있지만 폴더에 대한 액세스 권한은 없는 경우 개체를 볼 수 없습니다. 마찬가지로, 폴더에 대한 액세스 권한은 있지만 폴더의 파일에 대한 액세스 권한은 없는 경우 개체를 볼 수 없습니다. 폴더를 마우스 오른쪽 단추로 클릭하고 **보안 범위 설정**을 선택한 다음 적용할 보안 범위를 선택하세요.

#### <a name="views-sort-by-integer-values"></a>정수 값 기준 정렬 보기

*(1902 버전에서 도입됨)*

다양한 보기에서 데이터를 정렬하는 방식을 개선했습니다. 예를 들어 **모니터링** 작업 영역의 **배포** 노드에서 다음 열은 이제 문자열 값 대신 숫자로 정렬됩니다.  

- 오류 개수
- 진행 중인 개수
- 기타 개수
- 성공 개수
- 알 수 없는 개수  

#### <a name="move-the-warning-for-a-large-number-of-results"></a>많은 수의 결과에 대한 경고 이동

*(1902 버전에서 도입됨)*

콘솔에서 1,000개가 넘는 결과를 반환하는 노드를 선택하는 경우 Configuration Manager에서 표시하는 경고는 다음과 같습니다.

> Configuration Manager에서 많은 수의 결과를 반환했습니다. 검색을 사용하여 결과를 좁힐 수 있습니다. 또는 최대 100,000개의 결과를 보려면 여기를 클릭합니다.

이제 이 경고와 검색 필드 사이에 빈 공간이 추가되었습니다. 이 이동은 경고를 실수로 선택하여 더 많은 결과를 표시하지 않도록 방지하는 데 도움이 됩니다.

#### <a name="send-feedback"></a>의견 보내기

*(버전 1806에서 도입됨)*
<!--1357542-->

콘솔에서 피드백을 제출합니다.  

- **웃는 얼굴 보내기**: 좋아하는 것에 대한 피드백을 보냅니다.  

- **찡그린 얼굴 보내기**: 싫어하는 것에 대한 피드백을 보냅니다.  

- **제안 보내기**: UserVoice로 이동하여 아이디어를 공유합니다.  

자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#BKMK_1806Feedback)을 참조하세요.


### <a name="assets-and-compliance-workspace"></a>자산 및 규정 준수 작업 영역

#### <a name="real-time-actions-from-device-lists"></a>디바이스 목록에서 실시간 작업
<!--4616810-->
*(버전 1906에서 도입됨)*

몇 가지 방법으로 **자산 및 규정 준수** 작업 영역의 **디바이스**에서 디바이스 목록을 표시할 수 있습니다.

- **자산 및 규정 준수** 작업 영역에서 **디바이스 컬렉션** 노드를 선택합니다. 디바이스 컬렉션을 선택하고 **멤버 표시** 작업을 선택합니다. 이 작업을 수행하면 해당 컬렉션에 대한 디바이스 목록이 있는 **디바이스** 노드의 하위 노드가 열립니다.  

  - 컬렉션 하위 노드를 선택하면 리본의 컬렉션 그룹에서 **CMPivot**을 시작할 수 있습니다.  

- **모니터링** 작업 영역에서 **배포** 노드를 선택합니다. 배포를 선택하고 리본에서 **상태 보기** 작업을 선택합니다. 배포 상태 창에서 총 자산을 두 번 클릭하여 디바이스 목록까지 드릴스루합니다.  

  - 이 목록의 디바이스를 선택하면 리본의 디바이스 그룹에서 **CMPivot** 및 **스크립트 실행**을 시작할 수 있습니다.  


#### <a name="collections-tab-in-devices-node"></a>디바이스 노드의 컬렉션 탭
<!--4616810-->
*(버전 1906에서 도입됨)*

**자산 및 규정 준수** 작업 영역의 **디바이스** 노드로 이동하여 디바이스를 선택합니다. 세부 정보 창에서 새 **컬렉션** 탭으로 전환합니다. 이 탭은 이 디바이스를 포함하는 컬렉션을 나열합니다. 

> [!Note]  
> - 이 탭은 현재 **디바이스 컬렉션** 노드의 디바이스 하위 노드에서 사용할 수 없습니다. 예를 들어, 컬렉션에서 **멤버 표시** 옵션을 선택할 때입니다.
> - 일부 사용자에게는 이 탭이 예상대로 채워지지 않을 수 있습니다. 디바이스가 속한 컬렉션의 전체 목록을 확인하려면 **전체 관리자** 보안 역할이 있어야 합니다. 이것은 알려진 문제입니다. <!--5107309--> <!--5107309-->


#### <a name="add-smbios-guid-column-to-device-and-device-collection-nodes"></a>디바이스 및 디바이스 컬렉션 노드에 SMBIOS GUID 열 추가

*(버전 1906에서 도입됨)*

<!--4526580-->
**디바이스** 및 **디바이스 컬렉션** 노드에서 이제 새로운 **SMBIOS GUID** 열을 추가할 수 있습니다. 이 값은 시스템 리소스 클래스의 **BIOS GUID** 속성과 같습니다. 디바이스 하드웨어의 고유 식별자입니다.

#### <a name="search-device-views-using-mac-address"></a>MAC 주소를 사용하여 검색 디바이스 보기

<!--3600878-->
*(1902 버전에서 도입됨)*

Configuration Manager 콘솔의 디바이스 보기에서 MAC 주소를 검색할 수 있습니다. 이 속성은 PXE 기반 배포 문제를 해결하는 동안 OS 배포 관리자에게 유용합니다. 디바이스 목록을 확인하면 보기에 **MAC 주소** 열을 추가합니다. 검색 필드를 사용하여 **MAC 주소** 검색 조건을 추가합니다.

#### <a name="view-users-for-a-device"></a>디바이스에 대한 사용자 표시

1806 버전부터 다음 열을 **디바이스** 노드에서 사용할 수 있습니다.  

- **기본 사용자** <!--1357280-->  

- **현재 로그온한 사용자** <!--1358202-->  

    > [!NOTE]  
    > 현재 로그온한 사용자를 보려면 [사용자 검색](/sccm/core/servers/deploy/configure/configure-discovery-methods#bkmk_config-adud) 및 [사용자 디바이스 선호도](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)가 필요합니다.  

기본이 아닌 열을 표시하는 방법에 대한 자세한 내용은 [열](#columns)을 참조하세요.

#### <a name="improvement-to-device-search-performance"></a>디바이스 검색 성능 향상

<!-- 3614690 -->
버전 1806부터는 디바이스 컬렉션에서 검색할 때 모든 개체 속성에 대한 키워드를 검색하지 않습니다. 검색할 항목을 구체적으로 지정하지 않으면 다음과 같은 네 가지 속성을 검색합니다.

- Name
- 기본 사용자
- 현재 로그온한 사용자
- 마지막 로그온 사용자 이름

이 동작은 특히 대규모 환경에서 이름별로 검색하는 데 걸리는 시간을 대폭 개선합니다. 특정 기준별 사용자 지정 검색은 이 변경의 영향을 받지 않습니다.


### <a name="software-library-workspace"></a>소프트웨어 라이브러리 작업 영역

#### <a name="order-by-program-name-in-task-sequence"></a>작업 순서에서 프로그램 이름별로 정렬
<!--4616810-->
*(버전 1906에서 도입됨)*

**소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 펼치고 **작업 순서** 노드를 선택합니다. 작업 순서를 편집하고 [패키지 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallPackage) 단계를 선택하거나 추가합니다. 패키지에 둘 이상의 프로그램이 있는 경우 이제 드롭다운 목록이 프로그램을 사전순으로 정렬합니다.

#### <a name="task-sequences-tab-in-applications-node"></a>애플리케이션 노드의 작업 순서 탭
<!--4616810-->
*(버전 1906에서 도입됨)*

**소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 펼치고 **애플리케이션** 노드로 이동한 다음, 애플리케이션을 선택합니다. 세부 정보 창에서 새 **작업 순서** 탭으로 전환합니다. 이 탭은 이 애플리케이션을 참조하는 작업 순서를 나열합니다.

#### <a name="drill-through-required-updates"></a>필수 업데이트 드릴스루
<!--4224414-->
*(버전 1906에서 도입됨)*

1. Configuration Manager 콘솔에서 다음 위치 중 하나로 이동합니다.

   - **소프트웨어 라이브러리** > **소프트웨어 업데이트** > **모든 소프트웨어 업데이트**
   - **소프트웨어 라이브러리** > **Windows 10 서비스** > **모든 Windows 10 업데이트**
   - **소프트웨어 라이브러리** > **Office 365 클라이언트 관리** > **Office 365 업데이트**

1. 하나 이상의 디바이스에 필요한 업데이트를 선택합니다.
1. **요약** 탭을 확인하고 **통계**에서 원형 차트를 찾습니다.
1. 원형 차트 옆에 있는 **필수 보기** 하이퍼링크를 선택하여 디바이스 목록으로 드릴다운합니다.
1. 이 작업에서는 업데이트를 필요로 하는 디바이스를 볼 수 있는 **디바이스**의 임시 노드로 이동합니다. 목록에서 새 컬렉션 만들기와 같이 노드에 대한 조치를 취할 수도 있습니다.


#### <a name="maximize-the-browse-registry-window"></a>레지스트리 찾아보기 창 최대화

<!--3594151 includes all MMS 1902 console changes-->
*(1902 버전에서 도입됨)*

1. **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 펼치고, **애플리케이션** 노드를 선택합니다.
1. 검색 방법을 사용하여 배포 유형이 있는 애플리케이션을 선택합니다. 예를 들어 Windows Installer 검색 방법이 있습니다.
1. 세부 정보 창에서 **배포 유형** 탭으로 전환합니다.
1. 배포 유형의 속성을 열고, **검색 방법** 탭으로 전환합니다. **절 추가**를 선택합니다.
1. **설정 유형**을 **레지스트리**로 변경하고, **찾아보기**를 선택하여 **레지스트리 찾아보기** 창을 엽니다. 이제 이 창을 최대화할 수 있습니다.  

#### <a name="edit-a-task-sequence-by-default"></a>기본적으로 작업 순서 편집

*(1902 버전에서 도입됨)*

**소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 펼치고 **작업 순서** 노드를 선택합니다. 이제 작업 순서를 열면 **편집**이 기본 작업이 됩니다. 이전에는 기본 작업이 **속성**이었습니다.  

#### <a name="go-to-the-collection-from-an-application-deployment"></a>애플리케이션 배포에서 컬렉션으로 이동

*(1902 버전에서 도입됨)*

1. **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 펼치고, **애플리케이션** 노드를 선택합니다.
1. 애플리케이션을 선택합니다. 세부 정보 창에서 **배포** 탭으로 전환합니다.
1. 배포를 선택한 다음, [배포] 탭의 리본에서 새 **컬렉션** 옵션을 선택합니다. 이 작업은 보기를 배포의 대상인 컬렉션으로 전환합니다.
   - 이 작업은 이 보기에서 배포의 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴에서도 사용할 수 있습니다.


### <a name="monitoring-workspace"></a>모니터링 작업 영역

#### <a name="correct-names-for-client-operations"></a>클라이언트 작업의 올바른 이름
<!--4616810-->
*(버전 1906에서 도입됨)*

**모니터링** 작업 영역에서 **클라이언트 작업**을 선택합니다. **다음 소프트웨어 업데이트 지점으로 전환** 작업의 이름이 이제 제대로 지정되었습니다.

#### <a name="show-collection-name-for-scripts"></a>스크립트의 컬렉션 이름 표시
<!--4616810-->
*(버전 1906에서 도입됨)*

**모니터링** 작업 영역에서 **스크립트 상태** 노드를 선택합니다. 이제 ID와 함께 **컬렉션 이름**이 나열됩니다.

#### <a name="remove-content-from-monitoring-status"></a>모니터링 상태에서 콘텐츠 제거

*(1902 버전에서 도입됨)*

1. **모니터링** 작업 영역에서 **배포 상태**를 펼치고 **콘텐츠 상태**를 선택합니다.
1. 목록에서 항목을 선택하고, 리본에서 **상태 보기** 옵션을 선택합니다.
1. [자산 정보] 창에서 배포 지점을 마우스 오른쪽 단추로 클릭하고, 새 옵션인 **제거**를 선택합니다. 이 작업은 선택한 배포 지점에서 이 콘텐츠를 삭제합니다.

#### <a name="copy-details-in-monitoring-views"></a>모니터링 보기에서 세부 정보 복사

*(버전 1806에서 도입됨)*
<!--1357856-->
다음 모니터링 노드의 **자산 세부 정보** 창에서 정보를 복사합니다.  

- **콘텐츠 배포 상태**  

- **배포 상태**  

![배포 상태 보기, 복사 자산 세부 정보](media/1810-deployment-status.PNG)

### <a name="administration-workspace"></a>관리 작업 영역

<!--4223683-->
버전 1906부터 관리 서비스를 사용하도록 **보안** 노드의 일부 노드를 사용하도록 설정할 수 있습니다. 이 변화 덕분에 콘솔이 WMI 대신 HTTPS를 통해 SMS 공급자와 통신할 수 있습니다. 자세한 정보는 [관리 서비스](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_admin-service)를 참조하세요.


## <a name="next-steps"></a>다음 단계

[접근성 기능](/sccm/core/understand/accessibility-features)
