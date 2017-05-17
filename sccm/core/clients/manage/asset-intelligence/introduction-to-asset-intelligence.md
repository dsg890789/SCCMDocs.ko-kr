---
title: "Asset Intelligence 소개 | Microsoft 문서"
description: "System Center Configuration Manager의 Asset Intelligence를 소개합니다."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0bdfdef5-390f-4099-8bde-de51d9a89175
caps.latest.revision: 7
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: 6a851ddfeee78574fbb0b1eff0c7cc518a7bb598
ms.contentlocale: ko-kr
ms.lasthandoff: 12/16/2016


---
# <a name="introduction-to-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager의 Asset Intelligence 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Asset Intelligence를 통해 Asset Intelligence 카탈로그를 사용하여 엔터프라이즈 전체의 소프트웨어 라이선스 사용 현황을 인벤토리에 포함하고 관리할 수 있습니다. 많은 하드웨어 인벤토리 WMI(Windows Management Instrumentation) 클래스를 통해 사용 중인 하드웨어 및 소프트웨어 타이틀에 대해 수집되는 정보의 범위를 향상시킬 수 있습니다. 60개 이상의 보고서에서 사용하기 쉬운 형식으로 이 정보를 제공합니다. 이들 중 많은 보고서가 일반 정보를 쿼리하고 더 자세한 정보로 드릴다운할 수 있는 보다 구체적인 보고서에 연결됩니다. Asset Intelligence 카탈로그에 사용자 지정 소프트웨어 범주, 소프트웨어 제품군, 소프트웨어 레이블 및 하드웨어 요구 사항 등 사용자 지정 정보를 추가할 수 있습니다. 또한 최신 정보로 Asset Intelligence 카탈로그를 동적으로 업데이트하도록 System Center Online에 연결할 수도 있습니다. Microsoft 고객은 소프트웨어 라이선스 정보를 Configuration Manager 사이트 데이터베이스로 가져와서 엔터프라이즈 소프트웨어 라이선스 사용량을 사용 중인 구입한 소프트웨어 라이선스로 조정할 수 있습니다.  

##  <a name="BKMK_AssetIntelligenceCatalog"></a> Asset Intelligence 카탈로그  

 Configuration Manager Asset Intelligence 카탈로그는 300,000개 이상의 소프트웨어 타이틀 및 버전에 대한 분류 및 식별 정보가 들어 있는 사이트 데이터베이스에 저장되어 있는 데이터베이스 테이블 집합입니다. 이러한 데이터베이스 테이블은 특정 소프트웨어 타이틀에 대한 하드웨어 요구 사항을 관리하는 데에도 사용됩니다.  

 Asset Intelligence 카탈로그는 사용 중인 Microsoft 및 타사 소프트웨어 모두의 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보를 제공합니다. 소프트웨어 타이틀에 대한 미리 정의된 하드웨어 요구 사항 집합은 Asset Intelligence 카탈로그에서 사용할 수 있으며 사용자 지정 요구 사항에 맞게 새 사용자 정의 하드웨어 요구 사항 정보를 만들 수 있습니다. 또한 Asset Intelligence 카탈로그에서 정보를 사용자 지정할 수 있으며 분류를 위해 System Center Online에 소프트웨어 타이틀 정보를 업로드할 수 있습니다.  

 새로 릴리스된 소프트웨어가 들어 있는 Asset Intelligence 카탈로그 업데이트는 대량 카탈로그 업데이트를 수행하기 위해 주기적으로 다운로드할 수 있습니다. 또는 Asset Intelligence 동기화 지점 사이트 시스템 역할을 사용하여 카탈로그를 동적으로 업데이트할 수 있습니다.  

