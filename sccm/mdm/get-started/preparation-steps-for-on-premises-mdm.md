---
title: 온-프레미스 MDM 준비
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 모바일 장치 관리를 사용 하 여 장치 관리 준비
ms.date: 03/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: fad5ce96b84b5a6edfafdead64cff0223009ebf8
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62288646"
---
# <a name="preparation-steps-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 준비 단계

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 장치를 관리 하려면 먼저 필요한 인프라를 설정 합니다. 필요한 사이트 시스템 역할은 모바일 장치와 신뢰할 수 있는 채널을 통해 통신 해야 합니다. 이러한 역할에는 등록 프록시 지점, 등록 지점, 장치 관리 지점, 배포 지점 등이 포함 됩니다.

온-프레미스 MDM에 대 한 Configuration Manager를 준비 하려면 다음과 같은 개략적인 작업이 필요 합니다.  

- [온-프레미스 MDM에 대 한 Microsoft Intune 구독 설정](/sccm/mdm/get-started/set-up-intune-subscription-on-premises-mdm)  

    Microsoft Intune에 등록 한 다음 Configuration Manager 콘솔을 통해 Configuration Manager에 구독을 추가 합니다. 이 단계는 라이선싱용으로만 필요합니다. Intune은 장치를 관리 하거나 관리 정보를 저장 하는 데 사용 되지 않습니다. 온-프레미스 Configuration Manager 인프라를 사용하는 조직의 엔터프라이즈에서 디바이스에 대한 조정 및 관리 업무가 수행됩니다.  

    > [!Note]  
    > 버전 1810부터는 Intune 연결이 새로운 온-프레미스 MDM 배포에 더 이상 필요하지 않습니다.<!--3607730, fka 1359124--> 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 현재 기존 온-프레미스 MDM 배포에서 Intune 연결을 제거할 수 없습니다. 자세한 내용은 [Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)을 참조하세요.  

- [온-프레미스 MDM에 대 한 사이트 시스템 역할 설치](/sccm/mdm/get-started/install-site-system-roles-for-on-premises-mdm)  

    온-프레미스 Configuration Manager 인프라를 사용 하 여 장치를 관리 하는 데 필요한 사이트 시스템을 설치 하 고 구성 합니다. 이 기능에는 최소한 등록 프록시 지점, 등록 지점, 장치 관리 지점 및 배포 지점 역할이 필요 합니다.  

- [온-프레미스 MDM에 대 한 신뢰할 수 있는 통신에 대 한 인증서 설정](/sccm/mdm/get-started/set-up-certificates-on-premises-mdm)  

    필수 사이트 시스템 역할을 호스트 하는 서버와 관리 되는 장치 간에 신뢰할 수 있는 통신 (HTTPS)을 허용 하도록 온-프레미스 Configuration Manager 인프라를 구성 합니다.  

- [온-프레미스 MDM에 대 한 장치 등록 설정](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm)  

    사용자에 게 컴퓨터 및 장치를 등록할 수 있는 권한을 부여 합니다. 장치에 신뢰할 수 있는 루트 인증서를 설치 하 여 사이트 시스템 서버에 대 한 HTTPS 연결을 허용 합니다. 이러한 장치는 일반적으로 도메인에 가입 되지 않습니다.  

