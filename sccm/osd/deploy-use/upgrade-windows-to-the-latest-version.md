---
title: Windows 10으로 업그레이드
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 Windows 7 이상 OS를 Windows 10으로 업그레이드하는 방법을 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 35312c92a20f8e3842b5ee47dd3b916631671e45
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53417356"
---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 Windows를 최신 버전으로 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 컴퓨터의 OS를 업그레이드하는 Configuration Manager의 단계를 제공합니다. 독립 실행형 미디어 또는 소프트웨어 센터와 같은 여러 다양한 배포 방법 중에서 선택할 수 있습니다. 현재 위치 업그레이드 시나리오에는 다음과 같은 기능이 있습니다.  

-   현재 다음을 실행하는 컴퓨터의 OS를 업그레이드합니다.
    - Windows 7, Windows 8 또는 Windows 8.1. Windows 10의 빌드 간 업그레이드를 수행할 수도 있습니다. 예를 들어 Windows 10 버전 1607을 Windows 10, 버전 1709로 업그레이드할 수 있습니다.  
    
    - Windows Server 2012. Windows Server 2016의 빌드 간 업그레이드를 수행할 수도 있습니다. 지원되는 업그레이드 경로에 대한 자세한 내용은 [지원되는 업그레이드 경로](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016)를 참조하세요.    

-   컴퓨터의 애플리케이션, 설정 및 사용자 데이터는 그대로 유지됩니다.  

-   Windows ADK와 같은 외부 종속성이 없습니다.  

-   기존의 OS 배포에 비해 속도가 빠르고 복원성도 뛰어납니다.  


> [!Note]  
> 버전 1802부터 Windows 10 현재 위치 업그레이드 작업 순서는 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 통해 관리되는 인터넷 기반 클라이언트에 대한 배포를 지원합니다. 이 기능을 사용하면 원격 사용자가 인트라넷에 연결할 필요 없이 Windows 10으로 쉽게 업그레이드할 수 있습니다. 자세한 내용은 [CMG를 통한 Windows 10 현재 위치 업그레이드 배포](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg)를 참조하세요. <!-- 1357149 -->



##  <a name="BKMK_Plan"></a> 계획  

### <a name="task-sequence-requirements-and-limitations"></a>작업 순서 요구 사항 및 제한 사항

OS를 업그레이드하는 작업 순서에 대한 다음 요구 사항과 제한 사항을 검토하여 사용자의 요구를 충족하는지 확인합니다.  

- OS 업그레이드의 핵심 작업과 관련된 작업 순서 단계만 추가합니다. 이러한 단계는 패키지, 애플리케이션 또는 업데이트 설치를 주로 포함합니다. 또한 명령줄, PowerShell을 실행하거나 동적 변수를 설정하는 단계를 사용합니다.  

- 업그레이드 작업 순서를 배포하기 전에 컴퓨터에 설치된 드라이버와 애플리케이션을 검토하여 Windows 10과 호환되는지를 확인합니다.  

- 다음 작업은 현재 위치 업그레이드와 호환되지 않습니다. 기존 OS 배포를 사용해야 합니다.  

  - 컴퓨터의 도메인 구성원 자격 변경 또는 로컬 관리자 그룹 업데이트  

  - 다음과 같은 컴퓨터에서 기본적인 변경 구현: 
    - 디스크 파티션 변경
    - x86에서 x64로 시스템 아키텍처 변경
    - UEFI 구현 (가능한 옵션에 대한 자세한 내용은 [현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)을 참조하세요.)
    - 기본 OS 언어 수정  

  - 사용자 지정 기본 이미지 또는 타사 디스크 암호화를 사용하거나 WinPE 오프라인 작업을 수행해야 하는 등의 사용자 지정 요구 사항이 적용됩니다.  

### <a name="infrastructure-requirements"></a>인프라 요구 사항  

업그레이드 시나리오에 대한 유일한 필수 구성 요소는 사용 가능한 배포 지점을 가져야 하는 것입니다. OS 업그레이드 패키지 및 작업 순서에 포함하는 다른 패키지를 배포합니다. 자세한 내용은 [배포 지점 설치 또는 수정](../../core/servers/deploy/configure/install-and-configure-distribution-points.md)을 참조하세요.



##  <a name="BKMK_Configure"></a> 구성  

### <a name="prepare-the-os-upgrade-package"></a>OS 업그레이드 패키지 준비  

  Windows 10 업그레이드 패키지에는 대상 컴퓨터에 OS를 설치하는 데 필요한 원본 파일이 포함되어 있습니다. 업그레이드 패키지의 버전, 아키텍처 및 언어는 업그레이드할 클라이언트와 같아야 합니다. 자세한 내용은 [운영 체제 업그레이드 패키지 관리](../get-started/manage-operating-system-upgrade-packages.md)를 참조하세요.  


### <a name="create-a-task-sequence-to-upgrade-the-os"></a>OS를 업그레이드하는 작업 순서 만들기  

  OS 업그레이드를 자동화하려면 [운영 체제를 업그레이드하는 작업 순서 만들기](create-a-task-sequence-to-upgrade-an-operating-system.md)의 단계를 사용합니다.  

   > [!NOTE]  
   > 일반적으로 [운영 체제를 업그레이드하는 작업 순서 만들기](create-a-task-sequence-to-upgrade-an-operating-system.md)의 단계를 사용하여 OS를 Windows 10으로 업그레이드하는 작업 순서를 만듭니다. 작업 순서에는 운영 체제 업그레이드 단계와 종단 간 업그레이드 프로세스를 처리하기 위한 추가적인 권장 단계 및 그룹이 포함됩니다. 그렇지만 사용자 지정 작업 순서를 만들고 [운영 체제 업그레이드](../understand/task-sequence-steps.md#BKMK_UpgradeOS) 작업 순서 단계를 추가하여 OS를 업그레이드할 수 있습니다. 이 단계는 OS를 Windows 10으로 업그레이드하는 데 필요한 유일한 작업입니다. 이 방법을 선택하는 경우 운영 체제 업그레이드 단계 다음에 [컴퓨터 다시 시작](../understand/task-sequence-steps.md#BKMK_RestartComputer) 단계를 추가하여 업그레이드를 완료합니다. **현재 설치된 기본 운영 체제** 설정을 사용하여 컴퓨터를 Windows PE가 아닌 설치된 OS로 다시 시작해야 합니다.  



##  <a name="BKMK_Deploy"></a> 배포  

OS를 배포하려면 다음 배포 방법 중 하나를 사용합니다.  

  -   [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](use-software-center-to-deploy-windows-over-the-network.md)  

  -   [독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

      > [!IMPORTANT]  
      > 독립 실행형 미디어를 사용할 경우 부팅 이미지를 작업 순서 미디어 마법사에서 사용할 수 있도록 작업 순서에 포함해야 합니다.




## <a name="monitor"></a>모니터  

OS를 업그레이드하는 작업 순서 배포를 모니터링하려면 [운영 체제 배포 모니터링](monitor-operating-system-deployments.md)을 참조하세요.  
