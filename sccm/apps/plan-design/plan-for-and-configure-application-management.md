---
title: 애플리케이션 관리 계획
titleSuffix: Configuration Manager
description: Configuration Manager에서 애플리케이션 배포에 필요한 종속성을 구현하고 구성합니다.
ms.date: 08/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 2be84a1d-ebb9-47ae-8982-c66d5b92a52a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: df936f3ab5567840560497edd60a32f3bbb9c74d
ms.sourcegitcommit: 0d7efd9e064f9d6a9efcfa6a36fd55d4bee20059
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43893604"
---
# <a name="plan-for-and-configure-application-management-in-configuration-manager"></a>Configuration Manager에서 응용 프로그램 관리 계획 및 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 내용을 따르면 Configuration Manager에서 애플리케이션을 배포하기 위해 필요한 종속성을 구현할 수 있습니다.  



## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  


### <a name="internet-information-services-iis"></a>IIS(인터넷 정보 서비스)

다음 사이트 시스템 역할을 실행하는 서버에 IIS가 필요합니다. 
- 애플리케이션 카탈로그 웹 사이트 지점  
- 애플리케이션 카탈로그 웹 서비스 지점  
- 관리 지점  
- 배포 지점  

이 요구 사항에 대한 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.  


### <a name="certificates-on-code-signed-applications-for-mobile-devices"></a>모바일 디바이스에 대한 코드 서명 응용 프로그램의 인증서

응용 프로그램을 모바일 디바이스에 배포하기 위해 코드 서명할 경우 버전 3 템플릿(**Windows Server 2008, Enterprise Edition**)을 사용하여 생성된 인증서는 사용하지 마세요. 이 인증서 템플릿을 사용하면 모바일 디바이스용 Configuration Manager 응용 프로그램과 호환되지 않는 인증서가 만들어집니다.

모바일 디바이스 응용 프로그램에 대해 Active Directory 인증서 서비스를 사용하여 코드 서명할 경우 버전 3 인증서 템플릿은 사용하지 마세요.


### <a name="audit-sign-in-events-for-user-device-affinity"></a>사용자 디바이스 선호도에 대한 감사 로그인 이벤트  

자동으로 사용자 디바이스 선호도를 만들려면 클라이언트에서 로그인 이벤트를 감사하도록 구성해야 합니다.

구성 관리자 클라이언트는 Windows 보안 이벤트 로그에서 **성공** 유형의 로그인 이벤트를 읽어 자동 사용자 디바이스 선호도를 확인합니다. 다음 두 감사 정책에서 이러한 이벤트를 사용하도록 설정합니다.
- **계정 로그온 이벤트 감사**
- **로그온 이벤트 감사**

사용자와 디바이스 간의 관계를 자동으로 만들려면 클라이언트 컴퓨터에 이러한 두 설정이 사용하도록 설정되어 있어야 합니다. Windows 그룹 정책을 사용하여 이러한 설정을 구성할 수 있습니다.

사용자 디바이스 선호도에 대한 자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.  



## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성   


### <a name="management-point"></a>관리 지점

클라이언트는 관리 지점에 연결하여 클라이언트 정책을 다운로드하고, 콘텐츠를 찾고, 애플리케이션 카탈로그에 연결합니다. 클라이언트는 관리 지점에 액세스할 수 없는 경우 애플리케이션 카탈로그를 사용할 수 없습니다.

