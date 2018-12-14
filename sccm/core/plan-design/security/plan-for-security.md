---
title: 보안 계획
titleSuffix: Configuration Manager
description: Configuration Manager의 보안에 대한 모범 사례 및 기타 정보를 확인합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2a216814-ca8c-4d2e-bcef-dc00966a3c9f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5332fa778b343a5eaae93a08db0826823fffce42
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52456382"
---
# <a name="plan-for-security-in-configuration-manager"></a>Configuration Manager의 보안 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager 구현을 통해 보안을 계획할 때 고려해야 할 개념을 설명합니다. 여기에는 다음과 같은 섹션이 포함됩니다.  

- [인증서(자체 서명 및 PKI) 계획](#BKMK_PlanningForCertificates)  
    - [CNG(Cryptography: Next Generation) 인증서](#bkmk_plan-cng)  
    - [고급 HTTP](#bkmk_plan-ehttp)  
    - [CMG 및 CDP용 인증서](#bkmk_plan-cmgcdp)  
    - [사이트 서버 서명 인증서(자체 서명)](#bkmk_plansitesign)  
    - [PKI 인증서 해지](#BKMK_PlanningForCRLs)  
    - [PKI 신뢰할 수 있는 루트 인증서 및 인증서 발급자](#BKMK_PlanningForRootCAs)  
    - [PKI 클라이언트 인증서 선택](#BKMK_PlanningForClientCertificateSelection)  
    - [PKI 인증서 및 인터넷 기반 클라이언트 관리에 대한 전환 전략](#BKMK_PlanningForPKITransition)  

- [신뢰할 수 있는 루트 키 계획](#BKMK_PlanningForRTK)  

- [서명 및 암호화 계획](#BKMK_PlanningForSigningEncryption)  

- [역할 기반 관리 계획](#BKMK_PlanningForRBA)  

- [Azure Active Directory 계획](#bkmk_planazuread)  

- [SMS 공급 기업 인증 계획](#bkmk_auth)



##  <a name="BKMK_PlanningForCertificates"></a> 인증서(자체 서명 및 PKI) 계획  

 Configuration Manager에서는 자체 서명된 인증서와 PKI(공개 키 인프라) 인증서를 결합하여 사용합니다.  

 가능하면 항상 PKI 인증서를 사용합니다. 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요. 모바일 장치에 등록 중에 Configuration Manager가 PKI 인증서를 요청하는 경우 Active Directory Domain Services와 엔터프라이즈 인증 기관을 사용해야 합니다. 다른 모든 PKI 인증서의 경우 Configuration Manager와 별개로 인증서를 배포하고 관리합니다. 

 클라이언트 컴퓨터가 인터넷 기반 사이트 시스템에 연결하는 경우 PKI 인증서가 필요합니다. 클라우드 관리 게이트웨이 및 클라우드 배포 지점을 사용하는 일부 시나리오에도 PKI 인증서가 필요합니다. 자세한 내용은 [인터넷에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients-internet)를 참조하세요.

 또한 PKI를 사용하는 경우 IPsec을 사용하여 단일 사이트 내부 및 여러 사이트에 있는 사이트 시스템 간의 서버 통신을 보호하고 컴퓨터 간의 기타 데이터 전송에서 보안을 유지할 수 있습니다. IPsec 구현은 Configuration Manager와 관련이 없습니다.  

 PKI 인증서를 사용할 수 없으면 Configuration Manager는 자동으로 자체 서명 인증서를 생성합니다. Configuration Manager의 일부 인증서는 항상 자체 서명됩니다. 대부분의 경우 Configuration Manager에서는 자체 서명 인증서를 자동으로 관리하므로 추가 작업을 수행할 필요가 없습니다. 한 가지 예로 사이트 서버 서명 인증서가 있습니다. 이 인증서는 항상 자체 서명됩니다. 클라이언트가 관리 지점에서 다운로드한 정책이 사이트 서버에서 전송되어 변경되지 않았는지 확인합니다.  


### <a name="bkmk_plan-cng"></a> CNG(Cryptography: Next Generation) 인증서  

 Configuration Manager는 CNG(Cryptography: Next Generation) 인증서를 지원합니다. Configuration Manager 클라이언트는 CNG KSP(키 저장소 공급자)의 개인 키와 함께 PKI 클라이언트 인증 인증서를 사용할 수 있습니다. Configuration Manager 클라이언트는 KSP 지원을 통해 PKI 클라이언트 인증 인증서용 TPM KSP와 같은 하드웨어 기반 개인 키를 지원합니다. 자세한 내용은 [CNG 인증서 개요](/sccm/core/plan-design/network/cng-certificates-overview)를 참조하세요.


### <a name="bkmk_plan-ehttp"></a> 고급 HTTP  

 모든 Configuration Manager 통신 경로에는 HTTPS 통신을 사용하는 것이 좋지만 일부 고객의 경우 PKI 인증서 관리 부담으로 인해 어려울 수 있습니다. Azure AD(Azure Active Directory) 통합이 도입되면서 인증서 요구 사항의 일부는 줄었지만 전체가 없어지지는 않았습니다. 1806 버전부터 사이트에서 **고급 HTTP**를 사용하도록 설정할 수 있습니다. 이 구성은 자체 서명된 인증서와 Azure AD의 조합을 사용하여 사이트 시스템에서 HTTPS를 지원합니다. PKI는 필요하지 않습니다. 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.  


### <a name="bkmk_plan-cmgcdp"></a> CMG 및 CDP용 인증서

CMG(클라우드 관리 게이트웨이) 및 CDP(클라우드 배포 지점)를 통해 인터넷에서 클라이언트를 관리하려면 인증서를 사용해야 합니다. 인증서의 수와 종류는 특정 시나리오에 따라 달라집니다. 자세한 내용은 다음 아티클을 참조하세요.
- [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)  
- [클라우드 배포 지점에 대한 인증서](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_certs)  


### <a name="bkmk_plansitesign"></a> 사이트 서버 서명 인증서(자체 서명) 계획  

 Active Directory Domain Services와 클라이언트 강제 설치를 사용할 경우 클라이언트가 사이트 서버 서명 인증서의 복사본을 안전하게 가져올 수 있습니다. 클라이언트가 이러한 메커니즘 중 하나를 사용하여 이 인증서의 복사본을 가져올 수 없는 경우, 클라이언트를 설치할 때 인증서를 설치합니다. 이 프로세스는 클라이언트와 사이트의 첫 번째 통신이 인터넷 기반 관리 지점인 경우에 특히 중요합니다. 이 서버는 신뢰할 수 없는 네트워크에 연결되어 있기 때문에 공격에 더 취약합니다. 별도의 조치를 취하지 않을 경우 클라이언트는 관리 지점에서 사이트 서버 서명 인증서의 복사본을 자동으로 다운로드합니다.  

 클라이언트는 다음 시나리오에서 사이트 서버 인증서의 복사본을 안전하게 가져올 수 없습니다.  

 - 클라이언트 강제 설치를 사용하여 클라이언트를 설치하지 않으며,  

    - Configuration Manager용으로 Active Directory 스키마를 확장하지 않았습니다.  

    - 클라이언트의 사이트를 Active Directory Domain Services에 게시하지 않았습니다.  

    - 클라이언트가 신뢰할 수 없는 포리스트 또는 작업 그룹에 속해 있음  

 - 인터넷 기반 클라이언트 관리를 사용 중이고 인터넷에 있을 때 클라이언트를 설치합니다.  

#### <a name="to-install-clients-with-a-copy-of-the-site-server-signing-certificate"></a>클라이언트와 함께 사이트 서버 서명 인증서의 복사본을 설치하려면  

1.  기본 사이트 서버에서 사이트 서버 서명 인증서를 찾습니다. 인증서가 Windows의 **SMS** 인증서 저장소에 저장됩니다. 주체 이름 **사이트 서버**와 식별 이름인 **사이트 서버 서명 인증서**가 있습니다.  

2.  개인 키 없이 인증서를 내보내고, 파일을 안전하게 저장하고, 보안 채널에서만 액세스합니다.  

3.  `SMSSIGNCERT=<full path and file name>` client.msi 속성을 사용하여 클라이언트를 설치합니다.  


###  <a name="BKMK_PlanningForCRLs"></a> PKI 인증서 해지 계획  

Configuration Manager와 함께 PKI 인증서를 사용하는 경우 CRL(인증서 해지 목록) 사용 계획을 세우세요. 장치는 CRL을 사용하여 연결 컴퓨터에서 인증서를 확인합니다. CRL은 CA(인증 기관)가 만들고 서명하는 파일입니다. CA가 발급했지만 해지한 인증서 목록이 있습니다. 인증서 관리자가 인증서를 해지하면 해당 지문이 CRL에 추가됩니다. 예를 들어 발급된 인증서가 손상된 것으로 파악되거나 의심되는 경우가 있습니다.

> [!IMPORTANT]  
>  CRL 위치는 CA가 발급할 때 인증서에 추가되므로 Configuration Manager에서 사용하는 PKI 인증서를 배포하기 전에 CRL을 계획해야 합니다.  

IIS는 클라이언트 인증서에 대해 CRL을 항상 확인하며 사용자는 Configuration Manager에서 이 구성을 변경할 수 없습니다. 기본적으로 클라이언트는 항상 사이트 시스템에 대해 CRL을 확인합니다. 사이트 속성을 지정하고 CCMSetup 속성을 지정하여 이 설정을 사용하지 않도록 설정합니다.  

인증서 해지 확인을 사용하지만 CRL을 찾을 수 없는 컴퓨터는 인증 체인의 모든 인증서가 해지된 것처럼 작동합니다. 이 동작은 인증서가 목록에 있는지 확인할 수 없기 때문에 발생합니다. 이 시나리오에서는 인증서가 필요하고 CRL을 사용하는 모든 연결이 실패합니다.  

인증서가 사용될 때마다 CRL을 확인하면 해지된 인증서를 사용하는 경우보다 보안이 강화됩니다. 이로 인해 클라이언트에 연결 지연 및 추가 처리가 발생하지만 조직은 인터넷이나 신뢰할 수 없는 네트워크에 있는 클라이언트에 대해 이러한 추가 보안 확인을 요구할 수 있습니다.  

Configuration Manager 클라이언트가 CRL을 확인해야 하는지 여부를 결정하기 전에 PKI 관리자에게 문의하세요. 그런 후에, 다음 조건을 모두 만족하면 Configuration Manager에서 이 옵션을 활성화 상태로 유지하는 것이 좋습니다.  

-   PKI 인프라가 CRL을 지원하고 모든 Configuration Manager 클라이언트에서 CRL을 찾을 수 있는 위치에 게시됩니다. 이러한 클라이언트에는 인터넷에 있는 장치와 신뢰할 수 없는 포리스트에 있는 장치가 포함될 수 있습니다.  

-   PKI 인증서를 사용하도록 구성된 사이트 시스템에 대한 각 연결마다 CRL을 확인해야 하는 요구 사항이 다음 요구 사항보다 큽니다.  
    - 빠른 연결  
    - 클라이언트에서 효율적인 처리  
    - 클라이언트가 CRL을 찾을 수 없는 경우 서버에 연결하지 못할 위험  


###  <a name="BKMK_PlanningForRootCAs"></a> PKI 신뢰할 수 있는 루트 인증서 및 인증서 발급자 목록 계획  

IIS 사이트 시스템이 HTTP를 통한 클라이언트 인증과 HTTPS를 통한 클라이언트 인증 및 암호화에 PKI 클라이언트 인증서를 사용하는 경우 루트 CA 인증서를 사이트 속성으로 가져와야 할 수 있습니다. 다음은 두 가지 시나리오입니다.  

-   Configuration Manager를 사용하여 운영 체제를 배포합니다. 그러면 관리 지점에서 HTTPS 클라이언트 연결만 수락합니다.  

-   관리 지점에서 신뢰하는 루트 인증서에 연결하지 않는 PKI 클라이언트 인증서를 사용합니다.  

    > [!NOTE]  
    >  관리 지점에 사용하는 서버 인증서가 발급되는 CA 계층에서 클라이언트 PKI 인증서를 발급하는 경우, 루트 CA 인증서를 지정하지 않아도 됩니다. 그러나 여러 CA 계층을 사용하고 그러한 계층이 서로 신뢰하는지 여부를 확실하게 알 수 없는 경우 클라이언트의 CA 계층에 루트 CA를 가져와야 합니다.  

Configuration Manager에 루트 CA 인증서를 가져와야 하는 경우 발급 CA 또는 클라이언트 컴퓨터에서 인증서를 내보내세요. 루트 CA인 발급 CA에서 인증서를 내보내는 경우 개인 키를 내보내지 않아야 합니다. 내보내는 인증서 파일을 보안이 유지되는 위치에 저장하여 변조를 방지해야 합니다. 사이트를 설정할 때 파일에 액세스해야 합니다. 따라서 네트워크를 통해 파일에 액세스하는 경우 IPsec을 사용하여 통신이 변조되는 것을 방지해야 합니다.  

가져오는 루트 CA 인증서가 갱신된 경우 갱신된 인증서를 가져와야 합니다.  

이러한 가져온 루트 CA 인증서와 각 관리 지점의 루트 CA 인증서로 인증서 발급자 목록이 만들어지며, Configuration Manager 컴퓨터에서는 이 목록을 다음과 같은 방식으로 사용합니다.  

-   클라이언트가 관리 지점에 연결할 때 관리 지점에서는 클라이언트 인증서가 사이트의 인증서 발급자 목록에 있는 신뢰할 수 있는 루트 인증서에 연결되어 있는지 확인합니다. 그렇지 않으면 인증서가 거부되고 PKI 연결이 실패합니다.  

-   클라이언트가 PKI 인증서를 선택하고 인증서 발급자 목록이 있는 경우 해당 인증서 발급자 목록에 있는 신뢰할 수 있는 루트 인증서에 연결되는 인증서를 선택합니다. 그러한 인증서가 없는 경우 클라이언트는 PKI 인증서를 선택하지 않습니다. 자세한 내용은 [PKI 클라이언트 인증서 선택 계획](#BKMK_PlanningForClientCertificateSelection)을 참조하세요.  


###  <a name="BKMK_PlanningForClientCertificateSelection"></a> PKI 클라이언트 인증서 선택 계획  

 IIS 사이트 시스템이 HTTP를 통한 클라이언트 인증과 HTTPS를 통한 클라이언트 인증 및 암호화에 PKI 클라이언트 인증서를 사용하는 경우 Windows 클라이언트가 Configuration Manager에 사용할 인증서를 선택하는 방법을 계획해야 합니다.  

> [!NOTE]  
>  일부 장치에서는 인증서 선택 방법을 지원하지 않습니다. 대신, 인증서 요구 사항을 충족하는 첫 번째 인증서가 자동으로 선택됩니다. 예를 들어 Mac 컴퓨터 및 모바일 장치의 클라이언트는 인증서 선택 방법을 지원하지 않습니다.  

대부분의 경우 기본 구성과 동작으로 충분합니다. Windows 컴퓨터의 Configuration Manager 클라이언트는 다음 조건을 이 순서로 사용하여 여러 인증서를 필터링합니다.  

1.  인증서 발급자 목록: 인증서가 관리 지점에서 신뢰하는 루트 CA에 연결됩니다.  

2.  인증서가 기본 **개인**인증서 저장소에 있음  

3.  인증서가 해지되거나 만료되지 않고 유효함. 유효성 검사에서는 개인 키에 액세스할 수 있는지도 확인합니다.  

4.  인증서가 클라이언트 인증 기능을 지원하거나 컴퓨터 이름으로 발급되었습니다.  

5.  인증서 유효 기간이 가장 김  

다음 메커니즘을 통해 클라이언트가 인증서 발급자 목록을 사용하도록 구성합니다.  

-   Configuration Manager 사이트 정보와 함께 Active Directory Domain Services에 게시합니다.  

-   클라이언트 강제 설치를 사용하여 클라이언트를 설치합니다.  

-   클라이언트가 사이트에 성공적으로 할당된 후 관리 지점에서 다운로드합니다.  

-   클라이언트 설치 중에 CCMCERTISSUERS의 CCMSetup client.msi 속성으로 지정합니다.  

처음 설치될 때 인증서 발급자 목록이 없고 사이트에 아직 할당되지 않은 클라이언트는 이 검사를 건너뜁니다. 클라이언트가 인증서 발급자 목록이 있고 인증서 발급자 목록의 신뢰할 수 있는 루트 인증서에 연결되는 PKI 인증서를 보유하고 있지 않은 경우 인증서 선택이 실패합니다. 클라이언트는 다른 인증서 선택 기준을 진행하지 않습니다.  

대부분의 경우 Configuration Manager 클라이언트는 고유하고 적절한 PKI 인증서를 정확하게 식별합니다. 그러나 실제로 그렇지 않은 경우 클라이언트 인증 기능을 기반으로 인증서를 선택하는 대신 두 가지 다른 선택 방법을 설정할 수 있습니다.  

-   클라이언트 인증서 주체 이름의 부분 문자열이 일치합니다. 이 메서드는 대/소문자를 구분하지 않는 일치입니다. 주체 필드에 있는 컴퓨터의 FQDN(정규화된 도메인 이름)을 사용하고 도메인 접미사(예: **contoso.com**)를 기반으로 인증서를 선택하는 경우 적합합니다. 그러나 이 선택 방법을 사용하여 인증서를 클라이언트 인증서 저장소에 있는 다른 인증서와 구분하는 인증서 주체 이름의 순차적 문자열을 식별할 수 있습니다.  

    > [!NOTE]  
    >  사이트 설정으로 SAN(주체 대체 이름)에 부분 문자열 일치를 사용할 수 없습니다. CCMSetup을 사용하여 SAN에 부분 문자열 일치를 지정할 수는 있지만, 다음과 같은 시나리오에서는 사이트 속성이 부분 문자열 일치를 덮어씁니다.  
    >   
    >  -   클라이언트는 Active Directory Domain Services에 게시되는 사이트 정보를 검색합니다.  
    > -   클라이언트는 클라이언트 강제 설치를 사용하여 설치됩니다.  
    >   
    >  클라이언트를 수동으로 설치하고 이 클라이언트가 Active Directory Domain Services에서 사이트 정보를 검색하지 않는 경우에만 SAN(주체 대체 이름)에서 부분 문자열 일치를 사용하세요. 예를 들어 이러한 조건은 인터넷 전용 클라이언트에 적용됩니다.  

-   클라이언트 인증서 주체 이름 특성 값 또는 SAN(주체 대체 이름) 특성 값의 일치하는 항목입니다. 이 메서드는 대/소문자를 구분하는 일치입니다. RFC 3280을 준수하는 X500 고유 이름 또는 이와 동등한 OID(개체 식별자)를 사용 중이고 특성 값을 기반으로 인증서를 선택하려는 경우에 적합합니다. 인증서를 고유하게 식별하거나 인증서의 유효성을 검사하고 해당 인증서를 인증서 저장소의 다른 인증서와 구별하기 위해 필요한 특성 및 값만 지정할 수 있습니다.  

다음 표는 Configuration Manager에서 클라이언트 인증서 선택 기준에 대해 지원하는 특성 값을 보여 줍니다.  

|OID 특성|고유 이름 특성|특성 정의|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|도메인 구성 요소|  
|1.2.840.113549.1.9.1|E 또는 E-mail|전자 메일 주소|  
|2.5.4.3|CN|일반 이름|  
|2.5.4.4|SN|주체 이름|  
|2.5.4.5|SERIALNUMBER|일련 번호|  
|2.5.4.6|C|국가 코드|  
|2.5.4.7|L|소재지|  
|2.5.4.8|S 또는 St.|시/도 이름|  
|2.5.4.9|STREET|주소|  
|2.5.4.10|O|조직 이름|  
|2.5.4.11|OU|조직 구성 단위|  
|2.5.4.12|T 또는 Title|제목|  
|2.5.4.42|G 또는 GN 또는 GivenName|이름|  
|2.5.4.43|I 또는 Initials|이니셜|  
|2.5.29.17|(값 없음)|주체 대체 이름|  

선택 기준을 적용한 후 적합한 인증서를 두 개 이상 찾은 경우 기본 구성을 재정의하여 유효 기간이 가장 긴 인증서를 선택하고 그 대신 선택된 인증서가 없다고 지정할 수 있습니다. 이 시나리오에서는 클라이언트가 PKI 인증서를 사용하여 IIS 사이트 시스템과 통신할 수 없습니다. 클라이언트는 자체의 할당된 대체 상태 지점으로 오류 메시지를 보내 인증서 선택 실패에 대한 경고를 알림으로써 인증서 선택 기준을 변경하거나 구체화할 수 있도록 합니다. 그 다음의 클라이언트 동작은 HTTPS 또는 HTTP 중 어느 방식을 통해 연결이 실패했느냐에 따라 달라집니다.  

-   HTTPS를 통해 연결이 실패한 경우: 클라이언트는 HTTP를 통해 연결을 시도하고 클라이언트의 자체 서명된 인증서를 사용합니다.  

-   HTTP를 통해 연결이 실패한 경우: 클라이언트는 자체 서명된 클라이언트 인증서를 사용하여 HTTP를 통해 다시 연결을 시도합니다.  

고유 PKI 클라이언트 인증서를 식별하기 위해 **컴퓨터** 저장소에서 **개인** 저장소의 기본값이 아닌, 사용자 지정 저장소를 지정할 수도 있습니다. 그러나 Configuration Manager와 별도로 저장소를 만들어야 합니다. 인증서를 이 사용자 지정 저장소에 배포하고 유효 기간이 만료되기 전까지 갱신할 수 있어야 합니다.  

자세한 내용은 [클라이언트 PKI 인증서에 대한 설정 구성](/sccm/core/plan-design/security/configure-security#BKMK_ConfigureClientPKI)을 참조하세요.  


###  <a name="BKMK_PlanningForPKITransition"></a> PKI 인증서에 대한 전환 전략 및 인터넷 기반 클라이언트 관리 계획  

Configuration Manager의 유연한 구성 옵션을 사용하면 클라이언트 및 사이트에서 PKI 인증서를 사용하도록 단계적으로 전환하여 안전한 클라이언트 엔드포인트를 구현할 수 있습니다. PKI 인증서를 활용하면 보안을 강화하고 인터넷 클라이언트를 관리할 수 있습니다.  

Configuration Manager에서 선택할 수 있는 구성 옵션은 다양하므로 모든 클라이언트가 HTTPS 연결을 사용하도록 사이트를 전환할 수 있는 단 하나의 방식은 존재하지 않습니다. 그러나 다음 단계를 지침으로 활용할 수 있습니다.  

1.  Configuration Manager 사이트를 설치하고 사이트 시스템에서 HTTPS 및 HTTP를 통한 클라이언트 연결을 허용하도록 사이트를 구성합니다.  

2.  사이트 속성의 **클라이언트 컴퓨터 통신** 탭에서 **사이트 시스템 설정**이 **HTTP 또는 HTTPS**가 되도록 구성하고 **사용 가능한 경우 PKI 클라이언트 인증서(클라이언트 인증 기능) 사용**을 선택합니다.  자세한 내용은 [클라이언트 PKI 인증서에 대한 설정 구성](/sccm/core/plan-design/security/configure-security#BKMK_ConfigureClientPKI)을 참조하세요.  

3.  클라이언트 인증서에 대해 PKI 롤아웃을 시험합니다. 배포 예제는 [Windows 컴퓨터용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012)를 참조하세요.  

4.  클라이언트 강제 설치 방법을 사용하여 클라이언트를 설치합니다. 자세한 내용은 [클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)을 참조하세요.  

5.  Configuration Manager 콘솔에서 보고서와 정보를 사용하여 클라이언트 배포 및 상태를 모니터링합니다.  

6.  **자산 및 호환성** 작업 영역의 **장치** 노드에서 **클라이언트 인증서** 열을 확인하여 클라이언트 PKI 인증서를 사용하는 클라이언트 수를 추적합니다.  

     Configuration Manager HTTPS 준비 평가 도구(**cmHttpsReadiness.exe**)를 컴퓨터에 배포할 수도 있습니다. 그런 다음, 보고서를 사용하여 Configuration Manager와 함께 클라이언트 PKI 인증서를 사용할 수 있는 컴퓨터 수를 확인합니다.  

    > [!NOTE]  
    >  Configuration Manager 클라이언트를 설치하면 `%windir%\CCM` 폴더에 **CMHttpsReadiness.exe** 도구가 설치됩니다. 이 도구를 실행할 때 다음 명령줄 옵션을 사용할 수 있습니다.  
    >   
    > - `/Store:<name>`: 이 옵션은 **CCMCERTSTORE** client.msi 속성과 동일합니다.  
    > - `/Issuers:<list>`: 이 옵션은 **CCMCERTISSUERS** client.msi 속성과 동일합니다.    
    > - `/Criteria:<criteria>`: 이 옵션은 **CCMCERTSEL** client.msi 속성과 동일합니다.    
    > - `/SelectFirstCert`: 이 옵션은 **CCMFIRSTCERT** client.msi 속성과 동일합니다.    
    >   
    >  자세한 내용은 [클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

7.  충분한 클라이언트가 자체 클라이언트 PKI 인증서를 HTTP를 통한 인증에 성공적으로 사용하고 있다고 확신할 경우 다음 단계를 수행하세요.  

    1.  PKI 웹 서버 인증서를 사이트의 추가 관리 지점을 실행하는 구성원 서버에 배포하고 IIS에서 해당 인증서를 구성합니다. 자세한 내용은 [IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012)를 참조하세요.  

    2.  이 서버에 관리 지점 역할을 설치하고 **HTTPS** 에 대한 관리 지점 속성에서 **클라이언트 연결**옵션을 구성합니다.  

8.  PKI 인증서를 보유한 클라이언트에서 HTTPS를 통해 새 관리 지점을 사용하는지 모니터링 및 확인합니다. IIS 로깅 또는 성능 카운터를 사용하여 확인할 수 있습니다.  

9. HTTPS 클라이언트 연결을 사용하도록 다른 사이트 시스템 역할을 다시 구성합니다. 인터넷에서 클라이언트를 관리하려는 경우 사이트 시스템에 인터넷 FQDN이 있는지 확인합니다. 인터넷에서 들어오는 클라이언트 연결을 허용하도록 개별 관리 지점 및 배포 지점을 구성합니다.  

    > [!IMPORTANT]  
    >  사이트 시스템 역할에서 인터넷의 연결을 허용하도록 설정하기 전에 인터넷 기반 클라이언트 관리에 대한 계획 정보 및 필수 구성 요소를 검토하세요. 자세한 내용은 [엔드포인트 간의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints)을 참조하세요.  

10. 클라이언트 및 IIS를 실행하는 사이트 시스템에 대한 PKI 인증서 배포를 확장합니다. 필요에 따라 HTTPS 클라이언트 연결 및 인터넷 연결을 위한 사이트 시스템 역할을 설정합니다.  

11. 최상의 보안 구현: 모든 클라이언트에서 인증 및 암호화에 클라이언트 PKI 인증서를 사용하고 있다고 확신할 경우 HTTPS만 사용하도록 사이트 속성을 변경합니다.  

 이 계획에서는 먼저 HTTP를 통한 인증에만 사용할 PKI 인증서를 도입한 다음, HTTPS를 통한 인증 및 암호화에 사용할 PKI 인증서를 도입합니다. 이 계획에 따라 이러한 인증서를 점진적으로 도입하면 클라이언트가 관리되지 않을 위험이 줄어듭니다. Configuration Manager에서 지원하는 최상의 보안을 활용할 수도 있습니다.  

##  <a name="BKMK_PlanningForRTK"></a> 신뢰할 수 있는 루트 키 계획  

 Configuration Manager 신뢰 루트 키에서 제공하는 메커니즘을 통해 Configuration Manager 클라이언트가 사이트 시스템이 해당 계층 구조에 속하는지 확인할 수 있습니다. 모든 사이트 서버는 다른 사이트와 통신하기 위한 사이트 교환 키를 생성합니다. 계층 내 최상위 사이트의 사이트 교환 키는 신뢰할 수 있는 루트 키라고 합니다.  

 Configuration Manager에서 신뢰할 수 있는 루트 키의 기능은 공개 키 인프라의 루트 인증서와 유사합니다. 신뢰할 수 있는 루트 키의 개인 키로 서명된 모든 항목은 계층 구조의 아래쪽에서 더 신뢰됩니다. 클라이언트는 사이트의 신뢰할 수 있는 루트 키 복사본을 **root\ccm\locationservices** WMI 네임스페이스에 저장합니다. 

 예를 들어 사이트에서 신뢰할 수 있는 루트 키의 개인 키를 사용하여 서명하는 관리 지점에 인증서를 발급합니다. 사이트에서는 신뢰할 수 있는 루트 키의 공개 키를 클라이언트와 공유합니다. 그런 다음, 클라이언트는 해당 계층 구조에 있는 관리 지점과 해당 계층 구조에 없는 관리 지점을 구분할 수 있습니다.   

 클라이언트는 다음 두 가지 메커니즘을 통해 신뢰할 수 있는 루트 키의 공개 복사본을 자동으로 검색합니다.  

 - Configuration Manager를 위해 Active Directory 스키마를 확장하고 Active Directory Domain Services에 사이트를 게시합니다. 그런 다음, 글로벌 카탈로그 서버에서 이 사이트 정보를 검색합니다. 자세한 내용은 [사이트 게시를 위해 Active Directory 준비](/sccm/core/plan-design/network/extend-the-active-directory-schema)를 참조하세요.  

 - 클라이언트 강제 설치 방법을 사용하여 클라이언트를 설치하는 경우 자세한 내용은 [클라이언트 강제 설치](/sccm/core/clients/deploy/plan/client-installation-methods#client-push-installation)를 참조하세요.  

 클라이언트에서 이러한 메커니즘 중 하나를 사용하여 신뢰할 수 있는 루트 키를 검색할 수 없는 경우 클라이언트는 통신하는 첫 번째 관리 지점에서 제공하는 신뢰할 수 있는 루트 키를 신뢰합니다. 이 시나리오에서 클라이언트는 공격자의 관리 지점으로 잘못 연결될 수도 있으며 이 경우 클라이언트는 허위 관리 지점의 정책을 수신하게 됩니다. 이 작업에는 정교한 공격자가 필요합니다. 이 공격은 클라이언트가 유효한 관리 지점에서 신뢰할 수 있는 루트 키를 검색하기 전에 짧은 시간으로 제한됩니다. 공격자가 클라이언트를 악성 관리 지점으로 잘못 안내할 위험을 줄이려면 신뢰할 수 있는 루트 키를 사용하여 클라이언트를 사전 프로비전합니다.  

 다음 절차를 사용하여 사전 프로비전을 수행하고 Configuration Manager 클라이언트에 대해 신뢰할 수 있는 루트 키를 확인합니다.  

 - [파일을 사용하여 신뢰할 수 있는 루트 키로 클라이언트 사전 프로비전](#bkmk_trk-provision-file)  

 - [파일을 사용하지 않고 신뢰할 수 있는 루트 키로 클라이언트를 사전 프로비전](#bkmk_trk-provision-nofile)  

 - [클라이언트에서 신뢰할 수 있는 루트 키 확인](#bkmk_trk-verify)  

 - [신뢰할 수 있는 루트 키 제거 또는 교체](#bkmk_trk-reset)  

 > [!NOTE]  
 > 클라이언트가 Active Directory Domain Services 또는 클라이언트 강제 설치에서 신뢰할 수 있는 루트 키를 가져올 수 있는 경우에는 사전 프로비전할 필요가 없습니다. 
 > 
 > 클라이언트가 관리 지점에 HTTPS 통신을 사용하는 경우 신뢰할 수 있는 루트 키를 사전 프로비전할 필요가 없습니다. PKI 인증서를 사용하여 트러스트를 설정합니다.  


### <a name="bkmk_trk-provision-file"></a> 파일을 사용하여 신뢰할 수 있는 루트 키로 클라이언트 사전 프로비전  

1.  사이트 서버의 텍스트 편집기에서 `<Configuration Manager install directory>\bin\mobileclient.tcf` 파일을 엽니다.  

2.  **SMSPublicRootKey=** 인 항목을 찾습니다. 해당 행에서 키를 복사하고 아무 내용도 변경하지 않고 파일을 닫습니다.  

3.  새 텍스트 파일을 만들고 mobileclient.tcf 파일에서 복사한 키 정보를 붙여넣습니다.  

4.  모든 컴퓨터에서 액세스할 수 있지만 파일이 변조되지 않는 위치에 파일을 저장합니다.  

5.  Client.msi 속성을 허용하는 설치 방법을 사용하여 클라이언트를 설치합니다. `SMSROOTKEYPATH=<full path and file name>` 속성을 지정합니다.  

    > [!IMPORTANT]  
    >  클라이언트 설치 중에 신뢰할 수 있는 루트 키를 지정할 때는 사이트 코드도 지정합니다. `SMSSITECODE=<site code>` client.msi 속성을 사용합니다.   


### <a name="bkmk_trk-provision-nofile"></a> 파일을 사용하지 않고 신뢰할 수 있는 루트 키로 클라이언트를 사전 프로비전  

1.  사이트 서버의 텍스트 편집기에서 `<Configuration Manager install directory>\bin\mobileclient.tcf` 파일을 엽니다.  

2.  **SMSPublicRootKey=** 인 항목을 찾습니다. 해당 행에서 키를 복사하고 아무 내용도 변경하지 않고 파일을 닫습니다.  

3.  Client.msi 속성을 허용하는 설치 방법을 사용하여 클라이언트를 설치합니다. `SMSPublicRootKey=<key>` client.msi 속성을 지정합니다. 여기서 `<key>`는 mobileclient.tcf에서 복사한 문자열입니다.  

    > [!IMPORTANT]  
    >  클라이언트 설치 중에 신뢰할 수 있는 루트 키를 지정할 때는 사이트 코드도 지정합니다. `SMSSITECODE=<site code>` client.msi 속성을 사용합니다.   


### <a name="bkmk_trk-verify"></a> 클라이언트에서 신뢰할 수 있는 루트 키 확인  

1. Windows PowerShell 콘솔을 관리자 권한으로 엽니다.  

2. 다음 명령을 실행합니다.  

``` PowerShell
 (Get-WmiObject -Namespace root\ccm\locationservices -Class TrustedRootKey).TrustedRootKey
```

반환된 문자열은 신뢰할 수 있는 루트 키입니다. 사이트 서버의 mobileclient.tcf 파일에 있는 **SMSPublicRootKey** 값과 일치하는지 확인합니다.  


### <a name="bkmk_trk-reset"></a> 신뢰할 수 있는 루트 키 제거 또는 교체  

 client.msi 속성인 **RESETKEYINFORMATION = TRUE**를 사용하여 클라이언트에서 신뢰할 수 있는 루트 키를 제거합니다. 

 신뢰할 수 있는 루트 키를 교체하려면 클라이언트를 새 신뢰할 수 있는 루트 키와 함께 다시 설치합니다. 예를 들어 클라이언트 강제 설치를 사용하거나 client.msi 속성 **SMSPublicRootKey**를 지정합니다.  

 이러한 설치 속성에 대한 자세한 내용은 [클라이언트 설치 매개 변수 및 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.



##  <a name="BKMK_PlanningForSigningEncryption"></a> 서명 및 암호화 계획  
 
 모든 클라이언트 통신에 대해 PKI 인증서를 사용하는 경우 클라이언트 데이터 통신의 보안을 위해 서명 및 암호화를 계획할 필요가 없습니다. IIS를 실행하는 사이트 시스템에서 HTTP 클라이언트 연결을 허용하도록 설정하는 경우 사이트의 클라이언트 통신을 보호할 방법을 결정합니다.  

 클라이언트가 관리 지점에 보내는 데이터를 보호하려면 클라이언트에 데이터 서명을 요구하면 됩니다. 서명에 SHA-256 알고리즘을 요구할 수도 있습니다. 이 구성이 더욱 안전하지만 모든 클라이언트에서 지원하지 않는 한 SHA-256은 필요하지 않습니다. 많은 운영 체제가 기본적으로 이 알고리즘을 지원하지만 이전 운영 체제에서는 업데이트 또는 핫픽스가 필요할 수 있습니다. 

 서명은 데이터 변조를 방지하는 데 도움이 되지만 암호화는 정보 노출로부터 데이터를 보호하도록 도와줍니다. 클라이언트가 사이트의 관리 지점으로 보내는 인벤토리 데이터 및 상태 메시지에 3DES 암호화를 사용할 수 있습니다. 이 옵션을 지원하기 위해 클라이언트에 업데이트를 설치할 필요가 없습니다. 클라이언트 및 관리 지점에는 암호화 및 암호 해독을 위해 추가 CPU 사용량이 필요합니다.  

 서명 및 암호화 설정을 구성하는 방법에 대한 자세한 내용은 [서명 및 암호화 구성](/sccm/core/plan-design/security/configure-security#BKMK_ConfigureSigningEncryption)을 참조하세요.  



##  <a name="BKMK_PlanningForRBA"></a> 역할 기반 관리 계획  

 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.  



## <a name="bkmk_planazuread"></a> Azure Active Directory 계획

 Configuration Manager는 Azure AD(Azure Active Directory)와 통합되어 사이트 및 클라이언트가 최신 인증을 사용할 수 있도록 합니다. Azure AD를 사용하여 사이트를 온보딩하면 다음 Configuration Manager 시나리오가 지원됩니다.

**클라이언트**  

- [클라이언트 관리 게이트웨이를 통해 인터넷에서 클라이언트 관리](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#scenarios)  

- [클라우드 도메인 조인 장치 관리](/sccm/core/clients/deploy/deploy-clients-cmg-azure)  

- [공동 관리](/sccm/core/clients/manage/co-management-overview)  

- [사용자 사용 가능 앱 배포](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)  

- [비즈니스용 Microsoft Store 온라인 앱](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)  

- 인프라 요구 사항을 줄입니다. 예: 응용 프로그램 카탈로그 대신 [관리 지점을 사용하는 소프트웨어 센터](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_userex)  

- [Office 365 앱 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates)  


**서버**  

- [업그레이드 준비](/sccm/core/clients/manage/upgrade-readiness)  

- [Windows Analytics](/sccm/core/clients/manage/monitor-windows-analytics)  

- [Azure Log Analytics](/sccm/core/clients/manage/sync-data-log-analytics)  

- [커뮤니티 허브](/sccm/core/get-started/capabilities-in-technical-preview-1807#bkmk_hub)  

- [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)  

- [사용자 검색](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  


 사이트를 Azure AD에 연결하는 방법에 대한 자세한 내용은 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요.


 Azure AD에 대한 자세한 내용은 [Azure Active Directory 설명서](https://docs.microsoft.com/azure/active-directory/)를 참조하세요.



## <a name="bkmk_auth"></a> SMS 공급 기업 인증 계획
<!--1357013--> 

1810 버전부터 관리자가 Configuration Manager 사이트에 액세스하는 데 필요한 최소 인증 수준을 지정할 수 있습니다. 이 기능은 관리자에게 필요한 수준으로 Windows에 로그인하도록 요구합니다. 이 기능은 SMS 공급 기업에 액세스하는 모든 구성 요소에 적용됩니다. 예를 들어 Configuration Manager 콘솔, SDK 메서드 및 Windows PowerShell cmdlet에 적용됩니다. 

이 구성은 계층 구조 범위 설정입니다. 이 설정을 변경하기 전에 모든 Configuration Manager 관리자가 필요한 인증 수준을 사용하여 Windows에 로그인할 수 있는지 확인합니다. 

다음 수준을 사용할 수 있습니다.

- **Windows 인증**: Active Directory 도메인 자격 증명을 사용한 인증이 필요합니다.   

- **인증서 인증**: 신뢰할 수 있는 PKI 인증 기관에서 발급한 유효한 인증서를 사용한 인증을 요구합니다.  

- **비즈니스용 Windows Hello 인증**: 장치에 연결되고 생체 인식 또는 PIN을 사용하는 강력한 2단계 인증으로 인증해야 합니다.  

자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_auth)을 참조하세요. 



## <a name="see-also"></a>참고 항목
- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  

- [보안 구성](/sccm/core/plan-design/security/configure-security)  

- [엔드포인트 간의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints)  

- [암호화 컨트롤 기술 참조](/sccm/core/plan-design/security/cryptographic-controls-tehnical-reference)  

- [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)  

