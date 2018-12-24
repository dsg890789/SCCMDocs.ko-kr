---
title: OS 업그레이드 작업 순서 만들기
titleSuffix: Configuration Manager
description: 작업 순서를 사용하여 자동으로 Windows 7 이상에서 Windows 10으로 업그레이드
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bddcd356a3ee221d5b67935a5be91bbe89d2afc2
ms.sourcegitcommit: be8c0182db9ef55a948269fcbad7c0f34fd871eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42756057"
---
# <a name="create-a-task-sequence-to-upgrade-an-os-in-configuration-manager"></a>Configuration Manager에서 OS를 업그레이드하는 작업 순서 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 작업 순서를 사용하여 대상 컴퓨터의 OS를 자동으로 업그레이드합니다. Windows 7 이상에서 Windows 10으로 또는 Windows Server 2012 이상에서 Windows Server 2016으로 업그레이드할 수 있습니다. OS 업그레이드 패키지 및 응용 프로그램 또는 소프트웨어 업데이트와 같은 설치할 기타 콘텐츠를 참조하는 작업 순서를 만듭니다. OS를 업그레이드하는 작업 순서는 [최신 버전으로 Windows 업그레이드](upgrade-windows-to-the-latest-version.md) 시나리오의 일부입니다.  



## <a name="prerequisites"></a>필수 구성 요소

작업 순서를 만들려면 먼저 다음 요구 사항이 준비되어야 합니다.    

#### <a name="required"></a>필수  

- [OS 업그레이드 패키지](/sccm/osd/get-started/manage-operating-system-upgrade-packages)를 Configuration Manager 콘솔에서 사용할 수 있어야 합니다.  

- Windows Server 2016으로 업그레이드하는 경우, 운영 체제 업그레이드 작업 순서 단계에서 **무시할 수 있는 호환성 메시지 모두 무시** 설정을 선택합니다. 그렇지 않으면 업그레이드에 실패합니다.  

#### <a name="required-if-used"></a>필수(사용될 경우)  

-   Configuration Manager 콘솔에서 [소프트웨어 업데이트](/sccm/sum/get-started/synchronize-software-updates)를 동기화해야 합니다.  

-   Configuration Manager 콘솔에 [응용 프로그램](/sccm/apps/deploy-use/create-applications)을 추가해야 합니다.  



##  <a name="BKMK_UpgradeOS"></a> OS를 업그레이드하는 작업 순서 만들기  

클라이언트에서 OS를 업그레이드하려면 작업 순서 만들기 마법사에서 작업 순서를 만들고 **업그레이드 패키지에서 운영 체제 업그레이드**를 선택합니다. 마법사는 OS를 업그레이드하고 소프트웨어 업데이트를 적용한 다음, 응용 프로그램을 설치하는 작업 순서 단계를 추가합니다. 

#### <a name="to-create-a-task-sequence-that-upgrades-an-os"></a>OS를 업그레이드하는 작업 순서를 만들려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장한 다음, **작업 순서**를 클릭합니다.  

2.  에 **홈** 리본 메뉴의 탭에서 합니다 **만들기** 그룹에서 클릭 **작업 순서 만들기**합니다.  

3.  작업 순서 만들기 마법사의 **새 작업 순서 만들기** 페이지에서 **업그레이드 패키지에서 운영 체제 업그레이드**를 선택한 다음, **다음**을 클릭합니다.  

4.  **작업 순서 정보** 페이지에서 다음 설정을 지정한 다음, **다음**을 클릭합니다.  

    -   **작업 순서 이름**: 작업 순서를 식별하는 이름을 지정합니다.  

    -   **설명**: 필요에 따라 설명을 지정합니다.  

