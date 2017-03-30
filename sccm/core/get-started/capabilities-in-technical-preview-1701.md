---
title: "Technical Preview 1701 Configuration Manager의 기능"
description: "System Center Configuration Manager용 Technical Preview 버전 1701에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18598eaa-1131-44ff-8f8b-6093e87ac7a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b330c97a0853d1673f1cf7e0691891b72407fa51
ms.lasthandoff: 03/27/2017

---
# <a name="capabilities-in-technical-preview-1701-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1701의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*



이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1701에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="boundary-groups-improvements-for-software-update-points"></a>소프트웨어 업데이트 지점에 대한 향상된 경계 그룹
이 미리 보기부터 이제 경계 그룹을 사용하여 클라이언트를 소프트웨어 업데이트 지점에 연결합니다. 이는 추가 사이트 시스템 역할을 관리하기 위해 경계 그룹에 대한 변경을 확장하는 지속적인 작업의 일부입니다.  경계 그룹에 대한 변경은 Technical Preview 1609 및 버전 1610의 현재 분기에서 처음 도입되었습니다.  

이 미리 보기에서는 클라이언트에서 사용할 수 있는 배포 지점을 관리하는 방법과 마찬가지로, 새 경계 그룹 동작을 통해 클라이언트에서 사용할 수 있는 소프트웨어 업데이트 지점을 관리합니다.  

- 경계 그룹을 구성하여 소프트웨어 업데이트 지점을 호스트하는 서버를 하나 이상 연결합니다.
- 새 소프트웨어 업데이트 지점을 원하는 클라이언트는 현재 경계 그룹과 연결된 소프트웨어 업데이트 지점을 사용하려고 합니다.
- 클라이언트는 현재 소프트웨어 업데이트 지점에 연결하지 못하고 현재 경계 그룹에서 소프트웨어 업데이트 지점을 찾을 수 없는 경우 대체 동작을 사용하여 사용할 수 있는 소프트웨어 업데이트 지점 풀을 확장합니다.    

경계 그룹에 대한 자세한 내용은 현재 분기에 대한 콘텐츠에서 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups)을 참조하세요.

그러나 이 미리 보기에서는 소프트웨어 업데이트 지점에 대한 경계 그룹이 부분적으로만 구현되었습니다. 소프트웨어 업데이트 지점을 추가하고 소프트웨어 업데이트 지점을 포함하는 인접한 경계 그룹을 구성할 수 있지만 소프트웨어 업데이트 지점에 대한 대체 시간은 아직 지원되지 않으며, 클라이언트가 2시간 동안 기다려야 대체가 시작됩니다.

다음은 이 Technical Preview의 소프트웨어 업데이트 지점 동작에 대한 설명입니다.  

-    **새 클라이언트는 경계 그룹을 사용하여 소프트웨어 업데이트 지점을 선택합니다.** 버전 1701을 설치한 후 설치하는 클라이언트는 클라이언트의 경계 그룹과 연결된 소프트웨어 업데이트 지점에서 하나를 선택합니다.

  이 동작은 클라이언트가 클라이언트 포리스트를 공유하는 소프트웨어 업데이트 지점 목록에서 임의로 하나를 선택하는 이전 동작을 대체합니다.   

-    **이전에 설치한 클라이언트는 새 소프트웨어 업데이트 지점을 찾도록 대체될 때까지 현재 소프트웨어 업데이트 지점을 계속 사용합니다.**
이전에 설치했으며 이미 소프트웨어 업데이트 지점이 있는 클라이언트는 대체될 때까지 해당 소프트웨어 업데이트 지점을 계속 사용합니다. 여기에는 클라이언트의 현재 경계 그룹과 연결되지 않은 소프트웨어 업데이트 지점도 포함됩니다. 즉시 현재 경계 그룹에서 소프트웨어 업데이트 지점을 찾아서 사용하려고 하지 않습니다.

  이미 소프트웨어 업데이트 지점이 있는 클라이언트는 현재 소프트웨어 업데이트 지점에 연결하지 못하여 대체를 시작한 후에만 이 새로운 경계 그룹 동작을 사용하기 시작합니다.
새 동작으로 전환 시 발생하는 이 지연은 의도적인 것입니다. 이는 소프트웨어 업데이트 지점 변경 시 클라이언트가 새 소프트웨어 업데이트 지점과 데이터를 동기화하면서 네트워크 대역폭이 많이 사용될 수 있기 때문입니다. 전환 시의 지연은 모든 클라이언트가 새 소프트웨어 업데이트 지점으로 동시에 전환할 경우 발생하는 네트워크 혼잡을 방지하는 데 도움이 됩니다.

