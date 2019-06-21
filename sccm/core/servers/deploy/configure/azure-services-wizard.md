---
title: Azure 서비스 구성
titleSuffix: Configuration Manager
description: Configuration Manager 환경을 클라우드 관리, 업그레이드 준비, 비즈니스용 Microsoft 스토어, Log Analytics를 위한 Azure 서비스와 연결합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a26a653e-17aa-43eb-ab36-0e36c7d29f49
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6d7acf1d5c73c59f2ce1e6d2b7f3f7354e21979
ms.sourcegitcommit: 86968fc2f129e404ff8e08f91a05fa17b5c47527
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67251882"
---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Configuration Manager에서 사용하도록 Azure 서비스 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

**Azure 서비스 마법사**를 사용하여 Configuration Manager에서 사용하도록 Azure 서비스를 구성하는 과정을 단순화할 수 있습니다. 이 마법사는 Azure AD(Azure Active Directory) 웹앱 등록을 사용하여 일반적인 구성 환경을 제공합니다. 이러한 앱은 구독 및 구성 세부 정보를 제공하고 Azure AD와의 통신을 인증합니다. 이 앱을 사용하면 Azure에서 새 Configuration Manager 구성 요소 또는 서비스를 설정할 때마다 같은 정보를 입력하지 않아도 됩니다.



## <a name="available-services"></a>사용 가능한 서비스

이 마법사를 사용하여 다음과 같은 Azure 서비스를 구성합니다.  

