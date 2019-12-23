---
title: 연결 상태 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager에서 Desktop Analytics의 연결 상태와 디바이스 상태를 모니터링하는 방법에 대한 세부 정보입니다.
ms.date: 10/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1f4e26f7-42f2-40c8-80cf-efd405349c6c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82cfcab2add617f21d4d2bbec483ab8532e9b90b
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75197951"
---
# <a name="monitor-connection-health"></a>연결 상태 모니터링

Configuration Manager의 **연결 상태** 대시보드를 사용하여 디바이스 상태별로 범주를 드릴다운합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **Desktop Analytics Servicing** 노드를 확장하고 **연결 상태** 대시보드를 선택합니다.  

![Configuration Manager 연결 상태 대시보드의 스크린샷](media/connection-health-dashboard.png)

Desktop Analytics를 처음 설정하는 경우 해당 차트에는 완전한 데이터가 표시되지 않을 수 있습니다. 활성 디바이스에서 진단 데이터를 Desktop Analytics 서비스로 전송하고, 서비스에서 데이터를 처리하여 Configuration Manager 사이트와 동기화하는 데 2~3일이 소요될 수 있습니다.<!-- 4098037 -->


## <a name="connection-details"></a>연결 세부 정보

이 타일에는 Configuration Manager에서 Desktop Analytics로의 연결에 대한 다음과 같은 기본 정보가 표시됩니다.

- **테넌트 이름**: **Azure 서비스** 노드에서 Desktop Analytics 연결의 이름

- **대상 컬렉션**: Desktop Analytics에 Configuration Manager를 연결할 때 지정한 동일한 *대상 컬렉션*입니다. 이 컬렉션에는 Configuration Manager가 상업용 ID 및 진단 데이터 설정으로 구성하는 모든 디바이스가 포함됩니다. Configuration Manager가 Desktop Analytics 서비스에 연결하는 전체 디바이스 세트입니다.

