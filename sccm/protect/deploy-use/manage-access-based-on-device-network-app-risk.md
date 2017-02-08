---
title: "위험에 따라 액세스 제한 | System Center Configuration Manager"
description: "장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스를 제한합니다."
ms.custom: na
ms.date: 11/18/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: c13c6268fa76ade7feb0981f9c4a6e325e393aca
ms.openlocfilehash: 70ceac5d4ec88197ec8a08103a08d4218fac6136


---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune과 통합된 장치 위협 방지 솔루션인 Lookout에서 수행한 위험 평가에 따라 회사 리소스에 대한 모바일 장치의 액세스를 제어할 수 있습니다. 위험은 Lookout 서비스가 OS(운영 체제) 취약성, 설치된 악성 앱 및 악성 네트워크 프로필에 대해 장치에서 수집하는 원격 분석을 기반으로 합니다. 

SCCM(System Center Configuration Manager) 준수 정책을 통해 사용하도록 설정된, Lookout에서 보고된 위험 평가에 따라 조건부 액세스 정책을 구성하고 해당 장치에서 검색된 위협으로 인해 비규격으로 확인된 장치를 허용하거나 차단할 수 있습니다.  

## <a name="what-problem-does-this-solve"></a>이 기능을 통해 어떤 문제가 해결되나요?
회사와 조직은 OS 취약성뿐만 아니라 물리적, 앱 기반 및 네트워크 기반 위협을 포함하는 새로운 위협으로부터 중요한 데이터를 보호해야 합니다.

지금까지 회사와 조직은 악의적인 공격으로부터 PC를 적극적으로 보호해 왔습니다. 모바일은 새로운 분야로, 보호되지 않는 경우가 많습니다. 모바일 플랫폼에 앱 격리 및 점검된 소비자 앱 스토어와 같은 기술을 사용하는 기본 제공 OS 보호가 있는 경우에도 해당 플랫폼은 복잡한 공격에 계속 취약합니다. 직원들이 업무를 수행하고 중요할 수 있는 정보에 액세스하는 데 모바일 장치를 사용하는 경우가 증가함에 따라 이러한 장치를 다양한 복잡한 공격으로부터 보호해야 합니다.

[하이브리드 MDM 배포(SCCM 및 Intune)](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)는 Lookout 등의 장치 위협 방지 솔루션에서 제공하는 위험 평가에 따라 회사 리소스 및 데이터에 대한 액세스를 제어하는 기능을 제공합니다.

## <a name="how-do-the-hybrid-mdm-deployment-and-lookout-device-threat-protection-help-protect-company-resources"></a>하이브리드 MDM 배포 및 Lookout 장치 위협 방지는 회사 리소스 보호에 어떻게 도움이 되나요?
모바일 장치에서 실행되는 Lookout 모바일 앱(Lookout for Work)은 파일 시스템, 네트워크 스택, 장치 및 응용 프로그램 원격 분석(사용 가능한 경우)을 캡처하고 Lookout 장치 위협 방지 클라우드 서비스에 보내 모바일 위협에 대한 집계 장치 위험을 계산합니다. 요구에 맞게 Lookout 콘솔에서 위협의 위험 수준 분류를 변경할 수도 있습니다.  

이제 SCCM의 준수 정책에 Lookout 장치 위협 위험 평가를 기반으로 하는 Lookout 모바일 위협 방지에 대한 새 규칙이 포함되어 있습니다. 이 규칙이 사용되는 경우 장치의 준수가 평가됩니다.

장치가 준수 정책에서 비규격으로 확인될 경우 조건부 액세스 정책을 사용하여 Exchange Online, SharePoint Online 등의 리소스에 대한 액세스를 차단할 수 있습니다. 액세스가 차단되면 문제를 해결하고 회사 리소스에 다시 액세스할 수 있도록 최종 사용자에게 연습이 제공됩니다. 이 연습은 Lookout for Work 앱을 통해 시작됩니다.

