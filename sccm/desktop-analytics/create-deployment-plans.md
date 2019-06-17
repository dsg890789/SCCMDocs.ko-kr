---
title: 배포 계획을 만드는 방법
titleSuffix: Configuration Manager
description: 데스크톱 분석에서 배포 계획을 만들기 위한 방법 가이드입니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8e0e8496-136b-461f-8239-cc19c6b78c3b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc94bf46630e2770385b5efaffb431135e3667c7
ms.sourcegitcommit: d47d2f03482e48d343e2139a341e61022331e6c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67146038"
---
# <a name="how-to-create-deployment-plans-in-desktop-analytics"></a>데스크톱 분석에서 배포 계획을 만드는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

이 문서에서는 데스크톱 Analytics에서 배포 계획을 만드는 단계를 제공 합니다. 를 시작 하기 전에 먼저 [배포 계획에 알아봅니다](/sccm/desktop-analytics/about-deployment-plans)합니다.

## <a name="create-a-plan-for-windows-10"></a>Windows 10 용 계획 만들기

데스크톱 Analytics를 사용 하 여 Windows 10을 배포 하기 위한 계획을 만들려면이 섹션의 단계를 따릅니다.

1. 엽니다는 [데스크톱 Analytics 포털](https://aka.ms/desktopanalytics)합니다. 최소 권한이 있는 자격 증명을 사용 하 여 **작업 영역 참가자** 권한.  

2. 선택 **배포 계획** 관리 그룹에 있습니다.  

3. 에 **배포 계획** 창 **만들기**합니다.  

4. 에 **배포 계획 만들기** 창 다음 설정을 구성 합니다.  

    - **이름**: 배포 계획에 대 한 고유 이름  

    - **제품 및 버전**: 배포 하는 Windows 10 버전을 선택 합니다. 최신 버전을 사용 하는 배포 계획을 만드는 것이 좋습니다.  

    - **장치 그룹**: 하나 이상의 그룹을 선택 하 고 선택한 **대상 그룹으로 설정할**합니다. 그룹 **SCCM** 소스로 컬렉션 동기화 Configuration Manager에서 합니다.  

    - **준비 규칙**: 이러한 규칙은 장치 업그레이드에 대 한 정하는 결정 하는 데 도움이 됩니다. 자세한 내용은 [준비 규칙](#readiness-rules)합니다.  

    - **완료 날짜**: Windows 완벽 하 게 모든 대상된 장치에 배포할지 때 사용 되는 날짜를 선택 합니다.  

5. **만들기**를 선택합니다. 새 계획 처리 되 고 해당 하는 동안 배포 계획의 목록에 나타납니다. 처리를 신속 하 게 요청 시 데이터 새로 고침을 요청 합니다. 자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq##can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)합니다.  

6. 해당 이름을 선택 하 여 배포 계획을 엽니다.  

7. 배포 계획 메뉴에 **준비** 그룹에서 **중요도 식별**.  

    1. 에 **앱** 탭만 표시 하도록 선택 합니다 **를 검토 하지** 자산입니다.  

    2. 각 앱을 선택 하 고 선택한 **편집**합니다. 동시 편집 하려면 둘 이상의 앱을 선택할 수 있습니다.  

    3. 중요도 수준을 선택 합니다 **중요도** 목록입니다. 파일럿 기간 동안 앱 유효성을 검사 하려면 데스크톱 분석 선택 **Critical** 또는 **중요**합니다. 로 표시 되는 앱의 유효성을 검사 하지 않습니다 **중요 하지 않은**합니다. 평가 해당 [호환성](/sccm/desktop-analytics/compat-assessment) 및 중요도 수준을 할당할 때 다른 계획 정보입니다.  

        중요도 수준에 할당 하는 경우에 업그레이드 의사 결정을 선택할 수 있습니다.  

    4. 선택 **저장할** 완료 되 면 합니다.  

8. 배포 계획 메뉴에 **준비** 그룹에서 **식별 파일럿**.  

    1. 파일럿에 대 한 권장 되는 장치를 검토 합니다.  

    2. 각 장치를 선택 하 고 선택 **파일럿 추가할**합니다. 권장 사항을 사용 하 여 동의할 수 없는 경우 선택 **대체**합니다.  

        이러한 권장 사항은 데스크톱 분석을 사용 하는 방법에 대 한 자세한 내용은 오른쪽 위 모서리에서 정보 아이콘을 선택 합니다 **식별 파일럿** 창.

## <a name="readiness-rules"></a>준비 규칙

이러한 규칙에는 장치에서 전체 업그레이드에 대 한 정규화를 확인할 수 있습니다. 배포 계획을 만들거나 나중에 편집할 때 이러한 규칙을 설정할 수 있습니다.

준비 규칙의 이름을 바꾸려면:

1. 데스크톱 Analytics 포털에서 배포 계획을 선택 합니다.
1. 이름 옆에 있는 선택 **편집**합니다.
1. 선택 **준비 규칙**합니다.
1. 선택 **Windows OS**합니다.
1. 필요에 따라 변경 하 고 선택 **저장할**합니다.

에 대 한 **Windows OS** 업그레이드를 사용할 수 있는 두 개의 규칙이 있습니다. 장치 드라이버 및 Windows 응용 프로그램입니다.

### <a name="device-drivers"></a>디바이스 드라이버

장치가 Windows 업데이트에서 드라이버를 가져올 수 있는지 여부를 구성 합니다. 이 값은 **해제** 기본적으로 합니다. 드라이버를 포함 하 여 업데이트를 관리 하려면 비즈니스용 Windows 업데이트를 사용 하는 경우이 규칙을 사용 합니다. Configuration Manager 소프트웨어 업데이트 관리를 사용 하는 경우이 규칙 설정할 **해제**합니다.

### <a name="windows-applications"></a>Windows 응용 프로그램

데스크톱 Analytics로 표시 되는 앱 *주목할 만한* 낮은 설치 수 임계값을 기반으로 합니다. 배포 계획에 대 한 준비 규칙에서이 임계값을 설정 합니다. 이 임계값은 기본적으로 **2.0%** 합니다. 값을 변경할 수 있습니다 `0.0` 에 `10.0`입니다.


## <a name="next-steps"></a>다음 단계

파일럿 장치에 배포 하려면 다음 문서로 계속 진행 하세요.
> [!div class="nextstepaction"]  
> [파일럿 배포](/sccm/desktop-analytics/deploy-pilot)  
