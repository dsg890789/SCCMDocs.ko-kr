---
title: OS 업그레이드 패키지 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 OS 업그레이드 패키지를 관리하는 방법을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 49c402bcf88bbfde20acb5e52db5a520aa794a4d
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821293"
---
# <a name="manage-os-upgrade-packages-with-configuration-manager"></a>Configuration Manager에서 OS 업그레이드 패키지 관리

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 OS 업그레이드 패키지에는 컴퓨터의 기존 OS를 업그레이드하는 데 사용되는 Windows 설치 원본 파일이 포함되어 있습니다. 이 문서에는 OS 업그레이드 패키지를 추가, 배포 및 서비스하는 방법을 설명합니다.

> [!NOTE]
> 새 Windows 설치에도 OS 업그레이드 패키지가 사용될 수 있습니다. 그러나 이 방법에 사용할 수 있는 드라이버에 따라 달라질 수 있습니다. OS 업그레이드 패키지에서 새 Windows 설치를 수행하면 Windows PE에서 드라이버가 설치되거나 드라이버가 단지 삽입만 됩니다. 일부 드라이버는 Windows PE에서 설치되지 않습니다. Windows PE에서 드라이버를 설치할 수 없는 경우 **install.wim** 같은 [OS 이미지](/configmgr/osd/get-started/manage-operating-system-images)를 대신 사용하세요.

## <a name="BKMK_AddOSUpgradePkgs"></a> OS 업그레이드 패키지 추가  

OS 업그레이드 패키지를 사용하려면 먼저 Configuration Manager 사이트에 추가해야 합니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **운영 체제**를 확장한 다음, **운영 체제 업그레이드 패키지** 노드를 선택합니다.  

2. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **운영 체제 업그레이드 패키지 추가**를 선택합니다. 그러면 운영 체제 업그레이드 추가 마법사가 시작됩니다.  

3. **데이터 원본** 페이지에서 다음과 같은 설정을 지정합니다.

    - OS 업그레이드 패키지의 설치 원본 파일에 대한 네트워크 **경로**. 예: `\\server\share\path`  

        > [!NOTE]  
        >  설치 원본 파일에는 OS를 설치하는 setup.exe와 다른 파일 및 폴더가 포함되어 있습니다.  

        > [!IMPORTANT]  
        >  원치 않는 변조를 방지하기 위해 이러한 설치 원본 파일에 대한 액세스가 제한됩니다.  

    - **선택한 업그레이드 패키지의 설치 .wim 파일에서 특정 이미지 인덱스를 추출한** 다음 목록에서 이미지 인덱스를 선택 합니다.<!--4931110--> 버전 1910부터 이 옵션은 파일의 모든 이미지 인덱스가 아닌 단일 인덱스를 자동으로 가져옵니다. 이 옵션을 사용하면 이미지 파일이 작아지고 오프라인 서비스가 빨라집니다. 소프트웨어 업데이트를 적용한 후 작은 이미지 파일에 대해 [이미지 서비스 최적화](#bkmk_resetbase)를 위한 프로세스도 지원합니다.  

        > [!IMPORTANT]  
        > Configuration Manager는 OS 업그레이드 패키지의 기존 설치 .wim을 덮어씁니다. 이미지 인덱스를 임시 위치로 추출한 다음, 원래 원본 디렉터리로 이동합니다. OS 업그레이드 패키지를 가져오고 이 옵션을 사용하도록 설정하기 전에, 원래 원본 파일을 백업해야 합니다.

    - 클라이언트에서 콘텐츠를 사전 캐시하려는 경우 이미지의 **아키텍처** 및 **언어**를 지정합니다. 자세한 내용은 [사전 캐시 콘텐츠 구성](/configmgr/osd/deploy-use/configure-precache-content)을 참조하세요.  

4. **일반** 페이지에서 다음 정보를 지정합니다. 이 정보는 OS 업그레이드 패키지가 여러 개인 경우 목적을 식별하는 데 유용합니다.  

    - **이름**: OS 업그레이드 패키지에 사용할 고유 이름입니다.  

    - **버전**: 선택적 버전 식별자입니다. 이 속성은 업그레이드 패키지의 OS 버전이 아니어도 됩니다. 패키지에 대한 조직의 버전인 경우가 많습니다.  

    - **설명**: 선택적 간략한 설명입니다.  

5. 마법사를 완료합니다.  

다음으로, OS 업그레이드 패키지를 배포 지점에 배포합니다.  

## <a name="BKMK_Distribute"></a> 배포 지점에 콘텐츠 배포  

OS 업그레이드 패키지를 다른 콘텐츠와 동일한 배포 지점에 배포합니다. 작업 순서를 배포하기 전에 OS 업그레이드 패키지를 최소 하나의 배포 지점에 배포합니다. 자세한 내용은 [콘텐츠 배포](/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.  

[!INCLUDE [Apply software updates to an image](includes/wim-apply-updates.md)]

## <a name="next-steps"></a>다음 단계

[OS를 업그레이드하는 작업 순서 만들기](/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)
