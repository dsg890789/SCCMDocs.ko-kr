---
title: "사용자 지정 작업 순서 만들기"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에서 사용자 지정 작업 순서를 편집하여 작업 순서에 단계를 추가합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9800a66-7541-47ca-8276-da8ef6cb6d1b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: e25b60b64ae2ed75091c4f5b0ffa0f9eca4c6cac
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="create-a-custom-task-sequence-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 사용자 지정 작업 순서 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 사용자 지정 작업 순서를 만들 때는 작업 순서 단계가 포함되지 않습니다. 작업 순서를 만든 후에 편집하고 필요한 작업 순서 단계를 추가해야 합니다.  

##  <a name="BKMK_CustomTS"></a> 사용자 지정 작업 순서 만들기  
 사용자 지정 작업 순서를 만들려면 다음 절차를 사용합니다.  

#### <a name="to-create-a-custom-task-sequence"></a>사용자 지정 작업 순서를 만들려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **작업 순서 만들기** 를 클릭하여 작업 순서 만들기 마법사를 시작합니다.  

4.  **새 작업 순서 만들기** 페이지에서 **새 사용자 지정 작업 순서 만들기**를 선택합니다.  

5.  **작업 순서 정보** 페이지에서 작업 순서의 이름, 작업 순서에 대한 설명, 사용할 작업 순서의 부팅 이미지(선택 사항)를 지정한 다음 마법사를 완료합니다.  

 작업 순서 만들기 마법사를 완료하면 Configuration Manager에서 사용자 지정 작업 순서를 **작업 순서** 노드에 추가합니다. 이제 이 작업 순서를 편집하여 작업 순서 단계를 추가할 수 있습니다.  

 사용 가능한 작업 순서 단계 목록을 보려면 [작업 순서 단계](../understand/task-sequence-steps.md)를 참조하세요.  

 작업 순서를 편집하는 방법에 대한 자세한 내용은 [작업 순서 편집](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence)을 참조하세요.  

 작업 순서를 사용하여 운영 체제 배포에 대한 작업을 자동화하는 경우가 대부분이지만 사용자 지정 작업 순서를 만들어 다양한 작업을 자동화할 수 있습니다. 자세한 내용은 [비운영 체제 배포에 대한 작업 순서 만들기](create-a-task-sequence-for-non-operating-system-deployments.md)를 참조하세요.  

 ## <a name="next-steps"></a>다음 단계
 [작업 순서 배포](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)
