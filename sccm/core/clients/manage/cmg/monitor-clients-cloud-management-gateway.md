---
title: 클라우드 관리 게이트웨이 모니터링
titleSuffix: Configuration Manager
description: CMG(클라우드 관리 게이트웨이)를 통해 클라이언트 및 네트워크 트래픽을 모니터링합니다.
ms.date: 06/17/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d184118e0e99231a9160322740ab7690488a28a5
ms.sourcegitcommit: 3936b869d226cea41fa0090e2cbc92bd530db03a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67286758"
---
# <a name="monitor-cloud-management-gateway"></a>클라우드 관리 게이트웨이 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

클라우드 관리 게이트웨이(CMG)가 실행되고 클라이언트가 CMG를 통해 연결된 후에 클라이언트 및 네트워크 트래픽을 모니터링하여 서비스가 수행되는 방법을 확인할 수 있습니다.


## <a name="monitor-clients"></a>클라이언트 모니터링

CMG를 통해 연결된 클라이언트는 온-프레미스 클라이언트와 동일한 방식으로 Configuration Manager 콘솔에 표시됩니다. 자세한 내용은 [클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)을 참조하세요.


## <a name="monitor-traffic-in-the-console"></a>콘솔에서 트래픽 모니터링

Configuration Manager 콘솔을 사용하여 CMG에서 트래픽을 모니터링합니다.

1. **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 후, **클라우드 관리 게이트웨이** 노드를 선택합니다.  

2. 목록 창에서 CMG를 선택합니다.  

3. CMG 연결점 및 CMG가 연결된 사이트 시스템 역할에 대한 세부 정보 창에서 트래픽 정보를 확인합니다. 이러한 통계는 이러한 역할로 들어오는 클라이언트 요청을 보여 줍니다. 이 요청에는 정책, 위치, 등록, 콘텐츠, 인벤토리 및 클라이언트 알림이 포함됩니다.<!-- SCCMDocs#1208 -->

## <a name="set-up-outbound-traffic-alerts"></a>아웃바운드 트래픽 경고 설정

아웃바운드 트래픽 경고를 통해 네트워크 트래픽이 14일 임계값 수준에 가까워지면 알 수 있습니다. CMG를 만들 때 트래픽 경고를 설정할 수 있습니다. 해당 부분을 건너뛴 경우 서비스를 실행한 후에도 경고를 설정할 수 있습니다. 언제든지 경고 설정을 조정할 수 있습니다.

1. **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 후, **클라우드 관리 게이트웨이** 노드를 선택합니다.  

2. 목록 창에서 CMG를 선택한 다음, 리본 메뉴에서 **속성**을 선택합니다.  

3. **경고**로 이동하여 임계값 및 경고를 사용하도록 설정합니다. 기가바이트(GB) 단위로 14일 데이터 임계값을 지정합니다. 또한 임계값 백분율을 지정하여 경고 수준을 높입니다.  

4. 완료했으면 **확인**을 선택합니다.  


## <a name="monitor-logs"></a>로그 모니터링

CMG는 많은 로그 파일의 항목을 생성합니다. 자세한 내용은 [Configuration Manager 로그](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)를 참조하세요.


## <a name="cloud-management-dashboard"></a>클라우드 관리 대시보드

<!--1358461-->
1806 버전부터 클라우드 관리 대시보드는 CMG 사용량에 대한 중앙 집중식 보기를 제공합니다. 사이트가 클라우드 관리에 대한 [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)에 등록되면 사이트에는 클라우드 사용자 및 디바이스에 대한 데이터도 표시됩니다.  

다음 스크린샷은 사용 가능한 타일 두 가지를 보여 주는 클라우드 관리 대시보드의 일부입니다.  
![클라우드 관리 대시보드 타일 CMG 트래픽 및 현재 온라인 클라이언트](media/1358461-cmg-dashboard.png)

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다. **클라우드 관리** 노드를 선택하고 대시보드 타일을 봅니다.  


## <a name="connection-analyzer"></a>연결 분석기

