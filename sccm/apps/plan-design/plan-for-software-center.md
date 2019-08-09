---
title: 소프트웨어 센터 계획
titleSuffix: Configuration Manager
description: 사용자가 Configuration Manager와 상호 작용하도록 소프트웨어 센터를 구성하고 브랜딩하는 방법을 결정합니다.
ms.date: 08/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: c6826794-aa19-469d-ae47-1a0db68a1ff1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7fbd8f570fe0e6fad18b964220d5cb723e5fecad
ms.sourcegitcommit: c60fdfb9df107c430389b69b08f9670ce5f526c3
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68859858"
---
# <a name="plan-for-software-center"></a>소프트웨어 센터 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

사용자는 소프트웨어 센터에서 설정을 변경하고, 애플리케이션을 탐색하여 설치할 수 있습니다. Windows 디바이스에서 구성 관리자 클라이언트를 설치할 때 소프트웨어 센터가 자동으로 설치됩니다.

소프트웨어 센터의 다른 기능에 자세한 내용은 [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)를 참조하세요.  

## <a name="bkmk_userex"></a> 소프트웨어 센터 구성  

최신 개선 사항을 활용 하기 위해 Configuration Manager 사이트와 클라이언트를 1906 이상 버전으로 업데이트 합니다.

소프트웨어 센터에 대한 다음 개선 사항을 검토하세요.

> [!Important]  
> 소프트웨어 센터 및 관리 지점에 대한 이러한 반복적 향상은 애플리케이션 카탈로그 역할의 사용 중지를 위한 것입니다.
>
> - 현재 분기 버전 1806을 기준으로 Silverlight 사용자 환경은 지원되지 않습니다.
> - 버전 1906부터는 업데이트된 클라이언트가 사용자 이용 가능 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다.
> - 2019년 10월 31일 이후 첫 번째 현재 분기 릴리스에서는 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  

### <a name="starting-in-version-1802"></a>버전 1802부터 가능

- **컴퓨터 에이전트** 그룹에서 클라이언트 설정인 **새 소프트웨어 센터 사용**이 기본적으로 활성화됩니다. 이전 버전의 소프트웨어 센터는 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

- Azure Active Directory(Azure AD) 조인 디바이스에서 사용자가 사용할 수 있는 응용 프로그램을 찾아 설치할 수 있습니다. 자세한 내용은 [Azure AD 가입 디바이스에 사용자가 사용할 수 있는 응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)를 참조하세요.  

### <a name="starting-in-version-1806"></a>버전 1806부터 가능

