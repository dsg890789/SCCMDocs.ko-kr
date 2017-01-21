---
title: "1511, 1602 및 1606에 대한 경계 그룹 | System Center Configuration Manager"
description: "Configuration Manager 버전 1511, 1602 및 1606에서 경계 그룹을 사용합니다."
ms.custom: na
ms.date: 11/18/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dec1e0d7-5864-43a8-9f56-413923b3914e
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: b64f1f06af1ab4a255b6291b6eb5f85cff99ae63
ms.openlocfilehash: ef408041eb6d0d6716e244d34b9a2a4ebe5cb9cc


---
# <a name="boundary-groups-for-system-center-configuration-manager-version-1511-1602-and-1606"></a>System Center Configuration Manager 버전 1511, 1602 및 1606에 대한 경계 그룹

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 정보는 System Center Configuration Manager 버전 1511, 1602 및 1606에서 경계 그룹을 사용하는 경우에 해당합니다.
버전 1610 이상을 사용하는 경우 다시 디자인된 경계 그룹을 사용하는 방법에 대한 자세한 내용은 *정의 사이트 경계와 bondary 그룹 또는 System Center Configuration Manager*에서 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-group/)을 참조하세요.  


##  <a name="a-namebkmkboundarygroupsa-boundary-groups"></a><a name="BKMK_BoundaryGroups"></a> Boundary groups  
 경계 그룹을 만들어 관련 네트워크 위치(경계)를 논리적으로 그룹화하면 인프라를 보다 쉽게 관리할 수 있습니다. 경계 그룹을 사용하기 전에 경계 그룹에 경계를 할당해야 합니다. 클라이언트는 다음 항목에 대해 경계 그룹 구성을 사용합니다.  

-   자동 사이트 할당  

-   콘텐츠 위치  

-   기본 관리 지점. 기본 관리 지점을 사용하는 경우에는 경계 그룹 구성 내가 아닌 계층 구조에 대해 이 옵션을 사용하도록 설정해야 합니다. *기본 관리 지점을 사용하도록 설정하려면*절차를 참조하세요.  

경계 그룹을 구성할 때는 경계 그룹에 하나 이상의 경계를 추가한 다음 해당 경계에 있는 클라이언트가 사용할 추가 설정을 구성합니다.  

#### <a name="to-create-a-boundary-group"></a>경계 그룹을 만들려면  

1.  Configuration Manager 콘솔에서 **관리** > **계층 구조 구성** >  **경계 그룹**을 클릭합니다.  

2.  **홈** 탭의 **만들기** 그룹에서 **경계 그룹 만들기**를 클릭합니다.  

3.  **경계 그룹 만들기** 대화 상자에서 **일반** 탭을 선택하고 이 경계 그룹의 **이름** 을 지정합니다.  

4.  **확인** 을 클릭하여 새 경계 그룹을 저장합니다.  

#### <a name="to-configure-a-boundary-group"></a>경계 그룹을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **계층 구조 구성** >  **경계 그룹**을 클릭합니다.  

2.  수정할 경계 그룹을 선택합니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

4.  경계 그룹의 **속성** 대화 상자에서 **일반** 탭을 선택하여 이 경계 그룹에 속한 경계를 수정합니다.  

    -   이 경계를 추가하려면 **추가**를 클릭하고 경계 그룹 하나 이상의 확인란을 선택한 다음 **확인**을 클릭합니다.  

    -   경계를 제거하려면 경계를 선택하고 **제거**를 클릭합니다.  

5.  사이트 할당 및 연결된 사이트 시스템 서버 구성을 수정하려면 **참조** 탭을 선택합니다.  

    -   클라이언트에서 사이트 할당에 이 경계 그룹을 사용하도록 하려면 **사이트 할당에 대해 이 경계 그룹 사용**확인란을 선택한 다음 **할당된 사이트** 드롭다운 상자에서 사이트를 선택합니다.  

    -   이 경계 그룹에 연결되는 사용 가능한 사이트 시스템 서버를 구성하려면  

    1.  **추가**를 클릭한 다음 서버 하나 이상의 확인란을 선택합니다. 서버가 이 경계 그룹에 대해 연결된 사이트 시스템 서버로 추가됩니다. 지원되는 사이트 시스템 역할이 설치되어 있는 서버만 사용 가능합니다.  

        > [!NOTE]  
        >  계층의 모든 사이트에서 사용 가능한 사이트 시스템 조합을 선택할 수 있습니다. 선택한 사이트 시스템은 이 경계 그룹의 구성원인 각 경계의 속성에서 **사이트 시스템** 탭에 나열됩니다.  

    2.  이 경계 그룹에서 서버를 제거하려면 해당 서버를 선택하고 **제거**를 클릭합니다.  

        > [!NOTE]  
        >  사이트 시스템을 연결하는 데 이 경계 그룹을 더 이상 사용하지 않으려면 연결된 사이트 시스템 서버로 나열되어 있는 모든 서버를 제거해야 합니다.  

    3.  이 경계 그룹의 사이트 시스템 서버에 대한 네트워크 연결 속도를 변경하려면 해당 서버를 선택하고 **연결 변경**을 클릭합니다.  

         각 사이트 시스템의 연결 속도는 기본적으로 **고속**이지만 **저속**으로 변경할 수 있습니다. 네트워크 연결 속도와 배포 구성에 따라 클라이언트가 서버에서 콘텐츠를 다운로드할 수 있는지 여부가 결정됩니다.  

