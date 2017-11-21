---
title: "버전 1706의 새로운 기능"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager 버전 1706에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다."
ms.custom: na
ms.date: 08/11/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac034143-003e-4629-aac2-99eaffef4db1
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 2889de0709096aa481ca6203c5ab2bac1f064d5e
ms.sourcegitcommit: c4a1bafcd004638d264a93d307c70d8b6f7fe023
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2017
---
# <a name="what39s-new-in-version-1706-of-system-center-configuration-manager"></a>System Center Configuration Manager 버전 1706의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 현재 분기의 업데이트 1706은 버전 1606, 1610 또는 1702를 실행하는 이전에 설치된 사이트에 대한 콘솔 내 업데이트로 제공됩니다.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용해야 합니다.  
>  다음에 대해 자세히 알아보세요.    
>   - [새 사이트 설치](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [사이트에 업데이트 설치](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

다음 섹션에서는 Configuration Manager 버전 1706에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated features](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Version 1706 drops support for the following products:
-->


## <a name="site-infrastructure"></a>사이트 인프라

### <a name="client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365"></a>Windows 10 및 Office 365에 대한 고속 설치 파일을 위한 클라이언트 피어 캐시 지원  
<!-- 1352486 -->
이 릴리스부터 피어 캐시가 Windows 10 콘텐츠 고속 설치 파일과 Office 365 업데이트 파일 배포를 지원합니다. 이 변경을 지원하기 위한 추가 구성은 필요 없습니다.

### <a name="updates-for-the-data-warehouse"></a>데이터 웨어하우스 업데이트
<!-- 1277922 -->
데이터 웨어하우스는 더 이상 시험판 기능이 아닙니다. 또한 SQL Server Always On 가용성 그룹 및 장애 조치(failover) 클러스터에 대한 지원을 포함하도록 필수 구성 요소를 업데이트했습니다. 자세한 내용은 [데이터 웨어하우스 서비스 지점](/sccm/core/servers/manage/data-warehouse)을 참조하세요.

### <a name="accessibility-improvements"></a>향상된 접근성 기능
<!-- 1253000 -->
Configuration Manager 콘솔에 대한 접근성 기능을 추가로 개선했습니다. 자세한 내용은 [접근성 기능](/sccm/core/understand/accessibility-features)을 참조하세요.

### <a name="improvements--for-sql-server-always-on-availability-groups"></a>SQL Server Always On 가용성 그룹에 대한 향상된 기능
<!-- 1352094 -->
이 릴리스에서는 이제 Configuration Manager에서 SQL Server Always On 가용성 그룹의 비동기 커밋 복제본을 사용할 수 있습니다. 즉, 오프사이트(원격) 백업으로 사용하도록 추가 복제본을 가용성 그룹에 추가한 다음 재해 복구 시나리오에서 사용할 수 있습니다.  
  -   Configuration Manager에서는 비동기 커밋 복제본을 사용하여 동기 복제본을 복구하도록 지원합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 백업 및 복구 항목에서 [사이트 데이터베이스 복구 옵션](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption)을 참조하세요.
  -   이 릴리스에서는 비동기 커밋 복제본을 사이트 데이터베이스로 사용하기 위한 장애 조치를 지원하지 않습니다.
자세한 내용은 [Always On 가용성 그룹 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)를 참조하세요.

### <a name="update-reset-tool"></a>업데이트 다시 설정 도구
<!-- 1324589 -->
버전 1706부터 Configuration Manager 기본 사이트 및 중앙 관리 사이트에는 Configuration Manager 업데이트 다시 설정 도구 **CMUpdateReset.exe**가 포함되어 있습니다. 콘솔 내 업데이트를 다운로드하거나 복제하는 문제가 있는 경우 문제를 해결하려면 지원되는 현재 분기 버전에서 이 도구를 사용합니다. 자세한 내용은 [업데이트 다시 설정 도구](/sccm/core/servers/manage/update-reset-tool)를 참조하세요.

### <a name="high-dpi-console-support"></a>높은 DPI 콘솔 지원  
<!-- 1353476 -->
이 릴리스에서는 높은 DPI 장치(예: Surface Book)에서 볼 때 Configuration Manager 콘솔이 확장되고 UI의 다른 부분을 표시하는 방식의 문제가 수정되었습니다.

### <a name="improved-boundary-groups-for-software-update-points"></a>소프트웨어 업데이트 지점에 대한 향상된 경계 그룹
<!-- 1324591 -->
이 릴리스에서는 소프트웨어 업데이트 지점이 경계 그룹과 작동하는 방식이 개선되었습니다. 다음은 새로운 대체 동작을 요약해서 설명합니다.
-   이제 소프트웨어 업데이트 지점에 대한 대체는 인접 경계 그룹으로의 대체에 대해 구성 가능한 시간을 사용합니다.
-   대체 구성과 관계 없이, 클라이언트는 사용한 마지막 소프트웨어 업데이트 지점에 120분 이내에 도달하려고 합니다. 120분 내에 해당 서버에 도달하지 못하면 클라이언트는 사용 가능한 소프트웨어 업데이트 지점 풀을 확인하여 새 서버를 찾으려고 합니다.
-   2시간 내에 원래 서버에 도달하지 못하면 클라이언트는 새 소프트웨어 업데이트 지점에 연결하기 위해 더 짧은 주기로 전환합니다. 즉, 클라이언트가 새 서버에 연결하지 못할 경우 사용 가능한 서버 풀의 다음 서버를 빠르게 선택하고 해당 서버에 연결하려고 합니다.

자세한 내용은 현재 분기에 대한 경계 그룹 항목에서 [소프트웨어 업데이트 지점](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)을 참조하세요.

### <a name="azure-ad-integration-with-configuration-manager"></a>Configuration Manager와의 Azure AD 통합
<!-- 1248187, 1290765, 1258052, 1298097, 1319334, 1319883, 1352135, 1353331 -->
이 릴리스에서는 Configuration Manager 및 Azure AD(Azure Active Directory)의 통합을 개선했습니다.  이러한 향상된 기능은 Configuration Manager에서 사용하는 Azure 서비스를 구성하는 방법을 능률화하고 Azure AD를 통해 인증을 받는 클라이언트와 사용자를 관리하는 데 도움을 줍니다.

향상된 통합을 통해 다음이 가능해집니다.  
  -   Azure 서비스 마법사 - 이 마법사는 Configuration Manager에서 사용하는 다음 Azure 서비스를 설정하기 위한 개별 워크플로를 대체하는 공통 구성 환경을 제공합니다.
      - **클라우드 관리** Azure AD(Azure Active Directory)를 사용하여 클라이언트가 인증 받도록 합니다. Azure AD 사용자 검색을 구성할 수도 있습니다.
      - **OMS 커넥터** OMS(Operations Manager Suite)에 연결하고 컬렉션과 같은 데이터를 OMS Log Analytics와 동기화합니다.
      - **업그레이드 준비** 업그레이드 준비에 연결하고 클라이언트 업그레이드 호환성 데이터를 확인합니다.
      - **비즈니스용 Windows 스토어** 비즈니스용 Windows 스토어에 대한 온라인 스토어에 연결하고 Configuration Manager에서 배포할 수 있는 조직을 위한 앱을 가져옵니다.


  이 작업은 [Azure 서버 웹앱](/azure/azure/app-service/app-service-authentication-overview#service-to-service-authentication)을 사용하여 구독 및 구성 세부 정보를 제공함으로써 수행합니다. Azure Web App을 사용하지 않을 경우, Azure에서 새 Configuration Manager 구성 요소 또는 서비스를 설정할 때마다 이러한 세부 정보를 입력해야 합니다. 자세한 내용은 [Azure 서비스 마법사](/sccm/core/servers/deploy/configure/azure-services-wizard)를 참조하세요.

-   Configuration Manager 사이트에 액세스하려면 Azure AD를 사용하여 인터넷에서 클라이언트를 인증합니다. Azure AD를 사용하면 클라이언트 인증 인증서를 구성하고 사용할 필요가 없습니다. 이를 위해서는 클라우드 관리 게이트웨이 사이트 시스템 역할이 필요합니다. 자세한 내용은 [인증을 위해 Azure AD를 사용하여 인터넷에서 Configuration Manager 클라이언트 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)을 참조하세요.

-   인터넷에 있는 컴퓨터에서 Configuration Manager 클라이언트를 설치하고 관리합니다. 이를 위해서는 클라우드 관리 게이트웨이 사이트 시스템 역할을 사용해야 합니다. 자세한 내용은 [인증을 위해 Azure AD를 사용하여 인터넷에서 Configuration Manager 클라이언트 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)을 참조하세요.

-   Azure AD 사용자 검색을 구성합니다.  Azure 서비스 마법사를 사용하여 이 새 검색 방법을 구성합니다. 이 새로운 방법은 기존 검색 데이터와 함께 사용할 수 있는 사용자 데이터를 Azure AD에서 쿼리합니다.  전체 및 델타 동기화 둘 다 지원됩니다.  자세한 내용은 [Azure AD 사용자 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc)을 참조하세요.

### <a name="peer-cache-improvements"></a>피어 캐시 개선
<!-- 1252345 -->
피어 캐시는 더 이상 네트워크 액세스 계정을 사용하여 피어의 다운로드 요청을 인증하지 않습니다. 클라이언트에 해당 계정이 계속 필요할 때 피어 캐시를 사용하는 경우 한 가지 주의할 점이 있습니다. WinPE로 부팅하고 피어 캐시 원본의 콘텐츠에 액세스하는 클라이언트에는 이러한 요구 사항이 계속 적용됩니다. 자세한 내용은 [피어 캐시에 대한 요구 사항 및 고려 사항](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache)을 참조하세요.


<!-- ## Migration  -->


<!-- ## Client management  -->


## <a name="compliance-settings"></a>호환성 설정

### <a name="new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트에서 관리되지 않는 Windows 10 장치에 대한 새 구성 설정
<!-- 1354715 -->
이 릴리스에서는 Intune에 등록되었거나 Configuration Manager를 통해 온-프레미스에서 관리되는 Windows 10 장치에 대한 새 구성 항목 설정을 추가했습니다. 이러한 설정은 다음과 같습니다.

- **암호**
    - 장치 암호화
- **장치**
    - 지역 설정 수정(데스크톱만 해당)
    - 전원 및 절전 모드 설정 수정
    - 언어 설정 수정
    - 시스템 시간 수정
    - 장치 이름 수정
- **스토어**
    - 스토어에서 앱 자동 업데이트
    - 개인 저장소만 사용
    - 스토어에서 시작된 앱 시작
- **Microsoft Edge**
    - 플래그에 대한 액세스 차단
    - SmartScreen 프롬프트 재정의
    - 파일에 대한 SmartScreen 프롬프트 재정의
    - WebRTC 로컬 호스트 IP 주소
    - 기본 검색 엔진
    - OpenSearch XML URL
    - 홈페이지(데스크톱만 해당)

모든 Windows 10 설정에 대한 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Windows 10 및 Windows 8.1 장치에 대한 구성 항목을 만드는 방법](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)을 참조하세요.

### <a name="new-device-compliance-policy-rules"></a>새 장치 준수 정책 규칙

* **필수 암호 유형** 사용자가 영숫자 암호를 만들어야 할지, 아니면 숫자 암호를 만들어야 할지를 지정합니다. 영숫자 암호의 경우 암호에 포함해야 할 각 문자 집합의 최소 수도 지정합니다. 문자 집합으로는 소문자, 대문자, 기호, 숫자 등 4가지가 있습니다.

 **지원됨:**
 * Windows Phone 8+
 * Windows 8.1+
 * iOS 6+
<br></br>
* **장치에서 USB 디버깅 차단** USB 디버깅은 Android for Work 장치에서 이미 사용되지 않도록 설정되어 있으므로 구성할 필요가 없습니다.

 **지원됨:**
 * Android 4.0+
 * Samsung KNOX Standard 4.0 이상
<br></br>
* **알 수 없는 출처의 앱 차단** 장치가 알 수 없는 소스의 앱 설치를 방지해야 합니다. Android for Work 장치는 알 수 없는 출처의 설치를 하상 제한하므로 이 설정은 구성할 필요가 없습니다.

  **지원됨:**
  * Android 4.0+
  * Samsung KNOX Standard 4.0 이상
<br></br>
* **앱에서 위협 검색 필요** 이 설정은 장치에서 앱 확인 기능이 사용되도록 구성되어 있음을 지정합니다.

 **지원됨:**
 * Android 4.2 ~ 4.4
 * Samsung KNOX Standard 4.0 이상

새 장치 준수 규칙을 사용해 보려면 [장치 규정 준수 정책 만들기 및 배포](https://docs.microsoft.com/sccm/mdm/deploy-use/create-compliance-policy)를 참조하세요.

## <a name="application-management"></a>응용 프로그램 관리

### <a name="run-powershell-scripts-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 PowerShell 스크립트 실행
<!-- 1236459 -->

Configuration Manager에서 패키지 및 프로그램을 사용하여 클라이언트 장치에 스크립트를 배포할 수 있습니다. 이 릴리스에서는 다음 작업을 수행할 수 있는 새 기능을 추가했습니다.

- Configuration Manager에 PowerShell 스크립트 가져오기
- Configuration Manager 콘솔에서 스크립트 편집(서명되지 않은 스크립트만 해당)
- 스크립트를 승인 또는 거부로 표시하여 보안 강화
- Windows 클라이언트 PC 및 온-프레미스 관리 Windows PC 컬렉션에 대해 스크립트를 실행합니다. 스크립트는 배포하지 않아도 됩니다. 클라이언트 장치에서 거의 실시간으로 실행됩니다.
- Configuration Manager 콘솔에서 스크립트에 의해 반환된 결과를 검토합니다.

자세한 내용은 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

### <a name="new-mobile-application-management-policy-settings"></a>새 모바일 응용 프로그램 관리 정책 설정    
<!--1324760-->
이 릴리스부터 3개의 새 MAM(모바일 응용 프로그램 관리) 정책 설정을 사용할 수 있습니다.

- **화면 캡처 차단(Android 장치만 해당):** 이 앱을 사용할 때 장치의 화면 캡처 기능을 차단하도록 지정합니다.

새로운 앱 보호 정책 설정을 사용하려면 [Configuration Manager에서 앱 보호 정책을 사용하여 앱 보호](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies)를 참조하세요.


## <a name="operating-system-deployment"></a>운영 체제 배포

### <a name="hardware-inventory-collects-secure-boot-information"></a>하드웨어 인벤토리를 통해 보안 부팅 정보 수집
이제 하드웨어 인벤토리는 클라이언트에서 보안 부팅을 사용할 수 있는지에 대한 정보를 수집합니다. 이 정보는 버전 1702에 도입된 **SMS_Firmware** 클래스에 저장되며 하드웨어 인벤토리에서 기본적으로 사용하도록 설정됩니다. 하드웨어 인벤토리에 대한 자세한 내용은 [하드웨어 인벤토리 구성 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.

### <a name="collapsible-task-sequence-groups"></a>축소 가능한 작업 순서 그룹
이 버전에는 작업 순서 그룹을 확장하고 축소하는 기능이 도입되었습니다. 개별 그룹을 확장 또는 축소하거나, 모든 그룹을 한 번에 확장 또는 축소할 수 있습니다.

### <a name="reload-boot-images-with-current-windows-pe-version"></a>현재 Windows PE 버전을 사용하여 부팅 이미지 다시 로드
이제는 선택한 부팅 이미지에서 **배포 지점 업데이트**를 실행할 때 부팅 이미지의 Windows ADK 설치 디렉터리에서 최신 Windows PE 버전을 다시 로드하도록 선택할 수 있습니다. 자세한 내용은 [부팅 이미지를 사용하여 배포 지점 업데이트](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image)를 참조하세요.

## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="improvements-to-express-update-download-time"></a>빠른 업데이트 다운로드 시간 개선
이 릴리스에서는 빠른 업데이트의 다운로드 시간을 크게 개선했습니다. 자세한 내용은 [Windows 10 업데이트에 대한 빠른 설치 파일 관리](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)를 참조하세요.

### <a name="manage-microsoft-surface-driver-updates"></a>Microsoft Surface 드라이버 업데이트 관리
<!-- 1098490 -->
이제 Configuration Manager를 사용하여 Microsoft Surface 드라이버 업데이트를 관리할 수 있습니다.    


#### <a name="prerequisites"></a>전제 조건
- 모든 소프트웨어 업데이트 지점에서 Windows Server 2016이 실행되어야 합니다.    
- 이 기능은 사용하기 위해 설정해야 하는 시험판 기능입니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease)을 참조하세요.

#### <a name="to-manage-surface-driver-updates"></a>Surface 드라이버 업데이트를 관리하려면

1. Microsoft Surface 드라이버에 대한 동기화를 사용하도록 설정합니다. [분류 및 제품 구성](/sccm/sum/get-started/configure-classifications-and-products)의 절차를 사용하고 **분류** 탭에서 **Microsoft Surface 드라이버 및 펌웨어 업데이트 포함** 확인란을 선택하여 Surface 드라이버를 사용하도록 설정합니다.
2. [Microsoft Surface 드라이버를 동기화](/sccm/sum/get-started/synchronize-software-updates)합니다.
3. [동기화된 Microsoft Surface 드라이버를 배포](/sccm/sum/deploy-use/deploy-software-updates)합니다.

### <a name="configure-windows-update-for-business-deferral-policies"></a>비즈니스용 Windows 업데이트 지연 정책 구성
<!-- 1290890 -->
이제 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 장치에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. **소프트웨어 라이브러리** > **Windows 10 서비스** 아래의 새 **비즈니스용 Windows 업데이트 정책** 노드에서 지연 정책을 관리할 수 있습니다.

자세한 내용은 [Windows 10에서 비즈니스용 Windows 업데이트와 통합](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies)을 참조하세요.

### <a name="improved-user-notifications-for-office-365-updates"></a>Office 365 업데이트에 대한 향상된 사용자 알림
클라이언트가 Office 365 업데이트를 설치할 때 Office 간편 실행 사용자 환경을 활용하도록 개선되었습니다. 여기에는 팝업 및 앱 내 알림과 카운트다운 환경이 포함됩니다. 자세한 내용은 [Office 365 업데이트에 대한 동작 및 클라이언트 알림 다시 시작](/sccm/sum/deploy-use/manage-office-365-proplus-updates#restart-behavior-and-client-notifications-for-office-365-updates)을 참조하세요.

## <a name="reporting"></a>보고

### <a name="use-windows-analytics-with-configuration-manager"></a>Configuration Manager에서 Windows Analytics 사용
<!-- 1318608 -->
Windows Analytics는 Operations Management Suite에서 실행되는 솔루션 모음입니다. 이 솔루션을 사용하여 사용자 환경의 현재 상태에 대한 정보를 얻을 수 있습니다. 사용자 환경의 장치에서 Windows 원격 분석 데이터를 보고합니다. 이 데이터는 Operations Management Suite 웹 포털을 통해 액세스될 수 있습니다. 업그레이드 준비의 경우 Configuration Manager 콘솔의 모니터링 노드에서 직접 데이터를 사용할 수 있습니다.

자세한 내용은 [Configuration Manager에서 Windows Analytics 사용](/sccm/core/clients/manage/monitor-windows-analytics)을 참조하세요.


<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>모바일 장치 관리

### <a name="updates-to-android-for-work-sharing-configuration"></a>Android for Work 공유 구성에 대한 업데이트
<!-- 1338403 -->
이 릴리스에서는 **회사 프로필** 설정 그룹의 **회사 프로필과 개인 프로필 간의 데이터 공유 허용** 설정 값이 업데이트되었습니다. 또한 회사 및 개인 프로필 간의 복사하여 붙여넣기를 차단하기 위한 사용자 지정 설정을 추가했습니다.

자세한 내용은 [Android for Work 장치에 대한 구성 항목](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)을 참조하세요.

### <a name="android-and-ios-enrollment-restrictions"></a>Android 및 iOS 등록 제한
<!-- 1290826 -->
이제 이 릴리스에서 사용자가 개인 Android 또는 iOS 장치를 등록하도록 지정할 수 있습니다. 새 장치 제한 설정을 통해 미리 선언된 장치에 대한 Android 장치 등록을 제한할 수 있습니다. iOS 장치의 경우 Apple의 장비 등록 프로그램, Apple Configurator 또는 Intune 장치 등록 관리자 계정에 등록된 장치를 제외한 모든 장치의 등록을 차단할 수 있습니다.
- Android 등록 제한에 대한 자세한 내용은 [Android 장치 관리 설정](/sccm/mdm/deploy-use/enroll-hybrid-android)을 참조하세요.
- iOS 등록 제한에 대한 자세한 내용은 [iOS 등록 제한 구성](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac#configure-enrollment-restrictions)을 참조하세요.

## <a name="protect-devices"></a>장치 보호

### <a name="include-trust-for-specific-files-and-folders-in-a-device-guard-policy"></a>특정 파일 및 폴더에 대한 트러스트를 Device Guard 정책에 포함
<!--1324676-->
이 릴리스에서는 Device Guard 정책 관리에 기능이 추가되었습니다.

이제 Device Guard 정책에서 필요에 따라 폴더의 특정 파일에 대해 트러스트를 추가할 수 있습니다. 이를 통해 다음을 수행할 수 있습니다.

- 관리되는 설치 관리자 동작 문제 해결
- Configuration Manager로 배포할 수 없는 LOB(기간 업무) 앱 신뢰
- 운영 체제 배포 이미지에 포함된 앱 신뢰

자세한 내용은 [Configuration Manager로 Device Guard 관리](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)를 참조하세요.
