---
title: "사용되지 않는 기능 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 더 이상 지원되지 않는 기능, 제품 및 운영 체제에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 0f1e1070fd5b56b1abf22159e9f95b3b4bd8a8c6


---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>System Center Configuration Manager에서 제거되는 기능과 사용되지 않는 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 System Center Configuration Manager에서 이후 지원하지 않거나 업데이트에서 제거될 기능(사용되지 않음), 제품 및 운영 체제에 대해 설명합니다. 이는 Configuration Manager 사용에 영향을 줄 수 있는 향후 변경 사항에 대해 미리 알려드리기 위한 것입니다.  

 이 정보는 이후 릴리스에서 변경될 수 있으며 더 이상 지원되지 않는 각 기능, 제품 및 운영 체제가 누락될 수 있습니다.  

## <a name="deprecated-features-products-and-operating-systems"></a>이후 지원되지 않는 기능, 제품 및 운영 체제  
 이후 지원되지 않는 것으로 나열된 Microsoft 제품 및 운영 체제는 연장하여 지원 중이거나 수명을 다한 것입니다. 이후 지원되지 않는 것으로 나열된 Microsoft 제품 및 운영 체제는 Microsoft 지원 기간을 벗어날 때까지 Configuration Manager의 현재 버전을 사용하여 테스트됩니다.  자세한 내용은 [Microsoft 지원 기간](https://support.microsoft.com/lifecycle) 웹 사이트를 참조하세요.  

 **사용되지 않는 기능:**  


|**기능**|**처음 중단 발표**|**제거된 지원**|  
|-|-|-|  
|NAP(네트워크 액세스 보호) - System Center 2012 Configuration Manager에 있음|7/10/2015|√|  
|대역 외 관리 - System Center 2012 Configuration Manager에 있음|10/16/2015|√|  

 **사용되지 않는 서버 운영 체제:**  

 |**운영 체제**|**처음 중단 발표**|**제거된 지원**|  
|-|-|-|  
|Windows Server 2008|7/10/2015|2016년 12월 31일 이후 출시된 첫 번째 업데이트와 함께 지원 종료(참고 1 참조)|  
|Windows Server 2008 R2|7/10/2015|2016년 12월 31일 이후 출시된 첫 번째 업데이트와 함께 지원 종료(참고 2 참조)|  

-   참고 1: 지원이 종료된 후에 이 운영 체제는 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 더 이상 지원되지 않습니다. 그러나 이 지원의 중단이 발표되거나 이 운영 체제의 추가 지원 기간이 만료될 때까지 배포 지점 사이트 시스템 역할(풀(pull) 배포 지점 포함)에 대해 계속 지원됩니다.  

-   참고 2: 지원이 종료된 후에 이 운영 체제는 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 더 이상 지원되지 않습니다. 그러나 이 지원의 중단이 발표되거나 이 운영 체제의 추가 지원 기간이 만료될 때까지 상태 마이그레이션 지점 및 배포 지점 사이트 시스템 역할에 대해(풀(pull) 배포 지점 포함, PXE 및 멀티캐스트에 대해) 계속 지원됩니다.  버전 1602부터, Windows Sever 2008 R2에서 Windows Server 2012 R2로 사이트 서버의 운영 체제에 대해 현재 위치 업그레이드를 수행할 수 있습니다.  

     사이트 서버 운영 체제의 현재 위치 업그레이드에 대한 자세한 내용은 [System Center Configuration Manager의 변경된 내용](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)의 [Windows Server 2008 R2를 실행하는 사이트 서버의 운영 체제에 대한 현재 위치 업그레이드를 수행합니다.](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) 섹션을 참조하세요.



 **사용되지 않는 클라이언트 운영 체제:**  

 달리 언급되어 있지 않으면 Configuration Manager 클라이언트로 지원되는 각 운영 체제는 [Microsoft 지원 주기](https://support.microsoft.com/lifecycle)에 설명된 대로 해당 운영 체제의 확장 지원 종료 날짜까지 지원됩니다.  운영 체제에 대한 Configuration Manager 지원이 확장 지원 종료 날짜 전에 종료되는 경우 해당 운영 체제의 사용 중단 날짜 및 지원 제거 날짜가 여기에 제공됩니다.  

|**운영 체제**|**처음 중단 발표**|**제거된 지원**|  
|-|-|-|  
|Windows XP|7/10/2015|√|  
|Windows XP Embedded|7/10/2015|2016년 12월 31일 이후 출시된 첫 번째 업데이트와 함께 지원 종료|  
|Windows Server 2003|7/10/2015|√|  
|Windows Server 2003 R2|7/10/2015|√|  
|Windows Vista|7/10/2015|√|  
|Mac OS X 10.6 – 10.8|7/10/2015|√|  
|Windows Mobile 6.0 - 6.5|7/10/2015|√|  
|Nokia Symbian Belle|7/10/2015|√|  
|Windows CE 5.0 – 6.0|7/10/2015|√|  


 **사이트 데이터베이스인 SQL Server 버전에 대해 사용되지 않는 지원:**  

|**SQL Server 버전**|**처음 중단 발표**|**제거된 지원**|   
|-|-|-|  
|SQL Server 2008|7/10/2015|√|  
|SQL Server 2008 R2|7/10/2015|2016년 12월 31일 이후 출시된 첫 번째 업데이트와 함께 지원 종료|  

## <a name="features-removed-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 제거된 기능  
 초기 System Center Configuration Manager 릴리스부터 다음 기능이 제거됩니다.

###  <a name="a-namebkmkamta-out-of-band-management"></a><a name="bkmk_amt"></a> 대역 외 관리  
 Configuration Manager에서 Configuration Manager 콘솔 내의 AMT 기반 컴퓨터에 대한 기본 지원이 제거되었습니다.  

-    [Microsoft System Center Configuration Manager용 Intel SCS 추가 기능](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html)을 사용하는 경우 AMT 기반 컴퓨터가 완전히 관리되는 상태로 유지됩니다.  

-   추가 기능을 사용하면 AMT를 관리할 최신 기능에 액세스하고 구성 관리자가 해당 변경 사항을 통합할 수 있을 때까지 도입된 제한 사항을 제거합니다.  

-   System Center 2012 Configuration Manager의 대역 외 관리는 이 변경 사항에 의해 영향을 받지 않습니다.  

###  <a name="a-namebkmknapa-network-access-protection"></a><a name="bkmk_nap"></a> 네트워크 액세스 보호  
 System Center Configuration Manager에서 네트워크 액세스 보호에 대한 지원이 제거되었습니다. 이 기능은 Windows Server 2012 R2부터 사용되지 않으며 Windows 10에서 제거됩니다.  

 네트워크 액세스 보호를 위한 대체 방법은 **네트워크 정책 및 액세스 서비스 개요** 의 [사용되지 않는 기능](https://technet.microsoft.com/library/hh831683.aspx)섹션을 참조하세요.  



<!--HONumber=Nov16_HO1-->


