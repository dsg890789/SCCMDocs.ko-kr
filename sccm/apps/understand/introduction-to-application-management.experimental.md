---
title: "응용 프로그램 관리 소개 | System Center Configuration Manager"
description: "System Center Configuration Manager 응용 프로그램을 관리 및 배포하는 데 필요한 기본 정보를 검색합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: 18
author: robstackmsft
ms.author: robstack
manager: angrobe
experimental: true
experiment_id: rob-table-161101
translationtype: Human Translation
ms.sourcegitcommit: aa985dcb947803f7bc6d770f80a89a2fe6750681
ms.openlocfilehash: bec4d6d7008d5eabc7219dc7aaa1198c6e68a4df


---
# <a name="introduction-to-application-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 응용 프로그램 관리 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 System Center Configuration Manager 응용 프로그램에서 작업을 시작하기 전에 알아두어야 할 기본 사항을 설명합니다.  

> [!TIP]  
>  Configuration Manager에서 응용 프로그램을 관리하는 방법을 잘 알고 있는 경우 이 항목을 건너뛰고 바로 샘플 응용 프로그램을 만들어도 됩니다. [System Center Configuration Manager를 사용하여 응용 프로그램 만들기 및 배포](../../apps/get-started/create-and-deploy-an-application.md)를 참조하세요.  

## <a name="what-is-an-application"></a>응용 프로그램이란?  
 '응용 프로그램'은 널리 사용되는 컴퓨팅 용어지만 Configuration Manager에서는 다른 의미로 사용됩니다. 응용 프로그램을 상자처럼 간주하세요. 이 상자에는 소프트웨어 패키지에 대한 하나 이상의 설치 파일 집합( **배포 유형**이라고 함)과 소프트웨어 배포 방법 지침이 들어 있습니다.  

 장치에 응용 프로그램을 배포할 때 **요구 사항** 에 따라 장치에 설치되는 배포 유형이 결정됩니다.  

 물론, 응용 프로그램으로 수행할 수 있는 작업은 훨씬 더 많으며 이 가이드를 통해 알아보겠습니다. 다음 목록에서는 자세히 살펴보기 전에 알아야 할 몇 가지 개념을 소개합니다. 만든 모든 응용 프로그램에 이러한 개념이 모두 필요하지는 않습니다.  



- **요구 사항** 이전 버전의 Configuration Manager에서는 응용 프로그램을 배포하려는 장치가 포함된 컬렉션을 만드는 경우가 많았습니다. 이 작업도 가능하지만 응용 프로그램이 설치되는 조건을 훨씬 더 세부적으로 지정하면 필요한 요구 사항이 줄어듭니다.<br> 예를 들어 Windows 10을 실행하는 장치에만 응용 프로그램을 설치할 수 있도록 지정할 수 있습니다. 그런 다음 모든 장치에 응용 프로그램을 배포할 수 있지만 Windows 10을 실행하는 장치에만 설치됩니다.<br> Configuration Manager는 요구 사항을 평가하여 응용 프로그램과 해당 배포 유형을 설치할 것인지 여부를 결정합니다. 그런 다음 응용 프로그램을 설치할 올바른 배포 유형을 결정합니다. 기본적으로 요구 사항 규칙은 클라이언트 설정 **배포의 재평가 일정**에 따라 7일마다 재평가되어 호환성이 유지됩니다.<br> 자세한 내용은 [응용 프로그램 만들기 및 배포](../../apps/get-started/create-and-deploy-an-application.md)를 참조하세요. 


- **글로벌 조건** 요구 사항은 단일 응용 프로그램에서 특정 배포 유형과 함께 사용되지만 모든 응용 프로그램과 배포 유형에 사용할 수 있는 미리 정의된 요구 사항 라이브러리인 글로벌 조건을 만들 수도 있습니다.<br> Configuration Manager에는 기본 제공 글로벌 조건 집합이 포함되어 있으며, 직접 만들 수도 있습니다.<br> 자세한 내용은 [글로벌 조건 만들기](../../apps/deploy-use/create-global-conditions.md)를 참조하세요.


- **시뮬레이트된 배포** 응용 프로그램에 대한 요구 사항, 검색 방법 및 종속성을 평가한 다음 실제로 응용 프로그램을 설치하지 않고 결과를 보고합니다.<br> 자세한 내용은 [응용 프로그램 배포 시뮬레이션](../../apps/deploy-use/simulate-application-deployments.md)을 참조하세요. 


