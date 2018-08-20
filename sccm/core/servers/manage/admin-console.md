---
title: Configuration Manager 콘솔
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔을 통해 이동에 대해 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 463ce307-59dd-4abd-87b8-42ca9db178d7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 8d783211396f3cdc9f14798ed7dc97e921e45554
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385914"
---
# <a name="using-the-system-center-configuration-manager-console"></a>System Center Configuration Manager 콘솔 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

관리자는 System Center Configuration Manager 콘솔을 사용하여 Configuration Manager 환경을 관리합니다. 이 문서에서는 콘솔 탐색의 기본적인 사항을 다룹니다. 콘솔에 대한 개선 사항은 이 문서의 맨 아래에 버전별로 나열되어 있습니다. 

## <a name="connect-the-console-to-a-site-server"></a>콘솔을 사이트 서버에 연결
콘솔은 중앙 관리 사이트 서버 또는 기본 사이트 서버에 연결합니다. 그러나 Configuration Manager 콘솔을 보조 사이트에 연결할 수는 없습니다. 필요한 경우 [Configuration Manager 콘솔을 설치](../deploy/install/install-consoles.md)합니다. 설치하는 동안 Configuration Manager 콘솔이 연결하는 사이트 서버의 FQDN(정규화된 도메인 이름)을 지정했습니다. 다른 사이트 서버에 연결하려면 다음 지침을 사용합니다. 

1. 리본 메뉴의 맨 위에 있는 화살표를 클릭하고 **새 사이트에 연결**을 선택합니다.
    ![콘솔을 새 사이트에 연결](media/connect-to-a-new-site.png)
2. 사이트 서버의 FQDN을 입력합니다. 이전에 사이트 서버에 연결한 경우 드롭다운에서 서버를 선택합니다.  
    ![사이트 서버의 FQDN을 입력합니다.](media/site-server-fqdn.png)
3. **연결**을 클릭합니다. 

## <a name="navigate-the-console"></a>콘솔 탐색
콘솔에서 일부 옵션은 할당된 보안 역할에 따라 표시되지 않을 수 있습니다. 역할에 대한 자세한 내용은 [역할 기반 관리의 기본 사항](../../understand/fundamentals-of-role-based-administration.md)을 참조하세요. 

### <a name="workspaces"></a>작업 영역
Configuration Manager 콘솔에는 네 가지 **작업 영역**이 있습니다. 
   - **자산 및 호환성**
   - **소프트웨어 라이브러리**
   - **모니터링**
   - **관리**

 ![Configuration Manager 작업 영역](media/configuration-manager-workspaces.png)

아래쪽 화살표를 클릭하고 **탐색 창 옵션**을 선택하여 작업 영역 단추를 다시 정렬합니다. **위로 이동**하거나 **아래로 이동**하도록 항목을 선택합니다. **다시 설정**을 클릭하여 기본 단추 순서를 복원합니다. 

 ![Configuration Manager 작업 영역 다시 정렬](media/navigation-pane-options.png)

**단추 수 줄이기**를 선택하여 작업 영역 단추를 최소화할 수 있습니다. 작업 영역 목록의 마지막 작업 영역이 먼저 최소화됩니다. 최소화된 단추를 클릭하고 **단추 수 늘리기**를 선택하면 단추를 원래 크기로 복원합니다.  

![Configuration Manager 작업 영역](media/workspace-buttons.png)


### <a name="nodes"></a>노드
작업 영역은 **노드**의 컬렉션입니다. 노드의 한 예로 **소프트웨어 업데이트 그룹** 노드가 있습니다. 노드에 있으면 화살표를 클릭하여 탐색 창을 최소화할 수 있습니다. 

![Configuration Manager 작업 영역](media/software-update-groups-node.png)

**탐색 모음**을 사용하여 탐색 창이 최소화되었을 때 콘솔 주변을 이동할 수 있습니다. 

![Configuration Manager 최소화된 탐색 창](media/minimized-navigation-pane.png)

콘솔에서 노드는 경우에 따라 폴더로 구성됩니다. 폴더를 직접 클릭하면 일반적으로 **탐색 인덱스** 또는 **대시보드**로 이동합니다.

![Configuration Manager 소프트웨어 업데이트 탐색 인덱스](media/software-updates-navigation-index.png)

### <a name="ribbon"></a>리본 
리본은 Configuration Manager 콘솔의 맨 위에 있습니다. 리본은 둘 이상의 탭을 가질 수 있으며 오른쪽에 있는 화살표를 사용하여 최소화될 수 있습니다. 리본의 버튼은 노드에 따라 변경합니다. 리본에서 대부분의 단추를 오른쪽 클릭 메뉴로 사용할 수도 있습니다. 
 
![Configuration Manager 소프트웨어 업데이트 탐색 인덱스](media/ribbon.png)

### <a name="details-pane"></a>세부 정보 창
세부 정보 창을 검토하여 항목에 대한 추가 정보를 가져올 수 있습니다. 세부 정보 창은 하나 이상의 탭을 가질 수 있습니다. 탭은 노드에 따라 달라집니다. 
![Configuration Manager 세부 정보 창](media/details-pane.png)

### <a name="columns"></a>열 
열을 추가, 제거, 다시 정렬 및 크기 조정할 수 있습니다. 이러한 작업을 사용하여 원하는 데이터를 표시할 수 있습니다. 사용 가능한 열은 노드에 따라 달라집니다. 기존 열 제목을 마우스 오른쪽 단추로 클릭한 다음, 항목을 클릭하여 보기에서 추가하거나 제거합니다. 원하는 위치로 열 제목을 끌어 열을 다시 정렬합니다. 
![Configuration Manager에서 열 추가](media/add-columns.png)

열 오른쪽 클릭 메뉴의 맨 아래에서 열별로 정렬하거나 그룹화할 수 있습니다. 또한 해당 헤더를 클릭하여 열별로 정렬할 수 있습니다. 

![Configuration Manager에서 열별 그룹화](media/column-group-by.png)

## <a name="console-improvements-in-version-1806"></a>버전 1806의 콘솔 개선 사항
Configuration Manager 버전 1806에서 다음 콘솔 개선 사항이 추가되었습니다.

- **기본 사용자**를 장치 노드에서 열로 사용할 수 있습니다. <!--1357280-->
- **현재 로그온한 사용자**를 장치 노드에서 열로 사용할 수 있습니다.<!--1358202-->
- 다음 모니터링 보기에 대해 **자산 정보** 창에서 정보를 복사합니다. <!--1357856-->
    - 콘텐츠 배포 상태
    - 배포 상태 

    ![Configuration Manager에서 자산 세부 정보 복사](media/1810-deployment-status.PNG)

 - 콘솔에서 피드백을 제출합니다. 인터넷 액세스 권한이 없는 경우 나중에 제출하도록 복사본을 저장할 수 있습니다. <!--1357542-->
   
    - **웃는 얼굴 보내기**: 좋아하는 것에 대한 피드백을 보냅니다.
    - **찡그린 얼굴 보내기**: 싫어하는 것에 대한 피드백을 보냅니다. 
    - **제안 보내기**: UserVoice로 이동하여 아이디어를 공유합니다. 
 
       ![Configuration Manager용 피드백 보내기](media/1810-send-a-smile.PNG)
![Configuration Manager 피드백 양식](media/1810-feedback-form.PNG)

## <a name="next-steps"></a>다음 단계
> [!div class="nextstepaction"]
> [접근성 기능](/sccm/core/understand/accessibility-features.md)

