---
title: "컬렉션 소개 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 컬렉션을 사용하는 방법을 소개합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
caps.latest.revision: 8
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 47574218dec5069205f9dba5608c6f136fb032bc


---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>System Center Configuration Manager의 컬렉션 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 컬렉션은 리소스를 관리 가능한 단위로 구성하여 수행할 작업의 종류를 논리적으로 나타내는 구조를 체계적으로 만들 수 있는 방법을 제공합니다. 컬렉션은 한 번에 여러 리소스에 Configuration Manager 작업을 수행하는 데 사용되기도 합니다. 다음 표에서는 Configuration Manager에서 컬렉션을 사용하는 방법에 대한 몇 가지 예를 보여 줍니다.  

|작업|예|  
|---------|-------|  
|리소스 그룹화|조직의 계층 구조를 기반으로 하여 리소스를 논리적으로 그룹화하는 컬렉션을 만들 수 있습니다.<br /><br /> 예를 들어 "런던 본사" Active Directory OU(조직 구성 단위)에 있는 모든 컴퓨터의 컬렉션을 만들 수 있습니다. 이러한 유형의 컬렉션을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)을 참조하세요.<br /><br /> 그런 다음 이 컬렉션을 사용하여 Endpoint Protection 구성, 장치 전원 관리 설정 구성 또는 Configuration Manager 클라이언트 설치와 같은 작업을 수행할 수 있습니다.|  
|응용 프로그램 배포|Microsoft Office 2013이 설치되지 않은 모든 컴퓨터의 컬렉션을 만든 다음 해당 컬렉션의 모든 컴퓨터에 이 소프트웨어를 배포할 수 있습니다.<br /><br /> 또한 응용 프로그램 요구 사항을 사용하여 이 작업을 수행할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램을 만드는 방법](../../../../apps/deploy-use/create-applications.md)을 참조하세요.|  
|클라이언트 설정 관리|Configuration Manager의 기본 클라이언트 설정은 모든 장치 및 모든 사용자에게 적용되지만, 특정 장치 컬렉션 또는 사용자 컬렉션에 적용되는 사용자 지정 클라이언트 설정을 만들 수 있습니다.<br /><br /> 예를 들어 원격 제어를 몇 가지 장치를 제외한 모든 장치에 사용할 수 있도록 하려면, 원격 제어를 허용하도록 기본 클라이언트 설정을 구성한 다음 원격 제어를 허용하지 않는 사용자 지정 클라이언트 설정을 구성합니다. 이러한 사용자 지정 클라이언트 설정을 원격 제어를 사용하지 않을 컴퓨터가 포함된 컬렉션에 배포합니다.<br /><br /> 클라이언트 설정에 컬렉션을 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../../core/clients/deploy/about-client-settings.md)를 참조하세요.|  
|전원 관리|만드는 각 컬렉션에 대해 활성화되지 않은 컬렉션의 컴퓨터가 절전 모드로 전환되는 속도와 같은 전원 설정을 구성할 수 있습니다.<br /><br /> 전원 관리에 컬렉션을 사용하는 방법에 대한 자세한 내용은 [전원 관리 소개](../power/introduction-to-power-management.md)를 참조하세요.|  
|역할 기반 관리|역할 기반 관리에 컬렉션을 사용하여 Configuration Manager 콘솔의 다양한 기능에 액세스할 수 있는 사용자 그룹을 제어할 수 있습니다.<br /><br /> 역할 기반 관리용 컬렉션을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 역할 기반 관리 구성](../../../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.|  
|유지 관리 기간|관리자는 유지 관리 기간을 사용하여 장치 컬렉션 멤버에 대한 다양한 Configuration Manager 작업을 수행할 수 있는 기간을 정의할 수 있습니다. 유지 관리 기간을 사용하여 조직의 생산성에 영향을 미치지 않는 기간 동안 클라이언트 구성 변경이 이루어지도록 할 수 있습니다.<br /><br /> 유지 관리 기간에 대한 자세한 내용은 [System Center Configuration Manager에서 유지 관리 기간을 사용하는 방법](../../../../core/clients/manage/collections/use-maintenance-windows.md)을 참조하세요.|  

 대부분의 관리 작업에서는 하나 이상의 컬렉션을 사용합니다. 예를 들어 장치에 소프트웨어 업데이트를 배포하려면 먼저 소프트웨어 업데이트를 배포할 컬렉션을 식별해야 합니다. 모든 시스템의 기본 제공 컬렉션을 사용할 수 있지만 관리 작업에는 이 컬렉션을 사용하지 않는 것이 좋습니다. 일반적으로 테스트 환경을 제외한 모든 환경에서 사용자 고유의 사용자 지정 컬렉션을 만드는 것이 관리할 장치 또는 사용자를 좀 더 구체적으로 식별하는 데 도움이 됩니다.  

 기본 제공 및 사용자 지정 컬렉션은 Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에 있는 **사용자 컬렉션** 및 **장치 컬렉션** 노드에 표시됩니다.  

 최근에 본 컬렉션은 Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에 있는 **사용자** 노드 및 **장치** 노드에 표시됩니다.  

## <a name="collection-types-in-configuration-manager"></a>Configuration Manager의 컬렉션 유형  
 Configuration Manager에는 일반적인 작업에 사용할 수 있는 몇 가지 기본 제공 컬렉션이 있습니다. 또한 비즈니스 요구 사항에 맞게 리소스를 그룹화하는 사용자 지정 컬렉션을 만들 수 있습니다.  

### <a name="built-in-collections"></a>기본 제공 컬렉션  
 기본적으로 Configuration Manager에는 다음과 같은 컬렉션이 포함되며, 이러한 컬렉션은 수정할 수 없습니다.  

|**컬렉션 이름**|설명|  
|-------------------------|-----------------|  
|**모든 사용자 그룹**|Active Directory 보안 그룹 검색을 사용하여 검색된 사용자 그룹을 포함합니다.|  
|**모든 사용자**|Active Directory 사용자 검색을 사용하여 검색된 사용자를 포함합니다.|  
|**모든 사용자 및 사용자 그룹**|모든 사용자 및 모든 사용자 그룹 컬렉션을 포함합니다. 이 컬렉션은 수정할 수 없으며, 가장 큰 범위의 사용자 및 사용자 그룹 리소스를 포함합니다.|  
|**모든 데스크톱 및 서버 클라이언트**|Configuration Manager 클라이언트가 설치된 서버 및 데스크톱 장치를 포함합니다. 멤버 자격이 하트비트 검색을 통해 유지 관리됩니다.|  
|**모든 모바일 장치**|Configuration Manager에서 관리하는 모바일 장치를 포함합니다. 멤버 자격은 성공적으로 사이트에 할당되거나 Exchange Server 커넥터에서 검색된 모바일 장치로 제한됩니다.|  
|**모든 시스템**|Microsoft Intune에서 등록된 모든 데스크톱 및 서버 클라이언트, 모든 모바일 장치, 모든 알 수 없는 컴퓨터 컬렉션 및 모든 모바일 장치를 포함합니다.<br /><br /> 이 컬렉션은 수정할 수 없으며, 가장 큰 범위의 장치 리소스를 포함합니다.|  
|**알 수 없는 모든 컴퓨터**|여러 컴퓨터 플랫폼에 대한 일반 컴퓨터 레코드를 포함합니다. 이 컬렉션을 사용하면 작업 순서 및 PXE 부팅, 부팅 가능한 미디어 또는 사전 준비된 미디어를 사용하여 운영 체제를 배포할 수 있습니다.|  

### <a name="custom-collections"></a>사용자 지정 컬렉션  
 Configuration Manager에서 사용자 지정 컬렉션을 만드는 경우 해당 컬렉션의 멤버 자격은 하나 이상의 컬렉션 규칙에 의해 결정됩니다. 컬렉션 규칙을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)을 참조하세요. 다음과 같이 네 개의 규칙을 사용할 수 있습니다.  

