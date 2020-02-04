---
title: 릴리스 정보
titleSuffix: Configuration Manager
description: Microsoft 지원 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해 알아봅니다.
ms.date: 01/27/2020
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 5a03df7bb4e9860b34e7d2064e1006206c1d8f89
ms.sourcegitcommit: d2b6450fbc75e9937b090ab7d8a5e1d524c92f87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76813827"
---
# <a name="release-notes-for-configuration-manager"></a>Configuration Manager의 릴리스 정보

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager에서는 제품 릴리스 정보가 긴급한 문제로 제한됩니다. 이러한 문제는 제품에서 아직 해결되지 않았거나 Microsoft 지원 기술 자료 문서에서 자세히 설명되지 않은 문제입니다.  

기능별 문서에는 핵심 시나리오에 영향을 주는 알려진 문제에 대한 정보가 포함됩니다.  

이 문서에는 Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. 기술 미리 보기 분기에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.  

다른 버전에서 도입된 새 기능에 대한 자세한 내용은 다음 문서를 참조하세요.

- [버전 1910의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1910)
- [버전 1906의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1906)  
- [버전 1902의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1902)
- [버전 1810의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1810)

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22release+notes+-+Configuration+Manager%22&locale=en-us`


## <a name="set-up-and-upgrade"></a>설치 및 업그레이드  

### <a name="client-automatic-upgrade-happens-immediately-for-all-clients"></a>클라이언트 자동 업그레이드는 모든 클라이언트에 대해 즉시 실행됨

<!-- 6040412 -->

*버전 1910에 적용*

사이트에서 [자동 클라이언트 업그레이드](/configmgr/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 사용하는 경우 사이트를 버전 1910로 업데이트하면 사이트가 성공적으로 업데이트된 후에 모든 클라이언트가 즉시 업그레이드됩니다. 클라이언트가 정책을 받는 경우에만 임의 설정됩니다(기본적으로 1시간마다). 많은 클라이언트를 사용하는 큰 사이트의 경우 이 동작으로 인해 많은 양의 네트워크 트래픽 및 스트레스 배포 지점이 소비될 수 있습니다.

영향을 받는 버전에 대한 자세한 내용은 [Configuration Manager 현재 분기, 버전 1910용 클라이언트 업데이트](https://support.microsoft.com/help/4538166)를 참조하세요.

### <a name="site-server-in-passive-mode-doesnt-update-configurationmof"></a>수동 모드의 사이트 서버가 configuration.mof를 업데이트하지 않음

<!-- 5787848 -->

*버전 1910에 적용*

사이트에 [수동 모드의 사이트 서버](/configmgr/core/servers/deploy/configure/site-server-high-availability)가 포함된 경우 사이트를 업데이트하면 인벤토리 사용자 지정이 손실될 수 있습니다. 현재 사이트 서버를 장애 조치(failover)하는 경우 사이트가 configuration.mof를 동기화하지 않습니다.

이 문제를 해결하려면 사이트의 configuration.mof를 수동으로 백업 및 복원하세요.

### <a name="setup-prerequisite-warning-on-domain-functional-level-on-server-2019"></a>Server 2019에서 도메인 기능 수준에 대한 필수 구성 요소 경고 설정

<!-- 4904376 -->

*버전 1906에 적용*

Windows Server 2019를 실행하는 도메인 컨트롤러가 있는 환경에서 버전 1906에 대한 업데이트를 설치하는 경우 도메인 기능 수준에 대한 필수 구성 요소 검사는 다음 경고를 반환합니다.

`[Completed with warning]:Verify that the Active Directory domain functional level is Windows Server 2003 or later`

#### <a name="workaround"></a>해결 방법

경고를 무시합니다.

### <a name="azure-ad-user-discovery-and-collection-group-sync-dont-work-after-site-expansion"></a>사이트 확장 후 Azure AD 사용자 검색 및 컬렉션 그룹 동기화가 작동하지 않음

<!-- 4797313 -->
*버전 1906에 적용*

다음 기능 중 하나를 구성합니다.

- Azure Active Directory 사용자 그룹 검색
- Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화

그런 다음 독립 실행형 기본 사이트를 중앙 관리 사이트가 있는 계층 구조로 확장하면 SMS_AZUREAD_DISCOVERY_AGENT.log에 다음과 같은 오류가 표시됩니다.

`Could not obtain application secret for tenant xxxxx. If this is after a site expansion, please run "Renew Secret Key" from admin console.`

#### <a name="workaround"></a>해결 방법

Azure AD에서 앱 등록에 연결된 키를 갱신합니다. 자세한 내용은 [비밀 키 갱신](/sccm/core/servers/deploy/configure/azure-services-wizard#bkmk_renew)을 참조하세요.


### <a name="cloud-service-manager-component-stopped-on-site-server-in-passive-mode"></a>클라우드 서비스 관리자 구성 요소가 수동 모드의 사이트 서버에서 정지

<!--VSO 2858826, SCCMDocs issue 772-->
*적용 대상: Configuration Manager 버전 1806*

[서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)이 [수동 모드의 사이트 서버](/sccm/core/servers/deploy/configure/site-server-high-availability)에 배치되면 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)의 배포 및 모니터링이 시작되지 않습니다. 클라우드 서비스 관리자 구성 요소(SMS_CLOUD_SERVICES_MANAGER)가 중지 상태에 있습니다.

#### <a name="workaround"></a>해결 방법

서비스 연결점 역할을 다른 서버로 이동합니다.


<!-- ## Backup and recovery  -->

<!--## Client deployment and upgrade-->
## <a name="application-management"></a>애플리케이션 관리

### <a name="unable-to-get-certificate-for-powershell-error-when-deploying-microsoft-edge-version-77-and-later"></a>Microsoft Edge 버전 77 이후를 배포할 때 Powershell 오류에 대한 인증서를 가져올 수 없음
<!--5769384-->
*적용 대상: Configuration Manager 버전 1910*

언어가 스웨덴어, 헝가리어 또는 일본어로 설정된 OS에서 Configuration Manager 콘솔을 실행할 경우 Microsoft Edge 버전 77 이상을 배포할 때 다음과 같은 오류가 발생합니다.

- Powershell에 대한 인증서를 가져올 수 없습니다.

이 오류는 `AdminConsole\bin` 디렉터리에 스웨덴어, 헝가리어 또는 일본어에 대한 `scripts` 폴더가 없기 때문에 발생합니다. 스크립트 폴더는 해당 언어에 대해 현지화되어 있습니다.

#### <a name="workaround"></a>해결 방법

`AdminConsole\bin` 디렉터리에 `scripts`라는 폴더를 만듭니다. 현지화된 폴더에서 새로 만든 `scripts` 폴더로 파일을 복사합니다. 파일을 복사한 후에 Microsoft Edge 버전 77 이상을 배포합니다.


## <a name="os-deployment"></a>OS 배포

### <a name="after-passive-site-server-is-promoted-the-default-boot-image-packages-still-have-package-source-on-the-previous-active-server"></a>수동 사이트 서버가 승격된 후에도 기본 부팅 이미지 패키지에는 이전 활성 서버의 패키지 소스가 여전히 있습니다.

<!--3453224, SCCMDocs-pr issue 3097-->
*적용 대상: Configuration Manager 버전 1810*

수동 모드(서버 B)의 사이트 서버가 있는 경우, 사이트 서버를 활성으로 승격할 때 기본 부팅 이미지의 콘텐츠 위치는 이전의 활성 서버(서버 A)를 계속 참조합니다. 서버 A에 하드웨어 오류가 있으면 기본 부팅 이미지를 업데이트하거나 변경할 수 없습니다.

#### <a name="workaround"></a>해결 방법

없음


## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="security-roles-are-missing-for-phased-deployments"></a>단계적 배포에 대한 보안 역할이 누락됨

<!--3479337, SCCMDocs-pr issue 3095-->
*적용 대상: Configuration Manager 버전 1810, 1902*

**OS 배포 관리자** 기본 제공 보안 역할에는 [단계적 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)에 대한 권한이 있습니다. 이러한 권한이 없는 역할은 다음과 같습니다.  

- **애플리케이션 관리자**  
- **애플리케이션 배포 관리자**  
- **소프트웨어 업데이트 관리자**  

**앱 작성자** 역할은 단계적 배포에 대한 일부 권한이 있는 것처럼 보일 수 있지만 배포를 만들 수 없습니다.

이러한 역할이 있는 사용자는 단계적 배포 만들기 마법사를 시작할 수 있으며, 애플리케이션 또는 소프트웨어 업데이트에 대한 단계적 배포를 확인할 수 있습니다. 그러나 마법사를 완료하거나 기존 배포를 변경할 수 없습니다.

#### <a name="workaround"></a>해결 방법

사용자 지정 보안 역할을 만듭니다. 기존 보안 역할을 복사하고, **단계적 배포** 개체 클래스에 다음 권한을 추가합니다.

- 만들기  
- 삭제  
- 수정  
- 읽기  

자세한 내용은 [사용자 지정 보안 역할 만들기](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_CreateSecRole)를 참조하세요.

## <a name="desktop-analytics"></a>Desktop Analytics

### <a name="if-you-use-hardware-inventory-for-distributed-views-you-cant-onboard-to-desktop-analytics"></a>분산 보기에 하드웨어 인벤토리를 사용하는 경우 Desktop Analytics에 등록할 수 없습니다.

<!-- 4950335 -->
*적용 대상: Configuration Manager 버전 1902(업데이트 롤업 포함) 및 버전 1906*

계층 구조가 있고 사이트 복제 링크에서 [분산 보기](/sccm/core/plan-design/hierarchy/database-replication#bkmk_distviews)에 **하드웨어 인벤토리** 사이트 데이터를 사용하도록 설정한 경우 Configuration Manager에서 Desktop Analytics 연결을 구성한 후 M365UploadWorker.log에 다음과 같은 오류가 표시됩니다.

`Unexpected exception 'System.Data.SqlClient.SqlException' Remote access is not supported for transaction isolation level "SNAPSHOT".:    at System.Data.SqlClient.SqlConnection.OnError(SqlException exception, Boolean breakConnection, Action'1 wrapCloseInAction)`

#### <a name="workaround"></a>해결 방법

모든 사이트 복제 링크에서 분산 보기에 **하드웨어 인벤토리** 사이트 데이터를 사용하지 않습니다.


### <a name="console-unexpectedly-closes-when-removing-collections"></a>컬렉션을 제거할 때 콘솔이 예기치 않게 닫힘

<!-- 4749443 -->
*적용 대상: Configuration Manager 버전 1902, 업데이트 롤업’*

사이트를 [Desktop Analytics](/sccm/desktop-analytics/connect-configmgr)에 연결한 후 **Desktop Analytics와 동기화할 특정 컬렉션을 선택**할 수 있습니다. 컬렉션을 제거하고 변경 내용을 적용하는 경우 새 컬렉션을 즉시 추가하면 처리되지 않은 예외가 발생합니다. 콘솔이 예기치 않게 닫힙니다.

#### <a name="workaround"></a>해결 방법

컬렉션을 제거하면 **확인**을 선택하여 속성 창을 닫습니다. 그런 다음 속성을 다시 열어 **Desktop Analytics 연결** 탭에서 새 컬렉션을 추가합니다.

### <a name="pilot-status-tile-shows-some-devices-as-undefined"></a>파일럿 상태 타일에서 일부 디바이스를 ‘정의되지 않음’으로 표시함

<!-- 4547783 -->
*적용 대상: Configuration Manager 버전 1902, 업데이트 롤업’*

Configuration Manager 콘솔을 사용하여 파일럿 배포 상태를 모니터링하는 경우 해당 배포 플랜의 Windows 대상 버전에서 최신 상태인 파일럿 디바이스는 파일럿 상태 타일에 **정의되지 않음**으로 표시됩니다.  

이러한 **정의되지 않음** 디바이스는 해당 배포 계획의 OS 대상 버전에서 **최신 상태**입니다. 추가 작업은 필요하지 않습니다.

## <a name="cloud-services"></a>Cloud Services

### <a name="azure-service-for-us-government-cloud-shows-as-public-cloud"></a>미국 정부 클라우드용 Azure 서비스가 퍼블릭 클라우드로 표시됩니다.

<!-- 6036748 -->

*버전 1910에 적용*

Azure 서비스에 대한 연결을 만들고 **Azure 환경**을 정부 클라우드로 설정하는 경우 연결 속성은 환경을 Azure 퍼블릭 클라우드로 표시합니다. 이 문제는 콘솔에서의 표시 문제일 뿐이며, 서비스는 정부 클라우드에 있습니다. 구성을 확인하려면 사이트 데이터베이스에서 다음 SQL 쿼리를 실행하세요.

```SQL
Select Environment, Name, TenantID From AAD_Tenant_Ex
```

정부 클라우드의 경우 이 쿼리의 결과가 특정 테넌트에 대해 `2`입니다.

### <a name="cant-download-content-from-a-cloud-management-gateway-enabled-for-tls-12"></a>TLS 1.2를 사용하도록 설정된 클라우드 관리 게이트웨이에서 콘텐츠를 다운로드할 수 없음

<!-- 5771680 -->

*버전 1906, 1910 초기 업데이트 링에 적용*

CMG(클라우드 관리 게이트웨이)에서 **클라우드 배포 지점으로 작동하고 Azure Storage에서 콘텐츠를 제공할 수 있도록 허용** 및 **TLS 1.2 적용**을 설정한 경우 콘텐츠 다운로드에 실패할 수 있습니다.

클라이언트의 DataTransferService.log에 다음과 같은 오류가 표시됩니다.

``` log
Request to https://cmg1.contoso.com:443/downloadrestservice.svc/getcontentxmlsecure?pid=CMG00013&cid=CMG00013&tid=GUID:3fb5cf5d-28a5-4460-ab39-9184ca214369&iss=CMDP.IAAS2.CONTOSO.COM&alg=1.2.840.113549.1.1.11&st=2019-11-19T01:44:04&et=2019-11-19T09:44:04 failed with 400
Successfully queued event on HTTP/HTTPS failure for server 'cmg1.contoso.com'.
Error sending DAV request. HTTP code 400, status 'Bad Request'
GetDirectoryList_HTTP('https://cmg1.contoso.com:443/downloadrestservice.svc/getcontentxmlsecure?pid=CMG00013&cid=CMG00013&tid=GUID:3fb5cf5d-28a5-4460-ab39-9184ca214369&iss=CMDP.IAAS2.CONTOSO.COM&alg=1.2.840.113549.1.1.11&st=2019-11-19T01:44:04&et=2019-11-19T09:44:04') failed with code 0x87d0027e.
Error retrieving manifest (0x87d0027e).
```

서버의 CMGContentService.log에 다음과 같은 오류가 표시됩니다.

``` log
ERROR: Exception processing request. Microsoft.WindowsAzure.Storage.StorageException: The underlying connection was closed: An unexpected error occurred on a receive. ---> System.Net.WebException: The underlying connection was closed: An unexpected error occurred on a receive. ---> System.ComponentModel.Win32Exception: The client and server cannot communicate, because they do not possess a common algorithm...
```

이 문제를 해결하려면

- 2019년 12월 20일에 출시되어 전 세계적으로 사용 가능한 1910 버전으로 사이트를 업데이트합니다. 이전에 1910 초기 업데이트 링으로 업데이트한 경우에는 사용 가능할 때 이 빌드로 업데이트해야 합니다.

- 또는 기존의 [클라우드 배포 지점](/configmgr/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)을 사용합니다. 이 역할은 TLS 1.2를 적용하지는 않지만 TLS 1.2가 필요한 클라이언트와 호환됩니다.

## <a name="protection"></a>보호

### <a name="bitlocker-management-appears-in-version-1906"></a>BitLocker 관리가 버전 1906에 표시됩니다.

*버전 1906에 적용*

<!-- 5984688 -->

2019년 11월 21일 이후로 버전 1902 또는 이전 버전에서 버전 1906로 업데이트하는 경우 BitLocker 관리 기능이 설정되고 사용 가능합니다. 이 기능은 버전 1910부터 시작되는 선택적 기능입니다. 버전 1906에서는 지원되지 않습니다. 이 기능을 버전 1906에서 사용하려고 시도하는 경우 예기치 않은 결과가 발생할 수 있습니다. 이 기능을 사용하지 않는 경우에는 영향을 주지 않습니다.

[BitLocker 관리 기능](/configmgr/protect/plan-design/bitlocker-management)을 사용하려면 버전 1910으로 업데이트하세요.
