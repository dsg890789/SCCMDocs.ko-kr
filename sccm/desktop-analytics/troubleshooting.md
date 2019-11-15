---
title: Desktop Analytics 문제 해결
titleSuffix: Configuration Manager
description: Desktop Analytics와 관련된 문제를 해결하는 데 도움이 되는 기술 세부 정보입니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 63e08f3f-9558-4ed7-9bf3-3a185ddaac5c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ecb1657903fd3d1dfe43f2ad46258b4643c2f55
ms.sourcegitcommit: ef7800a294e5db5d751921c34f60296c1642fc1f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712597"
---
# <a name="troubleshoot-desktop-analytics"></a>Desktop Analytics 문제 해결

이 문서의 세부 정보를 사용하여 Configuration Manager와 통합된 Desktop Analytics의 문제를 해결할 수 있습니다.



## <a name="confirm-prerequisites"></a>필수 구성 요소 확인

많은 일반적인 문제는 필수 구성 요소 누락으로 인해 발생합니다. 먼저 다음 구성을 확인합니다.

- [전제 조건](/sccm/desktop-analytics/overview#prerequisites)  

- [Windows 구성 요소 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)  

- [데이터 공유를 사용하도록 설정](/sccm/desktop-analytics/enable-data-sharing): 다음 토픽에 대해 다룹니다.  

    - 클라이언트에서 연결해야 하는 인터넷 엔드포인트  

    - 프록시 서버 인증  

    - 진단 데이터 수준  



## <a name="monitor-connection-health"></a>연결 상태 모니터링

Configuration Manager의 **연결 상태** 대시보드를 사용하여 디바이스 상태별로 범주를 드릴다운합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **Desktop Analytics Servicing** 노드를 확장하고 **연결 상태** 대시보드를 선택합니다.  

자세한 내용은 [연결 상태 모니터링](/sccm/desktop-analytics/monitor-connection-health)을 참조하세요.


## <a name="log-files"></a>로그 파일

자세한 내용은 [Desktop Analytics에 대한 로그 파일](/sccm/core/plan-design/hierarchy/log-files#desktop-analytics)을 참조하세요.

Configuration Manager 버전 1906부터 Configuration Manager 설치 디렉터리에서 **DesktopAnalyticsLogsCollector.ps1** 도구를 사용하여 Desktop Analytics 문제를 해결할 수 있습니다. 이 도구는 몇 가지 기본적인 문제 해결 단계를 실행하고 관련 로그를 단일 작업 디렉터리로 수집합니다. 자세한 내용은 [로그 수집기](/sccm/desktop-analytics/log-collector)를 참조하세요.

### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용

1. 서비스 연결 지점에서 다음 레지스트리 키로 이동합니다. `HKLM\Software\Microsoft\SMS\Tracing\SMS_SERVICE_CONNECTOR`  
2. **LoggingLevel** 값을 `0`으로 설정합니다.  


## <a name="bkmk_AzureADApps"></a> Azure AD 애플리케이션

Desktop Analytics는 Azure AD에 다음 애플리케이션을 추가합니다.

- **Configuration Manager 마이크로서비스**: Configuration Manager를 Desktop Analytics와 연결합니다. 이 앱에는 액세스 요구 사항이 없습니다.  

- **MALogAnalyticsReader**: Log Analytics에서 만든 OMS 그룹 및 디바이스를 검색합니다. 자세한 내용은 [MALogAnalyticsReader 애플리케이션 역할](#bkmk_MALogAnalyticsReader)을 참조하세요.  

설치를 완료한 후 이러한 앱을 프로비저닝해야 하는 경우 **연결된 서비스** 창으로 이동합니다. **사용자 및 앱 액세스 구성**을 선택하고 앱을 프로비저닝합니다.  

- **Configuration Manager에 대한 Azure AD 앱** 설치를 완료한 후 연결 문제를 해결 또는 프로비저닝해야 하는 경우 [Configuration Manager에 대한 앱 만들기 및 가져오기](#create-and-import-app-for-configuration-manager)를 참조하세요. 이 앱을 사용하려면 **Configuration Manager Service** API에서 **CM 컬렉션 데이터를 작성**하고 **CM 컬렉션 데이터를 읽어야** 합니다.  


### <a name="create-and-import-app-for-configuration-manager"></a>Configuration Manager용 앱 만들기 및 가져오기

Azure 서비스 구성 마법사에서 Configuration Manager 용 Azure AD 앱을 만들 수 없거나 기존 앱을 다시 사용하려는 경우 수동으로 만들고 가져와야 합니다. Desktop Analytics 포털에서 [초기 온보딩](/sccm/desktop-analytics/set-up#initial-onboarding)을 완료한 후 다음 단계를 사용합니다.

#### <a name="create-app-in-azure-ad"></a>Azure AD에서 앱 만들기

1. *관리자* 권한이 있는 사용자로 [Azure Portal](https://portal.azure.com)을 열고 **Azure Active Directory**로 이동한 후 **앱 등록**을 선택합니다. 그런 다음, **새 등록**을 선택합니다.  

2. **만들기** 패널에서 다음 설정을 구성합니다.  

    - **이름**: 앱을 식별하는 고유 이름입니다(예: `Desktop-Analytics-Connection`).  

    - **지원되는 계정 유형**: **이 조직 디렉터리에만 있는 계정(Contoso)**

    - **리디렉션 URI(선택 사항)** : **웹**  

    <!--     - **Sign-on URL**: this value isn't used by Configuration Manager, but required by Azure AD. Enter a unique and valid URL, for example: `https://configmgrapp`   -->
  
    **등록**을 선택합니다.  

3. 앱을 선택하고 **애플리케이션(클라이언트) ID** 및 **디렉터리(테넌트) ID**를 적어둡니다. 값은 Configuration Manager 연결을 구성하는 데 사용되는 GUID입니다.  

4. **관리** 메뉴에서 **인증서 및 비밀**을 선택합니다. **새 클라이언트 비밀**을 선택합니다. **설명**을 입력하고, 만료 기간을 지정한 다음, **추가**를 선택합니다. Configuration Manager 연결을 구성하는 데 사용되는 키의 **값**을 복사합니다.

    > [!Important]  
    > 이는 키 값을 복사하기 위한 유일한 기회입니다. 지금 복사하지 않으면 다른 키를 만들어야 합니다.  
    >
    > 키 값을 안전한 위치에 저장합니다.  

5. **관리** 메뉴에서 **API 권한**을 선택합니다.  

    1. **API 권한** 패널에서 **권한 추가**를 선택합니다.  

    2. **API 권한 요청** 패널에서 **내 조직이 사용하는 API**로 전환합니다.  

    3. **Configuration Manager 마이크로서비스** API를 검색하여 선택합니다.  

    4. **애플리케이션 권한** 그룹을 선택합니다. **CmCollectionData**를 확장하고 다음 두 사용 권한을 모두 선택합니다. **CM 컬렉션 데이터를 작성**하고 **CM 컬렉션 데이터를 읽습니다**.  

    5. **모든 권한**을 선택합니다.  

6. **API 권한** 패널에서 **관리자 권한 부여**를 선택합니다. **예**를 선택합니다.  


#### <a name="import-app-in-configuration-manager"></a>Configuration Manager에서 앱 가져오기

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 리본에서 **Azure Services 구성**을 선택합니다.  

2. Azure Services 마법사의 **Azure Services** 페이지에서 다음 설정을 구성합니다.  

    - Configuration Manager의 개체 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    - 사용 가능한 서비스 목록에서 **Desktop Analytics**를 선택합니다.  
  
   **다음**을 선택합니다.  

3. **앱** 페이지에서 적절한 **Azure 환경**을 선택합니다. 그런 다음, 웹앱에 대해 **가져오기**를 선택합니다. **앱 가져오기** 창에서 다음 설정을 구성합니다.  

    - **Azure AD 테넌트 이름**: 이 이름은 Configuration Manager에서 이름이 지정되는 방식입니다.  

    - **Azure AD 테넌트 ID**: Azure AD에서 복사한 **디렉터리 ID**입니다.  

    - **클라이언트 ID**: Azure AD 앱에서 복사한 **애플리케이션 ID**입니다.  

    - **비밀 키**: Azure AD 앱에서 복사한 키 **값**입니다.  

    - **비밀 키 만료**: 키의 동일한 만료 날짜입니다.  

    - **앱 ID URI**: 이 설정은 다음 값으로 자동으로 채워집니다. `https://cmmicrosvc.manage.microsoft.com/`  
  
   **확인**을 선택한 다음, **확인**을 선택하여 앱 가져오기 창을 닫습니다. Azure Services 마법사의 앱 페이지에서 **다음**을 선택합니다.  

**진단 데이터** 페이지에서 마법사의 나머지 단계를 계속하려면 [서비스에 연결](/sccm/desktop-analytics/connect-configmgr#bkmk_connect)을 참조하세요.

#### <a name="troubleshoot-app-in-configuration-manager"></a>Configuration Manager의 앱 문제 해결

앱을 만들거나 가져오는 데 문제가 있는 경우 먼저 특정 오류에 대한 **SMSAdminUI.log**를 확인하세요. 그런 다음, 다음과 같은 구성을 확인합니다.

- Desktop Analytics 서비스에 테넌트를 성공적으로 등록했습니다. 자세한 내용은 [Desktop Analytics를 설정하는 방법](/sccm/desktop-analytics/set-up)을 참조하세요.

- 모든 필수 엔드포인트에 액세스할 수 있습니다. 자세한 내용은 [엔드포인트](/sccm/desktop-analytics/enable-data-sharing#endpoints)를 참조하세요.

- 로그인한 사용자에게 올바른 사용 권한이 있는지 확인합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.

- 사용자가 일반적으로 Azure에 로그인할 수 있는지 확인합니다. 이 작업은 일반적인 Azure AD 인증 문제가 있는지 여부를 확인합니다.

- *Desktop Analytics 작업자*와 관련된 **SMS_SERVICE_CONNECTOR** 구성 요소에 대한 상태 메시지를 확인합니다.


### <a name="bkmk_MALogAnalyticsReader"></a> MALogAnalyticsReader 애플리케이션 역할

Desktop Analytics를 설정하는 경우 사용자가 조직을 대신하여 동의하게 됩니다. 이 동의는 MALogAnalyticsReader 애플리케이션에 작업 영역에 대한 Log Analytics Reader 역할을 할당하는 것입니다. 이 애플리케이션 역할은 Desktop Analytics에 필요합니다.

설치하는 동안 이 프로세스에 문제가 있는 경우 다음 프로세스를 사용하여 이 권한을 수동으로 추가합니다.

1. [Azure Portal](https://portal.azure.com)로 이동하여 **모든 리소스**를 선택합니다. **Log Analytics** 형식의 작업 영역을 선택합니다.  

2. 작업 영역 메뉴에서 **액세스 제어(IAM)** 를 선택한 다음, **추가**를 선택합니다.  

3. **권한 추가** 패널에서 다음 설정을 구성합니다.  

    - **역할**: **독자**  

    - **다음에 대한 액세스 할당**: **Azure AD 사용자, 그룹 또는 애플리케이션**  

    - **선택**: **MALogAnalyticsReader**  

4. **저장**을 선택합니다.

포털에 역할 할당을 추가했음을 알리는 알림이 표시됩니다.


## <a name="data-latency"></a>데이터 대기 시간

<!-- 3846531 -->
처음으로 Desktop Analytics를 설정하거나, 새 클라이언트를 등록하거나, 새 배포 계획을 구성하는 경우 Configuration Manager 및 Desktop Analytics 포털의 보고서에 전체 데이터가 즉시 표시되지 않을 수 있습니다. 다음 단계를 수행하는 데 2-3일이 소요될 수 있습니다.

- 활성 디바이스에서 진단 데이터를 Desktop Analytics 서비스로 전송합니다.
- 서비스가 데이터를 처리합니다.
- 서비스가 Configuration Manager 사이트와 동기화됩니다.

Configuration Manager 계층 구조에서 Desktop Analytics로 디바이스 컬렉션을 동기화하는 경우 해당 컬렉션이 Desktop Analytics 포털에 표시되는 데 최대 1시간이 걸릴 수 있습니다. 마찬가지로, Desktop Analytics에서 배포 계획을 만들 때 배포 계획과 연결된 새 컬렉션이 Configuration Manager 계층 구조에 표시되는 데 최대 1시간이 걸릴 수 있습니다. 기본 사이트에서 컬렉션을 만들고 중앙 관리 사이트가 Desktop Analytics와 동기화됩니다. Configuration Manager에서 컬렉션 멤버 자격을 평가하고 업데이트하는 데 최대 24시간이 걸릴 수 있습니다. 이 프로세스를 더 빠르게 하려면 컬렉션 멤버 자격을 수동으로 업데이트합니다.<!-- 4984639 -->

> [!Note]
> 수동 컬렉션 업데이트로 변경 사항을 반영하려면 먼저 SMS_SERVICE_CONNECTOR_M365ADeploymentPlanWorker 구성 요소를 동기화해야 합니다. 이 프로세스를 실행하는 데 최대 1시간이 걸릴 수 있습니다. 자세한 내용은 **M365ADeploymentPlanWorker.log**를 참조하세요.

Desktop Analytics 포털 내에는 **관리자 데이터** 및 **진단 데이터**라는 두 가지 유형의 데이터가 있습니다.

- **관리자 데이터**는 작업 영역 구성에 대한 변경 내용을 나타냅니다. 예를 들어 자산의 **업그레이드 결정** 또는 **중요도**를 변경하는 경우 관리자 데이터를 변경하게 됩니다. 이러한 변경 내용은 종종 복잡한 효과를 내는데, 설치된 자산이 불확실한 디바이스의 준비 상태를 변경할 수 있기 때문입니다.

- **진단 데이터**는 클라이언트 디바이스에서 Microsoft로 업로드되는 시스템 메타데이터를 나타냅니다. Desktop Analytics는 이 데이터를 통해 작동합니다. 디바이스 인벤토리, 보안 및 기능 업데이트 상태와 같은 특성이 포함됩니다.

기본적으로 Desktop Analytics 포털의 모든 데이터는 매일 자동으로 새로 고쳐집니다. 이 새로 고침에는 진단 데이터의 변경 내용과 구성(관리자 데이터)에 대한 변경 내용이 포함됩니다. 매일 오전 8시(UTC)에 Desktop Analytics 포털에 표시되어야 합니다.

관리자 데이터를 변경할 때 작업 영역에서 관리자 데이터의 요청 시 새로 고침을 트리거할 수 있습니다. Desktop Analytics 포털의 모든 페이지에서 데이터 통화 플라이아웃을 엽니다.

![Desktop Analytics 포털의 데이터 통화 플라이아웃 탭 스크린샷](media/data-currency-flyout.png)

그런 다음, **변경 내용 적용**을 선택합니다.

![Desktop Analytics 포털의 확장된 데이터 통화 플라이아웃 스크린샷](media/data-currency-flyout-expand.png)

이 프로세스는 일반적으로 15-60분이 소요됩니다. 타이밍은 작업 영역의 크기 및 처리가 필요한 변경 내용의 범위에 따라 달라집니다. 요청 시 데이터 새로 고침을 요청하는 경우 진단 데이터는 변경되지 않습니다.  자세한 내용은 [Desktop Analytics FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조하세요.

위에 표시된 시간 프레임 내에 업데이트된 변경 내용이 표시되지 않으면 다음 일일 새로 고침을 위해 24시간 동안 기다립니다. 더 오래 지연되는 경우 서비스 상태 대시보드를 확인합니다. 서비스가 정상으로 보고되는 경우 Microsoft 지원에 문의하세요.<!-- 3896921 -->
