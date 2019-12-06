---
title: Desktop Analytics의 업데이트
titleSuffix: Configuration Manager
description: Desktop Analytics의 보안 및 기능 업데이트에 대해 알아봅니다.
ms.date: 08/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 14ae894c-26fb-4fe3-b51d-e80700122df4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f090c80f70ef8d286a36236c48503817adb93591
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72387025"
---
# <a name="updates-in-desktop-analytics"></a>Desktop Analytics의 업데이트

Desktop Analytics 포털에서 보안 및 기능 업데이트의 상태를 확인합니다. Desktop Analytics 주 메뉴의 모니터 그룹에서 이러한 노드를 선택합니다. 이러한 노드는 사용자 환경에서 이러한 업데이트 상태에 대한 인사이트를 제공합니다.


## <a name="security-updates"></a>보안 업데이트

보안 업데이트의 현재 상태를 검토하려면 Desktop Analytics의 **모니터** 섹션에서 **보안 업데이트**를 선택합니다.

![Desktop Analytics의 보안 업데이트 노드](media/security-updates.png)

이 보기에서는 Windows 10을 실행하는 디바이스에 대한 *보안* 업데이트가 요약되어 있습니다. 가로 막대형 차트의 디바이스는 다음 레이블로 분류됩니다.

#### <a name="latest"></a>최신

디바이스가 해당 버전 및 채널에 대한 최신 보안 업데이트를 실행하고 있습니다.

#### <a name="latest-1"></a>최신-1

디바이스가 해당 채널에서 사용 가능한 최신 업데이트보다 한 버전 이전의 보안 업데이트를 실행하고 있습니다.

#### <a name="older"></a>이전

디바이스가 최신-1 이전의 보안 업데이트를 실행하고 있습니다.

#### <a name="not-measured"></a>측정되지 않음

Desktop Analytics는 디바이스를 평가하지 않았습니다. 이 상태에는 Windows Insider Program에 등록된 Windows 7, Windows 8.1 또는 Windows 10 디바이스를 실행하는 디바이스가 포함됩니다.  

Windows 10 디바이스가 Microsoft 계정으로 *인증되지 않은* 경우 Windows에서 이 데이터를 보고하지 않습니다. 이 인증은 일반적으로 Windows 설치 프로그램 OOBE(기본 제공 환경)의 일부로 완료됩니다.<!-- 5148153 -->


## <a name="feature-updates"></a>기능 업데이트

기능 업데이트의 현재 상태를 검토하려면 Desktop Analytics의 **모니터** 섹션에서 **기능 업데이트**를 선택합니다.

![Desktop Analytics의 기능 업데이트 노드](media/feature-updates.png)

이 보기에서는 Windows 10을 실행하는 디바이스에 대한 *기능* 업데이트가 요약되어 있습니다.

서비스 기간에 대한 자세한 내용은 [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조하세요.  

가로 막대형 차트의 디바이스는 다음 레이블로 분류됩니다.

#### <a name="in-service"></a>서비스 중

디바이스가 해당 버전 및 채널에 대한 최신 기능 업데이트를 실행하고 있습니다.  

#### <a name="near-end-of-service"></a>서비스가 끝나감

디바이스가 서비스 종료에 도달하는 90일 이내에 기능 업데이트를 실행하고 있습니다.

#### <a name="end-of-service"></a>서비스 종료

디바이스가 서비스 종료 날짜가 지난 기능 업데이트를 실행하고 있습니다. 서비스 종료 날짜에 대한 자세한 내용은 [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조하세요.

#### <a name="not-measured"></a>측정되지 않음

Desktop Analytics는 디바이스를 평가하지 않았습니다. 이 상태에는 Windows Insider Program에 등록된 Windows 7, Windows 8.1 또는 Windows 10 디바이스를 실행하는 디바이스가 포함됩니다.

Windows 10 디바이스가 Microsoft 계정으로 *인증되지 않은* 경우 Windows에서 이 데이터를 보고하지 않습니다. 이 인증은 일반적으로 Windows 설치 프로그램 OOBE(기본 제공 환경)의 일부로 완료됩니다.<!-- 5148153 -->


## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 자산에 대해 알아보기](/sccm/desktop-analytics/about-assets): 디바이스, 드라이버 및 앱  

- [배포 계획에 대한 자세한 설명](/sccm/desktop-analytics/about-deployment-plans)  
