---
title: "System Center Configuration Manager에서 보안 계획 | Microsoft 문서"
description: "System Center Configuration Manager의 보안에 대한 모범 사례 및 기타 정보를 가져옵니다."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a216814-ca8c-4d2e-bcef-dc00966a3c9f
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: af06fb10d905e3fe447c6cd6ed35dac10488161f
ms.openlocfilehash: 1bf519ad4593f6a08d7dc393f9fab91c70b51b25
ms.contentlocale: ko-kr
ms.lasthandoff: 01/05/2017


---
# <a name="plan-for-security-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 보안 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

##  <a name="BKMK_PlanningForCertificates"></a> 인증서(자체 서명 및 PKI) 계획  
 Configuration Manager에서는 자체 서명된 인증서와 PKI(공개 키 인프라) 인증서를 결합하여 사용합니다.  

 보안 모범 사례에 따라 가능한 경우 항상 PKI 인증서를 사용하는 것이 좋습니다. PKI 인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요. 모바일 장치를 등록하거나 Intel AMT(Active Management Technology)를 프로비전하는 경우와 같이 Configuration Manager에서 PKI 인증서를 요구하는 경우 Active Directory Domain Services와 엔터프라이즈 인증 기관을 사용해야 합니다. 다른 모든 PKI 인증서의 경우 Configuration Manager와 별개로 인증서를 배포하고 관리해야 합니다.  

 또한 클라이언트 컴퓨터가 인터넷 기반 사이트 시스템에 연결되는 경우 PKI 인증서를 반드시 사용해야 하며, 클라이언트가 IIS(인터넷 정보 서비스)를 실행하는 사이트 시스템에 연결되는 경우 PKI 인증서를 사용하는 것이 좋습니다. 클라이언트 통신에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법](../../../core/clients/deploy/configure-client-communication-ports.md)을 참조하세요.  

 또한 PKI를 사용하는 경우 IPsec을 사용하여 단일 사이트 내부 및 여러 사이트에 있는 사이트 시스템 간의 서버 통신을 보호하고 컴퓨터 간의 기타 데이터 전송에서 보안을 유지할 수 있습니다. IPsec 구현은 Configuration Manager와 관련이 없습니다.  

 Configuration Manager에서는 PKI 인증서를 사용할 수 없을 때 자체 서명된 인증서를 자동으로 생성할 수 있으며, Configuration Manager의 일부 인증서는 항상 자체 서명됩니다. 대부분의 경우 Configuration Manager에서는 자체 서명된 인증서를 자동으로 관리하며, 사용자의 별도 작업이 필요 없습니다. 사이트 서버 서명 인증서는 예외입니다. 사이트 서버 서명 인증서는 항상 자체 서명되며, 클라이언트가 관리 지점에서 다운로드하는 클라이언트 정책이 사이트 서버에서 전송된 것이고 변조되지 않았음을 보증해 줍니다.  

### <a name="plan-for-the-site-server-signing-certificate-self-signed"></a>사이트 서버 서명 인증서(자체 서명) 계획  
 Active Directory Domain Services와 클라이언트 강제 설치를 사용할 경우 클라이언트가 사이트 서버 서명 인증서의 복사본을 안전하게 가져올 수 있습니다. 클라이언트에서 이러한 메커니즘 중 하나를 사용해서 사이트 서버 서명 인증서의 복사본을 가져올 수 없는 경우 모범 사례에 따라 클라이언트를 설치할 때 사이트 서버 서명 인증서의 복사본을 설치하는 것이 좋습니다. 클라이언트가 처음으로 사이트와 통신하는 경로가 인터넷인 경우 관리 지점이 신뢰할 수 없는 네트워크에 연결되어 공격에 취약해지므로 이렇게 하는 것이 특히 중요합니다. 이와 같은 별도의 조치를 취하지 않을 경우 클라이언트가 관리 지점에서 사이트 서버 서명 인증서의 복사본을 자동으로 다운로드합니다.  

 클라이언트가 사이트 서버 인증서의 복사본을 안전하게 가져올 수 없는 시나리오는 다음과 같습니다.  

-   클라이언트 강제 설치를 사용하여 클라이언트를 설치하지 않고 다음 조건 중 하나 이상에 해당하는 경우:  

    -   Active Directory 스키마는 Configuration Manager를 위해 확장되지 않습니다.  

    -   클라이언트의 사이트가 Active Directory Domain Services에 게시되지 않음  

    -   클라이언트가 신뢰할 수 없는 포리스트 또는 작업 그룹에 속해 있음  

-   인터넷에서 클라이언트 설치  

