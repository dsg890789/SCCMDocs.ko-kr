---
title: "사용되지 않는 기능 | Microsoft 문서"
description: "System Center Configuration Manager에서 더 이상 지원되지 않는 기능, 제품 및 운영 체제에 대해 알아봅니다."
ms.custom: na
ms.date: 1/5/2017
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
ms.sourcegitcommit: f912bb82b8d753f01b15f96eec5099c3f92abe75
ms.openlocfilehash: 18b411b05dd6fc9b572e1d3d201876172bb40d07


---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>System Center Configuration Manager에서 제거되는 기능과 사용되지 않는 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 System Center Configuration Manager에서 이후 지원하지 않거나 업데이트에서 제거될(사용되지 않음) 기능, 제품 및 운영 체제에 대해 설명합니다. 이를 통해 Configuration Manager 사용에 영향을 줄 수 있는 향후 변경 사항에 대해 미리 알려드립니다.  

이 정보는 이후 릴리스에서 변경될 수 있으며 더 이상 지원되지 않는 각 기능, 제품 및 운영 체제가 누락될 수 있습니다.  

## <a name="how-to-use-this-information"></a>이 정보를 사용하는 방법  
특정 기능 또는 운영 체제가 사용되지 않는 항목으로 처음 표시되면 Configuration Manager에서 해당 기능이나 운영 체제를 사용하도록 지원하는 기능은 이후 Configuration Manager 버전에서 제거되도록 예약됩니다. 이 정보는 해당 기능 또는 운영 체제 대신 사용할 항목을 계획할 수 있도록 돕기 위해 제공됩니다. 해당 지원이 제거되는 첫 번째 Configuration Manager 버전이 출시되면 해당 특정 버전을 나타내도록 이 항목이 업데이트됩니다.  

기능 또는 운영 체제 지원이 제거되더라도 이전 버전의 Configuration Manager가 계속 지원된다면 해당 Configuration Manager 버전을 사용할 때 지원이 제거된 기능이나 운영 체제는 계속 지원됩니다. 그러나 이 항목에 나와 있는 버전 또는 날짜 이후에 출시된 Configuration Manager 버전을 사용하는 경우 해당 Configuration Manager 버전에서는 기능 또는 운영 체제 지원을 제공하지 않습니다.

예를 들어, 2016년 9월 이후 출시된 첫 번째 업데이트에서 기능의 지원이 제거되도록 예약된 경우 2016년 10월에 출시된 업데이트 1610에는 해당 기능에 대한 지원이 더 이상 포함되지 않습니다.
-  즉, 업데이트 1610을 설치하면 해당 기능은 더 이상 지원되지 않습니다.
-  그러면 버전 1610에서 지원이 제거되었음을 나타내도록 항목이 업데이트됩니다.
그러나 버전 1602 또는 1606과 같이 해당 기능을 지원하는 이전 버전을 계속 사용하는 경우에는 사용 중인 버전의 지원이 중단될 때까지 해당 기능도 계속 사용할 수 있습니다.

자세한 내용은 다음을 참조하세요.
 - [Microsoft 지원 주기 정책](https://support.microsoft.com/lifecycle) 웹 사이트
 - [Configuration Manager 현재 분기 버전에 대한 지원](/sccm/core/servers/manage/current-branch-versions-supported)

## <a name="deprecated-features"></a>사용되지 않는 기능  

|**기능**|**처음 중단 발표**|**제거된 지원**|  
|-|-|-|  
|NAP(네트워크 액세스 보호) - System Center 2012 Configuration Manager에 있음|2015년 7월 10일|버전 1511|  
|대역 외 관리 - System Center 2012 Configuration Manager에 있음|2015년 10월 16일|버전 1511|
|작업 순서: <br /> - 동적 디스크로 변환 <br /> - 배포 도구 설치 |2016년 11월 18일|이러한 작업 순서에 대한 지원은 2017년 6월 1일 이후 처음으로 출시되는 업데이트와 함께 종료됨.|
|소프트웨어 센터가 새로운 세련된 디자인으로 바뀌었습니다. 이전에는 Silverlight 종속 응용 프로그램 카탈로그에서만 표시되었던 앱(사용자가 사용할 수 있는 앱)이 이제 소프트웨어 센터의 **응용 프로그램** 탭에 표시됩니다. 소프트웨어 센터의 **설치 상태** 탭에 있는 링크를 사용하면 응용 프로그램 카탈로그에 계속 액세스할 수 있습니다.<br><br>향후 몇 개월 이후 소프트웨어 센터의 이전 버전을 더 이상 사용할 수 없게 됩니다.<br><br>클라이언트 설정인 **컴퓨터 에이전트** > **새 소프트웨어 센터 사용**을 활성화하여 새로운 소프트웨어 센터를 사용하도록 클라이언트를 설정할 수 있습니다.<br><br>소프트웨어 센터에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 관리 계획 및 구성](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management)을 참조하세요.|2016년 12월 13일|공지 예정|
|Configuration Manager를 사용한 VHD(가상 하드 디스크) 관리 </br></br>새 VHD를 만들거나 작업 순서를 사용하여 VHD를 관리하는 옵션이 제거되고, Configuration Manager 콘솔에서 가상 하드 디스크 노드가 제거됩니다. </br></br>이 지원이 제거되면 기존 VHD가 삭제되는 것은 아니지만 더 이상 Configuration Manager 콘솔 내에서 액세스할 수 없게 됩니다.  |2017년 1월 6일 |2017년 1월 1일 이후에 릴리스되는 첫 번째 업데이트와 함께 VHD에 대한 지원이 종료됩니다.|


