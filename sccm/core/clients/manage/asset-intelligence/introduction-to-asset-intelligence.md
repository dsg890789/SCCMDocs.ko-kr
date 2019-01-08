---
title: Asset Intelligence 소개
titleSuffix: Configuration Manager
description: Configuration Manager에서 Asset Intelligence를 사용하여 기업 전반의 소프트웨어 라이선스 사용량을 인벤토리에 포함하고 관리합니다.
ms.date: 12/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0bdfdef5-390f-4099-8bde-de51d9a89175
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cf0d222c005da2b7d5b577ebdec64cd64eba536c
ms.sourcegitcommit: 4659946369d5352234f27c7682bce65a0e86c697
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53303927"
---
# <a name="introduction-to-asset-intelligence-in-configuration-manager"></a>Configuration Manager의 Asset Intelligence 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

Asset Intelligence 카탈로그를 사용하여 기업 전반의 소프트웨어 라이선스 사용량을 인벤토리에 포함하고 관리합니다. Asset Intelligence는 Configuration Manager에서 수집하는 정보의 범위를 개선하기 위해 하드웨어 인벤토리 클래스를 추가합니다. 이 정보에는 사용자 환경에서 사용되는 하드웨어 및 소프트웨어 타이틀이 포함됩니다. 60개 이상의 보고서에서 사용하기 쉬운 형식으로 이 정보를 제공합니다. 이러한 보고서 대부분이 보다 구체적인 보고서로 연결됩니다. 일반 정보에 대해 쿼리하고 더 자세한 정보로 드릴다운합니다. 

Asset Intelligence 카탈로그에 사용자 지정 정보를 추가합니다. 예를 들어 사용자 지정 소프트웨어 범주, 소프트웨어 제품군, 소프트웨어 레이블 및 하드웨어 요구 사항입니다. 최신 정보로 Asset Intelligence 카탈로그를 동적으로 업데이트하려면 해당 카탈로그를 Microsoft Cloud에 연결합니다. 

Asset Intelligence를 사용하여 엔터프라이즈 소프트웨어 라이선스 사용량을 조정할 수 있습니다. 소프트웨어를 사용하는 중에 소프트웨어 라이선스 정보를 보려면 Configuration Manager 사이트 데이터베이스로 해당 정보를 가져옵니다.  



## <a name="BKMK_AssetIntelligenceCatalog"></a> Asset Intelligence 카탈로그  

Asset Intelligence 카탈로그는 사이트 데이터베이스에 저장된 데이터베이스 테이블의 세트입니다. 이러한 테이블에는 300,000개 이상의 소프트웨어 타이틀 및 버전에 대한 분류 및 식별 정보가 포함됩니다. 이러한 테이블을 사용하면 특정 소프트웨어 타이틀에 대한 하드웨어 요구 사항을 관리할 수 있습니다.  

Asset Intelligence는 사용 중인 Microsoft 및 타사 소프트웨어 모두의 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보를 제공합니다. 소프트웨어 타이틀에 대한 미리 정의된 하드웨어 요구 사항 세트는 Asset Intelligence 카탈로그에서 사용할 수 있으며 사용자 지정 요구 사항에 맞게 새 사용자 정의 하드웨어 요구 사항 정보를 만들 수 있습니다. Asset Intelligence 카탈로그에서 정보를 사용자 지정할 수 있으며 Microsoft cloud에 소프트웨어 타이틀 정보를 업로드하여 분류할 수 있습니다.  

새로 릴리스된 소프트웨어가 들어 있는 Asset Intelligence 카탈로그 업데이트는 대량 카탈로그 업데이트를 수행하기 위해 주기적으로 다운로드할 수 있습니다. Asset Intelligence 동기화 지점을 사용하여 카탈로그를 동적으로 업데이트할 수 있습니다.  


### <a name="BKMK_SoftwareCategories"></a> 소프트웨어 범주  

