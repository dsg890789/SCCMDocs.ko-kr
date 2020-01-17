---
title: 미디어 캡처 만들기
titleSuffix: Configuration Manager
description: Configuration Manager의 미디어 캡처를 사용하여 참조 컴퓨터에서 OS 이미지를 캡처합니다.
ms.date: 05/02/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 10eb8958-3848-49d7-95c0-16119b624580
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5a6e76fea130329dcf812f9d18c7575c019da36a
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825458"
---
# <a name="create-capture-media"></a>미디어 캡처 만들기

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 미디어 캡처를 사용하면 참조 컴퓨터에서 OS 이미지를 캡처할 수 있습니다. 미디어 캡처에는 참조 컴퓨터를 시작하는 부팅 이미지와, OS 이미지를 캡처하는 작업 순서가 포함되어 있습니다. 이 시나리오의 경우 미디어 캡처를 사용하여 [OS를 캡처하는 작업 순서를 만듭니다](/sccm/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system).  


## <a name="prerequisites"></a>전제 조건

작업 순서 미디어 만들기 마법사를 사용하여 미디어 캡처를 만들려면 먼저 다음 조건을 모두 충족해야 합니다.

### <a name="boot-image"></a>부팅 이미지

OS를 배포하는 작업 순서에서 사용할 부팅 이미지에 대한 다음 사항을 고려하세요.

- 부팅 이미지의 아키텍처는 대상 컴퓨터의 아키텍처에 적합해야 합니다. 예를 들어 x64 대상 컴퓨터는 x86 또는 x64 부팅 이미지를 부팅하고 실행할 수 있습니다. 그러나 x86 대상 컴퓨터는 x86 부팅 이미지만 부팅하고 실행할 수 있습니다.
- 부팅 이미지에 대상 컴퓨터를 프로비저닝하는 데 필요한 네트워크 드라이버와 스토리지 드라이버가 포함되어 있어야 합니다.

### <a name="distribute-all-content-associated-with-the-task-sequence"></a>작업 순서와 관련된 모든 콘텐츠 배포

작업 순서에 필요한 모든 콘텐츠를 하나 이상의 배포 지점에 배포합니다. 이 콘텐츠에는 부팅 이미지, OS 이미지 및 관련된 기타 파일이 포함됩니다. 마법사는 미디어 캡처를 만들 때 배포 지점에서 콘텐츠를 수집합니다.

