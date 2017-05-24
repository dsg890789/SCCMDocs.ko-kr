---
title: "Windows 10에 대한 지원 | Microsoft 문서"
description: "System Center Configuration Manager가 OSD나 클라이언트로 지원되는 Windows 10 버전에 대해 알아보세요."
ms.custom: na
ms.date: 05/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 5
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ed5efcf7b305f8bee6e99e00c5285f6ae7033d82
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>System Center Configuration Manager의 Windows 10에 대한 지원  

*적용 대상: System Center Configuration Manager(현재 분기)*


 이 항목에서는 다양한 버전의 System Center Configuration Manager 현재 분기에서 사용할 수 있는 Windows 10 버전을 식별합니다. 여기에는 다음 항목이 포함됩니다.
 -  Configuration Manager 클라이언트인 Windows 10
 -  Windows 10 Windows ADK(평가 및 배포 키트)

## <a name="windows-10-as-a-client"></a>클라이언트인 Windows 10
Configuration Manager에서는 Windows 버전이 출시된 후 최대한 빨리 새로운 각 Windows 10 버전을 클라이언트로 지원하려고 합니다. 제품마다 별도의 개발 및 릴리스 일정이 있으므로 Configuration Manager에서 제공하는 지원은 각 제품의 버전 및 분기가 출시되는 시기에 따라 달라집니다.

예를 들어 Configuration Manager 버전은 [해당 버전의 지원](/sccm/core/servers/manage/current-branch-versions-supported)이 종료되면 매트릭스에서 삭제됩니다. 마찬가지로 Enterprise 2015 LTSB 또는 1607(CBB) 같은 Windows 10 버전의 지원은 Configuration Manager의 지원되는 구성 목록에서 제거되면 매트릭스에서 삭제됩니다. 자세한 내용은 [사용되지 않는 운영 체제](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems)를 참조하세요.

-   다음 정보는 [클라이언트 및 장치에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)를 보완합니다.
-   Configuration Manager의 장기 서비스 분기를 사용하는 경우 [장기 서비스 분기에 대해 지원되는 구성](/sccm/core/understand/supported-configurations-for-ltsb)을 참조하세요.

|Windows 10 버전                    |Configuration Manager 1606          |Configuration Manager 1610          |    Configuration Manager 1702 |
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |
|1507 <br />(*버전 참조*)            |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |
|1511(CB), (CBB)<br />(*버전 참조*) |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |
|Enterprise 2016 LTSB                   |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |
|1607(CB)    <br />1주년 업데이트<br />(*버전 참조*)      |![이전 버전과 호환](media/blue_compat.png) |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |
|1607(CBB)    <br />1주년 업데이트<br />(*버전 참조*)      |![지원되지 않음](media/Red_X.png)   |![지원됨](media/green_check.png) |![지원됨](media/green_check.png) |
|1703(CB)    <br />크리에이터 업데이트<br />(*버전 참조*)      |![지원되지 않음](media/Red_X.png)   |![지원되지 않음](media/Red_X.png) |![이전 버전과 호환](media/blue_compat.png) |


**버전:** Enterprise, Pro, Education, Pro Education   

|키|
|--|
|![지원됨](media/green_check.png) = **지원됨**  |
|![지원 안 됨](media/blue_compat.png)  = **이전 버전과 호환** - 기존 클라이언트 관리 기능(하드웨어 인벤토리, 소프트웨어 인벤토리, 소프트웨어 업데이트 등)이 새 Windows 10 현재 분기 빌드 작업에서 작용합니다. 알려진 문제 또는 주의 사항이 문서화됩니다. <br><br>이 방법은 새 Configuration Manager 업데이트 버전을 요구하지 않고 응용 프로그램 호환성 지원을 사용하여 하루 만에 새 Windows 10 CB 빌드를 배포하고 관리할 수 있습니다. |
|![지원됨](media/Red_X.png) = **지원 안 됨**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Configuration Manager로 운영 체제를 배포할 때 [Windows ADK는 필요한 외부 종속성](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) 입니다.

다음 표에는 여러 버전의 Configuration Manager에서 사용할 수 있는 Windows 10 ADK 버전이 나와 있습니다.

|Windows 10 ADK 버전 |Configuration Manager 1606 |Configuration Manager 1610  |Configuration Manager 1702 |
|--------------------|-----|-----|-----|
|1507  |![지원되지 않음](media/Red_X.png)         |![지원되지 않음](media/Red_X.png)  |![지원되지 않음](media/Red_X.png)|
|1511  |![이전 버전과 호환](media/blue_compat.png)|![지원되지 않음](media/Red_X.png)  |![지원되지 않음](media/Red_X.png)|
|1607  |![지원됨](media/green_check.png)       |![지원됨](media/green_check.png)|![이전 버전과 호환](media/blue_compat.png) |
|1703  |![지원되지 않음](media/Red_X.png)         |![지원되지 않음](media/Red_X.png)  |![지원됨](media/green_check.png) |  

|키|
|--|
|![지원됨](media/green_check.png) = **지원됨** - 배포하는 Windows 버전과 일치하는 Windows ADK를 사용하는 것이 좋습니다. 예를 들어 Windows 10 버전 1703을 배포할 때는 Windows 10용 Windows ADK 버전 1703을 사용합니다.  |
|![이전 버전과 호환](media/blue_compat.png)  = **이전 버전과 호환** - 이 조합은 테스트되지 않았지만 작동합니다. 알려진 문제 또는 주의 사항이 문서화됩니다. |
|![지원됨](media/Red_X.png) = **지원 안 됨**|

