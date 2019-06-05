---
title: OS 이미지 관리
titleSuffix: Configuration Manager
description: WIM(Windows 이미지) 파일에 저장된 OS 이미지를 관리하는 방법을 알아봅니다.
ms.date: 05/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: fab13949-371c-4a4c-978e-471db1e54966
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35670ea78c2883d232040da30898f753c88e39b1
ms.sourcegitcommit: 18a94eb78043cb565b05cd0e9469b939b29cccf0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355095"
---
# <a name="manage-os-images-with-configuration-manager"></a>Configuration Manager를 사용하여 OS 이미지 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 OS 이미지는 WIM(Windows 이미지) 파일 형식으로 저장됩니다. 이러한 이미지는 컴퓨터에 새 OS를 설치하고 구성하는 데 사용하는 참조 파일 및 폴더의 압축된 컬렉션입니다. 많은 OS 배포 시나리오에는 OS 이미지가 필요합니다.


## <a name="os-image-types"></a>OS 이미지 유형

[기본 OS 이미지](#default-image)를 사용하거나 구성한 [참조 컴퓨터](#bkmk_capture)에서 OS 이미지를 빌드할 수 있습니다. 참조 컴퓨터를 빌드할 때 OS 파일, 드라이버, 지원 파일, 소프트웨어 업데이트, 도구 및 애플리케이션을 OS에 추가합니다. 그런 다음, 캡처하여 이미지 파일을 만들 수 있습니다.

### <a name="default-image"></a>기본 이미지

Windows 설치 파일에는 기본 OS 이미지가 포함됩니다. 이 이미지는 표준 드라이버 세트를 포함하는 기본 OS 이미지입니다. 기본 OS 이미지를 사용하면 작업 순서 단계를 사용하여 앱을 설치하고, 디바이스에 OS가 설치된 후 다른 구성 작업을 수행합니다. Windows 원본 파일에서 기본 OS 이미지를 찾습니다. `\Sources\install.wim`  

#### <a name="default-image-advantages"></a>기본 이미지 장점

- 이미지 크기는 캡처된 이미지보다 작습니다.  

- 작업 순서 단계를 통한 앱 설치 및 구성이 더 동적입니다. 예를 들어, 디바이스에 이미지를 다시 설치하지 않고도 작업 순서에서 설치하는 구성 및 앱을 변경합니다.  

#### <a name="default-image-disadvantages"></a>기본 이미지 단점

- OS 설치에 더 많은 시간이 걸릴 수 있습니다. 애플리케이션 설치 및 기타 구성이 OS 설치가 완료된 후 발생합니다.  


### <a name="bkmk_capture"></a> 참조 컴퓨터에서 캡처된 이미지

사용자 지정된 OS 이미지를 만들려면 원하는 OS를 사용하여 참조 컴퓨터를 빌드합니다. 그런 다음, 애플리케이션을 설치하고 설정을 구성합니다. 참조 컴퓨터에서 OS 이미지를 캡처하여 WIM 파일을 만듭니다. 참조 컴퓨터를 수동으로 빌드하거나 작업 순서를 사용하여 빌드 단계의 일부 또는 전체를 자동화할 수 있습니다. 자세한 내용은 [OS 이미지 사용자 지정](/sccm/osd/get-started/customize-operating-system-images)을 참조하세요.  

#### <a name="captured-image-advantages"></a>캡처된 이미지 장점

- 기본 이미지를 사용하는 것보다 빠르게 설치할 수 있습니다. 예를 들어 캡처된 OS 이미지를 사용하여 애플리케이션을 미리 설치할 수 있습니다. 그러면 나중에 작업 순서 단계를 사용하여 이러한 동일한 애플리케이션을 설치할 필요가 없습니다.  

#### <a name="captured-image-disadvantages"></a>캡처된 이미지 단점

- 이미지 크기가 기본 이미지보다 더 클 수 있습니다.  

- 애플리케이션 및 도구에 대한 업데이트가 필요할 경우 새 이미지를 만들어야 합니다.  


## <a name="BKMK_AddOSImages"></a> OS 이미지 추가  

OS 이미지를 사용하려면 Configuration Manager 사이트에 추가합니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장한 다음, **운영 체제 이미지** 노드를 선택합니다.  

2. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **운영 체제 이미지 추가**를 선택합니다. 이 작업으로 운영 체제 이미지 추가 마법사가 시작됩니다.  

3. **데이터 원본** 페이지에서 다음 정보를 지정합니다.

    - OS 이미지 파일에 대한 네트워크 **경로**. 예: `\\server\share\path\image.wim`

    - **지정된 WIM 파일에서 특정 이미지 인덱스를 추출**한 다음, 목록에서 이미지 인덱스를 선택합니다.<!--3719699--> 버전 1902부터 이 옵션은 파일의 모든 이미지 인덱스가 아닌 단일 인덱스를 자동으로 가져옵니다. 이 옵션을 사용하면 이미지 파일이 작아지고 오프라인 서비스가 빨라집니다. 소프트웨어 업데이트를 적용한 후 작은 이미지 파일에 대해 [이미지 서비스 최적화](#bkmk_resetbase)를 위한 프로세스도 지원합니다.  

        > [!Note]  
        > Configuration Manager는 원본 이미지 파일을 수정하지 않습니다. 동일한 원본 디렉터리에서 새 이미지 파일을 만듭니다.
        >
        > 이 추출 프로세스는 매우 큰 이미지 파일(예: 60GB 초과)의 경우 실패할 수 있습니다. DISM 오류는 `Not enough storage is available to process this command.`입니다. Configuration Manager가 사용하는 명령줄은 smsprov.log 및 dism.log에 있습니다. 동일한 명령을 수동으로 실행한 다음, 이미지를 가져옵니다.<!-- SCCMDocs-pr issue 3502 -->  

4. **일반** 페이지에서 다음 정보를 지정합니다. 이 정보는 OS 이미지가 여러 개인 경우 목적을 식별하는 데 유용합니다.  

    - **이름**: 이미지에 대한 고유 이름입니다. 기본적으로 이름은 WIM 파일 이름을 사용합니다.  

    - **버전**: 선택적 버전 식별자입니다. 이 속성은 이미지의 OS 버전이 아니어도 됩니다. 패키지에 대한 조직의 버전인 경우가 많습니다.  

    - **주석**: 선택적 간략한 설명입니다.  

5. 마법사를 완료합니다.  

이 콘솔 마법사와 동등한 PowerShell cmdlet의 경우, [New-CMOperatingSystemImage](https://docs.microsoft.com/powershell/module/configurationmanager/new-cmoperatingsystemimage?view=sccm-ps)를 참조하세요.

다음으로, 배포 지점에 OS 이미지를 배포합니다.  


## <a name="BKMK_DistributeBootImages"></a> 배포 지점에 콘텐츠 배포  

다른 콘텐츠와 동일한 배포 지점에 OS 이미지를 배포합니다. 작업 순서를 배포하기 전에 OS 이미지를 하나 이상의 배포 지점에 배포합니다. 자세한 내용은 [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.  


[!INCLUDE [Apply software updates to an image](includes/wim-apply-updates.md)]


## <a name="BKMK_OSImageMulticast"></a> 멀티캐스트 배포를 위한 OS 이미지 준비  

멀티캐스트 배포를 사용하면 여러 컴퓨터에서 동시에 OS 이미지를 다운로드할 수 있습니다. 각 클라이언트가 개별 연결을 통해 배포 지점에서 이미지 복사본을 다운로드하는 대신 배포 지점에서 이미지를 클라이언트에 멀티캐스트합니다. OS 배포 방법을 선택하면 [네트워크를 통해 Windows를 배포하는 멀티캐스트를 사용](/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)하여 멀티캐스트를 지원하도록 OS 이미지를 구성합니다. 그런 다음, 멀티캐스트 사용 배포 지점에 이미지를 배포합니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장한 다음, **운영 체제 이미지** 노드를 선택합니다.  

2. 멀티캐스트를 지원하는 배포 지점에 배포할 OS 이미지를 선택합니다.  

3. 리본의 **홈** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

4. **배포 설정** 탭으로 전환하고 다음 옵션을 구성합니다.  

    - **멀티캐스트를 통해 이 패키지 전송(WinPE만 해당)** : Configuration Manager에서 멀티캐스트를 사용하여 OS 이미지를 동시에 배포하도록 하려면 이 옵션을 선택합니다.  

    - **멀티캐스트 패키지 암호화**: 배포 지점에 전송하기 전에 사이트에서 이미지를 암호화할지 여부를 지정합니다. 이미지에 중요한 정보가 포함된 경우 이 옵션을 사용합니다. 이미지가 암호화되지 않으면 해당 콘텐츠가 네트워크에서 일반 텍스트로 표시됩니다. 그러면 권한 없는 사용자가 이미지 콘텐츠를 가로채어 볼 수 있습니다.  

    - **멀티캐스트를 통해서만 이 패키지 전송**: 배포 지점에서 멀티캐스트 세션 동안만 이미지를 배포할지 여부를 지정합니다.  

         **멀티캐스트를 통해서만 이 패키지 전송**을 선택하는 경우 작업 순서 배포 옵션을 **실행 중인 작업 순서에 따라 필요 시 로컬로 콘텐츠 다운로드**로 지정해야 합니다. 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/deploy-a-task-sequence)항목을 참조하세요.  

5. **확인**을 선택하여 설정을 저장하고 이미지 속성을 닫습니다.  