###  <a name="BKMK_SoftwareCategories"></a> 소프트웨어 범주  
 Asset Intelligence 소프트웨어 범주는 인벤토리에 포함된 소프트웨어 타이틀을 폭넓게 분류하는 데 사용되고 또한 보다 구체적인 소프트웨어 제품군의 상위 수준 그룹화로도 사용됩니다. 예를 들어 소프트웨어 범주가 에너지 회사이고, 이 소프트웨어 범주 내에 소프트웨어 제품군은 석유, 가스 또는 수력 발전일 수 있습니다. 많은 소프트웨어 범주가 Asset Intelligence 카탈로그에 미리 정의되어 있으며 사용자 정의 범주를 만들어 인벤토리에 포함된 소프트웨어를 추가적으로 정의할 수 있습니다. 미리 정의된 모든 소프트웨어 범주에 대한 유효성 검사 상태는 항상 **유효성 검사됨**인 반면 Asset Intelligence 카탈로그에 추가된 사용자 지정 소프트웨어 범주 정보는 **사용자 정의됨**입니다. 소프트웨어 범주를 관리하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

> [!NOTE]  
>  Asset Intelligence 카탈로그에 저장되어 있는 미리 정의된 소프트웨어 범주 정보는 읽기 전용으로 변경하거나 삭제할 수 없습니다. 관리자는 사용자 정의 소프트웨어 범주를 추가, 수정 또는 삭제할 수 있습니다.  

###  <a name="BKMK_SoftwareFamilies"></a> 소프트웨어 제품군  
 Asset Intelligence 소프트웨어 제품군은 소프트웨어 범주 내에서 인벤토리에 포함된 소프트웨어 타이틀을 정의하는 데 사용됩니다. 많은 소프트웨어 제품군은 Asset Intelligence 카탈로그에 미리 정의되며 사용자 정의 범주를 만들어 인벤토리에 포함된 소프트웨어를 추가적으로 정의할 수 있습니다. 미리 정의된 모든 소프트웨어 제품군에 대한 유효성 검사 상태는 항상 **유효성 검사됨**인 반면 Asset Intelligence 카탈로그에 추가된 사용자 지정 소프트웨어 제품군 정보는 **사용자 정의됨**입니다. 소프트웨어 제품군을 관리하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

> [!NOTE]  
>  미리 정의된 소프트웨어 제품군 정보는 읽기 전용으로 변경할 수 없습니다. 관리자는 사용자 정의 소프트웨어 제품군을 추가, 수정 또는 삭제할 수 있습니다.  

###  <a name="BKMK_CustomLabels"></a> 소프트웨어 레이블  
 Asset Intelligence 사용자 지정 소프트웨어 레이블을 통해 Asset Intelligence 보고서를 사용하여 소프트웨어 타이틀을 그룹화하고 소프트웨어 타이틀을 보는 데 사용할 수 있는 필터를 만들 수 있습니다. 소프트웨어 레이블을 사용하여 공통 특성을 공유하는 소프트웨어 타이틀의 사용자 정의 그룹을 만들 수 있습니다. 예를 들어 셰어웨어라는 소프트웨어 레이블을 만들고 해당 소프트웨어 레이블을 인벤토리에 포함된 셰어웨어 타이틀에 연결한 다음 보고서를 실행하여 연결된 셰어웨어 소프트웨어 레이블이 있는 모든 소프트웨어 타이틀을 표시할 수 있습니다. 소프트웨어 레이블은 미리 정의되지 않습니다. 소프트웨어 레이블에 대한 유효성 검사 상태는 항상 **사용자 정의됨**입니다. 소프트웨어 레이블을 관리하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

###  <a name="BKMK_HardwareRequirements"></a> 하드웨어 요구 사항  
 하드웨어 요구 사항 정보를 사용하여 컴퓨터가 소프트웨어 배포 대상이 되기 전에 소프트웨어 타이틀을 위한 하드웨어 요구 사항을 충족하는지 확인할 수 있습니다. **Asset Intelligence** 노드 아래 **하드웨어 요구 사항** 노드의 **자산 및 준수** 작업 영역에서 소프트웨어 타이틀에 대한 하드웨어 요구 사항을 관리할 수 있습니다. 많은 하드웨어 요구 사항이 Asset Intelligence 카탈로그에 미리 정의되어 있으며 사용자 지정 요구 사항을 충족하기 위해 새 사용자 정의 하드웨어 요구 사항을 만들 수 있습니다. 미리 정의된 모든 하드웨어 요구 사항에 대한 유효성 검사 상태는 항상 **유효성 검사됨**인 반면 Asset Intelligence 카탈로그에 추가된 사용자 정의 하드웨어 요구 사항 정보는 **사용자 정의됨**입니다. 하드웨어 요구 사항을 관리하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

