---
title: 자습서 - Windows 10 배포
titleSuffix: Configuration Manager
description: Desktop Analytics 및 Configuration Manager를 사용하여 Windows 10을 파일럿 그룹에 배포하는 방법에 대한 자습서입니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: tutorial
ms.assetid: 3e82cd96-0ce0-474a-a597-d65fceadc95a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c84b5bf720a974bd767db56b9e9da4784caefad1
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72384679"
---
# <a name="tutorial-deploy-windows-10-to-pilot"></a>자습서: 파일럿에 Windows 10 배포

이 자습서에서는 Desktop Analytics 및 Configuration Manager를 사용하여 Windows 10을 파일럿 그룹에 배포합니다. 인사이트를 제공하여 온-프레미스 제품으로 Windows를 배포하는 클라우드 서비스를 통합하도록 강조합니다. Desktop Analytics를 사용하여 파일럿 그룹에 배치하는 데 가장 적합한 디바이스를 결정합니다. 그런 다음, Configuration Manager를 사용하여 Windows를 최신 상태로 가져옵니다.

이 자습서에서는 다음을 수행하는 방법을 알아봅니다.  

> [!div class="checklist"]  
> * Azure Portal에서 Desktop Analytics 설정  
> * Configuration Manager 연결 및 디바이스 설정 구성  
> * Windows 10용 Desktop Analytics 배포 계획 만들기  
> * Configuration Manager를 사용하여 파일럿 그룹에 Windows 10 배포  

