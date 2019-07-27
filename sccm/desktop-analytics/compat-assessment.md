---
title: 호환성 평가
titleSuffix: Configuration Manager
description: 데스크톱 분석의 Windows 앱 및 드라이버에 대 한 호환성 평가에 대해 알아봅니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ea78f726-b1b3-49b0-8141-d916be48c458
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6181f0e1a502d701ca7337641013a18b03251f9
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68535996"
---
# <a name="compatibility-assessment-in-desktop-analytics"></a>데스크톱 분석의 호환성 평가

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

Windows Analytics의 업그레이드 평가가 일반적입니다. 예를 들면 다음과 같습니다. 주의가 필요 하거나 수정할 수 있습니다. 문제 또는 업그레이드 정보를 사용 하 여 앱 또는 드라이버의 우선 순위를 지정 하는 방법에 대 한 시각적 표시기는 제공 하지 않습니다. 데스크톱 분석은 **호환성 위험**으로이 기능을 대체 합니다. 데스크톱 분석은 업그레이드 전 시나리오에 대 한 배포 보기의 앱에 대 한 평가만 보여 줍니다. Microsoft는 현재 배포 계획에 포함 된 컴퓨터에서 Microsoft가 제공 하는 정보를 기반으로 앱을 분류 합니다.

데스크톱 분석에서 사용 하는 호환성 평가 범주는 다음과 같습니다.

- **낮음**: 서비스가 Windows 업그레이드에 대 한 위험에이 앱을 배치할 신호를 찾지 못했습니다. 대상 OS에서 있는 그대로 작업할 가능성이 높습니다.  

- **보통**: 분석은 재구성이 가능 하더라도 응용 프로그램에 기능이 손상 되었을 수 있음을 나타냅니다.  

- **높음**: 응용 프로그램은 업그레이드 도중 이나 업그레이드 후에 거의 실패 합니다. 수정이 필요할 수 있습니다.  

- **알 수 없음**: 앱이 평가 되지 않았습니다. *MS의 알려진 문제* 또는 *Windows 준비*와 같은 다른 정보는 없습니다.  

배포 계획의 앱 또는 드라이버 자산 목록에서 **호환성 위험** 열의 각 자산에 대해이 값이 표시 됩니다.


## <a name="app-risk-assessment"></a>앱 위험 평가

![앱 위험 평가 원본 다이어그램](media/app-risk-assessment-sources.png)

데스크톱 분석에서 응용 프로그램에 대 한 평가 등급을 생성 하는 데 사용 하는 여러 소스가 있습니다.

