---
title: 진단 및 사용량 데이터 FAQ
titleSuffix: Configuration Manager
description: System Center Configuration Manager에 대한 진단 및 사용 현황 데이터에 대한 질문과 대답을 찾습니다.
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b4174c68d5a6ccd31355d976b7830b6d09f39d91
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 진단 및 사용 현황 데이터에 대한 질문과 대답

*적용 대상: System Center Configuration Manager(현재 분기)*

이 아티클에서는 Configuration Manager의 진단 및 사용량 데이터에 대해 자주 묻는 질문에 대한 대답을 제공합니다.

## <a name="faqs"></a>FAQ(질문과 대답)

###  <a name="bkmk_off"></a> 원격 분석을 해제하려면 어떻게 할까요?  
원격 분석은 해제할 수 없습니다. 그러나 수집되는 원격 분석 데이터의 수준을 선택할 수는 있습니다. 원격 분석 데이터가 제출되는 시기를 관리하려면 오프라인 모드에서 서비스 연결 지점을 사용하세요.

현재 분기의 Configuration Manager는 새 버전의 Windows 10 및 Microsoft Intune을 지원하도록 정기적으로 업데이트해야 합니다. Microsoft에서는 기본 수준 이상의 진단 및 사용량 데이터를 필요로 합니다. 이 데이터는 제품을 최신 상태로 유지하고, 업데이트 환경을 개선하고, 제품의 품질 및 보안을 개선하는 데 사용됩니다.

###  <a name="bkmk_retention"></a> 데이터 보존 기간이란 무엇인가요?  
 진단 및 사용 현황 데이터는 1년 동안 저장됩니다.  

###  <a name="bkmk_update"></a> 제품을 설치하거나 업데이트할 때 진단 및 사용 현황 데이터가 전송되나요?  
 아니요. 진단 및 사용 현황 데이터는 사이트가 설치되고 작동하는 후에만 전송됩니다.  

###  <a name="bkmk_frequency"></a> 데이터는 얼마나 자주 전송되나요?  
 SQL 저장 프로시저는 사이트가 설치된 날짜로부터 7일마다 실행됩니다. 온라인 모드에서 서비스 연결 지점은 쿼리가 실행된 후 데이터를 업로드하도록 구성됩니다. 오프라인 모드에서 관리자는 서비스 연결 도구를 사용하여 데이터를 업로드합니다. (사이트를 설치한 후 7일이 될 때까지는 데이터를 오프라인에서 사용할 수 없습니다.)  

###  <a name="bkmk_network"></a> 네트워크 맵을 만드는 데 데이터를 사용할 수 있나요?  
 진단 및 사용량 데이터 수준의 설명과 같이 사이트 세부 정보에는 각 사이트의 표준 시간대 정보가 포함됩니다. 이 정보로 특정 계층의 사이트에 대한 광범위한 지리적 위치 및 계층의 글로벌 분산에 대한 통찰력을 제공할 수 있습니다. 이러한 데이터에 IP 주소, 보다 자세한 지리적 정보 등 네트워크 세부 정보는 포함되지 않습니다. 자세한 내용을 보려면 [진단 및 사용량 데이터 아티클](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data#articles) 목록에서 사용 중인 버전의 진단 및 사용량 데이터 수집 수준을 확인하세요.


###  <a name="bkmk_tables"></a> 사용자 지정 테이블의 데이터를 볼 수 있나요?  
 아니요. Configuration Manager는 SQL 저장 프로시저를 통해 진단 및 사용 현황 데이터를 수집합니다. 이러한 저장 프로시저는 데이터베이스의 기본 제품 테이블에 대해 실행됩니다. 이러한 모든 SQL 테이블의 이름은 **TEL_** 로 시작합니다. SQL 스키마 검색 쿼리의 일부로, 알려진 기본값과 비교할 수 있도록 모든 테이블 이름이 해시됩니다. 이 동작은 데이터베이스에 사용자 지정 테이블이 존재하는지 확인합니다. 사용자 지정 테이블이 있다는 것은 데이터베이스 스키마가 기본값에서 확장되었다는 의미입니다. 해당 테이블 내에 저장된 데이터는 여기에 포함되지 않습니다.  

###  <a name="bkmk_databases"></a> 다른 데이터베이스의 이름 또는 다른 데이터베이스의 데이터를 볼 수 있나요? 
 아니요. 데이터를 수집하는 저장 프로시저는 사이트 데이터베이스로 제한됩니다.  

### <a name="bkmk_gdpr"></a> Configuration Manager에 GDPR(General Data Protection Regulation)이 적용되나요?
 아니요. Configuration Manager는 GDPR 단속 대상이 아닙니다. 사용자가 직접 배포, 관리 및 운영하는 온-프레미스 제품입니다. Microsoft에서 수집하는 진단 및 사용량 데이터는 향후 버전의 설치 환경, 품질 및 보안을 개선하는 데 사용됩니다. 이 데이터는 GDPR 단속 대상입니다. 최종 사용자 식별 정보(EUII) 또는 최종 사용자 가명 식별자(EUPI)는 수집되어 Microsoft에 전송되지 않습니다. GDPR에 대한 자세한 내용은 [GDPR에 대한 Microsoft 보안 센터](https://microsoft.com/gdpr)를 참조하세요. Configuration Manager 데이터에 대한 자세한 내용은 [진단 및 사용량 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조하세요.


## <a name="see-also"></a>참고 항목  
 [진단 및 사용 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)
