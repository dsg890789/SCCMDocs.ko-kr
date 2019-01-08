---
title: Windows 10 디바이스의 공동 관리
titleSuffix: Configuration Manager
description: Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 디바이스를 동시에 관리하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 08/02/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: d6bbc787-83a5-44b4-ad64-016e5da7413f
ms.openlocfilehash: 6434ba443cb884c7fbb5d727c5db3c80d2d88aad
ms.sourcegitcommit: 12b71da551350c99c5916df3629e33e31040db15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2018
ms.locfileid: "53530934"
---
# <a name="co-management-for-windows-10-devices"></a>Windows 10 디바이스의 공동 관리    

이전 Windows 10 업데이트에서 이미 Windows 10 디바이스를 온-프레미스 AD(Active Directory)와 클라우드 기반 Azure AD에 동시에 조인할 수 있습니다(하이브리드 Azure AD). Configuration Manager 버전 1710부터 공동 관리는 이 개선 사항을 활용합니다. 공동 관리를 사용하면 Configuration Manager와 Intune을 모두 사용하여 Windows 10 버전 1709 디바이스를 동시에 관리할 수 있습니다. <!-- 1350871 -->


## <a name="why-co-management"></a>공동 관리가 필요한 이유

고객은 보통 낮은 비용으로 간소화된 클라우드 기반 솔루션을 사용하여 모바일 디바이스를 관리하는 동일한 방식으로 Windows 10 디바이스를 관리하려고 합니다. 그러나 기존 관리에서 최신 관리로 전환하기가 어려울 수 있습니다.  


## <a name="what-is-co-management"></a>공동 관리란?

공동 관리를 사용하면 Configuration Manager와 Intune을 모두 사용하여 Windows 10 디바이스를 동시에 관리할 수 있습니다. 이것은 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다.


## <a name="benefits"></a>이점 

다음의 Intune 기능을 즉시 사용합니다.  
 
