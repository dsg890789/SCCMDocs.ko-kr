---
title: "Asset Intelligence 사용 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 일반적인 Asset Intelligence 작업을 수행합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8159bd9-5c2b-4d25-82f9-78fcfd732ba9
caps.latest.revision: 6
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 415ab53796b6f335e3f58ebce4b0bb1b6ecfa45e


---
# <a name="how-to-use-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Asset Intelligence를 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager 계층 구조에서 일반적인 Asset Intelligence 작업을 관리할 수 있는 정보가 포함되어 있습니다.  

##  <a name="a-namebkmkviewinformationa-view-asset-intelligence-information"></a><a name="BKMK_ViewInformation"></a> Asset Intelligence 정보 보기  
 **Asset Intelligence** 홈페이지 및 Asset Intelligence 보고서에서 Asset Intelligence 정보를 볼 수 있습니다.  

###  <a name="a-namebkmkassetintelligencehomepagea-asset-intelligence-home-page"></a><a name="BKMK_AssetIntelligenceHomePage"></a> Asset Intelligence 홈페이지  
 **Asset Intelligence** 홈페이지에는 Asset Intelligence 카탈로그 정보를 위한 요약 대시보드가 표시됩니다. 홈페이지에서 카탈로그 동기화 및 인벤토리에 포함된 소프트웨어 상태에 대한 정보를 볼 수 있습니다. **Asset Intelligence** 홈페이지는 다음 섹션으로 구분되어 있습니다.  

-   **카탈로그 동기화**: Asset Intelligence가 사용되도록 설정되는지 여부, Asset Intelligence 동기화 지점의 현재 상태, 동기화 일정, 고객 라이선스 계정을 가져오는지 여부, 상태가 마지막으로 업데이트된 시기 및 다음 예약된 업데이트 시간, Asset Intelligence 동기화 지점 사이트 시스템이 설치된 후 발생한 변경 사항 수에 대한 정보를 제공합니다.  

    > [!NOTE]  
    >  **Asset Intelligence** 홈페이지의 Asset Intelligence 카탈로그 동기화 섹션은 Asset Intelligence 동기화 지점 사이트 시스템 역할이 설치된 경우에만 표시됩니다.  

-   **인벤토리에 포함된 소프트웨어 상태**: 인벤토리에 포함된 소프트웨어, 소프트웨어 카테고리 및 소프트웨어 제품군의 개수 및 백분율을 제공합니다. 이러한 상태는 Microsoft 또는 관리자에 의해 보류 중인 온라인 식별 또는 미식별 및 보류 중이 아님으로 확인됩니다. 표 형식으로 표시된 정보는 각각에 대한 개수를 보여 주고 차트로 표시된 정보는 각각에 대한 백분율을 보여 줍니다.  

 다음 절차를 사용하여 **Asset Intelligence** 홈페이지의 Asset Intelligence 정보를 볼 수 있습니다.  

##### <a name="to-view-asset-intelligence-information-on-the-asset-intelligence-home-page"></a>Asset Intelligence 홈페이지의 Asset Intelligence 정보를 보려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭합니다. Asset Intelligence 보고서가 표시됩니다.  

###  <a name="a-namebkmkassetintelligencereportsa-asset-intelligence-reports"></a><a name="BKMK_AssetIntelligenceReports"></a> Asset Intelligence 보고서  
 Asset Intelligence에서 수집한 정보를 표시하는 60개 이상의 Asset Intelligence 보고서가 있습니다. 이들 중 많은 보고서는 일반 정보에 대해 쿼리하고 더 자세한 정보로 드릴다운할 수 있는 더 구체적인 보고서에 연결되어 있습니다. Asset Intelligence 보고서는 Configuration Manager 콘솔에서 **모니터링** 작업 영역에 있는 **보고** 노드 아래에 있습니다. 보고서는 하드웨어, 라이선스 관리 및 소프트웨어에 대한 정보를 제공합니다. Configuration Manager의 보고서에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../../../core/servers/manage/reporting.md)를 참조하세요.  

