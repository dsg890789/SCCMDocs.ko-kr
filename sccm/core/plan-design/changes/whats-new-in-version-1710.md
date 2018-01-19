---
title: "버전 1710의 새로운 기능 | Microsoft Docs"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager 버전 1710에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다."
ms.custom: na
ms.date: 1/08/2018
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc6c3e5f-b9e2-400e-9d9d-446ff93c520c
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: f944d4625e2e67a82098bf3b4373ea5f0ed70619
ms.sourcegitcommit: 9de3d74030b7c3313c34b5cbe2dbe6e18a48c043
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2018
---
# <a name="what39s-new-in-version-1710-of-system-center-configuration-manager"></a>System Center Configuration Manager 버전 1710의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 현재 분기의 업데이트 1710은 버전 1610, 1702 또는 1706을 실행하는 이전에 설치된 사이트에 대한 콘솔 내 업데이트로 제공됩니다.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용해야 합니다.  
>  다음에 대해 자세히 알아보세요.    
>   - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
>   - [사이트에 업데이트 설치](/sccm/core/servers/manage/updates)  
>   - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

다음 섹션에서는 Configuration Manager 버전 1710에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated features](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Version 1710 drops support for the following products:
-->


## <a name="site-infrastructure"></a>사이트 인프라

### <a name="updates-for-peer-cache-----sms500850---"></a>피어 캐시 업데이트 <!-- sms500850 -->
이 릴리스부터 피어 캐시는 더 이상 시험판 기능이 아닙니다.  이 릴리스에는 피어 캐시에 대한 다른 변경 내용이 없습니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)를 참조하세요.

### <a name="cloud-distribution-point-support-for-azure-government-cloud------sms491428---"></a>Azure Government 클라우드에 대한 클라우드 배포 지점 지원 <!-- sms491428 -->
이제 Azure Government 클라우드에서 [클라우드 기반 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)을 사용할 수 있습니다.   

### <a name="inventory-default-unit-revision----sms503697---"></a>인벤토리 기본 단위 수정 버전<!-- sms503697 -->
이제 장치에 GB(기가바이트), TB(테라바이트) 이상 크기의 하드 드라이브가 포함되므로 이 릴리스는 여러 보기에서 사용되는 기본 단위(SMS_Units)를 MB(메가바이트)에서 GB로 변경합니다. 예를 들어 v_gs_LogicalDisk.FreeSpace 값이 GB 단위를 보고합니다.


<!-- ## Migration  -->


## <a name="client-management"></a>클라이언트 관리

### <a name="co-management-for-windows-10-devices"></a>Windows 10 장치의 공동 관리    
<!-- 1350871 -->
이전 Windows 10 업데이트에서 이미 Windows 10 장치를 온-프레미스 AD(Active Directory)와 클라우드 기반 Azure AD에 동시에 조인할 수 있습니다(하이브리드 Azure AD). Configuration Manager 버전 1710부터 공동 관리에서는 이러한 향상된 기능을 통해 Configuration Manager 및 Intune을 모두 사용하여 Windows 10 버전 1709(Fall Creators Update라고도 함) 장치를 동시에 관리할 수 있습니다. 이것은 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다. 자세한 내용은 [Windows 10 장치의 공동 관리](/sccm/core/clients/manage/co-management-overview)를 참조하세요.

### <a name="restart-computers-from-the-configuration-manager-console-----1356283---"></a>Configuration Manager 콘솔에서 컴퓨터 다시 시작 <!-- 1356283 -->
이 릴리스부터 Configuration Manager 콘솔을 사용하여 다시 시작해야 하는 클라이언트 장치를 식별한 다음 클라이언트 알림 작업을 통해 해당 장치를 다시 시작할 수 있습니다.

