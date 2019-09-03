---
author: mestew
ms.author: mstewart
ms.prod: configuration-manager
ms.topic: include
ms.date: 08/23/2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4960c0b9a6c383a73766083a9e385bcd60d799d3
ms.sourcegitcommit: 04dd0c17e47763a3e2b6c44c005428ea7d67f4bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2019
ms.locfileid: "70036739"
---
<!--3555750 FKA 1357954 --Don't apply H2/H3 in this include file since they are context driven by article-->
1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다. 리본 메뉴에서 **공동 관리 구성**을 클릭하여 **공동 관리 구성 마법사**를 엽니다.

2. 마법사의 **구독** 페이지에서 다음 설정을 구성합니다.

    - 사용할 **Azure 환경**입니다. 예: Azure 퍼블릭 클라우드 또는 Azure 미국 정부 클라우드<!--4075452-->  

    - **로그인**을 선택합니다. Intune 테넌트에 로그인한 다음, **다음**을 선택합니다.  

3. **사용 여부** 페이지에서 다음 설정을 선택합니다.

   - **Intune에 자동 등록**: 기존 Configuration Manager 클라이언트에 대해 자동 클라이언트 등록을 사용하도록 설정할 수 있습니다. 이 옵션을 사용하면 클라이언트의 하위 집합에서 공동 관리를 사용하여 처음에 공동 관리를 테스트하고 단계적 접근을 사용하여 공동 관리를 롤아웃할 수 있습니다. 사용자가 디바이스를 등록 취소하는 경우, 다음 정책 평가 때 디바이스가 다시 등록됩니다. <!--3330596-->

      - **파일럿**: **Intune 자동 등록**의 멤버인 Configuration Manager 클라이언트만이 Intune에 자동으로 등록됩니다.
      - **모두**: 모든 Windows 10 버전 1709 이상 클라이언트에 대해 자동 등록을 사용하도록 설정합니다.

   - **Intune 자동 등록**: 이 컬렉션에는 공동 관리에 등록하려는 모든 클라이언트가 포함되어야 합니다. 기본적으로 다른 준비 컬렉션의 상위 세트입니다.

   ![Intune 자동 등록 컬렉션 지정 ](../media/3555750-co-management-onboarding-enablement.png)

      > [!Note]  
      > 버전 1806부터 자동 등록은 모든 클라이언트에 대해 직접 실행되지 않습니다. 이 동작은 대규모 환경에 대해 등록 확장을 보다 잘 수행하게 합니다. Configuration Manager는 클라이언트 수에 따라 등록을 임의 지정합니다. 예를 들어 사용자 환경에 100,000개의 클라이언트가 있는 경우 이 설정을 사용하도록 설정하면 며칠에 걸쳐 등록이 가능합니다.<!--1358003-->  
      >
      > 버전 1906부터 가능:
      >
      > - 이제 새 공동 관리형 디바이스는 해당 Azure AD(Azure Active Directory) *디바이스* 토큰에 따라 Microsoft Intune 서비스에 자동으로 등록됩니다. 사용자가 디바이스에 로그인하여 자동 등록을 시작할 때까지 기다릴 필요가 없습니다. 이렇게 바뀐 덕분에 등록 상태가 *사용자 로그인 보류 중*인 디바이스 수를 줄일 수 있습니다.<!-- 4454491 --> 이 동작을 지원하려면 디바이스에서 Windows 10 버전 1803 이상을 실행해야 합니다. 자세한 내용은 [공동 관리 등록 상태](/sccm/comanage/how-to-monitor#co-management-enrollment-status)를 참조하세요.
      >
      > - 이미 공동 관리에 등록된 디바이스가 있는 경우 이제 새 디바이스는 [필수 조건](/sccm/comanage/overview#prerequisites)을 충족하는 즉시 등록됩니다.<!--4321130-->

4. Intune에 이미 등록된 인터넷 기반 디바이스가 있는 경우 **등록** 페이지의 명령줄을 복사하고 저장합니다. 이 명령줄을 사용하여 인터넷 기반 디바이스의 Intune에서 Configuration Manager 클라이언트를 앱으로 설치할 수 있습니다. 이 명령줄을 지금 저장하지 않는 경우 이 명령줄을 받을 수 있도록 언제든지 공동 관리 구성을 검토할 수 있습니다.

5. **워크로드** 페이지에서 각 워크로드에 대해 Intune으로 관리하기 위해 이동할 디바이스 그룹을 선택합니다. 자세한 내용은 [Workloads](/sccm/comanage/workloads)(워크로드)를 참조하세요. 공동 관리만 사용하도록 설정하려면 지금 워크로드를 전환할 필요가 없습니다. 나중에 워크로드를 전환할 수 있습니다. 자세한 내용은 [워크로드를 전환하는 방법을](/sccm/comanage/how-to-switch-workloads)을 참조하세요.  

    - **파일럿 Intune**: **준비** 페이지에서 지정할 파일럿 컬렉션의 디바이스에 대해서만 연결된 워크로드를 전환합니다. 워크로드마다 파일럿 컬렉션이 다를 수 있습니다.
    - **Intune** - 공동 관리되는 모든 Windows 10 디바이스에 대한 관련 워크로드를 전환합니다.  

    > [!Important]
    > 워크로드를 전환하기 전에 Intune에서 해당 워크로드를 올바로 구성하고 배포해야 합니다. 워크로드가 항상 디바이스에 대한 관리 도구 중 하나에서 관리되어야 합니다.  

6. **준비** 페이지에서 **파일럿 Intune**으로 설정된 각 워크로드의 파일럿 컬렉션을 지정합니다.

   ![Intune 자동 등록 컬렉션 지정 ](../media/3555750-co-management-onboarding-staging.png)

7. 공동 관리를 사용하려면 마법사를 완료합니다.
