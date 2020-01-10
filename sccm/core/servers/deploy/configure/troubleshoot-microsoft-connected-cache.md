---
title: Connected Cache 문제 해결
titleSuffix: Configuration Manager
description: 문제 해결에 도움이 되는 Microsoft Connected Cache 기술 정보입니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 121e0341-4f51-4d54-a357-732c26caf7c5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 353d0a8d62086f7e8cdb2e302394d2999a66bd52
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75798363"
---
# <a name="troubleshoot-microsoft-connected-cache-in-configuration-manager"></a>Configuration Manager의 Microsoft Connected Cache 문제 해결

이 문서에서는 Configuration Manager의 Microsoft Connected Cache에 대한 기술 정보를 제공합니다. 이 정보는 참고하여 사용자 환경의 문제를 해결하세요. Microsoft Connected Cache의 작동 방식과 사용 방법에 대한 자세한 내용은 [Configuration Manager의 Microsoft Connected Cache](/sccm/core/plan-design/hierarchy/microsoft-connected-cache)를 참조하세요.

> [!NOTE]
> 버전 1910부터 이 기능을 **Microsoft Connected Cache**라고 합니다. 이전 명칭은 DOINC(전송 최적화 네트워크 내 캐시)였습니다.

## <a name="verify"></a>확인

전송 최적화 캐시 서버를 올바르게 설치하고 클라이언트를 올바르게 구성하는 경우 클라이언트는 인터넷이 아닌 배포 지점에 설치된 캐시 서버에서 다운로드됩니다.

