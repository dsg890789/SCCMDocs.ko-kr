---
title: 프록시 서버 지원
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 시스템 서버가 프록시 서버를 사용하는 방법에 대해 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5c689ff3621477aa84d958e97c2dfebb81dcca1
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "65499163"
---
# <a name="proxy-server-support-in-configuration-manager"></a>Configuration Manager의 프록시 서버 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

일부 Configuration Manager 사이트 시스템 서버는 인터넷 연결이 필요합니다. 사용자 환경에서 프록시 서버를 사용하기 위해 인터넷 트래픽이 필요한 경우 프록시를 사용하도록 이러한 사이트 시스템 역할을 구성합니다.  

-   사이트 시스템 서버를 호스팅하는 컴퓨터는 단일 프록시 서버 구성을 지원합니다. 해당 컴퓨터의 모든 사이트 시스템 역할은 동일한 프록시 구성을 공유합니다. 각 역할 또는 역할 인스턴스에 대해 개별 프록시 서버가 필요한 경우 별도의 사이트 시스템 서버에 이러한 역할을 저장합니다.  

-   이미 프록시 서버 구성이 있는 사이트 시스템 서버에 대해 새 프록시 서버 설정을 구성하면 원래 구성을 덮어씁니다.  

-   기본적으로 프록시 연결은 사이트 시스템 역할을 호스팅하는 컴퓨터의 **시스템** 계정을 사용합니다.  

-   컴퓨터 계정이 인증할 수 없는 경우 사이트 시스템 서버는 프록시 서버에 연결할 사용자 자격 증명을 저장할 수 있습니다. 이러한 자격 증명은 **사이트 시스템 프록시 서버 계정**입니다.  



## <a name="site-system-roles-that-use-a-proxy"></a>프록시를 사용하는 사이트 시스템 역할

다음 사이트 시스템 역할은 인터넷에 연결하고, 필요한 경우 프록시 서버를 사용할 수 있습니다.  


#### <a name="asset-intelligence-synchronization-point"></a>Asset Intelligence 동기화 지점
이 사이트 시스템 역할은 Microsoft에 연결하고 Asset Intelligence 동기화 지점을 호스팅하는 컴퓨터에 프록시 서버 구성을 사용합니다.  


#### <a name="cloud-distribution-point"></a>클라우드 배포 지점
클라우드 배포 지점 역할은 Microsoft Azure에서 실행됩니다. 프록시를 사용하도록 이 사이트 시스템 역할을 구성하지 마세요. 클라우드 배포 지점을 관리하는 기본 사이트 서버에 프록시 구성을 설정합니다.  

이 구성에서 기본 사이트 서버는 다음과 같은 특징이 있습니다.  

-   클라우드 배포 지점을 설정하고 모니터링하며 콘텐츠를 배포하기 위해 Microsoft Azure에 연결할 수 있어야 합니다.  

-   기본적으로 컴퓨터의 **시스템** 계정을 사용하여 연결합니다. 필요한 경우 사이트 시스템 프록시 서버 계정을 사용할 수도 있습니다.  

-   Windows 웹 브라우저 API를 사용합니다.  


#### <a name="exchange-server-connector"></a>Exchange Server 커넥터
이 사이트 시스템 역할은 Exchange Server에 연결합니다. Exchange Server 커넥터를 호스팅하는 컴퓨터에 프록시 서버 구성을 사용합니다.  


#### <a name="service-connection-point"></a>서비스 연결 지점
이 사이트 시스템 역할은 Configuration Manager 클라우드 서비스에 연결하여 Configuration Manager에 대한 버전 업데이트를 다운로드하고, 하이브리드 구성에서 Microsoft Intune에 연결합니다. 서비스 연결 지점을 호스팅하는 컴퓨터에 구성된 프록시 서버를 사용합니다.  


#### <a name="software-update-point"></a>소프트웨어 업데이트 지점
이 사이트 시스템 역할은 Microsoft 업데이트에 연결하여 패치를 다운로드하고 업데이트에 대한 정보를 동기화할 때 프록시를 사용합니다. 다른 모든 사이트 시스템 역할과 마찬가지로, 먼저 사이트 시스템 프록시 설정을 구성합니다. 그런 다음, 소프트웨어 업데이트 지점과 관련된 다음 옵션을 구성합니다.  

-   **소프트웨어 업데이트를 동기화하는 경우 프록시 서버 사용**  

-   **자동 배포 규칙을 사용하여 콘텐츠 다운로드 시 프록시 서버 사용**  

    > [!Note]  
    > 사용 가능한 동안, 이 설정은 보조 사이트의 소프트웨어 업데이트 지점에서 사용되지 않습니다.  

이러한 설정은 소프트웨어 업데이트 지점 속성의 **프록시 및 계정 설정** 탭에 있습니다.  

> [!NOTE]  
>  기본적으로 자동 배포 규칙을 실행하면 자동 배포 규칙을 만든 사이트 서버의 **시스템** 계정을 사용하여 인터넷에 연결하고 소프트웨어 업데이트를 다운로드합니다. 또는 사이트 시스템 프록시 서버 계정을 구성하고 사용합니다. 
>   
>  이 계정이 인터넷에 액세스할 수 없으면 소프트웨어 업데이트를 다운로드하지 못합니다. 다음 항목이 **ruleengine.log**에 로깅됩니다.  
> `Failed to download the update from internet. Error = 12007.`  



## <a name="configure-the-proxy-for-a-site-system-server"></a>사이트 시스템 서버에 대한 프록시 구성  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장한 다음, **서버 및 사이트 시스템 역할** 노드를 선택합니다.  

2.  편집할 사이트 시스템 서버를 선택합니다. 세부 정보 창에서 **사이트 시스템** 역할을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  

3.  사이트 시스템 속성에서 **프록시** 탭으로 전환합니다. 다음 프록시 설정을 구성합니다.  

    - **인터넷의 정보를 동기화할 때 프록시 서버 사용**: 사이트 시스템 서버가 프록시 서버를 사용하도록 설정하려면 이 옵션을 선택합니다.  

    - **프록시 서버 이름**: 사용자 환경에서 프록시 서버의 호스트 이름 또는 FQDN을 지정합니다.  

    - **포트**: 프록시 서버와 통신할 네트워크 포트를 지정합니다. 기본적으로 포트 **80**을 사용합니다.  

    - **자격 증명을 사용하여 프록시 서버에 연결**: 대부분의 프록시 서버에서는 사용자 인증이 필요합니다. 기본적으로 사이트 시스템 서버는 해당 컴퓨터 계정을 사용하여 프록시 서버에 연결합니다. 필요한 경우, 이 옵션을 활성화하고 **설정**을 클릭한 다음, **기존 계정**을 선택하거나 **새 계정**을 지정합니다. 이러한 자격 증명은 **사이트 시스템 프록시 서버 계정**입니다.  자세한 내용은 [Configuration Manager에 사용되는 계정](/sccm/core/plan-design/hierarchy/accounts)을 참조하세요.  

4.  **확인**을 클릭하여 새 프록시 서버 구성을 저장합니다.  
