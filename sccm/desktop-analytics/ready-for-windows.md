---
title: Windows 준비 완료
titleSuffix: Configuration Manager
description: Windows 웹 사이트 준비
ms.date: 10/30/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 3f09226c-4ca7-4e43-9ae8-5ee6e78e6bc2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 338ef88d4fa32767d9e4eb605a4ad800c11dbfce
ms.sourcegitcommit: c25a91db838805eca5dbb421a3de401928968bf0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73142961"
---
# <a name="ready-for-modern-desktop-retirement-faq"></a>최신 바탕 화면 사용 중지 FAQ

<!-- placeholder -->

## <a name="general"></a>일반

### <a name="what-happened-to-the-ready-for-windows-website"></a>Windows 웹 사이트 준비 완료는 어떻게 되었습니까?

대부분의 고객에 게는 Windows 10 및 Office 365 ProPlus를 통해 최신 상태를 유지 하는 데 문제가 있습니다. 이 프로세스는 일반적으로 수동 이기 때문에 응용 프로그램을 테스트 하는 것이 가장 중요 한 과제입니다. IT 관리자와 응용 프로그램 소유자가 기존 응용 프로그램을 지속적으로 분석 한 후 발생 하는 모든 문제를 해결 하는 데 시간이 많이 걸립니다.

*최신 데스크톱 디렉터리에* 는 Windows 10 및 Office 365 ProPlus를 실행 하는 상용 장치에서 지원 되 고 사용 중인 소프트웨어 솔루션이 나열 되어 있습니다. 디렉터리는 IT 관리자가 배포를 위해 최신 버전의 Windows 10 및 Office 365을 고려 하는 데 도움이 됩니다.