System Center Configuration Manager 버전 1511 출시와 함께 제거된 기능에 대한 추가 정보:

###  <a name="a-namebkmkamta-out-of-band-management"></a><a name="bkmk_amt"></a> 대역 외 관리  
 Configuration Manager에서 Configuration Manager 콘솔 내의 AMT 기반 컴퓨터에 대한 기본 지원이 제거되었습니다.  

-   [Microsoft System Center Configuration Manager용 Intel SCS 추가 기능](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html)을 사용하는 경우 AMT 기반 컴퓨터가 완전히 관리되는 상태로 유지됩니다. 추가 기능을 사용하면 AMT를 관리할 최신 기능에 액세스하고 Configuration Manager가 해당 변경 사항을 통합할 수 있을 때까지 도입된 제한 사항을 제거할 수 있습니다.  

-   System Center 2012 Configuration Manager의 대역 외 관리는 이 변경 사항에 의해 영향을 받지 않습니다.  

###  <a name="a-namebkmknapa-network-access-protection"></a><a name="bkmk_nap"></a> 네트워크 액세스 보호  
 System Center Configuration Manager에서 네트워크 액세스 보호에 대한 지원이 제거되었습니다. 이 기능은 Windows Server 2012 R2부터 사용되지 않으며 Windows 10에서 제거됩니다.  

 네트워크 액세스 보호를 위한 대체 방법은 *네트워크 정책 및 액세스 서비스 개요* 의 [사용되지 않는 기능](https://technet.microsoft.com/library/hh831683.aspx)섹션을 참조하세요.  


## <a name="deprecated-operating-systems"></a>사용되지 않는 운영 체제
### <a name="server-operating-systems"></a>서버 운영 체제  

|**운영 체제**|**처음 중단 발표**|**제거된 지원** |  
|-|-|-|  
|Windows Server 2008|2015년 7월 10일|2016년 12월 31일 이후 출시되는 첫 번째 업데이트와 함께 지원 종료(참고 1 참조)|  
|Windows Server 2008 R2|2015년 7월 10일|2016년 12월 31일 이후 출시되는 첫 번째 업데이트와 함께 지원 종료(참고 2 참조)|  

-   참고 1: 지원이 종료된 후에 이 운영 체제는 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 더 이상 지원되지 않습니다. 그러나 이 지원의 중단이 발표되거나 이 운영 체제의 추가 지원 기간이 만료될 때까지 배포 지점 사이트 시스템 역할(풀(pull) 배포 지점 포함)에 대해 계속 지원됩니다.  

-   참고 2: 지원이 종료된 후에 이 운영 체제는 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 더 이상 지원되지 않습니다. 그러나 이 지원의 중단이 발표되거나 이 운영 체제의 추가 지원 기간이 만료될 때까지 상태 마이그레이션 지점 및 배포 지점 사이트 시스템 역할에 대해(풀(pull) 배포 지점 포함, PXE 및 멀티캐스트에 대해) 계속 지원됩니다. 버전 1602부터, Windows Sever 2008 R2에서 Windows Server 2012 R2로 사이트 서버의 운영 체제에 대해 현재 위치 업그레이드를 수행할 수 있습니다.  

     사이트 서버 운영 체제의 현재 위치 업그레이드에 대한 자세한 내용은 [System Center Configuration Manager의 변경된 내용](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)의 [Windows Server 2008 R2를 실행하는 사이트 서버의 운영 체제에 대한 현재 위치 업그레이드를 수행합니다.](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) 섹션을 참조하세요.



### <a name="client-operating-systems"></a>클라이언트 운영 체제  

 달리 언급되어 있지 않으면 Configuration Manager 클라이언트로 지원되는 각 운영 체제는 해당 운영 체제의 확장 지원 종료 날짜까지 지원됩니다. 연장 지원 종료 날짜에 대한 자세한 내용은 [Microsoft 지원 주기](https://support.microsoft.com/lifecycle)를 참조하세요. 운영 체제에 대한 Configuration Manager 지원이 확장 지원 종료 날짜 전에 종료되는 경우 해당 운영 체제의 사용 중단 날짜 및 지원 제거 날짜가 여기에 제공됩니다.  

|**운영 체제**|**처음 중단 발표**|**제거된 지원**|  
|-|-|-|  
|Windows XP|2015년 7월 10일|버전 1511|  
|Windows XP Embedded|2015년 7월 10일|2016년 12월 31일 이후 출시된 첫 번째 업데이트와 함께 지원 종료|  
|Windows Server 2003|2015년 7월 10일|버전 1511|  
|Windows Server 2003 R2|2015년 7월 10일|버전 1511|  
|Windows Vista|2015년 7월 10일|버전 1511|  
|Mac OS X 10.6 – 10.8|2015년 7월 10일|버전 1511|  
|Windows Mobile 6.0 - 6.5|2015년 7월 10일|버전 1511|  
|Nokia Symbian Belle|2015년 7월 10일|버전 1511|  
|Windows CE 5.0 – 6.0|2015년 7월 10일|버전 1511|  


## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>사이트 데이터베이스인 SQL Server 버전에 대해 사용되지 않는 지원  

|**SQL Server 버전**|**처음 중단 발표**|**제거된 지원**|   
|-|-|-|  
|SQL Server 2008|2015년 7월 10일|버전 1511|  
|SQL Server 2008 R2|2015년 7월 10일|2016년 12월 31일 이후 출시된 첫 번째 업데이트와 함께 지원 종료|  



<!--HONumber=Jan17_HO1-->