5.  **Windows 운영 체제 업그레이드** 페이지에서 다음 설정을 지정한 다음, **다음**을 클릭합니다.  

    -   **업그레이드 패키지**: OS 업그레이드 원본 파일이 포함된 업그레이드 패키지를 지정합니다. **속성** 창에서 해당 정보를 확인하여 올바른 업그레이드 패키지를 선택했는지 알아봅니다. 자세한 내용은 [OS 업그레이드 패키지 관리](/sccm/osd/get-started/manage-operating-system-upgrade-packages)를 참조하세요.  

    -   **버전 인덱스**: 패키지에서 사용할 수 있는 OS 버전 인덱스가 여러 개 있는 경우 원하는 버전 인덱스를 선택합니다. 기본적으로 마법사는 첫 번째 인덱스를 선택합니다.  

    -   **제품 키**: 설치할 OS의 Windows 제품 키를 지정합니다. 인코딩된 볼륨 라이선스 키 또는 표준 제품 키를 지정하세요. 표준 제품 키를 사용하는 경우 5자로 이루어진 각 그룹을 대시(-)로 구분 합니다. 예: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX* 볼륨 라이선스 버전용 업그레이드의 경우에는 제품 키가 필요하지 않을 수 있습니다.  

        > [!Note]  
        > 이 제품 키는 MAK(복수 정품 인증 키) 또는 GVLK(일반 볼륨 라이선스 키)일 수 있습니다. GVLK는 또한 KMS(키 관리 서비스) 클라이언트 설정 키라고도 합니다. 자세한 내용은 [볼륨 활성화 계획](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client)을 참조하세요. KMS 클라이언트 설정 키의 목록은 Windows Server 정품 인증 가이드의 [부록 A](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys)를 참조하세요. 

    -   **무시할 수 있는 호환성 메시지 모두 무시**: Windows Server 2016으로 업그레이드하는 중인 경우 이 설정을 선택합니다. 이 설정을 선택하지 않으면 Windows 설치 프로그램이 사용자가 Windows 앱 호환성 대화 상자에서 **확인**을 클릭할 때까지 대기하므로 작업 순서가 완료되지 않습니다.   

7.  **업데이트 포함** 페이지에서 모든 소프트웨어 업데이트를 설치해야 하는지 아니면 소프트웨어 업데이트가 필요하지 않은지를 지정합니다. **다음**을 클릭합니다. 소프트웨어 업데이트를 설치하도록 지정하면 Configuration Manager에서 대상 컴퓨터가 속해 있는 컬렉션을 대상으로 하는 해당 업데이트만을 설치합니다.  

8.  **응용 프로그램 설치** 페이지에서 대상 컴퓨터에 설치할 응용 프로그램을 지정하고 **다음**을 클릭합니다. 둘 이상의 응용 프로그램을 지정하는 경우에는 특정 응용 프로그램 설치가 실패할 경우 작업 순서를 계속할지 여부도 지정하세요.  

9. 마법사를 완료합니다.  


> [!Important]  
> 디바이스에서 작업 순서가 실행되면 Configuration Manager 클라이언트는 다양한 시나리오에서 작업 순서 동작을 제어하도록 여러 스크립트를 만듭니다. 작업 순서가 완료되면 클라이언트는 컴퓨터가 다시 시작 될 때까지 이러한 스크립트를 제거하지 않습니다. 이 스크립트 파일에는 중요한 정보가 들어 있지 않습니다.  


