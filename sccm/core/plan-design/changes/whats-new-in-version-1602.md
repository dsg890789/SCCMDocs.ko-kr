---
title: "버전 1602의 새로운 기능"
titleSuffix: Configuraton Manager
description: "System Center Configuration Manager 버전 1602에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4021eca1-adfb-4e5a-adee-159263c29637
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 0e151b01d3399dafc6ed3962560e8e9975a37a8e
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="what39s-new-in-version-1602-of-system-center-configuration-manager"></a>System Center Configuration Manager 버전 1602의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager 업데이트 1602는 버전 1511을 실행하는 이전에 설치된 사이트에 대한 콘솔 내 업데이트로만 제공됩니다. 버전 1511은 새 Configuration Manager 사이트를 설치하는 데 사용하는 초기 기준선 버전입니다.  


> [!TIP]  
>  다음에 대해 자세히 알아보세요.  
>   
>   -   [새 사이트 설치](/sccm/core/servers/deploy/install)(1511 등의 기준 버전 사용)  
>   -   [사이트에서 업데이트 설치](/sccm/core/servers/manage/updates)(예: 업데이트 1602)  

 다음 섹션에서는 Configuration Manager 버전 1602에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.  

## <a name="site-infrastructure"></a>사이트 인프라  

###  <a name="bkmk_UpgradeOS"></a> Windows Server 2008 R2를 실행하는 사이트 서버의 운영 체제에 대한 현재 위치 업그레이드  
 버전 1602 이상을 실행하는 Configuration Manager 사이트에서는 Windows Server 2008 R2에서 Windows Server 2012 R2로 현재 위치에서 사이트 서버 운영 체제를 업그레이드할 수 있습니다.  

