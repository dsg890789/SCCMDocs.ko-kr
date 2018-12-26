---
title: 버전 1606의 새로운 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager 버전 1606에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: df2e57b9-6445-4067-98e7-ace85d4e6aa6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0dcd2db7543d68a97e00244536d2aac218d440e7
ms.sourcegitcommit: 2cc635835709fb8d86cdb63ea34233b36c94d4d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52259066"
---
# <a name="what39s-new-in-version-1606-of-system-center-configuration-manager"></a>System Center Configuration Manager 버전 1606의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 업데이트 1606은 버전 1511 또는 1602를 실행하는 이전에 설치된 사이트에 대한 콘솔 내 업데이트로 제공됩니다. 버전 1511은 새 Configuration Manager 사이트를 설치하는 데 사용하는 초기 기준 버전입니다.
> [!TIP]  
>  다음에 대해 자세히 알아보세요.  
>   
>  -   [새 사이트 설치](/sccm/core/servers/deploy/install)(1511 등의 기준 버전 사용)  
>  -   [사이트에서 업데이트 설치](/sccm/core/servers/manage/updates)(예: 업데이트 1602 또는 1606)  

 다음 섹션에서는 Configuration Manager 버전 1606에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.  



## <a name="updatesandservicing"></a>업데이트 및 서비스

### <a name="changes-for-the-updates-and-servicing-node"></a>업데이트 및 서비스 노드의 변경 내용
다음은 Configuration Manager 콘솔의 업데이트 및 서비스 노드에 대한 변경 내용입니다.
> [!NOTE]
> 버전 1606을 설치한 후에는 이러한 변경 내용을 사용할 수 없습니다.

- **노드 이름 변경:**

    **모니터링** 작업 영역에서 **사이트 서비스 상태** 노드의 이름이 **업데이트 및 서비스 상태**로 변경되었습니다.
- **추가 설치 상태 세부 정보:**

    이제 사이트에 대한 업데이트 설치 상태를 볼 때 콘솔에 다음 작업에 대한 별도 세부 정보가 표시됩니다.
    - **다운로드**(서비스 연결 지점 사이트 시스템 역할이 설치되어 있는 최상위 계층 사이트에만 적용됨)
    - **복제**
    - **필수 구성 요소 확인**
    - **설치**

  또한 추가 정보를 볼 수 있는 로그 파일을 포함하여 이제 각 단계에 대한 더 자세한 정보를 볼 수 있습니다.  
-   **필수 조건 실패 시 다시 시도하는 새 옵션:**

    **관리** 및 **모니터링** 작업 영역 둘 다에서 **업데이트 및 서비스** 노드에 **필수 조건 경고 무시**라는 리본의 새 단추가 포함됩니다.

    필수 조건 경고를 무시하는 옵션을 사용하지 않고 업데이트를 설치하는 경우(업데이트 마법사 내에서) 해당 업데이트 설치가 경고로 인해 중단되면 리본에서 **필수 조건 경고 무시**를 선택할 수 있습니다. 그러면 해당 업데이트 설치의 자동 진행이 트리거됩니다.  



- **업데이트의 명확한 정보:**

    **업데이트 및 서비스** 노드에서 이제 가장 최근에 설치된 업데이트와 설치 가능한 새 업데이트를 볼 수 있습니다. 이전에 설치된 업데이트를 보려면 리본에 새로 표시된 **기록** 단추를 클릭합니다.  

-   **이름이 변경된 사전 프로덕션 옵션:**

    **업데이트 및 서비스** 노드에서 **클라이언트 옵션** 단추는 이제 **사전 프로덕션 클라이언트 수준 올리기**로 표시됩니다.


###  <a name="pre-release-features"></a>시험판 기능
1606부터 System Center Configuration Manager의 시험판 기능 사용을 선택하고 사용하도록 설정하려면 먼저 해당 기능을 사용한다는 데 동의해야 합니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease)을 참조하세요.

### <a name="new-distribution-point-update-behavior"></a>새 배포 지점 업데이트 동작
업데이트 1606에서는 이후 업데이트를 설치할 때 배포 지점의 가용성을 개선하는 변경 내용이 도입되었습니다.

