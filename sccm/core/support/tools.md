---
title: Configuration Manager 도구
titleSuffix: Configuration Manager
description: Configuration Manager 인프라 문제를 해결하고 관리하는 도구에 대해 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 395403dc-6997-4415-93fd-6b1eeb6ba31a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fd23bd523eb64f7d00f71c38c79a180c4e2e569a
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39386544"
---
# <a name="configuration-manager-tools"></a>Configuration Manager 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 도구에는 [클라이언트 기반](#client-tools) 및 [서버 기반 도구](#server-tools)가 포함됩니다. 이러한 도구를 사용하여 Configuration Manager 인프라 문제를 해결하고 지원합니다. 

Configuration Manager 버전 1806부터 이러한 도구가 사이트 서버의 `CD.Latest\SMSSETUP\Tools` 폴더에 포함됩니다. 추가로 설치할 필요가 없습니다.<!--1357145--> Configuration Manager 버전 1806 이상에서 이러한 버전의 도구를 사용합니다.

[클라이언트 및 장치에 대해 지원되는 운영 체제](https://docs.microsoft.com/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)에 지원되는 클라이언트로 나열된 모든 Windows 운영 체제는 이러한 도구에서 사용을 지원합니다.

> [!Note]  
> [System Center 2012 R2 Configuration Manager Toolkit](https://www.microsoft.com/en-us/download/details.aspx?id=50012)은 Microsoft 다운로드 센터에서 계속 사용할 수 있습니다. Configuration Manager 버전 1806 이상의 경우 사이트 서버의 CD.Latest 폴더에서 이러한 버전의 도구를 사용합니다. 일부 도구는 이전에 도구 키트에 있었지만 1806 버전에는 포함되지 않았습니다. 이러한 레거시 도구는 더 이상 지원되지 않습니다.


## <a name="client-tools"></a>클라이언트 도구

- [CMTrace](/sccm/core/support/cmtrace): Configuration Manager 로그 파일을 보기, 모니터링 및 분석합니다.  

- [클라이언트 감시](/sccm/core/support/clispy): 소프트웨어 배포, 인벤토리 및 계량 관련 문제를 해결합니다.

- [배포 모니터링 도구](/sccm/core/support/deployment-monitoring-tool): 응용 프로그램, 업데이트 및 기준 배포의 문제를 해결합니다.  

- [정책 감시](/sccm/core/support/policy-spy): 정책 할당을 표시합니다.  

- [전원 뷰어 도구](/sccm/core/support/power-viewer-tool): 전원 관리 기능의 상태를 표시합니다.  

- [일정 보내기 도구](/sccm/core/support/send-schedule-tool): 구성 기준의 일정과 평가를 트리거합니다.  

> [!Note]  
> ClientTools 폴더에는 Microsoft.Diagnostics.Tracing.EventSource.dll 파일도 포함됩니다. 여러 클라이언트 도구에 이 라이브러리가 필요합니다. 이 라이브러리를 직접 사용할 수 없습니다.  


## <a name="server-tools"></a>서버 도구

- [DP 작업 큐 관리자](/sccm/core/support/dp-job-manager): 배포 지점에 콘텐츠를 배포하는 작업의 문제를 해결합니다.  

- [컬렉션 평가 뷰어](/sccm/core/support/ceviewer): 컬렉션 평가 세부 정보를 표시합니다.  

- [콘텐츠 라이브러리 탐색기](/sccm/core/support/content-library-explorer): 콘텐츠 라이브러리 단일 인스턴스 저장소의 콘텐츠를 표시합니다.  

- [콘텐츠 라이브러리 전송](/sccm/core/support/content-library-transfer): 드라이브 간에 콘텐츠 라이브러리를 전송합니다.  

- [콘텐츠 소유권 도구](/sccm/core/support/content-ownership-tool): 분리된 패키지의 소유권을 변경합니다. 이러한 패키지는 소유하는 사이트 서버가 없는 사이트에 존재합니다.  

- [역할 기반 관리 및 감사 도구](/sccm/core/support/rbaviewer): 관리자가 역할 구성을 감사하는 데 도움이 됩니다.  

- [측정기 요약 도구 실행](/sccm/core/support/run-meter-summ): 계량 요약 작업을 실행하고 계량 데이터를 분석합니다.

> [!Note]  
> ServerTools 폴더에는 다음 파일도 포함됩니다. 
> - AdminUI.WqlQueryEngine.dll
> - Microsoft.ConfigurationManagement.ManagementProvider.dll
> - Microsoft.Diagnostics.Tracing.EventSource.dll. 
>
> 여러 서버 도구에 이러한 라이브러리가 필요합니다. 이러한 라이브러리를 직접 사용할 수 없습니다.  



## <a name="other-tools"></a>다른 도구

- [콘텐츠 라이브러리 정리 도구](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool): `CD.Latest\SMSSETUP\TOOLS\ContentLibraryCleanup`에서 **ContentLibraryCleanup.exe**를 사용하여 배포 지점에서 분리된 콘텐츠를 제거합니다.  

- [계층 구조 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe): 사이트 서버의 `\<SiteServerName>\SMS_<SiteCode>\bin\X64\00000409` 공유 폴더에서 **Preinst.exe**를 사용하여 계층 구조 관리자 구성 요소에 명령을 전달합니다.  

- [업데이트 다시 설정 도구](/sccm/core/servers/manage/update-reset-tool): 콘솔 내 업데이트의 다운로드 및 복제에 문제가 있는 경우 `CD.Latest\SMSSETUP\TOOLS\CMUpdateReset`에서 **CMUpdateReset.exe**를 사용하여 문제를 수정합니다.  

- [서비스 연결 도구](/sccm/core/servers/manage/use-the-service-connection-tool): 서비스 연결 지점이 오프라인 상태일 때 `CD.Latest\SMSSETUP\TOOLS\ServiceConnectionTool`에서 **ServiceConnectionTool.exe**를 사용하여 사이트를 최신 상태로 유지합니다.  
