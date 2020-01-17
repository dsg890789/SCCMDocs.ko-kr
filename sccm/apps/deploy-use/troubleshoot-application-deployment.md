---
title: 앱 배포에 대 한 문제 해결 팁
titleSuffix: Configuration Manager
description: Configuration Manager에서 애플리케이션 배포 문제 해결을 위한 팁
ms.date: 05/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 4e8b46a3-3e11-475f-a4d7-6bf9ddf14145
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 696fd350d8fc98d1f84564c5e360af45a46c077e
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75817876"
---
# <a name="troubleshooting-tips-for-application-deployments"></a>응용 프로그램 배포에 대 한 문제 해결 팁

*적용 대상: Configuration Manager(현재 분기)*

애플리케이션 배포와 관련된 일반적인 문제는 다음 범주 중 하나에 속합니다.

- 애플리케이션 다운로드 실패

- 애플리케이션 배포 규정 준수가 0%에 고정됨

이러한 문제 중 하나가 발생하는 경우 이 문서에서는 문제를 해결하는 데 사용할 수 있는 몇 가지 단계를 제공합니다. 심층 문제 해결에 대 한 자세한 내용은 [응용 프로그램 배포 기술 참조 문제 해결](/sccm/apps/understand/app-deployment-technical-reference)을 참조 하세요.


## <a name="download-failures"></a>다운로드 실패

애플리케이션 다운로드 실패에는 다음과 같은 문제가 있습니다.

- 클라이언트가 애플리케이션 다운로드를 중단함

- 클라이언트가 애플리케이션 콘텐츠를 다운로드하지 못함

- 애플리케이션을 다운로드하는 동안 클라이언트가 0%에서 멈춤

애플리케이션 다운로드 오류가 발생할 때 가장 먼저 확인해야 할 것은 경계 및 경계 그룹의 누락 또는 잘못 구성 여부입니다. 예를 들어 클라이언트가 인트라넷에 있고 인터넷 전용 클라이언트 관리용으로 구성되지 않은 경우, 해당 네트워크 위치는 구성된 경계에 있어야 합니다. 클라이언트가 콘텐츠를 다운로드하려면 이 경계에 할당된 경계 그룹도 있어야 합니다. 자세한 내용은 [사이트 경계 및 경계 그룹 정의](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups)를 참조하세요.

클라이언트에 대한 경계를 구성할 수 없거나 특정 경계 그룹이 다른 경계 그룹의 멤버가 될 수 없는 경우:

1. Configuration Manager 콘솔에서 **배포 유형**의 속성을 엽니다.  

1. **콘텐츠** 탭으로 전환합니다.

1. 인접 경계 그룹 또는 기본 사이트 경계 그룹의 배포 지점을 사용하기 위한 섹션에서 **배포 옵션**을 **배포 지점에서 콘텐츠를 다운로드하고 로컬로 실행**으로 변경합니다. (기본적으로 이 설정은 **콘텐츠 다운로드 안함**입니다.)

클라이언트가 애플리케이션 콘텐츠를 다운로드할 수 없는 경우 배포 지점에 배포되었는지 확인합니다. 이 구성을 확인하려면 콘솔 내 기능을 사용하여 배포 지점에 대한 콘텐츠 배포를 모니터링합니다. 자세한 내용은 [배포한 콘텐츠 모니터링](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed)을 참조하세요.  


## <a name="compliance-stuck-at-0"></a>규정 준수가 0%에 고정됨

애플리케이션의 배포 규정 준수가 0%인 경우 **배포** 노드 아래의 **모니터링** 작업 영역에서 애플리케이션의 배포 상태를 확인합니다.

- **진행 중**: 클라이언트에서 [콘텐츠 다운로드](#download-failures)가 중단될 수 있습니다.

- **오류**: 이 문제를 해결하는 방법에 대한 자세한 내용은 다음 블로그 게시물을 참조하세요. [유용한 정보: 실패한 배포를 보고하는 자산에 대한 조치를 수행하는 방법](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Tips-and-Tricks-How-to-Take-Action-on-Assets-That-Report-a/ba-p/273019)

- **알 수 없음**: 이 상태는 일반적으로 클라이언트가 정책을 수신하지 못했음을 의미합니다. 클라이언트 정책을 수동으로 새로 고쳐 클라이언트가 정책을 수신하는지 확인합니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 정책 검색 시작](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.
  
이러한 작업을 수행해도 문제가 해결되지 않으면 클라이언트 상태를 확인합니다. 클라이언트와 관련된 더 깊은 근본적인 문제가 있을 수 있습니다. 자세한 내용은 [클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)을 참조하세요.


## <a name="next-steps"></a>다음 단계

- [애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)
- [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)
- [애플리케이션에 대한 관리 작업](/sccm/apps/deploy-use/management-tasks-applications)
- [애플리케이션 배포 기술 참조 문제 해결](/sccm/apps/understand/app-deployment-technical-reference)
