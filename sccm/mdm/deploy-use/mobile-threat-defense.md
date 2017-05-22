---
title: "위험에 따라 액세스 제한 | Microsoft Docs"
description: "장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스를 제한합니다."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 250671660c1c6da0ca9b593b06b8f344dfe17ad6
ms.contentlocale: ko-kr
ms.lasthandoff: 05/04/2017


---

# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Mobile Threat Defense 커넥터를 사용하면 선택한 모바일 위협 방어 공급업체를 준수 정책 및 조건부 액세스 규칙의 정보 소스로 활용할 수 있습니다. 이 경우 IT 관리자가 특히 손상된 모바일 장치에서 Exchange 및 Sharepoint와 같은 회사 리소스에 보호 계층을 추가할 수 있습니다.

## <a name="what-problem-does-this-solve"></a>이 기능을 통해 어떤 문제가 해결되나요?

회사는 OS 취약점뿐만 아니라 물리적 위협, 앱 기반 위협, 네트워크 기반 위협 등 출현하는 위협에서 중요한 데이터를 보호해야 합니다.
지금까지 회사는 공격으로부터 PC를 보호하는 데 사전 예방적인 자세를 취해 왔지만 모바일 장치는 모니터링 및 보호되지 않고 있습니다. 모바일 플랫폼에는 앱 격리 및 소비자 앱 스토어 점검과 같은 기본 제공 보호 기능이 있지만 이러한 플랫폼은 정교한 공격에 여전히 취약합니다. 오늘날 업무에 장치를 사용하며 중요한 정보에 액세스해야 하는 직원이 늘어나고 있습니다. 따라서 점점 더 정교한 공격으로부터 장치를 보호해야 합니다.

[하이브리드 MDM 배포(SCCM 및 Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)는 Mobile Threat Defense 파트너 등의 장치 위협 방지 솔루션에서 제공하는 위험 평가에 따라 회사 리소스 및 데이터에 대한 액세스를 제어하는 기능을 제공합니다.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 커넥터의 작동 방식

커넥터는 Intune과 선택한 모바일 위협 방어 공급업체 간에 통신 채널을 만들어 회사 리소스를 보호합니다. Intune Mobile Threat Defense 파트너는 직관적이고 배포하기 쉬운 모바일 장치용 응용 프로그램을 제공합니다. 이 응용 프로그램은 보고 또는 적용을 위해 Intune과 공유할 위협 정보를 적극적으로 검색하고 분석합니다. 예를 들어 연결된 Mobile Threat Defense 앱이 Mobile Threat Defense 공급업체에 네트워크의 휴대폰이 메시지 가로채기(man-in-the-middle) 공격에 취약한 네트워크에 현재 연결되어 있다고 보고하는 경우 이 정보는 공유되며 적절한 위험 수준(낮음/중간/높음)으로 분류됩니다. 그런 다음 Intune에서 구성된 허용 위험 수준과 비교하여 장치가 손상된 동안 선택한 특정 리소스에 대한 액세스를 해지할지 여부를 확인할 수 있습니다.

## <a name="sample-scenarios"></a>샘플 시나리오:

Mobile Threat Defense 솔루션에서 장치가 감염된 것으로 간주되는 경우

![Mobile Threat Defense 감염된 장치](../media/mtp/MTD-image-1.png)

장치를 재구성하면 액세스가 허용됩니다.

![Mobile Threat Defense 액세스 허용됨](../media/mtp/MTD-image-2.png)

## <a name="next-steps"></a>다음 단계

다음을 사용하여 장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스를 보호하는 방법을 알아봅니다.

- [Lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)
