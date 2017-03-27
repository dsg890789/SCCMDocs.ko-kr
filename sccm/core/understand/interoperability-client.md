---
title: "현재 분기에서 확장된 상호 운용성 클라이언트 사용 | Microsoft 문서"
description: "현재 분기 사이트에서 Configuration Manager 장기 서비스 분기의 클라이언트를 사용하는 방법을 알아봅니다."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
Robots: NOINDEX,NOFOLLOW
translationtype: Human Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 30d0177dc7fcc7f39d00c48067130d587435bf2d
ms.lasthandoff: 12/16/2016

---
# <a name="use-the-client-software-from-the-version-1606-baseline-media-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>이후 버전의 현재 분기 사이트와 확장된 상호 운용성을 위해 버전 1606 기준 미디어의 클라이언트 소프트웨어 사용

*적용 대상: System Center Configuration Manager(현재 분기), (장기 서비스 분기)*  

System Center 2016과 함께 제공된 버전 1606 기준 미디어 DVD 또는 System Center Configuration Manager(현재 분기 및 장기 서비스 분기 1606) 릴리스의 Windows 컴퓨터용 Configuration Manager 클라이언트 소프트웨어(client.msi)를 사용하여 현재 분기 사이트에 속하는 장치를 관리할 수 있습니다. 이 클라이언트를 확장된 상호 운용성 클라이언트라고 합니다.

## <a name="how-this-scenario-works"></a>이 시나리오의 작동 방식:
일반적으로 현재 분기에 대한 새 콘솔 내 업데이트를 설치하는 경우 클라이언트에서 해당 클라이언트 소프트웨어를 자동으로 업데이트하므로 새로운 기능을 사용할 수 있습니다.

이 시나리오에서는 현재 분기를 사용하고 새로운 기능 및 업데이트를 수신합니다. 대부분의 클라이언트는 현재 분기에서 클라이언트 소프트웨어를 실행하며, 해당 클라이언트 소프트웨어를 설치되는 각 버전 업데이트로 업데이트할 수 있습니다. 그러나 클라이언트 소프트웨어 업데이트를 수신하지 않으려는 일부 중요 시스템에는 확장된 상호 운용성 클라이언트를 설치합니다. 이러한 클라이언트는 새 버전의 클라이언트 소프트웨어가 명시적으로 배포될 때까지 새 클라이언트 소프트웨어를 설치하지 않습니다.

새 버전의 Configuration Manager를 설치할 때 현재 분기 클라이언트가 자동으로 업데이트하지 않도록 하는 방법에 대한 자세한 내용은 현재 분기 버전 1610과 함께 제공됩니다.

현재 분기 사이트에서 버전 1606 이상을 실행해야 합니다.

## <a name="the-extended-interoperability-client-software"></a>확장된 상호 운용성 클라이언트 소프트웨어
현재 분기 사이트에서 System Center 2016 또는 System Center Configuration Manager(현재 분기 및 장기 서비스 분기 1606) 릴리스의 확장된 상호 운용성 클라이언트를 사용하는 경우 릴리스의 일반 공급 날짜(2016년 10월 12일)부터 2년 동안 클라이언트가 지원됩니다.

클라이언트 지원이 만료되기 전에 현재 분기에서 관리하는 장치의 확장된 상호 운용성 클라이언트의 업데이트를 계획합니다. 이렇게 하려면 Microsoft에서 새 버전의 클라이언트를 다운로드한 다음 현재 확장된 상호 운용성 클라이언트를 사용하는 장치에 업데이트된 클라이언트 소프트웨어를 배포합니다.

**확장된 상호 운용성 클라이언트의 제한 사항:**
-     콘솔 내 업데이트를 사용하는 경우 확장된 상호 운용성 클라이언트 소프트웨어에 대한 업데이트를 사용할 수 없습니다. 업데이트된 클라이언트가 릴리스될 때 업데이트된 클라이언트 소프트웨어 배포에 대한 추가 정보가 제공됩니다.

## <a name="identify-the-client-version-you-use"></a>사용하는 클라이언트 버전 식별
현재 분기 및 LTSB 둘 다에 사용할 수 있는 주요 클라이언트 버전은 다음과 같습니다.

|클라이언트 버전|분기 및 버전 |  
|----------------|---------------------|
|5.00.8325.xxxx |    - 현재 분기 1511|
|5.00.8355.xxxx    |- 현재 분기 1602|
|5.00.8412.1307    |- 현재 분기 1606 </br> - 현재 분기 1606 및 1606 핫픽스 롤업(KB3186654)</br>- 버전 1606 기준 미디어의 확장된 상호 운용성 클라이언트|  

클라이언트에 있는 Configuration Manager 제어판 애플릿의 **일반** 탭에서 클라이언트 버전을 볼 수 있습니다.

애플릿의 **구성 요소** 탭에서 일부 구성 요소는 다른 값을 표시합니다. 예를 들어 클라이언트 버전 8412.1307의 경우 일부 구성 요소가 5.00.8412로.**1000** 또는 5.00.8412.**1006**으로 표시될 수도 있습니다.  일부 구성 요소에서 마지막 4자리가 다른 것은 정상적인 동작이며 구성 요소가 현재 클라이언트 버전으로 업데이트되지 않은 오류를 나타내는 것은 아닙니다.

