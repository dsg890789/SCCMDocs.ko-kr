---
title: '준비 단계 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 사용하여 디바이스 관리를 준비합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b97d30e1d5cc5cdca0cd69e260910c7981d1cec
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56134217"
---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위한 준비 단계

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 온\-프레미스 모바일 디바이스 관리를 사용하여 디바이스를 관리하려면 필수 사이트 시스템 역할(등록 프록시 지점, 등록 지점, 디바이스 관리 지점, 배포 지점)이 신뢰할 수 있는 채널을 통해 관리할 모바일 디바이스와 통신할 수 있도록 Configuration Manager 인프라를 설정해야 합니다.  

 다음은 Configuration Manager 시스템을 온\-프레미스 모바일 디바이스 관리용으로 준비하는 데 필요한 개략적인 작업입니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위해 Microsoft Intune 구독 설정](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     이 작업에서는 Microsoft Intune에 대해 등록한 다음 Configuration Manager 콘솔을 통해 Configuration Manager에 구독을 추가합니다. 이 단계는 라이선싱용으로만 필요합니다. Intune은 디바이스를 관리하거나 관리 정보를 저장하는 데 사용되지 않습니다. 온-프레미스 Configuration Manager 인프라를 사용하는 조직의 엔터프라이즈에서 디바이스에 대한 조정 및 관리 업무가 수행됩니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위한 사이트 시스템 역할 설치](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     이 작업에서는 온-프레미스 Configuration Manager 인프라를 사용하여 디바이스를 관리하는 데 필요한 사이트 시스템 역할을 설치 및 구성합니다. 온\-프레미스 모바일 디바이스 관리에는 최소한 등록 프록시 지점, 등록 지점, 디바이스 관리 지점, 배포 지점 사이트 시스템 역할이 필요합니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위해 신뢰할 수 있는 통신에 대한 인증서 설정](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     이 작업에서는 온-프레미스 Configuration Manager 인프라를 구성하여 필수 사이트 시스템 역할을 호스트하는 서버와 관리되는 디바이스 간에 신뢰할 수 있는 통신(HTTPS)을 허용합니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위한 디바이스 등록 설정](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     이 작업에서는 사용자에게 컴퓨터 및 디바이스를 등록할 수 있는 권한을 부여하고, 디바이스(일반적으로 도메인에 가입되지 않은 디바이스)에 신뢰할 수 있는 루트 인증서를 설치하여 사이트 시스템 서버에 대한 HTTPS 연결을 허용합니다.  
