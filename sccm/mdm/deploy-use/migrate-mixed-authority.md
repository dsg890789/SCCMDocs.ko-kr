---
title: MDM 기관 변경
titleSuffix: Configuration Manager
description: 하이브리드 MDM에서에서 Intune 독립 실행형에 대 한 특정 사용자 (혼합된 MDM 기관)에 대 한 MDM 기관을 변경 하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: 6f0201d7-5714-4ba0-b2bf-d1acd0203e9a
ms.openlocfilehash: 79cf4c2ec217a245bb5c4abbad40aad7188e0ac0
ms.sourcegitcommit: 3772ece83823714b2aae46ec20523cc094701760
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51688472"
---
# <a name="change-the-mdm-authority-for-specific-users-mixed-mdm-authority"></a>특정 사용자에 대한 MDM 기관 변경(혼합 MDM 기관) 

*적용 대상: System Center Configuration Manager (현재 분기)*    

혼합된 MDM 기관을 동일한 테 넌 트에서 구성할 수 있습니다. 하이브리드 MDM 사용 하 여 Microsoft Intune 등의 몇 가지 사용자 관리 이 문서에서는 Intune 독립 실행형으로 이동 하는 방법에 대 한 정보를 제공 합니다. 다음 단계를 완료 가정 합니다.  

- 데이터 가져오기 도구를 사용하여 [Configuration Manager 개체를 Intun으로 가져왔습니다](migrate-import-data.md)(선택 사항).  

- [Intune에서 사용자 마이그레이션을 준비](migrate-prepare-intune.md)하여 사용자와 장치가 마이그레이션된 이후에도 계속 관리되도록 했습니다.  

> [!Note]    
> 모든 정책, 앱 및 장치 등록을 제거 하는 테 넌 트를 완전히 다시 설정 합니다. 이 프로세스를 수행 하려는 경우 도움이 필요 하면 지원을 호출 합니다.  

마이그레이션된 사용자와 Intune에서 장치를 관리 합니다. Configuration Manager에서 다른 장치 관리를 계속 합니다. 를 모두 예상 대로 작동 하는지 확인 하려면 사용자의 작은 테스트 그룹을 사용 하 여 시작 합니다. 그런 다음 사용자 그룹을 추가 점진적으로 마이그레이션하십시오. 준비 되 면, 테 넌 트 수준 MDM 기관을 Configuration Manager에서 Intune 독립 실행형으로 전환 합니다. 

