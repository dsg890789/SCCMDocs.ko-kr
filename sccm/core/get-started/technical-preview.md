---
title: 기술 미리 보기 릴리스
titleSuffix: Configuration Manager
description: Configuration Manager에서 새로운 기능과 기술을 테스트할 수 있는 기술 미리 보기 릴리스에 대해 알아봅니다.
ms.date: 06/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1fd848c3e0ed663e0731eb86d39c930db3af7819
ms.sourcegitcommit: d1bf26bcf0d78b37ac7598fab36eb58ca69b1dc5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37066286"
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>System Center Configuration Manager Technical Preview

*적용 대상: System Center Configuration Manager(Technical Preview)*

**System Center Configuration Manager Technical Preview 시작**. 이 문서에서는 현재 작업 중인 새로운 기능을 소개하는 개발 중인 미리 보기 릴리스에 대해 자세히 다룹니다. 각 버전의 Technical Preview에서는 Technical Preview 버전이 사용 가능한 시점에서 현재 분기의 Configuration Manager에 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능이 결과적으로 현재 분기 버전의 업데이트에 포함될 수도 있지만, 기능을 완료하고 추가하기 전에 사용자가 사용해 보고 의견을 제공하는 기회를 갖길 원합니다.  

 이 릴리스는 기술적인 미리 보기이므로 세부 사항 및 기능은 변경될 수 있습니다.  

 이 문서는 모든 버전의 Technical Preview에 적용되는 정보를 포함합니다. 또한 2018년 6월의 1806 버전처럼, 기능이 가장 먼저 제공되는 Technical Preview 버전과 함께 새로운 각 기능을 설명합니다. 이러한 기능은 각 미리 보기 버전만을 다룬 별도 항목에서 자세히 설명합니다.  

 현재 분기의 Configuration Manager에서 제공하는 새로운 기능에 대한 자세한 내용은 [System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012)을 참조하세요.



##  <a name="bkmk_reqs"></a> Technical Preview의 요구 사항 및 제한  

> [!IMPORTANT]     
>  기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다. Microsoft에서 지원 서비스를 제공하지 않을수 있으며, 특정 기능은 미리 보기 소프트웨어에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 미리 보기 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

 대부분의 제품 필수 조건에 대한 자세한 내용은 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md)의 정보를 참조하세요. 기술 미리 보기 릴리스에는 다음과 같은 예외가 적용됩니다.  

-   각 설치는 90일 동안 활성 상태로 유지된 후에 비활성화됩니다.  

-   지원되는 언어는 영어뿐입니다.


-   다음 설치 플래그(스위치)만 지원됩니다.  

    -   **/silent**  
    -   **/testdbupgrade**    


-   기본적으로 Technical Preview를 사용하는 경우 서비스 연결 지점이 온라인 모드로 설치됩니다. 오프라인 모드로 변경되도록 지원하지 않습니다.

-   특정 버전의 기술 문서에 대한 별도 문서에는 해당되는 추가 제한 사항 또는 요구 사항이 포함되어 있습니다.

-   이 미리 보기 빌드에서/빌드로 마이그레이션할 수는 없습니다.  

-   이 미리 보기 빌드로 업그레이드할 수는 없습니다. 

-   cd.latest 폴더에서의 사이트 복구는 지원되지 않습니다.  <!--507106-->

