---
title: 사전 캐시 콘텐츠 구성
titleSuffix: Configuration Manager
description: 사용자가 작업 순서를 설치 하기 전에 클라이언트에서 OS 배포 콘텐츠를 다운로드 하는 방법을 알아봅니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 9d1e8252-99e3-48aa-bfa5-0cf4cd6637b2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ba7380d35742f01c620d95bfb9351180d56f7df
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537721"
---
# <a name="configure-pre-cache-content-for-task-sequences"></a>작업 순서에 대해 사전 캐시 콘텐츠 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1021244-->
작업 순서의 사용 가능한 배포에 대해 사전 캐시 기능을 사용하면 사용자가 작업 순서를 설치하기 전에 클라이언트에서 관련 콘텐츠를 다운로드할 수 있습니다. 클라이언트는 [os를 업그레이드](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system) 하거나 [os 이미지를 설치](/sccm/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system)하는 작업 순서에 대 한 콘텐츠를 미리 캐시할 수 있습니다.

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  

예를 들어 모든 사용자를 위한 단일 내부 업그레이드 작업 순서만 원하거나 많은 아키텍처 및 언어를 포함할 수 있습니다. 이전 버전에서 사용자가 소프트웨어 센터에서 사용 가능한 작업 순서 배포를 설치할 때 콘텐츠가 다운로드를 시작합니다. 이 지연 때문에 설치를 시작할 준비가 되기 전에 추가 시간이 필요합니다. 또한 작업 순서에서 참조되는 모든 콘텐츠가 다운로드됩니다. 이 콘텐츠에는 모든 언어 및 아키텍처에 대한 OS 업그레이드 패키지가 포함됩니다. 각 업그레이드 패키지의 크기가 약 3GB이면 전체 콘텐츠는 더 큽니다.

사전 캐시 콘텐츠를 사용하면 클라이언트가 배포를 받는 즉시 해당 콘텐츠뿐 아니라 관련된 다른 모든 콘텐츠를 다운로드할 수 있습니다. 사용자가 소프트웨어 센터에서 **설치**를 클릭하면 콘텐츠가 준비됩니다. 콘텐츠가 로컬 하드 드라이브에 있으므로 설치가 신속하게 시작합니다.

Configuration Manager 버전 1902 및 이전 버전에서이 동작은 *OS 업그레이드 패키지*에만 적용 됩니다. 해당 패키지는 일치하는 아키텍처 또는 언어를 지정하는 유일한 콘텐츠입니다. 예를 들어 작업 순서가 여러 드라이버 패키지를 참조하는 경우 클라이언트는 모든 패키지를 다운로드합니다. 작업 순서 엔진은 미리 하지 않고 작업 순서가 실행될 때 단계에 대한 조건을 평가합니다. 클라이언트는 패키지 속성에서 태그를 사용하여 사전 캐시되는 내용을 결정합니다.

버전 1906부터,<!--4224642--> 미리 캐싱을 사용 하 여 다음과 같은 콘텐츠 형식의 대역폭 사용량을 줄일 수 있습니다.

- OS 업그레이드 패키지
- OS 이미지
- 드라이버 패키지
- 패키지


## <a name="configure-pre-caching"></a>사전 캐싱 구성

사전 캐시 기능을 구성 하는 세 가지 단계가 있습니다.