> [!NOTE]  
>  Asset Intelligence 보고서에 표시된 라이선스 정보 및 설치된 소프트웨어 타이틀 수량의 정확성은 엔터프라이즈 환경에 설치된 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보 인벤토리와 관련된 복잡한 종속성 및 제한 때문에 환경에서 사용 중인 라이선스 또는 설치된 소프트웨어 타이틀의 실제 수량과 다를 수 있습니다. Asset Intelligence 보고서를 구매한 소프트웨어 라이선스 준수를 확인하기 위한 유일한 출처로 사용해서는 안 됩니다.  

 다음 절차를 사용하여 Asset Intelligence 보고서에서 Asset Intelligence 정보를 볼 수 있습니다.  

##### <a name="to-view-collected-asset-intelligence-information-by-using-asset-intelligence-reports"></a>Asset Intelligence 보고서를 사용하여 수집된 Asset Intelligence 정보를 보려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **보고**, **보고서**를 확장하고 **Asset Intelligence**를 클릭합니다. Asset Intelligence 보고서가 표시됩니다.  

    > [!WARNING]  
    >  보고서 폴더가 **보고서** 노드에 없는 경우 보고를 구성했는지 확인합니다. 자세한 내용은 [System Center Configuration Manager의 보고 구성](../../../../core/servers/manage/configuring-reporting.md)을 참조하세요.  

3.  실행할 Asset Intelligence 보고서를 선택한 다음 **홈** 탭의 **보고서 그룹** 그룹에서 **실행**을 클릭합니다.  

##  <a name="a-namebkmksynchronizethecataloga-synchronize-the-asset-intelligence-catalog"></a><a name="BKMK_SynchronizeTheCatalog"></a> Asset Intelligence 카탈로그 동기화  
 최신 소프트웨어 타이틀 분류를 검색하려면 로컬 Asset Intelligence 카탈로그를 System Center Online과 동기화하면 됩니다. System Center Online에서 카탈로그 동기화를 수동으로 요청하면 System Center Online에서 동기화 프로세스를 완료하는 데 15분 이상 걸릴 수 있습니다. Configuration Manager는 동기화가 성공적으로 완료된 현재 시간으로 **Asset Intelligence** 홈페이지의 **마지막으로 성공한 업데이트** 설정을 업데이트합니다.  

> [!NOTE]  
>  절차를 사용하기 전에 Asset Intelligence 동기화 지점 사이트 시스템 역할을 먼저 설치해야 합니다. Asset Intelligence 동기화 지점 설치에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

 다음 절차를 사용하여 Asset Intelligence 카탈로그에 대한 동기화 일정을 만들 수 있습니다.  

#### <a name="to-create-a-synchronization-schedule-for-the-asset-intelligence-catalog"></a>Asset Intelligence 카탈로그에 대한 동기화 일정을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **동기화**, **동기화 일정**을 차례로 클릭합니다.  

4.  **Asset Intelligence 동기화 지점 예약** 대화 상자에서 **일정에 따라 동기화 사용**을 선택한 다음 단순 또는 사용자 지정 일정을 구성합니다.  

5.  **확인** 을 클릭하여 변경 내용을 저장합니다.  

    > [!NOTE]  
    >  다음 예약된 동기화를 비롯한 동기화 일정에 대한 자세한 내용은 계층의 최상위 사이트에서 **자산 및 준수** 작업 영역에 있는 **Asset Intelligence** 노드를 참조하세요.  

 다음 절차를 사용하여 Asset Intelligence 카탈로그를 수동으로 동기화할 수 있습니다.  

> [!WARNING]  
>  System Center Online은 12시간 동안 하나의 수동 동기화 요청만 허용합니다.  

