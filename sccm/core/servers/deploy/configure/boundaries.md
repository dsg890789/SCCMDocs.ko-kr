---
title: 경계 정의
titleSuffix: Configuration Manager
description: 관리할 디바이스를 포함할 수 있는 인트라넷의 네트워크 위치를 정의하는 방법을 이해합니다.
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4a9dc4d9-e114-42ec-ae2b-73bee14ab04f
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7218f467df72d9ea9d9ae7b3e4bb15be3c74bda2
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68338182"
---
# <a name="define-network-locations-as-boundaries-for-system-center-configuration-manager"></a>네트워크 위치를 System Center Configuration Manager의 경계로 정의합니다.

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 경계는 관리할 디바이스가 포함된 네트워크의 위치입니다. 디바이스가 있는 경계는 디바이스에 설치된 Configuration Manager 클라이언트가 식별하는 네트워크 IP 주소 또는 Active Directory 사이트와 같습니다.
- 개별 경계를 수동으로 만들 수 있습니다. 하지만 Configuration Manager에서는 슈퍼넷을 경계로 직접 입력할 수 없습니다. 대신, IP 주소 범위 경계 유형을 사용합니다.
- [Active Directory 포리스트 검색](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutForest) 방법에서 검색하는 각 IP 서브넷 및 Active Directory 사이트에 대해 경계를 자동으로 검색하고 만들도록 구성할 수 있습니다. Active Directory 포리스트 검색에서 Active Directory 사이트에 할당된 슈퍼넷을 식별할 때 Configuration Manager가 슈퍼넷을 IP 주소 범위 경계로 변환합니다.  

Configuration Manager 관리자가 알지 못하는 IP 주소를 사용하는 디바이스도 드물지 않습니다. 디바이스의 네트워크 위치가 확실하지 않으면 디바이스에서 **IPCONFIG** 명령을 사용하여 디바이스가 위치로 보고하는 항목을 확인합니다.  

작성하는 경계는 경계 범위와 유형을 기준으로 하는 이름을 자동으로 수신합니다. 이 이름은 수정할 수 없습니다. 대신에 Configuration Manager 콘솔에서 경계를 식별하는 데 도움이 되는 설명을 지정할 수 있습니다.  

각 경계는 계층 구조의 모든 사이트에서 사용할 수 있습니다. 경계를 만든 후에는 해당 속성을 수정하여 다음 작업을 수행할 수 있습니다.  
- 하나 이상의 경계 그룹에 경계를 추가합니다.  
- 경계의 유형 또는 범위를 변경합니다.  
- 경계 **사이트 시스템** 탭에서 경계와 연결된 사이트 시스템 서버(배포 지점, 상태 마이그레이션 지점 및 관리 지점)를 확인합니다.  

## <a name="to-create-a-boundary"></a>경계를 만들려면  

1.  Configuration Manager 콘솔에서 **관리** > **계층 구조 구성** > **경계**를 클릭합니다.  

2.  **홈** 탭의 **만들기** 그룹에서 **만들기 Boundary.** 를 클릭합니다.  

3.  경계 만들기 대화 상자의 **일반** 탭에서 이름 또는 참조로 경계를 식별할 수 있도록 **설명** 을 지정할 수 있습니다.  

4.  이 경계의 **유형** 을 선택합니다.  

    - **IP 서브넷**을 선택한 경우 이 경계의 **서브넷 ID** 를 지정해야 합니다.  
      > [!TIP]  
      > **서브넷 ID** 를 자동으로 지정할 **네트워크** 및 **서브넷 마스크** 를 지정할 수 있습니다. 경계를 저장하면 서브넷 ID 값만 저장됩니다.  

    - **Active Directory 사이트**를 선택한 경우 사이트 서버의 로컬 포리스트에 있는 Active Directory 사이트를 지정하거나 **찾아보기** 로 선택해야 합니다.  
        
      - 경계에 대해 Active Directory 사이트를 지정하면 경계에 해당 Active Directory 사이트의 구성원인 각 IP 서브넷이 포함됩니다. Active Directory에서 Active Directory 사이트의 구성이 변경되면 이 경계에 포함된 네트워크 위치도 변경됩니다.  

      - Active Directory 사이트 경계는 순수 AzureAD 클라이언트에 대해 작동하지 않습니다. 온-프레미스에서 로밍하는 클라이언트는 오직 AD 사이트를 사용하여 정의된 경우 어느 경계에도 속하지 않게 됩니다.

    - **IPv6 접두사**를 선택하는 경우 IPv6 접두사 형식의 **접두사** 를 지정해야 합니다.  

    - **IP 주소 범위**를 선택하는 경우 IP 서브넷의 일부가 포함되거나 여러 IP 서브넷이 포함된 **시작 IP 주소** 와 **끝 IP 주소** 를 지정해야 합니다.    

5.  **확인** 을 클릭하여 새 경계를 저장합니다.  

## <a name="to-configure-a-boundary"></a>경계를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **계층 구조 구성** > **경계**를 클릭합니다.  

2.  수정할 경계를 선택합니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

4.  경계의 **속성** 대화 상자에서 **일반** 탭을 선택하여 경계의 **설명** 또는 **유형** 을 선택합니다. 경계의 네트워크 위치를 편집하여 경계의 범위를 변경할 수도 있습니다. 예를 들어 Active Directory 사이트 경계의 경우 새 Active Directory 사이트 이름을 지정하면 됩니다.  

5.  **사이트 시스템** 탭을 선택하여 이 경계에 연결된 사이트 시스템을 봅니다. 경계의 속성에서는 이 구성을 변경할 수 없습니다.  

    > [!TIP]  
    > 사이트 시스템 서버는 경계를 포함하는 경계 그룹 하나 이상에 대해 사이트 시스템 서버로 연결되어 있어야 해당 경계의 사이트 시스템으로 나열됩니다. 경계 그룹의 **참조** 탭에서 이러한 연결을 구성합니다.  

6.  **경계 그룹** 탭을 선택하여 이 경계의 경계 그룹 멤버 자격을 수정합니다.  

    - 이 경계를 하나 이상의 경계 그룹에 추가하려면 **추가**를 클릭하고 경계 그룹 하나 이상의 확인란을 선택한 다음 **확인**을 클릭합니다.  

    - 경계 그룹에서 이 경계를 제거하려면 경계 그룹을 선택하고 **제거**를 클릭합니다.  

7.  **확인** 을 클릭하여 경계 속성을 닫고 구성을 저장합니다.  
