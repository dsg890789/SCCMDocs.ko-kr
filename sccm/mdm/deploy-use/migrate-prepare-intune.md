---
title: 사용자 마이그레이션을 위한 Intune 준비
titleSuffix: Configuration Manager
description: 하이브리드 MDM으로부터 사용자를 마이그레이션하기 위해 Azure에서 Intune을 준비하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 12/26/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: db97ae9e-34f4-4e10-a282-cd211f612bb4
ms.collection: M365-identity-device-management
ms.openlocfilehash: e217c7afc2910a23fe3f29fa215d58574f3d79d8
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56137816"
---
# <a name="prepare-intune-for-user-migration"></a>사용자 마이그레이션을 위한 Intune 준비 

*적용 대상: System Center Configuration Manager (현재 분기)*    
Intune 독립 실행형에서 하이브리드 MDM 사용자를 마이그레이션하기 전에 Intune을 준비 하는 단계를 수행 합니다. 이러한 단계를 통해 마이그레이션된 사용자와 장치를 관리할 수 계속 되도록 합니다. 다음이 단계를 완료 하 고 Intune로의 마이그레이션을 시작 하면 영향을 주지 않고 사용자가 있습니다.  

## <a name="fix-issues-found-during-data-collection-and-import"></a>데이터 수집 및 가져오기 중 발견된 문제 해결
Intune 데이터 가져오기 도구를 사용 하는 경우 [Microsoft Intune로 Configuration Manager 데이터를 가져오는](migrate-import-data.md), 해당 요약 개체를 가져올 수 없습니다. 몇 가지 일반적인 문제 및 Intune에서이 해결 하는 단계는 다음 표에 나열 됩니다. 

|문제  |수정  |
|---------|---------|
|컬렉션 또는 복합 직접 멤버 자격에 따라 자동으로 마이그레이션되지 않습니다.|컬렉션을 가져오지 않았습니다을 바꾸려면 Azure에서 Azure Active Directory (Azure AD) 그룹을 만듭니다. 그런 다음 그룹에 개체를 할당 합니다.|
|정책을은 가져올 수 없습니다. |Intune에서 정책을 다시 만듭니다.|
|개체에 대한 배포를 가져오지 않습니다.|그룹에 개체를 할당 합니다. 그룹 배포에 대 한 컬렉션에서 동일한 사용자를 포함 해야 합니다.|

## <a name="create-intune-objects"></a>Intune 개체 만들기 
경우 있습니다 [Microsoft Intune로 Configuration Manager 데이터를 가져올](migrate-import-data.md) 가져온된 개체가 올바르게 구성 확인 프로세스 중 문제를 해결 합니다. 조직에서 해야 하는 Intune에서 모든 추가 개체 (정책, 프로필 및 앱)를 만들 수도 있습니다. 

## <a name="assign-intune-licenses-to-migrated-users"></a>마이그레이션된 사용자에게 Intune 라이선스 할당
Configuration Manager에서 Intune 구독에 컬렉션을 추가 하 고 컬렉션의 멤버는 장치를 등록할 수 있습니다. Intune 라이선스를 등록 된 장치에 대 한 예약 되는 동안 이러한 라이선스는 사용자 또는 장치가 표시 되지 않습니다. 예를 들어 찾을 수 없습니다 Intune 라이선스를 Azure AD에 등록 된 장치가 있는 사용자입니다. 

Intune 독립 실행형에서는 각 사용자에 대 한 Intune 라이선스를 구성 합니다. 라이선스를 구성 *하기 전에* Intune 독립 실행형으로 사용자를 마이그레이션. 이렇게 하는 사용자 및 해당 장치가 Intune에서 관리 되 MDM 기관 변경 후 합니다. 자세한 내용은 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/licenses-assign)을 참조하세요. 

