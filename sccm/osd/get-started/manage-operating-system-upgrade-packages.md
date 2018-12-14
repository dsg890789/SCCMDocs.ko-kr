---
title: OS 업그레이드 패키지 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 OS 업그레이드 패키지를 관리하는 방법을 알아봅니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f7b8b18cbec5a3b5972a448e8a70339533dc11fb
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52456012"
---
# <a name="manage-os-upgrade-packages-with-configuration-manager"></a>Configuration Manager에서 OS 업그레이드 패키지 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 OS 업그레이드 패키지에는 컴퓨터의 기존 OS를 업그레이드하는 데 사용되는 Windows 설치 원본 파일이 포함되어 있습니다. 이 문서에는 OS 업그레이드 패키지를 추가, 배포 및 서비스하는 방법을 설명합니다.



##  <a name="BKMK_AddOSUpgradePkgs"></a> OS 업그레이드 패키지 추가  

OS 업그레이드 패키지를 사용하려면 먼저 Configuration Manager 사이트에 추가해야 합니다. 

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **운영 체제**를 확장한 다음, **운영 체제 업그레이드 패키지** 노드를 선택합니다.  

2.  리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **운영 체제 업그레이드 패키지 추가**를 선택합니다. 그러면 운영 체제 업그레이드 추가 마법사가 시작됩니다.  

3.  **데이터 원본** 페이지에서 다음과 같은 설정을 지정합니다. 

    - OS 업그레이드 패키지의 설치 원본 파일에 대한 네트워크 **경로**. 예: `\\server\share\path`  

        > [!NOTE]  
        >  설치 원본 파일에는 OS를 설치하는 setup.exe와 다른 파일 및 폴더가 포함되어 있습니다.  

        > [!IMPORTANT]  
        >  원치 않는 변조를 방지하기 위해 이러한 설치 원본 파일에 대한 액세스가 제한됩니다.  

    - 클라이언트에서 콘텐츠를 사전 캐시하려는 경우 이미지의 **아키텍처** 및 **언어**를 지정합니다. 자세한 내용은 [사전 캐시 콘텐츠 구성](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)을 참조하세요.  

4.  **일반** 페이지에서 다음 정보를 지정합니다. 이 정보는 OS 업그레이드 패키지가 여러 개인 경우 목적을 식별하는 데 유용합니다.  

    -   **이름**: OS 업그레이드 패키지에 사용할 고유 이름입니다.  

    -   **버전**: 선택적 버전 식별자입니다. 이 속성은 업그레이드 패키지의 OS 버전이 아니어도 됩니다. 패키지에 대한 조직의 버전인 경우가 많습니다.  

    -   **주석**: 선택적 간략한 설명입니다.  

5.  마법사를 완료합니다.  


다음으로, OS 업그레이드 패키지를 배포 지점에 배포합니다.  



##  <a name="BKMK_Distribute"></a> 배포 지점에 콘텐츠 배포  

OS 업그레이드 패키지를 다른 콘텐츠와 동일한 배포 지점에 배포합니다. 작업 순서를 배포하기 전에 OS 업그레이드 패키지를 최소 하나의 배포 지점에 배포합니다. 자세한 내용은 [콘텐츠 배포](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)를 참조하세요.  



[!INCLUDE [Apply software updates to an image](includes/wim-apply-updates.md)]



## <a name="next-steps"></a>다음 단계

[OS를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)