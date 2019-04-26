---
title: 앱 상태 분석기
titleSuffix: Configuration Manager
description: 데스크톱 Analytics에서 앱 상태 분석기를 사용 하 여 호환성 평가 위한 방법 가이드입니다.
ms.date: 04/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2af150a4-0c18-4b40-8492-c04c5d154596
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: d982094a427f1f67992584e3262493d3f4a96766
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206560"
---
# <a name="how-to-assess-compatibility-with-app-health-analyzer"></a>앱 상태 분석기를 사용 하 여 호환성을 평가 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석을 위해 앱 상태 분석기 도구 키트를 사용 하 여 데스크톱 응용 프로그램 호환성 문제에 대해 평가 합니다. 기간 업무 앱을 포함 하 여 데스크톱 앱에 대 한 유효성 검사 노력을 집중할 수 있습니다. 도구에는 가능한 수정 작업과 함께 위험 등급을 제공합니다. 또한 앱 준비 보고서를 사용 하 여 Windows 10 업그레이드에 대 한 앱 준비 상태 평가를 포함 합니다.



## <a name="download"></a>다운로드

다운로드 링크를 표시 하려면 Microsoft 담당자에 게 문의 합니다. 항상 최신 버전을 사용 합니다.

다운로드에 Windows Installer (MSI) 파일입니다. 사용자의 컴퓨터에 앱 상태 분석기 도구 키트를 설치 합니다. 도구 키트를 실행 하면 마법사 앱 준비 보고서를 만드는 과정을 단계별로 안내 합니다.

샘플 스크립트를 포함 하는 도구 키트입니다. 조직 전체에서 장치의 준비 상태 정보의 컬렉션을 자동화 하는 경우 이러한 스크립트를 배포 하려면 Configuration Manager를 사용 합니다. 자세한 내용은 [Automation](#automation)합니다.



## <a name="how-it-works"></a>작동 방식

도구는 장치에 이미 설치 된 응용 프로그램의 정적 분석을 수행 합니다. 작동 하지 분석 앱 설치 관리자를 패키지 합니다. 사용자는 앱을 실행할 필요가 없습니다. 도구는 Windows 장치에서 등록 하는 모든 설치 된 응용 프로그램을 평가 합니다.

앱 상태 분석기 적극적으로 관리 하지 않는 레거시 앱에 대 한 설치 관리자를 유지 하는 것을 요구 하지 않습니다. 설치 된 상태로 앱을 사용 하 여 호환성 문제를 식별합니다. 모든 앱은 미리 정의 된 호환성 규칙에 대 한 평가 됩니다. 이러한 신호는 고객은 Windows 10으로 업그레이드 하는 경우 Microsoft에 보고 하는 일반적인 널리 알려진 문제입니다. 호환성 정보를 가능한 수정 작업 또는 수정에도 포함 됩니다. 문제를 사용 하 여 앱에 있는 경우 제안 된 작업을 시작 합니다.

> [!Important]  
> 도구 키트를 복구 하거나 앱을 수정 하는 기능을 지원 하지 않습니다. 앱 준비 보고서를 만든 경우 insights 및 Windows 10으로 업그레이드 하기 전에 앱을 수정 하는 데 대 한 지침 제공 합니다.  



## <a name="prerequisites"></a>필수 구성 요소

을 설치 하 고 도구 키트를 사용 하 여 이전 장치는 다음 요구 사항을 충족 하는지 확인 합니다.  

- Windows 7 서비스 팩 1 이상  

- 장치에 대 한 관리자 권한이  

- Microsoft.NET Framework 4.5.1 이상  

- 다음 요구 사항을 포함 하는 데스크톱 Analytics 서비스에 등록 합니다.  

    - 최신 업데이트입니다. 자세한 내용은 [장치 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)합니다.  

    - 진단 데이터 수준입니다. 자세한 내용은 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)합니다.  



## <a name="analyze"></a>분석

1. 대상 장치에 앱 상태 분석기를 설치 합니다. 기본적으로 다음 경로에 설치합니다. `C:\Program Files\Microsoft Corporation\Microsoft App Health Analyzer`  

2. Windows로 이동 **시작** 메뉴에서 확장을 **Microsoft 앱 상태 분석기** , 그룹 및 개방형를 **앱 상태 분석기** 관리자 권한으로 합니다. 보고서를 생성 하는 데 몇 분 정도 걸릴 수 있습니다.  

    > [!Note]  
    > 진단 데이터를 필요한 설정 중 필요한 설정을 구성 되지 않은 경우 오류가 표시 됩니다. 필수 구성 요소 설정을 적절 하 게 구성 했는지 확인 합니다. 자세한 내용은 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)합니다.  

3. 앱 준비 보고서를 열 때 응용 프로그램 평가 시작 합니다. 도구 키트를를 완료 하려면 시간이 오래 걸릴 수 있음에 대 한 대기 장치의 응용 프로그램의 수에 따라 합니다.  

![앱 상태 분석기의 앱 준비 보고서 스크린샷](media/app-readiness-report-evaluating.png)

창을 최소화 하 고 도구 키트를 백그라운드에서 실행 되는 동안 다른 작업을 진행할 수 있습니다.


### <a name="app-readiness-report-features"></a>앱 준비 보고서 기능

#### <a name="get-started"></a>시작

이 탭이 현재 버전에서 지원 되는 신호에 대 한 개요를 제공합니다. 또한 가능한 수정 작업을 포함합니다.

#### <a name="insights"></a>Insights

