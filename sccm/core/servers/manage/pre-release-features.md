---
title: "시험판 기능"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager의 시험판 기능"
ms.custom: na
ms.date: 12/19/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: "36"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 2ef961732431bd4314229e3da6a65df58592342f
ms.sourcegitcommit: 6c2aa79924c0e7fc64ef5e9003498fc00c349db9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>System Center Configuration Manager의 시험판 기능
*적용 대상: System Center Configuration Manager(현재 분기)*

시험판 기능은 프로덕션 환경에서의 초기 테스트를 위해 현재 분기에 포함된 기능입니다. 이러한 기능은 완전하게 지원되지만 아직 개발 중인 상태이므로 시험판 범주에서 벗어날 때까지는 변경될 수 있습니다.

 시험판 기능을 사용하려면 먼저 Configuration Manager 콘솔에서 시험판 기능을 사용한다는 데 동의해야 합니다. 그래야 해당 기능을 선택하고 사용하도록 설정할 수 있습니다.  

동의는 실행 취소할 수 없는 계층당 일회성 작업입니다. 동의할 때까지 업데이트에 포함된 새 시험판 기능을 사용하도록 설정할 수 없습니다. 시험판 기능을 설정한 후에는 해제할 수 없습니다.

동의하려면 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동한 다음 **계층 설정**을 선택합니다. **일반** 탭에서 **시험판 기능 사용 동의**를 선택합니다.

시험판 기능이 포함된 업데이트를 설치하는 경우 이러한 기능은 업데이트에 포함된 일반 기능과 함께 업데이트 및 서비스 마법사에 표시됩니다.
  - **동의하는 경우:** 업데이트를 설치하면 업데이트 및 서비스 마법사에서 시험판 기능을 사용할 수 있습니다. 이렇게 하려면 다른 모든 기능에서와 마찬가지로 시험판 기능을 선택합니다.     

    필요한 경우 나중에 콘솔의 **관리** > **업데이트 및 서비스** > **기능** 노드에서 시험판 기능을 사용하도록 설정할 수 있습니다. **기능** 노드에서 기능을 선택한 다음 **켜기**를 선택합니다. 이 옵션은 사용자가 동의할 때까지 회색으로 표시됩니다. 버전 1702 이전에는 업데이트 및 서비스가 **관리** > **Cloud Services** 아래에 있었습니다.
  -   **동의하지 않은 경우:** 업데이트를 설치할 때 시험판 기능이 업데이트 및 서비스 마법사에 나타나지만, 회색으로 표시되며 사용하도록 설정할 수 없습니다. 업데이트를 설치한 후에 **기능** 노드에서 이러한 기능을 볼 수 있습니다. 그러나 **계층 설정**에서 동의를 해야만 사용하도록 설정할 수 있습니다.

독립 실행형 기본 사이트에서 동의를 제공한 다음 새 중앙 관리 사이트를 설치하여 계층 구조를 확장하는 경우 중앙 관리 사이트에서 다시 동의를 제공해야 합니다.

 시험판 기능을 사용하도록 설정하면 Configuration Manager HMAN(계층 구조 관리자)은 해당 기능을 사용할 수 있게 되기 전에 변경 내용을 처리해야 합니다. 변경 내용 처리는 대개 즉시 이루어지지만, HMAN 처리 주기에 따라 완료하는 데 최대 30분까지 걸릴 수 있습니다. 변경 내용이 처리된 후 콘솔을 다시 시작해야만 해당 기능과 관련된 새 UI를 볼 수 있습니다.

**다음과 같은 시험판 기능을 사용할 수 있습니다.**

 |기능          |시험판으로 추가됨 | 전체 기능으로 추가됨|  
|------------------|---------------------|---------------------|
| 작업 순서 실행 단계 <!-- 1261338 --> |  [버전 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence) |![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Windows Defender Exploit Guard <!-- 1355468 --> |  [버전 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) |![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| 조건부 액세스의 준수 정책에 대한 장치 상태 증명 평가<!-- 1235616 --> |  [버전 1710](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm) |![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행 <!-- 1236459 --> |  [버전 1706](/sccm/apps/deploy-use/create-deploy-scripts)|![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Microsoft Surface 드라이버 업데이트 관리<!-- 1098490 --> |  [버전 1706](/sccm/sum/get-started/configure-classifications-and-products) | [버전 1710](/sccm/sum/get-started/configure-classifications-and-products)|
| Configuration Manager로 Device Guard 관리 <!-- 1319346 --> |  [버전 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| 작업 순서 콘텐츠 사전 캐싱 <!-- 1021244 --> |  [버전 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content) | [버전 1706](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
| 응용 프로그램을 설치하기 전에 실행 중인 실행 파일 확인 <!-- 1284624 --> |   [버전 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |[버전 1706](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application)|
| 데이터 웨어하우스 서비스 지점 <!-- 1277922 --> |  [버전 1702](/sccm/core/servers/manage/data-warehouse) |[버전 1706](/sccm/core/servers/manage/data-warehouse)|
| 클라이언트에 콘텐츠 배포를 위한 피어 캐시 <!-- 1101436 --> |  [버전 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) | [버전 1710](/sccm/core/plan-design/hierarchy/client-peer-cache)|
| 클라우드 관리 게이트웨이 <!-- 1101764 --> |  [버전 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Microsoft Operations Management Suite 커넥터 <!-- 1236739 --> | [버전 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| 클러스터 인식 컬렉션 서비스(서버 그룹 서비스) <!-- 1081776 --> | [버전 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![아직 추가되지 않음](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| System Center Configuration Manager에서 관리하는 PC에 대한 조건부 액세스 <!--  --> | [버전 1602](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)     | [버전 1702](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)                     |
