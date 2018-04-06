---
title: 새 버전 1802
titleSuffix: Configuration Manager
description: Configuration Manager 1802 버전에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bd637b1-d7a1-411b-877a-c7aae9741173
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 4582d1105f2465c37e001570227112bfca3bad1c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2018
---
# <a name="whats-new-in-version-1802-of-system-center-configuration-manager"></a>System Center Configuration Manager 1802 버전의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 현재 분기에 대한 1802 업데이트는 콘솔 내 업데이트로 사용할 수 있습니다. 1702, 1706 또는 1710 버전을 실행하는 사이트에서 이 업데이트를 적용합니다. <!-- baseline only statement: -->새 사이트를 설치할 때 기준 버전으로 사용할 수도 있습니다.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용해야 합니다.  
>
>  다음에 대해 자세히 알아보세요.    
>   - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
>   - [사이트에 업데이트 설치](/sccm/core/servers/manage/updates)  
>   - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

다음 섹션에서는 Configuration Manager 1802 버전에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated items](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated).

Version 1802 drops support for the following products:
-->


## <a name="site-infrastructure"></a>사이트 인프라

### <a name="reassign-distribution-point"></a>배포 지점 재할당
<!-- 1306937 -->
많은 고객들이 대형 Configuration Manager 인프라를 보유하고 있으며 환경을 단순화하기 위해 기본 또는 보조 사이트를 줄이고 있습니다. 하지만 관리 대상 고객에게 콘텐츠를 제공하기 위해 각 지사에서 배포 지점을 유지해야 합니다. 이러한 배포 지점에는 종종 여러 테라바이트 이상의 콘텐츠가 포함됩니다. 이 컨텐츠는 이러한 원격 서버에 배포하는 데 상당한 시간과 네트워크 대역폭을 소비합니다. 이 기능을 사용하면 콘텐츠를 재배포하지 않고 다른 기본 사이트에 배포 지점을 재할당할 수 있습니다. 이 작업은 서버의 모든 콘텐츠를 유지하면서 사이트 시스템 할당을 업데이트합니다. 자세한 내용은 [배포 지점 재할당](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_reassign)을 참조하세요.

### <a name="configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups"></a>Configuration Manager 경계 그룹을 사용하도록 Windows 배달 최적화 구성
<!-- 1324696 -->
Configuration Manager 경계 그룹을 사용하여 회사 네트워크 및 원격 사무실에 대한 콘텐츠 배포를 정의하고 규정합니다. [Windows 배달 최적화](/windows/deployment/update/waas-delivery-optimization)는 Windows 10 장치 간에 콘텐츠를 공유하는 클라우드 기반의 피어 투 피어 기술입니다. 이 릴리스부터는 피어 간에 콘텐츠를 공유할 때 경계 그룹을 사용하도록 배달 최적화를 구성합니다. 새 클라이언트 설정은 경계 그룹 식별자를 클라이언트의 배달 최적화 그룹 식별자로 적용합니다. 클라이언트는 배달 최적화 클라우드 서비스와 통신할 때 이 식별자를 사용하여 원하는 콘텐츠가 있는 피어를 찾습니다. 자세한 내용은 [콘텐츠 관리 관련 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization)을 참조하세요.

### <a name="support-for-windows-10-arm64-devices"></a>Windows 10 ARM64 장치 지원
<!-- 1353704 -->
이 릴리스부터는 Windows 10 ARM64 장치에서 구성 관리자 클라이언트가 지원됩니다. 기존 클라이언트 관리 기능도 이러한 새 장치에서 작동합니다. 예를 들어 하드웨어 및 소프트웨어 인벤토리, 소프트웨어 업데이트, 응용 프로그램 관리 등입니다. 운영 체제 배포는 현재 지원되지 않습니다. 

### <a name="improved-support-for-cng-certificates"></a>CNG 인증서에 대한 향상된 지원
<!-- 1357314 -->
Configuration Manager(현재 분기) 버전 1710은 [CNG(Cryptography: Next Generation) 인증서](/sccm/core/plan-design/network/cng-certificates-overview)를 지원합니다. 버전 1710은 여러 시나리오에서 클라이언트 인증서 지원을 제한합니다. 

