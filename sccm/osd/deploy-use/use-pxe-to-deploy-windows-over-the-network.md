---
title: 네트워크를 통해 OSD에 대해 PXE 사용
titleSuffix: Configuration Manager
description: PXE 시작 OS 배포를 사용하여 컴퓨터의 운영 체제를 새로 고치거나 새 컴퓨터에 새 버전의 Windows를 설치할 수 있습니다.
ms.date: 05/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 71fab49dc6ba5d949aeaf48145e1f7d0446c0f91
ms.sourcegitcommit: 18a94eb78043cb565b05cd0e9469b939b29cccf0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355005"
---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-configuration-manager"></a>Configuration Manager에서 PXE를 사용하여 네트워크를 통해 Windows 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 PXE(Preboot Execution Environment) 시작 OS 배포를 사용하면 클라이언트가 네트워크를 통해 운영 체제를 요청 및 배포할 수 있습니다. 이 배포 시나리오에서 OS 이미지와 부팅 이미지를 PXE 사용 배포 지점으로 보냅니다.

> [!NOTE]  
> x64 BIOS 컴퓨터만을 대상으로 OS 배포를 만드는 경우 x64 부팅 이미지와 x86 부팅 이미지 모두를 배포 지점에서 사용할 수 있어야 합니다.

다음과 같은 시나리오에서 PXE 시작 OS 배포를 사용할 수 있습니다.

- [새 버전의 Windows로 기존 컴퓨터 새로 고침](/sccm/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)  

- [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](/sccm/osd/deploy-use/install-new-windows-version-new-computer-bare-metal)  

OS 배포 시나리오 중 하나의 단계를 완료한 다음, 이 문서의 섹션을 사용하여 PXE 시작 배포를 준비합니다.



## <a name="BKMK_Configure"></a> PXE 요청을 수락하도록 하나 이상의 배포 지점 구성

