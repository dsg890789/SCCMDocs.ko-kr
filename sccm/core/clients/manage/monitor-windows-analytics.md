---
title: Windows Analytics로 클라이언트 모니터링
titleSuffix: Configuration Manager
description: Windows Analytics는 사용자 환경의 현재 상태에 대한 소중한 인사이트를 얻을 수 있는 솔루션 집합입니다.
ms.date: 09/04/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: CF35CE87-3BA8-4A84-9BC8-ABCEA4666212
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 8405a212f9e4cd845ac7591767eb27e5425f404e
ms.sourcegitcommit: 0d7efd9e064f9d6a9efcfa6a36fd55d4bee20059
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43893654"
---
# <a name="use-windows-analytics-with-configuration-manager"></a>Configuration Manager에서 Windows Analytics 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

[Windows Analytics](https://docs.microsoft.com/windows/deployment/update/windows-analytics-overview)는 사용자 환경의 현재 상태에 대한 인사이트를 얻을 수 있는 솔루션 집합입니다. 사용자 환경의 Windows 디바이스가 데이터를 Microsoft에 보고하며, 이때 이러한 솔루션에 액세스하여 분석할 수 있습니다. 예를 들어, [업그레이드 준비](/sccm/core/clients/manage/upgrade-readiness)를 Configuration Manager에 연결하여 Configuration Manager 콘솔의 **모니터링** 작업 영역에서 직접 데이터에 액세스할 수 있습니다.

Windows Analytics에서 사용되는 데이터는 Configuration Manager 사이트 서버로 직접 전송되지 않습니다. 클라이언트 컴퓨터에서 Windows 클라우드 서비스로 데이터를 보냅니다. 그러면 이 서비스는 관련 데이터를 조직의 작업 영역 중 하나에 호스트되는 Windows Analytics 솔루션으로 전송합니다. 이제 Configuration Manager는 컨텍스트 내 링크를 통해 웹 포털의 관련 데이터로 안내합니다. Configuration Manager에 연결하는 솔루션의 일부인 데이터를 직접 표시할 수도 있습니다.

> [!Important]  
> Configuration Manager가 진단 및 사용량 데이터를 Microsoft에 보고합니다. 이 데이터는 Windows Analytics 데이터와 구분됩니다. 자세한 내용은 [진단 및 사용 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.  



## <a name="configure-clients-to-report-data-to-windows-analytics"></a>Windows Analytics로 데이터를 보고하도록 클라이언트 구성

Windows Analytics에 데이터를 보고하는 클라이언트 디바이스의 경우 *상업용 ID 키*로 구성합니다. 이 키는 Windows Analytics 데이터를 호스팅하는 Azure Log Analytics 작업 영역입니다. 또한 사용하려는 특정 솔루션에 적합한 수준에서 데이터를 보고하도록 디바이스를 구성해야 합니다. 

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics 클라이언트 설정 구성
Windows Analytics을 구성하려면 다음을 수행하세요. 
1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **클라이언트 설정** 노드를 선택합니다.  
2. 리본에서 **사용자 지정 디바이스 클라이언트 설정 만들기**를 선택합니다.  
3. **Windows Analytics** 그룹을 이 사용자 지정 장치 클라이언트 설정 정책에 추가합니다.  

사용자 지정 디바이스 클라이언트 설정을 만드는 방법에 대한 자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.

**Windows Analytics** 설정 탭을 선택한 후 다음 설정을 구성합니다.  

#### <a name="manage-windows-telemetry-settings-with-configuration-manager"></a>Configuration Manager로 Windows 원격 분석 설정 관리
이 설정을 **예**로 구성하면 Windows 클라이언트에서 Windows 진단 데이터 설정을 구성할 수 있습니다.   

#### <a name="commercial-id-key"></a>상업용 ID 키
상업용 ID 키는 관리하는 디바이스의 정보를 조직의 Windows Analytics 데이터를 호스트하는 Log Analytics 작업 영역으로 매핑합니다. 업그레이드 준비에 사용하기 위한 상업용 ID 키를 이미 구성한 경우 해당 ID를 사용합니다. 상업용 ID 키가 아직 없는 경우 [상업용 ID 키 복사](https://docs.microsoft.com/windows/deployment/update/windows-analytics-get-started#copy-your-commercial-id-key)를 참조하세요.

#### <a name="windows-10-telemetry"></a>Windows 10 원격 분석
자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization##diagnostic-data-level)을 참조하세요.

> [!Note]  
> 이제 Windows 10 데이터 수집 수준을 **고급(제한적)** 으로 설정할 수 있습니다. 이 설정을 사용하면 Windows 10 버전 1709 이상을 사용하여 **고급** 수준의 모든 데이터를 보고하는 디바이스가 없는 환경에서 디바이스에 대해 조치 가능한 인사이트를 얻을 수 있습니다. 고급(제한적) 수준에는 Windows Analytics와 관련된 고급 수준에서 수집된 데이터 하위 집합뿐 아니라 기본 레벨의 메트릭도 포함됩니다.

#### <a name="windows-81-and-earlier-telemetry"></a>Windows 8.1 및 이전 원격 분석   
자세한 내용은 [Windows 7, Windows 8 및 Windows 8.1 평가자 원격 분석 이벤트 및 필드](https://go.microsoft.com/fwlink/?LinkID=822965)를 참조하세요.

#### <a name="enable-windows-81-and-earlier-internet-explorer-data-collection"></a>Windows 8.1 및 이전 Internet Explorer 데이터 수집 사용
Windows 8.1 또는 이전 버전을 실행하는 디바이스에서 Internet Explorer 데이터를 수집할 수 있습니다. 업그레이드 준비 기능을 통해 Windows 10으로의 원활한 업그레이드에 방해가 될 수 있는 웹 응용 프로그램 비호환성 문제를 감지할 수 있습니다. 인터넷 영역을 기반으로 Internet Explorer 데이터 수집을 활성화합니다. 인터넷 영역에 대한 자세한 내용은 [URL 보안 영역 정보](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537183\(v=vs.85\))를 참조하세요.



## <a name="use-upgrade-readiness-to-identify-windows-10-compatibility-issues"></a>업그레이드 준비를 사용하여 Windows 10 호환성 문제 식별

업그레이드 준비를 사용하면 Windows 10과의 호환성 및 디바이스 준비 상태를 분석할 수 있습니다. 이 평가를 통해 업그레이드를 좀 더 원활하게 진행할 수 있습니다. Configuration Manager를 업그레이드 준비에 연결한 후에는 Configuration Manager 관리 콘솔에서 직접 이 클라이언트 업그레이드 호환성 데이터에 액세스합니다. 그런 다음 디바이스 목록에서 업그레이드 또는 수정할 디바이스를 대상으로 지정합니다.

자세한 내용과 업그레이드 준비 구성 및 연결 방법에 대한 세부 정보를 보려면 [업그레이드 준비](/sccm/core/clients/manage/upgrade-readiness)를 참조하세요.



## <a name="use-windows-analytics-to-identify-gaps-in-windows-information-protection-policies"></a>Windows Analytics를 사용하여 Windows Information Protection 정책의 차이 식별

[Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip)(WIP) 정책으로 Windows 10 버전 1703 이후 장치를 구성할 수 있습니다. 이러한 환경에서 기업 데이터에 액세스하는 응용 프로그램에 대한 진단 데이터를 보고하지만, 정책 응용 프로그램 규칙에는 포함되지 않습니다. 사용자가 이러한 응용 프로그램의 생산성을 유지해야 할 수 있지만 WIP는 사용자의 액세스를 차단합니다. 이 정보는 Configuration Manager에서 Windows Information Protection 정책을 유지 관리하는 데 유용합니다. 

