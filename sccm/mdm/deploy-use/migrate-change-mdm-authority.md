---
title: MDM 기관을 Intune으로 변경
titleSuffix: Configuration Manager
description: Configuration Manager(하이브리드)에서 MDM 기관을 Intune 독립 실행형으로 변경하는 방법에 알아봅니다.
author: aczechowski
manager: dougeby
ms.date: 12/05/2017
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: be503ec9-5324-4f7c-bcf5-77204328e99c
ms.openlocfilehash: b295dad503b801ff9d04767f75c1688107016d0b
ms.sourcegitcommit: 493cc42f05b9388ef872e466e5a75d569642b9fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569683"
---
# <a name="change-your-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경

*적용 대상: System Center Configuration Manager(현재 분기)*    

Configuration Manager 콘솔(하이브리드 MDM)에서 구성된 기존 Microsoft Intune 테넌트를 Intune 독립 실행형으로 변경할 수 있습니다. 테넌트 수준 MDM 기관을 Intune으로 변경하는 것은 클라우드 전용 구성에서 [하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션](migrate-hybridmdm-to-intunesa.md)하는 프로세스의 최종 단계입니다.    

> [!Important]    
> 먼저 하이브리드 MDM 사용자를 Intune으로 마이그레이션하지 않고 MDM 기관을 변경하려면 [MDM 기관 변경](change-mdm-authority.md)을 참조하세요.

이 문서에서는 Configuration Manager 콘솔(하이브리드)에서 구성된 기존 Microsoft Intune 테넌트를 Intune 독립 실행형으로 변경하는 방법을 설명하며, 다음 단계를 이미 완료했다고 가정합니다.
- [Intune 데이터 가져오기 도구](migrate-import-data.md)를 사용하여 Configuration Manager 개체를 Intune으로 가져왔습니다. 
- [Intune에서 사용자 마이그레이션을 준비](migrate-prepare-intune.md)하여 사용자와 장치가 마이그레이션된 이후에도 계속 관리되도록 했습니다.
- [특정 사용자의 MDM 기관을 변경(혼합 MDM 기관)](migrate-mixed-authority.md)하여 Azure Portal에서 사용자 장치 관리를 시작했습니다.


## <a name="users-and-devices-that-have-not-been-migrated"></a>마이그레이션되지 않은 사용자 및 장치
이미 많은 사용자를 마이그레이션하고 Intune 기능을 테스트하여 기능이 올바로 작동하는지 테스트했습니다. 따라서 정책, 프로필, 앱 등이 Intune에 구성되어 있고 장치에서 개체를 철저히 테스트했습니다. MDM 기관 변경 후 테넌트 수준 정책에 필요한 새 구성은 없습니다. 그러나 이전에 마이그레이션되지 않은 사용자 및 장치의 경우에는 MDM 기관 변경 후 예상되는 상황을 다음 정보에서 확인하세요.    
- 장치가 체크 인되고 서비스와 동기화될 때까지 전환 시간(최대 8시간)이 있기 마련입니다.
- 장치는 새 MDM 기관(Intune 독립 실행형)의 설정이 장치의 기존 설정을 대체하도록 변경 후에도 서비스에 연결되어야 합니다.
- 이전 MDM 기관(하이브리드)의 일부 기본 설정(예: 프로필)은 최대 7일 동안 장치에 남아 있습니다. 
- 연결된 사용자가 없는 장치(일반적으로 iOS 장치 등록 프로그램 또는 대량 등록 시나리오가 있는 경우)는 새 MDM 기관으로 마이그레이션되지 않습니다. 이러한 장치의 경우 새 MDM 기관으로 이동하려면 지원 서비스에 문의해야 합니다.

## <a name="prerequisites"></a>필수 구성 요소
다음 정보를 검토하여 MDM 기관 변경을 준비하세요.
- MDM 기관을 변경하는 옵션을 사용하려면 Configuration Manager 버전 1610 이상이 있어야 합니다.
- 현재 하이브리드 MDM에서 관리되는 모든 사용자가 MDM 기관 변경 전에 Intune/EMS 라이선스를 할당받았는지 확인합니다. 라이선스가 있으면 MDM 기관 변경 후에 사용자 및 해당 장치가 Intune 독립 실행형에서 관리됩니다. 자세한 내용은 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)을 참조하세요.
- 관리자 사용자 계정이 Intune/EMS 라이선스를 할당받았는지 확인합니다.

## <a name="change-the-mdm-authority-to-intune"></a>MDM 기관을 Intune으로 변경
다음 절차에 따라 테넌트 수준 MDM 기관을 Intune으로 변경합니다.

