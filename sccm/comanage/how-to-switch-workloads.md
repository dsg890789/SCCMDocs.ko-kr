---
title: 공동 관리 워크로드 전환
titleSuffix: Configuration Manager
description: Configuration Manager에서 현재 관리하고 있는 워크로드를 Microsoft Intune으로 전환하는 방법을 알아봅니다.
ms.prod: configuration-manager
ms.technology: configmgr-client
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 01/14/2019
ms.topic: conceptual
ms.assetid: 60e2022f-a4f9-40dd-af01-9ecb37b43878
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4b50d0491644e6be0967c1adcf2db641c1bb1cd
ms.sourcegitcommit: 9aebc20b25cdef0af908918ccfd791f3264a5d94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "56755438"
---
# <a name="how-to-switch-configuration-manager-workloads-to-intune"></a>Configuration Manager 워크로드를 Intune으로 전환하는 방법

공동 관리의 이점 중 하나는 워크로드를 Configuration Manager에서 Microsoft Intune으로 전환하는 것입니다. Windows 10 디바이스에 Configuration Manager 클라이언트가 있고 디바이스가 Intune에 등록된 경우 두 서비스의 이점을 모두 활용할 수 있습니다. 어느 워크로드를 제어하든 기관을 Configuration Manager에서 Intune으로 전환할 수 있습니다. Intune으로 전환하지 않은 워크로드를 포함한 다른 모든 워크로드와 공동 관리에서 지원하지 않는 Configuration Manager의 다른 모든 기능은 계속 Configuration Manager에서 관리합니다.

지원되는 워크로드에 대한 자세한 내용은 [Workloads](/sccm/comanage/workloads)(워크로드)를 참조하세요.

공동 관리를 사용하도록 설정할 때나 나중에 준비가 될 때 워크로드를 전환할 수 있습니다. 공동 관리를 아직 사용하도록 설정하지 않았다면 먼저 그렇게 설정합니다. 자세한 내용은 [How to enable co-management](/sccm/comanage/how-to-enable)(공동 관리를 사용하도록 설정하는 방법)를 참조하세요.


공동 관리를 사용하도록 설정했으면 공동 관리 속성에서 설정을 수정합니다. 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다.  

2. 공동 관리 개체를 선택한 다음 리본에서 **속성**을 선택합니다.  

3. **워크로드** 탭으로 전환합니다. 기본적으로 모든 워크로드는 **Configuration Manager** 설정으로 설정됩니다. 워크로드를 전환하려면 해당 워크로드의 슬라이더 컨트롤을 원하는 설정으로 이동합니다.  

    ![공동관리 속성 페이지의 워크로드 탭 스크린샷](media/properties-workloads.png)

    - **Configuration Manager**: Configuration Manager가 이 워크로드를 계속 관리합니다.  

    - **파일럿 Intune**: 파일럿 컬렉션의 디바이스에서만 이 워크로드를 전환합니다. 공동 관리 속성 페이지의 **Staging**(준비) 탭에서 **파일럿 컬렉션**을 변경할 수 있습니다.  

    - **Intune**: 공동 관리에 등록된 모든 Windows 10 디바이스에서 이 워크로드를 전환합니다.  


> [!Important]  
> 워크로드를 전환하기 전에 Intune에서 해당 워크로드를 올바로 구성하고 배포해야 합니다. 워크로드가 항상 디바이스에 대한 관리 도구 중 하나에서 관리되어야 합니다.  

<!--1357377-->
Configuration Manager 버전 1806부터 공동 관리 워크로드를 전환하면 공동 관리되는 디바이스는 Microsoft Intune에서 자동으로 MDM 정책을 동기화합니다. 이 동기화는 Configuration Manager 콘솔의 클라이언트 알림에서 **컴퓨터 정책 다운로드** 작업을 시작할 때 발생합니다. 자세한 내용은 [클라이언트 알림을 사용하여 클라이언트 정책 검색 시작](/sccm/core/clients/manage/manage-clients#initiate-client-policy-retrieval-using-client-notification)을 참조합니다.


