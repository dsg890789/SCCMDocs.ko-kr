---
title: Windows 10 디바이스의 공동 관리
titleSuffix: Configuration Manager
description: Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 디바이스를 동시에 관리하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 01/14/2019
ms.topic: overview
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: d6bbc787-83a5-44b4-ad64-016e5da7413f
ms.collection: M365-identity-device-management
ms.openlocfilehash: c88bf98e035499c271de8acf9d8fa222e5058447
ms.sourcegitcommit: 9aebc20b25cdef0af908918ccfd791f3264a5d94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "56755373"
---
# <a name="what-is-co-management"></a>공동 관리란?

<!-- 1350871 -->
공동 관리는 기존 Configuration Manager 배포를 Microsoft 365 클라우드에 연결하는 기본적인 방법입니다. 따라서 조건부 액세스와 같은 추가 클라우드 기반 기능을 잠금 해제할 수 있습니다. 

공동 관리를 통해 Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 디바이스를 동시에 관리할 수 있습니다. 또한 새 기능을 추가하여 Configuration Manager의 기존 투자를 클라우드에 연결할 수 있습니다. 공동 관리를 사용하면 조직에 가장 적합한 기술 솔루션을 유연하게 사용할 수 있습니다. 

Windows 10 디바이스에 Configuration Manager 클라이언트가 있고 디바이스가 Intune에 등록된 경우 두 서비스의 이점을 모두 활용할 수 있습니다. 어느 워크로드를 제어하든 기관을 Configuration Manager에서 Intune으로 전환할 수 있습니다. Intune으로 전환하지 않은 워크로드를 포함한 다른 모든 워크로드와 공동 관리에서 지원하지 않는 Configuration Manager의 다른 모든 기능은 계속 Configuration Manager에서 관리합니다.

또한 워크로드를 별도의 디바이스 컬렉션으로 파일럿 실행할 수도 있습니다. 파일럿 실행을 사용하면 더 큰 그룹을 전환하기 전에 하위 집합의 디바이스로 Intune 기능을 테스트할 수 있습니다. 

![공동 관리의 개요 다이어그램](media/co-management-overview.png)



## <a name="paths-to-co-management"></a>공동 관리 경로

공동 관리에 연결하기 위한 두 가지 주요 경로가 있습니다.  

- **기존 Configuration Manager 클라이언트**: 이미 Configuration Manager 클라이언트인 Windows 10 디바이스가 있습니다. 하이브리드 Azure AD를 설정하여 Intune에 등록합니다.  

- **새 인터넷 기반 디바이스**: Azure AD에 가입되고 Intune에 자동으로 등록되는 새 Windows 10 디바이스가 있습니다. Configuration Manager 클라이언트를 설치하여 공동 관리 상태가 됩니다.  

경로에 대한 자세한 내용은 [공동 관리 경로](/sccm/comanage/quickstart-paths)를 참조하세요.



## <a name="benefits"></a>이점 

공동 관리에서 기존 Configuration Manager 클라이언트를 등록하면 다음과 같은 즉각적인 값을 얻을 수 있습니다.  

- 디바이스 준수를 사용한 조건부 액세스  

- Intune 기반 원격 작업(예: 다시 시작, 원격 제어 또는 초기화)

- 디바이스 상태의 중앙 집중식 가시성  

- Azure AD(Azure Active Directory)를 사용하여 사용자, 디바이스 및 앱 연결  

- Windows Autopilot을 사용한 최신 프로비저닝  

- 원격 작업

이러한 공동 관리의 즉치 값에 대한 자세한 내용은 [공동 관리에 연결된 클라우드](/sccm/comanage/quickstarts)를 참조하세요.

