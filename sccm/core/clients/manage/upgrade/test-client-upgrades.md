---
title: 클라이언트 업그레이드 사전 프로덕션 컬렉션 테스트
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트합니다.
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a8e7cbfefcb97506ac83231bcb7c24fc54f919e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62216929"
---
# <a name="how-to-test-client-upgrades-in-a-pre-production-collection-in-system-center-configuration-manager"></a>System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

새 Configuration Manager 클라이언트 버전을 사용하여 사이트의 나머지 부분을 업그레이드하기 전에 사전 프로덕션 컬렉션에서 해당 버전을 테스트할 수 있습니다.  이 작업을 수행하는 경우 테스트 컬렉션에 포함된 디바이스만 업그레이드됩니다. 테스트한 클라이언트는 수준을 올릴 수 있으며, 그러면 새 버전의 클라이언트 소프트웨어를 해당 사이트의 나머지 부분에 사용할 수 있습니다.

> [!NOTE]
> 테스트 클라이언트의 수준을 프로덕션 클라이언트로 올리려면 시스템 역할이 **전체 관리자**이고 보안 범위가 **모두**인 사용자로 로그인해야 합니다. 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요. 또한 중앙 관리 사이트 또는 최상위 독립 실행형 기본 사이트에 연결된 서버에 로그인해야 합니다.

 사전 프로덕션에서 클라이언트를 테스트하려면 기본적인 3단계를 수행해야 합니다.  

1.  사전 프로덕션 컬렉션을 사용하도록 자동 클라이언트 업그레이드를 구성합니다.  

2.  새 버전의 클라이언트가 포함된 Configuration Manager 업데이트를 설치합니다.  

3.  새 클라이언트를 프로덕션 수준으로 올립니다.  

##  <a name="to-configure-automatic-client-upgrades-to-use-a-pre-production-collection"></a>사전 프로덕션 컬렉션을 사용하도록 자동 클라이언트 업그레이드를 구성하려면  
> [!IMPORTANT]
> 작업 그룹 컴퓨터에서는 사전 프로덕션 클라이언트 배포가 지원되지 않습니다. 작업 그룹 컴퓨터는 배포 지점이 사전 프로덕션 클라이언트 패키지에 액세스하는 데 필요한 인증을 사용할 수 없습니다.  작업 그룹 컴퓨터는 프로덕션 클라이언트로 승격될 때 최신 클라이언트를 수신합니다.

1. 사전 프로덕션 클라이언트를 배포할 컴퓨터를 포함하는 [컬렉션을 설정](../collections/create-collections.md)합니다.   

2. Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 열고 **계층 설정**을 선택합니다.  

    **계층 설정 속성** 의 **클라이언트 업그레이드**탭:  

   -   **사전 프로덕션 클라이언트를 사용하여 자동으로 사전 프로덕션 컬렉션에 있는 모든 클라이언트 업그레이드**선택  

   -   사전 프로덕션 컬렉션으로 사용하는 컬렉션 이름 입력  

![클라이언트 업그레이드 테스트](media/test-client-upgrades.png)

>[!NOTE]
>이러한 설정을 변경하려면 계정이 **전체 관리자** 보안 역할 및 **모두** 보안 범위의 구성원이어야 합니다.


##  <a name="to-install-a-configuration-manager-update-that-includes-a-new-version-of-the-client"></a>새 버전의 클라이언트가 포함된 Configuration Manager 업데이트를 설치하려면  

1.  Configuration Manager 콘솔에서 **관리** > **업데이트 및 서비스**를 열고 **사용 가능** 업데이트를 선택하고 나서 **업데이트 팩 설치**를 선택합니다. 버전 1702 이전에는 업데이트 및 서비스가 **관리** > **Cloud Services** 아래에 있었습니다.

     업데이트 설치에 대한 자세한 내용은 [System Center Configuration Manager용 업데이트](../../../../core/servers/manage/updates.md)를 참조하세요.  

2.  업데이트를 설치하는 동안에 마법사의 **클라이언트 옵션** 페이지에서 **사전 프로덕션 컬렉션에서 테스트**를 선택합니다.  

3.  마법사의 나머지 단계를 완료하고 업데이트 팩을 설치합니다.  

     마법사를 완료한 후 사전 프로덕션 컬렉션의 클라이언트는 업데이트된 클라이언트 배포를 시작합니다. **모니터링** > **클라이언트 상태** > **사전 프로덕션 클라이언트 배포**로 이동하여 업그레이드된 클라이언트 배포를 모니터링할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 배포 상태를 모니터링하는 방법](../../../../core/clients/deploy/monitor-client-deployment-status.md)을 참조하세요.

    > [!NOTE]
    > 사전 프로덕션 컬렉션의 사이트 시스템 역할을 호스팅하는 컴퓨터의 배포 상태는 클라이언트가 배포된 경우에도 **호환되지 않음**으로 보고될 수 있습니다. 클라이언트 수준을 프로덕션에 올리면 배포 상태가 올바르게 나타납니다.

##  <a name="to-promote-the-new-client-to-production"></a>새 클라이언트를 프로덕션으로 승격하려면  

1.  Configuration Manager 콘솔에서 **관리** > **업데이트 및 서비스**를 열고 **사전 프로덕션 클라이언트 수준 올리기**를 선택합니다. 버전 1702 이전에는 업데이트 및 서비스가 **관리** > **Cloud Services** 아래에 있었습니다.

    > [!TIP]
    > **사전 프로덕션 클라이언트 수준 올리기** 단추는 **모니터링** > **클라이언트 상태** > **사전 프로덕션 클라이언트 배포**에서 콘솔의 클라이언트 배포를 모니터링할 경우에도 사용할 수 있습니다.

2.  프로덕션 및 사전 프로덕션의 클라이언트 버전을 검토하고 올바른 사전 프로덕션 컬렉션이 지정되었는지 확인한 다음 **수준 올리기**, **예**를 차례로 클릭합니다.  

3.  대화 상자를 닫으면 계층에서 사용하는 클라이언트 버전이 업데이트된 클라이언트 버전으로 대체됩니다. 그런 다음 전체 사이트에 대해 클라이언트를 업그레이드할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트를 업그레이드하는 방법](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md)을 참조하세요.  

>[!NOTE]
>사전 프로덕션 클라이언트를 사용하도록 설정하거나 사전 프로덕션 클라이언트를 프로덕션 클라이언트로 수준을 올리려면 계정이 **업데이트 패키지** 개체에 대한 **읽기** 및 **수정** 권한이 있는 보안 역할의 구성원이어야 합니다.
>클라이언트 업그레이드는 사용자가 구성한 Configuration Manager 유지 관리 기간을 준수합니다.
