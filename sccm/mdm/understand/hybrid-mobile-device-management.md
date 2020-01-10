---
title: Microsoft Intune과 사용하는 하이브리드 MDM
titleSuffix: Configuration Manager
description: Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 디바이스 관리)에 대해 알아보세요.
ms.date: 09/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: aaa1a6e3914c590a7575562fb5e6a29e31043c16
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75826410"
---
# <a name="hybrid-mdm-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager 및 Microsoft Intune에서 사용하는 하이브리드 MDM

*적용 대상: Configuration Manager (현재 분기)*

> [!WARNING]
> 하이브리드 MDM 서비스 제품은 2019년 9월 1일부로 종료되었습니다. 나머지 하이브리드 MDM 장치는 정책, 앱 또는 보안 업데이트를 받지 않습니다.

## <a name="remove-hybrid-mdm"></a>하이브리드 MDM 제거

Configuration Manager 사이트에 Microsoft Intune 구독이 있었다면 이를 제거해야 합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **Cloud Services**를 확장하고 **Microsoft Intune 구독** 노드를 선택합니다. 기존 Intune 구독은 삭제합니다.

1. **Microsoft Intune 구독 제거 마법사**에서 **Configuration Manager에서 Microsoft Intune 구독을 제거**하는 옵션을 선택 하 고 **다음**을 클릭 합니다.

1. 마법사 완료

## <a name="deprecation-announcement"></a>사용 중단 알림

