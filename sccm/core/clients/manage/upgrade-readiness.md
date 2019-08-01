---
title: 업그레이드 준비
titleSuffix: Configuration Manager
description: 업그레이드 준비를 Configuration Manager와 통합하면 Windows 10 업그레이드 호환성 데이터와 업그레이드 또는 수정 대상 디바이스에 액세스할 수 있습니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 09/04/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4340f21ad257bfe311915edaa918e704832e3e77
ms.sourcegitcommit: 3936b869d226cea41fa0090e2cbc92bd530db03a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67286431"
---
# <a name="integrate-upgrade-readiness-with-configuration-manager"></a>업그레이드 준비와 Configuration Manager 통합

*적용 대상: System Center Configuration Manager(현재 분기)*

업그레이드 준비는 [Windows Analytics](https://docs.microsoft.com/windows/deployment/upgrade/manage-windows-upgrades-with-upgrade-readiness)의 일부로, Windows 10으로 업그레이드하기 위해 사용자 환경에서 디바이스의 준비 상태를 평가하고 분석할 수 있습니다. 업그레이드 준비를 Configuration Manager와 통합하면 Configuration Manager 콘솔에서 클라이언트 업그레이드 호환성 데이터에 액세스할 수 있습니다. 이 데이터를 사용하여 컬렉션을 생성하거나 업그레이드나 수정을 할 디바이스를 정합니다.



## <a name="configure-clients"></a>클라이언트 구성

업그레이드 준비는 Windows Analytics 데이터를 사용합니다. 업그레이드 준비에서 데이터를 충분히 받으려면 다음과 같은 필수 구성 요소를 구성하세요.

- 모든 클라이언트는 *상업용 ID 키*로 구성되어야 합니다.  

- 기본 수준 이상의 데이터를 보고하도록 Windows Analytics용 Windows 10 클라이언트 구성  

- Windows 7 또는 8.1을 실행하는 클라이언트의 경우 다음을 수행하세요.  

    - [업그레이드 준비 시작하기](https://docs.microsoft.com/windows/deployment/upgrade/upgrade-readiness-get-started)에서 설명한 대로 업데이트 설치  

    - Windows Analytics 클라이언트 설정 활성화  

구성 관리자 클라이언트 설정을 사용하여 이러한 설정을 구성합니다. 자세한 내용은 [Windows Analytics 사용](/sccm/core/clients/manage/monitor-windows-analytics)을 참조하세요.

> [!NOTE]  
> 대부분의 환경에서는 올바른 필수 구성 요소 업데이트를 배포하고 클라이언트 설정을 구성하는 것으로 충분합니다. 사용자 환경의 디바이스에서 데이터를 받지 못하는 업그레이드 준비 문제가 발생하면 [업그레이드 준비 배포 스크립트](https://docs.microsoft.com/windows/deployment/upgrade/upgrade-readiness-deployment-script)를 사용하여 이러한 문제 중 일부를 해결할 수 있습니다. 



## <a name="connect-configuration-manager-to-upgrade-readiness"></a>Configuration Manager를 업그레이드 준비에 연결

[Azure 서비스 마법사](/sccm/core/servers/deploy/configure/azure-services-wizard)를 사용하여 Configuration Manager에서 사용하도록 Azure 서비스를 구성하는 과정을 단순화할 수 있습니다. Configuration Manager와 업그레이드 준비를 연결하려면 [Azure Portal](https://portal.azure.com)에서 *웹앱/API* 유형의 Azure AD(Azure Active Directory) 앱 등록을 만듭니다. 앱 등록을 만드는 방법에 대해 자세히 알아보려면 [Azure AD 테넌트로 애플리케이션 등록](/azure/active-directory/active-directory-app-registration)을 참조하세요. 

Azure Portal에서 새로 등록된 웹앱에 다음 권한을 제공합니다.
- 업그레이드 준비 데이터와 함께 Log Analytics 작업 영역을 포함하는 리소스 그룹에 대한 *Reader* 권한
- 업그레이드 준비 데이터를 호스트하는 Log Analytics 작업 영역에 대한 *Contributor* 권한

Azure 서비스 마법사는 이 앱 등록을 사용하여 Configuration Manager에서 Azure AD와 안전하게 통신하고 업그레이드 준비 데이터에 인프라를 연결할 수 있게 합니다.

> [!IMPORTANT]  
> Azure AD 사용자 ID가 아니라, 앱 자체에 권한을 부여합니다. 이는 등록된 응용 프로그램이며 Configuration Manager 인프라를 대신하여 데이터에 액세스합니다. 권한을 부여하려면 권한을 할당할 때 **사용자 추가** 영역에서 앱 등록 이름을 검색합니다. 
> 
> 이 프로세스는 Configuration Manager에 Log Analytics에 대한 권한을 제공하는 프로세스와 동일합니다. 이러한 단계는 *Azure 서비스 마법사*를 사용하여 앱 등록을 Configuration Manager로 가져오기 전에 완료해야 합니다.
> 
> 자세한 내용은 [Log Analytics에 Configuration Manager 연결](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm)을 참조하세요.


### <a name="use-the-azure-wizard-to-create-the-connection"></a>Azure 마법사를 사용하여 연결 만들기

[Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)의 지침에 따라 위에서 만든 웹앱 등록을 가져와서 업그레이드 준비에 대한 연결을 만듭니다. 

웹앱 가져오기가 성공하고 Azure Portal에서 올바른 권한이 할당된 경우 *구성* 페이지에서 다음 값이 미리 채워집니다.   
-  Azure 구독  
-  Azure 리소스 그룹  
-  Windows Analytics 작업 영역  

두 개 이상의 리소스 그룹 또는 작업 영역은 다음과 같은 경우에 제공됩니다. 
- 등록된 Azure AD 웹앱이 두 개 이상의 리소스 그룹에 대해 *참가자* 권한을 보유할 경우   
- 선택한 리소스 그룹에 두 개 이상의 Log Analytics 작업 영역이 있을 경우  



## <a name="view-and-use-upgrade-readiness-information-in-configuration-manager"></a>Configuration Manager에서 업그레이드 준비 정보 보기 및 사용

업그레이드 준비를 Configuration Manager와 통합한 후에는 클라이언트의 업그레이드 준비 상태에 대한 분석을 확인할 수 있습니다.

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **업그레이드 준비** 노드를 선택합니다.  

2. 데이터를 검토하세요. 예:  
    - 업그레이드 준비 상태  
    - 데이터를 보고하는 Windows 디바이스의 백분율  

3. 대시보드를 필터링하여 특정 컬렉션의 디바이스에 대한 데이터를 볼 수 있습니다.  

4. 특정 준비 상태의 디바이스를 확인하고 해당 디바이스에 대한 동적 컬렉션을 만듭니다. 그런 다음 해당 컬렉션을 사용하여 디바이스를 업그레이드하거나 차단된 상태의 디바이스를 수정하는 조치를 수행합니다.  

> [!Note]  
> 이 사이트는 일주일에 한 번씩 업그레이드 준비와 데이터를 동기화합니다.<!--SCCMDocs issue 732--> 동기화를 수동으로 트리거하려면 다음을 수행하세요.
> 1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다.  
> 2. 목록에서 업그레이드 준비 연결을 선택합니다.  
> 3. 리본에서 동기화할 옵션을 선택합니다.  



## <a name="next-steps"></a>다음 단계

- [최신 버전으로 Windows 업그레이드](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)  
- [OS를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)  
- [단계별 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)  
