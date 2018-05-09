---
title: '부팅 이미지 관리 '
titleSuffix: Configuration Manager
description: Configuration Manager에서 운영 체제를 배포하는 동안 사용하는 Windows PE 부팅 이미지를 관리하는 방법을 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6a2fe20896a781d7c897bd5a827d25a7b70390b7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-boot-images-with-system-center-configuration-manager"></a>System Center Configuration Manager로 부팅 이미지 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 부팅 이미지는 운영 체제 배포 중에 사용되는 [WinPE(Windows PE)](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) 이미지입니다. 부팅 이미지는 WinPE에서 컴퓨터를 시작하는 데 사용됩니다. 이 최소 운영 체제는 제한된 구성 요소 및 서비스를 포함합니다. Configuration Manager는 WinPE를 사용하여 Windows 설치용으로 대상 컴퓨터를 준비합니다. 부팅 이미지를 관리하려면 다음 섹션을 참조하세요.

## <a name="BKMK_BootImageDefault"></a> 기본 부팅 이미지
Configuration Manager는 x86 플랫폼을 지원하는 부팅 이미지와 x64 플랫폼을 지원하는 부팅 이미지 등 두 가지 기본 부팅 이미지를 제공합니다. 이러한 이미지는 \\\\*서버 이름*>\SMS_<*사이트 코드*>\osd\boot\\<*x64*> 또는 <*i386*>에 저장됩니다. 기본 부팅 이미지는 수행하는 작업에 따라 업데이트되거나 다시 생성됩니다.

기본 부팅 이미지에 대해 설명된 작업 중 하나에 대한 다음과 같은 동작을 고려합니다.
- 원본 드라이버 개체는 유효해야 합니다. 이러한 개체는 드라이버 원본 파일을 포함합니다. 개체가 유효하지 않으면 사이트는 부팅 이미지에 드라이버를 추가하지 않습니다.
- 같은 Windows PE 버전을 사용하더라도 기본 부팅 이미지를 기반으로 하지 않는 부팅 이미지는 수정되지 않습니다.
- 수정된 부팅 이미지를 배포 지점에 다시 배포합니다.
- 수정된 부팅 이미지를 사용하는 모든 미디어를 다시 만듭니다.
- 사용자 지정된/기본 부팅 이미지를 자동으로 업데이트하지 않으려면 기본 위치에 저장하지 마세요.

> [!NOTE]
> CMTrace(Configuration Manager 추적 로그 도구)가 **소프트웨어 라이브러리**의 모든 부팅 이미지에 추가됩니다. Windows PE에 있는 경우 명령 프롬프트에서 **CMTrace**를 입력하여 도구를 시작합니다. 버전 1802부터 Windows PE에서 cmtrace.exe를 시작할 때 이 프로그램을 로그 파일에 대한 기본 뷰어로 만들지 여부를 선택하는 메시지가 더 이상 표시되지 않습니다.

### <a name="use-updates-and-servicing-to-install-the-latest-version-of-configuration-manager"></a>업데이트 및 서비스를 사용하여 최신 버전의 Configuration Manager 설치
버전 1702부터 Windows ADK(평가 및 배포 키트) 버전을 업그레이드한 다음, 업데이트 및 설치를 사용하여 최신 버전의 Configuration Manager를 설치하면 사이트가 기본 부팅 이미지를 다시 생성합니다. 이 업데이트는 업데이트된 Windows ADK의 새 WinPE 버전, 새 Configuration Manager 클라이언트 버전, 드라이버 및 사용자 지정을 포함합니다. 사이트는 사용자 지정 부팅 이미지를 수정하지 않습니다.

버전 1702 이전의 Configuration Manager는 클라이언트 구성 요소, 드라이버 및 사용자 지정이 포함된 기존 부팅 이미지를 업데이트하지만 Windows ADK의 최신 WinPE 버전을 사용하지 않습니다. 새 Windows ADK 버전을 사용하려면 부팅 이미지를 수동으로 수정합니다.

### <a name="upgrade-from-configuration-manager-2012-to-configuration-manager-current-branch-cb"></a>Configuration Manager 2012에서 Configuration Manager CB(현재 분기)로 업그레이드
설치 프로세스를 사용하여 Configuration Manager 2012를 Configuration Manager CB로 업그레이드하면 사이트가 기본 부팅 이미지를 다시 생성합니다. 이 업데이트에는 업데이트된 Windows ADK의 새 WinPE 버전 및 새 Configuration Manager 클라이언트 버전이 포함됩니다. 모든 부팅 이미지 사용자 지정은 변경되지 않습니다. 사이트는 사용자 지정 부팅 이미지를 수정하지 않습니다.

