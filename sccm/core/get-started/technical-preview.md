---
title: 기술 미리 보기 릴리스
titleSuffix: Configuration Manager
description: Configuration Manager에서 새로운 기능과 기술을 시험 사용할 수 있는 기술 미리 보기 분기를 알아봅니다.
ms.date: 04/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6797b25138bdd09dd4a879ef461d5420c38ab47
ms.sourcegitcommit: 8eccf5429aabcef17d5762e4b03912ccad1215e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64928864"
---
# <a name="technical-preview-for-configuration-manager"></a>Configuration Manager에 대한 기술 미리 보기

*적용 대상: System Center Configuration Manager(기술 미리 보기)*

이 문서에서는 Configuration Manager의 월간 기술 미리 보기 분기를 자세히 설명합니다. 기술 미리 보기에서는 Microsoft가 작업하고 있는 새로운 기능을 소개합니다. Configuration Manager의 현재 분기에 아직 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능은 최종적으로 현재 분기에 대한 업데이트에 포함될 수 있습니다. 기능을 마무리하기 전에 기능을 사용해 보고 피드백을 보내 주시기 바랍니다.  

이 릴리스는 기술적인 미리 보기이므로 세부 사항 및 기능은 변경될 수 있습니다.  

이 정보는 Configuration Manager 기술 미리 보기 분기의 모든 버전에 적용됩니다. 이 문서에서는 먼저 나타나는 기술 미리 보기 버전과 함께 각 새로운 기능을 나열합니다. 예를 들어 2019년(19) 1월(01)에 대한 버전 **1901**입니다. 각 미리 보기 버전에 전용으로 제공되는 개별 문서에서 개별 기능을 자세히 설명합니다.  