이 릴리스부터 CNG 인증서를 사용하는 HTTPS 사용 서버 역할은 다음과 같습니다.
- 관리 지점
- 배포 지점
- 소프트웨어 업데이트 지점
- 상태 마이그레이션 지점  


### <a name="boundary-group-fallback-for-management-points"></a>관리 지점에 대한 경계 그룹 대체
<!-- 1324594 -->
[경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups) 간의 관리 지점에 대한 대체 관계를 구성합니다. 이 동작은 클라이언트에서 사용하는 관리 지점에 대한 제어를 강화합니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups#management-points)을 참조하세요.


### <a name="cloud-distribution-point-site-affinity"></a>클라우드 배포 지점 사이트 선호도
<!--503719-->
이 기능은 클라우드 배포 지점을 사용하여 지리적으로 분산된 다중 사이트 계층 구조의 고객에게 유용합니다. 인터넷 기반 클라이언트에서 콘텐츠를 검색할 때 이전에는 클라이언트에서 받는 클라우드 배포 지점 목록에 대한 순서가 없었습니다. 이 동작으로 인해 인터넷 기반 클라이언트는 지리적으로 멀리 떨어진 클라우드 배포 지점에서 콘텐츠를 받을 수 있습니다. 이처럼 먼 서버에서 콘텐츠를 다운로드하는 것은 일반적으로 더 가까운 서버보다 느립니다.
 
클라우드 배포 지점 사이트 선호도를 사용하면 인터넷 기반 클라이언트에서 정렬된 목록을 받습니다. 이 목록은 클라이언트의 할당된 사이트에서 클라우드 배포 지점의 우선 순위를 지정합니다. 이 동작을 통해 관리자는 사이트 리소스에서 콘텐츠를 다운로드할 때 의도한 디자인을 유지할 수 있습니다.
 

## <a name="management-insights"></a>관리 정보
<!-- 1353967 -->
System Center Configuration Manager의 관리 정보는 환경의 현재 상태에 대한 정보를 제공합니다. 이 정보는 사이트 데이터베이스의 데이터 분석을 기반으로 합니다. 이 정보를 통해 환경을 더 잘 이해하고 해당 정보에 기반한 조치를 취할 수 있습니다. 자세한 내용은 [관리 정보](/sccm/core/servers/manage/management-insights)를 참조하세요.

Configuration Manager 1802에서 사용할 수 있는 정보는 다음과 같습니다.
- 응용 프로그램:
    - 배포가 없는 응용 프로그램
- Cloud Services: <!--1356412-->
    - 공동 관리 준비 상태 평가 
    - 장치를 하이브리드 Azure Active Directory에 가입하도록 설정
    - ID 및 액세스 인프라 현대화
    -  Windows 10 1709 버전 이상으로 클라이언트 업그레이드 
- 컬렉션:
    - 비어 있는 컬렉션
- 간소화된 관리: <!--1355148-->
    - 오래된 클라이언트 버전  
- 소프트웨어 센터: 
    - 사용자를 응용 프로그램 카탈로그 대신 소프트웨어 센터로 직접 연결  
    - 새 버전의 Software Center 사용 
- Windows 10: <!--1357421-->
    - Windows 원격 분석 및 상용 ID 키 구성 
    - Configuration Manager를 업그레이드 준비에 연결 
   
<!-- ## Migration  -->



## <a name="client-management"></a>클라이언트 관리

