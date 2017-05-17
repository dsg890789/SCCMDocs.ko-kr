---
title: "클라우드 기반 배포 지점 설치 | Microsoft 문서"
description: "Microsoft Azure에서 클라우드 기반 배포 지점을 사용하기 위해 수행해야 하는 작업을 알아봅니다."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: f96905f50f879b843f98cb57c8a755aa856fb381
ms.openlocfilehash: 39b35cccf78bba4e69a7de0ca3a5a8dc516201e3
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---
# <a name="install-cloud-based-distribution-points-in-microsoft-azure-for-system-center-configuration-manager"></a>Microsoft Azure에서 System Center Configuration Manager에 대한 클라우드 기반 배포 지점 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Azure에서 System Center Configuration Manager 클라우드 기반 배포 지점을 설치할 수 있습니다. 클라우드 기반 배포 지점에 대해 잘 모르겠으면 계속하기 전에 [클라우드 기반 배포 지점 사용](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)을 참조하세요.

 설치를 시작하기 전에 필요한 인증서 파일이 있는지 확인합니다.  

-   .cer 파일 및 .pfx 파일로 내보낸 Microsoft Azure 관리 인증서  

-   .pfx 파일로 내보낸 Configuration Manager 클라우드 기반 배포 지점 서비스 인증서.  

    > [!TIP]
    >   이러한 인증서에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md) 항목에서 클라우드 기반 배포 지점 섹션을 참조하세요. 클라우드 기반 배포 지점 서비스 인증서의 배포 예제를 보려면 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에서 "클라우드 기반 배포 지점용 서비스 인증서 배포" 섹션을 참조하세요.  


 클라우드 기반 배포 지점을 설치한 후 Azure에서 서비스의 GUID를 자동으로 생성하고 이 GUID를 **cloudapp.net**의 DNS 접미사에 추가합니다. 이 GUID를 사용하여 DNS 별칭(CNAME 레코드)으로 DNS를 구성해야 합니다. 이렇게 하면 Configuration Manager 클라우드 기반 배포 지점 서비스 인증서에 정의한 서비스 이름을 자동으로 생성된 GUID에 매핑할 수 있습니다.  

 프록시 웹 서버를 사용하는 경우 배포 지점을 호스팅하는 클라우드 서비스와 통신할 수 있도록 하려면 프록시 설정을 구성해야 할 수 있습니다.  

##  <a name="BKMK_ConfigWindowsAzureandInstallDP"></a> Azure 설정 및 클라우드 기반 배포 지점 설치  
 배포 지점을 지원하도록 Azure를 설정한 다음 Configuration Manager에 클라우드 기반 배포 지점을 설치하려면 다음 절차를 따르세요.  

### <a name="to-set-up-a-cloud-service-in-azure-for-a-distribution-point"></a>배포 지점을 위해 Azure에서 클라우드 서비스를 설정하려면  

