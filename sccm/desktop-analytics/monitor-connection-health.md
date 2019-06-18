---
title: 연결 상태 모니터링
titleSuffix: Configuration Manager
description: 데스크톱 분석 in Configuration Manager에 대 한 연결 상태 및 장치 상태를 모니터링 하는 방법에 대 한 세부 정보입니다.
ms.date: 06/11/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1f4e26f7-42f2-40c8-80cf-efd405349c6c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c5d2af3cf97d6093037e248eff3447035ff413f
ms.sourcegitcommit: 659976b943226c5124057429ac7444989f98433f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67159064"
---
# <a name="monitor-connection-health"></a>연결 상태 모니터링

사용 된 **연결 상태** 장치 상태별으로 범주로 드릴 다운 하려면 Configuration Manager의 대시보드. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **데스크톱 분석 서비스** 노드를 선택한는 **연결 상태** 대시보드입니다.  

![Configuration Manager 연결 상태 대시보드의 스크린 샷](media/connection-health-dashboard.png)

데스크톱 Analytics를 처음 설치할 때 이러한 차트는 전체 데이터를 표시 되지 않습니다. 데스크톱 분석 서비스, 데이터를 처리 하 여 Configuration Manager 사이트를 사용 하 여 다음 동기화 서비스에 진단 데이터 보내기에 대 한 활성 장치에 대해 2 ~ 3 일 걸릴 수 있습니다.<!-- 4098037 -->


## <a name="connection-details"></a>연결 세부 정보

이 타일에는 Configuration Manager에서 데스크톱 Analytics에 연결 하는 방법에 대 한 기본 정보를 표시합니다.

- **테 넌 트 이름**: 데스크톱 Analytics 연결의 이름을 합니다 **Azure Services** 노드

- **대상 컬렉션**: 동일 *컬렉션을 대상* 데스크톱 Analytics에 Configuration Manager를 연결 하는 경우를 지정 합니다. 이 컬렉션에 진단 데이터 설정과 상업용 ID를 사용 하 여 Configuration Manager를 구성 하는 모든 장치를 포함 합니다. Configuration Manager에서 데스크톱 Analytics 서비스에 연결 하는 장치의 전체 집합은

