---
title: 호환성 평가
titleSuffix: Configuration Manager
description: Desktop Analytics에서 Windows 앱 및 드라이버에 대한 호환성 평가를 알아봅니다.
ms.date: 10/23/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ea78f726-b1b3-49b0-8141-d916be48c458
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f0832dc96a5b03e0ed603b76c794444eff7d967
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73049435"
---
# <a name="compatibility-assessment-in-desktop-analytics"></a>Desktop Analytics의 호환성 평가

Windows Analytics의 업그레이드 평가는 일반적입니다. 예를 들어 [주의 필요] 또는 [수정을 사용할 수 있음]입니다. 문제 해결 또는 업그레이드 인사이트를 사용하여 앱 또는 드라이버의 우선 순위를 지정하는 방법에 대한 시각적 표시기는 제공하지 않습니다. Desktop Analytics에서는 이 기능이 **호환성 위험**으로 대체됩니다. Desktop Analytics는 업그레이드 전 시나리오에 대한 배포 보기에서만 앱 평가를 보여 줍니다. Microsoft는 현재 배포 계획에 포함된 머신에서 얻은 인사이트를 기반으로 하여 앱을 분류합니다.

Desktop Analytics에서 사용하는 호환성 평가 범주는 다음과 같습니다.

- **낮음**: 서비스에서 이 앱을 Windows 업그레이드 위험으로 평가할 징후를 찾지 못했습니다. 대상 OS에서 있는 그대로 작동할 가능성이 높습니다.  

- **중간**: 분석에서 수정이 가능하지만 애플리케이션의 기능이 손상되었을 수 있음을 나타냅니다.  

- **높음**: 업그레이드 중 또는 업그레이드 후에 애플리케이션이 실패할 것이 거의 확실합니다. 수정이 필요할 수 있습니다.  

- **알 수 없음**: 앱이 평가되지 않았습니다. *MS의 알려진 문제* 또는 *Ready for Windows*와 같은 다른 인사이트가 없습니다.  

이 값은 배포 계획의 앱 또는 드라이버 자산 목록에서 **호환성 위험** 열의 각 자산에 대해 표시됩니다.


## <a name="app-risk-assessment"></a>앱 위험 평가

![앱 위험 평가 원본의 다이어그램](media/app-risk-assessment-sources.png)

Desktop Analytics에서 애플리케이션에 대한 평가 등급을 생성하는 데 사용하는 몇 가지 원본은 다음과 같습니다.

