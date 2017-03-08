---
title: "운영 체제를 업그레이드하는 작업 순서 만들기 | Microsoft 문서"
description: "System Center Configuration Manager에서 작업 순서를 사용하여 Windows 7 이상 운영 체제를 Windows 10으로 자동으로 업그레이드할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: 12
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 32af7da62bfe767a21a891338bd778ebf45f2685
ms.lasthandoff: 12/16/2016


---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 운영 체제를 업그레이드하는 작업 순서 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 작업 순서를 사용하여 대상 컴퓨터의 Windows 7 이상 운영 체제를 Windows 10으로 자동으로 업그레이드할 수 있습니다. 대상 컴퓨터에 설치할 운영 체제 이미지 및 그 밖의 추가 콘텐츠(예: 설치하려는 응용 프로그램 또는 소프트웨어 업데이트)를 참조하는 작업 순서를 만듭니다. 운영 체제를 업그레이드하는 작업 순서는 [최신 버전으로 Windows 업그레이드](upgrade-windows-to-the-latest-version.md) 시나리오의 일부입니다.  

##  <a name="BKMK_UpgradeOS"></a> 운영 체제를 업그레이드하는 작업 순서 만들기  
 컴퓨터의 운영 체제를 Windows 10으로 업그레이드하려면 작업 순서 만들기 마법사에서 작업 순서를 만들고 **업그레이드 패키지에서 운영 체제 업그레이드** 를 선택합니다. 마법사는 운영 체제를 업그레이드하고, 소프트웨어 업데이트를 적용하고, 응용 프로그램을 설치하는 단계를 추가합니다. 작업 순서를 만들려면 먼저 다음이 준비되어야 합니다.  

-   **필수**  

     - Windows 10 [운영 체제 업그레이드 패키지](../get-started/manage-operating-system-upgrade-packages.md)를 Configuration Manager 콘솔에서 사용할 수 있어야 합니다.  

-   **필수(사용될 경우)**  

    -   Configuration Manager 콘솔에서 [소프트웨어 업데이트](../../sum/get-started/synchronize-software-updates.md)를 동기화해야 합니다.  

    -   Configuration Manager 콘솔에 [응용 프로그램](../../apps/deploy-use/create-applications.md)을 추가해야 합니다.  

#### <a name="to-create-a-task-sequence-that-upgrades-an-operating-system"></a>운영 체제를 업그레이드하는 작업 순서를 만들려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **작업 순서 만들기** 를 클릭하여 작업 순서 만들기 마법사를 시작합니다.  

4.  **새 작업 순서 만들기** 페이지에서 **업그레이드 패키지에서 운영 체제 업그레이드**를 클릭하고 **다음**을 클릭합니다.  

5.  **작업 순서 정보** 페이지에서 다음 설정을 지정한 후에 **다음**을 클릭합니다.  

    -   **작업 순서 이름**: 작업 순서를 식별하는 이름을 지정합니다.  

    -   **설명**: 작업 순서를 통해 수행되는 작업에 대한 설명을 지정합니다.  

6.  **Windows 운영 체제 업그레이드** 페이지에서 다음 설정을 지정한 후 **다음**을 클릭합니다.  

    -   **업그레이드 패키지**: 운영 체제 업그레이드 원본 파일이 포함된 업그레이드 패키지를 지정합니다. **속성** 창에서 해당 정보를 확인하여 올바른 업그레이드 패키지를 선택했는지 알아볼 수 있습니다. 자세한 내용은 [운영 체제 업그레이드 패키지 관리](../get-started/manage-operating-system-upgrade-packages.md)를 참조하세요.  

    -   **버전 인덱스**: 패키지에서 사용할 수 있는 운영 체제 버전 인덱스가 여러 개 있는 경우 원하는 버전 인덱스를 선택합니다. 기본적으로 첫 번째 항목이 선택되어 있습니다.  

    -   **제품 키**: 설치할 Windows 운영 체제의 제품 키를 지정합니다. 인코딩된 볼륨 라이선스와 표준 제품 키를 지정할 수 있습니다. 인코딩되지 않은 제품 키를 사용할 경우 5자로 이루어진 각 그룹을 대시(-)로 구분해야 합니다. 예: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX* 볼륨 라이선스 버전용 업그레이드의 경우에는 제품 키가 필요하지 않습니다. 정품 Windows 버전용 업그레이드의 경우에만 제품 키가 필요합니다.  

