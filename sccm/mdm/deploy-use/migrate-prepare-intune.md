---
title: 사용자 마이그레이션을 위한 Intune 준비
titleSuffix: Configuration Manager
description: 하이브리드 MDM으로부터 사용자를 마이그레이션하기 위해 Azure에서 Intune을 준비하는 방법을 알아봅니다.
author: aczechowski
manager: dougeby
ms.date: 12/05/2017
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: db97ae9e-34f4-4e10-a282-cd211f612bb4
ms.openlocfilehash: 0d71abbe33def6e12e75c2042e48f3d7ddcfe5c6
ms.sourcegitcommit: 06d490d526070e17d77e86bc6c200899ded911cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38967150"
---
# <a name="prepare-intune-for-user-migration"></a>사용자 마이그레이션을 위한 Intune 준비 

*적용 대상: System Center Configuration Manager(현재 분기)*    

사용자를 하이브리드 MDM(Configuration Manager와 통합된 Intune)에서 Intune 독립 실행형으로 마이그레이션하기 전에 Intune을 준비하는 단계를 수행해야 합니다. 이러한 단계를 수행하면 마이그레이션된 사용자와 해당 장치를 계속 관리할 수 있게 합니다. 이러한 단계를 완료하고 Intune으로의 마이그레이션을 시작하는 경우 이 작업은 사용자에게 투명해야 합니다.  

## <a name="fix-issues-found-during-data-collection-and-import"></a>데이터 수집 및 가져오기 중 발견된 문제 해결
[Configuration Manager 데이터를 Microsoft Intune으로 가져오는 프로세스](migrate-import-data.md)를 수행한 경우, Intune 데이터 가져오기 도구에서 가져올 수 없는 모든 개체에 대한 요약을 제공했습니다. 다음 표에는 Intune에서 문제를 해결하는 데 수행할 수 있는 단계와 실행할 때 발생할 수도 있는 일반적인 문제 중 일부가 나와 있습니다. 

|문제  |픽스  |
|---------|---------|
|직접 멤버 관리 또는 복잡한 컬렉션 기반의 컬렉션은 자동으로 마이그레이션되지 않습니다.|가져오지 않은 컬렉션을 바꾸려면 Azure에서 AAD(Azure Active Directory) 그룹을 만들어야 합니다. 그런 다음 개체를 그룹에 할당해야 합니다.|
|정책을 가져올 수 없습니다. |Intune에서 정책을 다시 만들어야 합니다.|
|개체에 대한 배포를 가져오지 않습니다.|개체를 그룹에 할당해야 합니다. 그룹에는 배포에 대한 컬렉션과 동일한 사용자가 있어야 합니다.|

## <a name="create-intune-objects"></a>Intune 개체 만들기 
[Configuration Manager 데이터를 Microsoft Intune으로 가져오는 프로세스](migrate-import-data.md)를 수행하고 가져오기 프로세스 중에 발생한 문제를 해결한 경우, 가져온 개체가 올바르게 구성되었는지 확인해야 합니다. 또한 Intune에서 조직에 필요한 추가 개체(정책, 프로필, 앱 등)를 만듭니다. 

## <a name="assign-intune-licenses-to-migrated-users"></a>마이그레이션된 사용자에게 Intune 라이선스 할당
Configuration Manager에서 컬렉션을 Intune 구독에 추가하면 컬렉션의 멤버가 자신의 장치를 등록할 수 있습니다. Intune 라이선스는 등록된 장치에 대해 예약되지만, 이러한 라이선스가 사용자 또는 장치와 특별히 연결되지는 않습니다. 예를 들어 AAD에서 등록된 장치가 있는 사용자에 대한 Intune 라이선스를 찾을 수 없습니다. 그러나 Intune 독립 실행형에서는 각 사용자에 대해 Intune 라이선스를 구성해야 합니다. MDM 기관을 변경한 후에 Intune에서 사용자와 해당 장치를 관리하도록 하려면 사용자를 Intune 독립 실행형으로 마이그레이션하기 전에 이 작업을 수행해야 합니다. 자세한 내용은 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/licenses-assign)을 참조하세요. 

