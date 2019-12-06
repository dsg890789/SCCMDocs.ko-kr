---
title: 기술 미리 보기 1706
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1706에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 09/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ca3b4714-2a16-495e-8a17-1d87991d5556
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e7a13e53e4054593310378b5f667fd91c597448
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67677442"
---
# <a name="capabilities-in-technical-preview-1706-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1706의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1706에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
- **Issue Name**. Details
    Workaround details.
-->
**이 Technical Preview의 알려진 문제:**

- **배포 지점 이동** - 사이트 간에 배포 지점을 이동하기 위한 콘솔의 옵션은 단일 기본 사이트의 Technical Preview 제한으로 인해 이 릴리스에서 사용할 수 없습니다.

- **디바이스 준수 설정** - 새 디바이스 준수 설정 중 다음 2가지를 사용할 경우 반대 동작이 발생할 수 있습니다.
  - **디바이스에서 USB 디버깅 차단**
  - **알 수 없는 출처의 앱 차단**

    예를 들어 관리자가 **디바이스에서 USB 디버깅 차단**을 **true**로 설정하면 USB 디버깅이 사용되도록 설정되지 않은 모든 디바이스가 비규격으로 표시됩니다.

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improved-boundary-groups-for-software-update-points"></a>소프트웨어 업데이트 지점에 대한 향상된 경계 그룹
<!-- 1324591 -->
이 릴리스에서는 소프트웨어 업데이트 지점이 경계 그룹과 작동하는 방식이 개선되었습니다. 다음은 새로운 대체 동작을 요약해서 설명합니다.
- 이제 소프트웨어 업데이트 지점에 대한 대체는 인접 경계 그룹으로의 대체에 대해 구성 가능한 시간(최소 시간 120분)을 사용합니다.

- 대체 구성과 관계 없이, 클라이언트는 사용한 마지막 소프트웨어 업데이트 지점에 120분 이내에 도달하려고 합니다. 120분 내에 해당 서버에 도달하지 못하면 클라이언트는 사용 가능한 소프트웨어 업데이트 지점 풀을 확인하여 새 서버를 찾으려고 합니다.

  - 클라이언트의 현재 경계 그룹의 모든 소프트웨어 업데이트 지점이 클라이언트의 풀에 즉시 추가됩니다.

  - 클라이언트를 새 서버를 검색하기 전에 120분 동안 원본 서버로 사용하려고 하기 때문에 2시간이 지날 때까지 추가 서버에 연결되지 않습니다.

  - 인접 그룹에 대한 대체가 최소 120분으로 구성된 경우 해당 인접 경계 그룹에서의 소프트웨어 업데이트 지점은 사용 가능한 서버의 클라이언트의 풀에 포함됩니다.

- 2시간 내에 원래 서버에 도달하지 못하면 클라이언트는 새 소프트웨어 업데이트 지점에 연결하기 위해 더 짧은 주기로 전환합니다.

  즉, 클라이언트가 새 서버에 연결하지 못할 경우 사용 가능한 서버 풀의 다음 서버를 빠르게 선택하고 해당 서버에 연결하려고 합니다.

  - 이 주기는 클라이언트가 사용할 수 있는 소프트웨어 연결 지점에 연결할 때까지 계속됩니다.
  - 클라이언트가 소프트웨어 업데이트 지점을 찾을 때까지 각 인접 경계 그룹에 대한 대체 시간 범위 내에서 추가 서버가 사용 가능한 서버 풀에 추가됩니다.

자세한 내용은 현재 분기에 대한 경계 그룹 항목에서 [소프트웨어 업데이트 지점](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)을 참조하세요.


## <a name="site-server-role-high-availability"></a>사이트 서버 역할 고가용성
<!-- 1128774 -->
사이트 서버 역할에 대한 고가용성은 추가 기본 사이트 서버를 *수동* 모드에서 설치하기 위한 Configuration Manager 기반 솔루션입니다. 수동 모드 사이트 서버는 *활성* 모드의 기존의 기본 사이트 서버 외의 추가 서버입니다. 수동 모드 사이트 서버는 필요할 때 즉시 사용할 수 있습니다.

수동 모드의 기본 사이트 서버:
- 활성 사이트 서버와 동일한 사이트 데이터베이스를 사용합니다.
- 활성 사이트 서버의 콘텐츠 라이브러리의 복사본을 검색합니다. 이 복사본은 동기화된 상태로 유지됩니다.
- 수동 모드에서는 사이트 데이터베이스에 데이터를 쓰지 않습니다.
- 수동 모드에서는 선택적 사이트 시스템 역할의 설치 또는 제거가 지원되지 않습니다.

수동 모드 사이트 서버를 활성 모드 사이트 서버로 지정하려면 수동으로 수준을 올립니다. 이렇게 하면 활성 사이트 서버가 수동 사이트 서버로 전환됩니다. 원래 활성 모드인 서버에서 사용할 수 있는 사이트 시스템 역할은 컴퓨터에 액세스할 수 있기만 하면 사용 가능한 상태로 유지됩니다. 사이트 서버 역할만 활성 모드와 수동 모드 간에 전환됩니다.

수동 모드 사이트 서버를 설치하려면 **사이트 시스템 서버 만들기 마법사**를 사용하여 유형이 **기본 사이트 서버**이고 모드가 **수동**인 새 사이트 서버를 구성합니다. 그러면 마법사는 지정된 서버에서 Configuration Manager 설치 프로그램을 실행하여 수동 모드에서 새 사이트 서버를 설치합니다. 설치가 완료되면 활성 모드 사이트 서버는 수동 모드 사이트 서버로 유지되고 해당 콘텐츠 라이브러리는 활성 사이트 서버에 대해 수행한 변경 또는 구성 내용과 동기화된 상태로 유지됩니다.

### <a name="prerequisites-and-limitations"></a>필수 구성 요소 및 제한 사항
- 수동 모드의 단일 사이트 서버는 각 기본 사이트에서 지원됩니다.

- 수동 모드의 사이트 서버는 Azure에서 온-프레미스 또는 클라우드 기반일 수 있습니다.

- 활성 모드 및 수동 모드 사이트 서버 둘 다 동일한 도메인에 있어야 합니다.

