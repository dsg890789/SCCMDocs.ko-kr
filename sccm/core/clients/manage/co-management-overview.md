---
title: Windows 10 장치의 공동 관리
titleSuffix: Configuration Manager
description: Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 장치를 동시에 관리하는 방법을 알아봅니다.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology: ''
ms.assetid: d6bbc787-83a5-44b4-ad64-016e5da7413f
ms.openlocfilehash: 1657cbacde468ef7c54f95524e0fa9607a1a0186
ms.sourcegitcommit: e23350fe65ff99228274e465b24b5e163769f38f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="co-management-for-windows-10-devices"></a>Windows 10 장치의 공동 관리    
 이전 Windows 10 업데이트에서 이미 Windows 10 장치를 온-프레미스 AD(Active Directory)와 클라우드 기반 Azure AD에 동시에 조인할 수 있습니다(하이브리드 Azure AD). Configuration Manager 버전 1710부터 공동 관리에서는 이러한 향상된 기능을 통해 Configuration Manager 및 Intune을 모두 사용하여 Windows 10 버전 1709 장치를 동시에 관리할 수 있습니다. <!-- 1350871 -->
## <a name="why-co-management"></a>공동 관리가 필요한 이유
고객은 보통 낮은 비용으로 간소화된 클라우드 기반 솔루션을 사용하여 모바일 장치를 관리하는 동일한 방식으로 Windows 10 장치를 관리하려고 합니다. 그러나 기존 관리에서 최신 관리로 전환하기가 어려울 수 있습니다.  
## <a name="what-is-co-management"></a>공동 관리란?
공동 관리를 사용하면 Configuration Manager와 Intune을 모두 사용하여 Windows 10 장치를 동시에 관리할 수 있습니다. 이것은 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다.

