---
title: "새 버전의 Windows로 기존 컴퓨터 새로 고침"
titleSuffix: Configuration Manager
description: "Configuration Manager에서 몇 가지 방법을 사용하여 기존 컴퓨터에 파티션을 만들고 포맷(초기화)하고 컴퓨터에 새 운영 체제를 설치할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b189a346-8c0d-4870-a876-0719fbb0ab04
caps.latest.revision: "7"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: a7a3f61793e92453b8ccc048192d3ae858a78a4a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="refresh-an-existing-computer-with-a-new-version-of-windows-using-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 새 버전의 Windows로 기존 컴퓨터 새로 고침

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 기존 컴퓨터에 파티션을 만들고 포맷(초기화)하고 컴퓨터에 새 운영 체제를 설치하기 위한 System Center Configuration Manager의 일반 단계를 제공합니다. 이 시나리오에서는 PXE, 부팅 가능한 미디어 또는 소프트웨어 센터와 같은 여러 다양한 배포 방법 중에서 선택할 수 있습니다. 또한 설정을 저장하기 위한 상태 마이그레이션 지점을 설치하도록 선택한 다음 설치 후에 새 운영 체제로 복원할 수 있습니다. 올바른 운영 체제 배포 시나리오인지 확실하지 않으면 [엔터프라이즈 운영 체제를 배포하는 시나리오](scenarios-to-deploy-enterprise-operating-systems.md)를 참조하세요.  

 다음 섹션을 사용하여 새 버전의 Windows로 기존 컴퓨터를 새로 고치세요.  

##  <a name="BKMK_Plan"></a> 계획  

-   **인프라 요구 사항 계획 및 구현**  

     Windows ADK, USMT(사용자 환경 마이그레이션 도구), WDS(Windows 배포 서비스), 지원되는 하드 디스크 구성 등 운영 체제를 배포하기 전에 준비해야 하는 몇 가지 인프라 요구 사항이 있습니다. 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](../plan-design/infrastructure-requirements-for-operating-system-deployment.md)을 참조하세요.  

-   **상태 마이그레이션 지점 설치(설정을 전송하는 경우에만 필요)**  

     기존 컴퓨터에서 설정을 캡처한 다음 설정을 새 운영 체제로 복원하려는 경우 상태 마이그레이션 지점을 설치해야 합니다. 자세한 내용은 [상태 마이그레이션 지점](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints)을 참조하세요.  

##  <a name="BKMK_Configure"></a> 구성  

1.  **부팅 이미지 준비**  

     부팅 이미지는 Windows PE 환경(제한된 구성 요소 및 서비스를 포함하는 최소 운영 체제)에서 컴퓨터를 시작합니다. 그런 후에 전체 Windows 운영 체제를 컴퓨터에 설치할 수 있습니다.   운영 체제를 배포할 때 사용할 부팅 이미지를 선택하고 이미지를 배포 지점에 배포해야 합니다. 다음에 따라 부팅 이미지를 준비합니다.  

    -   부팅 이미지에 대한 자세한 내용은 [부팅 이미지 관리](../get-started/manage-boot-images.md)를 참조하세요.  

    -   부팅 이미지를 사용자 지정하는 방법에 대한 자세한 내용은 [부팅 이미지 사용자 지정](../get-started/customize-boot-images.md)을 참조하세요.  

    -   배포 지점에 부팅 이미지를 배포합니다. 자세한 내용은 [콘텐츠 배포](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute)를 참조하세요.  

2.  **운영 체제 이미지 준비**  

     운영 체제 이미지에는 대상 컴퓨터에 운영 체제를 설치하는 데 필요한 파일이 포함되어 있습니다. 다음에 따라 운영 체제 이미지를 준비합니다.  

    -   운영 체제 이미지를 만드는 방법에 대한 자세한 내용은 [운영 체제 이미지 관리](../get-started/manage-operating-system-images.md)를 참조하세요.  

    -   배포 지점에 운영 체제 이미지 배포 자세한 내용은 [콘텐츠 배포](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute)를 참조하세요.  

3.  **네트워크를 통해 운영 체제를 배포하는 작업 순서 만들기**  

     작업 순서를 사용하여 네트워크를 통한 운영 체제 설치를 자동화할 수 있습니다. [운영 체제를 설치하는 작업 순서 만들기](create-a-task-sequence-to-install-an-operating-system.md)의 단계를 수행하여 운영 체제를 배포하는 작업 순서를 만듭니다. 선택한 배포 방법에 따라 작업 순서에 대한 추가적으로 고려해야 할 사항이 있을 수 있습니다.  

    > [!NOTE]  
    >  이 시나리오에서 작업 순서는 컴퓨터의 하드 디스크를 포맷하고 파티션을 만듭니다. 사용자 설정을 캡처하려면 상태 마이그레이션 지점을 사용하고 작업 순서 만들기 마법사의 **상태 마이그레이션** 페이지에서 **상태 마이그레이션 지점에 사용자 설정 및 파일 저장** 을 선택해야 합니다. 사용자 설정 및 파일을 로컬로 저장하면 하드 디스크를 포맷할 때 손실되며 Configuration Manager에서 설정을 복원할 수 없게 됩니다. 자세한 내용은 [사용자 상태 관리](../get-started/manage-user-state.md)를 참조하세요.  

##  <a name="BKMK_Deploy"></a> 배포  

-   다음 배포 방법 중 하나를 사용하여 운영 체제를 배포합니다.  

    -   [PXE를 사용하여 네트워크를 통해 Windows 배포](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [팩터리 또는 로컬 저장소에 OEM에 대한 이미지 만들기](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](use-software-center-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>모니터  

-   **작업 순서 배포 모니터링**  

     운영 체제를 설치하는 작업 순서 배포를 모니터링하려면 [운영 체제 배포 모니터링](monitor-operating-system-deployments.md)을 참조하세요.  
