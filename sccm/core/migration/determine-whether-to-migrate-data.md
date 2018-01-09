---
title: "마이그레이션 항목 선택"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에 마이그레이션할 수 있는 데이터와 마이그레이션할 수 없는 데이터를 알아봅니다."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99222dc8-0e1e-4513-8302-7a1acf671e9b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 822bc5b4e17bdc611243fadfb13c551b0a8237a8
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2018
---
# <a name="determine-whether-to-migrate-data-to-system-center-configuration-manager"></a>System Center Configuration Manager로 데이터를 마이그레이션할지 여부 결정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 마이그레이션은 지원되는 버전의 Configuration Manager에서 만든 데이터 및 구성을 새 계층 구조로 전송할 수 있는 프로세스를 제공합니다.  이 프로세스를 통해 다음을 수행할 수 있습니다.  

-   여러 계층 구조를 하나로 결합합니다.  

-   랩 배포에서 프로덕션 배포로 데이터 및 구성을 이동합니다.

-   System Center Configuration Manager의 업그레이드 경로가 없는 Configuration Manager 2007과 같은 이전 버전의 Configuration Manager 또는 System Center Configuration Manager의 업그레이드 경로를 지원하는 System Center 2012 Configuration Manager에서 데이터 및 구성을 이동합니다.  

배포 지점 사이트 역할 및 배포 지점을 호스팅하는 컴퓨터를 제외하고 인프라(사이트, 사이트 시스템 역할 또는 사이트 시스템 역할을 호스팅하는 컴퓨터 포함)를 마이그레이션하거나 전송하거나 계층 간에 공유할 수 없습니다.  

 서버 인프라는 마이그레이션할 수 없지만 Configuration Manager 클라이언트는 계층 간에 마이그레이션할 수 있습니다. 클라이언트 마이그레이션 시에는 클라이언트에서 사용하는 데이터를 원본 계층에서 대상 계층으로 마이그레이션한 다음, 클라이언트 소프트웨어를 설치하거나 재할당하므로 클라이언트에서 새 계층에 보고할 수 있습니다.

새 계층 구조에 클라이언트를 설치하고 클라이언트가 해당 데이터를 제출하면 고유한 Configuration Manager ID를 통해 Configuration Manager에서 이전에 마이그레이션한 데이터를 각 클라이언트 컴퓨터에 연결할 수 있습니다.  

 마이그레이션을 통해 제공되는 기능을 사용하면 구성 및 배포에 대한 기존의 투자를 유지하면서도 System Center 2012 Configuration Manager에서 처음 도입되어 System Center Configuration Manager에서 계속 제공되는 첫 번째 제품의 핵심 변경 내용을 모두 활용할 수 있습니다. 이러한 변경 내용으로는 더 적은 사이트와 리소스를 사용하는 간단해진 Configuration Manager 계층 구조와, 64비트 하드웨어에서 실행되는 네이티브 64비트 코드를 사용하여 향상된 처리 기능이 있습니다.  

 마이그레이션에서 지원하는 Configuration Manager 버전에 대한 자세한 내용은 [System Center Configuration Manager에서 수행하는 마이그레이션을 위한 필수 조건](../../core/migration/prerequisites-for-migration.md)을 참조하세요.  

 다음 섹션의 내용을 참조하여 마이그레이션할 수 있는/없는 데이터를 계획할 수 있습니다.  