이 탭에는 도구를 평가 하는 모든 앱의 뷰를 제공 합니다. 위험 평가 및 호환성 문제를 식별 하는 데 사용 된 다양 한 신호 보여 줍니다.

- **신호** 메뉴: 신호 왼쪽의 메뉴를 사용 하 여 이러한 앱을 필터링 합니다.  

- **CSV 내보내기**: 이러한 정보를 쉼표로 구분 된 값 (CSV) 파일로 내보내려면  

- **응용 프로그램을 다시 검사**: 새 응용 프로그램을 설치 하는 경우이 옵션을 사용 하 여 도구를 다시 실행 하려면  

- **ID 문제 해결**: 장치에 설치 된 앱에 보고서의 정보를 표시 하지만 지원 하기 위해이 ID가 제공  

#### <a name="desktop-analytics"></a>Desktop Analytics

이 탭에 앱 상태 분석기를 사용 하 여 조직 전체에서 앱에 대 한 준비 정보를 제공 하는 방법을 간략하게를 설명 합니다.



## <a name="automation"></a>자동화

다양 한 장치에서 앱 정보를 가져오려는 앱 상태 분석기 명령줄 버전 Configuration Manager를 배포 합니다. 소수의 조직 내의 대표 장치에 배포 합니다. 예를 들어, 데스크톱 분석을 사용 하 여 *파일럿* 컬렉션입니다. 동일 [필수 구성 요소](#prerequisites) 이러한 장치에 적용 합니다.

광범위 한 배포를 수행 하기 전에 먼저 성공적인 실행을 확인 합니다. 데이터 분석 데스크톱에에서 표시 되 고 있는지 확인 합니다.

샘플 스크립트를 포함 하는 앱 상태 분석기 도구 키트 run_silent.cmd 합니다. 이 스크립트는 기본적으로 다음 경로에: `C:\Program Files\Microsoft Corporation\Microsoft App Health Analyzer`합니다. 이 스크립트를 사용 하 여 Configuration Manager를 사용 하 여 프로세스를 자동화 합니다.


### <a name="tips"></a>팁

- 대상 OS로 업그레이드 하기 전에 파일럿의 모든 장치에 앱 상태 분석기를 배포 합니다. 효과적인 준비 정보를 가져오려면 적어도 한 번 실행 파일럿 그룹 배포 계획에 대 한 합니다.  

- 데스크톱 분석 파일럿 그룹, 배포 계획에 대 한 권장 하는 기본 제공 기능이 있습니다. 중요 한 앱에서 전체 검사를 가져오려는 모든 파일럿 장치의 도구 키트를 실행 합니다.  

- 도구를 사용자에서 서명 되지 않은 경우 또는 장치를 사용 하지 않는 경우 실행을 예약 합니다.  

- 되풀이 일정을 구성 합니다. 예를 들어 30 일 마다 실행 합니다. 이 일정 수 있도록 최신 장치에서 최신 준비 정보를 가져옵니다.  



## <a name="desktop-analytics-integration"></a>데스크톱 Analytics 통합

데스크톱 분석의 다음 스크린샷은 버전 1.15.25 ContosoApp 세부 정보를 표시 합니다.

- 에 **중간** 위험 평가  
- 채택 된 버전이 사용 가능  
- 드라이버 종속성이 있습니다.  

![앱의 호환성 위험 요소를 보여 주는 데스크톱 분석](media/aha-desktop-analytics-compat-risk-factors.png)



## <a name="troubleshooting"></a>문제 해결

이 섹션에서는 문제 해결 단계와 앱 상태 분석기를 사용 하 여 표시 될 수 있습니다 하는 가장 일반적인 운영 문제를 다룹니다. 예:

- 앱 상태 분석기에서 시작 화면에 표시 되지 않으면  

- 앱이 장치에 설치 되어 있지만 앱 준비 상태 보고서에 대 한 정보를 표시 하지 않습니다.  

- 도구를 실행할 때 아무 작업도  

### <a name="diagnostic-data-settings"></a>진단 데이터 설정

Windows 진단 데이터 설정에 대 한 구성을 다시 확인 합니다. Configuration Manager는 이러한 설정 해야 경우 데스크톱 Analytics에 장치 등록 합니다. 해결 방법으로 스크립트 또는 그룹 정책과 같은 다른 메서드를 사용할 수 있습니다. 자세한 내용은 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)합니다.  

### <a name="verbose-mode"></a>자세한 정보 표시 모드

Run_verbose.cmd 스크립트를 사용 하 여 자세한 정보 표시 모드에서 도구를 실행 합니다. 기본적으로 스크립트는 다음 경로에서: `C:\Program Files\Microsoft Corporation\Microsoft App Health Analyzer\run_verbose.cmd`

자세한 정보 표시 모드는 잠재적인 문제를 해결할 수 있는 추가 로그를 생성 합니다. 로그를 저장 합니다 `LogCollection` 폴더에 설치 된 위치입니다. 예를 들어, 기본 로그 컬렉션 경로: `C:\Program Files\Microsoft Corporation\Microsoft App Health Analyzer\LogCollection\`


## <a name="see-also"></a>참고 항목

에 대 한 액세스를 제공 하는 Windows 10에 대 한 FastTrack 센터 혜택 **데스크톱 앱 보장**합니다. 이 혜택에는 Windows 10 및 Office 365 ProPlus 응용 프로그램 호환성 문제를 해결 하기 위해 새로운 서비스입니다. 자세한 내용은 [데스크톱 앱 보장](https://docs.microsoft.com/fasttrack/win-10-desktop-app-assure)합니다.
