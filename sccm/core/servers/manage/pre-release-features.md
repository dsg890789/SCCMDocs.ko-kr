---
title: 시험판 기능
titleSuffix: Configuration Manager
description: 시험판 기능은 프로덕션 환경에서의 초기 테스트를 위해 현재 분기에 포함된 기능입니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 04d23383d13e981d8a48f88e84444df1ac4915fe
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39386044"
---
# <a name="pre-release-features-in-configuration-manager"></a>Configuration Manager 시험판 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

시험판 기능은 프로덕션 환경에서의 초기 테스트를 위해 현재 분기에 포함된 기능입니다. 이러한 기능은 완전히 지원되지만 아직 개발 과정에 있습니다. 시험판 범주에서 벗어날 때까지는 변경이 있을 수 있습니다.



## <a name="give-consent"></a>동의  

시험판 기능을 사용하려면 먼저 시험판 기능 사용에 대한 동의가 필요합니다. 동의는 실행 취소할 수 없고 계층 구조당 1회가 필요한 작업입니다. 동의할 때까지 업데이트에 포함된 새 시험판 기능을 사용하도록 설정할 수 없습니다. 시험판 기능을 설정한 후에는 해제할 수 없습니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 리본에서 **계층 구조 설정**을 클릭합니다.  

3. 계층 구조 설정 속성의 **일반** 탭에서 **시험판 기능 사용 동의** 옵션을 사용하도록 선택합니다. **확인**을 클릭합니다.  



## <a name="enabling-pre-release-features"></a>시험판 기능을 사용하도록 설정

시험판 기능이 포함된 업데이트를 설치하는 경우 이러한 기능은 업데이트에 포함된 일반 기능과 함께 업데이트 및 서비스 마법사에 표시됩니다.

#### <a name="if-you-have-given-consent"></a>사용자가 동의하는 경우
업데이트 및 서비스 마법사에서 시험판 기능을 사용하도록 설정합니다. 다른 모든 기능에서와 마찬가지로 시험판 기능을 선택합니다.     

또는 **관리** 작업 영역에서 **업데이트 및 서비스**의 **기능** 노드에서 나중에 시험판 기능을 사용하도록 설정하게 대기합니다. 기능을 선택한 다음, 리본 메뉴에서 **켜기**를 클릭합니다. 동의할 때까지 이 옵션을 사용할 수 없습니다.

#### <a name="if-you-havent-given-consent"></a>사용자가 동의하지 않는 경우
업데이트 및 서비스 마법사에 시험판 기능이 표시는 되지만 사용하도록 설정할 수는 없습니다. 업데이트를 설치한 후에 **기능** 노드에서 이러한 기능을 볼 수 있습니다. 그러나 사용자가 동의할 때까지 사용하도록 설정할 수는 없습니다.


> [!Important]  
> 다중 사이트 계층에서는 중앙 관리 사이트에서만 선택적 또는 시험판 기능을 활성화할 수 있습니다. 이 동작은 계층 전체에 충돌이 발생하지 않도록 합니다. <!--507197-->  
> 
> 독립 실행형 기본 사이트에서 동의를 제공한 다음, 새 중앙 관리 사이트를 설치하여 계층 구조를 확장하는 경우 중앙 관리 사이트에서 다시 동의를 제공해야 합니다.  

시험판 기능을 사용하도록 설정하면 Configuration Manager HMAN(계층 구조 관리자)은 해당 기능을 사용할 수 있게 되기 전에 변경 내용을 처리해야 합니다. 변경 처리는 즉시 이루어지는 경우가 많습니다. HMAN 처리 주기에 따라 완료에 최대 30분이 소요될 수 있습니다. 변경 처리 후에는 기능을 사용하기 전에 먼저 콘솔을 다시 시작합니다.



## <a name="pre-release-features"></a>시험판 기능

<!--Note/tip for target article

> [!Note]  
> In this version of Configuration Manager, <feature name> is a pre-release feature. To enable it, see [Pre-release features](/sccm/core/servers/manage/pre-release-features).  


