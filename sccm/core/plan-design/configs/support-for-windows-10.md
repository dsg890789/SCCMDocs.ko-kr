---
title: Windows 10에 대한 지원
titleSuffix: Configuration Manager
description: System Center Configuration Manager가 OSD나 클라이언트로 지원되는 Windows 10 버전에 대해 알아보세요.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 877732c4095438b19a863335a4a0026b7b088b24
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2018
---
# <a name="support-for-windows-10-in-system-center-configuration-manager"></a>System Center Configuration Manager의 Windows 10에 대한 지원  

*적용 대상: System Center Configuration Manager(현재 분기)*


다음을 포함하여 Configuration Manager가 지원하는 Windows 10 버전에 대해 알아봅니다.
 -  Configuration Manager 클라이언트인 Windows 10
 -  Windows 10용 Windows ADK(평가 및 배포 키트)

## <a name="windows-10-as-a-client"></a>클라이언트인 Windows 10
새로운 Windows 10 버전이 지원되기 전에 Configuration Manager를 클라이언트로써 최대한 빨리 지원하려고 합니다. 제품마다 별도의 개발 및 릴리스 일정이 있으므로 Configuration Manager에서 제공하는 지원은 각 제품의 지원 시점에 따라 달라집니다.

예를 들어 Configuration Manager 버전은 [해당 버전의 지원](/sccm/core/servers/manage/current-branch-versions-supported)이 종료되면 매트릭스에서 삭제됩니다. 마찬가지로 Enterprise 2015 LTSB 또는 1511과 같은 Windows 10 버전의 지원이 제거될 때 매트릭스에서 삭제됩니다. 자세한 내용은 [사용되지 않는 운영 체제](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-client#deprecated-client-operating-systems)를 참조하세요.


-   다음 정보는 [클라이언트 및 장치에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)를 보완합니다.
-   Configuration Manager의 장기 서비스 분기를 사용하는 경우 [장기 서비스 분기에 대해 지원되는 구성](/sccm/core/understand/supported-configurations-for-ltsb)을 참조하세요.

| Windows 10 버전 | Configuration Manager 1706 | Configuration Manager 1710 | Configuration Manager 1802 |
|---------------------|-----|-----|-----|
| Enterprise 2015 LTSB            <!--10/14/2025-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| Enterprise 2016 LTSB            <!--10/13/2026-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1607   <br />(*버전 참조*)   <!--04/10/2018-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1703   <br />(*버전 참조*)   <!--10/09/2018-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1709   <br />(*버전 참조*)   <!--04/09/2019-->   | ![이전 버전과 호환](media/blue_compat.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |

<!-- lifecycle reference: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet -->

**버전:** Enterprise, Pro, Education, Pro Education   

|키|
|--|
|![지원됨](media/green_check.png) = **지원됨**  |
|![이전 버전과 호환](media/blue_compat.png)  = **이전 버전과 호환** - 기존 클라이언트 관리 기능은 새 Windows 10 버전을 사용해야 합니다. 예를 들어 하드웨어 인벤토리, 소프트웨어 인벤토리 및 소프트웨어 업데이트 등입니다. 알려진 문제 또는 주의 사항을 문서화합니다. <br><br>이 방법은 새 Configuration Manager 업데이트 버전을 요구하지 않고 응용 프로그램 호환성 지원을 사용하여 새 Windows 버전을 즉시 배포하고 관리할 수 있습니다. |
|![지원 안 됨](media/Red_X.png) = **지원 안 됨**|

 > [!NOTE]
 > 버전 1802부터 Configuration Manager는 Windows 10 ARM64 장치의 클라이언트를 지원합니다. 기존 클라이언트 관리 기능도 이러한 새 장치에서 작동합니다. 예를 들어 하드웨어 및 소프트웨어 인벤토리, 소프트웨어 업데이트, 응용 프로그램 관리 등입니다. 운영 체제 배포는 현재 지원되지 않습니다. <!-- 1353704 --> 



## <a name="windows-10-adk"></a>Windows 10 ADK
Configuration Manager로 운영 체제를 배포할 때 [Windows ADK는 필요한 외부 종속성](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) 입니다.

다음 표에는 여러 버전의 Configuration Manager에서 사용할 수 있는 Windows 10 ADK 버전이 나와 있습니다.

| Windows 10 ADK 버전  | Configuration Manager 1706 | Configuration Manager 1710 | Configuration Manager 1802   |
|--------------------|-----|-----|-----|
| 1607  | ![지원되지 않음](media/Red_X.png)   | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) |
| 1703  | ![지원됨](media/green_check.png) | ![이전 버전과 호환](media/blue_compat.png) | ![이전 버전과 호환](media/blue_compat.png) |
| 1709  | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |

|키|
|--|
|![지원됨](media/green_check.png) = **지원됨** - 배포하는 Windows 버전과 일치하는 Windows ADK를 사용하는 것이 좋습니다. 예를 들어 Windows 10 버전 1703을 배포할 때는 Windows 10용 Windows ADK 버전 1703을 사용합니다. Windows ADK 구성 요소 지원 가능성에 대한 자세한 내용은 [DISM 지원 플랫폼](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) 및 [USMT 요구 사항](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1)을 참조하세요. |
|![이전 버전과 호환](media/blue_compat.png)  = **이전 버전과 호환** - 이 조합은 테스트되지 않았지만 작동합니다. 알려진 문제 또는 주의 사항을 문서화합니다. |
|![지원 안 됨](media/Red_X.png) = **지원 안 됨**|

 > [!Note]
 > Configuration Manager는 Windows 10 ADK의 x86 및 amd64 구성 요소만을 지원합니다. 현재 arm 또는 arm64 구성 요소를 지원하지 않습니다. 