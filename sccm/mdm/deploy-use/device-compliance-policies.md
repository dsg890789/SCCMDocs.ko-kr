---
title: 디바이스 준수 정책
titleSuffix: Configuration Manager
description: 디바이스가 조건부 액세스 정책을 준수하도록 Configuration Manager에서 준수 정책을 관리하는 방법을 알아봅니다.
ms.date: 03/19/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e225b7ab54a1061387d1c8ee369641f68bd7889
ms.sourcegitcommit: f38ef9afb0c608c0153230ff819e5f5e0fb1520c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58196877"
---
# <a name="device-compliance-policies-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 디바이스 준수 정책 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 준수 정책은 디바이스가 조건부 액세스 정책을 준수하는 것으로 간주되기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 디바이스를 모니터링하고 준수 문제를 수정할 수도 있습니다.  


> [!IMPORTANT]  
>  이 문서에서는 Microsoft Intune으로 관리되는 디바이스에 대한 규정 준수 정책을 설명합니다. Configuration Manager 클라이언트에서 관리 되는 장치에 대 한 준수 정책에 설명 되어 [Configuration Manager에서 관리 하는 장치에 대 한 Office 365 서비스에 대 한 액세스 관리](/sccm/protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)합니다.  

 이러한 규칙에는 다음과 같은 요구 사항이 있습니다.  

-   디바이스에 액세스할 PIN 및 암호  

-   디바이스에 저장된 데이터 암호화  

-   디바이스의 무단 해제 또는 루팅 여부  

-   디바이스의 메일이 Intune 정책으로 관리되는지 여부 또는 디바이스가 Windows 디바이스 상태 증명 서비스에서 비정상으로 보고되는지 여부  

-   디바이스에 설치할 수 없는 앱.  


 준수 정책은 사용자 컬렉션에 배포합니다. 규정 준수 정책을 사용자에게 배포하면 모든 사용자 디바이스의 규정 준수가 확인됩니다.  



## <a name="supported-device-types"></a>지원되는 디바이스 유형

 다음 테이블은 정책을 조건부 액세스 정책과 함께 사용하는 경우 준수 정책에서 지원하는 디바이스 유형 및 준수에 위반된 설정을 관리하는 방법을 나열합니다.  

|규칙|Windows 8.1 이상|Windows Phone 8.1 이상|iOS 6.0 이상|Android 4.0 이상, Samsung KNOX Standard 4.0 이상, Android for Work|  
|----------|---------------------------|---------------------------------|-----------------------|---------------------------|-----------------------------------------|  
|**PIN 또는 암호 구성**|재구성됨|재구성됨|재구성됨|격리됨|  
|**디바이스 암호화**|해당 없음|재구성됨|재구성됨(PIN 설정)|격리됨<br>(Android for Work 항상 암호화됨)|  
|**무단 해제 또는 루팅된 디바이스**|해당 없음|해당 없음|격리됨(설정 아님)|격리됨(설정 아님)|  
|**전자 메일 프로필**|해당 없음|해당 없음|격리됨|해당 없음|  
|**최소 OS 버전**|격리됨|격리됨|격리됨|격리됨|  
|**최대 OS 버전**|격리됨|격리됨|격리됨|격리됨|  
|**디바이스 상태 증명(1602 업데이트)**|설정은 Windows 8.1에 적용되지 않음<br /><br /> Windows 10 및 Windows 10 Mobile이 격리됩니다.|해당 없음|해당 사항 없음|해당 없음|  
|**설치할 수 없는 앱**|해당 없음|해당 없음|격리됨|격리됨|

 **재구성** = 장치 OS에서 준수를 적용합니다. 예를 들어 사용자에게 PIN을 설정하도록 강제합니다. 설정이 비준수인 경우는 없습니다.  

 **격리** = 디바이스 OS는 준수를 강제 적용하지 않습니다. 예를 들어, Android 디바이스는 사용자에게 디바이스를 암호화하도록 강제하지 않습니다. 이 경우:  

-   사용자가 조건부 액세스 정책의 대상인 경우 디바이스가 차단됩니다.  

-   회사 포털 또는 웹 포털은 모든 준수 문제에 대해 사용자에게 알립니다.  



## <a name="devices-without-any-assigned-compliance-policy"></a>모든 할당된 준수 정책이 없는 디바이스
<!--2520152-->
2018 년 7 월부터, 할당 된 준수 정책이 없는 모든 장치 준수 또는 비준수 것으로 간주 하는지 여부를 구성 합니다. 기본적으로 할당된 준수 정책이 없는 디바이스는 준수로 간주됩니다. 다음 단계에 따라 Azure Portal에서 이 설정을 변경합니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에 로그인합니다.  

2. **디바이스 준수**를 선택한 다음, 설정 그룹에서 **준수 정책 설정**을 선택합니다.  

3. **할당된 준수 정책이 없는 디바이스를 표시**하도록 설정하려면, 다음 옵션 중 하나를 선택합니다.  

     - **준수**(기본값) - 할당된 준수 정책이 없는 디바이스는 정책을 준수하는 것으로 간주됩니다. 조건부 액세스가 활성화된 경우 이러한 디바이스는 내부 리소스에 액세스할 수 있습니다.  

     - **비준수** - 할당된 준수 정책이 없는 디바이스는 정책을 준수하지 않는 것으로 간주됩니다. 조건부 액세스가 활성화된 경우 이러한 디바이스는 조건부 액세스 정책의 조건에 따라 내부 리소스에서 차단됩니다.  

4. 저장을 클릭합니다.  

각 플랫폼에 대해 하나 이상의 준수 정책을 사용자 환경의 모든 사용자에게 배포하는 것이 좋습니다. 그런 다음, 내부 리소스의 보안을 위해 이 설정을 **비준수**로 구성합니다. 자세한 내용은 참조는 [Intune 서비스의 보안 강화 기능](https://aka.ms/compliance_policies) 블로그 게시물을 참조하세요.



## <a name="next-steps"></a>다음 단계  
[디바이스 준수 정책 만들기 및 배포](/sccm/mdm/deploy-use/create-compliance-policy)

### <a name="see-also"></a>참고 항목  
 [Configuration Manager에서 서비스에 대한 액세스 관리](/sccm/protect/deploy-use/manage-access-to-services)
