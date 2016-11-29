---
title: "System Center Configuration Manager용 Technical Preview 1610의 기능"
description: "System Center Configuration Manager용 Technical Preview 버전 1610에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 10/21/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: c9fe6961a63495d08a3e58e3ddf46c5d316e2613
ms.openlocfilehash: 865b5078282bf240aa6a2aef5cb2662f2471fb71

---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1610의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*



이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1610에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>자동 배포 규칙의 콘텐츠 크기에 따라 필터링
이제 자동 배포 규칙에서 소프트웨어 업데이트의 콘텐츠 크기를 기준으로 필터링할 수 있습니다. 예를 들어 **콘텐츠 크기(KB)** 필터를 **< 2048**로 설정하여 2MB보다 작은 크기의 소프트웨어 업데이트만 다운로드할 수 있습니다. 이 필터를 사용하면 큰 소프트웨어 업데이트가 자동으로 다운로드되는 것이 방지되므로 네트워크 대역폭이 제한된 경우 단순화된 Windows 하위 수준 서비스를 보다 잘 지원할 수 있습니다. 자세한 내용은 [Configuration Manager and Simplified Windows Servicing on Down Level Operating Systems](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)(Configuration Manager 및 하위 수준 운영 체제의 단순화된 Windows 서비스)를 참조하세요.

#### <a name="to-configure-the-content-size-field"></a>콘텐츠 크기 필드를 구성하려면
**콘텐츠 크기(KB)** 필드를 구성하려면 ADR을 만들 때 자동 배포 규칙 만들기 마법사의 **소프트웨어 업데이트** 페이지로 이동하거나 기존 ADR의 속성에 있는 **소프트웨어 업데이트** 탭으로 이동합니다.