> [!NOTE]  
>  Configuration Manager 콘솔에 표시되는 하드웨어 요구 사항은 Asset Intelligence 카탈로그에서 검색되며 System Center 2012 Configuration Manager 클라이언트의 인벤토리에 포함된 소프트웨어 타이틀 정보를 기반으로 하지 않습니다. 하드웨어 요구 사항 정보는 System Center Online과 동기화 프로세스 중 업데이트되지 않습니다. 연결된 하드웨어 요구 사항이 없는 인벤토리에 포함된 소프트웨어에 대한 사용자 정의 하드웨어 요구 사항을 만들 수 있습니다.  

 기본적으로 나열된 각 하드웨어 요구 사항에 대해 다음 정보가 표시됩니다.  

-   **소프트웨어 타이틀**: 하드웨어 요구 사항과 연결된 소프트웨어 타이틀을 지정합니다.  

-   **최소 CPU(MHz)**: 소프트웨어 타이틀에 필요한 최소 프로세서 속도(MHz)를 지정합니다.  

-   **최소 RAM(KB)**: 소프트웨어 타이틀에 필요한 최소 RAM(KB)을 지정합니다.  

-   **최소 디스크 공간(KB)**: 소프트웨어 타이틀에서 필요한 최소 사용 가능한 하드 디스크 공간(KB)을 지정합니다.  

-   **최소 디스크 크기(KB)**: 소프트웨어 타이틀에 필요한 최소 하드 디스크 크기(KB)를 지정합니다.  

-   **유효성 검사 상태**: 하드웨어 요구 사항에 대한 유효성 검사 상태를 지정합니다.  

 Asset Intelligence 카탈로그에 저장된 미리 정의된 하드웨어 요구 사항은 읽기 전용이며 삭제할 수 없습니다.  관리자는 Asset Intelligence 카탈로그에 저장되지 않은 소프트웨어 타이틀에 대한 사용자 정의 하드웨어 요구 사항을 추가, 수정 또는 삭제할 수 있습니다.  

##  <a name="BKMK_InventoriedSoftwareTitles"></a> 인벤토리에 포함된 소프트웨어 타이틀  
 **Asset Intelligence** 노드 아래 **인벤토리에 포함된 소프트웨어** 노드의 **자산 및 준수** 작업 영역에서 인벤토리에 포함된 소프트웨어 타이틀 정보를 볼 수 있습니다. 하드웨어 인벤토리 클라이언트 에이전트는 Asset Intelligence 카탈로그에 저장되어 있는 소프트웨어 타이틀을 기반으로 하는 인벤토리 소프트웨어 정보를 Configuration Manager 클라이언트에서 수집합니다.  

> [!WARNING]  
>  하드웨어 인벤토리 클라이언트 에이전트는 사용하도록 설정하는 Asset Intelligence 하드웨어 인벤토리 보고 클래스를 기반으로 한 인벤토리를 수집합니다. 보고 클래스를 사용하도록 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

 기본적으로 인벤토리에 포함된 각 소프트웨어 타이틀에 대해 다음 정보가 표시됩니다.  

-   **이름**: 인벤토리에 포함된 소프트웨어 타이틀의 이름을 지정합니다.  

-   **공급업체**: 인벤토리에 포함된 소프트웨어 타이틀을 개발한 공급업체의 이름을 지정합니다.  

-   **버전**: 인벤토리에 포함된 소프트웨어 타이틀의 제품 버전을 지정합니다.  

-   **범주**: 인벤토리에 포함된 소프트웨어 타이틀에 현재 할당되어 있는 소프트웨어 범주를 지정합니다.  

-   **제품군**: 인벤토리에 포함된 소프트웨어 타이틀에 현재 할당된 소프트웨어 제품군을 지정합니다.  

-   **레이블** [**1**, **2**및 **3**]: 소프트웨어 타이틀과 연결된 사용자 지정 레이블을 지정합니다. 인벤토리에 포함된 소프트웨어 타이틀은 연결된 사용자 지정 레이블을 3개까지 가질 수 있습니다.  

-   **개수**: 소프트웨어 타이틀이 인벤토리에 포함된 Configuration Manager 클라이언트 수를 지정합니다.  

