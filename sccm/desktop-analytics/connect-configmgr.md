---
title: Configuration Manager 연결
titleSuffix: Configuration Manager
description: 데스크톱 분석과 Configuration Manager 연결 하는 방법에 대 한 지침입니다.
ms.date: 07/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7ed389c3-a9ab-48ce-a5eb-27d52ee4fb94
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 138cf7b8cc6c1279e72d7c620154f703581a9f49
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72386630"
---
# <a name="how-to-connect-configuration-manager-with-desktop-analytics"></a>데스크톱 분석과 Configuration Manager 연결 하는 방법

데스크톱 분석은 Configuration Manager와 긴밀 하 게 통합 됩니다. 먼저 최신 기능을 지원 하기 위해 사이트가 최신 상태 인지 확인 합니다. 그런 다음 Configuration Manager에서 데스크톱 분석 연결을 만듭니다. 마지막으로 연결 상태를 모니터링 합니다.


## <a name="bkmk_hotfix"></a>사이트 업데이트

먼저 Configuration Manager 사이트에서 버전 1902 이상을 실행 하 고 있는지 확인 합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.

또한 데스크톱 분석과의 통합을 지원 하기 위해 버전 1902 업데이트 롤업 (4500571)을 설치 해야 합니다. 이 업데이트에 대 한 자세한 내용은 [Configuration Manager 현재 분기에 대 한 업데이트 롤업, 버전 1902](https://support.microsoft.com/help/4500571)을 참조 하세요.

1. 1902 버전에 대 한 업데이트 롤업을 사용 하 여 사이트를 업데이트 합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  



## <a name="bkmk_connect"></a>서비스에 연결

이 절차를 사용 하 여 Configuration Manager 데스크톱 분석에 연결 하 고 장치 설정을 구성 합니다. 이 절차는 계층을 클라우드 서비스에 연결 하는 일회성 프로세스입니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 리본에서 **Azure 서비스 구성** 을 선택 합니다.  

    > [!Tip]  
    > Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **데스크톱 분석 서비스** 노드를 선택 합니다. 데스크톱 분석 *새로 만들기* 상자에서 두 번째 링크를 선택 하 여 *Configuration Manager desktop Analytics 서비스에 연결*합니다.  

2. Azure 서비스 마법사의 **Azure 서비스** 페이지에서 다음 설정을 구성 합니다.  

    - Configuration Manager의 개체 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    - 사용 가능한 서비스 목록에서 **데스크톱 분석** 을 선택 합니다.  
  
   **다음**을 선택합니다.  

3. **앱** 페이지에서 적절 한 **Azure 환경을**선택 합니다. 그런 다음 웹 앱 **찾아보기** 를 선택 합니다.  

4. 이 서비스에 대해 다시 사용 하려는 기존 앱이 있는 경우 목록에서 선택 하 고 **확인**을 선택 합니다.  

5. 대부분의 경우이 마법사를 사용 하 여 데스크톱 분석 연결에 대 한 앱을 만들 수 있습니다. **만들기**를 선택합니다.<!-- 3572123 -->  

    > [!Tip]  
    > 이 마법사에서 앱을 만들 수 없는 경우 Azure AD에서 수동으로 앱을 만든 다음 Configuration Manager으로 가져올 수 있습니다. 자세한 내용은 [Configuration Manager에 대 한 앱 만들기 및 가져오기](/sccm/desktop-analytics/troubleshooting#create-and-import-app-for-configuration-manager)를 참조 하세요.  

6. **서버 응용 프로그램 만들기** 창에서 다음 설정을 구성 합니다.  

    - **응용 프로그램 이름**: Azure AD의 앱에 대 한 친숙 한 이름입니다.

    - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만 Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. Configuration Manager 클라이언트에서 서비스에 대 한 액세스를 요청 하는 데 사용 하는 액세스 토큰입니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.  

    **로그인** 을 선택 합니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다.
        
    > [!Note]  
    > **전역 관리자 권한**으로이 단계를 완료 합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다.  

    **확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. 서버 앱 대화 상자에서 **확인**을 선택 합니다. 그런 후에 Azure 서비스 마법사의 앱 페이지에서 **다음** 을 선택 합니다.  

7. **진단 데이터** 페이지에서 다음 설정을 구성 합니다.  

    - **상용 id**:이 값은 조직의 ID로 자동으로 채워집니다. 그렇지 않은 경우 계속 하기 전에 프록시 서버가 필요한 모든 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints) 을 허용 하도록 구성 되어 있는지 확인 합니다. 또는 [데스크톱 분석 포털](/sccm/desktop-analytics/monitor-connection-health#bkmk_ViewCommercialID)에서 수동으로 상용 ID를 검색 합니다.  

    - **Windows 10 진단 데이터 수준**: 최소 **기본**을 선택 합니다. [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels) 참조
  
    - **진단 데이터에서 장치 이름 허용**: **사용** 을 선택 합니다.  

        > [!Note]  
        > Windows 10 버전 1803부터 장치 이름은 기본적으로 Microsoft에 전송 되지 않습니다. 장치 이름을 보내지 않으면 데스크톱 분석에서 "알 수 없음"으로 표시 됩니다. 이 동작을 통해 장치를 식별 하 고 평가 하기 어려울 수 있습니다.  

   **다음**을 선택합니다. **사용 가능한 기능** 페이지에는 이전 페이지의 진단 데이터 설정에서 사용할 수 있는 데스크톱 분석 기능이 표시 됩니다. 계속 하려면 **다음** 을 선택 하 고, 변경 하려면 **이전** 을 선택 합니다.  

    ![Azure 서비스 마법사의 예제 사용 가능 기능 페이지](media/available-functionality.png)

8. **컬렉션** 페이지에서 다음 설정을 구성 합니다.  

    - **표시 이름**: 데스크톱 분석 포털은이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다. 이를 사용 하 여 서로 다른 계층을 구분 합니다. 예: *테스트 랩* 또는 *프로덕션*.  

    - **대상 컬렉션**:이 컬렉션에는 상업적 ID 및 진단 데이터 설정 Configuration Manager 구성 하는 모든 장치가 포함 됩니다. Configuration Manager는 데스크톱 분석 서비스에 연결 하는 전체 장치 집합입니다.  

    - **대상 컬렉션의 장치는 아웃 바운드 통신에 사용자 인증 프록시를 사용**합니다. 기본적으로이 값은 **아니요**입니다. 사용자 환경에 필요한 경우를 **예**로 설정 합니다.  

    - **데스크톱 분석과 동기화 할 특정 컬렉션 선택**: **추가** 를 선택 하 여 **대상 컬렉션** 계층의 추가 컬렉션을 포함 합니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화 하기 위해 데스크톱 분석 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  <!-- 4097528 -->  

        > [!Tip]  
        > 컬렉션 선택 창에는 **대상 컬렉션**에 의해 제한 되는 컬렉션만 표시 됩니다.
        >
        > 다음 예제에서는 CollectionA를 대상 컬렉션으로 선택 합니다. 그런 다음 컬렉션을 추가 하면 CollectionA, Collectiona 및 Collectiona가 표시 됩니다. CollectionD를 추가할 수 없습니다.
        >
        > - CollectionA: **모든 시스템** 컬렉션에 의해 제한 됨
        >     - CollectionB: Collectionb로 제한
        >         - CollectionC: Collectionc로 제한
        > - CollectionD: **모든 시스템** 컬렉션에 의해 제한 됨

        > [!Important]  
        > 이러한 컬렉션은 멤버 자격 변경 내용에 따라 계속 동기화 됩니다. 예를 들어 배포 계획에서는 Windows 7 멤버 자격 규칙을 사용 하는 컬렉션을 사용 합니다. 이러한 장치는 Windows 10으로 업그레이드 되 고 Configuration Manager 컬렉션 멤버 자격을 평가 하므로 해당 장치는 수집 및 배포 계획에서 제외 됩니다.  


9. 마법사 완료  

Configuration Manager 대상 컬렉션에서 장치를 구성 하는 설정 정책을 만듭니다. 이 정책에는 장치에서 Microsoft로 데이터를 보낼 수 있도록 진단 데이터 설정이 포함 되어 있습니다. 기본적으로 클라이언트는 매시간 정책을 업데이트 합니다. 새 설정을 받은 후에는 데스크톱 분석에서 데이터를 사용할 수 있을 때까지 몇 시간이 걸릴 수 있습니다.



## <a name="bkmk_monitor"></a>연결 상태 모니터링

데스크톱 분석에 대 한 장치의 구성을 모니터링 합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **데스크톱 분석 서비스** 노드를 확장 하 고 **연결 상태** 대시보드를 선택 합니다.  

자세한 내용은 [연결 상태 모니터링](/sccm/desktop-analytics/troubleshooting#monitor-connection-health)을 참조 하세요.

Configuration Manager는 연결을 만들 때 60 분 이내에 컬렉션을 동기화 합니다. 데스크톱 분석 포털에서 **전역 파일럿**으로 이동 하 여 Configuration Manager 장치 컬렉션을 확인 합니다.



## <a name="next-steps"></a>다음 단계

데스크톱 분석에 장치를 등록 하려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]  
> [디바이스 등록](/sccm/desktop-analytics/enroll-devices)  
