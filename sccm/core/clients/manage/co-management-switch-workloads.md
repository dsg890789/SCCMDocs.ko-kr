---
title: Configuration Manager 워크로드를 Intune으로 전환
titleSuffix: Configuraton Manager
description: Configuration Manager에서 현재 관리하고 있는 워크로드를 Microsoft Intune으로 전환하는 방법을 알아봅니다.
ms.prod: configuration-manager
ms.technology: configmgr-client
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.assetid: 60e2022f-a4f9-40dd-af01-9ecb37b43878
ms.openlocfilehash: 439e4e26c08b5a2710da0978ed2407d715bc86bd
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="switch-configuration-manager-workloads-to-intune"></a>Configuration Manager 워크로드를 Intune으로 전환
[공동 관리를 위해 Windows 10 장치 준비](co-management-prepare.md)에서 공동 관리를 위해 Windows 10 장치를 준비했습니다. 이러한 장치가 AD, Azure AD에 조인되고 Intune에 등록되고 Configuration Manager 클라이언트를 포함합니다. Windows 10 장치가 AD에 조인되고 Configuration Manager 클라이언트를 포함했지만 Azure AD에 되거나 Intune에 등록되지 않았습니다. 다음 절차에서는 공동 관리를 사용하고, 공동 관리를 위해 나머지 Windows 10 장치(Intune에 등록되지 않은 Configuration Manager 클라이언트)를 준비하고, 특정 Configuration Manager 워크로드를 Intune으로 전환하기 시작할 수 있는 단계를 제공합니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.    
2. [홈] 탭의 [관리] 그룹에서  **공동 관리 구성**을 선택하여 공동 관리 구성 마법사를 엽니다.    
3. 구독 페이지에서 **로그인**을 클릭하고 Intune 테넌트에 로그인하고 **다음**을 클릭합니다.   
4. [사용 여부] 페이지에서 **파일럿** 또는 **모두**를 선택하여 Intune에서 자동 등록을 사용하도록 설정하고 **다음**을 클릭합니다. **파일럿**을 선택하는 경우 파일럿 그룹의 멤버인 Configuration manager 클라이언트만이 Intune에서 자동으로 등록됩니다. 이 옵션을 사용하면 클라이언트의 하위 집합에서 공동 관리를 사용하여 처음에 공동 관리를 테스트하고 단계적 접근을 사용하여 공동 관리를 롤아웃할 수 있습니다. 명령줄을 사용하여 이미 Intune에 등록된 장치에 대해 Intune에서 Configuration Manager 클라이언트를 앱으로 배포할 수 있습니다. 자세한 내용은 [Intune에 등록된 Windows 10 장치](co-management-prepare.md#windows-10-devices-enrolled-in-intune)를 참조하세요.
5. [워크로드] 페이지에서 Configuration Manager 워크로드를 Pilot Intune 또는 Intune에서 관리하도록 전환할지 여부를 선택하고 **다음**을 클릭합니다. **Pilot Intune** 설정은 파일럿 그룹의 장치에 대해서만 관련된 워크로드를 전환합니다. **Intune** 설정은 공동 관리되는 모든 Windows 10 장치에 대해 관련된 워크로드를 전환합니다. 
        
   > [!Important]    
   > 워크로드를 전환하기 전에 Intune에서 해당 워크로드가 올바르게 구성되고 배포되었는지 확인합니다. 이렇게 하면 워크로드가 항상 장치에 대한 관리 도구 중 하나에서 관리됩니다.   
1. 스테이징 페이지에서 다음 설정을 구성한 후에 **다음**을 클릭합니다.
    - **파일럿**: 파일럿 그룹에는 선택한 컬렉션이 하나 이상 포함되어 있습니다. 이 그룹을 공동 관리의 단계별 롤아웃 중 일부로 사용합니다. 작은 테스트 컬렉션을 시작하고, 공동 관리를 더 많은 사용자 및 장치에 롤아웃하는 경우 파일럿 그룹에 더 많은 컬렉션을 추가할 수 있습니다. 공동 관리 속성에서 언제든지 파일럿 그룹의 컬렉션을 변경할 수 있습니다.
    - **프로덕션**: 하나 이상의 컬렉션이 포함된 **제외 그룹**을 구성합니다. 이 그룹에 있는 컬렉션의 멤버인 장치는 공동 관리를 사용하지 않도록 제외됩니다. 
2. 공동 관리를 사용하려면 마법사를 완료합니다.  

## <a name="modify-your-co-management-settings"></a>공동 관리 설정 수정
마법사를 사용하여 공동 관리를 사용하도록 설정하면 공동 관리 속성에서 설정을 수정할 수 있습니다.  
- Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.  
공동 관리 개체를 선택한 다음 [홈] 탭에서 **속성**을 클릭합니다. 

## <a name="workloads-able-to-be-transitioned-to-intune"></a>Intune으로 전환될 수 있는 워크로드
특정 워크로드는 Intune을 통해 전환될 수 있습니다. 다음 목록은 전환에 사용할 수 있는 워크로드로 업데이트됩니다.
1. 장치 준수 정책
2. 리소스 액세스 정책: 리소스 액세스 정책은 장치에 대한 VPN, Wi-Fi, 메일 및 인증서 설정을 구성합니다. 자세한 내용은 [리소스 액세스 프로필 배포](https://docs.microsoft.com/intune/device-profiles)를 참조하세요.
      - 전자 메일 프로필
      - Wi-Fi 프로필
      - VPN 프로필
      - 인증서 프로필
3. Windows 업데이트 정책
4. Endpoint Protection(Configuration Manager 버전 1802부터)
      - Windows Defender Application Guard
      - Windows Defender 방화벽
      - Windows Defender SmartScreen
      - Windows 암호화
      - Windows Defender Exploit Guard
      - Windows Defender Application Control
      - Windows Defender Security Center
      - Windows Defender Advanced Threat Protection



## <a name="monitor-co-management"></a>공동 관리 모니터링
공동 관리를 사용하도록 설정하면 다음 방법을 사용하여 공동 관리 장치를 모니터링할 수 있습니다.

- [공동 관리 대시보드](/sccm/core/clients/manage/co-management-dashboard)
- **SQL 보기 및 WMI 클래스**: Configuration Manager 사이트 데이터베이스 또는 **SMS&#95;Client&#95;ComanagementState** WMI 클래스에서 **v&#95;ClientCoManagementState** SQL 보기를 쿼리할 수 있습니다. WMI 클래스의 정보를 사용하면 Configuration Manager에서 사용자 지정 컬렉션을 만들어 공동 관리 배포 상태를 확인할 수 있습니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요. 다음 필드는 SQL 보기 및 WMI 클래스에서 사용할 수 있습니다. 
    - **MachineId**: Configuration Manager 클라이언트에 대한 고유한 장치 ID를 지정합니다.
    - **MDMEnrolled**: 장치가 MDM에 등록되었는지 여부를 지정합니다. 
    - **Authority**: 장치가 등록된 기관을 지정합니다.
    - **ComgmtPolicyPresent**: 클라이언트에 Configuration Manager 공동 관리 정책이 있는지 여부를 지정합니다. **MDMEnrolled** 값이 **0**이면 공동 관리 정책이 클라이언트에 있는지 여부에 관계 없이 장치가 공동 관리되지 않습니다.

   > [!Note]    
   > **MDMEnrolled** 필드 및 **ComgmtPolicyPresent** 필드의 값이 모두 **1**이면 장치가 공동 관리됩니다.

- **배포 정책**: **모니터링** > **배포**에서 만든 두 가지 정책, 즉 파일럿 그룹에 대한 정책과 프로덕션 환경에 대한 정책이 있습니다. 이러한 정책은 Configuration Manager에서 정책을 적용한 장치의 수만 보고합니다. 장치를 공동 관리할 수 있기 전의 요구 사항인 Intune에 등록된 장치의 수는 고려하지 않습니다.  

## <a name="check-compliance-for-co-managed-devices"></a>공동 관리되는 장치에 대한 준수 확인
Configuration Center 또는 Intune에서 조건부 액세스를 관리하는지 여부에 관계 없이 사용자는 소프트웨어 센터를 사용하여 공동 관리되는 Windows 10 장치의 준수 여부를 확인할 수 있습니다. 또한 Intune에서 조건부 액세스를 관리하는 경우 회사 포털 앱을 사용하여 준수 여부를 확인할 수도 있습니다.

## <a name="next-steps"></a>다음 단계
Intune으로 전환한 워크로드를 관리하는 데 도움이 되는 다음 리소스를 사용합니다.
- [장치 준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)
- [리소스 액세스 정책](https://docs.microsoft.com/intune/device-profiles)
- [비즈니스용 Windows 업데이트 정책](https://docs.microsoft.com/intune/windows-update-for-business-configure)
- [Microsoft Intune용 Endpoint Protection](https://docs.microsoft.com/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
