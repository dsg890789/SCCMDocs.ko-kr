---
title: 사이트 시스템 역할 계획
titleSuffix: Configuration Manager
description: Configuration Manager 계층 구조를 계획할 때 사이트 시스템 서버 및 사이트 시스템 역할을 고려하세요.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1af17ad6ac9350c6fb78644b0cc2592f6a529595
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68536672"
---
# <a name="plan-for-site-system-servers-and-site-system-roles-in-configuration-manager"></a>Configuration Manager에서 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

설치하는 각 Configuration Manager 사이트에는 **사이트 시스템 서버**인 사이트 서버가 포함됩니다. 또한 사이트에는 사이트 서버에 원격인 컴퓨터의 추가 사이트 시스템 서버도 포함될 수 있습니다. 사이트 시스템 서버(사이트 서버 또는 원격 사이트 시스템 서버)에서는 **사이트 시스템 역할**을 지원합니다.  

## <a name="bkmk_siteservers"></a> 사이트 시스템 서버  

컴퓨터에 사이트 시스템 역할을 설치하면 해당 컴퓨터가 사이트 시스템 서버가 됩니다. 각 사이트에서 하나 이상의 추가 사이트 시스템 서버를 설치할 수 있습니다. 추가 사이트 시스템 서버를 설치할 필요가 없으며, 사이트 서버 컴퓨터에서 직접 모든 사이트 시스템 역할을 실행하도록 선택할 수도 있습니다. 각 사이트 시스템 서버는 하나 이상의 사이트 시스템 역할을 지원합니다. 추가 서버는 사이트 시스템 역할이 서버에 지정하는 처리 부하를 공유하여 사이트의 기능 및 용량을 확장할 수 있습니다.  

사이트 시스템 서버의 추가를 고려하는 경우 서버가 용도에 대한 필수 조건을 충족해야 합니다. 또한 예상되는 엔드포인트와 통신하기에 충분한 대역폭이 있는 네트워크 위치에 추가합니다. 이러한 엔드포인트에는 사이트 서버, 도메인 리소스, 클라우드 기반 위치, 사이트 시스템 서버 및 클라이언트가 포함됩니다.  


## <a name="bkmk_planroles"></a> 사이트 시스템 역할  

사이트 시스템 역할을 서버에 설치하여 사이트에 추가 기능을 제공합니다. 다음과 같은 경우를 예로 들 수 있습니다.  

- 추가 관리 지점. 사이트는 사이트의 최대 지원 용량까지 더 많은 디바이스를 지원할 수 있습니다.  

- 콘텐츠 인프라를 확장할 추가 배포 지점. 디바이스에 콘텐츠를 배포하는 성능을 높일 수 있습니다.  

- 하나 이상의 기능별 사이트 시스템 역할. 예를 들어 소프트웨어 업데이트 지점을 통해 관리되는 디바이스에 대한 소프트웨어 업데이트를 관리할 수 있습니다. 보고 서비스 지점을 통해 사용자 환경에 대한 정보를 모니터링, 이해 및 공유하기 위한 보고서를 실행할 수 있습니다.  

Configuration Manager 사이트마다 다른 사이트 시스템 역할을 지원할 수 있습니다. 사이트 시스템 역할의 지원되는 집합은 사이트의 유형에 따라 달라집니다. (사이트 유형에는 중앙 관리 사이트, 기본 사이트 또는 보조 사이트가 포함됩니다.) 계층의 토폴로지는 특정 사이트 유형에서 일부 역할의 배치를 제한할 수 있습니다. 예를 들어, 서비스 연결 지점은 계층의 최상위 계층 사이트에서만 지원됩니다. 최상위 계층 사이트는 중앙 관리 사이트 또는 독립 실행형 기본 사이트가 될 수 있습니다. 이 역할은 자식 기본 사이트 또는 보조 사이트에서 지원되지 않습니다.  

사이트 설치 후 일부 사이트 시스템 역할의 위치를 사이트 서버의 기본 위치에서 다른 서버로 이동할 수 있습니다. 예를 들어 관리 지점 또는 배포 지점 역할은 기본적으로 기본 또는 보조 사이트 서버에 설치합니다. 또한 일부 사이트 시스템 역할의 추가 인스턴스를 설치하여 사이트의 기능을 확장하고 비즈니스 요구 사항을 충족할 수 있습니다. 일부 역할은 필수이지만 나머지는 선택 사항입니다.  