#### <a name="direct-rule"></a>직접 규칙  
 직접 규칙을 사용하면 컬렉션에 멤버로 추가하려는 사용자 또는 컴퓨터를 선택할 수 있습니다. 이 규칙은 컬렉션의 멤버인 리소스에 대한 직접 제어를 제공합니다. 멤버 자격은 리소스를 Configuration Manager에서 제거하지 않을 경우 자동으로 변경되지 않습니다. 리소스를 직접 규칙 컬렉션에 추가하려면 먼저 Configuration Manager에서 리소스를 검색하거나 리소스를 가져와야 합니다. 직접 규칙 컬렉션은 이 컬렉션 형식을 수동으로 수정해야 하므로 쿼리 규칙 컬렉션보다 관리 오버헤드가 높습니다.  

#### <a name="query-rule"></a>쿼리 규칙  
 쿼리 규칙은 Configuration Manager에서 일정에 따라 실행하는 쿼리를 기반으로 하는 컬렉션의 멤버 자격을 동적으로 업데이트합니다. 예를 들어 Active Directory Domain Services에서 인적 자원 조직 구성 단위의 멤버인 사용자 컬렉션을 만들 수 있습니다. 직접 규칙 컬렉션과 달리 이 컬렉션 멤버 자격은 인적 자원 조직 구성 단위에 새 사용자를 추가하거나 구성 단위에서 제거할 때 자동으로 업데이트됩니다. 쿼리 규칙은 직접 규칙을 사용하여 컬렉션에 장치를 수동으로 추가하는 관리 오버헤드를 제거합니다. 그러나 컬렉션에 추가되는 컴퓨터에 대한 제어 권한이 줄어듭니다. 다음은 쿼리 기반 규칙의 예입니다.  