##### <a name="to-install-clients-with-a-copy-of-the-site-server-signing-certificate"></a>클라이언트와 함께 사이트 서버 서명 인증서의 복사본을 설치하려면  

1.  클라이언트의 기본 사이트 서버에서 사이트 서버 서명 인증서를 찾습니다. 인증서는 **SMS** 인증서 저장소에 저장되어 있으며 주체 이름이 **사이트 서버**이고 이름이 **사이트 서버 서명 인증서**입니다.  

2.  개인 키 없이 인증서를 내보내고 인증서 파일을 안전하게 저장하며 보안 채널(예: SMB(서버 메시지 블록) 서명 또는 IPSec 사용)에서만 파일에 액세스합니다.  

3.  CCMSetup.exe로 Client.msi 속성 **SMSSIGNCERT=***&lt;전체 경로 및 파일 이름\>*을 사용하여 클라이언트를 설치합니다.  

###  <a name="BKMK_PlanningForCRLs"></a> PKI 인증서 해지 계획  
Configuration Manager에 PKI 인증서를 사용하는 경우 클라이언트와 서버가 연결하는 컴퓨터에서 인증서를 확인하기 위해 CRL(인증서 해지 목록)을 사용할지 여부와 사용하는 방식을 계획해야 합니다. CRL은 CA가 만들고 서명하는 파일이고 CA(인증 기관)가 발급했지만 해지한 인증서 목록을 포함합니다. 예를 들어 발급된 인증서가 손상된 것으로 파악되거나 의심될 경우 CA 관리자가 인증서를 해지할 수 있습니다.  

> [!IMPORTANT]  
>  CRL 위치는 CA가 발급할 때 인증서에 추가되므로 Configuration Manager에서 사용할 PKI 인증서를 배포하기 전에 CRL을 계획해야 합니다.  

기본적으로 IIS는 클라이언트 인증서에 대해 CRL을 항상 확인하며 사용자는 Configuration Manager에서 이 구성을 변경할 수 없습니다. 기본적으로 클라이언트는 항상 사이트 시스템에 대해 CRL을 확인합니다. 사이트 속성을 지정하고 CCMSetup 속성을 지정하여 이 설정을 사용하지 않도록 설정할 수 있습니다. 대역 외에서 Intel AMT 기반 컴퓨터를 관리하는 경우 대역 외 서비스 지점과 대역 외 관리 콘솔이 실행되는 컴퓨터에 대해 CRL 확인을 사용하도록 설정할 수 있습니다.  

인증서 해지 확인을 사용하지만 CRL을 찾을 수 없는 컴퓨터는 인증서가 목록에 없는지 확인할 수 없기 때문에 인증 체인의 모든 인증서가 해지된 것처럼 동작합니다. 이 시나리오에서는 인증서가 필요하고 CRL을 사용하는 모든 연결이 실패합니다.  

인증서가 사용될 때마다 CRL을 확인하면 해지된 인증서를 사용하는 위험을 더욱 철저하게 방지할 수 있는 반면, 클라이언트에서 연결 지연이 발생하고 추가 처리가 이루어집니다. 이러한 강력한 보안 확인은 클라이언트가 인터넷이나 신뢰할 수 없는 네트워크에 있는 경우 필요할 수 있습니다.  

Configuration Manager 클라이언트에서 CRL을 확인할지 여부를 결정하기 전에 먼저 PKI 관리자의 조언을 구하고, 다음 두 조건에 모두 해당하는 경우 Configuration Manager에서 이 옵션을 사용하는 것을 고려하세요.  

-   PKI 인프라가 CRL을 지원하고 CRL이 모든 Configuration Manager 클라이언트에서 찾을 수 있는 위치에 게시되어 있음. 여기에는 신뢰할 수 없는 포리스트에 있는 클라이언트와 인터넷에 있는 클라이언트(인터넷 기반 클라이언트 관리를 사용하는 경우)가 포함될 수 있습니다.  

-   PKI 인증서를 사용하도록 구성된 사이트 시스템에 연결할 때마다 CRL을 확인해야 하는 것은 클라이언트에서 더 빠르게 연결하고 효율적으로 처리해야 하는 것과 클라이언트가 CRL을 찾을 수 없어 서버에 연결하지 못하는 위험보다 더 중요합니다.  

###  <a name="BKMK_PlanningForRootCAs"></a> PKI 신뢰할 수 있는 루트 인증서 및 인증서 발급자 목록 계획  
IIS 사이트 시스템이 HTTP를 통한 클라이언트 인증과 HTTPS를 통한 클라이언트 인증 및 암호화에 PKI 클라이언트 인증서를 사용하는 경우 루트 CA 인증서를 사이트 속성으로 가져와야 할 수 있습니다. 다음은 두 가지 시나리오입니다.  