###  <a name="a-namebkmkmanuallysynchronizecataloga-to-manually-synchronize-the-asset-intelligence-catalog"></a><a name="BKMK_ManuallySynchronizeCatalog"></a> Asset Intelligence 카탈로그를 수동으로 동기화하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **동기화**, **Asset Intelligence 카탈로그 동기화**, **확인**을 차례로 클릭합니다.  

##  <a name="a-namebkmkcustomizecataloga-customize-the-asset-intelligence-catalog"></a><a name="BKMK_CustomizeCatalog"></a> Asset Intelligence 카탈로그 사용자 지정  
 System Center Online에서 받은 Asset Intelligence 카탈로그 분류 정보는 읽기 전용 권한을 가진 사이트 데이터베이스에 저장되고 수정되거나 삭제될 수 없습니다. 그러나 사용자 지정 소프트웨어 범주, 소프트웨어 제품군, 소프트웨어 레이블 및 하드웨어 요구 사항 카탈로그 정보를 만들고, 수정하고, 삭제할 수 있습니다. 그런 다음 기존 또는 사용자 정의 소프트웨어 타이틀 정보에 대해 System Center Online에서 제공된 정보 대신 사용자 지정 분류 데이터를 사용할 수 있습니다. 분류 정보를 변경하거나 추가할 때 카탈로그 정보는 사용자 정의로 간주됩니다. 사용자 정의 분류 정보는 유효성이 검사된 카탈로그 정보가 아닌 다른 데이터베이스 테이블에 저장됩니다.  

###  <a name="a-namebkmksoftwarecategoriesa-software-categories"></a><a name="BKMK_SoftwareCategories"></a> 소프트웨어 범주  
 Asset Intelligence 소프트웨어 범주는 인벤토리에 포함된 소프트웨어 타이틀을 광범위하게 분류하는 데 사용되며 보다 구체적인 소프트웨어 제품군의 상위 그룹으로도 사용됩니다. 예를 들어 소프트웨어 범주가 에너지 회사이고, 이 소프트웨어 범주 내에 소프트웨어 제품군은 석유, 가스 또는 수력 발전일 수 있습니다. 많은 소프트웨어 범주가 Asset Intelligence 카탈로그에 미리 정의되어 있으며 인벤토리에 포함된 소프트웨어를 추가로 정의하기 위해 추가 사용자 정의 범주를 만들 수 있습니다. 미리 정의된 모든 소프트웨어 범주에 대한 유효성 검사 상태는 항상 **유효성 검사됨**인 반면 Asset Intelligence 카탈로그에 추가된 사용자 지정 소프트웨어 범주 정보는 **사용자 정의됨**입니다.  

 다음 절차를 사용하여 사용자 정의 소프트웨어 범주를 만들 수 있습니다.  

##### <a name="to-create-a-user-defined-software-category"></a>사용자 정의 소프트웨어 범주를 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **카탈로그**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **소프트웨어 범주 만들기**를 클릭합니다.  

4.  **일반** 페이지에서 새 소프트웨어 범주에 대한 이름 및 필요한 경우 설명을 입력합니다.  

    > [!NOTE]  
    >  모든 새 사용자 지정 소프트웨어 범주에 대한 유효성 검사 상태는 항상 **사용자 정의됨**으로 설정됩니다.  

     **다음**을 클릭합니다.  

5.  **요약** 페이지에서 설정을 검토하고 **다음**을 클릭합니다.  

6.  **완료** 페이지에서 **닫기** 를 클릭하여 마법사를 종료합니다.  

