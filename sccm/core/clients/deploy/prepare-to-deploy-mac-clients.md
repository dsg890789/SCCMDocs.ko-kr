---
title: Mac에 클라이언트 배포 준비
titleSuffix: Configuration Manager
description: Mac에 Configuration Manager 클라이언트를 배포하기 전 구성 작업입니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2285a953-6a86-4ed5-97dd-cd57b02bc1ee
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b70150fe04900b467ea219da68ac674a18f9834d
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824795"
---
# <a name="prepare-to-deploy-client-software-to-macs"></a>Mac에 클라이언트 소프트웨어 배포 준비

*적용 대상: Configuration Manager(현재 분기)*

다음 단계에 따라 [Mac 컴퓨터에 Configuration Manager 클라이언트를 배포](/sccm/core/clients/deploy/deploy-clients-to-macs)할 준비가 되었는지 확인합니다.



## <a name="mac-prerequisites"></a>Mac 필수 조건

Mac 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/?LinkID=525184)에서 **추가 운영 체제용 클라이언트**를 다운로드합니다.  

지원되는 버전 목록은 [클라이언트 및 디바이스에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers)를 참조하세요.



## <a name="certificate-requirements"></a>인증서 요구 사항

Mac 컴퓨터에 대해 클라이언트 설치 및 관리를 수행하려면 PKI(공개 키 인프라) 인증서가 필요합니다. PKI 인증서는 상호 인증 및 암호화된 데이터 전송을 사용하여 Mac 컴퓨터와 Configuration Manager 사이트 간의 통신을 안전하게 보호합니다. Configuration Manager는 사용자 클라이언트 인증서를 요청하고 설치할 수 있습니다. 엔터프라이즈 인증 기관의 Certificate Services 및 Configuration Manager 등록 지점 및 등록 프록시 지점을 사용합니다. 또한 Configuration Manager와 별개로 컴퓨터 인증서를 요청하여 설치할 수 있습니다. 이 인증서는 Configuration Manager 인증서 요구 사항을 충족해야 합니다.  

Configuration Manager Mac 클라이언트는 항상 인증서 해지를 확인합니다. 이 기능은 사용하지 않도록 설정할 수 없습니다.  

Mac 클라이언트가CRL(인증서 해지 목록)을 찾을 수 없는 경우 Configuration Manager 사이트 시스템에 연결할 수 없습니다. 특히 발급 인증 기관에 대해 서로 다른 포리스트에 있는 Mac 클라이언트의 경우 CRL 디자인을 확인합니다. Mac 클라이언트가 CRL을 찾아 다운로드할 수 있는지 확인합니다.  

Mac 컴퓨터에 Configuration Manager 클라이언트를 설치하기 전에 클라이언트 인증서 설치 방법을 결정하세요.  

