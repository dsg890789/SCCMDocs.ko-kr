---
title: "새 버전 1610 | Microsoft 문서"
description: "System Center Configuration Manager 버전 1610에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다."
ms.custom: na
ms.date: 11/23/2016
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7eb0803-3f8f-4ab6-825a-99ac11f5ba7d
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Human Translation
ms.sourcegitcommit: db673277d1cc2d24e8dba2439b2b1891c883ebd0
ms.openlocfilehash: 8b80f4d14eafa4cbbfb083178a118bc0e71f4019
ms.contentlocale: ko-kr
ms.lasthandoff: 06/16/2017

---
# <a name="what39s-new-in-version-1610-of-system-center-configuration-manager"></a>System Center Configuration Manager 버전 1610의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 현재 분기의 업데이트 1610은 버전 1511, 1602 또는 1606을 실행하는 이전에 설치된 사이트에 대한 콘솔 내 업데이트로 제공됩니다.


> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용해야 합니다.  
>  다음에 대해 자세히 알아보세요.    
>  -   [새 사이트 설치](https://technet.microsoft.com/library/mt590197.aspx)  
>  -   [사이트에 업데이트 설치](https://technet.microsoft.com/library/mt607046.aspx)  
>  -   [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

다음 섹션에서는 Configuration Manager 버전 1610에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.  


## <a name="in-console-monitoring-of-update-installation-status"></a>콘솔 내 업데이트 설치 상태 모니터링  
버전 1610부터 콘솔에서 업데이트 팩을 설치하고 설치를 모니터링할 때 **사후 설치**라는 새 단계가 있습니다. 이 단계에는 주요 서비스 다시 시작, 복제 모니터링 초기화 등의 작업 상태가 포함됩니다. 이 단계는 버전 1610으로 사이트 업데이트를 수행해야 콘솔에서 사용할 수 있습니다. 업데이트 설치 상태에 대한 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)를 참조하세요.


## <a name="exclude-clients-from-automatic-upgrade"></a>자동 업그레이드에서 클라이언트 제외
새 버전의 클라이언트 소프트웨어로 업그레이드되지 않도록 Windows 클라이언트를 제외할 수 있습니다. 이렇게 하려면 업그레이드에서 제외하도록 지정된 컬렉션에 클라이언트 컴퓨터를 포함합니다. 제외된 컬렉션의 클라이언트는 클라이언트 소프트웨어 업데이트 요청을 무시합니다.  자세한 내용은 [업그레이드에서 Windows 클라이언트 제외](../../clients/manage/upgrade/exclude-clients-windows.md)를 참조하세요.


## <a name="improvements-for-boundary-groups"></a>경계 그룹의 향상된 기능
버전 1610에서는 경계 그룹에 대한 중요 변경 사항 및 배포 지점과 함께 작동하는 방식을 소개합니다. 이러한 변경 사항을 통해 콘텐츠 인프라 디자인이 간편해졌을 뿐 아니라 클라이언트가 콘텐츠 원본 위치로 추가 배포 지점을 검색하기 위해 대체하는 방법과 시기를 제어할 수 있습니다. 여기에는 온-프레미스와 클라우드 기반 배포 지점이 모두 포함됩니다.
이러한 향상된 기능은 이미 익숙할 수도 있는 개념과 동작(예: 배포 지점을 빠르거나 느리게 구성)을 대체합니다. 새 모델은 설정하고 유지 관리하기가 더 쉽습니다. 이러한 변경 내용은 또한 경계 그룹에 연결할 다른 사이트 시스템 역할을 향상시키는 추가 변경 사항의 기반이 됩니다.

버전 1610으로 업데이트하는 경우 업데이트는 이러한 변경 내용이 기존 콘텐츠 배포 구성을 방해하지 않도록 새 모델에 맞게 현재 경계 그룹 구성을 변환합니다.

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-groups)을 참조하세요.


## <a name="peer-cache-for-content-distribution-to-clients"></a>클라이언트에 콘텐츠 배포를 위한 피어 캐시
버전 1610부터 클라이언트 **피어 캐시**는 원격 위치의 클라이언트에 대한 콘텐츠 배포를 관리하는 데 도움이 됩니다. 피어 캐시는 클라이언트가 로컬 캐시의 콘텐츠를 다른 클라이언트와 직접 공유하도록 기본 제공되는 Configuration Manager 솔루션입니다.

피어 캐시를 사용하도록 설정된 클라이언트 설정을 컬렉션에 배포하고 나면 해당 컬렉션의 멤버가 동일 경계 그룹에서 다른 클라이언트의 피어 콘텐츠 원본 역할을 할 수 있습니다.

새 **클라이언트 데이터 원본** 대시보드를 사용하여 사용자 환경의 피어 캐시 콘텐츠 원본 사용을 파악할 수도 있습니다.

> [!TIP]  
> 버전 1610의 경우 피어 캐시 및 클라이언트 데이터 원본 대시보드는 시험판 기능입니다. 이러한 기능을 사용하도록 설정하려면 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease)을 참조하세요.

