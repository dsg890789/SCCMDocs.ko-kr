---
title: 연결 상태 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager에서 데스크톱 분석의 연결 상태와 장치 상태를 모니터링 하는 방법에 대 한 세부 정보입니다.
ms.date: 06/11/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1f4e26f7-42f2-40c8-80cf-efd405349c6c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3406c0fff57a1ecef24a045e3061417fc5fac46c
ms.sourcegitcommit: e0438c191df945305625ae91596c9417d16e8510
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68491651"
---
# <a name="monitor-connection-health"></a>연결 상태 모니터링

Configuration Manager의 **연결 상태** 대시보드를 사용 하 여 장치 상태별로 범주를 드릴 다운 합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **데스크톱 분석 서비스** 노드를 확장 하 고 **연결 상태** 대시보드를 선택 합니다.  

![Configuration Manager 연결 상태 대시보드의 스크린샷](media/connection-health-dashboard.png)

데스크톱 분석을 처음 설정 하는 경우 이러한 차트에는 완전 한 데이터가 표시 되지 않을 수 있습니다. 활성 장치에서 진단 데이터를 데스크톱 분석 서비스, 데이터를 처리 하는 서비스, Configuration Manager 사이트와 동기화 하는 데 2-3 일이 소요 될 수 있습니다.<!-- 4098037 -->


## <a name="connection-details"></a>연결 정보

이 타일에는 Configuration Manager에서 데스크톱 분석으로의 연결에 대 한 다음과 같은 기본 정보가 표시 됩니다.

- **테 넌 트 이름**: **Azure 서비스** 노드에서 데스크톱 분석 연결의 이름

- **대상 컬렉션**: 데스크톱 분석에 Configuration Manager 연결할 때 지정한 *대상 컬렉션* 입니다. 이 컬렉션에는 상업적 ID 및 진단 데이터 설정 Configuration Manager 구성 하는 모든 장치가 포함 됩니다. Configuration Manager는 데스크톱 분석 서비스에 연결 하는 전체 장치 집합입니다.