6.  **확인** 을 클릭하여 경계 그룹 속성을 닫고 구성을 저장합니다.  

#### <a name="to-associate-a-content-deployment-server-or-management-point-with-a-boundary-group"></a>경계 그룹과 콘텐츠 배포 서버 또는 관리 지점을 연결하려면  

1.  Configuration Manager 콘솔에서 **관리** > **계층 구조 구성** >  **경계 그룹**을 클릭합니다.  

2.  수정할 경계 그룹을 선택합니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

4.  경계 그룹의 **속성** 대화 상자에서 **참조** 탭을 선택합니다.  

5.  **사이트 시스템 서버 선택**아래에서 **추가**를 클릭하고 이 경계 그룹에 연결할 사이트 시스템 서버의 확인란을 선택한 다음 **확인**을 클릭합니다.  

6.  **확인** 을 클릭하여 대화 상자를 닫고 경계 그룹 구성을 저장합니다.  

#### <a name="to-enable-use-of-preferred-management-points"></a>기본 관리 지점을 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 클릭하고 **홈** 탭에서 **계층 구조 설정**을 선택합니다.  

2.  계층 구조 설정의 **일반** 탭에서 **클라이언트가 경계 그룹에 지정된 관리 지점 사용을 선호**를 선택합니다.  

3.  **확인** 을 클릭하여 대화 상자를 닫고 구성을 저장합니다.  

#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>자동 사이트 할당을 위한 대체 사이트를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** >  **사이트**를 클릭합니다.  

2.  **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 클릭합니다.  

3.  **일반** 탭에서 **대체 사이트 사용**확인란을 선택한 다음 **대체 사이트** 드롭다운 목록에서 사이트를 선택합니다.  

4.  **확인** 을 클릭하여 구성을 저장합니다.  

 다음 섹션에서는 경계 그룹 구성에 대한 추가 세부 정보를 제공합니다.  

###  <a name="a-namebkmkboundarysiteassignmenta-about-site-assignment"></a><a name="BKMK_BoundarySiteAssignment"></a> 사이트 할당 정보  
 클라이언트의 할당된 사이트로 각 경계 그룹을 구성할 수 있습니다.  

-   자동 사이트 할당을 사용하는 새로 설치된 클라이언트는 클라이언트의 현재 네트워크 위치가 포함된 경계 그룹의 할당된 사이트에 연결됩니다.  

-   사이트에 할당된 클라이언트는 네트워크 위치를 변경할 때 사이트 할당을 변경하지 않습니다. 예를 들어 클라이언트가 다른 사이트 할당이 지정된 경계 그룹의 경계가 표시하는 새 네트워크 위치로 로밍할 경우 이 클라이언트의 할당된 사이트는 변경되지 않고 그대로 유지됩니다.  

-   Active Directory 시스템 검색이 새 리소스를 검색하면 검색된 리소스의 네트워크 정보는 경계 그룹의 경계를 기준으로 평가됩니다. 이 프로세스는 클라이언트 강제 설치 방법에서 사용하도록 할당된 사이트에 새 리소스를 연결합니다.  

-   경계가 서로 다른 할당된 사이트를 포함하는 여러 경계 그룹의 구성원이면 클라이언트는 사이트 중 하나를 임의로 선택합니다.  

-   경계 그룹 할당된 사이트에 대한 변경 내용은 새 사이트 할당 작업에만 적용됩니다. 이전에 사이트에 할당된 클라이언트는 경계 그룹의 구성 또는 고유 네트워크 위치의 변경 내용을 기준으로 사이트 할당을 다시 평가하지 않습니다.  

클라이언트 사이트 할당에 대한 자세한 내용은 [System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법](../../../../core/clients/deploy/assign-clients-to-a-site.md)에서 [컴퓨터에 대한 자동 사이트 할당 사용](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment)을 참조하세요.  

###  <a name="a-namebkmkboundarycontentlocationa-about-content-location"></a><a name="BKMK_BoundaryContentLocation"></a> 콘텐츠 위치 정보  
 하나 이상의 배포 지점 및 상태 마이그레이션 지점을 사용하여 각 경계 그룹을 구성할 수 있으며, 같은 배포 지점 및 상태 마이그레이션 지점을 여러 경계 그룹과 연결할 수 있습니다.  

-   **소프트웨어 배포 중에**클라이언트는 배포 콘텐츠의 위치를 요청합니다. Configuration Manager에서는 클라이언트의 현재 네트워크 위치를 포함하는 각 경계 그룹에 연결된 배포 지점 목록을 클라이언트에 보냅니다.  

