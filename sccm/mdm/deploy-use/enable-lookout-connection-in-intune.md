---
title: "Intune에서 Lookout MTP 사용 | Microsoft 문서"
description: "Intune 관리 콘솔에서 Lookout 모바일 위협 방지를 사용하도록 설정합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 65d3dff359987e1d3175b06aa7a03827d48bc97d
ms.lasthandoff: 03/06/2017


---
# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Intune 관리 콘솔에서 Lookout MTP 연결 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 Intune에서 Lookout MTP 연결을 사용하도록 설정하는 방법을 보여 줍니다. 이 단계를 수행하기 전에 Lookout 콘솔에서 Intune 커넥터를 이미 구성한 상태여야 합니다.  아직 수행하지 않은 경우 [Lookout 모바일 위협 방지를 사용하여 구독 설정](set-up-your-subscription-with-lookout.md)에 설명된 단계를 수행합니다.

intune에서 Lookout MTP 연결을 사용하도록 설정하려면 [Microsoft Intune 관리자 콘솔](https://manage.microsoft.com)의 **관리** 페이지에서 **타사 서비스 통합**을 선택합니다. **Lookout 상태**를 선택하고 토글 단추를 사용하여 **MTP와 동기화**를 사용하도록 설정합니다.

![사용 토글 단추가 강조 표시된 Lookout 동기화 페이지 스크린샷](media/lookout-intune-synchronization.png)

Intune 관리자 콘솔에서 Lookout 및 Intune 통합 설정이 완료되었습니다.  이 솔루션을 구현하는 다음 몇 단계에는 [Lookout for Work 앱](configure-and-deploy-lookout-for-work-apps.md) 배포 및 [준수](enable-device-threat-protection-rule-compliance-policy.md) 정책 설정이 포함됩니다.

>[!IMPORTANT]
> 준수 정책 규칙을 만들고 조건부 액세스를 구성하기 전에 Lookout for Work 앱을 **구성해야 합니다**. 이렇게 하면 앱이 준비되고 최종 사용자가 앱을 설치하여 메일 또는 기타 회사 리소스에 액세스할 수 있습니다.

## <a name="next-steps"></a>다음 단계
[Lookout for Work 앱 구성](configure-and-deploy-lookout-for-work-apps.md)

