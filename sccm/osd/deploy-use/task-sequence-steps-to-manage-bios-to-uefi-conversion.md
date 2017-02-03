---
title: "BIOS-UEFI 변환을 관리하는 작업 순서 단계 | Configuration Manager"
description: "UEFI로 전환하기 위해 FAT32 파티션을 준비하는 운영 체제 배포 작업 순서를 사용자 지정하는 방법을 알아봅니다."
ms.custom: na
ms.date: 11/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: c92d88517b4e1d54add489a53cd34b0f23be0c4c
ms.openlocfilehash: 04951b3ed50206941850ddcc893fcf9c9596f89f


---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>BIOS-UEFI 변환을 관리하는 작업 순서 단계
Configuration Manager 버전 1610부터 이제 새로운 변수인 TSUEFIDrive를 사용하여 운영 체제 배포 작업 순서를 사용자 지정하여 UEFI로 전환하기 위해 **컴퓨터 다시 시작** 단계에서 하드 드라이브의 FAT32 파티션을 준비하도록 할 수 있습니다. 다음 절차는 BIOS-UEFI 변환을 위해 하드 드라이브를 준비하기 위한 작업 순서 단계를 만드는 방법의 예를 제공합니다.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>UEFI로 변환하기 위해 FAT32 파티션을 준비하려면:
운영 체제를 설치하는 기존 작업 순서에서 BIOS-UEFI 변환을 수행하는 단계가 포함된 새 그룹을 추가합니다.

1. 파일 및 설정을 캡처하는 단계와 운영 체제 단계 사이에 새 작업 순서 그룹을 만듭니다. 예를 들어 **파일 및 설정 캡처**라는 그룹 뒤에 **BIOS-UEFI**라는 그룹을 만듭니다.
2. 새 그룹의 **옵션** 탭에서 새 작업 순서 변수를 **_SMSTSBootUEFI**가 **true**와 **같지 않음**인 조건으로 추가합니다. 이렇게 하면 컴퓨터가 이미 UEFI 모드에서 실행 중인 경우 이 그룹의 단계가 실행되지 않습니다.

   ![BIOS-UEFI 그룹](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. 새 그룹 아래에 **컴퓨터 다시 시작** 작업 순서 단계를 추가합니다. **다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.**에서 **이 작업 순서에 할당된 부팅 이미지**를 선택하여 Windows PE에서 컴퓨터를 시작합니다.  
4. **옵션** 탭에서 작업 순서 변수를 **_SMSTSInWinPE = false**인 조건으로 추가합니다. 이렇게 하면 컴퓨터가 이미 Windows PE에서 실행 중인 경우 이 단계가 실행되지 않습니다.

    ![컴퓨터 다시 시작 단계](../../core/get-started/media/restart-in-windows-pe.png)
5. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구를 시작하는 단계를 추가합니다. 이 단계는 일반적으로 명령줄을 사용하여 OEM 도구를 시작하는 **명령줄 실행** 작업 순서 단계가 됩니다.
6.  하드 드라이브의 파티션을 나누고 포맷하는 디스크 포맷 및 파티션 만들기 작업 순서 단계를 추가합니다. 이 단계에서 다음을 수행합니다.
    1.  운영 체제를 설치하기 전에 UEFI로 변환하는 FAT32 파티션을 만듭니다. **디스크 유형**에 대해 **GPT**를 선택합니다.

       ![디스크 포맷 및 파티션 만들기 단계](../media/format-and-partition-disk.png)
    2.  FAT32 파티션의 속성으로 이동합니다. **변수** 필드에 **TSUEFIDrive**를 입력합니다. 작업 순서에서 이 변수를 발견하면 컴퓨터를 다시 시작하기 전에 UEFI 변환을 준비합니다.

       ![파티션 속성](../../core/get-started/media/partition-properties.png)
    3. 작업 순서 엔진이 상태를 저장하고 로그 파일을 저장하는 데 사용할 NTFS 파티션을 만듭니다.
7.  **컴퓨터 다시 시작** 작업 순서 단계를 추가합니다. **다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.**에서 **이 작업 순서에 할당된 부팅 이미지**를 선택하여 Windows PE에서 컴퓨터를 시작합니다.  



<!--HONumber=Jan17_HO1-->