## <a name="supported-platforms"></a>지원되는 플랫폼:
* **Android 4.1 이상** 및 Microsoft Intune에 등록됨
* **iOS 8 이상**, Microsoft Intune에 등록됨
Lookout에서 지원하는 플랫폼 및 언어에 대한 자세한 내용은 이 [문서](https://personal.support.lookout.com/hc/en-us/articles/114094140253)를 참조하세요.

## <a name="prerequisites"></a>필수 조건:
* [하이브리드 MDM 배포](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)
* Microsoft Intune 및 Azure Active Directory에 대한 구독
* Lookout Mobile EndPoint Security에 대한 엔터프라이즈 구독  자세한 내용은 [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)를 참조하세요.

## <a name="example-scenarios"></a>예제 시나리오
다음은 몇 가지 일반적인 시나리오입니다.
### <a name="control-access-based-on-threat-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스를 제어합니다.
맬웨어 같은 악성 앱이 장치에서 발견되면 해당 장치의 다음 작업을 차단할 수 있습니다.
* 위협을 해결하기 전에 회사 메일에 연결
* 회사용 OneDrive 앱을 사용하여 회사 파일 동기화
* 업무상 중요한 앱 액세스

**악성 앱이 발견되면 액세스 차단됨:**

![장치의 악성 앱으로 인해 장치가 비규격으로 확인되면 액세스를 차단하는 조건부 액세스 정책을 보여 주는 다이어그램](../media/config-mgr-maliciousapps_blocked.png)

**장치 차단이 해제되고 위협이 수정되면 회사 리소스에 액세스할 수 있음:**

![수정 후 장치가 규격으로 확인되면 액세스 권한을 부여하는 조건부 액세스 정책을 보여 주는 다이어그램](../media/config-mgr-maliciousapps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어:
메시지 가로채기(man-in-the-middle) 공격 등의 네트워크 위협을 검색하고 장치 위험에 따라 WiFi 네트워크에 대한 액세스를 제한합니다.

**WiFi를 통해 네트워크 액세스 차단됨:**

![네트워크 위협에 따라 WiFi 액세스를 차단하는 조건부 액세스를 보여 주는 다이어그램](../media/config-mgr-network-wifi-blocked.png)

**수정 시 액세스 권한 부여됨:**

![위협 수정 시 액세스를 허용하는 조건부 액세스를 보여 주는 다이어그램](../media/config-mgr-network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크 위협에 따라 SharePoint Online에 대한 액세스 제어:

메시지 가로채기(man-in-the-middle) 공격 등의 네트워크 위협을 검색하고 장치 위험에 따라 회사 파일에 대한 동기화를 차단합니다.

**장치에서 검색된 네트워크 위협에 따라 액세스가 차단된 SharePoint Online:**

![위협 검색에 따라 SharePoint Online에 대한 장치 액세스를 차단하는 조건부 액세스를 보여 주는 다이어그램](../media/config-mgr-network-spo-blocked.png)


**수정 시 액세스 권한 부여됨:**

![네트워크 위협이 수정된 후 액세스를 허용하는 조건부 액세스를 보여 주는 다이어그램](../media/config-mgr-network-spo-unblocked.png)

## <a name="next-steps"></a>다음 단계
이 솔루션을 구현하기 위해 수행해야 하는 주요 단계는 다음과 같습니다.
1.    [Lookout 모바일 위협 방지를 사용하여 구독 설정](set-up-your-subscription-with-lookout.md)
2.    [Intune에서 Lookout MTP 연결 사용](enable-lookout-connection-in-intune.md)
3.  [Lookout for Work 응용 프로그램 구성 및 배포](configure-and-deploy-lookout-for-work-apps.md)
4.    [준수 정책 구성](enable-device-threat-protection-rule-compliance-policy.md)
5.    [Lookout 통합 문제 해결](troubleshoot-lookout-integration.md)



<!--HONumber=Dec16_HO3-->


