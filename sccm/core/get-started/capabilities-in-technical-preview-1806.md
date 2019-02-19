---
title: Technical Preview 1806
titleSuffix: Configuration Manager
description: Configuration Manager Technical Preview 버전 1806에서 사용할 수 있는 새로운 기능에 대해 알아봅니다.
ms.date: 06/06/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 52d64ef0-8c0d-42c3-857e-07d7ec776f29
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 289cea97990b9f6736f325b153c8bfc375ccea92
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56128656"
---
# <a name="capabilities-in-technical-preview-1806-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1806의 기능

*적용 대상: System Center Configuration Manager(기술 미리 보기)*

이 문서에서는 Configuration Manager용 Technical Preview 버전 1806에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 기술 미리 보기 사이트를 업데이트하고 새 기능을 추가할 수 있습니다. 

이 업데이트를 설치하기 전에 [기술 미리 보기](/sccm/core/get-started/technical-preview) 아티클을 살펴보세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template
## Known Issues in this Technical Preview

### <a name="ki_ANCHOR"></a> Known issue title
<!--bugID--
Issue description and cause.

#### Workaround
Steps to workaround, if any.  
-->
## <a name="known-issues-in-this-technical-preview"></a>이 기술 미리 보기의 알려진 문제

### <a name="ki_contentlib"></a> 사이트는 원격 콘텐츠 라이브러리로 업그레이드 실패
<!--514642--> 사이트는 **cmupdate.log**에서 다음 오류로 인해 업그레이드에 실패합니다.  
```  
Failed to find any valid drives  
GetContentLibraryParameters failed; 0x80070057  
ERROR: Failed to process configuration manager update.  
```  

콘텐츠 라이브러리가 원격 위치에 있는 경우 이 릴리스에서 이 문제가 발생합니다.

