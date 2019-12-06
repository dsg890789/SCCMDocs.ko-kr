---
title: 보고에 대한 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 보고를 사용하는 데 영향을 주는 다양한 종속성을 이해합니다.
ms.date: 01/29/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 226a2632f8aa827975a764f0d22aea0a05ec6d96
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70379761"
---
# <a name="prerequisites-for-reporting-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 보고에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 보고에는 외부 종속성과 제품 내 종속성이 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  
 다음 표에는 보고에 대한 외부 종속성이 나열되어 있습니다.  

|필수 구성 요소|추가 정보|  
|------------------|----------------------|  
|SQL Server Reporting Services|Configuration Manager에서 보고를 사용하려면 먼저 SQL Server Reporting Services를 설치하고 구성해야 합니다.<br /><br /> 현재 환경에서 보고 서비스를 계획 및 배포하는 방법에 대한 자세한 내용은 SQL Server 2008 Books Online에서 [SQL Server Reporting Services](https://go.microsoft.com/fwlink/p/?LinkId=212032) 섹션을 참조하십시오.|  
|보고 서비스 지점을 실행하는 컴퓨터에 대한 사이트 시스템 역할 종속성|[System Center Configuration Manager에서 지원되는 구성](../../../core/plan-design/configs/supported-configurations.md)|  

## <a name="dependencies-internal-to-configuration-manager"></a>Configuration Manager 내부 종속성  
 다음 표에는 Configuration Manager의 보고에 대한 종속성이 나열되어 있습니다.  

|필수 구성 요소|추가 정보|  
|------------------|----------------------|  
|보고 서비스 지점|Configuration Manager에서 보고를 사용하려면 먼저 보고 서비스 지점 사이트 시스템 역할을 구성해야 합니다. 보고 서비스 지점을 설치하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 구성](../../../core/servers/manage/configuring-reporting.md)을 참조하세요.|  

## <a name="supported-sql-server-versions-for-the-reporting-services-point"></a>보고 서비스 지점에 대해 지원되는 SQL Server 버전  
 보고 서비스 데이터베이스는 64비트 SQL Server 설치의 기본 인스턴스 또는 명명된 인스턴스에 설치할 수 있습니다. SQL Server 인스턴스는 사이트 시스템 서버와 함께 배치하거나 원격 컴퓨터에 배치할 수 있습니다.  

 다음 표에서는 보고 서비스 지점에서 지원되는 SQL Server 버전을 보여 줍니다.  

|SQL Server 버전|보고 서비스 지점|  
|------------------------|------------------------------|
|누적 업데이트 2 이상이 설치된 SQL Server 2017<br /><br /> -   Standard<br />-   Enterprise|예, Configuration Manager 버전 1710부터 시작|  
|SQL Server 2016 SP1<br /><br /> -   Standard<br />-   Enterprise|예| 
|SQL Server 2016<br /><br /> -   Standard<br />-   Enterprise|예|
|SQL Server 2014 with SP2<br /><br /> -   Standard<br />-   Enterprise|예|
|SQL Server 2014 with SP1<br /><br /> -   Standard<br />-   Enterprise|예|
|SQL Server 2012 with SP4 <br /><br /> -   Standard<br />-   Enterprise|예|  
|SQL Server 2012 with SP3 <br /><br /> -   Standard<br />-   Enterprise|예|  
|SQL Server 2008 R2 with SP3<br /><br /> -   Standard<br />-   Enterprise<br />-   Datacenter|예, 1702 이전의 Configuration Manager 지원 버전의 경우입니다.|  
|SQL Server Express 2008 R2 with SP3|지원 안 됨| 




## <a name="next-steps"></a>다음 단계
[보고 작업 및 유지 관리](operations-and-maintenance-for-reporting.md)
