---
title: 온-프레미스 MDM 계획
titleSuffix: Configuration Manager
description: Configuration Manager에서 모바일 장치를 관리 하는 온-프레미스 모바일 장치 관리 계획
ms.date: 01/09/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 10a10eb7a437c606bcc6b103af8ae94161bd5d20
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035177"
---
# <a name="plan-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 계획

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)을 구현할 계획인 경우 몇 가지 주요 영역을 검토 해야 합니다.

- 지원 되는 장치 및 OS 버전
- 필수 사이트 시스템 역할
- 보안 통신
- 디바이스 등록

> [!IMPORTANT]
> 사이트 또는 모바일 장치는 Microsoft Intune에 연결 되지 않지만 조직에서이 기능을 사용 하려면 Intune 라이선스가 필요 합니다. 자세한 내용은 [Microsoft Intune 라이선스](https://docs.microsoft.com/intune/fundamentals/licenses)를 참조 하세요.

온-프레미스 MDM을 처리 하기 위해 Configuration Manager 인프라를 준비 하기 전에 다음 요구 사항을 고려 하세요.

## <a name="bkmk_devices"></a> 지원되는 디바이스  

현재 분기 Configuration Manager Windows 10을 실행 하는 장치에 대 한 온-프레미스 모바일 장치 관리의 등록을 지원 합니다. 이러한 장치 유형에는 주로 랩톱, IoT 및 Surface Hub 포함 됩니다. 특정 버전에 대 한 자세한 내용 및 목록은 [클라이언트 및 장치에 대해 지원 되는 OS 버전](/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS)을 참조 하세요.

## <a name="bkmk_roles"></a> 사이트 시스템 역할

온-프레미스 MDM에는 다음 사이트 시스템 역할 중 하나 이상이 필요 합니다.

- **등록 프록시 지점** : 등록 요청 지원

- **등록 지점** : 디바이스 등록 지원

- **디바이스 관리 지점** : 정책 배달 이 역할은 관리 지점의 변형 이지만 모바일 장치 관리를 허용 합니다.

- **배포 지점** : 콘텐츠 배달용

조직의 요구에 따라 이러한 역할을 단일 서버에 설치 하거나 서로 다른 서버에 별도로 설치할 수 있습니다.

> [!NOTE]
> 온-프레미스 MDM에 사용 되는 각 역할을 신뢰할 수 있는 장치와 통신 하기 위한 HTTPS 끝점으로 구성 해야 합니다. 자세한 내용은 [신뢰할 수 있는 필수 통신](#bkmk_trustedComs)항목을 참조하세요.

보다 일반적인 정보는 [사이트 시스템 서버 및 역할에 대 한 계획](/sccm/core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles)을 참조 하세요.

## <a name="bkmk_trustedComs"></a>신뢰할 수 있는 통신

온-프레미스 MDM을 사용 하려면 HTTPS 통신에 대 한 사이트 시스템 역할을 사용 하도록 설정 해야 합니다. 사용자의 요구에 따라 조직의 CA (인증 기관)를 사용 하 여 서버와 장치 간에 신뢰할 수 있는 연결을 설정할 수 있습니다. 공개적으로 사용 가능한 CA를 사용 하 여 신뢰할 수 있는 기관이 될 수도 있습니다. 어느 방법이 든 다음 인증서를 구성 해야 합니다.

- 필요한 사이트 시스템 역할을 호스트 하는 서버에서 IIS의 **웹 서버 인증서** 입니다. 한 서버에서 여러 사이트 시스템 역할을 호스트 하는 경우 해당 서버에 대 한 인증서가 하나만 필요 합니다. 각 역할이 별도의 서버에 있는 경우 각 서버에 별도의 인증서가 필요 합니다.

- 웹 서버 인증서를 발급 하는 CA의 **신뢰할 수 있는 루트 인증서** 입니다. 사이트 시스템 역할에 연결 해야 하는 모든 장치에이 루트 인증서를 설치 합니다.

자세한 내용은 [온-프레미스 MDM에서 신뢰할 수 있는 통신에 대 한 인증서 설정](/sccm/mdm/get-started/set-up-certificates-on-premises-mdm)을 참조 하세요.

## <a name="bkmk_enrollment"></a>장치 등록

온-프레미스 MDM에 대 한 장치 등록을 사용 하도록 설정 하려면:

- 사용자에 게 클라이언트 설정을 통해 등록할 수 있는 권한 부여

- 필요한 역할을 호스트 하는 사이트 시스템 서버와 신뢰할 수 있는 통신을 위한 장치 구성

사용자가 시작한 등록의 대 안으로 대량 등록 패키지를 설정할 수 있습니다. 이 패키지를 통해 사용자 개입 없이 장치를 등록할 수 있습니다. 패키지를 사용 하기 위해 프로 비전 하거나 OOBE 프로세스를 거치는 후에 장치에 제공 합니다.

자세한 내용은 [온-프레미스 MDM에 대 한 장치 등록 설정](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm)을 참조 하세요.

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [사이트 시스템 역할 설치](/configmgr/mdm/get-started/install-site-system-roles-for-on-premises-mdm)
