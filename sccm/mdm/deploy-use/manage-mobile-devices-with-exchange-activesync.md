---
title: Exchange를 사용한 디바이스 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 Exchange Server 커넥터를 사용 하 여 모바일 장치를 관리 합니다.
ms.date: 12/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: aba688d9-fd5b-4c42-8cb4-f7e1b161ef50
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 426bf16d984f364020362680e3eb7539c7f80ef3
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035259"
---
# <a name="device-management-with-exchange-and-configuration-manager"></a>Exchange 및 Configuration Manager를 사용 하 여 장치 관리

*적용 대상: Configuration Manager (현재 분기)*

ActiveSync 프로토콜을 통해 Exchange Server에 연결 하는 모바일 장치를 사용 하는 경우 Configuration Manager에서 Exchange Server 커넥터를 사용 하 여 이러한 장치를 관리할 수 있습니다. 커넥터는 온-프레미스 Exchange Server 또는 Exchange Online과 함께 작동 합니다. Configuration Manager 콘솔을 사용 하 여 Exchange 모바일 장치 관리 기능을 구성 합니다. 예를 들어 여러 Exchange 서버에 대 한 원격 장치 초기화 및 설정 제어가 있습니다.

![Configuration Manager를 사용 하는 Exchange Server 커넥터의 논리 다이어그램](media/configmgr-with-exchange.png)  

이 커넥터를 사용 하 여 모바일 장치를 관리 하는 경우 Configuration Manager 클라이언트를 설치 하거나 MDM을 통해 장치를 등록 하지 않습니다. Exchange Server의 관리 기능은 이러한 다른 옵션과 비교 하 여 제한 됩니다. 예를 들어 소프트웨어를 설치할 수 없거나 구성 항목을 사용 하 여 이러한 장치를 구성할 수 없습니다. 자세한 내용은 [Configuration Manager에 대 한 장치 관리 솔루션 선택](/configmgr/core/plan-design/choose-a-device-management-solution)을 참조 하세요.  

## <a name="policies"></a>정책

커넥터를 사용 하는 경우 Configuration Manager 모바일 장치에서 설정을 구성 합니다. 장치는 기본 Exchange ActiveSync 사서함 정책을 사용 하지 않습니다. 다음 그룹에서 사용 하려는 설정을 정의 합니다.

- **일반**
- **암호**
- **전자 메일 관리**
- **Security**
- **애플리케이션**

예를 들어 **암호** 그룹에서 다음 설정을 구성할 수 있습니다.

- 모바일 장치에 암호가 필요한 지 여부
- 최소 암호 길이
- 암호 복잡도
- 암호 복구 허용 여부

그룹에 하나 이상의 설정을 구성하면 Configuration Manager가 모바일 디바이스에 대한 그룹의 모든 설정을 관리합니다. 그룹에서 설정을 구성 하지 않으면 Exchange가 모바일 장치에 대 한 설정을 계속 관리 합니다. Exchange 서버에서 구성 하 고 사용자에 게 할당 하는 모든 Exchange ActiveSync 사서함 정책은 여전히 적용 됩니다.

## <a name="access-rules-and-remote-actions"></a>액세스 규칙 및 원격 작업

Exchange 액세스 규칙을 관리 하도록 Exchange Server 커넥터를 구성할 수도 있습니다. 이러한 액세스 규칙에는 모바일 장치 허용, 차단 또는 격리가 포함 됩니다. Configuration Manager 콘솔을 사용 하 여 원격으로 모바일 장치를 초기화할 수 있으며, 사용자는 응용 프로그램 카탈로그를 사용 하 여 모바일 장치를 원격으로 초기화할 수 있습니다.

사용자의 모바일 장치를 관리할 때 응용 프로그램 카탈로그에 자동으로 표시 되며 Exchange 서버가 온-프레미스입니다. Exchange Online을 사용할 때 응용 프로그램 카탈로그에 표시 되는 모바일 장치의 경우 사용자 장치 선호도를 수동으로 구성 합니다. 자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/configmgr/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.

> [!TIP]  
> 모바일 장치가 다른 사용자에 게 전송 될 때 새 소유자가 장치에서 자신의 Exchange 계정을 구성 하기 전에 Configuration Manager 콘솔에서 모바일 장치를 삭제 합니다.

## <a name="prerequisites"></a>전제 조건

> [!IMPORTANT]  
> 이 커넥터를 설치 하기 전에 Configuration Manager에서 Exchange의 버전을 지원 하는지 확인 합니다. 자세한 내용은 [지원 되는 구성-Exchange Server 커넥터](/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ExSrvConOS)를 참조 하세요.  

### <a name="permissions-to-configure-the-connector"></a>커넥터를 구성할 수 있는 권한

Configuration Manager에서 Exchange Server 커넥터를 구성 하려면 다음 보안 권한이 필요 합니다.

- Exchange Server 커넥터를 추가, 수정 및 삭제: **사이트** 개체에 대한 **수정** 권한이 필요합니다.  

- 모바일 디바이스 설정 구성: **사이트** 개체에 대한 **ModifyConnectorPolicy** 권한이 필요합니다.  

예를 들어 **전체 관리자** 기본 제공 역할에는 필요한 권한이 포함 됩니다.  

### <a name="permissions-to-manage-mobile-devices"></a>모바일 장치를 관리할 수 있는 권한

모바일 장치를 관리 하려면 다음 보안 권한이 필요 합니다.  

- 모바일 디바이스 초기화: **컬렉션** 개체에 대한 **리소스 삭제** 권한이 필요합니다.  

- 초기화 명령 취소: **컬렉션** 개체에 대한 **리소스 수정** 권한이 필요합니다.  

- 모바일 디바이스 허용 및 차단: **컬렉션** 개체에 대한 **리소스 수정** .  

예를 들어, **운영 관리자** 기본 제공 역할에는 이러한 필요한 권한이 포함 됩니다.

자세한 내용은 [역할 기반 관리 구성](/configmgr/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Exchange connector 설치 및 구성](/configmgr/mdm/deploy-use/install-configure-exchange-connector)
