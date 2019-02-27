---
title: 제품 수명 주기 대시보드
titleSuffix: Configuration Manager
description: Configuration Manager의 제품 수명 주기 대시보드를 사용하여 Microsoft 수명 주기 정책을 봅니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8b5b144a-0e5f-4fcc-87b2-33b9bcdb5655
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 716c5218eafaf6297292fdd852589b7327e2ecaa
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56120030"
---
# <a name="manage-microsoft-lifecycle-policy-with-configuration-manager"></a>Configuration Manager로 Microsoft 수명 주기 정책 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1806부터 Configuration Manager 제품 수명 주기 대시보드를 사용하여 Microsoft 수명 주기 정책을 볼 수 있습니다. 대시보드에는 Configuration Manager로 관리되는 디바이스에 설치된 Microsoft 제품에 대한 Microsoft 수명 주기 정책의 상태가 표시됩니다. 또한 사용자 환경의 Microsoft 제품, 지원 가능성 상태 및 지원 종료 날짜에 대한 정보도 제공합니다. 대시보드를 사용하여 각 제품에 대한 지원 가용성을 파악합니다. 이 정보는 현재 지원 종료에 도달하기 전에 사용하는 Microsoft 제품을 업데이트할 시기를 계획하는 데 도움이 됩니다.  

