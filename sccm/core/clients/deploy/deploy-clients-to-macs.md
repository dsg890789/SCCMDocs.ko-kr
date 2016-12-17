---
title: "Mac 클라이언트 배포 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 Mac 컴퓨터에 클라이언트를 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
caps.latest.revision: 12
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: eae9e76085a95cb09fe01a32fd4b57294bc1cc20


---
# <a name="how-to-deploy-clients-to-macs-in-system-center-configuration-manager"></a>How to deploy clients to Macs in System Center Configuration Manager

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 Mac 컴퓨터에 대한 클라이언트 설치 및 관리를 수행하려면 PKI(공개 키 인프라) 인증서가 필요합니다. Configuration Manager에서는 엔터프라이즈 CA(인증 기관) 및 Configuration Manager 등록 지점/등록 프록시 지점 사이트 시스템 역할과 함께 Microsoft 인증서 서비스를 사용하여 사용자 클라이언트 인증서를 요청하고 설치할 수 있습니다. 또는 인증서가 Configuration Manager의 요구 사항을 충족하는 경우 Configuration Manager와는 별도로 컴퓨터 인증서를 요청하고 설치할 수 있습니다. PKI 인증서는 상호 인증 및 암호화된 데이터 전송을 사용하여 Mac 컴퓨터와 Configuration Manager 사이트 간의 통신을 안전하게 보호합니다.  

> [!IMPORTANT]  
>  Configuration Manager Mac 클라이언트는 항상 인증서 해지 확인을 수행합니다. Windows에서 실행되는 Configuration Manager 클라이언트와 달리 이 CRL(인증서 해지 목록) 확인 기능을 사용하지 않도록 설정할 수는 없습니다.  
>   
>  Mac 클라이언트가 CRL을 찾을 수 없어 서버 인증서의 인증서 해지 상태를 확인할 수 없는 경우 Configuration Manager 사이트 시스템(예: 관리 지점 및 배포 지점)에 연결할 수 없습니다. 특히 발급 인증 기관과 다른 포리스트에 있는 Mac 클라이언트의 경우 CRL 디자인을 검토하여 Mac 클라이언트가 사이트 시스템 서버에 연결하기 위해 CDP(CRL 배포 지점)을 찾고 연결할 수 있는지 확인하세요.  

 Mac 컴퓨터에 Configuration Manager 클라이언트를 설치하기 전에 클라이언트 인증서 설치 방법을 결정하세요.  

-   CMEnroll 도구를 사용하여 Configuration Manager 등록을 사용하고 이 항목의 다음 섹션에 설명된 단계를 수행합니다. 등록 프로세스는 자동 인증서 갱신을 지원하지 않으므로 설치된 인증서가 만료되기 전에 Mac 컴퓨터를 다시 등록해야 합니다.  