-   [System Center Configuration Manager로 마이그레이션할 수 있는 데이터](#Can_Migrate)  

-   [System Center Configuration Manager로 마이그레이션할 수 없는 데이터](#Cannot_migrate)  

##  <a name="Can_Migrate"></a> System Center Configuration Manager로 마이그레이션할 수 있는 데이터  
 지원되는 Configuration Manager 계층 구조 간에는 대부분의 개체를 마이그레이션할 수 있습니다. 지원되는 버전의 Configuration Manager 2007에서 마이그레이션된 일부 개체의 인스턴스는 System Center 2012 Configuration Manager 스키마 및 개체 형식에 맞게 수정해야 합니다.

이렇게 수정한 내용은 원본 사이트 데이터베이스의 데이터에 영향을 주지 않습니다. 지원되는 버전의 System Center 2012 Configuration Manager 또는 System Center Configuration Manager에서 마이그레이션된 개체는 수정할 필요가 없습니다.  

 다음에는 원본 계층의 Configuration Manager 버전에 따라 마이그레이션할 수 있는 개체가 나와 있습니다. 쿼리와 같은 일부 개체는 마이그레이션되지 않습니다. 마이그레이션되지 않는 개체를 계속 사용하려면 새 계층에서 다시 만들어야 합니다. 다른 개체(일부 클라이언트 데이터 포함)는 새 계층 구조에서 클라이언트를 관리할 때 해당 계층 구조에서 자동으로 다시 만들어집니다.  

### <a name="objects-that-you-can-migrate-from-system-center-2012-configuration-manager-or-system-center-configuration-manager-current-branch"></a>System Center 2012 Configuration Manager 또는 System Center Configuration Manager 현재 분기에서 마이그레이션할 수 있는 개체

-   보급 알림  

-   System Center 2012 Configuration Manager 이상 버전용 응용 프로그램  

-   System Center 2012 Configuration Manager 이상 버전의 App-V 가상 환경  

-   Asset Intelligence 사용자 지정  

-   경계  

-   컬렉션: 지원되는 버전의 System Center 2012 Configuration Manager 또는 System Center Configuration Manager에서 컬렉션을 마이그레이션하려면 개체 마이그레이션 작업을 사용합니다.  

-   준수 설정:  

    -   구성 기준  

    -   구성 항목  

-   운영 체제 배포:  

    -   부팅 이미지  

    -   드라이버 패키지  

    -   드라이버  

    -   이미지  

    -   패키지  

    -   작업 순서  

-   검색 결과: 저장된 검색 조건  

-   소프트웨어 업데이트:  

    -   배포  

    -   배포 패키지  

    -   템플릿  

    -   소프트웨어 업데이트 목록  

-   소프트웨어 배포 패키지  

-   소프트웨어 계량 규칙  

-   가상 응용 프로그램 패키지  

### <a name="objects-that-you-can-migrate-from-configuration-manager-2007-sp2"></a>Configuration Manager 2007 SP2에서 마이그레이션할 수 있는 개체

-   보급 알림  

-   System Center 2012 Configuration Manager 이상 버전용 응용 프로그램  

-   System Center 2012 Configuration Manager 이상 버전의 App-V 가상 환경  

-   Asset Intelligence 사용자 지정  

-   경계  

-   컬렉션: 컬렉션 마이그레이션 작업을 사용하여 지원되는 Configuration Manager 2007 버전에서 컬렉션을 마이그레이션합니다.  

-   호환성 설정(Configuration Manager 2007에서는 Desired Configuration Management이라고 함)  

    -   구성 기준  

    -   구성 항목  

-   운영 체제 배포:  

    -   부팅 이미지  

    -   드라이버 패키지  

    -   드라이버  

    -   이미지  

    -   패키지  

    -   작업 순서  

-   검색 결과: 검색 폴더  

-   소프트웨어 업데이트:  

    -   배포  

    -   배포 패키지  

    -   템플릿  

    -   소프트웨어 업데이트 목록  

-   소프트웨어 배포 패키지  

-   소프트웨어 계량 규칙  

-   가상 응용 프로그램 패키지  

##  <a name="Cannot_migrate"></a> System Center Configuration Manager로 마이그레이션할 수 없는 데이터  
 다음과 같은 유형의 개체는 마이그레이션할 수 없습니다.  

-   AMT 클라이언트 프로비전 정보  

-   클라이언트의 다음 파일:  

    -   클라이언트 인벤토리 및 기록 데이터  

    -   클라이언트 캐시의 파일  

-   쿼리  

-   사이트 및 개체에 대한 Configuration Manager 2007 보안 권한 및 인스턴스  

-   SQL Server Reporting Services의 Configuration Manager 2007 보고서  

-   Configuration Manager 2007 웹 보고서  

-   System Center 2012 Configuration Manager 및 System Center Configuration Manager 보고서  

-   System Center 2012 Configuration Manager 및 System Center Configuration Manager 역할 기반 관리:  

    -   보안 역할  

    -   보안 범위  
