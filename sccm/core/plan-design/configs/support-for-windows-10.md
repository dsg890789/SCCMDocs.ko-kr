---
title: Windows 10에 대한 지원
titleSuffix: Configuration Manager
description: System Center Configuration Manager가 OSD나 클라이언트로 지원되는 Windows 10 버전에 대해 알아보세요.
ms.date: 05/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3ac15d0039377d4635e531052abcec72503b1c4
ms.sourcegitcommit: d1df13fc95a1f1540177c294555d9be26161b9cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974180"
---
# <a name="support-for-windows-10-in-configuration-manager"></a>Configuration Manager의 Windows 10에 대한 지원  

*적용 대상: System Center Configuration Manager(현재 분기)*

다음을 포함하여 Configuration Manager가 지원하는 Windows 10 버전에 대해 알아봅니다.

- [Configuration Manager 클라이언트인 Windows 10](#windows-10-as-a-client)
- [Windows 10용 Windows ADK(평가 및 배포 키트)](#windows-10-adk)

> [!Tip]
> 클라이언트인 Windows Server 빌드는 연결된 Windows 10 버전과 동일하게 지원됩니다. 예를 들어 Windows Server 2016은 Windows 10 LTSB 2016과 동일한 빌드 버전이고 Windows Server 버전 1803은 Windows 10 버전 1803과 동일한 빌드 버전입니다.
>
> 사이트 시스템인 Windows Server에 대한 자세한 내용은 [Configuration Manager 사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers#the-server-core-installation-of-windows-server-version-1803)를 참조하세요.



## <a name="windows-10-as-a-client"></a>클라이언트인 Windows 10

새로운 Windows 10 버전이 지원되기 전에 Configuration Manager를 클라이언트로써 최대한 빨리 지원하려고 합니다. 제품마다 별도의 개발 및 릴리스 일정이 있으므로 Configuration Manager에서 제공하는 지원은 각 제품의 지원 시점에 따라 달라집니다.

Configuration Manager 버전은 [해당 버전의 지원](/sccm/core/servers/manage/current-branch-versions-supported)이 종료되면 매트릭스에서 삭제됩니다. 마찬가지로 Enterprise 2015 LTSB 또는 1511과 같은 Windows 10 버전의 지원이 제거될 때 매트릭스에서 삭제됩니다.

- Configuration Manager 현재 분기의 최신 버전은 보안 및 중요한 업데이트를 둘 다 받는데, 여기에는 Windows 10 버전 관련 문제에 대한 수정 사항이 포함될 수 있습니다. Microsoft에서 Configuration Manager 현재 분기의 최신 버전을 릴리스하면 이전 버전은 보안 업데이트만 받습니다. 자세한 내용은 [Configuration Manager 현재 분기 버전 지원](/sccm/core/servers/manage/current-branch-versions-supported)을 참조하세요.  

    > [!Note]  
    > Windows 10을 최신 상태로 유지하는 가장 좋은 방법은 Configuration Manager를 최신 상태로 유지하는 것입니다. 자세한 내용은 [Configuration Manager 및 Windows as a Service](/sccm/core/understand/configuration-manager-and-windows-as-service)를 참조하세요.  

- 이 정보는 [클라이언트 및 디바이스에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)를 보완합니다.  

- Configuration Manager의 장기 서비스 분기를 사용하는 경우 [장기 서비스 분기에 대해 지원되는 구성](/sccm/core/understand/supported-configurations-for-ltsb)을 참조하세요.  

<br/>
다음 표에는 여러 버전의 Configuration Manager에서 클라이언트로서 사용할 수 있는 Windows 10 버전이 나와 있습니다.

| Windows 10 버전 | Configuration Manager 1710 | Configuration Manager 1802 | Configuration Manager 1806 | Configuration Manager 1810 | Configuration Manager 1902 |
|---------------------|-----|-----|-----|-----|-----|
| Enterprise 2015 LTSB <!--10/14/2025-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| Enterprise 2016 LTSB <!--10/13/2026-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| Enterprise LTSC 2019 <!--01/09/2029-->   | ![지원되지 않음](media/Red_X.png)   | ![지원되지 않음](media/Red_X.png)   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1703   <!--10/08/2019-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1709   <!--04/14/2020-->   | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1803   <!--11/10/2020-->   | ![지원되지 않음](media/Red_X.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1809   <!--05/11/2021-->   | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| 1903   <!--TBD-->   | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원됨](media/green_check.png) |

<!-- lifecycle reference: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet -->

> [!Note]  
> Windows 10 반기 채널 버전에 대한 지원에는 Enterprise, Pro, Education 및 Pro Education 버전이 포함됩니다.  

| 키 |
|--|
| ![지원됨](media/green_check.png) = **지원됨**  |
| ![지원 안 됨](media/Red_X.png) = **지원 안 됨** |

> [!NOTE]  
> 버전 1802부터 Configuration Manager는 Windows 10 ARM64 디바이스의 클라이언트를 지원합니다. 기존 클라이언트 관리 기능도 이러한 새 디바이스에서 작동합니다. 예를 들어 하드웨어 및 소프트웨어 인벤토리, 소프트웨어 업데이트, 애플리케이션 관리 등입니다. OS 배포는 현재 지원되지 않습니다. <!-- 1353704 -->

Windows 수명 주기에 대한 자세한 내용은 [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조하세요.



## <a name="windows-10-adk"></a>Windows 10 ADK

Configuration Manager로 운영 체제를 배포할 때 Windows ADK는 필요한 외부 종속성입니다. 자세한 내용은 [OS 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment#windows-adk-for-windows-10)을 참조하세요.

> [!Important]  
> Windows 10 버전 1809부터 Windows PE는 별도의 설치 프로그램입니다. 그러나 기능 차이는 없습니다.

<br/>
다음 표에는 여러 버전의 Configuration Manager에서 사용할 수 있는 Windows 10 ADK 버전이 나와 있습니다.

| Windows 10 ADK 버전  | Configuration Manager 1710 | Configuration Manager 1802 | Configuration Manager 1806 | Configuration Manager 1810 | Configuration Manager 1902 |
|--------------------|-----|-----|-----|-----|-----|
| **1703**<br>(10.1.15063) | ![이전 버전과 호환](media/blue_compat.png) | ![이전 버전과 호환](media/blue_compat.png) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) |
| **1709**<br>(10.1.16299) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![이전 버전과 호환](media/blue_compat.png) | ![지원되지 않음](media/Red_X.png)   | ![지원되지 않음](media/Red_X.png) |
| **1803**<br>(10.1.17134) | ![지원되지 않음](media/Red_X.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![이전 버전과 호환](media/blue_compat.png) | ![이전 버전과 호환](media/blue_compat.png) |
| **1809**<br>(10.1.17763) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) |
| **1903**<br>(10.1.18362) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원되지 않음](media/Red_X.png) | ![지원됨](media/green_check.png) |

|키|
|--|
| ![지원됨](media/green_check.png) = **지원됨** <br/> 배포하는 Windows 버전과 일치하는 Windows ADK를 사용하는 것이 좋습니다. 최신 Windows 10 버전을 배포하는 경우 최신 Windows ADK 버전을 사용하세요. 최신 Windows ADK 버전은 Windows 7과 같은 이전 OS 버전의 배포를 지원할 수 있습니다.<!-- SCCMDocs issue 1229 --> Windows ADK 구성 요소 지원 가능성에 대한 자세한 내용은 [DISM 지원 플랫폼](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) 및 [USMT 요구 사항](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1)을 참조하세요. |
| ![이전 버전과 호환](media/blue_compat.png)  = **이전 버전과 호환** <br/> 이 조합은 테스트되지 않지만 작동해야 합니다. 알려진 문제 또는 주의 사항은 문서화할 것입니다. |
| ![지원 안 됨](media/Red_X.png) = **지원 안 됨** |

> [!Note]  
> Configuration Manager는 Windows 10 ADK의 x86 및 amd64 구성 요소만을 지원합니다. 현재 ARM 또는 ARM64 구성 요소를 지원하지 않습니다.

> [!Tip]
> Windows Server 빌드에는 연관된 Windows 10 버전과 동일한 Windows ADK 요구 사항이 있습니다. 예를 들어, Windows Server 2016은 Windows 10 LTSB 2016과 동일한 빌드 버전입니다.
