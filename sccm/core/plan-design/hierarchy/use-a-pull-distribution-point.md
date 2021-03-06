---
title: 풀(pull) 배포 지점
titleSuffix: Configuration Manager
description: Configuration Manager에서 풀(pull) 배포 지점을 사용하기 위한 구성 및 제한 사항을 알아봅니다.
ms.date: 05/06/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7d8f530b-1a39-4a9d-a2f0-675b516da7e4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: dfceea40588f533cb2a29992f7236598380e140d
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799593"
---
# <a name="use-a-pull-distribution-point-with-configuration-manager"></a>Configuration Manager에서 풀(pull) 배포 지점 사용

*적용 대상: Configuration Manager(현재 분기)*


Configuration Manager 콘솔에서 표준 배포 지점에 콘텐츠를 배포하면 사이트 서버가 콘텐츠를 배포 지점으로 푸시합니다. 풀(pull) 배포 지점은 클라이언트와 같은 원본 위치에서 콘텐츠를 다운로드하여 얻습니다.  

다수의 배포 지점에 콘텐츠를 배포하는 경우 풀(pull) 배포 지점을 사용하면 사이트 서버에 대한 처리 부하를 줄일 수 있습니다. 또한 각 서버에 대한 콘텐츠 전송 속도를 높일 수 있습니다. 일반적으로 사이트 서버의 배포 관리자 구성 요소가 각 배포 지점에 콘텐츠를 보냅니다. 대신 사이트는 콘텐츠를 풀(pull) 배포 지점으로 전송하는 프로세스를 오프로드합니다.  

개별 배포 지점을 풀(pull) 배포 지점으로 구성할 수 있습니다. 각 풀(pull) 배포 지점에 대해 콘텐츠를 얻을 수 있는 하나 이상의 원본 배포 지점을 지정합니다. 풀(pull) 배포 지점은 원본 배포 지점으로 지정한 배포 지점에서만 콘텐츠를 다운로드할 수 있습니다. 

콘솔의 풀(pull) 배포 지점에 콘텐츠를 배포하면 사이트 서버가 알림을 보냅니다. 그러면 풀(pull) 배포 지점이 원본 배포 지점에서 콘텐츠를 다운로드합니다. 풀(pull) 배포 지점은 이미 콘텐츠 복사본이 있는 배포 지점에서 콘텐츠를 다운로드하여 콘텐츠 전송을 관리합니다.  

풀(pull) 배포 지점은 일반 배포 지점과 동일한 구성 및 기능을 지원합니다. 예를 들어 풀(pull) 배포 지점은 다음을 지원합니다. 
- 멀티캐스트 및 PXE 구성
- 콘텐츠 유효성 검사
- 주문형 콘텐츠 배포
- 클라이언트의 HTTP 또는 HTTPS 통신
- 다른 배포 지점과 동일한 인증서 옵션
- 개별적으로 또는 배포 지점 그룹의 멤버로 관리  

풀(pull) 배포 지점은 배포 지점을 설치할 때 구성합니다. 배포 지점을 만든 후에는 역할 속성을 편집하여 풀(pull) 배포 지점으로 구성합니다. 배포 지점을 풀(pull) 배포 지점으로 사용하도록 설정하는 방법은 [풀(pull) 배포 지점](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pull)을 참조하세요.  

배포 지점의 속성을 편집하여 풀(pull) 배포 지점에 대한 구성을 제거합니다. 풀(pull) 배포 지점으로 구성을 제거하면 정상 작동으로 돌아갑니다. 사이트 서버는 배포 지점에 대한 향후 콘텐츠 전송을 관리합니다.  



### <a name="distribution-process"></a>배포 프로세스

풀(pull) 배포 지점에 콘텐츠를 배포할 경우 다음과 같은 순서의 이벤트가 발생합니다.

-   콘솔의 풀(pull) 배포 지점에 콘텐츠를 배포하면 사이트 서버의 패키지 전송 관리자가 사이트 데이터베이스를 검사하여 원본 배포 지점에서 콘텐츠를 사용할 수 있는지 확인합니다. 풀(pull) 배포 지점의 원본 배포 지점에서 콘텐츠를 사용할 수 있는지 확인할 수 없는 경우 콘텐츠를 사용할 수 있을 때까지 20분 간격으로 검사를 반복합니다.  

-   패키지 전송 관리자가 콘텐츠를 사용할 수 있음을 확인하면 콘텐츠를 다운로드할 수 있도록 풀(pull) 배포 지점에 알립니다. 이 알림이 실패하면 풀(pull) 배포 지점에 대한 소프트웨어 배포 구성 요소 **다시 시도 설정**을 기반으로 다시 시도합니다. 풀(pull) 배포 지점에서 이 알림을 받으면 원본 배포 지점으로부터 콘텐츠 다운로드를 시도합니다.  

