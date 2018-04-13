---
title: 진단 및 사용 현황 데이터
titleSuffix: Configuration Manager
description: System Center Configuration Manager가 수집하는 자체 진단 및 사용 현황 데이터에 대해 알아봅니다.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: 9
caps.handback.revision: 0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5f783f11f6fbabda2fd1d6f98748e945affa878e
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2018
---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>System Center Configuration Manager의 진단 및 사용 현황 데이터

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서는 진단 및 사용 현황 데이터를 수집하며, 이러한 데이터는 Microsoft에서 향후 버전의 설치 환경, 품질 및 보안을 개선하기 위해 사용됩니다.  

 진단 및 사용 현황 데이터는 각 Configuration Manager 계층 구조에 대해 사용할 수 있습니다. 각 기본 사이트 및 중앙 관리 사이트에서 매주 실행되는 SQL Server 쿼리로 구성됩니다. 계층에서 중앙 관리 사이트를 사용하면 기본 사이트의 데이터가 해당 사이트에 복제됩니다. 계층의 최상위 사이트에서, 서비스 연결 지점은 업데이트를 확인할 때 이 정보를 제출합니다. 서비스 연결점이 오프라인 모드인 경우 서비스 연결 도구를 사용하여 정보가 전송됩니다.  

> [!NOTE]  
>  Configuration Manager는 사이트 SQL Server 데이터베이스에서만 데이터를 수집하고 클라이언트 또는 사이트 서버에서 직접 데이터를 수집하지 않습니다.  

 자세한 내용은 [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkID=626527)을 참조하세요.  

## <a name="articles"></a>문서
 다음 문서의 Configuration Manager에 대한 진단 및 사용 현황 데이터에 대해 자세히 알아봅니다.  

-   [진단 및 사용 현황 데이터 사용 방법](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   진단 사용 현황 데이터 수집의 수준:
    - [1802에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1802)  
    - [1710에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1710)  
    - [1706에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1706)    

<!--
    - [Diagnostic data for 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Diagnostic data for 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Diagnostic data for  1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [진단 및 사용 현황 데이터 수집 방법](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [진단 및 사용 현황 데이터를 보는 방법](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [CEIP(사용자 환경 개선 프로그램)](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

     > [!Note]  
     > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.


-   [진단 및 사용 현황 데이터에 대한 질문과 대답](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>참고 항목  
 [서비스 연결 지점 정보](../../../core/servers/deploy/configure/about-the-service-connection-point.md)
