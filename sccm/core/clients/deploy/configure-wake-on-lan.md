---
title: "Wake on LAN 구성 | Microsoft 문서"
description: "System Center Configuration Manager의 Wake on LAN 설정을 선택합니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b475a0c8-85d6-4cc4-b11f-32c0cc98239e
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 55c953f312a9fb31e7276dde2fdd59f8183b4e4d
ms.openlocfilehash: 09f8bc7ee04ff64934030f825a791bc043341963
ms.lasthandoff: 12/16/2016

---
# <a name="how-to-configure-wake-on-lan-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Wake on LAN을 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

소프트웨어 업데이트, 응용 프로그램, 작업 순서, 프로그램과 같은 필수 소프트웨어를 설치하기 위한 컴퓨터의 절전 모드를 해제하려는 경우 System Center Configuration Manager에 대한 Wake on LAN 설정을 지정합니다.

절전 모드 해제 프록시 클라이언트 설정을 사용하여 Wake on LAN을 보완할 수 있습니다. 그러나 절전 모드 해제 프록시를 사용하려면 먼저 사이트에 Wake on LAN을 사용하도록 설정하고 **절전 모드 해제 패킷만 사용** 을 지정하고 Wake on LAN 전송 방법에 **유니캐스트** 옵션을 지정합니다. 이 절전 모드 해제 방법은 원격 데스크톱 연결과 같은 임시 연결도 지원합니다.

기본 사이트에 Wake on LAN을 구성하려면 아래 첫 번째 절차를 따릅니다. 그런 다음 두 번째 절차에 따라 절전 모드 해제 프록시 클라이언트 설정을 구성합니다. 이 두 번째 절차는 계층의 모든 컴퓨터에 적용할 절전 모드 해제 프록시 설정에 대한 기본 클라이언트 설정을 구성합니다. 이러한 설정이 선택한 컴퓨터에만 적용되도록 하려면 사용자 지정 장치 설정을 만들어서 절전 모드 해제 프록시를 구성할 컴퓨터가 포함된 컬렉션에 할당합니다. 사용자 지정 클라이언트 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)섹션을 참조하십시오.

절전 모드 해제 프록시 클라이언트 설정을 수신하는 컴퓨터는 네트워크 연결이 1-3초 동안 일시 중지됩니다. 이는 절전 모드 해제 프록시 드라이버를 사용하기 위해 클라이언트가 네트워크 인터페이스 카드를 재설정해야 하기 때문입니다.

> [!WARNING]
> 네트워크 서비스의 예상치 못한 중단을 방지하려면 먼저 격리된 전형적인 네트워크 인프라에서 절전 모드 해제 프록시를 평가합니다. 그런 다음 사용자 지정 클라이언트 설정을 사용하여 여러 서브넷의 선택한 컴퓨터 그룹으로 테스트를 확장합니다. 절전 모드 해제 프록시 작동 방식에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트의 절전 모드 해제 계획](../../../core/clients/deploy/plan/plan-wake-up-clients.md)을 참조하세요.

## <a name="to-configure-wake-on-lan-for-a-site"></a>사이트에 대한 Wake on LAN을 구성하려면

1. Configuration Manager 콘솔에서 **관리 > 사이트 구성 > 사이트**로 이동합니다.
2. 구성할 기본 사이트를 클릭한 다음 **속성**을 클릭합니다.
3. **Wake on LAN** 탭을 클릭하고 이 사이트에 필요한 옵션을 구성합니다. 절전 모드 해제 프록시를 지원하려면 **절전 모드 해제 패킷만 사용** 및 **유니캐스트**를 선택해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트의 절전 모드 해제 계획](../../../core/clients/deploy/plan/plan-wake-up-clients.md)을 참조하세요.
4. **확인**을 클릭하여 계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.

## <a name="to-configure-wake-up-proxy-client-settings"></a>절전 모드 해제 프록시 클라이언트 설정을 구성하려면

1. Configuration Manager 콘솔에서 **관리 > 클라이언트 설정**으로 이동합니다.
2. **기본 클라이언트 설정**을 클릭한 다음 **속성**을 클릭합니다.
3. **전원 관리**를 선택한 다음 **절전 모드 해제 프록시 사용**에 대해 **예**를 선택합니다.
4. 검토하고 필요한 경우 다른 절전 모드 해제 프록시 설정을 구성합니다. 이러한 설정에 대한 자세한 내용은 [전원 관리 설정](../../../core/clients/deploy/about-client-settings.md#power-management)을 참조하세요.
5. **확인**을 클릭하여 대화 상자를 닫고 **확인**을 클릭하여 기본 클라이언트 설정 대화 상자를 닫습니다.

다음 Wake On LAN 보고서를 사용하여 절전 모드 해제 프록시의 설치와 구성을 모니터링할 수 있습니다.

- 절전 모드 해제 프록시 배포 상태 요약
- 절전 모드 해제 프록시 배포 상태 정보

> [!TIP]
> 절전 모드 해제 프록시가 작동하는지 테스트하려면 절전 모드의 컴퓨터에 테스트 연결합니다. 예를 들어 해당 컴퓨터의 공유 폴더에 연결하거나 원격 데스크톱을 사용하여 컴퓨터에 연결해 봅니다. DirectAccess를 사용하는 경우 현재 인터넷상에 있는 절전 모드의 컴퓨터에 대해 동일한 테스트를 수행하여 IPv6 접두사가 작동하는지 확인합니다.