IT 관리자의 의견은 배포 계획을 계획 하기 위해 이미 사용 하 고 있는 도구와 이러한 통찰력을 통합 하려고 한다는 것입니다. Configuration Manager에서 [데스크톱 분석](https://aka.ms/dadocs) 및 [office 365 proplus 준비 기능](https://docs.microsoft.com/deployoffice/readiness-tools#office-365-proplus-readiness-features-in-configuration-manager-current-branch) 을 사용 하 여 Windows 10 및 office 365 ProPlus 업그레이드 프로젝트를 계획 하 고 관리 합니다. 

### <a name="what-is-desktop-analytics"></a>Desktop Analytics란?

[데스크톱 분석](https://aka.ms/dadocs) 은 Configuration Manager와 통합 되는 클라우드 기반 서비스입니다. 이 서비스는 Windows 끝점의 업데이트 준비에 대 한 더 많은 의사 결정을 내릴 수 있는 통찰력 및 인텔리전스를 제공 합니다. Microsoft의 클라우드 서비스에 연결 된 수백만 대의 Windows 장치에서 집계 된 정보를 사용 하 여 조직과 관련 된 데이터를 결합 합니다.

-   조직에서 관리 하는 끝점, 응용 프로그램 및 드라이버에 대 한 포괄적인 보기를 가져옵니다.

-   최신 Windows 기능 업데이트를 사용 하 여 응용 프로그램 및 드라이버 호환성을 평가 합니다. 알려진 문제에 대 한 완화 권장 사항 및 lob (기간 업무) 앱에 대 한 고급 정보를 수신 합니다.

-   Microsoft 클라우드에서 AI (인공 지능)를 사용 하 여 전체 환경을 적절 하 게 표현 하는 파일럿 장치 집합을 최적화 합니다.

### <a name="why-should-i-use-desktop-analytics-for-my-windows-deployment-plans"></a>Windows 배포 계획에 데스크톱 분석을 사용 해야 하는 이유는 무엇 인가요?

데스크톱 분석은 다음과 같은 이점을 제공 합니다.

-   **장치 및 소프트웨어 인벤토리**: 앱 및 Windows 버전 등의 주요 요소에 대 한 인벤토리를 작성 합니다.

-   **파일럿 식별**: 가장 광범위 한 요소를 제공 하는 가장 작은 장치 집합의 id입니다. Windows 업그레이드 및 업데이트의 파일럿에 가장 중요 한 요소를 중점적으로 설명 합니다. 파일럿이 더 성공적인 지 확인 하 여 프로덕션 환경에서 광범위 한 배포에 대해 더 빠르고 안전 하 게 계속할 수 있습니다.

-   **문제 식별**: 사용자 환경의 데이터와 함께 집계 된 시장 데이터를 사용 하 여 서비스에서 Windows를 사용 하 여 최신 상태를 유지 하 고 유지 하는 잠재적인 문제를 예측 합니다. 그런 다음 잠재적 완화를 제안 합니다.

-   **Configuration Manager 통합**: It 클라우드-기존 온-프레미스 인프라를 사용 하도록 설정 합니다. 이 데이터 및 분석을 사용 하 여 장치에서 Windows를 배포 하 고 관리 합니다.

### <a name="what-does-the-ready-for-windows-status-mean-in-desktop-analytics"></a>데스크톱 분석에서 *Windows의 준비* 상태는 무엇을 의미 하나요?

**도입 상태** 는 Microsoft와 데이터를 공유 하는 상용 장치의 정보를 기반으로 합니다. 상태는 소프트웨어 공급 업체의 지원 문과 통합 되어 있습니다.

데스크톱 분석은 상용 장치에 있는 자산의 각 버전에 대 한 도입 상태를 제공 합니다. 이 상태에는 데이터를 공유 하지 않는 장치 또는 소비자 장치의 데이터가 포함 되지 않습니다. 상태는 모든 Windows 10 장치에서 도입 률을 나타내지 않을 수 있습니다.

자세한 내용은 [호환성 평가](/sccm/desktop-analytics/compat-assessment#ready-for-windows)를 참조 하세요.

### <a name="what-assets-get-the-ready-for-windows-status-in-desktop-analytics"></a>데스크톱 분석에서 *Windows 상태에 대 한 준비* 를 받는 자산은 무엇 인가요? 

다음과 같은 경우에는 데스크톱 분석에서 자산에 *Windows 상태를 준비할* 수 있습니다.

-   소프트웨어 공급자는 솔루션에 대 한 지원을 선언 합니다.
-   고객은 Microsoft와 정보를 공유 하는 많은 상용 Windows 10 장치에 배포 했습니다.
-   자산은 상업적 사용자와 관련이 있습니다.

### <a name="what-additional-insights-do-i-get-in-desktop-analytics"></a>데스크톱 분석에서 어떤 추가 정보를 얻을 까 요?

데스크톱 분석은 [장치 및 설치 된 앱](/sccm/desktop-analytics/about-assets)의 인벤토리 뿐만 아니라 lob (기간 업무) 앱에 대 한 [고급 정보](/sccm/desktop-analytics/compat-assessment#advanced-insights) 를 제공 합니다. 

## <a name="software-providers"></a>소프트웨어 공급자

### <a name="can-i-still-list-my-software-solution-in-desktop-analytics"></a>데스크톱 분석에 소프트웨어 솔루션을 계속 나열할 수 있나요?

제품이 32 비트 또는 64 비트 Windows 10 또는 Office 365 ProPlus와 함께 작동 하는 지원 문을 게시 합니다. 데스크톱 분석에서 솔루션을 소개 하려면 Microsoft 담당자에 게 문의 하세요.

### <a name="how-can-listing-my-solutions-benefit-me"></a>솔루션 혜택을 나열 하는 방법

수천 개의 IT 관리자가 Configuration Manager 및 데스크톱 분석으로 수백만 대의 장치를 관리 합니다. 이러한 도구를 사용 하 여 조직을 안전 하 게 계획 하 고 최신 버전의 Windows 10 및 Office 365 ProPlus로 업그레이드 합니다. 또한 소프트웨어 솔루션에 대 한 구매 결정을 내리는 데 사용 됩니다.

Microsoft는 소프트웨어 공급 업체의 지원 명세서와 상용 장치에서 받는 도입 정보를 통합 합니다. 전 세계의 조직은 데스크톱 분석 및 Office 준비 도구에서이 데이터를 사용 합니다. 

지원 문이 자산과 올바르게 연결 되지 않은 경우 Microsoft 담당자에 게 문의 하세요.

### <a name="can-i-see-detailed-performance-metrics-on-my-assets"></a>자산에 대 한 자세한 성능 메트릭을 볼 수 있나요?

개발자 센터를 통해 상태 및 메트릭 보고서를 사용 하 여 솔루션의 성능을 평가 합니다. 

- [Windows 스토어](https://docs.microsoft.com/windows/uwp/publish/health-report)
- [데스크톱과](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
- [Office 추가 기능](https://docs.microsoft.com/office/dev/store/update-unpublish-and-view-metrics) 

### <a name="how-can-i-develop-compatible-assets-for-windows-10-and-office-365-proplus"></a>Windows 10 및 Office 365 ProPlus에 대해 호환 되는 자산을 개발 하려면 어떻게 해야 하나요?

데스크톱 응용 프로그램이 지금 호환 되는지 확인 하 고 나중에 Windows 10과 호환 되는지 확인 합니다. 자세한 내용은 [개발자를 위한 응용 프로그램 호환성](https://developer.microsoft.com/windows/desktop/app-compatibility)을 참조 하세요.

Office 365 ProPlus에 대 한 솔루션을 개발 하는 경우 [office의 COM, VSTO 및 VBA 추가 기능에 대 한 개발 모범 사례](https://docs.microsoft.com/visualstudio/vsto/development-best-practices-for-com-vsto-and-vba-add-ins-in-office)를 참조 하세요.