-   Configuration Manager를 사용하여 운영 체제를 배포합니다. 그러면 관리 지점에서 HTTPS 클라이언트 연결만 수락합니다.  

-   관리 지점에서 신뢰하는 루트 CA(인증 기관)에 연결되지 않은 PKI 클라이언트 인증서를 사용합니다.  

    > [!NOTE]  
    >  관리 지점에 사용하는 서버 인증서가 발급되는 CA 계층에서 클라이언트 PKI 인증서를 발급하는 경우, 루트 CA 인증서를 지정하지 않아도 됩니다. 그러나 여러 CA 계층을 사용하고 그러한 계층이 서로 신뢰하는지 여부를 확실하게 알 수 없는 경우 클라이언트의 CA 계층에 루트 CA를 가져와야 합니다.  

Configuration Manager에 루트 CA 인증서를 가져와야 하는 경우 발급 CA 또는 클라이언트 컴퓨터에서 인증서를 내보내세요. 루트 CA인 발급 CA에서 인증서를 내보내는 경우 개인 키를 내보내지 않아야 합니다. 내보내는 인증서 파일을 보안이 유지되는 위치에 저장하여 변조를 방지해야 합니다. 사이트를 설정할 때 파일에 액세스할 수 있어야 합니다. 따라서 네트워크를 통해 파일에 액세스하는 경우 SMB 서명이나 IPsec을 사용하여 통신이 변조되지 않도록 해야 합니다.  

가져오는 루트 CA 인증서가 갱신된 경우 갱신된 인증서를 가져와야 합니다.  

이러한 가져온 루트 CA 인증서와 각 관리 지점의 루트 CA 인증서로 인증서 발급자 목록이 만들어지며, Configuration Manager 컴퓨터에서는 이 목록을 다음과 같은 방식으로 사용합니다.  

-   클라이언트가 관리 지점에 연결할 때 관리 지점에서는 클라이언트 인증서가 해당 사이트의 인증서 발급자 목록에 있는 신뢰할 수 있는 루트 인증서에 연결되는지 확인합니다. 그렇지 않은 경우 인증서가 거부되고 PKI 연결이 실패합니다.  

