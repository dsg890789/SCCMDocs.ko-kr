---
title: MDM 기관 변경
titleSuffix: Configuration Manager
description: Configuration Manager(하이브리드)에서 MDM 기관을 Intune 독립 실행형으로 변경하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 04/11/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: cc397ab5-125f-4f17-905b-fab980194f49
ms.openlocfilehash: e5b97ccea5bb6e52badb12f635b5bc97061ca1d1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="change-your-mdm-authority"></a>MDM 기관 변경
Microsoft 지원에 문의하지 않고 기존 관리 장치에 대한 등록 취소 및 다시 등록을 수행할 필요 없이 MDM 기관을 변경할 수 있습니다. 이 문서에서는 Configuration Manager 콘솔(하이브리드)에서 구성된 기존 Microsoft Intune 테넌트를 Intune 독립 실행형으로 변경하는 단계를 설명합니다. 이 문서의 단계를 완료하면 장치가 [Azure Portal](https://portal.azure.com)에서 Microsoft Intune을 통해 관리됩니다. 

> [!Note]    
> MDM 기관이 Intune으로 설정된 기존 Microsoft Intune 테넌트를 Configuration Manager(하이브리드)로 변경하려면 [MDM 기관 변경](https://docs.microsoft.com/intune-classic/deploy-use/change-mdm-authority)을 참조하세요.

> [!Important]    
> 이 문서에서는 이전에 사용자를 마이그레이션하지 않은 경우 MDM 기관을 변경합니다. [사용자의 하위 집합을 마이그레이션한](migrate-hybridmdm-to-intunesa.md) 후 MDM 기관을 변경하려면 [MDM 기관을 변경](migrate-change-mdm-authority.md)을 참조하세요.

## <a name="key-considerations"></a>핵심 고려 사항
MDM 기관으로 변경한 후 전환 시간은 최대 8시간으로 예상하시면 됩니다. 장치에서 서비스를 검사하고 서비스와 동기화하기까지 이처럼 시간이 오래 걸릴 수 있습니다. 등록된 장치가 변경 후에도 계속 관리되고 보호되도록 하려면 새 Intune에서 바로 설정을 구성하세요. 다음 고려 사항에 유의하세요.
- 새 MDM 기관(Intune 독립 실행형)의 설정이 장치의 기존 설정을 대체하도록 장치는 변경 후에 서비스에 연결해야 합니다.
- MDM 기관을 변경하면 이전 MDM 기관(하이브리드)의 일부 기본 설정(예: 프로필)은 최대 7일 동안 장치에 남아 있습니다. 새 MDM 기관에서 가능한 빨리 앱과 설정(정책, 프로필, 앱 등)을 구성하는 것이 좋습니다. 또 기존에 등록한 장치가 있는 사용자가 포함된 사용자 그룹에 설정을 배포합니다. MDM 기관을 변경한 후에 장치가 서비스와 연결되면 새 MDM 기관에서 새 설정을 받습니다. 대상이 새로 지정된 정책은 장치의 기존 정책을 재정의합니다.
- 새 MDM 기관으로 변경한 후에 [Azure Portal](https://portal.azure.com)에서 준수 데이터가 정확히 보고될 때까지 최대 1주가 걸릴 수 있습니다. 그러나 Azure Active Directory 및 장치의 준수 상태는 정확하게 유지됩니다. 장치는 계속 보호됩니다.
- 연결된 사용자가 없는 장치는 새 MDM 기관으로 마이그레이션되지 않습니다. 이 동작은 일반적으로 iOS 장치 등록 프로그램이 있는 경우 또는 대량 등록 시나리오에 해당합니다. 이러한 장치의 경우 새 MDM 기관으로 이동하려면 지원 서비스에 문의하세요.

## <a name="prepare-to-change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경하기 위한 준비
다음 정보를 검토하여 MDM 기관 변경을 준비하세요.
- 새 MDM 기관으로 변경한 후에 장치가 서비스에 연결되는 데 최대 8시간이 걸릴 수 있습니다.
- 현재 하이브리드에서 관리되는 모든 사용자가 MDM 기관 변경 전에 Intune/EMS 라이선스를 할당받았는지 확인합니다. 이 라이선스는 MDM 기관 변경 후에 사용자 및 해당 장치가 Intune 독립 실행형에서 관리되도록 합니다. 자세한 내용은 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)을 참조하세요.
- 관리자 사용자 계정이 Intune/EMS 라이선스를 할당받았는지 확인합니다. MDM 기관으로 변경하기 전에 관리 사용자 계정이 Intune에 로그인할 수 있는지 확인하세요. MDM 기관을 변경하기 전에 MDM 기관은 [Azure Portal](https://portal.azure.com)의 Intune에서 **Configuration Manager로 설정**(하이브리드 테넌트)을 표시해야 합니다.
- MDM 기관을 변경하는 동안 최종 사용자에게 거의 영향을 주지 않아야 합니다. 

## <a name="change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경
MDM 기관을 Intune 독립 실행형으로 변경하는 프로세스는 다음과 같은 고급 단계를 포함합니다.  
- Configuration Manager 콘솔에서 **MDM 기관을 Microsoft Intune으로 변경** 옵션을 사용하여 기존 Microsoft Intune 구독을 제거합니다.
- [Azure Portal](https://portal.azure.com)의 Intune에서 새 MDM 기관(Intune)의 새 설정과 앱을 구성하고 배포합니다.
- 다음 번에 장치가 서비스에 연결되면 새 MDM 기관과 동기화되어 새 설정을 받습니다.

#### <a name="to-change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경하려면
1. Configuration Manager 콘솔에서 **관리** &gt; **개요** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 기존 Intune 구독을 삭제합니다.
2. **MDM 기관을 Microsoft Intune으로 변경**을 클릭하고 **다음**을 클릭합니다.
   ![Microsoft Intune 구독 제거 마법사, 소개 페이지](./media/mdm-change-delete-subscription.png)
3. Configuration Manager에서 MDM 기관을 설정할 때 원래 사용했던 Intune 테넌트에 로그인합니다.
4. **다음** 을 클릭하여 마법사를 완료합니다.
5. MDM 기관이 이제 **Microsoft Intune**으로 설정되었습니다. Intune 구독은 Configuration Manager 콘솔의 Microsoft Intune 구독 노드에 표시되지 않습니다. 
6. MDM 기관이 설정되었는지 확인하려면 다음 단계를 수행합니다. 이전에 사용한 것과 동일한 Intune 테넌트를 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다. 
    b. **추가 서비스** > **모니터링 + 관리** > **Intune** > **장치 등록**을 차례로 선택합니다. MDM 기관이 **개요** 블레이드의 오른쪽 위에 표시됩니다. 

## <a name="next-steps"></a>다음 단계
MDM 기관 변경이 완료되면 다음 단계를 검토합니다.
- Intune 서비스에서 테넌트의 MDM 기관이 변경되었음을 감지하면 서비스에 체크 인하고 동기화하기 위해 등록된 모든 장치에 알림 메시지를 보냅니다. 이 동작은 정기적으로 예약된 체크인이 아닙니다. 따라서 테넌트의 MDM 기관을 하이브리드에서 Intune 독립 실행형으로 변경하면 전원이 켜져 있고 온라인 상태인 모든 장치가 서비스에 연결되고, 새 MDM 기관을 수신하고, Intune 독립 실행형으로 관리됩니다. 이러한 장치의 관리 및 보호가 중단되는 일은 없습니다.
- MDM 기관을 변경하는 동안(또는 직후에) 전원이 꺼져 있거나 오프라인 상태인 장치는 전원이 켜지고 온라인 상태가 될 때 새 MDM 기관의 서비스와 연결되어 동기화됩니다.  
- 사용자는 장치에서 서비스로의 체크 인을 수동으로 시작하여 새 MDM 기관을 빠르게 변경할 수 있습니다. 회사 포털 앱을 사용하고 장치 준수 검사를 시작하여 이 작업을 쉽게 수행할 수 있습니다.
- 장치가 MDM 기관을 변경한 다음 서비스에 체크 인되고 동기화된 후에 작업이 제대로 작동하는지 확인하려면 [Azure Portal](https://portal.azure.com)에서 장치를 찾습니다. 이전에 Configuration Manager(하이브리드)에서 관리되었던 장치는 이제 Intune에서 관리되는 장치로 표시됩니다.    
- MDM 기관 변경 동안 장치가 오프라인 상태일 때와 장치가 서비스로 체크 인될 때까지의 중간 기간이 있습니다. 이 중간 기간 동안 장치가 보호된 상태에서 제대로 작동하도록, 최대 7일 동안(또는 장치가 새 MDM 기관에 연결되고 기존 설정을 덮어쓰는 새 설정을 받을 때까지) 장치에서 다음 프로필이 그대로 유지됩니다.
    - 전자 메일 프로필
    - VPN 프로필
    - 인증서 프로필
    - Wi-Fi 프로필
    - 구성 프로필
- 이전 설정을 덮어쓰려면 기존 설정을 덮어쓸 새 설정이 이전 이름과 같은 이름이어야 합니다. 그렇지 않으면 장치에서 프로필 및 정책이 중복될 수 있습니다.    

  > [!TIP]   
  > 모범 사례는 MDM 기관 변경이 완료된 즉시, 모든 배포 뿐만 아니라 모든 관리 설정과 구성을 만드는 것입니다. 이렇게 하면 중간 기간 동안 장치가 보호되고 적극적으로 관리될 수 있습니다.   
-  MDM 기관을 변경한 후 다음 단계를 수행하여 새 장치가 새 기관에 성공적으로 등록되었는지 확인합니다.   
    - 새 장치 등록
    - 새로 등록된 장치가 [Azure Portal](https://portal.azure.com)에 표시되는지 확인합니다.
    - [Azure Portal](https://portal.azure.com)에서 [원격 잠금]과 같은 작업을 장치로 수행합니다. 성공한 경우 장치가 새 MDM 기관에서 관리되는 것입니다.
- 특정 장치에 문제가 있는 경우 등록을 취소하고 장치를 다시 등록합니다. 이 작업은 가능한 한 빨리 새 기관에 연결하여 관리를 받도록 합니다.
- [Android for Work](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)를 하이브리드 테넌트로 활성화한 후 Intune 독립 실행형으로 테넌트를 마이그레이션하면 등록 제한이 적용되는 Android for Work 설정이 허용이 아닌 차단됨으로 표시될 수 있습니다. Android for Work 등록을 다시 활성화하려면 이를 **허용**으로 수동 설정합니다.<!--512117-->