###  <a name="a-namebkmksoftwarefamiliesa-software-families"></a><a name="BKMK_SoftwareFamilies"></a> 소프트웨어 제품군  
 Asset Intelligence 소프트웨어 제품군은 소프트웨어 범주 내에 인벤토리에 포함된 소프트웨어 타이틀을 추가로 정의하는 데 사용됩니다. 예를 들어 소프트웨어 범주가 에너지 회사이고, 이 소프트웨어 범주 내에 소프트웨어 제품군은 석유, 가스 또는 수력 발전일 수 있습니다. 많은 소프트웨어 제품군이 Asset Intelligence 카탈로그에 미리 정의되어 있으며 인벤토리에 포함된 소프트웨어를 정의하기 위해 추가 사용자 정의 제품군을 만들 수 있습니다. 미리 정의된 모든 소프트웨어 제품군에 대한 유효성 검사 상태는 항상 **유효성 검사됨**인 반면 Asset Intelligence 카탈로그에 추가된 사용자 지정 소프트웨어 제품군 정보는 **사용자 정의됨**입니다.  

 다음 절차를 사용하여 사용자 정의 소프트웨어 제품군을 만들 수 있습니다.  

##### <a name="to-create-a-user-defined-software-family"></a>사용자 정의 소프트웨어 제품군을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **카탈로그**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **소프트웨어 패밀리 만들기**를 클릭합니다.  

4.  **일반** 페이지에서 새 소프트웨어 제품군에 대한 이름 및 필요한 경우 설명을 입력합니다.  

    > [!NOTE]  
    >  모든 새 사용자 지정 소프트웨어 제품군에 대한 유효성 검사 상태는 항상 **사용자 정의됨**으로 설정됩니다.  

5.  **요약** 페이지에서 설정을 검토하고 **다음**을 클릭합니다.  

6.  **완료** 페이지에서 **닫기** 를 클릭하여 마법사를 종료합니다.  

###  <a name="a-namebkmksoftwarelabelsa-software-labels"></a><a name="BKMK_SoftwareLabels"></a> 소프트웨어 레이블  
 Asset Intelligence 사용자 지정 소프트웨어 레이블을 통해 Asset Intelligence 보고서를 사용하여 소프트웨어 타이틀을 그룹화하고 보는 데 사용할 수 있는 필터를 만들 수 있습니다. 예를 들어 셰어웨어라는 소프트웨어 레이블을 만들고 여러 응용 프로그램과 연결한 다음 셰어웨어의 소프트웨어 레이블을 사용하는 모든 타이틀을 표시하는 보고서를 만들 수 있습니다. Asset Intelligence 카탈로그에 추가하는 모든 사용자 지정 소프트웨어 레이블에 대한 유효성 검사 상태는 **사용자 정의됨** 입니다.  

 다음 절차를 사용하여 사용자 정의 사용자 지정 레이블을 만들 수 있습니다.  

##### <a name="to-create-a-user-defined-software-label"></a>사용자 정의 소프트웨어 레이블을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **카탈로그**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **소프트웨어 레이블 만들기**를 클릭합니다.  

4.  **일반** 페이지에서 새 소프트웨어 제품군에 대한 이름 및 필요한 경우 설명을 입력합니다.  

    > [!NOTE]  
    >  모든 새 사용자 지정 소프트웨어 레이블에 대한 유효성 검사 상태는 항상 **사용자 정의됨**으로 설정됩니다.  

5.  **요약** 페이지에서 설정을 검토하고 **다음**을 클릭합니다.  

6.  **완료** 페이지에서 **닫기** 를 클릭하여 마법사를 종료합니다.  

###  <a name="a-namebkmkhardwarerequirementsa-hardware-requirements"></a><a name="BKMK_HardwareRequirements"></a> 하드웨어 요구 사항  
 하드웨어 요구 사항 정보가 있으면 컴퓨터가 소프트웨어 배포를 위한 대상으로 지정되기 전에 소프트웨어 타이틀에 대한 하드웨어 요구 사항을 충족하는지 확인할 수 있습니다. 많은 하드웨어 요구 사항이 Asset Intelligence 카탈로그에 미리 정의되어 있으며 사용자 지정 요구 사항을 충족하기 위해 새 사용자 정의 하드웨어 요구 사항을 만들 수 있습니다. 미리 정의된 모든 하드웨어 요구 사항에 대한 유효성 검사 상태는 항상 **유효성 검사됨**인 반면 Asset Intelligence 카탈로그에 추가된 사용자 정의 하드웨어 요구 사항 정보는 **사용자 정의됨**입니다.  

