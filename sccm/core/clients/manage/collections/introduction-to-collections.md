---
title: "컬렉션 소개 | Microsoft 문서"
description: "System Center Configuration Manager에서 컬렉션을 사용하는 방법을 소개합니다."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
caps.latest.revision: 8
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 05c27c7aa36e0b4236867766dab36125c31467b3
ms.openlocfilehash: fd4c6fd85d12592b3d4f57a48cf6da6c7a668615
ms.contentlocale: ko-kr
ms.lasthandoff: 01/03/2017


---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>System Center Configuration Manager의 컬렉션 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

컬렉션을 사용하면 리소스를 관리 가능한 단위로 구성할 수 있습니다. 클라이언트 관리 요구에 맞게 컬렉션을 만들고 여러 리소스에 대한 작업을 한 번에 수행할 수 있습니다. 

대부분의 관리 작업에서는 하나 이상의 컬렉션을 사용하거나 사용해야 합니다. 기본 제공 컬렉션인 모든 시스템을 사용할 수도 있지만 관리 작업에는 이 컬렉션을 사용하지 않는 것이 좋습니다. 작업의 사용자나 장치를 보다 구체적으로 식별하려면 사용자 지정 컬렉션을 만드세요.  

 기본 제공 및 사용자 지정 컬렉션은 Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에 있는 **사용자 컬렉션** 및 **장치 컬렉션** 노드에 표시됩니다.  

 최근에 본 컬렉션은 **자산 및 준수** 작업 영역에 있는 **사용자** 노드 및 **장치** 노드에 표시됩니다.  

아래에는 컬렉션 사용 방식의 몇 가지 예가 나와 있습니다.  

|작업|예|  
|---------|-------|  
|리소스 그룹화|조직의 계층을 기반으로 하여 리소스를 그룹화하는 컬렉션을 만들 수 있습니다.<br /><br /> 예를 들어 "런던 본사" Active Directory OU(조직 구성 단위)에 있는 모든 컴퓨터의 컬렉션을 만들 수 있습니다. 이러한 유형의 컬렉션을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)을 참조하세요.<br /><br /> 이 컬렉션을 사용하여 Endpoint Protection 설정 구성, 장치 전원 관리 설정 구성 또는 Configuration Manager 클라이언트 설치와 같은 작업을 수행할 수 있습니다.|  
|[응용 프로그램 배포]|Microsoft Office 2013이 설치되지 않은 모든 컴퓨터의 컬렉션을 만든 다음 해당 컬렉션의 모든 컴퓨터에 Microsoft Office 2013을 배포할 수 있습니다.<br /><br /> 또한 응용 프로그램 요구 사항을 사용하여 이 작업을 수행할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램을 만드는 방법](../../../../apps/deploy-use/create-applications.md)을 참조하세요.|  
|[클라이언트 설정 관리](../../../../core/clients/deploy/about-client-settings.md)|Configuration Manager의 기본 클라이언트 설정은 모든 장치 및 모든 사용자에게 적용되지만, 특정 장치 컬렉션 또는 사용자 컬렉션에 적용되는 사용자 지정 클라이언트 설정을 만들 수 있습니다.<br /><br /> 예를 들어 소수의 장치만을 제외한 모든 장치에서 원격 제어를 사용할 수 있도록 하려면 원격 제어를 허용하도록 기본 클라이언트 설정을 구성한 다음 원격 제어를 허용하지 않는 사용자 지정 클라이언트 설정을 구성하여 예외 클라이언트 컬렉션에 해당 설정을 배포합니다. |  
|[전원 관리](../power/introduction-to-power-management.md)|컬렉션별로 특정 전원 설정을 구성할 수 있습니다.|  
|[역할 기반 관리](../../../../core/servers/deploy/configure/configure-role-based-administration.md)|컬렉션을 사용하여 Configuration Manager 콘솔의 다양한 기능에 액세스할 수 있는 사용자 그룹을 제어할 수 있습니다.|  
|[유지 관리 기간](../../../../core/clients/manage/collections/use-maintenance-windows.md)|유지 관리 기간을 사용하면 장치 컬렉션 멤버에 대해 다양한 Configuration Manager 작업을 수행할 수 있는 기간을 정의할 수 있습니다. |  


## <a name="collection-types-in-configuration-manager"></a>Configuration Manager의 컬렉션 유형  
 Configuration Manager에는 일반 작업을 위한 기본 제공 컬렉션이 포함되어 있으며, 사용자 지정 컬렉션을 만들 수도 있습니다.   

### <a name="built-in-collections"></a>기본 제공 컬렉션  
 기본적으로 Configuration Manager에는 다음과 같은 컬렉션이 포함되며, 이러한 컬렉션은 수정할 수 없습니다.  

|**컬렉션 이름**|설명|  
|-------------------------|-----------------|  
|**모든 사용자 그룹**|Active Directory 보안 그룹 검색을 사용하여 검색된 사용자 그룹을 포함합니다.|  
|**모든 사용자**|Active Directory 사용자 검색을 사용하여 검색된 사용자를 포함합니다.|  
|**모든 사용자 및 사용자 그룹**|모든 사용자 및 모든 사용자 그룹 컬렉션을 포함합니다. 이 컬렉션은 가장 큰 범위의 사용자 및 사용자 그룹 리소스를 포함합니다.|  
|**모든 데스크톱 및 서버 클라이언트**|Configuration Manager 클라이언트가 설치된 서버 및 데스크톱 장치를 포함합니다. 멤버 자격이 하트비트 검색을 통해 유지 관리됩니다.|  
|**모든 모바일 장치**|Configuration Manager에서 관리하는 모바일 장치를 포함합니다. 멤버 자격은 성공적으로 사이트에 할당되거나 Exchange Server 커넥터에서 검색된 모바일 장치로 제한됩니다.|  
|**모든 시스템**|모든 데스크톱 및 서버 클라이언트, 모든 모바일 장치 및 모든 알 수 없는 컴퓨터 컬렉션 및 Microsoft Intune에서 등록된 모든 모바일 장치를 포함합니다. 이 컬렉션은 가장 큰 범위의 장치 리소스를 포함합니다.|  
|**알 수 없는 모든 컴퓨터**|여러 컴퓨터 플랫폼에 대한 일반 컴퓨터 레코드를 포함합니다. 이 컬렉션을 사용하면 작업 순서 및 PXE 부팅, 부팅 가능한 미디어 또는 사전 준비된 미디어를 사용하여 운영 체제를 배포할 수 있습니다.|  

### <a name="custom-collections"></a>사용자 지정 컬렉션  
 Configuration Manager에서 사용자 지정 컬렉션을 만드는 경우 해당 컬렉션의 멤버 자격은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)에서 설명하는 것처럼 하나 이상의 컬렉션 규칙에 의해 결정됩니다. 


