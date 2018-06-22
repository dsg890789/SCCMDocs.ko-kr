---
title: 모바일 위협 방어
titleSuffix: Configuration Manager
description: Configuration Manager 및 Intune Mobile Threat Defense 파트너를 사용하여 장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스를 제한합니다.
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6aeed0c7e509ee96b226f5d1c7649bcf84af3af8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347606"
---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Configuration Manager의 Intune Mobile Threat Defense 커넥터

*적용 대상: System Center Configuration Manager(현재 분기)*

[하이브리드 MDM 배포(SCCM 및 Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) 및 Intune과 Mobile Threat Defense 파트너 간의 통합은 장치 위험 평가에 따라 회사 리소스 및 데이터에 대한 액세스를 제어하는 기능을 제공합니다.

Intune Mobile Threat Defense 커넥터를 사용하면 선택한 모바일 위협 방어 공급업체를 준수 정책 및 조건부 액세스 규칙의 정보 소스로 활용할 수 있습니다. 이 경우 IT 관리자가 특히 손상된 모바일 장치에서 Exchange 및 Sharepoint와 같은 회사 리소스에 보호 계층을 추가할 수 있습니다.

## <a name="what-problem-does-this-solve"></a>이 기능을 통해 어떤 문제가 해결되나요?

회사는 OS 취약점뿐만 아니라 물리적 위협, 앱 기반 위협, 네트워크 기반 위협 등 출현하는 위협에서 중요한 데이터를 보호해야 합니다.
지금까지 회사는 공격으로부터 PC를 보호하는 데 사전 예방적인 자세를 취해 왔지만 모바일 장치는 모니터링 및 보호되지 않고 있습니다. 모바일 플랫폼에는 앱 격리 및 소비자 앱 스토어 점검과 같은 기본 제공 보호 기능이 있지만 이러한 플랫폼은 정교한 공격에 여전히 취약합니다. 오늘날 업무에 장치를 사용하며 중요한 정보에 액세스해야 하는 직원이 늘어나고 있습니다. 따라서 점점 더 정교한 공격으로부터 장치를 보호해야 합니다.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 커넥터의 작동 방식

커넥터는 Intune과 선택한 모바일 위협 방어 공급업체 간에 통신 채널을 만들어 회사 리소스를 보호합니다. Intune Mobile Threat Defense 파트너는 직관적이고 배포하기 쉬운 모바일 장치용 응용 프로그램을 제공합니다. 이 응용 프로그램은 보고 또는 적용을 위해 Intune과 공유할 위협 정보를 적극적으로 검색하고 분석합니다. 예를 들어 연결된 Mobile Threat Defense 앱이 Mobile Threat Defense 공급업체에 네트워크의 휴대폰이 메시지 가로채기(man-in-the-middle) 공격에 취약한 네트워크에 현재 연결되어 있다고 보고하는 경우 이 정보는 공유되며 적절한 위험 수준(낮음/중간/높음)으로 분류됩니다. 그런 다음 Intune에서 구성된 허용 위험 수준과 비교하여 장치가 손상된 동안 선택한 특정 리소스에 대한 액세스를 해지할지 여부를 확인할 수 있습니다.

## <a name="sample-scenarios"></a>샘플 시나리오:

Mobile Threat Defense 솔루션에서 장치가 감염된 것으로 간주되는 경우

![](http://i.imgur.com/Li1WUOU.png)

장치를 재구성하면 액세스가 허용됩니다.

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense 파트너

다음을 사용하여 장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스를 보호하는 방법을 알아봅니다.

- [Lookout](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