> [!IMPORTANT]  
>  Configuration Manager 콘솔에 표시되는 하드웨어 요구 사항은 로컬 컴퓨터의 Asset Intelligence 카탈로그에서 검색되며 System Center 2012 Configuration Manager 클라이언트의 인벤토리에 포함된 소프트웨어 타이틀 정보를 기반으로 하지 않습니다. 하드웨어 요구 사항 정보는 System Center Online과 동기화 프로세스 중 업데이트되지 않습니다. 연결된 하드웨어 요구 사항이 없는 인벤토리에 포함된 소프트웨어에 대한 사용자 정의 하드웨어 요구 사항을 만들 수 있습니다.  

 다음 절차를 사용하여 사용자 정의 하드웨어 요구 사항을 만들 수 있습니다.  

##### <a name="to-create-a-user-defined-hardware-requirements"></a>사용자 정의 하드웨어 요구 사항을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **하드웨어 요구 사항**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **하드웨어 요구 사항 만들기**를 클릭합니다.  

4.  **일반** 페이지에서 다음 정보를 입력합니다.  

    1.  **소프트웨어 타이틀**: 하드웨어 요구 사항이 관련된 소프트웨어 타이틀을 지정합니다. 소프트웨어 타이틀은 아직 Asset Intelligence 카탈로그에 없어야 합니다.  

    2.  **유효성 검사 상태**: 하드웨어 요구 사항에 대해 유효성 검사 상태를 **사용자 정의됨** 으로 나열합니다. 이 설정은 수정할 수 없습니다.  

    3.  **최소 CPU(MHz)**: 소프트웨어 타이틀에 필요한 최소 프로세서 속도(MHz)를 지정합니다.  

    4.  **최소 RAM(KB)**: 소프트웨어 타이틀에 필요한 최소 RAM(KB)을 지정합니다.  

    5.  **최소 디스크 공간(KB)**: 소프트웨어 타이틀에 필요한 최소 디스크 사용 가능한 공간(KB)을 지정합니다.  

    6.  **최소 디스크 크기(KB)**: 소프트웨어 타이틀에 필요한 최소 하드 디스크 크기(KB)를 지정합니다.  

     **다음**을 클릭합니다.  

5.  **요약** 페이지에서 설정을 검토하고 **다음**을 클릭합니다.  

6.  **완료** 페이지에서 **닫기** 를 클릭하여 마법사를 종료합니다.  

###  <a name="a-namebkmkmodifycategorizationa-modify-categorization-information-for-inventoried-software"></a><a name="BKMK_ModifyCategorization"></a> 인벤토리에 포함된 소프트웨어에 대한 분류 정보를 수정합니다.  
 Asset Intelligence 카탈로그의 미리 정의된 소프트웨어는 제품 이름, 공급업체, 소프트웨어 범주 및 소프트웨어 제품군과 같은 특정 범주화 정보로 구성되어 있습니다. 미리 정의된 분류 정보가 요구 사항을 충족하지 않는 경우 소프트웨어 타이틀에 대한 속성에서 정보를 수정할 수 있습니다. 미리 정의된 소프트웨어에 대한 분류 정보를 수정하는 경우 소프트웨어에 대한 유효성 검사 상태는 **유효성 검사됨** 에서 **사용자 정의됨**으로 변경됩니다.  

> [!IMPORTANT]  
>  분류 정보는 최상위 사이트에서만 수정할 수 있습니다.  

 다음 절차를 사용하여 인벤토리에 포함된 소프트웨어에 대한 분류 정보를 수정할 수 있습니다.  

