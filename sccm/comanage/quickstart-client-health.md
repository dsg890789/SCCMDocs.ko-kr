---
title: 공동 관리를 사용하는 클라이언트 상태
titleSuffix: Configuration Manager
description: Azure Portal의 Intune에서 Configuration Manager 클라이언트 상태의 표시 여부 관리
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 5b243aac-8a1a-4f14-ba3f-5446bb483e92
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6838371a80530d5ab66abd9d8a976af41513e15
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62193850"
---
# <a name="client-health-with-co-management"></a>공동 관리를 사용하는 클라이언트 상태

네트워크의 상태는 해당 네트워크로 들어오고 나가는 디바이스의 상태와 직접 관계가 있습니다. Intune은 비정상 클라이언트와 통신할 수 있으며, 비정상 클라이언트가 네트워크에 없어도 통신할 수 있습니다. 공동 관리를 사용하면 이 기능을 Configuration Manager의 기능과 결합하여 알려진 정상 클라이언트의 98%를 다시 보고할 수 있습니다. 따라서 모든 클라이언트를 실시간으로 검색, 평가 및 표시할 수 있습니다. 또한 Intune에서는 연결된 모든 클라이언트에서 준수 업그레이드에 필요한 지원도 추가합니다.

다음 비디오에서는 선임 프로그램 관리자 Rob York와 제품 마케팅 관리자 Locky Ainley가 공동 관리를 사용하는 클라이언트 상태에 관해 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Client-Health-Monitoring-with-Co-Management/player]



## <a name="benefits"></a>이점

클라이언트 상태를 평가하는 것이 무엇보다 중요합니다. System Center 2012 Configuration Manager에서는 **CCMeval**을 추가했습니다. 이 유틸리티는 Configuration Manager 클라이언트 외부에 있고, 클라이언트 상태 모니터링 및 자동 업데이트 관리를 제공합니다. 그러나 이 보고에서는 물리적 또는 가상으로 내부 네트워크에 있는 디바이스를 사용합니다. 공동 관리를 사용하면 이 문제를 해결할 수 있습니다.

공동 관리를 사용하면 Intune이 클라이언트 성능 상태를 보고할 수 있습니다. 즉, 데이터의 유효성에 대한 타임스탬프 정보를 제공합니다. 이 정보를 통해 디바이스가 정상인지, 연결할 수 있는지, 앱을 설치할 수 있는지 또는 필요한 OS 빌드로 업데이트할 수 있는지 알 수 있습니다. 

이 기능의 자세한 개요를 알아보려면 Ignite 2018의 [What's New in Configuration Manager](https://myignite.techcommunity.microsoft.com/sessions/64591)(Configuration Manager의 새로운 기능)에서 이 비디오를 시청하세요.

> [!VIDEO https://www.youtube.com/embed/UAW2KBUq7DM?start=518]


Configuration Manager에서 클라이언트가 설치된 디바이스 상태를 제공하지만 클라이언트가 설치되지 않은 경우 Intune에서 클라이언트에 연결하지 않고 추가 정보를 제공할 수 있습니다. Intune의 디바이스 상태 정보는 이해하기 쉽습니다. 상태가 **정상**이 아니면 Intune은 권장 사항과 문제 해결을 위한 다음 단계를 제공합니다.

> [!Note]  
> 이후 버전에 제공할 계획인 이점은 다음과 같습니다.
> - Configuration Manager에서 CCMeval에 추가 기능을 포함합니다.  
> - Configuration Manager와 Intune 모두에서 잠재적인 비정상 머신을 더 쉽게 식별할 수 있습니다.  
> - Intune에서 클라이언트 상태 데이터를 그룹화할 수 있습니다.  



## <a name="value-proposition"></a>가치 제안

이 기능을 사용하여 Intune에 외부 데이터 원본을 포함할 수 있습니다. 이를 통해 다양한 클라이언트 문제를 해결할 때 다음 단계를 결정할 수 있습니다. 이제 추가 보고서를 작성하거나 다른 도구를 사용하여 클라이언트 데이터를 끌어올 필요가 없습니다.

정상 클라이언트가 있으면 패치 준수를 쉽게 업데이트할 수 있습니다. 패치 준수가 나아지면 보안도 향상됩니다.



## <a name="configure"></a>구성

이 기능을 시작하려면 다음 단계를 따릅니다.

- 디바이스를 Windows 10 버전 1709 이상으로 업데이트  

- [공동 관리 사용](/sccm/comanage/how-to-enable)  
    - 모든 워크로드를 Intune으로 전환할 필요는 없음  

- Configuration Manager 사이트 및 클라이언트를 *버전 1806* 이상으로 업데이트  


### <a name="review-configuration-manager-client-health-in-intune"></a>Intune에서 Configuration Manager 클라이언트 상태 검토

1. 로그인은 [Azure 포털](https://portal.azure.com/)합니다.  

2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.  

3. **Microsoft Intune** 창이 열리면 **도움말 및 지원** 아래의 메뉴에서 **문제 해결** 페이지로 이동합니다.  

4. **사용자 선택** 옵션을 사용하고 **디바이스** 목록에서 특정 디바이스를 찾고 선택하여 디바이스 페이지를 엽니다.  

5. 공동 관리 정보는 디바이스 페이지의 맨 아래에 표시됩니다. 이 정보에는 다음과 같은 클라이언트 상태 필드가 포함됩니다.  
    - **Configuration Manager 에이전트 상태**  
    - **마지막 Configuration Manager 에이전트 체크 인 시간**  

> [!Tip]  
> Intune에 등록된 디바이스는 하루에 3번, 대략 8시간마다 클라우드 서비스에 연결합니다. 
