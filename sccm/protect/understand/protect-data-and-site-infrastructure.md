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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86eed6ef79a098bb53237890e410747d78788acd
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74660821"
---
# <a name="protect-data-and-site-infrastructure"></a>데이터 및 사이트 인프라 보호

*적용 대상: Configuration Manager (현재 분기)*

사용자가 조직의 리소스에 안전 하 게 액세스 하도록 하려고 합니다. 노출 또는 악의적인 공격 으로부터 인프라와 데이터를 모두 보호 합니다. Configuration Manager를 사용 하 여 액세스를 사용 하도록 설정 하 고 조직의 리소스를 보호할 수 있습니다.  

- [Endpoint Protection](/configmgr/protect/deploy-use/endpoint-protection) 를 사용 하면 클라이언트 컴퓨터에 대해 다음과 같은 Microsoft Defender 정책을 관리할 수 있습니다.

  - Microsoft Defender 맬웨어 방지 프로그램
  - Microsoft Defender 방화벽
  - Microsoft Defender Advanced Threat Protection
  - Microsoft Defender Exploit Guard
  - Microsoft Defender Application Guard
  - Microsoft Defender 애플리케이션 제어

  > [!TIP]
  > Microsoft Endpoint Manager 클라우드 서비스를 사용 하 여 공동 관리 되는 Windows 10 장치에서 endpoint protection을 관리 하려면 [ **Endpoint Protection** 워크 로드](/configmgr/comanage/workloads#endpoint-protection) 를 Intune으로 전환 합니다. 자세한 내용은 [Microsoft Intune Endpoint protection](https://docs.microsoft.com/intune/endpoint-protection-windows-10)을 참조 하세요.

- BitLocker 드라이브 암호화 (MANAGE-BDE)를 사용 하 여 온-프레미스 Windows 클라이언트에 저장 된 데이터를 보호 합니다. Configuration Manager은 MBAM (Microsoft BitLocker Administration and Monitoring)의 사용을 대체할 수 있는 전체 BitLocker 수명 주기 관리를 제공 합니다. 자세한 내용은 [BitLocker 관리 계획](/configmgr/protect/plan-design/bitlocker-management)을 참조 하세요.

- 기존 암호 대신 비즈니스용 Windows Hello를 사용 하 여 Windows 10 장치에서 대체 로그인 방법을 사용 하도록 설정 합니다. 자세한 내용은 [비즈니스용 Windows Hello 설정](/configmgr/protect/deploy-use/windows-hello-for-business-settings)을 참조하세요.

- VPN 프로필로 VPN 연결을 사용하도록 설정하면 사용자가 리소스에 손쉽게 연결할 수 있습니다. 자세한 내용은 [VPN 프로필](/configmgr/protect/deploy-use/vpn-profiles)을 참조하세요.  

- Wi-fi 프로필은 조직에서 장치에 대 한 무선 네트워크 설정을 관리 하는 데 도움이 되는 도구 및 리소스 집합을 제공 합니다. 이러한 설정을 배포하여, 최종 사용자가 무선 네트워크에 쉽게 연결하도록 지원할 수 있습니다. 자세한 내용은 [Wi-Fi 프로필](/configmgr/protect/deploy-use/create-wifi-profiles)을 참조하세요.  

- 사용자가 리소스에 연결 하는 데 필요한 인증서를 사용 하 여 장치를 프로 비전 합니다. 자세한 내용은 [인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)을 참조하세요.  

- 메일 프로필은 디바이스에서 메일 설정을 만들고, 배포하고, 모니터링하는 데 유용한 도구 및 리소스 세트를 제공합니다. 사용자가 필요한 설정 없이 자신의 개인 장치에서 메일에 액세스할 수 있습니다. 자세한 내용은 [메일 프로필](/configmgr/protect/deploy-use/introduction-to-email-profiles)을 참조하세요.  