-   지정한 OU의 모든 사용자  

-   Windows 8을 실행하는 모든 컴퓨터  

-   사용 가능한 디스크 공간이 20GB 이상인 모든 컴퓨터  

#### <a name="include-collections-rule"></a>컬렉션 규칙 포함  
 포함 컬렉션 규칙을 사용하면 Configuration Manager 컬렉션에 다른 컬렉션의 멤버를 포함할 수 있습니다. 포함된 컬렉션의 멤버 자격이 변경되면 Configuration Manager에서 일정에 따라 현재 컬렉션의 멤버 자격을 업데이트합니다.  

#### <a name="exclude-collections-rule"></a>컬렉션 규칙 제외  
 제외 컬렉션 규칙을 사용하면 Configuration Manager 컬렉션에서 다른 컬렉션의 멤버를 제외할 수 있습니다. 제외된 컬렉션의 멤버 자격이 변경되면 Configuration Manager에서 일정에 따라 현재 컬렉션의 멤버 자격을 업데이트합니다.  

> [!NOTE]  
>  컬렉션에 포함 컬렉션 및 제외 컬렉션 규칙이 모두 포함되어 있고 충돌이 있다면 제외 규칙이 포함 규칙에 우선합니다.  

## <a name="incremental-collection-updates"></a>증분 컬렉션 업데이트  
 컬렉션에 대해 증분 업데이트를 사용하는 경우 Configuration Manager는 이전 컬렉션 평가에서 새로 추가되거나 변경된 리소스를 정기적으로 검색하고 전체 컬렉션 평가와 별개로 컬렉션 멤버 자격을 검색된 리소스로 업데이트합니다. 증분 컬렉션 업데이트를 사용하는 경우 기본적으로 5분마다 한 번씩 업데이트가 실행되므로 전체 컬렉션 평가의 오버헤드 없이 컬렉션 데이터를 최신 상태로 유지하는 데 도움이 됩니다.  

> [!NOTE]  
>  새 컬렉션을 만들 때 증분 업데이트는 기본적으로 비활성화됩니다.  



<!--HONumber=Nov16_HO1-->


