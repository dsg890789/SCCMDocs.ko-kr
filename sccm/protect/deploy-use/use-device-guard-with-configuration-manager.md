---
title: Windows Device Guard 관리 방법
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 Windows Device Guard를 관리하는 방법을 알아봅니다.
ms.date: 12/19/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39ffdff0b9cd84e0eb0c48754bf95a46fc52f30c
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65493834"
---
# <a name="device-guard-management-with-configuration-manager"></a>Configuration Manager로 Device Guard 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="introduction"></a>소개
Device Guard는 맬웨어와 기타 신뢰할 수 없는 소프트웨어로부터 PC를 보호하도록 설계된 Windows 10 기능 그룹입니다. 사용자가 알고 있는 승인된 코드만 실행할 수 있도록 하여 악의적인 코드가 실행되지 못하게 합니다.

Device Guard는 소프트웨어 및 하드웨어 기반 보안 기능을 모두 포함합니다. Windows Defender 애플리케이션 제어는 PC에서 실행할 수 있는 명시적인 소프트웨어 목록을 적용하는 소프트웨어 기반 보안 계층입니다. 자체적으로 애플리케이션 제어에는 하드웨어 또는 펌웨어 필수 구성 요소가 없습니다. Configuration Manager와 함께 배포된 애플리케이션 제어 정책을 사용하면 이 문서에서 설명하는 최소 Windows 버전 및 SKU 요구 사항을 충족하는 대상 컬렉션의 PC에서 정책을 사용할 수 있습니다. 선택적으로 Configuration Manager를 통해 배포된 애플리케이션 제어 정책의 하이퍼바이저 기반 보호는 가능한 하드웨어의 그룹 정책을 통해 사용할 수 있습니다.

Device Guard에 대한 자세한 내용은 [Device Guard 배포 가이드](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)를 참조하세요.

   > [!NOTE]
   > Windows 10 버전 1709부터 구성 가능한 코드 무결성 정책을 Windows Defender 애플리케이션 제어라고 합니다.

## <a name="using-device-guard-with-configuration-manager"></a>Configuration Manager에서 Device Guard 사용

Configuration Manager를 사용하여 Windows Defender 애플리케이션 제어 정책을 배포할 수 있습니다. 이 정책을 사용하면 Device Guard가 컬렉션의 PC에서 실행되는 모드를 구성할 수 있습니다. 

다음 모드 중 하나를 구성할 수 있습니다.

1.  **적용 사용** - 신뢰할 수 있는 실행 파일만 실행할 수 있습니다.
2.  **감사 전용** - 모든 실행 파일을 실행할 수 있지만, 실행되는 신뢰할 수 없는 실행 파일을 로컬 클라이언트 이벤트 로그에 로깅합니다.

