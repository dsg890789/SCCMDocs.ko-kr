---
title: 자습서-Office 365를 배포 합니다.
titleSuffix: Configuration Manager
description: 데스크톱 분석 및 Configuration Manager를 사용 하 여 Office 365를 파일럿 그룹에 배포 하는 자습서입니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: tutorial
ms.assetid: 0b2b633a-91d7-4497-8c2a-1fc7aa310bb1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f05b1115338f9808a950bcd1646d8035f3a563b
ms.sourcegitcommit: 4441b3035222cfaf7442416873ed824ac7d852c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356362"
---
# <a name="tutorial-deploy-office-365-to-pilot"></a>자습서: Office 365를 파일럿 배포 

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

이 자습서에서는 파일럿 그룹에 Office 365 ProPlus를 배포 하려면 데스크톱 분석 및 Configuration Manager를 사용 합니다. 온-프레미스 제품을 사용 하 여 앱을 배포 하는 정보를 제공 하도록 클라우드 서비스의 통합 강조 표시 합니다. 파일럿 그룹에 배치할 최상의 장치를 확인 하려면 데스크톱 Analytics를 사용 합니다. 다음 Configuration Manager를 사용 하 여 Office를 사용 하 여 현재 가져오려고 합니다.

이 자습서에 알아봅니다 방법:  

> [!div class="checklist"]  
> * Azure portal에서 데스크톱 분석 설정  
> * Configuration Manager를 연결 하 고 장치 설정 구성  
> * Office 365 ProPlus에 대 한 데스크톱 Analytics 배포 계획 만들기  
> * 파일럿 그룹에 Office 365 ProPlus Configuration Manager에서 배포  

Azure 구독이 없으면 만듭니다는 [무료 계정](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) 시작 하기 전에 합니다. 올바르게 구성 하는 경우 데스크톱 분석을 사용 하 여 한 Azure 요금이 부과 하지 않습니다. 

데스크톱 Analytics를 사용 하는 *Log Analytics 작업 영역* Azure 구독에 있습니다. 작업 영역은 기본적으로 계정에 대 한 간단한 구성 정보와 계정 정보를 포함 하는 컨테이너입니다. 자세한 내용은 [작업 영역 관리](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-access?toc=/azure/azure-monitor/toc.json)합니다.



## <a name="prerequisites"></a>필수 구성 요소

이 자습서를 시작 하기 전에 다음 필수 구성 요소가 있는지 확인 합니다.  

- 활성 Azure 구독을 사용 하 여 **회사 관리자** 권한  

- Configuration Manager 1810 버전 4486457 이상을 사용 하 여 업데이트 롤업 **전체 관리자** 역할  

