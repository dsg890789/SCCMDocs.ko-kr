---
title: 사이트 서버에서 사용되지 않음
titleSuffix: Configuration Manager
description: Configuration Manager가 사이트 서버에서 더 이상 지원하지 않는 제품 및 운영 체제에 대해 알아봅니다.
ms.date: 01/15/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d53ac075-438b-41da-ab85-42f33982da0c
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 88b192163ac7a947f73ff658f7bafbfc1bfd5e14
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67285871"
---
# <a name="removed-and-deprecated-for-configuration-manager-site-servers"></a>Configuration Manager 사이트 서버에서 제거되거나 사용되지 않음

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager 사이트 서버 지원에서 제거되거나 향후 업데이트에서 제거될(사용되지 않음) 제품 및 운영 체제에 대해 설명합니다. Configuration Manager 사용에 영향을 줄 수 있는 향후 변경 내용에 대해 미리 알려드립니다.  

이 정보는 나중에 변경될 수 있습니다. 사용되지 않는 각 기능, 제품 또는 운영 체제를 포함하지 않을 수 있습니다.  



## <a name="server-os"></a>서버 OS  

|**운영 체제**|**처음 중단 발표**|**제거된 지원** |  
|-|-|-| 
|Windows Server 2008 R2 SP1|2015년 7월 10일| 버전 1702 <sup>[참고 1](#bkmk_note1)</sup>| 
|Windows Server 2008 SP2|2015년 7월 10일|버전 1511 <sup>[참고 2](#bkmk_note2)</sup>|  

#### <a name="bkmk_note1"></a> 참고 1: Windows Server 2008 R2 SP1
사이트 서버 또는 대부분의 사이트 시스템 역할에 대해서는 서비스 팩 1이 포함된 Windows Server 2008 R2가 지원되지 않습니다. 이 OS는 계속 배포 지점 역할을 지원합니다. 이 지원에는 끌어오기-배포 지점, PXE 및 멀티 캐스트가 포함됩니다. 

> [!Important]  
> SP1이 포함된 Windows Server 2008 R2의 확장된 지원 종료 날짜는 2020년 1월 14일입니다. 이 날짜 이후에 Configuration Manager에서는 이 OS를 사이트 시스템 역할로 지원하지 않습니다. 

사이트 서버 OS를 Windows Server 2008 R2에서 Windows Server 2012 R2로 업그레이드할 수 있습니다. 자세한 내용은 [Windows Server 2008 R2를 실행하는 사이트 서버의 운영 체제에 대한 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#BKMK_SupConfigUpgradeSiteSrv)를 참조하세요.  


#### <a name="bkmk_note2"></a> 참고 2: Windows Server 2008 SP2
사이트 서버 또는 대부분의 사이트 시스템 역할에 대해서는 서비스 팩 2가 포함된 Windows Server 2008이 지원되지 않습니다. 이 OS는 계속 배포 지점 역할을 지원합니다. 이 지원에는 끌어오기-배포 지점, PXE 및 멀티 캐스트가 포함됩니다. 

> [!Important]  
> SP2가 포함된 Windows Server 2008의 확장된 지원 종료 날짜는 2020년 1월 14일입니다. 이 날짜 이후에 Configuration Manager에서는 이 OS를 사이트 시스템 역할로 지원하지 않습니다.  



## <a name="sql-server"></a>SQL Server   

|**SQL Server 버전**|**처음 중단 발표**|**제거된 지원**|   
|-|-|-| 
|SQL Server 2008 R2|2015년 7월 10일|버전 1702| 
|SQL Server 2008|2015년 7월 10일|버전 1511|  


SQL Server 버전을 업그레이드해야 할 경우, 쉬운 경우부터 더 복잡한 경우까지 다음 방법을 권장합니다.

1. [SQL Server 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#BKMK_SupConfigUpgradeDBSrv)(권장).  

2. SQL Server의 새 버전을 새 컴퓨터에 설치합니다. 그런 다음, 사이트 서버를 새 SQL Server로 가리키려면 Configuration Manager 설치 프로그램의 [데이터베이스 이동 옵션을 사용](/sccm/core/servers/manage/modify-your-infrastructure#bkmk_dbconfig)합니다.  

3. [백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 사용합니다.  



## <a name="more-information"></a>추가 정보

자세한 내용은 다음 아티클을 참조하세요. 

- [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)  

- [Microsoft 지원 기간](https://support.microsoft.com/lifecycle)  

- [Configuration Manager 현재 분기 버전에 대한 지원](/sccm/core/servers/manage/current-branch-versions-supported)  

