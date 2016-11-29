---
title: "사전 프로덕션 컬렉션에서 클라이언트 업그레이드 테스트 | System Center Configuration Manager"
description: "System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
caps.latest.revision: 10
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 1e648b94a475bda2b35d69ff0a8863d2e0d248fb


---
# <a name="how-to-test-client-upgrades-in-a-preproduction-collection-in-system-center-configuration-manager"></a>System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Windows PC와 장치에서 Configuration Manager 클라이언트를 업그레이드하려면 해당 사이트의 나머지 부분을 업그레이드하기 전에 사전 프로덕션 컬렉션에서 새 클라이언트 버전을 테스트하면 됩니다.  이 작업을 수행하는 경우 사전 프로덕션 컬렉션에 포함된 장치만 새 클라이언트로 업그레이드됩니다. 이 사전 프로덕션 컬렉션에서 클라이언트를 테스트했다면 클라이언트를 승격할 수 있고 이렇게 하면 새 버전의 클라이언트 소프트웨어를 해당 사이트의 나머지 부분에 사용할 수 있습니다.  

 사전 프로덕션에서 클라이언트를 테스트하려면 3개의 기본 단계가 있습니다.  

1.  사전 프로덕션 컬렉션을 사용하도록[사전 프로덕션 컬렉션을 사용하도록 자동 클라이언트 업그레이드를 구성하려면](#BKMK_config)   

2.  새 버전의 클라이언트가 포함된[새 버전의 클라이언트가 포함된 Configuration Manager 업데이트를 설치하려면](#BKMK_install) . 설치하는 동안 새 클라이언트 소프트웨어에 대한 사전 프로덕션 컬렉션을 사용하도록 지정합니다.  

3.  새 클라이언트를 사전 프로덕션에서 충분히 테스트한 후[새 클라이언트를 프로덕션으로 승격하려면](#BKMK_promote)   

> [!TIP]  
>  이전 버전의 Configuration Manager\(예: Configuration Manager 2007 또는 System Center 2012 Configuration Manager\)에서 서버 인프라를 업그레이드하는 경우 Configuration Manager 클라이언트를 업그레이드하기 전에 현재 분기 업데이트를 모두 설치하는 등 서버를 업그레이드하는 것이 좋습니다.   최신 현재 분기 업데이트에는 클라이언트의 최신 버전이 포함되어 있으므로 사용하려는 Configuration Manager 업데이트를 모두 설치한 후에 클라이언트 업그레이드를 수행하는 것이 좋습니다.  

##  <a name="a-namebkmkconfiga-to-configure-automatic-client-upgrades-to-use-a-preproduction-collection"></a><a name="BKMK_config"></a> 사전 프로덕션 컬렉션을 사용하도록 자동 클라이언트 업그레이드를 구성하려면  

1. 사전 프로덕션 클라이언트를 배포할 컴퓨터를 포함하는 컬렉션을 설정합니다. 이 단계를 수행하는 방법에 대한 자세한 내용은 [컬렉션을 만드는 방법](..\collections\create-collections.md)을 참조하세요.

> [!NOTE]
> 사전 프로덕션 컬렉션에 작업 그룹 컴퓨터를 포함하지 마세요. 작업 그룹 컴퓨터는 배포 지점이 사전 프로덕션 클라이언트 패키지에 액세스하는 데 필요한 인증을 사용할 수 없습니다.   

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 열고 **계층 구조 설정**을 클릭합니다.  

     **계층 설정 속성** 의 **클라이언트 업그레이드**탭:  

    -    **사전 프로덕션 클라이언트를 사용하여 자동으로 사전 프로덕션 컬렉션에 있는 모든 클라이언트 업그레이드**선택  

    -   사전 프로덕션 컬렉션으로 사용하는 컬렉션 이름 입력  

2.  **확인** 을 클릭하여 클라이언트 업그레이드 설정을 저장합니다.  

##  <a name="a-namebkmkinstalla-to-install-a-configuration-manager-update-that-includes-a-new-version-of-the-client"></a><a name="BKMK_install"></a> 새 버전의 클라이언트가 포함된 Configuration Manager 업데이트를 설치하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **업데이트 및 서비스**를 열고 **사용 가능** 업데이트를 선택한 다음 **업데이트 팩 설치**를 클릭합니다.  

     업데이트 설치에 대한 자세한 내용은 [System Center Configuration Manager용 업데이트](../../../../core/servers/manage/updates.md)를 참조하세요.  

2.  업데이트를 설치하는 동안에 마법사의 **클라이언트 옵션** 페이지에서 **사전 프로덕션 컬렉션에서 테스트**를 선택하고 **다음**을 클릭합니다.  

3.  마법사의 나머지 단계를 완료하고 업데이트 팩을 설치합니다.  

     마법사를 완료한 후 사전 프로덕션 컬렉션의 클라이언트는 업데이트된 클라이언트 배포를 시작합니다. **모니터링** > **클라이언트 상태** > **사전 프로덕션 클라이언트 배포**로 이동하여 업그레이드된 클라이언트 배포를 모니터링할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 배포 상태를 모니터링하는 방법](../../../../core/clients/deploy/monitor-client-deployment-status.md)을 참조하세요.

    > [!NOTE]
    > 사전 프로덕션 컬렉션의 사이트 시스템 역할을 호스팅하는 컴퓨터의 배포 상태는 클라이언트가 배포된 경우에도 **시작되지 않음** 으로 나타날 수 있습니다. 클라이언트 수준을 프로덕션에 올리면 배포 상태가 올바르게 나타납니다.

##  <a name="a-namebkmkpromotea-to-promote-the-new-client-to-production"></a><a name="BKMK_promote"></a> 새 클라이언트를 프로덕션으로 승격하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **업데이트 및 서비스**를 열고 **사전 프로덕션 클라이언트 수준 올리기**를 클릭합니다.

    > [!TIP]
    > **사전 프로덕션 클라이언트 수준 올리기** 단추는 **모니터링** > **클라이언트 상태** > **사전 프로덕션 클라이언트 배포**에서 콘솔의 클라이언트 배포를 모니터링할 경우에도 사용할 수 있습니다.

2.  대화 상자에서 프로덕션 및 사전 프로덕션의 클라이언트 버전을 검토하고 올바른 사전 프로덕션 컬렉션이 지정되었는지 확인한 다음 **승격**을 클릭합니다. 확인 상자에서 **예**를 클릭합니다.  

3.  대화 상자를 닫으면 계층에서 사용하는 현재 클라이언트 버전이 업데이트된 클라이언트 버전으로 대체됩니다. 그런 다음 전체 사이트에 대해 클라이언트를 업그레이드할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트를 업그레이드하는 방법](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md)을 참조하세요.  



<!--HONumber=Nov16_HO1-->


