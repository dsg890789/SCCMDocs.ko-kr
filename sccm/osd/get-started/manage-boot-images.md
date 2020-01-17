---
title: 부팅 이미지 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 OS를 배포하는 동안 사용하는 Windows PE 부팅 이미지를 관리하는 방법을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9a2294502fe1550ef1f895544037c344a3a2f883
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821344"
---
# <a name="manage-boot-images-with-configuration-manager"></a>Configuration Manager를 사용하여 부팅 이미지 관리

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 부팅 이미지는 OS 배포 중에 사용되는 [WinPE(Windows PE)](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) 이미지입니다. 부팅 이미지는 WinPE에서 컴퓨터를 시작하는 데 사용됩니다. 이 최소 OS에는 제한된 구성 요소와 서비스가 포함되어 있습니다. Configuration Manager는 WinPE를 사용하여 Windows 설치용으로 대상 컴퓨터를 준비합니다.

## <a name="BKMK_BootImageDefault"></a> 기본 부팅 이미지

Configuration Manager에서 두 개의 기본 부팅 이미지 제공: x86 플랫폼을 지원하는 부팅 이미지와 x64 플랫폼을 지원하는 부팅 이미지의 두 가지 부팅 이미지를 제공합니다. 이러한 이미지는 사이트 서버의 공유 위치인 `\\<SiteServerName>\SMS_<sitecode>\osd\boot\`에 있는 *x64* 또는 *i386* 폴더에 저장됩니다. 기본 부팅 이미지는 수행하는 작업에 따라 업데이트되거나 다시 생성됩니다.

기본 부팅 이미지에 대해 설명된 작업 중 하나에 대한 다음과 같은 동작을 고려합니다.

- 원본 드라이버 개체는 유효해야 합니다. 이러한 개체는 드라이버 원본 파일을 포함합니다. 개체가 유효하지 않으면 사이트는 부팅 이미지에 드라이버를 추가하지 않습니다.  

- 같은 Windows PE 버전을 사용하더라도 기본 부팅 이미지를 기반으로 하지 않는 부팅 이미지는 수정되지 않습니다.  

- 수정된 부팅 이미지를 배포 지점에 다시 배포합니다.  

- 수정된 부팅 이미지를 사용하는 모든 미디어를 다시 만듭니다.  

- 사용자 지정된/기본 부팅 이미지를 자동으로 업데이트하지 않으려면 기본 위치에 저장하지 마세요.  

> [!NOTE]
> **CMTrace**(Configuration Manager 로그 도구)가 **소프트웨어 라이브러리**의 모든 부팅 이미지에 추가됩니다. Windows PE에 있는 경우 명령 프롬프트에서 `cmtrace`를 입력하여 도구를 시작합니다.
>
> CMTrace는 Windows PE의 로그 파일에 대 한 기본 뷰어입니다.

### <a name="use-updates-and-servicing-to-install-the-latest-version-of-configuration-manager"></a>업데이트 및 서비스를 사용하여 최신 버전의 Configuration Manager 설치

Windows ADK(Assessment and Deployment Kit) 버전을 업그레이드한 다음, 업데이트 및 설치를 사용하여 최신 버전의 Configuration Manager를 설치하면 사이트가 기본 부팅 이미지를 다시 생성합니다. 이 업데이트는 업데이트된 Windows ADK의 새 WinPE 버전, 새 Configuration Manager 클라이언트 버전, 드라이버 및 사용자 지정을 포함합니다. 사이트는 사용자 지정 부팅 이미지를 수정하지 않습니다.

### <a name="upgrade-from-configuration-manager-2012-to-current-branch"></a>Configuration Manager 2012에서 현재 분기로 업그레이드

Configuration Manager 2012를 현재 분기로 업그레이드하면 사이트에서 기본 부팅 이미지를 다시 생성합니다. 이 업데이트에는 업데이트된 Windows ADK의 새 WinPE 버전 및 새 Configuration Manager 클라이언트 버전이 포함됩니다. 모든 부팅 이미지 사용자 지정은 변경되지 않습니다. 사이트는 사용자 지정 부팅 이미지를 수정하지 않습니다.

### <a name="update-distribution-points-with-the-boot-image"></a>부팅 이미지를 사용하여 배포 지점 업데이트

콘솔의 **부팅 이미지** 노드에서 **배포 지점 업데이트** 작업을 사용하는 경우 사이트는 클라이언트 구성 요소, 드라이버 및 사용자 지정이 포함된 대상 부팅 이미지를 업데이트합니다.

Windows ADK 설치 디렉터리의 최신 버전 WinPE로 부팅 이미지를 다시 로드할 수 있습니다. 배포 지점 업데이트 마법사의 **일반** 페이지에서 다음 정보를 제공합니다.

- 사이트 서버에 설치된 현재 Windows ADK 버전
- 현재 프로덕션 클라이언트 버전
- 부팅 이미지의 WinPE의 Windows ADK 버전
- 부팅 이미지의 구성 관리자 클라이언트 버전

부팅 이미지의 버전이 오래된 경우 **Windows ADK의 현재 Windows PE 버전으로 이 부팅 이미지 다시 로드** 옵션을 사용합니다.

> [!Important]  
> 이 작업은 기본 부팅 이미지와 사용자 지정 부팅 이미지 둘 다에 사용할 수 있습니다. 부팅 이미지를 다시 로드하는 이 프로세스를 진행하는 동안에는 Configuration Manager 외부에서 수행되는 수동 사용자 지정 내용이 사이트에서 유지되지 않습니다. 이러한 사용자 지정에는 타사 확장이 포함됩니다. 이 옵션을 사용하면 WinPE의 최신 버전과 최신 클라이언트 버전을 사용하여 부팅 이미지를 다시 빌드합니다. 부팅 이미지 속성에 대해 지정된 구성만 다시 적용됩니다. <!--SCCMDocs issue #1283-->

**부팅 이미지** 노드에는 (**클라이언트 버전**)에 대한 새 열도 포함됩니다. 이 열을 사용하여 각 부팅 이미지에서 Configuration Manager 클라이언트 버전을 신속하게 확인합니다.

## <a name="BKMK_BootImageCustom"></a> 부팅 이미지 사용자 지정  

부팅 이미지가 Windows ADK의 지원되는 버전에서 WinPE 버전을 기반으로 하는 경우 콘솔에서 [부팅 이미지를 수정](#BKMK_ModifyBootImages)하거나 사용자 지정할 수 있습니다. 사이트를 업그레이드하고 Windows ADK의 새 버전을 설치하는 경우 사용자 지정 부팅 이미지가 Windows ADK의 새 버전을 사용하여 업데이트되지 않습니다. 이 경우, Configuration Manager 콘솔에서 부팅 이미지를 사용자 지정할 수 없습니다. 그러나 업그레이드하기 전과 마찬가지로 계속 작동합니다.  

부팅 이미지가 사이트에 설치된 Windows ADK의 다른 버전을 기반으로 하는 경우 부팅 이미지를 사용자 지정해야 합니다. 배포 이미지 서비스 및 관리(DISM) 명령줄 도구를 사용하는 등 다른 메서드를 사용하여 이러한 부팅 이미지를 사용자 지정합니다. DISM은 Windows ADK의 한 구성 요소입니다. 자세한 내용은 [부팅 이미지 사용자 지정](customize-boot-images.md)을 참조하세요.  

## <a name="BKMK_AddBootImages"></a> 부팅 이미지 추가  

사이트 설치 중 Configuration Manager는 지원되는 버전의 Windows ADK에 있는 WinPE 버전을 기반으로 하는 부팅 이미지를 자동으로 추가합니다. Configuration Manager의 버전에 따라 지원되는 버전의 Windows ADK에 있는 다른 WinPE 버전을 기반으로 하는 부팅 이미지를 추가할 수 있습니다. 지원되지 않는 버전의 WinPE를 포함하는 부팅 이미지를 추가하려고 하면 오류가 발생합니다. 다음 목록은 현재 지원되는 Windows ADK 및 WinPE 버전입니다.

|  |  |
|---------|---------|
| Windows ADK 버전 | Windows 10용 Windows ADK |
| Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 Windows PE 버전 | Windows PE 10 |
| Configuration Manager 콘솔에서 ‘사용자 지정할 수 없지만’ 지원되는 부팅 이미지의 Windows PE 버전  | - Windows PE 3.1<sup>[참고 1](#bkmk_note1)</sup> <br> - Windows PE 5 |

예를 들어 Configuration Manager 콘솔을 사용하여 Windows 10용 Windows ADK의 Windows PE 10 기반의 부팅 이미지를 사용자 지정합니다. Windows PE 5에 기반하는 부팅 이미지의 경우 Windows 8용 Windows ADK에서 DISM의 버전을 사용하여 다른 컴퓨터에서 사용자 지정합니다. 그런 다음, 사용자 지정 부팅 이미지를 Configuration Manager 콘솔에 추가합니다. 자세한 내용은 다음 아티클을 참조하세요.

- [부팅 이미지 사용자 지정](/configmgr/osd/get-started/customize-boot-images)
- [Windows 10 ADK 지원](/configmgr/core/plan-design/configs/support-for-windows-10#windows-10-adk)
- [DISM 지원 플랫폼](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms)

<a name="bkmk_note1"></a>

> [!NOTE]
> **참고 1: Windows PE 3.1 지원**
>
> Windows PE ‘버전 3.1’을 기반으로 하는 Configuration Manager에만 부팅 이미지를 추가합니다.  Windows 7용 Windows AIK(Windows PE 3.0에 기반)를 Windows 7 SP1용 Windows AIK 추가 기능(Windows PE 3.1에 기반)으로 업그레이드합니다. [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=5188)에서 Windows 7 SP1용 Windows AIK 추가 기능을 다운로드합니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **운영 체제**를 확장하고 **부팅 이미지** 노드를 선택합니다.  

2. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **부팅 이미지 추가**를 선택합니다. 이 작업으로 부팅 이미지 추가 마법사가 시작됩니다.  

3. **데이터 원본** 페이지에서 다음 옵션을 지정합니다.  

    - **경로** 상자에서 부팅 이미지 WIM 파일의 경로를 지정합니다. 지정하는 경로는 UNC 형식의 유효한 네트워크 경로여야 합니다. `\\ServerName\ShareName\BootImageName.wim`

    - **부팅 이미지** 드롭다운 목록에서 부팅 이미지를 선택합니다. WIM 파일에 여러 부팅 이미지가 포함되어 있는 경우 적절한 이미지를 선택합니다.  

4. **일반** 페이지에서 다음 옵션을 지정합니다.  

    - **이름** 상자에서 부팅 이미지의 고유한 이름을 지정합니다.  

    - **버전** 상자에서 부팅 이미지의 버전 번호를 지정합니다.  

    - **설명** 상자에서 부팅 이미지 사용 방법에 관한 간단한 설명을 지정합니다.  

5. 마법사를 완료합니다.  

이제 부팅 이미지가 **부팅 이미지** 노드에 나열됩니다. 부팅 이미지를 사용하여 OS를 배포하기 전에 먼저 배포 지점에 부팅 이미지를 배포합니다.

> [!Tip]  
> 콘솔의 **부팅 이미지** 노드에서 **크기(KB)** 열에 각 부팅 이미지의 압축 해제된 크기가 표시됩니다. 사이트가 네트워크를 통해 부팅 이미지를 보내면 압축된 복사본을 전송합니다. 이 복사본은 **크기(KB)** 열에 나열된 크기보다 일반적으로 작습니다.  

## <a name="BKMK_DistributeBootImages"></a> 부팅 이미지 배포  

부팅 이미지는 다른 콘텐츠를 배포하는 것과 같은 방식으로 배포 지점에 배포할 수 있습니다. OS를 배포하거나 미디어를 만들기 전에 하나 이상의 배포 지점에 부팅 이미지를 배포합니다.

부팅 이미지를 배포하는 방법에 대한 자세한 내용은 [콘텐츠 배포](/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.  

PXE를 사용하여 OS를 배포하려면 부팅 이미지를 배포하기 전에 다음 사항을 고려합니다.  

- PXE 요청을 수락하도록 배포 지점 구성  
- 하나 이상의 PXE 사용 배포 지점에 x86 및 x64 PXE 사용 부팅 이미지를 둘 다 배포합니다.  
- Configuration Manager에서는 부팅 이미지를 PXE 사용 배포 지점의 **RemoteInstall** 폴더에 배포합니다.  
  
PXE를 사용하여 운영 체제를 배포하는 방법에 대한 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.  

## <a name="BKMK_ModifyBootImages"></a> 부팅 이미지 수정  

이미지에 디바이스 드라이버를 추가 또는 제거하거나 부팅 이미지의 속성을 편집합니다. 추가하거나 제거하는 드라이버로는 네트워크 드라이버 또는 스토리지 드라이버가 있을 수 있습니다. 부팅 이미지를 수정할 경우 다음 요소를 고려하세요.  

- 부팅 이미지에 드라이버를 추가하려면 먼저 드라이버를 디바이스 드라이버 카탈로그에 가져와서 사용하도록 설정합니다.  

- 부팅 이미지를 수정하는 경우 부팅 이미지에서 참조하는 관련 패키지는 변경되지 않습니다.  

- 부팅 이미지를 변경한 후 이미 있는 배포 지점의 부팅 이미지를 **업데이트**합니다. 이 프로세스는 부팅 이미지의 가장 최신 버전을 클라이언트에서 사용할 수 있도록 합니다. 자세한 내용은 [배포한 콘텐츠 관리](/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage)를 참조하세요.  

### <a name="modify-the-properties-of-a-boot-image"></a>부팅 이미지의 속성 수정  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **운영 체제**를 확장하고 **부팅 이미지** 노드를 선택합니다.  

2. 수정할 부팅 이미지를 선택합니다.  

3. 리본의 **홈** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

4. 부팅 이미지의 동작을 변경하려면 다음 설정 중 필요한 설정을 지정하세요.  

#### <a name="images"></a>이미지

**이미지** 탭에서 외부 도구를 사용하여 부팅 이미지의 속성을 변경하려면 **다시 로드**를 선택합니다.  

#### <a name="drivers"></a>드라이버

**드라이버** 탭에서 WinPE를 사용하기 위해 부팅해야 할 Windows 디바이스 드라이버를 추가합니다. 디바이스 드라이버를 추가할 때는 다음 사항을 고려하세요.  

- 부팅 이미지에 추가하는 드라이버가 부팅 이미지의 아키텍처와 일치하는지 확인합니다.  

- 부팅 이미지의 아키텍처용 드라이버만 표시하려면 **부팅 이미지의 아키텍처와 일치하지 않는 드라이버 숨기기**를 선택합니다. 드라이버 아키텍처는 제조업체 INF에서 보고되는 아키텍처를 기준으로 합니다.  

- WinPE는 이미 많은 기본 제공 드라이버와 함께 제공됩니다. WinPE에 포함되지 않은 네트워크 및 스토리지 드라이버만 추가하세요.  

- WinPE에 다른 드라이버에 대한 요구 사항이 없다면 부팅 이미지에 네트워크 및 스토리지 드라이버만 추가합니다.  

- 스토리지 및 네트워크 드라이버만 표시하려면 **스토리지 또는 네트워크 클래스에 없는 드라이버 숨기기(부팅 이미지용)** 를 선택합니다. 이 옵션은 비디오 드라이버, 모뎀 드라이버 등 일반적으로 부팅 이미지에 필요하지 않은 기타 드라이버도 숨깁니다.  

- 유효한 디지털 서명이 없는 드라이버를 숨기려면 **디지털 서명되지 않은 드라이버 숨기기**를 선택합니다.  

> [!NOTE]  
> 디바이스 드라이버를 부팅 이미지에 추가하기 전에 먼저 드라이버 카탈로그로 가져옵니다. 디바이스 드라이버를 가져오는 방법에 대한 자세한 내용은 [드라이버 관리](/configmgr/osd/get-started/manage-drivers)를 참조하세요.  

#### <a name="customization"></a>사용자 지정

**사용자 지정** 탭에서 다음 설정 중 필요한 설정을 선택합니다.  

- 작업 순서를 실행하기 전에 실행할 명령을 지정하려면 **시작 전 명령 사용** 옵션을 선택합니다. 이 옵션을 사용하는 경우 실행할 명령줄 및 명령에 필요한 지원 파일을 지정합니다.  

    > [!WARNING]  
    > 명령줄의 시작 부분에 `cmd /c`를 추가합니다. `cmd /c`를 지정하지 않으면 명령이 실행된 후 닫히지 않습니다. 배포는 명령이 종료될 때까지 기다리며 다른 구성된 명령이나 작업을 시작하지 않습니다.  

    > [!TIP]  
    > 작업 순서 미디어를 만드는 동안 마법사는 **CreateTSMedia.log** 파일에 패키지 ID 및 시작 전 명령줄을 기록합니다. 이 정보에는 작업 순서 변수의 값이 포함됩니다. 이 로그는 Configuration Manager 콘솔을 실행하는 컴퓨터에 있습니다. 이 로그 파일을 검토하여 작업 순서 변수의 값을 확인합니다.  

- 기본 WinPE 배경을 사용할지 아니면 사용자 지정 배경을 사용할지 지정하려면 **Windows PE 배경** 설정을 지정합니다.  

- WinPE에서 사용하는 임시 스토리지(RAM 드라이브)인 **Windows PE 스크래치 공간(MB)** 을 구성합니다. 예를 들어 WinPE 내에서 애플리케이션을 실행할 때 애플리케이션이 임시 파일을 써야 하는 경우 WinPE가 파일을 메모리의 스크래치 공간으로 리디렉션하여 하드 디스크가 있는 것처럼 시뮬레이트합니다. 기본적으로 이 크기는 1GB 이상의 RAM을 사용하는 디바이스의 경우 512MB이며, 1GB 미만의 RAM을 사용하는 디바이스의 경우 32MB입니다.  

- 부팅 이미지를 배포하는 동안 **F8** 키를 사용하여 명령 프롬프트를 열려면 **명령 지원 사용(테스트 전용)** 을 선택합니다. 이 옵션은 배포를 테스트하는 동안 문제를 해결하는 데 유용합니다. 보안 문제로 인해 프로덕션 배포에는 이 설정을 사용하지 않는 것이 좋습니다.  

- **WinPE에서 기본 자판 배열 설정**: <!--4910348-->버전 1910부터 부팅 이미지에 대 한 기본 자판 배열을 구성 합니다. en-us 이외의 언어를 선택하는 경우에도 Configuration Manager의 사용 가능한 입력 로캘에 en-us가 계속 포함됩니다. 디바이스에서 초기 키보드 레이아웃은 선택된 로캘이지만 사용자는 필요한 경우 디바이스를 en-us로 전환할 수 있습니다.

    > [!Tip]
    > 이제 [Set-CMBootImage](https://docs.microsoft.com/powershell/module/configurationmanager/set-cmbootimage?view=sccm-ps) PowerShell cmdlet에 새 매개 변수 `-InputLocale`이 포함되어 있습니다. 예를 들면 다음과 같습니다.
    >
    > ```PowerShell
    > # Set boot image keyboard layout to Russian (Russia)
    > Set-CMBootimage -Id "CM100004" -InputLocale "ru-ru"`
    > ```

