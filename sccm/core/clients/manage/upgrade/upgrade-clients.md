---
title: 클라이언트 업그레이드
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라이언트를 업그레이드하는 방법에 관한 정보를 가져옵니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 40fc094d6c1a1acbd31f1d26e6fe6617972f8da5
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75823673"
---
# <a name="upgrade-clients-in-configuration-manager"></a>Configuration Manager에서 클라이언트 업그레이드

*적용 대상: Configuration Manager(현재 분기)*

다양한 방법을 사용하여 Windows 디바이스, UNIX 및 Linux 서버, Mac 컴퓨터에서 Configuration Manager 클라이언트 소프트웨어를 업그레이드할 수 있습니다. 각 방법의 장점과 단점은 다음과 같습니다.  

> [!TIP]  
>  이전 버전의 Configuration Manager\(예: Configuration Manager 2007 또는 System Center 2012 Configuration Manager\)에서 서버 인프라를 업그레이드하는 경우 Configuration Manager 클라이언트를 업그레이드하기 전에 현재 분기 업데이트를 모두 설치하는 등 서버를 업그레이드하는 것이 좋습니다. 이 방법으로 최신 버전의 클라이언트 소프트웨어를 보유하게 됩니다.  

## <a name="group-policy-installation"></a>그룹 정책 설치  
 **지원되는 클라이언트 플랫폼:** Windows  

#### <a name="advantages"></a>장점  

- 컴퓨터가 검색되지 않아도 클라이언트가 업그레이드될 수 있습니다.  

- 새 클라이언트 설치나 업그레이드에 모두 사용할 수 있습니다.  

- 컴퓨터에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성을 읽을 수 있습니다.  

- 해당 컴퓨터에 대한 설치 계정을 구성하고 관리하지 않아도 됩니다.  

#### <a name="disadvantages"></a>단점  

- 다수의 클라이언트를 업그레이드하는 경우 네트워크 트래픽이 높아질 수 있습니다.  

- Active Directory 스키마가 Configuration Manager를 지원하도록 확장되지 않은 경우 [그룹 정책 설정](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientGP)을 사용하여 클라이언트 설치 속성을 사이트의 컴퓨터에 추가해야 합니다.  


## <a name="logon-script-installation"></a>로그온 스크립트 설치  
 **지원되는 클라이언트 플랫폼:** Windows  

#### <a name="advantages"></a>장점  

- 컴퓨터가 검색되지 않아도 클라이언트가 설치될 수 있습니다.  

- 새 클라이언트 설치나 업그레이드에 모두 사용할 수 있습니다.  

- CCMSetup에 명령줄 속성을 사용할 수 있습니다.  

#### <a name="disadvantages"></a>단점  

- 짧은 기간 동안 다수의 클라이언트를 업그레이드하는 경우 네트워크 트래픽이 높아질 수 있습니다.  

- 사용자가 네트워크에 자주 로그온하지 않는 경우 모든 클라이언트 컴퓨터에서 업그레이드하는 데 오랜 시간이 걸릴 수 있습니다.  

  자세한 내용은 [로그온 스크립트를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientLogonScript)을 참조하세요.  

## <a name="manual-installation"></a>수동 설치  
 **지원되는 클라이언트 플랫폼:** Windows, UNIX/Linux, Mac OS X  

#### <a name="advantages"></a>장점  

- 컴퓨터가 검색되지 않아도 클라이언트가 업그레이드될 수 있습니다.  

- 테스트를 위해 유용할 수 있습니다.  

- CCMSetup에 명령줄 속성을 사용할 수 있습니다.  

#### <a name="disadvantages"></a>단점  

- 자동화되지 않아 시간이 많이 소모됩니다.  

  자세한 내용은 다음 항목을 참조하세요.  

- [Configuration Manager 클라이언트를 수동으로 설치하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Manual)  

