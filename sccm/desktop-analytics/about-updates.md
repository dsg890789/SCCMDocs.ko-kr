---
title: 데스크톱 분석의 업데이트
titleSuffix: Configuration Manager
description: 데스크톱 분석의 보안 및 기능 업데이트에 대해 알아봅니다.
ms.date: 08/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 14ae894c-26fb-4fe3-b51d-e80700122df4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0cceaf6f4475a024b8f3375ef962a6dfc2dddc4d
ms.sourcegitcommit: e0d303d87c737811c2d3c40d01cd3d260a5c7bde
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69974777"
---
# <a name="updates-in-desktop-analytics"></a>데스크톱 분석의 업데이트

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석 포털에서 보안 및 기능 업데이트의 상태를 확인 합니다. 데스크톱 분석 주 메뉴의 모니터 그룹에서 이러한 노드를 선택 합니다. 이러한 노드는 사용자 환경에서 이러한 업데이트의 상태에 대 한 정보를 제공 합니다.


## <a name="security-updates"></a>보안 업데이트

보안 업데이트의 현재 상태를 검토 하려면 데스크톱 분석의 **모니터** 섹션에서 **보안 업데이트** 를 선택 합니다.

![데스크톱 분석의 보안 업데이트 노드](media/security-updates.png)

이 보기에는 Windows 10을 실행 하는 장치에 대 한 *보안* 업데이트가 요약 되어 있습니다. 가로 막대형 차트의 장치는 다음 레이블로 분류 됩니다.

#### <a name="latest"></a>최신 버전

장치에서 해당 버전 및 채널에 대 한 최신 보안 업데이트를 실행 하 고 있습니다.

#### <a name="latest-1"></a>최신-1

장치가 해당 채널에서 사용 가능한 최신 업데이트 보다 이전 버전의 보안 업데이트를 실행 하 고 있습니다.

#### <a name="older"></a>아닌

장치에서 최신-1 이전의 보안 업데이트를 실행 하 고 있습니다.

#### <a name="not-measured"></a>측정 안 됨

데스크톱 분석에서 장치를 평가 하지 않았습니다. 이 상태에는 windows 7, Windows 8.1 또는 windows Insider Program에 등록 된 windows 10 장치를 실행 하는 장치가 포함 됩니다.  

Windows 10 장치가 Microsoft 계정으로 *인증 되지 않은* 경우 windows는이 데이터를 보고 하지 않습니다. 이 인증은 일반적으로 Windows 설치 프로그램 OOBE (기본 제공 환경)의 일부로 완료 됩니다.<!-- 5148153 -->


## <a name="feature-updates"></a>기능 업데이트

기능 업데이트의 현재 상태를 검토 하려면 데스크톱 분석의 **모니터** 섹션에서 **기능 업데이트** 를 선택 합니다.

![데스크톱 분석의 기능 업데이트 노드](media/feature-updates.png)

이 보기에서는 Windows 10을 실행 하는 장치에 대 한 *기능* 업데이트를 요약 합니다.

서비스 기간에 대 한 자세한 내용은 [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조 하십시오.  

가로 막대형 차트의 장치는 다음 레이블로 분류 됩니다.

#### <a name="in-service"></a>서비스에서

장치에서 해당 버전 및 채널에 대 한 최신 기능 업데이트를 실행 하 고 있습니다.  

#### <a name="near-end-of-service"></a>서비스 끝 근처

장치에서 서비스의 끝에 도달 하는 90 일 이내에 기능 업데이트를 실행 하 고 있습니다.

#### <a name="end-of-service"></a>서비스 종료

장치에서 서비스 종료 날짜가 지난 기능 업데이트를 실행 하 고 있습니다. 서비스 종료 날짜에 대 한 자세한 내용은 [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조 하십시오.

#### <a name="not-measured"></a>측정 안 됨

데스크톱 분석에서 장치를 평가 하지 않았습니다. 이 상태에는 windows 7, Windows 8.1 또는 windows Insider Program에 등록 된 windows 10 장치를 실행 하는 장치가 포함 됩니다.

Windows 10 장치가 Microsoft 계정으로 *인증 되지 않은* 경우 windows는이 데이터를 보고 하지 않습니다. 이 인증은 일반적으로 Windows 설치 프로그램 OOBE (기본 제공 환경)의 일부로 완료 됩니다.<!-- 5148153 -->


## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 자산에 대 한 자세한 정보](/sccm/desktop-analytics/about-assets): 장치, 드라이버 및 앱  

- [배포 계획에 대 한 자세한 정보](/sccm/desktop-analytics/about-deployment-plans)  
