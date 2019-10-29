---
title: 기술 미리 보기 릴리스
titleSuffix: Configuration Manager
description: Configuration Manager에서 새로운 기능과 기술을 시험 사용할 수 있는 기술 미리 보기 분기를 알아봅니다.
ms.date: 10/18/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 330a1a1b92a111836b49dcb0127b772d2c0cc636
ms.sourcegitcommit: 90f51008deeabf2a434bd12f81bb25669045029c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684803"
---
# <a name="technical-preview-for-configuration-manager"></a>Configuration Manager에 대한 기술 미리 보기

*적용 대상: System Center Configuration Manager(기술 미리 보기)*

이 문서에서는 Configuration Manager의 월간 기술 미리 보기 분기를 자세히 설명합니다. 기술 미리 보기에서는 Microsoft가 작업하고 있는 새로운 기능을 소개합니다. Configuration Manager의 현재 분기에 아직 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능은 최종적으로 현재 분기에 대한 업데이트에 포함될 수 있습니다. 기능을 마무리하기 전에 기능을 사용해 보고 피드백을 보내 주시기 바랍니다.  

이 릴리스는 기술적인 미리 보기이므로 세부 사항 및 기능은 변경될 수 있습니다.  

이 정보는 Configuration Manager 기술 미리 보기 분기의 모든 버전에 적용됩니다. 이 문서에서는 먼저 나타나는 기술 미리 보기 버전과 함께 각 새로운 기능을 나열합니다. 예를 들어, 2019(19)년 8월 8일의 경우 버전 **1908**입니다. 각 미리 보기 버전에 전용으로 제공되는 개별 문서에서 개별 기능을 자세히 설명합니다.  