Configuration Manager *현재 분기*의 새로운 기능에 대한 자세한 내용은 [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)을 참조하세요.

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22technical+preview+releases+-+Configuration+Manager%22&locale=en-us`

## <a name="bkmk_reqs"></a> 요구 사항 및 제한 사항  

> [!IMPORTANT]  
> 기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다. Microsoft에서 지원 서비스를 제공하지 않을수 있으며, 특정 기능은 미리 보기 소프트웨어에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 미리 보기 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

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

- 사이트는 최대 10개 클라이언트를 지원하며, 이러한 클라이언트는 다음 버전의 Windows 중 하나를 실행해야 합니다.  

    - Windows 10  
    - Windows 8.1  
    - Windows 7  

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

- **기술 미리 보기 버전 1902.2**: Configuration Manager 기술 미리 보기 버전 1902.2는 콘솔 내 업데이트와 새 기준 버전으로 사용할 수 있습니다. [TechNet 평가 센터에서](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 기준 버전을 다운로드합니다.

## <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  

기술 미리 보기의 새로운 기능에 대한 피드백을 보내 주시기 바랍니다. 자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#product-feedback)을 참조하세요.

새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 제출하고 다른 사용자가 제출한 아이디어에 투표하려면 [UserVoice 페이지](https://configurationmanager.uservoice.com)를 방문하세요.  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->

## <a name="bkmk_tpCaps"></a> 최신 버전의 기능  

다음 기능은 최신 Configuration Manager 기술 미리 보기 버전에서 사용할 수 있습니다.

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1904"></a>Technical Preview 버전 1904

<!-- - [title](/sccm/core/get-started/2019/technical-preview-1901#bkmk_anchor) <!--ID-->

- [Office 365 ProPlus 업그레이드 준비 대시보드](/sccm/core/get-started/2019/technical-preview-1904#bkmk_o365) <!--4021125-->  

- [기능 업데이트 동안 동적 업데이트 구성](/sccm/core/get-started/2019/technical-preview-1904#configure-dynamic-update-during-feature-updates) <!--4062619-->  

- [커뮤니티 허브 및 GitHub](/sccm/core/get-started/2019/technical-preview-1904#community-hub-and-github) <!--3555935,3555936-->  

- [CMPivot 독립 실행형](/sccm/core/get-started/2019/technical-preview-1904#bkmk_cmpivot) <!--3555890-->  

- [소프트웨어 센터 인프라 개선 사항](/sccm/core/get-started/2019/technical-preview-1904#bkmk_swctr) <!--3555950-->  

- [향상된 WSUS 유지 관리 제어](/sccm/core/get-started/2019/technical-preview-1904#improved-control-over-wsus-maintenance) <!--4110109-->  

- [드라이버 패키지 및 OS 이미지 사전 캐시](/sccm/core/get-started/2019/technical-preview-1904#bkmk_precache) <!--4224642-->  

- [향상된 OS 배포 기능](/sccm/core/get-started/2019/technical-preview-1904#bkmk_osd) <!--2839943,4447680-->  

> [!Note]  
> 이전 버전의 기술 미리 보기에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로 Configuration Manager 현재 분기에 추가된 기능은 기술 미리 보기 분기에서 계속 사용할 수 있습니다.  

## <a name="features-in-recent-supported-technical-previews"></a>최근 지원되는 기술 미리 보기의 기능

다음 기능은 계속 지원되는 이전 버전의 Configuration Manager 기술 미리 보기 분기와 함께 릴리스되었습니다.

<!-- This is the full list of new features in the past THREE (3) TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 | 기능 | 기술 미리 보기 버전 | 현재 분기 버전 |  
 |---------|---------------------------|------------------------|
 | 클라우드 서비스 비용 예측기 <!--3555774--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_cmg) | ![추가되지 않음](media/Red_X.gif) |
 | 전송 최적화를 위해 배포 지점을 로컬 캐시 서버로 사용 <!--3555764--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_doinc) | ![추가되지 않음](media/Red_X.gif) |
 | 작업 순서를 편집하기 위해 잠금 확보 <!--3699337--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_sedo) | ![추가되지 않음](media/Red_X.gif) |
 | 필수 업데이트 드릴스루 <!--4224414--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_req-updates) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 작업 순서 미디어 만들기 기능 <!--4090666--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_tsmedia) | ![추가되지 않음](media/Red_X.gif) |
 | Office 365 업데이트용 추가 언어 <!--3555955--> | [Tech Preview 1902.2](/sccm/core/get-started/2019/technical-preview-1902-2#bkmk_o365lang) | 버전 1902 |
 | Office 365 ProPlus 준비를 위한 분석과 통합 <!--3735402--> | [Tech Preview 1902.2](/sccm/core/get-started/2019/technical-preview-1902-2#bkmk_o365) | 버전 1902 |
 | 단계적 배포 성공 조건 개선 <!--3555946--> | [Tech Preview 1902.2](/sccm/core/get-started/2019/technical-preview-1902-2#bkmk_pod) | 버전 1902 |
 | 고급 HTTP로 개선 <!--3798957--> | [Tech Preview 1902.2](/sccm/core/get-started/2019/technical-preview-1902-2#bkmk_ehttp) | 버전 1902 |
 | 알림 메시지를 대화 상자 창으로 바꾸기 <!--3555947--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_impact) | 버전 1902 |
 | 현재 위치 업그레이드 작업 순서 중 진행 상태 <!--3747129--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_ipu) | 버전 1902 |
 | 알려진 Windows 폴더를 OneDrive로 리디렉션 <!--3556021--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_odfb) | 버전 1902 |
 | 원격 제어 시 첫 번째 화면만 보기 <!--3231732--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_rcmulti) | 버전 1902 |
 | PowerShell 스크립트 편집 또는 복사 <!--3705507--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_psedit) | 버전 1902 |
 | 경계 그룹에 클라우드 관리 게이트웨이 추가 <!--3640932--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_cmgbg) | 버전 1902 |
 | 소프트웨어 센터의 기본 보기 구성 <!--3612112--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_swctr) | 버전 1902 |
 | 클라이언트 상태 대시보드 개선 사항 <!--3599209--> | [Tech Preview 1902](/sccm/core/get-started/2019/technical-preview-1902#bkmk_health) | 버전 1902 |
 | 클라이언트 상태 대시보드 <!--3599209--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_health) | 버전 1902 |
 | Windows 10 서비스에서 기능 업데이트에 대한 우선 순위 지정 <!--3734525--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_neo) | 버전 1902 |
 | 단계별 배포에 대한 전용 모니터링 <!--3555949--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_pod) | 버전 1902 |
 | 중앙 관리 사이트에서 CMPivot 실행 <!--3610960--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_cmpivot) | 버전 1902 |
 | 향상된 PowerShell 스크립트 실행 작업 순서 단계 기능 <!--3556028--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_posh) | 버전 1902 |
 | 수명 주기 대시보드의 Office 제품 <!--3556026--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_lifecycle) | 버전 1902 |
 | 컬렉션에 대한 관리 인사이트 규칙 <!--3555752--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_micoll) | 버전 1902 |
 | MAC 주소를 사용하여 검색 디바이스 보기 <!--3600878--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_mac) | 버전 1902 |
 | 배포 지점 유지 관리 모드 <!--3555754--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_dpmaint) | 버전 1902 |
 | 최적화된 이미지 서비스 <!--3555951--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_resetbase) | 버전 1902 |
 | OS 이미지의 단일 인덱스 가져오기 <!--3719699--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_index) | 버전 1902 |
 | 클라우드 서비스에 대한 Azure Resource Manager 사용 <!--3605704--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_arm) | 버전 1902 |
 | 콘솔 피드백 확인 <!--3556010--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_feedback) | 버전 1902 |
 | Azure에서 Configuration Manager Technical Preview 랩 만들기 <!--3556017--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_azurevm) | 해당 없음 |
 | 피어 절전 모드 해제를 위한 사용자 지정 포트 지정 <!--3605925--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_sleep) | 버전 1902 |
 | 최근에 연결된 콘솔 보기 <!--3699367--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_console) | 버전 1902 |
 | 임계값을 초과하는 경우 클라우드 서비스 중지 <!--3735092--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_cmg) | 버전 1902 |
 | 클라이언트 프로비전 모드 시간 제한 <!--3197824--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_osdprov) | 버전 1902 |
 | 향상된 OS 배포 <!--3633146,3641475,3654172,3734270--> | [Tech Preview 1901](/sccm/core/get-started/2019/technical-preview-1901#bkmk_osd) | 버전 1902 |


## <a name="features-in-previous-technical-previews"></a>이전 기술 미리 보기의 기능

다음 기능은 이전 버전의 Configuration Manager 기술 미리 보기 분기와 함께 릴리스되었습니다. 이러한 기능은 이후 버전에서 사용할 수 있지만 현재 분기에서는 제공되지 않습니다.

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

| 기능        | 기술 미리 보기 버전 |  
|----------------|---------------------------|
| 커뮤니티 허브에서 보고서 다운로드<!--3555936--> | [Tech Preview 1812](capabilities-in-technical-preview-1812.md#bkmk_hub) |
| 커뮤니티 허브 <!--3556020, fka 1357766--> | [Tech Preview 1807](capabilities-in-technical-preview-1807.md#bkmk_hub) |
| 클라이언트 기반 PXE 응답자 서비스 <!--3556018, fka 1357148--> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service) |
| IPv6에 대한 PXE 네트워크 부팅 지원 <!--3601254, fka 1269793--> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
| Azure Active Directory 사용 <!--3607315, fka 1322145--> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
| Asset Intelligence 개선 <!--3601024, fka 1307390--> | [Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence) |
| 최종 사용자가 회사 포털에서 앱을 설치할 수 있습니다. <!--3601249, fka 1037233--> | [Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End) |

## <a name="see-also"></a>참고 항목  

자세한 내용은 다음 아티클을 참조하세요.  

- [랩에서 Configuration Manager 평가](/sccm/core/get-started/evaluate-with-lab-environment)
- [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
- [Configuration Manager 소개](/sccm/core/understand/introduction)

> [!Tip]  
> 사용하려면 동의가 필요한 현재 분기 기능에 대한 자세한 내용은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  
>
> 먼저 사용하도록 설정해야 하는 현재 분기 기능에 대한 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  
