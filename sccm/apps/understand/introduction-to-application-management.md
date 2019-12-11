---
title: 앱 관리 소개
titleSuffix: Configuration Manager
description: Configuration Manager의 애플리케이션을 관리 및 배포하는 데 필요한 기본 정보를 검색합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee7527492851a89b013c6f59464c06e73c72b247
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74661331"
---
# <a name="introduction-to-application-management-in-configuration-manager"></a>Configuration Manager의 애플리케이션 관리 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 Configuration Manager 애플리케이션 작업을 시작하기 전에 기본 사항을 알아봅니다.  

> [!TIP]  
> Configuration Manager로 애플리케이션을 관리하는 방법에 이미 익숙한 경우에는 이 문서를 건너뛰어도 됩니다. [애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)의 샘플 애플리케이션 만들기로 이동하세요.  

## <a name="what-is-an-application"></a>애플리케이션이란?

*애플리케이션* 또는 *앱*은 널리 사용되는 컴퓨팅 용어지만 Configuration Manager에서는 특정한 것을 의미합니다. 애플리케이션을 상자처럼 간주하세요. 이 상자에는 소프트웨어 패키지에 대한 하나 이상의 설치 파일 집합(*배포 유형*이라고 함)과 소프트웨어 배포 방법 지침이 들어 있습니다.  

디바이스에 애플리케이션을 배포할 때 **요구 사항**에 따라 Configuration Manager가 디바이스에 설치하는 배포 유형이 결정됩니다.  

애플리케이션으로 더 많은 작업을 수행할 수 있습니다. 이 가이드를 읽으면 이러한 기능에 대해 자세히 알아볼 수 있습니다. 다음 섹션에서는 더 깊이 파고들기 전에 알아야 할 몇 가지 개념을 소개합니다.  

### <a name="deployment-type"></a>배포 유형

*애플리케이션*이 상자라면 *배포 유형*은 상자에 있는 콘텐츠의 집합입니다. 애플리케이션에는 적어도 하나의 배포 유형이 필요합니다. 이에 따라 앱을 설치하는 방법이 결정되기 때문입니다. 둘 이상의 배포 유형을 사용하여 동일한 애플리케이션에 대해 서로 다른 콘텐츠와 설치 프로그램을 구성할 수 있습니다.

예를 들어, 회사에 Astoria라는 LOB(기간 업무) 애플리케이션이 있습니다. 애플리케이션 개발자는 다음과 같이 앱을 설치하는 방법을 제공합니다.

- Windows 10 디바이스의 전체 기능을 위한 Windows Installer 패키지
- 터미널 서버 팜에서 사용하기 위한 App-V 패키지
- 모바일 사용자를 위한 Android 앱 패키지  

Configuration Manager에서 Astoria용 단일 애플리케이션을 만듭니다. 이 애플리케이션은 모든 설치 방법과 플랫폼에 공통되는 앱에 대한 상위 수준의 메타데이터를 정의합니다. 그런 다음, 사용 가능한 설치 방법에 대한 세 가지 배포 유형을 만들고 모든 사용자에게 애플리케이션을 배포합니다. 배포 유형에 대한 요구 사항 및 기타 구성을 기반으로 Configuration Manager는 각 사용 사례에 맞는 방법을 결정합니다.

