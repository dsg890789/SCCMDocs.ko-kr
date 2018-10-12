---
title: 클라우드 관리 게이트웨이 모니터링
titleSuffix: Configuration Manager
description: CMG(클라우드 관리 게이트웨이)를 통해 클라이언트 및 네트워크 트래픽을 모니터링합니다.
ms.date: 09/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4ef27c67b9b17f41fbe71d57fdea9552b7dff9f7
ms.sourcegitcommit: 2badee2b63ae63687795250e298f463474063100
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601044"
---
# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Configuration Manager에서 클라우드 관리 게이트웨이 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

클라우드 관리 게이트웨이(CMG)가 실행되고 클라이언트가 CMG를 통해 연결된 후에 클라이언트 및 네트워크 트래픽을 모니터링하여 서비스가 수행되는 방법을 확인할 수 있습니다.



## <a name="monitor-clients"></a>클라이언트 모니터링

CMG를 통해 연결된 클라이언트는 온-프레미스 클라이언트와 동일한 방식으로 Configuration Manager 콘솔에 표시됩니다. 자세한 내용은 [클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)을 참조하세요.



## <a name="monitor-traffic-in-the-console"></a>콘솔에서 트래픽 모니터링

Configuration Manager 콘솔을 사용하여 CMG에서 트래픽을 모니터링합니다.

1. **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 후, **클라우드 관리 게이트웨이** 노드를 선택합니다.  

2. 목록 창에서 CMG를 선택합니다.  

3. CMG 연결점 및 CMG가 연결된 사이트 시스템 역할에 대한 세부 정보 창에서 트래픽 정보를 확인합니다.  



## <a name="set-up-outbound-traffic-alerts"></a>아웃바운드 트래픽 경고 설정

아웃바운드 트래픽 경고를 통해 네트워크 트래픽이 14일 임계값 수준에 가까워지면 알 수 있습니다. CMG를 만들 때 트래픽 경고를 설정할 수 있습니다. 해당 부분을 건너뛴 경우 서비스를 실행한 후에도 경고를 설정할 수 있습니다. 언제든지 경고 설정을 조정할 수 있습니다.

1. **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 후, **클라우드 관리 게이트웨이** 노드를 선택합니다.  

2. 목록 창에서 CMG를 선택한 다음, 리본 메뉴에서 **속성**을 선택합니다.  

3. **경고**로 이동하여 임계값 및 경고를 사용하도록 설정합니다. 기가바이트(GB) 단위로 14일 데이터 임계값을 지정합니다. 또한 임계값 백분율을 지정하여 경고 수준을 높입니다.  

4. 완료했으면 **확인**을 선택합니다.  



## <a name="monitor-logs"></a>로그 모니터링

CMG는 많은 로그 파일의 항목을 생성합니다. 자세한 내용은 [Configuration Manager 로그](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)를 참조하세요.



## <a name="cloud-management-dashboard"></a>클라우드 관리 대시보드
<!--1358461--> 버전 1806을 시작으로 클라우드 관리 대시보드는 CMG 사용량에 대한 중앙 집중식 보기를 제공합니다. 사이트가 클라우드 관리에 대한 [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)에 등록되면 사이트에는 클라우드 사용자 및 장치에 대한 데이터도 표시됩니다.  

다음 스크린샷은 사용 가능한 타일 두 가지를 보여 주는 클라우드 관리 대시보드의 일부입니다.  
![클라우드 관리 대시보드 타일 CMG 트래픽 및 현재 온라인 클라이언트](media/1358461-cmg-dashboard.png)

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다. **클라우드 관리** 노드를 선택하고 대시보드 타일을 봅니다.  



## <a name="connection-analyzer"></a>연결 분석기

버전 1806부터 실시간 확인에 CMG 연결 분석기를 사용하여 문제 해결에 도움을 줍니다. 콘솔 내 유틸리티는 서비스의 현재 상태를 확인하며, CMG 연결 지점을 통해 CMG 트래픽을 허용하는 모든 관리 지점에 대한 통신 채널을 확인합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **Cloud Services**를 확장하고 **클라우드 관리 게이트웨이** 노드를 선택합니다.  

2. 대상 CMG 인스턴스를 선택하고 리본에서 **연결 분석기**를 선택합니다.  

3. CMG 연결 분석기 창에서 다음 옵션 중 하나를 선택하여 서비스를 인증합니다.  

     1. **Azure AD 사용자**: 이 옵션을 사용하여 Azure AD 조인 Windows 10 장치에 클라우드 기반 사용자 ID가 로그인한 것과 동일하게 통신을 시뮬레이션합니다. **로그인**을 클릭하여 이 Azure AD 사용자 계정에 대한 자격 증명을 안전하게 입력합니다.  

     2. **클라이언트 인증서**: 이 옵션은 [클라이언트 인증 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#client-authentication-certificate)를 사용하는 Configuration Manager 클라이언트와 동일하게 통신을 시뮬레이션하는 데 사용합니다.  

4. **시작**을 선택하여 분석을 시작합니다. 분석기 창에 결과가 표시됩니다. 설명 필드에서 자세한 내용을 보려면 항목을 선택합니다.  

