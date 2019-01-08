---
title: Configuration Manager 워크로드를 Intune으로 전환
titleSuffix: Configuration Manager
description: Configuration Manager에서 현재 관리하고 있는 워크로드를 Microsoft Intune으로 전환하는 방법을 알아봅니다.
ms.prod: configuration-manager
ms.technology: configmgr-client
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: 60e2022f-a4f9-40dd-af01-9ecb37b43878
ms.openlocfilehash: e3bd3bfda92fb877bac3ca68dbecf8b4a4078d4d
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53416948"
---
# <a name="switch-configuration-manager-workloads-to-intune"></a>Configuration Manager 워크로드를 Intune으로 전환

[공동 관리를 위해 Windows 10 디바이스를 준비](/sccm/core/clients/manage/co-management-prepare)한 후 다음 단계는 Intune에 자동 클라이언트 등록을 사용하도록 설정하는 것입니다. 그런 다음, 준비되면 특정 Configuration Manager 워크로드를 Intune으로 전환합니다. 


## <a name="setup-co-management"></a>공동 관리 설정

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다.  

2. 리본의 **홈** 탭의 **관리** 그룹에서  **공동 관리 구성**을 선택합니다. 이 작업을 통해 공동 관리 구성 마법사를 엽니다.  

3. 구독 페이지에서 **로그인**을 선택합니다. Intune 테넌트에 로그인한 다음, **다음**을 선택합니다.  

