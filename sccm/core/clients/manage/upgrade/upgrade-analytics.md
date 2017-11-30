---
title: "업그레이드 준비"
titleSuffix: Configuration Manager
description: "업그레이드 준비를 Configuration Manager와 통합합니다. 관리 콘솔에서 업그레이드 호환성 데이터에 액세스합니다. 업그레이드 또는 수정 대상 장치를 지정합니다."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 7/31/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.openlocfilehash: df2950551e527788aeb01d57cdbf01ad19817ccd
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>업그레이드 준비를 System Center Configuration Manager와 통합

*적용 대상: System Center Configuration Manager(현재 분기)*

업그레이드 준비(이전의 Upgrade Analytics)는 [Windows Analytics](https://www.microsoft.com/WindowsForBusiness/windows-analytics)의 일부로, Windows 10으로 업그레이드하기 위해 사용자 환경에서 장치의 준비 상태를 평가하고 분석할 수 있습니다. 특정 버전을 구성할 수 있습니다. 업그레이드 준비는 Configuration Manager와 통합하여 Configuration Manager 관리 콘솔에서 클라이언트 업그레이드 호환성 데이터에 액세스할 수 있습니다. 이 데이터를 기반으로 하여 만든 동적 컬렉션을 통해 장치를 대상으로 지정하여 업그레이드 또는 수정할 수 있습니다.

업그레이드 준비는 [OMS(Operations Management Suite)](/azure/operations-management-suite/operations-management-suite-overview)에서 실행되는 솔루션입니다. [업그레이드 준비를 통해 Windows 업그레이드 관리](/windows/deployment/upgrade/manage-windows-upgrades-with-upgrade-readiness)에서 업그레이드 준비에 대해 자세히 알아볼 수 있습니다.

## <a name="configure-clients"></a>클라이언트 구성

업그레이드 준비는 모든 Windows Analytics 솔루션과 마찬가지로 Windows 원격 분석 데이터를 사용합니다. 업그레이드 준비에서 원격 분석 데이터를 충분히 받으려면 다음과 같은 필수 구성 요소가 충족되어야 합니다.

- 모든 클라이언트는 **상업용 ID 키**로 구성되어야 합니다. 
- 기본 수준 이상의 원격 분석을 보고하도록 Windows 10 클라이언트를 구성해야 합니다.
-  Windows에서 이전 버전을 실행하는 클라이언트에는 [업그레이드 준비 시작](/windows/deployment/upgrade/upgrade-readiness-get-started#deploy-the-compatibility-update-and-related-kbs)에서 설명한 대로 특정 KB가 설치되어 있어야 합니다. 또한 **클라이언트 설정**에서 사용하도록 설정된 원격 분석이 있어야 합니다.

상업용 ID 키 및 Windows 원격 분석은 **클라이언트 설정**에서 구성할 수 있습니다. 자세한 내용은 [Configuration Manager에서 Windows Analytics 사용](../monitor-windows-analytics.md)을 참조하세요.

>[!NOTE]
>예상대로 사용자 환경의 장치에서 원격 분석 데이터를 받지 못하는 업그레이드 준비 문제가 발생하면 [업그레이드 준비 배포 스크립트](/windows/deployment/upgrade/upgrade-readiness-deployment-script)를 사용하여 이러한 문제 중 일부를 해결할 수 있습니다. 그러나 올바른 KB를 배포하는 대부분의 환경에서는 **클라이언트 설정**에서 상업용 ID 키와 원격 분석을 구성하는 것으로 충분합니다.

## <a name="connect-configuration-manager-to-upgrade-readiness"></a>Configuration Manager를 업그레이드 준비에 연결

현재 분기 버전 1706부터 [Azure 서비스 마법사](../../../servers/deploy/configure/azure-services-wizard.md)를 사용하여 Configuration Manager에서 사용하도록 Azure 서비스를 구성하는 과정을 간소화할 수 있습니다. Configuration Manager와 업그레이드 준비를 연결하려면 *[Azure Portal](https://portal.azure.com)에서 웹앱/API* 유형의 Azure AD 앱 등록을 만들어야 합니다. 앱 등록을 만드는 방법에 대해 자세히 알아보려면 [Azure Active Directory 테넌트로 응용 프로그램 등록](/azure/active-directory/active-directory-app-registration)을 참조하세요. 또한 **Azure Portal**에서 업그레이드 준비 데이터를 호스팅하는 OMS 작업 영역이 포함된 리소스 그룹에 새로 등록된 웹앱 *참가자* 권한을 부여해야 합니다. **Azure 서비스 마법사**는 이 앱 등록을 사용하여 Configuration Manager에서 Azure AD와 안전하게 통신하고 업그레이드 준비 데이터에 인프라를 연결할 수 있게 합니다.

>[!IMPORTANT]
>Azure AD 사용자 ID와 달리 *참가자* 권한은 앱 자체에 부여해야 합니다. 이는 등록된 응용 프로그램이며 Configuration Manager 인프라를 대신하여 데이터에 액세스하는 Azure AD 사용자가 아니기 때문입니다. 이를 위해서는 권한을 할당할 때 **사용자 추가** 블레이드에서 앱 등록 이름을 검색해야 합니다. 이 작업은 [Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm)에 연결하기 위해 [OMS에 대한 권한을 Configuration Manager에 제공](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms)할 때 수행해야 하는 프로세스와 동일합니다. 이러한 단계는 *Azure 서비스 마법사*를 사용하여 앱 등록을 Configuration Manager로 가져오기 전에 완료해야 합니다.

### <a name="use-the-azure-wizard-to-create-the-connection"></a>Azure 마법사를 사용하여 연결 만들기

[Configuration Manager에서 사용하도록 Azure 서비스 구성](../../../servers/deploy/configure/azure-services-wizard.md)의 지침에 따라 위에서 만든 웹앱 등록을 가져와서 업그레이드 준비에 대한 연결을 만듭니다. 

웹앱 가져오기가 성공하고 **Azure Portal**에서 올바른 권한이 할당된 경우 *구성* 페이지에서 다음 값이 미리 채워집니다. 
-  Azure 구독
-  Azure 리소스 그룹
-  Windows Analytics 작업 영역

등록된 Azure AD 웹앱에 둘 이상의 리소스 그룹에 대한 *참가자* 권한이 있거나 선택한 리소스 그룹에 둘 이상의 OMS 작업 영역이 포함되어 있는 경우에만 둘 이상의 리소스 그룹 또는 작업 영역을 사용할 수 있습니다.
 
## <a name="view-and-use-upgrade-readiness-information-in-configuration-manager"></a>Configuration Manager에서 업그레이드 준비 정보 보기 및 사용

업그레이드 준비를 Configuration Manager와 통합한 후에는 클라이언트의 업그레이드 준비 상태에 대한 분석을 확인할 수 있습니다.

1. Configuration Manager 콘솔에서 **모니터링** > **개요** > **업그레이드 준비**를 선택합니다.
2. 업그레이드 준비 상태 및 원격 분석을 보고 하는 Windows 장치 비율이 포함된 데이터를 검토합니다.
3. 대시보드를 필터링하여 특정 컬렉션의 장치에 대한 데이터를 볼 수 있습니다.
4. 특정 준비 상태의 장치를 보고 이러한 장치에 대한 동적 컬렉션을 만들어 준비가 되었으면, 해당 장치를 업그레이드하거나 업그레이드로부터 차단된 장치를 수정하는 작업을 수행할 수 있습니다.

## <a name="using-the-upgrade-readiness-connector-version-1702-and-earlier"></a>업그레이드 준비 커넥터(버전 1702 이하) 사용

Configuration Manager 버전 1702 또는 이전 버전에서 업그레이드 준비에 대한 연결을 만드는 경우 다른 단계와 요구 사항 집합이 필요합니다.

### <a name="prerequisites"></a>전제 조건

- 연결을 추가하려면 Configuration Manager 환경에서 먼저 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 [온라인 모드](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)로 구성해야 합니다. 사용자 환경에 연결을 추가하면 이 사이트 시스템 역할을 실행하는 컴퓨터에 Microsoft Monitoring Agent도 설치됩니다.
- Configuration Manager를 "웹 응용 프로그램 및/또는 Web API" 관리 도구로 등록하고 [이 등록의 클라이언트 ID](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/)를 받습니다.
- Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.
- Azure Portal에서 [Configuration Manager에 OMS에 대한 사용 권한 제공](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms)에 설명된 대로 OMS에 액세스할 수 있는 권한을 등록된 웹앱에 제공합니다.

    > [!IMPORTANT]
    > OMS에 액세스할 수 있는 권한을 구성하는 경우 **참가자** 역할을 선택하고 등록된 앱의 리소스 그룹에 사용 권한을 할당해야 합니다.

### <a name="create-the-connection"></a>연결 만들기

1.  Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **업그레이드 준비 커넥터** > **Upgrade Analytics에 대한 연결 만들기**를 선택하여 **Upgrade Analytics 연결 추가 마법사**를 시작합니다.
3.  **Azure Active Directory** 화면에서 **테넌트**, **클라이언트 ID** 및 **클라이언트 비밀 키**를 제공하고 **다음**을 선택합니다.
4.  **업그레이드 준비** 화면에서 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 정보를 입력하여 연결 설정을 제공합니다.
5.  **요약** 화면에서 연결 설정을 확인하고 **다음**을 선택합니다.

    > [!NOTE]
    > 계층 구조의 최상위 계층 사이트에 업그레이드 준비를 연결해야 합니다. 업그레이드 준비를 독립 실행형 기본 사이트에 연결한 다음 사용자 환경에 중앙 관리 사이트를 추가하는 경우 OMS 연결을 삭제하고 새 계층 구조 내에서 다시 만들어야 합니다.