### <a name="configuration-manager-site-server"></a>Configuration Manager 사이트 서버

이 역할은 사이트 설치를 위해 Configuration Manager 설치 프로그램이 실행되는 서버 또는 보조 사이트가 설치되는 서버를 식별합니다. 이 역할은 사이트를 제거할 때까지 이동하거나 제거할 수 없습니다.  

### <a name="configuration-manager-site-system"></a>Configuration Manager 사이트 시스템

이 역할은 사이트를 설치하거나 사이트 시스템 역할을 설치할 컴퓨터에 할당됩니다. 이 역할은 컴퓨터에서 마지막 사이트 시스템 역할을 제거할 때까지 이동하거나 제거할 수 없습니다.  

### <a name="configuration-manager-component-site-system-role"></a>Configuration Manager 구성 요소 사이트 시스템 역할

이 역할은 **SMS Executive** 서비스의 인스턴스를 실행하는 사이트 시스템을 식별합니다. 관리 지점과 같은 다른 역할을 지원하는 데 필요합니다. 이 역할은 컴퓨터에서 마지막 해당하는 사이트 시스템 역할을 제거할 때까지 이동하거나 제거할 수 없습니다.  

### <a name="configuration-manager-site-database-server"></a>Configuration Manager 사이트 데이터베이스 서버

사이트는 이 역할을 사이트 데이터베이스의 인스턴스를 보유하는 사이트 시스템 서버에 할당합니다. 이 역할은 사이트 데이터베이스를 호스트하는 데 SQL Server의 다른 인스턴스를 사용하도록 사이트를 수정하는 설치 프로그램을 실행하여 새 서버로만 옮길 수 있습니다.  

### <a name="sms-provider"></a>사이트 데이터베이스

사이트가 SMS 공급자의 인스턴스를 호스트하는 각 컴퓨터에 이 역할을 할당합니다. 공급자는 Configuration Manager 콘솔과 사이트 데이터베이스 사이의 인터페이스입니다. 기본적으로 이 역할은 중앙 관리 사이트 및 기본 사이트의 사이트 서버에 자동으로 설치됩니다. 추가 관리자가 액세스할 수 있도록 또는 중복성을 위해 각 사이트에서 추가 인스턴스를 설치할 수 있습니다.  