> [!WARNING]  
>  Windows Server 2012 R2로 업그레이드하기 전에 서버에서 WSUS 3.2를 제거 해야 합니다.  
>   
>  이 중요 단계에 대한 자세한 내용은 Windows Server 문서에서 [Windows Server Update Services 개요](https://technet.microsoft.com/library/hh852345.aspx)의 “새로운 기능 및 변경된 기능” 섹션을 참조하세요.  

 서버를 업그레이드하려면 Windows Server 2012 R2 업그레이드 절차를 사용하세요. 업그레이드 후에 Configuration Manager 사이트 서버 복원을 실행할 필요가 없습니다. 업그레이드 절차에 대해서는 Windows Server 문서에서 [Windows Server 2012 R2에 대한 업그레이드 옵션](https://technet.microsoft.com/library/dn303416.aspx)을 참조하세요.  

###  <a name="bkmk_AOAG"></a> SQL Server AlwaysOn 가용성 그룹  
 SQL Server AlwaysOn 가용성 그룹을 사용하여 기본 사이트와 중앙 관리 사이트에서 사이트 데이터베이스를 고가용성 및 재해 복구 솔루션으로 호스트할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager용 항상 사용 가능한 사이트 데이터베이스를 위한 SQL Server AlwaysOn](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md)을 참조하세요.  

## <a name="operating-system-deployment"></a>운영 체제 배포  

### <a name="windows-10-servicing"></a>Windows 10 서비스  
 Windows 10 서비스에 대한 다음과 같은 향상된 기능이 Configuration Manager 버전 1602에 추가되었습니다.  

-   새 필터 옵션은 **언어**, **필수** 및 **제목**으로 필터링할 수 있는 서비스 계획에 사용할 수 있습니다. 지정된 조건을 충족하는 업그레이드만 연결된 배포에 추가됩니다.  

-   소프트웨어 업데이트 동기화에 대해 **업그레이드** 분류를 선택하면 경고가 표시됩니다. 이 경고를 통해 소프트웨어 업데이트를 성공적으로 동기화하고 Windows 10 서비스를 올바르게 작동하기 위해 WSUS(Windows Server Update Services) 4.0용 [핫픽스 3095113](https://support.microsoft.com/kb/3095113)이 필요하다는 사실을 알 수 있습니다. 이 경고 메시지에서 관련된 기술 자료 문서로 이동할 수 있습니다.  

-   이제 사용 가능한 Windows 10 업그레이드가 Configuration Manager 콘솔의 **Windows 10 서비스** \ **모든 Windows 10 업데이트** 노드에만 표시됩니다. 이러한 업데이트는 더 이상 콘솔의 **소프트웨어 업데이트** \ **모든 소프트웨어 업데이트** 노드에 표시되지 않습니다.  

-   서비스 계획은 높은 위험 수준의 배포로 간주되며 **컬렉션 선택** 창에는 사이트 속성에서 구성한 배포 확인 설정을 충족하는 사용자 지정 컬렉션만 표시됩니다. 자세한 내용은 [Settings to manage high-risk deployments for System Center Configuration Manager](../../../protect/understand/settings-to-manage-high-risk-deployments.md)항목을 참조하세요.  

-   이제 Windows 10 업그레이드 패키지를 시작하는 사용자는 해당 운영 체제를 업그레이드할 것임을 알리는 메시지를 받습니다.  

## <a name="application-management"></a>응용 프로그램 관리  

### <a name="ios-app-configuration-policies"></a>iOS 앱 구성 정책  
 Configuration Manager 앱 구성 정책을 사용하여 사용자가 iOS 앱을 실행할 때 필요할 수 있는 설정을 제공할 수 있습니다. 예를 들어 앱에서 사용자가 사용자 지정 포트 번호, 언어, 보안 설정 또는 브랜딩 설정(예: 회사 로고)을 지정하도록 요구할 수 있습니다. 이러한 설정을 잘못 입력하면 지원 센터의 부담이 증가하며 새 앱 도입도 지연됩니다.  

 앱 구성 정책을 사용하는 경우 사용자가 앱을 실행하기 전에 정책에서 이러한 설정을 사용자에게 배포할 수 있으므로 이러한 문제를 방지할 수 있습니다. 설정은 자동으로 제공되므로 사용자가 아무런 작업을 수행하지 않아도 됩니다. 자세한 내용은 [System Center Configuration Manager에서 앱 구성 정책을 사용하여 iOS 앱 구성](../../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md)을 참조하세요.  

### <a name="manage-volume-purchased-ios-apps"></a>Manage volume-purchased iOS apps  
 Configuration Manager를 통해 Apple VPP(Volume-Purchase Program)에서 대량 구매한 앱을 배포하고 관리할 수 있습니다. Configuration Manager는 App Store에서 라이선스 정보를 가져오고 사용한 라이선스 수를 추적합니다.  

 자세한 내용은 [System Center Configuration Manager를 사용하여 대량 구매한 iOS 앱 관리](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md)를 참조하세요.  

### <a name="automatic-creation-of-office-mobile-apps"></a>Office 모바일 앱의 자동 만들기  
 1511에서 1602 버전으로 업데이트하는 경우 Configuration Manager에서 Android 및 iOS용으로 다음과 같은 Microsoft Office 모바일 앱을 자동으로 만듭니다.  

-   Microsoft Word  

-   Microsoft Excel  

-   Microsoft PowerPoint  

-   Microsoft OneDrive  

-   Microsoft OneNote(iOS만 해당)  

-   Microsoft Outlook  

이러한 앱은 Configuration Manager 콘솔의 **응용 프로그램** 노드에 있습니다.  

 응용 프로그램을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램을 배포하는 방법](../../../apps/deploy-use/deploy-applications.md)을 참조하세요.  

## <a name="software-updates"></a>소프트웨어 업데이트  

### <a name="manage-office-365-client-updates"></a>Office 365 클라이언트 업데이트 관리  
 System Center Configuration Manager에서는 소프트웨어 업데이트 관리 워크플로를 사용하여 Office 365 클라이언트 업데이트를 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Office 365 ProPlus 업데이트 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates)를 참조하세요.  

## <a name="compliance-settings"></a>호환성 설정  

### <a name="compliance-settings-for-devices-running-windows-10-team"></a>Windows 10 Team을 실행하는 장치에 대한 준수 설정  
 **Windows 8.1 및 Windows 10** 구성 항목에 새로운 설정이 추가되었습니다. 이러한 설정을 통해 Windows 10 Team을 실행하는 장치(예: Surface Hub 장치)를 제어할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Windows 8.1 및 Windows 10 장치에 대한 구성 항목을 만드는 방법](../../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)을 참조하세요.  

### <a name="kiosk-mode-settings-for-android-samsung-knox-standard-devices"></a>Android Samsung KNOX Standard 장치에 대한 키오스크 모드 설정  
 키오스크 모드에서는 장치를 잠가 특정 기능만 작동하도록 허용할 수 있습니다. 예를 들어, 장치에서 지정된 관리되는 앱만 실행할 수 있게 하거나 장치에서 볼륨 단추를 사용되지 않도록 설정할 수 있습니다. 이러한 설정은 POS 장치와 같이 한 가지 기능만 수행하도록 지정된 장치 또는 장치의 데모 모델에 사용할 수 있습니다. 이제 Configuration Manager에서, Samsung KNOX Standard 장치에 대한 키오스크 모드 설정을 지정할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Android 및 Samsung KNOX Standard 장치에 대한 구성 항목을 만드는 방법](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)을 참조하세요.  

## <a name="conditional-access"></a>조건부 액세스  

