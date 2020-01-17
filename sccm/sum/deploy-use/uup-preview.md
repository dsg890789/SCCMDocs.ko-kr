---
title: UUP 미리 보기
titleSuffix: Configuration Manager
description: UUP 통합 미리 보기 지침
ms.date: 11/15/2019
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: f06955ac-70ed-424d-a3e7-6b80ff2e114f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: bf72755de71d9e044f79f92f148c6c3842d93bc6
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75818709"
---
# <a name="uup-private-preview-instructions"></a>UUP 프라이빗 미리 보기 지침

> [!Note]  
> 이 정보는 정식으로 출시되기 전에 대폭 수정될 수 있는 미리 보기 기능과 관련이 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

## <a name="introduction"></a>소개

통합 업데이트 플랫폼 (UUP)은 소비자 및 엔터프라이즈 장치가 비즈니스용 Windows 업데이트에서 업데이트를 수신 하는 데 사용 하는 패키징 및 게시 플랫폼입니다. UUP 비공개 미리 보기 프로그램은 Microsoft Configuration Manager에서 제공 하는 최신 업데이트 사용의 유효성을 확인 하는 데 도움이 되는 고객을 위한 것으로, 고객이 현재 Windows 서비스에 보고 하는 문제를 해결 하는 데 도움이 됩니다. 이러한 업데이트는 현재 공개적으로 사용할 수 없습니다.

