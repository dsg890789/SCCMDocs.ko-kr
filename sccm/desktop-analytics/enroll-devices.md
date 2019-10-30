---
title: 데스크톱 분석에 장치 등록
titleSuffix: Configuration Manager
description: 데스크톱 분석에서 장치를 등록 하는 방법을 알아봅니다.
ms.date: 04/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2ea18d09-c957-47f7-8e54-c6f2b3c74347
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5fc36829944b2366a05ce2c87e27ac97bfd9e764
ms.sourcegitcommit: 07756e9b4ed7b134e32349acb1eeae93c6de9e28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049397"
---
# <a name="how-to-enroll-devices-in-desktop-analytics"></a>데스크톱 분석에서 장치를 등록 하는 방법

데스크톱 분석에 [Configuration Manager 연결](/sccm/desktop-analytics/connect-configmgr) 하는 경우 데스크톱 분석에 장치를 등록 하는 설정을 구성 합니다. 이러한 설정은 언제 든 지 변경할 수 있습니다. 또한 장치가 최신 상태 인지 확인 합니다.



## <a name="update-devices"></a>장치 업데이트

데스크톱 분석의 최상의 경험을 위해 적용 해야 하는 업데이트에는 두 가지 유형이 있습니다.

- [호환성 업데이트](#bkmk_appraiser)  
- [연결 된 사용자 환경 및 원격 분석 서비스](#bkmk_diagtrack)


### <a name="bkmk_appraiser"></a>호환성 업데이트

호환성 구성 요소 (평가자)는 Windows 장치에서 진단을 실행 하 여 최신 버전의 Windows 10을 사용 하 여 호환성 상태를 평가 합니다.

Microsoft는이 구성 요소에 대 한 업데이트를 정기적으로 증가 하지만 관련 KB 번호는 변경 되지 않습니다. 항상 최신 버전의 업데이트를 사용할 수 있는지 확인 합니다.

처음으로 호환성 업데이트를 설치한 후 장치를 다시 시작 합니다.

> [!Tip]  
> Configuration Manager를 사용 하 여 최신 버전의 업데이트를 자동으로 설치 합니다. 자세한 내용은 [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)를 참조하세요.  

> [!Note]  
> 관련 옵션 업데이트 ( [KB 3150513)](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=3150513)가 있습니다. 이 업데이트는 이전 호환성 업데이트에 대 한 업데이트 된 구성 및 정의를 제공 합니다. 자세한 내용은 [Windows 용 최신 호환성 정의 업데이트](https://support.microsoft.com/help/3150513)를 참조 하세요.  

#### <a name="windows-10"></a>Windows 10

Windows 10에는 호환성 구성 요소가 포함 되어 있습니다. 최신 호환성 업데이트를 다운로드 하려면 최신 Windows 10 누적 업데이트를 설치 합니다.

#### <a name="windows-81"></a>Windows 8.1

업데이트 다운로드: [KB 2976978](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB2976978) 

Windows 사용자 환경 개선 프로그램에 참여 하는 Windows 8.1 시스템에서 진단을 실행 합니다. 이러한 진단은 Windows 10으로 업그레이드할 때 호환성 문제가 발생할 수 있는지 여부를 확인 하는 데 도움이 됩니다.

자세한 내용은 [Windows 8.1에서 Windows를 최신 상태로 유지 하기 위한 호환성 업데이트](https://support.microsoft.com/help/2976978)를 참조 하세요.

#### <a name="windows-7-with-service-pack-1"></a>Windows 7 서비스 팩 1

업데이트 다운로드: [KB 2952664](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB2952664) 

Windows 사용자 환경 개선 프로그램에 참여 하는 Windows 7 SP1 (서비스 팩 1) 시스템에서 진단을 실행 합니다. 이러한 진단은 Windows 10으로 업그레이드할 때 호환성 문제가 발생할 수 있는지 여부를 확인 하는 데 도움이 됩니다.

자세한 내용은 [windows 7에서 windows를 최신 상태로 유지 하기 위한 호환성 업데이트](https://support.microsoft.com/help/2952664)를 참조 하세요.


### <a name="bkmk_diagtrack"></a>연결 된 사용자 환경 및 원격 분석 서비스

Windows 진단 데이터를 사용 하도록 설정 하면 연결 된 사용자 환경 및 원격 분석 서비스 (DiagTrack)가 시스템, 응용 프로그램 및 드라이버 데이터를 수집 합니다. Microsoft는이 데이터를 분석 하 고 데스크톱 분석을 통해 다시 공유 합니다.

최상의 환경을 위해 OS 버전에 따라 다음 업데이트를 설치 합니다.

> [!Note]  
> 이러한 업데이트를 설치 하면 다음과 같은 동작이 발생할 수 있습니다.
> 
> - 데스크톱 분석에 등록 하는 장치는 한 시간 이내에 서비스에 표시 됩니다.  
> - 장치에서 Windows 기능 및 품질 업데이트에 대 한 상태를 신속 하 게 보고  
>
> 이러한 업데이트가 없으면 장치에서 데스크톱 분석에 보고 하는 데 48 시간이 넘게 걸릴 수 있습니다.  


#### <a name="windows-10"></a>Windows 10

최신 Windows 10 누적 업데이트를 설치 합니다.

<!-- 
- Windows 10 1809: Included in RTM build
- Windows 10 1803: [KB4458469](https://support.microsoft.com/help/4458469) (OS Build 17134.319)
- Windows 10 1709: [KB4457136](https://support.microsoft.com/help/4457136) (OS Build 16299.697)
- Windows 10 1703: [KB4457141](https://support.microsoft.com/help/4457141) (OS Build 15063.1358)
- Windows 10 1607: [KB4457127](https://support.microsoft.com/help/4457127) (OS Build 14393.2517)
 -->

#### <a name="windows-81"></a>Windows 8.1

10 월 2018 월 롤업 ( [KB4462926](https://support.microsoft.com/help/4462926) )을 설치 합니다.

#### <a name="windows-7"></a>Windows 7

10 월 2018 월 롤업 ( [KB4462923](https://support.microsoft.com/help/4462923) )을 설치 합니다.



## <a name="device-enrollment"></a>디바이스 등록

데스크톱 분석 서비스에 설치할 에이전트가 없습니다. 장치를 등록 하려면 모니터링할 장치에 대 한 설정을 구성 해야 합니다. 이러한 설정은 장치에서 데이터를 보내야 하는 데스크톱 분석 인스턴스와 기타 구성 옵션을 제어 합니다.

> [!Note]  
> Windows Analytics를 이미 사용 하 고 있는 경우 데스크톱 분석과 동일한 작업 영역을 사용 합니다. 이전에 Windows Analytics에 등록 한 데스크톱 분석에 장치를 했다가 해야 합니다.
>
> Azure AD 테 넌 트 당 하나의 데스크톱 분석 작업 영역만 사용할 수 있습니다. 장치는 하나의 작업 영역에만 진단 데이터를 보낼 수 있습니다.  

Configuration Manager는 이러한 설정을 관리 하 고 클라이언트에 배포 하는 통합 환경을 제공 합니다. 최상의 환경을 위해 Configuration Manager를 사용 합니다.

데스크톱 분석에 Configuration Manager 연결 하는 경우 장치를 등록 하는 설정을 구성 합니다. 자세한 내용은 [데스크톱 분석과 Configuration Manager 연결 하는 방법](/sccm/desktop-analytics/connect-configmgr#bkmk_connect)을 참조 하세요.

이러한 설정을 변경 하려면 다음 절차를 따르십시오.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 데스크톱 분석에 대 한 연결을 선택 하 고 리본에서 **속성** 을 선택 합니다.

2. **진단 데이터** 페이지에서 필요에 따라 다음 설정으로 변경 합니다.  

    - **상용 id**:이 값은 조직의 ID로 자동으로 채워집니다. 그렇지 않은 경우 계속 하기 전에 프록시 서버가 필요한 모든 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints) 을 허용 하도록 구성 되어 있는지 확인 합니다. 또는 [데스크톱 분석 포털](/sccm/desktop-analytics/monitor-connection-health#bkmk_ViewCommercialID)에서 수동으로 상용 ID를 검색 합니다.   

    - **Windows 10 진단 데이터 수준**: 자세한 내용은 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)을 참조 하세요.  

    - **진단 데이터에서 장치 이름 허용**: 자세한 내용은 [장치 이름](#device-name)을 참조 하세요.  

    이 페이지를 변경 하면 **사용 가능한 기능** 페이지에 선택한 진단 데이터 설정의 데스크톱 분석 기능 미리 보기가 표시 됩니다.  

3. **데스크톱 분석 연결** 페이지에서 필요에 따라 다음 설정으로 변경 합니다.

    - **표시 이름**: 데스크톱 분석 포털은이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다.  

    - **대상 컬렉션**:이 컬렉션에는 상업적 ID 및 진단 데이터 설정 Configuration Manager 구성 하는 모든 장치가 포함 됩니다. Configuration Manager는 데스크톱 분석 서비스에 연결 하는 전체 장치 집합입니다.  

    - **대상 컬렉션의 장치는 아웃 바운드 통신에 사용자 인증 프록시를 사용**합니다. 기본적으로이 값은 **아니요**입니다. 사용자 환경에 필요한 경우를 **예**로 설정 합니다. 자세한 내용은 [프록시 서버 인증](/sccm/desktop-analytics/enable-data-sharing#proxy-server-authentication)을 참조 하세요.  

    - **데스크톱 분석과 동기화 할 특정 컬렉션 선택**: **추가** 를 선택 하 여 **대상 컬렉션** 계층의 추가 컬렉션을 포함 합니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화 하기 위해 데스크톱 분석 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  <!-- 4097528 -->

        > [!Important] 
        > 이러한 컬렉션은 멤버 자격 변경 내용에 따라 계속 동기화 됩니다. 예를 들어 배포 계획에서는 Windows 7 멤버 자격 규칙을 사용 하는 컬렉션을 사용 합니다. 이러한 장치는 Windows 10으로 업그레이드 되 고 Configuration Manager 컬렉션 멤버 자격을 평가 하므로 해당 장치는 수집 및 배포 계획에서 제외 됩니다.  


### <a name="windows-settings"></a>Windows 설정

Configuration Manager 로컬 정책 경로 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection` 아래에 다음 Windows 설정을 설정 합니다.

| 정책   | 값  |
|----------|--------|
| **CommercialId** | *Windows 7, Windows 8.1 및 windows 10에 적용 됩니다*. 데스크톱 분석에서 장치를 표시 하려면 조직의 상용 ID를 사용 하 여 구성 합니다. |
| **AllowTelemetry 분석**  | *Windows 10에 적용 됩니다*. **전체** 진단 데이터에 대해 **Basic**, `2` **고급**또는 `3`에 대 한 `1` 설정 합니다. 데스크톱 분석에는 최소 기본 진단 데이터가 필요 합니다. 데스크톱 분석과 함께 향상 된 (제한 된) 수준을 사용 하는 것이 좋습니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization)을 참조하세요. |
| **LimitEnhancedDiagnosticDataWindowsAnalytics** | *Windows 10 버전 1709 이상에 적용*됩니다 .이 설정은 allowtelemetry 분석 설정이 `2` 경우에만 적용 됩니다. Microsoft로 전송 되는 향상 된 진단 데이터 이벤트를 데스크톱 분석에 필요한 이벤트로만 제한 합니다. 자세한 내용은 windows [10, 버전 1709 고급 진단 데이터 이벤트 및 Windows Analytics에서 사용 되는 필드](https://docs.microsoft.com/windows/configuration/enhanced-diagnostic-data-windows-analytics-events-and-fields)를 참조 하세요.|
| **AllowDeviceNameInTelemetry** | *Windows 10 버전 1803 이상에 적용*됩니다. 장치에서 장치 이름을 계속 보낼 수 있도록 하려면 별도의 옵트인이 필요 합니다.<br> <br>참고: 장치 이름은 기본적으로 Microsoft에 전송 되지 않습니다. 장치 이름을 보내지 않으면 데스크톱 분석에서 "알 수 없음"으로 표시 됩니다. 이 동작을 통해 장치를 식별 하 고 평가 하기 어려울 수 있습니다. 자세한 내용은 [장치 이름](#device-name)을 참조 하세요. |
| **CommercialDataOptIn** | *Windows 7 및 Windows 8.1에 적용*됩니다. 데스크톱 분석에는 `1` 값이 필요 합니다. 자세한 내용은 [Windows 7의 상용 데이터 옵트인](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/ee126127\(v=ws.10\))(영문)을 참조 하세요. |
| **RequestAllAppraiserVersions** | *모든 Windows 버전에 적용 됩니다*. 데이터 수집이 제대로 작동 하려면 데스크톱 분석에 `1` 값이 필요 합니다. |

그룹 정책 편집기에서 **컴퓨터 구성**  > **관리 템플릿**  > **Windows 구성 요소**  > **데이터 수집 및 미리 보기 빌드**에서 이러한 설정을 봅니다.

> [!Important]  
> 대부분의 경우 Configuration Manager만 사용 하 여 이러한 설정을 구성할 수 있습니다. 도메인 그룹 정책 개체에도 이러한 설정을 적용 하지 마십시오. 자세한 내용은 [충돌 해결](#conflict-resolution)을 참조 하세요.<!-- SCCMDocs-pr 3120 -->

### <a name="device-name"></a>장치 이름

Windows 10 버전 1803부터 장치 이름은 더 이상 기본적으로 수집 되지 않습니다. 진단 데이터를 사용 하 여 장치 이름을 수집 하려면 별도 옵트인이 필요 합니다. 장치 이름이 없으면 새 버전의 Windows로 업그레이드를 평가 하는 동안 주의가 필요한 장치를 식별 하는 것이 더 어렵습니다.

장치 이름을 보내지 않으면 데스크톱 분석에서 "알 수 없음"으로 표시 됩니다.

!["알 수 없음" 이름을 표시 하는 데스크톱 분석 장치 목록](media/unknown-device-name.png)

데스크톱 분석에 대 한 Configuration Manager 설정에는 **진단 데이터의 장치 이름 허용**옵션을 구성 하는 옵션이 있습니다. 이 Configuration Manager 설정은 Windows 정책 설정인 AllowDeviceNameInTelemetry를 제어 합니다.
 

### <a name="conflict-resolution"></a>충돌 해결

일반적으로 Configuration Manager 컬렉션을 사용 하 여 데스크톱 분석 설정 및 등록을 대상으로 합니다. 직접 멤버 자격 또는 쿼리를 사용 하 여 컬렉션에서 장치를 포함 하거나 제외 합니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.

Configuration Manager 값이 없는 경우에만 Windows 설정을 구성 합니다. 고유한 장치 그룹에 대해 서로 다른 설정을 구성 해야 하는 경우 [그룹 정책을](#windows-settings)사용할 수 있습니다. 그룹 정책에서 대상으로 지정 된 설정은 Configuration Manager 설정 보다 우선 적용 됩니다.

Windows Analytics 및 데스크톱 분석 설정을 사용 하 여 Configuration Manager 클라이언트를 대상으로 하는 경우 데스크톱 분석 설정이 우선 적용 됩니다.

진단 데이터 수준을 구성할 때 장치의 상한을 설정 합니다. 기본적으로 Windows 10 버전 1803 이상에서는 사용자가 하위 수준을 설정 하도록 선택할 수 있습니다. 그룹 정책 설정인 **원격 분석 옵트인 설정 사용자 인터페이스**를 사용 하 여이 동작을 제어할 수 있습니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.



## <a name="next-steps"></a>다음 단계

데스크톱 분석에서 배포 계획을 만들려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]  
> [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