- **대상 장치**: 대상 컬렉션에 있는 모든 장치로, 다음 유형의 장치를 제외 합니다.

    - 제거
    - 않게
    - 비활성
    - 관리 되지 않는
    - LTSC (장기 서비스 채널) 버전의 Windows 10을 실행 하는 장치
    - Windows Server를 실행 하는 장치

    이러한 장치 상태에 대 한 자세한 내용은 [클라이언트 상태 정보](/sccm/core/clients/manage/monitor-clients#bkmk_about)를 참조 하세요.

    > [!Note]  
    > 대상 컬렉션의 모든 장치를 제거 하 고 사용 되지 않는 클라이언트를 데스크톱 분석으로 업로드 Configuration Manager 합니다.

- **DA에 적합 한 장치**: 대상 장치에서 데스크톱 분석에 적합 하지 않은 장치를 뺀 수입니다. 예를 들어, Windows Server 또는 Windows 10 장기 서비스 채널 (LTSC)을 실행 하는 대상 컬렉션의 장치입니다.


## <a name="last-sync-details"></a>마지막 동기화 정보

이 타일은 Configuration Manager 데스크톱 분석 클라우드 서비스와 동기화 되는 시기 및 동기화 할 장치 수를 보여 줍니다.

- **동기화 된 장치**: 데스크톱 분석에 전송 Configuration Manager 하는 고유 장치 수입니다. 서비스는 현재 표시 되는 스냅숏에 이러한 장치를 포함 합니다.

- **마지막 서비스 동기화**: 데스크톱 분석 포털에서 **마지막으로 업데이트** 된 시간과 동일 합니다.

- **다음 서비스 동기화**: 데스크톱 분석에서 다음 일별 스냅숏을 예측할 수 있습니다.

> [!Note]  
> 주문형 스냅숏을 요청 하면 이러한 값이 자동으로 업데이트 되지 않습니다. 자세한 내용은 [데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조 하세요.

일부 장치가 데스크톱 분석에 표시 되지 않는다고 생각 되는 경우 데스크톱 분석에서 장치를 지원 하는지 확인 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.


## <a name="connection-health"></a>연결 상태

**연결 상태** 차트는 다음 상태의 장치 수를 표시 합니다.  

- [올바르게 등록](#properly-enrolled)됨: 장치는 데스크톱 분석에서 전체 인벤토리를 사용 하 여 표시 됩니다.
- [등록할 수 없음](#unable-to-enroll): 장치 등록을 차단 하는 차단 문제가 있습니다.
- [구성 경고](#configuration-alert): 장치가 데스크톱 분석에 표시 되지 않거나 불완전 한 인벤토리가 표시 됩니다. 또한 장치 등록 문제를 확인 Configuration Manager.
- [등록 대기](#awaiting-enrollment)중: 장치를 구성 Configuration Manager 데스크톱 분석에 아직 표시 되지 않습니다.
- [보류 중인 상태](#status-pending): 이 장치를 구성 하 고 있거나, 장치에서 해당 상태를 확인할 수 있는 충분 한 데이터가 없는 Configuration Manager
- [누락 된 데이터](#missing-data): 장치를 구성 Configuration Manager 데스크톱 분석에는 부분 데이터만 있습니다.

<!-- 
- [Configuration issues](#configuration-issues)  
- [Client not installed](#client-not-installed)  
- [Waiting for enrollment](#waiting-for-enrollment)  
- [Missing prerequisites](#missing-prerequisites)  
 -->

이 차트의 총 장치 수는 연결 세부 정보 타일의 DA 값 **에 적합 한 장치** 와 동일 해야 합니다.

차트에서 조각을 선택 하 여 해당 상태의 장치 목록으로 드릴 다운 합니다. 자세한 내용은 [장치 목록](#device-list)을 참조 하세요.

범례에서 범주 이름을 선택 하 여 차트에서 제거 하거나 추가 합니다. 이 작업을 사용 하면 더 작은 세그먼트의 상대적 크기를 확인할 수 있도록 차트를 확대/축소할 수 있습니다.

### <a name="properly-enrolled"></a>올바르게 등록 됨

장치에는 다음과 같은 특성이 있습니다.

- Configuration Manager 클라이언트 버전 1902 이상  
- 구성 오류가 없습니다.  
- 데스크톱 분석이 지난 28 일 동안이 장치에서 전체 진단 데이터를 받았습니다.  
- 데스크톱 분석에는 장치 구성 및 설치 된 앱의 전체 인벤토리가 있습니다.  

### <a name="unable-to-enroll"></a>등록할 수 없음

Configuration Manager는 장치 등록을 방해 하는 하나 이상의 차단 문제를 검색 합니다. 자세한 내용은 [Configuration Manager 데스크톱 분석 장치 속성](#bkmk_config-issues)목록을 참조 하십시오.  

예를 들어 Configuration Manager 클라이언트는 버전 1902 (5.0.8790) 이상이 아닙니다. 클라이언트를 최신 버전으로 업데이트 합니다. Configuration Manager 사이트에 대해 자동 클라이언트 업그레이드를 사용 하도록 설정 하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  

### <a name="configuration-alert"></a>구성 경고

장치가 데스크톱 분석에 표시 되지 않거나 불완전 한 인벤토리가 표시 됩니다. 또한 장치 등록 문제를 확인 Configuration Manager. 자세한 내용은 [Configuration Manager 데스크톱 분석 장치 속성](#bkmk_config-issues)목록을 참조 하십시오.

예를 들어 장치는 서비스에 연결 되지 않습니다. 자세한 내용은 [Windows 진단 끝점 연결](#windows-diagnostic-endpoint-connectivity)을 참조 하세요.

### <a name="awaiting-enrollment"></a>등록 대기 중

데스크톱 분석에는이 장치에 대 한 진단 데이터가 없습니다. 이 문제는 최근에 대상 컬렉션에 장치를 추가 하 고 데이터를 아직 보내지 않았기 때문일 수 있습니다. 또한 장치가 서비스와 제대로 통신 하지 않고 최신 진단 데이터가 28 일 이상 오래 된 것일 수 있습니다.

장치가 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)을 참조 하세요.  

### <a name="status-pending"></a>상태 보류 중

이 장치를 구성 하 고 있거나, 장치에서 해당 상태를 확인할 수 있는 충분 한 데이터가 없는 Configuration Manager입니다.

### <a name="missing-data"></a>누락 된 데이터

장치를 구성 Configuration Manager 데스크톱 분석에서 호환성 평가를 만들 수 없습니다. 장치 구성 (인구 조사) 또는 설치 된 앱 (인벤토리)에 대 한 전체 데이터 집합이 없습니다.

이 문제는 장치를 다시 시도할 때 자동으로 수정 되는 경우가 많습니다. 문제가 지속 되 면 장치가 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)을 참조 하세요.  


## <a name="device-list"></a>장치 목록

상태별로 특정 장치 목록을 보려면 **연결 상태** 대시보드에서 시작 합니다. **연결 상태** 타일의 세그먼트 중 하나를 선택 하 고이 상태의 장치 목록으로 드릴 다운 합니다. 이 사용자 지정 장치 보기에는 기본적으로 다음 데스크톱 분석 열이 표시 됩니다.

- 상용 ID 구성
- 최소 호환성 업데이트
- Windows 진단 데이터 옵트인
- Windows 상용 데이터 옵트인
- Windows 진단 끝점 연결

> [!Note]  
> **Office 진단 끝점 연결**에 대 한 열을 무시 합니다. 향후 기능을 위해 예약 되어 있습니다.

이러한 열은 장치에서 데스크톱 분석과 통신할 때 핵심적인 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites) 에 해당 합니다.

![제대로 등록 된 장치 목록의 스크린샷](media/sccm-device-list-properly-enrolled.png)

장치를 선택 하면 세부 정보 창에서 사용 가능한 속성의 전체 목록이 표시 됩니다. 이러한 속성을 장치 목록에 열로 추가할 수도 있습니다.


## <a name="bkmk_config-issues"></a>장치 속성

다음 데스크톱 분석 장치 속성은 Configuration Manager 장치 목록에서 열로 사용할 수 있습니다.

- [평가자 구성](#appraiser-configuration)  
- [최소 호환성 업데이트](#minimum-compatibility-update)  
- [평가자 버전](#appraiser-version)  
- [평가자를 마지막으로 성공한 전체 실행](#last-successful-full-run-of-appraiser)  
- [평가자 데이터 수집](#appraiser-data-collection)  
- [인구 조사를 마지막으로 성공한 전체 실행](#last-successful-full-run-of-census)  
- [인구 조사 데이터 수집](#census-data-collection)  
- [Windows 진단 끝점 연결](#windows-diagnostic-endpoint-connectivity)  
- [최종 사용자 진단 데이터 확인](#check-end-user-diagnostic-data)  
- [사용자 프록시 확인](#check-user-proxy)  
- [상용 ID 구성](#commercial-id-configuration)  
- [Windows 상용 데이터 옵트인](#windows-commercial-data-opt-in)  
- [진단 데이터의 장치 이름 확인](#check-device-name-in-diagnostic-data)  
- [DiagTrack 서비스 구성](#diagtrack-service-configuration)  
- [DiagTrack 버전](#diagtrack-version)  
- [SQM ID 검색](#sqm-id-retrieval)  
- [고유한 장치 식별자 검색](#unique-device-identifier-retrieval)  
- [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)  

> [!Note]  
> **Office 진단 끝점 연결** 및 **office 진단 데이터 옵트인**의 속성을 무시 합니다. 이후 기능을 위해 예약 되어 있습니다.

연결 상태 대시보드의 **가장 빈번한 등록 차단기 및 구성 경고** 타일에는 장치가 주로 문제로 보고 하는 속성이 표시 됩니다.

### <a name="appraiser-configuration"></a>평가자 구성

<!--20,21-->
평가자는 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)에 해당 하는 Windows 구성 요소입니다. 최신 버전의 Windows와의 호환성을 위해 장치의 앱과 드라이버를 평가 합니다. 

이 확인이 성공적으로 완료 되 면 장치에서 평가자 구성 요소가 올바르게 구성 된 것입니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.

- 장치 앱 호환성 데이터 수집 (SetRequestAllAppraiserVersions)을 구성할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 장치 앱 호환성 데이터 수집 (SetRequestAllAppraiserVersions)을 구성할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- RequestAllAppraiserVersions을 레지스트리 키 `HKLM:\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\AppCompatFlags\Appraiser`에 쓸 수 없습니다. 권한 확인  

이 레지스트리 키에 대 한 사용 권한을 확인 하십시오. Configuration Manager 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서이 키에 액세스할 수 있는지 확인 합니다.  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  

### <a name="minimum-compatibility-update"></a>최소 호환성 업데이트

<!--18,19,32-->
호환성 업데이트 (평가자)가 장치에 설치 되어 있지 않거나 만료 되지 않았습니다. 데스크톱 분석 10.0.17763에 대 한 최소 요구 사항 보다 이전 버전입니다.

최신 호환성 업데이트를 설치 합니다. 자세한 내용은 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)를 참조 하세요.

### <a name="appraiser-version"></a>평가자 버전

이 속성은 장치에서 평가자 구성 요소의 현재 버전을 표시 합니다. 소수점이 없는의 `%windir%\System32\appraiser.dll`파일 버전을 표시 합니다. 예를 들어 파일 버전 10.0.17763은 10017763로 표시 됩니다.

### <a name="last-successful-full-run-of-appraiser"></a>평가자를 마지막으로 성공한 전체 실행

이 속성은 장치가 평가자 성공적으로 실행 된 날짜 및 시간을 표시 합니다.

### <a name="appraiser-data-collection"></a>평가자 데이터 수집

<!--Appraiser run status-->
<!--22,33-->
이 속성은 평가자 구성 요소를 실행 하는 Windows의 최신 결과를 표시 합니다.

성공 하지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.

- 앱 호환성 데이터 (RunAppraiser)를 수집할 수 없습니다. 자세한 내용은 로그를 확인 하십시오.  

- 응용 프로그램 호환성 데이터 수집 (CompatTelRunner .exe)이 오류 코드와 함께 종료 되었습니다.  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.

다음 파일 `%windir%\System32\CompatTelRunner.exe`을 확인 합니다. 존재 하지 않는 경우 필요한 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)를 다시 설치 합니다. 이 파일을 제거 하는 다른 시스템 구성 요소 (예: 그룹 정책 또는 맬웨어 방지 서비스)가 없는지 확인 합니다.

클라이언트의 M365AHandler 파일에 다음 오류 중 하나가 포함 된 경우:
```
RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x800703F1
RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x80070005
RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x80080005
```

이러한 오류를 해결 하려면 영향을 받는 클라이언트의 관리자 권한 Windows PowerShell 콘솔에서 다음 명령을 실행 합니다.

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

### <a name="last-successful-full-run-of-census"></a>인구 조사를 마지막으로 성공한 전체 실행

이 속성은 장치가 인구 조사 성공적으로 실행 된 날짜 및 시간을 표시 합니다.

### <a name="census-data-collection"></a>인구 조사 데이터 수집

<!-- Census run status -->
<!--51,52-->
인구 조사는 장치를 인벤토리 하는 Windows 구성 요소입니다. 이 인벤토리 데이터는 장치 및 해당 구성을 이해 하는 데 사용 됩니다.

이 속성은 인구 조사 구성 요소를 실행 하는 Windows의 최신 결과를 표시 합니다.

성공 하지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.

- 장치 및 구성 (RunCensus)에 대 한 데이터를 수집할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 장치 및 구성 데이터 수집 도구 (devicecensus .exe)를 찾을 수 없습니다.  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.

다음 파일 `%windir%\System32\DeviceCensus.exe`을 확인 합니다. 존재 하지 않는 경우 필요한 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)를 다시 설치 합니다. 이 파일을 제거 하는 다른 시스템 구성 요소 (예: 그룹 정책 또는 맬웨어 방지 서비스)가 없는지 확인 합니다.

### <a name="windows-diagnostic-endpoint-connectivity"></a>Windows 진단 끝점 연결

<!--12,15-->
이 확인이 성공적으로 완료 되 면 장치는 연결 된 사용자 환경 및 원격 분석 끝점 (소용돌이)에 연결할 수 있습니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.  

- 연결 된 사용자 환경 및 원격 분석 끝점 (소용돌이)에 연결할 수 없습니다. 네트워크/프록시 설정 확인  

- 연결 된 사용자 환경 및 원격 분석 끝점 (CheckVortexConnectivity)에 대 한 연결을 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

장치는 OS 버전에 따라 다음 끝점에 대 한 GET 요청으로의 연결을 확인 합니다.

| OS 버전 | 엔드포인트 |
|------------|----------|
| 최신 누적 업데이트를 사용 하는 Windows 10, 버전 1803 이상 | `https://v10c.events.data.microsoft.com/health/keepalive` |
| 2018-09 이상 누적 업데이트 없이 Windows 10, 버전 1803 이상 | `https://v10.events.data.microsoft.com/health/keepalive` |
| Windows 10, 버전 1709 이전 | `https://v10.vortex-win.data.microsoft.com/health/keepalive` |
| Windows 7 또는 Windows 8.1 | `https://vortex-win.data.microsoft.com/health/keepalive` |

장치가 서비스와 통신할 수 있는지 확인 합니다. 이 검사는 필요한 끝점 중 일부에 대해서만 유효성을 검사 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)을 참조 하세요.  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  

### <a name="check-end-user-diagnostic-data"></a>최종 사용자 진단 데이터 확인

<!--1004-->
이 검사가 실패 하면 사용자가 장치에서 낮은 Windows 진단 데이터를 선택 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조 하세요.

비즈니스 요구 사항에 따라 그룹 정책을 통해 사용자 선택을 사용 하지 않도록 설정할 수 있습니다. 설정을 사용 하 여 **원격 분석 옵트인 설정 사용자 인터페이스를 구성**합니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.

### <a name="check-user-proxy"></a>사용자 프록시 확인

<!--30,35-->
DisableEnterpriseAuthProxy 설정은 Windows 7에 대해 기본적으로 사용 하도록 설정 됩니다. Windows 8.1 컴퓨터의 경우 DisableEnterpriseAuthProxy 설정을 0 (사용 안 함)으로 설정 Configuration Manager.

이 속성에는 다음과 같은 오류가 표시 될 수 있습니다.

- 인증 프록시를 사용할 수 있습니다. DisableEnterpriseAuthProxy를 0으로 설정 합니다.`HKLM\Software\Policies\Microsoft\Windows\DataCollection`

- 인증 프록시 상태를 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  

이 레지스트리 키에 대 한 사용 권한을 확인 하십시오. Configuration Manager 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서이 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조 하세요.  

### <a name="commercial-id-configuration"></a>상용 ID 구성

<!--9, 11, 53-->
Microsoft는 고유한 상용 ID를 사용 하 여 장치에서 데스크톱 분석 작업 영역으로 정보를 매핑합니다. 데스크톱 분석과 Configuration Manager를 통합 하는 경우 서비스에서이 ID를 자동으로 쿼리 합니다. 이 ID는 데스크톱 분석 설정을 대상으로 하는 클라이언트에 자동으로 적용 Configuration Manager 합니다.

이 확인이 성공적으로 완료 되 면 상업적 ID를 사용 하 여 장치를 적절히 구성 합니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.

- CommercialId을 레지스트리 키 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`에 쓸 수 없습니다. 권한 확인  

- 레지스트리 키 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`에서 CommercialId를 업데이트할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 에서 올바른 CommercialId 값을 제공 합니다.`HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  

이 레지스트리 키에 대 한 사용 권한을 확인 하십시오. Configuration Manager 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서이 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조 하세요.  

장치에 다른 ID가 있습니다. 이 레지스트리 키는 그룹 정책에 의해 사용 됩니다. Configuration Manager에서 제공 하는 ID 보다 우선적으로 적용 됩니다.  

<a name="bkmk_ViewCommercialID"></a>데스크톱 분석 포털에서 상업용 ID를 보려면 다음 절차를 따르십시오.

1. 데스크톱 분석 포털로 이동 하 고 전역 설정 그룹에서 **연결 된 서비스** 를 선택 합니다.  

2. **연결 된 서비스** 창에서 **장치 등록** 창이 기본적으로 선택 되어 있습니다. 장치 등록 창의 정보 섹션에는 상업용 ID 키가 표시 됩니다.  

![데스크톱 분석 포털의 상용 ID 스크린샷](media/commercial-id.png)

> [!Important]  
> 현재 항목을 사용할 수 없는 경우에만 **새 ID 키를 가져옵니다** . 상용 ID를 다시 생성 하는 경우 [새 id를 사용 하 여 장치를 다시 등록](/sccm/desktop-analytics/enroll-devices#device-enrollment)합니다. 이 프로세스로 인해 전환 하는 동안 진단 데이터가 손실 될 수 있습니다.  

### <a name="windows-commercial-data-opt-in"></a>Windows 상용 데이터 옵트인

<!--64-->
이 속성은 Windows 7 또는 Windows 8.1를 실행 하는 장치에만 적용 됩니다. CommercialDataOptIn 값을 제외 하 고 [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)과 비슷한 테스트를 실행 합니다.

### <a name="check-device-name-in-diagnostic-data"></a>진단 데이터의 장치 이름 확인

<!--56,58-->
이 확인이 성공적으로 완료 되 면 장치 이름을 공유 하도록 장치가 올바르게 구성 된 것입니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.

- Windows 진단 데이터의 일부로 Microsoft로 전송할 장치 이름을 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- AllowDeviceNameInTelemetry을 레지스트리 키 `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`에 쓸 수 없습니다. 권한 확인  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  

이 레지스트리 키에 대 한 사용 권한을 확인 하십시오. Configuration Manager 클라이언트가 설정할 수 있도록 로컬 시스템 계정에서이 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조 하세요.  

그룹 정책과 같은 다른 정책 메커니즘이이 설정을 사용 하지 않도록 설정 되어 있는지 확인 합니다.

### <a name="diagtrack-service-configuration"></a>DiagTrack 서비스 구성

<!--44,45,50-->
이 확인이 성공적으로 완료 되 면 장치에서 DiagTrack 구성 요소가 올바르게 구성 된 것입니다. 데스크톱 분석에 필요한 최소 버전은 10010586 (10.0.10586)입니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다.

- 연결 된 사용자 환경 및 원격 분석 (diagtrack) 구성 요소가 오래 되었습니다. 요구 사항 확인  

- 연결 된 사용자 환경 및 원격 분석 (diagtrack) 구성 요소를 찾을 수 없습니다. 요구 사항 확인  

- 연결 된 사용자 환경 및 원격 분석 서비스를 사용 하도록 설정 하 고 시작 하 여 Microsoft로 데이터 보내기  

<!--
 - An updated Connected User Experience and Telemetry (diagtrack.dll) component is available. Check requirements - this is for the newer version that improves performance
 -->

<!--include something about diagtrack perf update https://go.microsoft.com/fwlink/?linkid=2011593-->

최신 업데이트를 설치 합니다. 자세한 내용은 [장치 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)를 참조 하세요.

장치에서 연결 된 **사용자 환경 및 원격 분석** 서비스가 실행 중인지 확인 합니다.

### <a name="diagtrack-version"></a>DiagTrack 버전

이 속성은 장치에 연결 된 사용자 환경 및 원격 분석 구성 요소의 현재 버전을 표시 합니다. 소수점이 없는의 `%windir%\System32\diagtrack.dll`파일 버전을 표시 합니다. 예를 들어 파일 버전 10.0.10586은 10010586로 표시 됩니다.

### <a name="sqm-id-retrieval"></a>SQM ID 검색

<!--38-->
이 속성은 주로 Windows 7 장치에 대 한 것입니다. 이후 OS 버전에서 장치에 대 한 대체 식별자로 사용할 수 있습니다.

성공 하지 않으면 다음 오류가 표시 될 수 있습니다.

- 레거시 장치 원격 분석 식별자 (SQM ID)를 검색할 수 없습니다.

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  

사용자 환경에 중복 된 Id가 없는지 확인 합니다. 예를 들어, 일반화 되지 않은 OS 이미지를 사용 하 여 장치를 배포한 경우입니다.

### <a name="unique-device-identifier-retrieval"></a>고유한 장치 식별자 검색

<!--54-->
데스크톱 분석에서는 Microsoft 계정 서비스를 사용 하 여 보다 안정적인 장치 id를 사용 합니다.

**Microsoft 계정 로그인 도우미** 서비스를 사용 하지 않도록 설정 해야 합니다. 시작 유형은 **수동 (트리거 시작)** 이어야 합니다.

최종 사용자 Microsoft 계정 액세스를 사용 하지 않도록 설정 하려면이 끝점을 차단 하는 대신 정책 설정을 사용 합니다. 자세한 내용은 [엔터프라이즈의 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)을 참조 하세요.

### <a name="windows-diagnostic-data-opt-in"></a>Windows 진단 데이터 옵트인

<!--8,40,55,62-->
이 속성은 Windows에서 진단 데이터를 허용 하도록 제대로 구성 되어 있는지 확인 합니다. 다음 레지스트리 키에서 AllowTelemetry 분석 값을 확인 합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

이러한 레지스트리 키에 대 한 사용 권한을 확인 합니다. Configuration Manager 클라이언트가를 설정 하기 위해 로컬 시스템 계정이 이러한 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)을 참조 하세요.  

자세한 내용은 클라이언트에서 M365AHandler를 검토 하십시오.  



## <a name="see-also"></a>참고자료

[Desktop Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)
