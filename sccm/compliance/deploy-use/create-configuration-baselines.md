---
title: 구성 기준 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 컬렉션에 배포할 수 있는 구성 기준을 만듭니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 1a6d09e4a5552770a71dc44f473cebd13ba0715c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32331950"
---
# <a name="create-configuration-baselines-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 구성 기준 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 구성 기준에는 미리 정의된 구성 항목과 필요에 따라 다른 구성 기준이 포함됩니다. 구성 기준을 만든 다음 컬렉션에 배포하여 컬렉션의 장치가 구성 기준을 다운로드하고 이를 준수하는지 평가하게 할 수 있습니다.  

 Configuration Manager의 구성 기준에 특정한 수정 버전의 구성 항목을 포함하거나 항상 최신 버전의 구성 항목을 사용하도록 구성할 수 있습니다. 구성 항목 수정 버전에 대한 자세한 내용은 [구성 데이터에 대한 관리 작업](../../compliance/deploy-use/management-tasks-for-configuration-data.md)을 참조하세요.  

 구성 기준을 만들기 위해 사용할 수 있는 두 가지 방법은 다음과 같습니다.  

-   파일에서 구성 데이터를 가져옵니다. **구성 데이터 가져오기 마법사**를 시작하려면 **자산 및 준수** 작업 영역의 **구성 기준** 노드 또는 **구성 항목** 에서 **구성 데이터 가져오기**를 클릭합니다.  

-   **구성 기준 만들기** 대화 상자를 사용하여 새 구성 기준을 만듭니다.  

 다음 절차를 사용하여 **구성 기준 만들기** 대화 상자를 사용하여 구성 기준을 만들 수 있습니다.  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **구성 기준 만들기**를 클릭합니다.  

4.  **구성 기준 만들기** 대화 상자에 고유한 이름 및 구성 기준에 대한 설명을 입력합니다. 이름은 최대 255자를 사용할 수 있으며 설명은 최대 512자를 사용할 수 있습니다.  

5.  **구성 데이터** 목록에는 모든 구성 항목 또는 이 구성 기준에 포함된 구성 기준이 표시됩니다. **추가** 를 클릭하여 목록에 새 구성 항목 또는 구성 기준을 추가합니다. 다음 중에서 선택할 수 있습니다.  

    -   **자산 및 준수**  

    -   **소프트웨어 업데이트**  

    -   **구성 기준**  
      > [!IMPORTANT]
      > 각 구성 기준에 포함되는 소프트웨어 업데이트 수를 1000개 이내로 제한해야 합니다.
6.  **용도 변경** 목록을 사용하여 **구성 데이터** 목록에서 선택한 구성 항목의 동작을 지정합니다. 다음에서 선택할 수 있습니다.  

    -   **필수** 구성 항목이 클라이언트 장치에서 검색되지 않는 경우 구성 기준이 비규격으로 평가됩니다. 검색되는 경우 준수 여부를 평가합니다.  

    -   **선택 사항** 구성 항목이 참조하는 응용 프로그램이 클라이언트 컴퓨터에 있는 경우 구성 항목만 준수 여부를 평가합니다. 응용 프로그램이 없는 경우 구성 기준은 비규격으로 표시되지 않습니다(응용 프로그램 구성 항목에만 적용).  

    -   **금지** 구성 항목이 클라이언트 컴퓨터에서 검색되는 경우 구성 기준이 비규격으로 평가됩니다(응용 프로그램 구성 항목에만 적용).  

    > [!NOTE]
    >  **용도 변경** 목록은 **구성 항목 만들기 마법사** 의 **일반** 페이지에서 **이 구성 항목에 응용 프로그램 설정 포함**옵션을 클릭했을 때만 사용 가능합니다.  

7.  클라이언트 장치에서 준수 여부를 평가하기 위해 특정 또는 최신 수정 버전의 구성 항목을 선택하려면 **수정 버전 변경** 목록을 선택하고, 항상 최신 수정 버전을 사용하려면 **항상 최신 버전 사용** 을 선택합니다. 구성 항목 수정 버전에 대한 자세한 내용은 [구성 데이터에 대한 관리 작업](../../compliance/deploy-use/management-tasks-for-configuration-data.md)을 참조하세요.  

8.  구성 기준에서 구성 항목을 제거하려면 구성 항목을 선택한 다음 **제거**를 클릭합니다.  

9. **확인** 을 클릭하여 **구성 기준 만들기** 대화 상자를 닫고 구성 기준을 만듭니다.  
