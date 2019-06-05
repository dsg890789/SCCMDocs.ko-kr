---
title: OS 배포 상호 운용성
titleSuffix: Configuration Manager
description: 단일 계층 구조의 다른 System Center Configuration Manager 사이트가 서로 다른 버전을 사용하는 경우 상호 운용성 문제를 고려해야 합니다.
ms.date: 05/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d4f6275ede2a751acb8ca14d7b8b6ad307e78bd
ms.sourcegitcommit: 18a94eb78043cb565b05cd0e9469b939b29cccf0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355008"
---
# <a name="plan-for-os-deployment-interoperability"></a>OS 배포 상호 운용성 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

단일 계층 구조의 여러 System Center Configuration Manager 사이트가 서로 다른 버전을 사용하는 경우 일부 Configuration Manager 기능을 사용할 수 없습니다. 일반적으로 최신 버전의 Configuration Manager 기능은 더 낮은 버전을 실행하는 사이트 또는 클라이언트에서 액세스할 수 없습니다. 자세한 내용은 [서로 다른 버전의 System Center Configuration Manager 간 상호 운용성](/sccm/core/plan-design/hierarchy/interoperability-between-different-versions)을 참조하세요.  


## <a name="objects"></a>개체

계층의 최상위 사이트와 계층에서 이전 버전이 설치된 Configuration Manager를 실행하는 다른 사이트를 업그레이드할 경우 다음 개체를 고려하세요.  

### <a name="client-installation-package"></a>클라이언트 설치 패키지  

- 기본 클라이언트 설치 패키지의 원본이 자동으로 업그레이드됩니다. 계층 구조의 모든 배포 지점은 새 클라이언트 설치 패키지로 업데이트됩니다. 이 동작은 하위 버전에 있는 계층 구조에 사이트의 배포지점에서도 발생합니다.  

- 아직 새 버전으로 업그레이드하지 않은 사이트에는 새 버전 클라이언트를 할당할 수 없습니다. 관리 지점에서 할당이 차단됩니다.  

### <a name="boot-images"></a>부팅 이미지  

- 최상위 사이트를 최신 버전의 Configuration Manager로 업그레이드하면 기본 부트 이미지(x86 및 x64)가 자동으로 업데이트됩니다. 이 업데이트는 Windows PE 10이 포함된 Windows 10용 Windows ADK를 사용합니다. 기본 부팅 이미지와 연결된 파일은 최신 Configuration Manager 버전 파일로 업데이트됩니다. 사이트에서 사용자 지정 부팅 이미지를 자동으로 업데이트하지 않습니다. 이전 Windows PE 버전이 포함된 사용자 지정 부팅 이미지를 수동으로 업데이트해야 합니다.  

- 사이트 계층에 다른 버전의 Configuration Manager가 있는 사이트가 포함되어 있으면 동적 미디어를 사용하지 마세요. 대신 사이트 기반 미디어를 사용하여 특정 관리 지점에 문의하세요. 모든 사이트를 동일한 버전의 Configuration Manager로 업데이트한 후 동적 미디어를 다시 사용할 수 있습니다.

- 최신 Configuration Manager 부팅 이미지에 사용자 지정이 포함되어 있는지 확인합니다. 그런 다음, 새 버전 사이트의 모든 배포 지점을 새 부팅 이미지의 최신 버전으로 업데이트합니다.  

### <a name="user-state-migration-tool-usmt"></a>USMT(사용자 상태 마이그레이션 도구)  

최상위 사이트를 최신 버전의 Configuration Manager로 업그레이드하면 기본 USMT 패키지가 최신 버전으로 자동 업데이트됩니다. 모든 사용자 지정 USMT 패키지는 자동으로 업데이트되지 않습니다. 이러한 패키지는 수동으로 업데이트해야 합니다.  

### <a name="new-task-sequence-steps"></a>새 작업 순서 단계  

새 작업 순서 단계가 정기적으로 새 버전의 Configuration Manager가 있는 사이트가 포함되어 있으면 동적 미디어를 사용하지 마세요. 새 단계가 있는 작업 순서를 이전 클라이언트로 배포하면 해당 작업 순서 단계가 실패합니다. 새 단계를 포함하는 작업 순서를 배포하기 전에 대상 컬렉션의 클라이언트가 새 버전으로 업데이트되었는지 확인합니다.  