버전 1806부터 실시간 확인에 CMG 연결 분석기를 사용하여 문제 해결에 도움을 줍니다. 콘솔 내 유틸리티는 서비스의 현재 상태를 확인하며, CMG 연결 지점을 통해 CMG 트래픽을 허용하는 모든 관리 지점에 대한 통신 채널을 확인합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **Cloud Services**를 확장하고 **클라우드 관리 게이트웨이** 노드를 선택합니다.  

2. 대상 CMG 인스턴스를 선택하고 리본에서 **연결 분석기**를 선택합니다.  

3. CMG 연결 분석기 창에서 다음 옵션 중 하나를 선택하여 서비스를 인증합니다.  

     1. **Azure AD 사용자**: 이 옵션을 사용하여 Azure AD 조인 Windows 10 디바이스에 클라우드 기반 사용자 ID가 로그인한 것과 동일하게 통신을 시뮬레이션합니다. **로그인**을 클릭하여 이 Azure AD 사용자 계정에 대한 자격 증명을 안전하게 입력합니다.  

     2. **클라이언트 인증서**: 이 옵션은 [클라이언트 인증 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_clientauth)를 사용하는 Configuration Manager 클라이언트와 동일하게 통신을 시뮬레이션하는 데 사용합니다.  

4. **시작**을 선택하여 분석을 시작합니다. 분석기 창에 결과가 표시됩니다. 설명 필드에서 자세한 내용을 보려면 항목을 선택합니다.  


## <a name="bkmk_stop"></a> 임계값을 초과하는 경우 CMG 중지

<!--3735092-->
1902 버전부터 이제 Configuration Manager는 총 데이터 전송이 한도를 초과하는 경우 CMG 서비스를 중지할 수 있습니다. 사용량이 경고 또는 위험 수준에 도달하는 경우 [경고](#set-up-outbound-traffic-alerts)를 사용하여 알림을 트리거합니다. 사용량 급증으로 인한 예기치 않은 모든 Azure 비용을 줄이기 위해 이 옵션은 클라우드 서비스를 해제합니다.

> [!Important]  
> 서비스 실행 중이 아닌 경우에도 여전히 클라우드 서비스와 연결된 비용이 발생합니다. 서비스를 중지해도 연결된 모든 Azure 비용이 제거되지 않습니다. 클라우드 서비스에 대한 모든 비용을 제거하려면 [CMG를 제거](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg)합니다.  
>
> CMG 서비스가 중지되면 인터넷 기반 클라이언트는 Configuration Manager와 통신할 수 없습니다.  

총 데이터 전송(송신)에는 클라우드 서비스 및 스토리지 계정의 데이터가 포함됩니다. 다음 흐름에서 이 데이터를 가져옵니다.

- CMG에서 클라이언트로  
- CMG 로그 파일을 포함하여 CMG에서 사이트로  
- 콘텐츠에 대한 CMG를 사용하는 경우 스토리지 계정에서 클라이언트로  

이러한 데이터 흐름에 대한 자세한 내용은 [CMG 포트 및 데이터 흐름](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#ports-and-data-flow)을 참조하세요.

스토리지 경고 임계값은 별도입니다. 해당 경고는 Azure 스토리지 인스턴스의 용량을 모니터링합니다.

콘솔의 **클라우드 관리 게이트웨이** 노드에서 CMG 인스턴스를 선택하는 경우 세부 정보 창에 총 데이터 전송이 표시될 수 있습니다.

Configuration Manager는 6분마다 임계값을 확인합니다. 사용량이 급증하는 경우 Configuration Manager는 임계값이 초과되는 것을 검색하고 서비스를 중지하는 데 최대 6분이 걸릴 수 있습니다.

### <a name="process-to-stop-the-cloud-service-when-it-exceeds-threshold"></a>임계값을 초과하는 경우 클라우드 서비스를 중지하는 프로세스

1. [아웃바운드 트래픽 경고를 설정](#set-up-outbound-traffic-alerts)합니다.  

2. CMG 속성 창의 **경고** 탭에서 **위험 임계값이 초과되면 이 서비스 중지** 옵션을 사용하도록 설정합니다.  

이 기능을 테스트하려면 다음 값 중 하나를 일시적으로 줄입니다.  

- **아웃바운드 데이터 전송의 14일 임계값(GB)** . 기본값은 `10000`입니다.  

- **중요 알림 생성 임계값의 비율**. 기본값은 `90`입니다.  
