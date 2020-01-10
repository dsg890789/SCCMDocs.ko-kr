---
title: Desktop Analytics의 자산
titleSuffix: Configuration Manager
description: Desktop Analytics의 디바이스, 드라이버 및 앱에 대해 알아봅니다.
ms.date: 08/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d07198cf-49bb-4712-8c63-063b4302cc11
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e5d2ca6139783ba6fbb362434dcbd7b9b6878d3e
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825713"
---
# <a name="assets-in-desktop-analytics"></a>Desktop Analytics의 자산

디바이스가 Desktop Analytics에 데이터를 보고한 후 다음 자산의 인벤토리를 제공합니다.

- 디바이스
- 설치된 앱  

서비스 포털의 Desktop Analytics 메뉴에서 **자산**을 선택합니다.


## <a name="devices"></a>디바이스

**디바이스** 탭에는 Desktop Analytics에 등록하는 조직의 모든 디바이스에 대한 주요 정보가 표시됩니다. 특정 값에 대한 열 또는 필터를 기준으로 정렬할 수 있습니다.

> [!NOTE]  
> 대시보드가 사용자 환경에 표시되는 디바이스 수를 보고하지 않는 경우 [Desktop Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)을 참조하세요.  

배포 계획에는 디바이스에 대한 자세한 정보가 있습니다. 자세한 내용은 [계획 자산](/sccm/desktop-analytics/about-deployment-plans#plan-assets)을 참조하세요.

## <a name="apps"></a>앱

**Apps** 탭에는 서비스가 Windows 디바이스에서 검색하는 설치된 모든 앱이 표시됩니다.

**중요** 앱은 2%를 초과하는 등록된 디바이스에 설치됩니다.

다음 범주 중 하나를 설정하여 앱의 **중요도**를 구성합니다.

- 중요
- 중요
- 무시 
- 검토되지 않음
- 중요하지 않음<!-- 3587232 -->


목록에서 앱을 선택하고 **편집**을 선택합니다. 이 작업은 앱의 세부 정보를 표시합니다. **중요도** 드롭다운 메뉴를 선택하고 값을 설정합니다. **소유자**를 할당할 수도 있습니다. 변경한 경우 **저장**을 선택합니다.

### <a name="a-namebkmk_plan-autoapp--automatic-upgrade-decision-of-system-and-store-apps"></a><a name="bkmk_plan-autoapp" /> 시스템 및 스토어 앱의 자동 업그레이드 결정

<!-- 3587232 -->
데스크톱 분석 워크플로의 모든 중요한 앱에 **중요도** 및 **업그레이드 결정**을 식별하는 것이 중요합니다. 이러한 앱에 주석을 추가하는 작업을 줄이기 위해 특정 유형의 앱은 자동으로 *중요하지 않음*으로 표시됩니다. 이러한 앱에 대한 배포 계획 업그레이드 결정도 *준비*로 표시됩니다. 다음 앱은 호환되며 Windows를 업그레이드한 후에도 계속 작동해야 합니다.

- Microsoft에서 게시한 시스템 앱 및 구성 요소

- Microsoft Store에서 관리 및 업데이트된 앱

> [!Tip]
> 글로벌 수준 또는 배포 계획에 따라 모든 앱의 입력을 관리합니다. 
>
> 1. Desktop Analytics 포털의 **관리** 메뉴에서 **자산**을 선택합니다. 그런 다음, **앱**을 선택합니다.
>
> 2. **형식** 및 **범주** 열을 사용하여 다음 앱 범주를 관리합니다.
>
>    - 스토어 앱의 경우 **형식**을 **최신**으로 필터링합니다.
>    - 시스템 앱의 경우 **범주**를 **백그라운드 프로세스** 또는 **Windows 구성 요소**로 필터링합니다.



배포 계획에서 **업그레이드 결정**을 설정할 수도 있습니다. 자세한 내용은 [계획 자산](/sccm/desktop-analytics/about-deployment-plans#plan-assets)을 참조하세요.




## <a name="next-steps"></a>다음 단계

- [Desktop Analytics 배포 계획에 대한 자세한 정보](/sccm/desktop-analytics/about-deployment-plans)  

- [보안 및 기능 업데이트에 대한 자세한 정보](/sccm/desktop-analytics/about-updates)  

- [Desktop Analytics의 호환성 평가](/sccm/desktop-analytics/compat-assessment)  