### <a name="os-deployment-media"></a>OS 배포 미디어  

사이트가 새 버전으로 업데이트되면 새 Configuration Manager 클라이언트 패키지로 모든 미디어를 업데이트합니다. 이러한 미디어 유형에는 부팅 가능, 캡처, 사전 준비 및 독립 실행형이 포함됩니다.

### <a name="third-party-extensions-to-os-deployment"></a>OS 배포에 대한 타사 확장  

OS 배포에 대한 타사 확장이 있고 다양한 버전의 Configuration Manager 사이트 또는 Configuration Manager 클라이언트가 있는 경우 확장에 문제가 있을 수 있습니다.  


## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>혼합 계층에 있는 최신 버전의 Configuration Manager 사이트  

사이트를 최신 버전의 Configuration Manager로 업그레이드할 때 기본 클라이언트 설치 패키지를 참조하는 작업 순서가 자동으로 시작되어 최신 Configuration Manager 클라이언트 버전을 배포합니다.

사용자 지정 클라이언트 설치 패키지를 참조하는 작업 순서는 해당 사용자 지정 패키지에 포함된 클라이언트 버전을 계속 배포합니다. 사용자 지정 패키지에는 이전 버전의 Configuration Manager 클라이언트가 포함될 수 있습니다. 작업 순서 배포 실패를 방지하려면 모든 사용자 지정 클라이언트 설치 패키지를 최신 버전으로 업데이트합니다.

사용자 지정 클라이언트 설치 패키지를 사용하도록 작업 순서를 구성하는 경우 다음 작업 중 하나를 수행합니다.

- 클라이언트 설치 패키지의 최신 Configuration Manager 버전을 사용하도록 작업 순서 단계를 업데이트합니다.
- 최신 Configuration Manager 클라이언트 설치 원본을 사용하도록 사용자 지정 패키지를 업데이트합니다.

> [!IMPORTANT]  
> 최신 Configuration Manager 클라이언트 설치 패키지를 참조하는 작업 순서를 이전 Configuration Manager 사이트의 클라이언트에 배포하지 마세요. 이전 Configuration Manager 사이트에 할당된 클라이언트가 최신 Configuration Manager 클라이언트 버전으로 업그레이드되면 Configuration Manager는 이전 Configuration Manager 사이트에 대한 할당을 차단합니다. 이러한 클라이언트는 더 이상 어느 사이트에도 할당되지 않습니다. 클라이언트를 최신 Configuration Manager 사이트에 수동으로 할당하거나 이전 Configuration Manager 버전의 클라이언트를 컴퓨터에 다시 설치할 때까지 이러한 클라이언트는 관리되지 않습니다.


## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>혼합 계층에 있는 이전 버전의 Configuration Manager  

중앙 관리 사이트를 최신 버전의 Configuration Manager로 업그레이드할 때 배포하는 OS 배포 작업 순서가 해당 클라이언트를 관리되지 않은 상태로 두지 않도록 합니다. 예를 들어 아직 최신 버전의 Configuration Manager로 업그레이드하지 않은 이전 Configuration Manager 사이트에 할당된 클라이언트에 배포하는 경우

최신 버전의 Configuration Manager 사이트에서 클라이언트에 배포하는 데 사용하는 작업 순서의 복사본을 만듭니다. 그런 다음, 이전 Configuration Manager 사이트의 클라이언트에 배포할 수 있도록 작업 순서를 수정합니다. 이전 Configuration Manager 클라이언트 설치 원본을 사용하도록 사용자 지정 패키지를 업데이트해야 합니다. 이전 Configuration Manager 클라이언트 설치 원본을 참조하는 사용자 지정 클라이언트 설치 패키지가 없는 경우 수동으로 만듭니다.  

> [!Important]  
> 버전 1902부터는 패키지 또는 작업 순서를 클라이언트 5.7730 이하에 배포할 수 없습니다. 이 제한을 해결하려면 클라이언트를 최신 버전으로 업그레이드합니다.<!-- SCCMDocs-pr issue #3493 -->