-   **상태**: 인벤토리에 포함된 소프트웨어 타이틀에 대한 유효성 검사 상태를 지정합니다.  

> [!NOTE]  
>  계층의 최상위 사이트에서만 인벤토리에 포함된 소프트웨어에 대한 분류 정보(제품 이름, 공급업체, 소프트웨어 범주 및 소프트웨어 제품군)를 변경할 수 있습니다. 미리 정의된 소프트웨어에 대한 분류 정보를 수정하면 소프트웨어에 대한 유효성 검사 상태가 **유효성 검사됨** 에서 **사용자 정의됨**으로 변경됩니다.  

##  <a name="AssetIntelligenceSycnronizationPoint"></a> Asset Intelligence 동기화 지점  
 Asset Intelligence 동기화 지점은 동적 Asset Intelligence 카탈로그 정보 업데이트를 관리하기 위해 System Center Online에 연결(TCP 포트 443 사용)하는 데 사용되는 Configuration Manager 사이트 시스템 역할입니다. 이 사이트 역할은 계층의 최상위 사이트에만 설치할 수 있습니다. 모든 Asset Intelligence 카탈로그 사용자 지정은 최상위 사이트에 연결된 Configuration Manager 콘솔을 통해 구성해야 합니다. 모든 업데이트는 최상위 사이트에서 구성해야 하지만 Asset Intelligence 카탈로그 정보는 계층의 다른 사이트에 복제됩니다. Asset Intelligence 동기화 지점 사이트 역할을 통해 System Center Online과의 주문형 카탈로그 동기화를 요청하거나 자동 카탈로그 동기화를 예약할 수 있습니다. 새 Asset Intelligence 카탈로그 정보를 다운로드하는 것 외에도 Asset Intelligence 동기화 지점을 통해 사용자 지정 소프트웨어 타이틀 정보를 System Center Online에 분류를 위해 업로드할 수 있습니다. Microsoft에서는 분류를 위해 System Center Online에 업로드된 모든 소프트웨어 타이틀을 공개 정보로 처리합니다. 따라서 사용자 지정 소프트웨어 타이틀에 기밀 또는 비공개 정보가 포함되어 있지 않은지 확인해야 합니다.  

> [!NOTE]  
>  분류되지 않은 소프트웨어 타이틀이 제출된 후 동일한 소프트웨어 타이틀에 대해 4건 이상 고객의 분류 요청이 있으면 System Center Online 연구원이 식별하고 분류한 다음 해당 온라인 서비스를 사용하는 모든 고객이 소프트웨어 타이틀 분류 정보를 사용할 수 있도록 합니다. 분류에 대해 가장 많은 요청을 나타내는 소프트웨어 타이틀이 분류에서 우선 순위가 가장 높습니다. 사용자 지정 소프트웨어 및 기간 업무 응용 프로그램은 하나의 범주 및 모범 사례로 받을 가능성이 낮으므로 이러한 소프트웨어 타이틀은 분류를 위해 Microsoft에 보내지 않는 것이 좋습니다.  

> [!NOTE]  
>  Asset Intelligence 동기화 지점 사이트 시스템 역할은 System Center Online에 연결되어야 합니다. Asset Intelligence 동기화 지점을 설치하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

##  <a name="BKMK_AssetIntelligenceHomePage"></a> Asset Intelligence 홈페이지  
 **자산 및 준수** 작업 영역의 **Asset Intelligence** 노드는 Configuration Manager에서 Asset Intelligence의 홈페이지입니다. **Asset Intelligence** 홈페이지에는 Asset Intelligence 카탈로그 정보에 대한 요약 대시보드 보기가 표시됩니다.  

> [!NOTE]  
>  **Asset Intelligence** 를 보는 동안 홈페이지가 자동으로 업데이트되지 않습니다.  

 **Asset Intelligence** 홈페이지에는 다음 섹션이 포함되어 있습니다.  

