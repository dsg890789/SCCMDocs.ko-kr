---
title: "클라이언트 설치 방법 | System Center Configuration Manager"
description: "System Center Configuration Manager의 클라이언트 설치 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 169e7871bc1fbc83964ecb17e277d64ce4fd472c


---
# <a name="client-installation-methods-in-system-center-configuration-manager"></a>System Center Configuration Manager의 클라이언트 설치 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

다양한 방법을 사용하여 엔터프라이즈의 Windows 장치, UNIX/Linux 서버 및 Mac 컴퓨터에 System Center Configuration Manager 클라이언트 소프트웨어를 설치할 수 있습니다. 요구 사항에 따라 이러한 방법 중 한 가지를 사용하거나 여러 가지를 조합하여 사용할 수 있습니다.  

 다음 섹션에는 조직에 가장 적합한 방법을 결정하는 데 도움이 되도록 각 클라이언트 설치 방법의 장점과 단점이 정리되어 있습니다.  

## <a name="client-push-installation"></a>클라이언트 강제 설치  

 **지원되는 클라이언트 플랫폼:** Windows  

 **장점**  

-   클라이언트를 단일 컴퓨터나 컴퓨터 컬렉션에 설치하거나 쿼리 결과에 따라 설치할 수 있습니다.  

-   검색된 모든 컴퓨터에 클라이언트를 자동으로 설치할 수 있습니다.  

-   **클라이언트 강제 설치 속성** 대화 상자의 **클라이언트** 탭에 정의된 클라이언트 설치 속성을 자동으로 사용합니다.  

 **단점**  

-   많은 컬렉션에 강제 설치하는 경우 네트워크 트래픽이 높아질 수 있습니다.  

-   Configuration Manager에서 검색한 컴퓨터에만 사용할 수 있습니다.  

-   작업 그룹에는 클라이언트를 설치할 수 없습니다.  

-   해당 클라이언트 컴퓨터에 대한 관리자 권한이 있는 클라이언트 강제 설치 계정을 지정해야 합니다.  

-   클라이언트 컴퓨터에서 클라이언트 강제 설치를 수행할 수 있도록 Windows 방화벽에 예외를 구성해야 합니다.  

-   클라이언트 강제 설치는 취소할 수 없습니다. 사이트에 이 클라이언트 설치 방법을 사용하는 경우 Configuration Manager가 검색된 모든 리소스에 클라이언트를 설치하려고 하며 실패할 경우 최대 7일 동안 다시 시도합니다.  

 이 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)을 참조하세요.  

## <a name="software-update-point-based-installation"></a>소프트웨어 업데이트 지점 기반 설치  
 **지원되는 클라이언트 플랫폼:** Windows  

 **장점:**  

-   기존 소프트웨어 업데이트 인프라를 사용하여 클라이언트 소프트웨어를 관리할 수 있습니다.  

-   Active Directory Domain Services에서 WSUS(Windows Server Update Services) 및 그룹 정책 설정이 올바르게 구성된 경우 새 컴퓨터에 클라이언트 소프트웨어를 자동으로 설치할 수 있습니다.  

-   컴퓨터가 검색되지 않아도 클라이언트가 설치될 수 있습니다.  

-   컴퓨터에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성을 읽을 수 있습니다.  

-   클라이언트 소프트웨어가 제거될 경우 다시 설치됩니다.  

-   해당 컴퓨터에 대한 설치 계정을 구성하고 관리하지 않아도 됩니다.  

 **단점:**  

-   올바르게 작동하는 소프트웨어 업데이트 인프라가 필수 구성 요소로 필요합니다.  

-   클라이언트 설치와 소프트웨어 업데이트에 동일한 서버를 사용해야 하며, 이 서버가 기본 사이트에 있어야 합니다.  

-   새 클라이언트를 설치하려면 Active Directory Domain Services에서 클라이언트의 활성 소프트웨어 업데이트 지점과 포트를 사용하여 GPO(그룹 정책 개체)를 구성해야 합니다.  

-   Active Directory 스키마가 Configuration Manager를 지원하도록 확장되지 않은 경우 그룹 정책 설정을 사용하여 클라이언트 설치 속성으로 컴퓨터를 프로비전해야 합니다.  

 이 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)을 참조하세요.  

## <a name="group-policy-installation"></a>그룹 정책 설치  
 **지원되는 클라이언트 플랫폼:** Windows  

 **장점:**  

-   컴퓨터가 검색되지 않아도 클라이언트가 설치될 수 있습니다.  

-   새 클라이언트 설치나 업그레이드에 모두 사용할 수 있습니다.  

-   컴퓨터에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성을 읽을 수 있습니다.  

-   해당 컴퓨터에 대한 설치 계정을 구성하고 관리하지 않아도 됩니다.  

 **단점:**  

-   다수의 클라이언트를 설치하는 경우 네트워크 트래픽이 높아질 수 있습니다.  

-   Active Directory 스키마가 Configuration Manager를 지원하도록 확장되지 않은 경우 그룹 정책 설정을 사용하여 클라이언트 설치 속성을 사이트의 컴퓨터에 추가해야 합니다.  

 이 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)을 참조하세요.  

## <a name="logon-script-installation"></a>로그온 스크립트 설치  
 **지원되는 클라이언트 플랫폼:** Windows  

 **장점:**  

-   컴퓨터가 검색되지 않아도 클라이언트가 설치될 수 있습니다.  

-   CCMSetup에 명령줄 속성을 사용할 수 있습니다.  

 **단점:**  

-   짧은 기간 동안 다수의 클라이언트를 설치하는 경우 네트워크 트래픽이 높아질 수 있습니다.  

-   사용자가 네트워크에 자주 로그온하지 않는 경우 모든 클라이언트 컴퓨터에 설치하는 데 오랜 시간이 걸릴 수 있습니다.  

 이 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)을 참조하세요.  

## <a name="manual-installation"></a>수동 설치  
 **지원되는 클라이언트 플랫폼:** Windows, UNIX/Linux, Mac OS X  

 **장점:**  

-   컴퓨터가 검색되지 않아도 클라이언트가 설치될 수 있습니다.  

-   테스트를 위해 유용할 수 있습니다.  

-   CCMSetup에 명령줄 속성을 사용할 수 있습니다.  

 **단점:**  

-   자동화되지 않아 시간이 많이 소모됩니다.  

 각 플랫폼에서 클라이언트를 수동으로 설치하는 방법에 대한 자세한 내용은 다음을 참조하세요.  

-   [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

-   [System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)  

-   [System Center Configuration Manager에서 Mac에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-macs.md)  



<!--HONumber=Nov16_HO1-->


