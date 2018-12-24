---
title: 디바이스 및 사용자 리소스 검색
titleSuffix: Configuration Manager
description: 검색 프로세스 및 검색 데이터 기록 개요를 읽습니다.
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7d43415ce9517843490c815f7c9f2f3490e87674
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32338502"
---
# <a name="run-discovery-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 검색 실행

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 하나 이상의 검색 방법을 사용하여 관리할 수 있는 디바이스와 사용자 리소스를 찾습니다. 검색을 사용하여 환경 내의 네트워크 인프라를 식별할 수도 있습니다. 다양한 방법으로 여러 항목을 검색할 수 있습니다. 각 방법에는 고유한 구성이 사용되며 제한이 적용됩니다.  

## <a name="overview-of-discovery"></a>검색 프로세스의 개요  
 검색이란 Configuration Manager에서 관리할 수 있는 항목을 인식하는 프로세스입니다. 사용할 수 있는 검색 방법은 다음과 같습니다.  

-   Active Directory 포리스트 검색  

-   Active Directory 그룹 검색  

-   Active Directory 시스템 검색  

-   Active Directory 사용자 검색  

-   하트비트 검색  

-   네트워크 검색  

-   서버 검색  

> [!TIP]  
>  개별 검색 방법은 [System Center Configuration Manager에 대한 검색 방법 정보](../../../../core/servers/deploy/configure/about-discovery-methods.md)에서 알아볼 수 있습니다.  
>   
>  사용할 방법과 계층의 사이트를 선택하는 데 도움이 필요한 경우 [System Center Configuration Manager에 사용할 검색 방법 선택](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)을 참조하세요.  

 대부분의 검색 방법을 사용하기 위해서는 사이트에서 원하는 방법을 사용하도록 설정하고 특정 네트워크 또는 Active Directory 위치를 검색하도록 설정해야 합니다. 검색 방법을 실행하면 Configuration Manager에서 관리할 수 있는 디바이스 또는 사용자에 대한 정보에 대해 지정된 위치를 쿼리합니다. 검색 방법을 통해 리소스에 대한 정보를 찾으면 검색에서 해당 정보를 DDR(검색 데이터 레코드)이라는 파일에 저장합니다. 그 후에 파일은 기본 또는 중앙 관리 사이트에서 처리합니다. DDR이 처리되면 새로 검색된 리소스에 대해 사이트 데이터베이스에 새 레코드가 생성되거나 새 정보를 사용하여 기존 레코드가 업데이트됩니다.  

 일부 검색에서는 대량의 네트워크 트래픽이 발생할 수 있으며 검색에서 생성된 DDR을 처리하느라 상당한 CPU 리소스가 사용될 수 있습니다. 따라서 목표를 충족하는 데 필요한 검색 방법만 사용하도록 계획하세요. 한두 가지 검색 방법을 사용하고 제어된 방식으로 추가 방법을 사용하도록 설정하여 환경의 검색 수준을 확장할 수 있습니다.  

 사이트 데이터베이스에 추가된 검색 정보는 검색되거나 처리된 위치와 관계없이 계층의 각 사이트로 복제됩니다. 따라서 여러 사이트의 검색 방법에 다른 일정과 설정을 사용하면서 특정 방법을 한 사이트에서만 실행할 수도 있습니다. 그러면 중복 검색 작업을 통해 네트워크 대역폭 사용을 줄이고, 여러 사이트에서 중복 검색 데이터의 처리를 줄일 수 있습니다.  

 검색 데이터를 사용하여 관리 작업을 위해 리소스를 논리적으로 그룹화하는 사용자 지정 컬렉션과 쿼리를 만들 수 있습니다. 예:  

-   강제 클라이언트 설치 또는 업그레이드  

-   사용자 또는 디바이스에 콘텐츠 배포  

-   클라이언트 설정 및 관련 구성 배포

##  <a name="BKMK_DDRs"></a> 검색 데이터 기록 정보  
 DDR은 검색 방법으로 만든 파일입니다. Configuration Manager에서 관리할 수 있는 컴퓨터, 사용자와 같은 리소스(경우에 따라 네트워크 인프라도 포함)에 대한 정보가 포함되어 있습니다. DDR은 기본 사이트 또는 중앙 관리 사이트에서 처리됩니다. DDR의 리소스 정보가 데이터베이스에 입력된 후에는 DDR이 삭제되고 해당 정보가 글로벌 데이터로 해당 계층의 모든 사이트에 복제됩니다.  

 DDR이 처리되는 사이트는 DDR에 포함된 정보에 따라 달라집니다.  

-   데이터베이스에 없고 새로 검색된 리소스에 대한 DDR은 계층의 최상위 사이트에서 처리됩니다. 최상위 사이트에서 데이터베이스에 새 리소스 레코드가 만들어지고 이 레코드에 고유 식별자가 할당됩니다. DDR은 최상위 사이트에 도달할 때까지 파일 기반 복제를 통해 전송됩니다.  

-   이전에 검색된 개체에 대한 DDR은 기본 사이트에서 처리됩니다. 데이터베이스에 이미 있는 리소스에 대한 정보가 DDR에 포함된 경우 자식 기본 사이트에서 DDR을 중앙 관리 사이트로 전송하지 않습니다.  

-   보조 사이트에서는 DDR을 처리하지 않으며 항상 파일 기반 복제를 통해 부모 기본 사이트로 전송합니다.  

DDR 파일은 .ddr 확장명으로 식별되며 일반적으로 약 1KB의 크기를 갖습니다.  

## <a name="get-started-with-discovery"></a>검색 시작:  
 Configuration Manager 콘솔을 사용하여 검색을 설정하려면 수행할 수 있는 방법과 제한 사항(일부 방법에 대한) 간의 차이점을 이해해야 합니다.  

다음과 같은 항목은 검색 방법을 사용하는 데 유용한 기본 사항입니다.  

-   [System Center Configuration Manager에 대한 검색 방법 정보](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [System Center Configuration Manager에 사용할 검색 방법 선택](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

사용할 방법을 알고 있는 경우 [System Center Configuration Manager에 사용할 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)에서 각 방법의 설정에 관한 지침을 찾아보세요.  
