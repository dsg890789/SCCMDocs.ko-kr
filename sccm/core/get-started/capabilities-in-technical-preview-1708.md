---
title: 기술 미리 보기 1708
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 기술 미리 보기 버전 1708에서 사용할 수 있는 기능을 알아봅니다.
ms.date: 08/25/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3c061ceb-3bdb-4d4f-8c60-344964bd416b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e3cb09f6220f7a0fd57960a9b46087a25ee81c5
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67677343"
---
# <a name="capabilities-in-technical-preview-1708-for-system-center-configuration-manager"></a>System Center Configuration Manager용 기술 미리 보기 1708의 기능

*적용 대상: System Center Configuration Manager(기술 미리 보기)*

이 문서에서는 System Center Configuration Manager용 기술 미리 보기 버전 1708에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**이 Technical Preview의 알려진 문제:**
- **수동 모드의 사이트 서버가 있는 경우 미리 보기 1708 버전에 대한 업데이트가 실패합니다**. 미리 보기 1706 또는 1707 버전을 실행하고 [수동 모드의 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 경우 미리 보기 사이트를 1708 버전으로 성공적으로 업데이트하려면 먼저 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 1708 버전을 실행한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.




**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager"></a>Configuration Manager에서 PowerShell 스크립트를 배포할 때 매개 변수를 지정하도록 향상된 기능
<!-- 1236459 -->

Configuration Manager 1706 이상에서는 [Configuration Manager 콘솔에서 PowerShell 스크립트를 만들고 실행할 수 있습니다](/sccm/apps/deploy-use/create-deploy-scripts).

[기술 미리 보기 1707](/sccm/core/get-started/capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)에서 이 기능을 확장하여 Configuration Manager에서 스크립트의 매개 변수를 읽을 수 있게 했습니다.

이 기술 미리 보기에서는 스크립트 매개 변수 기능을 확장하여 필수 매개 변수와 선택적 매개 변수를 감지하고 이러한 매개 변수를 입력하라는 메시지를 표시합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

1. 지침에 따라 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 수행하세요.
2. **스크립트 만들기 마법사**의 새 **스크립트 매개 변수** 페이지에서 매개 변수를 선택한 다음 해당 값을 편집합니다.
마법사에는 필수 매개 변수와 선택적 매개 변수가 표시됩니다.
4. 매개 변수 편집을 완료하면 마법사를 완료합니다.

스크립트 실행 시 구성된 매개 변수 값이 사용됩니다. 필수 매개 변수를 구성하지 않은 경우 스크립트가 실행될 때 해당 매개 변수를 제공하라는 메시지가 최종 사용자에게 표시됩니다.

## <a name="management-insights"></a>관리 정보
<!-- 1353967 -->
이제는 사이트 데이터베이스의 데이터 분석에 따라 현재의 환경 상태에 대한 정보를 얻을 수 있습니다. 이 정보를 통해 환경을 더 잘 이해하고 해당 정보에 기반한 조치를 취할 수 있습니다. Configuration Manager 콘솔의 **관리** > **관리 정보** > **모든 정보**에서 관리 정보를 검토합니다. 이제 이 릴리스에서 사용할 수 있는 정보는 다음과 같습니다.

- **배포가 없는 애플리케이션**: 사용자 환경에서 활성 배포가 없는 애플리케이션을 나열합니다. 이렇게 하면 사용되지 않는 애플리케이션을 찾고 삭제하여 콘솔에 표시된 애플리케이션 목록을 간소화할 수 있습니다.
- **빈 컬렉션**: 사용자 환경에서 멤버가 없는 컬렉션을 나열합니다. 이러한 컬렉션을 삭제하여 개체를 배포할 때와 같이 표시되는 컬렉션 목록을 간소화할 수 있습니다.


## <a name="restart-computers-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 컴퓨터 다시 시작   
<!-- 1356283 -->
이 릴리스부터 Configuration Manager 콘솔을 사용하여 다시 시작해야 하는 클라이언트 디바이스를 식별한 다음 클라이언트 알림 작업을 통해 해당 디바이스를 다시 시작할 수 있습니다.

다시 시작을 보류 중인 디바이스를 확인하려면**자산 및 준수** > **디바이스**로 차례로 이동하여 다시 시작해야 할 수 있는 디바이스가 포함된 컬렉션을 선택합니다. 컬렉션을 선택하면 세부 정보 창의 **다시 부팅 보류 중**이라는 새로운 열에서 각 디바이스에 대한 상태를 확인할 수 있습니다. 각 디바이스의 값은 **예** 또는 **아니요**입니다.

디바이스를 다시 시작하라는 클라이언트 알림을 만들려면
1. 콘솔의 [디바이스] 노드에서 다시 시작하려는 디바이스를 찾습니다.
2. 해당 디바이스를 마우스 오른쪽 단추로 클릭하고 **클라이언트 알림**을 선택한 다음 **다시 부팅**을 선택합니다. 이렇게 하면 다시 시작에 대한 정보 창이 열립니다. **확인**을 클릭하여 다시 시작 요청을 확인합니다.

클라이언트에서 알림을 받으면 **소프트웨어 센터** 알림 창이 열려 사용자에게 다시 시작을 알려줍니다. 기본적으로 90분 후에 다시 시작됩니다. [클라이언트 설정](/sccm/core/clients/deploy/configure-client-settings)을 구성하여 다시 시작 시간을 수정할 수 있습니다. 다시 시작 동작에 대한 설정은 기본 설정의 [컴퓨터 다시 시작](/sccm/core/clients/deploy/about-client-settings#computer-restart) 탭에 있습니다.


### <a name="try-it-out"></a>기능 직접 사용해 보기
다음 작업을 완료한 다음 리본 메뉴의 **홈** 탭에서 **사용자 의견**을 전송하여 작동 상황을 알려주세요.
1. 다시 시작하여 설치를 완료해야 하는 디바이스에 응용 프로그램 또는 업데이트를 배포합니다.
2. 콘솔의 **자산 및 준수** > **디바이스** 노드에서 디바이스를 찾은 다음 **다시 부팅 보류 중** 열에서 **예**가 표시되는지 확인합니다 . [다시 부팅 보류 중] 상태가 콘솔에 반영되는 데 최대 20분이 걸릴 수 있습니다.
3. 디바이스를 모니터링하여 소프트웨어 센터 알림이 열리고 디바이스가 성공적으로 다시 시작되는지 확인합니다.


## <a name="software-center-customization"></a>소프트웨어 센터 사용자 지정
<!-- 1351224 -->
엔터프라이즈 브랜딩 요소를 추가하고 소프트웨어 센터에서 탭의 표시 여부를 지정할 수 있습니다. 소프트웨어 센터 특정의 회사 이름을 추가하고 소프트웨어 센터 구성 색 테마, 회사 로고 및 클라이언트 디바이스에 대한 표시 탭을 설정할 수 있습니다.

### <a name="customize-software-center"></a>소프트웨어 센터 사용자 지정

소프트웨어 센터를 수정하려면

1. **Configuration Manager** 콘솔에서 **관리** > **클라이언트 설정**을 차례로 선택합니다. 원하는 클라이언트 설정 인스턴스를 클릭합니다.
2. **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.
3. **기본 설정** 대화 상자에서 **소프트웨어 센터**를 선택합니다.
4. **새 설정을 선택하여 회사 정보 지정**에 **예**를 선택하여 소프트웨어 센터 사용자 지정 설정을 사용하도록 설정합니다.
5. **회사 이름**을 입력합니다.
6. **소프트웨어 센터에 대한 색 구성표**를 선택합니다.
7. **찾아보기**를 클릭하여 소프트웨어 센터에 대한 로고를 탐색합니다. 로고는 400 x 100 픽셀의 JPEG 또는 PNG여야 하며 최대 크기는 750KB입니다.
8. 클라이언트 디바이스에 대한 소프트웨어 센터에 탭이 표시되도록 하려면 **예**를 선택합니다. 다음과 같은 탭 중 하나 이상이 표시되어야 합니다.

    -  애플리케이션 사용 탭
    -  업데이트 사용 탭
    -  운영 체제 사용 탭
    -  설치 상태 사용 탭
    -  디바이스 준수 사용 탭
    -  옵션 사용 탭

### <a name="next-steps"></a>다음 단계

Configuration Manager의 애플리케이션 관리에 대한 자세한 내용은 [System Center Configuration Manager의 애플리케이션 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.