-   클라이언트가 PKI 인증서를 선택하고 인증서 발급자 목록이 있는 경우 해당 인증서 발급자 목록에 있는 신뢰할 수 있는 루트 인증서에 연결되는 인증서를 선택합니다. 그러한 인증서가 없는 경우 클라이언트가 PKI 인증서를 선택하지 않습니다. 클라이언트 인증서 프로세스에 대한 자세한 내용은 이 문서에서 [PKI 클라이언트 인증서 선택 계획](#BKMK_PlanningForClientCertificateSelection)을 참조하세요.  

또한 사이트 구성과는 별도로 모바일 장치를 등록하고, Mac 컴퓨터를 등록하고, 무선 네트워크에 Intel AMT 기반 컴퓨터를 설정할 때 루트 CA 인증서를 가져와야 할 수 있습니다.  

###  <a name="BKMK_PlanningForClientCertificateSelection"></a> PKI 클라이언트 인증서 선택 계획  
 IIS 사이트 시스템이 HTTP를 통한 클라이언트 인증과 HTTPS를 통한 클라이언트 인증 및 암호화에 PKI 클라이언트 인증서를 사용하는 경우 Windows 클라이언트가 Configuration Manager에 사용할 인증서를 선택하는 방식을 계획해야 합니다.  

> [!NOTE]  
>  일부 장치에서는 인증서 선택 방법을 지원하지 않습니다. 대신, 인증서 요구 사항을 충족하는 첫 번째 인증서가 자동으로 선택됩니다. 예를 들어 Mac 컴퓨터의 클라이언트 및 모바일 장치는 인증서 선택 방법을 지원하지 않습니다.  

대부분의 경우 기본 구성과 동작으로 충분합니다. Windows 컴퓨터의 Configuration Manager 클라이언트는 다음 조건을 이 순서로 사용하여 여러 인증서를 필터링합니다.  

1.  인증서 발급자 목록: 인증서가 관리 지점에서 신뢰하는 루트 CA에 연결됩니다.  

2.  인증서가 기본 **개인**인증서 저장소에 있음  

3.  인증서가 해지되거나 만료되지 않고 유효함. 유효성 확인을 통해 개인 키를 액세스할 수 있는지 확인하고 인증서가 Configuration Manager와 호환되지 않는 버전 3 인증서 템플릿을 사용하여 만들어지지 않았는지 확인합니다.  

4.  인증서가 클라이언트 인증 기능을 갖거나 해당 컴퓨터 이름으로 발급되었음  

5.  인증서 유효 기간이 가장 김  

다음과 같은 메커니즘을 통해 클라이언트가 인증서 발급자 목록을 사용하도록 구성할 수 있습니다.  

-   이는 Active Directory Domain Services에 Configuration Manager 사이트 정보로 게시됩니다.  

-   클라이언트 강제 설치를 사용하여 클라이언트가 설치됩니다.  

-   클라이언트가 사이트에 할당된 후 관리 지점에서 인증서 발급자 목록을 다운로드합니다.  

-   클라이언트 설치 시 CCMCERTISSUERS의 CCMSetup client.msi 속성으로 인증서 발급자 목록을 지정합니다.  

처음 설치될 때 인증서 발급자 목록이 없고 사이트에 아직 할당되지 않은 클라이언트는 이 확인을 건너뜁니다. 클라이언트에 인증서 발급자 목록이 있고 인증서 발급자 목록에 있는 신뢰할 수 있는 루트 인증서에 연결되는 PKI 인증서가 없는 경우, 인증서 선택이 실패하며 클라이언트가 계속해서 다른 인증서 선택 기준을 사용하지 않습니다.  

대부분의 경우 Configuration Manager 클라이언트는 고유하고 적절한 PKI 인증서를 정확하게 식별합니다. 그러나 이렇게 하지 못할 경우 클라이언트 인증 기능을 기반으로 인증서를 선택하는 대신 두 가지 다른 선택 방법을 설정할 수 있습니다.  

-   클라이언트 인증서 주체 이름의 부분 문자열 일치. 이 방법은 주체 필드에 컴퓨터의 FQDN(정규화된 도메인 이름)을 사용하고 도메인 접미사(예: **contoso.com**)를 기반으로 인증서를 선택하는 경우 적절한 일치이며 대/소문자를 구분하지 않습니다. 그러나 이 선택 방법을 사용하여 인증서를 클라이언트 인증서 저장소에 있는 다른 인증서와 구분하는, 인증서 주체 이름의 순차적 문자열을 식별할 수 있습니다.  

    > [!NOTE]  
    >  사이트 설정으로 SAN(주체 대체 이름)에 부분 문자열 일치를 사용할 수 없습니다. CCMSetup을 사용하여 SAN에 부분 문자열 일치를 지정할 수는 있지만, 다음과 같은 시나리오에서 사이트 속성이 부분 문자열 일치를 덮어씁니다.  
    >   
    >  -   클라이언트는 Active Directory Domain Services에 게시되는 사이트 정보를 검색합니다.  
    > -   클라이언트는 클라이언트 강제 설치를 사용하여 설치됩니다.  
    >   
    >  클라이언트를 수동으로 설치하고 이 클라이언트가 Active Directory Domain Services에서 사이트 정보를 검색하지 않는 경우에만 SAN(주체 대체 이름)에서 부분 문자열 일치를 사용하세요. 예를 들어 이러한 조건은 인터넷 전용 클라이언트에 적용됩니다.  

-   이 경우 클라이언트 인증서 주체 이름 특성 값 또는 SAN(주체 대체 이름) 특성 값의 일치 내용이 해당됩니다. 이는 대소문자 구분 일치 방식으로서, X500 고유 이름 또는 그에 해당하는 RFC 3280 호환 OID(개체 식별자)를 사용 중이고 인증서 선택 기준을 특성 값으로 설정하려 할 때 적합한 방식입니다. 인증서를 고유하게 식별하거나 인증서의 유효성을 검사하고 해당 인증서를 인증서 저장소의 다른 인증서와 구별하기 위해 필요한 특성 및 값만 지정할 수 있습니다.  

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

선택 기준을 적용한 후 적합한 인증서를 두 개 이상 찾은 경우 기본 구성을 재정의하여 유효 기간이 가장 긴 인증서를 선택하고 그 대신 선택된 인증서가 없다고 지정할 수 있습니다. 이 시나리오에서 클라이언트는 PKI 인증서를 사용하여 IIS 사이트 시스템과 통신할 수 없습니다. 클라이언트는 자체의 할당된 대체 상태 지점으로 오류 메시지를 보내 인증서 선택 실패에 대한 경고를 알림으로써 인증서 선택 기준을 변경하거나 구체화할 수 있도록 합니다. 그 다음의 클라이언트 동작은 HTTPS 또는 HTTP 중 어느 방식을 통해 연결이 실패했느냐에 따라 달라집니다.  

-   HTTPS를 통해 연결이 실패한 경우: 클라이언트는 HTTP를 통해 연결을 시도하고 클라이언트의 자체 서명된 인증서를 사용합니다.  

-   HTTP를 통해 연결이 실패한 경우: 클라이언트는 자체 서명된 클라이언트 인증서를 사용하여 HTTP를 통해 다시 연결을 시도합니다.  

고유 PKI 클라이언트 인증서를 식별하기 위해 **컴퓨터** 저장소에서 **개인** 저장소의 기본값이 아닌, 사용자 지정 저장소를 지정할 수도 있습니다. 그러나 이 저장소는 Configuration Manager와 독립적으로 만들어야 하며 인증서를 이 사용자 지정 저장소에 배포하고 유효 기간이 만료되기 전까지 갱신할 수 있어야 합니다.  

클라이언트 인증서 설정을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 보안 구성](../../../core/plan-design/security/configure-security.md) 문서에서 [클라이언트 PKI 인증서의 설정 구성](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) 섹션을 참조하세요.  

