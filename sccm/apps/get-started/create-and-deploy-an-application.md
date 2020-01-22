---
title: 애플리케이션 만들기 및 배포
titleSuffix: Configuration Manager
description: 기간 업무 앱이 포함된 애플리케이션을 만들어 배포하고 앱을 효과적으로 관리하는 방법을 알아봅니다.
ms.date: 07/19/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 59eba57edbed0eb281074345dfa13e869fffe793
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76033186"
---
# <a name="create-and-deploy-an-application-with-configuration-manager"></a>Configuration Manager를 사용하여 애플리케이션 만들기 및 배포

*적용 대상: Configuration Manager(현재 분기)*

이 항목에서는 바로 Configuration Manager를 사용하여 애플리케이션을 만듭니다. 이 예제에서는 Windows PC용 LOB(기간 업무) 앱이 포함된 **Contoso.msi**라는 애플리케이션을 만들어 배포합니다. 회사에서 Windows 10을 실행하는 모든 PC에 이 애플리케이션을 설치해야 합니다. 이 과정에서 애플리케이션을 효과적으로 관리하기 위해 수행할 수 있는 많은 작업을 살펴보겠습니다.  

 이 절차는 Configuration Manager 애플리케이션을 만들어 배포하는 방법을 간략하게 설명하기 위한 것입니다. 그러나 모든 구성 옵션이나 다른 플랫폼용 애플리케이션을 만들어 배포하는 방법은 설명하지 않습니다.  

 각 플랫폼과 관련된 자세한 내용은 다음 항목 중 하나를 참조하세요.  

