---
title: Updates Publisher
titleSuffix: Configuration Manager
description: System Center Updates Publisher를 사용하여 사용자 지정 업데이트 관리
ms.date: 6/17/2019
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26ad3be032a3dd8ea21d7eeb6a4755c32d546f38
ms.sourcegitcommit: 659976b943226c5124057429ac7444989f98433f
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67158666"
---
# <a name="system-center-updates-publisher"></a>System Center Updates Publisher

*적용 대상: System Center Updates Publisher*

System Center Updates Publisher(Updates Publisher)는 독립 소프트웨어 공급업체 또는 LOB(기간 업무) 애플리케이션 개발자가 사용자 지정 업데이트를 관리할 수 있도록 하는 독립 실행형 도구입니다. 이 사용자 지정 업데이트 관리에는 드라이버 및 업데이트 번들과 같은 종속성이 있는 업데이트가 포함 됩니다.

Updates Publisher를 사용하여 다음을 수행할 수 있습니다.

-   외부 카탈로그(Microsoft가 아닌 타사 업데이트 카탈로그)에서 업데이트를 가져옵니다.
-   적용 가능성 및 배포 메타데이터를 포함하여 업데이트 정의를 수정합니다.
-   외부 카탈로그로 업데이트를 내보냅니다.
-   업데이트 서버에 업데이트를 게시합니다.

업데이트 서버에 업데이트를 게시한 후에는 System Center Configuration Manager를 사용하여 해당 업데이트를 검색하고 관리되는 디바이스에 배포할 수 있습니다.

> [!TIP]  
> 이전 버전인 [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/?LinkId=848111)은 계속 지원됩니다. 이 업데이트된 버전은 기능은 동일하지만 추가 운영 체제, 일부 작업을 간소화하는 새로운 기능이 지원되고 사용자 인터페이스가 업데이트되었습니다.

## <a name="workspaces"></a>작업 영역
Updates Publisher를 열면 기본적으로 *업데이트 작업 영역*의 개요 노드가 열립니다.

![Updates Publisher 콘솔](media/console1.png)   


Updates Publisher에는 구성에 도움이 되는 4개의 작업 영역이 있습니다.


**업데이트 작업 영역**: 이 작업 영역을 사용하여 소프트웨어 업데이트 및 업데이트 번들 [만들기](/sccm/sum/tools/create-updates-with-updates-publisher) 및 [관리](/sccm/sum/tools/manage-updates-with-updates-publisher)를 수행할 수 있습니다. 이 작업 영역에는 업데이트 및 번들을 게시물에 할당하고, 게시하고, 다른 Updates Publisher 리포지토리로 내보내는 작업이 포함됩니다.

**게시물 작업 영역:** 이 작업 영역은 [게시물을 관리](/sccm/sum/tools/updates-publisher-publications)하는 곳입니다. 게시물은 업데이트 내보내기 및 업데이트 게시물을 간소화하기 위해 만드는 업데이트 그룹입니다.

게시물 관리에는 클라이언트가 업데이트를 찾아 설치할 수 있도록 서버에 업데이트를 게시하고, 다른 Updates Publisher 설치에서 사용하도록 업데이트 및 번들을 내보내거나, 게시물의 콘텐츠 또는 세부 정보를 수정하는 작업이 포함됩니다.

**규칙 작업 영역**: 배포하는 업데이트에서 저장한 후 사용할 수 있는 [적용 가능성 규칙을 관리](/sccm/sum/tools/updates-publisher-applicability-rules)하는 곳입니다. 두 가지 유형의 규칙이 있습니다.

-   설치 가능 규칙 - 이 규칙은 클라이언트가 업데이트를 설치해야 할지 결정하는 데 도움이 됩니다.
-   설치됨 규칙 - 이 규칙은 업데이트가 이미 설치되었는지 확인합니다.