1. [패키지 만들기 및 구성](#bkmk_createpkg)
2. [조건부 단계를 사용 하 여 작업 순서 만들기](#bkmk_createts)
3. [작업 순서를 배포 하 고 미리 캐싱을 사용 하도록 설정](#bkmk_deploy)


### <a name="bkmk_createpkg"></a>-1 패키지 만들기 및 구성

클라이언트는 패키지의 특성을 평가 하 여 사전 캐싱을 수행 하는 동안 다운로드 하는 콘텐츠를 결정 합니다.  

#### <a name="os-upgrade-package"></a>OS 업그레이드 패키지

특정 아키텍처 및 언어에 대한 [OS 업그레이드 패키지](/sccm/osd/get-started/manage-operating-system-upgrade-packages)를 만듭니다. 그 속성의 **데이터 원본** 탭에서 **아키텍처** 및 **언어**를 지정합니다.

#### <a name="os-image"></a>OS 이미지

특정 아키텍처 및 언어에 대한 [OS 이미지](/sccm/osd/get-started/manage-operating-system-images)를 만듭니다. 그 속성의 **데이터 원본** 탭에서 **아키텍처** 및 **언어**를 지정합니다.

#### <a name="driver-package"></a>드라이버 패키지

특정 하드웨어 모델용 [드라이버 패키지](/sccm/osd/get-started/manage-drivers#BKMK_ManagingDriverPackages)를 만듭니다. 속성의 **일반** 탭에서 **모델** 을 지정 합니다.

사전 캐시하는 동안 다운로드할 드라이버 패키지를 결정하기 위해 클라이언트는 모델의 **Win32_ComputerSystemProduct** WMI 속성을 평가합니다.  

#### <a name="package"></a>패키지

특정 아키텍처 및 언어에 대한 [패키지](/sccm/apps/deploy-use/packages-and-programs)를 만듭니다. 속성의 **일반** 탭에서 **아키텍처** 및 **언어** 를 지정 합니다.


### <a name="bkmk_createts"></a> 2. 작업 순서 만들기

다양 한 언어 및 아키텍처에 대 한 조건부 단계 또는 드라이버 패키지에 대 한 다른 하드웨어 모델을 포함 하는 작업 순서를 만듭니다.

|Content|단계|
|---------|---------|
|OS 업그레이드 패키지|[OS 업그레이드](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS)|
|OS 이미지|[OS 이미지 적용](/sccm/osd/understand/task-sequence-steps#BKMK_ApplyOperatingSystemImage)|
|드라이버 패키지|[드라이버 패키지 적용](/sccm/osd/understand/task-sequence-steps#BKMK_ApplyDriverPackage)|
|패키지|[패키지 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallPackage)|

예를 들어 다음 **OS 업그레이드** 단계는 영어 버전을 사용합니다.  

![ENU, DEU 및 JPN에 대한 여러 OS 업그레이드 단계를 보여 주는 작업 순서 편집기](../media/precacheproperties2.png)

![로캘 및 OSArchitecture에 대한 WMI WQL 쿼리를 표시하는 작업 순서 편집기, 옵션 탭](../media/precacheoptions2.png)  

> [!Tip]
> 다음 WMI 쿼리는 영어 (미국) OS 및 64 비트 아키텍처에 권장 됩니다.
>
> ```WMI
> SELECT * FROM Win32_OperatingSystem WHERE OSArchitecture LIKE '%64%' AND OSLanguage=1033`
> ```
>
> 먼저 **운영 체제 언어** 조건을 선택 하 여 언어를 추가 합니다. 그런 다음, WMI 쿼리를 편집 하 여 architecture 절을 포함 합니다.


### <a name="bkmk_deploy"></a> 3. 작업 순서 배포

[작업 순서를 배포합니다](/sccm/osd/deploy-use/deploy-a-task-sequence). 사전 캐시 기능에 대해 다음 설정을 구성합니다.  

- **일반** 탭에서 **이 작업 순서에 대한 콘텐츠 사전 다운로드**를 선택합니다.  

- **배포 설정** 탭에서 해당 작업 순서를 **사용 가능**으로 구성합니다.  

- **예약** 탭의 **이 배포를 사용할 수 있는 시점 예약** 설정에서 현재 선택된 시간을 선택합니다. 클라이언트는 배포의 사용 가능한 시간에 콘텐츠를 사전 캐시하기 시작합니다. 대상 클라이언트가 이 정책의 수신할 때 사용할 수 있는 시간은 과거입니다. 따라서 미리 캐시 다운로드를 즉시 시작합니다. 클라이언트에서 이 정책을 수신하지만 사용할 수 있는 시간이 나중이면 클라이언트가 사용할 수 있는 시간이 발생할 때까지 콘텐츠를 사전 캐시하기 시작하지 않습니다.  

- **배포 지점** 탭에서 **배포 옵션** 설정을 구성합니다. 사용자가 설치를 시작하기 전에 콘텐츠가 사전 캐시되지 않은 경우 클라이언트에서 이러한 설정을 사용합니다.  

    > [!Important]  
    > OS 이미지를 설치 하는 작업 순서에서는 **실행 중인 작업 순서에 따라 필요한 경우**배포 옵션을 사용 하 여 콘텐츠를 로컬로 다운로드 하지 마세요. OS 이미지를 적용 하기 전에 작업 순서에서 디스크를 초기화 하면 클라이언트 캐시가 제거 됩니다. 콘텐츠가 사라진 후에는 작업 순서가 실패 합니다.<!-- SCCMDocs-PR #1338 -->


## <a name="user-experience"></a>사용자 환경

- 클라이언트가 배포 정책을 받으면 배포를 사용할 수 있는 시간 이후에 콘텐츠의 사전 캐시를 시작합니다. 이 콘텐츠는 참조되는 모든 패키지를 포함하지만, 패키지의 아키텍처 및 언어 특성과 일치하는 OS 업그레이드 패키지여야 합니다.  

- 클라이언트에서 배포가 사용자에게 제공되면 사용자에게 새로운 배포를 알리는 알림이 표시됩니다. 이제 작업 순서가 소프트웨어 센터에 표시됩니다. 사용자가 소프트웨어 센터로 이동한 다음 **설치**를 클릭하여 설치를 시작합니다.  

- 사용자가 작업 순서를 설치할 때 클라이언트가 콘텐츠를 완전하게 사전 캐시하지 않은 경우 클라이언트는 배포의 **배포 옵션** 탭에서 지정한 설정을 사용합니다.  


## <a name="see-also"></a>참고 항목

- [OS를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)
- [최신 버전으로 Windows 업그레이드하는 시나리오](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)