-    **대체 시간 구성:** 클라이언트가 새 소프트웨어 업데이트 지점을 검색하도록 대체를 시작하는 시기에 대한 구성은 이 Technical Preview에서 지원되지 않습니다. 여기에는 다양한 경계 그룹 관계에 대해 구성할 수 있는 **대체 시간(분)** 및 **대체 안 함** 구성이 포함됩니다.

  대신, 클라이언트가 사용할 수 있는 새 소프트웨어 업데이트 지점을 찾도록 대체를 시작하기 전에 2시간 동안 현재 소프트웨어 업데이트 지점에 연결을 시도하는 현재 클라이언트 동작은 유지됩니다.

  클라이언트는 대체를 사용할 때 대체에 대한 경계 그룹 구성을 사용하여 사용 가능한 소프트웨어 업데이트 지점 풀을 만듭니다. 이 풀에는 클라이언트 *현재 경계 그룹*, *인접한 경계 그룹* 및 클라이언트 *사이트 기본 경계 그룹*의 모든 소프트웨어 업데이트 지점이 포함됩니다.

- **기본 사이트 경계 그룹 구성:**  
 *기본 사이트 경계 그룹&lt;사이트 코드>*에 소프트웨어 업데이트 지점을 추가하는 것이 좋습니다. 이렇게 하면 다른 경계 그룹의 구성원이 아닌 클라이언트가 소프트웨어 업데이트 지점을 찾도록 대체될 수 있습니다.


