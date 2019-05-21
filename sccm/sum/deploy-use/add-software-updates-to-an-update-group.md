---
title: '업데이트 그룹에 업데이트 추가 '
titleSuffix: Configuration Manager
description: 사용자 환경에서 소프트웨어 업데이트 그룹에 소프트웨어 업데이트를 수동 또는 자동으로 추가합니다.
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: a0767664-fd60-46a8-9da5-86cc431ce53c
manager: dougeby
author: mestew
ms.author: mstewart
ms.collection: M365-identity-device-management
ms.openlocfilehash: b207d0c210aa25489d67a5a551bf795e86c1582b
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65500243"
---
# <a name="add-software-updates-to-an-update-group"></a>업데이트 그룹에 소프트웨어 업데이트 추가  

*적용 대상: System Center Configuration Manager(현재 분기)*

 소프트웨어 업데이트 그룹을 활용하면 현재의 환경에서 소프트웨어 업데이트를 효과적으로 구성할 수 있습니다. 소프트웨어 업데이트를 소프트웨어 업데이트 그룹에 수동으로 추가하거나, ADR을 사용하여 소프트웨어 업데이트를 소프트웨어 업데이트 그룹에 자동으로 추가할 수 있습니다. 또한 소프트웨어 업데이트 그룹을 수동으로 배포하거나, ADR을 사용하여 소프트웨어 업데이트 그룹을 자동으로 배포할 수 있습니다. 소프트웨어 업데이트 그룹을 배포한 후 이 그룹에 새 소프트웨어 업데이트를 추가할 수 있으며 그 후 Configuration Manager는 새 소프트웨어 업데이트를 자동으로 배포합니다. 새로운 또는 기존 소프트웨어 업데이트 그룹에 소프트웨어 업데이트를 추가하려면 다음 절차를 따르세요.  

#### <a name="to-add-software-updates-to-a-new-software-update-group"></a>새 소프트웨어 업데이트 그룹에 소프트웨어 업데이트를 추가하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  소프트웨어 라이브러리 작업 영역에서 **소프트웨어 업데이트**를 확장한 다음 **모든 소프트웨어 업데이트**를 클릭합니다.  

3.  새 소프트웨어 업데이트 그룹에 추가할 소프트웨어 업데이트를 선택합니다.  

4.  **홈** 탭의 **업데이트** 그룹에서 **소프트웨어 업데이트 그룹 만들기**를 클릭합니다.  

5.  소프트웨어 업데이트 그룹의 이름을 지정하고 선택적으로 설명을 입력합니다. 이때 소프트웨어 업데이트 그룹에 어떤 유형의 소프트웨어 업데이트가 있는지 쉽게 알 수 있도록 충분한 정보를 제공하는 이름과 설명을 사용합니다. 계속하려면 **만들기**를 클릭합니다.  

6.  **소프트웨어 업데이트 그룹** 을 클릭하여 새 소프트웨어 업데이트 그룹을 표시합니다.  

7.  소프트웨어 업데이트 그룹을 선택하고 **홈** 탭의 **업데이트** 그룹에서 **구성원 표시** 를 클릭하여 그룹에 포함된 소프트웨어 업데이트의 목록을 표시합니다.  

#### <a name="to-add-software-updates-to-an-existing-software-update-group"></a>기존 소프트웨어 업데이트 그룹에 소프트웨어 업데이트를 추가하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  소프트웨어 라이브러리 작업 영역에서 **소프트웨어 업데이트**를 확장한 다음 **모든 소프트웨어 업데이트**를 클릭합니다.  

3.  새 소프트웨어 업데이트 그룹에 추가할 소프트웨어 업데이트를 선택합니다.  

    > [!NOTE]  
    >  **모든 소프트웨어 업데이트** 노드에서 Configuration Manager는 **업그레이드** 분류 및 **Office 365 클라이언트** 제품 분류에 포함된 업데이트를 제외한 모든 업데이트를 표시합니다.  

4.  **홈** 탭의 **업데이트** 그룹에서 **멤버 자격 편집**을 클릭합니다.  

5.  소프트웨어 업데이트를 추가할 소프트웨어 업데이트 그룹을 선택합니다.  

6.  **소프트웨어 업데이트 그룹** 노드를 클릭하여 소프트웨어 업데이트 그룹을 표시합니다.  

7.  소프트웨어 업데이트 그룹을 선택하고 **홈** 탭의 **업데이트** 그룹에서 **구성원 표시** 를 클릭하여 소프트웨어 업데이트 그룹에 포함된 소프트웨어 업데이트의 목록을 표시합니다.  
