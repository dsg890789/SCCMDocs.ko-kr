---
title: 보고 기능 소개
titleSuffix: Configuration Manager
description: Configuration Manager에서 보고를 관리할 수 있도록 제공되는 도구 및 리소스 집합을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 230be984-d2cd-4d53-bd7a-bc24dd93fc22
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: c42b8a97c5ceb5bdff64def06f18275585c51dc6
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70379783"
---
# <a name="introduction-to-reporting-in-system-center-configuration-manager"></a>System Center Configuration Manager의 보고 기능 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 보고 기능은 SSRS(SQL Server Reporting Services)의 고급 보고 기능과 Reporting Services 보고서 작성기가 제공하는 풍부한 제작 환경을 사용할 수 있도록 하는 일련의 도구와 리소스를 제공합니다. 보고 기능을 사용하면 사용자, 하드웨어, 소프트웨어 인벤토리, 소프트웨어 업데이트, 애플리케이션, 사이트 상태 및 조직의 기타 Configuration Manager 작업에 대한 정보를 수집, 구성 및 제공할 수 있습니다. 보고 기능은 다양한 미리 정의된 보고서를 제공하여, 이를 변경 없이 그대로 사용하거나 요구 사항에 맞게 수정할 수 있습니다. 또한 사용자 지정 보고서를 만들 수 있습니다. 다음 섹션을 사용하여 Configuration Manager의 보고를 관리할 수 있습니다.  

##  <a name="BKMK_SQLServerReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services는 조직의 보고서를 만들고 배포하고 관리하는 데 도움이 되는 즉시 사용 가능한 광범위한 도구 및 서비스와 더불어, 보고 기능을 확장하고 사용자 지정할 수 있도록 하는 프로그래밍 기능을 제공합니다. Reporting Services는 서버 기반의 보고 플랫폼으로서 다양한 데이터 원본에 대한 포괄적인 보고 기능을 제공합니다.  

 Configuration Manager에서는 SQL Server Reporting Services를 보고 솔루션으로 사용합니다. Reporting Services와의 통합에 따른 다음과 같은 이점이 있습니다.  

- 업계 표준 보고 시스템을 사용하여 Configuration Manager 데이터베이스를 쿼리합니다.  

- 보고서의 웹 기반 연결인 Configuration Manager 보고서 뷰어 또는 보고서 관리자를 사용하여 보고서를 표시할 수 있습니다.  

- 고성능, 가용성 및 확장성을 제공합니다.  

- 구독 기능을 통해 사용자가 보고서를 구독할 수 있습니다. 예를 들어 관리자가 매일 소프트웨어 업데이트 배포 상태에 대한 보고서를 전자 메일로 자동 전송 받도록 구독할 수 있습니다.  

- 사용자가 일반적으로 사용되는 다양한 형식을 선택하여 보고서를 내보낼 수 있습니다.  

  Reporting Services에 대한 자세한 내용은 SQL Server 2008 Books Online의 [SQL Server Reporting Services](https://go.microsoft.com/fwlink/p/?LinkID=212032) 를 참조하세요.  

##  <a name="BKMK_ReportingServicesPoint"></a> 보고 서비스 지점  
 보고 서비스 지점은 Microsoft SQL Server Reporting Services를 실행하는 서버에 설치되는 사이트 시스템 역할입니다. 보고 서비스 지점은 Configuration Manager 보고서 정의를 Reporting Services로 복사하고, 보고서 범주를 기반으로 보고서 폴더를 만들며, Configuration Manager 관리자의 역할 기반 권한에 따라 보고서 폴더와 보고서에 대한 보안 정책을 설정합니다. 보고 서비스 지점은 10분 간격으로 Reporting Services에 연결하여 보안 정책이 변경된 경우 보고서 관리자 등을 사용해서 보안 정책을 다시 적용합니다. 보고 서비스 지점을 계획하고 설치하는 방법에 대한 자세한 내용은 다음 문서를 참조하세요.  

-   [System Center Configuration Manager의 보고 계획](planning-for-reporting.md)  

-   [System Center Configuration Manager의 보고 구성](configuring-reporting.md)  

##  <a name="BKMK_ConfigurationManagerReports"></a> Configuration Manager 보고서  
 Configuration Manager에서는 50여 개의 보고서 폴더에 있는 400개 이상의 보고서에 대한 보고서 정의를 제공하며, 이는 보고 서비스 지점 설치 과정에서 SQL Server Reporting Services의 루트 보고서 폴더로 복사됩니다. 보고서는 Configuration Manager 콘솔에 표시되며 보고서 범주에 따라 여러 하위 폴더로 구성됩니다. 보고서는 Configuration Manager 계층 구조의 위 또는 아래로 전파되지 않으며 보고서가 생성된 사이트의 데이터베이스에 대해서만 실행됩니다. 그러나 Configuration Manager에서 계층 구조 전체에 글로벌 데이터를 복제하므로 계층 구조 수준의 정보에 액세스할 수 있습니다. 보고서는 사이트 데이터베이스에서 데이터를 검색할 때 현재 사이트와 자식 사이트의 사이트 데이터와 해당 계층에 있는 모든 사이트의 전역 데이터에 액세스할 수 있습니다. 다른 Configuration Manager 개체와 마찬가지로, 관리자는 보고서를 실행하거나 수정할 수 있는 적절한 권한을 갖습니다. 보고서를 실행하려면 관리자에게 개체에 대한 **보고서 실행** 권한이 있어야 합니다. 보고서를 만들거나 수정하려면 관리자에게 개체에 대한 **보고서 수정** 권한이 있어야 합니다.  

###  <a name="BKMK_CreatingReports"></a> 보고서 만들기 및 수정  
 Configuration Manager에서는 모델 기반 및 SQL 기반 보고서에 대한 전용 제작 및 편집 도구로 Microsoft SQL Server 보고서 작성기를 사용합니다. Configuration Manager 콘솔에서 보고서를 만들거나 편집하는 경우 보고서 작성기가 열립니다. 보고서 관리 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 작업 및 유지 관리](operations-and-maintenance-for-reporting.md)를 참조하세요.  