- [Windows 애플리케이션 만들기](/configmgr/apps/get-started/creating-windows-applications)
- [Windows Phone 애플리케이션 만들기](/configmgr/mdm/deploy-use/management-tasks-applications#bkmk_winphone)
- [Mac 컴퓨터 애플리케이션 만들기](/configmgr/apps/get-started/creating-mac-computer-applications)
- [Linux 및 UNIX 서버 애플리케이션 만들기](/configmgr/apps/get-started/creating-linux-and-unix-server-applications)
- [Windows Embedded 애플리케이션 만들기](/configmgr/apps/get-started/creating-windows-embedded-applications)


Configuration Manager 애플리케이션에 이미 익숙한 경우에는 이 항목을 건너뛰어도 됩니다. 그러나 [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 검토하여 애플리케이션을 만들어 배포할 때 사용할 수 있는 모든 옵션을 알아보는 것이 좋습니다.  

## <a name="before-you-start"></a>시작하기 전에  

[애플리케이션 관리 소개](/sccm/apps/understand/introduction-to-application-management)의 내용을 검토하여 애플리케이션을 설치할 수 있도록 사이트를 준비했으며 이 항목에서 사용되는 용어를 알고 있는지 확인합니다.  

 또한 **Contoso.msi** 앱의 설치 파일이 액세스 가능한 네트워크 위치에 있는지 확인합니다.  

## <a name="create-the-configuration-manager-application"></a>Configuration Manager 애플리케이션 만들기  

### <a name="to-start-the-create-application-wizard-and-create-the-application"></a>애플리케이션 만들기 마법사를 시작하고 애플리케이션을 만들려면  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **애플리케이션 관리** > **애플리케이션**을 선택합니다.  

2. **홈** 탭의 **만들기** 그룹에서 **애플리케이션 만들기**를 선택합니다.  

3. **애플리케이션 만들기 마법사**의 **일반** 페이지에서 **설치 파일에서 이 애플리케이션에 대한 정보 자동 검색**을 선택합니다. 이렇게 하면 마법사의 일부 정보가 설치 .msi 파일에서 추출된 정보로 미리 채워집니다. 그런 후에 다음 정보를 지정합니다.  

   - **형식**: **Windows Installer(\*.msi 파일)** 를 선택합니다.  

   - **위치**: 설치 파일**Contoso.msi**의 위치를 입력하거나 **찾아보기**를 선택하여 위치를 선택합니다. Configuration Manager에서 설치 파일을 찾을 수 있도록 하려면 위치를 *\\\Server\Share\File* 형식으로 지정해야 합니다.  

   그러면 다음 스크린샷과 같은 화면이 표시됩니다.  

   ![앱 관리 마법사 일반 페이지](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  

4. **다음**을 선택합니다. **정보 가져오기** 페이지에 Configuration Manager로 가져온 앱 및 관련된 모든 파일에 대한 일부 정보가 표시됩니다. 완료되면 다시 **다음**을 선택합니다.  

5. **일반 정보** 페이지에서 애플리케이션에 대한 추가 정보를 제공하면 Configuration Manager 콘솔에서 정렬하고 찾는 데 도움이 됩니다.  

    또한 **설치 프로그램** 필드를 통해 PC에 애플리케이션을 설치하는 데 사용할 전체 명령줄을 지정할 수 있습니다. 이 필드를 편집하여 사용자 고유의 속성을 추가할 수 있습니다(예: 무인 설치의 경우 **/q**).  

   > [!TIP]  
   > 마법사의 이 페이지에 있는 일부 필드는 애플리케이션 설치 파일을 가져올 때 자동으로 채워졌을 수 있습니다.  

    그러면 다음 스크린샷과 같은 화면이 표시됩니다.  

    ![앱 관리 마법사 일반 정보 페이지](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  

6. **다음**을 선택합니다. 요약 페이지에서 애플리케이션 설정을 확인한 후 마법사를 완료할 수 있습니다.  

   앱을 만드는 작업을 완료했습니다. 앱을 찾으려면 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 확장하고 **애플리케이션**을 선택합니다. 이 예제에서는 다음과 같이 표시됩니다.  

   ![최종 앱 그래픽](/sccm/apps/get-started/media/Final-app-graphic.png)  

## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>애플리케이션 및 배포 유형의 속성 검사  

이제 애플리케이션을 만들었으므로 필요한 경우 애플리케이션 설정을 구체화할 수 있습니다. 애플리케이션 속성을 확인하려면 앱을 선택한 다음 **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

 **&lt;Contoso\> 애플리케이션 속성** 대화 상자에는 애플리케이션의 동작을 구체화하기 위해 구성할 수 있는 많은 항목이 표시됩니다. 구성할 수 있는 모든 설정에 대한 자세한 내용은 [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요. 이 예제의 목적을 위해 애플리케이션 배포 유형의 일부 속성을 변경하겠습니다.  

 **배포 유형** 탭 &gt; **Contoso 애플리케이션** 배포 유형 &gt; **편집**을 선택합니다.

다음과 같은 대화 상자가 표시됩니다.  

![앱 관리 앱 속성 페이지](/sccm/apps/get-started/media/App-management-app-properties-page.png)  

## <a name="add-a-requirement-to-the-deployment-type"></a>배포 유형에 요구 사항 추가

 요구 사항은 디바이스에 애플리케이션을 설치하기 전에 충족해야 하는 조건을 지정합니다.  기본 제공 요구 사항에서 선택하거나 요구 사항을 직접 만들 수 있습니다. 이 예제에서는 Windows 10을 실행하는 PC에만 애플리케이션을 설치해야 하는 요구 사항을 추가합니다.  

1. 방금 열린 배포 유형 속성 페이지에서 **요구 사항** 탭을 선택합니다.  

2. **추가**를 선택하여 **요구 사항 만들기** 대화 상자를 엽니다.  

3. **요구 사항 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    - **범주**: **디바이스**  

    - **조건**: **운영 체제**  

    - **규칙 유형**: **값**  

    - **연산자**: **중 하나**  

    - 운영 체제 목록에서 **Windows 10**을 선택합니다.  

    다음과 같은 대화 상자가 표시됩니다.  

    ![앱 관리 요구 사항 페이지](/sccm/apps/get-started/media/App-management-requirements-page.png)  

4. **확인**을 선택하여 열려 있는 각 속성 페이지를 닫습니다. 그런 후에 Configuration Manager 콘솔의 **애플리케이션** 목록으로 돌아옵니다.  

> [!TIP]  
> 요구 사항을 통해 필요한 Configuration Manager 컬렉션 수를 줄일 수 있습니다. Windows 10을 실행하는 PC에만 애플리케이션을 설치할 수 있도록 지정했으므로 나중에 다른 여러 운영 체제를 실행하는 PC가 포함된 컬렉션에 이 요구 사항을 배포할 수 있습니다. 애플리케이션은 Windows 10 PC에만 설치됩니다.

## <a name="add-the-application-content-to-a-distribution-point"></a>배포 지점에 애플리케이션 콘텐츠 추가  

다음으로는 애플리케이션을 PC에 배포하기 위해 애플리케이션 콘텐츠를 배포 지점에 복사해야 합니다. PC는 애플리케이션을 설치하는 배포 지점에 액세스합니다.  

> [!TIP]  
> Configuration Manager의 배포 지점 및 콘텐츠 관리에 대해 자세히 알아보려면 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 선택합니다.  

2. **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션**을 선택합니다. 그런 다음 앞서 만든 **Contoso 애플리케이션**을 애플리케이션 목록에서 선택합니다.  

3. **홈** 탭의 **배포** 그룹에서 **콘텐츠 배포**를 선택합니다.  

4. **콘텐츠 배포 마법사**의 **일반** 페이지에서 애플리케이션 이름이 올바른지 확인하고 **다음**을 선택합니다.  

5. **콘텐츠** 페이지에서 배포 지점에 복사할 정보를 검토하고 **다음**을 선택합니다.  

6. **콘텐츠 대상** 페이지에서 **추가**를 선택하여 애플리케이션 콘텐츠를 설치할 하나 이상의 배포 지점 또는 배포 지점 그룹을 선택합니다.  

7. 마법사를 완료합니다.  

**모니터링** 작업 영역의 **배포 상태** > **콘텐츠 상태**에서 애플리케이션 콘텐츠가 배포 지점에 복사되었는지를 확인할 수 있습니다.  

## <a name="deploy-the-application"></a>애플리케이션 배포  

이제, 계층 구조의 디바이스 컬렉션에 애플리케이션을 배포합니다. 이 예제에서는 **모든 시스템** 디바이스 컬렉션에 애플리케이션을 배포합니다.  

> [!TIP]  
> 이전에 선택한 요구 사항 때문에 Windows 10 컴퓨터에서만 애플리케이션을 설치합니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **애플리케이션 관리** > **애플리케이션**을 선택합니다.  

2. 앞서 만든 애플리케이션인 **Contoso 애플리케이션**을 애플리케이션 목록에서 선택한 다음 **홈** 탭의 **배포** 그룹에서 **배포**를 선택합니다.  

3. **소프트웨어 배포 마법사**의 **일반** 페이지에서 **찾아보기**를 선택하여 **모든 시스템** 디바이스 컬렉션을 선택합니다.  

4. **콘텐츠** 페이지에서 애플리케이션을 설치할 PC의 배포 지점이 선택되었는지 확인합니다.  

5. **배포 설정** 페이지에서 배포 작업이 **설치**로 설정되어 있고 해당 응용 프로그램이 **필수** 배포용으로 설정되어 있는지 확인합니다.  

    > [!TIP]  
    > **필수** 배포용으로 설정하는 애플리케이션은 설정된 요구 사항을 충족하는 PC에 설치됩니다. 이 값을 **사용 가능**으로 설정하면 사용자가 필요 시 소프트웨어 센터에서 애플리케이션을 설치할 수 있습니다.

6. **일정** 페이지에서 애플리케이션이 설치되는 시기를 구성할 수 있습니다. 이 예에서는 **사용 가능해지면 되도록 빨리**를 선택합니다.  

7. **사용자 환경** 페이지에서 **다음**을 선택하여 기본값을 적용합니다.  

8. 마법사를 완료합니다.  

아래의 **애플리케이션 모니터링** 섹션의 내용을 참조하여 애플리케이션 배포의 상태를 확인합니다.  

## <a name="monitor-the-application"></a>애플리케이션 모니터링

 이 섹션에서는 방금 배포된 애플리케이션의 배포 상태를 빠르게 확인합니다.  

### <a name="to-review-the-deployment-status"></a>배포 상태를 검토하려면  

1. Configuration Manager 콘솔에서 **모니터링** > **배포**를 선택합니다.  

2. 배포의 목록에서 **Contoso 애플리케이션**을 선택합니다.  

3. **홈** 탭의 **배포** 그룹에서 **상태 보기**를 선택합니다.  

4. 다음 탭 중 하나를 선택하여 애플리케이션 배포에 대한 추가 상태 업데이트를 확인합니다.  

    - **성공**: 표시된 PC에 애플리케이션을 성공적으로 설치했습니다.  

    - **진행 중**: 애플리케이션 설치가 아직 완료되지 않았습니다.  

    - **오류**: 표시된 PC에 애플리케이션을 설치하는 동안 오류가 발생했습니다. 오류에 대한 자세한 내용도 표시됩니다.  

    - **요구 사항에 맞지 않음**: 표시된 디바이스가 구성된 요구 사항에 맞지 않아서(이 예제에서는 Windows 10에서 실행되지 않아서) 해당 디바이스에 대해 설치가 시도되지 않았습니다.  

    - **알 수 없음**: Configuration Manager에서 배포 상태를 보고할 수 없습니다. 나중에 다시 확인하세요.  

> [!TIP]  
> 몇 가지 방법으로 애플리케이션 배포를 모니터링할 수 있습니다. 자세한 내용은 [애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)을 참조하세요.

## <a name="end-user-experience"></a>최종 사용자 환경  

Configuration Manager를 통해 관리되며 Windows 10을 실행하는 PC의 사용자에게는 Contoso 애플리케이션을 설치해야 한다는 메시지가 표시됩니다. 사용자가 설치에 동의하면 애플리케이션이 설치됩니다.  

Configuration Manger 1906 버전부터 **새 소프트웨어를 사용할 수 있습니다** 알림은 특정 애플리케이션과 수정 버전의 사용자에게 한 번만 표시됩니다. 이후에는 사용자가 로그인할 때 알림이 표시되지 않습니다. 애플리케이션이 변경되거나 다시 배포된 경우 애플리케이션에 대한 다른 알림만 표시됩니다.

## <a name="next-steps"></a>다음 단계

[애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)
