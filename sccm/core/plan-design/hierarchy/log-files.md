---
title: 로그 파일 참조
titleSuffix: Configuration Manager
description: Configuration Manager 클라이언트, 서버, 종속 구성 요소에 대한 모든 로그 파일의 참조입니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c1ff371e-b0ad-4048-aeda-02a9ff08889e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c88035f7aff8b6021639b3c26387567e722cfc63
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68536701"
---
# <a name="log-file-reference"></a>로그 파일 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서는 클라이언트 및 사이트 서버 구성 요소가 개별 로그 파일에 프로세스 정보를 기록합니다. 이러한 로그 파일의 정보를 사용하면 발생할 수 있는 문제를 해결할 수 있습니다. Configuration Manager에서는 기본적으로 클라이언트 및 서버 구성 요소 로깅을 사용하도록 설정됩니다.

Configuration Manager의 로그 파일에 대한 자세한 내용은 [로그 파일 정보](/sccm/core/plan-design/hierarchy/about-log-files)를 참조하세요. 해당 문서에는 사용할 도구, 로그 구성 방법, 로그를 찾을 위치에 대한 정보가 포함됩니다.

다음 섹션에는 제공되는 여러 가지 로그 파일에 대한 자세한 정보가 나와 있습니다. 작업 정보에 대한 Configuration Manager 클라이언트 및 서버 로그를 모니터링하고, 오류 정보를 보고 문제를 해결할 수 있습니다.  