자세한 내용은 [애플리케이션의 배포 유형 만들기](/sccm/apps/deploy-use/create-applications#bkmk_create-dt)를 참조하세요.

### <a name="requirements"></a>요구 사항

이전 버전의 Configuration Manager에서는 애플리케이션을 배포할 디바이스 컬렉션을 만들었습니다. 컬렉션을 여전히 만들 수 있지만 *요구 사항*을 사용하여 애플리케이션 배포에 대해 보다 자세한 조건을 지정할 수 있습니다.

예를 들어 Windows 10을 실행하는 디바이스에만 애플리케이션을 설치하도록 지정할 수 있습니다. 모든 디바이스에 애플리케이션을 배포하면 Windows 10을 실행하는 디바이스에만 설치됩니다.

Configuration Manager는 요구 사항을 평가하여 애플리케이션과 해당 배포 유형을 설치할지 여부를 결정합니다. 그런 다음 애플리케이션을 설치할 올바른 배포 유형을 결정합니다. 기본적으로 7일마다 Configuration Manager 클라이언트는 요구 사항 규칙을 재평가하여 클라이언트 설정 **배포의 재평가 일정**에 따라 규정 준수 여부 결정합니다.

자세한 내용은 [애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application) 및 [배포 유형 요구 사항](/sccm/apps/deploy-use/create-applications#bkmk_dt-require)을 참조하세요.

### <a name="global-conditions"></a>글로벌 조건

요구 사항은 단일 애플리케이션의 특정 배포 유형에 사용되지만 *글로벌 조건*을 만들 수도 있습니다. 이 조건은 모든 애플리케이션 및 배포 유형에 사용할 수 있는 미리 정의된 요구 사항의 라이브러리입니다. Configuration Manager에는 기본 제공 글로벌 조건 집합이 포함되어 있으며, 직접 만들 수도 있습니다.

자세한 내용은 [글로벌 조건 만들기](/sccm/apps/deploy-use/create-global-conditions)를 참조하세요.

### <a name="simulated-deployment"></a>시뮬레이트된 배포

*시뮬레이트된 배포*는 요구 사항, 검색 방법 및 애플리케이션에 대한 종속성을 평가합니다. 클라이언트는 애플리케이션을 실제로 설치하지 않고 결과만 보고합니다.

자세한 내용은 [애플리케이션 배포 시뮬레이트](/sccm/apps/deploy-use/simulate-application-deployments)를 참조하세요.  

### <a name="deployment-action"></a>배포 작업

*배포 작업*은 배포할 애플리케이션의 설치 또는 제거 여부를 지정합니다. 일부 배포 유형은 제거 작업을 지원하지 않습니다.

자세한 내용은 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.  

### <a name="deployment-purpose"></a>배포 목적

*배포용*은 배포 앱이 **필수**인지 아니면 **사용 가능**인지를 지정합니다.  

- 클라이언트는 사용자가 설정한 일정에 따라 필수 배포를 자동으로 설치합니다.  애플리케이션이 숨겨져 있지 않으면 사용자가 배포 상태를 추적할 수 있습니다. 소프트웨어 센터를 사용하여 최종 기한 전에 애플리케이션을 설치할 수도 있습니다.  

- 애플리케이션을 사용 가능으로 사용자에게 배포하면 소프트웨어 센터에서 애플리케이션을 볼 수 있고 필요할 때 요청할 수 있습니다.   

자세한 내용은 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.  

### <a name="revisions"></a>수정 버전

애플리케이션 또는 배포 유형의 수정 버전을 만들면 Configuration Manager가 새 버전의 애플리케이션을 만듭니다.  Configuration Manager 콘솔에서 다음 작업 중 하나를 선택합니다.

- 각 애플리케이션 수정 버전의 기록 표시
- 속성 보기
- 애플리케이션의 이전 버전 복원
- 이전 버전 삭제

자세한 내용은 [애플리케이션 업데이트 및 사용 중지](/sccm/apps/deploy-use/update-and-retire-applications)를 참조하세요.  

### <a name="detection-method"></a>검색 방법

검색 방법을 사용하여 디바이스에 애플리케이션이 이미 설치되었는지 여부를 확인할 수 있습니다.  검색 방법에 애플리케이션이 설치되어 있다고 표시되면 Configuration Manager에서 설치를 다시 시도하지 않습니다.

자세한 내용은 [배포 유형 검색 방법 옵션](/sccm/apps/deploy-use/create-applications##bkmk_dt-detect)을 참조하세요.

### <a name="dependencies"></a>종속성

종속성은 클라이언트가 이 배포 유형을 설치하기 전에 먼저 설치해야 하는 다른 애플리케이션에서 하나 이상의 배포 유형을 정의합니다. 

자세한 내용은 [배포 유형 종속성](/sccm/apps/deploy-use/create-applications#bkmk_dt-depend)을 참조하세요.  

### <a name="supersedence"></a>교체

Configuration Manager에서 대체 관계를 사용하여 기존 애플리케이션을 업그레이드하거나 대체할 수 있습니다.  애플리케이션을 대체할 때는 새 배포 유형을 지정하여 대체된 애플리케이션의 배포 유형을 바꿉니다. 또한 클라이언트가 교체 애플리케이션을 설치하기 전에 교체된 애플리케이션을 업그레이드할지 아니면 제거할지를 결정할 수도 있습니다.

자세한 내용은 [애플리케이션 대체](/sccm/apps/deploy-use/revise-and-supersede-applications#application-supersedence)를 참조하세요.  

### <a name="user-centric-management"></a>사용자 중심 관리

Configuration Manager 애플리케이션은 사용자 중심 관리를 지원하므로 특정 사용자를 특정 디바이스와 연결할 수 있습니다.  사용자의 디바이스 이름을 기억할 필요 없이 사용자와 디바이스에 앱을 배포할 수 있습니다. 이러한 기능을 통해 가장 중요한 앱을 각 사용자의 디바이스에서 항상 사용할 수 있도록 유지할 수 있습니다. 사용자가 새 컴퓨터를 구입하면 Configuration Manager는 로그인하기 전에 디바이스에 자동으로 사용자의 앱을 설치합니다.

자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.  

### <a name="application-group"></a>애플리케이션 그룹

1906 버전부터는 사용자 또는 디바이스 컬렉션을 단일 배포로 보낼 수 있는 애플리케이션 그룹을 만듭니다. 앱 그룹에 대해 지정한 메타데이터는 소프트웨서 센터에 단일 항목으로 표시됩니다. 클라이언트가 특정 순서대로 앱을 설치하도록 그룹에서 순서를 지정할 수 있습니다.

자세한 내용은 [애플리케이션 그룹 만들기](/sccm/apps/deploy-use/create-app-groups)를 참조하세요.

## <a name="what-application-types-can-you-deploy"></a>배포할 수 있는 애플리케이션 유형

Configuration Manager에서는 다음과 같은 앱 유형을 배포할 수 있습니다.  

- Windows Installer(msi)  

- Windows 앱 패키지(appx 또는 appxbundle)  

    > [!Note]  
    > 이 유형에는 새로운 Windows 10 앱 패키지(msix) 및 앱 번들(msixbundle) 형식이 포함됩니다.<!--1357427-->  

- Microsoft Store의 Windows 앱 패키지  

- Microsoft App-V v4 및 v5  

- macOS  

또한 Microsoft Intune 또는 Configuration Manager 온-프레미스 디바이스 관리를 통해 디바이스를 관리하는 경우 다음과 같은 앱 유형을 추가로 관리합니다.  

- Windows Phone 앱 패키지(xap)  

- Microsoft Store의 Windows Phone 앱 패키지  

- iOS용 앱 패키지(ipa)  

- Apple 앱 스토어의 iOS용 앱 패키지  

- Android용 앱 패키지(apk)  

- Google Play의 Android용 앱 패키지  

- MDM을 통한 Windows Installer(msi)  

- 웹 애플리케이션

## <a name="state-based-applications"></a>상태 기반 애플리케이션  

Configuration Manager 애플리케이션은 상태 기반 모니터링을 사용합니다. 사용자 및 디바이스의 마지막 애플리케이션 배포 상태를 추적할 수 있습니다. 상태 메시지는 개별 디바이스에 대한 정보를 표시합니다. 예를 들어 애플리케이션을 사용자 컬렉션에 배포하는 경우 Configuration Manager 콘솔에서 배포의 준수 상태 및 배포 용도를 볼 수 있습니다. Configuration Manager 콘솔의 **모니터링** 작업 영역에서 모든 소프트웨어 배포를 모니터링합니다. 자세한 내용은 [애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)을 참조하세요.  

Configuration Manager 클라이언트는 애플리케이션 배포를 정기적으로 다시 평가합니다. 예:  

- 배포된 애플리케이션을 사용자가 제거합니다. 다음 평가 주기에서 Configuration Manager가 앱이 없는 것을 감지합니다. 그러면 클라이언트가 앱을 자동으로 다시 설치합니다.  

- Configuration Manager가 요구 사항을 충족하지 못하는 디바이스에 애플리케이션을 설치하지 않았습니다. 나중에 디바이스가 변경되어 이제는 요구 사항이 충족됩니다. Configuration Manager가 변화를 감지하고, 클라이언트가 애플리케이션을 설치합니다.  

애플리케이션 배포에 대한 재평가 간격을 설정할 수 있습니다. **소프트웨어 배포** 그룹의 **배포의 재평가 일정** 클라이언트 설정을 사용합니다. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#software-deployment)를 참조하세요.  

## <a name="get-started-creating-an-application"></a>애플리케이션을 만들기 시작  

바로 애플리케이션을 만들기 시작하려는 경우에는 [애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application) 문서에서 연습을 찾을 수 있습니다.  

기본 사항에 익숙하고 사용 가능한 모든 옵션에 대한 자세한 참조 정보가 필요하면 [애플리케이션 만들기](/sccm/apps/deploy-use/create-applications)부터 시작하세요.  

## <a name="software-center"></a>소프트웨어 센터  

소프트웨어 센터는 Configuration Manager 클라이언트와 함께 설치되는 Windows 애플리케이션입니다. 이것을 사용하여 다음 작업을 수행할 수 있습니다.  

- 디바이스 또는 사용자에게 배포된 애플리케이션을 찾아보고 요청합니다.
- 소프트웨어 설치 프로그램 설치 및 예약
- 애플리케이션, 소프트웨어 업데이트 및 운영 체제의 설치 상태 보기
- 원격 제어 설정 구성
- 전원 관리 설정

자세한 내용은 다음 아티클을 참조하세요.  

- [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)
- [소프트웨어 센터 계획](/sccm/apps/plan-design/plan-for-software-center)
- [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)

> [!Note]  
> 버전 1910을 사용 하는 응용 프로그램 카탈로그 역할에 대 한 지원이 종료 됩니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

## <a name="packages-and-programs"></a>패키지 및 프로그램  

Configuration Manager에서는 이전 버전의 제품에서 사용된 패키지와 프로그램을 계속 지원합니다.

자세한 내용은 [패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs)을 참조하세요.  

## <a name="next-steps"></a>다음 단계

Configuration Manager에서 애플리케이션을 관리하는 기본 개념을 이해했으면 다음 문서를 계속 진행하세요.

- [예제 애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)
- [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)
- [애플리케이션 만들기](/sccm/apps/deploy-use/create-applications)
