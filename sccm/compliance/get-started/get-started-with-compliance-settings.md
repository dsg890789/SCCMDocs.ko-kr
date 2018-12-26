---
title: 준수 설정 시작
titleSuffix: Configuration Manager
description: 핵심 개념 및 준수 설정의 작동 방법에 대해 알아보기
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ec350bdb6b3b421d95bf13eafc562919bccc3c38
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32335612"
---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 준수 설정 시작

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 준수 설정을 만들기 전에 먼저 핵심 개념에 대해 알아보고 작동 방식을 이해합니다.  



## <a name="how-compliance-settings-work"></a>준수 설정의 작동 방식  
 준수 설정을 통해 조직에서 클라이언트의 구성과 준수를 관리할 수 있습니다.  

 구성 항목은 다음 두 가지 주요 범주로 나뉩니다.  

-   **Configuration Manager 클라이언트를 사용하여 관리되는 장치 설정** - 일반적으로 장치를 관리할 수 있도록 하는 Configuration Manager 클라이언트 소프트웨어가 설치된 장치입니다.  

-   **Configuration Manager 클라이언트 없이 관리되는 장치 설정** - 일반적으로 Microsoft Intune 또는 Configuration Manager 온-프레미스 장치 관리로 관리되는 장치입니다.  



## <a name="what-devices-are-supported"></a>지원되는 디바이스  

| 디바이스 유형 | 추가 정보 |  
|------------|----------------------|  
| Configuration Manager 클라이언트를 사용하여 Windows PC 관리 | 사용자 지정 구성 항목을 만들어 레지스트리 키, 파일 및 Active Directory 특성과 같은 개체를 평가합니다.<br /><br /> Windows 10 구성 항목 유형을 사용하는 경우 미리 정의된 목록에서 설정을 선택합니다. |  
| Windows PC(Microsoft Intune에 등록) | 미리 정의된 목록에서 설정을 선택합니다. |  
| iOS 디바이스(Microsoft Intune에 등록) | 미리 정의된 목록에서 설정을 선택합니다. |  
| Android 디바이스(Microsoft Intune에 등록) | 미리 정의된 목록에서 설정을 선택합니다. |  
| Windows Phone 디바이스(Microsoft Intune에 등록) | 미리 정의된 목록에서 설정을 선택합니다. |  
| Mac 컴퓨터(Configuration Manager 클라이언트 포함) | 사용자 지정 구성 항목을 만들어 macOS 기본 설정과 같은 개체 및 스크립트에서 반환되는 결과를 평가합니다. |  
| Mac 컴퓨터(Microsoft Intune에 등록) | 미리 정의된 목록에서 설정을 선택합니다. |  



## <a name="what-is-a-configuration-item"></a>구성 항목 정의  
 구성 항목은 특정 정보를 저장하는 컨테이너입니다. 구성하는 정보는 구성 항목 유형에 따라 달라집니다. 구성 항목은 다음 정보를 포함할 수 있습니다.

-   **검색 방법 정보**는 응용 프로그램 설정을 포함하는 Windows 구성 항목에만 적용됩니다. 애플리케이션이 설치되어 있는지 여부를 검색합니다. 이 검색은 애플리케이션에 대한 Windows 설치 관리자 파일 또는 사용자 지정 스크립트를 사용합니다.  

-   **설정**은 클라이언트 장치에서 준수를 평가하는 비즈니스 또는 기술 조건을 나타냅니다. 새 설정을 구성하거나 참조 컴퓨터에서 기존 설정을 찾습니다.  

-   **준수 규칙**은 구성 항목 설정의 준수를 정의하는 조건을 지정합니다. 클라이언트가 준수에 대한 설정을 평가하려면 하나 이상의 준수 규칙이 있어야 합니다. 일부 설정은 비호환 값을 재구성합니다. 새 규칙을 만들거나 모든 구성 항목에서 기존 설정을 검색하고 규칙을 선택합니다.  

-   **지원되는 플랫폼**은 클라이언트가 구성 항목의 준수를 평가하도록 정의하는 장치 플랫폼입니다. 지원되는 플랫폼 목록에 없는 디바이스에 구성 항목을 배포하는 경우 준수를 평가하지 않습니다.  



