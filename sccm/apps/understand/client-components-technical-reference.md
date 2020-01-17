---
title: 응용 프로그램 배포 클라이언트 구성 요소 기술 참조
titleSuffix: Configuration Manager
description: Configuration Manager에서 응용 프로그램 배포 문제를 해결 하는 데 사용 되는 클라이언트 구성 요소입니다.
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: 701a3456-9dd6-4aaa-9c5a-37c1e1773216
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 692b705f7e24bf71aa05111cafce68647dfeef9f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75782050"
---
# <a name="understanding-application-deployment-client-components"></a>응용 프로그램 배포 클라이언트 구성 요소 이해

*적용 대상: Configuration Manager(현재 분기)*

응용 프로그램 배포 평가 및 적용 작업은 클라이언트의 DCM 에이전트 및 CI 에이전트 구성 요소에 의해 처리 됩니다. 이 문서에서는 일반적인 DCM 및 CI 에이전트 작업이 작동 하는 방식을 설명 합니다.

## <a name="dcm-agent"></a>DCM 에이전트

DCM 에이전트는 응용 프로그램을 포함 하는 구성 항목의 평가를 담당 하는 상위 수준의 클라이언트 구성 요소입니다. 배포를 활성화 하거나 적용 하면 할당 정책을 읽고 수행 해야 하는 작업을 결정 하는 DCM 에이전트 작업이 생성 됩니다. 응용 프로그램 고유 ID를 검색 하 여 식별할 수 있는 DCM 에이전트 작업 ID를 사용 하 여 클라이언트에서이 작업을 추적할 수 있습니다 **.**

### <a name="device-deployments"></a>장치 배포

- **필수** 배포의 경우에는 해당 작업이 해당 작업에 표시 됩니다. 이러한 작업은 배포 최종 기한이 이미 경과 되었는지 여부에 따라 다를 수 있습니다.

    ```text
    # Evaluation Job example:
    DCMAgentJob({A9E850E2-91B0-4122-94FD-D14EDF925AF7}): CDCMAgentJob::PopulateCIsFromAssignment - CI policy Id:ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/RequiredApplication_fc76ef0a-3ab0-4110-8cce-1addc36d0225 version:3 with actions: Evaluation, Content Download

    # Enforcement Job example:
    DCMAgentJob({4C8A9F6E-390B-450E-B505-B5698DB68EDD}): CDCMAgentJob::PopulateCIsFromAssignment - CI policy Id:ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/RequiredApplication_fc76ef0a-3ab0-4110-8cce-1addc36d0225 version:3 with actions: Evaluation, Install, Uninstall, Update, Look-ahead Install, Look-ahead Uninstall, Look-ahead Update
    ```

- **사용할 수** 있는 배포의 경우에는 배포 `is not mandatory`에 대 한 자세한 내용은 DCMAgent .log를 표시 합니다. 이러한 배포의 경우 응용 프로그램 평가가 수행 되지만 사용자가 설치를 시작 하지 않으면 적용을 건너뜁니다.

    ```text
    # Evaluation Job example:
    DCMAgentJob({E353BF94-D7ED-4ADD-AF0F-9273F6A67FC1}): CDCMAgentJob::PopulateCIsFromAssignment - [SCAN] CI policy Id :ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/RequiredApplication_fc76ef0a-3ab0-4110-8cce-1addc36d0225 version:3 - Assignment:{3AC57DFE-3F87-4C59-930B-B9F57CB41B91} is not mandatory.

    # Enforcement Job (user initiated) example:
    Request to enforce application ConfigMgr Toolkit(ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/Application_fc76ef0a-3ab0-4110-8cce-1addc36d0225.3) immediately for target: machine with action(s): Evaluation, Install, Update
    CDCMAgentJobMgr::CreateInteractiveJob - Queuing new job: {D331249E-F7DE-481B-A497-8E8B5E7B91C3}

    ```

### <a name="user-deployments"></a>사용자 배포

- **필수** 배포의 경우에는 해당 작업이 해당 작업에 표시 됩니다. 이러한 작업은 배포 최종 기한이 이미 경과 되었는지 여부에 따라 다를 수 있습니다.

    ```text
    # Evaluation Job example:
    DCMAgentJob({65D9688D-1781-4DA3-B07A-193D481251C6}): CDCMAgentJob::PopulateCIsFromAssignment - CI policy Id:ScopeId_C8F7EAE6-DBA8-4970-B3FF-47ED706868DE/RequiredApplication_6b39398b-fd20-47ca-bd68-074274509f98 version:2 with actions: Evaluation, Content Download

    # Enforcement Job example:
    DCMAgentJob({2B0DA272-FC65-4F31-9557-C4D840D650F1}): CDCMAgentJob::PopulateCIsFromAssignment - CI policy Id:ScopeId_C8F7EAE6-DBA8-4970-B3FF-47ED706868DE/RequiredApplication_6b39398b-fd20-47ca-bd68-074274509f98 version:2 with actions: Evaluation, Install, Uninstall, Update, Look-ahead Install, Look-ahead Uninstall, Look-ahead Update
    ```

