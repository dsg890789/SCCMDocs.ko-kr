---
title: Configuration Manager 콘솔
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔을 통해 이동에 대해 알아봅니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 463ce307-59dd-4abd-87b8-42ca9db178d7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bf617a579108f58723f267a065338ab857832d8f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56134574"
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

콘솔에서 노드는 경우에 따라 폴더로 구성됩니다. 폴더를 직접 클릭하면 일반적으로 **탐색 인덱스** 또는 **대시보드**로 이동합니다.  

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

### <a name="send-feedback"></a>의견 보내기
<!--1357542-->

1806 버전부터 콘솔에서 제품 사용자 의견을 제출합니다.  

- **웃는 얼굴 보내기**: 좋아하는 것에 대한 피드백을 보냅니다.  

- **찡그린 얼굴 보내기**: 싫어하는 것에 대한 피드백을 보냅니다.  

- **제안 보내기**: UserVoice로 이동하여 아이디어를 공유합니다.  
 
자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#BKMK_1806Feedback)을 참조하세요.


### <a name="assets-and-compliance-workspace"></a>자산 및 규정 준수 작업 영역

#### <a name="view-users-for-a-device"></a>디바이스에 대한 사용자 표시
1806 버전부터 다음 열을 **디바이스** 노드에서 사용할 수 있습니다.  

- **기본 사용자** <!--1357280-->  

- **현재 로그온한 사용자** <!--1358202-->  

기본이 아닌 열을 표시하는 방법에 대한 자세한 내용은 [열](#columns)을 참조하세요.


### <a name="monitoring-workspace"></a>모니터링 작업 영역

#### <a name="copy-details-in-monitoring-views"></a>모니터링 보기에서 세부 정보 복사
<!--1357856--> 1806 버전부터 다음 모니터링 노드에 대해 **자산 세부 정보** 창에서 정보를 복사합니다.  

- **콘텐츠 배포 상태**  

- **배포 상태**  

![배포 상태 보기, 복사 자산 세부 정보](media/1810-deployment-status.PNG)



## <a name="next-steps"></a>다음 단계

[접근성 기능](/sccm/core/understand/accessibility-features)

