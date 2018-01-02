---
title: "하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션"
titleSuffix: Configuration Manager
description: "Azure에서 하이브리드 MDM 사용자와 장치를 Intune으로 마이그레이션하는 방법을 알아봅니다."
keywords: 
author: dougeby
manager: angrobe
ms.date: 09/12/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: 1dd696ce-3e46-4dfa-a76d-592fe0f0320e
ms.openlocfilehash: 30474f6dd0216078ab1ac1f4bd9f5044f1b174f0
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2017
---
# <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone"></a>하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션

*적용 대상: System Center Configuration Manager(현재 분기)*    

Azure에서 Intune을 사용하여 하이브리드 MDM(Configuration Manager와 통합된 Intune)에서 클라우드 전용 환경으로 마이그레이션할 준비가 되었다고 판단하면 이 문서가 도움이 될 것입니다. 아직도 확신할 수 없으면 [System Center Configuration Manager를 사용하여 Microsoft Intune 독립 실행형 및 하이브리드 장치 관리 중에서 선택](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)을 참조하세요. 

대부분의 사용자와 장치를 하이브리드 MDM을 통해 계속 관리하면서 사용자 및 장치의 작은 하위 집합을 테스트할 수 있는 단계별 접근 방식을 통해 Intune 독립 실행형으로 마이그레이션할 수 있습니다. 그런 다음 Intune 기능을 확인한 후에 더 많은 사용자를 Intune으로 마이그레이션할 수 있습니다.    

다음 항목에서는 단계별 접근 방식을 사용하여 사용자를 Intune 독립 실행형으로 마이그레이션하는 단계에 대해 설명합니다.    
  
1.  [Configuration Manager 데이터를 Microsoft Intune으로 가져오기](migrate-import-data.md)   
    Intune 데이터 가져오기 도구는 Configuration Manager 계층에서 선택한 개체에 대한 데이터를 수집하고, 가져오도록 선택할 수 있는 개체에 대한 정보와 일부 개체를 가져올 수 없는 이유에 대한 정보를 제공하며, 선택한 개체를 Microsoft Intune 테넌트로 가져올 수 있습니다. 이 단계는 선택 사항이지만 Configuration Manager에서 Intune으로 개체를 다시 만드는 프로세스를 자동화하여 많은 시간을 절약할 수 있습니다. 
2.  [사용자 마이그레이션을 위한 Intune 준비](migrate-prepare-intune.md)    
    Configuration Manager에서 가져온 개체의 유효성을 검사하고, 새 개체를 만들고, AAD 그룹을 만들고, 이러한 그룹에 개체를 할당하고, NDES 및 Exchange 커넥터를 설치합니다. 단계를 완료하고 Intune 독립 실행형으로의 마이그레이션을 시작하는 경우 이 작업은 사용자에게 투명해야 합니다.  
3.  [특정 사용자에 대한 MDM 기관 변경(혼합 MDM 기관)](migrate-mixed-authority.md)    
    Intune에서 관리할 일부 사용자를 선택하고 다른 모든 장치는 하이브리드 MDM(Configuration Manager와 통합된 Intune)으로 계속 관리하면서 혼합 MDM 기관을 동일한 테넌트에 구성합니다. 추가 사용자 마이그레이션을 시작하기 전에 사용자의 작은 하위 집합에 대한 장치에서 Intune 기능이 예상대로 작동하는지 테스트할 수 있습니다. 
4.  [MDM 기관을 Intune 독립 실행형으로 변경](change-mdm-authority.md)     
    테넌트 수준의 MDM 기관을 Configuration Manager에서 Intune으로 변경합니다. 나머지 모든 사용자와 장치는 Intune 독립 실행형으로 마이그레이션됩니다. 이전 단계에서 Intune 기능을 철저히 테스트하고 대부분 또는 모든 사용자를 이미 마이그레이션한 후에는 테넌트 수준의 MDM 기관을 변경합니다.