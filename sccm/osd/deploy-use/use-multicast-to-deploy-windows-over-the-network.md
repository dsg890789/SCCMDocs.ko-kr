---
title: 멀티캐스트를 사용하여 네트워크를 통해 Windows 배포
titleSuffix: Configuration Manager
description: 여러 컴퓨터에서 운영 체제 이미지를 동시에 다운로드할 수 있도록 System Center Configuration Manager 환경에서 멀티캐스트를 사용합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e47df52fd3b59c950f7005a7639abe57b2080bb
ms.sourcegitcommit: 2db6863c6740380478a4a8beb74f03b8178280ba
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083216"
---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 멀티캐스트를 사용하여 네트워크를 통해 Windows 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

멀티캐스트는 여러 클라이언트가 동시에 같은 운영 체제 이미지를 다운로드할 수도 있는 System Center Configuration Manager 환경에서 사용할 수 있는 네트워크 최적화 방법입니다. 멀티캐스트를 사용할 경우 여러 컴퓨터는 배포 지점에서 멀티캐스트되는 운영 체제 이미지를 동시에 다운로드하며 배포 지점은 개별 연결을 통해 데이터 복사본을 각 클라이언트에 전송하지 않습니다.  

 다음 운영 체제 배포 시나리오에서 멀티캐스트를 사용하여 네트워크를 통해 운영 체제를 배포할 수 있습니다.  

- [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

- [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

  운영 체제 배포 시나리오 중 하나의 단계를 완료한 후 다음 섹션을 참조하여 멀티미디어를 지원합니다.  

##  <a name="BKMK_Configure"></a> 멀티캐스트를 지원하기 위한 배포 지점 구성  
 운영 체제를 배포할 때 멀티캐스트를 사용하려면 멀티캐스트를 지원하도록 배포 지점을 구성해야 합니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-multicast)을 참조하세요. 멀티 캐스트를 지원하는 데 필요한 포트 목록은 [포트](/sccm/core/plan-design/hierarchy/ports#BKMK_PortsClient-DP2)를 참조하세요.  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>멀티캐스트 배포를 위한 운영 체제 이미지 준비  
 멀티캐스트를 지원하도록 운영 체제 이미지 패키지를 구성하려면 [멀티캐스트 배포를 위한 운영 체제 이미지 준비](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast)를 참조하세요.  

##  <a name="BKMK_Deploy"></a> 작업 순서 배포  
 대상 컬렉션에 운영 체제 배포 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/deploy-a-task-sequence)항목을 참조하세요.  
