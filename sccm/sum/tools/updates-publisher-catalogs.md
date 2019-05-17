---
title: 업데이트 카탈로그 관리
titleSuffix: Configuration Manager
description: System Center Updates Publisher의 소프트웨어 업데이트 카탈로그 관리
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 887f8029-1a3a-423c-a9c1-31dc0d693386
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ad9387b3864511af6e619d19be2107fab818f86e
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65493739"
---
# <a name="manage-software-update-catalogs-in-updates-publisher"></a>Updates Publisher의 소프트웨어 업데이트 카탈로그 관리

*적용 대상: System Center Updates Publisher*

**카탈로그** **작업 영역**을 사용하여 소프트웨어 업데이트 카탈로그를 관리합니다. 여기에는 새 카탈로그 추가, 기존 카탈로그 구독 관리 및 카탈로그에서 Updates Publisher 리포지토리로 업데이트에 대한 정보 가져오기가 포함됩니다.

소프트웨어 업데이트 카탈로그에는 Microsoft 외의 다른 조직에서 만든 관련 업데이트에 대한 정보가 있습니다. 다른 조직에는 사용자의 조직과 Microsoft에 카탈로그를 등록한 타사 소프트웨어 공급업체가 포함됩니다. 소프트웨어 공급업체의 등록된 카탈로그를 *파트너 카탈로그*라고 합니다. 사용자가 만들고 Microsoft에 등록되지 않은 카탈로그는 *사용자* 카탈로그라고 합니다.

## <a name="add-software-update-catalogs"></a>소프트웨어 업데이트 카탈로그 추가
먼저 Updates Publisher에 업데이트 카탈로그를 추가해야 카탈로그에 포함된 업데이트를 관리할 수 있습니다. 카탈로그를 추가할 때 Updates Publisher는 다음을 수행합니다.
-   해당 카탈로그에 대한 구독을 만들므로 해당 카탈로그에 대한 업데이트를 확인할 수 있습니다.
-   **카탈로그 작업 영역**에 있는 **My Software Update Catalogs**(내 소프트웨어 업데이트 카탈로그) 창에서 카탈로그를 목록에 추가합니다.  

각각의 구독 카탈로그에 대한 정보가 콘솔에 제공됩니다. 정보에는 다운로드 URL 또는 위치, 카탈로그를 만든 회사 또는 조직의 이름, 마지막으로 가져오거나 수정한 시점이 포함되어 있습니다.