Azure 구독이 없는 경우 시작하기 전에 먼저 [체험 계정](https://azure.microsoft.com/free)을 만듭니다. 올바르게 구성된 Desktop Analytics를 사용하면 Azure 비용이 발생하지 않습니다.

Desktop Analytics는 Azure 구독에서 *Log Analytics 작업 영역*을 사용합니다. 작업 영역은 기본적으로 계정 정보 및 해당 계정에 대한 간단한 구성 정보를 포함하는 컨테이너입니다. 자세한 내용은 [작업 영역 관리](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-access?toc=/azure/azure-monitor/toc.json)를 참조하세요.



## <a name="prerequisites"></a>필수 구성 요소

이 자습서를 시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.  

- 활성 Azure 구독 - [**글로벌 관리자**](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator-permissions) 권한 부여  

    자세한 내용은 [Desktop Analytics 필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.

- Configuration Manager 버전 1902 - 업데이트 롤업(4500571) 이상 포함, **전체 관리자** 역할 수행  

- Windows 10 최신 버전용 설치 미디어

- 다음 구성을 사용하는 하나 이상의 Windows 10 디바이스:  

    - Windows 10 버전 1709 이상, 단 사용하려는 설치 미디어 버전보다 작음

    - 최신 Windows 10 누적 품질 업데이트  

    - Configuration Manager 클라이언트 버전 1902 - 업데이트 롤업(4500571) 이상 포함  

- 비즈니스 승인 - 파일럿 디바이스에서 Windows 진단 데이터 수준을 **향상됨(제한됨)** 으로 구성  

    자세한 내용은 [Desktop Analytics 개인 정보 보호](/sccm/desktop-analytics/privacy)를 참조하세요.

- 디바이스에서 다음 인터넷 엔드포인트로의 네트워크 연결:

    - `https://v10c.events.data.microsoft.com`  
    - `https://settings-win.data.microsoft.com`  
    - `http://adl.windows.com`  
    - `https://watson.telemetry.microsoft.com`  
    - `https://umwatsonc.events.data.microsoft.com`  
    - `https://ceuswatcab01.blob.core.windows.net`  
    - `https://ceuswatcab02.blob.core.windows.net`  
    - `https://eaus2watcab01.blob.core.windows.net`  
    - `https://eaus2watcab02.blob.core.windows.net`  
    - `https://weus2watcab01.blob.core.windows.net`  
    - `https://weus2watcab02.blob.core.windows.net`  
    - `https://kmwatsonc.events.data.microsoft.com`  
    - `https://oca.telemetry.microsoft.com`  
    - `https://login.live.com`  
    - `https://graph.windows.net`(Configuration Manager 서버 역할에만 해당)
    - `https://*.manage.microsoft.com`(Configuration Manager 서버 역할에만 해당)

    자세한 내용은 [Desktop Analytics에 데이터 공유를 사용하도록 설정하는 방법](/sccm/desktop-analytics/enable-data-sharing#endpoints)을 참조하세요.  

> [!Important]  
> 이러한 필수 구성 요소는 이 자습서를 위한 것입니다. Configuration Manager를 사용하는 Desktop Analytics의 일반적인 필수 구성 요소에 대한 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.  



## <a name="set-up-desktop-analytics"></a>Desktop Analytics 설정

다음 절차를 사용하여 Desktop Analytics에 로그인하고 구독에서 구성합니다. 이 절차는 조직에 대해 Desktop Analytics를 설정하는 일회성 프로세스입니다.  

1. Microsoft 365 디바이스 관리에서 [**글로벌 관리자** 권한이 있는 사용자로서 Desktop Analytics 포털](https://aka.ms/desktopanalytics)을 엽니다. **시작**을 선택합니다.  

2. **서비스 계약 동의** 페이지에서 서비스 계약을 검토하고, **동의함**을 선택합니다.  

3. **구독 확인** 페이지에서 필요한 적격 라이선스 목록은 Desktop Analytics의 Windows 디바이스 상태 기능에 대한 것입니다. 계속하려면 **다음**을 선택합니다.  

4. **사용자에게 액세스 권한 부여** 페이지에서 다음을 수행합니다.

    - **Desktop Analytics에서 사용자를 대신하여 디렉터리 역할을 관리하도록 허용**: Desktop Analytics는 **작업 영역 소유자**에게 **Desktop Analytics 관리자** 역할을 자동으로 할당합니다. 해당 그룹이 이미 **글로벌 관리자**인 경우에는 변경할 필요가 없습니다.  

        이 옵션이 선택되지 않으면 Desktop Analytics에서 여전히 사용자를 보안 그룹의 멤버로 추가합니다. **글로벌 관리자**는 사용자에게 **Desktop Analytics 관리자** 역할을 수동으로 할당해야 합니다.  

        Azure Active Directory에서 관리자 역할 권한을 할당하는 방법 및 **Desktop Analytics 관리자**에 할당된 권한에 대한 자세한 내용은 [Azure Active Directory의 관리자 역할 권한](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)을 참조하세요.  

    - Desktop Analytics는 Azure Active Directory에서 **작업 영역 소유자** 보안 그룹을 미리 구성하여 작업 영역과 배포 계획을 만들고 관리합니다. 

        사용자를 그룹에 추가하려면 **이름 또는 이메일 주소 입력** 섹션에서 해당 이름 또는 이메일 주소를 입력합니다. 완료되면 **다음**을 선택합니다.

5. **작업 영역 설정** 페이지에서 다음을 수행합니다.  

    > [!Note]  
    > 이 단계를 완료하려면 사용자에게 **작업 영역 소유자** 권한과 Azure 구독 및 리소스 그룹에 대한 추가 액세스 권한이 필요합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.  

    - Azure 구독을 선택합니다.  

    - 기존 작업 영역을 Desktop Analytics에 사용하려면 해당 작업 영역을 선택하고 다음 단계를 계속 진행합니다.  

    - Desktop Analytics에 대한 작업 영역을 만들려면 **작업 영역 추가**를 선택합니다.  

        1. **작업 영역 이름**을 입력합니다.  

        2. 드롭다운 목록에서 **이 작업 영역에 대한 Azure 구독 이름 선택**을 선택하고, 이 작업 영역에 대한 Azure 구독을 선택합니다.  

        3. 리소스 그룹을 **새로 만들거나** **기존 리소스 그룹을 사용**합니다.  

        4. 목록에서 **영역**을 선택한 다음, **추가**를 선택합니다.  

6. 새 작업 영역 또는 기존 작업 영역을 선택한 다음, **Desktop Analytics 작업 영역으로 설정**을 선택합니다.  그런 다음, **확인 및 액세스 권한 부여** 대화 상자에서 **계속**을 선택합니다.  

7. 새 브라우저 탭에서 로그인하는 데 사용할 계정을 선택합니다. **조직 대신 동의** 옵션을 선택하고, **동의함**을 선택합니다.  


    > [!Note]  
    > 이 동의는 MALogAnalyticsReader 애플리케이션에 작업 영역에 대한 Log Analytics 읽기 권한자 역할을 할당하는 것입니다. Desktop Analytics에는 이 애플리케이션 역할이 필요합니다. 자세한 내용은 [MALogAnalyticsReader 애플리케이션 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)을 참조하세요.  

8. 페이지에서 **작업 영역 설정**으로 돌아가서 **다음**을 선택합니다.  

9. **마지막 단계** 페이지에서 **Desktop Analytics로 이동**을 선택합니다. Azure Portal에 Desktop Analytics **홈** 페이지가 표시됩니다.  



## <a name="connect-configuration-manager"></a>Configuration Manager 연결

다음 절차를 사용하여 Configuration Manager를 업데이트하고, Desktop Analytics에 연결하고, 디바이스 설정을 구성합니다. 이 절차는 계층 구조를 클라우드 서비스에 연결하는 일회성 프로세스입니다.  

### <a name="update-configuration-manager"></a>Configuration Manager 업데이트

Desktop Analytics와의 통합을 지원하기 위해 Configuration Manager 버전 1902 업데이트 롤업(4500571)을 설치합니다. 이 업데이트에 대한 자세한 내용은 [Configuration Manager 현재 분기 버전 1902에 대한 업데이트 롤업](https://support.microsoft.com/help/4500571)을 참조하세요.

1. 1902 버전용 업데이트 롤업을 사용하여 사이트를 업데이트합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  


### <a name="connect-to-the-service"></a>서비스에 연결

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 리본 메뉴에서 **Azure 서비스 구성**을 선택합니다.  

2. Azure 서비스 마법사의 **Azure 서비스** 페이지에서 다음 설정을 구성합니다.  

    - Configuration Manager의 개체에 대한 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되는 선택적 **설명**을 지정합니다.  

    - 사용 가능한 서비스 목록에서 **Desktop Analytics**를 선택합니다.  
  
   **다음**을 선택합니다.  

3. **앱** 페이지에서 적절한 **Azure 환경**을 선택합니다. 그런 다음, 웹앱에 대한 **찾아보기**를 선택합니다.

4. **만들기**를 선택하여 Desktop Analytics 연결에 사용할 Azure AD 앱을 쉽게 추가합니다.

5. **서버 애플리케이션 만들기** 창에서 다음 설정을 구성합니다.  

    - **애플리케이션 이름**: Azure AD의 앱에 대한 식별 이름입니다.

    - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. 서비스에 대한 액세스를 요청하기 위해 Configuration Manager 클라이언트에서 사용하는 액세스 토큰에 있습니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.  

    **로그인**을 선택합니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다.

    > [!Note]  
    > 이 단계는 **글로벌 관리자** 권한으로 수행합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다.  

    **확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. [서버 앱] 대화 상자에서 **확인**을 선택합니다. 그런 다음, Azure 서비스 마법사의 [앱] 페이지에서 **다음**을 선택합니다.  

6. **진단 데이터** 페이지에서 다음 설정을 구성합니다.  

    - **상업용 ID**: 이 값은 조직의 ID로 자동으로 채워집니다.  

    - **Windows 10 진단 데이터 수준**: **향상됨(제한됨)** 이상을 선택합니다.  

    - **진단 데이터에 디바이스 이름 허용**: **사용**을 선택합니다.  
  
   **다음**을 선택합니다. **사용 가능한 기능** 페이지에는 이전 페이지의 진단 데이터 설정에서 사용할 수 있는 Desktop Analytics 기능이 표시됩니다. **다음**을 선택합니다.  

7. **컬렉션** 페이지에서 다음 설정을 구성합니다.  

    - **표시 이름**: Desktop Analytics 포털에서 이 이름을 사용하여 이 Configuration Manager 연결을 표시합니다. 이를 사용하여 서로 다른 계층을 구분합니다. 예를 들어 *테스트 랩* 또는 *프로덕션*입니다.  

    - **대상 컬렉션**: 이 컬렉션에는 Configuration Manager에서 상업용 ID 및 진단 데이터 설정으로 구성하는 모든 디바이스가 포함됩니다. 이는 Configuration Manager에서 Desktop Analytics 서비스에 연결하는 전체 디바이스 세트입니다.  

    - **대상 컬렉션의 디바이스에서 아웃바운드 통신에 사용자 인증 프록시 사용**: 이 값은 기본적으로 **아니요**입니다. 사용자 환경에 필요한 경우 **예**로 설정합니다.  

    - **대상 컬렉션의 디바이스에서 아웃바운드 통신에 사용자 인증 프록시 사용**: 추가 컬렉션을 포함하려면 **추가**를 선택합니다. 이러한 컬렉션은 Desktop Analytics 포털에서 배포 계획과 그룹화할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함해야 합니다.  

        멤버 자격이 변경됨에 따라 이러한 컬렉션도 계속 동기화됩니다. 예를 들어 배포 계획에서는 Windows 7 멤버 자격 규칙이 있는 컬렉션을 사용합니다. 이러한 디바이스가 Windows 10으로 업그레이드되고 Configuration Manager에서 컬렉션 멤버 자격을 평가하면 해당 디바이스는 컬렉션 및 배포 계획에서 제외됩니다.  

8. 마법사를 완료합니다.  

Configuration Manager는 대상 컬렉션에서 디바이스를 구성하는 설정 정책을 만듭니다. 이 정책에는 디바이스에서 Microsoft로 데이터를 보낼 수 있도록 하는 진단 데이터 설정이 포함되어 있습니다. 클라이언트는 기본적으로 1시간마다 정책을 업데이트합니다. 새 설정을 받은 후 Desktop Analytics에서 데이터를 사용할 수 있을 때까지 몇 시간이 더 걸릴 수 있습니다.

> [!Note]  
> 이러한 설정에 대한 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조하세요.  

Desktop Analytics에 대한 디바이스 구성을 모니터링합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **Desktop Analytics 서비스** 노드를 펼치고, **연결 상태** 대시보드를 선택합니다.  

Configuration Manager는 연결을 만든 후 60분 이내에 컬렉션을 동기화합니다. Desktop Analytics 포털에서 **글로벌 파일럿**으로 이동하여 Configuration Manager 디바이스 컬렉션을 확인합니다.


## <a name="create-a-desktop-analytics-deployment-plan"></a>Desktop Analytics 배포 계획 만들기

다음 절차를 사용하여 Desktop Analytics에서 배포 계획을 만듭니다.

1. [Desktop Analytics 포털](https://aka.ms/desktopanalytics)을 엽니다. **작업 영역 기여자** 권한 이상의 자격 증명을 사용합니다.  

2. 관리 그룹에서 **배포 계획**을 선택합니다.  

3. **배포 계획** 창에서 **만들기**를 선택합니다.  

4. **배포 계획 만들기** 창에서 다음 설정을 구성합니다.  

    - **이름**: 배포 계획의 고유한 이름입니다(예: `Windows 10 pilot`).  

    - **제품 및 버전**: **Windows** 제품 및 사용 가능한 최신 추천 버전을 선택합니다. 예를 들어 **Windows 10, 버전 1809(추천)** 가 있습니다.  

    - **디바이스 그룹**: Configuration Manager 탭에서 하나 이상의 그룹을 선택한 다음, **대상 그룹으로 설정**을 선택합니다. 이러한 그룹은 Configuration Manager에서 동기화된 컬렉션입니다.  

    - **준비 규칙**: 이러한 규칙은 업그레이드에 적합한 디바이스를 결정하는 데 도움이 됩니다. **WIndows OS**를 선택하고, 다음 설정을 구성합니다.  

        - **Windows 업데이트에서 자동으로 드라이버 받기**: 기본 설정은 **끄기**입니다. 이 설정은 Configuration Manager를 사용하여 배포할 때 추천됩니다.  

        - **앱에 대한 낮은 설치 횟수 임계값을 정의합니다**: 기본 설정은 `2%`입니다. 이 임계값보다 낮은 앱은 자동으로 *낮은 설치 수*로 설정됩니다. Desktop Analytics는 파일럿 중에 이러한 추가 기능의 유효성을 검사하지 않습니다.  

            앱이 이 임계값보다 높은 비율의 컴퓨터에 설치된 경우 배포 계획에서 앱을 *중요*로 표시합니다. 그런 다음, 파일럿 단계에서 테스트의 중요도를 결정할 수 있습니다.  

    - **완료 날짜**: Windows를 모든 대상 디바이스에 완전히 배포해야 하는 날짜를 선택합니다.  

5. **만들기**를 선택합니다. 새 계획이 처리되는 동안 배포 계획 목록에 표시됩니다. 빠른 처리를 위해 요청 시 데이터 새로 고침을 요청합니다. 자세한 내용은 [Desktop Analytics FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조하세요.

6. 해당 이름을 선택하여 배포 계획을 엽니다.  

7. 배포 계획 메뉴의 **준비** 그룹에서 **중요도 식별**을 선택합니다.  

    1. **앱** 탭에서 **검토되지 않음** 자산만 표시하도록 선택합니다.  

    2. 각 앱을 선택한 다음, **편집**을 선택합니다. 둘 이상의 앱을 동시에 편집하도록 선택할 수 있습니다.  

    3. **중요도** 목록에서 중요도 수준을 선택합니다. 파일럿 중에 Desktop Analytics를 통해 앱의 유효성을 검사하려면 **위험** 또는 **중요**를 선택합니다. **중요하지 않음**으로 표시된 앱의 유효성은 검사하지 않습니다. 중요도 수준을 할당할 때 [호환성](/sccm/desktop-analytics/compat-assessment) 및 기타 계획 인사이트를 평가합니다.  

        중요도 수준을 할당할 때 [업그레이드] 결정을 선택할 수도 있습니다.  

    4. 완료되면 **저장**을 선택합니다.  

8. 배포 계획 메뉴의 **준비** 그룹에서 **파일럿 식별**을 선택합니다.  

    1. 파일럿에 추천되는 디바이스를 검토합니다.  

    2. 각 디바이스를 선택하고, **파일럿에 추가**를 선택합니다. 추천 사항에 동의하지 않으면 **바꾸기**를 선택합니다.  

        Desktop Analytics에서 이러한 추천 사항을 적용하는 방법에 대한 자세한 내용은 **파일럿 식별** 창의 오른쪽 위 모서리에 있는 정보 아이콘을 선택합니다.



## <a name="deploy-windows-10-in-configuration-manager"></a>Configuration Manager에서 Windows 10 배포

다음 절차를 사용하여 Configuration Manager에서 Windows 10을 파일럿 그룹에 배포합니다.

- 아직 없는 경우 먼저 [Windows 10용 OS 업그레이드 패키지를 만듭니다](#bkmk_create-package).  

- 아직 없는 경우 [Windows 10용 OS 업그레이드 작업 순서를 만듭니다](#bkmk_create-ts).  

- Desktop Analytics 배포 계획을 사용하여 [작업 순서를 배포합니다](#bkmk_deploy-ts).  

- 소프트웨어 센터에서 대상 디바이스에 [작업 순서를 설치합니다](#bkmk_install-ts).  

<!-- 
- [Monitor](#bkmk_monitor-ts) status in Configuration Manager  
 -->

### <a name="bkmk_create-package"></a> Windows 10용 OS 업그레이드 패키지 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **운영 체제**를 확장한 다음, **운영 체제 업그레이드 패키지** 노드를 선택합니다.  

2. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **운영 체제 업그레이드 패키지 추가**를 선택합니다. 그러면 운영 체제 업그레이드 추가 마법사가 시작됩니다.  

3. **데이터 원본** 페이지에서 OS 업그레이드 패키지의 설치 원본 파일에 대한 네트워크 **경로**를 지정합니다. 예: `\\server\share\path`  

    > [!NOTE]  
    > 설치 원본 파일에는 OS를 설치하는 setup.exe와 다른 파일 및 폴더가 포함되어 있습니다.  

4. **일반** 페이지에서 OS 업그레이드 패키지의 고유한 **이름**을 지정합니다.  

5. 운영 체제 업그레이드 패키지 추가 마법사를 완료합니다.  

#### <a name="distribute-content"></a>콘텐츠 배포

다음으로, OS 업그레이드 패키지를 배포 지점에 배포합니다.  

1. 목록에서 OS 업그레이드 패키지를 선택합니다. 리본의 **홈** 탭에 있는 **배포** 그룹에서 **콘텐츠 배포**를 선택합니다. 콘텐츠 배포 마법사를 엽니다.  

2. **일반** 페이지에서 나열된 콘텐츠가 배포하려는 콘텐츠인지 확인하고, **다음**을 선택합니다.  

3. **콘텐츠 대상** 페이지에서 **추가**, **배포 지점**을 차례로 선택합니다. 기존 배포 지점을 선택한 다음, **확인**을 선택합니다. 콘텐츠 대상 추가가 완료되면 **다음**을 선택합니다.  

4. 콘텐츠 배포 마법사를 완료합니다.  


### <a name="bkmk_create-ts"></a> Windows 10용 OS 업그레이드 작업 순서 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장한 다음 **작업 순서**를 선택합니다.  

2. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **작업 순서 만들기**를 선택합니다.  

3. 작업 순서 만들기 마법사의 **새 작업 순서 만들기** 페이지에서 **업그레이드 패키지에서 운영 체제 업그레이드**를 선택한 다음, **다음**을 선택합니다.  

4. **작업 순서 정보** 페이지에서 작업 순서를 식별하는 **작업 순서 이름**을 지정합니다.  

5. **Windows 운영 체제 업그레이드** 페이지에서 다음 설정을 지정하고, **다음**을 선택합니다.  

    - **업그레이드 패키지**:  OS 업그레이드 원본 파일이 포함된 업그레이드 패키지를 지정합니다.  

    - **버전 인덱스**: 패키지에서 사용할 수 있는 OS 버전 인덱스가 여러 개 있는 경우 원하는 버전 인덱스를 선택합니다. 기본적으로 마법사는 첫 번째 인덱스를 선택합니다.  

    - **제품 키**: 설치할 OS의 Windows 제품 키를 지정합니다. 인코딩된 볼륨 라이선스 키 또는 표준 제품 키를 지정하세요. 표준 제품 키를 사용하는 경우 5자로 이루어진 각 그룹을 대시(-)로 구분 합니다. 예: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. 볼륨 라이선스 버전용 업그레이드의 경우에는 제품 키가 필요하지 않을 수 있습니다.  

        > [!Note]  
        > 이 제품 키는 MAK(복수 정품 인증 키) 또는 GVLK(일반 볼륨 라이선스 키)일 수 있습니다. GVLK는 또한 KMS(키 관리 서비스) 클라이언트 설정 키라고도 합니다. 자세한 내용은 [볼륨 활성화 계획](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client)을 참조하세요. KMS 클라이언트 설정 키의 목록은 Windows Server 정품 인증 가이드의 [부록 A](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys)를 참조하세요.

6. **업데이트 포함** 페이지에서 **다음**을 선택하여 소프트웨어 업데이트를 설치하지 않습니다.  

7. **애플리케이션 설치** 페이지에서 **다음**을 선택하여 애플리케이션을 설치하지 않습니다.

8. 작업 순서 만들기 마법사를 완료합니다.  


### <a name="bkmk_deploy-ts"></a> Desktop Analytics 배포 계획을 사용하여 작업 순서 배포

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**로 이동하여 **Desktop Analytics 서비스**를 펼치고, **배포 계획** 노드를 선택합니다.  

2. Windows 10 파일럿 배포 계획을 선택한 다음, 리본에서 **배포 계획 세부 정보**를 선택합니다.  

3. **파일럿 상태** 타일의 드롭다운 목록에서 **작업 순서**를 선택한 다음, **배포**를 선택합니다.  

4. 소프트웨어 배포 마법사의 **일반** 페이지에서 **소프트웨어** 필드 옆에 있는 **찾아보기**를 선택합니다. Windows 10 전체 업그레이드 작업 순서를 선택하고, **다음**을 선택합니다.  

    > [!Note]  
    > Desktop Analytics 통합을 사용하면 Configuration Manager에서 배포 계획에 대한 파일럿 및 프로덕션 컬렉션을 자동으로 만듭니다. 이러한 컬렉션을 동기화하여 사용할 수 있을 때까지 시간이 걸릴 수 있습니다. 자세한 내용은 [문제 해결 - 데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조하세요.<!-- 4984639 -->
    >
    > 이 컬렉션은 Desktop Analytics 배포 계획 디바이스용으로 예약되어 있습니다. 이 컬렉션에 대한 수동 변경은 지원되지 않습니다.<!-- 3866460, SCCMDocs-pr 3544 -->  

5. **콘텐츠** 페이지에서 **추가**, **배포 지점**을 차례로 선택합니다. 설치 콘텐츠를 호스팅하는 데 사용할 수 있는 배포 지점을 선택하고, **확인**을 선택합니다. **다음**을 선택합니다.  

6. **배포 설정** 페이지에서 **다음**을 선택하여 기본 설정을 적용합니다. (사용 가능한 설치입니다.)  

7. **일정 예약** 페이지에서 **다음**을 선택하여 기본 설정을 적용합니다. (가능한 한 빨리 사용할 수 있습니다.)  

8. **사용자 환경** 페이지에서 **다음**을 선택하여 기본 설정을 적용합니다. (소프트웨어 센터에 표시되며, 컴퓨터 다시 시작에 대한 알림만 표시합니다.)  

9. **경고** 페이지에서 **다음**을 선택하여 기본 설정을 적용합니다.  

10. 마법사를 완료합니다.  


### <a name="bkmk_install-ts"></a> 소프트웨어 센터에서 작업 순서 설치

1. 파일럿 배포 계획의 멤버인 디바이스에 로그인합니다.  

2. **소프트웨어 센터**를 열고, Windows 10에 사용할 수 있는 운영 체제를 설치합니다.  


<!--
### <a name="bkmk_monitor-app"></a> Monitor status in Configuration Manager
-->


## <a name="next-steps"></a>다음 단계

Desktop Analytics 배포 계획에 대해 자세히 알아보려면 다음 문서로 계속 진행하세요.
> [!div class="nextstepaction"]  
> [배포 계획](/sccm/desktop-analytics/about-deployment-plans)
