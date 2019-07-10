---
title: Configuration Manager 연결
titleSuffix: Configuration Manager
description: 데스크톱 Analytics를 사용 하 여 Configuration Manager를 연결 하기 위한 방법 가이드입니다.
ms.date: 07/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7ed389c3-a9ab-48ce-a5eb-27d52ee4fb94
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f24161b61c796f9c1605a61656af0eb91f225067
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67676057"
---
# <a name="how-to-connect-configuration-manager-with-desktop-analytics"></a>데스크톱 Analytics를 사용 하 여 Configuration Manager를 연결 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석 Configuration Manager와 긴밀 하 게 통합 됩니다. 먼저, 사이트 최신 기능을 지 원하는 최신 상태 인지 확인 합니다. 그런 다음 Configuration Manager의 분석 데스크톱 연결을 만듭니다. 마지막으로, 연결의 상태를 모니터링 합니다.


## <a name="bkmk_hotfix"></a> 사이트 업데이트

먼저 Configuration Manager 사이트를 하나 이상 하 게 실행 중인지 확인 1902 버전입니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.

1902 버전 업데이트 롤업을 설치 합니다 (4500571) 데스크톱 Analytics와의 통합을 지원 하도록 해야 합니다. 이 업데이트에 대 한 자세한 내용은 참조 하세요. [Configuration Manager 현재 분기, 버전 1902 용 업데이트 롤업](https://support.microsoft.com/help/4500571)합니다.

1. 1902 버전에 대 한 업데이트 롤업을 사용 하 여 사이트를 업데이트 합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  



## <a name="bkmk_connect"></a> 서비스에 연결

이 절차를 사용 하 여 Configuration Manager 데스크톱 Analytics에 연결할 및 장치 설정을 구성 합니다. 이 절차는 계층 클라우드 서비스에 연결 하는 일회성 프로세스입니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 선택 **Azure 서비스 구성** 리본 메뉴에 있습니다.  

    > [!Tip]  
    > Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 선택한 합니다 **데스크톱 분석 서비스** 노드. 에 *데스크톱 Analytics에 새?* 상자에서 두 번째 링크를 선택 *Desktop Analytics 서비스에 연결할 Configuration Manager*합니다.  

2. 에 **Azure Services** 페이지 Azure 서비스 마법사의 다음 설정을 구성 합니다.  

    - Configuration Manager의 개체 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    - 선택 **데스크톱 분석** 사용 가능한 서비스 목록에서.  
  
   **다음**을 선택합니다.  

3. 에 **앱** 페이지에서 적절 한 선택 **Azure 환경**합니다. 선택한 **찾아보기** 웹 앱에 대 한 합니다.  

4. 이 서비스에 대 한 다시 사용 하려는 기존 앱에 있는 경우 목록에서 선택 및 선택 **확인**합니다.  

5. 대부분의 경우에서이 마법사를 사용 하 여 데스크톱 Analytics 연결에 대 한 앱을 만들 수 있습니다. **만들기**를 선택합니다.<!-- 3572123 -->  

    > [!Tip]  
    > 이 마법사에서 앱을 만들 수 없는 경우 수동으로 Azure AD에서 앱을 만들 수 있으며 다음 Configuration Manager로 가져옵니다. 자세한 내용은 [Configuration Manager에 대 한 앱 만들기 및 가져오기](/sccm/desktop-analytics/troubleshooting#create-and-import-app-for-configuration-manager)합니다.  

6. 다음 설정을 구성 합니다 **서버 응용 프로그램 만들기** 창:  

    - **애플리케이션 이름**: Azure AD에 앱의 이름입니다.

    - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. 액세스 토큰에는 Configuration Manager 클라이언트에서 서비스에 대 한 액세스를 요청 하려면 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.  

    선택 **로그인** 합니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다.
        
    > [!Note]  
    > 이 단계를 완료 한 **전역 관리자**합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다.  

    **확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. 서버 앱 대화 상자에서 선택 **확인**합니다. 선택한 **다음** Azure 서비스 마법사의 앱 페이지에 있습니다.  

7. 에 **진단 데이터** 페이지에서 다음 설정을 구성 합니다.  

    - **상업용 ID**:이 값은 조직의 id 자동 채우기 프록시 서버에 필요한 모든을 허용 하도록 구성 되어 있는지 확인 하지 않는 경우 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints) 계속 하기 전에 합니다. 또는에서 수동으로 상업용 ID를 검색 합니다 [데스크톱 Analytics 포털](/sccm/desktop-analytics/monitor-connection-health#bkmk_ViewCommercialID)합니다.  

    - **Windows 10 진단 데이터 수준**: 하나 이상 선택 **기본**입니다. 참조 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)
  
    - **장치 이름을 진단 데이터의 허용**: 선택 **사용 하도록 설정**  

        > [!Note]  
        > Windows 10 버전 1803부터 장치 이름에 전송 되지 않습니다 Microsoft 기본적으로 합니다. 경우 "Unknown"으로 데스크톱 분석 나타나는 장치 이름을 보내지 않습니다. 이 동작을 파악 하 고 장치를 평가 어렵게 만들 수 있습니다.  

   **다음**을 선택합니다. 합니다 **사용할 수 있는 기능** 페이지는 이전 페이지에서 진단 데이터 설정을 사용 하 여 사용할 수 있는 데스크톱 분석 기능을 보여 줍니다. 선택 **다음** 계속 하거나 **이전** 변경할 수 있도록 합니다.  

    ![Azure 서비스 마법사에서 사용할 수 있는 기능 페이지 예](media/available-functionality.png)

8. 에 **컬렉션** 페이지에서 다음 설정을 구성 합니다.  

    - **표시 이름**: 데스크톱 Analytics 포털에이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다. 다른 계층 간에 구분 하기 위해 사용 합니다. 예를 들어 *테스트 랩을* 하거나 *프로덕션*합니다.  

    - **컬렉션을 대상**: 이 컬렉션에 진단 데이터 설정과 상업용 ID를 사용 하 여 Configuration Manager를 구성 하는 모든 장치를 포함 합니다. Configuration Manager에서 데스크톱 Analytics 서비스에 연결 하는 장치의 전체 집합은  

    - **아웃 바운드 통신에 대 한 사용자 인증 프록시를 사용 하는 대상 컬렉션의 장치**: 기본적으로이 값은 **No**합니다. 사용자 환경에서 필요한 경우로 **예**합니다.  

    - **데스크톱 Analytics와 동기화 하도록 특정 컬렉션 선택**: 선택 **추가** 에서 추가 컬렉션을 포함 하 여 **컬렉션을 대상** 계층입니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화에 대 한 데스크톱 Analytics 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  <!-- 4097528 -->  

        > [!Tip]  
        > 컬렉션 선택 창에서 제한 된 컬렉션만 표시 합니다 **컬렉션을 대상**합니다.
        >
        > 다음 예제에서는 같고 대상 컬렉션으로 선택합니다. 추가 컬렉션에 추가 하면 같고, CollectionB, 및 CollectionC 하는 것이 표시 됩니다. CollectionD를 추가할 수 없습니다.
        >
        > - 같고: 제한 된 **모든 시스템** 컬렉션
        >     - 같고 CollectionB: 제한
        >         - CollectionB CollectionC: 제한
        > - CollectionD: 제한을 받지 **모든 시스템** 컬렉션

        > [!Important]  
        > 이러한 컬렉션의 멤버 자격 변경으로 동기화 계속 합니다. 예를 들어 배포 계획을 Windows 7 멤버 관리 규칙을 사용 하 여 컬렉션을 사용 합니다. 해당 장치를 Windows 10으로 업그레이드 하 고 Configuration Manager 컬렉션 멤버 자격을 평가, 수집 및 배포 계획에서 해당 장치를 삭제 합니다.  


9. 마법사를 완료합니다.  

Configuration Manager에는 대상 컬렉션의 장치를 구성 하는 설정 정책을 만듭니다. 이 정책은 장치가 Microsoft에 데이터를 보낼 수 있도록 진단 데이터 설정을 포함 합니다. 기본적으로 클라이언트 1 시간 마다 정책을 업데이트합니다. 새 설정을 받은 후 데이터가 데스크톱 Analytics에서 사용할 수 있는 전에 몇 시간 더 많은 수 있습니다.



## <a name="bkmk_monitor"></a> 연결 상태 모니터

데스크톱 분석에 대 한 장치 구성을 모니터링 합니다. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **데스크톱 분석 서비스** 노드를 선택한는 **연결 상태** 대시보드입니다.  

자세한 내용은 [연결 상태를 모니터링](/sccm/desktop-analytics/troubleshooting#monitor-connection-health)합니다.

Configuration Manager는 연결을 만드는 60 분 내 컬렉션을 동기화 합니다. 데스크톱 Analytics 포털에서로 이동 **전역 파일럿**, Configuration Manager 장치 컬렉션을 표시 합니다.



## <a name="next-steps"></a>다음 단계

데스크톱 Analytics에는 장치를 등록 하려면 다음 문서로 계속 진행 하세요.
> [!div class="nextstepaction"]  
> [디바이스 등록](/sccm/desktop-analytics/enroll-devices)  
