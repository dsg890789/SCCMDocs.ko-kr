---
title: 사이트 시스템 역할 추가
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 시스템 역할과 사이트의 기능 및 용량을 확장하기 위해 역할을 추가하는 방법을 이해합니다.
ms.date: 02/7/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b90de2d9-494e-43ad-b269-c8ed589f37d3
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 633b61e9a97cf61690168db920c271be11cb2198
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799046"
---
# <a name="add-site-system-roles-for-configuration-manager"></a>Configuration Manager에 대한 사이트 시스템 역할 추가

*적용 대상: Configuration Manager(현재 분기)*

각 Configuration Manager 사이트에서는 여러 사이트 시스템 역할을 지원합니다. 각 역할은 사이트에 서비스를 제공하고 디바이스 및 사용자를 관리하도록 사이트의 기능과 용량을 확장합니다. 사이트 시스템 서버의 각 사이트 시스템 역할은 같은 사이트의 역할이어야 합니다.   

Configuration Manager는 한 사이트 시스템 서버에서 여러 사이트에 대한 사이트 시스템 역할을 지원하지 않습니다.  

> [!TIP]  
>  사이트 시스템 역할과 관련된 기본 사항 또는 사이트 서버/사이트 시스템 서버/사이트 시스템 역할 간의 차이점에 대해 잘 모르는 경우 [Configuration Manager의 기본 사항](../../../../core/understand/fundamentals.md)을 참조하세요.  

 다음 항목에서는 사이트 시스템 역할에 대한 자세한 절차 및 관련 세부 정보를 제공합니다.  

-   [Configuration Manager에 대한 사이트 시스템 역할 설치](../../../../core/servers/deploy/configure/install-site-system-roles.md)  

     이 항목에서는 새 사이트 시스템 역할을 설치하는 데 사용할 수 있는 2개의 콘솔 내 마법사를 사용하는 방법에 대한 기본 지침을 제공합니다.  

-   [Microsoft Azure에서 Configuration Manager에 대한 클라우드 기반 배포 지점 설치](../../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md)  

    Microsoft Azure를 사용하여 클라이언트에 배포하는 콘텐츠를 호스트하려는 경우 이 항목의 정보를 사용하여 Configuration Manager에서 Microsoft Azure 구독과 통신하고 이 구독을 사용하는 데 필요한 인증서 파일을 설정할 수 있습니다. 또한 클라이언트에서 클라우드 기반 배포 지점을 찾을 수 있도록 이름 확인을 설정해야 합니다.  

-   [온-프레미스 모바일 디바이스 관리를 위한 사이트 시스템 역할 설치](../../../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     이 항목의 내용은 Configuration Manager 온-프레미스 MDM을 사용하여 최신 디바이스 관리를 지원하도록 사이트 시스템 역할을 설정하는 데 도움이 됩니다.  

-   [Configuration Manager의 사이트 시스템 역할에 대한 구성 옵션](../../../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md)  

     일부 사이트 시스템 역할은 사용자 인터페이스서 설명할 수 있는 것보다 더 자세한 정보를 필요로 하는 구성을 지원합니다. 이 항목에서 세부 정보를 제공합니다.  
