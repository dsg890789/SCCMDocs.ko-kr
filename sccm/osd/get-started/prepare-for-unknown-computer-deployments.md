---
title: 알 수 없는 컴퓨터 배포 준비
titleSuffix: Configuration Manager
description: System Center Configuration Manager 환경에서 Configuration Manager가 관리하지 않는 컴퓨터에 운영 체제를 배포하는 방법을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 9e447e34-0943-49ed-b6ba-3efebf3566c1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c64ae61e2ff31a14b6c4b094eafa5feac197e21
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56132594"
---
# <a name="prepare-for-unknown-computer-deployments-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 알 수 없는 컴퓨터 배포 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 정보를 통해 System Center Configuration Manager 환경에서 알 수 없는 컴퓨터에 운영 체제를 배포합니다. 알 수 없는 컴퓨터는 Configuration Manager에서 관리되지 않는 컴퓨터입니다. 따라서 Configuration Manager 데이터베이스에 이러한 컴퓨터의 레코드가 없습니다. 알 수 없는 컴퓨터는 다음과 같습니다.  

- Configuration Manager 클라이언트가 설치되지 않은 컴퓨터  

- Configuration Manager로 가져오지 않은 컴퓨터  

- Configuration Manager에서 검색되지 않은 컴퓨터  

  다음과 같은 배포 방법을 사용하여 알 수 없는 컴퓨터에 운영 체제를 배포할 수 있습니다.  

- [PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)  

- [부팅 가능한 미디어를 사용하여 운영 체제 배포](../deploy-use/create-bootable-media.md)  

- [사전 준비된 미디어를 사용하여 운영 체제 배포](../deploy-use/create-prestaged-media.md)  

## <a name="unknown-computer-deployment-workflow"></a>알 수 없는 컴퓨터 배포 워크플로  
 다음은 알 수 없는 컴퓨터에 운영 체제를 배포하기 위한 기본 워크플로입니다.  

-   배포에서 사용할 알 수 없는 컴퓨터 개체를 선택합니다. **모든 알 수 없는 컴퓨터** 컬렉션의 알 수 없는 컴퓨터 개체 중 하나에 운영 체제를 배포하거나 **모든 알 수 없는 컴퓨터** 컬렉션의 개체를 다른 컬렉션에 추가할 수 있습니다. Configuration Manager는 **모든 알 수 없는 컴퓨터** 컬렉션에서 두 개의 알 수 없는 컴퓨터 개체를 제공합니다. 그 중 하나는 x86 컴퓨터용이고 다른 하나는 x64 컴퓨터용입니다.  

    > [!NOTE]  
    >  **x86 알 수 없는 컴퓨터** 개체는 x86으로만 지원되는 컴퓨터를 위한 개체입니다. **x64 알 수 없는 컴퓨터** 개체는 x86 및 x64으로만 지원되는 컴퓨터를 위한 개체입니다. 즉, 이러한 개체는 대상 컴퓨터의 아키텍처를 설명합니다. 이 개체는 대상 컴퓨터에 배포할 운영 체제는 설명하지 않습니다.  

-   알 수 없는 컴퓨터 배포를 지원하기 위해 PXE 사용 배포 지점을 구성하거나 미디어를 만듭니다.  

-   운영 체제를 설치하기 위한 작업 순서를 배포합니다.  

## <a name="unknown-computer-installation-process"></a>알 수 없는 컴퓨터 설치 프로세스  
 컴퓨터가 PXE 또는 미디어에서 처음 시작되는 경우 Configuration Manager에서 Configuration Manager 데이터베이스에 해당 컴퓨터에 대한 레코드가 있는지 확인합니다. 레코드가 있는 경우 Configuration Manager는 이 레코드에 배포된 작업 순서가 있는지 확인합니다. 레코드가 없는 경우 Configuration Manager는 알 수 없는 컴퓨터 개체에 배포된 작업 순서가 있는지 확인합니다. 두 경우 모두 Configuration Manager에서 다음 작업 중 하나를 수행합니다.  

- 사용 가능한 작업 순서가 있는 경우 Configuration Manager에서 작업 순서를 실행할지 묻는 메시지가 표시됩니다.  

- 필수 작업 순서가 있는 경우 Configuration Manager는 해당 작업 순서를 자동으로 실행합니다.  

- 레코드에 대해 배포된 작업 순서가 없는 경우 Configuration Manager는 대상 컴퓨터에 대해 배포된 작업 순서가 없다는 오류를 생성합니다.  

  알 수 없는 컴퓨터가 시작되면 Configuration Manager는 해당 컴퓨터를 알 수 없는 컴퓨터가 아닌 프로비전 안 된 컴퓨터로 인식합니다. 따라서 이 컴퓨터는 이제 알 수 없는 컴퓨터 개체에 배포되었던 작업 순서를 수신할 수 있습니다. 그런 다음 배포된 작업 순서에서는 Configuration Manager 클라이언트가 포함된 운영 체제 이미지를 설치합니다.  

  Configuration Manager 클라이언트가 설치되면 컴퓨터의 레코드가 만들어지고 이 컴퓨터는 해당 Configuration Manager 컬렉션에 표시됩니다. 컴퓨터에 운영 체제 이미지 또는 Configuration Manager 클라이언트를 설치하지 못한 경우 컴퓨터에 대한 "알 수 없는" 레코드가 만들어지고 이 컴퓨터는 **모든 시스템** 컬렉션에 표시됩니다.  

> [!NOTE]  
>  운영 체제 이미지를 설치하는 동안 작업 순서는 이 컴퓨터에서 컬렉션 변수를 검색할 수 있지만 컴퓨터 변수는 검색할 수 없습니다.  

##  <a name="BKMK_EnablingUnknown"></a> 알 수 없는 컴퓨터 지원 사용  
 다음을 사용하여 PXE 배포, 부팅 가능한 미디어, 미리 준비된 미디어를 사용하여 운영 체제를 배포할 때 알 수 없는 컴퓨터 지원을 사용할 수 있습니다.  

-   **PXE**  

     PXE가 설정된 배포 지점에 대해 **PXE** 탭에서 **알 수 없는 컴퓨터 지원 사용** 확인란을 선택합니다. 자세한 내용은 [PXE 요청을 수락하도록 배포 지점 구성](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)을 참조하세요.  

-   **부팅 가능한 미디어**  

     작업 순서 미디어 만들기 마법사의 **보안** 페이지에서 **알 수 없는 컴퓨터 지원 사용** 확인란을 선택합니다. 자세한 내용은 [PXE 요청을 수락하도록 배포 지점 구성](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint) 및 [System Center Configuration Manager에서 PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

-   **미리 준비된 미디어**  

     작업 순서 미디어 만들기 마법사의 **보안** 페이지에서 **알 수 없는 컴퓨터 지원 사용** 확인란을 선택합니다. 자세한 내용은 [System Center Configuration Manager에서 사전 준비된 미디어 만들기](../deploy-use/create-prestaged-media.md)를 참조하세요.  
