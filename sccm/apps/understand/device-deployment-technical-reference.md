---
title: 장치 컬렉션에 대 한 앱 배포 기술 참조
titleSuffix: Configuration Manager
description: 장치 컬렉션에 대 한 응용 프로그램 배포 문제 해결 Configuration Manager에 대 한 기술 참조입니다.
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: 4e62b04d-fe56-42ed-87dc-e673cf061d52
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 608f1442990f5b202cd4449d46a69c1102e99723
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74823363"
---
# <a name="application-deployment-for-device-collections"></a>장치 컬렉션에 대 한 응용 프로그램 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

응용 프로그램을 장치 컬렉션에 배포 하는 경우 해당 정책은 배포 목적에 관계 없이 컬렉션에 있는 모든 장치를 대상으로 합니다. 이 문서에서는 클라이언트에서 정책 다운로드 및 배포를 처리 하는 방법을 설명 합니다.

> [!TIP]
> 클라이언트 로그를 검토 하는 데 필요한 모든 정보는 [시작 하기 전에](/sccm/apps/understand/app-deployment-technical-reference#before-you-begin) 섹션에서 참조 하는 SQL 쿼리를 실행 하 여 가져올 수 있습니다.

## <a name="policy-download"></a>정책 다운로드

응용 프로그램 배포에 대 한 정책이 클라이언트를 대상으로 지정 된 후 클라이언트는 다음 정책 폴링 주기에서 정책을 다운로드 합니다. 클라이언트는 정책을 다운로드할 때 배포 정책 외에도 관련 정책을 다운로드 합니다. 이러한 관련 정책에는 응용 프로그램에 대 한 정책, 배포 유형, 글로벌 조건 등이 포함 됩니다. 정책 다운로드 작업은 응용 프로그램 또는 할당 고유 ID를 사용 하 여 클라이언트의 **Policyagent** 에서 추적할 수 있습니다.

<pre><code class="lang-text">Download of policy CCM_Policy_Policy5.PolicyID="{<b>3AC57DFE-3F87-4C59-930B-B9F57CB41B91</b>}",PolicySource="SMS:PS1",PolicyVersion="1.00" completed (DTS Job ID: {AE88E639-0E59-40D7-AAA9-4403AAE6EE82})
Policy state for [CCM_Policy_Policy5.PolicyID="{<b>3AC57DFE-3F87-4C59-930B-B9F57CB41B91</b>}",PolicySource="SMS:PS1",PolicyVersion="1.00"] is currently [Active]
</code></pre>

클라이언트에서 정책을 다운로드 한 후에는 스케줄러 구성 요소가 배포 활성화 및 적용 일정을 만듭니다.

## <a name="deployment-activation"></a>배포 활성화

응용 프로그램 평가는 배포가 활성화 될 때 시작 됩니다. Scheduler 구성 요소는 배포에 구성 된 사용 가능한 시간에 할당을 활성화 하는 일정을 만듭니다. 이 작업은 응용 프로그램 할당 고유 ID를 사용 하 여 클라이언트의 Scheduler에서 추적할 수 있습니다 **.**

- **필수** 배포의 경우 활성화 일정이 만들어지지만, 사이트 서버 및 배포 지점의 리소스 경합을 방지 하는 데 최대 2 시간의 지연이 있습니다. 지연 시간을 사용 하면 정의 된 요구 사항 규칙에 따라 응용 프로그램을 적용할 수 있는 경우 평가 중에 응용 프로그램 콘텐츠를 다운로드할 수 있으므로 경합이 발생 하지 않습니다.

    <pre><code class="lang-text">SMSTrigger '15AF8C4000080000' for scheduler '<b>Machine/{5F2FA409-C9B2-4100-8BC8-051820311DE1}</b>' will fire at 08/15/2019 01:44:00 PM with randomization.
    </code></pre>

- **사용 가능한** 배포의 경우 배포에 구성 된 사용 가능한 시간에 활성화 일정이 발생 하도록 활성화 일정이 생성 됩니다.

    <pre><code class="lang-text">SMSTrigger '1E4F8C4000080001' for scheduler '<b>Machine/{3AC57DFE-3F87-4C59-930B-B9F57CB41B91}</b>' will fire at 08/15/2019 01:13:33 PM without randomization.
    </code></pre>

일정 시간이 도착 하면 Scheduler 구성 요소는 응용 프로그램 평가를 수행 하기 위해 활성화 메시지를 DCM 에이전트로 보냅니다.

<pre><code class="lang-text">Sending message for schedule '<b>Machine/{3AC57DFE-3F87-4C59-930B-B9F57CB41B91}</b>' (Target: 'direct:DCMAgent', Name: '')
</code></pre>

DCM 에이전트는 활성화 메시지를 받고 응용 프로그램을 평가 하는 작업을 만듭니다.

```text
CDCMAgent::HandleMessage - Message received for machine: '<?xml version='1.0' ?><CIAssignmentMessage MessageType='Activation'><AssignmentID>{3AC57DFE-3F87-4C59-930B-B9F57CB41B91}</AssignmentID></CIAssignmentMessage>'
```

## <a name="deployment-enforcement"></a>배포 적용

응용 프로그램 설치는 배포가 적용 될 때 시작 됩니다.

- **필수** 배포의 경우 스케줄러는 배포 최종 기한에 응용 프로그램을 적용 하기 위해 정책을 다운로드 한 후 최종 기한 일정을 만듭니다. 최종 기한 일정은 기본적으로 무작위로 아닙니다. [최종 기한 임의 설정 사용 안 함](/sccm/core/clients/deploy/about-client-settings#disable-deadline-randomization) 클라이언트 설정에서 활성화에 대 한 임의 설정 동작을 제어할 수 있습니다.

    <pre><code class="lang-text">SMSTrigger '15EF8C4000080000' for scheduler '<b>Machine/DEADLINE:{5F2FA409-C9B2-4100-8BC8-051820311DE1}</b>' will fire at 08/15/2019 03:05:00 PM without randomization.
    </code></pre>

    최종 기한에 Scheduler 구성 요소는 최종 기한 메시지를 DCM 에이전트로 보냅니다. 

    <pre><code class="lang-text">Sending message for schedule '<b>Machine/DEADLINE:{5F2FA409-C9B2-4100-8BC8-051820311DE1}</b>' (Target: 'direct:DCMAgent', Name: '')
    </code></pre>

    DCM 에이전트는 최종 기한 메시지를 받고 응용 프로그램을 적용 하는 작업을 만듭니다.
  
    ```text
    CDCMAgent::HandleMessage - Message received for machine: '<?xml version='1.0' ?><CIAssignmentMessage MessageType='EnforcementDeadline'><AssignmentID>{5F2FA409-C9B2-4100-8BC8-051820311DE1}</AssignmentID></CIAssignmentMessage>'
    ```

    > [!NOTE]
    > 과거 최종 기한이 있는 배포의 경우 응용 프로그램이 평가, 다운로드 및 설치 작업을 수행 하는 동일한 DCM 에이전트 작업에 의해 즉시 활성화 되 고 적용 됩니다.

- **사용 가능한** 배포의 경우 소프트웨어 센터에서 사용자가 응용 프로그램 설치를 시작할 때 적용 되는 최종 기한 일정이 없습니다. 사용자가 설치를 시작 하면 응용 프로그램 평가, 다운로드 및 설치를 수행 하는 DCM 에이전트 작업이 만들어집니다. 이 활동은 클라이언트의 **Dcmagent .log** 에서 추적할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [응용 프로그램 배포 클라이언트 구성 요소 이해](/sccm/apps/understand/client-components-technical-reference)
