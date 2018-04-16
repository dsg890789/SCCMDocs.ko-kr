---
title: 클라우드 관리 게이트웨이 모니터링
titleSuffix: Configuration Manager
description: CMG(클라우드 관리 게이트웨이)를 통해 클라이언트 및 네트워크 트래픽을 모니터링합니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18a98ae924b985b08aed911797b07ef0a1974420
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2018
---
# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Configuration Manager에서 클라우드 관리 게이트웨이 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

클라우드 관리 게이트웨이가 실행되고 클라이언트가 해당 서비스를 통해 연결한 후에 클라이언트 및 네트워크 트래픽을 모니터링하여 서비스 성능을 확인할 수 있습니다.



## <a name="monitor-clients"></a>클라이언트 모니터링

클라우드 관리 게이트웨이를 통해 연결된 클라이언트는 온-프레미스 클라이언트와 동일한 방식으로 Configuration Manager 콘솔에 표시됩니다. 자세한 내용은 [클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)을 참조하세요.



## <a name="monitor-traffic-in-the-console"></a>콘솔에서 트래픽 모니터링

Configuration Manager 콘솔을 사용하여 클라우드 관리 게이트웨이에서 트래픽을 모니터링합니다.

1. **관리 > 클라우드 서비스 > 클라우드 관리 게이트웨이**로 이동합니다.

2. 목록 창에서 클라우드 관리 게이트웨이를 선택합니다.

3. 세부 정보 창에서 클라우드 관리 게이트웨이 연결점 및 연결된 사이트 시스템 역할에 대한 트래픽 정보를 봅니다.



## <a name="set-up-outbound-traffic-alerts"></a>아웃바운드 트래픽 경고 설정

아웃바운드 트래픽 경고를 통해 네트워크 트래픽이 14일 임계값 수준에 가까워지면 알 수 있습니다. 클라우드 관리 게이트웨이를 만들 때 트래픽 경고를 설정할 수 있습니다. 해당 부분을 건너뛴 경우 서비스를 실행한 후에도 경고를 설정할 수 있습니다. 언제든지 경고 설정을 조정할 수 있습니다.

1. **관리 > 클라우드 서비스 > 클라우드 관리 게이트웨이**로 이동합니다.

2. 목록 창에서 클라우드 관리 게이트웨이를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

3. **경고** 탭을 클릭합니다. 임계값 및 경고를 사용하도록 설정합니다. 기가바이트(GB) 단위로 14일 데이터 임계값을 지정합니다. 또한 임계값 백분율을 지정하여 경고 수준을 높입니다.

4. 완료했으면 **확인**을 클릭합니다.



## <a name="monitor-logs"></a>로그 모니터링

클라우드 관리 게이트웨이는 많은 로그 파일에 항목을 생성합니다. 자세한 내용은 [Configuration Manager 로그](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)를 참조하세요.