- [Microsoft의 알려진 문제](#microsoft-known-issues)
- [Ready for Windows 카탈로그](#ready-for-windows)
- [고급 인사이트](#advanced-insights)

앱의 각 원본에 대한 평가는 Desktop Analytics에서 확인할 수 있습니다. 배포 계획의 앱 자산 목록에서 개별 앱을 선택하여 해당 속성 플라이아웃 창을 엽니다. 전체 추천 사항 및 평가 수준이 표시됩니다. **호환성 위험 요소** 섹션에는 이러한 평가에 대한 세부 정보가 표시됩니다.


## <a name="microsoft-known-issues"></a>Microsoft의 알려진 문제

Desktop Analytics는 Microsoft 앱 호환성 데이터베이스에서 알려진 문제를 확인합니다. 이 데이터베이스를 사용하여 공개적으로 사용 가능한 애플리케이션에 대한 Microsoft 또는 다른 게시자의 기존 호환성 블록을 결정합니다. 이 확인은 선택한 배포 계획에 대한 대상 OS에만 적용됩니다.

앱 속성 창에서 **MS의 알려진 문제**로 표시되는 문제는 다음과 같습니다.

### <a name="asset-is-removed-during-upgrade"></a>업그레이드 중에 자산이 제거됨

Windows에서 애플리케이션 또는 드라이버와의 호환성 문제를 감지했습니다. 자산이 새 OS 버전으로 마이그레이션되지 않습니다. 업그레이드를 계속하려면 아무 작업도 수행할 필요가 없습니다. 호환되는 버전의 애플리케이션 또는 드라이버를 새 OS 버전에 설치합니다.

<!-- 3594545 -->
Windows에서 이러한 자산을 부분적으로 또는 완전히 제거할 수 있습니다.

- 전체 제거: Windows 설치 프로그램이 업그레이드 중에 디바이스에서 앱 또는 드라이버를 완전히 제거합니다.
- 부분 제거: Windows 설치 프로그램이 디바이스에서 앱 또는 드라이버를 부분적으로 제거합니다. Windows를 업그레이드한 후에 수동으로 제거해야 합니다.

두 경우 모두에서 Windows를 업그레이드한 후에는 사용자가 드라이버와 연결된 앱 또는 하드웨어를 사용할 수 없습니다.

Desktop Analytics 포털에서 이 추천 사항을 확인하려면 다음을 수행합니다.

1. 배포 계획에서 **파일럿 준비**를 선택합니다.
1. 목록에서 자산을 선택합니다.
1. 사이드 창에서 호환성 위험 요소 및 추천 사항을 확인합니다.

![Desktop Analytics 포털의 자산 추천 사항에 대한 스크린샷](media/3594545-app-removed.png)

### <a name="blocking-upgrade"></a>업그레이드 차단

Windows에서 차단 문제를 감지했으며, 업그레이드 중에 애플리케이션을 제거할 수 없습니다. 새 OS 버전에서 작동하지 않을 수 있습니다. 업그레이드하기 전에 애플리케이션을 제거합니다. 새 OS 버전에 다시 설치하고 테스트합니다.

### <a name="blocking-upgrade-but-can-be-reinstalled-after-upgrading"></a>업그레이드를 차단하지만 업그레이드 후에 다시 설치할 수 있음

애플리케이션이 새 OS 버전과 호환되지만 마이그레이션하지 않습니다. Windows를 업그레이드하기 전에 애플리케이션을 제거합니다. 새 OS 버전에 다시 설치합니다.

### <a name="blocking-upgrade-update-application-to-newest-version"></a>업그레이드 차단, 최신 버전으로 애플리케이션 업데이트

기존 버전의 애플리케이션이 새 OS 버전과 호환되지 않으며 마이그레이션하지 않습니다. 호환되는 버전의 애플리케이션을 사용할 수 있습니다. 업그레이드하기 전에 애플리케이션을 업데이트합니다.

### <a name="disk-encryption-blocking-upgrade"></a>디스크 암호화 차단 업그레이드

애플리케이션의 암호화 기능으로 업그레이드를 차단합니다. Windows를 업그레이드하기 전에 암호화 기능을 사용하지 않도록 설정하고, 업그레이드한 후에 이를 사용하도록 설정합니다.

### <a name="does-not-work-with-new-os-but-wont-block-upgrade"></a>새 OS에서 작동하지 않지만 업그레이드를 차단하지 않음

애플리케이션이 새 OS 버전과 호환되지 않지만 업그레이드를 차단하지 않습니다. 업그레이드를 계속하려면 아무 작업도 수행할 필요가 없습니다. 호환되는 버전의 애플리케이션을 새 OS 버전에 설치합니다.

### <a name="does-not-work-with-new-os-and-will-block-upgrade"></a>새 OS에서 작동하지 않고 업그레이드를 차단함

애플리케이션이 새 OS 버전과 호환되지 않고 업그레이드를 차단합니다. 업그레이드하기 전에 애플리케이션을 제거합니다. 호환되는 버전의 애플리케이션을 사용할 수도 있습니다.

### <a name="evaluate-application-on-new-os"></a>새 OS에서 애플리케이션 평가

Windows에서 애플리케이션을 마이그레이션하지만, 새 OS 버전에서 앱 성능에 영향을 줄 수 있는 문제를 감지했습니다. 업그레이드를 계속하려면 아무 작업도 수행할 필요가 없습니다. 새 OS 버전에서 애플리케이션을 테스트합니다.

### <a name="may-block-upgrade-test-application"></a>업그레이드를 차단할 수 있음, 애플리케이션 테스트

Windows에서 업그레이드를 방해할 수 있는 문제를 감지했지만 추가 조사가 필요합니다. 업그레이드 중에 애플리케이션의 동작을 테스트합니다. 업그레이드를 차단하는 경우 업그레이드하기 전에 제거합니다. 그런 다음, 새 OS 버전에 다시 설치하고 테스트합니다.

### <a name="multiple"></a>여러 개

여러 문제가 애플리케이션에 영향을 줍니다. **쿼리**를 선택하여 Windows에서 감지한 문제에 대한 세부 정보를 확인합니다.

### <a name="reinstall-application-after-upgrading"></a>업그레이드 후 애플리케이션 다시 설치

애플리케이션이 새 OS 버전과 호환되지만 Windows를 업그레이드한 후에는 다시 설치해야 합니다. 업그레이드 프로세스에서 애플리케이션을 제거합니다. 업그레이드를 계속하려면 아무 작업도 수행할 필요가 없습니다. 애플리케이션을 새 OS 버전에 다시 설치합니다.


## <a name="ready-for-windows"></a>Ready for Windows

[Ready for Windows](https://www.readyforwindows.com) 애플리케이션 카탈로그와 서로 연결되는 데이터 원본은 다음과 같습니다.

- 동일한 앱을 보고하는 다른 고객의 진단 데이터
- 디바이스의 호환성 블록과 같은 Microsoft의 추가 검사

가능한 범주는 다음과 같습니다.

- **높은 채택**: 100,000개 이상의 상용 Windows 10 디바이스에서 이 앱을 설치했습니다.  

- **채택**: 10,000개 이상의 상용 Windows 10 디바이스에서 이 앱을 설치했습니다.  

- **데이터 부족**: 이 앱에 대한 정보를 공유하는 상용 Windows 10 디바이스가 너무 적어 Microsoft에서 채택을 분류할 수 없습니다.

- **개발자에게 문의**: 이 버전의 앱과 호환성 문제가 있을 수 있습니다. 자세한 내용은 소프트웨어 공급자에게 문의하는 것이 좋습니다. 자세한 내용은 [Ready for Windows](https://www.readyforwindows.com/)를 참조하세요.  

- **알 수 없음**: 이 버전의 애플리케이션에 사용할 수 있는 Ready for Windows 정보가 없습니다. 다른 버전의 애플리케이션에 대한 정보는 [Ready for Windows](https://www.readyforwindows.com/)에서 사용할 수 있습니다.  

### <a name="support-statement"></a>지원 정책

소프트웨어 공급자가 Windows 10에서 이 애플리케이션의 버전을 하나 이상 지원하는 경우 앱 속성 창에 이 정책이 표시됩니다. [호환성 위험 요소 섹션]에서 **지원 정책**을 확인하세요.



## <a name="advanced-insights"></a>고급 인사이트

Desktop Analytics는 다음과 같은 추가 인사이트를 사용하여 문제를 감지할 수도 있습니다.

### <a name="adopted-version-available"></a>사용 가능한 채택 버전

다른 고객이 많이 채택하는 이 앱의 또 다른 버전이 있습니다. 이 표시는 Ready for Windows의 데이터를 사용합니다. 현재 버전의 업그레이드 차단이 있는 경우 대체 버전을 대신 배포하는 것이 좋습니다.

### <a name="driver-dependency"></a>드라이버 종속성

앱은 드라이버에 종속됩니다. Desktop Analytics는 파일럿 테스트용 앱을 사용하여 재발을 검색하도록 추천합니다. 문제가 있는 경우 게시자에게 문의하여 Windows 10을 준수하는 버전을 요청합니다.

### <a name="additional-insights"></a>추가 인사이트

<!-- 4021225 -->
Configuration Manager 사이트와 클라이언트를 1906 버전으로 업데이트하는 경우 진단 데이터 수준이 [향상됨(제한됨)]으로 설정되면 클라이언트에서 다음과 같은 추가 인사이트도 보고합니다.

> [!Important]  
> 새 Configuration Manager 기능을 모두 활용하려면 사용자를 업데이트한 후 클라이언트를 최신 버전으로 업데이트합니다. 이 시나리오는 클라이언트 버전도 최신 버전이 될 때까지 작동하지 않습니다.

#### <a name="16-bit-apps"></a>16비트 앱

애플리케이션에서 16비트 구성 요소를 모두 제거하고 32비트 또는 64비트 대체 가능한 구성 요소로 바꿉니다. 자세한 내용은 [Windows Vista 및 Windows Server 2008 개발자 사례: 애플리케이션 호환성 쿡북](https://docs.microsoft.com/previous-versions/aa480152\(v=msdn.10\))을 참조하세요.

다른 옵션은 Windows 10에서 지원하기 위해 NTVDM(NT Virtual DOS Machine)을 사용하도록 설정하는 것입니다.

#### <a name="requires-admin-privileges"></a>관리자 권한 필요

앱을 사용하려면 사용자에게 디바이스에 대한 관리 액세스 권한이 있어야 합니다. 관리자 권한이 필요한 이러한 앱에 앱 매니페스트를 사용합니다. 자세한 내용은 [애플리케이션 매니페스트 만들기 및 포함](https://docs.microsoft.com/previous-versions/bb756929\(v=msdn.10\))을 참조하세요.

Desktop Analytics는 파일럿 테스트용 앱을 사용하여 재발을 검색하도록 추천합니다.

#### <a name="java-dependency"></a>Java 종속성

대부분의 Java 애플리케이션은 별도로 설치된 JRE(Java Runtime Environment)를 사용합니다. 이전 JRE 버전은 Windows 10에서 계속 작동할 수 있지만 Oracle에서는 최신 JRE 버전만 지원합니다. 지원되지 않는 이전 JRE를 사용하면 보안 취약성이 있을 수 있습니다. 애플리케이션이 최신 JRE 버전에서 실행되는지 확인하세요.

#### <a name="not-dpi-aware"></a>DPI 인식 안 함

앱에 Windows 10의 고급 화면 해상도와 관련된 표시 문제가 있을 수 있습니다. 앱 매니페스트를 사용하여 DPI 해상도가 높은 문제를 방지합니다. 자세한 내용은 [애플리케이션 매니페스트](https://docs.microsoft.com/windows/desktop/SbsCs/application-manifests)를 참조하세요.

Desktop Analytics는 파일럿 테스트용 앱을 사용하여 재발을 검색하도록 추천합니다.

#### <a name="silverlight-framework"></a>Silverlight 프레임워크

브라우저 기반이 아닌 앱은 Silverlight를 사용하지 않는 것이 좋습니다. Silverlight 5의 지원 종료 날짜는 2021년 10월입니다.

대부분의 최신 웹 브라우저는 Silverlight를 지원하지 않습니다.

| 브라우저 | Support(지원) |
|---------|---------|
| Google Chrome | 지원 종료: 2015년 9월 |
| Firefox | 지원 종료: 2017년 3월 |
| Microsoft Edge | 플러그 인을 사용할 수 없음 |

Desktop Analytics는 파일럿 테스트용 앱을 사용하여 재발을 검색하도록 추천합니다.

#### <a name="net-framework-1011"></a>.NET Framework 1.0/1.1

.NET Framework 1.0 버전은 Windows 10에서 지원되지 않습니다. 1\.1 버전은 Windows 10에서 호환되지 않습니다. 타사 게시자의 앱인 경우 공급업체에 문의하여 Windows 10과 호환되는 버전을 요청하세요. 그렇지 않으면 지원되는 .NET 버전을 사용하도록 애플리케이션을 다시 개발하세요.

#### <a name="net-framework-2030"></a>.NET Framework 2.0/3.0

.NET 2.0 및 3.5 프레임워크는 Windows 10에서 지원됩니다. Windows 기능을 사용하도록 설정해야 할 수도 있습니다. 자세한 내용은 [Windows 10에 .NET Framework 3.5 설치](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)를 참조하세요.

#### <a name="ui-access"></a>UI 액세스

UI 액세스 권한이 있는 애플리케이션은 사용자 인터페이스 제어 수준을 무시하여 바탕 화면에서 더 높은 권한 창에 대한 입력을 구동합니다. 이 설정은 사용자 인터페이스 보조 기술 애플리케이션에만 사용합니다.

앱에서 내게 필요한 옵션 기능을 사용하지 않는 경우 앱 매니페스트의 UI 액세스 플래그를 false로 설정합니다. 자세한 내용은 [애플리케이션 매니페스트 만들기 및 포함](https://docs.microsoft.com/previous-versions/bb756929\(v=msdn.10\))을 참조하세요.

Desktop Analytics는 파일럿 테스트용 앱을 사용하여 재발을 검색하도록 추천합니다.


## <a name="driver-risk-assessment"></a>드라이버 위험 평가

Desktop Analytics는 OS 버전으로 마이그레이션하지 않는 드라이버도 가용성별로 나열하고 그룹화합니다.

Desktop Analytics에서 드라이버에 대한 평가를 확인할 수 있습니다. 배포 계획의 드라이버 자산 목록에서 개별 드라이버를 선택하여 해당 속성 플라이아웃 창을 엽니다. 전체 추천 사항 및 평가 수준이 표시됩니다. **호환성 위험 요소** 섹션에는 이러한 평가에 대한 세부 정보가 표시됩니다.

| 드라이버 가용성 | 필요한 작업 | 의미 | 지침 |
|---------------------|------------------|---------------|----------|
| 기본 제공 | 아니요, 인식 전용 | 현재 설치된 애플리케이션 또는 드라이버 버전이 새 OS 버전으로 마이그레이션하지 않습니다. 호환되는 버전이 새 OS 버전과 함께 설치됩니다. | 업그레이드를 계속하려면 아무 작업도 수행할 필요가 없습니다. |
| Windows 업데이트에서 가져오기 | 예 | 현재 설치된 드라이버 버전이 새 OS 버전으로 마이그레이션하지 않습니다. 호환되는 버전은 Windows 업데이트에서 사용할 수 있습니다. | 컴퓨터가 Windows 업데이트에서 자동으로 업데이트를 받는 경우 아무 작업도 수행할 필요가 없습니다. 그렇지 않으면 Windows를 업그레이드한 후에 Windows 업데이트에서 새 드라이버를 가져옵니다. |
| 기본 제공 및 Windows 업데이트에서 제공 | 예 | 현재 설치된 드라이버 버전이 새 OS 버전으로 마이그레이션하지 않습니다. 업그레이드 중에 새 드라이버가 설치되지만 Windows 업데이트에서 최신 버전을 사용할 수 있습니다. | 컴퓨터가 Windows 업데이트에서 자동으로 업데이트를 받는 경우 아무 작업도 수행할 필요가 없습니다. 그렇지 않으면 Windows를 업그레이드한 후에 Windows 업데이트에서 새 드라이버를 가져옵니다. |
| 공급업체에 문의 | 예 | 드라이버가 새 OS 버전으로 마이그레이션하지 않고, Desktop Analytics에서 호환되는 버전을 찾을 수 없습니다. | 이 문제를 해결하려면 드라이버를 제조하는 IHV(독립 하드웨어 공급업체) 또는 디바이스를 제공한 OEM(원본 장비 제조업체)에 문의하세요. |


## <a name="see-also"></a>참고 항목

Windows 10용 FastTrack Center 혜택은 **Desktop App Assure**에 대한 액세스를 제공합니다. 이 혜택은 Windows 10 및 Office 365 ProPlus 앱 호환성과 관련된 문제를 해결하도록 설계된 새로운 서비스입니다. 자세한 내용은 [Desktop App Assure](https://docs.microsoft.com/fasttrack/win-10-desktop-app-assure)를 참조하세요.
