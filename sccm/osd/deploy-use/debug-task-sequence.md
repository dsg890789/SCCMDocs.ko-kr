---
title: 작업 순서 디버그
titleSuffix: Configuration Manager
description: 작업 순서 디버깅 도구를 사용 하 여 작업 순서 문제를 해결할 수 있습니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 4b60b0e1-ffa4-4fd5-864e-70a0546c8b3b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fadcd362f44e5261ae5226ed22b7cff4c4eb261f
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537741"
---
# <a name="debug-a-task-sequence"></a>작업 순서 디버그

<!--3612274-->

버전 1906부터 작업 순서 디버거는 새로운 문제 해결 도구입니다. 디버그 모드에서 작은 컬렉션에 작업 순서를 배포 합니다. 이렇게 하면 제어되는 방식으로 작업 순서에 따라 문제 해결 및 조사를 지원할 수 있습니다. 디버거는 현재 작업 순서 엔진과 동일한 장치에서 실행 되며 원격 디버거가 아닙니다.

> [!Note]  
> 이 버전의 Configuration Manager에서 작업 순서 디버거는 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  


## <a name="prerequisites"></a>필수 구성 요소

- 대상 디바이스의 Configuration Manager 클라이언트를 업데이트합니다.

- 로컬 **관리자** 그룹의 사용자로 대상 장치에 로그인 합니다. 디버거는 관리자에 대해서만 실행 됩니다.

- 작업 순서와 연결된 부트 이미지를 업데이트하여 최신 클라이언트 버전을 갖추도록 합니다.


## <a name="start-the-tool"></a>도구 시작

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.

1. 작업 순서를 선택합니다. 리본 메뉴의 배포 그룹에서 **디버그**를 선택합니다.

    > [!Tip]  
    > 또는 작업 순서가 배포되는 컬렉션에서 **TSDebugMode** 변수를 `TRUE`로 설정합니다. 이 변수는 해당 컬렉션의 모든 디바이스에서 모든 작업 순서의 동작을 변경합니다.  

1. 디버그 배포를 만듭니다. 배포 설정은 일반적인 작업 순서 배포와 동일 합니다. 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/deploy-a-task-sequence#process)항목을 참조하세요.

    > [!Note]  
    > 디버그 배포에 대 한 작은 컬렉션을 선택할 수 있습니다. 구성원이 10 개 이하인 장치 컬렉션만 표시 됩니다.


## <a name="use-the-tool"></a>도구 사용

작업 순서가 디바이스에서 실행될 때 다음 스크린샷과 비슷한 작업 순서 디버거 창이 열립니다.

![작업 순서 디버거 스크린샷](media/3612274-tsdebug.png)

디버거에는 다음 컨트롤이 포함되어 있습니다.

- **단계**: *현재* 위치에서 작업 순서에서 다음 단계만 실행합니다.  

    > [!Note]  
    > 작업 순서가 디버그 모드에 있을 때 단계가 심각한 오류를 반환 하면 작업 순서가 정상적으로 실패 하지 않습니다. 이 동작은 외부 변경을 수행한 후 단계를 다시 시도 하는 옵션을 제공 합니다.

- **실행**: *현재* 위치에서 작업 순서를 일반적으로 마지막에 또는 단계가 실패한 경우, 다음 *중단* 지점에서 실행합니다. 이 작업을 사용 하기 전에 **중단 동작 설정** 을 사용 하 여 중단점을 설정 해야 합니다.

- **현재 설정**: 디버거에서 단계를 선택하고 **현재 설정**을 선택합니다. 이 작업은 *현재* 해당 포인터를 해당 단계로 이동합니다. 이 작업에서는 단계를 건너뛰거나 뒤로 이동할 수 있습니다.  

    > [!Warning]  
    > 순서에서 현재 위치를 변경할 때 디버거는 단계 형식을 고려하지 않습니다. 일부 단계는 이후 단계에서 조건 평가에 필요한 작업 순서 변수를 설정할 수 있습니다. 순서에 따라 실행되지 않으면 일부 단계는 실패하거나, 디바이스에 중대한 손상을 초래할 수 있습니다. 이 옵션의 사용 결과는 사용자의 책임입니다.  