사용자 계정에는 해당 배포 지점의 콘텐츠 라이브러리에 대해 적어도 **읽기** 액세스 권한이 있어야 합니다. 자세한 내용은 [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.

### <a name="prepare-the-removable-usb-drive"></a>이동식 USB 드라이브 준비

이동식 USB 드라이브를 사용하는 경우 작업 순서 미디어 만들기 마법사를 실행할 컴퓨터에 연결합니다. 이 USB 드라이브는 Windows에서 이동식 디바이스로 검색되어야 합니다. 마법사는 USB 드라이브에 직접 기록하여 미디어를 만듭니다.

### <a name="create-an-output-folder"></a>출력 폴더 만들기

작업 순서 미디어 만들기 마법사를 실행하여 CD 또는 DVD 세트에 미디어를 만들려면 생성할 출력 파일의 폴더를 만듭니다. CD 또는 DVD 세트용 미디어를 만드는 경우 해당 폴더에 .ISO 파일로 직접 기록됩니다.


## <a name="process"></a>프로세스

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장하고 **작업 순서** 노드를 선택합니다.  

2. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **작업 순서 미디어 만들기**를 선택합니다. 이 작업은 작업 순서 미디어 만들기 마법사를 시작합니다.  

3. **미디어 유형 선택** 페이지에서 **미디어 캡처**를 선택합니다.  

4. **미디어 유형** 페이지에서 미디어가 **이동식 USB 드라이브**인지, **CD/DVD 세트**인지 지정합니다. 그런 후 다음 옵션을 구성합니다.  

    > [!IMPORTANT]  
    > 미디어는 FAT32 파일 시스템을 사용합니다. 콘텐츠가 4GB 이상인 파일을 포함하는 USB 드라이브에는 독립 실행형 미디어를 만들 수 없습니다.  

    - **이동식 USB 드라이브**를 선택하는 경우 콘텐츠를 저장할 드라이브를 선택합니다.  

        - **이동식 USB 드라이브 포맷(FAT32) 및 부팅 가능하도록 구성**: 기본적으로 Configuration Manager를 통해 USB 드라이브를 준비합니다. 많은 최신 UEFI 디바이스에 부팅 가능한 FAT32 파티션이 필요합니다. 그러나 이 포맷은 파일의 크기와 드라이브의 전체 용량도 제한합니다. 이동식 드라이브를 이미 포맷하고 구성한 경우에는 이 옵션을 사용하지 않도록 설정합니다.

    - **CD/DVD 세트**를 선택하는 경우 미디어 용량(**미디어 크기**) 및 출력 파일(**미디어 파일**)의 이름과 경로를 지정해야 합니다. 마법사에서 출력 파일을 이 위치에 기록합니다. `\\servername\folder\outputfile.iso`  

        미디어 용량이 부족하여 전체 콘텐츠를 저장하지 못하는 경우 여러 파일을 만듭니다. 그런 다음 여러 CD 또는 DVD에 콘텐츠를 저장해야 합니다. 여러 미디어 파일이 필요한 경우 Configuration Manager는 생성된 각 출력 파일의 이름에 일련 번호를 추가합니다.  

        > [!IMPORTANT]  
        > 기존 .iso 이미지를 선택하는 경우 작업 순서 미디어 만들기 마법사는 다음 페이지로 진행된 후 바로 드라이브나 공유에서 해당 이미지를 삭제합니다. 기존 이미지는 이후에 마법사를 취소하는 경우라도 삭제됩니다.  

    - **준비 폴더**<!--1359388-->: 미디어 만들기 프로세스에는 임시 드라이브 공간이 많이 필요할 수 있습니다. 기본적으로 이 위치는 다음 경로 `%UserProfile%\AppData\Local\Temp`와 유사합니다. 버전 1902부터, 이러한 임시 파일의 저장 위치를 보다 유연하게 지정할 수 있도록 이 값을 다른 드라이브 및 경로로 변경할 수 있습니다.  

    - **미디어 레이블**<!--1359388-->: 버전 1902부터 작업 순서 미디어에 레이블을 추가합니다. 이 레이블을 통해 미디어를 만든 후 미디어를 보다 잘 식별할 수 있습니다. 기본값은 `Configuration Manager`입니다. 이 텍스트 필드는 다음 위치에 나타납니다.  

        - ISO 파일을 탑재하는 경우 Windows는 탑재된 드라이브의 이름으로 이 레이블을 표시합니다.  

        - USB 드라이브를 포맷하는 경우 해당 이름으로 레이블의 처음 11자를 사용합니다.  

        - Configuration Manager는 미디어의 루트에 `MediaLabel.txt`라는 텍스트 파일을 작성합니다. 기본적으로 파일은 텍스트: `label=Configuration Manager`의 한 줄을 포함합니다. 미디어에 대한 레이블을 사용자 지정하는 경우 이 줄은 기본값 대신 사용자 지정 레이블을 사용합니다.  

    - **미디어에 autorun.inf 파일 포함**<!-- 4090666 -->: 버전 1906부터 Configuration Manager는 기본적으로 autorun.inf 파일을 추가하지 않습니다. 이 파일은 일반적으로 맬웨어 방지 제품에서 차단됩니다. Windows의 자동 실행 기능에 대한 자세한 내용은 [자동 실행 가능한 CD-ROM 애플리케이션 만들기](https://docs.microsoft.com/windows/desktop/shell/autoplay)를 참조하세요. 시나리오에 여전히 필요한 경우 이 옵션을 선택하여 해당 파일을 포함합니다.  

5. **부팅 이미지** 페이지에서 다음 옵션을 지정합니다.  

    > [!IMPORTANT]  
    > 배포되는 부팅 이미지의 아키텍처는 대상 컴퓨터의 아키텍처에 적합해야 합니다. 예를 들어 x64 대상 컴퓨터는 x86 또는 x64 부팅 이미지를 부팅하고 실행할 수 있습니다. 그러나 x86 대상 컴퓨터는 x86 부팅 이미지만 부팅하고 실행할 수 있습니다.  

    - **부팅 이미지**: 대상 컴퓨터를 시작할 부팅 이미지를 선택합니다.  

    - **배포 지점**: 부팅 이미지가 있는 배포 지점을 선택합니다. 마법사는 배포 지점에서 부팅 이미지를 검색하여 미디어에 기록합니다.  

        > [!NOTE]  
        > 사용자 계정에는 배포 지점의 콘텐츠 라이브러리에 대해 적어도 **읽기** 권한이 있어야 합니다.  

6. 마법사를 완료합니다.  


## <a name="next-steps"></a>다음 단계

[OS를 캡처하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system)
