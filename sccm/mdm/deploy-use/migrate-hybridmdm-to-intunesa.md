---
title: 하이브리드 MDM 자원을 Intune 독립 실행형에 마이그레이션
titleSuffix: Configuration Manager
description: Azure에서 하이브리드 MDM 사용자와 장치를 Intune으로 마이그레이션하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 08/14/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: 1dd696ce-3e46-4dfa-a76d-592fe0f0320e
ms.openlocfilehash: 09ea3340d8474c69e6e346fc68120b8849159374
ms.sourcegitcommit: 316899b08f2ef372993909e08e069f7edfed1d33
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44111045"
---
# <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone"></a>하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션

*적용 대상: System Center Configuration Manager(현재 분기)*    

이 문서는 하이브리드 MDM에서 Azure의 Intune을 사용하는 클라우드 전용 환경으로 마이그레이션하는 방법을 다룹니다. 

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 장치 관리 [기능이 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  


단계적 접근 방식을 사용하여 Intune 독립 실행형으로의 마이그레이션을 시작하세요. 이 접근 방식을에서는 대부분의 사용자와 장치를 하이브리드 MDM을 통해 계속 관리하면서 작은 사용자 및 장치 하위 집합을 테스트합니다. Intune 기능을 확인한 후에 더 많은 리소스를 Intune으로 마이그레이션합니다.    

자세한 내용은 다음 아티클을 참조하세요.    
  
1.  [Configuration Manager 데이터를 Microsoft Intune로 가져오기](migrate-import-data.md)   

    Intune Data Importer 도구:  

    - Configuration Manager 계층 구조에서 선택한 개체에 대한 데이터를 수집합니다.  

    - 가져오도록 선택할 수 있는 개체에 대한 세부 정보를 제공합니다.   

    - 일부 개체를 가져올 수 없는 이유에 대한 정보를 제공합니다.  

    - 선택한 개체를 Microsoft Intune 테넌트로 가져올 수 있도록 합니다.  

    이 단계는 선택 항목입니다. 이 단계를 통해 Configuration Manager에서 Intune으로 개체를 다시 만드는 프로세스를 자동화하여 많은 시간을 절약할 수 있습니다.  

2.  [사용자 마이그레이션을 위한 Intune 준비](migrate-prepare-intune.md)    

    - Configuration Manager에서 가져온 개체의 유효성을 검사합니다.  

    - 새 개체를 만듭니다.  

    - Azure AD 그룹을 만들고 이 그룹에 개체를 할당합니다.  

    - NDES 및 Exchange 커넥터를 설치합니다.  

    단계를 완료하고 Intune 독립 실행형으로의 마이그레이션을 시작하는 경우 이 작업은 사용자에게 투명해야 합니다.   

3.  [특정 사용자에 대한 MDM 기관 변경(혼합 MDM 기관)](migrate-mixed-authority.md)    

    동일한 테넌트에서 혼합 MDM 기관을 구성하세요. 하이브리드 MDM을 사용하여 다른 모든 장치를 관리하면서 Intune에서 관리할 사용자를 선택합니다. 추가 사용자 마이그레이션을 시작하기 전에 작은 사용자 하위 집합에 대한 장치에서 Intune 기능이 작동하는지 테스트합니다.   

4.  [MDM 기관을 Intune 독립 실행형으로 변경](change-mdm-authority.md)     

    테넌트 수준의 MDM 기관을 Configuration Manager에서 Intune으로 변경합니다. 나머지 모든 사용자와 장치는 Intune 독립 실행형으로 마이그레이션됩니다. 이전 단계에서 Intune 기능을 철저히 테스트하고 대부분 또는 모든 사용자를 마이그레이션한 후에는 테넌트 수준의 MDM 기관을 변경합니다.



## <a name="request-assistance"></a>지원 요청
<!--Intune bug 2339232--> Microsoft FastTrack 프로그램의 지원을 요청하려면 [Microsoft 365용 FastTrack](https://fasttrack.microsoft.com/microsoft365/capabilities?view=security)으로 이동합니다.

1. “로그인”을 클릭하고 조직 ID를 입력합니다.  

2. 대시보드로 이동하고 지시에 따라 **지원 요청** 양식에 액세스합니다.    

3. Microsoft에서 요청을 검토하고 특정 요구 사항 및 자격을 해결할 적절한 팀에 라우팅합니다.  

이 대시보드에서 FastTrack 전문가로부터 모범 사례, 도구 및 리소스를 찾아 Microsoft 클라우드 사용 환경을 좋은 환경을 만들 수 있습니다.