업데이트 1606이 설치된 후 해당 사이트에서 표준 및 끌어오기-배포 지점 사이트 시스템 역할을 자동으로 다시 설치해야 하는 업데이트를 설치할 경우 모든 배포 지점이 동시에 업데이트되기 위해 더 이상 오프라인으로 전환되지 않습니다. 대신, 사이트 서버에서 사이트의 콘텐츠 배포 설정을 사용하여 지정된 시간에 배포 지점 하위 집합에 업데이트를 배포합니다. 따라서 일부 배포 지점만 업데이트 설치를 위해 오프라인으로 전환됩니다. 이렇게 하면 아직 업데이트가 시작되지 않았거나 업데이트가 완료된 배포 지점은 온라인 상태로 유지되고 클라이언트에 콘텐츠를 제공할 수 있습니다.



## <a name="accessibility"></a> 접근성
작업 영역의 다른 노드로 이동하려면 이제 노드 이름의 첫 글자를 입력하면 됩니다. 키를 누를 때마다 해당 문자로 시작하는 다음 노드로 커서가 이동합니다. 화면 읽기 프로그램을 사용하는 사용자의 경우 읽기 프로그램이 해당 노드의 이름을 읽어냅니다. 접근성 옵션에 대한 자세한 내용은 [System Center Configuration Manager의 접근성 기능](../../../core/understand/accessibility-features.md)을 참조하세요.

## <a name="administration"></a>관리
다음은 Configuration Manager 콘솔의 관리에 대한 변경 내용입니다.
### <a name="oms-connector"></a>OMS 커넥터