###  <a name="BKMK_PlanningForPKITransition"></a> PKI 인증서에 대한 전환 전략 및 인터넷 기반 클라이언트 관리 계획  
Configuration Manager의 유연한 구성 옵션을 사용하면 클라이언트 및 사이트에서 PKI 인증서를 사용하도록 단계적으로 전환하여 안전한 클라이언트 끝점을 구현할 수 있습니다. PKI 인증서를 활용하면 보안을 강화하고 인터넷 클라이언트를 관리할 수 있습니다.  

Configuration Manager에서 선택할 수 있는 구성 옵션은 다양하므로 모든 클라이언트가 HTTPS 연결을 사용하도록 사이트를 전환할 수 있는 단 하나의 방식은 존재하지 않습니다. 그러나 다음 단계를 지침으로 활용할 수 있습니다.  

1.  Configuration Manager 사이트를 설치하고 사이트 시스템에서 HTTPS 및 HTTP를 통한 클라이언트 연결을 허용하도록 사이트를 구성합니다.  

2.  사이트 속성의 **클라이언트 컴퓨터 통신** 탭에서 **사이트 시스템 설정**이 **HTTP 또는 HTTPS**가 되도록 구성하고 **사용 가능한 경우 PKI 클라이언트 인증서(클라이언트 인증 기능) 사용**을 선택합니다.  자세한 내용은 [System Center Configuration Manager에서 보안 구성](../../../core/plan-design/security/configure-security.md) 문서에서 [클라이언트 PKI 인증서의 설정 구성](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) 섹션을 참조하세요.  

3.  클라이언트 인증서에 대해 PKI 롤아웃을 시험합니다. 배포 예는 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) 문서에서 *Windows 컴퓨터용 클라이언트 인증서 배포* 섹션을 참조하세요.  

4.  클라이언트 강제 설치 방법을 사용하여 클라이언트를 설치합니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) 문서에서 [클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush) 섹션을 참조하세요.  

5.  Configuration Manager 콘솔에서 보고서와 정보를 사용하여 클라이언트 배포 및 상태를 모니터링합니다.  

6.  **자산 및 호환성** 작업 영역의 **장치** 노드에서 **클라이언트 인증서** 열을 확인하여 클라이언트 PKI 인증서를 사용하는 클라이언트 수를 추적합니다.  

     또한 Configuration Manager HTTPS 준비 평가 도구(**cmHttpsReadiness.exe**)를 컴퓨터에 배포하고 보고서를 사용하면 Configuration Manager를 통해 클라이언트 PKI 인증서를 사용할 수 있는 컴퓨터 수를 확인할 수 있습니다.  

    > [!NOTE]  
    >  Configuration Manager 클라이언트가 설치되면 **cmHttpsReadiness.exe** 도구가 *%windir%***\CCM** 폴더에 설치됩니다. 클라이언트에서 이 도구를 실행할 때 다음 옵션을 지정할 수 있습니다.  
    >   
    >  -   /Store:&lt;이름\>  
    > -   /Issuers:&lt;목록\>  
    > -   /Criteria:&lt;조건\>  
    > -   /SelectFirstCert  
    >   
    >  이러한 옵션은 **CCMCERTSTORE**, **CCMCERTISSUERS**, **CCMCERTSEL**및 **CCMFIRSTCERT** Client.msi 속성에 각각 매핑됩니다. 이러한 옵션에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

