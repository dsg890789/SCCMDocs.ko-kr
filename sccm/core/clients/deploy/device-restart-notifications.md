---
title: 디바이스 다시 시작 알림
titleSuffix: Configuration Manager
description: Configuration Manager의 다양한 클라이언트 설정을 위한 다시 시작 알림 동작
ms.date: 08/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 5ef1bff8-9733-4b5a-b65f-26b94accd210
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e057a7391bbdbe697b7f53c13a90a74efe22635
ms.sourcegitcommit: c60fdfb9df107c430389b69b08f9670ce5f526c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68859647"
---
# <a name="device-restart-notifications-in-configuration-manager"></a>Configuration Manager에서 디바이스 다시 시작 알림

*적용 대상: System Center Configuration Manager(현재 분기)*

디바이스 다시 시작 보류 중에 대해 사용자가 받는 알림은 [컴퓨터 다시 시작 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#computer-restart) 및 사용 중인 Configuration Manager 버전에 따라 달라질 수 있습니다. 이 문서는 디바이스 다시 시작 보류 중 알림의 사용자 환경을 관리자가 결정하는 데 도움이 됩니다.

>[!NOTE]
> - 이 문서에서는 Configuration Manager 버전 1902 및 버전 1906에 있는 클라이언트 설정을 주로 설명합니다.


## <a name="deployment-types-for-restart-notifications"></a>다시 시작 알림의 배포 유형

[컴퓨터 다시 시작 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#computer-restart)은 다음 유형의 다시 시작이 필요한 모든 필수 배포의 사용자 환경을 변경합니다.

- [애플리케이션](/sccm/apps/deploy-use/deploy-applications)
- [작업 순서](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS)
- [소프트웨어 업데이트](/sccm/sum/deploy-use/deploy-software-updates)

## <a name="restart-notification-types"></a>다시 시작 알림 유형

다시 시작이 필요한 경우 최종 사용자에게 예정된 다시 시작 알림이 제공됩니다. 사용자가 받을 수 있는 네 가지 일반적인 알림은 다음과 같습니다.

다시 시작이 필요하다고 알리는 **알림 메시지**. 알림 메시지의 정보는 실행 중인 Configuration Manager 버전에 따라 다를 수 있습니다. 이 알림 유형은 Windows OS에 기본으로 사용 되며, 타사 소프트웨어에서도 이러한 유형의 알림이 사용되는 것을 볼 수 있습니다.

![다시 시작 보류 중 알림 메시지](media/3555947-restart-toast.png)

다시 시작이 적용되기까지 남은 시간을 보여 주는 다시 알림 옵션이 포함된 소프트웨어 센터 알림입니다. 메시지는 Configuration Manager 버전에 따라 다를 수 있습니다.

![다시 알림 단추가 포함된 다시 시작 보류 중 소프트웨어 센터 알림](media/3976435-snooze-restart-countdown.png)

사용자가 닫을 수 없는 소프트웨어 센터 최종 카운트다운 알림입니다. 다시 알림 단추는 회색으로 표시됩니다.

![소프트웨어 센터 최종 카운트다운 알림](media/3976435-final-restart-countdown.png)

다시 시작이 필요한 필수 소프트웨어를 사용자가 최종 기한 전에 미리 설치하는 경우 다른 알림이 표시됩니다. 다음 알림은 사용자 환경 설정에서 알림을 허용하는 경우 및 배포에 대한 알림 메시지를 사용하지 않는 경우에 발생합니다. 이러한 설정을 구성하는 자세한 방법은 [배포 **사용자 환경** 설정](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy-ux) 및 [필수 배포의 사용자 알림](/sccm/apps/deploy-use/deploy-applications#bkmk_notify)을 참조하세요.

![미리 설치된 소프트웨어에 대한 알림](media/3976435-proactive-user-restart-notification.png)

- 알림 메시지를 사용하지 않는 경우 **사용 가능**으로 표시된 소프트웨어의 대화 상자는 미리 설치된 소프트웨어와 비슷합니다.

  - **사용 가능한** 소프트웨어의 경우 알림에 다시 시작 최종 기한이 없으며 사용자는 다시 알림 간격을 선택할 수 있습니다. 자세한 내용은 [승인 설정](/sccm/apps/deploy-use/deploy-applications#bkmk_approval)을 참조하세요.

    !["사용 가능"으로 표시된 소프트웨어는 알림에다시 시작 최종 기한이 없습니다.](media/3555947-deployment-marked-available-restart.png)

## <a name="device-restart-notifications-in-version-1902"></a>버전 1902의 디바이스 다시 시작 알림

<!--3555947-->
사용자가 다시 시작이나 필요한 배포에 대한 Windows 알림 메시지를 보지 못하고 지나치는 경우가 있습니다. 이 경우 알림을 반복 설정하는 기능도 보지 못하게 됩니다. 이는 클라이언트가 기한에 도달했을 때 사용자 환경을 저하할 수 있습니다.

버전 1902부터 소프트웨어 변경이 필요하거나 배포 시 다시 시작이 필요한 경우 더 간섭적인 대화 상자 창을 사용할 수 있습니다.

클라이언트 설정의 [컴퓨터 다시 시작](/sccm/core/clients/deploy/about-client-settings#computer-restart) 그룹에서 다음 옵션을 사용하도록 설정합니다. **배포를 다시 시작해야 하는 경우 알림 메시지 대신 사용자에게 대화 상자 창 표시**.  

이 클라이언트 설정을 구성하면 알림 메시지에서 다시 시작을 요구하는 모든 필수 배포의 사용자 환경이 변경됩니다.

![다시 시작이 필요하다는 알림 메시지](media/3555947-restart-toast-initial.png)  

더 간섭적인 소프트웨어 센터 대화 상자 창:

![컴퓨터를 다시 시작하라는 대화 상자 창](media/3976435-proactive-user-restart-notification.png)

설치 후 디바이스를 다시 시작하지 않은 사용자는 미리 알림 형식으로 알림을 받게 됩니다. 이 임시 미리 알림은 클라이언트 설정에 따라 사용자에게 표시됩니다. **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**. 이 설정은 컴퓨터가 강제로 다시 시작되기 전에 사용자가 컴퓨터를 다시 시작해야 하는 전체 시간입니다.

- 알림 메시지를 사용하는 경우 임시 알림:

  ![다시 시작 보류 중 알림 메시지](media/3555947-restart-toast.png)

- 알림 메시지가 아닌 소프트웨어 센터 대화 상자 창을 사용하는 경우의 임시 알림:

  ![다시 알림 단추가 포함된 다시 시작 보류 중 소프트웨어 센터 알림](media/3555947-1902-hide-notification.png)

임시 알림 후에 다시 시작하지 않는 사용자에게는 사용자가 닫을 수 없는 최종 카운트다운 알림이 제공됩니다. 최종 알림이 표시되는 시기는 클라이언트 설정에 따라 달라집니다. **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 카운트다운 간격(분)을 표시하는 대화 상자 표시(사용자가 닫을 수 없음)** . 예를 들어 설정이 60인 경우 강제로 다시 부팅되기 1시간 전에 최종 알림이 사용자에게 표시됩니다.

![소프트웨어 센터 최종 카운트다운 알림](media/3555947-1902-final-countdown.png)

다음 설정은 컴퓨터에 적용된 최단 [유지 관리 기간](/sccm/core/clients/manage/collections/use-maintenance-windows)보다 기간이 짧아야 합니다.

- **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**
- **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 카운트다운 간격(분)을 표시하는 대화 상자 표시(사용자가 닫을 수 없음)**

> [!IMPORTANT]
> Configuration Manager 1902에서 경우에 따라 대화 상자가 알림 메시지를 바꾸지 않습니다. 이 문제를 해결하려면 [Configuration Manager 버전 1902용 업데이트 롤업](https://support.microsoft.com/help/4500571/update-rollup-for-configuration-manager-current-branch-1902)을 설치합니다. <!--4404715-->

## <a name="device-restart-notifications-starting-in-version-1906"></a>버전 1906부터의 디바이스 다시 시작 알림
<!--3976435-->
일부 관리자는 다시 시작 알림이 빈번하고 다시 시작을 연기할 수 있는 시간 프레임이 짧은 것을 선호합니다. 다른 관리자들은 사용자가 더 오랫동안 다시 시작을 연기하는 것을 허용하고 다시 시작 보류 중에 대해 사용자에게 가끔 알리는 것을 선호합니다. Configuration Manager 버전 1906은 다시 시작 알림 시기와 빈도에 대한 추가 제어 기능을 관리자에게 제공합니다. 다음 항목은 관리자에게 향상된 제어를 제공하기 위해 버전 1906에서 도입되었습니다.

- **컴퓨터 다시 시작 카운트다운 알림의 다시 알림 기간 지정(시간)** 이 [컴퓨터 다시 시작 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#computer-restart)에 추가되었습니다.
- **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**의 최댓값이 1440분(24시간)에서 20160분(2주)으로 늘어났습니다.
- 보류 중인 다시 시작 시간이 24시간 이내로 줄어들 때까지 다시 시작 알림의 진행률 표시줄이 표시되지 않습니다.

### <a name="notifications-when-required-software-is-installed-at-or-after-the-deadline"></a>필수 소프트웨어가 최종 기한 또는 그 이후에 설치되는 경우의 알림

필수 소프트웨어가 최종 기한 또는 그 이후에 설치되면 사용자에게는 선택한 클라이언트 설정에 따라 알림이 표시됩니다.

**배포에 다시 시작이 필요한 경우 알림 메시지 대신 사용자에게 대화 상자 창 표시** 설정이

- **아니요**로 설정되면 최종 카운트다운 알림에 도달할 때까지 알림 메시지가 사용되고,
- **예**로 설정되면 소프트웨어 센터 알림이 표시됩니다.
  - 다시 시작이 24시간 이상 남아 있다면 예상되는 다시 시작 시간이 표시됩니다. 이 알림의 시기는 다음 설정에 기반합니다. **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**.

     ![다시 시작 시간이 24시간 이상 남아 있음](media/3976435-notification-greater-than-24-hours.png)

  - 남아 있는 다시 시작 시간이 24시간 미만인 경우 진행률 표시줄이 표시됩니다. 이 알림의 시기는 다음 설정에 기반합니다. **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**

     ![다시 시작 시간이 24시간 미만 남아 있음](media/3976435-notification-less-than-24-hours.png)

사용자가 **다시 알림** 단추를 선택하면 아직 최종 카운트다운에 도달하지 않았다고 가정하여 다시 알림 기간 경과 후 또 다른 임시 알림이 발생합니다. 다음 번 알림 시기는 다음 설정에 기반합니다. **컴퓨터 다시 시작 카운트다운 알림의 다시 알림 기간 지정(시간)** . 사용자가 **다시 알림**을 선택하고 다시 알림 간격이 1시간인 경우 아직 최종 카운트다운에 도달하지 않았다고 가정하여 60분 후에 사용자에게 다시 알립니다.

최종 카운트다운에 도달하면 닫을 수 없는 알림이 사용자에게 제공됩니다. 진행률 표시줄이 빨간색으로 표시되고 사용자는 **다시 알림**을 클릭할 수 없습니다.

![버전 1906의 소프트웨어 센터 최종 카운트다운 알림](media/3976435-1906-final-restart-countdown.png)

### <a name="the-user-proactively-installs-before-the-deadline"></a>사용자가 최종 기한 전에 미리 설치

다시 시작이 필요한 필수 소프트웨어를 사용자가 최종 기한 전에 미리 설치하는 경우 다른 알림이 표시됩니다. 이러한 설정을 구성하는 자세한 방법은 [배포 **사용자 환경** 설정](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy-ux) 및 [필수 배포의 사용자 알림](/sccm/apps/deploy-use/deploy-applications#bkmk_notify)을 참조하세요. 

다음 알림은 사용자 환경 설정에서 알림을 허용하는 경우 및 배포에 대한 알림 메시지를 사용하지 않는 경우에 발생합니다.

![미리 설치된 소프트웨어에 대한 알림](media/3976435-proactive-user-restart-notification.png)

소프트웨어 최종 기한에 도달하면 [필수 소프트웨어를 최종 기한 또는 그 이후에 설치하는 경우의 알림](#notifications-when-required-software-is-installed-at-or-after-the-deadline) 동작에 따릅니다.

## <a name="log-files"></a>로그 파일

디바이스 다시 시작 문제 해결에 **RebootCoordinator.log** 및 **SCNotify.log**를 사용하세요. 사용된 배포 유형에 따라 추가적인 클라이언트 [로그 파일](/sccm/core/plan-design/hierarchy/log-files)을 사용해야 할 수도 있습니다.

## <a name="next-steps"></a>다음 단계

- [애플리케이션 관리 소개](/sccm/apps/understand/introduction-to-application-management)
- [운영 체제 배포 소개](/sccm/osd/understand/introduction-to-operating-system-deployment)
- [소프트웨어 업데이트 관리 소개](/sccm/sum/understand/software-updates-introduction)
