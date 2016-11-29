---
title: "사이트 시스템 역할 계획 | System Center Configuration Manager"
description: "System Center Configuration Manager 계층 구조를 계획할 때 사이트 시스템 서버 및 사이트 시스템 역할을 고려하세요."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 5f8d051a92cd74938f1a5235b37f02ebe0ff542c


---
# <a name="plan-for-site-system-servers-and-site-system-roles-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

설치하는 각 System Center Configuration Manager 사이트에는 **사이트 시스템 서버**인 사이트 서버가 포함됩니다. 또한 사이트에는 사이트 서버에 원격인 컴퓨터의 추가 사이트 시스템 서버도 포함될 수 있습니다.   사이트 시스템 서버(사이트 서버 또는 원격 사이트 시스템 서버)에서는 **사이트 시스템 역할**을 지원합니다.


##  <a name="a-namebkmksiteserversa-site-system-servers"></a><a name="bkmk_siteservers"></a> 사이트 시스템 서버  
 컴퓨터에 사이트 시스템 역할을 설치하면 해당 컴퓨터가 사이트 시스템 서버가 됩니다. 각 사이트에서 하나 이상의 추가 사이트 시스템 서버를 설치할 수 있습니다. 또한 추가 사이트 시스템 서버를 설치하고 사이트 서버 컴퓨터에서 직접 모든 사이트 시스템 역할을 실행하지 않도록 선택할 수도 있습니다.  각 사이트 시스템 서버는 하나 이상의 사이트 시스템 역할을 지원하며, 사이트 시스템 역할이 서버에 지정하는 CPU 처리 부하를 공유하여 사이트의 기능 및 용량을 확장하는 데 도움이 됩니다.  

 사이트 시스템 서버 추가를 고려할 때 서버가 용도의 필수 조건을 충족하며, 사이트 서버, 도메인 리소스, 클라우드 기반 위치, 사이트 시스템 서버, 클라이언트 등 예상되는 끝점과 통신할 수 있는 충분한 대역폭이 있는 네트워크 위치에 있는지 확인하세요.  

 사이트 시스템 역할에 사용할 프록시를 사이트 시스템 서버와 함께 구성하는 경우 [프록시 서버를 사용할 수 있는 사이트 시스템 역할](#bkmk_proxy)을 참조하세요.  

##  <a name="a-namebkmkplanrolesa-site-system-roles"></a><a name="bkmk_planroles"></a> 사이트 시스템 역할  
 사이트 시스템 역할은 사이트에 추가 기능을 제공하는 컴퓨터에 설치됩니다. 다음과 같은 경우를 예로 들 수 있습니다.  

-   추가 관리 지점. 사이트는 사이트의 최대 지원 용량까지 더 많은 장치를 지원할 수 있습니다.  

-   콘텐츠 인프라를 확장할 추가 배포 지점. 장치 및 사용자에게 콘텐츠를 배포하는 성능을 높일 수 있습니다.  

-   소프트웨어 업데이트 지점(관리되는 장치에 대한 소프트웨어 업데이트를 관리하는 데 사용할 수 있음) 또는 보고 서비스 지점 같은, 하나 이상의 기능별 사이트 시스템 역할. 모니터링할 보고서를 실행하고 배포 정보를 파악하거나 공유할 수 있습니다.  


Configuration Manager 사이트마다 다른 사이트 시스템 역할을 지원할 수 있습니다. 지원되는 사이트 시스템 역할은 사이트의 유형(중앙 관리 사이트, 기본 사이트 또는 보조 사이트)에 따라 달라집니다. 계층의 토폴로지는 특정 사이트 유형에서 일부 역할의 배치를 제한할 수 있습니다. 예를 들어 서비스 연결 지점은 중앙 관리 사이트 또는 독립 실행형 기본 사이트가 될 수 있는 계층의 최상위 계층 사이트에서만 지원됩니다. 이 역할은 자식 기본 사이트 또는 보조 사이트에서 지원되지 않습니다.  

사이트를 설치한 후 사이트 서버의 기본 위치에서 다른 서버(예: 관리 지점 또는 기본적으로 기본 또는 보조 사이트 서버에 설치되는 배포 지점)로 일부 사이트 시스템 역할의 위치를 이동할 수 있습니다. 또한 일부 사이트 시스템 역할의 추가 인스턴스를 설치하여 사이트의 기능을 확장하고(클라이언트에 더 많은 서비스 제공) 비즈니스 요구 사항을 충족할 수 있습니다. 일부 역할은 필수이지만 나머지는 선택 사항입니다.  

-   **Configuration Manager 사이트 서버** - 이 역할은 사이트 설치를 위해 Configuration Manager 설치 프로그램이 실행되는 서버 또는 보조 사이트가 설치되는 서버를 식별합니다. 이 역할은 사이트를 제거할 때까지 옮기거나 제거할 수 없습니다.  

-   **Configuration Manager 사이트 시스템** - 이 역할은 사이트를 설치하거나 사이트 시스템 역할을 설치할 컴퓨터에 할당됩니다.  이 역할은 컴퓨터에서 마지막 사이트 시스템 역할을 제거할 때까지 옮기거나 제거할 수 없습니다.  

-   **Configuration Manager 구성 요소 사이트 시스템 역할** - 이 역할은 SMS Executive 서비스의 인스턴스를 실행하는 사이트 시스템을 식별하며, 관리 지점과 같은 다른 역할을 지원하는 데 필수입니다. 이 역할은 컴퓨터에서 적용 가능한 마지막 사이트 시스템 역할을 제거할 때까지 옮기거나 제거할 수 없습니다.  

-   **Configuration Manager 사이트 데이터베이스 서버** - 이 역할은 사이트를 위해 사이트 데이터베이스의 인스턴스를 보유하는 사이트 시스템 서버에 할당됩니다.  이 역할은 새 서버에 옮길 수만 있는데, 사이트 데이터베이스를 호스팅할 때 다른 SQL Server를 사용하도록 사이트를 수정하면 됩니다.  

-   **SMS 공급자** - SMS 공급자 역할은 SMS 공급자(Configuration Manager 콘솔과 사이트 데이터베이스의 인터페이스 역할)의 인스턴스를 호스트하는 각 컴퓨터에 할당됩니다.  기본적으로 이 역할은 중앙 관리 사이트 및 기본 사이트의 사이트 서버에 자동으로 설치되며, 각 사이트에 추가 인스턴스를 설치하여 추가 관리자에게 사이트 관리 액세스 권한을 제공할 수 있습니다.  

     콘솔 내에서 설치하는 대부분의 사이트 시스템 역할과 달리 추가 공급자를 설치하려면 [SMS 공급자를 관리](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider)할 Configuration Manager 설치 프로그램을 실행한 후 추가 컴퓨터에 추가 공급자를 설치해야 합니다. SMS 공급자의 인스턴스를 한 개만 컴퓨터에 설치할 수 있으며 해당 컴퓨터는 사이트 서버와 동일한 도메인에 있어야 합니다.  

-   **응용 프로그램 카탈로그 웹 서비스 지점** - 소프트웨어 라이브러리의 소프트웨어 정보를 응용 프로그램 카탈로그 웹 사이트에 제공하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

-   **응용 프로그램 카탈로그 웹 사이트 지점** - 응용 프로그램 카탈로그에서 사용 가능한 소프트웨어 목록을 사용자에게 제공하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

     응용 프로그램 카탈로그에서 인터넷을 통해 클라이언트 컴퓨터를 지원하는 경우 보안 모범 사례에 따라 응용 프로그램 카탈로그 웹 사이트 지점은 경계 네트워크에, 응용 프로그램 카탈로그 웹 서비스 지점은 인트라넷에 설치합니다.  

-   **Asset Intelligence 동기화 지점** - Asset Intelligence 카탈로그 정보를 다운로드하고 분류되지 않은 타이틀을 업로드하기 위해 Microsoft에 연결되는 사이트 시스템 역할입니다. 이 역할은 카탈로그에 나중에 포함할 수 있습니다.  계층에서는 이 역할의 단일 인스턴스만 지원하므로, 이 역할의 인스턴스는 계층의 최상위 계층 사이트(중앙 관리 사이트 또는 독립 실행형 기본 사이트)에 있어야 합니다. 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음 중앙 관리 사이트에서 설치해야 합니다.   자세한 내용은 [System Center Configuration Manager의 Asset Intelligence](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md)를 참조하세요.  

-   **인증서 등록 지점** - SCEP(단순 인증서 등록 프로토콜)를 사용하는 장치 인증서 요청을 관리하기 위해 네트워크 장치 등록 서비스를 실행하는 서버와 통신하는 사이트 시스템 역할입니다.  이 역할은 기본 사이트와 중앙 관리 사이트에서만 지원됩니다.   단일 인증서 등록 지점에서 전체 계층에 기능을 제공할 수 있지만 인증서 요청의 부하를 분산하기 위해 한 사이트에 그리고 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다. 여러 인스턴스가 한 계층에 있는 경우 클라이언트가 인증서 등록 지점 중 하나에 임의로 할당됩니다.  

     각 인증서 등록 지점을 사용하려면 네트워크 장치 등록 서비스의 개별 인스턴스에 액세스할 수 있어야 합니다. 두 개 이상의 인증서 등록 지점에서 동일한 네트워크 장치 등록 서비스를 사용하도록 구성할 수는 없습니다. 그 밖에도 네트워크 장치 등록 서비스를 실행하는 동일한 서버에 인증서 등록 지점을 설치하지 않아야 합니다.  

-   **배포 지점** - 클라이언트가 다운로드하는 원본 파일(예: 응용 프로그램 콘텐츠, 소프트웨어 패키지, 소프트웨어 업데이트, 운영 체제 이미지 및 부팅 이미지)을 포함하는 사이트 시스템 역할입니다. 기본적으로 이 역할은 사이트가 설치될 때 새로운 기본 및 보조 사이트의 사이트 서버 컴퓨터에 설치되지만 중앙 관리 사이트에서는 지원되지 않습니다.  지원되는 사이트에 그리고 동일한 계층 내 여러 사이트에 이 역할의 인스턴스를 여러 개 설치할 수 있습니다.  자세한 내용은 [System Center Configuration Manager에서 콘텐츠 관리의 기본 개념](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) 및 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

-   **대체 상태 지점** 클라이언트 설치를 모니터링하고, 관리 지점과 통신할 수 없기 때문에 관리되지 않는 클라이언트를 파악하는 데 도움이 되는 사이트 시스템 역할입니다.  이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 그리고 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  자세한 내용은 [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md)을 참조하세요.


-   **Endpoint Protection 지점** - Configuration Manager가 Endpoint Protection 사용 조건에 동의하고 클라우드 보호 서비스(이전의 MAPS)의 기본 멤버 자격을 구성하는 데 사용하는 사이트 시스템 역할입니다. 계층에서는 이 역할의 단일 인스턴스만 지원하므로, 이 역할의 인스턴스는 계층의 최상위 계층 사이트(중앙 관리 사이트 또는 독립 실행형 기본 사이트)에 있어야 합니다. 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음 중앙 관리 사이트에서 설치해야 합니다. 자세한 내용은 [System Center Configuration Manager의 Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md)을 참조하세요.  

-   **등록 지점** - Configuration Manager의 PKI 인증서를 사용하여 모바일 장치와 Mac 컴퓨터를 등록하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

     사용자가 Configuration Manager를 사용하여 모바일 장치를 등록하고 해당 Active Directory 계정이 사이트 서버의 포리스트에서 트러스트되지 않은 포리스트에 있는 경우, 사용자가 인증받을 수 있도록 사용자의 포리스트에 등록 지점을 설치해야 합니다.  

-   **등록 프록시 지점** - 모바일 장치와 Mac 컴퓨터에서 Configuration Manager 등록 요청을 관리하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

     인터넷을 통해 모바일 장치를 지원하는 경우 보안 모범 사례에 따라 등록 프록시 지점은 경계 네트워크에, 등록 지점은 인트라넷에 설치합니다.  

-   **Exchange Server 커넥터** - 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

-   **관리 지점** - 정책 및 서비스 위치 정보를 클라이언트에 제공하고 클라이언트에서 구성 데이터를 받는 사이트 시스템 역할입니다.  
    기본적으로 이 역할은 사이트가 설치될 때 새로운 기본 및 보조 사이트의 사이트 서버 컴퓨터에 설치됩니다. 기본 사이트에서는 이 역할의 인스턴스를 여러 개 사용할 수 있고, 보조 사이트에서는 컴퓨터 및 사용자 정책을 얻을 수 있는 로컬 연락 지점을 클라이언트에 제공할 때 단일 관리 지점을 사용할 수 있습니다(보조 사이트의 관리 지점은 프록시 관리 지점이라고 함).  

     System Center Configuration Manager 온\-프레미스 모바일 장치 관리로 관리하는 모바일 장치를 지원할 뿐 아니라 HTTP 또는 HTTPs를 지원하도록 관리 지점을 구성할 수 있습니다. [System Center Configuration Manager의 관리 지점용 데이터베이스 복제본](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)을 사용하면 관리 지점이 클라이언트의 요청을 처리할 때 사이트 데이터베이스 서버에 발생시키는 CPU 부하를 줄이는 데 도움이 됩니다.  

-   **보고 서비스 지점** - SQL Server Reporting Services와 통합되어 Configuration Manager용 보고서를 만들고 관리하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트와 중앙 관리 사이트에서 지원되며, 지원되는 사이트에서 이 역할의 여러 인스턴스를 설치할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 보고 계획](../../../core/servers/manage/planning-for-reporting.md)을 참조하세요.  

