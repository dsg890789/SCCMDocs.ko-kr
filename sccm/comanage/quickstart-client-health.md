---
title: 공동 관리를 사용 하 여 클라이언트 상태
titleSuffix: Configuration Manager
description: Azure portal의 Intune에서 Configuration Manager 클라이언트 상태 표시를 유지 관리
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
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755325"
---
# <a name="client-health-with-co-management"></a>공동 관리를 사용 하 여 클라이언트 상태

네트워크의 상태는 해당 내부 및 외부로 이동 하는 장치의 상태에 직접 연결 됩니다. 네트워크에서 그렇지 않을 경우에 Intune는 정상적인 상태가 아닌 클라이언트를 사용 하 여 통신할 수 있습니다. 공동 관리를 사용 하 여 알려진 정상 클라이언트 98%에 다시 보고 하려면 Configuration Manager의 기능을 사용 하 여이 기능을 결합 합니다. 그런 다음 검색 하 고, 평가 하 고, 실시간으로 모든 클라이언트에서 가시성을 제공할 수 있습니다. Intune에는 연결 된 모든 클라이언트에서 규정 준수 업그레이드에 대 한 필요한 지원이 추가 되었습니다.

다음 비디오에서는 수석 프로그램 관리자 Rob York 및 제품 마케팅 관리자 Locky Ainley 설명 및 공동 관리를 사용 하 여 클라이언트 상태를 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Client-Health-Monitoring-with-Co-Management/player]



## <a name="benefits"></a>이점

클라이언트 상태를 평가 하는 것이 가장 우선 합니다. System Center 2012 Configuration Manager 추가 **CCMeval**합니다. 이 유틸리티는 Configuration Manager 클라이언트를 외부입니다. 클라이언트 상태 모니터링 및 자동 업데이트 관리를 제공합니다. 그러나 물리적으로 장치 또는 내부 네트워크에 거의 사용이 보고 합니다. 공동 관리는이 문제를 해결 하는 데 도움이 됩니다.

공동 관리를 사용 하 여 Intune 클라이언트 상태에 보고할 수 있습니다. 데이터의 유효성에 대 한 타임 스탬프 정보를 제공 합니다. 이 정보를 알려 줍니다 빌드 장치는 정상, 연결할 앱을 설치할 수 있습니다 하거나 필요한 OS로 업데이트할 수 있습니다. 

이 기능의 자세한 개요를 보려면이 비디오에서 합니다 [What's New in Configuration Manager](https://myignite.techcommunity.microsoft.com/sessions/64591) Ignite 2018 세션입니다.

> [!VIDEO https://www.youtube.com/embed/UAW2KBUq7DM?start=518]


Configuration Manager 클라이언트가 설치 되어 있지만 실행 되어 있지는 장치 상태에서 제공 하는 경우 Intune 클라이언트에 연결할 필요 없이 자세한 정보를 제공할 수 있습니다. Intune에서 장치 상태 정보를 이해 하기 쉽습니다. 상태가 이면 아무 것도 이외의 **정상**, 권장 사항 및 문제 해결 및 해결 하기 위한 다음 단계를 제공 합니다.

> [!Note]  
> 다음과 같은 이점은 이후 버전에 대 한 계획:
> - Configuration Manager CCMeval에 추가 기능을 포함 합니다.  
> - Configuration Manager와 Intune에서 컴퓨터를 잠재적으로 비정상을 식별 하기 쉬운 것  
> - Intune에서 클라이언트 상태 데이터를 그룹화 할 수 있습니다.  



## <a name="value-proposition"></a>가치 제안

이 기능을 이제 Intune 사용 하 여 외부 데이터 원본입니다. 다양 한 클라이언트 문제를 해결 하는 경우 다음 단계를 확인할 수 있습니다. 이제 추가 보고서를 만들거나 클라이언트 데이터를 다른 도구를 사용할 필요가 없습니다.

정상적인 클라이언트만 경우 패치 호환성 즉시 업데이트. 더 나은 패치 호환성 향상 된 보안을 의미합니다.



## <a name="configure"></a>구성

이 기능을 사용 하 여 시작 하려면 다음 단계를 사용 합니다.

- Windows 10 버전 1709 이상으로 장치 업데이트  

- [공동 관리를 사용 하도록 설정](/sccm/comanage/how-to-enable)  
    - 모든 워크 로드를 Intune로 전환 하지 않아도 됩니다.  

- Configuration Manager 사이트 및 클라이언트를 업데이트할 *버전 1806* 이상  


### <a name="review-configuration-manager-client-health-in-intune"></a>Intune에서 Configuration Manager 클라이언트 상태를 검토 합니다.

1. [Azure 포털](https://portal.azure.com/)할 수 있습니다.  

2. 선택할 **모든 서비스** > **Intune**합니다. Intune에는 **모니터링 + 관리** 섹션입니다.  

3. 연 후 합니다 **Microsoft Intune** 창 메뉴에서 **도움말 및 지원**로 이동 합니다 **문제 해결** 페이지.  

4. 사용 하 여는 **사용자 선택** 옵션을에서 특정 장치를 찾을 합니다 **장치** 목록 및 선택 하 여 장치 페이지를 엽니다.  

5. 장치 페이지의 맨 아래에서 공동 관리 정보가 표시 됩니다. 이 정보에는 클라이언트 상태에 대 한 다음 필드가 포함 됩니다.  
    - **Configuration Manager 에이전트 상태**  
    - **마지막 구성 관리자 에이전트 체크 인 시간**  

> [!Tip]  
> Intune에 등록 된 장치는 하루에 3 번, 대략 8 시간 마다 클라우드 서비스에 연결합니다. 