-   **카탈로그 동기화**: Asset Intelligence가 사용하도록 설정되어 있는지 여부와 Asset Intelligence 동기화 지점의 현재 상태에 대한 정보를 제공합니다. 또한 섹션에서는 동기화 일정, 고객 라이선스 계정을 가져왔는지 여부, 상태가 마지막으로 업데이트된 때, 예약된 다음 업데이트 시간 및 Asset Intelligence 동기화 지점 사이트 시스템이 설치된 후 발생한 변경 횟수를 제공합니다.  

    > [!NOTE]  
    >  **Asset Intelligence** 홈페이지의 Asset Intelligence 카탈로그 동기화 섹션은 Asset Intelligence 동기화 지점 사이트 시스템 역할이 설치된 경우에만 표시됩니다.  

-   **인벤토리에 포함된 소프트웨어 상태**: 인벤토리에 포함된 소프트웨어, 소프트웨어 카테고리 및 소프트웨어 제품군의 개수 및 백분율을 제공합니다. 이들은 Microsoft 또는 관리자, 보류 중인 온라인 ID로 식별되거나 식별되지 않고 보류 중이 아닙니다. 표 형식으로 표시되는 정보는 각각에 대한 개수를 보여 주고 차트에 표시되는 정보는 각각에 대한 백분율을 보여 줍니다.  

##  <a name="BKMK_AssetIntelligenceReports"></a> Asset Intelligence 보고서  
 Asset Intelligence 보고서는 Configuration Manager 콘솔의 **모니터링** 작업 영역에서 **보고** 노드 아래의 Asset Intelligence 폴더에 있습니다. 보고서는 하드웨어, 라이선스 관리 및 소프트웨어에 대한 정보를 제공합니다. Configuration Manager의 보고서에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../../../core/servers/manage/reporting.md)를 참조하세요.  

> [!NOTE]  
>  Asset Intelligence 보고서에 표시되는 설치된 소프트웨어 타이틀 및 라이선스 정보의 양의 정확도는 환경에서 사용되는 라이선스 또는 설치된 소프트웨어 타이틀의 실제 수와 다를 수 있습니다. 이 차이는 엔터프라이즈 환경에 설치된 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보의 인벤토리 작성과 관련된 복잡한 종속성과 제한 사항 때문입니다. Asset Intelligence 보고서를 구입한 소프트웨어 라이선스 규격을 확인하기 위한 유일한 출처로 사용하지 마세요.  

###  <a name="BKMK_HardwareReports"></a> Asset Intelligence 하드웨어 보고서  
 Asset Intelligence 하드웨어 보고서는 조직의 하드웨어 자산에 대한 정보를 제공합니다. Asset Intelligence 하드웨어 보고서에서는 속도, 메모리, 주변 장치 등과 같은 하드웨어 인벤토리 정보를 사용하여 USB 장치, 업그레이드해야 하는 하드웨어 및 특정 소프트웨어 업그레이드에 대해 준비가 되지 않은 컴퓨터에 대한 정보까지 제공할 수 있습니다.  

> [!NOTE]  
>  Asset Intelligence 하드웨어 보고서의 일부 사용자 데이터는 시스템 보안 이벤트 로그에서 수집됩니다. 더 나은 보고서 정확도를 위해 컴퓨터를 새 사용자에게 재할당할 때 이 로그를 지우는 것이 좋습니다.  

###  <a name="BKMK_LicenseManagementReports"></a> Asset Intelligence 라이선스 관리 보고서  
 Asset Intelligence 라이선스 관리 보고서는 사용 중인 라이선스에 대한 데이터를 제공합니다. 라이선스 원장 보고서에서는 MLS(Microsoft 라이선스 계정)에 적절한 형식으로 설치된 Microsoft 응용 프로그램을 나열합니다. 이는 구매한 라이선스와 사용되는 라이선스를 일치시키는 편리한 방법을 제공합니다. 다른 라이선스 관리 보고서에서는 운영 체제 정품 인증 통계에 대해 KMS(키 관리 서비스)를 실행하는 서버로 사용되는 컴퓨터에 대한 정보를 제공합니다.  

