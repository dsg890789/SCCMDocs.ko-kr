---
title: MDM 기관을 Intune으로 변경
titleSuffix: Configuration Manager
description: Configuration Manager(하이브리드)에서 MDM 기관을 Intune 독립 실행형으로 변경하는 방법에 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: be503ec9-5324-4f7c-bcf5-77204328e99c
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d6a909be4b1817b9a251046d666839e2e351443
ms.sourcegitcommit: 0bf253085adeca0d9ea62d76497eb5ebf5ce89da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57012431"
---
# <a name="change-your-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경

*적용 대상: System Center Configuration Manager(현재 분기)*    

Configuration Manager 콘솔(하이브리드 MDM)에서 구성된 기존 Microsoft Intune 테넌트를 Intune 독립 실행형으로 변경할 수 있습니다. 테넌트 수준 MDM 기관을 Intune으로 변경하는 것은 클라우드 전용 구성에서 [하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션](migrate-hybridmdm-to-intunesa.md)하는 프로세스의 최종 단계입니다.    

> [!Important]    
> 먼저 하이브리드 MDM 사용자를 Intune으로 마이그레이션하지 않고 MDM 기관을 변경하려면 [MDM 기관 변경](change-mdm-authority.md)을 참조하세요.

이 문서는 기존 Microsoft Intune 테 넌 트를 Intune 독립 실행형 Configuration Manager 콘솔 (하이브리드)에서 구성 변경 하는 방법에 대 한 정보를 제공 합니다. 다음 단계를 이미 완료 했다고 가정 합니다.
- [Intune 데이터 가져오기 도구](migrate-import-data.md)를 사용하여 Configuration Manager 개체를 Intune으로 가져왔습니다. 
- [Intune에서 사용자 마이그레이션을 준비](migrate-prepare-intune.md)하여 사용자와 장치가 마이그레이션된 이후에도 계속 관리되도록 했습니다.
- [특정 사용자의 MDM 기관을 변경(혼합 MDM 기관)](migrate-mixed-authority.md)하여 Azure Portal에서 사용자 디바이스 관리를 시작했습니다.


## <a name="users-and-devices-that-havent-been-migrated"></a>사용자 및 장치 마이그레이션되지 않은
이미 많은 사용자를 마이그레이션 하 고 작업이 예상 대로 작동 하는지 확인 하는 Intune 기능을 테스트 했습니다. 정책, 프로필 및 앱을 Intune에서 구성한 및 장치에서 개체를 철저히 테스트 했습니다. MDM 기관 변경 후 테넌트 수준 정책에 필요한 새 구성은 없습니다. 그러나 사용자와 이전에 마이그레이션한 하지 않은 장치에 대 한 MDM 기관 변경 후 예상 되는 상황에 대 한 다음 정보를 검토 합니다.    

- 가능성이 최대 8 시간의 장치 확인 하 고 서비스와 동기화 되기 전에 전환 시간을 합니다.  

- 디바이스는 새 MDM 기관(Intune 독립 실행형)의 설정이 디바이스의 기존 설정을 대체하도록 변경 후에도 서비스에 연결되어야 합니다.  

- 이전 MDM 기관(하이브리드)의 일부 기본 설정(예: 프로필)은 최대 7일 동안 디바이스에 남아 있습니다.  

- 연결된 사용자가 없는 디바이스는 새 MDM 기관으로 마이그레이션되지 않습니다. 이러한 장치는 일반적으로 iOS 장치 등록 프로그램에 대 한 시나리오 또는 대량 등록 합니다. 이러한 디바이스의 경우 새 MDM 기관으로 이동하려면 지원 서비스에 문의해야 합니다.



## <a name="prerequisites"></a>필수 구성 요소
다음 정보를 검토하여 MDM 기관 변경을 준비하세요.
- MDM 기관을 변경하는 옵션을 사용하려면 Configuration Manager 버전 1610 이상이 있어야 합니다.
- 현재 하이브리드 MDM에서 관리 하는 모든 사용자에 게 Intune/EMS 라이선스를 할당할 수 있는지 확인 라이선스는 사용자 및 장치 관리 Intune 독립 실행형으로 MDM 기관 변경 후 했는지 확인 합니다. 자세한 내용은 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)을 참조하세요.
- 관리자 사용자 계정이 Intune/EMS 라이선스를 할당받았는지 확인합니다.

## <a name="change-the-mdm-authority-to-intune"></a>MDM 기관을 Intune으로 변경
다음 절차에 따라 테넌트 수준 MDM 기관을 Intune으로 변경합니다.

1. Configuration Manager 콘솔에서로 이동 합니다 **관리** 작업 영역에서 확장 **Cloud Services**, 선택는 **Microsoft Intune 구독** 노드. 기존 Intune 구독은 삭제합니다.  

2. 선택 **Microsoft Intune에 MDM 기관을 변경**를 선택한 후 **다음**합니다.

    ![Microsoft Intune 구독 제거 대화 상자](media/mdm-change-delete-subscription.png)  

3. Configuration Manager에서 MDM 기관을 설정할 때 원래 사용했던 Intune 테넌트에 로그인합니다. 선택 **다음** 마법사를 완료 합니다.

    이제 MDM 기관이 다시 설정되었습니다. Intune 구독은 Configuration Manager 콘솔의 Microsoft Intune 구독 노드에 더 이상 표시되지 않습니다.  