-   풀(pull) 배포 지점에서 콘텐츠를 다운로드하는 동안 패키지 전송 관리자는 풀(pull) 배포 지점에 대한 소프트웨어 배포 구성 요소 **상태 폴링 설정**을 기준으로 상태를 폴링합니다.  풀(pull) 배포 지점은 콘텐츠의 다운로드가 완료되면 해당 상태를 관리 지점에 제출합니다.  



## <a name="configure-site-component-settings"></a>사이트 구성 요소 설정 구성

풀(pull) 배포 지점 사용을 사용하는 경우에는 다음 사이트 구성 요소 설정을 검토하고 구성합니다.  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2.  사이트를 선택합니다. 리본에서 **사이트 구성 요소 구성**을 클릭하고 **소프트웨어 배포**를 선택합니다.  

3. **풀(pull) 배포 지점** 탭으로 전환합니다.  

4.  **다시 시도 설정** 그룹에서 다음 값을 검토합니다.  

    -   **다시 시도 횟수**: 패키지 전송 관리자가 풀(pull) 배포 지점에 콘텐츠 다운로드를 알리려고 시도하는 횟수입니다. 이 횟수만큼 시도한 후에는 패키지 전송 관리자가 전송을 취소합니다. 이 값은 기본적으로 30입니다.  

    -   **다시 시도하기 전 지연(분)** : 패키지 전송 관리자가 시도 사이에 대기하는 시간(분)입니다. 이 값은 기본적으로 20입니다.  

5.  **상태 폴링 설정** 그룹에서 다음 값을 검토합니다.  

    -   **폴링 수**: 패키지 전송 관리자가 작업 상태를 검색하기 위해 풀(pull) 배포 지점에 연결하는 횟수입니다. 작업이 완료되기 전에 이 횟수만큼 시도하면, 패키지 전송 관리자가 전송을 취소합니다. 이 값은 기본적으로 72입니다.   

    -   **다시 시도하기 전 지연(분)** : 패키지 전송 관리자가 시도 사이에 대기하는 시간(분)입니다. 이 값은 기본적으로 60입니다.   
    
    > [!NOTE]  
    >  폴링 재시도 횟수가 초과되어 전송 관리자가 작업을 취소하는 경우 풀(pull) 배포 지점에서 콘텐츠를 계속 다운로드합니다. 완료되면 풀(pull) 배포 지점에서 적절한 상태 메시지를 보내고 콘솔에 새 상태가 반영됩니다.  
    


## <a name="limitations"></a>제한 사항 

-   클라우드 배포 지점은 풀(pull) 배포 지점으로 구성할 수 없습니다.  

-   사이트 서버의 배포 지점 역할은 풀(pull) 배포 지점으로 구성할 수 없습니다.  

-   사전 준비 콘텐츠 구성은 풀(pull) 배포 지점 구성을 재정의합니다. 풀(pull) 배포 지점에서 **사전 준비된 콘텐츠에 이 배포 지점 사용** 옵션을 켜면, 콘텐츠를 기다립니다. 원본 배포 지점에서 콘텐츠를 풀(pull)하지 않습니다. 사전 준비된 콘텐츠에 사용 가능한 표준 배포 지점과 마찬가지로 사이트 서버에서 콘텐츠를 수신하지 못합니다. 자세한 내용은 [사전 준비된 콘텐츠](/sccm/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent)를 참조하세요.  

-   풀(pull) 배포 지점은 일정 또는 속도 제한 구성을 사용하지 않습니다. 이전에 설치된 배포 지점을 풀(pull) 배포 지점으로 구성할 경우 일정 및 속도 제한에 대한 구성이 저장되지만 사용되지는 않습니다. 이후에 풀(pull) 배포 지점 구성을 제거하면 일정 및 속도 제한 구성이 이전에 구성된 것으로 구현됩니다.  

    > [!NOTE]  
    >  **일정** 및 **속도 제한** 탭은 배포 지점의 속성에 표시되지 않습니다.  

-   풀(pull) 배포 지점은 **소프트웨어 배포 구성 요소 속성**의 **일반** 탭에서 각 사이트에 대한 설정을 사용하지 않습니다. 이러한 설정에는 **동시 배포** 및 **멀티캐스트 재시도**가 포함됩니다.  

-   원격 포리스트의 원본 배포 지점에서 콘텐츠를 전송하려면 풀(pull) 배포 지점에 Configuration Manager 클라이언트를 설치합니다. 원본 배포 지점에 액세스할 수 있는 네트워크 액세스 계정도 구성합니다. 버전 1806부터 사이트에서 **HTTP 사이트 시스템에 Configuration Manager가 생성한 인증서 사용** 옵션을 사용하도록 설정하면 네트워크 액세스 계정이 필요하지 않습니다.<!--1358228-->  

