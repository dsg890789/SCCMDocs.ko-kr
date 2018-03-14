---
title: "기술 미리 보기 릴리스"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에서 새로운 기능을 테스트 시험해 볼 수 있는 기술 미리 보기 릴리스에 대해 알아봅니다."
ms.custom: na
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.reviewer: nab
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 1cb4d775985839ea7c4fb1b48a04ab0be64f5d8c
ms.sourcegitcommit: 32bbc006a41868a6d9a708db5f7b372d9c71d985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2018
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>System Center Configuration Manager Technical Preview

*적용 대상: System Center Configuration Manager(Technical Preview)*

**System Center Configuration Manager Technical Preview 시작**. 이 문서에서는 현재 작업 중인 새로운 기능을 소개하는 개발 중인 미리 보기 릴리스에 대해 자세히 다룹니다. 각 버전의 Technical Preview에서는 Technical Preview 버전이 사용 가능한 시점에서 현재 분기의 Configuration Manager에 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능이 결과적으로 현재 분기 버전의 업데이트에 포함될 수도 있지만, 기능을 완료하고 추가하기 전에 사용자가 사용해 보고 의견을 제공하는 기회를 갖길 원합니다.  

 이 릴리스는 기술적인 미리 보기이므로 세부 사항 및 기능은 변경될 수 있습니다.  

 이 문서는 모든 버전의 Technical Preview에 적용되는 정보를 포함합니다. 또한 2018년 2월의 1802 버전처럼, 기능이 가장 먼저 제공되는 Technical Preview 버전과 함께 새로운 각 기능을 설명합니다. 이러한 기능은 각 미리 보기 버전만을 다룬 별도 항목에서 자세히 설명합니다.  

 현재 분기의 Configuration Manager에서 제공하는 새로운 기능에 대한 자세한 내용은 [System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012)을 참조하세요.



##  <a name="bkmk_reqs"></a> Technical Preview의 요구 사항 및 제한  

> [!IMPORTANT]     
>  기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다.  Microsoft에서 지원 서비스를 제공하지 않을수 있으며, 특정 기능은 미리 보기 소프트웨어에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 미리 보기 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

 대부분의 제품 필수 조건에 대한 자세한 내용은 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md)의 정보를 참조하세요. 기술 미리 보기 릴리스에는 다음과 같은 예외가 적용됩니다.  

-   각 설치는 90일 동안 활성 상태로 유지된 후에 비활성화됩니다.  

-   지원되는 언어는 영어뿐입니다.


-   다음 설치 플래그(스위치)만 지원됩니다.  

    -   **/silent**  
    -   **/testdbupgrade**    


-   기본적으로 Technical Preview를 사용하는 경우 서비스 연결 지점이 온라인 모드로 설치됩니다. 오프라인 모드로 변경되도록 지원하지 않습니다.

-   특정 버전의 기술 문서에 대한 별도 문서에는 해당되는 추가 제한 사항 또는 요구 사항이 포함되어 있습니다.

-   이 미리 보기 빌드에서/빌드로 마이그레이션할 수는 없습니다.  

-   이 미리 보기 빌드로 업그레이드할 수는 없습니다. 

-   cd.latest 폴더에서의 사이트 복구는 지원되지 않습니다.  <!--507106-->

