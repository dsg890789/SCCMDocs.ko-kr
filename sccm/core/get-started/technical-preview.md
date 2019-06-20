---
title: 기술 미리 보기 릴리스
titleSuffix: Configuration Manager
description: Configuration Manager에서 새로운 기능과 기술을 시험 사용할 수 있는 기술 미리 보기 분기를 알아봅니다.
ms.date: 06/12/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd2336ecef4af05d253c413f0402d5a83414df97
ms.sourcegitcommit: e3c1eb0b75d79c05a750d49354c851d15d5e26a3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67038713"
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

### <a name="technical-preview-version-1906"></a>Technical Preview 버전 1906

<!-- - [title](/sccm/core/get-started/2019/technical-preview-1901#bkmk_anchor) <!--ID-->

- [유지 관리 작업 개선](/sccm/core/get-started/2019/technical-preview-1906#improvements-to-maintenance-tasks) <!--3555894-->
- [Configuration Manager 업데이트 데이터베이스 업그레이드 모니터링](/sccm/core/get-started/2019/technical-preview-1906#configuration-manager-update-database-upgrade-monitoring) <!--4200581-->
- [공동 관리 워크로드를 위한 여러 파일럿 그룹](/sccm/core/get-started/2019/technical-preview-1906#bkmk_comgmt_pilot) <!--3555750-->
- [새로 제공되는 소프트웨어의 알림 논리 재설계](/sccm/core/get-started/2019/technical-preview-1906#redesigned-notification-logic-for-newly-available-software) <!--3555904-->
- [폴더에 대한 RBAC](/sccm/core/get-started/2019/technical-preview-1906#rbac-on-folders) <!--3600867-->
- [Azure Active Directory 사용자 그룹 검색](/sccm/core/get-started/2019/technical-preview-1906#bkmk_aad-disco) <!--3611956-->
- [어디서나 클라우드 관리 게이트웨이를 사용하여 원격 제어](/sccm/core/get-started/2019/technical-preview-1906#remote-control-anywhere-using-cloud-management-gateway) <!--4575930-->
- [향상된 커뮤니티 허브 기능](/sccm/core/get-started/2019/technical-preview-1906#bkmk_hub) <!--3555935-->
- [CMPivot에서 조인, 추가 연산자 및 집계 추가](/sccm/core/get-started/2019/technical-preview-1906#bkmk_cmpivot) <!--4054074-->
- [향상된 CMPivot 기능](/sccm/core/get-started/2019/technical-preview-1906#improvements-to-cmpivot) <!--4619340,4683130-->
- [향상된 Configuration Manager 콘솔 기능](/sccm/core/get-started/2019/technical-preview-1906#bkmk_console) <!--4223683-->
- [Windows Virtual Desktop 지원](/sccm/core/get-started/2019/technical-preview-1906#bkmk_winsku) <!--3556025-->
- [다시 시작에 대한 카운트다운 미리 알림 빈도 증가](/sccm/core/get-started/2019/technical-preview-1906#more-frequent-countdown-notifications-for-restarts) <!--3976435-->
- [디바이스 토큰을 사용하여 공동 관리 자동 등록](/sccm/core/get-started/2019/technical-preview-1906#bkmk_comgmt) <!--4454491-->
- [타사 업데이트 카탈로그에 대한 추가 옵션](/sccm/core/get-started/2019/technical-preview-1906#additional-options-for-third-party-update-catalogs) <!--4469002-->
- [작업 순서 중에 클라이언트 캐시에서 앱 콘텐츠 제거](/sccm/core/get-started/2019/technical-preview-1906#bkmk_tscache) <!--4485675-->
- [새 Windows 10 버전 1903 이상 제품 범주](/sccm/core/get-started/2019/technical-preview-1906#new-windows-10-version-1903-and-later-product-category) <!--4682946-->
- [NTLM 대체에 대한 관리 인사이트 규칙](/sccm/core/get-started/2019/technical-preview-1906#bkmk_ntlm) <!--4572953-->
- [디바이스에 배포된 필터 애플리케이션](/sccm/core/get-started/2019/technical-preview-1906#bkmk_appcategory) <!--4451056-->
- [향상된 OS 배포 기능](/sccm/core/get-started/2019/technical-preview-1906#bkmk_osd) <!--4668846, 2840337, 4512937-->
- [소프트웨어 센터의 사용자 지정 탭에 대한 직접 링크](/sccm/core/get-started/2019/technical-preview-1906#bkmk_swctr) <!--4655176-->

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
 | 향상된 WSUS 유지 관리 제어 <!--4110109--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#improved-control-over-wsus-maintenance) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 Configuration Manager 콘솔 기능 <!--4616810--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_console) | ![추가되지 않음](media/Red_X.gif) |
 | 소프트웨어 업데이트에 대한 기본 최대 실행 시간 구성 <!--3734426--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_timeout) | ![추가되지 않음](media/Red_X.gif) |
 | Windows Defender Application Guard 파일 신뢰 기준 <!--3555858--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_wdag) | ![추가되지 않음](media/Red_X.gif) |
 | 애플리케이션 그룹 <!--3555907--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_app-group) | ![추가되지 않음](media/Red_X.gif) |
 | 앱 모델 배포 유형의 작업 순서 <!--3555953--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_tsdt) | ![추가되지 않음](media/Red_X.gif) |
 | BitLocker 관리 <!--3601034--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_bitlocker) | ![추가되지 않음](media/Red_X.gif) |
 | 작업 순서 디버거 <!--3612274--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_tsdebug) | ![추가되지 않음](media/Red_X.gif) |
 | 클라이언트 데이터 원본 대시보드의 전송 최적화 <!--3555759--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_do) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 커뮤니티 허브 기능 <!--4224401--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_hub) | ![추가되지 않음](media/Red_X.gif) |
 | 디바이스 목록에서 SMBIOS GUID 보기 <!--4526580--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_smbios) | ![추가되지 않음](media/Red_X.gif) |
 | OneTrace 로그 뷰어 <!--3555962--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_onetrace) | ![추가되지 않음](media/Red_X.gif) |
 | 소프트웨어 센터 인프라 개선 사항 <!--3555950--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_swctr) | ![추가되지 않음](media/Red_X.gif) |
 | 소프트웨어 센터 탭 사용자 지정의 개선 사항 <!--4063773--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#improvements-to-software-center-tab-customizations) | ![추가되지 않음](media/Red_X.gif) |
 | 앱 승인 개선 사항 <!--4224910--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_approve) | ![추가되지 않음](media/Red_X.gif) |
 | 사전 승인된 애플리케이션의 설치 다시 시도 <!--4336307--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_retry) | ![추가되지 않음](media/Red_X.gif) |
 | 디바이스용 애플리케이션 설치 <!--4402180--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_device-app) | ![추가되지 않음](media/Red_X.gif) |
 | 다시 시작에 대한 카운트다운 알림 빈도 증가 <!--3976435--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_restart) | ![추가되지 않음](media/Red_X.gif) |
 | Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화 <!--3607475--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_aadcollsync) | ![추가되지 않음](media/Red_X.gif) |
 | 클라이언트 캐시 최소 보존 기간 구성 <!--4485509--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_cache) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 OS 배포 <!--4512937,4224642--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_osd) | ![추가되지 않음](media/Red_X.gif) |
 | SQL AlwaysOn 노드 추가 <!--3127336--> | [Tech Preview 1905](/sccm/core/get-started/2019/technical-preview-1905#bkmk_sqlao) | ![추가되지 않음](media/Red_X.gif) |
 | Office 365 ProPlus 업그레이드 준비 대시보드 <!--4021125--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#bkmk_o365) | ![추가되지 않음](media/Red_X.gif) |
 | 기능 업데이트 동안 동적 업데이트 구성 <!--4062619--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#configure-dynamic-update-during-feature-updates) | ![추가되지 않음](media/Red_X.gif) |
 | 커뮤니티 허브 및 GitHub <!--3555935,3555936--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#community-hub-and-github) | ![추가되지 않음](media/Red_X.gif) |
 | CMPivot 독립 실행형 <!--3555890--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#bkmk_cmpivot) | ![추가되지 않음](media/Red_X.gif) |
 | 소프트웨어 센터 인프라 개선 사항 <!--3555950--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#bkmk_swctr) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 WSUS 유지 관리 제어 <!--4110109--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#improved-control-over-wsus-maintenance) | ![추가되지 않음](media/Red_X.gif) |
 | 드라이버 패키지 및 OS 이미지 사전 캐시 <!--4224642--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#bkmk_precache) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 OS 배포 <!--2839943,4447680--> | [Tech Preview 1904](/sccm/core/get-started/2019/technical-preview-1904#bkmk_osd) | ![추가되지 않음](media/Red_X.gif) |
 | 클라우드 서비스 비용 예측기 <!--3555774--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_cmg) | ![추가되지 않음](media/Red_X.gif) |
 | 전송 최적화를 위해 배포 지점을 로컬 캐시 서버로 사용 <!--3555764--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_doinc) | ![추가되지 않음](media/Red_X.gif) |
 | 작업 순서를 편집하기 위해 잠금 확보 <!--3699337--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_sedo) | ![추가되지 않음](media/Red_X.gif) |
 | 필수 업데이트 드릴스루 <!--4224414--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_req-updates) | ![추가되지 않음](media/Red_X.gif) |
 | 향상된 작업 순서 미디어 만들기 기능 <!--4090666--> | [Tech Preview 1903](/sccm/core/get-started/2019/technical-preview-1903#bkmk_tsmedia) | ![추가되지 않음](media/Red_X.gif) |


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
