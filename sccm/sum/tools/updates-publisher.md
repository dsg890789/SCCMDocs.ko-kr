---
title: Updates Publisher
titleSuffix: Configuration Manager
description: System Center Updates Publisher를 사용하여 사용자 지정 업데이트 관리
ms.date: 11/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 878e69ffb3f4b5a1c823b1b98a1e53305382ac7b
ms.sourcegitcommit: 54f56bd30a161e8847f8bfd00ede586a1cf97d33
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73710528"
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

## <a name="whats-new-in-system-center-updates-publisher"></a>System Center Updates Publisher의 새로운 기능

>[!NOTE] 
> 최신 버전의 System Center Updates Publisher는 2019 년 11 월 6 일에 출시 되었습니다. 자세한 내용은 [릴리스 기록](#release-history) 섹션을 참조 하세요.

업데이트를 작성 하는 데 도움이 되는 새로운 제작 모드 System Center Updates Publisher 있습니다. 제작 모드를 사용 하도록 설정 하면 **범주 작업 영역이** 시작 화면에 추가 됩니다. 제작 모드를 사용 하는 경우 새 **Detectoid** 단추도 **업데이트 작업 영역** 에 추가 됩니다.

### <a name="to-enable-authoring-mode"></a>제작 모드를 사용 하도록 설정 하려면

1. 콘솔의 왼쪽 위 모서리에서 **Updates Publisher** **속성** 탭을 클릭 한 다음 **옵션**을 선택 합니다.
1. **제작** 옵션으로 이동 합니다.
1. **제작 모드 사용**확인란을 선택 합니다.

![Updates Publisher에 대 한 제작 모드 사용](media/scup-enable-authoring-mode.png)

### <a name="about-the-categories-workspace"></a>범주 작업 영역 정보

범주 작업 영역에서 업데이트 작성자는 함께 포함 된 업데이트를 구성할 수 있습니다. 예를 들어 OEM 인 경우 모델 또는 제품 라인에 따라 업데이트를 구성할 수 있습니다. 두 수준으로 제한 되므로 범주 및 자식 범주를 여러 개 정의할 수 있지만, 그랜드 자식 범주는 정의할 수 없습니다.

![범주 작업 영역의 스크린샷](media/scup-categories-workspace.png)

### <a name="assign-an-update-to-a-category"></a>범주에 업데이트 할당

업데이트를 작성 한 후에는 업데이트를 선택 하 고 **분류** 단추를 클릭 하 여 범주에 할당할 수 있습니다. 업데이트를 마우스 오른쪽 단추로 클릭 하 고 **범주**를 선택할 수도 있습니다.

![업데이트 분류 스크린샷](media/scup-categorize-update.png)

### <a name="about-detectoids"></a>Detectoids 정보

제작 모드를 사용 하도록 설정 하면 업데이트에 대 한 detectoids를 만들 수 있습니다. Detectoids는 동일한 규칙 또는 규칙 집합을 사용 하 여 적용 가능성을 결정 하는 여러 업데이트가 있는 경우에 유용 합니다. 이러한 인스턴스에서 detectoid를 만들어 업데이트를 위한 필수 구성 요소로 할당 합니다. 작성 된 업데이트에 여러 detectoids를 할당할 수 있습니다.


### <a name="create-a-detectoid"></a>Detectoid 만들기

1. **작업 영역 업데이트**를 엽니다.
1. 리본에서 **Detectoid** 단추를 클릭 합니다.
1. 마법사의 지시에 따라 detectoid을 만듭니다.



![Detectoid를 사용 하 여 필수 구성 요소 업데이트](media/scup-detectoid-as-prerequisite.png)

## <a name="release-history"></a>릴리스 기록

- [2019 RTW 버전 6.0.394.0](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/SCUP-adds-support-for-update-categories/ba-p/990111). 릴리스 날짜: 2019년 11월 6일
- [KB4462765에서 롤업 버전 6.0.283.0을 업데이트](https://support.microsoft.com/help/4462765/update-rollup-for-system-center-updates-publisher)합니다. 릴리스 날짜: 2018년 9월 7일
- [2017 RTW 버전 6.0.276.0](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/System-Center-Updates-Publisher-adds-support-for-new-OSes/ba-p/274986). 릴리스 날짜: 2018년 3월 26일


## <a name="next-steps"></a>다음 단계
시작하려면 먼저 [설치](/sccm/sum/tools/install-updates-publisher)한 다음 Updates Publisher의 [옵션을 구성](/sccm/sum/tools/updates-publisher-options)합니다.
