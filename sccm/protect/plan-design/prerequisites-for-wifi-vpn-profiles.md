---
title: Wi-Fi 및 VPN 프로필 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 인증서 프로필, Wi-Fi 프로필 및 VPN 프로필을 관리하는 데 필요한 보안 권한에 대해 알아봅니다.
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: d2dacb2d-ab3b-42a2-8dc8-94da31f993c2
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 894717df4b5acb7142aa7d171a8b8b63a28f8dc0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347385"
---
# <a name="prerequisites-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Wi-Fi 및 VPN 프로필에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Wi-Fi 및 VPN 프로필에는 제품 내 종속성만 있습니다.  

 회사 리소스 액세스 설정(예: 인증서 프로필, Wi-Fi 프로필 및 VPN 프로필)을 관리하려면 다음과 같은 보안 권한이 있어야 합니다.  

-   Wi-Fi 프로필에 대한 경고 및 보고서를 보고 관리하려면: **경고** 개체에 대한 **만들기**, **삭제**, **수정**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.  

-   인증서 프로필을 만들고 관리하려면: **인증서 프로필**개체에 대한 **작성자 정책**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.  

-   Wi-Fi, 인증서 및 VPN 프로필 배포를 관리하려면: **컬렉션**개체에 대한 **구성 정책 배포**, **클라이언트 상태 알림 수정**, **읽기** 및 **리소스 읽기** 권한이 필요합니다.  

-   모든 구성 정책을 관리하려면: **구성 정책**개체에 대한 **만들기**, **삭제**, **수정**, **읽기** 및 **보안 범위 설정** 권한이 필요합니다.  

-   Wi-Fi 및 VPN 프로필과 관련된 쿼리를 실행하려면: **쿼리** 개체에 대한 **읽기** 권한이 필요합니다.  

-   System Center Configuration Manager 콘솔에서 Wi-Fi 및 VPN 프로필 정보를 보려면: **사이트** 개체에 대한 **읽기** 권한이 필요합니다.  

-   Wi-Fi 및 VPN 프로필에 대한 상태 메시지를 보려면: **상태 메시지** 개체에 대한 **읽기** 권한이 필요합니다.  

-   신뢰할 수 있는 CA 인증서 프로필을 만들고 수정하려면: **신뢰할 수 있는 CA 인증서 프로필**개체에 대한 **작성자 정책**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.  

-   VPN 프로필을 만들고 관리하려면: **VPN 프로필**개체에 대한 **작성자 정책**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.  

-   Wi-Fi 프로필을 만들고 관리하려면: **Wi-Fi 프로필**개체에 대한 **작성자 정책**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.  

 **회사 리소스 액세스 관리자** 보안 역할에는 System Center Configuration Manager에서 Wi-Fi 프로필을 관리하는 데 필요한 이와 같은 권한이 포함됩니다. 자세한 내용은 [Configure security in System Center Configuration Manager](../../core/plan-design/security/configure-security.md)항목을 참조하세요.
