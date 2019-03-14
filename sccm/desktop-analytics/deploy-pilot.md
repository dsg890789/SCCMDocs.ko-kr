---
title: 파일럿 배포 하는 방법
titleSuffix: Configuration Manager
description: 데스크톱 분석 파일럿 그룹에 배포 하기 위한 방법 가이드입니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 637fbd8e-b8ea-4c7e-95ee-a60a323c496e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 797b8ab61f5be2fd851e735c475ed610ed7d3cfe
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755168"
---
# <a name="how-to-deploy-to-pilot-with-desktop-analytics"></a>데스크톱 분석으로 파일럿 배포 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

가장 작은 요소 중 가장 넓은 범위를 제공 하는 장치 집합을 식별할 수 있도록 방법은 데스크톱 분석의 이점 중 하나입니다. Windows 및 Office를 업그레이드 및 업데이트의 파일럿을 가장 중요 한 요소에 중점을 둡니다. 더 성공적인 파일럿이 있도록 더 빠르고 자신 있게 프로덕션 환경에서 광범위 한 배포를 이동할 수 있습니다.  

[!INCLUDE [Definition of pilot and production](includes/define-pilot-prod.md)]



## <a name="address-issues"></a>문제를 해결

배포를 차단할 수 있는 자산을 사용 하 여 보고 된 문제를 검토 하려면 데스크톱 분석 포털을 사용 합니다. 그런 다음 승인, 거부 또는 제안 된 수정 프로그램을 수정 합니다. 모든 항목이 표시 되어야 합니다 **준비** 또는 **준비가 완료 되었습니다 (재구성)** 파일럿 배포를 시작 하기 전에 합니다. 

1. 선택한 데스크톱 Analytics 포털로 이동 **배포 계획** 관리 그룹에 있습니다.  

2. 해당 이름을 선택 하 여 배포 계획을 엽니다.  

3. 선택 **준비 파일럿** 준비 그룹의 배포 계획 합니다.  

4. 에 **앱** 탭에서 입력을 필요로 하는 앱을 검토 합니다.  

5. 각 앱에 대 한 앱 이름을 선택 합니다. 정보 창에서 권장 사항 검토 하 고 업그레이드 의사 결정을 선택 합니다. 선택 하면 **를 검토 하지** 또는 **없습니다**, 데스크톱 분석 파일럿 배포에서이 앱을 사용 하 여 장치를 포함 하지 않습니다.  

6. 다른 자산에 대 한이 검토를 반복 합니다.  




## <a name="create-software"></a>소프트웨어 만들기

Windows 또는 Office를 배포 하기 전에 Configuration Manager에서 만드는 소프트웨어 개체 우선 합니다.

- [Office 365 ProPlus 응용 프로그램](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)  

- [Windows 10 현재 위치 업그레이드 작업 순서](https://docs.microsoft.com/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)



## <a name="deploy-to-pilot-devices"></a>파일럿 장치에 배포

Configuration Manager 데스크톱 Analytics에서 데이터를 사용 하 여 파일럿 배포를 위해 컬렉션을 만듭니다. 기존 배포를 사용 하 여 응용 프로그램 또는 작업 순서를 배포 하지 마세요. 데스크톱 Analytics 통합 배포를 만들려면 다음 절차를 사용 합니다.

1. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리**, 확장 **데스크톱 분석 서비스**, 선택는 **배포 계획** 노드.  

2. 배포 계획을 선택한 후 **배포 계획 세부 정보** 리본 메뉴에 있습니다.  

3. 에 **상태를 파일럿 실행** 타일, 드롭 다운 목록에서 다음 개체 형식 중 하나를 선택 합니다.  

    - **응용 프로그램** for Office 365 ProPlus  

    - **작업 순서** Windows 10 용  
  
   선택 **배포**합니다. 이 작업은 선택한 개체 형식에 대 한 소프트웨어 배포 마법사를 시작 합니다. 


자세한 내용은 다음 아티클을 참조하세요.  

- [응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy)  

- [작업 순서 배포](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS)  


배포 계획에 대 한 경우 Windows 10 및 Office 365에는 두 번째 배포를 만드는 데이 프로세스를 반복 합니다. 예를 들어, 첫 번째 배포 작업 순서에 대 한 경우에 응용 프로그램에 대 한 두 번째 배포를 만듭니다.



## <a name="monitor"></a>모니터

### <a name="configuration-manager-console"></a>Configuration Manager 콘솔

구성 관리자를 사용 하 여 배포 같은 다른 응용 프로그램 및 작업 순서 배포를 모니터링 합니다. 자세한 내용은 다음 아티클을 참조하세요.  

- [Configuration Manager 콘솔에서 응용 프로그램 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)  

- [모니터 OS 배포](/sccm/osd/deploy-use/monitor-operating-system-deployments)  


### <a name="desktop-analytics-portal"></a>데스크톱 Analytics 포털

배포 계획의 상태를 보려면 바탕 화면 분석 포털을 사용 합니다. 배포 계획을 선택 하 고 선택한 **계획 개요**합니다. 

![데스크톱 분석의 배포 계획 개요 스크린샷](media/deployment-plan-overview.png)

선택 된 **파일럿** 바둑판식으로 배열 합니다. 파일럿 배포의 현재 상태를 요약 합니다. 이 타일에는 진행 중, 완료 또는 문제를 반환, 시작 되지 않은 장치의 수에 대 한 데이터도 표시 됩니다.

오류 또는 기타 문제를 보고 하는 모든 장치의 오른쪽 파일럿 실행 세부 정보 영역에도 나열 됩니다. 선택에 보고 된 문제 세부 정보를 얻으려면 **검토**합니다. 이 작업에 뷰를 변경 합니다 **배포 상태** 페이지

합니다 **배포 상태** 페이지는 다음 범주에서 장치를 나열 합니다.

- 시작 안 됨
- 진행 중
- 완료
- 주의-장치
- 주의-문제

합니다 **주의가 필요한** 범주 다르게 정렬 되지만 같은 정보를 보여 줍니다.

검색 된 문제에 대 한 자세한 내용을 보려면 두 가지 뷰에서 특정 목록을 선택 합니다.

이러한 배포 문제를 해결 하는 대로 대시보드 계속 장치의 진행률을 표시 합니다. 장치에서 나가면서 업데이트 **주의 필요** 하 **완료**합니다.



## <a name="next-steps"></a>다음 단계

운영 데이터를 수집 하는 기간에 대 한 파일럿 실행을 사용 수 있습니다. 파일럿 장치의 사용자가 앱, 추가 기능 및 매크로 테스트 하는 것이 좋습니다. 

파일럿 배포 성공 조건을 만족 하는 경우 프로덕션에 배포 하려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]  
> [프로덕션 환경에 배포](/sccm/desktop-analytics/deploy-prod)  