-   **운영 체제를 배포하는 동안 클라이언트는** 상태 마이그레이션 정보를 보내거나 받을 위치를 요청합니다. Configuration Manager에서는 클라이언트의 현재 네트워크 위치를 포함하는 각 배포 그룹과 관련된 상태 마이그레이션 지점 목록을 클라이언트에 보냅니다.  

클라이언트는 이 동작을 통해 콘텐츠나 상태 마이그레이션 정보를 전송할 가장 가까운 서버를 선택할 수 있습니다.  

###  <a name="a-namebkmkpreferredmpa-about-preferred-management-points"></a><a name="BKMK_PreferredMP"></a> 기본 설정 관리 지점 정보  
 기본 설정 관리 지점은 클라이언트가 현재 네트워크 위치(경계)와 연결된 관리 지점을 식별할 수 있도록 합니다.  

-   클라이언트는 할당된 사이트에서 기본 설정 관리 지점으로 구성되지 않은 관리 지점을 사용하기 전에 할당된 사이트의 기본 설정 관리 지점을 사용하려고 시도합니다.  

-   이 옵션을 사용하려면 계층 구조에 대해 이 옵션을 사용하도록 설정해야 하며, 경계 그룹에 연결된 경계와 연결해야 하는 관리 지점을 포함하도록 개별 기본 사이트에서 경계 그룹을 구성해야 합니다.  

-   기본 설정 관리 지점이 구성되어 있으면 클라이언트는 관리 지점 목록을 구성할 때 할당된 관리 지점 목록 맨 위에 기본 설정 관리 지점을 표시합니다. 할당된 관리 지점 목록에는 클라이언트의 할당된 사이트에 있는 모든 관리 지점이 포함됩니다.  

> [!NOTE]  
>  클라이언트는 로밍 시, 즉 노트북을 원격 사무실 위치로 이동할 때와 같이 클라이언트의 네트워크 위치가 변경될 때 할당된 사이트의 관리 지점(기본 설정 관리 지점 포함)을 사용하려고 시도하기 전에 로컬 사이트의 관리 지점 또는 프록시 관리 지점을 새 위치로 사용할 수 있습니다.  [클라이언트가 System Center Configuration Manager에 대한 사이트 리소스 및 서비스를 찾는 방법 이해](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)를 참조하세요.  

###  <a name="a-namebkmkboundaryoverlapa-about-overlapping-boundaries"></a><a name="BKMK_BoundaryOverlap"></a> 겹치는 경계 정보  
 Configuration Manager에서는 콘텐츠 위치에 대한 겹치는 경계를 구성할 수 있습니다.  

-   **클라이언트에서 콘텐츠를 요청할 때** 클라이언트 네트워크 위치가 여러 경계 그룹에 속해 있으면 Configuration Manager에서 콘텐츠가 있는 모든 배포 지점 목록을 클라이언트로 보냅니다.  

-   **클라이언트가 서버에 해당 상태 마이그레이션 정보 전송 또는 수신을 요청할 때** 클라이언트 네트워크 위치가 여러 경계 그룹에 속해 있으면 Configuration Manager에서 클라이언트의 현재 네트워크 위치가 포함된 경계 그룹에 연결된 모든 상태 마이그레이션 지점 목록을 클라이언트로 보냅니다.  

클라이언트는 이 동작을 통해 콘텐츠나 상태 마이그레이션 정보를 전송할 가장 가까운 서버를 선택할 수 있습니다.  

###  <a name="a-namebkmkboudnarynetworkspeeda-about-network-connection-speed"></a><a name="BKMK_BoudnaryNetworkSpeed"></a> 네트워크 연결 속도 정보  
 경계 그룹의 각 사이트 시스템 서버에 대해 네트워크 연결 속도를 설정할 수 있습니다. 이 설정은 이 경계 그룹 구성을 기준으로 하여 사이트 시스템에 연결하는 클라이언트에 적용됩니다. 서로 다른 여러 경계 그룹에서 동일한 사이트 시스템 서버에 대해 각기 다른 연결 속도를 설정할 수 있습니다.  

 네트워크 연결 속도는 기본적으로 **고속**으로 구성되어 있지만 **저속**으로 구성할 수도 있습니다. 네트워크 연결 속도 및 배포 구성에 따라 클라이언트가 연결된 경계 그룹에 있을 때 해당 클라이언트가 배포 지점에서 콘텐츠를 다운로드할 수 있는지 여부가 결정됩니다.  

 네트워크 연결 속도 구성이 클라이언트가 콘텐츠를 가져오는 방법에 어떤 영향을 주는지에 대한 자세한 내용은 [콘텐츠 원본 위치 시나리오](../../../../core/plan-design/hierarchy/content-source-location-scenarios.md)를 참조하세요.  



<!--HONumber=Dec16_HO3-->


