---
title: 애플리케이션 승인
titleSuffix: Configuration Manager
description: Configuration Manager에서 애플리케이션 승인을 위한 설정 및 동작에 대해 알아봅니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 20493c86-6454-4b35-8f22-0d049b68b8bb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a650fd5517fb86108d230cc997c8586520826e7
ms.sourcegitcommit: 16dd488c51b5cf01a7dd4204f7d40ee9ae0abe85
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68743589"
---
# <a name="approve-applications-in-configuration-manager"></a>Configuration Manager에서 애플리케이션 승인

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 [애플리케이션을 배포](/sccm/apps/deploy-use/deploy-applications)할 때는 설치에 앞서 승인을 요구할 수 있습니다. 사용자가 소프트웨어 센터에서 애플리케이션을 요청하면 Configuration Manager 콘솔에서 요청을 검토합니다. 요청을 승인 또는 거부할 수 있습니다.

## <a name="bkmk_approval"></a> 승인 설정

응용 프로그램 승인 동작은 권장 되는 [선택적 앱 승인 환경을](#bkmk_opt)사용 하는지 여부에 따라 달라 집니다. 다음 승인 설정 중 하나가 애플리케이션 배포의 **배포 설정** 페이지에 표시됩니다.  

### <a name="bkmk_opt"></a> 관리자가 디바이스에서 이 애플리케이션에 대한 요청을 승인해야 함

> [!Note]  
> Configuration Manager는 기본적으로 이 기능을 활성화하지 않습니다. 사용하기 전에 선택적 기능인 **디바이스당 사용자에 대한 애플리케이션 요청 승인**을 사용하도록 설정합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.
>
> 이 기능은 사용하도록 설정하지 않으면 [이전 환경](#bkmk_prior)이 표시됩니다.  

관리자는 사용자가 요청된 디바이스에 애플리케이션을 설치하기 전에 모든 사용자 요청을 승인합니다. 관리자가 요청을 승인하면 사용자는 해당 디바이스에만 애플리케이션을 설치할 수 있습니다. 사용자가 다른 디바이스에 애플리케이션을 설치하려면 다른 요청을 제출해야 합니다. 배포 용도가 **필수**인 경우 또는 애플리케이션을 디바이스 컬렉션에 배포하는 경우에는 이 옵션이 회색으로 표시됩니다. <!--1357015-->  

> [!Note]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.<!--SCCMDocs issue 646-->  

Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리** 아래의 **애플리케이션 요청**을 확인합니다. 버전 1902 및 이전 버전에서는이 노드를 **승인 요청**이라고 합니다. 이제 각 요청의 **디바이스** 열이 목록에 있습니다. 요청에 대한 작업을 수행하는 경우 애플리케이션 요청 대화 상자에 사용자가 요청을 제출한 디바이스 이름도 포함됩니다.

요청이 30일 안에 승인되지 않으면 제거됩니다. 클라이언트를 다시 설치하면 보류 중인 승인 요청이 취소될 수 있습니다.  

장치 컬렉션에 대 한 배포에 대 한 승인이 필요한 경우 앱이 소프트웨어 센터에 표시 되지 않습니다. 사용자 컬렉션에 대 한 배포에 대 한 승인이 필요한 경우 앱이 소프트웨어 센터에 표시 됩니다. 클라이언트 설정인 **소프트웨어 센터에서 승인 되지 않은 응용 프로그램 숨기기**를 사용 하 여 사용자가 계속 숨길 수 있습니다. 자세한 내용은 [소프트웨어 센터 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-center)을 참조하세요.

애플리케이션 설치를 승인한 후 Configuration Manager 콘솔에서 요청을 **거부**할 수 있습니다. 이 작업을 수행해도 클라이언트가 디바이스에서 애플리케이션을 제거하지는 않습니다. 사용자가 소프트웨어 센터에서 애플리케이션의 새 복사본을 설치하지 못하게 합니다.  

> [!Important]  
> 버전 1806부터 이전에 승인되어 설치된 애플리케이션에 대한 승인을 취소하는 경우 *동작이 변경*됩니다. 이제 애플리케이션에 대한 요청을 **거부**하면 클라이언트가 사용자의 디바이스에서 애플리케이션을 제거합니다.<!--1357891-->  

1906 버전부터 콘솔에서 앱 요청을 승인한 후 거부한 경우 이제 다시 승인할 수 있습니다. 승인 후에는 앱이 클라이언트에 다시 설치됩니다.  <!-- 4224910 -->

[Approve-CMApprovalRequest](https://docs.microsoft.com/powershell/module/configurationmanager/approve-cmapprovalrequest?view=sccm-ps) PowerShell cmdlet을 사용하여 승인 프로세스를 자동화합니다. 1902 버전부터 이 cmdlet에는 **InstallActionBehavior** 매개 변수가 포함되어 있습니다. 이 매개 변수를 사용하여 애플리케이션을 즉시 설치할지, 아니면 업무외 시간에 설치할지를 지정합니다.<!-- SCCMDocs-pr issue #3418 -->

1906부터 승인이 필요한 배포를 확인할 수 있습니다. **응용 프로그램** 노드에서 앱을 선택 합니다. 세부 정보 창에서 **배포** 탭으로 전환합니다. 기본적으로 표시 되는 새 열은 **승인이 필요**합니다.

#### <a name="bkmk_retry"></a>사전 승인된 애플리케이션의 설치 다시 시도

<!--4336307-->
1906 버전부터 이전에 사용자 또는 디바이스에 대해 승인한 앱의 설치를 다시 시도할 수 있습니다. 승인 옵션은 사용 가능한 배포에만 해당합니다. 사용자 앱을 제거할 경우 또는 최초 설치 프로세스가 실패한 경우 Configuration Manager가 그 상태를 다시 평가하지 않고 다시 설치합니다. 이 기능을 통해 엔지니어는 지원을 요청하는 사용자에 대해 앱 설치를 신속하게 다시 시도할 수 있습니다.

1. 응용 프로그램 개체에 대 한 **승인** 권한이 있는 사용자로 Configuration Manager 콘솔을 엽니다. 예를 들어, **애플리케이션 관리자** 또는 **응애플리케이션 작성자** 기본 제공 역할에 이 권한이 있습니다.

1. 승인이 필요한 앱을 배포하고 승인합니다.

    > [!Tip]  
    > 또는 [장치에 대 한 응용 프로그램을 설치](/sccm/apps/deploy-use/install-app-for-device)합니다. 디바이스에서 앱에 대한 승인 요청을 만듭니다.  

응용 프로그램이 제대로 설치 되지 않거나 사용자가 앱을 제거 하는 경우 다음 프로세스를 사용 하 여 다시 시도 하세요.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **애플리케이션 관리**를 확장하고 **애플리케이션 요청** 노드를 선택합니다. 버전 1902 및 이전 버전에서는이 노드를 **승인 요청**이라고 합니다.

1. 이전에 승인된 앱을 선택합니다. 리본 메뉴의 승인 요청 그룹에서 **설치 다시 시도**를 선택합니다.

#### <a name="other-app-approval-resources"></a>다른 앱 승인 리소스

- [ConfigMgr 1810의 애플리케이션 승인 개선 사항](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/Application-approval-improvements-in-ConfigMgr-1810/ba-p/303534)
- [Configuration Manager의 애플리케이션 승인 프로세스 업데이트](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/Updates-to-the-application-approval-process-in-Configuration/ba-p/275048)

### <a name="bkmk_prior"></a> 사용자가 이 애플리케이션을 요청하는 경우 관리자 승인 필요

> [!Note]  
> 권장 되는 [선택적 앱 승인 환경을](#bkmk_opt)사용 하지 않는 경우이 환경이 적용 됩니다.

관리자는 사용자가 설치하기 전에 애플리케이션에 대한 모든 사용자 요청을 승인합니다. 배포 용도가 **필수**인 경우 또는 애플리케이션을 디바이스 컬렉션에 배포하는 경우에는 이 옵션이 회색으로 표시됩니다.  

애플리케이션 승인 요청은 **소프트웨어 라이브러리** 작업 영역의 **애플리케이션 관리** 아래에 있는 **애플리케이션 요청** 노드에 표시됩니다. 버전 1902 및 이전 버전에서는이 노드를 **승인 요청**이라고 합니다. 요청이 30일 안에 승인되지 않으면 제거됩니다. 클라이언트를 다시 설치하면 보류 중인 승인 요청이 취소될 수 있습니다.  

애플리케이션 설치를 승인한 후 Configuration Manager 콘솔에서 요청을 **거부**할 수 있습니다. 이 작업을 수행해도 클라이언트가 디바이스에서 애플리케이션을 제거하지는 않습니다. 사용자가 소프트웨어 센터에서 애플리케이션의 새 복사본을 설치하지 못하게 합니다.  


## <a name="bkmk_email-approve"></a> 이메일 알림

<!--1321550-->

1810 버전부터 애플리케이션 승인 요청에 대한 이메일 알림을 구성합니다. 사용자가 애플리케이션을 요청하면 메일을 받게 됩니다. 메일의 링크를 클릭하면 Configuration Manager 콘솔을 사용하지 않고 요청을 승인 또는 거부할 수 있습니다.

애플리케이션에 대한 새 배포를 만드는 동안 요청을 승인하거나 거부할 수 있는 사용자의 이메일 주소를 정의할 수 있습니다. 나중에 이메일 주소 목록을 변경해야 하는 경우 **모니터링** 작업 영역으로 이동하여 **경고**를 확장하고 **구독** 노드를 선택합니다. 애플리케이션 배포와 관련된 **이메일을 통해 애플리케이션 승인** 구독 중 하나에서 **속성**을 선택합니다.

둘 이상의 경고가 있는 경우 배포와 함께 사용할 경고를 결정할 수 있습니다. 경고 속성을 열고 일반 탭에서 **선택된 경고**의 목록을 봅니다. 배포가 이 구독에 대한 경고로 활성화됩니다.

사용자는 소프트웨어 센터의 요청에 주석을 추가할 수 있습니다. 이 주석은 Configuration Manager 콘솔의 애플리케이션 요청에 표시됩니다. 1902 버전부터 해당 주석은 이메일에도 표시됩니다. 이메일에 이 주석이 포함되면 승인자가 요청을 승인하거나 거부하는 데 더 나은 결정을 내릴 수 있습니다.<!--3594063-->


### <a name="prerequisites"></a>필수 구성 요소

#### <a name="to-send-email-notifications-and-take-action-on-internal-network"></a>이메일 알림을 보내고 내부 네트워크에 대한 작업 수행

이 필수 구성 요소에 따라 받는 사람은 요청 알림이 담긴 이메일을 받게 됩니다. 내부 네트워크에 있는 경우 이메일에서 요청을 승인하거나 거부할 수도 있습니다.

- [선택적 기능](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)인 **디바이스당 사용자에 대한 응용 프로그램 요청 승인**을 사용하도록 설정합니다.  

- [경고에 대한 메일 알림](/sccm/core/servers/manage/use-alerts-and-the-status-system#to-configure-email-notification-for-alerts)을 구성합니다.  

- SMS 공급자에서 인증서를 사용하도록 설정합니다.<!--SCCMDocs-pr issue 3135--> 다음 옵션 중 하나를 사용합니다.  

    - [향상된 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http) 사용(추천)  

        > [!Note]  
        > 사이트에서 SMS 공급자에 대한 인증서를 만들면 클라이언트의 웹 브라우저에서 신뢰할 수 없게 됩니다. 보안 설정에 따라 애플리케이션 요청에 응답할 때 보안 경고가 표시될 수 있습니다.  

    - SMS 공급자 역할을 호스팅하는 서버의 IIS에 있는 443 포트에 PKI 기반 인증서를 수동으로 바인딩  

#### <a name="to-take-action-from-internet"></a>인터넷에서 작업 수행

이 추가 옵션 필수 구성 요소에서는 받는 사람이 인터넷 액세스가 있는 어디서나 요청을 승인 또는 거부할 수 있습니다.

- 클라우드 관리 게이트웨이를 통해 SMS 공급자 관리 서비스를 사용하도록 설정합니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할** 노드를 선택합니다. SMS 공급자 역할이 있는 서버를 선택합니다. 세부 정보 창에서 **SMS 공급자** 역할을 선택하고 사이트 역할 탭의 리본에서 **속성**을 선택합니다. **관리 서비스에 대해 Configuration Manager 클라우드 관리 게이트웨이 트래픽 허용** 옵션을 선택합니다.  

    - SMS 공급자에는 **.NET 4.5.2** 이상이 필요합니다.  

- [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)  

- **클라우드 관리**를 위해 [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)에 사이트를 등록합니다.  

    - [Azure AD 사용자 검색](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)을 사용하도록 설정합니다.  

    - Azure AD에서 설정을 수동으로 구성합니다.  

        1. *전역 관리자* 권한을 가진 사용자로 [Azure Portal](https://portal.azure.com)로 이동합니다. **Azure Active Directory**로 이동해서 **앱 등록**을 선택합니다.  

        2. Configuration Manager **클라우드 관리** 통합에 대해 만든 애플리케이션을 선택합니다.  

        3. **관리** 메뉴에서 **인증**을 선택 합니다.  

            1. **URI 리디렉션** 섹션에서 다음 경로를 붙여넣습니다. `https://<CMG FQDN>/CCM_Proxy_ServerAuth/ImplicitAuth`  

            2. `<CMG FQDN>`을 CMG(클라우드 관리 게이트웨이) 서비스의 FQDN(정규화된 도메인 이름)으로 변경합니다. 예를 들어 GraniteFalls.Contoso.com입니다.  

            3. 그런 다음, **저장**을 선택합니다.  

        4. **관리** 메뉴에서 **매니페스트**를 선택 합니다.  

            1. 매니페스트 편집 창에서 **oauth2AllowImplicitFlow** 속성을 찾습니다.  

            2. 값을 **true**로 변경합니다. 예를 들어, 전체 줄은 `"oauth2AllowImplicitFlow": true,`와 비슷하게 보입니다.  

            3. **저장**을 선택합니다.  


### <a name="configure-email-approval"></a>이메일 승인 구성

1. Configuration Manager 콘솔에서 사용자 컬렉션에 대해 사용 가능하도록 [애플리케이션을 배포](/sccm/apps/deploy-use/deploy-applications)합니다. **배포 설정** 페이지에서 승인을 위해 사용하도록 설정합니다. 그런 다음, 알림을 받을 이메일 주소를 하나 이상 입력합니다. 이메일 주소는 세미콜론(`;`)으로 구분합니다.  

     > [!Note]  
     > 메일을 받는 Azure AD 조직의 모든 사용자가 요청을 승인할 수 있습니다. 작업을 수행하게 하려는 경우가 아니면 다른 사용자에게 메일을 전달하지 마세요.  

2. 사용자로서 소프트웨어 센터에서 애플리케이션을 요청합니다.  

3. 5분 안에 이메일 알림이 도착합니다. 이메일 콘텐츠는 다음 예제와 유사합니다.  

![애플리케이션 승인을 위한 예제 메일 알림](media/1321550-email.png)

> [!Note]  
> 승인 또는 거부 링크는 일회용으로 제공됩니다. 예를 들어 알림을 받도록 그룹 별칭을 구성합니다. Meg가 요청을 승인합니다. 이제 Bruce가 요청을 거부할 수 없습니다.  

문제 해결을 위해 사이트 서버의 **NotiCtrl.log** 파일을 검토합니다.


## <a name="maintenance"></a>유지 관리

Configuration Manager는 애플리케이션 승인 요청에 관한 정보를 사이트 데이터베이스에 저장합니다. 취소 또는 거부된 요청에 대해서는 사이트가 30일 후 요청 기록을 삭제합니다. **오래된 애플리케이션 요청 데이터 삭제** [사이트 유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks)으로 삭제 동작을 구성할 수 있습니다. 사이트가 승인 또는 대기 중인 애플리케이션 요청을 절대 삭제하지 않습니다.
