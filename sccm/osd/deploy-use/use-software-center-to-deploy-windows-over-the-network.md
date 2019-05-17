---
title: 소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포
titleSuffix: Configuration Manager
description: 소프트웨어 센터에 운영 체제를 배포하여 기존 컴퓨터를 새 버전의 Windows로 새로 고치거나 Windows를 최신 버전으로 업그레이드할 수 있습니다.
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa86d335b94db796f37955462abddeb9451ccf4e
ms.sourcegitcommit: 2db6863c6740380478a4a8beb74f03b8178280ba
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083133"
---
# <a name="use-software-center-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 운영 체제를 설치하기 위한 작업 순서를 소프트웨어 센터에서 사용하도록 만들 수 있습니다. 다음 운영 체제 배포 시나리오에서 소프트웨어 센터에 운영 체제를 배포할 수 있습니다.

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [최신 버전으로 Windows 업그레이드](upgrade-windows-to-the-latest-version.md)

운영 체제 배포 시나리오 중 하나의 단계를 완료합니다. 그런 후 다음 섹션을 사용하여 소프트웨어 센터에서 사용할 수 있는 배포를 준비합니다.

## <a name="configure-deployment-settings"></a>배포 설정 구성  
소프트웨어 센터에서 운영 체제 배포를 사용하용할 수 있게 하려면 해당 배포를 구성합니다. 소프트웨어 배포 마법사의 **배포 설정** 페이지 또는 배포에 대한 속성의 **배포 설정** 탭에서 배포를 구성할 수 있습니다. **다음에 사용 가능하도록 설정** 설정에 대해 **Configuration Manager 클라이언트만** 또는 **Configuration Manager 클라이언트, 미디어 및 PXE**를 구성합니다. 시스템에서 운영 체제가 배포되면 대상 컬렉션의 구성원에 대해 소프트웨어 센터에 해당 운영 체제가 표시됩니다.

##  <a name="BKMK_Deploy"></a> 컴퓨터에 작업 순서 배포  
대상 컬렉션에 운영 체제 배포 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/deploy-a-task-sequence)항목을 참조하세요. 소프트웨어 센터에 대해 운영 체제를 배포할 경우 배포를 필수 또는 사용 가능으로 구성할 수 있습니다.

-   **필수 배포**: 필수 배포는 소프트웨어 센터에서 운영 체제를 사용할 수 있게 하지만 구성된 할당 일정에 따라 자동으로 시작됩니다.

-   **사용 가능한 배포**: 해당 운영 체제를 소프트웨어 센터에서 사용할 수 있으며 사용자가 필요할 때 설치할 수 있습니다.