##### <a name="to-modify-the-categorizations-for-software-titles"></a>소프트웨어 타이틀에 대한 분류를 수정하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **인벤토리에 포함된 소프트웨어**를 클릭합니다.  

3.  분류를 수정하려는 소프트웨어 타이틀을 하나 또는 여러 개 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  **일반** 탭에서 다음 분류 정보를 수정할 수 있습니다.  

    -   **제품 이름**: 인벤토리에 포함된 소프트웨어 타이틀의 이름을 지정합니다.  

    -   **공급업체**: 인벤토리에 포함된 소프트웨어 타이틀을 개발한 공급업체의 이름을 지정합니다.  

    -   **범주**: 인벤토리에 포함된 소프트웨어 타이틀에 현재 할당되어 있는 소프트웨어 범주를 지정합니다.  

    -   **제품군**: 인벤토리에 포함된 소프트웨어 타이틀에 현재 할당된 소프트웨어 제품군을 지정합니다.  

6.  **확인** 을 클릭하여 변경 내용을 저장합니다.  

 다음 절차를 사용하여 소프트웨어를 원래 분류 정보로 되돌릴 수 있습니다.  

### <a name="revert-categorization-information-to-original-settings-for-software"></a>분류 정보를 소프트웨어에 대한 원래 설정으로 되돌리기  
 Configuration Manager는 데이터베이스의 System Center Online에서 가져온 분류 정보를 저장합니다. 정보를 삭제할 수 없습니다. 정보를 수정한 후 System Center Online 분류로 분류 정보를 되돌릴 수 있습니다. Asset Intelligence 카탈로그에 없는 인벤토리에 포함된 소프트웨어도 다시 원래 설정으로 되돌릴 수 있습니다.  

 다음 절차를 사용하여 분류 정보를 원래 설정으로 되돌릴 수 있습니다.  

##### <a name="to-revert-categorization-information-to-original-settings"></a>분류 정보를 원래 설정으로 되돌리려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **인벤토리에 포함된 소프트웨어**를 클릭합니다.  

3.  원래 설정으로 되돌리려는 소프트웨어 타이틀을 하나 또는 여러 개 선택합니다. 상태가 **사용자 정의됨** 인 소프트웨어만 되돌릴 수 있습니다.  

    > [!TIP]  
    >  유효성 검사 상태별로 정렬하려면 **상태** 열을 클릭합니다. 정렬을 사용하면 유효성 검사 상태별로 모든 소프트웨어를 표시하여 원래 설정으로 되돌릴 여러 항목을 빠르게 선택할 수 있습니다.  

4.  **홈** 탭의 **제품** 그룹에서 **되돌리기**를 클릭합니다.  

5.  소프트웨어를 원래 분류 정보로 되돌리려면 **예** 를 클릭합니다.  

6.  Asset Intelligence 카탈로그에 있는 소프트웨어에 대한 분류 정보를 되돌리면 유효성 검사 상태가 **사용자 정의됨** 에서 **유효성 검사됨**으로 변경됩니다. 카탈로그에 없는 소프트웨어를 되돌리면 유효성 검사 상태가 **사용자 정의됨** 에서 **범주화되지 않음**으로 변경됩니다.  

##  <a name="a-namebkmkrequestcatalogupdatea-request-a-catalog-update-for-uncategorized-software-titles"></a><a name="BKMK_RequestCatalogUpdate"></a> 범주화되지 않은 소프트웨어 타이틀에 대한 카탈로그 업데이트 요청  
 연구 및 분류하기 위해 범주화되지 않은 소프트웨어 타이틀 정보를 System Center Online에 제출할 수 있습니다. 범주화되지 않은 소프트웨어 타이틀이 제출되면 동일한 소프트웨어 타이틀에 대해 고객으로부터 최소 4개의 범주화 요청이 있으며, 연구원은 소프트웨어 타이틀 분류 정보를 식별하고 분류한 다음 System Center Online 서비스를 사용하는 모든 고객에게 해당 정보를 제공합니다. Microsoft는 분류를 위해 가장 많은 요청이 있는 소프트웨어 타이틀에 대해 가장 높은 우선 순위를 부여합니다. 사용자 지정 소프트웨어 및 기간 업무 응용 프로그램은 하나의 범주 및 모범 사례로 받을 가능성이 낮으므로 이러한 소프트웨어 타이틀은 분류를 위해 Microsoft에 보내지 않는 것이 좋습니다.  

 분류를 위해 소프트웨어 타이틀 정보가 System Center Online에 제출되는 경우 다음 조건이 적용됩니다.  