[System Center Configuration Manager에서 클라이언트를 관리하는 방법](/sccm/core/clients/manage/manage-clients#restart-clients)을 참조하세요.


<!-- ## Compliance settings -->


## <a name="application-management"></a>응용 프로그램 관리
### <a name="improvements-for-run-scripts------1236459---"></a>향상된 스크립트 실행 기능 <!-- 1236459 -->
이 릴리스에서는 몇 가지 **스크립트 실행** 기능이 향상되어 관리되는 장치에서 실행되는 PowerShell 스크립트를 배포할 수 있습니다. 이 기능은 1706 버전에서 처음 소개되었습니다.

향상된 기능은 다음과 같습니다.
- 보안 범위를 사용하여 스크립트 실행을 사용할 수 있는 사용자 제어
- 실행되는 스크립트에 대한 실시간 모니터링
- 스크립트에 대한 매개 변수가 스크립트 만들기 마법사, 유효성 검사 지원에 표시되며 필수 또는 선택 사항으로 식별됩니다.

스크립트 실행에 대한 자세한 내용은 [스크립트 만들기 및 실행](../../../apps/deploy-use/create-deploy-scripts.md)을 참조하세요.

### <a name="new-mobile-application-management-policy-settings"></a>새 모바일 응용 프로그램 관리 정책 설정
<!-- 1324760 -->
모바일 응용 프로그램 관리 정책 설정에 다음과 같은 설정이 추가되었습니다.
- **연락처 동기화 사용 안 함:** 앱에서 장치의 네이티브 연락처 앱에 데이터를 저장하지 않도록 방지합니다.
- **인쇄 사용 안 함:** 앱에서 회사 또는 학교 데이터를 인쇄하지 않도록 방지합니다.

### <a name="software-center-no-longer-distorts-icons-larger-than-250x250"></a>소프트웨어 센터는 더 이상 250x250보다 큰 아이콘을 왜곡하지 않음  
<!-- 1356194 -->

이 릴리스를 사용하면 소프트웨어 센터는 더 이상 250x250보다 큰 아이콘을 왜곡하지 않습니다. 소프트웨어 센터는 그러한 아이콘이 흐리게 표시되도록 만듭니다. 이제 최대 512x512 픽셀 크기로 아이콘을 설정할 수 있으며 아이콘은 왜곡 없이 표시됩니다.

소프트웨어 센터에서 앱에 대한 아이콘을 추가하려면 [응용 프로그램 만들기](/sccm/apps/deploy-use/create-applications)를 참조하세요.

## <a name="operating-system-deployment"></a>운영 체제 배포
 > [!TIP]   
 > <!-- 1354281 -->
 > Windows 10, 버전 1709(Fall Creators Update라고도 함) 릴리스부터 Windows 미디어에는 여러 버전이 포함되어 있습니다. 운영 체제 업그레이드 패키지 또는 운영 체제 이미지를 사용하도록 작업 시퀀스를 구성할 때 [Configuration Manager가 사용할 수 있도록 지원되는 버전](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)을 선택해야 합니다.

### <a name="add-child-task-sequences-to-a-task-sequence"></a>작업 순서에 자식 작업 순서 추가
<!-- 1261338 -->

작업 순서 간에 부모/자식 관계를 만드는 다른 작업 순서를 실행하는 새 작업 순서 단계를 추가할 수 있습니다. 이러한 관계를 생성하면 다시 사용 가능한 모듈식 작업 순서를 더 만들 수 있습니다.  

자식 작업 순서에 대한 자세한 내용은 [자식 작업 순서](/sccm/osd/understand/task-sequence-steps#child-task-sequence)를 참조하세요.

## <a name="software-center-customization"></a>소프트웨어 센터 사용자 지정
<!-- 1351224 -->
엔터프라이즈 브랜딩 요소를 추가하고 소프트웨어 센터에서 탭의 표시 여부를 지정할 수 있습니다. 소프트웨어 센터 특정의 회사 이름을 추가하고 소프트웨어 센터 구성 색 테마, 회사 로고 및 클라이언트 장치에 대한 표시 탭을 설정할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)을 참조하세요.

## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="surface-driver-updates-----1098490---"></a>Surface 드라이버 업데이트 <!-- 1098490 -->
이 릴리스부터 Surface 드라이버 업데이트 관리는 더 이상 시험판 기능이 아닙니다.  


## <a name="reporting"></a>보고

### <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Windows 10 향상된 원격 분석을 Windows Analytics 장치 상태와 관련된 데이터만 전송하도록 제한
<!-- 1356148 -->

이제 Windows 10 원격 분석 데이터 수집 수준을 **고급(제한적)**으로 설정할 수 있습니다. 이 설정을 사용하면 Windows 10 버전 1709 이상을 사용하여 **고급** 원격 분석 수준의 모든 데이터를 보고하는 장치가 없는 환경에서 장치에 대해 조치 가능한 통찰력을 얻을 수 있습니다.

자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)섹션을 참조하세요.

