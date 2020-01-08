---
title: 위험에 따라 액세스 제한
titleSuffix: Configuration Manager
description: 디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스를 제한합니다.
ms.date: 08/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9ae69ca94d2a196ae46631cb269189f069853d4
ms.sourcegitcommit: 7f64c5fb3e9fa3dba006af618b1f1ceaf61a99f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75520731"
---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스 관리

*적용 대상: Configuration Manager (현재 분기)*

Lookout에서 수행한 위험 평가를 기반으로 회사 리소스에 대한 모바일 디바이스의 액세스를 제어하세요. Lookout은 Microsoft Intune과 통합된 디바이스 위협 방지 솔루션입니다. 위험은 Lookout 서비스 수집하는 데이터를 기반으로 합니다. Lookout 서비스에서는 디바이스로부터 OS(운영 체제) 취약성, 설치된 악성 앱 및 악성 네트워크 프로필에 대한 데이터를 수집합니다. 

Configuration Manager 준수 정책을 통해 사용 설정되는 Lookout의 위험 평가 보고에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책은 Configuration Manager가 해당 디바이스에서 검색된 위협으로 인해 규정을 준수하지 않는 것으로 판단하는 디바이스를 허용하거나 차단합니다.

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 [기능은 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  



## <a name="how-does-it-work"></a>어떤 방식으로 작동합니까?

하이브리드 MDM 배포 및 Lookout 디바이스 위협 방지는 회사 리소스 보호에 어떻게 도움이 되나요?

Lookout의 모바일 앱(Lookout for Work)은 모바일 디바이스에서 실행됩니다. 이 앱은 사용 가능한 경우 파일 시스템, 네트워크 스택, 디바이스, 애플리케이션 사용량 현황 데이터를 캡처하고, 이 데이터를 Lookout 디바이스 위협 방지 클라우드 서비스에 전송하여 모바일 위협에 대한 종합적인 디바이스 위험을 집계합니다. 요구에 맞게 위협의 위험 수준 분류를 변경하려면 Lookout 콘솔을 사용하세요.  

이제 Configuration Manager의 준수 정책에 Lookout 디바이스 위협 위험 평가를 기반으로 하는 Lookout Mobile Threat Protection에 대한 새 규칙이 포함되어 있습니다. 이 규칙을 사용하도록 설정하면 Configuration Manager에서 디바이스가 정책을 준수하는지 평가합니다.

디바이스가 준수 정책을 준수하지 않는 경우 조건부 액세스 정책을 사용하여 Exchange Online, SharePoint Online 등의 리소스에 대한 액세스를 차단할 수 있습니다. 액세스가 차단되면 문제를 해결하고 회사 리소스에 다시 액세스하는 데 도움이 되도록 최종 사용자에게 연습이 제공됩니다. 최종 사용자는 Lookout for Work 앱을 통해 이 연습을 시작합니다.



## <a name="supported-platforms"></a>지원되는 플랫폼

- **Android 4.1 이상** 및 Microsoft Intune에 등록됨  

- **iOS 8 이상**, Microsoft Intune에 등록됨  


Lookout에서 지원하는 플랫폼 및 언어에 대한 자세한 내용은 이 [Lookout 지원 문서](https://personal.support.lookout.com/hc/articles/114094140253)를 참조하세요.



## <a name="prerequisites"></a>전제 조건

- [하이브리드 MDM](/sccm/mdm/understand/hybrid-mobile-device-management)  

- Microsoft Intune 및 Azure Active Directory에 대한 구독  

- Lookout Mobile EndPoint Security에 대한 엔터프라이즈 구독. 자세한 내용은 [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)를 참조하세요.  



## <a name="example-scenarios"></a>예제 시나리오


### <a name="control-access-based-on-threat-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어 같은 악성 앱이 디바이스에서 발견되면 해당 디바이스의 다음 작업을 차단할 수 있습니다.

- 위협을 해결하기 전에 회사 메일에 연결  

- 회사용 OneDrive 앱을 사용하여 회사 파일 동기화  

- 업무상 중요한 앱 액세스  

#### <a name="access-blocked-when-malicious-apps-are-detected"></a>악성 앱이 발견되면 액세스 차단됨

![악성 앱이 검색되면 액세스를 차단하는 조건부 액세스 정책](media/config-mgr-maliciousapps_blocked.png)

#### <a name="device-unblocked-and-is-able-to-access-company-resources-when-the-threat-is-remediated"></a>디바이스 차단이 해제되고 위협이 수정되면 회사 리소스에 액세스할 수 있음

![준수 디바이스로 확인되면 액세스 권한을 부여하는 조건부 액세스 정책](media/config-mgr-maliciousapps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

메시지 가로채기(man-in-the-middle) 공격 등의 네트워크 위협을 검색하고 디바이스 위험에 따라 WiFi 네트워크에 대한 액세스를 제한합니다.

#### <a name="access-to-network-through-wifi-blocked"></a>WiFi를 통해 네트워크 액세스 차단됨

![네트워크 위협에 따라 WiFi 액세스를 차단하는 조건부 액세스](media/config-mgr-network-wifi-blocked.png)

#### <a name="access-granted-on-remediation"></a>수정 시 액세스 권한 부여됨

![위협 수정 시 액세스를 허용하는 조건부 액세스](media/config-mgr-network-wifi-unblocked.png)


### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크 위협에 따라 SharePoint Online에 대한 액세스 제어

메시지 가로채기(man-in-the-middle) 공격 등의 네트워크 위협을 검색하고 디바이스 위험에 따라 회사 파일에 대한 동기화를 차단합니다.

#### <a name="access-blocked-sharepoint-online-based-on-network-threat-detected-on-the-device"></a>디바이스에서 검색된 네트워크 위협에 따라 액세스가 차단된 SharePoint Online

![SharePoint Online에 대한 디바이스 액세스를 차단하는 조건부 액세스](media/config-mgr-network-spo-blocked.png)


#### <a name="access-granted-on-remediation"></a>수정 시 액세스 권한 부여됨

![위협이 수정된 후 액세스를 허용하는 조건부 액세스](media/config-mgr-network-spo-unblocked.png)



## <a name="next-steps"></a>다음 단계

이 솔루션을 구현하려면 다음 단계를 사용하세요.  

1. [Lookout 모바일 위협 방지를 사용하여 구독 설정](set-up-your-subscription-with-lookout.md)
2. [Intune에서 Lookout MTP 연결 사용](enable-lookout-connection-in-intune.md)
3.  [Lookout for Work 애플리케이션 구성 및 배포](configure-and-deploy-lookout-for-work-apps.md)
4. [준수 정책 구성](enable-device-threat-protection-rule-compliance-policy.md)
5. [Lookout 통합 문제 해결](troubleshoot-lookout-integration.md)