자세한 내용은 [Configuration Manager 클라이언트에 대한 피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache) 및 [클라이언트 데이터 원본 대시보드](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)를 참조하세요.


## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>동시에 여러 공유 배포 지점 마이그레이션
이제 **배포 지점 다시 할당** 옵션을 사용하여 Configuration Manager 프로세스에서 동시에 최대 50개의 공유 배포 지점을 병렬로 다시 할당하도록 할 수 있습니다. 이 릴리스 이전에는 다시 할당된 배포 지점이 한 번에 하나씩 처리되었습니다. 자세한 내용은 [동시에 여러 공유 배포 지점 마이그레이션](/sccm/core/migration/planning-a-content-deployment-migration-strategy#migrate-multiple-shared-distribution-points-at-the-same-time)을 참조하세요.

## <a name="cloud-management-gateway-for-managing-internet-based-clients"></a>인터넷 기반 클라이언트 관리를 위한 클라우드 관리 게이트웨이

클라우드 관리 게이트웨이는 인터넷에서 Configuration Manager 클라이언트를 관리할 수 있는 간단한 방법을 제공합니다. Microsoft Azure에 배포되고 Azure 구독이 필요한 클라우드 관리 게이트웨이 서비스는 클라우드 관리 게이트웨이 연결점이라는 새 역할을 사용하여 온-프레미스 Configuration Manager 인프라에 연결합니다. 완전히 배포되고 구성된 클라이언트는 내부 개인 네트워크 또는 인터넷에 연결되었는지 여부에 관계없이 온-프레미스 Configuration Manager 사이트 시스템 역할 및 클라우드 기반 배포 지점과 통신할 수 있습니다. 자세한 내용 및 클라우드 관리 게이트웨이와 인터넷 기반 클라이언트 관리의 차이점을 보려면 [인터넷에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients-internet)를 참조하세요.

## <a name="improvements-to-the-windows-10-edition-upgrade-policy"></a>Windows 10 버전 업그레이드 정책의 향상 기능
이번 릴리스에서는 이 정책 유형이 다음과 같이 향상되었습니다.

- 이제 Microsoft Intune에 등록된 Windows 10 PC 외에도 Configuration Manager를 실행하는 Windows 10 PC에서 버전 업그레이드 정책을 사용할 수 있습니다.
- Windows 10 Professional에서 마법사에 있는 하드웨어와 호환되는 아무 플랫폼으로나 업그레이드할 수 있습니다.

## <a name="manage-hardware-identifiers"></a>하드웨어 식별자 관리
이제 Configuration Manager에서 PXE 부팅 및 클라이언트 등록을 위해 무시하는 하드웨어 ID 목록을 제공할 수 있습니다. 이 목록은 두 가지 일반적인 문제 해결에 도움이 됩니다.

1. Surface Pro 3과 같이 온보드 이더넷 포트가 포함되어 있지 않은 장치가 많습니다. USB-이더넷 어댑터는 일반적으로 운영 체제 배포를 위해 유선 연결을 설정하는 데 사용됩니다. 그러나 비용 및 일반적인 유용성 때문에 공유 어댑터인 경우가 많습니다. 이 어댑터의 MAC 주소는 장치를 식별하는 데 사용되기 때문에 각 배포 간에 추가 관리자 작업 없이 어댑터를 다시 사용하면 문제가 발생합니다. 이제 Configuration Manager 버전 1610에서는 이 시나리오에서 쉽게 다시 사용할 수 있도록 어댑터의 MAC 주소를 제외할 수 있습니다.
2. SMBIOS ID는 고유 하드웨어 식별자여야 하지만 일부 특수 하드웨어 장치는 중복된 ID로 빌드됩니다. 이 문제는 방금 설명한 USB-이더넷 어댑터 시나리오만큼 흔하지는 않지만, 제외된 하드웨어 ID 목록을 사용하여 해결할 수 있습니다.

자세한 내용은 [중복된 하드웨어 식별자 관리](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers)를 참조하세요.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Configuration Manager와 비즈니스용 Windows 스토어 통합 향상
이 릴리스의 변경 내용:
- 이전에는 비즈니스용 Windows 스토어에서 무료 앱만 배포할 수 있었습니다. 이제 Configuration Manager에서 사용이 허가된 유료 온라인 앱 배포를 추가로 지원합니다(Intune에 등록된 장치에 한함).
- 이제 비즈니스용 Windows 스토어와 Configuration Manager 간의 즉시 동기화를 시작할 수 있습니다.
- 이제 Azure Active Directory에서 얻은 클라이언트 비밀 키를 수정할 수 있습니다.
- 저장소에 대한 구독을 삭제할 수 있습니다.

자세한 내용은 [System Center Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)를 참조하세요.


## <a name="policy-sync-for-intune-enrolled-devices"></a>Intune에 등록된 장치에 대한 정책 동기화
이제 장치 자체의 회사 포털 앱에서 동기화를 요청할 필요 없이 Configuration Manager 콘솔에서 Intune 등록 장치에 대한 정책 동기화를 요청할 수 있습니다. 동기화 요청 상태 정보는 장치 뷰에서 **원격 동기화 상태**라는 새 열로 제공됩니다. 각 장치의 **속성** 대화 상자에 있는 검색 데이터 섹션에서도 정보를 확인할 수 있습니다.
자세한 내용은 [Configuration Manager 콘솔에서 원격으로 Intune에 등록된 장치의 정책 동기화](/sccm/mdm/deploy-use/sync-intune-device)를 참조하세요.


## <a name="use-compliance-settings-to-configure-windows-defender-settings"></a>준수 설정을 사용하여 Windows Defender 설정 구성
이제 Configuration Manager 콘솔에서 구성 항목을 사용하여 Intune에 등록된 Windows 10 컴퓨터에 대한 Windows Defender 클라이언트 설정을 구성할 수 있습니다.
자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Windows 8.1 및 Windows 10 장치에 대한 구성 항목을 만드는 방법](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)에서 **Windows Defender** 섹션을 참조하세요.



