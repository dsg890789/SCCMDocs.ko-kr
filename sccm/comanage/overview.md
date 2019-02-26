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
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755373"
---
# <a name="what-is-co-management"></a>공동 관리란?

<!-- 1350871 --> 공동 관리에는 Microsoft 365 클라우드로 기존 Configuration Manager 배포를 연결 하는 기본 방법 중 하나입니다. 조건부 액세스와 같은 추가 클라우드 기반 기능을 잠금 해제 수 있습니다. 

공동 관리를 사용 하면 동시에 Configuration Manager 및 Microsoft Intune을 사용 하 여 Windows 10 장치를 관리할 수 있습니다. 새로운 기능을 추가 하 여 기존 투자 Configuration Manager에서 클라우드-연결할 수 있습니다. 공동 관리를 사용 하 여 유연성을 조직에 가장 적합 한 기술 솔루션을 사용 해야 합니다. 

Windows 10 장치에 Configuration Manager 클라이언트를 Intune에 등록 되는 경우 두 서비스의 이점을 얻게 됩니다. 있는 경우 기관을 Configuration Manager에서 Intune로 전환 하는 워크 로드를 제어 합니다. Configuration Manager가 계속 모든 다른 워크 로드를 Intune로 전환 하지 않습니다 하 고 다른 모든 기능은 Configuration Manager 공동 관리를 지원 하지 않습니다는 해당 워크 로드를 포함 하 여 관리.

장치는 별도 컬렉션을 사용 하 여 작업을 파일럿 할 하기도 합니다. 파일럿 실행을 사용 하면 대규모 그룹을 전환 하기 전에 장치의 하위 집합을 사용 하 여 Intune 기능을 테스트할 수 있습니다. 

![공동 관리의 개요 다이어그램](media/co-management-overview.png)



## <a name="paths-to-co-management"></a>공동 관리 경로

공동 관리에 연결하기 위한 두 가지 주요 경로가 있습니다.  

- **기존 Configuration Manager 클라이언트**: Windows 10 장치에 Configuration Manager 클라이언트 포함 되어 있습니다. 하이브리드 Azure AD 설정 하 고 Intune에 등록 합니다.  

- **새로운 인터넷 기반 장치**: 새 Windows 10 장치를 Azure AD에 가입 및 Intune에 자동으로 등록 해야 합니다. 공동 관리 상태에 연결할 Configuration Manager 클라이언트를 설치할 수 있습니다.  

경로 대 한 자세한 내용은 참조 하세요. [공동 관리에 대 한 경로](/sccm/comanage/quickstart-paths)합니다.



## <a name="benefits"></a>이점 

공동 관리에서 기존 Configuration Manager 클라이언트를 등록 하면 다음 즉시 값을 얻을 수 있습니다.  

- 장치 준수를 사용 하 여 조건부 액세스  

- Intune 기반 원격 작업, 예: 다시 시작, 원격 제어 나 공장 기본 설정

- 장치 상태의 중앙 집중식된 가시성  

- 사용자, 장치 및 Azure Active Directory (Azure AD)를 사용 하 여 앱 연결  

- 최신 Windows Autopilot을 사용 하 여 프로 비전  

- 원격 작업

이 즉 치 값 공동 관리에서에 대 한 자세한 내용은 빠른 시작 시리즈를 참조 하세요 [공동 관리를 사용 하 여 클라우드 연결](/sccm/comanage/quickstarts)합니다.

