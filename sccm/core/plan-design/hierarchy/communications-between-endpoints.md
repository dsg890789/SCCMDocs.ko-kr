---
title: 엔드포인트 간의 통신
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 시스템 및 구성 요소가 네트워크를 통해 통신하는 방법을 알아봅니다.
ms.date: 10/25/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 68fe0e7e-351e-4222-853a-877475adb589
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ebe37bb97c4a1e231bfaf94f420f7f0471f30f6
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56141962"
---
# <a name="communications-between-endpoints-in-configuration-manager"></a>Configuration Manager의 엔드포인트 간 통신

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager 사이트 시스템과 클라이언트가 네트워크를 통해 통신하는 방법을 설명합니다. 여기에는 다음과 같은 섹션이 포함됩니다.  

- [사이트의 사이트 시스템 간 통신](#Planning_Intra-site_Com)  
    - [사이트 서버에서 배포 지점으로의 통신](#bkmk_site2dp)  

- [클라이언트와 사이트 시스템 및 서비스 간의 통신](#Planning_Client_to_Site_System)  
    - [클라이언트에서 관리 지점으로의 통신](#bkmk_client2mp)  
    - [클라이언트에서 배포 지점으로의 통신](#bkmk_client2dp)  
    - [인터넷 또는 신뢰할 수 없는 포리스트에서 들어오는 클라이언트 통신에 대한 고려 사항](#BKMK_clientspan)  
    - [인터넷 연결 사이트 시스템 정보](#bkmk_internetfacing)  

- [Active Directory 포리스트 간 통신](#Plan_Com_X-Forest)  
    - [사이트 서버의 포리스트에서 신뢰하지 않는 포리스트의 도메인 컴퓨터 지원](#bkmk_noforesttrust)  
    - [작업 그룹의 컴퓨터 지원](#bkmk_workgroup)  
    - [여러 도메인과 포리스트에 걸쳐 있는 사이트 또는 계층을 지원하는 시나리오](#bkmk_span)  



##  <a name="Planning_Intra-site_Com"></a> 사이트의 사이트 시스템 간 통신  

 Configuration Manager 사이트 시스템 또는 구성 요소는 네트워크를 통해 다른 사이트 시스템이나 사이트 내 구성 요소와 통신할 때 사이트를 구성하는 방법에 따라 다음 프로토콜 중 하나를 사용합니다.  

-   SMB(서버 메시지 블록)  

-   HTTP  

-   HTTPS  

사이트 서버에서 배포 지점으로 향하는 통신을 제외하고, 사이트 내 서버 간 통신은 언제든지 발생할 수 있습니다. 이러한 통신은 네트워크 대역폭을 제어하는 메커니즘을 사용하지 않습니다. 사이트 시스템 간 통신은 제어할 수 없으므로 빠르고 잘 연결된 네트워크가 있는 위치에 사이트 시스템 서버를 설치해야 합니다.  


### <a name="bkmk_site2dp"></a> 사이트 서버에서 배포 지점으로의 통신 

사이트 서버에서 배포 지점으로의 콘텐츠 전송을 관리하는 데 도움이 되도록 다음 전략을 사용하세요.  

-   배포 지점을 네트워크 대역폭 제어 및 일정에 대해 구성합니다. 이러한 컨트롤은 사이트 간 주소에서 사용되는 구성과 유사합니다. 대역폭을 고려할 때 원격 네트워크 위치로 콘텐츠를 전송하는 것을 중요하게 생각한다면 다른 Configuration Manager 사이트를 설치하는 대신 이 구성을 사용하세요.  

-   배포 지점을 미리 준비된 배포 지점으로 설치할 수 있습니다. 미리 준비된 배포 지점을 활용하면 배포 지점 서버에 수동으로 전송된 콘텐츠를 사용할 수 있고 네트워크를 통해 콘텐츠 파일을 전송할 필요가 없습니다.  

자세한 내용은 [콘텐츠 관리를 위한 네트워크 대역폭 관리](manage-network-bandwidth.md)를 참조하세요.



##  <a name="Planning_Client_to_Site_System"></a> 클라이언트와 사이트 시스템 및 서비스 간의 통신  

클라이언트는 사이트 시스템 역할, Active Directory Domain Services 및 온라인 서비스에 대한 통신을 시작합니다. 이러한 통신을 설정하려면 방화벽에서 클라이언트와 통신 엔드포인트 간의 네트워크 트래픽을 허용해야 합니다. 이러한 엔드포인트와 통신할 때 클라이언트에서 사용하는 포트 및 프로토콜에 대한 자세한 내용은 [Configuration Manager에서 사용되는 포트](/sccm/core/plan-design/hierarchy/ports)를 참조하세요.  

클라이언트가 사이트 시스템 역할과 통신하기 전에 클라이언트는 서비스 위치를 사용하여 클라이언트의 프로토콜(HTTP 또는 HTTPS)을 지원하는 역할을 찾습니다. 기본적으로 클라이언트는 제공되는 방법 중 가장 안전한 방법을 사용합니다. 자세한 내용은 [클라이언트가 사이트 리소스 및 서비스를 찾는 방법 이해](/sccm/core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services)를 참조하세요.  

HTTPS를 사용하려면 다음 옵션 중 하나를 구성합니다.  

- PKI(공개 키 인프라)를 사용하여 클라이언트 및 서버에 PKI 인증서를 설치합니다. 인증서를 사용하는 방법에 대한 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

- 버전 1806부터 사이트를 **HTTP 사이트 시스템용 Configuration Manager 생성 인증서 사용**으로 구성합니다. 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.  

IIS(인터넷 정보 서비스)를 사용하고 클라이언트의 통신을 지원하는 사이트 시스템 역할을 배포할 때 클라이언트가 HTTP를 사용하여 사이트 시스템에 연결하는지 또는 HTTPS를 사용하여 사이트 시스템에 연결하는지 지정해야 합니다. HTTP를 사용하는 경우 서명 및 암호화 선택도 고려해야 합니다. 자세한 내용은 [서명 및 암호화 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForSigningEncryption)을 참조하세요.  


### <a name="bkmk_client2mp"></a> 클라이언트에서 관리 지점으로의 통신

클라이언트가 관리 지점과 통신할 때는 인증(전송)과 권한 부여(메시지)라는 두 단계를 거칩니다. 이 프로세스는 다음 요인에 따라 달라집니다. 
- 사이트 구성: HTTP, HTTPS 또는 향상된 HTTP
- 관리 지점 구성: HTTPS만 또는 HTTP 또는 HTTPS 허용
- 디바이스 중심 시나리오의 디바이스 ID
- 사용자 중심 시나리오의 사용자 ID

다음 표를 사용하여 이 프로세스의 작동 방식을 이해합니다.  

| MP 유형  | 클라이언트 인증  | 클라이언트 권한 부여<br>디바이스 ID  | 클라이언트 권한 부여<br>사용자 ID  |
|----------|---------|---------|---------|
| HTTP     | 익명<br>고급 HTTP를 사용하면 사이트에서 Azure AD *사용자* 또는 *디바이스* 토큰을 확인합니다. | 위치 요청: 익명<br>클라이언트 패키지: 익명<br>디바이스 ID를 증명하기 위해 다음 방법 중 하나를 사용하여 등록:<br> - 익명(수동 승인)<br> - Windows 통합 인증<br> - Azure AD *디바이스* 토큰(고급 HTTP)<br>등록 후 클라이언트는 메시지 서명을 사용하여 디바이스 ID를 증명합니다. | 사용자 중심 시나리오의 경우 다음 방법 중 하나를 사용하여 사용자 ID를 증명합니다.<br> - Windows 통합 인증<br> - Azure AD *사용자* 토큰(고급 HTTP) |
| HTTPS    | 다음 방법 중 하나를 사용합니다.<br> - PKI 인증서<br> - Windows 통합 인증<br> - Azure AD *사용자* 또는 *디바이스* 토큰 | 위치 요청: 익명<br>클라이언트 패키지: 익명<br>디바이스 ID를 증명하기 위해 다음 방법 중 하나를 사용하여 등록:<br> - 익명(수동 승인)<br> - Windows 통합 인증<br> - PKI 인증서<br> - Azure AD *사용자* 또는 *디바이스* 토큰<br>등록 후 클라이언트는 메시지 서명을 사용하여 디바이스 ID를 증명합니다. | 사용자 중심 시나리오의 경우 다음 방법 중 하나를 사용하여 사용자 ID를 증명합니다.<br> - Windows 통합 인증<br> - Azure AD *사용자* 토큰 |

> [!Tip]  
> 다른 디바이스 ID 유형과 클라우드 관리 게이트웨이에 대한 관리 지점 구성에 대한 자세한 내용은 [HTTPS에 대한 관리 지점 사용](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_mphttps)을 참조하세요.  


### <a name="bkmk_client2dp"></a> 클라이언트에서 배포 지점으로의 통신

클라이언트가 배포 지점과 통신할 때는 콘텐츠를 다운로드하기 전에 인증하기만 하면 됩니다. 다음 표를 사용하여 이 프로세스의 작동 방식을 이해합니다.


| DP 유형  | 클라이언트 인증  |
|----------|---------|
| HTTP     | - 익명(허용하는 경우)<br>- 컴퓨터 계정 또는 네트워크 액세스 계정으로 Windows 통합 인증<br> - 콘텐츠 액세스 토큰(고급 HTTP) |
| HTTPS    | - PKI 인증서<br> - 컴퓨터 계정 또는 네트워크 액세스 계정으로 Windows 통합 인증<br> - 콘텐츠 액세스 토큰 |


###  <a name="BKMK_clientspan"></a> 인터넷 또는 신뢰할 수 없는 포리스트에서 들어오는 클라이언트 통신에 대한 고려 사항  

기본 사이트에 설치된 다음 사이트 시스템 역할은 인터넷 또는 신뢰할 수 없는 포리스트와 같이 신뢰할 수 없는 위치에 있는 클라이언트에서 들어오는 연결을 지원합니다. (보조 사이트는 신뢰할 수 없는 위치에서 들어오는 클라이언트 연결을 지원하지 않습니다.) 

-   애플리케이션 카탈로그 웹 사이트 지점  

-   Configuration Manager 정책 모듈(NDES) 

-   배포 지점   

-   클라우드 기반 배포 지점(HTTPS 필요)

-   등록 프록시 지점  

-   대체 상태 지점  

-   관리 지점  

-   소프트웨어 업데이트 지점  

-   클라우드 관리 게이트웨이(HTTPS 필요)


### <a name="bkmk_internetfacing"></a> 인터넷 연결 사이트 시스템 정보

> [!Note]  
> 다음 섹션에서는 인터넷 기반 클라이언트 관리 시나리오에 대해 설명합니다. 클라우드 관리 게이트웨이 시나리오에는 적용되지 않습니다. 자세한 내용은 [인터넷에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients-internet)를 참조하세요.  

클라이언트 포리스트와 사이트 시스템 서버 포리스트 간의 신뢰 관계에 대한 요구 사항은 없습니다. 하지만 인터넷 연결 사이트 시스템을 포함하는 포리스트가 사용자 계정을 포함하는 포리스트를 신뢰하는 경우, 이 구성은 **클라이언트 정책** 클라이언트 설정 **인터넷 클라이언트의 사용자 정책 요청 사용**을 사용하도록 설정할 때 인터넷상의 디바이스에 사용자 기반 정책을 지원합니다.  

예를 들어 다음 구성은 인터넷 기반 클라이언트 관리에서 인터넷의 디바이스에 사용자 정책을 지원하는 경우를 보여줍니다.  

-   인터넷 기반 관리 지점은 읽기 전용 도메인 컨트롤러가 사용자 인증을 위해 상주하는 경계 네트워크에 있으며 중간 방화벽은 Active Directory 패킷을 허용합니다.  

-   사용자 계정은 포리스트 A(인트라넷)에 있고 인터넷 기반 관리 지점은 포리스트 B(경계 네트워크)에 있습니다. 포리스트 B는 포리스트 A를 트러스트하고 중간 방화벽은 인증 패킷을 허용합니다.  

-   사용자 계정 및 인터넷 기반 관리 지점은 포리스트 A(인트라넷)에 있습니다. 관리 지점은 웹 프록시 서버(예: Forefront Threat Management Gateway)를 통해 인터넷에 게시됩니다.  

> [!NOTE]  
>  Kerberos 인증이 실패하면 자동으로 NTLM 인증이 시도됩니다.  

이전 예제에서 볼 수 있듯이 인터넷 기반 사이트 시스템을 웹 프록시 서버를 통해 인터넷에 게시하면 인트라넷에 배치할 수 있습니다. 이러한 사이트 시스템은 인터넷의 클라이언트 연결에만 구성하거나 인터넷 및 인트라넷의 클라이언트 연결에 구성할 수 있습니다. 웹 프록시 서버를 사용할 경우 해당 웹 프록시 서버에서 보안 수준이 더 높은 SSL(Secure Sockets Layer) 또는 SSL 터널링에 대한 SSL 브리징을 다음과 같이 구성할 수 있습니다.  

-   **SSL에 대한 SSL 브리징:**   
    인터넷 기반 클라이언트 관리에 프록시 웹 서버를 사용할 경우 권장되는 구성은 SSL에 대한 SSL 브리징입니다. 이 구성에서는 인증과 함께 SSL 종료를 사용합니다. 클라이언트 컴퓨터는 컴퓨터 인증으로 인증되어야 하며 모바일 디바이스 기존 클라이언트는 사용자 인증으로 인증됩니다. Configuration Manager에서 등록한 모바일 디바이스는 SSL 브리징을 지원하지 않습니다.  

     프록시 웹 서버에서 SSL 종료의 이점은 인터넷의 패킷이 내부 네트워크에 전달되기 전에 검사를 받아야 한다는 것입니다. 프록시 웹 서버는 클라이언트에서의 연결을 인증하고 종료한 다음, 인터넷 기반 사이트 시스템에 대한 새로운 인증 연결을 엽니다. Configuration Manager 클라이언트에서 프록시 웹 서버를 사용하면 클라이언트 ID(클라이언트 GUID)가 패킷 페이로드에 안전하게 보관되므로 관리 지점은 프록시 웹 서버를 클라이언트로 간주하지 않습니다. Configuration Manager에서는(HTTP에서 HTTPS로 또는 HTTPS에서 HTTP로) 브리징이 지원되지 않습니다.  

-   **터널링:**:   
    프록시 웹 서버가 SSL 브리징에 대한 요구 사항을 지원할 수 없는 경우 또는 Configuration Manager에서 등록된 모바일 디바이스에 대해 인터넷 지원을 구성하려는 경우를 위해 SSL 터널링도 지원됩니다. 인터넷의 SSL 패킷이 SSL 종료 없이 사이트 시스템으로 전달되어 악성 콘텐츠를 검사할 수 없기 때문에 보안 수준이 낮은 옵션입니다. SSL 터널링을 사용할 경우 프록시 웹 서버에 대한 인증서 요구 사항은 없습니다.  



##  <a name="Plan_Com_X-Forest"></a> Active Directory 포리스트 간 통신  

Configuration Manager는 여러 Active Directory 포리스트에 걸쳐 있는 사이트 및 계층을 지원합니다. 또한 사이트 서버와 동일한 Active Directory 포리스트에 있지 않은 도메인 컴퓨터 및 작업 그룹에 있는 컴퓨터를 지원합니다.  


### <a name="bkmk_noforesttrust"></a> 사이트 서버의 포리스트에서 신뢰하지 않는 포리스트의 도메인 컴퓨터 지원 

-   사이트 정보를 Active Directory 포리스트에 게시하는 옵션을 포함해 트러스트되지 않은 해당 포리스트에 사이트 시스템 역할을 설치합니다.  

-   이러한 컴퓨터는 작업 그룹 컴퓨터처럼 관리합니다.  

트러스트되지 않은 Active Directory 포리스트에 사이트 시스템 서버를 설치하면 포리스트의 클라이언트와 서버 간의 통신은 해당 포리스트 내에 유지되고 Configuration Manager에서 Kerberos를 사용하여 컴퓨터를 인증할 수 있습니다. 사이트 정보를 클라이언트의 포리스트에 게시하면 클라이언트는 사용할 수 있는 관리 지점의 목록과 같은 사이트 정보를 할당된 관리 지점에서 다운로드하는 대신 Active Directory 포리스트에서 검색할 수 있는 이점을 얻을 수 있습니다.  

> [!NOTE]  
>  인터넷에 있는 디바이스를 관리하기 위해 Active Directory 포리스트에 사이트 시스템 서버가 있는 경우 경계 네트워크에 인터넷 기반 사이트 시스템 역할을 설치할 수 있습니다. 이 시나리오에서는 경계 네트워크 및 사이트 서버의 포리스트 간에 양방향 트러스트가 필요하지 않습니다.  


### <a name="bkmk_workgroup"></a> 작업 그룹의 컴퓨터 지원  

-   사이트 시스템 역할에 대해 HTTP 클라이언트 연결을 사용할 때 작업 그룹 컴퓨터를 수동으로 승인합니다. Configuration Manager에서 Kerberos를 사용하여 해당 컴퓨터를 인증할 수 없습니다.  

-   이러한 컴퓨터가 배포 지점에서 콘텐츠를 검색할 수 있게 네트워크 액세스 계정을 사용하도록 작업 그룹 클라이언트를 구성합니다.  

-   작업 그룹 클라이언트가 관리 지점을 검색하는 대체 메커니즘을 제공합니다. DNS 게시, WINS를 사용하거나 관리 지점을 직접 할당합니다. 이러한 클라이언트는 Active Directory Domain Services에서 사이트 정보를 검색할 수 없습니다.  

자세한 내용은 다음 아티클을 참조하세요.  

-   [충돌 레코드 관리](/sccm/core/clients/manage/manage-clients#BKMK_ConflictingRecords)  

-   [네트워크 액세스 계정](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#accounts-used-for-content-management)  

-   [작업 그룹 컴퓨터에 Configuration Manager 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientWorkgroup)  


###  <a name="bkmk_span"></a> 여러 도메인과 포리스트에 걸쳐 있는 사이트 또는 계층을 지원하는 시나리오  

#### <a name="scenario-1-communication-between-sites-in-a-hierarchy-that-spans-forests"></a>시나리오 1: 여러 포리스트에 걸쳐 있는 계층 내 사이트 간 통신  
이 시나리오에서는 Kerberos 인증을 지원하는 양방향 포리스트 트러스트가 필요합니다.  Kerberos 인증을 지원하는 양방향 포리스트 트러스트가 없는 경우 Configuration Manager는 원격 포리스트의 자식 사이트를 지원하지 않습니다.  

Configuration Manager는 부모 사이트의 포리스트와 필수 양방향 트러스트가 설정된 원격 포리스트에 자식 사이트를 설치하도록 지원합니다. 예를 들어 필수 트러스트가 있으면 기본 부모 사이트의 포리스트와 다른 포리스트에 보조 사이트를 배치할 수 있습니다.  

> [!NOTE]  
>  자식 사이트는 기본 사이트(중앙 관리 사이트가 부모 사이트임) 또는 보조 사이트가 될 수 있습니다.  

Configuration Manager의 사이트 간 통신에서는 데이터베이스 복제 및 파일 기반 전송을 사용합니다. 사이트를 설치할 때 지정된 서버에 사이트를 설치할 계정을 지정해야 합니다. 또한 이 계정은 사이트 간 통신도 설정 및 유지 관리합니다. 사이트가 성공적으로 설치되고 파일 기반 전송 및 데이터베이스 복제를 시작하면 사이트 통신에 대해 더 이상 구성할 내용은 없습니다.  

양방향 포리스트 트러스트가 설정된 경우 Configuration Manager에서 추가 구성 단계를 수행할 필요가 없습니다.  

기본적으로 새 자식 사이트를 설치하면 Configuration Manager에서 다음 구성 요소를 구성합니다.  

-   사이트 서버 컴퓨터 계정을 사용하는 각 사이트의 사이트 간 파일 기반 복제 경로. Configuration Manager는 대상 컴퓨터의 **SMS_SiteToSiteConnection_&lt;sitecode\>** 그룹에 각 컴퓨터의 컴퓨터 계정을 추가합니다.  

-   각 사이트의 SQL Server 간 데이터베이스 복제.  

다음 구성도 설정합니다.  

-   중간 방화벽 및 네트워크 디바이스에서 Configuration Manager에 필요한 네트워크 패킷을 허용해야 합니다.  

-   포리스트 간에 이름 확인이 작동해야 합니다.  

-   사이트 또는 사이트 시스템 역할을 설치하려면 지정된 컴퓨터에 대한 로컬 관리자 권한이 있는 계정을 지정해야 합니다.  

#### <a name="scenario-2-communication-in-a-site-that-spans-forests"></a>시나리오 2: 여러 포리스트에 걸쳐 있는 사이트 내 통신:  
이 시나리오에서는 양방향 포리스트 트러스트가 필요하지 않습니다.  

기본 사이트는 원격 포리스트의 컴퓨터에 사이트 시스템 역할을 설치할 수 있도록 지원합니다.  

-   단, 애플리케이션 카탈로그 웹 서비스 지점은 예외입니다.  사이트 서버와 동일한 포리스트에서만 지원됩니다.  

-   사이트 시스템 역할이 인터넷의 연결을 허용하는 경우 포리스트 경계에서 사이트 서버를 보호할 수 있도록 위치(예: 경계 네트워크)에 사이트 시스템 역할을 설치하는 것이 보안을 위해 가장 좋습니다.  

신뢰할 수 없는 포리스트의 컴퓨터에 사이트 시스템 역할을 설치하려면  

- 사이트에서 사이트 시스템 역할을 설치하는 데 사용되는 **사이트 시스템 설치 계정**을 지정합니다. 이 계정에는 연결할 로컬 관리자 자격 증명이 있어야 합니다. 그런 다음 지정된 컴퓨터에 사이트 시스템 역할을 설치합니다.  

- 사이트 시스템 옵션 **이 사이트 시스템의 연결을 시작하려면 사이트 서버 필요**를 선택합니다. 이 설정을 사용하려면 사이트 서버에서 데이터 전송을 위해 사이트 시스템 서버에 대한 연결을 설정해야 합니다. 이렇게 구성하면 신뢰할 수 없는 위치의 컴퓨터가 신뢰할 수 있는 네트워크 내에 있는 사이트 서버와의 연결을 시작할 수 없습니다. 이러한 연결에서는 **사이트 시스템 설치 계정**을 사용합니다.  

신뢰할 수 없는 포리스트에 설치된 사이트 시스템 역할을 사용하려면 사이트 서버에서 데이터 전송을 시작하는 경우에도 방화벽에서 네트워크 트래픽을 허용해야 합니다.  

또한 다음 사이트 시스템 역할이 사이트 데이터베이스에 직접 액세스할 수 있어야 합니다. 따라서 방화벽이 트러스트되지 않은 포리스트에서 SQL Server 사이트로의 해당 트래픽을 허용해야 합니다.  

-   Asset Intelligence 동기화 지점  

-   Endpoint Protection 지점  

-   등록 지점  

-   관리 지점  

-   보고 서비스 지점  

-   상태 마이그레이션 지점  

자세한 내용은 [Configuration Manager에 사용되는 포트](/sccm/core/plan-design/hierarchy/ports)를 참조하세요.  

사이트 데이터베이스에 대한 관리 지점 및 등록 지점 액세스를 구성해야 할 수 있습니다.

-   기본적으로 이러한 역할을 설치할 때 Configuration Manager에서는 새 사이트 시스템 서버의 컴퓨터 계정을 사이트 시스템 역할의 연결 계정으로 구성합니다. 그런 다음, 적절한 SQL Server 데이터베이스 역할에 계정을 추가합니다.  

-   이 사이트 시스템 역할을 신뢰할 수 없는 도메인에 설치할 경우 사이트 시스템 역할이 데이터베이스에서 정보를 가져올 수 있도록 사이트 시스템 역할 연결 계정을 구성합니다.  

도메인 사용자 계정을 이러한 사이트 시스템 역할의 연결 계정으로 구성하는 경우 도메인 사용자 계정에 해당 사이트의 SQL Server 데이터베이스에 대한 적절한 액세스 권한이 있는지 확인합니다.  

-   관리 지점: **관리 지점 데이터베이스 연결 계정**  

-   등록 지점: **등록 지점 연결 계정**  

다른 포리스트의 사이트 시스템 역할을 계획할 때 다음 추가 정보를 고려하세요.  

-   Windows 방화벽을 실행하는 경우 사이트 데이터베이스 서버 및 원격 사이트 시스템 역할과 함께 설치된 컴퓨터 간에 통신을 전달하기 위해 해당되는 방화벽 프로필을 구성합니다.   

-   인터넷 기반 관리 지점에서 사용자 계정이 포함된 포리스트를 트러스트하면 사용자 정책이 지원됩니다. 트러스트가 없으면 컴퓨터 정책만 지원됩니다.  

#### <a name="scenario-3-communication-between-clients-and-site-system-roles-when-the-clients-arent-in-the-same-active-directory-forest-as-their-site-server"></a>시나리오 3: 클라이언트가 사이트 서버와 동일한 Active Directory 포리스트에 없는 경우 클라이언트 및 사이트 시스템 역할 간 통신  
Configuration Manager에서는 해당 사이트의 사이트 서버와 동일한 포리스트에 있지 않은 클라이언트에 다음 시나리오를 지원합니다.  

-   클라이언트의 포리스트와 사이트 서버의 포리스트 간에 양방향 포리스트 트러스트가 존재합니다.  

-   사이트 시스템 역할 서버가 클라이언트와 동일한 포리스트에 있습니다.  

-   사이트 서버와 양방향 포리스트 트러스트가 없는 도메인 컴퓨터에 클라이언트가 있고, 클라이언트의 포리스트에 사이트 시스템 역할이 설치되어 있지 않습니다.  

-   클라이언트가 작업 그룹 컴퓨터에 있습니다.  

도메인에 가입된 컴퓨터의 클라이언트에서 자체 사이트가 자체 Active Directory 포리스트에 게시될 때 서비스 위치에 대해 Active Directory Domain Services를 사용할 수 있습니다.  

다른 Active Directory 포리스트에 사이트 정보를 게시하려면:  

-   포리스트를 지정한 다음 **관리** 작업 영역의 **Active Directory 포리스트** 노드에서 해당 포리스트에 게시하도록 설정합니다.  

-   각 사이트에서 해당 데이터를 Active Directory Domain Services에 게시하도록 구성합니다. 이러한 구성을 통해 해당 포리스트의 클라이언트는 사이트 정보를 검색하고 관리 지점을 찾을 수 있습니다. 서비스 위치로 Active Directory Domain Service를 사용할 수 없는 클라이언트에 DNS, WINS 또는 클라이언트의 할당된 관리 지점을 사용할 수 있습니다.  


####  <a name="bkmk_xchange"></a> 시나리오 4: 원격 포리스트에 Exchange Server 커넥터 배치  

이 시나리오를 지원하려면 포리스트 간에 이름 확인이 작동하는지 확인합니다. 예를 들어, DNS 전달을 구성합니다. Exchange Server 커넥터를 구성할 때 Exchange Server의 인트라넷 FQDN을 지정합니다. 자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  



## <a name="see-also"></a>참고 항목

- [보안 계획](/sccm/core/plan-design/security/plan-for-security)  

- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  