이제 System Center Configuration Manager에서 [Microsoft OMS(Operations Management Suite)](https://azure.microsoft.com/documentation/articles/operations-management-suite-overview/)로 Configuration Manager를 컬렉션으로 연결할 수 있습니다. 이렇게 하면 Configuration Manager 배포의 데이터(예: 컬렉션)가 OMS에 표시됩니다. 자세한 내용은 [Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md)를 참조하세요.

OMS 커넥터는 시험판 기능입니다. 사용하도록 설정하려면 [업데이트에서 시험판 기능 사용](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease)을 참조하세요.

### <a name="support-for-cache-size-in-client-settings"></a>클라이언트 설정에서 캐시 크기 지원

이제 Configuration Manager 콘솔의 **클라이언트 설정**을 사용하여 클라이언트 컴퓨터의 캐시 폴더 크기를 구성할 수 있습니다. 이전에는 클라이언트 소프트웨어를 설치하거나 다시 설치할 때만 클라이언트 캐시 크기를 설정할 수 있었습니다. 이제 클라이언트 설정(기본값 또는 사용자 지정)으로 캐시 크기를 지정한 다음 클라이언트를 다시 설치할 필요 없이 클라이언트에서 다음 정책 업데이트 시 해당 설정을 적용할 수 있습니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 클라이언트 캐시 구성](../../../core/clients/manage/manage-clients.md#BKMK_ClientCache)항목을 참조하세요.

## <a name="on-premises-mobile-device-management"></a>온-프레미스 MDM(모바일 디바이스 관리)

### <a name="support-for-multiple-device-management-points"></a>여러 디바이스 관리 지점에 대한 지원

이제 온-프레미스 MDM(모바일 디바이스 관리)에서 둘 이상의 디바이스 관리 지점을 사용할 수 있도록 등록된 디바이스를 자동으로 구성하는 Windows 10 1주년 업데이트의 새로운 기능을 지원합니다. 이 기능을 통해 디바이스는 사용 중인 디바이스 관리 지점을 사용할 수 없게 되면 다른 디바이스 관리 지점으로 대체할 수 있습니다. 이 기능은 Windows 10 1주년 업데이트가 설치된 PC 및 디바이스에서만 사용할 수 있습니다.


## <a name="application-management"></a>애플리케이션 관리

### <a name="manage-apps-from-the-windows-store-for-business"></a>비즈니스용 Windows 스토어에서 앱 관리

[비즈니스용 Windows 스토어](https://www.microsoft.com/business-store)에서 조직을 위한 Windows 앱을 찾아서 개별적으로 또는 대량으로 구매할 수 있습니다. 저장소를 Configuration Manager에 연결하면 구입한 앱 목록을 Configuration Manager와 동기화하고 Configuration Manager 콘솔에서 해당 앱을 보고 다른 앱처럼 배포할 수 있습니다.

자세한 내용은 [System Center Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱 관리](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business.md)를 참조하세요.

### <a name="manage-ios-volume-purchased-apps"></a>iOS 대량 구매 앱 관리

Configuration Manager를 사용하여 대량 구매 iOS 앱을 관리하고 배포하기 위한 워크플로가 향상되었습니다.

자세한 내용은 [System Center Configuration Manager를 사용하여 대량 구매한 iOS 앱 관리](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md)를 참조하세요.

### <a name="software-center-user-interface"></a>소프트웨어 센터 사용자 인터페이스

소프트웨어 센터 사용자 인터페이스가 검색하기 쉽도록 간소화되었습니다.
*  **설치 상태** 및 **설치된 소프트웨어** 탭이 하나의 **설치 상태** 탭으로 결합되었습니다.
*  **업데이트**, **운영 체제** 및 **응용 프로그램**이 3개의 개별 탭으로 구분되었습니다.
* 이제 한 번에 설치하기 위해 여러 업데이트를 선택하거나, **모두 설치**를 클릭하여 한 번에 모든 업데이트를 설치할 수 있습니다.

### <a name="content-status-links"></a>콘텐츠 상태 링크
애플리케이션 또는 패키지의 속성에는 이제 해당 개체의 상태로 이동하는 링크가 있습니다.

## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="client-setting-to-manage-the-office-365-client-agent"></a>Office 365 클라이언트 에이전트를 관리하는 클라이언트 설정
이제 Configuration Manager 클라이언트 설정을 사용하여 Office 365 클라이언트 에이전트를 관리할 수 있습니다. 이를 설정하고 Office 365 업데이트를 배포한 후 Configuration Manager 클라이언트 에이전트는 Office 365 클라이언트 에이전트와 연동하여 배포 지점에서 Office 365 업데이트를 다운로드하고 설치합니다.

자세한 내용은 [Configuration Manager를 사용하여 Office 365 ProPlus 업데이트 관리](../../../sum/deploy-use/manage-office-365-proplus-updates.md)를 참조하세요.

### <a name="manually-switch-clients-to-a-new-software-update-point"></a>수동으로 클라이언트를 새 소프트웨어 업데이트 지점으로 전환
이제 활성 소프트웨어 업데이트 지점에 문제가 있는 경우 Configuration Manager 클라이언트가 새로운 소프트웨어 업데이트 지점으로 전환하는 옵션을 사용할 수 있습니다. 사용하도록 설정하면 클라이언트가 다음 검사 시 다른 소프트웨어 업데이트 지점을 찾습니다.

자세한 내용은 [Configuration Manager에서 소프트웨어 업데이트 계획](../../../sum/plan-design/plan-for-software-updates.md#BKMK_ManuallySwitchSUPs)을 참조하세요.

### <a name="restart-options-for-windows-10-clients-after-software-update-installation"></a>소프트웨어 업데이트 설치 후 Windows 10 클라이언트의 다시 시작 옵션
Configuration Manager를 사용하여 다시 시작이 필요한 소프트웨어 업데이트를 배포하고 컴퓨터에 설치한 경우 다시 시작 보류가 예약됩니다. 다시 시작 대화 상자도 표시됩니다. Configuration Manager 버전 1606부터 Configuration Manager 소프트웨어 업데이트에 대해 보류 중인 다시 시작이 있으면 언제든지 **업데이트 및 다시 시작** 및 **업데이트 및 종료** 옵션을 사용할 수 있습니다. 이러한 옵션은 Windows 10 컴퓨터의 Windows 전원 옵션에서 사용할 수 있습니다. 이러한 옵션 중 하나를 사용한 후 컴퓨터를 다시 시작하면 다시 시작 대화 상자가 표시되지 않습니다.

자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](../../../sum/plan-design/plan-for-software-updates.md#BKMK_RestartOptions)을 참조하세요.

### <a name="run-software-updates-compliance-scan-immediately-after-a-client-installs-software-updates-and-restarts"></a>클라이언트에서 소프트웨어 업데이트를 설치하고 다시 시작한 직후에 소프트웨어 업데이트 준수 검사 실행
이제 클라이언트에서 소프트웨어 업데이트를 설치하고 다시 시작한 직후에 준수 검사를 실행할 수 있습니다. 배포를 위해 이를 설정하려면 소프트웨어 업데이트 배포 마법사의 **사용자 환경** 페이지에서 **이 배포의 업데이트를 적용하기 위해 시스템을 다시 시작해야 하는 경우 다시 시작한 후 업데이트 배포 평가 주기 실행**을 선택합니다. 이렇게 하면 클라이언트가 다시 시작된 후 해당하는 추가 소프트웨어 업데이트를 확인한 다음, 동일한 유지 관리 기간 동안 해당 업데이트를 설치하여 규격을 준수할 수 있습니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates) 또는 [소프트웨어 업데이트 수동 배포](/sccm/sum/deploy-use/manually-deploy-software-updates)를 참조하세요.

## <a name="operating-system-deployment"></a>운영 체제 배포

### <a name="improvements-to-the-task-sequence-step-install-software-updates"></a>작업 순서 단계의 향상 기능: 소프트웨어 업데이트 설치
새로운 설정, **캐시된 검색 결과에서 소프트웨어 업데이트 평가**는 캐시된 검색 결과를 사용하는 대신 소프트웨어 업데이트에 대한 전체 검색을 수행하는 옵션을 제공합니다. 자세한 내용은 [System Center Configuration Manager의 작업 순서 단계](../../../osd/understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates)를 참조하세요.

또한 새 작업 순서 변수, **SMSTSSoftwareUpdateScanTimeout**을 사용할 수 있습니다. 이 변수를 사용하여 소프트웨어 업데이트 설치 작업 순서 단계를 진행하는 동안 소프트웨어 업데이트 검사 시간 제한을 제어할 수 있습니다. 기본값은 30분입니다. 자세한 내용은 [System Center Configuration Manager의 작업 순서 기본 제공 변수](../../../osd/understand/task-sequence-built-in-variables.md)를 참조하세요.

### <a name="osdpreservedriveletter-task-sequence-variable-has-been-deprecated"></a>OSDPreserveDriveLetter 작업 순서 변수는 사용되지 않음
OSDPreserveDriveLetter 작업 순서 변수는 사용되지 않습니다. Configuration Manager 버전 1606부터 Windows 설치 프로그램에서 기본적으로 운영 체제 배포 중 사용할 최상의 드라이브 문자(일반적으로 C:)를 결정합니다.

자세한 내용은 [System Center Configuration Manager의 작업 순서 기본 제공 변수](../../../osd/understand/task-sequence-built-in-variables.md)를 참조하세요.

### <a name="customize-the-ramdisk-tftp-window-size-for-pxe-enabled-distribution-points"></a>PXE 사용 배포 지점에 대한 RamDisk TFTP 창 크기 사용자 지정
이제 PXE 사용 배포 지점에 대한 RamDisk 창 크기를 사용자 지정할 수 있습니다. 네트워크를 사용자 지정한 경우 창 크기가 너무 커서 시간 초과 오류로 인해 부팅 이미지 다운로드가 실패할 수 있습니다. RamDisk TFTP(Trivial File Transfer Protocol) 창 크기 사용자 지정을 통해 PXE를 사용하여 특정 네트워크 요구 사항을 충족하는 경우 TFTP 트래픽을 최적화할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에서 운영 체제 배포를 위한 사이트 시스템 역할 준비](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP)를 참조하세요.

## <a name="compliance-settings"></a>호환성 설정

### <a name="smart-lock-setting-for-android-devices"></a>Android 디바이스에 대한 Smart Lock 설정
새 설정인 **스마트 잠금 및 기타 신뢰 에이전트 허용**이 Android 및 Samsung KNOX Standard 구성 항목에 추가되었습니다.

이 설정을 사용하면 호환 가능한 Android 디바이스에 대한 Smart Lock 기능을 제어할 수 있습니다. “신뢰 에이전트”라고도 하는 이 전화 기능을 통해 디바이스가 신뢰할 수 있는 위치에 있는 경우 디바이스 잠금 화면 암호를 사용하지 않도록 설정하거나 무시할 수 있습니다. 예를 들어 신뢰할 수 있는 위치는 디바이스가 특정 Bluetooth 디바이스에 연결된 경우 또는 NFC 태그에 가까이 있는 경우일 수 있습니다. 이 설정을 사용하면 최종 사용자가 스마트 잠금을 구성하지 않도록 방지할 수 있습니다.

자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Android 및 Samsung KNOX Standard 디바이스에 대한 구성 항목을 만드는 방법](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)을 참조하세요.