경계 그룹에 대한 소프트웨어 업데이트 지점을 관리하려면 [현재 분기 설명서의 절차](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#procedures-for-boundary-groups)를 사용합니다. 단, 구성하는 대체 시간은 소프트웨어 업데이트 지점에 아직 사용되지 않습니다.


## <a name="hardware-inventory-collects-uefi-information"></a>하드웨어 인벤토리를 통해 UEFI 정보 수집
새 하드웨어 인벤토리 클래스(**SMS_Firmware**) 및 속성(**UEFI**)을 사용하여 컴퓨터를 UEFI 모드로 시작할지 여부를 결정할 수 있습니다. 컴퓨터를 UEFI 모드로 시작하는 경우 **UEFI** 속성을 **TRUE**로 설정합니다. 하드웨어 인벤토리에서 기본적으로 사용됩니다. 하드웨어 인벤토리에 대한 자세한 내용은 [하드웨어 인벤토리를 구성하는 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.

## <a name="improvements-to-operating-system-deployment"></a>운영 체제 배포 향상
운영 체제 배포가 다음과 같이 향상되었으며, 이러한 향상된 기능은 대부분 사용자 의견 피드백의 결과입니다.
- [**응용 프로그램 설치 작업 순서 단계와 관련해서 더 많은 응용 프로그램 지원**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17062207-task-sequence-allow-more-than-9-applications-in-t): **응용 프로그램 설치** 작업 순서 단계에서 설치할 수 있는 최대 응용 프로그램 수가 99개로 증가되었습니다. 이전의 최대 개수는 응용 프로그램 9개였습니다.
- [**앱 설치 작업 순서 단계에서 여러 앱 선택**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15459978-when-adding-items-to-an-install-application-step): 작업 순서 편집기에서 응용 프로그램 설치 작업 순서 단계에 응용 프로그램을 추가하는 경우 이제 **설치할 응용 프로그램 선택** 창에서 여러 응용 프로그램을 선택할 수 있습니다.
- [**독립 실행형 미디어 만료**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/14448564-provide-a-method-for-expiring-standalone-media): 독립 실행형 미디어를 만드는 경우 미디어에 선택적 시작 및 만료 날짜를 설정하는 새 옵션이 있습니다. 이러한 설정은 기본적으로 사용되지 않습니다. 독립 실행형 미디어를 실행하기 전에 날짜가 컴퓨터의 시스템 시간과 비교됩니다. 시스템 시간이 시작 시간보다 이전이거나 만료 시간보다 이후이면 독립 실행형 미디어가 시작되지 않습니다. New-CMStandaloneMedia PowerShell cmdlet을 사용하여 이러한 옵션을 사용할 수도 있습니다.
- [**독립 실행형 미디어의 추가 콘텐츠 지원**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8341257-support-installation-of-packages-apps-via-dynamic): 이제 독립 실행형 미디어에서 추가 콘텐츠가 지원됩니다. 작업 순서에서 참조된 다른 콘텐츠와 함께 미디어에 스테이징할 추가 패키지, 드라이버 패키지 및 응용 프로그램을 선택할 수 있습니다. 이전에는 작업 순서에서 참조된 콘텐츠만 독립 실행형 미디어에 스테이징되었습니다.
- [**드라이버 자동 적용 작업 순서 단계에 대한 구성 가능한 시간 제한**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17153660-auto-apply-driver-timeout): 이제 새 작업 순서 변수를 사용하여 HTTP 카탈로그 요청 시 드라이버 자동 적용 작업 순서 단계에 대한 시간 제한 값을 구성할 수 있습니다. 다음 변수와 기본값(초)을 사용할 수 있습니다.
   - SMSTSDriverRequestResolveTimeOut 기본값: 60
   - SMSTSDriverRequestConnectTimeOut 기본값: 60
   - SMSTSDriverRequestSendTimeOut 기본값: 60
   - SMSTSDriverRequestReceiveTimeOut 기본값: 480
- [**이제 작업 순서 단계에 패키지 ID가 표시됨**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16167430-display-packageid-when-viewing-a-task-sequence-ste): 이제 패키지, 드라이버 패키지, 운영 체제 이미지, 부팅 이미지 또는 운영 체제 업그레이드 패키지를 참조하는 모든 작업 순서 단계에 참조된 개체의 패키지 ID가 표시됩니다. 응용 프로그램을 참조하는 작업 순서 단계에 개체 ID가 표시됩니다.
- **Windows 10 ADK가 빌드 버전별로 추적됨**: 이제 Windows 10 ADK가 빌드 버전별로 추적되므로 Windows 10 부팅 이미지를 사용자 지정할 때 환경에서 더 많은 지원이 제공됩니다. 예를 들어 사이트에서 Windows 10 버전 1607용 Windows ADK를 사용하는 경우 버전 10.0.14393인 부팅 이미지만 콘솔에서 사용자 지정할 수 있습니다. WinPE 버전을 사용자 지정하는 방법에 대한 자세한 내용은 [부팅 이미지 사용자 지정](/sccm/osd/get-started/customize-boot-images)을 참조하세요.
- **기본 부팅 이미지 원본 경로를 더 이상 변경할 수 없음**: 기본 부팅 이미지가 Configuration Manager에서 관리되며, 더 이상 Configuration Manager 콘솔이나 Configuration Manager SDK를 사용하여 기본 부팅 이미지 원본 경로를 변경할 수 없습니다. 사용자 지정 부팅 이미지에 대한 사용자 지정 원본 경로는 계속 구성할 수 있습니다.

## <a name="host-software-updates-on-cloud-based-distribution-points"></a>클라우드 기반 배포 지점에서 소프트웨어 업데이트 호스트
이 미리 보기 버전부터 클라우드 기반 배포 지점을 사용하여 소프트웨어 업데이트 패키지를 호스트할 수 있습니다. 그러나 Microsoft 업데이트에서 직접 소프트웨어 업데이트를 다운로드하도록 클라이언트를 구성할 수 있으므로 클라우드 기반 배포 지점에 소프트웨어 업데이트 패키지를 배포할 경우 발생할 수 있는 추가 비용을 고려해야 합니다.

클라우드 기반 배포 지점을 사용하는 방법에 대한 자세한 내용은 Configuration Manager 현재 분기에 대한 콘텐츠에서 [클라우드 기반 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)을 참조하세요.

## <a name="validate-device-health-attestation-data-via-management-points"></a>관리 지점을 통해 장치 상태 증명 데이터의 유효성 검사

이 미리 보기 버전부터 클라우드 또는 온-프레미스 상태 증명 서비스에 대한 상태 증명 보고 데이터의 유효성을 검사하도록 관리 지점을 구성할 수 있습니다. **관리 지점 구성 요소 속성** 대화 상자의 새 **고급 옵션** 탭에서 **온-프레미스 장치 상태 증명 서비스 URL**을 **추가**, **편집** 또는 **제거**할 수 있습니다. **온-프레미스 상태 증명 서비스를 사용**하도록 클라이언트 에이전트에 대한 **사용자 지정 장치 설정**을 지정할 수도 있습니다.  이 설정에 대해 **예**를 설정하면 클라우드 기반 서비스 대신 온-프레미스 관리 지점에 보고할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

- **관리 지점에서 온-프레미스 장치 상태 증명 사용**<br>  Configuration Manager 콘솔에서 관리 지점으로 이동하고 **관리 지점 구성 요소 속성**을 연 다음 **고급 옵션** 탭을 클릭합니다. **추가**를 클릭하고 **온-프레미스 장치 상태 증명 서비스 URL**에 대해 온-프레미스 URL (예: https://10.10.10.10) 을 지정합니다.
- **클라이언트 에이전트에 대해 온-프레미스 관리 지점 상태 증명 보고 사용**<br>Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**을 선택하고 두 번 클릭하거나 새 **사용자 지정 장치 설정**을 만듭니다. **컴퓨터 에이전트**를 선택하고 **온-프레미스 상태 증명 서비스 사용**을 **예**로 설정합니다. **장치 상태 증명 서비스와 통신 사용**이 **예**로 설정되고 **온-프레미스 상태 증명 사용**이 **아니요**로 설정된 경우 관리 지점에서 클라우드 기반 장치 상태 증명 서비스를 사용합니다.

## <a name="use-the-oms-connector-for-microsoft-azure-government-cloud"></a>Microsoft Azure Government 클라우드용 OMS 커넥터 사용
이 Technical Preview에서는 Microsoft OMS(Operations Management Suite) 커넥터를 사용하여 Microsoft Azure Government 클라우드에 있는 OMS 작업 영역에 연결할 수 있습니다.  

이렇게 하려면 Government 클라우드를 가리키도록 구성 파일을 수정한 후 OMS 커넥터를 설치합니다.

### <a name="set-up-an-oms-connector-to-microsoft-azure-government-cloud"></a>Microsoft Azure Government 클라우드에 대한 OMS 커넥터 설정
1.  Configuration Manager 콘솔이 설치되어 있는 컴퓨터에서 Government 클라우드를 가리키도록 다음 구성 파일을 편집합니다. ***&lt;CM 설치 경로>\AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **편집:**

    설정 이름 *FairFaxArmResourceID*의 값을 "https://management.usgovcloudapi.net/"으로 변경합니다.

   - **원래 값:**
      &lt;setting name="FairFaxArmResourceId" serializeAs="String">   
      &lt;value>&lt;/value>   
      &lt;/setting>

   - **편집된 값:**     
      &lt;setting name="FairFaxArmResourceId" serializeAs="String"> &lt;value>https://management.usgovcloudapi.net/&lt;/value>  
      &lt;/setting>

  설정 이름 *FairFaxAuthorityResource*의 값을 "https://login.microsoftonline.com/"으로 변경합니다.

  - **원래 값:**
    &lt;setting name="FairFaxAuthorityResource" serializeAs="String">   
    &lt;value>&lt;/value>

    - **편집된 값:**
    &lt;setting name="FairFaxAuthorityResource" serializeAs="String">   
    &lt;value>https://login.microsoftonline.com/&lt;/value>

2.    두 가지 사항을 변경하고 파일을 저장한 후 동일한 컴퓨터에서 Configuration Manager 콘솔을 다시 시작하고 해당 콘솔을 사용하여 OMS 커넥터를 설치합니다. 커넥터를 설치하려면 [Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)에 제공된 정보를 사용하고 Microsoft Azure Government 클라우드에 있는 **Operations Management Suite 작업 영역**을 선택합니다.

3.    OMS 커넥터가 설치되면 사이트에 연결하는 모든 콘솔에서 Government 클라우드에 대한 연결을 사용할 수 있습니다.

## <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android 및 iOS 버전은 하이브리드 MDM 만들기 마법사에서 대상 지정이 가능하지 않음

하이브리드 MDM(모바일 장치 관리)에 대한 이 Technical Preview부터 Intune 관리 장치에 대한 새 정책 및 프로필을 만들 때 특정 버전의 Android 및 iOS를 대상으로 지정할 필요가 없습니다. 대신 다음 장치 유형 중 하나를 선택합니다.

- Android
- Samsung KNOX Standard 4.0 이상
- iPhone
- iPad

이 변경 내용은 다음 항목을 만들기 위한 마법사에 영향을 줍니다.

- 구성 항목
- 규정 준수 정책
- 인증서 프로필
- 전자 메일 프로필
- VPN 프로필
- Wi-Fi 프로필

이러한 변경으로 인해 하이브리드 배포에서 새 Configuration Manager 릴리스나 확장 없이 새 Android 및 iOS 버전을 더 빠르게 지원할 수 있습니다. Intune 독립 실행형에서 새 버전이 지원되게 되면 사용자는 모바일 장치를 해당 버전으로 업그레이드할 수 있습니다.

이전 버전의 Configuration Manager에서 업그레이드할 때 문제를 방지하려면 이러한 항목의 속성 페이지에서 모바일 운영 체제 버전을 계속 사용할 수 있습니다. 특정 버전을 대상으로 지정해야 하는 경우 새 항목을 만든 다음 새로 만든 항목의 속성 페이지에서 대상 버전을 지정할 수 있습니다.

