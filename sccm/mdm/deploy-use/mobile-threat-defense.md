---
title: 위험에 따라 액세스 제한
titleSuffix: Configuration Manager
description: 디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스를 제한합니다.
ms.date: 08/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 61dbf9f7835a8ca88ae5bf3bbdfb87011d8b8c0a
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75826750"
---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스 관리

*적용 대상: Configuration Manager (현재 분기)*

Mobile Threat Defense 커넥터를 사용하면 선택한 모바일 위협 방어 공급업체를 준수 정책 및 조건부 액세스 규칙의 정보 소스로 활용할 수 있습니다. 이 경우 특히 손상된 모바일 디바이스에서 Exchange 및 Sharepoint와 같은 조직 리소스에 보호 계층을 추가할 수 있습니다.

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 [기능은 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  



## <a name="what-problem-does-this-solve"></a>어떤 문제를 해결합니까?

조직은 OS 취약성뿐만 아니라 물리적, 앱 기반 및 네트워크 기반 위협 등 새로운 위협으로부터 중요한 데이터를 보호해야 합니다.

지금까지 조직은 공격으로부터 PC를 보호하는 데 사전 예방적인 자세를 취해 왔지만 모바일 디바이스는 모니터링 및 보호되지 않고 있습니다. 모바일 플랫폼에는 앱 격리 및 소비자 앱 스토어 점검과 같은 기본 제공 보호 기능이 있지만 이러한 플랫폼은 정교한 공격에 여전히 취약합니다. 오늘날 업무에 디바이스를 사용하며 중요한 정보에 액세스해야 하는 직원이 늘어나고 있습니다. 따라서 점점 더 정교한 공격으로부터 디바이스를 보호해야 합니다.



## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 커넥터의 작동 방식

커넥터는 Intune과 선택한 모바일 위협 방어 공급업체 간에 통신 채널을 만들어 조직 리소스를 보호합니다. Intune Mobile Threat Defense 파트너는 직관적이고 배포하기 쉬운 모바일 디바이스용 애플리케이션을 제공합니다. 이 애플리케이션은 Intune과 공유할 위협 정보를 적극적으로 검색하고 분석합니다. 보고 또는 적용하려면 이 정보를 사용하세요. 

예를 들어 연결된 Mobile Threat Defense 앱이 Mobile Threat Defense 공급업체에 디바이스가 메시지 가로채기(man-in-the-middle) 공격에 취약한 네트워크에 현재 연결되어 있다고 보고하는 경우 이 정보는 공유되며 적절한 위험 수준(낮음/중간/높음)으로 분류됩니다. 이 위험을 Intune에서 구성된 허용 위험 수준과 비교하여 디바이스가 손상되어 있는 동안 선택한 특정 리소스에 대한 액세스를 철회할지 여부를 결정하세요.



## <a name="sample-scenarios"></a>샘플 시나리오:

모바일 위협 방어 솔루션에서 디바이스가 감염된 것으로 간주되는 경우

![Mobile Threat Defense 감염된 디바이스](../media/mtp/MTD-image-1.png)

디바이스를 재구성하면 액세스가 허용됩니다.

![Mobile Threat Defense 액세스 허용됨](../media/mtp/MTD-image-2.png)



## <a name="next-steps"></a>다음 단계

다음을 사용하여 디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스를 보호하는 방법을 알아봅니다.

- [Lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)
