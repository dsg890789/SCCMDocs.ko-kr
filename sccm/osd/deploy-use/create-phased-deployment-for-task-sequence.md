---
title: 작업 순서에 대한 단계적 배포 만들기
titleSuffix: Configuration Manager
description: 작업 순서에 대한 단계적 배포 만들기
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b634ff68-b909-48d2-9e2c-0933486673c5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2bda41cfd01e5ef90771350e650f68a27c3af6ed
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32348636"
---
# <a name="create-phased-deployments-for-a-task-sequence-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 작업 순서에 대한 단계적 배포 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

단계적 배포는 여러 컬렉션에서 작업 순서가 조정된 순차적 출시를 자동화합니다. 기본적으로 두 단계의 단계적 배포를 만들거나 여러 단계를 수동으로 구성할 수 있습니다. 작업 순서의 단계적 배포는 PXE 또는 미디어 설치를 지원하지 않습니다. 

>[!NOTE]
> 단계적 배포는 Configuration Manager 1802에 도입된 시험판 기능입니다. <!--1356837-->

## <a name="security-scope-and-log-file-information"></a>보안 범위 및 로그 파일 정보

**보안 범위**:</br>
**모든** 보안 범위를 갖지 않는 모든 사용자는 단계적 배포에서 만든 배포를 볼 수 없습니다.

**로그 파일**: </br>
SMS_PhasedDeployment.log

## <a name="create-a-default-two-phased-deployment-for-a-task-sequence"></a>작업 순서에 대한 두 단계의 단계적 배포 만들기

다음 지침을 사용하여 단계적 배포를 만듭니다. 

1. **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.

2. 기존 작업 순서를 마우스 오른쪽 버튼으로 클릭하고 **단계별 배포 만들기**를 선택합니다. 

3. **일반** 탭에서 단계별 배포에 이름을 지정하고 설명(선택 사항)을 입력한 다음, **자동으로 기본 두 단계 배포 만들기**를 선택합니다. 

4. **첫 번째 컬렉션** 및 **두 번째 컬렉션** 필드를 채웁니다. **다음**을 선택합니다.

5. **설정** 탭에서 각 일정 설정에 대해 하나의 옵션을 선택하고 완료되면 **다음**을 선택합니다. 
    - **첫 번째 단계의 성공에 대한 조건입니다.** 
        - **배포 성공 백분율** - 단계 성공 조건에 대해 배포를 성공적으로 완료한 장치의 백분율을 지정합니다. 
    - **첫 번째 단계에 성공한 후에 배포의 두 번째 단계를 시작하는 조건**(하나 선택):
        - **지연 기간(일) 후에 이 단계를 자동으로 시작** - 첫 번째 단계 성공 후에 두 번째 단계를 시작하기 전에 대기할 기간(일)을 선택합니다. 
        - **배포의 두 번째 단계 수동으로 시작** - 첫 번째 단계를 성공한 후에 두 번째 단계를 자동으로 시작하지 않습니다. 수동으로 시작해야 합니다. 
    - **장치를 대상으로 지정하면 소프트웨어 설치**(하나 선택):
        - **가능하면 빨리** - 장치를 대상으로 지정하고 나서 가능한 빨리 장치에서 설치의 최종 기한을 설정합니다.
        - **최종 기한 시간(장치를 대상으로 지정한 시간과 관련)** - 장치를 대상으로 지정하고 나서 특정 기간(일)을 설치의 최종 기한으로 설정합니다. 

6. **단계** 탭에서 첫 번째 단계를 클릭한 다음, **편집**을 클릭합니다.  **사용자 알림** 및 **Windows Embedded 장치를 처리하는 필터 쓰기** 등 **사용자 환경**을 지정합니다. **적용**을 클릭합니다.

7. **배포 지점** 탭에서 단계에 대한 **배포 지점** 설정을 지정합니다. **적용** 및 **확인**을 클릭합니다.        

8. **단계** 탭에서 **사용자 환경** 및 **배포 지점**에 대한 두 번째 단계를 편집합니다. **적용** 및 **확인**을 클릭합니다.

9. **요약** 탭에서 선택 영역을 확인한 다음, **다음**을 클릭하여 마법사를 진행합니다.

>[!WARNING]
>단계적 배포는 작업 순서 배포가 [위험 수준이 높은](/sccm/protect/understand/settings-to-manage-high-risk-deployments.md) 경우 알리지 않습니다. 


## <a name="suspend-and-resume-phases-or-move-to-the-next-phase"></a>단계 일시 중단 및 다시 시작 또는 다음 단계로 이동
경우에 따라 수동으로 단계적 배포를 일시 중단하고, 일시 중단된 단계적 배포를 다시 시작하거나 다음 단계로 이동해야 합니다. 

### <a name="move-to-the-next-phase"></a>다음 단계로 이동
**배포의 두 번째 단계 수동으로 시작** 설정을 선택하면 두 번째 단계를 시작해야 합니다. 다음 지침을 따라 두 번째 단계로 이동합니다. 

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 선택하고, **운영 체제**를 확장하고, **작업 순서**를 클릭합니다.
2. 작업 순서를 강조 표시합니다.
3. 콘솔의 아래쪽에 있는 **단계적 배포** 탭을 클릭합니다. 
4. 단계적 배포를 마우스 오른쪽 단추로 클릭하고 **다음 단계로 이동**을 선택합니다.
![일시 중단, 다시 시작 또는 다음 단계로 이동](media/Suspend-phased-deployment.PNG)

### <a name="suspend-or-resume-a-phased-deployment"></a>단계적 배포 일시 중단 또는 다시 시작
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 선택하고, **운영 체제**를 확장하고, **작업 순서**를 클릭합니다.
2. 작업 순서를 강조 표시하고 콘솔의 아래쪽에 있는 **단계적 배포** 탭을 클릭합니다. 
3. 단계적 배포를 선택하고 리본 메뉴에서 **일시 중단** 또는 **다시 시작**을 클릭합니다.

## <a name="next-steps"></a>다음 단계
[사용자 지정 작업 순서 만들기](create-a-custom-task-sequence.md) </br>
[비운영 체제 배포에 대한 작업 순서 만들기](create-a-task-sequence-for-non-operating-system-deployments.md) 








