---
title: 사용자 경험 분석 미리 보기
titleSuffix: Configuration Manager
description: 사용자 경험 분석 미리 보기에 대한 지침입니다.
ms.date: 01/29/2020
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 00537b90-f6d2-45e9-a9a1-6b3ada466a16
author: mestew
ms.author: mstewart
manager: dougeby
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: b8231ba0b97b9c4f87d35ab753e01644b254df94
ms.sourcegitcommit: 4d49103722654f12ffe8df4d5848def44b7e1eb3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76891666"
---
# <a name="bkmk_uea"></a> 사용자 경험 분석 비공개 미리 보기

> [!Note]  
> 이 정보는 정식으로 출시되기 전에 대폭 수정될 수 있는 미리 보기 기능과 관련이 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

## <a name="user-experience-analytics-overview"></a>사용자 경험 분석 개요

최종 사용자가 긴 부팅 시간 또는 기타 장애를 경험하는 것은 드문 일이 아닙니다. 이러한 장애는 다음과 같은 요인으로 발생할 수 있습니다.

- 레거시 하드웨어
- 최종 사용자 환경에 최적화되지 않은 소프트웨어 구성
- 구성 변경 및 업데이트로 인한 문제

이러한 문제 및 기타 최종 사용자 환경 문제는 IT가 최종 사용자 환경에 대한 가시성을 충분히 확보하지 못하기 때문에 지속됩니다. 일반적으로 이러한 문제에 대한 가시성은 대개 최적화해야 할 사항에 대한 명확한 정보를 제공하지 않는 느리고 비용이 많이 드는 지원 채널에서만 제공합니다. 이러한 문제로 인한 비용은 IT 지원만 부담하는 것은 아닙니다. 정보 작업자가 문제를 처리하는 데 소비하는 시간 역시 많은 비용을 초래합니다. 사용자 생산성을 낮추는 성능, 안정성 및 지원 문제는 조직의 수익성에도 큰 영향을 미칠 수 있습니다.

**사용자 경험 분석**은 사용자 환경에 대한 인사이트를 제공하여 사용자의 생산성을 개선하고 IT 지원 비용을 절감하는 데 그 목적이 있습니다. IT는 이 인사이트를 통해 구성 변경의 사용자 영향을 평가하여 사전 지원으로 최종 사용자 환경을 최적화하고 사용자 환경에서 재발을 검색할 수 있습니다.

이 초기 릴리스는 다음 세 가지에 중점을 두고 있습니다.

