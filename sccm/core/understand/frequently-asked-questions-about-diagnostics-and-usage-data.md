---
title: "진단 데이터에 대한 FAQ"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에 대한 진단 및 사용 현황 데이터에 대한 질문과 대답을 찾습니다."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: "6"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 43e67262ce2b22e604f5b6d3ff1971921cd82637
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2017
---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 진단 및 사용 현황 데이터에 대한 질문과 대답

*적용 대상: System Center Configuration Manager(현재 분기)*

다음은 System Center Configuration Manager에 대한 진단 및 사용 현황 데이터에 대한 질문과 대답입니다.  

###  <a name="bkmk_off"></a> 원격 분석을 해제하려면 어떻게 할까요?  
원격 분석은 해제할 수 없습니다. 그러나 수집되는 원격 분석 데이터의 수준을 선택할 수는 있습니다. 서비스 연결 지점을 오프라인 모드로 사용하여 원격 분석 데이터의 제출 시기를 관리할 수도 있습니다.

현재 분기의 Configuration Manager는 새 버전의 Windows 10 및 Microsoft Intune을 지원하도록 정기적으로 업데이트해야 합니다. Microsoft에서 제품을 최신 상태로 유지하고 업데이트 환경을 개선하고 제품의 품질 및 보안을 개선하려면 최소한 기본 수준의 진단 및 사용 현황 데이터가 필요합니다.

###  <a name="bkmk_retention"></a> 데이터 보존 기간이란 무엇인가요?  
 진단 및 사용 현황 데이터는 1년 동안 보존됩니다.  

###  <a name="bkmk_update"></a> 제품을 설치하거나 업데이트할 때 진단 및 사용 현황 데이터가 전송되나요?  
 아니요. 진단 및 사용 현황 데이터는 사이트가 설치되고 작동하는 후에만 전송됩니다.  

###  <a name="bkmk_frequency"></a> 데이터는 얼마나 자주 전송되나요?  
 SQL 저장 프로시저는 7일마다 실행됩니다(사이트가 설치된 날짜로부터). 온라인 모드에서 서비스 연결 지점은 쿼리가 실행된 후 데이터를 업로드하도록 구성됩니다. 오프라인 모드에서 관리자는 서비스 연결 도구를 사용하여 데이터를 업로드합니다. 사이트를 설치한 후 7일이 될 때까지는 데이터를 오프라인에서 사용할 수 없습니다.  

###  <a name="bkmk_network"></a> 네트워크 맵을 만드는 데 데이터를 사용할 수 있나요?  
 System Center Configuration Manager에 대한 진단 사용 현황 데이터 수집의 수준의 설명과 같이 사이트 세부 정보에는 각 사이트의 표준 시간대 정보가 포함됩니다. 이 정보로 특정 계층의 사이트에 대한 광범위한 지리적 위치 및 계층의 글로벌 분산에 대한 통찰력을 제공할 수 있습니다. 그러나 IP 주소나 자세한 지리적 정보와 같은 네트워크 세부 정보는 수집되지 않습니다.
 - [1511에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
 - [1602에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
 - [1606에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)
 - [1610에 대한 진단 데이터](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)


###  <a name="bkmk_tables"></a> 사용자 지정 테이블의 데이터를 볼 수 있나요?  
 아니요. SQL 저장 프로시저를 통해 데이터베이스의 기본 제품 테이블에 대한 진단 및 사용 현황 데이터가 수집됩니다(접두사가 **TEL_**인 모든 항목). SQL 스키마 검색 쿼리의 일부로, 알려진 기본값과 비교할 수 있도록 모든 테이블 이름이 해시됩니다. 따라서 사용자 지정 테이블이 데이터베이스에 존재하지만(데이터베이스 스키마가 기본에서 확장되었음) 해당 테이블 내에 데이터를 포함하지 않는지를 확인할 수 있습니다.  

###  <a name="bkmk_databases"></a> 다른 데이터베이스의 이름 또는 다른 데이터베이스의 데이터를 볼 수 있나요?  
 아니요. 데이터를 수집하는 저장 프로시저는 사이트 데이터베이스로 제한됩니다.  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager의 진단 및 사용 현황 데이터](../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)