-   Configuration Manager와 별개의 인증서 요청 및 설치 방법을 사용합니다. 이 설치 방법은 이 항목에서 [Use a certificate request and installation method that is independent from Configuration Manager](#BKMK_ManualCertifcateInstallation) 섹션을 참조하세요.  

> [!NOTE]  
>  Mac 클라이언트 인증서 요구 사항 및 Mac 컴퓨터를 지원하는 데 필요한 다른 PKI 인증서에 대한 자세한 내용은 [System Center Configuration Manager에 대한 PKI 인증서 요구 사항](../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

 Mac 클라이언트는 해당 클라이언트를 관리하는 Configuration Manager 사이트에 자동으로 할당됩니다. 통신이 인트라넷으로 제한된 경우라도 Mac 클라이언트는 인터넷 전용 클라이언트로 설치됩니다. 이러한 클라이언트 구성을 통해 Mac 클라이언트의 할당된 사이트에 있는 사이트 시스템 역할(관리 지점 및 배포 지점)이 인터넷에서 클라이언트 연결을 허용하도록 구성한 경우 Mac 클라이언트가 이러한 사이트 시스템 역할과 통신하게 됩니다. Mac 컴퓨터는 할당된 사이트 외부의 사이트 시스템 역할과는 통신하지 않습니다.  

> [!IMPORTANT]  
>  Configuration Manager Mac 클라이언트를 사용하여 데이터베이스 복제본을 사용하도록 구성된 관리 지점에 연결할 수는 없습니다. 데이터베이스 복제본에 대한 자세한 내용은 [System Center Configuration Manager의 관리 지점용 데이터베이스 복제본](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)을 참조하세요.  

 Configuration Manager를 위해 Mac 컴퓨터를 설치하고 구성하고 관리하려면 다음 섹션을 사용하세요.  

-   [Mac용 클라이언트를 설치하고 구성하는 단계](#InstallSteps)  

-   [Uninstalling the Mac client](#uninstallMacClient)  

-   [Renewing the Mac client certificate](#BKMK_Renew)  

-   [Use a certificate request and installation method that is independent from Configuration Manager](#BKMK_ManualCertifcateInstallation)  

##  <a name="a-nameinstallstepsa-steps-to-install-and-configure-the-client-for-macs"></a><a name="InstallSteps"></a> Mac용 클라이언트를 설치하고 구성하는 단계  

> [!IMPORTANT]  
>  이러한 단계를 수행하기 전에 Mac 컴퓨터가 필수 조건을 충족해야 합니다. 자세한 내용은 [Mac 지원 운영 체제](../../plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mac-computers)를 참조하세요.  

### <a name="step-1-deploy-a-web-server-certificate-to-site-system-servers"></a>1단계: 사이트 시스템 서버에 웹 서버 인증서 배포  
 이러한 사이트 시스템에는 다른 Configuration Manager 클라이언트용으로 이 인증서가 이미 있을 수도 있습니다. 없다면 다음 사이트 시스템 역할을 보유한 다음 컴퓨터에 웹 서버 인증서를 배포합니다.  

-   관리 지점  

-   배포 지점  

-   등록 지점  

-   등록 프록시 지점  

> [!IMPORTANT]  
>  웹 서버 인증서는 사이트 시스템 속성에서 지정된 인터넷 FQDN을 포함해야 합니다.  
>   
>  이는 Mac 컴퓨터를 지원하기 위해 서버를 인터넷에서 액세스할 수 있어야 한다는 의미는 아닙니다. 인터넷 기반 클라이언트 관리가 필요하지 않은 경우 인터넷 FQDN에 대해 인트라넷 FQDN 값을 지정할 수 있습니다.  

 이 웹 서버 인증서를 만들고 설치하는 배포의 예는 [IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_webserver2008_cm2012)를 참조하세요.  

> [!IMPORTANT]  
>  관리 지점, 배포 지점 및 등록 프록시 지점용 웹 서버 인증서에 사이트 시스템의 인터넷 FQDN 값을 지정해야 합니다.  

### <a name="step-2-deploy-a-client-authentication-certificate-to-site-system-servers"></a>2단계: 사이트 시스템 서버에 클라이언트 인증 인증서 배포  
 이러한 사이트 시스템에는 Configuration Manager 기능용으로 이 인증서가 이미 있을 수도 있습니다. 없다면 다음 사이트 시스템 역할을 보유한 다음 컴퓨터에 클라이언트 인증서를 배포합니다.  

-   관리 지점  

-   배포 지점  

 관리 지점에 대한 클라이언트 인증서를 만들고 설치하는 배포의 예는 [Windows 컴퓨터용 클라이언트 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_client2008_cm2012)를 참조하세요.  

 배포 지점에 대한 클라이언트 인증서를 만들고 설치하는 배포의 예는 [배포 지점용 클라이언트 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_clientdistributionpoint2008_cm2012)를 참조하세요.  

### <a name="step-3-prepare-the-client-certificate-template-for-macs"></a>3단계: Mac용 클라이언트 인증서 템플릿 준비  

> [!NOTE]  
>  Configuration Manager 등록 도구를 실행하려면 Active Directory 사용자 계정이 있어야 합니다.  

 인증서 템플릿에는 Mac 컴퓨터에 인증서를 등록할 사용자 계정에 대한 **읽기** 및 **등록** 권한이 있어야 합니다.  

 [Mac 컴퓨터용 클라이언트 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_MacClient_SP1)를 참조하세요.  

### <a name="step-4-configure-the-management-point-and-distribution-point"></a>4단계: 관리 지점 및 배포 지점 구성  
 관리 지점에 다음 옵션을 구성합니다.  

-   HTTPS  

-   인터넷에서 클라이언트 연결 허용  

    > [!NOTE]  
    >  이 구성 값은 Mac 컴퓨터를 관리하는 데 필요합니다. 하지만 사이트 시스템 서버를 반드시 인터넷에서 액세스할 수 있어야 한다는 것을 의미하지는 않습니다.  

-   모바일 장치 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용  

 Mac 컴퓨터용 클라이언트를 설치하는 데는 배포 지점이 필요하지 않지만 Configuration Manager 클라이언트를 설치한 후에 이러한 Mac 컴퓨터에 소프트웨어를 배포하려면 인터넷에서 클라이언트 연결을 허용하도록 배포 지점을 구성해야 합니다.  

 이 절차는 Mac 컴퓨터를 지원하도록 기존 관리 지점과 배포 지점을 구성합니다. 이 절차를 시작하기 전에 관리 지점과 배포 지점을 실행하는 사이트 시스템 서버에 인터넷 FQDN이 구성되어 있어야 합니다. 이러한 사이트 시스템 서버가 인터넷 기반 클라이언트 관리를 지원하지 않는 경우 인터넷 FQDN 값으로 인트라넷 FQDN을 지정할 수 있습니다. 또한 이러한 사이트 시스템 역할이 기본 사이트에 있어야 합니다.  

##### <a name="to-configure-management-points-and-distribution-points-to-support-macs"></a>Mac을 지원하도록 관리 지점과 배포 지점을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 선택한 다음 구성할 사이트 시스템 역할이 있는 서버를 선택합니다.  

3.  세부 정보 창에서 **관리 지점**을 마우스 오른쪽 단추로 클릭하고 **역할 속성**을 클릭한 후 **관리 지점 속성** 대화 상자에서 다음 옵션을 구성하고 **확인**을 클릭합니다.  

    1.  **HTTPS**를 선택합니다.  

    2.  **인터넷 전용 클라이언트 연결 허용** 또는 **인터넷 및 인트라넷 클라이언트 연결 허용**을 선택합니다. 사이트 시스템 서버를 인터넷에서 액세스할 수 없는 경우라도 이러한 옵션을 사용하려면 사이트 시스템 속성에 인터넷 FQDN을 지정해야 합니다.  

    3.  **모바일 장치 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용**을 선택합니다.  

4.  세부 정보 창에서 **배포 지점**을 마우스 오른쪽 단추로 클릭하고 **역할 속성**을 클릭한 후 **배포 지점 속성** 대화 상자에서 다음 옵션을 구성하고 **확인**을 클릭합니다.  

    -   **HTTPS**를 선택합니다.  

    -   **인터넷 전용 클라이언트 연결 허용** 또는 **인터넷 및 인트라넷 클라이언트 연결 허용**을 선택합니다. 사이트 시스템 서버를 인터넷에서 액세스할 수 없는 경우라도 이러한 옵션을 사용하려면 사이트 시스템 속성에 인터넷 FQDN을 지정해야 합니다.  

    -   **인증서 가져오기**를 클릭하고 내보낸 클라이언트 배포 지점 인증서 파일을 찾은 다음 암호를 지정합니다.  

5.  Mac 컴퓨터를 사용할 기본 사이트의 모든 관리 지점과 배포 지점에 대해 2단계부터 4단계까지 반복합니다.  

### <a name="step-5-configure-the-enrollment-proxy-point-and-the-enrollment-point"></a>5단계: 등록 프록시 지점 및 등록 지점 구성  
 이러한 사이트 시스템 역할을 둘 다 동일한 사이트에 설치할 수 있지만 동일한 사이트 시스템 서버 또는 동일한 Active Directory 포리스트에 설치할 필요는 없습니다.  

 사이트 시스템 역할 및 고려 사항에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)에서 [사이트 시스템 역할](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles)을 참조하세요.  

 다음 절차는 Mac 컴퓨터를 지원하도록 사이트 시스템 역할을 구성합니다. Mac 컴퓨터를 지원하기 위해 새 사이트 시스템 서버를 설치할지 아니면 기존 사이트 시스템 서버를 사용할지에 따라 다음 절차 중 하나를 선택합니다.  

-   [등록 사이트 시스템: 새 사이트 시스템 서버를 설치 및 구성하려면](#BKMK_HowtoInstallEnrollmentSiteSystems_new)  

-   [등록 사이트 시스템: 기존 사이트 시스템 서버를 설치 및 구성하려면](#BKMK_HowtoInstallEnrollmentSiteSystems_existing)  

####  <a name="a-namebkmkhowtoinstallenrollmentsitesystemsnewa-to-install-and-configure-the-enrollment-site-systems-new-site-system-server"></a><a name="BKMK_HowtoInstallEnrollmentSiteSystems_new"></a> 등록 사이트 시스템: 새 사이트 시스템 서버를 설치 및 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.   **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 클릭합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다.  

    > [!IMPORTANT]  
    >  사이트 시스템 서버를 인터넷에서 액세스할 수 없는 경우라도 인터넷 FQDN의 값을 지정해야 합니다. 사이트 시스템 서버를 인터넷에서 액세스할 수 없어서 인터넷 FQDN이 없는 경우 인터넷 FQDN으로 인트라넷 FQDN 값을 지정할 수 있습니다. Mac 컴퓨터는 인트라넷에 있어도 항상 인터넷 FQDN에 연결합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **등록 프록시 지점** 및 **등록 지점** 을 선택하고 **다음**을 클릭합니다.  

6.  **등록 프록시 지점** 페이지에서 설정을 검토하고 필요한 내용을 변경한 후 **다음**을 클릭합니다.  

7.  **등록 지점 설정** 페이지에서 설정을 검토하고 필요한 내용을 변경한 후 **다음**을 클릭합니다.  

8.  마법사를 완료합니다.  

####  <a name="a-namebkmkhowtoinstallenrollmentsitesystemsexistinga-to-install-and-configure-the-enrollment-site-systems-existing-site-system-server"></a><a name="BKMK_HowtoInstallEnrollmentSiteSystems_existing"></a> 등록 사이트 시스템: 기존 사이트 시스템 서버를 설치 및 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 선택한 다음 Mac 컴퓨터를 지원하는 데 사용할 서버를 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 역할 추가**를 클릭합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다.  

    > [!IMPORTANT]  
    >  사이트 시스템 서버를 인터넷에서 액세스할 수 없는 경우라도 인터넷 FQDN의 값을 지정해야 합니다. 사이트 시스템 서버를 인터넷에서 액세스할 수 없어서 인터넷 FQDN이 없는 경우 인터넷 FQDN으로 인트라넷 FQDN 값을 지정할 수 있습니다. Mac 컴퓨터는 인트라넷에 있어도 항상 인터넷 FQDN에 연결합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **등록 프록시 지점** 및 **등록 지점** 을 선택하고 **다음**을 클릭합니다.  

6.  **등록 프록시 지점** 페이지에서 설정을 검토하고 필요한 내용을 변경한 후 **다음**을 클릭합니다.  

7.  **등록 지점 설정** 페이지에서 설정을 검토하고 필요한 내용을 변경한 후 **다음**을 클릭합니다.  

8.  마법사를 완료합니다.  

### <a name="step-6-optional-install-the-reporting-services-point"></a>6단계: 옵션: 보고 서비스 지점 설치  
 Mac 컴퓨터에 대한 보고서를 실행하려면 보고 서비스 지점을 설치합니다.  

 보고 서비스 지점을 설치하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 보고 구성](../../../core/servers/manage/configuring-reporting.md)을 참조하세요.  

### <a name="step-7-configure-client-settings-for-enrollment"></a>7단계: 등록을 위한 클라이언트 설정 구성  
 Mac 컴퓨터에 대해 등록을 구성하려면 기본 클라이언트 설정을 사용해야 합니다. 사용자 지정 클라이언트 설정은 사용할 수 없습니다.  

 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../core/clients/deploy/about-client-settings.md)를 참조하세요.  

 Mac 컴퓨터에 인증서를 요청하고 설치하려면 Configuration Manager에서 이 단계를 수행해야 합니다.  

##### <a name="to-configure-the-default-client-settings-for-configuration-manager-to-enroll-certificates-for-macs"></a>Configuration Manager의 기본 클라이언트 설정에서 Mac용 인증서를 등록하도록 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.  

3.  **기본 클라이언트 설정**을 클릭합니다.  

    > [!IMPORTANT]  
    >  등록 구성을 위해서는 사용자 지정 클라이언트 설정을 사용할 수 없고 기본 클라이언트 설정을 사용해야 합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  **등록** 섹션을 선택하고 다음 사용자 설정을 구성합니다.  

    1.  **사용자가 모바일 장치 및 Mac 컴퓨터를 등록할 수 있도록 허용: 예**  

    2.  **등록 프로필:** **프로필 설정**을 클릭합니다.  

6.  **모바일 장치 등록 프로필** 대화 상자에서 **만들기**를 클릭합니다.  

7.  **등록 프로필 만들기** 대화 상자에서 이 등록 프로필의 이름을 입력한 다음 **관리 사이트 코드**를 구성합니다. Mac 컴퓨터를 관리할 관리 지점이 포함된 Configuration Manager 기본 사이트를 선택합니다.  

    > [!NOTE]  
    >  이 사이트를 선택할 수 없는 경우 사이트에서 모바일 장치를 지원할 관리 지점을 하나 이상 구성했는지 확인합니다.  

8.  **추가**를 클릭합니다.  

9. **모바일 장치에 대한 인증 기관 추가** 대화 상자에서 Mac 컴퓨터에 대한 인증서를 발급할 CA(인증 기관) 서버를 선택하고 **확인**을 클릭합니다.  

10. **등록 프로필 만들기** 대화 상자에서 3단계에서 만든 Mac 컴퓨터 인증서 템플릿을 선택하고 **확인**을 클릭합니다.  

11. **확인** 을 클릭하여 **등록 프로필** 대화 상자를 닫고, **확인** 을 클릭하여 **기본 클라이언트 설정** 대화 상자를 닫습니다.  

    > [!TIP]  
    >  클라이언트 정책 간격을 변경하려면 **클라이언트 정책** 클라이언트 설정 그룹에서 **클라이언트 정책 폴링 간격** 클라이언트 설정을 사용합니다.  

 모든 사용자가 다음 번에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [Configuration Manager 클라이언트에 대한 정책 검색 시작](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval)을 참조하세요.  

 등록 클라이언트 설정 외에도 다음 Configuration Manager 클라이언트 장치 설정을 구성했는지 확인합니다.  

-   **하드웨어 인벤토리**: Mac 및 Windows 클라이언트 컴퓨터에서 하드웨어 인벤토리를 수집하려면 이 클라이언트 설정을 사용하도록 설정하고 구성합니다. 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 확장하는 방법](../../../core/clients/manage/inventory/extend-hardware-inventory.md)을 참조하세요.  

-   **준수 설정**: Mac 및 Windows 클라이언트 컴퓨터에 대한 설정을 평가하고 수정하려면 이 클라이언트 설정을 사용하도록 설정하고 구성합니다. 자세한 내용은 [준수 설정 계획 및 구성](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)을 참조하세요.  

> [!NOTE]  
>  Configuration Manager 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

### <a name="step-8-download-the-client-source-files-for-macs"></a>8단계: Mac용 클라이언트 원본 파일 다운로드  
 Mac에서 Configuration Manager 클라이언트를 설치하고 관리하려면 다음 프로그램을 다운로드하고 설치해야 합니다.  

-   **Ccmsetup**: 조직의 Mac 컴퓨터에 Configuration Manager 클라이언트를 설치하려면 이 응용 프로그램을 사용합니다.  

-   **CMDiagnostics**: 조직의 Mac 컴퓨터에 설치된 Configuration Manager 클라이언트와 관련된 진단 정보를 수집하려면 이 도구를 사용합니다.  

-   **CMUninstall**: 조직의 Mac 컴퓨터에서 Configuration Manager 클라이언트를 제거하려면 이 도구를 사용합니다.  

-   **CMAppUtil**: Apple 응용 프로그램 패키지를 Configuration Manager 응용 프로그램으로 배포할 수 있는 형식으로 변환하려면 이 도구를 사용합니다.  

-   **CMEnroll**: Configuration Manager 클라이언트를 설치할 수 있도록 Mac 컴퓨터에 대한 클라이언트 인증서를 요청하고 설치하려면 이 도구를 사용합니다.  

> [!IMPORTANT]  
>  Mac 컴퓨터용 새 클라이언트를 설치할 때 Configuration Manager 콘솔에서 새 클라이언트 정보를 반영하려면 Configuration Manager 업데이트도 설치해야 할 수 있습니다.  

##### <a name="to-download-and-install-the-mac-os-x-client-files"></a>Mac OS X 클라이언트 파일을 다운로드하고 설치하려면  

1.  Mac OS X 클라이언트 파일 패키지 **ConfigmgrMacClient.msi**를 다운로드하여 Windows를 실행하는 컴퓨터에 저장합니다.  

     이 파일은 Configuration Manager 설치 미디어에서 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 다운로드할 수 있습니다.  

2.  Windows 컴퓨터에서 방금 다운로드한 **ConfigmgrMacClient.msi** 파일을 실행하여 Mac 클라이언트 패키지 Macclient.dmg를 로컬 디스크의 폴더(기본적으로 **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client\\**)에 추출합니다.  

3.  Macclient.dmg 파일을 Mac 컴퓨터의 폴더에 복사합니다.  

4.  Mac 컴퓨터에서 방금 다운로드한 Macclient.dmg 파일을 실행하여 로컬 디스크의 폴더에 추출합니다.  

5.  이 폴더에서 Ccmsetup and CMClient.pkg 파일이 추출되어 있고 CMDiagnostics, CMUninstall, CMAppUtil, CMEnroll 도구가 포함된 Tools 폴더가 만들어졌는지 확인합니다.  

### <a name="step-9-install-the-client-and-then-enroll-the-client-certificate-on-the-mac"></a>9단계: Mac에 클라이언트를 설치한 다음 클라이언트 인증서 등록  
 이 절차는 클라이언트를 설치한 후에 CMEnroll 도구를 사용하여 Mac 컴퓨터에 대한 클라이언트 인증서를 요청하고 설치합니다. 그러면 Configuration Manager를 사용하여 컴퓨터를 관리할 수 있습니다.  

 CMEnroll 도구를 사용할 필요 없이 Mac 컴퓨터 등록 마법사를 사용하여 클라이언트를 등록할 수 있습니다. 자세한 내용은 아래 절차를 참조하세요.  

##### <a name="to-install-the-client-and-enroll-the-certificate-by-using-the-cmenroll-tool"></a>CMEnroll 도구를 사용하여 클라이언트를 설치하고 인증서를 등록하려면  

1.  Mac 컴퓨터에서, Microsoft 다운로드 센터에서 다운로드한 Macclient.dmg 파일의 콘텐츠를 추출한 폴더를 찾습니다.  

2.  다음 명령줄을 입력합니다. **sudo ./ccmsetup**  

3.  **설치 완료** 메시지가 나타날 때까지 기다립니다. 설치 관리자에서 지금 다시 시작해야 한다는 메시지가 표시되더라도 지금 다시 시작하지 않고 다음 단계를 계속합니다.  

4.  Mac 컴퓨터의 Tools 폴더에서 다음 명령을 입력합니다. **sudo ./CMEnroll -s &lt;enrollment_proxy_server_name> -ignorecertchainvalidation -u &lt;사용자 이름'>**  

    > [!NOTE]  
    >  클라이언트를 설치한 후 Mac 컴퓨터 등록을 안내하는 Mac 컴퓨터 등록 마법사가 열립니다. 이 방법으로 클라이언트를 등록하려면 이 항목에서 [To enroll the client by using the Mac Computer Enrollment Wizard](#BKMK_EnrollR2) 섹션을 참조하세요.  

     그런 다음 메시지가 나타나면 Active Directory 사용자 계정의 암호를 입력합니다.  

    > [!IMPORTANT]  
    >  이 명령을 입력하면 실제로 두 가지 암호를 묻는 메시지가 나타납니다. 첫 번째는 명령을 실행하기 위한 슈퍼 사용자 계정의 암호를 묻고, 두 번째는 Active Directory 사용자 계정의 암호를 묻습니다. 메시지가 동일하게 나타날 수 있으므로 올바른 순서로 암호를 지정해야 합니다.  

     사용자 이름은 다음 형식이 될 수 있습니다.  

    -   '도메인\이름'. 예를 들면 'contoso\mnorth'와 같습니다.  

    -   'user@domain'. 예를 들면 다음과 같습니다. 'mnorth@contoso.com'  

     사용자 이름과 해당 암호는 Mac 클라이언트 인증서 템플릿에 대한 읽기 및 등록 권한이 부여된 Active Directory 사용자 계정과 일치해야 합니다.  

     예: 등록 프록시 지점 서버 이름이 **server02.contoso.com**이고 사용자 이름이 **contoso\mnorth**인 사용자에게 Mac 클라이언트 인증서 템플릿에 대한 권한이 부여된 경우 다음을 입력합니다. **sudo ./CMEnroll -s server02.contoso.com -ignorecertchainvalidation -u 'contoso\mnorth'**  

    > [!IMPORTANT]  
    >  사용자 이름에 **&lt;>"+=,** 중 하나가 포함된 경우 등록에 실패합니다.  
    >   
    >  이 문제를 해결하려면 이러한 문자가 포함되지 않은 사용자 이름으로 대역 외 인증서를 가져옵니다.  

    > [!NOTE]  
    >  보다 원활한 사용자 경험을 위해 설치 단계와 명령을 스크립팅하여 사용자가 사용자 이름과 암호만 입력하면 되도록 할 수 있습니다.  

5.  **등록 성공** 메시지가 나타날 때까지 기다립니다.  

6.  등록된 인증서를 Configuration Manager로 제한하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    1.   **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**명령을 입력합니다.  

    2.  **키 집합 접근** 대화 상자의 **키 집합** 섹션에서 **시스템**을 클릭한 다음 **카테고리** 섹션에서 **키**를 클릭합니다.  

    3.  클라이언트 인증서를 보려면 해당 키를 확장합니다. 방금 설치한 인증서를 개인 키로 식별한 경우 키를 두 번 클릭합니다.  

    4.  **연결 조절** 탭에서 **접근 허용 전 확인**을 선택합니다.  

    5.  **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 클릭합니다.  

    6.  **변경사항 저장** 을 클릭하고 **키 집합 접근** 대화 상자를 닫습니다.  

7.  Mac 컴퓨터를 다시 시작합니다.  

 Mac 컴퓨터에서, **시스템 환경설정** 에서 **Configuration Manager** 를 열어 설치가 성공했는지 확인합니다. 또한 **모든 시스템** 컬렉션을 업데이트하고 확인하여 이제 Mac 컴퓨터가 이 컬렉션에 관리되는 클라이언트로 나타나는지 확인합니다.  

> [!TIP]  
>  Mac 클라이언트에 대한 문제를 해결하려는 경우 Mac OS X 클라이언트 패키지에 포함된 CMDiagnostics 프로그램을 사용하여 다음 진단 정보를 수집할 수 있습니다.  
>   
>  -   실행 중인 프로세스 목록  
> -   Mac OS X 운영 체제 버전  
> -   **CCM\*.crash** 및 **System Preference.crash**를 비롯한 Configuration Manager 클라이언트와 관련된 Mac OS X 충돌 보고서  
> -   Configuration Manager 클라이언트 설치를 통해 생성된 BOM(제품 구성 정보) 파일 및 속성 목록(.plist) 파일  
> -   라이브러리/응용 프로그램 지원/Microsoft/CCM/Logs 폴더의 내용  
>   
>  CmDiagnostics를 통해 수집되는 정보는 이름이 cmdiag-*<호스트 이름\>***-***<날짜 및 시간\>*.zip인 압축 파일에 추가되어 컴퓨터 바탕 화면에 저장됩니다.  

####  <a name="a-namebkmkenrollr2a-to-enroll-the-client-by-using-the-mac-computer-enrollment-wizard"></a><a name="BKMK_EnrollR2"></a> To enroll the client by using the Mac Computer Enrollment Wizard  

1.  클라이언트 설치를 마치면 컴퓨터 등록 마법사가 열립니다. **다음** 을 클릭하여 시작 페이지를 지나 계속 진행합니다.  

    > [!NOTE]  
    >  마법사가 열리지 않거나 마법사를 실수로 닫은 경우 **Configuration Manager** 기본 설정 페이지에서 **등록** 을 클릭하여 마법사를 엽니다.  

2.  마법사의 다음 페이지에서 다음 정보를 지정합니다.  

    -   **사용자 이름** - 사용자 이름은 다음 형식이 될 수 있습니다.  

        -   '도메인\이름'. 예를 들면 'contoso\mnorth'와 같습니다.  

        -   'user@domain'. 예를 들면 다음과 같습니다. 'mnorth@contoso.com'  

            > [!IMPORTANT]  
            >  메일 주소를 사용하여 **사용자 이름** 필드를 채운 경우 Configuration Manager는 메일 주소의 도메인 이름과 등록 프록시 지점 서버의 기본 이름을 자동으로 사용하여 **서버 이름** 필드를 채웁니다. 이 도메인 이름과 서버 이름이 등록 프록시 지점 서버의 이름과 일치하지 않는 경우 사용자에게 사용할 올바른 이름을 알려서 사용자가 Mac 컴퓨터를 등록할 때 올바른 이름을 입력할 수 있도록 합니다.  

         사용자 이름과 해당 암호는 Mac 클라이언트 인증서 템플릿에 대한 읽기 및 등록 권한이 부여된 Active Directory 사용자 계정과 일치해야 합니다.  

    -   **암호** – 지정한 사용자 이름에 해당하는 암호를 입력합니다.  

    -   **서버 이름** – 등록 프록시 지점 서버의 이름을 입력합니다.  

3.  **다음** 을 클릭하여 계속 진행한 후 마법사를 완료합니다.  

##  <a name="a-nameuninstallmacclienta-uninstalling-the-mac-client"></a><a name="uninstallMacClient"></a> Uninstalling the Mac client  
 Mac 클라이언트를 제거하려면 웹에서 다운로드한 Mac 클라이언트 파일과 함께 제공된 CMUninstall 스크립트를 사용합니다. Mac 컴퓨터에서 Configuration Manager 클라이언트를 제거하려면 다음 절차를 따르세요.  

#### <a name="to-uninstall-the-mac-client"></a>Mac 클라이언트를 제거하려면  

1.  Mac 컴퓨터에서, 터미널 윈도우를 열고 Microsoft 다운로드 센터에서 다운로드한 macclient.dmg 파일의 콘텐츠를 추출한 폴더를 찾습니다.  

2.  Tools 폴더로 이동하여 다음 명령줄을 입력합니다.  

     **./CMUninstall -c**  

    > [!NOTE]  
    >  **–c** 속성을 지정하면 클라이언트 제거 시 클라이언트 충돌 로그 및 로그 파일도 제거됩니다. 이 속성은 선택적이지만 나중에 클라이언트를 다시 설치할 경우 혼동을 방지하기 위해 사용하는 것이 좋습니다.  

3.  필요한 경우 Configuration Manager에 사용되던 클라이언트 인증 인증서를 수동으로 제거하거나 해지합니다. CMUnistall은 이 인증서를 제거하거나 해지하지 않습니다.  

##  <a name="a-namebkmkrenewa-renewing-the-mac-client-certificate"></a><a name="BKMK_Renew"></a> Renewing the Mac client certificate  
 다음 방법 중 하나를 사용하여 Mac 클라이언트 인증서를 갱신할 수 있습니다.  

-   [Renewing the Mac client certificate by using the Renew Certificate Wizard](#BKMK_UI)  

-   [Renewing the Mac client certificate manually](#BKMK_Man)  

###  <a name="a-namebkmkuia-renewing-the-mac-client-certificate-by-using-the-renew-certificate-wizard"></a><a name="BKMK_UI"></a> Renewing the Mac client certificate by using the Renew Certificate Wizard  
 다음 절차에 따라 Configuration Manager에서 인증서 갱신 마법사를 구성 및 사용할 수 있습니다.  

##### <a name="to-renew-the-mac-client-certificate-by-using-the-renew-certificate-wizard"></a>인증서 갱신 마법사를 사용하여 Mac 클라이언트 인증서를 갱신하려면  

1.  ccmclient.plist 파일에서 인증서 갱신 마법사가 열리는 시기를 제어하는 값을 다음과 같이 구성합니다.  

    > [!IMPORTANT]  
    >  이러한 값은 문자열로 구성해야 합니다. 값을 정수 데이터 형식으로 구성하는 경우( **–int** 속성 사용), 해당 값은 읽히지 않습니다.  

    -   **RenewalPeriod1** – 사용자가 인증서를 갱신할 수 있는 첫 번째 갱신 기간(초)을 지정합니다. 기본값은 3,888,000초(45일)입니다.  

        > [!NOTE]  
        >  **RenewalPeriod1** 이 구성되어 있으며 값이 300초 이상이면 구성된 값이 사용됩니다.  구성된 값이 0초보다 크고 300초보다 작으면 기본값인 45일이 사용됩니다.  

    -   **RenewalPeriod2** – 사용자가 인증서를 갱신할 수 있는 두 번째 갱신 기간(초)을 지정합니다. 기본값은 259,200초(3일)입니다.  

        > [!NOTE]  
        >  **RenewalPeriod2** 가 구성되었으며 300초 이상이면서 **RenewalPeriod1**이하인 경우 구성된 값이 사용됩니다. **RenewalPeriod1** 가 3일보다 크면 **RenewalPeriod2**에 대해 값으로 3일이 사용됩니다.  **RenewalPeriod1** 3일보다 작은 경우에는 **RenewalPeriod2** 가 **RenewalPeriod1**과 같은 값으로 설정됩니다.  

    -   **RenewalReminderInterval1** – 첫 번째 갱신 기간 중 인증서 갱신 마법사가 사용자에게 표시하는 빈도(초)를 지정합니다. 기본값은 86,400초(1일)입니다.  

        > [!NOTE]  
        >  **RenewalReminderInterval1** 이 300초보다 크고 **RenewalPeriod1**에 대해 구성된 값보다 작은 경우 구성된 값이 사용됩니다. 그렇지 않은 경우 1일의 기본값이 사용됩니다.  

    -   **RenewalReminderInterval2** – 두 번째 갱신 기간 중 인증서 갱신 마법사가 사용자에게 표시하는 빈도(초)를 지정합니다. 기본값은 28,800초(8시간)입니다.  

        > [!NOTE]  
        >  **RenewalReminderInterval2** 가 300초보다 크고 **RenewalReminderInterval1** 및 **RenewalPeriod2**이하인 경우에는 구성된 값이 사용됩니다. 그렇지 않은 경우에는 값으로 8시간이 사용됩니다.  

     **예제:** 값을 기본값으로 유지하는 경우 인증서 만료 45일 전에 마법사가 24시간마다 열립니다.  인증서 만료 3일 전부터는 마법사가 8시간마다 열립니다.  

     **예제:** 다음 명령줄 또는 스크립트를 사용하여 첫 번째 갱신 기간을 20일로 설정할 수 있습니다.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  인증서 갱신 마법사가 열릴 때 **사용자 이름** 및 **서버 이름** 필드가 일반적으로 미리 채워지며 사용자는 암호만 입력하면 인증서를 갱신할 수 있습니다.  

    > [!NOTE]  
    >  마법사가 열리지 않거나 마법사를 실수로 닫은 경우 **Configuration Manager** 기본 설정 페이지에서 **갱신** 을 클릭하여 마법사를 엽니다.  

###  <a name="a-namebkmkmana-renewing-the-mac-client-certificate-manually"></a><a name="BKMK_Man"></a> Renewing the Mac client certificate manually  
 Mac 클라이언트 인증서의 일반적인 유효 기간은 1년입니다. Configuration Manager에서는 등록 중에 요청하는 사용자 인증서를 자동으로 갱신하지 않으므로 다음 절차에 따라 인증서를 수동으로 갱신해야 합니다.  

> [!IMPORTANT]  
>  인증서가 만료된 경우 인증서를 제거하고 다시 설치한 후 Mac 클라이언트를 다시 등록해야 합니다.  

 이 절차는 동일한 Mac 컴퓨터에 대한 새 인증서를 요청하는 데 필요한 SMSID를 제거합니다. 새 인증서가 요청된 후에는 Configuration Manager에서 자동으로 사용됩니다.  

> [!IMPORTANT]  
>  SMSID를 제거하고 대체할 경우 Configuration Manager 콘솔에서 클라이언트를 삭제한 후에 인벤토리와 같은 저장된 클라이언트 기록이 삭제됩니다.  

##### <a name="to-renew-the-mac-client-certificate-manually"></a>Mac 클라이언트 인증서를 수동으로 갱신하려면  

1.  사용자 인증서를 갱신해야 하는 Mac 컴퓨터에 대한 장치 컬렉션을 만든 다음 이 컬렉션에 Mac 컴퓨터를 추가합니다.  

    > [!WARNING]  
    >  Configuration Manager에서는 Mac 컴퓨터에 등록되는 인증서의 유효 기간을 모니터링하지 않습니다. 이 컬렉션을 추가할 Mac 컴퓨터를 식별하려면 Configuration Manager에서 별도로 이를 모니터링해야 합니다.  

2.  **자산 및 호환성** 작업 영역에서 **구성 항목 만들기 마법사**를 시작합니다.  

3.  마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **유형:Mac OS X**  

4.  마법사의 **지원되는 플랫폼** 페이지에서 모든 Mac OS X 버전이 선택되어 있는지 확인합니다.  

5.  마법사의 **설정** 페이지에서 **새로 만들기** 를 클릭하고 **설정 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **설정 유형:스크립트**  

    -   **데이터 형식:문자열**  

6.  **설정 만들기** 대화 상자의 **검색 스크립트**에 대해 **스크립트 추가** 를 클릭하여 SMSID가 구성된 Mac 컴퓨터를 검색하는 스크립트를 지정합니다.  

7.  **검색 스크립트 편집** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  **확인** 을 클릭하여 **검색 스크립트 편집** 대화 상자를 닫습니다.  

9. **설정 만들기** 대화 상자의 **재구성 스크립트(옵션)**에 대해 **스크립트 추가** 를 클릭하여 Mac 컴퓨터에서 발견된 SMSID를 제거하는 스크립트를 지정합니다.  

10. **재구성 스크립트 만들기** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. **확인** 을 클릭하여 **재구성 스크립트 만들기** 대화 상자를 닫습니다.  

12. 마법사의 **호환성 규칙** 페이지에서 **새로 만들기**를 클릭하고 **규칙 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **선택한 설정:** **찾아보기** 를 클릭하고 이전에 지정한 검색 스크립트를 선택합니다.  

    -   **다음 값** 필드에 **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**를 입력합니다.  

    -   **이 설정이 규칙과 호환되지 않는 경우 지정한 재구성 스크립트 실행**옵션을 사용하도록 설정합니다.  

13. 구성 항목 만들기 마법사를 완료합니다.  

14. 방금 만든 구성 항목을 포함하는 구성 기준을 만들고 이를 1단계에서 만든 장치 컬렉션에 배포합니다.  

     구성 기준을 만들고 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 구성 기준을 만드는 방법](../../../compliance/deploy-use/create-configuration-baselines.md) 및 [System Center Configuration Manager에서 구성 기준을 배포하는 방법](../../../compliance/deploy-use/deploy-configuration-baselines.md)을 참조하세요.  

15. SMSID가 제거된 Mac 컴퓨터에서 다음 명령을 실행하여 새 인증서를 설치합니다.  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     메시지가 나타나면 명령을 실행할 슈퍼 사용자 계정의 암호를 지정한 후 Active Directory 사용자 계정의 암호를 지정합니다.  

16. 등록된 인증서를 Configuration Manager로 제한하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    1.   **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**명령을 입력합니다.  

    2.  **키 집합 접근** 대화 상자의 **키 집합** 섹션에서 **시스템**을 클릭한 다음 **카테고리** 섹션에서 **키**를 클릭합니다.  

    3.  클라이언트 인증서를 보려면 해당 키를 확장합니다. 방금 설치한 인증서를 개인 키로 식별한 경우 키를 두 번 클릭합니다.  

    4.  **연결 조절** 탭에서 **접근 허용 전 확인**을 선택합니다.  

    5.  **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 클릭합니다.  

    6.  **변경사항 저장** 을 클릭하고 **키 집합 접근** 대화 상자를 닫습니다.  

17. Mac 컴퓨터를 다시 시작합니다.  

##  <a name="a-namebkmkmanualcertifcateinstallationa-use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager"></a><a name="BKMK_ManualCertifcateInstallation"></a> Use a certificate request and installation method that is independent from Configuration Manager  
 Configuration Manager 등록을 사용하지 않고 대신 Configuration Manager와는 별개로 클라이언트 인증서를 요청 및 설치하는 경우 구성 단계는 약간 다릅니다.  

1.  1, 2, 4, 6단계(선택적) 및 8단계를 수행합니다.  

2.  3, 5, 7, 9단계를 수행하지 않습니다.  

3.  다음 지침을 사용하여 클라이언트를 설치합니다.  

#### <a name="to-install-the-client-certificate-independently-from-configuration-manager-and-install-the-client"></a>Configuration Manager와 별개로 클라이언트 인증서를 설치한 후 클라이언트를 설치하려면  

1.  Configuration Manager와 별개로 클라이언트 인증서를 설치하려면 선택한 인증서 배포 방법에 따른 지침을 사용하여 Mac 컴퓨터에서 클라이언트 인증서를 요청하고 설치합니다.  

2.  Microsoft 다운로드 센터에서 다운로드한 macclient.dmg 파일의 콘텐츠를 추출한 폴더를 찾습니다.  

3.  **sudo ./ccmsetup -MP <관리 지점 인터넷 FQDN\> -SubjectName <인증서 주체 값\>** 명령줄을 입력합니다.  

    > [!IMPORTANT]  
    >  인증서 주체 값은 대소문자를 구분하므로 인증서 세부 정보에 나타난 대로 정확히 입력합니다.  

     예: 사이트 시스템 속성의 인터넷 FQDN이 **server03.contoso.com**이고 Mac 클라이언트 인증서가 **mac12.contoso.com**의 FQDN을 인증서 주체의 일반 이름으로 사용하는 경우 다음을 입력합니다. **sudo ./ccmsetup -MP server03.contoso.com -SubjectName mac12.contoso.com**  

4.   **설치 완료** 메시지가 나타날 때까지 기다렸다가 Mac 컴퓨터를 다시 시작합니다.  

5.  이 인증서를 Configuration Manager에서 액세스할 수 있도록 하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    1.   **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**명령을 입력합니다.  

    2.  **키 집합 접근** 대화 상자의 **키 집합** 섹션에서 **시스템**을 클릭한 다음 **카테고리** 섹션에서 **키**를 클릭합니다.  

    3.  클라이언트 인증서를 보려면 해당 키를 확장합니다. 방금 설치한 인증서를 개인 키로 식별한 경우 키를 두 번 클릭합니다.  

    4.  **연결 조절** 탭에서 **접근 허용 전 확인**을 선택합니다.  

    5.  **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 클릭합니다.  

    6.  **변경사항 저장** 을 클릭하고 **키 집합 접근** 대화 상자를 닫습니다.  

6.  동일한 주체 값을 포함하는 인증서가 둘 이상 있는 경우 Configuration Manager 클라이언트에 사용하려는 인증서를 식별할 수 있도록 인증서 일련 번호를 지정해야 합니다. 이 작업을 수행하려면 다음 명령을 사용합니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "<일련 번호\>"**.  

     예를 들면 다음과 같습니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

 Mac 컴퓨터에서, **시스템 환경설정** 에서 **Configuration Manager** 를 열어 설치가 성공했는지 확인합니다. 또한 **모든 시스템** 컬렉션을 업데이트하고 확인하여 이제 Mac 컴퓨터가 이 컬렉션에 관리되는 클라이언트로 나타나는지 확인합니다.  

### <a name="renewing-the-mac-client-certificate"></a>Mac 클라이언트 인증서 갱신  
 Mac 컴퓨터에서 컴퓨터 인증서를 갱신하기 전에 다음 단계를 따르세요.  

 이 절차는 클라이언트에서 Mac 컴퓨터에 대한 새 인증서 또는 갱신된 인증서를 사용하는 데 필요한 SMSID를 제거합니다.  

> [!IMPORTANT]  
>  SMSID를 제거하고 대체할 경우 Configuration Manager 콘솔에서 클라이언트를 삭제한 후에 인벤토리와 같은 저장된 클라이언트 기록이 삭제됩니다.  

##### <a name="to-renew-the-mac-client-certificate"></a>Mac 클라이언트 인증서를 갱신하려면  

1.  컴퓨터 인증서를 갱신해야 하는 Mac 컴퓨터에 대한 장치 컬렉션을 만든 다음 이 컬렉션에 Mac 컴퓨터를 추가합니다.  

2.  **자산 및 호환성** 작업 영역에서 **구성 항목 만들기 마법사**를 시작합니다.  

3.  마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **유형:Mac OS X**  

4.  마법사의 **지원되는 플랫폼** 페이지에서 모든 Mac OS X 버전이 선택되어 있는지 확인합니다.  

5.  마법사의 **설정** 페이지에서 **새로 만들기** 를 클릭하고 **설정 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **설정 유형:스크립트**  

    -   **데이터 형식:문자열**  

6.  **설정 만들기** 대화 상자의 **검색 스크립트**에 대해 **스크립트 추가** 를 클릭하여 SMSID가 구성된 Mac 컴퓨터를 검색하는 스크립트를 지정합니다.  

7.  **검색 스크립트 편집** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  **확인** 을 클릭하여 **검색 스크립트 편집** 대화 상자를 닫습니다.  

9. **설정 만들기** 대화 상자의 **재구성 스크립트(옵션)**에 대해 **스크립트 추가** 를 클릭하여 Mac 컴퓨터에서 발견된 SMSID를 제거하는 스크립트를 지정합니다.  

10. **재구성 스크립트 만들기** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. **확인** 을 클릭하여 **재구성 스크립트 만들기** 대화 상자를 닫습니다.  

12. 마법사의 **호환성 규칙** 페이지에서 **새로 만들기**를 클릭하고 **규칙 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **선택한 설정:** **찾아보기** 를 클릭하고 이전에 지정한 검색 스크립트를 선택합니다.  

    -   **다음 값** 필드에 **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**를 입력합니다.  

    -   **이 설정이 규칙과 호환되지 않는 경우 지정한 재구성 스크립트 실행**옵션을 사용하도록 설정합니다.  

13. 구성 항목 만들기 마법사를 완료합니다.  

14. 방금 만든 구성 항목을 포함하는 구성 기준을 만들고 이를 1단계에서 만든 장치 컬렉션에 배포합니다.  

     구성 기준을 만들고 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 구성 기준을 만드는 방법](../../../compliance/deploy-use/create-configuration-baselines.md)을 참조하세요.  

15. SMSID가 제거된 Mac 컴퓨터에 새 인증서를 설치한 후 다음 명령을 실행하여 새 인증서를 사용하도록 클라이언트를 구성합니다.  

    ```  
    sudo defaults write com.microsoft.ccmclient SubjectName -string <Subject_Name_of_New_Certificate>  
    ```  

16. 동일한 주체 값을 포함하는 인증서가 둘 이상 있는 경우에는 Configuration Manager 클라이언트에 사용하려는 인증서를 식별할 수 있도록 인증서 일련 번호를 지정해야 합니다. 이 작업을 수행하려면 다음 명령을 사용합니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "<일련 번호\>"**.  

     예를 들면 다음과 같습니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

17. Mac 컴퓨터를 다시 시작합니다.  



<!--HONumber=Nov16_HO1-->


