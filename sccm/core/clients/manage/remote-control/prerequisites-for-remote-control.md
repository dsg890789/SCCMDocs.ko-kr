---
title: 원격 제어 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 원격 제어에 대한 필수 조건을 확인합니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 117ad9a087151db51c4cf33112ab662f53b9134e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332018"
---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 원격 제어에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 원격 제어에는 외부 종속성과 제품 내 종속성이 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|컴퓨터 비디오 카드 드라이버|최적의 원격 제어 성능을 보장하기 위해 최신 비디오 드라이버가 클라이언트 컴퓨터에 설치되었는지 확인합니다.|  

 Windows Embedded, Windows Embedded for POS(Point of Service) 및 Windows Fundamentals for Legacy PC를 실행하는 디바이스는 원격 제어 뷰어를 지원하지 않지만 원격 제어 클라이언트는 지원합니다.  

 Configuration Manager 원격 제어는 Systems Management Server 2003 또는 Configuration Manager 2007을 실행하는 클라이언트 컴퓨터를 원격으로 관리하는 데 사용할 수 없습니다.  

> [!NOTE]  
>  Windows 서비스가 없는 원격 제어에 대 한 외부 종속성으로 필요 합니다.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>원격 제어 뷰어에 대해 지원되는 운영 체제  
Configuration Manager 콘솔에 지원되는 모든 운영 체제에서 원격 제어 뷰어를 사용할 수 있습니다. 자세한 내용은 [System Center Configuration Manager 콘솔에서 지원되는 구성](../../../../core/plan-design/configs/supported-operating-systems-consoles.md)을 참조하세요.   

## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|클라이언트에 대해 원격 제어를 사용하도록 설정해야 합니다.|기본적으로 Configuration Manager를 설치할 때 원격 제어가 사용하도록 설정되어 있지 않습니다. 원격 제어를 설정하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 원격 제어 구성](../../../../core/clients/manage/remote-control/configuring-remote-control.md)을 참조하세요.|  
|보고 서비스 지점|원격 제어에 대한 보고서를 실행하려면 보고 서비스 지점 사이트 시스템 역할이 설치되어야 합니다. 자세한 내용은 [System Center Configuration Manager의 보고](../../../../core/servers/manage/reporting.md)를 참조하세요.|  
|원격 제어를 관리하는 보안 권한|컬렉션 리소스에 액세스하고 Configuration Manager 콘솔에서 원격 제어 세션을 시작하려면 **컬렉션** 개체에 대한 **읽기**, **리소스 읽기** 및 **원격 제어** 권한이 필요합니다.<br /><br /> **원격 도구 운영자** 보안 역할에는 Configuration Manager에서 원격 제어를 관리하기 위해 필요한 이러한 권한이 포함됩니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager용 역할 기반 관리 구성](../../../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.<br /><br /> 또한 **원격 도구** 클라이언트 설정에서 **원격 제어 및 원격 지원의 허용된 뷰어** 목록에 이러한 사용자를 추가하여 허용된 뷰어에 원격 제어를 사용할 수 있는 사용 권한을 부여합니다.
