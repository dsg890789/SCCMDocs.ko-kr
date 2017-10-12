---
title: Configuration Manager Technical Preview | Microsoft Docs
description: "System Center Configuration Manager에서 새로운 기능을 테스트 시험해 볼 수 있는 기술 미리 보기 릴리스에 대해 알아봅니다."
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.reviewer: nab
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: "157"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 429e20185bd23519f78c37ded39f2638d0c80ced
ms.sourcegitcommit: 8ac9c2c9ba1fdcbb7cc8d5be898586865fcf67c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2017
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>System Center Configuration Manager Technical Preview

*적용 대상: System Center Configuration Manager(Technical Preview)*

**System Center Configuration Manager Technical Preview 시작**. 이 항목에서는 현재 작업 중인 새로운 기능을 소개하는 개발 중인 미리 보기 릴리스에 대해 자세히 다룹니다. 각 버전의 기술 미리 보기에서는, 기술 미리 보기 버전이 사용 가능한 시기를 기준으로 현재 분기의 System Center Configuration Manager에 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능이 결과적으로 현재 분기 버전의 업데이트에 포함될 수도 있지만, 기능을 완료하고 추가하기 전에 사용자가 사용해 보고 의견을 제공하는 기회를 갖길 원합니다.  

 이 항목은 기술 미리 보기이므로 세부 정보 및 기능은 변경될 수 있습니다.  

 이 항목에서는 기술 미리 보기의 모든 버전에 적용되며, 2017년 1월의 버전 1701처럼 기능이 가장 먼저 제공되는 기술 미리 보기 버전과 함께 새로운 각 기능을 설명합니다. 이러한 기능에 대한 세부 정보는 각 미리 보기 버전만을 다룬 별도 항목에서 자세히 설명합니다.  

 현재 분기의 Configuration Manager에서 제공하는 새로운 기능에 대한 자세한 내용은 [System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012)을 참조하세요.



##  <a name="bkmk_reqs"></a> Technical Preview의 요구 사항 및 제한  

> [!IMPORTANT]     
>  기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다.  Microsoft에서 지원 서비스를 제공하지 않고, 특정 기능은 미리 보기 소프트웨어에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 Preview 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

 대부분의 제품 필수 조건에 대한 자세한 내용은 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md)의 정보를 참조하세요. 기술 미리 보기 릴리스에는 다음과 같은 예외가 적용됩니다.  

-   각 설치는 90일 동안 활성 상태로 유지된 후에 비활성화됩니다.  

-   지원되는 언어는 영어뿐입니다.


-   다음 설치 플래그(스위치)만 지원됩니다.  

    -   **/silent**  
    -   **/testdbupgrade**    


-   기본적으로 Technical Preview를 사용할 경우 서비스 연결 지점은 설치 시 온라인 모드로 설정되며 오프라인 모드로 변경할 수 없습니다.

-   해당되는 추가 제한 사항 또는 요구 사항이 특정 버전의 각 Technical Preview에 대한 세부 정보에 포함되어 있습니다.  

-   이 미리 보기 빌드에서/빌드로 마이그레이션할 수는 없습니다.  

-   이 미리 보기 빌드로 업그레이드할 수는 없습니다.  

