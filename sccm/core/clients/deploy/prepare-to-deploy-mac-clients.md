---
title: Mac에 클라이언트 소프트웨어 배포 준비
titleSuffix: Configuration Manager
description: Mac에 Configuration Manager 클라이언트를 배포하기 전 구성 작업입니다.
ms.date: 11/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2285a953-6a86-4ed5-97dd-cd57b02bc1ee
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 748a56155ca7dbbcf6764c72cf5fdf37d24a277b
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32336700"
---
# <a name="prepare-to-deploy-client-software-to-macs"></a>Mac에 클라이언트 소프트웨어 배포 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 단계에 따라 [Mac 컴퓨터에 Configuration Manager 클라이언트를 배포](/sccm/core/clients/deploy/deploy-clients-to-macs)할 준비가 되었는지 확인합니다.

## <a name="mac-prerequisites"></a>Mac 필수 조건

Mac 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 **추가 운영 체제용 클라이언트**를 다운로드합니다.  

**지원되는 버전:**  

-   **Mac OS X 10.6**(Snow Leopard)

-   **Mac OS X 10.7**(Lion)

-   **Mac OS X 10.8**(Mountain Lion)

-   **Mac OS X 10.9**(Mavericks)

-   **Mac OS X 10.9**(Mavericks)  

-   **Mac OS X 10.10**(Yosemite)  

-   **Mac OS X 10.11**(El Capitan)  

-   **Mac OS X 10.12**(macOS Sierra )  

-   **Mac OS X 10.13**(macOS High Sierra)  

## <a name="certificate-requirements"></a>인증서 요구 사항
Mac 컴퓨터에 대해 클라이언트 설치 및 관리를 수행하려면 PKI(공개 키 인프라) 인증서가 필요합니다. PKI 인증서는 상호 인증 및 암호화된 데이터 전송을 사용하여 Mac 컴퓨터와 Configuration Manager 사이트 간의 통신을 안전하게 보호합니다. Configuration Manager에서는 엔터프라이즈 CA(인증 기관) 및 Configuration Manager 등록 지점/등록 프록시 지점 사이트 시스템 역할과 함께 Microsoft 인증서 서비스를 사용하여 사용자 클라이언트 인증서를 요청하고 설치할 수 있습니다. 또는 인증서가 Configuration Manager의 요구 사항을 충족하는 경우 Configuration Manager와는 별도로 컴퓨터 인증서를 요청하고 설치할 수 있습니다.   

Configuration Manager Mac 클라이언트는 항상 인증서 해지 확인을 수행합니다. 이 기능은 사용하지 않도록 설정할 수 없습니다.  

Mac 클라이언트가 CRL을 찾을 수 없어 서버 인증서의 인증서 해지 상태를 확인할 수 없는 경우 Configuration Manager 사이트 시스템에 연결할 수 없습니다. 특히 발급 인증 기관과 다른 포리스트에 있는 Mac 클라이언트의 경우 CRL 디자인을 검토하여 Mac 클라이언트가 사이트 시스템 서버에 연결하기 위해 CDP(CRL 배포 지점)을 찾고 연결할 수 있는지 확인하세요.  

Mac 컴퓨터에 Configuration Manager 클라이언트를 설치하기 전에 클라이언트 인증서 설치 방법을 결정하세요.  

