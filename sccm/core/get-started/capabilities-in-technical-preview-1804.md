---
title: Technical Preview 1804
titleSuffix: Configuration Manager
description: Configuration Manager Technical Preview 버전 1804에서 사용할 수 있는 새로운 기능에 대해 알아봅니다.
ms.date: 05/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8af43618-ec60-4c3e-a007-12399d1335b9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 80f16244c10899ed264b83f6c7a9a050fba7a224
ms.sourcegitcommit: ef3fdf21180e43afd7af6c8264524711435e426e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54898310"
---
# <a name="capabilities-in-technical-preview-1804-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1804의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 Configuration Manager용 Technical Preview 버전 1804에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 기술 미리 보기 사이트를 업데이트하고 새 기능을 추가할 수 있습니다. 

이 업데이트를 설치하기 전에 [기술 미리 보기](/sccm/core/get-started/technical-preview) 아티클을 살펴보세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template   -->
## <a name="known-issues-in-this-technical-preview"></a>이 기술 미리 보기의 알려진 문제

### <a name="bkmk_ki-prereqs"></a> 업데이트를 다운로드하는 설치 링크가 작동하지 않음
<!--514334--> 미디어에서 설치를 실행하는 경우 초기 페이지에 **최신 Configuration Manager 업데이트 다운로드**라는 제목의 링크가 포함되어 있으며, 이 링크는 이 릴리스에서 작동하지 않습니다. 이 링크는 설치에 필요한 파일을 다운로드하기 위한 것입니다.

#### <a name="workaround"></a>해결 방법
설치에 필요한 파일을 다운로드하려면 설치 마법사를 실행합니다. 필수 다운로드 페이지에서 **필수 파일 다운로드** 옵션을 사용합니다. 


### <a name="bkmk_appcathttps"></a> 애플리케이션 카탈로그 웹 서비스 지점에서 HTTPS를 사용할 수 없음
<!--512637--> 응용 프로그램 카탈로그 웹 서비스 지점에서 HTTPS를 사용하도록 설정할 경우

- 사용자가 사용할 수 있도록 배포된 애플리케이션이 소프트웨어 센터에 표시되지 않습니다.  

- 다음 오류가 awebsctl.log에 표시됩니다.  

     `Call to HttpSendRequestSync failed for port 443 with status code 500, text: Internal Server Error`

#### <a name="workaround"></a>해결 방법
HTTP 연결을 사용하여 통신하도록 애플리케이션 카탈로그 웹 서비스 지점을 다시 구성합니다.  




</br>

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  


## <a name="configure-a-remote-content-library-for-the-site-server"></a>사이트 서버에 대해 원격 콘텐츠 라이브러리 구성  
<!--1357525--> 기본 사이트 서버에서 하드 드라이브 공간을 확보하려면 해당 [콘텐츠 라이브러리](/sccm/core/plan-design/hierarchy/the-content-library)를 다른 저장소 위치로 이동합니다. 사이트 서버의 다른 드라이브, 별도의 서버 또는 SAN(스토리지 영역 네트워크)의 내결함성 디스크로 콘텐츠 라이브러리를 이동할 수 있습니다. 시간 경과에 따라 사용자의 변화하는 콘텐츠 요구 사항에 맞게 확장되거나 축소되는 탄력적인 스토리지를 제공하므로 SAN을 사용하는 것이 좋습니다. 

이 원격 콘텐츠 라이브러리는 [사이트 서버 역할 고가용성](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)을 위한 새로운 필수 조건입니다. 

> [!Note]  
> 이 작업은 사이트 서버의 콘텐츠 라이브러리만 이동합니다. 배포 지점에 있는 콘텐츠 라이브러리의 위치에는 영향을 주지 않습니다. 

### <a name="prerequisites"></a>필수 구성 요소  
- 사이트 서버 컴퓨터 계정에 콘텐츠 라이브러리를 이동하는 네트워크 경로에 대한 **읽기** 및 **쓰기** 권한이 필요합니다. 원격 시스템에 설치된 구성 요소가 없습니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 전환합니다. **사이트 구성**을 확장하고 **사이트**를 선택합니다. 세부 정보 창의 맨 아래에 있는 **요약** 탭에서 **콘텐츠 라이브러리**에 대한 새 열을 확인합니다.  

2. 리본에서 **콘텐츠 라이브러리 관리**를 클릭합니다.  

3. **네트워크 공유**를 선택하고 유효한 네트워크 경로를 입력합니다. 이 경로는 사이트에서 콘텐츠 라이브러리를 이동하는 위치입니다. **확인**을 클릭합니다.  

