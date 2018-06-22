---
title: Deprecated for Configuration Manager 사이트 서버
titleSuffix: Configuration Manager
description: 사이트 서버에 대해 System Center Configuration Manager에서 더 이상 지원되지 않는 제품 및 운영 체제에 대해 알아봅니다.
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d53ac075-438b-41da-ab85-42f33982da0c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b92eb8083ce886fcab4d9957b2a79999d72a1a5a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332766"
---
# <a name="removed-and-deprecated-for-system-center-configuration-manager-site-servers"></a>System Center Configuration Manager 사이트 서버에서 제거된 기능과 사용되지 않는 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 System Center Configuration Manager 사이트 서버 지원에서 제거되거나 향후 업데이트에서 제거될(사용되지 않음) 제품 및 운영 체제에 대해 설명합니다. 이 문서에서는 Configuration Manager 사용에 영향을 줄 수 있는 향후 변경 사항에 대해 미리 알려줍니다.  

이 정보는 이후 릴리스에서 변경될 수 있으며 더 이상 지원되지 않는 각 기능, 제품 및 운영 체제가 누락될 수 있습니다.  


## <a name="deprecated-server-operating-systems"></a>사용되지 않는 서버 운영 체제  

|**운영 체제**|**처음 중단 발표**|**제거된 지원** |  
|-|-|-| 
|Windows Server 2008 R2|2015년 7월 10일| 버전 1702(참고 1 참조)| 
|Windows Server 2008|2015년 7월 10일|버전 1511 </br></br>사이트 시스템으로 지원이 제거됩니다. (참고 2 참조).|  

>[!NOTE]
>-   1702 버전부터 Windows Server 2008 R2는 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 지원되지 않습니다. 하지만 1702 이전 버전은 계속 사용할 수 있도록 지원합니다. 이 운영 체제는 지원의 중단이 발표되거나 운영 체제의 추가 지원 기간이 만료될 때까지 배포 지점 사이트 시스템 역할에 대해(풀(pull) 배포 지점 포함, PXE 및 멀티캐스트에 대해) 계속 지원됩니다. 버전 1602부터 Windows Sever 2008 R2에서 Windows Server 2012 R2로 사이트 서버의 운영 체제에 대해 현재 위치 업그레이드를 수행할 수 있습니다.  
>- 사이트 서버 운영 체제의 현재 위치 업그레이드에 대한 자세한 내용은 [System Center Configuration Manager를 지원하는 온-프레미스 인프라 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure)의 [Windows Server 2008 R2을 실행하는 사이트 서버의 운영 체제에 대한 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#bkmk_from2008r2) 섹션을 참조하세요.

>[!NOTE]
>-   Windows Server 2008는 배포 지점 및 풀(pull) 배포 지점을 제외하고, 사이트 서버 또는 사이트 시스템 역할에 대해 지원되지 않습니다. 이 지원의 중단이 발표되거나 운영 체제의 추가 지원 기간이 만료될 때까지 운영 체제를 배포 지점으로 계속 사용할 수 있습니다. 자세한 내용은 [Installation of System Center Configuration Manager CB and LTSB fails on Windows Server 2008](https://support.microsoft.com/help/4015095)(Windows Server 2008에서 System Center Configuration Manager CB 및 LTSB 설치 실패)을 참조하세요.

## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>사이트 데이터베이스인 SQL Server 버전에 대해 사용되지 않는 지원  

|**SQL Server 버전**|**처음 중단 발표**|**제거된 지원**|   
|-|-|-| 
|SQL Server 2008 R2|2015년 7월 10일|버전 1702| 
|SQL Server 2008|2015년 7월 10일|버전 1511|  


SQL Server 버전을 업그레이드해야 할 경우, 쉬운 경우부터 더 복잡한 경우까지 다음 방법을 권장합니다.
1. [SQL Server 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server)(권장).
2. SQL Server의 새 버전을 새 컴퓨터에 설치합니다. 그런 다음, Configuration Manager 설치 프로그램의 [데이터베이스 이동 옵션을 사용](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration)하여 사용 중인 사이트 서버를 새 SQL Server로 지정합니다.
3. [백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 사용합니다.


## <a name="more-information"></a>추가 정보
자세한 내용은 다음을 참조하십시오.
 - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
 - [Microsoft 지원 주기 정책](https://support.microsoft.com/lifecycle) 웹 사이트
 - [Configuration Manager 현재 분기 버전에 대한 지원](/sccm/core/servers/manage/current-branch-versions-supported)