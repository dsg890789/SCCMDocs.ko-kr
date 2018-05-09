---
title: Windows Analytics로 클라이언트 모니터링
titleSuffix: Configuration Manager
description: Windows Analytics는 Operations Management Suite에서 실행되는 솔루션 모음으로, 사용자 환경의 장치에서 보고되는 Windows 원격 분석 데이터를 활용하여 사용자 환경의 현재 상태에 대한 귀중한 정보를 얻을 수 있도록 합니다.
ms.date: 01/02/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: CF35CE87-3BA8-4A84-9BC8-ABCEA4666212
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e792f421520798a0e000384aafcb99f31dc8eb14
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="use-windows-analytics-with-configuration-manager"></a>Configuration Manager에서 Windows Analytics 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

[Windows Analytics](https://www.microsoft.com/WindowsForBusiness/windows-analytics)은 OMS([Operations Management Suite](/azure/operations-management-suite/operations-management-suite-overview))에서 실행되는 솔루션 모음입니다. 이 솔루션을 사용하여 사용자 환경의 현재 상태에 대한 정보를 얻을 수 있습니다. 사용자 환경의 장치는 Windows 원격 분석 데이터를 보고하며, 이 데이터는 [Operations Management Suite 웹 포털](https://mms.microsoft.com)의 솔루션을 통해 액세스 및 분석될 수 있습니다. [업그레이드 준비](/sccm/core/clients/manage/upgrade/upgrade-analytics)를 Configuration Manager에 연결하여 Configuration Manager 콘솔의 **모니터링** 노드에서 직접 데이터에 액세스할 수 있습니다.

Windows Analytics에서 사용되는 Windows 원격 분석 데이터는 Configuration Manager 사이트 서버로 직접 전송되지 않습니다. 클라이언트 컴퓨터는 Windows 원격 분석 서비스에 Windows 원격 분석 데이터를 보냅니다. 그러면 이 서비스는 관련 데이터를 조직의 OMS 작업 영역 중 하나에 호스트되는 Windows Analytics 솔루션으로 전송합니다. Configuration Manager에서는 상황별 링크로 웹 포털의 관련 데이터로 사용자를 연결하거나 Configuration Manager에 연결한 솔루션에 속하는 데이터를 직접 표시할 수 있습니다. 또한 Operation Management Suite 웹 포털에서 직접 데이터를 쿼리할 수도 있습니다.

>[!Important]
>Configuration Manager 사이트 서버에서 Microsoft로 보고된 [Configuration Manager 진단 및 사용 현황 데이터](../../plan-design/diagnostics/diagnostics-and-usage-data.md)는 Windows Analytics 및 Windows 원격 분석과 분리됩니다.

## <a name="configure-clients-to-report-data-to-windows-analytics"></a>Windows Analytics로 데이터를 보고하도록 클라이언트 구성

클라이언트 장치가 Windows Analytics에 데이터를 보고하려면 Windows Analytics 데이터를 호스트하는 OMS 작업 영역과 연결된 상용 ID 키로 장치를 구성해야 합니다. 또한 사용하려는 특정 솔루션에 적합한 원격 분석 수준에서 원격 분석을 보고하도록 장치를 구성해야 합니다. 

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics 클라이언트 설정 구성
Windows Analytics를 구성하려면 Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**을 선택하고 **사용자 지정 장치 클라이언트 설정 만들기**를 두 번 클릭한 다음 **Windows Analytics**를 클릭합니다.  

**Windows Analytics** 설정 탭으로 이동한 후 다음 설정을 구성합니다.
  -  **상용 ID 키**  
상업용 ID 키는 관리하는 장치의 정보를 조직의 Windows Analytics 데이터를 호스트하는 OMS 작업 영역으로 매핑합니다. 업그레이드 준비에 사용하기 위한 상업용 ID 키를 이미 구성한 경우 해당 ID를 사용합니다. 아직 상업용 ID 키가 없는 경우 [상업용 ID 키 생성]( https://technet.microsoft.com/itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key)을 참조하세요.

  -  **Windows 10 장치에 대한 원격 분석 수준**   
각 Windows 10 원격 분석 수준에 대한 자세한 내용은 [조직에서 Windows 원격 분석 구성](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels)을 참조하세요.

   > [!Note]
   > 1710 업데이트를 사용하면 Windows 10 원격 분석 데이터 수집 수준을 **고급(제한적)** 으로 설정할 수 있습니다. 이 설정을 사용하면 Windows 10 버전 1709 이상을 사용하여 **고급** 원격 분석 수준의 모든 데이터를 보고하는 장치가 없는 환경에서 장치에 대해 조치 가능한 통찰력을 얻을 수 있습니다. 고급(제한적) 원격 분석 수준에는 Windows Analytics와 관련된 고급 수준에서 수집된 데이터 하위 집합뿐 아니라 기본 레벨의 메트릭도 포함됩니다.


  -  **Windows 7, 8 및 8.1 장치에서 상용 데이터 수집에 옵트인**   
자세한 내용은 [Windows 7, Windows 8 및 Windows 8.1 평가자 원격 분석 이벤트 및 필드](https://go.microsoft.com/fwlink/?LinkID=822965)를 참조하세요.

  -  **Internet Explorer 데이터 수집 구성**  
Windows 8.1 또는 이전 버전을 실행하는 장치에서 Internet Explorer 데이터 수집을 수행하면 업그레이드 준비 기능을 통해 Windows 10으로의 원활한 업그레이드에 방해가 될 수 있는 웹 응용 프로그램 비호환성 문제를 감지할 수 있습니다. Internet Explorer 데이터 수집은 인터넷 영역별로 사용 가능하게 설정할 수 있습니다. 인터넷 영역에 대한 자세한 내용은 [URL 보안 영역 정보](https://msdn.microsoft.com/library/ms537183(v=vs.85).aspx)를 참조하세요.

## <a name="use-upgrade-readiness-to-identify-windows-10-compatibility-issues"></a>업그레이드 준비를 사용하여 Windows 10 호환성 문제 식별

업그레이드 준비(이전의 Upgrade Analytics)를 사용하면 Windows 10과의 호환성 및 장치 준비 상태를 분석할 수 있습니다. 이 평가를 통해 업그레이드를 좀 더 원활하게 진행할 수 있습니다. Configuration Manager를 업그레이드 준비에 연결한 후에는 Configuration Manager 관리 콘솔에서 직접 이 클라이언트 업그레이드 호환성 데이터에 액세스합니다. 그런 다음 장치 목록에서 업그레이드 또는 수정할 장치를 대상으로 지정합니다.

자세한 내용과 업그레이드 준비 구성 및 연결 방법에 대한 세부 정보를 보려면 [업그레이드 준비](../../clients/manage/upgrade/upgrade-analytics.md)를 참조하세요.

## <a name="use-windows-analytics-to-identify-gaps-in-windows-information-protection-policies"></a>Windows Analytics를 사용하여 Windows Information Protection 정책의 차이 식별

WIP([Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip)) 정책으로 구성된 Windows 10 버전 1703 이상 장치는 환경의 회사 데이터에 액세스하지만 WIP 정책 응용 프로그램 규칙에 포함되지 않는 응용 프로그램에 대한 원격 분석을 보고합니다. 사용자가 이러한 응용 프로그램의 생산성을 유지해야 할 수 있지만 WIP는 사용자의 액세스를 차단합니다. 사용자가 회사 데이터에 액세스하는 기술은 Configuration Manager에서 Windows Information Protection 정책을 유지 관리하는 데 유용합니다. 

이 [Operations Management Suite 쿼리](https://go.microsoft.com/fwlink/?linkid=849952)를 사용하여 이 Windows Information Protection 데이터에 액세스합니다.