---
title: "응용 프로그램 만들기 및 배포 | System Center Configuration Manager"
description: "기간 업무 앱이 포함된 응용 프로그램을 만들어 배포하고 앱을 효과적으로 관리하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 12653342e2e311a9bbfc2a7aad3101c0e7f0bce0


---
# <a name="create-and-deploy-an-application-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 응용 프로그램 만들기 및 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 바로 System Center Configuration Manager를 사용하여 응용 프로그램을 만듭니다. 이 예제에서는 Windows PC용 LOB(기간 업무) 앱이 포함된 **Contoso.msi** 라는 응용 프로그램을 만들어 배포합니다. 회사에서 Windows 10을 실행하는 모든 PC에 이 응용 프로그램을 설치해야 합니다. 이 과정에서 응용 프로그램을 효과적으로 관리하기 위해 수행할 수 있는 많은 작업을 살펴보겠습니다.  

 이 절차는 Configuration Manager 응용 프로그램을 만들어 배포하는 방법을 간략하게 설명하기 위한 것입니다. 그러나 구성할 수 있는 모든 옵션이나 다른 플랫폼용 응용 프로그램을 만들어 배포하는 방법은 설명하지 않습니다.  

 각 플랫폼과 관련된 자세한 내용은 다음 항목 중 하나를 참조하세요.  

-   [Windows 응용 프로그램 만들기](../../apps/get-started/creating-windows-applications.md)  
-   [iOS 응용 프로그램 만들기](../../apps/get-started/creating-ios-applications.md)  
-   [Android 응용 프로그램 만들기](../../apps/get-started/creating-android-applications.md)  
-   [Windows Phone 응용 프로그램 만들기](../../apps/get-started/creating-windows-phone-applications.md)  
-   [Mac 컴퓨터 응용 프로그램 만들기](../../apps/get-started/creating-mac-computer-applications.md)  
-   [Linux 및 UNIX 서버 응용 프로그램 만들기](../../apps/get-started/creating-linux-and-unix-server-applications.md) 
-   [Windows Embedded 응용 프로그램 만들기](../../apps/get-started/creating-windows-embedded-applications.md) 

  
Configuration Manager 응용 프로그램에 이미 익숙한 경우에는 이 항목을 건너뛰어도 됩니다. 그러나 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 검토하여 응용 프로그램을 만들어 배포할 때 사용할 수 있는 모든 옵션을 알아보는 것이 좋습니다.  
  
## <a name="before-you-start"></a>시작하기 전에  

[응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management)의 내용을 검토하여 응용 프로그램을 설치할 수 있도록 사이트가 준비되고 이 항목에서 사용되는 용어를 알고 있는지 확인합니다.  

 또한 **Contoso.msi** 앱의 설치 파일이 액세스 가능한 네트워크 위치에 있는지 확인합니다.  
  
## <a name="create-the-configuration-manager-application"></a>Configuration Manager 응용 프로그램 만들기  
  
### <a name="start-the-create-application-wizard-and-create-the-application"></a>응용 프로그램 만들기 마법사 시작 및 응용 프로그램 만들기  
  
1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램**을 클릭합니다.  
  
3.  **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 클릭합니다.  

