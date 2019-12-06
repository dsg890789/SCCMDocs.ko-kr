---
title: 기존 컴퓨터의 OS 새로 고침
titleSuffix: Configuration Manager
description: Configuration Manager에서 몇 가지 방법을 사용하여 기존 컴퓨터에 파티션을 만들고 포맷하고 컴퓨터에 새 운영 체제를 설치할 수 있습니다.
ms.date: 08/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b189a346-8c0d-4870-a876-0719fbb0ab04
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2443f8ddc280e880ffb43a8e82bbc47b49d4395
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70110212"
---
# <a name="refresh-an-existing-computer-with-a-new-version-of-windows"></a>새 버전의 Windows로 기존 컴퓨터 새로 고침

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 사용 하 여 기존 컴퓨터를 분할 하 고 포맷 한 다음 새 OS를 설치 합니다. 이 프로세스를 *이미지로 다시 설치* 또는 *초기화 및 로드*라고도 합니다. 이 시나리오에서는 PXE, 부팅 가능한 미디어 또는 소프트웨어 센터와 같은 여러 다양한 배포 방법 중에서 선택할 수 있습니다. 또한 상태 마이그레이션 지점을 사용 하 여 설정을 저장 한 다음 새 OS로 복원할 수 있습니다.

올바른 OS 배포 시나리오를 선택 하려면 [엔터프라이즈 운영 체제를 배포 하는 시나리오](/sccm/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems)를 참조 하세요.  

## <a name="BKMK_Plan"></a> 계획  

### <a name="plan-for-and-implement-infrastructure-requirements"></a>인프라 요구 사항 계획 및 구현

OS를 배포 하기 전에 준비 해야 하는 몇 가지 인프라 요구 사항이 있습니다. 이러한 요구 사항 중 일부에는 Windows ADK, USMT (사용자 환경 마이그레이션 도구) 및 WDS (Windows 배포 서비스)가 포함 됩니다. 자세한 내용은 [OS 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

### <a name="install-a-state-migration-point"></a>상태 마이그레이션 지점 설치

기존 컴퓨터에서 설정을 캡처한 다음 설정을 새 OS로 복원 하려면 상태 마이그레이션 지점을 사용 하는 것이 좋습니다. 자세한 내용은 [상태 마이그레이션 지점](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_StateMigrationPoints)을 참조하세요.  

## <a name="BKMK_Configure"></a> 구성  

### <a name="prepare-a-boot-image"></a>부팅 이미지 준비

부팅 이미지는 Windows PE 환경에서 컴퓨터를 시작 합니다. Windows PE는 제한 된 구성 요소 및 서비스를 포함 하는 최소 OS입니다. 그러면 Windows PE에서 컴퓨터에 전체 Windows OS를 설치할 수 Configuration Manager.

자세한 내용은 다음 아티클을 참조하세요.

- [부팅 이미지 관리](/sccm/osd/get-started/manage-boot-images)

- [부팅 이미지 사용자 지정](/sccm/osd/get-started/customize-boot-images)

- [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

### <a name="prepare-an-os-image"></a>OS 이미지 준비

OS 이미지에는 대상 컴퓨터에 OS를 설치 하는 데 필요한 파일이 포함 되어 있습니다.

자세한 내용은 다음 아티클을 참조하세요.

- [OS 이미지 관리](/sccm/osd/get-started/manage-operating-system-images)

- [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

### <a name="create-a-task-sequence-to-deploy-an-os"></a>OS를 배포하는 작업 순서 만들기

작업 순서를 사용 하 여 OS 설치를 자동화 합니다. 선택한 배포 방법에 따라 작업 순서에 대한 추가적으로 고려해야 할 사항이 있을 수 있습니다.

자세한 내용은 다음 아티클을 참조하세요.

- [OS를 설치하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system)

- [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)

## <a name="BKMK_Deploy"></a> 배포

- OS를 배포하려면 다음 배포 방법 중 하나를 사용합니다.  

  - [PXE를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)  

  - [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)  

  - [팩터리 또는 로컬 저장소에 OEM에 대한 이미지 만들기](/sccm/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot)  

  - [독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](/sccm/osd/deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network)  

  - [부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network)  

  - [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network)  

## <a name="monitor"></a>모니터  

자세한 내용은 [OS 배포 모니터링](/sccm/osd/deploy-use/monitor-operating-system-deployments)을 참조하세요.  

> [!Note]
> UEFI 장치를 이미지로 다시 설치 하면 Windows 부팅 관리자가 부팅 로더에 새 항목을 만듭니다. 이 동작은 테스트 환경 또는 학생 랩에서와 같이 장치를 반복적으로 이미지로 다시 설치 하는 경우에 가장 두드러지게 나타납니다. 일반적으로 장치의 성능 또는 사용에 영향을 주지 않습니다. 목록이 너무 크면 일부 특정 하드웨어 장치에서 기능 문제가 발생할 수 있습니다. 예를 들어 외부 USB 드라이브로 부팅 하거나 목록에서 현재 부팅 항목을 선택할 수 없습니다. Windows **bcdedit** 명령을 사용 하 여 사용 되지 않는 부팅 항목을 지웁니다. 자세한 내용은 [BCDEdit/deletevalue](https://docs.microsoft.com/windows-hardware/drivers/devtest/bcdedit--deletevalue)를 참조 하세요.<!-- 2841926 -->
