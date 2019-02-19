---
title: 기존 컴퓨터 바꾸기 및 설정 전송
titleSuffix: Configuration Manager
description: Configuration Manager에서 부팅 가능한 미디어, 멀티캐스트 또는 소프트웨어 센터와 같은 배포 방법 중에서 선택하여 기존 컴퓨터를 새 컴퓨터로 바꿉니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: d28f4363-9e8a-4c54-9cb7-0594fabfff26
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 769794f98a14b5d8bf27b46c6fb2408d0b0ebe18
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56136112"
---
# <a name="replace-an-existing-computer-and-transfer-settings-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 기존 컴퓨터 바꾸기 및 설정 전송

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 System Center Configuration Manager에서 기존 컴퓨터를 새 컴퓨터로 바꾸기 위한 일반 단계를 제공합니다. 이 시나리오에서는 부팅 가능한 미디어, 멀티캐스트 또는 소프트웨어 센터와 같은 여러 다양한 배포 방법 중에서 선택할 수 있습니다. 또한 설정을 저장하기 위한 상태 마이그레이션 지점을 설치하도록 선택한 다음 설치 후에 새 운영 체제로 복원할 수 있습니다. 올바른 운영 체제 배포 시나리오인지 확실하지 않으면 [엔터프라이즈 운영 체제를 배포하는 시나리오](scenarios-to-deploy-enterprise-operating-systems.md)를 참조하세요.  

 다음 섹션을 사용하여 새 버전의 Windows로 기존 컴퓨터를 새로 고치세요.  

##  <a name="BKMK_Plan"></a> 계획  

-   **인프라 요구 사항 계획 및 구현**  

     Windows ADK, USMT(사용자 환경 마이그레이션 도구), WDS(Windows 배포 서비스), 지원되는 하드 디스크 구성 등 운영 체제를 배포하기 전에 준비해야 하는 몇 가지 인프라 요구 사항이 있습니다. 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](../plan-design/infrastructure-requirements-for-operating-system-deployment.md)을 참조하세요.  

-   **상태 마이그레이션 지점 설치(설정을 전송하는 경우에만 필요)**  

     기존 컴퓨터에서 설정을 캡처한 다음 설정을 새 운영 체제로 복원하려는 경우 상태 마이그레이션 지점을 설치해야 합니다. 자세한 내용은 [상태 마이그레이션 지점](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints)을 참조하세요.  

##  <a name="BKMK_Configure"></a> 구성  

1.  **부팅 이미지 준비**  

     부팅 이미지는 Windows PE 환경(제한된 구성 요소 및 서비스를 포함하는 최소 운영 체제)에서 컴퓨터를 시작합니다. 그런 후에 전체 Windows 운영 체제를 컴퓨터에 설치할 수 있습니다. 운영 체제를 배포할 때 사용할 부팅 이미지를 선택하고 이미지를 배포 지점에 배포해야 합니다. 다음에 따라 부팅 이미지를 준비합니다.  

    -   부팅 이미지에 대한 자세한 내용은 [부팅 이미지 관리](../get-started/manage-boot-images.md)를 참조하세요.  

    -   부팅 이미지를 사용자 지정하는 방법에 대한 자세한 내용은 [부팅 이미지 사용자 지정](../get-started/customize-boot-images.md)을 참조하세요.  

    -   배포 지점에 부팅 이미지를 배포합니다. 자세한 내용은 [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute)을 참조하십시오.  

2.  **운영 체제 이미지 준비**  

     운영 체제 이미지에는 대상 컴퓨터에 운영 체제를 설치하는 데 필요한 파일이 포함되어 있습니다. 다음에 따라 운영 체제 이미지를 준비합니다.  

    -   운영 체제 이미지를 만드는 방법에 대한 자세한 내용은 [운영 체제 이미지 관리](../get-started/manage-operating-system-images.md)를 참조하세요.  

    -   배포 지점에 운영 체제 이미지 배포 자세한 내용은 [콘텐츠 배포](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute)를 참조하세요.  

3.  **네트워크를 통해 운영 체제를 배포하는 작업 순서 만들기**  

     작업 순서를 사용하여 네트워크를 통한 운영 체제 설치를 자동화할 수 있습니다. [운영 체제를 설치하는 작업 순서 만들기](create-a-task-sequence-to-install-an-operating-system.md)의 단계를 수행하여 운영 체제를 배포하는 작업 순서를 만듭니다. 선택한 배포 방법에 따라 작업 순서에 대한 추가적으로 고려해야 할 사항이 있을 수 있습니다.  

    > [!NOTE]  
    >  이 시나리오에서 사용자 설정 및 파일을 캡처 및 복원하는 경우 상태 마이그레이션 지점을 사용하거나 파일을 로컬로 저장하도록 선택할 수 있습니다. 자세한 내용은 [사용자 상태 관리](../get-started/manage-user-state.md)를 참조하세요.  

##  <a name="BKMK_Deploy"></a> 배포  

-   다음 배포 방법 중 하나를 사용하여 운영 체제를 배포합니다.  

    -   [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [팩터리 또는 로컬 저장소에 OEM에 대한 이미지 만들기](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

## <a name="monitor"></a>모니터  

-   **작업 순서 배포 모니터링**  

     운영 체제를 설치하는 작업 순서 배포를 모니터링하려면 [운영 체제 배포 모니터링](monitor-operating-system-deployments.md)을 참조하세요.  