-   기본 소프트웨어 타이틀 정보만 System Center Online에 전송되므로 제출하기 전에 분류될 소프트웨어 타이틀 정보를 검토할 수 있습니다.  

-   소프트웨어 라이선스 정보는 전송되지 않습니다.  

-   업로드된 모든 소프트웨어 타이틀은 System Center Online 카탈로그의 일부로 공개적으로 사용할 수 있으며 다른 고객이 다운로드할 수 있습니다.  

-   소프트웨어 타이틀의 원본은 System Center Online 카탈로그에 저장되지 않습니다. 그러나 기밀 또는 소유 정보가 포함된 응용 프로그램 타이틀은 System Center Online에서 분류를 위해 제출하지 말아야 합니다.  

> [!NOTE]  
>  Asset Intelligence 개인 정보에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 대한 보안 및 개인 정보](../../../../core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence.md)를 참조하세요.  

 다음 절차를 사용하여 System Center Online에서 Asset Intelligence 카탈로그 소프트웨어 타이틀 분류를 요청할 수 있습니다.  

#### <a name="to-request-a-catalog-update-for-uncategorized-software-titles"></a>분류되지 않은 소프트웨어 타이틀에 대한 카탈로그 업데이트를 요청하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **인벤토리에 포함된 소프트웨어**를 클릭합니다.  

3.  분류를 위해 System Center Online에 제출할 제품 이름을 하나 또는 여러 개 선택합니다. 범주화되지 않은 인벤토리에 포함된 소프트웨어 타이틀만 분류를 위해 System Center Online에 제출할 수 있습니다. 인벤토리에 포함된 소프트웨어 타이틀이 관리자에 의해 분류되어 사용자 정의 상태가 된 경우 인벤토리에 포함된 소프트웨어 타이틀을 마우스 오른쪽 단추로 클릭한 다음 **되돌리기** 를 클릭하여 소프트웨어 타이틀을 **범주화되지 않음** 상태로 되돌려야 분류를 위해 System Center Online에 제출할 수 있습니다.  

    > [!NOTE]  
    >  Configuration Manager는 한 번에 분류를 위해 최대 100개의 소프트웨어 타이틀을 처리할 수 있습니다. 100개가 넘는 소프트웨어 타이틀을 선택한 경우 처음 100개의 소프트웨어 타이틀만 처리됩니다. 나머지 소프트웨어 타이틀을 분류하려면 100개 미만의 일괄 처리로 선택해야 합니다.  

    > [!TIP]  
    >  유효성 검사 상태별로 정렬하려면 **상태** 열을 클릭합니다. 그러면 범주화되지 않은 모든 제품 이름을 보고 분류를 위해 제출할 여러 항목을 빠르게 선택할 수 있습니다.  

4.  **홈** 탭의 **제품** 그룹에서 **카탈로그 업데이트 요청**을 클릭합니다.  

5.  System Center Online 분류 제출 개인 메시지를 검토합니다. System Center Online에 전송할 정보를 보려면 **세부 정보** 를 클릭합니다.  

6.  **이 메시지를 읽고 이해했음**을 선택한 다음 **확인** 을 클릭하여 선택한 소프트웨어 타이틀을 분류를 위해 제출할 수 있습니다.  