- [Microsoft의 알려진 문제](#microsoft-known-issues)
- [Windows 카탈로그 준비 완료](#ready-for-windows)
- [고급 정보](#advanced-insights)

데스크톱 분석에서 앱의 각 원본에 대 한 평가를 찾을 수 있습니다. 배포 계획의 앱 자산 목록에서 개별 앱을 선택 하 여 해당 속성 플라이 아웃 창을 엽니다. 전체 권장 사항 및 평가 수준이 표시 됩니다. **호환성 위험 요소** 섹션에는 이러한 평가에 대 한 세부 정보가 표시 됩니다.


## <a name="microsoft-known-issues"></a>Microsoft의 알려진 문제

데스크톱 분석은 Microsoft 앱 호환성 데이터베이스에서 알려진 문제를 확인 합니다. 이 데이터베이스를 사용 하 여 Microsoft 또는 다른 게시자에서 공개적으로 사용할 수 있는 응용 프로그램에 대 한 기존 호환성 블록을 확인 합니다. 이 확인은 선택한 배포 계획에 대 한 대상 OS에만 적용 됩니다.

응용 프로그램 속성 창에서 다음과 같은 문제를 **알려진 MS 문제로**표시 합니다.

### <a name="application-is-removed-during-upgrade"></a>업그레이드 하는 동안 응용 프로그램이 제거 됨

Windows에서 호환성 문제를 발견 했습니다. 응용 프로그램이 새 OS 버전으로 마이그레이션되지 않습니다. 업그레이드를 계속 하려면 아무 작업도 수행 하지 않아도 됩니다.

### <a name="blocking-upgrade"></a>업그레이드 차단

Windows에서 차단 문제를 발견 하 여 업그레이드 하는 동안 응용 프로그램을 제거할 수 없습니다. 새 OS 버전에서 작동 하지 않을 수 있습니다. 업그레이드 하기 전에 응용 프로그램을 제거 합니다. 새 OS 버전에서 다시 설치 하 고 테스트 합니다.

### <a name="blocking-upgrade-but-can-be-reinstalled-after-upgrading"></a>업그레이드를 차단 하지만 업그레이드 후 다시 설치할 수 있습니다.

응용 프로그램이 새 OS 버전과 호환 되지만 마이그레이션하지 않습니다. Windows를 업그레이드 하기 전에 응용 프로그램을 제거 하십시오. 새 OS 버전에 다시 설치 합니다.

### <a name="blocking-upgrade-update-application-to-newest-version"></a>업그레이드 차단, 최신 버전으로 응용 프로그램 업데이트

응용 프로그램의 기존 버전은 새 OS 버전과 호환 되지 않으며 마이그레이션하지 않습니다. 응용 프로그램의 호환 버전을 사용할 수 있습니다. 업그레이드 하기 전에 응용 프로그램을 업데이트 합니다.

### <a name="disk-encryption-blocking-upgrade"></a>디스크 암호화 차단 업그레이드

응용 프로그램의 암호화 기능으로 업그레이드를 차단 합니다. Windows를 업그레이드 하 고 업그레이드 후에 사용 하도록 설정 하기 전에 암호화 기능을 사용 하지 않도록 설정 합니다.

### <a name="does-not-work-with-new-os-but-wont-block-upgrade"></a>새 OS에서는 작동 하지 않지만 업그레이드는 차단 하지 않음

응용 프로그램은 새 OS 버전과 호환 되지 않지만 업그레이드는 차단 되지 않습니다. 업그레이드를 계속 하려면 아무 작업도 수행 하지 않아도 됩니다. 새 OS 버전에 호환 되는 버전의 응용 프로그램을 설치 합니다.

### <a name="does-not-work-with-new-os-and-will-block-upgrade"></a>새 OS에서 작동 하지 않고 업그레이드를 차단 합니다.

응용 프로그램이 새 OS 버전과 호환 되지 않으며 업그레이드가 차단 됩니다. 업그레이드 하기 전에 응용 프로그램을 제거 하십시오. 응용 프로그램의 호환 버전을 사용할 수 있습니다.

### <a name="evaluate-application-on-new-os"></a>새 OS에서 응용 프로그램 평가

Windows에서 응용 프로그램을 마이그레이션하고 새 OS 버전의 앱 성능에 영향을 줄 수 있는 문제를 발견 했습니다. 업그레이드를 계속 하려면 아무 작업도 수행 하지 않아도 됩니다. 새 OS 버전에서 응용 프로그램을 테스트 합니다.

### <a name="may-block-upgrade-test-application"></a>업그레이드를 차단할 수 있습니다. 응용 프로그램 테스트

Windows에서 업그레이드를 방해할 수 있는 문제를 발견 했지만 추가 조사가 필요 합니다. 업그레이드 하는 동안 응용 프로그램의 동작을 테스트 합니다. 업그레이드를 차단 하는 경우 업그레이드 하기 전에 제거 합니다. 그런 다음 다시 설치 하 고 새 OS 버전을 테스트 합니다.

### <a name="multiple"></a>여러 개

여러 문제가 응용 프로그램에 영향을 줍니다. Windows에서 검색 된 문제에 대 한 세부 정보를 보려면 **쿼리** 를 선택 합니다.

### <a name="reinstall-application-after-upgrading"></a>업그레이드 후 응용 프로그램 다시 설치

응용 프로그램이 새 OS 버전과 호환 되지만, Windows를 업그레이드 한 후에는 응용 프로그램을 다시 설치 해야 합니다. 업그레이드 프로세스는 응용 프로그램을 제거 합니다. 업그레이드를 계속 하려면 아무 작업도 수행 하지 않아도 됩니다. 새 OS 버전에 응용 프로그램을 다시 설치 합니다.


## <a name="ready-for-windows"></a>Windows 준비 완료

Windows 응용 프로그램 카탈로그 [준비](https://www.readyforwindows.com) 는 다음과 같은 데이터 원본에 상관 관계를 적용 합니다.

- 동일한 앱을 보고 하는 다른 고객의 진단 데이터
- Microsoft에서 장치에 대 한 호환성 블록과 같은 추가 검사

가능한 범주는 다음과 같습니다.

- **매우 채택**: 최소 10만 상용 Windows 10 장치에서이 앱을 설치 했습니다.  

- **채택**: 최소 1만 상용 Windows 10 장치에서이 앱을 설치 했습니다.  

- **데이터 부족**: 상용 Windows 10 장치가 너무 적으면 Microsoft에서 채택 하는 앱의 정보를 공유 하 고 있습니다.

- **개발자에 게 문의**: 이 버전의 앱과 호환성 문제가 있을 수 있습니다. 자세한 내용은 소프트웨어 공급자에 게 문의 하는 것이 좋습니다. 자세한 내용은 [Windows 준비](https://www.readyforwindows.com/)를 참조 하세요.  

- **알 수 없음**: 이 응용 프로그램의이 버전에 사용할 수 있는 Windows 정보는 준비 되어 있지 않습니다. [Windows 준비](https://www.readyforwindows.com/)에서 다른 버전의 응용 프로그램에 대 한 정보를 사용할 수 있습니다.  

### <a name="support-statement"></a>지원 문

소프트웨어 공급자가 Windows 10에서이 응용 프로그램의 버전을 하나 이상 지원 하면 앱 속성 창에이 문이 표시 됩니다. 호환성 위험 요소 섹션에서 **지원 문을**확인 합니다.



## <a name="advanced-insights"></a>고급 정보

데스크톱 분석은 다음과 같은 추가 정보를 사용 하 여 문제를 검색할 수도 있습니다.

### <a name="adopted-version-available"></a>사용 가능한 채택 버전

다른 고객에 게 매우 채택 된 다른 버전의이 앱이 있습니다. 이 신호는 Windows의 준비 된 데이터를 사용 합니다. 현재 버전에 대 한 업그레이드 블 로커가 있는 경우 대신 대체 버전을 배포 하는 것이 좋습니다.

### <a name="driver-dependency"></a>드라이버 종속성

앱은 드라이버에 종속 됩니다. 데스크톱 분석에서는 재발을 검색 하기 위한 파일럿 테스트를 위한 앱을 권장 합니다. 문제가 있는 경우 게시자에 게 문의 하 여 Windows 10과 호환 되는 버전을 요청 하십시오.

### <a name="additional-insights"></a>추가 정보

<!-- 4021225 -->
Configuration Manager 사이트와 클라이언트를 버전 1906으로 업데이트 하면 클라이언트는 다음과 같은 추가 정보를 보고 합니다.

> [!Important]  
> 새 Configuration Manager 기능을 모두 활용하려면 사용자를 업데이트한 후 클라이언트를 최신 버전으로 업데이트합니다. 이 시나리오는 클라이언트 버전이 최신 버전 이기도 해질 때까지 작동 하지 않습니다.

#### <a name="16-bit-apps"></a>16 비트 앱

응용 프로그램에서 16 비트 구성 요소를 모두 제거 하 고를 32 비트 또는 64 비트 동등한 것으로 바꿉니다. 자세한 내용은 windows Vista 및 [windows Server 2008 개발자 사례를 참조 하세요. 응용 프로그램 호환성](https://docs.microsoft.com/previous-versions/aa480152\(v=msdn.10\))Cookbook.

다른 옵션은 Windows 10에서 지원 하기 위해 NT NTVDM (가상 DOS 컴퓨터)를 사용 하도록 설정 하는 것입니다.

#### <a name="requires-admin-privileges"></a>관리자 권한 필요

앱을 사용 하려면 사용자에 게 장치에 대 한 관리자 권한이 있어야 합니다. 관리자 권한이 필요한 앱에 대해 앱 매니페스트를 사용 합니다. 자세한 내용은 [응용 프로그램 매니페스트 만들기 및 포함](https://docs.microsoft.com/previous-versions/bb756929\(v=msdn.10\))을 참조 하세요.

데스크톱 분석에서는 재발을 검색 하기 위한 파일럿 테스트를 위한 앱을 권장 합니다.

#### <a name="java-dependency"></a>Java 종속성

대부분의 Java 응용 프로그램은 개별적으로 설치 된 Java Runtime Environment (JRE)를 사용 합니다. 이전 JRE 버전은 Windows 10에서 계속 작동할 수 있지만 Oracle은 최신 JRE 버전만 지원 합니다. 지원 되지 않는 이전 JRE를 사용 하면 보안 취약점이 발생할 수 있습니다. 최신 JRE 버전에서 응용 프로그램이 실행 되는지 확인 합니다.

#### <a name="not-dpi-aware"></a>DPI 인식 안 함

앱이 Windows 10의 고급 화면 해상도와 관련 하 여 표시 될 수 있습니다. 응용 프로그램 매니페스트를 사용 하 여 높은 DPI 해상도로 인 한 문제를 방지 합니다. 자세한 내용은 [응용 프로그램 매니페스트](https://docs.microsoft.com/windows/desktop/SbsCs/application-manifests)를 참조 하세요.

데스크톱 분석에서는 재발을 검색 하기 위한 파일럿 테스트를 위한 앱을 권장 합니다.

#### <a name="silverlight-framework"></a>Silverlight 프레임 워크

비 브라우저 기반 앱은 Silverlight를 사용 하지 않는 것이 좋습니다. Silverlight 5에 대 한 지원 종료 날짜는 10 월 2021입니다.

최신 웹 브라우저는 Silverlight를 지원 하지 않습니다.

| 브라우저 | Support(지원) |
|---------|---------|
| Google Chrome | 지원 종료: 9 월 2015 |
| Firefox | 지원 종료: 2017년 3월 |
| Microsoft Edge | 플러그 인을 사용할 수 없음 |

데스크톱 분석에서는 재발을 검색 하기 위한 파일럿 테스트를 위한 앱을 권장 합니다.

#### <a name="net-framework-1011"></a>.NET Framework 1.0/1.1

.NET Framework 버전 1.0는 Windows 10에서 지원 되지 않습니다. 버전 1.1는 Windows 10에서 호환 되지 않습니다. 타사 게시자의 앱 인 경우 공급 업체에 문의 하 여 Windows 10과 호환 되는 버전을 요청 합니다. 그렇지 않으면 지원 되는 .NET 버전을 사용 하도록 응용 프로그램을 다시 개발 합니다.

#### <a name="net-framework-2030"></a>.NET Framework 2.0/3.0

.NET 2.0 및 3.5 프레임 워크는 Windows 10에서 지원 됩니다. Windows 기능을 사용 하도록 설정 해야 할 수도 있습니다. 자세한 내용은 [Windows 10에 .NET Framework 3.5 설치](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)를 참조 하세요.

#### <a name="ui-access"></a>UI 액세스

UI 액세스를 사용 하는 응용 프로그램은 사용자 인터페이스 컨트롤 수준을 무시 하 고 바탕 화면에서 더 높은 권한 창에 대 한 입력을 구동 합니다. 사용자 인터페이스 보조 기술 응용 프로그램에만이 설정을 사용 합니다.

앱에서 내게 필요한 옵션 기능을 사용 하지 않는 경우 응용 프로그램 매니페스트의 UI 액세스 플래그를 false로 설정 합니다. 자세한 내용은 [응용 프로그램 매니페스트 만들기 및 포함](https://docs.microsoft.com/previous-versions/bb756929\(v=msdn.10\))을 참조 하세요.

데스크톱 분석에서는 재발을 검색 하기 위한 파일럿 테스트를 위한 앱을 권장 합니다.


## <a name="driver-risk-assessment"></a>드라이버 위험 평가

또한 데스크톱 분석은 OS 버전으로 마이그레이션하지 않는 모든 드라이버를 가용성 별로 나열 하 고 그룹화 합니다.

데스크톱 분석에서 드라이버에 대 한 평가를 찾을 수 있습니다. 배포 계획의 드라이버 자산 목록에서 개별 드라이버를 선택 하 여 해당 속성 플라이 아웃 창을 엽니다. 전체 권장 사항 및 평가 수준이 표시 됩니다. **호환성 위험 요소** 섹션에는 이러한 평가에 대 한 세부 정보가 표시 됩니다.

| 드라이버 가용성 | 작업이 필요 한가요? | 의미 | 지침 |
|---------------------|------------------|---------------|----------|
| 사용할 수 있는 기본 제공 | 아니요, 인식 전용 | 현재 설치 된 응용 프로그램 또는 드라이버 버전은 새 OS 버전으로 마이그레이션하지 않습니다. 새 OS 버전과 호환 되는 버전이 설치 되어 있습니다. | 업그레이드를 계속 하려면 아무 작업도 수행 하지 않아도 됩니다. |
| Windows 업데이트에서 가져오기 | 예 | 현재 설치 된 드라이버 버전은 새 OS 버전으로 마이그레이션하지 않습니다. 호환 되는 버전은 Windows 업데이트에서 사용할 수 있습니다. | 컴퓨터가 Windows 업데이트에서 자동으로 업데이트를 수신 하는 경우에는 아무 조치도 필요 하지 않습니다. 그렇지 않으면 Windows를 업그레이드 한 후 Windows 업데이트에서 새 드라이버를 가져옵니다. |
| Windows 업데이트에서 사용할 수 있습니다. | 예 | 현재 설치 된 드라이버 버전은 새 OS 버전으로 마이그레이션하지 않습니다. 업그레이드 하는 동안 새 드라이버가 설치 되지만 Windows 업데이트에서 최신 버전을 사용할 수 있습니다. | 컴퓨터가 Windows 업데이트에서 자동으로 업데이트를 수신 하는 경우에는 아무 조치도 필요 하지 않습니다. 그렇지 않으면 Windows를 업그레이드 한 후 Windows 업데이트에서 새 드라이버를 가져옵니다. |
| 공급 업체에 문의 | 예 | 드라이버가 새 OS 버전으로 마이그레이션되지 않으며 데스크톱 분석에서 호환 되는 버전을 찾을 수 없습니다. | 솔루션의 경우 드라이버를 제조 하는 IHV (독립 하드웨어 공급 업체) 또는 장치를 제공한 OEM (원본 장비 제조업체)으로 확인 합니다. |


## <a name="see-also"></a>참고자료

Windows 10 용 FastTrack 센터 혜택은 **데스크톱 앱**에 대 한 액세스를 제공 합니다. 이 혜택은 Windows 10 및 Office 365 ProPlus 앱 호환성 문제를 해결 하기 위해 설계 된 새로운 서비스입니다. 자세한 내용은 [데스크톱 앱](https://docs.microsoft.com/fasttrack/win-10-desktop-app-assure)확인을 참조 하세요.
