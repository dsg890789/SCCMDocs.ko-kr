---
title: CMG 인증서
description: 클라우드 관리 게이트웨이와 함께 사용할 다양한 디지털 인증서에 대해 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 11/27/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 71eaa409-b955-45d6-8309-26bf3b3b0911
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9368bedd80171077767ead54763abede2381c909
ms.sourcegitcommit: bfb8a17f60dcb9905e739045a5141ae45613fa2c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66198447"
---
# <a name="certificates-for-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 인증서

*적용 대상: System Center Configuration Manager(현재 분기)*

CMG(클라우드 관리 게이트웨이)를 통해 인터넷에서 클라이언트를 관리하는 데 사용하는 시나리오에 따라 다음 디지털 인증서 중 하나 이상이 필요합니다.  

- [CMG 서버 인증 인증서](#bkmk_serverauth)  
    - [클라이언트에서 신뢰할 수 있는 CMG 루트 인증서](#bkmk_cmgroot)  
    - [공용 공급자가 발급한 서버 인증 인증서](#bkmk_serverauthpublic)  
    - [엔터프라이즈 PKI에서 발급한 서버 인증 인증서](#bkmk_serverauthpki)  

- [Azure 관리 인증서](#bkmk_azuremgmt)  

- [클라이언트 인증 인증서](#bkmk_clientauth)  
    - [CMG에서 신뢰할 수 있는 클라이언트 루트 인증서](#bkmk_clientroot)  

- [HTTPS에 대한 관리 지점 사용](#bkmk_mphttps)  


다양한 시나리오에 대한 자세한 내용은 [클라우드 관리 게이트웨이에 대한 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.


### <a name="general-information"></a>일반 정보
<!--SCCMDocs issue #779-->
클라우드 관리 게이트웨이의 인증서는 다음 구성을 지원합니다.  

- 2048 또는 4096비트 키 길이

- 버전 1710부터는 인증서 개인 키를 위한 키 스토리지 공급자를 지원합니다. 자세한 내용은 [CNG 인증서 개요](/sccm/core/plan-design/network/cng-certificates-overview)를 참조하세요.  

- 버전 1802부터 다음 정책을 사용하여 Windows를 구성합니다. **시스템 암호화: 암호화, 해시, 서명에 FIPS 규격 알고리즘 사용**  

- 버전 1802부터는 **TLS 1.2**를 지원합니다. 자세한 내용은 [암호화 컨트롤 기술 참조](/sccm/core/plan-design/security/cryptographic-controls-technical-reference#about-ssl-vulnerabilities)를 참조하세요.  



## <a name="bkmk_serverauth"></a> CMG 서버 인증 인증서

*이 인증서는 모든 시나리오에서 필요합니다.*

Configuration Manager 콘솔에서 CMG를 만들 때 이 인증서를 제공합니다.

CMG는 인터넷 기반 클라이언트에서 연결하는 HTTPS 서비스를 만듭니다. 서버에서 보안 채널을 구축하려면 서버 인증 인증서가 필요합니다. 이 목적을 위해 인증서를 공용 공급자로부터 구입하거나 PKI(공개 키 인프라)에서 획득합니다. 자세한 내용은 [클라이언트에서 신뢰할 수 있는 CMG 루트 인증서](#bkmk_cmgroot)를 참조하세요.

 > [!TIP]
 > 이 인증서에는 Azure에서 서비스를 식별하기 위해 전역적으로 고유한 이름을 필요합니다. 인증서를 요청하기 전에 원하는 Azure 도메인 이름이 고유한지 확인합니다. 예를 들어 *GraniteFalls.CloudApp.Net*과 같습니다. [Microsoft Azure Portal](https://portal.azure.com)에 로그온합니다. **리소스 만들기**를 선택하고, **컴퓨팅** 범주를 선택한 다음, **클라우드 서비스**를 선택합니다. **DNS 이름** 필드에서 원하는 접두사를 입력합니다(예: *GraniteFalls*). 인터페이스에는 도메인 이름을 사용할 수 있는지, 아니면 다른 서비스에서 이미 사용 중인지 여부가 표시됩니다. 포털에서 서비스를 만들지 말고, 이 프로세스를 사용하여 이름 가용성을 확인하세요. 
  
 > [!TIP]
 > CMG도 클라우드 배포 지점으로 사용하도록 설정될 경우 선택한 CMG 서비스 이름이 고유한 Azure Storage 계정 이름인지도 확인하세요. 예를 들면 *GraniteFalls*입니다. [Microsoft Azure Portal](https://portal.azure.com)에 로그온합니다. **리소스 만들기**를 선택하고 **스토리지** 범주를 선택한 다음, **스토리지 계정 - Blob, 파일, 테이블, 큐**를 선택합니다. **만들기**를 클릭하고 **인스턴스 정보** 아래에 CMG 서비스에 대해 선택한 것과 동일한 이름을 입력합니다(예: *GraniteFalls*). 인터페이스에는 스토리지 계정 이름을 사용할 수 있는지, 아니면 다른 서비스에서 이미 사용 중인지 여부가 표시됩니다. 포털에서 스토리지 계정을 만들지 말고, 이 프로세스를 사용하여 이름 가용성만 확인하세요. CMG 클라우드 서비스 이름이 고유하지만, 스토리지 계정 이름이 고유하지 않은 경우 프로비전에 실패합니다.
 
 > [!NOTE]
 > 1802 버전부터 CMG 서버 인증 인증서는 와일드카드를 지원합니다. 일부 인증 기관은 호스트 이름에 와일드카드 문자를 사용하는 인증서를 발행합니다. 예를 들어 **\*.contoso.com**과 같습니다. 일부 조직에서는 PKI를 간소화하고 유지 관리 비용을 절약하기 위해 와일드카드 인증서를 사용합니다.<!--491233-->  
 > 
 > CMG에서 와일드카드 인증서를 사용하는 방법에 대한 자세한 내용은 [CMG 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#set-up-a-cmg)을 참조하세요.<!--SCCMDocs issue #565-->  


### <a name="bkmk_cmgroot"></a> 클라이언트에서 신뢰할 수 있는 CMG 루트 인증서

클라이언트는 CMG 서버 인증 인증서를 신뢰해야 합니다. 이 신뢰를 수행하는 데는 두 가지 방법이 있습니다. 

- 공용 및 전역 신뢰할 수 있는 인증서 공급자의 인증서를 사용합니다. 예를 들어 DigiCert, VeriSign 또는 Thawte가 있지만, 이에 국한되지는 않습니다. Windows 클라이언트에는 이러한 공급자의 신뢰할 수 있는 루트 CA(인증 기관)가 포함됩니다. 이러한 공급자 중 하나에서 발급된 서버 인증 인증서를 사용하면 클라이언트에서 이 인증서를 자동으로 신뢰합니다.  

- PKI(공개 키 인프라)의 엔터프라이즈 CA에서 발급한 인증서를 사용합니다. 대부분의 엔터프라이즈 PKI 구현에서는 신뢰할 수 있는 루트 CA를 Windows 클라이언트에 추가합니다. 예를 들어 그룹 정책과 함께 Active Directory 인증서 서비스를 사용합니다. 클라이언트에서 자동으로 신뢰하지 않는 CA에서 CMG 서버 인증 인증서를 발급하는 경우 신뢰할 수 있는 루트 CA 인증서를 인터넷 기반 클라이언트에 추가합니다.  

    - Configuration Manager 인증서 프로필을 사용하여 클라이언트에 인증서를 프로비전할 수도 있습니다. 자세한 내용은 [인증서 프로필 소개](/sccm/protect/deploy-use/introduction-to-certificate-profiles)를 참조하세요.  

> [!Note]  
> 버전 1806부터는 CMG를 만들 경우 설정 페이지에서 신뢰할 수 있는 루트 인증서를 더 이상 제공할 필요가 없습니다. 이 인증서는 클라이언트 인증용 Azure AD(Azure Active Directory)를 사용할 때 필요하지 않지만 마법사에서는 필요합니다. PKI 클라이언트 인증 인증서를 사용하는 경우 여전히 신뢰할 수 있는 루트 인증서를 CMG에 추가해야 합니다.<!--SCCMDocs-pr issue #2872-->  


### <a name="bkmk_serverauthpublic"></a> 공용 공급자가 발급한 서버 인증 인증서

해당 도메인을 Microsoft에서 소유하므로 타사 인증서 공급자는 CloudApp.net에 대한 인증서를 만들 수 없습니다. 소유하는 도메인에 대해 발급된 인증서만 가져올 수 있습니다. 타사 공급자에서 발급한 인증서를 가져오는 주된 이유는 클라이언트에서 이미 해당 공급자의 루트 인증서를 신뢰하기 때문입니다.

다음 프로세스를 사용하여 DNS 별칭을 만듭니다.

1. 조직의 공용 DNS에 CNAME(정식 이름) 레코드를 만듭니다. 이 레코드는 CMG에 대한 별칭을 공용 인증서에서 사용하는 친숙한 이름으로 만듭니다.

    예를 들어 Contoso는 Azure에서 **GraniteFalls.CloudApp.Net**이 되는 **GraniteFalls**라는 CMG 이름을 지정합니다. Contoso의 공용 DNS contoso.com 네임스페이스에서 DNS 관리자는 실제 호스트 이름인 **GraniteFalls.CloudApp.net**에 대해 **GraniteFalls.Contoso.com**이라는 새 CNAME 레코드를 만듭니다.  

2. CNAME 별칭의 CN(일반 이름)을 사용하여 공용 공급자의 서버 인증 인증서를 요청합니다.
예를 들어 Contoso는 인증서 CN에 **GraniteFalls.Contoso.com**을 사용합니다.  

3. 이 인증서를 사용하여 Configuration Manager 콘솔에서 CMG를 만듭니다. 클라우드 관리 게이트웨이 만들기 마법사의 **설정** 페이지에서 다음을 수행합니다.   

    - **인증서 파일**에서 이 클라우드 서비스에 대한 서버 인증서를 추가하면, 마법사에서 인증서 CN의 호스트 이름을 서비스 이름으로 추출합니다.  

    - 그런 다음, Azure에 서비스를 만들기 위해 해당 호스트 이름을 서비스 FQDN으로 **cloudapp.net** 또는 **usgovcloudapp.net**(Azure US Government 클라우드)에 추가합니다.  

    - 예를 들어 Contoso에서 CMG를 만들면 Configuration Manager는 인증서 CN에서 **GraniteFalls** 호스트 이름을 추출합니다. Azure는 실제 서비스를 **GraniteFalls.CloudApp.net**으로 만듭니다.  

Configuration Manager에서 CMG 인스턴스를 만들면 인증서에 GraniteFalls.Contoso.com이 포함된 반면 Configuration Manager에서는 호스트 이름만 추출합니다 (예: GraniteFalls). Azure에서 클라우드 서비스를 만들 때 필요한 이 호스트 이름을 CloudApp.net에 추가합니다. Contoso.com이라는 도메인에 대한 DNS 네임스페이스의 CNAME 별칭은 이러한 두 개의 FQDN에 함께 매핑됩니다. Configuration Manager에서는 클라이언트에게 이 CMG에 액세스하기 위한 정책을 제공합니다. DNS 매핑은 해당 클라이언트가 Azure에서 서비스에 안전하게 액세스할 수 있도록 이 정책을 함께 연결합니다.<!--SCCMDocs issue #565-->  


### <a name="bkmk_serverauthpki"></a> 엔터프라이즈 PKI에서 발급한 서버 인증 인증서

클라우드 배포 지점과 마찬가지로 CMG에 대한 사용자 지정 SSL 인증서를 만듭니다. [클라우드 기반 배포 지점용 서비스 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012)에 대한 지침을 따르는 대신, 다음 작업은 다르게 수행하세요.

- 사용자 지정 웹 서버 인증서를 요청할 때 인증서의 일반 이름에 대해 FQDN을 제공합니다. 이 이름은 소유한 공용 도메인 이름이거나 cloudapp.net 도메인을 사용할 수 있습니다. 보유한 공용 도메인을 사용하는 경우 조직의 공용 DNS에서 DNS 별칭을 만들려면 위의 프로세스를 참조하세요.  

- CMG 웹 서버 인증서에 대해 cloudapp.net 공용 도메인을 사용하는 경우:  

    - Azure 공용 클라우드에서 **cloudapp.net**으로 끝나는 이름을 사용합니다.  

    - Azure US Government 클라우드에 대해 **usgovcloudapp.net**으로 끝나는 이름을 사용합니다.  



## <a name="bkmk_azuremgmt"></a> Azure 관리 인증서

*이 인증서는 클래식 서비스 배포에 필요하지만, Azure Resource Manager 배포에는 필요하지 않습니다.*

> [!Important]  
> 1810 버전부터 Azure의 클래식 서비스 배포는 Configuration Manager에서 사용되지 않습니다. 클라우드 관리 게이트웨이에 대해 Azure Resource Manager 배포를 사용하기 시작합니다. 자세한 내용은 [CMG 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager)을 참조하세요.

이 인증서는 Azure Portal 또는 Configuration Manager 콘솔에서 CMG를 만들 때 제공합니다.

Azure에서 CMG를 만들려면 먼저 Configuration Manager 서비스 연결 지점에서 Azure 구독을 인증해야 합니다. 클래식 서비스 배포를 사용하는 경우 이 인증에 Azure 관리 인증서를 사용합니다. Azure 관리자가 이 인증서를 구독에 업로드합니다. Configuration Manager 콘솔에서 CMG를 만들 때 이 인증서를 제공합니다.

관리 인증서를 업로드하는 방법에 대한 자세한 내용 및 지침은 Azure 설명서에서 다음 문서를 참조하세요.

- [클라우드 서비스 및 관리 인증서](https://docs.microsoft.com/azure/cloud-services/cloud-services-certs-create#what-are-management-certificates)  

- [Azure 서비스 관리 인증서 업로드](https://docs.microsoft.com/azure/azure-api-management-certs)  

> [!IMPORTANT]
> 관리 인증서와 연결된 구독 ID를 복사해야 합니다. 이는 Configuration Manager 콘솔에서 CMG를 만드는 데 사용합니다.



## <a name="bkmk_clientauth"></a> 클라이언트 인증 인증서

*이 인증서는 Azure AD(Azure Active Directory)에 가입하지 않은 Windows 7, Windows 8.1 및 Windows 10 디바이스를 실행하는 인터넷 기반 클라이언트에 필요합니다. CMG 연결 지점에도 필요합니다. Azure AD에 조인한 Windows 10 클라이언트에는 필요하지 않습니다.*

클라이언트는 이 인증서를 사용하여 CMG를 인증합니다. 하이브리드 또는 클라우드 도메인에 가입한 Windows 10 디바이스는 Azure AD를 사용하여 인증하므로 이 인증서가 필요하지 않습니다.

Configuration Manager의 컨텍스트 외부에서 이 인증서를 제공합니다. 예를 들어 Active Directory 인증서 서비스 및 그룹 정책을 사용하여 클라이언트 인증 인증서를 발급합니다. 자세한 내용은 [Windows 컴퓨터용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012)를 참조하세요.

CMG 연결 지점에서 클라이언트 요청을 HTTPS 관리 지점으로 안전하게 전달하려면 이 인증서가 필요합니다. Azure AD 또는 고급 HTTP를 사용하는 경우 이 인증서는 필요하지 않습니다. 자세한 내용은 [HTTPS에 대한 관리 지점 설정](#bkmk_mphttps)을 참조하세요.


### <a name="bkmk_clientroot"></a> CMG에서 신뢰할 수 있는 클라이언트 루트 인증서

*이 인증서는 클라이언트 인증 인증서를 사용할 때 필요합니다. 모든 클라이언트에서 Azure AD를 인증에 사용하는 경우 이 인증서는 필요하지 않습니다.* 

Configuration Manager 콘솔에서 CMG를 만들 때 이 인증서를 제공합니다.

CMG는 클라이언트 인증 인증서를 신뢰해야 합니다. 이 신뢰를 수행하려면 신뢰할 수 있는 루트 인증서 체인을 제공합니다. 두 개의 신뢰할 수 있는 루트 CA 및 네 개의 중간(하위) CA를 지정할 수 있습니다. 


#### <a name="export-the-client-certificates-trusted-root"></a>클라이언트 인증서의 신뢰할 수 있는 루트 내보내기

컴퓨터에 클라이언트 인증 인증서를 발급한 후 해당 컴퓨터에서 이 프로세스를 사용하여 신뢰할 수 있는 루트를 내보냅니다.

1.  [시작] 메뉴를 엽니다. "run"을 입력하여 [실행] 창을 엽니다. `mmc`를 엽니다.  

2.  [파일] 메뉴에서 **스냅인 추가/제거**를 선택합니다.  

3.  스냅인 추가/제거 대화 상자에서 **인증서**를 선택한 다음, **추가**를 선택합니다.  

    a. 인증서 스냅인 대화 상자에서 **컴퓨터 계정**을 선택한 다음, **다음**을 선택합니다.  

    b. 컴퓨터 선택 대화 상자에서 **로컬 컴퓨터**를 선택한 다음, **마침**을 선택합니다.  

    c. 스냅인 추가/제거 대화 상자에서 **확인**을 선택합니다.  

4.  **인증서**, **개인**을 차례로 펼치고 **인증서**를 선택합니다.  

5.  [용도]가 **클라이언트 인증**인 인증서를 선택합니다.  

    a. [작업] 메뉴에서 **열기**를 선택합니다.  

    b. **인증 경로** 탭으로 이동합니다.  

    c. 체인의 다음 인증서를 선택하고 **인증서 보기**를 선택합니다.  

6.  이 새 인증서 대화 상자에서 **세부 정보** 탭으로 이동합니다. **파일에 복사...** 를 선택합니다.  

7.  기본 인증서 형식인 **DER로 인코딩된 X.509 바이너리(.CER)** 를 사용하여 인증서 내보내기 마법사를 완료합니다. 내보낸 인증서의 이름과 위치를 적어 둡니다.  

8. 원래 클라이언트 인증 인증서의 인증서 경로에 있는 모든 인증서를 내보냅니다. 내보낸 인증서 중 중간 CA 및 신뢰할 수 있는 루트 CA에 해당하는 인증서를 적어 둡니다.  



## <a name="bkmk_mphttps"></a> HTTPS에 대한 관리 지점 사용

Configuration Manager의 컨텍스트 외부에서 이 인증서를 제공합니다. 예를 들어 Active Directory 인증서 서비스 및 그룹 정책을 사용하여 웹 서버 인증서를 발급합니다. 자세한 내용은 [PKI 인증 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements) 및 [IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012)를 참조하세요.


- 1710 버전에서 클라이언트 인증 인증서를 사용하여 온-프레미스 ID가 있는 기존 클라이언트를 관리하는 경우 이 인증서를 권장하지만 반드시 필요한 것은 아닙니다. Azure AD에 가입한 Windows 10 클라이언트를 관리할 때 이 인증서가 관리 지점에 필요합니다.

- 1802 버전에서 이 인증서는 모든 시나리오에서 필요합니다. CMG에 대해 사용할 수 있는 관리 지점만 HTTPS여야 합니다. 이 동작이 변경되면 Azure AD 토큰 기반 인증에 대한 지원이 개선됩니다.  

- 버전 1806부터 **HTTP 사이트 시스템에 대해 Configuration Manager가 생성한 인증서 사용**이라는 사이트 옵션을 사용하는 경우 관리 지점이 HTTP가 될 수 있습니다. 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.

### <a name="management-point-client-connection-mode-summary"></a>관리 지점 클라이언트 연결 모드 요약
다음 표에는 클라이언트 및 사이트 버전의 유형에 따라 관리 지점에 HTTP 또는 HTTPS가 필요한지 여부가 요약되어 있습니다.

#### <a name="for-internet-based-clients-communicating-with-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이와 통신하는 인터넷 기반 클라이언트인 경우
다음 클라이언트 연결 모드로 CMG에서 들어오는 연결을 허용하도록 온-프레미스 관리 지점을 구성합니다.

| 클라이언트 유형   | 1710        | 1802        | 1806        | 1810        |
|------------------|-------------|-------------|-------------|-------------|
| 작업 그룹        | HTTP, HTTPS | HTTPS       | E-HTTP<sup>[참고 1](#bkmk_note1)</sup>, HTTPS | E-HTTP<sup>[참고 1](#bkmk_note1)</sup>, HTTPS |
| AD 도메인 조인 | HTTP, HTTPS | HTTPS       | E-HTTP<sup>[참고 1](#bkmk_note1)</sup>, HTTPS | E-HTTP<sup>[참고 1](#bkmk_note1)</sup>, HTTPS |
| Azure AD 조인  | HTTPS       | HTTPS       | E-HTTP, HTTPS | E-HTTP, HTTPS |
| 하이브리드 조인    | HTTP, HTTPS | HTTPS       | E-HTTP, HTTPS | E-HTTP, HTTPS |

<a name="bkmk_note1"></a> 

> [!Note]  
> **참고 1**: 이 구성에서는 클라이언트에 [클라이언트 인증 인증서](#bkmk_clientauth)를 요구하며 디바이스 중심 시나리오만 지원합니다.  

#### <a name="for-on-premises-clients-communicating-with-the-on-premises-management-point"></a>온-프레미스 관리 지점과 통신하는 온-프레미스 클라이언트인 경우
다음 클라이언트 연결 모드로 온-프레미스 관리 지점을 구성합니다.

| 클라이언트 유형   | 1710        | 1802        | 1806        | 1810        |
|------------------|-------------|-------------|-------------|-------------|
| 작업 그룹        | HTTP, HTTPS | HTTP, HTTPS | HTTP, HTTPS | HTTP, HTTPS |
| AD 도메인 조인 | HTTP, HTTPS | HTTP, HTTPS | HTTP, HTTPS | HTTP, HTTPS |
| Azure AD 조인  | HTTPS       | HTTPS       | HTTPS       | HTTPS       |
| 하이브리드 조인    | HTTP, HTTPS | HTTP, HTTPS | HTTP, HTTPS | HTTP, HTTPS |

> [!Note]  
> 버전 1806에서는 AD 도메인 조인 클라이언트가 HTTP 또는 HTTPS 관리 지점과 통신하는 디바이스 및 사용자 중심 시나리오를 모두 지원합니다.  
> 
> Azure AD 조인 및 하이브리드 조인 클라이언트는 디바이스 중심 시나리오의 경우 HTTP를 통해 통신할 수 있지만, 사용자 중심 시나리오를 사용하려면 E-HTTP 또는 HTTPS가 필요합니다. 그렇지 않으면 작업 그룹 클라이언트와 동일하게 작동합니다.  


#### <a name="legend-of-terms"></a>용어 범례
- *작업 그룹*: 디바이스가 도메인 또는 Azure AD에 조인되어 있지 않지만 [클라이언트 인증 인증서](#bkmk_clientauth)를 보유하고 있습니다.  
- *AD 도메인 조인*: 디바이스를 온-프레미스 Active Directory 도메인에 조인합니다.  
- *Azure AD 조인*: 클라우드 도메인 조인이라고도 하며, 디바이스를 Azure Active Directory 테넌트에 조인합니다.  
- *하이브리드 조인*: 디바이스를 Active Directory 도메인과 Azure AD 테넌트 모두에 조인합니다.  
- *HTTP*: 관리 지점 속성에서 클라이언트 연결을 **HTTP**로 설정합니다.  
- *HTTPS*: 관리 지점 속성에서 클라이언트 연결을 **HTTPS**로 설정합니다.  
- *E-HTTP*: 사이트 속성의 [클라이언트 컴퓨터 통신] 탭에서 사이트 시스템 설정을 **HTTPS 또는 HTTP**로 설정하고 **HTTP 사이트 시스템에 대한 Configuration Manager 생성 인증서 사용** 옵션을 사용하도록 설정합니다. HTTP에 대한 관리 지점을 구성하고, HTTP 관리 지점이 HTTP 및 HTTPS 통신(토큰 인증 시나리오)에 대해 준비되었습니다.   



## <a name="next-steps"></a>다음 단계

- [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)  

- [클라우드 관리 게이트웨이에 대한 FAQ](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)  

- [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)  
