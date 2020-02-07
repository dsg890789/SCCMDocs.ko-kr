---
title: 크기 조정 및 규모
titleSuffix: Configuration Manager
description: 환경에서 디바이스를 지원하는 데 필요한 사이트 시스템 역할 및 사이트 수를 확인합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 552ac6d1f974b41fa97e7343e72a187c99c9b44f
ms.sourcegitcommit: e7583b5e522d01bc8710ec8e0fe3e5f75a281577
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035167"
---
# <a name="size-and-scale-numbers-for-configuration-manager"></a>Configuration Manager의 크기 및 비율 값

*적용 대상: Configuration Manager(현재 분기)*

각 Configuration Manager 배포에서 지원할 수 있는 사이트, 사이트 시스템 역할 및 디바이스의 최대 개수가 있습니다. 이러한 숫자 값은 계층 구조, 사용하는 사이트의 유형 및 개수, 배포하는 사이트 시스템 역할에 따라 달라집니다. 이 문서의 정보는 관리할 것으로 예상하는 디바이스를 지원하기 위해 필요한 사이트 시스템 역할 및 사이트 수를 확인하는 데 도움이 될 수 있습니다.

자세한 내용은 다음 아티클을 참조하세요.

- [권장 하드웨어](/sccm/core/plan-design/configs/recommended-hardware)
- [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)  
- [클라이언트 및 디바이스에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)
- [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)

이러한 지원 숫자 값은 Configuration Manager의 권장 하드웨어 사용을 기반으로 합니다. 또한 사용 가능한 모든 Configuration Manager 기능의 기본 설정을 기반으로 합니다. 권장 하드웨어를 사용하지 않거나 보다 적극적으로 사용자 지정 설정을 사용할 경우 사이트 시스템 성능이 저하될 수 있습니다. 사이트 시스템이 명시된 지원 수준을 충족하지 않을 수 있습니다. (보다 적극적인 클라이언트 설정의 예로는 하드웨어 또는 소프트웨어 인벤토리를 기본값인 7일에 1회보다 더 자주 실행하는 경우를 들 수 있습니다.)


## <a name="bkmk_SiteSystemScale"></a> 사이트 유형  

### <a name="central-administration-site"></a>중앙 관리 사이트  

- 중앙 관리 사이트는 최대 25개의 자식 기본 사이트를 지원합니다.  

### <a name="primary-site"></a>기본 사이트  

- 각 기본 사이트는 최대 250개의 보조 사이트를 지원합니다.  