UUP에 대한 자세한 내용은 다음 Windows 블로그 게시물을 참조하세요. [UUP(Unified Update Platform)에 대한 업데이트](https://blogs.windows.com/windowsexperience/2017/03/02/an-update-on-our-unified-update-platform-uup/).

## <a name="benefits"></a>이점

Windows 10 UUP 기능 및 누적 업데이트는 고객이 현재 Windows 서비스를 사용 하 여 보고 하는 여러 문제를 해결 하는 데 도움이 됩니다.

### <a name="feature-updates"></a>기능 업데이트

- UUP 기능 업데이트를 사용 하는 경우 Windows 업데이트 프로세스는 UUP (주문형 기능) 및 언어 팩을 유지 합니다.

- 바로 최신 보안 준수 수준으로 업데이트 합니다. 기능 업데이트 후에 즉시 보안 업데이트를 설치할 필요는 없습니다. Microsoft는 매월 최신 누적 보안 업데이트를 사용 하 여 새로운 기능 업데이트를 게시 합니다. 매월 대부분의 기능 업데이트 콘텐츠를 다운로드 하거나 배포할 필요가 없습니다. 누적 업데이트를 사용 하 여 공유 하는 보안 업데이트만 다운로드 합니다.

### <a name="cumulative-updates"></a>누적 업데이트

- UUP 누적 업데이트는 월별 누적 보안 업데이트를 통한 서비스 스택 업데이트(SSU)를 포함합니다. UUP를 통한 누적 업데이트를 통해 이러한 두 업데이트의 오케스트레이션 문제를 해결할 수 있습니다. 이를 통해 누적 업데이트를 설치 하기 위해 서비스 스택 업데이트가 준비 되었는지 확인할 수 있습니다. 이러한 관계를 관리 하 고 오케스트레이션 할 필요는 없습니다.

- UUP를 사용 하는 누적 업데이트를 사용 하면 사용자가 해당 콘텐츠를 오프 라인으로 배포할 수 있습니다. 이 동작을 통해 사용자는 요청 시 추가할 수 있습니다. 사용자는 인터넷에서 다운로드할 필요가 없으며,이 콘텐츠를 사전 준비 하는 방법을 알아낼 필요가 없습니다.

## <a name="set-up"></a>설정

### <a name="1-send-your-wsus-id-to-microsoft"></a>1. Microsoft에 WSUS ID 보내기

UUP 비공개 미리 보기에 참여 하려면 WSUS ID를 UUP 미리 보기 연락처와 공유 합니다. Microsoft는 WSUS 환경을 UUP 미리 보기 프로그램으로 승인 합니다. 이 ID가 없으면, 미리 보기가 공개로 설정될 때까지 모든 UUP 업데이트를 볼 수 없습니다.

WSUS ID를 가져오려면 다음 PowerShell 스크립트를 실행 합니다.

```PowerShell
$server = Get-WsusServer
$config = $server.GetConfiguration()
$config.ServerId

# also check MUUrl
$config.MUUrl
```

**MUUrl** 속성은 `https://sws.update.microsoft.com`이어야 합니다. 변경 하려면 다음 지원 문서에서 해결 방법을 참조 하세요. [SoapException을 사용 하 여 WSUS 동기화가 실패](https://support.microsoft.com/help/4482416/wsus-synchronization-fails-with-soapexception)합니다.

### <a name="2-update-configuration-manager"></a>2. Configuration Manager 업데이트

Configuration Manager 사이트에 다음 변경을 수행하여 이 UUP 미리 보기를 지원합니다.

#### <a name="diagnostics-and-usage-data-level"></a>진단 및 사용량 데이터 수준

이 미리 보기 기간 동안 Configuration Manager 진단 및 데이터 사용량 수준을 증가하는 것이 좋습니다. **전체** 수준을 통해 Microsoft에서는 이 새로운 기능으로 문제를 효과적으로 분석하고 해결합니다. 자세한 내용은 [버전 1906의 진단 사용량 데이터 수집 수준](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1906)을 참조하세요.

#### <a name="install-the-latest-update"></a>최신 업데이트 설치

1. 다음 업데이트 중 하나로 사이트를 업데이트 합니다.

    - [업데이트 롤업으로](https://support.microsoft.com/help/4500571) 버전 1902
    - [버전 1906](/sccm/core/servers/manage/checklist-for-installing-update-1906)

    자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.

2. 클라이언트 업데이트  

    - 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  

    - *약 6GB의 사용되지 않은 콘텐츠를 클라이언트에 불필요하게 다운로드*하지 않도록 UUP 업데이트를 대상으로 하는 모든 클라이언트를 업데이트합니다.

### <a name="3-update-windows-clients-to-a-supported-version"></a>3. Windows 클라이언트를 지원되는 버전으로 업데이트

업데이트를 성공적으로 설치 하려면 다음 업데이트를 모두 설치 합니다.

1. 특정 최소 누적 월별 호환성 수준입니다.

2. Microsoft 업데이트 카탈로그에서 누적 되지 않은 특정 비보안 업데이트입니다. 배포를 위한 Configuration Manager로 업데이트를 가져오려면 [Microsoft 업데이트 카탈로그에서 업데이트 가져오기](/sccm/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)를 참조 하세요.

#### <a name="supported-versions-of-windows-10-and-required-updates"></a>지원 되는 버전의 Windows 10 및 필수 업데이트

| Windows 10 버전 | 최소 준수 수준 | 추가 카탈로그 업데이트 |
| ------------------ | ------------------------ | ------------------ |
| **Windows 10, 버전 1903** | RTM | 2019 년 11 월 7 일, [KB4529943](https://www.catalog.update.microsoft.com/search.aspx?q=4529943) |
| **Windows 10, 버전 1809** | 8 월 2019, [KB4511553](https://support.microsoft.com/help/4511553/windows-10-update-kb4511553) | 2019 년 11 월 7 일, [KB4514987](https://www.catalog.update.microsoft.com/search.aspx?q=4514987) |
| **Windows 10, 버전 1803** | 4 월 2019 [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464) | 2019 년 11 월 7 일, [KB4512745](https://www.catalog.update.microsoft.com/search.aspx?q=4512745) |
| **Windows 10, 버전 1709** | 4 월 2019 [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) | 2019 년 11 월 7 일, [KB4512744](https://www.catalog.update.microsoft.com/search.aspx?q=4512744) |

> [!IMPORTANT]
> - 11 월 7 일, 2019 추가 카탈로그 업데이트를 적용 하기 전에 클라이언트에 11 월 12 일 2019 업데이트를 적용 하는 경우 UUP을 지 원하는 데 필요한 Windows 업데이트 에이전트 변경 내용을 덮어쓰게 됩니다. 해당 시나리오에서 클라이언트를 재구성 하려면 2019 업데이트가 설치 된 후에 추가 카탈로그 업데이트를 적용 합니다.
> - 클라이언트에 기능 업데이트를 적용 하는 경우 업그레이드가 완료 된 후 추가 카탈로그 업데이트를 다시 설치 해야 합니다.
> - 기능 업데이트를 쉽게 테스트 하려면 업데이트를 Configuration Manager으로 가져옵니다. 자세한 내용은 [Microsoft 업데이트 카탈로그에서 업데이트 가져오기](/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)를 참조 하세요. 기능 업데이트가 완료 되 면 추가 카탈로그 업데이트는 **필수**로 표시 되며,이를 통해 상위 수준 OS 버전에 자동으로 배포할 수 있습니다.

### <a name="4-allow-clients-to-download-delta-content-when-available"></a>4. 클라이언트가 사용 가능한 경우 델타 콘텐츠를 다운할 수 있도록 허용

다운로드 업데이트가 제대로 다운로드 되도록 클라이언트 설정을 사용 하도록 설정 하 여 클라이언트에서 **사용 가능한 경우 델타 콘텐츠를 다운로드할 수**있도록 합니다. 이 설정을 사용 하면 Configuration Manager Windows 업데이트 에이전트 (WUA)에서 클라이언트에 다운로드 하는 데 필요한 콘텐츠를 결정할 수 있습니다. 이 동작은 Configuration Manager 클라이언트가 UUP 업데이트와 연결 된 모든 콘텐츠를 다운로드 하는 기본이 아닌입니다. 이 설정을 사용 하도록 설정 하면 각 UUP 업데이트에서 필요한 추가 콘텐츠가 WUA에 의해 결정 됩니다. 예를 들어 필요한 항목 d 및 언어 팩만 있으면 됩니다.

이 설정을 사용 하도록 설정 하면 인터넷에서 서버 콘텐츠를 다운로드 하는 것에 영향을 주지 않습니다. 클라이언트 다운로드에만 적용 됩니다. 클라이언트에 UUP 업데이트를 배포 하기 전에이 설정을 UUP에 대해 지원 되는 버전을 충족 하는 클라이언트에 적용 합니다. 필수 구성 요소 클라이언트 업데이트는 WSUS 및 Configuration Manager의 업데이트에 대 한 호환성 문제를 해결 합니다.

이 클라이언트 설정에 대한 자세한 내용은 [클라이언트 설정 정보 - 소프트웨어 업데이트](/sccm/core/clients/deploy/about-client-settings#allow-clients-to-download-delta-content-when-available)를 참조하세요.

### <a name="5-review-your-software-update-infrastructure"></a>5. 소프트웨어 업데이트 인프라 검토

UUP 업데이트를 동기화 하기 전에 ADR (자동 배포 규칙) 및 서비스 계획을 검토 합니다. 이러한 업데이트를 자동으로 배포 하지 않으려면 ADRs를 수정 하 여 필터링 합니다. 자세한 내용은 [동기화 된 UUP 업데이트를 찾는 방법](#how-to-find-synced-uup-updates)을 참조 하세요. 기본적으로 기존 서비스 계획은 UUP 업데이트만 배포 합니다. 서비스 계획을 수정 하 여이 동작을 변경할 수 있습니다.

준수 보고서를 검토 하 고 필요에 따라 수정 합니다. 예를 들어 모든 제품에 대 한 규정 준수를 측정 하는 경우, 이제 UUP 및 UUP 누적 업데이트가 모두 표시 됩니다. 장치는 두 가지 유형의 업데이트에 대 한 호환성을 보고 합니다. 규정 준수 보고서가이 변경 내용을 처리 하는지 확인 합니다.

## <a name="enable-uup-and-start-testing"></a>UUP 사용 및 테스트 시작

### <a name="select-products-and-classifications-to-sync"></a>동기화할 제품 및 분류 선택

UUP 업데이트 동기화를 시작할 준비가 되 면 Microsoft에서 WSUS ID를 승인한 후 새 제품을 사용 하도록 설정 합니다.

1. [소프트웨어 업데이트를 동기화하여](/sccm/sum/get-started/synchronize-software-updates) 새 제품을 채웁니다.  

2. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.

3. CAS(중앙 관리 사이트) 또는 독립 실행형 기본 사이트 중 하나인 최상위 사이트를 선택합니다.

4. 리본에서 **사이트 구성 요소 구성**을 선택하고 **소프트웨어 업데이트 지점**을 선택합니다.

5. **제품** 탭으로 전환 하 고 다음 제품 중 하나 이상을 선택 합니다. 

    - **Windows 10 UUP 미리 보기**
    - **Windows Server UUP 미리 보기**

6. **분류** 탭으로 전환 하 고 다음 옵션을 선택 합니다.  

    - **보안 업데이트**: 누적 업데이트를 보려면  
    - **업그레이드**: UUP 기능 업데이트를 보려면  

7. 소프트웨어 업데이트를 다시 동기화하여 새 UUP 업데이트를 확인합니다.

### <a name="how-to-find-synced-uup-updates"></a>동기화된 UUP 업데이트를 찾는 방법

업데이트를 환경에 동기화 한 후 Configuration Manager 콘솔에서 찾아 테스트 합니다. 다음 두 가지 방법으로 미리 보기 업데이트를 찾을 수 있습니다.

- 이러한 미리 보기 업데이트는 별도의 제품에 있으므로 제품을 사용 하 여 이러한 업데이트를 찾도록 필터링 합니다. 서비스 계획의 제품 필터를 사용 하 여 UUP 또는 UUP 기능 업데이트를 배포 합니다.  

- **소프트웨어 라이브러리**의 **모든 소프트웨어 업데이트** 및 **모든 Windows 10 업데이트** 노드에 새로운 선택적인 **태그** 열이 있습니다. 이 속성은 ADRs에서 필터로도 사용할 수 있습니다. UUP 업데이트의 경우 `UUP`에 대해이 필드를 검색 합니다. UUP 업데이트의 경우 비어 있습니다.  

### <a name="updates-available-during-preview"></a>미리 보기 동안 사용 가능한 업데이트

Microsoft에서 릴리스된 모든 Windows 10 업데이트에 대 한 자세한 내용은 [windows 10 릴리스 정보](https://docs.microsoft.com/windows/release-information/)를 참조 하세요.

#### <a name="cumulative-updates-to-test"></a>테스트에 대 한 누적 업데이트

여러 개의 UUP 태그가 지정 된 업데이트를 사용할 수 있는 반면, **2019 년 9 월** (2019-09) 이상 버전부터 시작 합니다. 예를 들면 다음과 같습니다.

- 2019-09 x64 기반 시스템용 Windows 10 버전 1809 누적 업데이트 (KB4512578) (영문)
- 2019-09 x64 기반 시스템용 Windows 10 버전 1803 누적 업데이트 (KB4516058) (영문)
- 2019-09 x64 기반 시스템용 Windows 10 버전 1709 누적 업데이트 (KB4516066) (영문)

#### <a name="feature-updates-to-test"></a>테스트할 기능 업데이트

여러 개의 UUP 태그가 지정 된 업데이트가 표시 될 수 있지만, **9 월 2019** (2019-09b) 업데이트 이상 버전부터 시작 합니다. 예를 들면 다음과 같습니다.

- Windows 10 버전 1809 x64 2019-09B로 기능 업데이트
- Windows 10 버전 1803 x64 2019-09B로 기능 업데이트

## <a name="scenarios-to-test"></a>테스트할 시나리오

### <a name="test-feature-updates"></a>테스트 기능 업데이트

- 선택한 보안 준수 수준으로 직접 업데이트  

- 업데이트 전에 Ods 및 언어 팩을 설치 합니다. 업데이트가 이러한 구성 요소를 유지 하는지 확인 합니다.  

### <a name="test-cumulative-updates"></a>누적 업데이트 테스트

미리 보기 중에는 연속 되는 여러 업데이트에 대해 UUP 유형 업데이트를 사용 하 여 클라이언트의 호환성을 유지 합니다. 이 테스트는 진행 중인 동작을 이해 하는 데 도움이 됩니다.

### <a name="test-content"></a>테스트 콘텐츠

각 주 버전 (1809, 1803, 1709), 아키텍처 및 언어 조합에 대 한 첫 번째 업데이트는 큰 것으로 나타납니다. 이 크기는 더 이상 사용 되지 않는 업데이트를 사용 하 여 이전에 표시 한 것과 비교 하 여 파일 수 및 디스크 공간입니다. 이 추가 콘텐츠는 주로 누적 업데이트에 대한 모든 FOD 및 언어 팩에 사용됩니다. 기능 업데이트의 경우 첫 번째 업데이트에 대 한 추가 내용이 더 많이 있습니다.

이후 누적 및 기능 업데이트의 경우 사이트에서 다운로드 하 여 배포 하는 새 콘텐츠의 양은 훨씬 더 작습니다. 업데이트 간에 모든 패키지 및 언어 팩 콘텐츠를 지능적으로 공유 합니다. 이 공유 콘텐츠를 redownload 하거나 재배포할 필요가 없습니다. 미리 보기 중 Windows 10 버전 1709 및 1803에서이 월간 다운로드는 UUP 시나리오의 누적 업데이트 크기와 동일 합니다. Windows 10 버전 1809 이상에서 누적 업데이트의 증분 다운로드는 매달 훨씬 더 작습니다.

*비표준*를 위해 12 개월 동안 다운로드 하 여 배포 된 전체 콘텐츠를 확인 하는 경우 Windows 10 버전 1803은 uup의 버전 1809과 동일 해야 합니다. 릴리스 전체 수명 동안 다운로드 되 고 배포 되는 전체 콘텐츠는 버전 1809에서 더 작습니다.

### <a name="supported-content-channels"></a>지원되는 콘텐츠 채널

미리 보기의 경우 일반적인 실제 시나리오를 테스트 합니다. UUP은 다음을 비롯 한 모든 콘텐츠 채널을 지원 합니다.

- Windows 배달 최적화(DO)
  - DO를 사용 하는 경우 올바르게 구성 되었는지 확인 합니다. 자세한 내용은 [Windows 10 업데이트 배달 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)를 참조하세요.
- Configuration Manager 피어 캐시
- Windows BranchCache
- **배포 패키지 없음** 옵션을 사용 하 고 클라이언트는 Microsoft 업데이트에서 바로 다운로드 합니다. 배달 최적화와 함께이 옵션을 사용 합니다.
- 타사 대체 콘텐츠 공급자

콘텐츠 채널에 대 한 자세한 내용은 [Windows 10 업데이트 배달 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)를 참조 하세요.

<!-- TODO: Addlink to WSUS Perf documentation-->
