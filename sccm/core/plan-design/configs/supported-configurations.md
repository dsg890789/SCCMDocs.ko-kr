---
title: 지원되는 구성
titleSuffix: Configuration Manager
description: 작동하는 Configuration Manager 배포를 계획, 배포 및 유지 관리할 수 있도록 주요 구성 및 요구 사항을 식별합니다.
ms.date: 10/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 45a10878-ff48-4318-9c6d-c014b38a4039
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 20384ae1705f35fc4b99d4245bbc6a2567428825
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75801718"
---
# <a name="supported-configurations-for-configuration-manager"></a>Configuration Manager에서 지원되는 구성

*적용 대상: Configuration Manager(현재 분기)*

온-프레미스 솔루션인 Configuration Manager는 서버, 클라이언트, 네트워크 구성 및 Microsoft Intune, SQL Server, Azure 등의 추가 제품을 사용합니다.

이 항목과 다음 항목의 정보는 작동하는 Configuration Manager 배포를 계획, 배포 및 유지 관리할 수 있도록 주요 구성, 요구 사항 및 제한 사항을 식별하는 데 필요합니다.  이 정보는 Configuration Manager 사이트, 계층 구조 및 관리 디바이스에 대한 인프라와 관련이 있습니다.

Configuration Manager 기능 또는 특징에 보다 구체적인 구성이 필요한 경우 해당 정보는 기능 관련 설명서에 포함되며 이러한 일반적인 구성 세부 정보를 보완합니다.  

 다음 항목에서 설명하는 제품 및 기술은 Configuration Manager에서 지원됩니다. 그러나 이 내용에 포함되었다고 해서 개별 지원 주기가 끝난 제품의 지원 연장을 의미하지는 않습니다. [ESU(확장 보안 업데이트) ](https://support.microsoft.com/help/4497181/lifecycle-faq-extended-security-updates) 프로그램에서 적용되는 모든 제품을 포함하여 지원 주기가 끝난 제품은 Configuration Manager에서 사용할 수 없습니다. Microsoft 지원 주기에 대한 자세한 내용은 [Microsoft 지원 주기](https://go.microsoft.com/fwlink/p/?LinkId=208270) 웹 사이트를 참조하세요. Configuration Manager의 확장 보안 업데이트에 대한 자세한 내용은 [Configuration Manager의 클라이언트 및 장치에 대해 지원되는 OS 버전](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ESU)을 참조하세요.

> [!NOTE]  
>  Microsoft 지원 주기 정책에 대한 자세한 내용은 Microsoft 지원 주기 지원 정책 FAQ 웹 사이트([Microsoft 지원 주기 정책 FAQ](https://go.microsoft.com/fwlink/p/?LinkId=31976))를 참조하세요.  

 또한 다음 항목에 나열되지 않은 제품 및 제품 버전은 [Enterprise Mobility 및 보안 블로그](https://blogs.technet.microsoft.com/enterprisemobility/)에서 공지되지 않은 경우 Configuration Manager에서 지원되지 않습니다.  이 블로그의 내용이 이 설명서 본문에 대한 업데이트보다 앞서는 경우도 있습니다.


-  [크기 조정 및 규모 숫자 값](../../../core/plan-design/configs/size-and-scale-numbers.md)  
Configuration Manager에 대한 각 계층 구조 디자인에서 지원되는 사이트, 사이트당 사이트 시스템 역할 및 클라이언트 또는 디바이스 수를 알아봅니다.

-  [사이트 및 사이트 시스템 필수 조건](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)  
각 사이트 유형 및 사이트 시스템 역할을 지원하기 위해 Windows 서버에서 필요한 구성을 알아봅니다.

-  [사이트 시스템 서버에 대해 지원되는 운영 체제](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
사이트 서버 또는 사이트 시스템 서버로 사용할 수 있는 운영 체제를 알아봅니다.

-  [클라이언트 및 디바이스에 대해 지원되는 운영 체제](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)  
Windows, Windows Embedded, Linux 및 UNIX, Mac, 모바일 디바이스를 포함하여 Configuration Manager를 사용하여 관리할 수 있는 운영 체제를 알아봅니다.

-  [콘솔의 지원되는 운영 체제](../../../core/plan-design/configs/supported-operating-systems-consoles.md)  
배포 관리용 액세스 지점을 제공하기 위해 Configuration Manager 콘솔을 호스트할 수 있는 운영 체제를 알아봅니다.  

-  [SQL Server 버전 지원](../../../core/plan-design/configs/support-for-sql-server-versions.md)  
사이트 데이터베이스 및 보고 데이터베이스를 호스트할 수 있는 SQL Server 버전과 필수 구성 및 사용할 수 있는 선택적 구성을 알아봅니다.

-  [고가용성 옵션](../../../protect/understand/high-availability-options.md)  
Configuration Manager 배포에 대해 높은 수준의 사용 가능한 서비스를 유지할 수 있도록 사용자 환경을 디자인할 때 구현할 수 있는 옵션을 알아봅니다.

-  [권장 하드웨어](../../../core/plan-design/configs/recommended-hardware.md)  
Configuration Manager 사이트 및 주요 서비스를 호스트할 올바른 하드웨어와 구성을 식별하는 데 도움이 되는 지침을 알아봅니다.

-  [Active Directory 도메인 지원](../../../core/plan-design/configs/support-for-active-directory-domains.md)  
Configuration Manager에 필요하고 지원하는 Active Directory 도메인 구성을 알아봅니다.

-  [Windows 기능 및 네트워크 지원](../../../core/plan-design/configs/support-for-windows-features-and-networks.md)  
Configuration Manager에서 사용할 수 있도록 지원되는 Windows 기술(예: BranchCache 및 데이터 중복 제거) 및 제한 사항을 알아봅니다.

-  [가상화 환경 지원](../../../core/plan-design/configs/support-for-virtualization-environments.md)  
지원되는 가상 머신 기술을 사용하는 방법을 알아봅니다.
