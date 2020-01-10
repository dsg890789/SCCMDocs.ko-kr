---
title: Windows 준비 완료
titleSuffix: Configuration Manager
description: Windows 준비 완료의 사용 중지 웹 사이트 정보
ms.date: 10/30/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3f09226c-4ca7-4e43-9ae8-5ee6e78e6bc2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 2e5ead90769d8fdacc28502852dccead7c2dbd52
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825577"
---
# <a name="ready-for-modern-desktop-retirement-faq"></a>최신 데스크톱 준비 완료 사용 중지 FAQ

<!-- placeholder -->

## <a name="general"></a>일반

### <a name="what-happened-to-the-ready-for-windows-website"></a>Windows 준비 완료 웹 사이트는 어떻게 되었습니까?

대부분의 고객은 Windows 10 및 Office 365 ProPlus를 사용하여 현재 상태를 유지하는 데 어려움이 있습니다. 이 프로세스는 일반적으로 수동이기 때문에 애플리케이션을 테스트하는 것이 가장 중요한 과제입니다. IT 관리자와 애플리케이션 소유자가 기존 애플리케이션을 지속적으로 분석한 다음, 발생하는 모든 문제를 해결하는 데는 많은 시간이 소요됩니다.

*최신 데스크톱 준비 완료* 디렉터리는 Windows 10 및 Office 365 ProPlus를 실행하는 상업용 디바이스에서 지원되고 현재 사용 중인 소프트웨어 솔루션을 나열했습니다. 이 디렉터리는 배포를 위해 최신 버전의 Windows 10 및 Office 365를 고려하고 있는 IT 관리자를 돕습니다.

