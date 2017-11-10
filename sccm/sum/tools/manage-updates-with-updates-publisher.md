---
title: "업데이트 관리"
titleSuffix: Configuration Manager
description: "System Center Updates Publisher로 배포 및 생성하는 업데이트 관리"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd64994c-b426-4465-96cd-54b0edc2778d
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 19a1a84a58923d3345852fc1245a524e7f246e5b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="manage-software-updates-in-updates-publisher"></a>Updates Publisher에서 소프트웨어 업데이트 관리

*적용 대상: System Center Updates Publisher*     

System Center Updates Publisher에서는 **업데이트 작업 영역**을 사용하여 리포지토리로 가져온 소프트웨어 업데이트 및 번들을 관리합니다.  

관리 작업에는 업데이트 및 번들 복제, 편집, 만료 또는 재활성화, 게시물에 업데이트 및 번들 할당 등의 작업이 포함됩니다. 다른 Updates Publisher 설치와 함께 사용할 사용자 지정 카탈로그를 내보낼 수도 있습니다.

관리할 수 있는 업데이트를 얻으려면:
-  Updates Publisher 설치에 [업데이트 카탈로그 추가](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs)
-  해당 카탈로그에서 리포지토리로 업데이트 [가져오기](/sccm/sum/tools/updates-publisher-catalogs#import-updates)

또한 [사용자만의 업데이트를 만들](/sccm/sum/tools/create-updates-with-updates-publisher) 수도 있습니다.



## <a name="create-a-duplicate-of-an-update"></a>업데이트의 복제본 만들기
리포지토리에 있는 업데이트의 복제본 또는 복사본을 만들 수 있습니다. 그런 다음 원본 업데이트를 수정하는 대신 복사본을 수정할 수 있습니다. 업데이트 번들의 복사본은 만들 수 없습니다.

복사본을 만들려면 **업데이트 작업 영역**에서 업데이트를 선택한 다음 **복제**를 선택합니다. 업데이트 복사본은 해당 이름에 *복사본*이 추가된 상태로 업데이트 작업 영역의 동일한 위치에 저장됩니다.

새로 만든 복사본의 상태는 **만료되지 않음**이지만 나머지는 원본의 설정이 유지됩니다.

## <a name="edit-updates-and-bundles"></a>업데이트 및 번들 편집
리포지토리에 있는 업데이트 및 번들을 선택하여 수정할 수 있습니다.

**업데이트 작업 영역**에서 업데이트 또는 번들을 선택한 다음 **홈** 탭에서 **편집**을 선택하여 편집 마법사를 엽니다. 업데이트 및 번들마다 있는 마법사는 개별적이지만 서로 밀접하게 관련되어 있으며 [Create Update](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard)(업데이트 만들기) 또는 [Create Bundle](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-bundle-wizard)(번들 만들기) 마법사와 동일한 옵션을 제공합니다.

편집할 때 업데이트 또는 번들에 대해 사용 가능한 세부 정보를 변경하여 사용자 환경에서 사용할 수 있습니다. 예를 들어 적용 가능성 또는 우선 순위 규칙을 편집하거나 언어를 변경할 수 있습니다. 또한 제품 및 공급업체를 변경하여 업데이트 또는 번들을 사용자 지정 폴더로 이동하고 자신의 용도에 맞게 업데이트를 그룹화할 수 있습니다.

## <a name="assign-updates-and-bundles-to-a-publication"></a>게시물에 업데이트 및 번들 할당
**업데이트 작업 영역**에서 업데이트 및 번들을 선택한 다음 리본의 **홈** 탭에서 **할당**을 선택하여 게시물에 추가할 수 있습니다. 그러면 **Assign Software Updates**(소프트웨어 업데이트 할당) 마법사가 시작됩니다.
-  업데이트 및 번들을 선택하고 단일 작업으로 게시하는 방법에 대한 자세한 내용은 [업데이트 및 번들 게시](#publish-updates-and-bundles-from-the-updates-workspace)를 참조하세요.
-  업데이트 및 번들 그룹을 단일 개체로 관리하는 방법에 대한 자세한 내용은 [게시물 관리](/sccm/sum/tools/updates-publisher-publications)를 참조하세요. 게시물에 업데이트를 할당한 후에는 해당 게시물을 관리한 다음 할당된 모든 업데이트를 포함할 수 있습니다.

게시물에 업데이트를 할당할 때 :

-   만료되거나 만료되지 않은 업데이트 및 번들을 같은 게시물에 포함할 수 있습니다.

-   게시물 유형을 지정합니다.

    -   **전체 콘텐츠** – 업데이트의 전체 콘텐츠가 WSUS 서버에 게시됩니다. 여기에는 메타데이터 및 업데이트 이진 파일이 포함됩니다.

    -   **메타데이터만** - 메타데이터만 게시되고 업데이트 이진 파일은 게시되지 않습니다. 준수 데이터를 수집하려는 경우 이 옵션을 선택할 수 있습니다.

    -   **자동** - 이 모드는 Updates Publisher를 Configuration Manager에 연결한 경우에만 사용할 수 있습니다([ConfigMgr Server](/sccm/sum/tools/updates-publisher-options#configmgr-server) 옵션 참조).

    이 유형을 사용하면 Updates Publisher에서 Configuration Manager를 쿼리하여 업데이트 또는 번들을 게시할 때 전체 콘텐츠를 게시할지 아니면 메타데이터만 게시할지 여부를 결정할 수 있습니다. 업데이트의 전체 콘텐츠는 해당 업데이트가 Updates Publisher 옵션의 **ConfigMgr Server** 페이지에 지정된 **Requested client count threshold**(요청된 클라이언트 수 임계값) 및 **Package source size threshold**(패키지 원본 크기 임계값)를 충족하는 경우에만 게시됩니다.

-   게시물을 선택합니다.

    -   사용할 게시물을 이미 만들었으면 **Assign software update to existing publications**(기존 게시물에 소프트웨어 업데이트 할당)를 사용합니다. 이 옵션은 하나 이상의 게시물이 존재할 때까지 사용할 수 없습니다.

    -   적합한 게시물이 없으면 **Assign software update to a new publication**(새 게시물에 소프트웨어 업데이트 할당)을 사용합니다. 이렇게 하면 지정한 이름으로 새 게시물이 만들어집니다.

게시물에 업데이트를 할당한 후에는 **게시물 작업 영역**을 사용하여 게시물을 그룹에 [게시](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) 또는 [내보낼](/sccm/sum/tools/updates-publisher-publications#export-a-pubilcation) 수 있습니다.

## <a name="publish-updates-and-bundles-from-the-updates-workspace"></a>업데이트 작업 영역에서 업데이트 및 번들 게시
업데이트 및 번들을 게시하면 Updates Publisher가 해당 업데이트 및 번들에 대한 정보(메타데이터)와 업데이트용 이진 파일(전체 콘텐츠)을 장치 배포용 업데이트 서버에 추가합니다.

게시 옵션을 사용하려면 Updates Publisher의 [업데이트 서버](/sccm/sum/tools/updates-publisher-options#update-server) 옵션을 구성해야 합니다. 이 구성 옵션을 열려면 **업데이트 작업 영역** &gt; **개요**로 이동하여 **Configure WSUS and Signing Certificate**(WSUS 및 서명 인증서 구성)를 선택합니다. Updates Publisher 옵션의 [업데이트 서버] 페이지로 이동할 수도 있습니다.

업데이트와 번들을 게시하는 방법에는 두 가지가 있습니다.
-   업데이트 작업 영역에서 직접. *업데이트 및 번들을 게시하려면* 절차를 참조하세요.
-   게시물 작업 영역에서 [게시물](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations)로.  

> [!NOTE]   
> Updates Publisher는 크기가 375MB 이하인 업데이트만 게시할 수 있습니다.

### <a name="to-publish-updates-and-bundles"></a>업데이트 및 번들을 게시하려면
1.  **업데이트 작업 영역**으로 이동하여 게시할 업데이트 및 번들을 하나 이상 선택합니다. 그런 다음 리본의 **홈** 탭에서 **게시**를 선택합니다.

2.  **게시** 마법사의 **선택** 페이지에서 업데이트를 게시할 방법을 선택합니다. 옵션은 [업데이트 할당](#assign-updates-and-bundles-to-a-publication)과 동일하게 **전체 콘텐츠**, **메타데이터만** 또는 **자동**입니다.

    새 게시 인증서로 모든 업데이트에 서명하도록 선택할 수도 있습니다.

3.  마법사를 완료합니다.

게시에 실패하면 자세한 정보를 제공할 수 있는 UpdatesPublisher.log 파일에 대한 링크가 제공됩니다.

## <a name="export-updates"></a>업데이트 내보내기
Updates Publisher 리포지토리에서 업데이트 및 번들을 내보내서 사용자 지정 업데이트 카탈로그를 만들 수 있습니다. 그러면 카탈로그를 [추가](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs)하고 해당 카탈로그를 Updates Publisher의 다른 인스턴스로 [가져올](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) 수 있습니다. 또한 [업데이트를 게시물로 내보낼](/sccm/sum/tools/updates-publisher-publications##export-a-publication) 수도 있습니다.

직접 내보내려면 **업데이트 작업 영역** > **모든 소프트웨어 업데이트**로 이동하여 하나 이상의 업데이트 및 번들을 선택합니다. 공급업체 또는 제품 폴더는 내보낼 수 없지만 폴더를 선택한 다음 해당 폴더에서 내보낼 업데이트를 선택할 수 있습니다.

하나 이상의 업데이트를 선택하고 리본의 **홈** 탭에서 **내보내기**를 선택한 다음 카탈로그 내보내기에 대한 경로와 파일 이름을 제공합니다.

종속 소프트웨어 업데이트를 내보낼(포함할) 수도 있습니다.

## <a name="delete-updates-and-bundles"></a>업데이트 및 번들 삭제
업데이트 및 업데이트 번들을 삭제하여 Updates Publisher 리포지토리에서 제거할 수 있습니다.

**업데이트 작업 영역** > **모든 소프트웨어 업데이트**로 이동하여 하나 이상의 개별 업데이트를 선택합니다. 그런 다음 리본의 **홈** 탭에서 **삭제**를 선택합니다.

-   선택한 항목에 게시되지 않거나 만료된 업데이트 또는 번들만 포함되어 있는 경우 제거하기 전에 삭제할 것인지 확인하는 메시지가 표시됩니다.

-   선택한 항목에 게시되고 아직 만료되지 않은 번들 또는 업데이트가 포함되어 있는 경우 경고가 표시됩니다. 리포지토리에서 삭제하기 전에 해당 업데이트를 [만료](/sccm/sum/tools/updates-publisher-pubilcations#expire-or-reactivate-updates-and-bundles)한 다음 해당 변경 사항을 게시해야 합니다.  

공급업체에서 업데이트 또는 번들을 삭제한 다음 해당 카탈로그를 다시 가져올 경우 해당 업데이트가 리포지토리에 복원됩니다.

## <a name="manage-vendor-and-product-folders"></a>공급업체 및 제품 폴더 관리
업데이트를 가져오거나 만든 각 공급업체의 제품 및 공급업체 목록을 보려면 **업데이트 작업 영역** > **개요** > **모든 소프트웨어 업데이트**로 이동합니다.

마법사를 사용하여 소프트웨어 업데이트 또는 번들을 가져오거나 만들면 Updates Publisher에서 공급업체 및 제품 폴더를 자동으로 만듭니다. 이러한 폴더를 수동으로 만들 수도 있습니다.

-   공급업체 폴더를 만들려면 **업데이트 작업 영역** 탐색 창에서 **모든 소프트웨어 업데이트**를 마우스 오른쪽 단추로 클릭한 다음 **Create Vendor**(공급업체 만들기)를 선택합니다.

-   공급업체 폴더 아래에 제품 폴더를 만들려면 공급업체 폴더를 마우스 오른쪽 단추로 클릭하고 **Create Product**(제품 만들기)를 선택합니다.

폴더를 만드는 것 외에 리포지토리에서 공급업체 또는 제품 폴더의 이름을 바꾸거나 삭제할 수도 있습니다. 이렇게 하려면 폴더를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기** 또는 **삭제** 중 원하는 옵션을 선택합니다. 폴더를 삭제하면 해당 폴더와 해당 제품 폴더의 모든 업데이트와 번들이 Updates Publisher 리포지토리에서 제거됩니다.

사용자가 만든 폴더를 포함하여 공급업체와 제품 폴더 간에 업데이트를 이동할 수 있습니다. 업데이트 또는 번들을 새 폴더로 이동하려면 업데이트 또는 번들을 선택하고 **편집**을 클릭합니다. 그런 다음 Edit Update(업데이트 편집) 마법사의 **정보** 페이지에서 공급업체 및 제품을 다시 할당할 수 있습니다. **Edit Update**(업데이트 편집) 마법사가 완료되면 변경 내용이 적용되고 업데이트가 새 폴더로 이동합니다.

## <a name="view-the-xml-of-an-update-or-bundle"></a>업데이트 또는 번들의 XML 보기
**업데이트 작업 영역**에서 단일 업데이트 또는 번들을 선택한 다음 XML **보기**를 선택하여 해당 업데이트의 XML 구조를 표시할 수 있습니다. XML 구조를 직접 편집할 수 있는 옵션은 없습니다.
