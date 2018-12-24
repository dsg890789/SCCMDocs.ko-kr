---
title: 데이터 및 사이트 인프라 보호
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 노출이나 악의적인 공격으로부터 조직의 리소스를 보호하는 방법에 대해 알아봅니다.
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 2117f786-d521-4790-9e8d-ec096c63c9d7
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: e76a16fab84f5ccfcd71af4bc80913e31acdadd9
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347555"
---
# <a name="protect-data-and-site-infrastructure-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 데이터 및 사이트 인프라 보호

*적용 대상: System Center Configuration Manager(현재 분기)*


인프라 및 데이터를 노출이나 악의적인 공격으로부터 보호하기 위해 사용자가 조직의 리소스에 안전하게 액세스할 수 있도록 설정할 수 있습니다. 이 항목의 정보는 System Center Configuration Manager(ConfigMgr 또는 SCCM이라고도 함)를 사용하여 해당 액세스를 허용하는 방법과 조직의 리소스를 보호하는 방법을 설명합니다.  

-   VPN 프로필로 VPN 연결을 사용하도록 설정하면 사용자가 회사 리소스에 손쉽게 연결할 수 있습니다. [System Center Configuration Manager에서 VPN 프로필](../deploy-use/vpn-profiles.md)을 참조하세요.  

-   Wi-Fi 프로필은 조직에서 디바이스에 대한 무선 네트워크 설정을 만들고 배포하고 모니터링하는 데 유용한 도구 및 리소스 집합을 제공합니다. 이러한 설정을 배포하여, 최종 사용자가 회사 무선 네트워크에 쉽게 연결하도록 지원합니다. [System Center Configuration Manager에서 Wi-Fi 프로필](/sccm/protect/deploy-use/create-wifi-profiles)을 참조하세요.  

-   [System Center Configuration Manager의 인증서 프로필](../deploy-use/introduction-to-certificate-profiles.md)에서는 회사 리소스에 연결하는 데 필요한 인증서로 사용자의 장치를 프로비전하는 방법을 설명합니다.  

-   [System Center Endpoint Protection](../deploy-use/endpoint-protection.md)에서 클라이언트 컴퓨터에 대한 맬웨어 방지 정책 및 Windows 방화벽 보안을 관리할 수 있습니다.  

-   [System Center Configuration Manager에서 서비스 액세스 관리](../deploy-use/manage-access-to-services.md)에 설명된 대로 조건부 액세스를 사용하여 Microsoft Intune에 등록된 장치의 메일과 기타 서비스를 보호할 수 있습니다.  

-   메일 프로필은 디바이스에서 메일 설정을 만들고, 배포하고, 모니터링하는 데 유용한 도구 및 리소스 집합을 제공합니다. 이를 통해 사용자는 별도의 설정 없이 자신의 개인 디바이스에서 회사 전자 메일에 액세스할 수 있습니다. [System Center Configuration Manager에서 메일 프로필](../deploy-use/introduction-to-email-profiles.md)을 참조하세요.  

-   Configuration Manager에서는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대신하는 대체 로그인 방법인 비즈니스용 Windows Hello(이전의 Microsoft Passport for Work)와 통합할 수 있습니다. [System Center Configuration Manager의 비즈니스용 Windows Hello 설정](../deploy-use/windows-hello-for-business-settings.md)을 참조하세요.  