-   이 미리 보기 빌드에서 프로덕션 빌드(현재 분기)로 업그레이드할 수 없습니다. 그러나 미리 보기 버전용 업데이트를 사용할 수 있는 경우 Configuration Manager 콘솔의 **업데이트 및 서비스** 노드에서 해당 업데이트를 찾아 설치할 수 있습니다. 콘솔 내 업그레이드 프로세스에 대한 비디오를 보려면 youtube.com에서 [ConfigMgr 업데이트 패키지 설치](https://www.youtube.com/embed/KBd_EGFbUT8) (영문)를 참조하세요.  
-   독립 실행형 기본 사이트만 지원됩니다. 중앙 관리 사이트, 여러 기본 사이트 또는 보조 사이트는 지원되지 않습니다.  

다음 제품 및 기술은 이 Configuration Manager 분기에서 지원됩니다. 그러나 이 내용에 포함되었다고 해서 개별 지원 주기가 끝난 제품 또는 버전의 지원 연장을 의미하지는 않습니다. 즉, 지원 주기가 끝난 제품은 Configuration Manager에서 사용할 수 없습니다. Microsoft 지원 주기에 대한 자세한 내용은 [Microsoft 지원 주기](https://go.microsoft.com/fwlink/p/?LinkId=208270) 웹 사이트를 참조하세요.  

-   다음 SQL Server 버전만 지원됩니다.  

    -   Configuration Manager 버전 1710에서 시작하는 SQL Server 2017(누적 업데이트 2 이상)
    -   SQL Server 2016(서비스 팩 없음 버전 이상)
    -   SQL Server 2014(서비스 팩 1 이상)
    -   SQL Server 2012(서비스 팩 3 이상)


-   사이트는 최대 10개 클라이언트를 지원하며, 이러한 클라이언트는 다음 버전의 Windows 중 하나를 실행해야 합니다.  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 7  

##  <a name="bkmk_install"></a> 기술 미리 보기 설치 및 업데이트  
 System Center Configuration Manager Technical Preview는 현재 릴리스의 System Center Configuration Manager와 다릅니다.  

 Technical Preview를 사용하려면 먼저 Technical Preview 빌드의 **기준 버전**을 설치해야 합니다. 기준선 버전을 설치한 후 **콘솔 내 업데이트**를 사용하여 최근의 미리 보기 버전으로 설치를 업데이트할 수 있습니다. 일반적으로 새 버전의 기술 미리 보기는 매달 사용할 수 있습니다.

세 가지 후속 릴리스를 사용할 수 있을 때까지 각 미리 보기 릴리스가 지원됩니다. 즉, 버전 1708이 출시되면 버전 1704는 더 이상 지원되지 않지만 버전 1705, 1706 및 1707은 계속 지원됩니다. 기준 버전이 지원되지 않는 경우에도 해당 설치를 지원되는 버전으로 업데이트하는 한 새 기준 버전을 사용할 수 있을 때까지 새 Technical Preview 사이트를 설치할 수 있습니다. 사용 가능한 최신 버전을 업데이트하고, 최신 버전의 Technical Preview를 설치할 수 있을 때까지 해당 프로세스를 반복합니다.

> [!TIP]  
>  기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다. 기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하거나 현재 분기 릴리스의 업데이트를 받을 수 있는 옵션이 없습니다.  

**기술 미리 보기의 활성 기준선 버전:**
   
릴리스 후 최대 1년 동안 기준 버전을 설치할 수 있습니다. 그러나 새 Technical Preview 사이트를 설치할 경우 사용 가능한 최신 기준선 버전을 사용하는 것이 좋습니다.
-  **Technical Preview 1806** - Configuration Manager Technical Preview 1806는 콘솔 내 업데이트와 새로운 기준 버전으로 모두 제공됩니다. [TechNet 평가 센터에서](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 기준 버전을 다운로드합니다.


##  <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  
 Technical Preview의 기능에 대한 피드백을 보내 주시기 바랍니다. 자세한 내용은 [제품 피드백](../understand/find-help.md#product-feedback)을 참조하세요.

새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 전송하고 다른 사용자들이 전송한 아이디어에 대해 투표를 하려면 [사용자 의견 페이지를 방문](https://configurationmanager.uservoice.com)하세요.  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> 가장 최근의 Technical Preview에 포함된 기능  
최신 Configuration Manager Technical Preview 릴리스에 포함된 기능은 다음과 같습니다. 이전 버전의 Technical Preview에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로, Configuration Manager 현재 분기에 추가된 기능은 Technical Preview 릴리스에서도 계속 사용할 수 있습니다. 각 미리 보기 버전에 대한 콘텐츠를 클릭하여 특정 기능에 대한 자세한 내용을 알아볼 수 있습니다.  

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-18062"></a>Technical Preview 버전 1806.2
- [단계적 배포 개선 사항](capabilities-in-technical-preview-1806-2.md#bkmk_pod) <!--1358577,1358147,1358578-->
- [새로운 Windows 앱 패키지 형식에 대한 지원](capabilities-in-technical-preview-1806-2.md#bkmk_msix) <!--1357427-->
- [클라이언트 강제 보안 개선 사항](capabilities-in-technical-preview-1806-2.md#bkmk_client-push) <!--1358204-->
- [자동 유지 관리에 대한 관리 인사이트](capabilities-in-technical-preview-1806-2.md#bkmk_insights) <!--1352184,et al-->
- [공동 관리하는 장치에 대한 모바일 앱 워크로드 전환](capabilities-in-technical-preview-1806-2.md#bkmk_comgmt) <!--1357892-->
- [피어 다운로드를 위한 경계 그룹 옵션](capabilities-in-technical-preview-1806-2.md#bkmk_bgoptions) <!--1356193-->
- [사용자 지정 카탈로그에 대한 타사 소프트웨어 업데이트 지원](capabilities-in-technical-preview-1806-2.md#bkmk_3pupdate) <!--1358714-->
- [클라우드 관리 기능 개선 사항](capabilities-in-technical-preview-1806-2.md#bkmk_cloud) <!--511980,515854-->
- [새 소프트웨어 업데이트 준수 보고서](capabilities-in-technical-preview-1806-2.md#bkmk_report) <!--1357775-->



## <a name="capabilities-delivered-in-recent-supported-technical-previews"></a>최근 지원되는 Technical Preview에 포함된 기능
이전 버전의 Configuration Manager Technical Preview 릴리스에 포함되어 여전히 지원되는 기능은 다음과 같습니다. 

<!-- This is the full list of new features in the past THREE (3) TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 |기능 |기술 미리 보기 버전 |현재 분기 버전|  
 |----------------|---------------------|--------------------|
 | 타사 소프트웨어 업데이트 <!--1352101--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#bkmk-3pupdate)  | ![추가되지 않음](media/Red_X.gif) |  
 | Microsoft Edge용 Windows Defender SmartScreen 설정 구성 <!--1353701--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#configure-windows-defender-smartscreen-settings-for-microsoft-edge)  | ![추가되지 않음](media/Red_X.gif) |  
 | Microsoft Intune에서 공동 관리하는 장치에 대한 MDM 정책 동기화 <!--1357377--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#sync-mdm-policy-from-microsoft-intune-for-a-co-managed-device)  | ![추가되지 않음](media/Red_X.gif) |  
 | 공동 관리를 사용하여 Office 365 워크로드를 Intune으로 전환 <!--1357841--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#transition-office-365-workload-to-intune-using-co-management)  | ![추가되지 않음](media/Red_X.gif) |  
 | Package Conversion Manager <!--1357861--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#package-conversion-manager)  | ![추가되지 않음](media/Red_X.gif) |  
 | 콘텐츠 없이 소프트웨어 업데이트 배포 <!--1357933--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#deploy-software-updates-without-content)  | ![추가되지 않음](media/Red_X.gif) |  
 | Office 365 설치 관리자와 Office 사용자 지정 도구 통합 <!--1358149--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#office-customization-tool-integration-with-the-office-365-installer)  | ![추가되지 않음](media/Red_X.gif) |  
 | 클라우드 관리 게이트웨이의 향상된 기능 <!--1358215,1358651,503899--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#improvements-to-cloud-management-gateway)   | ![추가되지 않음](media/Red_X.gif) |  
 | 보안 클라이언트 통신 개선 <!--1358278,1358279--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#improvements-to-secure-client-communications)  | ![추가되지 않음](media/Red_X.gif) |  
 | 소프트웨어 센터 인프라 개선 사항 <!--1358309--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#software-center-infrastructure-improvements)  | ![추가되지 않음](media/Red_X.gif) |  
 | 장치의 모든 사용자에 대해 Windows 앱 패키지 프로비전 <!--1358310--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#provision-windows-app-packages-for-all-users-on-a-device)  | ![추가되지 않음](media/Red_X.gif) |  
 | Surface 대시보드에 대한 개선 사항 <!--1358654--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#improvements-to-the-surface-dashboard)  | ![추가되지 않음](media/Red_X.gif) |  
 | 하드웨어 인벤토리 기본 단위 수정 버전 <!--514442--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#hardware-inventory-default-unit-revision)  | ![추가되지 않음](media/Red_X.gif) |  
 | 작업 순서에 대해 수동으로 구성된 단계를 사용하여 단계적 배포 만들기 <!--1358148--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#create-a-phased-deployment-with-manually-configured-phases-for-a-task-sequence)  | ![추가되지 않음](media/Red_X.gif) |  
 | Azure Resource Manager에 대한 클라우드 배포 지점 지원 <!--1322209--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cloud-distribution-point-support-for-azure-resource-manager)  | ![추가되지 않음](media/Red_X.gif) |  
 | 관리 인사이트를 기반으로 작업 수행 <!--1357930--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#take-actions-based-on-management-insights)  | ![추가되지 않음](media/Red_X.gif) |  
 | 공동 관리를 사용하여 장치 구성 워크로드를 Intune으로 전환 <!--1357903--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#transition-device-configuration-workload-to-intune-using-co-management)  | ![추가되지 않음](media/Red_X.gif) |  
 | 배포 지점에서 네트워크 정체 제어를 사용하도록 설정 <!--1358112--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#enable-distribution-points-to-use-network-congestion-control)  | ![추가되지 않음](media/Red_X.gif) |  
 | 클라우드 관리 대시보드 <!--1358461--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cloud-management-dashboard)  | ![추가되지 않음](media/Red_X.gif) |  
 | CMPivot <!--1358456--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cmpivot)  | ![추가되지 않음](media/Red_X.gif) |  
 | 개선된 보안 클라이언트 통신 <!--1356889,1358228,1358460--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improved-secure-client-communications)  | ![추가되지 않음](media/Red_X.gif) |  
 | 타사 소프트웨어 업데이트 지원에 대한 개선 사항 <!--1357605--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-for-enabling-third-party-software-update-support)  | ![추가되지 않음](media/Red_X.gif) |  
 | 향상된 Windows 10 전체 업그레이드 작업 순서 <!--1358500--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-to-windows-10-in-place-upgrade-task-sequence)  | ![추가되지 않음](media/Red_X.gif) |  
 | CMTrace가 클라이언트와 함께 설치됨 <!--1357971--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cmtrace-installed-with-client)  | ![추가되지 않음](media/Red_X.gif) |  
 | Configuration Manager 콘솔 개선 사항 <!--1358202--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-the-configuration-manager-console)  | ![추가되지 않음](media/Red_X.gif) |  
 | 콘솔 피드백 개선 사항 <!--1357542--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-to-console-feedback)  | ![추가되지 않음](media/Red_X.gif) |  
 | 향상된 PXE 사용 배포 지점 <!--1357580--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-to-pxe-enabled-distribution-points)  | ![추가되지 않음](media/Red_X.gif) |  
 | 큰 정수 값에 대한 하드웨어 인벤토리 개선 사항 <!--1357880--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-hardware-inventory-for-large-integer-values)  | ![추가되지 않음](media/Red_X.gif) |  
 | WSUS 유지 관리 개선 사항 <!--1357898--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-wsus-maintenance)  | ![추가되지 않음](media/Red_X.gif) |  
 | CNG 인증서 지원 개선 사항 <!--1357314--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-support-for-cng-certificates)  | ![추가되지 않음](media/Red_X.gif) |  
| 사이트 서버에 대해 원격 콘텐츠 라이브러리 구성 <!--1357525--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#configure-a-remote-content-library-for-the-site-server)  | ![추가되지 않음](media/Red_X.gif) | 
 | Configuration Manager 콘솔에서 피드백 제출 <!--1357542--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#bkmk_feedback)  | ![추가되지 않음](media/Red_X.gif) | 
 | 지원 센터 <!--1357489--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#support-center)  | ![추가되지 않음](media/Red_X.gif) | 
 | Configuration Manager Toolkit <!--1357145--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#configuration-manager-toolkit)  | ![추가되지 않음](media/Red_X.gif) | 
 | 승인 취소 시 응용 프로그램 제거 <!--1357891--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#uninstall-application-on-approval-revocation)  | ![추가되지 않음](media/Red_X.gif) | 
 | 검색에서 Active Directory 컨테이너 제외 <!--1358143--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#exclude-active-directory-containers-from-discovery)  | ![추가되지 않음](media/Red_X.gif) | 
 | 소프트웨어 센터에서 응용 프로그램 카탈로그 웹 사이트 링크의 표시 여부 지정 <!--1358214--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#specify-the-visibility-of-the-application-catalog-website-link-in-software-center)  | ![추가되지 않음](media/Red_X.gif) | 
 | 소프트웨어 업데이트 아키텍처를 기준으로 자동 배포 규칙 필터링 <!--1322266--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#filter-automatic-deployment-rules-by-software-update-architecture)  | ![추가되지 않음](media/Red_X.gif) | 
 | 향상된 OS 배포 <!--1358330,1358493--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#improvements-to-os-deployment) | ![추가되지 않음](media/Red_X.gif) | 
 | 풀(pull) 배포 지점은 클라우드 배포 지점을 원본으로 지원함 <!--1321554--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#pull-distribution-points-support-cloud-distribution-points-as-source)  | ![추가되지 않음](media/Red_X.gif) | 
 | WAN 사용률을 줄이기 위해 클라이언트 피어 캐시에서 부분 다운로드 지원 <!--1357346--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#partial-download-support-in-client-peer-cache-to-reduce-wan-utilization)  | ![추가되지 않음](media/Red_X.gif) | 
 | 소프트웨어 센터의 유지 관리 기간 <!--1358131--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#maintenance-windows-in-software-center)  | ![추가되지 않음](media/Red_X.gif) | 
 | 소프트웨어 센터의 웹 페이지용 사용자 지정 탭 <!--1358132--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#custom-tab-for-webpage-in-software-center)  | ![추가되지 않음](media/Red_X.gif) | 
 | 클라이언트에서 타사 소프트웨어 업데이트 지원 사용 <!--1357605--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#enable-third-party-software-update-support-on-clients)  | ![추가되지 않음](media/Red_X.gif) | 
 | 모니터링 보기에서 자산 정보의 복사/붙여넣기 사용 <!--1357552--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#enable-copypaste-of-asset-details-from-monitoring-views)  | ![추가되지 않음](media/Red_X.gif) | 
 | SCAP 확장 <!--1357552--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#scap-extensions)  | ![추가되지 않음](media/Red_X.gif) | 
 
  

## <a name="capabilities-delivered-in-previous-technical-previews"></a>이전 Technical Preview에 포함된 기능
이전 버전의 Configuration Manager Technical Preview 릴리스에 포함된 특정 기능은 다음과 같습니다. 이러한 기능은 이후 버전에서 사용할 수 있지만 현재 분기 릴리스에서는 제공되지 않습니다. 

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

 |기능 |기술 미리 보기 버전 |  
 |----------------|---------------------|
 | 향상된 PXE 사용 배포 지점 <!-- 1357580 --> | [기술 미리 보기 1802](capabilities-in-technical-preview-1802.md#improvements-to-pxe-enabled-distribution-points) | 
 | 제품 수명 주기 대시보드 <!--1319632 --> | [기술 미리 보기 1802](capabilities-in-technical-preview-1802.md#product-lifecycle-dashboard) | 
 | 클라이언트 기반 PXE 응답자 서비스 <!-- 1357148 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service) |
 |사이트 서버 역할 고가용성<!-- 1128774 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |
 |IPv6에 대한 PXE 네트워크 부팅 지원<!-- 1269793 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
 |Azure Active Directory 사용 <!-- 1322145? --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
 |Windows Update for Business 업데이트에 대한 준수 평가<!-- 1235390 --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |
 |OData 끝점 데이터 액세스<!-- 1321523 --> |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|
 |Asset Intelligence 개선 <!-- 1307390 --> |[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|
 |최종 사용자가 회사 포털에서 앱을 설치할 수 있습니다.<!-- 1037233? --> |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|



## <a name="see-also"></a>참고 항목  
[System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [System Center Configuration Manager 소개](../../core/understand/introduction.md)

> [!Tip]  
> 사용하려면 동의가 필요한 현재 분기 기능에 대한 자세한 내용은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  
> 먼저 사용하도록 설정해야 하는 현재 분기 기능에 대한 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  