### <a name="cloud-management-gateway-support-for-azure-resource-manager"></a>Azure Resource Manager에 대한 클라우드 관리 게이트웨이 지원
<!-- 1324735 -->
CMG([클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)) 인스턴스를 만들 때 이제 마법사에서 **Azure Resource Manager 배포**를 만들 수 있는 옵션을 제공합니다. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)는 모든 솔루션 리소스를 [리소스 그룹](/azure/azure-resource-manager/resource-group-overview#resource-groups)이라는 단일 엔터티로 관리하기 위한 최신 플랫폼입니다. Azure Resource Manager로 CMG를 배포하는 경우 사이트에서 Azure AD(Azure Active Directory)를 사용하여 필요한 클라우드 리소스를 인증하고 만듭니다. 이 최신 배포에는 클래식 Azure 관리 인증서가 필요하지 않습니다. 자세한 내용은 [CMG 토폴로지 디자인](/sccm/core/clients/manage/plan-cloud-management-gateway#azure-resource-manager)을 참조하세요.

> [!IMPORTANT]
> 이 기능은 Azure CSP(클라우드 서비스 공급자)를 지원하지 않습니다. Azure Resource Manager를 통한 CMG 배포는 CSP에서 지원하지 않는 클래식 클라우드 서비스를 계속 사용합니다. 자세한 내용은 [Azure CSP에 사용할 수 있는 Azure 서비스](/azure/cloud-solution-provider/overview/azure-csp-available-services)를 참조하세요.  

### <a name="improvements-to-cloud-management-gateway"></a>클라우드 관리 게이트웨이드의 향상된 기능  

- 이 릴리스부터 **클라우드 관리 게이트웨이**는 더 이상 시험판 기능이 아닙니다.  

- 기능 설명서가 개정되고 보강되었습니다. 자세한 내용은 다음 아티클을 참조하세요.
    - [클라우드 관리 게이트웨이에 대한 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
    - [클라우드 관리 게이트웨이 크기 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
    - [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
    - [클라우드 관리 게이트웨이에 대한 FAQ](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
    - [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
    - [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)  


### <a name="configure-hardware-inventory-to-collect-strings-larger-than-255-characters"></a>255자보다 큰 문자열을 수집하도록 하드웨어 인벤토리 구성
<!-- 1357389 -->
하드웨어 인벤토리 속성의 경우 255자를 초과하는 문자열을 구성할 수 있습니다. 이 변경 내용은 새로 추가된 클래스 및 키가 아닌 하드웨어 인벤토리 속성에만 적용됩니다. 자세한 내용은 [하드웨어 인벤토리 확장](/sccm/core/clients/manage/inventory/extend-hardware-inventory#BKMK_GreaterThan255) 문서를 참조하세요. 

 ### <a name="deprecation-announcement-for-linux-and-unix-client-support"></a>Linux 및 Unix 클라이언트 지원에 대한 사용 중단 알림
 <!--510139-->
Microsoft는 약 1년 후에 System Center Configuration Manager에서 Linux 및 UNIX 클라이언트 지원을 중단할 예정이므로 2019년 초에 SCCM 1902 릴리스에는 이러한 클라이언트가 포함되지 않습니다.  2018년 후반기의 Configuration Manager 1810 릴리스는 Linux 및 UNIX 클라이언트를 포함하는 마지막 릴리스이며, Configuration Manager 1810의 전체 수명 주기 동안 이러한 클라이언트가 지원됩니다.  Configuration Manager 1810 이후 고객이 Linux 서버를 관리하려면 Microsoft의 OMS(Operations Management Suite)를 고려해야 합니다.  OMS는 대부분의 경우 Linux용 종단 간 패치 관리를 포함하여 Configuration Manager 기능을 능가하는 광범위한 Linux 지원을 제공합니다.

### <a name="surface-device-dashboard"></a>Surface 장치 대시보드
<!--1355788-->
Surface 장치 대시보드는 사용자 환경에 있는 Surface 장치에 대한 정보를 제공합니다. 콘솔에서 **Surface 장치**  > **모니터링**으로 이동합니다. 표시되는 항목은 다음과 같습니다.
- Surfaces의 백분율
- Surface 모델의 백분율
- 상위 5개 펌웨어 버전

자세한 내용은 [Surface 대시보드](/sccm/core/clients/manage/surface-device-dashboard) 문서를 참조하세요.

### <a name="change-in-the-configuration-manager-client-install"></a>Configuration Manager 클라이언트 설치 변경
<!--1356195-->|
이 릴리스부터 Silverlight는 더 이상 클라이언트 장치에 자동으로 설치되지 않습니다. 자세한 내용은 [Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.#BKMK_ExternalDependencies)을 참조하세요.

## <a name="co-management"></a>공동 관리

### <a name="transition-endpoint-protection-workload-to-intune-using-co-management"></a>공동 관리를 사용하여 Endpoint Protection 워크로드를 Intune으로 전환
<!-- 1357365 -->
 공동 관리를 사용하도록 설정한 후 Endpoint Protection 워크로드를 Intune으로 전환할 수 있습니다. Endpoint Protection 워크로드를 전환하려면 공동 관리 속성 페이지로 이동한 다음, 슬라이더 막대를 Configuration Manager에서 **파일럿** 또는 **모두**로 이동합니다. 워크로드에 대한 자세한 내용은 [Intune으로 전환할 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune)를 참조하세요. 공동 관리에 대한 자세한 내용은 [Windows 10 장치에 대한 공동 관리](/sccm/core/clients/manage/co-management-overview)를 참조하세요.
 
### <a name="co-management-dashboard-in-system-center-configuration-manager"></a>System Center Configuration Manager의 공동 관리 대시보드
<!--1356648-->
이 릴리스부터 공동 관리에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 대시보드를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 장치를 식별하는 데 도움이 될 수 있습니다. 자세한 내용은 [공동 관리 대시보드](\sccm\core\clients\manage\client-management-dashboard) 문서를 참조하세요. 


## <a name="compliance-settings"></a>호환성 설정

### <a name="microsoft-edge-browser-policies"></a>Microsoft Edge 브라우저 정책
<!-- 1357310 -->
Windows 10 클라이언트에서 [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) 웹 브라우저를 사용하는 고객의 경우 Configuration Manager 준수 설정 정책을 만들어 여러 Microsoft Edge 설정을 구성합니다. 자세한 내용은 [Microsoft Edge 브라우저 프로필 만들기](/sccm/compliance/deploy-use/browser-profiles)를 참조하세요. 



## <a name="application-management"></a>응용 프로그램 관리

### <a name="allow-user-interaction-when-installing-an-application"></a>응용 프로그램 설치 시 사용자 상호 작용 허용
<!-- 1356976 -->
최종 사용자가 작업 순서를 실행하는 동안 응용 프로그램 설치와 상호 작용할 수 있습니다. 예를 들어 최종 사용자에게 다양한 옵션을 요구하는 설치 프로세스를 실행합니다. 일부 응용 프로그램 설치 관리자에서 사용자 프롬프트를 닫을 수 없거나, 설치 프로세스에 사용자에게만 알려진 특정 구성 값이 필요할 수 있습니다. 이 기능을 사용하면 이러한 설치 시나리오를 처리할 수 있습니다. 자세한 내용은 [배포 유형에 대한 사용자 환경 옵션 지정](/sccm/apps/deploy-use/create-applications#specify-user-experience-options-for-the-deployment-type)을 참조하세요.

### <a name="do-not-automatically-upgrade-superseded-applications"></a>교체된 응용 프로그램을 자동으로 업그레이드하지 않습니다
<!-- 1351266 -->
대체된 버전을 자동으로 업그레이드하지 않도록 응용 프로그램 배포를 구성합니다. 이제 **소프트웨어 배포 마법사**의 **배포 설정** 페이지에서 배포를 만들 때 **사용 가능** 또는 **필수** 설치 목적으로 **이 응용 프로그램의 교체된 버전을 자동으로 업그레이드**하는 옵션을 활성화하거나 비활성화할 수 있습니다. 자세한 내용은 [배포 설정 지정](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings)을 참조하세요.

### <a name="approve-application-requests-for-users-per-device"></a>장치당 사용자에 대한 응용 프로그램 요청 승인
<!-- 1357015 -->
이 릴리스부터는 사용자가 승인이 필요한 응용 프로그램을 요청할 때 특정 장치 이름이 요청의 일부로 포함됩니다. 관리자가 요청을 승인하면 사용자는 해당 장치에만 응용 프로그램을 설치할 수 있습니다. 사용자가 다른 장치에 응용 프로그램을 설치하려면 다른 요청을 제출해야 합니다. 자세한 내용은 [배포 설정 지정](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings)을 참조하세요.

 > [!Note]  
 > 이는 선택적 기능입니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  


### <a name="run-scripts-improvements"></a>향상된 스크립트 실행 기능 
<!-- 1236459 -->
 이 릴리스부터 **스크립트 실행**은 더 이상 시험판 기능이 아닙니다. 스크립트 출력은 이제 JSON 형식을 사용하여 반환됩니다. 자세한 내용은 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.


## <a name="operating-system-deployment"></a>운영 체제 배포

### <a name="windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway"></a>클라우드 관리 게이트웨이를 통한 Windows 10 현재 위치 업그레이드 작업 순서
<!-- 1357149 -->
이제 Windows 10 [내부 업그레이드 작업 순서](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)에서 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 통해 관리되는 인터넷 기반 클라이언트에 대한 배포를 지원합니다. 이 기능을 사용하면 원격 사용자가 회사 네트워크에 연결할 필요 없이 Windows 10으로 쉽게 업그레이드할 수 있습니다. 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg)항목을 참조하세요.

### <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Windows 10 현재 위치 업그레이드 작업 순서 개선 사항
<!-- 1357425 -->
이제 Windows 10 내부 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스 전후에 추가할 권장 작업이 있는 추가 그룹이 포함되어 있습니다. 이러한 작업은 장치를 Windows 10으로 성공적으로 업그레이드한 많은 고객들에게 공통적으로 적용됩니다. 자세한 내용은 [OS를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#recommended-task-sequence-steps-to-prepare-for-upgrade)를 참조하세요.

### <a name="improvements-to-operating-system-deployment"></a>운영 체제 배포 향상
이 릴리스에 포함된 운영 체제 배포에 대한 향상된 기능은 다음과 같습니다.
 - Windows PE에서 cmtrace.exe를 시작할 때 이 프로그램을 로그 파일에 대한 기본 뷰어로 만들지 여부를 선택하는 메시지가 더 이상 표시되지 않습니다. <!-- SMS 500897 -->
 - [패키지 콘텐츠 다운로드](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent) 작업 순서 단계에 부팅 이미지를 추가합니다.
 - [작업 순서 실행](/sccm/osd/understand/task-sequence-steps#child-task-sequence) 단계의 향상된 기능: <!-- 1261338 -->   
     - 소프트웨어 센터, PXE 및 미디어에서 모든 운영 체제 배포 시나리오를 지원합니다.
     - 개체 삭제 중 복사, 가져오기, 내보내기 및 경고와 같은 콘솔 작업이 향상되었습니다.
     - [사전 준비된 콘텐츠 파일 만들기](/sccm/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent) 마법사를 지원합니다.
     - 배포 확인과 통합됩니다. 자세한 내용은 [높은 위험 수준의 작업 순서 배포](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS)를 참조하세요. 
     - 작업 순서 실행 단계는 이제 단일 부모-자식 관계뿐만 아니라 여러 수준의 작업 순서에서도 사용할 수 있습니다. 여러 수준 관계는 복잡성이 증가되므로 신중하게 사용합니다. 이러한 관계는 여전히 순환 참조를 확인합니다.
    
### <a name="deployment-templates-for-task-sequences"></a>작업 순서에 대한 배포 템플릿
<!-- 1357391 -->
[작업 순서에 대한 배포 마법사](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS)에서 이제 배포 템플릿을 만들 수 있습니다. 배포 템플릿을 저장하고 기존 작업 순서나 새 작업 순서에 적용하여 배포를 만들 수 있습니다. 

### <a name="phased-deployments-for-task-sequences"></a>작업 순서에 대한 단계별 배포
<!--1356837-->
 단계별 배포는 [시험판 기능](/sccm/core/servers/manage/pre-release-features)입니다. 단계별 배포는 여러 컬렉션에서 작업 순서가 조정된 순차적 출시를 자동화합니다. 기본적으로 두 단계의 [단계별 배포를 만들거나](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence) 여러 단계를 수동으로 구성할 수 있습니다. 작업 순서의 단계별 배포는 PXE 또는 미디어 설치를 지원하지 않습니다.




## <a name="software-center"></a>소프트웨어 센터

### <a name="install-multiple-applications-in-software-center"></a>소프트웨어 센터에서 여러 응용 프로그램 설치
<!-- 1357126 -->
이제 최종 사용자 또는 데스크톱 기술자가 장치에 여러 응용 프로그램을 설치해야 하는 경우 소프트웨어 센터는 선택한 여러 응용 프로그램을 설치하도록 지원합니다. 이 동작을 사용하면 한 설치가 완료될 때까지 기다리지 않고 다음 설치를 시작할 수 있도록 사용자가 더 효율적으로 작업할 수 있습니다. 자세한 내용은 새 소프트웨어 센터 사용자 가이드의 [여러 응용 프로그램 설치](/sccm/core/understand/software-center#install-multiple-applications)를 참조하세요.

### <a name="use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices"></a>소프트웨어 센터를 사용하여 Azure AD 조인 장치에서 사용자가 사용할 수 있는 응용 프로그램 찾아보기 및 설치
<!-- 1322613 -->
사용자가 사용할 수 있는 응용 프로그램으로 배포하는 경우 이제 Azure AD(Azure Active Directory) 장치에서 소프트웨어 센터를 통해 해당 응용 프로그램을 찾아보고 설치할 수 있습니다. 자세한 내용은 [Azure AD 가입 장치에 사용자가 사용할 수 있는 응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)를 참조하세요.

### <a name="hide-installed-applications-in-software-center"></a>소프트웨어 센터에서 설치된 응용 프로그램 숨기기
<!--1357592-->
이제 설치된 응용 프로그램을 소프트웨어 센터에서 숨길 수 있습니다. 클라이언트 설정에서 이 옵션을 사용하도록 설정하면 이미 설치된 응용 프로그램이 더 이상 응용 프로그램 탭에 표시되지 않습니다. 이 옵션은 Configuration Manager 1802를 설치하거나 이 버전으로 업그레이드할 때 기본값으로 설정됩니다.  설치 상태 탭에서는 설치된 응용 프로그램을 계속 검토할 수 있습니다. [소프트웨어 센터에서 설치된 응용 프로그램 숨기기](/sccm/core/clients/deploy/about-client-settings#BKMK_HideInstalled)에는 추가적인 세부 정보가 있습니다.   

### <a name="hide-unapproved-applications-in-software-center"></a>소프트웨어 센터에서 승인되지 않은 프로그램 숨기기
 <!--1355146-->
이 클라이언트 설정 옵션을 용하도록 설정하면 승인이 필요한 사용자가 사용할 수 있는 응용 프로그램이 소프트웨어 센터에서 숨겨집니다.  [소프트웨어 센터에서 승인되지 않은 프로그램 숨기기](/sccm/core/clients/deploy/about-client-settings#BKMK_HideUnapproved)에는 추가적인 세부 정보가 있습니다.  

### <a name="software-center-shows-user-additional-compliance-information"></a>소프트웨어 센터에서 사용자에게 추가 준수 정보 표시
<!-- 1235616 -->
 장치 상태 증명 상태를 회사 리소스 조건부 액세스에 대한 준수 정책 규칙으로 사용하는 경우, Software Center에서 사용자에게 호환되지 않는 장치 상태 증명 설정을 표시합니다.


 ## <a name="software-updates"></a>소프트웨어 업데이트 

### <a name="schedule-automatic-deployment-rule-evaluation-to-be-offset-from-a-base-day"></a>자동 배포 규칙 평가가 기본 일에서 오프셋되도록 예약됩니다. 
<!--1357133-->
자동 배포 규칙은 기본 일로부터의 오프셋을 평가하도록 예약할 수 있습니다. 즉, 화요일의 패치가 실제로 수요일에 있는 경우 평가 일정은 1일 간격으로 오프셋된 월의 두 번째 화요일에 대해 설정할 수 있습니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates#BKMK_CreateAutomaticDeploymentRule)를 참조하세요. 



## <a name="reporting"></a>보고

### <a name="report-for-default-browser-counts"></a>기본 브라우저 개수에 대한 보고서
<!-- 1357830 -->
이제 특정 웹 브라우저를 Windows 기본값으로 사용하는 클라이언트 수를 표시하는 새 보고서가 있습니다. **소프트웨어 - 회사 및 제품** 보고서 그룹의 **기본 브라우저 수** 보고서를 참조하세요. 자세한 내용은 [보고서 목록](/sccm/core/servers/manage/list-of-reports#software---companies-and-products)을 참조하세요.

### <a name="report-on-windows-autopilot-device-information"></a>Windows AutoPilot 장치 정보에 대한 보고서
<!-- 1351442 -->
Windows AutoPilot은 새로운 Windows 10 장치를 최신 방법으로 온보딩 및 구성하기 위한 솔루션입니다. 자세한 내용은 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)를 참조하세요. 기존 장치를 Windows AutoPilot에 등록하는 한 가지 방법은 비즈니스 및 교육용 Microsoft 스토어에 장치 정보를 업로드하는 것입니다. 이 정보에는 장치 일련 번호, Windows 제품 식별자 및 하드웨어 식별자가 포함됩니다. Configuration Manager를 사용하여 **하드웨어 - 일반** 보고서 노드에 있는 새로운 **Windows AutoPilot 장치 정보** 보고서를 통해 이 장치 정보를 수집하고 보고합니다. 자세한 내용은 '공동 관리를 위한 준비'의 [새 Windows 10 장치](/sccm/core/clients/manage/co-management-prepare#new-windows-10-devices)를 참조하세요.

### <a name="report-on-windows-10-servicing-details-for-a-specific-collection"></a>특정 컬렉션에 대한 Windows 10 서비스 세부 정보 보고서
<!--1357653-->
**특정 컬렉션에 대한 Windows 10 서비스 세부 정보** 보고서는 특정 컬렉션에 대한 Windows 10 서비스와 관련된 일반 정보를 표시합니다. 이 보고서에는 Windows 10 장치의 리소스 ID, NetBIOS 이름, OS 이름, OS 릴리스 이름, 빌드, OS 분기 및 서비스 상태가 표시됩니다. 자세한 내용은 [보고서 목록](/sccm/core/servers/manage/list-of-reports#operating-system)을 참조하세요.



<!-- ## Inventory  -->



<!-- ## Mobile device management -->



 ## <a name="protect-devices"></a>장치 보호

### <a name="improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard"></a>Windows Defender Exploit Guard에 대한 Configuration Manager 정책 개선 사항
<!-- 1356220 -->
[Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)에 대한 Configuration Manager에 [공격 노출 영역 축소](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy#BKMK_ASR) 및 [제어된 폴더 액세스](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy#BKMK_CFA) 구성 요소에 대한 추가 정책 설정이 추가되었습니다.

### <a name="new-host-interaction-settings-for-windows-defender-application-guard"></a>Windows Defender Application Guard에 대한 새 호스트 상호 작용 설정
<!-- 1356256 -->
Windows 10 1709 버전 이상이 설치된 장치에는 [Windows Defender Application Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy#BKMK_HIS)에 대한 새로운 두 가지 호스트 상호 작용 설정이 있습니다. 
- 호스트의 가상 그래픽 프로세서에 대한 액세스 권한을 웹 사이트에 부여할 수 있습니다. 
- 컨테이너 내부에 다운로드한 파일을 호스트에 유지할 수 있습니다. 




## <a name="configuration-manager-console"></a>Configuration Manager 콘솔

### <a name="improvements-to-the-configuration-manager-console"></a>Configuration Manager 콘솔에 대한 향상된 기능 
이 릴리스에서 Configuration Manager 콘솔에 포함된 향상된 기능은 다음과 같습니다.
- [자산 및 호환성], [장치] 아래의 [장치] 목록에는 이제 기본적으로 기본 사용자가 표시됩니다. 이 열은 [장치] 노드에만 표시됩니다. 마지막으로 로그온한 사용자도 선택적 열로 추가될 수 있습니다.<!-- 1357280 --> 사이트에 대한 [사용자 및 장치 선호도](/sccm/core/clients/deploy/about-client-settings#user-and-device-affinity) 클라이언트 설정을 사용하도록 설정하여 기본 사용자를 장치와 연결합니다.
- 컬렉션이 다른 컬렉션의 멤버이고 이름이 변경되면 멤버 자격 규칙에 따라 새 이름이 업데이트됩니다.<!--1357282--> 
- 서로 다른 DPI 배율의 여러 모니터가 있는 클라이언트에서 원격 제어를 사용하는 경우 이제 마우스 커서가 서로 정확하게 매핑됩니다. <!--433170-->
- 그래프 섹션을 선택하면 [Office 365 클라이언트 관리 대시보드](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)에 관련 장치의 목록이 표시됩니다. <!--1357281 --> 



## <a name="next-steps"></a>다음 단계
이 버전을 설치할 준비가 되었으면 [Configuration Manager 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.
