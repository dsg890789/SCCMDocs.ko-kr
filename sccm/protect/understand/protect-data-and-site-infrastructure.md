---
title: 데이터 및 사이트 인프라 보호
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 노출이나 악의적인 공격으로부터 조직의 리소스를 보호하는 방법에 대해 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 2117f786-d521-4790-9e8d-ec096c63c9d7
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: fc680486454957c83936525e7403a975d8d3f94a
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035077"
---
# <a name="protect-data-and-site-infrastructure"></a>데이터 및 사이트 인프라 보호

*적용 대상: Configuration Manager(현재 분기)*

사용자가 조직의 리소스에 안전하게 액세스하도록 하려고 합니다. 인프라와 데이터를 노출 또는 악의적인 공격으로부터 보호합니다. Configuration Manager를 사용하여 액세스를 사용하도록 설정하고 조직의 리소스를 보호할 수 있습니다.  

- [Endpoint Protection](/configmgr/protect/deploy-use/endpoint-protection)을 사용하면 클라이언트 컴퓨터에 대해 다음과 같은 Microsoft Defender 정책을 관리할 수 있습니다.

  - Microsoft Defender 맬웨어 방지 프로그램
  - Microsoft Defender 방화벽
  - Microsoft Defender Advanced Threat Protection
  - Microsoft Defender Exploit Guard
  - Microsoft Defender Application Guard
  - Microsoft Defender 애플리케이션 제어

  > [!TIP]
  > Microsoft 엔드포인트 관리자 클라우드 서비스를 사용하여 공동 관리되는 Windows 10 디바이스에서 Endpoint Protection을 관리하려면 [**Endpoint Protection** 워크로드](/configmgr/comanage/workloads#endpoint-protection)를 Intune으로 전환합니다. 자세한 내용은 [Microsoft Intune Endpoint Protection](https://docs.microsoft.com/intune/endpoint-protection-windows-10)을 참조하세요.

- BitLocker 드라이브 암호화(BDE)를 사용하여 온-프레미스 Windows 클라이언트에 저장된 데이터를 보호합니다. Configuration Manager은 MBAM(Microsoft BitLocker Administration and Monitoring)의 사용을 대체할 수 있는 전체 BitLocker 수명 주기 관리를 제공합니다. 자세한 내용은 [BitLocker 관리 계획](/configmgr/protect/plan-design/bitlocker-management)을 참조하세요.

- 기존 암호 대신 비즈니스용 Windows Hello를 사용하여 Windows 10 디바이스에서 대체 로그인 방법을 사용하도록 설정합니다. 자세한 내용은 [비즈니스용 Windows Hello 설정](/configmgr/protect/deploy-use/windows-hello-for-business-settings)을 참조하세요.

- VPN 프로필로 VPN 연결을 사용하도록 설정하면 사용자가 리소스에 손쉽게 연결할 수 있습니다. 자세한 내용은 [VPN 프로필](/configmgr/protect/deploy-use/vpn-profiles)을 참조하세요.  

- Wi-Fi 프로필은 조직에서 디바이스에 대한 무선 네트워크 설정을 관리하는 데 유용한 도구 및 리소스 집합을 제공합니다. 이러한 설정을 배포하여, 최종 사용자가 무선 네트워크에 쉽게 연결하도록 지원할 수 있습니다. 자세한 내용은 [Wi-Fi 프로필](/configmgr/protect/deploy-use/create-wifi-profiles)을 참조하세요.  

- 사용자가 리소스에 연결하는 데 필요한 인증서를 사용하여 디바이스를 프로비저닝합니다. 자세한 내용은 [인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)을 참조하세요.  
