---
title: 버전 1902의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager 현재 분기, 버전 1902에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.
ms.date: 05/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4812324b-e6aa-4431-bf1d-9fcd763a8caa
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c88cdc52442463bb3788c80c45d6c074dd900f5
ms.sourcegitcommit: 53f2380ac67025fb4a69fc1651edad15d98e0cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65673419"
---
# <a name="whats-new-in-version-1902-of-configuration-manager-current-branch"></a>Configuration Manager 현재 분기, 버전 1902의 새 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 현재 분기, 버전 1902 업데이트는 콘솔 내 업데이트로 사용할 수 있습니다. 1802, 1806, 또는 1810 버전을 실행하는 사이트에서 이 업데이트를 적용합니다. <!-- baseline only statement:-->새 사이트를 설치할 때 기준 버전으로 사용할 수도 있습니다. 이 문서에는 Configuration Manager 버전 1902의 변경 내용과 새로운 기능이 요약되어 있습니다.  

이 업데이트를 설치하기 위한 최신 검사 목록을 항상 검토하세요. 자세한 내용은 [업데이트 1902를 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1902)을 참조하세요. 사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1902#post-update-checklist)도 검토하세요.

새 Configuration Manager 기능을 모두 활용하려면 사용자를 업데이트한 후 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.