- 원격 작업
    - [초기화](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
    - [선택적 초기화](https://docs.microsoft.com/intune/apps-selective-wipe)
    - [디바이스 삭제](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
    - [디바이스 다시 시작](https://docs.microsoft.com/intune/device-restart)
    - [새로운 시작](https://docs.microsoft.com/intune/device-fresh-start)  

- 다음 워크로드에 대해 Intune과 오케스트레이션:
    - [준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)
    - [리소스 액세스 정책](https://docs.microsoft.com/intune/device-profiles)
    - [Windows 업데이트 정책](https://docs.microsoft.com/intune/windows-update-for-business-configure)
    - [Endpoint Protection](https://docs.microsoft.com/intune/endpoint-protection-windows-10)(Configuration Manager 버전 1802부터) <!-- 1357365 -->
    - [디바이스 구성](https://docs.microsoft.com/intune/device-profile-create)(Configuration Manager 1806부터 시작) <!-- 1357903 -->
    - [Office 간편 실행 앱](https://docs.microsoft.com/intune/apps-add-office365)(Configuration Manager 1806부터 시작)<!--1357841-->
    - [모바일 앱](https://docs.microsoft.com/intune/app-management)(Configuration Manager 1806부터 시작하는 시험판 기능) <!--1357892-->



## <a name="how-to-configure-co-management"></a>공동 관리 구성 방법

 공동 관리에 연결하기 위한 두 가지 주요 경로가 있습니다.  

   - Configuration Manager에서 공동 관리 프로비전: 이미 Configuration Manager 클라이언트인 Azure AD 조인 Windows 10 디바이스를 Intune에 등록합니다.  

   - 프로비전된 Intune: 이미 Intune에 등록된 디바이스의 경우 Configuration Manager 클라이언트를 설치하여 공동 관리 상태가 됩니다. 


### <a name="configuration-manager"></a>Configuration Manager

 -  Configuration Manager 버전 1710 이상으로 업그레이드합니다.


### <a name="azure-active-directory"></a>Azure Active Directory

 - Windows 10 디바이스는 Azure AD에 조인되어야 합니다. 이러한 장치는 다음 형식 중 하나일 수 있습니다.  

     - [하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan), 여기서 디바이스가 온-프레미스 Active Directory에 조인되고 Azure Active Directory에 등록됩니다.

     - [Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)만 (이 유형은 "클라우드 도메인 조인"이라고도 함)<!--SCCMDocs issue 605-->

 - [Windows 10 자동 등록을 사용하도록 설정합니다](https://docs.microsoft.com/intune/windows-enroll).  


### <a name="intune"></a>Intune

- [Intune 구독 설정 방법](/sccm/mdm/deploy-use/configure-intune-subscription) 또는 [Intune 설정](/intune/setup-steps)  

- [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)  

  > [!Note]  
  > 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. 그러나 사용자를 Intune 독립 실행형으로 마이그레이션하기 시작한 후 관련 Windows 10 디바이스에 공동 관리를 활성화할 수 있습니다. Intune 독립 실행형으로 마이그레이션하는 방법에 대한 자세한 정보는 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.  


### <a name="enable-co-management"></a>공동 관리 사용 

 > [!Important]  
 > 버전 1802부터 공동 관리를 사용하도록 설정하려면 Configuration Manager의 관리자 계정이 **모든** 보안 범위를 갖는 **전체 관리자**이어야 합니다. 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.<!--SCCMDoc issue 626-->  

 Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다. 리본에서 **공동 관리 구성**을 클릭하여 **공동 관리 등록 마법사**를 엽니다. 
   
1. **구독** 페이지에서 **로그인**을 클릭합니다. Intune 테넌트에 로그인한 다음, **다음**을 클릭합니다.  

    > [!Tip]   
    > 테넌트에 로그인하는 데 사용된 계정이 Intune 라이선스를 할당했는지 확인합니다. 그렇지 않으면 “사용자가 인식되지 않습니다”라는 오류 메시지가 표시되고 실패합니다.  

2. **사용 여부** 페이지에서 **Intune에 자동 등록** 설정을 선택합니다. 필요한 경우 Intune에 이미 등록된 디바이스의 명령줄을 복사합니다.  

    > [!Note]  
    > 버전 1806부터 자동 등록은 모든 클라이언트에 대해 직접 실행되지 않습니다. 이 동작은 대규모 환경에 대해 등록 확장을 보다 잘 수행하게 합니다. Configuration Manager는 클라이언트 수에 따라 등록을 임의 지정합니다. 예를 들어 사용자 환경에 100,000명의 클라이언트가 있는 경우 이 설정을 사용하도록 설정하면 며칠에 걸쳐 등록이 가능합니다.<!--1358003-->  

3. **워크로드** 페이지에서 각 워크로드에 대해 Intune으로 관리하기 위해 이동할 디바이스 그룹을 선택합니다.  

4. **준비** 페이지에서 **파일럿 컬렉션**으로 지정할 디바이스 컬렉션을 선택합니다. **요약**을 확인하고 마법사를 완료합니다.  


### <a name="upgrade-windows-10-client"></a>Windows 10 클라이언트 업그레이드

- [Windows 10 버전 1709(Fall Creators Update라고도 함) 이상](/sccm/osd/deploy-use/manage-windows-as-a-service)으로 업그레이드


### <a name="configure-workloads-to-switch-to-intune"></a>Intune으로 전환하도록 워크로드 구성 

[Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune) 문서에서는 특정 Configuration Manager 워크로드를 Intune으로 전환하는 방법을 보여 줍니다. 또한 이 문서에서는 워크로드가 전환되는 디바이스 그룹 변경에 대한 지침도 제공합니다.

#### <a name="compliance-policies"></a>규정 준수 정책 
규정 준수 정책은 디바이스가 조건부 액세스 정책을 준수하는 것으로 간주되려면 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 디바이스를 모니터링하고 준수 문제를 수정할 수도 있습니다. 자세한 내용은 [디바이스 규정 준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)를 참조하세요.  

#### <a name="windows-update-policies"></a>Windows 업데이트 정책
비즈니스용 Windows 업데이트 정책을 통해 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 디바이스에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. 자세한 내용은 [비즈니스용 Windows 업데이트 지연 정책 구성](https://docs.microsoft.com/intune/windows-update-for-business-configure)을 참조하세요.  

#### <a name="resource-access-policies"></a>리소스 액세스 정책
리소스 액세스 정책은 디바이스에 대한 VPN, Wi-Fi, 전자 메일 및 인증서 설정을 구성합니다. 자세한 내용은 [리소스 액세스 프로필 배포](https://docs.microsoft.com/intune/device-profiles)를 참조하세요.

#### <a name="endpoint-protection"></a>Endpoint Protection
Configuration Manager 1802부터 Endpoint Protection 워크로드를 Intune으로 전환할 수 있습니다. 자세한 내용은 [Microsoft Intune용 Endpoint Protection](https://docs.microsoft.com/intune/endpoint-protection-windows-10)<!-- 1357365 --> 및 [Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune)를 참조하세요.

#### <a name="device-configuration"></a>디바이스 구성
Configuration Manager 1806부터 디바이스 구성 워크로드를 Intune으로 전환할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 디바이스 프로필 만들기](https://docs.microsoft.com/intune/device-profile-create) 및 [Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune)를 참조하세요.  <!--1357903-->

#### <a name="office-click-to-run-apps"></a>Office 간편 실행 앱
Configuration Manager 1806부터 Office 365 워크로드를 Intune으로 전환할 수 있습니다. 자세한 내용은 [Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune)를 참조하세요. <!--1357841-->

#### <a name="mobile-apps"></a>모바일 앱
Configuration Manager 1806부터 모바일 앱 워크로드를 Intune으로 전환할 수 있습니다. 이는 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요. 이 워크로드를 전환하면 Intune에서 배포된 사용 가능한 모든 앱을 회사 포털에서 사용할 수 있습니다. Configuration Manager에서 배포하는 앱은 소프트웨어 센터에서 사용할 수 있습니다.<!--1357892-->


### <a name="install-configuration-manager-client-to-the-devices-enrolled-in-intune"></a>Intune에 등록된 디바이스에 Configuration Manager 클라이언트 설치

Windows 10 디바이스를 Intune에 등록하는 경우 공동 관리를 위해 클라이언트를 준비하기 위해 [특정 명령줄을 사용](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client)하여 디바이스에 Configuration Manager 클라이언트를 설치합니다. 그런 다음 Configuration Manager 콘솔에서 공동 관리를 사용하여 특정 Windows 10 디바이스의 Intune에 특정 워크로드를 이동하기 시작합니다.
아직 Intune에 등록되지 않은 Windows 10 디바이스의 경우 Azure에서 자동 등록을 사용하여 디바이스를 등록합니다. 새 Windows 10 디바이스의 경우 [Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot)을 사용하여 OOBE(Out of Box Experience)를 구성합니다. 여기에는 Intune에서 디바이스를 등록하는 자동 등록이 포함됩니다.

Intune을 사용하여 Configuration Manager 클라이언트를 설치하는 경우 Configuration Manager의 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway)를 사용하도록 설정합니다.



## <a name="monitor-co-management"></a>공동 관리 모니터링

[공동 관리 대시보드](/sccm/core/clients/manage/co-management-dashboard)를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 디바이스를 식별하는 데 도움이 될 수 있습니다.



## <a name="next-steps"></a>다음 단계

[공동 관리를 위한 Windows 10 디바이스 준비](co-management-prepare.md)