> [!Tip]  
> This feature was first introduced in version 1702 as a [pre-release feature](/sccm/core/servers/manage/pre-release-features). Beginning with version 1706, this feature is no longer a pre-release feature.  

-->


| 기능          | 시험판으로 추가됨 | 전체 기능으로 추가됨 |  
|------------------|----------------------|-------------------------|
| 향상된 HTTP 사이트 시스템<!--1356889,1358228--> |버전 1806|![아직 추가되지 않음](media/red_x.png)|
| 공동 관리하는 장치용 모바일 앱<!--1357892-->|[버전 1806](/sccm/core/clients/manage/co-management-switch-workloads#workloads-able-to-be-transitioned-to-intune)|![아직 추가되지 않음](media/red_x.png)|
| Package Conversion Manager<!--1357861-->|버전 1806|![아직 추가되지 않음](media/red_x.png)|
| Cisco AnyConnect 4.0.07x 및 이후에 iOS에 대한 지원<!--1357393-->|[1802 버전](/sccm/mdm/deploy-use/create-vpn-profiles)| [업데이트 4163547 적용 1802 버전](/sccm/mdm/deploy-use/create-vpn-profiles) |
| 단계별 배포<!--1356837-->|[1802 버전](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)|[1806 버전](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)|
| 작업 순서 실행 단계 <!-- 1261338 --> |  [버전 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence) |[1802 버전](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#add-child-task-sequences-to-a-task-sequence)|
| Windows Defender Exploit Guard <!-- 1355468 --> |  [버전 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) |[1802 버전](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy)|
| 조건부 액세스의 준수 정책에 대한 장치 상태 증명 평가<!-- 1235616 --> |  [버전 1710](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm) |[1802 버전](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)|
| Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행 <!-- 1236459 --> |  [버전 1706](/sccm/apps/deploy-use/create-deploy-scripts)|[1802 버전](/sccm/apps/deploy-use/create-deploy-scripts)|
| Microsoft Surface 드라이버 업데이트 관리<!-- 1098490 --> |  [버전 1706](/sccm/sum/get-started/configure-classifications-and-products) | [버전 1710](/sccm/sum/get-started/configure-classifications-and-products)|
| Configuration Manager로 Device Guard 관리 <!-- 1319346 --> |  [버전 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![아직 추가되지 않음](media/red_x.png)|
| 작업 순서 콘텐츠 사전 캐싱 <!-- 1021244 --> |  [버전 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content) | [버전 1710](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
| 응용 프로그램을 설치하기 전에 실행 중인 실행 파일 확인 <!-- 1284624 --> |   [버전 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |[버전 1706](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application)|
| 데이터 웨어하우스 서비스 지점 <!-- 1277922 --> |  [버전 1702](/sccm/core/servers/manage/data-warehouse) |[버전 1706](/sccm/core/servers/manage/data-warehouse)|
| 클라이언트에 콘텐츠 배포를 위한 피어 캐시 <!-- 1101436 --> |  [버전 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) | [버전 1710](/sccm/core/plan-design/hierarchy/client-peer-cache)|
| 클라우드 관리 게이트웨이 <!-- 1101764 --> |  [버전 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |[1802 버전](/sccm/core/clients/manage/plan-cloud-management-gateway)|
| Microsoft Operations Management Suite 커넥터 <!-- 1236739 --> | [버전 1606](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) |[1802 버전](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)|
| 클러스터 인식 컬렉션 서비스(서버 그룹 서비스) <!-- 1081776 --> | [버전 1602](/sccm/core/get-started/capabilities-in-technical-preview-1605#BKMK_ServerGroups)|![아직 추가되지 않음](media/red_x.png)|
| System Center Configuration Manager에서 관리하는 PC에 대한 조건부 액세스 <!--  --> | [버전 1602](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)     | [버전 1702](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)                     |
<!--Image used = ![Not yet](media/red_x.png) -->

> [!Tip]  
> 사용하기 전에 활성화해야 하는 시험판 이외 기능에 대한 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  
> 
> 기술 미리 보기 분기에만 제공되는 기능에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.  
