---
title: "마이그레이션 원본 계층 구조 | Microsoft 문서"
description: "System Center Configuration Manager 환경에 데이터를 마이그레이션할 수 있도록 원본 계층 및 원본 사이트를 구성합니다."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 80c43ab93ee5a2de6bf8d7993dfd46f0005d2df8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="configure-source-hierarchies-and-source-sites-for-migration-to-system-center-configuration-manager"></a>System Center Configuration Manager로 마이그레이션할 원본 계층 및 원본 사이트 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 환경으로 데이터를 마이그레이션할 수 있도록 하려면 지원되는 Configuration Manager 원본 계층을 구성하고 해당 계층에 마이그레이션할 데이터가 포함된 원본 사이트를 하나 이상 구성해야 합니다.  

> [!NOTE]  
>  마이그레이션을 위한 작업은 대상 계층의 최상위 사이트에서 실행됩니다. 기본 자식 사이트에 연결된 Configuration Manager 콘솔을 사용하는 경우 마이그레이션을 구성하면 중앙 관리 사이트에 구성을 복제하여 시작한 다음, 연결된 기본 사이트로 상태를 다시 복제할 시간을 허용해야 합니다.  

 원본 계층을 지정하고 다른 원본 사이트를 더 추가하려면 다음 섹션의 정보 및 절차를 사용하세요. 이러한 절차를 완료하면 마이그레이션 작업을 만들어 원본 계층에서 대상 계층으로 데이터를 마이그레이션할 수 있습니다.  