Configuration Manager *현재 분기*의 새로운 기능에 대한 자세한 내용은 [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)을 참조하세요.

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22technical+preview+releases+-+Configuration+Manager%22&locale=en-us`

## <a name="bkmk_reqs"></a> 요구 사항 및 제한 사항  

> [!IMPORTANT]  
> 기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다. Microsoft에서 지원 서비스를 제공하지 않을 수 있으며, 특정 기능은 기술 미리 보기에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 기술 미리 보기 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

대다수 제품 필수 구성 요소의 경우에는 [지원되는 구성](/sccm/core/plan-design/configs/supported-configurations)의 정보를 사용합니다. 기술 미리 보기 분기에는 다음 예외가 적용됩니다.  

- 각 설치는 90일 동안 활성화된 후에 비활성화됩니다.  

- 지원되는 언어는 영어뿐입니다.  

- 다음 설정 명령줄 매개 변수만 지원합니다.  

    - `/silent`  
    - `/testdbupgrade`  

- 서비스 연결점은 온라인 모드로 설치됩니다. 오프라인 모드는 지원하지 않습니다.  

- 특정 버전의 기술 문서에 대한 별도 문서에는 해당되는 추가 제한 사항 또는 요구 사항이 포함되어 있습니다.

- 다음 기능은 기술 미리 보기 분기에서 지원되지 않습니다.  

    - 이 미리 보기 분기에서 또는 이 미리 보기 분기로 [마이그레이션](/sccm/core/migration/migrate-data-between-hierarchies).  

    - 이 미리 보기 분기로 [업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).  

    - cd.latest 폴더의 [사이트 복구](/sccm/core/servers/manage/recover-sites).  <!--507106-->

- 이 미리 보기 분기에서 현재 분기로 업데이트하는 기능은 지원되지 않습니다.  

    > [!Note]  
    > 미리 보기 버전용 업데이트를 사용할 수 있는 경우 Configuration Manager 콘솔의 **업데이트 및 서비스** 노드에서 해당 업데이트를 찾아 설치합니다. 콘솔 내 업그레이드 프로세스에 대한 비디오를 보려면 youtube.com에서 [Installing Configuration Manager update packages](https://www.youtube.com/embed/KBd_EGFbUT8)(Configuration Manager 업데이트 패키지 설치)를 참조하세요.  

- 독립 실행형 기본 사이트만 지원합니다. 중앙 관리 사이트, 여러 기본 사이트 또는 보조 사이트는 지원되지 않습니다.  

Configuration Manager의 기술 미리 보기 분기는 다음 제품 및 기술을 지원합니다.

- 다음 버전의 **SQL Server**만 지원합니다.  

    - SQL Server 2017(누적 업데이트 2 이상)
    - SQL Server 2016(서비스 팩 없음 버전 이상)
    - SQL Server 2014(서비스 팩 1 이상)
    - SQL Server 2012(서비스 팩 3 이상)  

- 사이트는 [지원되는 클라이언트 OS 버전](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)을 실행할 수 있는 최대 10개의 클라이언트를 지원합니다.<!-- SCCMDocs#1656 -->

> [!Note]  
> 이러한 제품이 이 내용에 포함되었다고 해서 해당 지원 주기가 끝난 버전의 지원 연장을 의미하지는 않습니다. Configuration Manager는 지원 주기가 끝난 제품은 지원하지 않습니다. 자세한 내용은 [Microsoft Lifecycle 정책](https://go.microsoft.com/fwlink/p/?LinkId=208270)을 참조하세요.  

## <a name="bkmk_install"></a> 설치 및 업데이트  

랩 사용에 대한 Configuration Manager 기술 미리 보기 분기는 프로덕션 사용에 대한 Configuration Manager 현재 분기와 다릅니다.  

먼저 기술 미리 보기 분기의 기준 버전을 설치합니다. 기준 버전을 설치한 후 콘솔 내 업데이트를 사용하여 최근의 미리 보기 버전으로 설치를 업데이트합니다. 일반적으로 새 버전의 기술 미리 보기는 매달 사용할 수 있습니다.

Microsoft는 세 개의 연속 버전을 사용할 수 있을 때까지 각 기술 미리 보기 버전을 지원합니다. 예를 들어 버전 1708이 릴리스되면 버전 1704는 더 이상 지원되지 않습니다. 버전 1705, 1706 및 1707은 계속 지원됩니다. 기준 버전이 지원되지 않는 경우에도 지원되는 버전으로 즉시 업데이트한다고 가정하여 새 기술 미리 보기 사이트를 설치할 수 있습니다. 새 기준 버전을 사용할 수 있을 때까지 이전 기준 버전이 지원됩니다. 기준 버전에서 사용 가능한 최신 버전으로 업데이트하고 나서, 최신 기술 미리 보기 버전을 설치할 때까지 업데이트 프로세스를 반복합니다.

> [!TIP]  
> 기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다. 기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하는 옵션이 없습니다. 또한 현재 분기 릴리스의 업데이트를 받을 수 없습니다.
>
> 한 해에 여러 번, 동일한 버전 번호를 가진 기술 미리 보기 분기 및 현재 분기 버전이 있습니다. 예를 들면 Technical Preview 버전 1802 및 현재 분기 버전 1802입니다.

### <a name="active-baseline-versions"></a>활성 기준 버전

릴리스 후 최대 1년 동안 기준 버전을 설치합니다. 새 기술 미리 보기 사이트를 설치할 때 현재 둘 이상의 기준 버전을 사용할 수 있는 경우 최신 기준 버전을 사용합니다.

- **기술 미리 보기 버전 1907**: Configuration Manager 기술 미리 보기 버전 1907은 콘솔 내 업데이트와 새 기준 버전으로 모두 사용할 수 있습니다. [TechNet 평가 센터에서](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 기준 버전을 다운로드합니다.


## <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  

기술 미리 보기의 새로운 기능에 대한 피드백을 보내 주시기 바랍니다. 자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#product-feedback)을 참조하세요.

새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 제출하고 다른 사용자가 제출한 아이디어에 투표하려면 [UserVoice 페이지](https://configurationmanager.uservoice.com)를 방문하세요.  


<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->


## <a name="bkmk_tpCaps"></a> 최신 버전의 기능  

다음 기능은 최신 Configuration Manager 기술 미리 보기 버전에서 사용할 수 있습니다.

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1910"></a>Technical preview 버전 1910

<!-- - [title](/sccm/core/get-started/2019/technical-preview-1901#bkmk_anchor) <!--ID-->

- [Microsoft Edge, 버전 77 이상 배포](/sccm/core/get-started/2019/technical-preview-1910#bkmk_Microsoft_Edge) <!--4561024-->
- [규정 준수 정책 평가의 일환으로 사용자 지정 구성 기준 포함](/sccm/core/get-started/2019/technical-preview-1910#bkmk_CAbaselines) <!--3608345-->
- [애플리케이션 그룹 개선 사항](/sccm/core/get-started/2019/technical-preview-1910#bkmk_appgrp) <!--4760058-->
- [SEDO 잠금 회수](/sccm/core/get-started/2019/technical-preview-1910#bkmk_sedo) <!--4786915-->
- [피드백에 파일 첨부](/sccm/core/get-started/2019/technical-preview-1910#attach-files-to-feedback) <!--3556011-->
- [클라이언트 진단 작업](/sccm/core/get-started/2019/technical-preview-1910#bkmk_diag) <!--4433455-->
- [Office 365 ProPlus 파일럿 및 상태 대시보드](/sccm/core/get-started/2019/technical-preview-1910#office-365-proplus-pilot-and-health-dashboard) <!--4488272-->
- [콘솔 검색 개선 사항](/sccm/core/get-started/2019/technical-preview-1910#bkmk_search) <!--4640570-->
- [Windows 10 전체 업그레이드에에 대한 새 변수](/sccm/core/get-started/2019/technical-preview-1910#bkmk_osdvar) <!--4680263-->
- [Windows Virtual Desktop 지원에 대한 개선 사항](/sccm/core/get-started/2019/technical-preview-1910#bkmk_wvd) <!--4737447-->

> [!Note]  
> 이전 버전의 기술 미리 보기에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로 Configuration Manager 현재 분기에 추가된 기능은 기술 미리 보기 분기에서 계속 사용할 수 있습니다.  


## <a name="features-in-recent-technical-previews"></a>최신 기술 미리 보기의 기능

현재 분기 버전 1906 이후 Configuration Manager 기술 미리 보기 분기와 함께 다음 기능이 릴리스되었습니다.

### <a name="technical-preview-version-1909"></a>Technical Preview 버전 1909

- [오케스트레이션 그룹](/sccm/core/get-started/2019/technical-preview-1909#bkmk_OGs) <!--3098816-->
- [BitLocker 관리의 향상된 기능](/sccm/core/get-started/2019/technical-preview-1909#bkmk_bitlocker) <!--3601034-->
- [온-프레미스 사이트를 확장하고 Microsoft Azure로 마이그레이션](/sccm/core/get-started/2019/technical-preview-1909#bkmk_Azure-migration) <!--3556022-->
- [추가 CMPivot 엔터티 및 향상된 기능](/sccm/core/get-started/2019/technical-preview-1909#bkmk_CMPivot) <!--5410930-->
- [인터넷을 통해 주문형으로 작업 순서 다운로드](/sccm/core/get-started/2019/technical-preview-1909#bkmk_dodcmg) <!--3601238-->
- [Windows 참가자를 위한 지원](/sccm/core/get-started/2019/technical-preview-1909#bkmk_wifb) <!--3556023-->
- [작업 순서에서 향상된 언어 지원](/sccm/core/get-started/2019/technical-preview-1909#bkmk_osd) <!--5411057-->
- [Office 365 ProPlus 상태 대시보드](/sccm/core/get-started/2019/technical-preview-1909#bkmk_o365health) <!--4488301-->
- [작업 순서 디버거의 향상된 기능](/sccm/core/get-started/2019/technical-preview-1909#bkmk_tsdebug) <!-- 5012536, 5012509 -->

### <a name="technical-preview-version-19082"></a>Technical Preview 버전 1908.2

- [콘솔 연결 개선](/sccm/core/get-started/2019/technical-preview-1908-2#improvements-to-console-connections) <!--4923997-->
- [멀티캐스트 사용 배포 지점 개선](/sccm/core/get-started/2019/technical-preview-1908-2#bkmk_multicast) <!--3785535-->
- [CMPivot 엔진에 대한 최적화](/sccm/core/get-started/2019/technical-preview-1908-2#optimizations-to-the-cmpivot-engine) <!--3197353-->
- [OS 배포 중 키보드 레이아웃 설정](/sccm/core/get-started/2019/technical-preview-1908-2#bkmk_osd) <!--5138936-->

### <a name="technical-preview-version-1908"></a>Technical Preview 버전 1908

- [전원 계획의 작업 순서 성능 향상](/sccm/core/get-started/2019/technical-preview-1908#bkmk_tsperf) <!--3555926-->
- [CMPivot 독립 실행형을 사용하는 로컬 디바이스 쿼리 평가](/sccm/core/get-started/2019/technical-preview-1908#local-device-query-evaluation-using-cmpivot-standalone) <!--3197353-->
- [ADR용 추가 소프트웨어 업데이트 필터](/sccm/core/get-started/2019/technical-preview-1908#additional-software-update-filter-for-adrs) <!--4852033-->
- [모든 Windows 업데이트에 대해 배달 최적화 사용](/sccm/core/get-started/2019/technical-preview-1908#use-delivery-optimization-for-all-windows-updates) <!--4699118 (4685210)-->
- [단계적 배포 템플릿](/sccm/core/get-started/2019/technical-preview-1908#phased-deployment-templates) <!--4961086-->
- [콘솔 연결 노드 개선](/sccm/core/get-started/2019/technical-preview-1908#improvements-to-console-connections-node) <!--4923997 (4951240)-->
- [복사 및 붙여넣기 작업 순서 조건](/sccm/core/get-started/2019/technical-preview-1908#bkmk_tscondition) <!--4621098-->
- [작업 순서 검색 기능 개선](/sccm/core/get-started/2019/technical-preview-1908#bkmk_tssearch) <!--4621085-->
- [향상된 OS 배포 기능](/sccm/core/get-started/2019/technical-preview-1908#bkmk_osd) <!--4910348, 4931110, 4977616-->

### <a name="technical-preview-version-1907"></a>Technical Preview 버전 1907

- [작업 순서 편집기 검색](/sccm/core/get-started/2019/technical-preview-1907#bkmk_tsedit) <!--4621085-->
- [Office 365 ProPlus 업그레이드 준비 대시보드 개선](/sccm/core/get-started/2019/technical-preview-1907#improvements-to-office-365-proplus-upgrade-readiness-dashboard) <!--4021125-->


> [!Tip]  
> 새 현재 분기 버전을 사용할 수 있는 경우 해당 버전에서 사용할 수 있는 기능은 최신 *새로운 기능* 문서에 나열됩니다. 자세한 내용은 [증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions#supported-versions)을 참조하세요.

<!-- This is the full list of new features in the past TP releases since the last CB release.
Each month, add features from the list above to a new H3 section at the top of this section.
When there's a new CB, add any features not in that CB to the table in H2 "Features in previous technical previews"
-->


## <a name="features-in-previous-technical-previews"></a>이전 기술 미리 보기의 기능

다음 기능은 이전 버전의 Configuration Manager 기술 미리 보기 분기와 함께 릴리스되었습니다. 이러한 기능은 이후 버전에서 사용할 수 있지만 현재 분기에서는 제공되지 않습니다.

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

| 기능        | 기술 미리 보기 버전 |  
|----------------|---------------------------|
| 어디서나 클라우드 관리 게이트웨이를 사용하여 원격 제어 <!--4575930--> | [Tech Preview 1906](/sccm/core/get-started/2019/technical-preview-1906#remote-control-anywhere-using-cloud-management-gateway) |
| 향상된 커뮤니티 허브 기능 <!--3555935--> | [Tech Preview 1906](/sccm/core/get-started/2019/technical-preview-1906#bkmk_hub) |
| 타사 업데이트 카탈로그에 대한 추가 옵션 <!--4469002--> | [Tech Preview 1906](/sccm/core/get-started/2019/technical-preview-1906#additional-options-for-third-party-update-catalogs) |
| 앱 모델 배포 유형의 작업 순서 <!--3555953--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_tsdt) |
| BitLocker 관리 <!--3601034--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_bitlocker) |
| 향상된 커뮤니티 허브 기능 <!--4224401--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_hub) |
| 커뮤니티 허브 및 GitHub <!--3555935--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#community-hub-and-github) |
| 클라우드 서비스 비용 예측기 <!--3555774--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_cmg) |
| 커뮤니티 허브에서 보고서 다운로드 <!--3555936--> | [Tech Preview 1812](capabilities-in-technical-preview-1812.md#bkmk_hub) |
| 커뮤니티 허브 <!--3556020, fka 1357766--> | [Tech Preview 1807](capabilities-in-technical-preview-1807.md#bkmk_hub) |
| 클라이언트 기반 PXE 응답자 서비스 <!--3556018, fka 1357148--> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service) |
| IPv6에 대한 PXE 네트워크 부팅 지원 <!--3601254, fka 1269793--> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
| Azure Active Directory 사용 <!--3607315, fka 1322145--> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
| Asset Intelligence 개선 <!--3601024, fka 1307390--> | [Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence) |


## <a name="see-also"></a>참고 항목  

자세한 내용은 다음 아티클을 참조하세요.  

- [랩에서 Configuration Manager 평가](/sccm/core/get-started/evaluate-with-lab-environment)
- [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
- [Configuration Manager 소개](/sccm/core/understand/introduction)

> [!Tip]  
> 사용하려면 동의가 필요한 현재 분기 기능에 대한 자세한 내용은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  
>
> 먼저 사용하도록 설정해야 하는 현재 분기 기능에 대한 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  
