---
title: 개체 마이그레이션
titleSuffix: Configuration Manager
description: System Center Configuration Manager 환경에서 계층 구조 간의 개체 마이그레이션을 계획하는 방법을 알아봅니다.
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0e42b7c8db3ef8c6d645d29f371fd6da475159bd
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32336819"
---
# <a name="plan-for-the-migration-of-configuration-manager-objects-to-system-center-configuration-manager"></a>Configuration Manager 개체를 System Center Configuration Manager로 마이그레이션하도록 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 원본 사이트에 있는 다른 기능과 연결된 여러 다른 개체를 마이그레이션할 수 있습니다. 계층 간의 개체 마이그레이션을 계획하려면 다음 섹션을 참조하세요.  

-   [소프트웨어 업데이트 마이그레이션 계획](#Plan_migrate_Software_updates)  

-   [콘텐츠 마이그레이션 계획](#Plan_Migrate_content)  

-   [컬렉션 마이그레이션 계획](#BKMK_MigrateCollections)  

-   [운영 체제 배포 마이그레이션 계획](#Plan_migrate_OSD)  

-   [원하는 구성 관리 마이그레이션 계획](#Plan_Migrate_Compliance_settings)  

-   [경계 마이그레이션 계획](#Plan_migrate_Boundaries)  

-   [보고서 마이그레이션 계획](#Plan_Migrate_reports)  

-   [조직 폴더 및 검색 폴더의 마이그레이션 계획](#Plan_Migrate_Org_Folders)  

-   [Asset Intelligence 사용자 지정 항목 마이그레이션 계획](#Plan_Migrate_AI)  

-   [소프트웨어 계량 규칙 사용자 지정 항목 마이그레이션 계획](#Plan_Migrate_SWM_Rules)  

##  <a name="Plan_migrate_Software_updates"></a>소프트웨어 업데이트 마이그레이션 계획  
 소프트웨어 업데이트 개체(예: 소프트웨어 업데이트 패키지 및 소프트웨어 업데이트 배포)를 마이그레이션할 수 있습니다.  

 소프트웨어 업데이트 개체를 성공적으로 마이그레이션하려면 먼저 대상 계층 구조를 원본 계층 구조 환경과 일치하는 구성으로 설정해야 합니다. 그렇게 하려면 다음 작업을 수행해야 합니다.  

-   대상 계층 구조에 활성 소프트웨어 업데이트 지점을 배포합니다.  

-   제품 및 언어의 카탈로그를 원본 계층 구조의 구성과 일치하도록 설정합니다.  

-   대상 계층 구조의 소프트웨어 업데이트 지점을 WSUS(Windows Server Update Services)와 동기화합니다.  

소프트웨어 업데이트를 마이그레이션하는 경우 다음 사항을 고려하세요.  

-   대상 계층 구조의 정보를 원본 계층 구조의 구성과 일치하도록 동기화하지 않으면 소프트웨어 업데이트 개체를 마이그레이션할 수 없습니다.  

    > [!WARNING]  
    >  Configuration Manager에서 원본 계층 구조와 대상 계층 구조 간에 데이터를 동기화하는 WSUSutil 도구의 사용을 지원하지 않습니다.  

-   System Center Updates Publisher를 사용하여 게시된 사용자 지정 업데이트는 마이그레이션할 수 없습니다. 그 대신 사용자 지정 업데이트를 대상 계층에 다시 게시해야 합니다.  

Configuration Manager 2007 원본 계층 구조에서 마이그레이션할 때 마이그레이션 프로세스에서 일부 소프트웨어 업데이트 개체를 대상 계층 구조에서 사용 중인 형식으로 수정합니다. Configuration Manager 2007에서 소프트웨어 업데이트 개체를 마이그레이션하려고 계획하려면 다음 표를 참조하세요.  

|Configuration Manager 2007 개체|마이그레이션 후의 개체 이름|  
|-----------------------------------|---------------------------------|  
|소프트웨어 업데이트 목록|소프트웨어 업데이트 목록은 소프트웨어 업데이트 그룹으로 변환됩니다.|  
|소프트웨어 업데이트 배포|소프트웨어 업데이트 배포는 배포 및 업데이트 그룹으로 변환됩니다.<br /><br /> Configuration Manager 2007에서 소프트웨어 업데이트 배포를 마이그레이션한 후 배포하려면 먼저 대상 계층에서 이 배포를 사용하도록 설정해야 합니다.|  
|소프트웨어 업데이트 패키지|소프트웨어 업데이트 패키지는 소프트웨어 업데이트 패키지로 유지됩니다.|  
|소프트웨어 업데이트 템플릿|소프트웨어 업데이트 템플릿은 소프트웨어 업데이트 템플릿으로 유지됩니다.<br /><br /> Configuration Manager 2007 배포 템플릿의 **기간** 값은 마이그레이션되지 않습니다.|  

System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층에서 개체를 마이그레이션할 때 소프트웨어 업데이트 개체는 수정되지 않습니다.  

##  <a name="Plan_Migrate_content"></a> 콘텐츠 마이그레이션 계획  
 지원되는 원본 계층에서 대상 계층으로 콘텐츠를 마이그레이션할 수 있습니다. Configuration Manager 2007 원본 계층 구조의 경우 이러한 콘텐츠로는 소프트웨어 배포 패키지 및 프로그램과 가상 응용 프로그램(예: Microsoft Application Virtualization(App-V))이 있습니다. System Center 2012 Configuration Manager 및 System Center Configuration Manager 원본 계층 구조의 경우 이러한 콘텐츠에 응용 프로그램 및 App-V 가상 응용 프로그램이 포함됩니다. 계층 구조 간에 콘텐츠를 마이그레이션하는 경우 압축된 원본 파일이 대상 계층 구조로 마이그레이션됩니다.  

### <a name="packages-and-programs"></a>패키지 및 프로그램  
 패키지 및 프로그램은 마이그레이션할 때 마이그레이션으로 인해 수정되지 않습니다. 그러나 마이그레이션하기 전에 원본 파일 위치에 UNC(범용 명명 규칙) 경로를 사용하도록 각 패키지를 설정해야 합니다. 패키지 및 프로그램을 마이그레이션하기 위한 구성 과정에서 이 콘텐츠를 관리할 대상 계층의 사이트를 할당해야 합니다. 할당된 사이트에서는 콘텐츠가 마이그레이션되지 않지만 마이그레이션 후에 할당된 사이트에서 UNC 매핑을 사용하여 원래의 원본 파일 위치에 액세스합니다.  

 패키지 및 프로그램을 대상 계층 구조에 마이그레이션한 후에 원본 계층 구조에서 마이그레이션이 활성 상태로 남아 있는 동안 공유 배포 지점을 사용하면 콘텐츠를 해당 계층 구조의 클라이언트에서 사용할 수 있도록 만들 수 있습니다. 공유 배포 지점을 사용하려면 콘텐츠가 원본 사이트의 배포 지점에서 액세스할 수 있는 상태로 남아 있어야 합니다. 공유 배포 지점에 대한 자세한 내용은 [System Center Configuration Manager에서 콘텐츠 배포 마이그레이션 전략 계획](../../core/migration/planning-a-content-deployment-migration-strategy.md)에서 [원본 계층과 대상 계층 간에 배포 지점 공유](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration)를 참조하세요.  

 마이그레이션된 콘텐츠의 경우 원본 계층 구조나 대상 계층 구조에서 콘텐츠 버전이 변경되면 클라이언트가 더 이상 대상 계층 구조 공유 배포 지점의 콘텐츠에 액세스할 수 없습니다. 이 시나리오에서 원본 계층과 대상 계층 간의 패키지를 동일한 버전으로 복원하려면 콘텐츠를 다시 마이그레이션해야 합니다. 이 정보는 데이터 수집 주기 중에 동기화됩니다.  

> [!TIP]  
>  마이그레이션하는 각 패키지에 대해 대상 계층에서 패키지를 업데이트합니다. 이 동작은 패키지를 대상 계층의 배포 지점에 배포할 때 발생할 수 있는 문제를 방지할 수 있습니다. 그러나 대상 계층 구조의 배포 지점에서 패키지를 업데이트하면 해당 계층 구조의 클라이언트가 더 이상 공유 배포 지점에서 해당 패키지를 가져올 수 없습니다. 대상 계층 구조에서 패키지를 업데이트하려면 Configuration Manager 콘솔에서 소프트웨어 라이브러리로 이동하여 패키지를 마우스 오른쪽 단추로 클릭하고 **배포 지점 업데이트**를 선택합니다. 마이그레이션하는 각 패키지에 대해 이 동작을 수행합니다.  

> [!TIP]  
>  Microsoft System Center Configuration Manager Package Conversion Manager를 사용하면 패키지와 프로그램을 System Center Configuration Manager 응용 프로그램으로 변환할 수 있습니다. Package Conversion Manager는 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/p/?LinkId=212950) 사이트에서 다운로드할 수 있습니다. 자세한 내용은 [Configuration Manager Package Conversion Manager](http://go.microsoft.com/fwlink/p/?LinkId=247245)를 참조하세요.  

### <a name="virtual-applications"></a>가상 응용 프로그램  
지원되는 Configuration Manager 2007 사이트에서 App-V 패키지를 마이그레이션하면 마이그레이션 프로세스에서 이 패키지를 대상 계층의 응용 프로그램으로 변환합니다. 또한, App-V 패키지의 기존 보급 알림에 따라 대상 계층에서 다음 배포 유형이 만들어집니다.  

-   보급 알림이 없는 경우 기본 배포 유형 설정을 사용하는 한 가지 배포 유형이 만들어집니다.  

-   보급 알림이 하나만 있는 경우 Configuration Manager 2007 보급 알림과 같은 설정을 사용하는 한 가지 배포 유형이 만들어집니다.  

-   보급 알림이 여러 개 있는 경우 해당 보급 알림의 설정을 사용하여 각 Configuration Manager 2007 보급 알림에 대한 배포 유형이 만들어집니다.  

> [!IMPORTANT]  
>  이전에 마이그레이션된 Configuration Manager 2007 App-V 패키지를 다시 마이그레이션하는 경우 가상 응용 프로그램 패키지가 덮어쓰기 마이그레이션 동작을 지원하지 않기 때문에 마이그레이션되지 않습니다. 이 시나리오에서는 대상 계층에서 마이그레이션된 가상 응용 프로그램 패키지를 삭제한 다음 새 마이그레이션 작업을 만들어 가상 응용 프로그램을 마이그레이션해야 합니다.  

> [!NOTE]  
>  App-V 패키지를 마이그레이션한 후에는 콘텐츠 업데이트 마법사를 사용하여 App-V 배포 유형의 원본 경로를 변경할 수 있습니다. 배포 유형의 콘텐츠를 업데이트하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 응용 프로그램에 대한 관리 작업](../../apps/deploy-use/management-tasks-applications.md)에서 배포 유형을 관리하는 방법을 참조하세요.  

System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층 구조에서 마이그레이션할 때 App-V 배포 유형과 응용 프로그램뿐만 아니라 App-V 가상 환경의 개체도 마이그레이션할 수 있습니다. App-V 환경에 대한 자세한 내용은 [System Center Configuration Manager에서 App-V 가상 응용 프로그램 배포](../../apps/get-started/deploying-app-v-virtual-applications.md)를 참조하세요.  

### <a name="advertisements"></a>보급 알림  
컬렉션 기반 마이그레이션을 사용하면 지원되는 Configuration Manager 2007 원본 사이트에서 대상 계층으로 보급 알림을 마이그레이션할 수 있습니다. 클라이언트를 업그레이드하는 경우 클라이언트가 마이그레이션된 보급 알림을 다시 실행하지 않도록 이전에 실행한 보급 알림 기록을 유지합니다.  

> [!NOTE]  
>  가상 패키지의 보급 알림은 마이그레이션할 수 없습니다. 이것은 보급 알림 마이그레이션에서 제외됩니다.  

### <a name="applications"></a>응용 프로그램  
 지원되는 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층에서 대상 계층으로 응용 프로그램을 마이그레이션할 수 있습니다. 원본 계층에서 대상 계층으로 클라이언트를 재할당하면 클라이언트가 마이그레이션된 응용 프로그램을 다시 실행하지 않도록 이전에 설치한 응용 프로그램 기록을 유지합니다.  

##  <a name="BKMK_MigrateCollections"></a> 컬렉션 마이그레이션 계획  
 지원되는 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층에서 컬렉션 조건을 마이그레이션할 수 있습니다. 이 경우 개체 기반 마이그레이션 작업을 사용할 수 있습니다. 컬렉션을 마이그레이션할 때 컬렉션의 규칙은 마이그레이션하지만 컬렉션의 구성원에 대한 정보나 컬렉션의 구성원과 관련된 정보 또는 개체는 마이그레이션하지 않습니다.  

 Configuration Manager 2007 원본 계층에서 마이그레이션할 때 컬렉션 개체는 마이그레이션할 수 없습니다.  

##  <a name="Plan_migrate_OSD"></a> 운영 체제 배포 마이그레이션 계획  
지원되는 원본 계층에서 다음 운영 체제 배포 개체를 마이그레이션할 수 있습니다.  

-   운영 체제 이미지 및 패키지. 부팅 이미지의 원본 경로가 대상 사이트의 Windows AIK(Windows 자동 설치 키트)의 기본 이미지 위치로 업데이트됩니다. 다음은 운영 체제 이미지 및 패키지를 마이그레이션하기 위한 요구 사항 및 제한 사항입니다.  

    -   이미지 파일을 성공적으로 마이그레이션하려면 대상 계층 구조 최상위 사이트의 SMS 공급자 서버 컴퓨터 계정에 원본 사이트 Windows AIK 위치의 이미지 원본 파일에 대한 **읽기** 및 **쓰기** 권한이 있어야 합니다.  

    -   운영 체제 설치 패키지를 마이그레이션하는 경우 원본 사이트의 패키지 구성이 WIM 파일 자체가 아니라 WIM 파일이 있는 폴더를 가리켜야 합니다. 설치 패키지가 WIM 파일을 가리키면 설치 패키지가 마이그레이션되지 않습니다.  

    -   Configuration Manager 2007 원본 사이트에서 부팅 이미지 패키지를 마이그레이션하는 경우에는 대상 사이트에서 패키지의 패키지 ID가 유지되지 않습니다. 그러면 대상 계층의 클라이언트가 공유 배포 지점에서 사용할 수 있는 부팅 이미지 패키지를 사용할 수 없게 됩니다.  

-   작업 순서. 클라이언트 설치 패키지에 대한 참조가 있는 작업 순서를 마이그레이션하면 해당 참조가 대상 계층 구조의 클라이언트 설치 패키지에 대한 참조로 바뀝니다.  

    > [!NOTE]  
    >  작업 순서를 마이그레이션할 때 Configuration Manager에서 대상 계층에 필요 없는 개체를 마이그레이션할 수 있습니다. 이러한 개체에는 부팅 이미지와 Configuration Manager 2007 클라이언트 설치 패키지가 포함됩니다.  

-   드라이버 및 드라이버 패키지 드라이버 패키지를 마이그레이션할 때 대상 계층에 있는 SMS 공급자의 컴퓨터 계정은 패키지 원본에 대해 모든 권한을 갖고 있어야 합니다.

##  <a name="Plan_Migrate_Compliance_settings"></a> 원하는 구성 관리 마이그레이션 계획  
구성 항목 및 구성 기준을 마이그레이션할 수 있습니다.  

> [!NOTE]  
>  Configuration Manager 2007 원본 계층에서 해석되지 않는 구성 항목은 마이그레이션할 수 없습니다. 이러한 구성 항목은 대상 계층으로 마이그레이션하거나 가져올 수 없습니다. 해석되지 않은 구성 항목에 대한 자세한 내용은 Configuration Manager 2007 문서 라이브러리에서 [원하는 구성 관리의 구성 항목 정보](http://go.microsoft.com/fwlink/?LinkId=103846) 항목의 해석되지 않은 구성 항목을 참조하세요.  

Configuration Manager 2007 구성 팩을 가져올 수 있습니다. 가져오기 프로세스에서 구성 팩이 System Center Configuration Manager와 호환되도록 자동으로 변환됩니다.  

##  <a name="Plan_migrate_Boundaries"></a> 경계 마이그레이션 계획  
 계층 간에 경계를 마이그레이션할 수 있습니다. Configuration Manager 2007에서 경계를 마이그레이션하는 경우 원본 사이트의 각 경계가 동시에 마이그레이션되고, 대상 계층에 만들어진 새 경계 그룹에 추가됩니다. System Center 2012 Configuration Manager 또는 System Center Configuration Manager 계층 구조에서 경계를 마이그레이션하는 경우 선택한 각 경계는 대상 계층 구조의 새 경계 그룹에 추가됩니다.  

 자동으로 생성된 각 경계 그룹은 콘텐츠 위치에 대해 사용할 수 있지만 사이트 할당에는 사용할 수 없습니다. 이를 통해 원본 계층과 대상 계층 간의 사이트 할당에서 경계가 겹치지 않도록 방지됩니다. Configuration Manager 2007 원본 사이트에서 마이그레이션하면 새로 설치되는 Configuration Manager 2007 클라이언트가 대상 계층 구조에 잘못 할당되는 현상을 방지할 수 있습니다. 기본적으로 System Center Configuration Manager 클라이언트는 Configuration Manager 2007 사이트에 자동으로 할당하지 않습니다.  

 마이그레이션하는 동안 대상 계층과 함께 배포 지점을 공유하는 경우 해당 배포와 연결된 모든 경계는 자동으로 대상 계층에 마이그레이션됩니다. 대상 계층에서 마이그레이션은 각 공유 배포 지점에 대해 새로운 읽기 전용 경계 그룹을 만듭니다. 원본 계층의 배포 지점에 대한 경계를 변경하는 경우 대상 계층의 경계 그룹은 다음 데이터 수집 주기 동안 이러한 변경 내용으로 업데이트됩니다.  

##  <a name="Plan_Migrate_reports"></a> 보고서 마이그레이션 계획  
Configuration Manager는 보고서 마이그레이션을 지원하지 않습니다. 대신, SQL Server Reporting Services 보고서 작성기를 사용하여 원본 계층에서 보고서를 내보내고 대상 계층으로 다시 가져올 수 있습니다.  

> [!NOTE]  
>  Configuration Manager 2007 및 System Center Configuration Manager 간의 보고서에 대한 스키마 변경 내용이 있으므로 Configuration Manager 2007 계층 구조에서 가져온 각 보고서를 테스트하여 예상대로 작동하는지 확인합니다.  

보고에 대한 자세한 내용은 [System Center Configuration Manager에서 보고](../../core/servers/manage/reporting.md)를 참조하세요.  

##  <a name="Plan_Migrate_Org_Folders"></a> 조직 폴더 및 검색 폴더의 마이그레이션 계획  
 지원되는 원본 계층에서 대상 계층으로 조직 폴더 및 검색 폴더를 마이그레이션할 수 있습니다. 또한 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층에서 저장된 검색 조건을 대상 계층으로 마이그레이션할 수 있습니다.  

 기본적으로 마이그레이션할 때 마이그레이션 프로세스에 개체 및 컬렉션의 검색 폴더 및 관리 폴더 구조가 유지됩니다. 하지만 마이그레이션 작업 만들기 마법사의 **설정** 페이지에서 이 옵션의 확인란을 선택 취소하여 개체의 조직 구조를 마이그레이션하지 않도록 마이그레이션 작업을 설정할 수 있습니다. 컬렉션의 조직 구조는 항상 유지됩니다.  

 한 가지 예외로는 가상 응용 프로그램을 포함하는 검색 폴더가 있습니다. App-V 패키지가 마이그레이션되면 App-V 패키지는 System Center Configuration Manager에서 응용 프로그램으로 변환됩니다. 검색 폴더의 마이그레이션 이후 남은 패키지만 검색되고, App-V 패키지가 마이그레이션된 경우 응용 프로그램으로의 이러한 변환으로 인해 검색 폴더는 App-V 패키지를 찾지 못합니다.  

 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 계층에서 저장된 검색을 마이그레이션하는 경우 검색 조건이 마이그레이션되며 검색 결과에 대한 정보는 마이그레이션되지 않습니다. 저장된 검색의 마이그레이션은 Configuration Manager 2007 원본 사이트에서 적용되지 않습니다.  

##  <a name="Plan_Migrate_AI"></a> Asset Intelligence 사용자 지정 항목 마이그레이션 계획  
 지원되는 원본 계층에서 대상 계층으로 Asset Intelligence 사용자 지정 항목을 마이그레이션할 수 있습니다. Configuration Manager 2007과 System Center Configuration Manager 간에 Asset Intelligence 사용자 지정 항목의 구조는 크게 변경되지 않았습니다.  

> [!NOTE]  
>  System Center Configuration Manager는 Asset Intelligence Service 2.0(AIS 2.0)을 사용하는 Configuration Manager 2007 사이트에서의 Asset Intelligence 개체 마이그레이션을 지원하지 않습니다.  

##  <a name="Plan_Migrate_SWM_Rules"></a> 소프트웨어 계량 규칙 사용자 지정 항목 마이그레이션 계획  
 Configuration Manager 2007과 System Center Configuration Manager 간의 소프트웨어 계량 규칙은 크게 변경되지 않았습니다. 지원되는 원본 계층에서 대상 계층으로 소프트웨어 계량 규칙을 마이그레이션할 수 있습니다.  

 기본적으로, 대상 계층으로 마이그레이션하는 소프트웨어 계량 규칙은 대상 계층의 특정 사이트와 연결되는 것이 아니며 대신, 계층의 모든 클라이언트에 적용됩니다. 특정 사이트의 클라이언트에 소프트웨어 계량 규칙을 적용하려면 마이그레이션 이후 계량 규칙을 편집해야 합니다.  
