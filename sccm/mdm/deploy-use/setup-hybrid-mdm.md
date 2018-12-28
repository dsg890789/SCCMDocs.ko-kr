---
title: 하이브리드 MDM 설정
titleSuffix: Configuration Manager
description: Configuration Manager 및 Intune을 사용하여 하이브리드 디바이스 등록을 설정합니다.
ms.date: 08/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a69f849d4843ff7a0cf7df4a0b6de044a9506301
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53421810"
---
# <a name="set-up-hybrid-mdm-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager 및 Microsoft Intune에서 하이브리드 MDM 설정

*적용 대상: System Center Configuration Manager (현재 분기)*


Configuration Manager를 사용하여 iOS, Windows 및 Android 디바이스를 관리하려면 먼저 Intune에 등록해야 합니다. Configuration Manager 및 Intune을 사용하여 하이브리드 디바이스 등록을 설정하려면 다음 단계를 따르세요. 다음 단계를 완료하면 사용자에 대해 BYOD("Bring Your Own Device") 등록을 사용하도록 설정됩니다. 이 단계는 [BYOD 디바이스 등록](enroll-hybrid-ios-mac.md) 및 [회사 소유 디바이스 등록](enroll-company-owned-devices.md)의 필수 조건이기도 합니다.

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 [기능은 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  



## <a name="set-up-steps"></a>설정 절차

 |단계|세부 정보|  
 |-----------|-------------|  
 |**1 단계:** [MDM 컬렉션 만들기](create-mdm-collection.md)|해당 디바이스를 등록할 수 있는 사용자를 포함하는 Configuration Manager 사용자 컬렉션을 만듭니다.|  
 |**2 단계:** [도메인 이름 요구 사항](confirm-dns.md)|조직의 DNS(도메인 이름 서비스) 및 Active Directory 사용자 관리가 MDM 요구 사항을 충족하는지 확인합니다.|
 |**3 단계:** [Intune 구독 구성](configure-intune-subscription.md)|Intune 서비스를 사용하면 인터넷을 통해 디바이스를 관리할 수 있습니다.|  
 |**4 단계:** [사용 약관 추가](terms-and-conditions.md)| 회사 포털 앱을 사용하기 전에 사용자가 동의해야 하는 계약조건을 만듭니다.|
 |**5 단계:** [서비스 연결 지점 만들기](create-service-connection-point.md)|서비스 연결 지점은 설정과 소프트웨어 배포 정보를 Configuration Manager에 전송하고 모바일 디바이스에서 상태 및 인벤토리 메시지를 검색합니다. |  
 |**6 단계:** [플랫폼 등록 사용](enable-platform-enrollment.md)|iOS 및 Windows 디바이스에 대한 MDM 등록에는 서비스와 디바이스 간의 통신을 위한 추가 단계가 필요합니다. Android에는 추가 구성이 필요하지 않습니다.|  
 |**7 단계:** [추가 관리 설정](set-up-additional-management.md)|(선택 사항) 등록된 디바이스에 대한 구성 항목 및 조건부 액세스를 설정합니다.|
 |**8 단계:** [MDM 구성 확인](verify-mdm-configuration.md)|로그 파일을 보고 서비스 연결 지점이 성공적으로 만들어졌는지, 그리고 사용자 계정이 동기화되고 있는지 확인합니다.|



## <a name="enroll-devices"></a>디바이스 등록

하이브리드 설치가 완료된 후 Configuration Manager에서 다음과 같은 다양한 방법으로 디바이스를 등록할 수 있습니다.

- **회사 소유 (COD) 장치:** [회사 소유 장치 등록](enroll-company-owned-devices.md) 회사 소유 장치를 등록 하려면 다양 한 플랫폼별 방법에 지침을 제공 합니다.  

- **사용자 소유 (BYOD) 장치:** [사용자 소유 (BYOD) 장치 등록](enroll-hybrid-ios-mac.md) 사용자 소유 장치를 등록 하는 방법에 지침을 제공 합니다.  



## <a name="see-also"></a>참고 항목

Configuration Manager 없이 Intune을 사용하고 싶으세요?
> [!div class="button"]
> [Intune 문서 보기 >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)


