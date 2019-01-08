---
title: 운영 체제 배포 상호 운용성 계획
titleSuffix: Configuration Manager
description: 단일 계층 구조의 다른 System Center Configuration Manager 사이트가 서로 다른 버전을 사용하는 경우 상호 운용성 문제를 고려해야 합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: aceb5f032cd0a4a5c12672db625b540465e37800
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53418478"
---
# <a name="planning-for-operating-system-deployment-interoperability-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 운영 체제 배포 상호 운용성 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

단일 계층 구조의 여러 System Center Configuration Manager 사이트가 서로 다른 버전을 사용하는 경우 일부 Configuration Manager 기능을 사용할 수 없습니다. 일반적으로 최신 버전의 Configuration Manager 기능은 더 낮은 버전을 실행하는 사이트 또는 클라이언트에서 액세스할 수 없습니다. 자세한 내용은 [서로 다른 버전의 System Center Configuration Manager 간 상호 운용성](../../core/plan-design/hierarchy/interoperability-between-different-versions.md)을 참조하세요.  

 계층의 최상위 사이트와 계층에서 이전 버전이 설치된 Configuration Manager를 실행하는 다른 사이트를 업그레이드할 경우 다음 사항을 고려하세요.  

- 클라이언트 설치 패키지  

  -   기본 클라이언트 설치 패키지의 원본이 자동으로 업그레이드되고 계층의 모든 배포 지점(계층에서 이전 버전이 설치된 사이트의 배포 지점도 포함)이 새 클라이언트 설치 패키지로 업데이트됩니다.  

  -   새 버전을 실행하는 클라이언트는 새 버전으로 아직 업그레이드되지 않은 사이트에 할당할 수 없습니다. 관리 지점에서 할당이 차단됩니다.  

- 부팅 이미지  

  -   최상위 사이트를 최신 버전의 Configuration Manager로 업그레이드하면 기본 부팅 이미지(x86 및 x64)가 Windows PE 10을 사용하는 Windows 10용 Windows ADK 기반 부팅 이미지로 자동 업데이트됩니다. 기본 부팅 이미지와 연결된 파일은 최신 Configuration Manager 버전 파일로 업데이트됩니다. 사용자 지정 부팅 이미지는 자동으로 업데이트되지 않습니다. 이전 Windows PE 버전이 포함된 사용자 지정 부팅 이미지를 수동으로 업데이트해야 합니다.  

  -   사이트 계층에 여러 가지 버전의 Configuration Manager가 있으면 동적 미디어를 사용하지 마세요. 대신 모든 사이트가 같은 버전의 Configuration Manager가 있는 사이트가 포함되어 있으면 동적 미디어를 사용하지 마세요.  

  -   최신 Configuration Manager 부팅 이미지에 원하는 사용자 지정이 포함되어 있는지 확인한 다음 최신 버전의 Configuration Manager 사이트의 모든 배포 지점을 새 부팅 이미지로 업데이트합니다.  

- USMT(사용자 상태 마이그레이션 도구)  

  -   최상위 사이트를 최신 버전의 Configuration Manager로 업그레이드하면 기본 USMT 패키지는 최신 버전으로 자동으로 업데이트됩니다. 사용자 지정 USMT 패키지는 자동으로 업데이트되지 않습니다. 이러한 패키지는 수동으로 업데이트해야 합니다.  

- 새 작업 순서 단계  

  -   새 작업 순서 단계가 정기적으로 새 버전의 Configuration Manager가 있는 사이트가 포함되어 있으면 동적 미디어를 사용하지 마세요. 새 단계가 있는 작업 순서를 이전 버전의 클라이언트로 배포하면 해당 작업 순서 단계가 실패합니다. 새 단계를 포함하는 작업 순서를 배포하기 전에 대상 컬렉션의 클라이언트가 새 버전으로 업데이트되었는지 확인합니다.  

- 운영 체제 배포 미디어  

  -   사이트가 새 버전으로 업데이트될 때 모든 미디어(부팅 가능, 캡처, 사전 준비 및 독립 실행형)를 새 Configuration Manager 클라이언트 패키지로 업데이트해야 합니다.  

- 운영 체제 배포에 대한 타사 확장  

  -   운영 체제 배포에 대한 타사 확장이 있고 다양한 버전의 Configuration Manager 사이트 또는 Configuration Manager 클라이언트가 있는 혼합 계층 구조를 사용하는 경우 확장에 문제가 있을 수 있습니다.  

  계층의 사이트를 업그레이드하는 동안 운영 체제 배포에 도움이 필요하면 다음 섹션을 참조하세요.  

## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>혼합 계층에 있는 최신 버전의 Configuration Manager 사이트  
 사이트를 최신 버전의 Configuration Manager로 업그레이드할 때 기본 클라이언트 설치 패키지를 참조하는 작업 순서가 자동으로 시작되어 최신 Configuration Manager 클라이언트 버전을 배포합니다. 사용자 지정 클라이언트 설치 패키지를 참조하는 작업 순서는 해당 사용자 지정 패키지에 포함된 클라이언트 버전을 계속 배포하므로(이전 Configuration Manager 클라이언트 버전과 마찬가지) 작업 순서 배포에 실패하지 않으려면 업데이트해야 합니다. 사용자 지정 클라이언트 설치 패키지를 사용하도록 구성된 작업 순서가 있으면 최신 Configuration Manager 버전의 클라이언트 설치 패키지를 사용하도록 작업 순서 단계를 업데이트하거나 최신 Configuration Manager 클라이언트 설치 원본을 사용하도록 사용자 지정 패키지를 업데이트해야 합니다.  

> [!IMPORTANT]  
>  최신 Configuration Manager 클라이언트 설치 패키지를 참조하는 작업 순서를 이전 Configuration Manager 사이트의 클라이언트에 배포하지 마세요. 이전 Configuration Manager 사이트에 할당된 클라이언트가 최신 Configuration Manager 클라이언트 버전으로 업그레이드되면 Configuration Manager는 이전 Configuration Manager 사이트에 대한 할당을 차단합니다. 그러므로 수동으로 클라이언트를 최신 Configuration Manager 사이트에 할당하거나 컴퓨터에서 이전 Configuration Manager 버전의 클라이언트를 다시 설치할 때까지 클라이언트가 더 이상 어느 사이트에도 할당되지 않으며 관리되지 않습니다.  

## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>혼합 계층에 있는 이전 버전의 Configuration Manager  
 중앙 관리 사이트를 최신 버전의 Configuration Manager로 업그레이드한 경우 다음 단계를 수행하여 이전 Configuration Manager 사이트(최신 버전의 Configuration Manager로 업그레이드하지 않은)에 할당된 클라이언트에 배포한 운영 체제 배포 작업 순서가 해당 클라이언트를 관리되지 않는 상태로 남겨 두지 않았는지 확인해야 합니다.  

-   Configuration Manager 사이트의 클라이언트에만 배포하는 데 사용할 작업 순서를 만듭니다. 마찬가지로, 최신 버전의 Configuration Manager 사이트에 있는 클라이언트에 배포하는 데 사용할 작업 순서의 사본을 만든 다음, 작업 순서를 수정하면 이전 Configuration Manager 사이트의 클라이언트에 배포하지 마세요. 그런 다음, 이전 Configuration Manager 클라이언트 설치 원본을 사용하도록 사용자 지정 패키지를 업데이트해야 합니다. 이전 Configuration Manager 클라이언트 설치 원본을 참조하는 사용자 지정 클라이언트 설치 패키지가 아직 없는 경우 수동으로 만들어야 합니다.  