- [클라이언트 로그 파일](#BKMK_ClientLogs)  

    - [클라이언트 작업](#BKMK_ClientOpLogs)  

    - [클라이언트 설치](#BKMK_ClientInstallLog)  

    - [Linux 및 UNIX용 클라이언트](#BKMK_LogFilesforLnU)  

    - [Mac 컴퓨터용 클라이언트](#BKMK_LogfilesforMac)  

- [서버 로그 파일](#BKMK_ServerLogs)  

    - [사이트 서버 및 사이트 시스템](#BKMK_SiteSiteServerLog)  

    - [사이트 서버 설치](#BKMK_SiteInstallLog)

    - [데이터 웨어하우스 서비스 지점](#BKMK_DataWarehouse)

    - [대체 상태 지점](#BKMK_FSPLog)  

    - [관리 지점](#BKMK_MPLog)  

    - [서비스 연결 지점](#BKMK_WITLog)  

    - [소프트웨어 업데이트 지점](#BKMK_SUPLog)  

- [함수별 로그 파일](#BKMK_FunctionLogs)  

    - [애플리케이션 관리](#BKMK_AppManageLog)  

    - [Asset Intelligence](#BKMK_AILog)  

    - [백업 및 복구](#BKMK_BnRLog)  

    - [인증서 등록](#BKMK_CertificateEnrollment)

    - [클라이언트 알림](#BKMK_BGB)

    - [클라우드 관리 게이트웨이](#cloud-management-gateway)

    - [준수 설정 및 회사 리소스 액세스](#BKMK_CompSettingsLog)  

    - [조건부 액세스](#BKMK_CA)

    - [Configuration Manager 콘솔](#BKMK_ConsoleLog)  

    - [콘텐츠 관리](#BKMK_ContentLog)  

    - [Desktop Analytics](#desktop-analytics)

    - [검색](#BKMK_DiscoveryLog)  

    - [Endpoint Protection](#BKMK_EPLog)  

    - [확장](#BKMK_Extensions)  

    - [인벤토리](#BKMK_InventoryLog)  

    - [마이그레이션](#BKMK_MigrationLog)  

    - [모바일 디바이스](#BKMK_MDMLog)  

    - [OS 배포](#BKMK_OSDLog)  

    - [전원 관리](#BKMK_PowerMgmtLog)  

    - [원격 제어](#BKMK_RCLog)  

    - [보고](#BKMK_ReportLog)  

    - [역할 기반 관리](#BKMK_RBALog)  

    - [소프트웨어 계량](#BKMK_MeteringLog)  

    - [소프트웨어 업데이트](#BKMK_SU_NAPLog)  

    - [Wake On LAN](#BKMK_WOLLog)  

    - [Windows 10 서비스](#BKMK_WindowsServicingLog)

    - [Windows 업데이트 에이전트](#BKMK_WULog)  

    - [WSUS 서버](#BKMK_WSUSLog)  


## <a name="BKMK_ClientLogs"></a> 클라이언트 로그 파일

다음 섹션에는 클라이언트 작업 및 클라이언트 설치와 관련된 로그 파일이 나와 있습니다.  

### <a name="BKMK_ClientOpLogs"></a> 클라이언트 작업

다음 표에는 Configuration Manager 클라이언트에 있는 로그 파일이 나와 있습니다.  

|로그 이름|설명|  
|--------------|-----------------|  
|CAS.log|콘텐츠 액세스 서비스입니다. 클라이언트의 로컬 패키지 캐시를 유지 관리합니다.|  
|Ccm32BitLauncher.log|*32비트로 실행*으로 표시된 클라이언트에서 애플리케이션을 시작하는 작업을 기록합니다.|  
|CcmEval.log|Configuration Manager 클라이언트 상태 평가 활동 및 Configuration Manager 클라이언트에 필요한 구성 요소에 관한 세부 정보를 기록합니다.|  
|CcmEvalTask.log|평가 예약 작업에 의해 시작된 Configuration Manager 클라이언트 상태 평가 활동을 기록합니다.|  
|CcmExec.log|클라이언트 및 SMS 에이전트 호스트 서비스의 활동을 기록합니다. 이 로그 파일에는 절전 모드 해제 프록시를 사용하거나 사용하지 않도록 설정하는 작업에 대한 정보도 포함됩니다.|  
|CcmMessaging.log|클라이언트와 관리 지점 간의 통신과 관련된 활동을 기록합니다.|  
|CCMNotificationAgent.log|클라이언트 알림 작업과 관련된 활동을 기록합니다.|  
|Ccmperf.log|클라이언트 성능 카운터와 관련된 데이터의 유지 관리 및 캡처와 관련된 활동을 기록합니다.|  
|CcmRestart.log|클라이언트 서비스 다시 시작 활동을 기록합니다.|  
|CCMSDKProvider.log|클라이언트 SDK 인터페이스에 대한 활동을 기록합니다.|  
|CertificateMaintenance.log|Active Directory Domain Services 및 관리 지점의 인증서를 유지 관리합니다.|  
|CIDownloader.log|구성 항목 정의 다운로드에 대한 세부 정보를 기록합니다.|  
|CITaskMgr.log|각 애플리케이션 및 배포 유형(예: 콘텐츠 다운로드, 설치 또는 제거 작업)에 대해 시작된 작업을 기록합니다.|  
|ClientAuth.log|클라이언트의 서명 및 인증 활동을 기록합니다.|  
|ClientIDManagerStartup.log|클라이언트 GUID를 만들고 유지 관리하며 클라이언트 등록 및 할당 중에 수행된 작업을 식별합니다.|  
|ClientLocation.log|클라이언트 사이트 할당과 관련된 작업을 기록합니다.|  
|CMHttpsReadiness.log|Configuration Manager HTTPS 준비 평가 도구를 실행한 결과를 기록합니다. 이 도구는 Configuration Manager에 사용할 수 있는 PKI(공개 키 인프라) 클라이언트 인증 인증서가 컴퓨터에 있는지 확인합니다.|  
|CmRcService.log|원격 제어 서비스에 대한 정보를 기록합니다.|  
|CoManagementHandler.log|클라이언트에서 공동 관리의 문제를 해결하려면 사용합니다.|
|ContentTransferManager.log|BITS(Background Intelligent Transfer Service) 또는 SMB(서버 메시지 블록)에서 패키지를 다운로드하거나 액세스할 일정을 예약합니다.|  
|DataTransferService.log|정책 또는 패키지 액세스에 대한 모든 BITS 통신을 기록합니다.|  
|EndpointProtectionAgent|System Center Endpoint Protection 클라이언트의 설치 및 해당 클라이언트에 대한 맬웨어 방지 정책 적용에 대한 정보를 기록합니다.|  
|execmgr.log|클라이언트에서 실행하는 패키지 및 작업 순서에 대한 세부 정보를 기록합니다.|  
|ExpressionSolver.log|자세한 정보 또는 디버그 로깅을 켤 때 사용되는 향상된 검색 방법에 대한 세부 정보를 기록합니다.|  
|ExternalEventAgent.log|Endpoint Protection 맬웨어 검색 기록 및 클라이언트 상태와 관련된 이벤트를 기록합니다.|  
|FileBITS.log|모든 SMB 패키지 액세스 작업을 기록합니다.|  
|FileSystemFile.log|소프트웨어 인벤토리 및 파일 컬렉션에 대한 WMI(Windows Management Instrumentation) 공급자의 활동을 기록합니다.|  
|FSPStateMessage.log|클라이언트가 대체 상태 지점에 보내는 상태 메시지에 대한 활동을 기록합니다.|  
|InternetProxy.log|클라이언트의 네트워크 프록시 구성 및 사용 활동을 기록합니다.|  
|InventoryAgent.log|클라이언트의 하드웨어 인벤토리, 소프트웨어 인벤토리 및 하트비트 검색 작업에 대한 활동을 기록합니다.|  
|LocationCache.log|클라이언트의 위치 캐시 사용 및 유지 관리에 대한 활동을 기록합니다.|  
|LocationServices.log|관리 지점, 소프트웨어 업데이트 지점 및 배포 지점을 찾는 클라이언트 활동을 기록합니다.|  
|M365AHandler.log|Desktop Analytics 설정 정책에 대한 정보|
|MaintenanceCoordinator.log|클라이언트의 일반 유지 관리 작업에 대한 활동을 기록합니다.|  
|Mifprovider.log|MIF(관리 정보 형식) 파일에 대한 WMI 공급자의 활동을 기록합니다.|  
|mtrmgr.log|모든 소프트웨어 계량 프로세스를 모니터링합니다.|  
|PolicyAgent.log|데이터 전송 서비스를 사용하여 만든 정책에 대한 요청을 기록합니다.|  
|PolicyAgentProvider.log|정책 변경 내용을 기록합니다.|  
|PolicyEvaluator.log|소프트웨어 업데이트의 정책을 포함한 클라이언트 컴퓨터의 정책에 대한 평가와 관련된 세부 정보를 기록합니다.|  
|PolicyPlatformClient.log|파일 공급자를 제외하고 \Program Files\Microsoft Policy Platform에 있는 모든 공급자의 재구성 및 준수 프로세스를 기록합니다.|  
|PolicySdk.log|정책 시스템 SDK 인터페이스에 대한 활동을 기록합니다.|  
|Pwrmgmt.log|절전 모드 해제 프록시 클라이언트 설정을 사용하거나 사용하지 않도록 설정하고 구성하는 데 대한 정보를 기록합니다.|  
|PwrProvider.log|WMI 서비스에서 호스트되는 전원 관리 공급자(PWRInvProvider)의 활동을 기록합니다. 지원되는 모든 Windows 버전에서 공급자는 하드웨어 인벤토리 중에 컴퓨터의 현재 설정을 열거하고 전원 계획 설정을 적용합니다.|  
|SCClient_&lt;*도메인*\>@&lt;*사용자 이름*\>_1.log|클라이언트 컴퓨터의 지정된 사용자에 대한 소프트웨어 센터의 활동을 기록합니다.|  
|SCClient_&lt;*도메인*\>@&lt;*사용자 이름*\>_2.log|클라이언트 컴퓨터의 지정된 사용자에 대한 소프트웨어 센터의 이전 활동을 기록합니다.|  
|Scheduler.log|모든 클라이언트 작업에 대해 예약된 작업의 활동을 기록합니다.|  
|SCNotify_&lt;*도메인*\>@&lt;*사용자 이름*\>_1.log|지정된 사용자의 소프트웨어에 대해 사용자에게 알리는 활동을 기록합니다.|  
|SCNotify_&lt;*도메인*\>@&lt;*사용자 이름*\>_1-&lt; *날짜\_시간*>.log|지정된 사용자의 소프트웨어에 대해 사용자에게 알리는 이전 정보를 기록합니다.|  
|setuppolicyevaluator.log|WMI의 구성 및 인벤토리 정책 작성을 기록합니다.|  
|SleepAgent_&lt;*도메인*\>@SYSTEM_0.log|절전 모드 해제 프록시에 대한 기본 로그 파일입니다.|  
|smscliui.log|제어판에서 Configuration Manager 클라이언트의 사용을 기록합니다.|  
|SrcUpdateMgr.log|설치된 후 현재 배포 지점 원본 위치로 업데이트된 Windows Installer 애플리케이션의 활동을 기록합니다.|  
|StatusAgent.log|클라이언트 구성 요소에서 만든 상태 메시지를 기록합니다.|  
|SWMTRReportGen.log|계량 에이전트에서 수집한 사용 데이터 보고서를 생성합니다. 이 데이터는 Mtrmgr.log에 기록됩니다.|  
|UserAffinity.log|사용자 디바이스 선호도에 대한 세부 정보를 기록합니다.|  
|VirtualApp.log|Application Virtualization(App-V) 배포 유형의 평가에 관한 정보를 기록합니다.|  
|Wedmtrace.log|Windows Embedded 클라이언트의 쓰기 필터와 관련된 작업을 기록합니다.|  
|wakeprxy install.log|클라이언트가 절전 모드 해제 프록시를 켜는 클라이언트 설정 옵션을 받을 경우의 설치 정보를 기록합니다.|  
|wakeprxy-uninstall.log|이전에 절전 모드 해제 프록시를 켠 경우 클라이언트가 절전 모드 해제 프록시를 끄는 클라이언트 설정 옵션을 받을 경우 절전 모드 해제 프록시 제거에 대한 정보를 기록합니다.|  

### <a name="BKMK_ClientInstallLog"></a> 클라이언트 설치

다음 표에는 Configuration Manager 클라이언트의 설치와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|  
|--------------|-----------------|  
|ccmsetup.log|클라이언트 설정, 클라이언트 업그레이드 및 클라이언트 제거에 대한 ccmsetup.exe 작업을 기록합니다. 클라이언트 설치 문제를 해결하는 데 사용할 수 있습니다.|  
|ccmsetup ccmeval.log|클라이언트 상태 및 재구성에 대한 ccmsetup.exe 작업을 기록합니다.|  
|CcmRepair.log|클라이언트 에이전트의 복구 활동을 기록합니다.|  
|client.msi.log|client.msi를 통해 수행된 설치 작업을 기록합니다. 클라이언트 설치 또는 제거 문제를 해결하는 데 사용할 수 있습니다.|  

### <a name="BKMK_LogFilesforLnU"></a> Linux 및 UNIX용 클라이언트

> [!Important]  
> 버전 1902부터 Configuration Manager는 Linux 또는 UNIX 클라이언트를 지원하지 않습니다.
>
> 따라서 Linux 서버를 관리하려면 Microsoft Azure 관리를 고려해야 합니다. Azure 솔루션은 대부분의 경우 Linux용 엔드투엔드 패치 관리를 포함하여 Configuration Manager 기능을 능가하는 광범위한 Linux 지원을 제공합니다.

Linux 및 UNIX용 Configuration Manager 클라이언트는 다음 로그 파일에 정보를 기록합니다.  

> [!TIP]
> CMTrace를 사용하여 Linux 및 UNIX 클라이언트의 로그 파일을 봅니다.

|로그 이름|세부 정보|
|-------------------|-----------------------------------------------------------------|
|Scxcm.log| Linux 및 UNIX용 Configuration Manager 클라이언트의 핵심 서비스(ccmexec.bin)에 대한 로그 파일입니다. 이 로그 파일에는 ccmexec.bin의 설치 및 진행 중인 작업에 대한 정보가 포함됩니다.<br /><br /> 이 로그 파일은 기본적으로 **/var/opt/microsoft/scxcm.log**에 있습니다.<br /><br /> 이 로그 파일의 위치를 변경하려면 **/opt/microsoft/configmgr/etc/scxcm.conf** 를 편집하고 **경로** 필드를 변경합니다. 변경 사항을 적용하기 위해 클라이언트 컴퓨터 또는 서비스를 다시 시작하지 않아도 됩니다.<br /><br /> 로그 수준은 다음 네 가지 설정 중 하나로 설정할 수 있습니다. |
| Scxcmprovider.log |Linux 및 UNIX용 Configuration Manager 클라이언트의 CIM 서비스(omiserver.bin)에 대한 로그 파일입니다. 이 로그 파일에는 nwserver.bin의 지속적인 작업에 대한 정보가 포함됩니다.<br /><br /> 이 로그는 <strong>/var/opt/microsoft/configmgr/scxcmprovider.log</strong>에 있습니다.<br /><br /> 이 로그 파일의 위치를 변경하려면 **/opt/microsoft/omi/etc/scxcmprovider.conf** 를 편집하고 **경로** 필드를 변경합니다. 변경 사항을 적용하기 위해 클라이언트 컴퓨터 또는 서비스를 다시 시작하지 않아도 됩니다.<br /><br /> 로그 수준은 다음 세 가지 설정 중 하나로 설정할 수 있습니다.|

두 로그 파일은 여러 수준의 로깅을 지원합니다.  

- **scxcm.log**. 로그 수준을 변경하려면 **/opt/microsoft/configmgr/etc/scxcm.conf** 를 편집하고 **MODULE** 태그의 각 인스턴스를 원하는 로그 수준으로 변경합니다.  

    - 오류: 주의가 필요한 문제를 나타냄  

    - 경고: 클라이언트 작업에 대해 발생 가능한 문제를 나타냄  

    - 정보: 클라이언트의 다양한 이벤트 상태를 나타내는 자세한 로깅  

    - 추적: 일반적으로 문제를 진단하는 데 사용되는 자세한 정보 로깅  

- **scxcmprovider.log**. 로그 수준을 변경하려면 **/opt/microsoft/omi/etc/ scxcmprovider.conf**를 편집하여 **MODULE** 태그의 각 인스턴스를 원하는 로그 수준으로 변경합니다.  

    - 오류: 주의가 필요한 문제를 나타냄  

    - 경고: 클라이언트 작업에 대해 발생 가능한 문제를 나타냄

    - 정보: 클라이언트의 다양한 이벤트 상태를 나타내는 자세한 로깅  

정상 작동 상태에서는 ERROR 로그 수준을 사용합니다. 이 로그 수준이 가장 작은 로그 파일을 만듭니다. 로그 수준을 ERROR에서 WARNING, INFO, TRACE 등으로 올리는 경우 더 많은 데이터가 파일에 기록되므로 더 큰 로그 파일이 생성됩니다.  

#### <a name="BKMK_ManageLinuxLogs"></a> Linux 및 UNIX 클라이언트용 로그 파일 관리

Linux와 UNIX의 클라이언트는 클라이언트 로그 파일의 최대 크기를 제한하지 않습니다. 또한 .log 파일의 콘텐츠를 .lo_ 파일 등의 다른 파일에 자동으로 복사하지도 않습니다. 로그 파일의 최대 크기를 제한하려면 Linux 및 UNIX Configuration Manager 클라이언트로부터 독립적인 로그 파일을 관리하는 프로세스를 구현합니다.  

예를 들어 표준 Linux 및 UNIX 명령 **logrotate**를 사용하여 클라이언트 로그 파일의 크기 및 회전을 관리할 수 있습니다. Linux 및 UNIX용 Configuration Manager 클라이언트에는 **logrotate**가 로그 회전 완료 시 클라이언트에 신호를 보내 클라이언트가 로그 파일에 로깅을 다시 시작할 수 있도록 하는 인터페이스가 있습니다.  

**logrotate**에 대한 자세한 내용은 사용 중인 Linux 및 UNIX 배포에 대한 설명서를 참조하세요.  

### <a name="BKMK_LogfilesforMac"></a> Mac 컴퓨터용 클라이언트

Mac 컴퓨터용 Configuration Manager 클라이언트는 다음 로그 파일에 정보를 기록합니다.  

|로그 이름|세부 정보|  
|--------------|-------------|  
|CCMClient-&lt;*날짜_시간*>.log|애플리케이션 관리, 인벤토리, 오류 로그 등 Mac 클라이언트 작업과 관련된 활동을 기록합니다.<br /><br /> 이 로그 파일은 Mac 컴퓨터의 /Library/Application Support/Microsoft/CCM/Logs 폴더에 있습니다.|  
|CCMAgent-&lt;*날짜_시간*>.log|사용자 로그인/로그아웃 작업 및 Mac 컴퓨터 작업을 포함하여 클라이언트 작업과 관련된 정보를 기록합니다.<br /><br /> 이 로그 파일은 Mac 컴퓨터의 ~/Library/Logs 폴더에 있습니다.|  
|CCMNotifications-&lt;*날짜_시간*>.log|Mac 컴퓨터에 표시된 Configuration Manager 알림과 관련된 작업을 기록합니다.<br /><br /> 이 로그 파일은 Mac 컴퓨터의 ~/Library/Logs 폴더에 있습니다.|  
|CCMPrefPane-&lt;*날짜_시간*>.log|일반 상태 및 오류 로그를 포함하여 Mac 컴퓨터의 Configuration Manager 기본 설정 대화 상자와 관련된 작업을 기록합니다.<br /><br /> 이 로그 파일은 Mac 컴퓨터의 ~/Library/Logs 폴더에 있습니다.|  

사이트 시스템 서버의 **SMS_DM.log** 로그 파일은 모바일 디바이스와 Mac 컴퓨터에 설정된 관리 지점과 Mac 컴퓨터 간의 통신도 기록합니다.  


## <a name="BKMK_ServerLogs"></a> 서버 로그 파일

다음 섹션에는 사이트 서버에 있는 로그 파일 또는 특정 사이트 시스템 역할과 관련된 로그 파일이 나와 있습니다.  

### <a name="BKMK_SiteSiteServerLog"></a> 사이트 서버 및 사이트 시스템

다음 표에는 Configuration Manager 사이트 서버 및 사이트 시스템 서버에 있는 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|adctrl.log|등록 처리 작업을 기록합니다.|사이트 서버|  
|ADForestDisc.log|Active Directory 포리스트 검색 작업을 기록합니다.|사이트 서버|  
|adminservice.log|SMS 공급자 관리에 서비스 REST API의 작업 기록|SMS 공급자가 설치된 컴퓨터|
|ADService.log|Active Directory의 계정 만들기 및 보안 그룹 세부 정보를 기록합니다.|사이트 서버|  
|adsgdis.log|Active Directory 그룹 검색 작업을 기록합니다.|사이트 서버|  
|adsysdis.log|Active Directory 시스템 검색 작업을 기록합니다.|사이트 서버|  
|adusrdis.log|Active Directory 사용자 검색 작업을 기록합니다.|사이트 서버|  
|ccm.log|클라이언트 강제 설치 작업을 기록합니다.|사이트 서버|  
|CertMgr.log|사이트 간 통신을 위한 인증서 활동을 기록합니다.|사이트 시스템 서버|  
|chmgr.log|클라이언트 상태 관리자의 작업을 기록합니다.|사이트 서버|  
|Cidm.log|CIDM(클라이언트 설치 데이터 관리자)에 의해 변경된 클라이언트 설정을 기록합니다.|사이트 서버|  
|colleval.log|컬렉션 평가기에서 컬렉션을 만들고 변경하고 삭제한 경우 관련 세부 정보를 기록합니다.|사이트 서버|  
|compmon.log|사이트 서버에 대해 모니터링되는 구성 요소 스레드의 상태를 기록합니다.|사이트 시스템 서버|  
|compsumm.log|구성 요소 상태 요약 작성기 작업을 기록합니다.|사이트 서버|  
|ComRegSetup.log|사이트 서버의 초기 COM 등록 설치 결과를 기록합니다.|사이트 시스템 서버|  
|dataldr.log|Configuration Manager 데이터베이스에서 MIF 파일 및 하드웨어 인벤토리 처리 작업에 대한 정보를 기록합니다.|사이트 서버|  
|ddm.log|검색 데이터 관리자의 작업을 기록합니다.|사이트 서버|  
|despool.log|들어오는 사이트 간 통신 전송을 기록합니다.|사이트 서버|  
|distmgr.log|패키지 만들기, 압축, 델타 복제, 정보 업데이트 등과 관련된 세부 정보를 기록합니다.|사이트 서버|  
|EPCtrlMgr.log|Endpoint Protection 사이트 시스템 역할 서버에서 Configuration Manager 데이터베이스로의 맬웨어 위협 정보 동기화에 대한 정보를 기록합니다.|사이트 서버|  
|EPMgr.log|Endpoint Protection 사이트 시스템 역할의 상태를 기록합니다.|사이트 시스템 서버|  
|EPSetup.log|Endpoint Protection 사이트 시스템 역할의 설치에 대한 정보를 제공합니다.|사이트 시스템 서버|  
|EnrollSrv.log|등록 서비스 프로세스의 작업을 기록합니다.|사이트 시스템 서버|  
|EnrollWeb.log|등록 웹 사이트 프로세스의 작업을 기록합니다.|사이트 시스템 서버|  
|fspmgr.log|대체 상태 지점 사이트 시스템 역할의 작업을 기록합니다.|사이트 시스템 서버|  
|hman.log|Active Directory Domain Services의 사이트 정보 게시 및 사이트 구성 변경에 대한 정보를 기록합니다.|사이트 서버|  
|Inboxast.log|관리 지점에서 사이트 서버의 해당 INBOXES 폴더로 이동한 파일을 기록합니다.|사이트 서버|  
|inboxmgr.log|수신함 폴더 간의 파일 전송 작업을 기록합니다.|사이트 서버|  
|inboxmon.log|수신함 파일의 처리 정보 및 성능 카운터 업데이트를 기록합니다.|사이트 서버|  
|invproc.log|보조 사이트에서 해당 부모 사이트로 전달된 MIF 파일을 기록합니다.|사이트 서버|  
|migmctrl.log|마이그레이션 작업, 공유 배포 지점 및 배포 지점 업그레이드와 관련된 마이그레이션 작업에 대한 정보를 기록합니다.|Configuration Manager 계층 구조의 최상위 사이트 및 각 하위 기본 사이트.<br /><br /> 기본 사이트가 여러 개인 계층 구조인 경우 중앙 관리 사이트에 만들어진 로그 파일을 사용합니다.|  
|mpcontrol.log|관리 지점의 WINS(Windows Internet Name Service) 등록을 기록합니다. 10분마다 관리 지점의 가용성을 기록합니다.|사이트 시스템 서버|  
|mpfdm.log|클라이언트 파일을 사이트 서버의 해당 INBOXES 폴더로 이동한 관리 지점 구성 요소의 작업을 기록합니다.|사이트 시스템 서버|  
|mpMSI.log|관리 지점 설치에 대한 세부 정보를 기록합니다.|사이트 서버|  
|MPSetup.log|관리 지점 설치 래퍼 프로세스를 기록합니다.|사이트 서버|  
|netdisc.log|네트워크 검색 작업을 기록합니다.|사이트 서버|  
|NotiCtrl.log|애플리케이션 요청 알림입니다.|사이트 서버|  
|ntsvrdis.log|사이트 시스템 서버의 검색 작업을 기록합니다.|사이트 서버|  
|Objreplmgr|복제를 위해 개체 변경 알림 처리 정보를 기록합니다.|사이트 서버|  
|offermgr.log|보급 알림 업데이트를 기록합니다.|사이트 서버|  
|offersum.log|배포 상태 메시지의 요약 정보를 기록합니다.|사이트 서버|  
|OfflineServicingMgr.log|운영 체제 이미지 파일에 업데이트를 적용한 작업을 기록합니다.|사이트 서버|  
|outboxmon.log|발신함 파일의 처리 정보 및 성능 카운터 업데이트를 기록합니다.|사이트 서버|  
|PerfSetup.log|성능 카운터의 설치 결과를 기록합니다.|사이트 시스템 서버|  
|PkgXferMgr.log|기본 사이트에서 원격 배포 지점으로 콘텐츠를 보내는 SMS Executive 구성 요소의 작업을 기록합니다.|사이트 서버|  
|policypv.log|클라이언트 설정 또는 배포의 변경 내용을 반영하도록 클라이언트 정책의 업데이트를 기록합니다.|기본 사이트 서버|  
|rcmctrl.log|계층 내 사이트 간의 데이터베이스 복제 작업을 기록합니다.|사이트 서버|  
|replmgr.log|사이트 서버 구성 요소와 스케줄러 구성 요소 간의 파일 복제를 기록합니다.|사이트 서버|  
|ResourceExplorer.log|리소스 탐색기 실행과 관련된 오류, 경고, 정보 등을 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|ruleengine.log|식별, 콘텐츠 다운로드, 소프트웨어 업데이트 그룹, 배포 만들기 등 자동 배포 규칙에 대한 세부 정보를 기록합니다.|사이트 서버|  
|schedule.log|사이트 간 작업 및 파일 복제와 관련된 세부 정보를 기록합니다.|사이트 서버|  
|sender.log|사이트 간 파일 기반 복제 시 전송되는 파일을 기록합니다.|사이트 서버|  
|sinvproc.log|사이트 데이터베이스에 대한 소프트웨어 인벤토리 데이터의 처리에 대한 정보를 기록합니다.|사이트 서버|  
|sitecomp.log|사이트의 모든 사이트 시스템 서버에 설치된 사이트 구성 요소의 유지 관리 관련 세부 정보를 기록합니다.|사이트 서버|  
|sitectrl.log|데이터베이스의 사이트 제어 개체에 적용된 사이트 설정 변경 내용을 기록합니다.|사이트 서버|  
|sitestat.log|모든 사이트 시스템의 가용성 및 디스크 공간 모니터링 프로세스를 기록합니다.|사이트 서버|
|SMS_AZUREAD_DISCOVERY_AGENT.log| Azure Active Directory에의 컬렉션 멤버 자격 결과 동기화에 대한 로그 파일입니다. 이 기능은 Configuration Manager 버전 1906부터 시험판으로 처음 도입되었습니다.| 사이트 서버|
|SMS_ISVUPDATES_SYNCAGENT.log| Configuration Manager 버전 1806부터 시작되는 타사 소프트웨어 동기화에 대한 로그 파일입니다.| Configuration Manager 계층 구조의 최상위 수준 소프트웨어 업데이트 지점입니다.|
|SMS_PhasedDeployment.log| 단계적 배포에 대한 로그 파일|Configuration Manager 계층 구조의 최상위 사이트|   
|SmsAdminUI.log|Configuration Manager 콘솔 작업을 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|SMSAWEBSVCSetup.log|애플리케이션 카탈로그 웹 서비스의 설치 작업을 기록합니다.|사이트 시스템 서버|  
|smsbkup.log|사이트 백업 프로세스의 출력을 기록합니다.|사이트 서버|  
|smsdbmon.log|데이터베이스 변경 내용을 기록합니다.|사이트 서버|  
|SMSENROLLSRVSetup.log|등록 웹 서비스의 설치 작업을 기록합니다.|사이트 시스템 서버|  
|SMSENROLLWEBSetup.log|등록 웹 사이트의 설치 작업을 기록합니다.|사이트 시스템 서버|  
|smsexec.log|모든 사이트 서버 구성 요소 스레드의 처리 작업을 기록합니다.|사이트 서버 또는 사이트 시스템 서버|  
|SMSFSPSetup.log|대체 상태 지점 설치 시 생성된 메시지를 기록합니다.|사이트 시스템 서버|  
|SMSPORTALWEBSetup.log|애플리케이션 카탈로그 웹 사이트의 설치 작업을 기록합니다.|사이트 시스템 서버|  
|SMSProv.log|사이트 데이터베이스에 대한 WMI 공급자 액세스를 기록합니다.|SMS 공급자가 설치된 컴퓨터|  
|srsrpMSI.log|보고 지점 설치 프로세스의 세부적인 MSI 출력 결과를 기록합니다.|사이트 시스템 서버|  
|srsrpsetup.log|보고 지점 설치 프로세스의 결과를 기록합니다.|사이트 시스템 서버|  
|statesys.log|상태 시스템 메시지의 처리 정보를 기록합니다.|사이트 서버|  
|statmgr.log|데이터베이스에 기록된 모든 상태 메시지를 기록합니다.|사이트 서버|  
|swmproc.log|계량 파일 및 설정의 처리 정보를 기록합니다.|사이트 서버|  

### <a name="BKMK_SiteInstallLog"></a> 사이트 서버 설치

다음 표에는 사이트 설치와 관련된 정보가 있는 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|ConfigMgrPrereq.log|필수 구성 요소 평가 및 설치 작업을 기록합니다.|사이트 서버|  
|ConfigMgrSetup.log|사이트 서버 설치 프로그램에서 출력된 세부 정보를 기록합니다.|사이트 서버|  
|ConfigMgrSetupWizard.log|설치 마법사의 작업과 관련된 정보를 기록합니다.|사이트 서버|  
|SMS_BOOTSTRAP.log|시작한 보조 사이트 설치 프로세스의 진행률 정보를 기록합니다. 실제 설치 프로세스에 대한 세부 정보는 ConfigMgrSetup.log에 포함되어 있습니다.|사이트 서버|  
|smstsvc.log|연결을 시작하는 서버의 컴퓨터 계정을 통해 네트워크 연결과 사이트 간 사용 권한을 테스트하는 데 사용되는 Windows 서비스의 설치, 사용 및 제거에 대한 정보를 기록합니다.|사이트 서버 및 사이트 시스템 서버|  

### <a name="BKMK_DataWarehouse"></a> 데이터 웨어하우스 서비스 지점

다음 표에는 데이터 웨어하우스 서비스 지점과 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|DWSSMSI.log|데이터 웨어하우스 서비스 지점 설치 시 생성된 메시지를 기록합니다.|사이트 시스템 서버|  
|DWSSSetup.log|데이터 웨어하우스 서비스 지점 설치 시 생성된 메시지를 기록합니다.|사이트 시스템 서버|  
|Microsoft.ConfigMgrDataWarehouse.log|사이트 데이터베이스와 데이터 웨어하우스 데이터베이스 간의 데이터 동기화에 대한 정보를 기록합니다.|사이트 시스템 서버|  

### <a name="BKMK_FSPLog"></a> 대체 상태 지점

다음 표에는 대체 상태 지점과 관련된 정보가 있는 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|FspIsapi|대체 상태 지점과 모바일 디바이스 기존 클라이언트 및 클라이언트 컴퓨터 간에 수행되는 통신 관련 세부 정보를 기록합니다.|사이트 시스템 서버|  
|fspMSI.log|대체 상태 지점 설치 시 생성된 메시지를 기록합니다.|사이트 시스템 서버|  
|fspmgr.log|대체 상태 지점 사이트 시스템 역할의 작업을 기록합니다.|사이트 시스템 서버|  

### <a name="BKMK_MPLog"></a> 관리 지점

다음 표에는 관리 지점과 관련된 정보가 있는 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CcmIsapi.log|엔드포인트의 클라이언트 메시징 작업을 기록합니다.|사이트 시스템 서버|  
|MP_CliReg.log|관리 지점에서 처리한 클라이언트 등록 작업을 기록합니다.|사이트 시스템 서버|  
|MP_Ddr.log|클라이언트에서 XML.ddr 레코드를 변환하여 사이트 서버에 복사하는 작업을 기록합니다.|사이트 시스템 서버|  
|MP_Framework.log|핵심 관리 지점 및 클라이언트 프레임워크 구성 요소의 작업을 기록합니다.|사이트 시스템 서버|  
|MP_GetAuth.log|클라이언트의 권한 부여 작업을 기록합니다.|사이트 시스템 서버|  
|MP_GetPolicy.log|클라이언트 컴퓨터의 정책 요청 작업을 기록합니다.|사이트 시스템 서버|  
|MP_Hinv.log|클라이언트의 XML 하드웨어 인벤토리 레코드를 변환하여 해당 파일을 사이트 서버에 복사하는 작업과 관련된 세부 정보를 기록합니다.|사이트 시스템 서버|  
|MP_Location.log|클라이언트의 위치 요청 및 응답 작업을 기록합니다.|사이트 시스템 서버|  
|MP_OOBMgr.log|클라이언트에서 OTP를 수신하는 것과 관련된 관리 지점 활동을 기록합니다.|사이트 시스템 서버|  
|MP_Policy.log|정책 통신을 기록합니다.|사이트 시스템 서버|  
|MP_Relay.log|클라이언트에서 수집한 파일의 전송을 기록합니다.|사이트 시스템 서버|  
|MP_Retry.log|하드웨어 인벤토리 재시도 프로세스를 기록합니다.|사이트 시스템 서버|  
|MP_Sinv.log|클라이언트의 XML 소프트웨어 인벤토리 레코드를 변환하여 해당 파일을 사이트 서버에 복사하는 작업과 관련된 세부 정보를 기록합니다.|사이트 시스템 서버|  
|MP_SinvCollFile.log|파일 컬렉션에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|MP_Status.log|클라이언트의 XML.svf 상태 메시지 파일을 변환하여 해당 파일을 사이트 서버에 복사하는 작업과 관련된 세부 정보를 기록합니다.|사이트 시스템 서버|
|mpcontrol.log|관리 지점의 WINS 등록을 기록합니다. 10분마다 관리 지점의 가용성을 기록합니다.|사이트 서버|  
|mpfdm.log|클라이언트 파일을 사이트 서버의 해당 INBOXES 폴더로 이동한 관리 지점 구성 요소의 작업을 기록합니다.|사이트 시스템 서버|  
|mpMSI.log|관리 지점 설치에 대한 세부 정보를 기록합니다.|사이트 서버|  
|MPSetup.log|관리 지점 설치 래퍼 프로세스를 기록합니다.|사이트 서버|  
|UserService.log|소프트웨어 센터에서 사용자 요청을 기록하며 사용자가 사용할 수 있는 서버의 애플리케이션을 검색하고 설치합니다.|사이트 시스템 서버|

### <a name="BKMK_WITLog"></a> 서비스 연결 지점

다음 표에는 서비스 연결 지점과 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CertMgr.log|인증서 및 프록시 계정 정보를 기록합니다.|사이트 서버|  
|CollEval.log|컬렉션 평가기에서 컬렉션을 만들고 변경하고 삭제한 경우 관련 세부 정보를 기록합니다.|기본 사이트 및 중앙 관리 사이트|  
|Cloudusersync.log|사용자의 라이선스 사용을 기록합니다.|서비스 연결 지점이 있는 컴퓨터|  
|Dataldr.log|MIF 파일 처리와 관련된 정보를 기록합니다.|사이트 서버|  
|ddm.log|검색 데이터 관리자의 작업을 기록합니다.|사이트 서버|  
|distmgr.log|콘텐츠 배포 요청에 대한 세부 정보를 기록합니다.|최상위 사이트 서버|  
|Dmpdownloader.log|Microsoft Intune의 다운로드에 대한 세부 정보를 기록합니다.|서비스 연결 지점이 있는 컴퓨터|  
|Dmpuploader.log|데이터베이스 변경 내용을 Microsoft Intune에 업로드하는 작업과 관련된 세부 정보를 기록합니다.|서비스 연결 지점이 있는 컴퓨터|  
|hman.log|메시지 전달에 대한 정보를 기록합니다.|사이트 서버|  
|objreplmgr.log|정책 및 할당 처리 작업을 기록합니다.|기본 사이트 서버|  
|policypv.log|모든 정책의 정책 생성을 기록합니다.|사이트 서버|  
|outgoingcontentmanager.log|Microsoft Intune에 업로드된 콘텐츠를 기록합니다.|서비스 연결 지점이 있는 컴퓨터|  
|Sitecomp.log|서비스 연결 지점 설치 세부 정보를 기록합니다.|사이트 서버|  
|SmsAdminUI.log|Configuration Manager 콘솔 작업을 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|Smsprov.log|SMS 공급자가 수행한 작업을 기록합니다. Configuration Manager 콘솔 작업은 SMS 공급자를 사용합니다.|SMS 공급자가 설치된 컴퓨터|  
|SrvBoot.log|서비스 연결 지점 설치 관리자 서비스 세부 정보를 기록합니다.|서비스 연결 지점이 있는 컴퓨터|  
|statesys.log|모바일 디바이스 관리 메시지의 처리를 기록합니다.|기본 사이트 및 중앙 관리 사이트|  

### <a name="BKMK_SUPLog"></a> 소프트웨어 업데이트 지점

다음 표에는 소프트웨어 업데이트 지점과 관련된 정보가 있는 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|objreplmgr.log|부모 사이트에서 자식 사이트로 소프트웨어 업데이트 알림 파일을 복제하는 작업과 관련된 세부 정보를 기록합니다.|사이트 서버|  
|PatchDownloader.log|소프트웨어 업데이트를 업데이트 원본에서 사이트 서버의 다운로드 대상으로 다운로드하는 프로세스에 대한 세부 정보를 기록합니다.|업데이트를 수동으로 다운로드하면 이 파일이 콘솔을 사용하는 컴퓨터의 `%temp%` 디렉터리에 있습니다. 자동 배포 규칙의 경우 Configuration Manager 클라이언트가 사이트 서버에 설치되었다면 이 파일이 `%windir%\CCM\Logs`의 사이트 서버에 있습니다.|  
|ruleengine.log|식별, 콘텐츠 다운로드, 소프트웨어 업데이트 그룹, 배포 만들기 등 자동 배포 규칙에 대한 세부 정보를 기록합니다.|사이트 서버| 
|SMS_ISVUPDATES_SYNCAGENT.log| Configuration Manager 버전 1806부터 시작되는 타사 소프트웨어 동기화에 대한 로그 파일입니다.| Configuration Manager 계층 구조의 최상위 수준 소프트웨어 업데이트 지점입니다.| 
|SUPSetup.log|소프트웨어 업데이트 지점 설치에 대한 세부 정보를 기록합니다. 소프트웨어 업데이트 지점 설치가 완료되면 이 로그 파일에 **Installation was successful** 이 기록됩니다.|사이트 시스템 서버|  
|WCM.log|소프트웨어 업데이트 지점 구성과 구독된 업데이트 범주, 분류 및 언어를 위한 WSUS 서버 연결에 대한 세부 정보를 기록합니다.|WSUS 서버에 연결하는 사이트 서버|  
|WSUSCtrl.log|사이트에 대한 WSUS 서버의 구성, 데이터베이스 연결 및 상태에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|wsyncmgr.log|소프트웨어 업데이트 동기화 프로세스에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|WUSSyncXML.log|Microsoft 업데이트 동기화 프로세스용 인벤토리 도구에 대한 세부 정보를 기록합니다.|Microsoft 업데이트용 인벤토리 도구에 대한 동기화 호스트로 구성된 클라이언트 컴퓨터|  


## <a name="BKMK_FunctionLogs"></a> 함수별 로그 파일

다음 섹션에는 Configuration Manager 기능과 관련된 로그 파일이 나와 있습니다.  

### <a name="BKMK_AppManageLog"></a> 애플리케이션 관리

다음 표에는 애플리케이션 관리와 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|AppIntentEval.log|애플리케이션의 현재 및 의도 상태, 애플리케이션의 적용 가능성, 요구 사항 충족 여부, 배포 유형 및 종속성에 대한 세부 정보를 기록합니다.|클라이언트|  
|AppDiscovery.log|클라이언트 컴퓨터의 애플리케이션 검색에 대한 세부 정보를 기록합니다.|클라이언트|  
|AppEnforce.log|클라이언트의 애플리케이션에서 수행한 적용 작업(설치 및 제거)에 대한 세부 정보를 기록합니다.|클라이언트|  
|AppGroupHandler.log|애플리케이션 그룹의 검색 및 적용 정보입니다(버전 1906부터).|클라이언트|
|awebsctl.log|애플리케이션 카탈로그 웹 서비스 지점 사이트 시스템 역할에 대한 모니터링 활동을 기록합니다.|사이트 시스템 서버|  
|awebsvcMSI.log|애플리케이션 카탈로그 웹 서비스 지점 사이트 시스템 역할에 대한 자세한 설치 정보를 기록합니다.|사이트 시스템 서버|  
|CCMSDKProvider.log|애플리케이션 관리 SDK의 활동을 기록합니다.|클라이언트|  
|colleval.log|컬렉션 평가기에서 컬렉션을 만들고 변경하고 삭제한 경우 관련 세부 정보를 기록합니다.|사이트 시스템 서버|  
|ConfigMgrSoftwareCatalog.log|Silverlight 사용을 포함한 애플리케이션 카탈로그의 활동을 기록합니다.|클라이언트|  
|NotiCtrl.log|애플리케이션 요청 알림입니다.|사이트 서버|  
|portlctl.log|애플리케이션 카탈로그 웹 사이트 지점 사이트 시스템 역할에 대한 모니터링 활동을 기록합니다.|사이트 시스템 서버|  
|portlwebMSI.log|애플리케이션 카탈로그 웹 사이트 역할에 대한 MSI 설치 활동을 기록합니다.|사이트 시스템 서버|  
|PrestageContent.log|사전 준비된 원격 배포 지점에서 ExtractContent.exe 도구를 사용하는 방법에 대한 세부 정보를 기록합니다. 이 도구는 파일로 내보낸 콘텐츠를 추출합니다.|사이트 시스템 서버|  
|ServicePortalWebService.log|애플리케이션 카탈로그 웹 서비스의 활동을 기록합니다.|사이트 시스템 서버|  
|ServicePortalWebSite.log|애플리케이션 카탈로그 웹 사이트의 활동을 기록합니다.|사이트 시스템 서버|  
|SettingsAgent.log|특정 애플리케이션, 애플리케이션 그룹 평가의 기록 오케스트레이션, 공동 관리 정책의 세부 정보 적용 정보입니다.|클라이언트|
|SMSdpmon.log|배포 지점에 구성된 배포 지점 상태 모니터링 예약 작업에 대한 세부 정보를 기록합니다.|사이트 서버|  
|SoftwareCatalogUpdateEndpoint.log|소프트웨어 센터에 표시된 애플리케이션 카탈로그의 URL을 관리하는 활동을 기록합니다.|클라이언트|  
|SoftwareCenterSystemTasks.log|소프트웨어 센터 필수 구성 요소 유효성 검사와 관련된 활동을 기록합니다.|클라이언트|  

#### <a name="packages-and-programs"></a>패키지 및 프로그램

다음 표에는 패키지 및 프로그램 배포와 관련된 정보를 포함하는 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|colleval.log|컬렉션 평가기에서 컬렉션을 만들고 변경하고 삭제한 경우 관련 세부 정보를 기록합니다.|사이트 서버|  
|execmgr.log|실행하는 패키지 및 작업 순서에 대한 세부 정보를 기록합니다.|클라이언트|  

### <a name="BKMK_AILog"></a> Asset Intelligence

다음 표에는 Asset Intelligence와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|AssetAdvisor.log|Asset Intelligence 인벤토리 작업의 활동을 기록합니다.|클라이언트|  
|aikbmgr.log|Asset Intelligence 카탈로그 업데이트를 위해 수신함에서 XML 파일을 처리하는 데 대한 세부 정보를 기록합니다.|사이트 서버|  
|AIUpdateSvc.log|온라인 웹 서비스인 SCO(System Center Online)와 Asset Intelligence 동기화 지점의 상호 작용을 기록합니다.|사이트 시스템 서버|  
|AIUSMSI.log|Asset Intelligence 동기화 지점 사이트 시스템 역할의 설치에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|AIUSSetup.log|Asset Intelligence 동기화 지점 사이트 시스템 역할의 설치에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|ManagedProvider.log|연결된 소프트웨어 ID 태그로 소프트웨어를 검색하는 데 대한 세부 정보를 기록합니다. 또한 하드웨어 인벤토리와 관련된 활동을 기록합니다.|사이트 시스템 서버|  
|MVLSImport.log|가져온 라이선스 파일의 처리에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  

### <a name="BKMK_BnRLog"></a> 백업 및 복구

다음 표에는 사이트 다시 설정 및 SMS 공급자의 변경을 포함한 백업 및 복구 작업과 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|ConfigMgrSetup.log|Configuration Manager가 백업에서 사이트를 복구하는 경우 설치 및 복구 작업에 대한 정보를 기록합니다.|사이트 서버|  
|Smsbkup.log|사이트 백업 활동에 대한 세부 정보를 기록합니다.|사이트 서버|  
|smssqlbkup.log|사이트 서버가 아닌 서버에 SQL Server를 설치할 때 사이트 데이터베이스 백업 프로세스의 결과를 기록합니다.|사이트 데이터베이스 서버|  
|Smswriter.log|백업 프로세스에서 사용하는 Configuration Manager VSS 작성기의 상태에 대한 정보를 기록합니다.|사이트 서버|  

### <a name="BKMK_CertificateEnrollment"></a> 인증서 등록

다음 표에는 인증서 등록과 관련된 정보가 포함된 Configuration Manager 로그 파일이 나와 있습니다. 인증서 등록은 NDES(네트워크 디바이스 등록 서비스)를 실행하는 서버의 인증서 등록 지점 및 Configuration Manager 정책 모듈을 사용합니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|Crp.log|등록 작업을 기록합니다.|인증서 등록 지점|  
|Crpctrl.log|인증서 등록 지점의 작업 상태를 기록합니다.|인증서 등록 지점|  
|Crpsetup.log|인증서 등록 지점의 설치 및 구성에 대한 세부 정보를 기록합니다.|인증서 등록 지점|  
|Crpmsi.log|인증서 등록 지점의 설치 및 구성에 대한 세부 정보를 기록합니다.|인증서 등록 지점|  
|NDESPlugin.log|문제 확인 및 인증서 등록 작업을 기록합니다.|Configuration Manager 정책 모듈 및 네트워크 디바이스 등록 서비스|  

Configuration Manager 로그 파일뿐 아니라 네트워크 디바이스 등록 서비스를 실행하는 서버와 인증서 등록 지점을 호스트하는 서버의 이벤트 뷰어에서 Windows 응용 프로그램 로그를 검토합니다. 예를 들어 **NetworkDeviceEnrollmentService** 원본에서 메시지를 찾아 봅니다. 

다음 로그 파일도 사용할 수 있습니다.  

- 네트워크 디바이스 등록 서비스에 대한 IIS 로그 파일: **%SYSTEMDRIVE%\inetpub\logs\LogFiles\W3SVC1**  

- 인증서 등록 지점에 대한 IIS 로그 파일: **%SYSTEMDRIVE%\inetpub\logs\LogFiles\W3SVC1**  

- 네트워크 디바이스 등록 정책 로그 파일: **mscep.log**  

    > [!NOTE]  
    > 이 파일은 NDES 계정 프로필의 폴더(예: C:\Users\SCEPSvc)에 있습니다. NDES 로깅 사용 방법에 대한 자세한 내용은 NDES wiki의 [로깅 사용](https://social.technet.microsoft.com/wiki/contents/articles/9063.active-directory-certificate-services-ad-cs-network-device-enrollment-service-ndes.aspx#Enable_Logging) 섹션을 참조하세요.  

### <a name="BKMK_BGB"></a> 클라이언트 알림

다음 표에는 클라이언트 알림과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|bgbmgr.log|클라이언트 알림 작업과 온라인 처리 및 작업 상태 파일과 관련된 사이트 서버 활동에 대한 세부 정보를 기록합니다.|사이트 서버|  
|BGBServer.log|클라이언트 및 서버 간 통신과 클라이언트로 작업 푸시와 같은 알림 서버의 활동을 기록합니다. 또한 사이트 서버로 전송할 온라인 및 작업 상태 파일 생성에 대한 정보도 기록합니다.|관리 지점|  
|BgbSetup.log|설치 및 제거 중 알림 서버 설치 래퍼 프로세스의 활동을 기록합니다.|관리 지점|  
|bgbisapiMSI.log|알림 서버 설치 및 제거에 대한 세부 정보를 기록합니다.|관리 지점|  
|BgbHttpProxy.log|HTTP를 사용하는 클라이언트가 알림 서버와 주고 받는 메시지를 릴레이할 때의 알림 HTTP 프록시의 활동을 기록합니다.|클라이언트|  
|CCMNotificationAgent.log|클라이언트와 서버의 통신과 같은 알림 에이전트의 활동과 수신한 작업 및 다른 클라이언트 에이전트로 발송한 작업에 대한 정보를 기록합니다.|클라이언트|  

### <a name="cloud-management-gateway"></a>클라우드 관리 게이트웨이

다음 표에는 클라우드 관리 게이트웨이와 관련된 정보가 포함된 로그 파일이 나와 있습니다.

|로그 이름|설명|로그 파일이 있는 컴퓨터|
|--------------|-----------------|----------------------------|  
|CloudMgr.log|클라우드 관리 게이트웨이 서비스 배포, 지속적인 서비스 상태 및 서비스와 연결된 사용 데이터에 대한 세부 정보를 기록합니다.<br>레지스트리 키 HKLM\SOFTWARE\ Microsoft\SMS\COMPONENTS\ SMS_CLOUD_ SERVICES_MANAGER의 **로깅 수준** 값을 편집하여 로깅 수준을 구성할 수 있습니다.|기본 사이트 서버 또는 CA의 *installdir* 폴더|
|CMGSetup.log<sup>[참고 1](#bkmk_note1)</sup>|클라우드 관리 게이트웨이 배포의 두 번째 단계(Azure의 로컬 배포)에 대한 세부 정보를 기록합니다.<br>**Azure 포털\클라우드 서비스 구성** 탭에서 설정 **추적 수준**(**정보**(기본값), **자세한 정보**, **오류**)을 사용하여 로깅 수준을 구성할 수 있습니다.|Azure 서버의 **%approot%\logs** 또는 사이트 시스템 서버의 SMS/Logs 폴더|
|CMGHttpHandler.log<sup>[참고 1](#bkmk_note1)</sup>|Azure에서 인터넷 정보 서비스와 바인딩하는 클라우드 관리 게이트웨이 HTTP 처리기에 대한 세부 정보를 기록합니다.<br>**Azure 포털\클라우드 서비스 구성** 탭에서 설정 **추적 수준**(**정보**(기본값), **자세한 정보**, **오류**)을 사용하여 로깅 수준을 구성할 수 있습니다.<br>버전 1806부터 이 로그가 없습니다. 구성 요소 기능이 CMG 서비스 구성 요소에 병합됩니다. 대신 CMGService.log를 참조하세요.<!--SCCMDocs-pr issue #2822-->|Azure 서버의 **%approot%\logs** 또는 사이트 시스템 서버의 SMS/Logs 폴더|
|CMGService.log<sup>[참고 1](#bkmk_note1)</sup>|Azure의 클라우드 관리 게이트웨이 핵심 구성 요소에 대한 세부 정보를 기록합니다.<br>**Azure 포털\클라우드 서비스 구성** 탭에서 설정 **추적 수준**(**정보**(기본값), **자세한 정보**, **오류**)을 사용하여 로깅 수준을 구성할 수 있습니다.|Azure 서버의 **%approot%\logs** 또는 사이트 시스템 서버의 SMS/Logs 폴더|
|SMS_Cloud_<br>ProxyConnector.log|클라우드 관리 게이트웨이 서비스와 클라우드 관리 게이트웨이 연결 지점 간에 연결을 설정하는 방법에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|
|CMGContentService.log<sup>[참고 1](#bkmk_note1)</sup>|<!--SCCMDocs-pr issue #2822-->버전 1806부터 Azure 스토리지에서 콘텐츠를 제공하기 위해 CMG를 사용하도록 설정하는 경우 이 로그는 해당 서비스의 세부 정보를 기록합니다.|Azure 서버의 **%approot%\logs** 또는 사이트 시스템 서버의 SMS/Logs 폴더|

- 배포 문제 해결에는 **CloudMgr.log** 및 **CMGSetup.log**를 사용합니다.
- 서비스 상태 문제 해결에는 **CMGService.log** 및 **SMS_Cloud_ProxyConnector.log**를 사용합니다.
- 클라이언트 트래픽 문제 해결에는 **CMGHttpHandler.log**, **CMGService.log** 및 **SMS_Cloud_ProxyConnector.log**를 사용합니다.

#### <a name="bkmk_note1"></a> 참고 1: Azure에서 동기화된 로그

클라우드 서비스 관리자가 5분마다 Azure 스토리지에서 동기화하는 로컬 Configuration Manager 로그 파일입니다. 클라우드 관리 게이트웨이는 5분마다 로그를 Azure Storage에 푸시합니다. 따라서 최대 지연은 10분입니다. 자세한 정보 스위치는 로컬 및 원격 로그 둘 다에 영향을 미칩니다. 실제 파일 이름에는 서비스 이름 및 역할 인스턴스 식별자가 포함됩니다. 예: CMG-*ServiceName*-*RoleInstanceID*-CMGSetup.log

### <a name="BKMK_CompSettingsLog"></a> 준수 설정 및 회사 리소스 액세스

다음 표에는 호환성 설정 및 회사 리소스 액세스와 관련된 정보가 포함된 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CIAgent.log|호환성 설정, 소프트웨어 업데이트, 애플리케이션 관리에 대한 재구성 및 호환성 프로세스에 대한 세부 정보를 기록합니다.|클라이언트|  
|CITaskManager.log|구성 항목 작업 일정에 대한 정보를 기록합니다.|클라이언트|  
|DCMAgent.log|구성 항목과 애플리케이션의 평가, 충돌 보고 및 재구성에 대한 높은 수준의 정보를 기록합니다.|클라이언트|  
|DCMReporting.log|구성 항목에 대한 상태 메시지에 정책 플랫폼 결과를 보고하는 작업에 대한 정보를 기록합니다.|클라이언트|  
|DcmWmiProvider.log|WMI에서 구성 항목 synclet를 읽는 작업에 대한 정보를 기록합니다.|클라이언트|  

### <a name="BKMK_CA"></a> 조건부 액세스

다음 표에는 조건부 액세스와 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|ADALOperationProvider.log|AAD 토큰 취득에 대한 세부 정보를 기록합니다.|클라이언트|  
|cloudusersync.log|사용자의 라이선스 사용을 기록합니다.|서비스 연결 지점이 있는 컴퓨터|  
|ComplRelayAgent.log|DCM에서 전반적인 준수 상태를 수신하고, MP 토큰을 취득하고, AAD 토큰을 취득하며, Intune에 준수를 다시 보고(CA 릴레이 서비스)합니다.|클라이언트|  
|DcmWmiProvider.log|WMI에서 구성 항목 synclet를 읽는 작업에 대한 정보를 기록합니다.|클라이언트|  
|dmpdownloader.log|Microsoft Intune의 다운로드에 대한 세부 정보를 기록합니다.|서비스 연결 지점이 있는 컴퓨터|
|dmpuploader.log|데이터베이스 변경 내용을 Microsoft Intune에 업로드하는 작업과 관련된 세부 정보를 기록합니다.|서비스 연결 지점이 있는 컴퓨터|
|MP_Token.log|클라이언트의 토큰 요청을 기록합니다.|사이트 시스템 서버|  

### <a name="BKMK_ConsoleLog"></a> Configuration Manager 콘솔

다음 표에는 Configuration Manager 콘솔과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|ConfigMgrAdminUISetup.log|Configuration Manager 콘솔 설치를 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|SmsAdminUI.log|Configuration Manager 콘솔의 작업에 대한 정보를 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|Smsprov.log|SMS 공급자가 수행한 작업을 기록합니다. Configuration Manager 콘솔 작업은 SMS 공급자를 사용합니다.|사이트 서버 또는 사이트 시스템 서버|  

### <a name="BKMK_ContentLog"></a> 콘텐츠 관리

다음 표에는 콘텐츠 관리와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CloudDP-&lt;guid\>.log|스토리지 및 콘텐츠 액세스에 대한 정보를 포함하여 특정 클라우드 기반 배포 지점에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|CloudMgr.log|콘텐츠 프로비전, 스토리지 및 대역폭 통계 수집, 클라우드 기반 배포 지점을 실행하는 클라우드 서비스를 중지하거나 시작하기 위해 관리자가 시작한 작업에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|DataTransferService.log|정책 또는 패키지 액세스에 대한 모든 BITS 통신을 기록합니다. 이 로그는 풀(pull) 배포 지점의 콘텐츠 관리에도 사용됩니다.|풀(pull) 배포 지점으로 구성된 컴퓨터|  
|PullDP.log|풀(pull) 배포 지점이 원본 배포 지점에서 전송하는 콘텐츠에 대한 세부 정보를 기록합니다.|풀(pull) 배포 지점으로 구성된 컴퓨터|  
|PrestageContent.log|사전 준비된 원격 배포 지점에서 ExtractContent.exe 도구를 사용하는 방법에 대한 세부 정보를 기록합니다. 이 도구는 파일로 내보낸 콘텐츠를 추출합니다.|사이트 시스템 역할|  
|SMSdpmon.log|배포 지점에 구성된 배포 지점 상태 모니터링 예약 작업에 대한 세부 정보를 기록합니다.|사이트 시스템 역할|  
|smsdpprov.log|기본 사이트에서 받은 압축 파일의 압축 풀기에 대한 세부 정보를 기록합니다. 이 로그는 원격 배포 지점의 WMI 공급자가 생성합니다.|사이트 서버와 함께 있지 않은 배포 지점 컴퓨터|  
|smsdpusage.log|배포 지점 사용량 요약 보고서에 대한 데이터를 실행하고 수집하는 smsdpusage.exe에 대한 세부 정보를 기록합니다.|사이트 시스템 역할|  

### <a name="desktop-analytics"></a>Desktop Analytics

다음 로그를 사용하여 Configuration Manager와 통합된 Desktop Analytics의 문제를 해결할 수 있습니다.

서비스 연결 지점의 로그 파일은 `%ProgramFiles%\Configuration Manager\Logs\M365A` 디렉터리에 있습니다.
구성 관리자 클라이언트의 로그 파일은 `%WinDir%\CCM\logs` 디렉터리에 있습니다.

| 로그 | 설명 |로그 파일이 있는 컴퓨터|
|---------|---------|---------|
| M365ADeploymentPlanWorker.log | Desktop Analytics 클라우드 서비스와 온-프레미스 Configuration Manager 간 배포 계획 동기화에 대한 정보 |서비스 연결 지점|
| M365ADeviceHealthWorker.log | Configuration Manager에서 Microsoft 클라우드로 디바이스 상태 업로드에 대한 정보 |서비스 연결 지점|
| M365AHandler.log | Desktop Analytics 설정 정책에 대한 정보 |클라이언트|
| M365AUploadWorker.log | Configuration Manager에서 Microsoft 클라우드로 컬렉션 및 디바이스 업로드에 대한 정보 |서비스 연결 지점|
| SmsAdminUI.log | Azure 클라우드 서비스 구성과 같은 Configuration Manager 콘솔 작업에 대한 정보  |서비스 연결 지점|

### <a name="BKMK_DiscoveryLog"></a> 검색

다음 표에는 검색과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|adsgdis.log|Active Directory 보안 그룹 검색 작업을 기록합니다.|사이트 서버|  
|adsysdis.log|Active Directory 시스템 검색 작업을 기록합니다.|사이트 서버|  
|adusrdis.log|Active Directory 사용자 검색 작업을 기록합니다.|사이트 서버|  
|ADForestDisc.log|Active Directory 포리스트 검색 작업을 기록합니다.|사이트 서버|  
|ddm.log|검색 데이터 관리자의 작업을 기록합니다.|사이트 서버|  
|InventoryAgent.log|클라이언트의 하드웨어 인벤토리, 소프트웨어 인벤토리 및 하트비트 검색 작업에 대한 활동을 기록합니다.|클라이언트|  
|netdisc.log|네트워크 검색 작업을 기록합니다.|사이트 서버|  

### <a name="BKMK_EPLog"></a> Endpoint Protection

다음 표에는 Endpoint Protection과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|EndpointProtectionAgent.log|Endpoint Protection 클라이언트의 설치 및 해당 클라이언트에 대한 맬웨어 방지 정책 적용에 대한 세부 정보를 기록합니다.|클라이언트|  
|EPCtrlMgr.log|Endpoint Protection 역할 서버에서 Configuration Manager 데이터베이스로의 맬웨어 위협 정보 동기화에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|EPMgr.log|Endpoint Protection 사이트 시스템 역할의 상태를 모니터링합니다.|사이트 시스템 서버|  
|EPSetup.log|Endpoint Protection 사이트 시스템 역할의 설치에 대한 정보를 제공합니다.|사이트 시스템 서버|  

### <a name="BKMK_Extensions"></a> 확장

다음 표에는 확장과 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|AdminUI.ExtensionInstaller.log|Microsoft 확장 다운로드와 모든 확장의 설치 및 제거에 대한 정보를 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|FeatureExtensionInstaller.log|개별 확장이 Configuration Manager 콘솔에서 사용되거나 사용되지 않는 경우 해당 확장의 설치 및 제거에 대한 정보를 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|SmsAdminUI.log|Configuration Manager 콘솔 작업을 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  

### <a name="BKMK_InventoryLog"></a> 인벤토리

다음 표에는 인벤토리 데이터 처리와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|dataldr.log|Configuration Manager 데이터베이스에서 MIF 파일 및 하드웨어 인벤토리 처리 작업에 대한 정보를 기록합니다.|사이트 서버|  
|invproc.log|보조 사이트에서 해당 부모 사이트로 전달된 MIF 파일을 기록합니다.|보조 사이트 서버|  
|sinvproc.log|사이트 데이터베이스에 대한 소프트웨어 인벤토리 데이터의 처리에 대한 정보를 기록합니다.|사이트 서버|  

### <a name="BKMK_MeteringLog"></a> 계량

다음 표에는 계량과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|mtrmgr.log|모든 소프트웨어 계량 프로세스를 모니터링합니다.|클라이언트|  
|SWMTRReportGen.log|계량 에이전트에서 수집한 사용 데이터 보고서를 생성합니다. 이 데이터는 Mtrmgr.log에 기록됩니다.|클라이언트|
|swmproc.log|계량 파일 및 설정의 처리 정보를 기록합니다.|사이트 서버|

### <a name="BKMK_MigrationLog"></a> 마이그레이션

다음 표에는 마이그레이션과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|migmctrl.log|마이그레이션 작업, 공유 배포 지점 및 배포 지점 업그레이드와 관련된 마이그레이션 작업에 대한 정보를 기록합니다.|Configuration Manager 계층 구조의 최상위 사이트 및 각 하위 기본 사이트.<br /><br /> 기본 사이트가 여러 개인 계층인 경우 중앙 관리 사이트에 만들어진 로그 파일을 사용하세요.|  

### <a name="BKMK_MDMLog"></a> 모바일 디바이스

다음 섹션에는 모바일 디바이스 관리와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

#### <a name="BKMK_EnrollmentLog"></a> 등록

다음 표에는 모바일 디바이스 등록과 관련된 정보가 포함된 로그가 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|DMPRP.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점과 관리 지점 엔드포인트 간의 통신을 기록합니다.|사이트 시스템 서버|  
|dmpmsi.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점의 구성에 대한 Windows Installer 데이터를 기록합니다.|사이트 시스템 서버|  
|DMPSetup.log|모바일 디바이스에 대해 관리 지점이 사용되는 경우 해당 관리 지점의 구성을 기록합니다.|사이트 시스템 서버|  
|enrollsrvMSI.log|등록 지점의 구성에 대한 Windows Installer 데이터를 기록합니다.|사이트 시스템 서버|  
|enrollmentweb.log|모바일 디바이스와 등록 프록시 지점 간의 통신을 기록합니다.|사이트 시스템 서버|  
|enrollwebMSI.log|등록 프록시 지점의 구성에 대한 Windows Installer 데이터를 기록합니다.|사이트 시스템 서버|  
|enrollmentservice.log|등록 프록시 지점과 등록 지점 간의 통신을 기록합니다.|사이트 시스템 서버|  
|SMS_DM.log|모바일 디바이스, Mac 컴퓨터, 그리고 모바일 디바이스와 Mac 컴퓨터에 대해 사용하도록 설정된 관리 지점 간의 통신을 기록합니다.|사이트 시스템 서버|  

#### <a name="BKMK_ExchSrvLog"></a> Exchange Server 커넥터

다음 로그에는 Exchange Server 커넥터와 관련된 정보가 포함되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|easdisc.log|Exchange Server 커넥터의 활동과 상태를 기록합니다.|사이트 서버|  

#### <a name="BKMK_MDLegLog"></a> 모바일 디바이스 기존

다음 표에는 모바일 디바이스 기존 클라이언트와 관련된 정보가 포함된 로그가 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|DmCertEnroll.log|모바일 디바이스 기존 클라이언트의 인증서 등록 데이터에 대한 세부 정보를 기록합니다.|클라이언트|  
|DMCertResp.htm|모바일 디바이스 기존 클라이언트 등록자 프로그램에서 PKI 인증서를 요청할 경우 인증서 서버의 HTML 응답을 기록합니다.|클라이언트|  
|DmClientHealth.log|모바일 디바이스에 사용되는 관리 지점과 통신하는 모든 모바일 디바이스 기존 클라이언트의 GUID를 기록합니다.|사이트 시스템 서버|  
|DmClientRegistration.log|모바일 디바이스 기존 클라이언트와 주고 받는 등록 요청 및 응답을 기록합니다.|사이트 시스템 서버|  
|DmClientSetup.log|모바일 디바이스 기존 클라이언트에 대한 클라이언트 설치 데이터를 기록합니다.|클라이언트|  
|DmClientXfer.log|모바일 디바이스 기존 클라이언트 및 ActiveSync 배포에 대한 클라이언트 설치 데이터를 기록합니다.|클라이언트|  
|DmCommonInstaller.log|모바일 디바이스 기존 클라이언트 전송 파일 구성을 위한 클라이언트 전송 파일 설치를 기록합니다.|클라이언트|  
|DmInstaller.log|DMInstaller가 DmClientSetup을 제대로 호출하는지 여부 및 DmClientSetup이 모바일 디바이스 기존 클라이언트 종료 시 성공 또는 실패 여부를 기록합니다.|클라이언트|  
|DmpDatastore.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점에서 만든 모든 사이트 데이터베이스 연결과 쿼리를 기록합니다.|사이트 시스템 서버|  
|DmpDiscovery.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점에 있는 모바일 디바이스 기존 클라이언트의 모든 검색 데이터를 기록합니다.|사이트 시스템 서버|  
|DmpHardware.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점에 있는 모바일 디바이스 기존 클라이언트의 하드웨어 인벤토리 데이터를 기록합니다.|사이트 시스템 서버|  
|DmpIsapi.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점과 모바일 디바이스 기존 클라이언트의 통신을 기록합니다.|사이트 시스템 서버|  
|dmpmsi.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점의 구성에 대한 Windows Installer 데이터를 기록합니다.|사이트 시스템 서버|  
|DMPSetup.log|모바일 디바이스에 대해 관리 지점이 사용되는 경우 해당 관리 지점의 구성을 기록합니다.|사이트 시스템 서버|  
|DmpSoftware.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점에 있는 모바일 디바이스 기존 클라이언트의 소프트웨어 배포 데이터를 기록합니다.|사이트 시스템 서버|  
|DmpStatus.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점에 있는 모바일 디바이스 클라이언트의 상태 메시지 데이터를 기록합니다.|사이트 시스템 서버|  
|DmSvc.log|모바일 디바이스에 대해 사용하도록 설정된 관리 지점을 대상으로 하는 모바일 디바이스 기존 클라이언트로부터의 클라이언트 통신을 기록합니다.|클라이언트|  
|FspIsapi.log|대체 상태 지점과 모바일 디바이스 기존 클라이언트 및 클라이언트 컴퓨터 간에 수행되는 통신 관련 세부 정보를 기록합니다.|사이트 시스템 서버|  

### <a name="BKMK_OSDLog"></a> OS 배포

다음 표에는 OS 배포와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CAS.log|참조된 콘텐츠의 배포 지점이 발견된 경우 세부 정보를 기록합니다.|클라이언트|  
|ccmsetup.log|클라이언트 설정, 클라이언트 업그레이드 및 클라이언트 제거에 대한 ccmsetup 작업을 기록합니다. 클라이언트 설치 문제를 해결하는 데 사용할 수 있습니다.|클라이언트|  
|CreateTSMedia.log|작업 순서 미디어 작성에 대한 세부 정보를 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|DeployToVhd.log|VHD(가상 하드 디스크) 만들기 및 수정 프로세스에 대한 세부 정보를 기록합니다.|Configuration Manager 콘솔을 실행하는 컴퓨터|  
|Dism.log|오프라인 서비스를 위한 드라이버 설치 작업 또는 애플리케이션 업데이트 작업을 기록합니다.|사이트 시스템 서버|  
|distmgr.log|PXE(Preboot Execution Environment)에 대해 배포 지점을 사용하도록 설정하는 구성에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|DriverCatalog.log|드라이버 카탈로그로 가져온 디바이스 드라이버에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|mcsisapi.log|멀티캐스트 패키지 전송 및 클라이언트 요청 응답에 대한 정보를 기록합니다.|사이트 시스템 서버|  
|mcsexec.log|상태 검사, 네임스페이스, 세션 작성 및 인증서 확인 작업을 기록합니다.|사이트 시스템 서버|  
|mcsmgr.log|구성, 보안 모드 및 가용성의 변경 내용을 기록합니다.|사이트 시스템 서버|  
|mcsprv.log|WDS(Windows 배포 서비스)와의 멀티캐스트 공급자 상호 작용을 기록합니다.|사이트 시스템 서버|  
|MCSSetup.log|멀티캐스트 서버 역할 설치에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|MCSMSI.log|멀티캐스트 서버 역할 설치에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|Mcsperf.log|멀티캐스트 성능 카운터 업데이트에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|MP_ClientIDManager.log|작업 순서가 PXE 또는 부팅 미디어에서 시작하는 클라이언트 ID 요청에 대한 관리 지점 응답을 기록합니다.|사이트 시스템 서버|  
|MP_DriverManager.log|드라이버 자동 적용 작업 순서 작업 요청에 대한 관리 지점 응답을 기록합니다.|사이트 시스템 서버|  
|OfflineServicingMgr.log|운영 체제 WIM(Windows Imaging Format) 파일에 대한 오프라인 지원 예약 및 업데이트 적용 작업의 세부 정보를 기록합니다.|사이트 시스템 서버|  
|Setupact.log|Windows Sysprep 및 설치 로그에 대한 세부 정보를 기록합니다. 자세한 내용은 [로그 파일](https://docs.microsoft.com/windows/deployment/upgrade/log-files)을 참조하세요.|클라이언트|  
|Setupapi.log|Windows Sysprep 및 설치 로그에 대한 세부 정보를 기록합니다.|클라이언트|  
|Setuperr.log|Windows Sysprep 및 설치 로그에 대한 세부 정보를 기록합니다.|클라이언트|  
|smpisapi.log|클라이언트 상태 캡처 및 복원 작업, 그리고 임계값 정보에 대한 세부 정보를 기록합니다.|클라이언트|  
|Smpmgr.log|상태 마이그레이션 지점 상태 검사 및 구성 변경 사항에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|smpmsi.log|상태 마이그레이션 지점에 대한 설치 및 구성 세부 정보를 기록합니다.|사이트 시스템 서버|  
|smpperf.log|상태 마이그레이션 지점 성능 카운터 업데이트를 기록합니다.|사이트 시스템 서버|  
|smspxe.log|PXE 부팅을 사용하는 클라이언트에 보낸 응답에 대한 세부 정보 및 부팅 이미지 및 부팅 파일의 확장에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|smssmpsetup.log|상태 마이그레이션 지점에 대한 설치 및 구성 세부 정보를 기록합니다.|사이트 시스템 서버|
| SMS_PhasedDeployment.log| 단계적 배포에 대한 로그 파일|Configuration Manager 계층 구조의 최상위 사이트| 
|Smsts.log|작업 순서 활동을 기록합니다.|클라이언트|  
|TSAgent.log|작업 순서를 시작하기 전에 작업 순서 종속성의 결과를 기록합니다.|클라이언트|  
|TaskSequenceProvider.log|작업 순서를 가져오거나 내보내거나 편집할 때 작업 순서에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|loadstate.log|USMT(사용자 환경 마이그레이션 도구) 및 사용자 상태 데이터 복원에 대한 세부 정보를 기록합니다.|클라이언트|  
|scanstate.log|USMT(사용자 환경 마이그레이션 도구) 및 사용자 상태 데이터 캡처에 대한 세부 정보를 기록합니다.|클라이언트|  

### <a name="BKMK_PowerMgmtLog"></a> 전원 관리

다음 표에는 전원 관리와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|Pwrmgmt.log|전원 관리 클라이언트 에이전트에 의한 모니터링 및 설정 적용을 포함한 클라이언트 컴퓨터의 전원 관리 활동에 대한 세부 정보를 기록합니다.|클라이언트|  

### <a name="BKMK_RCLog"></a> 원격 제어

다음 표에는 원격 제어와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CMRcViewer.log|원격 제어 뷰어의 활동에 대한 세부 정보를 기록합니다.|원격 제어 뷰어를 실행하는 컴퓨터의 %temp% 폴더에 있습니다.|  

### <a name="BKMK_ReportLog"></a> 보고

다음 표에는 보고와 관련된 정보가 포함된 Configuration Manager 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|srsrp.log|보고 서비스 지점의 활동 및 상태에 대한 정보를 기록합니다.|사이트 시스템 서버|  
|srsrpMSI.log|MSI 출력에서 제공하는 보고 서비스 지점 설치 프로세스의 자세한 결과를 기록합니다.|사이트 시스템 서버|  
|srsrpsetup.log|보고 서비스 지점 설치 프로세스의 결과를 기록합니다.|사이트 시스템 서버|  

### <a name="BKMK_RBALog"></a> 역할 기반 관리

다음 표에는 관리 역할 기반 관리와 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|hman.log|사이트 구성 변경 내용 및 Active Directory Domain Services에 사이트 정보를 게시하는 작업에 대한 정보를 기록합니다.|사이트 서버|  
|SMSProv.log|사이트 데이터베이스에 대한 WMI 공급자 액세스를 기록합니다.|SMS 공급자가 설치된 컴퓨터|  

### <a name="BKMK_MeteringLog"></a> 소프트웨어 계량

다음 표에는 소프트웨어 계량과 관련된 정보가 포함된 로그 파일이 나열되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|mtrmgr.log|모든 소프트웨어 계량 프로세스를 모니터링합니다.|사이트 서버|  

### <a name="BKMK_SU_NAPLog"></a> 소프트웨어 업데이트

다음 표에는 소프트웨어 업데이트와 관련된 정보가 포함된 로그 파일이 나와 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|AlternateHandler.log|클라이언트가 언제 Office 간편 실행 COM 인터페이스를 호출하여 Office 365 클라이언트 업데이트를 다운로드 및 설치하는지에 대한 세부 정보를 기록합니다. Windows 업데이트 에이전트 API를 호출하여 Windows 업데이트를 다운로드 및 설치할 때는 사용 방법이 WuaHandler와 유사합니다.<!-- SCCMDocs#888 -->|클라이언트|
|ccmperf.log|클라이언트 성능 카운터와 관련된 데이터의 유지 관리 및 캡처와 관련된 활동을 기록합니다.|클라이언트|  
|PatchDownloader.log|소프트웨어 업데이트를 업데이트 원본에서 사이트 서버의 다운로드 대상으로 다운로드하는 프로세스에 대한 세부 정보를 기록합니다.|업데이트를 수동으로 다운로드할 때는 이 로그 파일이 콘솔을 실행하는 머신에서 콘솔을 실행하는 사용자의 %temp% 디렉터리에 있습니다. 자동 배포 규칙의 경우 이 로그 파일은 사이트 서버에 ConfigMgr 클라이언트가 설치되었다면 %windir%\CCM\Logs의 사이트 서버에 있습니다.|  
|PolicyEvaluator.log|소프트웨어 업데이트의 정책을 포함한 클라이언트 컴퓨터의 정책에 대한 평가와 관련된 세부 정보를 기록합니다.|클라이언트|  
|RebootCoordinator.log|소프트웨어 업데이트 설치 후 클라이언트 컴퓨터의 시스템 다시 시작 조정에 대한 세부 정보를 기록합니다.|클라이언트|  
|ScanAgent.log|소프트웨어 업데이트, WSUS 위치 및 관련 작업에 대한 검사 요청과 관련된 세부 정보를 기록합니다.|클라이언트|  
|SdmAgent.log|재구성 및 준수 추적에 대한 세부 정보를 기록합니다. 그러나 소프트웨어 업데이트 로그 파일인 Updateshandler.log는 준수에 필요한 소프트웨어 업데이트를 설치하는 작업에 대한 자세한 세부 정보를 제공합니다.<br /><br /> 이 로그 파일은 호환성 설정과 공유됩니다.|클라이언트|  
|ServiceWindowManager.log|유지 관리 기간의 평가에 대한 세부 정보를 기록합니다.|클라이언트|
|SMS_ISVUPDATES_SYNCAGENT.log| Configuration Manager 버전 1806부터 시작되는 타사 소프트웨어 동기화에 대한 로그 파일입니다.| Configuration Manager 계층 구조의 최상위 수준 소프트웨어 업데이트 지점입니다.|  
|SmsWusHandler.log|Microsoft 업데이트용 인벤토리 도구의 검사 프로세스에 대한 세부 정보를 기록합니다.|클라이언트|  
|StateMessage.log|생성된 후 관리 지점으로 전송되는 소프트웨어 업데이트 상태 메시지에 대한 세부 정보를 기록합니다.|클라이언트|  
|SUPSetup.log|소프트웨어 업데이트 지점 설치에 대한 세부 정보를 기록합니다. 소프트웨어 업데이트 지점 설치가 완료되면 이 로그 파일에 **Installation was successful** 이 기록됩니다.|사이트 시스템 서버|  
|UpdatesDeployment.log|소프트웨어 업데이트 활성화, 평가, 적용을 포함하여 클라이언트에 배포하는 작업에 대한 세부 정보를 기록합니다. 자세한 정보 로깅에는 클라이언트 사용자 인터페이스와의 상호 작용에 대한 추가 정보가 표시됩니다.|클라이언트|  
|UpdatesHandler.log|소프트웨어 업데이트 호환성 검사에 대한 세부 정보 및 클라이언트에 소프트웨어 업데이트를 다운로드하고 설치하는 작업에 대한 세부 정보를 기록합니다.|클라이언트|  
|UpdatesStore.log|호환성 검사 주기 동안 평가된 소프트웨어 업데이트의 호환성 상태에 대한 세부 정보를 기록합니다.|클라이언트|  
|WCM.log|소프트웨어 업데이트 지점 구성과 구독된 업데이트 범주, 분류 및 언어를 위한 WSUS 서버 연결에 대한 세부 정보를 기록합니다.|사이트 서버|  
|WSUSCtrl.log|사이트에 대한 WSUS 서버의 구성, 데이터베이스 연결 및 상태에 대한 세부 정보를 기록합니다.|사이트 시스템 서버|  
|wsyncmgr.log|소프트웨어 업데이트 동기화 프로세스에 대한 세부 정보를 기록합니다.|사이트 서버|  
|WUAHandler.log|소프트웨어 업데이트가 검색되는 경우 클라이언트의 Windows Update 에이전트 관련 세부 정보를 기록합니다.|클라이언트|  

### <a name="BKMK_WOLLog"></a> Wake On LAN

다음 표에는 Wake On LAN 사용과 관련된 정보가 있는 로그 파일이 나와 있습니다.  

> [!NOTE]  
> 절전 모드 해제 프록시를 사용하여 Wake On LAN을 보완하는 경우 이 작업의 로그는 클라이언트에 기록됩니다. 예를 들어 이 문서의 [클라이언트 작업](#BKMK_ClientOpLogs) 섹션에서 CcmExec.log 및 SleepAgent_<*도메인*\>@SYSTEM_0.log를 참조하세요.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|wolcmgr.log|절전 모드 해제 패킷을 보내야 하는 클라이언트, 전송한 절전 모드 해제 패킷 수, 사용이 중단된 절전 모드 해제 패킷의 수 등에 대한 세부 정보를 기록합니다.|사이트 서버|  
|wolmgr.log|Wake On LAN에 구성된 배포의 절전 모드를 해제하는 경우와 같이 절전 모드 해제 절차에 대한 세부 정보를 기록합니다.|사이트 서버|  

### <a name="BKMK_WindowsServicingLog"></a> Windows 10 서비스

다음 표에는 Windows 10 서비스와 관련된 정보가 포함된 로그 파일이 나와 있습니다.  
서비스는 소프트웨어 업데이트와 동일한 인프라 및 프로세스를 사용합니다. 서비스 시나리오에 적용되는 다른 로그는 [소프트웨어 업데이트](#BKMK_SU_NAPLog)를 참조하세요.

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|CBS.log|Windows 업데이트 또는 역할 및 기능 변경과 관련된 서비스 오류를 기록합니다.|클라이언트|
|DISM.log|DISM을 사용하는 모든 작업을 기록합니다. 더 자세한 내용이 필요한 경우, DISM.log가 CBS.log를 가리킵니다.|클라이언트|
|setupact.log|Windows 설치 과정에서 발생하는 대부분의 오류에 대한 기본 로그 파일입니다. 로그 파일은 %windir%\$Windows.~BT\sources\panther 폴더에 있습니다.|클라이언트|

자세한 내용은 [온라인 서비스 관련 로그 파일](https://docs.microsoft.com/windows-hardware/manufacture/desktop/deployment-troubleshooting-and-log-files#online-servicing-related-log-files)을 참조하세요.

### <a name="BKMK_WULog"></a> Windows 업데이트 에이전트

다음 표에는 Windows Update 에이전트와 관련된 정보가 있는 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|WindowsUpdate.log|Windows 업데이트 에이전트가 WSUS 서버에 연결하여 준수 평가를 위해 소프트웨어 업데이트를 검색하는 경우에 대한 세부 정보와 에이전트 구성 요소에 대한 업데이트가 있는지 여부에 대한 세부 정보를 기록합니다.|클라이언트|  

자세한 내용은 [Windows 업데이트 로그 파일](https://docs.microsoft.com/windows/deployment/update/windows-update-logs)을 참조하세요.

### <a name="BKMK_WSUSLog"></a> WSUS 서버

다음 표에는 WSUS 서버와 관련된 정보가 있는 로그 파일이 정리되어 있습니다.  

|로그 이름|설명|로그 파일이 있는 컴퓨터|  
|--------------|-----------------|----------------------------|  
|Change.log|변경된 WSUS 서버 데이터베이스 정보에 대한 세부 정보를 기록합니다.|WSUS 서버|  
|SoftwareDistribution.log|구성된 업데이트 원본에서 WSUS 서버 데이터베이스로 동기화된 소프트웨어 업데이트에 대한 세부 정보를 기록합니다.|WSUS 서버|  

이러한 로그 파일은 `%ProgramFiles%\Update Services\LogFiles` 폴더에 있습니다.


## <a name="see-also"></a>참고 항목

- [로그 파일 정보](/sccm/core/plan-design/hierarchy/about-log-files)

- [지원 센터 OneTrace](/sccm/core/support/support-center-onetrace)

- [지원 센터 로그 파일 뷰어](/sccm/core/support/support-center#support-center-log-file-viewer)

- [CMTrace](/sccm/core/support/cmtrace)
