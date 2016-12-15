---
title: "System Center Configuration Manager에서 독립 실행형 미디어 만들기 | Microsoft 문서"
description: "독립 실행형 미디어를 사용하여 Configuration Manager 사이트나 네트워크에 연결하지 않고 컴퓨터에 운영 체제를 배포합니다."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
caps.latest.revision: 21
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 06ade037c580d64503e6b8b5c3bf31004ab0650b
ms.openlocfilehash: b566c101b58774805a6ff103fd0c9ad16603ed34


---
# <a name="create-stand-alone-media-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 독립 실행형 미디어 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 독립 실행형 미디어에는 Configuration Manager 사이트에 연결하거나 네트워크를 사용하지 않고 컴퓨터에 운영 체제를 배포하는 데 필요한 모든 항목이 포함됩니다. 독립 실행형 미디어는 다음과 같은 운영 체제 배포 시나리오에서 사용합니다.  

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

-   [최신 버전으로 Windows 업그레이드](upgrade-windows-to-the-latest-version.md)  

 독립 실행형 미디어에는 운영 체제와 부팅 이미지, 운영 체제 이미지, 장치 드라이버 등의 다른 모든 필수 콘텐츠를 설치하는 단계를 자동화하는 작업 순서가 포함됩니다. 독립 실행형 미디어에는 운영 체제 배포에 필요한 모든 항목이 저장되므로 이 미디어에 필요한 디스크 공간은 다른 미디어 유형에 필요한 디스크 공간보다 훨씬 더 큽니다. 중앙 관리 사이트에서 독립 실행형 미디어를 만들 때 클라이언트가 Active Directory에서 할당된 사이트 코드를 검색합니다. 자식 사이트에 생성된 독립 실행형 미디어에서 자동으로 해당 사이트의 사이트 코드를 클라이언트에 할당합니다.  

##  <a name="a-namebkmkcreatestandalonemediaa-create-stand-alone-media"></a><a name="BKMK_CreateStandAloneMedia"></a> 독립 실행형 미디어 만들기  
 작업 순서 미디어 만들기 마법사를 사용하여 독립 실행형 미디어를 만들기 전에 다음 조건을 충족해야 합니다.  

### <a name="create-a-task-sequence-to-deploy-an-operating-system"></a>운영 체제를 배포하는 작업 순서 만들기
독립 실행형 미디어의 일부로 운영 체제를 배포하는 작업 순서를 지정해야 합니다. 새 작업 순서를 만드는 단계는 [System Center Configuration Manager에서 운영 체제를 설치하는 작업 순서 만들기](create-a-task-sequence-to-install-an-operating-system.md)를 참조하세요.

다음 작업은 독립 실행형 미디어에 대해 지원되지 않습니다.
- 작업 순서의 드라이버 자동 적용 단계. 드라이버 카탈로그에서 장치 드라이버 자동 적용은 지원되지 않지만 Windows 설치 프로그램에서 지정된 드라이버 집합을 사용할 수 있도록 드라이버 패키지 적용 단계를 선택할 수 있습니다.
- 작업 순서의 패키지 콘텐츠 다운로드 단계. 독립 실행형 미디어에서는 관리 지점 정보가 제공되지 않으므로 콘텐츠 위치를 열거하려고 하면 단계가 실패합니다.
- 소프트웨어 업데이트 설치
- 운영 체제 배포 전에 소프트웨어를 설치합니다.
- 사용자를 대상 컴퓨터와 연결하여 사용자 장치 선호도 지원
- 동적 패키지는 패키지 설치 작업을 통해 설치됩니다.
- 동적 응용 프로그램은 응용 프로그램 설치 작업을 통해 설치됩니다.