공동 관리를 사용 하면 여러 워크 로드에 대 한 Intune을 사용 하 여 오케스트레이션 할 수 있습니다. 자세한 내용은 참조는 [워크 로드](#workloads) 섹션입니다. 



## <a name="prerequisites"></a>필수 구성 요소

공동 관리는 다음 영역에서 이러한 필수 구성이 요소를 가집니다.

- [라이선스](#licensing)  
- [Configuration Manager](#configuration-manager)  
- [Azure Active Directory](#azure-ad) (Azure AD)  
- [Microsoft Intune](#intune)  
- [Windows 10](#windows-10)  
- [사용 권한 및 역할](#permissions-and-roles)  

### <a name="licensing"></a>라이선스

- Azure AD Premium 
- 모든 사용자의 EMS 또는 Intune 라이선스  

    > [!Note]  
    > Enterprise Mobility + Security (EMS) 구독에 Azure Active Directory Premium 및 Microsoft Intune을 모두 포함 됩니다.

> [!Tip]  
> 테 넌 트에 로그인 하는 데 사용 하는 계정에 Intune 라이선스를 할당 했는지 확인 합니다. 그렇지 않은 경우 "User 인식할 수 없습니다" 오류 메시지와 함께 실패에 로그인 합니다.  


### <a name="configuration-manager"></a>Configuration Manager

공동 관리는 Configuration Manager 버전 1710 이상 필요합니다.

Configuration Manager 버전 1806부터 여러 Configuration Manager 인스턴스를 단일 Intune 테 넌 트에 연결할 수 있습니다. <!--1357944-->  

자체 공동 관리를 사용 하도록 설정 하지 않아도 해당 온 보 딩 할 Azure AD 사용 하 여 사이트입니다. 에 대 한 합니다 [두 번째 경로 시나리오](#paths-to-co-management), 인터넷 기반 Configuration Manager 클라이언트에 필요 합니다 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway) (CMG). CMG 사이트가 필요 [클라우드 관리를 위한 Azure AD에 온 보 딩](/sccm/core/servers/deploy/configure/azure-services-wizard)합니다. 


### <a name="azure-ad"></a>Azure AD

- Windows 10 디바이스는 Azure AD에 조인되어야 합니다. 이러한 장치는 다음 형식 중 하나일 수 있습니다.  

    - [하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan), 여기서 디바이스가 온-프레미스 Active Directory에 조인되고 Azure Active Directory에 등록됩니다.  

    - [Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)만 (이 유형은 "클라우드 도메인 조인"이라고도 함)<!--SCCMDocs issue 605-->  


### <a name="intune"></a>Intune

- [Intune 설정](https://docs.microsoft.com/intune/setup-steps)  

- [Windows 10 자동 등록 사용](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)  

> [!Note]  
> 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. 그러나 사용자를 Intune 독립 실행형으로 마이그레이션하기 시작한 후 관련 Windows 10 디바이스에 공동 관리를 활성화할 수 있습니다. Intune 독립 실행형으로 마이그레이션하는 방법에 대한 자세한 정보는 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.  
> 
> [혼합 기관](/sccm/mdm/deploy-use/migrate-mixed-authority)을 사용 중인 경우 먼저 Intune 독립 실행형으로 마이그레이션을 완료합니다. 그런 다음, 공동 관리를 설정하기 전에 MDM 기관을 Intune으로 설정합니다.<!--SCCMDocs issue #797-->


### <a name="windows-10"></a>Windows 10

Windows 10 버전 1709 이상에 장치를 업그레이드 합니다. 자세한 내용은 [서비스로 Windows 채택](/sccm/core/understand/configuration-manager-and-windows-as-service#key-articles-about-adopting-windows-as-a-service)합니다.

> [!IMPORTANT]
> Windows 10 mobile 장치는 공동 관리를 지원 하지 않습니다.


### <a name="permissions-and-roles"></a>사용 권한 및 역할
<!--SCCMDocs issue #667-->

| 작업 | 필요한 역할 |
|----|----|
| Configuration Manager에서 클라우드 관리 게이트웨이 설정 | Azure **구독 관리자** |
| Configuration Manager에서 Azure AD 앱 만들기 | Azure AD **전역 관리자** |
| Configuration Manager에서 Azure 앱 가져오기 | Configuration Manager **전체 관리자**<br>필요 없는 추가 Azure 역할 |
| Configuration Manager에서 공동 관리를 사용 하도록 설정 | Azure AD 사용자<br>Configuration Manager **전체 관리자** 사용 하 여 **모든** 권한 범위입니다.<!--SCCMDoc issue 626--> | 

Azure 역할에 대한 자세한 내용은 [서로 다른 역할 이해하기](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles)를 참조하세요.

Configuration Manager 역할에 대 한 자세한 내용은 참조 하세요. [의 역할 기반 관리 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)합니다.


## <a name="workloads"></a>워크로드 

워크 로드를 전환 하지 않아도 됩니다. 또는 준비 된 경우 개별적으로 수행할 수 있습니다. Configuration Manager가 계속 모든 다른 워크 로드를 Intune로 전환 하지 않습니다 하 고 다른 모든 기능은 Configuration Manager 공동 관리를 지원 하지 않습니다는 해당 워크 로드를 포함 하 여 관리.

공동 관리는 다음 워크 로드를 지원합니다.

- 규정 준수 정책  

- Windows 업데이트 정책  

- 리소스 액세스 정책  

- Endpoint Protection  

- 디바이스 구성  

- Office 간편 실행 앱  

- 클라이언트 앱  

자세한 내용은 [워크 로드](/sccm/comanage/workloads)합니다.



## <a name="monitor-co-management"></a>공동 관리 모니터링

공동 관리 대시보드를 사용 하면 사용자 환경에서 공동 관리 되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 디바이스를 식별하는 데 도움이 될 수 있습니다.

![공동 관리 대시보드의 스크린 샷](media/co-management-dashboard.png)

자세한 내용은 [공동 관리를 모니터링 하는 방법](/sccm/comanage/how-to-monitor)합니다.



## <a name="next-steps"></a>다음 단계

- [즉 치 값 공동 관리를 사용 하 여 시작 및 자세히 알아보기](/sccm/comanage/quickstarts)  

- [자습서: 기존 Configuration Manager 클라이언트에 대 한 공동 관리를 사용 하도록 설정](/sccm/comanage/tutorial-co-manage-clients)  

