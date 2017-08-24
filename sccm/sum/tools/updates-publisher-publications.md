---
title: "게시물 관리 | Microsoft 문서"
description: "System Center Updates Publisher를 사용하여 게시물로 소프트웨어 업데이트 그룹을 관리합니다."
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c1df1d-7728-4980-9199-bc32cde5439e
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: ddea7af935d5be880b96e383401061f8aa11e6da
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="manage-publications-in-updates-publisher"></a>Updates Publisher의 게시물 관리

*적용 대상: System Center Updates Publisher*

게시물을 사용하여 업데이트 및 번들 그룹을 단일 개체로 관리할 수 있습니다. 여기에는 업데이트를 관리 서버에 게시하고 게시물을 Updates Publisher의 다른 설치에 사용할 그룹으로 내보내는 작업이 포함됩니다.

## <a name="create-publications"></a>게시물 만들기
게시는 두 가지 방법으로 만들어집니다.

-   **업데이트 작업 영역**에서 업데이트 및 번들을 관리하는 경우 이때 만들어지는 새 게시물에 업데이트 및 번들을 [할당](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)할 수 있습니다.

-   **게시물 작업 영역**(게시 작업 영역)에서 리본의 **게시** 탭에 있는 **만들기** 단추를 사용할 수 있습니다. 이 방법을 사용하면 나중에 사용할 수 있도록 게시물을 만들 수 있습니다. 나중에 업데이트를 할당하면 이 게시물을 사용할 수 있습니다.

## <a name="rename-a-publication"></a>게시물 이름 바꾸기
게시물의 이름을 바꾸려면 **게시물 작업 영역** 내에서 게시물을 선택한 다음 리본의 **게시물** 탭에서 **편집**을 선택합니다.

## <a name="change-the-publication-type-of-updates-in-a-publication"></a>게시물에서 업데이트의 게시물 유형을 변경합니다.
**게시물 작업 영역**에서 게시물에 할당된 업데이트 및 번들의 **게시물 유형**을 수정할 수 있습니다.

1. 수정하려는 업데이트를 포함하는 게시물을 선택한 다음  **&lt;게시물 이름> 구성원 업데이트** 목록에서 하나 이상의 업데이트 또는 번들을 선택합니다.

2. 다음으로 **홈** 탭에서 다음 옵션 중 하나를 선택합니다. 사용할 수 있는 옵션은 선택한 업데이트의 게시물 유형에 따라 달라집니다.

  -   **자동**
  -   **전체 콘텐츠**
  -   **메타데이터만**

변경한 후 새 값을 보려면 게시물 뷰를 새로 고쳐야 할 수 있습니다.

다른 게시물 유형에 대한 자세한 내용은 [게시물에 업데이트 및 번들 할당](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)을 참조하세요.

> [!TIP]    
> 번들의 게시물 유형을 설정할 때 해당 번들의 모든 소프트웨어 업데이트는 해당 번들의 게시물 유형으로 게시됩니다.

## <a name="remove-updates-from-a-publication"></a>게시물에서 업데이트 제거
게시물에서 업데이트 또는 번들을 제거하려면 **게시물 작업 영역**에서 수정할 게시물을 선택한 다음 제거할 업데이트 및 번들을 선택합니다. 다음으로 리본의 **홈** 탭에서 **제거**를 선택합니다.

게시물에서 업데이트가 제거된 후에도 Updates Publisher 리포지토리에서 계속 사용할 수 있습니다.

## <a name="publish-publications"></a>게시물 게시
업데이트 및 번들을 게시하면 Updates Publisher가 해당 업데이트 및 번들에 대한 정보(메타데이터)와 업데이트용 이진 파일(전체 콘텐츠)을 장치 배포용 업데이트 서버에 추가합니다.