> [!IMPORTANT]  
>  Asset Intelligence 라이선스 관리 보고서 중 몇 가지는 볼륨 라이선스를 관리하는 방법인 KMS의 기능에 대한 정보를 제공합니다. KMS 서버가 구현되지 않은 경우 일부 보고서는 데이터를 반환하지 않을 수 있습니다. KMS에 대한 자세한 내용은 [Microsoft TechNet](http://go.microsoft.com/fwlink/?linkid=3225)에서 KMS를 검색하세요.  

###  <a name="BKMK_SoftwareReports"></a> Asset Intelligence 소프트웨어 보고서  
 Asset Intelligence 소프트웨어 보고서는 조직의 컴퓨터에 설치된 소프트웨어 제품군, 범주 및 특정 소프트웨어 타이틀에 대한 정보를 제공합니다. 소프트웨어 보고서는 브라우저 도우미 개체, 자동으로 시작하는 소프트웨어 등에 대한 정보를 제공합니다. 이러한 보고서는 애드웨어, 스파이웨어 및 기타 맬웨어를 식별하고 소프트웨어 구매 및 지원을 간소화하는 데 도움이 되도록 소프트웨어 중복을 식별하는 데 사용할 수 있습니다.  

###  <a name="BKMK_SoftwareIdTagReports"></a> Asset Intelligence 소프트웨어 ID 태그 보고서  
 Asset Intelligence 소프트웨어 ID 태그 보고서는 ISO/IEC 19770-2와 호환되는 소프트웨어 ID 태그가 포함된 소프트웨어에 대한 정보를 제공합니다. 소프트웨어 ID 태그는 설치된 소프트웨어를 식별하는 데 사용되는 신뢰할 수 있는 정보를 제공합니다. SMS_SoftwareTag 하드웨어 인벤토리 보고 클래스를 사용하도록 설정하면 Configuration Manager에서 소프트웨어 ID 태그가 있는 소프트웨어에 대한 정보를 수집합니다. 다음 보고서는 소프트웨어에 대한 정보를 제공합니다.  

-   **소프트웨어 14A - 소프트웨어 ID 태그가 사용하도록 설정된 소프트웨어 검색**: 이 보고서는 소프트웨어 ID 태그가 사용하도록 설정된, 설치되어 있는 소프트웨어 수를 제공합니다.  

-   **소프트웨어 14B - 특정 소프트웨어 ID 태그가 사용하도록 설정된 소프트웨어가 설치된 컴퓨터**: 이 보고서는 특정 소프트웨어 ID 태그가 사용하도록 설정된 소프트웨어가 설치되어 있는 모든 컴퓨터를 나열합니다.  

-   **소프트웨어 14C - 설치된 소프트웨어 ID 태그가 사용하도록 설정된 특정 컴퓨터의 소프트웨어**: 이 보고서는 특정 소프트웨어 ID 태그가 사용하도록 설정된, 특정 컴퓨터에 설치되어 있는 모든 소프트웨어를 나열합니다.  

###  <a name="BKMK_ReportingLImitations"></a> Asset Intelligence 보고 제한 사항  
 Asset Intelligence 보고서는 사용 중인 설치된 소프트웨어 타이틀 및 구입한 소프트웨어 라이선스에 대한 많은 양의 정보를 제공할 수 있습니다. 그러나 이 정보를 구입한 소프트웨어 라이선스 규격을 확인하기 위한 유일한 출처로 사용하지 않아야 합니다.  

####  <a name="BKMK_ExampleDependencies"></a> 종속성 예  
 설치된 소프트웨어 타이틀 및 라이선스 정보에 대해 Asset Intelligence 보고서에 표시된 양의 정확도는 현재 사용되는 실제 양과 다를 수 있습니다. 이러한 차이는 엔터프라이즈 환경에서 사용 중인 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보의 인벤토리 작성과 관련된 복잡한 종속성으로 인해 발생합니다. 다음 예는 Asset Intelligence 보고서의 정확도에 영향을 줄 수도 있는 Asset Intelligence를 사용하여 엔터프라이즈의 설치된 소프트웨어의 인벤토리 작성과 관련된 종속성을 보여 줍니다.  

 **클라이언트 하드웨어 인벤토리 종속성**  
 Asset Intelligence의 설치된 소프트웨어 보고서는 Asset Intelligence 보고를 사용할 수 있도록 하드웨어 인벤토리를 확장하여 Configuration Manager 클라이언트에서 수집된 데이터를 기반으로 합니다. 하드웨어 인벤토리 보고에 대한 이러한 종속성 때문에 Asset Intelligence 보고서는 필수 Asset Intelligence WMI 보고 클래스를 사용하여 하드웨어 인벤토리 프로세스를 완료한 Configuration Manager 클라이언트의 데이터만 반영합니다. 또한 Configuration Manager 클라이언트는 관리자가 정의한 일정에 따라 하드웨어 인벤토리 프로세스를 수행하기 때문에 데이터 보고 지연으로 인해 Asset Intelligence 보고서의 정확도가 영향을 받을 수도 있습니다. 예를 들어 클라이언트가 성공적으로 하드웨어 인벤토리 주기를 종료한 후 인벤토리에 포함된 사용이 허가된 소프트웨어 타이틀이 제거될 수도 있습니다. 그러나 다음에 예약된 클라이언트의 하드웨어 인벤토리 보고 주기 때까지는 소프트웨어 타이틀이 Asset Intelligence 보고서에 설치된 것으로 표시됩니다.  

 **소프트웨어 패키징 종속성**  
 Asset Intelligence 보고서는 표준 Configuration Manager 클라이언트 하드웨어 인벤토리 프로세스를 사용하여 수집된, 설치되어 있는 소프트웨어 타이틀 데이터를 기반으로 하기 때문에 일부 소프트웨어 타이틀 데이터는 올바르게 수집되지 않았을 수 있습니다. 예를 들어 표준 설치 프로세스를 준수하지 않는 소프트웨어 설치 또는 설치 전에 변경된 소프트웨어 설치는 정확하지 않은 Asset Intelligence 보고를 발생시킬 수 있습니다.  

####  <a name="BKMK_LegalLimitations"></a> 법적 제한 사항  
 Asset Intelligence 보고에 표시되는 정보는 많은 제한 사항이 적용되며 법률, 회계 또는 기타 전문가 조언을 나타내지 않습니다. Asset Intelligence 보고서에서 제공되는 정보는 정보용으로만 사용하고 소프트웨어 라이선스 사용 규격을 확인하기 위한 정보의 유일한 출처로 사용하지 않아야 합니다.  

 다음은 Asset Intelligence 보고서의 정확도에 영향을 줄 수도 있는 Asset Intelligence를 사용하여 엔터프라이즈의 설치된 소프트웨어 및 라이선스 사용에 대한 인벤토리 작성과 관련된 제한 사항 예입니다.  

 **Microsoft 라이선스 사용 수량 제한**  
 -   구매한 Microsoft 소프트웨어 라이선스의 수량은 관리자가 제공하는 정보를 바탕으로 하며 올바른 개수의 소프트웨어 라이선스가 제공되는지 자세히 검토되어야 합니다.  

-   보고된 Microsoft 소프트웨어 라이선스 수량에는 볼륨 라이선스 프로그램을 통해 얻은 Microsoft 소프트웨어 라이선스에 대한 정보만 포함하며 소매, OEM(Original Equipment Manufacturer) 또는 기타 소프트웨어 라이선스 판매 채널을 통해 구입한 소프트웨어 라이선스에 대한 정보는 반영하지 않습니다.  

-   지난 45일 이내에 획득한 소프트웨어 라이선스는 소프트웨어 재판매인 보고 요구 사항 및 일정으로 인해 보고된 Microsoft 소프트웨어 라이선스의 수량에 포함되지 않을 수 있습니다.  

-   기업 합병 또는 인수로 인한 소프트웨어 라이선스 양도는 Microsoft 소프트웨어 라이선스 수량에 반영되지 않을 수 있습니다.  

-   MVLS(Microsoft Volume Licensing) 계약의 표준이 아닌 조건에 따라 보고되는 소프트웨어 라이선스의 수가 달라질 수 있으므로 Microsoft 담당자가 추가로 검토해야 할 수 있습니다.  

 **설치된 소프트웨어 타이틀 수량 제한**  
 Asset Intelligence 보고서에서 설치된 소프트웨어 타이틀의 수량을 정확히 보고하려면 Configuration Manager 클라이언트가 하드웨어 인벤토리 보고 주기를 완료해야 합니다. 또한 클라이언트가 예정된 다음 하드웨어 인벤토리를 보고하기 전에 실행되는 Asset Intelligence 보고서에서 반영되지 않은 성공적인 하드웨어 인벤토리 보고 주기 후, 사용이 허가된 소프트웨어 타이틀의 설치 또는 제거 사이에 지연이 있을 수 있습니다.  

 **라이선스 조정 제한**  
 구매한 소프트웨어 라이선스 수량과 설치된 소프트웨어 타이틀 수량의 조정은 관리자가 지정한 라이선스 수량과 관리자가 설정한 일정에 따라 Configuration Manager 클라이언트 하드웨어 인벤토리에서 수집된 설치되어 있는 소프트웨어 타이틀 수량을 비교하여 계산합니다. 이 비교가 라이선스 입장에 대한 Microsoft의 최종 결론을 나타내지 않습니다. 실제 라이선스 입장은 사용 조건에서 부여하는 특정 소프트웨어 타이틀 라이선스 및 사용 권한에 따라 달라집니다.  

##  <a name="BKMK_ValidationStates"></a> Asset Intelligence 유효성 검사 상태  
 Asset Intelligence 유효성 검사 상태는 Asset Intelligence 카탈로그 정보의 출처 및 현재 유효성 검사 상태를 나타냅니다. 다음 표에서는 가능한 Asset Intelligence 유효성 검사 상태와 이러한 상태를 발생시킬 수 있는 관리자 작업을 보여 줍니다.  

|**상태**|**정의**|**관리자 작업**|**설명**|  
|---------------|--------------------|------------------------------|-----------------|  
|**유효성 검사됨**|카탈로그 항목은 System Center Online 연구원에 의해 정의되었습니다.|없음|최상의 상태입니다.|  
|**사용자 정의됨**|카탈로그 항목이 System Center Online 연구원에 의해 정의되지 않았습니다.|로컬 카탈로그 정보를 사용자 지정했습니다.|이 상태는 Asset Intelligence 보고서에 표시됩니다.|  
|**보류 중**|카탈로그 항목이 System Center Online 연구원에 의해 정의되지 않았지만 항목이 분류를 위해 System Center Online에 제출되었습니다.|System Center Online에서 분류를 요청했습니다.|카탈로그 항목은 System Center Online 연구원이 항목을 분류하고 Asset Intelligence 카탈로그가 동기화될 때까지 이 상태로 유지됩니다.|  
|**업데이트 가능**|사용자 정의된 카탈로그 항목이 후속 카탈로그 동기화 중 System Center Online에서 다르게 분류되었습니다.|항목을 사용자 정의로 분류하도록 로컬 Asset Intelligence 카탈로그를 사용자 지정했습니다.|충돌 해결 작업을 사용하여 새 분류 정보를 사용할지 아니면 이전 사용자 정의 값을 사용할지 여부를 결정할 수 있습니다. 충돌을 해결하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 Asset Intelligence 작업](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md)을 참조하세요.|  
|**범주화되지 않음**|카탈로그 항목이 System Center Online 연구원에 의해 정의되지 않았고, 항목이 분류를 위해 System Center Online에 제출되지 않았으며, 관리자가 사용자 정의 분류 값을 할당하지 않았습니다.|없음|분류를 요청하거나 로컬 카탈로그 정보를 사용자 지정합니다.<br /><br /> 범주화를 요청하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 Asset Intelligence 작업](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md)을 참조하세요.<br /><br /> 소프트웨어 타이틀의 범주를 변경하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 Asset Intelligence 작업](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md)을 참조하세요.|  

> [!NOTE]  
>  분류를 위해 System Center Online에 제출된 카탈로그 항목은 중앙 관리 사이트에서 유효성 검사 상태가 **보류 중** 이지만 하위 기본 사이트에서는 유효성 검사 상태가 **범주화되지 않음** 으로 계속 표시됩니다.  

> [!NOTE]  
>  분류 충돌이 해결된 후, 이후 분류 업데이트에서 항목에 대한 새 정보를 도입하지 않으면 항목이 충돌하는 것으로 다시 확인되지 않습니다.  

 유효성 검사 상태가 다른 상태로 전환될 수 있는 경우의 예를 보려면 [System Center Configuration Manager의 Asset Intelligence에 대한 유효성 검사 상태 전환 예제](../../../../core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence.md)를 참조하세요.  

