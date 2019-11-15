---
title: Configuration Manager 연결
titleSuffix: Configuration Manager
description: Configuration Manager를 Desktop Analytics와 연결하는 방법 가이드입니다.
ms.date: 07/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7ed389c3-a9ab-48ce-a5eb-27d52ee4fb94
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 776c79afea87523fb6da5c92d0b50f128af2a515
ms.sourcegitcommit: edc7a5ad6a2eb72d0448d4689b9534f7e6f4d2b7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623395"
---
# <a name="how-to-connect-configuration-manager-with-desktop-analytics"></a>Configuration Manager를 Desktop Analytics와 연결하는 방법

Desktop Analytics는 Configuration Manager와 긴밀하게 통합되어 있습니다. 먼저 최신 기능을 지원하기 위해 사이트가 최신 상태인지 확인합니다. 그런 다음, Configuration Manager에서 Desktop Analytics 연결을 만듭니다. 마지막으로 연결 상태를 모니터링합니다.


## <a name="bkmk_hotfix"></a> 사이트 업데이트

먼저 Configuration Manager 사이트가 버전 1902 이상을 실행하고 있는지 확인합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.

또한 Desktop Analytics와의 통합을 지원하기 위해 버전 1902 업데이트 롤업(4500571)을 설치해야 합니다. 이 업데이트에 대한 자세한 내용은 [Configuration Manager 현재 분기 버전 1902에 대한 업데이트 롤업](https://support.microsoft.com/help/4500571)을 참조하세요.

1. 버전 1902에 대한 업데이트 롤업을 사용하여 사이트를 업데이트합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  



## <a name="bkmk_connect"></a> 서비스에 연결

이 절차를 사용하여 Configuration Manager를 Desktop Analytics에 연결하고 디바이스 설정을 구성합니다. 이 절차는 계층을 클라우드 서비스에 연결하는 일회성 프로세스입니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 리본 메뉴에서 **Azure Services 구성**을 선택합니다.  

    > [!Tip]  
    > **Desktop Analytics Servicing** 노드에서 직접 서비스에 연결합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **Desktop Analytics Servicing** 노드를 선택합니다. *Desktop Analytics를 처음 사용하시나요?* 상자에서 *Desktop Analytics 서비스에 연결*에 대한 두 번째 링크를 선택합니다.  

2. Azure Services 마법사의 **Azure Services** 페이지에서 다음 설정을 구성합니다.  

    - Configuration Manager의 개체 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    - 사용 가능한 서비스 목록에서 **Desktop Analytics**를 선택합니다.  
  
   **다음**을 선택합니다.  

3. **App** 페이지에서 적절한 **Azure 환경**을 선택합니다. 그런 다음, 웹앱에 대한 **찾아보기**를 선택합니다.  

4. 이 서비스에 대해 다시 사용하려는 기존 앱이 있는 경우 목록에서 해당 앱을 선택하고 **확인**을 선택합니다.  

5. 대부분의 경우 이 마법사를 사용하여 Desktop Analytics 연결을 위한 앱을 만들 수 있습니다. **만들기**를 선택합니다.<!-- 3572123 -->  

    > [!Tip]  
    > 이 마법사에서 앱을 만들 수 없는 경우 Azure AD에서 수동으로 앱을 만든 다음, Configuration Manager로 가져올 수 있습니다. 자세한 내용은 [Configuration Manager용 앱 만들기 및 가져오기](/sccm/desktop-analytics/troubleshooting#create-and-import-app-for-configuration-manager)를 참조하세요.  

6. **서버 애플리케이션 만들기** 창에서 다음 설정을 구성합니다.  

    - **애플리케이션 이름**: Azure AD에 있는 앱의 식별 이름입니다.

    - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. 서비스에 대한 액세스를 요청하기 위해 Configuration Manager 클라이언트에서 사용하는 액세스 토큰에 있습니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

    - **비밀 키 유효 기간**: 드롭다운 목록에서 **1년** 또는 **2년** 중 하나를 선택합니다. 기본값은 1년입니다.  

    **로그인**을 선택합니다. Azure에 성공적으로 인증되면 페이지에 **Azure AD 테넌트 이름**이 참조용으로 표시됩니다.
        
    > [!Note]  
    > **글로벌 관리자**로 이 단계를 완료합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관 없습니다.  

    **확인**을 선택하여 Azure AD에서 웹앱을 만들고 서버 애플리케이션 만들기 대화 상자를 닫습니다. 서버 앱 대화 상자에서 **확인**을 선택합니다. 그런 다음, Azure Services 마법사의 앱 페이지에서 **다음**을 선택합니다.  

7. **진단 데이터** 페이지에서 다음 설정을 구성합니다.  

    - **상업용 ID**: 이 값은 조직의 ID로 자동으로 채워집니다. 그렇지 않은 경우 계속하기 전에 프록시 서버가 필요한 [엔드포인트](/sccm/desktop-analytics/enable-data-sharing#endpoints)를 모두 허용하도록 구성되어 있는지 확인합니다. 또는 [Desktop Analytics 포털](/sccm/desktop-analytics/monitor-connection-health#bkmk_ViewCommercialID)에서 상업용 ID를 수동으로 검색합니다.  

    - **Windows 10 진단 데이터 수준**: **기본** 이상을 선택합니다. [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)을 참조하세요.
  
    - **진단 데이터에서 디바이스 이름 허용**: **사용**을 선택합니다.  

        > [!Note]  
        > Windows 10 버전 1803부터 디바이스 이름은 기본적으로 Microsoft로 전송되지 않습니다. 디바이스 이름을 보내지 않으면 Desktop Analytics에 "알 수 없음"으로 표시됩니다. 이 동작으로 인해 디바이스를 식별하고 평가하기가 어려울 수 있습니다.  

   **다음**을 선택합니다. **사용 가능한 기능** 페이지는 이전 페이지의 진단 데이터 설정과 함께 사용할 수 있는 Desktop Analytics 기능을 보여줍니다. **다음**을 선택하여 계속하거나 **이전**을 선택하여 변경합니다.  

    ![Azure Services 마법사의 사용 가능한 기능 페이지 예제](media/available-functionality.png)

8. **컬렉션** 페이지에서 다음 설정을 구성합니다.  

    - **표시 이름**: Desktop Analytics 포털은 이 이름을 사용하여 이 Configuration Manager 연결을 표시합니다. 이를 사용하여 서로 다른 계층을 구분합니다. *테스트 랩* 또는 *프로덕션*이 예입니다.  

    - **대상 컬렉션**: 이 컬렉션에는 Configuration Manager가 상업용 ID 및 진단 데이터 설정으로 구성하는 모든 디바이스가 포함됩니다. Configuration Manager가 Desktop Analytics 서비스에 연결하는 전체 디바이스 세트입니다.  

    - **대상 컬렉션의 디바이스는 아웃바운드 통신에 사용자 인증 프록시를 사용합니다**. 기본적으로 이 값은 **아니요**입니다. 사용자 환경에 필요한 경우 **예**로 설정합니다.  

    - **Desktop Analytics와 동기화할 특정 컬렉션을 선택합니다**. **대상 컬렉션** 계층에서 추가 컬렉션을 포함하려면 **추가**를 선택합니다. 이러한 컬렉션은 Desktop Analytics 포털에서 배포 계획과 그룹화할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함해야 합니다.  <!-- 4097528 -->  

        > [!Tip]  
        > 컬렉션 선택 창에는 **대상 컬렉션**으로 제한된 컬렉션만 표시됩니다.
        >
        > 다음 예제에서는 CollectionA를 대상 컬렉션으로 선택합니다. 그런 다음, 컬렉션을 추가하면 CollectionA, CollectionB 및 CollectionC가 표시됩니다. CollectionD를 추가할 수 없습니다.
        >
        > - CollectionA: **모든 시스템** 컬렉션에 의해 제한됨
        >     - CollectionB: CollectionA로 제한됨
        >         - CollectionC: CollectionB로 제한됨
        > - CollectionD: **모든 시스템** 컬렉션에 의해 제한됨

        > [!Important]  
        > 이러한 컬렉션은 멤버 자격 변경 내용에 따라 계속 동기화됩니다. 예를 들어 배포 계획에서는 Windows 7 멤버 자격 규칙이 있는 컬렉션을 사용합니다. 이러한 디바이스가 Windows 10으로 업그레이드되고 Configuration Manager가 컬렉션 멤버 자격을 평가하면 해당 디바이스는 컬렉션 및 배포 계획에서 제외됩니다.  


9. 마법사를 완료합니다.  

Configuration Manager는 대상 컬렉션에서 디바이스를 구성하는 설정 정책을 만듭니다. 이 정책에는 디바이스가 Microsoft로 데이터를 보낼 수 있도록 하는 진단 데이터 설정이 포함되어 있습니다. 기본적으로 클라이언트는 매 시간마다 정책을 업데이트합니다. 새 설정을 받은 후 Desktop Analytics에서 데이터를 사용할 수 있으려면 몇 시간이 더 걸릴 수 있습니다.



## <a name="bkmk_monitor"></a> 연결 상태 모니터링

Desktop Analytics에 대한 디바이스 구성을 모니터링합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **Desktop Analytics Servicing** 노드를 확장하고 **Connection Health** 대시보드를 선택합니다.  

자세한 내용은 [연결 상태 모니터링](/sccm/desktop-analytics/troubleshooting#monitor-connection-health)을 참조하세요.

Configuration Manager는 연결을 만든 후 60분 이내에 컬렉션을 동기화합니다. Desktop Analytics 포털에서 **글로벌 파일럿**으로 이동하여 Configuration Manager 디바이스 컬렉션을 확인합니다.



## <a name="next-steps"></a>다음 단계

Desktop Analytics에 디바이스를 등록하려면 다음 문서로 이동합니다.
> [!div class="nextstepaction"]  
> [디바이스 등록](/sccm/desktop-analytics/enroll-devices)  