-   **서비스 연결 지점** - Microsoft Intune 및 온-프레미스 MDM에서 모바일 장치를 관리하는 데 사용하는 사이트 시스템 역할입니다. 이 역할은 사이트의 사용 현황 데이터를 업로드하며 Configuration Manager 콘솔에서 Configuration Manager의 업데이트를 사용하도록 하는 데 필요합니다. 계층에서는 이 역할의 단일 인스턴스만 지원하므로, 이 역할의 인스턴스는 계층의 최상위 계층 사이트(중앙 관리 사이트 또는 독립 실행형 기본 사이트)에 있어야 합니다. 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음 중앙 관리 사이트에서 설치해야 합니다. 자세한 내용은 [About the service connection point in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md)을 참조하십시오.  

-   **소프트웨어 업데이트 지** - WSUS(Windows Server Update Services)와 통합되어 Configuration Manager 클라이언트에 소프트웨어 업데이트를 제공하는 사이트 시스템 역할입니다. 이 역할은 모든 사이트에서 지원됩니다.  

    -   이 사이트 시스템을 Windows Server Update Services와 동기화하도록 중앙 관리 사이트에 설치합니다.  

    -   중앙 관리 사이트와 동기화하도록 자식 기본 사이트에 있는 이 역할의 각 인스턴스를 구성합니다.  

    -   또한 네트워크를 통한 데이터 전송 속도가 느린 경우 보조 사이트에 소프트웨어 업데이트 지점을 설치하는 것을 고려하세요.  

    자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](../../../sum/plan-design/plan-for-software-updates.md)을 참조하세요.  

