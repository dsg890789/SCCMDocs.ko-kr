---
title: 배포 계획을 만드는 방법
titleSuffix: Configuration Manager
description: 데스크톱 분석에서 배포 계획을 만드는 방법에 대 한 지침입니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8e0e8496-136b-461f-8239-cc19c6b78c3b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03befc6758d70acd93f1d884b9f29ca01483fe01
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72386534"
---
# <a name="how-to-create-deployment-plans-in-desktop-analytics"></a>데스크톱 분석에서 배포 계획을 만드는 방법

이 문서에서는 데스크톱 분석에서 배포 계획을 만드는 단계를 제공 합니다. 시작 하기 전에 먼저 [배포 계획에 대해 알아봅니다](/sccm/desktop-analytics/about-deployment-plans).

## <a name="create-a-plan-for-windows-10"></a>Windows 10 용 계획 만들기

이 섹션의 단계에 따라 데스크톱 분석을 사용 하 여 Windows 10 배포 계획을 만듭니다.

1. [데스크톱 분석 포털](https://aka.ms/desktopanalytics)을 엽니다. 적어도 **작업 영역 참가자** 권한이 있는 자격 증명을 사용 합니다.  

2. 관리 그룹에서 **배포 계획** 을 선택 합니다.  

3. **배포 계획** 창에서 **만들기**를 선택 합니다.  

4. **배포 계획 만들기** 창에서 다음 설정을 구성 합니다.  

    - **이름**: 배포 계획에 대 한 고유한 이름입니다.  

    - **제품 및 버전**: 배포할 Windows 10 버전을 선택 합니다. 최신 버전을 사용 하는 배포 계획을 만드는 것이 좋습니다.  

    - **장치 그룹**: 그룹을 하나 이상 선택한 다음 **대상 그룹으로 설정**을 선택 합니다. 원본으로 사용 되는 **SCCM** 의 그룹은 Configuration Manager에서 동기화 되는 컬렉션입니다.  

    - **준비 규칙**: 이러한 규칙은 업그레이드할 수 있는 장치를 확인 하는 데 도움이 됩니다. 자세한 내용은 [준비 규칙](#readiness-rules)을 참조 하세요.  

    - **완료 날짜**: 모든 대상 장치에 Windows를 완전히 배포 해야 하는 날짜를 선택 합니다.  

5. **만들기**를 선택합니다. 새 계획은 처리 중인 배포 계획 목록에 표시 됩니다. 신속한 처리를 위해 요청 시 데이터 새로 고침을 요청 합니다. 자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq##can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조 하세요.  

6. 이름을 선택 하 여 배포 계획을 엽니다.  

7. 배포 계획 메뉴의 **준비** 그룹에서 **중요도 식별**을 선택 합니다.  

    1. **앱** 탭에서 **검토 되지 않은** 자산만 표시 하도록 선택 합니다.  

    2. 각 앱을 선택 하 고 **편집**을 선택 합니다. 동시에 둘 이상의 앱을 편집 하도록 선택할 수 있습니다.  

    3. **중요도** 목록에서 중요도 수준을 선택 합니다. 파일럿 중에 데스크톱 분석을 통해 앱의 유효성을 검사 하려면 **위험** 또는 **중요**를 선택 합니다. **중요 하지 않은**것으로 표시 된 앱은 유효성을 검사 하지 않습니다. 중요도 수준을 할당할 때 [호환성](/sccm/desktop-analytics/compat-assessment) 및 기타 계획 정보를 평가 합니다.  

        중요도 수준을 할당할 때 업그레이드 결정을 선택할 수도 있습니다.  

    4. 완료 되 면 **저장** 을 선택 합니다.  

8. 배포 계획 메뉴의 **준비** 그룹에서 **파일럿 식별**을 선택 합니다.  

    1. 파일럿에 권장 되는 장치를 검토 합니다.  

    2. 각 장치를 선택 하 고 **파일럿에 추가를**선택 합니다. 권장 사항에 동의 하지 않는 경우 **바꾸기**를 선택 합니다.  

        데스크톱 분석에서 이러한 권장 사항을 적용 하는 방법에 대 한 자세한 내용은 **파일럿 식별** 창의 오른쪽 위 모퉁이에 있는 정보 아이콘을 선택 합니다.

## <a name="readiness-rules"></a>준비 규칙

이러한 규칙을 통해 전체 업그레이드에 적합 한 장치를 확인할 수 있습니다. 이러한 규칙은 배포 계획을 만들 때 설정 하거나 나중에 편집할 수 있습니다.

준비 규칙을 변경 하려면:

1. 데스크톱 분석 포털에서 배포 계획을 선택 합니다.
1. 이름 옆에 있는 **편집**을 선택 합니다.
1. **준비 규칙**을 선택 합니다.
1. **WINDOWS OS**를 선택 합니다.
1. 필요에 따라 변경 하 고 **저장**을 선택 합니다.

**WINDOWS OS** 업그레이드의 경우 장치 드라이버 및 Windows 응용 프로그램의 두 가지 규칙을 사용할 수 있습니다.

### <a name="device-drivers"></a>디바이스 드라이버

장치가 Windows 업데이트에서 드라이버를 가져올 것인지 여부를 구성 합니다. 이 값은 기본적으로 **해제** 되어 있습니다. 비즈니스 Windows 업데이트를 사용 하 여 드라이버를 비롯 한 업데이트를 관리 하는 경우이 규칙을 사용 하도록 설정 합니다. Configuration Manager를 사용 하 여 소프트웨어 업데이트를 관리 하는 경우이 규칙을 **해제**로 설정 합니다.

### <a name="windows-applications"></a>Windows 응용 프로그램

데스크톱 분석에서 *주목할 만한* 것으로 표시 되는 앱은 낮은 설치 수 임계값을 기반으로 합니다. 배포 계획에 대 한 준비 규칙에서이 임계값을 설정 합니다. 기본적으로이 임계값은 **2.0%** 입니다. @No__t_0에서 `10.0`로 값을 변경할 수 있습니다.


## <a name="next-steps"></a>다음 단계

파일럿 장치에 배포 하려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]  
> [파일럿에 배포](/sccm/desktop-analytics/deploy-pilot)  
