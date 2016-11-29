---
title: "관리 지점 DNS 게시를 찾도록 클라이언트 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 DNS 게시를 사용하여 관리 지점을 찾도록 클라이언트 컴퓨터를 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 03cec407-0f9f-454f-a360-b005af738d29
caps.latest.revision: 6
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: c6470a39519bc25357ba5d9721afe9c39a28c348


---
# <a name="how-to-configure-client-computers-to-find-management-points-by-using-dns-publishing-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 DNS 게시를 사용하여 관리 지점을 찾도록 클라이언트 컴퓨터를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 클라이언트는 사이트 할당을 완료하고 계속되는 프로세스를 관리되는 상태로 유지하기 위해 관리 지점을 찾아야 합니다. 인트라넷의 클라이언트가 관리 지점을 찾는 데 Active Directory Domain Services를 사용하는 것이 가장 안전하지만, 예를 들어 Active Directory 스키마를 확장하지 않았거나 클라이언트가 작업 그룹에 없어서 클라이언트가 이 서비스 위치 방법을 사용할 수 없는 경우에는 기본 대체 서비스 위치 방법으로 DNS 게시를 사용하십시오.  

> [!NOTE]  
>  Linux 및 UNIX 서버에 클라이언트를 설치하는 경우 초기 연결 지점으로 사용할 관리 지점을 지정해야 합니다. Linux 및 UNIX용 클라이언트를 설치하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)을 참조하세요.  

 관리 지점에 DNS 게시를 사용하기 전에 인트라넷의 DNS 서버에 사이트 관리 지점에 대한 SRV RR(서비스 위치 리소스 레코드)과 해당 호스트(A 또는 AAA) 리소스 레코드가 있어야 합니다. 서비스 위치 리소스 레코드는 Configuration Manager에서 자동으로 만들거나 DNS에 레코드를 만드는 DNS 관리자가 수동으로 만들 수 있습니다.  

 Configuration Manager 클라이언트의 서비스 위치 방법으로 DNS 게시를 사용하는 방법에 대한 자세한 내용은 [클라이언트가 System Center Configuration Manager에 대한 사이트 리소스 및 서비스를 찾는 방법 이해](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)를 참조하세요.  

 기본적으로 클라이언트는 해당 DNS 도메인에서 관리 지점의 DNS를 검색합니다. 그러나 클라이언트의 도메인에 게시된 관리 지점이 없으면 관리 지점 DNS 접미사를 사용하여 수동으로 클라이언트를 구성해야 합니다. 클라이언트 설치 중이나 후에 클라이언트에서 이 DNS 접미사를 구성할 수 있습니다.  

-   클라이언트 설치 중에 클라이언트에서 관리 지점 접미사를 구성하려면 CCMSetup Client.msi 속성을 구성합니다.  

-   클라이언트 설치 후에 클라이언트에서 관리 지점 접미사를 구성하려면 제어판에서 **Configuration Manager 속성**을 구성합니다.  

#### <a name="to-configure-clients-for-a-management-point-suffix-during-client-installation"></a>클라이언트 설치 중에 클라이언트에서 관리 지점 접미사를 구성하려면  

-   다음 CCMSetup Client.msi 속성을 사용하여 클라이언트를 설치합니다.  

    -   **DNSSUFFIX=** *&lt;관리 지점 도메인\>*  

         사이트가 관리 지점을 둘 이상 갖고 둘 이상의 도메인에 있는 경우 한 도메인만 지정합니다. 클라이언트가 이 도메인의 관리 지점에 연결하면 사용 가능한 관리 지점 목록을 다운로드하며, 여기에는 다른 도메인의 관리 지점도 포함됩니다.  

     CCMSetup 명령줄 속성에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

#### <a name="to-configure-clients-for-a-management-point-suffix-after-client-installation"></a>클라이언트 설치 후에 클라이언트에서 관리 지점 접미사를 구성하려면  

1.  클라이언트 컴퓨터의 제어판에서 **Configuration Manager**로 이동하여 **속성**을 두 번 클릭합니다.  

2.  **사이트** 탭에서 관리 지점의 DNS 접미사를 지정한 후에 **확인**을 클릭합니다.  

     사이트가 관리 지점을 둘 이상 갖고 둘 이상의 도메인에 있는 경우 한 도메인만 지정합니다. 클라이언트가 이 도메인의 관리 지점에 연결하면 사용 가능한 관리 지점 목록을 다운로드하며, 여기에는 다른 도메인의 관리 지점도 포함됩니다.



<!--HONumber=Nov16_HO1-->