추가 공급자를 설치하려면 [SMS 공급자를 관리](/sccm/core/servers/manage/modify-your-infrastructure#BKMK_ManageSMSprovider)할 Configuration Manager 설치 프로그램을 실행합니다. 그런 다음, 추가 컴퓨터에 추가 공급자를 설치합니다. 컴퓨터에서 SMS 공급자의 인스턴스를 하나만 설치합니다. 해당 컴퓨터는 사이트 서버와 동일한 도메인에 있어야 합니다.  

### <a name="application-catalog-web-service-point"></a>애플리케이션 카탈로그 웹 서비스 지점

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터는 업데이트된 클라이언트가 사용자 이용 가능 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 2019년 10월 31일 이후 첫 번째 현재 분기 릴리스에서는 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

소프트웨어 라이브러리에서 애플리케이션 카탈로그 웹 사이트로 소프트웨어 정보를 제공하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

### <a name="application-catalog-website-point"></a>애플리케이션 카탈로그 웹 사이트 지점

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터는 업데이트된 클라이언트가 사용자 이용 가능 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 2019년 10월 31일 이후 첫 번째 현재 분기 릴리스에서는 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

애플리케이션 카탈로그에서 사용 가능한 소프트웨어 목록을 사용자에게 제공하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

### <a name="asset-intelligence-synchronization-point"></a>Asset Intelligence 동기화 지점

Asset Intelligence 카탈로그의 정보를 다운로드하도록 Microsoft에 연결하는 사이트 시스템 역할입니다. 또한 이 역할은 범주화되지 않은 타이틀을 업로드하므로 Microsoft는 나중에 카탈로그에 포함되는 것으로 간주할 수도 있습니다. 계층 구조는 사용자 계층의 최상위 계층 사이트에서 이 역할의 단일 인스턴스를 지원합니다. 더 큰 계층으로 독립 실행형 기본 사이트를 확장하는 경우 기본 사이트에서 이 역할을 제거합니다. 그런 다음, 중앙 관리 사이트에서 설치합니다.

자세한 내용은 [Configuration Manager의 Asset Intelligence](/sccm/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence)를 참조하세요.  

### <a name="certificate-registration-point"></a>인증서 등록 지점

NDES(네트워크 디바이스 등록 서비스)를 실행하는 서버와 통신하는 사이트 시스템 역할입니다. 이 역할은 SCEP(단순 인증서 등록 프로토콜)를 사용하는 디바이스 인증서 요청을 관리합니다. 이 역할은 기본 사이트와 중앙 관리 사이트에서만 지원됩니다.

단일 인증서 등록 지점에서 전체 계층에 기능을 제공할 수 있지만 한 사이트에 그리고 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다. 이 디자인은 부하 분산에 도움이 됩니다. 여러 인스턴스가 한 계층에 있는 경우 클라이언트가 인증서 등록 지점 중 하나에 임의로 할당됩니다.  

각 인증서 등록 지점은 개별 NDES 인스턴스에 액세스할 수 있어야 합니다. 두 개 이상의 인증서 등록 지점에서 동일한 NDES 인스턴스를 사용하도록 구성할 수는 없습니다. 또한 NDES를 실행하는 동일한 서버에 인증서 등록 지점을 설치하지 마세요.  

### <a name="cloud-management-gateway-connection-point"></a>클라우드 관리 게이트웨이 연결점

[클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)와 통신하기 위한 사이트 시스템 역할입니다.  

### <a name="data-warehouse-service-point"></a>데이터 웨어하우스 서비스 지점

데이터 웨어하우스 서비스 지점을 사용하여 Configuration Manager 환경에서 장기 기록 데이터를 저장하고 보고합니다. 자세한 내용은 [데이터 웨어하우스](/sccm/core/servers/manage/data-warehouse)를 참조하세요.  

### <a name="distribution-point"></a>배포 지점

클라이언트가 다운로드할 원본 파일을 포함하는 다음과 같은 사이트 시스템 역할입니다.

- 애플리케이션 콘텐츠
- 소프트웨어 패키지
- 소프트웨어 업데이트
- OS 이미지
- 부팅 이미지  

기본적으로 이 역할은 새로운 기본 또는 보조 사이트를 설치할 때 사이트 서버에 설치됩니다. 이 역할은 중앙 관리 사이트에서 지원되지 않습니다. 지원되는 사이트 및 동일한 계층 내 여러 사이트에서 이 역할의 인스턴스를 여러 개 설치합니다. 자세한 내용은 [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) 및 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  

### <a name="endpoint-protection-point"></a>Endpoint Protection 지점

Configuration Manager가 Endpoint Protection 사용 조건에 동의하고 클라우드 보호 서비스의 기본 멤버 자격을 구성하는 데 사용하는 사이트 시스템 역할입니다. 계층 구조는 이 역할의 단일 인스턴스만 지원하며, 최상위 계층 사이트에 있어야 합니다. 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음, 중앙 관리 사이트에서 설치합니다. 자세한 내용은 [Configuration Manager의 Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.  

### <a name="enrollment-point"></a>등록 지점

모바일 디바이스와 macOS 컴퓨터를 등록하기 위해 Configuration Manager의 PKI 인증서를 사용하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

사용자가 Configuration Manager를 사용하여 모바일 디바이스를 등록하고 사용자의 Active Directory 계정이 사이트 서버의 포리스트에서 트러스트되지 않은 포리스트에 있는 경우, 사용자의 포리스트에 등록 지점을 설치합니다. 그런 다음, Configuration Manager는 사용자를 인증할 수 있습니다.  

### <a name="enrollment-proxy-point"></a>등록 프록시 지점

모바일 디바이스와 macOS 컴퓨터에서 Configuration Manager 등록 요청을 관리하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트에 또는 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.  

인터넷을 통해 모바일 디바이스를 지원하는 경우 등록 프록시 지점은 경계 네트워크에, 등록 지점은 인트라넷에 설치합니다.

### <a name="exchange-server-connector"></a>Exchange Server 커넥터

이 역할에 대한 자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  

### <a name="fallback-status-point"></a>대체 상태 지점

클라이언트 설치를 모니터링하는 데 유용한 사이트 시스템 역할입니다. 관리 지점과 통신할 수 없어 관리되지 않는 클라이언트를 식별합니다. 이 역할은 기본 사이트에서만 지원되지만, 한 사이트 및 동일한 계층의 여러 사이트에 이 역할의 여러 인스턴스를 설치할 수 있습니다.

### <a name="management-point"></a>관리 지점

정책 및 서비스 위치 정보를 클라이언트에게 제공하는 사이트 시스템 역할입니다. 또한 클라이언트로부터 구성 데이터를 받습니다.  

기본적으로 이 역할은 새로운 기본 또는 보조 사이트를 설치할 때 사이트 서버에 설치됩니다. 기본 사이트에서는 이 역할의 여러 인스턴스를 지원합니다. 보조 사이트는 단일 관리 지점을 지원합니다. 프록시 관리 지점이라고도 하는 이 역할은 보조 사이트에서 컴퓨터 및 사용자 정책을 가져오기 위해 클라이언트에 대한 연결 로컬 지점을 제공합니다.  

HTTP 또는 HTTPs를 지원하도록 관리 지점을 설정합니다. 또한 Configuration Manager 온-프레미스 MDM(모바일 디바이스 관리)을 통해 관리하는 모바일 디바이스를 지원할 수 있습니다. 클라이언트의 요청을 처리하는 관리 지점이 사이트 데이터베이스 서버에 적용하는 프로세스 부하를 줄이려면 [관리 지점용 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 사용합니다.  

### <a name="reporting-services-point"></a>보고 서비스 지점

SQL Server Reporting Services와 통합되어 Configuration Manager용 보고서를 만들고 관리하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트와 중앙 관리 사이트에서 지원되며, 지원되는 사이트에서 이 역할의 여러 인스턴스를 설치할 수 있습니다. 자세한 내용은 [보고 계획](/sccm/core/servers/manage/planning-for-reporting)을 참조하세요.  

### <a name="service-connection-point"></a>서비스 연결 지점

사이트에서 사용 현황 데이터를 업로드하는 사이트 시스템 역할로, 콘솔에서 Configuration Manager에 대한 업데이트를 사용하도록 하는 데 필요합니다. 이 역할을 또한 Microsoft Intune 및 온-프레미스 MDM에서 모바일 디바이스를 관리하는 데 유용합니다. 계층 구조는 이 역할의 단일 인스턴스만 지원하며, 계층 구조의 최상위 계층 사이트에 있어야 합니다. 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음, 중앙 관리 사이트에서 설치합니다. 자세한 내용은 [서비스 연결 지점 정보](/sccm/core/servers/deploy/configure/about-the-service-connection-point)를 참조하세요.  

### <a name="software-update-point"></a>소프트웨어 업데이트 지점

WSUS(Windows Server Update Services)와 통합되어 Configuration Manager 클라이언트에 소프트웨어 업데이트를 제공하는 사이트 시스템 역할입니다. 이 역할은 모든 사이트에서 지원됩니다.  

- WSUS와 동기화하도록 중앙 관리 사이트에 이 사이트 시스템을 설치합니다.  

- 중앙 관리 사이트와 동기화하도록 자식 기본 사이트에 있는 이 역할의 각 인스턴스를 설정합니다.  

- 네트워크를 통한 데이터 전송 속도가 느린 경우 보조 사이트에 소프트웨어 업데이트 지점을 설치하는 것을 고려하세요.  

자세한 내용은 [소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates)을 참조하세요.  

### <a name="state-migration-point"></a>상태 마이그레이션 지점

컴퓨터를 새 운영 체제로 마이그레이션하는 경우 사용자 상태 데이터를 저장하는 사이트 시스템 역할입니다. 이 역할은 기본 사이트 및 보조 사이트에서 지원됩니다. 한 사이트 및 동일한 계층 내 여러 사이트에 이 역할의 인스턴스를 여러 개 설치합니다. OS를 배포할 때 사용자 상태를 저장하는 방법에 대한 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  


## <a name="next-steps"></a>다음 단계

일부 Configuration Manager 사이트 시스템 역할은 인터넷 연결이 필요합니다. 사용자 환경에서 프록시 서버를 사용하기 위해 인터넷 트래픽이 필요한 경우 프록시를 사용하도록 이러한 사이트 시스템 역할을 구성합니다. 자세한 내용은 [프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support)을 참조하세요.  
