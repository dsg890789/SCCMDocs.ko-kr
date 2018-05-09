---
title: Asset Intelligence 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 Asset Intelligence에 대한 필수 조건을 확인합니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 23ab4f94-7bfe-436e-8a6a-029409a2730c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b8e7477f8a5b837327640f78656070579fad23a8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager의 Asset Intelligence에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Asset Intelligence에는 외부 종속성과 제품 내 종속성이 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  
 다음 표에서는 Configuration Manager 외부에 있는 Asset Intelligence에 대한 종속성을 제공합니다.  

|종속성|추가 정보|  
|----------------|----------------------|  
|성공 로그온 이벤트 필수 조건 감사|네 가지 Asset Intelligence 보고서에 클라이언트 컴퓨터의 Windows 보안 이벤트 로그에서 수집된 정보가 표시됩니다. 보안 이벤트 로그 설정이 모든 성공 로그온 이벤트를 기록하도록 구성되지 않으면 적절한 하드웨어 인벤토리 보고 클래스를 사용하도록 설정된 경우에도 해당 보고서에 데이터가 포함되지 않습니다.<br /><br /> 다음 Asset Intelligence 보고서는 수집된 Windows 보안 이벤트 로그 정보에 따라 달라집니다.<br /><br /> -   하드웨어 03A - 기본 컴퓨터 사용자<br />-   하드웨어 03B - 특정 기본 콘솔 사용자의 컴퓨터<br />-   하드웨어 04A - 공유(다중 사용자) 컴퓨터<br />-   하드웨어 05A - 특정 컴퓨터의 콘솔 사용자<br /><br /> 이러한 보고서를 지원하는 데 필요한 정보를 인벤토리에 포함하기 위해 하드웨어 인벤토리 클라이언트 에이전트를 사용하도록 설정하려면, 먼저 모든 성공 로그온 이벤트를 기록하도록 클라이언트의 Windows 보안 이벤트 로그 설정을 수정하고 **SMS_SystemConsoleUser** 하드웨어 인벤토리 보고 클래스를 사용하도록 설정해야 합니다. 모든 성공 로그온 이벤트를 기록하도록 보안 이벤트 로그 설정을 수정하는 방법에 대한 자세한 내용은 [성공 로그온 이벤트 감사 사용](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableSuccessLogonEvents)을 참조하세요.|  

> [!NOTE]  
>  **SMS_SystemConsoleUser** 하드웨어 인벤토리 보고 클래스는 로그의 길이와 관계없이 보안 이벤트 로그의 이전 90일간의 성공적인 로그온 이벤트 데이터만 보존합니다. 보안 이벤트 로그에 있는 데이터가 90일 미만인 경우 전체 로그를 읽습니다.  

## <a name="dependencies-internal-to-configuration-manager"></a>Configuration Manager 내부 종속성  
 다음 표에서는 Configuration Manager 내부에 있는 Asset Intelligence에 대한 종속성을 제공합니다.  

|종속성|추가 정보|  
|----------------|----------------------|  
|클라이언트 에이전트 필수 조건|Asset Intelligence 보고서는 클라이언트 하드웨어 및 소프트웨어 인벤토리 보고서를 통해 얻은 클라이언트 정보에 따라 달라집니다. 모든 Asset Intelligence 보고서에 필요한 정보를 얻으려면 다음 클라이언트 에이전트를 사용하도록 설정해야 합니다.<br /><br /> -   하드웨어 인벤토리 클라이언트 에이전트<br />-   소프트웨어 계량 클라이언트 에이전트|  
|하드웨어 인벤토리 클라이언트 에이전트 종속성|일부 Asset Intelligence 보고서에 필요한 인벤토리 데이터를 수집하려면 하드웨어 인벤토리 클라이언트 에이전트를 사용하도록 설정해야 합니다. 또한 Asset Intelligence 보고서가 종속되는 일부 하드웨어 인벤토리 보고 클래스는 기본 사이트 서버 컴퓨터에서 사용하도록 설정해야 합니다.<br /><br /> 하드웨어 인벤토리 클라이언트 에이전트를 활성화하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 확장하는 방법](../../../../core/clients/manage/inventory/extend-hardware-inventory.md)을 참조하세요.|  
|소프트웨어 계량 클라이언트 에이전트 종속성|다양한 Asset Intelligence 소프트웨어 보고서는 데이터에 대한 소프트웨어 계량 클라이언트 에이전트에 따라 달라집니다. 소프트웨어 계량 클라이언트 에이전트를 사용하도록 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 소프트웨어 계량을 사용하여 앱 사용 모니터링](../../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.<br /><br /> 다음 Asset Intelligence 보고서는 데이터를 제공하는 소프트웨어 계량 클라이언트 에이전트에 따라 달라집니다.<br /><br /> -   소프트웨어 07A - 컴퓨터 수별 최근 사용된 실행 파일<br />-   소프트웨어 07B - 지정된 실행 파일을 최근 사용한 컴퓨터<br />-   소프트웨어 07C - 특정 컴퓨터에서 최근 사용된 실행 파일<br />-   소프트웨어 08A - 사용자 수별 최근 사용된 실행 파일<br />-   소프트웨어 08B - 지정된 실행 파일을 최근 사용한 사용자<br />-   소프트웨어 08C - 지정된 사용자가 최근 사용한 실행 파일|  
|Asset Intelligence 하드웨어 인벤토리 보고 클래스 필수 조건|Configuration Manager의 Asset Intelligence 보고서는 특정 하드웨어 인벤토리 보고 클래스에 따라 달라집니다. 하드웨어 인벤토리 보고 클래스가 사용하도록 설정되고 클라이언트가 이러한 클래스를 기반으로 하는 하드웨어 인벤토리를 보고할 때까지 관련된 Asset Intelligence 보고서에는 데이터가 포함되지 않습니다. Asset Intelligence 보고 요구 사항을 지원하도록 다음 하드웨어 인벤토리 보고 클래스를 사용하도록 설정할 수 있습니다.<br /><br /> -   SMS_SystemConsoleUsage<sup>1</sup><br />-   SMS_SystemConsoleUser<sup>1</sup><br />-   SMS_InstalledSoftware<br />-   SMS_AutoStartSoftware<br />-   SMS_BrowserHelperObject<br />-   Win32_USBDevice<br />-   SMS_InstalledExecutable<br />-   SMS_SoftwareShortcut<br />-   SoftwareLicensingService<br />-   SoftwareLicensingProduct<br />-   SMS_SoftwareTag<br /><br /> <sup>1</sup> 기본적으로 **SMS_SystemConsoleUsage** 및 **SMS_SystemConsoleUser** Asset Intelligence 하드웨어 인벤토리 보고 클래스는 사용하도록 설정되어 있습니다.<br /><br /> **Asset Intelligence** 노드를 클릭하면 **자산 및 준수** 작업 영역의 Configuration Manager 콘솔에서 하드웨어 인벤토리 보고 클래스를 편집할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md) 항목의 [Asset Intelligence 하드웨어 인벤토리 보고 클래스를 사용하도록 설정](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableAssetIntelligence) 섹션을 참조하세요.|  
|보고 서비스 지점|소프트웨어 업데이트 보고서가 표시되려면 먼저 보고 서비스 지점 사이트 시스템 역할이 설치되어 있어야 합니다. 보고 서비스 지점을 만드는 방법에 대한 자세한 내용은 [Configuration Manager에서 보고 구성](http://go.microsoft.com/fwlink/p/?LinkId=232661)을 참조하세요.|  
