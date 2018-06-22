---
title: 장치 준수 정책
titleSuffix: Configuration Manager
description: 장치가 조건부 액세스 정책을 준수하도록 System Center Configuration Manager에서 준수 정책을 관리하는 방법을 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 776af7499c576f21d47dafec8a668f3c4051ad88
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347266"
---
# <a name="device-compliance-policies-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 장치 준수 정책 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 **준수 정책**은 장치가 조건부 액세스 정책을 준수하는 것으로 간주되기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 장치를 모니터링하고 준수 문제를 수정할 수도 있습니다.  


> [!IMPORTANT]  
>  이 문서에서는 Microsoft Intune으로 관리되는 장치에 대한 규정 준수 정책을 설명합니다.    System Center Configuration Manager로 관리되는 PC에 대한 규정 준수 정책은 [System Center Configuration Manager에서 관리되는 PC용 O365 서비스에 대한 액세스 관리](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)에 설명되어 있습니다.  

 이러한 규칙에는 다음과 같은 요구 사항이 있습니다.  

-   장치에 액세스할 PIN 및 암호

-   장치에 저장된 데이터 암호화

-   장치의 무단 해제 또는 루팅 여부  

-   장치의 메일이 Intune 정책으로 관리되는지 여부 또는 장치가 Windows 장치 상태 증명 서비스에서 비정상으로 보고되는지 여부
-   장치에 설치할 수 없는 앱


 준수 정책은 사용자 컬렉션에 배포합니다. 규정 준수 정책을 사용자에게 배포하면 모든 사용자 장치의 규정 준수가 확인됩니다.  

 다음 테이블은 정책을 조건부 액세스 정책과 함께 사용하는 경우 규정 준수 정책에서 지원하는 장치 유형 및 규정에 위반된 설정을 관리하는 방법을 나열합니다.  

|규칙|Windows 8.1 이상|Windows Phone 8.1 이상|iOS 6.0 이상|Android 4.0 이상, Samsung KNOX Standard 4.0 이상, Android for Work|  
|----------|---------------------------|---------------------------------|-----------------------|---------------------------|-----------------------------------------|  
|**PIN 또는 암호 구성**|재구성됨|재구성됨|재구성됨|격리됨|  
|**장치 암호화**|해당 없음|재구성됨|재구성됨(PIN 설정)|격리됨<br>(Android for Work 항상 암호화됨)|  
|**무단 해제 또는 루팅된 장치**|해당 없음|해당 없음|격리됨(설정 아님)|격리됨(설정 아님)|  
|**전자 메일 프로필**|해당 없음|해당 없음|격리됨|해당 없음|  
|**최소 OS 버전**|격리됨|격리됨|격리됨|격리됨|  
|**최대 OS 버전**|격리됨|격리됨|격리됨|격리됨|  
|**장치 상태 증명(1602 업데이트)**|설정은 Windows 8.1에 적용되지 않습니다.<br /><br /> Windows 10 및 Windows 10 Mobile이 격리됩니다.|해당 없음|해당 없음|해당 없음|  
|**설치할 수 없는 앱**|해당 없음|해당 없음|격리됨|격리됨|

 **재구성됨** = 장치 운영 체제에서 준수를 적용하도록 요구합니다. 예를 들어, 사용자는 직접 PIN을 설정해야 합니다.  설정이 비규격인 경우는 없습니다.  

 **격리됨** = 장치 운영 체제에서 준수를 적용하도록 요구하지 않습니다. 예를 들어, Android 장치에서 사용자에게 장치를 암호화하도록 강제하지 않습니다.  이 경우:  

-   사용자가 조건부 액세스 정책의 대상인 장치가 차단됩니다.  

-   회사 포털 또는 웹 포털은 모든 규정 준수 문제에 대해 사용자에게 알립니다.  


### <a name="next-steps"></a>다음 단계  
[장치 준수 정책 만들기 및 배포](create-compliance-policy.md)
### <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager에서 서비스 액세스 관리](../../protect/deploy-use/manage-access-to-services.md)
