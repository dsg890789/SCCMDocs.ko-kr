---
title: 기술 미리 보기 릴리스
titleSuffix: Configuration Manager
description: Configuration Manager에서 새로운 기능과 기술을 시험 사용할 수 있는 기술 미리 보기 분기를 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b60ebcf0ce94dfdc25466b31c9a64d0d556e1ac6
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385391"
---
# <a name="technical-preview-for-configuration-manager"></a>Configuration Manager용 기술 미리 보기

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 Configuration Manager의 월간 기술 미리 보기 분기를 자세히 설명합니다. 기술 미리 보기에서는 Microsoft가 작업하고 있는 새로운 기능을 소개합니다. Configuration Manager의 현재 분기에 아직 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능은 최종적으로 현재 분기에 대한 업데이트에 포함될 수 있습니다. 기능을 마무리하기 전에 기능을 사용해 보고 피드백을 보내 주시기 바랍니다.  

이 릴리스는 기술적인 미리 보기이므로 세부 사항 및 기능은 변경될 수 있습니다.  

이 정보는 Configuration Manager 기술 미리 보기 분기의 모든 버전에 적용됩니다. 이 문서에서는 먼저 나타나는 기술 미리 보기 버전과 함께 각 새로운 기능을 나열합니다. 예를 들면 2018년(18) 6월(06)에 대한 **1806**입니다. 각 미리 보기 버전에 전용으로 제공되는 개별 문서에서 개별 기능을 자세히 설명합니다.  

Configuration Manager *현재 분기*의 새로운 기능에 대한 자세한 내용은 [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)을 참조하세요.



##  <a name="bkmk_reqs"></a> 요구 사항 및 제한 사항  

> [!IMPORTANT]     
>  기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다. Microsoft에서 지원 서비스를 제공하지 않을 수 있으며, 특정 기능은 미리 보기 소프트웨어에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 미리 보기 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

대다수 제품 필수 구성 요소의 경우에는 [지원되는 구성](/sccm/core/plan-design/configs/supported-configurations)의 정보를 사용합니다. 기술 미리 보기 분기에는 다음 예외가 적용됩니다.  

-   각 설치는 90일 동안 활성화된 후에 비활성화됩니다.  

-   지원되는 언어는 영어뿐입니다.  

-   다음 설정 명령줄 매개 변수만 지원합니다.  
    -   `/silent`  
    -   `/testdbupgrade`    

-   서비스 연결점은 온라인 모드로 설치됩니다. 오프라인 모드는 지원하지 않습니다.  

-   특정 버전의 기술 문서에 대한 별도 문서에는 해당되는 추가 제한 사항 또는 요구 사항이 포함되어 있습니다.

-   다음 기능은 기술 미리 보기 분기에서 지원되지 않습니다.  

    - 이 미리 보기 분기에서 또는 이 미리 보기 분기로 [마이그레이션](/sccm/core/migration/migrate-data-between-hierarchies).  

    - 이 미리 보기 분기로 [업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).  

    - cd.latest 폴더의 [사이트 복구](/sccm/core/servers/manage/recover-sites).  <!--507106-->