## <a name="verify-intune-user-groups"></a>Intune 사용자 그룹 확인
사용자 및 그룹 가능성이 이미 Azure AD에서에서 디렉터리 동기화를 구성 해야 하기 때문입니다. 사용자가 올바른 사용자 그룹의 멤버인지 확인하려면 Intune 사용자 그룹을 검토하는 것이 좋습니다. 정책, 프로필 및 이러한 그룹에 앱을 대상 있습니다. Intune 독립 실행형으로 마이그레이션한 사용자가 올바른 그룹의 멤버인지 확인합니다. 

## <a name="configure-role-based-administration-control-rbac"></a>RBAC(역할 기반 관리 제어) 구성
마이그레이션의 일부로 Intune에서 필요한 모든 RBAC 역할을 구성하고 해당 역할에 사용자를 할당합니다. 차이가 RBAC in Configuration Manager 및 Intune 같은 리소스의 범위를 지정 합니다. 자세한 내용은 [Intune 통한 역할 기반 관리 제어 (RBAC)](https://docs.microsoft.com/intune/role-based-access-control)합니다.

## <a name="assign-apps-and-policies-to-aad-groups"></a>AAD 그룹에 앱 및 정책 할당
경우 있습니다 [Microsoft Intune로 Configuration Manager 데이터를 가져올](migrate-import-data.md), Azure AD 그룹에 이미 할당 될 수 있습니다 대부분의 개체입니다. 올바른 (앱, 정책 및 프로필)의 개체를 모두 할당 되었는지 확인 Azure AD 그룹입니다. 개체를 올바르게 할당 하면 사용자가 마이그레이션된 후 마이그레이션에는 사용자에 게 영향을 주지 중요 없어야 합니다. 사용자의 장치가 자동으로 구성 됩니다. Azure AD 그룹에 개체를 할당 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 합니다. 
- [정책 할당](https://docs.microsoft.com/intune/get-started-policies)  
- [프로필 할당](https://docs.microsoft.com/intune/device-profile-assign)  
    > [!NOTE]  
    > 새 전자 메일 프로필을 배포 하는 Intune에서 사용자가 자신의 암호를 다시 입력 하 라는 메시지가 수신 합니다. 이 동작은 사용자의 장치에서 다시 다운로드할 되는 전자 메일에서 발생 합니다. 사용자가 완료 된 모든 사용자 지정 수정을 다시 수행 해야 합니다. 
- [앱 할당](https://docs.microsoft.com/intune/get-started-apps) 

## <a name="terms-and-conditions-policy"></a>사용 약관 정책
다른 테넌트 수준 정책과 마찬가지로, 테넌트에 대해 혼합 기관을 사용하도록 설정되면 사용 약관이 Intune으로 자동 마이그레이션됩니다.  그러나 조건에 할당 해야 하 고 조건이 포함 된 그룹에 마이그레이션된 정확 하 게 마이그레이션된 사용자에 대 한 승인을 보고 되는지 확인 하는 조건에는 대상으로 올바르게 지정 향후의 사용 약관 및 조건 업데이트 또는 장치에 대 한 사용자 등록 합니다. 사용자는 Configuration Manager 콘솔에서 정책을 변경 하지 않는 한 사용 약관을 다시 수락 하지 않아도 됩니다. 자세한 내용은 [사용 약관 할당](https://docs.microsoft.com/intune/terms-and-conditions-create#assign-terms-and-conditions)합니다.

## <a name="configure-the-exchange-connector"></a>Exchange Connector 구성
Exchange를 사용하고 Configuration Manager에 온-프레미스 Exchange Connector가 있는 경우 [Intune에서 온-프레미스 Exchange Connector를 구성](https://docs.microsoft.com/intune/exchange-connector-install)해야 합니다. 또한 Intune Exchange Connector로 마이그레이션할 수 있도록 및 조건부 액세스 마이그레이션 후 제대로 작동 하는지 확인 하려면 다음 섹션의 정보를 고려 합니다.

### <a name="powershell-scripts-to-help-you-migrate-to-the-intune-exchange-connector"></a>Intune Exchange Connector로 마이그레이션하는 데 도움이 되는 PowerShell 스크립트 
Exchange 디바이스를 사용하면 Configuration Manager Exchange Connector에서 Intune Exchange Connector로 전환할 준비를 하는 데 유용한 PowerShell 스크립트를 사용할 수 있습니다. 이러한 스크립트 실행은 선택 사항이지만 Intune에서 불필요한 디바이스를 검색하지 않도록 이 스크립트를 실행하여 Exchange에서 비활성 디바이스를 제거하는 것이 좋습니다. 스크립트를 실행하면 Exchange를 통해 검색된 디바이스가 Intune에 등록된 디바이스와 최대한 원활하게 병합될 수 있습니다. Intune Exchange Connector를 설정하기 전에 이러한 스크립트를 실행하세요. PowerShell 스크립트는 다음 문서에서 [Microsoft Intune으로 Configuration Manager 데이터를 가져오는](migrate-import-data.md) 데 사용하는 Intune 데이터 가져오기 도구 설치의 일부입니다. 자세한 내용과 스크립트 다운로드 방법은 [Microsoft Intune Data Importer](https://github.com/ConfigMgrTools/Intune-Data-Importer)(Microsoft Intune 데이터 가져오기 도구) GitHub 페이지를 참조하세요.

### <a name="steps-to-make-sure-conditional-access-works-properly-after-user-migration"></a>사용자 마이그레이션 후 제대로 작동 되었는지 조건부 액세스를 확인 하는 단계
조건부 액세스 사용자를 마이그레이션한 후 올바르게 작동 하 고 사용자가 자신의 전자 메일 서버에 액세스할 수 있도록 계속 되도록 작성에 대 한 다음과 같은 구성이 설정 되어 있는지 확인 합니다.
- Exchange ActiveSync 기본 액세스 수준 설정(DefaultAccessLevel)이 차단 또는 격리로 설정된 경우 디바이스에서 전자 메일에 대한 액세스를 손실할 수 있습니다. 
- Exchange Connector가 Configuration Manager에서 설치 된 경우 및 **모바일 장치 규칙에 의해 관리 되지 않는 경우의 액세스 수준** 설정의 값이 **대 한 액세스 허용**를 설치 합니다 [ 온-프레미스 Exchange connector](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access) 사용자를 마이그레이션하기 전에 Intune에서 합니다. Intune에서 기본 액세스 수준 설정을 구성 합니다 **Exchange 온-프레미스** 페이지에서 **고급 Exchange ActiveSync 액세스 설정**합니다. 자세한 내용은 [구성 Exchange 온-프레미스 액세스](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access)합니다.
- 두 커넥터 모두에 대해 동일한 구성을 사용합니다. 마지막으로 구성한 커넥터는 이전에 다른 커넥터에서 쓴 ActiveSync 조직 설정을 덮어씁니다. 커넥터를 다르게 구성하면 조건부 액세스가 예기치 않게 변경될 수 있습니다.
- 사용자가 Intune 독립 실행형으로 마이그레이션되었으면 Configuration Manager의 조건부 액세스 대상에서 사용자를 제거합니다.

## <a name="configure-the-microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connector 구성
NDES를 사용하여 SCEP를 사용하는 인증서를 발급하는 경우 Microsoft Intune Certificate Connector를 구성해야 합니다. Intune에서 NDES 커넥터를 호스트 하는 컴퓨터에 Configuration Manager에서 NDES 커넥터를 호스팅하는 동일한 컴퓨터 일 수 없습니다. 자세한 내용은 [구성 및 Intune 사용 하 여 SCEP 인증서 관리](https://docs.microsoft.com/intune/certificates-scep-configure)합니다. 

> [!Important]    
> 커넥터를 구성한 후에 새 서버 URL을 참조 하도록 가져온된 SCEP 프로필을 수정 합니다.

## <a name="next-step"></a>다음 단계
마이그레이션에 대 한 Intune을 준비한 후 Intune 독립 실행형 테스트 사용자 집합을 마이그레이션할 준비가 되었습니다. 자세한 내용은 [특정 사용자 (혼합 기관)에 대 한 MDM 기관을 변경](migrate-mixed-authority.md)합니다.