### <a name="update-distribution-points-with-the-boot-image"></a>부팅 이미지를 사용하여 배포 지점 업데이트
콘솔의 **부팅 이미지** 노드에서 **배포 지점 업데이트** 작업을 사용하는 경우 사이트는 클라이언트 구성 요소, 드라이버 및 사용자 지정이 포함된 대상 부팅 이미지를 업데이트합니다.    

Configuration Manager 버전 1706부터 부팅 이미지를 Windows ADK 설치 디렉터리에서 최신 버전의 WinPE로 다시 로드합니다. 배포 지점 업데이트 마법사의 **일반** 페이지에서 다음 정보를 제공합니다. 
 - 사이트 서버에 설치된 Windows ADK 버전
 - 부팅 이미지의 WinPE의 Windows ADK 버전
 - Configuration Manager 클라이언트의 버전은 이 정보를 사용하여 부팅 이미지를 다시 로드할지 여부를 결정하도록 돕습니다. **부팅 이미지** 노드에는 (**클라이언트 버전**)에 대한 새 열도 포함됩니다. 이 열을 사용하여 각 부팅 이미지에서 Configuration Manager 클라이언트 버전을 신속하게 확인합니다.    


##  <a name="BKMK_BootImageCustom"></a> 부팅 이미지 사용자 지정  
 부팅 이미지가 Windows ADK의 지원되는 버전에서 WinPE 버전을 기반으로 하는 경우 콘솔에서 [부팅 이미지를 수정](#BKMK_ModifyBootImages)하거나 사용자 지정할 수 있습니다. 사이트를 새 버전으로 업그레이드하고 Windows ADK의 새 버전을 설치하는 경우 사용자 지정 부팅 이미지(기본 부팅 이미지의 위치에 없음)는 Windows ADK의 새 버전으로 업데이트되지 않습니다. 이 경우, Configuration Manager 콘솔에서 부팅 이미지를 사용자 지정할 수 없습니다. 그러나 업그레이드하기 전과 마찬가지로 계속 작동합니다.  

 부팅 이미지가 사이트에 설치된 Windows ADK의 다른 버전을 기반으로 하는 경우 부팅 이미지를 사용자 지정해야 합니다. 배포 이미지 서비스 및 관리(DISM) 명령줄 도구를 사용하는 등 다른 메서드를 사용하여 이러한 부팅 이미지를 사용자 지정합니다. DISM은 Windows ADK의 한 구성 요소입니다. 자세한 내용은 [부팅 이미지 사용자 지정](customize-boot-images.md)을 참조하세요.  

##  <a name="BKMK_AddBootImages"></a> 부팅 이미지 추가  

 사이트 설치 중 Configuration Manager는 지원되는 버전의 Windows ADK에 있는 WinPE 버전을 기반으로 하는 부팅 이미지를 자동으로 추가합니다. Configuration Manager의 버전에 따라 지원되는 버전의 Windows ADK에 있는 다른 WinPE 버전을 기반으로 하는 부팅 이미지를 추가할 수 있습니다. 지원되지 않는 버전의 WinPE를 포함하는 부팅 이미지를 추가하려고 하면 오류가 발생합니다. 다음 목록은 현재 지원되는 Windows ADK 및 WinPE 버전입니다. 

-   **Windows ADK 버전**  

     Windows 10용 Windows ADK  

-   **Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 Windows PE 버전**  

     Windows PE 10  

-   **Configuration Manager 콘솔에서 사용자 지정할 수 없지만 지원되는 부팅 이미지의 Windows PE 버전**  

     Windows PE 3.1<sup>1</sup> 및 Windows PE 5  

     <sup>1</sup> 부팅 이미지가 Windows PE 3.1을 기반으로 하는 경우에만 Configuration Manager에 부팅 이미지를 추가할 수 있습니다. Windows 7용 Windows AIK(Windows PE 3.0에 기반)를 Windows 7 SP1용 Windows AIK 추가 기능(Windows PE 3.1에 기반)으로 업그레이드합니다. [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=5188)에서 Windows 7 SP1용 Windows AIK 추가 기능을 다운로드합니다.  

     예를 들어 Configuration Manager 콘솔을 사용하여 Windows 10용 Windows ADK의 Windows PE 10 기반의 부팅 이미지를 사용자 지정합니다. Windows PE 5에 기반하는 부팅 이미지의 경우 Windows 8용 Windows ADK에서 DISM의 버전을 사용하여 다른 컴퓨터에서 사용자 지정합니다. 그런 다음, 사용자 지정 부팅 이미지를 Configuration Manager 콘솔에 추가합니다. 자세한 내용은 [부팅 이미지 사용자 지정](customize-boot-images.md)을 참조하세요.

 수동으로 부팅 이미지를 추가하려면 다음 절차를 따르세요.  

#### <a name="to-add-a-boot-image"></a>부팅 이미지를 추가하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **부팅 이미지 추가** 를 클릭하여 부팅 이미지 추가 마법사를 시작합니다.  

4.  **데이터 원본** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.  

    -   **경로** 상자에서 부팅 이미지 WIM 파일의 경로를 지정합니다.  

         지정하는 경로는 UNC 형식의 유효한 네트워크 경로여야 합니다. 예를 들면 \\\\<*서버 이름*\\<*공유 이름*>\\<*부팅 이미지 이름*>.wim입니다.  

    -   **부팅 이미지** 드롭다운 목록에서 부팅 이미지를 선택합니다. WIM 파일에 여러 부팅 이미지가 포함되어 있는 경우 적절한 이미지를 선택합니다.  

5.  **일반**  페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.  

    -   **이름** 상자에서 부팅 이미지의 고유한 이름을 지정합니다.  

    -   **버전** 상자에서 부팅 이미지의 버전 번호를 지정합니다.  

    -   **설명** 상자에서 부팅 이미지의 사용 방법에 관한 간단한 설명을 지정합니다.  

6.  마법사를 완료합니다.  

 이제 부팅 이미지가 Configuration Manager 콘솔의 **부팅 이미지** 노드에 나열됩니다. 부팅 이미지를 사용하여 운영 체제를 배포하기 전에 배포 지점에 부팅 이미지를 배포합니다. 

> [!NOTE]  
>  콘솔의 **부팅 이미지** 노드에서 **크기(KB)** 열에 각 부팅 이미지의 압축 해제된 크기가 표시됩니다. 사이트가 네트워크를 통해 부팅 이미지를 보내면 압축된 복사본을 전송합니다. 이 복사본은 **크기(KB)** 열에 나열된 크기보다 일반적으로 작습니다.  

##  <a name="BKMK_DistributeBootImages"></a> 배포 지점에 부팅 이미지 배포  
 부팅 이미지는 다른 콘텐츠를 배포하는 것과 같은 방식으로 배포 지점에 배포할 수 있습니다. 대부분의 경우 운영 체제를 배포하고 미디어를 만들기 전에 하나 이상의 배포 지점에 부팅 이미지를 배포해야 합니다.   

> [!NOTE]  
> PXE를 사용하여 운영 체제를 배포하려면 부팅 이미지를 배포하기 전에 다음 사항을 고려합니다.  
> - PXE 요청을 수락하도록 배포 지점 구성  
> - 하나 이상의 PXE 사용 배포 지점에 x86 및 x64 PXE 사용 부팅 이미지를 둘 다 배포합니다.  
> - Configuration Manager에서는 부팅 이미지를 PXE 사용 배포 지점의 **RemoteInstall** 폴더에 배포합니다.  
>   
> PXE를 사용하여 운영 체제를 배포하는 방법에 대한 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

 부팅 이미지를 배포하는 단계는 [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.  

##  <a name="BKMK_ModifyBootImages"></a> 부팅 이미지 수정  
 이미지에 장치 드라이버를 추가 또는 제거하거나 부팅 이미지와 관련된 속성을 편집할 수 있습니다. 추가하거나 제거할 수 있는 장치 드라이버에는 네트워크 어댑터 또는 대용량 저장소 장치 드라이버 등이 있습니다. 부팅 이미지를 수정할 경우 다음 요소를 고려하세요.  

-   부팅 이미지에 추가하려면 먼저 장치 드라이버를 가져오고 장치 드라이버 카탈로그에서 사용하도록 설정합니다.  

-   부팅 이미지를 수정하는 경우 부팅 이미지에서 참조하는 관련 패키지는 변경되지 않습니다.  

-   부팅 이미지를 변경한 후 이미 있는 배포 지점의 부팅 이미지를 **업데이트**합니다. 이 프로세스는 부팅 이미지의 가장 최신 버전을 클라이언트에서 사용할 수 있도록 합니다. 자세한 내용은 [배포한 콘텐츠 관리](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage)를 참조하세요.  

 부팅 이미지를 수정하려면 다음 절차를 따르세요.  

#### <a name="to-modify-the-properties-of-a-boot-image"></a>부팅 이미지의 속성을 수정하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

3.  수정할 부팅 이미지를 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성** 을 클릭하여 부팅 이미지의 **속성** 대화 상자를 엽니다.  

5.  부팅 이미지의 동작을 변경하려면 다음 설정 중 필요한 설정을 지정하세요.  

    -   **이미지** 탭에서 외부 도구를 사용하여 부팅 이미지의 속성을 변경한 경우 **다시 로드**를 클릭합니다.  

    -   **드라이버** 탭에서 WinPE를 부팅하는 데 필요한 Windows 장치 드라이버를 추가합니다. 장치 드라이버를 추가할 때는 다음 사항을 고려하세요.  

        -   부팅 이미지의 아키텍처용 드라이버만 표시하려면 **부팅 이미지의 아키텍처와 일치하지 않는 드라이버 숨기기**를 선택합니다. 아키텍처는 제조업체 INF에서 보고되는 아키텍처를 기준으로 합니다.  

        -   **(부팅 이미지용) 저장소 또는 네트워크 클래스에 없는 드라이버 숨기기**를 선택하여 저장소 및 네트워크 드라이버만 표시합니다. 이 옵션은 또한 비디오 또는 모뎀 드라이버 등의 부팅 이미지에 일반적으로 필요하지 않은 기타 드라이버를 숨깁니다.  

        -   **디지털 서명되지 않은 드라이버 숨기기**를 선택하여 유효한 디지털 서명이 없는 드라이버를 숨깁니다.  

        -   WinPE에서 다른 드라이버에 대한 요구 사항이 없다면 부팅 이미지에 네트워크 및 대용량 저장소 드라이버만 추가하는 것이 좋습니다.  

        -   WinPE에서는 이미 많은 드라이버를 기본 제공하므로 WinPE에서 제공하지 않는 네트워크 및 대용량 저장소 드라이버만 추가합니다.  

        -   부팅 이미지에 추가하는 드라이버가 부팅 이미지의 아키텍처와 일치하는지 확인합니다.  

        > [!NOTE]  
        >  장치 드라이버를 부팅 이미지에 추가하기 전에 드라이버 카탈로그로 가져와야 합니다. 장치 드라이버를 가져오는 방법에 대한 자세한 내용은 [드라이버 관리](manage-drivers.md)를 참조하세요.  

    -   **사용자 지정** 탭에서 다음 설정 중 필요한 설정을 선택합니다.  

        -   작업 순서를 실행하기 전에 실행할 명령을 지정하려면 **시작 전 명령 사용** 확인란을 선택합니다. 이 옵션을 사용하는 경우 실행할 명령줄 및 명령에 필요한 지원 파일을 지정합니다.  

            > [!WARNING]  
            >  명령줄의 시작 부분에 **cmd /c**를 추가합니다. **cmd /c**를 지정하지 않으면 명령이 실행된 후 닫히지 않습니다. 배포는 명령이 종료될 때까지 기다리며 다른 구성된 명령이나 작업을 시작하지 않습니다.  

            > [!TIP]  
            >  작업 순서 미디어를 만드는 동안 마법사는 CreateTSMedia.log 로그 파일에 작업 순서 변수의 값을 포함하여 패키지 ID 및 시작 전 명령줄을 기록합니다. 이 로그는 Configuration Manager 콘솔을 실행하는 컴퓨터에 있습니다. 이 로그 파일을 검토하여 작업 순서 변수의 값을 확인합니다.  

        -   기본 WinPE 배경을 사용할지 아니면 사용자 지정 배경을 사용할지 지정하려면 **Windows PE 배경** 설정을 지정합니다.  

        -   부팅 이미지를 배포하는 동안 **F8** 키를 사용하여 명령 프롬프트를 열려면 **명령 지원 사용(테스트 전용)** 을 선택합니다. 이 옵션은 배포를 테스트하는 동안 문제를 해결하는 데 유용합니다. 프로덕션 배포에는 이 설정을 사용하지 않는 것이 좋습니다.  

        -   WinPE에서 사용하는 임시 저장소(RAM 드라이브)인 Windows PE 스크래치 공간을 구성합니다. 예를 들어 WinPE 내에서 응용 프로그램을 실행할 때 응용 프로그램이 임시 파일을 써야 하는 경우 WinPE가 파일을 메모리의 스크래치 공간으로 리디렉션하여 하드 디스크가 있는 것처럼 시뮬레이트합니다. WinPE에서는 기본적으로 32MB의 쓰기 가능 메모리를 할당합니다.  

    -   **데이터 원본** 탭에서 다음 설정 중 필요한 설정을 업데이트합니다.  

        -   부팅 이미지의 원본 파일을 변경하려면 **이미지 경로** 및 **이미지 인덱스**를 설정합니다.  

        -   사이트에서 부팅 이미지를 업데이트하는 일정을 만들려면 **일정에 따라 배포 지점 업데이트**를 선택합니다.  

        -   다른 콘텐츠에 필요한 공간을 만들기 위해 시간 경과에 따라 클라이언트 캐시에서 이 패키지의 콘텐츠가 삭제되지 않도록 하려면 **클라이언트 캐시에 콘텐츠 보관**을 선택합니다.  

        -   사이트에서 배포 지점에서 부팅 이미지 패키지를 업데이트할 때 변경된 파일만 배포하도록 지정하려면 **이진 차등 복제 사용**(BDR)을 선택합니다. 이 설정은 사이트 간의 네트워크 트래픽을 최소화합니다. BDR은 부팅 이미지 패키지가 크고 변경 내용이 상대적으로 적은 경우에 특히 유용합니다.  

        -   부팅 이미지를 PXE 사용 배포에 사용하는 경우 **PXE 사용 배포 지점에서 이 부팅 이미지 배포**를 선택합니다.  

            > [!NOTE]  
            >  자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

    -   **데이터 액세스** 탭에서 다음 설정 중 필요한 설정을 선택합니다.  

        -   클라이언트가 이 패키지의 콘텐츠를 네트워크에서 설치하도록 하려면 **패키지 공유 설정** 을 지정합니다.  

        -   Configuration Manager가 배포 지점에서 사용자 연결을 끊는 방법을 지정하려면 **패키지 업데이트 설정**을 지정합니다. Configuration Manager가 부팅 이미지를 업데이트하지 못할 수도 있습니다.  

    -   **배포 설정** 탭에서 다음 설정 중 필요한 설정을 선택합니다.  

        -   **배포 우선 순위** 목록에서 우선 순위 수준을 지정합니다. Configuration Manager는 사이트에서 동일한 배포 지점으로 여러 패키지를 배포하는 경우 이 우선 순위 목록을 사용합니다.  

        -   주문형 콘텐츠 배포를 기본 배포 지점으로 사용하도록 설정하려면 **기본 배포 지점으로 이 패키지의 콘텐츠 배포**를 선택합니다. 이 설정을 사용하면 클라이언트에서 패키지에 대한 콘텐츠를 요청하고 기본 배포 지점에서 해당 콘텐츠를 사용할 수 없는 경우 관리 지점에서 모든 기본 배포 지점에 콘텐츠를 배포합니다.  

        -   사이트에서 사전 준비된 콘텐츠에 사용되는 배포 지점에 부팅 이미지를 배포할 방법을 지정하려면 **사전 준비된 배포 지점 설정**을 설정합니다.  

            > [!NOTE]  
            >  사전 준비된 콘텐츠에 대한 자세한 내용은 [콘텐츠 사전 준비](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage)를 참조하세요.  

    -   **콘텐츠 위치** 탭에서 배포 지점 또는 배포 지점 그룹을 선택하고 다음 작업 중 필요한 작업을 수행합니다.  

        -   **재배포** 를 클릭하여 선택한 배포 지점 또는 배포 지점 그룹에 다시 부팅 이미지를 배포합니다.  

        -   **유효성 검사** 를 클릭하여 선택한 배포 지점 또는 배포 지점 그룹의 부팅 이미지 패키지에 대한 무결성을 확인합니다.  

    -   **옵션 구성 요소** 탭에서 Configuration Manager와 함께 사용하기 위해 Windows PE에 추가할 구성 요소를 지정합니다. 사용 가능한 선택적 구성 요소에 대한 자세한 내용은 [WinPE: 패키지 추가(선택적 구성 요소 참조)](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-add-packages--optional-components-reference)를 참조하세요.  

    -   **보안** 탭에서 관리자를 선택하고 관리자가 수행할 수 있는 작업을 변경합니다.  

6.  속성을 구성했으면 **확인**을 클릭합니다.  

##  <a name="BKMK_BootImagePXE"></a> PXE 사용 배포 지점에서 배포하도록 부팅 이미지 구성  
 PXE 운영 체제 배포에 부팅 이미지를 사용하려면 먼저 해당 부팅 이미지를 PXE 사용 배포 지점에서 배포하도록 구성해야 합니다.  

#### <a name="to-configure-a-boot-image-to-deploy-from-a-pxe-enabled-distribution-point"></a>PXE 사용 배포 지점에서 배포하도록 부팅 이미지를 구성하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

3.  수정할 부팅 이미지를 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성** 을 클릭하여 부팅 이미지의 **속성** 대화 상자를 엽니다.  

5.  **데이터 원본** 탭에서 **PXE 사용 배포 지점에서 이 부팅 이미지 배포**를 선택합니다.  

    > [!NOTE]  
    >  자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

6.  속성을 구성했으면 **확인**을 클릭합니다.  

##  <a name="BKMK_BootImageLanguage"></a> 부팅 이미지 배포에 필요한 여러 언어 구성  
 부팅 이미지는 언어 중립적입니다. 이 기능을 통해 하나의 부팅 이미지를 사용하여 WinPE에 있는 동안 여러 언어로 작업 순서 텍스트를 표시할 수 있습니다. 부팅 이미지 **선택적 구성 요소** 탭에서 적절한 언어 지원을 포함합니다. 그런 다음, 표시할 언어를 나타내도록 적절한 작업 순서 변수를 설정합니다. 배포된 운영 체제의 언어는 WinPE에서 언어와 독립적입니다. WinPE에서 사용자에게 표시하는 언어는 다음과 같은 방식으로 결정됩니다.  

-   기존 운영 체제에서 작업 순서를 실행하는 경우 Configuration Manager는 사용자에게 구성된 언어를 자동으로 사용합니다. 필수 배포 최종 기한에 도달하여 작업 순서가 자동으로 실행된 경우 Configuration Manager는 운영 체제의 언어를 사용합니다.  

-   PXE 또는 미디어를 사용하는 운영 체제 배포의 경우 시작 전 명령의 일부로 **SMSTSLanguageFolder** 변수에 언어 ID 값을 설정합니다. 컴퓨터를 WinPE로 부팅하는 경우 변수에 지정한 언어로 메시지가 표시됩니다. 지정한 폴더의 언어 리소스 파일에 액세스하는 동안 오류가 발생하거나 변수를 설정하지 않은 경우 WinPE는 기본 언어로 메시지를 표시합니다.  

    > [!NOTE]  
    >  미디어가 암호로 보호된 경우 사용자에게 암호를 요청하는 텍스트는 WinPE 언어로 표시됩니다.  

 PXE 또는 미디어로 시작하는 운영 체제 배포에 대해 WinPE 언어를 설정하려면 다음 절차를 따르세요.  

#### <a name="to-set-the-windows-pe-language-for-a-pxe-or-media-initiated-operating-system-deployment"></a>PXE 또는 미디어로 시작하는 운영 체제 배포에 대해 Windows PE 언어를 설정하려면  

1.  부팅 이미지를 업데이트하기 전에 사이트 서버의 해당 언어 폴더에 적합한 작업 순서 리소스 파일(tsres.dll)이 있는지 확인합니다. 예를 들어 영어 리소스 파일은 <*ConfigMgrInstallationFolder*>\OSD\bin\x64\00000409\tsres.dll 위치에 있습니다.  

2.  시작 전 명령의 일부로 SMSTSLanguageFolder 환경 변수를 적합한 언어 ID로 설정합니다. 언어 ID는 16진수가 아닌 10진수를 사용하여 지정해야 합니다. 예를 들어 언어 ID를 영어로 설정하려면 폴더 이름의 16진수 값인 00000409 대신 10진수 값인 1033을 지정합니다.  
