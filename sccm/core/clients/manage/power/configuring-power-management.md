---
title: 전원 관리 구성
titleSuffix: Configuration Manager
description: Configuration Manager에서 전원 관리를 설정합니다.
ms.date: 09/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 435c923c-ea30-4dce-8afd-48962ed85502
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f76cf68cc007a5cefb323828752186ded62ad5f
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70902901"
---
# <a name="configure-power-management-in-configuration-manager"></a>Configuration Manager에서 전원 관리 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager에서 전원 관리를 설정하는 방법을 설명합니다.

## <a name="enable-and-configure-client-settings"></a>클라이언트 설정 사용 및 구성

이 절차는 전원 관리에 관한 ‘기본 클라이언트 설정’을 구성합니다.  계층 구조의 모든 컴퓨터에 적용됩니다.

이 설정이 일부 컴퓨터에만 적용되도록 하려면 ‘사용자 지정 디바이스 클라이언트 설정’을 만듭니다.  그런 다음, 전원 관리를 위한 컴퓨터를 포함하는 컬렉션에 할당합니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **클라이언트 설정** 노드를 선택하고, **기본 클라이언트 설정**을 선택합니다.

1. 리본의 **홈** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

1. **전원 관리** 그룹을 선택합니다.  

1. **디바이스의 전원 관리 허용**에 관한 클라이언트 설정을 사용하도록 설정합니다.

1. 필요한 추가 클라이언트 설정을 구성합니다. 자세한 내용은 [클라이언트 설정 정보 - 전원 관리](/sccm/core/clients/deploy/about-client-settings#power-management)를 참조하세요.  

클라이언트는 다음번에 클라이언트 정책을 다운로드할 때 이 설정을 구성합니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [클라이언트를 관리하는 방법](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.  

## <a name="exclude-computers"></a>컴퓨터 제외

컴퓨터의 컬렉션이 전원 관리 설정을 받지 않도록 차단할 수 있습니다. 컴퓨터가 전원 관리 설정에서 제외되는 ‘임의’ 컬렉션의 멤버인 경우 해당 컴퓨터는 전원 관리 설정을 적용하지 않습니다.  이 동작은 전원 관리 설정을 적용하는 다른 컬렉션의 멤버인 경우에도 적용됩니다.  

다음과 같은 이유로 컴퓨터를 전원 관리에서 제외하려 할 수 있습니다.  

- 컴퓨터가 항상 켜져 있어야 하는 비즈니스 요구 사항이 있습니다.  

- 전원 관리 설정을 적용하지 않으려는 컴퓨터의 컨트롤 컬렉션이 있습니다.  

- 일부 컴퓨터가 전원 관리 설정을 적용할 수 없습니다.  

- Windows Server를 실행하는 컴퓨터를 전원 관리에서 제외하려고 합니다.  

> [!NOTE]  
> **사용자가 전원 관리에서 디바이스를 제외할 수 있도록 허용**에 관한 클라이언트 설정을 구성하면 사용자는 소프트웨어 센터를 사용하여 자신의 컴퓨터를 전원 관리에서 제외할 수 있습니다.  

전원 관리에서 제외된 컴퓨터를 확인하려면 **제외된 컴퓨터** 보고서를 실행합니다. 이 보고서에 관한 자세한 내용은 [전원 관리를 모니터링하고 계획하는 방법](/sccm/core/clients/manage/power/monitor-and-plan-for-power-management#BKMK_Excluded)을 참조하세요.  

> [!IMPORTANT]  
> 전원 관리에서 컴퓨터를 제외하면 모든 전원 설정이 원래 값으로 되돌아갑니다. 개별 전원 설정을 원래 값으로 되돌릴 수 없습니다.  

### <a name="how-to-exclude-a-collection-of-computers-from-power-management"></a>컴퓨터의 컬렉션을 전원 관리에서 제외하는 방법  

1. Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동하여 **디바이스 컬렉션** 노드를 선택합니다.  

1. 전원 관리에서 제외하려는 컬렉션을 선택합니다. 리본의 **홈** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

1. **전원 관리** 탭으로 전환하고 **이 컬렉션의 컴퓨터에 전원 관리 설정 적용 안 함**을 선택합니다.  

## <a name="next-steps"></a>다음 단계

[전원 계획을 만들고 적용하는 방법](/sccm/core/clients/manage/power/create-and-apply-power-plans)

[전원 관리를 모니터링하고 계획하는 방법](/sccm/core/clients/manage/power/monitor-and-plan-for-power-management)
