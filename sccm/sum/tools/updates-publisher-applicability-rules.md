---
title: "적용 가능성 규칙 | Microsoft 문서"
description: "System Center Updates Publisher의 적용 가능성 규칙 관리"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cf0c2cd-397a-4622-b11c-961f334fb7d7
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Human Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 2925abda07abaa46ad56b9b433ce003c22aede5e
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---

# <a name="manage-applicability-rules-in-updates-publisher"></a>Updates Publisher의 적용 가능성 규칙 관리

*적용 대상: System Center Updates Publisher*

Updates Publisher에서 적용 가능성 규칙은 장치에 업데이트를 설치하기 전에 충족해야 할 요구 사항을 정의합니다. 규칙을 사용하여 컴퓨터에 업데이트가 설치되었는지 확인할 수도 있습니다. 여러 부분으로 구성된 복잡한 적용 가능성 규칙을 규칙 집합이라고 합니다.

업데이트 번들은 적용 가능성 규칙을 사용하지 않습니다.

## <a name="overview-of-applicability-rules"></a>적용 가능성 규칙 개요
**규칙 작업 영역**에서 적용 가능성 규칙을 관리합니다. 규칙을 만들 때 하나 이상의 조건을 지정하려고 합니다. 여러 조건을 지정하는 경우, 조건을 순차적으로 평가하거나 논리적 **And** 또는 **Or** 문으로 조합할 수 있도록 조건 간의 관계를 구성할 수 있습니다.

예를 들어 다음은 세 가지 규칙을 포함하는 규칙 집합입니다. 첫 번째 규칙은 *MyFile* 파일이 있는지 확인하고, 두 번째와 세 번째 규칙은 Windows 운영 체제의 언어가 영어인지 일본어인지 확인합니다.

    And  
      File ‘\[PROGRAM\_FILES\] \\Microsoft\\MyFile’ exists  
      Or  
        Windows Language is English   
        Windows Language is Japanese

모든 업데이트에는 하나 이상의 적용 가능성 규칙이 필요합니다. 가져오는 업데이트에 이미 적용 가능성 규칙이 적용되어 있고 고유한 업데이트를 만들 경우 이 업데이트에 하나 이상의 규칙을 추가해야 합니다. Updates Publisher의 모든 업데이트에 대한 규칙을 수정하고 업데이트할 수 있습니다.

만든 규칙을 보려면 **규칙 작업 영역**에서 **My saved rules**(내 저장된 규칙) 목록에 있는 규칙을 선택합니다. 해당 규칙의 개별 조건 및 논리 연산은 콘솔의 **적용 가능성 규칙** 창에 표시됩니다. 가져오는 업데이트에 대한 규칙은 해당 업데이트를 편집할 경우 보거나 수정만 할 수 있습니다.

Updates Publisher의 두 위치에 규칙을 만들 수 있습니다.

-   **규칙 작업 영역**에서 규칙 집합을 만들고 **저장**하면 나중에 사용할 수 있습니다. 업데이트를 편집하거나 만들 경우 **Saved rule**(저장된 규칙)을 **규칙 유형**으로 선택한 다음 미리 만든 규칙 집합 목록에서 선택할 수 있습니다.

-   업데이트를 만들거나 편집할 때 새 규칙을 만들 수도 있습니다. 이러한 방식으로 만든 규칙은 나중에 사용할 수 있도록 저장되지 않습니다.

## <a name="create-applicability-rule"></a>적용 가능성 규칙 만들기
다음 정보는 [Create Update(업데이트 만들기) 마법사](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard) 내에서 규칙을 만드는 방법과 비슷합니다. 하지만 마법사와는 달리 나중에 사용하기 위해 규칙 집합을 저장할 수도 있습니다.

1.  **규칙 작업 영역**에서 **만들기**를 선택하여 **Create Rule**(규칙 만들기) 마법사를 엽니다.

2.  규칙의 이름을 지정한 다음 ![새 규칙](media/newrule.png)을 클릭합니다. 그러면 규칙을 구성할 수 있는 **적용 가능성 규칙** 페이지가 열립니다.