## <a name="general-improvements-to-software-center"></a>소프트웨어 센터에 대한 일반적인 개선 사항
- 이제 사용자가 응용 프로그램 카탈로그와 소프트웨어 센터에서 앱을 요청할 수 있습니다.
- 사용자가 새로운 관련 소프트웨어를 이해하는 데 도움이 되는 개선 사항입니다.

## <a name="new-columns-in-device-collection-views"></a>장치 컬렉션 뷰의 새 열
이제 장치 컬렉션 뷰에서 **IMEI** 및 **일련 번호**(iOS 장치)의 열을 표시할 수 있습니다.
자세한 내용은 [IMEI 또는 iOS 일련 번호로 장치 미리 선언](https://docs.microsoft.com/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)을 참조하세요.

## <a name="customizable-branding-for-software-center-dialogs"></a>소프트웨어 센터 대화 상자에 대한 사용자 지정 가능한 브랜딩
소프트웨어 센터에 대한 사용자 지정 브랜딩은 Configuration Manager 버전 1602에서 도입되었습니다. 버전 1610에서는 해당 브랜딩이 이제 모든 관련 대화 상자로 확장되어 소프트웨어 센터 사용자에게 보다 일관된 환경을 제공합니다.

소프트웨어 센터에 대한 사용자 지정 브랜딩은 다음 규칙에 따라 적용됩니다.

- 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되지 않은 경우 소프트웨어 센터에서 **컴퓨터 에이전트** 클라이언트 설정의 **소프트웨어 센터에 표시되는 조직 이름**에 지정된 조직 이름을 표시합니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](../../clients/deploy/configure-client-settings.md)을 참조하세요.