>[!TIP]
>이 버전의 Configuration Manager에서 Device Guard는 시험판 기능입니다. 이 기능을 사용하도록 설정하려면 [System Center Configuration Manager의 시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

## <a name="what-can-run-when-you-deploy-a-windows-defender-application-control-policy"></a>Windows Defender 애플리케이션 제어 정책을 배포할 때 실행할 수 있는 항목

Windows Device Guard를 사용하면 사용자가 관리하는 PC에서 실행할 수 있는 사항을 철저하게 제어할 수 있습니다. 이 기능은 원하지 않는 소프트웨어가 실행되지 못하게 하는 것이 중요한 높은 수준의 보안이 요구되는 부서의 PC에 특히 유용할 수 있습니다.

정책을 배포할 때 일반적으로 다음과 같은 실행 파일을 실행할 수 있습니다.

- Windows 운영 체제 구성 요소
- Windows Hardware Quality Labs 시그니처가 있는 하드웨어 개발자 센터 드라이버
- Windows 스토어 앱
- Configuration Manager 클라이언트 
- Windows Defender 애플리케이션 제어 정책이 처리된 후 PC에서 설치한 Configuration Manager를 통해 배포되는 모든 소프트웨어 
- Windows 구성 요소 업데이트 소스:
    - Windows Update
    - Windows Update for Business
    - Windows Server Update Services
    - Configuration Manager
    - 선택적으로, Microsoft ISG(Intelligent Security Graph)에서 결정된 대로 평판이 좋은 소프트웨어입니다. ISG에는 Windows Defender SmartScreen 및 기타 Microsoft 서비스가 포함되어 있습니다. 신뢰할 수 있는 소프트웨어가 되도록 하려면 디바이스에서 Windows Defender SmartScreen 및 Windows 10 버전 1709 이상을 실행해야 합니다.

>[!IMPORTANT]
>이러한 항목에 설치에 사용하는 방식(앞서 언급된 업데이트 메커니즘 또는 인터넷)과 상관없이 인터넷 또는 타사 소프트웨어 업데이트에서 자동으로 업데이트되는 Windows에 기본으로 제공되지 *않는* 소프트웨어는 포함되지 않습니다. Configuration Manager 클라이언트를 통해 배포된 소프트웨어 변경 사항만 실행할 수 있습니다.

## <a name="before-you-start"></a>시작하기 전에

Windows Defender 애플리케이션 제어 정책을 구성하거나 배포하기 전에 다음 정보를 참조하세요.

- Device Guard 관리는 Configuration Manager의 시험판 기능이므로 변경될 수 있습니다.
- Configuration Manager에서 Device Guard를 사용하려면 관리하는 PC에서 Windows 10 Enterprise 버전 1703 이상이 실행 중이어야 합니다.
- 클라이언트 PC에서 정책을 처리하고 나면 Configuration Manager가 해당 클라이언트에서 관리되는 설치 프로그램으로 구성됩니다. 정책을 처리한 후 이를 통해 배포된 소프트웨어는 자동으로 신뢰됩니다. Windows Defender 애플리케이션 제어 정책이 처리되기 전에 Configuration Manager에서 설치한 소프트웨어는 자동으로 신뢰되지 않습니다.
- Windows Defender 애플리케이션 제어 정책을 성공적으로 처리하려면 클라이언트 PC가 도메인 컨트롤러에 연결되어 있어야 합니다.
- 배포 중에 구성할 수 있는 애플리케이션 제어 정책의 준수는 기본적으로 매일 평가하도록 예약됩니다. 정책 처리 시 문제가 발생하면 규정 준수 평가 일정을 더 짧게 구성하면 좋을 수 있습니다(예: 1시간마다). 이 일정은 장애 발생 시 클라이언트에서 Windows Defender 애플리케이션 제어 정책을 다시 처리하는 빈도를 나타냅니다.
- 선택한 적용 모드와 관계 없이 Windows Defender 애플리케이션 제어 정책을 배포할 때는 클라이언트 PC에서 .hta 확장명을 사용하는 HTML 애플리케이션을 실행할 수 없습니다.

## <a name="how-to-create-a-windows-defender-application-control-policy"></a>Windows Defender 애플리케이션 제어 정책을 만드는 방법
1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.
2.  **자산 및 준수** 작업 영역에서 **Endpoint Protection**을 확장한 다음, **Windows Defender 애플리케이션 제어**를 클릭합니다.
3.  **홈** 탭의 **만들기** 그룹에서 **애플리케이션 제어 정책 만들기**를 클릭합니다.
4.  **애플리케이션 제어 정책 만들기 마법사**의 **일반** 페이지에서 다음 설정을 지정합니다.
    - **이름** - 이 Windows Defender 애플리케이션 제어 정책에 대한 고유한 이름을 입력합니다. 
    - **설명** - 필요에 따라 Configuration Manager 콘솔에서 이 정책을 식별하는 데 도움이 되는 설명을 입력합니다.
    - **모든 프로세스에 대해 이 정책을 적용할 수 있도록 디바이스 다시 시작 적용** - 정책이 클라이언트 PC에서 처리되면 **컴퓨터 다시 시작**에 대한 **클라이언트 설정**에 따라 클라이언트에서 다시 시작이 예약됩니다.
        - Windows 10 버전 1703 이하를 실행하는 디바이스는 항상 자동으로 다시 시작됩니다.
        - Windows 10 버전 1709부터는 다시 시작한 다음에야 현재 디바이스에서 실행 중인 응용 프로그램에 새 응용 프로그램 제어 정책이 적용됩니다. 그러나 정책이 적용된 후 시작된 애플리케이션은 새 애플리케이션 제어 정책을 사용합니다. 
    - **적용 모드** - 클라이언트 PC에서 다음과 같은 Device Guard 적용 방법 중 하나를 선택합니다.
        - **적용 사용** - 신뢰할 수 있는 실행 파일만 실행할 수 있습니다.
        - **감사 전용** - 모든 실행 파일을 실행할 수 있지만, 실행되는 신뢰할 수 없는 실행 파일을 로컬 클라이언트 이벤트 로그에 로깅합니다.
5.  **애플리케이션 제어 정책 만들기 마법사**의 **포함** 탭에서 **Intelligent Security Graph에서 신뢰하는 소프트웨어 권한 부여** 를 사용할지를 선택합니다.
6. PC의 특정 파일 또는 폴더에 대한 신뢰를 추가하려면 **추가**를 클릭합니다. **신뢰할 수 있는 파일 또는 폴더 추가** 대화 상자에서 신뢰할 로컬 파일 또는 폴더 경로를 지정할 수 있습니다. 또한 연결할 권한이 있는 원격 디바이스에서 파일 또는 폴더 경로를 지정할 수도 있습니다. Windows Defender 애플리케이션 제어 정책에서 특정 파일 또는 폴더에 대한 신뢰를 추가하면 다음을 수행할 수 있습니다.
    - 관리되는 설치 관리자 동작 문제 해결
    - Configuration Manager로 배포할 수 없는 LOB(기간 업무) 앱 신뢰
    - 운영 체제 배포 이미지에 포함된 앱 신뢰 
8.  **다음**을 클릭하여 마법사를 완료합니다.

>[!IMPORTANT]
>Configuration Manager 클라이언트의 버전 1706 이상을 실행하는 클라이언트 PC에서만 신뢰할 수 있는 파일 또는 폴더를 포함하도록 지원됩니다. 모든 포함 규칙이 Windows Defender 애플리케이션 제어 정책에 포함되어 있고 정책이 Configuration Manager 클라이언트에서 이전 버전을 실행하는 클라이언트 PC에 배포되는 경우 정책이 적용되지 않습니다. 이전 클라이언트를 업그레이드하여 이 문제를 해결합니다. 포함 규칙을 포함하지 않는 정책은 여전히 이전 버전의 Configuration Manager 클라이언트에 적용될 수 있습니다.

## <a name="how-to-deploy-a-windows-defender-application-control-policy"></a>Windows Defender 애플리케이션 제어 정책을 배포하는 방법
1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.
2.  **자산 및 준수** 작업 영역에서 **Endpoint Protection**을 확장한 다음, **Windows Defender 애플리케이션 제어**를 클릭합니다.
3.  정책 목록에서 배포하려는 정책을 선택하고 **홈** 탭의 **배포** 그룹에서 **애플리케이션 제어 정책 배포**를 클릭합니다.
4.  **애플리케이션 제어 정책 배포** 대화 상자에서 정책을 배포하려는 컬렉션을 선택합니다. 그런 다음 클라이언트에서 정책을 평가하는 일정을 구성합니다. 마지막으로 클라이언트에는 구성된 모든 유지 관리 기간 외에도 정책을 평가할 수 있는지 여부를 선택합니다.
5.  작업을 마쳤으면 **확인**을 클릭하여 정책을 배포합니다. 

<!--Reworked article to put this inline while working on VSO 1355092
### Restarting the device after deploying the policy

After the policy is processed on a client PC, a restart is scheduled on that client according to the **Client Settings** for **Computer Restart**. A restart is not required to apply policies, but it is the default. If you want to turn off restarts, follow these steps:

1. Open the **Create Windows Defender Application Policy** wizard.
2. On the **General** page, clear the check box for **Enforce a restart of devices so that this policy can be enforced for all processes**.
3. Click **Next** until the wizard completes.-->


## <a name="how-to-monitor-a-windows-defender-application-control-policy"></a>Windows Defender 애플리케이션 제어 정책을 모니터링하는 방법

모든 PC에 올바르게 적용되었는지 확인하기 위해 [준수 설정 모니터링](/sccm/compliance/deploy-use/monitor-compliance-settings) 문서의 정보를 사용하여 배포된 정책이 모든 PC에 올바르게 적용되었는지 모니터링할 수 있습니다.

Windows Defender 애플리케이션 제어 정책의 처리를 모니터링하려면 클라이언트 PC에서 다음 로그 파일을 사용합니다.

**%WINDIR%\CCM\Logs\DeviceGuardHandler.log**

차단 또는 감사되는 특정 소프트웨어를 확인하려면 다음 로컬 클라이언트 이벤트 로그를 참조하세요.

1.  실행 파일을 차단하고 감사하려면 **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **코드 무결성** > **운영**을 사용합니다.
2.  Windows Installer 및 스크립트 파일을 차단하고 감사하려면 **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **AppLocker** > **MSI 및 스크립트**를 사용합니다.

<!--Reworked article to put this inline while working on VSO 1355092
## Automatically let software run if it is trusted by Intelligent Security Graph

You can let locked-down devices run software with a good reputation as determined by the Microsoft Intelligent Security Graph (ISG). The ISG includes [Windows Defender SmartScreen](https://docs.microsoft.com/windows/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) and other Microsoft services. The devices must be running Windows Defender SmartScreen for this software to be trusted.

1. Open the **Create Windows Defender Application Policy** wizard.
2. On the **Inclusions** page, check the box for **Authorize software that is trusted by the Intelligent Security Graph**.
3. Click **Next** until the wizard completes.
-->


## <a name="security-and-privacy-information-for-device-guard"></a>Device Guard의 보안 및 개인 정보

- 이 시험판 버전의 경우 프로덕션 환경에서 Windows Defender 애플리케이션 제어 정책을 **감사만** 적용 모드로 배포하지 마세요. 이 모드는 랩 설정에서만 기능을 테스트하는 데 도움이 됩니다.
- **감사만** 또는 **적용 사용** 모드에서 정책을 배포했으며 정책을 적용하기 위해 다시 시작하지 않은 디바이스는 신뢰할 수 없는 소프트웨어 설치에 취약합니다.
이 경우 디바이스를 다시 시작하거나 **적용 사용** 모드에서 정책을 받아도 소프트웨어가 계속 실행될 수 있습니다.
- Windows Defender 응용 프로그램 제어 정책이 유효한지 확인하려면 랩 환경에서 디바이스를 준비합니다. 그런 다음 **적용 사용** 정책을 배포하고 마지막으로 최종 사용자에게 디바이스를 제공하기 전에 디바이스를 다시 시작합니다.
- **적용 사용**으로 정책을 배포한 후, 나중에 **감사 전용**으로 동일한 디바이스에 정책을 배포하지 마세요. 이 구성을 사용하면 신뢰할 수 없는 소프트웨어가 실행될 수 있습니다.
- Configuration Manager를 사용하여 Windows Defender 애플리케이션 제어를 클라이언트 PC에서 사용하도록 설정하는 경우 이 정책은 로컬 관리자 권한이 있는 사용자가 애플리케이션 제어 정책을 우회하거나 그렇지 않고 신뢰할 수 없는 소프트웨어를 실행하는 것을 차단하지 않습니다. 
- 로컬 관리자 권한이 있는 사용자가 애플리케이션 제어를 사용 안 함으로 설정하지 못하게 하는 유일한 방법은 서명된 이진 파일을 배포하는 것입니다. 이 배포 방법은 그룹 정책을 통해 가능하지만 현재 Configuration Manager에서는 지원되지 않습니다.
- 클라이언트 PC에서 Configuration Manager를 관리된 설치 프로그램으로 설정하면 AppLocker 정책을 사용합니다. AppLocker는 관리되는 설치 프로그램을 식별하는 데만 사용하고 모든 적용은 Windows Defender Application Control을 통해 수행됩니다. 




