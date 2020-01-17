---
title: 애플리케이션 제거
titleSuffix: Configuration Manager
description: Configuration Manager를 사용 하 여 응용 프로그램 제거
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 0ea3edaa-27c6-4391-9896-cd97d9c5d06d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: dc8268ede9ecf43329cf37f789a7fe99e13635b8
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75817859"
---
# <a name="uninstall-applications-with-configuration-manager"></a>Configuration Manager를 사용하여 애플리케이션 제거

*적용 대상: Configuration Manager(현재 분기)*


이전에 배포한 애플리케이션을 제거하려면 다음 작업을 수행합니다.

-   배포 유형 만들기 마법사의 **콘텐츠** 페이지에서 배포 유형 콘텐츠를 제거하도록 명령줄을 지정합니다.  

-   **제거**배포 작업을 사용하여 애플리케이션을 배포합니다.  

> [!IMPORTANT]  
> 일부 애플리케이션 유형은 제거를 지원하지 않습니다.  

 이 목록은 애플리케이션 제거가 작동하는 방식에 대한 자세한 정보를 제공합니다.  

-   Configuration Manager(Configuration Manager) 애플리케이션을 제거할 때 종속된 애플리케이션은 자동으로 제거되지 않습니다.  

-   **제거** 작업을 사용하는 애플리케이션을 사용자에게 배포하고 컴퓨터의 모든 사용자를 위해 애플리케이션을 설치한 경우, 사용자 계정에 애플리케이션 제거 권한이 없으면 제거가 실패할 수 있습니다.  

-   애플리케이션이 배포되어 있는 컬렉션에서 사용자 또는 디바이스를 제거하는 경우 해당 애플리케이션이 디바이스에서 자동으로 제거되지 않습니다.  

-   배포 목적이 **제거** 인 배포는 요구 사항 규칙을 확인하지 않습니다. 애플리케이션이 배포가 실행되는 컴퓨터에 설치된 경우 제거됩니다.  

> [!IMPORTANT]  
> 제거 작업으로 애플리케이션을 배포하려면 먼저 기존 애플리케이션 배포, 시뮬레이션된 배포 또는 이 애플리케이션을 포함하는 작업 순서 배포를 삭제해야 합니다. 

 배포 유형을 만드는 방법에 대한 자세한 내용은 [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.  

 애플리케이션을 배포하는 방법에 대한 자세한 내용은 [애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.  

## <a name="uninstall-an-application"></a>애플리케이션 제거  

1.  다음 방법 중 하나를 사용하여 제거 명령줄에 애플리케이션 배포 유형을 구성합니다.  

    -   배포 만들기 마법사의 **일반** 페이지에서 **설치 파일에서 이 배포 유형에 대한 정보 자동 확인** 옵션을 선택합니다. 설치 파일에서 해당 정보를 사용할 수 없는 경우 제거 명령줄이 배포 유형 속성에 자동으로 추가됩니다.  

    -   배포 유형 만들기 마법사의 **콘텐츠** 페이지에 있는 **제거 프로그램** 필드에서 애플리케이션을 제거하도록 명령줄을 지정합니다.  

        > [!NOTE]  
        >  **콘텐츠** 페이지는 배포 유형 만들기 마법사의 **일반** 페이지에서 **배포 유형 정보 수동 지정** 옵션을 선택한 경우에만 표시됩니다.  

    -   **<*배포 유형 이름*&gt; 속성** 대화 상자의 **프로그램** 탭에 있는 **프로그램 제거** 필드에서 애플리케이션을 제거하도록 명령줄을 지정합니다.  

2.  애플리케이션을 배포한 다음 소프트웨어 배포 마법사의 **배포 설정** 페이지에서 **제거** 배포 작업을 선택합니다.  

    > [!NOTE]  
    >  **제거**배포 작업을 선택하면 배포 목적이 자동으로 **필수**로 구성됩니다.  
