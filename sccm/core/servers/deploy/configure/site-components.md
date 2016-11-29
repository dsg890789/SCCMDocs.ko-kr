---
title: "사이트 구성 요소 | System Center Configuration Manager"
description: "사이트 시스템 역할 및 사이트 상태 보고의 동작을 수정하기 위해 사이트 구성 요소를 구성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: a0c2ff2ad2f76e7e769d49674ccf4d3efe6b4f3e


---
# <a name="site-components-for-system-center-configuration-manager"></a>System Center Configuration Manager의 사이트 구성 요소

*적용 대상: System Center Configuration Manager(현재 분기)*

각 System Center Configuration Manager 사이트에서는 사이트 시스템 역할 및 사이트 상태 보고의 동작을 수정하기 위해 사이트 구성 요소를 구성할 수 있습니다. 사이트 구성 요소 구성은 사이트와 해당 사이트의 해당하는 각 사이트 시스템 역할 인스턴스에 적용됩니다.  

## <a name="about-site-components"></a>사이트 구성 요소 정보  
 다양한 사이트 구성 요소에 대한 대부분의 옵션은 Configuration Manager 콘솔에 표시되는 상태를 보면 해당 용도를 파악할 수 있습니다. 아래 세부 정보는 보다 복잡한 일부 구성에 대한 설명 또는 해당 설명이 포함된 추가 콘텐츠를 제공합니다.  

**소프트웨어 배포:**  

-   **콘텐츠 배포 설정:**  사이트 서버가 배포 지점에 콘텐츠를 전송하는 방법을 수정하는 설정을 구성할 수 있습니다. 동시 배포 설정에 사용하는 값을 더 크게 지정하면 콘텐츠 배포에서 네트워크 대역폭을 더 많이 사용할 수 있습니다.  

-   **네트워크 액세스 계정:** 네트워크 액세스 계정을 구성 및 사용하는 방법에 대한 자세한 내용은 [네트워크 액세스 계정](../../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA)을 참조하세요.  

**소프트웨어 업데이트 지점:**  

-   소프트웨어 업데이트 지점 구성 요소의 구성 옵션에 대한 자세한 내용은 [소프트웨어 업데이트 지점 설치](../../../../sum/get-started/install-a-software-update-point.md)를 참조하세요.  

**관리 지점:**  

-   **관리 지점:** Active Directory Domain Services에 해당 관리 지점에 대한 정보를 게시하도록 사이트를 구성할 수 있습니다.  

     Configuration Manager 클라이언트는 서비스 위치용 관리 지점을 사용하여 경계 그룹 구성원 자격 및 PKI 인증서 선택 옵션과 같은 사이트 정보를 찾고, 소프트웨어를 다운로드할 배포 지점과 사이트의 기타 관리 지점을 찾습니다. 또한 클라이언트는 사이트 할당을 완료하고 클라이언트 정책을 다운로드하며 클라이언트 정보를 업로드하기 위해 관리 지점을 사용합니다.  

     클라이언트가 관리 지점을 검색하는 가장 안전한 방법은 Active Directory Domain Services에 게시하는 것이므로 일반적으로 항상 올바르게 작동하는 모든 관리 지점을 Active Directory Domain Services에 게시하도록 선택합니다. 그러나 이 서비스 위치 방법을 사용하려면 Configuration Manager용 스키마를 확장해야 하고, 사이트 서버가 컨테이너에 게시하기 위한 적절한 보안 권한을 갖는 **System Management** 컨테이너가 있어야 하고, Configuration Manager 사이트가 Active Directory Domain Services에 게시하도록 구성되고, 클라이언트가 사이트 서버의 포리스트와 동일한 Active Directory 포리스트에 속해 있어야 합니다.  

     인트라넷의 클라이언트가 Active Directory Domain Services를 사용하여 관리 지점을 찾을 수 없는 경우 [DNS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_dns) 게시를 사용합니다.  

     서비스 위치에 대한 일반적인 내용은 [클라이언트가 System Center Configuration Manager에 대한 사이트 리소스 및 서비스를 찾는 방법 이해](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)를 참조하세요.  

-   **DNS에 선택한 인트라넷 관리 지점 게시:** 인트라넷의 클라이언트가 Active Directory Domain Services에서는 관리 지점을 찾지 못하지만 DNS SRV RR(서비스 위치 리소스 레코드)을 사용하여 할당된 사이트에서 관리 지점을 찾을 수 있는 경우 이 옵션을 지정합니다.  

    Configuration Manager에서 인트라넷 관리 지점을 DNS에 게시하려면 다음 모든 조건을 충족해야 합니다.  

    -   DNS 서버의 BIND 버전은 8.1.2 이상이어야 합니다.  

    -   DNS 서버에 자동 업데이트가 구성되어 있고 DNS 서버가 서비스 위치 리소스 레코드를 지원해야 합니다.  

    -   Configuration Manager에서 관리 지점에 지정한 FQDN에 DNS의 호스트 항목(A 또는 AAA 레코드)가 있어야 합니다.  

    > [!WARNING]  
    >  클라이언트에서 DNS에 게시된 관리 지점을 찾으려면 자동 사이트 할당 기능을 사용하지 말고 클라이언트에 해당 사이트를 할당해야 하며, 이러한 클라이언트가 해당 관리 지점의 도메인 접미사가 있는 사이트 코드를 사용하도록 구성해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법](../../../../core/clients/deploy/assign-clients-to-a-site.md)에서 [관리 지점 찾기](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_LocatingMPs)를 참조하세요.  

     Configuration Manager 클라이언트가 Active Directory Domain Services 또는 DNS를 사용하여 인트라넷에서 관리 지점을 찾을 수 없는 경우 [WINS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_wins)를 사용하도록 대체됩니다. 사이트에 설치된 첫 번째 관리 지점은 인트라넷에서 HTTP 클라이언트 연결을 허용하도록 구성된 경우 WINS에 자동으로 게시됩니다.  

