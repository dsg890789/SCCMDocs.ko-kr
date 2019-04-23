---
title: Desktop Analytics 설정
titleSuffix: Configuration Manager
description: 데스크톱 analytics 설정 및 온 보 딩에 대 한 방법 가이드입니다.
ms.date: 04/15/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7ff8d453-f24d-4230-a116-585190a663fc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: b75b82f632c8bfbbc11a2b11d58ab83116e2180a
ms.sourcegitcommit: d23ccf7b95e6c2a6b156975194ebbc375cb5e6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124440"
---
# <a name="how-to-set-up-desktop-analytics"></a>데스크톱 Analytics를 설정 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석에 로그인 하 고 구독에서 구성 하려면이 절차를 따르십시오. 이 절차는 조직에 대 한 데스크톱 Analytics를 설정 하는 일회성 프로세스입니다.  



## <a name="initial-onboarding"></a>초기 온 보 딩

1. 사용자로 Microsoft 365 장치 관리에서 데스크톱 Analytics 포털을 엽니다 **회사 관리자** 권한. 선택 **시작**합니다.  

2. 에 **서비스 계약에 동의** 페이지에서 서비스 계약을 검토 하 고 선택 **Accept**합니다.  

3. 에 **구독을 확인 하** 페이지에서 라이선스를 정규화 하는 데 필요한 목록을 검토 합니다. 으로 설정을 전환한 **Yes** 옆에 **할 지원 되는 또는 더 높은 구독 중 하나**를 선택한 후 **다음**합니다.  

4. 에 **사용자가 액세스할** 페이지:

    - **사용자에 대 한 디렉터리 역할을 관리 하려면 데스크톱 분석 하려는**: 데스크톱 Analytics 자동으로 할당 합니다 **작업 영역 소유자** 및 **작업 영역 참가자** 그룹을 **데스크톱 분석 관리자** 역할. 이러한 그룹은 이미 있는 경우는 **전역 관리자**, 변경 되지 않았습니다.  

        이 옵션을 선택 하지 않으면, 데스크톱 Analytics는 여전히 사용자 두 보안 그룹의 구성원으로 추가 합니다. A **전역 관리자** 수동으로 할당 해야 합니다 **데스크톱 분석 관리자** 사용자 역할.  

        Azure Active Directory에서 관리자 역할 권한 및 할당 된 권한을 할당 하는 방법에 대 한 자세한 내용은 **데스크톱 Analytics Administrators**를 참조 하세요 [azure에서 관리자 역할 권한 Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)합니다.  

    - 데스크톱 Analytics Azure Active Directory에서 두 개의 보안 그룹 같은 미리 구성합니다.:  

        - **작업 영역 소유자**: 보안 그룹을 만들고 작업 영역을 관리 합니다. 이러한 계정은 Azure 구독에 대 한 소유자 액세스를 해야합니다.  

        - **작업 영역 참가자**: 보안 그룹을 만들고이 작업 영역에서 배포 계획을 관리 합니다. 모든 추가 Azure 액세스할이 필요는 없습니다.  

        각 그룹에 사용자를 추가할에서 해당 이름 또는 전자 메일 주소를 입력 합니다 **이름 또는 전자 메일 주소 입력** 적절 한 그룹의 섹션입니다. 완료 되 면 선택 **다음**합니다.

다음 단계를 완료할 수 있습니다는 **작업 영역 소유자** 하거나 **참가자**합니다. 참조 [필수 구성 요소입니다.](/sccm/desktop-analytics/overview#prerequisites) 

5. 페이지에서 **작업 영역 설정**:  

    - 기존 작업 영역에 데스크톱 Analytics를 사용 하려면를 선택 하 고 단계를 진행 합니다.  

        > [!Note]  
        > Windows Analytics를 이미 사용 중인 경우에 동일한 작업 영역을 선택 합니다. Windows Analytics에서 이전에 등록 하는 데스크톱 분석 하는 장치를 등록 해야 합니다.
        >
        > Azure AD 테 넌 트 당 하나의 데스크톱 분석 작업 영역을만 있습니다. 장치만 하나의 작업 영역에 진단 데이터를 보낼 수 있습니다.  

    - 데스크톱 분석을 위해 작업 영역을 만들려면 **작업 영역 추가**합니다.  

        1. 입력 한 **작업 영역 이름**합니다.<!--do we have any guidance for this name?-->  

        2. 드롭다운 목록 선택 **이 작업 영역에 대 한 Azure 구독 이름을 선택**,이 작업 영역에 대 한 Azure 구독을 선택 합니다.  

        3. 선택 된 **지역** 을 선택 하 고 목록에서 **추가**합니다.  

6. 새 또는 기존 작업 영역을 선택한 후 **데스크톱 Analytics 작업 영역으로 설정**합니다.  선택한 **계속** 에 **Confirm 및 권한 부여 액세스** 대화 합니다.  

7. 새 브라우저 탭에서 계정을 사용 하 여 로그인을 선택 합니다. 옵션을 선택 **조직을 대신 하 여 동의** 선택한 **Accept**합니다.  

    > [!Note]  
    > 이 동의 MALogAnalyticsReader 응용 프로그램 작업 영역에 대 한 Log Analytics Reader 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석 필요 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)입니다.  

8. 페이지에서 다시 **작업 영역 설정**를 선택 **다음**합니다.  

9. 에 **마지막 단계** 페이지에서 **Desktop Analytics로 이동**합니다.

Azure portal에 데스크톱 분석을 보여 줍니다 **홈** 페이지입니다.



## <a name="create-app-for-configuration-manager"></a>Configuration Manager에 대 한 app 만들기

Configuration Manager에 대 한 Azure AD에서 앱을 만듭니다.

1. 엽니다는 [Azure portal](http://portal.azure.com) 회사 관리자 권한이 있는 사용자로 이동 **Azure Active Directory**를 선택한 **앱 등록**합니다. 선택한 **새 응용 프로그램 등록**합니다.  

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



## <a name="next-steps"></a>다음 단계

데스크톱 Analytics를 사용 하 여 Configuration Manager를 연결 하려면 다음 문서로 계속 진행 하세요.
> [!div class="nextstepaction"]  
> [Configuration Manager 연결](/sccm/desktop-analytics/connect-configmgr)  
