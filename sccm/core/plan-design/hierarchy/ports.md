---
title: 연결에 사용되는 포트
titleSuffix: Configuration Manager
description: Configuration Manager가 연결에 사용하는 필수 및 사용자 지정 네트워크 포트에 대해 알아봅니다.
ms.date: 04/11/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c6777fb0-0754-4abf-8a1b-7639d23e9391
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8818f858900db76192df1503d9043e6435a4999
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68338692"
---
# <a name="ports-used-in-configuration-manager"></a>Configuration Manager에서 사용되는 포트

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager가 사용하는 네트워크 포트를 나열합니다. 일부 연결은 구성할 수 없는 포트를 사용하고, 일부 연결은 지정하는 사용자 지정 포트를 지원합니다. 포트 필터링 기술을 사용하는 경우 필수 포트를 사용할 수 있는지 확인합니다. 이러한 포트 필터링 기술에는 방화벽, 라우터, 프록시 서버 또는 IPsec이 포함됩니다.   

> [!NOTE]  
> SSL 브리징을 사용하여 인터넷 기반 클라이언트를 지원하는 경우 포트 요구 사항 외에 방화벽을 트래버스할 수 있도록 일부 HTTP 동사 및 헤더를 허용해야 할 수 있습니다.   



##  <a name="BKMK_ConfigurablePorts"></a> 구성할 수 있는 포트  
Configuration Manager를 사용하여 다음 유형의 통신에 대한 포트를 구성할 수 있습니다.  

- 애플리케이션 카탈로그 웹 사이트 지점과 애플리케이션 카탈로그 웹 서비스 지점 간의 통신  

- 등록 프록시 지점과 등록 지점 간의 통신  

- 클라이언트와 IIS를 실행하는 사이트 시스템 간의 통신  

- 클라이언트와 인터넷 간의 통신(프록시 서버 설정 사용)  

- 소프트웨어 업데이트 지점과 인터넷 간의 통신(프록시 서버 설정 사용)  

- 소프트웨어 업데이트 지점과 WSUS 서버 간의 통신  

- 사이트 서버와 사이트 데이터베이스 서버 간의 통신  

- 보고 서비스 지점  

  > [!NOTE]  
  > 보고 서비스 지점의 사이트 시스템 역할에 사용되는 포트는 SQL Server Reporting Services에 구성됩니다. 그런 다음 이러한 포트는 보고 서비스 지점과 통신하는 동안 Configuration Manager에 사용됩니다. IPsec 정책 또는 방화벽 구성의 IP 필터 정보를 정의하는 이러한 포트를 검토해야 합니다.  

기본적으로 클라이언트와 사이트 시스템 간의 통신에 사용되는 HTTP 포트는 80이고 기본 HTTPS 포트는 443입니다. HTTP 또는 HTTPS를 통한 클라이언트 및 사이트 시스템 간 통신용 포트는 설치 중에 변경할 수도 있고 Configuration Manager 사이트의 사이트 속성에서 변경할 수도 있습니다.  

보고 서비스 지점의 사이트 시스템 역할에 사용되는 포트는 SQL Server Reporting Services에 구성됩니다. 그런 다음 이러한 포트는 보고 서비스 지점과 통신하는 동안 Configuration Manager에 사용됩니다. IPsec 정책 또는 방화벽 구성의 IP 필터 정보를 정의하는 경우 이러한 포트를 검토해야 합니다.  



##  <a name="BKMK_NonConfigurablePorts"></a> 구성할 수 없는 포트  

Configuration Manager를 사용하여 다음 유형의 통신에 대한 포트를 구성할 수 없습니다.  

- 사이트 간 통신  

- 사이트 서버와 사이트 시스템 간 통신  

- Configuration Manager 콘솔과 SMS 공급자 간 통신  

- Configuration Manager 콘솔과 인터넷 간 통신  

- Microsoft Intune 및 클라우드 배포 지점 등 클라우드 서비스와의 연결  



##  <a name="BKMK_CommunicationPorts"></a> Configuration Manager 클라이언트 및 사이트 시스템에 사용되는 포트  

다음 섹션에서는 Configuration Manager의 통신에 사용되는 포트에 대해 자세히 설명합니다. 섹션 제목의 화살표는 통신 방향을 보여줍니다.  

- -- &gt; 한 컴퓨터에서 통신을 시작하고 다른 쪽 컴퓨터는 항상 응답함을 나타냅니다.  

- &lt; -- &gt; 어느 쪽 컴퓨터든 통신을 시작할 수 있음을 나타냅니다.  


###  <a name="BKMK_PortsAI"></a> Asset Intelligence 동기화 지점 -- &gt; Microsoft  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  


