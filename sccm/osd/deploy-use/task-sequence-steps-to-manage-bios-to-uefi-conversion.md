---
title: BIOS-UEFI 변환을 관리하는 작업 순서 단계
titleSuffix: Configuration Manager
description: UEFI로 전환하기 위해 FAT32 파티션을 준비하는 운영 체제 배포 작업 순서를 사용자 지정하는 방법을 알아봅니다.
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bd1181bd14779a6ac659927979185aa174203206
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53420178"
---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>BIOS-UEFI 변환을 관리하는 작업 순서 단계
Windows 10에서는 UEFI 사용 디바이스가 필요한 많은 새로운 보안 기능을 제공합니다. UEFI를 지원하지만 레거시 BIOS를 사용하는 최신 Windows PC가 있을 수 있습니다. 디바이스를 UEFI로 변환하려면 각 PC로 이동하여 하드 디스크를 다시 분할하고 펌웨어를 다시 구성해야 했습니다. Configuration Manager에서 작업 순서를 사용하여 하드 드라이브를 BIOS에서 UEFI로 변환할 준비를 하고, 현재 위치 업그레이드 프로세스의 일부로 BIOS에서 UEFI로 변환하고, 하드웨어 인벤토리의 일부로 UEFI 정보를 수집할 수 있습니다.

