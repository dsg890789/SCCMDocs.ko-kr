---
title: 사용자 상태 캡처 및 복원
titleSuffix: Configuration Manager
description: Configuration Manager 작업 순서를 사용하여 OS 배포 시나리오에서 사용자 상태 데이터를 캡처 및 복원합니다.
ms.date: 08/17/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: d566d85c-bf7a-40e7-8239-57640a1db5f4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 709442083cd2d9c935aeb2c5fe6c2ad30a2dddf5
ms.sourcegitcommit: 2db6863c6740380478a4a8beb74f03b8178280ba
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083043"
---
# <a name="create-a-task-sequence-to-capture-and-restore-user-state-in-configuration-manager"></a>Configuration Manager에서 사용자 상태를 캡처 및 복원하는 작업 순서 만들기

 *적용 대상: System Center Configuration Manager(현재 분기)*

 Configuration Manager 작업 순서를 사용하여 OS 배포 시나리오에서 사용자 상태 데이터를 캡처 및 복원합니다. 이러한 시나리오에서 현재 OS의 사용자 상태를 유지할 수 있습니다. 만드는 작업 순서 유형에 따라, 캡처 및 복원 단계가 작업 순서의 일부로 자동으로 추가될 수도 있습니다. 다른 시나리오에서는 캡처 및 복원 단계를 작업 순서에 수동으로 추가해야 할 수 있습니다. 이 문서에서는 사용자 상태 데이터를 캡처 및 복원하기 위해 기존 작업 순서에 추가해야 하는 단계를 제공합니다.  