**상태 보고:**  

-   이러한 설정은 사이트와 클라이언트의 상태 보고서에 포함되는 세부 정보 수준을 직접 구성합니다.  

**메일 알림:**  

-   Configuration Manager에서 경고를 위한 메일 알림을 보내도록 설정하려면 계정 및 메일 서버 세부 정보를 지정합니다.  

**컬렉션 멤버 평가:**  

-   이 작업을 사용하여 컬렉션 멤버의 추가 증가분을 평가할 빈도를 설정합니다. 증가분 평가는 컬렉션 멤버 자격에서 변경되거나 새로운 리소스만 업데이트합니다.  

#### <a name="to-edit-the-site-components-at-a-site"></a>사이트에서 사이트 구성 요소를 편집하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 클릭하고 구성할 사이트 구성 요소가 있는 사이트를 선택합니다.  

2.  **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성** 을 클릭하고 구성할 사이트 구성 요소를 선택합니다.  

##  <a name="a-namebkmkservicemgra-use-the-configuration-manager-service-manager-to-manage-site-components"></a><a name="BKMK_ServiceMgr"></a> Configuration Manager Service Manager를 사용하여 사이트 구성 요소 관리  
Configuration Manager Service Manager를 사용하여 Configuration Manager 서비스를 제어하고 Configuration Manager 서비스 또는 작업 스레드(Configuration Manager 구성 요소로 총칭)의 상태를 확인할 수 있습니다.  

-   Configuration Manager 구성 요소는 모든 사이트 시스템에서 실행할 수 있습니다.  

-   구성 요소는 Windows에서 서비스를 관리하는 것과 같은 방식으로 관리할 수 있으므로, Configuration Manager 구성 요소를 시작, 중지, 일시 중지, 재시작 또는 쿼리할 수 있습니다.  

Configuration Manager 서비스는 수행해야 할 작업이 있을 때, 즉 일반적으로 구성 파일이 구성 요소의 수신함에 기록될 때 실행됩니다. 작업에 관련된 구성 요소를 식별해야 할 경우 **Configuration Manager Service Manager**를 사용하여 다양한 Configuration Manager 서비스 및 스레드를 조작한 다음 Configuration Manager의 동작에서 그 결과로 변경된 내용을 확인하면 됩니다. 예를 들어 특정 응답이 제거될 때까지 Configuration Manager 서비스를 한 번에 하나씩 중지할 수 있습니다. 이렇게 하면 특정 동작을 일으키는 서비스를 확인할 수 있습니다.  

> [!TIP]  
>  다음 절차에 따라 Configuration Manager 구성 요소 작업을 조작할 수 있습니다.  

#### <a name="to-use-the-configuration-manager-service-manager"></a>Configuration Manager Service Manager를 사용하려면  

1.  Configuration Manager 콘솔에서 **모니터링** >  **시스템 상태**를 클릭한 다음 **구성 요소 상태**를 클릭합니다.  

2.  **홈** 탭의 **구성 요소** 그룹에서 **시작**을 클릭한 다음 **Configuration Manager Service Manager**를 선택합니다.  

3.  Configuration Manager Service Manager가 열리면 관리할 사이트에 연결합니다.  

     관리할 사이트가 보이지 않으면 **사이트**, **연결**을 차례로 클릭한 다음 올바른 사이트의 사이트 서버 이름을 입력합니다.  

4.  해당 사이트를 확장하고 관리할 구성 요소의 위치에 따라 **구성 요소** 또는 **서버** 로 이동합니다.  

5.  오른쪽 창에서 하나 이상의 구성 요소를 선택한 다음 **구성 요소** 메뉴에서 **쿼리** 를 클릭하여 선택 항목의 상태를 업데이트합니다.  

6.  구성 요소의 상태가 업데이트되면 **구성 요소** 메뉴에서 4개의 동작 기반 옵션 중 하나를 사용하여 구성 요소 작업을 수정합니다. 작업을 요청한 후에는 구성 요소의 새 상태가 표시되도록 구성 요소를 쿼리해야 합니다.  

7.  구성 요소 작업 상태의 수정을 마치면 Configuration Manager Service Manager를 닫습니다.  



<!--HONumber=Nov16_HO1-->