###  <a name="BKMK_PortsAI-to-SQL"></a> Asset Intelligence 동기화 지점 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsAppCatalogService-SQL"></a> 애플리케이션 카탈로그 웹 서비스 지점 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsAppCatalogWebSitePoint_AppCatalogWebServicePoint"></a> 애플리케이션 카탈로그 웹 사이트 지점 -- &gt; 애플리케이션 카탈로그 웹 서비스 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsClient-AppCatalogWebsitePoint"></a> 클라이언트 -- &gt; 애플리케이션 카탈로그 웹 사이트 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsClient-ClientWakeUp"></a> 클라이언트 -- &gt; 클라이언트  

이 테이블에 나열된 포트 외에도 절전 모드 해제 프록시도 클라이언트 간에 ICMP 에코 요청 메시지를 사용합니다. 클라이언트는 이 통신을 사용하여 네트워크의 다른 클라이언트가 절전 모드에서 해제되었는지 여부를 확인합니다. ICMP는 Ping 명령이라고도 합니다. ICMP에는 UDP 또는 TCP 프로토콜 번호가 없으므로 다음 표에는 나열되지 않습니다. 하지만 이러한 클라이언트 컴퓨터의 호스트 기반 방화벽이나 서브넷 내에 장애가 있는 네트워크 디바이스에서 ICMP 트래픽을 허용해야 절전 모드 해제 프록시 통신이 성공합니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|Wake On LAN|9 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|--|  
|절전 모드 해제 프록시|25536 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|--|  
|Windows PE 피어 캐시 브로드캐스트|8004|--|  
|Windows PE 피어 캐시 다운로드|--|8003|  