-   **상태 마이그레이션 지점** - 컴퓨터가 새 운영 체제로 마이그레이션될 때 사용자 상태 데이터를 저장하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트 및 보조 사이트에서 지원되며, 한 사이트에 그리고 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다. 운영 체제를 배포할 때 사용자 상태를 저장하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 사용자 상태 관리](../../../osd/get-started/manage-user-state.md)를 참조하세요.  

-   **시스템 상태 검사기 지점** - 이 사이트 시스템 역할은 Configuration Manager 콘솔에 표시는 되지만 더 이상 System Center Configuration Manager에 사용되지 않습니다.  

##  <a name="a-namebkmkproxya-site-system-roles-that-can-use-a-proxy-server"></a><a name="bkmk_proxy"></a> 프록시 서버를 사용할 수 있는 사이트 시스템 역할  
 일부 Configuration Manager 사이트 시스템 역할은 인터넷에 대한 연결을 필요로 하며, 역할을 호스트하는 사이트 시스템 서버가 구성된 경우에 프록시 서버를 사용합니다. 대개 이러한 인터넷 연결은 사이트 시스템 역할이 설치되는 컴퓨터의 **시스템** 컨텍스트에서 이루어지며 일반적인 사용자 계정에 프록시 구성을 사용할 수 없습니다. 인터넷 연결을 완료하기 위해 프록시 서버가 필요한 경우 컴퓨터에서 프록시 서버를 사용하도록 구성해야 합니다.  

