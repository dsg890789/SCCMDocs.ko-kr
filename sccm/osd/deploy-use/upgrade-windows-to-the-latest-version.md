---
title: Windows 10으로 업그레이드
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 Windows 7 이상 OS를 Windows 10으로 업그레이드하는 방법을 알아봅니다.
ms.date: 08/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b85c29bb87bb8b05f857198b56ed8ffebf46d964
ms.sourcegitcommit: ee0d33ef79e1de1f5057a7d7e743f500da977caa
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70150808"
---
# <a name="upgrade-windows-to-the-latest-version-with-configuration-manager"></a>Configuration Manager를 사용하여 최신 버전으로 Windows 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 컴퓨터의 OS를 업그레이드하는 Configuration Manager의 단계를 제공합니다. 독립 실행형 미디어 또는 소프트웨어 센터와 같은 여러 다양한 배포 방법 중에서 선택할 수 있습니다. 현재 위치 업그레이드 시나리오에는 다음과 같은 기능이 있습니다.  

- OS를 Windows 10 또는 Windows Server 2016 이상으로 업그레이드 합니다.

- 컴퓨터의 애플리케이션, 설정 및 사용자 데이터 유지

- Windows ADK와 같은 외부 종속성 없음

- 기존의 OS 배포에 비해 빠른 속도 및 뛰어난 복원성

