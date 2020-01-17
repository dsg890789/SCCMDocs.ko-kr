---
title: 응용 프로그램 평가 기술 참조
titleSuffix: Configuration Manager
description: Configuration Manager에 대 한 응용 프로그램 평가 기술 참조 문제 해결
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: a7035223-d7bd-47b4-896f-08de3416a4eb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fff63f58ebc261f4d9aef42be7c9cbe24450938a
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821514"
---
# <a name="application-deployment-evaluation"></a>애플리케이션 배포 평가

*적용 대상: Configuration Manager(현재 분기)*

계속 하기 전에 [응용 프로그램 배포 클라이언트 구성 요소](/sccm/apps/understand/client-components-technical-reference) 를 검토 하 여 DCM 및 CI 에이전트 작업 처리를 이해 하세요.

응용 프로그램 평가는 배포를 활성화할 때 DCM 에이전트 및 CI 에이전트 구성 요소에 의해 수행 됩니다. 할당이 활성화 된 시기를 이해 하려면 [장치 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/device-deployment-technical-reference) 또는 [사용자 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/user-deployment-technical-reference) 문서를 참조 하세요.

## <a name="application-detection-and-evaluation"></a>응용 프로그램 검색 및 평가

응용 프로그램 평가는 CI 에이전트 작업의 **InvokingSdmMethod** 단계에서 수행 됩니다. 이 단계에서는 응용 프로그램이 장치에 설치 되어 있는지 여부를 확인 하기 위해 클라이언트가 응용 프로그램에 대해 정의 된 검색 방법을 평가 합니다. 이 활동은 배포 유형 고유 ID 또는 배포 유형 이름을 사용 하 여 **Appdiscovery** 에서 추적할 수 있습니다.

```text
Performing detection of app deployment type ConfigMgr Toolkit - Windows Installer (*.msi file)(ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44, revision 2) for system.
+++ Did not detect app deployment type ConfigMgr Toolkit - Windows Installer (*.msi file)(ScopeId_B63CEBE7-8A69-4FBE-994F-5AD0A8488D27/DeploymentType_1d49ef88-cf3b-42fa-b198-388d220ccb44, revision 2) for system.
```

> [!NOTE]
> 위의 예제에서는 msi 응용 프로그램이 장치에 설치 되어 있는지 확인 하 여 검색을 수행 하는 MSI 응용 프로그램을 검색 하는 방법을 보여 줍니다. 대체 검색 방법을 사용 하는 응용 프로그램의 경우 적절 한 검색 방법을 사용 하 여 응용 프로그램이 설치 되어 있는지 확인 합니다.

그런 다음 클라이언트는 배포 목적에 따라 응용 프로그램의 원하는 상태를 평가 합니다. 또한이 단계에서는 응용 프로그램에 응용 프로그램에 대해 적용 해야 하는 종속성 또는 교체 규칙이 있는지 여부도 검색 합니다. 이 활동은 응용 프로그램 및 배포 유형 고유 ID를 사용 하 여 **Appintenteval .log** 에서 추적할 수 있습니다.

<pre><code class="lang-text"># Available Application Deployment

[Application or DT Unique ID] :- <b>Current State = NotInstalled, Applicability = Applicable, ResolvedState = Available</b>, ConfigureState = NotNeeded, Title = [Application or DT Name]

# Required Application Deployment

[Application or DT Unique ID] :- <b>Current State = NotInstalled, Applicability = Applicable, ResolvedState = Installed</b>, ConfigureState = NotNeeded, Title = [Application or DT Name]

# Requirement Rules Not Met

[Application or DT Unique ID] :- <b>Current State = NotInstalled, Applicability = NotApplicable, ResolvedState = None</b>, ConfigureState = NotNeeded, Title = [Application or DT Name]
</code></pre>

위의 로그 항목에서 **현재 상태** 는 응용 프로그램이 현재 장치에 설치 되어 있는지 여부를 나타냅니다. **적용 가능성** 정의 된 요구 사항 규칙에 따라 응용 프로그램을 적용할 수 있는지 여부를 나타냅니다. **ResolvedState** 는 배포 목적에 따라 응용 프로그램의 원하는 상태를 나타냅니다.

> [!TIP]
> [배포 모니터링 도구](/sccm/core/support/deployment-monitoring-tool) 를 사용 하 여 응용 프로그램 상태, 적용 가능성 상태 및 요구 사항 위반을 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [애플리케이션 다운로드](/sccm/apps/understand/deployment-download-technical-reference)
