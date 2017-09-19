---
title: "클라이언트 통신 포트 구성 | Microsoft 문서"
description: "System Center Configuration Manager에서 클라이언트 통신 포트를 설정합니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 406bbdbf-ab4a-4121-a68b-154f96ea14ec
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: a181bd78f1925fa2f17aa4071ea81f58ae1570af
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-configure-client-communication-ports-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 클라이언트가 통신용으로 HTTP 및 HTTPS를 사용하는 사이트 시스템과 통신하는 데 사용하는 요청 포트 번호를 변경할 수 있습니다. 방화벽을 위해 HTTP 또는 HTTPS가 이미 구성되어 있을 가능성이 높지만 사용자 지정 포트 번호를 사용하는 경우 HTTP 또는 HTTPS를 사용하는 클라이언트 알림을 지정하면 관리 지점 컴퓨터의 CPU 사용량과 메모리가 더 많이 필요합니다. 절전 모드 해제 패킷을 사용하여 클라이언트의 절전 모드를 해제하는 경우 사용할 사이트 포트 번호를 지정할 수도 있습니다.  

 HTTP 및 HTTPS 요청 포트를 지정하는 경우 기본 포트 번호와 대체 포트 번호를 모두 지정할 수 있습니다. 클라이언트는 기본 포트를 사용한 통신에 실패하면 자동으로 대체 포트와의 통신을 시도합니다. HTTP 및 HTTPS 데이터 통신에 대한 설정을 지정할 수 있습니다.  

 클라이언트 요청 포트의 기본값은 HTTP 트래픽의 경우 **80** 이고 HTTPS 트래픽의 경우 **443** 입니다. 이 값은 기본값을 사용하지 않으려는 경우에만 변경하십시오. 사용자 지정 포트는 일반적으로 IIS에서 기본 웹 사이트 대신 사용자 지정 웹 사이트를 사용하는 경우에 적용합니다. IIS에서 기본 웹 사이트에 대한 기본 포트 번호를 변경할 경우 기본 웹 사이트를 사용하는 다른 응용 프로그램은 작동에 실패할 수 있습니다.  

> [!IMPORTANT]  
>  결과를 알 수 없는 경우 Configuration Manager에서 포트 번호를 변경하지 마세요. 예제:  
>   
>  -   사이트 구성으로 클라이언트 요청 서비스에 대한 포트 번호를 변경했지만 기존 클라이언트는 새 포트 번호를 사용하도록 다시 구성되지 않은 경우 이러한 클라이언트는 관리되지 않는 상태가 됩니다.  
> -   기본 포트 번호 이외의 포트 번호를 구성하려면 방화벽과 모든 중간 네트워크 장치에서 이러한 구성을 지원하고 필요에 따라 다시 구성할 수 있어야 합니다. 인터넷을 통해 클라이언트를 관리할 때 기본 HTTPS 포트 번호 443을 변경할 경우 인터넷에 연결된 라우터와 방화벽에서 이 통신을 차단할 수 있습니다.  

 요청 포트 번호를 변경한 후 클라이언트가 관리되지 않는 상태가 되지 않도록 하려면 해당 클라이언트에서 새 요청 포트 번호를 사용하도록 구성해야 합니다. 기본 사이트에서 요청 포트를 변경할 경우 모든 연결된 보조 사이트에서 동일한 포트 구성을 자동으로 상속합니다. 기본 사이트에서 요청 포트를 구성하려면 이 항목의 절차를 수행하십시오.  

> [!NOTE]  
>  Linux 및 UNIX를 실행하는 컴퓨터에서 클라이언트에 대한 요청 포트를 구성하는 방법에 대한 자세한 내용은 [Linux 및 UNIX의 클라이언트에 대한 요청 포트 구성](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigLnUClientCommuincations)을 참조하세요.  

 Configuration Manager 사이트가 Active Directory Domain Services에 게시된 경우 이 정보에 액세스할 수 있는 새 클라이언트와 기존 클라이언트는 자동으로 해당 사이트 포트 설정으로 구성되므로 추가 작업을 수행할 필요가 없습니다. Active Directory Domain Services에 게시된 이 정보에 액세스할 수 없는 클라이언트에는 작업 그룹 클라이언트, 다른 Active Directory 포리스트의 클라이언트, 인터넷 전용으로 구성된 클라이언트, 현재 인터넷에 연결되어 있는 클라이언트 등이 있습니다. 이러한 클라이언트를 설치한 후 기본 포트 번호를 변경하는 경우에는 클라이언트를 다시 설치하고 다음 방법 중 하나를 사용하여 새 클라이언트를 설치하십시오.  

-   클라이언트 강제 설치 마법사를 사용하여 클라이언트를 다시 설치합니다. 클라이언트 강제 설치는 자동으로 현재 사이트 포트 구성으로 클라이언트를 구성합니다. 클라이언트 강제 설치 마법사를 사용하는 방법에 대한 자세한 내용은 [클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush)을 참조하세요.  

-   CCMSetup.exe와 CCMHTTPPORT 및 CCMHTTPSPORT의 client.msi 설치 속성을 사용하여 클라이언트를 다시 설치합니다. 이러한 속성에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

-   Active Directory Domain Services에서 Configuration Manager 클라이언트 설치 속성을 검색하는 방법을 사용하여 클라이언트를 다시 설치합니다. 자세한 내용은 [System Center Configuration Manager에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md)를 참조하세요.  

 기존 클라이언트의 포트 번호를 다시 구성하기 위해 설치 미디어의 SMSSETUP\Tools\PortConfiguration 폴더에 제공된 PORTSWITCH.VBS 스크립트를 사용할 수도 있습니다.  

> [!IMPORTANT]  
>  현재 인터넷에 있는 기존 클라이언트와 새 클라이언트의 경우 CCMSetup.exe와 CCMHTTPPORT 및 CCMHTTPSPORT의 client.msi 속성을 사용하여 기본 포트 번호가 아닌 포트 번호를 구성해야 합니다.  

 사이트의 요청 포트를 변경하면 사이트 전체 클라이언트 강제 설치 방법을 사용하여 설치한 새 클라이언트가 자동으로 사이트의 현재 포트 번호로 구성됩니다.  

#### <a name="to-configure-the-client-communication-port-numbers-for-a-site"></a>사이트의 클라이언트 통신 포트 번호를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭한 다음 구성할 기본 사이트를 선택합니다.  

3.  **홈** 탭에서 **속성**을 클릭한 다음 **포트** 탭을 클릭합니다.  

4.  원하는 항목을 선택하고 속성 아이콘을 클릭하여 **포트 세부 정보** 대화 상자를 표시합니다.  

5.  **포트 세부 정보** 대화 상자에서 항목의 포트 번호와 설명을 지정한 다음 **확인**을 클릭합니다.  

6.  IIS를 실행하는 사이트 시스템에 **SMSWeb** 이라는 사용자 지정 웹 사이트 이름을 사용할 경우 **사용자 지정 웹 사이트 사용** 을 선택합니다.  

7.  **확인** 을 클릭하여 사이트의 속성 대화 상자를 닫습니다.  

 계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.
