---
title: "설치 참조 | System Center Configuration Manager"
description: "Configuration Manager 사이트 또는 계층 구조의 설치를 준비하려면 이 참조를 검토합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdb9fb0c-0912-41e4-b427-f40620971763
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 06bab7e01fee2c0b030a2879fa67fd455bf668fe


---
# <a name="reference-for-system-center-configuration-manager-setup"></a>System Center Configuration Manager 설치에 대한 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 설치 프로그램은 다음 섹션에 자세히 설명된 여러 항목에 대한 링크를 제공합니다. 다음 섹션의 정보는 Configuration Manager 사이트 또는 계층 구조의 설치를 준비하고 설치 중에 결정해야 하는 몇 가지 사항을 준비하는 데 도움이 되는 다음 섹션에 대한 링크를 제공합니다.  

-   [시작하기 전에](#bkmk_start)  

-   [서버 준비 상태 평가](#bkmk_assess)  

-   [추가 운영 체제에 대한 클라이언트](#bkmk_Addclients)  

-   [System Center Configuration Manager의 진단 및 사용 현황 데이터](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)  

##  <a name="a-namebkmkstarta-before-you-begin"></a><a name="bkmk_start"></a> 시작하기 전에  
 Configuration Manager 사이트를 새로 설치하기 전에 성공적인 배포 디자인을 준비하는 데 유용한 다음 정보를 검토해야 합니다.  

-   [System Center Configuration Manager의 기본 사항](../../../../core/understand/fundamentals.md)  

-   [System Center Configuration Manager 인프라 계획](../../../plan-design/network/configure-firewalls-ports-domains.md)  

-   [System Center Configuration Manager 사이트 설치 준비](prepare-to-install-sites.md)  

##  <a name="a-namebkmkassessa-assess-server-readiness"></a><a name="bkmk_assess"></a> 서버 준비 상태 평가  
 새 사이트 설치를 시작하기 전에 사이트에 사용하려는 사이트 서버 및 원격 사이트 시스템 서버(예: 사이트 데이터베이스를 호스트하는 서버)가 모든 필수 조건 구성을 충족하는지 확인합니다. 문서 라이브러리의 다음 항목을 활용할 수 있습니다.  

-   [System Center Configuration Manager에서 지원되는 구성](../../../../core/plan-design/configs/supported-configurations.md)  

-   [필수 구성 요소 검사기](https://technet.microsoft.com/library/mt590813.aspx#bkmk_PreqChk)  

##  <a name="a-namebkmkaddclientsa-clients-for-additional-operating-systems"></a><a name="bkmk_Addclients"></a> 추가 운영 체제에 대한 클라이언트  
 Microsoft 다운로드 센터에서 다음 운영 체제에 대한 Configuration Manager용 클라이언트 소프트웨어를 다운로드할 수 있습니다.  

-   Mac(Apple)  

-   UNIX  

-   Linux  

**사용하는 Configuration Manager 버전용 클라이언트를 다운로드하려면 다음 링크를 사용합니다.**  

-   [System Center Configuration Manager(현재 분기)](http://www.microsoft.com/download/details.aspx?id=47719)  

-   [System Center 2012 R2 Configuration Manager SP1 및 System Center 2012 Configuration Manager SP2](http://go.microsoft.com/fwlink/?LinkID=626550)  

-   [System Center 2012 R2 Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=316448)  

-   [System Center 2012 Configuration Manager SP1](http://www.microsoft.com/en-pk/download/details.aspx?id=36212)  

##  <a name="a-namebkmkusagea-usage-data-levels-and-settings"></a><a name="bkmk_usage"></a> 사용 현황 데이터 수준 및 설정  
System Center Configuration Manager 사이트를 처음 설치하는 경우 자동으로 설치되고 사이트 서버에 새 사이트 시스템 역할이 구성되며 **서비스 연결 지점**이 다음과 같은 기본 설정으로 구성됩니다.  

-   **온라인** 모드(오프 라인 모드도 지원됨)  

-   **확장** 데이터 수집 수준(다른 두 데이터 수집 수준인 기본과 전체도 지원됨)  

이 역할이 온라인 상태이면 Microsoft에서 인터넷을 통해 진단 및 사용 정보를 자동으로 수집할 수 있습니다. 수집된 정보는 다음 작업에 도움이 됩니다.  

-   문제 식별 및 해결  

-   제품 및 서비스 개선  

-   사용하는 버전의 Configuration Manager에 적용되는 Configuration Manager 업데이트 식별  

데이터 컬렉션의 세 가지 수준은 다음과 같습니다.  

-   **기본** - 사이트 수, 사용하도록 설정된 Configuration Manager 기능 등의 설치 및 업그레이드 관련 데이터가 포함됩니다. 개인 식별이 가능한 정보는 전송되지 않습니다.  

-   **확장** - 기본 설정의 데이터와 함께 계층, 각 기능을 사용하는 방법(빈도/기간) 및 확장된 진단 정보(예: 시스템 또는 앱 작동 중단 발생 시의 서버 메모리 상태)에 대한 데이터를 전송합니다. 개인 식별이 가능한 데이터는 전송되지 않습니다.  

-   **전체** - 기본 및 확장 설정의 데이터와 함께 시스템 파일, 시스템 스냅숏 등의 고급 진단 정보도 전송됩니다. 이 옵션을 선택하는 경우 개인 식별이 가능한 정보가 포함될 수도 있지만 Microsoft는 해당 정보를 토대로 사용자를 식별하거나 사용자에게 연락을 하지 않으며 사용자를 대상으로 하는 광고를 전송하지도 않습니다.  

각 수준별로 수집되는 정보의 공개를 비롯한 자세한 내용은 [System Center Configuration Manager의 진단 및 사용 현황 데이터](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)를 참조하세요.  

[System Center Configuration Manager 개인 정보 취급 방침](http://go.microsoft.com/fwlink/?LinkID=626527)



<!--HONumber=Nov16_HO1-->


