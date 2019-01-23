---
title: 애플리케이션 승인
titleSuffix: Configuration Manager
description: Configuration Manager에서 애플리케이션 승인을 위한 설정 및 동작에 대해 알아봅니다.
ms.date: 12/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 20493c86-6454-4b35-8f22-0d049b68b8bb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 776d0a477d56a178927fb2d09866eacf63b4895a
ms.sourcegitcommit: d5c013a29f53b975fe3a6cb0a41f1e817bd7b235
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54342791"
---
# <a name="approve-applications-in-configuration-manager"></a>Configuration Manager에서 애플리케이션 승인

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 [애플리케이션을 배포](/sccm/apps/deploy-use/deploy-applications)할 때는 설치에 앞서 승인을 요구할 수 있습니다. 사용자가 소프트웨어 센터에서 애플리케이션을 요청하면 Configuration Manager 콘솔에서 요청을 검토합니다. 요청을 승인 또는 거부할 수 있습니다. 



## <a name="bkmk_approval"></a> 승인 설정

애플리케이션 승인 동작은 Configuration Manager 버전에 따라 다릅니다. 다음 승인 설정 중 하나가 애플리케이션 배포의 **배포 설정** 페이지에 표시됩니다.  

#### <a name="require-administrator-approval-if-users-request-this-application"></a>사용자가 이 애플리케이션을 요청한 경우 관리자 승인 필요
*1710 및 이전 버전에 적용*

관리자는 사용자가 설치하기 전에 애플리케이션에 대한 모든 사용자 요청을 승인합니다. 배포 용도가 **필수**인 경우 또는 애플리케이션을 장치 컬렉션에 배포하는 경우에는 이 옵션이 회색으로 표시됩니다.  

애플리케이션 승인 요청은 **소프트웨어 라이브러리** 작업 영역의 **애플리케이션 관리** 아래에 있는 **승인 요청** 노드에 표시됩니다. 요청이 30일 안에 승인되지 않으면 제거됩니다. 클라이언트를 다시 설치하면 보류 중인 승인 요청이 취소될 수 있습니다.  

애플리케이션 설치를 승인한 후 Configuration Manager 콘솔에서 요청을 **거부**할 수 있습니다. 이 작업을 수행해도 클라이언트가 장치에서 애플리케이션을 제거하지는 않습니다. 사용자가 소프트웨어 센터에서 애플리케이션의 새 복사본을 설치하지 못하게 합니다.  


#### <a name="an-administrator-must-approve-a-request-for-this-application-on-the-device"></a>관리자가 장치에서 이 애플리케이션에 대한 요청을 승인해야 함
*1802 이상 버전에 적용 <sup>[참고 1](#bkmk_note1)</sup>*

<a name="bkmk_note1"></a>

> [!Note]  
> **참고 1**: Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요. 
> 
> 이 기능은 사용하도록 설정하지 않으면 이전 환경이 표시됩니다.  

관리자는 사용자가 요청된 장치에 애플리케이션을 설치하기 전에 모든 사용자 요청을 승인합니다. 관리자가 요청을 승인하면 사용자는 해당 장치에만 애플리케이션을 설치할 수 있습니다. 사용자가 다른 장치에 애플리케이션을 설치하려면 다른 요청을 제출해야 합니다. 배포 용도가 **필수**인 경우 또는 애플리케이션을 장치 컬렉션에 배포하는 경우에는 이 옵션이 회색으로 표시됩니다. <!--1357015-->  

> [!Note]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.<!--SCCMDocs issue 646-->  

Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리** 아래의 **승인 요청**을 확인합니다. 이제 각 요청의 **디바이스** 열이 목록에 있습니다. 요청에 대한 작업을 수행하는 경우 애플리케이션 요청 대화 상자에 사용자가 요청을 제출한 장치 이름도 포함됩니다.  

요청이 30일 안에 승인되지 않으면 제거됩니다. 클라이언트를 다시 설치하면 보류 중인 승인 요청이 취소될 수 있습니다.  

애플리케이션 설치를 승인한 후 Configuration Manager 콘솔에서 요청을 **거부**할 수 있습니다. 이 작업을 수행해도 클라이언트가 장치에서 애플리케이션을 제거하지는 않습니다. 사용자가 소프트웨어 센터에서 애플리케이션의 새 복사본을 설치하지 못하게 합니다.  

> [!Important]  
> 버전 1806부터 이전에 승인되어 설치된 애플리케이션에 대한 승인을 취소하는 경우 *동작이 변경*됩니다. 이제 애플리케이션에 대한 요청을 **거부**하면 클라이언트가 사용자의 장치에서 애플리케이션을 제거합니다.<!--1357891-->  



## <a name="bkmk_email-approve"></a> 이메일 알림
<!--1321550-->

1810 버전부터 애플리케이션 승인 요청에 대한 이메일 알림을 구성합니다. 사용자가 애플리케이션을 요청하면 메일을 받게 됩니다. 메일의 링크를 클릭하면 Configuration Manager 콘솔을 사용하지 않고 요청을 승인 또는 거부할 수 있습니다.

애플리케이션에 대한 새 배포를 만드는 동안 요청을 승인하거나 거부할 수 있는 사용자의 이메일 주소를 정의할 수 있습니다. 나중에 이메일 주소 목록을 변경해야 하는 경우 **모니터링** 작업 영역으로 이동하여 **경고**를 확장하고 **구독** 노드를 선택합니다. 애플리케이션 배포와 관련된 **이메일을 통해 애플리케이션 승인** 구독 중 하나에서 **속성**을 선택합니다. 

둘 이상의 경고가 있는 경우 배포와 함께 사용할 경고를 결정할 수 있습니다. 경고 속성을 열고 일반 탭에서 **선택된 경고**의 목록을 봅니다. 배포가 이 구독에 대한 경고로 활성화됩니다. 


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

        1. [Azure Portal](https://portal.azure.com)로 이동하고 **Azure Active Directory**를 선택한 다음, **앱 등록**을 선택합니다.  

        2. Configuration Manager **클라우드 관리** 통합에 대해 만든 **네이티브** 유형 애플리케이션을 선택합니다.  

        3. 앱 속성에서 **설정**을 선택한 다음, **URI 리디렉션**을 선택합니다.  

            1. URI 리디렉션 창에서 `https://<CMG FQDN>/CCM_Proxy_ServerAuth/ImplicitAuth` 경로를 붙여 넣습니다.  

            2. `<CMG FQDN>`을 CMG(클라우드 관리 게이트웨이) 서비스의 FQDN(정규화된 도메인 이름)으로 변경합니다. 예를 들어 GraniteFalls.Contoso.com입니다.  

            3. 그런 다음, **저장**을 선택합니다. **설정** 창을 닫습니다.  

        4. 앱 속성에서 **매니페스트**를 선택합니다.  

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

