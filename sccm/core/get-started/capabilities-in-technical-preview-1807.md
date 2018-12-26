---
title: Technical Preview 1807
titleSuffix: Configuration Manager
description: Configuration Manager Technical Preview 분기 버전 1807에서 사용할 수 있는 새로운 기능에 대해 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bcde47a7-433e-4944-964b-539b17d15d64
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9095bdf431525a66a570267c4fff07a382a16fe4
ms.sourcegitcommit: af4f8bd8dffe6fb05f51322ea9e94d335a2cc0c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39360773"
---
# <a name="capabilities-in-configuration-manager-technical-preview-version-1807"></a>Configuration Manager Technical Preview 버전 1807의 기능 

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 Configuration Manager Technical Preview 버전 1807에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 기술 미리 보기 사이트를 업데이트하고 새 기능을 추가합니다. 

이 업데이트를 설치하기 전에 [기술 미리 보기](/sccm/core/get-started/technical-preview) 문서를 살펴보세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template
## Known issues 

### <a name="ki_ANCHOR"></a> Known issue title
<!--bugID--
Issue description and cause.

#### Workaround
Steps to workaround, if any.  
-->



## <a name="known-issues"></a>알려진 문제 

### <a name="ki_o365"></a> Office 365 소프트웨어 업데이트 관련 문제
<!--521365--> Technical Preview 분기 버전 1806 및 1806.2를 사용하여 Office 365 업데이트를 관리하는 경우 업데이트가 클라이언트에 설치되지 않을 수 있습니다. 

#### <a name="workaround"></a>해결 방법
- Office 365용 기존 배포 패키지 및 소프트웨어 업데이트 그룹을 삭제합니다.  

- 2018년 7월 31일부터, Office 365 소프트웨어 업데이트를 동기화하고 최신 업데이트만 배포합니다.  



</br>

**다음 섹션에서는 이 버전에서 소개된 새로운 기능을 설명합니다.**  


## <a name="bkmk_hub"></a> 커뮤니티 허브
<!--1357766-->

커뮤니티 허브는 다른 사용자와 유용한 구성 관리자 개체를 공유하기 위한 중앙 위치입니다. Configuration Manager 콘솔에서 새 **커뮤니티** 작업 영역을 확인하고 **허브** 노드를 선택합니다. 커뮤니티 허브를 사용하여 다음 형식의 구성 관리자 개체를 다운로드합니다. 
- 스크립트
- 구성 항목

![Configuration Manager 콘솔, 커뮤니티 작업 영역, 허브 노드](media/1357766-hub.png)

사용 가능한 항목에 대한 자세한 정보를 보려면 허브에서 해당 항목을 클릭합니다. 세부 정보 페이지에서 **다운로드**를 클릭하여 항목을 가져옵니다. 허브에서 항목을 다운로드하면 항목이 사이트에 자동으로 추가됩니다. 

![Configuration Mnager 콘솔, 커뮤니티 작업 영역, 허브 노드, 세부 정보 페이지](media/1357766-hub-details.png)

**커뮤니티** 작업 영역에는 다음 노드도 포함됩니다.