-   [마이그레이션할 원본 계층 지정](#BKBM_ConfigSrcHierarchy)  

-   [원본 계층의 추가 원본 사이트 식별](#BKBM_ConfigSrcSites)  

##  <a name="BKBM_ConfigSrcHierarchy"></a> 마이그레이션할 원본 계층 지정  
 대상 계층으로 데이터를 마이그레이션하려면 마이그레이션할 데이터가 포함된 지원되는 원본 계층을 지정해야 합니다. 기본적으로 해당 계층의 최상위 사이트가 원본 계층의 원본 사이트가 됩니다. Configuration Manager 2007 계층 구조에서 마이그레이션하는 경우 첫 번째 원본 사이트에서 데이터를 수집한 다음 마이그레이션할 추가 원본 사이트를 설정할 수 있습니다. System Center 2012 Configuration Manager 또는 System Center Configuration Manager 계층 구조에서 마이그레이션하는 경우 원본 계층에서 데이터를 마이그레이션하기 위해 추가 원본 사이트를 설정할 필요가 없습니다. 이러한 버전의 Configuration Manager에서는 원본 계층의 최상위 사이트에서 사용할 수 있는 공유 데이터베이스를 사용하기 때문입니다. 공유 데이터베이스에는 마이그레이션할 수 있는 모든 정보가 포함되어 있습니다.  

 마이그레이션할 원본 계층을 지정하고 Configuration Manager 2007 계층 구조에서 추가 원본 사이트를 식별하려면 다음 절차를 수행합니다.  

 대상 계층에 연결된 Configuration Manager 콘솔에서 이 절차를 수행합니다.  

### <a name="to-configure-a-source-hierarchy"></a>원본 계층을 구성하려면   

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **마이그레이션**을 확장한 후 **원본 계층**을 클릭합니다.  

3.  **홈** 탭의 **마이그레이션** 그룹에서 **원본 계층 지정**을 클릭합니다.  

4.  **원본 계층 지정** 대화 상자에서 **원본 계층**에 대해 **새로운 원본 계층**을 선택합니다.  

5.  **최상위 Configuration Manager 사이트 서버**에 대해서는 지원되는 원본 계층의 최상위 사이트 이름 또는 IP 주소를 입력합니다.  

6.  다음 권한이 있는 원본 사이트 액세스 계정을 지정합니다.  

    -   원본 사이트 계정: 원본 계층의 지정된 최상위 사이트에 대한 SMS 공급자 **읽기** 권한 배포 지점 공유 및 업그레이드에는 소스 계층 구조의 사이트에 대한 **수정** 및 **삭제** 권한이 필요합니다.

    -   원본 사이트 데이터베이스 계정: 원본 계층의 지정된 최상위 사이트에 대한 SQL Server 데이터베이스 **읽기** 및 **실행** 권한  

     컴퓨터 계정의 사용을 지정하면 Configuration Manager에서 대상 계층 최상위 사이트의 컴퓨터 계정을 사용합니다. 이 옵션을 사용하는 경우 이 계정이 원본 계층의 최상위 사이트가 있는 도메인에서 **Distributed COM Users** 보안 그룹의 구성원이어야 합니다.  

7.  원본 계층과 대상 계층 간에 배포 지점을 공유하려면 **원본 사이트 서버에 대한 배포 지점 공유 사용** 확인란을 선택합니다. 지금은 배포 지점 공유를 사용하지 않는 경우 데이터 수집이 완료된 후에 원본 사이트의 자격 증명을 편집하면 배포 지점 공유를 사용하도록 설정할 수 있습니다.  

8.  **확인** 을 클릭하여 구성을 저장합니다. 그러면 **데이터 수집 상태** 대화 상자가 열리고 자동으로 데이터 수집이 시작됩니다.  

9. 데이터 수집을 마치면 **닫기** 를 클릭하여 **데이터 수집 상태** 대화 상자를 닫고 구성을 완료합니다.  

##  <a name="BKBM_ConfigSrcSites"></a> 원본 계층의 추가 원본 사이트 식별  
 지원되는 원본 계층을 구성하면 해당 계층의 최상위 사이트가 자동으로 원본 사이트로 구성되고 해당 사이트에서 자동으로 데이터가 수집됩니다. 수행할 다음 작업은 원본 계층에서 실행하는 Configuration Manager의 버전에 따라 다릅니다.  

-   Configuration Manager 2007 원본 계층의 경우 첫 번째 원본 사이트에 대해 데이터 수집을 완료한 후에 해당 첫 번째 원본 사이트에서 마이그레이션을 시작하거나 원본 계층에서 추가 원본 사이트를 설정할 수 있습니다. 자식 사이트에서만 사용할 수 있는 데이터를 마이그레이션하려면 Configuration Manager 2007 계층 구조의 추가 원본 사이트를 설정합니다. 예를 들어 마이그레이션할 콘텐츠를 원본 계층의 자식 사이트에서 만들었고 원본 계층의 최상위 사이트에서 사용할 수 없는 경우에 해당 콘텐츠에 대한 데이터를 수집하도록 추가 원본 사이트를 구성할 수 있습니다.  

-   System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층의 경우 원본 사이트를 추가로 구성할 필요가 없습니다. 이러한 버전의 Configuration Manager에서는 원본 계층의 최상위 사이트에서 사용할 수 있는 공유 데이터베이스를 사용하기 때문입니다. 공유 데이터베이스에는 해당 원본 계층의 모든 사이트에서 마이그레이션할 수 있는 모든 정보가 포함되어 있습니다. 따라서 마이그레이션할 수 있는 데이터를 원본 계층의 최상위 사이트에서 사용할 수 있습니다.  

Configuration Manager 2007 원본 계층의 추가 원본 사이트를 구성할 때는 원본 계층의 최상위부터 최하위까지 추가 원본 사이트를 구성해야 합니다. 자식 사이트를 원본 사이트로 구성하기 전에 부모 사이트를 원본 사이트로 구성해야 합니다.  

Configuration Manager 2007 원본 계층에 대한 추가 원본 사이트를 구성하려면 다음 절차를 수행하세요.  

### <a name="to-identify-additional-source-sites-in-the-source-hierarchy"></a>원본 계층에서 추가 원본 사이트를 식별하려면 

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **마이그레이션**을 확장한 후 **원본 계층**을 클릭합니다.  

3.  원본 사이트로 구성할 사이트를 선택합니다.  

4.  **홈** 탭의 **원본 사이트** 그룹에서 **구성**을 클릭합니다.  

5.  **원본 사이트 자격 증명** 대화 상자에서 원본 사이트 액세스 계정에 대해 다음 권한이 있는 계정을 지정합니다.  

    -   원본 사이트 계정: 원본 계층의 지정된 최상위 사이트에 대한 SMS 공급자 **읽기** 권한 배포 지점 공유 및 업그레이드에는 소스 계층 구조의 사이트에 대한 **수정** 및 **삭제** 권한이 필요합니다.  

    -   원본 사이트 데이터베이스 계정: 원본 계층의 지정된 최상위 사이트에 대한 SQL Server 데이터베이스 **읽기** 및 **실행** 권한  

    컴퓨터 계정의 사용을 지정하면 Configuration Manager에서 대상 계층 최상위 사이트의 컴퓨터 계정을 사용합니다. 이 옵션을 사용하는 경우 이 계정이 원본 계층의 최상위 사이트가 있는 도메인에서 **Distributed COM Users** 보안 그룹의 구성원이어야 합니다.  

6.  원본 계층과 대상 계층 간에 배포 지점을 공유하려면 **원본 사이트 서버에 대한 배포 지점 공유 사용** 확인란을 선택합니다. 현재 배포 지점 공유를 사용하지 않는 경우 데이터 수집이 완료된 후에 원본 사이트의 자격 증명을 편집하면 배포 지점 공유를 사용하도록 설정할 수 있습니다.  

7. **확인** 을 클릭하여 구성을 저장합니다. 그러면 **데이터 수집 상태** 대화 상자가 열리고 자동으로 데이터 수집이 시작됩니다.  

8.  데이터 수집을 마치면 **닫기** 를 클릭하여 구성을 완료합니다.  