자세한 내용은 [Windows PE 피어 캐시](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic#BKMK_PeerCacheRequirements)를 참조하세요.


###  <a name="BKMK_PortsClient-PolicyModule"></a> 클라이언트 -- &gt; Configuration Manager NDES(네트워크 디바이스 등록 서비스) 정책 모듈   

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP||80|  
|HTTPS|--|443|  


###  <a name="BKMK_PortsClient-CloudDP"></a> 클라이언트 -- > 클라우드 배포 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  

자세한 내용은 [포트 및 데이터 흐름](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_dataflow)을 참조하세요.


###  <a name="bkmk_client-cmg"></a> 클라이언트 -- > CMG(클라우드 관리 게이트웨이)  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  

자세한 내용은 [CMG 포트 및 데이터 흐름](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#ports-and-data-flow)을 참조하세요.


###  <a name="BKMK_PortsClient-DP"></a> 클라이언트 -- &gt; 배포 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsClient-DP2"></a> 클라이언트 -- &gt; 멀티캐스트에 구성된 배포 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|멀티캐스트 프로토콜|63000-64000|--|  

###  <a name="BKMK_PortsClient-DP3"></a> 클라이언트 -- &gt; PXE에 구성된 배포 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|DHCP|67 및 68|--|  
|TFTP|69 <sup>[참고 4](#bkmk_note4)</sup> |--|  
|BINL(Boot Information Negotiation Layer)|4011|--|  

> [!Important]  
> 호스트 기반 방화벽을 사용하도록 설정한 경우 규칙이 서버가 이러한 포트에서 송수신하도록 허용하는지 확인합니다. PXE에 대한 분산 지점을 사용하는 경우 Configuration Manager는 Windows 방화벽에서 인바운드(수신) 규칙을 사용하도록 설정할 수 있습니다. 아웃바운드(송신) 규칙을 구성하지는 않습니다.<!--SCCMDocs issue #744-->  


###  <a name="BKMK_PortsClient-FSP"></a> 클라이언트 -- &gt; 대체 상태 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsClient-GCDC"></a> 클라이언트 -- &gt; 글로벌 카탈로그 도메인 컨트롤러  
Configuration Manager 클라이언트는 글로벌 카탈로그 서버가 작업 그룹 컴퓨터인 경우나 인터넷 전용 통신용으로 구성된 경우 글로벌 카탈로그 서버를 연결하지 않습니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|글로벌 카탈로그 LDAP|--|3268|  


###  <a name="BKMK_PortsClient-MP"></a> 클라이언트 -- &gt; 관리 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|클라이언트 알림(HTTP 또는 HTTPS로 대체되기 이전의 기본 통신)|--|10123 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsClient-SUP"></a> 클라이언트 -- &gt; 소프트웨어 업데이트 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 또는 8530 <sup>[참고 3](#bkmk_note3)</sup>|  
|HTTPS|--|443 또는 8531 <sup>[참고 3](#bkmk_note3)</sup>|  


###  <a name="BKMK_PortsClient-SMP"></a> 클라이언트 -- &gt; 상태 마이그레이션 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|SMB(서버 메시지 블록)|--|445|  


###  <a name="bkmk_cmgcp-cmg"></a> CMG 연결 지점 --> CMG 클라우드 서비스  

Configuration Manager는 이러한 연결을 사용하여 CMG 채널을 빌드합니다. 자세한 내용은 [CMG 포트 및 데이터 흐름](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#ports-and-data-flow)을 참조하세요.

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|TCP-TLS(기본 설정)|--|10140-10155|  
|HTTPS(한 개의 VM으로 대체)|--|443|  
|HTTPS(두 개 이상의 VM으로 대체)|--|10124-10139|  


###  <a name="bkmk_cmgcp-mp"></a> CMG 연결 지점 -- > 관리 지점  

#### <a name="version-1706-or-1710"></a>버전 1706 또는 1710
특정 포트는 관리 지점 구성에 따라 달라집니다. 

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|
|HTTP|--|80|  

#### <a name="version-1802"></a>1802 버전

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|

자세한 내용은 [CMG 포트 및 데이터 흐름](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#ports-and-data-flow)을 참조하세요.


###  <a name="bkmk_cmgcp-sup"></a> CMG 연결 지점 -- > 소프트웨어 업데이트 지점  

특정 포트는 소프트웨어 업데이트 지점 구성에 따라 달라집니다. 

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|
|HTTP|--|80|  

자세한 내용은 [CMG 포트 및 데이터 흐름](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#ports-and-data-flow)을 참조하세요.


###  <a name="BKMK_PortsConsole-Client"></a> Configuration Manager 콘솔 -- &gt; 클라이언트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|원격 제어(제어)|--|2701|  
|원격 지원(RDP 및 RTC)|--|3389|  


###  <a name="BKMK_PortsConsole-Internet"></a> Configuration Manager 콘솔 -- &gt; 인터넷  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80|  
|HTTPS|--|443|

Configuration Manager 콘솔은 다음 구성에 대해 인터넷 액세스를 사용합니다. 
- Microsoft 업데이트에서 배포 패키지에 대한 소프트웨어 업데이트 다운로드.
- 리본의 피드백 항목.
- 콘솔 내 문서에 대한 링크.
<!--506823-->


###  <a name="BKMK_PortsConsole-RSP"></a> Configuration Manager 콘솔 -- > 보고 서비스 지점  


|설명|UDP|TCP|
|-----------------|---------|---------|   
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsConsole-Site"></a> Configuration Manager 콘솔 -- &gt; 사이트 서버  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|RPC(공급자 시스템을 찾기 위해 초기에 WMI에 연결)|--|135|  


###  <a name="BKMK_PortsConsole-Provider"></a> Configuration Manager 콘솔 -- &gt; SMS 공급자  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsCertificateRegistationPoint_PolicyModule"></a> Configuration Manager NDES(네트워크 장치 등록 서비스) -- > 인증서 등록 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsDWSPSQL"></a> 데이터 웨어하우스 서비스 지점 -- > SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsDist_MP"></a> 배포 지점 -- &gt; 관리 지점  
배포 지점은 다음과 같은 시나리오에서 관리 지점과 통신합니다.  

- 사전 준비된 콘텐츠의 상태를 보고하려면  

- 사용 요약 데이터 보고  

- 콘텐츠 유효성 검사 보고  

- 패키지 다운로드(풀(pull) 배포 지점)의 상태를 보고하려면

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsEndpointProtection_Internet"></a> Endpoint Protection 지점 -- &gt; 인터넷  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80|  


###  <a name="BKMK_PortsEP-to-SQL"></a> Endpoint Protection 지점 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsEnrollmentProxyEnrollmentPoint"></a> 등록 프록시 지점 -- &gt; 등록 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsEnrollmentEnrollmentSQL"></a> 등록 지점 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsExchangeConnectorHosted"></a> Exchange Server 커넥터 -- &gt; Exchange Online  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS를 통한 Windows 원격 관리|--|5986|  


###  <a name="BKMK_PortsExchangeConnectorOnPrem"></a> Exchange Server 커넥터 -- &gt; 온-프레미스 Exchange Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP를 통한 Windows 원격 관리|--|5985|  


###  <a name="BKMK_PortsMacEnrollmentProxyPoint"></a> Mac 컴퓨터 -- &gt; 등록 프록시 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  


###  <a name="BKMK_PortsMP-DC"></a> 관리 지점 -- &gt; 도메인 컨트롤러  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|LDAP(Lightweight Directory Access Protocol)|389|389|  
|글로벌 카탈로그 LDAP|--|3268|  
|RPC 엔드포인트 매퍼|--|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsMP-Site"></a> 관리 지점 &lt; -- &gt; 사이트 서버  
<sup>[참고 5](#bkmk_note5)</sup>   

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|RPC 엔드포인트 매퍼|--|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  
|SMB(서버 메시지 블록)|--|445|  


###  <a name="BKMK_PortsMP-SQL"></a> 관리 지점 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsMobileDeviceClient-EnrollmentProxyPoint"></a> 모바일 디바이스 -- &gt; 등록 프록시 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  


###  <a name="BKMK_PortsMobileDeviceClient-WindowsIntune"></a> 모바일 디바이스 -- &gt; Microsoft Intune  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  


###  <a name="BKMK_PortsRSP-SQL"></a> 보고 서비스 지점 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsIntuneConnector-WindowsIntune"></a> 서비스 연결 지점 -- &gt; Microsoft Intune  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|

자세한 내용은 서비스 연결 지점에 대한 [인터넷 액세스 요구 사항](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)을 참조하세요.


###  <a name="bkmk_scp-cmg"></a> 서비스 연결 지점 -- > Azure(CMG)  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|CMG 서비스 배포에 대한 HTTPS|--|443|

자세한 내용은 [CMG 포트 및 데이터 흐름](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#ports-and-data-flow)을 참조하세요.


###  <a name="BKMK_PortsAppCatalogWebServicePoint_SiteServer"></a> 사이트 서버 &lt; -- &gt; 애플리케이션 카탈로그 웹 서비스 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsAppCatalogWebSitePoint_SiteServer"></a> 사이트 서버 &lt; -- &gt; 애플리케이션 카탈로그 웹 사이트 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-AISP"></a> 사이트 서버 &lt; -- &gt; Asset Intelligence 동기화 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-Client"></a> 사이트 서버 -- &gt; 클라이언트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|Wake On LAN|9 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|--|  


###  <a name="BKMK_PortsSiteServer-CloudDP"></a> 사이트 서버 -- > 클라우드 배포 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS|--|443|  

자세한 내용은 [포트 및 데이터 흐름](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_dataflow)을 참조하세요.


###  <a name="BKMK_PortsSite-DP"></a> 사이트 서버 -- &gt; 배포 지점  
 <sup>[참고 5](#bkmk_note5)</sup>  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-DC"></a> 사이트 서버 -- &gt; 도메인 컨트롤러  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|LDAP(Lightweight Directory Access Protocol)|389|389|  
|글로벌 카탈로그 LDAP|--|3268|  
|RPC 엔드포인트 매퍼|--|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsCertificateRegistrationPoint_SiteServer"></a> 사이트 서버 &lt; -- &gt; 인증서 등록 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsEndpointProtection_SiteServer"></a> 사이트 서버 &lt; -- &gt; Endpoint Protection 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_EnrollmentPoint_SiteServer"></a> 사이트 서버 &lt; -- &gt; 등록 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_EnrollmentProxyPoint_SiteServer"></a> 사이트 서버 &lt; -- &gt; 등록 프록시 지점  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-FSP"></a> 사이트 서버 &lt; -- &gt; 대체 상태 지점  
 <sup>[참고 5](#bkmk_note5)</sup>  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortSite-Internet"></a> 사이트 서버 -- &gt; 인터넷  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 1](#bkmk_note1)</sup>|  


###  <a name="BKMK_PortsIssuingCA_SiteServer"></a> 사이트 서버 &lt; -- &gt; 발급 CA(인증 기관)  
 이 통신은 인증서 등록 지점을 사용하여 인증서 프로필을 배포할 때 사용됩니다. 이 통신은 계층 구조의 모든 사이트 서버에 사용되지 않고 계층 구조의 최상위에 있는 사이트 서버에만 사용됩니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC(DCOM)|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-RCL"></a> 사이트 서버 -- > 원격 콘텐츠 라이브러리 공유를 호스팅하는 서버  
버전 1806부터 중앙 관리 또는 기본 사이트 서버에서 하드 드라이브 공간을 확보하기 위해 다른 스토리지 위치로 콘텐츠 라이브러리의 위치를 변경할 수 있습니다. 자세한 내용은 [사이트 서버에 대해 원격 콘텐츠 라이브러리 구성](/sccm/core/plan-design/hierarchy/the-content-library#bkmk_remote)을 참조합니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  


###  <a name="BKMK_PortsSite-RSP"></a> 사이트 서버 &lt; -- &gt; 보고 서비스 지점  
 <sup>[참고 5](#bkmk_note5)</sup>  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-Site"></a> 사이트 서버 &lt; -- &gt; 사이트 서버  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  


###  <a name="BKMK_PortsSite-SQL"></a> 사이트 서버 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  

 원격 SQL Server를 사용하여 사이트 데이터베이스를 호스팅하는 사이트 설치 중에 사이트 서버와 SQL Server 간에 다음과 같은 포트를 엽니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-Provider"></a> 사이트 서버 -- &gt; SMS 공급자  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  
|RPC|--|동적 <sup>[참고 6](#bkmk_note6)</sup>|  


###  <a name="BKMK_PortsSite-SUP"></a> 사이트 서버 &lt; -- &gt; 소프트웨어 업데이트 지점  
 <sup>[참고 5](#bkmk_note5)</sup>  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|HTTP|--|80 또는 8530 <sup>[참고 3](#bkmk_note3)</sup>|  
|HTTPS|--|443 또는 8531 <sup>[참고 3](#bkmk_note3)</sup>|  


###  <a name="BKMK_PortsSite-SMP"></a> 사이트 서버 &lt; -- &gt; 상태 마이그레이션 지점  
 <sup>[참고 5](#bkmk_note5)</sup>  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  
|RPC 엔드포인트 매퍼|135|135|  


###  <a name="BKMK_PortsProvider-SQL"></a> SMS 공급자 -- &gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMK_PortsSUP-Internet"></a> 소프트웨어 업데이트 지점 -- &gt; 인터넷  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 <sup>[참고 1](#bkmk_note1)</sup>|  


###  <a name="BKMK_PortsSUP-WSUS"></a> 소프트웨어 업데이트 지점 -- &gt; 업스트림 WSUS 서버  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP|--|80 또는 8530 <sup>[참고 3](#bkmk_note3)</sup>|  
|HTTPS|--|443 또는 8531 <sup>[참고 3](#bkmk_note3)</sup>|  


###  <a name="BKMK_PortsSQL-SQL"></a> SQL Server-- &gt; SQL Server  
 사이트 간 데이터베이스 복제를 사용하려면 해당 부모 또는 자식 사이트의 SQL Server와 직접 통신하는 한 사이트에 SQL Server를 설치해야 합니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL Server 서비스|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  
|SQL Server Service Broker|--|4022 <sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  

> [!TIP]  
>  Configuration Manager에는 UDP 1434 포트를 사용하는 SQL Server Browser가 필요하지 않습니다.  


###  <a name="BKMK_PortsStateMigrationPoint-to-SQL"></a> 상태 마이그레이션 지점 --&gt; SQL Server  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SQL over TCP|--|1433<sup>[참고 2](#bkmk_note2) 대체 포트 사용 가능</sup>|  


###  <a name="BKMY_PortNotes"></a> Configuration Manager 클라이언트 및 사이트 시스템에 사용되는 포트에 대한 참고 사항  

#### <a name="bkmk_note1"></a> 참고 1: 프록시 서버 포트
이 포트는 구성할 수 없지만 구성된 프록시 서버를 통해 라우팅될 수 있습니다.  

#### <a name="bkmk_note2"></a> 참고 2: 대체 포트 사용 가능
이 값에 대해 Configuration Manager 내에서 대체 포트를 정의할 수 있습니다. 사용자 지정 포트가 정의된 경우 IPsec 정책 또는 방화벽 구성의 IP 필터 정보를 정의할 때 해당 사용자 지정 포트를 대체해야 합니다.  

#### <a name="bkmk_note3"></a> 참고 3: WSUS(Windows Server Update Services)
클라이언트 통신용으로 포트 80/443 또는 포트 8530/8531에 WSUS를 설치할 수 있습니다. Windows Server 2012 또는 Windows Server 2016에서 실행하는 WSUS는 기본적으로 HTTP에는 포트 8530을 사용하고 HTTPS에는 포트 8531을 사용하도록 구성됩니다.  

설치 후에 포트를 변경할 수 있습니다. 사이트 계층 전체에 같은 포트 번호를 사용할 필요가 없습니다.  

- HTTP 포트가 80이면 HTTPS 포트는 443이어야 합니다.  

- HTTP 포트가 80이 아니면 HTTPS 포트는 HTTP 포트보다 1 이상 커야 합니다. 예를 들어 HTTP 포트는 8530이고 HTTPS 포트는 8531일 수 있습니다.   

    > [!NOTE]  
    >  HTTPS를 사용하도록 소프트웨어 업데이트 지점을 구성할 경우 HTTP 포트도 열려 있어야 합니다. 특정 업데이트에 대한 EULA와 같은 암호화되지 않은 데이터는 HTTP 포트를 사용합니다.  

#### <a name="bkmk_note4"></a> 참고 4: TFTP(Trivial FTP) 디먼
TFTP(Trivial FTP) 디먼 시스템 서비스에는 사용자 이름 또는 암호가 필요하지 않으며, 해당 디먼 시스템 서비스는 WDS(Windows 배포 서비스)의 필수적인 부분입니다. Trivial FTP 디먼 서비스는 다음 RFC로 정의된 TFTP 프로토콜을 지원합니다.  

- RFC 1350: TFTP  

- RFC 2347: 옵션 확장  

- RFC 2348: 블록 크기 옵션  

- RFC 2349: 시간 제한 간격 및 전송 크기 옵션  

TFTP는 디스크 없이 부팅하는 환경을 지원하도록 설계됩니다. TFTP 디먼은 UDP 포트 69를 수신하지만 동적으로 할당된 높은 포트에서 응답합니다. 그러므로 이 포트를 사용하면 TFTP 서비스는 들어오는 TFTP 요청을 수신할 수 있지만 선택한 서버는 해당 요청에 응답할 수 없습니다. 포트 69에서 응답하도록 TFTP 서버를 구성하지 않으면 선택한 서버가 인바운드 TFTP 요청에 응답하도록 설정할 수 없습니다.  

PXE 지원 배포 지점 및 Windows PE의 클라이언트는 TFTP 전송에 대해 동적으로 할당된 높은 포트를 선택합니다. 이러한 포트는 Microsoft에 의해 49152 및 65535 사이에서 정의됩니다. 자세한 내용은 [Windows의 서비스 개요 및 네트워크 포트 요구 사항](https://support.microsoft.com/help/832017/service-overview-and-network-port-requirements-for-windows)을 참조하세요.

그러나 실제로 PXE를 부팅하는 동안 디바이스의 네트워크 카드는 TFTP를 전송하는 동안 사용하는 동적으로 할당된 높은 포트를 선택합니다. 디바이스의 네트워크 카드는 Microsoft에서 정의된 동적으로 할당된 높은 포트에 바인딩되지 않습니다. RFC 1350에서 정의된 포트로만 바인딩됩니다. 이 포트는 0 및 65535 사이의 하나일 수 있습니다. 네트워크 카드가 사용하는 동적으로 할당된 높은 포트에 대한 자세한 내용은 디바이스 하드웨어 제조업체에 문의하세요.


#### <a name="bkmk_note5"></a> 참고 5: 사이트 서버 및 사이트 시스템 간 통신
기본적으로 사이트 서버 및 사이트 시스템 간 통신은 양방향 통신입니다. 사이트 서버는 통신을 시작하여 사이트 시스템을 구성합니다. 그런 다음 대부분의 사이트 시스템은 사이트 서버로 다시 연결하여 상태 정보를 보냅니다. 보고 서비스 지점 및 배포 지점은 상태 정보를 보내지 않습니다. 사이트 시스템을 설치한 후 사이트 시스템 속성에 대해 **이 사이트 시스템의 연결을 시작하려면 사이트 서버 필요**를 선택하면 사이트 시스템이 사이트 서버와의 통신을 시작하지 않습니다. 대신, 사이트 서버는 통신을 시작하고 사이트 시스템 서버에 대한 인증에 사이트 시스템 설치 계정을 사용합니다.  

#### <a name="bkmk_note6"></a> 참고 6: 동적 포트
동적 포트는 OS 버전에서 정의된 포트 번호 범위를 사용합니다. 이러한 포트는 삭제 포트라고도 합니다. 기본 포트 범위에 대한 자세한 내용은 [Windows 서버 시스템의 서비스 개요 및 네트워크 포트 요구 사항](https://support.microsoft.com/help/832017/service-overview-and-network-port-requirements-for-windows)을 참조하세요.  



##  <a name="BKMK_AdditionalPorts"></a> 추가 포트 목록  

 다음 섹션에서는 Configuration Manager에 사용되는 포트에 대해 추가 정보를 제공합니다.  

###  <a name="BKMK_ClientShares"></a> 클라이언트-서버 공유  

 클라이언트는 UNC 공유에 연결할 때마다 SMB(Server Message Block)를 사용합니다. 예:  

- CCMSetup.exe **/source:** 명령줄 속성을 지정하는 수동 클라이언트 설치  

- UNC 경로에서 정의 파일을 다운로드하는 Endpoint Protection 클라이언트

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|SMB(서버 메시지 블록)|--|445|  


###  <a name="BKMK_SQLPorts"></a> Microsoft SQL Server에 연결  

 SQL Server 데이터베이스 엔진에 대한 통신 및 사이트 간 복제의 경우 기본 SQL Server 포트를 사용하거나 다음과 같이 사용자 지정 포트를 지정할 수 있습니다.  

- 사이트 간 통신에서는 다음을 사용합니다.  

  - 포트 TCP 4022를 기본값으로 사용하는 SQL Server Service Broker  

  - 포트 TCP 1433을 기본값으로 사용하는 SQL Server 서비스  

- SQL Server 데이터베이스 엔진 및 다양한 Configuration Manager 사이트 시스템 역할 사이에서 사이트 간 통신은 포트 TCP 1433을 기본값으로 사용합니다.  

- Configuration Manager는 사이트 데이터베이스를 호스트하는 각 SQL 가용성 그룹 복제본과 통신할 때 각 복제본이 독립 실행형 SQL Server 인스턴스인 것처럼 동일한 포트와 프로토콜을 사용합니다.

Azure를 사용하고 사이트 데이터베이스가 내부 또는 외부 부하 분산 장치 뒤에 있는 경우 다음 구성 요소를 구성합니다.
- 각 복제본의 방화벽 예외
- 부하 분산 규칙 

다음 포트를 구성합니다.
- SQL over TCP: TCP 1433
- SQL Server Service Broker: TCP 4022
- SMB(서버 메시지 블록): TCP 445
- RPC 엔드포인트 매퍼: TCP 135

> [!WARNING]  
> Configuration Manager는 동적 포트를 지원하지 않습니다. 기본적으로 SQL Server로 명명된 인스턴스는 데이터베이스 엔진에 연결하는 데 동적 포트를 사용합니다. 명명된 인스턴스를 사용하는 경우 사이트 간 통신을 위해 정적 포트를 수동으로 구성합니다.  

다음 사이트 시스템 역할은 SQL Server 데이터베이스와 직접 통신합니다.  

- 애플리케이션 카탈로그 웹 서비스 지점  

- 인증서 등록 지점 역할  

- 등록 지점 역할  

- 관리 지점  

- 사이트 서버  

- 보고 서비스 지점  

- 사이트 데이터베이스  

- SQL Server-- > SQL Server  

SQL Server가 하나를 초과하는 사이트에서 데이터베이스를 호스팅하는 경우 각 데이터베이스는 별도의 SQL Server 인스턴스를 사용해야 합니다. 고유한 포트 집합을 사용하여 각 인스턴스를 구성합니다.  

SQL Server에서 호스트 기반 방화벽을 사용하도록 설정하는 경우 올바른 포트를 허용하도록 해당 방화벽을 구성합니다. 또한 SQL Server와 통신하는 컴퓨터 간의 네트워크 방화벽도 구성합니다.  

특정 포트를 사용하도록 SQL Server를 구성하는 방법에 대한 예는 [특정 TCP 포트로 수신하도록 서버 구성](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port)을 참조하세요.  


### <a name="bkmk_discovery"> </a> 검색 및 게시

Configuration Manager는 사이트 정보의 검색 및 게시에 다음 포트를 사용합니다.
- LDAP(Lightweight Directory Access Protocol): 389
- 글로벌 카탈로그 LDAP: 3268
- RPC 엔드포인트 매퍼: 135
- RPC: 동적으로 할당된 높은 TCP 포트
- TCP: 1024: 5000
- TCP:  49152: 65535


###  <a name="BKMK_External"></a> Configuration Manager에서 수행하는 외부 연결  

온-프레미스 Configuration Manager 클라이언트 또는 사이트 시스템은 다음과 같은 외부 연결을 설정할 수 있습니다.  

- [Asset Intelligence 동기화 지점 -- &gt; Microsoft](#BKMK_PortsAI)  

- [Endpoint Protection 지점 -- &gt; 인터넷](#BKMK_PortsEndpointProtection_Internet)  

- [클라이언트 -- &gt; 글로벌 카탈로그 도메인 컨트롤러](#BKMK_PortsClient-GCDC)  

- [Configuration Manager 콘솔 -- &gt; 인터넷](#BKMK_PortsConsole-Internet)  

- [관리 지점 -- &gt; 도메인 컨트롤러](#BKMK_PortsMP-DC)  

- [사이트 서버 -- &gt; 도메인 컨트롤러](#BKMK_PortsSite-DC)  

- [사이트 서버 &lt; -- &gt; 발급 CA(인증 기관)](#BKMK_PortsIssuingCA_SiteServer)  

- [소프트웨어 업데이트 지점 -- &gt; 인터넷](#BKMK_PortsSUP-Internet)  

- [소프트웨어 업데이트 지점 -- &gt; 업스트림 WSUS 서버](#BKMK_PortsSUP-WSUS)  

- [서비스 연결 지점 -- &gt; Microsoft Intune](#BKMK_PortsIntuneConnector-WindowsIntune)  

- [서비스 연결 지점 -- > Azure(CMG)](#bkmk_scp-cmg)  

- [CMG 연결 지점 --> CMG 클라우드 서비스](#bkmk_cmgcp-cmg)  


###  <a name="BKMK_IBCMports"></a> 인터넷 기반 클라이언트를 지원하는 사이트 시스템의 설치 요구 사항  

> [!Note]  
> 이 섹션은 IBCM(인터넷 기반 클라이언트 관리)에만 적용되고 클라우드 관리 게이트웨이에는 적용되지 않습니다. 자세한 내용은 [인터넷에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients-internet)를 참조하세요.  

인터넷 기반 클라이언트를 지원하는 인터넷 기반 관리 지점 및 배포 지점, 소프트웨어 업데이트 지점 및 대체 상태 지점은 설치 및 복구에 다음 포트를 사용합니다.  

- 사이트 서버 --> 사이트 시스템: UDP 및 TCP 포트 135를 사용하는 RPC 엔드포인트 매퍼입니다.  

- 사이트 서버 --> 사이트 시스템: RPC 동적 TCP 포트입니다.  

- 사이트 서버 &lt; --> 사이트 시스템: TCP 포트 445를 사용하는 SMB(Server Message Block)

배포 지점에 애플리케이션 및 패키지를 설치하려면 다음 RPC 포트가 필요합니다.  

- 사이트 서버 --> 배포 지점: UDP 및 TCP 포트 135를 사용하는 RPC 엔드포인트 매퍼

- 사이트 서버 --> 배포 지점: RPC 동적 TCP 포트입니다.  

IPsec을 사용하여 사이트 서버 및 사이트 시스템 간 트래픽을 보호할 수 있습니다. RPC에 사용된 동적 포트를 제한해야 하는 경우 Microsoft RPC 구성 도구(rpccfg.exe)를 사용하여 이러한 RPC 패킷에 제한된 포트 범위를 구성할 수 있습니다. RPC 구성 도구에 대한 자세한 내용은 [RPC에서 특정 포트를 사용하도록 구성하는 방법과 IPsec을 사용하여 이러한 포트를 보호하는 방법](https://support.microsoft.com/help/908472/how-to-configure-rpc-to-use-certain-ports-and-how-to-help-secure-those)을 참조하세요.  

> [!IMPORTANT]  
>  이러한 사이트 시스템을 설치하기 전에 원격 레지스트리 서비스를 사이트 시스템 서버에서 실행해야 하며 트러스트 관계가 없는 다른 Active Directory 포리스트에 사이트 시스템이 있는 경우 사이트 시스템 설치 계정을 지정했어야 합니다.  


###  <a name="BKMK_PortsClientInstall"></a> Configuration Manager 클라이언트 설치에 사용되는 포트  

클라이언트 설치 중에 Configuration Manager가 사용하는 포트는 배포 방법에 따라 달라집니다. 

- 각 클라이언트 배포 방식별 포트 목록에 대한 자세한 내용은 [Configuration Manager 클라이언트 배포 시 사용되는 포트](/sccm/core/clients/deploy/windows-firewall-and-port-settings-for-clients#ports-used-during-configuration-manager-client-deployment)를 참조  

- 클라이언트 설치 및 설치 후 통신에 대해 클라이언트에서 Windows 방화벽을 구성하는 방법은 [클라이언트에 대한 Windows 방화벽 및 포트 설정](/sccm/core/clients/deploy/windows-firewall-and-port-settings-for-clients)을 참조  


###  <a name="BKMK_MigrationPorts"></a> 마이그레이션에서 사용되는 포트  

마이그레이션을 실행하는 사이트 서버는 여러 포트를 사용하여 원본 계층에 적용 가능한 사이트에 연결합니다. 자세한 내용은 [마이그레이션을 위한 필수 구성](/sccm/core/migration/prerequisites-for-migration#BKMK_Required_Configurations)을 참조하세요.  


###  <a name="BKMK_ServerPorts"></a> Windows Server에 사용되는 포트  

다음 표에는 Windows Server에서 사용하는 일부 핵심 포트가 나열됩니다. 

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|DNS|53|53|  
|DHCP|67 및 68|--|  
|NetBIOS 이름 확인|137|--|  
|NetBIOS 데이터그램 서비스|138|--|  
|NetBIOS 세션 서비스|--|139|  
|Kerberos 인증|--|88|

자세한 내용은 다음 아티클을 참조하세요.
- [Windows Server 시스템에 대한 서비스 개요 및 네트워크 포트 요구 사항](https://support.microsoft.com/help/832017/service-overview-and-network-port-requirements-for-windows).  

- [도메인 및 트러스트에 대한 방화벽을 구성하는 방법](https://support.microsoft.com/help/179442/how-to-configure-a-firewall-for-domains-and-trusts)
