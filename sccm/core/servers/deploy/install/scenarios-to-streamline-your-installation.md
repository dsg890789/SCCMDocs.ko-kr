---
title: "설치 시나리오"
titleSuffix: Configuration Manager
description: "사이트를 업데이트하거나 업그레이드하는 경우 새 Configuration Manager 계층 구조를 설치하는 기술에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35586a85-4af9-4c8b-925a-0e32dc8b7346
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9e7cdd08ba7850f4cb3558c7474c0583e4411b98
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="scenarios-to-streamline-your-installation-of-system-center-configuration-manager"></a>System Center Configuration Manager의 설치를 간소화하는 시나리오

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 현재 분기에 대한 업데이트 버전 릴리스의 경우 업데이트 버전(예: 업데이트 1610)으로 새 계층 구조 설치를 간소화하고 Microsoft System Center 2012 Configuration Manager에서 업그레이드하는 새 시나리오가 있습니다.

지원되는 시나리오:  

업데이트 버전을 실행하는 **새로운 System Center Configuration Manager 현재 분기 계층 구조를 설치**합니다.  

-   최상위 계층 사이트만 설치한 다음 즉시 업데이트를 설치하여 사용할 업데이트 버전으로 해당 사이트를 최신 상태로 만듭니다. 그런 후 해당 업데이트 버전에 직접 추가 사이트를 설치할 수 있습니다.  
-   이 시나리오에서는 기준선 수준에 추가 사이트를 설치한 후 사용할 업데이트 버전으로 업데이트하는 프로세스를 건너뜁니다.  
-   이 시나리오에서는 기준 버전에 클라이언트를 설치한 후 이후 버전으로 업데이트할 때 다시 설치하는 프로세스를 건너뜁니다.  

System Center Configuration Manager의 업데이트 버전으로 **Microsoft System Center 2012 Configuration Manager 인프라를 업그레이드**합니다.  

-   업데이트 버전(예: 1610)을 설치하기 전에 기준 버전(예: 1606)으로 중앙 관리 사이트 및 각 기본 사이트를 수동으로 업그레이드합니다.  
-   기본 사이트에서 사용하려는 업데이트 버전을 실행할 때까지 Microsoft System Center 2012 Configuration Manager에서 보조 사이트를 업그레이드하지 마세요.  
-   기본 사이트에서 사용하려는 업데이트 버전을 실행할 때까지 Microsoft System Center 2012 Configuration Manager에서 클라이언트를 업그레이드하지 마세요.  

## <a name="scenario-install-a-new-hierarchy-to-an-update-version"></a>시나리오: 업데이트 버전에 새 계층 구조 설치  
이 예제 시나리오에서는 System Center Configuration Manager의 기준 버전인 버전 1610을 사용하여 계층 구조의 첫 번째 사이트를 설치합니다. 그런 다음 추가 사이트 또는 클라이언트를 배포하기 전에 1610 업데이트를 설치합니다.  

-   업데이트 버전(예: 버전 1610)을 사용할 계획이고 기준 버전(예: 버전 1606)에 있지 않기 때문에 추가 사이트를 설치한 후 업그레이드할 필요는 없습니다. 이는 클라이언트에도 적용됩니다.  
-   버전 1606을 사용하여 보조 사이트를 설치한 후 버전 1610으로 업그레이드하지 마세요. 대신, 기본 사이트에서 버전 1610을 실행한 후 보조 사이트를 설치합니다.  

다음 순서를 따르세요.  

1.  기준 미디어를 사용하여 **새 계층 구조의 최상위 사이트를 설치**합니다.  

    -   기준 미디어만 사용하여 새 계층 구조의 첫 번째 사이트를 설치할 수 있습니다.  
    -   예를 들어 기준 버전 1606을 사용하여 최상위 사이트를 설치합니다. 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites)를 참조하세요.  

    이 단계를 수행하면 최상위 사이트는 버전 1606을 실행합니다.  

2.  **콘솔 내 업데이트를 사용하여 이후 버전으로 최상위 사이트를 업데이트합니다.**  

    -   자식 사이트 또는 클라이언트를 설치하기 전에 사용할 업데이트 버전으로 최상위 사이트를 업데이트합니다.  
    -   예를 들어 버전 1606을 실행하는 최상위 사이트를 버전 1610으로 업데이트할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 업데이트](../../../../core/servers/manage/updates.md)를 참조하세요.  

    이 단계를 수행하면 최상위 사이트는 버전 1610을 실행합니다.  

3.  **중앙 관리 사이트 아래에 새 자식 기본 사이트를 설치합니다.**  

    -   중앙 관리 사이트 서버에 있는 CD.Latest 폴더에서 설치 미디어를 사용하여 자식 기본 사이트를 설치합니다. 자세한 내용은 [System Center Configuration Manager의 CD.Latest 폴더](../../../../core/servers/manage/the-cd.latest-folder.md)를 참조하세요.  

      이 원본 미디어는 새 자식 기본 사이트가 중앙 관리 사이트의 버전과 일치하는지 확인하는 데 필요합니다.  

    이 단계를 수행한 후 새 자식 기본 사이트에서는 버전 1610을 실행합니다.  

4.  **각 기본 사이트에서, 콘솔 내 옵션을 사용하여 새 보조 사이트를 설치합니다.**  

    -   기본 사이트가 버전 1606에 있는 동안 보조 사이트를 설치하지 않았기 때문에 보조 사이트를 업그레이드할 필요가 없습니다.  
    -   대신, 버전 1610을 실행하는 새 보조 사이트를 설치합니다. 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites) 항목에서 [보조 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary)를 참조하세요.  

    이 단계를 수행하면 새 보조 사이트가 설치되고 버전 1610을 실행합니다.  

