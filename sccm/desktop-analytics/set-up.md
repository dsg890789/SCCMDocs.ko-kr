---
title: Desktop Analytics 설정
titleSuffix: Configuration Manager
description: Desktop Analytics를 설정하고 온보딩하는 방법 가이드입니다.
ms.date: 09/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7ff8d453-f24d-4230-a116-585190a663fc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2d682a7cf53c01e1e5f3d65f3143b1107436dff
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72384856"
---
# <a name="how-to-set-up-desktop-analytics"></a>Desktop Analytics를 설정하는 방법

이 절차를 사용하여 Desktop Analytics에 로그인하고 구독에서 구성합니다. 이 절차는 조직에 대해 Desktop Analytics를 설정하는 일회성 프로세스입니다.  


> [!Important]  
> Configuration Manager를 사용하는 Desktop Analytics의 일반적인 필수 구성 요소에 대한 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.  

## <a name="initial-onboarding"></a>초기 온보딩

1. **글로벌 관리자** 역할을 가진 사용자로 Microsoft 365 Device Management에서 [Desktop Analytics 포털](https://aka.ms/desktopanalytics)을 엽니다. **시작**을 선택합니다. 또는 Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **Desktop Analytics Servicing** 노드를 선택하고 **계획 배포**를 선택합니다.

2. **서비스 계약 수락** 페이지에서 서비스 계약을 검토하고 **수락**을 선택합니다.  

3. **구독 확인** 페이지에서 필요한 적격 라이선스 목록을 검토합니다. **지원되는 구독 또는 상위 구독 중 하나가 있나요?** 옆에 있는 **예**로 설정을 전환한 후, **다음**을 선택합니다.  

4. **사용자에게 액세스 권한 부여** 페이지에서 다음을 수행합니다.

    - **Desktop Analytics가 사용자를 대신하여 디렉터리 역할을 관리할 수 있도록 허용**: Desktop Analytics는 **Workspace Owners**에게 **Desktop Analytics 관리자** 역할을 자동으로 할당합니다. 이러한 그룹이 이미 **글로벌 관리자**인 경우에는 변경 내용이 없습니다.

        이 옵션을 선택하지 않으면 Desktop Analytics는 여전히 사용자를 보안 그룹의 구성원으로 추가합니다. **글로벌 관리자**는 사용자에게 **Desktop Analytics 관리자** 역할을 수동으로 할당해야 합니다.   

        Azure Active Directory에서 관리자 역할 권한을 할당하는 방법 및 **Desktop Analytics 관리자**에 할당된 권한에 대한 자세한 내용은 [Azure Active Directory의 관리자 역할 권한](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)을 참조하세요.  

    - Desktop Analytics는 Azure Active Directory의 **Workspace Owners** 보안 그룹을 미리 구성하여 작업 영역 및 배포 계획을 만들고 관리합니다. 

        사용자를 그룹에 추가하려면 **이름 또는 이메일 주소 입력** 섹션에 해당 이름 또는 이메일 주소를 입력합니다. 완료되면 **다음**을 선택합니다.

5. 페이지에서 **작업 영역을 설정**합니다.  

    - Desktop Analytics에 기존 작업 영역을 사용하려면 해당 작업 영역을 선택하고 다음 단계를 계속 진행합니다.  

        > [!Note]  
        > Azure AD 테넌트당 하나의 Desktop Analytics 작업 영역만 사용할 수 있습니다. 디바이스는 하나의 작업 영역에만 진단 데이터를 보낼 수 있습니다.  

        Windows Analytics를 이미 사용 중인 경우에는 동일한 작업 영역을 선택합니다. 이전에 Windows Analytics에 등록한 Desktop Analytics에 디바이스를 다시 등록해야 합니다.

        선택한 Windows Analytics 작업 영역에서 입력을 마이그레이션하려면 **Windows Analytics의 입력을 확인하겠습니까?** 에서 **예**로 설정합니다. 마이그레이션하지 않으려면 이 설정을 **아니요**로 전환합니다. 자세한 내용은 [기존 Windows Analytics 고객](/sccm/desktop-analytics/faq#existing-windows-analytics-customers)에 대한 FAQ를 참조하세요.

    - Desktop Analytics에 대한 작업 영역을 만들려면 **작업 영역 추가**를 선택합니다.  

        1. 전역적으로 고유한 **작업 영역 이름**을 입력합니다.<!--do we have any guidance for this name?-->  

        2. 드롭다운 목록을 선택하여 **이 작업 영역에 대한 Azure 구독 이름을 선택**하고 이 작업 영역에 대한 Azure 구독을 선택합니다.  

        3. 리소스 그룹을 **새로 만들**거나 **기존 리소스 그룹을 사용**합니다.

        4. 목록에서 **영역**을 선택한 다음, **추가**를 선택합니다.  

6. 새 작업 영역 또는 기존 작업 영역을 선택한 다음, **Desktop Analytics 작업 영역으로 설정**을 선택합니다.  그런 다음, **액세스 확인 및 허용** 대화 상자에서 **계속**을 선택합니다.  

7. 새 브라우저 탭에서 로그인하는 데 사용할 계정을 선택합니다. **조직을 대신하여 동의**하는 옵션을 선택하고 **수락**을 선택합니다.  

    > [!Note]  
    > 이 동의는 MALogAnalyticsReader 애플리케이션에 작업 영역에 대한 Log Analytics Reader 역할을 할당하는 것입니다. 이 애플리케이션 역할은 Desktop Analytics에 필요합니다. 자세한 내용은 [MALogAnalyticsReader 애플리케이션 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)을 참조하세요.  

8. 페이지에서 **작업 영역 설정**으로 돌아가 **다음**을 선택합니다.  

9. **마지막 단계** 페이지에서 **Desktop Analytics로 이동**을 선택합니다.

Azure Portal에는 Desktop Analytics **홈** 페이지가 표시됩니다.


## <a name="next-steps"></a>다음 단계

다음 문서로 이동하여 Configuration Manager를 Desktop Analytics와 연결합니다.
> [!div class="nextstepaction"]  
> [Configuration Manager 연결](/sccm/desktop-analytics/connect-configmgr)  
