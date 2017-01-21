---
title: "사용자 상태 관리 | Microsoft 문서"
description: "System Center Configuration Manager는 사용자 상태 마이그레이션 도구를 사용하여 운영 체제 배포 시나리오에서 사용자 상태 데이터를 캡처 및 복원합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8d5c345-1e91-410b-b8a9-0170dcfa846e
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 65ebfd385a27ebda8d5057f503c01b8b33628a72


---
# <a name="manage-user-state-in-system-center-configuration-manager"></a>System Center Configuration Manager의 사용자 상태 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 작업 순서를 사용하여 현재 운영 체제의 사용자 상태를 보존하려는 운영 체제 배포 시나리오에서 사용자 상태 데이터를 캡처 및 복원할 수 있습니다. 예를 들면 다음과 같습니다.  

-   배포 시 한 컴퓨터에서 사용자 상태를 캡처하여 다른 컴퓨터에서 복원  

-   동일한 컴퓨터에서 사용자 상태를 캡처하고 복원할 수 있는 업데이트 배포  

 Configuration Manager에서는 USMT(사용자 상태 마이그레이션 도구) 10.0을 사용하여 운영 체제 설치가 완료된 후 원본 컴퓨터에서 대상 컴퓨터로의 사용자 상태 데이터 마이그레이션을 관리합니다. USMT 10.0에 대한 일반적인 마이그레이션 시나리오에 대해서는  [일반적인 마이그레이션 시나리오](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)를 참조하세요.  

 사용자 데이터를 캡처 및 복원하려면 다음 섹션을 참조하세요.


##  <a name="a-namebkmkstoringuserdataa-store-user-state-data"></a><a name="BKMK_StoringUserData"></a> 사용자 상태 데이터 저장  
 사용자 상태를 캡처하는 경우 대상 컴퓨터 또는 상태 마이그레이션 지점에 사용자 상태 데이터를 저장할 수 있습니다. 사용자 상태 마이그레이션 지점에 사용자 상태를 저장하려면 상태 마이그레이션 지점 사이트 시스템 역할을 호스트하는 Configuration Manager 사이트 시스템 서버를 사용해야 합니다. 대상 컴퓨터에 사용자 상태를 저장하려면 링크를 사용하여 로컬로 데이터를 저장하도록 작업 순서를 구성해야 합니다.  

> [!NOTE]  
>  사용자 상태를 저장하는 데 사용되는 링크를 하드 링크라고 합니다. 하드 링크는 컴퓨터에서 사용자 파일과 설정을 검색한 후 그러한 파일에 대한 하드 링크 디렉터리를 만드는 USMT 10.0 기능입니다. 새 운영 체제가 배포된 후에 하드 링크를 사용하여 사용자 데이터를 복원할 수 있습니다.  

> [!IMPORTANT]  
>  상태 마이그레이션 지점을 사용하는 경우 하드 링크를 사용하여 사용자 상태 데이터를 저장할 수 없습니다.  

 사용자 상태 정보는 캡처 시 다음 방식 중 하나로 저장될 수 있습니다.  

-   상태 마이그레이션 지점을 구성하여 원격으로 사용자 상태 데이터를 저장할 수 있습니다. **캡처** 작업 순서가 데이터를 상태 마이그레이션 지점으로 전송합니다. 그런 다음 운영 체제가 배포된 후에 **복원** 작업 순서가 데이터를 검색하여 대상 컴퓨터에서 사용자 상태를 복원합니다.  

-   사용자 상태 데이터를 특정 위치에 로컬로 저장할 수 있습니다. 이 시나리오에서는 **캡처** 작업 순서가 사용자 데이터를 대상 컴퓨터의 특정 위치로 복사합니다. 그런 다음 운영 체제가 배포된 후에 **복원** 작업 순서가 해당 위치에서 사용자 데이터를 검색합니다.  

-   하드 링크를 지정하여 사용자 데이터를 원래 위치로 복원하는 데 사용할 수 있습니다. 이 시나리오에서는 이전 운영 체제를 제거할 때 드라이브에 사용자 상태 데이터가 유지됩니다. 그런 다음 새 운영 체제가 배포된 후에 **복원** 작업 순서가 하드 링크를 사용하여 사용자 상태 데이터를 원래 위치로 복원합니다.  

###  <a name="a-namebkmkuserdatasmpa-store-user-data-on-a-state-migration-point"></a><a name="BKMK_UserDataSMP"></a> 상태 마이그레이션 지점에 사용자 데이터 저장  
 상태 마이그레이션 지점에 사용자 상태 데이터를 저장하려면 다음을 수행해야 합니다.  

