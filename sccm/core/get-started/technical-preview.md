---
title: "System Center Configuration Manager Technical Preview | Microsoft 문서"
description: "System Center Configuration Manager에서 새로운 기능을 테스트 시험해 볼 수 있는 기술 미리 보기 릴리스에 대해 알아봅니다."
ms.custom: na
ms.date: 1/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 157
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 8e4ccaf26b83896d12efcbd7ebd4bda4d4bf6675
ms.openlocfilehash: d7d03c4494338a1d4583b6c82d3d5009b7785cfe


---
# <a name="technical-preview-for-system-center-configuration-manager"></a>System Center Configuration Manager Technical Preview

*적용 대상: System Center Configuration Manager(Technical Preview)*

**System Center Configuration Manager Technical Preview 시작**. 이 항목에서는 현재 작업 중인 새로운 기능을 소개하는 개발 중인 미리 보기 릴리스에 대해 자세히 다룹니다. 각 버전의 기술 미리 보기에서는, 기술 미리 보기 버전이 사용 가능한 시기를 기준으로 현재 분기의 System Center Configuration Manager에 포함되지 않은 새로운 기능을 소개합니다. 이러한 기능이 결과적으로 현재 분기 버전의 업데이트에 포함될 수도 있지만, 기능을 완료하고 추가하기 전에 사용자가 사용해 보고 의견을 제공하는 기회를 갖길 원합니다.  

 이 항목은 기술 미리 보기이므로 세부 정보 및 기능은 변경될 수 있습니다.  

 이 항목에서는 기술 미리 보기의 모든 버전에 적용되며, 2015년 12월의 버전 1512처럼 기능이 가장 먼저 제공되는 기술 미리 보기 버전과 함께 새로운 각 기능을 설명합니다. 이러한 기능에 대한 세부 정보는 각 미리 보기 버전만을 다룬 별도 항목에서 자세히 설명합니다.  

 현재 분기의 Configuration Manager에서 제공하는 새로운 기능에 대한 자세한 내용은 [System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012)을 참조하세요.



##  <a name="a-namebkmkreqsa-requirements-and-limitations-for-the-technical-preview"></a><a name="bkmk_reqs"></a> Technical Preview의 요구 사항 및 제한  

> [!IMPORTANT]  
>  기술 미리 보기는 랩 환경에서만 사용하도록 허가되었습니다.  Microsoft에서 지원 서비스를 제공하지 않고, 특정 기능은 미리 보기 소프트웨어에서 사용하지 못할 수 있습니다. 또한 상업적으로 제공되는 소프트웨어와 비교했을 때 Preview 소프트웨어의 보안, 개인 정보 보호, 액세스 가능성, 가용성 및 안정성 표준이 낮거나 다를 수 있습니다.  

 대부분의 제품 필수 조건에 대한 자세한 내용은 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md)의 정보를 참조하세요. 기술 미리 보기 릴리스에는 다음과 같은 예외가 적용됩니다.  

-   각 설치는 90일 동안 활성 상태로 유지된 후에 비활성화됩니다.  

-   지원되는 언어는 영어뿐입니다.  

-   독립 실행형 기본 사이트만 지원됩니다. 중앙 관리 사이트, 여러 기본 사이트 또는 보조 사이트는 지원되지 않습니다.  

-   다음 SQL Server 버전만 지원됩니다.  

    -   SQL Server 2012 누적 업데이트 2 이상  

    -   SQL Server 2014  

-   사이트는 최대 10개 클라이언트를 지원하며, 이러한 클라이언트는 다음 운영 체제 중 하나를 실행해야 합니다.  

    -   Windows 7  

    -   Windows 8  

    -   Windows 8.1  

    -   Windows 10  

-   다음 설치 플래그(스위치)만 지원됩니다.  

    -   **/silent**  

    -   **/testdbupgrade**  

-   해당되는 추가 제한 사항 또는 요구 사항이 특정 버전의 각 Technical Preview에 대한 세부 정보에 포함되어 있습니다.  