#### <a name="optional-components"></a>선택적 구성 요소

**옵션 구성 요소** 탭에서 Configuration Manager와 함께 사용하기 위해 Windows PE에 추가할 구성 요소를 지정합니다. 사용 가능한 선택적 구성 요소에 대한 자세한 내용은 [WinPE: 패키지 추가(선택적 구성 요소 참조)](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-add-packages--optional-components-reference)를 참조하세요.  

다음 구성 요소는 Configuration Manager에 필수이며 항상 부팅 이미지에 추가됩니다.

- 스크립팅(WinPE-Scripting)
- 시작(WinPE-SecureStartup)
- 네트워크(WinPE-WDS-Tools)
- 스크립팅(WinPE-WMI)

**구성 요소** 목록은 이 부팅 이미지에 추가되는 추가 항목을 보여 줍니다. 구성 요소를 더 추가하려면 금색 별표를 선택합니다. 구성 요소를 제거하려면 목록에서 해당 구성 요소를 선택한 후 빨간색 X를 선택합니다.

다음은 고객이 일반적으로 사용하는 구성 요소입니다.

- Microsoft .NET (WinPE-NetFX):이 구성 요소는 PowerShell에 대 한 필수 구성 요소입니다. 크기가 큰 선택적 구성 요소 중 하나입니다.  
- Windows PowerShell (WinPE-PowerShell):이 구성 요소는 .NET을 필요로 하며 제한 된 PowerShell 지원을 추가 합니다. 작업 순서의 WinPE 단계에서 사용자 지정 PowerShell 스크립트를 실행하는 경우 이 구성 요소를 추가합니다. 다른 PowerShell cmdlet에는 다른 구성 요소가 필요할 수 있습니다.
- HTML(WinPE-HTA): 작업 순서의 WinPE 단계에서 사용자 지정 HTML 애플리케이션을 실행하는 경우 이 구성 요소를 추가합니다.