1.  웹 브라우저에서 Azure 포털 (https://manage.windowsazure.com) 을 열고 해당 계정에 액세스합니다.  

2.  **호스팅된 서비스, 저장소 계정 및 CDN**을 클릭한 다음 **관리 인증서**를 선택합니다.  

3.  구독을 마우스 오른쪽 단추로 클릭한 다음 **인증서 추가**를 클릭합니다.  

4.  **인증서 파일**에는 이 클라우드 서비스에 사용하려고 내보낸 Azure 관리 인증서가 포함된 .cer 파일을 지정하고 **확인**을 클릭합니다.  

관리 인증서가 Azure에 로드되므로 이제 클라우드 기반 배포 지점을 설치할 수 있습니다.  

### <a name="to-install-a-cloud-based-distribution-point-for-configuration-manager"></a>Configuration Manager의 클라우드 기반 배포 지점을 설치하려면  

1.  앞의 절차에 설명된 단계를 완료하여 Azure에서 관리 인증서로 클라우드 서비스를 설정합니다.  

2.  Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장하고 **클라우드 배포 지점**을 선택합니다. **홈** 탭에서 **클라우드 배포 지점 만들기**를 클릭합니다.  

3.  클라우드 배포 지점 만들기 마법사의 **일반** 페이지에서 다음을 설정합니다.  

    -   Azure 계정의 **구독 ID**를 지정합니다.  

        > [!TIP]  
        >  Azure 포털에서 Azure 구독 ID를 찾을 수 있습니다.  

    -   **관리 인증서**를 지정합니다. **찾아보기**를 클릭하여 내보낸 Azure 관리 인증서가 포함된 .pfx 파일을 지정한 다음 인증서의 암호를 입력합니다. 필요한 경우 Azure SDK 1.7에서 버전 1 .publishsettings 파일을 지정할 수 있습니다.  

4.  **다음**을 클릭합니다. Configuration Manager에서 Azure에 연결하여 관리 인증서의 유효성을 검사합니다.  

5.  **설정** 페이지에서 다음을 완료한 후 **다음**을 클릭합니다.  

    -   **영역**에서 이 배포 지점을 호스트하는 클라우드 서비스를 만들 Azure 지역을 선택합니다.  

    -   **인증서 파일**에서 내보낸 Configuration Manager 클라우드 기반 배포 지점 서비스 인증서가 포함된 .pfx 파일을 지정합니다. 암호를 입력합니다.  

        > [!NOTE]  
        >  **서비스 FQDN** 상자에는 인증서 주체 이름이 자동으로 채워집니다. 대부분의 경우 이 이름을 편집할 필요가 없습니다. 단, 테스트 환경에서 와일드카드 인증서를 사용하는 경우는 예외입니다. 예를 들어 이 경우에는 동일한 DNS 접미사를 가진 여러 컴퓨터에서 인증서를 사용할 수 있도록 호스트 이름을 지정할 수 없습니다. 이 시나리오에서는 인증서 주체에 **CN=\*.contoso.com**과 유사한 값이 포함되며 Configuration Manager에서 올바른 FQDN을 지정해야 한다는 메시지가 표시됩니다. **확인** 을 클릭하여 메시지를 닫은 다음 DNS 접미사 앞에 특정 이름을 입력하여 온전한 FQDN을 제공합니다. 예를 들어 **clouddp1.contoso.com** 의 온전한 서비스 FQDN을 지정하기 위해 **clouddp1**을 추가할 수 있습니다. 서비스 FQDN은 도메인에서 고유해야 하며 도메인에 가입된 장치와 일치하지 않아야 합니다.  
        >   
        >  와일드카드 인증서는 테스팅 환경에서만 지원됩니다.  

6.  **경고** 페이지에서 저장소 할당량, 전송 할당량 및 Configuration Manager에서 이러한 할당량에 대해 경고를 생성할 비율(%)을 설정합니다. **다음**을 클릭합니다.  

7.  마법사를 완료합니다.  

마법사에서 클라우드 기반 배포 지점에 대해 새로 호스팅되는 서비스를 만듭니다. 마법사를 닫은 후에는 Configuration Manager 콘솔에서 클라우드 기반 배포 지점의 설치 진행률을 모니터링할 수 있습니다. 기본 사이트 서버에서 **CloudMgr.log** 파일을 모니터링할 수도 있습니다. Azure Portal에서 클라우드 서비스의 프로비전을 모니터링할 수 있습니다.  

> [!NOTE]  
>  Azure에서 새 배포 지점을 프로비전하는 데 최대 30분 정도 걸릴 수 있습니다. 저장소 계정이 프로비전될 때까지 **컨테이너가 있는지 확인하려고 대기 중입니다. 메시지가 **CloudMgr.log** 파일에서 반복됩니다.(!!) 10초 후에 다시 확인합니다**. 그런 다음 서비스가 만들어지고 구성됩니다.  

 다음 방법을 사용하여 클라우드 기반 배포 지점 설치가 완료되었는지 확인할 수 있습니다.  

-   Azure Portal에서 클라우드 기반 배포 지점의 **배포**가 **준비 완료** 상태로 표시됩니다.  

-   Configuration Manager 콘솔의 **관리** 작업 영역, **계층 구성**, **클라우드** 노드에 클라우드 기반 배포 지점 상태가 **준비 완료**로 표시됩니다.  

-   Configuration Manager에서 SMS_CLOUD_SERVICES_MANAGER 구성 요소에 대해 상태 메시지 ID **9409**를 표시합니다.  

##  <a name="BKMK_ConfigDNSforCloudDPs"></a> 클라우드 기반 배포 지점에 대한 이름 확인 설정  
 클라이언트에서 클라우드 기반 배포 지점에 액세스할 수 있으려면 먼저 클라이언트가 클라우드 기반 배포 지점의 이름을 Azure가 관리하는 IP 주소로 확인할 수 있어야 합니다. 클라이언트는 다음 두 단계로 이를 수행합니다.  

1.  Configuration Manager 클라우드 기반 배포 지점 서비스 인증서에 지정된 서비스 이름을 Azure 서비스 FQDN에 매핑합니다. 이 FQDN에는 GUID와 **cloudapp.net**의 DNS 접미사가 포함되어 있습니다. GUID는 클라우드 기반 배포 지점을 설치한 후에 자동으로 설치됩니다. Azure Portal에서 클라우드 서비스의 대시보드에 있는 **사이트 URL**을 참조하여 전체 FQDN을 확인할 수 있습니다. 사이트 URL 예: **http://d1594d4527614a09b934d470.cloudapp.net**  

2.  Azure 서비스 FQDN을 Azure가 할당하는 IP 주소로 확인합니다. 이 IP 주소는 Azure Portal 클라우드 서비스의 대시보드에서도 확인할 수 있으며 **공용 VIP(가상 IP 주소)**라고 합니다.  

Configuration Manager 클라우드 기반 배포 지점 서비스 인증서에 대해 지정한 서비스 이름(예: **clouddp1.contoso.com**)을 Azure 서비스 FQDN(예: **d1594d4527614a09b934d470.cloudapp.net**)에 매핑하려면 인터넷의 DNS 서버에 DNS 별칭(CNAME 레코드)이 있어야 합니다. 그러면 클라이언트가 인터넷의 DNS 서버를 사용하여 Azure 서비스 FQDN을 IP 주소로 확인할 수 있습니다.  

##  <a name="BKMK_ConfigProxyforCloud"></a> 클라우드 서비스를 관리하는 기본 사이트의 프록시 설정 지정  
 Configuration Manager에 클라우드 서비스를 사용하는 경우 클라우드 기반 배포 지점을 관리하는 기본 사이트가 Azure Portal에 연결할 수 있어야 합니다. 사이트는 기본 사이트 컴퓨터의 **시스템** 계정을 사용하여 연결합니다. 이 연결은 기본 사이트 서버 컴퓨터에서 기본 웹 브라우저를 사용하여 이루어집니다.  

 클라우드 기반 배포 지점을 관리하는 기본 사이트 서버에서 기본 사이트가 인터넷과 Azure에 액세스할 수 있도록 프록시 설정을 지정해야 할 수도 있습니다.  

 Configuration Manager 콘솔에서 기본 사이트 서버에 대한 프록시 설정을 지정하려면 다음 절차를 따르세요.  

> [!TIP]  
>  또한 기본 사이트 서버에 새 사이트 시스템 역할을 설치할 때 **사이트 시스템 역할 추가 마법사**를 사용하여 프록시 서버를 설정할 수도 있습니다.  

#### <a name="to-set-up-proxy-settings-for-the-primary-site-server"></a>기본 사이트 서버에 대한 프록시 설정을 지정하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다. 그런 다음 클라우드 기반 배포 지점을 관리하는 기본 사이트 서버를 선택합니다.  

3.  세부 정보 창에서 **사이트 시스템**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  

4.  **사이트 시스템 속성**에서 **프록시** 탭을 선택하고 이 기본 사이트 서버에 대한 프록시 설정을 지정합니다.  

5.  **확인**을 클릭하여 설정을 저장합니다.  