- 기본 사이트당 보조 사이트 수는 지속적으로 연결되며 안정적으로 유지되는 WAN(광역 네트워크) 연결을 기준으로 합니다. 클라이언트 수가 500개 미만인 위치의 경우에는 보조 사이트 대신 배포 지점을 사용할 수 있습니다.  

  기본 사이트에서 지원할 수 있는 클라이언트 및 디바이스 수에 대한 자세한 내용은 [사이트 및 계층 구조에 대한 클라이언트 수](#bkmk_clientnumbers)를 참조하세요.  

### <a name="secondary-site"></a>보조 사이트  

- 보조 사이트는 자식 사이트를 지원하지 않습니다.  


## <a name="bkmk_roles"></a> 사이트 시스템 역할

### <a name="application-catalog-web-service-point"></a>애플리케이션 카탈로그 웹 서비스 지점  

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터 업데이트된 클라이언트는 사용자가 이용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

- 기본 사이트에서 애플리케이션 카탈로그 웹 서비스 지점의 여러 인스턴스를 설치할 수 있습니다.  

### <a name="application-catalog-website-point"></a>애플리케이션 카탈로그 웹 사이트 지점  

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터 업데이트된 클라이언트는 사용자가 이용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

- 기본 사이트에서 애플리케이션 카탈로그 웹 사이트 지점의 여러 인스턴스를 설치할 수 있습니다.  

### <a name="bkmk_cmg"></a> 클라우드 관리 게이트웨이

- 기본 사이트 또는 중앙 관리 사이트에 여러 CMG(클라우드 관리 게이트웨이) 인스턴스를 설치할 수 있습니다.  

    > [!Tip]  
    > 계층 구조에서 중앙 관리 사이트에 CMG를 만듭니다.  

    - 하나의 CMG는 Azure 클라우드 서비스에서 1-16개의 VM(가상 머신)을 지원합니다.  

    - 각 CMG VM 인스턴스는 6000개의 동시 클라이언트 연결을 지원합니다. 지원되는 클라이언트 수를 초과하여 CMG의 부하가 높은 경우에도 CMG에서 요청을 처리하지만 지연이 발생할 수 있습니다.  

자세한 내용은 CMG [성능 및 크기 조정](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#performance-and-scale)을 참조하세요.

### <a name="cloud-management-gateway-connection-point"></a>클라우드 관리 게이트웨이 연결점

- 기본 사이트에 여러 CMG 연결점 인스턴스를 설치할 수 있습니다.  

- 하나의 CMG 연결점은 최대 4개의 VM 인스턴스가 포함된 CMG를 지원할 수 있습니다. CMG의 VM 인스턴스가 4개보다 많으면 부하 분산을 위해 두 번째 CMG 연결점을 추가합니다. VM 인스턴스 16개가 포함된 CMG에는 4개의 CMG 연결점을 연결해야 합니다.

자세한 내용은 CMG [성능 및 크기 조정](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#performance-and-scale)을 참조하세요.

### <a name="distribution-point"></a>배포 지점  

- 사이트별 배포 지점:  

    - 각 기본 및 보조 사이트는 최대 250개의 배포 지점을 지원합니다.  

    - 각 기본 및 보조 사이트는 풀(pull) 배포 지점으로 구성된 추가 배포 지점을 2,000개까지 지원합니다. **예를 들어** 배포 지점 2,000개가 풀(pull) 배포 지점으로 구성되어 있으면 단일 기본 사이트는 2,250개의 배포 지점을 지원합니다.  

    - 각 배포 지점은 최대 4,000개 클라이언트로부터의 연결을 지원합니다.  

    - 풀(pull) 배포 지점은 원본 배포 지점의 콘텐츠에 액세스할 때 클라이언트처럼 작동합니다.  

- 각 기본 사이트는 최대 5,000개의 배포 지점(총 합계)을 지원합니다. 이 합계에는 기본 사이트의 모든 배포 지점과 기본 사이트의 자식 보조 사이트에 속하는 모든 배포 지점이 포함됩니다.  

- 각 배포 지점은 최대 10,000개의 패키지 및 애플리케이션(총 합계)을 지원합니다.  

> [!WARNING]  
> 한 배포 지점이 지원할 수 있는 실제 클라이언트 수는 네트워크 속도와 서버의 하드웨어 구성에 따라 달라집니다.  
>
> 마찬가지로 단일 원본 배포 지점이 지원할 수 있는 풀(pull) 배포 지점의 수도 원본 배포 지점의 네트워크 속도 및 하드웨어 구성에 따라 달라집니다. 하지만 이 수는 배포한 콘텐츠의 양에도 영향을 받습니다. 배포하는 동안 서로 다른 시간에 콘텐츠에 액세스하는 클라이언트와는 달리, 모든 끌어오기 배포 지점에서 동시에 콘텐츠를 요청하기 때문입니다. 끌어오기 배포 지점에서는 적용되는 콘텐츠뿐 아니라 사용 가능한 모든 콘텐츠를 요청할 수 있습니다. 원본 배포 지점의 처리 부하가 높으면 대상 배포 지점으로 콘텐츠를 배포하는 과정이 예기치 않게 지연될 수 있습니다.  

### <a name="fallback-status-point"></a>대체 상태 지점  

- 각 대체 상태 지점은 최대 100,000개의 클라이언트를 지원할 수 있습니다.  

### <a name="management-point"></a>관리 지점  

- 각 기본 사이트는 최대 15개의 관리 지점을 지원합니다.  

    > [!TIP]  
    > 기본 사이트 서버 또는 사이트 데이터베이스 서버에서 저속 링크를 사용하여 서버에 관리 지점을 설치하지 마세요.  

- 각 보조 사이트는 관리 지점 하나를 지원하며, 이 관리 지점은 보조 사이트 서버에 설치해야 합니다.  

관리 지점에서 지원할 수 있는 클라이언트 및 디바이스 수에 대한 자세한 내용은 [관리 지점](#bkmk_mp) 섹션을 참조하세요.  

### <a name="software-update-point"></a>소프트웨어 업데이트 지점  

다음 권장 사항을 기준으로 사용합니다. 이 기준은 조직에 적절한 소프트웨어 업데이트 용량 계획에 대한 정보를 파악하도록 도와줍니다. 실제 용량 요구 사항은 다음 기준에 따라 이 문서에 나열된 권장 사항과 다를 수 있습니다. 
- 특정 네트워킹 환경
- 소프트웨어 업데이트 지점 사이트 시스템을 호스팅하는 데 사용하는 하드웨어
- 관리되는 클라이언트 수
- 서버에 설치된 다른 사이트 시스템 역할  

#### <a name="BKMK_SUMCapacity"></a> 소프트웨어 업데이트 지점에 대한 용량 계획  

지원되는 클라이언트 수는 소프트웨어 업데이트 지점에서 실행되는 WSUS(Windows Server Update Services)의 버전에 따라 다릅니다. 또한 소프트웨어 업데이트 지점 사이트 시스템 역할이 다른 사이트 시스템 역할과 함께 있는지 여부에 따라 달라집니다.  

- 소프트웨어 업데이트 지점 서버에서 WSUS가 실행되고 소프트웨어 업데이트 지점이 다른 사이트 시스템 역할과 함께 있는 경우 소프트웨어 업데이트 지점은 최대 25,000개의 클라이언트를 지원할 수 있습니다.  

- 원격 서버가 WSUS 요구 사항을 충족하고 WSUS가 Configuration Manager에서 사용되며 다음 설정을 구성하는 경우 소프트웨어 업데이트 지점은 최대 15만 개의 클라이언트를 지원할 수 있습니다.

    IIS 애플리케이션 풀:
    - WsusPool 큐 길이를 2000으로 증가
    - WsusPool 프라이빗 메모리 제한을 4배로 늘리거나 0(무제한)으로 설정합니다. 예를 들어, 기본 제한이 1,843,200KB이면 7,372,800으로 증가합니다. 자세한 내용은 이 [Configuration Manager 지원 팀 블로그 게시물](https://www.phoenixtekk.com/configmgr-2012-support-tip-wsus-sync-fails-with-http-503-errors/)을 참조하세요.  

    소프트웨어 업데이트 지점의 하드웨어 요구 사항에 대한 자세한 내용은 [사이트 시스템용 권장 하드웨어](/sccm/core/plan-design/configs/recommended-hardware#bkmk_ScaleSieSystems)를 참조하세요.  


#### <a name="bkmk_sum-capacity-obj"></a> 소프트웨어 업데이트 개체를 위한 용량 계획  

소프트웨어 업데이트 개체에 대한 계획을 세울 때에는 다음 용량 정보를 따릅니다.  

- **배포의 소프트웨어 업데이트 수를 1,000개로 제한** - 각 소프트웨어 업데이트 배포의 소프트웨어 업데이트 수를 1,000개로 제한합니다. ADR(자동 배포 규칙)을 만드는 경우 소프트웨어 업데이트 수를 제한하는 조건을 지정합니다. 지정된 조건에서 1000개를 초과하는 소프트웨어 업데이트가 반환되면 ADR이 실패합니다. Configuration Manager 콘솔의 **자동 배포 규칙** 노드에서 ADR의 상태를 확인합니다. 소프트웨어 업데이트를 수동으로 배포할 경우 배포할 업데이트는 1000개 이하로 선택합니다.  

  또한 구성 기준에서 소프트웨어 업데이트 수를 1000개로 제한합니다. 자세한 내용은 [Create configuration baselines](/sccm/compliance/deploy-use/create-configuration-baselines)(구성 기준 만들기)를 참조하세요.

- **자동 배포 규칙에 대한 보안 범위를 580으로 제한** -<!--ado 4962928-->
ADR(자동 배포 규칙)의 보안 범위 수를 580 미만으로 제한합니다. ADR을 만들 때 액세스할 수 있는 보안 범위가 자동으로 추가됩니다. 580개가 넘는 보안 범위가 설정된 경우 ADR이 실행되지 않으며 ruleengine.log에 오류가 기록됩니다.

## <a name="bkmk_clientnumbers"></a> 사이트 및 계층 구조에 대한 클라이언트 수

다음 정보를 활용하면 사이트 또는 계층 구조에서 지원할 수 있는 클라이언트 수 및 유형을 확인할 수 있습니다.  

### <a name="bkmk_cas"></a> 중앙 관리 사이트가 있는 계층 구조

중앙 관리 사이트는 다음과 같은 세 그룹에 대해 나열된 디바이스 수까지 포함하는 총 디바이스 수를 지원합니다.  

- 70만 Windows 데스크톱입니다. 또한 [임베디드 디바이스](#embedded) 지원을 참조하세요.

- Mac 및 Windows CE 7.0을 실행하는 디바이스 25,000대  

- 온-프레미스 MDM(모바일 디바이스 관리)을 사용하여 관리하는 디바이스 100,000대

예를 들어 계층 구조에서 데스크톱 700,000대, Mac 및 Windows CE 7.0 디바이스 최대 25,000대, 온-프레미스 MDM에서 관리하는 디바이스 최대 100,000대를 지원할 수 있습니다. 이 계층 구조는 총 825,000대의 디바이스를 지원합니다.

> [!IMPORTANT]  
> 중앙 관리 사이트가 SQL Server Standard Edition을 사용하는 계층 구조에서, 계층 구조는 최대 50,000대의 데스크톱 및 디바이스를 지원합니다. 50,000개 이상의 데스크톱과 디바이스를 지원하려면 SQL Server Enterprise Edition을 사용해야 합니다. 이 요구 사항은 중앙 관리 사이트에만 적용됩니다. 독립 실행형 기본 사이트 또는 자식 기본 사이트에는 적용되지 않습니다. 기본 사이트에 사용하는 SQL Server 버전은 명시된 클라이언트 수를 지원하는 용량을 제한하지 않습니다.

독립 실행형 기본 사이트에서 사용 중인 SQL Server의 버전은 명시된 클라이언트 수까지 지원하도록 해당 사이트 용량을 제한하지 않습니다.  

### <a name="bkmk_chipri"></a> 자식 기본 사이트

중앙 관리 사이트가 있는 계층의 각 자식 기본 사이트에서는 다음과 같은 클라이언트 수를 지원합니다.  

- 계층 구조에 대해 지원되는 수를 초과하지 않는 한 특정 그룹 또는 유형으로 제한되지 않는 총 클라이언트 및 디바이스 150,000대. 또한 [임베디드 디바이스](#embedded) 지원을 참조하세요.

예를 들어 기본 사이트는 Mac 및 Windows CE 7.0 디바이스 25,000대를 지원합니다. 이 숫자가 계층 구조의 제한입니다. 이 기본 사이트는 데스크톱 컴퓨터 125,000대를 추가로 지원할 수 있습니다. 따라서 자식 기본 사이트에 지원되는 총 디바이스 수는 지원되는 최대 제한인 150,000대가 됩니다.

### <a name="bkmk_pri"></a> 독립 실행형 기본 사이트

독립 실행형 기본 사이트는 다음과 같은 디바이스 수를 지원합니다.  

- 총 클라이언트 및 디바이스 수는 175,000대이지만 다음을 초과하지 않습니다.  

    - 데스크톱(Windows, Linux 및 UNIX를 실행하는 컴퓨터) 150,000대 또한 [임베디드 디바이스](#embedded) 지원을 참조하세요.

    - Mac 및 Windows CE 7.0을 실행하는 디바이스 25,000대

    - 온-프레미스 MDM을 사용하여 관리하는 디바이스 50,000대  

예를 들어 데스크톱 150,000대와 Mac 10,000대를 지원하는 독립 실행형 기본 사이트는 온-프레미스 MDM에서 관리하는 모바일 디바이스 15,000대만 추가로 지원할 수 있습니다.

### <a name="embedded"></a>기본 사이트와 Windows Embedded 디바이스

기본 사이트가 FBWF(파일 기반 쓰기 필터)를 사용할 수 있는 Windows Embedded 디바이스를 지원합니다. 임베디드 디바이스에서 쓰기 필터를 사용할 수 없는 경우 기본 사이트는 임베디드 디바이스를 해당 사이트에 대해 허용되는 디바이스 수까지 지원할 수 있습니다. 임베디드 디바이스에서 FBWF 또는 UWF(Unified Write Filters)가 활성화되면 기본 사이트는 최대 10,000대의 Windows Embedded 디바이스를 지원할 수 있습니다. 이러한 디바이스는 [Windows Embedded 디바이스에 클라이언트 배포 계획](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices)에 있는 중요 참고 사항에 나열된 예외로 구성해야 합니다. EWF를 사용할 수 있으며 예외가 적용되도록 구성되어 있지 않은 Windows Embedded 디바이스의 경우 기본 사이트에서 3,000개만 지원됩니다.

### <a name="bkmk_sec"></a> 보조 사이트

보조 사이트에서 지원하는 디바이스 수는 다음과 같습니다.  

- 데스크톱(Windows, Linux 및 UNIX를 실행하는 컴퓨터) 15,000대  

### <a name="bkmk_mp"></a> 관리 지점

각 관리 지점에서는 다음과 같은 디바이스 수를 지원할 수 있습니다.  

- 총 클라이언트 및 디바이스 수는 25,000대이지만 다음을 초과하지 않습니다.  

    - 데스크톱(Windows, Linux 및 UNIX를 실행하는 컴퓨터) 25,000대  

    - 다음 중 하나입니다(둘 다는 될 수 없음).  

        - 온-프레미스 MDM을 사용하여 관리하는 디바이스 10,000대  

        - Mac 및 Windows CE 7.0 클라이언트를 실행하는 디바이스 10,000대
