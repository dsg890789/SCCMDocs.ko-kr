---
title: 배포 계획을 만드는 방법
titleSuffix: Configuration Manager
description: 데스크톱 분석에서 배포 계획을 만들기 위한 방법 가이드입니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8e0e8496-136b-461f-8239-cc19c6b78c3b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b56fac3060acc16fe46221464ddc6535b478399
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755285"
---
# <a name="how-to-create-deployment-plans-in-desktop-analytics"></a>데스크톱 분석에서 배포 계획을 만드는 방법 

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

이 문서에서는 데스크톱 Analytics에서 배포 계획을 만드는 단계를 제공 합니다. 를 시작 하기 전에 먼저 [배포 계획에 알아봅니다](/sccm/desktop-analytics/about-deployment-plans)합니다.

데스크톱 Analytics를 사용 하 여 Windows 10 및 Office 365 ProPlus를 배포 하기 위한 계획을 만들려면이 문서의 단계를 수행 합니다. Windows 10, Office 365 ProPlus 또는 둘 다에 대 한 배포 계획을 만듭니다.

1. 엽니다는 [데스크톱 Analytics 포털](https://aka.ms/m365aprod)합니다. 최소 권한이 있는 자격 증명을 사용 하 여 **작업 영역 참가자** 권한.  

2. 선택 **배포 계획** 관리 그룹에 있습니다.  

3. 에 **배포 계획** 창 **만들기**합니다.  

4. 에 **배포 계획 만들기** 창 다음 설정을 구성 합니다.  

    - **이름**: 배포 계획에 대 한 고유 이름  

    - **제품 및 버전**: 제품 및 배포 하는 버전을 선택 합니다. 함께 Office 및 Windows 용 배포 계획을 수립 하 고 최신 버전을 사용 하는 것이 좋습니다.  

    - **장치 그룹**: 하나 이상의 그룹을 선택 하 고 선택한 **대상 그룹으로 설정할**합니다. 그룹 **SCCM** 소스로 컬렉션 동기화 Configuration Manager에서 합니다.  

    - **준비 규칙**: 이러한 규칙은 장치 업그레이드에 대 한 정하는 결정 하는 데 도움이 됩니다. 

    - **완료 날짜**: Windows 및 Office 완벽 하 게 배포 해야 모든 대상된 장치에 날짜를 선택 합니다.  

5. **만들기**를 선택합니다. 새 계획 처리 되 고 해당 하는 동안 배포 계획의 목록에 나타납니다. 처리는 다음 단계를 진행 하기 전에 최대 48 시간이 걸릴 수 있습니다.   

6. 해당 이름을 선택 하 여 배포 계획을 엽니다.  

7. 배포 계획 메뉴에 **준비** 그룹에서 **중요도 식별**.  

    1. 에 **앱** 탭만 표시 하도록 선택 합니다 **를 검토 하지** 자산입니다.  

    2. 각 앱을 선택 하 고 선택한 **편집**합니다. 동시 편집 하려면 둘 이상의 앱을 선택할 수 있습니다.   

    3. 중요도 수준을 선택 합니다 **중요도** 목록입니다. 데스크톱 Analytics는 파일럿 기간 동안 추가 유효성 검사를 원한다 면 선택 **Critical** 또는 **중요**합니다. 추가 기능으로 표시의 유효성을 검사 하지 않습니다 **중요 하지 않은**합니다. 중요도 수준을 할당할 때 호환성 위험 및 기타 계획 정보를 고려 합니다.  

        중요도 수준에 할당 하는 경우에 업그레이드 의사 결정을 선택할 수 있습니다.  

    4. 선택 **저장할** 완료 되 면 합니다.  

    5. 이러한 단계를 반복 합니다 **Office 추가 기능**합니다.  

8. 배포 계획 메뉴에 **준비** 그룹에서 **식별 파일럿**.  

    1. 파일럿에 대 한 권장 되는 장치를 검토 합니다.  

    2. 각 장치를 선택 하 고 선택 **파일럿 추가할**합니다. 권장 사항을 사용 하 여 동의할 수 없는 경우 선택 **대체**합니다.  

        이러한 권장 사항은 데스크톱 분석을 사용 하는 방법에 대 한 자세한 내용은 오른쪽 위 모서리에서 정보 아이콘을 선택 합니다 **식별 파일럿** 창.



### <a name="next-steps"></a>다음 단계

파일럿 장치에 배포 하려면 다음 문서로 계속 진행 하세요.
> [!div class="nextstepaction"]  
> [파일럿 배포](/sccm/desktop-analytics/deploy-pilot)  