-   사이트 시스템 역할을 설치하는 경우 프록시 서버를 구성할 수 있습니다.  

-   Configuration Manager 콘솔을 사용할 때 프록시 서버 구성을 추가하거나 수정할 수 있습니다.  

-   프록시 서버 구성을 사용할 수 있는 사이트 시스템 서버의 모든 사이트 시스템 역할은 동일한 프록시 서버 구성을 사용합니다. 각 사이트 시스템 역할마다 다른 프록시 서버를 사용해야 하는 경우 모든 사이트 시스템 역할을 서로 다른 사이트 시스템 서버 컴퓨터에 설치해야 합니다.  

-   프록시 서버 구성을 수정하거나 프록시 서버 구성이 이미 있는 컴퓨터에서 새 사이트 시스템 역할을 설치하는 경우 새 구성이 원래 구성을 덮어씁니다.  


사이트 시스템 역할에 대해 프록시 서버를 구성하는 절차는 [System Center Configuration Manager에 대한 사이트 시스템 역할 추가](../../../core/servers/deploy/configure/add-site-system-roles.md) 항목을 참조하세요.  

다음은 프록시 서버를 사용할 수 있는 사이트 시스템 역할입니다.  

-   **Asset Intelligence 동기화 지점** - 이 사이트 시스템 역할은 Microsoft에 연결되며 Asset Intelligence 동기화 지점을 호스트하는 컴퓨터의 프록시 서버 구성을 사용합니다.  