**카탈로그 작업 영역**: 이 작업 영역을 사용하여 [소프트웨어 업데이트 카탈로그 관리](/sccm/sum/tools/updates-publisher-catalogs) 및 추가를 수행합니다. 이 작업 영역에는 해당 카탈로그에서 Updates Publisher 리포지토리로 소프트웨어 업데이트 가져오기가 포함됩니다.

## <a name="whats-new-in-the-system-center-updates-publisher-preview"></a>System Center Updates Publisher 미리 보기의 새로운 기능

>[!NOTE] 
>이 섹션의 정보는 System Center Updates publisher의 미리 보기 버전에만 적용 됩니다. 미리 보기를 설치 하려면에서 다운로드 합니다 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=58390)합니다.

업데이트를 작성 하는 데 System Center Updates Publisher에 대 한 미리 보기에서 새 제작 모드를 있습니다. 제작 모드를 사용 하는 경우는 **범주 작업 영역** 시작 화면에 추가 됩니다. 새 **되었고** 단추에도 추가 됩니다 합니다 **업데이트 작업 영역** 제작 모드 활성화 된 경우. 

### <a name="to-enable-authoring-mode-in-the-preview"></a>미리 보기에서 제작 모드를 사용 하도록 설정 하려면

1. 콘솔의 왼쪽된 위 모퉁이에서 클릭 하 여 **Updates Publisher** **속성** 탭을 선택한 후 **옵션**합니다.
1. 로 이동 합니다 **Authoring** 옵션입니다.
1. 확인란 **제작 모드 사용**합니다.

![Updates Publisher에 대 한 제작 모드를 사용 하도록 설정](media/scup-enable-authoring-mode.png)

### <a name="about-the-categories-workspace"></a>범주 작업 영역 정보

범주 작업 영역에 속하는 업데이트를 구성 하려면 업데이트 작성자를 수 있습니다. 예를 들어, OEM 라면 하고자 할 수 모델 또는 제품 라인에 따라 업데이트를 구성 합니다. 여러 범주를 정의할 수 있습니다 및 자식 범주 있지만 것 없습니다 총합계 자식 범주는 두 가지 수준으로 제한 합니다.

![범주 작업 영역 스크린샷](media/scup-categories-workspace.png)

### <a name="assign-an-update-to-a-category"></a>업데이트 범주에 할당

업데이트에서 작성 한 후 할당할 수 있습니다 범주를 클릭 하 여 업데이트를 선택 하 여 **범주** 단추입니다. 또한 업데이트를 마우스 오른쪽 단추로 클릭 하 고 선택할 수 **범주**합니다.

![업데이트 분류의 스크린샷](media/scup-categorize-update.png)


### <a name="about-detectoids"></a>디 텍 토이 드에 대 한

제작 모드 활성화 되 면 업데이트에 대 한 디 텍 토이 드를 만들 수 있습니다. 디 텍 토이 드 적용 가능성을 확인 하려면 동일한 규칙 (또는 규칙 집합이)를 사용 하는 여러 업데이트 해야 하는 경우에 유용 합니다. 이러한 경우는 되었고 만들고 업데이트에 대 한 필수 조건으로 할당 합니다. 작성 된 업데이트에 여러 디 텍 토이 드를 할당할 수 있습니다.


### <a name="create-a-detectoid"></a>되었고 만들기

1. **작업 영역 업데이트**를 엽니다.
1. 리본 메뉴를 클릭 합니다 **되었고** 단추입니다.
1. 프로그램 되었고 만들기 마법사의 지시를 따릅니다.



![되었고를 사용 하 여 필수 구성 요소를 업데이트 합니다.](media/scup-detectoid-as-prerequisite.png)


## <a name="next-steps"></a>다음 단계
시작하려면 먼저 [설치](/sccm/sum/tools/install-updates-publisher)한 다음 Updates Publisher의 [옵션을 구성](/sccm/sum/tools/updates-publisher-options)합니다.