#### <a name="workaround"></a>해결 방법
콘텐츠 라이브러리를 사이트 서버의 로컬 드라이브로 이동합니다. 자세한 내용은 [사이트 서버에 대해 원격 콘텐츠 라이브러리 구성](/sccm/core/get-started/capabilities-in-technical-preview-1804#configure-a-remote-content-library-for-the-site-server)을 참조합니다. 



</br>

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  



## <a name="bkmk-3pupdate"></a> 타사 소프트웨어 업데이트
<!--1352101--> 이 릴리스에서는 [UserVoice 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8803711-3rd-party-patching-scup-integration-with-sccm-co)의 결과로서 타사 소프트웨어 업데이트에 대한 지원을 계속 반복합니다. 일부 일반적인 시나리오에 대한 SCUP(System Center Updates Publisher) 사용이 더 이상 필요하지 않습니다. Configuration Manager 콘솔에서 새 **타사 소프트웨어 업데이트 카탈로그** 노드는 타사 카탈로그를 구독하고 소프트웨어 업데이트 지점에 해당 업데이트를 게시한 다음, 클라이언트에 업데이트를 배포할 수 있게 합니다. 

다음의 타사 소프트웨어 업데이트 카탈로그는 이 릴리스에서 사용할 수 있습니다.

 | 게시자 | 카탈로그 이름 |
 |--------|---------------------|
 | HP | HP 클라이언트 업데이트 카탈로그 |

SCUP는 다른 카탈로그 및 시나리오를 계속 지원합니다. Configuration Manager 콘솔의 타사 소프트웨어 업데이트 카탈로그 노드에 있는 카탈로그 목록은 동적이며, 추가 카탈로그가 사용가능하고 지원될 때 업데이트됩니다.


### <a name="prerequisites"></a>필수 구성 요소
- HTTPS 사용 소프트웨어 업데이트 지점을 사용하여 소프트웨어 업데이트 관리를 설정합니다. 자세한 내용은 [소프트웨어 업데이트 관리 준비](/sccm/sum/get-started/prepare-for-software-updates-management)를 참조하세요.  
  - 소프트웨어 업데이트 지점은 이 릴리스에서 이 기능에 대한 사이트 서버에 있어야 합니다. <!--515810--> 

    > [!Tip]  
    > 서명 인증서를 처리하는 데 사용되는 WSUS API에 대한 요구 사항이 있기 때문에 소프트웨어 업데이트 지점에는 HTTPS가 필요합니다. 클라이언트에도 HTTPS를 설정할 필요가 없습니다. WSUS에서 HTTPS를 사용하도록 설정하는 방법은 지원하기 위한 다음 문서를 참조하세요.  
    > - [Secure Sockets Layer 프로토콜을 사용한 WSUS 보안](/windows-server/administration/windows-server-update-services/deploy/2-configure-wsus#bkmk_2.5.ConfigSSL) 
    > - [WSUS 지원 블로그 게시물](https://blogs.technet.microsoft.com/sus/2011/05/09/how-to-create-an-internet-facing-wsus-server-that-uses-different-internal-and-external-names/)

- 타사 소프트웨어 업데이트에 대한 원본 이진 콘텐츠를 저장하려면 소프트웨어 업데이트 지점인 WSUSContent 폴더에 충분한 디스크 공간이 있어야 합니다. 필요한 스토리지 양은 공급 업체, 업데이트 유형 및 배포를 위해 게시하는 특정 업데이트에 따라 다릅니다. 더 많은 여유 공간을 사용하여 WSUSContent 폴더를 다른 드라이브로 이동해야 하는 경우 WSUS 지원 팀의 블로그 게시물 [WSUS가 로컬로 업데이트를 저장하는 위치를 변경하는 방법](https://blogs.technet.microsoft.com/sus/2008/05/19/wsus-how-to-change-the-location-where-wsus-stores-updates-locally/)을 참조합니다.  

- **소프트웨어 업데이트** 그룹에서 [타사 소프트웨어 업데이트 사용](/sccm/core/clients/deploy/about-client-settings#enable-third-party-software-updates) 클라이언트 설정을 사용하고 배포합니다.  

- 사이트 서버는 HTTPS 포트 443을 통한 download.microsoft.com에 인터넷 액세스가 필요합니다. 타사 소프트웨어 업데이트 동기화 서비스는 현재 사이트 서버에서 실행됩니다. 게시될 때 업데이트를 구독하고 다운로드하는 경우 이 서비스는 사용 가능한 타사 카탈로그 목록을 업데이트하고 해당 카탈로그를 다운로드합니다. 필요한 경우 사이트 서버 컴퓨터의 사이트 시스템 역할 속성 **프록시** 탭에서 인터넷 프록시 설정을 구성합니다.  


### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.


#### <a name="phase-1-enable-and-set-up-the-feature"></a>1단계: 기능 사용 및 설정
사용을 위해 해당 기능을 설정하고 사용하려면 *계층당 한 번씩* 다음 단계를 수행합니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 계층에서 최상위 사이트를 선택합니다. 리본에서 **사이트 구성 요소 구성**를 클릭하고 **소프트웨어 업데이트 지점**을 선택합니다.  

3. **타사 업데이트** 탭으로 전환합니다. **타사 소프트웨어 업데이트 사용** 옵션을 선택합니다. 인증서 옵션에 대 한 자세한 내용은 [타사 소프트웨어 업데이트 지원 개선 사항](/sccm/core/get-started/capabilities-in-technical-preview-1805#improvements-for-enabling-third-party-software-update-support)을 참조하십시오.  

   > [!Note]  
   > 이 인증서를 관리하기 위해 Configuration Manager에 대한 기본 옵션을 사용하는 경우 새 인증서 형식인 **타사 WSUS 서명**이 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에서 만들어집니다.  


#### <a name="phase-2-subscribe-to-a-third-party-catalog-and-sync-updates"></a>2단계: 타사 카탈로그 구독 및 업데이트 동기화
구독하려는 *각 타사 카탈로그*에 대한 다음 단계를 수행합니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동합니다. **소프트웨어 업데이트**를 확장해 **타사 소프트웨어 업데이트 카탈로그** 노드를 선택합니다.  

2. 구독할 카탈로그를 선택하고 리본 메뉴에서 **카탈로그 구독**을 클릭합니다.   

3. 카탈로그 인증서를 검토하고 승인합니다.  

   > [!Note]  
   > 타사 소프트웨어 업데이트 카탈로그를 구독하면 마법사에서 검토하고 승인하는 인증서가 사이트에 추가됩니다. 이 인증서는 **타사 소프트웨어 업데이트 카탈로그** 형식입니다. 이 인증서를 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에서 관리할 수 있습니다.  

4. 마법사를 완료합니다.  

   > [!Tip]  
   > 초기 구독 후 카탈로그를 즉시 다운로드해야 합니다. 그런 다음, 이 릴리스에서 24시간마다 다시 동기화합니다. 카탈로그가 자동으로 다운로드되기를 기다리지 않으려면 리본 메뉴에서 **지금 동기화**를 클릭합니다.  
   > 
   > 카탈로그를 다운로드한 후 제품 메타데이터를 소프트웨어 업데이트 지점에 동기화해야 합니다. 이 프로세스 및 수동으로 시작하는 방법에 대한 자세한 내용은 [소프트웨어 업데이트 동기화](/sccm/sum/get-started/synchronize-software-updates)를 참조합니다. 이 시점에 **모든 업데이트** 노드에서 타사 업데이트를 확인할 수 있습니다. 

5. 다음으로 구독한 타사 카탈로그에 대한 소프트웨어 업데이트 지점 **제품**을 구성합니다. 자세한 내용은 [동기화할 분류 및 제품 구성](/sccm/sum/get-started/configure-classifications-and-products)을 참조하세요. 제품 조건이 변경된 후 소프트웨어 업데이트 동기화는 다시 일어나야 합니다.

클라이언트에서 준수 결과를 확인할 수 있기 전에 업데이트를 검사하고 평가해야 합니다. **소프트웨어 업데이트 검사 주기**를 실행하여 클라이언트의 Configuration Manager 제어판에서 이 주기를 수동으로 트리거할 수 있습니다. 프로세스에 대한 자세한 내용은 [소프트웨어 업데이트 소개](/sccm/sum/understand/software-updates-introduction)를 참조하십시오.


#### <a name="phase-3-deploy-third-party-software-updates"></a>3단계: 타사 소프트웨어 업데이트 배포
클라이언트에 배포하려는 *모든 타사 소프트웨어 업데이트*에 대해 다음 단계를 수행합니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동합니다. **소프트웨어 업데이트**를 확장해 **모든 소프트웨어 업데이트** 노드를 선택합니다.  

   > [!Tip]  
   > **조건 추가**를 클릭하여 업데이트 목록을 필터링합니다. 예를 들어 Adobe에서 모든 업데이트를 보려면 **Adobe Systems, Inc.** 에 대한 **공급 업체**를 추가합니다.  

2. 클라이언트에서 필요한 업데이트를 선택합니다. **타사 소프트웨어 업데이트 콘텐츠 게시**를 클릭하고 SMS_ISVUPDATES_SYNCAGENT.log에서 진행률을 검토합니다. 이 작업은 공급 업체에서 업데이트 바이너리를 다운로드하여 소프트웨어 업데이트 지점의 WSUSContent 폴더에 저장합니다. 업데이트 상태를 메타데이터 전용에서 배포 가능한 콘텐츠로 변경합니다.  

   > [!Note]  
   > 타사 소프트웨어 업데이트 콘텐츠를 게시하면 콘텐츠 서명에 사용된 모든 인증서가 사이트에 추가됩니다. 이러한 인증서는 **타사 소프트웨어 업데이트 콘텐츠** 형식입니다. 이 인증서를 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에서 관리할 수 있습니다.  

3. 기존 소프트웨어 업데이트 관리 프로세스를 사용하여 업데이트를 배포합니다. 자세한 내용은 [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)를 참조하세요. 소프트웨어 업데이트 배포 마법사의 **다운로드 위치** 페이지에서 **인터넷에서 소프트웨어 업데이트 다운로드**하기 위한 기본 옵션을 선택합니다. 이 시나리오에서 콘텐츠는 배포 패키지의 콘텐츠를 다운로드하는 데 사용되는 소프트웨어 업데이트 지점에 게시됩니다.


### <a name="monitoring-progress-of-third-party-software-updates"></a>타사 소프트웨어 업데이트의 진행률 모니터링
타사 소프트웨어 업데이트 동기화는 사이트 서버에서 SMS_ISVUPDATES_SYNCAGENT 구성 요소에 의해 처리됩니다. 이 구성 요소에서 상태 메시지를 보거나 SMS_ISVUPDATES_SYNCAGENT.log에서 자세한 상태를 확인할 수 있습니다. 이 로그는 사이트 설치 디렉터리의 **로그** 하위 폴더의 사이트 서버에 있습니다. 기본 포트는 `C:\Program Files\Microsoft Configuration Manager\Logs`입니다. 일반 소프트웨어 업데이트 관리 프로세스 모니터링에 대한 자세한 내용은 [소프트웨어 업데이트 모니터링](/sccm/sum/deploy-use/monitor-software-updates)을 참조하십시오.


### <a name="known-issues"></a>알려진 문제
- 타사 소프트웨어 업데이트 동기화 서비스는 **WSUS 서버 연결 계정**을 사용하기 위해 구성된 소프트웨어 업데이트 지점을 지원하지 않습니다. 이 계정을 소프트웨어 업데이트 지점 속성 페이지의 **프록시 및 계정 설정** 탭에서 구성한 경우 SMS_ISVUPDATES_SYNCAGENT.log에서 다음과 같은 오류가 표시됩니다.  
`WSUS access account appears to be configured, it is not yet supported for third party updates sync.`  
이 계정에 대한 자세한 내용은 [소프트웨어 업데이트 지점 연결 계정](/sccm/core/plan-design/hierarchy/accounts#software-update-point-connection-account)을 참조하십시오.<!--515492-->  

- 새로 통합된 이 타사 소프트웨어 업데이트 기능과 SCUP 같은 다른 도구의 사용을 혼합하지 마십시오. 타사 소프트웨어 업데이트 동기화 서비스는 SCUP 같은 다른 애플리케이션, 도구 또는 스크립트가 WSUS에 추가한 메타데이터 전용 업데이트에 콘텐츠를 게시할 수 없습니다. **타사 소프트웨어 업데이트 콘텐츠 게시** 작업은 이러한 업데이트에서 실패합니다. 이 기능은 아직 지원하지 않는 타사 업데이트를 배포해야 하는 경우 해당 업데이트를 배포 하는 데 기존 프로세스 전체를 사용합니다.<!--515497-->  



## <a name="configure-windows-defender-smartscreen-settings-for-microsoft-edge"></a>Microsoft Edge용 Windows Defender SmartScreen 설정 구성
<!--1353701--> 이 릴리스는 [Windows Defender SmartScreen](/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview)의 세 가지 설정을 [Microsoft Edge 브라우저 규정 준수 설정 정책](/sccm/compliance/deploy-use/browser-profiles)에 추가합니다. 해당 정책에는 **SmartScreen 설정** 페이지에 다음과 같은 추가 정책이 포함됩니다.
- **SmartScreen 허용**: Windows Defender SmartScreen 허용되는지 여부를 지정합니다. 자세한 내용은 참조는 [AllowSmartScreen 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)을 참조합니다.
- **사용자는 사이트에서 SmartScreen 프롬프트를 재정의할 수 있음**: 사용자가 잠재적으로 악성인 웹 사이트에 대한 Windows Defender SmartScreen 필터 경고를 재정의할 수 있는지 여부를 지정합니다. 자세한 내용은 [PreventSmartScreenPromptOverride 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)을 참조합니다.
- **사용자는 파일에서 SmartScreen 프롬프트를 재정의할 수 있음**: 사용자가 확인되지 않은 파일 다운로드에 대한 Windows Defender SmartScreen 필터 경고를 재정의할 수 있는지 여부를 지정합니다. 자세한 내용은 [PreventSmartScreenPromptOverrideForFiles 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)을 참조합니다.



## <a name="sync-mdm-policy-from-microsoft-intune-for-a-co-managed-device"></a>Microsoft Intune에서 공동 관리하는 디바이스에 대한 MDM 정책 동기화
<!--1357377--> 이 릴리스부터 [공동 관리 워크로드를 전환](/sccm/core/clients/manage/co-management-switch-workloads)할 경우 공동 관리되는 디바이스는 Microsoft Intune에서 자동으로 MDM 정책을 동기화합니다. 이 동기화는 Configuration Manager 콘솔의 클라이언트 알림에서 **컴퓨터 정책 다운로드** 작업 시작할 때 발생합니다. 자세한 내용은 [클라이언트 알림을 사용하여 클라이언트 정책 검색 시작](/sccm/core/clients/manage/manage-clients#initiate-client-policy-retrieval-using-client-notification)을 참조합니다.



## <a name="transition-office-365-workload-to-intune-using-co-management"></a>공동 관리를 사용하여 Office 365 워크로드를 Intune으로 전환
<!--1357841--> 이제 공동 관리를 사용하도록 설정한 후에 Configuration Manager에서 Microsoft Intune으로 Office 365 워크로드를 전환할 수 있습니다. 이 워크로드를 전환하려면 공동 관리 속성 페이지로 이동하고 슬라이더 막대를 Configuration Manager에서 파일럿 또는 모두로 이동합니다. 자세한 내용은 [Windows 10 디바이스의 공동 관리](/sccm/core/clients/manage/co-management-overview)를 참조하세요.

**장치에서 Intune으로 Office 365 응용 프로그램 관리**라는 새 글로벌 조건이 있습니다. 이 조건은 기본적으로 새 Office 365 애플리케이션에 대한 요구 사항으로 추가됩니다. 이 워크로드를 전환하는 경우 공동 관리되는 클라이언트는 애플리케이션의 요구 사항을 충족하지 못하므로 Configuration Manager를 통해 배포된 Office 365를 설치하지 마십시오.

### <a name="known-issue"></a>알려진 문제
- 이 워크로드 전환은 현재 Office 365 배포에만 적용됩니다. Configuration Manager가 Office 365 업데이트를 계속 관리합니다.<!--510876--> 가능한 해결 방법을 포함한 자세한 내용은 Configuration Manager 버전 1802 릴리스 정보, [Office 365 클라이언트 설정 변경이 적용되지 않습니다](/sccm/core/servers/deploy/install/release-notes#changing-office-365-client-setting-doesnt-apply)를 참조합니다.



## <a name="package-conversion-manager"></a>Package Conversion Manager 
<!--1357861--> Package Conversion Manager는 레거시 Configuration Manager 2007 패키지를 Configuration Manager 현재 분기 애플리케이션으로 변환할 수 있는 통합 도구입니다. 이와 같은 변환을 수행한 후에는 종속성, 요구 사항 규칙, 사용자 디바이스 선호도 등의 응용 프로그램 기능을 사용할 수 있습니다.

> [!Tip]  
> Package Conversion Manager의 기존 기능에 대한 레거시 설명서는 [TechNet](https://technet.microsoft.com/library/hh531519.aspx)에서 확인할 수 있습니다. 관련 정보는 docs.microsoft.com 라이브러리로 마이그레이션 중입니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

> [!Important]  
> 이전 버전의 Package Conversion Manager를 전에 설치한 경우 먼저 이를 제거한 후 사이트를 업그레이드합니다. 통합된 새 버전이 설치를 요구하지 않지만 기존 버전과 충돌할 수 있습니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동합니다. **응용 프로그램 관리**를 확장하고 **패키지**를 선택합니다.  
2. 패키지를 선택하십시오. 리본 메뉴의 **패키지 변환** 그룹에서 다음 세 가지 옵션을 사용할 수 있습니다.  
     - **패키지 분석**: 패키지를 분석하여 변환 프로세스를 시작합니다.
     - **패키지 변환**: 이 작업으로 일부 패키지를 애플리케이션으로 쉽게 변환할 수 있습니다.
     - **수정 및 변환**: 일부 패키지에서는 애플리케이션으로 변환하기 전에 문제를 수정해야 합니다.  

   이러한 작업에 대한 자세한 내용은 [패키지 변환 및 분석 방법](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/hh846244%28v%3dtechnet.10%29)을 참조하십시오.  

3. **모니터링** 작업 영역으로 이동하여 **패키지 변환 상태**를 선택합니다. 이 새 대시보드는 사이트에 패키지의 전반적인 분석 및 변환 상태를 표시합니다. 새 백그라운드 작업은 자동으로 분석 데이터를 요약합니다.  

   > [!Tip]  
   > Package Conversion Manager는 패키지의 분석 예약을 요구하지 않습니다. 이제 통합된 요약 작업에서 이 작업을 처리합니다.  

![패키지 변환 상태 대시보드 스크린샷](media/1357861-pcm-dashboard.png)



## <a name="deploy-software-updates-without-content"></a>콘텐츠 없이 소프트웨어 업데이트 배포
<!--1357933--> 이제 소프트웨어 업데이트 콘텐츠를 배포 지점에 먼저 다운로드하여 배포하지 않고 디바이스에 소프트웨어 업데이트를 배포할 수 있습니다. 이 기능은 매우 큰 업데이트 콘텐츠를 처리할 때 또는 항상 클라이언트가 Microsoft 업데이트 클라우드 서비스에서 콘텐츠를 가져오려 할 때 유용합니다. 이 시나리오에서 클라이언트는 이미 필요한 콘텐츠가 있는 피어로부터 콘텐츠를 다운로드할 수 있습니다. Configuration Manager 클라이언트는 계속 콘텐츠 다운로드를 관리하므로 Configuration Manager 피어 캐시 기능 또는 배달 최적화 같은 다른 기술을 활용할 수 있습니다. 이 기능은 Windows 및 Office 업데이트를 포함하여 Configuration Manager 소프트웨어 업데이트 관리에서 지원하는 모든 업데이트 유형을 지원합니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. 기본 단위 소프트웨어 업데이트 배포를 시작합니다. 자세한 내용은 [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)를 참조하세요.
2. 소프트웨어 업데이트 배포 마법사의 **배포 패키지** 페이지에서 **배포 패키지 아님**에 대한 새 옵션을 선택합니다.

### <a name="known-issues"></a>알려진 문제
- 이 설정으로 배포된 업데이트에 대한 아이콘은 마치 업데이트가 잘못된 것처럼 부정확하게 빨간색 X로 표시됩니다. 자세한 내용은 [소프트웨어 업데이트에 사용된 아이콘](/sccm/sum/understand/software-updates-icons)을 참조하세요. <!--515556-->  
- 이 설정은 소프트웨어 업데이트 배포 마법사와만 통합됩니다. 자동 배포 규칙은 현재 사용할 수 없습니다. <!--515558-->  



## <a name="office-customization-tool-integration-with-the-office-365-installer"></a>Office 365 설치 관리자와 Office 사용자 지정 도구 통합
<!--1358149--> Office 사용자 지정 도구는 Configuration Manager 콘솔에서 Office 365 설치 관리자와 통합됩니다. Office 365에 대한 배포를 만들 때 최신 Office 관리 효율성 설정을 이제 동적으로 구성할 수 있습니다. Office 사용자 지정 도구는 새로운 빌드의 Office 365의 릴리스와 동시에 업데이트됩니다. Office 365에서 새 관리 효율성 설정은 사용할 수 있으면 바로 활용할 수 있습니다. 

### <a name="prerequisites"></a>필수 구성 요소
- Configuration Manager 콘솔을 실행하는 컴퓨터는 HTTPS 포트 443을 통한 인터넷 액세스가 필요합니다. Office 365 클라이언트 설치 마법사는 Windows 표준 웹 브라우저 API를 사용하여 https://config.office.com을 엽니다. 인터넷 프록시를 사용하는 경우 사용자는 이 URL에 액세스할 수 있어야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **Office 365 클라이언트 관리** 노드를 선택합니다.
2. Office 365 클라이언트 설치 마법사를 시작하려면 대시보드에서 **Office 365 설치 관리자** 타일을 클릭합니다. 자세한 내용은 [Office 365 앱 배포](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)를 참조하세요.
3. **Office 설정** 페이지에서 **Office 웹 페이지로 이동**을 클릭합니다. 온라인 Office 사용자 지정 도구를 사용하여 이 배포에 대한 설정을 지정합니다. 
4. 완료되면 상단 오른쪽 모서리에서 **제출**을 클릭합니다. Office 365 클라이언트 설치 마법사를 마칩니다.



## <a name="improvements-to-cloud-management-gateway"></a>클라우드 관리 게이트웨이드의 향상된 기능
이 릴리스에서 CMG(클라우드 관리 게이트웨이)에 포함된 향상된 기능은 다음과 같습니다.

### <a name="simplified-client-bootstrap-command-line"></a>간소화된 클라이언트 부트스트랩 명령줄
<!--1358215--> 이제 CMG를 통해 Configuration Manager 클라이언트를 인터넷에 설치할 때 명령줄 속성이 거의 필요하지 않습니다. 이 시나리오의 한 가지 예에 대한 자세한 내용은 공동 관리를 준비하는 경우 [Configuration Manager 클라이언트를 설치하는 명령줄](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client)을 참조합니다. 

모든 시나리오에서 다음 명령줄 속성이 필요합니다.
  - CCMHOSTNAME  
  - SMSSITECODE  

다음 속성은 PKI 기반의 클라이언트 인증 인증서 대신 클라이언트 인증용 Azure AD를 사용하는 경우 필요합니다.
  - AADCLIENTAPPID  
  - AADRESOURCEURI  

클라이언트가 인트라넷으로 다시 로밍되는 경우 다음 속성이 필요합니다.
  - SMSMP  

다음 예제에서는 위의 속성 모두를 포함합니다.   
`ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com`

자세한 내용은 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties)을 참조합니다.

### <a name="download-content-from-a-cmg"></a>CMG에서 콘텐츠 다운로드
<!--1358651--> 이전에 클라우드 배포 지점 및 CMG를 별도 역할로 배포해야 했습니다. 이제 이 릴리스에서 CMG는 클라이언트에게 콘텐츠를 제공할 수 있습니다. 이 기능은 필요한 인증서 및 Azure VM 비용을 줄여줍니다. 이 기능을 사용하려면 CMG 속성의 **설정** 탭에서 **CMG가 클라우드 배포 지점으로 기능하고 Azure 스토리지에서 콘텐츠를 제공하도록 허용**하는 새 옵션을 사용하도록 설정합니다. 

### <a name="trusted-root-certificate-isnt-required-with-azure-ad"></a>신뢰할 수 있는 루트 인증서는 Azure AD에서 필요하지 않음
<!--503899--> CMG를 만들 경우 설정 페이지에서 [신뢰할 수 있는 루트 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-trusted-root-certificate-to-clients)를 더 이상 제공할 필요가 없습니다. 이 인증서는 클라이언트 인증용 Azure AD(Azure Active Directory)를 사용할 때 필요하지 않지만 마법사에서는 필요합니다.

> [!Important]  
> PKI 클라이언트 인증 인증서를 사용하는 경우 여전히 신뢰할 수 있는 루트 인증서를 CMG에 추가해야 합니다.



## <a name="improvements-to-secure-client-communications"></a>보안 클라이언트 통신 개선
<!--1358278,1358279--> 이 릴리스에서는 네트워크 액세스 계정에서 추가 종속성을 제거하여 [개선된 보안 클라이언트 통신](/sccm/core/get-started/capabilities-in-technical-preview-1805#improved-secure-client-communications)을 계속 반복합니다. 에 새 사이트 옵션을 설정 하면 **HTTP 사이트 시스템에 대한 Configuration Manager 생성 인증서 사용**하기 위해 새 사이트 옵션을 사용하는 경우 다음과 같은 시나리오는 배포 지점에서 콘텐츠를 다운로드하기 위한 네트워크 액세스 계정이 필요하지 않습니다.  

- 부팅 미디어 또는 PXE에서 실행하는 작업 순서
- 소프트웨어 센터에서 실행하는 작업 순서  

이러한 작업 순서는 OS 배포 또는 사용자 지정용일 수 있습니다. 작업 그룹 컴퓨터에도 지원됩니다.



## <a name="software-center-infrastructure-improvements"></a>소프트웨어 센터 인프라 개선 사항
<!--1358309--> 소프트웨어 센터에 사용자가 사용할 수 있는 애플리케이션을 표시하는 데 더 이상 애플리케이션 카탈로그 역할이 필요하지 않습니다. 이 변경은 사용자에게 애플리케이션을 전달하기 위해 필요한 서버 인프라를 줄일 수 있습니다. 소프트웨어 센터는 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups#management-points)에 할당하여 대규모 환경의 크기 조정을 더 잘하도록 도움을 주는 이 정보를 얻으려면 관리 지점에 의존합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. 사이트에서 모든 응용 프로그램 카탈로그 역할을 제거합니다. 이러한 역할에는 응용 프로그램 카탈로그 웹 서비스 지점 및 응용 프로그램 카탈로그 웹 사이트 지점이 포함됩니다.
2. 사용자 컬렉션이 사용할 수 있는 애플리케이션으로 배포합니다.
3. 소프트웨어 센터를 찾아볼 대상으로 지정된 사용자로 사용하고 요청하고 응용 프로그램을 설치합니다.

### <a name="known-issue"></a>알려진 문제
- 이 기능을 사용하여 Azure Active Directory에 가입된 클라이언트를 사용하는 경우 **HTTP 사이트 시스템에 대해 Configuration Manager에서 생성된 인증서를 사용**하려면 사이트를 구성하지 마십시오. 현재 이 기능과 충돌합니다.<!--515846--> 이 설정에 대한 자세한 내용은 [개선된 보안 클라이언트 통신](/sccm/core/get-started/capabilities-in-technical-preview-1805#improved-secure-client-communications)을 참조하십시오.



## <a name="provision-windows-app-packages-for-all-users-on-a-device"></a>디바이스의 모든 사용자에 대해 Windows 앱 패키지 프로비전
<!--1358310--> 이제 디바이스에서 모든 사용자에 대한 Windows 앱 패키지를 사용하여 애플리케이션을 프로비전할 수 있습니다. 이 시나리오의 일반적인 한 예는 Minecraft 교육용 버전처럼 비즈니스 및 교육용 Microsoft Store의 앱을 학교에서 학생들이 사용하는 모든 디바이스에 프로비전하는 것입니다. 전에 Configuration Manager는 사용자 당 이러한 애플리케이션 설치만 지원했습니다. 새 디바이스에 로그인한 후 학생은 앱에 액세스하기를 기다려야 합니다. 앱이 모든 사용자용 디바이스에 프로비전되는 경우 더 신속하게 생산적이 될 수 있습니다.

> [!Important]  
> 디바이스에 다른 버전의 동일한 Windows 앱 패키지의 설치, 프로비저닝 및 업데이트 시 예기치 않은 결과가 발생할 수 있으니 주의하십시오. 이 동작은 앱을 프로비전하기 위해 Configuration Manager를 사용하는 경우에 발생할 수 있지만 사용자는 Microsoft 스토어에서 앱을 업데이트할 수 있습니다. 자세한 내용은 [비즈니스용 Microsoft Store에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#next-steps)할 때 다음 단계 지침을 참조하세요.  

오프라인 라이선스 앱을 프로비전하면 Configuration Manager는 Windows가 Microsoft Store에서 자동으로 업데이트하도록 허용하지 않습니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. 새 응용 프로그램을 만듭니다. 이 앱은 비즈니스 및 교육용 Microsoft Store에서 동기화된 Windows 앱 패키지 또는 오프라인 라이선스 앱에서 온 것이어야 합니다.  

2. 응용 프로그램 만들기 마법사의 **일반 정보** 페이지에서 **디바이스에서 모든 사용자에 대해 이 응용 프로그램을 프로비전**하는 옵션을 사용합니다.  

   > [!Tip]  
   > 기존 애플리케이션을 수정하는 경우 이 설정은 애플리케이션 속성의 **사용자 경험** 탭에 있습니다.  

3. 디바이스 컬렉션에 응용 프로그램을 배포합니다.  

4. 다른 사용자 계정으로 대상 디바이스에 로그인하고 응용 프로그램을 시작합니다.  

> [!Note]  
> 사용자가 이미 로그인한 디바이스에서 프로비전된 응용 프로그램을 제거해야 할 경우 두 개의 제거 배포를 만들어야 합니다. 첫 번째 제거 배포를 디바이스를 포함하는 디바이스 컬렉션의 대상으로 지정합니다. 두 번째 제거 배포를 프로비전된 응용 프로그램을 사용하여 디바이스에 이미 로그인한 사용자를 포함하는 사용자 컬렉션의 대상으로 지정합니다. 디바이스에서 프로비전된 앱을 제거하는 경우 Windows는 현재 사용자를 위해 해당 앱을 제거하지 않습니다. 



## <a name="improvements-to-the-surface-dashboard"></a>Surface 대시보드에 대한 개선 사항
<!--1358654--> 이 릴리스에 포함된 [Surface 대시보드](/sccm/core/clients/manage/surface-device-dashboard)에 대한 향상된 기능은 다음과 같습니다.
- 그래프 섹션을 선택하면 이제 Surface 대시보드에 관련 디바이스 목록이 표시됩니다.
   - **Surface 디바이스 비율** 타일을 클릭하면 Surface 디바이스 목록이 열립니다.
   - **상위 5개 펌웨어 버전** 타일에서 막대를 클릭하면 해당 특정 펌웨어 버전으로 Surface 디바이스 목록이 열립니다.
- Surface 대시보드에서 이러한 디바이스 목록을 볼 때 디바이스를 마우스 오른쪽 단추로 클릭하고 일반 작업을 수행할 수 있습니다.



## <a name="hardware-inventory-default-unit-revision"></a>하드웨어 인벤토리 기본 단위 수정 버전
<!--514442-->[Configuration Manager 버전 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710#site-infrastructure)에서 많은 보고 보기에 사용된 기본 단위는 메가바이트(MB)에서 기가바이트(GB)로 변경됐습니다. [큰 정수 값에 대한 하드웨어 인벤토리의 향상된 기능](/sccm/core/get-started/capabilities-in-technical-preview-1805#improvement-to-hardware-inventory-for-large-integer-values) 때문에 또한 고객 의견에 따라 이 기본 단위는 다시 MB로 됩니다.



## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