- **사용 가능한** 배포의 경우 사용자가 응용 프로그램 설치를 시작할 때 평가 및 적용을 위해 DCM 에이전트 작업이 생성 됩니다.

    ```text
    # Evaluation Job example:
    DCMAgentJob({FBB44C84-DB06-41F7-8DC1-D9BA368F0C20}): CDCMAgentJob::PopulateCIsFromAssignment - [SCAN] CI policy Id :ScopeId_C8F7EAE6-DBA8-4970-B3FF-47ED706868DE/RequiredApplication_6b39398b-fd20-47ca-bd68-074274509f98 version:2 - Assignment:{7EA17128-EB4F-448A-88A7-B865E7DA228C} is not mandatory.

    # Enforcement Job example:
    CAppMgmtSDK::EnforceAppPolicy ScopeId_C8F7EAE6-DBA8-4970-B3FF-47ED706868DE/RequiredApplication_6b39398b-fd20-47ca-bd68-074274509f98.
    CDCMAgentJobMgr::CreateInteractiveJob - Queuing new job: {7936D7F3-24B0-401D-BADD-59EB5B49C2C2}
    ```

## <a name="ci-agent"></a>CI 에이전트

CI 에이전트는 구성 항목의 평가 및 수정을 담당 하는 클라이언트 구성 요소입니다. DCM 에이전트는 할당 정책을 읽고 요청 된 작업을 수행 하는 CI 에이전트 구성 요소에 대 한 작업을 만듭니다. **Dcmagent .log** 는 Ci 에이전트 작업 ID를 기록 합니다 .이 ID는 클라이언트의 **ciagent. 로그** 에서 ci 에이전트 작업을 추적 하는 데 유용 합니다.

<pre><code class="lang-text">DCMAgentJob({E353BF94-D7ED-4ADD-AF0F-9273F6A67FC1}): CDCMAgent::InitiateCIAgentJob - <b>Starting CI Agent Job</b> {57AF6FA1-3482-4469-9881-A63F41D18406} for target: machine. Refer to this CI agent job ID in ciagent.log for more details
</code></pre>

일반적인 CI 에이전트 작업은 여러 단계로 진행 됩니다 .이 작업은 CI 에이전트 작업 ID에 대해 log를 필터링 한 다음 `TransitionState`을 검색 하 여 확인할 수 있습니다 **.** 응용 프로그램 배포 CI 에이전트 작업에 대 한 몇 가지 주요 단계는 다음과 같습니다.

- **DownloadingCIs**
  - 이 단계에서 응용 프로그램을 평가 하는 데 필요한 응용 프로그램 메타 데이터가 다운로드 됩니다. 메타 데이터에는 검색 방법, 요구 사항 규칙, 글로벌 조건 등이 포함 됩니다. 이 활동은 **Cidownloader .log** 및 **datatransferservice.log와 pulldp.log**에서 추적할 수 있습니다. **사용 가능한** 배포의 경우이 프로세스는 응용 프로그램의 첫 번째 평가 중에 발생 합니다. 그러나 **필수** 배포의 경우이 프로세스는 정책이 다운로드 된 직후에 발생 합니다.

- **InvokingSdmMethod**
  - 이 단계에서는 응용 프로그램 검색 방법을 사용 하 여 응용 프로그램이 설치 되어 있는지 확인 하 고 필요한 상태를 확인 합니다. 이 활동은 **Appdiscovery .log** 및 **Appintenteval .log**에서 추적할 수 있습니다. 이 단계에 대 한 자세한 내용은 [응용 프로그램 평가](/sccm/apps/understand/deployment-evaluation-technical-reference)를 참조 하세요.

- **StateDownloadingContents**
  - 이 단계 중에는 필요한 경우 응용 프로그램 콘텐츠가 다운로드 됩니다. 이 활동은 Ca에서 추적할 수 있습니다 **. log**, **content전송자 관리자. .Log**, **locationservices**및. **DataTransferService.log** 이 단계에 대 한 자세한 내용은 [응용 프로그램 다운로드](/sccm/apps/understand/deployment-download-technical-reference)를 참조 하세요.

- **StateEnforcingCIs**
  - 이 단계에서 응용 프로그램 설치가 시작 됩니다. 이 활동은 **Appenforce .log**에서 추적할 수 있습니다. 이 단계에 대 한 자세한 내용은 [응용 프로그램 설치](/sccm/apps/understand/deployment-install-technical-reference)를 참조 하세요.

- **StateEnforcementReporting**
  - 이 단계에서 관리 지점에 보고 하기 위해 응용 프로그램 설치 상태가 기록 됩니다. 이 활동은 **StateMessage**에서 추적할 수 있습니다.

CI 에이전트 작업이 모든 단계를 진행 하지만 필요 하지 않은 경우 단계를 건너뜁니다. 예를 들어, **사용 가능한** 배포에 대해 StateDownloadingContents 및 StateEnforcingCIs 단계는 사용자가 소프트웨어 센터에서 응용 프로그램을 설치 하려고 할 때까지 건너뜁니다. 그러나 **필수** 배포의 경우 StateDownloadingContents 단계는 할당을 활성화할 때 응용 프로그램 콘텐츠 (필요한 경우)를 다운로드 하지만 최종 기한이 미래에 StateEnforcingCIs 단계는 건너뜁니다. 이 동작은 CI 에이전트 작업 ID를 필터링 하 고 `Skipping policy`을 검색 하 여 CIAgent에서 관찰할 수 있습니다.

```text
{57AF6FA1-3482-4469-9881-A63F41D18406} - Skipping policy CI <CI Unique ID> and all dependents for ContentDownload task since CI action was not requested.
{57AF6FA1-3482-4469-9881-A63F41D18406} - Skipping policy CI <CI Unique ID> and all dependents for Enforce task since CI action was not requested.
```

## <a name="next-steps"></a>다음 단계

- [애플리케이션 평가](/sccm/apps/understand/deployment-evaluation-technical-reference)
- [애플리케이션 다운로드](/sccm/apps/understand/deployment-download-technical-reference)
- [애플리케이션 설치](/sccm/apps/understand/deployment-install-technical-reference)
