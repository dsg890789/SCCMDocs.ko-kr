---
title: Windows 앱에 대한 호환성 위험
titleSuffix: Configuration Manager
description: 데스크톱 Analytics에서 Windows 앱에 대 한 호환성 위험에 알아봅니다.
ms.date: 04/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ea78f726-b1b3-49b0-8141-d916be48c458
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: da0bde04e019fdf0fbb0a997be652860824270b1
ms.sourcegitcommit: 5ee9487c891c37916294bd34a10d04e398f111f7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59069401"
---
# <a name="compatibility-risk-for-windows-apps-in-desktop-analytics"></a>데스크톱 Analytics에서 Windows 앱에 대 한 호환성 위험

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

Windows Analytics에서 업그레이드 평가 된 일반, 예를 들어: 주의가 필요한 또는 수정을 사용할 수 있습니다. 모든 시각적 표시기 문제를 사용 하 여 앱을 우선 순위를 지정 하거나 insights를 업그레이드 하는 방법은 제공 하지 않습니다. 사용 하 여이 기능을 대체 하는 데스크톱 분석 **호환성 위험**합니다. 데스크톱 Analytics 업그레이드 전 시나리오에 대 한 배포 보기에만 앱에 대 한 앱 위험 평가 보여 줍니다. 현재 배포 계획에 포함 된 컴퓨터에서 Microsoft 가져옵니다 정보에 따라 앱을 분류 합니다.

데스크톱 분석에는 다음 호환성 위험 범주를 사용 합니다.

- **낮음**: 서비스를 찾을 수 없는 신호는 Windows에 대 한이 응용 프로그램 위험에 처를 업그레이드 합니다. 대상 OS로 작업할 가능성이-됩니다.  

- **중간**: 수정 가능성이 높은 수는 있지만 분석 응용 프로그램 수 기능을 장애가 있는 나타냅니다.  

- **높은**: 응용 프로그램은 거의 확실히 중 또는 업그레이드 후에 실패 합니다. 이 수정을 해야 합니다.  

- **알 수 없음**: 앱은 앱 상태 분석기에 의해 평가 되지 않았습니다. 와 같은 다른 정보는 *MS 알려진 문제* 하거나 *준비에 대 한 Windows*합니다.  



## <a name="risk-assessment-engine"></a>위험 평가 엔진

위험 등급을 생성 하 여 앱 상태 분석기를 사용 하는 여러 원본 있습니다.

![앱 상태 분석기 위험 평가 엔진 영역의 다이어그램](media/aha-risk-assessment-engine.png)


### <a name="ms-known-issues"></a>MS 알려진 문제

앱 상태 분석기 알려진된 문제에 대 한 Microsoft 응용 프로그램 호환성 데이터베이스에 살펴봅니다. 이 데이터베이스를 사용 하 여 Microsoft에서 공개적으로 사용 가능한 응용 프로그램에 대 한 모든 기존 호환성 블록 또는 다른 게시자를 확인 합니다. 이 검사는 선택 하면 배포 계획에 대 한 대상 OS에만 적용 됩니다.


### <a name="ready-for-windows"></a>Windows에 대 한 준비

Windows에 대 한 준비 데이터 저장소 장치에서 호환성 블록에 대 한 확인합니다. 또한 유사한 앱을 보고 다른 고객의에서 데이터를 상호 연결 합니다. Microsoft이 앱이 없는 문제를 보고 하는 위치와 유사한 다른 장치에서 데이터를 사용 합니다.


### <a name="app-health-analyzer-signals-for-compatibility-assessment"></a>호환성 평가 대 한 앱 상태 분석기 신호

응용 프로그램 호환성에 대 한 추가 신호를 수집 하려면 앱 상태 분석기 도구 키트를 사용 합니다. 자세한 내용은 [앱 상태 분석기](/sccm/desktop-analytics/app-health-analyzer)합니다.

다음 신호 현재 사용할 수 있습니다.