###  <a name="BKMK_RunningReports"></a> 보고서 실행  
 Configuration Manager 콘솔에서 보고서를 실행하면 보고서 뷰어가 열려 Reporting Services에 연결됩니다. 필요한 보고 매개 변수를 지정하면 Reporting Services에서 해당 데이터가 검색되어 뷰어에 결과가 표시됩니다. 또한 SQL Services Reporting Services에 연결한 후 사이트의 데이터 원본에 연결하여 보고서를 실행할 수 있습니다.  

###  <a name="BKMK_ReportPrompts"></a> 보고서 프롬프트  
 Configuration Manager의 보고서 프롬프트 또는 보고서 매개 변수는 보고서를 만들거나 수정할 때 구성할 수 있는 보고서 속성입니다. 보고서 프롬프트는 보고서에서 검색하는 데이터를 제한하거나 지정하기 위해 만듭니다. 보고서에는 둘 이상의 프롬프트가 포함될 수 있습니다. 단, 각 프롬프트 이름이 고유하고 SQL Server의 식별자 규칙에 따른 영숫자 문자만 포함해야 합니다.  

 보고서를 실행하면 프롬프트가 필요한 매개 변수의 값을 요청하고 해당 값에 따라 보고서 데이터를 검색합니다. 예를 들어 **특정 컴퓨터의 컴퓨터 정보** 보고서는 특정 컴퓨터에 대한 컴퓨터 정보를 검색하고 관리자에게 컴퓨터 이름을 입력하도록 요청합니다. Reporting Services는 지정된 값을 해당 보고서에 대해 SQL 문에 정의된 변수로 전달합니다.  

###  <a name="BKMK_ReportLinks"></a> 보고서 링크  
 Configuration Manager의 보고서 링크는 원본 보고서에 사용되어 관리자가 원본 보고서의 각 항목에 대한 자세한 정보와 같은 추가 데이터를 손쉽게 액세스할 수 있도록 합니다. 대상 보고서에서 하나 이상의 프롬프트를 실행해야 하는 경우 원본 보고서에 각 프롬프트에 대해 해당 값을 갖는 열을 포함해야 합니다. 프롬프트의 값을 제공하는 열 번호를 지정해야 합니다. 예를 들어 최근에 검색된 컴퓨터 목록이 있는 보고서를 특정 컴퓨터에 대해 받은 마지막 메시지 목록이 있는 보고서에 연결해야 할 수 있습니다. 링크가 만들어지면 대상 보고서에 필요한 프롬프트인 컴퓨터 이름이 원본 보고서의 열 2에 포함되도록 지정해야 할 수 있습니다. 원본 보고서가 실행되면 링크 아이콘이 각 데이터 행 왼쪽에 표시됩니다. 행에 있는 아이콘을 클릭하면 보고서 뷰어가 해당 행의 지정된 열 값을 대상 보고서를 표시하는 데 필요한 프롬프트 값으로 전달합니다. 보고서는 하나의 링크만 사용해서 구성할 수 있고 이 링크를 하나의 대상 리소스에만 연결할 수 있습니다.  

> [!WARNING]  
>  대상 보고서를 다른 보고서 폴더로 이동하는 경우 대상 보고서의 위치가 변경됩니다. 원본 보고서의 보고서 링크는 새 위치로 자동 업데이트되지 않고 보고서 링크가 원본 보고서에서 작동하지 않게 됩니다.  