언어 추가에 대한 자세한 내용은 [여러 언어 구성](#BKMK_BootImageLanguage)을 참조하세요.

#### <a name="data-source"></a>데이터 원본

**데이터 원본** 탭에서 다음 설정 중 필요한 설정을 업데이트합니다.  

- 부팅 이미지의 원본 파일을 변경하려면 **이미지 경로** 및 **이미지 인덱스**를 설정합니다.  

- 사이트에서 부팅 이미지를 업데이트하는 일정을 만들려면 **일정에 따라 배포 지점 업데이트**를 선택합니다.  

- 다른 콘텐츠에 필요한 공간을 만들기 위해 시간 경과에 따라 클라이언트 캐시에서 이 패키지의 콘텐츠가 삭제되지 않도록 하려면 **클라이언트 캐시에 콘텐츠 보관**을 선택합니다.  

- 사이트에서 배포 지점에서 부팅 이미지 패키지를 업데이트할 때 변경된 파일만 배포하도록 지정하려면 **이진 차등 복제 사용**(BDR)을 선택합니다. 이 설정은 사이트 간의 네트워크 트래픽을 최소화합니다. BDR은 부팅 이미지 패키지가 크고 변경 내용이 상대적으로 적은 경우에 특히 유용합니다.  

- 부팅 이미지를 PXE 사용 배포에 사용하는 경우 **PXE 사용 배포 지점에서 이 부팅 이미지 배포**를 선택합니다. 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.  

#### <a name="data-access"></a>데이터 액세스

**데이터 액세스** 탭에서 패키지 공유 설정을 구성할 수 있습니다. 사용자 환경에 필요한 경우 이 옵션을 **배포 지점의 패키지 공유에 이 패키지의 콘텐츠 복사**로 설정합니다. 그러면 **패키지 공유에 대한 사용자 지정 이름 사용** 옵션을 추가로 선택하고 사용자 지정 **공유 이름**을 지정할 수 있습니다. 이 옵션을 사용하는 경우 배포 지점에 추가 디스크 공간이 필요합니다. 이 부팅 이미지를 수신하는 모든 배포 지점에 이러한 공간 요구 사항이 적용됩니다.

#### <a name="distribution-settings"></a>배포 설정

**배포 설정** 탭에서 다음 설정 중 필요한 설정을 선택합니다.  

- **배포 우선 순위** 목록에서 우선 순위 수준을 지정합니다. Configuration Manager는 사이트에서 동일한 배포 지점으로 여러 패키지를 배포하는 경우 이 우선 순위 목록을 사용합니다.  

- 기본 배포 지점에 대해 주문형 콘텐츠 배포를 사용하려면 **주문형 배포 시 사용**을 선택합니다. 이 설정을 사용하면 클라이언트에서 패키지에 대한 콘텐츠를 요청했는데 일부 배포 지점에서는 해당 콘텐츠를 사용할 수 없는 경우 관리 지점에서 콘텐츠를 배포합니다. 자세한 내용은 [주문형 콘텐츠 배포](/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management#on-demand-content-distribution)를 참조하세요.  

- 사이트에서 사전 준비된 콘텐츠에 사용되는 배포 지점에 부팅 이미지를 배포할 방법을 지정하려면 **사전 준비된 배포 지점 설정**을 설정합니다. 사전 준비된 콘텐츠에 대한 자세한 내용은 [콘텐츠 사전 준비](/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage)를 참조하세요.  

#### <a name="content-locations"></a>콘텐츠 위치

**콘텐츠 위치** 탭에서 배포 지점 또는 배포 지점 그룹을 선택하고 다음 작업을 사용합니다.  

- **유효성 검사**: 선택한 배포 지점 또는 배포 지점 그룹의 부팅 이미지 패키지에 대한 무결성을 확인합니다.  

- **재배포**: 선택한 배포 지점 또는 배포 지점 그룹에 다시 부팅 이미지를 배포합니다.  

- **제거**: 선택한 배포 지점 또는 배포 지점 그룹에서 부팅 이미지를 삭제합니다.  

#### <a name="security"></a>보안

**보안** 탭에는 이 개체에 대한 권한이 있는 관리자가 표시됩니다.

## <a name="BKMK_BootImagePXE"></a> PXE 부팅 이미지 구성  

PXE 기반 배포에 부팅 이미지를 사용하려면 먼저 해당 부팅 이미지를 PXE 사용 배포 지점에서 배포하도록 구성합니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **운영 체제**를 확장하고 **부팅 이미지** 노드를 선택합니다.  

2. 수정할 부팅 이미지를 선택합니다.  

3. 리본의 **홈** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

4. **데이터 원본** 탭에서 **PXE 사용 배포 지점에서 이 부팅 이미지 배포**를 선택합니다. 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.  

## <a name="BKMK_BootImageLanguage"></a> 여러 언어 구성

> [!TIP]
> 버전 1910부터 부팅 이미지의 속성에 대 한 기본 키보드 레이아웃을 구성 합니다. 자세한 내용은 [사용자 지정](#customization)을 참조하세요.<!--4910348-->

부팅 이미지는 언어 중립적입니다. 이 기능을 통해 하나의 부팅 이미지를 사용하여 WinPE에 있는 동안 여러 언어로 작업 순서 텍스트를 표시할 수 있습니다. 부팅 이미지 **선택적 구성 요소** 탭에서 적절한 언어 지원을 포함합니다. 그런 다음, 표시할 언어를 나타내도록 적절한 작업 순서 변수를 설정합니다. 배포된 OS의 언어와 WinPE의 언어는 상호 독립적입니다. WinPE에서 사용자에게 표시하는 언어는 다음과 같은 방식으로 결정됩니다.  

- 사용자가 기존 OS에서 작업 순서를 실행하는 경우 Configuration Manager는 해당 사용자에 대해 구성된 언어를 자동으로 사용합니다. 필수 배포 마감일에 도달하여 작업 순서가 자동으로 실행되는 경우 Configuration Manager는 OS의 언어를 사용합니다.  

- PXE 또는 미디어를 사용하는 OS 배포의 경우 시작 전 명령의 일부로 **SMSTSLanguageFolder** 변수에 언어 ID 값을 설정합니다. 컴퓨터를 WinPE로 부팅하는 경우 변수에 지정한 언어로 메시지가 표시됩니다. 지정한 폴더의 언어 리소스 파일에 액세스하는 동안 오류가 발생하거나 변수를 설정하지 않은 경우 WinPE는 기본 언어로 메시지를 표시합니다.  

    > [!NOTE]  
    > 미디어가 암호로 보호되는 경우 사용자에게 암호를 요청하는 텍스트는 항상 WinPE 언어로 표시됩니다.  

PXE 또는 미디어로 시작하는 OS 배포에 대해 WinPE 언어를 설정하려면 다음 절차를 따르세요.  

### <a name="set-the-windows-pe-language-for-a-pxe-or-media-initiated-os-deployment"></a>PXE 또는 미디어로 시작하는 OS 배포에 대해 Windows PE 언어를 설정합니다.  

1. 부팅 이미지를 업데이트하기 전에 사이트 서버의 해당 언어 폴더에 적합한 작업 순서 리소스 파일(tsres.dll)이 있는지 확인합니다. 예를 들어 영어 리소스 파일이 있는 위치는 `<ConfigMgrInstallationFolder>\OSD\bin\x64\00000409\tsres.dll`입니다.  

2. 시작 전 명령의 일부로 **SMSTSLanguageFolder** 환경 변수를 적합한 언어 ID로 설정합니다. 언어 ID는 16진수 형식이 아닌 10진수 형식을 사용하여 지정해야 합니다. 예를 들어 언어 ID를 영어로 설정하려면 폴더 이름의 16진수 값인 00000409 대신 10진수 값인 **1033**을 지정합니다.  