4. 에 로그인 합니다 [Intune 포털](https://aka.ms/IntunePortal)합니다.

5. 선택 **장치 등록**합니다.  

6. 장치 등록 개요를 표시 합니다 **MDM 기관을** 속성.

   > [!Important]    
   > Intune 클래식 콘솔을 사용 하지 마세요. Azure portal에서 Intune에 로그인 합니다.  

7. MDM 기관이 **Microsoft Intune**으로 변경되었는지 확인합니다. 



## <a name="after-migration"></a>마이그레이션 후

MDM 기관 변경이 완료되면 다음 정보를 검토합니다.

- MDM 기관을 변경하는 동안 최종 사용자에게 거의 영향을 주지 않아야 합니다.  

- 테 넌 트 수준 정책을 다시 구성할 필요가 없습니다.  

- 테 넌 트 수준 정책을 편집 해야 할 경우 Azure portal의 Intune에서이 작업을 수행 합니다.  

- 특정 디바이스에 문제가 있는 경우 등록을 취소하고 디바이스를 다시 등록합니다. 이 작업을 가져옵니다 새 기관에 연결 하 고 최대한 신속 하 게 관리 합니다.


#### <a name="validate-new-device-enrollment"></a>새 장치 등록 확인
MDM 기관을 변경한 후 새 장치가 새 기관으로 성공적으로 등록 되었는지 유효성을 검사 하려면 다음 단계를 사용 합니다.   
1. 새 디바이스 등록
2. 새로 등록 된 장치가 Intune에 표시 되는지 확인
3. 같은 Intune 포털에서 장치 동작을 시작할 [원격 잠금](https://docs.microsoft.com/intune/device-remote-lock)합니다. 성공한 경우 장치가 새 MDM 기관에 의해 성공적으로 관리 됩니다.


#### <a name="for-users-and-devices-that-you-havent-previously-migrated"></a>이전에 마이그레이션한 않은 장치와 사용자에 대 한

- 장치에서 이제 표시 되는지 확인 합니다 **장치** 관리 되는 장치로 페이지입니다. 를 표시 하기 전에 이러한 장치 체크 인를 업데이트 하 고 MDM 기관 변경 후 서비스와 동기화 해야 합니다. 

- Intune 서비스에서 테 넌 트의 MDM 기관이 변경 되었음을 감지를 모든 등록 된 장치에 알림 메시지를 보냅니다. 이 장치를 체크 인하고 서비스와 동기화 하도록 지시 합니다. 이 알림은 정기적으로 예약 된 체크 인에 외부에서 발생합니다. MDM 기관이 하이브리드에서 Intune 독립 실행형 테 넌 트를 변경한 후 모든 온라인 장치 서비스에 연결 합니다. 새 MDM 기관을 수신 하 고는 관리 되는 Intune 독립 실행형으로 이제 합니다. 이러한 장치에 대 한 보호 관리에 중단이 발생 하지 있습니다.

- 동안 또는 MDM 기관 변경 직후 오프 라인 상태인 장치에 대 한가 연결 하 고 해당 하는 전원이 켜져 있고 온라인 때 새 MDM 기관에서 해당 서비스와 동기화 합니다.  

- 수동으로 서비스에 장치에서 체크 인을 시작 하 여 새 MDM 기관으로 신속 하 게 변경할 수 있습니다. 장치 준수 검사를 시작 하려면 회사 포털 앱을 사용 합니다.

- MDM 기관에서 및 해당 장치가 서비스에 체크 인할 때 변경 하는 동안 장치는 오프 라인 때 까지의 중간 기간이 있습니다. 되도록 장치가 보호 되 고 기능이 중간 기간 동안, 최대 7 일에 대 한 다음 프로필을 장치에 남아 있습니다. 또한 장치는 새 MDM 기관에 연결 하 고 기존 덮어쓰는 새 설정의 받을 때까지 유지할 수 있습니다.
    - 전자 메일 프로필
    - VPN 프로필
    - 인증서 프로필
    - Wi-Fi 프로필
    - 구성 프로필

- 사용자와 연결 되지 않은 장치의 경우 MDM 기관을 변경 하는 데 지원에 문의. 

#### <a name="bkmk-ki-dep"></a> Apple DEP 장치 레코드
<!--ICM 105091970--> 하이브리드 MDM에서에서 마이그레이션이 완료 한 후에 Configuration Manager 콘솔에서 레코드를 유지 하는 Apple DEP 장치를 확인할 수 있습니다. MDM 기관을 Intune로 변경 되 면 Configuration Manager에서 이러한 장치를 제거할 수 없습니다. 

두 가지 해결 방법이 있습니다.

- MDM 기관을 변경 하기 전에이 동작을 표시 하는 경우 Configuration Manager에서 삭제 DEP 기록 합니다.  

- 이미 마이그레이션된 했습니다 하 고 Configuration Manager를 여전히 사용 하는 경우 다음 명령을 사용 하 여 다음 SQL 사이트 데이터베이스에서 레코드를 제거 합니다.  

    ```SQL
    Delete from MDMCorpOwnedDevices where DeviceType=8 and DiscoverySources=4
    ```



## <a name="next-steps"></a>다음 단계

마이그레이션을 완료 했으므로 이제 Intune 사용 하 여 모바일 장치를 관리 합니다. 자세한 내용은 [Microsoft Intune의 새로운 기능](https://docs.microsoft.com/intune/whats-new)합니다.