IT 관리자의 피드백은 배포 계획을 계획하기 위해 이미 사용하고 있는 도구와 이러한 인사이트를 통합하려고 한다는 것입니다. Configuration Manager에서 [Desktop Analytics](https://aka.ms/dadocs) 및 [Office 365 ProPlus 준비 기능](https://docs.microsoft.com/deployoffice/readiness-tools#office-365-proplus-readiness-features-in-configuration-manager-current-branch)을 사용하여 Windows 10 및 Office 365 ProPlus 업그레이드 프로젝트를 계획하고 관리합니다. 

### <a name="what-is-desktop-analytics"></a>Desktop Analytics란?

[Desktop Analytics](https://aka.ms/dadocs)는 Configuration Manager와 통합되는 클라우드 기반 서비스입니다. 서비스는 Windows 엔드포인트의 업데이트 준비 사항에 대해 충분한 정보를 파악한 후 결정하도록 인사이트와 인텔리전스를 제공합니다. 조직과 관련된 데이터를 Microsoft의 클라우드 서비스에 연결된 수백만 대의 Windows 디바이스에서 집계된 인사이트와 결합합니다.

-   조직에서 관리하는 엔드포인트, 애플리케이션 및 드라이버에 대한 포괄적인 보기를 가져옵니다.

-   최신 Windows 기능 업데이트를 사용하여 애플리케이션 및 드라이버 호환성을 평가합니다. 알려진 문제에 대한 완화 권장 사항 및 기간 업무 앱에 대한 고급 인사이트를 수신합니다.

-   Microsoft 클라우드에서 AI(인공 지능)를 사용하여 전체 환경을 적절하게 표현하는 파일럿 디바이스 세트를 최적화합니다.

### <a name="why-should-i-use-desktop-analytics-for-my-windows-deployment-plans"></a>Windows 배포 계획에 Desktop Analytics를 사용해야 하는 이유는 무엇인가요?

Desktop Analytics는 다음과 같은 이점을 제공합니다.

-   **디바이스 및 소프트웨어 인벤토리**: 앱 및 Windows 버전 등의 주요 요소에 대한 인벤토리

-   **파일럿 식별**: 가장 광범위한 요소를 제공하는 가장 작은 디바이스 세트의 식별입니다. Windows 업그레이드 및 업데이트의 파일럿에 가장 중요한 요소에 중점을 둡니다. 파일럿이 더 성공하도록 하면 프로덕션 환경에서 더 빠르고 자신 있게 광범위하게 배포할 수 있습니다.

-   **문제 식별**: 서비스는 사용자 환경의 데이터와 함께 집계된 시장 데이터를 사용하여 Windows에 대한 현재 상태를 유지하는 데 잠재적인 문제를 예측합니다. 그런 다음, 잠재적 완화를 제안합니다.

-   **Configuration Manager 통합**: 기존 온-프레미스 인프라를 클라우드 활성화합니다. 이 데이터 및 분석을 사용하여 디바이스에서 Windows를 배포하고 관리합니다.

### <a name="what-does-the-ready-for-windows-status-mean-in-desktop-analytics"></a>Desktop Analytics에서 *Windows 준비 완료* 상태는 무엇을 의미하나요?

**도입 상태**는 Microsoft와 데이터를 공유하는 상업용 디바이스의 정보를 기반으로 합니다. 상태는 소프트웨어 공급 업체의 지원 명령문과 통합되어 있습니다.

Desktop Analytics는 상업용 디바이스에 있는 자산의 각 버전에 대한 도입 상태를 제공합니다. 이 상태는 데이터를 공유하지 않는 소비자 디바이스 또는 디바이스의 데이터를 포함하지 않습니다. 상태는 모든 Windows 10 디바이스에서 도입률을 나타내지 않을 수 있습니다.

자세한 내용은 [호환성 평가](/sccm/desktop-analytics/compat-assessment#ready-for-windows)를 참조하세요.

### <a name="what-assets-get-the-ready-for-windows-status-in-desktop-analytics"></a>Desktop Analytics에서 *Windows 준비 완료* 상태를 얻는 자산은 무엇인가요? 

자산은 다음의 경우 Desktop Analytics에서 *Windows 준비 완료* 상태를 갖습니다.

-   소프트웨어 공급자가 솔루션에 대한 지원을 선언합니다.
-   고객은 이를 Microsoft와 정보를 공유하는 상당 수의 상업용 Windows 10 디바이스에 배포했습니다.
-   자산은 상업용 사용자와 관련이 있습니다.

### <a name="what-additional-insights-do-i-get-in-desktop-analytics"></a>Desktop Analytics에서 어떤 추가 인사이트를 얻나요?

Desktop Analytics는 [디바이스 및 설치된 앱](/sccm/desktop-analytics/about-assets)의 인벤토리와 기간 업무 앱에 대한 [고급 인사이트](/sccm/desktop-analytics/compat-assessment#advanced-insights)를 제공합니다. 

## <a name="software-providers"></a>소프트웨어 공급자

### <a name="can-i-still-list-my-software-solution-in-desktop-analytics"></a>Desktop Analytics에 소프트웨어 솔루션을 계속 나열할 수 있나요?

제품이 32비트 또는 64비트 Windows 10 또는 Office 365 ProPlus와 함께 작동하는 지원 명령문을 게시합니다. Desktop Analytics에서 솔루션을 소개하려면 Microsoft 담당자에게 문의하세요.

### <a name="how-can-listing-my-solutions-benefit-me"></a>솔루션을 나열하는 것이 어떻게 도움이 될 수 있나요?

수천 개의 IT 관리자가 Configuration Manager 및 Desktop Analytics로 수백만 대의 디바이스를 관리합니다. 관리자는 이러한 도구를 사용하여 조직을 최신 버전의 Windows 10 및 Office 365 ProPlus로 안전하게 계획하고 업그레이드합니다. 또한 소프트웨어 솔루션에 대한 구매 결정을 내리는 데도 사용합니다.

Microsoft는 소프트웨어 공급 업체의 지원 명령문과 상업용 디바이스에서 받는 도입 정보를 통합합니다. 그런 다음, 전 세계의 조직은 Desktop Analytics 및 Office 준비 도구에서 이 데이터를 사용합니다. 

지원 명령문이 자산과 올바르게 연결되지 않은 경우 Microsoft 담당자에게 문의하세요.

### <a name="can-i-see-detailed-performance-metrics-on-my-assets"></a>자산에서 자세한 성능 메트릭을 볼 수 있나요?

개발자 센터를 통해 상태 및 메트릭 보고서를 사용하여 솔루션의 성능을 평가합니다. 

- [Windows 스토어](https://docs.microsoft.com/windows/uwp/publish/health-report)
- [데스크톱](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
- [Office 추가 기능](https://docs.microsoft.com/office/dev/store/update-unpublish-and-view-metrics) 

### <a name="how-can-i-develop-compatible-assets-for-windows-10-and-office-365-proplus"></a>Windows 10 및 Office 365 ProPlus에 대해 호환되는 자산을 개발하려면 어떻게 해야 하나요?

데스크톱 애플리케이션이 지금 호환되는지 확인하고, 향후 Windows 10과 호환되는지 확인합니다. 자세한 내용은 [개발자를 위한 애플리케이션 호환성](https://developer.microsoft.com/windows/desktop/app-compatibility)을 참조하세요.

Office 365 ProPlus에 대한 솔루션을 개발하는 경우 [Office의 COM, VSTO 및 VBA 추가 기능에 대한 개발 모범 사례](https://docs.microsoft.com/visualstudio/vsto/development-best-practices-for-com-vsto-and-vba-add-ins-in-office)를 참조하세요.
