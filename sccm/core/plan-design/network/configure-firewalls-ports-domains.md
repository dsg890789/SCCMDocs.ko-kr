---
title: 방화벽 및 도메인
titleSuffix: Configuration Manager
description: System Center Configuration Manager 통신을 준비하기 위해 방화벽, 포트 및 도메인을 설정합니다.
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1cc3a1532a326019db3517c70723831f309be76b
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56127136"
---
# <a name="set-up-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>System Center Configuration Manager용 방화벽, 포트 및 도메인 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 지원을 위해 네트워크를 준비하려면 Configuration Manager에서 사용하는 통신을 전달하도록 방화벽 등의 인프라를 설정할 계획을 세웁니다.  

|고려 사항|세부 정보|  
|-------------------|-------------|  
|다른 Configuration Manager 기능에서 사용되는 **포트 및 프로토콜**. 일부 포트는 필수이며, 다른 **도메인 및 서비스**를 사용자 지정할 수도 있습니다.|대부분의 Configuration Manager 통신에서는 HTTP용 포트 80 또는 HTTPS 통신용 443과 같은 일반 포트를 사용합니다. 그러나 [일부 사이트 시스템 역할은 사용자 지정 웹 사이트](/sccm/core/plan-design/network/websites-for-site-system-servers) 및 사용자 지정 포트 사용을 지원합니다.<br /><br /> **Configuration Manager를 배포하기 전에** 사용할 포트를 식별하고 방화벽을 적절하게 설정합니다.<br /><br /> Configuration Manager를 설치한 후에 **포트를 변경해야 하는 경우**에는 디바이스와 네트워크에서 방화벽을 업데이트하고 Configuration Manager에서 포트 구성을 변경해야 합니다.<br /><br /> 자세한 내용은 다음을 참조하세요. </br>- [클라이언트 통신 포트를 구성하는 방법](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [Configuration Manager에서 사용되는 포트](../../../core/plan-design/hierarchy/ports.md) </br>- [Internet access requirements for the service connection point](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)(서비스 연결 지점의 인터넷 액세스 요구 사항)|  
|사이트 서버와 클라이언트가 사용해야 할 수 있는**도메인 및 서비스**.|Configuration Manager 기능을 사용하려면 사이트 서버와 클라이언트에 Windowsudpate.microsoft.com 또는 Microsoft Intune 서비스와 같은 인터넷의 특정 서비스와 도메인에 대한 액세스 권한이 필요할 수 있습니다.<br /><br /> Microsoft Intune을 사용하여 모바일 디바이스를 관리하려는 경우에는 [Intune에 필요한 포트와 도메인](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)에 대한 액세스 권한도 구성해야 합니다.|  
|사이트 시스템 서버 및 클라이언트 통신용**프록시 서버** . 여러 사이트 시스템 서버와 클라이언트에 대해 각기 다른 프록시 서버를 지정할 수 있습니다.|이러한 구성은 사이트 시스템 역할이나 클라이언트를 설치할 때 수행하므로, 사이트 시스템 역할 및 클라이언트를 구성할 때는 나중에 참조할 수 있도록 프록시 서버 구성만 확인하면 됩니다.<br /><br /> 배포에서 프록시 서버를 사용해야 하는지 여부를 모르는 경우 [System Center Configuration Manager의 프록시 서버 지원](../../../core/plan-design/network/proxy-server-support.md)을 검토하여 프록시 서버를 사용할 수 있는 사이트 시스템 역할 및 클라이언트 작업에 대해 확인하세요.|   
|  
