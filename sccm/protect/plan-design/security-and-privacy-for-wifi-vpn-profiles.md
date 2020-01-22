---
title: Wi-Fi 및 VPN 프로필 보안 및 개인 정보
titleSuffix: Configuration Manager
description: Configuration Manager에서 디바이스의 Wi-Fi 및 VPN 프로필 관리를 위한 보안 권고 사항을 알아봅니다.
ms.date: 01/14/2020
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: a6f444e35e16a3b42414fdc6fbee50687cf76f2f
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035078"
---
# <a name="security-and-privacy-for-wi-fi-and-vpn-profiles-in-configuration-manager"></a>Configuration Manager의 Wi-Fi 및 VPN 프로필에 대한 보안 및 개인 정보

*적용 대상: Configuration Manager(현재 분기)*

## <a name="security-recommendations"></a>보안 권장 사항

디바이스의 Wi-Fi 및 VPN 프로필을 관리하는 경우 다음 보안 모범 사례를 따르세요.

### <a name="choose-the-most-secure-options-that-your-wi-fi-and-vpn-infrastructure-and-client-operating-systems-can-support"></a>Wi-Fi 및 VPN 인프라 및 클라이언트 운영 체제에서 지원할 수 있는 가장 강력한 보안 옵션을 선택합니다.

Wi-Fi 및 VPN 프로필을 사용하면 디바이스에서 이미 지원하는 Wi-Fi 및 VPN 설정을 중앙에서 편리하게 배포하고 관리할 수 있습니다. Configuration Manager는 Wi-Fi 및 VPN 기능을 추가하지 않습니다. 디바이스와 인프라에 권장되는 모든 보안 권장 사항을 식별하여 구현하고 따르세요.

## <a name="privacy-information"></a>개인 정보 취급 방침

Wi-Fi 및 VPN 프로필을 사용하여 클라이언트 디바이스를 Wi-Fi 및 VPN 서버에 연결하도록 구성할 수 있습니다. 그런 다음 Configuration Manager를 사용하여 프로필이 적용된 후 해당 디바이스가 호환되는지를 평가합니다. 관리 지점에서 호환성 정보를 사이트 서버로 보내며, 해당 정보는 사이트 데이터베이스에 저장됩니다. 디바이스에서 관리 지점으로 정보를 보낼 때 정보가 암호화되지만 사이트 데이터베이스에는 암호화된 형식으로 저장되지 않습니다. 이 데이터베이스는 사이트 유지 관리 작업인 **오래된 구성 관리 데이터 삭제** 에서 정보를 삭제할 때까지 해당 정보를 보존합니다. 기본 삭제 간격은 90일이지만 변경할 수 있습니다. 규정 준수 정보는 Microsoft로 전송되지 않습니다.

기본적으로 디바이스는 Wi-Fi 및 VPN 프로필을 평가하지 않습니다. 또한 프로필을 구성한 다음 사용자에게 배포해야 합니다.  

Wi-Fi 및 VPN 프로필을 구성하려면 먼저 개인 정보 요구 사항을 고려합니다.  