## <a name="device-configuration-and-protection"></a>디바이스 구성 및 보호

### <a name="product-name-changes"></a>제품 이름 변경

* Microsoft Passport for Work는 이제 **비즈니스용 Windows Hello**로 변경되었습니다.
* 엔터프라이즈 데이터 보호는 이제 **Windows Information Protection**로 변경되었습니다.

### <a name="deployment-of-windows-hello-for-business-passport-for-work"></a>비즈니스용 Windows Hello(Passport for Work) 배포

이제 Configuration Manager 클라이언트에서 관리되는 도메인에 가입된 Windows 10 디바이스에 비즈니스용 Windows Hello 정책을 배포할 수 있습니다.

Configuration Manager 콘솔이 이러한 변경 내용을 반영하도록 업데이트되었습니다.

### <a name="ios-activation-lock"></a>iOS 활성화 잠금
Configuration Manager를 사용하면 iOS 7.1 이상 디바이스용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금이 설정되면 사용자의 Apple ID와 암호를 입력해야 다음 작업을 수행할 수 있습니다.
* 나의 iPhone 찾기를 끕니다.
* 디바이스의 콘텐츠를 지웁니다.
* 디바이스를 다시 활성화합니다.

다음 두 가지 방법으로 Configuration Manager에서 활성화 잠금 관리를 지원할 수 있습니다.

