---
title: 배포 계획을 만드는 방법
titleSuffix: Configuration Manager
description: Desktop Analytics에서 배포 계획을 만드는 방법에 대한 지침입니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8e0e8496-136b-461f-8239-cc19c6b78c3b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18bb8d2431e096969d193f32747249b6b84ed37f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791680"
---
# <a name="how-to-create-deployment-plans-in-desktop-analytics"></a>Desktop Analytics에서 배포 계획을 만드는 방법

이 문서에서는 Desktop Analytics에서 배포 계획을 만드는 단계를 제공합니다. 시작하기 전에 먼저 [배포 계획에 대해 알아봅니다](/sccm/desktop-analytics/about-deployment-plans).

## <a name="create-a-plan-for-windows-10"></a>Windows 10용 계획 만들기

이 섹션의 단계에 따라 Desktop Analytics를 사용하여 Windows 10 배포 계획을 만듭니다.

1. [Desktop Analytics 포털](https://aka.ms/desktopanalytics)을 엽니다. **작업 영역 기여자** 권한 이상의 자격 증명을 사용합니다.  

2. 관리 그룹에서 **배포 계획**을 선택합니다.  

3. **배포 계획** 창에서 **만들기**를 선택합니다.  

4. **배포 계획 만들기** 창에서 다음 설정을 구성합니다.  

    - **이름**: 배포 계획의 고유한 이름  

    - **제품 및 버전**: 배포할 Windows 10 버전을 선택합니다. 최신 버전을 사용하는 배포 계획을 만드는 것이 좋습니다.  

    - **디바이스 그룹**: 하나 이상의 그룹을 선택한 다음, **대상 그룹으로 설정**을 선택합니다. 원본으로 **SCCM**을 포함하는 그룹은 Configuration Manager에서 동기화된 컬렉션입니다.  

    - **준비 규칙**: 이러한 규칙은 업그레이드에 적합한 디바이스를 확인하는 데 도움이 됩니다. 자세한 내용은 [준비 규칙](#readiness-rules)을 참조하세요.  

    - **완료 날짜**: Windows를 모든 대상 디바이스에 완전히 배포해야 하는 날짜를 선택합니다.  

5. **만들기**를 선택합니다. 새 계획이 처리되는 동안 배포 계획 목록에 표시됩니다. 빠른 처리를 위해 요청 시 데이터 새로 고침을 요청합니다. 자세한 내용은 [Desktop Analytics FAQ](/sccm/desktop-analytics/faq##can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조하세요.  

6. 해당 이름을 선택하여 배포 계획을 엽니다.  

7. 배포 계획 메뉴의 **준비** 그룹에서 **중요도 식별**을 선택합니다.  

    1. **앱** 탭에서 **검토되지 않음** 자산만 표시하도록 선택합니다.  

    2. 각 앱을 선택한 다음, **편집**을 선택합니다. 둘 이상의 앱을 동시에 편집하도록 선택할 수 있습니다.  

    3. **중요도** 목록에서 중요도 수준을 선택합니다. 파일럿 중에 Desktop Analytics를 통해 앱의 유효성을 검사하려면 **위험** 또는 **중요**를 선택합니다. **중요하지 않음**으로 표시된 앱의 유효성은 검사하지 않습니다. 중요도 수준을 할당할 때 [호환성](/sccm/desktop-analytics/compat-assessment) 및 기타 계획 인사이트를 평가합니다.  

        중요도 수준을 할당할 때 [업그레이드] 결정을 선택할 수도 있습니다.  

    4. 완료되면 **저장**을 선택합니다.  

8. 배포 계획 메뉴의 **준비** 그룹에서 **파일럿 식별**을 선택합니다.  

    1. 파일럿에 추천되는 디바이스를 검토합니다.  

    2. 각 디바이스를 선택하고, **파일럿에 추가**를 선택합니다. 추천 사항에 동의하지 않으면 **바꾸기**를 선택합니다.  

        Desktop Analytics에서 이러한 권장 사항을 적용하는 방법에 대한 자세한 내용은 **파일럿 식별** 창의 오른쪽 위 모퉁이에 있는 정보 아이콘을 선택합니다.

## <a name="readiness-rules"></a>준비 규칙

이러한 규칙은 현재 위치 업그레이드에 적합한 디바이스를 확인하는 데 도움이 됩니다. 이러한 규칙은 배포 계획을 만들 때 설정하거나 나중에 편집할 수 있습니다.

준비 규칙을 변경하려면 다음을 수행합니다.

1. Desktop Analytics 포털에서 배포 계획을 선택합니다.
1. 이름 옆에 있는 **편집**을 선택합니다.
1. **준비 규칙**을 선택합니다.
1. **Windows OS**를 선택합니다.
1. 필요에 따라 변경하고, **저장**을 선택합니다.

**Windows OS** 업그레이드의 경우 두 가지 규칙을 사용할 수 있습니다. 디바이스 드라이버 및 Windows 애플리케이션

### <a name="device-drivers"></a>디바이스 드라이버

디바이스가 Windows 업데이트에서 드라이버를 가져올 것인지 여부를 구성합니다. 이 값은 기본적으로 **해제**입니다. 비즈니스용 Windows 업데이트를 사용하여 드라이버를 비롯한 업데이트를 관리하는 경우 이 규칙을 사용하도록 설정합니다. Configuration Manager를 사용하여 소프트웨어 업데이트를 관리하는 경우 이 규칙을 **해제**로 설정합니다.

### <a name="windows-applications"></a>Windows 애플리케이션

Desktop Analytics에서 *중요*로 표시하는 앱은 낮은 설치 수 임계값을 기반으로 합니다. 배포 계획에 대한 준비 규칙에서 이 임계값을 설정합니다. 기본적으로 이 임계값은 **2.0%** 입니다. `0.0`에서 `10.0`으로 값을 변경할 수 있습니다.


## <a name="next-steps"></a>다음 단계

파일럿 디바이스에 배포하려면 다음 문서로 이동합니다.
> [!div class="nextstepaction"]  
> [파일럿에 배포](/sccm/desktop-analytics/deploy-pilot)  
