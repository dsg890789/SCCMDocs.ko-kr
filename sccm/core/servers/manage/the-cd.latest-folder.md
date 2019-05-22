---
title: CD.Latest 폴더
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔 내에서 제품 업데이트를 제공하는 프로세스에 대해 알아봅니다.
ms.date: 03/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4f69d686a48af3c6e710c6aff592d71de1dbff1
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65496998"
---
# <a name="the-cdlatest-folder-for-configuration-manager"></a>Configuration Manager의 CD.Latest 폴더

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에는 Configuration Manager 콘솔 내에서 제품 업데이트를 제공하는 프로세스가 있습니다. Configuration Manager를 업데이트하는 이 새로운 방법을 지원하기 위해 **CD.Latest**라는 새 폴더가 만들어집니다. 이 폴더에는 업데이트된 버전의 사이트에 대한 Configuration Manager 설치 파일의 복사본이 포함되어 있습니다.  

CD.Latest 폴더에는 **Redist**라는 폴더가 포함되어 있습니다. Redist 폴더에는 설치 프로그램에서 다운로드하고 사용하는 재배포 가능한 파일이 포함되어 있습니다. 이러한 파일은 해당 CD.Latest 폴더에 있는 Configuration Manager 파일의 버전에 대응됩니다. CD.Latest 폴더에서 설치 프로그램을 실행할 때 설치 프로그램의 버전에 대응되는 파일을 사용해야 합니다. Microsoft에서 새 파일 및 최신 파일을 다운로드하거나, CD.Latest 폴더에 있는 Redist 폴더에서 파일을 사용하도록 설치 프로그램에 지시할 수 있습니다.

기준 미디어에는 **Redist** 폴더가 포함되어 있지 않습니다. 사이트는 콘솔 내 업데이트를 설치할 때까지 Redist 폴더를 만들지 않습니다. 그 동안에는 기준 미디어에서 사이트를 설치할 때 사용한 Redist 폴더를 사용합니다.  

> [!TIP]  
> 사용하는 재배포 가능한 파일이 최신 파일인지 확인하세요. 재배포 가능한 파일을 최근에 다운로드하지 않은 경우 설치 프로그램을 통해 Microsoft에서 다운로드하도록 계획하세요.   

중앙 관리 사이트 또는 기본 사이트 서버에 CD.Latest 폴더를 만들거나 업데이트하는 시나리오는 다음과 같습니다.  

- Configuration Manager 콘솔 내에서 업데이트 또는 핫픽스를 설치하면 사이트가 Configuration Manager 설치 폴더에서 폴더를 생성하거나 업데이트합니다.  

- 기본 제공 Configuration Manager 백업 작업을 실행하면 사이트가 지정된 백업 폴더 위치에서 폴더를 생성하거나 업데이트합니다.  

- 기준 미디어를 사용하여 새 사이트를 설치할 경우 사이트에서 CD.Latest 폴더가 만들어집니다.


## <a name="supported-scenarios"></a>지원되는 시나리오

CD.Latest 폴더의 소스 파일은 다음 시나리오에서 지원됩니다.  

### <a name="backup-and-recovery"></a>백업 및 복구
사이트를 복구하려면 사용 중인 사이트와 일치하는 CD.Latest 폴더의 소스 파일을 사용합니다. 기본 제공 사이트 백업 작업을 사용하여 사이트 백업을 실행할 경우 CD.Latest 폴더는 백업의 일부로 포함됩니다.

- 사이트 복구 과정에서 사이트를 다시 설치하는 경우 백업에 포함된 CD.Latest 폴더에서 사이트를 설치합니다. 이 작업을 수행하면 사이트 백업 및 사이트 데이터베이스와 일치하는 파일 버전을 사용하여 사이트가 설치됩니다.  

    - 올바른 CD.Latest 폴더 버전에 액세스할 수 없으면 랩 환경에 사이트를 설치하여 올바른 파일 버전의 CD.Latest 폴더를 가져옵니다. 그런 다음, 해당 사이트를 복구할 버전과 일치하도록 업데이트합니다.  

    - 올바른 CD.Latest 폴더와 폴더 내용을 사용할 수 없는 경우에는 사이트를 복구할 수 없습니다. 이 경우에는 사이트를 다시 설치해야 합니다.  

- CD.Latest 폴더가 없지만 작동하는 자식 기본 사이트 또는 중앙 관리 사이트는 있는 경우 사이트 복구에 대한 참조 사이트로 해당 사이트를 사용할 수 있습니다.  

### <a name="install-a-child-primary-site"></a>자식 기본 사이트 설치
콘솔 내 업데이트를 하나 이상 설치한 중앙 관리 사이트 아래에 새 자식 기본 사이트를 설치하려는 경우 중앙 관리 사이트의 CD.Latest 폴더에 있는 설치 프로그램과 소스 파일을 사용합니다. 이 프로세스는 중앙 관리 사이트의 버전과 일치하는 설치 소스 파일을 사용합니다. 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites)를 참조하세요.  

### <a name="expand-a-stand-alone-primary-site"></a>독립 실행형 기본 사이트 확장
새 중앙 관리 사이트를 설치하여 독립 실행형 기본 사이트를 확장하는 경우 기본 사이트의 CD.Latest 폴더에서 설치 프로그램 및 소스 파일을 사용합니다. 이 프로세스는 기본 사이트의 버전과 일치하는 설치 소스 파일을 사용합니다. 자세한 내용은 [독립 실행형 기본 사이트 확장](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_expand)을 참조하세요.

### <a name="install-a-secondary-site"></a>보조 사이트 설치
<!-- SCCMDocs-pr issue #3164 -->
콘솔 내 업데이트를 하나 이상 설치한 기본 사이트 아래에 새 보조 사이트를 설치하려는 경우 기본 사이트의 CD.Latest 폴더에 있는 소스 파일을 사용합니다. 

자세한 내용은 [보조 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary)를 참조하세요. 


## <a name="unsupported-scenarios"></a>지원되지 않는 시나리오

업데이트된 CD.Latest 소스 파일은 다음에 대해 지원되지 않습니다.  
   
- 새 계층을 위한 새 사이트 설치  
- Microsoft System Center 2012 Configuration Manager 사이트를 System Center Configuration Manager 현재 분기로 업그레이드
- Configuration Manager 클라이언트 설치
- Configuration Manager 콘솔 설치