1.  Configuration Manager 콘솔에서 **관리** &gt; **개요** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 기존 Intune 구독을 삭제합니다.
2.  **MDM 기관을 Microsoft Intune으로 변경**을 클릭하고 **다음**을 클릭합니다.

    ![Microsoft Intune 구독 제거 대화 상자](media/mdm-change-delete-subscription.png)
3.  Configuration Manager에서 MDM 기관을 설정할 때 원래 사용했던 Intune 테넌트에 로그인합니다.
4.  **다음** 을 클릭하여 마법사를 완료합니다.
5.  이제 MDM 기관이 다시 설정되었습니다. Intune 구독은 Configuration Manager 콘솔의 Microsoft Intune 구독 노드에 더 이상 표시되지 않습니다.
6.  [Intune 포털](https://aka.ms/IntunePortal)에 로그인합니다.
7.  Microsoft Intune 블레이드에서 **장치 등록**을 클릭합니다.
8.  장치 등록 개요 블레이드에서 **MDM 기관** 속성을 참조합니다.

  > [!Important]    
  > Intune 클래식 콘솔을 사용하지 마세요. Azure Portal에서 Intune에 로그인해야 합니다.
7.  MDM 기관이 **Microsoft Intune**으로 변경되었는지 확인합니다. 

## <a name="next-steps"></a>다음 단계
MDM 기관 변경이 완료되면 다음 정보를 검토합니다.
- MDM 기관을 변경하는 동안 최종 사용자에게 거의 영향을 주지 않아야 합니다. 
- 테넌트 수준 정책을 다시 구성할 필요가 없습니다. 
- MDM 기관을 변경 후 Azure Portal에서 Intune의 테넌트 수준 정책을 편집할 수 있습니다.
-  MDM 기관을 변경한 후 다음 단계를 수행하여 새 장치가 새 기관에 성공적으로 등록되었는지 확인합니다.   
    - 새 장치 등록
    - 새로 등록된 장치가 Intune에 표시되어야 합니다.
    - 장치의 관리 콘솔에서 원격 잠금 등의 작업을 수행합니다. 성공한 경우 장치가 새 MDM 기관에서 관리되는 것입니다.
- 특정 장치에 문제가 있는 경우 등록을 취소했다가 다시 등록하여 가능한 한 빠른 시일 내에 장치가 새 기관에 연결되고 관리될 수 있도록 합니다.
- 이전에 마이그레이션되지 않은 사용자 및 장치의 경우:
    - 장치가 **장치** 블레이드에서 관리되는 장치로 표시되는지 확인합니다. 이러한 장치는 MDM 기관 변경 후 체크 인하고 서비스와 동기화되어야만 표시됩니다. 
    - Intune 서비스에서 테넌트의 MDM 기관이 변경되었음을 감지하면 서비스에 체크 인하고 동기화하기 위해 등록된 모든 장치에 알림 메시지를 보냅니다(정기적으로 예약된 체크 인이 아님). 따라서 테넌트의 MDM 기관이 하이브리드에서 Intune 독립 실행형으로 변경된 후에 전원이 켜져 있고 온라인 상태인 모든 장치는 서비스에 연결되고, 새 MDM 기관을 수신하고, 이제 Intune 독립 실행형으로 관리되게 됩니다. 이러한 장치의 관리 및 보호가 중단되는 일은 없습니다.
    - MDM 기관을 변경하는 동안(또는 직후에) 전원이 꺼져 있거나 오프라인 상태인 장치는 전원이 켜지고 온라인 상태가 될 때 새 MDM 기관의 서비스와 연결되어 동기화됩니다.  
    - 사용자는 장치에서 서비스로의 체크 인을 수동으로 시작하여 새 MDM 기관을 빠르게 변경할 수 있습니다. 회사 포털 앱을 사용하고 장치 준수 검사를 시작하여 체크 인을 쉽게 수행할 수 있습니다.
    - MDM 기관 변경 동안 장치가 오프라인 상태일 때와 장치가 서비스로 체크 인될 때까지의 중간 기간이 있습니다. 이 중간 기간 동안 장치가 보호된 상태에서 제대로 작동하도록, 최대 7일 동안(또는 장치가 새 MDM 기관에 연결되고 기존 설정을 덮어쓰는 새 설정을 받을 때까지) 장치에서 다음 프로필이 그대로 유지됩니다.
        - 전자 메일 프로필
        - VPN 프로필
        - 인증서 프로필
        - Wi-Fi 프로필
        - 구성 프로필
    - 사용자와 연결되지 않은 장치의 MDM 기관 변경을 지원하려면 지원 센터에 문의하세요. 