-   풀(pull) 배포 지점이 Configuration Manager 클라이언트인 경우에는 클라이언트 버전이 풀(pull) 배포 지점을 설치하는 Configuration Manager 사이트와 동일해야 합니다. 풀(pull) 배포 지점은 풀(pull) 배포 지점과 Configuration Manager 클라이언트에 공통으로 적용되는 CCMFramework를 사용합니다.  



## <a name="about-source-distribution-points"></a>원본 배포 지점 정보  

풀(pull) 배포 지점을 구성할 때는 원본 배포 지점을 하나 이상 지정합니다.  

-   마법사에는 원본 배포 지점으로 사용할 수 있는 배포 지점만 표시됩니다.  

-   풀(pull) 배포 지점은 다른 풀(pull) 배포 지점에 대한 원본 배포 지점으로 지정할 수 있습니다.  

-   Configuration Manager 콘솔을 사용할 때는 HTTP를 지원하는 배포 지점만 원본 배포 지점으로 지정할 수 있습니다.  

-   Configuration Manager SDK를 사용하면 HTTPS용으로 구성된 원본 배포 지점을 지정할 수 있습니다. HTTPS용으로 구성된 원본 배포 지점을 사용하려면 풀(pull) 배포 지점에 Configuration Manager 클라이언트를 설치합니다.  

-   버전 1806부터는 원격 사무실의 인터넷 연결 속도가 더 빠르거나 WAN 링크에 대한 부하를 줄이려는 경우 Microsoft Azure의 [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)을 원본으로 사용합니다. 풀(pull) 배포 지점은 인터넷에 액세스할 수 있어야 Microsoft Azure와 통신할 수 있습니다. 콘텐츠는 원본 클라우드 배포 지점에 배포되어야 합니다.<!--1321554-->  

    > [!Note]  
    > 이 기능은 데이터 스토리지 및 네트워크 출력에 대한 Azure 구독에 요금을 부과합니다. 자세한 내용은 [클라우드 배포 지점을 사용하는 데 드는 비용](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_cost)을 참조하세요.  


> [!Tip]  
> 원본 배포 지점에서 콘텐츠를 다운로드하는 풀(pull) 배포 지점은 **배포 지점 사용량 요약** 보고서의 **액세스된 클라이언트(고유)** 열에서 클라이언트로 계산됩니다.  


### <a name="source-priorities"></a>원본 우선 순위

-   각 원본 배포 지점에 별도의 우선 순위를 할당하거나, 여러 원본 배포 지점을 동일한 우선 순위에 할당합니다.  

-   우선 순위는 풀(pull) 배포 지점이 소스 배포 지점의 콘텐츠를 요청하는 순서를 결정합니다.  

-   풀(pull) 배포 지점은 우선 순위에서 값이 가장 낮은 원본 배포 지점을 처음으로 연결합니다. 우선 순위가 동일한 원본 배포 지점이 여러 개 있는 경우 풀(pull) 배포 지점은 해당 우선 순위의 원본 중 하나를 임의로 선택합니다.  

-   선택한 원본에서 콘텐츠를 사용할 수 없으면 풀(pull) 배포 지점이 동일한 우선 순위의 다른 배포 지점에서 콘텐츠를 다운로드하려고 시도합니다.  

-   지정된 우선 순위의 배포 지점에 콘텐츠가 없으면, 풀(pull) 배포 지점은 다음 우선 순위의 소스 배포 지점에서 콘텐츠를 다운로드하려고 시도합니다. 콘텐츠를 찾을 때까지 이 검색이 계속됩니다.   

- 할당된 원본 배포 지점에 콘텐츠가 없으면 풀(pull) 배포 지점은 30분 동안 대기한 다음, 프로세스를 다시 시작합니다.  



## <a name="inside-the-pull-distribution-point"></a>풀(pull) 배포 지점 내부 

-   콘텐츠 전송을 관리하기 위해 풀(pull) 배포 지점에서는 **CCMFramework** 구성 요소를 사용합니다. Configuration Manager 클라이언트는 이 구성 요소를 포함합니다.  

-   풀(pull) 배포 지점을 사용하도록 설정하면 사이트는 **pulldp.msi**를 설치합니다. 이 설치 관리자는 CCMFramework 구성 요소도 추가합니다. 프레임워크에는 Configuration Manager 클라이언트가 필요하지 않습니다.  

-   풀(pull) 배포 지점이 설치된 후에는 **CCMExec** 서비스를 주로 사용하여 작동합니다.  

-   풀(pull) 배포 지점이 콘텐츠를 전송하는 경우에는 Windows에 기본 제공되는 BITS(**Background Intelligent Transfer Service**)를 사용합니다. 풀(pull) 배포 지점에는 IIS 서버용 BITS 확장을 설치할 필요가 없습니다.<!--sms.503672 -Clarified BITS use-->

-  작동에 대한 자세한 내용은 풀(pull) 배포 지점의 다음 로그 파일을 참조하세요.  
    - **DataTransferService.log**
    - **PullDP.log**



## <a name="see-also"></a>참고 항목  
 [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   
