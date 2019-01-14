---
title: Microsoft Intune과 사용하는 하이브리드 MDM
titleSuffix: Configuration Manager
description: Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 디바이스 관리)에 대해 알아보세요.
ms.date: 11/02/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a84dfc33fe79f5eb4d5397505a12052b8e92aebf
ms.sourcegitcommit: a3cec96a771eed69e58a29917d1a3fe1a5fb2e73
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54250615"
---
# <a name="hybrid-mdm-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager 및 Microsoft Intune에서 사용하는 하이브리드 MDM

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 [기능은 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).
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
> - 라이선싱은 동일하게 유지됩니다. Azure의 Intune 라이선스는 하이브리드 MDM에 포함되어 있습니다.  
> 
> - Configuration Manager의 조건부 액세스 및 온-프레미스 MDM 기능은 더 이상 사용되지 않습니다. 예정된 Configuration Manager의 변경 내용을 통해 하이브리드 MDM 없이도 이러한 기능이 작동될 수 있습니다. 
> 
> - 2019년 9월 1일에는 나머지 모든 하이브리드 MDM 디바이스에서 더 이상 정책, 앱 또는 보안 업데이트를 받지 않습니다.  
> 
> **이러한 변경에 대비하려면 어떻게 해야 하나요?**
> 
> - MDM을 위한 ConfigMgr 콘솔에서 Azure로의 마이그레이션 계획을 시작하세요. Microsoft IT를 비롯한 많은 고객은 이 프로세스를 통과했습니다. 자세한 내용은 이 [Microsoft 사례 연구](https://aka.ms/Intune_MSFT)를 참조하세요.  
> 
> - 하이브리드 MDM에서 Azure의 Intune으로 이동하는 프로세스를 간소화하려면 다음 도구 및 설명서를 검토하세요.  
>     - [Configuration Manager 데이터를 Microsoft Intune로 가져오기](/sccm/mdm/deploy-use/migrate-import-data)  
>     - [하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)  
> 
> - 도움이 필요하면 공식 파트너나 FastTrack에 문의하세요. [Microsoft 365용 FastTrack](https://aka.ms/hybrid_fasttrack)이 하이브리드 MDM에서 Azure의 Intune으로의 마이그레이션을 지원할 수 있습니다. 
> 
> 자세한 내용은 [Intune 지원 블로그 게시물](https://aka.ms/hybrid_notification)을 참조하세요.



Configuration Manager의 하이브리드 MDM(모바일 디바이스 관리) 기능을 사용하여 iOS, Windows 및 Android 디바이스를 관리하세요. 모든 관리 작업은 Configuration Manager 콘솔에서 처리되며, 나머지 관리 작업은 인터넷을 통해 Microsoft Intune 온라인 서비스와 원활하게 통합되어 수행됩니다. Configuration Manager를 사용하여 사용자가 관리되는 안전한 방식으로 디바이스에서 회사 리소스에 액세스하도록 하세요. 디바이스 관리를 사용하면 사용자가 개인 또는 회사 소유의 디바이스를 등록하여 회사 데이터에 액세스할 수 있도록 허용하는 동시에 회사 데이터를 보호할 수 있습니다. 

이 문서에서는 Configuration Manager를 사용하여 컴퓨터를 관리하며 Intune에서 Configuration Manager 콘솔을 확장하여 모바일 디바이스를 관리하는 데 관심이 있다고 가정합니다. 



## <a name="capabilities"></a>기능

하이브리드 MDM은 디바이스에서 다음과 같은 관리 기능이 제공합니다.

-   디바이스 사용 중지 및 초기화  

-   암호, 보안, 로밍, 암호화 및 무선 통신과 같은 준수 설정 구성  

-   디바이스에 LOB(기간 업무) 앱 배포  

-   Windows 스토어, Windows Phone 스토어, 앱 스토어 또는 Google Play에 연결하는 디바이스에 앱 배포  

-   하드웨어 인벤토리 수집  

-   기본 제공 보고서를 사용하여 소프트웨어 인벤토리 수집  

하이브리드 MDM에 사용할 수 있는 새로운 기능에 대한 자세한 내용은 [하이브리드 모바일 디바이스 관리의 새로운 기능](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)을 참조하세요.



## <a name="hybrid-mdm-enrollment"></a>하이브리드 MDM 등록

디바이스에 하이브리드 관리를 사용하려면 해당 디바이스를 서비스에 등록해야 합니다. 디바이스를 등록하는 방법은 디바이스 유형, 소유권 및 필요한 관리 수준에 따라 다릅니다.

- **Bring your own device (BYOD)**: 사용자가 개인 휴대폰, 태블릿 또는 Pc를 등록합니다.  

- **회사 소유 장치 (COD)**: 원격 초기화, 공유 장치 또는 장치에 대 한 사용자 선호도 같은 관리 시나리오를 사용 하도록 설정  

- [Exchange ActiveSync](/sccm/mdm/plan-design/device-enrollment-methods#mobile-device-management-with-exchange-activesync-and-configuration-manager)를 클라우드에서 호스트하거나 온-프레미스로 사용하는 경우 등록하지 않고 간단한 Intune 관리를 사용할 수 있습니다. [Intune 클라이언트 소프트웨어](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)를 사용하여 Windows PC를 관리할 수도 있습니다.
