---
title: 콘솔 내 업데이트
titleSuffix: Configuration Manager
description: Microsoft 클라우드에서 Configuration Manager에 업데이트 설치
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 944b502c2c4ae258cef693f7bc3f59ed22917fd9
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74661246"
---
# <a name="install-in-console-updates-for-configuration-manager"></a>Configuration Manager용 콘솔 내 업데이트 설치

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager는 Microsoft 클라우드 서비스와 동기화하여 업데이트를 가져옵니다. 그런 다음, Configuration Manager 콘솔 내에서 이러한 업데이트를 설치합니다.

## <a name="get-available-updates"></a>사용 가능 업데이트 가져오기

사이트에서는 인프라 및 버전에 적용되는 업데이트만 다운로드합니다. 이 동기화는 계층 구조에 대한 서비스 연결 지점을 구성하는 방법에 따라 자동이나 수동이 될 수 있습니다.

- **온라인 모드**에서, 서비스 연결 지점은 Microsoft 클라우드 서비스에 자동으로 연결하고 적용 가능한 업데이트를 다운로드합니다.  

    기본적으로 Configuration Manager는 24시간마다 새 업데이트를 확인합니다. Configuration Manager 콘솔에서 수동으로 업데이트를 확인합니다. **관리** 작업 영역으로 이동하고, **업데이트 및 서비스** 노드를 선택하고, 리본에서 **업데이트 확인**을 선택합니다.  

- **오프라인 모드**에서 서비스 연결 지점은 Microsoft 클라우드 서비스에 연결하지 않습니다. 사용 가능한 업데이트를 다운로드한 후 가져오려면 [서비스 연결 도구를 사용합니다](/sccm/core/servers/manage/use-the-service-connection-tool).  

> [!NOTE]  
> 필요한 경우 대역 외(out-of-band) 수정을 콘솔로 가져옵니다. 이렇게 하려면 [업데이트 등록 도구](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes)를 사용합니다. 이러한 대역 외 수정 내용은 Microsoft 클라우드 서비스와 동기화할 때 가져오는 업데이트를 보완합니다.  

업데이트가 동기화되면 Configuration Manager 콘솔에서 해당 업데이트를 확인합니다. **관리** 작업 영역으로 이동하고, **업데이트 및 서비스** 노드를 선택합니다.  

- 설치하지 않은 업데이트는 **사용 가능**으로 표시됩니다.  

- 설치한 업데이트는 **설치됨**으로 표시됩니다. 가장 최근에 설치된 업데이트만 표시됩니다. 이전에 설치된 업데이트를 보려면 리본에서 **기록**을 선택합니다.  

서비스 연결 지점을 구성하기 전에 추가적인 사용을 이해하고 계획하세요. 다음 사용은 이 사이트 시스템 역할을 구성하는 방법에 영향을 줄 수 있습니다.  