4.  **응용 프로그램 만들기 마법사** 의 **일반**페이지에서 **설치 파일에서 이 응용 프로그램에 대한 정보 자동 검색**을 선택합니다. 마법사의 일부 정보가 설치 .msi 파일에서 추출한 정보로 채워진 후 다음 정보를 지정합니다.  

    -   **형식** - **Windows Installer(\*.msi 파일)**를 선택합니다.  

    -   **위치** -설치 파일 **Contoso.msi** 의 위치를 입력하거나 **찾아보기**를 클릭하여 위치를 선택합니다. Configuration Manager에서 설치 파일을 찾으려면 위치를 *\\\Server\Share\File* 형식으로 지정해야 합니다.  
  
    다음 스크린샷과 같이 지정합니다.  
  
    ![앱 관리 마법사 일반 페이지](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  
  
5.  **다음**을 클릭합니다. **정보 가져오기** 페이지에 Configuration Manager로 가져온 앱 및 관련된 모든 파일에 대한 일부 정보가 표시됩니다. 완료되면 다시 **다음** 을 클릭합니다.  

6.  **일반 정보** 페이지에서 응용 프로그램에 대한 추가 정보를 제공하면 Configuration Manager 콘솔에서 정렬하고 찾는 데 도움이 됩니다.  

     또한 설치 프로그램 필드를 통해 PC에 응용 프로그램을 설치하는 데 사용할 전체 명령줄을 지정할 수 있습니다. 이 필드를 편집하여 사용자 고유의 속성을 추가할 수 있습니다(예: 무인 설치의 경우 **/q** ).  

    > [!TIP]  
    >  마법사의 이 페이지에 있는 일부 필드는 응용 프로그램 설치 파일을 가져올 때 자동으로 채워졌을 수 있습니다.  

     아래 스크린샷과 유사한 화면이 표시됩니다.  
  
     ![앱 관리 마법사 일반 정보 페이지](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  
  
7.  **다음**을 클릭합니다. 요약 페이지에서 응용 프로그램 설정을 확인한 후 마법사를 완료할 수 있습니다.  

 앱을 만드는 작업을 완료했습니다. 앱을 찾으려면 **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리**를 확장하고 **응용 프로그램**을 클릭합니다. 이 예제에서는 다음과 같이 표시됩니다.  
  
 ![최종 앱 그래픽](/sccm/apps/get-started/media/Final-app-graphic.png)  
  
## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>응용 프로그램 및 배포 유형의 속성 검사  

이제 응용 프로그램을 만들었으며, 필요한 경우 응용 프로그램 설정을 구체화할 수 있습니다. 응용 프로그램 속성을 확인하려면 앱을 선택한 다음 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

 **<Contoso\> 응용 프로그램 속성** 대화 상자에는 응용 프로그램의 동작을 미세 조정하기 위해 구성할 수 있는 많은 항목이 표시됩니다. 구성할 수 있는 모든 설정에 대한 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요. 이 예제의 목적을 위해 응용 프로그램 배포 유형의 일부 속성을 변경하겠습니다.  
  
 **배포 유형** 탭에서 **Contoso 응용 프로그램** 배포 유형을 선택하고 **편집**을 클릭합니다.   
다음과 같은 대화 상자가 표시됩니다.  
 
![앱 관리 앱 속성 페이지](/sccm/apps/get-started/media/App-management-app-properties-page.png)  
  
## <a name="add-a-requirement-to-the-deployment-type"></a>배포 유형에 요구 사항 추가  
 요구 사항은 장치에 응용 프로그램을 설치하기 전에 충족해야 하는 조건을 지정합니다.  기본 제공 요구 사항에서 선택하거나 직접 만들 수 있습니다. 이 예제에서는 Windows 10을 실행하는 PC에만 응용 프로그램을 설치해야 하는 요구 사항을 추가합니다.  
  
1.  방금 열린 배포 유형 속성 페이지에서 **요구 사항** 탭을 클릭합니다.  

2.  **추가** 를 클릭하여 **요구 사항 만들기** 대화 상자를 엽니다.  

3.  **요구 사항 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **범주** - **장치**  

    -   **조건** - **운영 체제**  

    -   **규칙 유형** - **값**  

    -   **연산자** - **One of(그중 하나)**  

    -   운영 체제 목록에서 **Windows 10**을 선택합니다.  
  
    다음과 같은 대화 상자가 표시됩니다.  
  
    ![앱 관리 요구 사항 페이지](/sccm/apps/get-started/media/App-management-requirements-page.png)  
  
4.  **확인**을 클릭하여 열린 각 속성 페이지를 닫고 Configuration Manager 콘솔의 **응용 프로그램** 목록으로 돌아갑니다.  

> [!TIP]  
>  요구 사항을 통해 필요한 Configuration Manager 컬렉션 수를 줄일 수 있습니다. Windows 10을 실행하는 PC에만 응용 프로그램을 설치할 수 있도록 지정했으므로 나중에 다른 여러 운영 체제를 실행하는 PC가 포함된 컬렉션에 배포할 수 있으며, 응용 프로그램은 Windows 10에만 설치됩니다.  
  
## <a name="add-the-application-content-to-a-distribution-point"></a>배포 지점에 응용 프로그램 콘텐츠 추가  

PC에 응용 프로그램을 성공적으로 배포하기 위해서는 다음에 응용 프로그램 콘텐츠가 배포 지점에 복사되었는지 확인해야 합니다. PC는 응용 프로그램을 설치하는 배포 지점에 액세스합니다.  

> [!TIP]  
>  Configuration Manager의 배포 지점 및 콘텐츠 관리에 대해 자세히 알아보려면 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  
  
1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램** 을 확장하고, 응용 프로그램 목록에서 앞서 만든 **Contoso 응용 프로그램** 을 선택합니다.  

3.  **홈** 탭의 **배포** 그룹에서 **콘텐츠 배포**를 클릭합니다.  

4.  **콘텐츠 배포 마법사** 의 **일반**페이지에서, 응용 프로그램 이름이 올바른지 확인하고 **다음**을 클릭합니다.  

5.  **콘텐츠** 페이지에서 배포 지점에 복사할 정보를 검토하고 **다음**을 클릭합니다.  

6.  **콘텐츠 대상** 페이지에서 추가를 클릭하여 응용 프로그램 콘텐츠를 설치할 하나 이상의 배포 지점 또는 배포 지점 그룹을 선택합니다.  

7.  마법사를 완료합니다.  

 **모니터링** 작업 영역의 **배포 상태** > **콘텐츠 상태**에서 응용 프로그램을 만듭니다.  
  
## <a name="deploy-the-application"></a>응용 프로그램 배포  

이제, 계층 구조의 장치 컬렉션에 응용 프로그램을 배포합니다. 이 예제에서는 **모든 시스템** 장치 컬렉션에 응용 프로그램을 배포합니다.  

> [!TIP]  
>  이전에 선택한 요구 사항 때문에 Windows 10 컴퓨터에서만 응용 프로그램을 설치합니다.  
  
1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램**을 클릭합니다.  
  
3.  응용 프로그램의 목록에서 앞서 만든 응용 프로그램인 **Contoso 응용 프로그램**을 선택한 다음, **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

4.  **소프트웨어 배포 마법사** 의 **일반**페이지에서, **찾아보기** 를 클릭하여 **모든 시스템** 장치 컬렉션을 선택합니다.  

5.  **콘텐츠** 페이지에서 응용 프로그램을 설치할 PC의 배포 지점이 선택되었는지 확인합니다.  

6.  **배포 설정** 페이지에서 배포 작업이 **설치**로 설정되어 있고, 배포 용도가 **필수**로 설정되어 있는지 확인합니다.  

    > [!TIP]  
    >  배포 목적을 **필수**로 설정하면 응용 프로그램이 설정된 요구 사항을 충족하는 PC에 설치됩니다. 이 값을 **사용 가능**으로 설정하면 사용자가 필요 시 소프트웨어 센터에서 응용 프로그램을 설치할 수 있습니다.  

7.  **일정** 페이지에서 응용 프로그램이 설치되는 시기를 구성할 수 있습니다. 이 예에서는 **사용 가능해지면 되도록 빨리**를 선택합니다.  

8.  **사용자 환경** 페이지에서, **다음**을 클릭하여 기본값을 적용합니다.  

9. 마법사를 완료합니다.  

 아래의 **응용 프로그램 모니터링** 섹션의 내용을 참조하여 응용 프로그램 배포의 상태를 확인합니다.  
  
## <a name="monitor-the-application"></a>응용 프로그램 모니터링  
 이 섹션에서는 방금 배포된 응용 프로그램의 배포 상태를 빠르게 확인합니다.  
  
### <a name="to-review-the-deployment-status"></a>배포 상태를 검토하려면  
  
1.  Configuration Manager 콘솔에서 **모니터링** > **배포**를 클릭합니다.  
  
3.  배포의 목록에서 **Contoso 응용 프로그램**을 선택합니다.  

4.  **홈** 탭의 **배포** 그룹에서 **상태 보기**를 클릭합니다.  

5.  다음 탭 중 하나를 선택하여 응용 프로그램 배포에 대한 자세한 상태를 확인합니다.  

    -   **성공** - 응용 프로그램이 표시된 PC에 성공적으로 설치되었습니다.  

    -   **진행 중** - 응용 프로그램이 아직 설치를 완료하지 않았습니다.  

    -   **오류** - 표시된 PC에 응용 프로그램을 설치하는 동안 오류가 발생했습니다. 오류에 대한 자세한 내용도 표시됩니다.  

    -   **요구 사항에 맞지 않음** - 표시된 장치가 구성된 요구 사항에 맞지 않아서(이 예제에서는 Windows 10을 실행하지 않아서) 응용 프로그램이 해당 장치에 설치하려고 하지 않았습니다.  

    -   **알 수 없음** - Configuration Manager에서 배포 상태를 보고할 수 없습니다. 나중에 다시 확인하세요.  

> [!TIP]  
>  몇 가지 방법으로 응용 프로그램 배포를 모니터링할 수 있습니다. 자세한 내용은 [응용 프로그램 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)을 참조하세요.  
  
## <a name="end-user-experience"></a>최종 사용자 환경  

Configuration Manager를 통해 관리되는 Windows 10을 실행하는 PC의 사용자에게는 Contoso 응용 프로그램을 설치해야 한다는 메시지가 곧 표시됩니다. 사용자가 설치에 동의하면 응용 프로그램이 설치됩니다.  



<!--HONumber=Nov16_HO1-->