7.  충분한 클라이언트가 자체 클라이언트 PKI 인증서를 HTTP를 통한 인증에 성공적으로 사용하고 있다고 확신할 경우 다음 단계를 따르세요.  

    1.  PKI 웹 서버 인증서를 사이트에 대한 추가 관리 지점을 실행할 구성원 서버에 배포하고 IIS에서 이 인증서를 구성합니다. 자세한 내용은 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) 문서의 *IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포* 섹션을 참조하세요.  

    2.  이 서버에 관리 지점 역할을 설치하고 **HTTPS** 에 대한 관리 지점 속성에서 **클라이언트 연결**옵션을 구성합니다.  

8.  PKI 인증서를 보유한 클라이언트에서 HTTPS를 통해 새 관리 지점을 사용하는지 모니터링 및 확인합니다. 이 사항을 확인하려면 IIS 로깅 또는 성능 카운터를 사용하면 됩니다.  

9. HTTPS 클라이언트 연결을 사용하도록 다른 사이트 시스템 역할을 다시 구성합니다. 인터넷의 클라이언트를 관리하려면 사이트 시스템에 인터넷 FQDN이 있는지 확인하고 각 관리 지점 및 배포 지점에서 인터넷의 클라이언트 연결을 허용하도록 구성합니다.  

    > [!IMPORTANT]  
    >  사이트 시스템 역할에서 인터넷의 연결을 허용하도록 설정하기 전에 인터넷 기반 클라이언트 관리에 대한 계획 정보 및 필수 구성 요소를 검토하세요. 자세한 내용은 [System Center Configuration Manager에서 끝점 간의 통신](../../../core/plan-design/hierarchy/communications-between-endpoints.md)을 참조하세요.  

10. PKI 인증서 롤아웃을 IIS를 실행하는 사이트 시스템 및 클라이언트에 대해 확장하고 사이트 시스템 역할을 HTTPS 클라이언트 연결 및 인터넷 연결에 대해 필요에 따라 설정합니다.  

11. 최상의 보안 구현: 모든 클라이언트에서 인증 및 암호화에 클라이언트 PKI 인증서를 사용하고 있다고 확신할 경우 HTTPS만 사용하도록 사이트 속성을 변경합니다.  

 이 계획에 따라 PKI 인증서를 단계적으로 채택하면, 즉 먼저 HTTP를 통한 인증에만 사용하고 그다음에는 HTTPS를 통한 인증 및 암호화에 사용하면 관리되지 않는 클라이언트가 발생할 위험성은 줄어듭니다. 또한 Configuration Manager에서 지원하는 최상의 보안으로 이점을 얻을 수 있습니다.  

##  <a name="BKMK_PlanningForRTK"></a> 신뢰할 수 있는 루트 키 계획  
Configuration Manager의 신뢰할 수 있는 루트 키에서 제공하는 메커니즘을 통해 Configuration Manager 클라이언트가 사이트 시스템이 해당 계층 구조에 속하는지 확인할 수 있습니다. 모든 사이트 서버는 다른 사이트와 통신하기 위한 사이트 교환 키를 생성합니다. 계층 내 최상위 사이트의 사이트 교환 키는 신뢰할 수 있는 루트 키라고 합니다.  

Configuration Manager에 있는 신뢰할 수 있는 루트 키의 기능은 신뢰할 수 있는 루트 키의 개인 키에서 서명된 모든 항목은 계층 내 하부 수준에서도 신뢰할 수 있다는 점에서 공개 키 인프라의 루트 인증서와 유사합니다. 예를 들어, 신뢰할 수 있는 루트 키 쌍의 개인 키로 관리 지점 인증서를 서명하고 신뢰할 수 있는 루트 키 쌍의 공개 키 사본을 클라이언트에서 사용할 수 있도록 설정하면 클라이언트는 자체 계층 구조에 있는 관리 지점과 자체 계층 구조에 없는 관리 지점을 서로 구별할 수 있습니다. 클라이언트에서는 WMI(Windows Management Instrumentation)를 사용하여 신뢰할 수 있는 루트 키 사본을 **root\ccm\locationservices** 네임스페이스에 저장합니다.  

클라이언트는 다음 두 가지 메커니즘을 통해 신뢰할 수 있는 루트 키의 공개 사본을 자동으로 검색할 수 있습니다.  

-   Active Directory 스키마는 Configuration Manager에 대해 확장되고, 사이트는 Active Directory Domain Services에 게시되며, 클라이언트는 글로벌 카탈로그 서버에서 이 사이트 정보를 검색할 수 있습니다.  

-   클라이언트 강제 설치를 사용하여 클라이언트가 설치됩니다.  