<!-- ## Inventory  -->


## <a name="mobile-device-management"></a>모바일 장치 관리

### <a name="actions-for-non-compliance"></a>비준수에 대한 작업 
<!--1321366 -->    
이제 규정을 준수하지 않는 장치에 적용되는 작업을 시간 순으로 구성할 수 있습니다. 예를 들어 전자 메일을 통해 사용자에게 비준수 장치를 알리거나 해당 장치를 비준수 장치로 표시할 수 있습니다. 자세한 내용은 [비준수에 대한 작업 설정](/sccm/mdm/deploy-use/actions-for-noncompliance)을 참조하세요.

### <a name="windows-10-arm64-device-support"></a>Windows 10 ARM64 장치 지원
<!-- 1355000 -->

하이브리드 MDM(모바일 장치 관리) 시나리오는 이러한 장치를 사용할 수 있을 때 Windows 10을 실행하는 ARM64 장치에서 지원됩니다.

이러한 시나리오는 다음과 같습니다.

- [장치 등록](../../../mdm/deploy-use/enroll-hybrid-windows.md)
- [원격 전체 및 선택적 초기화 작업 수행](../../../mdm/deploy-use/wipe-lock-reset-devices.md)
- [구성 항목 및 기준을 통해 설정 관리](../../../mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [규정 준수 정책](../../../mdm/deploy-use/device-compliance-policies.md) 및 [조건부 액세스](../../../protect/deploy-use/manage-access-to-services.md)
- 회사 리소스에 대한 액세스는 다음 항목을 통해 관리합니다.
   - [인증서 프로필](../../../mdm/deploy-use/create-pfx-certificate-profiles.md)
   - [VPN 프로필](../../../mdm/deploy-use/create-vpn-profiles.md)
   - [Wi-Fi 프로필](../../../mdm/deploy-use/create-wifi-profiles.md)
   - [메일 프로필](../../../mdm/deploy-use/create-exchange-activesync-profiles.md)
- [비즈니스용 Windows Hello 정책 구성](../../../mdm/deploy-use/windows-hello-for-business-settings.md)
- [응용 프로그램 관리](../../../mdm/deploy-use/management-tasks-applications.md)

> [!NOTE]
> 여러 아키텍처용으로 빌드된 .appxbundle 응용 프로그램을 배포하면 이들 장치에서 작동하지 않을 수 있으며, 현재 이 시나리오는 지원되지 않습니다.

### <a name="improved-vpn-profile-experience-in-configuration-manager-console"></a>Configuration Manager 콘솔의 VPN 프로필 환경 개선 
<!-- 1318232 -->

이 릴리스에서는 VPN 프로필 마법사 및 속성 페이지를 업데이트하여 선택한 플랫폼에 적절한 설정을 표시했습니다.


- 각 플랫폼에는 고유한 워크플로가 있습니다. 즉, 새 VPN 프로필에는 플랫폼에서 지원되는 설정만 포함됩니다.
- **지원되는 플랫폼** 페이지는 이제 **일반** 페이지 뒤에 표시됩니다.  이제 속성 값을 설정하기 전에 플랫폼을 선택합니다.
- 플랫폼이 **Android**, **Android for Work** 또는 **Windows Phone 8.1**로 설정되면 **지원되는 플랫폼** 페이지는 필요하지 않으므로 표시되지 않습니다.
- Configuration Manager 클라이언트 기반 워크플로는 하이브리드 모바일 장치(MDM) 클라이언트 기반 Windows 10 워크플로와 결합되었습니다. 모두 동일한 설정을 지원합니다.
- 각 플랫폼 워크플로에는 해당 워크플로에 대한 적절한 설정만이 포함됩니다.  예를 들어, Android 워크플로에는 Android에 적절한 설정이 포함되고 iOS 또는 Windows 10 Mobile에 적절한 설정은 Android 워크플로에 더 이상 표시되지 않습니다.
- 자동 VPN 페이지는 사용되지 않으며 제거되었습니다.

이러한 변경 내용은 새 VPN 프로필에 적용됩니다.  

호환성 위험을 최소화하기 위해 기존 VPN 프로필은 변경되지 않습니다.  기존 프로필을 편집하는 경우 프로필을 만들 때와 마찬가지로 설정이 표시됩니다.  

자세한 내용은 [System Center Configuration Manager의 모바일 장치에 대한 VPN 프로필](../../../mdm/deploy-use/create-vpn-profiles.md)을 참조하세요.

### <a name="limited-support-for-cryptography-next-generation-cng-certificates----1356191---"></a>CNG(Cryptography: Next Generation) 인증서에 대한 제한된 지원 <!-- 1356191 -->

Configuration Manager는 CNG(Cryptography: Next Generation) 인증서를 제한적으로 지원합니다. Configuration Manager 클라이언트는 CNG KSP(키 저장소 공급자)의 개인 키와 함께 PKI 클라이언트 인증 인증서를 사용할 수 있습니다. Configuration Manager 클라이언트는 KSP 지원을 통해 PKI 클라이언트 인증 인증서용 TPM KSP와 같은 하드웨어 기반 개인 키를 지원합니다.

자세한 내용은 [CNG 인증서 개요](../network/cng-certificates-overview.md)를 참조하세요.

## <a name="protect-devices"></a>장치 보호

### <a name="create-and-deploy-exploit-guard-policies"></a>Exploit Guard 정책 만들기 및 배포
<!-- 1355468 -->

공격에 대한 취약성 감소, 제어된 폴더 액세스, 악용 방지 및 네트워크 보호를 포함한 네 가지 Windows Defender Exploit Guard 구성 요소를 모두 관리하는 [정책을 만들고 배포](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy)할 수 있습니다.

### <a name="create-and-deploy-windows-defender-application-guard-policy"></a>Windows Defender Application Guard 정책 만들기 및 배포
<!-- 1351960 -->

Configuration Manager 엔드포인트 보호를 사용하여 [Windows Defender Application Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy) 정책을 만들고 배포할 수 있습니다.

### <a name="device-guard-policy-changes"></a>Device Guard 정책 변경
<!-- 1355092 -->
Device Guard 정책과 관련하여 다음 세 가지 항목이 변경되었습니다.

- Device Guard 정책의 이름이 Windows Defender 응용 프로그램 제어 정책으로 바뀌었습니다. 예를 들어 **Device Guard 정책 만들기 마법사**의 이름이 이제는 **Windows Defender 응용 프로그램 제어 정책 만들기 마법사**입니다.
- Windows용 Fall Creators Update 버전 1709를 사용하는 장치는 Windows Defender 응용 프로그램 제어 정책을 적용하기 위해 다시 시작할 필요가 없습니다. 다시 시작은 여전히 기본값이지만 [다시 시작을 해제](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)할 수 있습니다.
- Intelligent Security Graph에서 신뢰할 수 있는 [소프트웨어를 자동으로 실행하도록 장치를 설정](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)할 수 있습니다.





## <a name="next-steps"></a>다음 단계
이 버전을 설치할 준비가 되었으면 [Configuration Manager 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.