> [!Important]  
> 2018년 8월 13일부터 하이브리드 모바일 디바이스 관리 [기능이 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  



## <a name="things-to-know-before-you-migrate-users"></a>사용자를 마이그레이션하기 전에 알아야 할 사항

- 단계별 마이그레이션 중에 Configuration Manager의 기존 MDM 정책이나 앱은 모두 하이브리드 MDM 디바이스에 계속 적용됩니다.  

- Intune 구독과 연결된 컬렉션의 사용자에 대한 디바이스는 하이브리드 MDM에 등록할 수 있습니다. 사용자와 연결되어 있지만 컬렉션에 없는 모든 디바이스는 사용자에게 Intune/EMS 라이선스가 있는 경우 Intune에서 관리됩니다.   

    > [!Note]  
    > 사용자는 Configuration Manager 콘솔을 통해 차단된 경우에도 Intune 독립 실행형에 등록할 수 있습니다. 사용자가 등록하는 것을 완전히 차단하려면 Intune에 원치 않는 사용자에게는 라이선스를 제공하지 마세요. 라이선스 없이는 등록할 수 없습니다.<!--SCCMDocs issue 738-->  

- 사용자를 Intune으로 마이그레이션하면 사용자와 디바이스가 Azure Portal의 Inture에 약 15분 후에 표시됩니다.   

- 사용자를 Intune 독립 실행형으로 마이그레이션하는 경우 Intune 독립 실행형과 하이브리드 MDM 디바이스 모두에 대해 Configuration Manager에서 다음 설정을 계속 관리합니다.  

    - [APN(Apple Push Notification) 서비스 인증서](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)  

    - [장치 등록 프로그램](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)  

        > [!Note]  
        > DEP 토큰을 다시 만들거나 Configuration Manager에서 제거할 필요가 없습니다. Intune 24 시간으로 변경 하면 테 넌 트의 MDM 기관을 Configuration Manager에서 Intune에 자동으로 마이그레이션합니다. 이 변경은 마이그레이션의 마지막 단계입니다. (DEP 토큰 하지 24 시간 이내를 마이그레이션할 경우 Microsoft 지원에 문의 합니다.)  

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
  > 테넌트 수준 정책은 onfiguration Manager 콘솔을 사용하여 계속 편집됩니다. 한 후 [테 넌 트 수준 MDM 기관을 변경](/sccm/mdm/deploy-use/change-mdm-authority) Intune로 Configuration Manager에서 자동으로 관리 된 테 넌 트 수준 정책을 Azure의 Intune로 마이그레이션. Apple Push Notification 서비스 (APNs) 인증서에 대 한 이러한 정책의 예가입니다.<!--SCCMDocs issue #971-->  

-   코드 서명 인증서를 사용하는 경우 사용자를 단계적으로 마이그레이션하는 것이 좋습니다. 모바일 디바이스를 마이그레이션한 후에 새 인증서에 대한 인증서 기관 요청을 수행합니다. 단계별적으로 사용자(및 디바이스)를 마이그레이션하여 동시 인증서 기관 요청 수를 제한합니다.  

- Configuration Manager에서 DEM(디바이스 등록 관리자)으로 추가된 사용자 계정은 마이그레이션하지 마세요. 나중에 테넌트 수준 MDM 기관을 Intune으로 변경하면 이러한 사용자 계정이 올바르게 마이그레이션됩니다. 테 넌 트 수준 MDM 기관 변경 전에 DEM 사용자 계정, 마이그레이션하는 경우 Azure에서 Intune의 DEM으로 사용자를 수동으로 추가 해야 있습니다. 그러나는 DEM을 사용 하 여 등록 된 장치는 성공적으로 마이그레이션되지 않습니다. 이러한 디바이스를 마이그레이션하려면 지원을 요청합니다. 자세한 내용은 [디바이스 등록 관리자 추가](https://docs.microsoft.com/intune/device-enrollment-manager-enroll#add-a-device-enrollment-manager)를 참조하세요.  

    > [!Note]  
    > 혼합된 기관 모드일 때에는 이러한 계정을 ConfigMgr 클라우드 컬렉션에서 제거하여 Intune으로 이동하지 마세요. 그럴 경우, 사용자가 표준 사용자 되어 15개 이상의 디바이스를 등록할 수 없습니다. 대신, 테넌트를 위한 MDM 기관이 완전히 전환되면 이러한 사용자 및 디바이스를 마이그레이션하세요.<!--Intune bug 2174210-->  

- DEM 및 없이 장치를 사용 하 여 장치 등록 [사용자 선호도](/sccm/mdm/deploy-use/user-affinity-for-hybrid-managed-devices) 새 MDM 기관으로 자동으로 마이그레이션되지 않습니다. 이러한 MDM 디바이스의 관리 기관을 전환하려면 [사용자 선호도가 없는 디바이스 마이그레이션](#migrate-devices-without-user-affinity)을 참조하세요.  



## <a name="migrate-users-to-intune"></a>Intune으로 사용자 마이그레이션

Intune 구성이 예상대로 작동하는지 테스트하려면 먼저 작은 사용자 집합과 해당 디바이스를 마이그레이션합니다. 그런 다음 작업이 예상대로 작동하는지 확인한 후에 더 많은 사용자와 해당 디바이스가 있는 AAD 그룹을 더 많이 마이그레이션할 수 있습니다.



## <a name="migrate-a-test-group-of-users-to-intune-standalone"></a>Intune 독립 실행형으로 테스트 사용자 그룹 마이그레이션

Intune 구독과 연결된 컬렉션의 사용자에 대한 디바이스는 하이브리드 MDM에 등록할 수 있습니다. 사용자에 게 Intune 라이선스를 할당 된 경우 컬렉션에서 사용자를 제거 하는 경우 등록 된 장치의 Intune 독립 실행형으로 마이그레이션됩니다. 계획 하지 않은 이미 할당 한 경우 라이선스가 사용자에 게는 마이그레이션을 참조 하십시오 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/licenses-assign)합니다. Intune 구독에 대한 컬렉션에서 기본 컬렉션의 사용자 컬렉션을 제외하여 제외된 컬렉션의 사용자를 마이그레이션할 수 있습니다. 

다음 예제에서는 [모든 사용자] 컬렉션의 모든 멤버가 하이브리드 사용자 컬렉션에 포함되어 있습니다. 이 구성을 통해 모든 사용자가 하이브리드 MDM에 디바이스를 등록할 수 있습니다. 사용자를 Intune 독립형으로 마이그레이션하려면 [컬렉션 제외]를 선택하고 마이그레이션할 사용자가 있는 컬렉션을 추가합니다. 더 많은 사용자를 마이그레이션할 준비가 되면 해당 사용자가 있는 제외된 컬렉션을 추가합니다. 

![컬렉션 제외](../media/migrate-excludecollections.png)

> [!Note]  
> 경우는 **모든 사용자** Intune 구독에 대 한 선택한 컬렉션 제외 컬렉션 규칙을 추가 하려면 허용 되지 않습니다. 기반으로 새 컬렉션을 만들 합니다 **모든 사용자에 게** 컬렉션입니다. 예상 되는 사용자 컬렉션에 포함 되어 있는지 확인 합니다. 그런 다음 새 컬렉션을 사용 하려면 Intune 구독을 편집 합니다. 새 컬렉션에서 사용자 컬렉션을 제외하여 사용자를 마이그레이션할 수 있습니다.  

테스트 사용자 그룹을 Intune로 마이그레이션하기 위해 마이그레이션할 사용자가 포함 된 사용자 컬렉션을 만듭니다. 다음 Intune 구독에 사용 되는 컬렉션에서 사용자 컬렉션을 제외 합니다.   

다음 다이어그램에서는 사용자 마이그레이션의 작동 방식에 대한 개요를 보여 줍니다.

 ![혼합 기관 개요](../media/migrate-mixedauthority.svg)

1. 사용자에게 Intune/EMS 라이선스가 있는지 확인합니다.   

2. Intune 구독에 대한 컬렉션에서 제외할 컬렉션을 만듭니다. 이 예제에서는 **마이그레이션 파일럿** 컬렉션에서 사용자를 제외하는 규칙이 **모든 하이브리드 사용자** 컬렉션에 포함되어 있습니다. **User1**은 **마이그레이션 파일럿** 컬렉션의 멤버이며, **모든 하이브리드 사용자** 컬렉션에서 제외됩니다.  

3. **User1**의 장치가 이제 Azure Portal의 Intune에서 관리됩니다.   

4. 다른 모든 디바이스는 Configuration Manager 콘솔에서 계속 관리됩니다.  



## <a name="verify-intune-standalone-functionality"></a>Intune 독립 실행형 기능 확인

작은 사용자 집합을 마이그레이션한 후에는 사용자의 디바이스가 Intune에서 나열되는지 확인합니다. **장치**로 이동하여 **모든 장치**를 선택합니다. 

그런 다음, 정책, 프로필, 앱이 사용자 디바이스에서 예상대로 작동하는지 확인합니다.



## <a name="migrate-additional-users"></a>추가 사용자 마이그레이션

Intune 독립 실행형 장치가 예상대로 작동하는지 확인한 후에는 추가 사용자 마이그레이션을 시작합니다. 테스트 사용자 집합이 포함 된 컬렉션을 만든 것 처럼 사용자가 마이그레이션할를 포함 하는 컬렉션을 만듭니다. Intune 구독과 연결 된 컬렉션에서 해당 컬렉션을 제외 합니다. 자세한 내용은 [Intune 구독과 연결된 컬렉션](#collection-associated-with-your-intune-subscription)을 참조하세요.



## <a name="migrate-devices-without-user-affinity"></a>사용자 선호도가 없는 디바이스 마이그레이션

디바이스 등록 관리자를 사용하여 등록한 디바이스와 [사용자 선호도](/sccm/mdm/deploy-use/user-affinity-for-hybrid-managed-devices)가 없는 디바이스는 새로운 MDM 기관으로 자동으로 마이그레이션되지 않습니다. 다음과 같은 시나리오에서 *Switch-MdmDeviceAuthority* PowerShell cmdlet을 사용하여 Intune과 Configuration Manager 관리 기간 간에 전환할 수 있습니다. 

-   시나리오 1: 사용 된 *Switch-mdmdeviceauthority* 선택한 장치를 마이그레이션하고 관리할 수 있습니다 Azure에서 Intune을 사용 하 여 유효성을 검사 하는 cmdlet입니다. 그런 다음, 준비가 되면 [테넌트에 대해 MDM 기관을 Intune으로 변경](migrate-change-mdm-authority.md)하여 디바이스의 마이그레이션을 완료합니다.  

-   시나리오 2: 테 넌 트에 대 한 MDM 기관을 Intune로 변경 하는 준비 된 경우에 사용자 선호도 없는 장치를 마이그레이션하려면 다음 작업을 수행 합니다.  

    - [테넌트에 대해 MDM 기관을 Intune으로 변경](migrate-change-mdm-authority.md)하기 전에 이 cmdlet을 사용하여 사용자 선호도가 없는 장치에 대한 MDM 기관을 변경합니다.     

    - 테넌트에 대해 MDM 기관을 Intune으로 변경한 후 사용자 선호도가 없는 디바이스는 전환하려면 지원 서비스에 문의하세요.  

이러한 MDM 디바이스에 대한 관리 기관을 전환하려면 *Switch-MdmDeviceAuthority* cmdlet을 사용하여 Intune과 Configuration Manager 관리 기관 사이를 전환할 수 있습니다. 

### <a name="cmdlet-switch-mdmdeviceauthority"></a>*Switch-MdmDeviceAuthority* cmdlet

#### <a name="synopsis"></a>개요
이 cmdlet은 사용자 선호도가 없는 MDM 디바이스(예: 대량 등록된 디바이스)의 관리 기관을 전환합니다. Cmdlet은 관리 기관을 Intune과 Configuration Manager 간의 전환합니다. Cmdlet을 실행 하는 경우 해당 관리 기관에 따라 지정된 된 장치에 대 한 전환 됩니다.

### <a name="syntax"></a>구문
`Switch-MdmDeviceAuthority -DeviceIds <Guid[]> [-Credential <PSCredential>] [-Force] [-LogFilePath <string>] [-LoggingLevel {Off | Critical | Error | Warning | Information | Verbose | ActivityTracing | All}] [-Confirm] [-WhatIf] [<CommonParameters>]`


### <a name="parameters"></a>매개 변수
#### `-Credential <PSCredential>`
디바이스 관리 기관을 전환할 때 사용되는 Azure AD 사용자 계정에 대한 PowerShell 자격 증명 개체입니다. 매개 변수를 지정 하지 않으면 사용자가 자격 증명을 입력 합니다. 이 사용자 계정에 대한 디렉터리 역할은 **Intune 관리자**의 관리 역할이 있는 **전역 관리자** 또는 **제한된 관리자**여야 합니다.

#### `-DeviceIds <Guid[]>`
해당 관리 기관을 전환해야 하는 MDM 디바이스의 ID입니다. 디바이스 ID는 Configuration Manager 콘솔이 표시하는 디바이스에 대한 고유 식별자입니다.

#### `-Force [<SwitchParameter>]`
계속해야 하는 프롬프트를 사용하지 않도록 설정하려면 매개 변수를 지정합니다.<br>
 
#### `-LogFilePath <string>`
로그 파일 위치의 경로입니다.
 
#### `-LoggingLevel <SourceLevels>`
로그 파일에 기록돼야 할 로그 형식을 결정하는 데 사용된 로그 수준입니다.
 
다음은 LoggingLevel에 대한 가능한 값입니다.

  - ActivityTracing
  - 모두
  - 중요
  - 오류
  - 정보
  - 해제
  - 자세한 정보 표시
  - 경고
 
#### `-Confirm [<SwitchParameter>]`
명령을 실행 하기 전에 확인을 묻는 됩니다.
 
#### `-WhatIf [<SwitchParameter>]`
실제로 명령을 실행 하지 않고 명령을 실행할 경우에 상황에 대해 설명 합니다.
 
#### `<CommonParameters>`
이 cmdlet은 공통 매개 변수를 지원 합니다. Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer, PipelineVariable, 및 outvariable을 지원 합니다. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

### <a name="example-1"></a>예제 1

``` powershell
C:\PS>Switch-MdmDeviceAuthority -Credential $creds -DeviceIds $deviceIds
 
  DeviceId       : 62e6ea43-18f8-4278-bcd4-a4baed2c6d24
  Success        : True
  FailureReason  :
  NewAuthority   : Intune
  CompletionTime : 11/15/2017 8:00:11 PM
 
Description
 
-----------
 
Successfully switched the management authority of the device from Configuration Manager to Intune.
```

### <a name="remarks"></a>설명
- 예제를 보려면 `get-help Switch-MdmDeviceAuthority -examples`을 입력합니다.  
- 자세한 내용은 `get-help Switch-MdmDeviceAuthority -detailed`을 입력합니다.  
- 기술 정보는 `get-help Switch-MdmDeviceAuthority -full`을 입력합니다.  
- 온라인 도움말은 `get-help Switch-MdmDeviceAuthority -online`을 입력합니다.   



## <a name="next-steps"></a>다음 단계

사용자를 마이그레이션하고 Intune 기능을 테스트한 후에는 Intune 테넌트의 [MDM 기관을 Configuration Manager에서 Intune으로 변경](migrate-change-mdm-authority.md)할 준비가 되었는지 확인하는 것이 좋습니다. 
