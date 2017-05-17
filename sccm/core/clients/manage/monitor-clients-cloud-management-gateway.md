---
title: "클라우드 관리 게이트웨이 모니터링 - Configuration Manager | Microsoft 문서"
description: 
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: df32a7d95799d8ae685fd66e2d9ddf25e32b37d0
ms.contentlocale: ko-kr
ms.lasthandoff: 03/27/2017

---

# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Configuration Manager에서 클라우드 관리 게이트웨이 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1610부터 클라우드 관리 게이트웨이 서비스가 실행되고 클라이언트가 해당 서비스를 통해 연결한 후 클라이언트 및 네트워크 트래픽을 모니터링하여 서비스 성능을 확인할 수 있습니다.

## <a name="monitor-clients"></a>클라이언트 모니터링

클라우드 관리 게이트웨이 서비스를 통해 연결된 클라이언트는 온-프레미스 클라이언트와 동일한 방식으로 Configuration Manager 콘솔에 표시됩니다. 자세한 내용은 [클라이언트를 모니터링하는 방법](monitor-clients.md)을 참조하세요.

## <a name="monitor-traffic-in-the-console"></a>콘솔에서 트래픽 모니터링

Configuration Manager 콘솔을 사용하여 클라우드 관리 게이트웨이에서 트래픽을 모니터링할 수 있습니다.

1. **관리 > 클라우드 서비스 > 클라우드 관리 게이트웨이**로 이동합니다.

2. 목록 창에서 클라우드 관리 게이트웨이 서비스를 선택합니다.

3. 세부 정보 창에서 클라우드 관리 게이트웨이 연결 역할 및 이 역할이 연결하는 사이트 시스템 역할에 대한 트래픽 정보를 봅니다.

## <a name="set-up-outbound-traffic-alerts"></a>아웃바운드 트래픽 경고 설정

아웃바운드 트래픽 경고는 트래픽이 14일(2주) 임계값 수준에 가까워지면 알려줍니다. 클라우드 관리 게이트웨이 서비스를 만들 때 트래픽 경고를 설정하는 옵션이 제공됩니다. 해당 부분을 건너뛴 경우 서비스를 실행한 후에도 경고를 설정할 수 있습니다. 또한 언제든지 경고 설정을 조정할 수 있습니다.

1. **관리 > 클라우드 서비스 > 클라우드 관리 게이트웨이**로 이동합니다.

2. 목록 창에서 클라우드 관리 게이트웨이 서비스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

3. 경고 탭을 클릭하고 임계값 및 경고를 켜거나 끄도록 선택합니다. 그런 다음 14일 임계값(GB) 및 다양한 경고 수준 발생에 대한 임계값 비율을 지정합니다.

4. 완료했으면 **확인**을 클릭합니다.

## <a name="monitor-logs"></a>로그 모니터링

클라우드 관리 게이트웨이 서비스는 많은 로그 파일에 항목을 생성합니다. 자세한 내용은 [Configuration Manager 로그](/sccm/core/plan-design/hierarchy/log-files)를 참조하세요.