![콘텐츠 크기 필드](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>필수 소프트웨어 대화 상자에 대한 향상된 기능
사용자가 필수 소프트웨어를 받으면 **다음 시간 후 다시 알림** 설정에서 다음 드롭다운 값 목록을 선택할 수 있습니다.
- 나중에: 클라이언트 에이전트 설정에 구성된 알림 설정에 따라 알림을 예약합니다.
- 고정 시간: 선택한 시간 후에 다시 표시하도록 알림을 예약합니다. 예를 들어 사용자가 30분을 선택하면 알림이 30분 후에 다시 표시됩니다.

![클라이언트 에이전트 설정의 컴퓨터 에이전트 페이지](media/computeragentsettings.png)

최대 다시 알림 시간은 항상 배포 타임라인을 따라 클라이언트 에이전트 설정에 구성된 알림 값을 기반으로 합니다. 예를 들어 컴퓨터 에이전트 페이지의 **배포 최종 기한이 24시간 미만 남은 경우 사용자에게 다음 시간마다 미리 알림(시)** 설정이 10시간으로 구성되고 대화 상자가 실행되기까지 남은 마감일이 24시간보다 큰 경우 사용자에게 일련의 다시 알림 옵션이 표시되지만 10시간 이하여야 합니다. 마감일이 가까워지면 대화 상자에게 몇 가지 옵션이 나타나는데 이 옵션은 배포 타임라인의 각 구성 요소와 관련된 클라이언트 에이전트 설정과 일치합니다.

또한 운영 체제를 배포하는 작업 순서 등 고위험성 배포의 경우 최종 사용자 알림 환경의 침투성이 더 높아졌습니다. 사용자에게 중요 소프트웨어 유지 관리 알림을 표시해야 할 때마다 임시 작업 표시줄 알림 대신 다음과 같은 대화 상자가 사용자 컴퓨터에 표시됩니다.

![필수 소프트웨어 대화 상자](media/requiredsoftwaredialog.png)


자세한 내용을 보려면 다음을 수행하십시오.
- [높은 위험 수준의 배포를 관리하는 설정](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [클라이언트 설정을 구성하는 방법](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>이전에 승인된 응용 프로그램 요청 거부

관리자는 이제 이전에 승인된 응용 프로그램 요청을 거부할 수 있습니다. 요청이 거부된 응용 프로그램을 나중에 설치하려면 요청을 다시 제출해야 합니다. 요청을 거부해도 응용 프로그램이 제거되지는 않으며 해당 응용 프로그램에 대한 해당 사용자의 새 요청을 다시 승인하도록 합니다. 이전에는 승인되지 않은 응용 프로그램 요청에 대해서만 응용 프로그램 요청을 거부할 수 있었습니다.

#### <a name="try-it-out"></a>기능 직접 사용해 보기
승인된 응용 프로그램 요청을 거부하려면:

1.  Configuration Manager 콘솔에서 승인이 필요한 [응용 프로그램을 만들고 배포합니다](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/create-applications).
2.  클라이언트 컴퓨터에서 소프트웨어 센터를 열고 응용 프로그램에 대한 요청을 제출합니다.
3.  Configuration Manager 콘솔에서 응용 프로그램 요청을 승인합니다.
4.  승인된 응용 프로그램 요청 거부: Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **승인 요청**으로 이동한 다음 거부할 응용 프로그램 요청을 선택합니다.  리본에서 **거부**를 클릭합니다.

## <a name="exclude-clients-from-automatic-upgrade"></a>자동 업그레이드에서 클라이언트 제외
Technical Preview 1610에는 업데이트된 클라이언트 버전을 자동으로 설치하지 않도록 제외할 클라이언트 컬렉션을 지정할 수 있는 설정이 새로 추가되었습니다.  이 설정은 자동 업그레이드 및 소프트웨어 업데이트 기반 업그레이드, 로그온 스크립트 및 그룹 정책 등에 적용됩니다. 클라이언트를 업그레이드할 때 주의가 필요한 컴퓨터 컬렉션에 이 설정을 사용할 수 있습니다. 제외된 컬렉션에 있는 클라이언트는 업데이트된 클라이언트 소프트웨어 설치 요청을 무시합니다.

### <a name="configure-exclusion-from-automatic-upgrade"></a>자동 업그레이드 작업의 제외 구성
자동 업그레이드 제외를 구성하려면:
1.  Configuration Manager 콘솔에서 **관리 > 사이트 구성 > 사이트** 아래의 **계층 설정**을 열고 **클라이언트 업그레이드** 탭을 선택합니다.
2.  **Exclude specified clients from upgrade**(지정된 클라이언트를 업그레이드에서 제외)의 확인란을 선택하고 **Exclusion collection**(제외 컬렉션)에서 제외할 컬렉션을 선택합니다. 제외할 컬렉션은 하나만 선택할 수 있습니다.
3.  **확인**을 클릭하여 구성을 닫고 저장합니다. 그러면 클라이언트가 정책을 업데이트한 후 제외된 컬렉션의 클라이언트가 클라이언트 소프트웨어에 대한 업데이트를 더 이상 자동으로 설치하지 않습니다.

  ![자동 업그레이드 제외에 대한 설정](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> 사용자 인터페이스에는 어떠한 방법으로도 클라이언트가 업그레이드되지 않는다고 명시되어 있지만 두 가지 방법을 통해 이러한 설정을 재정의할 수 있습니다. 클라이언트 강제 설치 및 수동 클라이언트 설치를 사용하여 이 구성을 재정의할 수 있습니다. 자세한 내용은 다음 섹션을 참조하세요.


### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>제외된 컬렉션에 있는 클라이언트를 업그레이드하는 방법
컬렉션이 제외되도록 구성하면 해당 컬렉션의 멤버가 다음 두 가지 방법 중 하나를 사용하여 제외를 재정의해야만 클라이언트 소프트웨어를 업그레이드할 수 있습니다.
 - **클라이언트 강제 설치** – 클라이언트 강제 설치를 사용하여 제외된 컬렉션에 있는 클라이언트를 업그레이드할 수 있습니다. 이 방법은 관리자의 의도인 것으로 간주되고 전체 컬렉션을 제외에서 제거하지 않고 클라이언트를 업그레이드할 수 있습니다.       
 - **수동 클라이언트 설치** – ccmsetup과 명령줄 스위치 ***/ignoreskipupgrade***를 함께 사용하면 제외된 컬렉션에 있는 클라이언트를 수동으로 업그레이드할 수 있습니다.

  제외된 컬렉션의 멤버인 클라이언트를 수동으로 업그레이드할 때 이 스위치를 사용하지 않으면 새 클라이언트 소프트웨어가 설치되지 않습니다. 자세한 내용은 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually)을 참조하세요.

클라이언트 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.


## <a name="see-also"></a>참고 항목
[System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)



<!--HONumber=Nov16_HO1-->