- 이제 소프트웨어 센터의 **설치 상태** 탭에서 애플리케이션 카탈로그 웹 사이트 링크의 표시 여부를 지정할 수 있습니다. 자세한 내용은 [소프트웨어 센터](/sccm/core/clients/deploy/about-client-settings#software-center) 클라이언트 설정을 참조하세요.  

- 소프트웨어 센터에 사용자가 사용할 수 있는 애플리케이션을 표시하는 데 더 이상 애플리케이션 카탈로그 역할이 필요하지 않습니다. 이 변경은 사용자에게 애플리케이션을 전달하기 위해 필요한 서버 인프라를 줄일 수 있습니다. 소프트웨어 센터는 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups#management-points)에 할당하여 대규모 환경의 크기 조정을 더 잘하도록 도움을 주는 이 정보를 얻으려면 관리 지점에 의존합니다.<!--1358309-->  

    > [!Note]  
    > 현재 애플리케이션 카탈로그를 사용 중인 경우, Configuration Manager를 버전 1806으로 업데이트하면 계속 작동합니다. 애플리케이션 카탈로그 웹 사이트 지점 및 웹 서비스 지점 역할은 더 이상 *필요하지 않지만* *지원은 계속* 됩니다. 응용 프로그램 카탈로그 *웹 사이트 지점*에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.
    >
    > 이후에 인프라에서 응용 프로그램 카탈로그 역할을 제거할 계획을 시작합니다. 관리 지점을 사용할 수 있도록 소프트웨어 센터 개선 사항을 활용하고 Configuration Manager 환경을 간소화합니다.  

### <a name="starting-in-version-1902"></a>버전 1902부터 가능

- 사용자 디바이스 선호도를 구성합니다. 자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.

### <a name="starting-in-version-1906"></a>버전 1906부터 가능

- 이제 소프트웨어 센터는 사용자를 대상으로 하는 앱의 관리 지점과 통신합니다. 애플리케이션 카탈로그는 더 이상 사용하지 않습니다. 이러한 변경을 통해 사이트에서 애플리케이션 카탈로그를 보다 쉽게 제거할 수 있습니다.

- 이전에 소프트웨어 센터는 사용 가능한 서버 목록에서 첫 번째 관리 지점을 선택했습니다. 이 릴리스부터 클라이언트가 사용하는 동일한 관리 지점을 사용합니다. 이러한 변경을 통해 소프트웨어 센터에서는 클라이언트와 동일한 할당된 기본 사이트의 관리 지점을 사용할 수 있습니다.

- 관리 지점에는 이러한 새 기능을 지 원하는 소프트웨어 센터 끝점이 있습니다. 이제 5 분 마다 이러한 끝점의 상태를 확인 합니다. SMS_MP_CONTROL_MANAGER 사이트 구성 요소에 대한 상태 메시지를 통해 문제를 보고합니다.

- 새 응용 프로그램 카탈로그 역할을 사이트에 추가할 수 없습니다. 기존 역할은 계속 작동 합니다. 기존 클라이언트만 사용자가 사용할 수 있는 배포에 응용 프로그램 카탈로그를 사용 합니다. 업데이트 된 클라이언트는 모든 배포에 대해 관리 지점을 자동으로 사용 합니다.

- 소프트웨어 센터에 최대 5 개의 사용자 지정 탭을 추가할 수 있습니다. 자세한 내용은 [소프트웨어 센터 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-center)을 참조하세요. <!--4063773-->

### <a name="summary-of-infrastructure-requirements-per-version"></a>버전 당 인프라 요구 사항 요약

다음 표를 활용하여 Configuration Manager의 특정 버전에 따른 소프트웨어 센터 요구 사항을 파악합니다.

| 디바이스 유형 | 사이트 버전 | 인프라 |
|-----------------|--------------|----------------|
| Azure AD 조인 디바이스<br>(또는 “클라우드 도메인 조인”) | 1802 또는 1806 | 모든 앱 배치에 대한 관리 지점 |
| 인터넷의 [하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) 디바이스 | 1802 또는 1806 | 모든 앱 배치에 대한 클라우드 관리 게이트웨이 및 관리 지점 |
| 온-프레미스 Active Directory 도메인 조인 디바이스 | 1802 | 소프트웨어 센터를 통해 사용자가 이용할 수 있는 앱에 필요한 응용 프로그램 카탈로그 |
| 온-프레미스 Active Directory 도메인 조인 디바이스 | 1806 | 모든 앱 배치에 대한 관리 지점 |

> [!Important]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.


## <a name="bkmk_impact"></a> 알림 메시지를 대화 상자 창으로 바꾸기

<!--3555947-->
사용자가 다시 시작이나 필요한 배포에 대한 Windows 알림 메시지를 보지 못하고 지나치는 경우가 있습니다. 이 경우 알림을 반복 설정하는 기능도 보지 못하게 됩니다. 이는 클라이언트가 기한에 도달했을 때 사용자 환경을 저하할 수 있습니다.

1902 버전부터, [소프트웨어 변경이 필요하거나](#software-changes-are-required) 배포 시 [다시 시작해야 하는 경우](#restart-required) 더 확실히 표시되는 대화 상자 창을 사용할 수 있습니다.

### <a name="software-changes-are-required"></a>소프트웨어 변경 필요

향후 일정에 따라 [애플리케이션을 배포](/sccm/apps/deploy-use/deploy-applications)해야 하는 경우 소프트웨어 배포 마법사의 **사용자 환경** 페이지에서 다음 사용자 알림 옵션을 선택합니다.

- **소프트웨어 센터에 모든 알림 표시**
- **소프트웨어 변경이 필요할 때 알림 메시지 대신 사용자에게 대화 상자 창 표시**

이 시나리오에서 이 배포 설정을 구성하면 사용자 환경이 변경됩니다.

변경 전 알림 메시지:

![소프트웨어 변경이 필요하다는 알림 메시지](media/3555947-required-toast.png)  

변경 후 대화 상자 창:

![소프트웨어 변경이 필요하다는 대화 상자 창](media/3555947-required-dialog.png)


### <a name="restart-required"></a>다시 시작 필요

클라이언트 설정의 [컴퓨터 다시 시작](/sccm/core/clients/deploy/about-client-settings#computer-restart) 그룹에서 **배포를 다시 시작해야 하는 경우 알림 메시지 대신 사용자에게 대화 상자 창 표시** 옵션을 사용하도록 설정합니다.  

이 클라이언트 설정을 구성하면 다음 유형의 다시 시작이 필요한 모든 필수 배포에서 사용자 환경이 변경됩니다.

- [애플리케이션](/sccm/apps/deploy-use/deploy-applications)
- [작업 순서](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS)
- [소프트웨어 업데이트](/sccm/sum/deploy-use/deploy-software-updates)

변경 전 알림 메시지:

![다시 시작이 필요하다는 알림 메시지](media/3555947-restart-toast.png)  

변경 후 대화 상자 창:

![컴퓨터를 다시 시작하라는 대화 상자 창](media/3555947-restart-dialog.png)

> [!IMPORTANT]
> Configuration Manager 1902에서 특정 상황에서 대화 상자는 알림 메시지를 대체 하지 않습니다. 이 문제를 해결 하려면 [Configuration Manager 버전 1902에 대 한 업데이트 롤업을](https://support.microsoft.com/help/4500571/update-rollup-for-configuration-manager-current-branch-1902)설치 합니다. <!--4404715-->

## <a name="branding-software-center"></a>브랜딩 소프트웨어 센터

조직의 브랜딩 요구 사항에 맞게 소프트웨어 센터 디자인을 변경합니다. 이 구성은 사용자가 소프트웨어 센터를 신뢰하는 데 도움이 됩니다.

### <a name="configure-software-center-branding"></a>소프트웨어 센터 브랜딩 구성

<!-- 1351224 -->
조직의 브랜딩 요소를 추가하고 탭 표시 여부를 지정하여 소프트웨어 센터의 디자인을 사용자 지정합니다.

자세한 내용은 다음 아티클을 참조하세요.

- 클라이언트 설정의 [소프트웨어 센터](/sccm/core/clients/deploy/about-client-settings#software-center) 그룹  
- [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)  

### <a name="branding-priorities"></a>브랜딩 우선 순위

Configuration Manager는 다음과 같은 우선 순위에 따라 소프트웨어 센터에 대한 사용자 지정 브랜딩을 적용합니다.  

1. **소프트웨어 센터** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#software-center)를 참조하세요.  

2. **컴퓨터 에이전트** 그룹에 있는**조직 이름** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#computer-agent)를 참조하세요.  

#### <a name="application-catalog-branding-priorities"></a>응용 프로그램 카탈로그 브랜딩 우선 순위

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터는 업데이트된 클라이언트가 사용자 이용 가능 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 2019년 10월 31일 이후 첫 번째 현재 분기 릴리스에서는 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  

응용 프로그램 카탈로그를 사용 하는 경우 브랜딩은 다음 우선 순위를 따릅니다.  

1. **소프트웨어 센터** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#software-center)를 참조하세요.  

2. Microsoft Intune 구독을 Configuration Manager에 연결한 경우 소프트웨어 센터에서 Intune 구독 속성에 지정한 *조직 이름*, *색* 및 *회사 로고*를 표시합니다. 자세한 내용은 [Configuring the Microsoft Intune subscription](/sccm/mdm/deploy-use/configure-intune-subscription)을 참조하십시오.  

    > [!Important]
    > 하이브리드 모바일 디바이스 관리는 [사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)입니다.

3. 애플리케이션 카탈로그 웹 사이트 지점 속성에 지정한 *조직 이름* 및 *색*입니다. 자세한 내용은 [애플리케이션 카탈로그 웹 사이트 지점에 대한 옵션 구성](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#BKMK_ApplicationCatalog_Website)을 참조하세요.  

4. **컴퓨터 에이전트** 그룹에 있는**조직 이름** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#computer-agent)를 참조하세요.  


## <a name="see-also"></a>참고 항목

- [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)
- [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)