-   [CMEnroll 도구](/sccm/core/clients/deploy/deploy-clients-to-macs#client-and-certificate-automation-with-cmenroll)를 사용하여 Configuration Manager 등록을 사용합니다. 등록 프로세스는 자동 인증서 갱신을 지원하지 않습니다. 인증서가 만료되기 전에 Mac 컴퓨터를 다시 등록합니다.  

-   [Configuration Manager와 별개의 인증서 요청 및 설치 방법을 사용합니다](/sccm/core/clients/deploy/deploy-clients-to-macs#bkmk_external).  

Mac 클라이언트 인증서 요구 사항에 대한 자세한 내용은 [Configuration Manager를 위한 PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

Mac 클라이언트는 해당 클라이언트를 관리하는 Configuration Manager 사이트에 자동으로 할당됩니다. 통신이 인트라넷으로 제한된 경우라도 Mac 클라이언트는 인터넷 전용 클라이언트로 설치됩니다. 이 구성은 할당된 해당 사이트에서 인터넷 사용 관리 지점 및 배포 지점과 통신함을 의미합니다. Mac 컴퓨터는 할당된 해당 사이트 외부의 사이트 시스템과는 통신하지 않습니다.  

> [!IMPORTANT]  
>  [데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 사용하도록 구성된 관리 지점에 연결하는 데에는 macOS용 Configuration Manager 클라이언트를 사용할 수 없습니다.  



## <a name="deploy-a-web-server-certificate-to-site-system-servers"></a>사이트 시스템 서버에 웹 서버 인증서 배포  

이러한 사이트 시스템에 인증서가 없는 경우 다음과 같은 사이트 시스템 역할이 있는 컴퓨터에 웹 서버 인증서를 배포합니다.  

-   관리 지점  

-   배포 지점  

-   등록 지점  

-   등록 프록시 지점  

웹 서버 인증서는 사이트 시스템 속성에서 지정된 인터넷 FQDN을 포함해야 합니다. 서버는 인터넷에서 액세스할 수 없는 경우에도 Mac 컴퓨터를 지원할 수 있습니다. 인터넷 기반 클라이언트 관리가 필요하지 않은 경우 인터넷 FQDN에 대해 인트라넷 FQDN 값을 지정할 수 있습니다.  

관리 지점, 배포 지점 및 등록 프록시 지점용 웹 서버 인증서에 사이트 시스템의 인터넷 FQDN 값을 지정합니다.

예제 배포에 대한 자세한 내용은 [IIS를 실행하는 사이트 시스템에 대해 웹 서버 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012)를 참조하세요.  



## <a name="deploy-a-client-authentication-certificate-to-site-system-servers"></a>사이트 시스템 서버에 클라이언트 인증 인증서 배포  

이러한 사이트 시스템에 인증서가 없는 경우 다음 사이트 시스템 역할을 호스트하는 컴퓨터에 클라이언트 인증서를 배포합니다.  

-   관리 지점  

-   배포 지점  

관리 지점에 대한 클라이언트 인증서를 만들고 설치하는 배포의 예제는 [Windows 컴퓨터용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012)를 참조하세요.  

배포 지점에 대한 클라이언트 인증서를 만들고 설치하는 배포의 예제는 [배포 지점용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clientdistributionpoint2008_cm2012)를 참조하세요.  

> [!IMPORTANT]  
>  macOS Sierra를 실행하는 디바이스에 클라이언트를 배포하려면 관리 지점 인증서의 주체 이름을 올바르게 구성해야 합니다. 예를 들어 관리 지점 서버의 FQDN을 사용합니다.  



## <a name="prepare-the-client-certificate-template-for-macs"></a>Mac용 클라이언트 인증서 템플릿 준비  

인증서 템플릿에는 Mac 컴퓨터에 인증서를 등록하는 사용자 계정에 대한 **읽기** 및 **등록** 권한이 있어야 합니다.  

자세한 내용은 [Mac 컴퓨터용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_MacClient_SP1)를 참조하세요.  



## <a name="configure-the-management-point-and-distribution-point"></a>관리 지점 및 배포 지점 구성  

관리 지점에 다음 옵션을 구성합니다.  

-   HTTPS  

-   인터넷에서 클라이언트 연결 허용. 이 구성 값은 Mac 컴퓨터를 관리하는 데 필요합니다. 하지만 사이트 시스템 서버를 반드시 인터넷에서 액세스할 수 있어야 함을 의미하지는 않습니다.  

-   모바일 디바이스 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용  

Mac용 클라이언트를 설치하는 데 배포 지점은 필요하지 않습니다. 클라이언트를 설치한 후 이러한 컴퓨터에 소프트웨어를 배포하려는 경우 인터넷에서 클라이언트 연결을 허용하도록 배포 지점을 구성합니다.  


### <a name="to-configure-management-points-and-distribution-points-to-support-macs"></a>Mac을 지원하도록 관리 지점과 배포 지점을 구성하려면  

이 절차를 시작하기 전에 관리 지점 및 배포 지점을 인터넷 FQDN으로 구성해야 합니다. 이러한 서버가 인터넷 기반 클라이언트 관리를 지원하지 않는 경우 인터넷 FQDN 값으로 인트라넷 FQDN을 지정합니다.

사이트 시스템 역할이 기본 사이트에 있어야 합니다.  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할** 노드를 선택합니다. 그런 다음, 적합한 사이트 시스템 역할이 있는 서버를 선택합니다.  

2.  세부 정보 창에서 **관리 지점** 역할을 선택한 후, 리본 메뉴에서 **속성**을 선택합니다. **관리 지점 속성** 창에서 이러한 옵션을 구성합니다.  

    1.  **HTTPS**를 선택합니다.  

    2.  **인터넷 전용 클라이언트 연결 허용** 또는 **인터넷 및 인트라넷 클라이언트 연결 허용**을 선택합니다. 이러한 옵션에는 인터넷 또는 인트라넷 FQDN이 필요합니다.  

    3.  **모바일 디바이스 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용**을 선택합니다.  

    4. **확인**을 선택하여 이 구성을 저장합니다.  

3.  서버 및 사이트 시스템 역할 노드의 세부 정보 창에서 **배포 지점** 역할을 선택하고 리본 메뉴에서 **속성**을 선택합니다. **관리 지점 속성** 창에서 이러한 옵션을 구성합니다.  

    -   **HTTPS**를 선택합니다.  

    -   **인터넷 전용 클라이언트 연결 허용** 또는 **인터넷 및 인트라넷 클라이언트 연결 허용**을 선택합니다. 이러한 옵션에는 인터넷 또는 인트라넷 FQDN이 필요합니다.  

    -   **인증서 가져오기**를 선택하고 내보낸 클라이언트 배포 지점 인증서 파일을 찾은 다음, 암호를 지정합니다.  

4.  Mac 컴퓨터를 관리하는 기본 사이트의 모든 관리 지점과 배포 지점에 대해 이 단계를 반복합니다.  



## <a name="configure-the-enrollment-proxy-point-and-the-enrollment-point"></a>등록 프록시 지점 및 등록 지점 구성  

동일한 사이트에서 두 역할을 설치합니다. 동일한 사이트 시스템 서버나 동일한 Active Directory 포리스트에 설치할 필요는 없습니다.  

사이트 시스템 역할 배치와 고려 사항에 대한 자세한 내용은 [사이트 시스템 역할](/sccm/core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles#bkmk_planroles)을 참조하세요.  

다음 절차는 Mac 컴퓨터를 지원하는 사이트 시스템 역할을 구성합니다.   

-   [새 사이트 시스템 서버](/sccm/core/servers/deploy/configure/install-site-system-roles#to-install-site-system-roles-on-a-new-site-system-server)  

-   [기존 사이트 시스템 서버](/sccm/core/servers/deploy/configure/install-site-system-roles#bkmk_Install)    

두 경우에서 **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **등록 프록시 지점** 및 **등록 지점**을 선택합니다.  



## <a name="install-the-reporting-services-point"></a>보고 서비스 지점 설치  

자세한 내용은 [보고 서비스 지점 설치](/sccm/core/servers/manage/configuring-reporting)를 참조하세요.  



## <a name="next-steps"></a>다음 단계

[Mac 컴퓨터에 Configuration Manager 클라이언트 배포](/sccm/core/clients/deploy/deploy-clients-to-macs)  
