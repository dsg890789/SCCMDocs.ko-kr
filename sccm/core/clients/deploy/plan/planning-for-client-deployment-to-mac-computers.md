---
title: Mac 컴퓨터에 클라이언트 배포 계획
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 Mac 컴퓨터에 클라이언트 배포를 계획합니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 05268780bd6dc3b86052b694f360065f8f70d6e6
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332368"
---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Mac 컴퓨터에 클라이언트 배포 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

Mac OS X 운영 체제를 실행하는 Mac 컴퓨터에 Configuration Manager 클라이언트를 설치하고 다음 관리 기능을 사용할 수 있습니다.  

-   **하드웨어 인벤토리**  

     Configuration Manager 하드웨어 인벤토리를 사용하여 Mac 컴퓨터의 하드웨어 및 설치된 애플리케이션에 대한 정보를 수집할 수 있습니다. 이 정보는 Configuration Manager 콘솔의 리소스 탐색기에서 볼 수 있으며 컬렉션, 쿼리 및 보고서를 만드는 데 활용할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md)을 참조하세요.  

     Configuration Manager는 Mac 컴퓨터에서 다음 하드웨어 정보를 수집합니다.  

    -   프로세서  

    -   컴퓨터 시스템  

    -   디스크 드라이브  

    -   디스크 파티션  

    -   네트워크 어댑터  

    -   운영 체제  

    -   서비스  

    -   프로세스  

    -   설치된 소프트웨어  

    -   컴퓨터 시스템 제품  

    -   USB 컨트롤러  

    -   USB 디바이스  

    -   CDROM 드라이브  

    -   비디오 컨트롤러  

    -   데스크톱 모니터  

    -   휴대용 배터리  

    -   실제 메모리  

    -   프린터  

    > [!IMPORTANT]  
    >  하드웨어 인벤토리 중에는 Mac 컴퓨터에서 수집한 하드웨어 정보를 확장할 수 없습니다.  

-   **준수 설정**  

     Configuration Manager 준수 설정을 사용하여 Mac OS X 기본(.plist) 설정의 준수를 확인하고 이 설정을 재구성할 수 있습니다. 예를 들어 Safari 웹 브라우저의 홈 페이지에 대한 설정을 강제 적용하거나 Apple 방화벽을 사용하도록 설정할 수 있습니다. 또한 셸 스크립트를 사용하면 MAC OS X의 설정을 모니터링하고 재구성할 수 있습니다.  

-   **응용 프로그램 관리**  

     Configuration Manager는 Mac 컴퓨터에 소프트웨어를 배포할 수 있습니다. 이 경우 Mac 컴퓨터에 배포할 수 있는 소프트웨어 형식은 다음과 같습니다.  

    -   Apple 디스크 이미지(.DMG)  

    -   메타 패키지 파일(.MPKG)  

    -   Mac OS X 설치 관리자 패키지(.PKG)  

    -   Mac OS X 애플리케이션(.APP)  

 Configuration Manager 클라이언트를 Mac 컴퓨터에 설치할 경우 Windows 기반 컴퓨터에서 Configuration Manager 클라이언트가 지원하는 다음 관리 기능을 사용할 수 없습니다.  

-   클라이언트 강제 설치  

-   운영 체제 배포  

-   소프트웨어 업데이트  

    > [!NOTE]  
    >  Configuration Manager 애플리케이션 관리를 사용하면 필수 Mac OS X 소프트웨어 업데이트를 Mac 컴퓨터에 배포할 수 있습니다. 또한 호환성 설정을 사용하여 컴퓨터에 모든 필수 소프트웨어 업데이트가 설치되어 있는지 확인할 수 있습니다.  

-   유지 관리 기간  

-   원격 제어  

-   전원 관리  

-   클라이언트 상태 클라이언트 검사 및 재구성  

 Configuration Manager Mac 클라이언트를 설치하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Mac에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-macs.md)을 참조하세요.