4. 세부 정보 창의 콘텐츠 라이브러리 열에서 **상태** 속성을 확인합니다. 이 속성은 콘텐츠 라이브러리 이동 시 업데이트되어 사이트 진행 상황을 표시합니다. 진행 중인 경우 완료율이 표시됩니다. 오류 상태가 있을 경우 오류가 표시됩니다. 일반적인 오류에는 `access denied`, `disk full` 등이 있습니다. 완료되면 `OK`가 표시됩니다. 자세한 내용은 **distmgr.log**를 참조하세요. 자세한 내용은 [사이트 서버 및 사이트 시스템 서버 로그](/sccm/core/plan-design/hierarchy/log-files#BKMK_SiteSiteServerLog)를 참조하세요.  

콘텐츠 라이브러리를 다시 사이트 서버로 이동해야 하는 경우 이 프로세스를 반복하되 **사이트 서버 로컬** 옵션을 선택합니다.  

> [!Tip]  
> 사이트 서버의 다른 드라이브로 콘텐츠를 이동하려면 **콘텐츠 라이브러리 전송** 도구를 사용합니다. 자세한 내용은 [Configuration Manager Toolkit](#configuration-manager-toolkit)를 참조하세요.  



## <a name="bkmk_feedback"></a> Configuration Manager 콘솔에서 피드백 제출  
<!--1357542-->

웃는 얼굴 보내기! 이제 Configuration Manager 팀에게 사용자 경험을 직접 알릴 수 있습니다. Configuration Manager 콘솔에서 쉽게 피드백을 보낼 수 있습니다. 칭찬, 문제, 제안 사항 등 모든 피드백에 귀를 기울이겠습니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, **피드백**을 전송하여 작업이 어떻게 진행되었는지 알려주세요.  

1. Configuration Manager 콘솔의 오른쪽 위에서 리본 위의 웃는 얼굴 단추를 클릭합니다.  

2. 드롭다운 목록에서 사용 가능한 옵션 중 하나를 선택합니다.  

   - **웃는 얼굴 보내기**: 특정 항목을 정말 좋아한 경우입니다. 이 옵션의 경우 피드백을 자세히 입력합니다. 그런 다음, 스크린샷과 메일 주소를 선택적으로 포함합니다.  

   - **찡그린 얼굴 보내기**: 콘솔에서 문제가 발생했거나, 특정 항목이 예상대로 작동하지 않은 경우입니다. 이 옵션의 경우 잠재적인 제품 문제를 자세히 입력합니다. 그런 다음, 스크린샷, 메일 주소, 진단 데이터를 선택적으로 포함합니다.  

   - **제안 보내기**: Configuration Manager를 변경하고 개선하기 위한 아이디어가 있는 경우입니다. 이 옵션을 선택하면 웹 브라우저에서 [UserVoice](https://configurationmanager.uservoice.com) 사이트가 열립니다.  

이 피드백은 Microsoft의 Configuration Manager 제품 팀에게 바로 전달됩니다. Windows 10 피드백 허브도 사용할 수 있지만, 콘솔 내 피드백 메커니즘을 사용하는 것이 좋습니다.  

컨텍스트를 위해 항상 다음 익명 정보가 피드백과 함께 포함됩니다.  

 - Configuration Manager 콘솔 버전 및 언어  

 - Configuration Manager 사이트 버전  

 - 지원 ID(계층 구조 ID라고도 함)  

 - 콘솔을 실행 중인 시스템의 OS 버전 및 언어  

 - 콘솔에서 웃는 얼굴을 클릭한 정확한 위치  

이 데이터는 진단 및 사용 데이터 컬렉션과 일치합니다. 자세한 내용은 [진단 및 사용 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.

### <a name="known-issues"></a>알려진 문제

인터넷에 액세스할 수 없는 장치에서 피드백을 보내려고 하면 애플리케이션이 예기치 않게 닫힐 수 있습니다. 웃는 얼굴이나 찡그린 얼굴을 보내려면 디바이스가 petrol.office.microsoft.com에 액세스할 수 있는지 확인합니다.



## <a name="support-center"></a>지원 센터
<!--1357489-->

클라이언트 문제 해결, 실시간 로그 보기, 나중에 분석하기 위해 구성 관리자 클라이언트 컴퓨터의 상태 캡처 등의 작업에 지원 센터를 사용합니다. 지원 센터는 많은 관리자 문제 해결 도구를 통합하는 단일 도구입니다. 버그 수정, 개선 사항 및 새로운 로그 뷰어 미리 보기가 포함된 지원 센터의 최신 버전 미리 보기를 기술 미리 보기로 사용할 수 있습니다. 사이트 서버의 **cd.latest\SMSSETUP\Tools\SupportCenter** 폴더에서 지원 센터 설치 관리자를 찾습니다.

 > [!Tip]  
 > 지원 센터의 기존 기능에 대한 레거시 설명서는 [TechNet](https://technet.microsoft.com/library/dn688621.aspx)에서 확인할 수 있습니다. 관련 정보는 docs.microsoft.com 라이브러리로 마이그레이션 중입니다.  

### <a name="new-support-center-features"></a>새로운 지원 센터 기능  

 - 새 로그 뷰어, OneTrace. CMTrace와 유사하게 작동하며 탭 보기, 도킹 가능한 창 등의 개선 사항을 포함합니다.  

 - 새 데이터 수집기 기능은 로컬 또는 원격 구성 관리자 클라이언트에서 진단 로그를 수집합니다. 인벤토리(클라이언트 감시 대체), 정책(정책 감시 대체) 및 클라이언트 캐시에 대한 실시간 진단을 제공합니다.  



## <a name="configuration-manager-toolkit"></a>Configuration Manager Toolkit
<!--1357145-->

구성 관리자 서버 및 클라이언트 도구가 이제 기술 미리 보기에 포함되었습니다. 이러한 도구는 사이트 서버의 **cd.latest\SMSSETUP\Tools** 폴더에 있습니다. 추가로 설치할 필요가 없습니다.

#### <a name="server-tools"></a>서버 도구  

 - **DP 작업 관리자**: 배포 지점에 콘텐츠를 배포하는 작업의 문제를 해결합니다.  

 - **컬렉션 평가 뷰어**: 컬렉션 평가 세부 정보를 봅니다.  

 - **콘텐츠 라이브러리 탐색기**: 콘텐츠 라이브러리 단일 인스턴스 저장소의 콘텐츠를 표시합니다.  

 - **콘텐츠 라이브러리 전송**: 드라이브 간에 콘텐츠 라이브러리를 전송합니다.  

 - **콘텐츠 소유권 도구**: 분리된 패키지의 소유권을 변경합니다. 이러한 패키지는 소유하는 사이트 서버가 없는 사이트에 존재합니다.  

 - **역할 기반 관리 및 감사 도구**: 관리자가 역할 구성을 감사하도록 지원합니다.  

#### <a name="client-tools"></a>클라이언트 도구

 - **CMTrace**: 로그를 봅니다.  

 - **배포 모니터링 도구**: 애플리케이션, 업데이트 및 기준 배포의 문제를 해결합니다.  

 - **정책 감시**: 정책 할당을 표시합니다.  

 - **전원 뷰어 도구**: 전원 관리 기능의 상태를 표시합니다.  

 - **일정 보내기 도구**: DCM 기준의 일정과 평가를 트리거합니다.  

> [!Important]  
> [지원 센터](#support-center)는 다음 도구와 동일하거나 향상된 기능을 포함하므로 대부분의 사용 사례에서 권장됩니다.  
>  - 클라이언트 감시
>  - CMTrace<sup>1</sup> 
>  - 배포 모니터링 도구
>  - 정책 감시
>  - 일정 보내기 도구
> 
> <sup>1</sup> CMTrace는 .NET 또는 WPF(Windows Presentation Foundation)를 사용하지 않으므로 Windows PE 부팅 이미지에서 계속 사용됩니다.

### <a name="known-issues"></a>알려진 문제
일부 클라이언트 및 서버 도구는 시작 시 예기치 않게 종료될 수 있습니다. 이 문제는 미디어에 누락된 파일 때문입니다. 해결책으로서 AdminConsole\bin directory에서 SMSSETUP\Tools\ClientTools 및 ServerTools 디렉터리 모두로 **Microsoft.Diagnostics.Tracing.EventSource.dll** 파일을 복사합니다. 이 파일은 Configuration Manager 콘솔에서 사용하는 것과 동일한 버전이어야 합니다. 다른 버전은 작동하지 않을 수 있습니다. <!--513977-->



## <a name="uninstall-application-on-approval-revocation"></a>승인 취소 시 애플리케이션 제거
<!--1357891-->

애플리케이션 승인 취소 시의 동작이 변경되었습니다. 이제 애플리케이션에 대한 요청을 거부하면 클라이언트가 사용자 장치에서 애플리케이션을 제거합니다. 

### <a name="prerequisites"></a>필수 구성 요소
- **장치당 사용자에 대한 애플리케이션 요청 승인** 기능을 사용하도록 설정합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 승인이 필요한 애플리케이션을 사용자에게 배포합니다. 배포의 **배포 설정** 탭에서 **관리자가 장치에서 이 애플리케이션에 대한 요청을 승인해야 합니다.** 옵션을 사용하도록 설정합니다.  

2. 구성 관리자 클라이언트의 소프트웨어 센터에서 사용자가 애플리케이션 설치 승인을 요청합니다.  

3. Configuration Manager 콘솔에서 장치에 애플리케이션을 설치하려는 이 사용자의 요청을 승인합니다. 애플리케이션 승인 요청은 **소프트웨어 라이브러리** 작업 영역의 **애플리케이션 관리** 아래에 있는 **승인 요청** 노드에 표시됩니다.  

4. 클라이언트의 소프트웨어 센터에서 사용자가 애플리케이션을 설치합니다.  

5. Configuration Manager 콘솔에서 장치의 애플리케이션에 대한 사용자 요청을 거부합니다.  

### <a name="known-issues"></a>알려진 문제
- 사용자가 클라이언트에 애플리케이션을 설치한 후 사용자 정책을 업데이트합니다. 소프트웨어 센터에서 **옵션** 탭으로 전환하고 **컴퓨터 유지 관리**를 확장한 다음 **정책 동기화**를 클릭합니다.<!--480609-->  

- 애플리케이션 카탈로그 웹 서비스 지점은 HTTP여야 합니다. 자세한 내용은 [이 기술 미리 보기의 알려진 문제](#bkmk_appcathttps)를 참조하세요.<!--512637-->  



## <a name="exclude-active-directory-containers-from-discovery"></a>검색에서 Active Directory 컨테이너 제외
<!--1358143--> 검색되는 개체 수를 줄이기 위해 이제 Active Directory 시스템 검색에서 특정 컨테이너를 제외할 수 있습니다. 이 기능은 [UserVoice 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8414520-exclude-virtual-cluster-and-ou-from-discovery)을 반영한 결과입니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **계층 구조 구성**을 확장하고 **검색 방법**을 선택합니다. **Active Directory 시스템 검색**을 선택하고 리본에서 **속성**을 클릭합니다.  

2. 새로 만들기 아이콘을 클릭하여 새 Active Directory 컨테이너를 지정합니다.   

3. Active Directory 컨테이너 대화 상자의 위치 섹션에서 **경로**를 찾거나 입력하여 검색을 시작합니다.  

4. 검색 옵션 섹션에서 **회귀적으로 Active Directory 자식 컨테이너 검색** 옵션을 사용하도록 설정합니다. 그런 다음, **추가**를 클릭하여 이 검색에서 제외할 하위 컨테이너를 선택합니다.  

5. 새 컨테이너 선택 대화 상자에서 제외할 자식 컨테이너를 선택합니다. **확인**을 클릭하여 새 컨테이너 선택 대화 상자를 닫습니다.  

6. **확인**을 클릭하여 Active Directory 컨테이너 대화 상자를 닫습니다.  

7. Active Directory 시스템 검색 속성 창에서 검색이 시작되는 Active Directory 컨테이너의 경로를 확인합니다. **재귀** 열에 **예**가 표시되고, 새로운 **제외 있음** 열에도 **예**가 표시됩니다. **확인**을 클릭하여 Active Directory 시스템 검색 속성 창을 닫습니다.  



## <a name="specify-the-visibility-of-the-application-catalog-website-link-in-software-center"></a>소프트웨어 센터에서 애플리케이션 카탈로그 웹 사이트 링크의 표시 여부 지정
<!--1358214-->

이제 소프트웨어 센터의 **설치 상태** 노드에 **애플리케이션 카탈로그 웹 사이트 열기** 링크를 표시할지 여부를 제어할 수 있습니다.  

> [!Note]  
> 2018년 6월 1일 이후 릴리스되는 첫 번째 업데이트부터 애플리케이션 카탈로그 웹 사이트 사용자 환경에 대한 지원이 종료됩니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔, **관리** 작업 영역, **클라이언트 설정** 노드에서 사용자 지정 클라이언트 디바이스 설정 정책을 만듭니다.  

2. **소프트웨어 센터** 그룹을 선택합니다.  

3. **소프트웨어 센터 설정**에 대해 **사용자 지정**을 클릭합니다.  

4. **소프트웨어 센터에서 애플리케이션 카탈로그 웹 사이트 링크 숨기기** 옵션을 사용하도록 설정합니다.   

클라이언트 설정에 대한 자세한 내용은 [클라이언트 설정 구성](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.




## <a name="filter-automatic-deployment-rules-by-software-update-architecture"></a>소프트웨어 업데이트 아키텍처를 기준으로 자동 배포 규칙 필터링
 <!--1322266--> 이제 자동 배포 규칙을 필터링하여 Itanium, ARM64 등의 아키텍처를 제외할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 전환합니다. **소프트웨어 업데이트**를 확장하고 **자동 배포 규칙**을 선택합니다. 리본에서 **자동 배포 규칙 만들기**를 선택합니다.  

2. **일반** 탭과 **배포 설정** 탭에 적합한 설정을 채웁니다.  

3. **소프트웨어 업데이트** 탭에서 **아키텍처**를 선택한 다음 **검색 조건**에서 **찾을 항목**을 클릭합니다.  

4. 자동 배포 규칙에 포함할 아키텍처를 선택합니다.  

5. **다음**을 클릭하고 자동 배포 규칙 만들기를 계속 진행합니다.  

> [!IMPORTANT]  
> 64비트(x64) 시스템에서 실행되는 32비트(x86) 애플리케이션 및 구성 요소도 있습니다. 확실히 x86이 필요 없는 경우가 아니면 x64를 선택할 때 x86도 사용하도록 설정합니다.  

### <a name="known-issues"></a>알려진 문제
아키텍처 조건을 추가하면 자동 배포 규칙 속성 페이지의 검색 조건에 **제목**이 표시됩니다. 자동 배포 규칙은 여전히 예상대로 작동하며 올바른 소프트웨어 업데이트를 선택합니다. 그러나 이번에는 **아키텍처** 및 **제목** 조건을 둘 다 포함할 수 없습니다. <!--512634,512632-->



## <a name="improvements-to-os-deployment"></a>향상된 OS 배포
OS 배포가 다음과 같이 향상되었으며, 일부는 사용자 의견 피드백을 반영한 결과입니다.  

 - [작업 순서 변수에 저장된 중요한 데이터 마스킹](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15282795-secret-task-sequence-variable-value-exposed): [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계에서 새 옵션인 **이 값 표시 안 함**을 선택합니다. 예를 들어 암호를 지정하는 경우입니다.<!--1358330--> 이 옵션을 사용하도록 설정하는 경우 다음 동작이 적용됩니다.
   - 변수 값이 smsts.log에 표시되지 않습니다.
   - Configuration Manager 콘솔과 SMS 공급자에서 이 값이 암호 등의 다른 비밀과 동일하게 처리됩니다.
   - 작업 순서를 내보낼 때 값이 포함되지 않습니다.
   - 단계를 편집할 때 작업 순서 편집기에서 이 값을 읽지 않습니다. 변경하려면 전체 값을 다시 입력합니다.

   > [!Important]  
   > 변수와 해당 값이 작업 순서와 함께 XML로 저장되고 데이터베이스에서 난독 처리됩니다. 클라이언트가 관리 지점에서 작업 순서 정책을 요청하는 경우 전송 중 및 클라이언트에 저장될 때 암호화됩니다. 그러나 클라이언트에서 런타임 중 메모리 내 작업 순서 환경의 모든 변수 값은 일반 텍스트입니다. 작업 순서에 변수 값을 출력하는 단계가 포함된 경우 이 출력은 일반 텍스트입니다. 이 동작의 경우 관리자가 작업 순서에 이러한 단계를 포함하는 명시적 작업을 수행해야 합니다. 


 - [작업 순서의 명령 실행 단계에서 프로그램 이름 마스크](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15282795-secret-task-sequence-variable-value-exposed): 잠재적으로 중요한 데이터가 표시되거나 기록되지 않도록 하려면 작업 순서 변수 **OSDDoNotLogCommand**를 `TRUE`로 설정합니다. 이 변수는 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 작업 순서 단계 중 smsts.log에서 프로그램 이름을 마스크합니다. <!--1358493-->  



## <a name="improvements-to-the-configuration-manager-console"></a>Configuration Manager 콘솔에 대한 향상된 기능
- **자산 및 준수**, **디바이스 컬렉션** 아래에서 컬렉션 멤버를 볼 때 이제 기본 사용자 정보가 표시됩니다.<!--510252-->  



## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