-   이 미리 보기 빌드에서/빌드로 마이그레이션할 수는 없습니다.  

-   이 미리 보기 빌드로 업그레이드할 수는 없습니다.  

-   이 미리 보기 빌드에서 프로덕션 빌드(현재 분기)로 업그레이드할 수 없습니다. 그러나 미리 보기 버전용 업데이트를 사용할 수 있는 경우 Configuration Manager 콘솔의 **업데이트 및 서비스** 노드에서 해당 업데이트를 찾아 설치할 수 있습니다. 콘솔 내 업그레이드 프로세스에 대한 비디오를 보려면 youtube.com에서 [ConfigMgr 업데이트 패키지 설치](https://www.youtube.com/embed/KBd_EGFbUT8) (영문)를 참조하세요.  

##  <a name="a-namebkmkinstalla-install-and-update-the-technical-preview"></a><a name="bkmk_install"></a> 기술 미리 보기 설치 및 업데이트  
 System Center Configuration Manager Technical Preview는 현재 릴리스의 System Center Configuration Manager와 다릅니다.  

 기술 미리 보기를 사용하려면 먼저 기술 미리 보기 빌드의 **기준선 버전** 을 설치해야 합니다. 기준선 버전을 설치한 후 **콘솔 내 업데이트** 를 사용하여 최근의 미리 보기 버전으로 설치를 업데이트할 수 있습니다.     일반적으로 새 버전의 기술 미리 보기는 매달 사용할 수 있습니다.  

> [!TIP]  
>  기술 미리 보기에 대한 업데이트를 설치하면 해당 새 기술 미리 보기 버전으로 미리 보기 설치가 업데이트됩니다.    기술 미리 보기 설치에는 현재 분기 설치로 업그레이드하거나 현재 분기 릴리스의 업데이트를 받을 수 있는 옵션이 없습니다.  

 **기술 미리 보기의 활성 기준선 버전:**  
 릴리스 후 최대 1년 동안 기준 버전을 설치할 수 있습니다.

-   **Technical Preview 1610** - Configuration Manager Technical Preview 1610은 Configuration Manager Technical Preview의 콘솔 내 업데이트로, 그리고 [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 웹 사이트에서 사용할 수 있는 새 기준 버전으로 제공됩니다.

-   **System Center Technical Preview 5**의 일부인 **Technical Preview 1603** - Configuration Manager Technical Preview 1603은 Configuration Manager Technical Preview의 콘솔 내 업데이트로, 그리고 System Center Technical Preview 5에 포함된 새 기준 버전으로 사용할 수 있습니다.    System Center Technical Preview 5에 포함된 버전만 초기 설치에 사용할 수 있습니다.  

     [System Center Technical Preview 5의 Configuration Manager Technical Preview](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview) 기준 버전 정보:  

    -   설치 프로그램과 Configuration Manager 콘솔은 둘 다 System Center Configuration Manager Technical Preview 1603으로 버전이 표시됩니다.  

    -   이 기준 버전은 콘솔 내 업데이트에 대한 지원을 비롯하여 Configuration Manager Technical Preview 1603과 마찬가지로 작동합니다.  


##  <a name="a-namebkmktpfeedbacka-providing-feedback"></a><a name="BKMK_TPFeedback"></a> 사용자 의견 제공  
 기술 미리 보기에 대한 여러분의 의견을 보내 주시기 바랍니다. 각 미리 보기의 기능에 대한 의견을 제출하려면 링크를 클릭하여 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) 페이지에 있는 사용자 의견 양식으로 이동하세요.  

 새로 추가되기를 원하는 기능에 대한 의견을 보내 주셔도 됩니다. 새로운 아이디어를 전송하고 다른 사용자들이 전송한 아이디어에 대해 투표를 하려면 [사용자 의견 페이지를 방문](http://configurationmanager.uservoice.com)하세요.  

##  <a name="a-namebdmktpknownissuesa-general-changes-introduced-in-technical-previews"></a><a name="bdmk_tpknownissues"></a> Technical Preview에 도입된 일반 변경 내용  

-   **Technical Preview 1603:**  

    -   Technical Preview 1603부터, 클라이언트에서 소프트웨어 업데이트를 설치하고 다시 시작한 직후에 소프트웨어 업데이트 준수 검사를 실행하도록 소프트웨어 업데이트 배포를 구성할 수 있습니다. 이렇게 하면 클라이언트가 다시 시작된 후 해당하는 추가 소프트웨어 업데이트를 확인한 다음, 동일한 유지 관리 기간 동안 해당 업데이트를 설치하여 규격을 준수할 수 있습니다.  

         배포를 위해 이를 구성하려면 소프트웨어 업데이트 배포 마법사의 **사용자 환경** 페이지에서 **이 배포의 업데이트를 적용하기 위해 시스템을 다시 시작해야 하는 경우 다시 시작한 후 업데이트 배포 평가 주기 실행**옵션을 선택합니다.  

    -   Technical Preview 1603 부터 SMSTSRebootDelay 작업 순서 변수의 동작이 변경되었습니다. SMSTSRebootDelay 변수는 컴퓨터를 다시 시작하기 전까지 대기하는 시간(초)을 지정합니다. 이 변수를 0으로 설정하지 않은 경우에는 다시 시작하기 전에 작업 순서 관리자에 알림 대화 상자가 표시됩니다.  
        이 변수의 값을 구성하면 해당 값은 새 값을 구성할 때까지 유지됩니다. 모든 후속 컴퓨터 다시 시작에 대한 지연의 값은 동일합니다. Configuration Manager 1602 이전 버전에서는, 컴퓨터가 다시 시작된 후 이 변수가 기본값(30초)으로 다시 설정됩니다.   자세한 내용은 [System Center Configuration Manager에서 작업 순서 기본 제공 변수](../../osd/understand/task-sequence-built-in-variables.md)를 참조하세요.

-   **Technical Preview 1602:** Technical Preview 1602부터는 Windows 2008 Server R2를 실행하는 사이트 시스템 서버의 운영 체제를 Windows 2012 Server R2로 전체 업그레이드할 수 있습니다.  Windows Server 2012 R2 업그레이드 절차를 사용하면 업그레이드 후에 Configuration Manager 사이트 서버 복원을 실행할 필요가 없습니다.  업그레이드 절차를 [Windows Server 2012 R2에 대한 업그레이드 옵션](https://technet.microsoft.com/library/dn303416.aspx)을 참조하세요.  

    > [!WARNING]  
    >  Windows Server 2012 R2로 업그레이드하기 전에 서버에서 **WSUS 3.2를 제거** 해야 합니다.  
    >   
    >  이 중요 단계에 대한 자세한 내용은 Windows Server 문서에서 [Windows Server Update Services 개요](https://technet.microsoft.com/library/hh852345.aspx) 새로운 기능 및 변경된 기능 섹션을 참조하세요.  

-   **Technical Preview 1601:** 기본적으로 서비스 연결 지점은 설치 시 온라인 모드로 설정되며 오프라인 모드로 변경할 수 없습니다.  





##  <a name="a-namebkmktpcapsa-capabilities-delivered-in-technical-previews"></a><a name="bkmk_tpCaps"></a> 기술 미리에 포함된 기능  
 다음에는 각 Configuration Manager 기술 미리 보기 릴리스에 포함된 기능이 나와 있습니다.  기술 미리 보기의 특정 버전에서 사용할 수 있는 기능은 이후 버전에서도 계속 사용할 수 있습니다. 마찬가지로, System Center Configuration Manager 릴리스(현재 분기)에 추가된 기능은 후속 기술 미리 보기에서도 계속 사용할 수 있습니다.  각 미리 보기 버전에 대한 콘텐츠를 클릭하여 특정 기능에 대한 자세한 내용을 알아볼 수 있습니다.  

 |기능|기술 미리 보기 버전|현재 분기 버전|  
 |----------------|---------------------|--------------------|
 |소프트웨어 업데이트 지점에 대한 향상된 경계 그룹 | [Tech Preview 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |![추가되지 않음](media/Red_X.gif)  |
 |하드웨어 인벤토리를 통해 UEFI 정보 수집 | [Tech Preview 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|![추가되지 않음](media/Red_X.gif)  |
 |운영 체제 배포 향상| [Tech Preview 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|![추가되지 않음](media/Red_X.gif)  |
 |클라우드 기반 배포 지점에서 소프트웨어 업데이트 호스트| [Tech Preview 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|![추가되지 않음](media/Red_X.gif) |
 |관리 지점을 통해 장치 상태 증명 데이터의 유효성 검사| [Tech Preview 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)|![추가되지 않음](media/Red_X.gif) |
 |Microsoft Azure Government 클라우드용 OMS 커넥터 |[Tech Preview 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |![추가되지 않음](media/Red_X.gif) |
 |OData 끝점 데이터 액세스 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![추가되지 않음](media/Red_X.gif)|
 |데이터 웨어하우스 서비스 지점 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|![추가되지 않음](media/Red_X.gif)|
 |콘텐츠 라이브러리 정리 도구 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|![추가되지 않음](media/Red_X.gif)|
 |콘솔 내 검색의 향상된 기능 |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|![추가되지 않음](media/Red_X.gif)|
 |지정한 프로그램이 실행되는 경우 응용 프로그램 설치 차단|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|![추가되지 않음](media/Red_X.gif)|
 |최종 사용자에 대한 새 비즈니스용 Windows Hello 알림|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|![추가되지 않음](media/Red_X.gif)|
 |Configuration Manager의 비즈니스용 Windows 스토어 지원|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|![추가되지 않음](media/Red_X.gif)|
 |작업 순서가 실패할 경우 이전 페이지로 돌아가기|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|![추가되지 않음](media/Red_X.gif)|
 |Windows 10 업데이트에 대한 빠른 설치 파일 지원|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|![추가되지 않음](media/Red_X.gif)|
 |Azure Active Directory 등록|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|![추가되지 않음](media/Red_X.gif)|
|장치 등록에 대한 다단계 인증 구성 변경|[Tech Preview 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![추가되지 않음](media/Red_X.gif)|
|배포 및 작업 순서에 대한 콘텐츠 사전 캐시 |[Tech Preview 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|![추가되지 않음](media/Red_X.gif)|
 |Windows Defender 구성 설정|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[버전 1610](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |관리자 콘솔에서 정책 동기화 요청|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[버전 1610](/sccm/mdm/deploy-use/sync-intune-device)|
 |모든 회사 소유 장치 노드에 대한 추가 보안 역할 지원|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[버전 1610](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Windows 10 VPN 프로필에 대한 조건부 액세스|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[버전 1610](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |자동 배포 규칙의 콘텐츠 크기에 따라 필터링|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[버전 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |필수 소프트웨어 대화 상자에 대한 향상된 기능|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[버전 1610](/sccm/apps/deploy-use/deploy-applications)|
 |이전에 승인된 응용 프로그램 요청 거부|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[버전 1610](/sccm/apps/deploy-use/deploy-applications)|
 |자동 업그레이드에서 클라이언트 제외|[Tech Preview 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[버전 1610](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Endpoint Protection 개선|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|![추가되지 않음](media/Red_X.gif)|
 |등록된 장치 수 증가|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#increased-number-of-enrolled-devices)|![추가되지 않음](media/Red_X.gif)|
 |추가 Apple DEP 설정|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[버전 1610](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Configuration Manager와 비즈니스용 Windows 스토어 통합 향상|[Tech Preview 1609](capabilities-in-technical-preview-1609.md)|[버전 1610](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |구성 항목의 새 준수 설정|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[버전 1610](/sccm/compliance/deploy-use/create-configuration-items)|
 |Upgrade Analytics 통합|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[버전 1610](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |Windows 10 VPN 하이브리드 프로필에 대한 네이티브 연결 형식|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![추가되지 않음](media/Red_X.gif)|
 |경계 그룹의 향상된 기능|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[버전 1610](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Office 365 클라이언트 관리 대시보드|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[버전 1610](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |클라이언트에 Office 365 앱 배포|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|![추가되지 않음](media/Red_X.gif)|
 |BIOS-UEFI 변환의 향상된 기능|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[버전 1610](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Intune 준수 차트|[Tech Preview 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[버전 1610](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|
 |ConfigMgr 클라이언트 캡처 준비 작업 순서 단계의 향상 기능|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[버전 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |소프트웨어 센터 개선|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Asset Intelligence 개선|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|![추가되지 않음](media/Red_X.gif)|
 |원격 제어 키보드 변환|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)|![추가되지 않음](media/Red_X.gif)|
 |Windows 10 버전 업그레이드 정책의 향상 기능|[Tech Preview 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[버전 1610](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |소프트웨어 센터 대화 상자에 대한 사용자 지정 가능한 브랜딩|[Tech Preview 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|![추가되지 않음](media/Red_X.gif)|  
 |온-프레미스 모바일 장치 관리에 대한 여러 장치 관리 지점|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |컬렉션으로 장치 자동 분류|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[버전 1606](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |필수 응용 프로그램 및 소프트웨어 업데이트 배포를 위한 유예 기간 적용|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[버전 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Device Guard로 Configuration Manager를 관리되는 설치 프로그램으로 사용|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|![추가되지 않음](media/Red_X.gif)|
 |클라우드 관리 게이트웨이(이전의 클라우드 프록시 서비스)|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [버전 1610](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Configuration Manager에서 Office 365 클라이언트 에이전트 관리|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |OSDPreserveDriveLetter 작업 순서 변수는 사용되지 않습니다.|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[버전 1606](/sccm/osd/understand/task-sequence-built-in-variables) |
 |업데이트 및 서비스 노드의 변경 내용|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Windows 10 장치를 위한 앱당 VPN|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[버전 1606](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |소프트웨어 업데이트 설치 작업 순서의 향상 기능|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |ConfigMgr 클라이언트 캡처 준비 작업 순서 단계의 향상 기능 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[버전 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |필수 응용 프로그램 배포를 위한 유예 기간 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|![추가되지 않음](media/Red_X.gif)|  
 |원격 장치 작업을 위한 새로운 환경 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |비즈니스용 Windows 스토어 앱 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[버전 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |대량 구매 앱의 일반적인 향상 기능|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |EDP(엔터프라이즈 데이터 보호)|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |최종 사용자가 회사 포털에서 앱을 설치할 수 있습니다. |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|![추가되지 않음](media/Red_X.gif)|  
 |소프트웨어 센터의 업데이트 및 운영 체제에 대한 새로운 탭|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[버전 1606 ](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |서버 그룹 제공 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[버전 1606](/sccm/sum/deploy-use/service-a-server-group)|   
 |Windows Defender Advanced Threat Protection 서비스에 대한 지원 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[버전 1606](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |소프트웨어 업데이트 설치 후 Windows 10 클라이언트의 다시 시작 옵션|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[버전 1606](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |온-프레미스 장치 상태 증명 |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[버전 1606](/sccm/core/servers/manage/health-attestation)|  
 |IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[버전 1606](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  
 |비즈니스용 Windows 스토어에서 대량 구매 앱 관리| [Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[버전 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Microsoft Passport for Work 관리의 개선 사항|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |클라이언트에서 새 소프트웨어 업데이트 지점으로 전환하는 옵션|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[버전 1606](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |클라이언트 캐시 설정 및 클라이언트 피어 캐시를 관리하는 클라이언트 설정 |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|클라이언트 설정: [버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>피어 캐시: [버전 1610](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |KSP로서 Passport for Work에 대한 지원 |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[버전 1606](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |온-프레미스 장치 상태 증명|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[버전 1606](/sccm/core/servers/manage/health-attestation)|  
 |Android 장치에 대한 SmartLock 설정|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[버전 1606](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 |소프트웨어 센터 개선|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |원격 제어의 개선 사항|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |PXE 사용 배포 지점에서 RamDisk TFTP 블록 크기 및 창 크기 사용자 지정|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[버전 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |모바일 장치 관리 개선|[Tech Preview 1602](capabilities-in-technical-preview-1602.md#BKMK_MDM)|[버전 1602](/sccm/mdm/deploy-use/manage-ios-activation-lock) |  
 |1602 버전에서 소프트웨어 센터의 개선 사항|[Tech Preview 1602](capabilities-in-technical-preview-1602.md#BKMK_SC1601)| [버전 1602](/sccm/core/plan-design/changes/whats-new-in-version-1602#client-management)|  
 |Windows 10 서비스 개선|[Tech Preview 1602](capabilities-in-technical-preview-1602.md#BKMK_Win10Servicing)|[버전 1602](/sccm/core/plan-design/changes/whats-new-in-version-1602#operating-system-deployment) |  
 |Microsoft Intune 통합 향상|[Tech Preview 1601](capabilities-in-technical-preview-1601.md#bkmk_hybrid1)|[버전 1602](/sccm/core/plan-design/changes/whats-new-in-version-1602#conditional-access)|  
 |클라이언트 온라인 상태|[Tech Preview 1601](capabilities-in-technical-preview-1601.md#bkmk_clientStatus)|[버전 1602](/sccm/core/clients/manage/monitor-clients)|
 |응용 프로그램 관리 향상|[Tech Preview 1601](capabilities-in-technical-preview-1601.md#bkmk_appmgmt1601)|[버전 1602](/sccm/core/plan-design/changes/whats-new-in-version-1602#application-management)|  
 |향상된 호환성 설정|[Tech Preview 1601](capabilities-in-technical-preview-1601.md#bkmk_compliance1601)|[버전 1602](/sccm/core/plan-design/changes/whats-new-in-version-1602#compliance-settings)|  
 |장치 상태 증명|[Tech Preview 1512](capabilities-in-technical-preview-1512.md#bkmk_devicehealth)|[버전 1602](/sccm/core/servers/manage/health-attestation))|
 |콘솔 내 사용 약관 모니터링|[Tech Preview 1512](capabilities-in-technical-preview-1512.md#bkmk_viewterms)|[버전 1602](/sccm/mdm/deploy-use/terms-and-conditions)|  
 |Endpoint Protection 정책 설정의 향상된 기능|[Tech Preview 1512](capabilities-in-technical-preview-1512.md#bkmk_EPpolicy)|[버전 1602](/sccm/protect/deploy-use/endpoint-antimalware-policies)|  
 |Windows 10에서 비즈니스용 Windows 업데이트와 통합|[Tech Preview 1511](capabilities-in-technical-preview-1511.md#BKMK_WUfB)|[버전 1602](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10)|  
 |System Center Configuration Manager를 통해 Office 365 ProPlus 클라이언트 업데이트 관리|[Tech Preview 1511](capabilities-in-technical-preview-1511.md#BKMK_Office365ProPlus)|[버전 1602](/sccm/sum/deploy-use/manage-office-365-proplus-updates)|  
 |항상 사용 가능한 데이터베이스에 대한 SQL Server AlwaysOn 지원|[Tech Preview 1511](capabilities-in-technical-preview-1511.md#BKMK_AlwasyOn)|[버전 1602](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)|  
 |서버 클러스터 서비스|[Tech Preview 1511](capabilities-in-technical-preview-1511.md#BKMK_ClusterServerUpdates)|[버전 1606](/sccm/sum/deploy-use/service-a-server-group)|  
## <a name="see-also"></a>참고 항목  
[System Center Configuration Manager의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [System Center Configuration Manager 소개](../../core/understand/introduction.md)



<!--HONumber=Jan17_HO3-->


