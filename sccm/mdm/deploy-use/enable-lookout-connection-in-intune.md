---
title: Intune에서 Lookout MTD 사용
description: Microsoft Intune 포털에서 Lookout MTD(모바일 위협 방어)를 사용하도록 설정합니다.
ms.date: 05/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 179aae5fdbd8d6c09a34dca6dd01437d5f61f7b8
ms.sourcegitcommit: 0a4556820fabe004d45a82b0ee1176f6891ac9f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37949597"
---
# <a name="enable-lookout-mtd-connection-in-the-intune-admin-console"></a>Intune 관리 콘솔에서 Lookout MTD 연결 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서는 Microsoft Intune에서 Lookout MTD(모바일 위협 방어) 연결을 사용하는 방법에 대해 설명합니다. 이 단계를 수행하기 전에 Lookout 콘솔에서 Intune 커넥터를 이미 구성한 상태여야 합니다. 아직 수행하지 않은 경우 [Lookout 모바일 위협 방어를 사용하여 구독 설정](set-up-your-subscription-with-lookout.md)에 설명된 단계를 수행합니다.



## <a name="enable-the-lookout-mtd-connector"></a>Lookout MTD 커넥터 사용

1. [Azure Portal](https://portal.azure.com)로 이동하여 Intune 자격 증명을 사용하여 로그인합니다. 성공적으로 로그인한 후 **Azure 대시보드**를 참조합니다.  

2. **Azure 대시보드**의 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.  

3. **Intune**을 선택하면 **Intune 대시보드**가 열립니다.  

4. **Intune 대시보드**에서 **장치 규정 준수**를 선택한 다음, **설치** 섹션 아래에서 **Mobile Threat Defense**를 선택합니다.  

5. **Mobile Threat Defense** 창에서 **추가**를 선택합니다.  

6. 드롭 다운 목록에서 **Lookout**을 **설치할 Mobile Threat Defense 커넥터**로 선택합니다.  

7. 조직의 요구 사항에 따라 설정/해제 옵션을 사용하도록 설정합니다.  



## <a name="mtd-toggle-options"></a>MTD 설정/해제 옵션

조직의 요구 사항에 따라 사용 하도록 설정해야 하는 MTD 설정/해제 옵션을 결정할 수 있습니다. 다음은 자세한 내용입니다.

- **Android 4.1+ 장치를 Lookout for Work MTD에 연결**: 이 옵션을 사용하도록 설정하면 Android 4.1+ 장치가 보안 위험을 Intune에 보고하게 할 수 있습니다.  
    - **수신된 데이터가 없는 경우 비규격으로 표시**: Intune이 Lookout에서 이 플랫폼의 장치에 대한 데이터를 수신하지 못하면 장치를 비규격으로 간주합니다.  

- **iOS 8.0+ 장치를 Lookout for Work MTD에 연결**: 이 옵션을 사용하도록 설정하면 iOS 8.0+ 장치가 보안 위험을 Intune에 보고하게 할 수 있습니다.
    - **수신된 데이터가 없는 경우 비규격으로 표시**: Intune이 Lookout에서 이 플랫폼의 장치에 대한 데이터를 수신하지 못하면 장치를 비규격으로 간주합니다.  

> [!TIP]  
> Mobile Threat Defense 창에서 Intune 및 Lookout 간의 **연결 상태** 및 **마지막 동기화** 시간을 확인할 수 있습니다.



## <a name="next-steps"></a>다음 단계
Lookout 및 Intune 통합 설정이 완료되었습니다. 이 솔루션을 구현하는 다음 몇 단계에는 [Lookout for Work 앱](configure-and-deploy-lookout-for-work-apps.md) 배포 및 [준수](enable-device-threat-protection-rule-compliance-policy.md) 정책 설정이 포함됩니다.

>[!IMPORTANT]
> 준수 정책 규칙을 만들고 조건부 액세스를 구성하기 전에 Lookout for Work 앱을 *구성해야 합니다*. 이렇게 하면 앱이 준비되고 최종 사용자가 앱을 설치하여 이메일 또는 기타 회사 리소스에 액세스할 수 있습니다.

[Lookout for Work 앱 구성](configure-and-deploy-lookout-for-work-apps.md)
