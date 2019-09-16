---
title: 독립 실행형 미디어 만들기
titleSuffix: Configuration Manager
description: 독립 실행형 미디어를 사용하여 네트워크에 연결하지 않고 컴퓨터에 OS를 배포합니다.
ms.date: 05/02/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a00da1511c6410088f318fc619bbddc537e20708
ms.sourcegitcommit: 2db6863c6740380478a4a8beb74f03b8178280ba
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083260"
---
# <a name="create-stand-alone-media"></a>독립 실행형 미디어 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 독립 실행형 미디어에는 네트워크에 연결하지 않고 컴퓨터에 OS를 배포하는 데 필요한 모든 항목이 포함됩니다.

독립 실행형 미디어는 다음과 같은 OS 배포 시나리오에서 사용합니다.  

- [새 버전의 Windows로 기존 컴퓨터 새로 고침](/sccm/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)  

- [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](/sccm/osd/deploy-use/install-new-windows-version-new-computer-bare-metal)  

- [최신 버전으로 Windows 업그레이드](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)  


## <a name="usage"></a>사용

독립 실행형 미디어에는 OS와 기타 모든 필수 콘텐츠를 설치하는 단계를 자동화하는 작업 순서가 포함됩니다. 이 콘텐츠에는 부팅 이미지, OS 이미지 및 디바이스 드라이버가 포함됩니다. 독립 실행형 미디어에는 OS 배포에 필요한 모든 항목이 저장되기 때문에 다른 미디어 유형에 필요한 것보다 더 많은 디스크 공간이 필요합니다.

중앙 관리 사이트에서 독립 실행형 미디어를 만들 때 클라이언트가 Active Directory에서 할당된 사이트 코드를 검색합니다. 자식 사이트에 생성된 독립 실행형 미디어에서 자동으로 해당 사이트의 사이트 코드를 클라이언트에 할당합니다.  


## <a name="prerequisites"></a>필수 구성 요소

작업 순서 미디어 만들기 마법사를 사용하여 독립 실행형 미디어를 만들려면 먼저 다음 조건을 모두 충족해야 합니다.

### <a name="create-a-task-sequence-to-deploy-an-os"></a>OS를 배포하는 작업 순서 만들기

독립 실행형 미디어의 일부로 OS를 배포하는 작업 순서를 지정합니다. 자세한 내용은 [OS를 설치하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system)를 참조하세요.

#### <a name="unsupported-actions-for-stand-alone-media"></a>독립 실행형 미디어에 대해 지원되지 않는 작업

다음 작업은 독립 실행형 미디어에 대해 지원되지 않습니다.