- 사이트에서 서비스 연결 지점을 사용하여 사이트에 대한 사용 정보를 업로드합니다. 이 정보는 Microsoft 클라우드 서비스에서 현재 인프라 버전에 사용할 수 있는 업데이트를 식별하는 데 도움이 됩니다. 자세한 내용은 [진단 및 사용량 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.  

- 사이트에서 서비스 연결 지점을 사용하여 Microsoft Intune을 사용하는 디바이스를 관리하고, Configuration Manager 온-프레미스 모바일 디바이스 관리를 사용합니다. 자세한 내용은 [하이브리드 MDM(모바일 디바이스 관리)](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.  

업데이트를 다운로드할 때 수행되는 작업을 더 잘 이해하려면 다음 순서도를 참조하세요.  

- [순서도 – 업데이트 다운로드](/sccm/core/servers/manage/download-updates-flowchart)  

- [순서도 – 업데이트 복제](/sccm/core/servers/manage/update-replication-flowchart)  


## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>업데이트 및 기능을 보고 관리할 수 있는 권한 할당

콘솔에서 업데이트를 보려면 사용자에게 **업데이트 패키지** 보안 클래스가 포함된 역할 기반 관리 보안 역할이 있어야 합니다. 이 클래스는 Configuration Manager 콘솔에서 업데이트를 보고 업데이트할 수 있는 액세스 권한을 부여합니다.

### <a name="about-the-update-packages-class"></a>업데이트 패키지 클래스 정보

기본적으로 **업데이트 패키지** 클래스(SMS_CM_Updatepackages)는 다음과 같이 나열된 권한이 있는 기본 제공 보안 역할의 일부입니다.  

- **수정** 및 **읽기** 권한이 있는 **전체 관리자** :  

    - 이 보안 역할 및 **모든** 보안 범위에 대한 액세스 권한이 있는 사용자는 업데이트를 보고 설치할 수 있습니다. 사용자는 설치 중에 기능을 사용하도록 설정하고, 사이트 업데이트 후에는 개별 기능을 사용하도록 설정할 수도 있습니다.  

    - 이 보안 역할 및 **기본** 보안 범위에 대한 액세스 권한이 있는 사용자는 업데이트를 보고 설치할 수 있습니다. 사용자는 설치 중에 기능을 사용하도록 설정하고, 사이트 업데이트 후에는 개별 기능을 볼 수도 있습니다. 그러나 이 사용자는 사이트를 업데이트한 후에 기능을 사용하도록 설정할 수 없습니다.  

- **읽기** 권한이 있는 **읽기 전용 분석가** :  

    - 이 보안 역할 및 **기본** 범위에 대한 액세스 권한을 가진 사용자는 업데이트를 볼 수 있지만 설치할 수는 없습니다. 이 사용자는 사이트를 업데이트한 후에도 기능을 볼 수 있지만 사용하도록 설정할 수는 없습니다.  

### <a name="permissions-required-for-updates-and-servicing"></a>업데이트 및 서비스에 필요한 권한

- **수정** 및 **읽기** 권한이 모두 있는 **업데이트 패키지** 클래스가 포함된 보안 역할을 할당하는 계정을 사용합니다.  

- 계정을 **기본** 범위에 할당합니다.  

### <a name="permissions-to-only-view-updates"></a>업데이트 보기만 가능한 권한

- **읽기** 권한만 있는 **업데이트 패키지** 클래스가 포함된 역할을 할당하는 계정을 사용합니다.  

- 계정을 **기본** 범위에 할당합니다.  

### <a name="permissions-required-to-enable-features-after-the-site-updates"></a>사이트 업데이트 후 기능을 사용하도록 설정하는 데 필요한 권한

- **수정** 및 **읽기** 권한이 모두 있는 **업데이트 패키지** 클래스가 포함된 보안 역할을 할당하는 계정을 사용합니다.  

- 계정을 **모든** 범위에 할당합니다.  


## <a name="bkmk_beforeinstall"></a> 콘솔 내 업데이트를 설치하기 전에  

Configuration Manager 콘솔 내에서 업데이트를 설치하기 전에 다음 단계를 검토합니다.  

### <a name="bkmk_step1"></a> 1단계: 업데이트 검사 목록 검토  

업데이트를 시작하기 전에 수행할 작업에 해당하는 업데이트 검사 목록을 검토합니다.

- [업데이트 1910을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1910)  

- [업데이트 1906을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1906)  

- [업데이트 1902를 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1902)

- [업데이트 1810을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1810)  

### <a name="bkmk_step2"></a> 2단계: 업데이트를 설치하기 전에 필수 조건 검사 실행  

업데이트를 설치하기 전에 해당 업데이트에 대한 필수 조건 검사를 실행하는 것이 좋습니다. 업데이트를 설치하기 전에 필수 구성 요소를 실행하면  

- 사이트에서 업데이트를 설치하기 전에 업데이트 파일을 다른 사이트에 복제합니다.  

- 업데이트를 설치하도록 선택하면 필수 구성 요소 검사가 자동으로 다시 실행됩니다.  

> [!NOTE]  
> 필수 구성 요소 검사를 시작한 다음, 상태를 볼 때 **설치** 단계가 활성 상태로 표시되지만, 실제로는 이 사이트에서 업데이트를 설치하지 않습니다. 필수 구성 요소 검사를 실행하기 위해 업데이트 프로세스는 콘텐츠 라이브러리에서 패키지를 추출합니다. 그런 다음, 현재 필수 구성 요소 검사에 액세스할 수 있는 준비 폴더에 패키지를 배치합니다. 업데이트를 설치하면 이와 동일한 프로세스가 실행됩니다. 이 동작으로 인해 설치 단계가 **진행 중**으로 표시됩니다. *업데이트 패키지 추출* 단계만 설치 범주에 표시됩니다.  

나중에 업데이트를 설치하면 필수 조건 검사 경고를 무시하도록 업데이트를 구성할 수 있습니다.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>업데이트를 설치하기 전에 필수 조건 검사를 실행하려면  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **배포 지점** 노드를 선택합니다.  

2. 필수 구성 요소 검사를 실행하려는 업데이트 패키지를 선택합니다.  

3. 리본에서 **필수 구성 요소 검사 실행**을 선택합니다.  

    필수 조건 검사를 실행하면 업데이트의 콘텐츠가 하위 사이트에 복제됩니다. 사이트 서버에서 **distmgr.log**를 보고 해당 콘텐츠가 성공적으로 복제되었는지 확인합니다.  

4. 필수 구성 요소 검사 결과를 보려면 다음을 수행합니다.  

    1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다.  

    2. **업데이트 및 서비스 상태** 노드를 선택하고, 필수 구성 요소를 찾습니다.  

    3. 자세한 내용은 사이트 서버의 **ConfigMgrPrereq.log**를 참조하세요.  


## <a name="bkmk_install"></a> 콘솔 내 업데이트 설치  

Configuration Manager 콘솔 내에서 업데이트를 설치할 준비가 되면 계층 구조의 최상위 사이트에서 시작합니다. 이 사이트는 중앙 관리 사이트 또는 독립 실행형 기본 사이트입니다.  

각 사이트의 정상적인 업무 시간 외에 업데이트를 설치하여 비즈니스 운영에 미치는 영향을 최소화합니다. 업데이트 설치에는 사이트 구성 요소 및 사이트 시스템 역할을 다시 설치하는 것과 같은 작업이 포함될 수 있습니다.  

- 중앙 관리 사이트에서 업데이트 설치가 완료되면 자식 기본 사이트에서 업데이트를 자동으로 시작합니다. 이것이 권장되는 기본 프로세스입니다. 기본 사이트에서 업데이트를 설치할 시기를 제어하려면 [사이트 서버에 대한 서비스 기간](/sccm/core/servers/manage/service-windows)을 사용합니다.  

- 부모 기본 사이트 업데이트가 완료되면 Configuration Manager 콘솔 내에서 보조 사이트를 수동으로 업데이트합니다. 보조 사이트 서버의 자동 업데이트는 지원되지 않습니다.  

- 사이트가 업데이트된 후 Configuration Manager 콘솔을 사용하면 콘솔을 업데이트하라는 메시지가 표시됩니다.  

- 사이트 서버는 업데이트 설치를 완료한 후 해당하는 사이트 시스템 역할을 자동으로 모두 업데이트합니다. 그러나 모든 배포 지점에서 다시 설치하지 않고, 동시에 업데이트하기 위해 오프라인 상태로 전환되지 않습니다. 대신, 사이트 서버에서 사이트의 콘텐츠 배포 설정을 사용하여 한 번에 하나씩 배포 지점 하위 집합에 업데이트를 배포합니다. 따라서 일부 배포 지점만 업데이트 설치를 위해 오프라인으로 전환됩니다. 업데이트가 시작되지 않았거나 완료된 배포 지점은 온라인 상태로 유지되고 클라이언트에 콘텐츠를 제공할 수 있습니다.

### <a name="bkmk_overview"></a> 콘솔 내 업데이트 설치의 개요  

#### <a name="1-when-the-update-installation-starts"></a>1. 업데이트 설치가 시작되면

업데이트가 적용되는 제품 영역의 목록을 표시하는 마법사가 나타납니다.  

- 마법사의 **일반** 페이지에서 필요에 따라 **필수 구성 요소 경고**를 구성합니다.  

    - 필수 조건 오류는 항상 업데이트 설치를 중지합니다. 업데이트 설치를 성공적으로 다시 시도하려면 먼저 오류를 수정합니다. 자세한 내용은 [실패한 업데이트의 설치 다시 시도](#bkmk_retry)를 참조하세요.  

    - 필수 조건 경고도 업데이트 설치를 중지할 수 있습니다. 업데이트 설치를 다시 시도하려면 먼저 경고를 해결합니다. 자세한 내용은 [실패한 업데이트의 설치 다시 시도](#bkmk_retry)를 참조하세요.  

    - **필수 구성 요소 검사의 모든 경고를 무시하고 누락된 요구 사항에 상관없이 이 업데이트 설치**: 필수 구성 요소 경고를 무시하도록 업데이트 설치에 대한 조건을 설정합니다. 이 옵션을 통해 업데이트 설치를 계속 진행할 수 있습니다. 이 옵션을 선택하지 않은 경우 프로세스에서 경고가 발생하면 업데이트 설치가 중지됩니다. 이전에 사이트에 대한 필수 구성 요소 검사 및 고정된 필수 구성 요소 경고를 실행하지 않은 경우 이 옵션은 사용하지 않습니다.  

        **관리** 및 **모니터링** 작업 영역 모두에서 [업데이트 및 서비스] 노드에는 **필수 구성 요소 경고 무시**라는 리본 메뉴 단추가 포함되어 있습니다. 필수 조건 검사 경고로 인해 업데이트 패키지에서 설치를 완료하지 못하는 경우 이 단추를 사용할 수 있습니다. 예를 들어 필수 조건 경고를 무시하는 옵션을 사용하지 않고 업데이트를 설치한다고 가정해봅니다(업데이트 마법사에서). 업데이트 설치는 필수 조건 경고는 발생하지만 오류는 없이 중지됩니다. 나중에 리본에서 **필수 구성 요소 경고 무시**를 선택합니다. 이 작업은 필수 구성 요소 경고를 무시하는 해당 업데이트 설치의 자동 진행을 트리거합니다. 이 옵션을 사용하면 몇 분 후에 업데이트 설치가 자동으로 진행됩니다.  

- Configuration Manager 클라이언트에 업데이트가 적용되면 제한된 클라이언트 집합을 사용하여 업데이트를 테스트하도록 선택합니다. 자세한 내용은 [사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](/sccm/core/clients/manage/upgrade/test-client-upgrades)을 참조하세요.  

#### <a name="2-during-the-update-installation"></a>2. 업데이트 설치 중

업데이트 설치의 일환으로 Configuration Manager에서 수행하는 작업은 다음과 같습니다.  

- 사이트 시스템 역할 또는 Configuration Manager 콘솔과 같은 영향을 받는 모든 구성 요소를 다시 설치합니다.  

- 클라이언트 파일럿에 대한 선택 사항에 따라, 그리고 [자동 클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#bkmk_autoupdate)를 위해 클라이언트 업데이트를 관리합니다.  

- 사이트 시스템 서버는 일반적으로 업데이트의 일부로 다시 시작할 필요가 없습니다. 역할에서 .NET을 사용하고 패키지에서 해당 필수 구성 요소를 업데이트하면 사이트 시스템이 다시 시작될 수 있습니다.  

> [!TIP]  
> Configuration Manager 업데이트가 설치되면 사이트에서 CD.Latest 폴더도 업데이트됩니다. 자세한 내용은 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)를 참조하세요.  

#### <a name="3-monitor-the-progress-of-updates-as-they-install"></a>3. 설치하는 업데이트의 진행률 모니터링

다음 단계를 사용하여 진행 상황을 모니터링합니다.  

- Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **배포 지점** 노드를 선택합니다. 이 노드에는 모든 업데이트 패키지의 설치 상태가 표시됩니다.  

- Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고, **업데이트 및 서비스 상태** 노드를 선택합니다. 이 노드에는 사이트에서 설치하는 현재 업데이트 패키지의 설치 상태만 표시됩니다.  

    업데이트 설치는 더 쉽게 모니터링할 수 있도록 여러 단계로 구분됩니다. 다음의 각 단계와 관련된 설치 상태의 추가 세부 정보에는 자세한 내용을 확인할 수 있는 로그 파일이 포함됩니다.  

    - **다운로드**: 이 단계는 서비스 연결 지점이 있는 최상위 사이트에만 적용됩니다.

    - **복제**

    - **필수 구성 요소 확인**

    - **설치**

    - **설치 후**: 자세한 내용은 [설치 후 작업](#post-installation-tasks)을 참조하세요.  

- 사이트 서버의 `<ConfigMgr_Installation_Directory>\Logs`에 있는 **CMUpdate.log** 파일을 봅니다.  

>[!NOTE]
> 버전 1906부터 **설치**단계 동안 **ConfigMgr 데이터베이스 업그레이드** 작업의 상태를 볼 수 있습니다.
>
> - 데이터베이스 업그레이드가 차단된 경우 **진행 중. 주의 필요**라는 경고가 표시됩니다.
>   - cmupdate.log는 데이터베이스 업그레이드를 차단하는 SQL의 프로그램 이름 및 sessionid를 기록합니다.
> - 데이터베이스 업그레이드가 더 이상 차단되지 않으면 상태가 **진행 중** 또는 **완료**로 다시 설정됩니다.
>   - 데이터베이스 업그레이드가 차단되면 5분마다 업그레이드가 여전히 차단되는지 확인하는 작업이 수행됩니다.

#### <a name="4-when-the-update-installation-completes"></a>4. 업데이트 설치가 완료되면

첫 번째 사이트 업데이트가 설치를 완료한 후  

- 자식 기본 사이트에서 업데이트를 자동으로 설치합니다. 추가적인 조치가 필요하지 않습니다.  

- Configuration Manager 콘솔 내에서 보조 사이트를 수동으로 업데이트합니다. 자세한 내용은 [보조 사이트에서 업데이트 설치 시작](#bkmk_secondary)을 참조하세요.  

- 계층의 모든 사이트가 새 버전으로 업데이트될 때까지 계층이 혼합 버전 모드로 작동합니다. 자세한 내용은 [서로 다른 버전 간 상호 운용성](/sccm/core/plan-design/hierarchy/interoperability-between-different-versions)을 참조하세요.  

#### <a name="5-update-configuration-manager-consoles"></a>5. Configuration Manager 콘솔 업데이트

중앙 관리 사이트 또는 기본 사이트가 업데이트되면 해당 사이트에 연결된 각 Configuration Manager 콘솔도 업데이트해야 합니다. 콘솔을 업데이트하라는 메시지가 표시되는 경우는 다음과 같습니다.  

- 콘솔을 열 때  

- 열린 콘솔에서 새 노드로 이동할 때  

사이트가 업데이트되는 즉시 콘솔을 업데이트합니다.  

콘솔 업데이트가 완료되면 콘솔 및 사이트 버전이 올바른지 확인합니다. 콘솔의 왼쪽 위에 있는 **Configuration Manager 정보**로 이동합니다.  

> [!Note]  
> 콘솔 버전은 사이트 버전과 약간 다릅니다. 콘솔의 부 버전이 Configuration Manager 릴리스 버전에 해당합니다. 예를 들어, Configuration Manager 버전 1802에서 초기 사이트 버전은 5.0.8634.1000이고 초기 콘솔 버전은 5.**1802**.1082.1700입니다. 빌드(1082) 및 수정(1700) 번호는 향후 핫픽스에서 변경될 수 있습니다.

### <a name="bkmk_toptier"></a> 최상위 사이트에서 업데이트 설치를 시작하려면  

계층 구조의 최상위 사이트에 있는 Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **업데이트 및 서비스** 노드를 선택합니다. 상태가 **사용 가능**인 업데이트를 선택한 다음, 리본에서 **업데이트 팩 설치**를 선택합니다.  

### <a name="bkmk_secondary"></a> 보조 사이트에서 업데이트 설치를 시작하려면  

보조 사이트의 부모 기본 사이트가 업데이트되면 Configuration Manager 콘솔 내에서 보조 사이트를 업데이트합니다. 그렇게 하려면 **보조 사이트 업그레이드 마법사**를 사용합니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 업데이트하려는 보조 사이트를 선택한 다음, 리본에서 **업그레이드**를 선택합니다.  

2. **예**를 선택하여 보조 사이트의 업데이트를 시작합니다.  

보조 사이트의 업데이트 설치를 모니터링하려면 보조 사이트를 선택하고 리본에서 **설치 상태 표시**를 선택합니다. 또한 각 보조 사이트의 버전이 표시되도록 사이트 노드에 **버전** 열을 추가합니다.  

경우에 따라 콘솔의 상태가 새로 고쳐지지 않거나 업데이트가 실패했다고 표시됩니다. 보조 사이트가 성공적으로 업데이트된 후 **설치 다시 시도** 옵션을 사용합니다. 이 옵션은 업데이트가 성공적으로 설치되지 않은 보조 사이트에 대한 업데이트를 다시 설치하지는 않지만 콘솔에서 상태를 강제로 업데이트합니다.

### <a name="post-installation-tasks"></a>설치 후 작업

사이트에서 업데이트를 설치하는 경우 사이트 서버의 업데이트 설치가 완료될 때까지 시작할 수 없는 몇 가지 작업이 있습니다. 이 목록에는 사이트 및 계층 구조 작업에 중요한 설치 후 작업이 포함됩니다. 이러한 작업은 중요하므로 적극적으로 모니터링됩니다. 직접 모니터링되지 않는 추가 작업에는 사이트 시스템 역할을 다시 설치하는 작업이 포함됩니다. 중요한 설치 후 작업의 상태를 보려면 사이트에 대한 업데이트 설치를 모니터링하는 동안 **설치 후** 작업을 선택합니다.

모든 작업이 즉시 완료되는 것은 아닙니다. 일부 작업은 각 사이트에서 업데이트의 설치를 완료할 때까지 시작되지 않습니다. 이러한 작업이 완료될 때까지 필요한 새 기능이 지연될 수 있습니다. 새 기능을 켜도, 모든 사이트의 업데이트 설치가 완료될 때까지 시작되지 않으므로 얼마 동안 새 기능이 표시되지 않을 수 있습니다.

설치 후 작업에는 다음이 포함됩니다.

- **SMS_EXECUTIVE 서비스 설치**

    - 사이트 서버에서 실행되는 중요한 서비스입니다.
    - 이 서비스의 다시 설치는 신속하게 완료됩니다.

- **SMS_DATABASE_NOTIFICATION_MONITOR 구성 요소 설치**

    - SMS_EXECUTIVE 서비스의 중요한 사이트 구성 요소 스레드입니다.
    - 이 서비스의 다시 설치는 신속하게 완료됩니다.

- **SMS_HIERARCHY_MANAGER 구성 요소 설치**

    - 사이트 서버에서 실행되는 중요한 사이트 구성 요소입니다.
    - 사이트 시스템 서버에 역할을 다시 설치해야 합니다. 개별 사이트 시스템 역할 다시 설치에 대한 상태는 표시되지 않습니다.
    - 이 서비스의 다시 설치는 신속하게 완료됩니다.

    > [!Note]
    > 일부 Configuration Manager 사이트 역할은 클라이언트 프레임워크를 공유합니다. 예를 들어 관리 지점과 풀(pull) 배포 지점이 그렇습니다. 이러한 역할이 업데이트될 때 이러한 서버의 클라이언트 버전도 동시에 업데이트됩니다. 자세한 내용은 [클라이언트 업그레이드 방법](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers)을 참조하세요.

- **SMS_REPLICATION_CONFIGURATION_MONITOR 구성 요소 설치**

    - 사이트 서버에서 실행되는 중요한 사이트 구성 요소입니다.
    - 이 서비스의 다시 설치는 신속하게 완료됩니다.

- **SMS_POLICY_PROVIDER 구성 요소 설치**

    - 기본 사이트서만 실행되는 중요한 사이트 구성 요소입니다.
    - 이 서비스의 다시 설치는 신속하게 완료됩니다.

- **복제 초기화 모니터링**

    - 이 작업만 중앙 관리 사이트 및 자식 기본 사이트에 표시됩니다.
    - SMS_REPLICATION_CONFIGURATION_MONITOR에 종속됩니다.
    - 신속하게 완료해야 합니다.

- **Configuration Manager 클라이언트 사전 프로덕션 패키지 업데이트**

    - 이 작업은 클라이언트 사전 프로덕션(클라이언트 파일럿이라고도 함)이 사용되도록 설정되지 않는 경우에도 표시됩니다.
    - 계층 구조의 모든 사이트가 업데이트 설치를 완료할 때까지 시작되지 않습니다.

- **사이트 서버에서 클라이언트 폴더 업데이트**

    - 이 작업은 사전 프로덕션에서 클라이언트를 사용하는 경우에는 표시되지 않습니다.  
    - 신속하게 완료해야 합니다.

- **Configuration Manager 클라이언트 패키지 업데이트**

    - 이 작업은 사전 프로덕션에서 클라이언트를 사용하는 경우에는 표시되지 않습니다.  
    - 모든 사이트에서 업데이트를 설치한 후에만 완료됩니다.  

- **기능 켜기**

    - 이 작업은 계층 구조의 최상위 계층 사이트에만 표시됩니다.
    - 계층 구조의 모든 사이트가 업데이트 설치를 완료할 때까지 시작되지 않습니다.
    - 개별 기능은 표시되지 않습니다.


## <a name="bkmk_retry"></a> 실패한 업데이트의 설치 다시 시도  

업데이트를 설치하지 못하는 경우 콘솔 내 피드백을 검토하여 경고 및 오류가 해결되었는지 확인합니다. 자세한 내용은 사이트 서버의 **ConfigMgrPrereq.log**를 참조하세요. 업데이트 설치를 다시 시도하기 전에 오류를 수정하고 경고를 해결해야 합니다.  

> [!TIP]  
> 업데이트를 다운로드하거나 복제하는 데 문제가 있는 경우 [업데이트 다시 설정 도구](/sccm/core/servers/manage/update-reset-tool)를 사용하세요.  

업데이트 설치를 다시 시도할 준비가 되면 실패한 업데이트를 선택한 다음, 해당 옵션을 선택합니다. 업데이트 설치 다시 시도 동작은 다시 시도를 시작하는 노드와 사용하는 다시 시도 옵션에 따라 다릅니다.  

### <a name="retry-installation-for-the-hierarchy"></a>계층에 대한 설치 다시 시도

해당 업데이트가 다음 상태 중 하나인 경우 전체 계층 구조에 대한 업데이트 설치를 다시 시도합니다.  

- 하나 이상의 경고와 함께 필수 구성 요소 검사를 통과했으며, 업데이트 마법사에서 필수 구성 요소 검사 경고를 무시하는 옵션이 설정되지 않았음 (**업데이트 및 서비스** 노드에서 **필수 구성 요소 경고 무시**에 대한 업데이트 값이 **아니요**임)

- 필수 조건 실패

- 설치 실패  

- 콘텐츠를 사이트로 복제 실패

**관리** 작업 영역으로 이동하고, **업데이트 및 서비스** 노드를 선택합니다. 업데이트를 선택한 다음, 다음 옵션 중 하나를 선택합니다.  

- **다시 시도**: **업데이트 및 서비스**에서 **다시 시도**를 설정하면 업데이트 설치가 다시 시작되고 필수 구성 요소 경고가 자동으로 무시됩니다. 이전에 콘텐츠 복제가 실패한 경우 업데이트 콘텐츠가 다시 복제됩니다.  

- **필수 구성 요소 경고 무시**: 경고로 인해 업데이트 설치가 중지되면 **필수 구성 요소 경고 무시**를 선택할 수 있습니다. 이 작업을 수행하면 몇 분 후에 업데이트 설치가 계속 진행되며 필수 구성 요소 경고를 무시하는 옵션이 사용됩니다.

### <a name="retry-installation-for-the-site"></a>사이트에 대한 설치 다시 시도

해당 업데이트가 다음 상태 중 하나인 경우 특정 사이트에서 업데이트 설치를 다시 시도합니다.  

- 하나 이상의 경고와 함께 필수 구성 요소 검사를 통과했으며, 업데이트 마법사에서 필수 구성 요소 검사 경고를 무시하는 옵션이 설정되지 않았음 ([업데이트 및 서비스] 노드에서 **필수 구성 요소 경고 무시**에 대한 업데이트 값이 **아니요**임)  

- 필수 조건 실패

- 설치 실패

**모니터링** 작업 영역으로 이동하고, **사이트 서비스 상태** 노드를 선택합니다. 업데이트를 선택한 다음, 다음 옵션 중 하나를 선택합니다.  

- **다시 시도**: **사이트 서비스 상태**에서 **다시 시도**를 설정하면 업데이트 설치가 해당 사이트에서만 다시 시작됩니다. **업데이트 및 서비스** 노드에서 **다시 시도**를 실행하는 경우와 달리, 이 다시 시도 작업에서는 필수 구성 요소 경고가 무시되지 않습니다.  

- **필수 구성 요소 경고 무시**: 경고로 인해 업데이트 설치가 중지되면 **필수 구성 요소 경고 무시**를 선택할 수 있습니다. 이 작업을 수행하면 몇 분 후에 업데이트 설치가 계속 진행되며 필수 구성 요소 경고를 무시하는 옵션이 사용됩니다.  

## <a name="bkmk_after"></a> 사이트에서 업데이트를 설치한 후  

사이트 업데이트 후 해당 버전에 대한 업데이트 후 검사 목록을 검토합니다.  

- [버전 1910용 업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1910#post-update-checklist)  

- [버전 1906용 업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1906#post-update-checklist)  

- [버전 1902용 업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1902#post-update-checklist)  

- [버전 1810용 업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist)  

## <a name="bkmk_options"></a> 업데이트에서 선택적 기능 사용  

업데이트에 하나 이상의 선택적 기능이 포함될 때 계층에서 이러한 기능을 사용하도록 설정할 수 있습니다. 업데이트가 설치될 때 기능을 사용하도록 설정하거나 나중에 콘솔로 돌아가서 선택적 기능을 사용하도록 설정합니다.

사용 가능한 기능 및 해당 상태를 보려면 콘솔에서 **관리** 작업 영역으로 이동하고, **업데이트 및 서비스**를 펼친 다음, **기능** 노드를 선택합니다.

옵션이 아닌 기능은 자동으로 설치됩니다. **기능** 노드에 나타나지 않습니다.  

> [!Important]  
> 다중 사이트 계층 구조에서는 중앙 관리 사이트에서만 선택적 또는 시험판 기능을 사용하도록 설정합니다. 이 동작은 계층 전체에 충돌이 발생하지 않도록 합니다. <!--507197-->  

새 기능 또는 시험판 기능을 사용하도록 설정하면 Configuration Manager HMAN(계층 구조 관리자)은 해당 기능을 사용할 수 있게 되기 전에 변경 내용을 처리해야 합니다. 변경 처리는 즉시 처리되는 경우가 많습니다. HMAN 처리 주기에 따라 완료하는 데 최대 30분이 걸릴 수 있습니다. 변경이 처리되면 기능을 사용하기 전에 콘솔을 다시 시작합니다.

### <a name="list-of-optional-features"></a>옵션 기능 목록

다음은 Configuration Manager 최신 버전의 옵션 기능입니다.<!--505213-->  

<!--Note to include in target articles

> [!Note]  
> Configuration Manager doesn't enable this optional feature by default. You must enable this feature before using it. For more information, see [Enable optional features from updates](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).  

-->

- [BitLocker 관리](/configmgr/protect/plan-design/bitlocker-management) <!-- 3601034,6DD56E46-C3EC-4E38-A16F-E98644BB6434 -->
- [Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화](/sccm/core/clients/manage/collections/create-collections#bkmk_aadcollsync) <!--3607475,C2127144-C8DE-49F6-9CB3-D4F5B59F9515-->
- [Azure Active Directory 사용자 그룹 검색](/sccm/core/servers/deploy/configure/configure-discovery-methods#bkmk_azuregroupdisco) <!--3611956,023715E7-BFBA-4E9E-A80F-B5B626464ADD-->
- [애플리케이션 그룹](/sccm/apps/deploy-use/create-app-groups) <!--3555907,EE16A1D8-EF1B-4094-845F-AC107E7C621D-->
- [작업 순서 배포](/sccm/osd/deploy-use/debug-task-sequence) <!--3612274,C3F37661-69E4-4D53-A39C-5D02F97E0E71-->
- [Package Conversion Manager](/sccm/apps/pcm/package-conversion-manager) <!--1357861,4E0C09AF-7FC1-4412-A8BB-166D9BCD0093-->
- [공동 관리형 디바이스용 클라이언트 앱](/sccm/comanage/workloads#client-apps) <!--1357892,CC3AE625-BF72-49B1-8AB1-AF0DCF2D6F4C-->
- [타사 소프트웨어 업데이트](/sccm/sum/deploy-use/third-party-software-updates)<!--1357605,1352101,1358714;B5E192AE-C81F-4348-9EF9-07A3C0FBE597-->
- [디바이스당 사용자에 대한 애플리케이션 요청 승인](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy-settings) <!--1357015,4BA987C9-08FC-48E2-BFFE-C9DCF35B496A-->  
- [조건부 액세스의 준수 정책에 대한 디바이스 상태 증명 평가](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm) <!--1235616,0E986DC1-D20A-4386-9EB5-108D9D5118EB-->
- [스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts) <!--1236459,566F8720-F415-4E10-9A51-CDE682BA2B2E-->
- [Surface 드라이버 업데이트](/sccm/sum/get-started/configure-classifications-and-products) <!--1098490,82AD973A-7CDF-4B67-A665-72875D6E099A-->
- [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway) <!--1101764,DD043119-789C-4158-AC79-725E999F385A-->
- [PFX 만들기](/sccm/protect/deploy-use/introduction-to-certificate-profiles) <!--1321368,CED76B79-929C-4C45-981F-B9BCA6D38A17-->
- [Azure Log Analytics 커넥터](/sccm/core/clients/manage/sync-data-log-analytics) <!--1258052,73A7EC4D-EF22-4EA4-82A9-419C2A8CFC4D-->
- [Windows Defender Exploit Guard 정책](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) <!--1355468,8491D4C8-8484-46B8-BCD6-17DC2CADBAEB-->
- [Windows 10용 VPN](/sccm/protect/deploy-use/vpn-profiles) <!--1283610,EDBEBA3D-3A4D-4465-84D9-D71EB811E7F6-->
- [클러스터 인식 컬렉션 서비스(서버 그룹 서비스)](/sccm/sum/deploy-use/service-a-server-group) <!--1081776,290B66D8-C735-4895-B59A-DD732D84A697-->
- [비즈니스용 Windows Hello](/sccm/protect/deploy-use/windows-hello-for-business-settings)(이전의 *Passport for Work*) <!--1245704,8BCA2642-3719-4862-A355-9D39C979E1B4-->
- [관리형 PC에 대한 조건부 액세스](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)  <!--1191496,1CD5B9FC-022E-4A78-89F5-DEA58B6F5050-->

> [!Tip]  
> 사용하려면 동의가 필요한 기능에 대한 자세한 내용은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  
>
> 기술 미리 보기 분기에만 제공되는 기능에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.


## <a name="bkmk_prerelease"></a> 업데이트에서 시험판 기능 사용

현재 분기에는 프로덕션 환경의 초기 테스트를 위한 시험판 기능이 포함되어 있습니다. 자세한 내용은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.


## <a name="bkmk_faq"></a> 질문과 대답

### <a name="why-dont-i-see-certain-updates-in-my-console"></a>콘솔에서 특정 업데이트가 표시되지 않는 이유는 무엇인가요?

Microsoft 클라우드 서비스와 성공적으로 동기화한 후 콘솔에서 특정 업데이트를 찾을 수 없는 경우 다음 이유 중 하나로 인해 이 동작이 발생할 수 있습니다.  

- 인프라에서 사용하지 않는 구성이 업데이트에 필요하거나 현재 제품 버전에서 업데이트를 받는 데 필요한 필수 구성 요소가 충족되지 않습니다.  

    누락된 업데이트에 필요한 구성 및 필수 구성 요소가 있다고 생각되면 서비스 연결 지점이 온라인 모드인지 확인합니다. 그런 다음 **업데이트 및 서비스** 노드에서 **업데이트 확인** 옵션을 사용하여 확인을 강제로 적용합니다. 서비스 연결 지점이 오프라인 모드인 경우 서비스 연결 도구를 사용하여 클라우드 서비스와 수동으로 동기화합니다.  

- Configuration Manager 콘솔에서 업데이트를 볼 수 있는 올바른 역할 기반 관리 권한이 계정에 없습니다. 자세한 내용은 [업데이트 관리 권한](#assign-permissions-to-view-and-manage-updates-and-features)을 참조하세요.  
