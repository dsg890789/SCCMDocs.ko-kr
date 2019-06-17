---
title: 자습서-Windows 10 배포
titleSuffix: Configuration Manager
description: 데스크톱 분석 및 Configuration Manager를 사용 하 여 파일럿 그룹에 Windows 10을 배포 하는 자습서입니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: tutorial
ms.assetid: 3e82cd96-0ce0-474a-a597-d65fceadc95a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8b73deb60cf88f0bdf428bb87250ce115a1084b
ms.sourcegitcommit: d47d2f03482e48d343e2139a341e61022331e6c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67145827"
---
# <a name="tutorial-deploy-windows-10-to-pilot"></a>자습서: 파일럿을 Windows 10을 배포 합니다.

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

이 자습서는 파일럿 그룹에 Windows 10을 배포 하려면 데스크톱 분석 및 Configuration Manager를 사용 합니다. 온-프레미스 제품을 사용 하 여 Windows를 배포 하는 정보를 제공 하도록 클라우드 서비스의 통합 강조 표시 합니다. 파일럿 그룹에 배치할 최상의 장치를 확인 하려면 데스크톱 Analytics를 사용 합니다. 다음 Configuration Manager를 사용 하 여 Windows를 사용 하 여 현재 가져오려고 합니다.

이 자습서에 알아봅니다 방법:  

> [!div class="checklist"]  
> * Azure portal에서 데스크톱 분석 설정  
> * Configuration Manager를 연결 하 고 장치 설정 구성  
> * Windows 10 용 데스크톱 Analytics 배포 계획 만들기  
> * Configuration Manager를 사용 하 여 파일럿 그룹에 Windows 10을 배포 하려면  