## <a name="hardware-inventory-collects-uefi-information"></a>하드웨어 인벤토리를 통해 UEFI 정보 수집
버전 1702부터 새 하드웨어 인벤토리 클래스(**SMS_Firmware**) 및 속성(**UEFI**)을 사용하여 컴퓨터를 UEFI 모드에서 시작할지 결정할 수 있습니다. 컴퓨터를 UEFI 모드로 시작하는 경우 **UEFI** 속성을 **TRUE**로 설정합니다. 하드웨어 인벤토리에서 기본적으로 사용됩니다. 하드웨어 인벤토리에 대한 자세한 내용은 [하드웨어 인벤토리를 구성하는 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.

## <a name="create-a-custom-task-sequence-to-prepare-the-hard-drive-for-bios-to-uefi-conversion"></a>사용자 지정 작업 순서를 만들어 하드웨어를 BIOS에서 UEFI로 변환하도록 준비
Configuration Manager 버전 1610부터 이제 새로운 변수인 TSUEFIDrive를 사용하여 운영 체제 배포 작업 순서를 사용자 지정하여 UEFI로 전환하기 위해 **컴퓨터 다시 시작** 단계에서 하드 드라이브의 FAT32 파티션을 준비하도록 할 수 있습니다. 다음 절차는 BIOS-UEFI 변환을 위해 하드 드라이브를 준비하기 위한 작업 순서 단계를 만드는 방법의 예를 제공합니다.

### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>UEFI로 변환하기 위해 FAT32 파티션을 준비하려면:
운영 체제를 설치하는 기존 작업 순서에서 BIOS-UEFI 변환을 수행하는 단계가 포함된 새 그룹을 추가합니다.

1. 파일 및 설정을 캡처하는 단계와 운영 체제 단계 사이에 새 작업 순서 그룹을 만듭니다. 예를 들어 **파일 및 설정 캡처**라는 그룹 뒤에 **BIOS-UEFI**라는 그룹을 만듭니다.
2. 새 그룹의 **옵션** 탭에서 새 작업 순서 변수를 **_SMSTSBootUEFI**가 **true**와 **같지 않음**인 조건으로 추가합니다. 이렇게 하면 컴퓨터가 이미 UEFI 모드에서 실행 중인 경우 이 그룹의 단계가 실행되지 않습니다.

   ![BIOS-UEFI 그룹](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. 새 그룹 아래에 **컴퓨터 다시 시작** 작업 순서 단계를 추가합니다. **다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.** 에서 **이 작업 순서에 할당된 부팅 이미지**를 선택하여 Windows PE에서 컴퓨터를 시작합니다.  
4. **옵션** 탭에서 작업 순서 변수를 **_SMSTSInWinPE = false**인 조건으로 추가합니다. 이렇게 하면 컴퓨터가 이미 Windows PE에서 실행 중인 경우 이 단계가 실행되지 않습니다.

   ![컴퓨터 다시 시작 단계](../../core/get-started/media/restart-in-windows-pe.png)
5. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구를 시작하는 단계를 추가합니다. 이 단계는 일반적으로 명령줄을 사용하여 OEM 도구를 시작하는 **명령줄 실행** 작업 순서 단계가 됩니다.
6. 하드 드라이브의 파티션을 나누고 포맷하는 디스크 포맷 및 파티션 만들기 작업 순서 단계를 추가합니다. 이 단계에서 다음을 수행합니다.
   1. 운영 체제를 설치하기 전에 UEFI로 변환하는 FAT32 파티션을 만듭니다. **디스크 유형**에 대해 **GPT**를 선택합니다.
    ![디스크 포맷 및 파티션 만들기 단계](../media/format-and-partition-disk.png)
   2. FAT32 파티션의 속성으로 이동합니다. **변수** 필드에 **TSUEFIDrive**를 입력합니다. 작업 순서에서 이 변수를 발견하면 컴퓨터를 다시 시작하기 전에 UEFI 변환을 준비합니다.
    ![파티션 속성](../../core/get-started/media/partition-properties.png)
   3. 작업 순서 엔진이 상태를 저장하고 로그 파일을 저장하는 데 사용할 NTFS 파티션을 만듭니다.
7. **컴퓨터 다시 시작** 작업 순서 단계를 추가합니다. **다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.** 에서 **이 작업 순서에 할당된 부팅 이미지**를 선택하여 Windows PE에서 컴퓨터를 시작합니다.  

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환
Windows 10 크리에이터 업데이트에서는 UEFI 사용 하드웨어에 맞게 하드 디스크를 다시 분할하는 프로세스를 자동화하는 간단한 변환 도구를 소개하고 Windows 7에서 Windows 10으로의 현재 위치 업그레이드 프로세스에 변환 도구를 통합합니다. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구 및 운영 체제 업그레이드 작업 순서와 이 도구를 결합하면 Windows 10 크리에이터 업데이트로의 현재 위치 업그레이드 중에 BIOS에서 UEFI로 컴퓨터를 변환할 수 있습니다.

**요구 사항**:
- Windows 10 크리에이터 업데이트
- UEFI를 지원하는 컴퓨터
- 컴퓨터의 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구

### <a name="to-convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환하려면
1. Windows 10 크리에이터 업데이트로의 현재 위치 업그레이드를 수행하는 운영 체제 업그레이드 작업 순서를 만듭니다.
2. 작업 순서를 편집합니다. **사후 처리 그룹**에서 다음 작업 순서 단계를 추가합니다.
   1. [일반]에서 **명령줄 실행** 단계를 추가합니다. 디스크에서 데이터를 수정하거나 삭제하지 않고 MBR에서 GPT로 디스크를 변환하는 MBR2GPT 도구에 대한 명령줄 도구를 추가합니다. 명령줄에서 다음을 입력합니다.  **MBR2GPT /convert /disk:0 /AllowFullOS**. 전체 운영 체제가 아닌 Windows PE에 있을 때 MBR2GPT.EXE 도구를 실행할 수도 있습니다. 이 작업을 수행하려면 MBR2GPT.EXE 도구를 실행하는 단계 전에 컴퓨터를 WinPE로 다시 시작하는 단계를 추가하고 명령줄에서 /AllowFullOS 옵션을 제거합니다. 도구 및 사용 가능한 옵션에 대한 자세한 내용은 [MBR2GPT.EXE](https://technet.microsoft.com/itpro/windows/deploy/mbr-to-gpt)를 참조하세요.
   2. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구를 시작하는 단계를 추가합니다. 이 단계는 일반적으로 명령줄을 사용하여 OEM 도구를 시작하는 명령줄 실행 작업 순서 단계가 됩니다.
   3. [일반]에서 **컴퓨터 다시 시작** 단계를 추가합니다. [다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.]에서 **현재 설치된 기본 운영 체제**를 선택합니다.
3. 작업 순서를 배포합니다.
