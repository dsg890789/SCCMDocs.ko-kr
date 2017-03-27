---
title: "원격 제어 필수 조건 | Microsoft 문서"
description: "System Center Configuration Manager에서 원격 제어에 대한 필수 조건을 확인합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: eafa0d85935c2009cc63d17b06ed83a4666d7fac
ms.lasthandoff: 12/16/2016


---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 원격 제어에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 원격 제어에는 외부 종속성과 제품 내 종속성이 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|컴퓨터 비디오 카드 드라이버|최적의 원격 제어 성능을 보장하기 위해 최신 비디오 드라이버가 클라이언트 컴퓨터에 설치되었는지 확인합니다.|  

 Windows Embedded, Windows Embedded for POS(Point of Service) 및 Windows Fundamentals for Legacy PC를 실행하는 장치는 원격 제어 뷰어를 지원하지 않지만 원격 제어 클라이언트는 지원합니다.  

 Configuration Manager 원격 제어는 Systems Management Server 2003 또는 Configuration Manager 2007을 실행하는 클라이언트 컴퓨터를 원격으로 관리하는 데 사용할 수 없습니다.  

> [!NOTE]  
>  원격 제어에 대한 외부 의존 관계로 Windows 서비스가 필요하지 않습니다.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>원격 제어 뷰어에 대해 지원되는 운영 체제  
 다음 표에서는 원격 제어 뷰어를 지원하는 운영 체제에 대한 정보를 제공합니다. 지원하는 클라이언트 운영 체제에 대한 정보는 [System Center Configuration Manager에서 지원되는 구성](../../../../core/plan-design/configs/supported-configurations.md)을 참조하세요.  

|운영 체제|뷰어 지원|추가 정보|  
|----------------------|--------------------|----------------------|  
|Windows XP(32비트)|예|이 운영 체제에서 원격 제어 뷰어를 실행하려면 먼저 Microsoft 다운로드 센터에서 [RDC(원격 데스크톱 연결) 클라이언트 업데이트 7.0(KB969084)](https://www.microsoft.com/en-us/download/details.aspx?id=12767)을 다운로드하여 설치해야 합니다.|  
|Windows XP(64비트)|아니요|추가 정보가 없습니다.|  
|Windows Vista(32비트)|예|이 운영 체제에서 원격 제어 뷰어를 실행하려면 먼저 Microsoft 다운로드 센터에서 [RDC(원격 데스크톱 연결) 클라이언트 업데이트 7.0(KB969084)](https://www.microsoft.com/en-us/download/details.aspx?id=12767)을 다운로드하여 설치해야 합니다.|  
|Windows Vista(64비트)|예|이 운영 체제에서 원격 제어 뷰어를 실행하려면 먼저 Microsoft 다운로드 센터에서 [RDC(원격 데스크톱 연결) 클라이언트 업데이트 7.0(KB969084)](https://www.microsoft.com/en-us/download/details.aspx?id=12767)을 다운로드하여 설치해야 합니다.|  
|Windows 7(32비트)|예|추가 정보가 없습니다.|  
|Windows 7(64비트)|예|추가 정보가 없습니다.|  
|Windows Server 2003(32비트)|아니요|추가 정보가 없습니다.|  
|Windows Server 2003(64비트)|아니요|추가 정보가 없습니다.|  
|Windows Server 2008(32비트)|아니요|추가 정보가 없습니다.|  
|Windows Server 2008(64비트)|아니요|추가 정보가 없습니다.|  
|Windows Server 2008 R2(64비트)|예|추가 정보가 없습니다.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|클라이언트에 대해 원격 제어를 사용하도록 설정해야 합니다.|기본적으로 Configuration Manager를 설치할 때 원격 제어가 사용하도록 설정되어 있지 않습니다. 원격 제어를 설정하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 원격 제어 구성](../../../../core/clients/manage/remote-control/configuring-remote-control.md)을 참조하세요.|  
|보고 서비스 지점|원격 제어에 대한 보고서를 실행하려면 보고 서비스 지점 사이트 시스템 역할이 설치되어야 합니다. 자세한 내용은 [System Center Configuration Manager의 보고](../../../../core/servers/manage/reporting.md)를 참조하세요.|  
|원격 제어를 관리하는 보안 권한|컬렉션 리소스에 액세스하고 Configuration Manager 콘솔에서 원격 제어 세션을 시작하려면: **컬렉션**개체에 대한 **AMT 제어**, **읽기**, **리소스 읽기** 및 **원격 제어** 권한이 필요합니다.<br /><br /> **원격 도구 운영자** 보안 역할에는 Configuration Manager에서 원격 제어를 관리하기 위해 필요한 이러한 권한이 포함됩니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager용 역할 기반 관리 구성](../../../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.<br /><br /> 또한 **원격 도구** 클라이언트 설정에서 **원격 제어 및 원격 지원의 허용된 뷰어** 옵션을 사용하여 원격 제어가 허용된 보기 목록에 원격 제어 및 원격 지원을 사용할 권한을 주려는 사용자를 추가해야 합니다.|  

