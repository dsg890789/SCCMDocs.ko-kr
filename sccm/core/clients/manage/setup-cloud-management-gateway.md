---
title: "클라우드 관리 게이트웨이 설정 | Microsoft 문서"
description: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.openlocfilehash: 84b617b3e83636ab4578174ef40e786dcf1178cd
ms.sourcegitcommit: 06aef618f72c700f8a716a43fb8eedf97c62a72b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2017
---
# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Configuration Manager용 클라우드 관리 게이트웨이 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

1610 버전부터는 Configuration Manager에서 클라우드 관리 게이트웨이를 설정하는 프로세스에 다음 단계가 포함됩니다.

## <a name="step-1-configure-required-certificates"></a>1단계: 필요한 인증서 구성

> [!TIP]  
> 인증서를 요청하기 전에 원하는 Azure 도메인 이름 (예: GraniteFalls.CloudApp.Net)이 고유한지 확인합니다. [Microsoft Azure Portal](https://manage.windowsazure.com)에서 이 로그인을 수행하려면 **새로 만들기**를 클릭하고, **Cloud Service** 및 **사용자 지정 만들기**를 차례로 선택합니다. **URL** 필드에서 원하는 도메인 이름을 입력합니다(서비스를 만들려면 확인 표시를 클릭하지 않음). 포털은 사용할 수 있는 도메인 이름인지 아니면 다른 서비스에서 이미 사용 중인지를 반영합니다.

## <a name="option-1-preferred---use-the-server-authentication-certificate-from-a-public-and-globally-trusted-certificate-provider-like-verisign"></a>옵션 1(기본 설정) - 공용 및 전 세계적으로 신뢰할 수 있는 인증서 공급자(예: VeriSign)의 서버 인증 인증서를 사용합니다.

이 방법을 사용하면 클라이언트가 인증서를 자동으로 신뢰하므로 직접 사용자 지정 SSL 인증서를 만들 필요가 없습니다.

1. 조직의 공용 DNS(도메인 이름 서비스)에 CNAME(정식 이름 레코드)을 만들어 클라우드 관리 게이트웨이 서비스의 별칭을 공용 인증서에 사용할 친숙한 이름으로 지정합니다.
예를 들어 Contoso는 Azure에서 **GraniteFalls.CloudApp.Net**인 클라우드 관리 게이트웨이 서비스 **GraniteFalls**의 이름을 지정합니다. Contoso의 공용 DNS contoso.com 네임스페이스에서 DNS 관리자는 실제 호스트 이름인 **GraniteFalls.CloudApp.net**에 대한 새 CNAME 레코드인 **GraniteFalls.Contoso.com**을 만듭니다.
2. 그런 다음 CNAME 별칭의 CN(일반 이름)을 사용하여 공용 공급자에서 서버 인증 인증서를 요청합니다.
예를 들어 Contoso는 인증서 CN에 **GraniteFalls.Contoso.com**을 사용합니다.
3. 이 인증서를 사용하여 Configuration Manager 콘솔에서 클라우드 관리 게이트웨이 서비스를 만듭니다.
    - 클라우드 관리 게이트웨이 만들기 마법사의 **설정** 페이지에서 이 클라우드 서비스에 대한 서버 인증서를 추가하면(**인증서 파일**에서) 마법사가 인증서 CN에서 호스트 이름을 서비스 이름으로 추출한 다음 Azure에서 서비스를 만들기 위한 서비스 FQDN으로 **cloudapp.net**(또는 Azure US Government 클라우드의 경우 **usgovcloudapp.net**)에 추가합니다.
예를 들어 Contoso에서 클라우드 관리 게이트웨이를 만들 때 인증서 CN에서 호스트 이름 **GraniteFalls**가 추출되므로 Azure의 실제 서비스가 **GraniteFalls.CloudApp.net**으로 만들어집니다.

### <a name="option-2---create-a-custom-ssl-certificate-for-cloud-management-gateway-in-the-same-way-as-for-a-cloud-based-distribution-point"></a>옵션 2 - 클라우드 기반 배포 지점과 동일한 방식으로 클라우드 관리 게이트웨이에 대한 사용자 지정 SSL 인증서를 만듭니다.

클라우드 기반 배포 지점에 대해 수행하는 방법과 동일하게 클라우드 관리 게이트웨이용으로 사용자 지정 SSL 인증서를 만들 수 있습니다. [클라우드 기반 배포 지점용 서비스 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에 대한 지침을 따르되 다음 사항은 다르게 수행합니다.

- 사용자 지정 웹 서버 인증서를 요청할 때는 Azure 공용 클라우드의 클라우드 관리 게이트웨이를 사용하려는 경우 **cloudapp.net**으로 끝나는 인증서 일반 이름의 FQDN을 입력하고, Azure 정부 클라우드를 사용하려는 경우 **usgovcloudapp.net**으로 끝나는 인증서 일반 이름의 FQDN을 입력합니다.


## <a name="step-2-export-the-client-certificates-root"></a>2단계: 클라이언트 인증서의 루트 내보내기

네트워크에서 사용되는 클라이언트 인증서의 루트를 내보내는 가장 쉬운 방법은 도메인에 가입된 컴퓨터 중 인증서가 있는 컴퓨터에서 클라이언트 인증서를 열어 해당 인증서를 복사하는 것입니다.

> [!NOTE] 
>
> 클라우드 관리 게이트웨이를 사용하여 관리하려는 컴퓨터 및 클라우드 관리 게이트웨이 연결점을 호스트하는 사이트 시스템 서버에는 클라이언트 인증서가 필요합니다. 이러한 컴퓨터 중 하나에 클라이언트 인증서를 추가해야 하는 경우 [Windows 컴퓨터용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012)를 참조하세요.

1.  실행 창에 **mmc**를 입력하고 Return 키를 누릅니다.

2.  파일 메뉴에서 **스냅인 추가/제거**를 선택합니다.

3.  스냅인 추가/제거 대화 상자에서 **인증서** > **추가&gt;** > **컴퓨터 계정** > **다음** > **로컬 컴퓨터** > **마침**을 선택합니다. 

4.  **인증서** &gt; **개인** &gt; **인증서**로 이동합니다.

5.  컴퓨터에서 클라이언트 인증에 사용할 인증서를 두 번 클릭하고 인증 경로 탭을 선택한 다음 경로 상단에 있는 루트 기관을 두 번 클릭합니다.

6.  세부 정보 탭에서 **파일에 복사...**를 선택합니다.

7.  기본 인증서 형식을 사용하여 인증서 내보내기 마법사를 완료합니다. 만든 루트 인증서의 이름과 위치를 적어 둡니다. 이러한 정보는 [이후 단계](#step-4-set-up-cloud-management-gateway)에서 클라우드 관리 게이트웨이를 구성하는 데 필요합니다.

>[!NOTE]
>클라이언트 인증서가 하위 인증 기관에서 발급된 경우 체인에서 각 인증서에 이 단계를 반복해야 합니다.

## <a name="step-3-upload-the-management-certificate-to-azure"></a>3단계: Azure에 관리 인증서 업로드

API Management 인증서는 Configuration Manager에서 Azure API에 액세스하고 클라우드 관리 게이트웨이를 구성하는 데 필요합니다. 관리 인증서를 업로드하는 방법에 대한 자세한 내용 및 지침은 Azure 설명서에서 다음 문서를 참조하세요.

- [Azure Cloud Services 인증서 개요](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)

- [Azure Management API Management 인증서 업로드](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

>[!IMPORTANT]
>관리 인증서와 연결된 구독 ID를 복사해야 합니다. 이 ID는 Configuration Manager 콘솔에서 클라우드 관리 게이트웨이를 구성하는 [다음 단계](#step-4-set-up-cloud-management-gateway)에서 필요합니다.



## <a name="step-4-set-up-cloud-management-gateway"></a>4단계: 클라우드 관리 게이트웨이 설정

>[!NOTE]
>버전 1610에서 클라우드 관리 게이트웨이는 시험판 기능입니다. 사용하도록 설정하려면 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease)을 참조하세요.

1. Configuration Manager 콘솔에서 **관리** > **Cloud Services** > **클라우드 관리 게이트웨이**로 이동합니다.
2. **클라우드 관리 게이트웨이 만들기**를 선택합니다.

3. 클라우드 관리 게이트웨이 만들기 마법사에서 Azure 관리 포털에서 복사한 Azure 구독 ID를 입력하고 Azure 관리 인증서로 업로드하는 데 사용한 인증서 파일을 찾습니다. **다음**을 선택하고 콘솔이 Azure에 연결하는 동안 잠시 기다립니다.

4. 마법사에서 추가 세부 정보를 입력합니다.

    - Azure에서 실행할 서비스의 이름을 지정합니다. 서비스 이름은 영숫자 문자만 포함해야 하며 길이는 3~24자여야 합니다.

    - 서비스를 실행하려는 Azure 지역을 선택합니다.

    - 서비스에 사용하려는 Virtual Machines의 수를 지정합니다. 기본값은 1이지만 서비스용으로 Virtual Machines를 16개까지 실행할 수 있습니다.

    >[!NOTE]
    >클라우드 관리 게이트웨이 연결점용으로 인터넷 프록시를 사용하는 경우에는 포트 10124부터 프록시의 포트 수를 사용하는 Virtual Machines 수만큼 늘려야 합니다.

    - 사용자 지정 SSL 인증서에서 내보낸 개인 키(.pfx 파일)를 지정합니다.

    - 클라이언트 인증서에서 내보낸 루트 인증서(및 하위 인증서)를 지정합니다. 마법사는 최대 두 개의 루트 인증서와 네 개의 하위 인증서를 허용합니다.

    -   새 인증서 템플릿을 만들 때 사용한 동일한 서비스 이름 FQDN을 지정합니다. 사용 중인 Azure 클라우드를 기준으로 하여 FQDN 서비스 이름에 대해 다음 접미사 중 하나를 지정해야 합니다.

    Azure 클라우드 | FQDN 접두사
    --------------|-------------
    공용(상업용) 클라우드 | .cloudapp.net    
    정부 클라우드 | .usgovcloudapp.net

  - CRL 정보를 공개적으로 게시할 경우를 제외하고는 **클라이언트 인증서 해지 확인** 옆의 확인란의 선택을 해제합니다.

  - 작업을 완료한 후 **다음**을 선택합니다.

5. 14일 임계값을 사용하여 클라우드 관리 게이트웨이 트래픽을 모니터링하려면 임계값 경고를 설정하는 확인란을 선택합니다. 그런 다음 임계값을 지정하고 각 경고 수준을 높일 백분율을 지정합니다. 작업을 완료한 후 **다음**을 선택합니다.

6. 설정을 검토하고 **다음**을 선택합니다. Configuration Manager가 서비스 설정을 시작합니다. 마법사를 닫은 후 Azure에서 서비스가 완전히 프로비전될 때까지는 5~15분 정도 걸립니다. 새로 설정한 클라우드 관리 게이트웨이의 **상태** 열을 통해 서비스가 준비되는 시점을 확인합니다.

## <a name="step-5-configure-primary-site-for-client-certification-authentication"></a>5단계: 클라이언트 인증서 인증용 기본 사이트 구성

1. Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동합니다.

2. 클라우드 관리 게이트웨이를 통해 관리하려는 클라이언트의 기본 사이트를 선택하고 **속성**을 선택합니다.

3. 기본 사이트 속성 시트의 클라이언트 컴퓨터 통신 탭에서 **사용 가능한 경우 PKI 클라이언트 인증서(클라이언트 인증 기능) 사용**을 선택합니다.

4. **클라이언트에서 사이트 시스템에 대한 CRL(인증서 해지 목록) 확인** 선택을 취소해야 합니다. CRL을 공개적으로 게시하는 경우에만 이 옵션이 필요합니다.


## <a name="step-6-add-the-cloud-management-gateway-connector-point"></a>6단계: 클라우드 관리 게이트웨이 연결점 추가

클라우드 관리 게이트웨이 연결점은 클라우드 관리 게이트웨이와 통신하기 위한 새로운 사이트 시스템 역할입니다. 클라우드 관리 게이트웨이 연결점을 추가하려면 [System Center Configuration Manager용 사이트 시스템 역할 추가](/sccm/core/servers/deploy/configure/add-site-system-roles)의 지침을 따릅니다.

## <a name="step-7-configure-roles-for-cloud-management-gateway-traffic"></a>7단계: 클라우드 관리 게이트웨이 트래픽용 역할 구성

클라우드 관리 게이트웨이를 설정하는 마지막 단계에서는 클라우드 관리 게이트웨이 트래픽을 허용하도록 사이트 시스템 역할을 구성합니다. 클라우드 관리 게이트웨이에서 관리 지점 및 소프트웨어 업데이트 지점 역할만 지원됩니다. 각 역할을 별도로 구성해야 합니다.

1. Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동합니다.

2. 클라우드 관리 게이트웨이 트래픽용으로 구성할 역할에 대한 사이트 시스템 서버를 클릭합니다.

3. 역할을 선택한 다음 **속성**을 클릭합니다.

4. 역할 속성 시트의 클라이언트 연결에서 **Configuration Manager 클라우드 관리 게이트웨이 트래픽 허용** 옆의 확인란을 선택한 다음 **확인**을 선택합니다. 나머지 역할에 대해 이 단계를 반복합니다. 또한 보안 모범 사례로 **HTTPS** 옵션을 사용하는 것이 권장되지만 필수는 아닙니다.

## <a name="step-8-configure-clients-for-cloud-management-gateway"></a>8단계: 클라우드 관리 게이트웨이용 클라이언트 구성

클라우드 관리 게이트웨이와 사이트 시스템 역할이 완전히 구성되어 실행되면 클라이언트는 다음 위치 요청 시 클라우드 관리 게이트웨이 서비스의 위치를 자동으로 가져옵니다. 클라이언트가 회사 네트워크에 있어야 클라우드 관리 게이트웨이 서비스의 위치를 수신할 수 있습니다. 위치 요청에 대한 폴링 주기는 매 24시간입니다. 정상적으로 예약된 위치 요청을 기다리고 싶지 않으면 컴퓨터에서 SMS 에이전트 호스트 서비스(ccmexec.exe)를 다시 시작하여 요청을 강제로 실시할 수 있습니다.

클라우드 관리 게이트웨이 서비스의 위치가 클라이언트에 구성되어 있으면 클라이언트는 해당 서비스의 위치(인트라넷 또는 인터넷)를 자동으로 확인할 수 있습니다. 클라이언트는 도메인 컨트롤러 또는 온-프레미스 관리 지점에 연결할 수 있는 경우 Configuration Manager와의 통신에 해당 관리 지점을 사용합니다. 그렇지 않은 경우 클라이언트는 서비스가 인터넷에 있는 것으로 간주하여 클라우드 관리 게이트웨이의 위치를 통신에 사용합니다.

>[!NOTE]
> 클라우드 관리 게이트웨이의 위치(인트라넷 또는 인터넷)에 관계없이 클라이언트가 항상 클라우드 관리 게이트웨이를 사용하도록 강제 지정할 수 있습니다. 이렇게 하려면 클라이언트 컴퓨터에서 다음 레지스트리 키를 설정합니다.
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

클라이언트가 Configuration Manager에 연결할 수 있는지 확인하려는 경우 클라이언트 컴퓨터에서 다음 PowerShell 명령을 실행하면 됩니다.

`gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate`

이 명령을 실행하면 클라우드 관리 게이트웨이 서비스를 비롯하여 클라이언트가 연결할 수 있는 관리 지점이 표시됩니다.

## <a name="next-steps"></a>다음 단계

[클라이언트에서 클라우드 관리 게이트웨이 모니터링](monitor-clients-cloud-management-gateway.md)
