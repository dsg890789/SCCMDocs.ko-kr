---
title: Desktop Analytics 설정
titleSuffix: Configuration Manager
description: 데스크톱 분석을 설정 하 고 등록 하는 방법에 대 한 지침입니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72384856"
---
# <a name="how-to-set-up-desktop-analytics"></a>데스크톱 분석을 설정 하는 방법

이 절차를 사용 하 여 데스크톱 분석에 로그인 하 고 구독에서 구성 합니다. 이 절차는 조직에 대 한 데스크톱 분석을 설정 하는 일회성 프로세스입니다.  


> [!Important]  
> Configuration Manager 사용 하는 데스크톱 분석의 일반적인 필수 구성 요소에 대 한 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조 하세요.  

## <a name="initial-onboarding"></a>초기 온 보 딩

1. **전역 관리자** 역할이 있는 사용자로 Microsoft 365 장치 관리에서 [데스크톱 분석 포털](https://aka.ms/desktopanalytics) 을 엽니다. **시작**을 선택 합니다. 또는 Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **데스크톱 분석 서비스** 노드를 선택 하 고 **배포 계획**을 선택 합니다.

2. **서비스 계약 수락** 페이지에서 서비스 계약을 검토 하 고 **동의**를 선택 합니다.  

3. **구독 확인** 페이지에서 필요한 적격 라이선스 목록을 검토 합니다. **지원 되는 구독 중 하나 이상이 있습니까?** 옆의 설정을 **예** 로 전환 하 **고 다음을 선택 합니다**.  

4. 사용자에 게 **액세스 권한 부여** 페이지에서 다음을 수행 합니다.

    - **사용자를 대신해 데스크톱 분석에서 디렉터리 역할을 관리할 수 있도록 허용**: desktop Analytics는 **작업 영역 소유자** 에 게 자동으로 **데스크톱 분석 관리자** 역할을 할당 합니다. 해당 그룹이 이미 **전역 관리자**인 경우에는 변경 내용이 없습니다.

        이 옵션을 선택 하지 않으면 데스크톱 분석에서 여전히 사용자를 보안 그룹의 구성원으로 추가 합니다. **전역 관리자** 는 사용자에 대 한 **데스크톱 분석 관리자** 역할을 수동으로 할당 해야 합니다.   

        Azure Active Directory에서 관리자 역할 사용 권한을 할당 하는 방법과 **데스크톱 분석 관리자**에 게 할당 된 사용 권한에 대 한 자세한 내용은 [Azure Active Directory의 관리자 역할 권한](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)을 참조 하세요.  

    - 데스크톱 분석은 Azure Active Directory의 **작업 영역 소유자** 보안 그룹을 미리 구성 하 여 작업 영역 및 배포 계획을 만들고 관리 합니다. 

        그룹에 사용자를 추가 하려면 **이름 또는 전자 메일 주소 입력** 섹션에 해당 이름 또는 전자 메일 주소를 입력 합니다. 완료 되 면 **다음**을 선택 합니다.

5. 페이지에서 **작업 영역을 설정**합니다.  

    - 데스크톱 분석에 기존 작업 영역을 사용 하려면 해당 작업 영역을 선택 하 고 다음 단계를 계속 진행 합니다.  

        > [!Note]  
        > Azure AD 테 넌 트 당 하나의 데스크톱 분석 작업 영역만 사용할 수 있습니다. 장치는 하나의 작업 영역에만 진단 데이터를 보낼 수 있습니다.  

        Windows Analytics를 이미 사용 중인 경우에는 동일한 작업 영역을 선택 합니다. 이전에 Windows Analytics에 등록 한 데스크톱 분석에 장치를 했다가 해야 합니다.

        선택한 Windows Analytics 작업 영역에서 입력을 마이그레이션하려면 **Windows analytics에서 입력을 확인** 하 시겠습니까?를 **예**로 설정 합니다. 마이그레이션하지 않으려면이 설정을 **아니요**로 전환 합니다. 자세한 내용은 [기존 Windows Analytics 고객](/sccm/desktop-analytics/faq#existing-windows-analytics-customers)에 대 한 FAQ를 참조 하세요.

    - 데스크톱 분석의 작업 영역을 만들려면 **작업 영역 추가**를 선택 합니다.  

        1. 전역적으로 고유한 **작업 영역 이름을**입력 합니다.<!--do we have any guidance for this name?-->  

        2. 드롭다운 목록을 선택 하 여 **이 작업 영역에 대 한 azure 구독 이름을 선택**하 고이 작업 영역에 대 한 azure 구독을 선택 합니다.  

        3. **새로 만들기** 리소스 그룹 또는 **기존**리소스 그룹을 사용 합니다.

        4. 목록에서 **지역을** 선택 하 고 **추가**를 선택 합니다.  

6. 새 또는 기존 작업 영역을 선택한 다음 **데스크톱 분석 작업 영역으로 설정**을 선택 합니다.  그런 다음 **액세스 확인 및 부여** 대화 상자에서 **계속** 을 선택 합니다.  

7. 새 브라우저 탭에서 로그인 하는 데 사용할 계정을 선택 합니다. **조직을 대신** 하 여 동의 하는 옵션을 선택 하 고 **동의**를 선택 합니다.  

    > [!Note]  
    > 이러한 동의는 MALogAnalyticsReader 응용 프로그램에 작업 영역에 대 한 Log Analytics 판독기 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석에 필요 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](/sccm/desktop-analytics/troubleshooting#bkmk_MALogAnalyticsReader)을 참조 하세요.  

8. 페이지로 돌아가 **작업 영역을 설정**하 고 **다음**을 선택 합니다.  

9. **마지막 단계** 페이지에서 **데스크톱 분석으로 이동**을 선택 합니다.

Azure Portal에는 데스크톱 분석 **홈** 페이지가 표시 됩니다.


## <a name="next-steps"></a>다음 단계

다음 문서로 이동 하 여 데스크톱 분석과 Configuration Manager 연결 합니다.
> [!div class="nextstepaction"]  
> [연결 Configuration Manager](/sccm/desktop-analytics/connect-configmgr)  