Updates Publisher는 시작할 때마다 변경 사항에 대한 구독을 자동으로 확인할 수 있습니다. 이 기능은 [고급 옵션](/sccm/sum/tools/updates-publisher-options#advanced)으로 구성됩니다. 구성되면 Updates Publisher는 구독의 다운로드 URL 또는 위치 정보를 참조하고 리포지토리에 마지막으로 가져온 후 카탈로그에 변경 사항이 있는 경우에 경고합니다.

카탈로그 업데이트를 수동으로 확인하려면 **My Software Update Catalogs**(내 소프트웨어 업데이트 카탈로그) 목록에서 카탈로그를 선택한 다음 리본에서 **새로 고침**을 선택합니다.

카탈로그를 추가하고 구독 카탈로그에 대한 정보를 보는 것 외에도 다음을 수행할 수 있습니다.
-  *사용자* 카탈로그에 대한 정보를 **편집**합니다.
-  카탈로그를 Updates Publisher에서 **삭제**(제거)합니다.
-  카탈로그에서 Updates Publisher 리포지토리로 업데이트를 **가져옵니다**. 업데이트를 가져올 때는 해당 카탈로그에 포함된 모든 업데이트를 가져옵니다. 그런 다음 업데이트 작업 영역에서 업데이트를 보고 여기서 업데이트를 선택하여 업데이트 서버에 게시할 수 있습니다.

> [!NOTE]   
> Updates Publisher에서 카탈로그를 삭제하면 해당 카탈로그의 업데이트가 리포지토리에서 제거됩니다. 그러나 업데이트 서버에 게시한 업데이트에는 영향을 주지 않습니다. 더 이상 리포지토리에 없는 업데이트 서버에서 업데이트를 제거하려면 [참조되지 않은 소프트웨어 업데이트 만료](/sccm/sum/tools/updates-publisher-options#expire-unreferenced-software-updates)를 참조하세요.

## <a name="manage-update-catalogs"></a>업데이트 카탈로그 관리
**카탈로그 작업 영역**의 **My Software Update Catalogs**(내 소프트웨어 업데이트 카탈로그) 창에서 가져온 목록 카탈로그를 볼 수 있습니다. 이 작업 영역에서 다음을 수행할 수 있습니다.

-   **파트너 카탈로그 추가:** 다음 중 하나를 사용하여 새 파트너 카탈로그를 찾습니다.

    -   콘솔에서 **업데이트 작업 영역** > **개요**로 이동합니다. **시작** 창에서 **Add Partner Software Updates Catalogs**(파트너 소프트웨어 업데이트 카탈로그 추가)를 선택합니다.

    -   콘솔에서 **카탈로그 작업 영역** > **My Catalogs**(내 카탈로그)로 이동합니다. 그런 다음 리본 메뉴에서 **Add Catalogs**(카탈로그 추가)를 선택합니다.

-   **사용자 카탈로그 추가:** 콘솔에서 **카탈로그 작업 영역** > **My Catalogs**(내 카탈로그)로 이동합니다. 그런 다음 리본 메뉴에서 **Add Catalogs**(카탈로그 추가)를 선택합니다. 카탈로그를 식별하려면 .cab 파일의 위치뿐만 아니라 게시자, 이름 및 설명을 지정해야 합니다.


-   **카탈로그에 대한 업데이트 확인:** 하나 이상의 카탈로그를 선택한 다음 리본에서 **새로 고침**을 선택합니다.

-   **사용자 카탈로그 편집:** *사용자* 카탈로그를 선택한 다음 리본에서 **편집**을 선택합니다. 그런 다음 사용자 정의 속성을 수정할 수 있습니다.

-   **카탈로그 삭제:** 하나 이상의 카탈로그를 선택한 다음 리본에서 **제거**를 선택합니다. 그러면 Updates Publisher 리포지토리에서 카탈로그, 구독 및 해당 카탈로그의 업데이트가 제거됩니다.

-   **카탈로그에서 리포지토리에 업데이트 추가**: 리본에서 **가져오기**를 선택하여 **Import Catalog**(카탈로그 가져오기) 마법사를 시작합니다. 자세한 내용은 [업데이트 가져오기](#import-updates)를 참조하세요.

## <a name="import-updates"></a>업데이트 가져오기
카탈로그를 가져올 때 업데이트 관리자가 해당 카탈로그에서 Updates Publisher 리포지토리로 업데이트를 추가합니다. 업데이트를 가져온 후 관리되는 디바이스에 사용할 수 있도록 업데이트 서버에 게시할 수 있습니다.

### <a name="to-import-updates"></a>업데이트를 가져오려면
1. **Import Catalog**(카탈로그 가져오기) 마법사를 시작하려면 다음 작업 영역 중 하나의 리본에서 **가져오기**를 선택합니다.

   -   카탈로그 작업 영역

   -   업데이트 작업 영역

2. **가져오기 형식** 페이지에서 Updates Publisher에 추가한 하나 이상의 카탈로그를 선택하거나 아직 구독으로 추가하지 않은 카탈로그에 대한 경로를 지정합니다. **다음**을 선택하여 요약 화면을 보고 준비가 되면 **다음**을 선택하여 가져오기를 시작합니다.

3. **Security Warning – Catalog Validation**(보안 경고 - 카탈로그 유효성 검사) 창에서 카탈로그 인증서를 검토하고 준비가 되면 **Accept**(수락)를 선택하여 업데이트를 가져옵니다.

   > [!CAUTION]
   > 신뢰할 수 있는 게시자의 업데이트만 수락합니다. 신뢰할 수 없는 게시자의 소프트웨어 업데이트는 업데이트 검색 시 클라이언트 컴퓨터를 잠재적으로 손상시킬 수 있습니다.
   > 
   >  더 이상 게시자를 신뢰할 수 없는 경우 해당 게시자를 신뢰할 수 있는 게시자 목록에서 제거합니다. 카탈로그를 허용하는 방법에 대한 자세한 내용을 보려면 **Security Warning – Catalog Validation**(보안 경고 - 카탈로그 유효성 검사) 대화 상자에서 **자세히**를 클릭합니다.

   게시자의 카탈로그를 항상 수락하도록 선택하면 해당 게시자는 [신뢰할 수 있는 게시자 목록](/sccm/sum/tools/updates-publisher-options#trusted-publishers)에 추가됩니다. Updates Publisher 옵션으로 이 목록을 검토하고 편집할 수 있습니다.

4. 가져오기는 업데이트가 이미 리포지토리에 있고 다음 중 하나가 충족될 때 업데이트 가져오기를 건너뜁니다.

   -   업데이트가 마지막으로 가져온 이후에 변경되지 않았습니다.

   -   업데이트가 편집되었으며 새 디지털 해시가 있습니다. 업데이트를 편집하면 새 업데이트가 원본을 덮어쓰지 않는데 이렇게 하면 배포한 변경 내용을 덮어쓰는 것을 방지합니다.

5. **확인** 페이지에서 가져오기 결과를 검토합니다.

6. **닫기**를 클릭하여 마법사를 완료합니다. 이제 업데이트 작업 영역에서 이 카탈로그에 대한 업데이트를 볼 수 있습니다.

## <a name="next-steps"></a>다음 단계
업데이트를 가져온 후 일반적인 작업은 다음과 같습니다.
-   [업데이트 관리](/sccm/sum/tools/manage-updates-with-updates-publisher)를 통해 업데이트 서버에 번들을 작성하고 할당하고 배포합니다.
-   [적용 가능성 규칙 만들기](/sccm/sum/tools/updates-publisher-applicability-rules)를 통해 업데이트가 업데이트 서버에 배포되는 시점을 결정하는 데 도움이 됩니다.
