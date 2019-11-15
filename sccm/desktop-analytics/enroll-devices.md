---
title: Desktop Analytics에서 디바이스 등록
titleSuffix: Configuration Manager
description: Desktop Analytics에서 디바이스를 등록하는 방법을 알아봅니다.
ms.date: 10/30/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2ea18d09-c957-47f7-8e54-c6f2b3c74347
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10535acc49f047876eafb188569e82db7a2bbea9
ms.sourcegitcommit: b0f1c2fe1e034f0fe8676f1528249a4b26f54bd3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704801"
---
# <a name="how-to-enroll-devices-in-desktop-analytics"></a>Desktop Analytics에서 디바이스를 등록하는 방법

Desktop Analytics에 [Configuration Manager를 연결](/sccm/desktop-analytics/connect-configmgr)하는 경우 Desktop Analytics에 디바이스를 등록하는 설정을 구성합니다. 이러한 설정은 언제든지 변경할 수 있습니다. 또한 디바이스가 최신 상태인지 확인합니다.



## <a name="update-devices"></a>디바이스 업데이트

Desktop Analytics의 최상의 경험을 위해 적용해야 하는 업데이트에는 두 가지 유형이 있습니다.

- [호환성 업데이트](#bkmk_appraiser)  
- [연결된 사용자 환경 및 원격 분석 서비스](#bkmk_diagtrack)


### <a name="bkmk_appraiser"></a> 호환성 업데이트

호환성 구성 요소(평가자)는 Windows 디바이스에서 진단을 실행하여 최신 버전의 Windows 10을 통해 호환성 상태를 평가합니다.

Microsoft는 이 구성 요소에 대한 업데이트를 정기적으로 증가시키고 있지만, 관련 KB 번호는 변경되지 않습니다. 항상 최신 버전의 업데이트를 사용할 수 있는지 확인하세요.

처음으로 호환성 업데이트를 설치한 후에는 디바이스를 다시 시작합니다.

> [!Tip]  
> Configuration Manager를 사용하면 이러한 업데이트의 최신 버전을 자동으로 설치할 수 있습니다. 자세한 내용은 [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)를 참조하세요.  

> [!Note]  
> 관련된 선택적 업데이트([KB 3150513](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=3150513))가 있습니다. 이 업데이트는 이전 호환성 업데이트에 대한 업데이트된 구성 및 정의를 제공합니다. 자세한 내용은 [Windows에 대한 최신 호환성 정의 업데이트](https://support.microsoft.com/help/3150513)를 참조하세요.  

#### <a name="windows-10"></a>Windows 10

Windows 10에는 호환성 구성 요소가 포함되어 있습니다. 최신 호환성 업데이트를 가져오려면 최신 Windows 10 누적 업데이트를 설치합니다.

#### <a name="windows-81"></a>Windows 8.1

다음 업데이트를 다운로드합니다. [KB 2976978](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB2976978) 

Windows 사용자 환경 개선 프로그램에 참여하는 Windows 8.1 시스템에서 진단을 실행합니다. 이러한 진단은 Windows 10으로 업그레이드할 때 호환성 문제가 발생할 수 있는지 여부를 확인하는 데 도움이 됩니다.

자세한 내용은 [Windows 8.1에서 Windows를 최신 상태로 유지하기 위한 호환성 업데이트](https://support.microsoft.com/help/2976978)를 참조하세요.

#### <a name="windows-7-with-service-pack-1"></a>Windows 7 서비스 팩 1

다음 업데이트를 다운로드합니다. [KB 2952664](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB2952664) 

Windows 사용자 환경 개선 프로그램에 참여하는 Windows 7 서비스 팩 1(SP1) 시스템에서 진단을 실행합니다. 이러한 진단은 Windows 10으로 업그레이드할 때 호환성 문제가 발생할 수 있는지 여부를 확인하는 데 도움이 됩니다.

자세한 내용은 [Windows 7에서 Windows를 최신 상태로 유지하기 위한 호환성 업데이트](https://support.microsoft.com/help/2952664)를 참조하세요.


### <a name="bkmk_diagtrack"></a> 연결된 사용자 환경 및 원격 분석 서비스

Windows 진단 데이터를 사용하도록 설정하면 연결된 사용자 환경 및 원격 분석 서비스(DiagTrack)가 시스템, 애플리케이션 및 드라이버 데이터를 수집합니다. Microsoft는 이 데이터를 분석하고 Desktop Analytics를 통해 다시 공유합니다.

최상의 환경을 위해 OS 버전에 따라 다음 업데이트를 설치합니다.

> [!Note]  
> 이러한 업데이트를 설치하면 다음과 같은 동작이 발생할 수 있습니다.
> 
> - Desktop Analytics에 등록하는 디바이스가 한 시간 이내에 서비스에 표시됩니다.  
> - 디바이스에서 Windows 기능 및 품질 업데이트에 대한 상태를 신속하게 보고합니다.  
>
> 이러한 업데이트가 없으면 디바이스에서 Desktop Analytics에 보고하는 데 48시간 이상이 걸릴 수 있습니다.  


#### <a name="windows-10"></a>Windows 10

최신 Windows 10 누적 업데이트를 설치합니다.

<!-- 
- Windows 10 1809: Included in RTM build
- Windows 10 1803: [KB4458469](https://support.microsoft.com/help/4458469) (OS Build 17134.319)
- Windows 10 1709: [KB4457136](https://support.microsoft.com/help/4457136) (OS Build 16299.697)
- Windows 10 1703: [KB4457141](https://support.microsoft.com/help/4457141) (OS Build 15063.1358)
- Windows 10 1607: [KB4457127](https://support.microsoft.com/help/4457127) (OS Build 14393.2517)
 -->

#### <a name="windows-81"></a>Windows 8.1

2018년 10월 월별 롤업([KB4462926](https://support.microsoft.com/help/4462926))을 설치합니다.

#### <a name="windows-7"></a>Windows 7

2018년 10월 월별 롤업([KB4462923](https://support.microsoft.com/help/4462923))을 설치합니다.



## <a name="device-enrollment"></a>디바이스 등록

Desktop Analytics 서비스에 설치할 에이전트가 없습니다. 디바이스를 등록하려면 모니터링할 디바이스에 대한 설정을 구성해야 합니다. 이러한 설정은 디바이스에서 해당 데이터를 보내야 하는 Desktop Analytics 인스턴스와 기타 구성 옵션을 제어합니다.

> [!Note]  
> Windows Analytics를 이미 사용 중인 경우에는 Desktop Analytics에 대해 동일한 작업 영역을 선택합니다. 이전에 Windows Analytics에 등록한 Desktop Analytics에 디바이스를 다시 등록해야 합니다.
>
> Azure AD 테넌트당 하나의 Desktop Analytics 작업 영역만 사용할 수 있습니다. 디바이스는 하나의 작업 영역에만 진단 데이터를 보낼 수 있습니다.  

Configuration Manager는 이러한 설정을 관리하고 클라이언트에 배포하는 통합 환경을 제공합니다. 최상의 환경을 위해 Configuration Manager를 사용합니다.

Desktop Analytics에 Configuration Manager를 연결하는 경우 디바이스를 등록하는 설정을 구성합니다. 자세한 내용은 [Configuration Manager를 Desktop Analytics와 연결하는 방법](/sccm/desktop-analytics/connect-configmgr#bkmk_connect)을 참조하세요.

이러한 설정을 변경하려면 다음 절차를 사용합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. Desktop Analytics에 대한 연결을 선택하고 리본에서 **속성**을 선택합니다.

2. **진단 데이터** 페이지에서 필요에 따라 다음 설정으로 변경합니다.  

    - **상업용 ID**: 이 값은 조직의 ID로 자동으로 채워집니다. 그렇지 않은 경우 계속하기 전에 프록시 서버가 필요한 [엔드포인트](/sccm/desktop-analytics/enable-data-sharing#endpoints)를 모두 허용하도록 구성되어 있는지 확인합니다. 또는 [Desktop Analytics 포털](/sccm/desktop-analytics/monitor-connection-health#bkmk_ViewCommercialID)에서 상업용 ID를 수동으로 검색합니다.   

    - **Windows 10 진단 데이터 수준**: 자세한 내용은 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)을 참조하세요.  

    - **진단 데이터의 디바이스 이름 허용**: 자세한 내용은 [디바이스 이름](#device-name)을 참조하세요.  

    이 페이지를 변경하는 경우 **사용 가능한 기능** 페이지에 선택한 진단 데이터 설정을 사용하여 Desktop Analytics 기능의 미리 보기가 표시됩니다.  

3. **Desktop Analytics 연결** 페이지에서 필요에 따라 다음 설정으로 변경합니다.

    - **표시 이름**: Desktop Analytics 포털에서 이 이름을 사용하여 이 Configuration Manager 연결을 표시합니다.  

    - **대상 컬렉션**: 이 컬렉션에는 Configuration Manager가 상업용 ID 및 진단 데이터 설정으로 구성하는 모든 디바이스가 포함됩니다. Configuration Manager가 Desktop Analytics 서비스에 연결하는 전체 디바이스 세트입니다.  

    - **대상 컬렉션의 디바이스가 아웃바운드 통신에 사용자 인증 프록시 사용**: 기본적으로 이 값은 **아니요**입니다. 사용자 환경에 필요한 경우 **예**로 설정합니다. 자세한 내용은 [프록시 서버 인증](/sccm/desktop-analytics/enable-data-sharing#proxy-server-authentication)을 참조하세요.  

    - **Desktop Analytics와 동기화할 특정 컬렉션 선택**: **대상 컬렉션** 계층 구조에서 추가 컬렉션을 포함하려면 **추가**를 선택합니다. 이러한 컬렉션은 Desktop Analytics 포털에서 배포 계획과 그룹화할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함해야 합니다.  <!-- 4097528 -->

        > [!Important] 
        > 이러한 컬렉션은 멤버 자격이 변경됨에 따라 계속 동기화됩니다. 예를 들어 배포 계획에서는 Windows 7 멤버 자격 규칙이 있는 컬렉션을 사용합니다. 이러한 디바이스가 Windows 10으로 업그레이드되고 Configuration Manager가 컬렉션 멤버 자격을 평가하면 해당 디바이스는 컬렉션 및 배포 계획에서 제외됩니다.  


### <a name="windows-settings"></a>Windows 설정

Configuration Manager는 다음 레지스트리 키 중 하나 또는 모두에 해당하는 Windows 정책을 설정합니다.

- **GPO**: `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

- **로컬 정책** 기본 설정: `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`

| 정책   | 경로 | 값  | 
|----------|------|--------|
| **CommercialId** | 로컬 정책 | *Windows 7, Windows 8.1 및 Windows 10에 적용*: Desktop Analytics에서 디바이스를 표시하려면 조직의 상업용 ID를 사용하여 디바이스를 구성합니다. | 
| **AllowTelemetry**  | GPO | *Windows 10에 적용*: **기본**에 대한 `1`, **고급**에 대해 `2` 또는 **전체** 진단 데이터에 대해 `3`을 설정합니다. Desktop Analytics에는 최소 기본 진단 데이터가 필요합니다. Microsoft는 Desktop Analytics와 함께 고급(제한) 수준을 사용하는 것을 권장합니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization)을 참조하세요. |
| **LimitEnhancedDiagnosticDataWindowsAnalytics** | GPO | *Windows 10, 버전 1803 이상에 적용*: 이 설정은 AllowTelemetry 설정이 `2`인 경우에만 적용됩니다. Microsoft로 전송되는 고급 진단 데이터 이벤트를 Desktop Analytics에 필요한 이벤트로만 제한합니다. 자세한 내용은 [고급 진단 데이터 제한 정책을 통해 수집된 Windows 10 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/windows/configuration/enhanced-diagnostic-data-windows-analytics-events-and-fields)를 참조하세요.|
| **AllowDeviceNameInTelemetry** | GPO | *Windows 10, 버전 1803 이상에 적용*: 디바이스에서 디바이스 이름을 계속 보낼 수 있도록 하려면 별도 옵트인이 필요합니다.<br> <br>참고: 디바이스 이름은 기본적으로 Microsoft로 전송되지 않습니다. 디바이스 이름을 보내지 않으면 Desktop Analytics에 “알 수 없음”으로 표시됩니다. 이 동작으로 인해 디바이스를 식별하고 평가하기가 어려울 수 있습니다. 자세한 내용은 [디바이스 이름](#device-name)을 참조하세요. | 
| **CommercialDataOptIn** | 로컬 정책 |*Windows 7 및 Windows 8.1에 적용*: Desktop Analytics에는 `1` 값이 필요합니다. 자세한 내용은 [Windows 7의 상업용 데이터 옵트인](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/ee126127\(v=ws.10\))을 참조하세요. |
| **RequestAllAppraiserVersions** | 모두 |*Windows 7 및 Windows 8.1에 적용*: 데이터 수집이 제대로 작동하려면 Desktop Analytics에 `1` 값이 필요합니다. | 
| **DisableEnterpriseAuthProxy** | GPO |*모든 Windows 플랫폼에 적용*: 데이터 수집이 제대로 작동하려면 Desktop Analytics에 `0` 값이 필요합니다. | 

> [!Important]  
> 대부분의 경우 Configuration Manager만 사용하여 이러한 설정을 구성합니다. 도메인 그룹 정책 개체에도 이러한 설정을 적용하지 마십시오. 자세한 내용은 [충돌 해결](#conflict-resolution)을 참조하세요.<!-- SCCMDocs-pr 3120 -->

### <a name="device-name"></a>디바이스 이름

Windows 10 버전 1803부터 디바이스 이름은 더 이상 기본적으로 수집되지 않습니다. 진단 데이터를 사용하여 디바이스 이름을 수집하려면 별도 옵트인이 필요합니다. 디바이스 이름이 없으면 새 버전의 Windows로 업그레이드를 평가하는 동안 주의가 필요한 디바이스를 식별하는 것이 더 어렵습니다.

디바이스 이름을 보내지 않으면 Desktop Analytics에 “알 수 없음”으로 표시됩니다.

![“알 수 없음” 이름을 표시하는 Desktop Analytics 디바이스 목록](media/unknown-device-name.png)

Desktop Analytics에 대한 Configuration Manager 설정에는 이 옵션을 구성하는 옵션이 있습니다. **진단 데이터의 디바이스 이름 허용**: 이 Configuration Manager 설정은 Windows 정책 설정인 AllowDeviceNameInTelemetry를 제어합니다.
 

### <a name="conflict-resolution"></a>충돌 해결

일반적으로 Configuration Manager 컬렉션을 사용하여 Desktop Analytics 설정 및 등록을 대상으로 합니다. 직접 멤버 자격 또는 쿼리를 사용하여 컬렉션에서 디바이스를 포함하거나 제외합니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.

Configuration Manager는 값이 없는 경우에만 Windows 설정을 구성합니다. 고유한 디바이스 그룹에 대해 서로 다른 설정을 구성해야 하는 경우 [그룹 정책](#windows-settings)를 사용할 수 있습니다. 

다음 경로의 그룹 정책 편집기에서 이러한 설정을 봅니다. **컴퓨터 구성** > **관리 템플릿** > **Windows 구성 요소** > **데이터 수집 및 미리 보기 빌드**. 그룹 정책에서 대상으로 지정된 설정은 Configuration Manager 설정보다 우선 적용됩니다.

Windows Analytics 및 Desktop Analytics 설정을 모두 사용하는 Configuration Manager 클라이언트를 대상으로 하는 경우 Desktop Analytics에 대한 설정이 우선 적용됩니다.

진단 데이터 수준을 구성할 때 디바이스의 상한을 설정합니다. 기본적으로 Windows 10 버전 1803 이상에서는 사용자가 하위 수준을 설정하도록 선택할 수 있습니다. 그룹 정책 설정인 **원격 분석 옵트인 설정 사용자 인터페이스 구성**을 사용하여 이 동작을 제어할 수 있습니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.



## <a name="next-steps"></a>다음 단계

Desktop Analytics에서 배포 계획을 만드는 다음 문서로 이동합니다.
> [!div class="nextstepaction"]  
> [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
