---
title: 진단 데이터 사용
titleSuffix: Configuration Manager
description: Microsoft가 System Center Configuration Manager에서 수집하는 진단 및 사용 현황 데이터를 사용하는 방식을 알아봅니다.
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 404c68f954828dffe2bb9aed9dc59800aff83110
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56120779"
---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>System Center Configuration Manager의 진단 및 사용 현황 데이터 사용 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager가 수집한 진단 및 사용 현황 데이터는 제품이 작동되는 방식에 대한 피드백을 Microsoft에 거의 즉시 제공하므로 이를 사용하여 향후 업데이트가 조정됩니다. 또한 프로덕션에 있는 구성을 엔지니어링하고 테스트하는 데 도움이 되는 구성 데이터를 볼 수 있습니다. 예:  

-   사이트 서버에서 사용되는 Windows Server 버전  

-   설치된 언어 팩  

-   제품 기본값에 대한 SQL 스키마의 델타  

이 데이터는 엔지니어링 팀이 가장 일반적인 구성에 대해 최상의 환경을 보장할 수 있도록 향후 테스트를 계획하는 데 사용됩니다. Windows 10, Microsoft Intune 등 빠르게 변화하는 기술을 더욱 효과적으로 지원할 수 있도록 Configuration Manager 업데이트가 더 빠른 주기로 릴리스되고 있으므로 그에 맞추어 이 데이터를 신속하게 조정하고 적용하는 것이 중요합니다.  

진단 및 사용 현황 데이터가 사용되지 않는 방식도 동일하게 중요합니다. Microsoft는 이 데이터를 다음과 같은 목적으로 사용하지 않습니다.  

-   고객의 사용 방식을 사용권 계약과 비교하는 등 라이선스 감사  

-   지원되지 않는 제품 감사  

-   기능 사용 또는 지리적 위치(표준 시간대)와 같은 사용 가능한 데이터를 기반으로 하는 광고  

##  <a name="bkmk_improve"></a> 진단 및 사용 현황 데이터는 제품을 개선하는 방법의 예  
Microsoft에서는 사용 가능한 데이터를 사용하여 제품을 개선합니다. 다음은 몇 가지 예입니다.  

-   **이전 서버 운영 체제에 대한 수정된 지원:**  

     System Center Configuration Manager의 현재 분기에서 제공하는 초기 지원에서는 Windows Server 2008 R2의 지원 타임라인을 제한했습니다. Configuration Manager 현재 분기로 업그레이드한 고객의 사용 현황 데이터를 검사한 후 여전히 이 서버 운영 체제를 사용하여 사이트 서버 및 사이트 시스템 역할을 호스트하는 고객을 지원하기 위해 이 타임라인을 수정하고 개정해야 할 필요성을 확인했습니다.  

-   **개선된 필수 구성 요소 확인:**  

     사용 현황 데이터에 따라 업데이트를 설치하여 기존 규칙을 제거하고, 추가 사례를 확인하고, 경우에 따라 몇 가지 문제를 자동 해결하기 위한 필수 조건 검사를 개선했습니다.  
