---
title: 응용 프로그램 다운로드 기술 참조
titleSuffix: Configuration Manager
description: Configuration Manager에 대 한 응용 프로그램 다운로드 기술 참조 문제 해결
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: 41c29a07-9bf6-4ec4-b3f2-1c05e001eff7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b7405112ee1114c1da8b0c5764045637012d7420
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75815581"
---
# <a name="application-download-in-configuration-manager"></a>Configuration Manager에서 응용 프로그램 다운로드

*적용 대상: Configuration Manager(현재 분기)*

계속 하기 전에 [응용 프로그램 배포 클라이언트 구성 요소](/sccm/apps/understand/client-components-technical-reference) 를 검토 하 여 DCM 및 CI 에이전트 작업 처리를 이해 하세요.

## <a name="download-initiation"></a>다운로드 시작

응용 프로그램 콘텐츠 다운로드는 **Statedownloadingcontents** 단계 중에 클라이언트의 CI 에이전트 구성 요소에 의해 시작 됩니다. 이 프로세스는 응용 프로그램이 장치 컬렉션 또는 사용자 컬렉션에 배포 되었는지 여부에 관계 없이 동일 합니다.

- **사용 가능한** 배포의 경우 사용자가 소프트웨어 센터에서 응용 프로그램 설치를 시작할 때 응용 프로그램 콘텐츠가 다운로드 됩니다.
- **필수** 배포의 경우 할당을 활성화 하 고 평가 후 해당 응용 프로그램을 찾을 때 응용 프로그램 콘텐츠가 다운로드 됩니다. 할당이 활성화 된 시기를 이해 하려면 [장치 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/device-deployment-technical-reference) 또는 [사용자 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/user-deployment-technical-reference) 문서를 참조 하세요.

CI 에이전트가 콘텐츠 다운로드를 시작 하면 CI 작업 관리자 구성 요소에서 처리 하는 작업을 만듭니다. 그런 다음 CI 작업 관리자에서 콘텐츠 다운로드를 시작 합니다. 이 활동은 배포 유형 고유 ID를 사용 하 여 CITaskMgr에서 추적할 수 있습니다 **.**

<pre><code class="lang-text"><b>Initiating task ContentDownload</b> for CI ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44.2 (ConfigMgr Toolkit - Windows Installer (*.msi file)) for target: , consumer: {53EA65C2-D596-4215-83E4-F7007B78E18C}
</code></pre>

## <a name="distribution-point-location"></a>배포 지점 위치

모든 다운로드 작업은 클라이언트 캐시 관리를 담당 하는 Content Access 구성 요소에 의해 처리 됩니다. 다운로드 작업을 만든 후 콘텐츠 액세스 구성 요소는 콘텐츠를 클라이언트 캐시에서 이미 사용할 수 있는지 확인 합니다. 콘텐츠를 사용할 수 없는 경우 콘텐츠를 가져올 수 있는 배포 지점 목록을 가져오는 위치 요청을 만듭니다. 이 활동은 콘텐츠 고유 ID를 사용 하 여 클라이언트에서 **CAS** 및 **locationservices .log** 에서 추적할 수 있습니다.

```text
Requesting locations synchronously for content Content_00a8f9e6-8e44-42f5-a0ef-9b5c86a88498.1 with priority Foreground
ContentLocationRequest : <Request XML Body>
Reply Message Body : <Reply XML Body>
```

> [!IMPORTANT]
> Location Services 구성 요소는 위치 요청을 처리 하지만 관리 지점에서 직접 위치를 요청 하지 않습니다. 관리 지점에 대 한 모든 요청은 일반적으로 **CcmMessaging**에 기록 되는 CCM 메시징 구성 요소를 통해 이동 합니다.