## <a name="what-is-a-configuration-baseline"></a>구성 기준 정의  
 평가할 구성 항목을 포함하는 구성 기준을 정의합니다. 또한 필요한 준수 수준을 설명하는 설정 및 규칙을 포함합니다. Configuration Manager 구성 팩에서 이 구성 데이터를 가져옵니다. Microsoft 및 기타 공급 업체는 이러한 구성 팩을 정의합니다. 또는 새 구성 항목 및 구성 기준을 만듭니다.  

 구성 기준을 정의한 후 사용자 및 디바이스 컬렉션에 배포합니다. 그런 다음, 클라이언트는 일정에 따라 준수에 대한 기준 설정을 평가합니다. 디바이스에 둘 이상의 구성 기준을 배포할 수 있습니다. 이 세분성은 준수의 효과적인 제어를 제공합니다. 

 클라이언트 디바이스는 배포된 각 구성 기준에 대해 준수를 평가하고 상태 메시지 및 상황 메시지를 사용하여 해당 결과를 사이트에 즉시 보고합니다. 디바이스가 현재 네트워크에서 연결이 끊겼지만 구성 기준을 다운로드한 경우 여전히 구성 항목의 준수를 평가합니다. 다시 연결되면 준수 정보를 보냅니다.  

### <a name="monitoring-configuration-baselines"></a>구성 기준 모니터링
- **배포** 노드에서 **모니터링** 작업 영역 아래의 Configuration Manager 콘솔에서 준수 평가의 결과를 모니터링합니다. 예:
    - 비준수의 일반적인 원인
    - 오류
    - 영향을 받는 사용자와 디바이스 수
- 추가 세부 정보로 준수 설정 보고서를 실행합니다. 예:
    - 디바이스의 호환 또는 비호환 여부
    - 구성 기준의 요소는 컴퓨터를 비호환으로 만듦
- Configuration Manager 클라이언트를 실행하는 Windows 컴퓨터에서 준수 평가 결과를 봅니다. **Configuration Manager** 제어판을 열고, **구성** 탭으로 전환합니다.  



## <a name="user-data-and-profiles-configuration-items"></a>사용자 데이터 및 프로필 구성 항목  
 사용자 데이터 및 프로필의 구성 항목은 Windows 8 이상을 실행하는 컴퓨터의 사용자가 관리하는 방법을 제어하는 설정을 포함합니다.  
   - 폴더 리디렉션
   - 오프 라인 파일
   - 로밍 프로필  

사용자 컬렉션에 이러한 구성 항목을 배포합니다. Configuration Manager 콘솔의 **모니터링** 노드에서 해당 준수를 모니터링합니다. 다른 구성 항목과 달리 배포 전에 구성 기준에 추가하지 마십시오. 리본에서 **배포**를 클릭하여 직접 배포합니다.  

 자세한 내용은 [사용자 데이터 및 프로필 구성 항목 만들기](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)를 참조하세요.  



## <a name="remote-connection-profiles"></a>원격 연결 프로필  
 원격 연결 프로필은 원격 연결 설정을 만들어 배포하고 모니터링하는 데 유용한 도구 및 리소스 집합을 제공합니다. 이러한 설정을 디바이스에 배포하여 최종 사용자가 회사 네트워크에 자신의 컴퓨터를 연결하기 위해 수행해야 하는 작업을 최소화합니다.  

자세한 내용은 [원격 연결 프로필 만들기](/sccm/compliance/deploy-use/create-remote-connection-profiles)를 참조하세요.  



## <a name="windows-edition-upgrade"></a>Windows 버전 업그레이드
버전 업그레이드 정책은 Windows 10의 특정 버전을 실행하는 디바이스를 자동으로 최신 버전으로 업그레이드합니다. 이 정책은 디바이스가 업그레이드하는 데 사용하는 새 제품 키 또는 라이선스 파일을 제공합니다.

자세한 내용은 [버전 업그레이드 정책을 사용하여 Windows 디바이스 업그레이드](/sccm/compliance/deploy-use/upgrade-windows-version)를 참조하세요.



## <a name="microsoft-edge-browser-profiles"></a>Microsoft Edge 브라우저 프로필
<!-- 1357310 -->
1802 버전부터 Windows 10 클라이언트에서 [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) 웹 브라우저를 사용하는 고객은 준수 설정 정책을 만들어 여러 Microsoft Edge 설정을 구성합니다. 

자세한 내용은 [Microsoft Edge 브라우저 프로필](/sccm/compliance/deploy-use/browser-profiles)을 참조하세요.

