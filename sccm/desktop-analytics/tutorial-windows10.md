---
title: 자습서-Windows 10 배포
titleSuffix: Configuration Manager
description: 데스크톱 분석 및 Configuration Manager를 사용 하 여 파일럿 그룹에 Windows 10을 배포 하는 방법에 대 한 자습서입니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: tutorial
ms.assetid: 3e82cd96-0ce0-474a-a597-d65fceadc95a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c3e69f2403b3a937c0ad6ba4c913483eb5dfdb1
ms.sourcegitcommit: ef7800a294e5db5d751921c34f60296c1642fc1f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712513"
---
# <a name="tutorial-deploy-windows-10-to-pilot"></a>자습서: 파일럿에 Windows 10 배포

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

이 자습서에서는 데스크톱 분석 및 Configuration Manager를 사용 하 여 파일럿 그룹에 Windows 10을 배포 합니다. 클라우드 서비스를 통합 하 여 온-프레미스 제품으로 Windows를 배포 하기 위한 정보를 제공 하는 것을 강조 합니다. 데스크톱 분석을 사용 하 여 파일럿 그룹에 배치할 최적의 장치를 확인 합니다. 그런 다음 Configuration Manager를 사용 하 여 Windows를 사용 하 여 현재를 가져옵니다.

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.  

> [!div class="checklist"]  
> * Azure Portal에서 데스크톱 분석 설정  
> * 연결 Configuration Manager 및 장치 설정 구성  
> * Windows 10 용 데스크톱 분석 배포 계획 만들기  
> * Configuration Manager를 사용 하 여 파일럿 그룹에 Windows 10 배포  