Location reply XML은 클라이언트의 경계 그룹을 기반으로 하는 배포 지점의 목록을 포함 합니다. 이 목록은 [콘텐츠 원본 우선 순위](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#content-source-priority)에 따라 클라이언트의 WMI에서 구문 분석 되 고 유지 됩니다. 콘텐츠 고유 ID를 사용 하 고 `Persisted location`을 검색 하 여 **Content전송자 관리자 .log**에서이 활동을 볼 수 있습니다. 

위치 회신 XML에 배포 지점이 포함 되지 않은 경우 **content\\.log** 는 `Received empty location update` 표시 하 고 클라이언트는 응용 프로그램을 다운로드 하는 동안 0%에서 중단 될 수 있습니다. 이 회신은 일반적으로 경계 그룹 구성 문제로 인해 발생할 수 있습니다. 자세한 내용은 [다운로드 실패](/sccm/apps/deploy-use/troubleshoot-application-deployment#download-failures)를 참조하세요.

## <a name="content-download"></a>콘텐츠 다운로드

배포 지점 위치를 가져오면 콘텐츠 액세스 구성 요소가 콘텐츠 전송 작업을 만듭니다. 이 활동은 콘텐츠 고유 ID를 사용 하 여 **ca .log** 에서 추적할 수 있습니다.

<pre><code class="lang-text">Submitted CTM job <b>{6D0EA720-EB4E-4893-8395-8B27470A6CFB}</b> to download Content <b>Content_00a8f9e6-8e44-42f5-a0ef-9b5c86a88498.1</b> under context System
</code></pre>

그런 다음 콘텐츠 전송 관리자는 콘텐츠 다운로드를 수행 하는 데이터 전송 서비스 작업을 만듭니다. 이 활동은 콘텐츠 고유 ID를 사용 하 여 클라이언트의 **Content전송자 관리자. log** 에서 추적할 수 있습니다.

<pre><code class="lang-text">CTM job <b>{6D0EA720-EB4E-4893-8395-8B27470A6CFB}</b> (corresponding DTS job <b>{708C7F21-8898-49AB-900E-BA6E5F1A39BC}</b>) started download from '<Distribution Point URL>/<b>Content_00a8f9e6-8e44-42f5-a0ef-9b5c86a88498.1</b>' for full content download.
</code></pre>

> [!NOTE]
> 이 로그 항목은 CTM 및 DTS 작업 ID를 식별 하는 데 사용할 수 있습니다 .이 ID는 각각 **ContentTransferManager.log** 및 **DataTransferService.log** 의 콘텐츠 전송 진행률을 추적 하는 데 사용할 수 있습니다.

데이터 전송 서비스는 BITS (Background Intelligent Transfer Service) 작업을 만들고 다운로드가 완료 될 때까지 대기 하 여 응용 프로그램 콘텐츠 다운로드를 수행 합니다. 이 활동은 **Contentdatatransferservice.log와 pulldp.log**에서 가져온 DTS 작업 ID를 사용 하 여 클라이언트의 **로그** 에서 추적할 수 있습니다.

<pre><code class="lang-text">Starting BITS job '{40263E01-2EDD-462F-ABBA-A5E892CB9229}' for DTS job '<b>{708C7F21-8898-49AB-900E-BA6E5F1A39BC}</b>' under user 'S-1-5-18'.
DTSJob <b>{708C7F21-8898-49AB-900E-BA6E5F1A39BC}</b> in state 'DownloadingData'.
DTS job <b>{708C7F21-8898-49AB-900E-BA6E5F1A39BC}</b> has completed
</code></pre>

다운로드가 완료 되 면 Content Access 구성 요소에 알림이 표시 됩니다. 그런 다음 콘텐츠 액세스 구성 요소는 다운로드 한 콘텐츠를 확인 하 여 다운로드 하는 동안 콘텐츠가 변경 되지 않도록 합니다. 이 활동은 콘텐츠 고유 ID를 사용 하 여 **ca .log** 에서 추적할 수 있습니다.

```text
Hash verification succeeded for content Content_00a8f9e6-8e44-42f5-a0ef-9b5c86a88498.1 downloaded under context System
```

마지막으로, 콘텐츠를 확인 한 후 CI 에이전트가 작업 완료 알림을 받고 CI 에이전트 작업이 다음 단계로 이동 합니다.

<pre><code class="lang-text">CIAgentJob({2BF84225-C9E8-49A6-A308-A160C4B799D3}): CAgentJob::HandleEvent(<b>Event=CITaskComplete, CurrentState=StateDownloadingContents</b>)
</code></pre>

## <a name="next-steps"></a>다음 단계

- [애플리케이션 설치](/sccm/apps/understand/deployment-install-technical-reference)