운영 체제를 배포하는 작업 순서에 [패키지 설치](../../osd/understand/task-sequence-steps.md#BKMK_InstallPackage) 단계가 포함되어 있고 중앙 관리 사이트에서 독립 실행형 미디어를 만들면 오류가 발생할 수 있습니다. 중앙 관리 사이트에는 작업 순서를 실행하는 동안 소프트웨어 배포 에이전트를 사용하도록 설정하는 데 필요한 필수 클라이언트 구성 정책이 없습니다. CreateTsMedia.log 파일에 다음 오류가 나타날 수 있습니다.<br /><br /> "WMI 메서드 SMS_TaskSequencePackage.GetClientConfigPolicies가 실패했습니다(0x80041001)."<br /><br /> **패키지 설치** 단계가 포함된 독립 실행형 미디어를 사용할 경우 소프트웨어 배포 에이전트를 사용하도록 설정된 기본 사이트에 독립 실행형 미디어를 만들거나 작업 순서에서 [Windows 및 ConfigMgr 설치](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) 단계와 첫 번째 **패키지 설치** 단계 사이에 [명령줄 실행](../understand/task-sequence-steps.md#BKMK_RunCommandLine) 단계를 추가해야 합니다. **명령줄 실행** 단계에서는 WMIC 명령을 실행하여 첫 번째 패키지 설치 단계가 실행되기 전에 소프트웨어 배포 에이전트를 사용하도록 설정합니다. **명령줄 실행** 작업 순서 단계에서 다음을 사용할 수 있습니다.<br /><br />
```WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE
```

### Distribute all content associated with the task sequence
You must distribute all content that is required by the task sequence the  to at least one distribution point. This includes the boot image, operating system image, and other associated files. The wizard gathers the information from the distribution point when it creates the stand-alone media. You must have **Read** access rights to the content library on that distribution point.  For details, see [Distribute content referenced by a task sequence](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS).

### Prepare the removable USB drive
*For a removable USB drive:*

If you are going to use a removable USB drive, the USB  drive must be connected to the computer where the wizard is run and the USB drive must be detectable by Windows as a removal device. The wizard writes directly to the USB drive when it creates the media. Stand-alone media uses a FAT32 file system. You cannot create stand-alone media on a USB flash drive whose content contains a file over 4 GB in size.

### Create an output folder
*For a CD/DVD set:*

Before you run the Create Task Sequence Media Wizard to create media for a CD or DVD set, you must create a folder for the output files created by the wizard. Media that is created for a CD or DVD set is written as .iso files directly to the folder.


 Use the following procedure to create stand-alone media for a removable USB drive or a CD/DVD set.  

## To create stand-alone media  

1.  In the Configuration Manager console, click **Software Library**.  

2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Task Sequences**.  

3.  On the **Home** tab, in the **Create** group, click **Create Task Sequence Media** to start the Create Task Sequence Media Wizard.  

4.  On the **Select Media Type** page, specify the following options, and then click **Next**.  

    -   Select **Stand-alone media**.  

    -   Optionally, if you want to allow the operating system to be deployed without requiring user input, select **Allow unattended operating system deployment**. When you select this option the user is not prompted for network configuration information or for optional task sequences. However, the user is still prompted for a password if the media is configured for password protection.  

5.  On the **Media Type** page, specify whether the media is a flash drive or a CD/DVD set, and then click configure the following:  

    > [!IMPORTANT]  
    >  Stand-alone media uses a FAT32 file system. You cannot create stand-alone media on a USB flash drive whose content contains a file over 4 GB in size.  

    -   If you select **USB flash drive**, specify the drive where you want to store the content.  

    -   If you select **CD/DVD set**, specify the capacity of the media and the name and path of the output files. The wizard writes the output files to this location. For example: **\\\servername\folder\outputfile.iso**  

         If the capacity of the media is too small to store the entire content, multiple files are created and you must store the content on multiple CDs or DVDs. When multiple media is required, Configuration Manager adds a sequence number to the name of each output file that it creates. In addition, if you deploy an application along with the operating system and the application cannot fit on a single media, Configuration Manager stores the application across multiple media. When the stand-alone media is run, Configuration Manager prompts the user for the next media where the application is stored.  

        > [!IMPORTANT]  
        >  If you select an existing .iso image, the Task Sequence Media Wizard deletes that image from the drive or share as soon as you proceed to the next page of the wizard. The existing image is deleted, even if you then cancel the wizard.  

     Click **Next**.  

6.  On the **Security** page, enter a strong password to help protect the media, and then click **Next**. If you specify a password, the password is required to use the media.  

    > [!IMPORTANT]  
    >  On stand-alone media, only the task sequence steps and their variables are encrypted. The remaining content of the media is not encrypted, so do not include any sensitive information in task sequence scripts. Store and implement all sensitive information by using task sequence variables.  

7.  On the **Stand-Alone CD/DVD** page, specify the task sequence that deploys the operating system, and then click **Next**. The wizard lets you select only those task sequences that are associated with a boot image.  

8.  On the **Distribution Points** page, specify the distribution points that contain the content required by the task sequence, and then click **Next**.  

     Configuration Manager will only display distribution points that have the content. You must distribute all of the content associated with the task sequence (boot image, operating system image, etc.) to at least one distribution point before you can continue. After you distribute the content, you can either restart the wizard or remove any distribution points that you already selected  on this page, go to the previous page, and then back to the **Distribution Points** page to refresh the distribution point list. For more information about distributing content, see [Distribute content referenced by a task sequence](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS). For more information about distribution points and content management, see [Manage content and content infrastructure for System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    > [!NOTE]  
    >  You must have **Read** access rights to the content library on the distribution points.  

9. On the **Customization** page, specify the following information, and then click **Next**.  

    -   Specify the variables that the task sequence uses to deploy the operating system.  

    -   Specify any prestart commands that you want to run before the task sequence. Prestart commands are a script or an executable that can interact with the user in Windows PE before the task sequence runs to install the operating system. For more information about prestart commands for media, see [Prestart commands for task sequence media in System Center Configuration Manager](../understand/prestart-commands-for-task-sequence-media.md).  

         Optionally, select **Files for the prestart command** to include any required files for the prestart command.  

        > [!TIP]  
        >  During task sequence media creation, the task sequence writes the package ID and prestart command-line, including the value for any task sequence variables, to the CreateTSMedia.log log file on the computer that runs the Configuration Manager console. You can review this log file to verify the value for the task sequence variables.  

10. Complete the wizard.  

 The stand-alone media files (.iso) are created in the destination folder. If you selected **Stand-Alone CD/DVD**, you can now copy the output files to a set of CDs or DVDs.  

##  <a name="BKMK_StandAloneMediaTSExample"></a> Example task sequence for stand-alone media  
 Use the following table as a guide as you create a task sequence to deploy an operating system using stand-alone media. The table will help you decide the general sequence for your task sequence steps and how to organize and structure those task sequence steps into logical groups. The task sequence that you create might vary from this sample and can contain more or fewer task sequence steps and groups.  

> [!NOTE]  
>  You must always use the Task Sequence Media Wizard to create stand-alone media.  

|Task Sequence Group or Step|Description|  
|---------------------------------|-----------------|  
|Capture File and Settings - **(New Task Sequence Group)**|Create a task sequence group. A task sequence group keeps similar task sequence steps together for better organization and error control.|  
|Capture Windows Settings|Use this task sequence step to identify the Microsoft Windows settings that are captured from the existing operating system on the destination computer prior to reimaging. You can capture the computer name, user and organizational information, and the time zone settings.|  
|Capture Network Settings|Use this task sequence step to capture network settings from the computer that receives the task sequence. You can capture the domain or workgroup membership of the computer and the network adapter setting information.|  
|Capture User Files and Settings - **(New Task Sequence Sub-Group)**|Create a task sequence group within a task sequence group. This sub-group contains the steps needed to capture user state data from the existing operating system on the destination computer prior to reimaging. Similar to the initial group that you added, this sub-group keeps similar task sequence steps together for better organization and error control.|  
|Set Local State Location|Use this task sequence step to specify a local location using the protected path task sequence variable. The user state is stored on a protected directory on the hard drive.|  
|Capture User State|Use this task sequence step to capture the user files and settings you want to migrate to the new operating system.|  
|Install Operating System - **(New Task Sequence Group)**|Create another task sequence sub-group. This sub-group contains the steps needed to install the operating system.|  
|Reboot to Windows PE or hard disk|Use this task sequence step to specify restart options for the computer that receives this task sequence. This step will display a message to the user indicating that the computer will be restarted so that the installation can continue.<br /><br /> This step uses the read-only **_SMSTSInWinPE** task sequence variable. If the associated value equals **false** the task sequence step will continue.|  
|Apply Operating System|Use this task sequence step to install the operating system image onto the destination computer. This step deletes all files on that volume (with the exception of Configuration Manager-specific control files) and then applies all volume images contained in the WIM file to the corresponding sequential disk volume. You can also specify a **sysprep** answer file to configure which disk partition to use for the installation.|  
|Apply Windows Settings|Use this task sequence step to configure the Windows settings configuration information for the destination computer. The windows settings you can apply are user and organizational information, product or license key information, time zone, and the local administrator password.|  
|Apply Network Settings|Use this task sequence step to specify the network or workgroup configuration information for the destination computer. You can also specify if the computer uses a DHCP server or you can statically assign the IP address information.|  
|Apply Driver Package|Use this task sequence step to make all device drivers in a driver package available for use by Windows setup. All necessary device drivers must be contained on the stand-alone media.|  
|Setup Operating System - **(New Task Sequence Group)**|Create another task sequence sub-group. This sub-group contains the steps needed to install the Configuration Manager client.|  
|Setup Windows and ConfigMgr|Use this task sequence step to install the Configuration Manager client software. Configuration Manager installs and registers the Configuration Manager client GUID. You can assign the necessary installation parameters in the **Installation properties** window.|  
|Restore User Files and Settings - **(New Task Sequence Group)**|Create another task sequence sub-group. This sub-group contains the steps needed to restore the user state.|  
|Restore User State|Use this task sequence step to initiate the User State Migration Tool (USMT) to restore the user state and settings that were captured from the Capture User State Action to the destination computer.|  



<!--HONumber=Dec16_HO2-->