- [**권장 소프트웨어**](#bkmk_uea_rs): 최상의 사용자 환경을 제공하기 위한 권장 사항
- [**사전 예방적 수정 스크립팅**](#bkmk_uea_prs): 최종 사용자가 문제를 인식하기 전에 일반적인 지원 문제를 해결
- [**시작 성능**](#bkmk_uea_bp): 사용자가 전원을 켜는 순간부터 긴 부팅 시간과 로그인 지연 없이 신속하게 생산성을 확보하도록 지원하는 데 활용

이 릴리스는 시작일 뿐입니다. 초기 릴리스 후 바로 다른 주요 사용자 환경에 대한 새로운 인사이트를 신속하게 롤아웃할 예정입니다.

## <a name="bkmk_uea_prereq"></a> 시작하기

사용자 경험 분석을 사용하기 시작하려면 필수 구성 요소를 확인하고 데이터 수집을 시작합니다. 

### <a name="prerequisites"></a>전제 조건

현재 미리 보기에는 다음이 필요합니다.
- Windows 10을 실행하는 Intune 등록 디바이스
- 시작 성능 인사이트는 Windows 10 버전 1903 이상을 실행하는 디바이스에서만 사용할 수 있습니다.

이전 버전의 Windows 10을 실행하는 Configuration Manager 디바이스 및 Intune 등록 디바이스는 현재 이 미리 보기에서 지원되지 않습니다.

### <a name="start-gathering-data"></a>데이터 수집 시작

1. `https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Enrollment/UXAnalyticsMenu` 로 이동
1. **시작**을 클릭합니다. Intune 등록 디바이스로부터 시작 성능 데이터를 채우는 데 최대 24시간이 걸릴 수 있습니다.

## <a name="overview-page"></a>개요 페이지

데이터가 준비되면 **개요** 페이지에서 아래에 자세히 설명된 정보를 확인할 수 있습니다.

- **사용자 환경 점수**는 **권장 소프트웨어** 및 **시작 성능** 점수의 50/50 가중 평균입니다. 향후 계속해서 하위 점수 집합을 확장할 예정입니다.

- 기준을 설정하여 현재 점수를 다른 점수와 비교할 수 있습니다.
  - [기준](#bkmk_uea_baselines) 섹션에 설명된 대로 일반적인 엔터프라이즈와 비교할 수 있는 *상업용 중앙값* 기준이 기본 제공됩니다. 현재 메트릭에 따라 새 기준을 만들어 시간 경과에 따라 진전을 추적하거나 재발을 확인할 수 있습니다.
   - 기준 마커는 전체 점수 및 하위 점수에 대해 표시됩니다. 선택한 기준에서 구성 가능한 임계값을 초과하여 재발한 점수가 있는 경우 해당 점수는 빨간색으로 표시되고 최상위 점수는 주의가 필요한 것으로 플래그가 지정됩니다.
  - **데이터 부족** 상태는 의미 있는 점수를 제공하기에 충분한 보고 디바이스가 없음을 의미합니다. 현재 5개 이상의 디바이스가 필요합니다.

- **필터**를 사용하여 디바이스 또는 사용자의 하위 집합에 대한 점수를 볼 수 있습니다. 단, 이 미리 보기에서는 필터 기능을 사용할 수 없습니다.

- **인사이트 및 권장 사항**은 점수를 향상하기 위해 우선 순위가 지정된 목록입니다. **모범 사례** 또는 **권장 소프트웨어**로 이동하면 이 목록이 하위 노드의 컨텍스트로 필터링됩니다.

[![사용자 경험 분석 개요 페이지](media/uea-overview-page.png)](media/uea-overview-page.png#lightbox)

## <a name="bkmk_uea_rs"></a> 권장 소프트웨어

특정 소프트웨어는 하위 수준 상태 메트릭에 관계없이 최종 사용자 환경을 개선하는 것으로 알려져 있습니다. 예를 들어 Windows 10은 Windows 7보다 Net Promoter 점수가 훨씬 높습니다. **소프트웨어 도입** 점수는 다양한 권장 소프트웨어가 배포된 디바이스 비율의 가중 평균을 나타내는 0~100 사이의 숫자입니다. 사용자가 더 자주 상호 작용하므로 현재 가중치는 Office 365 및 Windows가 다른 메트릭에 비해 더 높습니다. 메트릭에 대한 설명은 다음과 같습니다. 

[![사용자 경험 분석 권장 소프트웨어 페이지](media/uea-recommended-software.png)](media/uea-recommended-software.png#lightbox)

### <a name="bkmk_uea_win10"></a> Windows 10

Windows 10은 이전 버전의 Windows보다 더 나은 사용자 환경을 제공합니다. 이 메트릭은 Windows 10 및 이전 버전의 Windows를 실행하는 디바이스의 비율을 측정합니다.

이전 버전의 Windows에서 디바이스를 이동하기 위한 권장 수정 작업은 [Desktop Analytics](/sccm/desktop-analytics/overview)를 사용하여 배포 계획을 만드는 것입니다.

### <a name="bkmk_uea_opp"></a> Office 365

Office 365는 이전 버전의 Office와 비교하여 더 나은 사용자 환경을 제공하고 공동 작업을 개선합니다. 이 메트릭은 Office 365 및 이전 버전이 설치된 디바이스의 비율을 측정합니다.

이전 버전의 Office에서 Office 365로 디바이스를 이동하기 위한 권장 수정 작업은 [Microsoft Intune](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Deploying-Office-365-ProPlus-with-Microsoft-Intune/ba-p/250292) 또는 [Configuration Manager](https://docs.microsoft.com/deployoffice/deploy-office-365-proplus-with-configuration-manager)를 사용하여 업그레이드하는 것입니다.

### <a name="bkmk_uea_ap"></a> Autopilot

Autopilot은 사용자가 엔터프라이즈 관리를 위해 새 디바이스를 등록하는 데 유용한 환경을 제공합니다. 이 메트릭은 Autopilot에 등록된 디바이스의 비율을 측정합니다.

권장되는 수정 작업은 [Microsoft Intune](https://docs.microsoft.com/intune/enrollment-autopilot)을 사용하여 Autopilot에 기존 디바이스를 등록하는 것입니다. Autopilot은 다음에 대해 뛰어난 사용자 환경을 제공합니다.
- 장치를 재설정하는 경우 다시 프로비전.
- 새 디바이스에 대한 초기 프로비전 환경은 Autopilot에 미리 등록되어 있습니다.

### <a name="bkmk_uea_aad"></a> Azure Active Directory

Azure Active Directory(Azure AD)는 사용자에게 필요한 앱 및 서비스에 대한 Single Sign-On을 제공합니다. 이 메트릭은 Azure AD에 등록된 디바이스의 비율을 측정합니다.

Microsoft Intune 관리 디바이스는 Azure AD에 이미 등록되어 있습니다. Configuration Manager에서 관리하는 디바이스에 대해 권장되는 수정 작업은 [Azure AD에 디바이스를 등록](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains)하거나 [디바이스를 공동 관리](/sccm/comanage/overview)하는 것입니다. 디바이스를 공동 관리하면 클라우드 관리 점수도 향상됩니다.

### <a name="bkmk_uea_intune"></a> 클라우드 관리

Microsoft Intune을 사용하면 그룹 정책의 성능 오버헤드가 발생하지 않으므로 최종 사용자 환경이 향상됩니다. 이 메트릭은 Microsoft Intune에 등록된 PC 비율을 측정합니다.

Configuration Manager에서 관리하지만 아직 Intune에 등록되지 않은 디바이스에 대한 권장 수정 작업은 [디바이스를 공동 관리](/sccm/comanage/overview)하는 것입니다.

### <a name="bkmk_uea_np"></a> 상업용 중앙값 없음

기본 제공되는 **상업용 중앙값** 기준은 현재 위의 섹션에 나열된 하위 점수에 대한 메트릭이 없습니다.

## <a name="bkmk_uea_bp"></a> 시작 성능

IT는 시작 성능 점수를 활용하여 사용자가 전원을 켜는 순간부터 긴 부팅 시간과 로그인 지연 없이 신속하게 생산성을 확보하도록 지원할 수 있습니다. **시작 점수**는 0~100 사이의 숫자입니다. 이 점수는 **부팅 점수** 및 **로그인** 점수의 가중 평균으로, 다음과 같이 계산됩니다.

- **부팅 점수**: 전원 켜기부터 로그인까지 걸린 시간을 기준으로 합니다. 업데이트 단계를 제외하고 각 디바이스에서 마지막 부팅 시간을 확인하여 0(나쁨)부터 100(예외)까지 점수를 매깁니다. 이들 점수를 평균하여 전체 테넌트 부팅 점수를 제공합니다.
- **로그인 점수**: 사용자가 자격 증명을 입력한 후 바탕 화면에 액세스할 수 있을 때까지 걸린 시간을 기준으로 합니다. 최초 로그인 또는 기능 업데이트 직후 로그인을 제외하고 각 디바이스에 대한 마지막 로그인 시간을 확인하여 0(나쁨)에서 100(예외)까지 점수를 매깁니다. 이들 점수를 평균하여 전체 테넌트 부팅 점수를 제공합니다.

[![사용자 경험 분석 시작 성능 페이지](media/uea-startup-performance.png)](media/uea-startup-performance.png#lightbox)

**시작 성능** 페이지에는 다음 섹션에 설명된 **인사이트 및 권장 사항**의 우선 순위가 지정된 목록도 제공됩니다.

### <a name="bkmk_uea_hdd"></a> 하드 디스크 드라이브

시작 성능은 부팅 드라이브가 하드 디스크에 있는 디바이스 수에 대한 인사이트를 제공합니다. 하드 디스크 드라이브는 부팅 시간이 일반적으로 반도체 드라이브보다 3~4배 더 깁니다. 또한 반도체 드라이브로 이동할 경우 예상되는 시작 성능 향상도 보고됩니다.

클릭하면 하드 디스크 드라이브를 사용하는 디바이스 목록이 표시됩니다. 권장 작업은 이러한 디바이스를 반도체 드라이브로 업그레이드하는 것입니다.

### <a name="bkmk_uea_gp"></a> 그룹 정책

시작 성능은 그룹 정책으로 인해 부팅 및 로그인 시간이 지연되는 디바이스 수에 대한 인사이트를 제공합니다. 클릭하면 디바이스 보기로 이동합니다. 보기는 그룹 정책 시간을 기준으로 정렬되므로 추가 문제 해결을 위해 영향을 받는 디바이스를 확인할 수 있습니다.

특정 디바이스를 클릭하면 부팅 및 로그인 기록을 볼 수 있습니다. 이 기록은 문제의 재발 여부와 문제가 발생한 시점을 확인하는 데 도움이 됩니다.

그룹 정책 성능을 최적화하는 방법에 대한 많은 문서가 있지만, 대신 클라우드 관리로 마이그레이션하도록 선택할 수 있습니다. 클라우드 관리로 마이그레이션하면 [Intune 보안 기준](https://docs.microsoft.com/intune/protect/security-baselines)과 곧 출시 예정인 정책 분석 도구를 사용할 수 있습니다.

### <a name="bkmk_uea_sb"></a> 느린 부팅 및 로그인 시간

시작 성능은 부팅 및 로그인 시간이 느린 디바이스 수에 대한 인사이트를 제공합니다. 부팅 점수 또는 로그인 점수가 "0"이면 속도가 느리다는 의미입니다. 클릭하면 디바이스 보기로 이동합니다. 디바이스는 각각 코어 부팅 시간 또는 코어 로그인 시간을 기준으로 정렬되므로 추가 문제 해결을 위해 영향을 받는 디바이스를 확인할 수 있습니다.

특정 디바이스를 클릭하면 부팅 및 로그인 기록을 볼 수 있습니다. 이 기록은 문제의 재발 여부와 문제가 발생한 시점을 확인하는 데 도움이 됩니다.

### <a name="more-startup-performance-insights-are-on-the-way"></a>더 많은 시작 성능 인사이트를 준비 중

이후 미리 보기에서 제공하기 위해 더 많은 시작 성능 인사이트를 개발 중입니다.

## <a name="bkmk_uea_prs"></a> 사전 예방적 수정

사전 예방적 수정은 사용자가 문제를 인식하기도 전에 디바이스에서 일반적인 지원 문제를 검색하고 수정할 수 있는 스크립트 패키지입니다. 이러한 수정을 통해 지원 호출을 줄일 수 있습니다. 사용자 자체 스크립트 패키지를 만들거나 Microsoft 환경에서 지원 티켓을 줄이기 위해 작성 및 사용하는 스크립트 중 하나를 배포할 수 있습니다.

각 스크립트 패키지는 검색 스크립트, 수정 스크립트 및 메타데이터로 구성됩니다. Intune을 통해 이러한 스크립트 패키지를 배포하고 해당 효율성에 대한 보고서를 볼 수 있습니다. Microsoft에서는 새 스크립트를 적극적으로 개발하고 있으며 이러한 스크립트를 사용하여 사용자 환경을 파악하고자 합니다. 스크립트 패키지에 대한 의견이 있는 경우 사용자 경험 분석 미리 보기 담당자에게 연락하세요.

### <a name="bkmk_uea_prs_ps1"></a> 검색 및 수정 스크립트 가져오기

1. [PowerShell 스크립트](#bkmk_uea_ps_scripts) 섹션에서 이 문서의 맨 아래에 있는 스크립트를 복사합니다.
    - 이름이 `det`로 시작하는 스크립트 파일은 검색 스크립트입니다. 수정 스크립트는 `rem`으로 시작합니다.
    - 스크립트에 대한 설명은 [스크립트 설명](#bkmk_uea_scripts)을 참조하세요.
1. 제공된 이름을 사용하여 각 스크립트를 저장합니다. 이름은 각 스크립트의 맨 위에 있는 주석에도 있습니다.
    - 다른 스크립트 이름을 사용할 수 있지만 [스크립트 설명](#bkmk_uea_scripts) 섹션에 나열된 이름과는 일치하지 않게 됩니다.


### <a name="bkmk_uea_prs_deploy"></a> 스크립트 배포 및 모니터링

1. 콘솔에서 **사전 예방적 수정** 노드로 이동합니다.
1. **만들기** 단추를 클릭하여 스크립트 패키지를 만듭니다.
     [![사용자 경험 분석 사전 예방적 수정 페이지. 만들기 링크를 선택합니다.](media/uea-proactive-remediations-create.png)](media/uea-proactive-remediations-create.png#lightbox)
1. **기본 사항** 단계에서 스크립트 패키지에 **이름**을 지정하고 필요에 따라 **설명**을 입력합니다. **게시자** 필드는 편집할 수 있지만 기본적으로 테넌트 이름으로 설정됩니다. **버전**은 편집할 수 없습니다. 
1. **설정** 단계에서 앞서 다운로드한 스크립트의 텍스트를 **검색 스크립트** 및 **수정 스크립트** 필드로 복사합니다. 
   - 일치하는 검색 및 수정 스크립트가 동일한 패키지에 있어야 합니다. 예를 들어 `DetGPLastUpd.ps1` 검색 스크립트는 `RemGPLastUpd.ps11` 수정 스크립트와 일치합니다.
       [![사용자 경험 분석 사전 예방적 수정 스크립트 설정 페이지.](media/uea-proactive-remediations-script-settings.png)](media/uea-proactive-remediations-script-settings.png#lightbox)
1. 다음 권장 구성을 사용하여 **설정** 페이지에서 옵션을 완료합니다.
   - **로그온된 자격 증명을 사용하여 이 스크립트 실행**: 이는 스크립트에 따라 달라집니다. 자세한 내용은 [스크립트 설명](#bkmk_uea_scripts)을 참조하세요.
   - **스크립트 서명 확인 적용**: 아니요
   - **64비트 PowerShell에서 스크립트 실행**: 아니요
1. **다음**을 클릭하고 필요한 **범위 태그**를 할당합니다.
1. **할당** 단계에서 스크립트 패키지를 배포하려는 디바이스 그룹을 선택합니다.
1. 배포에 대한 **검토 + 만들기** 단계를 완료합니다.
1. **보고** > **사용자 경험 분석 - 사전 예방적 수정**에서 검색 및 수정 상태 개요를 확인할 수 있습니다.
       [![사용자 경험 분석 사전 예방적 수정 보고서, 개요 페이지.](media/uea-proactive-remediations-report-overview.png)](media/uea-proactive-remediations-report-overview.png#lightbox)
1. **디바이스 상태**를 클릭하여 배포의 각 디바이스에 대한 상태 정보를 가져옵니다.
       [![사용자 경험 분석 사전 예방적 수정 디바이스 상태.](media/uea-proactive-remediations-device-status.png)](media/uea-proactive-remediations-device-status.png#lightbox)


## <a name="bkmk_uea_set"></a> 사용자 경험 분석 설정

설정 페이지에서 **일반** 또는 **기준**을 선택할 수 있습니다. 각 설정은 아래에 설명되어 있습니다.

### <a name="bkmk_uea_gen"></a> 일반

**설정**의 **일반** 페이지를 사용하여 Intune 시작 성능 데이터 수집이 사용하도록 설정되었는지 확인할 수 있습니다. 이 옵션은 사용자 환경 분석을 활성화하기 위해 **시작**을 클릭하면 기본적으로 모든 디바이스에 대해 사용하도록 자동으로 설정됩니다. Intune 데이터 수집 정책 노드로 이동하여 부팅 및 로그인 레코드가 수집되는 디바이스 집합을 변경할 수 있습니다.

> [참고!] Configuration Manager 데이터 커넥터 구성 지침에 대한 자리 표시자가 있습니다. 그러나 이 기능은 초기 프라이빗 미리 보기에서는 구현되지 않았습니다.

  [![사용자 경험 분석 일반 설정 페이지](media/uea-settings-general.png)](media/uea-settings-general.png#lightbox)

### <a name="bkmk_uea_baselines"></a> 기준 관리

기준을 설정하여 현재 점수 및 하위 점수를 다른 사용자들과 비교할 수 있습니다.

1. **상업용 중앙값** 기준이 기본 제공됩니다. 이 기준을 사용하여 점수를 일반적인 엔터프라이즈와 비교할 수 있습니다.
1. 현재 메트릭에 따라 새 기준을 만들어 시간 경과에 따라 진전을 추적하거나 재발을 확인할 수 있습니다. **새로 만들기** 단추를 클릭하고 새 기준에 이름을 지정합니다. 보고서 페이지의 드롭다운에서 더 쉽게 선택할 수 있도록 이름에 날짜를 포함하는 것이 좋습니다.
1. 기준은 테넌트당 100개로 제한됩니다. 더 이상 필요하지 않은 이전 기준을 삭제할 수 있습니다.
1. 현재 메트릭은 보고서의 현재 기준을 하회하는 경우 빨간색으로 플래그가 지정되고 재발로 표시됩니다. 메트릭이 날마다 변동하는 것은 지극히 일반적이므로 재발 임계값을 설정할 수 있습니다. 기본값은 10%입니다. 이 임계값을 사용하면 10% 이상 재발한 경우에만 메트릭의 플래그가 재발로 지정됩니다.

   [![사용자 경험 분석 기준 설정 페이지](media/uea-settings-baseline.png)](media/uea-settings-baseline.png#lightbox)

## <a name="bkmk_uea_tshoot"></a> 문제 해결

사용자 경험 분석에 디바이스를 등록하려면 디바이스가 필수 기능 데이터를 Microsoft에 전송해야 합니다. 환경에서 프록시 서버를 사용하는 경우 이 정보를 사용하여 프록시를 구성합니다.

### <a name="endpoints"></a>엔드포인트

기능 데이터 공유를 사용하도록 설정하려면 다음 엔드포인트를 허용하도록 프록시 서버를 구성합니다.

> [!Important]  
> 개인 정보 및 데이터 무결성을 위해 Windows는 필수 기능 데이터 공유 엔드포인트와 통신할 때 Microsoft SSL 인증서(인증서 고정)를 확인합니다. SSL 가로채기 및 검사는 불가능합니다. 사용자 경험 분석을 사용하려면 이러한 엔드포인트를 SSL 검사에서 제외합니다.<!-- BUG 4647542 -->

| 엔드포인트  | 함수  |
|-----------|-----------|
| `https://v10c.events.data.microsoft.com` | 연결된 사용자 환경 및 진단 구성 요소 엔드포인트입니다. |
| `https://graph.windows.net` | Configuration Manager 서버 역할에서 사용자 경험 분석에 계층을 연결할 때 설정을 자동으로 검색하는 데 사용됩니다. 자세한 내용은 [사이트 시스템 서버에 대한 프록시 구성](/sccm/core/plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server)을 참조하세요. |
| `https://*.manage.microsoft.com` | 디바이스 컬렉션 및 디바이스를 사용자 경험 분석과 동기화하기 위하여 Configuration Manager 서버 역할에서만 사용됩니다. 자세한 내용은 [사이트 시스템 서버에 대한 프록시 구성](/sccm/core/plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server)을 참조하세요. |


### <a name="proxy-server-authentication"></a>프록시 서버 인증

인증으로 인해 프록시에서 데이터를 차단하지 않는지 확인합니다. 조직에서 아웃바운드 트래픽에 대해 프록시 서버 인증을 사용하는 경우 다음 방법 중 하나 이상을 사용합니다.

#### <a name="bypass-recommended"></a>바이패스(권장)

프록시 서버에서 데이터 공유 엔드포인트에 대한 트래픽에 대해 프록시 인증을 요구하지 않도록 구성합니다. 이 옵션은 가장 포괄적인 솔루션입니다. 모든 버전의 Windows 10에서 작동합니다.  

#### <a name="user-proxy-authentication"></a>사용자 프록시 인증

프록시 인증을 위해 로그인한 사용자의 컨텍스트를 사용하도록 디바이스를 구성합니다. 이 메서드에는 다음과 같은 구성이 필요합니다.

- 디바이스에 최신 Windows 10 품질 업데이트가 설치되어 있습니다.
- Windows 설정의 네트워크 & 인터넷 그룹의 **프록시 설정**에서 사용자 수준 프록시(WinINET 프록시)를 구성합니다. 레거시 인터넷 옵션 제어판을 사용할 수도 있습니다. 
- 사용자에게 데이터 공유 엔드포인트에 연결할 수 있는 프록시 권한이 있는지 확인합니다. 이 옵션을 사용하려면 디바이스에 프록시 권한이 있는 콘솔 사용자가 있어야 하므로 헤드리스 디바이스에서 이 방법을 사용할 수 없습니다.

> [!IMPORTANT]
> 사용자 프록시 인증 방법은 Microsoft Defender Advanced Threat Protection 사용과 호환되지 않습니다. 이 동작은 이 인증이 `0`으로 설정된 **DisableEnterpriseAuthProxy** 레지스트리 키를 사용하는 반면 Microsoft Defender ATP에서는 `1`로 설정하도록 요구하기 때문입니다. 자세한 내용은 [머신 프록시 및 인터넷 연결 설정 구성](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-proxy-internet-windows-defender-advanced-threat-protection)을 참조하세요.

#### <a name="device-proxy-authentication"></a>디바이스 프록시 인증

이 방법은 다음과 같은 구성이 필요하기 때문에 가장 복잡합니다.

- 디바이스가 로컬 시스템 컨텍스트에서 WinHTTP를 통해 프록시 서버에 연결할 수 있는지 확인합니다. 이 동작을 구성하려면 다음 옵션 중 하나를 사용합니다.
  - 명령줄 `netsh winhttp set proxy`
  - WPAD(웹 프록시 자동 검색) 프로토콜
  - 투명 프록시
  - 라우팅된 연결 또는 NAT(Network Address Translation) 사용

- Active Directory의 컴퓨터 계정에서 진단 데이터 엔드포인트에 액세스할 수 있도록 프록시 서버를 구성합니다. 이 구성에서는 Windows 통합 인증을 지원하기 위해 프록시 서버가 필요합니다.  

## <a name="bkmk_uea_faq"></a> 질문과 대답

### <a name="why-are-the-scripts-exiting-with-a-code-of-1"></a>스크립트가 코드 1로 종료되는 이유는 무엇인가요?

스크립트는 Intune에 수정이 발생해야 함을 알리기 위해 코드 1로 종료됩니다. 이 경우 검색 스크립트가 1로 끝나면 수정이 필요하다는 것을 의미합니다. CM에서만 실행되는 많은 스크립트 패키지는 준수를 표시하지만 코드 1로 종료될 수 있습니다. 이러한 스크립트의 경우 코드 1로 종료하더라도 문제가 있는 것은 아니지만 디바이스가 올바르게 수정되는지 확인하는 것이 좋습니다.

### <a name="why-did-the-update-stale-group-policies-script-return-with-error-0x87d00321"></a>기한 경과 그룹 정책 업데이트 스크립트가 0x87D00321 오류를 반환하는 이유는 무엇인가요?

0x87D00321는 스크립트 실행 시간 초과 오류입니다. 이 오류는 일반적으로 원격으로 연결된 컴퓨터에서 발생합니다. 잠재적 완화 한 가지는 내부 네트워크에 연결된 컴퓨터의 동적 컬렉션에만 배포하는 것일 수 있습니다.

## <a name="bkmk_uea_scripts"></a> 스크립트 설명

다음 표에서는 스크립트 이름, 설명, 검색, 수정 및 구성 가능한 항목을 보여 줍니다. 이름이 `det`로 시작하는 스크립트 파일은 검색 스크립트입니다. 수정 스크립트는 `rem`으로 시작합니다. 이러한 스크립트는 이 문서의 다음 섹션에서 복사할 수 있습니다.

|스크립트 이름|설명|
|---|---|
|**기한 경과 그룹 정책 업데이트** </br>`DetGPLastUpd.ps1` </br> `RemGPLastUpd.ps1`| 마지막 그룹 정책 새로 고침이 `7 days`보다 오래 되었는지 검색합니다.  </br>검색 스크립트에서 `$numDays` 값을 변경하여 7일 임계값을 사용자 지정합니다. </br></br>`gpupdate /target:computer /force` 및 `gpupdate /target:user /force`를 실행하여 수정합니다.  </br> </br>그룹 정책을 통해 인증서 및 구성이 전달될 때 네트워크 연결 관련 지원 호출을 줄이는 데 도움이 됩니다. </br> </br> **로그온된 자격 증명을 사용하여 스크립트 실행**: 예|
|**Office 간편 실행 서비스 다시 시작** </br> `DetectClickToRunServiceState.ps1` </br> `RemediateClickToRunServiceState.ps1`| 간편 실행 서비스가 자동으로 시작하도록 설정되었는지 여부와 서비스가 중지되었는지 여부를 검색합니다. </br> </br> 서비스를 자동으로 시작하도록 설정하고 서비스가 중지된 경우 서비스를 시작하여 수정합니다. </br></br> 간편 실행 서비스가 중지되어 Win32 Office 365 ProPlus가 시작되지 않는 문제를 해결하는 데 도움이 됩니다. </br> </br> **로그온된 자격 증명을 사용하여 스크립트 실행**: 아니요|
|**네트워크 인증서 확인** </br>`DetExpIssuerCerts.ps1` </br>`RemExpIssuerCerts.ps1`|컴퓨터 또는 사용자의 개인 저장소에서 만료되었거나 만료가 가까운 CA 발급 인증서를 검색합니다. </br> 검색 스크립트에서 `$strMatch` 값을 변경하여 CA를 지정합니다. 만료된 인증서를 찾으려면 `$expiringDays`에 0을 지정하고, 만료가 가까운 인증서를 찾으려면 다른 일 수를 지정합니다.  </br></br>사용자에 대한 토스트 알림을 발생시켜 수정합니다. </br> `$Title` 및 `$msgText` 값과 사용자에게 표시할 메시지 제목 및 텍스트를 지정합니다. </br> </br> 갱신해야 할 수 있는 만료된 인증서를 사용자에게 알립니다. </br> </br> **로그온된 자격 증명을 사용하여 스크립트 실행**: 아니요|
|**기한 만료 인증서 지우기** </br>`DetExpUserCerts.ps1` </br> `RemExpUserCerts.ps1`| 현재 사용자의 개인 저장소에서 만료된 CA 발급 인증서를 검색합니다. </br> 검색 스크립트에서 `$certCN` 값을 변경하여 CA를 지정합니다. </br> </br> 현재 사용자의 개인 저장소에서 만료된 CA 발급 인증서를 삭제하여 수정합니다. </br> 수정 스크립트에서 `$certCN` 값을 변경하여 CA를 지정합니다. </br> </br> 현재 사용자의 개인 저장소에서 만료된 CA 발급 인증서를 찾아 삭제합니다. </br> </br> **로그온된 자격 증명을 사용하여 스크립트 실행**: 예|

## <a name="bkmk_uea_ps_scripts"></a> PowerShell 스크립트

### <a name="detgplastupdps1"></a>DetGPLastUpd.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     DetGPLastUpd.ps1
# Description:     Detect if Group Policy has been updated within number of days
# Notes:           Remediate if "Match", $numDays default value of 7, change as appropriate
#
#=============================================================================================================================

# Define Variables
$numDays = 7

try {
    $gpResult = gpresult /R | Select-String -pattern “Last time Group Policy was applied:” | Select-Object -last 1

    if ($gpResult){
    [int]$lastGPUpdateDays = (New-TimeSpan -Start $lastGPUpdateDate -End (Get-Date)).Days
        if ($lastGPUpdateDays -gt $numDays){
            #We want within last $numDays so we get "Match"
            Write-Host "Match"
            exit 1
        }
        else {
            #Script succeeds but > $numDays since last update so remediate
            #Exit 1 for Intune and "Match" for ConfigMan
            Write-Host "No_Match"
            exit 0
        }
    }
}
catch {
    $errMsg = $_.Exception.Message
    Write-Error $errMsg
    exit 1
}
```

### <a name="remgplastupdps1"></a>RemGPLastUpd.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     RemGPLastUpd.ps1
# Description:     This script triggers Group Policy update
# Notes:           No variable substitution needed
#
#=============================================================================================================================

try{
    $compGP = gpupdate /target:computer /force | out-string
    $userGP = gpupdate /target:user /force | out-string
    exit 0
}
catch{
    $errMsg = $_.Exception.Message
    Write-Error $errMsg
    exit 1
}
```

### <a name="detectclicktorunservicestateps1"></a>DetectClickToRunServiceState.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     DetectClickToRunServiceState.ps1
# Description:     Detect if Office 16 installed and if "Click to Run Service" is running.
# Notes:           No variable substitution should be necessary
#
#=============================================================================================================================

# Define Variables
$curSvcStat,$svcCTRSvc,$errMsg = "","",""

# Main script
If (-not (Test-Path -Path 'hklm:\Software\Microsoft\Office\16.0')){
    Return "Office 16.0 (or greater) not present on this machine"
    exit 0   
} 

Try{        
    $svcCTRSvc = Get-Service "ClickToRunSvc"
    $curSvcStat = $svcCTRSvc.Status
}

Catch{    
    $errMsg = $_.Exception.Message
    Write-Error $errMsg
    exit 1
}

If ($curSvcStat -eq "Running"){
    Write-Output $curSvcStat
    exit 0                        
}
Else{
    If($curSvcStat -eq "Stopped"){
    Write-Output $curSvcStat
    exit 1     
    }
}
Else{
    Write-Error "Error: " + $errMsg
    exit 1
}
```

### <a name="remediateclicktorunservicestateps1"></a>RemediateClickToRunServiceState.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     RemediateClickToRunServiceState.ps1
# Description:     Start the "Click to Run Service" and change its startup type to Automatic
#       Notes:     No variable substitution needed
#
#=============================================================================================================================

# Define Variables
$svcCur = "ClickToRunSvc"
$curSvcStat,$svcCTRSvc,$errMsg = "","",""
$ctr = 0

# Main script
# Make sure nothing has changed since detection, the service exists and is stopped
Try{        
    $svcCTRSvc = Get-Service "ClickToRunSvc"
    $curSvcStat = $svcCTRSvc.Status
    }

Catch{    
    $errMsg = $_.Exception.Message
    }
        
# If the service got started between detection and now (nested if) then return
# If the service got uninstalled or corrupted between detection and now (else) then return the "Error: " + the error
If ($curSvcStat -ne "Stopped"){
    If ($curSvcStat -eq "Running"){
        return
    }
    Else{
        return "Error: " + $errMsg
    }
}

# Service should be there and stopped, change the startup type and start
Try{        
    Set-Service $svcCur -StartupType Automatic
    Start-Service $svcCur
    $svcCTRSvc = Get-Service $svcCur
    $curSvcStat = $svcCTRSvc.Status
        While ($curSvcStat.Equals("Stopped")){
            Start-Sleep -Seconds 5
            ctr++
            if(ctr == 12){
                Return "Service could not be started after 60 seconds"
                break
            }
        }
    }

Catch{    
    $errMsg = $_.Exception.Message
    Return $errMsg
    }

Return $curSvcStat
```

### <a name="detexpissuercertsps1"></a>DetExpIssuerCerts.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     DetExpIssuerCerts.ps1
# Description:     Detect expired certificates issued by "CN=<your CA here>" in either Machine
#                  or User certificate store
# Notes:           Change the value of the variable $strMatch from "CN=<your CA here>" to "CN=..."
#                  For testing purposes the value of the variable $expiringDays can be changed to a positive integer
#                  Don't change the $results variable
#
#=============================================================================================================================

# Define Variables
$results = @()
$expiringDays = 0
$strMatch = "CN=<your CA here>"

try
{
    $results = @(Get-ChildItem -Path Cert:\LocalMachine\My -Recurse -ExpiringInDays $expiringDays | where {$_.Issuer -match $strMatch})
    $results += @(Get-ChildItem -Path Cert:\CurrentUser\My -Recurse -ExpiringInDays $expiringDays | where {$_.Issuer -match $strMatch}) 
    if (($results -ne $null)){
        #Below necessary for Intune as of 10/2019 will only remediate Exit Code 1
        Write-Host "Match"
        Return $results.count
        exit 1
    }
    else{
        #No matching certificates, do not remediate
        Write-Host "No_Match"        
        exit 0
    }   
}
catch{
    $errMsg = $_.Exception.Message
    Write-Error $errMsg
    exit 1
}
```

### <a name="remexpissuercertsps1"></a>RemExpIssuerCerts.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     RemExpIssuerCerts.ps1
# Description:     Raise a Toast Notification if expired certificates issued by "CN=..."
#                  to user or machine on the machine where detection script found them. No remediation action besides
#                  the Toast is taken.
# Notes:           Change the values of the variables $Title and $msgText
#
#=============================================================================================================================

## Raise toast to have user contact whoever is specified in the $msgText

# Define Variables
$delExpCert = 0
$Title = "Title"
$msgText = "message"

# Main script
[Windows.UI.Notifications.ToastNotificationManager, Windows.UI.Notifications, ContentType = WindowsRuntime] | Out-Null
[Windows.UI.Notifications.ToastNotification, Windows.UI.Notifications, ContentType = WindowsRuntime] | Out-Null
[Windows.Data.Xml.Dom.XmlDocument, Windows.Data.Xml.Dom.XmlDocument, ContentType = WindowsRuntime] | Out-Null

$APP_ID = '{1AC14E77-02E7-4E5D-B744-2EB1AE5198B7}\WindowsPowerShell\v1.0\powershell.exe'

$template = @"
<toast>
    <visual>
        <binding template="ToastText02">
            <text id="1">$Title</text>
            <text id="2">$msgText</text>
        </binding>
    </visual>
</toast>
"@

$xml = New-Object Windows.Data.Xml.Dom.XmlDocument
$xml.LoadXml($template)
$toast = New-Object Windows.UI.Notifications.ToastNotification $xml
[Windows.UI.Notifications.ToastNotificationManager]::CreateToastNotifier($APP_ID).Show($toast)
```

### <a name="detexpusercertsps1"></a>DetExpUserCerts.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     DetExpUserCerts.ps1
# Description:     Detect expired certificates issued by "CN=<your CA here>" to User
# Notes:           Change the value of the variable $certCN from "CN=<your CA here>" to "CN=...".
#                  Don't change $results
#
#=============================================================================================================================

# Define Variables
$results = 0
$certCN = "CN=<your CA here>"

try
{   
    $results = Get-ChildItem -Path Cert:\CurrentUser\My -Recurse -ExpiringInDays 0 | where {$_.Issuer -eq($certCN)}
    if (($results -ne $null)){
        #Below necessary for Intune as of 10/2019 will only remediate Exit Code 1
        Write-Host "Match"
        Return $results.count
        exit 1
    }
    else{
        Write-Host "No_Match"
        exit 0
    }    
}
catch{
    $errMsg = $_.Exception.Message
    Write-Error $errMsg
    exit 1
}
```

### <a name="remexpusercertsps1"></a>RemExpUserCerts.ps1

```powershell
#=============================================================================================================================
#
# Script Name:     RemExpUserCerts.ps1
# Description:     Remove expired certificates issued by "CN=<your CA here>" to User
# Notes:           Change the value of the variable $certCN from "CN=<your CA here>" to "CN=..."
#
#=============================================================================================================================

# Define Variables
$certCN = "CN=<your CA here>"

try
{
    Get-ChildItem -Path cert:\CurrentUser -Recurse -ExpiringInDays 0 | where {$_.Issuer -eq($certCN)} | Remove-Item
    exit 0
}
catch{
    $errMsg = $_.Exception.Message
    Write-Error $errMsg
    exit 1
}
```

## <a name="bkmk_uea_privacy"></a> 사용자 경험 분석 데이터 프라이버시

### <a name="data-flow"></a>데이터 흐름

다음 그림에서는 데이터 서비스, 임시 저장소 및 테넌트를 통해 개별 디바이스에서 필수 기능 데이터를 전달하는 방법을 보여 줍니다. 데이터는 Windows 진단 데이터에 의존하지 않고 기존 엔터프라이즈 파이프라인을 통해 흐릅니다.


[![사용자 경험 데이터 흐름 다이어그램](media/uea-dataflow.png)](media/uea-dataflow.png#lightbox)

1. 등록된 디바이스에 대한 **Intune 데이터 수집** 정책을 구성합니다.

2. 디바이스에서 필수 기능 데이터를 보냅니다.

    - Intune 디바이스의 경우 Intune 관리 확장에서 데이터가 전송됩니다.
    - Configuration Manager 관리 디바이스의 경우 데이터가 ConfigMgr 커넥터를 통해 Microsoft Endpoint Management로 전달될 수도 있습니다. ConfigMgr 커넥터는 클라우드로 연결되어 있습니다. 공동 관리를 설정하는 것이 아니라 Intune 테넌트에 대한 연결만 필요합니다.

3. 데이터는 Microsoft Graph를 통해 관리 콘솔로 흐릅니다.

### <a name="resources"></a>리소스

관련된 개인 정보 측면에 대한 자세한 내용은 다음 문서를 참조하세요.

- [Microsoft Intune 개인 정보 취급 방침](https://docs.microsoft.com/legal/intune/microsoft-intune-privacy-statement)
- [Windows 10 및 개인 정보 규정 준수](https://docs.microsoft.com/windows/privacy/windows-10-and-privacy-compliance)
- [사용 약관 및 설명서](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)  
- [Microsoft Azure 데이터 센터에서 보안 및 개인 정보 보호](https://azure.microsoft.com/global-infrastructure/)  
- [신뢰할 수 있는 클라우드의 신뢰도](https://azure.microsoft.com/overview/trusted-cloud/)  
- [보안 센터](https://www.microsoft.com/trustcenter)  

