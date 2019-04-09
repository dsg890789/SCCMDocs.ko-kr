---
title: 데스크톱 분석에서 장치 등록
titleSuffix: Configuration Manager
description: 데스크톱 Analytics에서 장치를 등록 하는 방법을 알아봅니다.
ms.date: 04/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2ea18d09-c957-47f7-8e54-c6f2b3c74347
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5d5e6665b0ddd2e7726af4b8ac8929d5019fedf
ms.sourcegitcommit: 5ee9487c891c37916294bd34a10d04e398f111f7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59069469"
---
# <a name="how-to-enroll-devices-in-desktop-analytics"></a>데스크톱 Analytics에서 장치를 등록 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

경우 있습니다 [Configuration Manager 연결](/sccm/desktop-analytics/connect-configmgr) 데스크톱 Analytics로 데스크톱 Analytics에는 장치를 등록 하는 설정을 구성한 합니다. 이러한 설정은 언제 든 지 변경할 수 있습니다. 또한 장치는 최신 해야 합니다.



## <a name="update-devices"></a>장치 업데이트

데스크톱 Analytics를 사용 하 여 최상의 환경을 위해 적용 해야 하는 업데이트는 다음과 같은 두 종류가 있습니다.

- [호환성 업데이트](#bkmk_appraiser)  
- [연결 된 사용자 환경 및 원격 분석 서비스](#bkmk_diagtrack)


### <a name="bkmk_appraiser"></a> 호환성 업데이트

Windows 10의 최신 버전을 사용 하 여 해당 호환성 상태를 평가 하는 Windows 장치에서 진단 유틸리티를 실행 하는 호환성 구성 요소 (평가자).

Microsoft는이 구성 요소에 대 한 업데이트를 정기적으로 증가 하지만 관련된 KB 번호 변경 되지 않습니다. 있는지 항상 최신 버전의 업데이트를 확인 합니다.

처음에 대 한 호환성 업데이트를 설치한 후에 장치를 다시 시작 합니다.

> [!Tip]  
> 이러한 업데이트의 최신 버전을 자동으로 설치 하려면 Configuration Manager를 사용 합니다. 자세한 내용은 [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)를 참조하세요.  

> [!Note]  
> 선택적 업데이트를 관련된 없는 [KB 3150513](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=3150513)합니다. 이 업데이트는 업데이트 된 구성과 이전 호환성 업데이트에 대 한 정의 제공합니다. 자세한 내용은 [Windows 용 최신 호환성 정의 업데이트](https://support.microsoft.com/help/3150513)합니다.  

#### <a name="windows-10"></a>Windows 10

Windows 10 호환성 구성 요소를 포함 합니다. 최신 호환성 업데이트를 가져오려면 최신 Windows 10 누적 업데이트를 설치 합니다.

#### <a name="windows-81"></a>Windows 8.1

업데이트 다운로드: [KB 2976978](http://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB2976978) 

Windows 사용자 환경 개선 프로그램에 참여 하는 Windows 8.1 시스템에서 진단 유틸리티를 실행 합니다. 이러한 진단 확인할 지 여부를 Windows 10으로 업그레이드 하는 경우 호환성 문제가 있을 수 있습니다.

자세한 내용은 [Windows를 Windows 8.1 최신 상태로 유지 하는 것에 대 한 호환성 업데이트](https://support.microsoft.com/help/2976978)합니다.

#### <a name="windows-7-with-service-pack-1"></a>Windows 7 서비스 팩 1

업데이트 다운로드: [KB 2952664](http://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB2952664) 

Windows 사용자 환경 개선 프로그램에 참여 하는 서비스 팩 1 (SP1) 시스템을 사용 하 여 Windows 7에서 진단 유틸리티를 실행 합니다. 이러한 진단 확인할 지 여부를 Windows 10으로 업그레이드 하는 경우 호환성 문제가 있을 수 있습니다.

자세한 내용은 [Windows를 Windows 7의 최신 상태로 유지 하는 것에 대 한 호환성 업데이트](https://support.microsoft.com/help/2952664)합니다.


### <a name="bkmk_diagtrack"></a> 연결 된 사용자 환경 및 원격 분석 서비스

설정 된 Windows 진단 데이터를 사용 하 여 연결 된 사용자 환경 및 원격 분석 서비스 (DiagTrack) 시스템, 응용 프로그램 및 드라이버 데이터를 수집 합니다. Microsoft이이 데이터를 분석 하 고 데스크톱 분석을 통해를 공유 합니다.

최상의 환경을 위해 OS 버전에 따라 다음 업데이트를 설치 합니다.

> [!Note]  
> 이러한 업데이트를 설치할 때 다음 동작을 예상 합니다.
> 
> - 데스크톱 Analytics에 등록 하는 장치에에서 표시 서비스에서 1 시간 미만  
> - 장치 신속 하 게 상태를 보고 기능 및 품질 업데이트에서 Windows 및 Office에 대 한  
>
> 이러한 업데이트를 하지 않고 이러한 프로세스에는 데스크톱 Analytics에 보고 하는 장치에 대 한 48 시간 이상 걸릴 수 있습니다.  


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

2018 년 10 월 월별 롤업 설치 [KB4462926](https://support.microsoft.com/help/4462926)

#### <a name="windows-7"></a>Windows 7

2018 년 10 월 월별 롤업 설치 [KB4462923](https://support.microsoft.com/help/4462923)



## <a name="device-enrollment"></a>디바이스 등록

데스크톱 분석 서비스에 설치 하려면 에이전트 없음 장치 등록을 모니터링 하려는 장치의 설정을 구성 해야 합니다. 이러한 설정은 데스크톱 분석 인스턴스 장치 보내야 하는 데이터 및 기타 구성 옵션을 제어 합니다.

> [!Note]  
> Windows Analytics를 이미 사용 중인 경우 데스크톱 분석을 위해 동일한 작업 영역을 사용 합니다. Windows Analytics에서 이전에 등록 하는 데스크톱 분석 하는 장치를 등록 해야 합니다.
>
> Azure AD 테 넌 트 당 하나의 데스크톱 분석 작업 영역을만 있습니다. 장치만 하나의 작업 영역에 진단 데이터를 보낼 수 있습니다.  

Configuration Manager 클라이언트에 이러한 설정을 배포 및 관리에 대 한 통합된 된 환경을 제공 합니다. 최상의 환경을 위해 Configuration Manager를 사용 합니다.

Configuration Manager를 데스크톱 Analytics에 연결 하는 경우 장치 등록 설정 구성 자세한 내용은 [데스크톱 Analytics를 사용 하 여 Configuration Manager를 연결 하는 방법을](/sccm/desktop-analytics/connect-configmgr#bkmk_connect)합니다.

이러한 설정을 변경 하려면 다음 절차를 따르십시오.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 데스크톱 분석에 대 한 연결을 선택 하 고 선택 **속성** 리본 메뉴에 있습니다.

2. 에 **진단 데이터** 페이지에서 다음 설정이 필요에 따라 변경 합니다.  

    - **상업용 ID**: 변경 하거나이 값을 편집할 필요가 없습니다. 상용 ID 사용 하 여 문제 해결에 대 한 자세한 내용은 참조 하세요. [상용 ID 구성](/sccm/desktop-analytics/troubleshooting#commercial-id-configuration)합니다.  

    - **Windows 10 진단 데이터 수준**: 자세한 내용은 [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)합니다.  

    - **장치 이름을 진단 데이터의 허용**: 자세한 내용은 [장치 이름](#device-name)합니다.  

    이 페이지를 변경 하는 경우는 **사용할 수 있는 기능** 페이지 선택된 된 진단 데이터 설정 사용 하 여 데스크톱 분석 기능의 미리 보기를 표시 합니다.  

3. 에 **Microsoft 365 Analytics 연결** 페이지에서 다음 설정이 필요에 따라 변경 합니다.

    - **표시 이름**: 데스크톱 Analytics 포털에이 이름을 사용 하 여이 Configuration Manager 연결을 표시 합니다.  

    - **컬렉션을 대상**: 이 컬렉션에 진단 데이터 설정과 상업용 ID를 사용 하 여 Configuration Manager를 구성 하는 모든 장치를 포함 합니다. Configuration Manager에서 데스크톱 Analytics 서비스에 연결 하는 장치의 전체 집합은  

    - **아웃 바운드 통신에 대 한 사용자 인증 프록시를 사용 하는 대상 컬렉션의 장치**: 기본적으로이 값은 **No**합니다. 사용자 환경에서 필요한 경우로 **예**합니다. 자세한 내용은 [프록시 서버 인증](/sccm/desktop-analytics/enable-data-sharing#proxy-server-authentication)합니다.  

    - **데스크톱 Analytics와 동기화 하도록 특정 컬렉션 선택**: 선택 **추가** 추가 컬렉션을 포함 합니다. 이러한 컬렉션은 배포 계획을 사용 하 여 그룹화에 대 한 데스크톱 Analytics 포털에서 사용할 수 있습니다. 파일럿 및 파일럿 제외 컬렉션을 포함 해야 합니다.  

        이러한 컬렉션의 멤버 자격 변경으로 동기화 계속 합니다. 예를 들어 배포 계획을 Windows 7 멤버 관리 규칙을 사용 하 여 컬렉션을 사용 합니다. 해당 장치를 Windows 10으로 업그레이드 하 고 Configuration Manager 컬렉션 멤버 자격을 평가, 수집 및 배포 계획에서 해당 장치를 삭제 합니다.  


### <a name="windows-settings"></a>Windows 설정

Configuration Manager 설정 아래에서 다음 Windows 설정을 `Microsoft\Windows\DataCollection`:

| 정책   | 값  |
|----------|--------|
| **CommercialId** | 데스크톱 분석에 표시 하려면 장치에 대 한 순서로 구성에 사용 하 여 조직의 상업용 id입니다. |
| **AllowTelemetry**  | 설정할 `1` 에 대 한 **기본**를 `2` 에 대 한 **고급**, 또는 `3` 에 대 한 **전체** 진단 데이터입니다. 데스크톱 분석에는 최소한 기본 진단 데이터가 필요합니다. 고급 (제한적) 수준을 사용 하 여 데스크톱 Analytics를 사용 하는 것이 좋습니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization)을 참조하세요. |
| **LimitEnhancedDiagnosticDataWindowsAnalytics** | *Windows 10 버전 1709 이상에 적용 됩니다*: 이 설정은 AllowTelemetry 설정이 인 경우에 적용 `2`합니다. 데스크톱 분석에 필요한 해당 이벤트를 Microsoft로 전송 고급 진단 데이터 이벤트를 제한 합니다. 자세한 내용은 [Windows 10 버전 1709 향상 된 진단 데이터 이벤트 및 Windows Analytics에 의해 사용 되는 필드](https://docs.microsoft.com/windows/configuration/enhanced-diagnostic-data-windows-analytics-events-and-fields)합니다.|
| **AllowDeviceNameInTelemetry** | *Windows 10, 버전 1803 이상에 적용 됩니다*: 장치 이름을 보내려면 장치를 활성화 하는 별도 옵트인 필요 합니다.<br> <br>참고: 장치 이름은 기본적으로 Microsoft에 전송 되지 않습니다. 경우 "Unknown"으로 데스크톱 분석 나타나는 장치 이름을 보내지 않습니다. 이 동작을 파악 하 고 장치를 평가 어렵게 만들 수 있습니다. 자세한 내용은 [장치 이름](#device-name)합니다. |
| **CommercialDataOptIn** | *Windows 7 및 Windows 8.1 적용 됩니다*: 값 `1` 데스크톱 분석을 위해 필요 합니다. 자세한 내용은 [상용 데이터 옵트인 Windows 7에서](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/ee126127\(v=ws.10\))합니다. |

다음 경로에서 그룹 정책 편집기에서 이러한 설정을 봅니다. **컴퓨터 구성** > **관리 템플릿** > **Windows 구성 요소** > **데이터 컬렉션 및 미리 보기 빌드**합니다.

> [!Important]  
> 대부분의 경우에 이러한 설정을 구성 하려면 Configuration Manager를 사용 합니다. 도메인 그룹 정책 개체에서 이러한 설정을 적용할 수도 없습니다. 자세한 내용은 [충돌 해결](#conflict-resolution)합니다.<!-- SCCMDocs-pr 3120 -->

### <a name="device-name"></a>장치 이름

부터 Windows 10, 버전 1803에서 장치 이름은 더 이상 기본적으로 수집 됩니다. 진단 데이터를 사용 하 여 장치 이름을 수집을 별도 옵트인 해야 합니다. 장치 이름 없이 더 어렵습니다 어떤 장치를 새 버전의 Windows 또는 Office로의 업그레이드를 평가 하는 동안 주의가 식별할 수 있습니다.

경우 "Unknown"으로 데스크톱 분석 나타나는 장치 이름을 보내지 않습니다.

!["알 수 없음된" 이름을 표시 하는 데스크톱 분석 장치 목록](media/unknown-device-name.png)

이 옵션을 구성 하려면 데스크톱 분석을 위해 Configuration Manager 설정에는 옵션이 제공 됩니다. **장치 이름을 진단 데이터의 허용**합니다. 이 Configuration Manager 설정은 AllowDeviceNameInTelemetry Windows 정책 설정 제어.
 

### <a name="conflict-resolution"></a>충돌 해결

일반적으로 Configuration Manager 컬렉션을 사용 하 여 데스크톱 분석 설정 및 등록을 대상으로 합니다. 직접 멤버 자격 또는 쿼리를 사용 하 여 포함 하거나 컬렉션에서 장치를 제외 합니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.

Configuration Manager는만 값이 존재 하지 않는 경우 Windows 설정을 구성 합니다. 장치의 고유 그룹에 대 한 다른 설정을 구성 해야 하는 경우 사용할 수 있습니다 [그룹 정책](#windows-settings)합니다. 그룹 정책에서 대상으로 하는 설정 구성 관리자 설정 보다 우선 합니다.

Windows Analytics와 데스크톱 Analytics 설정 사용 하 여 Configuration Manager 클라이언트를 대상으로 하는 경우 데스크톱 분석에 대 한 설정이 우선 합니다.

진단 데이터 수준에서 구성 된 장치에 대 한 상한을 설정 합니다. Windows 10, 버전 1803 이상에서 기본적으로 사용자 하위 수준을 설정할 수 있습니다. 그룹 정책 설정을 사용 하 여이 동작을 제어할 수 있습니다 **원격 분석 옵트인 설정 사용자 인터페이스 구성**합니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.



## <a name="next-steps"></a>다음 단계

데스크톱 분석에서 배포 계획을 만드는 다음 문서로 계속 진행 하세요.
> [!div class="nextstepaction"]  
> [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
