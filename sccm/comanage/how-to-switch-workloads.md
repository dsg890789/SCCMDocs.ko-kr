---
title: 공동 관리 워크 로드 전환
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
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755438"
---
# <a name="how-to-switch-configuration-manager-workloads-to-intune"></a>Configuration Manager 워크 로드를 Intune로 전환 하는 방법

Microsoft Intune로 Configuration Manager에서 워크 로드 전환은 공동 관리의 이점 중 하나입니다. Windows 10 장치에 Configuration Manager 클라이언트를 Intune에 등록 되는 경우 두 서비스의 이점을 얻게 됩니다. 있는 경우 기관을 Configuration Manager에서 Intune로 전환 하는 워크 로드를 제어 합니다. Configuration Manager가 계속 모든 다른 워크 로드를 Intune로 전환 하지 않습니다 하 고 다른 모든 기능은 Configuration Manager 공동 관리를 지원 하지 않습니다는 해당 워크 로드를 포함 하 여 관리.

지원 되는 워크 로드에 대 한 자세한 내용은 참조 하세요. [워크 로드](/sccm/comanage/workloads)합니다.

공동 관리 또는 뒷부분에 나오는 경우를 사용 하도록 설정 하면 워크 로드를 전환할 수 있습니다 준비가 되었습니다. 공동 관리를 아직 사용 하지 않은 경우 작업을 먼저 수행 합니다. 자세한 내용은 [공동 관리를 사용 하도록 설정 하는 방법을](/sccm/comanage/how-to-enable)합니다.


공동 관리를 활성화 하면 공동 관리 속성에서 설정을 수정 합니다. 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다.  

2. 공동 관리 개체를 선택 하 고 선택한 **속성** 리본 메뉴에 있습니다.  

3. 으로 전환 합니다 **워크 로드** 탭 합니다. 기본적으로 모든 워크 로드 설정 합니다 **Configuration Manager** 설정 합니다. 워크 로드를 전환 하려면를 원하는 설정 작업에 대 한 슬라이더 컨트롤을 이동 합니다.  

    ![공동 관리 속성 페이지의 스크린 샷의 워크 로드 탭](media/properties-workloads.png)

    - **Configuration Manager**: Configuration Manager는이 워크 로드 관리를 계속 합니다.  

    - **Intune 파일럿**: 파일럿 컬렉션의 장치에 대해서만이 워크 로드를 전환 합니다. 변경할 수 있습니다 합니다 **파일럿 컬렉션** 에 **스테이징** 공동 관리 속성 페이지의 탭 합니다.  

    - **Intune**: 공동 관리에 등록 된 모든 Windows 10 장치에 대 한이 워크 로드를 전환 합니다.  


> [!Important]  
> 워크 로드를 전환 하기 전에 제대로 구성 하 고 Intune에서 해당 워크 로드를 배포에 있는지 확인 합니다. 워크로드가 항상 디바이스에 대한 관리 도구 중 하나에서 관리되어야 합니다.  

<!--1357377--> Configuration Manager 버전 1806부터 공동 관리 워크로드를 전환하면 공동 관리되는 디바이스는 Microsoft Intune에서 자동으로 MDM 정책을 동기화합니다. 이 동기화는 Configuration Manager 콘솔의 클라이언트 알림에서 **컴퓨터 정책 다운로드** 작업을 시작할 때 발생합니다. 자세한 내용은 [클라이언트 알림을 사용하여 클라이언트 정책 검색 시작](/sccm/core/clients/manage/manage-clients#initiate-client-policy-retrieval-using-client-notification)을 참조합니다.