- **문서**: Configuration Manager [문서 라이브러리](https://docs.microsoft.com/sccm/)를 표시합니다.  

- **피드백**: Configuration Manager [UserVoice 사이트](https://configurationmanager.uservoice.com/)를 표시합니다.  


### <a name="prerequisites"></a>필수 구성 요소

- 클라이언트 OS에서 Configuration Manager 콘솔을 사용합니다.  

    - 선택할 수 있지만 권장하지 않음: 서버에서 [Internet Explorer: 고급 보안 구성](https://go.microsoft.com/fwlink/?LinkId=253461)을 사용하지 않도록 설정합니다.  

- 콘솔이 있는 컴퓨터는 인터넷 액세스가 필요하고 다음 사이트에 연결해야 합니다.  
    - `https://aka.ms`  
    - `https://comfigmgr-hub.azurewebsites.net`  
    - `https://configmgronline.visualstudio.com`  


### <a name="known-issue"></a>알려진 문제

이 버전에서는 항목을 허브에 포함하는 기능이 현재 제공되지 않습니다. 



## <a name="bkmk_osd"></a> 오프라인 OS 이미지 서비스용 드라이브 지정  
<!--1358924-->

[UserVoice 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/33506009-gui-option-for-offline-os-image-servicing-drive)을 기반으로 OS 이미지의 오프라인 서비스 제공 중에 Configuration Manager가 사용하는 드라이브를 지정합니다. 이 프로세스에서는 임시 파일이 있는 큰 디스크 공간을 사용할 수 있으므로 이 옵션을 통해 사용할 드라이브를 유연하게 선택할 수 있습니다. 


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, 기능에 대한 의견이 포함된 [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 보내주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 리본에서 **사이트 구성 요소 구성**을 클릭하고 **소프트웨어 업데이트 지점**을 선택합니다.  

2. **오프라인 서비스** 탭으로 전환하고 **이미지의 오프라인 설치에서 사용할 로컬 드라이브**의 옵션을 지정합니다.  

기본적으로 이 설정은 **자동**입니다. 이 값을 사용하면 Configuration Manager가 설치된 드라이브를 선택합니다. 

오프라인 서비스를 제공하는 동안 Configuration Manager는 임시 파일을 `<drive>:\ConfigMgr_OfflineImageServicing` 폴더에 저장합니다. 또한 이 폴더에 OS 이미지를 탑재합니다. 

**OfflineServicingMgr.log** 로그 파일을 검토합니다. 



## <a name="bkmk_comgmt"></a> Intune에서 공동 관리되는 장치 동기화 작업
<!--1358565-->

공동으로 관리하는 디바이스가 Microsoft Intune에서 활성화되었는지 여부를 Configuration Manager 콘솔에 표시합니다. 이 상태는 [Intune 데이터 웨어하우스](https://docs.microsoft.com/intune/reports-nav-create-intune-reports)의 데이터를 기반으로 합니다. Configuration Manager 콘솔의 **클라이언트 상태** 대시보드에 **Intune을 사용하는 비활성 클라이언트**가 표시됩니다. 이 새 범주는 Configuration Manager에서 비활성 상태이나 지난주에 Intune 서비스와 동기화된 공동 관리되는 디바이스에 해당합니다.


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, 기능에 대한 의견이 포함된 [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 보내주세요.

공동 관리를 사용하도록 사이트를 이미 설정한 경우: 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다. 리본에서 **속성**을 클릭합니다.  

2. **보고** 탭으로 전환합니다. **로그인**을 클릭하고 인증합니다. 그런 다음, **업데이트**를 클릭하여 Intune 데이터 웨어하우스에 대한 읽기 권한을 사용하도록 설정합니다.  

3. Intune과 사이트를 동기화한 후 **모니터링** 작업 영역으로 이동하고 **클라이언트 상태** 노드를 선택합니다. **전체 클라이언트 상태** 섹션에서 **Intune을 사용하는 비활성 클라이언트**에 대한 행을 참조하세요.  

공동 관리 사용에 대한 자세한 내용은 [Windows 10 디바이스에 대한 공동 관리](/sccm/core/clients/manage/co-management-overview)를 참조하세요.



## <a name="bkmk_app-repair"></a> 응용 프로그램 복구
<!--1357866-->

이제 [UserVoice 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8365071-force-reinstall-of-application)을 기반으로 Windows Installer 및 스크립트 설치 관리자 배포 유형에 대한 복구 명령줄을 지정합니다. 


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, 기능에 대한 의견이 포함된 [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 보내주세요.

1. Configuration Manager 콘솔에서 Windows Installer 또는 스크립트 설치 관리자 배포 유형의 속성을 엽니다.  

2. **프로그램** 탭으로 전환합니다. **프로그램 복구** 명령을 지정합니다.  

3. 앱을 배포합니다. 배포의 **배포 설정** 탭에서 **최종 사용자가 이 애플리케이션을 복구할 수 있도록 허용** 옵션을 사용하도록 설정합니다.  


### <a name="known-issue"></a>알려진 문제

이 버전에서는 사용자가 앱을 **복구**하기 위한 소프트웨어 센터의 새 단추가 표시되지 않습니다.  



## <a name="bkmk_email-approve"></a> 메일을 통해 응용 프로그램 요청 승인
<!--1321550-->

애플리케이션 승인 요청에 대한 메일 알림을 구성합니다. 사용자가 애플리케이션을 요청하면 메일을 받게 됩니다. 메일의 링크를 클릭하면 Configuration Manager 콘솔을 사용하지 않고 요청을 승인 또는 거부할 수 있습니다.


### <a name="prerequisites"></a>필수 구성 요소

#### <a name="to-send-email-notifications"></a>메일 알림을 보내려면
- [선택적 기능](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)인 **장치당 사용자에 대한 응용 프로그램 요청 승인**을 사용하도록 설정합니다.  

- [경고에 대한 메일 알림](/sccm/core/servers/manage/use-alerts-and-the-status-system#to-configure-email-notification-for-alerts)을 구성합니다.  

#### <a name="to-approve-or-deny-requests-from-email"></a>메일에서 요청을 승인 또는 거부하려면
이러한 필수 구성 요소를 구성하지 않으면 사이트에서는 요청을 승인 또는 거부하기 위한 링크 없이 애플리케이션 요청에 대한 메일 알림을 보냅니다.  

- 사이트 속성에서 **이 사이트의 모든 공급자 역할에 대해 REST 엔드포인트를 사용하고 Configuration Manager 클라우드 관리 게이트웨이 트래픽을 허용합니다**. 자세한 내용은 [OData 엔드포인트 데이터 액세스](/sccm/core/get-started/capabilities-in-technical-preview-1612#odata-endpoint-data-access)를 참조하세요.  

    - REST 엔드포인트를 사용하도록 설정한 후 SMS_EXEC 서비스를 다시 시작합니다.

- [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)  

- **클라우드 관리**를 위해 [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)에 사이트를 등록합니다.  

    - [Azure AD 사용자 검색](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)을 사용하도록 설정합니다.  

    - Azure AD에서 이 네이티브 앱에 대한 다음 설정을 수동으로 구성합니다.  

        - **리디렉션 URI**: `https://<CMG FQDN>/CCM_Proxy_ServerAuth/ImplicitAuth`. CMG(클라우드 관리 게이트웨이) 서비스의 FQDN(정규화된 도메인 이름)을 사용합니다(예: GraniteFalls.Contoso.com).   

        - **매니페스트**: **oauth2AllowImplicitFlow**를 true로 설정: `"oauth2AllowImplicitFlow": true,`  


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, 기능에 대한 의견이 포함된 [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 보내주세요.

1. Configuration Manager 콘솔에서 사용자 컬렉션에 사용할 수 있는 것으로 애플리케이션을 배포합니다. **배포 설정** 페이지에서 승인을 위해 사용하도록 설정합니다. 그런 다음, 알림을 받을 *단일* 메일 주소를 입력합니다.  

     > [!Note]  
     > 메일을 받는 Azure AD 조직의 모든 사용자가 요청을 승인할 수 있습니다. 작업을 수행하게 하려는 경우가 아니면 다른 사용자에게 메일을 전달하지 마세요.  

2. 사용자로서 소프트웨어 센터에서 애플리케이션을 요청합니다.  

3. 다음 예제와 유사한 메일 알림을 받습니다.  

![애플리케이션 승인을 위한 예제 메일 알림](media/1321550-email.png)

> [!Note]  
> 승인 또는 거부 링크는 일회용으로 제공됩니다. 예를 들어 알림을 받도록 그룹 별칭을 구성합니다. Meg가 요청을 승인합니다. 이제 Bruce가 요청을 거부할 수 없습니다.  



## <a name="bkmk_script"></a> 스크립트 출력 개선 사항
<!--1236459-->

이제 원시 또는 구조적 JSON 형식으로 세부 스크립트 출력을 볼 수 있습니다. 이 형식을 사용하면 출력을 더 쉽게 읽고 분석할 수 있습니다. 스크립트가 유효한 JSON 형식 텍스트를 반환하면 세부 출력이 **JSON 출력** 또는 **원시 출력**으로 표시됩니다. 그렇지 않으면 유일한 옵션은 **스크립트 출력**입니다. 

#### <a name="example-script-output-is-valid-json"></a>예제: 스크립트 출력이 유효한 JSON인 경우
명령: `$PSVersionTable.PSVersion`  

출력:  
```
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      16299  551
```

#### <a name="example-script-output-isnt-valid-json"></a>예제: 스크립트 출력이 유효한 JSON이 아닌 경우
명령: `Write-Output (Get-WmiObject -Class Win32_OperatingSystem).Caption`  

출력:  
```
Microsoft Windows 10 Enterprise
```


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, 기능에 대한 의견이 포함된 [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 보내주세요.

1. Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동하여 **디바이스 컬렉션** 노드를 선택합니다. 컬렉션을 마우스 오른쪽 단추로 클릭하고 **스크립트 실행**을 선택합니다. 스크립트 만들기 및 실행에 대한 자세한 내용은 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.  

2. 대상 컬렉션에서 스크립트를 실행합니다.  

3. 스크립트 실행 마법사의 **스크립트 상태 모니터링** 페이지의 아래쪽에서 **요약** 탭을 선택합니다. 위쪽에 있는 두 개의 드롭다운 목록을 **스크립트 출력** 및 **데이터 테이블**로 변경합니다. 그런 다음, 결과 행을 두 번 클릭하여 **자세한 출력** 대화 상자를 엽니다.  

4. 스크립트 실행 마법사의 **스크립트 상태 모니터링** 페이지의 아래쪽에서 **실행 정보** 탭을 선택합니다. 결과 행을 두 번 클릭하여 해당 디바이스에 대한 자세한 출력 대화 상자를 엽니다.  



## <a name="bkmk_3pupdate"></a> 타사 소프트웨어 업데이트 개선 사항
<!--1358714-->

이제 사용자 지정 카탈로그의 속성을 수정할 수 있습니다.

자세한 내용은 [사용자 지정 카탈로그에 대한 타사 소프트웨어 업데이트 지원](/sccm/core/get-started/capabilities-in-technical-preview-1806-2#bkmk_3pupdate)을 참조하세요.



## <a name="next-steps"></a>다음 단계

기술 미리 보기 분기를 설치하거나 업데이트하는 방법에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.    

Configuration Manager의 다양한 분기에 대한 자세한 내용은 [사용해야 하는 Configuration Manager 분기](/sccm/core/understand/which-branch-should-i-use)를 참조하세요.