### <a name="conditional-access-for-pcs-managed-by-system-center-configuration-manager"></a>System Center Configuration Manager에서 관리하는 PC에 대한 조건부 액세스 지원  
 이 릴리스 이전에서는, PC에 대한 조건부 액세스를 설정하려면 PC가 Intune에 등록되어 있거나 도메인에 가입된 PC여야 합니다. 1602 업데이트부터, System Center Configuration Manager에서 관리하는 PC에 대한 조건부 액세스가 지원됩니다. System Center Configuration Manager에서 관리하는 사용자 PC에 대해, 설정하는 준수 정책을 준수하는 장치로만 Exchange Online 및 SharePoint Online에 대한 액세스를 제한할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager에서 관리되는 PC용 O365 서비스에 대한 액세스 관리](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)를 참조하세요.  

### <a name="restricting-access-based-on-the-health-of-devices"></a>장치 상태에 따라 액세스 제한  
 이제 상태 증명 서비스에서 보고하는 장치의 상태를 기준으로, 메일 및 Office 365 서비스에 대한 액세스를 제한할 수 있습니다. 또한 Intune에서 관리하는 장치는 장치 상태 보고서에 포함됩니다.  

 Configuration Manager 콘솔에서는 상태에 따라 장치의 액세스가 허용되거나 차단되어야 하는지를 지정할 수 있는 새 준수 규칙을 제공합니다. 상태 증명 서비스 및 Intune에서 장치 상태가 보고되는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 상태 증명](../../../core/servers/manage/health-attestation.md)을 참조하세요.  

### <a name="new-compliance-policy-rules"></a>새 준수 정책 규칙  
 자동 업데이트, 장치 잠금을 해제하는 암호 요구 등 새로운 준수 정책 규칙이 더 나은 보안 요구 사항을 지원하기 위해 추가되었습니다.

 자세한 내용은 [System Center Configuration Manager의 장치 준수 정책](../../../protect/deploy-use/device-compliance-policies.md)을 참조하세요.  

### <a name="make-sure-enrolled-and-compliant-devices-always-have-access-to-exchange-on-premises"></a>등록된 규격 장치에서 항상 Exchange 온-프레미스에 액세스할 수 있는지 확인  
 다음 옵션을 선택하면 Intune에 등록되었으며 준수 정책을 준수하는 장치에서 Exchange 온-프레미스에 액세스할 수 있습니다. **기본 규칙 재정의 - Intune에 등록된 규격 장치의 Exchange 온-프레미스 액세스 항상 허용:**. 이 규칙은 Exchange 온-프레미스에 대한 **조건부 액세스 정책 구성 마법사**의 **일반 페이지**에서 사용할 수 있습니다.

 이 규칙은 기본 규칙을 재정의하며, 이것은 기본 규칙을 액세스를 격리 또는 차단하도록 설정하더라도 등록 및 규격 장치는 여전히 Exchange 온-프레미스에 액세스할 수 있음을 의미합니다. 등록된 규격 장치에서 Exchange 온-프레미스를 통해 항상 메일에 액세스할 수 있도록 하려면 이 설정을 사용합니다.   

 자세한 연습을 보려면 [System Center Configuration Manager의 메일 액세스 관리](../../../protect/deploy-use/manage-email-access.md)를 참조하세요.  

## <a name="client-management"></a>클라이언트 관리  

### <a name="client-online-status"></a>클라이언트 온라인 상태  
 클라이언트에 대한 새로운 상태를 컴퓨터가 온라인인지 여부를 모니터링하는 데 사용할 수 있습니다. 컴퓨터가 할당된 관리 지점에 연결된 경우 온라인인 것으로 간주합니다. 컴퓨터가 온라인 상태임을 나타내기 위해 클라이언트에서 관리 지점에 ping과 유사한 메시지를 보냅니다. 관리 지점에서 5분 후에 메시지를 받지 못하면 클라이언트 상태가 오프라인인 것으로 간주됩니다.  

 자세한 내용은 [System Center Configuration Manager에서 클라이언트를 모니터링하는 방법](../../../core/clients/manage/monitor-clients.md)을 참조하세요.  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>소프트웨어 센터에서 PC 컴퓨터 및 사용자 정책 새로 고침  
 PC가 해당 Configuration Manager 컴퓨터 및 사용자 정책을 새로 고치도록 하는 새 옵션, **동기화 정책**이 **옵션** > **컴퓨터 유지 관리** 페이지에 추가되었습니다.  

### <a name="software-center-branding-changes"></a>소프트웨어 센터 브랜딩 변경 내용  
 소프트웨어 센터에 표시되는 색, 조직 이름 및 아이콘을 변경할 수 있습니다. 이러한 설정은 다음 규칙에 따라 적용됩니다.  