-   이 미리 보기 빌드에서 프로덕션 빌드(현재 분기)로 업그레이드할 수 없습니다. 그러나 미리 보기 버전용 업데이트를 사용할 수 있는 경우 Configuration Manager 콘솔의 **업데이트 및 서비스** 노드에서 해당 업데이트를 찾아 설치할 수 있습니다. 콘솔 내 업그레이드 프로세스에 대한 비디오를 보려면 youtube.com에서 [ConfigMgr 업데이트 패키지 설치](https://www.youtube.com/embed/KBd_EGFbUT8) (영문)를 참조하세요.  
-   독립 실행형 기본 사이트만 지원됩니다. 중앙 관리 사이트, 여러 기본 사이트 또는 보조 사이트는 지원되지 않습니다.  

다음 제품 및 기술은 이 Configuration Manager 분기에서 지원됩니다. 그러나 이 내용에 포함되었다고 해서 개별 지원 주기가 끝난 제품 또는 버전의 지원 연장을 의미하지는 않습니다. 즉, 지원 주기가 끝난 제품은 Configuration Manager에서 사용할 수 없습니다. Microsoft 지원 주기에 대한 자세한 내용은 [Microsoft 지원 주기](http://go.microsoft.com/fwlink/p/?LinkId=208270) 웹 사이트를 참조하세요.  

-   다음 SQL Server 버전만 지원됩니다.  

    -   Configuration Manager 버전 1710에서 시작하는 SQL Server 2017(누적 업데이트 2 이상)
    -   SQL Server 2016(서비스 팩 없음 버전 이상)
    -   SQL Server 2014(서비스 팩 1 이상)
    -   SQL Server 2012(서비스 팩 3 이상)


-   사이트는 최대 10개 클라이언트를 지원하며, 이러한 클라이언트는 다음 버전의 Windows 중 하나를 실행해야 합니다.  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 7  

##  <a name="bkmk_install"></a> 기술 미리 보기 설치 및 업데이트  
 System Center Configuration Manager Technical Preview는 현재 릴리스의 System Center Configuration Manager와 다릅니다.  

 Technical Preview를 사용하려면 먼저 Technical Preview 빌드의 **기준 버전**을 설치해야 합니다. 기준선 버전을 설치한 후 **콘솔 내 업데이트**를 사용하여 최근의 미리 보기 버전으로 설치를 업데이트할 수 있습니다. 일반적으로 새 버전의 기술 미리 보기는 매달 사용할 수 있습니다.

세 가지 후속 릴리스를 사용할 수 있을 때까지 각 미리 보기 릴리스가 지원됩니다. 즉, 버전 1708이 출시되면 버전 1704는 더 이상 지원되지 않지만 버전 1705, 1706 및 1707은 계속 지원됩니다. 기준 버전이 지원되지 않는 경우에도 해당 설치를 지원되는 버전으로 업데이트하는 한 새 기준 버전을 사용할 수 있을 때까지 새 Technical Preview 사이트를 설치할 수 있습니다. 사용 가능한 최신 버전을 업데이트하고, 최신 버전의 Technical Preview를 설치할 수 있을 때까지 해당 프로세스를 반복합니다.

> [!TIP]  
>  기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다.    기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하거나 현재 분기 릴리스의 업데이트를 받을 수 있는 옵션이 없습니다.  

**기술 미리 보기의 활성 기준선 버전:**
   
릴리스 후 최대 1년 동안 기준 버전을 설치할 수 있습니다. 그러나 새 Technical Preview 사이트를 설치할 경우 사용 가능한 최신 기준선 버전을 사용하는 것이 좋습니다.
-  **Technical Preview 1711** - Configuration Manager Technical Preview 1711은 콘솔 내 업데이트와 새로운 기준 버전으로 모두 제공됩니다. [TechNet 평가 센터에서](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 기준 버전을 다운로드합니다.


##  <a name="BKMK_TPFeedback"></a> 사용자 의견 제공  
 Technical Preview의 기능에 대한 피드백을 보내 주시기 바랍니다. 자세한 내용은 [제품 피드백](../understand/find-help.md#product-feedback)을 참조하세요.

새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 전송하고 다른 사용자들이 전송한 아이디어에 대해 투표를 하려면 [사용자 의견 페이지를 방문](http://configurationmanager.uservoice.com)하세요.  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> 가장 최근의 Technical Preview에 포함된 기능  
최신 Configuration Manager Technical Preview 릴리스에 포함된 기능은 다음과 같습니다.  이전 버전의 Technical Preview에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로, Configuration Manager 현재 분기에 추가된 기능은 Technical Preview 릴리스에서도 계속 사용할 수 있습니다.  각 미리 보기 버전에 대한 콘텐츠를 클릭하여 특정 기능에 대한 자세한 내용을 알아볼 수 있습니다.  

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1802"></a>Technical Preview 버전 1802
- [공동 관리를 사용하여 Endpoint Protection 워크로드를 Intune으로 전환](capabilities-in-technical-preview-1802.md#transition-endpoint-protection-workload-to-intune-using-co-management) <!-- 1357365 -->
- [Configuration Manager 경계 그룹을 사용하도록 Windows 배달 최적화 구성](capabilities-in-technical-preview-1802.md#configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups) <!-- 1324696 --> 
- [클라우드 관리 게이트웨이를 통한 Windows 10 현재 위치 업그레이드 작업 순서](capabilities-in-technical-preview-1802.md#windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway) <!-- 1357149 -->
- [Windows 10 현재 위치 업그레이드 작업 순서 개선 사항](capabilities-in-technical-preview-1802.md#improvements-to-windows-10-in-place-upgrade-task-sequence) <!-- 1357425 --> 
- [PXE 사용 배포 지점 개선 사항](capabilities-in-technical-preview-1802.md#improvements-to-pxe-enabled-distribution-points) <!-- 1357580 --> 
- [작업 순서에 대한 배포 템플릿](capabilities-in-technical-preview-1802.md#deployment-templates-for-task-sequences) <!-- 1357391 --> 
- [제품 수명 주기 대시보드](capabilities-in-technical-preview-1802.md#product-lifecycle-dashboard) <!--1319632 --> 
- [보고 개선 사항](capabilities-in-technical-preview-1802.md#improvements-to-reporting) <!--1357653 --> 
- [소프트웨어 센터 개선 사항](capabilities-in-technical-preview-1802.md#improvements-to-software-center) <!--1357592 --> 
- [스크립트 실행의 향상된 기능](capabilities-in-technical-preview-1802.md#improvements-to-run-scripts) <!--1236459 --> 
- [관리 지점에 대한 경계 그룹 대체](capabilities-in-technical-preview-1802.md#boundary-group-fallback-for-management-points) <!-- 1324594 --> 
- [CNG 인증서에 대한 향상된 지원](capabilities-in-technical-preview-1802.md#improved-support-for-cng-certificates) <!-- 1357314 --> 
- [Azure Resource Manager에 대한 클라우드 관리 게이트웨이 지원](capabilities-in-technical-preview-1802.md#cloud-management-gateway-support-for-azure-resource-manager) <!-- 1324735 --> 
- [장치당 사용자에 대한 응용 프로그램 요청 승인](capabilities-in-technical-preview-1802.md#approve-application-requests-for-users-per-device) <!-- 1357015 --> 
- [소프트웨어 센터를 사용하여 Azure AD 조인 장치에서 사용자가 사용할 수 있는 응용 프로그램 찾아보기 및 설치](capabilities-in-technical-preview-1802.md#use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices) <!-- 1322613 --> 
- [Windows AutoPilot 장치 정보에 대한 보고서](capabilities-in-technical-preview-1802.md#report-on-windows-autopilot-device-information) <!-- 1351442 --> 
- [Windows Defender Exploit Guard에 대한 Configuration Manager 정책 개선 사항](capabilities-in-technical-preview-1802.md#improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard) <!-- 1356220 -->
- [Microsoft Edge 브라우저 정책](capabilities-in-technical-preview-1802.md#microsoft-edge-browser-policies) <!-- 1357310 -->
- [기본 브라우저 개수에 대한 보고서](capabilities-in-technical-preview-1802.md#report-for-default-browser-counts) <!-- 1357830 --> 
- [Windows 10 ARM64 장치 지원](capabilities-in-technical-preview-1802.md#support-for-windows-10-arm64-devices) <!-- 1353704 --> 
- [단계별 배포 변경 사항](capabilities-in-technical-preview-1802.md#changes-to-phased-deployments) <!-- 1357405 -->



## <a name="capabilities-delivered-in-recent-supported-technical-previews"></a>최근 지원되는 Technical Preview에 포함된 기능
이전 버전의 Configuration Manager Technical Preview 릴리스에 포함되어 여전히 지원되는 기능은 다음과 같습니다. 

<!-- This is the full list of new features in the past three TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 |기능 |기술 미리 보기 버전 |현재 분기 버전|  
 |----------------|---------------------|--------------------|
 |단계별 배포 만들기 <!-- 1357405 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#create-phased-deployments)  |![추가되지 않음](media/Red_X.gif)    |
 |공동 관리 보고 <!-- 1356648 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#co-management-reporting)  |![추가되지 않음](media/Red_X.gif)    |
 |자동 배포 규칙 평가 일정 개선 사항 <!-- 1357133 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-automatic-deployment-rule-evaluation-schedule)  |![추가되지 않음](media/Red_X.gif)    |
 |배포 지점 다시 할당 <!-- 1306937 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#reassign-distribution-point)  |![추가되지 않음](media/Red_X.gif)    |
 |하드웨어 인벤토리 개선 사항 <!-- 1357389 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-hardware-inventory)  |![추가되지 않음](media/Red_X.gif)    |
 |소프트웨어 센터에 대한 클라이언트 설정 개선 사항 <!-- 1355146 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-client-settings-for-software-center)  |![추가되지 않음](media/Red_X.gif)    |
 |Windows Defender Application Guard에 대한 새로운 설정 <!-- 1356256 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#new-settings-for-windows-defender-application-guard)  |![추가되지 않음](media/Red_X.gif)    |
 |스크립트 실행 개선 사항 <!-- 1236459 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-run-scripts)  |![추가되지 않음](media/Red_X.gif)    |
 |교체된 응용 프로그램을 자동으로 업그레이드하지 않습니다 <!-- 1351266 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#do-not-automatically-upgrade-superseded-applications)  |![추가되지 않음](media/Red_X.gif)    | 
 |소프트웨어 센터에서 여러 응용 프로그램 설치 <!-- 1357126 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#install-multiple-applications-in-software-center)  |![추가되지 않음](media/Red_X.gif)    |
 |클라이언트 기반 PXE 응답자 서비스 <!-- 1357148 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service)  |![추가되지 않음](media/Red_X.gif)    |
 |Configuration Manager 클라이언트 설치 변경 <!-- 1356195 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#change-in-the-configuration-manager-client-install)  |![추가되지 않음](media/Red_X.gif)    | 
 |Surface 장치 대시보드 변경 <!-- 1355788 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#change-to-the-surface-device-dashboard)  |![추가되지 않음](media/Red_X.gif)    | 
 |Office 365 클라이언트 관리 대시보드에 대한 향상된 기능 <!-- 1357281 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#improvements-to-office-365-client-management-dashboard)  |![추가되지 않음](media/Red_X.gif)    | 
 |Configuration Manager 콘솔에 대한 향상된 기능 <!-- 1357280,1357282 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#improvements-to-the-configuration-manager-console)  |![추가되지 않음](media/Red_X.gif)    | 
 |운영 체제 배포에 대한 향상된 기능 <!-- SMS 500897 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#improvements-to-operating-system-deployment)  |![추가되지 않음](media/Red_X.gif)    | 
 |작업 순서 실행 단계<!-- 1261338 --> | [Tech Preview 1711](capabilities-in-technical-preview-1711.md) |[버전 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence)    |
 |응용 프로그램 설치 시 사용자 상호 작용 허용 <!-- 1356976 --> | [Tech Preview 1711](capabilities-in-technical-preview-1711.md) |![추가되지 않음](media/Red_X.gif)    |

 

## <a name="capabilities-delivered-in-previous-technical-previews"></a>이전 Technical Preview에 포함된 기능
이전 버전의 Configuration Manager Technical Preview 릴리스에 포함된 특정 기능은 다음과 같습니다. 이러한 기능은 이후 버전에서 사용할 수 있지만 현재 분기 릴리스에서는 제공되지 않습니다. 

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

 |기능 |기술 미리 보기 버전 |  
 |----------------|---------------------|
 |Configuration Manager 콘솔에서 개선된 VPN 프로필<!-- 1313282 --> | [Tech Preview 1709](capabilities-in-technical-preview-1709.md) |
 |관리 정보 <!-- 1353967 --> |[기술 미리 보기 1708](capabilities-in-technical-preview-1708.md#management-insights)|
 |Surface 장치 대시보드<!-- 1355788 --> |[Tech Preview 1707](capabilities-in-technical-preview-1707.md#surface-device-dashboard)|
 |사이트 서버 역할 고가용성<!-- 1128774 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |
 |IPv6에 대한 PXE 네트워크 부팅 지원<!-- 1269793 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
 |조건부 액세스의 준수 정책에 대한 장치 상태 증명 평가<!-- 1235616 -->|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#device-health-attestation-assessment-for-compliance-policies-for-conditional-access)|
 |Azure Active Directory 사용 <!-- 1322145? --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
 |Windows Update for Business 업데이트에 대한 준수 평가<!-- 1235390 --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |
 |OData 끝점 데이터 액세스<!-- 1321523 --> |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|
 |Asset Intelligence 개선 <!-- 1307390 --> |[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|
 |최종 사용자가 회사 포털에서 앱을 설치할 수 있습니다.<!-- 1037233? --> |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|



## <a name="see-also"></a>참고 항목  
[System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [System Center Configuration Manager 소개](../../core/understand/introduction.md)
