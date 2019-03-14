---
title: 데스크톱 Analytics 문제 해결
titleSuffix: Configuration Manager
description: 데스크톱 Analytics를 사용 하 여 문제를 해결 하려면 기술 세부 정보입니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 63e08f3f-9558-4ed7-9bf3-3a185ddaac5c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bebf4065a4db1c45ee7eaa0a5b04b8d1533f29f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755245"
---
# <a name="troubleshooting-desktop-analytics"></a>데스크톱 Analytics 문제 해결

데스크톱 Analytics를 Configuration Manager 통합을 사용 하 여 문제를 해결 하기 위해이 문서에서 세부 정보를 사용 합니다.



## <a name="confirm-prerequisites"></a>필수 구성 요소 확인

많은 일반적인 문제는 누락 된 필수 구성 요소에서 발생 합니다. 먼저 다음과 같은 구성을 확인 합니다.

- [전제 조건](/sccm/desktop-analytics/overview#prerequisites)  

- [Windows 구성 요소 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)  

- [데이터 공유를 사용 하는 방법](/sccm/desktop-analytics/enable-data-sharing)에 다음 항목을 다룹니다.  

    - 클라이언트를 연결 하려면 인터넷 끝점  

    - 프록시 서버 인증  

    - 진단 데이터 수준  



## <a name="monitor-connection-health"></a>연결 상태 모니터

사용 된 **연결 상태** 장치 상태별으로 범주로 드릴 다운 하려면 Configuration Manager의 대시보드. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **Microsoft 365 서비스** 노드를 선택한는 **연결 상태** 대시보드.  

![Configuration Manager 연결 상태 대시보드의 스크린 샷](media/connection-health-dashboard.png)

일부 장치를 데스크톱 Analytics에서 표시 하지 않는 경우 먼저 비율을 확인할 **연결 된 장치**합니다. 100% 미만인 경우 데스크톱 분석 하 여 장치를 지원 하는지 확인 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.


### <a name="connection-health-states"></a>연결 상태

다음을 검토 합니다 **연결 상태** 차트입니다. 다음 상태 범주에서 장치의 수가 표시 됩니다.  

- [제대로 등록](#properly-enrolled)  
- [구성 문제](#configuration-issues)  
- [클라이언트 설치 안 됨](#client-not-installed)  
- [등록에 대 한 대기](#waiting-for-enrollment)  
- [누락 된 필수 구성 요소](#missing-prerequisites)  
- [누락 된 데이터](#missing-data)  

차트에서 추가 하거나 제거 하려면 범주 이름을 선택 합니다. 이 작업을 더 작은 세그먼트의 상대 크기를 볼 수 있도록 차트를 확대/축소 수 있습니다. 

#### <a name="properly-enrolled"></a>제대로 등록
장치에는 다음 특성이 있습니다.  
- Configuration Manager 1810 이상 클라이언트 버전  
- 구성 오류가 없음을  
- 데스크톱 분석 지난 28 일 동안에서이 장치에서 전체 진단 데이터를 수신  
- 데스크톱 장치 구성의 전체 인벤토리를가 분석과 설치 된 앱  

#### <a name="configuration-issues"></a>구성 문제
Configuration Manager는 데스크톱 분석에 필요한 구성을 사용 하 여 하나 이상의 문제를 검색 합니다. 자세한 내용은 목록을 참조 하세요 [Configuration Manager의 분석 데스크톱 장치 속성](#bkmk_config-issues)합니다.  

#### <a name="client-not-installed"></a>클라이언트 설치 안 됨
장치가 목표로 하는 데스크톱 분석용 왔지만 Configuration Manager 클라이언트를 합니다. 

Configuration Manager 클라이언트를 구성 하 고 데스크톱 분석을 위해 장치를 관리 해야 합니다. 자세한 내용은 [클라이언트 설치 방법](/sccm/core/clients/deploy/plan/client-installation-methods)을 참조하세요.  

#### <a name="waiting-for-enrollment"></a>등록에 대 한 대기
데스크톱 Analytics이이 장치에 대 한 진단 데이터 필요는 없습니다. 장치가 대상 컬렉션에 최근에 추가 된 데이터를 아직 보내지 않은 때문에이 문제가 될 수 있습니다. 장치 서비스와 제대로 통신 하지 못합니다 및 최신 진단 데이터가 28 일 보다 오래 의미할 수도 있습니다. 

장치는 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  

#### <a name="missing-prerequisites"></a>누락 된 필수 구성 요소
Configuration Manager 클라이언트가 없는 이상 버전 1810 (5.0.8740). 

최신 버전으로 클라이언트를 업데이트 합니다. Configuration Manager 사이트에 대해 자동 클라이언트 업그레이드를 사용 하도록 설정 하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  

#### <a name="missing-data"></a>누락 된 데이터
데스크톱 Analytics 호환성 평가 만들 수 없습니다. 장치 구성 (인구 조사)에 대 한 완전 한 데이터 집합에 없는 또는 응용 프로그램 (인벤토리)를 설치 합니다. 

이 문제는 종종 장치 재시도할 때 자동으로 해결 됩니다. 지속 되 면 장치는 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  


### <a name="device-list"></a>장치 목록

특정 장치 목록을 상태별으로 보려는 시작 합니다 **연결 상태** 대시보드. 세그먼트 중 하나를 선택 합니다 **연결 상태** 타일 및이 범주의 장치 목록으로 드릴 다운 합니다. 기본적으로 데스크톱 분석 열을 표시 하는이 사용자 지정 장치 보기:
- 상용 ID 구성
- 최소 호환성 업데이트
- Windows 진단 데이터 옵트인
- Windows 상용 데이터 옵트인
- Windows 진단 끝점 연결
- Office 진단 끝점 연결

키에 해당 하는 이러한 열 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites) 데스크톱 Analytics와 통신 하는 장치에 대 한 합니다. 

![스크린 샷의 제대로 등록 장치 목록](media/sccm-device-list-properly-enrolled.png)

장치 세부 정보 창에서 사용 가능한 속성의 전체 목록을 보려면를 선택 합니다. 추가할 수 있습니다도 이러한 속성에 열으로 장치 목록으로. 


### <a name="bkmk_config-issues"></a> 데스크톱 분석 장치 Configuration Manager의 속성

다음 열은 장치 목록에서 사용할 수 있습니다.
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
- [Office 진단 끝점 연결](#office-diagnostic-endpoint-connectivity)  

#### <a name="appraiser-configuration"></a>평가자 구성
<!--20,21--> 평가자는 해당 하는 Windows 구성 요소를 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)합니다. 앱 및 최신 버전의 Windows 사용 하 여 호환성을 위해 장치에서 드라이버를 평가합니다. 

이 검사에 성공한 경우 평가자 구성 요소가 제대로 장치의 구성 되어 있습니다. 

그렇지 않으면 다음 오류 중 하나가 표시할 수 있습니다.

- 장치 앱 호환성 데이터 컬렉션 (SetRequestAllAppraiserVersions)를 구성할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 장치 앱 호환성 데이터 컬렉션 (SetRequestAllAppraiserVersions)를 구성할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 레지스트리 키에는 RequestAllAppraiserVersions를 쓸 수 없습니다 `HKLM:\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\AppCompatFlags\Appraiser`합니다. 사용 권한 확인  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  


#### <a name="minimum-compatibility-update"></a>최소 호환성 업데이트
<!--18,19,32--> 호환성 업데이트 (appraiser.dll)에 설치 또는 장치에서 만료 되지 않습니다. 분석 데스크톱 10.0.17763의 최소 요구 사항 보다 오래 된 것입니다. 

최신 호환성 업데이트를 설치 합니다. 자세한 내용은 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)합니다.


#### <a name="appraiser-version"></a>평가자 버전
이 속성은 장치의 평가자 구성 요소의 현재 버전을 표시합니다. 파일 버전에서 표시 `%windir%\System32\appraiser.dll`, 소수점 없이 합니다. 예를 들어, 파일 버전 10.0.17763 10017763으로 표시 됩니다. 


#### <a name="last-successful-full-run-of-appraiser"></a>마지막 전체 실행을 성공적으로 평가자
이 속성에는 날짜 및 시간 장치가 마지막으로 성공적으로 실행 된 평가자를 표시 합니다.


#### <a name="appraiser-data-collection"></a>평가자 데이터 수집
<!--Appraiser run status-->
<!--22,33--> 이 속성 평가자 구성 요소를 실행 합니다. Windows에서 최신 결과 보여 줍니다. 

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

#### <a name="last-successful-full-run-of-census"></a>마지막 전체 실행을 성공적으로 인구 조사
이 속성에는 날짜 및 장치가 마지막으로 성공적으로 실행 된 인구 조사 하는 시간을 표시 합니다. 

#### <a name="census-data-collection"></a>인구 조사 데이터 수집
<!-- Census run status -->
<!--51,52--> 인구 조사는 장치를 인벤토리 하는 Windows 구성 요소입니다. 이 인벤토리 데이터는 장치 및 해당 구성을 이해 하려면 사용 됩니다. 

이 속성 인구 조사 구성 요소를 실행 합니다. Windows에서 최신 결과 보여 줍니다.

그렇지 않은 경우 성공이 표시 될 수 있습니다 다음 오류 중 하나: 

- 장치 및 해당 구성 (RunCensus)에 대 한 데이터를 수집할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 장치 및 구성 데이터 수집 도구 (devicecensus.exe) 찾을 수 없음  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다. 

다음 파일이 있는지 확인: `%windir%\System32\DeviceCensus.exe`합니다. 존재 하지 않는 경우 다시 필수 설치 [호환성 업데이트](/sccm/desktop-analytics/enroll-devices#bkmk_appraiser)합니다. 다른 시스템 구성 요소가 없으면 그룹 정책 등이 파일 또는 맬웨어 방지 서비스를 제거 하는 있는지 확인 합니다. 


#### <a name="windows-diagnostic-endpoint-connectivity"></a>Windows 진단 끝점 연결
<!--12,15--> 이 검사에 성공한 경우 장치는 연결 된 사용자 환경 및 원격 분석 끝점 (소용돌이)에 연결할 수 있습니다. 

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


#### <a name="check-end-user-diagnostic-data"></a>최종 사용자가 진단 데이터를 확인 합니다.
<!--1004-->

이 검사를 성공한 없으면 사용자 장치에서 더 낮은 Windows 진단 데이터를 선택 합니다.

비즈니스 요구 사항에 따라 그룹 정책을 통해 사용자 선택을 해제할 수 있습니다. 설정을 사용 하 여 **원격 분석 옵트인 설정 사용자 인터페이스 구성**합니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)을 참조하세요.


#### <a name="check-user-proxy"></a>사용자 프록시를 확인 합니다.
<!--30,35-->

DisableEnterpriseAuthProxy 설정은 Windows 7에 대 한 기본으로 사용 됩니다. Windows 8.1 컴퓨터에 대 한 Configuration Manager 설정 DisableEnterpriseAuthProxy 0 (해제 되지 않음).

이 속성에는 다음과 같은 오류가 표시 될 수 있습니다.

- 인증 프록시를 사용 합니다. DisableEnterpriseAuthProxy에서 0으로 설정 `HKLM\Software\Policies\Microsoft\Windows\DataCollection` 

- 인증 프록시 상태를 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다.  


#### <a name="commercial-id-configuration"></a>상용 ID 구성
<!--9, 11, 53--> Microsoft은 Desktop Analytics 작업 영역에서 장치 정보를 매핑할 고유한 상업용 ID를 사용 합니다. 이 ID에 대 한 서비스 데스크톱 Analytics를 사용 하 여 Configuration Manager와 통합 하면 자동으로 쿼리 자동으로 configuration Manager 클라이언트를 대상 데스크톱 분석 설정 하려는이 ID를 적용 해야 합니다. 

이 확인이 성공한 경우 다음 장치가 제대로 구성 되어 상업용 id

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다 것:

- 레지스트리 키에는 CommercialId를 쓸 수 없습니다 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`합니다. 사용 권한 확인  

- 레지스트리 키에서 CommercialId를 업데이트할 수 없습니다 `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`합니다. 예외 세부 정보에 대 한 로그를 확인 합니다.   

- 올바른 CommercialId 값 제공 `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다.  

장치에 대 한 다른 ID가 있습니다. 이 레지스트리 키 그룹 정책에 의해 사용 됩니다. Configuration Manager에서 제공 하는 ID를 통해 우선 합니다.  


데스크톱 Analytics 포털에서 상업용 ID를 보려면 다음 절차를 따르십시오. 

1. 선택한 데스크톱 Analytics 포털로 이동 **연결 된 서비스** 의 전역 설정 그룹입니다.  

2. 에 **연결 된 서비스** 창 합니다 **장치를 등록** 창 기본적으로 선택 됩니다. 등록 장치 창에 정보 섹션을 상업용 ID 키를 표시합니다.  

![데스크톱 Analytics 포털에서 상업용 ID의 스크린샷](media/commercial-id.png)

> [!Important]  
> 만 **새 ID 키 가져오기** 때 현재 사용할 수 없습니다. 상용 ID를 다시 생성 하면 새 ID를 장치에 배포 합니다. 이 프로세스는 전환 하는 동안 진단 데이터의 손실에서 될 수 있습니다.  


#### <a name="windows-commercial-data-opt-in"></a>Windows 상용 데이터 옵트인
<!--64-->

이 속성은 Windows 7 또는 Windows 8.1 실행 하는 장치에 특정 합니다. 으로 유사한 테스트 실행 도중 [Windows 진단 데이터 옵트인](#windows-diagnostic-data-opt-in)는 CommercialDataOptIn 값이 점을 제외 하 고, 합니다.


#### <a name="check-device-name-in-diagnostic-data"></a>장치 이름을 진단 데이터를 확인 합니다.
<!--56,58-->

이 검사에 성공한 경우 장치에서 장치 이름을 공유할 구성 제대로 됩니다.

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다 것:

- Windows 진단 데이터의 일부로 Microsoft에 전송할 수 있도록 장치 이름을 확인할 수 없습니다. 예외 세부 정보에 대 한 로그를 확인 합니다.  

- 레지스트리 키에 AllowDeviceNameInTelemetry를 쓸 수 없습니다 `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`합니다. 사용 권한 확인  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

이 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한이 키에 액세스할 수 있는지 확인 합니다.  

그룹 정책과 같은 다른 정책 메커니즘,이 설정을 사용 하지 않도록 설정 되지 있는지 확인 합니다. 


#### <a name="diagtrack-service-configuration"></a>DiagTrack 서비스 구성
<!--44,45,50--> 이 검사에 성공한 경우 DiagTrack 구성 요소가 제대로 장치의 구성 되어 있습니다. 데스크톱 분석에 필요한 최소 버전은 10010586 (10.0.10586). 

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

#### <a name="diagtrack-version"></a>DiagTrack 버전
이 속성은 장치에서 연결 된 사용자 환경 및 원격 분석 구성 요소의 현재 버전을 표시합니다. 파일 버전에서 표시 `%windir%\System32\diagtrack.dll`, 소수점 없이 합니다. 예를 들어, 파일 버전 10.0.10586 10010586으로 표시 됩니다. 

#### <a name="sqm-id-retrieval"></a>SQM ID 검색
<!--38-->

이 속성은 주로 Windows 7 장치입니다. 이 사용할 수 이상 운영 체제 버전에서 대체 (fallback) 식별자로 장치에 대 한 합니다. 

그렇지 않은 경우 성공 하면 표시할 수 있습니다 다음 오류.

- 레거시 장치 원격 분석 식별자 (SQM ID)를 검색할 수 없습니다.

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  

사용자 환경에서 중복 된 Id 필요가 있는지 확인 합니다. 예를 들어, 장치 일반화 되지 않은 OS 이미지를 사용 하 여 배포 된 경우. 


#### <a name="unique-device-identifier-retrieval"></a>고유한 장치 식별자 검색
<!--54--> 데스크톱 Analytics 더 신뢰할 수 있는 장치 id에 대 한 Microsoft 계정 서비스를 사용합니다. 

있는지 확인 합니다 **Microsoft 계정 로그인 도우미** 서비스가 비활성화 되지 않습니다. 시작 유형 이어야 합니다 **수동 (트리거 시작)** 합니다.

최종 사용자가 Microsoft 계정 액세스를 비활성화 하려면이 끝점을 차단 하는 대신 정책 설정을 사용 합니다. 자세한 내용은 [기업에서 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)합니다.


#### <a name="windows-diagnostic-data-opt-in"></a>Windows 진단 데이터 옵트인
<!--8,40,55,62--> 이 속성은 Windows 진단 데이터를 허용 하도록 올바르게 구성 되어 있는지 확인 합니다. 다음 레지스트리 키를 AllowTelemetry 값을 확인 합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

이러한 레지스트리 키에 대 한 권한을 확인 합니다. 로컬 시스템 계정을 설정 하려면 Configuration Manager 클라이언트에 대 한 이러한 키에 액세스할 수 있는지 확인 합니다.  

자세한 내용은 클라이언트에서 M365AHandler.log를 검토 합니다.  


#### <a name="office-diagnostic-endpoint-connectivity"></a>Office 진단 끝점 연결
<!-- 1001,1002,1003 -->

이 검사에 성공한 경우 장치는 Office 진단 끝점에 연결할 수 있습니다. 

그렇지 않으면 다음 오류 중 하나가 표시 될 수 있습니다 것:

- Office 진단 끝점 (Aria)에 연결할 수 없습니다. 네트워크/프록시 설정을 확인합니다  

- Office 진단 끝점 (Nexusrules)에 연결할 수 없습니다. 네트워크/프록시 설정을 확인합니다  

- Office 진단 끝점 (Nexus)에 연결할 수 없습니다. 네트워크/프록시 설정을 확인합니다  

장치는 서비스와 통신할 수 있는지 확인 합니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.  



## <a name="log-files"></a>로그 파일

Configuration Manager와 통합 하는 데스크톱 Analytics를 사용 하 여 문제를 해결 하는 다음 로그 파일을 사용 합니다. 


### <a name="service-connection-point"></a>서비스 연결 지점

다음 로그 파일은 다음 디렉터리에 서비스 연결 지점에서: `C:\Program Files\Configuration Manager\Logs\M365A`:

| 로그 | Description |
|---------|---------|
| **M365ADeploymentPlanWorker.log** | 데스크톱 분석에서 계획 동기화를 배포 하는 방법은 클라우드 서비스를 온-프레미스 Configuration Manager |
| **M365ADeviceHealthWorker.log** | 장치 상태에 대 한 정보는 Configuration Manager에서 Microsoft cloud에 업로드 |
| **M365AUploadWorker.log** | 컬렉션 및 장치에 대 한 정보는 Configuration Manager에서 Microsoft cloud에 업로드 |


### <a name="configuration-manager-client"></a>Configuration Manager 클라이언트

다음 로그 파일은 다음 디렉터리에 Configuration Manager 클라이언트에서: `C:\Windows\CCM\logs`:

| 로그 | Description |
|---------|---------|
| **M365Handler.log** | 데스크톱 분석 설정 정책에 대 한 정보 |


### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용 

1. 서비스 연결 지점에서 다음 레지스트리 키로 이동 합니다. `HKLM\Software\Microsoft\SMS\Tracing\SMS_SERVICE_CONNECTOR`  
2. 설정 된 **LogLevel** 값 `0`  
3. 사이트 데이터베이스에서 다음 SQL 명령을 실행 합니다.  

    ```SQL
    DELETE FROM M365AProperties WHERE Name = 'M365ATenantUpdateInfo_LastUpdateTime'
    ```

4. 다시 시작 합니다 **SMS_EXECUTIVE** 사이트 서버의 서비스



## <a name="bkmk_MALogAnalyticsReader"></a> MALogAnalyticsReader 응용 프로그램 역할

데스크톱 Analytics를 설정 하는 경우 조직을 대신 하 여 동의 허용 합니다. 이 동의 MALogAnalyticsReader 응용 프로그램 작업 영역에 대 한 Log Analytics Reader 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석 필요 합니다. 

설정 하는 동안이 프로세스에 문제가 없는 경우이 사용 권한을 수동으로 추가 하려면 다음 프로세스를 사용 합니다.

1. 로 이동 합니다 [Azure portal](http://portal.azure.com), 선택한 **모든 리소스**합니다. 형식의 작업 영역 선택 **Log Analytics**합니다.  

2. 작업 영역 메뉴에서 선택 **액세스 제어 (IAM)** 을 선택한 후 **추가**합니다.  

3. 에 **권한 추가** 패널에서 다음 설정을 구성 합니다.  

    - **역할**: **Log Analytics Reader**  

    - **에 대 한 액세스 할당**: **Azure AD 사용자, 그룹 또는 응용 프로그램**  

    - **선택**: **MALogAnalyticsReader**  
  
4. **저장**을 선택합니다. 

알림 역할 할당을 추가 하는 포털 보여 줍니다.

