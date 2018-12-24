---
title: 클라우드 배포 지점 설치
titleSuffix: Configuration Manager
description: 이러한 단계를 사용하여 Configuration Manager에서 클라우드 배포 지점을 설정합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a2d39617db7f2ea9a61e73a3c21cc2509fed2f07
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52456620"
---
# <a name="install-a-cloud-distribution-point-for-configuration-manager"></a>Configuration Manager의 클라우드 배포 지점 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Microsoft Azure에서 Configuration Manager 클라우드 배포 지점을 설치하는 단계를 자세히 설명합니다. 여기에는 다음과 같은 섹션이 포함됩니다.
- [시작하기 전에](#bkmk_before) 
- [설치](#bkmk_setup)
- [DNS 구성](#bkmk_dns)
- [사이트 서버 프록시 설치](#bkmk_proxy)
- [콘텐츠 배포 및 클라이언트 구성](#bkmk_client)
- [관리 및 모니터링](#bkmk_monitor)
- [수정](#bkmk_modify)
- [고급 문제 해결](#bkmk_tshoot) 



## <a name="bkmk_before"></a> 시작하기 전에

[클라우드 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) 문서를 먼저 읽으세요. 해당 문서는 클라우드 배포 지점을 계획 및 디자인하는 데 용이합니다. 

다음 검사 목록을 사용하여 클라우드 배포 지점을 만드는 데 필요한 정보 및 필수 구성 요소가 있는지 확인합니다.  

- 사이트 서버는 Azure에 연결할 수 있습니다. 네트워크가 프록시를 사용하는 경우 [사이트 시스템 역할을 구성](#bkmk_proxy)합니다.  

- 사용할 **Azure 환경**입니다. 예: Azure 공용 클라우드 또는 Azure 미국 정부 클라우드  

- 1806 버전 및 *권장 버전*부터 **Azure Resource Manager 배포**를 사용합니다. 요구 사항은 다음과 같습니다.<!--1322209-->  

    - **클라우드 관리**를 위한 [Azure Active Directory](/sccm/core/servers/deploy/configure/azure-services-wizard)와의 통합. Azure AD 사용자 검색은 필요하지 않습니다.  

    - Azure **구독 ID**.  

    - Azure **리소스 그룹**.  

    - **구독 관리자 계정**은 마법사를 실행하는 동안 로그인해야 합니다.  

- Azure **클래식 서비스 배포**를 사용하려면 다음 요구 사항이 필요합니다.  
    > [!Important]  
    > 1810 버전부터 Azure의 클래식 서비스 배포는 Configuration Manager에서 사용되지 않습니다. 클라우드 관리 게이트웨이에 대해 Azure Resource Manager 배포를 사용하기 시작합니다. 자세한 내용은 [CMG 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager)을 참조하세요.  

    - Azure **구독 ID**.  

    - .CER 및 .PFX 파일 둘 다로 내보낸 Azure **관리 인증서**. Azure 구독 관리자는 .CER 관리 인증서를 [Azure Portal](https://portal.azure.com)의 구독에 추가해야 합니다.  

- .PFX 파일로 내보낸 **서버 인증 인증서**.  

- 클라우드 배포 지점에 대해 전역적으로 고유한 **서비스 이름**.  

    > [!TIP]  
    > 이 서비스 이름을 사용하는 서버 인증 인증서를 요청하기 전에 원하는 Azure 도메인 이름이 고유한지 확인합니다. 예를 들어 *WallaceFalls.CloudApp.Net*이 있습니다. [Microsoft Azure Portal](https://portal.azure.com)에 로그인합니다. **리소스 만들기**를 선택하고, **계산** 범주를 선택한 다음, **클라우드 서비스**를 선택합니다. **DNS 이름** 필드에서 원하는 접두사를 입력합니다(예: *WallaceFalls*). 인터페이스에는 도메인 이름을 사용할 수 있는지, 아니면 다른 서비스에서 이미 사용 중인지 여부가 표시됩니다. 포털에서 서비스를 만들지 말고, 이 프로세스를 사용하여 이름 가용성을 확인하세요.  
 
- 이 배포에 대한 Azure **지역**입니다.  



##  <a name="bkmk_setup"></a> 설치   

[디자인](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_topology)에서 결정된 이 클라우드 배포 지점을 호스트하는 사이트에서 이 절차를 수행합니다.  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **클라우드 배포 지점**을 선택합니다. 리본에서 **클라우드 배포 지점 만들기**를 선택합니다.  

2.  클라우드 배포 지점 만들기 마법사의 **일반** 페이지에서 다음 설정을 구성합니다.  

    1. 먼저 **Azure 환경**을 지정합니다.  

    2. 1806 버전 및 *권장 버전*부터 배포 메서드로 **Azure Resource Manager 배포**를 선택합니다. **로그인**을 선택하여 Azure 구독 관리자 계정으로 인증합니다. 마법사가 Azure AD 통합 필수 구성 요소 중에 저장된 정보로 나머지 필드를 자동으로 채웁니다. 여러 구독을 소유하고 있는 경우 사용할 구독의 **구독 ID**를 선택합니다.  

    > [!Note]  
    > 1810 버전부터 Azure의 클래식 서비스 배포는 Configuration Manager에서 사용되지 않습니다. 
    > 
    > 클래식 서비스 배포를 사용해야 하는 경우 이 페이지에서 해당 옵션을 선택합니다. 먼저 Azure **구독 ID**를 입력합니다. 그런 다음, **찾아보기**를 선택하고 Azure 관리 인증서에 대한 .PFX 파일을 선택합니다.  

3.  **다음**을 선택합니다. 사이트가 Azure에 대한 연결을 테스트할 때까지 기다립니다.  

4.  **설정** 페이지에서 다음과 같은 설정을 지정한 다음, **다음**을 선택합니다.  

    - **지역**: 클라우드 배포 지점을 만들 Azure 지역을 선택합니다.  

    - **리소스 그룹**(Azure Resource Manager 배포 메서드만)  

        - **기존 항목 사용**: 드롭다운 목록에서 기존 리소스 그룹을 선택합니다.  

        - **새로 만들기**: Azure 구독에서 만들려는 새 리소스 그룹 이름을 입력합니다.  

    - **기본 사이트**: 이 배포 지점에 콘텐츠를 배포하는 기본 사이트를 선택합니다.

    - **인증서 파일**: **찾아보기**를 선택하고 이 클라우드 배포 지점의 서버 인증 인증서에 대한 .PFX 파일을 선택합니다. 이 인증서의 일반 이름은 필수 **서비스 FQDN** 및 **서비스 이름** 필드를 채웁니다.  

        > [!NOTE]  
        > 클라우드 배포 지점 서버 인증 인증서는 와일드카드를 지원합니다. 와일드카드 인증서를 사용하는 경우 **서비스 FQDN** 필드의 별표(*)를 서비스에 원하는 호스트 이름으로 바꿉니다.  

5. **경고** 페이지에서 저장소 할당량, 전송 할당량 및 Configuration Manager에서 이러한 할당량에 대해 경고를 생성할 비율(%)을 설정합니다. **다음**을 선택합니다.  

6. 마법사를 완료합니다.  


### <a name="monitor-installation"></a>설치 모니터링  

사이트가 클라우드 배포 지점에 대해 새로 호스팅되는 서비스를 만들기 시작합니다. 마법사를 닫은 후 Configuration Manager 콘솔에서 클라우드 배포 지점의 설치 진행률을 모니터링합니다. 또한 기본 사이트 서버에서 **CloudMgr.log** 파일을 모니터링합니다. 필요한 경우 Azure Portal에서 클라우드 서비스의 프로비전을 모니터링합니다.  

> [!NOTE]  
>  Azure에서 새 배포 지점을 프로비전하는 데 최대 30분 정도 걸릴 수 있습니다. 저장소 계정이 프로비전될 때까지 **CloudMgr.log** 파일에서 다음 메시지가 반복됩니다.  
> `Waiting for check if container exists. Will check again in 10 seconds`  
> 저장소 계정을 프로비전한 후 서비스가 생성 및 구성됩니다.  


### <a name="verify-installation"></a>설치 확인

다음 방법을 사용하여 클라우드 배포 지점 설치가 완료되었는지 확인합니다.  

- Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **Cloud Services**를 확장하고 **클라우드 배포 지점** 노드를 선택합니다. 목록에서 새로운 클라우드 배포 지점을 찾습니다. 상태 열이 **준비** 상태여야 합니다.  

- Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다. **시스템 상태**를 확장하고 **구성 요소 상태** 노드를 선택합니다. **SMS_CLOUD_SERVICES_MANAGER** 구성 요소에 모든 메시지를 표시하고 상태 메시지 ID **9409**를 찾습니다.  

- 필요한 경우 Azure Portal로 이동합니다. 클라우드 배포 지점의 **배포**가 **준비** 상태로 표시됩니다.  



##  <a name="bkmk_dns"></a> DNS 구성  

클라이언트에서 클라우드 배포 지점을 사용할 수 있으려면 클라우드 배포 지점의 이름을 Azure가 관리하는 IP 주소로 확인할 수 있어야 합니다. 관리 지점은 클라우드 배포 지점의 **서비스 FQDN**을 제공합니다. 클라우드 배포 지점은 Azure에 **서비스 이름**으로 존재합니다. 클라우드 배포 지점 속성의 **설정** 탭에서 이러한 값을 확인합니다. 

> [!Note]  
> 콘솔의 **클라우드 배포 지점** 노드에는 **서비스 이름**이라는 열이 포함되지만, 실제로는 **서비스 FQDN** 값을 표시합니다. 두 값을 모두 보려면 클라우드 배포 지점에 대한 **속성**을 열고 **설정** 탭으로 전환합니다.  

<!-- Remove based on feedback from RoYork
If you issue the server authentication certificate from your PKI, you may directly specify the Azure **Service name**. For example, `WallaceFalls.cloudapp.net`. When you specify this certificate in the Create Cloud Distribution Point Wizard, both the **Service FQDN** and **Service name** properties are the same. In this scenario, you don't need to configure DNS. The name that clients receive from the management point is the same name as the service in Azure.  
-->

서버 인증 인증서 일반 이름에는 도메인 이름이 포함되어야 합니다. 이 이름은 공용 공급자의 인증서를 구입하는 경우 필수입니다. PKI에서 이 인증서를 발급하는 경우 권장됩니다. 예: `WallaceFalls.contoso.com` 클라우드 배포 지점 만들기 마법사에서 이 인증서를 지정하는 경우 일반 이름은 **서비스 FQDN** 속성(`WallaceFalls.contoso.com`)을 채웁니다. **서비스 이름**은 동일한 호스트 이름(`WallaceFalls`)을 사용하고 Azure 도메인 이름(`cloudapp.net`)에 추가합니다. 이 시나리오에서 클라이언트는 Azure **서비스 이름**(`WallaceFalls.cloudapp.net`)에 대한 사용자 도메인의 **서비스 FQDN**(`WallaceFalls.contoso.com`)을 확인해야 합니다. 이러한 이름에 매핑할 CNAME 별칭을 만듭니다.


### <a name="create-cname-alias"></a>CNAME 별칭 만들기

조직의 공용 인터넷 연결 DNS에서 CNAME(정식 이름) 레코드를 만듭니다. 이 레코드는 Azure **서비스 이름**에 대해 클라이언트가 수신하는 클라우드 배포 지점의 **서비스 FQDN** 속성의 별칭을 만듭니다. 예를 들어 `WallaceFalls.cloudapp.net`에 대한 `WallaceFalls.contoso.com`의 새 CNAME 레코드를 만듭니다.  


### <a name="client-name-resolution-process"></a>클라이언트 이름 확인 프로세스

다음 프로세스는 클라이언트가 클라우드 배포 지점의 이름을 확인하는 방법을 보여 줍니다.  

1. 클라이언트는 콘텐츠 원본 목록에서 클라우드 배포 지점의 **서비스 FQDN**을 가져옵니다. 예: `WallaceFalls.contoso.com`  

2. Azure **서비스 이름**에 대한 CNAME 별칭을 사용하여 서비스 FQDN을 확인하는 DNS를 쿼리합니다. 예: `WallaceFalls.cloudapp.net`  

3. Azure 공용 IP 주소에 대해 Azure 서비스 이름을 확인하는 DNS를 다시 쿼리합니다.   

4. 클라이언트는 클라우드 배포 지점과 통신을 시작하는 데 이 IP 주소를 사용합니다.   

5. 클라우드 배포 지점은 클라이언트에 대한 서버 인증 인증서를 나타냅니다. 클라이언트는 유효성 검사에 인증서의 신뢰 체인을 사용합니다.  



## <a name="bkmk_proxy"></a> 사이트 서버 프록시 설치  

클라우드 배포 지점을 관리하는 기본 사이트 서버는 Azure와 통신해야 합니다. 조직이 프록시 서버를 사용하여 인터넷 액세스를 제어하는 경우 이 프록시를 사용하도록 기본 사이트 서버를 구성합니다.   

자세한 내용은 [프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support)을 참조하세요.  



## <a name="bkmk_client"></a> 콘텐츠 배포 및 클라이언트 구성

다른 온-프레미스 배포 지점과 마찬가지로 클라우드 배포 지점에 콘텐츠를 배포합니다. 관리 지점은 클라이언트가 요청한 콘텐츠가 없는 경우 외에는 콘텐츠 위치의 목록에 클라우드 배포 지점을 포함하지 않습니다. 자세한 내용은 [콘텐츠 배포 및 관리](/sccm/core/servers/deploy/configure/deploy-and-manage-content)를 참조하세요. 

다른 온-프레미스 배포 지점과 마찬가지로 클라우드 배포 지점을 관리합니다. 이러한 작업에는 콘텐츠 패키지를 관리하고 배포 지점 그룹에 할당하는 것이 포함됩니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points)을 참조하세요.

기본 클라이언트 설정은 자동으로 클라이언트가 클라우드 배포 지점을 사용하도록 설정합니다. 다음 클라이언트 설정을 사용하여 계층의 모든 클라우드 배포 지점에 대한 액세스를 제어합니다.  

   - **클라우드 설정** 그룹에서 **클라우드 배포 지점에 대한 액세스 허용** 설정을 수정합니다.  

       - 기본적으로 이 설정은 **예**로 설정됩니다.  

       - 사용자와 디바이스 모두에 대해 이 설정을 수정 및 배포합니다.  



## <a name="bkmk_monitor"></a> 관리 및 모니터링  

다른 온-프레미스 배포 지점과 마찬가지로 클라우드 배포 지점에 배포하는 콘텐츠를 모니터링합니다. 자세한 내용은 [콘텐츠 모니터링](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed)을 참조하세요. 

### <a name="bkmk_alerts"></a> 경고  

Configuration Manager는 주기적으로 Azure 서비스를 확인합니다. 서비스가 활성화되지 않거나 구독 또는 인증서 문제가 있는 경우 Configuration Manager에서 경고를 생성합니다. 

클라우드 배포 지점에 저장할 데이터 양 및 배포 지점에서 클라이언트가 다운로드하는 데이터 양의 임계값을 구성합니다. 이러한 임계값에 대한 경고를 사용하면 적시에 클라우드 서비스를 중지 또는 삭제하거나, 클라우드 배포 지점에 저장하는 콘텐츠를 조정하거나, 클라이언트가 서비스를 사용할 수 있는 항목을 수정할 수 있습니다. 

- **저장소 경고 임계값**: 저장소 경고 임계값은 클라우드 배포 지점에 저장할 데이터 또는 콘텐츠 양에 대한 상한을 GB 단위로 설정합니다. 기본적으로 이 임계값은 2,000GB입니다. Configuration Manager는 사용 가능한 나머지 공간이 지정한 수준에 도달할 때 경고 및 중요한 알림을 생성합니다. 기본적으로 임계값 50% 및 90%에서 이러한 경고가 발생합니다.  

- **월간 전송 경고 임계값**: 월간 전송 경고 임계값은 30일의 기간 동안 배포 지점에서 클라이언트로 전송되는 콘텐츠 양을 모니터링하는 데 도움이 됩니다. 기본적으로 이 임계값은 10,000GB입니다. 전송이 사용자가 정의하는 값에 도달하는 경우 경고 및 중요한 알림이 사이트에서 발생합니다. 기본적으로 임계값 50% 및 90%에서 이러한 경고가 발생합니다.  

    > [!IMPORTANT]  
    >  Configuration Manager에서는 데이터 전송을 모니터링하지만 지정된 전송 경고 임계값을 넘어 데이터가 전송되는 것을 중지하지 않습니다.  

설치하는 동안 각 클라우드 배포 지점에 대한 임계값을 지정하거나 클라우드 배포 지점 속성의 **경고** 탭을 사용합니다.  

> [!NOTE]  
>  클라우드 배포 지점에 대한 경고는 Azure의 사용량 통계에 따라 달라지며, 사용할 수 있기까지 최대 24시간이 걸릴 수 있습니다. Azure를 위한 저장소 분석의 자세한 내용은 [저장소 분석](https://docs.microsoft.com/rest/api/storageservices/storage-analytics)을 참조하세요.  

클라우드 배포 지점을 모니터링하는 기본 사이트에서는 1시간 주기로 Azure에서 트랜잭션 데이터를 다운로드합니다. 이 트랜잭션 데이터를 사이트 서버의 `CloudDP-<ServiceName>.log` 파일에 저장합니다. 그런 다음, Configuration Manager에서 이 정보를 각 클라우드 배포 지점의 저장소 및 전송 할당량과 비교하여 평가합니다. 데이터 전송이 경고 또는 중요한 알림에 대해 지정된 양에 도달하거나 이를 초과하면 Configuration Manager에서 적절한 경고를 생성합니다.  

> [!WARNING]  
>  사이트에서는 데이터 전송에 대한 정보가 한 시간마다 Azure에서 다운로드되기 때문에 Configuration Manager가 데이터에 액세스하여 경고를 발생시키기 전에 사용량이 경고 또는 위험 임계값을 초과할 수도 있습니다.  



## <a name="bkmk_modify"></a> 수정

Configuration Manager 콘솔의 **관리** 작업 영역의 **Cloud Services**에 있는 **클라우드 배포 지점** 노드에서 배포 지점에 대한 세부 정보를 확인합니다. 배포 지점을 선택하고 **속성**을 선택하여 자세한 내용을 확인합니다.  

클라우드 배포 지점의 속성을 편집하는 경우 다음 탭에는 편집할 설정이 포함됩니다.  

#### <a name="settings"></a>설정  

- **설명**  

- **인증서 파일**: 서버 인증 인증서가 만료되기 전에 동일한 일반 이름으로 새 인증서를 발급합니다. 그런 다음, 사용을 시작할 수 있도록 여기서 서비스에 대한 새 인증서를 추가합니다. 인증서가 만료된 경우 클라이언트는 서비스를 신뢰 및 사용하지 않습니다.  

#### <a name="alerts"></a>경고
저장소 및 월간 전송 경고에 대한 데이터 임계값을 조정합니다.  

#### <a name="content"></a>Content
온-프레미스 배포 지점과 동일한 방식으로 콘텐츠를 관리합니다.  


### <a name="redeploy-the-service"></a>서비스를 다시 배포

다음 구성 등의 보다 중요한 변경 내용은 서비스를 다시 배포해야 합니다.
- 클래식 배포 메서드에서 Azure Resource Manager
- 구독
- 서비스 이름
- 개인에서 공개 PKI
- Azure 지역

1806 버전부터는 클래식 배포 메서드에서 기존 클라우드 배포 지점이 설치되어 있는 경우 Azure Resource Manager 배포 메서드를 사용하려면 새 클라우드 배포 지점을 배포해야 합니다. 두 가지 옵션 중에서 선택할 수 있습니다.

- 동일한 서비스 이름을 다시 사용하려면:  

    1. 먼저 클래식 클라우드 배포 지점을 삭제합니다. 다른 클라우드 배포 지점이 없으면 클라이언트에서 콘텐츠를 가져오지 못할 수 있습니다.  

    2. Resource Manager 배포를 사용하여 새 클라우드 배포 지점을 만듭니다. 동일한 서버 인증 인증서를 다시 사용합니다.  

    3. 새 클라우드 배포 지점에 필요한 소프트웨어 패키지 콘텐츠를 배포합니다.  

- 새로운 서비스 이름을 사용하려면:  

    1. Resource Manager 배포를 사용하여 새 클라우드 배포 지점을 만듭니다. 새로운 서버 인증 인증서를 사용합니다.  

    2. 새 클라우드 배포 지점에 필요한 소프트웨어 패키지 콘텐츠를 배포합니다.  

    3. 클래식 클라우드 배포 지점을 삭제합니다.

> [!Tip]  
> 클라우드 배포 지점 <!--SCCMDocs issue #611-->의 현재 배포 모델을 확인하려면  
> 1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **클라우드 배포 지점** 노드를 선택합니다.  
> 2. **배포 모델** 특성을 목록 보기에 열로 추가합니다. Resource Manager 배포의 경우 이 특성은 **Azure Resource Manager**입니다.  


### <a name="stop-or-start-the-cloud-service-on-demand"></a>주문형 클라우드 서비스를 중지하거나 시작합니다.

Configuration Manager 콘솔에서 클라우드 배포 지점을 언제든지 중지합니다. 이 작업은 즉시 서비스에서 클라이언트로 추가 콘텐츠가 다운로드되지 않습니다. 클라이언트에 대한 액세스를 복원하려면 Configuration Manager 콘솔에서 클라우드 서비스를 다시 시작합니다. 예를 들어 데이터 임계값에 도달하면 클라우드 서비스를 중지합니다.  

클라우드 배포 지점을 중지하는 경우 클라우드 서비스는 저장소 계정에서 콘텐츠를 삭제하지 않습니다. 또한 사이트 서버에서 클라우드 배포 지점으로 추가 콘텐츠를 전송하지 않도록 합니다. 관리 지점은 클라이언트에 클라우드 배포 지점을 유효한 콘텐츠 원본으로 계속 반환합니다. 

클라우드 배포 지점을 중지하려면 다음 절차를 사용합니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **Cloud Services**를 확장하고 **클라우드 배포 지점** 노드를 선택합니다.  

2. 클라우드 배포 지점을 선택합니다. Azure에서 실행되는 클라우드 서비스를 중지하려면 리본에서 **서비스 중지**를 선택합니다.  

3. 클라우드 배포 지점을 다시 시작하려면 **서비스 시작**을 선택합니다.  


### <a name="delete-a-cloud-distribution-point"></a>클라우드 배포 지점 삭제

클라우드 배포 지점을 제거하려면 Configuration Manager 콘솔에서 배포 지점을 선택한 다음, **삭제**를 선택합니다.  

계층 구조에서 클라우드 배포 지점을 삭제하는 경우 Configuration Manager가 Azure의 클라우드 서비스에서 콘텐츠를 제거합니다. 

Azure의 모든 구성 요소를 수동으로 제거하면 시스템에 불일치가 발생할 수 있습니다. 이 상태는 분리된 정보를 남기고, 예기치 않은 동작이 발생할 수 있습니다.



## <a name="bkmk_tshoot"></a> 고급 문제 해결

클라우드 배포 지점을 사용하여 문제 해결을 위해 Azure VM에서 진단 로그를 수집해야 하는 경우 다음 PowerShell 샘플을 사용하여 구독에 대한 서비스 진단 확장을 사용하도록 설정합니다.<!--514275-->  

``` PowerShell
# Change these variables for your Azure environment. The current values are provided as examples. You can find the values for these from the Azure portal.
$storage_name="4780E38368358502‬‭23C071" # The name of the storage account that goes with the CloudDP
$key="3jSyvMssuTyAyj5jWHKtf2bV5JF^aDN%z%2g*RImGK8R4vcu3PE07!P7CKTbZhT1Sxd3l^t69R8Cpsdl1xhlhZtl" # The storage access key from the Storage Account view
$service_name="4780E38368358502‬‭23C071" # The name of the cloud service for the CloudDP, which for a Cloud DP is the same as the storage name
$azureSubscriptionName="8ba1cb83-84a2-457e-bd37-f78d2dd371ee" # The subscription name the tenant is using 
$subscriptionId="8ba1cb83-84a2-457e-bd37-f78d2dd371ee" # The subscription ID the tenant is using 

# This variable is the path to the config file on the local computer.
$public_config="F:\PowerShellDiagFile\diagnostics.wadcfgx"

# These variables are for the Azure management certificate. Install it in the Current User certificate store on the system running this script. 
$thumbprint="dac9024f54d8f6df94935fb1732638ca6ad77c13" # The thumbprint of the Azure management certificate 
$mycert = Get-Item cert:\\CurrentUser\My\$thumbprint

Set-AzureSubscription -SubscriptionName $azureSubscriptionName -SubscriptionId $subscriptionId -Certificate $mycert

Select-AzureSubscription $azureSubscriptionName

Set-AzureServiceDiagnosticsExtension -StorageAccountName $storage_name -StorageAccountKey $key -DiagnosticsConfigurationPath $public_config –ServiceName $service_name -Slot 'Production' -Verbose
```


다음 샘플은 위의 PowerShell 스크립트에서 **public_config** 변수에서 참조되는 예제 **diagnostics.wadcfgx** 파일입니다. 자세한 내용은 [Azure 진단 확장 구성 스키마](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics-schema)를 참조하세요.  

``` XML
<?xml version="1.0" encoding="utf-8"?>
<PublicConfig xmlns="http://schemas.microsoft.com/ServiceHosting/2010/10/DiagnosticsConfiguration">
  <WadCfg>
    <DiagnosticMonitorConfiguration overallQuotaInMB="4096">
      <Directories scheduledTransferPeriod="PT1M">
        <IISLogs containerName ="wad-iis-logfiles" />
        <FailedRequestLogs containerName ="wad-failedrequestlogs" />
      </Directories>
      <WindowsEventLog scheduledTransferPeriod="PT1M">
        <DataSource name="Application!*" />
      </WindowsEventLog>
      <Logs scheduledTransferPeriod="PT1M" scheduledTransferLogLevelFilter="Information" />
      <CrashDumps dumpType="Full">
        <CrashDumpConfiguration processName="WaAppAgent.exe" />
        <CrashDumpConfiguration processName="WaIISHost.exe" />
        <CrashDumpConfiguration processName="WindowsAzureGuestAgent.exe" />
        <CrashDumpConfiguration processName="WaWorkerHost.exe" />
        <CrashDumpConfiguration processName="DiagnosticsAgent.exe" />
        <CrashDumpConfiguration processName="w3wp.exe" />
      </CrashDumps>
      <PerformanceCounters scheduledTransferPeriod="PT1M">
        <PerformanceCounterConfiguration counterSpecifier="\Memory\Available MBytes" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\Web Service(_Total)\ISAPI Extension Requests/sec" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\Web Service(_Total)\Bytes Total/Sec" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\ASP.NET Applications(__Total__)\Requests/Sec" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\ASP.NET Applications(__Total__)\Errors Total/Sec" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\ASP.NET\Requests Queued" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\ASP.NET\Requests Rejected" sampleRate="PT3M" />
        <PerformanceCounterConfiguration counterSpecifier="\Processor(_Total)\% Processor Time" sampleRate="PT3M" />
      </PerformanceCounters>
    </DiagnosticMonitorConfiguration>
  </WadCfg>
</PublicConfig>
```

