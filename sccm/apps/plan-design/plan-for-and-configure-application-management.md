---
title: "응용 프로그램 관리 계획 및 구성 | Microsoft 문서"
description: "System Center Configuration Manager에서 응용 프로그램 배포에 필요한 종속성을 구현하고 구성합니다."
ms.custom: na
ms.date: 01/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2be84a1d-ebb9-47ae-8982-c66d5b92a52a
caps.latest.revision: 13
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: d2a12edcc6bc7413558e25b694b69133c2496019
ms.openlocfilehash: 0a38ea116e589425048f6c46378df46ecc0d375b


---
# <a name="plan-for-and-configure-application-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 응용 프로그램 관리 계획 및 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 내용을 따르면 System Center Configuration Manager에서 응용 프로그램을 배포하기 위해 필요한 종속성을 구현할 수 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

|종속성|추가 정보|  
|------------------|----------------------|  
|응용 프로그램 카탈로그 웹 사이트 지점, 응용 프로그램 카탈로그 웹 서비스 지점, 관리 지점, 배포 지점 등을 실행하는 사이트 시스템 서버에 IIS(인터넷 정보 서비스)가 필요합니다.|이 요구 사항에 대한 자세한 내용은 [지원되는 구성](../../core/plan-design/configs/supported-configurations.md)을 참조하세요.|  
|Configuration Manager에서 등록된 모바일 장치|응용 프로그램을 모바일 장치에 배포하기 위해 코드 서명할 경우 버전 3 템플릿(**Windows Server 2008, Enterprise Edition**)을 사용하여 생성된 인증서는 사용하지 마세요. 이 인증서 템플릿을 사용하면 모바일 장치용 Configuration Manager 응용 프로그램과 호환되지 않는 인증서가 만들어집니다.<br /><br /> 모바일 장치 응용 프로그램에 대해 Active Directory 인증서 서비스를 사용하여 코드 서명할 경우 버전 3 인증서 템플릿은 사용하지 마세요.|  
|자동으로 사용자 장치 선호도를 만들려면 클라이언트에서 로그인 이벤트를 감사하도록 구성해야 합니다.|Configuration Manager 클라이언트는 PC 보안 이벤트 로그에서 **성공** 유형의 로그온 이벤트를 읽어 자동 사용자 장치 선호도를 확인합니다.  이러한 이벤트는 다음 두 감사 정책에서 사용하도록 설정됩니다.<br>**계정 로그온 이벤트 감사**<br>**로그온 이벤트 감사**<br>사용자와 장치 간의 관계를 자동으로 만들려면 클라이언트 컴퓨터에 이러한 두 설정이 사용하도록 설정되어 있어야 합니다. Windows 그룹 정책을 사용하여 이러한 설정을 구성할 수 있습니다.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성   

