---
title: "최신 버전으로 Windows 업그레이드 | Microsoft 문서"
description: "Configuration Manager를 사용하여 Windows 7 이상 운영 체제를 Windows 10으로 업그레이드하는 방법을 알아봅니다."
ms.custom: na
ms.date: 02/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: "13"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 412c2c644cc7f17f307c02b84471f3ee494045ec
ms.sourcegitcommit: 31c670a4bce74fd64a7d46ebf7702f65b80d4147
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/13/2017
---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 Windows를 최신 버전으로 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 System Center Configuration Manager에서 컴퓨터 운영 체제를 Windows 7 이상에서 Windows 10으로 업그레이드하거나 대상 컴퓨터의 운영 체제를 Windows Server 2012에서 Windows Server 2016으로 업그레이드하는 단계를 제공합니다. 독립 실행형 미디어 또는 소프트웨어 센터와 같은 여러 다양한 배포 방법 중에서 선택할 수 있습니다. 전체 업그레이드 시나리오:  

-   현재 다음을 실행하는 컴퓨터의 운영 체제를 업그레이드합니다.
    - Windows 7, Windows 8 또는 Windows 8.1. Windows 10의 빌드 간 업그레이드를 수행할 수도 있습니다. 예를 들어 Windows 10 RTM을 Windows 10, 1511 버전으로 업그레이드할 수 있습니다.  
    - Windows Server 2012. Windows Server 2016의 빌드 간 업그레이드를 수행할 수도 있습니다. 지원되는 업그레이드 경로에 대한 자세한 내용은 [지원되는 업그레이드 경로](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016)를 참조하세요.    

-   컴퓨터의 응용 프로그램, 설정 및 사용자 데이터는 그대로 유지됩니다.  

-   Windows ADK와 같은 외부 종속성이 없습니다.  

-   기존의 운영 체제 배포에 비해 속도가 빠르고 복원성도 뛰어납니다.  

 작업 순서를 사용하여 네트워크를 통해 운영 체제를 배포하려면 다음 섹션을 사용하세요.  

##  <a name="BKMK_Plan"></a> 계획  

-   **운영 체제를 업그레이드하는 작업 순서에 대한 제한 사항 검토**  

     운영 체제를 업그레이드하는 작업 순서에 대한 다음 요구 사항과 제한 사항을 검토하여 사용자의 요구를 충족하는지 확인합니다.  

    -   이미지를 설치한 후 운영 체제를 배포하고 컴퓨터를 구성하는 핵심 작업과 관련된 작업 순서 단계만 추가해야 합니다. 여기에는 패키지, 응용 프로그램 또는 업데이트를 설치하는 단계 및 명령줄/PowerShell을 실행하거나 동적 변수를 설정하는 단계가 포함됩니다.  

    -   업그레이드 작업 순서를 배포하기 전에 컴퓨터에 설치된 드라이버와 응용 프로그램을 검토하여 Windows 10과 호환되는지를 확인합니다.  

    -   다음 작업은 전체 업그레이드와 호환되지 않으며 기존의 운영 체제 배포를 사용해야 합니다.  

        -   컴퓨터 도메인 구성원 자격 변경 또는 로컬 관리자 업데이트  

        -   디스크 분할, x86에서 x64로 아키텍처 변경, UEFI 구현, 기본 운영 체제 언어 수정 등, 컴퓨터에서 구현하는 기본적인 변경  

        -   사용자 지정 기본 이미지 또는 타사<sup> </sup> 디스크 암호화를 사용하거나 WinPE 오프라인 작업을 수행해야 하는 등의 사용자 지정 요구 사항이 적용됩니다.  

-   **인프라 요구 사항 계획 및 구현**  

     업그레이드 시나리오에 대한 유일한 필수 구성 요소는 운영 체제 업그레이드 패키지 및 작업 순서에 포함된 기타 패키지에 사용할 수 있는 배포 지점입니다. 자세한 내용은 [배포 지점 설치 또는 수정](../../core/servers/deploy/configure/install-and-configure-distribution-points.md)을 참조하세요.

##  <a name="BKMK_Configure"></a> 구성  

1.  **운영 체제 업그레이드 패키지 준비**  

     Windows 10 업그레이드 패키지에는 대상 컴퓨터에 운영 체제를 설치하는 데 필요한 원본 파일이 포함되어 있습니다. 업그레이드 패키지의 버전, 아키텍처 및 언어는 업그레이드할 클라이언트와 같아야 합니다.  자세한 내용은 [운영 체제 업그레이드 패키지 관리](../get-started/manage-operating-system-upgrade-packages.md)를 참조하세요.  

2.  **운영 체제를 업그레이드하는 작업 순서 만들기**  

     운영 체제 업그레이드를 자동화하려면 [운영 체제를 업그레이드하는 작업 순서 만들기](create-a-task-sequence-to-upgrade-an-operating-system.md)의 단계를 따르세요.  

    > [!IMPORTANT]
    > 독립 실행형 미디어를 사용할 경우 부팅 이미지를 작업 순서 미디어 마법사에서 사용할 수 있도록 작업 순서에 포함해야 합니다.

    > [!NOTE]  
    > 일반적으로 [운영 체제를 업그레이드하는 작업 순서 만들기](create-a-task-sequence-to-upgrade-an-operating-system.md)의 단계를 사용하여 운영 체제를 Windows 10으로 업그레이드하는 작업 순서를 만듭니다. 작업 순서에는 운영 체제 업그레이드 단계와 종단 간 업그레이드 프로세스를 처리하기 위한 추가적인 권장 단계 및 그룹이 포함됩니다. 그렇지만 사용자 지정 작업 순서를 만들고 [운영 체제 업그레이드](../understand/task-sequence-steps.md#BKMK_UpgradeOS) 작업 순서 단계를 추가하여 운영 체제를 업그레이드할 수 있습니다. 이것이 운영 체제를 Windows 10으로 업그레이드하는 데 필요한 유일한 단계입니다. 이 방법을 선택하는 경우 운영 체제 업그레이드 단계 다음에 [컴퓨터 다시 시작](../understand/task-sequence-steps.md#BKMK_RestartComputer) 단계를 추가하여 업그레이드를 완료합니다. **현재 설치된 기본 운영 체제** 설정을 사용하여 컴퓨터를 Windows PE가 아닌 설치된 운영 체제로 다시 시작해야 합니다.  

##  <a name="BKMK_Deploy"></a> 배포  

-   다음 배포 방법 중 하나를 사용하여 운영 체제를 배포합니다.  

    -   [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

## <a name="monitor"></a>모니터  

-   **작업 순서 배포 모니터링**  

     운영 체제를 업그레이드하는 작업 순서 배포를 모니터링하려면 [운영 체제 배포 모니터링](monitor-operating-system-deployments.md)을 참조하세요.  
