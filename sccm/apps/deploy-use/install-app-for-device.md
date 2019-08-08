---
title: 디바이스용 애플리케이션 설치
titleSuffix: Configuration Manager
description: 컬렉션 없이 장치에 응용 프로그램을 즉시 설치 하려면 Configuration Manager을 사용 합니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: c2a71fca-8744-4d72-abf9-9d8c5d2afb00
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ba68dc78f289b779a157398e9487b637318788c6
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537691"
---
# <a name="install-applications-for-a-device"></a>디바이스용 애플리케이션 설치

<!--4402180-->

1906 버전부터는 Configuration Manager 콘솔에서 실시간으로 디바이스에 애플리케이션을 설치할 수 있습니다. 이 기능을 사용하면 애플리케이션마다 별도의 컬렉션이 필요하지 않습니다.

## <a name="prerequisites"></a>필수 구성 요소

- [선택적 기능](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)인 **디바이스당 사용자에 대한 응용 프로그램 요청 승인**을 사용하도록 설정합니다.  

- 장치 컬렉션에 *사용할 수 있는* [응용 프로그램을 배포](/sccm/apps/deploy-use/deploy-applications) 합니다.  

    - 배포 마법사의 **배포 설정** 페이지에서 다음 옵션을 선택 합니다. 관리자가 **장치에서이 응용 프로그램에 대 한 요청을 승인 해야**합니다.  

        > [!Note]  
        > 이러한 배포 설정을 사용 하면 클라이언트에 정책이 전송 되지 않습니다. 앱이 소프트웨어 센터에서 사용할 수 있는 것으로 표시 되지 않으며 사용자가이 배포를 사용 하 여 앱을 설치할 수 없습니다. 이 작업을 사용하여 앱을 설치한 뒤에는 사용자가 실행할 수 있고 소프트웨어 센터에서 설치 상태를 볼 수 있습니다.

- 사용자 계정에 다음 사용 권한이 있어야 합니다.

    - **응용 프로그램**: 읽기, 승인

    - **컬렉션**: 읽기, 리소스 읽기, 리소스 수정, 수집 된 파일 보기

    예를 들어 **애플리케이션 관리자** 기본 제공 역할에는 이 권한이 있습니다.


## <a name="process"></a>프로세스

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동하고 **디바이스** 노드를 선택합니다. 대상 디바이스를 선택한 다음, 리본 메뉴에서 **애플리케이션 설치** 작업을 선택합니다.

1. 목록에서 하나 이상의 애플리케이션을 선택합니다. 이 목록에는 필수 구성 요소 설정을 사용 하 여 이미 배포 된 응용 프로그램만 표시 됩니다.

이 작업은 디바이스에 비리 배포된 선택한 애플리케이션의 설치를 트리거합니다.

승인 요청 상태를 보려면 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 펼친 다음, **애플리케이션 요청** 노드를 선택합니다.

**모니터링** 작업 영역의 **배포** 노드에서 일반적인 방법으로 앱 설치를 모니터링합니다.


## <a name="see-also"></a>참고 항목

[애플리케이션 승인](/sccm/apps/deploy-use/app-approval)