|종속성|추가 정보|  
|------------------|----------------------|  
|관리 지점|클라이언트는 관리 지점에 연결하여 클라이언트 정책을 다운로드하고, 콘텐츠를 찾고, 응용 프로그램 카탈로그에 연결합니다.<br /><br /> 클라이언트는 관리 지점에 액세스할 수 없는 경우 응용 프로그램 카탈로그를 사용할 수 없습니다.|  
|배포 지점|계층에 배포 지점이 하나 이상 있어야만 클라이언트에 응용 프로그램을 배포할 수 있습니다. 기본적으로 사이트 서버에는 표준 설치 중 활성화된 배포 지점 사이트 역할이 있습니다. 배포 지점의 수와 위치는 각 기업의 특정 요구 사항에 따라 달라집니다.<br /><br /> 배포 지점을 설치하고 콘텐츠를 관리하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|클라이언트 설정|여러 클라이언트 설정에서는 응용 프로그램이 클라이언트에 설치되는 방식과 클라이언트상의 사용자 환경을 제어합니다. 이러한 클라이언트 설정은 다음과 같습니다.<br /><br /><ul><li>컴퓨터 에이전트</li><li>컴퓨터 다시 시작</li><li>소프트웨어 배포</li><li>사용자 및 장치 선호도</li></ul> 이러한 클라이언트 설정에 대한 자세한 내용은 [클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)를 참조하세요.<br /><br /> 클라이언트 설정을 구성하는 방법에 대한 자세한 내용은 [클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.|  
|응용 프로그램 카탈로그의 경우:<br /><br /> 검색된 사용자 계정|사용자가 응용 프로그램 카탈로그에서 응용 프로그램을 확인하고 요청하려면 먼저 Configuration Manager에서 해당 사용자를 검색해야 합니다. 자세한 내용은 [검색 실행](/sccm/core/servers/deploy/configure/run-discovery)을 참조하세요.|  
|가상 응용 프로그램 실행을 위한 App-V 4.6 SP1 이상의 클라이언트|Configuration Manager에서 가상 응용 프로그램을 만들려면 클라이언트 컴퓨터에 App-V 4.6 SP1 이상의 클라이언트가 설치되어 있어야 합니다.<br /><br /> 또한 가상 응용 프로그램을 배포하려면 먼저 기술 자료 [문서 2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322)에 설명된 핫픽스로 App-V 클라이언트를 업데이트해야 합니다.|  
|응용 프로그램 카탈로그 웹 서비스 지점|응용 프로그램 카탈로그 웹 서비스 지점은 소프트웨어 라이브러리의 사용 가능한 소프트웨어에 대한 정보를 응용 프로그램 카탈로그 웹 사이트에 제공하는 사이트 시스템 역할입니다.<br /><br /> 이 사이트 시스템 역할을 구성하는 방법에 대한 자세한 내용은 이 문서의 [소프트웨어 센터 및 응용 프로그램 카탈로그 구성(Windows PC만 해당)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only)을 참조하세요.|  
|응용 프로그램 카탈로그 웹 사이트 지점|응용 프로그램 카탈로그 웹 사이트 지점은 사용자에게 사용 가능한 소프트웨어 목록을 제공하는 사이트 시스템 역할입니다.<br /><br /> 이 사이트 시스템 역할을 구성하는 방법에 대한 자세한 내용은 이 문서의 [소프트웨어 센터 및 응용 프로그램 카탈로그 구성(Windows PC만 해당)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only)을 참조하세요.|  
|보고 서비스 지점|응용 프로그램 관리를 위해 Configuration Manager에서 보고서를 사용하려면 먼저 보고 서비스 지점을 설치하고 구성해야 합니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager의 보고](../../core/servers/manage/reporting.md)를 참조하세요.|  
|응용 프로그램 관리를 위한 보안 권한|응용 프로그램을 관리하려면 다음 보안 권한이 있어야 합니다.<br /><br /> **응용 프로그램 작성자** 보안 역할에는 Configuration Manager에서 응용 프로그램을 만들고, 변경하고, 사용 중지하는 데 필요한 앞에 나열된 권한이 포함되어 있습니다.<br /><br /> **응용 프로그램을 배포하려면:**<br /><br /> **응용 프로그램 배포 관리자** 보안 역할에는 Configuration Manager에서 응용 프로그램을 배포하는 데 필요한 앞에 나열된 권한이 포함되어 있습니다.<br /><br /> **응용 프로그램 관리자** 보안 역할에는 **응용 프로그램 작성자** 및 **응용 프로그램 배포 관리자** 보안 역할의 모든 권한이 포함되어 있습니다.<br /><br /> 자세한 내용은 [역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.|  

##  <a name="configure-software-center-and-the-application-catalog-windows-pcs-only"></a>소프트웨어 센터 및 응용 프로그램 카탈로그 구성(Windows PC만 해당)  

 이제 System Center Configuration Manager에서 사용자가 설정을 변경하고, 응용 프로그램을 찾아서 설치하는 방법에 대한 두 가지 옵션이 제공됩니다.  

-   **새로운 소프트웨어 센터** - 새로운 소프트웨어 센터의 모양이 최신 스타일로 변경되었습니다. 이전에는 Silverlight 종속 응용 프로그램 카탈로그에서만 표시되었던 앱(사용자가 사용할 수 있는 앱)이 이제 소프트웨어 센터의 **응용 프로그램** 탭 아래에 표시됩니다. 소프트웨어 센터의 **설치 상태** 탭에 있는 링크를 사용하면 응용 프로그램 카탈로그에 계속 액세스할 수 있습니다.  

     클라이언트 설정인 **컴퓨터 에이전트** > **새 소프트웨어 센터 사용**을 활성화하여 새로운 소프트웨어 센터를 사용하도록 클라이언트를 구성할 수 있습니다.  

    > [!IMPORTANT]  
    >  더 이상 응용 프로그램 카탈로그에 연결할 필요는 없지만 여전히 응용 프로그램 카탈로그 웹 사이트 지점 및 응용 프로그램 카탈로그 웹 서비스 지점을 다음 섹션에 설명된 대로 구성해야 합니다.  

-   **이전 소프트웨어 센터 및 응용 프로그램 카탈로그** - 기본적으로 사용자가 소프트웨어 센터의 이전 버전에 연결하고 응용 프로그램 카탈로그(Silverlight 사용 웹 브라우저 필요)에 연결하여 사용 가능한 응용 프로그램을 찾아볼 수 있습니다.  

 사용하도록 선택한 버전과 상관없이 Windows PC에 Configuration Manager 클라이언트를 설치할 때 소프트웨어 센터가 자동으로 설치됩니다.  

    > [!TIP]  
    >  사용자에게 표시되는 소프트웨어 센터의 버전은 Configuration Manager 클라이언트 설정에 따라 다릅니다. 따라서 컬렉션에 배포하는 사용자 지정 클라이언트 설정에 따라 사용되는 버전을 유연하게 제어할 수 있습니다. 

    > [!IMPORTANT]
    > 향후 몇 개월 동안 소프트웨어 센터의 이전 버전이 제거될 예정이므로 이전 버전은 더 이상 사용할 수 없게 됩니다.
    > 클라이언트 설정인 **컴퓨터 에이전트** > **새 소프트웨어 센터 사용**을 활성화하여 새로운 소프트웨어 센터를 사용하도록 클라이언트를 구성할 수 있습니다. 

## <a name="steps-to-install-and-configure-the-application-catalog-and-software-center"></a>응용 프로그램 카탈로그 및 소프트웨어 센터를 설치하고 구성하는 단계  

> [!IMPORTANT]  
>  이러한 단계를 수행하기 전에 앞에 나열된 모든 필수 조건을 충족하는지 확인합니다.  

|단계|세부 정보|추가 정보|  
|-----------|-------------|----------------------|  
|**1단계:** HTTPS 연결을 사용할 경우 사이트 시스템 서버에 웹 서버 인증서를 배포했는지 확인합니다.|응용 프로그램 카탈로그 웹 사이트 지점 및 응용 프로그램 카탈로그 웹 서비스 지점을 실행할 사이트 시스템 서버에 웹 서버 인증서를 배포합니다.<br /><br /> 그리고, 클라이언트가 인터넷에서 응용 프로그램 카탈로그를 사용하도록 하려면 적어도 하나 이상의 관리 지점 사이트 시스템 서버에 웹 서버 인증서를 배포하고 인터넷에서 클라이언트 연결이 가능하도록 인증서를 구성합니다.|인증서 요구 사항에 대한 자세한 내용은 [PKI 인증서 요구 사항](../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.|  
|**2단계:** 관리 지점에 연결하는 데 클라이언트 PKI 인증서를 사용하려면 클라이언트 컴퓨터에 클라이언트 인증 인증서를 배포합니다.|클라이언트는 응용 프로그램 카탈로그에 연결하기 위해 클라이언트 PKI 인증서를 사용하지 않지만 관리 지점에 연결해야 응용 프로그램 카탈로그를 사용할 수 있습니다. 다음 시나리오에서는 클라이언트 컴퓨터에 클라이언트 인증 인증서를 배포해야 합니다.<br /><br /><ul><li>인트라넷의 모든 관리 지점에서 HTTPS 클라이언트 연결만 허용합니다.</li><li>클라이언트가 인터넷에서 응용 프로그램 카탈로그에 연결합니다.</li></ul>|인증서 요구 사항에 대한 자세한 내용은 [PKI 인증서 요구 사항](../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.|  
|**3단계:** 응용 프로그램 카탈로그 웹 서비스 지점과 응용 프로그램 카탈로그 웹 사이트를 설치하고 구성합니다.|두 사이트 시스템 역할은 모두 같은 사이트에 설치해야 합니다. 같은 사이트 시스템 서버나 같은 Active Directory 포리스트에 설치할 필요는 없습니다. 그러나 응용 프로그램 카탈로그 웹 서비스 지점은 사이트 데이터베이스와 같은 포리스트에 있어야 합니다.|사이트 시스템 역할 배치에 대한 자세한 내용은 [사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)을 참조하세요.<br /><br /> 응용 프로그램 카탈로그 웹 서비스 지점과 응용 프로그램 카탈로그 웹 사이트 지점을 구성하려면 **3단계: 응용 프로그램 카탈로그 사이트 시스템 역할 설치 및 구성**을 참조하세요.|  
|**4단계:** 응용 프로그램 카탈로그 및 소프트웨어 센터에 대한 클라이언트 설정을 구성합니다.|모든 사용자가 같은 설정을 사용하도록 하려면 기본 클라이언트 설정을 구성합니다. 아니면 특정 컬렉션에 대한 사용자 지정 클라이언트 설정을 구성합니다.|클라이언트 설정에 대한 자세한 내용은 [클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)를 참조하세요.<br /><br /> 이러한 클라이언트 설정을 구성하는 방법에 대한 자세한 내용은 **4단계: 응용 프로그램 카탈로그 및 소프트웨어 센터에 대한 클라이언트 설정 구성**을 참조하세요.|  
|**5단계:** 응용 프로그램 카탈로그가 작동하는지 확인합니다.|응용 프로그램 카탈로그는 브라우저나 소프트웨어 센터에서 직접 사용할 수 있습니다.|**5단계: 응용 프로그램 카탈로그가 작동하는지 확인**을 참조하세요.|  

## <a name="supplemental-procedures-to-install-and-configure-the-application-catalog-and-software-center"></a>응용 프로그램 카탈로그 및 소프트웨어 센터를 설치하고 구성하는 보완 절차  
 위의 표에 설명된 단계에 보완 절차가 필요한 경우 다음 정보를 사용하세요.  

###  <a name="step-3-install-and-configure-the-application-catalog-site-system-roles"></a>3단계: 응용 프로그램 카탈로그 사이트 시스템 역할 설치 및 구성  
 다음 절차는 응용 프로그램 카탈로그의 사이트 시스템 역할을 구성합니다. 새 사이트 시스템 서버를 설치할지 아니면 기존 사이트 시스템 서버를 사용할지에 따라 다음 두 절차 중 하나를 선택합니다.  

> [!NOTE]  
>  응용 프로그램 카탈로그는 보조 사이트나 중앙 관리 사이트에 설치할 수 없습니다.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-new-site-system-server"></a>응용 프로그램 카탈로그 사이트 시스템을 설치 및 구성하려면 새 사이트 시스템 서버  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **서버 및 사이트 시스템 역할**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 선택합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 선택합니다.  

    > [!TIP]  
    >  클라이언트 컴퓨터에서 인터넷을 통해 응용 프로그램 카탈로그를 사용하도록 하려면 인터넷 FQDN(정규화된 도메인 이름)을 지정합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **응용 프로그램 카탈로그 웹 서비스 지점** 및 **응용 프로그램 카탈로그 웹 사이트 지점**을 선택하고 **다음**을 선택합니다.  

6.  마법사를 마칩니다.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-existing-site-system-server"></a>응용 프로그램 카탈로그 사이트 시스템을 설치 및 구성하려면 기존 사이트 시스템 서버  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **서버 및 사이트 시스템 역할**을 선택한 다음 응용 프로그램 카탈로그에 사용할 서버를 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 역할 추가**를 선택합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 선택합니다.  

    > [!TIP]  
    >  클라이언트 컴퓨터에서 인터넷을 통해 응용 프로그램 카탈로그를 사용하도록 하려면 인터넷 FQDN(정규화된 도메인 이름)을 지정합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **응용 프로그램 카탈로그 웹 서비스 지점** 및 **응용 프로그램 카탈로그 웹 사이트 지점**을 선택하고 **다음**을 선택합니다.  

6.  마법사를 마칩니다.  

7. 상태 메시지를 사용하고 로그 파일을 검토하여 이러한 사이트 시스템 역할이 설치되었는지 확인합니다.  

    상태 메시지: **SMS_PORTALWEB_CONTROL_MANAGER** 및 **SMS_AWEBSVC_CONTROL_MANAGER**구성 요소를 사용합니다.  

    예를 들어 **SMS_PORTALWEB_CONTROL_MANAGER** 의 상태 ID **1015** 는 사이트 구성 요소 관리자가 응용 프로그램 카탈로그 웹 사이트 지점에 제대로 설치되었음을 확인합니다.  

    로그 파일: **SMSAWEBSVCSetup.log** 및 **SMSPORTALWEBSetup.log**를 검색합니다.  

    자세한 내용을 보려면 **awebsvcMSI.log** 및 **portlwebMSI.log** 로그 파일을 검색하세요.  

###  <a name="step-4-configure-the-client-settings-for-the-application-catalog-and-software-center"></a>4단계: 응용 프로그램 카탈로그 및 소프트웨어 센터에 대한 클라이언트 설정 구성  
 이 절차는 계층의 모든 장치에 적용할 응용 프로그램 카탈로그 및 소프트웨어 센터의 기본 클라이언트 설정을 구성합니다. 이러한 설정을 일부 장치에만 적용하려면 사용자 지정 클라이언트 설정을 만들어 특정 설정을 적용할 장치가 포함된 컬렉션에 배포하면 됩니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md) 문서의 [사용자 지정 클라이언트 설정을 만들어 배포하는 방법](../../core/clients/deploy/configure-client-settings.md#create-and-deploy-custom-client-settings) 섹션을 참조하세요.  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

4.  사용자 알림, 응용 프로그램 카탈로그 및 소프트웨어 센터와 관련된 설정을 검토하고 구성합니다. 예를 들면 다음과 같습니다.  

    1.  **컴퓨터 에이전트** 그룹:  

        -   **기본 응용 프로그램 카탈로그 웹 사이트 지점**  

        -   **기본 응용 프로그램 카탈로그 웹 사이트를 Internet Explorer의 신뢰할 수 있는 사이트 영역에 추가**  

        -   **소프트웨어 센터에 표시된 조직 이름**  

            > [!TIP]  
            >  응용 프로그램 카탈로그에 표시되는 조직 이름을 지정하고 웹 사이트 테마를 구성하려면 응용 프로그램 카탈로그 웹 사이트 속성의 **사용자 지정** 탭을 사용합니다.  

        -   **새 소프트웨어 센터 사용** - 사용자가 응용 프로그램 카탈로그(Silverlight 지원 웹 브라우저 필요)에 액세스할 필요 없이 사용 가능한 앱을 검색하여 설치할 수 있는 새로운 소프트웨어 센터를 사용하려는 경우 **예**로 설정합니다.  

        -   **설치 권한**  

        -   **새 배포에 대한 알림 표시**  

    2.  **전원 관리** 그룹:  

        -   **사용자가 전원 관리에서 장치를 제외할 수 있도록 허용**  

    3.  **원격 도구** 그룹:  

        -   **소프트웨어 센터에서 사용자가 정책 또는 알림 설정 변경 가능**  

    4.  **사용자 및 장치 선호도** 그룹:  

        -   **사용자가 기본 장치를 정의할 수 있도록 허용**  

    > [!NOTE]  
    >  클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)를 참조하세요.  

5.  **확인**을 선택하여 **기본 클라이언트 설정** 대화 상자를 닫습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [클라이언트를 관리하는 방법](../../core/clients/manage/manage-clients.md)을 참조하세요.

#### <a name="how-to-customize-software-center-branding"></a>소프트웨어 센터 브랜딩을 사용자 지정하는 방법

소프트웨어 센터에 대한 사용자 지정 브랜딩은 다음 규칙에 따라 적용됩니다.

1. 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되지 않은 경우 소프트웨어 센터에서 **컴퓨터 에이전트** 클라이언트 설정 **소프트웨어 센터에 표시되는 조직 이름**에 지정된 조직 이름을 표시합니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.
2. 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되어 있는 경우 소프트웨어 센터에서 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할 속성에 지정된 조직 이름 및 색을 표시합니다. 자세한 내용은 [응용 프로그램 카탈로그 웹 사이트 지점에 대한 옵션 구성](https://docs.microsoft.com/en-us/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#BKMK_ApplicationCatalog_Website)을 참조하세요.
3. Microsoft Intune 구독을 구성하고 Configuration Manager에 연결한 경우 소프트웨어 센터에서 Intune 구독 속성에 지정된 조직 이름, 색 및 회사 로고를 표시합니다. 자세한 내용은 [Configuring the Microsoft Intune subscription](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription)을 참조하십시오.

> [!IMPORTANT]  
>  소프트웨어 센터 브랜딩은 14일마다 Intune 서비스와 동기화되므로 Intune에서 적용한 변경 내용이 Configuration Manager에 표시될 때까지 시간이 지연될 수도 있습니다.

###  <a name="step-5-verify-that-the-application-catalog-is-operational"></a>5단계: 응용 프로그램 카탈로그가 작동하는지 확인  
 응용 프로그램 카탈로그가 작동하는지 확인하려면 다음 절차를 수행하세요. 응용 프로그램 카탈로그는 브라우저나 소프트웨어 센터에서 직접 사용할 수 있습니다.  

> [!NOTE]  
>  응용 프로그램 카탈로그를 사용하려면 Microsoft Silverlight가 필요합니다. Microsoft Silverlight는 Configuration Manager 클라이언트 필수 조건으로, 자동으로 설치됩니다. Configuration Manager 클라이언트가 설치되지 않은 컴퓨터를 통해 브라우저에서 직접 응용 프로그램 카탈로그를 사용하는 경우 먼저 컴퓨터에 Microsoft Silverlight가 설치되어 있는지 확인하세요.  

> [!TIP]  
>  설치 후에 응용 프로그램 카탈로그가 잘못된 방식으로 작동하는 원인 중 가장 일반적인 원인은 필수 구성 요소가 누락되었기 때문입니다. 응용 프로그램 카탈로그 사이트 시스템 역할의 사이트 시스템 역할 필수 구성 요소를 확인합니다. [지원되는 구성](../../core/plan-design/configs/supported-configurations.md) 문서를 참조하여 이 확인을 수행할 수 있습니다.  

> [!NOTE]  
>  도메인 관리자 계정을 사용하여 로그인한 경우에는 Configuration Manager 클라이언트에서 알림 메시지(예: 새 소프트웨어를 사용할 수 있음을 나타내는 메시지)가 표시되지 않습니다.  

### <a name="to-use-the-application-catalog-directly-from-a-browser"></a>브라우저에서 직접 응용 프로그램 카탈로그를 사용하려면  

-   브라우저에서 응용 프로그램 카탈로그 웹 사이트 주소를 입력하고 해당 웹 페이지에 **응용 프로그램 카탈로그**, **내 응용 프로그램 요청**, **내 장치** 등 세 가지 탭이 표시되는지 확인합니다.  

     응용 프로그램 카탈로그에 대해 아래 목록에 나와 있는 적합한 주소를 선택하여 사용합니다. 여기서 &lt;서버&gt;는 컴퓨터 이름, 인트라넷 FQDN 또는 인터넷 FQDN입니다.  

    -   HTTPS 클라이언트 연결 및 기본 사이트 시스템 역할 설정: **https://&lt;서버&gt;/CMApplicationCatalog**  

    -   HTTP 클라이언트 연결 및 기본 사이트 시스템 역할 설정: **http://&lt;서버&gt;/CMApplicationCatalog**  

    -   HTTPS 클라이언트 연결 및 사용자 지정 사이트 시스템 역할 설정: **https://&lt;서버&gt;:&lt;포트&gt;/&lt;웹 응용 프로그램 이름&gt;**  

    -   HTTP 클라이언트 연결 및 사용자 지정 사이트 시스템 역할 설정: **http://&lt;서버&gt;:&lt;포트&gt;/&lt;웹 응용 프로그램 이름&gt;**  

### <a name="to-use-the-application-catalog-from-software-center-does-not-apply-to-the-new-version-of-software-center"></a>소프트웨어 센터에서 응용 프로그램 카탈로그를 사용하려면(새 버전의 소프트웨어 센터에는 적용 안 됨)  

1.  클라이언트 컴퓨터에서 **시작** > **모든 프로그램** > **Microsoft System Center 2012** > **Configuration Manager** > **소프트웨어 센터**를 선택합니다.  

2.  이전에 소프트웨어 센터의 조직 이름을 클라이언트 설정으로 구성한 경우 지정한 대로 표시되는지 확인합니다.  

3.  **응용 프로그램 카탈로그에서 다른 소프트웨어 찾기**를 선택하고 해당 웹 페이지에 **응용 프로그램 카탈로그**, **내 응용 프로그램 요청**, **내 장치** 등 세 가지 탭이 표시되는지 확인합니다.  

> [!WARNING]  
>  응용 프로그램 카탈로그 사이트 시스템 역할을 설치한 후에 소프트웨어 센터에서 **응용 프로그램 카탈로그에서 다른 소프트웨어 찾기** 링크를 선택하자마자 바로 응용 프로그램 카탈로그가 표시되지는 않습니다. 응용 프로그램 카탈로그 사이트 시스템 역할을 설치하고 나서 최대 25시간 후나 클라이언트에서 다음에 해당 클라이언트 정책을 다운로드한 후에야 소프트웨어 센터에서 응용 프로그램 카탈로그를 사용할 수 있게 됩니다.  



<!--HONumber=Jan17_HO3-->