게시 옵션을 사용하려면 Updates Publisher의 [업데이트 서버](/sccm/sum/tools/updates-publisher-options#update-server) 옵션을 구성해야 합니다. 이 구성 옵션을 열려면 **업데이트 작업 영역** &gt; **개요**로 이동하여 **Configure WSUS and Signing Certificate**(WSUS 및 서명 인증서 구성)를 선택합니다. Updates Publisher 옵션의 [업데이트 서버] 페이지로 이동할 수도 있습니다.

> [!NOTE]   
> Updates Publisher는 크기가 375MB 이하인 업데이트만 게시할 수 있습니다.

### <a name="to-publish-a-publication"></a>게시물을 게시하려면

1.  **게시물 작업 영역**으로 이동한 다음 게시하거나 내보내려는 업데이트 및 번들 그룹이 포함된 게시물을 선택합니다. 그런 다음 리본의 **홈** 탭에서 **게시**를 선택합니다.

2.  **게시** 마법사의 **선택** 페이지에서 새 게시 인증서를 사용하여 모든 업데이트에 서명하도록 선택할 수 있지만 게시물 유형은 변경할 수 없습니다.

3.  마법사를 완료합니다.

  게시에 실패하면 자세한 정보를 제공할 수 있는 UpdatesPublisher.log 파일에 대한 링크가 제공됩니다.

## <a name="export-a-publication"></a>게시물 내보내기
Updates Publisher 리포지토리에서 게시물을 내보낼 수 있습니다. 이렇게 하면 해당 게시물에 할당된 업데이트 및 번들을 내보내고 업데이트 카탈로그를 만듭니다. 그러면 카탈로그를 [추가](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs)하고 해당 카탈로그를 Updates Publisher의 다른 인스턴스로 [가져올](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) 수 있습니다. 게시물의 일부가 아닌 [업데이트를 내보낼](/sccm/sum/tools/manage-updates-with-updates-publisher#export-updates) 수도 있습니다.

게시물을 내보내려면 **게시물 작업 영역**으로 이동하고 내보낼 업데이트를 포함하는 게시물을 선택합니다. 한 번에 하나의 게시물만 선택할 수 있습니다.

게시물을 선택하고 리본의 **홈** 탭에서 **내보내기**를 선택한 다음 카탈로그 내보내기에 대한 경로와 파일 이름을 제공합니다.

종속 소프트웨어 업데이트를 내보내기의 일부로 내보낼(포함할) 수도 있습니다.

## <a name="rename-a-publication"></a>게시물 이름 바꾸기
게시물의 이름을 바꾸려면 **게시물 작업 영역**에서 게시물을 선택한 다음 리본의 **게시물** 탭에서 **편집**을 선택합니다.

## <a name="delete-a-publication"></a>게시물 삭제
게시물을 삭제하려면 **게시물 작업 영역**에서 게시물을 선택한 다음 리본의 **게시물** 탭에서 **삭제**를 선택합니다.

Updates Publisher에서 게시물을 제거한 후에도 게시물에 있던 업데이트는 Updates Publisher 리포지토리에서 계속 사용할 수 있습니다.

## <a name="expire-or-reactivate-updates-and-bundles"></a>업데이트 및 번들 만료 또는 다시 활성화
**업데이트 작업 영역**에서 업데이트 및 번들을 선택하여 만료시키거나 다시 활성화할 수 있습니다. 선택한 횟수만큼 업데이트 및 번들을 만료 및 다시 활성화할 수 있습니다.

-   **업데이트 또는 번들을 만료시키려면** 업데이트 작업 영역에서 만료되지 않은 하나 이상의 업데이트 또는 번들을 선택한 다음 **홈** 탭에서 **만료**를 선택합니다. Configuration Manager에 업데이트 또는 번들을 만료됨으로 게시할 때까지 다시 활성화할 수 있습니다.

    사용자 지정 업데이트 또는 번들을 만료시킨 다음 만료됨 상태를 Configuration Manager에 게시한 후에야 Configuration Manager에서 사용자 지정 업데이트 또는 번들을 제거(삭제)할 수 있습니다. Configuration Manager에서 업데이트 또는 번들이 만료된 후에는 업데이트 또는 번들을 더 이상 배포하거나 다시 활성화할 수 없습니다.

-   **업데이트 또는 번들을 다시 활성화하려면** 업데이트 작업 영역에서 만료된 하나 이상의 업데이트를 선택한 다음 리본의 **홈** 탭에서 **다시 활성화**를 선택합니다. 만료된 업데이트가 이전에 Configuration Manager에 만료됨으로 게시된 경우에는 이를 다시 활성화할 수 없습니다.
