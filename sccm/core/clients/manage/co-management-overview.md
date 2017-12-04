---
title: "Windows 10 장치의 공동 관리"
description: "Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 장치를 동시에 관리하는 방법을 알아봅니다."
keywords: 
author: dougeby
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: 
ms.assetid: d6bbc787-83a5-44b4-ad64-016e5da7413f
ms.openlocfilehash: c0a577c6076630f0615f953091f35c4f3c2d0a7d
ms.sourcegitcommit: 536f7295e9ea361f1f9ead6c25f3685deb041ad8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="co-management-for-windows-10-devices"></a>Windows 10 장치의 공동 관리    
<!-- 1350871 -->
고객은 보통 낮은 비용으로 간소화된 클라우드 기반 솔루션을 사용하여 모바일 장치를 관리하는 동일한 방식으로 Windows 10 장치를 관리하려고 합니다. 그러나 기존 관리에서 최신 관리로 전환하기가 어려울 수 있습니다. Windows 10, 버전 1709(Fall Creators Update라고도 함) 이상부터는 Windows 10 장치를 온-프레미스 AD(Active Directory)와 클라우드 기반 Azure AD에 동시에 조인할 수 있습니다(하이브리드 Azure AD). Configuration Manager 버전 1710부터 공동 관리에서는 이러한 향상된 기능을 통해 Configuration Manager 및 Intune을 모두 사용하여 Windows 10 장치를 동시에 관리할 수 있습니다. 이것은 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다. 

공동 관리에 도달하는 데는 두 가지 주요 경로가 있습니다.  하나는 Configuration Manager가 프로전된 공동 관리이며, Configuration Manager에서 관리하는 Windows 10 장치와 조인된 하이브리드 Azure AD가 Intune에 등록됩니다. 다른 하나는 Intune이 프로비전된 장치이며, Intune에 등록된 다음 Configuration Manager 클라이언트와 함께 설치되어 공동 관리 상태가 됩니다.  

## <a name="prerequisites"></a>전제 조건
공동 관리를 활성화하기 전에 다음 필수 구성 요소를 준비해야 합니다. 일반 필수 구성 요소 및 Configuration Manager 클라이언트가 있는 장치와 클라이언트가 설치되지 않은 장치에 대한 다른 필수 구성 요소가 있습니다.

### <a name="general-prerequisites"></a>일반 전제 조건
다음은 공동 관리를 사용하기 위한 일반 전제 조건입니다.  

- Configuration Manager 버전 1710 이상
- Azure AD
- 모든 사용자의 EMS 또는 Intune 라이선스
- 사용하도록 설정된 [Azure AD 자동 등록](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- **Intune**으로 설정된 Intune 구독 및 Intune의 MDM 기관


   > [!Note]  
   > 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. Intune 독립 실행형으로 마이그레이션하는 방법을 알아보려면 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.

### <a name="additional-prerequisites-for-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 있는 장치에 대한 추가 필수 구성 요소
- Windows 10, 버전 1709(Fall Creators Update라고도 함) 이상
- [조인된 하이브리드 Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)(AD와 Azure AD에 조인)

### <a name="additional-prerequisites-for-devices-without-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 없는 장치에 대한 추가 필수 구성 요소
- Windows 10, 버전 1709(Fall Creators Update라고도 함) 이상
- Configuration Manager의 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway)(Intune을 사용하여 Configuration Manager 클라이언트를 설치하는 경우)

## <a name="workloads-you-can-switch-to-intune"></a>Intune으로 전환할 수 있는 작업
공동 관리를 활성화한 후에 Configuration Manager가 계속 모든 워크로드를 관리합니다. 준비되었는지 결정할 때 Intune으로 사용 가능한 워크로드를 관리하기 시작할 수 있습니다. Intune에서 다음과 같은 워크로드를 관리할 수 있습니다.   

### <a name="compliance-policies"></a>규정 준수 정책
규정 준수 정책은 장치가 조건부 액세스 정책을 준수하는 것으로 간주되기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 장치를 모니터링하고 준수 문제를 수정할 수도 있습니다. 자세한 내용은 [장치 규정 준수 정책](/sccm/mdm/deploy-use/device-compliance-policies)를 참조하세요.  

### <a name="windows-update-for-business-policies"></a>비즈니스용 Windows 업데이트 정책
비즈니스용 Windows 업데이트 정책을 통해 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 장치에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. 자세한 내용은 [비즈니스용 Windows 업데이트 지연 정책 구성](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies)을 참조하세요.  

### <a name="resource-access-policies"></a>리소스 액세스 정책
리소스 액세스 정책은 장치에 대한 VPN, Wi-Fi, 전자 메일 및 인증서 설정을 구성합니다. 자세한 내용은 [리소스 액세스 프로필 배포](/sccm/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)를 참조하세요.

## <a name="architectural-overview-for-co-management"></a>공동 관리에 대한 아키텍처 개요
다음 다이어그램은 공동 관리의 아키텍처 개요 및 기존 구성 및 Intune 인프라에 맞추는 방법을 제공합니다.

![공동 관리 아키텍처 다이어그램](./media/co-management-arch.svg)

## <a name="scenarios-to-enable-co-management"></a>공동 관리를 사용하도록 설정하는 시나리오  
공동 관리를 Microsoft Intune에 등록된 Windows 10 장치 및 기존 Windows 10 Configuration Manager 클라이언트 모두에서 사용할 수 있습니다. 두 시나리오는 Windows 10 장치를 Configuration Manager와 Intune에서 동시에 관리하고 AD와 Azure AD에 조인합니다.  

### <a name="devices-enrolled-in-intune"></a>Intune에 등록된 장치  
Windows 10 장치를 Intune에 등록하는 경우 공동 관리를 위해 클라이언트를 준비하기 위해 (특정 명령줄 인수를 사용하여) 장치에 Configuration Manager 클라이언트를 설치할 수 있습니다. 그런 다음 Configuration Manager 콘솔에서 공동 관리를 사용하여 특정 Windows 10 장치의 Intune에 특정 워크로드를 이동하기 시작합니다.  

아직 Intune에 등록되지 않은 Windows 10 장치의 경우 Azure에서 자동 등록을 사용하여 장치를 등록할 수 있습니다. 새 Windows 10 장치의 경우 [Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot)을 사용하여 OOBE(Out of Box Experience)를 구성할 수 있습니다. 여기에는 Intune에서 장치를 등록하는 자동 등록이 포함되어 있습니다.  

### <a name="configuration-manager-clients"></a>Configuration Manager 클라이언트
Windows 10 장치가 Configuration Manager 클라이언트에 있는 경우 이러한 장치를 등록하고 Configuration Manager 콘솔에서 공동 관리를 사용할 수 있습니다. Configuration Manager는 Azure AD 테넌트 정보에 따라 Intune에 자동 등록을 트리거합니다.  


## <a name="remote-actions-available-in-intune-on-azure-for-co-managed-devices"></a>Azure의 Intune에서 공동 관리 장치에 사용할 수 있는 원격 작업
Windows 10 장치가 공동 관리를 사용하도록 설정한 경우 Azure의 Intune에서 다음과 같은 원격 작업을 사용할 수 있습니다.  
- [초기화](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
- [선택적 초기화](https://docs.microsoft.com/intune/apps-selective-wipe)
- [장치 삭제](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
- [장치 다시 시작](https://docs.microsoft.com/intune/device-restart)
- [새로운 시작](https://docs.microsoft.com/intune/device-fresh-start)

## <a name="next-steps"></a>다음 단계
[공동 관리를 위해 Windows 10 장치 준비](co-management-prepare.md)