- 작업 순서의 [드라이버 자동 적용](/sccm/osd/understand/task-sequence-steps#BKMK_AutoApplyDrivers) 단계. 독립 실행형 미디어는 드라이버 카탈로그의 디바이스 드라이버 자동 적용을 지원하지 않습니다. Windows 설치 프로그램에 지정된 드라이버 집합을 제공하려면 [드라이버 패키지 적용](/sccm/osd/understand/task-sequence-steps#BKMK_ApplyDriverPackage) 단계를 수행하세요.  

- 작업 순서의 [패키지 콘텐츠 다운로드](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent) 단계. 독립 실행형 미디어에서는 관리 지점 정보가 제공되지 않으므로 콘텐츠 위치를 열거하려고 하면 단계가 실패합니다.  

- 소프트웨어 업데이트 설치.  

- OS 배포 전에 소프트웨어 설치  

- 비 OS 배포에 대한 사용자 지정 작업 순서입니다.  

- 사용자를 대상 컴퓨터와 연결하여 사용자 디바이스 선호도 지원  

- 동적 패키지는 [패키지 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallPackage) 단계를 통해 설치됩니다.  

- 동적 애플리케이션은 [애플리케이션 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallApplication) 단계를 통해 설치됩니다.

- **Windows 및 ConfigMgr 설치** 작업 순서 단계의 **사용 가능한 경우 사전 프로덕션 클라이언트 패키지 사용** 설정. 이 설정에 대한 자세한 내용은 [Windows 및 ConfigMgr 설치](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr)를 참조하세요.  

> [!NOTE]  
> 작업 순서에 [패키지 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallPackage) 단계가 포함되어 있고 중앙 관리 사이트에서 독립 실행형 미디어를 만들면 오류가 발생할 수 있습니다. 중앙 관리 사이트에는 필요한 클라이언트 구성 정책이 없습니다. 이러한 정책은 작업 순서를 실행할 때 소프트웨어 배포 에이전트를 사용하도록 설정하는 데 필요합니다. **CreateTsMedia.log** 파일에 다음 오류가 나타날 수 있습니다.  
>
> `WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)`
>
> **패키지 설치** 단계가 포함된 독립 실행형 미디어의 경우 소프트웨어 배포 에이전트를 사용하도록 설정된 기본 사이트에서 독립 실행형 미디어를 만듭니다.
>
> 또는 사용자 지정 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계를 사용합니다. 또는 [Windows 및 ConfigMgr 설치](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr) 단계 뒤 및 첫 번째 **패키지 설치** 단계 앞에 추가합니다. **명령줄 실행** 단계에서는 다음 WMIC 명령을 실행하여 첫 번째 패키지 설치 단계 이전에 소프트웨어 배포 에이전트를 사용하도록 설정합니다.  
>
> `WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE`

### <a name="distribute-all-content-associated-with-the-task-sequence"></a>작업 순서와 관련된 모든 콘텐츠 배포

작업 순서에 필요한 모든 콘텐츠를 하나 이상의 배포 지점에 배포합니다. 이 콘텐츠에는 부팅 이미지, OS 이미지 및 관련된 기타 파일이 포함됩니다. 마법사는 미디어를 만들 때 배포 지점에서 콘텐츠를 수집합니다.

사용자 계정에는 해당 배포 지점의 콘텐츠 라이브러리에 대해 적어도 **읽기** 액세스 권한이 있어야 합니다. 자세한 내용은 [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.

### <a name="prepare-the-removable-usb-drive"></a>이동식 USB 드라이브 준비

이동식 USB 드라이브를 사용하는 경우 작업 순서 미디어 만들기 마법사를 실행할 컴퓨터에 연결합니다. 이 USB 드라이브는 Windows에서 이동식 디바이스로 검색되어야 합니다. 마법사는 USB 드라이브에 직접 기록하여 미디어를 만듭니다.

독립 실행형 미디어는 FAT32 파일 시스템을 사용합니다. 크기가 4GB 이상인 파일을 포함하는 이동식 USB 드라이브에 독립 실행형 미디어를 만들 수 없습니다.

### <a name="create-an-output-folder"></a>출력 폴더 만들기

작업 순서 미디어 만들기 마법사를 실행하여 CD 또는 DVD 세트에 미디어를 만들려면 생성할 출력 파일의 폴더를 만듭니다. CD 또는 DVD 세트용 미디어를 만드는 경우 해당 폴더에 .ISO 파일로 직접 기록됩니다.


## <a name="process"></a>프로세스

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장하고 **작업 순서** 노드를 선택합니다.  

2. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **작업 순서 미디어 만들기**를 선택합니다. 이 작업은 작업 순서 미디어 만들기 마법사를 시작합니다.  

3. **미디어 유형 선택** 페이지에서 다음 옵션을 지정합니다.  

    - **독립 실행형 미디어**를 선택합니다.  

    - 선택적으로, 사용자가 입력할 필요 없이 OS가 배포되도록 하려면 **운영 체제 자동 배포 허용**을 선택합니다.  

        > [!IMPORTANT]  
        > 이 옵션을 선택하는 경우 사용자에게 네트워크 구성 정보나 선택적 작업 순서에 대해 묻지 않습니다. 미디어 암호 보호를 구성한 경우 사용자가 암호를 입력해야 합니다.  

4. **미디어 유형** 페이지에서 미디어가 **이동식 USB 드라이브**인지, **CD/DVD 세트**인지 지정합니다. 그런 후 다음 옵션을 구성합니다.  

    > [!IMPORTANT]  
    > 미디어는 FAT32 파일 시스템을 사용합니다. 콘텐츠가 4GB 이상인 파일을 포함하는 USB 드라이브에는 독립 실행형 미디어를 만들 수 없습니다.  

    - **이동식 USB 드라이브**를 선택하는 경우 콘텐츠를 저장할 드라이브를 선택합니다.  

        - **이동식 USB 드라이브 포맷(FAT32) 및 부팅 가능하도록 구성**: 기본적으로 Configuration Manager가 USB 드라이브를 준비하도록 합니다. 많은 최신 UEFI 디바이스에 부팅 가능한 FAT32 파티션이 필요합니다. 그러나 이 포맷은 파일의 크기와 드라이브의 전체 용량도 제한합니다. 이동식 드라이브를 이미 포맷하고 구성한 경우에는 이 옵션을 사용하지 않도록 설정합니다.

    - **CD/DVD 세트**를 선택하는 경우 미디어 용량(**미디어 크기**) 및 출력 파일(**미디어 파일**)의 이름과 경로를 지정해야 합니다. 마법사에서 출력 파일을 이 위치에 기록합니다. `\\servername\folder\outputfile.iso`  

        미디어 용량이 부족하여 전체 콘텐츠를 저장하지 못하는 경우 여러 파일을 만듭니다. 그런 다음 여러 CD 또는 DVD에 콘텐츠를 저장해야 합니다. 여러 미디어 파일이 필요한 경우 Configuration Manager는 생성된 각 출력 파일의 이름에 일련 번호를 추가합니다.  

        애플리케이션과 함께 OS를 배포하는 경우 애플리케이션이 단일 미디어에 맞지 않는 경우 Configuration Manager는 여러 미디어를 사용하여 애플리케이션을 저장합니다. 독립 실행형 미디어가 실행되는 경우 Configuration Manager는 애플리케이션이 저장된 그다음 미디어를 삽입하라는 메시지를 표시합니다.  

        > [!IMPORTANT]  
        > 기존 .iso 이미지를 선택하는 경우 작업 순서 미디어 만들기 마법사는 다음 페이지로 진행된 후 바로 드라이브나 공유에서 해당 이미지를 삭제합니다. 기존 이미지는 이후에 마법사를 취소하는 경우라도 삭제됩니다.  

    - **준비 폴더**<!--1359388-->: 미디어 만들기 프로세스에는 임시 드라이브 공간이 많이 필요할 수 있습니다. 기본적으로 이 위치는 다음 경로 `%UserProfile%\AppData\Local\Temp`와 유사합니다. 버전 1902부터, 이러한 임시 파일의 저장 위치를 보다 유연하게 지정할 수 있도록 이 값을 다른 드라이브 및 경로로 변경할 수 있습니다.  

    - **미디어 레이블**<!--1359388-->: 버전 1902부터 작업 순서 미디어에 레이블을 추가합니다. 이 레이블을 통해 미디어를 만든 후 미디어를 보다 잘 식별할 수 있습니다. 기본값은 `Configuration Manager`입니다. 이 텍스트 필드는 다음 위치에 나타납니다.  

        - ISO 파일을 탑재하는 경우 Windows는 탑재된 드라이브의 이름으로 이 레이블을 표시합니다.  

        - USB 드라이브를 포맷하는 경우 해당 이름으로 레이블의 처음 11자를 사용합니다.  

        - Configuration Manager는 미디어의 루트에 `MediaLabel.txt`라는 텍스트 파일을 작성합니다. 기본적으로 파일은 텍스트: `label=Configuration Manager`의 한 줄을 포함합니다. 미디어에 대한 레이블을 사용자 지정하는 경우 이 줄은 기본값 대신 사용자 지정 레이블을 사용합니다.  

    - **미디어에 autorun.inf 파일 포함**<!-- 4090666 -->: 버전 1902부터 Configuration Manager는 기본적으로 autorun.inf 파일을 추가하지 않습니다. 이 파일은 일반적으로 맬웨어 방지 제품에서 차단됩니다. Windows의 자동 실행 기능에 대한 자세한 내용은 [자동 실행 가능한 CD-ROM 애플리케이션 만들기](https://docs.microsoft.com/windows/desktop/shell/autoplay)를 참조하세요. 시나리오에 여전히 필요한 경우 이 옵션을 선택하여 해당 파일을 포함합니다.  

5. **보안** 페이지에서 다음 옵션을 지정합니다.

    - **암호로 미디어 보호**: 강력한 암호를 입력하여 미디어의 무단 액세스를 방지합니다. 암호를 지정하면 사용자가 미디어를 사용하기 위해 암호를 입력해야 합니다.  

        > [!IMPORTANT]  
        > 미디어를 보호하기 위해 항상 암호를 지정하는 것이 좋습니다.  
        >
        > 독립 실행형 미디어에서는 작업 순서 단계 및 관련 변수만 암호화합니다. 미디어의 나머지 콘텐츠는 암호화하지 않습니다. 작업 순서 스크립트에 중요한 정보를 포함하지 마세요. 모든 중요 정보는 작업 순서 변수를 사용하여 저장 및 구현해야 합니다.  

    - **이 독립 실행형 미디어가 유효한 날짜 범위 선택**: 미디어에 대한 선택적 시작 및 만료 날짜를 설정합니다. 이 설정은 기본적으로 사용되지 않습니다. 독립 실행형 미디어를 실행하기 전에 날짜가 컴퓨터의 시스템 시간과 비교됩니다. 시스템 시간이 시작 시간보다 이전이거나 만료 시간보다 이후이면 독립 실행형 미디어가 시작되지 않습니다. [New-CMStandaloneMedia](https://docs.microsoft.com/powershell/module/configurationmanager/new-cmstandalonemedia?view=sccm-ps) PowerShell cmdlet을 사용하여 이러한 옵션을 사용할 수도 있습니다.  

6. **독립 실행형 CD/DVD** 페이지에서 OS를 배포하는 작업 순서를 선택합니다. 부팅 이미지와 연결된 해당 작업 순서만 선택할 수 있습니다. 작업 순서에서 참조되는 콘텐츠 목록을 확인합니다.  

    - **연결된 애플리케이션 종속성을 검색하고 이 미디어에 추가**: 애플리케이션 종속성에 대한 콘텐츠를 미디어에 추가합니다.  

        > [!TIP]  
        > 예상한 애플리케이션 종속성이 표시되지 않으면 이 옵션을 선택 취소한 후 다시 선택하여 목록을 새로 고칩니다.  

7. **애플리케이션 선택** 페이지에서 미디어 파일의 일부로 포함할 추가 애플리케이션 콘텐츠를 지정합니다.  

8. **패키지 선택** 페이지에서 미디어 파일의 일부로 포함할 추가 패키지 콘텐츠를 지정합니다.  

9. **드라이버 패키지 선택** 페이지에서 미디어 파일의 일부로 포함할 추가 드라이버 패키지 콘텐츠를 지정합니다.  

10. **배포 지점** 페이지에서 필요한 콘텐츠가 포함된 배포 지점을 지정합니다.  

    Configuration Manager는 콘텐츠가 있는 배포 지점만 표시합니다. 계속하기 전에 작업 순서와 연결된 모든 콘텐츠를 하나 이상의 배포 지점에 배포합니다. 콘텐츠를 배포한 후 배포 지점 목록을 새로 고칩니다. 이 페이지에서 이미 선택한 배포 지점을 모두 제거하고 이전 페이지로 이동한 후 **배포 지점** 페이지로 돌아갑니다. 또는 마법사를 다시 시작합니다. 자세한 내용은 [작업 순서에서 참조되는 콘텐츠 배포](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DistributeTS) 및 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  

11. **사용자 지정** 페이지에서 다음 옵션을 지정합니다.  

    - 작업 순서에서 사용하는 모든 변수를 추가합니다.  

    - **시작 전 명령 사용**: 작업 순서를 실행하기 전에 실행할 시작 전 명령을 지정합니다. 시작 전 명령은 작업 순서를 실행하기 전에 Windows PE의 사용자와 상호 작용할 수 있는 스크립트나 실행 파일입니다. 자세한 내용은 [작업 순서 미디어에 대한 시작 전 명령](/sccm/osd/understand/prestart-commands-for-task-sequence-media)을 참조하세요.  

        > [!TIP]  
        > 미디어를 만드는 동안 작업 순서는 Configuration Manager 콘솔을 실행하는 컴퓨터의 **CreateTSMedia.log** 파일에, 모든 작업 순서 변수의 값을 비롯하여 패키지 ID 및 시작 전 명령줄을 기록합니다. 이 로그 파일을 검토하여 작업 순서 변수의 값을 확인할 수 있습니다.  

        시작 전 명령에 콘텐츠가 필요한 경우 **시작 전 명령을 위한 파일 포함** 옵션을 선택합니다.  

12. 마법사를 완료합니다.  

독립 실행형 미디어 파일(.ISO)이 대상 폴더에 생성됩니다. **CD/DVD 세트**를 선택한 경우 CD 또는 DVD 세트에 출력 파일을 복사합니다.


## <a name="next-steps"></a>다음 단계

[독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](/sccm/osd/deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network)