4. 사용 여부 페이지에서 **파일럿** 또는 **모두** 중 하나를 선택합니다.  

    이 작업을 통해 Intune에서 자동 클라이언트 등록을 사용하도록 설정합니다. **파일럿**을 선택하는 경우 파일럿 컬렉션의 멤버인 Configuration Manager 클라이언트만이 Intune에 자동으로 등록됩니다. 이 옵션을 사용하면 클라이언트의 하위 집합에서 공동 관리를 사용하여 처음에 공동 관리를 테스트하고 단계적 접근을 사용하여 공동 관리를 롤아웃할 수 있습니다.  

    표시된 명령줄을 사용하여 이미 Intune에 등록된 디바이스에 대해 Intune에서 Configuration Manager 클라이언트를 앱으로 배포합니다. 자세한 내용은 [Intune에 등록된 Windows 10 디바이스](/sccm/core/clients/manage/co-management-prepare#windows-10-devices-enrolled-in-intune)를 참조하세요.  

5. 워크로드 페이지에서 Configuration Manager 워크로드를 Intune에서 관리하도록 전환할지를 선택합니다. 이번에는 모든 워크로드를 전환하지 않고 이전 페이지에서 등록을 사용할 수 있습니다. 

    **Pilot Intune** 설정은 파일럿 컬렉션의 디바이스에 대해서만 관련된 워크로드를 전환합니다. **Intune** 설정은 공동 관리되는 모든 Windows 10 디바이스에 대해 관련된 워크로드를 전환합니다.  

    > [!Important] 
    > 워크로드를 전환하기 전에 Intune에서 해당 워크로드를 올바로 구성하고 배포했는지 확인합니다. 워크로드가 항상 디바이스에 대한 관리 도구 중 하나에서 관리되어야 합니다.  

6. 준비 페이지에서 다음 설정을 구성합니다.  

    - **파일럿**: 파일럿 그룹에는 선택한 컬렉션이 하나 이상 포함되어 있습니다. 이 그룹을 공동 관리의 단계별 롤아웃 중 일부로 사용합니다. 작은 테스트 컬렉션으로 시작한 다음, 공동 관리를 더 많은 사용자 및 디바이스에 롤아웃하는 경우 파일럿 그룹에 더 많은 컬렉션을 추가합니다. 언제든 파일럿 그룹의 컬렉션을 변경할 수 있습니다.  

    - **프로덕션:** 하나 이상의 컬렉션을 포함하여 **제외 그룹**을 구성합니다. 이 그룹에 있는 컬렉션의 멤버인 디바이스는 공동 관리를 사용하지 않도록 제외됩니다.  

7. 공동 관리를 사용하려면 마법사를 완료합니다.  

<!--1357377--> Configuration Manager 버전 1806부터 공동 관리 워크로드를 전환하면 공동 관리되는 디바이스는 Microsoft Intune에서 자동으로 MDM 정책을 동기화합니다. 이 동기화는 Configuration Manager 콘솔의 클라이언트 알림에서 **컴퓨터 정책 다운로드** 작업을 시작할 때 발생합니다. 자세한 내용은 [클라이언트 알림을 사용하여 클라이언트 정책 검색 시작](/sccm/core/clients/manage/manage-clients#initiate-client-policy-retrieval-using-client-notification)을 참조합니다.



## <a name="modify-your-co-management-settings"></a>공동 관리 설정 수정

마법사를 사용하여 공동 관리를 사용하도록 설정한 후 공동 관리 속성에서 설정을 수정합니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다. 공동 관리 개체를 선택한 다음, 리본 메뉴에서 **속성**을 선택합니다. 



## <a name="supported-workloads"></a>지원되는 작업

다음 워크로드를 Configuration Manager에서 Intune으로 전환하는 데 사용할 수 있습니다.

- **디바이스 준수 정책**  

- **리소스 액세스 정책**: 이러한 Intune 정책에 대한 자세한 내용은 [리소스 액세스 프로필 배포](https://docs.microsoft.com/intune/device-profiles)를 참조하세요.
    - 전자 메일 프로필  
    - Wi-Fi 프로필  
    - VPN 프로필  
    - 인증서 프로필  

- **Windows 업데이트 정책**  

- **Endpoint Protection:** Configuration Manager 버전 1802부터 이 워크로드에는 다음과 같은 기능이 포함됩니다.  
    - Windows Defender Application Guard  
    - Windows Defender 방화벽  
    - Windows Defender SmartScreen  
    - Windows 암호화  
    - Windows Defender Exploit Guard  
    - Windows Defender Application Control  
    - Windows Defender Security Center  
    - Windows Defender Advanced Threat Protection  
    - Windows Information Protection  

- **디바이스 구성**: Configuration Manager 버전 1806부터<!--1357903-->:  

    - 디바이스 구성 워크로드를 이동하면 **리소스 액세스** 및 **Endpoint Protection** 워크로드도 이동합니다.  

    - Intune이 디바이스 구성 기관이더라도 Configuration Manager에서 공동 관리 디바이스로 설정을 배포할 수 있습니다. 이 예외는 조직에 필요한 설정을 구성하는 데 사용할 수 있지만 Intune에서는 아직 사용할 수 없습니다. 이 예외는 [Configuration Manager 구성 기준](/sccm/compliance/deploy-use/create-configuration-baselines)에서 지정합니다. 기준을 만들 때 또는 기존 기준 속성의 **일반** 탭에서 **공동 관리하는 클라이언트에 대해서도 항상 이 기준 적용** 옵션을 사용하도록 설정합니다.  

- **Office 365 간편 실행 앱**: Configuration Manager 버전 1806부터<!--1357841-->:  

    - 워크로드를 이동하면 앱이 디바이스의 **회사 포털**에 표시됩니다.  

    - 디바이스를 다시 시작하지 않을 경우 Office 업데이트가 클라이언트에 표시되는 데 약 24시간이 걸릴 수 있습니다.  

    - **디바이스에서 Intune으로 Office 365 애플리케이션 관리**라는 새 글로벌 조건이 있습니다. 이 조건은 기본적으로 새 Office 365 애플리케이션에 대한 요구 사항으로 추가됩니다. 이 워크로드를 전환하는 경우 공동 관리되는 클라이언트는 애플리케이션의 요구 사항을 충족하지 못합니다. 따라서 Configuration Manager를 통해 배포된 Office 365를 설치하지 않습니다.  

- **클라이언트 앱**: Configuration Manager 버전 1806부터 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 제공<!--1357892-->:  

    - 이 워크로드를 전환하면 Intune에서 배포된 사용 가능한 모든 앱을 회사 포털에서 사용 가능  

    - Configuration Manager에서 배포하는 앱은 소프트웨어 센터에서 사용 가능  



## <a name="monitor-co-management"></a>공동 관리 모니터링

공동 관리를 사용하도록 설정하면 다음 방법을 사용하여 공동 관리 디바이스를 모니터링합니다.

- [공동 관리 대시보드](/sccm/core/clients/manage/co-management-dashboard)  

- **SQL 보기 및 WMI 클래스**: Configuration Manager 사이트 데이터베이스 또는 **SMS_Client_ComanagementState** WMI 클래스에서 **v_ClientCoManagementState** SQL 보기를 쿼리합니다. WMI 클래스의 정보를 사용하면 Configuration Manager에서 사용자 지정 컬렉션을 만들어 공동 관리 배포 상태를 확인할 수 있습니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요. 다음 필드는 SQL 보기 및 WMI 클래스에서 사용할 수 있습니다.  
  - **MachineId**: Configuration Manager 클라이언트에 대한 고유한 디바이스 ID 지정  
  - **MDMEnrolled**: 디바이스가 MDM에 등록되었는지 여부 지정  
  - **기관**: 디바이스가 등록된 기관 지정  
  - **ComgmtPolicyPresent**: 클라이언트에 Configuration Manager 공동 관리 정책이 있는지 여부를 지정합니다. **MDMEnrolled** 값이 **0**이면 공동 관리 정책이 클라이언트에 있는지 여부에 관계 없이 디바이스를 공동 관리하지 않습니다.  

    > [!Note]  
    > **MDMEnrolled** 필드 및 **ComgmtPolicyPresent** 필드의 값이 모두 **1**이면 디바이스가 공동 관리됩니다.  

- **배포 정책**: 두 정책을 **모니터링** 작업 영역의 **배포** 노드에서 만듭니다. 한 정책은 파일럿 그룹용이며 다른 정책은 프로덕션용입니다. 이러한 정책은 Configuration Manager에서 정책을 적용한 디바이스의 수만 보고합니다. 디바이스를 공동 관리할 수 있기 전의 요구 사항인 Intune에 등록된 디바이스의 수는 고려하지 않습니다.  



## <a name="check-compliance-for-co-managed-devices"></a>공동 관리되는 디바이스에 대한 준수 확인

Configuration Center 또는 Intune에서 조건부 액세스를 관리하는지 여부에 관계없이 사용자는 소프트웨어 센터를 사용하여 공동 관리되는 Windows 10 디바이스의 준수 여부를 확인할 수 있습니다. 또한 Intune에서 조건부 액세스를 관리하는 경우 회사 포털 앱을 사용하여 준수 여부를 확인할 수도 있습니다.



## <a name="next-steps"></a>다음 단계

Intune으로 전환한 워크로드를 관리하는 데 도움이 되는 다음 리소스를 사용합니다.
- [디바이스 준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)
- [리소스 액세스 정책](https://docs.microsoft.com/intune/device-profiles)
- [비즈니스용 Windows 업데이트 정책](https://docs.microsoft.com/intune/windows-update-for-business-configure)
- [Microsoft Intune용 Endpoint Protection](https://docs.microsoft.com/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
