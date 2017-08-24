---
title: "하이브리드 MDM(모바일 장치 관리) - Configuration Manager 및 Microsoft Intune | Microsoft 문서"
description: "System Center Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 장치 관리)에 대해 알아보세요."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
caps.latest.revision: "34"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: e54478a03807c939ffa64ff39a21ef6f9ea4ae2d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune

*적용 대상: System Center Configuration Manager(현재 분기)*


Configuration Manager 및 Microsoft Intune을 사용하여 iOS, Windows 및 Android 장치를 관리할 수 있습니다. 모든 관리 작업은 Configuration Manager 콘솔에서 처리되며, 나머지 관리 작업은 인터넷을 통해 Microsoft Intune 온라인 서비스와 원활하게 통합되어 수행됩니다.  Configuration Manager를 사용하여 사용자가 관리되는 안전한 방식으로 장치에서 회사 리소스에 액세스하도록 할 수 있습니다. 장치 관리를 사용하면 사용자가 개인 또는 회사 소유의 장치를 등록하여 회사 데이터에 액세스할 수 있도록 허용하는 동시에 회사 데이터를 보호할 수 있습니다. 장치의 관리 기능:

-   장치 사용 중지 및 초기화
-   암호, 보안, 로밍, 암호화 및 무선 통신과 같은 준수 설정 구성
-   장치에 LOB(기간 업무) 앱 배포
-   Windows 스토어, Windows Phone 스토어, 앱 스토어 또는 Google Play에 연결하는 장치에 앱 배포
-   하드웨어 인벤토리 수집
-   기본 제공 보고서를 사용하여 소프트웨어 인벤토리 수집

하이브리드 MDM에 사용할 수 있는 새로운 기능에 대한 자세한 내용은 [하이브리드 모바일 장치 관리의 새로운 기능](../understand/whats-new-in-hybrid-mobile-device-management.md)을 참조하세요.

이 문서에서는 Configuration Manager를 사용하여 컴퓨터를 관리하고 있으며 Intune으로 Configuration Manager 콘솔을 확장하여 모바일 장치를 관리하려 한다고 가정합니다. Intune과 하이브리드 모바일 장치 관리 간의 차이점을 이해하려면 [Microsoft Intune 독립 실행형 관리와 System Center Configuration Manager를 사용하는 하이브리드 모바일 장치 관리 중에서 선택](choose-between-standalone-intune-and-hybrid-mobile-device-management.md)을 참조하세요.

Intune으로 Configuration Manager를 확장하면 관리자가 회사 소유 장치를 등록 및 관리하거나 사용자에게 개인 장치를 등록할 수 있는 권한을 부여할 수 있습니다. Intune에서 Configuration Manager를 사용하여 회사 소유 장치를 관리할 수도 있습니다.

## <a name="hybrid-mdm-enrollment"></a>하이브리드 MDM 등록
장치에 하이브리드 관리를 사용하려면 해당 장치를 서비스에 등록해야 합니다. 장치를 등록하는 방법은 장치 유형, 소유권 및 필요한 관리 수준에 따라 달라집니다.
- BYOD("Bring Your Own Device") 등록을 사용하면 사용자가 개인 휴대폰, 태블릿 또는 PC를 등록할 수 있습니다.
- COD(회사 소유 장치) 등록을 사용하면 원격 초기화, 공유 장치 또는 장치에 대한 사용자 선호도 등의 관리 시나리오를 지원할 수 있습니다.
- [Exchange ActiveSync](../plan-design/device-enrollment-methods.md#mobile-device-management-with-exchange-activesync-and-configuration-manager)를 클라우드에서 호스트하거나 온-프레미스로 사용하는 경우 등록하지 않고 간단한 Intune 관리를 사용할 수 있습니다. [Intune 클라이언트 소프트웨어](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)를 사용하여 Windows PC를 관리할 수도 있습니다.