> [!Note]  
> Windows 10 내부 업그레이드 작업 순서에서 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 통해 관리되는 인터넷 기반 클라이언트에 대한 배포를 지원합니다. 이 기능을 사용하면 원격 사용자가 인트라넷에 연결할 필요 없이 Windows 10으로 쉽게 업그레이드할 수 있습니다. 자세한 내용은 [CMG를 통한 Windows 10 현재 위치 업그레이드 배포](/sccm/osd/deploy-use/deploy-a-task-sequence#deploy-windows-10-in-place-upgrade-via-cmg)를 참조하세요. <!-- 1357149 -->


## <a name="supported-versions"></a>지원되는 버전

### <a name="upgrade-version"></a>업그레이드 버전

OS 업그레이드 패키지만 만들어 다음 OS 버전으로 업그레이드 합니다.

- Windows 10
- Windows Server 2016
- Windows Server 2019

### <a name="original-version"></a>원본 버전

장치는 OS 업그레이드 작업 순서를 대상으로 하려면 다음 OS 버전 중 하나를 실행 해야 합니다.

#### <a name="windows-client"></a>Windows 클라이언트

- Windows 7
- Windows 8.1
- 이전 버전의 Windows 10 예를 들어 Windows 10 버전 1809을 Windows 10, 버전 1903으로 업그레이드할 수 있습니다.  

자세한 내용은 [Windows 10 업그레이드 경로](https://docs.microsoft.com/windows/deployment/upgrade/windows-10-upgrade-paths)를 참조 하세요.

#### <a name="windows-server"></a>Windows Server

- Windows Server 2012
- Windows Server 2012 R2
- 이전 버전의 Windows Server 2016
- 이전 버전의 Windows Server 2019

Windows Server의 지원 되는 업그레이드 경로에 대 한 자세한 내용은 [Windows server 2016 지원 되는 업그레이드 경로](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016) 및 [Windows server 업그레이드 센터](http://aka.ms/upgradecenter)를 참조 하세요.


## <a name="BKMK_Plan"></a> 계획  

### <a name="task-sequence-requirements-and-limitations"></a>작업 순서 요구 사항 및 제한 사항

OS를 업그레이드하는 작업 순서에 대한 다음 요구 사항과 제한 사항을 검토하여 사용자의 요구를 충족하는지 확인합니다.  

- OS 업그레이드의 핵심 작업과 관련된 작업 순서 단계만 추가합니다. 이러한 단계는 패키지, 애플리케이션 또는 업데이트 설치를 주로 포함합니다. 또한 명령줄, PowerShell을 실행하거나 동적 변수를 설정하는 단계를 사용합니다.  

- 컴퓨터에 설치 된 드라이버 및 응용 프로그램을 검토 합니다. 업그레이드 작업 순서를 배포 하기 전에 드라이버가 Windows 10과 호환 되는지 확인 합니다.  

다음 작업은 현재 위치 업그레이드와 호환되지 않습니다. 기존 OS 배포를 사용해야 합니다.  

- 컴퓨터의 도메인 구성원 자격 변경 또는 로컬 관리자 그룹 업데이트  

- 다음과 같은 컴퓨터에서 기본적인 변경 구현:

  - 디스크 파티션 변경
  - x86에서 x64로 시스템 아키텍처 변경
  - UEFI 구현 (가능한 옵션에 대한 자세한 내용은 [현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)을 참조하세요.)
  - 기본 OS 언어 수정  

- 사용자 지정 기본 이미지 또는 타사 디스크 암호화를 사용하거나 WinPE 오프라인 작업을 수행해야 하는 등의 사용자 지정 요구 사항이 적용됩니다.  

### <a name="infrastructure-requirements"></a>인프라 요구 사항  

업그레이드 시나리오에 대한 유일한 필수 구성 요소는 사용 가능한 배포 지점을 가져야 하는 것입니다. OS 업그레이드 패키지 및 작업 순서에 포함하는 다른 패키지를 배포합니다. 자세한 내용은 [배포 지점 설치 또는 수정](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points)을 참조하세요.


## <a name="BKMK_Configure"></a> 구성  

### <a name="prepare-the-os-upgrade-package"></a>OS 업그레이드 패키지 준비  

Windows 10 업그레이드 패키지에는 대상 컴퓨터에 OS를 설치하는 데 필요한 원본 파일이 포함되어 있습니다. 업그레이드 패키지의 버전, 아키텍처 및 언어는 업그레이드할 클라이언트와 같아야 합니다. 자세한 내용은 [OS 업그레이드 패키지 관리](/sccm/osd/get-started/manage-operating-system-upgrade-packages)를 참조하세요.  

### <a name="create-a-task-sequence-to-upgrade-the-os"></a>OS를 업그레이드하는 작업 순서 만들기  

OS 업그레이드를 자동화하려면 [운영 체제를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)의 단계를 따릅니다.  

> [!NOTE]  
> 일반적으로 [운영 체제를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)의 단계를 따라 OS를 Windows 10으로 업그레이드하는 작업 순서를 만듭니다. 작업 순서에는 **운영 체제 업그레이드** 단계와 엔드투엔드 업그레이드 프로세스를 처리하기 위한 추가적인 권장 단계 및 그룹이 포함됩니다.
>
> 사용자 지정 작업 순서를 만들고 [OS 업그레이드](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS) 단계를 추가할 수 있습니다. 이 단계는 OS를 Windows 10으로 업그레이드하는 데 필요한 유일한 작업입니다. 이 방법을 선택하는 경우 **운영 체제 업그레이드** 단계 다음에 [컴퓨터 다시 시작](/sccm/osd/understand/task-sequence-steps#BKMK_RestartComputer) 단계를 추가하여 업그레이드를 완료합니다. **현재 설치된 기본 운영 체제** 설정을 사용하여 컴퓨터를 Windows PE가 아닌 설치된 OS로 다시 시작해야 합니다.  


## <a name="BKMK_Deploy"></a> 배포  

OS를 배포하려면 다음 배포 방법 중 하나를 사용합니다.  

- [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network)  

- [독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](/sccm/osd/deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network)  

  > [!IMPORTANT]  
  > 독립 실행형 미디어를 사용 하는 경우 작업 순서에 부팅 이미지를 포함 해야 합니다. 이 구성은 작업 순서 미디어 마법사에서 작업 순서를 사용할 수 있도록 합니다.


## <a name="monitor"></a>모니터  

OS를 업그레이드하는 작업 순서 배포를 모니터링하려면 [운영 체제 배포 모니터링](/sccm/osd/deploy-use/monitor-operating-system-deployments)을 참조하세요.  