또한 공동 관리를 통해 여러 워크로드에 맞게 Intune으로 오케스트레이션할 수 있습니다. 자세한 내용은 참조는 [워크로드](#workloads) 섹션을 참조하세요. 



## <a name="prerequisites"></a>필수 구성 요소

공동 관리에는 다음 영역에서 다음과 같은 필수 조건이 있습니다.

- [라이선스](#licensing)  
- [Configuration Manager](#configuration-manager)  
- [Azure AD(Azure Active Directory)](#azure-ad)  
- [Microsoft Intune](#intune)  
- [Windows 10](#windows-10)  
- [사용 권한 및 역할](#permissions-and-roles)  

### <a name="licensing"></a>라이선스

- Azure AD Premium 
- 모든 사용자의 EMS 또는 Intune 라이선스  

    > [!Note]  
    > EMS(Enterprise Mobility + Security) 구독에는 Azure Active Directory Premium 및 Microsoft Intune이 모두 포함되어 있습니다.

> [!Tip]  
> 테넌트에 로그인하는 데 사용하는 계정에 Intune 라이선스를 할당해야 합니다. 그러지 않으면 로그인이 실패하고 “사용자를 인식할 수 없음” 오류 메시지가 표시됩니다.  


### <a name="configuration-manager"></a>Configuration Manager

공동 관리에는 Configuration Manager 버전 1710 이상이 필요합니다.

Configuration Manager 버전 1806부터 단일 Intune 테넌트에 여러 Configuration Manager 인스턴스를 연결할 수 있습니다. <!--1357944-->  

공동 관리를 사용하도록 설정하는 것 자체와 관련해서는 사이트를 Azure AD에 등록하지 않아도 됩니다. [두 번째 경로 시나리오](#paths-to-co-management)의 경우 인터넷 기반 Configuration Manager 클라이언트에 [CMG(클라우드 관리 게이트웨이)](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)가 필요합니다. CMG를 사용하려면 사이트가 [클라우드 관리를 위해 Azure AD에 등록](/sccm/core/servers/deploy/configure/azure-services-wizard)되어 있어야 합니다. 


### <a name="azure-ad"></a>Azure AD

- Windows 10 디바이스는 Azure AD에 조인되어야 합니다. 이러한 장치는 다음 형식 중 하나일 수 있습니다.  

    - [하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan), 여기서 디바이스가 온-프레미스 Active Directory에 조인되고 Azure Active Directory에 등록됩니다.  

    - [Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)만 (이 유형은 “클라우드 도메인 연결”이라고도 함)<!--SCCMDocs issue 605-->  


### <a name="intune"></a>Intune

- [Intune 설정](https://docs.microsoft.com/intune/setup-steps)  

- [Windows 10 자동 등록을 사용하도록 설정](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)  

> [!Note]  
> 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. 그러나 사용자를 Intune 독립 실행형으로 마이그레이션하기 시작한 후 관련 Windows 10 디바이스에 공동 관리를 활성화할 수 있습니다. Intune 독립 실행형으로 마이그레이션하는 방법에 대한 자세한 정보는 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.  
> 
> [혼합 기관](/sccm/mdm/deploy-use/migrate-mixed-authority)을 사용 중인 경우 먼저 Intune 독립 실행형으로 마이그레이션을 완료합니다. 그런 다음 공동 관리를 설정하기 전에 MDM 기관을 Intune으로 설정합니다.<!--SCCMDocs issue #797-->


### <a name="windows-10"></a>Windows 10

Windows 10 버전 1709 이상으로 디바이스를 업그레이드합니다. 자세한 내용은 [Windows as a Service 채택](/sccm/core/understand/configuration-manager-and-windows-as-service#key-articles-about-adopting-windows-as-a-service)을 참조하세요.

> [!IMPORTANT]
> Windows 10 모바일 디바이스는 공동 관리를 지원하지 않습니다.


### <a name="permissions-and-roles"></a>사용 권한 및 역할
<!--SCCMDocs issue #667-->

| 작업 | 필요한 역할 |
|----|----|
| Configuration Manager에서 클라우드 관리 게이트웨이 설정 | Azure **구독 관리자** |
| Configuration Manager에서 Azure AD 앱 만들기 | Azure AD **전역 관리자** |
| Configuration Manager에서 Azure 앱 가져오기 | Configuration Manager **전체 관리자**<br>추가 Azure 역할 필요 없음 |
| Configuration Manager에서 공동 관리 사용 | Azure AD 사용자<br>**모든** 범위 권한이 있는 Configuration Manager **전체 관리자**<!--SCCMDoc issue 626--> | 

Azure 역할에 대한 자세한 내용은 [서로 다른 역할 이해하기](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles)를 참조하세요.

Configuration Manager 역할에 대한 자세한 내용은 [역할 기반 관리 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.


## <a name="workloads"></a>워크로드 

워크로드를 전환할 필요가 없거나 준비될 때 개별적으로 전환할 수 있습니다. Intune으로 전환하지 않은 워크로드를 포함한 다른 모든 워크로드와 공동 관리에서 지원하지 않는 Configuration Manager의 다른 모든 기능은 계속 Configuration Manager에서 관리합니다.

공동 관리에서는 다음 워크로드를 지원합니다.

- 규정 준수 정책  

- Windows 업데이트 정책  

- 리소스 액세스 정책  

- Endpoint Protection  

- 디바이스 구성  

- Office 간편 실행 앱  

- 클라이언트 앱  

자세한 내용은 [Workloads](/sccm/comanage/workloads)(워크로드)를 참조하세요.



## <a name="monitor-co-management"></a>공동 관리 모니터링

공동 관리 대시보드를 사용하면 사용자 환경에서 공동으로 관리되는 머신을 검토할 수 있습니다. 그래프는 주의가 필요한 디바이스를 식별하는 데 도움이 될 수 있습니다.

![공동 관리 대시보드의 스크린샷](media/co-management-dashboard.png)

자세한 내용은 [How to monitor co-management](/sccm/comanage/how-to-monitor)(공동 관리를 모니터링하는 방법)를 참조하세요.



## <a name="next-steps"></a>다음 단계

- [즉치 값에 대해 자세히 알아보고 공동 관리 시작](/sccm/comanage/quickstarts)  

- [자습서: 기존 Configuration Manager 클라이언트에 대해 공동 관리 사용](/sccm/comanage/tutorial-co-manage-clients)  