PXE 부팅 요청을 만드는 Configuration Manager 클라이언트에 운영 체제를 배포하려면 PXE 요청을 수락하도록 하나 이상의 배포 지점을 구성해야 합니다. 구성하고 나면 배포 지점에서 PXE 부팅 요청에 응답하고 수행해야 할 적절한 배포 작업을 결정합니다. 자세한 내용은 [배포 지점 설치 또는 수정](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  

> [!NOTE]  
> 여러 서브넷을 지원하기 위해 단일 PXE 사용 배포 지점을 구성하는 경우 DHCP 옵션을 사용할 수 없습니다. 라우터에서 IP 도우미를 구성하여 PXE 요청을 PXE 사용 배포 지점으로 전달할 수 있도록 합니다.

> [!Note]  
> 버전 1810 이하에서는 DHCP 서버도 실행하는 서버에서 WDS 없이 PXE 응답기를 사용하도록 지원되지 않습니다.
>
> 버전 1902부터는 Windows 배포 서비스 없이 배포 지점에서 PXE 응답기를 사용하도록 설정하면 이제 DHCP 서비스와 동일한 서버에서 실행할 수 있습니다.<!--3734270, SCCMDocs-pr #3416--> 이 구성을 지원하려면 다음 설정을 추가합니다.  
>
> - 다음 레지스트리 키 `HKLM\Software\Microsoft\SMS\DP`에서 DWord 값 **DoNotListenOnDhcpPort**를 `1`로 설정합니다.
> - DHCP 옵션 60을 `PXEClient`로 설정합니다.  
> - 서버에서 SCCMPXE 및 DHCP 서비스를 다시 시작합니다.  


## <a name="prepare-a-pxe-enabled-boot-image"></a>PXE 사용 부팅 이미지 준비

PXE를 사용하여 OS를 배포하려면 하나 이상의 PXE 사용 배포 지점에 x86 및 x64 PXE 사용 부팅 이미지가 둘 다 배포되어 있어야 합니다. 다음 정보를 사용하여 부팅 이미지에서 PXE를 사용하도록 설정하고 배포 지점에 부팅 이미지를 배포하세요.

- 부팅 이미지에서 PXE를 사용하도록 설정하려면 부팅 이미지 속성의 **데이터 원본** 탭에서 **PXE 사용 배포 지점에서 이 부팅 이미지 배포**를 선택합니다.

- 부팅 이미지에 대한 속성을 변경하면 부팅 이미지가 업데이트되고 배포 지점에 부팅 이미지가 다시 배포됩니다. 자세한 내용은 [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.



## <a name="manage-duplicate-hardware-identifiers"></a>중복된 하드웨어 식별자 관리

Configuration Manager는 SMBIOS 특성을 중복했거나 공유 네트워크 어댑터를 사용하는 경우 여러 컴퓨터를 동일한 디바이스로 인식할 수 있습니다. 계층 설정에서 중복 하드웨어 식별자를 관리하여 이러한 문제를 완화합니다. 자세한 내용은 [중복된 하드웨어 식별자 관리](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers)를 참조하세요.



## <a name="BKMK_PXEExclusionList"></a> PXE 배포의 제외 목록 만들기

> [!Note]  
> 상황에 따라 [중복된 하드웨어 식별자 관리](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers) 프로세스가 더 쉬울 수 있습니다.<!-- SCCMDocs issue 802 -->
>
> 일부 시나리오에서는 각 동작이 다른 결과를 야기할 수 있습니다. 제외 목록에 나열된 MAC 주소로는 어떤 경우든 클라이언트가 절대 부팅되지 않습니다.
>
> 중복된 ID 목록은 클라이언트에 대한 작업 순서 정책의 찾기 위해 MAC 주소를 사용하지 않습니다. SMBIOS ID와 일치하거나 알 수 없는 컴퓨터에 대한 작업 순서 정책이 있는 경우 클라이언트가 계속 부팅됩니다.

PXE를 사용하여 운영 체제를 배포할 때 각 배포 지점에 제외 목록을 만들 수 있습니다. 배포 지점에서 무시하도록 하려는 컴퓨터의 MAC 주소를 제외 목록에 추가합니다. 나열된 컴퓨터는 Configuration Manager에서 PXE 배포에 사용하는 배포 작업 순서를 받지 않습니다.

### <a name="process-to-create-the-exclusion-list"></a>제외 목록을 만드는 프로세스

1. PXE에 사용되는 배포 지점에서 텍스트 파일을 만듭니다. 예를 들어 이 텍스트 파일의 이름을 **pxeExceptions.txt**로 지정합니다.  

2. 메모장과 같은 일반 텍스트 편집기를 사용하여 PXE 사용 배포 지점에서 무시할 컴퓨터의 MAC 주소를 추가합니다. MAC 주소 값은 콜론으로 구분하고 각 주소를 별도의 줄에 입력합니다. `01:23:45:67:89:ab`  

3. PXE 사용 배포 지점 사이트 시스템 서버에서 텍스트 파일을 저장합니다. 텍스트 파일은 서버의 모든 위치에 저장할 수 있습니다.  

4. PXE 사용 배포 지점의 레지스트리를 편집하여 **MACIgnoreListFile** 레지스트리 키를 만듭니다. PXE 사용 배포 지점 사이트 시스템 서버에 있는 텍스트 파일의 전체 경로에 대한 문자열 값을 추가합니다. 다음 레지스트리 경로를 사용하십시오.  

    `HKLM\Software\Microsoft\SMS\DP`  

    > [!WARNING]  
    > 레지스트리 편집기를 잘못 사용하면 Windows를 다시 설치해야 할 수 있는 심각한 문제가 발생할 수 있습니다. 레지스트리 편집기를 잘못 사용하여 발생하는 문제는 해결할 수 있다는 보장이 없습니다. 레지스트리 편집기 사용에 따른 결과는 사용자의 책임입니다.  

5. 이 레지스트리를 변경한 후 WDS 서비스 또는 PXE 응답기 서비스를 다시 시작합니다. 서버를 다시 시작할 필요가 없습니다.<!--512129-->  



## <a name="BKMK_RamDiskTFTP"></a> RamDisk TFTP 블록 크기 및 창 크기

PXE 사용 배포 지점의 RamDisk TFTP 블록 및 창 크기를 사용자 지정할 수 있습니다. 네트워크를 사용자 지정한 경우 블록 또는 창 크기가 너무 커서 시간 초과 오류로 부팅 이미지 다운로드가 실패할 수 있습니다. RamDisk TFTP 블록 및 창 크기 사용자 지정을 통해 PXE를 사용하여 특정 네트워크 요구 사항을 충족하는 경우 TFTP 트래픽을 최적화할 수 있습니다. 가장 효율적인 구성을 결정하기 위해 환경에서 사용자 지정된 설정을 테스트합니다. 자세한 내용은 [PXE 사용 배포 지점에서 RamDisk TFTP 블록 크기 및 창 크기 사용자 지정](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_RamDiskTFTP)을 참조하세요.



## <a name="configure-deployment-settings"></a>배포 설정 구성

PXE 시작 OS 배포를 사용하려면 해당 OS를 PXE 부팅 요청에 사용할 수 있도록 배포를 구성합니다. 배포 속성의 **배포 설정** 탭에서 사용 가능한 운영 체제를 구성합니다. **다음에 사용 가능하도록 설정** 설정에 대해 다음 옵션 중 하나를 선택합니다.

- Configuration Manager 클라이언트, 미디어 및 PXE

- 미디어 및 PXE만

- 미디어 및 PXE만(숨김)



## <a name="BKMK_Deploy"></a> 작업 순서 배포

대상 컬렉션에 OS를 배포합니다. 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/deploy-a-task-sequence)항목을 참조하세요. PXE를 사용하여 운영 체제를 배포할 경우 배포를 필수 또는 사용 가능으로 구성할 수 있습니다.

- **필수 배포**: 필수 배포에서는 사용자 작업 없이 PXE를 사용합니다. 사용자는 PXE 부트를 무시할 수 없습니다. 그러나 배포 지점에서 응답하기 전에 사용자가 PXE 부트를 취소하면 OS는 배포되지 않습니다.

- **사용 가능한 배포**: 사용 가능한 배포를 활용하려면 사용자가 대상 컴퓨터 앞에 있어야 합니다. 사용자는 **F12** 키를 눌러 PXE 부트 프로세스를 계속 진행해야 합니다. 사용자가 **F12** 키를 누르지 못할 경우 컴퓨터는 현재 OS로 부팅하거나 사용 가능한 다음 부팅 디바이스에서 부팅합니다.

Configuration Manager 컬렉션 또는 컴퓨터에 할당된 마지막 PXE 배포의 상태를 지우면 필수 PXE 배포를 재배포할 수 있습니다. **필수 PXE 배포 지우기** 작업에 대한 자세한 내용은 [클라이언트 관리](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode) 또는 [컬렉션 관리](/sccm/core/clients/manage/collections/manage-collections#how-to-manage-device-collections)를 참조하세요. 이 작업은 해당 배포의 상태를 다시 설정하고 가장 최근의 필수 배포를 다시 설치합니다.

> [!IMPORTANT]  
> PXE 프로토콜은 안전하지 않습니다. PXE 서버 및 PXE 클라이언트는 사이트에 대한 무단 액세스를 방지하기 위해 데이터 센터 내부와 같은 물리적으로 안전한 네트워크에 있는지 확인합니다.



## <a name="how-the-boot-image-is-selected-for-pxe"></a>PXE에 대한 부팅 이미지를 선택하는 방법

클라이언트가 PXE를 사용하여 부팅하는 경우 Configuration Manager에서 사용할 부팅 이미지를 클라이언트에 제공합니다. Configuration Manager는 아키텍처가 정확히 일치하는 부팅 이미지를 사용합니다. 아키텍처가 정확히 일치하는 부팅 이미지를 사용할 수 없는 경우 Configuration Manager는 아키텍처가 호환되는 부팅 이미지를 사용합니다.

다음 목록에서는 PXE를 사용하여 부팅하는 클라이언트에 대해 부팅 이미지가 선택되는 방식에 대한 세부 정보를 제공합니다.  

1. Configuration Manager는 사이트 데이터베이스에서 부팅하려는 클라이언트의 MAC 주소 또는 SMBIOS와 일치하는 시스템 레코드를 찾습니다.  

    > [!NOTE]  
    > 특정 사이트에 할당된 컴퓨터가 다른 사이트용 PXE로 부팅되는 경우에는 해당 컴퓨터에 대해 정책이 표시되지 않습니다. 예를 들어 클라이언트가 사이트 A에 이미 할당되어 있으면 사이트 B의 관리 지점 및 배포 지점에서는 사이트 A의 정책에 액세스할 수 없으며 클라이언트는 정상적으로 PXE 부팅되지 않습니다.  

2. Configuration Manager는 1단계에서 찾은 시스템 레코드에 배포되는 작업 순서를 찾습니다.  

3. 2단계에서 찾은 작업 순서 목록에서 Configuration Manager는 부팅하려는 클라이언트의 아키텍처와 일치하는 부팅 이미지를 찾습니다. 동일한 아키텍처를 가진 부팅 이미지가 있으면 해당 부팅 이미지가 사용됩니다.  

    둘 이상의 부팅 이미지를 찾으면 *가장 높거나* 가장 최신의 배포 ID를 사용합니다. 다중 사이트 계층 구조의 경우 *더 높은* 문자 사이트가 문자열 비교에서 우선권이 있습니다. 예를 들어, 둘 다 일치하는 경우 사이트 ZZZ의 1년된 배포가 사이트 AAA의 어제 배포보다 먼저 선택됩니다.<!-- SCCMDocs issue 877 -->  

4. 동일한 아키텍처를 가진 부팅 이미지가 없으면 Configuration Manager는 클라이언트의 아키텍처와 호환되는 부팅 이미지를 찾습니다. 즉, 2단계에서 찾은 작업 순서 목록에서 찾습니다. 예를 들어, 64비트 BIOS/MBR 클라이언트는 32비트 및 64비트 부팅 이미지와 호환됩니다. 32비트 BIOS/MBR 클라이언트는 32비트 부팅 이미지와만 호환됩니다. UEFI 클라이언트는 일치하는 아키텍처와만 호환됩니다. 64비트 UEFI 클라이언트는 64비트 부팅 이미지와 호환되고, 32비트 UEFI 클라이언트는 32비트 부팅 이미지와만 호환됩니다.