- **대상으로 지정된 디바이스**: 대상 컬렉션에 있는 모든 디바이스로, 다음 유형의 디바이스를 제외합니다.

    - 서비스 해제됨
    - 사용되지 않음
    - 비활성
    - 관리되지 않음
    - LTSC(장기 서비스 채널) 버전의 Windows 10을 실행하는 디바이스
    - Windows Server를 실행하는 디바이스

    해당 디바이스 상태에 대한 자세한 내용은 [클라이언트 상태 정보](/sccm/core/clients/manage/monitor-clients#bkmk_about)를 참조하세요.

    > [!Note]  
    > Configuration Manager는 서비스가 해제되고 사용되지 않는 클라이언트를 제외하고 대상 컬렉션의 모든 디바이스를 Desktop Analytics로 업로드합니다.

- **DA에 적격한 디바이스**: 대상 디바이스에서 Desktop Analytics에 적격이 아닌 디바이스를 뺀 수입니다. 예를 들어, Windows Server 또는 Windows 10 LTSC(장기 서비스 채널)를 실행하는 대상 컬렉션의 디바이스입니다.


## <a name="last-sync-details"></a>마지막 동기화 세부 정보

이 타일은 Configuration Manager가 Desktop Analytics 클라우드 서비스와 동기화되는 시기 및 동기화할 디바이스 수를 보여줍니다.

- **디바이스가 동기화됨**: Configuration Manager가 Desktop Analytics에 전송한 적격 디바이스의 수입니다. 서비스는 현재 표시되는 스냅샷에 해당 디바이스를 포함합니다.

- **마지막 서비스 동기화**: Desktop Analytics 포털에서 **마지막으로 업데이트된** 시간과 동일합니다.

- **다음 서비스 동기화**: Desktop Analytics에서 다음 일별 스냅샷을 예상할 수 있는 시기입니다.

> [!Note]  
> Desktop Analytics에 처음으로 디바이스를 등록하는 경우 데이터를 업로드하고 처리하는 데 며칠이 걸릴 수 있습니다. 이 시간 동안 **마지막 동기화 세부 정보** 타일이 빈 상태로 표시될 수 있습니다. 또한 주문형 스냅샷을 요청할 때 이 타일의 값이 자동으로 업데이트되지 않습니다. 자세한 내용은 [데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조하세요.

일부 디바이스가 Desktop Analytics에 표시되지 않는다고 생각되는 경우 Desktop Analytics에서 디바이스를 지원하는지 확인하세요. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.


## <a name="connection-health"></a>연결 상태

**연결 상태** 차트는 다음 성능 상태의 디바이스 수를 표시합니다.  

- [제대로 등록됨](#properly-enrolled): 디바이스는 Desktop Analytics에서 완전한 인벤토리로 표시됩니다.
- [등록할 수 없음](#unable-to-enroll): 디바이스 등록을 막는 차단 문제가 있습니다.
- [구성 경고](#configuration-alert): 디바이스가 Desktop Analytics에 표시되지 않거나 불완전한 인벤토리가 표시됩니다. 또한 Configuration Manager가 디바이스 등록의 문제를 식별했습니다.
- [등록 대기 중](#awaiting-enrollment): Configuration Manager가 디바이스를 구성했지만 Desktop Analytics에 아직 표시되지 않습니다.
- [상태 보류 중](#status-pending): Configuration Manager가 여전히 이 디바이스를 구성하고 있거나, 디바이스에서 해당 상태를 확인할 수 있는 충분한 데이터를 얻지 못합니다.
- [누락된 데이터](#missing-data): Configuration Manager가 디바이스를 구성했지만 Desktop Analytics에 부분 데이터만 있습니다.

<!-- 
- [Configuration issues](#configuration-issues)  
- [Client not installed](#client-not-installed)  
- [Waiting for enrollment](#waiting-for-enrollment)  
- [Missing prerequisites](#missing-prerequisites)  
 -->

이 차트의 총 디바이스 수는 연결 세부 정보 타일에서 **DA에 적격한 디바이스** 값과 동일해야 합니다.

차트에서 조각을 선택하여 해당 상태의 디바이스 목록으로 드릴다운합니다. 자세한 내용은 [디바이스 목록](#device-list)을 참조하세요.

범례에서 범주 이름을 선택하여 차트에서 제거하거나 추가합니다. 이 작업을 사용하면 더 작은 세그먼트의 상대적 크기를 확인할 수 있도록 차트를 확대/축소할 수 있습니다.

### <a name="properly-enrolled"></a>제대로 등록됨

디바이스에는 다음과 같은 특성이 있습니다.

- 구성 관리자 클라이언트 버전 1902 이상  
- 구성 오류 없음  
- Desktop Analytics가 지난 28일 동안 이 디바이스에서 전체 진단 데이터를 받음  
- Desktop Analytics에 디바이스 구성 및 설치된 앱의 전체 인벤토리가 있음  

### <a name="unable-to-enroll"></a>등록할 수 없음

Configuration Manager가 디바이스 등록을 방해하는 하나 이상의 차단 문제를 감지합니다. 자세한 내용은 [Configuration Manager의 Desktop Analytics 디바이스 속성 목록](#bkmk_config-issues)을 참조하세요.  

예를 들어 구성 관리자 클라이언트는 버전 1902(5.0.8790) 이상이 아닙니다. 클라이언트를 최신 버전으로 업데이트합니다. Configuration Manager 사이트에 대해 자동 클라이언트 업그레이드를 사용하도록 설정하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  

### <a name="configuration-alert"></a>구성 경고

디바이스가 Desktop Analytics에 표시되지 않거나 불완전한 인벤토리가 표시됩니다. 또한 Configuration Manager가 디바이스 등록의 문제를 식별했습니다. 자세한 내용은 [Configuration Manager의 Desktop Analytics 디바이스 속성 목록](#bkmk_config-issues)을 참조하세요.

예를 들어 디바이스가 서비스에 연결되어 있지 않습니다. 자세한 내용은 [Windows 진단 엔드포인트 연결](#windows-diagnostic-endpoint-connectivity)을 참조하세요.

### <a name="awaiting-enrollment"></a>등록 대기 중

Desktop Analytics에 이 디바이스에 대한 진단 데이터가 없습니다. 이 문제는 최근에 대상 컬렉션에 디바이스를 추가하고 데이터를 아직 보내지 않았기 때문에 발생할 수 있습니다. 또한 디바이스가 서비스와 제대로 통신하지 않고 최신 진단 데이터가 28일이 넘은 것일 수 있습니다.

디바이스가 서비스와 통신할 수 있는지 확인합니다. 자세한 내용은 [엔드포인트](/sccm/desktop-analytics/enable-data-sharing#endpoints)를 참조하세요.  

### <a name="status-pending"></a>상태 보류 중

Configuration Manager가 여전히 이 디바이스를 구성하고 있거나, 디바이스에서 해당 상태를 확인할 수 있는 충분한 데이터를 얻지 못합니다.

### <a name="missing-data"></a>누락된 데이터

Configuration Manager가 성공적으로 디바이스를 구성했지만 Desktop Analytics에서 호환성 평가를 만들 수 없습니다. 디바이스 구성(인구 조사) 또는 설치된 앱(인벤토리)에 대한 전체 데이터 세트가 없습니다.

이 문제는 디바이스를 다시 시도할 때 자동으로 수정되는 경우가 많습니다. 문제가 지속되면 디바이스가 서비스와 통신할 수 있는지 확인합니다. 자세한 내용은 [엔드포인트](/sccm/desktop-analytics/enable-data-sharing#endpoints)를 참조하세요.  


## <a name="device-list"></a>디바이스 목록

상태별로 특정 디바이스 목록을 보려면 **연결 상태** 대시보드에서 시작합니다. **연결 상태** 타일 중 하나를 선택하고 이 상태에서 디바이스 목록으로 드릴다운합니다. 이 사용자 지정 디바이스 보기에는 기본적으로 다음의 Desktop Analytics 열이 표시됩니다.

- 상업용 ID 구성
- 최소 호환성 업데이트
- Windows 진단 데이터 옵트인
- Windows 상용 데이터 옵트인
- Windows 진단 엔드포인트 연결

> [!Note]  
> **Office 진단 엔드포인트 연결**용 열은 무시합니다. 향후 기능을 위해 예약되어 있습니다.

해당 열은 디바이스가 Desktop Analytics와 통신할 수 있도록 해주는 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)에 해당합니다.

![적절하게 등록된 디바이스 목록의 스크린샷](media/sccm-device-list-properly-enrolled.png)

디바이스를 선택하면 세부 정보 창에서 사용 가능한 속성의 전체 목록이 표시됩니다. 해당 속성을 디바이스 목록에 열로 추가할 수도 있습니다.


## <a name="bkmk_config-issues"></a> 디바이스 속성

다음 Desktop Analytics 디바이스 속성은 Configuration Manager 디바이스 목록에서 열로 사용할 수 있습니다.

- [평가자 구성](#appraiser-configuration)  
- [최소 호환성 업데이트](#minimum-compatibility-update)  
- [평가자 버전](#appraiser-version)  
- [마지막으로 성공한 평가자의 전체 실행](#last-successful-full-run-of-appraiser)  
- [평가자 데이터 수집](#appraiser-data-collection)  
- [마지막으로 성공한 전체 인구 조사 실행](#last-successful-full-run-of-census)  
- [인구 조사 데이터 수집](#census-data-collection)  
- [Windows 진단 엔드포인트 연결](#windows-diagnostic-endpoint-connectivity)  
- [최종 사용자 진단 데이터 확인](#check-end-user-diagnostic-data)  
- [사용자 프록시 확인](#check-user-proxy)  
- [상업용 ID 구성](#commercial-id-configuration)  
- [Windows 상용 데이터 옵트인](#windows-commercial-data-opt-in)  
- [진단 데이터의 디바이스 이름 확인](#check-device-name-in-diagnostic-data)  
- [DiagTrack 서비스 구성](#diagtrack-service-configuration)  
- [DiagTrack 버전](#diagtrack-version)  
- [SQM ID 검색](#sqm-id-retrieval)  
- [고유한 디바이스 식별자 검색](#unique-device-identifier-retrieval)  
- [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)  

> [!Note]  
> **Office 진단 엔드포인트 연결**용 속성 및 **Office 진단 데이터 옵트인**을 무시합니다. 향후 기능을 위해 예약되어 있습니다.

연결 상태 대시보드의 **가장 자주 발생하는 등록 차단기 및 구성 경고** 타일은 디바이스가 주로 문제로 보고하는 속성을 표시합니다.

### <a name="appraiser-configuration"></a>평가자 구성

<!--20,21-->
평가자는 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)에 해당하는 Windows 구성 요소입니다. 최신 버전의 Windows와의 호환성을 위해 디바이스의 앱과 드라이버를 평가합니다. 

이 확인이 성공적으로 완료되면 디바이스에서 평가자 구성 요소가 올바르게 구성된 것입니다.

그렇지 않으면 다음 오류 중 하나가 표시될 수 있습니다.

- 디바이스 앱 호환성 데이터 수집(SetRequestAllAppraiserVersions)을 구성할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.  

- 디바이스 앱 호환성 데이터 수집(SetRequestAllAppraiserVersions)을 구성할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.  

- RequestAllAppraiserVersions을 레지스트리 키 `HKLM:\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\AppCompatFlags\Appraiser`로 쓸 수 없습니다. 사용 권한 확인  

이 레지스트리 키에 대한 사용 권한을 확인합니다. 구성 관리자 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서 이 키에 액세스할 수 있는지 확인합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  

### <a name="minimum-compatibility-update"></a>최소 호환성 업데이트

<!--18,19,32-->
호환성 업데이트(appraiser.dll)가 디바이스에 설치되어 있지 않거나 만료되지 않았습니다. Desktop Analytics 10.0.17763에 대한 최소 요구 사항보다 더 이전입니다.

최신 호환성 업데이트를 설치합니다. 자세한 내용은 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)를 참조하세요.

### <a name="appraiser-version"></a>평가자 버전

이 속성은 디바이스에서 평가자 구성 요소의 현재 버전을 표시합니다. 소수점을 포함하지 않고 `%windir%\System32\appraiser.dll`의 파일 버전을 표시합니다. 예를 들어 파일 버전 10.0.17763은 10017763으로 표시됩니다.

### <a name="last-successful-full-run-of-appraiser"></a>마지막으로 성공한 평가자의 전체 실행

이 속성은 디바이스가 평가자를 마지막으로 성공적으로 실행한 날짜 및 시간을 표시합니다.

### <a name="appraiser-data-collection"></a>평가자 데이터 수집

<!--Appraiser run status-->
<!--22,33-->
이 속성은 평가자 구성 요소를 실행하는 Windows의 최신 결과를 표시합니다.

성공하지 않으면 다음 오류 중 하나가 표시될 수 있습니다.

- 앱 호환성 데이터(RunAppraiser)를 수집할 수 없습니다. 자세한 내용은 로그를 확인하세요.  

- 오류 코드로 인해 앱 호환성 데이터 수집(CompatTelRunner.exe)이 종료되었습니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.

다음 파일을 확인하세요. `%windir%\System32\CompatTelRunner.exe` 존재하지 않는 경우 필요한 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)를 다시 설치합니다. 이 파일을 제거하는 다른 시스템 구성 요소(예: 그룹 정책 또는 맬웨어 방지 서비스)가 없는지 확인합니다.

클라이언트의 M365AHandler.log 파일에 다음 오류 중 하나가 포함된 경우:

``` Log
RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x800703F1
RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x80070005
RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x80080005
```

오류를 해결하려면 영향을 받는 클라이언트에서 상승된 Windows PowerShell 콘솔의 다음 명령을 실행합니다.

```PowerShell
# stop associated services
Stop-Service -Name diagtrack #Connected User Experiences and Telemetry
Stop-Service -Name pcasvc #Program Compatibility Assistant Service
Stop-Service -Name dps #Diagnostic Policy Service

# regenerate diagnostic data cache
Remove-Item -Path $Env:WinDir\appcompat\programs\amcache.hve
Remove-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags" -Name AmiHivePermissionsCorrect -Force

# set ASL logging level to output log files in %windir%\temp
New-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags" -Name LogFlags -Value 4 -PropertyType DWord -Force

# restart services
Start-Service -Name diagtrack
Start-Service -Name pcasvc
Start-Service -Name dps
```

### <a name="last-successful-full-run-of-census"></a>마지막으로 성공한 전체 인구 조사 실행

이 속성은 디바이스가 인구 조사를 마지막으로 성공적으로 실행한 날짜 및 시간을 표시합니다.

### <a name="census-data-collection"></a>인구 조사 데이터 수집

<!-- Census run status -->
<!--51,52-->
인구 조사는 디바이스의 인벤토리를 만드는 Windows 구성 요소입니다. 이 인벤토리 데이터는 디바이스 및 해당 구성을 이해하는 데 사용됩니다.

이 속성은 인구 조사 구성 요소를 실행하는 Windows의 최신 결과를 표시합니다.

성공하지 않으면 다음 오류 중 하나가 표시될 수 있습니다.

- 디바이스 및 구성(RunCensus)에 대한 데이터를 수집할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.  

- 디바이스 및 구성 데이터 수집 도구(devicecensus.exe)를 찾을 수 없음  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.

다음 파일을 확인하세요. `%windir%\System32\DeviceCensus.exe` 존재하지 않는 경우 필요한 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)를 다시 설치합니다. 이 파일을 제거하는 다른 시스템 구성 요소(예: 그룹 정책 또는 맬웨어 방지 서비스)가 없는지 확인합니다.

### <a name="windows-diagnostic-endpoint-connectivity"></a>Windows 진단 엔드포인트 연결

<!--12,15-->
이 확인이 성공적으로 완료되면 디바이스는 연결된 사용자 환경 및 원격 분석 엔드포인트(Vortex)에 연결할 수 있습니다.

그렇지 않으면 다음 오류 중 하나가 표시될 수 있습니다.  

- 연결된 사용자 환경 및 원격 분석 엔드포인트(Vortex)에 연결할 수 없습니다. 네트워크/프록시 설정을 확인하세요.  

- 연결된 사용자 환경 및 원격 분석 엔드포인트(CheckVortexConnectivity)에 대한 연결을 확인할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.  

디바이스는 OS 버전에 따라 다음 엔드포인트에 대한 GET 요청으로의 연결을 확인합니다.

| OS 버전 | 엔드포인트 |
|------------|----------|
| - Windows 10 버전 1809 이상<br/>- Windows 10, 버전 1803(2018-09 누적 업데이트 이상 포함) | `https://v10c.events.data.microsoft.com/health/keepalive` |
| 2018-09 이상 누적 업데이트 *미포함* Windows 10, 버전 1803 | `https://v10.events.data.microsoft.com/health/keepalive` |
| Windows 10, 버전 1709 이전 | `https://v10.vortex-win.data.microsoft.com/health/keepalive` |
| Windows 7 또는 Windows 8.1 | `https://vortex-win.data.microsoft.com/health/keepalive` |

디바이스가 서비스와 통신할 수 있는지 확인합니다. 이 검사는 필요한 엔드포인트 중 일부에 대해서만 유효성을 검사합니다. 자세한 내용은 [엔드포인트](/sccm/desktop-analytics/enable-data-sharing#endpoints)를 참조하세요.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  

### <a name="check-end-user-diagnostic-data"></a>최종 사용자 진단 데이터 확인

<!--1004-->
이 검사가 실패하면 사용자가 디바이스에서 낮은 Windows 진단 데이터를 선택했습니다. 또는 충돌하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조하세요.

비즈니스 요구 사항에 따라 그룹 정책을 통해 사용자 선택을 사용하지 않도록 설정할 수 있습니다. 설정을 사용하여 **원격 분석 옵트인 설정 사용자 인터페이스를 구성합니다**. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.

### <a name="check-user-proxy"></a>사용자 프록시 확인

<!--30,35-->
DisableEnterpriseAuthProxy 설정은 Windows 7에 대해 기본적으로 사용하도록 설정됩니다. Windows 8.1 컴퓨터의 경우 Configuration Manager가 DisableEnterpriseAuthProxy 설정을 0(사용 안 함)으로 설정합니다.

이 속성에는 다음과 같은 오류가 표시될 수 있습니다.

- 인증 프록시가 사용되도록 설정되어 있습니다. `HKLM\Software\Policies\Microsoft\Windows\DataCollection`에서 DisableEnterpriseAuthProxy를 0으로 설정합니다.

- 인증 프록시 상태를 확인할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  

이 레지스트리 키에 대한 사용 권한을 확인합니다. 구성 관리자 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서 이 키에 액세스할 수 있는지 확인합니다. 또는 충돌하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조하세요.  

### <a name="commercial-id-configuration"></a>상업용 ID 구성

<!--9, 11, 53-->
Microsoft는 고유한 상업용 ID를 사용하여 디바이스에서 Desktop Analytics 작업 영역으로 정보를 매핑합니다. Desktop Analytics와 Configuration Manager를 통합하는 경우 서비스에서 이 ID에 대해 자동으로 쿼리합니다. Configuration Manager는 Desktop Analytics 설정 대상으로 지정한 클라이언트에 자동으로 이 ID를 적용합니다.

이 확인이 성공적으로 완료되면 디바이스가 상업용 ID로 적절하게 구성됩니다.

그렇지 않으면 다음 오류 중 하나가 표시될 수 있습니다.

- CommercialId를 레지스트리 키 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`으로 쓸 수 없습니다. 사용 권한 확인  

- CommercialId를 레지스트리 키 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`에서 업데이트할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.  

- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`에서 올바른 CommercialId 값을 제공합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  

이 레지스트리 키에 대한 사용 권한을 확인합니다. 구성 관리자 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서 이 키에 액세스할 수 있는지 확인합니다. 또는 충돌하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조하세요.  

디바이스에 다른 ID가 있습니다. 이 레지스트리 키는 그룹 정책에 의해 사용됩니다. Configuration Manager에서 제공하는 ID보다 우선적으로 적용됩니다.  

<a name="bkmk_ViewCommercialID"></a> Desktop Analytics 포털에서 상업용 ID를 보려면 다음 프로시저를 따르세요.

1. Desktop Analytics 포털로 이동하고 전역 설정 그룹에서 **연결된 서비스**를 선택합니다.  

2. **연결된 서비스** 창에서 **디바이스 등록** 창이 기본적으로 선택되어 있습니다. 디바이스 등록 창의 정보 섹션에는 상업용 ID 키가 표시됩니다.  

![Desktop Analytics 포털의 상업용 ID 스크린샷](media/commercial-id.png)

> [!Important]  
> 현재 항목을 사용할 수 없는 경우에만 **새 ID 키 가져옵니다**. 상업용 ID를 다시 생성하는 경우 [새 ID를 사용하여 디바이스를 다시 등록하세요](/sccm/desktop-analytics/enroll-devices#device-enrollment). 이 프로세스로 인해 전환하는 동안 진단 데이터가 손실될 수 있습니다.  

### <a name="windows-commercial-data-opt-in"></a>Windows 상용 데이터 옵트인

<!--64-->
이 속성은 Windows 7 또는 Windows 8.1을 실행하는 디바이스에만 적용됩니다. CommercialDataOptIn 값을 제외하고 [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)과 유사한 테스트를 실행합니다.

### <a name="check-device-name-in-diagnostic-data"></a>진단 데이터의 디바이스 이름 확인

<!--56,58-->
이 확인이 성공적으로 완료되면 디바이스가 디바이스 이름을 공유하도록 적절하게 구성됩니다.

그렇지 않으면 다음 오류 중 하나가 표시될 수 있습니다.

- Windows 진단 데이터의 일부로 Microsoft에 보낼 디바이스 이름을 확인할 수 없습니다. 예외 세부 정보에 대한 로그를 확인합니다.  

- AllowDeviceNameInTelemetry를 레지스트리 키 `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`에 쓸 수 없습니다. 사용 권한 확인  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  

이 레지스트리 키에 대한 사용 권한을 확인합니다. 구성 관리자 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서 이 키에 액세스할 수 있는지 확인합니다. 또는 충돌하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조하세요.  

그룹 정책과 같은 다른 정책 메커니즘이 이 설정을 사용하지 않도록 설정되어 있는지 확인합니다.

### <a name="diagtrack-service-configuration"></a>DiagTrack 서비스 구성

<!--44,45,50-->
이 확인이 성공적으로 완료되면 디바이스에서 DiagTrack 구성 요소가 올바르게 구성된 것입니다. Desktop Analytics에 필요한 최소 버전은 10010586(10.0.10586)입니다.

그렇지 않으면 다음 오류 중 하나가 표시될 수 있습니다.

- 연결된 사용자 환경 및 원격 분석(diagtrack.dll) 구성 요소가 오래되었습니다. 요구 사항 확인  

- 연결된 사용자 환경 및 원격 분석(diagtrack.dll) 구성 요소를 찾을 수 없습니다. 요구 사항 확인  

- 연결된 사용자 환경 및 원격 분석 서비스를 사용하도록 설정하고 시작하여 Microsoft로 데이터를 보냅니다.  

<!--
 - An updated Connected User Experience and Telemetry (diagtrack.dll) component is available. Check requirements - this is for the newer version that improves performance
 -->

<!--include something about diagtrack perf update https://go.microsoft.com/fwlink/?linkid=2011593-->

최신 업데이트를 설치합니다. 자세한 내용은 [디바이스 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)를 참조하세요.

디바이스에서 **연결된 사용자 환경 및 원격 분석** 서비스가 실행 중인지 확인합니다.

### <a name="diagtrack-version"></a>DiagTrack 버전

이 속성은 디바이스에 연결된 사용자 환경 및 원격 분석 구성 요소의 현재 버전을 표시합니다. 소수점을 포함하지 않고 `%windir%\System32\diagtrack.dll`의 파일 버전을 표시합니다. 예를 들어 파일 버전 10.0.10586은 10010586으로 표시됩니다.

### <a name="sqm-id-retrieval"></a>SQM ID 검색

<!--38-->
이 속성은 주로 Windows 7 디바이스에 대한 것입니다. 이후 OS 버전에서는 디바이스에 대한 대체 식별자로 사용할 수 있습니다.

성공하지 않으면 다음 오류가 표시될 수 있습니다.

- 레거시 디바이스 원격 분석 식별자(SQM ID)를 검색할 수 없습니다.

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  

사용자 환경에 중복된 ID가 없는지 확인합니다. 예를 들어, 일반화되지 않은 OS 이미지를 사용하여 디바이스를 배포한 경우입니다.

### <a name="unique-device-identifier-retrieval"></a>고유한 디바이스 식별자 검색

<!--54-->
Desktop Analytics에서는 Microsoft 계정 서비스를 사용하여 더 안정적인 디바이스 ID를 사용합니다.

**Microsoft 계정 로그인 도우미** 서비스를 사용하지 않도록 설정했는지 확인합니다. 시작 유형은 **수동(트리거 시작)** 이어야 합니다.

최종 사용자 Microsoft 계정 액세스를 사용하지 않도록 설정하려면 이 엔드포인트를 차단하는 대신 정책 설정을 사용합니다. 자세한 내용은 [Enterprise의 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)을 참조하세요.

### <a name="windows-diagnostic-data-opt-in"></a>Windows 진단 데이터 옵트인

<!--8,40,55,62-->
이 속성은 Windows에서 진단 데이터를 허용하도록 제대로 구성되어 있는지 확인합니다. 다음 레지스트리 키에서 AllowTelemetry 분석값을 확인합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

레지스트리 키에 대한 사용 권한을 확인합니다. 구성 관리자 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서 키에 액세스할 수 있는지 확인합니다. 또는 충돌하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조하세요.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토하세요.  



## <a name="see-also"></a>참고 항목

[Desktop Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)
