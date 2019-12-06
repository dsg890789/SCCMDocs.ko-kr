---
title: 마이그레이션 필수 조건
titleSuffix: Configuration Manager
description: 지원되는 Configuration Manager 버전, 지원되는 원본 사이트 언어 및 마이그레이션을 위한 필수 조건을 이해합니다.
ms.date: 05/7/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ec976930-7467-4d3c-b33c-991bf408a74a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81073cc22d7bb59188cf881590d07deb0c20158c
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70891462"
---
# <a name="prerequisites-for-migration-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 마이그레이션을 수행하기 위한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

지원되는 원본 계층에서 마이그레이션하려면 해당하는 각 Configuration Manager 원본 사이트에 대한 액세스 권한 및 System Center Configuration Manager 대상 사이트에서 마이그레이션 작업을 구성하고 실행할 수 있는 권한이 있어야 합니다.  

 마이그레이션에 지원되는 Configuration Manager 버전 및 필수 구성을 이해하려면 다음 섹션의 정보를 참조하세요.  

-   [마이그레이션에 지원되는 Configuration Manager 버전](#BKMK_SupportedMigrationVersions)  

-   [마이그레이션에 지원되는 원본 사이트 언어](#BKMK_SorceSiteLanguage)  

-   [마이그레이션을 위한 필수 구성](#BKMK_Required_Configurations)  

##  <a name="BKMK_SupportedMigrationVersions"></a> 마이그레이션에 지원되는 Configuration Manager 버전  
 다음 Configuration Manager 버전을 실행하는 원본 계층에서 데이터를 마이그레이션할 수 있습니다.  

- Configuration Manager 2007 SP2. 마이그레이션 시 원본 사이트의 Configuration Manager 2007 버전이 R2인지 아니면 R3인지는 고려하지 않아도 됩니다. 원본 사이트에서 SP2를 실행한다면 R2 또는 R3 추가 기능이 설치된 사이트를 System Center Configuration Manager로 마이그레이션할 수 있습니다.  

- System Center 2012 Configuration Manager SP2 또는 System Center 2012 R2 Configuration Manager SP1  

  > [!TIP]  
  >  마이그레이션 외에도 System Center Configuration Manager에 대해 System Center 2012 Configuration Manager를 실행하는 사이트의 현재 위치 업그레이드를 사용할 수 있습니다.  

- 버전이 같거나 낮은 System Center Configuration Manager의 System Center Configuration Manager 계층 구조  

  예를 들어 System Center Configuration Manager 1606을 실행하는 대상 계층이 있는 경우 마이그레이션을 사용하여 버전 1606 또는 1602를 실행하는 원본 계층에서 데이터를 복사할 수 있습니다. 그러나 1610을 실행하는 원본 계층에서는 데이터를 마이그레이션할 수 없습니다.  


##  <a name="BKMK_SorceSiteLanguage"></a> 마이그레이션에 지원되는 원본 사이트 언어  
 Configuration Manager 계층 구조 간에 데이터를 마이그레이션하면 데이터가 System Center Configuration Manager에 대해 언어 중립적인 형식의 대상 계층에 저장됩니다. Configuration Manager 2007에서는 데이터를 언어 중립적인 형식으로 저장하지 않으므로 Configuration Manager 2007에서 마이그레이션할 때 마이그레이션 프로세스에서 개체를 이 형식으로 변환해야 합니다. 그러므로 다음 언어로 설치된 Configuration Manager 2007 원본 사이트만 마이그레이션이 가능합니다.  

-   영어  

-   프랑스어  

-   독일어  

-   일본어  

-   한국어  

-   러시아어  

-   중국어(간체)  

-   중국어(번체)  

System Center 2012 Configuration Manager 또는 System Center Configuration Manager 계층 구조에서 데이터를 마이그레이션할 때는 원본 사이트 언어 제한이 없습니다. 원본 사이트 데이터베이스에 있는 개체는 이미 언어 중립적인 형식입니다.  

##  <a name="BKMK_Required_Configurations"></a> 마이그레이션을 위한 필수 구성  
다음에는 마이그레이션 및 마이그레이션 작업을 사용하기 위한 필수 구성이 나와 있습니다.  

- **Configuration Manager 콘솔에서 마이그레이션을 구성, 실행, 모니터링하려면:**  

   대상 사이트에서 계정에 **인프라 관리자**의 역할 기반 관리 보안 역할을 할당해야 합니다. 이 보안 역할은 마이그레이션 작업 만들기, 정리, 모니터링 및 배포 지점을 공유하고 업그레이드하는 작업을 포함한 모든 마이그레이션 작업을 관리할 수 있는 권한을 부여합니다.  

- **데이터 수집:**  

   대상 사이트에서 데이터를 수집할 수 있도록 하려면 각 원본 사이트에서 사용할 다음 두 원본 사이트 액세스 계정을 구성해야 합니다.  

  -   **원본 사이트 계정:** 이 계정은 원본 사이트의 SMS 공급자에 액세스하는 데 사용됩니다.  

      -   Configuration Manager 2007 SP2 원본 사이트의 경우 이 계정에 모든 원본 사이트 개체에 대한 **읽기** 권한이 있어야 합니다.  

      -   System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 사이트의 경우에는 이 계정에 모든 원본 사이트 개체에 대한 **읽기** 권한이 있어야 합니다. 역할 기반 관리를 사용하여 계정에 이 권한을 부여합니다. 역할 기반 관리를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../core/understand/fundamentals-of-role-based-administration.md)항목을 참조하세요.  

  -   **원본 사이트 데이터베이스 계정:** 이 계정은 원본 사이트의 SQL Server 데이터베이스에 액세스하는 데 사용되며 원본 사이트 데이터베이스에 대한 **연결**, **실행** 및 **선택** 권한이 필요합니다.  

  새 원본 계층을 구성하거나, 다른 원본 사이트의 데이터 수집을 구성하거나, 원본 사이트의 자격 증명을 다시 구성할 때 이러한 계정을 구성할 수 있습니다. 이러한 계정은 도메인 사용자 계정을 사용할 수 있습니다. 아니면 대상 계층 최상위 사이트의 컴퓨터 계정을 지정할 수 있습니다.  

  > [!IMPORTANT]  
  >  각 액세스 계정으로 Configuration Manager 컴퓨터 계정을 사용하는 경우 이 계정은 원본 사이트가 있는 도메인의 **Distributed COM Users** 보안 그룹에 속해야 합니다.  

  데이터를 수집할 때 다음 네트워크 프로토콜 및 포트가 사용됩니다.  

  -   NetBIOS/SMB - 445(TCP)  

  -   RPC(WMI) - 135(TCP)  

  -   SQL Server - 원본 사이트 데이터베이스와 대상 사이트 데이터베이스 모두에서 사용 중인 TCP 포트  

- **소프트웨어 업데이트 마이그레이션:**  

   소프트웨어 업데이트를 마이그레이션하기 전에 소프트웨어 업데이트 지점이 있는 대상 계층을 구성해야 합니다. 자세한 내용은 [소프트웨어 업데이트 마이그레이션 계획](../../core/migration/planning-for-the-migration-of-objects.md#Plan_migrate_Software_updates)을 참조하세요.  

- **배포 지점 공유:**  

   원본 사이트에서 배포 지점을 공유하려면 대상 계층의 기본 사이트나 중앙 관리 사이트 하나 이상에서 클라이언트 요청에 대해 원본 사이트와 같은 포트 번호를 사용해야 합니다. 클라이언트 요청 포트에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법](../../core/clients/deploy/configure-client-communication-ports.md)을 참조하세요.  

   각 원본 사이트에 대해 FQDN으로 구성된 사이트 시스템 서버에 설치된 배포 지점만 공유됩니다.  

   또한 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 사이트에서 배포 지점을 공유하려면 **원본 사이트 계정**(원본 사이트 서버의 SMS 공급자에 액세스하는 계정)에 원본 사이트의 **사이트** 개체에 대한 **수정** 권한이 있어야 합니다. 역할 기반 관리를 사용하여 계정에 이 권한을 부여합니다. 역할 기반 관리를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../core/understand/fundamentals-of-role-based-administration.md)항목을 참조하세요.  


- **배포 지점 업그레이드 또는 재할당:**  

   원본 사이트의 SMS 공급자에서 데이터를 수집하도록 구성된 **원본 사이트 액세스 계정** 에는 다음 권한이 필요합니다.  

  - Configuration Manager 2007 배포 지점을 업그레이드하려면 계정에 Configuration Manager2007 사이트 서버의 **사이트** 클래스에 대한 **읽기**, **실행**, **삭제** 권한이 있어야 Configuration Manager2007 원본 사이트에서 배포 지점을 제거할 수 있습니다.  

  - System Center 2012 Configuration Manager 또는 System Center Configuration Manager 배포 지점을 재할당하려면 계정에 원본 사이트의 **사이트** 개체에 대한 **수정** 권한이 있어야 합니다. 역할 기반 관리를 사용하여 계정에 이 권한을 부여합니다. 역할 기반 관리를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../core/understand/fundamentals-of-role-based-administration.md)항목을 참조하세요.  

    배포 지점을 업그레이드하거나 새 계층에 재할당하려면 원본 계층에서 배포 지점을 관리하는 사이트에서 클라이언트 요청에 대해 구성한 포트가 배포 지점을 관리할 대상 사이트에서 클라이언트 요청에 대해 구성한 포트와 일치해야 합니다. 클라이언트 요청 포트에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법](../../core/clients/deploy/configure-client-communication-ports.md)을 참조하세요.  