클라이언트에서 이러한 메커니즘 중 하나를 사용하여 신뢰할 수 있는 루트 키를 검색할 수 없는 경우 해당 클라이언트는 통신을 수행하는 첫 번째 관리 지점에서 제공되는 신뢰할 수 있는 루트 키를 신뢰합니다. 이 시나리오에서 클라이언트는 공격자의 관리 지점으로 잘못 연결될 수도 있으며 이 경우 클라이언트는 허위 관리 지점의 정책을 수신하게 됩니다. 이러한 방식의 공격은 노련한 공격자가 자주 이용하게 되며 클라이언트가 유효한 관리 지점에서 신뢰할 수 있는 루트 키를 검색하기 전 제한된 시간 안에만 발생하기 마련입니다. 그러나 신뢰할 수 있는 루트 키를 사용하여 클라이언트를 사전 프로비전하면 클라이언트를 허위 관리 지점으로 유도하는 이러한 공격을 방지할 수 있습니다.  

다음 절차를 사용하여 사전 프로비전을 수행하고 Configuration Manager 클라이언트에 대해 신뢰할 수 있는 루트 키를 확인합니다.  

-   파일을 사용하여 신뢰할 수 있는 루트 키로 클라이언트를 사전 프로비전합니다.  

-   파일을 사용하지 않고 신뢰할 수 있는 루트 키로 클라이언트를 사전 프로비전합니다.  

-   클라이언트에서 신뢰할 수 있는 루트 키를 확인합니다.  

> [!NOTE]  
>  클라이언트가 Active Directory Domain Services에서 신뢰할 수 있는 루트 키를 가져올 수 있거나 클라이언트 강제를 사용하여 설치된 경우 신뢰할 수 있는 루트 키를 사용하여 클라이언트를 사전 프로비전할 필요가 없습니다. 또한 클라이언트에서 관리 지점에 대해 HTTPS 통신을 사용할 경우 트러스트는 PKI 인증서를 통해 설정되므로 클라이언트를 사전 프로비전할 필요가 없습니다.  

CCMSetup.exe를 통해 Client.msi 속성 **RESETKEYINFORMATION = TRUE**를 사용하여 클라이언트에서 신뢰할 수 있는 루트 키를 제거할 수 있습니다. 신뢰할 수 있는 루트 키를 교체하려면 클라이언트를 새 신뢰할 수 있는 루트 키와 함께 다시 설치하세요. 예를 들어 클라이언트 강제 설치를 사용하거나 CCMSetup.exe를 사용해 Client.msi **SMSPublicRootKey** 속성을 지정하면 됩니다.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-by-using-a-file"></a>파일을 사용하여 신뢰할 수 있는 루트 키로 클라이언트를 사전 프로비전하려면  

1.  텍스트 편집기에서 *&lt;Configuration Manager 디렉터리\>***\bin\mobileclient.tcf** 파일을 엽니다.  

2.  **SMSPublicRootKey=** 항목을 찾아 해당 행에서 키를 복사한 다음 아무 내용도 변경하지 않고 파일을 닫습니다.  

3.  새 텍스트 파일을 만들고 mobileclient.tcf 파일에서 복사한 키 정보를 붙여넣습니다.  

4.  모든 컴퓨터에서 액세스할 수 있지만 파일이 무단 변경되지 않도록 보호되는 위치에 파일을 저장합니다.  

5.  Client.msi 속성이 허용되는 설치 방법으로 클라이언트를 설치하고 Client.msi 속성 **SMSROOTKEYPATH=***&lt;전체 경로 및 파일 이름\>*을 지정합니다.  

    > [!IMPORTANT]  
    >  클라이언트 설치 중 추가 보안을 위해 신뢰할 수 있는 루트 키를 지정하는 경우에는 Client.msi 속성 **SMSSITECODE=&lt;사이트 코드\>**를 사용하여 사이트 코드도 지정해야 합니다.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-without-using-a-file"></a>파일을 사용하지 않고 신뢰할 수 있는 루트 키로 클라이언트를 사전 프로비전하려면  

1.  텍스트 편집기에서 *&lt;Configuration Manager 디렉터리\>***\bin\mobileclient.tcf** 파일을 엽니다.  

2.  SMSPublicRootKey= 항목을 찾아 해당 행에서 키를 메모하거나 클립보드에 복사한 다음 아무 내용도 변경하지 않고 파일을 닫습니다.  

