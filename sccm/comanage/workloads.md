---
title: 공동 관리 워크로드
titleSuffix: Configuration Manager
description: Configuration Manager에서 Microsoft Intune으로 전환할 수 있는 워크로드에 대해 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 11/29/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 4c90befe-9c4e-4c27-a947-625887e15052
ms.openlocfilehash: 345d0be107a2ea68cf4d7e662b43e41181031be5
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75816669"
---
# <a name="co-management-workloads"></a>공동 관리 워크로드

워크로드를 전환할 필요가 없거나 준비될 때 개별적으로 전환할 수 있습니다. Intune으로 전환하지 않은 워크로드를 포함한 다른 모든 워크로드와 공동 관리에서 지원하지 않는 Configuration Manager의 다른 모든 기능은 계속 Configuration Manager에서 관리합니다.

워크로드를 Intune으로 변경하지만, 나중에 마음을 바꾸는 경우 다시 Configuration Manager로 전환할 수 있습니다.

공동 관리에서는 다음 워크로드를 지원합니다.

- [준수 정책](#compliance-policies)  

- [Windows 업데이트 정책](#windows-update-policies)  

- [리소스 액세스 정책](#resource-access-policies)  

- [Endpoint Protection](#endpoint-protection)  

- [디바이스 구성](#device-configuration)  

- [Office 간편 실행 앱](#office-click-to-run-apps)  

- [클라이언트 앱](#client-apps)  

## <a name="compliance-policies"></a>규정 준수 정책

규정 준수 정책은 디바이스가 조건부 액세스 정책을 준수하는 것으로 간주되려면 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 디바이스를 모니터링하고 준수 문제를 수정할 수도 있습니다. Configuration Manager 버전 1910부터, 사용자 지정 구성 기준의 평가를 준수 정책 평가 규칙으로 추가할 수 있습니다. 자세한 내용은 [준수 정책 평가의 일환으로 사용자 지정 구성 기준 포함](/sccm/compliance/deploy-use/create-configuration-baselines#bkmk_CAbaselines)을 참조하세요.

Intune 기능에 대한 자세한 내용 [디바이스 준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)을 참조하세요.  

## <a name="windows-update-policies"></a>Windows 업데이트 정책

비즈니스용 Windows 업데이트 정책을 통해 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 디바이스에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다.

Intune 기능에 대한 자세한 내용은 [비즈니스용 Windows 업데이트 지연 정책 구성](https://docs.microsoft.com/intune/windows-update-for-business-configure)을 참조하세요.  

## <a name="resource-access-policies"></a>리소스 액세스 정책

리소스 액세스 정책은 디바이스에 대한 VPN, Wi-Fi, 전자 메일 및 인증서 설정을 구성합니다.

Intune 기능에 대한 자세한 내용은 [리소스 액세스 프로필 배포](https://docs.microsoft.com/intune/device-profiles)를 참조하세요.

> [!Note]  
> 리소스 액세스 워크로드는 디바이스 구성의 일부이기도 합니다. 이러한 정책은 [디바이스 구성](#device-configuration) 워크로드로 전환하는 경우 Intune에서 관리됩니다.

## <a name="endpoint-protection"></a>Endpoint Protection

<!--1357365-->

Endpoint Protection 워크로드는 다음과 같은 Windows Defender 맬웨어 방지 보호 기능 도구 모음을 포함합니다.

- Windows Defender 맬웨어 방지
- Windows Defender Application Guard  
- Windows Defender 방화벽  
- Windows Defender SmartScreen  
- Windows 암호화  
- Windows Defender Exploit Guard  
- Windows Defender Application Control  
- Windows Defender Security Center  
- Windows Defender Advanced Threat Protection(현재 Microsoft Defender Threat Protection으로 알려짐)
- Windows Information Protection  

Intune 기능에 대한 자세한 내용 [Microsoft Intune용 Endpoint Protection](https://docs.microsoft.com/intune/endpoint-protection-windows-10)을 참조하세요.

> [!Note]  
> 이 워크로드를 전환하면 Intune 정책이 덮어쓸 때까지 디바이스에서 Configuration Manager 정책이 유지됩니다. 이 동작은 전환 동안에도 디바이스에 여전히 보호 정책이 적용되도록 합니다.
>
> Endpoint Protection 워크로드는 디바이스 구성의 일부이기도 합니다. [디바이스 구성](#device-configuration) 워크로드를 전환하는 경우 동일한 동작이 적용됩니다.<!-- SCCMDocs.nl-nl issue #4 -->

## <a name="device-configuration"></a>디바이스 구성

<!--1357903-->

디바이스 구성 워크로드는 조직의 디바이스에 대해 관리하는 설정을 포함합니다. 이 워크로드를 전환하면 **리소스 액세스** 및 **Endpoint Protection** 워크로드로 이동합니다.

Intune이 디바이스 구성 기관이더라도 Configuration Manager에서 공동 관리 디바이스로 설정을 배포할 수 있습니다. 이 예외는 Intune에서는 아직 사용할 수 없지만 조직에 필요한 설정을 구성하는 데 사용할 수 있습니다. 이 예외는 [Configuration Manager 구성 기준](/sccm/compliance/deploy-use/create-configuration-baselines)에서 지정합니다. 기준을 만들 때 **공동 관리하는 클라이언트에 대해서도 항상 이 기준 적용** 옵션을 사용하도록 설정합니다. 나중에 기존 기준에 대한 속성의 **일반** 탭에서 이 옵션을 변경할 수 있습니다.  

Intune 기능에 대한 자세한 내용은 [Microsoft Intune에서 디바이스 프로필 만들기](https://docs.microsoft.com/intune/device-profile-create)를 참조하세요.  

## <a name="office-click-to-run-apps"></a>Office 간편 실행 앱

<!--1357841-->

이 워크로드는 공동 관리형 디바이스에서 Office 365 앱을 관리합니다.

- 워크로드를 이동하면 앱이 디바이스의 **회사 포털**에 표시됩니다.  

- 디바이스를 다시 시작하지 않을 경우 Office 업데이트가 클라이언트에 표시되는 데 약 24시간이 걸릴 수 있습니다.  

- **디바이스에서 Intune으로 Office 365 애플리케이션 관리**라는 새 글로벌 조건이 있습니다. 이 조건은 기본적으로 새 Office 365 애플리케이션에 대한 요구 사항으로 추가됩니다. 이 워크로드를 전환하는 경우 공동 관리되는 클라이언트는 애플리케이션의 요구 사항을 충족하지 못합니다. 따라서 Configuration Manager를 통해 배포된 Office 365를 설치하지 않습니다.  

Intune 기능에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](https://docs.microsoft.com/intune/apps-add-office365)을 참조하세요.

## <a name="client-apps"></a>클라이언트 앱

<!--1357892-->

공동 관리형 Windows 10 디바이스에서 Intune을 사용하여 클라이언트 앱 및 PowerShell 스크립트를 관리할 수 있습니다. 이 워크로드를 전환하면 Intune에서 배포된 사용 가능한 모든 앱을 회사 포털에서 사용할 수 있습니다. Configuration Manager에서 배포하는 앱은 소프트웨어 센터에서 사용할 수 있습니다.

Intune 기능에 대한 자세한 내용은 [Microsoft Intune 앱 관리란?](https://docs.microsoft.com/intune/app-management)을 참조하세요.

> [!Note]  
> 클라이언트 앱 워크로드는 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요. 이 기능은 **공동 관리 디바이스용 모바일 앱** 기능으로 기능 목록에 표시될 수 있습니다.<!-- 5849669 -->

버전 1910부터, Configuration Manager 배포 지점에서 Microsoft Connected Cache를 사용하도록 설정하면 배포 지점이 공동 관리형 클라이언트에 Microsoft Intune Win32 앱을 제공할 수 있습니다. 자세한 내용은 [Configuration Manager의 Microsoft Connected Cache](/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune)를 참조하세요.

## <a name="diagram-for-app-workloads"></a>앱 워크로드에 대한 다이어그램

![공동 관리 앱 워크로드 다이어그램](media/co-management-apps.svg)

[전체 화면 크기로 다이어그램 보기](media/co-management-apps.svg)

## <a name="next-steps"></a>다음 단계

[워크로드를 전환하는 방법](/sccm/comanage/how-to-switch-workloads)  