- **중단 설정**: 디버거에서 단계를 선택하고 **중단 설정**을 선택합니다. 이 작업은 디버거에 *중단* 지점을 추가합니다. 작업 순서를 **실행**할 때 *중단*에서 멈춥니다.  

    - **실행** 작업을 사용 하기 전에 중단점을 설정 합니다.

    - 컴퓨터 [다시 시작](/sccm/osd/understand/task-sequence-steps#BKMK_RestartComputer) 단계와 같이 컴퓨터를 다시 시작한 후에는 중단 지점이 저장 되지 않습니다. 예를 들어 이미징 작업 순서에 대해 소프트웨어 센터에서 디버거를 시작 하는 경우 Windows PE 단계에서 중단을 설정 하지 마세요. 컴퓨터가 Windows PE로 다시 시작 되 면 디버거는 중단을 설정할 수 있도록 작업 순서를 일시 중지 합니다.

- **모든 중단 지우기**: 모든 중단점을 제거 합니다.

- **로그 파일**: [cmtrace](/sccm/core/support/cmtrace)를 사용 하 여 현재 작업 순서 로그 파일인 **smsts .log**를 엽니다. 작업 순서 엔진이 "디버거를 기다리는 중" 인 경우 로그 항목을 볼 수 있습니다.

- **Cmd prompt**: Windows PE에서 명령 프롬프트를 엽니다.

- **취소**: 디버거를 닫고 작업 순서를 실패 합니다.

- **끝내기**: 디버거를 분리 하 고 닫아도 작업 순서는 정상적으로 계속 실행 됩니다.

작업 **순서 변수** 창에는 작업 순서 환경의 모든 변수에 대 한 현재 값이 표시 됩니다. 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables)\(작업 순서 변수\)를 참조하세요. **이 값을 표시 하지**않는 옵션을 사용 하 여 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계를 사용 하는 경우 디버거에 변수 값이 표시 되지 않습니다. 디버거에서 변수 값을 편집할 수 없습니다.

> [!Note]
> 일부 작업 순서 변수는 내부 에서만 사용 되며 참조 설명서에는 나와 있지 않습니다.

작업 순서 디버거는 [컴퓨터를 다시 시작한](/sccm/osd/understand/task-sequence-steps#BKMK_RestartComputer) 후에도 계속 실행 되지만 중단점을 다시 만들어야 합니다. 작업 순서에는이 작업이 필요 하지 않을 수 있지만 디버거에서 사용자 조작이 필요 하므로 계속 하려면 Windows에 로그인 해야 합니다. 한 시간 후에 로그인 하지 않고 디버깅을 계속 진행 하면 작업 순서가 실패 합니다.

또한 [작업 순서 실행](/sccm/osd/understand/task-sequence-steps#child-task-sequence) 단계를 사용 하 여 자식 작업 순서를 한 단계씩 실행 합니다. 디버거 창에는 주 작업 순서와 함께 자식 작업 순서의 단계가 표시 됩니다.


## <a name="known-issues"></a>알려진 문제

여러 배포를 통해 동일한 장치에 대 한 일반 배포와 디버그 배포를 모두 대상으로 하는 경우 작업 순서 디버거가 시작 되지 않을 수 있습니다.


## <a name="see-also"></a>참고 항목

- [작업 순서 단계 정보](/sccm/osd/understand/task-sequence-steps)
- [작업 순서 변수](/sccm/osd/understand/task-sequence-variables)
- [작업 순서 변수 사용 방법](/sccm/osd/understand/using-task-sequence-variables)
- [작업 순서 배포](/sccm/osd/deploy-use/deploy-a-task-sequence)