##  <a name="BKMK_ReportFolders"></a> 보고서 폴더  
 System Center Configuration Manager의 보고서 폴더에서는 Reporting Services에 저장된 보고서를 정렬 및 필터링하기 위한 방법을 제공합니다. 보고서 폴더는 관리할 보고서가 많은 경우에 특히 유용합니다. 보고 서비스 지점을 설치하면 보고서가 Reporting Services로 복사되고 50여 개의 보고서 폴더로 구성됩니다. 보고서 폴더는 읽기 전용으로, Configuration Manager 콘솔에서는 수정할 수 없습니다.  

##  <a name="BKMK_ReportSubscriptions"></a> 보고서 구독  
 Reporting Services의 보고서 구독은 특정 시간이나 이벤트에 대응하여 구독에 지정된 애플리케이션 파일 형식으로 보고서를 배달하기 위한 되풀이 요청입니다. 구독은 주문형으로 보고서를 실행하는 것의 대안입니다. 주문형 보고를 사용하려면 보고서를 보려고 할 때마다 보고서를 직접 선택해야 합니다. 반면 구독을 사용하면 보고서 배달을 예약하여 자동화할 수 있습니다.  

 Configuration Manager 콘솔에서 보고서 구독을 관리할 수 있습니다. 보고서 구독은 보고서 서버에서 처리됩니다. 구독은 서버에 배포된 배달 확장을 사용하여 배포됩니다. 기본적으로 공유 폴더 또는 전자 메일 주소로 보고서를 전송하는 구독을 만들 수 있습니다. 보고서 구독 관리 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 작업 및 유지 관리](operations-and-maintenance-for-reporting.md)를 참조하세요.  

##  <a name="BKMK_ReportBuilder"></a> 보고서 작성기  
 Configuration Manager에서는 모델 기반 및 SQL 기반 보고서 둘 다에 대한 전용 제작 및 편집 도구로 Microsoft SQL Server Reporting Services 보고서 작성기를 사용합니다. Configuration Manager 콘솔에서 보고서를 만들거나 편집하기 시작하면 보고서 작성기가 열립니다. 보고서를 처음으로 만들거나 수정할 때 보고서 작성기가 자동으로 설치됩니다. 보고서를 실행하거나 편집할 때 설치된 SQL Server 버전에 연결된 보고서 작성기 버전이 열립니다.  

 보고서 작성기는 20개 이상의 언어로 설치할 수 있습니다. 보고서 작성기를 실행하면 로컬 컴퓨터에서 실행되는 운영 체제 언어로 데이터가 표시됩니다. 보고서 작성기가 해당 언어를 지원하지 않을 경우 데이터가 영어로 표시됩니다. 보고서 작성기는 다음 기능을 포함하여 SQL Server 2008 Reporting Services의 전체 기능을 지원합니다.  

- Microsoft Office와 비슷한 모양의 직관적인 보고서 제작 환경을 제공합니다.  

- SQL Server 2008 RDL(Report Definition Language)의 유연한 보고서 레이아웃을 제공합니다.  

- 차트와 계기를 포함한 다양한 형태의 데이터 시각화를 제공합니다.  

- 서식 있는 텍스트 상자를 제공합니다.  

- Microsoft Word 형식으로 내보낼 수 있습니다.  

  또한 SQL Server Reporting Services에서 보고서 작성기를 열 수도 있습니다.  

##  <a name="BKMK_ReportModels"></a> SQL Server Reporting Services의 보고서 모델  
 Configuration Manager의 SQL Reporting Services는 관리자가 모델 기반 보고서에 포함할 항목을 데이터베이스에서 선택할 수 있도록 하는 보고서 모델을 사용합니다. 보고서를 작성하는 관리자에게는 지정된 보기와 선택할 항목만 표시됩니다. 모델 기반 보고서를 작성하려면 하나 이상의 보고서 모델을 사용할 수 있어야 합니다. 보고서 모델은 다음과 같은 기능이 있습니다.  

- 보고서 작성에 도움이 되는 논리적 비즈니스 이름을 데이터베이스 필드와 보기에 지정할 수 있습니다. 보고서를 작성하는 데 데이터베이스 구조에 대한 지식은 필요 없습니다.  

- 항목을 논리적으로 그룹화할 수 있습니다.  

- 항목 간의 관계를 정의할 수 있습니다.  

- 관리자가 권한이 있는 데이터만 볼 수 있도록 모델 요소에 보안을 설정할 수 있습니다.  

  Configuration Manager에서 샘플 보고서 모델을 제공하긴 하지만 해당 비즈니스 요구 사항에 맞춰 보고서 모델을 정의할 수 있습니다. 보고서 모델을 만드는 방법에 대한 자세한 내용은 [SQL Server Reporting Services에서 System Center Configuration Manager에 대한 사용자 지정 보고서 모델 만들기](creating-custom-report-models-in-sql-server-reporting-services.md)를 참조하세요.  

## <a name="next-steps"></a>다음 단계
[보고 계획](planning-for-reporting.md)
