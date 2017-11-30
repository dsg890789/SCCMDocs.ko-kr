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
ms.openlocfilehash: a6e430248fdeedd310087c9a32c6d69ca1864a09
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
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

<!--
The following provides a typical workflow for migrating users from hybrid MDM to Intune standalone:
1.  Admin runs the Microsoft Intune Data Importer Tool, selecting which objects and assignments to import. Selected objects are imported into Intune standalone.
    1. Some objects cannot be imported because they contain settings the tool does not understand or setting that are not available in Intune standalone.
    2. Assignments are migrated. However, only if the collection an object was targeted to is based on a single Active Directory (AD) security group and the same group exists in Azure Active Directory (AAD).
    > [!Note]    
    > If you want, you can skip this step and create the objects that you want directly in Intune in the Azure portal without running the Intune Data Importer Tool. 
2.  Admin logs into the Intune on Azure portal
    1. Creates any additional objects required for their organization that were not imported by the Microsoft Intune Data Importer tool.
    2. Creates any required AAD groups and makes any additional assignments for each object to AAD groups.
    3. Installs the NDES connector on an on-premises server if using SCEP or PFX certificate deployment.
    4. Installs the Exchange connector on an on-premises server if using conditional access. 
3.  Admin ensures that all existing Intune users in their organization have an Intune license assigned to them using AAD or the Office administrator portal.
4.  Admin selects some test users to migrate to Intune standalone and removes them from the collection associated with the Intune subscription in Configuration Manager.
5.  Once removed from the collection, the user and all devices are managed by Intune in the Azure portal. Remaining users and devices continue to be managed by hybrid mobile device management in Configuration Manager. 
6.  Admin validates that things are working as expected on the device and moves more users to Intune standalone by removing them from the collection associated with the Intune subscription in Configuration Manager.
7.  Once the admin is comfortable with the functionality in Intune standalone, they can move the rest of their users and devices by switching their MDM authority to Intune standalone. This can be done by removing the Intune subscription from SCCM and choosing to change the MDM authority. Tenant level policies will be automatically migrated to Intune standalone, all objects and assignments in Intune standalone will remain, and devices will not be required to re-enroll.
-->