---
title: 사용자 지정 데이터베이스 파일 위치
titleSuffix: Configuration Manager
description: SQL Server 데이터베이스 파일에 대해 사용자 지정 위치를 지정하는 방법을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 597ce060dc1fb37f1cc827da3e1c059958a91163
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332732"
---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>System Center Configuration Manager 사이트 데이터베이스 파일에 대한 사용자 지정 위치

*적용 대상: System Center Configuration Manager(현재 분기)*

 System Center Configuration Manager는 SQL Server 데이터베이스 파일에 대해 사용자 지정 위치를 지원합니다.  

> [!NOTE]  
>  SQL Server 클러스터를 사용할 때는 기본 파일 위치가 아닌 위치를 지정하는 옵션을 사용할 수 없습니다.  

 새 기본 사이트 또는 중앙 관리 사이트를**설치하는 동안** 다음을 수행할 수 있습니다.  

-   **사이트 데이터베이스에 대해 기본이 아닌 파일 위치 지정**: Configuration Manager 설치 프로그램은 이러한 위치를 사용하여 사이트 데이터베이스를 만듭니다.  

-   **사용자 지정 파일 위치를 사용하는 미리 만든 SQL Server 데이터베이스 사용 지정**:  Configuration Manager 설치 프로그램은 이 미리 만든 데이터베이스와 미리 구성된 파일 위치를 사용합니다.  

**설치 후**에는 사이트 데이터베이스 파일의 위치를 변경할 수 있습니다. 이렇게 하려면 사이트를 중지하고 SQL Server에서 파일 위치를 편집해야 합니다.  

-   Configuration Manager 사이트 서버에서 **SMS_Executive** 서비스를 중지합니다.  

-   SQL Server 버전의 설명서에서 사용자 데이터베이스를 이동하는 방법을 확인합니다. 예를 들어 SQL Server 2014를 사용하는 경우 TechNet에서 [사용자 데이터베이스 이동](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) 을 참조하세요.  

-   데이터베이스 파일 이동을 완료한 후 Configuration Manager 사이트 서버에서 **SMS_Executive** 서비스를 다시 시작합니다.  
