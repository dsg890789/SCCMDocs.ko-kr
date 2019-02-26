---
title: 공동 관리 사용
titleSuffix: Configuration Manager
description: 신속 하 게 공동 관리 구성 관리자의 즉각적인 가치를 얻을 수를 사용 하도록 설정 합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 8fac7ac5-96a3-4ec1-85cb-623b26bf5b1c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 37dce37551627394da2630fa591a3c803ae8343f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755414"
---
# <a name="how-to-enable-co-management-in-configuration-manager"></a>Configuration Manager에서 공동 관리를 사용 하는 방법

공동 관리를 사용 하면 즉각적인 가치를 얻을 수 있습니다. 그런 다음 준비가 되 면 사용자 환경에서 필요에 따라 워크 로드를 전환를 시작할 수 있습니다.

이 프로세스를 시작 하기 전에 공동 관리 사전 요구 사항 설정 되었는지 확인 합니다. 자세한 내용은 [필수 구성 요소](/sccm/comanage/overview#prerequisites)를 참조하세요.



## <a name="process"></a>프로세스

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다. 리본에서 **공동 관리 구성**을 클릭하여 **공동 관리 등록 마법사**를 엽니다.  

2. 에 **구독** 마법사의 페이지 **로그인**합니다. Intune 테넌트에 로그인한 다음, **다음**을 선택합니다.  

3. 에 **사용** 페이지를 선택 하 **Intune에 자동 등록** 설정 하거나 **파일럿** 또는 **모든**합니다.   

    이 작업을 통해 기존 Configuration Manager 클라이언트에 대 한 Intune에서 자동 클라이언트 등록 합니다. **파일럿**을 선택하는 경우 파일럿 컬렉션의 멤버인 Configuration Manager 클라이언트만이 Intune에 자동으로 등록됩니다. 이 옵션을 사용하면 클라이언트의 하위 집합에서 공동 관리를 사용하여 처음에 공동 관리를 테스트하고 단계적 접근을 사용하여 공동 관리를 롤아웃할 수 있습니다.  

    > [!Note]  
    > 버전 1806부터 자동 등록은 모든 클라이언트에 대해 직접 실행되지 않습니다. 이 동작은 대규모 환경에 대해 등록 확장을 보다 잘 수행하게 합니다. Configuration Manager는 클라이언트 수에 따라 등록을 임의 지정합니다. 예를 들어 사용자 환경에 100,000명의 클라이언트가 있는 경우 이 설정을 사용하도록 설정하면 며칠에 걸쳐 등록이 가능합니다.<!--1358003-->  

    Intune에 이미 등록 된 인터넷 기반 장치에 있는 경우이 페이지의 명령줄을 복사 합니다. Intune에서 앱으로 Configuration Manager 클라이언트를 설치 하려면이 명령줄을 사용할 수 있습니다.

4. **워크로드** 페이지에서 각 워크로드에 대해 Intune으로 관리하기 위해 이동할 디바이스 그룹을 선택합니다. 자세한 내용은 [워크 로드](/sccm/comanage/workloads)합니다.  

    공동 관리를 사용 하도록 설정 하려는 경우에 이제 워크 로드를 전환할 필요가 없습니다. 나중에 워크 로드를 전환할 수 있습니다. 자세한 내용은 [워크 로드를 전환 하는 방법을](/sccm/comanage/how-to-switch-workloads)합니다.  

    **Pilot Intune** 설정은 파일럿 컬렉션의 디바이스에 대해서만 관련된 워크로드를 전환합니다. **Intune** 설정은 공동 관리되는 모든 Windows 10 디바이스에 대해 관련된 워크로드를 전환합니다.  

    > [!Important] 
    > 워크 로드를 전환 하기 전에 제대로 구성 하 고 Intune에서 해당 워크 로드를 배포에 있는지 확인 합니다. 워크로드가 항상 디바이스에 대한 관리 도구 중 하나에서 관리되어야 합니다.  

5. 에 **스테이징** 페이지에서 다음 설정을 구성 합니다.  

    - **파일럿**: 파일럿 그룹에는 선택한 컬렉션이 하나 이상 포함되어 있습니다. 이 그룹을 공동 관리의 단계별 롤아웃 중 일부로 사용합니다. 작은 테스트 컬렉션으로 시작한 다음, 공동 관리를 더 많은 사용자 및 디바이스에 롤아웃하는 경우 파일럿 그룹에 더 많은 컬렉션을 추가합니다. 언제든 파일럿 그룹의 컬렉션을 변경할 수 있습니다.  

    - **프로덕션:** 하나 이상의 컬렉션을 포함하여 **제외 그룹**을 구성합니다. 이 그룹에 있는 컬렉션의 멤버인 디바이스는 공동 관리를 사용하지 않도록 제외됩니다.  

6. 공동 관리를 사용하려면 마법사를 완료합니다.  



## <a name="next-steps"></a>다음 단계

공동 관리를 사용 하도록 설정한 했으므로 사용자 환경에서 얻을 수 있습니다 즉 치 값에 대 한 다음 문서를 살펴봅니다.

- [조건부 액세스](/sccm/comanage/quickstart-conditional-access)  

- [Intune에서 원격 작업](/sccm/comanage/quickstart-remote-actions)  

- [클라이언트 상태](/sccm/comanage/quickstart-client-health)  