-   **클라우드 관리**: 이 서비스를 사용하면 Azure AD를 사용하여 사이트 및 클라이언트를 인증할 수 있습니다. 이 인증은 다음과 같은 다른 시나리오를 지원합니다.  

    - [인증을 위해 Azure AD를 사용하여 Configuration Manager Windows 10 클라이언트 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)  

    - [Azure AD 사용자 검색 구성](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

    - 특정 [클라우드 관리 게이트웨이 시나리오](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#scenarios) 지원  

-   **Log Analytics 커넥터**: [Azure Log Analytics에 연결합니다](/sccm/core/clients/manage/sync-data-log-analytics). 컬렉션 데이터를 Log Analytics에 동기화합니다.  

    > [!Note]  
    > 이 문서는 *Log Analytics 커넥터*(이전의 *OMS 커넥터*)를 참조합니다. 기능 차이는 없습니다. 자세한 내용은 [Azure 관리 - 모니터링](/azure/azure-monitor/terminology#log-analytics)을 참조하세요.  

-   **업그레이드 준비 커넥터**: Windows Analytics [업그레이드 준비](/sccm/core/clients/manage/upgrade/upgrade-analytics)에 연결합니다. 클라이언트 업그레이드 호환성 데이터를 봅니다.  

-   **비즈니스용 Microsoft Store**: [비즈니스용 Microsoft Store](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)에 연결합니다. Configuration Manager와 함께 배포할 수 있는 조직용 스토어 앱을 가져옵니다.  

### <a name="service-details"></a>서비스 정보

다음 표에는 각 서비스에 대한 세부 정보가 나열되어 있습니다.  

- **테넌트**: 구성할 수 있는 서비스 인스턴스 수. 각 인스턴스는 서로 다른 Azure 테넌트여야 합니다.  

- **클라우드**: 모든 서비스가 전역 Azure 클라우드를 지원하지만, 일부 서비스는 Azure 미국 정부 클라우드 같은 프라이빗 클라우드를 지원하지 않습니다.  

- **웹앱**: 서비스에서 *웹앱/API* 형식의 Azure AD 앱을 사용하는지 여부를 나타내며, Configuration Manager에서는 서버 앱이라고도 합니다.  

- **네이티브 앱**: 서비스에서 *네이티브* 형식의 Azure AD 앱을 사용하는지 여부를 나타내며, Configuration Manager에서는 클라이언트 앱이라고도 합니다.  

- **작업**: Configuration Manager Azure 서비스 마법사에서 이러한 앱을 가져오거나 만들 수 있는지 여부를 나타냅니다.  


|서비스  |테넌트  |클라우드  |웹앱  |네이티브 앱  |작업  |
|---------|---------|---------|---------|---------|---------|
|클라우드 관리 수단<br>Azure AD 사용자 검색 | 여러 개 | 퍼블릭, 프라이빗 | ![지원됨](media/green_check.png) | ![지원됨](media/green_check.png) | 가져오기, 만들기 |
|Log Analytics 커넥터 | 하나 | 퍼블릭, 프라이빗 | ![지원됨](media/green_check.png) | ![지원되지 않음](media/Red_X.png) | 가져오기 |
|업그레이드 준비 | 하나 | 공용 | ![지원됨](media/green_check.png) | ![지원되지 않음](media/Red_X.png) | 가져오기 |
|비즈니스 및 교육용<br>비즈니스 | 하나 | 공용 | ![지원됨](media/green_check.png) | ![지원되지 않음](media/Red_X.png) | 가져오기, 만들기 |


### <a name="about-azure-ad-apps"></a>Azure AD 앱 정보

Azure 서비스마다 고유의 구성이 필요하며, Azure Portal에서 만들 수 있습니다. 또한 각 서비스에 대한 앱은 Azure 리소스에 대한 별도의 권한이 필요할 수 있습니다.  

하나를 초과하는 서비스에 단일 앱을 사용할 수 있습니다. Configuration Manager와 Azure AD에는 관리할 개체가 하나밖에 없습니다. 앱의 보안 키가 만료되면 키를 새로 고치기만 하면 됩니다.

<!-- The most secure configuration is using separate apps for each service. An app for one service might require additional permissions that another service doesn't require. Using one app for different services can provide the app with more permissions than it otherwise requires. 
 --> 

마법사에서 추가 Azure 서비스를 만들 때 Configuration Manager는 서비스 간의 공통 정보를 다시 사용하도록 설계 되었습니다. 이 동작 덕분에 동일한 정보를 한 번을 초과해서 입력할 필요가 없습니다. 

각 서비스에 필요한 앱 권한 및 구성에 대한 자세한 내용은 [사용 가능한 서비스](#available-services)에서 관련 Configuration Manager 문서를 참조하세요. 

Azure 앱에 대한 자세한 내용은 다음 문서부터 참조하세요.
- [Azure App Service의 인증 및 권한 부여](/azure/app-service/app-service-authentication-overview)
- [Web Apps 개요](/azure/app-service-web/app-service-web-overview)
- [Azure AD에서 애플리케이션 등록의 기본 사항](/azure/active-directory/develop/authentication-scenarios#authentication-basics-in-microsoft-identity-platform)  
- [Azure Active Directory 테넌트에 애플리케이션 등록](/azure/active-directory/active-directory-app-registration)



## <a name="before-you-begin"></a>시작하기 전에

연결할 서비스를 결정했으면 [서비스 정보](#service-details)의 표를 참조하세요. 이 표는 Azure 서비스 마법사를 완료하는 데 필요한 정보를 제공합니다. Azure AD 관리자와 미리 토론합니다. 수행할 다음 작업을 결정합니다. 

- Azure Portal에서 미리 수동으로 앱을 만듭니다. 그런 다음, Configuration Manager로 앱 세부 정보를 가져옵니다.  

- Configuration Manager를 사용하여 Azure AD에서 직접 앱을 만듭니다. Azure AD에서 필요한 데이터를 수집하려면 이 문서의 다른 섹션에서 제공하는 정보도 검토합니다.  

일부 서비스는 Azure AD 앱에 특정 권한이 필요합니다. 각 서비스에 대한 정보를 검토하여 필요한 권한을 확인하세요. 예를 들어 웹앱을 가져오려면 먼저 Azure 관리자가 [Azure Portal](https://portal.azure.com)에서 웹앱을 만들어야 합니다. 

업그레이드 준비 또는 Log Analytics 커넥터를 구성할 때 관련 작업 영역이 포함된 리소스 그룹에 새로 등록된 웹앱 *기여자* 권한을 부여합니다. 이 권한이 있으면 Configuration Manager가 해당 작업 영역에 액세스할 수 있습니다. 권한을 할당할 때 Azure Portal의 **사용자 추가** 영역에서 앱 등록 이름을 검색합니다. 이 프로세스는 [Configuration Manager에 Log Analytics에 대한 권한을 제공](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#grant-configuration-manager-with-permissions-to-log-analytics)하는 프로세스와 동일합니다. Azure 관리자가 이러한 권한을 할당해야만 Configuration Manager로 앱을 가져올 수 있습니다.



## <a name="start-the-azure-services-wizard"></a>Azure 서비스 마법사 시작

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다.  

2.  리본의 **홈** 탭에 있는 **Azure 서비스** 그룹에서 **Azure 서비스 구성**을 선택합니다.  

3.  Azure 서비스 마법사의 **Azure 서비스** 페이지에서 다음 작업을 수행합니다.  

    1. Configuration Manager의 개체 **이름**을 지정합니다.  

    2. 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    3. Configuration Manager와 연결할 Azure 서비스를 선택합니다.  

4. **다음**을 선택하여 Azure 서비스 마법사의 [Azure 앱 속성](#azure-app-properties) 페이지로 넘어갑니다.  



## <a name="azure-app-properties"></a>Azure 앱 속성

Azure 서비스 마법사의 **앱** 페이지에서, 먼저 목록에서 **Azure 환경**을 선택합니다. 현재 환경을 사용할 수 있는 서비스에 대한 [서비스 정보](#service-details)의 표를 참조하세요.

앱 페이지의 나머지 부분은 서비스에 따라 달라집니다. 서비스에서 사용하는 앱 형식과 사용자가 사용할 수 있는 작업에 대한 [서비스 정보](#service-details)의 표를 참조하세요. 

- 앱이 작업 가져오기 및 만들기를 모두 지원하는 경우 **찾아보기**를 선택합니다. 이 작업은 [서버 앱 대화 상자](#server-app-dialog) 또는 [클라이언트 앱 대화 상자](#client-app-dialog)를 엽니다.  

- 앱이 가져오기 작업만 지원하는 경우 **가져오기**를 선택합니다. 이 작업은 [앱 가져오기 대화 상자(서버)](#import-apps-dialog-server) 또는 [앱 가져오기 대화 상자(클라이언트)](#import-apps-dialog-client)를 엽니다.

이 페이지에서 앱을 지정한 후 **다음**을 선택하여 Azure 서비스 마법사의 [구성 또는 검색](#configuration-or-discovery) 페이지로 넘어갑니다.

### <a name="web-app"></a>웹앱

이 앱은 Azure AD 형식 *웹앱/API*이며, Configuration Manager에서는 서버 앱이라고도 합니다.

#### <a name="server-app-dialog"></a>서버 앱 대화 상자

Azure 서비스 마법사의 앱 페이지에서 **웹앱**에 대한 **찾아보기**를 선택하면 서버 앱 대화 상자가 열립니다. 이 대화 상자에는 기존 웹앱의 다음 속성을 보여주는 목록이 표시됩니다.
- 테넌트 표시 이름
- 앱 표시 이름
- 서비스 종류

서버 앱 대화 상자에서는 다음과 같은 세 가지 작업을 수행할 수 있습니다.
- 기존 웹앱을 다시 사용하려면 목록에서 기존 웹앱을 선택합니다. 
- **가져오기**를 선택하여 [앱 가져오기 대화 상자](#import-apps-dialog-server)를 엽니다.
- **만들기**를 선택하여 [서버 애플리케이션 만들기 대화 상자](#create-server-application-dialog)를 엽니다.

웹앱을 선택하거나, 가져오거나, 만든 후에는 **확인**을 선택하여 서버 앱 대화 상자를 닫습니다. 이 작업은 Azure 서비스 마법사의 [앱 페이지](#azure-app-properties)로 돌아갑니다.

#### <a name="import-apps-dialog-server"></a>앱 가져오기 대화 상자(서버)

Azure 서비스 마법사의 서버 앱 대화 상자 또는 앱 페이지에서 **가져오기**를 선택하면 앱 가져오기 대화 상자가 열립니다. 이 페이지에서는 이미 Azure Portal에서 만든 Azure AD 웹앱에 대한 정보를 입력할 수 있습니다. 이 페이지는 해당 웹앱에 대한 메타데이터를 Configuration Manager로 가져옵니다. 다음 정보를 지정하세요.
- **Azure AD 테넌트 이름**
- **Azure AD 테넌트 ID**
- **애플리케이션 이름**: 앱의 식별 이름입니다.
- **클라이언트 ID**
- **비밀 키**
- **비밀 키 만료**: 달력에서 미래의 날짜를 선택합니다. 
- **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. Configuration Manager 클라이언트가 서비스 액세스를 요청할 때 사용하는 액세스 토큰입니다. 기본적으로 이 값은 https\://ConfigMgrService입니다.  

정보를 입력한 후 **확인**을 선택합니다. 그런 다음, **확인**을 선택하여 앱 가져오기 대화 상자를 닫습니다. 이 작업은 Azure 서비스 마법사의 [앱 페이지](#azure-app-properties) 또는 [서버 앱 대화 상자](#server-app-dialog)로 돌아갑니다.

#### <a name="create-server-application-dialog"></a>서버 애플리케이션 만들기 대화 상자

서버 앱 대화 상자에서 **만들기**를 선택하면 서버 애플리케이션 만들기 대화 상자가 열립니다. 이 페이지는 Azure AD에서 웹앱 만들기를 자동화합니다. 다음 정보를 지정하세요.
- **애플리케이션 이름**: 앱의 식별 이름입니다.
- **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만 Azure AD에 필요합니다. 기본적으로 이 값은 https\://ConfigMgrService입니다.  
- **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. Configuration Manager 클라이언트가 서비스 액세스를 요청할 때 사용하는 액세스 토큰입니다. 기본적으로 이 값은 https\://ConfigMgrService입니다.  
- **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.

**로그인**을 선택하여 Azure에 관리 사용자로 인증합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다. 

**확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. 이 작업은 [서버 앱 대화 상자](#server-app-dialog)로 돌아갑니다.


### <a name="native-client-app"></a>네이티브 클라이언트 앱
    
이 앱은 Azure AD 형식 *네이티브*이며, Configuration Manager에서는 클라이언트 앱이라고도 합니다.

#### <a name="client-app-dialog"></a>클라이언트 앱 대화 상자

Azure 서비스 마법사의 앱 페이지에서 **네이티브 클라이언트 앱**에 대한 **찾아보기**를 선택하면 클라이언트 앱 대화 상자가 열립니다. 이 대화 상자에는 기존 네이티브 앱의 다음 속성을 보여주는 목록이 표시됩니다.
- 테넌트 표시 이름
- 앱 표시 이름
- 서비스 종류

클라이언트 앱 대화 상자에서는 다음과 같은 세 가지 작업을 수행할 수 있습니다.
- 기존 네이티브 앱을 다시 사용하려면 목록에서 기존 네이티브 앱을 선택합니다. 
- **가져오기**를 선택하여 [앱 가져오기 대화 상자](#import-apps-dialog-client)를 엽니다.
- **만들기**를 선택하여 [클라이언트 애플리케이션 만들기 대화 상자](#create-client-application-dialog)를 엽니다.

네이티브 앱을 선택하거나, 가져오거나, 만든 후 **확인**을 선택하여 클라이언트 앱 대화 상자를 닫습니다. 이 작업은 Azure 서비스 마법사의 [앱 페이지](#azure-app-properties)로 돌아갑니다.

#### <a name="import-apps-dialog-client"></a>앱 가져오기 대화 상자(클라이언트)

클라이언트 앱 대화 상자에서 **가져오기**를 선택하면 앱 가져오기 대화 상자가 열립니다. 이 페이지에서는 이미 Azure Portal에서 만든 Azure AD 네이티브 앱에 대한 정보를 입력할 수 있습니다. 이 페이지는 해당 네이티브 앱에 대한 메타데이터를 Configuration Manager로 가져옵니다. 다음 정보를 지정하세요.
- **애플리케이션 이름**: 앱의 식별 이름입니다.
- **클라이언트 ID** 

정보를 입력한 후 **확인**을 선택합니다. 그런 다음, **확인**을 선택하여 앱 가져오기 대화 상자를 닫습니다. 이 작업은 [클라이언트 앱 대화 상자](#client-app-dialog)로 돌아갑니다.

#### <a name="create-client-application-dialog"></a>클라이언트 애플리케이션 만들기 대화 상자

클라이언트 앱 대화 상자에서 **만들기**를 선택하면 클라이언트 애플리케이션 만들기 대화 상자가 열립니다. 이 페이지는 Azure AD에서 네이티브 앱 만들기를 자동화합니다. 다음 정보를 지정하세요.
- **애플리케이션 이름**: 앱의 식별 이름입니다.
- **회신 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 기본적으로 이 값은 https\://ConfigMgrService입니다. 

**로그인**을 선택하여 Azure에 관리 사용자로 인증합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다. 

**확인**을 선택하여 Azure AD에서 네이티브 앱을 만들고 클라이언트 애플리케이션 만들기 대화 상자를 닫습니다. 이 작업은 [클라이언트 앱 대화 상자](#client-app-dialog)로 돌아갑니다.


### <a name="renew-secret-key-azure-ad-apps"></a>비밀 키 갱신, Azure AD 앱
버전 1806 이전에서 Azure 앱의 비밀 키를 갱신하려면 앱을 다시 만들어야 합니다.

버전 1806 이상:

- 만든 앱: **Cloud Services 노드** 아래에서 **Azure Active Directory 테넌트**로 이동합니다. [세부 정보] 창에서 애플리케이션이 만들어진 테넌트를 선택하고 **비밀 키 갱신**을 선택합니다.  

    - **로그인**을 선택하여 Azure에 관리 사용자로 인증합니다.  

    - **확인**을 선택하여 Azure AD에서 네이티브 앱을 만들고 클라이언트 애플리케이션 만들기 대화 상자를 닫습니다. 이 작업은 [클라이언트 앱 대화 상자](#client-app-dialog)로 돌아갑니다.  

- 가져온 앱: Azure Portal을 사용하여 갱신하고 새 비밀 키와 만료 날짜를 기록합니다. **비밀 키 갱신** 마법사에서 이 정보를 추가합니다.  

> [!Note]  
> 비밀 키를 저장한 후 Azure 애플리케이션 속성 **키** 페이지를 닫습니다. 페이지를 닫으면 이 정보는 제거됩니다.


## <a name="configuration-or-discovery"></a>구성 또는 검색

웹 페이지에서 웹앱 및 네이티브 앱을 지정한 후에는 사용자가 연결하려는 서비스에 따라 Azure 서비스 마법사가 **구성** 또는 **검색** 페이지를 진행합니다. 이 페이지의 세부 정보는 서비스마다 다릅니다. 자세한 내용은 다음 문서 중 하나를 참조하세요.  

-   **클라우드 관리** 서비스, **검색** 페이지: [Azure AD 사용자 검색 구성](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

-   **Log Analytics 커넥터** 서비스, **구성** 페이지: [Log Analytics에 연결 구성](/sccm/core/clients/manage/sync-data-log-analytics#configure-the-connection-to-log-analytics)  

-   **업그레이드 준비 커넥터** 서비스, **구성** 페이지: [Azure 마법사를 사용하여 연결 만들기](/sccm/core/clients/manage/upgrade/upgrade-analytics#use-the-azure-wizard-to-create-the-connection)  

-   **비즈니스용 Microsoft Store** 서비스, **구성** 페이지: [비즈니스용 Microsoft Store 동기화 구성](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#bkmk_config)  


마지막으로 요약, 진행률 및 완료 페이지를 통해 Azure 서비스 마법사를 완료합니다. Configuration Manager에서 Azure 서비스 구성을 완료했습니다. 이 프로세스를 반복하여 다른 Azure 서비스를 구성하세요.


## <a name="view-the-configuration-of-an-azure-service"></a>Azure 서비스의 구성 보기
사용하도록 구성한 Azure 서비스의 속성을 봅니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스**를 선택합니다. 보거나 편집하려는 서비스를 선택한 다음, **속성**을 선택합니다.

서비스를 선택한 다음, 리본에서 **삭제**를 선택하는 경우 이 작업은 Configuration Manager에서 연결을 삭제합니다. Azure AD의 앱은 제거되지 않습니다. 앱이 더 이상 필요 없는 경우 Azure 관리자에게 앱을 삭제해 달라고 요청하거나 또는 Azure 서비스 마법사를 실행하여 앱을 가져오세요.<!--483440-->


## <a name="cloud-management-data-flow"></a>클라우드 관리 데이터 흐름

다음 다이어그램은 Configuration Manager, Azure AD 및 연결된 클라우드 서비스 간의 상호 작용에 대한 개념적 데이터 흐름을 나타낸 것입니다. 이 예제에서는 Windows 10 클라이언트와 서버 앱 및 클라이언트 앱이 모두 포함된 **클라우드 관리** 서비스를 사용합니다. 다른 서비스에 대한 흐름은 비슷합니다.

![Configuration Manager와 Azure AD 및 클라우드 관리 간의 데이터 흐름 다이어그램](media/aad-auth.png)

1.  Configuration Manager 관리자가 Azure AD에서 클라이언트 앱 및 서버 앱을 가져오거나 만듭니다.  

2.  Configuration Manager Azure AD 사용자 검색 메서드가 실행됩니다. 사이트에서 Azure AD 서버 앱 토큰을 사용하여 Microsoft Graph에 사용자 개체를 쿼리합니다.  

3.  사이트에서 사용자 개체에 대한 데이터를 저장합니다. 자세한 내용은 [Azure AD 사용자 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc)을 참조하세요.  

4.  Configuration Manager 클라이언트가 Azure AD 사용자 토큰을 요청합니다. 클라이언트에서 Azure AD 클라이언트 앱의 애플리케이션 ID를 사용하여, 그리고 서버 앱을 대상 그룹으로 사용하여 클레임을 만듭니다. 자세한 내용은 [Azure AD 보안 토큰의 클레임](/azure/active-directory/develop/authentication-scenarios#claims-in-microsoft-identity-platform-security-tokens)을 참조하세요.  

5.  클라이언트는 클라우드 관리 게이트웨이 및/또는 온-프레미스 HTTPS 사용 관리 지점에 Azure AD 토큰을 제공하여 사이트에 인증합니다.  