3.  **규칙 유형**에서 다음 중 하나를 선택합니다. 구성해야 하는 옵션은 각 유형별로 다릅니다.

    -   **파일** – 이 업데이트를 적용하기 전에 지정한 하나 이상의 조건을 충족하는 속성을 가진 파일이 장치에 있어야 하는 경우 이 규칙을 사용합니다.

    -   **레지스트리 -** 장치에서 이 업데이트를 설치하도록 규정하기 전에 있어야 할 레지스트리 세부 정보를 지정하려면 이 유형을 사용합니다.

    -   **시스템 -** 이 규칙은 시스템 세부 정보를 사용하여 적용 가능성을 결정합니다. Windows 버전, Windows 언어, 프로세서 아키텍처를 정의하거나 WMI 쿼리를 지정하여 장치 운영 체제를 식별할 수 있습니다.

    -   **Windows Installer -** 설치된 .MSI 또는 Windows Installer 패치(.MSP)를 기반으로 적용 가능성을 결정하려면 이 규칙 유형을 사용합니다. 특정 구성 요소 또는 기능이 요구 사항의 일부로 설치되어 있는지도 확인할 수 있습니다.

       > [!IMPORTANT]   
       > 관리되는 장치에서 Windows 업데이트 에이전트는 사용자 단위로 설치된 Windows Installer 패키지를 검색할 수 없습니다. 이 규칙 유형을 사용하면 파일 버전이나 레지스트리 키 값과 같은 추가 적용 가능성 규칙을 구성하여 사용자 단위인지 또는 시스템 단위인지에 관계없이 Windows Installer 패키지를 올바르게 검색할 수 있습니다.

    -   **저장된 규칙** - 이 옵션을 사용하면 이전에 구성하고 저장한 규칙을 찾아서 사용할 수 있습니다.

4.  원하는 대로 추가 규칙을 계속 추가하고 구성합니다.

5.  보다 복잡한 필수 조건 검사를 만들려면 논리 연산 단추를 사용하여 다양한 규칙의 순서를 지정하고 그룹화합니다.

6.  규칙 집합이 완료되면 **확인**을 클릭하여 저장합니다. 이제 규칙 집합이 **My saved rules**(내 저장된 규칙) 목록에 나타납니다.

## <a name="edit-applicability-rule-sets"></a>적용 가능성 규칙 집합 편집
적용 가능성 규칙을 편집하려면 **규칙 작업 영역**에서 **My saved rules**(내 저장된 규칙) 목록에 저장된 임의의 규칙을 선택한 다음 리본 메뉴에서 **편집**을 선택합니다. 그러면 **Edit Rule**(규칙 편집) 마법사가 열립니다.

**Edit Rule**(규칙 편집) 마법사에 규칙 집합의 현재 규칙이 표시됩니다. **Create Rule**(규칙 만들기) 마법사를 사용하여 새 규칙을 만드는 것과 같은 방법으로 규칙을 편집합니다. 이 마법사를 사용하여 규칙 집합의 이름을 바꾸거나, 규칙을 삭제하거나, 규칙 및 관계의 순서를 재정렬하거나, 새 규칙을 추가할 수 있습니다.

변경을 수행한 후 **확인**을 선택하여 변경 내용을 저장하고 마법사를 닫습니다.

규칙 마법사 사용에 대한 자세한 내용은 [Create Update(업데이트 만들기) 마법사](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard)의 **7단계**, 적용 가능성 페이지를 참조하세요.

## <a name="delete-applicability-rules"></a>적용 가능성 규칙 삭제
저장된 적용 가능성 규칙을 삭제하려면 **규칙 작업 영역**에서 **My saved rules**(내 저장된 규칙) 목록에 있는 규칙 또는 규칙 집합을 선택한 다음 리본 메뉴에서 **삭제**를 선택합니다. 이렇게 하면 저장된 규칙 또는 규칙 집합이 Updates Publisher에서 제거됩니다.

특정 업데이트에서 규칙을 삭제하려면 [업데이트를 편집](/sccm/sum/tools/manage-updates-with-updates-publisher#edit-updates-and-bundles)해야 합니다.