Azure 구독이 없으면 만듭니다는 [무료 계정](https://azure.microsoft.com/free) 시작 하기 전에 합니다. 올바르게 구성 하는 경우 데스크톱 분석을 사용 하 여 한 Azure 요금이 부과 하지 않습니다.

데스크톱 Analytics를 사용 하는 *Log Analytics 작업 영역* Azure 구독에 있습니다. 작업 영역은 기본적으로 계정에 대 한 간단한 구성 정보와 계정 정보를 포함 하는 컨테이너입니다. 자세한 내용은 [작업 영역 관리](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-access?toc=/azure/azure-monitor/toc.json)합니다.



## <a name="prerequisites"></a>필수 구성 요소

이 자습서를 시작 하기 전에 다음 필수 구성 요소가 있는지 확인 합니다.  

- 활성 Azure 구독을 사용 하 여 [ **전역 관리자** ](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator) 권한  

    자세한 내용은 [데스크톱 Analytics 필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)합니다.

- Configuration Manager 업데이트 롤업 (4500571) 이상을 사용 하 여 버전 1902 **전체 관리자** 역할  

- Windows 10의 최신 버전은 설치 미디어

- 다음 구성이 포함 된 하나 이상의 Windows 10 장치:  

    - Windows 10 버전 1709 이상을 사용 하려면 설치 미디어의 버전 보다 낮은 하지만

    - 최신 Windows 10 누적 품질 업데이트  

    - Configuration Manager 클라이언트 버전 1902 업데이트 롤업 (4500571) 이상  

- Windows 진단 데이터 수준을 구성 하려면 비즈니스 승인 **고급 (제한적)** 파일럿 장치에서  

    자세한 내용은 [데스크톱 분석 개인 정보 보호](/sccm/desktop-analytics/privacy)합니다.

- 다음 인터넷 끝점에는 장치에서 네트워크 연결:

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
    - `https://graph.windows.net` (에서 Configuration Manager 서버 역할에만 해당)
    - `https://fef.msua06.manage.microsoft.com` (에서 Configuration Manager 서버 역할에만 해당)

    자세한 내용은 [데스크톱 분석에 대 한 공유 데이터를 사용 하도록 설정 하는 방법을](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  

> [!Important]  
> 이러한 필수 구성이 요소는이 자습서의 목적입니다. Configuration Manager에서 데스크톱 Analytics에 대 한 일반적인 필수 구성 요소에 대 한 자세한 내용은 참조 하세요. [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)합니다.  



## <a name="set-up-desktop-analytics"></a>Desktop Analytics 설정

데스크톱 분석에 로그인 하 고 구독에서 구성 하려면이 절차를 따르십시오. 이 절차는 조직에 대 한 데스크톱 Analytics를 설정 하는 일회성 프로세스입니다.  

1. 열기는 [데스크톱 Analytics 포털](https://aka.ms/desktopanalytics) 사용자로 Microsoft 365 장치 관리에서 **전역 관리자** 권한. 선택 **시작**합니다.  

2. 에 **서비스 계약에 동의** 페이지에서 서비스 계약을 검토 하 고 선택 **Accept**합니다.  

3. 에 **구독을 확인 하** 데스크톱 Analytics의 Windows 장치 상태 모니터링 기능에 대 한 페이지에서 필요한 정식 라이선스 목록이 됩니다. 계속하려면 **다음**을 선택합니다.  

4. 에 **사용자가 액세스할** 페이지:

    - **사용자에 대 한 디렉터리 역할을 관리 하려면 데스크톱 분석 하려는**: 데스크톱 Analytics 자동으로 할당 합니다 **작업 영역 소유자** 및 **작업 영역 참가자** 그룹을 **데스크톱 분석 관리자** 역할. 이러한 그룹은 이미 있는 경우는 **전역 관리자**, 변경 되지 않았습니다.  

        이 옵션을 선택 하지 않으면, 데스크톱 Analytics는 여전히 사용자 두 보안 그룹의 구성원으로 추가 합니다. A **전역 관리자** 수동으로 할당 해야 합니다 **데스크톱 분석 관리자** 사용자 역할.  

        Azure Active Directory에서 관리자 역할 권한 및 할당 된 권한을 할당 하는 방법에 대 한 자세한 내용은 **데스크톱 Analytics Administrators**를 참조 하세요 [azure에서 관리자 역할 권한 Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)합니다.  

    - 데스크톱 Analytics Azure Active Directory에서 두 개의 보안 그룹 같은 미리 구성합니다.:  

        - **작업 영역 소유자**: 보안 그룹을 만들고 작업 영역을 관리 합니다. 이러한 계정은 Azure 구독에 대 한 소유자 액세스를 해야합니다.  

        - **작업 영역 참가자**: 보안 그룹을 만들고이 작업 영역에서 배포 계획을 관리 합니다. 모든 추가 Azure 액세스할이 필요는 없습니다.  

        각 그룹에 사용자를 추가할에서 해당 이름 또는 전자 메일 주소를 입력 합니다 **이름 또는 전자 메일 주소 입력** 적절 한 그룹의 섹션입니다. 완료 되 면 선택 **다음**합니다.

5. 페이지에서 **작업 영역 설정**:  

    > [!Note]  
    > 이 단계를 완료 한 **작업 영역 소유자** 또는 **참가자**합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)합니다.  

    - Azure 구독을 선택 합니다.  

    - 기존 작업 영역에 데스크톱 Analytics를 사용 하려면를 선택 하 고 단계를 진행 합니다.  

    - 데스크톱 분석을 위해 작업 영역을 만들려면 **작업 영역 추가**합니다.  

        1. 입력 한 **작업 영역 이름**합니다.  

        2. 드롭다운 목록 선택 **이 작업 영역에 대 한 Azure 구독 이름을 선택**,이 작업 영역에 대 한 Azure 구독을 선택 합니다.  

        3. **새로 만들기** 리소스 그룹 또는 **기존 항목 사용**합니다.  

        4. 선택 된 **지역** 을 선택 하 고 목록에서 **추가**합니다.  

6. 새 또는 기존 작업 영역을 선택한 후 **데스크톱 Analytics 작업 영역으로 설정**합니다.  선택한 **계속** 에 **Confirm 및 권한 부여 액세스** 대화 합니다.  

7. 새 브라우저 탭에서 계정을 사용 하 여 로그인을 선택 합니다. 옵션을 선택 **조직을 대신 하 여 동의** 선택한 **Accept**합니다.  


    > [!Note]  
    > 이 동의 MALogAnalyticsReader 응용 프로그램 작업 영역에 대 한 Log Analytics Reader 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석 필요 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)입니다.  

8. 페이지에서 다시 **작업 영역 설정**를 선택 **다음**합니다.  

9. 에 **마지막 단계** 페이지에서 **Desktop Analytics로 이동**합니다. Azure portal에 데스크톱 분석을 보여 줍니다 **홈** 페이지입니다.  



## <a name="connect-configuration-manager"></a>Configuration Manager 연결

Configuration Manager 업데이트, 데스크톱 Analytics에 연결 및 장치 설정을 구성 하려면이 절차를 따르십시오. 이 절차는 계층 클라우드 서비스에 연결 하는 일회성 프로세스입니다.  

### <a name="update-configuration-manager"></a>Configuration Manager 업데이트

데스크톱 Analytics와의 통합을 지원 하기 위해 Configuration Manager 버전 1902 업데이트 롤업 (4500571)를 설치 합니다. 이 업데이트에 대 한 자세한 내용은 참조 하세요. [Configuration Manager 현재 분기, 버전 1902 용 업데이트 롤업](https://support.microsoft.com/help/4500571)합니다.

1. 1902 버전에 대 한 업데이트 롤업을 사용 하 여 사이트를 업데이트 합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  


### <a name="connect-to-the-service"></a>서비스에 연결

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 선택 **Azure 서비스 구성** 리본 메뉴에 있습니다.  

2. 에 **Azure Services** 페이지 Azure 서비스 마법사의 다음 설정을 구성 합니다.  

    - 지정 된 **이름을** in Configuration Manager 개체에 대 한  

    - 선택적인 지정할 **설명을** 서비스를 식별 하는 데  

    - 선택 **데스크톱 분석** 사용 가능한 서비스 목록에서  
  
   **다음**을 선택합니다.  

3. 에 **앱** 페이지에서 적절 한 선택 **Azure 환경**합니다. 선택한 **찾아보기** 웹 앱에 대 한 합니다.

4. 선택 **만들기** 쉽게 데스크톱 Analytics 연결에 대 한 Azure AD 앱을 추가 합니다.

5. 다음 설정을 구성 합니다 **서버 응용 프로그램 만들기** 창:  

    - **애플리케이션 이름**: Azure AD에 앱의 이름입니다.

    - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. 액세스 토큰에는 Configuration Manager 클라이언트에서 서비스에 대 한 액세스를 요청 하려면 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.  

    선택 **로그인**합니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다.

    > [!Note]  
    > 이 단계를 완료 한 **회사 관리자**합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다.  

    **확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. 서버 앱 대화 상자에서 선택 **확인**합니다. 선택한 **다음** Azure 서비스 마법사의 앱 페이지에 있습니다.  

6. 에 **진단 데이터** 페이지에서 다음 설정을 구성 합니다.  

    - **상업용 ID**:이 값은 조직의 ID를 사용 하 여 자동 채우기  

    - **Windows 10 진단 데이터 수준**: 하나 이상 선택 **고급 (제한적)**  

    - **장치 이름을 진단 데이터의 허용**: 선택 **사용 하도록 설정**  
  
   **다음**을 선택합니다. 합니다 **사용할 수 있는 기능** 페이지는 이전 페이지에서 진단 데이터 설정을 사용 하 여 사용할 수 있는 데스크톱 분석 기능을 보여 줍니다. **다음**을 선택합니다.  

7. 에 **컬렉션** 페이지에서 다음 설정을 구성 합니다.  

    - **표시 이름**: 데스크톱 Analytics 포털에이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다. 다른 계층 간에 구분 하기 위해 사용 합니다. 예를 들어 *테스트 랩을* 하거나 *프로덕션*합니다.  

    - **컬렉션을 대상**: 이 컬렉션에 진단 데이터 설정과 상업용 ID를 사용 하 여 Configuration Manager를 구성 하는 모든 장치를 포함 합니다. Configuration Manager에서 데스크톱 Analytics 서비스에 연결 하는 장치의 전체 집합은  

    - **아웃 바운드 통신에 대 한 사용자 인증 프록시를 사용 하는 대상 컬렉션의 장치**: 기본적으로이 값은 **No**합니다. 사용자 환경에서 필요한 경우로 **예**합니다.  

    - **데스크톱 Analytics와 동기화 하도록 특정 컬렉션 선택**: 선택 **추가** 추가 컬렉션을 포함 합니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화에 대 한 데스크톱 Analytics 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  

        이러한 컬렉션의 멤버 자격 변경으로 동기화 계속 합니다. 예를 들어 배포 계획을 Windows 7 멤버 관리 규칙을 사용 하 여 컬렉션을 사용 합니다. 해당 장치를 Windows 10으로 업그레이드 하 고 Configuration Manager 컬렉션 멤버 자격을 평가, 수집 및 배포 계획에서 해당 장치를 삭제 합니다.  

8. 마법사를 완료합니다.  

Configuration Manager에는 대상 컬렉션의 장치를 구성 하는 설정 정책을 만듭니다. 이 정책은 장치가 Microsoft에 데이터를 보낼 수 있도록 진단 데이터 설정을 포함 합니다. 기본적으로 클라이언트 1 시간 마다 정책을 업데이트합니다. 새 설정을 받은 후 데이터가 데스크톱 Analytics에서 사용할 수 있는 전에 몇 시간 더 많은 수 있습니다.

데스크톱 분석에 대 한 장치 구성을 모니터링 합니다. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **데스크톱 분석 서비스** 노드를 선택한는 **연결 상태** 대시보드입니다.  

Configuration Manager는 연결을 만드는 60 분 내 컬렉션을 동기화 합니다. 데스크톱 Analytics 포털에서로 이동 **전역 파일럿**, Configuration Manager 장치 컬렉션을 표시 합니다.


## <a name="create-a-desktop-analytics-deployment-plan"></a>데스크톱 Analytics 배포 계획 만들기

데스크톱 Analytics에서 배포 계획을 만들려면이 절차를 사용 합니다.

1. 엽니다는 [데스크톱 Analytics 포털](https://aka.ms/desktopanalytics)합니다. 최소 권한이 있는 자격 증명을 사용 하 여 **작업 영역 참가자** 권한.  

2. 선택 **배포 계획** 관리 그룹에 있습니다.  

3. 에 **배포 계획** 창 **만들기**합니다.  

4. 에 **배포 계획 만들기** 창 다음 설정을 구성 합니다.  

    - **이름**: 예를 들어 배포에 대 한 고유한 이름을 계획합니다 `Windows 10 pilot`  

    - **제품 및 버전**: 선택 된 **Windows** 제품 및 최신 권장된 버전입니다. 예를 들어 **Windows 10 버전 (권장) 1809**합니다.  

    - **장치 그룹**: 구성 관리자 탭에서 하나 이상의 그룹을 선택 하 고 선택한 **대상 그룹으로 설정할**합니다. 이러한 그룹은 Configuration Manager에서 동기화 하는 컬렉션입니다.  

    - **준비 규칙**: 이러한 규칙은 장치 업그레이드에 대 한 정하는 결정 하는 데 도움이 됩니다. 선택 **WIndows OS** 하 고 다음 설정을 구성 합니다.  

        - **내 컴퓨터가 Windows 업데이트에서 드라이버를 자동으로 가져오기**: 기본 설정은 **해제**, Configuration Manager를 배포 하는 경우 권장 되는 합니다.  

        - **앱에 대 한 낮은 설치 수 임계값을 정의할**: 기본 설정은 `2%`입니다. 앱이이 임계값 아래로 하도록 자동 설정 됩니다 *낮은 설치 수*입니다. 데스크톱 분석 하지는 파일럿 기간 동안 이러한 추가 기능을 확인 합니다.  

            앱이이 임계값 보다 높은 비율로 컴퓨터에 설치, 배포 계획으로 앱 표시 *Noteworthy*합니다. 그런 다음 파일럿 단계 테스트의 중요성을 결정할 수 있습니다.  

    - **완료 날짜**: Windows 완벽 하 게 모든 대상된 장치에 배포할지 때 사용 되는 날짜를 선택 합니다.  

5. **만들기**를 선택합니다. 새 계획 처리 되 고 해당 하는 동안 배포 계획의 목록에 나타납니다. 처리를 신속 하 게 요청 시 데이터 새로 고침을 요청 합니다. 자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)합니다.

6. 해당 이름을 선택 하 여 배포 계획을 엽니다.  

7. 배포 계획 메뉴에 **준비** 그룹에서 **중요도 식별**.  

    1. 에 **앱** 탭만 표시 하도록 선택 합니다 **를 검토 하지** 자산입니다.  

    2. 각 앱을 선택 하 고 선택한 **편집**합니다. 동시 편집 하려면 둘 이상의 앱을 선택할 수 있습니다.  

    3. 중요도 수준을 선택 합니다 **중요도** 목록입니다. 파일럿 기간 동안 앱 유효성을 검사 하려면 데스크톱 분석 선택 **Critical** 또는 **중요**합니다. 로 표시 되는 앱의 유효성을 검사 하지 않습니다 **중요 하지 않은**합니다. 평가 해당 [호환성](/sccm/desktop-analytics/compat-assessment) 및 중요도 수준을 할당할 때 다른 계획 정보입니다.  

        중요도 수준에 할당 하는 경우에 업그레이드 의사 결정을 선택할 수 있습니다.  

    4. 선택 **저장할** 완료 되 면 합니다.  

8. 배포 계획 메뉴에 **준비** 그룹에서 **식별 파일럿**.  

    1. 파일럿에 대 한 권장 되는 장치를 검토 합니다.  

    2. 각 장치를 선택 하 고 선택 **파일럿 추가할**합니다. 권장 사항을 사용 하 여 동의할 수 없는 경우 선택 **대체**합니다.  

        이러한 권장 사항은 데스크톱 분석을 사용 하는 방법에 대 한 자세한 내용은 오른쪽 위 모서리에서 정보 아이콘을 선택 합니다 **식별 파일럿** 창.



## <a name="deploy-windows-10-in-configuration-manager"></a>Configuration Manager에서 Windows 10 배포

파일럿 그룹을 Configuration Manager에서 Windows 10을 배포 하려면이 절차를 따르십시오.

- 아직 없다면, 먼저 경우 [Windows 10에 대 한 OS 업그레이드 패키지 만들기](#bkmk_create-package)  

- 아직 없는 한 경우 [Windows 10에 대 한 OS 업그레이드 작업 순서 만들기](#bkmk_create-ts)  

- [작업 순서를 배포할](#bkmk_deploy-ts) 데스크톱 Analytics 배포 계획을 사용 하 여  

- [작업 순서를 설치할](#bkmk_install-ts) 대상된 장치에 소프트웨어 센터에서  

<!-- 
- [Monitor](#bkmk_monitor-ts) status in Configuration Manager  
 -->

### <a name="bkmk_create-package"></a> Windows 10에 대 한 OS 업그레이드 패키지 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **운영 체제**를 확장한 다음, **운영 체제 업그레이드 패키지** 노드를 선택합니다.  

2. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **운영 체제 업그레이드 패키지 추가**를 선택합니다. 그러면 운영 체제 업그레이드 추가 마법사가 시작됩니다.  

3. 에 **데이터 원본** 페이지에서 네트워크를 지정 **경로** OS의 소스 파일에서 업그레이드 하는 패키지를 설치 합니다. 예를 들어 `\\server\share\path`의 관리 Hyper-V 호스트로 추가하려면 다음 절차를 따르면 됩니다.  

    > [!NOTE]  
    > 설치 원본 파일에는 OS를 설치하는 setup.exe와 다른 파일 및 폴더가 포함되어 있습니다.  

4. 에 **일반** 페이지에서 지정 하는 고유한 **이름** OS에 대 한 패키지를 업그레이드 합니다.  

5. 완료 된 운영 체제 업그레이드 패키지 마법사를 추가 합니다.  

#### <a name="distribute-content"></a>콘텐츠 배포

다음으로, OS 업그레이드 패키지를 배포 지점에 배포합니다.  

1. 목록에서 OS 업그레이드 패키지를 선택 합니다. 리본의 **홈** 탭에 있는 **배포** 그룹에서 **콘텐츠 배포**를 선택합니다. 콘텐츠 배포 마법사를 엽니다.  

2. 에 **일반** 페이지에서 나열 된 콘텐츠가 배포 하 고 클릭 하려는 콘텐츠 확인 **다음**합니다.  

3. 에 **콘텐츠 대상** 페이지에서 **추가**를 선택 하 고 **배포 지점**합니다. 기존 배포 지점을 선택한 후 **확인**합니다. 콘텐츠 대상 추가 완료 하면 선택할 **다음**합니다.  

4. 완료는 콘텐츠 배포 마법사.  


### <a name="bkmk_create-ts"></a> Windows 10에 대 한 OS 업그레이드 작업 순서 만들기

1. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장 **운영 체제**를 선택한 후 **작업 순서**합니다.  

2. 에 **홈** 리본 메뉴의 탭에서를 **만들기** 그룹에서 **작업 순서 만들기**합니다.  

3. 에 **새 작업 순서 만들기** 작업 순서 만들기 마법사에서 선택 페이지 **업그레이드 패키지에서 운영 체제를 업그레이드**를 선택한 후 **다음**합니다.  

4. 에 **작업 순서 정보** 페이지에서 지정을 **작업 순서 이름** 작업 순서를 식별 하는 합니다.  

5. 에 **Windows 운영 체제 업그레이드** 페이지에서 다음 설정을 지정 하 고 선택한 **다음**:  

    - **업그레이드 패키지**:  OS 업그레이드 원본 파일이 포함된 업그레이드 패키지를 지정합니다.  

    - **버전 인덱스**: 패키지에서 사용할 수 있는 OS 버전 인덱스가 여러 개 있는 경우 원하는 버전 인덱스를 선택합니다. 기본적으로 마법사는 첫 번째 인덱스를 선택합니다.  

    - **제품 키**: 설치할 OS의 Windows 제품 키를 지정합니다. 인코딩된 볼륨 라이선스 키 또는 표준 제품 키를 지정하세요. 표준 제품 키를 사용하는 경우 5자로 이루어진 각 그룹을 대시(-)로 구분 합니다. 예: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. 볼륨 라이선스 버전용 업그레이드의 경우에는 제품 키가 필요하지 않을 수 있습니다.  

        > [!Note]  
        > 이 제품 키는 MAK(복수 정품 인증 키) 또는 GVLK(일반 볼륨 라이선스 키)일 수 있습니다. GVLK는 또한 KMS(키 관리 서비스) 클라이언트 설정 키라고도 합니다. 자세한 내용은 [볼륨 활성화 계획](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client)을 참조하세요. KMS 클라이언트 설정 키의 목록은 Windows Server 정품 인증 가이드의 [부록 A](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys)를 참조하세요.

6. 에 **업데이트 포함** 페이지에서 **다음** 모든 소프트웨어를 설치 하지 않도록 업데이트 합니다.  

7. 에 **응용 프로그램 설치** 페이지에서 **다음** 응용 프로그램을 설치 하지 않도록 합니다.

8. 작업 순서 만들기 마법사를 완료 합니다.  


### <a name="bkmk_deploy-ts"></a> 데스크톱 Analytics 배포 계획을 사용 하 여 작업 순서 배포

1. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리**, 확장 **데스크톱 분석 서비스**, 선택는 **배포 계획** 노드.  

2. Windows 10 파일럿 배포 계획을 선택한 후 **배포 계획 세부 정보** 리본 메뉴에 있습니다.  

3. 에 **상태 파일럿** 타일을 선택 **작업 순서** 를 선택 하 고 드롭 다운 목록에서 **배포**합니다.  

4. 에 **일반적인** 배포 소프트웨어 마법사의 선택 페이지 **찾아보기** 옆에 **소프트웨어** 필드. Windows 10 현재 위치 업그레이드 작업 순서를 선택 하 고 선택 **다음**합니다.  

    > [!Note]  
    > 데스크톱 분석 통합을 사용 하 여 Configuration Manager는 자동으로 파일럿 배포 계획에 대 한 컬렉션을 만듭니다. 사용 하기 전에 동기화를이 컬렉션에 대 일 분 정도 걸릴 수 있습니다.<!-- 3887891 -->
    >
    > 이 컬렉션은 데스크톱 Analytics 배포 계획 장치에 대 한 예약 되어 있습니다. 이 컬렉션에 수동으로 변경한 내용은 지원 되지 않습니다.<!-- 3866460, SCCMDocs-pr 3544 -->  

5. 에 **콘텐츠** 페이지에서 **추가**를 선택한 후 **배포 지점**합니다. 설치 콘텐츠를 호스트 하 고 선택에 사용할 수 있는 배포 지점을 선택 **확인**합니다. **다음**을 선택합니다.  

6. 에 **배포 설정** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다. (사용 가능한 설치입니다.)  

7. 에 **일정** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다. (사용 가능 가능한 한 빨리)  

8. 에 **사용자 환경** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다. (소프트웨어 센터에 표시 및 컴퓨터를 다시 시작에 대 한 알림을 표시 합니다.)  

9. 에 **경고** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다.  

10. 마법사를 완료합니다.  


### <a name="bkmk_install-ts"></a> 작업 순서가 소프트웨어 센터에서 설치

1. 파일럿 배포 계획의 구성원임을 확인 하는 장치에 로그인 합니다.  

2. 오픈 **소프트웨어 센터** 및 Windows 10에 대 한 사용 가능한 운영 체제를 설치 합니다.  


<!--
### <a name="bkmk_monitor-app"></a> Monitor status in Configuration Manager
-->


## <a name="next-steps"></a>다음 단계

데스크톱 Analytics 배포 계획에 자세히 알아보려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]  
> [배포 계획](/sccm/desktop-analytics/about-deployment-plans)