> [!Note]  
> 이 문서는 현재 이 버전의 모든 중요한 기능을 나열합니다. 그러나 일부 섹션은 새 기능에 대한 추가 정보가 있는 업데이트된 콘텐츠에 아직 연결되지 않았습니다. 이 페이지에서 정기적으로 업데이트를 확인하세요. 변경 내용은 ***[업데이트]*** 태그로 표시됩니다. 이 표시는 콘텐츠가 최종 버전이 되면 제거될 것입니다.  

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22what%27s+new+in+version+1902+-+Configuration+Manager%22&locale=en-us`



## <a name="bkmk_deprecated"></a> 사용되지 않는 기능 및 운영 체제

[제거되는 항목과 사용되지 않는 항목](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)에서 구현되기 전의 지원 변경 내용을 알아보세요.

- Azure 콘텐츠 공유를 위한 구현이 변경되었습니다. **CMG가 클라우드 배포 지점으로 기능하고 Azure 스토리지에서 콘텐츠를 제공하도록 허용** 옵션을 사용하도록 설정하여 콘텐츠 지원 클라우드 관리 게이트웨이를 사용합니다. 나중에는 기존 클라우드 배포 지점을 만들 수 없습니다.

버전 1902에서는 다음 제품이 지원되지 않습니다.  

- Linux 및 UNIX 클라이언트. [버전 1802](/sccm/core/plan-design/changes/whats-new-in-version-1802#deprecation-announcement-for-linux-and-unix-client-support)의 지원 중단이 발표되었습니다. 따라서 Linux 서버를 관리하려면 Microsoft Azure 관리를 고려해야 합니다. Azure 솔루션은 대부분의 경우 Linux용 종단 간 패치 관리를 포함하여 Configuration Manager 기능을 능가하는 광범위한 Linux 지원을 제공합니다.



## <a name="bkmk_infra"></a> 사이트 인프라

### <a name="client-health-dashboard"></a>클라이언트 상태 대시보드
<!--3599209-->
사용자의 환경을 보호하기 위해 소프트웨어 업데이트 및 기타 앱을 배포하지만 이러한 배포는 정상 클라이언트에만 적용됩니다. 비정상 Configuration Manager 클라이언트는 전반적인 규정 준수에 부정적인 영향을 줍니다. 클라이언트 상태 확인은 분모에 따라 어려울 수 있습니다. 관리 범위에 있어야 하는 총 디바이스는 몇 개인가요? 예를 들어 Active Directory에서 모든 시스템을 검색 하는 경우 이러한 레코드의 일부가 사용 중지된 머신에 해당된다 해도 이 프로세스는 분모를 증가시킵니다. 

이제 사용자 환경에서 Configuration Manager 클라이언트의 상태에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 클라이언트 상태, 시나리오 상태 및 일반적인 오류를 봅니다. OS 및 클라이언트 버전으로 잠재적인 문제를 확인하려면 몇 가지 특성으로 뷰를 필터링합니다. 

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다. **클라이언트 상태**를 확장하고 **클라이언트 상태 대시보드** 노드를 선택합니다. 

![클라이언트 상태 대시보드의 스크린샷](media/3599209-client-health-dashboard.png)

<!-- For more information, see [How to monitor clients](/sccm/core/clients/manage/monitor-clients). -->


### <a name="new-management-insight-rules"></a>새 관리 인사이트 규칙
관리 인사이트 기능에는 다음과 같은 새 규칙에 있습니다.

- 컬렉션 관리에 대한 권장 사항이 포함된 여러 규칙. 이러한 정보를 사용하여 관리를 간소화하고 성능을 개선합니다. **컬렉션** 그룹에서 이 새로운 규칙을 검토하세요.<!--3555752-->  

- **단순화된 관리** 그룹의 **클라이언트를 지원되는 Windows 10 버전으로 업데이트** 규칙. 이 규칙을 실행하면 더 이상 지원되지 않는 Windows 10 버전을 실행하는 클라이언트가 보고됩니다. 서비스 종료일이 임박한(3개월 이내) Windows 10 버전을 사용하는 클라이언트도 보고됩니다.<!--3897268-->  

<!-- For more information, see [Management insights](/sccm/core/servers/manage/management-insights). -->


### <a name="improvement-to-enhanced-http"></a>고급 HTTP로 개선
<!--3798957-->
이제 기본 사이트당 또는 중앙 관리 사이트에 대해 고급 HTTP를 활성화할 수 있습니다. 

중앙 관리 사이트의 속성에서 **HTTP 사이트 시스템에 대해 Configuration Manager 생성 인증서 사용**에 대한 옵션을 선택합니다. 이 설정은 중앙 관리 사이트의 사이트 시스템 역할에만 적용됩니다. 즉 이 설정은 계층에 대한 전역 설정이 아닙니다. 

<!-- For more information, see [enhanced HTTP](/sccm/core/plan-design/hierarchy/enhanced-http). -->


### <a name="improvement-to-setup-prerequisites"></a>설치 필수 조건 개선 사항
버전 1902를 설치하거나 해당 버전으로 업데이트하는 경우 Configuration Manager 설치는 이제 다음과 같은 필수 구성 요소 검사를 포함합니다.

- **원격 SQL Server에서 시스템 다시 시작 보류 중**: 이 필수 조건 검사 항목은 **시스템 다시 시작 보류 중** 규칙과 비슷하지만 원격 SQL Server를 검사합니다. 자세한 내용은 [필수 조건 검사 목록](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#pending-system-restart-on-the-remote-sql-server)을 참조하세요. <!--SCCMDocs-pr issue 3377-->  



## <a name="bkmk_cloud"></a> 클라우드 연결 관리

### <a name="stop-cloud-service-when-it-exceeds-threshold"></a>임계값을 초과하는 경우 클라우드 서비스 중지
<!--3735092-->
이제 Configuration Manager는 총 데이터 전송이 한도를 초과하는 경우 CMG(클라우드 관리 게이트웨이) 서비스를 중지할 수 있습니다. CMG에는 사용량이 경고 또는 위험 수준에 도달하는 경우 항상 알림을 트리거하는 경고가 있습니다. 사용량 급증으로 인한 예기치 않은 모든 Azure 비용을 줄이려면 이 새 옵션은 클라우드 서비스를 해제합니다. 

CMG에서 [아웃바운드 트래픽 경고를 설정](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway#set-up-outbound-traffic-alerts)한 다음, **중요한 임계값을 초과하는 경우 이 서비스 중지** 옵션을 사용하도록 설정합니다.  

<!-- For more information, see [Set up outbound traffic alerts](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway#set-up-outbound-traffic-alerts). -->


### <a name="use-azure-resource-manager-for-cloud-services"></a>클라우드 서비스에 대한 Azure Resource Manager 사용
<!--3605704-->
1810 버전부터 Azure의 기존 서비스 배포는 Configuration Manager에서 더 이상 사용되지 않습니다. 해당 버전은 이러한 Azure 배포의 만들기를 지원하는 마지막 버전입니다. 

기존 배포가 계속 작동합니다. 이번 현재 분기 버전부터 Azure Resource Manager는 클라우드 관리 게이트웨이 및 클라우드 배포 지점의 새 인스턴스를 배포하는 유일한 메커니즘입니다.

<!-- For more information, see [Azure Resource Manager for the cloud management gateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager).   -->


### <a name="add-cloud-management-gateway-to-boundary-groups"></a>경계 그룹에 클라우드 관리 게이트웨이 추가
<!--3640932-->
이제 경계 그룹에 클라우드 관리 게이트웨이(CMG)를 연결할 수 있습니다. 이 구성을 사용하면 클라이언트 통신 시 클라이언트가 경계 그룹 관계에 따라 CMG로 기본 설정되거나 대체됩니다. 이 동작은 지점과 VPN 시나리오에서 특히 유용합니다. 느리고 값비싼 WAN 링크를 사용하는 대신 Microsoft Azure에 연결된 빠른 인터넷 링크를 사용하도록 클라이언트 트래픽을 유도할 수 있습니다.

<!-- For more information, see [Plan for the CMG](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway). -->



## <a name="bkmk_real"></a> 실시간 관리

### <a name="run-cmpivot-from-the-central-administration-site"></a>중앙 관리 사이트에서 CMPivot 실행
<!--3610960-->
***[업데이트됨]*** Configuration Manager는 이제 계층 구조의 중앙 관리 사이트에서 CMPivot의 실행을 지원합니다. 기본 사이트는 계속 클라이언트 통신을 처리합니다. 중앙 관리 사이트에서 CMPivot을 실행하는 경우 고속 메시지 구독 채널을 통해 기본 사이트와 통신합니다. 이 통신은 사이트 간 표준 SQL 복제를 따르지 않습니다.

자세한 내용은 [실시간 데이터용 CMPivot](/sccm/core/servers/manage/cmpivot#bkmk_cmpivot1902)을 참조하세요.


### <a name="edit-or-copy-powershell-scripts"></a>PowerShell 스크립트 편집 또는 복사
<!--3705507-->
이제 스크립트 실행 기능으로 사용되는 기존 PowerShell 스크립트를 **편집**하거나 **복사**할 수 있습니다. 변경하려는 스크립트를 다시 만드는 대신 직접 편집하면 됩니다. 두 작업 모두 새 스크립트를 만들 대와 동일한 마법사 환경을 사용합니다. 스크립트를 편집하거나 복사할 때는 Configuration Manager의 승인 상태가 유지되지 않습니다. 

<!-- For more information, see [Run Scripts](/sccm/apps/deploy-use/create-deploy-scripts). -->



## <a name="bkmk_content"></a> 콘텐츠 관리

### <a name="distribution-point-maintenance-mode"></a>배포 지점 유지 관리 모드 
<!--3555754-->
이제 유지 관리 모드에서 배포 지점을 설정할 수 있습니다. 소프트웨어 업데이트를 설치할 때나 서버에서 하드웨어를 변경할 때 유지 관리 모드를 사용합니다.

배포 지점이 유지 관리 모드 상태인 동안 다음 동작을 유지합니다. 

- 사이트는 배포 지점에 콘텐츠를 배포하지 않습니다.  

- 관리 지점이 클라이언트에 이 배포 지점의 위치를 반환하지 않습니다. 

- 사이트를 업데이트하면 유지 관리 모드의 배포 지점이 계속 업데이트됩니다. 

- 배포 지점 속성은 읽기 전용입니다. 예를 들어 인증서를 변경하거나 경계 그룹을 추가할 수 없습니다.  

- 콘텐츠 유효성 검사와 같은 모든 예약된 작업은 계속 동일한 일정에 따라 실행됩니다. 

<!-- For more information, see [Maintenance mode](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_maint) -->



## <a name="bkmk_client"></a> 클라이언트 관리

### <a name="client-provisioning-mode-timeout"></a>클라이언트 프로비전 모드 시간 제한
<!--3197824-->
작업 순서가 클라이언트를 프로비전 모드에 배치하는 경우 타임스탬프를 설정합니다. 프로비전 모드의 클라이언트는 타임스탬프 이후의 기간을 60분마다 확인합니다. 48시간을 초과하는 프로비전 모드에 있는 경우 클라이언트는 자동으로 프로비전 모드를 종료하고 해당 프로세스를 다시 시작합니다. 

<!-- For more information, see ... -->

### <a name="view-first-screen-only-during-remote-control"></a>원격 제어 시 첫 번째 화면만 보기
<!--3231732-->
***[업데이트]*** 두 대 이상의 모니터를 사용하는 클라이언트에 연결하면 Configuration Manager 원격 제어 뷰어에서 모든 화면을 보기 어려울 수 있습니다. 이제 원격 도구 운영자가 **모든 화면** 보기와 **첫 번째 화면**만 보기 중 선택할 수 있습니다.

자세한 내용은 [Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법](/sccm/core/clients/manage/remote-control/remotely-administer-a-windows-client-computer)을 참조하세요. 


### <a name="specify-a-custom-port-for-peer-wakeup"></a>피어 절전 모드 해제를 위한 사용자 지정 포트 지정
<!--3605925-->
***[업데이트]*** 이제 절전 모드 해제 프록시에 대한 사용자 지정 포트 번호를 지정할 수 있습니다. 클라이언트 설정의 **전원 관리** 그룹에서 **Wake On LAN 포트 번호(UDP)** 설정을 구성합니다.  

자세한 내용은 [Wake On LAN을 구성하는 방법](/sccm/core/clients/deploy/configure-wake-on-lan)을 참조하세요.



<!-- ## <a name="bkmk_comgmt"></a> Co-management -->




<!-- ## <a name="bkmk_compliance"></a> Compliance settings -->



## <a name="bkmk_app"></a> 애플리케이션 관리

### <a name="improvements-to-application-approvals-via-email"></a>메일을 통한 애플리케이션 승인 기능 향상
<!--3594063-->
이 버전에서는 애플리케이션 요청에 대한 메일 알림을 받는 기능이 향상되었습니다. 사용자는 항상 소프트웨어 센터의 요청에 주석을 추가할 수 있습니다. 이 주석은 Configuration Manager 콘솔의 애플리케이션 요청에 표시됩니다. 이제 해당 주석은 이메일에도 표시됩니다. 이메일에 이 주석이 포함되면 승인자가 요청을 승인하거나 거부하는 데 더 나은 결정을 내릴 수 있습니다.

<!-- For more information, see [Email notifications](/sccm/apps/deploy-use/app-approval#bkmk_email-approve). -->


### <a name="improvements-to-package-conversion-manager"></a>Package Conversion Manager 개선 사항
<!-- SCCMDocs-pr issue #3357 -->
이 버전에는 다음의 [Package Conversion Manager](/sccm/apps/pcm/package-conversion-manager) 개선 사항이 포함되어 있습니다.
- 기본적으로 7일마다 예약된 패키지 분석이 실행됩니다.
- 패키지 분석 및 변환을 위한 PowerShell cmdlet
- 일반 버그 수정 및 개선 사항



## <a name="bkmk_osd"></a> OS 배포


### <a name="progress-status-during-in-place-upgrade-task-sequence"></a>현재 위치 업그레이드 작업 순서 중 진행 상태
<!--3747129-->
이제 Windows 10 현재 위치 업그레이드 작업 순서 중에 더욱 자세한 진행률 표시줄이 표시됩니다. 진행률 표시줄은 작업 순서가 진행되는 동안 확인하기 어려운 Windows 설정의 진행률을 보여줍니다. 사용자는 이제 백그라운드 진행 상태를 어느 정도 파악할 수 있습니다. 더 이상 진행률을 확인할 방법이 없어서 업그레이드 프로세스가 일시 중단되지는 않았는지 걱정할 필요가 없습니다.  

![Windows 업그레이드 진행률을 보여주는 작업 순서의 예](media/3747129-installation-progress.png)

이 기능은 지원되는 모든 Windows 10 버전에서 현재 위치 업그레이드 작업 순서로만 작동합니다. 


### <a name="improvements-to-task-sequence-media-creation"></a>향상된 작업 순서 미디어 만들기 기능

<!--3556027, fka 1359388-->
***[업데이트]*** 이 버전에는 작업 순서 미디어를 더 잘 만들고 관리하는 데 도움이 되는 몇 가지 향상된 기능이 포함되어 있습니다. 자세한 내용은 특정 미디어 유형에 대한 다음 문서를 참조하세요.

- [독립 실행형 미디어 만들기](/sccm/osd/deploy-use/create-stand-alone-media)
- [사전 준비된 미디어 만들기](/sccm/osd/deploy-use/create-prestaged-media)
- [부팅 가능한 미디어 만들기](/sccm/osd/deploy-use/create-bootable-media)
- [미디어 캡처 만들기](/sccm/osd/deploy-use/create-capture-media)

#### <a name="specify-temporary-storage"></a>임시 스토리지 지정

작업 순서 미디어를 만들 때 이제 사이트에서 데이터의 임시 스토리지에 사용하는 위치를 사용자 지정합니다. 이 프로세스에는 많은 임시 드라이브 공간이 필요할 수 있습니다. 이 변경 내용은 이러한 임시 파일을 저장할 위치를 선택하는 데 큰 유연성을 제공합니다.

**작업 순서 미디어 만들기 마법사**에서 **준비 폴더**에 대한 위치를 지정합니다. 기본적으로 이 위치는 다음 경로 `%UserProfile%\AppData\Local\Temp`와 유사합니다.

#### <a name="add-a-label-to-the-media"></a>미디어에 레이블 추가

이제 작업 순서 미디어에 레이블을 추가할 수 있습니다. 이 레이블을 통해 미디어를 만든 후 미디어를 보다 잘 식별할 수 있습니다. **작업 순서 미디어 만들기 마법사**에서 **미디어 레이블**을 지정합니다.

#### <a name="include-autoruninf-file-on-media"></a>미디어에 autorun.inf 파일 포함

<!-- 4090666 -->
작업 순서 미디어를 만들 때 Configuration Manager는 autorun.inf 파일을 추가하지 않습니다. 이 파일은 일반적으로 맬웨어 방지 제품에서 차단됩니다. 시나리오에 필요한 경우 파일이 포함될 수 있습니다.


### <a name="import-a-single-index-of-an-os-image"></a>OS 이미지의 단일 인덱스 가져오기
<!--3719699-->
WIM(Windows 이미지) 파일을 Configuration Manager로 가져오면 이제 파일의 모든 이미지 인덱스가 아닌 단일 인덱스를 자동으로 가져오도록 지정할 수 있습니다. 이 옵션은 다음과 같은 이점을 제공합니다.

- 더 작은 이미지 파일  
- 더 빠른 오프라인 설치  
- 오프라인 설치 후 더 작은 이미지 파일에 대한 이미지 서비스 최적화 

OS 이미지를 가져올 때 **지정된 WIM 파일에서 특정 이미지 인덱스 추출** 옵션을 선택하세요. 그런 다음, 목록에서 이미지 인덱스를 선택합니다.  

<!-- For more information, see [Add an OS image](/sccm/osd/get-started/manage-operating-system-images#BKMK_AddOSImages). -->


### <a name="optimized-image-servicing"></a>최적화된 이미지 서비스
<!--3555951-->
OS 이미지에 소프트웨어 업데이트를 적용하는 경우 대체된 모든 업데이트를 제거하여 출력을 최적화하는 새로운 옵션이 있습니다. 오프라인 설치의 최적화는 단일 인덱스를 사용하는 이미지에만 적용됩니다. 

OS 이미지를 업데이트할 일정을 생성할 때 **이미지가 업데이트된 후 대체된 업데이트 제거** 옵션을 선택합니다. 

<!-- For more information, see [Apply software updates to an image](/sccm/osd/get-started/manage-operating-system-images#BKMK_OSImagesApplyUpdates).  -->


### <a name="improvements-to-run-powershell-script-task-sequence-step"></a>향상된 PowerShell 스크립트 실행 작업 순서 단계 기능

<!--3556028, fka 1359389-->
***[업데이트]*** **PowerShell 스크립트 실행** 작업 순서 단계에는 이제 다음과 같은 개선 사항이 포함됩니다.  

- 이제 이 단계에서 Windows PowerShell 코드를 직접 입력할 수 있습니다. 이 변경을 통해 먼저 스크립트를 사용하여 패키지를 만들고 배포하지 않고 작업 순서 중 PowerShell 명령을 실행할 수 있습니다.

- **PowerShell 스크립트 입력** 옵션을 선택할 때 **스크립트 편집**을 선택합니다. 새 PowerShell 스크립트 창에서 제공하는 작업은 다음과 같습니다.  

    - 직접 스크립트 편집  

    - 파일에서 기존 스크립트 열기  

    - Configuration Manager에서 승인된 기존 스크립트로 이동

- 사용자 지정 작업 순서 변수에 스크립트 출력 저장  

- 작업 순서 로그에 스크립트 매개 변수를 포함시키려면 **OSDLogPowerShellParameters** 작업 순서 변수를 **TRUE**로 설정합니다. 기본적으로 매개 변수는 로그에 없습니다.  

- [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계와 유사한 기능을 제공하는 기타 개선 사항. 예를 들어 대체 사용자 자격 증명을 지정하거나 시간 제한을 지정합니다.

> [!Important]  
> 이 새로운 Configuration Manager 기능을 활용하려면 사용자를 업데이트한 후 클라이언트를 최신 버전으로 업데이트하세요. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.

자세한 내용은 [PowerShell 스크립트 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunPowerShellScript)을 참조하세요.


### <a name="other-improvements-to-os-deployment"></a>기타 향상된 OS 배포

<!--3633146,3641475,3654172,3734270-->
***[업데이트]*** 이 버전에는 다음과 같은 향상된 OS 배포가 포함됩니다.

- 작업 순서에 대한 새로운 **보기** 기본 동작이 있습니다. <!--3633146-->  

- 이제 작업 순서 오류 대화 상자 창에 자세한 정보가 표시됩니다. 실패한 작업 순서 단계의 이름이 표시됩니다. <!--3641475-->  

- **OSDDoNotLogCommand** 작업 순서 변수를 true로 설정한 경우 로그 파일의 명령줄 실행 단계에서 명령줄을 감춥니다. 이전에 smsts.log의 패키지 설치 단계에서 프로그램 이름을 마스킹했습니다.<!--3654172-->  

- Windows 배포 서비스 없이 배포 지점에서 PXE 응답기를 사용하도록 설정하면 이제 DHCP 서비스와 동일한 서버에서 실행할 수 있습니다. <!--3734270-->  <!-- For more information, see ... -->



## <a name="bkmk_userxp"></a> 소프트웨어 센터

### <a name="replace-toast-notifications-with-dialog-window"></a>알림 메시지를 대화 상자 창으로 바꾸기

<!--3555947-->
***[업데이트]*** 사용자가 다시 시작이나 필요한 배포에 대한 Windows 알림 메시지를 보지 못하고 지나치는 경우가 있습니다. 이 경우 알림을 반복 설정하는 기능도 보지 못하게 됩니다. 이는 클라이언트가 기한에 도달했을 때 사용자 환경을 저하할 수 있습니다.

이제 환경을 다시 시작해야 하거나 소프트웨어 변경이 필요한 경우, 알림 메시지보다 더 확실히 표시되는 대화 상자 창을 사용할 수 있습니다.

자세한 내용은 [소프트웨어 센터 계획](/sccm/apps/plan-design/plan-for-software-center#bkmk_impact)을 참조하세요.


### <a name="configure-user-device-affinity-in-software-center"></a>소프트웨어 센터에서 사용자 디바이스 선호도 구성
<!--3485366-->
1806 버전에서 시작된 [소프트웨어 센터 인프라 개선 사항](/sccm/core/plan-design/changes/whats-new-in-version-1806#software-center-infrastructure-improvements)을 사용하는 경우 대부분의 시나리오에서 애플리케이션 카탈로그 사이트 서버 역할이 더 이상 필요하지 않습니다. 일부 고객은 여전히 애플리케이션 카탈로그에 의존하여 사용자가 사용자 디바이스 선호도에 대해 자신의 기본 디바이스를 설정할 수 있도록 했습니다. 

이제 사용자는 소프트웨어 센터에서 자신의 기본 디바이스를 설정할 수 있습니다. 이렇게 하면 이러한 사용자가 Configuration Manager에서 디바이스의 기본 사용자로 지정됩니다.

<!-- For more information, see [Link users and devices with user device affinity](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity). -->


### <a name="configure-default-views-in-software-center"></a>소프트웨어 센터의 기본 보기 구성
<!--3612112-->
이 버전의 Configuration Manager에서 소프트웨어 센터를 사용자 지정하는 방법입니다.
 
- 애플리케이션의 기본 레이아웃을 타일 또는 목록으로 설정  

    - 사용자가 이 구성을 변경하면 소프트웨어 센터에 사용자의 선택 사항이 저장됩니다.  

- 기본 애플리케이션 필터를 모두 또는 필수 앱만으로 구성  

    - 소프트웨어 센터는 항상 사용자의 기본 설정을 사용합니다. 사용자는 이 필터를 변경할 수 있으나, 소프트웨어 센터에 사용자의 선택 사항이 저장되지 않습니다.    

클라이언트 설정의 **소프트웨어 센터** 그룹에서 이 설정들을 지정합니다.

<!-- For more information, see [About client settings](/sccm/core/clients/deploy/about-client-settings#software-center). -->



## <a name="bkmk_sum"></a> 소프트웨어 업데이트

### <a name="specify-priority-for-feature-updates-in-windows-10-servicing"></a>Windows 10 서비스에서 기능 업데이트에 대한 우선 순위 지정
<!--3734525-->
***[업데이트]*** 클라이언트가 [Windows 10 서비스](/sccm/osd/deploy-use/manage-windows-as-a-service)를 통해 기능 업데이트를 설치하는 우선 순위를 조정합니다. 기본적으로 클라이언트는 처리 우선 순위가 높은 기능 업데이트부터 설치합니다. 

이 옵션은 클라이언트 설정을 사용하여 구성합니다. **소프트웨어 업데이트** 그룹에서 다음 설정을 구성합니다. **기능 업데이트에 대한 스레드 우선 순위를 지정합니다**.

자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#software-updates)를 참조하세요. 



## <a name="bkmk_o365"></a> Office 관리

### <a name="redirect-windows-known-folders-to-onedrive"></a>알려진 Windows 폴더를 OneDrive로 리디렉션
<!--3556021-->
***[업데이트]*** Configuration Manager를 사용하여 알려진 Windows 폴더를 비즈니스용 OneDrive로 이동합니다. 이러한 폴더로는 바탕 화면, 문서, 사진 등이 있습니다. Windows 10 업그레이드의 간소화를 위해, 작업 순서를 배포하기 전에 해당 설정을 Windows 7 클라이언트에 배포하세요. 

비즈니스용 OneDrive의 이 기능에 대한 자세한 내용은 [알려진 Windows 폴더를 OneDrive로 리디렉션 및 이동](https://docs.microsoft.com/onedrive/redirect-known-folders)을 참조하세요.

먼저 [Office 365 테넌트 ID를 찾습니다](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id). 그런 다음 OneDrive 동기화 클라이언트 버전 18.111.0603.0004 이상을 배포합니다. 자세한 내용은 [System Center Configuration Manager를 사용하여 OneDrive 앱 배포](https://docs.microsoft.com/onedrive/deploy-on-windows)를 참조하세요.  

Business용 OneDrive 프로필을 만들고 배포하려면 Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동합니다. **준수 설정**을 확장하고 **비즈니스용 OneDrive 프로필** 노드를 선택합니다.  

자세한 내용은 [비즈니스 프로필용 OneDrive](/sccm/compliance/deploy-use/onedrive-profile) 문서의 Windows 알려진 폴더를 OneDrive 섹션으로 리디렉션을 참조하세요.


### <a name="integration-for-office-365-proplus-readiness"></a>Office 365 ProPlus 준비를 위한 통합
<!--3735402-->
***[업데이트]*** Configuration Manager를 사용하여 Office 365 ProPlus로 업그레이드할 준비가 된 높은 정확도의 디바이스를 확인합니다. 통합은 Office 추가 기능 및 사용자 환경에서 사용되는 매크로의 잠재적인 호환성 문제에 대한 인사이트를 제공합니다. 그런 다음, Configuration Manager를 사용하여 준비된 디바이스에 Office를 배포합니다. 

기존 Office 365 클라이언트 관리 대시보드에는 이제 새 타일인 **Office 365 ProPlus 업그레이드 준비**가 포함됩니다.

자세한 내용은 [Office 365 클라이언트 관리 대시보드](/sccm/sum/deploy-use/office-365-dashboard#bkmk_o365_readiness)를 참조하세요.


### <a name="additional-languages-for-office-365-updates"></a>Office 365 업데이트용 추가 언어
<!--3555955-->
이제 Configuration Manager는 Office 365 클라이언트 업데이트를 위해 지원되는 모든 언어를 지원합니다. 이제 업데이트 워크플로는 **Office 365 클라이언트 업데이트**를 위한 다양한 언어**에서 Windows 업데이트**를 위한 38개 언어를 구분합니다. 

자세한 내용은 [Office 365 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates#bkmk_o365_lang)를 참조하세요.


### <a name="office-products-on-lifecycle-dashboard"></a>수명 주기 대시보드의 Office 제품
<!--3556026-->
***[업데이트]*** 제품 수명 주기 대시보드에는 이제 Office 2003에서 Office 2016까지 설치 버전에 대한 정보가 포함됩니다. 사이트가 24시간마다 수명 주기 요약 작업을 실행한 후 데이터가 표시됩니다.

자세한 내용은 [제품 수명 주기 대시보드 사용](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard)을 참조하세요.



<!-- ## <a name="bkmk_inv"></a> Inventory -->



## <a name="bkmk_pod"></a> 단계별 배포

### <a name="dedicated-monitoring-for-phased-deployments"></a>단계별 배포에 대한 전용 모니터링
<!--3555949-->
***[업데이트]*** 이제 단계별 배포에는 자체 전용 모니터링 노드가 있습니다. 이 노드를 사용하면 만든 단계별 배포를 식별한 다음, 단계별 배포 모니터링 보기로 이동하기가 쉬워집니다. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **단계별 배포** 노드를 선택합니다. 그러면 단계별 배포 목록이 표시됩니다.

자세한 내용은 [단계별 배포 모니터링 보기](/sccm/osd/deploy-use/manage-monitor-phased-deployments#bkmk_monitor)를 참조하세요. 


### <a name="improvement-to-phased-deployment-success-criteria"></a>단계적 배포 성공 조건 개선
<!--3555946-->
***[업데이트]*** 단계별 배포에서 단계의 성공을 위한 추가 조건을 지정합니다. 백분율 대신 이 조건은 이제 성공적으로 배포된 디바이스의 수도 사용할 수 있습니다. 이 옵션은 컬렉션의 크기가 변수이고, 다음 단계로 이동하기 전에 성공을 표시하는 특정 수의 디바이스가 있을 때 유용합니다. 

작업 순서, 소프트웨어 업데이트 또는 애플리케이션에 대한 단계별 배포를 만듭니다. 그런 다음 마법사의 설정 페이지에서 첫 번째 단계의 성공을 위한 조건으로 다음 옵션을 선택합니다. **성공적으로 배포된 디바이스 수**.

자세한 내용은 [단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)를 참조하세요.



## <a name="bkmk_admin"></a> Configuration Manager 콘솔

### <a name="bkmk_console"></a> 향상된 Configuration Manager 콘솔 기능
<!--3594151-->
MMS(Midwest Management Summit) Desert Edition 2018에서 수렴한 고객의 피드백에 따라 이 버전에는 다음과 같은 향상된 Configuration Manager 콘솔 기능이 포함되어 있습니다.
- 애플리케이션 검색 방법을 위한 레지스트리 찾아보기 창 최대화
- 애플리케이션 배포에서 컬렉션으로 이동
- 모니터링 상태에서 콘텐츠 제거
- **모니터링** 작업 영역의 **배포** 노드에서 정수 값으로 보기 정렬
- 많은 수의 결과에 대한 경고 이동

<!-- For more information, see [Using the Configuration Manager console](/sccm/core/servers/manage/admin-console). -->


### <a name="configuration-manager-console-notifications"></a>Configuration Manager 콘솔 알림
<!--3556016, fka 1318035-->
적절한 작업을 수행할 수 있도록 보다 정확한 정보를 제공하기 위해 Configuration Manager 콘솔은 이제 다음 이벤트를 알려 줍니다.
- Configuration Manager 자체에 대한 업데이트를 사용할 수 있는 경우
- 환경에서 수명 주기 및 유지 관리 이벤트가 발생하는 경우

이 알림은 리본 아래의 콘솔 창의 맨 위에 있는 막대입니다. Configuration Manager 업데이트를 사용할 수 있는 경우 이전 환경을 대체합니다. 이러한 콘솔 내 알림은 여전히 중요한 정보를 표시하지만 콘솔에서 작업에 방해가 되지 않습니다. 중요한 알림을 해제할 수 없습니다. 콘솔은 제목 표시줄의 새 알림 영역에서 모든 알림을 표시합니다. 

<!-- For more information, see [Using the Configuration Manager console](/sccm/core/servers/manage/admin-console). -->


### <a name="confirmation-of-console-feedback"></a>콘솔 피드백 확인
<!--3556010-->
***[업데이트됨]*** Configuration Manager 콘솔에서 [피드백](/sccm/core/understand/find-help#product-feedback)을 보내면 이제 확인 메시지가 표시됩니다. 이 메시지에는 사용자가 추적 식별자로서 Microsoft에 제공할 수 있는 **피드백 ID**가 포함되어 있습니다.

자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#bkmk_feedbackid)을 참조하세요.


### <a name="view-recently-connected-consoles"></a>최근에 연결된 콘솔 보기 
<!--3699367-->
***[업데이트됨]*** 이제 Configuration Manager 콘솔에 대한 가장 최근의 연결을 볼 수 있습니다. 보기에는 활성 연결 및 최근에 연결된 콘솔이 포함되어 있습니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **보안**을 확장한 다음, **콘솔 연결** 노드를 선택합니다.

자세한 내용은 [Configuration Manager 콘솔 사용](/sccm/core/servers/manage/admin-console#bkmk_viewconnected)을 참조하세요.


### <a name="in-console-documentation-dashboard"></a>콘솔 내 설명서 대시보드
<!--3556019, fka 1357546-->
새 **커뮤니티** 작업 영역에 새 **설명서** 노드가 있습니다. 이 노드는 Configuration Manager 설명서 및 지원 문서에 대한 최신 정보를 포함합니다.

<!-- For more information, see [Using the Configuration Manager console](/sccm/core/servers/manage/admin-console). -->


### <a name="search-device-views-using-mac-address"></a>MAC 주소를 사용하여 검색 디바이스 보기
<!--3600878-->
이제 Configuration Manager 콘솔의 디바이스 보기에서 MAC 주소를 검색할 수 있습니다. 이 속성은 PXE 기반 배포 문제를 해결하는 동안 OS 배포 관리자에게 유용합니다. 디바이스 목록을 확인하면 보기에 **MAC 주소** 열을 추가합니다. 검색 필드를 사용하여 **MAC 주소** 검색 조건을 추가합니다. 


### <a name="use-net-47-for-improved-console-accessibility"></a>콘솔 접근성 향상을 위해 .NET 4.7 사용
<!-- SCCMDocs-pr issue #3228 -->
Configuration Manager 콘솔의 접근성 기능을 개선하려면 콘솔을 실행하는 컴퓨터에서 .NET을 4.7 버전 이상으로 업데이트하세요. 

자세한 내용은 [Configuration Manager의 내게 필요한 옵션 기능](/sccm/core/understand/accessibility-features)을 참조하세요.


### <a name="changes-to-console-setup-process"></a>콘솔 설치 프로세스 변경 내용

<!-- 3612513 -->
***[업데이트]***  Configuration Manager 콘솔을 설치할 때 필요한 새 구성 요소가 있습니다. 콘솔을 다른 컴퓨터에서 설치하기 위한 패키지를 생성하는 경우, 패키지에 다음 파일이 포함되어 있는지 확인합니다.

- ConsoleSetup.exe
- AdminConsole.msi
- ConfigMgr.AC_Extension.i386.cab
- ConfigMgr.AC_Extension.amd64.cab

사이트 서버를 설치하거나 업데이트하는 경우 설치 파일 및 사이트의 지원되는 언어 팩이 **Tools\ConsoleSetup** 하위 폴더에 복사됩니다. 자세한 내용은 [Configuration Manager 콘솔 설치](/sccm/core/servers/deploy/install/install-consoles)를 참조하세요.



<!-- ## <a name="bkmk_opmdm"></a> On-premises MDM -->




## <a name="other-updates"></a>기타 업데이트

새 기능 외에 이 릴리스에는 버그 수정과 같은 추가 변경 사항도 포함되어 있습니다. 자세한 내용은 [Configuration Manager 현재 분기 버전 1902의 변경 내용 요약](https://support.microsoft.com/help/4498910)을 참조하세요.

Configuration Manager용 Windows PowerShell cmdlet의 변경 내용에 대한 자세한 내용은 [PowerShell 버전 1902 릴리스 정보](https://docs.microsoft.com/powershell/sccm/1902-release-notes?view=sccm-ps)를 참조하세요.

<!-- 
The following update rollup (4486457) is available in the console starting on 25 January 2019: [Update rollup for Configuration Manager current branch, version 1902](https://support.microsoft.com/help/4486457).


### Hotfixes

The following additional hotfixes are available to address specific issues:

| ID | Title | Date | In-console |
|---------|---------|---------|---------|
| [4487960](https://support.microsoft.com/help/4487960) | Microsoft Intune connector certificate does not renew in Configuration Manager | 18 January 2019 | Yes |
 
-->



## <a name="next-steps"></a>다음 단계

이 버전을 설치할 준비가 되었으면 [Configuration Manager에 대한 업데이트 설치](/sccm/core/servers/manage/updates) 및 [업데이트 1902를 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1902)을 참조하세요.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용합니다.  
>
>  다음에 대해 자세히 알아보세요.    
>   - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
>   - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

알려진 중요한 문제는 [릴리스 정보](/sccm/core/servers/deploy/install/release-notes)를 참조하세요.

사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1902#post-update-checklist)도 검토하세요.