-   이 미리 보기 분기에서 현재 분기로 업데이트하는 기능은 지원되지 않습니다.  

    > [!Note]  
    > 미리 보기 버전용 업데이트를 사용할 수 있는 경우 Configuration Manager 콘솔의 **업데이트 및 서비스** 노드에서 해당 업데이트를 찾아 설치합니다. 콘솔 내 업그레이드 프로세스에 대한 비디오를 보려면 youtube.com에서 [Installing Configuration Manager update packages](https://www.youtube.com/embed/KBd_EGFbUT8)(Configuration Manager 업데이트 패키지 설치)를 참조하세요.  

-   독립 실행형 기본 사이트만 지원합니다. 중앙 관리 사이트, 여러 기본 사이트 또는 보조 사이트는 지원되지 않습니다.  

Configuration Manager의 기술 미리 보기 분기는 다음 제품 및 기술을 지원합니다. 

-   다음 버전의 **SQL Server**만 지원합니다.  

    -   Configuration Manager 버전 1710에서 시작하는 SQL Server 2017(누적 업데이트 2 이상)
    -   SQL Server 2016(서비스 팩 없음 버전 이상)
    -   SQL Server 2014(서비스 팩 1 이상)
    -   SQL Server 2012(서비스 팩 3 이상)  


-   사이트는 최대 10개 클라이언트를 지원하며, 이러한 클라이언트는 다음 버전의 Windows 중 하나를 실행해야 합니다.  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 7  

> [!Note]  
> 이러한 제품이 이 내용에 포함되었다고 해서 해당 지원 주기가 끝난 버전의 지원 연장을 의미하지는 않습니다. Configuration Manager는 지원 주기가 끝난 제품은 지원하지 않습니다. 자세한 내용은 [Microsoft Lifecycle 정책](https://go.microsoft.com/fwlink/p/?LinkId=208270)을 참조하세요.  



##  <a name="bkmk_install"></a> 설치 및 업데이트  

랩 사용에 대한 Configuration Manager 기술 미리 보기 분기는 프로덕션 사용에 대한 Configuration Manager 현재 분기와 다릅니다.  

먼저 기술 미리 보기 분기의 기준 버전을 설치합니다. 기준 버전을 설치한 후 콘솔 내 업데이트를 사용하여 최근의 미리 보기 버전으로 설치를 업데이트합니다. 일반적으로 새 버전의 기술 미리 보기는 매달 사용할 수 있습니다.

Microsoft는 세 개의 연속 버전을 사용할 수 있을 때까지 각 기술 미리 보기 버전을 지원합니다. 예를 들어 버전 1708이 릴리스되면 버전 1704는 더 이상 지원되지 않습니다. 버전 1705, 1706 및 1707은 계속 지원됩니다. 기준 버전이 지원되지 않는 경우에도 지원되는 버전으로 즉시 업데이트한다고 가정하여 새 기술 미리 보기 사이트를 설치할 수 있습니다. 새 기준 버전을 사용할 수 있을 때까지 이전 기준 버전이 지원됩니다. 기준 버전에서 사용 가능한 최신 버전으로 업데이트하고 나서, 최신 기술 미리 보기 버전을 설치할 때까지 업데이트 프로세스를 반복합니다.

> [!TIP]  
>  기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다. 기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하는 옵션이 없습니다. 또한 현재 분기 릴리스의 업데이트를 받을 수 없습니다. 
> 
> 한 해에 여러 번, 동일한 버전 번호를 가진 기술 미리 보기 분기 및 현재 분기 버전이 있습니다. 예를 들면 Technical Preview 버전 1802 및 현재 분기 버전 1802입니다. 


### <a name="active-baseline-versions"></a>활성 기준 버전
   
릴리스 후 최대 1년 동안 기준 버전을 설치합니다. 새 기술 미리 보기 사이트를 설치할 때 현재 둘 이상의 기준 버전을 사용할 수 있는 경우 최신 기준 버전을 사용합니다.

-  **Technical Preview 버전 1806**: Configuration Manager Technical Preview 버전 1806은 콘솔 내 업데이트와 새로운 기준 버전으로 모두 제공됩니다. [TechNet 평가 센터에서](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 기준 버전을 다운로드합니다.



##  <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  

기술 미리 보기의 새로운 기능에 대한 피드백을 보내 주시기 바랍니다. 자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#product-feedback)을 참조하세요.

새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 제출하고 다른 사용자가 제출한 아이디어에 투표하려면 [UserVoice 페이지](https://configurationmanager.uservoice.com)를 방문하세요.  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->



##  <a name="bkmk_tpCaps"></a> 최신 버전의 기능  

다음 기능은 최신 Configuration Manager 기술 미리 보기 버전에서 사용할 수 있습니다. 

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1807"></a>Technical Preview 버전 1807

- [커뮤니티 허브](capabilities-in-technical-preview-1807.md#bkmk_hub) <!--1357766-->
- [오프라인 OS 이미지 서비스용 드라이브 지정](capabilities-in-technical-preview-1807.md#bkmk_osd) <!--1358924-->
- [Intune에서 공동 관리되는 장치 동기화 작업](capabilities-in-technical-preview-1807.md#bkmk_comgmt) <!--1358565-->
- [응용 프로그램 복구](capabilities-in-technical-preview-1807.md#bkmk_app-repair) <!--1357866-->
- [메일을 통해 응용 프로그램 요청 승인](capabilities-in-technical-preview-1807.md#bkmk_email-approve) <!--1321550-->
- [스크립트 출력 개선 사항](capabilities-in-technical-preview-1807.md#bkmk_script) <!--1236459-->
- [타사 소프트웨어 업데이트 개선 사항](capabilities-in-technical-preview-1807.md#bkmk_3pupdate) <!--1358714-->


> [!Note]  
> 이전 버전의 기술 미리 보기에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로 Configuration Manager 현재 분기에 추가된 기능은 기술 미리 보기 분기에서 계속 사용할 수 있습니다.   



## <a name="features-in-recent-supported-technical-previews"></a>최근 지원되는 기술 미리 보기의 기능

다음 기능은 계속 지원되는 이전 버전의 Configuration Manager 기술 미리 보기 분기와 함께 릴리스되었습니다. 

<!-- This is the full list of new features in the past THREE (3) TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 |기능 |기술 미리 보기 버전 |현재 분기 버전|  
 |----------------|---------------------|--------------------|
 | 단계적 배포 개선 사항 <!--1358577,1358147,1358578--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_pod)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 새로운 Windows 앱 패키지 형식에 대한 지원 <!--1357427--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_msix)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 클라이언트 강제 보안 개선 사항 <!--1358204--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_client-push)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 자동 유지 관리에 대한 관리 인사이트 <!--1352184,et al--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_insights)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 공동 관리하는 장치에 대한 모바일 앱 워크로드 전환 <!--1357892--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_comgmt)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 피어 다운로드를 위한 경계 그룹 옵션 <!--1356193--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_bgoptions)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 사용자 지정 카탈로그에 대한 타사 소프트웨어 업데이트 지원 <!--1358714--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_3pupdate)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 클라우드 관리 기능 개선 사항 <!--511980,515854--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_cloud)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 새 소프트웨어 업데이트 준수 보고서 <!--1357775--> | [Tech Preview 1806.2](capabilities-in-technical-preview-1806-2.md#bkmk_report)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 타사 소프트웨어 업데이트 <!--1352101--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#bkmk-3pupdate)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Microsoft Edge용 Windows Defender SmartScreen 설정 구성 <!--1353701--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#configure-windows-defender-smartscreen-settings-for-microsoft-edge)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Microsoft Intune에서 공동 관리하는 장치에 대한 MDM 정책 동기화 <!--1357377--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#sync-mdm-policy-from-microsoft-intune-for-a-co-managed-device)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 공동 관리를 사용하여 Office 365 워크로드를 Intune으로 전환 <!--1357841--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#transition-office-365-workload-to-intune-using-co-management)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Package Conversion Manager <!--1357861--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#package-conversion-manager)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 콘텐츠 없이 소프트웨어 업데이트 배포 <!--1357933--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#deploy-software-updates-without-content)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Office 365 설치 관리자와 Office 사용자 지정 도구 통합 <!--1358149--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#office-customization-tool-integration-with-the-office-365-installer)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 클라우드 관리 게이트웨이의 향상된 기능 <!--1358215,1358651,503899--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#improvements-to-cloud-management-gateway)   | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 보안 클라이언트 통신 개선 <!--1358278,1358279--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#improvements-to-secure-client-communications)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 소프트웨어 센터 인프라 개선 사항 <!--1358309--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#software-center-infrastructure-improvements)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 장치의 모든 사용자에 대해 Windows 앱 패키지 프로비전 <!--1358310--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#provision-windows-app-packages-for-all-users-on-a-device)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Surface 대시보드에 대한 개선 사항 <!--1358654--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#improvements-to-the-surface-dashboard)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 하드웨어 인벤토리 기본 단위 수정 버전 <!--514442--> | [Tech Preview 1806](capabilities-in-technical-preview-1806.md#hardware-inventory-default-unit-revision)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 작업 순서에 대해 수동으로 구성된 단계를 사용하여 단계적 배포 만들기 <!--1358148--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#create-a-phased-deployment-with-manually-configured-phases-for-a-task-sequence)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Azure Resource Manager에 대한 클라우드 배포 지점 지원 <!--1322209--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cloud-distribution-point-support-for-azure-resource-manager)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 관리 인사이트를 기반으로 작업 수행 <!--1357930--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#take-actions-based-on-management-insights)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 공동 관리를 사용하여 장치 구성 워크로드를 Intune으로 전환 <!--1357903--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#transition-device-configuration-workload-to-intune-using-co-management)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 배포 지점에서 네트워크 정체 제어를 사용하도록 설정 <!--1358112--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#enable-distribution-points-to-use-network-congestion-control)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 클라우드 관리 대시보드 <!--1358461--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cloud-management-dashboard)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | CMPivot <!--1358456--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cmpivot)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 개선된 보안 클라이언트 통신 <!--1356889,1358228,1358460--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improved-secure-client-communications)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 타사 소프트웨어 업데이트 지원에 대한 개선 사항 <!--1357605--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-for-enabling-third-party-software-update-support)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 향상된 Windows 10 전체 업그레이드 작업 순서 <!--1358500--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-to-windows-10-in-place-upgrade-task-sequence)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | CMTrace가 클라이언트와 함께 설치됨 <!--1357971--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#cmtrace-installed-with-client)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | Configuration Manager 콘솔 개선 사항 <!--1358202--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-the-configuration-manager-console)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 콘솔 피드백 개선 사항 <!--1357542--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-to-console-feedback)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 향상된 PXE 사용 배포 지점 <!--1357580--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvements-to-pxe-enabled-distribution-points)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 큰 정수 값에 대한 하드웨어 인벤토리 개선 사항 <!--1357880--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-hardware-inventory-for-large-integer-values)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | WSUS 유지 관리 개선 사항 <!--1357898--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-wsus-maintenance)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | CNG 인증서 지원 개선 사항 <!--1357314--> | [Tech Preview 1805](capabilities-in-technical-preview-1805.md#improvement-to-support-for-cng-certificates)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) |  
 | 사이트 서버에 대해 원격 콘텐츠 라이브러리 구성 <!--1357525--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#configure-a-remote-content-library-for-the-site-server)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | Configuration Manager 콘솔에서 피드백 제출 <!--1357542--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#bkmk_feedback)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 지원 센터 <!--1357489--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#support-center)  | ![추가되지 않음](media/Red_X.gif) | 
 | Configuration Manager Toolkit <!--1357145--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#configuration-manager-toolkit)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 승인 취소 시 응용 프로그램 제거 <!--1357891--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#uninstall-application-on-approval-revocation)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 검색에서 Active Directory 컨테이너 제외 <!--1358143--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#exclude-active-directory-containers-from-discovery)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 소프트웨어 센터에서 응용 프로그램 카탈로그 웹 사이트 링크의 표시 여부 지정 <!--1358214--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#specify-the-visibility-of-the-application-catalog-website-link-in-software-center)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 소프트웨어 업데이트 아키텍처를 기준으로 자동 배포 규칙 필터링 <!--1322266--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#filter-automatic-deployment-rules-by-software-update-architecture)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 향상된 OS 배포 <!--1358330,1358493--> | [Tech Preview 1804](capabilities-in-technical-preview-1804.md#improvements-to-os-deployment) | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 풀(pull) 배포 지점은 클라우드 배포 지점을 원본으로 지원함 <!--1321554--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#pull-distribution-points-support-cloud-distribution-points-as-source)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | WAN 사용률을 줄이기 위해 클라이언트 피어 캐시에서 부분 다운로드 지원 <!--1357346--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#partial-download-support-in-client-peer-cache-to-reduce-wan-utilization)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 소프트웨어 센터의 유지 관리 기간 <!--1358131--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#maintenance-windows-in-software-center)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 소프트웨어 센터의 웹 페이지용 사용자 지정 탭 <!--1358132--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#custom-tab-for-webpage-in-software-center)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 클라이언트에서 타사 소프트웨어 업데이트 지원 사용 <!--1357605--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#enable-third-party-software-update-support-on-clients)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | 모니터링 보기에서 자산 정보의 복사/붙여넣기 사용 <!--1357552--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#enable-copypaste-of-asset-details-from-monitoring-views)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 | SCAP 확장 <!--1357552--> | [Tech Preview 1803](capabilities-in-technical-preview-1803.md#scap-extensions)  | [버전 1806](/sccm/core/plan-design/changes/whats-new-in-version-1806) | 
 
  

## <a name="features-in-previous-technical-previews"></a>이전 기술 미리 보기의 기능

다음 기능은 이전 버전의 Configuration Manager 기술 미리 보기 분기와 함께 릴리스되었습니다. 이러한 기능은 이후 버전에서 사용할 수 있지만 현재 분기에서는 제공되지 않습니다. 

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

|기능 |기술 미리 보기 버전 |  
|----------------|---------------------|
| 클라이언트 기반 PXE 응답자 서비스 <!-- 1357148 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service) |
|IPv6에 대한 PXE 네트워크 부팅 지원<!-- 1269793 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
|Azure Active Directory 사용 <!-- 1322145? --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
|Windows Update for Business 업데이트에 대한 준수 평가<!-- 1235390 --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |
|OData 끝점 데이터 액세스<!-- 1321523 --> |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|
|Asset Intelligence 개선 <!-- 1307390 --> |[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|
|최종 사용자가 회사 포털에서 앱을 설치할 수 있습니다.<!-- 1037233? --> |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|

<!--Removed for 1806 CB:
 |Site server role high availability <!-- 1128774  |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |
 | Product lifecycle dashboard <!--1319632  | [Tech Preview 1802](capabilities-in-technical-preview-1802.md#product-lifecycle-dashboard) | 
 | Improvements to PXE-enabled distribution points <!-- 1357580  | [Tech Preview 1802](capabilities-in-technical-preview-1802.md#improvements-to-pxe-enabled-distribution-points) | 
-->



## <a name="see-also"></a>참고 항목  

자세한 내용은 다음 아티클을 참조하세요.  

- [랩에서 Configuration Manager 평가](/sccm/core/get-started/evaluate-with-lab-environment)
- [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
- [Configuration Manager 소개](/sccm/core/understand/introduction)

> [!Tip]  
> 사용하려면 동의가 필요한 현재 분기 기능에 대한 자세한 내용은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  
> 
> 먼저 사용하도록 설정해야 하는 현재 분기 기능에 대한 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  