## <a name="verify-intune-user-groups"></a>Intune 사용자 그룹 확인
디렉터리 동기화가 구성되어 있으므로 사용자와 그룹이 이미 AAD에 있을 가능성이 높습니다. 사용자가 올바른 사용자 그룹의 멤버인지 확인하려면 Intune 사용자 그룹을 검토하는 것이 좋습니다. 이러한 그룹에 정책, 프로필, 앱 등을 대상으로 지정합니다. Intune 독립 실행형으로 마이그레이션한 사용자가 올바른 그룹의 멤버인지 확인합니다. 

## <a name="configure-role-based-administration-control-rbac"></a>RBAC(역할 기반 관리 제어) 구성
마이그레이션의 일부로 Intune에서 필요한 모든 RBAC 역할을 구성하고 해당 역할에 사용자를 할당합니다. 리소스 범위 지정과 같이 Configuration Manager와 Intune의 RBAC 간에는 차이점이 있습니다. 자세한 내용은 [Intune을 통한 RBAC(역할 기반 관리 제어)](https://docs.microsoft.com/intune/role-based-access-control)를 참조하세요.

## <a name="assign-apps-and-policies-to-aad-groups"></a>AAD 그룹에 앱 및 정책 할당
다른 Configuration Manager 개체를 Intune으로 마이그레이션하는 마이그레이션 프로세스에 대해 [Configuration Manager 데이터를 Microsoft Intune으로 가져오는 단계](migrate-import-data.md)를 수행한 경우, 많은 개체가 이미 AAD 그룹에 할당되었을 수 있습니다. 그러나 모든 개체(앱, 정책, 프로필 등)가 올바른 AAD 그룹에 할당되어 있는지 확인해야 합니다. 개체를 올바르게 할당하면 사용자가 마이그레이션된 후 해당 사용자의 장치가 자동으로 구성되며 마이그레이션은 사용자에게 투명해야 합니다. AAD 그룹에 개체를 할당하는 방법에 대한 자세한 내용은 다음을 참조하세요. 
- [정책 할당](https://docs.microsoft.com/intune/get-started-policies) 
- [프로필 할당](https://docs.microsoft.com/intune/device-profile-assign) 
- [앱 할당](https://docs.microsoft.com/intune/get-started-apps) 

## <a name="terms-and-conditions-policy"></a>사용 약관 정책
다른 테넌트 수준 정책과 마찬가지로, 테넌트에 대해 혼합 기관을 사용하도록 설정되면 사용 약관이 Intune으로 자동 마이그레이션됩니다.  그러나 마이그레이션된 사용자에 대한 승인을 정확하게 보고하기 위해 해당 사용자가 포함된 그룹에 사용 약관을 할당하고, 향후의 사용 약관 업데이트 또는 장치 등록을 위한 대상으로 올바르게 지정되었는지 확인해야 합니다. Configuration Manager 콘솔에서 정책을 변경하지 않는 한 사용자는 사용 약관에 다시 동의하지 않아도 됩니다. 자세한 내용은 [사용 약관 할당](https://docs.microsoft.com/intune/terms-and-conditions-create#assign-terms-and-conditions)을 참조하세요.

## <a name="configure-the-exchange-connector"></a>Exchange Connector 구성
Exchange를 사용하고 Configuration Manager에 온-프레미스 Exchange Connector가 있는 경우 [Intune에서 온-프레미스 Exchange Connector를 구성](https://docs.microsoft.com/intune/exchange-connector-install)해야 합니다. 또한 다음 섹션의 정보를 고려하여 Intune Exchange Connector로 마이그레이션하고 마이그레이션 후 조건부 액세스가 제대로 작동하는지 확인할 수 있습니다.

### <a name="powershell-scripts-to-help-you-migrate-to-the-intune-exchange-connector"></a>Intune Exchange Connector로 마이그레이션하는 데 도움이 되는 PowerShell 스크립트 
Exchange 장치를 사용하면 Configuration Manager Exchange Connector에서 Intune Exchange Connector로 전환할 준비를 하는 데 유용한 PowerShell 스크립트를 사용할 수 있습니다. 이러한 스크립트 실행은 선택 사항이지만 Intune에서 불필요한 장치를 검색하지 않도록 이 스크립트를 실행하여 Exchange에서 비활성 장치를 제거하는 것이 좋습니다. 스크립트를 실행하면 Exchange를 통해 검색된 장치가 Intune에 등록된 장치와 최대한 원활하게 병합될 수 있습니다. Intune Exchange Connector를 설정하기 전에 이러한 스크립트를 실행하세요. PowerShell 스크립트는 다음 문서에서 [Microsoft Intune으로 Configuration Manager 데이터를 가져오는](migrate-import-data.md) 데 사용하는 Intune 데이터 가져오기 도구 설치의 일부입니다. 자세한 내용과 스크립트 다운로드 방법은 [Microsoft Intune Data Importer](https://github.com/ConfigMgrTools/Intune-Data-Importer)(Microsoft Intune 데이터 가져오기 도구) GitHub 페이지를 참조하세요.

### <a name="steps-to-ensure-conditional-access-works-properly-after-user-migration"></a>사용자 마이그레이션 후 조건부 액세스가 제대로 작동하는지 확인하는 단계
사용자를 마이그레이션한 후에 조건부 액세스가 제대로 작동하고 사용자가 자신의 전자 메일 서버에 계속 액세스할 수 있게 하려면 다음 사항이 사실인지 확인하세요.
- Exchange ActiveSync 기본 액세스 수준 설정(DefaultAccessLevel)이 차단 또는 격리로 설정된 경우 장치에서 전자 메일에 대한 액세스를 손실할 수 있습니다. 
- Exchange Connector가 Configuration Manager에 설치되어 있고 **모바일 장치가 규칙으로 관리되지 않는 경우의 액세스 수준** 설정에 **액세스 허용** 값이 있는 경우 사용자를 마이그레이션하기 전에 Intune에 [온-프레미스 Exchange Connector](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access)를 설치해야 합니다. **고급 Exchange ActiveSync 액세스 설정**의 **Exchange 온-프레미스** 블레이드에서 Intune의 기본 액세스 수준 설정을 구성합니다. 자세한 내용은 [Exchange 온-프레미스 액세스 구성](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access)을 참조하세요.
- 두 커넥터 모두에 대해 동일한 구성을 사용합니다. 마지막으로 구성한 커넥터는 이전에 다른 커넥터에서 쓴 ActiveSync 조직 설정을 덮어씁니다. 커넥터를 다르게 구성하면 조건부 액세스가 예기치 않게 변경될 수 있습니다.
- 사용자가 Intune 독립 실행형으로 마이그레이션되었으면 Configuration Manager의 조건부 액세스 대상에서 사용자를 제거합니다.

## <a name="configure-the-microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connector 구성
NDES를 사용하여 SCEP를 사용하는 인증서를 발급하는 경우 Microsoft Intune Certificate Connector를 구성해야 합니다. Intune에서 NDES 커넥터를 호스팅하는 컴퓨터는 Configuration Manager에서 NDES 커넥터를 호스팅하는 컴퓨터와 같을 수 없습니다. 자세한 내용은 [Intune을 사용하여 SCEP 인증서 구성 및 관리](https://docs.microsoft.com/intune/certificates-scep-configure)를 참조하세요. 

> [!Important]    
> 커넥터를 구성한 후에 새 서버 URL을 참조하도록 가져온 SCEP 프로필을 수정해야 합니다.

## <a name="next-step"></a>다음 단계
마이그레이션을 위해 Intune이 준비되면 테스트 사용자 집합을 Intune 독립 실행형으로 마이그레이션할 준비가 되었습니다. 자세한 내용은 [특정 사용자에 대한 MDM 기관 변경(혼합 기관)](migrate-mixed-authority.md)을 참조하세요.