7.  분류를 위해 System Center Online에 제출된 인벤토리에 포함된 소프트웨어 제품 이름의 상태가 **범주화되지 않음** 에서 **보류 중**으로 변경되었는지 확인합니다.  

    > [!NOTE]  
    >  분류를 위해 System Center Online에 제출된 소프트웨어는 중앙 관리 사이트에서 유효성 검사 상태가 **보류 중** 이므로 하위 기본 사이트에서는 여전히 **범주화되지 않음** 의 유효성 확인 상태로 표시됩니다.  

##  <a name="a-namebkmkresolvesoftwaredetailsa-resolve-software-details-conflicts"></a><a name="BKMK_ResolveSoftwareDetails"></a> 소프트웨어 세부 정보 충돌 해결  
 기존 소프트웨어 세부 정보와 충돌하는 새로 업데이트된 소프트웨어 분류 세부 정보를 System Center Online에서 받은 경우 충돌을 해결하는 방법을 선택할 수 있습니다. 현재 충돌이 있는 소프트웨어의 유효성 검사 상태는 **업데이트 가능**입니다. 소프트웨어 세부 정보 충돌이 해결된 후에는 지정하는 설정에 따라 소프트웨어 분류 정보가 Asset Intelligence 카탈로그에 유지됩니다. 충돌이 해결된 후 동일한 소프트웨어 분류 값에 대해 System Center Online 값이 변경되지 않는 한 소프트웨어 세부 정보 충돌이 다시 발생하지 않습니다.  

 다음 절차를 사용하여 소프트웨어 세부 정보 충돌 문제를 해결할 수 있습니다.  

#### <a name="to-resolve-a-software-details-conflict"></a>소프트웨어 세부 정보 충돌을 해결하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 클릭하고 **인벤토리에 포함된 소프트웨어**를 클릭합니다.  

3.  **업데이트 가능** 상태에서 소프트웨어 타이틀의 **상태** 열을 검토합니다.  

4.  충돌을 해결해야 하는 소프트웨어 타이틀을 선택한 다음 **홈** 탭의 **제품** 그룹에서 **충돌 해결**을 클릭합니다.  

5.  다음과 같은 정보를 검토합니다.  

    -   **로컬 값**: 최신 System Center Online 소프트웨어 분류 세부 정보와 충돌하는 Asset Intelligence 카탈로그의 기존 소프트웨어 분류 정보를 지정합니다.  

    -   **다운로드한 값**: 충돌하는 Asset Intelligence 카탈로그 소프트웨어 분류 정보에 대해 새 System Center Online 소프트웨어 분류 정보를 지정합니다.  

6.  소프트웨어 세부 정보 충돌을 해결하려면 다음 설정 중 하나를 선택합니다.  

    -   **Do not change the locally edited catalog information value**(로컬로 편집한 카탈로그 정보 값 변경 안 함): 기존 Asset Intelligence 카탈로그 소프트웨어 분류 정보를 유지하여 소프트웨어 세부 정보 충돌을 해결합니다. 이 설정을 선택하면 소프트웨어 타이틀 상태가 **업데이트 가능** 에서 **사용자 정의됨**으로 변경됩니다.  

    -   **Overwrite the locally edited catalog information value with the downloaded System Center Online value**(다운로드한 System Center Online 값으로 로컬로 편집한 카탈로그 정보 값 덮어쓰기): 기존 Asset Intelligence 카탈로그 소프트웨어 분류 정보를 System Center 온라인에서 가져온 새 정보로 덮어써 소프트웨어 세부 정보 충돌을 해결합니다. 이 설정을 선택하면 소프트웨어 타이틀 상태가 **업데이트 가능** 에서 **유효성 확인됨**으로 변경됩니다.  

     **확인** 을 클릭하여 충돌 해결을 저장합니다.  



<!--HONumber=Nov16_HO1-->