- **대상 장치**: 모든 장치 유형은 빼기 대상 컬렉션의 장치:

    - 서비스 해제
    - 사용 되지 않음
    - 비활성
    - 관리 되지 않는

    이러한 장치 상태에 대 한 자세한 내용은 참조 하세요. [클라이언트 상태에 대 한](/sccm/core/clients/manage/monitor-clients#bkmk_about)합니다.

    > [!Note]  
    > Configuration Manager 데스크톱 Analytics에 업로드 모든 폐기 및 사용 되지 않는 클라이언트에서 뺀 대상 컬렉션의 장치입니다.

- **장치 DA 적합**: 빼기 데스크톱 분석에 적합 하지 않은 장치를 대상으로 하는 장치 수입니다. 예를 들어, 대상 컬렉션에서 실행 하는 장치 Windows Server 또는 Windows 10 장기 서비스 채널 (LTSC).


## <a name="last-sync-details"></a>마지막 동기화 세부 정보

이 타일에 표시 하면 Configuration Manager와 동기화 데스크톱 분석 클라우드 서비스 및 장치 수가 나타나며가 동기화 합니다.

- **동기화 된 장치**: Configuration Manager 데스크톱 Analytics로 전송 하는 고유 장치 수입니다. 서비스는 현재 표시 되는 스냅숏의 이러한 장치를 포함합니다.

- **마지막 서비스 동기화**: 와 동일 합니다 **마지막으로 업데이트** 데스크톱 Analytics 포털에서 시간입니다.

- **다음 동기화 서비스**: 경우 데스크톱 Analytics에서 일일 스냅숏은 다음을 기대할 수 있습니다.

> [!Note]  
> 이러한 값는 주문형 스냅숏을 요청할 때 자동으로 업데이트 합니다. 자세한 내용은 [의 데이터 대기 시간이](/sccm/desktop-analytics/troubleshooting#data-latency)합니다.

일부 장치를 데스크톱 Analytics에서 표시 하지 않는 경우 데스크톱 분석 하 여 장치를 지원 하는지 확인 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.


## <a name="connection-health"></a>연결 상태

합니다 **연결 상태** 차트는 다음 상태에서 장치 수를 표시 합니다.  

- [제대로 등록](#properly-enrolled): 장치가 전체 인벤토리를 사용 하 여 데스크톱 분석에 표시합니다.
- [등록할 수 없습니다](#unable-to-enroll): 장치 등록을 방지 하는 차단 문제
- [구성 경고](#configuration-alert): 데스크톱 분석에 표시 되지 않으면 장치나 불완전 한 인벤토리를 사용 하 여 표시 됩니다. 또한 configuration Manager는 장치 등록을 사용 하 여 문제를 식별 합니다.
- [대기 중 등록](#awaiting-enrollment): Configuration Manager 장치를 구성 하지만 데스크톱 Analytics에서 아직 표시 되지
- [상태 보류 됨](#status-pending): Configuration Manager 구성 하는 것이 장치를 여전히 또는 해당 상태를 확인 하려면 장치에서 충분 한 데이터가 없습니다.
- [누락 된 데이터](#missing-data): Configuration Manager 장치를 구성 하지만 일부 데이터는 권한만 보유 하는 데스크톱 분석

<!-- 
- [Configuration issues](#configuration-issues)  
- [Client not installed](#client-not-installed)  
- [Waiting for enrollment](#waiting-for-enrollment)  
- [Missing prerequisites](#missing-prerequisites)  
 -->

이 차트에서 장치의 총 수와 동일 해야 합니다 **DA 적합 장치** 연결 세부 정보 타일에는 값입니다.

해당 상태를 사용 하 여 장치 목록으로 드릴 다운 하려면 차트의 조각을 선택 합니다. 자세한 내용은 [장치 목록](#device-list)합니다.

차트에서 추가 하거나 제거 하려면 범례에 범주 이름을 선택 합니다. 이 작업을 더 작은 세그먼트의 상대 크기를 볼 수 있도록 차트를 확대/축소 수 있습니다.

### <a name="properly-enrolled"></a>제대로 등록

장치에는 다음 특성이 있습니다.

- Configuration Manager 클라이언트 버전 1902 이상  
- 구성 오류가 없음을  
- 데스크톱 분석 지난 28 일 동안에서이 장치에서 전체 진단 데이터를 수신  
- 데스크톱 장치 구성의 전체 인벤토리를가 분석과 설치 된 앱  

### <a name="unable-to-enroll"></a>등록할 수 없습니다.

Configuration Manager에서 장치 등록을 방지 하는 하나 이상의 차단 문제를 감지 합니다. 자세한 내용은 목록을 참조 하세요 [Configuration Manager의 분석 데스크톱 장치 속성](#bkmk_config-issues)합니다.  

예를 들어 Configuration Manager 클라이언트 되지 이상 버전 1902 (5.0.8790). 최신 버전으로 클라이언트를 업데이트 합니다. Configuration Manager 사이트에 대해 자동 클라이언트 업그레이드를 사용 하도록 설정 하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  

### <a name="configuration-alert"></a>구성 경고

데스크톱 분석에 표시 되지 않으면 장치나 불완전 한 인벤토리를 사용 하 여 표시 됩니다. 또한 configuration Manager는 장치 등록을 사용 하 여 문제를 식별 합니다. 자세한 내용은 목록을 참조 하세요 [Configuration Manager의 분석 데스크톱 장치 속성](#bkmk_config-issues)합니다.

예를 들어, 장치 연결 서비스에 없습니다. 자세한 내용은 [Windows 진단 끝점 연결](#windows-diagnostic-endpoint-connectivity)합니다.

### <a name="awaiting-enrollment"></a>등록을 대기 중

데스크톱 Analytics이이 장치에 대 한 진단 데이터 필요는 없습니다. 이 문제는 대상 컬렉션에 장치를 최근에 추가 되 고 데이터를 아직 전송 되지 않은 것 되었으므로 수 있습니다. 장치 서비스와 제대로 통신 하지 못합니다 및 최신 진단 데이터가 28 일 보다 오래 의미할 수도 있습니다.

장치는 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  

### <a name="status-pending"></a>상태 보류 됨

Configuration Manager는 여전히이 장치를 구성 하는 것 또는 해당 상태를 확인 하려면 장치에서 충분 한 데이터가 없습니다.

### <a name="missing-data"></a>누락 된 데이터

Configuration Manager 장치를 성공적으로 구성 되지만 데스크톱 Analytics 호환성 평가 만들 수 없습니다. 장치 구성 (인구 조사)에 대 한 완전 한 데이터 집합에 없는 또는 응용 프로그램 (인벤토리)를 설치 합니다.

이 문제는 종종 장치 재시도할 때 자동으로 해결 됩니다. 지속 되 면 장치는 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  


## <a name="device-list"></a>장치 목록

특정 장치 목록을 상태별으로 보려는 시작 합니다 **연결 상태** 대시보드. 세그먼트 중 하나를 선택 합니다 **연결 상태** 타일 및이 상태의 장치 목록으로 드릴 다운 합니다. 기본적으로 데스크톱 분석 열을 표시 하는이 사용자 지정 장치 보기:

- 상용 ID 구성
- 최소 호환성 업데이트
- Windows 진단 데이터 옵트인
- Windows 상용 데이터 옵트인
- Windows 진단 끝점 연결

> [!Note]  
> 에 대 한 열을 무시 **Office 진단 끝점 연결**합니다. 향후 기능에 대해 예약 됩니다.

키에 해당 하는 이러한 열 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites) 데스크톱 Analytics와 통신 하는 장치에 대 한 합니다.

![스크린 샷의 제대로 등록 장치 목록](media/sccm-device-list-properly-enrolled.png)

장치 세부 정보 창에서 사용 가능한 속성의 전체 목록을 보려면를 선택 합니다. 추가할 수 있습니다도 이러한 속성에 열으로 장치 목록으로.


## <a name="bkmk_config-issues"></a> 장치 속성

다음 데스크톱 분석 장치 속성은 Configuration Manager 장치 목록의 열으로 사용할 수 있습니다.

- [평가자 구성](#appraiser-configuration)  
- [최소 호환성 업데이트](#minimum-compatibility-update)  
- [평가자 버전](#appraiser-version)  
- [마지막 전체 실행을 성공적으로 평가자](#last-successful-full-run-of-appraiser)  
- [평가자 데이터 수집](#appraiser-data-collection)  
- [마지막 전체 실행을 성공적으로 인구 조사](#last-successful-full-run-of-census)  
- [인구 조사 데이터 수집](#census-data-collection)  
- [Windows 진단 끝점 연결](#windows-diagnostic-endpoint-connectivity)  
- [최종 사용자가 진단 데이터를 확인 합니다.](#check-end-user-diagnostic-data)  
- [사용자 프록시를 확인 합니다.](#check-user-proxy)  
- [상용 ID 구성](#commercial-id-configuration)  
- [Windows 상용 데이터 옵트인](#windows-commercial-data-opt-in)  
- [장치 이름을 진단 데이터를 확인 합니다.](#check-device-name-in-diagnostic-data)  
- [DiagTrack 서비스 구성](#diagtrack-service-configuration)  
- [DiagTrack 버전](#diagtrack-version)  
- [SQM ID 검색](#sqm-id-retrieval)  
- [고유한 장치 식별자 검색](#unique-device-identifier-retrieval)  
- [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)  

> [!Note]  
> 에 대 한 속성을 무시 **Office 진단 끝점 연결** 하 고 **Office 진단 데이터 옵트인**합니다. 향후 기능에 대해 예약 됩니다.

**가장 자주 사용 등록 차단 기능 및 구성 경고** 연결 상태 대시보드의 타일 문제도 장치를 가장 자주 보고 하는 속성을 표시 합니다.

### <a name="appraiser-configuration"></a>평가자 구성

<!--20,21-->
평가자는 해당 하는 Windows 구성 요소를 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)합니다. 앱 및 최신 버전의 Windows 사용 하 여 호환성을 위해 장치에서 드라이버를 평가합니다. 

이 검사에 성공한 경우 평가자 구성 요소가 제대로 장치의 구성 되어 있습니다.

그렇지 않으면 다음 오류 중 하나가 표시할 수 있습니다.

- 장치 앱 호환성 데이터 컬렉션 (SetRequestAllAppraiserVersions)를 구성할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 장치 앱 호환성 데이터 컬렉션 (SetRequestAllAppraiserVersions)를 구성할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 레지스트리 키에는 RequestAllAppraiserVersions를 쓸 수 없습니다 `HKLM:\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\AppCompatFlags\Appraiser`합니다. 사용 권한 확인  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

### <a name="minimum-compatibility-update"></a>최소 호환성 업데이트

<!--18,19,32-->
호환성 업데이트 (appraiser.dll)에 설치 또는 장치에서 만료 되지 않습니다. 분석 데스크톱 10.0.17763의 최소 요구 사항 보다 오래 된 것입니다.

최신 호환성 업데이트를 설치 합니다. 자세한 내용은 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)합니다.

### <a name="appraiser-version"></a>평가자 버전

이 속성은 장치의 평가자 구성 요소의 현재 버전을 표시합니다. 파일 버전에서 표시 `%windir%\System32\appraiser.dll`, 소수점 없이 합니다. 예를 들어, 파일 버전 10.0.17763 10017763으로 표시 됩니다.

### <a name="last-successful-full-run-of-appraiser"></a>마지막 전체 실행을 성공적으로 평가자

이 속성에는 날짜 및 시간 장치가 마지막으로 성공적으로 실행 된 평가자를 표시 합니다.

### <a name="appraiser-data-collection"></a>평가자 데이터 수집

<!--Appraiser run status-->
<!--22,33-->
이 속성 평가자 구성 요소를 실행 합니다. Windows에서 최신 결과 보여 줍니다.

그렇지 않은 경우 성공이 표시 될 수 있습니다 다음 오류 중 하나:

- 앱 호환성 (RunAppraiser) 데이터를 수집할 수 없습니다. 자세한 내용은 로그를 확인 합니다.  

- 오류 코드를 사용 하 여 앱 호환성 데이터 컬렉션 (CompatTelRunner.exe) 종료 되었습니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.

다음 파일이 있는지 확인: `%windir%\System32\CompatTelRunner.exe`합니다. 존재 하지 않는 경우 다시 필수 설치 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)합니다. 다른 시스템 구성 요소가 없으면 그룹 정책 등이 파일 또는 맬웨어 방지 서비스를 제거 하는 있는지 확인 합니다.

클라이언트에서 M365Handler.log 파일에는 다음 오류 중 하나가 포함: `RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x800703F1`
`RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x80070005`
`RunAppraiser failed. CompatTelRunner.exe exited with last error code: 0x80080005`  

이러한 오류를 해결 하려면 영향을 받는 클라이언트에서 관리자 권한 Windows PowerShell 콘솔에서 다음 명령을 실행 합니다.

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

### <a name="last-successful-full-run-of-census"></a>마지막 전체 실행을 성공적으로 인구 조사

이 속성에는 날짜 및 장치가 마지막으로 성공적으로 실행 된 인구 조사 하는 시간을 표시 합니다.

### <a name="census-data-collection"></a>인구 조사 데이터 수집

<!-- Census run status -->
<!--51,52-->
인구 조사는 장치를 인벤토리 하는 Windows 구성 요소입니다. 이 인벤토리 데이터는 장치 및 해당 구성을 이해 하려면 사용 됩니다.

이 속성 인구 조사 구성 요소를 실행 합니다. Windows에서 최신 결과 보여 줍니다.

그렇지 않은 경우 성공이 표시 될 수 있습니다 다음 오류 중 하나:

- 장치 및 해당 구성 (RunCensus)에 대 한 데이터를 수집할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 장치 및 구성 데이터 수집 도구 (devicecensus.exe) 찾을 수 없음  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.

다음 파일이 있는지 확인: `%windir%\System32\DeviceCensus.exe`합니다. 존재 하지 않는 경우 다시 필수 설치 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)합니다. 다른 시스템 구성 요소가 없으면 그룹 정책 등이 파일 또는 맬웨어 방지 서비스를 제거 하는 있는지 확인 합니다.

### <a name="windows-diagnostic-endpoint-connectivity"></a>Windows 진단 끝점 연결

<!--12,15-->
이 검사에 성공한 경우 장치가 연결 된 사용자 환경 및 원격 분석 (소용돌이) 끝점에 연결할 수 있습니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다 것:  

- 연결 된 사용자 환경 및 원격 분석 끝점 (소용돌이)에 연결할 수 없습니다. 네트워크/프록시 설정을 확인합니다  

- 연결 된 사용자 환경 및 원격 분석 끝점 (CheckVortexConnectivity)에 대 한 연결을 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

장치 OS 버전을 기준으로 다음 끝점에 대 한 GET 요청을 사용 하 여 연결을 확인 합니다.

| OS 버전 | 엔드포인트 |
|------------|----------|
| Windows 10, 버전 1803 이상이 최신 누적 업데이트를 사용 하 여 | `https://v10c.events.data.microsoft.com/health/keepalive` |
| Windows 10, 버전 1803 또는 2018-09 없이 이후 또는 나중에 누적 업데이트 | `https://v10.events.data.microsoft.com/health/keepalive` |
| Windows 10 버전 1709 이하의 | `https://v10.vortex-win.data.microsoft.com/health/keepalive` |
| Windows 7 또는 Windows 8.1 | `https://vortex-win.data.microsoft.com/health/keepalive` |

장치는 서비스와 통신할 수 있는지 확인 합니다. 이 검사는 일부 유효성을 검사 하지만 필요한 끝점의 일부입니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

### <a name="check-end-user-diagnostic-data"></a>최종 사용자가 진단 데이터를 확인 합니다.

<!--1004-->
이 검사를 성공한 없으면 사용자 장치에서 더 낮은 Windows 진단 데이터를 선택 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)합니다.

비즈니스 요구 사항에 따라 그룹 정책을 통해 사용자 선택을 해제할 수 있습니다. 설정을 사용 하 여 **원격 분석 옵트인 설정 사용자 인터페이스 구성**합니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.

### <a name="check-user-proxy"></a>사용자 프록시를 확인 합니다.

<!--30,35-->
DisableEnterpriseAuthProxy 설정은 Windows 7에 대 한 기본으로 사용 됩니다. Windows 8.1 컴퓨터에 대 한 Configuration Manager 설정 DisableEnterpriseAuthProxy 0 (해제 되지 않음).

이 속성에는 다음과 같은 오류가 표시 될 수 있습니다.

- 인증 프록시를 사용 합니다. DisableEnterpriseAuthProxy에서 0으로 설정 `HKLM\Software\Policies\Microsoft\Windows\DataCollection`

- 인증 프록시 상태를 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)합니다.  

### <a name="commercial-id-configuration"></a>상용 ID 구성

<!--9, 11, 53-->
Microsoft은 Desktop Analytics 작업 영역에서 장치 정보를 매핑할 고유한 상업용 ID를 사용 합니다. 이 ID에 대 한 서비스 데스크톱 Analytics를 사용 하 여 Configuration Manager와 통합 하면 자동으로 쿼리 자동으로 configuration Manager 클라이언트를 대상 데스크톱 분석 설정 하려는이 ID를 적용 해야 합니다.

이 확인이 성공한 경우 다음 장치가 제대로 구성 되어 상업용 id

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다 것:

- 레지스트리 키에는 CommercialId를 쓸 수 없습니다 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`합니다. 사용 권한 확인  

- 레지스트리 키에서 CommercialId를 업데이트할 수 없습니다 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`합니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 올바른 CommercialId 값 제공 `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)합니다.  

장치에 대 한 다른 ID가 있습니다. 이 레지스트리 키 그룹 정책에 의해 사용 됩니다. Configuration Manager에서 제공 하는 ID를 통해 우선 합니다.  

<a name="bkmk_ViewCommercialID"></a> 데스크톱 Analytics 포털에서 상업용 ID를 보려면 다음 절차를 따르십시오.

1. 선택한 데스크톱 Analytics 포털로 이동 **연결 된 서비스** 의 전역 설정 그룹입니다.  

2. 에 **연결 된 서비스** 창 합니다 **장치를 등록** 창 기본적으로 선택 됩니다. 등록 장치 창에 정보 섹션을 상업용 ID 키를 표시합니다.  

![데스크톱 Analytics 포털에서 상업용 ID의 스크린샷](media/commercial-id.png)

> [!Important]  
> 만 **새 ID 키 가져오기** 때 현재 사용할 수 없습니다. 상용 ID를 다시 생성 [새 Id 사용 하 여 장치를 다시 등록](/sccm/desktop-analytics/enroll-devices#device-enrollment)합니다. 이 프로세스는 전환 하는 동안 진단 데이터의 손실에서 될 수 있습니다.  

### <a name="windows-commercial-data-opt-in"></a>Windows 상용 데이터 옵트인

<!--64-->
이 속성은 Windows 7 또는 Windows 8.1 실행 하는 장치에 특정 합니다. 으로 유사한 테스트 실행 도중 [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)는 CommercialDataOptIn 값이 점을 제외 하 고, 합니다.

### <a name="check-device-name-in-diagnostic-data"></a>장치 이름을 진단 데이터를 확인 합니다.

<!--56,58-->
이 검사에 성공한 경우 장치에서 장치 이름을 공유할 구성 제대로 됩니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다 것:

- Windows 진단 데이터의 일부로 Microsoft에 전송할 수 있도록 장치 이름을 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 레지스트리 키에 AllowDeviceNameInTelemetry를 쓸 수 없습니다 `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`합니다. 사용 권한 확인  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)합니다.  

그룹 정책과 같은 다른 정책 메커니즘,이 설정을 사용 하지 않도록 설정 되지 있는지 확인 합니다.

### <a name="diagtrack-service-configuration"></a>DiagTrack 서비스 구성

<!--44,45,50-->
이 검사에 성공한 경우 DiagTrack 구성 요소가 제대로 장치의 구성 되어 있습니다. 데스크톱 분석에 필요한 최소 버전은 10010586 (10.0.10586).

그렇지 않으면 다음 오류 중 하나가 표시할 수 있습니다.

- 사용자 환경에 연결 된 원격 분석 (diagtrack.dll) 구성 요소는 오래 된 합니다. 요구 사항 확인  

- 연결 된 사용자 환경 및 원격 분석 (diagtrack.dll) 구성 요소를 찾을 수 없습니다. 요구 사항 확인  

- 사용 하도록 설정 하 고 Microsoft로 데이터를 보낼 연결 된 사용자 환경 및 원격 분석 서비스를 시작  

<!--
 - An updated Connected User Experience and Telemetry (diagtrack.dll) component is available. Check requirements - this is for the newer version that improves performance
 -->

<!--include something about diagtrack perf update https://go.microsoft.com/fwlink/?linkid=2011593-->

최신 업데이트를 설치 합니다. 자세한 내용은 [장치 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)합니다.

있는지 확인 합니다 **연결 된 사용자 환경 및 원격 분석** 서비스가 장치에서 실행 되 고 합니다.

### <a name="diagtrack-version"></a>DiagTrack 버전

이 속성은 장치에서 연결 된 사용자 환경 및 원격 분석 구성 요소의 현재 버전을 표시합니다. 파일 버전에서 표시 `%windir%\System32\diagtrack.dll`, 소수점 없이 합니다. 예를 들어, 파일 버전 10.0.10586 10010586으로 표시 됩니다.

### <a name="sqm-id-retrieval"></a>SQM ID 검색

<!--38-->
이 속성은 주로 Windows 7 장치입니다. 이 사용할 수 이상 운영 체제 버전에서 대체 (fallback) 식별자로 장치에 대 한 합니다.

그렇지 않은 경우 성공 하면 표시할 수 있습니다 다음 오류.

- 레거시 장치 원격 분석 식별자 (SQM ID)를 검색할 수 없습니다.

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

사용자 환경에서 중복 된 Id 필요가 있는지 확인 합니다. 예를 들어, 장치 일반화 되지 않은 OS 이미지를 사용 하 여 배포 된 경우.

### <a name="unique-device-identifier-retrieval"></a>고유한 장치 식별자 검색

<!--54-->
데스크톱 Analytics 더 신뢰할 수 있는 장치 id에 대 한 Microsoft 계정 서비스를 사용합니다.

있는지 확인 합니다 **Microsoft 계정 로그인 도우미** 서비스가 비활성화 되지 않습니다. 시작 유형 이어야 합니다 **수동 (트리거 시작)** 합니다.

최종 사용자가 Microsoft 계정 액세스를 비활성화 하려면이 끝점을 차단 하는 대신 정책 설정을 사용 합니다. 자세한 내용은 [기업에서 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)합니다.

### <a name="windows-diagnostic-data-opt-in"></a>Windows 진단 데이터 옵트인

<!--8,40,55,62-->
이 속성은 Windows 진단 데이터를 허용 하도록 올바르게 구성 되어 있는지 확인 합니다. 다음 레지스트리 키를 AllowTelemetry 값을 확인 합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

이러한 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한 이러한 키에 액세스할 수 있는지 확인 합니다. 충돌 하는 그룹 정책 개체에 의해 발생할 수도 있습니다. 자세한 내용은 [Windows 설정](/sccm/desktop-analytics/enroll-devices#windows-settings)합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  



## <a name="see-also"></a>참고 항목

[데스크톱 Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)