- 다음 구성이 포함 된 하나 이상의 Windows 10 장치:  

    - Windows 10 버전 1709 이상

    - 최신 Windows 10 누적 품질 업데이트  

    - Configuration Manager 클라이언트 버전 1810 4486457 이상 업데이트 롤업  

    - Windows installer 기반 버전의 Office 2013과 같은 Office  

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
    - `https://www.msftncsi.com`  
    - `https://www.msftconnecttest.com`  
    - `https://kmwatsonc.events.data.microsoft.com`  
    - `https://oca.telemetry.microsoft.com`  
    - `https://login.live.com`  
    - `https://nexusrules.officeapps.live.com`  
    - `https://nexus.officeapps.live.com`  
    - `https://office.pipe.aria.microsoft.com`  
    - `https://graph.windows.net` (에서 Configuration Manager 서버 역할에만 해당)
    - `https://fef.msua06.manage.microsoft.com` (에서 Configuration Manager 서버 역할에만 해당)

    자세한 내용은 [데스크톱 분석에 대 한 공유 데이터를 사용 하도록 설정 하는 방법을](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  

> [!Important]  
> 이러한 필수 구성이 요소는이 자습서의 목적입니다. Configuration Manager에서 데스크톱 Analytics에 대 한 일반적인 필수 구성 요소에 대 한 자세한 내용은 참조 하세요. [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)합니다.  



## <a name="set-up-desktop-analytics"></a>Desktop Analytics 설정

데스크톱 분석에 로그인 하 고 구독에서 구성 하려면이 절차를 따르십시오. 이 절차는 조직에 대 한 데스크톱 Analytics를 설정 하는 일회성 프로세스입니다.  

1. 사용자로 Microsoft 365 장치 관리에서 데스크톱 Analytics 포털을 엽니다 **회사 관리자** 권한. 선택 **시작**합니다.  

2. 에 **서비스 계약에 동의** 페이지에서 서비스 계약을 검토 하 고 선택 **Accept**합니다.  

3. 에 **구독을 확인 하** 데스크톱 Analytics의 Windows 장치 상태 모니터링 기능에 대 한 페이지에서 필요한 정식 라이선스 목록이 됩니다. 계속하려면 **다음**을 선택합니다.  

4. 에 **사용자가 액세스할 수** 데스크톱 분석 페이지에서 Azure Active Directory에서 두 개의 보안 그룹을 미리 구성 합니다.  

    - **작업 영역 소유자**: 작업 영역을 만들고 설정 합니다. 이러한 계정은 Azure 구독에 대 한 소유자 액세스를 해야합니다.  

    - **작업 영역 참가자**: 이 작업 영역에서 배포 계획을 만들고 설정 합니다. 모든 추가 Azure 액세스할이 필요는 없습니다.  
  
   각 그룹에 사용자를 추가할에서 해당 이름 또는 전자 메일 주소를 입력 합니다 **이름 또는 전자 메일 주소 입력** 적절 한 그룹의 섹션입니다. 완료 되 면 선택 **다음**합니다. 

5. 페이지에서 **작업 영역 설정**:  

    - 기존 작업 영역에 데스크톱 Analytics를 사용 하려면를 선택 하 고 단계를 진행 합니다.  

    - 데스크톱 분석을 위해 작업 영역을 만들려면 **작업 영역 추가**합니다.  

        1. 입력 한 **작업 영역 이름**합니다.  

        2. 드롭다운 목록 선택 **이 작업 영역에 대 한 Azure 구독 이름을 선택**,이 작업 영역에 대 한 Azure 구독을 선택 합니다.  

        3. 선택 된 **지역** 을 선택 하 고 목록에서 **추가**합니다.  

6. 새 또는 기존 작업 영역을 선택한 후 **데스크톱 Analytics 작업 영역으로 설정**합니다.  선택한 **계속** 에 **Confirm 및 권한 부여 액세스** 대화 합니다.  

7. 새 브라우저 탭에서 계정을 사용 하 여 로그인을 선택 합니다. 옵션을 선택 **조직을 대신 하 여 동의** 선택한 **Accept**합니다.  

8. 페이지에서 다시 **작업 영역 설정**를 선택 **다음**합니다.  

9. 에 **마지막 단계** 페이지에서 **Desktop Analytics로 이동**합니다. Azure portal에 데스크톱 분석을 보여 줍니다 **홈** 페이지입니다.  


### <a name="create-an-app-in-azure-ad-for-configuration-manager"></a>Configuration Manager에 대 한 Azure AD에서 앱 만들기  

1. 에 [Azure portal](https://portal.azure.com)로 이동 하세요 **Azure Active Directory**를 선택한 **앱 등록**합니다. 선택한 **새 응용 프로그램 등록**합니다.  

2. 에 **만들기** 패널에서 다음 설정을 구성 합니다.  

    - **이름**: 예를 들어 앱을 식별 하는 고유 이름: `Desktop-Analytics-Connection`  

    - **응용 프로그램 유형을**: **웹 앱 / API**  

    - **로그온 URL**:이 값이 Configuration Manager에서 사용 되지 않지만 Azure AD에 필요 합니다. 예를 들어 고유 하 고 올바른 URL을 입력 합니다. `https://configmgrapp`  
  
    **만들기**를 선택합니다.  

3. 앱을 선택 하 고 확인 합니다 **응용 프로그램 ID**합니다. 이 값은 Configuration Manager 연결을 구성 하는 데 사용 되는 GUID입니다.  

4. 선택 **설정을** 에 앱을 선택한 후 **키**합니다. 에 **암호** 섹션에서 입력을 **키 설명**, 만료 날짜를 지정 **기간**를 선택한 후 **저장**. 복사 합니다 **값** Configuration Manager 연결을 구성 하는 데 사용 되는 키입니다. 

    > [!Important]  
    > 키 값을 복사만 기회입니다. 이제 복사 안 함, 하는 경우 다른 키를 만들 해야 합니다.  
    > 
    > 키 값을 안전한 위치에 저장 합니다.  

5. 앱에서 **설정을** 패널에서 **필요한 권한**합니다.  

    1. 에 **필요한 권한** 패널에서 **추가**합니다.  

    2. 에 **API 액세스 추가** 패널 **API 선택**합니다.  

    3. 검색 된 **Configuration Manager 마이크로 서비스** API. 선택 하 고 선택한 **선택**합니다.  

    4. 에 **액세스 사용** 패널에서 응용 프로그램 권한을 모두 선택 합니다. **CM 컬렉션 데이터를 쓸** 하 고 **CM 컬렉션 데이터를 읽을**합니다. 선택한 **선택**합니다.  

    5. 에 **API 액세스 추가** 패널에서 **수행**합니다.  

6. 에 **필요한 권한** 페이지에서 **권한을 부여**합니다. 선택 **예**합니다.  

7. Azure AD 테 넌 트 ID를 복사 합니다. 이 값은 Configuration Manager 연결을 구성 하는 데 사용 되는 GUID입니다. 선택 **Azure Active Directory** 에서 주 메뉴를 선택 합니다 **속성**합니다. 복사 합니다 **디렉터리 ID** 값입니다.  



## <a name="connect-configuration-manager"></a>Configuration Manager 연결

Configuration Manager 업데이트, 데스크톱 Analytics에 연결 및 장치 설정을 구성 하려면이 절차를 따르십시오. 이 절차는 계층 클라우드 서비스에 연결 하는 일회성 프로세스입니다.  


### <a name="update-configuration-manager"></a>Configuration Manager 업데이트

데스크톱 Analytics와의 통합을 지원 하기 위해 Configuration Manager 버전 1810 업데이트 롤업 (4486457)를 설치 합니다. 이 업데이트에 대 한 자세한 내용은 참조 하세요. [Configuration Manager 현재 분기, 버전 1810 용 업데이트 롤업](https://support.microsoft.com/help/4486457)합니다.

1. 버전 1810에 대한 업데이트 롤업을 사용하여 사이트를 업데이트합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  


### <a name="connect-to-the-service"></a>서비스에 연결

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 선택 **Azure 서비스 구성** 리본 메뉴에 있습니다.  

2. 에 **Azure Services** 페이지 Azure 서비스 마법사의 다음 설정을 구성 합니다.  

    - 지정 된 **이름을** in Configuration Manager 개체에 대 한  

    - 선택적인 지정할 **설명을** 서비스를 식별 하는 데  

    - 선택 **데스크톱 분석** 사용 가능한 서비스 목록에서  
  
   **다음**을 선택합니다.  

3. 에 **앱** 페이지에서 적절 한 선택 **Azure 환경**합니다. 선택한 **가져오기** 웹 앱에 대 한 합니다. 다음 설정을 구성 합니다 **앱 가져오기** 창:  

    - **Azure AD 테 넌 트 이름**: 이 이름은 Configuration Manager에서 지정 됩니다 하는 방법  

    - **Azure AD 테 넌 트 ID**: 합니다 **디렉터리 ID** Azure AD에서 복사한   

    - **클라이언트 ID**: 합니다 **응용 프로그램 ID** Azure AD 앱에서 복사   

    - **비밀 키**: 키 **값** Azure AD 앱에서 복사   

    - **비밀 키 만료**: 동일한 키의 만료 날짜   

    - **앱 ID URI**: 이 설정은 다음 값을 사용 하 여 자동으로 채워야 합니다. `https://cmmicrosvc.manage.microsoft.com/`  
  
   선택 **확인**를 선택한 후 **확인** 앱 가져오기 창을 닫습니다. 선택 **다음** Azure 서비스 마법사의 앱 페이지에 있습니다.  

4. 에 **진단 데이터** 페이지에서 다음 설정을 구성 합니다.  

    - **상업용 ID**:이 값은 조직의 ID를 사용 하 여 자동 채우기  

    - **Windows 10 진단 데이터 수준**: 하나 이상 선택 **고급 (제한적)**  

    - **장치 이름을 진단 데이터의 허용**: 선택 **사용 하도록 설정**  
  
   **다음**을 선택합니다. 합니다 **사용할 수 있는 기능** 페이지는 이전 페이지에서 진단 데이터 설정을 사용 하 여 사용할 수 있는 데스크톱 분석 기능을 보여 줍니다. **다음**을 선택합니다.  

5. 에 **컬렉션** 페이지에서 다음 설정을 구성 합니다.  

    - **표시 이름**: 데스크톱 Analytics 포털에이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다. 다른 계층 간에 구분 하기 위해 사용 합니다. 예를 들어 *테스트 랩을* 하거나 *프로덕션*합니다.  

    - **컬렉션을 대상**: 이 컬렉션에 진단 데이터 설정과 상업용 ID를 사용 하 여 Configuration Manager를 구성 하는 모든 장치를 포함 합니다. Configuration Manager에서 데스크톱 Analytics 서비스에 연결 하는 장치의 전체 집합은  

    - **아웃 바운드 통신에 대 한 사용자 인증 프록시를 사용 하는 대상 컬렉션의 장치**: 기본적으로이 값은 **No**합니다. 사용자 환경에서 필요한 경우로 **예**합니다.   

    - **데스크톱 Analytics와 동기화 하도록 특정 컬렉션 선택**: 선택 **추가** 추가 컬렉션을 포함 합니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화에 대 한 데스크톱 Analytics 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  

        이러한 컬렉션의 멤버 자격 변경으로 동기화 계속 합니다. 예를 들어 배포 계획을 Windows 7 멤버 관리 규칙을 사용 하 여 컬렉션을 사용 합니다. 해당 장치를 Windows 10으로 업그레이드 하 고 Configuration Manager 컬렉션 멤버 자격을 평가, 수집 및 배포 계획에서 해당 장치를 삭제 합니다.  

6. 마법사를 완료합니다.  

Configuration Manager에는 대상 컬렉션의 장치를 구성 하는 설정 정책을 만듭니다. 이 정책은 장치가 Microsoft에 데이터를 보낼 수 있도록 진단 데이터 설정을 포함 합니다. 기본적으로 클라이언트 1 시간 마다 정책을 업데이트합니다. 새 설정을 받은 후 데이터가 데스크톱 Analytics에서 사용할 수 있는 전에 몇 시간 더 많은 수 있습니다.

데스크톱 분석에 대 한 장치 구성을 모니터링 합니다. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **Microsoft 365 서비스** 노드를 선택한는 **연결 상태** 대시보드.  

Configuration Manager 연결을 만든 후 15 분 내에서 모든 데스크톱 Analytics 배포 계획을 동기화 합니다. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **Microsoft 365 서비스** 노드를 선택한는 **배포 계획** 노드. 



## <a name="create-a-desktop-analytics-deployment-plan"></a>데스크톱 Analytics 배포 계획 만들기

데스크톱 Analytics에서 배포 계획을 만들려면이 절차를 사용 합니다.

1. 엽니다는 [데스크톱 Analytics 포털](https://aka.ms/m365aprod)합니다. 최소 권한이 있는 자격 증명을 사용 하 여 **작업 영역 참가자** 권한.  

2. 선택 **배포 계획** 관리 그룹에 있습니다.  

3. 에 **배포 계획** 창 **만들기**합니다.  

4. 에 **배포 계획 만들기** 창 다음 설정을 구성 합니다.  

    - **이름**: 예를 들어 배포에 대 한 고유한 이름을 계획합니다 `Office 365 pilot`  

    - **제품 및 버전**: 선택 된 **Office** 제품 및 최신 권장된 버전입니다. 예를 들어 **Office 365 클라이언트의 경우 버전 (권장) 1808**합니다.  

    - **장치 그룹**: 하나 이상의 그룹을 선택 하 고 선택한 **대상 그룹으로 설정할**합니다. 그룹 **sccm** 소스로 컬렉션 동기화 Configuration Manager에서 합니다.  

    - **준비 규칙**: 이러한 규칙은 장치 업그레이드에 대 한 정하는 결정 하는 데 도움이 됩니다. 선택 **Office 응용 프로그램** 하 고 다음 설정을 구성 합니다.  

        - 업데이트 Office 365 ProPlus에서 32 비트에서 64 비트입니다. 이 설정은 Windows의 64 비트 버전을 실행 하는 장치에만 적용 됩니다. 기본 설정은 **예**입니다.  

        - 이전 버전의 Office 업데이트할 때 두십시오 이전 Office 앱을 사용 되지 않습니다. 이 동작에는 해당 앱 Office의 최신 버전에 없는 경우에 적용 됩니다. 기본 설정은 **No**합니다.  

        - 낮은은 Office 추가 기능에 대 한 count 임계값을 설치 합니다. 기본 임계값은 `2%`합니다. 이 임계값 보다 추가 기능 자동으로 설정 됩니다 *낮은 설치 수*입니다. 데스크톱 분석 하지는 파일럿 기간 동안 이러한 추가 기능을 확인 합니다. 

            배포 계획에서 추가 기능으로 표시 추가 기능에서이 임계값 보다 높은 비율로 컴퓨터에 설치 된 경우 *Noteworthy*합니다. 그런 다음 파일럿 단계 테스트의 중요성을 결정할 수 있습니다.   

    - **완료 날짜**: Office 완벽 하 게 모든 대상된 장치에 배포할지 때 사용 되는 날짜를 선택 합니다.  

5. **만들기**를 선택합니다. 새 계획 처리 되 고 해당 하는 동안 배포 계획의 목록에 나타납니다. 처리는 다음 단계를 진행 하기 전에 최대 48 시간이 걸릴 수 있습니다.  

6. 해당 이름을 선택 하 여 배포 계획을 엽니다.  

7. 배포 계획 메뉴에 **준비** 그룹에서 **중요도 식별**.  

    1. 에 **Office 추가 기능** 탭만 표시 하도록 선택 합니다 **를 검토 하지** 자산입니다.  

    2. 각 추가 기능에서 선택 하 고 선택한 **편집**합니다. 동시 편집 하려면 둘 이상의 앱을 선택할 수 있습니다.   

    3. 중요도 수준을 선택 합니다 **중요도** 목록입니다. 데스크톱 Analytics는 파일럿 기간 동안 추가 유효성 검사를 원한다 면 선택 **Critical** 또는 **중요**합니다. 추가 기능으로 표시의 유효성을 검사 하지 않습니다 **중요 하지 않은**합니다. 중요도 수준을 할당할 때 호환성 위험 및 기타 계획 정보를 고려 합니다.  

        중요도 수준에 할당 하는 경우에 업그레이드 의사 결정을 선택할 수 있습니다.  

    4. 선택 **저장할** 완료 되 면 합니다.  

8. 배포 계획 메뉴에 **준비** 그룹에서 **식별 파일럿**.  

    1. 파일럿에 대 한 권장 되는 장치를 검토 합니다.  

    2. 각 장치를 선택 하 고 선택 **파일럿 추가할**합니다. 권장 사항을 사용 하 여 동의할 수 없는 경우 선택 **대체**합니다.  

        이러한 권장 사항은 데스크톱 분석을 사용 하는 방법에 대 한 자세한 내용은 오른쪽 위 모서리에서 정보 아이콘을 선택 합니다 **식별 파일럿** 창.



## <a name="deploy-office-365-in-configuration-manager"></a>Configuration Manager에서 Office 365 배포

파일럿 그룹에 Office 365 ProPlus in Configuration Manager를 배포 하려면이 절차를 따르십시오.

- 아직 없다면, 먼저 경우 [Office 365 proplus 앱 만들기](#bkmk_create-app)  

- [앱을 배포할](#bkmk_deploy-app) 데스크톱 Analytics 배포 계획을 사용 하 여  

- [앱을 설치](#bkmk_install-app) 대상된 장치에 소프트웨어 센터에서  

<!-- 
- [Monitor](#bkmk_monitor-app) status in Configuration Manager  
 -->

### <a name="bkmk_create-app"></a> Office 365 ProPlus 앱 만들기

1. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리**, 선택한 합니다 **Office 365 클라이언트 관리** 노드. 선택 된 **Office 365 설치 관리자** 대시보드에서 타일을 합니다.  

2. 에 **응용 프로그램 설정** 페이지에서 제공을 **이름** 이 응용 프로그램에 대 한 합니다. 예를 들어 `Office 365 ProPlus`의 관리 Hyper-V 호스트로 추가하려면 다음 절차를 따르면 됩니다. 필요에 따라 지정 된 **설명을**합니다. 지정 된 **콘텐츠 위치** 설치 파일을 선택 합니다 **다음**합니다.  

3. 에 **Office 설정** 페이지에서 **Office 사용자 지정 도구로 이동 하 고**입니다. Office 365 설치에 대 한 모든 필요한 배포 설정을 구성 합니다.  

    1. 에 **제품 및 릴리스** 그룹에서 **Office 365 ProPlus** 선택 하 고 목록에서 **추가**합니다.  

    2. 에 **언어** 그룹에서 주 언어를 선택 합니다.  

    3. 에 **업데이트 및 업그레이드** 그룹 설정 되어 있는지 확인 합니다 **office, Visio 및 프로젝트를 포함 하 여 MSI 버전을 제거** 됩니다 **에서**합니다.  

    4. 조직에서 필요에 따라 추가 설정을 구성 합니다.  

    5. 완료 되 면 선택 **검토** 오른쪽 위 모퉁이에서. 구성된 설정을 검토 하 고 선택한 **제출**합니다.  

5. **다음**을 선택합니다. 에 **배포** 페이지에서 **No** 이제 배포 합니다. (다음 절차에서는 데스크톱 Analytics 배포 계획 배포용) 선택 **다음** 마법사를 완료 합니다.  


### <a name="bkmk_deploy-app"></a> Office 365 데스크톱 Analytics 배포 계획을 사용 하 여 배포

1. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리**, 확장 **데스크톱 분석 서비스**, 선택는 **배포 계획** 노드.  

2. Office 365 파일럿 배포 계획을 선택한 후 **배포 계획 세부 정보** 리본 메뉴에 있습니다.  

3. 에 **상태 파일럿** 타일을 선택 **응용 프로그램** 를 선택 하 고 드롭 다운 목록에서 **배포**합니다.  

4. 에 **일반적인** 배포 소프트웨어 마법사의 선택 페이지 **찾아보기** 옆에 **소프트웨어** 필드. 예를 들어 Office 365 응용 프로그램 선택 **Office 365 ProPlus**합니다. 데스크톱 분석 통합을 사용 하 여 Configuration Manager는 자동으로 파일럿 배포 계획에 대 한 컬렉션을 만듭니다. **다음**을 선택합니다.  

5. 에 **콘텐츠** 페이지에서 **추가**를 선택한 후 **배포 지점**합니다. 설치 콘텐츠를 호스트 하 고 선택에 사용할 수 있는 배포 지점을 선택 **확인**합니다. **다음**을 선택합니다.  

6. 에 **배포 설정** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다. (사용 가능한 설치입니다.)  

7. 에 **일정** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다. (사용 가능 가능한 한 빨리)  

8. 에 **사용자 환경** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다. (소프트웨어 센터에 표시 및 컴퓨터를 다시 시작에 대 한 알림을 표시 합니다.)  

9. 에 **경고** 페이지에서 **다음** 기본 설정을 그대로 적용 합니다.  

10. 마법사를 완료합니다.  


### <a name="bkmk_install-app"></a> 소프트웨어 센터에서 Office 365 설치

1. 파일럿 배포 계획의 구성원임을 확인 하는 장치에 로그인 합니다.  

2. 오픈 **소프트웨어 센터** 및 Office 365에 대 한 사용 가능한 앱을 설치 합니다.  


<!--
### <a name="bkmk_monitor-app"></a> Monitor status in Configuration Manager
-->




## <a name="next-steps"></a>다음 단계

데스크톱 Analytics 배포 계획에 자세히 알아보려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]  
> [배포 계획](/sccm/desktop-analytics/about-deployment-plans)