5.  **기본 사이트에 새 클라이언트를 설치합니다.**  

    -   기본 사이트가 버전 1606에 있는 동안 클라이언트를 설치하지 않았기 때문에 버전 1606에서 버전 1610로 클라이언트를 업그레이드할 필요가 없습니다.  
    -   대신, 버전 1610을 실행하는 새 클라이언트를 설치합니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 배포](../../../clients/deploy/deploy-clients-to-windows-computers.md)를 참조하세요.  

    이 단계를 수행하면 버전 1610을 실행하는 새 클라이언트가 설치됩니다.  

## <a name="scenario-upgrade-system-center-2012-configuration-manager-to-an-update-version-of-system-center-configuration-manager-current-branch"></a>시나리오: System Center Configuration Manager 현재 분기의 업데이트 버전으로 System Center 2012 Configuration Manager 업그레이드  
이 예제 시나리오에서는 System Center Configuration Manager의 업데이트 버전(예: 버전 1610)으로 Microsoft System Center 2012 Configuration Manager 인프라를 업그레이드합니다.  

-   버전 1610에 대한 업데이트를 설치하기 전에 중앙 관리 사이트 및 각 기본 사이트를 기준 버전인 1606으로 업그레이드해야 합니다.  
-   보조 사이트와 클라이언트에서는 버전 1606을 업그레이드하거나 설치하지 않습니다. 대신, Microsoft System Center 2012 Configuration Manager에서 System Center Configuration Manager 버전 1610으로 직접 이동합니다.  

다음 순서를 따르세요.  

1.  System Center Configuration Manager에 대한 원본 미디어(예: 버전 1606)를 사용하여 현재 분기의 기준 버전으로 **최상위 Microsoft System Center 2012 Configuration Manager 사이트를 업그레이드**합니다. 자세한 내용은 [System Center Configuration Manager 업그레이드](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md)를 참조하세요.  

    -   기존의 업그레이드 시나리오와 같이 항상 계층의 최상위 사이트를 먼저 업그레이드한 후 하위 사이트를 업그레이드합니다.  

    이 단계를 수행하면 최상위 사이트는 버전 1606을 실행합니다.  

2.  **계층의 각 자식 기본 사이트를 동일한 기준선 버전으로 업그레이드** 합니다.  

    -   Microsoft System Center 2012 Configuration Manager에서 업그레이드하는 경우 현재 분기의 기준선 버전으로 각 기본 사이트를 수동으로 업그레이드해야 합니다.  
    -   지금은 보조 사이트를 업그레이드하지 않습니다.  

    이 단계를 수행하면 기본 사이트에서 버전 1606을 실행합니다.  

3.  **자식 기본 사이트에서 유지 관리 기간을 설정합니다.** 모든 기본 사이트를 기준 버전으로 업그레이드한 후 해당 사이트가 인프라 업데이트를 설치하는 경우를 제어하도록 유지 관리 기간을 구성합니다. 자세한 내용은 [System Center Configuration Manager에서 유지 관리 기간을 사용하는 방법](../../../../core/clients/manage/collections/use-maintenance-windows.md)을 참조하세요.  유지 관리 기간을 버전 1606에서는 *서비스 기간*이라고 합니다.  

    -   자식 기본 사이트에서는 중앙 관리 사이트에 설치하는 것과 동일한 업데이트를 자동으로 설치합니다.  
    -   보조 사이트에는 새 버전이 자동으로 설치되지 않습니다. 콘솔 내에서 수동으로 업그레이드해야 합니다.  

  이 단계를 수행하면 중앙 관리 사이트에서 업데이트를 설치할 경우 자식 기본 사이트에서는 유지 관리 기간에서 허용할 때 해당 업데이트만 설치합니다.  

4.  **최상위 사이트에서 업데이트 버전을 설치합니다.** 최상위 사이트가 업데이트됩니다. 중앙 관리 사이트에서 업데이트 버전을 설치한 후 설치가 유지 관리 기간으로 차단되지 않는 한 각 자식 기본 사이트에서 자동으로 업데이트를 설치합니다.  

    -   예를 들어 버전 1606에서 버전 1610으로 최상위 사이트를 업데이트할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 업데이트](../../../../core/servers/manage/updates.md)를 참조하세요.  

    이 단계를 수행하면 중앙 관리 사이트와 각 기본 사이트에서 버전 1610을 실행합니다.  

5.  **보조 사이트를 업그레이드합니다.** 기본 사이트에서 업데이트를 설치하고 버전 1610을 실행한 후 콘솔 내 옵션을 사용하여 보조 사이트를 업그레이드합니다.  

    -   그러면 Microsoft System Center 2012 Configuration Manager에서 기본 사이트에 설치된 업데이트 버전으로 직접 보조 사이트가 업그레이드됩니다.  
    -   보조 사이트를 업그레이드하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 업그레이드](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md) 항목의 [사이트 업그레이드](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_upgrade)를 참조하세요.  

6.  **클라이언트를 업그레이드합니다.** 클라이언트를 업그레이드하려면 [System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트를 업그레이드하는 방법](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md)의 정보를 참조하세요.  

    -   그러면 Microsoft System Center 2012 Configuration Manager에서 기본 사이트에 설치된 업데이트 버전으로 직접 클라이언트가 업그레이드됩니다.  

    이 단계를 수행하면 먼저 버전 1606으로 업그레이드하지 않고도 클라이언트가 버전 1610으로 업그레이드됩니다.
