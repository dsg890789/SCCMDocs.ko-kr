---
title: 데스크톱 분석의 자산
titleSuffix: Configuration Manager
description: 데스크톱 분석의 장치, 드라이버 및 앱에 대해 알아봅니다.
ms.date: 08/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d07198cf-49bb-4712-8c63-063b4302cc11
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b60326a746768e7045104a571d05a085ac0bd2a
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72387112"
---
# <a name="assets-in-desktop-analytics"></a>데스크톱 분석의 자산

장치에서 데스크톱 분석에 데이터를 보고 한 후에는 다음과 같은 자산에 대 한 인벤토리를 제공 합니다.

- 디바이스가
- 설치 된 앱  

서비스 포털의 데스크톱 분석 메뉴에서 **자산** 을 선택 합니다.


## <a name="devices"></a>디바이스가

**장치** 탭은 데스크톱 분석에 등록 하는 조직의 모든 장치에 대 한 주요 정보를 표시 합니다. 특정 값에 대해 열 또는 필터를 기준으로 정렬할 수 있습니다.

> [!NOTE]  
> 대시보드가 사용자 환경에 대해 표시 되는 장치 수를 보고 하지 않는 경우 [데스크톱 분석 문제 해결](/sccm/desktop-analytics/troubleshooting)을 참조 하세요.  

배포 계획에는 장치에 대 한 자세한 정보가 있습니다. 자세한 내용은 [자산 계획](/sccm/desktop-analytics/about-deployment-plans#plan-assets) 을 참조 하세요.

## <a name="apps"></a>App

**앱** 탭에는 서비스가 Windows 장치에서 검색 하는 설치 된 모든 앱이 표시 됩니다.

**중요** 한 앱은 2% 이상의 등록 된 장치에 설치 됩니다.

다음 범주 중 하나를 설정 하 여 앱의 **중요도** 를 구성 합니다.

- 중요
- 중요
- 무시 
- 검토 되지 않음
- 중요 하지 않음<!-- 3587232 -->


목록에서 앱을 선택 하 고 **편집**을 선택 합니다. 이 작업을 수행 하면 앱에 대 한 세부 정보가 표시 됩니다. **중요도** 드롭다운 메뉴를 선택 하 고 값을 설정 합니다. 또한 **소유자**를 할당할 수 있습니다. 변경을 수행 하는 경우 **저장**을 선택 합니다.

### <a name="a-namebkmk_plan-autoapp--automatic-upgrade-decision-of-system-and-store-apps"></a>시스템 및 스토어 앱의 자동 업그레이드 결정 <a name="bkmk_plan-autoapp" />

<!-- 3587232 -->
데스크톱 분석 워크플로에서 중요 한 모든 앱에 대해 **중요도** 와 **업그레이드 결정** 을 확인 하는 것이 중요 합니다. 이러한 앱에 주석을 추가 하는 데 도움을 줄 수 있도록 특정 유형의 앱은 자동으로 *중요 하지 않은*것으로 표시 됩니다. 이러한 앱에 대 한 배포 계획 업그레이드 결정도 *준비*로 표시 됩니다. 다음 앱은 호환 되며 Windows를 업그레이드 한 후에도 계속 작동 해야 합니다.

- Microsoft에서 게시 한 시스템 앱 및 구성 요소

- Microsoft Store에서 관리 및 업데이트 된 앱

> [!Tip]
> 전역 수준 또는 배포 계획에 따라 모든 앱에 대 한 입력을 관리 합니다. 
>
> 1. 데스크톱 분석 포털의 **관리** 메뉴에서 **자산**을 선택 합니다. 그런 다음 **앱**을 선택 합니다.
>
> 2. **유형** 및 **범주** 열을 사용 하 여 이러한 앱 범주를 관리 합니다.
>
>    - 스토어 앱의 경우 **형식** 을 **최신** 으로 필터링 합니다.
>    - 시스템 앱의 경우 **범주** 를 **백그라운드 프로세스** 또는 **Windows 구성 요소로** 필터링 합니다.



배포 계획에서 **업그레이드 결정**을 설정할 수도 있습니다. 자세한 내용은 [자산 계획](/sccm/desktop-analytics/about-deployment-plans#plan-assets) 을 참조 하세요.




## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 배포 계획에 대 한 자세한 정보](/sccm/desktop-analytics/about-deployment-plans)  

- [보안 및 기능 업데이트에 대 한 자세한 정보](/sccm/desktop-analytics/about-updates)  

- [데스크톱 분석의 호환성 평가](/sccm/desktop-analytics/compat-assessment)  