자세한 내용은 [Microsoft 수명 주기 정책](https://support.microsoft.com/lifecycle)을 참조하세요.

1810 버전부터 대시보드에는 System Center 2012 Configuration Manager 이상에 대한 정보가 포함되어 있습니다.<!--1358702-->  



## <a name="prerequisites"></a>필수 구성 요소 

 제품 수명 주기 대시보드에서 데이터를 보려면 다음 구성 요소가 필요합니다.  

- Configuration Manager 콘솔을 실행하는 컴퓨터에 Internet Explorer 9 이상이 설치되어 있어야 합니다.  

- 대시보드에서 하이퍼링크가 작동하려면 보고 서비스 지점이 필요합니다. 대시보드는 SSRS(SQL Server Reporting Services) 보고서에 연결됩니다. 자세한 내용은 [Configuration Manager의 보고 기능](/sccm/core/servers/manage/reporting)을 참조하세요.  

- Asset Intelligence 동기화 지점을 구성하고 동기화해야 합니다. 대시보드는 Asset Intelligence 카탈로그를 제품 제목의 메타데이터로 사용합니다. 메타데이터는 계층 구조의 인벤토리 데이터와 비교됩니다. 자세한 내용은 [Configuration Manager에서 Asset Intelligence 구성](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence)을 참조하세요.  

     > [!NOTE]  
     > Asset Intelligence 서비스 지점을 처음 구성하는 경우 [Asset Intelligence 하드웨어 인벤토리 클래스를 사용하도록 설정](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence#BKMK_EnableAssetIntelligence)해야 합니다. 수명 주기 대시보드는 이러한 Asset Intelligence 하드웨어 인벤토리 클래스에 따라 달라집니다. 대시보드는 클라이언트가 하드웨어 인벤토리를 검색하고 반환할 때까지 데이터를 표시하지 않습니다.  



## <a name="use-the-product-lifecycle-dashboard"></a>제품 수명 주기 대시보드 사용

사이트가 관리 디바이스에서 수집한 인벤토리 데이터를 기반으로 대시보드에 모든 현재 제품에 대한 정보가 표시됩니다. 그러나 운영 체제 및 SQL Server에 대해 표시되는 정보는 다음 버전으로 제한됩니다.

- Windows Server 2008 이상
- Windows XP 이상
- SQL Server 2008 이상

Configuration Manager 콘솔에서 수명 주기 대시보드에 액세스하려면 **자산 및 호환성** 작업 영역으로 이동하여 **Asset Intelligence**를 펼쳐서 **제품 수명 주기** 노드를 선택합니다.

> [!NOTE]  
> 대시보드의 데이터는 Configuration Manager 콘솔이 연결되는 사이트를 기반으로 합니다. 콘솔이 최상위 계층 사이트에 연결되는 경우 전체 계층 구조에 대한 데이터가 표시됩니다. 자식 기본 사이트에 연결되는 경우 해당 사이트의 데이터만 표시됩니다.

### <a name="product-lifecycle-dashboard"></a>제품 수명 주기 대시보드

![콘솔의 제품 수명 주기 대시보드 스크린샷](media/product-lifecycle-dashboard.png)

**제품 범주** 목록에서 다음 옵션 중 하나를 선택하여 보기를 변경합니다.  
- **모두**: 모든 제품을 함께 표시합니다.  
- **Windows 클라이언트**: Windows 클라이언트 OS 버전을 표시합니다.  
- **Windows Server**: Windows Server OS 버전을 표시합니다.  
- **데이터베이스**: SQL Server 버전 보기  
- **Configuration Manager**: 1810 버전부터 Configuration Manager 버전을 표시합니다.  

이 대시보드에는 다음과 같은 타일에 있습니다.  

- **수명이 종료된 상위 5개 제품:**  이 타일은 사용자 환경에서 찾은 수명이 종료된 제품의 통합 데이터 뷰입니다. 그래프는 운영 체제 및 SQL Server 제품에 대한 지원 수명 주기를 기준으로 만료된, 설치된 소프트웨어를 보여 줍니다.  

- **수명이 종료되는 상위 5개 제품:**  이 타일은 사용자 환경에서 찾은, 앞으로 18개월 이내에 수명이 종료되는 제품의 통합 데이터 뷰입니다. 그래프는 운영 체제 및 SQL Server 제품에 대한 지원 수명 주기를 기준으로 18개월 이내에 수명이 종료되는, 설치된 소프트웨어를 보여 줍니다.  

- **설치된 제품에 대한 수명 주기 데이터:**  이 타일은 제품이 지원됨 상태에서 만료됨 상태로 전환되는 시기를 일반적으로 설명합니다. 차트는 제품이 설치된 클라이언트 수의 분류, 지원 가용성 상태 및 다음에 수행할 단계에 대해 자세히 알아볼 수 있는 링크를 제공합니다. 차트에는 다음 정보가 포함됩니다.     
    - 남은 지원 시간
    - 환경의 클라이언트 수 
    - 일반 지원 종료 날짜
    - 추가 지원 종료 날짜
    - 다음 단계  

> [!IMPORTANT]  
> 이 대시보드에 표시된 정보는 편의를 위해 제공되며, 회사 내에서 내부적으로만 사용해야 합니다. 따라서 준수를 확인하기 위해 이 정보에만 의존해서는 안 됩니다. [Microsoft 수명 주기 정책](https://support.microsoft.com/lifecycle)을 방문하여 제공된 정보가 정확하고 지원 정보를 사용할 수 있는지 확인해야 합니다.  



## <a name="reporting"></a>보고

추가 보고서도 제공됩니다. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **보고**를 펼치고 **보고서**를 펼칩니다. 다음 보고서가 **Asset Intelligence** 범주에 새로 추가되었습니다.  

- **수명 주기 01A - 특정 소프트웨어 제품이 있는 컴퓨터**: 지정한 제품이 검색된 컴퓨터 목록을 표시합니다.  

- **수명 주기 02A - 조직에서 만료된 제품이 있는 머신의 목록**: 만료된 제품이 있는 컴퓨터를 표시합니다. 이 보고서는 제품 이름으로 필터링할 수 있습니다.

- **수명 주기 03A - 조직에 있는 만료된 제품의 목록**: 현재 환경에서 수명 주기 날짜가 만료된 제품에 대한 세부 정보를 표시합니다.  

- **수명 주기 04A - 일반적인 제품 수명 주기 개요**: 제품 수명 주기 목록을 표시합니다. 제품 이름과 만료일별로 목록을 필터링합니다.  

- **수명 주기 05A - 제품 수명 주기 대시보드**: 1810 버전부터 이 보고서에는 콘솔 내 대시보드와 비슷한 정보가 포함됩니다. 사용자 환경의 제품 개수 및 남은 지원 기간을 표시하려면 범주를 선택합니다.  

자세한 내용은 [보고서 목록](/sccm/core/servers/manage/list-of-reports#asset-intelligence)을 참조하세요.<!--SCCMDocs issue 997-->  