## <a name="benefits"></a>이점 
- 즉시 Intune 기능 사용 
    - 원격 작업
        - [초기화](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
        - [선택적 초기화](https://docs.microsoft.com/intune/apps-selective-wipe)
        - [장치 삭제](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
        - [장치 다시 시작](https://docs.microsoft.com/intune/device-restart)
        - [새로운 시작](https://docs.microsoft.com/intune/device-fresh-start)
    - 다음 워크로드에 대해 Intune과 오케스트레이션:
        - [준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)
        - [리소스 액세스 정책](https://docs.microsoft.com/intune/device-profiles)
        - [Windows 업데이트 정책](https://docs.microsoft.com/intune/windows-update-for-business-configure)
        - [Endpoint Protection](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10)(Configuration Manager 버전 1802부터) <!-- 1357365 -->
    
## <a name="how-to-configure-co-management"></a>공동 관리 구성 방법
공동 관리에 도달하는 데는 두 가지 주요 경로가 있습니다. 하나는 Configuration Manager가 프로전된 공동 관리이며, Configuration Manager에서 관리하는 Windows 10 장치와 조인된 하이브리드 Azure AD가 Intune에 등록됩니다. 다른 하나는 Intune이 프로비전된 장치이며, Intune에 등록된 다음 Configuration Manager 클라이언트와 함께 설치되어 공동 관리 상태가 됩니다.

### <a name="configuration-manager"></a>**Configuration Manager**
 -  Configuration Manager 버전 1710 이상으로 업그레이드합니다.


### <a name="azure-active-directory"></a>**Azure Active Directory**
  - [하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)(AD와 Azure AD에 조인)
  - [Windows 10 자동 등록 사용](https://docs.microsoft.com/intune/windows-enroll)


### <a name="intune"></a>**Intune**
 - [Intune 구독 설정 방법](/sccm/mdm/deploy-use/configure-intune-subscription) 또는 https://docs.microsoft.com/en-us/intune/setup-steps
 - [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)


### <a name="enable-co-management"></a>공동 관리 사용 
 Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다. 리본에서  **공동 관리 구성**을 선택하여 **공동 관리 등록 마법사**를 엽니다. 
   
1. **구독** 페이지에서 **로그인**을 클릭하고 Intune 테넌트에 로그인한 후 **다음**을 클릭합니다.    
2. **사용 여부** 페이지에서 **Automatic enrollment into Intune**(Intune에 자동 등록) 설정을 선택합니다. 필요한 경우 Intune에 이미 등록된 장치의 명령줄을 복사합니다. 
3. **워크로드** 페이지에서 각 워크로드에 대해 Intune으로 관리하기 위해 이동할 장치 그룹을 선택합니다.
4. **준비** 페이지에서 **파일럿 컬렉션**으로 지정할 장치 컬렉션을 선택합니다. **요약**을 확인하고 마법사를 완료합니다. 

### <a name="upgrade-windows-10-client"></a>Windows 10 클라이언트 업그레이드
- [Windows 10 버전 1709(Fall Creators Update라고도 함) 이상](/sccm/osd/deploy-use/manage-windows-as-a-service)으로 업그레이드

### <a name="configure-workloads-to-switch-to-intune"></a>Intune으로 전환하도록 워크로드 구성 
[Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune) 문서에서는 특정 Configuration Manager 워크로드를 Intune으로 전환하는 방법을 보여 줍니다. 또한 이 문서에서는 워크로드가 전환되는 장치 그룹 변경에 대한 지침도 제공합니다.

- **준수 정책:** 준수 정책은 장치가 조건부 액세스 정책을 준수하는 것으로 간주되기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 장치를 모니터링하고 준수 문제를 수정할 수도 있습니다. 자세한 내용은 [장치 규정 준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)를 참조하세요.  

- **Windows 업데이트 정책:** 비즈니스용 Windows 업데이트 정책을 통해 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 장치에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. 자세한 내용은 [비즈니스용 Windows 업데이트 지연 정책 구성](https://docs.microsoft.com/intune/windows-update-for-business-configure)을 참조하세요.  

- **리소스 액세스 정책:** 리소스 액세스 정책은 장치에 대한 VPN, Wi-Fi, 메일 및 인증서 설정을 구성합니다. 자세한 내용은 [리소스 액세스 프로필 배포](https://docs.microsoft.com/intune/device-profiles)를 참조하세요.

- **Endpoint Protection:** Configuration Manager 1802부터 Endpoint Protection 워크로드를 Intune으로 전환할 수 있습니다. 자세한 내용은 [Microsoft Intune용 Endpoint Protection](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10)<!-- 1357365 --> 및 [Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune)를 참조하세요.


### <a name="install-configuration-manager-client-to-the-devices-enrolled-in-intune"></a>Intune에 등록된 장치에 Configuration Manager 클라이언트 설치
Windows 10 장치를 Intune에 등록하는 경우 공동 관리를 위해 클라이언트를 준비하기 위해 [특정 명령줄 인수를 사용](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client)하여 장치에 Configuration Manager 클라이언트를 설치할 수 있습니다. 그런 다음 Configuration Manager 콘솔에서 공동 관리를 사용하여 특정 Windows 10 장치의 Intune에 특정 워크로드를 이동하기 시작합니다.
아직 Intune에 등록되지 않은 Windows 10 장치의 경우 Azure에서 자동 등록을 사용하여 장치를 등록할 수 있습니다. 새 Windows 10 장치의 경우 [Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot)을 사용하여 OOBE(Out of Box Experience)를 구성할 수 있습니다. 여기에는 Intune에서 장치를 등록하는 자동 등록이 포함되어 있습니다.
 - Configuration Manager의 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) 사용(Intune을 사용하여 Configuration Manager 클라이언트를 설치하는 경우만 해당)

## <a name="monitor-co-management"></a>공동 관리 모니터링
[공동 관리 대시보드](/sccm/core/clients/manage/co-management-dashboard)를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 장치를 식별하는 데 도움이 될 수 있습니다.


## <a name="next-steps"></a>다음 단계
[공동 관리를 위해 Windows 10 장치 준비](co-management-prepare.md)