-   [CMEnroll 도구](/sccm/core/clients/deploy/deploy-clients-to-macs#install-the-client-and-then-enroll-the-client-certificate-on-the-mac)를 사용하여 Configuration Manager 등록을 사용합니다. 등록 프로세스는 자동 인증서 갱신을 지원하지 않으므로 설치된 인증서가 만료되기 전에 Mac 컴퓨터를 다시 등록해야 합니다.  

-   [Configuration Manager와 별개의 인증서 요청 및 설치 방법을 사용합니다](/sccm/core/clients/deploy/deploy-clients-to-macs#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager).  

Mac 클라이언트 인증서 요구 사항 및 Mac 컴퓨터를 지원하는 데 필요한 다른 PKI 인증서에 대한 자세한 내용은 [System Center Configuration Manager에 대한 PKI 인증서 요구 사항](../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

Mac 클라이언트는 해당 클라이언트를 관리하는 Configuration Manager 사이트에 자동으로 할당됩니다. 통신이 인트라넷으로 제한된 경우라도 Mac 클라이언트는 인터넷 전용 클라이언트로 설치됩니다. 이러한 클라이언트 구성을 통해 Mac 클라이언트의 할당된 사이트에 있는 사이트 시스템 역할(관리 지점 및 배포 지점)이 인터넷에서 클라이언트 연결을 허용하도록 구성한 경우 Mac 클라이언트가 이러한 사이트 시스템 역할과 통신하게 됩니다. Mac 컴퓨터는 할당된 사이트 외부의 사이트 시스템 역할과는 통신하지 않습니다.  

> [!IMPORTANT]  
>  Configuration Manager Mac 클라이언트를 사용하여 [데이터베이스 복제본](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)을 사용하도록 구성된 관리 지점에 연결할 수는 없습니다.  


## <a name="deploy-a-web-server-certificate-to-site-system-servers"></a>사이트 시스템 서버에 웹 서버 인증서 배포  
이러한 사이트 시스템에 인증서가 없는 경우 다음과 같은 사이트 시스템 역할이 있는 컴퓨터에 웹 서버 인증서를 배포합니다.  

-   관리 지점  

-   배포 지점  

-   등록 지점  

-   등록 프록시 지점  

웹 서버 인증서는 사이트 시스템 속성에서 지정된 인터넷 FQDN을 포함해야 합니다. 서버는 인터넷에서 액세스할 수 없는 경우에도 Mac 컴퓨터를 지원할 수 있습니다. 인터넷 기반 클라이언트 관리가 필요하지 않은 경우 인터넷 FQDN에 대해 인트라넷 FQDN 값을 지정할 수 있습니다.  

관리 지점, 배포 지점 및 등록 프록시 지점용 웹 서버 인증서에 사이트 시스템의 인터넷 FQDN 값을 지정합니다.

이 웹 서버 인증서를 만들고 설치하는 배포의 예는 [IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_webserver2008_cm2012)를 참조하세요.  


## <a name="deploy-a-client-authentication-certificate-to-site-system-servers"></a>사이트 시스템 서버에 클라이언트 인증 인증서 배포  
 이러한 사이트 시스템에 인증서가 없는 경우 다음 사이트 시스템 역할을 호스트하는 컴퓨터에 클라이언트 인증서를 배포합니다.  

-   관리 지점  

-   배포 지점  

 관리 지점에 대한 클라이언트 인증서를 만들고 설치하는 배포의 예는 [Windows 컴퓨터용 클라이언트 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_client2008_cm2012)를 참조하세요.  

 배포 지점에 대한 클라이언트 인증서를 만들고 설치하는 배포의 예는 [배포 지점용 클라이언트 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_clientdistributionpoint2008_cm2012)를 참조하세요.  

>[!IMPORTANT]
>  macOS Sierra를 실행하는 장치에 클라이언트를 배포하려면 관리 지점 인증서의 주체 이름을 관리 지점 서버의 FQDN 등을 사용하여 올바로 구성해야 합니다.

## <a name="prepare-the-client-certificate-template-for-macs"></a>Mac용 클라이언트 인증서 템플릿 준비  

 인증서 템플릿에는 Mac 컴퓨터에 인증서를 등록할 사용자 계정에 대한 **읽기** 및 **등록** 권한이 있어야 합니다.  

 [Mac 컴퓨터용 클라이언트 인증서 배포](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_MacClient_SP1)를 참조하세요.  

## <a name="configure-the-management-point-and-distribution-point"></a>관리 지점 및 배포 지점 구성  
 관리 지점에 다음 옵션을 구성합니다.  

-   HTTPS  

-   인터넷에서 클라이언트 연결 허용. 이 구성 값은 Mac 컴퓨터를 관리하는 데 필요합니다. 하지만 사이트 시스템 서버를 반드시 인터넷에서 액세스할 수 있어야 한다는 것을 의미하지는 않습니다.  

-   모바일 장치 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용  

 클라이언트를 설치하는 데는 배포 지점이 필요하지 않지만 클라이언트를 설치한 후에 이러한 컴퓨터에 소프트웨어를 배포하려면 인터넷에서 클라이언트 연결을 허용하도록 배포 지점을 구성해야 합니다.  


### <a name="to-configure-management-points-and-distribution-points-to-support-macs"></a>Mac을 지원하도록 관리 지점과 배포 지점을 구성하려면  

이 절차를 시작하기 전에 관리 지점과 배포 지점을 실행하는 사이트 시스템 서버에 인터넷 FQDN이 구성되어 있어야 합니다. 이러한 사이트 시스템 서버가 인터넷 기반 클라이언트 관리를 지원하지 않는 경우 인터넷 FQDN 값으로 인트라넷 FQDN을 지정할 수 있습니다.

사이트 시스템 역할이 기본 사이트에 있어야 합니다.  


1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **서버 및 사이트 시스템 역할**을 선택한 다음, 적합한 사이트 시스템 역할이 있는 서버를 선택합니다.  

3.  세부 정보 창에서 **관리 지점**을 마우스 오른쪽 단추로 클릭하고 **역할 속성**을 선택한 후 **관리 지점 속성** 대화 상자에서 다음 옵션을 구성합니다.  

    1.  **HTTPS**를 선택합니다.  

    2.  **인터넷 전용 클라이언트 연결 허용** 또는 **인터넷 및 인트라넷 클라이언트 연결 허용**을 선택합니다. 이러한 옵션에는 인터넷 또는 인트라넷 FQDN이 필요합니다.  

    3.  **모바일 장치 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용**을 선택합니다.  

4.  세부 정보 창에서 **배포 지점**을 마우스 오른쪽 단추로 클릭하고 **역할 속성**을 선택한 후 **배포 지점 속성** 대화 상자에서 다음 옵션을 구성합니다.  

    -   **HTTPS**를 선택합니다.  

    -   **인터넷 전용 클라이언트 연결 허용** 또는 **인터넷 및 인트라넷 클라이언트 연결 허용**을 선택합니다. 이러한 옵션에는 인터넷 또는 인트라넷 FQDN이 필요합니다.  

    -   **인증서 가져오기**를 선택하고 내보낸 클라이언트 배포 지점 인증서 파일을 찾은 다음, 암호를 지정합니다.  

5.  Mac을 사용할 기본 사이트의 모든 관리 지점과 배포 지점에 대해 2단계부터 4단계까지 반복합니다.  

## <a name="configure-the-enrollment-proxy-point-and-the-enrollment-point"></a>등록 프록시 지점 및 등록 지점 구성  
 이러한 사이트 시스템 역할을 둘 다 동일한 사이트에 설치할 수 있지만 동일한 사이트 시스템 서버 또는 동일한 Active Directory 포리스트에 설치할 필요는 없습니다.  

 사이트 시스템 역할 및 고려 사항에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)에서 [사이트 시스템 역할](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles)을 참조하세요.  

 다음 절차는 Mac 컴퓨터를 지원하도록 사이트 시스템 역할을 구성합니다.   

-   [새 사이트 시스템 서버](#new-site-system-server)  

-   [기존 사이트 시스템 서버](#existing-site-system-server)  

###  <a name="new-site-system-server"></a>새 사이트 시스템 서버  

1.  Configuration Manager 콘솔에서 **관리** >  **사이트 구성** > **서버 및 사이트 시스템 역할**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 선택합니다.  

4.  **일반** 페이지에서 사이트 시스템에 대한 일반 설정을 지정합니다.  인터넷 FQDN의 값을 지정해야 합니다. 인터넷에서 서버에 액세스할 수 없는 경우 인트라넷 FQDN을 사용합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **등록 프록시 지점** 및 **등록 지점**을 선택합니다.  

6.  **등록 프록시 지점** 페이지에서 설정을 검토하고 필요한 내용을 변경합니다.  

7.  **등록 지점 설정** 페이지에서 설정을 검토하고 필요한 내용을 변경합니다. 그런 다음 마법사를 완료합니다.  

### <a name="existing-site-system-server"></a>기존 사이트 시스템 서버  

1.  Configuration Manager 콘솔에서 **관리** >  **사이트 구성** > **서버 및 사이트 시스템 역할**을 선택한 다음, Mac을 지원하는 데 사용할 서버를 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 역할 추가**를 선택합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다. 인터넷 FQDN의 값을 지정해야 합니다. 인터넷에서 서버에 액세스할 수 없는 경우 인트라넷 FQDN을 사용합니다.   

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **등록 프록시 지점** 및 **등록 지점**을 선택합니다.  

6.  **등록 프록시 지점** 페이지에서 설정을 검토하고 필요한 내용을 변경합니다.  

7.  **등록 지점 설정** 페이지에서 설정을 검토하고 필요한 내용을 변경합니다. 그런 다음 마법사를 완료합니다.  

## <a name="install-the-reporting-services-point"></a>보고 서비스 지점 설치  
 Mac에 대한 보고서를 실행하려면 [보고 서비스 지점을 설치](../../../core/servers/manage/configuring-reporting.md)합니다.  

### <a name="next-steps"></a>다음 단계

[Mac 컴퓨터에 Configuration Manager 클라이언트 배포](/sccm/core/clients/deploy/deploy-clients-to-macs)  