- [Linux 및 UNIX 서버용 클라이언트를 업그레이드하는 방법](../../../../core/clients/manage/upgrade/upgrade-clients-for-linux-and-unix-servers.md)  

- [Mac 컴퓨터의 클라이언트를 업그레이드하는 방법](../../../../core/clients/manage/upgrade/upgrade-clients-on-mac-computers.md)  

## <a name="upgrade-installation-application-management"></a>업그레이드 설치(애플리케이션 관리)  
 **지원되는 클라이언트 플랫폼:** Windows  

> [!NOTE]  
>  이 방법으로는 Configuration Manager 2007 클라이언트를 업그레이드할 수 없습니다. 이 시나리오에서는 Configuration Manager 2007 사이트에서 최신 버전의 Configuration Manager 클라이언트를 배포하거나, 최신 버전의 클라이언트가 포함된 패키지를 자동으로 만들어 배포하는 자동 클라이언트 업그레이드를 사용할 수 있습니다.  

#### <a name="advantages"></a>장점  

- CCMSetup에 명령줄 속성을 사용할 수 있습니다.  

#### <a name="disadvantages"></a>단점  

- 많은 컬렉션에 클라이언트를 배포하는 경우 네트워크 트래픽이 높아질 수 있습니다.  

- 검색되어 사이트에 할당된 컴퓨터에서만 클라이언트를 업그레이드할 수 있습니다.  

  자세한 내용은 [패키지 및 프로그램을 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientApp)을 참조하세요.  

## <a name="automatic-client-upgrade"></a>자동 클라이언트 업그레이드  

> [!NOTE]  
> Configuration Manager 2007 클라이언트를 Configuration Manager 현재 분기 클라이언트로 업그레이드하는 데 사용할 수 있습니다. Configuration Manager 2007 클라이언트에서 Configuration Manager 사이트에 할당할 수 있지만 자동 클라이언트 업그레이드 외에 다른 작업은 수행할 수 없습니다.  

 **지원되는 클라이언트 플랫폼:** Windows  

#### <a name="advantages"></a>장점  

- 자동 업그레이드는 지정된 기간 동안의 불규칙화로 인해 대규모 클라이언트 업그레이드에 적합합니다. 다른 메서드는 대규모 작업에서 성능이 너무 느리거나 불규칙화 기능을 포함하지 않습니다. 

    > [!Note]
    > 클라이언트 파일럿은 불규칙화를 사용하지 않으므로 대규모 작업에 유용하지 않습니다.  
- 사이트의 클라이언트를 자동으로 최신 버전으로 유지할 수 있습니다.  

- 관리 작업이 최소화됩니다.  

#### <a name="disadvantages"></a>단점  

- 클라이언트 소프트웨어를 업그레이드할 수만 있고 새 클라이언트를 설치할 수는 없습니다.  

- 사이트에 할당된 계층의 모든 클라이언트에 적용됩니다. 컬렉션으로 범위를 나눌 수 없습니다.  

- 일정 옵션이 제한적입니다.  

  자세한 내용은 [Windows 컴퓨터에 대한 클라이언트를 업그레이드하는 방법](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md)을 참조하세요.  

## <a name="client-testing"></a>클라이언트 테스트  
 **지원되는 클라이언트 플랫폼:** Windows  

#### <a name="advantages"></a>장점  

- 작은 규모의 사전 프로덕션 컬렉션에서 새 클라이언트 버전을 테스트하는 데 사용할 수 있습니다.  

- 테스트가 완료되면 사전 프로덕션의 클라이언트 수준이 프로덕션으로 올라가고 Configuration Manager 사이트 전체에 걸쳐 자동으로 업그레이드됩니다.  

#### <a name="disadvantages"></a>단점  

- 클라이언트 소프트웨어를 업그레이드할 수만 있고 새 클라이언트를 설치할 수는 없습니다.  

  [사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](../../../../core/clients/manage/upgrade/test-client-upgrades.md)  