#### <a name="adopted-version-available"></a>사용 가능한 채택된 버전

다른 고객이 많이 채택 되는이 앱의 다른 버전이 있습니다. 이 신호는 Windows에 대 한 준비에서 데이터를 사용합니다. 현재 버전을 사용 하 여 모든 업그레이드 블 로커 인 경우에 대신 대체 버전을 배포 하는 것이 좋습니다.

#### <a name="16-bit"></a>16 비트

응용 프로그램에서 모든 16 비트 구성 요소를 제거 하 고 32 비트 또는 64 비트 해당 항목을 바꿉니다. 자세한 내용은 참조 하세요. [The Windows Vista 및 Windows Server 2008 개발자를 위한 정보: 응용 프로그램 호환성 설명서](https://msdn.microsoft.com/library/aa480152.aspx)합니다.

Windows 10에서 지원에 대 한 NT Virtual DOS Machine NTVDM ()를 사용 하도록 설정 하려면 다른 옵션이입니다.

#### <a name="requires-admin-privileges"></a>관리자 권한 필요

앱 사용자에 게 장치에 대 한 관리 액세스에 필요 합니다. 관리자 권한이 필요한 이러한 앱에 대 한 응용 프로그램 매니페스트를 사용 합니다. 자세한 내용은 [만들기 응용 프로그램 매니페스트를 포함 하 고](https://msdn.microsoft.com/library/bb756929.aspx)입니다.
<!--Is this a better, more current link? https://docs.microsoft.com/windows/desktop/sbscs/application-manifests-->

데스크톱 분석 파일럿 테스트를 위해 앱을 권장합니다. 파일럿에 대 한 제대로 작동 해야 하지만 회귀를 찾을 수 있습니다.

#### <a name="java-dependency"></a>Java 종속성

대부분의 Java 응용 프로그램에는 별도로 설치 된 Java Runtime Environment (JRE)를 사용합니다. Oracle는 JRE 버전 이전 Windows 10에서 작업을 계속할 수, 최신 JRE 버전만 지원 합니다. 이전에 지원 되지 않는 JRE를 사용 하 여 보안 취약점으로 인 한 있을 수 있습니다. 응용 프로그램 최신 JRE 버전에서 실행 되는지 확인 합니다.

#### <a name="not-dpi-aware"></a>Not DPI 인식

앱을 Windows 10에서 고급 화면 해상도 사용 하 여 표시 문제가 있을 수 있습니다. 높은 DPI 해상도 사용 하 여 문제를 방지 하려면 응용 프로그램 매니페스트를 사용 합니다. 자세한 내용은 [응용 프로그램 매니페스트](https://docs.microsoft.com/windows/desktop/SbsCs/application-manifests)합니다.

데스크톱 분석 파일럿 테스트를 위해 앱을 권장합니다. 파일럿에 대 한 제대로 작동 해야 하지만 회귀를 찾을 수 있습니다.

#### <a name="visual-basic-version-6-vb6"></a>Visual Basic 버전 6 (VB6)

데스크톱 분석 파일럿 테스트를 위해 앱을 권장합니다. VB6 응용 프로그램 호환 많습니다. 앱 regresses 파일럿 기간 동안 위젯을 나 추가 종속성으로 인해 다음 Visual Basic.net 앱을 업데이트 해야 하는 경우

#### <a name="os-version-dependency"></a>OS 버전 종속성

버전 도우미 API를 사용 하 여 응용 프로그램을 개발 하는 것이 좋습니다. 또는 Windows 10을 대상 응용 프로그램 매니페스트 합니다.

데스크톱 분석 파일럿 테스트를 위해 앱을 권장합니다. 파일럿에 대 한 제대로 작동 해야 하지만 회귀를 찾을 수 있습니다.

#### <a name="silverlight-framework"></a>Silverlight 프레임 워크

비 브라우저 기반 앱이 Silverlight를 사용 하지 않는 것이 좋습니다. Silverlight 5에 대 한 지원 종료 날짜 이며 2021 년 10 월

최신 웹 브라우저는 Silverlight를 지원 하지 않습니다.

| 브라우저 | Support(지원) |
|---------|---------|
| Google Chrome | 지원 종료: 2015 년 9 월 |
| Firefox | 지원 종료: 2017년 3월 |
| Microsoft Edge | 사용 가능한 플러그 인 |

데스크톱 분석 파일럿 테스트를 위해 앱을 권장합니다. 파일럿에 대 한 제대로 작동 해야 하지만 회귀를 찾을 수 있습니다.

#### <a name="net-framework-1011"></a>.NET framework 1.0/1.1

.NET framework 버전 1.0은 Windows 10에서 지원 되지 않습니다. 버전 1.1는 Windows 10에서 호환 되지 않습니다. 제 3 자 게시자의 앱 인 경우 Windows 10과 호환 되는 버전을 요청 하려면 공급 업체에 문의 합니다. 지원 되는.NET 버전을 사용 하 여 응용 프로그램 많지만 그렇지 않은 경우.

#### <a name="net-framework-2030"></a>.NET framework 2.0/3.0

.NET 2.0 및 3.5 프레임 워크는 Windows 10에서 지원 됩니다. Windows 기능을 사용 하도록 설정 해야 합니다. 자세한 내용은 [Windows 10에.NET Framework 3.5 설치](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)합니다.

#### <a name="ui-access"></a>UI 액세스

응용 프로그램 UI 액세스를 사용 하 여 사용자 인터페이스 컨트롤 수준 높은 입력된 권한 windows 바탕 화면에서 드라이브를 무시할 수 있습니다. 만이 설정을 사용 하 여 사용자 인터페이스에 대 한 보조 기술 응용 프로그램에 대 한 합니다.

앱에서 내게 필요한 옵션 기능을 사용 하지 않는 경우 false로 응용 프로그램 매니페스트에서 UI 액세스 플래그를 설정 합니다. 자세한 내용은 [만들기 응용 프로그램 매니페스트를 포함 하 고](https://msdn.microsoft.com/library/bb756929.aspx)입니다.

#### <a name="driver-dependency"></a>드라이버 종속성

앱은 드라이버에 따라 달라 집니다. 데스크톱 분석 파일럿 테스트를 위해 앱을 권장합니다. 파일럿에 대 한 제대로 작동 해야 하지만 회귀를 찾을 수 있습니다. 를 문제가 있는 경우에 Windows 10과 호환 되는 버전을 요청 하려면 게시자에 게 문의 합니다.



## <a name="app-confidence-simulation-for-a-sample-population"></a>샘플 모집단에 대 한 앱 신뢰 시뮬레이션

다음 차트는 샘플 사례 연구에서입니다. 이 데이터의 데이터 기반 접근 방식을 응용 유효성을 검사 하는 데 데스크톱 Analytics를 사용 하 여 앱 상태 분석기 사용을 강조 표시 합니다. 이 방식은 시간 및 Windows 10 업그레이드 하는 동안 응용 프로그램을 테스트 노력을 줄일 것이 도움이 됩니다.

이 데이터에는 기간 업무 앱을 비롯 한 899 응용 프로그램을 사용 하 여 60 장치에 대 한 정확도 메트릭을 보여 줍니다.

![이전 및 이후 앱 신뢰를 보여 주는 차트](media/aha-app-confidence-simulation.png)


## <a name="see-also"></a>참고 항목

에 대 한 액세스를 제공 하는 Windows 10에 대 한 FastTrack 센터 혜택 **데스크톱 앱 보장**합니다. 이 혜택에는 Windows 10 및 Office 365 ProPlus 응용 프로그램 호환성 문제를 해결 하기 위해 새로운 서비스입니다. 자세한 내용은 [데스크톱 앱 보장](https://docs.microsoft.com/fasttrack/win-10-desktop-app-assure)합니다.
