---
title: 사용자 지정 작업 순서 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 사용자 지정 작업 순서를 편집하여 작업 순서에 단계를 추가합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b9800a66-7541-47ca-8276-da8ef6cb6d1b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0058c78f9e2eb3546b570d65f8c7c90e283935d0
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74659648"
---
# <a name="create-a-custom-task-sequence-with-configuration-manager"></a>Configuration Manager를 사용하여 사용자 지정 작업 순서 만들기

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager에서 사용자 지정 작업 순서를 만들 때는 작업 순서 단계가 포함되지 않습니다. 작업 순서를 만든 후에 편집하고 필요한 작업 순서 단계를 추가합니다.  

## <a name="BKMK_CustomTS"></a> 사용자 지정 작업 순서 만들기

사용자 지정 작업 순서를 만들려면 다음 절차를 사용합니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장하고 **작업 순서** 노드를 선택합니다.  

1. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **작업 순서 만들기**를 선택합니다. 이 작업은 작업 순서 만들기 마법사를 시작합니다.  

1. **새 작업 순서 만들기** 페이지에서 **새 사용자 지정 작업 순서 만들기**를 선택합니다.  

1. **작업 순서 정보** 페이지에서 다음을 지정 합니다.

    - 작업 순서의 이름입니다.
    - 작업 순서에 대한 설명입니다.
    - 사용할 작업 순서에 대 한 부팅 이미지 (옵션)

작업 순서 만들기 마법사를 완료하면 Configuration Manager에서 사용자 지정 작업 순서를 **작업 순서** 노드에 추가합니다. 이제 이 작업 순서를 편집하여 작업 순서 단계를 추가할 수 있습니다.  

사용 가능한 작업 순서 단계 목록을 보려면 [작업 순서 단계](/sccm/osd/understand/task-sequence-steps)를 참조하세요.  

작업 순서를 편집하는 방법에 대한 자세한 내용은 [작업 순서 편집기 사용](/sccm/osd/understand/task-sequence-editor)을 참조하세요.  

작업 순서를 사용 하 여 OS 배포에 대 한 작업을 자동화 하는 것이 가장 일반적 이지만 사용자 지정 작업 순서를 만들어 다양 한 종류의 작업을 자동화할 수 있습니다. 자세한 내용은 [비 OS 배포에 대한 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments)를 참조하세요.  

## <a name="next-steps"></a>다음 단계

[작업 순서 배포](/sccm/osd/deploy-use/deploy-a-task-sequence)
