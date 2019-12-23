---
title: 기술 미리 보기 릴리스
titleSuffix: Configuration Manager
description: Configuration Manager에서 새로운 기능과 기술을 시험 사용할 수 있는 기술 미리 보기 분기를 알아봅니다.
ms.date: 12/12/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: cdf4a185a60bff7988b028b9ea8ae9f345cb5d78
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198543"
---
# <a name="technical-preview-for-configuration-manager"></a>Configuration Manager에 대한 기술 미리 보기

*적용 대상: Configuration Manager(기술 미리 보기 분기)*

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

Microsoft는 세 개의 연속 버전을 사용할 수 있을 때까지 각 기술 미리 보기 버전을 지원합니다. 예를 들어 버전 1908이 릴리스되면 버전 1904는 더 이상 지원되지 않습니다. 버전 1905, 1906 및 1907은 계속 지원됩니다. 기준 버전이 지원되지 않는 경우에도 지원되는 버전으로 즉시 업데이트한다고 가정하여 새 기술 미리 보기 사이트를 설치할 수 있습니다. 새 기준 버전을 사용할 수 있을 때까지 이전 기준 버전이 지원됩니다. 기준 버전에서 사용 가능한 최신 버전으로 업데이트하고 나서, 최신 기술 미리 보기 버전을 설치할 때까지 업데이트 프로세스를 반복합니다.

> [!TIP]  
> 기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다. 기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하는 옵션이 없습니다. 또한 현재 분기 릴리스의 업데이트를 받을 수 없습니다.
>
> 한 해에 여러 번, 동일한 버전 번호를 가진 기술 미리 보기 분기 및 현재 분기 버전이 있습니다. 예를 들어, 기술 미리 보기 버전 1910과 현재 분기 버전 1910이 있습니다.

### <a name="active-baseline-versions"></a>활성 기준 버전

릴리스 후 최대 1년 동안 기준 버전을 설치합니다. 새 기술 미리 보기 사이트를 설치할 때는 최신 기준 버전을 사용합니다.

- **기술 미리 보기 버전 1911**: Configuration Manager 기술 미리 보기 분기 버전 1911은 콘솔 내 업데이트와 새 기준 버전으로 모두 사용할 수 있습니다.

[TechNet 평가 센터](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview)에서 기준 버전을 다운로드합니다.

## <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  

기술 미리 보기의 새로운 기능에 대한 피드백을 보내 주시기 바랍니다. 자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#product-feedback)을 참조하세요.

새로 추가되기를 원하는 기능에 대한 의견이 있으면 보내 주세요! 새로운 아이디어를 제출하고 다른 사용자가 제출한 아이디어에 투표하려면: [Configuration Manager UserVoice](https://configurationmanager.uservoice.com)를 방문하세요.  

<!--
## <a name="bdmk_tpknownissues"></a> General changes introduced in technical preview branch

<!-- (explanatory comment)
Enable this section if needed to include any broad change to the tech preview branch
-->

## <a name="bkmk_tpCaps"></a> 최신 버전의 기능  

<!-- (explanatory comment)
This is the full list of new features in the latest TP release
-->

다음 기능은 최신 Configuration Manager 기술 미리 보기 버전에서 사용할 수 있습니다.

### <a name="technical-preview-version-1912"></a>Technical Preview 버전 1912

<!-- - [title](/sccm/core/get-started/2019/technical-preview-1912#bkmk_anchor) <!--ID-->

- [클라이언트 등록 직후 작업 순서 부트스트랩](/sccm/core/get-started/2019/technical-preview-1912#bkmk_provisionts) <!--5526972-->
- [Microsoft Defender ATP(Advanced Threat Protection) 온보딩 확장](/sccm/core/get-started/2019/technical-preview-1912#bkmk_atp) <!--5229962-->
- [Microsoft 서비스의 새 관리 인사이트 규칙](/sccm/core/get-started/2019/technical-preview-1912#bkmk_rules) <!--3607758-->
- [클라이언트 로그 수집](/sccm/core/get-started/2019/technical-preview-1912#client-log-collection) <!--4226618-->
- [향상된 CMPivot 기능](/sccm/core/get-started/2019/technical-preview-1912#improvements-to-cmpivot) <!--5870934-->
- [향상된 OS 배포 기능](/sccm/core/get-started/2019/technical-preview-1912#bkmk_osd) <!--5842295,5573175,5690481-->

> [!NOTE]  
> 이전 버전의 기술 미리 보기에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로 Configuration Manager 현재 분기에 추가된 기능은 기술 미리 보기 분기에서 계속 사용할 수 있습니다.  

## <a name="features-in-recent-technical-previews"></a>최신 기술 미리 보기의 기능

<!-- (explanatory comment)
This is the full list of new features in the past TP releases since the last CB release.
Each month, add features from the list above to a new H3 section at the top of this section.
When there's a new CB, add any features not in that CB to the table in H2 "Features in previous technical previews"
-->

<!-- (commented out for 1910 CB since there's nothing to show, 1910tp section is an example for next TP)
The following features were released with previous versions of the Configuration Manager technical preview branch since current branch version 1910:

### Technical preview version 1910

- [Attach files to feedback](/sccm/core/get-started/2019/technical-preview-1910#attach-files-to-feedback) <!--3556011-->

> [!TIP]  
> 새 현재 분기 버전을 사용할 수 있는 경우 해당 버전에서 사용할 수 있는 기능은 최신 *새로운 기능* 문서에 나열됩니다. 자세한 내용은 [증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions#supported-versions)을 참조하세요.

## <a name="features-in-previous-technical-previews"></a>이전 기술 미리 보기의 기능

<!-- (explanatory comment)
This is the list of individual features that are still in TP (not in CB). 
Copy from the lists above any individual features that are still in TP and add to the top of this list
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

다음 기능은 이전 버전의 Configuration Manager 기술 미리 보기 분기와 함께 릴리스되었습니다. 이러한 기능은 이후 버전에서 사용할 수 있지만 현재 분기에서는 제공되지 않습니다.

| 기능        | 기술 미리 보기 버전 |  
|----------------|---------------------------|
| 피드백에 파일 첨부 <!--3556011--> | [Tech Preview 1910](/sccm/core/get-started/2019/technical-preview-1910#attach-files-to-feedback) |
| 오케스트레이션 그룹 <!--3098816--> | [Tech Preview 1909](/sccm/core/get-started/2019/technical-preview-1909#bkmk_OGs) |
| 멀티캐스트 사용 배포 지점 개선 <!--3785535--> | [Tech Preview 1908.2](/sccm/core/get-started/2019/technical-preview-1908-2#bkmk_multicast) |
| 단계적 배포 템플릿 <!--4961086--> | [Tech Preview 1908](/sccm/core/get-started/2019/technical-preview-1908#phased-deployment-templates) |
| 어디서나 클라우드 관리 게이트웨이를 사용하여 원격 제어 <!--4575930--> | [Tech Preview 1906](/sccm/core/get-started/2019/technical-preview-1906#remote-control-anywhere-using-cloud-management-gateway) |
| 향상된 커뮤니티 허브 기능 <!--3555935--> | [Tech Preview 1906](/sccm/core/get-started/2019/technical-preview-1906#bkmk_hub) |
| 앱 모델 배포 유형의 작업 순서 <!--3555953--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_tsdt) |
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