- 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되지 않은 경우 소프트웨어 센터에서 **소프트웨어 센터에 표시되는 조직 이름**이라는 **컴퓨터 에이전트** 클라이언트 설정에 지정된 조직 이름을 표시합니다.  

- 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되어 있는 경우 소프트웨어 센터에서 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할의 속성에 지정된 조직 이름 및 색을 표시합니다.  

- Microsoft Intune 구독을 구성하고 Configuration Manager 환경에 연결한 경우 소프트웨어 센터에서 Intune 구독 속성에 지정된 조직 이름, 색 및 회사 로고를 표시합니다.  

### <a name="health-attestation"></a>상태 증명  
 관리자는 Configuration Manager 콘솔에서 Windows 10 장치 상태 증명의 상태를 볼 수 있습니다. 이 기능은 Configuration Manager와 Microsoft Intune에서의 Configuration Manager에 사용할 수 있습니다. 장치 상태 증명을 사용하여 관리자는 클라이언트 컴퓨터가 다음과 같이 신뢰할 수 있는 BIOS, TPM 및 부팅 소프트웨어 구성을 활성화했는지 확인할 수 있습니다.  

-   맬웨어 방지 조기 실행  

-   BitLocker  

-   보안 부팅  

-   코드 무결성  

자세한 내용은 [System Center Configuration Manager에 대한 상태 증명](../../../core/servers/manage/health-attestation.md)을 참조하세요.  

### <a name="improvements-to-endpoint-protection-antimalware-settings"></a>Endpoint Protection 맬웨어 방지 설정의 향상된 기능  
 1602에서는 Windows Defender에 대한 Endpoint Protection 맬웨어 방지 프로그램 정책에서 다음과 같은 새 설정을 추가합니다.  

-   실시간 보호: 다운로드 시 및 설치 전에 잠재적으로 원치 않는 응용 프로그램 차단  

-   검색 설정: 전체 검색 중 매핑된 네트워크 드라이브 검색  

-   자동 샘플 파일 전송 설정:  

     맬웨어 방지 엔진은 추가 분석을 위해 샘플 파일을 Microsoft로 보내도록 요청할 수 있습니다. 기본적으로 이러한 샘플을 보내기 전에 항상 확인 메시지가 표시됩니다. 관리자는 이 동작을 구성하기 위해 다음 설정을 관리할 수 있습니다.  

    -   고급: 검색된 특정 항목의 악성 여부를 Microsoft가 확인할 수 있도록 자동 샘플 파일 전송 설정  

    -   고급: 사용자가 자동 샘플 파일 전송 설정을 수정하도록 허용  

    또한 Endpoint Protection 맬웨어 방지 정책의 "제외 설정" 섹션에 포함된 기존의 **파일 및 폴더 제외** 설정이 이제 장치 제외를 허용합니다.  

자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](../../../protect/deploy-use/endpoint-antimalware-policies.md)을 참조하세요.  

## <a name="mobile-device-management"></a>모바일 장치 관리  

### <a name="ios-activation-lock"></a>iOS 활성화 잠금  
 Configuration Manager를 사용하면 iOS 7.1 이상 장치용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금은 장치에서 나의 iPhone 찾기 앱을 사용할 때 자동으로 사용하도록 설정됩니다. 활성화 잠금이 설정되면 사용자의 Apple ID와 암호를 입력해야 다음 작업을 수행할 수 있습니다.  

-   나의 iPhone 찾기를 끕니다.  

-   장치의 콘텐츠를 지웁니다.  

-   장치를 다시 활성화합니다.  

Configuration Manager에서는 iOS 7.1 이상을 실행하는 감독된/감독되지 않은 장치의 활성화 잠금 상태를 요청할 수 있습니다. 감독된 장치의 경우 Configuration Manager에서 활성화 잠금 무시 코드를 검색하여 장치에 직접 제공할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager의 활성화 잠금 무시를 사용하여 iOS 장치 보호](/sccm/mdm/deploy-use/manage-ios-activation-lock)를 참조하세요.  

### <a name="monitor-terms-and-conditions-deployments"></a>사용 약관 배포 모니터링  
 Configuration Manager 콘솔에서 사용 약관 배포를 모니터링할 수 있습니다.  

 배포 목록에서 사용 약관 배포를 선택합니다. 요약 영역에는 다음 통계가 표시됩니다.  

-   **준수**: 사용자가 최신 버전의 사용 약관을 수락했습니다.  

-   **오류**  

-   **비준수**: 사용자가 사용 약관의 버전을 수락했지만 최신 버전이 아닙니다.  

-   **알 수 없음**: 사용자가 등록된 장치가 없는 사용 약관을 비롯하여 사용 약관을 수락하지 않았습니다.  
