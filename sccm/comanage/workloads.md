---
title: 공동 관리 워크 로드
titleSuffix: Configuration Manager
description: Configuration Manager에서 Microsoft Intune로 전환할 수 있는 워크 로드에 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 01/14/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 4c90befe-9c4e-4c27-a947-625887e15052
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3723595091e57a7ad2267a4da325e7c134c7bf1
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755268"
---
# <a name="co-management-workloads"></a>공동 관리 워크 로드

워크 로드를 전환 하지 않아도 됩니다. 또는 준비 된 경우 개별적으로 수행할 수 있습니다. Configuration Manager가 계속 모든 다른 워크 로드를 Intune로 전환 하지 않습니다 하 고 다른 모든 기능은 Configuration Manager 공동 관리를 지원 하지 않습니다는 해당 워크 로드를 포함 하 여 관리.

공동 관리는 다음 워크 로드를 지원합니다.

- [준수 정책](#compliance-policies)  

- [Windows 업데이트 정책](#windows-update-policies)  

- [리소스 액세스 정책](#resource-access-policies)  

- [Endpoint Protection](#endpoint-protection)  

- [장치 구성](#device-configuration)  

- [Office 간편 실행 앱](#office-click-to-run-apps)  

- [클라이언트 앱](#client-apps)  



## <a name="compliance-policies"></a>규정 준수 정책 

규정 준수 정책은 디바이스가 조건부 액세스 정책을 준수하는 것으로 간주되려면 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 디바이스를 모니터링하고 준수 문제를 수정할 수도 있습니다. 

Intune 기능에 대 한 자세한 내용은 참조 하세요. [장치 준수 정책](https://docs.microsoft.com/intune/device-compliance-get-started)합니다.  



## <a name="windows-update-policies"></a>Windows 업데이트 정책

비즈니스용 Windows 업데이트 정책을 통해 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 디바이스에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. 

Intune 기능에 대 한 자세한 내용은 참조 하세요. [Windows 업데이트 지연 정책 비즈니스에 대 한 구성](https://docs.microsoft.com/intune/windows-update-for-business-configure)합니다.  



## <a name="resource-access-policies"></a>리소스 액세스 정책

리소스 액세스 정책은 디바이스에 대한 VPN, Wi-Fi, 전자 메일 및 인증서 설정을 구성합니다. 

Intune 기능에 대 한 자세한 내용은 참조 하세요. [리소스 액세스 프로필 배포](https://docs.microsoft.com/intune/device-profiles)합니다.



## <a name="endpoint-protection"></a>Endpoint Protection
<!--1357365-->

Configuration Manager 1802부터 Endpoint Protection 워크 로드 Windows Defender 맬웨어 방지 보호 기능 집합을 포함 합니다. 

- Windows Defender Application Guard  
- Windows Defender 방화벽  
- Windows Defender SmartScreen  
- Windows 암호화  
- Windows Defender Exploit Guard  
- Windows Defender Application Control  
- Windows Defender Security Center  
- Windows Defender Advanced Threat Protection  
- Windows Information Protection  

Intune 기능에 대 한 자세한 내용은 참조 하세요. [Microsoft Intune 용 Endpoint Protection](https://docs.microsoft.com/intune/endpoint-protection-windows-10)합니다.



## <a name="device-configuration"></a>디바이스 구성
<!--1357903-->

Configuration Manager 1806부터 장치 구성 작업 조직에서 장치를 관리 하는 설정이 포함 됩니다. 이동이 워크 로드를 전환 합니다 **리소스 액세스** 하 고 **Endpoint Protection** 워크 로드.

Intune이 디바이스 구성 기관이더라도 Configuration Manager에서 공동 관리 디바이스로 설정을 배포할 수 있습니다. 조직에 필요 하지만 Intune에서 사용할 수 있는 아직는 설정을 구성 하려면이 예외를 사용할 수 있습니다. 이 예외는 [Configuration Manager 구성 기준](/sccm/compliance/deploy-use/create-configuration-baselines)에서 지정합니다. 옵션을 사용 하도록 설정 **공동 관리 되는 클라이언트에 대해서도이 초기 계획을 항상 적용** 기준선을 만들 때. 나중에 변경할 수 있습니다 합니다 **일반** 는 기존 기준선의 속성을 탭 합니다.  

Intune 기능에 대 한 자세한 내용은 참조 하세요. [Microsoft Intune에서 장치 프로필을 만드는](https://docs.microsoft.com/intune/device-profile-create)합니다.  



## <a name="office-click-to-run-apps"></a>Office 간편 실행 앱
<!--1357841-->

Configuration Manager 1806부터이 워크 로드는 공동 관리 장치에 Office 365 앱을 관리 합니다. 

- 워크로드를 이동하면 앱이 디바이스의 **회사 포털**에 표시됩니다.  

- 디바이스를 다시 시작하지 않을 경우 Office 업데이트가 클라이언트에 표시되는 데 약 24시간이 걸릴 수 있습니다.  

- **디바이스에서 Intune으로 Office 365 애플리케이션 관리**라는 새 글로벌 조건이 있습니다. 이 조건은 기본적으로 새 Office 365 애플리케이션에 대한 요구 사항으로 추가됩니다. 이 워크로드를 전환하는 경우 공동 관리되는 클라이언트는 애플리케이션의 요구 사항을 충족하지 못합니다. 따라서 Configuration Manager를 통해 배포된 Office 365를 설치하지 않습니다.  

Intune 기능에 대 한 자세한 내용은 참조 하세요. [Microsoft Intune을 사용 하 여 Windows 10 장치에 Office 365 할당 앱](https://docs.microsoft.com/intune/apps-add-office365)합니다. 



## <a name="client-apps"></a>클라이언트 앱
<!--1357892-->

Configuration Manager 버전 1806부터 Windows 10 장치의 공동 관리 하는 클라이언트 앱을 관리 하려면 Intune을 사용 합니다. 이 워크로드를 전환하면 Intune에서 배포된 사용 가능한 모든 앱을 회사 포털에서 사용할 수 있습니다. Configuration Manager에서 배포하는 앱은 소프트웨어 센터에서 사용할 수 있습니다.

Intune 기능에 대 한 자세한 내용은 참조 하세요. [Microsoft Intune 앱 관리란?](https://docs.microsoft.com/intune/app-management)합니다. 

> [!Note]  
> 클라이언트 앱 워크 로드에는 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  



## <a name="next-steps"></a>다음 단계

[워크 로드를 전환 하는 방법](/sccm/comanage/how-to-switch-workloads)  


