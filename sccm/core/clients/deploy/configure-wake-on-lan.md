---
title: Wake on LAN 구성
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 Wake on LAN 설정을 선택합니다.
ms.date: 08/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: b475a0c8-85d6-4cc4-b11f-32c0cc98239e
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d28b4809f3f3c615657a9d4c95af67f97b3d0b66
ms.sourcegitcommit: c60fdfb9df107c430389b69b08f9670ce5f526c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68859714"
---
# <a name="how-to-configure-wake-on-lan-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Wake on LAN을 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

컴퓨터를 절전 모드에서 해제하려는 경우 System Center Configuration Manager에 대해 Wake on LAN 설정을 지정합니다.

## <a name="bkmk_wol-1810"></a> 버전 1810부터 지원되는 Wake on LAN
<!--3607710-->
Configuration Manager 1810부터 머신의 절전 모드를 해제하는 새로운 방법이 제공됩니다. 이제 클라이언트가 사이트 서버와 동일한 서브넷에 있지 않더라도 Configuration Manager 콘솔에서 클라이언트의 절전 모드를 해제할 수 있습니다. 유지 관리를 수행하거나 디바이스를 쿼리해야 하는 경우 절전 상태의 원격 클라이언트로 인해 제한되지 않습니다. 사이트 서버는 클라이언트 알림 채널을 사용하여 동일한 원격 서브넷에서 깨어 있는 다른 클라이언트를 식별하고 해당 클라이언트를 사용하여 Wake on LAN 요청(매직 패킷)을 전송합니다. 클라이언트 알림 채널을 사용하면 라우터에 의해 포트가 종료될 수 있는 MAC 플랩을 방지할 수 있습니다. 새 버전의 Wake on LAN은 [이전 버전](#bkmk_wol-previous)과 동시에 사용하도록 설정할 수 있습니다.

### <a name="limitations"></a>제한 사항

- 대상 서브넷에 있는 하나 이상의 클라이언트가 깨어 있어야 합니다.
- 이 기능은 다음 네트워크 기술을 지원하지 않습니다.
   - IPv6
   - 802.1x 네트워크 인증
    >[!NOTE]
    > 802.1x 네트워크 인증은 하드웨어 및 해당 구성에 따라 추가 구성으로도 사용할 수 있습니다.
- 머신은 **절전 모드 해제** 클라이언트 알림을 통해 알림을 받을 때만 절전 모드에서 해제됩니다.
    - 마감일이 될 때 절전 모드에서 해제하려면 이전 버전의 Wake on LAN이 사용됩니다.
    -  이전 버전을 사용하도록 설정하지 않으면 **필수 배포를 위해 클라이언트의 최대 절전 모드를 해제하도록 Wake-On-LAN 사용** 또는 **절전 모드 해제 패킷 보내기** 설정으로 만든 배포에 대해 클라이언트 절전 모드 해제가 발생하지 않습니다.  


### <a name="security-role-permissions"></a>보안 역할 사용 권한

- 컬렉션 범주에서 **리소스 알림**

### <a name="configure-the-clients-to-use-wake-on-lan-starting-in-version-1810"></a>버전 1810부터 Wake on LAN을 사용하도록 클라이언트 구성

이전에는 네트워크 어댑터 속성에서 Wake on LAN을 사용하도록 수동으로 클라이언트를 설정해야 했습니다. Configuration Manager 1810에는 **네트워크 절전 모드 해제 허용**이라는 새 클라이언트 설정이 포함되어 있습니다. 네트워크 어댑터의 속성을 수정하는 대신 이 설정을 구성 및 배포합니다.

1. **관리** 아래에서 **클라이언트 설정**으로 이동합니다.
1. 편집하려는 클라이언트 설정을 선택하거나 배포할 새 사용자 지정 클라이언트 설정을 만듭니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.
1. **전원 관리** 클라이언트 설정 아래에서 **네트워크 절전 모드 해제 허용** 설정에 대해 **사용**을 선택합니다. 이 설정에 대한 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#power-management)를 참조하세요.

4. Configuration Manager 1902부터 새 버전의 Wake on LAN은 **Wake On LAN 포트 번호(UDP)** [클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#power-management)에 대해 지정한 사용자 지정 UDP 포트를 사용합니다. 이 설정은 Wake on LAN의 신규 및 이전 버전에서 공유됩니다.
 
<!--3605925-->

### <a name="wake-up-a-client-using-client-notification-starting-in-1810"></a>1810부터 클라이언트 알림을 사용하여 클라이언트 절전 모드 해제
 
단일 클라이언트 또는 컬렉션의 모든 절전 모드 클라이언트의 절전 모드를 해제할 수 있습니다. 컬렉션에서 이미 절전 모드가 해제된 디바이스의 경우에는 아무 작업도 수행되지 않습니다. 절전 모드에 있는 클라이언트에는 Wake On LAN 요청이 전송됩니다. 클라이언트에 절전 모드를 해제하라는 알림을 보내는 방법에 대한 자세한 내용은 [클라이언트 알림](/sccm/core/clients/manage/client-notification)을 참조하세요.

- **단일 클라이언트의 절전 모드를 해제하려면** 클라이언트를 마우스 오른쪽 단추로 클릭하고 **클라이언트 알림**으로 이동한 후 **절전 모드 해제**를 선택합니다.

   ![콘솔의 클라이언트 절전 모드 해제 알림](media/wol-wake-up-client-notification.png)

- **컬렉션에서 절전 상태인 모든 클라이언트의 절전 모드를 해제하려면:** 디바이스 컬렉션을 마우스 오른쪽 단추로 클릭하고 **클라이언트 알림**으로 이동한 후 **절전 모드 해제**를 선택합니다.
   - 기본 제공 컬렉션에는 이 작업을 실행할 수 없습니다.
   - 컬렉션에 절전 상태인 클라이언트와 절전 모드가 해제된 클라이언트가 혼합되어 있으면 절전 상태인 클라이언트에만 Wake on LAN 요청이 전송됩니다.
   - 이 작업은 Configuration Manager 콘솔이 독립 실행형 또는 자식 기본 사이트에 연결된 경우에만 활성화됩니다. 중앙 관리 사이트에 연결된 경우에는 해당 작업을 사용할 수 없습니다.

### <a name="what-to-expect-when-only-the-new-version-of-wake-on-lan-is-enabled"></a>새 버전의 Wake on LAN만 사용하도록 설정한 경우 예상되는 결과

새 버전의 Wake on LAN만 사용하도록 설정한 경우 **절전 모드 해제** 클라이언트 알림만 사용하도록 설정됩니다. 작업 순서, 소프트웨어 배포 또는 소프트웨어 업데이트 설치와 같은 배포에 마감일이 수신되면 클라이언트에 알림이 전송되지 않습니다. 절전 상태의 머신이 다시 온라인 상태가 되면 관리 지점에서 체크 인된 후에 콘솔에 반영됩니다.

Configuration Manager 버전 1902부터 Wake on LAN 포트를 지정할 수 있습니다. 이 설정은 Wake on LAN의 신규 및 이전 버전에서 공유됩니다.

### <a name="what-to-expect-when-both-versions-of-wake-on-lan-are-enabled"></a>두 버전의 Wake on LAN을 모두 사용하도록 설정한 경우 예상되는 결과

두 버전의 Wake on LAN을 모두 사용하도록 설정하면 **절전 모드 해제** 클라이언트 알림과 절전 모드 해제 마감일을 사용할 수 있습니다. 클라이언트 알림은 기존의 Wake on LAN과는 약간 다르게 작동합니다. 클라이언트 알림이 작동하는 방식에 대한 간단한 설명을 보려면 [버전 1810부터 지원되는 Wake on LAN](#bkmk_wol-1810) 섹션을 참조하세요. 새 클라이언트 설정 **네트워크 절전 모드 해제 허용**은 Wake on LAN을 허용하도록 NIC 속성을 변경합니다. 사용자 환경에 추가된 새 머신의 경우에는 더 이상 이 속성을 수동으로 변경할 필요가 없습니다. Wake on LAN의 다른 모든 기능은 변경되지 않았습니다.

버전부터 1902부터 **절전 모드 해제** 클라이언트 알림이 기존 **Wake On LAN 포트 번호(UDP)** 설정을 유지합니다.


## <a name="bkmk_wol-previous"></a>  버전 1806 이하의 Wake on LAN

소프트웨어 업데이트, 애플리케이션, 작업 순서, 프로그램과 같은 필수 소프트웨어를 설치하기 위한 컴퓨터의 절전 모드를 해제하려는 경우 System Center Configuration Manager에 대한 Wake on LAN 설정을 지정합니다.

절전 모드 해제 프록시 클라이언트 설정을 사용하여 Wake on LAN을 보완할 수 있습니다. 그러나 절전 모드 해제 프록시를 사용하려면 먼저 사이트에 Wake on LAN을 사용하도록 설정하고 **절전 모드 해제 패킷만 사용** 을 지정하고 Wake on LAN 전송 방법에 **유니캐스트** 옵션을 지정합니다. 이 절전 모드 해제 방법은 원격 데스크톱 연결과 같은 임시 연결도 지원합니다.

기본 사이트에 Wake on LAN을 구성하려면 아래 첫 번째 절차를 따릅니다. 그런 다음 두 번째 절차에 따라 절전 모드 해제 프록시 클라이언트 설정을 구성합니다. 이 두 번째 절차는 계층의 모든 컴퓨터에 적용할 절전 모드 해제 프록시 설정에 대한 기본 클라이언트 설정을 구성합니다. 이러한 설정이 선택한 컴퓨터에만 적용되도록 하려면 사용자 지정 디바이스 설정을 만들어서 절전 모드 해제 프록시를 구성할 컴퓨터가 포함된 컬렉션에 할당합니다. 사용자 지정 클라이언트 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)섹션을 참조하십시오.

절전 모드 해제 프록시 클라이언트 설정을 수신하는 컴퓨터는 네트워크 연결이 1-3초 동안 일시 중지됩니다. 이는 절전 모드 해제 프록시 드라이버를 사용하기 위해 클라이언트가 네트워크 인터페이스 카드를 재설정해야 하기 때문입니다.

> [!WARNING]
> 네트워크 서비스의 예상치 못한 중단을 방지하려면 먼저 격리된 전형적인 네트워크 인프라에서 절전 모드 해제 프록시를 평가합니다. 그런 다음 사용자 지정 클라이언트 설정을 사용하여 여러 서브넷의 선택한 컴퓨터 그룹으로 테스트를 확장합니다. 절전 모드 해제 프록시 작동 방식에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트의 절전 모드 해제 계획](../../../core/clients/deploy/plan/plan-wake-up-clients.md)을 참조하세요.


### <a name="to-configure-wake-on-lan-for-a-site-for-version-1806-and-earlier"></a>버전 1806 이하의 사이트에 대해 Wake on LAN을 구성하려면

 Wake on LAN을 사용하려면 계층 구조의 각 사이트에 대해 이 기능을 사용하도록 설정해야 합니다.

1. Configuration Manager 콘솔에서 **관리 > 사이트 구성 > 사이트**로 이동합니다.
2. 구성할 기본 사이트를 클릭한 다음 **속성**을 클릭합니다.
3. **Wake on LAN** 탭을 클릭하고 이 사이트에 필요한 옵션을 구성합니다. 절전 모드 해제 프록시를 지원하려면 **절전 모드 해제 패킷만 사용** 및 **유니캐스트**를 선택해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트의 절전 모드 해제 계획](../../../core/clients/deploy/plan/plan-wake-up-clients.md)을 참조하세요.
4. **확인**을 클릭하여 계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.

![사이트 속성에서 Wake On LAN을 사용하도록 설정](media/wol-site-properties.png)

### <a name="to-configure-wake-up-proxy-client-settings"></a>절전 모드 해제 프록시 클라이언트 설정을 구성하려면

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
