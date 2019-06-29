---
title: Desktop Analytics 설정
titleSuffix: Configuration Manager
description: 데스크톱 analytics 설정 및 온 보 딩에 대 한 방법 가이드입니다.
ms.date: 06/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7ff8d453-f24d-4230-a116-585190a663fc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6658f0b7a65027715975e6075e5c18a430d38405
ms.sourcegitcommit: d8cfd0edf2579e2b08a0ca8a0a7b8f53d1e4196f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67463761"
---
# <a name="how-to-set-up-desktop-analytics"></a>데스크톱 Analytics를 설정 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석에 로그인 하 고 구독에서 구성 하려면이 절차를 따르십시오. 이 절차는 조직에 대 한 데스크톱 Analytics를 설정 하는 일회성 프로세스입니다.  



## <a name="initial-onboarding"></a>초기 온 보 딩

1. 엽니다는 [데스크톱 Analytics 포털](https://aka.ms/desktopanalytics) 사용자로 Microsoft 365 장치 관리에는 **전역 관리자** 역할. 선택 **시작**합니다.  

    > [!Tip]  
    > 에 Configuration Manager 콘솔에서 데스크톱 Analytics 포털에 액세스 하려면로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 합니다 **데스크톱 분석 서비스** 노드를 선택한 **계획 배포**합니다.

2. 에 **서비스 계약에 동의** 페이지에서 서비스 계약을 검토 하 고 선택 **Accept**합니다.  

3. 에 **구독을 확인 하** 페이지에서 라이선스를 정규화 하는 데 필요한 목록을 검토 합니다. 으로 설정을 전환한 **Yes** 옆에 **할 지원 되는 또는 더 높은 구독 중 하나**를 선택한 후 **다음**합니다.  

4. 에 **사용자가 액세스할** 페이지:

    - **사용 하면 사용자를 대신해 디렉터리 역할을 관리 하려면 데스크톱 분석**: 데스크톱 Analytics 자동으로 할당 합니다 **작업 영역 소유자** 는 **데스크톱 분석 관리자** 역할입니다. 이러한 그룹은 이미 있는 경우는 **전역 관리자**, 변경 되지 않았습니다.

        이 옵션을 선택 하지 않으면, 데스크톱 Analytics는 여전히 사용자 보안 그룹의 구성원으로 추가 합니다. A **전역 관리자** 수동으로 할당 해야 합니다 **데스크톱 분석 관리자** 사용자 역할.   

        Azure Active Directory에서 관리자 역할 권한 및 할당 된 권한을 할당 하는 방법에 대 한 자세한 내용은 **데스크톱 Analytics Administrators**를 참조 하세요 [azure에서 관리자 역할 권한 Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)합니다.  

    - 데스크톱 분석 미리 구성 된 **작업 영역 소유자** 배포 계획 및 작업 영역 만들기 및 관리 하도록 Azure Active Directory 보안 그룹입니다. 

        사용자 그룹에 추가할에서 해당 이름 또는 전자 메일 주소를 입력 합니다 **이름이 나 전자 메일 주소 입력** 섹션입니다. 완료 되 면 선택 **다음**합니다.

5. 페이지에서 **작업 영역 설정**:  

    > [!Note]  
    > 이 단계에서는 사용자가 필요한 데 **작업 영역 소유자** 권한 및 Azure 구독 및 리소스 그룹에 대 한 추가 액세스 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)합니다.  

    - 기존 작업 영역에 데스크톱 Analytics를 사용 하려면를 선택 하 고 단계를 진행 합니다.  

        > [!Note]  
        > Windows Analytics를 이미 사용 중인 경우에 동일한 작업 영역을 선택 합니다. Windows Analytics에서 이전에 등록 하는 데스크톱 분석 하는 장치를 등록 해야 합니다.
        >
        > Azure AD 테 넌 트 당 하나의 데스크톱 분석 작업 영역을만 있습니다. 장치만 하나의 작업 영역에 진단 데이터를 보낼 수 있습니다.  

    - 데스크톱 분석을 위해 작업 영역을 만들려면 **작업 영역 추가**합니다.  

        1. 입력 한 **작업 영역 이름**합니다.<!--do we have any guidance for this name?-->  

        2. 드롭다운 목록 선택 **이 작업 영역에 대 한 Azure 구독 이름을 선택**,이 작업 영역에 대 한 Azure 구독을 선택 합니다.  

        3. **새로 만들기** 리소스 그룹 또는 **기존 항목 사용**합니다.

        4. 선택 된 **지역** 을 선택 하 고 목록에서 **추가**합니다.  

6. 새 또는 기존 작업 영역을 선택한 후 **데스크톱 Analytics 작업 영역으로 설정**합니다.  선택한 **계속** 에 **Confirm 및 권한 부여 액세스** 대화 합니다.  

7. 새 브라우저 탭에서 계정을 사용 하 여 로그인을 선택 합니다. 옵션을 선택 **조직을 대신 하 여 동의** 선택한 **Accept**합니다.  

    > [!Note]  
    > 이 동의 MALogAnalyticsReader 응용 프로그램 작업 영역에 대 한 Log Analytics Reader 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석 필요 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)입니다.  

8. 페이지에서 다시 **작업 영역 설정**를 선택 **다음**합니다.  

9. 에 **마지막 단계** 페이지에서 **Desktop Analytics로 이동**합니다.

Azure portal에 데스크톱 분석을 보여 줍니다 **홈** 페이지입니다.


## <a name="next-steps"></a>다음 단계

데스크톱 Analytics를 사용 하 여 Configuration Manager를 연결 하려면 다음 문서로 계속 진행 하세요.
> [!div class="nextstepaction"]  
> [Configuration Manager 연결](/sccm/desktop-analytics/connect-configmgr)  