Asset Intelligence 소프트웨어 범주는 인벤토리에 포함된 소프트웨어 타이틀을 폭넓게 분류하는 데 사용되고 보다 구체적인 소프트웨어 제품군의 상위 수준 그룹화로도 사용됩니다. 예를 들어 소프트웨어 범주가 에너지 회사이고, 이 소프트웨어 범주 내에 소프트웨어 제품군은 석유, 가스 또는 수력 발전일 수 있습니다. 많은 소프트웨어 범주가 Asset Intelligence 카탈로그에서 미리 정의됩니다. 사용자 정의 범주를 만들어 인벤토리에 포함된 소프트웨어를 추가적으로 정의할 수 있습니다. 미리 정의된 모든 소프트웨어 범주에 대한 유효성 검사 상태는 항상 **유효성 검사됨**입니다. Asset Intelligence 카탈로그에 추가하는 사용자 지정 소프트웨어 범주 정보는 **사용자 정의됨**입니다. 

소프트웨어 범주를 관리하는 방법에 대한 자세한 내용은 [Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  

> [!NOTE]  
> Asset Intelligence 카탈로그에 저장된 미리 정의된 소프트웨어 범주 정보는 읽기 전용으로 변경하거나 삭제할 수 없습니다. 관리자는 사용자 정의 소프트웨어 범주를 추가, 수정 또는 삭제할 수 있습니다.  


### <a name="BKMK_SoftwareFamilies"></a> 소프트웨어 제품군  

Asset Intelligence 소프트웨어 제품군은 소프트웨어 범주 내에서 인벤토리에 포함된 소프트웨어 타이틀을 정의하는 데 사용됩니다. 많은 소프트웨어 제품군이 Asset Intelligence 카탈로그에서 미리 정의됩니다. 사용자 정의 범주를 만들어 인벤토리에 포함된 소프트웨어를 추가적으로 정의할 수 있습니다. 미리 정의된 모든 소프트웨어 제품군에 대한 유효성 검사 상태는 항상 **유효성 검사됨**입니다. Asset Intelligence 카탈로그에 추가하는 사용자 지정 소프트웨어 제품군 정보는 **사용자 정의됨**입니다. 

소프트웨어 제품군을 관리하는 방법에 대한 자세한 내용은 [Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  

> [!NOTE]  
> 미리 정의된 소프트웨어 제품군 정보는 읽기 전용으로 변경할 수 없습니다. 관리자는 사용자 정의 소프트웨어 제품군을 추가, 수정 또는 삭제할 수 있습니다.  


### <a name="BKMK_CustomLabels"></a> 소프트웨어 레이블  

Asset Intelligence 사용자 지정 소프트웨어 레이블을 사용하면 Asset Intelligence 보고서에서 소프트웨어 타이틀을 그룹화하고 확인하는 필터를 만들 수 있습니다. 소프트웨어 레이블을 사용하여 공통 특성을 공유하는 소프트웨어 타이틀의 사용자 정의 그룹을 만듭니다. 예를 들어 셰어웨어라는 소프트웨어 레이블을 만들고 해당 레이블을 인벤토리에 포함된 셰어웨어 타이틀에 연결하고 보고서를 실행하여 해당 레이블이 포함된 모든 소프트웨어 타이틀을 표시할 수 있습니다. 미리 정의된 레이블이 없습니다. 소프트웨어 레이블에 대한 유효성 검사 상태는 항상 **사용자 정의됨**입니다. 

소프트웨어 레이블을 관리하는 방법에 대한 자세한 내용은 [Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  


### <a name="BKMK_HardwareRequirements"></a> 하드웨어 요구 사항  

하드웨어 요구 사항 정보를 사용하여 컴퓨터가 소프트웨어 배포 대상이 되기 전에 소프트웨어 타이틀의 하드웨어 요구 사항을 충족하는지 확인합니다. **Asset Intelligence** 노드 아래 **하드웨어 요구 사항** 노드의 **자산 및 규정 준수** 작업 영역에서 소프트웨어 타이틀에 대한 하드웨어 요구 사항을 관리합니다. 

많은 하드웨어 요구 사항이 Asset Intelligence 카탈로그에서 미리 정의됩니다. 사용자 지정 요구 사항에 맞게 새 사용자 정의 하드웨어 요구 사항 정보를 만듭니다. 미리 정의된 모든 하드웨어 요구 사항에 대한 유효성 검사 상태는 항상 **유효성 검사됨**입니다. Asset Intelligence 카탈로그에 추가하는 사용자 정의 하드웨어 요구 사항 정보는 **사용자 정의됨**입니다. 

하드웨어 요구 사항을 관리하는 방법에 대한 자세한 내용은 [Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  

> [!NOTE]  
> Configuration Manager 콘솔에 표시된 하드웨어 요구 사항은 Asset Intelligence 카탈로그에서 검색됩니다. 이러한 요구 사항은 클라이언트의 인벤토리에 포함된 소프트웨어 타이틀 정보에 따르지 않습니다. 
> 
> 하드웨어 요구 사항 정보는 Microsoft와 동기화 프로세스의 일부로 업데이트되지 않습니다. 
> 
> 연결된 하드웨어 요구 사항이 없는 인벤토리에 포함된 소프트웨어에 대한 사용자 정의 하드웨어 요구 사항을 만들 수 있습니다.  

기본적으로 나열된 각 하드웨어 요구 사항에 대해 다음 정보가 표시됩니다.  

- **소프트웨어 타이틀**: 하드웨어 요구 사항과 연결된 소프트웨어 타이틀  

- **최소 CPU(MHz)**: 소프트웨어 타이틀에 필요한 최소 프로세서 속도(MHz)  

- **최소 RAM(KB)**: 소프트웨어 타이틀에 필요한 최소 RAM(KB)  

- **최소 디스크 공간(KB)**: 소프트웨어 타이틀에 필요한 최소 하드 디스크 사용 가능한 공간(KB)  

- **최소 디스크 크기(KB)**: 소프트웨어 타이틀에 필요한 최소 하드 디스크 크기(KB)  

- **유효성 검사 상태**: 하드웨어 요구 사항에 대한 유효성 검사 상태  

Asset Intelligence 카탈로그에 저장된 미리 정의된 하드웨어 요구 사항은 읽기 전용으로 삭제할 수 없습니다. 관리자는 Asset Intelligence 카탈로그에 저장되지 않은 소프트웨어 타이틀에 대한 사용자 정의 하드웨어 요구 사항을 추가, 수정 또는 삭제할 수 있습니다.  



## <a name="BKMK_InventoriedSoftwareTitles"></a> 인벤토리에 포함된 소프트웨어 타이틀  

Configuration Manager 콘솔에서 인벤토리에 포함된 소프트웨어 타이틀 정보를 확인하려면 **자산 및 규정 준수** 작업 영역으로 이동하여 **Asset Intelligence** 노드를 확장하고 **인벤토리에 포함된 소프트웨어** 노드를 선택합니다. 하드웨어 인벤토리 에이전트는 Asset Intelligence 카탈로그에 저장된 소프트웨어 타이틀에 따라 인벤토리에 포함된 소프트웨어 정보를 Configuration Manager 클라이언트에서 수집합니다.  

> [!Note]  
> 하드웨어 인벤토리 에이전트는 사용하도록 설정하는 Asset Intelligence 하드웨어 인벤토리 보고 클래스에 따라 인벤토리를 수집합니다. 보고 클래스를 사용하도록 설정하는 방법에 대한 자세한 내용은 [Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  

기본적으로 인벤토리에 포함된 각 소프트웨어 타이틀에 대해 다음 정보가 표시됩니다.  

- **이름**: 인벤토리에 포함된 소프트웨어 타이틀의 이름  

- **공급 기업**: 인벤토리에 포함된 소프트웨어 타이틀을 개발한 공급 기업의 이름  

- **버전**: 인벤토리에 포함된 소프트웨어 타이틀의 제품 버전  

- **범주**: 인벤토리에 포함된 소프트웨어 타이틀에 현재 할당되어 있는 소프트웨어 범주  

- **제품군**: 인벤토리에 포함된 소프트웨어 타이틀에 현재 할당되어 있는 소프트웨어 제품군  

- **레이블**[**1**, **2** 및 **3**]: 소프트웨어 타이틀과 연결된 사용자 지정 레이블입니다. 인벤토리에 포함된 소프트웨어 타이틀은 연결된 사용자 지정 레이블을 3개까지 가질 수 있습니다.  

- **개수**: 소프트웨어 타이틀이 인벤토리에 포함된 Configuration Manager 클라이언트 수  

- **상태**: 인벤토리에 포함된 소프트웨어 타이틀에 대한 유효성 검사 상태  

> [!NOTE]  
> 계층 구조의 최상위 사이트에서만 인벤토리에 포함된 소프트웨어에 대한 분류 정보를 변경할 수 있습니다. 이 정보에는 제품 이름, 공급 기업, 소프트웨어 범주 및 소프트웨어 제품군이 포함됩니다. 미리 정의된 소프트웨어에 대한 분류 정보를 수정하면 소프트웨어에 대한 유효성 검사 상태가 **유효성 검사됨** 에서 **사용자 정의됨**으로 변경됩니다.  



## <a name="AssetIntelligenceSycnronizationPoint"></a> Asset Intelligence 동기화 지점  

Asset Intelligence 동기화 지점은 Configuration Manager 사이트 시스템 역할입니다. 해당 역할을 443 TCP 포트에서 Microsoft 클라우드에 연결하는 데 사용하여 동적 카탈로그 정보 업데이트를 관리합니다. 이 사이트 역할은 계층 구조의 최상위 사이트에만 설치합니다. 최상위 사이트에 연결된 Configuration Manager 콘솔을 사용하여 모든 Asset Intelligence 카탈로그 사용자 지정을 구성합니다. 

최상위 사이트에서 모든 업데이트를 구성하는 동안 카탈로그 정보는 계층 구조의 다른 사이트에 복제됩니다. 사이트 역할을 사용하면 Microsoft와의 주문형 카탈로그 동기화를 요청하거나 자동 카탈로그 동기화를 예약할 수 있습니다. 새 카탈로그 정보를 다운로드하는 것 외에도 Asset Intelligence 동기화 지점을 통해 사용자 지정 소프트웨어 타이틀 정보를 Microsoft에 업로드하여 분류할 수 있습니다. Microsoft에서는 모든 업로드된 소프트웨어 타이틀을 공개 정보로 처리합니다. 사용자 지정 소프트웨어 타이틀에 기밀 정보나 비공개 정보가 포함되지 않아야 합니다.  

범주화되지 않은 소프트웨어 타이틀을 제출하면 Microsoft에서는 고객에게서 동일한 소프트웨어 타이틀에 대해 최소 4번의 분류 요청이 있을 때까지 해당 타이틀을 검토하지 않습니다. Microsoft 연구원은 소프트웨어 타이틀 분류 정보를 파악하고 분류하여 온라인 서비스를 사용하는 모든 고객이 해당 정보를 사용할 수 있게 만듭니다. 분류에 대해 가장 많은 요청을 나타내는 소프트웨어 타이틀이 분류에서 우선 순위가 가장 높습니다. 사용자 지정 소프트웨어 및 LOB(기간 업무) 애플리케이션은 범주를 받을 수 없습니다. 이러한 소프트웨어 타이틀은 분류를 위해 Microsoft로 보내지 마십시오.  

Asset Intelligence 동기화 지점은 Microsoft 클라우드에 연결되어야 합니다. 역할을 설치하는 방법에 대한 자세한 정보는 [Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  



## <a name="BKMK_AssetIntelligenceHomePage"></a> Asset Intelligence 홈페이지  

**자산 및 규정 준수** 작업 영역의 **Asset Intelligence** 노드는 Configuration Manager의 Asset Intelligence 홈페이지입니다. 이 홈페이지에는 Asset Intelligence 카탈로그 정보에 대한 요약 대시보드 보기가 표시됩니다.  

> [!NOTE]  
> **Asset Intelligence**를 보는 동안 홈페이지가 자동으로 업데이트되지 않습니다.  

**Asset Intelligence** 홈페이지에는 다음 섹션이 포함되어 있습니다.  

- **카탈로그 동기화**: Asset Intelligence가 사용하도록 설정되어 있는지 여부와 Asset Intelligence 동기화 지점의 현재 상태에 대한 정보입니다.  

    > [!NOTE]  
    > 홈페이지에는 Asset Intelligence 동기화 지점을 설치할 경우만 이 섹션이 표시됩니다.  

    섹션에서 다음 정보를 제공합니다.  

    - 동기화 일정  

    - 고객 라이선스 계정을 가져온 경우   

    - 마지막 상태 업데이트  

    - 예약된 다음 업데이트 시간  

    - Asset Intelligence 동기화 지점을 설치한 후 변경 횟수   

- **인벤토리에 포함된 소프트웨어 상태**: Microsoft 및 관리자에 의해 온라인 식별 또는 미식별이 보류 중이거나 보류 중이 아님으로 확인된 인벤토리에 포함된 소프트웨어, 소프트웨어 범주 및 소프트웨어 제품군의 개수 및 백분율입니다. 각각에 대 한 백분율을 표시 하는 차트에 표시 되는 정보 및 테이블 형식으로 표시 되는 정보는 각각에 대해 개수를 보여줍니다.  



## <a name="BKMK_AssetIntelligenceReports"></a> Asset Intelligence 보고서  

Asset Intelligence 보고서는 Configuration Manager 콘솔, **모니터링** 작업 영역, **보고** 노드 아래의 **Asset Intelligence** 폴더에 있습니다. 보고서는 하드웨어, 라이선스 관리 및 소프트웨어에 대한 정보를 제공합니다. Configuration Manager의 보고서에 대한 자세한 내용은 [보고](/sccm/core/servers/manage/reporting)를 참조하세요.  

> [!NOTE]  
> Asset Intelligence 보고서에 표시되는 설치된 소프트웨어 타이틀 및 라이선스 정보의 정확한 양은 환경에서 사용되는 라이선스 또는 설치된 소프트웨어 타이틀의 실제 수와 다를 수 있습니다. 이 차이는 엔터프라이즈 환경에 설치된 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보의 인벤토리 작성과 관련된 복잡한 종속성과 제한 사항 때문입니다. 구입한 소프트웨어 라이선스 규정 준수를 결정하려면 Asset Intelligence 보고서를 유일한 소스로 사용하지 마세요.  


### <a name="BKMK_HardwareReports"></a> 하드웨어 보고서  

Asset Intelligence 하드웨어 보고서는 조직의 하드웨어 자산에 대한 정보를 제공합니다. Asset Intelligence 하드웨어 보고서에서는 속도, 메모리 및 주변 디바이스와 같은 하드웨어 인벤토리 정보를 사용하여 USB 디바이스, 업그레이드해야 하는 하드웨어 및 특정 소프트웨어 업그레이드에 대해 준비가 되지 않은 컴퓨터에 대한 정보까지 제공할 수 있습니다.  

> [!NOTE]  
> Asset Intelligence 하드웨어 보고서의 일부 사용자 데이터는 Windows 보안 이벤트 로그에서 수집됩니다. 더 정확한 보고서를 위해서는 컴퓨터를 새 사용자에게 재할당할 때 이 로그를 지웁니다.  


### <a name="BKMK_LicenseManagementReports"></a> 라이선스 관리 보고서  

Asset Intelligence 라이선스 관리 보고서는 사용 중인 라이선스에 대한 데이터를 제공합니다. **라이선스 원장** 보고서에서는 MLS(Microsoft 라이선스 계정)와 일치하는 형식으로 설치된 Microsoft 애플리케이션을 나열합니다. 이 형식은 획득한 라이선스와 사용된 라이선스를 일치시키는 편리한 방법을 제공합니다. 다른 라이선스 관리 보고서에서는 Windows 정품 인증 통계에 대해 KMS(키 관리 서비스)를 실행하는 서버로 사용되는 컴퓨터에 대한 정보를 제공합니다.  

> [!IMPORTANT]  
> Asset Intelligence 라이선스 관리 보고서 중 몇 가지는 볼륨 라이선스를 관리하는 방법인 KMS의 기능에 대한 정보를 제공합니다. KMS 서버가 구현되지 않은 경우 일부 보고서는 데이터를 반환하지 않을 수 있습니다.  


### <a name="BKMK_SoftwareReports"></a> 소프트웨어 보고서  

Asset Intelligence 소프트웨어 보고서는 조직의 컴퓨터에 설치된 소프트웨어 제품군, 범주 및 특정 소프트웨어 타이틀에 대한 정보를 제공합니다. 소프트웨어 보고서는 브라우저 도우미 개체 및 자동으로 시작하는 소프트웨어와 같은 정보를 제공합니다. 이러한 보고서는 애드웨어, 스파이웨어 및 기타 맬웨어를 식별하는 데 사용할 수 있습니다. 소프트웨어 취득 및 지원을 간소화하려면 이러한 보고서를 사용하여 소프트웨어 중복을 식별할 수도 있습니다.  


### <a name="BKMK_SoftwareIdTagReports"></a> 소프트웨어 ID 태그 보고서  

Asset Intelligence 소프트웨어 ID 태그 보고서는 ISO/IEC 19770-2와 호환되는 소프트웨어 ID 태그가 포함된 소프트웨어에 대한 정보를 제공합니다. 소프트웨어 ID 태그는 설치된 소프트웨어를 식별 하는 데 사용되는 신뢰할 수 있는 정보를 제공합니다. **SMS_SoftwareTag** 하드웨어 인벤토리 보고 클래스를 사용하도록 설정하면 Configuration Manager에서 소프트웨어 ID 태그가 포함된 소프트웨어에 대한 정보를 수집합니다. 

다음 보고서는 소프트웨어에 대한 정보를 제공합니다.  

- **소프트웨어 14A - 소프트웨어 ID 태그 사용 소프트웨어 검색**: 소프트웨어 ID 태그가 사용하도록 설정된 설치되어 있는 소프트웨어 수  

- **소프트웨어 14B - 특정 소프트웨어 ID 태그 사용 소프트웨어가 설치된 컴퓨터**: 지정한 소프트웨어 ID 태그가 사용하도록 설정된 소프트웨어가 설치되어 있는 모든 컴퓨터  

- **소프트웨어 14C - 특정 컴퓨터의 설치된 소프트웨어 ID 태그 사용 소프트웨어**: 특정 컴퓨터에서 특정 소프트웨어 ID 태그가 사용되는 모든 설치된 소프트웨어  


### <a name="BKMK_ReportingLImitations"></a> 보고 제한 사항  

Asset Intelligence 보고서는 설치된 소프트웨어 타이틀 및 사용 중인 획득한 소프트웨어 라이선스에 대한 많은 정보를 제공할 수 있습니다. 획득한 소프트웨어 라이선스 규정 준수를 확인하려면 유일한 소스로 이 정보를 사용하지 마세요.  

#### <a name="BKMK_ExampleDependencies"></a> 종속성 예  
설치된 소프트웨어 타이틀 및 라이선스 정보에 대해 Asset Intelligence 보고서에 표시된 정확한 양은 현재 사용되는 실제 양과 다를 수 있습니다. 이러한 차이는 엔터프라이즈 환경에서 사용 중인 소프트웨어 타이틀에 대한 소프트웨어 라이선스 정보의 인벤토리 작성과 관련된 복잡한 종속성으로 인해 발생합니다. 다음 예제에서는 Asset Intelligence 보고서의 정확도에 영향을 줄 수 있는 Asset Intelligence를 사용하여 엔터프라이즈의 설치된 소프트웨어 인벤토리 작성과 관련된 종속성을 보여줍니다.  

- **클라이언트 하드웨어 인벤토리 종속성**: Asset Intelligence의 설치된 소프트웨어 보고서는 Asset Intelligence 보고를 사용할 수 있도록 하드웨어 인벤토리를 확장하여 Configuration Manager 클라이언트에서 수집된 데이터를 기반으로 합니다. 하드웨어 인벤토리 보고에 대한 이 종속성으로 인해 Asset Intelligence 보고서는 필수 Asset Intelligence WMI 보고 클래스를 사용하도록 설정한 하드웨어 인벤토리 프로세스를 완료하는 클라이언트의 데이터만 반영합니다. Configuration Manager 클라이언트는 관리자가 정의한 일정에 따라 하드웨어 인벤토리 프로세스를 수행하기 때문에 Asset Intelligence 보고서의 정확도가 영향을 주는 데이터 보고 지연이 발생할 수 있습니다. 

    예를 들어 클라이언트가 성공적으로 하드웨어 인벤토리 주기를 종료한 후 인벤토리에 포함된 사용이 허가된 소프트웨어 타이틀이 제거될 수도 있습니다. 다음에 예약된 클라이언트의 하드웨어 인벤토리 보고 주기 때까지는 Asset Intelligence 보고서에 소프트웨어 타이틀이 설치된 것으로 표시됩니다.  

- **소프트웨어 패키징 종속성**: Asset Intelligence 보고서는 표준 Configuration Manager 클라이언트 하드웨어 인벤토리 프로세스를 사용하여 수집되는 설치된 소프트웨어 타이틀 데이터를 기반으로 합니다. 따라서 일부 소프트웨어 타이틀 데이터가 올바르게 수집되지 않을 수 있습니다. 정확하지 않은 Asset Intelligence 보고를 발생시킬 수 있는 예제:  

    - 표준 설치 프로세스를 준수하지 않는 소프트웨어 설치  

    - 설치 전에 변경된 소프트웨어 설치   

#### <a name="BKMK_LegalLimitations"></a> 법적 제한 사항  
Asset Intelligence 보고서에 표시되는 정보는 많은 제한을 받습니다. Asset Intelligence 보고서에 표시되는 정보는 법률, 회계 또는 기타 전문가 조언이 아닙니다. Asset Intelligence 보고서에서 제공된 정보는 정보용으로만 사용합니다. 소프트웨어 라이선스 사용 규정 준수를 확인하려면 유일한 소스로 이 정보를 사용하지 마세요.  

보고서의 정확도에 영향을 줄 수 있는 Asset Intelligence를 사용하는 예제에는 다음과 같은 제한 사항이 있습니다.  

- **Microsoft 라이선스 사용 수량 제한**:  

    - 획득한 Microsoft 소프트웨어 라이선스의 수량은 관리자가 제공하는 정보에 따릅니다. 이 정보를 자세히 검토하여 올바른 수의 소프트웨어 라이선스가 제공되었는지 확인합니다.  

    - 보고된 Microsoft 소프트웨어 라이선스 수량에는 볼륨 라이선스 프로그램을 통해 획득한 Microsoft 소프트웨어 라이선스 정보만 포함되며, 소매, OEM 또는 기타 소프트웨어 라이선스 판매 채널을 통해 획득한 소프트웨어 라이선스에 대한 정보는 반영되지 않습니다.  

    - 지난 45일 이내에 획득한 소프트웨어 라이선스는 소프트웨어 재판매인 보고 요구 사항 및 일정으로 인해 보고된 Microsoft 소프트웨어 라이선스의 수량에 포함되지 않을 수 있습니다.  

    - 기업 합병 또는 인수로 인한 소프트웨어 라이선스 양도는 Microsoft 소프트웨어 라이선스 수량에 반영되지 않을 수 있습니다.  

    - MVLS(Microsoft 볼륨 라이선스) 계약의 표준이 아닌 사용 약관은 보고되는 소프트웨어 라이선스에 영향을 줄 수 있습니다. 따라서 Microsoft 담당자가 추가로 검토해야 할 수 있습니다.  

- **설치된 소프트웨어 타이틀 수량 제한**: Asset Intelligence 보고서가 설치된 소프트웨어 타이틀의 수량을 정확히 보고하려면 Configuration Manager 클라이언트가 하드웨어 인벤토리 보고 주기를 완료해야 합니다. 성공적인 하드웨어 인벤토리 보고 주기 후 사용이 허가된 소프트웨어 타이틀의 설치 또는 제거 사이에 지연이 있을 수 있습니다. 클라이언트가 예약된 다음 하드웨어 인벤토리를 보고하기 전에 실행된 Asset Intelligence 보고서에 이 작업이 반영되지 않을 수 있습니다.  

- **라이선스 조정 제한**: 획득한 소프트웨어 라이선스 수량과 설치된 소프트웨어 타이틀 수량 간의 조정은 관리자가 지정한 라이선스 수량과 관리자가 설정한 일정에 따라 Configuration Manager 클라이언트 하드웨어 인벤토리에서 수집된 설치되어 있는 소프트웨어 타이틀 수량을 비교하여 계산합니다. 이 비교가 라이선스 입장에 대한 Microsoft의 최종 결론은 아닙니다. 사용 조건에 의해 부여 된 특정 소프트웨어 타이틀 라이선스 및 사용 권한에서 실제 라이선스 위치에 따라 달라 집니다.  



## <a name="BKMK_ValidationStates"></a> Asset Intelligence 유효성 검사 상태  

Asset Intelligence 유효성 검사 상태는 Asset Intelligence 카탈로그 정보의 소스 및 현재 유효성 검사 상태를 나타냅니다. 다음 테이블에는 가능한 Asset Intelligence 유효성 검사 상태와 이러한 상태를 발생시킬 수 있는 관리자 작업이 표시됩니다.  

| 시스템 상태 | 정의 | 관리자 작업 | 설명 |  
|---------------|--------------------|------------------------------|-----------------|  
|**유효성 검사됨**|Microsoft 연구원이 카탈로그 항목 정의|없음|최상의 상태|  
|**사용자 정의됨**|Microsoft 연구원이 카탈로그 항목 정의하지 않음|로컬 카탈로그 정보 사용자 지정|이 상태는 Asset Intelligence 보고서에 표시됨|  
|**보류 중**|Microsoft 연구원이 카탈로그 항목을 정의하지 않았지만 사용자는 분류를 위해 Microsoft에 항목을 제출함|분류 요청 뒤 추가 작업 없음|카탈로그 항목은 Microsoft 연구원이 항목을 분류하고 사용자가 자신의 Asset Intelligence 카탈로그를 동기화할 때까지 이 상태로 유지됨|  
|**업데이트 가능**|사용자 정의된 카탈로그 항목이 카탈로그 동기화 중 Microsoft에서 다르게 분류되었습니다.|**충돌 해결** 작업을 사용하여 새 분류 정보를 사용할지 아니면 이전 사용자 정의 값을 사용할지 여부를 결정합니다. 충돌을 해결하는 방법에 대한 자세한 내용은 [Asset Intelligence 작업](/sccm/core/clients/manage/asset-intelligence/operations-for-asset-intelligence)을 참조하세요.|분류 충돌이 해결되면 이후 분류 업데이트에서 항목에 대한 새 정보를 도입하지 않는 경우 항목이 충돌하는 것으로 다시 확인되지 않습니다.|  
|**범주화되지 않음**|카탈로그 항목이 Microsoft 연구원에 의해 정의되지 않았고, 항목이 분류를 위해 Microsoft에 제출되지 않았으며, 관리자가 사용자 정의 분류 값을 할당하지 않았습니다.|분류를 요청하거나 로컬 카탈로그 정보를 사용자 지정합니다. 자세한 내용은 [Asset Intelligence 작업](/sccm/core/clients/manage/asset-intelligence/operations-for-asset-intelligence)을 참조하세요.|없음|  

> [!NOTE]  
> 분류를 위해 Microsoft에 제출한 카탈로그 항목은 중앙 관리 사이트에서 유효성 검사 상태가 **보류 중** 이지만 하위 기본 사이트에서는 유효성 검사 상태가 **범주화되지 않음**으로 계속 표시됩니다.  

유효성 검사 상태가 한 상태에서 다른 상태로 전환될 수 있는 경우의 예제는 [Asset Intelligence의 유효성 검사 상태 전환 예제](/sccm/core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence)를 참조하세요.  
