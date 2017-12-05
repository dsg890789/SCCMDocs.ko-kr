---
title: "특정 사용자에 대한 MDM 기관 변경(혼합 MDM 기관)"
titleSuffix: Configuration Manager
description: "일부 사용자에 대해 MDM 기관을 하이브리드 MDM에서 Intune 독립 실행형으로 변경하는 방법을 알아봅니다."
keywords: 
author: dougeby
manager: dougeby
ms.date: 09/14/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: 6f0201d7-5714-4ba0-b2bf-d1acd0203e9a
ms.openlocfilehash: 31d1d84c225d041f644669f0d3279e6bcd3f75ba
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="change-the-mdm-authority-for-specific-users-mixed-mdm-authority"></a>특정 사용자에 대한 MDM 기관 변경(혼합 MDM 기관) 

*적용 대상: System Center Configuration Manager(현재 분기)*    

Intune에서 관리할 일부 사용자와 하이브리드 MDM(Configuration Manager와 통합된 Intune)으로 관리할 다른 사용자를 선택하여 동일한 테넌트에 혼합 MDM 기관을 구성할 수 있습니다. 이 항목에서는 Intune을 독립 실행형으로 이동하는 방법에 대한 정보를 제공하고 다음 단계를 완료했다고 가정합니다.
- 데이터 가져오기 도구를 사용하여 [Configuration Manager 개체를 Intun으로 가져왔습니다](migrate-import-data.md)(선택 사항).
- [Intune에서 사용자 마이그레이션을 준비](migrate-prepare-intune.md)하여 사용자와 장치가 마이그레이션된 이후에도 계속 관리되도록 했습니다.

> [!Note]    
> 모든 정책, 앱 및 장치 등록을 제거하는 테넌트를 완전히 다시 설정하려면 지원 서비스에 문의하여 지원을 요청하세요.

마이그레이션된 사용자와 해당 장치는 Intune에서 관리되며, 다른 장치는 Configuration Manager에서 계속 관리됩니다. 작은 테스트 사용자 그룹으로 시작하여 모든 항목이 예상대로 작동하는지 확인합니다. 그런 다음 테넌트 수준 MDM 기관을 Configuration Manager에서 Intune 독립 실행형으로 전환할 준비가 될 때까지 점진적으로 사용자 그룹을 추가하면서 마이그레이션합니다. 

## <a name="things-to-know-before-you-migrate-users"></a>사용자를 마이그레이션하기 전에 알아야 할 사항
- 단계별 마이그레이션 중에 Configuration Manager의 기존 MDM 정책이나 앱은 모두 하이브리드 MDM 장치에 계속 적용됩니다.
- 사용자는 마이그레이션 그룹으로 지정한 AAD 그룹에 추가됩니다. 마이그레이션 그룹의 사용자와 연결된 모든 장치는 Intune에서 관리됩니다.
- AAD 그룹에 추가된 장치가 연결된 사용자가 없는 장치이면 무시됩니다.
- 마이그레이션 대상으로 표시된 AAD 그룹에 없는 사용자는 자동으로 테넌트 수준 MDM 기관(Configuration Manager)을 상속합니다.
- 사용자를 Intune으로 마이그레이션하면 사용자 및 장치가 약 15분 후에 Azure Portal의 Inture에 표시됩니다.  
- 사용자를 Intune 독립 실행형으로 마이그레이션하는 경우 Intune 독립 실행형과 하이브리드 MDM 장치 모두에 대해 Configuration Manager에서 다음 설정을 계속 관리합니다.
    - [APN(Apple Push Notification) 서비스 인증서](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)
    - [장치 등록 프로그램](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)
    - 등록 프로필
    - [VPP(Volume Purchase Program) 라이선스](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)
    - 회사 식별자 
    - [코드 서명 인증서](/sccm/mdm/deploy-use/enroll-hybrid-windows)
    - [장치 범주](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections)
    - [등록 관리자](/sccm/mdm/plan-design/device-enrollment-methods)
    - Terms and conditions
    - Windows SLK
    - 회사 포털 브랜딩    
      
> [!Important]    
  > 테넌트 수준 정책은 onfiguration Manager 콘솔을 사용하여 계속 편집됩니다. [테넌트 수준 MDM 기관을 Intune으로 변경](change-mdm-authority.md)하면 Azune의 Intune에서 이러한 정책을 관리하게 됩니다. 