## <a name="task-sequence-steps"></a>작업 순서 단계  

 사용자 상태를 캡처하고 복원하려면 작업 순서에 다음 단계를 추가합니다.  

 - [상태 저장소 요청](/sccm/osd/understand/task-sequence-steps#BKMK_RequestStateStore): 상태 마이그레이션 지점에 사용자 상태를 저장하는 경우 이 단계가 필요합니다.  

- [사용자 상태 캡처](/sccm/osd/understand/task-sequence-steps#BKMK_CaptureUserState): 이 단계에서는 사용자 상태 데이터를 캡처합니다. 그런 다음 상태 마이그레이션 지점이나 하드 링크를 사용하는 로컬 디스크에 데이터를 저장합니다.  

- [사용자 상태 복원](/sccm/osd/understand/task-sequence-steps#BKMK_RestoreUserState): 이 단계는 대상 컴퓨터에서 사용자 상태 데이터를 복원합니다. 상태 마이그레이션 지점에서 데이터를 검색하거나 로컬 디스크에서 하드 링크된 데이터를 검색할 수 있습니다.  

- [상태 저장소 해제](/sccm/osd/understand/task-sequence-steps#BKMK_ReleaseStateStore): 상태 마이그레이션 지점에 사용자 상태를 저장하는 경우 이 단계가 필요합니다. 이 단계는 상태 마이그레이션 지점에서 데이터를 제거합니다.  


 사용자 상태를 캡처하고 복원하는 데 필요한 작업 순서 단계를 추가하려면 다음 단계를 따르세요. 작업 순서를 만드는 방법에 대한 자세한 내용은 [작업 순서를 관리하여 작업 자동화](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks)를 참조하세요.  



## <a name="capture-the-user-state"></a>사용자 상태 캡처  

 사용자 상태를 캡처하는 작업 순서 단계를 추가하려면 다음 절차를 따릅니다.

1.  **작업 순서** 목록에서 작업 순서를 선택한 후 **편집**을 클릭합니다.  

2.  상태 마이그레이션 지점을 사용하여 사용자 상태를 저장하는 경우 작업 순서에 **상태 저장소 요청** 단계를 추가합니다. **작업 순서 편집기**에서 **추가**를 클릭합니다. **사용자 상태**를 가리킨 다음, **상태 저장소 요청**을 클릭합니다. 이 단계에 대한 속성 및 옵션을 구성한 다음, **적용**을 클릭합니다. 사용할 수 있는 설정에 대한 자세한 내용은 [상태 저장소 요청](/sccm/osd/understand/task-sequence-steps#BKMK_RequestStateStore)을 참조하세요.  

3.  작업 순서에 **사용자 상태 캡처** 단계를 추가합니다. **작업 순서 편집기**에서 **추가**를 클릭합니다. **사용자 상태**를 가리킨 다음, **사용자 상태 캡처**를 클릭합니다. 이 단계에 대한 속성 및 옵션을 구성한 다음, **적용**을 클릭합니다. 사용할 수 있는 설정에 대한 자세한 내용은 [사용자 상태 캡처](/sccm/osd/understand/task-sequence-steps#BKMK_CaptureUserState)를 참조하세요.  

    > [!IMPORTANT]  
    >  작업 순서에 이 단계를 추가하는 경우 **OSDStateStorePath** 작업 순서 변수도 설정하여 사용자 상태 데이터를 저장할 위치를 지정합니다. 사용자 상태를 로컬로 저장하는 경우 루트 폴더를 지정하지 마세요. 그럴 경우 작업 순서가 실패할 수 있습니다. 사용자 데이터를 로컬로 저장하는 경우 항상 폴더 또는 하위 폴더를 사용합니다. 이 변수에 대한 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#OSDStateStorePath)\(작업 순서 변수)\를 참조하세요.  

4.  상태 마이그레이션 지점을 사용하는 경우 **상태 저장소 해제** 단계를 작업 순서에 추가합니다. **작업 순서 편집기**에서 **추가**를 클릭합니다. **사용자 상태**를 가리킨 다음, **상태 저장소 해제**를 클릭합니다. 이 단계에 대한 속성 및 옵션을 구성한 다음, **적용**을 클릭합니다. 사용할 수 있는 설정에 대한 자세한 내용은 [상태 저장소 해제](/sccm/osd/understand/task-sequence-steps#BKMK_ReleaseStateStore)를 참조하세요.  

    > [!IMPORTANT]  
    >  **상태 저장소 해제** 단계 이전에 실행되는 작업 순서 작업은 **상태 저장소 해제** 단계가 시작되기 전에 모두 성공적으로 수행되어야 합니다.  


 대상 컴퓨터에서 사용자 상태를 캡처할 수 있도록 이 작업 순서를 배포합니다. 작업 순서를 배포하는 방법에 대한 자세한 내용은 [작업 순서 배포](/sccm/osd/deploy-use/deploy-a-task-sequence)를 참조하세요.  



## <a name="restore-the-user-state"></a>사용자 상태 복원  

 사용자 상태를 복원하는 작업 순서 단계를 추가하려면 다음 절차를 따릅니다.

1. **작업 순서** 목록에서 작업 순서를 선택한 후 **편집**을 클릭합니다.  

2. **사용자 상태 복원** 단계를 작업 순서에 추가합니다. **작업 순서 편집기**에서 **추가**를 클릭합니다. **사용자 상태**를 가리킨 다음, **사용자 상태 복원**을 클릭합니다. 필요할 경우 이 단계에서 상태 마이그레이션 지점에 연결됩니다. 이 단계에 대한 속성 및 옵션을 구성한 다음, **적용**을 클릭합니다. 사용할 수 있는 설정에 대한 자세한 내용은 [사용자 상태 복원](/sccm/osd/understand/task-sequence-steps#BKMK_RestoreUserState)을 참조하세요.  

   > [!Important]  
   >  **표준 옵션을 사용하여 모든 사용자 프로필 캡처** 옵션과 함께 [사용자 상태 캡처](/sccm/osd/understand/task-sequence-steps#BKMK_CaptureUserState) 단계를 사용하면 **사용자 상태 복원** 단계의 **로컬 컴퓨터 사용자 프로필 복원** 설정을 선택해야 합니다. 그렇지 않으면 작업 순서가 실패합니다.  

   > [!Note]  
   > 로컬 하드 링크를 사용하여 사용자 상태를 저장했는데 복원에 성공하지 못하는 경우 데이터를 저장하기 위해 만든 하드 링크를 직접 삭제하세요. 작업 순서에서 USMTUtils 도구를 실행하여 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계에서 이 작업을 자동화할 할 수 있습니다. USMTUtils를 사용하여 하드 링크를 삭제하는 경우 USMTUtils를 실행한 후 [컴퓨터 다시 시작](/sccm/osd/understand/task-sequence-steps#BKMK_RestartComputer) 단계를 추가해야 합니다.  

3. 상태 마이그레이션 지점을 사용하여 사용자 상태를 저장하는 경우 **상태 저장소 해제** 단계를 작업 순서에 추가합니다. **작업 순서 편집기**에서 **추가**를 클릭합니다. **사용자 상태**를 가리킨 다음, **상태 저장소 해제**를 클릭합니다. 이 단계에 대한 속성 및 옵션을 구성한 다음, **적용**을 클릭합니다. 사용할 수 있는 설정에 대한 자세한 내용은 [상태 저장소 해제](/sccm/osd/understand/task-sequence-steps#BKMK_ReleaseStateStore)를 참조하세요.  

   > [!IMPORTANT]  
   >  **상태 저장소 해제** 단계 이전에 실행되는 작업 순서 작업은 **상태 저장소 해제** 단계가 시작되기 전에 모두 성공적으로 수행되어야 합니다.  


 대상 컴퓨터에서 사용자 상태를 복원할 수 있도록 이 작업 순서를 배포합니다. 작업 순서를 배포하는 방법에 대한 자세한 내용은 [작업 순서 배포](/sccm/osd/deploy-use/deploy-a-task-sequence)를 참조하세요.  



## <a name="next-steps"></a>다음 단계

[작업 순서 배포 모니터링](/sccm/osd/deploy-use/monitor-operating-system-deployments#BKMK_TSDeployStatus)