- **배포 작업** 배포하는 응용 프로그램을 설치할지 아니면 제거할지를(지원되는 경우) 지정합니다.<br> 자세한 내용은 [응용 프로그램 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.  


- **배포용** 배포 앱이 **필수**인지 아니면 **사용 가능**인지를 지정합니다.<br>
**필수** - 구성된 일정에 따라 자동으로 응용 프로그램이 배포됩니다. 그러나 응용 프로그램 배포 상태가 숨겨져 있지 않으면 사용자가 이 상태를 추적할 수 있으며 소프트웨어 센터를 사용하여 최종 기한 전에 응용 프로그램을 설치할 수 있습니다.<br> **사용 가능** - 응용 프로그램이 사용자에 배포된 경우 사용자는 소프트웨어 센터에 게시된 응용 프로그램을 확인하고 필요한 경우 요청할 수 있습니다.<br> 자세한 내용은 [응용 프로그램 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.


- **수정 버전** 응용 프로그램 또는 응용 프로그램에 포함된 배포 유형을 수정하면 Configuration Manager에서 응용 프로그램의 새 수정 버전을 만듭니다. 각 응용 프로그램 수정 버전의 기록을 표시하거나, 속성을 확인하거나, 이전 응용 프로그램 수정 버전을 복원하거나, 이전 수정 버전을 삭제할 수 있습니다.<br> 자세한 내용은 [응용 프로그램 업데이트 및 사용 중지](../../apps/deploy-use/update-and-retire-applications.md)를 참조하세요.


- **검색 방법** 검색 방법은 배포된 응용 프로그램이 이미 설치되었는지를 검색하는 데 사용됩니다. 검색 방법에서 응용 프로그램이 설치되었다고 표시하면 Configuration Manager에서 다시 설치하려고 시도하지 않습니다.<br> 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요. 


- **종속성** 종속성은 다른 배포 유형이 설치되기 전에 먼저 설치해야 할 하나 이상의 배포 유형(다른 응용 프로그램의 배포 유형)을 정의합니다. 배포 유형이 설치되기 전에 종속 배포 유형을 자동으로 설치하도록 구성할 수 있습니다.<br> 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.  


- **대체** Configuration Manager에서 대체 관계를 사용하여 기존 응용 프로그램을 업그레이드하거나 대체할 수 있습니다. 응용 프로그램을 교체할 때 교체된 응용 프로그램의 배포 유형을 대체할 새 배포 유형을 지정하고 교체할 응용 프로그램을 설치하기 전에 교체된 응용 프로그램을 업그레이드할지 아니면 제거할지를 구성할 수도 있습니다.<br> 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.


- **사용자 중심 관리** Configuration Manager 응용 프로그램은 사용자 중심 관리를 지원하므로 특정 사용자를 특정 장치와 연결할 수 있습니다. 사용자 장치의 이름을 기억할 필요 없이 사용자와 장치에 앱을 배포할 수 있습니다. 이러한 기능을 통해 가장 중요한 앱을 특정 사용자가 액세스하는 각 장치에서 항상 사용 가능하도록 유지할 수 있습니다. 사용자가 새 컴퓨터를 구입하는 경우 관리자는 사용자가 로그온하기 전에 해당 장치에 사용자 앱을 자동으로 설치할 수 있습니다.<br> 자세한 내용은 [사용자 장치 선호도를 사용하여 사용자와 장치 연결](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)을 참조하세요.  

## <a name="what-application-types-can-you-deploy"></a>배포할 수 있는 응용 프로그램 유형  
 Configuration Manager에서는 다음과 같은 앱 유형을 배포할 수 있습니다.  

- Windows Installer(*.msi 파일)
- Windows 앱 패키지(*.appx, \*.appxbundle)
- Windows 앱 패키지(Windows 스토어)
- Microsoft Application Virtualization 4
- Microsoft Application Virtualization 5
- Windows Mobile 캐비닛
- Mac OS X  


또한 Microsoft Intune 또는 Configuration Manager 온-프레미스 장치 관리를 통해 장치를 관리하는 경우 다음과 같은 앱 유형을 추가로 관리할 수 있습니다.

- Windows Phone 앱 패키지(*.xap 파일)
- iOS용 앱 패키지(*.ipa 파일)
- Android용 앱 패키지(*.apk 파일)
- Google Play의 Android용 앱 패키지
- Windows Phone 앱 패키지(Windows Phone 스토어)
- MDM을 사용하는 Windows Installer
- 웹 응용 프로그램



## <a name="state-based-applications"></a>상태 기반 응용 프로그램  
 Configuration Manager 응용 프로그램에서는 상태 기반 모니터링을 사용합니다. 이 방식을 통해 사용자 및 장치에 대한 마지막 응용 프로그램 배포 상태를 추적할 수 있습니다. 상태 메시지는 개별 장치에 대한 정보를 표시합니다. 예를 들어 응용 프로그램이 사용자 컬렉션에 배포된 경우 Configuration Manager 콘솔에서 배포의 준수 상태 및 배포 용도를 확인할 수 있습니다. Configuration Manager 콘솔의 **모니터링** 작업 영역을 사용하여 모든 소프트웨어 배포를 모니터링할 수 있습니다. 소프트웨어 배포에는 소프트웨어 업데이트, 호환성 설정, 응용 프로그램, 작업 순서, 패키지 및 프로그램 등이 포함됩니다. 자세한 내용은 [응용 프로그램 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)을 참조하세요.  

 응용 프로그램 배포는 Configuration Manager에서 정기적으로 다시 평가됩니다. 예를 들면 다음과 같습니다.  

-   최종 사용자가 배포된 응용 프로그램을 제거합니다. 그다음 평가 주기에서 응용 프로그램이 없는 것이 검색되면 Configuration Manager에서 다시 설치합니다.  

-   요구 사항을 충족하지 못해 응용 프로그램이 장치에 설치되지 않았습니다. 나중에 장치가 변경되어 이제는 요구 사항이 충족됩니다. Configuration Manager에서 이 변경 내용을 검색하며, 응용 프로그램이 설치됩니다.  

 **배포의 재평가 일정** 클라이언트 설정을 사용하여 응용 프로그램 배포에 대한 재평가 간격을 구성할 수 있습니다. 자세한 내용은 [클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)를 참조하세요.  

## <a name="get-started-creating-an-application"></a>응용 프로그램을 만들기 시작  
 바로 응용 프로그램을 만들기 시작하려는 경우 [응용 프로그램 만들기 및 배포](../../apps/get-started/create-and-deploy-an-application.md) 항목에 간단한 응용 프로그램을 만드는 연습이 있습니다.  

 기본 사항을 알고 있으며 사용 가능한 모든 옵션에 대한 자세한 참조 정보를 찾고 있는 경우 [응용 프로그램 만들기](/sccm/apps/deploy-use/create-applications)에서 시작합니다.  

## <a name="software-center-and-the-application-catalog"></a>소프트웨어 센터 및 응용 프로그램 카탈로그  
 이전 버전의 Configuration Manager에서는 소프트웨어 센터를 사용하여 소프트웨어를 설치 및 예약하고, 원격 제어 설정을 구성하고, 전원 관리 설정을 구성했습니다. 사용자는 검색할 응용 프로그램 카탈로그에 연결하고, 소프트웨어를 요청하고, 일부 기본 설정을 구성하며, 모바일 장치를 원격으로 초기화할 수 있었습니다.  

 System Center Configuration Manager에서 이러한 설정을 계속 사용할 수 있지만, 이제 새로운 버전의 소프트웨어 센터에서는 Silverlight 사용 웹 브라우저가 필요한 응용 프로그램 카탈로그를 사용하지 않고도 응용 프로그램을 검색할 수 있습니다. 그러나 사용자가 사용할 수 있는 앱이 소프트웨어 센터에 표시되려면 응용 프로그램 카탈로그 웹 사이트 지점 및 응용 프로그램 카탈로그 웹 서비스 지점 사이트 시스템 역할이 여전히 필요합니다.  

 자세한 내용은 [응용 프로그램 관리 계획 및 구성](../../apps/plan-design/plan-for-and-configure-application-management.md)을 참조하세요.  

## <a name="using-configuration-manager-packages-and-programs"></a>Configuration Manager 패키지 및 프로그램 사용  
 Configuration Manager에서는 이전 버전의 제품에서 사용된 패키지와 프로그램을 계속 지원합니다. 다음 스크립트를 배포하는 경우 패키지 및 프로그램을 사용하여 배포하는 것이 응용 프로그램을 사용하여 배포하는 것보다 적합할 수 있습니다.  

-   컴퓨터에 응용 프로그램을 설치하지 않는 스크립트(예: 컴퓨터 디스크 드라이브를 조각 모음하는 스크립트)  

-   지속적으로 모니터링하지 않아도 되는 "일회용" 스크립트  

-   되풀이 일정에서 실행되고 전역 평가를 사용할 수 없는 스크립트  

 자세한 내용은 [패키지 및 프로그램](../../apps/deploy-use/packages-and-programs.md)을 참조하세요.  




<!--HONumber=Dec16_HO3-->