- 활성 모드 및 수동 모드 사이트 서버 둘 다 각 사이트 서버 컴퓨터에서 원격 위치에 있는 동일한 사이트 데이터베이스를 사용해야 합니다.

    - 데이터베이스를 호스트하는 SQL Server는 기본 인스턴스, 명명된 인스턴스, SQL Server 클러스터 또는 Always On 가용성 그룹을 사용할 수 있습니다.

    - 수동 모드의 사이트 서버는 활성 모드 사이트 서버와 동일한 사이트 데이터베이스를 사용하도록 구성됩니다. 그러나 수동 모드 사이트 서버는 활성 모드로 수준을 올릴 때까지 해당 데이터베이스를 사용하지 않습니다.

- 수동 모드 사이트 서버를 실행하는 컴퓨터에는 다음이 적용됩니다.

    - [기본 사이트를 설치하기 위한 필수 구성 요소](https://docs.microsoft.com/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#primary-sites-and-the-central-administration-site)를 충족해야 합니다.

    - 활성 모드 사이트 서버의 버전과 일치하는 원본 파일을 사용하여 설치됩니다.

    - 수동 모드 사이트를 설치하기 전에는 어떤 사이트의 사이트 시스템 역할도 가질 수 없습니다.

- 활성 및 수동 모드 사이트 서버 컴퓨터는 사용 중인 Configuration Manager 버전에서 지원될 경우 다른 운영 체제 또는 서비스 팩 버전을 실행할 수 있습니다.

- 활성 모드 사이트 서버에서 수동 모드 서버로의 수준 올리기는 수동으로 수행됩니다. 자동 장애 조치(failover)는 없습니다.

- 활성 모드에 있는 사이트 서버에만 사이트 시스템 역할을 설치할 수 있습니다.

    - 활성 모드의 사이트 서버는 모든 사이트 시스템 역할을 지원합니다. 수동 모드일 때는 서버에서 사이트 시스템 역할을 설치할 수 없습니다.

    - 데이터베이스를 사용하는 사이트 시스템 역할(예: 보고 지점)의 경우 활성 모드 및 수동 모드 사이트 서버 둘 다에서 원격인 서버에 해당 데이터베이스가 있어야 합니다.

    - SMS_Provider는 수동 모드로 사이트 서버에 설치되지 않습니다. 사이트에서 수동 모드 사이트 서버를 수동으로 활성 모드로 수준을 올리려면 SMS_Provider에 연결해야 하므로 추가 컴퓨터에 [공급자의 추가 인스턴스를 하나 이상 설치](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)하는 것이 좋습니다.

**알려진 문제**:   
이 릴리스에서 다음 조건에 대한 **상태**가 읽을 수 있는 텍스트 대신 숫자 값으로 콘솔에 표시됩니다.
- 131071 – 사이트 서버 설치 실패
- 720895 – 사이트 서버 역할 제거 실패
- 851967 – 장애 조치(failover) 실패

### <a name="add-a-site-server-in-passive-mode"></a>수동 모드로 사이트 서버 추가
1. 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동한 후 [사이트 시스템 역할 추가 마법사](/sccm/core/servers/deploy/configure/install-site-system-roles)를 시작합니다. **사이트 시스템 서버 만들기 마법사**를 사용할 수도 있습니다.

2. **일반** 페이지에서 수동 모드 사이트 서버를 호스트하는 서버를 지정합니다. 지정한 서버는 수동 모드에서 사이트 서버를 설치하기 전에는 사이트 시스템 역할을 호스트할 수 없습니다.

3. **시스템 역할 선택** 페이지에서 **수동 모드의 기본 사이트 서버**만 선택합니다.

4. 마법사를 완료하려면 설치 프로그램을 실행하고 지정된 서버에서 사이트 서버 역할을 설치하는 데 사용되는 다음 정보를 제공해야 합니다.
    - 활성 사이트 서버에서 새 수동 모드 사이트 서버로 설치 파일을 복사하거나 활성 사이트 서버의 **CD.Latest** 폴더 콘텐츠를 포함하는 위치의 경로를 지정합니다.

    - 활성 모드 사이트 서버에서 사용되는 것과 동일한 사이트 데이터베이스 서버 및 데이터베이스 이름을 지정합니다.

5. 그러면 Configuration Manager는 수동 모드에서 사이트 서버를 지정된 서버에 설치합니다.

자세한 설치 상태에 대해 알아보려면 **관리** > **사이트 구성** > **사이트**로 이동합니다.
- 수동 모드의 사이트 서버 상태는 **설치 중**으로 표시됩니다.

- 자세한 내용을 보려면 서버를 선택한 다음 **상태 표시**를 클릭하여 **사이트 서버 설치 상태**를 엽니다.



### <a name="promote-the-passive-mode-site-server-to-active-mode"></a>수동 모드 사이트 서버를 활성 모드로 수준 올리기
수동 모드 사이트 서버를 활성 모드로 변경하려는 경우 **관리** > **사이트 구성** > **사이트**의 **노드** 창에서 수행합니다. SMS_Provider의 인스턴스에 액세스할 수만 있으면 해당 사이트에 액세스하여 이러한 변경을 수행할 수 있습니다.
1. Configuration Manager 콘솔의 **노드** 창에서 수동 모드의 사이트 서버를 선택한 다음 리본에서 **활성으로 수준 올리기**를 선택합니다.

2. 수준을 올리려는 서버의 간단한 **상태**가 **노드** 창에서 **수준 올리기**로 표시됩니다.

3. 수준 올리기가 끝나면 새 *활성* 모드 사이트 서버 및 새 *수동* 모드 사이트 서버 둘 다의 **상태** 열에 **확인**이 표시됩니다.

4. **관리** > **사이트 구성** > **사이트**에서 이제 기본 사이트 서버의 이름에 새 *활성* 모드 사이트 서버의 이름이 표시됩니다.
자세한 상태를 보려면 **모니터링** > **사이트 서버 상태**로 이동합니다.
    - **모드** 열에는 *활성* 또는 *수동* 서버가 식별됩니다.

    - 수동 모드에서 활성 모드로 서버의 수준을 올리는 경우 활성으로 수준을 올리려는 사이트 서버를 선택하고 리본에서 **상태 표시**를 선택합니다. 이렇게 하면 프로세스에 대한 추가 세부 정보를 표시하는 **사이트 서버 수준 올리기 상태** 창이 열립니다.

활성 모드의 사이트 서버가 수동 모드로 전환될 경우 사이트 시스템 역할만 수동으로 지정됩니다. 해당 컴퓨터에 설치된 다른 모든 사이트 시스템은 활성 상태를 유지하며 클라이언트에서 액세스할 수 있습니다.


### <a name="daily-monitoring"></a>일별 모니터링
기본 사이트가 수동 모드인 경우 매일 모니터링하여 활성 모드 사이트 서버와 동기화된 상태로 유지하고 사용할 수 있는 상태가 되도록 합니다. 이렇게 하려면 **모니터링** > **사이트 서버 상태**로 이동합니다. 여기서 활성 모드 및 수동 모드 사이트 서버 둘 다를 확인할 수 있습니다.

**요약** 탭:
- **모드** 열에는 활성 또는 수동 서버가 식별됩니다.
- 수동 모드 서버가 활성 모드 서버와 동기화되면 **상태** 열에는 목록을 **확인**이 표시됩니다.
- 콘텐츠 동기화 상태에 대한 추가 세부 정보를 보려면 콘텐츠 동기화 상태에서 **상태 표시**를 클릭합니다. 이렇게 하면 콘텐츠 동기화 문제를 해결할 수 있는 콘텐츠 라이브러리 탭이 열립니다.

**콘텐츠 라이브러리** 탭에서 다음을 수행합니다.
- 활성 사이트 서버에서 수동 모드 사이트 서버로 동기화되는 콘텐츠의 **상태**를 봅니다.
- 상태가 **실패**인 콘텐츠를 선택하고 리본 메뉴에서 **선택한 항목 동기화**를 선택할 수 있습니다. 이렇게 하면 콘텐츠 원본에서 해당 콘텐츠를 수동 모드 사이트 서버와 다시 동기화하려고 시도합니다. 복구 동안에는 상태가 **진행 중**으로 표시되고, 동기화된 후에는 **성공**으로 표시됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
다음 작업을 완료한 다음 리본 메뉴의 **홈** 탭에서 **사용자 의견**을 전송하여 작동 상황을 알려주세요.
- 기본 사이트는 수동 모드로 설치할 수 없습니다.
- 콘솔을 사용하여 수동 모드 사이트 서버를 활성 모드 사이트 서버로 수준을 올릴 수 있으며 두 사이트 서버의 상태 변경 결과를 확인할 수 있습니다.


## <a name="include-trust-for-specific-files-and-folders-in-a-device-guard-policy"></a>특정 파일 및 폴더에 대한 트러스트를 Device Guard 정책에 포함
<!-- 1324676 -->
이 릴리스에서는 [Device Guard](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager) 정책 관리에 기능이 추가되었습니다.

이제 Device Guard 정책에서 필요에 따라 폴더의 특정 파일에 대해 트러스트를 추가할 수 있습니다. 이를 통해 다음을 수행할 수 있습니다.

1. 관리되는 설치 관리자 동작 문제 해결
2. Configuration Manager로 배포할 수 없는 LOB(기간 업무) 앱 신뢰
3. 운영 체제 배포 이미지에 포함된 앱 신뢰

### <a name="try-it-out"></a>기능 직접 사용해 보기

1. Device Guard 정책을 만드는 동안 Device Guard 정책 만들기 마법사의 포함 탭에서 **추가**를 클릭합니다.
2. **신뢰할 수 있는 파일 또는 폴더 추가** 대화 상자에서 신뢰하려는 파일 또는 폴더에 대한 정보를 지정합니다. 로컬 파일 또는 폴더 경로를 지정하거나 연결할 수 잇는 권한이 있는 원격 디바이스에 연결한 후 해당 디바이스의 파일 또는 폴더 경로를 지정할 수 있습니다.
3. 마법사를 완료합니다.


## <a name="hide-task-sequence-progress"></a>작업 순서 진행률 숨기기
<!-- 1354291 -->
이 릴리스에서는 새 변수를 사용하여 최종 사용자에게 작업 순서 진행률이 표시되는 시기를 제어할 수 있습니다. 작업 순서에서 **작업 순서 변수 설정** 단계를 사용하여 작업 순서 진행률을 표시하거나 숨기도록 **TSDisableProgressUI** 변수의 값을 설정합니다. 한 작업 순서에서 작업 순서 변수 설정 단계를 여러 번 사용하여 변수 값을 변경할 수 있습니다. 이렇게 하면 작업 순서 진행률을 작업 순서의 여러 섹션에서 숨기거나 표시할 수 있습니다.

#### <a name="to-hide-task-sequence-progress"></a>작업 순서 진행률을 숨기려면
작업 순서 진행률을 숨기려면 작업 순서 편집기에서 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계를 사용하여 **TSDisableProgressUI** 변수를 **True**로 설정합니다.

#### <a name="to-display-task-sequence-progress"></a>작업 순서 진행률을 표시하려면
작업 순서 진행률을 표시하려면 작업 순서 편집기에서 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계를 사용하여 **TSDisableProgressUI** 변수를 **False**로 설정합니다.

## <a name="specify-a-different-content-location-for-install-content-and-uninstall-content"></a>설치 콘텐츠 및 제거 콘텐츠에 대해 다른 콘텐츠 위치 지정
<!-- 1097546 -->
이제 Configuration Manager에서 앱에 대한 설치 파일을 포함하는 설치 위치를 지정합니다. 설치 위치를 지정하면 애플리케이션 콘텐츠에 대한 제거 위치로도 사용됩니다.
사용자 의견에 따르면 배포된 애플리케이션을 제거하려고 하고 앱 콘텐츠가 클라이언트 컴퓨터에 없는 경우 클라이언트가 애플리케이션이 제거되기 전에 모든 앱 설치 파일을 다시 다운로드됩니다.
이 문제를 해결하기 위해 이제 설치 콘텐츠 위치 및 선택적 제거 콘텐츠 위치를 둘 다 지정할 수 있습니다. 또한 제거 콘텐츠 위치를 지정하지 않도록 선택할 수도 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

1. 애플리케이션의 배포 유형 속성에서 **콘텐츠** 탭을 클릭합니다.
2. 평소처럼 **설치 콘텐츠 위치**를 구성합니다.
3. **제거 콘텐츠 설정**에서 다음 중 하나를 선택합니다.
   - **설치 콘텐츠와 같음** - 애플리케이션을 설치하든, 제거하든 관계없이, 동일한 콘텐츠 위치가 사용됩니다.
   - **제거 콘텐츠 없음** - 애플리케이션에 대해 제거 콘텐츠 위치는 제공하지 않으려면 이 옵션을 선택합니다.
   - **설치 콘텐츠와 다름** - 설치 콘텐츠 위치와 다른 제거 콘텐츠 위치를 지정하려면 이 옵션을 선택합니다.
5. **설치 콘텐츠와 다름**을 선택한 경우 애플리케이션을 제거하는 데 사용할 애플리케이션 콘텐츠의 위치를 찾아 이동하거나 입력합니다.
6. **확인**을 클릭하여 배포 유형 속성 대화 상자를 닫습니다.


## <a name="accessibility-improvements"></a>향상된 접근성 기능  
<!--1253000 -->
이 미리 보기에서는 Configuration Manager 콘솔의 [접근성 기능](/sccm/core/understand/accessibility-features)이 일부 개선되었습니다. 여기에는 다음이 포함됩니다.     

**콘솔에서 이동하기 위한 새 바로 가기 키:**
- Ctrl+M - 주(가운데) 창에 포커스를 설정합니다.
- Ctrl+T - 탐색 창에서 최상위 노드에 포커스를 설정합니다. 포커스가 이미 해당 창에 있는 경우 포커스는 마지막으로 방문한 노드로 설정됩니다.
- Ctrl+I - 리본 메뉴 바로 아래의 이동 경로 탐색 막대로 포커스를 설정합니다.
- Ctrl+L - 사용 가능한 경우 **검색** 필드로 포커스를 설정합니다.
- Ctrl+D - 사용 가능한 경우 세부 정보 창으로 포커스를 설정합니다.
- Alt - 포커스를 리본 메뉴 안 및 밖으로 변경합니다.

**일반적인 개선 사항:**
- 노드 이름의 문자를 입력할 때 탐색 창의 탐색이 개선되었습니다.
- 주 보기 및 리본 메뉴 간의 키보드 탐색이 순환됩니다.
- 세부 정보 창의 키보드 탐색이 순환됩니다. 이전 개체 또는 창으로 돌아가려면 Ctrl+D를 누른 다음 Shift+탭을 누릅니다.
- 작업 영역 보기를 새로 고치면 포커스가 작업 영역의 주 창으로 설정됩니다.
- 화면 판독기에서 목록 항목의 이름이 표시되는 문제가 수정되었습니다.
- 화면 판독기에 중요한 정보를 표시할 수 있도록 하는 페이지의 여러 컨트롤에 대한 액세스 가능 이름이 추가되었습니다.


## <a name="changes-to-the-azure-services-wizard-to-support-upgrade-readiness"></a>업그레이드 준비 상태를 지원하기 위한 Azure 서비스 마법사 변경
<!-- 1353331 -->
이 릴리스부터 Azure 서비스 마법사를 사용하여 Configuration Manager에서 [업그레이드 준비 상태](/sccm/core/clients/manage/upgrade/upgrade-analytics)로의 연결을 구성할 수 있습니다. 이 마법사를 사용하면 관련 Azure 서비스에 대한 공통 마법사를 사용하여 커넥터의 구성을 간소화할 수 있습니다.   

연결을 구성하는 방법이 변경되었으나 연결의 필수 구성 요소 및 업그레이드 준비 상태를 사용하는 방법은 동일합니다.   

### <a name="prerequisites-for-upgrade-readiness"></a>업그레이드 준비 상태에 대한 필수 구성 요소
[업그레이드 준비 상태에 연결](/sccm/core/clients/manage/upgrade-readiness#connect-configuration-manager-to-upgrade-readiness)하기 위한 필수 구성 요소는 Configuration Manager의 현재 분기에 대한 필수 구성 요소에서 달라지지 않았습니다. 여기에서는 편의를 위해 반복해서 설명됩니다.  

**전제 조건**
- 연결을 추가하려면 Configuration Manager 환경에서 먼저 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 [온라인 모드](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes)로 구성해야 합니다. 사용자 환경에 연결을 추가하면 이 사이트 시스템 역할을 실행하는 컴퓨터에 Microsoft Monitoring Agent도 설치됩니다.
- Configuration Manager를 "웹 애플리케이션 및/또는 Web API" 관리 도구로 등록하고 [이 등록의 클라이언트 ID](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/)를 받습니다.
- Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.
- Azure 관리 포털에서 [Configuration Manager에 OMS에 대한 사용 권한 제공](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms)에 설명된 대로 OMS에 액세스할 수 있는 권한을 등록된 웹앱에 제공합니다.

> [!IMPORTANT]       
> OMS에 액세스할 수 있는 권한을 구성하는 경우 **참가자** 역할을 선택하고 등록된 앱의 리소스 그룹에 사용 권한을 할당해야 합니다.

필수 구성 요소를 구성한 후에는 마법사를 사용하여 연결을 만들 수 있습니다.

### <a name="use-the-azure-services-wizard-to-configure-upgrade-readiness"></a>Azure 서비스 마법사를 사용하여 업그레이드 준비 상태 구성
1. 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **Azure 서비스**로 이동한 후 리본 메뉴의 **홈** 탭에서 **Azure 서비스 구성**을 선택하여 **Azure 서비스 마법사**를 시작합니다.

2. **Azure 서비스** 페이지에서 **업그레이드 준비 커넥터**를 선택한 후 **다음**을 클릭합니다.

3. **앱** 페이지에서 **Azure 환경**(기술 미리 보기는 퍼블릭 클라우드만 지원함)을 지정합니다. 그런 후 **가져오기**를 클릭하여 **앱 가져오기** 창을 엽니다.

4. **앱 가져오기** 창에서 Azure AD에 이미 존재하는 웹앱에 대한 세부 정보를 지정합니다.
    - Azure AD 테넌트 이름을 입력합니다. 그런 다음 테넌트 ID, 애플리케이션 이름, 클라이언트 ID, Azure Web App의 비밀 키, 앱 ID URI를 지정합니다.
    - **확인**을 클릭하고 성공하면 **확인**을 클릭하여 계속합니다.

5.  **구성** 페이지에서 업그레이드 준비 상태에 대한 이 연결에 사용하려는 구독, 리소스 그룹 및 Windows Analytics 작업 영역을 지정합니다.  

6. **다음**을 클릭하여 **요약** 페이지로 이동한 후 마법사를 완료하여 연결을 생성합니다.


## <a name="new-client-settings-for-cloud-services"></a>클라우드 서비스에 대한 새 클라이언트 설정
<!-- 1319883 -->

이 릴리스에서는 두 개의 새 클라이언트 설정을 Configuration Manager에 추가했습니다. 이러한 설정은 **클라우드 서비스** 섹션에 포함되어 있습니다.  이러한 설정은 다음과 같은 기능을 제공합니다.

- 구성된 클라우드 관리 게이트웨이에 액세스할 수 있는 Configuration Manager 클라이언트를 제어합니다.
- Windows 10 도메인에 연결된 Configuration Manger 클라이언트를 Azure Active Directory에 자동으로 등록합니다.

이러한 새 설정은 [Configuration Manager 1705 Technical Preview](/sccm/core/get-started/capabilities-in-technical-preview-1705#new-capabilities-for-azure-ad-and-cloud-management)에 설명된 기능을 완료하는 데 도움이 됩니다.

### <a name="before-you-start"></a>시작하기 전에

온-프레미스 Active Directory와 Azure AD 테넌트 간에 Azure AD Connect를 설치하고 구성해야 합니다.

연결을 제거하는 경우 디바이스는 등록 취소되지 않지만 새 디바이스는 등록되지 않습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

1. [클라이언트 설정 구성 방법](/sccm/core/clients/deploy/configure-client-settings)의 정보를 사용하여 다음 클라이언트 설정(클라우드 서비스에 있음) 섹션을 구성합니다.
   - **Azure Active Directory에 새 Windows 10 도메인에 연결된 디바이스를 자동으로 등록** – **예**(기본값) 또는 **아니요**로 설정합니다.
   - **클라이언트가 클라우드 관리 게이트웨이를 사용하도록 설정** – **예**(기본값) 또는 **아니요**로 설정합니다.
2. 필요한 디바이스 컬렉션에 클라이언트 설정을 배포합니다.

디바이스가 Azure AD에 연결되어 있는지 확인하려면 명령 프롬프트 창에서 명령 **dsregcmd.exe /status**를 실행합니다. 결과의 **AzureAdjoined** 필드는 디바이스가 Azure AD에 연결된 경우 **예**를 표시합니다.

## <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행
<!-- 1236459 -->

Configuration Manager에서 패키지 및 프로그램을 사용하여 클라이언트 디바이스에 스크립트를 배포할 수 있습니다. 이 Technical Preview에서는 다음 작업을 수행할 수 있는 새 기능을 추가했습니다.

- Configuration Manager에 PowerShell 스크립트 가져오기
- Configuration Manager 콘솔에서 스크립트 편집(서명되지 않은 스크립트만 해당)
- 스크립트를 승인 또는 거부로 표시하여 보안 강화
- Windows 클라이언트 PC 및 온-프레미스 관리 Windows PC 컬렉션에 대해 스크립트를 실행합니다. 스크립트는 배포하지 않아도 됩니다. 클라이언트 디바이스에서 거의 실시간으로 실행됩니다.
- Configuration Manager 콘솔에서 스크립트에 의해 반환된 결과를 검토합니다.


### <a name="prerequisites"></a>필수 구성 요소

스크립트를 사용하려면 해당 Configuration Manager 보안 역할의 구성원이어야 합니다.

- **스크립트를 가져오기 작성하려면** - 계정의 **전체 관리자** 보안 역할에 **SMS 스크립트**에 대한 **만들기** 권한이 있어야 합니다.
- **스크립트를 승인하거나 거부하려면** - 계정의 **전체 관리자** 보안 역할에 **SMS 스크립트**에 대한 **승인** 권한이 있어야 합니다.
- **스크립트를 실행하려면** - 계정의 **준수 설정 관리자** 보안 역할에 **컬렉션**에 대한 **스크립트 실행** 권한이 있어야 합니다.

Configuration Manager 보안 역할에 대한 자세한 내용은 [역할 기반 관리 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.

기본적으로 사용자는 작성한 스크립트를 승인할 수 없습니다. 스크립트는 강력하고 다양한 기능을 제공하며 여러 디바이스에 배포할 수 있으므로 스크립트를 작성하는 사용자와 스크립트를 승인하는 사용자 간에 역할을 분리하는 기능을 제공하는 새로운 개념을 도입했습니다. 이를 통해 감독 없이 스크립트를 실행할 때도 추가적으로 보안을 강화하는 효과를 얻을 수 있습니다. Technical Preview 릴리스 동안 특히 용이한 테스트를 위해 이러한 보조 승인을 해제할 수 있습니다.

사용자가 자신의 스크립트를 승인하도록 허용하려면

1. Configuration Manager 콘솔에서 **관리**를 클릭합니다.
2. **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.
3. 사이트 목록에서 사이트를 선택한 후 **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 클릭합니다.
4. **계층 구조 설정 속성** 대화 상자의 **일반** 탭에서 **스크립트 작성자가 스크립트를 승인하도록 허용 안 함** 확인란을 선택 취소합니다.


### <a name="try-it-out"></a>기능 직접 사용해 보기

#### <a name="import-and-edit-a-script"></a>스크립트 가져오기 및 편집

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. **소프트웨어 라이브러리** 작업 영역에서 **스크립트**를 클릭합니다.
3. **홈** 탭의 **만들기** 그룹에서 **스크립트 만들기**를 클릭합니다.
4. **스크립트 만들기** 마법사의 **스크립트** 페이지에서 다음을 구성합니다.
   - **스크립트 이름** - 스크립트의 이름을 입력합니다. 여러 스크립트를 같은 이름으로 만들 수 있지만 Configuration Manager 콘솔에서 필요한 스크립트를 찾는 것이 더 어려워집니다.
   - **스크립트 언어** - 현재 **PowerShell** 스크립트만 지원됩니다.
   - **가져오기** - 콘솔로 PowerShell 스크립트를 가져옵니다. 스크립트는 **스크립트** 필드에 표시됩니다.
   - **지우기** - **스크립트** 필드에서 현재 스크립트를 제거합니다.
   - **스크립트** - 현재 가져온 스크립트를 표시합니다. 필요에 따라 이 필드에서 스크립트를 편집할 수 있습니다.
5. 마법사를 완료합니다. 새 스크립트가 **승인 대기 중** 상태로 **스크립트** 목록에 표시됩니다. 클라이언트 디바이스에서 이 스크립트를 실행하려면 먼저 승인해야 합니다.


#### <a name="approve-or-deny-a-script"></a>스크립트 승인 또는 거부



스크립트를 실행하려면 먼저 승인을 받아야 합니다. 스크립트를 승인하려면

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. **소프트웨어 라이브러리** 작업 영역에서 **스크립트**를 클릭합니다.
3. **스크립트** 목록에서 승인 또는 거부하려는 스크립트를 선택한 후 **홈** 탭의 **스크립트** 그룹에서 **승인/거부**를 클릭합니다.
4. **스크립트 승인 또는 거부** 대화 상자에서 스크립트를 **승인** 또는 **거부**한 다음, 필요에 따라 이와 같은 결정에 대한 설명을 입력합니다. 스크립트를 거부하는 경우 클라이언트 디바이스에서 실행할 수 없습니다.
5. 마법사를 완료합니다. **스크립트** 목록에서 **승인 상태** 열이 수행한 작업에 따라 변경됩니다.

#### <a name="run-a-script"></a>스크립트 실행

스크립트가 승인되면 선택한 컬렉션에 대해 실행할 수 있습니다.

1. Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.
2. **자산 및 호환성** 작업 영역에서 **디바이스 컬렉션**을 클릭합니다.
3. **디바이스 컬렉션** 목록에서 스크립트를 실행하려는 디바이스 컬렉션을 클릭합니다.
3. **홈** 탭의 **모든 시스템** 그룹에서 **스크립트 실행**을 클릭합니다.
4. **스크립트 실행** 마법사의 **스크립트** 페이지에서 목록에 있는 스크립트를 선택합니다. 승인된 스크립트만 표시됩니다. **다음**을 클릭하여 마법사를 완료합니다.

#### <a name="monitor-a-script"></a>스크립트 모니터링

클라이언트 디바이스에 대해 스크립트를 실행한 후 다음 절차를 사용하여 작업의 성공 여부를 모니터링합니다.

1. Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.
2. **모니터링** 작업 영역에서 **스크립트 결과**를 클릭합니다.
3. **스크립트 결과** 목록에서 클라이언트 디바이스에서 실행한 각 스크립트에 대한 결과를 확인합니다. 스크립트 종료 코드 **0**은 일반적으로 스크립트가 성공적으로 실행되었음을 나타냅니다.

## <a name="pxe-network-boot-support-for-ipv6"></a>IPv6에 대한 PXE 네트워크 부팅 지원
<!-- 1269793 -->
이제 IPv6에 대한 PXE 네트워크 부팅 지원을 사용하도록 설정하여 작업 순서 운영 체제 배포를 시작할 수 있습니다. 이 설정을 사용하는 경우 PXE 사용 배포 지점은 IPv4 및 IPv6를 둘 다 지원합니다. 이 옵션은 WDS가 필요하지 않으며 WDS가 있으면 중지합니다.

#### <a name="to-enable-pxe-boot-support-for-ipv6"></a>IPv6에 대한 PXE 부팅 지원을 사용하도록 설정하려면
다음 절차에 따라 PXE에 대한 IPv6 지원 옵션을 사용하도록 설정합니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **배포 지점**으로 이동한 후 PXE 사용 배포 지점에 대한 **속성**을 클릭합니다.
2. **PXE** 탭에서 **IPv6 지원**을 선택하여 PXE에 대한 IPv6 지원을 사용하도록 설정합니다.

## <a name="manage-microsoft-surface-driver-updates"></a>Microsoft Surface 드라이버 업데이트 관리
<!-- 1098490 -->
이제 Configuration Manager를 사용하여 Microsoft Surface 드라이버 업데이트를 관리할 수 있습니다.

### <a name="prerequisites"></a>필수 구성 요소
모든 소프트웨어 업데이트 지점에서 Windows Server 2016이 실행되어야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
다음 작업을 완료한 다음 리본 메뉴의 **홈** 탭에서 **사용자 의견**을 전송하여 작동 상황을 알려주세요.
1. Microsoft Surface 드라이버에 대한 동기화를 사용하도록 설정합니다. [분류 및 제품 구성](/sccm/sum/get-started/configure-classifications-and-products)의 절차를 사용하고 **분류** 탭에서 **Microsoft Surface 드라이버 및 펌웨어 업데이트 포함**을 선택하여 Surface 드라이버를 사용하도록 설정합니다.
2. [Microsoft Surface 드라이버를 동기화](/sccm/sum/get-started/synchronize-software-updates)합니다.
3. [동기화된 Microsoft Surface 드라이버를 배포](/sccm/sum/deploy-use/deploy-software-updates)합니다.

## <a name="configure-windows-update-for-business-deferral-policies"></a>비즈니스용 Windows 업데이트 지연 정책 구성
<!-- 1290890 -->
이제 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 디바이스에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. **소프트웨어 라이브러리** > **Windows 10 서비스** 아래의 새 **비즈니스용 Windows 업데이트 정책** 노드에서 지연 정책을 관리할 수 있습니다.

### <a name="prerequisites"></a>필수 구성 요소
비즈니스용 Windows 업데이트에서 관리되는 Windows 10 디바이스는 인터넷에 연결되어 있어야 합니다.

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>비즈니스용 Windows 업데이트 지연 정책을 만들려면
1. **소프트웨어 라이브러리** > **Windows 10 서비스** > **비즈니스용 Windows 업데이트 정책**으로 이동합니다.
2. **홈** 탭의 **만들기** 그룹에서 **비즈니스용 Windows 업데이트 정책 만들기**를 선택하여 비즈니스용 Windows 업데이트 정책 만들기 마법사를 엽니다.
3. **일반** 페이지에서 정책의 이름 및 설명을 제공합니다.
4. **지연 정책** 페이지에서 기능 업데이트를 연기할지 또는 일시 중지할지를 구성합니다.    
    기능 업데이트는 일반적으로 새로운 Windows용 기능입니다. **분기 준비 수준** 설정을 구성한 후에 Microsoft에서 출시한 후에 기능 업데이트 수신을 연기할지 여부 및 연기 기간을 정의할 수 있습니다.
    - **분기 준비 상태 수준**: 디바이스가 Windows 업데이트(현재 분기 또는 비즈니스용 현재 분기)를 받을 분기를 설정합니다.
    - **지연 기간(일)** :  기능 업데이트를 연기할 일 수를 지정합니다. 이러한 기능 업데이트는 출시되고 180일 동안 수신을 연기할 수 있습니다.
    - **기능 업데이트 시작 일시 중지**: 기능 업데이트를 일시 중지한 날로부터 최대 60일 동안 디바이스에서 기능 업데이트를 받지 못하도록 일시 중지할지 여부를 선택합니다. 최대 일수가 경과하고 나면 일시 중지 기능은 자동으로 만료되고 디바이스가 Windows 업데이트에서 적용되는 업데이트를 검색합니다. 이 검색 후에 업데이트를 다시 일시 중지할 수 있습니다. 이 확인란을 선택 취소하여 기능 업데이트 일시 중지를 해제할 수 있습니다.   
5. 품질 업데이트를 연기할지 또는 일시 중지할지를 선택합니다.     
    품질 업데이트는 일반적으로 기존 Windows 기능에 대한 수정 내용 및 향상된 기능이며, 매월 첫째 화요일에 게시되는 것이 보통입니다. 물론 Microsoft는 언제든지 이러한 업데이트를 출시할 수 있습니다. 출시된 후에 품질 업데이트 수신을 연기할지 여부 및 연기할 기간을 정의할 수 있습니다.
    - **지연 기간(일)** : 기능 업데이트를 연기할 일 수를 지정합니다. 이러한 기능 업데이트는 출시되고 180일 동안 수신을 연기할 수 있습니다.
    - **품질 업데이트 시작 일시 중지**: 기능 업데이트를 일시 중지한 날로부터 최대 35일 동안 디바이스에서 품질 업데이트를 받지 못하도록 일시 중지할지 여부를 선택합니다. 최대 일수가 경과하고 나면 일시 중지 기능은 자동으로 만료되고 디바이스가 Windows 업데이트에서 적용되는 업데이트를 검색합니다. 이 검색 후에 업데이트를 다시 일시 중지할 수 있습니다. 이 확인란을 선택 취소하여 품질 업데이트 일시 중지를 해제할 수 있습니다.
6. **다른 Microsoft 제품에 대한 업데이트 설치**를 선택하여 지연 설정이 Windows 업데이트 뿐만 아니라 Microsoft 업데이트에도 적용될 수 있게 하는 그룹 정책 설정을 사용하도록 설정합니다.
7. Windows 업데이트에서 드라이버를 자동으로 업데이트하려면 **Windows 업데이트에 드라이버 포함**을 선택합니다. 이 설정을 선택 취소하면 드라이버 업데이트가 Windows 업데이트에서 다운로드되지 않습니다.
8. 마법사를 완료하여 새 지연 정책을 만듭니다.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>비즈니스용 Windows 업데이트 지연 정책을 배포하려면
1. **소프트웨어 라이브러리** > **Windows 10 서비스** > **비즈니스용 Windows 업데이트 정책**으로 이동합니다.
2. **홈** 탭의 **배포** 그룹에서 **비즈니스용 Windows 업데이트 정책 배포**를 선택합니다.
3. 다음 설정을 구성합니다.
    - **배포할 구성 정책**: 배포하려는 비즈니스용 Windows 업데이트 정책을 선택합니다.
    - **컬렉션**: **찾아보기**를 클릭하여 프로필을 배포하려는 컬렉션을 선택합니다.
    - **지원되는 경우 비규정 준수 규칙 수정**: Configuration Manager에서 등록된 모바일 디바이스의 레지스트리, 스크립트 및 모든 설정, WMI(Windows Management Instrumentation)에 대해 비규정 준수 규칙을 자동으로 수정하도록 선택합니다.
    - **유지 관리 기간을 벗어나도 수정 허용**: 정책을 배포할 컬렉션에 대해 유지 관리 기간이 구성된 경우 유지 관리 기간 외의 기간에 규정 준수 설정이 값을 수정할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다. 유지 관리 기간에 대한 자세한 내용은 [유지 관리 기간을 사용하는 방법](/sccm/core/clients/manage/collections/use-maintenance-windows)을 참조하세요.
    - **경고 생성**: 지정된 날짜 및 시간을 기준으로 구성 기준 규정 준수가 지정된 비율에 못 미치는 경우에 생성되는 경고를 구성합니다. 경고를 System Center Operations Manager로 전송할지 여부도 지정할 수 있습니다.
    - **임의 지연(시)** : 네트워크 디바이스 등록 서비스의 과도한 처리를 방지하기 위해 지연 기간을 지정합니다. 기본값은 64시간입니다.
    - **일정**: 클라이언트 컴퓨터에서 배포된 프로필이 평가되는 규정 준수 평가 일정을 지정합니다. 단순 일정 또는 사용자 지정 일정 중에서 지정할 수 있습니다. 사용자가 로그온해 있을 때 클라이언트 컴퓨터에서 프로필을 평가합니다.
4.  마법사를 완료하여 프로필을 배포합니다.



## <a name="support-for-entrust-certification-authorities"></a>Entrust 인증 기관에 대한 지원
<!-- 1350740 -->
Configuration Manager는 이제 Entrust 인증 기관을 지원합니다. 따라서 Microsoft Intune에 등록된 디바이스에 PFX 인증서를 전달할 수 있습니다.

Configuration Manager에서 인증서 등록 지점 역할을 추가할 때 Entrust를 인증 기관으로 구성할 수 있습니다. PFX 인증서를 발급하는 새 인증서 프로필을 추가할 때는 Microsoft 또는 Entrust 인증 기관을 선택할 수 있습니다.

**알려진 문제**: 1706 Technical Preview에서는 PFX 인증서가 Microsoft 인증 기관에 대해 발급되지 않습니다. 이러한 문제는 가져온 PFX 인증서 또는 SCEP 프로필에는 영향을 주지 않습니다.


## <a name="cisco-ipsec-support-for-ios-vpn-profiles"></a>iOS용 VPN 프로필에 대한 Cisco(IPsec) 지원
<!-- 1321367 -->

연결 형식으로 Cisco(IPsec)를 사용하여 iOS VPN 프로필을 만들 수 있습니다. 자세한 내용은 [VPN 프로필 만들기](https://docs.microsoft.com/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles)를 참조하세요.


## <a name="new-windows-configuration-item-settings"></a>새 Windows 구성 항목 설정
<!-- 1354715 -->

이 릴리스에서는 Windows 구성 항목에서 사용할 수는 다음과 같은 새 설정이 추가되었습니다.

### <a name="password"></a>암호

- **디바이스 암호화**

### <a name="device"></a>디바이스

- **지역 설정 수정(데스크톱만 해당)**
- **전원 및 절전 모드 설정 수정**
- **언어 설정 수정**
- **시스템 시간 수정**
- **디바이스 이름 수정**

### <a name="store"></a>스토어

- **스토어에서 앱 자동 업데이트**
- **프라이빗 저장소만 사용**
- **스토어에서 시작된 앱 시작**

### <a name="microsoft-edge"></a>Microsoft Edge

- **플래그에 대한 액세스 차단**
- **SmartScreen 프롬프트 재정의**
- **파일에 대한 SmartScreen 프롬프트 재정의**
- **WebRTC 로컬 호스트 IP 주소**
- **기본 검색 엔진**
- **OpenSearch XML URL**
- **홈페이지(데스크톱만 해당)**

준수 설정에 대한 자세한 내용은 [디바이스 준수 확인](/sccm/compliance/understand/ensure-device-compliance)을 참조하세요.


## <a name="new-device-compliance-policy-rules"></a>새 디바이스 준수 정책 규칙

* **필수 암호 유형** 사용자가 영숫자 암호를 만들어야 할지, 아니면 숫자 암호를 만들어야 할지를 지정합니다. 영숫자 암호의 경우 암호에 포함해야 할 각 문자 집합의 최소 수도 지정합니다. 4가지 문자 세트는 다음과 같습니다. 소문자, 대문자, 기호 및 숫자.

  **지원됨:**
  * Windows Phone 8+
  * Windows 8.1+
  * iOS 6+
<br></br>
* **디바이스에서 USB 디버깅 차단** USB 디버깅은 Android for Work 디바이스에서 이미 사용되지 않도록 설정되어 있으므로 구성할 필요가 없습니다.

  **지원됨:**
  * Android 4.0+
  * Samsung KNOX Standard 4.0 이상
<br></br>
* **알 수 없는 출처의 앱 차단** 디바이스가 알 수 없는 소스의 앱 설치를 방지해야 합니다. Android for Work 디바이스는 알 수 없는 출처의 설치를 하상 제한하므로 이 설정은 구성할 필요가 없습니다.

  **지원됨:**
  * Android 4.0+
  * Samsung KNOX Standard 4.0 이상
<br></br>
* **앱에서 위협 검색 필요** 이 설정은 디바이스에서 앱 확인 기능이 사용되도록 구성되어 있음을 지정합니다.

  **지원됨:**
  * Android 4.2 ~ 4.4
  * Samsung KNOX Standard 4.0 이상

새 디바이스 준수 규칙을 사용해 보려면 [디바이스 규정 준수 정책 만들기 및 배포](https://docs.microsoft.com/sccm/mdm/deploy-use/create-compliance-policy)를 참조하세요.

## <a name="new-mobile-application-management-policy-settings"></a>새 모바일 애플리케이션 관리 정책 설정
이 릴리스부터 3개의 새 MAM(모바일 애플리케이션 관리) 정책 설정을 사용할 수 있습니다.

- **화면 캡처 차단(Android 디바이스 전용)** : 이 앱을 사용할 때 디바이스의 화면 캡처 기능을 차단하도록 지정합니다.

- **연락처 동기화 사용 안 함**: 앱에서 디바이스의 네이티브 연락처 앱에 데이터를 저장하지 않도록 방지합니다.

- **인쇄 사용 안 함:** 앱에서 회사 또는 학교 데이터를 인쇄하지 않도록 방지합니다.

새로운 앱 보호 정책 설정을 사용하려면 [Configuration Manager에서 앱 보호 정책을 사용하여 앱 보호](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies)를 참조하세요.

## <a name="android-and-ios-enrollment-restrictions"></a>Android 및 iOS 등록 제한
<!-- 1290826 -->
이번 릴리스부터, 관리자는 이제 사용자가 하이브리드 환경에서 개인 Android 또는 iOS 디바이스를 등록할 수 었도록 지정할 수 있습니다. 이렇게 하면 등록된 디바이스를 미리 선언된 회사 소유 디바이스 또는 디바이스 등록 프로그램에 등록된 iOS 디바이스으로 제한할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
1. Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.
2. **홈** 탭의 **구독** 그룹에서 **플랫폼 구성**을 선택하고 **Android** 또는 **iOS**를 선택합니다.
3. **Intune에서 미리 선언된 디바이스만 등록 허용**을 선택합니다.

## <a name="android-for-work-application-management-policy-for-copy-paste"></a>복사-붙여넣기에 대한 Android for Work 애플리케이션 관리 정책
Android for Work 구성 항목 **회사 프로필과 개인 프로필 간의 데이터 공유 허용**에 대한 설정 설명을 업데이트했습니다.

|1706 Technical Preview 이전 | 새 옵션 이름 | 동작|
|-|-|-|
|경계를 넘은 공유 방지| 기본 공유 제한 사항| 회사-개인: 기본값(모든 버전에서 차단) <br>개인-회사: 기본값(6.x+에서 허용, 5.x에서 차단)|
|제한 없음| 개인 프로필의 앱에서 회사 프로필의 공유 요청을 처리할 수 있음| 회사-개인: 허용  <br>개인-회사: 허용|
|회사 프로필의 앱에서 개인 프로필의 공유 요청을 처리할 수 있음 |회사 프로필의 앱에서 개인 프로필의 공유 요청을 처리할 수 있음 |회사-개인: 기본값<br>개인-회사: 허용<br>(개인-회사가 차단된 경우 5.x에서만 유용)|

이러한 어떤 옵션도 복사-붙여넣기 동작을 직접 차단하지 않습니다. 복사-붙여넣기를 방지하도록 구성할 수 있는 1704의 서비스 및 회사 포털 앱에 사용자 지정 설정을 추가했습니다. 이 설정은 사용자 지정 URI를 통해 지정할 수 있습니다.

- OMA-URI:  ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste
- 값 형식: 부울

DisallowCrossProfileCopyPaste을 true로 설정하면 Android for Work 개인 및 회사 프로필 간에 복사-붙여넣기 동작이 방지됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
1. Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **준수 설정** > **구성 항목**을 선택합니다.
2. **만들기**를 선택하여 새 구성 항목을 만들고 **이름** 및 **Android for Work**를 지정합니다.
3. 구성할 디바이스 설정 그룹에서 **작업 프로필**을 선택하고 **다음**을 선택합니다.
4. **회사 프로필과 개인 프로필 간의 데이터 공유 허용**에 대한 값을 선택하고 마법사를 완료합니다.

## <a name="device-health-attestation-assessment-for-compliance-policies-for-conditional-access"></a>조건부 액세스의 준수 정책에 대한 디바이스 상태 증명 평가
<!-- 1097546 -->
이 릴리스부터 회사 리소스에 대한 조건부 액세스를 위해 디바이스 상태 증명 상태를 준수 정책 규칙으로 사용할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
디바이스 상태 증명 규칙을 준수 정책 평가의 일부로 선택합니다.