1.  사용자 상태 데이터를 저장하는[Configure a state migration point](#BKMK_StateMigrationPoint)   

2.  원본 컴퓨터와 대상 컴퓨터 사이의[Create a computer association](#BKMK_ComputerAssociation) . 원본 컴퓨터에서 사용자 상태를 캡처하기 전에 이 연결을 만들어야 합니다.  

3.  [System Center Configuration Manager에서 사용자 상태를 캡처 및 복원하는 작업 순서 만들기](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md) 특히 컴퓨터에서 사용자 데이터를 캡처하고, 상태 마이그레이션 지점에 사용자 데이터를 저장하고, 사용자 데이터를 컴퓨터에 복원하는 다음 작업 순서 단계를 추가해야 합니다.  

    -   [상태 저장소 요청](../understand/task-sequence-steps.md#BKMK_RequestStateStore): 컴퓨터에서 상태를 캡처하거나 컴퓨터로 상태를 복원할 때 상태 마이그레이션 지점에 대한 액세스 요청  

    -   [사용자 상태 캡처](../understand/task-sequence-steps.md#BKMK_CaptureUserState): 사용자 상태 데이터를 캡처하고 상태 마이그레이션 지점에 저장  

    -   [사용자 상태 복원](../understand/task-sequence-steps.md#BKMK_RestoreUserState): 사용자 상태 마이그레이션 지점에서 데이터를 검색하여 대상 컴퓨터에서 사용자 상태 복원  

    -   [상태 저장소 해제](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore): 상태 마이그레이션 지점에 캡처 또는 복원 작업이 완료되었음을 알림  

###  <a name="a-namebkmkuserdatadestinationa-store-user-data-locally"></a><a name="BKMK_UserDataDestination"></a> 사용자 데이터를 로컬로 저장  
 사용자 상태 데이터를 로컬로 저장하려면 다음을 수행해야 합니다.  

-   [사용자 상태를 캡처 및 복원하는 작업 순서 만들기](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md) 특히 컴퓨터에서 사용자 데이터를 캡처하고, 하드 링크를 사용하여 사용자 데이터를 컴퓨터에 복원하는 다음 작업 순서 단계를 추가해야 합니다.  

    -   [사용자 상태 캡처](../understand/task-sequence-steps.md#BKMK_CaptureUserState): 하드 링크를 사용하여 사용자 상태 데이터를 캡처한 후 로컬 폴더에 저장  

    -   [사용자 상태 복원](../understand/task-sequence-steps.md#BKMK_RestoreUserState): 하드 링크를 사용하여 데이터를 검색하여 대상 컴퓨터에서 사용자 상태 복원  

        > [!NOTE]  
        >  작업 순서를 통해 이전 운영 체제가 제거된 후에도 하드 링크가 참조하는 사용자 상태 데이터는 컴퓨터에 유지됩니다. 새 운영 체제가 배포된 후에 이 데이터를 사용하여 사용자 상태가 복원됩니다.  

##  <a name="a-namebkmkstatemigrationpointa-configure-a-state-migration-point"></a><a name="BKMK_StateMigrationPoint"></a> Configure a state migration point  
 상태 마이그레이션 지점에서는 한 컴퓨터에서 캡처된 후 다른 컴퓨터에서 복원된 사용자 상태 데이터를 저장합니다. 그러나 대상 컴퓨터에서 운영 체제를 새로 고치는 배포와 같이 동일한 컴퓨터에서 운영 체제 배포에 대한 사용자 설정을 캡처하는 경우, 하드 링크를 사용하여 동일한 컴퓨터에 데이터를 저장하거나 상태 마이그레이션 지점에 데이터를 저장할 수 있습니다. 일부 컴퓨터 배포에 대해 상태 저장소를 만들 경우 Configuration Manager에서 이 상태 저장소와 대상 컴퓨터 간에 자동으로 연결을 만듭니다. 다음 방법을 사용하여 사용자 상태 데이터를 저장하도록 상태 마이그레이션 지점을 구성할 수 있습니다.  

-   **사이트 시스템 서버 만들기 마법사** 를 사용하여 상태 마이그레이션 지점을 위한 새 사이트 시스템 서버를 만듭니다.  

-   **사이트 시스템 역할 추가 마법사** 를 사용하여 기존 서버에 상태 마이그레이션 지점을 추가합니다.  

 이러한 마법사를 사용하는 경우 상태 마이그레이션 지점에 대한 다음 정보를 제공해야 합니다.  

-   사용자 상태 데이터를 저장하는 폴더  

-   상태 마이그레이션 지점에 데이터를 저장할 수 있는 최대 클라이언트 수  

-   상태 마이그레이션 지점이 사용자 상태 데이터를 저장하는 데 사용할 수 있는 최소 공간  

-   역할에 대한 삭제 정책. 사용자 상태 데이터가 컴퓨터에서 복원되고 나서 즉시 또는 특정 일수 후에 데이터를 삭제하도록 지정할 수 있습니다.  

-   상태 마이그레이션 지점이 사용자 상태 데이터를 복원하는 요청에만 응답하도록 할지 여부. 이 옵션을 사용하면 상태 마이그레이션 지점을 사용하여 사용자 상태 데이터를 저장할 수 없습니다.  

 상태 마이그레이션 지점 및 구성 단계에 대한 자세한 내용은 [상태 마이그레이션 지점](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints)을 참조하세요.  

##  <a name="a-namebkmkcomputerassociationa-create-a-computer-association"></a><a name="BKMK_ComputerAssociation"></a> Create a computer association  
 새 하드웨어에 운영 체제를 설치하고 사용자 데이터 설정을 캡처 및 복원하려면 원본 컴퓨터와 대상 컴퓨터 사이의 관계를 정의하는 컴퓨터 연결을 만듭니다. 원본 컴퓨터는 Configuration Manager가 관리하는 기존 컴퓨터입니다. 새 운영 체제를 대상 컴퓨터에 배포하는 경우 원본 컴퓨터에 대상 컴퓨터로 마이그레이션되는 사용자 상태가 포함됩니다.  

> [!NOTE]  
>  Configuration Manager 상위 사이트에 있는 컴퓨터와 하위 사이트에 있는 컴퓨터 사이에 컴퓨터 연결을 만들 수는 없습니다. 컴퓨터 연결은 사이트로만 한정되며 복제되지 않습니다.  

#### <a name="to-create-a-computer-association"></a>컴퓨터 연결을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **사용자 상태 마이그레이션**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **컴퓨터 연결 만들기**를 클릭합니다.  

4.  **컴퓨터 연결 속성** 대화 상자의 **컴퓨터 연결** 탭에서 캡처할 사용자 상태가 있는 원본 컴퓨터와 사용자 상태 데이터를 복원할 대상 컴퓨터를 지정합니다.  

5.  **사용자 계정** 탭에서 대상 컴퓨터로 마이그레이션할 사용자 계정을 지정합니다. 다음 설정 중 하나를 지정합니다.  

    -   **모든 사용자 계정 캡처 및 복원**: 이 설정은 모든 사용자 계정을 캡처하고 복원합니다. 동일한 원본 컴퓨터에 대한 여러 연결을 만들려면 이 설정을 사용합니다.  

    -   **모든 사용자 계정 캡처 및 지정한 계정 복원**: 이 설정은 원본 컴퓨터에서 모든 사용자 계정을 캡처하고 대상 컴퓨터에서 지정한 계정만 복원합니다. 또한 동일한 원본 컴퓨터에 대한 여러 연결을 만들려는 경우 이 설정을 사용할 수 있습니다.  

    -   **지정한 사용자 계정 캡처 및 복원**: 이 설정은 지정한 계정만 캡처하고 복원합니다. 이 설정을 선택한 경우 동일한 원본 컴퓨터에 대한 여러 연결을 만들 수 없습니다.  

##  <a name="a-namebkmkmigrationfailsa-restore-user-state-data-when-an-operating-system-deployment-fails"></a><a name="BKMK_MigrationFails"></a> 운영 체제 배포 실패 시 사용자 상태 데이터 복원  
 운영 체제 배포가 실패하는 경우 USMT 10.0 LoadState 기능을 사용하여 배포 프로세스가 진행되는 동안 캡처된 사용자 상태 데이터를 검색해야 합니다. 여기에는 상태 마이그레이션 지점에 저장된 데이터나, 대상 컴퓨터에 로컬로 저장된 데이터가 포함됩니다. 이러한 USMT 기능에 대한 자세한 내용은 [LoadState 구문](https://technet.microsoft.com/library/mt299188\(v=vs.85\).aspx)을 참조하십시오.  



<!--HONumber=Dec16_HO3-->