-   **클라우드 기반 배포 지점** - 클라우드 기반 배포 지점을 사용하는 경우 클라우드 기반 배포 지점을 관리하는 기본 사이트가 배포 지점을 프로비전하고 모니터링하며 콘텐츠를 프로비전하기 위해 Microsoft Azure에 연결할 수 있어야 합니다. 이 연결을 위해 프록시 서버가 필요한 경우 기본 사이트 서버에 프록시 서버를 구성해야 합니다. Windows Azure에서 클라우드 기반 배포 지점에 프록시 서버를 구성할 수는 없습니다.  자세한 내용은 [Microsoft Azure에서 클라우드 기반의 System Center Configuration Manager용 배포 지점 설치](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md) 항목의 [클라우드 서비스를 관리하는 기본 사이트의 프록시 설정 구성](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md#BKMK_ConfigProxyforCloud) 섹션을 참조하세요.  

-   **Exchange Server 커넥터** - 이 사이트 시스템 역할은 Exchange Server에 연결되며 Exchange Server 커넥터를 호스트하는 컴퓨터에 프록시 서버 구성을 사용합니다.  

-   **소프트웨어 업데이트 지점** - 이 사이트 시스템 역할에서 패치를 다운로드하고 업데이트 관련 정보를 동기화하려면 Microsoft 업데이트에 대한 연결이 필요할 수 있습니다. 일반적으로, 프록시 서버를 구성할 경우 프록시 서버 사용을 지원하는 해당 컴퓨터에 있는 각 사이트 시스템 역할은 추가 구성 없이도 프록시 서버를 사용하게 됩니다. 그러나 소프트웨어 업데이트 지점은 예외입니다. 기본적으로 소프트웨어 업데이트 지점에서는 사용자가 소프트웨어 업데이트 지점을 구성할 때 다음 옵션도 사용하도록 설정하지 않는 한 제공된 프록시 서버를 사용하지 않습니다.  

    -   **소프트웨어 업데이트를 동기화하는 경우 프록시 서버 사용**  

    -   **자동 배포 규칙을 사용하여 콘텐츠 다운로드 시 프록시 서버 사용**  

    > [!TIP]  
    >  두 옵션을 선택하기 전에 소프트웨어 업데이트 지점을 호스팅하는 사이트 시스템 서버에 프록시 서버를 구성해야 합니다. 프록시 서버는 선택한 특정 옵션에 대해서만 사용됩니다.  

 소프트웨어 업데이트 지점에 대한 프록시 서버와 관련된 자세한 내용은 [소프트웨어 업데이트 지점 설치](../../../sum/get-started/install-a-software-update-point.md) 항목의 프록시 서버 설정 섹션을 참조하세요.  

-   **서비스 연결 지점** - 온라인(오프라인이 아님)으로 구성된 경우 이 사이트 시스템 역할은 Microsoft Intune 및 Microsoft 클라우드 서비스에 연결합니다.  



<!--HONumber=Nov16_HO1-->