[클라이언트](#bkmk_verify-client) 또는 [서버](#bkmk_verify-server)에서 이 동작을 확인합니다.

### <a name="bkmk_verify-client"></a> 클라이언트에서 확인

1. Windows 10 버전 1809 이상을 실행하는 클라이언트에서 클라우드 관리형 콘텐츠를 다운로드합니다. Connected Cache가 지원하는 콘텐츠 유형에 대한 자세한 내용은 [Connected Cache 확인](/sccm/core/plan-design/hierarchy/delivery-optimization-in-network-cache#verify)을 참조하세요.

2. PowerShell을 열고 다음 명령을 실행합니다. `Get-DeliveryOptimizationStatus`

예를 들면 다음과 같습니다.

```PowerShell
PS C:\> Get-DeliveryOptimizationStatus

FileId                      : ec523d49c4f7c3c4444f0d9b952286ce40fdcee4
FileSize                    : 549064
TotalBytesDownloaded        : 549064
PercentPeerCaching          : 0
BytesFromPeers              : 0
BytesFromHttp               : 0
Status                      : Caching
Priority                    : Background
BytesFromCacheServer        : 549064
BytesFromLanPeers           : 0
BytesFromGroupPeers         : 0
BytesFromInternetPeers      : 0
BytesToLanPeers             : 0
BytesToGroupPeers           : 0
BytesToInternetPeers        : 0
DownloadDuration            : 00:00:00.0780000
HttpConnectionCount         : 2
LanConnectionCount          : 0
GroupConnectionCount        : 0
InternetConnectionCount     : 0
DownloadMode                : 99
SourceURL                   : http://au.download.windowsupdate.com/c/msdownload/update/software/defu/2019/09/am_delta_p
                              atch_1.301.664.0_ec523d49c4f7c3c4444f0d9b952286ce40fdcee4.exe
NumPeers                    : 0
PredefinedCallerApplication : WU Client Download
ExpireOn                    : 9/6/2019 8:36:19 AM
IsPinned                    : False
```

`BytesFromCacheServer` 특성은 0이 아닙니다.

클라이언트가 올바르게 구성되지 않거나 캐시 서버가 올바르게 설치되지 않은 경우에는 전송 최적화 클라이언트가 원래 클라우드 원본으로 대체됩니다. 그런 다음, BytesFromCacheServer 특성은 0이 됩니다.

### <a name="bkmk_verify-server"></a> 서버에서 확인

먼저 레지스트리 속성이 올바르게 구성되어 있는지 확인합니다. `HKLM\SOFTWARE\Microsoft\Delivery Optimization In-Network Cache` 예를 들어 드라이브 캐시 위치는 `PrimaryDrivesInput\DOINC-E77D08D0-5FEA-4315-8C95-10D359D59294`입니다. 여기서 `PrimaryDrivesInput`은 `C,D,E` 같은 여러 드라이브가 될 수 있습니다.

그런 다음, 다음 방법을 사용하여 필수 헤더가 있는 서버에 관한 클라이언트 다운로드 요청을 시뮬레이트합니다.

1. 관리자 권한으로 64비트 PowerShell 창을 엽니다.
2. 다음 명령을 실행하고 서버의 이름 또는 IP 주소를 `<DoincServer>`로 바꿉니다.

```PowerShell
Invoke-WebRequest -URI "http://<DoincServer>/mscomtest/wuidt.gif" -Headers @{"Host"="b1.download.windowsupdate.com"}
```

출력은 다음 예제와 같이 표시됩니다.

```PowerShell
PS C:\WINDOWS\system32> Invoke-WebRequest -URI "http://SERVER01.CONTOSO.COM/mscomtest/wuidt.gif" -Headers @{"Host"="b1.download.windowsupdate.com"}


StatusCode        : 200
StatusDescription : OK
Content           : {71, 73, 70, 56...}
RawContent        : HTTP/1.1 200 OK
                    X-HW: 1567797125.dop019.se2.t,1567797125.cds058.se2.s,1567797125.dop114.at2.r,1567797125.cds079.at2
                    .p,1567797125.cds058.se2.p
                    X-CCC: cdP+dRBgUCoZO1mezA9zhg2VwQ7P1JWTh9k+GhfQmu8=_SLwv...
Headers           : {[X-HW, 1567797125.dop019.se2.t,1567797125.cds058.se2.s,1567797125.dop114.at2.r,1567797125.cds079.a
                    t2.p,1567797125.cds058.se2.p], [X-CCC,
                    cdP+dRBgUCoZO1mezA9zhg2VwQ7P1JWTh9k+GhfQmu8=_SLwvtSBQdT3uPQ5ikBe1ABMbdYIIncem+h5dtcLI6GY=],
                    [X-CID, 100], [Accept-Ranges, bytes]...}
RawContentLength  : 969710
```

다음 특성은 성공을 나타냅니다.

- `StatusCode : 200`
- `StatusDescription : OK`

## <a name="log-files"></a>로그 파일

- ARR 설치 로그: `%temp%\arr_setup.log`

- DO 캐시 서버 설치 로그: 배포 지점의 `SMS_DP$\Ms.Dsp.Do.Inc.Setup\DoincSetup.log` 및 사이트 서버의 `DistMgr.log`

- IIS 작업 로그: 기본적으로 `%SystemDrive%\inetpub\logs\LogFiles`

- DO 캐시 서버 작업 로그: `C:\Doinc\Product\Install\Logs`

    > [!TIP]
    > 어떤 용도보다도 이 로그를 통해 Microsoft 클라우드를 사용한 연결 문제를 식별할 수 있습니다.

## <a name="setup-error-codes"></a>설치 오류 코드

다음 표에는 Configuration Manager에서 배포 지점에 Connected Cache 구성 요소를 설치할 때 발생할 수 있는 오류 코드가 나와 있습니다.

| 오류 코드 | 오류 설명 |
|------------|-------------------|
| 0x00000000 | 성공 |
| 0x00000BC2 | 성공, 다시 부팅 필요 |
| 0x00000643 | 일반 설치 오류 |
| 0x00D00001 | IIS(인터넷 정보 서비스)가 설치된 경우에만 Connected Cache 설치 프로그램을 실행할 수 있음 |
| 0x00D00002 | 서버에 '기본 웹 사이트'가 있는 경우에만 Connected Cache 설치 프로그램을 실행할 수 있음 |
| 0x00D00003 | ARR(애플리케이션 요청 라우팅)이 이미 설치된 경우 Connected Cache를 설치할 수 없음 |
| 0x00D00004 | ARR(애플리케이션 요청 라우팅)이 Install.ps1 스크립트를 통해 설치된 경우에만 Connected Cache 설치 프로그램을 실행할 수 있음 |
| 0x00D00005 | Connected Cache 설치 프로그램을 사용하려면 PowerShell 세션이 관리자 권한으로 실행되어야 함 |
| 0x00D00006 | Connected Cache 설치 프로그램은 64비트 PowerShell 환경에서만 실행할 수 있음 |
| 0x00D00007 | Connected Cache 설치 프로그램은 Windows Server에서만 실행할 수 있음 |
| 0x00D00008 | 실패: 지정된 캐시 드라이브 수는 지정된 캐시 드라이브 크기 비율의 수와 일치해야 함 |
| 0x00D00009 | 실패: 유효한 캐시 노드 ID를 제공해야 함 |
| 0x00D0000A | 실패: 유효한 캐시 드라이브 세트를 제공해야 함 |
| 0x00D0000B | 실패: 유효한 캐시 드라이브 크기 비율 세트를 제공해야 함 |
| 0x00D0000C | 실패: 유효한 캐시 드라이브 크기 비율 세트 또는 캐시 드라이브 크기(GB)를 제공해야 함 |
| 0x00D0000D | 실패: 유효한 캐시 드라이브 크기 비율 세트 및 캐시 드라이브 크기(GB)를 둘 다 제공할 수는 없음 |
| 0x00D0000E | 실패: 지정된 캐시 드라이브 수는 지정된 캐시 드라이브 크기(GB)의 수와 일치해야 함 |
| 0x00D0000F | 실패: $AppHostConfig에서 $AppHostConfigDestinationName으로 applicationhost.config 파일을 백업할 수 없음 |
| 0x00D00010 | 실패: $WebsiteConfigFilePath에서 $WebConfigDestinationName으로 기본 웹 사이트 web.config 파일을 백업할 수 없음 |
| 0x00D00011 | 실패: SetupARRWebFarm.ps1에서 예외가 발생함 |
| 0x00D00012 | 실패: SetupARRWebFarmRewriteRules.ps1에서 예외가 발생함 |
| 0x00D00013 | 실패: SetupARRWebFarmProperties.ps1에서 예외가 발생함 |
| 0x00D00014 | 실패: SetupAllowableServerVariables.ps1에서 예외가 발생함 |
| 0x00D00015 | 실패: SetupFirewallRules.ps1에서 예외가 발생함 |
| 0x00D00016 | 실패: SetupAppPoolProperties.ps1에서 예외가 발생함 |
| 0x00D00017 | 실패: SetupARROutboundRules.ps1에서 예외가 발생함 |
| 0x00D00018 | 실패: SetupARRDiskCache.ps1에서 예외가 발생함 |
| 0x00D00019 | 실패: SetupARRProperties.ps1에서 예외가 발생함 |
| 0x00D0001A | 실패: SetupARRHealthProbes.ps1에서 예외가 발생함 |
| 0x00D0001B | 실패: VerifyIISSItesStarted.ps1에서 예외가 발생함 |
| 0x00D0001C | 실패: SetDrivesToHealthy.ps1에서 예외가 발생함 |
| 0x00D0001D | 실패: VerifyCacheNodeSetup.ps1에서 예외가 발생함 |
| 0x00D0001E | 기본 웹 사이트가 포트 80에 있지 않은 경우 Connected Cache를 설치할 수 없음 |
| 0x00D0001F | 실패: 캐시 드라이브 할당(%)은 100를 초과할 수 없음 |
| 0x00D00020 | 실패: 캐시 드라이브 할당(GB)은 드라이브의 여유 공간을 초과할 수 없음 |
| 0x00D00021 | 실패: 캐시 드라이브 할당(%)은 0보다 커야 함 |
| 0x00D00022 | 실패: 캐시 드라이브 할당(GB)은 0보다 커야 함 |
| 0x00D00023 | 실패: RegisterScheduledTask_CacheNodeKeepAlive에서 예외가 발생함 |
| 0x00D00024 | 실패: RegisterScheduledTask_Maintenance에서 예외가 발생함 |
| 0x00D00025 | 실패: HTTPS 팜 $FarmName에 관한 다시 쓰기 규칙을 설정하는 동안 예외가 발생함 |
| 0x00D00026 | 실패: HTTP 팜 $FarmName에 관한 다시 쓰기 규칙을 설정하는 동안 예외가 발생함 |
| 0x00D00027 | 종속 소프트웨어 “ARR(애플리케이션 요청 라우팅)”을 설치하지 못했으므로 Connected Cache를 설치할 수 없음. %temp%\arr_setup.log에 있는 로그 파일 참조 |

## <a name="iis-configurations"></a>IIS 구성

DO 캐시 서버 설치에서 배포 지점의 IIS 구성에 관한 여러 수정 버전이 생성됩니다.

### <a name="application-request-routing"></a>애플리케이션 요청 라우팅

DO 캐시 서버 설치에서 IIS [ARR(애플리케이션 요청 라우팅)](https://www.iis.net/downloads/microsoft/application-request-routing)을 설치 및 구성합니다. 잠재적인 충돌을 방지하려면 배포 지점에 이 구성 요소가 설치되어 있으면 안 됩니다.

### <a name="allowed-server-variables"></a>허용된 서버 변수

DO 캐시 서버를 설치한 후 기본 웹 사이트에는 다음 ‘로컬’ 서버 변수가 있습니다. 

- HTTP_HOST
- QUERY_STRING
- X-CCC
- X-CID
- X-DOINC-OUTBOUND

### <a name="rewrite-rules"></a>다시 쓰기 규칙

DO 캐시 서버는 다음 다시 쓰기 규칙을 추가합니다.

#### <a name="inbound-rewrite-rules"></a>인바운드 다시 쓰기 규칙

- `Doinc_ForwardToFarm_shswda01.download.manage-selfhost.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_swdc01.manage.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_swdc02.manage.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_dl.delivery.mp.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_officecdn.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_b1.download.windowsupdate.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_download.windowsupdate.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_officecdn.microsoft.com.edgesuite.net_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_au.b1.download.windowsupdate.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_assets1.xboxlive.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_au.download.windowsupdate.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_emdl.ws.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_tlu.dl.delivery.mp.microsoft.com_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_ForwardToFarm_assets2.xboxlive.com_E77D08D0-5FEA-4315-8C95-10D359D59294`

#### <a name="outbound-rewrite-rules"></a>아웃바운드 다시 쓰기 규칙

- `Doinc_Outbound_SetHeader_X_CID_E77D08D0-5FEA-4315-8C95-10D359D59294`
- `Doinc_Outbound_SetHeader_X_CCC_E77D08D0-5FEA-4315-8C95-10D359D59294`

## <a name="manage-server-resources"></a>서버 리소스 관리

각 DO 캐시 서버에 필요한 디스크 공간은 조직의 업데이트 요구 사항에 따라 달라질 수 있습니다. 다음 콘텐츠를 캐시할 수 있는 충분한 공간은 100GB입니다.

- 기능 업데이트
- 2~3개월 품질 및 Office 업데이트
- Microsoft Intune 앱 및 Windows 받은 편지함 앱

DO 캐시 서버는 시스템 메모리 또는 프로세서 시간을 많이 소비하지 않아야 합니다. DO 캐시 서버를 설치한 후 프로세스 또는 메모리 리소스 소비가 많은 경우 IIS 및 ARR 로그 파일을 분석합니다.

IIS 및 ARR 로그 파일이 서버에서 너무 많은 공간을 차지하는 경우 로그 파일을 관리하는 데 사용할 수 있는 여러 가지 방법이 있습니다. 자세한 내용은 [Managing IIS Log File Storage](https://docs.microsoft.com/iis/manage/provisioning-and-managing-iis/managing-iis-log-file-storage#overview)(IIS 로그 파일 스토리지 관리)를 참조하세요.

## <a name="see-also"></a>참고 항목

[Configuration Manager의 Microsoft Connected Cache](/sccm/core/plan-design/hierarchy/microsoft-connected-cache)
