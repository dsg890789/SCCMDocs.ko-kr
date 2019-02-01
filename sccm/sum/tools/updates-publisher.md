---
title: Updates Publisher
titleSuffix: Configuration Manager
description: System Center Updates Publisher를 사용하여 사용자 지정 업데이트 관리
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2047874bb44c89e510abd52a387277e749cf65db
ms.sourcegitcommit: ef3fdf21180e43afd7af6c8264524711435e426e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54896450"
---
# <a name="system-center-updates-publisher"></a>System Center Updates Publisher

*적용 대상: System Center Updates Publisher*

System Center Updates Publisher(Updates Publisher)는 독립 소프트웨어 공급업체 또는 LOB(기간 업무) 애플리케이션 개발자가 사용자 지정 업데이트를 관리할 수 있도록 하는 독립 실행형 도구입니다. 여기에는 드라이버 및 업데이트 번들과 같은 종속성이 있는 업데이트가 포함됩니다.

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


**업데이트 작업 영역:** 이 작업 영역을 사용하여 소프트웨어 업데이트 및 업데이트 번들을 [만들고](/sccm/sum/tools/create-updates-with-updates-publisher) [관리](/sccm/sum/tools/manage-updates-with-updates-publisher)합니다. 여기에는 업데이트 및 번들을 게시물에 할당하고, 게시하고, 다른 Updates Publisher 리포지토리로 내보내는 작업이 포함됩니다.

**게시물 작업 영역:** [게시물을 관리](/sccm/sum/tools/updates-publisher-publications)하는 곳입니다. 게시물은 업데이트 내보내기 및 업데이트 게시물을 간소화하기 위해 만드는 업데이트 그룹입니다.

게시물 관리에는 클라이언트가 업데이트를 찾아 설치할 수 있도록 서버에 업데이트를 게시하고, 다른 Updates Publisher 설치에서 사용하도록 업데이트 및 번들을 내보내거나, 게시물의 콘텐츠 또는 세부 정보를 수정하는 작업이 포함됩니다.



**규칙 작업 영역:** 배포하는 업데이트에서 저장한 다음, 사용할 수 있는 [적용 가능성 규칙을 관리](/sccm/sum/tools/updates-publisher-applicability-rules)하는 곳입니다. 두 가지 유형의 규칙이 있습니다.

-   설치 가능 규칙 - 이 규칙은 클라이언트가 업데이트를 설치해야 할지 결정하는 데 도움이 됩니다.
-   설치됨 규칙 - 이 규칙은 업데이트가 이미 설치되었는지 확인합니다.

**카탈로그 작업 영역:** 이 작업 영역을 사용하여 [소프트웨어 업데이트 카탈로그를 관리](/sccm/sum/tools/updates-publisher-catalogs)하고 추가합니다. 여기에는 해당 카탈로그에서 Updates Publisher 리포지토리로 소프트웨어 업데이트 가져오기가 포함됩니다.
## <a name="first-steps"></a>첫 번째 단계
시작하려면 먼저 [설치](/sccm/sum/tools/install-updates-publisher)한 다음 Updates Publisher의 [옵션을 구성](/sccm/sum/tools/updates-publisher-options)합니다.
