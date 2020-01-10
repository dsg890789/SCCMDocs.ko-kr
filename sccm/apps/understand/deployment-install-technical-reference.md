---
title: 응용 프로그램 설치 기술 참조
titleSuffix: Configuration Manager
description: 응용 프로그램 설치 문제 해결 Configuration Manager에 대 한 기술 참조입니다.
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: 2af4f9c3-16b8-4691-a59d-aea6241d288e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 09d86e57d5bef1fccf3220be1ed79811985fe1fc
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75818369"
---
# <a name="application-installation"></a>애플리케이션 설치

*적용 대상: Configuration Manager(현재 분기)*

계속 하기 전에 [응용 프로그램 배포 클라이언트 구성 요소](/sccm/apps/understand/client-components-technical-reference) 를 검토 하 여 DCM 및 CI 에이전트 작업 처리를 이해 하세요.

응용 프로그램 설치는 배포가 적용 될 때 DCM 에이전트 및 CI 에이전트 구성 요소에 의해 수행 됩니다. 적용 시간은 사용 가능한 배포와 필수 배포에 따라 다릅니다. 할당이 적용 되는 시기를 이해 하려면 [응용 프로그램을 장치 컬렉션에 배포](/sccm/apps/understand/device-deployment-technical-reference) 또는 [사용자 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/user-deployment-technical-reference) 문서를 참조 하세요.

## <a name="enforcement-initiation"></a>적용 시작

응용 프로그램 설치는 **StateEnforcingCIs** 단계에서 클라이언트의 CI 에이전트 구성 요소에 의해 시작 됩니다. 이 프로세스는 응용 프로그램이 장치 컬렉션 또는 사용자 컬렉션에 배포 되었는지 여부에 관계 없이 동일 합니다.

- **사용 가능한** 배포의 경우 사용자가 소프트웨어 센터에서 응용 프로그램 설치를 시작할 때 응용 프로그램이 설치 됩니다.
- **필수** 배포의 경우 응용 프로그램은 배포 최종 기한에 설치 됩니다. 그러나 사용자는 최종 기한 전에 소프트웨어 센터에서 설치를 시작할 수 있습니다.

CI 에이전트가 응용 프로그램 설치를 시작 하면 CI 작업 관리자 구성 요소에서 처리 하는 작업을 만듭니다. 그런 다음 CI 작업 관리자에서 설치를 시작 합니다. 이 활동은 배포 유형 고유 ID를 사용 하 여 CITaskMgr에서 추적할 수 있습니다 **.**

<pre><code class="lang-text"><b>Initiating task Enforce</b> for CI ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44.2 (ConfigMgr Toolkit - Windows Installer (*.msi file)) for target: , consumer: {9BC3154A-98F1-4595-A967-173D536A3F94}
Initiated application enforcement. : CITask(ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44.2..Install.Enforce)
</code></pre>

## <a name="application-enforcement"></a>응용 프로그램 적용

응용 프로그램 적용을 시작한 후에 클라이언트는 응용 프로그램 검색을 다시 수행 하 여 응용 프로그램이 아직 설치 되지 않았는지 확인 합니다. 응용 프로그램이 설치 되지 않은 것으로 확인 되 면 응용 프로그램 설치가 시작 됩니다. 이 활동은 배포 유형 고유 ID를 사용 하 여 클라이언트의 **Appenforce. 로그** 에서 추적할 수 있습니다.

```text
+++ Starting Install enforcement for App DT "ConfigMgr Toolkit - Windows Installer (*.msi file)" ApplicationDeliveryType - ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44, Revision - 2, ContentPath - C:\WINDOWS\ccmcache\2, Execution Context - System
    Executing Command line: "C:\WINDOWS\system32\msiexec.exe" /i "ConfigMgrTools.msi" /q /qn with user context
    Process 7292 terminated with exitcode: 0
Status is switching to Success
```

## <a name="installation-verification"></a>설치 확인

응용 프로그램을 설치한 후 응용 프로그램이 설치 된 것으로 검색 되도록 응용 프로그램 검색 방법을 다시 사용 합니다.

<pre><code class="lang-text">Performing detection of app deployment type ConfigMgr Toolkit - Windows Installer (*.msi file)(ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44, revision 2) for system.
+++ <b>Discovered MSI application</b> [AppDT Id: ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44, Revision: 2, MSI Product code: {4FFF7ECC-CCF7-4530-B938-E7812BB91186}, MSI Product version: ]
++++++ <b>App enforcement completed</b> (3 seconds) for App DT "ConfigMgr Toolkit - Windows Installer (*.msi file)" [ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44], Revision: 2, User SID: ] ++++++
</code></pre>

마지막으로, 적용이 완료 되 면 CI 에이전트가 작업 완료 알림을 수신 하 고 CI 에이전트 작업이 다음 단계로 이동 합니다.

<pre><code class="lang-text">CIAgentJob({2BF84225-C9E8-49A6-A308-A160C4B799D3}): CAgentJob::HandleEvent(<b>Event=CITaskComplete, CurrentState=StateEnforcingCIs</b>)
</code></pre>

## <a name="next-steps"></a>다음 단계

[애플리케이션 배포 문제 해결](/sccm/apps/deploy-use/troubleshoot-application-deployment)