원본 사용 중단 발표는 다음과 같습니다.

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 [기능은 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 2019년 2월 말로 예정된 1902 Intune 서비스 릴리스부터, 신규 고객은 새 하이브리드 연결을 만들 수 없습니다.
> <!--Intune feature 2683117-->  
> Intune은 1년여 전 Azure에서 실행된 이후 고객들이 요청하고 업계에서 선두를 달리는 수백 개의 새로운 서비스 기능을 추가했습니다. 이제는 하이브리드 모바일 디바이스 관리(MDM)를 통해 제공하는 것 보다 훨씬 더 많은 기능을 제공합니다. Azure의 Intune에서는 기업 무선 통신 요구 사항을 충족하기 위해 보다 통합되고 간소화된 관리 환경을 제공합니다.
>
> 그 결과, 대부분의 고객은 하이브리드 MDM 통해 Azure에서 Intune을 선택합니다. 하이브리드 MDM을 사용하는 고객의 수는 더 많은 고객이 클라우드로 이동함에 따라 계속 줄어듭니다. 따라서 2019년 9월 1일, Microsoft에서는 하이브리드 MDM 서비스 제공을 중지합니다. MDM 요구 사항을 충족하려면 [Azure의 Intune으로의 마이그레이션](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 계획하세요.
>
> 이 변경이 온-프레미스 Configuration Manager나 [Windows 10 디바이스의 공동 관리](/sccm/comanage/overview)에 영향을 주지는 않습니다. 하이브리드 MDM을 사용 중인지 모르는 경우에는 Configuration Manager 콘솔의 **관리** 작업 영역으로 이동하여 **Cloud Services**를 확장하고 **Microsoft Intune 구독**을 클릭하세요. Microsoft Intune 구독이 설정되어 있다면 하이브리드 MDM용으로 테넌트가 구성되어 있는 것입니다.
>
> **이 변경 사항은 어떤 영향을 미치나요?**
>
> - Microsoft에서는 다음 해에 대한 하이브리드 MDM 사용을 지원하며, 이 기능에서는 주요 버그 수정 사항을 계속 수신합니다. Microsoft는 iOS 12의 등록과 같이, 새 OS 버전의 기존 기능을 지원하게 됩니다. 하이브리드 MDM에 대한 새로운 기능은 없습니다.  
>
> - 하이브리드 MDM 제공이 종료되기 전에 Azure의 Intune으로 마이그레이션하는 경우 최종 사용자에게는 영향이 없어야 합니다.  
>
> - 2019년 9월 1일에는 나머지 모든 하이브리드 MDM 디바이스에서 더 이상 정책, 앱 또는 보안 업데이트를 받지 않습니다.  
>
> - 라이선싱은 동일하게 유지됩니다. Azure의 Intune 라이선스는 하이브리드 MDM에 포함되어 있습니다.  
>
> - Configuration Manager의 온-프레미스 MDM 기능은 더 이상 사용 되지 않습니다. Configuration Manager 버전 1810부터 Intune 연결 없이 온-프레미스 MDM을 사용할 수 있습니다. 자세한 내용은 [Intune 연결이 새 온-프레미스 MDM 배포에 더 이상 필요 하지](/sccm/core/plan-design/changes/whats-new-in-version-1810#bkmk_opmdm)않습니다 .를 참조 하세요.
>
> - Configuration Manager의 온-프레미스 조건부 액세스 기능도 하이브리드 MDM에서 더 이상 사용 되지 않습니다. Configuration Manager 클라이언트를 사용 하 여 관리 되는 장치에서 조건부 액세스를 사용 하는 경우 마이그레이션 전에 보호 되는지 확인 합니다.
>     1. Azure에서 조건부 액세스 정책 설정
>     2. Intune 포털에서 준수 정책 설정
>     3. 하이브리드 마이그레이션 완료 및 MDM 기관을 Intune으로 설정
>     4. 공동 관리 사용
>     5. 준수 정책 공동 관리 워크 로드를 Intune으로 이동
>
>     자세한 내용은 [공동 관리를 사용 하는 조건부 액세스](https://docs.microsoft.com/sccm/comanage/quickstart-conditional-access)를 참조 하세요.
>
> **이러한 변경에 대비하려면 어떻게 해야 하나요?**
>
> - MDM을 위한 ConfigMgr 콘솔에서 Azure로의 마이그레이션 계획을 시작하세요. Microsoft IT를 비롯한 많은 고객은 이 프로세스를 통과했습니다. 자세한 내용은 이 [Microsoft 사례 연구](https://aka.ms/Intune_MSFT)를 참조하세요.  
>
> - 하이브리드 MDM에서 Azure의 Intune으로 이동하는 프로세스를 간소화하려면 다음 도구 및 설명서를 검토하세요.  
>   - [Configuration Manager 데이터를 Microsoft Intune로 가져오기](/sccm/mdm/deploy-use/migrate-import-data)  
>   - [하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)  
>
> - 도움이 필요하면 공식 파트너나 FastTrack에 문의하세요. [Microsoft 365용 FastTrack](https://aka.ms/hybrid_fasttrack)이 하이브리드 MDM에서 Azure의 Intune으로의 마이그레이션을 지원할 수 있습니다.
>
> 자세한 내용은 [Intune 지원 블로그 게시물](https://aka.ms/hybrid_notification)을 참조하세요.

<!--

With the hybrid mobile device management (MDM) feature of Configuration Manager, manage iOS, Windows, and Android devices. All management tasks are handled from the Configuration Manager console where you perform the rest of your management tasks seamlessly integrated with Microsoft Intune's online service over the internet. Use Configuration Manager to let users access company resources on their devices in a secure, managed way. By using device management, you protect company data while letting users enroll their personal or company-owned devices to access company data. 

This article assumes that you use Configuration Manager to manage computers. It also assumes that you're interested in extending the Configuration Manager console with Intune to manage mobile devices. 



## Capabilities

Hybrid MDM supports the following management capabilities on devices:

-   Retire and wipe devices  

-   Configure compliance settings such as passwords, security, roaming, encryption, and wireless communication  

-   Deploy line-of-business (LOB) apps to devices  

-   Deploy apps to devices that connect to Windows Store, Windows Phone Store, App Store, or Google Play  

-   Collect hardware inventory  

-   Collect software inventory by using built-in reports  



## Hybrid MDM enrollment

To bring devices into hybrid management, those devices must be enrolled with the service. How devices enroll devices depends on the device type, ownership, and the level of management needed.

- **"Bring your own device" (BYOD)**: Users enroll their personal phones, tablets, or PCs  

- **Corporate-owned device (COD)**: Enable management scenarios like remote wipe, shared devices, or user affinity for a device  

- If you use [Exchange ActiveSync](/sccm/mdm/plan-design/device-enrollment-methods#mobile-device-management-with-exchange-activesync-and-configuration-manager), either on-premises or hosted in the cloud, you can enable simple Intune management without enrollment. Windows PCs can also be managed using [Intune client software](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).

-->

## <a name="next-steps"></a>다음 단계

MDM 장치를 관리 하는 데 지원 되는 기능에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Microsoft Intune 이란?](https://docs.microsoft.com/intune/what-is-intune)
- [온-프레미스 MDM 이란?](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)
- [Exchange를 사용한 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)