Azure 구독이 없는 경우 시작 하기 전에 [무료 계정](https://azure.microsoft.com/free) 을 만듭니다. 올바르게 구성 된 경우 데스크톱 분석을 사용 하면 Azure 비용이 발생 하지 않습니다.

데스크톱 분석은 Azure 구독에서 *Log Analytics 작업 영역* 을 사용 합니다. 작업 영역은 기본적으로 계정에 대 한 간단한 구성 정보와 계정 정보를 포함 하는 컨테이너입니다. 자세한 내용은 [작업 영역 관리](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-access?toc=/azure/azure-monitor/toc.json)를 참조 하세요.



## <a name="prerequisites"></a>필수 구성 요소

이 자습서를 시작 하기 전에 다음과 같은 필수 구성 요소가 있는지 확인 하세요.  

- [**전역 관리자**](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator) 권한이 있는 활성 Azure 구독  

    자세한 내용은 [데스크톱 분석 필수 조건](/sccm/desktop-analytics/overview#prerequisites)을 참조 하세요.

- Configuration Manager, 버전 1902 (업데이트 롤업 (4500571) 이상, **전체 관리자** 역할 포함)  

- 최신 버전의 Windows 10 용 설치 미디어

- 다음 구성을 사용 하는 Windows 10 장치 하나 이상:  

    - Windows 10 버전 1709 이상 (사용 하려는 설치 미디어 버전 보다 작음)

    - 최신 Windows 10 누적 품질 업데이트  

    - 업데이트 롤업 (4500571) 이상을 사용 하 여 클라이언트 버전 1902 Configuration Manager  

- 파일럿 장치에서 Windows 진단 데이터 수준을 **강화 (제한)** 하도록 구성 하는 비즈니스 승인  

    자세한 내용은 [데스크톱 분석 개인 정보](/sccm/desktop-analytics/privacy)를 참조 하세요.

- 장치에서 다음 인터넷 끝점으로의 네트워크 연결:

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
    - `https://graph.windows.net`(Configuration Manager 서버 역할만 해당)
    - `https://fef.msua06.manage.microsoft.com`(Configuration Manager 서버 역할만 해당)

    자세한 내용은 [데스크톱 분석을 위해 데이터 공유를 사용 하도록 설정 하는 방법](/sccm/desktop-analytics/enable-data-sharing#endpoints)을 참조 하세요.  

> [!Important]  
> 이러한 필수 구성 요소는이 자습서의 목적을 위한 것입니다. Configuration Manager 사용 하는 데스크톱 분석의 일반적인 필수 구성 요소에 대 한 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조 하세요.  



## <a name="set-up-desktop-analytics"></a>Desktop Analytics 설정

이 절차를 사용 하 여 데스크톱 분석에 로그인 하 고 구독에서 구성 합니다. 이 절차는 조직에 대 한 데스크톱 분석을 설정 하는 일회성 프로세스입니다.  

1. **전역 관리자** 권한이 있는 사용자로 Microsoft 365 장치 관리에서 [데스크톱 분석 포털](https://aka.ms/desktopanalytics) 을 엽니다. **시작**을 선택 합니다.  

2. **서비스 계약 수락** 페이지에서 서비스 계약을 검토 하 고 **동의**를 선택 합니다.  

3. **구독 확인** 페이지에서 필요한 정식 라이선스 목록은 데스크톱 분석의 Windows 장치 상태 기능에 대 한 것입니다. 계속하려면 **다음**을 선택합니다.  

4. 사용자에 게 **액세스 권한 부여** 페이지에서 다음을 수행 합니다.

    - **데스크톱 분석에서 사용자 대신 디렉터리 역할을 관리할 수 있도록 허용**: 데스크톱 분석은 **작업 영역 소유자** 에 게 자동으로 **데스크톱 분석 관리자** 역할을 할당 합니다. 해당 그룹이 이미 **전역 관리자**인 경우에는 변경 내용이 없습니다.  

        이 옵션을 선택 하지 않으면 데스크톱 분석에서 여전히 사용자를 보안 그룹의 구성원으로 추가 합니다. **전역 관리자** 는 사용자에 대 한 **데스크톱 분석 관리자** 역할을 수동으로 할당 해야 합니다.  

        Azure Active Directory에서 관리자 역할 사용 권한을 할당 하는 방법과 **데스크톱 분석 관리자**에 게 할당 된 사용 권한에 대 한 자세한 내용은 [Azure Active Directory의 관리자 역할 권한](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)을 참조 하세요.  

    - 데스크톱 분석은 Azure Active Directory의 **작업 영역 소유자** 보안 그룹을 미리 구성 하 여 작업 영역 및 배포 계획을 만들고 관리 합니다. 

        그룹에 사용자를 추가 하려면 **이름 또는 전자 메일 주소 입력** 섹션에 해당 이름 또는 전자 메일 주소를 입력 합니다. 완료 되 면 **다음**을 선택 합니다.

5. 페이지에서 **작업 영역을 설정**합니다.  

    > [!Note]  
    > 이 단계를 완료 하려면 사용자에 게 **작업 영역 소유자** 권한 및 Azure 구독 및 리소스 그룹에 대 한 추가 액세스 권한이 필요 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조 하세요.  

    - Azure 구독을 선택 합니다.  

    - 데스크톱 분석에 기존 작업 영역을 사용 하려면 해당 작업 영역을 선택 하 고 다음 단계를 계속 진행 합니다.  

    - 데스크톱 분석의 작업 영역을 만들려면 **작업 영역 추가**를 선택 합니다.  

        1. **작업 영역 이름을**입력 합니다.  

        2. 드롭다운 목록을 선택 하 여 **이 작업 영역에 대 한 azure 구독 이름을 선택**하 고이 작업 영역에 대 한 azure 구독을 선택 합니다.  

        3. **새로 만들기** 리소스 그룹 또는 **기존**리소스 그룹을 사용 합니다.  

        4. 목록에서 **지역을** 선택 하 고 **추가**를 선택 합니다.  

6. 새 또는 기존 작업 영역을 선택한 다음 **데스크톱 분석 작업 영역으로 설정**을 선택 합니다.  그런 다음 **액세스 확인 및 부여** 대화 상자에서 **계속** 을 선택 합니다.  

7. 새 브라우저 탭에서 로그인 하는 데 사용할 계정을 선택 합니다. **조직을 대신** 하 여 동의 하는 옵션을 선택 하 고 **동의**를 선택 합니다.  


    > [!Note]  
    > 이러한 동의는 MALogAnalyticsReader 응용 프로그램에 작업 영역에 대 한 Log Analytics 판독기 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석에 필요 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)을 참조 하세요.  

8. 페이지로 돌아가 **작업 영역을 설정**하 고 **다음**을 선택 합니다.  

9. **마지막 단계** 페이지에서 **데스크톱 분석으로 이동**을 선택 합니다. Azure Portal에는 데스크톱 분석 **홈** 페이지가 표시 됩니다.  



## <a name="connect-configuration-manager"></a>Configuration Manager 연결

이 절차를 사용 하 여 Configuration Manager를 업데이트 하 고, 데스크톱 분석에 연결 하 고, 장치 설정을 구성할 수 있습니다. 이 절차는 계층을 클라우드 서비스에 연결 하는 일회성 프로세스입니다.  

### <a name="update-configuration-manager"></a>업데이트 Configuration Manager

데스크톱 분석과의 통합을 지원 하기 위해 Configuration Manager 버전 1902 업데이트 롤업 (4500571)을 설치 합니다. 이 업데이트에 대 한 자세한 내용은 [Configuration Manager 현재 분기에 대 한 업데이트 롤업, 버전 1902](https://support.microsoft.com/help/4500571)을 참조 하세요.

1. 1902 버전에 대 한 업데이트 롤업을 사용 하 여 사이트를 업데이트 합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  


### <a name="connect-to-the-service"></a>서비스에 연결

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 리본에서 **Azure 서비스 구성** 을 선택 합니다.  

2. Azure 서비스 마법사의 **Azure 서비스** 페이지에서 다음 설정을 구성 합니다.  

    - Configuration Manager에서 개체의 **이름을** 지정 합니다.  

    - 서비스를 식별 하는 데 도움이 되는 **설명** (선택 사항)을 지정 합니다.  

    - 사용 가능한 서비스 목록에서 **데스크톱 분석** 을 선택 합니다.  
  
   **다음**을 선택합니다.  

3. **앱** 페이지에서 적절 한 **Azure 환경을**선택 합니다. 그런 다음 웹 앱 **찾아보기** 를 선택 합니다.

4. **만들기** 를 선택 하 여 데스크톱 분석 연결에 대 한 Azure AD 앱을 쉽게 추가 합니다.

5. **서버 응용 프로그램 만들기** 창에서 다음 설정을 구성 합니다.  

    - **애플리케이션 이름**: Azure AD의 앱에 대 한 친숙 한 이름입니다.

    - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. Configuration Manager 클라이언트에서 서비스에 대 한 액세스를 요청 하는 데 사용 하는 액세스 토큰입니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.  

    **로그인**을 선택 합니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다.

    > [!Note]  
    > **전역 관리자 권한**으로이 단계를 완료 합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다.  

    **확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. 서버 앱 대화 상자에서 **확인**을 선택 합니다. 그런 후에 Azure 서비스 마법사의 앱 페이지에서 **다음** 을 선택 합니다.  

6. **진단 데이터** 페이지에서 다음 설정을 구성 합니다.  

    - **상용 ID**:이 값은 자동으로 조직의 id로 채워집니다.  

    - **Windows 10 진단 데이터 수준**: 최소 **확장 (제한 됨)** 을 선택 합니다.  

    - **진단 데이터에서 장치 이름 허용**: **사용** 을 선택 합니다.  
  
   **다음**을 선택합니다. **사용 가능한 기능** 페이지에는 이전 페이지의 진단 데이터 설정에서 사용할 수 있는 데스크톱 분석 기능이 표시 됩니다. **다음**을 선택합니다.  

7. **컬렉션** 페이지에서 다음 설정을 구성 합니다.  

    - **표시 이름**: 데스크톱 분석 포털은이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다. 이를 사용 하 여 서로 다른 계층을 구분 합니다. 예: *테스트 랩* 또는 *프로덕션*.  

    - **대상 컬렉션**: 이 컬렉션에는 상업적 ID 및 진단 데이터 설정 Configuration Manager 구성 하는 모든 장치가 포함 됩니다. Configuration Manager는 데스크톱 분석 서비스에 연결 하는 전체 장치 집합입니다.  

    - **대상 컬렉션의 장치는 아웃 바운드 통신에 사용자 인증 프록시를 사용**합니다. 기본적으로이 값은 **아니요**입니다. 사용자 환경에 필요한 경우를 **예**로 설정 합니다.  

    - **데스크톱 분석과 동기화 할 특정 컬렉션 선택**: 추가 컬렉션을 포함 하려면 **추가** 를 선택 합니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화 하기 위해 데스크톱 분석 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  

        이러한 컬렉션은 멤버 자격 변경 내용에 따라 계속 동기화 됩니다. 예를 들어 배포 계획에서는 Windows 7 멤버 자격 규칙을 사용 하는 컬렉션을 사용 합니다. 이러한 장치는 Windows 10으로 업그레이드 되 고 Configuration Manager 컬렉션 멤버 자격을 평가 하므로 해당 장치는 수집 및 배포 계획에서 제외 됩니다.  

8. 마법사를 완료합니다.  

Configuration Manager 대상 컬렉션에서 장치를 구성 하는 설정 정책을 만듭니다. 이 정책에는 장치에서 Microsoft로 데이터를 보낼 수 있도록 진단 데이터 설정이 포함 되어 있습니다. 기본적으로 클라이언트는 매시간 정책을 업데이트 합니다. 새 설정을 받은 후에는 데스크톱 분석에서 데이터를 사용할 수 있을 때까지 몇 시간이 걸릴 수 있습니다.

> [!Note]  
> 이러한 설정에 대 한 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조 하세요.  

데스크톱 분석에 대 한 장치의 구성을 모니터링 합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **데스크톱 분석 서비스** 노드를 확장 하 고 **연결 상태** 대시보드를 선택 합니다.  

Configuration Manager는 연결을 만들 때 60 분 이내에 컬렉션을 동기화 합니다. 데스크톱 분석 포털에서 **전역 파일럿**으로 이동 하 여 Configuration Manager 장치 컬렉션을 확인 합니다.


## <a name="create-a-desktop-analytics-deployment-plan"></a>데스크톱 분석 배포 계획 만들기

데스크톱 분석에서 배포 계획을 만들려면 다음 절차를 따르십시오.

1. [데스크톱 분석 포털](https://aka.ms/desktopanalytics)을 엽니다. 적어도 **작업 영역 참가자** 권한이 있는 자격 증명을 사용 합니다.  

2. 관리 그룹에서 **배포 계획** 을 선택 합니다.  

3. **배포 계획** 창에서 **만들기**를 선택 합니다.  

4. **배포 계획 만들기** 창에서 다음 설정을 구성 합니다.  

    - **이름**: 배포 계획에 대 한 고유한 이름 (예:)`Windows 10 pilot`  

    - **제품 및 버전**: **Windows** 제품을 선택 하 고 사용 가능한 최신 버전을 선택 합니다. 예를 들어 **Windows 10, 버전 1809 (권장)** 입니다.  

    - **장치 그룹**: Configuration Manager 탭에서 그룹을 하나 이상 선택한 다음 **대상 그룹으로 설정**을 선택 합니다. 이러한 그룹은 Configuration Manager에서 동기화 되는 컬렉션입니다.  

    - **준비 규칙**: 이러한 규칙은 업그레이드를 위해 자격이 있는 장치를 확인 하는 데 도움이 됩니다. **WINDOWS OS** 를 선택 하 고 다음 설정을 구성 합니다.  

        - **내 컴퓨터가 자동으로 Windows 업데이트에서 드라이버를 가져옵니다**. 기본 설정은 **해제**이며 Configuration Manager를 사용 하 여 배포할 때 권장 됩니다.  

        - **앱에 대 한 낮은 설치 수 임계값을 정의 합니다**. 기본 설정은 `2%`입니다. 이 임계값 이하의 앱은 자동으로 *낮은 설치 수*로 설정 됩니다. 데스크톱 분석은 파일럿 동안 이러한 추가 기능의 유효성을 검사 하지 않습니다.  

            앱이이 임계값 보다 더 높은 비율의 컴퓨터에 설치 된 경우 배포 계획에서 앱을 *주목할 만한*것으로 표시 합니다. 그런 다음 파일럿 단계에서 테스트할 중요도를 결정할 수 있습니다.  

    - **완료 날짜**: 모든 대상 장치에 Windows를 완전히 배포 해야 하는 날짜를 선택 합니다.  

5. **만들기**를 선택합니다. 새 계획은 처리 중인 배포 계획 목록에 표시 됩니다. 신속한 처리를 위해 요청 시 데이터 새로 고침을 요청 합니다. 자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조 하세요.

6. 이름을 선택 하 여 배포 계획을 엽니다.  

7. 배포 계획 메뉴의 **준비** 그룹에서 **중요도 식별**을 선택 합니다.  

    1. **앱** 탭에서 **검토 되지 않은** 자산만 표시 하도록 선택 합니다.  

    2. 각 앱을 선택 하 고 **편집**을 선택 합니다. 동시에 둘 이상의 앱을 편집 하도록 선택할 수 있습니다.  

    3. **중요도** 목록에서 중요도 수준을 선택 합니다. 파일럿 중에 데스크톱 분석을 통해 앱의 유효성을 검사 하려면 **위험** 또는 **중요**를 선택 합니다. **중요 하지 않은**것으로 표시 된 앱은 유효성을 검사 하지 않습니다. 중요도 수준을 할당할 때 [호환성](/sccm/desktop-analytics/compat-assessment) 및 기타 계획 정보를 평가 합니다.  

        중요도 수준을 할당할 때 업그레이드 결정을 선택할 수도 있습니다.  

    4. 완료 되 면 **저장** 을 선택 합니다.  

8. 배포 계획 메뉴의 **준비** 그룹에서 **파일럿 식별**을 선택 합니다.  

    1. 파일럿에 권장 되는 장치를 검토 합니다.  

    2. 각 장치를 선택 하 고 **파일럿에 추가를**선택 합니다. 권장 사항에 동의 하지 않는 경우 **바꾸기**를 선택 합니다.  

        데스크톱 분석에서 이러한 권장 사항을 적용 하는 방법에 대 한 자세한 내용은 **파일럿 식별** 창의 오른쪽 위 모퉁이에 있는 정보 아이콘을 선택 합니다.



## <a name="deploy-windows-10-in-configuration-manager"></a>Configuration Manager에서 Windows 10 배포

이 절차를 사용 하 여 Configuration Manager에서 Windows 10을 파일럿 그룹에 배포할 수 있습니다.

- 아직 없는 경우 먼저 [Windows 10 용 OS 업그레이드 패키지를 만듭니다](#bkmk_create-package) .  

- 아직 없는 경우 [Windows 10에 대 한 OS 업그레이드 작업 순서 만들기](#bkmk_create-ts)  

- 데스크톱 분석 배포 계획을 사용 하 여 [작업 순서 배포](#bkmk_deploy-ts)  

- 대상 장치의 소프트웨어 센터에서 [작업 순서 설치](#bkmk_install-ts)  

<!-- 
- [Monitor](#bkmk_monitor-ts) status in Configuration Manager  
 -->

### <a name="bkmk_create-package"></a>Windows 10 용 OS 업그레이드 패키지 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **운영 체제**를 확장한 다음, **운영 체제 업그레이드 패키지** 노드를 선택합니다.  

2. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **운영 체제 업그레이드 패키지 추가**를 선택합니다. 그러면 운영 체제 업그레이드 추가 마법사가 시작됩니다.  

3. **데이터 원본** 페이지에서 OS 업그레이드 패키지의 설치 원본 파일에 대 한 네트워크 **경로** 를 지정 합니다. `\\server\share\path` )을 입력합니다.  

    > [!NOTE]  
    > 설치 원본 파일에는 OS를 설치하는 setup.exe와 다른 파일 및 폴더가 포함되어 있습니다.  

4. **일반** 페이지에서 OS 업그레이드 패키지에 대 한 고유한 **이름을** 지정 합니다.  

5. 운영 체제 업그레이드 패키지 추가 마법사를 완료 합니다.  

#### <a name="distribute-content"></a>콘텐츠 배포

다음으로, OS 업그레이드 패키지를 배포 지점에 배포합니다.  

1. 목록에서 OS 업그레이드 패키지를 선택 합니다. 리본의 **홈** 탭에 있는 **배포** 그룹에서 **콘텐츠 배포**를 선택합니다. 콘텐츠 배포 마법사를 엽니다.  

2. **일반** 페이지에서 나열 된 콘텐츠가 배포 하려는 콘텐츠 인지 확인 하 고 **다음**을 선택 합니다.  

3. **콘텐츠 대상** 페이지에서 **추가**를 선택 하 고 **배포 지점**을 선택 합니다. 기존 배포 지점을 선택한 다음 **확인**을 선택 합니다. 콘텐츠 대상 추가를 마쳤으면 **다음**을 선택 합니다.  

4. 콘텐츠 배포 마법사를 완료 합니다.  


### <a name="bkmk_create-ts"></a>Windows 10에 대 한 OS 업그레이드 작업 순서 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **운영 체제**를 확장 하 고 **작업 순서**를 선택 합니다.  

2. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **작업 순서 만들기**를 선택 합니다.  

3. 작업 순서 만들기 마법사의 **새 작업 순서 만들기** 페이지에서 **업그레이드 패키지에서 운영 체제 업그레이드**를 선택 하 고 **다음**을 선택 합니다.  

4. 작업 **순서 정보** 페이지에서 작업 순서를 식별 하는 **작업 순서 이름을** 지정 합니다.  

5. **Windows 운영 체제 업그레이드** 페이지에서 다음 설정을 지정한 후에 다음 **을 선택 합니다**.  

    - **업그레이드 패키지**:  OS 업그레이드 원본 파일이 포함된 업그레이드 패키지를 지정합니다.  

    - **버전 인덱스**: 패키지에서 사용할 수 있는 OS 버전 인덱스가 여러 개 있는 경우 원하는 버전 인덱스를 선택합니다. 기본적으로 마법사는 첫 번째 인덱스를 선택합니다.  

    - **제품 키**: 설치할 OS의 Windows 제품 키를 지정합니다. 인코딩된 볼륨 라이선스 키 또는 표준 제품 키를 지정하세요. 표준 제품 키를 사용하는 경우 5자로 이루어진 각 그룹을 대시(-)로 구분 합니다. 예: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. 볼륨 라이선스 버전용 업그레이드의 경우에는 제품 키가 필요하지 않을 수 있습니다.  

        > [!Note]  
        > 이 제품 키는 MAK(복수 정품 인증 키) 또는 GVLK(일반 볼륨 라이선스 키)일 수 있습니다. GVLK는 또한 KMS(키 관리 서비스) 클라이언트 설정 키라고도 합니다. 자세한 내용은 [볼륨 활성화 계획](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client)을 참조하세요. KMS 클라이언트 설정 키의 목록은 Windows Server 정품 인증 가이드의 [부록 A](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys)를 참조하세요.

6. **업데이트 포함** 페이지에서 **다음** 을 선택 하 여 소프트웨어 업데이트를 설치 하지 않습니다.  

7. 응용 프로그램 **설치** 페이지에서 **다음** 을 선택 하 여 응용 프로그램을 설치 하지 않습니다.

8. 작업 순서 만들기 마법사를 완료 합니다.  


### <a name="bkmk_deploy-ts"></a>데스크톱 분석 배포 계획을 사용 하 여 작업 순서 배포

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**로 이동 하 여 **데스크톱 분석 서비스**를 확장 하 고 **배포 계획** 노드를 선택 합니다.  

2. Windows 10 파일럿 배포 계획을 선택 하 고 리본에서 **배포 계획 세부 정보** 를 선택 합니다.  

3. **파일럿 상태** 타일의 드롭다운 목록에서 **작업 순서** 를 선택 하 고 **배포**를 선택 합니다.  

4. 소프트웨어 배포 마법사의 **일반** 페이지에서 **소프트웨어** 필드 옆에 있는 **찾아보기** 를 선택 합니다. Windows 10 전체 업그레이드 작업 순서를 선택 하 고 **다음**을 선택 합니다.  

    > [!Note]  
    > 데스크톱 분석 통합을 사용 하면 Configuration Manager는 배포 계획에 대 한 파일럿 및 프로덕션 컬렉션을 자동으로 만듭니다. 이러한 컬렉션을 사용 하려면 이러한 컬렉션을 동기화 하는 데 시간이 오래 걸릴 수 있습니다. 자세한 내용은 [문제 해결-데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조 하세요.<!-- 4984639 -->
    >
    > 이 컬렉션은 데스크톱 분석 배포 계획 장치용으로 예약 되어 있습니다. 이 컬렉션에 대 한 수동 변경은 지원 되지 않습니다.<!-- 3866460, SCCMDocs-pr 3544 -->  

5. **콘텐츠** 페이지에서 **추가**를 선택한 후 **배포 지점**을 선택 합니다. 설치 콘텐츠를 호스트할 사용 가능한 배포 지점을 선택 하 고 **확인**을 선택 합니다. **다음**을 선택합니다.  

6. **배포 설정** 페이지에서 **다음** 을 선택 하 여 기본 설정을 적용 합니다. (사용 가능한 설치)  

7. **일정** 페이지에서 **다음** 을 선택 하 여 기본 설정을 적용 합니다. (가능한 한 빨리 사용 가능)  

8. **사용자 환경** 페이지에서 **다음** 을 선택 하 여 기본 설정을 적용 합니다. 소프트웨어 센터에 표시 되 고 컴퓨터를 다시 시작 하는 알림만 표시 됩니다.  

9. **경고** 페이지에서 **다음** 을 선택 하 여 기본 설정을 적용 합니다.  

10. 마법사를 완료합니다.  


### <a name="bkmk_install-ts"></a>소프트웨어 센터에서 작업 순서 설치

1. 파일럿 배포 계획의 구성원 인 장치에 로그인 합니다.  

2. **소프트웨어 센터** 를 열고 Windows 10 용으로 사용 가능한 운영 체제를 설치 합니다.  


<!--
### <a name="bkmk_monitor-app"></a> Monitor status in Configuration Manager
-->


## <a name="next-steps"></a>다음 단계

데스크톱 분석 배포 계획에 대 한 자세한 내용을 보려면 다음 문서로 이동 하세요.
> [!div class="nextstepaction"]  
> [배포 계획](/sccm/desktop-analytics/about-deployment-plans)
