---
title: 클라이언트 설정 구성
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 클라이언트 설정을 선택합니다.
ms.date: 12/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dc3b4d64511e944bd7d03feca7370d1d4b5d8b6
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56135428"
---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

**관리** > **클라이언트 설정**에서 System Center Configuration Manager의 모든 클라이언트 설정을 관리합니다. 계층에서 사용자 지정 설정이 적용되지 않은 모든 사용자 및 디바이스에 대한 설정을 구성하려면 기본 설정을 수정하세요. 일부 사용자 또는 디바이스에만 다른 설정을 적용하려면 사용자 지정 설정을 만들어 컬렉션에 배포하세요.  

각 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../core/clients/deploy/about-client-settings.md)를 참조하세요.

> [!NOTE]  
>  또한 클라이언트를 관리할 구성 항목을 사용하여 디바이스의 구성 호환성을 평가, 추적 및 재구성할 수 있습니다. 자세한 내용은 [System Center Configuration Manager를 사용하여 디바이스 준수 확인](../../../compliance/understand/ensure-device-compliance.md)을 참조하세요.  

##  <a name="configure-the-default-client-settings"></a>기본 클라이언트 설정 구성    

1. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

2. **홈** 탭에서 **속성**을 선택합니다.  

3. 탐색 창에서 각 설정 그룹의 클라이언트 설정을 보고 구성합니다.  

   클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대해 정책 검색을 시작하려면 [System Center Configuration Manager의 클라이언트 관리 방법](../../../core/clients/manage/manage-clients.md)에서 [Configuration Manager 클라이언트에 대한 정책 검색 시작](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval)을 참조하세요.  

##  <a name="create-and-deploy-custom-client-settings"></a>사용자 지정 클라이언트 설정 만들기 및 배포  
이러한 사용자 지정 설정을 배포하면 기본 클라이언트 설정이 재정의됩니다. 이 절차를 시작하기 전에 이러한 사용자 지정 클라이언트 설정이 필요한 사용자 또는 디바이스가 포함된 컬렉션이 있는지 확인하세요.  

1. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**을 선택합니다.  

2. **홈** 탭의 **만들기** 그룹에서 **사용자 지정 클라이언트 설정 만들기**를 선택하고 다음 중 하나를 선택합니다.  

   -   **사용자 지정 클라이언트 디바이스 설정 만들기**  

   -   **사용자 지정 클라이언트 사용자 설정 만들기**  

3. 고유한 이름 및 설명(선택 사항)을 지정합니다.  

4. 설정 그룹을 표시하는 확인란 중 하나 이상을 선택합니다.  

5. 탐색 창에서 각 설정 그룹을 선택하고 사용 가능한 설정을 구성한 다음 **확인**을 클릭합니다.   

6. 작성한 사용자 지정 클라이언트 설정을 선택합니다. **홈** 탭의 **클라이언트 설정** 그룹에서 **배포**를 선택합니다.  

7. **컬렉션 선택** 대화 상자에서 적합한 컬렉션을 선택한 다음 **확인**을 선택합니다. 세부 정보 창에서 **배포** 탭을 클릭하면 선택한 컬렉션을 확인할 수 있습니다.  

8. 만든 사용자 지정 클라이언트 설정 순서를 봅니다. 사용자 지정 클라이언트 설정이 여러 개인 경우 해당 순서 번호에 따라 적용됩니다. 충돌이 있는 경우 순서 번호가 가장 낮은 설정이 다른 설정을 재정의합니다. 순서를 변경하려면 **홈** 탭의 **클라이언트 설정** 그룹에서 **위로 항목 이동** 또는 **아래로 항목 이동**을 선택합니다.  

   클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대해 정책 검색을 시작하려면 [System Center Configuration Manager의 클라이언트 관리 방법](../../../core/clients/manage/manage-clients.md)에서 [Configuration Manager 클라이언트에 대한 정책 검색 시작](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval)을 참조하세요.  



##  <a name="view-client-settings"></a>클라이언트 설정 보기  
 같은 디바이스, 사용자 또는 사용자 그룹에 여러 클라이언트 설정을 배포한 경우 설정의 우선 순위 및 조합이 복잡합니다. 클라이언트 설정을 보려면 다음을 수행합니다.  

1.  Configuration Manager 콘솔에서 **자산 및 호환성** > **디바이스** > **사용자** 또는 **사용자 컬렉션**을 선택합니다.  

3.  디바이스, 사용자 또는 사용자 그룹을 선택하고 **클라이언트 설정** 그룹에서 **결과 클라이언트 설정**을 선택합니다.  

4.  왼쪽 창에서 클라이언트 설정을 선택하면 설정이 표시됩니다. 이 보기에서 설정은 읽기 전용입니다. 

    > [!NOTE]  
    >  클라이언트 설정을 보려면 클라이언트 설정에 대한 읽기 액세스 권한이 있어야 합니다.  

    