-   이 미리 보기 빌드에서 프로덕션 빌드(현재 분기)로 업그레이드할 수 없습니다. 그러나 미리 보기 버전용 업데이트를 사용할 수 있는 경우 Configuration Manager 콘솔의 **업데이트 및 서비스** 노드에서 해당 업데이트를 찾아 설치할 수 있습니다. 콘솔 내 업그레이드 프로세스에 대한 비디오를 보려면 youtube.com에서 [ConfigMgr 업데이트 패키지 설치](https://www.youtube.com/embed/KBd_EGFbUT8) (영문)를 참조하세요.  
-   독립 실행형 기본 사이트만 지원됩니다. 중앙 관리 사이트, 여러 기본 사이트 또는 보조 사이트는 지원되지 않습니다.  

다음 제품 및 기술은 이 Configuration Manager 분기에서 지원됩니다. 그러나 이 내용에 포함되었다고 해서 개별 지원 주기가 끝난 제품 또는 버전의 지원 연장을 의미하지는 않습니다. 즉, 지원 주기가 끝난 제품은 Configuration Manager에서 사용할 수 없습니다. Microsoft 지원 주기에 대한 자세한 내용은 [Microsoft 지원 주기](http://go.microsoft.com/fwlink/p/?LinkId=208270) 웹 사이트를 참조하세요.  

-   다음 SQL Server 버전만 지원됩니다.  

    -   SQL Server 2016(서비스 팩 없음 버전 이상)
    -   SQL Server 2014(서비스 팩 1 이상)
    -   SQL Server 2012(서비스 팩 3 이상)


-   사이트는 최대 10개 클라이언트를 지원하며, 이러한 클라이언트는 다음 운영 체제 중 하나를 실행해야 합니다.  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> 기술 미리 보기 설치 및 업데이트  
 System Center Configuration Manager Technical Preview는 현재 릴리스의 System Center Configuration Manager와 다릅니다.  

 기술 미리 보기를 사용하려면 먼저 기술 미리 보기 빌드의 **기준선 버전** 을 설치해야 합니다. 기준선 버전을 설치한 후 **콘솔 내 업데이트** 를 사용하여 최근의 미리 보기 버전으로 설치를 업데이트할 수 있습니다.     일반적으로 새 버전의 기술 미리 보기는 매달 사용할 수 있습니다.

세 가지 후속 릴리스를 사용할 수 있을 때까지 각 미리 보기 릴리스가 지원됩니다. 즉 버전 1708이 출시되면 버전 1704는 더 이상 지원되지 않지만 버전 1705, 1706 및 1707은 계속 지원됩니다. 기준 버전(예: 버전 1703)이 지원되지 않는 경우에도 해당 설치를 지원되는 버전으로 업데이트하는 한 새 기준 버전을 사용할 수 있을 때까지 새 기술 미리 보기 사이트를 설치할 수 있습니다. 업데이트할 때 콘솔에 사용 가능한 최신 버전이 표시되지 않으면 제공된 최신 버전으로 업데이트한 다음 최신 버전의 Technical Preview를 설치할 수 있을 때까지 해당 프로세스를 반복합니다.

> [!TIP]  
>  기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다.    기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하거나 현재 분기 릴리스의 업데이트를 받을 수 있는 옵션이 없습니다.  

**기술 미리 보기의 활성 기준선 버전:**  
릴리스 후 최대 1년 동안 기준 버전을 설치할 수 있습니다. 그러나 새 Technical Preview 사이트를 설치할 경우 사용 가능한 최신 기준선 버전을 사용하는 것이 좋습니다.
-  **Technical Preview 1703** - Configuration Manager Technical Preview 1703은 Configuration Manager Technical Preview의 콘솔 내 업데이트와 [TechNet Evaluation Center 웹 사이트에서 사용할 수 있는](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 새 기준 버전으로 제공됩니다.

<!-- out of support. Use baseline 1703
-  **Technical Preview 1610** - The Configuration Manager Technical Preview 1610 was available as both an in-console update for the Configuration Manager Technical Preview, and as a baseline version. If you have media for installing 1610, we recommend you download version 1703 and install that version instead.
-->



##  <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  
 기술 미리 보기에 대한 여러분의 의견을 보내 주시기 바랍니다. 각 미리 보기의 기능에 대한 의견을 제출하려면 링크를 클릭하여 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) 페이지에 있는 사용자 의견 양식으로 이동하세요.  

 새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 전송하고 다른 사용자들이 전송한 아이디어에 대해 투표를 하려면 [사용자 의견 페이지를 방문](http://configurationmanager.uservoice.com)하세요.  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> 가장 최근의 Technical Preview에 포함된 기능  
 다음에는 각 Configuration Manager 기술 미리 보기 릴리스에 포함된 기능이 나와 있습니다.  기술 미리 보기의 특정 버전에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로, System Center Configuration Manager 릴리스(현재 분기)에 추가된 기능은 후속 기술 미리 보기에서도 계속 사용할 수 있습니다.  각 미리 보기 버전에 대한 콘텐츠를 클릭하여 특정 기능에 대한 자세한 내용을 알아볼 수 있습니다.  

 |기능 |기술 미리 보기 버전 |현재 분기 버전|  
 |----------------|---------------------|--------------------|
 |Configuration Manager 콘솔에서 개선된 VPN 프로필<!-- 1313282 --> | [Tech Preview 1709](capabilities-in-technical-preview-1709.md) |![추가되지 않음](media/Red_X.gif)    |
 |Windows 10 장치의 공동 관리|[Tech Preview 1709](capabilities-in-technical-preview-1709.md#co-management-for-windows-10-devices)|![추가되지 않음](media/Red_X.gif)    |


## <a name="capabilities-delivered-in-previous-technical-previews"></a>이전 Technical Preview에 포함된 기능
 Technical Preview 릴리스의 모든 기능을 현재 분기의 지원되는 최소 버전으로 사용할 수 있는 경우 해당 미리 보기 버전에 대한 세부 정보는 다음 표에서 제거됩니다.  

 |기능 |기술 미리 보기 버전 |현재 분기 버전|  
 |----------------|---------------------|--------------------|
 |Configuration Manager에서 PowerShell 스크립트를 배포할 때 매개 변수를 지정하도록 향상된 기능 <!-- 1236459 -->|[기술 미리 보기 1708](capabilities-in-technical-preview-1708.md#improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)|![추가되지 않음](media/Red_X.gif)|
 |관리 정보 <!-- 1353967 --> |[기술 미리 보기 1708](capabilities-in-technical-preview-1708.md#management-insights)|![추가되지 않음](media/Red_X.gif)|
 |Configuration Manager 콘솔에서 컴퓨터 다시 시작 <!-- 1356283 --> |[기술 미리 보기 1708](capabilities-in-technical-preview-1708.md#restart-computers-from-the-configuration-manager-console)|![추가되지 않음](media/Red_X.gif)|
 |소프트웨어 센터 사용자 지정 <!-- 1351224 --> |[기술 미리 보기 1708](capabilities-in-technical-preview-1708.md#software-center-customization)|![추가되지 않음](media/Red_X.gif)|
|Windows 10 및 Office 365에 대한 고속 설치 파일을 위한 클라이언트 피어 캐시 지원|[Tech Preview 1707](capabilities-in-technical-preview-1707.md#client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365)|![추가되지 않음](media/Red_X.gif)|
 |Surface 장치 대시보드|[Tech Preview 1707](capabilities-in-technical-preview-1707.md#surface-device-dashboard)|![추가되지 않음](media/Red_X.gif)|
 |Windows Defender Application Guard 정책 구성 및 배포|[Tech Preview 1707](capabilities-in-technical-preview-1707.md#configure-and-deploy-windows-defender-application-guard-policies)|![추가되지 않음](media/Red_X.gif)|
 |Configuration Manager에서 PowerShell 스크립트를 배포할 때 매개 변수 추가|[Tech Preview 1707](capabilities-in-technical-preview-1707.md#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)|![추가되지 않음](media/Red_X.gif)|
 |새 모바일 응용 프로그램 관리 정책 설정|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#new-mobile-application-management-policy-settings)|![추가되지 않음](media/Red_X.gif)|
 |소프트웨어 업데이트 지점에 대한 향상된 경계 그룹|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#improved-boundary-groups-for-software-update-points)|[버전 1706](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)|
 |사이트 서버 역할 고가용성|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |![추가되지 않음](media/Red_X.gif)|
 |특정 파일 및 폴더에 대한 트러스트를 Device Guard 정책에 포함|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#include-trust-for-specific-files-and-folders-in-a-device-guard-policy)|[버전 1706](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|
 |작업 순서 진행률 숨기기|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#hide-task-sequence-progress)|![추가되지 않음](media/Red_X.gif)|
 |설치 콘텐츠 및 제거 콘텐츠에 대해 다른 콘텐츠 위치 지정|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#specify-a-different-content-location-for-install-content-and-uninstall-content)|[버전 1706](/sccm/core/get-started/capabilities-in-technical-preview-1706#hide-task-sequence-progress)|
 |향상된 접근성 기능 |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#accessibility-improvements)|[버전 1706](/sccm/core/understand/accessibility-features)|
 |업그레이드 준비 상태에 대한 Azure 서비스 마법사 지원 |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#changes-to-the-azure-services-wizard-to-support-upgrade-readiness)|[버전 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |클라우드 서비스에 대한 새 클라이언트 설정|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#new-client-settings-for-cloud-services)|[버전 1706](/sccm/core/clients/deploy/deploy-clients-cmg-azure)|
 |Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#create-and-run-powershell-scripts-from-the-configuration-manager-console)|[버전 1706](/sccm/apps/deploy-use/create-deploy-scripts)|
 |IPv6에 대한 PXE 네트워크 부팅 지원 |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|![추가되지 않음](media/Red_X.gif)|
 |Microsoft Surface 드라이버 업데이트 관리 |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#manage-microsoft-surface-driver-updates)|[버전 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#manage-microsoft-surface-driver-updates)|
 |비즈니스용 Windows 업데이트 지연 정책 구성 |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#configure-windows-update-for-business-deferral-policies)|[버전 1706](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies)|
 |iOS 등록 제한|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#android-and-ios-enrollment-restrictions)|[버전 1706](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac#configure-enrollment-restrictions)|
 |Android 등록 제한|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#android-and-ios-enrollment-restrictions)|[버전 1706](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)|
 |복사-붙여넣기에 대한 Android for Work 응용 프로그램 관리 정책|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#android-for-work-application-management-policy-for-copy-paste)|[버전 1706](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client#android-for-work-configuration-item-settings-reference)|
 |새 Windows 구성 항목 설정|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#new-windows-configuration-item-settings)|[버전 1706](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |새 장치 준수 정책 규칙|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#new-device-compliance-policy-rules)|[버전 1706](/sccm/mdm/deploy-use/create-compliance-policy)|
 |조건부 액세스의 준수 정책에 대한 장치 상태 증명 평가|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#device-health-attestation-assessment-for-compliance-policies-for-conditional-access)|![추가되지 않음](media/Red_X.gif)|
 |Entrust 인증 기관에 대한 지원|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#support-for-entrust-certification-authorities)|[버전 1706](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |macOS VPN 프로필에 대한 Cisco(IPSec) 지원|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#cisco-ipsec-support-for-macos-vpn-profiles)|[버전 1706](/sccm/protect/deploy-use/vpn-profiles)|
 |Azure AD 및 클라우드 관리에 대한 새로운 기능|[Tech Preview 1705](capabilities-in-technical-preview-1705.md#new-capabilities-for-azure-ad-and-cloud-management)|[버전 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#azure-ad-integration-with-configuration-manager)|
 |Windows Defender Application Guard 정책 구성 및 배포|[Tech Preview 1705](capabilities-in-technical-preview-1705.md#configure-and-deploy-windows-defender-application-guard-policies)|![추가되지 않음](media/Red_X.gif)|
 |업데이트 다시 설정 도구  |[Tech Preview 1705](capabilities-in-technical-preview-1705.md#update-reset-tool)|[버전 1706](/sccm/core/servers/manage/update-reset-tool)|
 |높은 DPI 콘솔 지원  |[Tech Preview 1705](capabilities-in-technical-preview-1705.md#high-dpi-console-support)|[버전 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#high-dpi-console-support)|
 |피어 캐시 개선  |[Tech Preview 1705](capabilities-in-technical-preview-1705.md#peer-cache-improvements) |[버전 1706](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache)|
 |SQL Server Always On 가용성 그룹에 대한 향상된 기능 |[Tech Preview 1705](capabilities-in-technical-preview-1705.md#improvements-for-sql-server-always-on-availability-groups) |[버전 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#improvements-for-sql-server-always-on-availability-groups)|
 |Office 365 업데이트에 대한 향상된 사용자 알림|[Tech Preview 1705](capabilities-in-technical-preview-1705.md#improved-user-notifications-for-office-365-updates) |[버전 1706](/sccm/sum/deploy-use/manage-office-365-proplus-updates#restart-behavior-and-client-notifications-for-office-365-updates)|
 |Azure 서비스 마법사를 사용하여 OMS에 대한 연결 구성|[Tech Preview 1705](capabilities-in-technical-preview-1705.md#use-azure-services-wizard-to-configure-a-connection-to-oms) |[버전 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |앱 구성 정책을 사용하여 Android 앱 구성  |[Tech Preview 1704](capabilities-in-technical-preview-1704.md#configure-android-apps-with-app-configuration-policies)|![추가되지 않음](media/Red_X.gif)|
 |하드웨어 인벤토리를 통해 보안 부팅 정보 수집 |[Tech Preview 1704](capabilities-in-technical-preview-1704.md#hardware-inventory-collects-secure-boot-information)|[버전 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#hardware-inventory-collects-secure-boot-information)|
 |작업 순서에 자식 작업 순서 추가|[Tech Preview 1704](capabilities-in-technical-preview-1704.md#add-child-task-sequences-to-a-task-sequence)|![추가되지 않음](media/Red_X.gif)|
 |현재 Windows PE 버전을 사용하여 부팅 이미지 다시 로드 |[Tech Preview 1704](capabilities-in-technical-preview-1704.md#reload-boot-images-with-current-windows-pe-version)|[버전 1706](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image)|
 |운영 체제 배포 향상 <!-- This item does not track to be added to the Current Branch. It is covered by various other incremental work. --> |[Tech Preview 1704](capabilities-in-technical-preview-1704.md#improvements-to-operating-system-deployment)|![추가되지 않음](media/Red_X.gif)|
 |장치 컬렉션에 대량 구매한 iOS 앱 배포|[Tech Preview 1703](capabilities-in-technical-preview-1703.md#deploy-volume-purchased-ios-apps-to-device-collections)|[버전 1702](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)|
 |소프트웨어 센터의 응용 프로그램에 대한 직접 링크|[Tech Preview 1703](capabilities-in-technical-preview-1703.md#direct-links-to-applications-in-software-center)|[버전 1706](/sccm/apps/deploy-use/share-applications)
 |Configuration Manager Windows 클라이언트 컴퓨터에 대한 PFX 인증서|[Tech Preview 1703](capabilities-in-technical-preview-1703.md#pfx-certificates-for-configuration-manager-windows-client-computers)|[버전 1706](/sccm/protect/deploy-use/create-certificate-profiles)|
 |Azure 서비스 구성 마법사|[Tech Preview 1703](capabilities-in-technical-preview-1703.md#configure-azure-services-wizard)|[버전 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |운영 체제 업그레이드 작업 순서에서 BIOS에서 UEFI로 변환| [Tech Preview 1703](capabilities-in-technical-preview-1703.md#convert-from-bios-to-uefi-during-an-in-place-upgrade) |[버전 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)|
 |축소 가능한 작업 순서 그룹| [Tech Preview 1703](capabilities-in-technical-preview-1703.md#collapsible-task-sequence-groups) |[버전 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#collapsible-task-sequence-groups)|
 |업그레이드 준비를 위해 Windows Analytics를 구성하기 위한 클라이언트 설정 | [Tech Preview 1703](capabilities-in-technical-preview-1703.md#client-settings-to-configure-windows-analytics-for-upgrade-readiness) |[버전 1706](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics)|
 |iOS 장치에 대한 새 준수 설정|[Tech Preview 1702](capabilities-in-technical-preview-1702.md#new-compliance-settings-for-ios-devices)|[버전 1702](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)|
 |S/MIME을 지원하는 PFX 인증서 만들기|[Tech Preview 1702](capabilities-in-technical-preview-1702.md#create-pfx-certificates-with-s-mime-support)|[버전 1706](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |응용 프로그램을 설치하기 전에 실행 중인 실행 파일 확인|[Tech Preview 1702](capabilities-in-technical-preview-1702.md#check-for-running-executable-files-before-installing-an-application)|[버전 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Configuration Manager 콘솔에서 피드백 보내기 | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#send-feedback-from-the-configuration-manager-console)    |[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#send-feedback-from-the-configuration-managercconsole)  |
 |업데이트 및 서비스의 변경 내용  | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#changes-for-updates-and-servicing)  |[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#changes-for-updates-and-servicing) |
 |피어 캐시 개선  | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#peer-cache-improvements) |[버전 1702](/sccm/core/plan-design/hierarchy/client-peer-cache)|
 |Azure Active Directory 사용 <!-- This item does not track to be added to the Current Branch. It is covered by various other incremental work. --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |![추가되지 않음](media/Red_X.gif)|
 |조건부 액세스 장치 준수 정책 개선 | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#conditional-access-device-compliance-policy-improvements) |[버전 1702](/sccm/mdm/deploy-use/create-compliance-policy)|
 |맬웨어 방지 클라이언트 버전 경고 | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert) |[버전 1702](/sccm/protect/deploy-use/endpoint-configure-alerts?branch=live#alert-for-outdated-malware-client)|
 |Windows Update for Business 업데이트에 대한 준수 평가 | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |![추가되지 않음](media/Red_X.gif)|
 |강력한 작업 순서에 대한 소프트웨어 센터 설정 및 알림 메시지 개선|[Tech Preview 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert)|[버전 1702](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)|
 |Android for Work 지원| [Tech Preview 1702](capabilities-in-technical-preview-1702.md#android-for-work-support) |[버전 1702](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-for-work-enrollment)|
 |소프트웨어 업데이트 지점에 대한 향상된 경계 그룹 | [Tech Preview 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |[버전 1702](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)  |
 |하드웨어 인벤토리를 통해 UEFI 정보 수집 | [Tech Preview 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|[버전 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#hardware-inventory-collects-uefi-information) |
 |운영 체제 배포 향상| [Tech Preview 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment) |
 |클라우드 기반 배포 지점에서 소프트웨어 업데이트 호스트| [Tech Preview 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|[버전 1702](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#plan-to-use-a-cloud-based-distribution-point) |
 |관리 지점을 통해 장치 상태 증명 데이터의 유효성 검사| [Tech Preview 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)| [버전 1702](/sccm/core/servers/manage/health-attestation) |
 |Microsoft Azure Government 클라우드용 OMS 커넥터 |[Tech Preview 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |[버전 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig) |
 |Android 및 iOS 버전은 만들기 마법사에서 대상 지정이 가능하지 않음 |[Tech Preview 1701](capabilities-in-technical-preview-1701.md#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |
 |OData 끝점 데이터 액세스 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![추가되지 않음](media/Red_X.gif)|
 |데이터 웨어하우스 서비스 지점 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|[버전 1702](/sccm/core/servers/manage/data-warehouse)|
 |콘텐츠 라이브러리 정리 도구 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|[버전 1702](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) |
 |콘솔 내 검색의 향상된 기능 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-for-in-console-search)|
 |지정한 프로그램이 실행되는 경우 응용 프로그램 설치 차단|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|[버전 1702](/sccm/apps/deploy-use/deploy-applications)|
 |최종 사용자에 대한 새 비즈니스용 Windows Hello 알림|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#new-windows-hello-for-business-notification-for-end-users)|
 |Configuration Manager의 비즈니스용 Windows 스토어 지원|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|[버전 1702](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |작업 순서가 실패할 경우 이전 페이지로 돌아가기|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|[버전 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment)|
 |Windows 10 업데이트에 대한 빠른 설치 파일 지원|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|[버전 1702](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)|
 |Azure Active Directory 등록|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|[버전 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |장치 등록에 대한 다단계 인증 구성 변경|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![추가되지 않음](media/Red_X.gif)|
 |배포 및 작업 순서에 대한 콘텐츠 사전 캐시 |[Tech Preview 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|[버전 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
 |Windows Defender 구성 설정|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[버전 1610](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |관리자 콘솔에서 정책 동기화 요청|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[버전 1610](/sccm/mdm/deploy-use/sync-intune-device)|
 |모든 회사 소유 장치 노드에 대한 추가 보안 역할 지원|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[버전 1610](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Windows 10 VPN 프로필에 대한 조건부 액세스|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[버전 1610](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |자동 배포 규칙의 콘텐츠 크기에 따라 필터링|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[버전 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |필수 소프트웨어 대화 상자에 대한 향상된 기능|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[버전 1610](/sccm/apps/deploy-use/deploy-applications)|
 |이전에 승인된 응용 프로그램 요청 거부|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[버전 1610](/sccm/apps/deploy-use/deploy-applications)|
 |자동 업그레이드에서 클라이언트 제외|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[버전 1610](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Endpoint Protection 개선|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|[버전 1610](/sccm/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)|
 |등록된 장치 수 증가|[Tech Preview 1609](/sccm/mdm/deploy-use/enable-platform-enrollment)|[버전 1610](/sccm/mdm/deploy-use/enable-platform-enrollment)|
 |추가 Apple DEP 설정|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[버전 1610](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Configuration Manager와 비즈니스용 Windows 스토어 통합 향상|[Tech Preview 1609](capabilities-in-technical-preview-1609.md)|[버전 1610](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |구성 항목의 새 준수 설정|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[버전 1610](/sccm/compliance/deploy-use/create-configuration-items)|
 |Upgrade Analytics 통합|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[버전 1610](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |Windows 10 VPN 하이브리드 프로필에 대한 네이티브 연결 형식|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![추가되지 않음](media/Red_X.gif)|
 |경계 그룹의 향상된 기능|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[버전 1610](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Office 365 클라이언트 관리 대시보드|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[버전 1610](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |클라이언트에 Office 365 앱 배포|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|[버전 1702](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)|
 |BIOS-UEFI 변환의 향상된 기능|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[버전 1610](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Intune 준수 차트|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[버전 1610](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|


 <!--  TP 1608 and earlier have aged out of support. Features from these previews are either in the minimum supported Current Branch version, or are not scheduled for inclusion.
 |Improvements to the Prepare ConfigMgr Client for Capture task sequence step|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[Version 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |Improvements to Software Center|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[Version 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Improvements to Asset Intelligence|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|N/A|
 |Remote control keyboard translation|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)|[Version 1702](/sccm/core/clients/manage/remote-control/configuring-remote-control#enable-keyboard-translation)|
 |Improvements to the Windows 10 Edition Upgrade Policy|[Tech Preview 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[Version 1610](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |Customizable Branding for Software Center Dialogs|[Tech Preview 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|[Version 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#customizable-branding-for-software-center-dialogs)|  
 |Multiple device management points for On-premises Mobile Device Management|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |Automatically categorize devices into collections|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[Version 1606](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |Enforcement grace period for required application and software update deployments|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[Version 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Using Configuration Manager as a Managed Installer with Device Guard|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|[Version 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|
 |Cloud management gateway (formerly Cloud Proxy Service)|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [Version 1610](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Manage the Office 365 client agent in Configuration Manager|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |The OSDPreserveDriveLetter task sequence variable has been deprecated|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[Version 1606](/sccm/osd/understand/task-sequence-built-in-variables) |
 |Changes for the Updates and Servicing Node|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Per-app VPN for Windows 10 devices|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[Version 1606](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |Improvements to the Install software updates task sequence|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |Improvements to the Prepare ConfigMgr Client for Capture task sequence step |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[Version 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |Grace period for required application deployments |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|N/A|  
 |New experience for remote device actions |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Windows Store for Business apps |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[Version 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |General improvements for volume-purchased apps|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Enterprise Data Protection (EDP)|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |End users can install apps from the Company Portal |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|N/A|  
 |New tabs for Updates and Operating Systems in Software Center|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[Version 1606 ](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Service a server group |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[Version 1606](/sccm/sum/deploy-use/service-a-server-group)|   
 |Support for Windows Defender Advanced Threat Protection service |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[Version 1606](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |New restart options for Windows 10 clients after software update installation|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[Version 1606](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |On-premises Device Health Attestation |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[Version 1606](/sccm/core/servers/manage/health-attestation)|  
 |Pre-declare corporate-owned devices with IMEI or iOS serial number|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[Version 1606](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  
 |Manage volume-purchased apps from the Windows Store for Business| [Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[Version 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Improvements to Microsoft Passport for Work management|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Option for clients to switch to a new software update point|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[Version 1606](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |Client settings to manage Client Cache Settings and client Peer Cache |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|Client Settings: [Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>Peer Cache: [Version 1610](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |Support for Passport for Work as a KSP |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[Version 1606](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |On-premises Device Health Attestation|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[Version 1606](/sccm/core/servers/manage/health-attestation)|  
 |SmartLock setting for Android devices|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[Version 1606](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 |Improvements to Software Center|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Improvements to remote control|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
-->



## <a name="see-also"></a>참고 항목  
[System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [System Center Configuration Manager 소개](../../core/understand/introduction.md)