3.  Client.msi 속성이 허용되는 설치 방법으로 클라이언트를 설치하고 Client.msi 속성 **SMSPublicRootKey=***&lt;키\>*를 지정합니다. 여기서 *&lt;키\>*는 mobileclient.tcf에서 복사한 문자열입니다.  

    > [!IMPORTANT]  
    >  클라이언트 설치 중 추가 보안을 위해 신뢰할 수 있는 루트 키를 지정하는 경우에는 Client.msi 속성 **SMSSITECODE=&lt;사이트 코드\>**를 사용하여 사이트 코드도 지정해야 합니다.  

#### <a name="to-verify-the-trusted-root-key-on-a-client"></a>클라이언트에서 신뢰할 수 있는 루트 키를 확인하려면  

1.  **시작** 메뉴에서 **실행**을 선택하고 **Wbemtest**를 입력합니다.  

2.  **WMI(Windows Management Instrumentation) Tester** 대화 상자에서 **연결**을 선택합니다.  

3.  **연결** 대화 상자의 **네임스페이스** 상자에 **root\ccm\locationservices**를 입력한 다음 **연결**을 선택합니다.  

4.  **WMI(Windows Management Instrumentation) Tester** 대화 상자의 **IWbemServices** 섹션에서 **Enum 클래스**를 선택합니다.  

5.  **Superclass 정보** 대화 상자에서 **하위 항목 포함**을 선택한 다음 **확인**을 선택합니다.  

6.  **쿼리 결과** 창에서 목록 끝으로 스크롤한 다음 **TrustedRootKey ()**를 두 번 클릭합니다.  

7.  **TrustedRootKey용 개체 편집기** 대화 상자에서 **인스턴스**를 선택합니다.  

8.  **TrustedRootKey**의 인스턴스가 표시되는 새 **쿼리 결과** 창에서 **TrustedRootKey=@**을 두 번 클릭합니다.  

9. **TrustedRootKey=@용 개체 편집기** 대화 상자의 **속성** 섹션에서 **TrustedRootKey CIM_STRING**으로 스크롤합니다. 오른쪽 열에 있는 문자열이 신뢰할 수 있는 루트 키입니다. 이 문자열이 *&lt;Configuration Manager 디렉터리\>***\bin\mobileclient.tcf** 파일의 **SMSPublicRootKey** 값과 일치하는지 확인합니다.  

##  <a name="BKMK_PlanningForSigningEncryption"></a> 서명 및 암호화 계획  
 모든 클라이언트 통신에 대해 PKI 인증서를 사용하는 경우 클라이언트 데이터 통신의 보안을 위해 서명 및 암호화를 계획할 필요가 없습니다. 그러나 IIS를 실행하는 사이트 시스템에서 HTTP 클라이언트 연결을 허용하도록 설정할 경우 사이트에 대한 클라이언트 통신을 보호할 방법을 결정해야 합니다.  

 클라이언트가 관리 지점에 보내는 데이터를 보호하려면 해당 데이터를 서명해야 합니다. 또한 HTTP를 사용하는 서명된 모든 클라이언트 데이터는 SHA-256 알고리즘을 사용하여 서명되도록 할 수 있습니다. 이 설정이 더 안전하기는 하지만, 모든 클라이언트가 SHA-256을 지원하는 경우가 아니면 이 옵션을 사용하도록 설정하지 마세요. 대부분의 운영 체제는 기본적으로 SHA-256을 지원하지만 이전 버전 운영 체제의 경우에는 업데이트나 핫픽스를 설치해야 할 수도 있습니다. 예를 들어 Windows Server 2003 SP2를 실행하는 컴퓨터는 [기술 자료 문서 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666)에 언급된 핫픽스를 설치해야 합니다.  

 서명은 데이터 변조를 방지할 수 있는 반면, 암호화는 정보 노출로부터 데이터를 방지하는 데 도움이 됩니다. 클라이언트가 사이트의 관리 지점으로 보내는 인벤토리 데이터 및 상태 메시지에 3DES 암호화를 사용할 수 있습니다. 이 옵션을 지원하기 위해 클라이언트에 설치해야 할 업데이트는 없지만 클라이언트 및 관리 지점에서 암호화 및 암호 해독을 수행하는 데 필요한 추가 CPU 사용량을 고려해야 합니다.  

 서명 및 암호화 설정을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보안 구성](../../../core/plan-design/security/configure-security.md) 문서의 [서명 및 암호화 구성](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) 섹션을 참조하세요.  

##  <a name="BKMK_PlanningForRBA"></a> 역할 기반 관리 계획  
 자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../../core/understand/fundamentals-of-role-based-administration.md)을 참조하세요.  

### <a name="see-also"></a>참고 항목
[System Center Configuration Manager에 대한 암호화 제어 기술 참조](../../../protect/deploy-use/cryptographic-controls-technical-reference.md)  