1802 버전부터 Windows 10 내부 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스 전후에 추가할 권장 작업이 있는 추가 그룹이 포함되어 있습니다. 이러한 작업은 디바이스를 Windows 10으로 성공적으로 업그레이드한 많은 고객들에게 공통적으로 적용됩니다. 자세한 내용은 [업그레이드 준비](#recommended-task-sequence-steps-to-prepare-for-upgrade) 및 [사후 처리](#recommended-task-sequence-steps-for-post-processing)를 위한 권장되는 작업 순서 단계를 참조하세요.

1806 버전부터 이 작업 순서 템플릿에는 업그레이드 프로세스가 실패할 경우, 추가할 권장 작업이 있는 그룹도 포함되어 있습니다. 이러한 작업을 수행하면 문제를 더 쉽게 해결할 수 있습니다. 자세한 내용은 [실패 시 권장되는 작업 순서 단계](#recommended-task-sequence-steps-on-failure)를 참조하세요.<!--1358500-->  



## <a name="configure-pre-cache-content"></a>사전 캐시 콘텐츠 구성
<!--1021244--> 작업 순서의 사용 가능한 배포에 대해 사전 캐시 기능을 사용하면 사용자가 작업 순서를 설치하기 전에 클라이언트에서 관련 OS 업그레이드 패키지 콘텐츠를 다운로드할 수 있습니다.  

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  


예를 들어 모든 사용자를 위한 단일 내부 업그레이드 작업 순서만 원하거나 많은 아키텍처 및 언어를 포함할 수 있습니다. 이전 버전에서 사용자가 소프트웨어 센터에서 사용 가능한 작업 순서 배포를 설치할 때 콘텐츠가 다운로드를 시작합니다. 이 지연 때문에 설치를 시작할 준비가 되기 전에 추가 시간이 필요합니다. 또한 작업 순서에서 참조되는 모든 콘텐츠가 다운로드됩니다. 이 콘텐츠에는 모든 언어 및 아키텍처에 대한 OS 업그레이드 패키지가 포함됩니다. 각 업그레이드 패키지의 크기가 약 3GB이면 전체 콘텐츠는 더 큽니다.

사전 캐시 콘텐츠를 사용하면 클라이언트가 배포를 받는 즉시 해당 OS 업그레이드 패키지뿐만 아니라 관련된 다른 모든 콘텐츠를 다운로드할 수 있습니다. 사용자가 소프트웨어 센터에서 **설치**를 클릭하면 콘텐츠가 준비됩니다. 콘텐츠가 로컬 하드 드라이브에 있으므로 설치가 신속하게 시작합니다.

> [!NOTE]  
> 현재 이 동작은 OS 업그레이드 패키지에만 적용됩니다. 해당 패키지는 일치하는 아키텍처 또는 언어를 지정하는 유일한 콘텐츠입니다. 예를 들어 작업 순서가 여러 드라이버 패키지를 참조하는 경우 현재 클라이언트는 모든 패키지를 다운로드합니다. 작업 순서 엔진은 미리 하지 않고 작업 순서가 실행될 때 단계에 대한 조건을 평가합니다. 클라이언트는 패키지 속성에서 태그를 사용하여 사전 캐시되는 내용을 결정합니다.


### <a name="to-configure-the-pre-cache-feature"></a>사전 캐시 기능을 구성하려면

1. 특정 아키텍처 및 언어에 대한 OS 업그레이드 패키지를 만듭니다. 패키지의 **데이터 원본** 탭에서 아키텍처 및 언어를 지정합니다. 언어의 경우 10진수 변환을 사용합니다. 예를 들어 **1033**은 영어의 10진수 값이며, **0x0409**는 동등한 16진수입니다.  

    클라이언트는 아키텍처 및 언어 값을 평가하여 사전 캐시하는 동안 다운로드하는 OS 업그레이드 패키지를 결정합니다.  

2. 다양한 언어 및 아키텍처에 대한 조건부 단계를 사용하여 작업 순서를 만듭니다. 예를 들어 다음 단계는 영어 버전을 사용합니다.  

    ![ENU, DEU 및 JPN에 대한 여러 OS 업그레이드 단계를 보여 주는 작업 순서 편집기](../media/precacheproperties2.png)

    ![로캘 및 OSArchitecture에 대한 WMI WQL 쿼리를 표시하는 작업 순서 편집기, 옵션 탭](../media/precacheoptions2.png)  

3. 작업 순서를 배포합니다. 사전 캐시 기능에 대해 다음 설정을 구성합니다.  

    - **일반** 탭에서 **이 작업 순서에 대한 콘텐츠 사전 다운로드**를 선택합니다.  

    - **배포 설정** 탭에서 해당 작업 순서를 **사용 가능**으로 구성합니다.  

    - **예약** 탭의 **이 배포를 사용할 수 있는 시점 예약** 설정에서 현재 선택된 시간을 선택합니다. 클라이언트는 배포의 사용 가능한 시간에 콘텐츠를 사전 캐시하기 시작합니다. 대상 클라이언트가 이 정책의 수신할 때 사용할 수 있는 시간은 과거입니다. 따라서 미리 캐시 다운로드를 즉시 시작합니다. 클라이언트에서 이 정책을 수신하지만 사용할 수 있는 시간이 나중이면 클라이언트가 사용할 수 있는 시간이 발생할 때까지 콘텐츠를 사전 캐시하기 시작하지 않습니다.  

    - **배포 지점** 탭에서 **배포 옵션** 설정을 구성합니다. 사용자가 설치를 시작하기 전에 콘텐츠가 사전 캐시되지 않은 경우 클라이언트에서 이러한 설정을 사용합니다.  
  

### <a name="user-experience"></a>사용자 환경

- 클라이언트가 배포 정책을 받으면 배포를 사용할 수 있는 시간 이후에 콘텐츠의 사전 캐시를 시작합니다. 이 콘텐츠는 참조되는 모든 패키지를 포함하지만, 패키지의 아키텍처 및 언어 특성과 일치하는 OS 업그레이드 패키지여야 합니다.  

- 클라이언트에서 배포가 사용자에게 제공되면 사용자에게 새로운 배포를 알리는 알림이 표시됩니다. 이제 작업 순서가 소프트웨어 센터에 표시됩니다. 사용자가 소프트웨어 센터로 이동한 다음 **설치**를 클릭하여 설치를 시작합니다.  

- 사용자가 작업 순서를 설치할 때 클라이언트가 콘텐츠를 완전하게 사전 캐시하지 않은 경우 클라이언트는 배포의 **배포 옵션** 탭에서 지정한 설정을 사용합니다.  



## <a name="recommended-task-sequence-steps-to-prepare-for-upgrade"></a>업그레이드 준비를 위한 권장되는 작업 순서 단계

1802 버전부터 Windows 10 내부 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스 전에 추가할 권장 작업이 있는 추가 그룹이 포함되어 있습니다. **업그레이드 준비** 그룹의 이러한 작업은 장치를 Windows 10으로 성공적으로 업그레이드한 많은 고객들에게 공통적으로 적용됩니다. 1802 이전 버전의 사이트에서는 이러한 동작을 **업그레이드 준비** 그룹의 작업 순서에 수동으로 추가합니다.  

- **배터리 확인**: 컴퓨터에서 배터리를 사용하는지 또는 유선 전원을 사용하는지를 확인하려면 이 그룹의 단계를 추가합니다. 이 작업에서 배터리 확인을 수행하려면 사용자 지정 스크립트 또는 유틸리티가 필요합니다.  

- **네트워크/유선 연결 확인**: 컴퓨터가 네트워크에 연결되어 있고 무선 연결을 사용하고 있지 않은지 확인하려면 이 그룹의 단계를 추가합니다. 이 작업에서 배터리 확인을 수행하려면 사용자 지정 스크립트 또는 유틸리티가 필요합니다.  

- **호환되지 않는 응용 프로그램 제거**: 이 Windows 10 버전과 호환되지 않는 응용 프로그램을 제거하려면 이 그룹의 단계를 추가합니다. 응용 프로그램을 제거하는 방법은 다양합니다.  

    - 응용 프로그램이 Windows Installer를 사용하는 경우 응용 프로그램의 Windows Installer 배포 유형 속성에 있는 **프로그램** 탭의 **제거 프로그램** 명령줄을 복사합니다. 그런 다음, 제거 프로그램 명령줄을 사용하여 이 그룹의 **명령줄 실행** 단계를 추가합니다. 예: </br>`msiexec /x {150031D8-1234-4BA8-9F52-D6E5190D1CBA} /q`</br>  

- **호환되지 않는 드라이버 제거**: 이 Windows 10 버전과 호환되지 않는 드라이버를 제거하려면 이 그룹의 단계를 추가합니다.  

- **제거/일시 중단**: 바이러스 백신과 같은 타사 보안 프로그램을 제거하거나 일시 중단하려면 이 그룹의 단계를 추가합니다.  

   - 타사 디스크 암호화 프로그램을 사용하는 경우 `/ReflectDrivers` [명령줄 옵션](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-setup-command-line-options#23)을 사용하여 Windows 설치 프로그램에 해당 암호화 드라이버를 제공합니다. 이 그룹의 작업 순서에 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계를 추가합니다. 작업 순서 변수를 **OSDSetupAdditionalUpgradeOptions**로 설정합니다. 드라이버 경로를 사용하여 값을 `/ReflectDrivers`로 설정합니다. 이 [작업 순서 변수](/sccm/osd/understand/task-sequence-variables#OSDSetupAdditionalUpgradeOptions)는 작업 순서에서 사용되는 Windows 설치 명령줄을 추가합니다. 이 프로세스에 대한 추가 지침은 소프트웨어 공급업체에 문의하세요.  


### <a name="download-package-content-task-sequence-step"></a>패키지 콘텐츠 작업 순서 단계 다운로드  

[패키지 콘텐츠 다운로드](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent) 단계는 다음 시나리오에서 **운영 체제 업그레이드** 단계 이전에 사용합니다.  

-   x86 및 x64 플랫폼에서 단일 업그레이드 작업 순서를 사용합니다. **업그레이드 준비** 그룹에서 두 개의 **패키지 콘텐츠 다운로드** 단계가 포함됩니다. 클라이언트 아키텍처를 감지하는 각 단계에 대한 조건을 설정합니다. 이 조건으로 인해 적절한 OS 업그레이드 패키지만을 다운로드하는 단계가 생성됩니다. 각 **패키지 콘텐츠 다운로드** 단계가 같은 변수를 사용하도록 구성하고 **운영 체제 업그레이드** 단계에서 미디어 경로에 대해 변수를 사용합니다.  

-   해당 드라이버 패키지를 동적으로 다운로드하려면 각 드라이버 패키지에 대해 적합한 하드웨어 종류를 검색하는 조건을 포함하는 두 가지 **패키지 콘텐츠 다운로드** 단계를 사용합니다. 같은 변수를 사용하도록 각 **패키지 콘텐츠 다운로드** 단계를 구성합니다. 그런 다음 **운영 체제 업그레이드** 단계의 드라이버 섹션에서 **준비된 콘텐츠** 값에 해당 변수를 사용합니다.  

    > [!NOTE]  
    > 둘 이상의 패키지가 있는 경우 Configuration Manager에서 변수 이름에 숫자 접미사를 추가합니다. 예를 들어 사용자 지정 변수로 `%mycontent%`를 지정하는 경우 클라이언트는 이 위치에 참조된 모든 콘텐츠를 저장합니다. **운영 체제 업그레이드**와 같은 하위 시퀀스 단계에서 변수를 참조하는 경우 숫자 접미사가 있는 변수를 사용합니다. 이 예제의 `%mycontent01%` 또는 `%mycontent02%`에서 숫자는 **패키지 콘텐츠 다운로드** 단계에서 이 특정 콘텐츠를 나열하는 순서에 해당합니다.  



## <a name="recommended-task-sequence-steps-for-post-processing"></a>사후 처리를 위한 권장되는 작업 순서 단계   

작업 순서를 만든 후 작업 순서의 **사후 처리** 그룹에서 추가적인 단계를 추가합니다.  

> [!NOTE]  
>  이 작업 순서는 선형이 아닙니다. 작업 순서의 결과에 영향을 미칠 수 있는 단계에 대한 조건이 있습니다. 이 동작은 클라이언트 컴퓨터를 성공적으로 업그레이드했는지 또는 원래 OS로 클라이언트 컴퓨터를 롤백해야 하는지 여부에 따라 달라집니다.  

1802 버전부터 Windows 10 내부 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스 후에 추가할 권장 작업이 있는 추가 그룹이 포함되어 있습니다. **사후 처리** 그룹의 이러한 작업은 장치를 Windows 10으로 성공적으로 업그레이드한 많은 고객들에게 공통적으로 적용됩니다. 1802 이전 버전의 사이트에서는 이러한 동작을 **사후 처리** 그룹의 작업 순서에 수동으로 추가합니다.  

- **설치 기반 드라이버 적용**: 패키지에서 설치 기반 드라이버(.exe)를 설치하려면 이 그룹의 단계를 추가합니다.  

- **타사 보안 설치/사용**: 바이러스 백신과 같은 타사 보안 프로그램을 설치하거나 사용하도록 설정하려면 이 그룹의 단계를 추가합니다.  

- **Windows 기본 앱 및 연결 설정**: Windows 기본 앱 및 파일 연결을 설정하려면 이 그룹의 단계를 추가합니다. 먼저 원하는 앱 연결을 사용하여 참조 컴퓨터를 준비합니다. 그런 후에 다음 명령줄을 실행하여 내보냅니다. </br>`dism /online /Export-DefaultAppAssociations:"%UserProfile%\Desktop\DefaultAppAssociations.xml"`</br>패키지에 XML 파일을 추가합니다. 그런 다음, 이 그룹의 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계를 추가합니다. XML 파일이 포함된 패키지를 지정한 후 다음 명령줄을 지정합니다. </br>`dism /online /Import-DefaultAppAssociations:DefaultAppAssocations.xml`</br> 자세한 내용은 [기본 응용 프로그램 연결 내보내기 또는 가져오기](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations)을 참조하세요.  

- **사용자 지정 및 개인 설정 적용**: 프로그램 그룹 구성과 같은 시작 메뉴 사용자 지정을 적용하려면 이 그룹의 단계를 추가합니다. 자세한 내용은 [시작 화면 사용자 지정](/windows-hardware/manufacture/desktop/customize-the-start-screen)을 참조하세요.  



## <a name="optional-task-sequence-steps-for-rollback"></a>롤백을 위한 선택적 작업 순서 단계  

컴퓨터를 다시 시작한 후 업그레이드 프로세스에 문제가 발생하는 경우 Windows 설치 프로그램은 시스템을 이전 OS로 롤백합니다. 그런 다음, 작업 순서는 **롤백** 그룹의 단계를 계속 진행합니다. 작업 순서를 만든 후 필요에 따라 이 그룹의 선택적 단계를 추가합니다. 예를 들어 호환되지 않는 소프트웨어를 제거하는 것처럼 업그레이드 준비 그룹의 시스템에 대한 변경 사항을 되돌립니다.



## <a name="recommended-task-sequence-steps-on-failure"></a>실패 시 권장되는 작업 순서 단계
<!--1358500-->

1806 버전부터 Windows 10 현재 위치 업그레이드의 기본 작업 순서 템플릿에 **실패 시 작업을 실행**할 그룹이 포함되어 있습니다. 이 그룹에는 업그레이드 프로세스가 실패할 경우 추가할 권장 작업이 포함됩니다. 이러한 작업을 수행하면 문제를 더 쉽게 해결할 수 있습니다.

- **로그 수집**: 클라이언트에서 로그를 수집하려면 이 그룹의 단계를 추가합니다.  

    - 일반적으로 로그 파일을 네트워크 공유에 복사합니다. 이 연결을 설정하려면 [네트워크 폴더에 연결](/sccm/osd/understand/task-sequence-steps#BKMK_ConnectToNetworkFolder) 단계를 사용하세요.  

    - 복사 작업을 수행하려면 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 또는 [PowerShell 스크립트 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunPowerShellScript) 단계에서 사용자 지정 스크립트나 유틸리티를 사용합니다.  

    - 수집할 파일에는 다음과 같은 로그가 포함될 수 있습니다.  
         `%_SMSTSLogPath%\*.log`   
         `%SystemDrive%\$Windows.~BT\Sources\Panther\setupact.log`  

    - setupact.log 및 기타 Windows 설치 로그에 대한 자세한 내용은 [Windows Setup Log files](https://docs.microsoft.com/windows/deployment/upgrade/log-files)(Windows 설치 로그 파일)를 참조하세요.  

    - Configuration Manager 클라이언트 로그에 대한 자세한 내용은 [Configuration Manager 클라이언트 로그](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs)를 참조하세요.  

    - **_SMSTSLogPath** 및 기타 유용한 변수에 대한 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables)\(작업 순서 변수\)를 참조하세요.  

- **진단 도구 실행**: 추가 진단 도구를 실행하려면 이 그룹의 단계를 추가합니다. 실패 후 시스템에서 바로 추가 정보를 수집하도록 이러한 도구를 자동화합니다.  

    - 이러한 도구 중 하나는 Windows [SetupDiag](https://docs.microsoft.com/windows/deployment/upgrade/setupdiag)입니다. 이 도구는 Windows 10 업그레이드 실패 이유에 대한 세부 정보를 얻기 위한 독립 실행형 진단 도구입니다.  

        - Configuration Manager에서 도구에 대한 [패키지를 만듭니다](/sccm/apps/deploy-use/packages-and-programs#create-a-package-and-program).  

        - 이 작업 순서 그룹에 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계를 추가합니다. 도구를 참조하려면 **패키지** 옵션을 사용하세요. 다음 문자열은 예제 **명령줄**입니다.  
             `SetupDiag.exe /Output:"%_SMSTSLogPath%\SetupDiagResults.log" /Mode:Online`  



## <a name="additional-recommendations"></a>추가 권장 사항

- [Windows 10 업그레이드 오류를 해결](https://docs.microsoft.com/windows/deployment/upgrade/resolve-windows-10-upgrade-errors)하려면 Windows 설명서를 검토하세요. 이 문서에는 업그레이드 프로세스에 대한 자세한 정보도 포함되어 있습니다.  

- 기본 **확인 준비** 단계에서 **사용 가능한 최소 디스크 공간(MB) 확인**을 사용하도록 설정합니다. 32비트 OS 업그레이드 패키지의 경우 이 값을 **16384**(16GB) 이상으로 설정하고, 64비트의 경우 **20480**(20GB) 이상으로 설정합니다.  

- **SMSTSDownloadRetryCount** [작업 순서 변수](/sccm/osd/understand/task-sequence-variables#SMSTSDownloadRetryCount)를 사용하여 정책 다운로드를 다시 시도합니다. 현재, 클라이언트가 기본적으로 두 번 다시 시도하므로 이 변수는 2로 설정되어 있습니다. 클라이언트가 유선 인트라넷 네트워크 연결을 사용하지 않는 경우 추가로 다시 시도하면 클라이언트가 정책을 가져오는 데 도움이 됩니다. 이 변수를 사용해도 정책을 다운로드할 수 없는 경우 오류가 지연되는 점 이외의 다른 부작용은 없습니다.<!--501016--> 또한 **SMSTSDownloadRetryDelay** 변수를 기본값인 15초에서 늘립니다.  

- 인라인 호환성 평가를 수행합니다.  

   - **업그레이드 준비** 그룹의 초기에 두 번째 **운영 체제 업그레이드** 단계를 추가합니다. 이름을 *업그레이드 평가*로 지정합니다. 동일한 업그레이드 패키지를 지정한 후 **업그레이드를 시작하지 않고 Windows 설치 프로그램 호환성 검사 수행** 옵션을 사용하도록 설정합니다. 옵션 탭에서 **오류 발생 시 계속**을 사용하도록 설정합니다.  

   - 이 *업그레이드 평가* 단계 바로 뒤에 **명령줄 실행** 단계를 추가합니다. 다음 명령줄을 지정합니다.</br> `cmd /c exit %_SMSTSOSUpgradeActionReturnCode%`</br>**옵션** 탭에서 다음 조건을 추가합니다. </br>`Task Sequence Variable _SMSTSOSUpgradeActionReturnCode not equals 3247440400` </br>이 반환 코드는 문제없이 호환성 검사에 성공하는 MOSETUP_E_COMPAT_SCANONLY(0xC1900210)에 해당하는 10진 코드입니다. *업그레이드 평가* 단계가 성공하고 이 코드를 반환하는 경우 작업 순서는 이 단계를 건너뜁니다. 또는 평가 단계가 다른 반환 코드를 반환하는 경우 이 단계에서 작업 순서가 실패하고 Windows 설치 호환성 검사의 반환 코드가 표시됩니다. **_SMSTSOSUpgradeActionReturnCode**에 대한 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSOSUpgradeActionReturnCode)\(작업 순서 변수\)를 참조하세요.  

   - 자세한 내용은 [운영 체제 업그레이드](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS)를 참조하세요.  

- 이 작업 순서 중에 디바이스를 BIOS에서 UEFI로 변경하려는 경우 [현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)을 참조하세요.  

- BitLocker 디스크 암호화를 사용하는 경우 기본 Windows 설치 프로그램은 업그레이드 중 자동으로 일시 중단합니다. Windows 10 버전 1803부터 Windows 설치 프로그램에는 이 동작을 제어할 `/BitLocker` 명령줄 매개 변수가 포함되어 있습니다. 보안 요구 사항에 따라 활성 디스크 암호화를 항상 유지해야 하는 경우 **업그레이드 준비** 그룹에서 **OSDSetupAdditionalUpgradeOptions** [작업 순서 변수](/sccm/osd/understand/task-sequence-variables#OSDSetupAdditionalUpgradeOptions)를 사용하여 `/BitLocker TryKeepActive`를 포함합니다. 자세한 내용은 [Windows 설치 프로그램 명령줄 옵션](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-setup-command-line-options#33)을 참조하세요.<!--SCCMDocs issue #494-->  

- 일부 고객은 Windows 10의 프로비전된 기본 앱(예: Bing 날씨 앱 또는 Microsoft Solitaire Collection)을 제거합니다. 이러한 앱은 경우에 따라 Windows 10 업데이트 후 복귀됩니다. 자세한 내용은 [Windows 10에서 앱을 제거된 상태로 유지하는 방법](https://docs.microsoft.com/windows/application-management/remove-provisioned-apps-during-update)을 참조하세요. **명령줄 실행** 단계를 **업그레이드 준비** 그룹의 작업 순서에 추가합니다. 다음 예와 유사하게 명령줄을 지정합니다.</br> `cmd /c reg delete "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Appx\AppxAllUserStore\Deprovisioned\Microsoft.BingWeather_8wekyb3d8bbwe" /f` <!--SCCMDocs issue #526-->  
