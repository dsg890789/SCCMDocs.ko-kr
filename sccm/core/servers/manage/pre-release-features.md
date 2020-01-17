---
title: 시험판 기능
titleSuffix: Configuration Manager
description: 시험판 기능은 프로덕션 환경에서의 초기 테스트를 위해 현재 분기에 포함된 기능입니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 0142d8a6dbf2f7cbc23f14972ec5e536e946fc98
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75794549"
---
# <a name="pre-release-features-in-configuration-manager"></a>Configuration Manager 시험판 기능

*적용 대상: Configuration Manager(현재 분기)*

시험판 기능은 프로덕션 환경에서의 초기 테스트를 위해 현재 분기에 포함된 기능입니다. 이러한 기능은 완전히 지원되지만 아직 개발 과정에 있습니다. 시험판 범주에서 벗어날 때까지는 변경이 있을 수 있습니다.

## <a name="give-consent"></a>동의  

시험판 기능을 사용하려면 먼저 시험판 기능 사용에 대한 동의가 필요합니다. 동의는 실행 취소할 수 없고 계층 구조당 1회가 필요한 작업입니다. 동의할 때까지 업데이트에 포함된 새 시험판 기능을 사용하도록 설정할 수 없습니다. 시험판 기능을 설정한 후에는 해제할 수 없습니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 리본에서 **계층 구조 설정**을 클릭합니다.  

3. 계층 구조 설정 속성의 **일반** 탭에서 **시험판 기능 사용 동의** 옵션을 사용하도록 선택합니다. **확인**을 클릭합니다.  

## <a name="enable-pre-release-features"></a>시험판 기능 사용

시험판 기능이 포함된 업데이트를 설치하는 경우 이러한 기능은 업데이트에 포함된 일반 기능과 함께 업데이트 및 서비스 마법사에 표시됩니다.

### <a name="if-you-have-given-consent"></a>사용자가 동의하는 경우

업데이트 및 서비스 마법사에서 시험판 기능을 사용하도록 설정합니다. 다른 모든 기능에서와 마찬가지로 시험판 기능을 선택합니다.

또는 **관리** 작업 영역에서 **업데이트 및 서비스**의 **기능** 노드에서 나중에 시험판 기능을 사용하도록 설정하게 대기합니다. 기능을 선택한 다음, 리본 메뉴에서 **켜기**를 클릭합니다. 동의할 때까지 이 옵션을 사용할 수 없습니다.

### <a name="if-you-havent-given-consent"></a>사용자가 동의하지 않는 경우

업데이트 및 서비스 마법사에 시험판 기능이 표시는 되지만 사용하도록 설정할 수는 없습니다. 업데이트를 설치한 후에 **기능** 노드에서 이러한 기능을 볼 수 있습니다. 그러나 사용자가 동의할 때까지 사용하도록 설정할 수는 없습니다.

> [!IMPORTANT]  
> 다중 사이트 계층에서는 중앙 관리 사이트에서만 선택적 또는 시험판 기능을 활성화할 수 있습니다. 이 동작은 계층 전체에 충돌이 발생하지 않도록 합니다. <!--507197-->  
>
> 독립 실행형 기본 사이트에서 동의를 제공한 다음, 새 중앙 관리 사이트를 설치하여 계층 구조를 확장하는 경우 중앙 관리 사이트에서 다시 동의를 제공해야 합니다.  

시험판 기능을 사용하도록 설정하면 Configuration Manager HMAN(계층 구조 관리자)은 해당 기능을 사용할 수 있게 되기 전에 변경 내용을 처리해야 합니다. 변경 처리는 즉시 처리되는 경우가 많습니다. HMAN 처리 주기에 따라 완료에 최대 30분이 소요될 수 있습니다. 변경 처리 후에는 기능을 사용하기 전에 먼저 콘솔을 다시 시작합니다.

## <a name="bkmk_table"></a> 시험판 기능 목록

<!--Note/tip for target article

> [!Note]  
> In this version of Configuration Manager, <feature name> is a pre-release feature. To enable it, see [Pre-release features](/sccm/core/servers/manage/pre-release-features).  

> [!Tip]  
> This feature was first introduced in version 1702 as a [pre-release feature](/sccm/core/servers/manage/pre-release-features). Beginning with version 1906, it's no longer a pre-release feature.  

-->

<!-- With each current branch release, to help purge this list a bit, remove any entries that were added as a full feature in a version that's no longer supported -->
| 기능          | 시험판으로 추가됨 | 전체 기능으로 추가됨 |  
|------------------|----------------------|-------------------------|
| [작업 순서 배포](/sccm/osd/deploy-use/debug-task-sequence) <!--3612274,C3F37661-69E4-4D53-A39C-5D02F97E0E71--> | 버전 1906 | ![아직 추가되지 않음](media/red_x.png) |
| [애플리케이션 그룹](/sccm/apps/deploy-use/create-app-groups) <!--3555907,EE16A1D8-EF1B-4094-845F-AC107E7C621D--> | 버전 1906 | ![아직 추가되지 않음](media/red_x.png) |
| [Azure Active Directory 사용자 그룹 검색](/sccm/core/servers/deploy/configure/configure-discovery-methods#bkmk_azuregroupdisco) <!--3611956,023715E7-BFBA-4E9E-A80F-B5B626464ADD-->| 버전 1906 | ![아직 추가되지 않음](media/red_x.png) |
| [Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화](/sccm/core/clients/manage/collections/create-collections#bkmk_aadcollsync) <!--3607475,C2127144-C8DE-49F6-9CB3-D4F5B59F9515-->| 버전 1906| ![아직 추가되지 않음](media/red_x.png)|
| [CMPivot 독립 실행형](/sccm/core/servers/manage/cmpivot#bkmk_standalone) <!--3555890/4692885,no GUID--> | 버전 1906 | ![아직 추가되지 않음](media/red_x.png) |
| [SMS 공급자 관리 서비스](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_admin-service) <!--1359052--> | 버전 1810 | 버전 1906 |
| [향상된 HTTP 사이트 시스템](/sccm/core/plan-design/hierarchy/enhanced-http) <!--1356889,1358228--> | 버전 1806 | 버전 1810 |
| [공동 관리형 디바이스용 클라이언트 앱](/sccm/comanage/workloads#client-apps) <br/> (이전의 *공동 관리형 디바이스용 모바일 앱*) <!--1357892,CC3AE625-BF72-49B1-8AB1-AF0DCF2D6F4C--> | 버전 1806 | ![아직 추가되지 않음](media/red_x.png) |
| [SCAP 확장](/sccm/compliance/plan-design/scap/about-scap) <!--3607889--> | 버전 1806 | ![아직 추가되지 않음](media/red_x.png) |
| [Package Conversion Manager](/sccm/apps/pcm/package-conversion-manager) <!--1357861--> | 버전 1806 | 버전 1810 |
| [단계별 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence) <!--1356837--> | 1802 버전 | 버전 1806 |
| [Windows Defender Application Control 관리](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager) <!--3600958 (fka 1355092 & 1319346)--> | 버전 1702 | 버전 1906 |
| [클러스터 인식 컬렉션 서비스(서버 그룹 서비스)](/sccm/sum/deploy-use/service-a-server-group) <!--1081776,290B66D8-C735-4895-B59A-DD732D84A697--> | 버전 1602 | ![아직 추가되지 않음](media/red_x.png) |

<!--Image used = ![Not yet](media/red_x.png) -->

> [!TIP]  
> 사용하기 전에 활성화해야 하는 시험판 이외 기능에 대한 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  
>
> 기술 미리 보기 분기에만 제공되는 기능에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.  
