---
title: 데스크톱 Analytics에서 업데이트
titleSuffix: Configuration Manager
description: 데스크톱 Analytics의 보안 및 기능 업데이트에 알아봅니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 14ae894c-26fb-4fe3-b51d-e80700122df4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: a10a7b5bbb3a1b7d0dada86774f3412e22faff01
ms.sourcegitcommit: 6f4c2987debfba5d02ee67f6b461c1a988a3e201
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59673550"
---
# <a name="updates-in-desktop-analytics"></a>데스크톱 Analytics에서 업데이트 

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 Analytics 포털에서 보안 및 기능 업데이트 상태를 봅니다. 데스크톱 분석 주 메뉴의 모니터 그룹에 이러한 노드를 선택 합니다. 이러한 노드 환경에서 이러한 업데이트의 상태에 대 한 정보를 제공합니다. 



## <a name="security-updates"></a>보안 업데이트

보안 업데이트의 현재 상태를 검토 하려면 선택 **보안 업데이트** 에 **모니터** 데스크톱 분석의 섹션:

![보안 업데이트 노드의 데스크톱 분석](media/security-updates.png)

이 보기 요약 *보안* Windows 10 또는 Office 365 ProPlus를 실행 하는 장치에 대 한 업데이트 합니다. 가로 막대형 차트에는 장치는 다음과 같은 레이블으로 분류 됩니다.

#### <a name="latest"></a>최신 버전
장치는 버전 및 채널에 대 한 최신 보안 업데이트를 실행 하 고 있습니다.

#### <a name="latest-1"></a>최신-1
장치에는 해당 채널에서 보안 업데이트 이상의 버전을 사용 가능한 최신 업데이트로 보다 오래 실행 됩니다.

#### <a name="older"></a>이전
장치가 최신-1 보다 오래 된 보안 업데이트를 실행 합니다.

#### <a name="not-measured"></a>측정 되지 않습니다.
데스크톱 분석 되지 않은 장치를 평가 합니다. 

- Windows, Windows 참가자 프로그램에 대해 등록 된 Windows 7, Windows 8.1 또는 Windows 10 장치를 실행 하는 장치 포함  

- Office 용 다음 버전 중 하나를 사용 하 여 장치 포함 됩니다.  

    - Office 365 ProPlus의 경우 Insider 채널  

    - Windows installer를 사용 하는 Office의 정품 버전입니다. 예를 들어, Office 2016, Office 2013 또는 Office 2010.  

    - 보안 상태를 평가 하는 데 충분 한 데이터가 반환 되지 않은 장치에서 office 365 ProPlus  



## <a name="feature-updates"></a>기능 업데이트

기능 업데이트의 현재 상태를 검토 하려면 선택 **기능 업데이트** 에 **모니터** 데스크톱 분석의 섹션:

![기능 업데이트 노드의 데스크톱 분석](media/feature-updates.png)

이 보기 요약 *기능* Windows 10 또는 Office 365 ProPlus를 실행 하는 장치에 대 한 업데이트 합니다. 

서비스 기간에 대 한 자세한 내용은 다음 문서를 참조 하세요. 
- [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)  
- [Office 365 ProPlus의 업데이트 기록](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date)  

가로 막대형 차트에는 장치는 다음과 같은 레이블으로 분류 됩니다.

#### <a name="in-service"></a>서비스에서
장치는 버전 및 채널에 대 한 최신 기능 업데이트를 실행 하 고 있습니다.  

#### <a name="near-end-of-service"></a>서비스 수명이 끝
장치는 서비스의 끝에 도달한 후 90 일 내에 있는 기능 업데이트를 실행 하 고 있습니다.

#### <a name="end-of-service"></a>서비스의 끝
장치는 서비스 날짜의 끝을 지난 기능 업데이트를 실행 하 고 있습니다. 서비스 날짜는 종료에 대 한 세부 정보를 참조 하세요. [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)  <!-- {xlink into relevant section of UDR_monitoring}|-->

#### <a name="not-measured"></a>측정 되지 않습니다.
데스크톱 분석 되지 않은 장치를 평가 합니다. 

- Windows, Windows 참가자 프로그램에 대해 등록 된 Windows 7, Windows 8.1 또는 Windows 10 장치를 실행 하는 장치 포함

- Office 용 다음 버전 중 하나를 사용 하 여 장치 포함 됩니다.  

    - Office 365 ProPlus의 경우 Insider 채널  

    - Windows installer를 사용 하는 Office의 정품 버전입니다. 예를 들어, Office 2016, Office 2013 또는 Office 2010.  

    - 보안 상태를 평가 하는 데 충분 한 데이터가 반환 되지 않은 장치에서 office 365 ProPlus  



## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 자산에 대 한 알아봅니다](/sccm/desktop-analytics/about-assets): 장치, 앱, Office 앱, Office 추가 기능 및 Office 매크로  

- [배포 계획에 알아봅니다](/sccm/desktop-analytics/about-deployment-plans)  