7.  **업데이트 포함** 페이지에서 필수 소프트웨어 업데이트를 설치할지, 모든 소프트웨어 업데이트를 설치할지, 아니면 소프트웨어 업데이트를 설치하지 않을지를 지정한 후 **다음**을 클릭합니다. 소프트웨어 업데이트를 설치하도록 지정하면 Configuration Manager에서 대상 컴퓨터가 속해 있는 컬렉션을 대상으로 하는 소프트웨어 업데이트만 설치합니다.  

8.  **응용 프로그램 설치** 페이지에서 대상 컴퓨터에 설치할 응용 프로그램을 지정하고 **다음**을 클릭합니다. 여러 응용 프로그램을 지정하는 경우 특정 응용 프로그램 설치가 실패할 경우 작업 순서가 계속되도록 지정할 수 있습니다.  

9. 마법사를 완료합니다.  

## <a name="download-package-content-task-sequence-step"></a>패키지 콘텐츠 작업 순서 단계 다운로드  
 [패키지 콘텐츠 다운로드](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) 단계는 다음 시나리오에서 **운영 체제 업그레이드** 단계 이전에 사용할 수 있습니다.  

-   x86 및 x64 플랫폼에서 둘 다 사용 가능한 단일 업그레이드 작업 순서를 사용하는 경우. 이렇게 하려면 클라이언트 아키텍처를 검색하여 적합한 운영 체제 업그레이드 패키지만 다운로드하는 조건을 포함하는 두 가지 **패키지 콘텐츠 다운로드** 단계를 **업그레이드 준비** 그룹에 포함합니다. 각 **패키지 콘텐츠 다운로드** 단계가 같은 변수를 사용하도록 구성하고 **운영 체제 업그레이드** 단계에서 미디어 경로에 대해 변수를 사용합니다.  

-   해당 드라이버 패키지를 동적으로 다운로드하려면 각 드라이버 패키지에 대해 적합한 하드웨어 종류를 검색하는 조건을 포함하는 두 가지 **패키지 콘텐츠 다운로드** 단계를 사용합니다. 같은 변수 및 **운영 체제 업그레이드** 단계의 드라이버 섹션에서 **준비된 콘텐츠** 값에 대한 변수를 사용하여 각 **패키지 콘텐츠 다운로드** 단계를 구성합니다.  

   > [!NOTE]
   > 둘 이상의 패키지가 있는 경우 Configuration Manager에서 변수 이름에 숫자 접미사를 추가합니다. 예를 들어 사용자 지정 변수로 %mycontent% 변수를 지정하는 경우 이는 모든 참조된 콘텐츠가 저장된 위치(여러 패키지일 수 있음)의 루트입니다. 운영 체제 업그레이드와 같은 하위 시퀀스 단계에서 변수를 참조하는 경우 숫자 접미사와 함께 사용됩니다. 이 예제에서는 %mycontent01% 또는 %mycontent02%이고, 숫자는 패키지가 이 단계에서 나열되는 순서에 해당합니다.

## <a name="optional-post-processing-task-sequence-steps"></a>선택적 사후 처리 작업 순서 단계  
 작업 순서를 만든 후에는 알려진 호환성 문제가 있는 응용 프로그램을 제거하는 단계 등의 단계를 더 추가하거나, 컴퓨터가 다시 시작되고 Windows 10으로 정상적으로 업그레이드한 후에 실행할 사후 처리 작업을 추가할 수 있습니다. 작업 순서의 사후 처리 그룹에 이러한 단계를 더 추가합니다.  

> [!NOTE]  
>  이 작업 순서는 선형이 아니므로 클라이언트 컴퓨터가 정상적으로 업그레이드되는지 아니면 업그레이드를 시작했던 운영 체제 버전으로 클라이언트 컴퓨터를 롤백해야 하는지에 따라 작업 순서 결과에 영향을 주는 단계에 대한 조건이 있습니다.  

## <a name="optional-rollback-task-sequence-steps"></a>선택적 롤백 작업 순서 단계  
 컴퓨터를 다시 시작한 후 업그레이드 프로세스에 문제가 발생하는 경우 설치 프로그램은 업그레이드를 이전 운영 체제로 롤백하며 작업 순서는 롤백 그룹의 단계를 계속 진행합니다. 작업 순서를 만든 후에 롤백 그룹에 선택적 단계를 추가할 수 있습니다.  

## <a name="folder-and-files-removed-after-computer-restart"></a>컴퓨터 다시 시작 후 폴더 및 파일 제거됨  
 운영 체제를 Windows 10으로 업그레이드하는 작업 순서와 작업 순서의 다른 모든 단계가 완료되어도 컴퓨터를 다시 시작하기 전에는 사후 처리 및 롤백 스크립트가 제거되지 않습니다.  이 스크립트 파일에는 중요한 정보가 들어 있지 않습니다.  