- Configuration Manager에서 장치 등록 관리자로 추가된 사용자 계정은 마이그레이션하지 않는 것이 좋습니다. 나중에 테넌트 수준 MDM 기관을 Intune으로 변경하면 이러한 사용자 계정이 올바르게 마이그레이션됩니다. 테넌트 수준 MDM 기관이 변경되기 전에 장치 등록 관리자 사용자 계정을 마이그레이션하는 경우 Azure의 Intune에서 사용자를 장치 등록 관리자로 수동으로 추가해야 합니다. 그러나 장치 등록 관리자를 사용하여 등록한 장치는 성공적으로 마이그레이션되지 않습니다. 이러한 장치를 마이그레이션하려면 지원을 요청해야 합니다. 자세한 내용은 [장치 등록 관리자 추가](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll#add-a-device-enrollment-manager)를 참조하세요.
- 장치 등록 관리자를 사용하여 등록한 장치와 관련 사용자가 없는 장치는 새로운 MDM 기관으로 마이그레이션되지 않습니다. 이러한 장치의 경우 지원 서비스에 문의하여 개별 장치에 대한 지원을 요청해야 합니다. MDM 기관 다시 설정을 실행하지 않거나 Intune에서 데이터를 초기화합니다. Configuration Manager 콘솔에서 [MDM 기관을 변경](migrate-change-mdm-authority.md)해야 합니다.

## <a name="migrate-users-to-intune"></a>Intune으로 사용자 마이그레이션
Intune 구성이 예상대로 작동하는지 테스트하려면 먼저 작은 사용자 집합과 해당 장치를 마이그레이션합니다. 그런 다음 작업이 예상대로 작동하는지 확인한 후에 더 많은 사용자와 해당 장치가 있는 AAD 그룹을 더 많이 마이그레이션할 수 있습니다.

## <a name="migrate-a-test-group-of-users-to-intune-standalone"></a>Intune 독립 실행형으로 테스트 사용자 그룹 마이그레이션
Intune 구독과 연결된 컬렉션의 사용자에 대한 장치는 하이브리드 MDM에 등록할 수 있습니다. 컬렉션에서 사용자를 제거하면 사용자에게 할당된 Intune 라이선스가 있는 경우 등록된 장치가 Intune 독립 실행형으로 마이그레이션됩니다. 마이그레이션하려는 사용자에게 라이선스를 아직 할당하지 않은 경우 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/licenses-assign)을 참조하세요. Intune 구독에 대한 컬렉션에서 기본 컬렉션의 사용자 컬렉션을 제외하여 제외된 컬렉션의 사용자를 마이그레이션할 수 있습니다. 

다음 예제에서는 [모든 사용자] 컬렉션의 모든 멤버가 하이브리드 사용자 컬렉션에 포함되어 있습니다. 이를 통해 모든 사용자가 하이브리드 MDM에 장치를 등록할 수 있습니다. 사용자를 Intune 독립형으로 마이그레이션하려면 [컬렉션 제외]를 선택하고 마이그레이션할 사용자가 있는 컬렉션을 추가합니다. 더 많은 사용자를 마이그레이션할 준비가 되면 해당 사용자가 있는 제외된 컬렉션을 추가할 수 있습니다. 

![컬렉션 제외](../media/migrate-excludecollections.png)

> [!Note] 
> Intune 구독에 대해 **모든 사용자** 그룹을 선택하면 컬렉션을 제외하는 규칙을 추가할 수 없습니다. **모든 사용자** 컬렉션을 기반으로 하여 새 컬렉션을 만들고, 예상되는 사용자가 컬렉션에 포함되어 있는지 확인한 다음, Intune 구독을 편집하여 새 컬렉션을 사용합니다. 새 컬렉션에서 사용자 컬렉션을 제외하여 사용자를 마이그레이션할 수 있습니다. 

테스트 사용자 그룹을 Intune으로 마이그레이션하려면, 마이그레이션할 사용자가 포함된 사용자 컬렉션을 만든 다음 Intune 구독에 사용된 컬렉션에서 사용자 컬렉션을 제외합니다.   

다음 다이어그램에서는 사용자 마이그레이션의 작동 방식에 대한 개요를 보여 줍니다.

 ![혼합 기관 개요](../media/migrate-mixedauthority.svg)

1. 사용자에게 Intune/EMS 라이선스가 있는지 확인합니다. 
2. Intune 구독에 대한 컬렉션에서 제외할 컬렉션을 만듭니다. 이 예제에서는 **마이그레이션 파일럿** 컬렉션에서 사용자를 제외하는 규칙이 **모든 하이브리드 사용자** 컬렉션에 포함되어 있습니다. **User1**은 **마이그레이션 파일럿** 컬렉션의 멤버이며, **모든 하이브리드 사용자** 컬렉션에서 제외됩니다. 
3. **User1**의 장치가 이제 Azure Portal의 Intune에서 관리됩니다. 
4. 다른 모든 장치는 Configuration Manager 콘솔에서 계속 관리됩니다. 

## <a name="verify-intune-standalone-functionality"></a>Intune 독립 실행형 기능 확인
작은 사용자 집합을 마이그레이션한 후에는 사용자의 장치가 Intune에서 나열되는지 확인합니다. **장치** 블레이드로 이동하여 **모든 장치**를 선택합니다. 

그런 다음 정책, 프로필, 앱 등이 사용자 장치에서 예상대로 작동하는지 확인합니다.

## <a name="migrate-additional-users"></a>추가 사용자 마이그레이션
Intune 독립 실행형 장치가 예상대로 작동하는지 확인한 후에 추가 사용자 마이그레이션을 시작할 수 있습니다. 테스트 사용자 집합이 있는 컬렉션을 만든 것처럼 Intune 구독과 연결된 컬렉션에서 해당 컬렉션을 마이그레이션하고 제외할 사용자가 포함된 컬렉션을 만듭니다. 자세한 내용은 [Intune 구독과 연결된 컬렉션](#collection-associated-with-your-intune-subscription)을 참조하세요.

## <a name="next-steps"></a>다음 단계
사용자를 마이그레이션하고 Intune 기능을 테스트한 후에는 Intune 테넌트의 [MDM 기관을 Configuration Manager에서 Intune으로 변경](migrate-change-mdm-authority.md)할 준비가 되었는지 확인하는 것이 좋습니다. 