- 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되어 있는 경우 소프트웨어 센터에서 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할 속성에 지정된 조직 이름 및 색을 표시합니다. 자세한 내용은 [응용 프로그램 카탈로그 웹 사이트 지점에 대한 옵션 구성](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#Application-Catalog-website-point)을 참조하세요.

- Microsoft Intune 구독을 구성하고 Configuration Manager 환경에 연결한 경우 소프트웨어 센터에서 Intune 구독 속성에 지정된 조직 이름, 색 및 회사 로고를 표시합니다. 자세한 내용은 [Configuring the Microsoft Intune subscription](/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription)을 참조하십시오.


## <a name="enforcement-grace-period-for-required-application-and-software-update-deployments"></a>필수 응용 프로그램 및 소프트웨어 업데이트 배포를 위한 유예 기간 적용
간혹 설정한 기한 이후에도 필수 응용 프로그램 배포 또는 소프트웨어 업데이트를 설치할 수 있는 시간을 사용자에게 더 제공하려는 경우가 있습니다. 예를 들어 컴퓨터가 오랫동안 꺼져 있었거나 많은 응용 프로그램 또는 업데이트 배포를 설치해야 할 때 이런 조치가 필요할 수 있습니다. 예를 들어 최종 사용자가 휴가에서 막 돌아온 경우 지연된 응용 프로그램 배포를 설치하는 데 너무 오래 기다려야 할 수 있습니다. 이 문제를 해결하기 위해 이제 컬렉션에 Configuration Manager 클라이언트 설정을 배포하여 유예 기간 적용을 정의할 수 있습니다. 

유예 기간을 구성하려면 다음 작업을 수행합니다.
1.      클라이언트 설정의 **컴퓨터 에이전트** 페이지에서 새 속성, **배포 최종 기한 이후 적용 유예 기간(시간)**을 **1**시간에서 **120**시간 사이의 값으로 구성합니다.
2.      새 필수 응용 프로그램 배포 또는 기존 배포 속성의 **일정** 페이지에서 클라이언트 설정에 정의된 유예 기간까지 **이 배포의 적용을 사용자 기본 설정에 따라 연기** 확인란을 선택합니다. 이 확인란이 선택되고 클라이언트 설정도 배포된 대상 장치의 모든 배포에서 유예 기간 적용을 사용합니다.

유예 기간 적용을 구성하고 확인란을 선택하면 응용 프로그램 설치 마감일에 도달한 후 사용자가 해당 유예 기간에 구성한 첫 번째 업무 외 시간에서 응용 프로그램이 설치됩니다. 하지만 여전히 사용자가 소프트웨어 센터를 열고 언제든지 원하는 응용 프로그램을 설치할 수 있습니다. 유예 기간이 만료되면 지연 배포에 대한 일반적인 동작이 적용됩니다. 소프트웨어 업데이트 배포 마법사, 자동 배포 규칙 마법사 및 속성 페이지에 비슷한 옵션이 추가되었습니다.



## <a name="improved-functionality-in-dialog-boxes-about-required-software"></a>필수 소프트웨어와 관련된 대화 상자의 향상된 기능
사용자가 필수 소프트웨어를 받으면 **다음 시간 후 다시 알림** 설정에서 다음 드롭다운 값 목록을 선택할 수 있습니다. 
- **나중에**. 클라이언트 에이전트 설정에 구성된 알림 설정에 따라 알림을 예약합니다.
- **고정 시간**. 선택한 시간 후에 다시 표시하도록 알림을 예약합니다(예: 30분 후).

![클라이언트 에이전트 설정의 컴퓨터 에이전트 페이지](media/client-notification-settings.png)

최대 다시 알림 시간은 클라이언트 에이전트 설정에서 구성된 알림 값을 기반으로 합니다. 예를 들어 컴퓨터 에이전트 페이지의 **배포 최종 기한이 24시간 미만 남은 경우 사용자에게 다음 시간마다 미리 알림(시)** 설정이 10시간으로 구성되고 최종 기한까지 24시간이 넘게 남은 경우, 사용자에게 최대 10시간까지의 다시 알림 옵션들이 표시됩니다. 최종 기한이 가까워지면 배포 타임라인의 각 구성 요소와 관련된 클라이언트 에이전트 설정에 따라 사용 가능한 옵션이 줄어듭니다.

또한 운영 체제를 배포하는 작업 순서 등 고위험성 배포의 경우 사용자 알림 환경의 침투성이 더 높아졌습니다. 사용자에게 중요 소프트웨어 유지 관리 알림을 표시해야 할 때마다 임시 작업 표시줄 알림 대신 다음과 같은 대화 상자가 사용자 컴퓨터에 표시됩니다.

![필수 소프트웨어 대화 상자](media/client-toast-notification.png)


자세한 내용을 보려면 다음을 수행하십시오.
- [높은 위험 수준의 배포를 관리하는 설정](../../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [클라이언트 설정을 구성하는 방법](../../clients/deploy/configure-client-settings.md)

## <a name="software-updates-dashboard"></a>소프트웨어 업데이트 대시보드
새 소프트웨어 업데이트 대시보드를 사용하여 조직 내 장치의 현재 준수 상태를 보고 데이터를 빠르게 분석하여 위험한 장치를 확인합니다. 대시보드를 보려면 **모니터링** > **개요** > **보안** > **소프트웨어 업데이트 대시보드**로 이동합니다.

자세한 내용은 [소프트웨어 업데이트 모니터링](/sccm/sum/deploy-use/monitor-software-updates)을 참조하세요.


## <a name="improvements-to-the-application-request-process"></a>응용 프로그램 요청 프로세스에 대한 개선 사항
응용 프로그램 설치를 승인한 후 Configuration Manager 콘솔에서 **거부**를 클릭하여 요청을 거부하도록 선택할 수 있습니다. 이전에는 승인 후에 이 단추가 회색으로 표시되었습니다.

이 작업을 수행해도 장치에서 응용 프로그램이 제거되지는 않습니다. 그러나 사용자가 소프트웨어 센터에서 응용 프로그램의 새 복사본을 설치할 수 없습니다.

## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>자동 배포 규칙의 콘텐츠 크기에 따라 필터링
이제 자동 배포 규칙에서 소프트웨어 업데이트의 콘텐츠 크기를 기준으로 필터링할 수 있습니다. 예를 들어 2MB보다 작은 크기의 소프트웨어 업데이트만 다운로드하려면 **콘텐츠 크기(KB)** 필터를 **< 2048**로 설정할 수 있습니다. 이 필터를 사용하면 큰 소프트웨어 업데이트가 자동으로 다운로드되는 것이 방지되므로 네트워크 대역폭이 제한된 경우 단순화된 Windows 하위 수준 서비스를 보다 잘 지원할 수 있습니다. 자세한 내용은 다음을 참조하세요.
- [Configuration Manager and Simplified Windows Servicing on Down Level Operating Systems](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)(Configuration Manager 및 하위 수준 운영 체제의 단순화된 Windows 서비스).
- [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)

**콘텐츠 크기(KB)** 필드를 구성하려면 다음 중 하나를 수행합니다.
- 자동 배포 규칙 만들기 마법사에서 자동 배포 규칙을 만들 때 **소프트웨어 업데이트** 페이지로 이동합니다.
- 기존 자동 배포 규칙의 속성에서 **소프트웨어 업데이트** 탭으로 이동합니다.

## <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드
이제 Configuration Manager 콘솔에서 Office 365 클라이언트 관리 대시보드를 사용할 수 있습니다. 대시보드를 보려면 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.

대시보드는 다음에 대한 차트를 표시합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널     

자세한 내용은 [Office 365 ProPlus 업데이트 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates)를 참조하세요.

## <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>BIOS-UEFI 변환을 관리하는 작업 순서 단계
이제 새로운 변수인 TSUEFIDrive를 사용하여 운영 체제 배포 작업 순서를 사용자 지정하여 UEFI로 전환하기 위해 **컴퓨터 다시 시작** 단계에서 하드 드라이브의 FAT32 파티션을 준비하도록 할 수 있습니다. 다음 절차는 BIOS-UEFI 변환을 위해 하드 드라이브를 준비하기 위한 작업 순서 단계를 만드는 방법의 예를 제공합니다. 자세한 내용은 [BIOS-UEFI 변환을 관리하는 작업 순서 단계](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)를 참조하세요.

##  <a name="improvements-to-the-task-sequence-step-prepare-configmgr-client-for-capture"></a>작업 순서 단계 향상: ConfigMgr 클라이언트 캡처 준비  
이제 ConfigMgr 클라이언트 준비 단계에서 주요 정보만 제거하는 것이 아니라 Configuration Manager 클라이언트를 완전히 제거합니다. 작업 순서에서 운영 체제 캡처 이미지를 배포할 때마다 새 Configuration Manager 클라이언트를 설치합니다. 자세한 내용은 [작업 순서 단계](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)를 참조하세요.



## <a name="intune-compliance-policy-charts"></a>Intune 준수 정책 차트
이제 Configuration Manager 콘솔의 **모니터링** 작업 영역 아래에 있는 새 차트를 사용하여 장치의 전체 준수 및 주요 비준수 이유에 대한 간략한 보기를 볼 수 있습니다. 차트에서 섹션을 클릭하여 해당 범주의 장치 목록으로 드릴다운할 수 있습니다. 자세한 내용은 [준수 정책 모니터링](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)을 참조하세요.


## <a name="lookout-integration-for-hybrid-implementations-to-protect-ios-and-android-devices"></a>하이브리드 구현에서 iOS 및 Android 장치를 보호하기 위한 Lookout 통합
Microsoft는 맬웨어, 위험한 앱 등을 장치에서 검색하여 iOS 및 Android 모바일 장치를 보호하기 위해 Lookout 모바일 위협 방지 솔루션과 통합합니다. Lookout 솔루션은 구성할 수 있는 위협 수준을 확인하는 데 도움이 됩니다. System Center Configuration Manager에서 준수 정책 규칙을 만들어 Lookout의 위험 평가에 따라 장치 준수를 확인할 수 있습니다. 조건부 액세스 정책을 사용하여 장치 준수 상태에 따라 회사 리소스에 대한 액세스를 차단할 수 있습니다. 통합 및 작동 방식에 대해 알아보려면 [장치, 네트워크 및 응용 프로그램 위험에 따라 액세스 관리](/sccm/protect/deploy-use/manage-access-based-on-device-network-app-risk)를 참조하세요.

호환되지 않는 iOS 장치 사용자에게는 등록하라는 내용의 메시지가 표시됩니다. 그러면 장치에 Lookout for Work 앱을 설치하고, 앱을 활성화하고, Lookout for Work 응용 프로그램에서 보고된 위협을 수정한 후에 회사 데이터에 액세스할 수 있습니다. [Lookout for Work 앱 구성 및 배포](/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps) 방법을 알아봅니다.



## <a name="new-compliance-settings-for-configuration-items"></a>구성 항목의 새 준수 설정
다양한 장치 플랫폼의 구성 항목에 사용할 수 있는 여러 가지 새로운 설정이 있습니다. 이러한 설정은 이전에 Microsoft Intune의 독립 실행형 구성에 있던 설정이며 이제 Intune과 Configuration Manager를 사용할 때 제공됩니다.
자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 장치에 대한 구성 항목](/sccm/compliance/deploy-use/configuration-items-for-devices-managed-without-the-client)을 참조하세요.

### <a name="new-settings-for-android-devices"></a>Android 장치에 대한 새로운 설정
#### <a name="password-settings"></a>암호 설정
- **암호 기록 기억**
- **지문 잠금 해제 허용**

#### <a name="security-settings"></a>보안 설정
- **메모리 카드 암호화 필요**
- **화면 캡처 허용**
- **진단 데이터 제출 허용**

#### <a name="browser-settings"></a>브라우저 설정
- **웹 브라우저 허용**
- **자동 채우기 허용**
- **팝업 차단 허용**
- **쿠키 허용**
- **액티브 스크립팅 허용**

#### <a name="app-settings"></a>앱 설정
- **Google Play 스토어 사용 가능**

#### <a name="device-capability-settings"></a>장치 기능 설정
- **이동식 저장소 허용**
- **Wi-Fi 테더링 허용**
- **지리적 위치 허용**
- **NFC 허용**
- **Bluetooth 허용**
- **음성 로밍 허용**
- **데이터 로밍 허용**
- **SMS/MMS 메시지 허용**
- **음성 지원 허용**
- **음성 전화 걸기 허용**
- **복사 및 붙여넣기 허용**

### <a name="new-settings-for-ios-devices"></a>iOS 장치에 대한 새 설정
#### <a name="password-settings"></a>암호 설정
- **암호에 필요한 복합 문자 수**
- **단순 암호 허용**
- **암호를 요구하기 전까지 비활성 시간(분)**
- **암호 기록 기억**

### <a name="new-settings-for-mac-os-x-devices"></a>Mac OS X 장치에 대한 새 설정
#### <a name="password-settings"></a>암호 설정
- **암호에 필요한 복합 문자 수**
- **단순 암호 허용**
- **암호 기록 기억**
- **화면 보호기가 활성화되기까지의 비활성 시간(분)**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Windows 10 Desktop 및 모바일 장치에 대한 새로운 설정
#### <a name="password-settings"></a>암호 설정
- **최소 문자 집합 수**
- **암호 기록 기억**
- **장치가 유휴 상태에서 되돌아오는 경우 암호 필요**

#### <a name="security-settings"></a>보안 설정
- **모바일 장치 암호화 필요**
- **수동 등록 취소 허용**

#### <a name="device-capability-settings"></a>장치 기능 설정
- **셀룰러에서 VPN 허용**
- **셀룰러에서 VPN 로밍 허용**
- **휴대폰 초기화 허용**
- **USB 연결 허용**
- **Cortana 허용**
- **알림 센터 알림 허용**

### <a name="new-settings-for-windows-10-team-devices"></a>Windows 10 Team 장치에 대한 새 설정
#### <a name="device-settings"></a>장치 설정
- **Azure Operational Insights 사용**
- **Miracast 무선 프로젝션 사용**
- **시작 화면에 표시되는 모임 정보 선택**
- **잠금 화면 배경 이미지 URL**

### <a name="new-settings-for-windows-81-devices"></a>Windows 8.1 장치의 새로운 설정
#### <a name="applicability-settings"></a>적용 가능성 설정
- **Windows 10에 모든 구성 적용**

#### <a name="password-settings"></a>암호 설정
- **필수 암호 유형**
- **최소 문자 집합 수**
- **최소 암호 길이**
- **장치를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수**
- **화면이 잠기기 전까지 비활성 시간(분)**
- **암호 만료(일)**
- **암호 기록 기억**
- **이전 암호 다시 사용 방지**
- **사진 암호 및 PIN 허용**

#### <a name="browser-settings"></a>브라우저 설정
- **인트라넷 네트워크의 자동 검색 허용**

### <a name="new-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 장치에 대한 새로운 설정
#### <a name="applicability-settings"></a>적용 가능성 설정
- **Windows 10에 모든 구성 적용**

#### <a name="password-settings"></a>암호 설정
- **최소 문자 집합 수**
- **단순 암호 허용**
- **암호 기록 기억**

#### <a name="device-capability-settings"></a>장치 기능 설정
- **무료 Wi-Fi 핫스팟에 자동 연결 허용**