- 감독된 디바이스에서 활성화 잠금을 사용합니다.
- 감독된 디바이스에서 활성화 잠금을 무시합니다.

자세한 내용은 [System Center Configuration Manager로 iOS 활성화 잠금 관리](../../../mdm/deploy-use/manage-ios-activation-lock.md)를 참조하세요.


### <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

Endpoint Protection은 Windows Defender ATP(Advanced Threat Protection)를 관리하고 모니터링하는 데 도움이 됩니다. Windows Defender ATP는 엔터프라이즈에서 네트워크에 대한 고급 공격을 검색하고 조사하고 대응할 수 있도록 하는 새로운 서비스입니다. Configuration Manager 정책은 Windows 10 버전 1607(빌드 14328) 이상을 실행하는 관리되는 컴퓨터를 등록하고 모니터링하는 데 도움이 됩니다.

자세한 내용은 [Windows Defender Advanced Threat Protection](../../../protect/deploy-use/windows-defender-advanced-threat-protection.md)을 참조하세요.

### <a name="device-categories"></a>디바이스 범주
Microsoft Intune에서 Configuration Manager를 사용하는 경우 디바이스 컬렉션에 디바이스를 자동으로 배치하는 데 사용할 수 있는 디바이스 범주를 만들 수 있습니다. 그런 다음 사용자는 Intune에 디바이스를 등록할 때 디바이스 범주를 선택해야 합니다. 또한 Configuration Manager 콘솔에서 디바이스의 범주를 변경할 수 있습니다.

자세한 내용은 [System Center Configuration Manager를 사용하여 컬렉션으로 디바이스를 자동으로 분류하는 방법](../../../core/clients/manage/collections/automatically-categorize-devices-into-collections.md)을 참조하세요.

### <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>IMEI 또는 iOS 일련 번호로 디바이스 미리 선언

해당 IMEI(International station Mobile Equipment Identity) 번호 또는 iOS 일련 번호를 가져와서 회사 소유의 디바이스를 식별할 수 있습니다. 디바이스 IMEI 번호를 포함한 쉼표로 구분된 값(.csv) 파일을 업로드하거나 디바이스 정보를 수동으로 입력할 수 있습니다. 가져온 정보에 따라 디바이스 목록에 "회사"로 등록된 디바이스의 소유권이 설정됩니다. 서비스에 액세스하는 각 사용자는 Intune 라이선스가 여전히 필요합니다.

자세한 내용은 [IMEI 또는 iOS 일련 번호로 디바이스 미리 선언](../../../mdm/deploy-use/predeclare-devices-with-hardware-id.md)을 참조하세요.

### <a name="on-premises-health-attestation-service-communication"></a>온-프레미스 상태 증명 서비스 통신

이제 인터넷 액세스가 없는 컴퓨터에서 DHA(디바이스 상태 증명)를 보고할 수 있도록 온-프레미스 인프라만 사용하여 Windows 10 PC에 대한 상태 증명 서비스 모니터링을 지원할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에 대한 상태 증명](../../../core/servers/manage/health-attestation.md#how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers)을 참조하세요.  

## <a name="remote-control"></a>원격 제어
원격 제어 세션에서 공유 클립보드의 콘텐츠를 전송하기 전에 사용자에게 파일 전송을 수락하거나 거부할 기회를 허용합니다. 사용자는 세션당 한 번만 사용 권한을 부여하면 되며, 조회자는 파일 전송을 진행할 수 있는 권한을 자신에게 부여할 수 없습니다. **관리** 작업 영역에서 이 새로운 설정을 찾을 수 있습니다. **클라이언트 설정**으로 이동하고 **기본 설정**에서 **원격 도구** 패널을 엽니다.