> [!Note]  
> 버전 1806부터 소프트웨어 센터에 사용자가 사용할 수 있는 애플리케이션을 표시하는 데 더 이상 애플리케이션 카탈로그 역할이 필요하지 않습니다. 자세한 내용은 [소프트웨어 센터 구성](#bkmk_userex)을 참조하세요.<!--1358309-->  
  

### <a name="distribution-point"></a>배포 지점

계층에 배포 지점이 하나 이상 있어야만 클라이언트에 애플리케이션을 배포할 수 있습니다. 기본적으로 사이트 서버에는 표준 설치 중 활성화된 배포 지점 사이트 역할이 있습니다. 배포 지점의 수와 위치는 각 환경의 특정 요구 사항에 따라 달라집니다. 

배포 지점을 설치하고 콘텐츠를 관리하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  


### <a name="reporting-services-point"></a>보고 서비스 지점

애플리케이션 관리를 위해 Configuration Manager에서 보고서를 사용하려면 먼저 보고 서비스 지점을 설치하고 구성해야 합니다.

자세한 내용은 [Configuration Manager의 보고 기능](/sccm/core/servers/manage/reporting)을 참조하세요.  


### <a name="client-settings"></a>클라이언트 설정

많은 클라이언트 설정은 클라이언트가 디바이스에 응용 프로그램 및 사용자 환경을 설치하는 방법을 제어합니다. 이러한 클라이언트 설정은 다음 그룹과 같습니다.
- 컴퓨터 에이전트  
- 컴퓨터 다시 시작  
- 소프트웨어 센터  
- 소프트웨어 배포  
- 사용자 및 디바이스 선호도  

자세한 내용은 다음 아티클을 참조하세요.
- [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings)  
- [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)  


### <a name="security-permissions-for-application-management"></a>애플리케이션 관리를 위한 보안 권한

- **응용 프로그램 작성자** 보안 역할에는 응용 프로그램을 만들고, 수정하고, 사용 중지하는 데 필요한 권한이 포함되어 있습니다.  

- **응용 프로그램 배포 관리자** 보안 역할에는 응용 프로그램을 배포하는 데 필요한 권한이 포함되어 있습니다.  

- **응용 프로그램 관리자** 보안 역할에는 **응용 프로그램 작성자** 및 **응용 프로그램 배포 관리자** 보안 역할의 모든 권한이 포함되어 있습니다.  

자세한 내용은 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요.  


### <a name="app-v-46-sp1-or-later-client-to-run-virtual-applications"></a>가상 애플리케이션 실행을 위한 App-V 4.6 SP1 이상의 클라이언트

Configuration Manager에서 가상 응용 프로그램을 만들려면 디바이스에 App-V 4.6 SP1 이상이 설치되어 있어야 합니다.

또한 가상 애플리케이션을 배포하려면 [Microsoft 지원 문서 2645225](https://support.microsoft.com/help/2645225)에 설명된 핫픽스로 App-V 클라이언트를 업데이트해야 합니다.  


### <a name="discovered-user-accounts-for-application-catalog"></a>애플리케이션 카탈로그에 대해 검색된 사용자 계정

사용자가 애플리케이션 카탈로그에서 애플리케이션을 확인하고 요청하려면 먼저 Configuration Manager에서 해당 사용자 계정을 검색해야 합니다. 자세한 내용은 [검색 실행](/sccm/core/servers/deploy/configure/run-discovery)을 참조하세요.  


### <a name="application-catalog-web-service-point"></a>애플리케이션 카탈로그 웹 서비스 지점

애플리케이션 카탈로그 웹 서비스 지점은 소프트웨어 라이브러리의 사용 가능한 소프트웨어에 대한 정보를 사용자가 액세스하는 애플리케이션 카탈로그 웹 사이트에 제공하는 사이트 시스템 역할입니다.

이 사이트 시스템 역할을 구성하는 방법에 대한 자세한 내용은 [소프트웨어 센터 구성](#bkmk_userex)을 참조하세요.  

> [!Note]  
> 버전 1806부터 응용 프로그램 카탈로그 웹 서비스 지점 역할은 더 이상 *필요하지 않지만* *지원은 계속됩니다*.<!--1358309-->  
> 
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  


### <a name="application-catalog-website-point"></a>애플리케이션 카탈로그 웹 사이트 지점

애플리케이션 카탈로그 웹 사이트 지점은 사용자에게 사용 가능한 소프트웨어 목록을 제공하는 사이트 시스템 역할입니다.
이 사이트 시스템 역할을 구성하는 방법에 대한 자세한 내용은 [소프트웨어 센터 구성](#bkmk_userex)을 참조하세요.

> [!Note]  
> 버전 1806부터 응용 프로그램 카탈로그 웹 사이트 지점 역할은 더 이상 *필요하지 않지만* *지원은 계속됩니다*.<!--1358309-->  
> 
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  



## <a name="bkmk_userex"></a> 소프트웨어 센터 구성  

사용자는 소프트웨어 센터에서 설정을 변경하고, 애플리케이션을 탐색하여 설치할 수 있습니다. Windows 디바이스에서 구성 관리자 클라이언트를 설치할 때 소프트웨어 센터가 자동으로 설치됩니다. 소프트웨어 센터가 새로운 세련된 디자인으로 바뀌었습니다. 이전에는 Silverlight 종속 애플리케이션 카탈로그에서만 표시되었던 앱(사용자가 사용할 수 있는 앱)이 이제 소프트웨어 센터의 **애플리케이션** 탭 아래에 표시됩니다. 소프트웨어 센터의 다른 기능에 자세한 내용은 [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)를 참조하세요.  

소프트웨어 센터에 대한 다음 개선 사항을 검토하세요. 

#### <a name="starting-in-version-1802"></a>버전 1802부터 가능

- **컴퓨터 에이전트** 그룹에서 클라이언트 설정인 **새 소프트웨어 센터 사용**이 기본적으로 활성화됩니다. 이전 버전의 소프트웨어 센터는 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

- Azure Active Directory(Azure AD) 조인 디바이스에서 사용자가 사용할 수 있는 응용 프로그램을 찾아 설치할 수 있습니다. 자세한 내용은 [Azure AD 가입 디바이스에 사용자가 사용할 수 있는 응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)를 참조하세요.  

#### <a name="starting-in-version-1806"></a>버전 1806부터 가능

- 이제 소프트웨어 센터의 **설치 상태** 탭에서 애플리케이션 카탈로그 웹 사이트 링크의 표시 여부를 지정할 수 있습니다. 자세한 내용은 [소프트웨어 센터](/sccm/core/clients/deploy/about-client-settings#software-center) 클라이언트 설정을 참조하세요.  

- 소프트웨어 센터에 사용자가 사용할 수 있는 애플리케이션을 표시하는 데 더 이상 애플리케이션 카탈로그 역할이 필요하지 않습니다. 이 변경은 사용자에게 애플리케이션을 전달하기 위해 필요한 서버 인프라를 줄일 수 있습니다. 소프트웨어 센터는 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups#management-points)에 할당하여 대규모 환경의 크기 조정을 더 잘하도록 도움을 주는 이 정보를 얻으려면 관리 지점에 의존합니다.<!--1358309-->  

    > [!Note]  
    > 현재 애플리케이션 카탈로그를 사용 중인 경우, Configuration Manager를 버전 1806으로 업데이트하면 계속 작동합니다. 응용 프로그램 카탈로그 웹 사이트 지점 및 웹 서비스 지점 역할은 더 이상 *필요하지 않지만* *지원은 계속*됩니다. 애플리케이션 카탈로그 *웹 사이트 지점*에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요. 
    > 
    > 이후에 인프라에서 애플리케이션 카탈로그 역할을 제거할 계획을 시작합니다. 관리 지점을 사용할 수 있도록 소프트웨어 센터 개선 사항을 활용하고 Configuration Manager 환경을 간소화합니다.  

다음 표를 활용하여 Configuration Manager의 특정 버전에 따른 소프트웨어 센터 요구 사항을 파악합니다.

| 디바이스 유형 | 사이트 버전 | 인프라 | 
|-----------------|--------------|----------------|
| Azure AD 조인 디바이스</br>(또는 “클라우드 도메인 조인”) | 1802 또는 1806 | 모든 앱 배치에 대한 관리 지점 | 
| 인터넷의 [하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) 장치 | 1802 또는 1806 | 모든 앱 배치에 대한 클라우드 관리 게이트웨이 및 관리 지점 |
| 온-프레미스 Active Directory 도메인 조인 디바이스 | 1802 | 소프트웨어 센터를 통해 사용자가 이용할 수 있는 앱에 필요한 애플리케이션 카탈로그 |
| 온-프레미스 Active Directory 도메인 조인 디바이스 | 1806 | 모든 앱 배치에 대한 관리 지점 |


> [!Important]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.



## <a name="branding-software-center"></a>브랜딩 소프트웨어 센터

조직의 브랜딩 요구 사항에 맞게 소프트웨어 센터 디자인을 변경합니다. 이 구성은 사용자가 소프트웨어 센터를 신뢰하는 데 도움이 됩니다. 

Configuration Manager는 다음과 같은 우선 순위에 따라 소프트웨어 센터에 대한 사용자 지정 브랜딩을 적용합니다.  

- 애플리케이션 카탈로그를 설치하지 않은 경우(권장):  

    1. **소프트웨어 센터** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#software-center)를 참조하세요.  

    2. **컴퓨터 에이전트** 그룹에 있는**조직 이름** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#computer-agent)를 참조하세요.  

- 애플리케이션 카탈로그를 설치한 경우:  

    1. **소프트웨어 센터** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#software-center)를 참조하세요.  

    2. Microsoft Intune 구독을 Configuration Manager에 연결한 경우 소프트웨어 센터에서 Intune 구독 속성에 지정한 *조직 이름*, *색* 및 *회사 로고*를 표시합니다. 자세한 내용은 [Configuring the Microsoft Intune subscription](/sccm/mdm/deploy-use/configure-intune-subscription)을 참조하십시오.  

    3. 애플리케이션 카탈로그 웹 사이트 지점 속성에 지정한 *조직 이름* 및 *색*입니다. 자세한 내용은 [애플리케이션 카탈로그 웹 사이트 지점에 대한 옵션 구성](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#BKMK_ApplicationCatalog_Website)을 참조하세요.  

    4. **컴퓨터 에이전트** 그룹에 있는**조직 이름** 클라이언트 설정. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#computer-agent)를 참조하세요.  

#### <a name="configure-software-center-branding"></a>소프트웨어 센터 브랜딩 구성
<!-- 1351224 --> 조직의 브랜딩 요소를 추가하고 탭 표시 여부를 지정하여 소프트웨어 센터의 디자인을 사용자 지정합니다. 

자세한 내용은 다음 아티클을 참조하세요.
- 클라이언트 설정의 [소프트웨어 센터](/sccm/core/clients/deploy/about-client-settings#software-center) 그룹  
- [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)  



## <a name="bkmk_appcat"> </a> 응용 프로그램 카탈로그 설치 및 구성  

> [!Note]  
> 버전 1806부터 응용 프로그램 카탈로그 웹 사이트 지점 및 웹 서비스 지점은 더 이상 *필요하지 않지만* *지원은 계속*됩니다. 자세한 내용은 [소프트웨어 센터 구성](#bkmk_userex)을 참조하세요.  
> 
> 애플리케이션 카탈로그 *웹 사이트 지점*에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

> [!IMPORTANT]  
>  이러한 단계를 수행하기 전에 모든 종속성이 제 위치에 있는지 확인하세요. 자세한 내용은 이 문서에서 다음 섹션을 참조하세요.
> - [Configuration Manager 외부 종속성](#dependencies-external-to-configuration-manager)  
> - [Configuration Manager 종속성](#configuration-manager-dependencies)


### <a name="step-1-web-server-certificate-for-https"></a>1단계: HTTPS에 대한 웹 서버 인증서

HTTPS 연결을 사용하는 경우 애플리케이션 카탈로그 웹 사이트 지점 및 애플리케이션 카탈로그 웹 서비스 지점에 대한 사이트 시스템 서버에 웹 서버 인증서를 배포합니다. 

클라이언트가 인터넷에서 애플리케이션 카탈로그를 사용하도록 하려면 적어도 하나 이상의 관리 지점에 웹 서버 인증서를 배포합니다. 인터넷에서 클라이언트 연결에 맞게 구성하세요.

인증서 요구 사항에 대한 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  


### <a name="step-2-client-authentication-certificate-for-https"></a>2단계: HTTPS에 대한 클라이언트 인증 인증서

관리 지점에 연결하는 데 클라이언트 PKI 인증서를 사용하려면 클라이언트 컴퓨터에 클라이언트 인증 인증서를 배포합니다. 클라이언트는 애플리케이션 카탈로그에 연결하기 위해 클라이언트 PKI 인증서를 사용하지 않지만, 관리 지점에 연결해야 애플리케이션 카탈로그를 사용할 수 있습니다. 

다음 시나리오에서는 클라이언트 컴퓨터에 클라이언트 인증 인증서를 배포합니다.
- 인트라넷의 모든 관리 지점에서 HTTPS 클라이언트 연결만 허용합니다.
- 클라이언트가 인터넷에서 애플리케이션 카탈로그에 연결합니다.

인증서 요구 사항에 대한 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  


### <a name="step-3-install-and-configure-the-application-catalog-roles"></a>3단계: 애플리케이션 카탈로그 역할 설치 및 구성

동일한 사이트에 애플리케이션 카탈로그 웹 서비스 지점 및 애플리케이션 카탈로그 웹 사이트 역할을 모두 설치합니다. 같은 서버나 같은 Active Directory 포리스트에 설치할 필요는 없습니다. 그러나 애플리케이션 카탈로그 웹 서비스 지점은 사이트 데이터베이스와 같은 포리스트에 있어야 합니다.

서버 배치에 대한 자세한 내용은 [사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](/sccm/core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles)을 참조하세요.

> [!NOTE]  
> 기본 사이트에 애플리케이션 카탈로그를 설치합니다. 보조 사이트 또는 중앙 관리 사이트에 설치할 수 없습니다.  

새 사이트 시스템 서버 또는 사이트의 기존 서버에 애플리케이션 카탈로그를 설치합니다. 일반 프로시저에 대한 자세한 내용은 [사이트 시스템 역할 설치](/sccm/core/servers/deploy/configure/install-site-system-roles)를 참조하세요. 마법사에서 사이트 시스템 역할을 추가하거나 사이트 시스템 서버를 만들려면 목록에서 다음 역할을 선택합니다.  
- **응용 프로그램 카탈로그 웹 서비스 지점**  
- **응용 프로그램 카탈로그 웹 사이트 지점**  

> [!TIP]  
>  클라이언트 컴퓨터에서 인터넷을 통해 애플리케이션 카탈로그를 사용하도록 하려면 인터넷 FQDN(정규화된 도메인 이름)을 지정합니다.  

#### <a name="verify-the-installation-of-these-site-system-roles"></a>이러한 사이트 시스템 역할 설치를 확인하세요.  

- 상태 메시지: **SMS_PORTALWEB_CONTROL_MANAGER** 및 **SMS_AWEBSVC_CONTROL_MANAGER**구성 요소를 사용합니다.  

    예를 들어 **SMS_PORTALWEB_CONTROL_MANAGER**의 상태 ID **1015**는 사이트 구성 요소 관리자가 애플리케이션 카탈로그 웹 사이트 지점을 설치했음을 확인합니다.  

- 로그 파일: **SMSAWEBSVCSetup.log** 및 **SMSPORTALWEBSetup.log**를 검색합니다.  

    자세한 내용을 보려면 **awebsvcMSI.log** 및 **portlwebMSI.log** 로그 파일을 검색하세요.  


### <a name="step-4-configure-client-settings"></a>4단계: 클라이언트 설정 구성

모든 사용자가 같은 설정을 사용하도록 하려면 기본 클라이언트 설정을 구성합니다. 아니면 특정 컬렉션에 대한 사용자 지정 클라이언트 설정을 구성합니다.

자세한 내용은 다음 아티클을 참조하세요.
- [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings)  
    - 컴퓨터 에이전트  
    - 컴퓨터 다시 시작  
    - 소프트웨어 센터  
    - 소프트웨어 배포  
    - 사용자 및 디바이스 선호도  
- [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)  

구성 관리자 클라이언트는 다음에 클라이언트 정책을 다운로드할 때 이러한 설정으로 디바이스를 구성합니다. 단일 클라이언트에 대한 정책 검색을 트리거하려면 [클라이언트를 관리하는 방법](/sccm/core/clients/manage/manage-clients)을 참조하세요.


### <a name="step-5-verify-that-the-application-catalog-is-operational"></a>5단계: 애플리케이션 카탈로그가 작동하는지 확인

애플리케이션 카탈로그가 작동하는지 확인하려면 다음 절차를 수행하세요. 

> [!NOTE]  
>  애플리케이션 카탈로그 사용자 환경에는 Microsoft Silverlight가 필요합니다. 브라우저에서 직접 애플리케이션 카탈로그를 사용하는 경우 먼저 컴퓨터에 Microsoft Silverlight가 설치되어 있는지 확인하세요.  

> [!TIP]  
>  설치 후에 애플리케이션 카탈로그가 잘못된 방식으로 작동하는 원인 중 가장 일반적인 원인은 필수 구성 요소가 누락되었기 때문입니다. 애플리케이션 카탈로그 역할의 사이트 시스템 역할 필수 구성 요소를 확인합니다. 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.  

브라우저에서 애플리케이션 카탈로그 웹 사이트의 주소를 입력합니다. 해당 웹 페이지에 **응용 프로그램 카탈로그**, **내 응용 프로그램 요청**, **내 디바이스** 등 세 가지 탭이 표시되는지 확인합니다.  

애플리케이션 카탈로그에 대해 아래 목록에 나와 있는 적합한 주소를 사용합니다. 여기서 &lt;서버&gt;는 컴퓨터 이름, 인트라넷 FQDN 또는 인터넷 FQDN입니다.  

- HTTPS 클라이언트 연결 및 기본 사이트 시스템 역할 설정: **https://&lt;서버&gt;/CMApplicationCatalog**  

- HTTP 클라이언트 연결 및 기본 사이트 시스템 역할 설정: **http://&lt;서버&gt;/CMApplicationCatalog**  

- HTTPS 클라이언트 연결 및 사용자 지정 사이트 시스템 역할 설정: **https://&lt;서버&gt;:&lt;포트&gt;/&lt;웹 애플리케이션 이름&gt;**  

- HTTP 클라이언트 연결 및 사용자 지정 사이트 시스템 역할 설정: **http://&lt;서버&gt;:&lt;포트&gt;/&lt;웹 애플리케이션 이름&gt;**  

> [!NOTE]  
>  도메인 관리자 계정으로 디바이스에 로그인하는 경우, 구성 관리자 클라이언트는 알림 메시지를 표시하지 않습니다. 예를 들어, 새 소프트웨어를 사용할 수 있음을 나타내는 메시지가 있습니다.  

