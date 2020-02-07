---
title: Technical Preview 1805
titleSuffix: Configuration Manager
description: Configuration Manager Technical Preview 버전 1805에서 사용할 수 있는 새로운 기능에 대해 알아봅니다.
ms.date: 05/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7996b3eb-5259-483b-af40-adae2943d123
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: d60b99bc17c40e20e6472b367a67b06f9f22a15f
ms.sourcegitcommit: e7583b5e522d01bc8710ec8e0fe3e5f75a281577
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035269"
---
# <a name="capabilities-in-technical-preview-1805-for-configuration-manager"></a>Configuration Manager용 Technical Preview 1805의 기능

*적용 대상: Configuration Manager(기술 미리 보기 분기)*

이 문서에서는 Configuration Manager Technical Preview 버전 1805에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 기술 미리 보기 사이트를 업데이트하고 새 기능을 추가할 수 있습니다. 

이 업데이트를 설치하기 전에 [기술 미리 보기](/sccm/core/get-started/technical-preview) 아티클을 살펴보세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template
## Known Issues in this Technical Preview

### <a name="bkmk_ANCHOR"></a> Known issue title
<!--bugID--
Issue description and cause.

#### Workaround
Steps to workaround, if any.  
-->



</br>

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  



## <a name="create-a-phased-deployment-with-manually-configured-phases-for-a-task-sequence"></a>작업 순서에 대해 수동으로 구성된 단계를 사용하여 단계적 배포 만들기
<!--1358148-->
이제 작업 순서에 대해 수동으로 구성된 단계를 사용하여 [단계적 배포를 만들 수 있습니다](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence). 단계적 배포 만들기 마법사의 **단계** 탭에서 단계를 최대 10개까지 더 추가할 수 있습니다. 


### <a name="try-it-out"></a>기능 직접 사용해 보기
지침에 따라 모든 단계를 수동으로 구성하는 단계적 배포를 만드세요. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요. 

1. **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.  

2. 기존 작업 순서를 마우스 오른쪽 버튼으로 클릭하고 **단계별 배포 만들기**를 선택합니다.  

3. **일반** 탭에서 단계적 배포에 이름을 지정하고 설명(선택 사항)을 입력한 다음, **모든 단계를 수동으로 구성**을 선택합니다.  

4. **단계** 탭에서 **추가**를 클릭합니다.  

5. 단계의 **이름**을 지정한 후 대상 **Phase Collection**(단계 컬렉션)으로 이동합니다.  

6. **단계 설정** 탭에서 각 일정 설정에 대해 하나의 옵션을 선택하고 완료되면 **다음**을 선택합니다.  

    - 이전 단계의 성공에 대한 조건(첫 번째 단계에는 이 옵션을 사용할 수 없음)
        - **배포 성공률**: 이전 단계 성공 조건에 대해 배포를 성공적으로 완료한 디바이스의 백분율을 지정합니다.  

    - 이전 단계 성공 후 배포의 이 단계를 시작하기 위한 조건  
        - **지연 기간(일) 후 자동으로 이 단계 시작**: 이전 단계 성공 후 다음 단계 시작 전까지 대기하는 기간(일)을 선택합니다. 
        - **수동으로 이 배포 단계 시작**: 이전 단계 성공 후 자동으로 이 단계를 시작하지 않습니다.  

    - 디바이스가 대상으로 지정된 후 소프트웨어 설치
        - **가능하면 빨리**: 디바이스를 대상으로 지정하는 즉시 디바이스에 설치하는 최종 기한을 설정합니다.
        - **최종 기한 시간(디바이스가 대상으로 지정된 시간 기준)** : 디바이스가 대상으로 지정되고 설치가 진행되기까지의 특정 일 수를 설정합니다.  
     
7. 단계 설정 마법사를 완료합니다.

8. 단계적 배포 만들기 마법사의 **단계** 탭에서 이 배포의 단계를 추가, 제거, 다시 정렬 또는 편집할 수 있습니다.  

9. 단계적 배포 만들기 마법사를 완료합니다.  



## <a name="cloud-distribution-point-support-for-azure-resource-manager"></a>Azure Resource Manager에 대한 클라우드 배포 지점 지원
<!--1322209-->
[클라우드 배포 지점](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure) 인스턴스를 만들 때 이제 마법사에서 **Azure Resource Manager 배포**를 만들 수 있는 옵션을 제공합니다. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)는 모든 솔루션 리소스를 [리소스 그룹](/azure/azure-resource-manager/resource-group-overview#resource-groups)이라는 단일 엔터티로 관리하기 위한 최신 플랫폼입니다. Azure Resource Manager로 클라우드 배포 지점을 배포하는 경우 사이트에서 Azure AD(Azure Active Directory)를 사용하여 필요한 클라우드 리소스를 인증하고 만듭니다. 이 최신 배포에서는 클래식 Azure 관리 인증서가 필요하지 않습니다.  

Azure 관리 인증서를 사용하는 **클래식 서비스 배포** 옵션도 클라우드 배포 지점 마법사에서 계속 제공됩니다. 리소스의 배포 및 관리를 간소화하려면 모든 새 클라우드 배포 지점에 Azure Resource Manager 배포 모델을 사용하는 것이 좋습니다. 가능하면 Resource Manager를 통해 기존 클라우드 배포 지점을 재배포합니다.

Configuration Manager는 기존 클래식 클라우드 배포 지점을 Azure Resource Manager 배포 모델로 마이그레이션하지 않습니다. Azure Resource Manager 배포를 사용하여 새 클라우드 배포 지점을 만든 다음, 클래식 클라우드 배포 지점을 제거합니다. 

> [!IMPORTANT]  
> 이 기능은 Azure CSP(클라우드 서비스 공급자) 지원을 사용하도록 설정하지 않습니다. Azure Resource Manager를 통한 클라우드 배포 지점 배포는 CSP가 지원하지 않는 클래식 클라우드 서비스를 계속 사용합니다. 자세한 내용은 [Azure CSP에서 사용 가능한 Azure 서비스](/azure/cloud-solution-provider/overview/azure-csp-available-services)를 참조하세요.  


### <a name="prerequisites"></a>전제 조건  
- [Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure)와의 통합. Azure AD 사용자 검색은 필요하지 않습니다.  

- Azure 관리 인증서를 제외하고 [클라우드 배포 지점의 요구 사항](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_requirements)과 동일합니다.  


### <a name="try-it-out"></a>기능 직접 사용해 보기  
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장하고 **클라우드 배포 지점**을 선택합니다. 리본에서 **클라우드 배포 지점 만들기**를 클릭합니다.   

2. **일반** 페이지에서 **Azure Resource Manager 배포**를 선택합니다. **로그인**을 클릭하여 Azure 구독 관리자 계정으로 인증합니다. 마법사가 통합 필수 조건 중에 저장된 Azure AD 구독 정보의 나머지 필드를 자동으로 채웁니다. 여러 구독을 소유하고 있는 경우 사용할 구독을 선택합니다. **다음**을 클릭합니다.  

3. **설정** 페이지에서 서버 PKI **인증서 파일**을 평소대로 제공합니다. 이 인증서는 Azure에서 사용하는 클라우드 배포 지점 **서비스 FQDN**을 정의합니다. **지역**을 선택한 다음, **새로 만들기** 또는 **기존 항목 사용** 리소스 그룹 옵션을 선택합니다. 새 리소스 그룹 이름을 입력하거나 드롭다운 목록에서 기존 리소스 그룹을 선택합니다.  

4. 마법사를 완료합니다.  

> [!NOTE]  
> 선택된 Azure AD 서버 앱에 대해 Azure가 구독 **참가자** 권한을 할당합니다.  

서비스 연결 지점에서 **cloudmgr.log**를 사용하여 서비스 배포 진행 상황을 모니터링합니다.



## <a name="take-actions-based-on-management-insights"></a>관리 인사이트를 기반으로 작업 수행
<!--1357930-->
일부 [관리 인사이트](/sccm/core/servers/manage/management-insights)에는 작업을 수행할 수 있는 옵션이 있습니다. 규칙에 따라 이 작업은 다음 동작 중 하나를 보여 줍니다.  

- 콘솔에서 추가 작업을 수행할 수 있는 노드로 자동으로 이동합니다. 예를 들어, 관리 인사이트에서 클라이언트 설정을 변경하도록 권장하는 경우 작업을 수행하면 클라이언트 설정 노드로 이동합니다. 기본값 또는 사용자 지정 클라이언트 설정 개체를 수정하여 추가 작업을 수행할 수 있습니다.  

- 쿼리를 기반으로 하는 필터링된 보기로 이동합니다. 예를 들어, 빈 컬렉션 규칙에 대한 작업을 수행하면 이러한 컬렉션만 컬렉션 목록에 표시됩니다. 여기에서 컬렉션 삭제 또는 멤버 관리 규칙 수정과 같은 추가 작업을 수행할 수 있습니다.  

이번 릴리스에서는 다음과 같은 관리 인사이트 규칙에 작업이 있습니다.
- 보안
    - 지원되지 않는 맬웨어 방지 클라이언트 버전
- 소프트웨어 센터
    - 새 버전의 Software Center 사용
- 애플리케이션
    - 배포가 없는 애플리케이션
- 간소화된 관리
    - 비 CB 클라이언트 버전
- 컬렉션
    - 비어 있는 컬렉션 
- Cloud Services
    - 클라이언트를 최신 Windows 10 버전으로 업데이트



## <a name="transition-device-configuration-workload-to-intune-using-co-management"></a>공동 관리를 사용하여 디바이스 구성 워크로드를 Intune으로 전환
<!--1357903-->

이제 공동 관리를 사용하도록 설정한 후 Configuration Manager에서 Intune으로 디바이스 구성 워크로드를 전환할 수 있습니다. 이 워크로드를 전환하면 Intune을 사용하여 MDM 정책을 배포할 수 있지만 애플리케이션 배포에는 Configuration Manager를 계속 사용할 수 있습니다. 

이 워크로드를 전환하려면 공동 관리 속성 페이지로 이동하고 슬라이더 막대를 Configuration Manager에서 **파일럿** 또는 **모두**로 이동합니다. 자세한 내용은 [Windows 10 디바이스의 공동 관리](/sccm/core/clients/manage/co-management-overview)를 참조하세요.

> [!Note]  
> 이 워크로드를 이동하면 디바이스 구성 워크로드의 일부인 **리소스 액세스** 및 **Endpoint Protection** 워크로드도 이동합니다.

이 워크로드를 전환하면 Intune이 디바이스 구성 기관이더라도 Configuration Manager에서 공동 관리하는 디바이스로 설정을 배포할 수 있습니다. 이 예외는 조직에 필요한 설정을 구성하는 데 사용할 수 있지만 Intune에서는 아직 사용할 수 없습니다. 이 예외는 Configuration Manager 구성 기준에서 지정합니다. 기준을 만들 때 또는 기존 기준 속성의 **일반** 탭에서 **공동 관리하는 클라이언트에 대해서도 항상 이 기준 적용** 옵션을 사용하도록 설정합니다. 



## <a name="enable-distribution-points-to-use-network-congestion-control"></a>배포 지점에서 네트워크 정체 제어를 사용하도록 설정
<!--1358112-->

Windows LEDBAT(Low Extra Delay Background Transport)는 백그라운드 네트워크 전송을 관리하는 데 도움이 되는 Windows Server의 기능입니다. 지원되는 Windows Server 버전에서 실행되는 배포 지점의 경우 네트워크 트래픽을 조정하는 옵션을 사용할 수 있습니다. 클라이언트는 사용 가능한 경우에만 네트워크 대역폭을 사용합니다. 

Windows LEDBAT에 대한 자세한 정보는 [New transport advancements](https://blogs.technet.microsoft.com/networking/2016/07/18/announcing-new-transport-advancements-in-the-anniversary-update-for-windows-10-and-windows-server-2016/)(새로운 전송 개선 사항) 블로그 게시물을 참조하세요.


### <a name="prerequisites"></a>전제 조건
- Windows Server 버전 1709의 배포 지점.  

- 클라이언트의 필수 구성 요소는 없습니다.<!--SCCMDocs issue 699-->  


### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **배포 지점** 노드를 선택합니다. 대상 배포 지점을 선택하고 리본에서 **속성**을 클릭합니다.  

2. **일반** 탭에서 **사용되지 않는 네트워크 대역폭(Windows LEDBAT)을 사용하도록 다운로드 속도 조정** 옵션을 사용하도록 설정합니다.  



## <a name="cloud-management-dashboard"></a>클라우드 관리 대시보드
<!--1358461-->
새로운 **클라우드 관리 대시보드**는 CMG(클라우드 관리 게이트웨이) 사용량에 대한 중앙 집중식 보기를 제공합니다. 사이트가 Azure AD에 등록되면 클라우드 사용자 및 디바이스에 대한 데이터도 표시됩니다.  

다음 스크린샷은 사용 가능한 타일 두 가지를 보여 주는 클라우드 관리 대시보드의 일부입니다.  
![클라우드 관리 대시보드 타일 CMG 트래픽 및 현재 온라인 클라이언트](media/1358461-cmg-dashboard.png)

이 기능에는 문제 해결에 도움이 되도록 실시간 확인에 사용하는 **CMG 연결 분석기**도 포함됩니다. 콘솔 내 유틸리티는 서비스의 현재 상태를 확인하며, CMG 연결 지점을 통해 CMG 트래픽을 허용하는 모든 관리 지점에 대한 통신 채널을 확인합니다.


### <a name="prerequisites"></a>전제 조건
- 인터넷 기반 클라이언트에서 사용하는 활성 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).  

- 클라우드 관리를 위해 [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)에 등록된 사이트.  


### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

#### <a name="cloud-management-dashboard"></a>클라우드 관리 대시보드

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다. **클라우드 관리** 노드를 선택하고 대시보드 타일을 봅니다.  

#### <a name="cmg-connection-analyzer"></a>CMG 연결 분석기

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **Cloud Services**를 확장하고 **클라우드 관리 게이트웨이**를 선택합니다.  

2. 대상 CMG 인스턴스를 선택하고 리본에서 **연결 분석기**를 선택합니다.  

3. CMG 연결 분석기 창에서 다음 옵션 중 하나를 선택하여 서비스를 인증합니다.  

     1. **Azure AD 사용자**: 이 옵션은 Azure AD 조인 Windows 10 디바이스에 로그온한 클라우드 기반 사용자 ID와 동일하게 통신을 시뮬레이션하는 데 사용합니다. **로그인**을 클릭하여 이 Azure AD 사용자 계정에 대한 자격 증명을 안전하게 입력합니다.  

     2. **클라이언트 인증서**: 이 옵션은 [클라이언트 인증 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_clientauth)를 사용하는 Configuration Manager 클라이언트와 동일하게 통신을 시뮬레이션하는 데 사용합니다.  

4. **시작**을 클릭하여 분석을 시작합니다. 분석기 창에 결과가 표시됩니다. 설명 필드에서 자세한 내용을 보려면 항목을 선택합니다.  



## <a name="cmpivot"></a>CMPivot
<!--1358456-->
Configuration Manager는 고객이 보고용으로 사용하는 디바이스 데이터의 대규모 중앙 저장소를 항상 제공해왔습니다. 그러나 해당 데이터는 클라이언트에서 마지막으로 수집될 때와 마찬가지입니다. 

CMPivot은 사용자 환경에서 디바이스의 실시간 상태에 액세스할 수 있는 새로운 콘솔 내 유틸리티입니다. 이 유틸리티는 대상 컬렉션에서 현재 연결된 모든 디바이스에 대해 바로 쿼리를 실행하고 결과를 반환합니다. 그러면 도구에서 이 데이터를 필터링하고 그룹화할 수 있습니다. 온라인 클라이언트에서 실시간 데이터를 제공함으로써 비즈니스 질문에 신속하게 대답하고 문제를 해결하며 보안 인시던트에 응답할 수 있습니다.

예를 들어, [잘못된 실행 부채널 취약성을 완화](https://techcommunity.microsoft.com/t5/configuration-manager-blog/additional-guidance-to-mitigate-speculative-execution-side/ba-p/274974)할 때 요구 사항 중 하나는 시스템 BIOS 업데이트입니다. CMPivot을 사용하여 시스템 BIOS 정보를 신속하게 쿼리하고 준수하지 않는 클라이언트를 찾을 수 있습니다. 

다음 스크린샷에서 CMPivot은 각각 디바이스 수가 하나인 별도의 BIOS 버전 두 개를 보여 줍니다. CMPivot을 사용해 볼 때 이 예제 쿼리를 사용할 수 있습니다.  
`Registry('hklm:\\Hardware\\Description\\System\\BIOS') | where (Property == 'BIOSVersion') | summarize dcount( Device ) by Value`  

![BIOSVersion에 대한 예제 쿼리가 있는 CMPivot 창](media/1358456-cmpivot-biosversion.png)

디바이스 수를 클릭하면 드릴다운하여 특정 디바이스를 볼 수 있습니다. CMPivot에 디바이스를 표시할 때 디바이스를 마우스 오른쪽 단추로 클릭하고 다음과 같은 [클라이언트 알림 작업](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode)을 선택할 수 있습니다.
- 스크립트 실행
- 원격 제어
- 리소스 탐색기

특정 디바이스를 마우스 오른쪽 단추로 클릭하면 특정 디바이스의 보기를 다음 특성 중 하나로 피벗할 수도 있습니다.
- 자동 시작 명령
- 설치된 제품
- Processes
- 서비스
- 사용자
- 활성 연결
- 누락 업데이트

### <a name="prerequisites"></a>전제 조건
- 대상 클라이언트를 최신 버전으로 업데이트해야 합니다.  

- Configuration Manager 관리자는 스크립트를 실행할 수 있는 권한이 필요합니다. 자세한 내용은 [스크립트의 보안 역할](/sccm/apps/deploy-use/create-deploy-scripts#bkmk_ScriptRoles)을 참조하세요.  

### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동하여 **디바이스 컬렉션**을 선택합니다. 대상 컬렉션을 선택하고 리본에서 **CMPivot 시작**을 클릭하여 도구를 시작합니다.  

2. 인터페이스에서 도구 사용에 대한 추가 정보를 제공합니다. 
     - 맨 위에 쿼리 문자열을 수동으로 입력하거나 인라인 문서에서 링크를 클릭할 수 있습니다.
     - **엔터티** 중 하나를 클릭하여 쿼리 문자열에 추가합니다. 
     - **표 연산자**, **집계 함수** 및 **스칼라 함수**에 대한 링크를 클릭하면 웹 브라우저에서 언어 참조 문서를 엽니다. CMPivot은 [Azure Log Analytics](https://docs.microsoft.com/azure/kusto/query/)와 동일한 쿼리 언어를 사용합니다.



## <a name="improved-secure-client-communications"></a>개선된 보안 클라이언트 통신
<!--1356889,1358228,1358460-->
모든 Configuration Manager 통신 경로에는 HTTPS 통신을 사용하는 것이 좋지만 일부 고객의 경우 PKI 인증서 관리 오버헤드로 인해 어려울 수 있습니다. Azure AD(Azure Active Directory) 통합이 도입되면서 인증서 요구 사항의 일부는 줄었지만 전체가 없어지지는 않았습니다. 

이번 릴리스에서는 클라이언트가 사이트 시스템과 통신하는 방법이 개선되었습니다. 이러한 개선에는 두 가지 기본 목표가 있습니다.  

- PKI 서버 인증 인증서가 없어도 클라이언트 통신의 보안을 유지할 수 있습니다.  

- 클라이언트는 네트워크 액세스 계정이 없어도 배포 지점에서 콘텐츠에 안전하게 액세스할 수 있습니다.  

> [!Note]  
> PKI 인증서는 해당 인증서를 사용하려는 고객에게 여전히 유효한 옵션입니다.  


### <a name="bkmk_token"></a> 시나리오
다음은 이러한 개선 사항을 활용하는 시나리오입니다.  

#### <a name="bkmk_token1"></a> 시나리오 1: 관리 지점의 클라이언트
<!--1356889-->
[Azure AD 조인 디바이스](/azure/active-directory/devices/concept-azure-ad-join)가 CMG(클라우드 관리 게이트웨이)를 통해 HTTP용으로 구성된 관리 지점과 통신할 수 있습니다. 사이트 서버는 관리 지점에 대한 인증서를 생성하여 보안 채널을 통해 통신할 수 있도록 허용합니다.   

> [!Note]  
> 이 동작은 Configuration Manager 현재 분기 버전 1802에서 변경되어 이 시나리오에 HTTPS 사용 관리 지점이 필요합니다. 자세한 내용은 [HTTPS에 대한 관리 지점 설정](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_mphttps)을 참조하세요.  

#### <a name="bkmk_token2"></a> 시나리오 2: 배포 지점의 클라이언트
<!--1358228-->
작업 그룹 또는 Azure AD 조인 클라이언트는 HTTP용으로 구성된 배포 지점에서 보안 채널을 통해 콘텐츠를 다운로드할 수 있습니다.   

#### <a name="bkmk_token3"></a> 시나리오 3: Azure AD 디바이스 ID 
<!--1358460-->
Azure AD 사용자가 로그인되지 않은 Azure AD 조인 또는 [하이브리드 Azure AD 디바이스](/azure/active-directory/devices/concept-azure-ad-join-hybrid)에서 할당된 사이트와 안전하게 통신할 수 있습니다. 이제 클라우드 기반 디바이스 ID만 있으면 CMG 및 관리 지점을 인증하는 데 충분합니다.  


### <a name="prerequisites"></a>전제 조건  

- HTTP 클라이언트 연결용으로 구성된 관리 지점. 사이트 시스템 역할 속성의 **일반** 탭에서 이 옵션을 설정합니다.  

- HTTP 클라이언트 연결용으로 구성된 배포 지점. 사이트 시스템 역할 속성의 **일반** 탭에서 이 옵션을 설정합니다. **클라이언트의 익명 연결 허용** 옵션을 사용하도록 설정하지 마세요.  

- 클라우드 관리 게이트웨이.  

- 클라우드 관리를 위해 Azure AD에 사이트 등록.  

    - 사이트에 대한 이 필수 구성 요소를 이미 충족한 경우 Azure AD 애플리케이션을 업데이트해야 합니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 다음, **Azure Active Directory 테넌트**를 선택합니다. Azure AD 테넌트를 선택하고 **애플리케이션** 창에서 웹 애플리케이션을 선택한 다음, 리본에서 **애플리케이션 설정 업데이트**를 클릭합니다.  

- Windows 10 버전 1803을 실행하고 Azure AD에 조인된 클라이언트. 이 요구 사항은 기술적으로 [시나리오 3](#bkmk_token3)에만 적용됩니다. 


### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트**를 선택합니다. 사이트를 선택하고 리본 메뉴에서 **속성**을 클릭합니다.  

2. **클라이언트 컴퓨터 통신** 탭으로 전환합니다. **HTTPS 또는 HTTP**에 대한 옵션을 선택한 후, 새로운 **Use Configuration Manager-generated certificates for HTTP site systems**(HTTP 사이트 시스템에 Configuration Manager 생성 인증서 사용) 옵션을 사용하도록 설정합니다.  

유효성을 검사하려면 앞부분의 [시나리오 목록](#bkmk_token)을 참조하세요.

> [!Tip]
> 이번 릴리스에서는 관리 지점이 사이트에서 새 인증서를 받고 구성하려면 최대 30분까지 기다려야 합니다.

이러한 인증서는 Configuration Manager 콘솔에서 볼 수 있습니다. **관리** 작업 공간으로 이동하여 **보안**을 확장하고 **인증서** 노드를 선택합니다. SMS 발급 루트에서 발급한 사이트 서버 역할 인증서뿐만 아니라 **SMS 발급** 루트 인증서를 찾습니다.


### <a name="known-issues"></a>알려진 문제
- 사용자가 소프트웨어 센터에서 사용 가능한 대상으로 지정된 애플리케이션을 볼 수 없습니다.  

- OS 배포 시나리오에는 여전히 네트워크 액세스 계정이 필요합니다.  

- **Use Configuration Manager-generated certificates for HTTP site systems**(HTTP 사이트 시스템에 Configuration Manager 생성 인증서 사용) 옵션을 빠르게 반복적으로 사용 및 사용 안 함으로 설정하면 인증서가 사이트 시스템 역할에 제대로 바인딩되지 않을 수 있습니다. “SMS 발급” 인증서로 발급된 인증서가 Windows Server IIS(인터넷 정보 서비스)의 웹 사이트에 바인딩되어 있지 않습니다. 이 문제를 해결하려면 Windows의 **SMS** 인증서 저장소에서 “SMS 발급”으로 발급된 인증서를 모두 삭제한 다음, smsexec 서비스를 다시 시작하세요.



## <a name="improvements-for-enabling-third-party-software-update-support"></a>타사 소프트웨어 업데이트 지원 개선 사항
<!--1357605-->
[타사 소프트웨어 업데이트 지원](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8803711-3rd-party-patching-scup-integration-with-sccm-co)에 대한 UserVoice 피드백에 따라 이번 릴리스에서는 SCUP(System Center Updates Publisher)와의 통합을 추가로 반복합니다. Configuration Manager Technical Preview [버전 1803](/sccm/core/get-started/capabilities-in-technical-preview-1803#enable-third-party-software-update-support-on-clients)에서는 타사 업데이트를 위해 WSUS에서 인증서를 읽은 다음, 해당 인증서를 클라이언트에 배포하는 기능을 추가했습니다. 그러나 여전히 SCUP 도구를 사용하여 타사 소프트웨어 업데이트에 서명하는 데 필요한 인증서를 만들고 관리해야 했습니다.

이번 릴리스에서는 Configuration Manager 사이트를 사용하여 인증서를 자동으로 구성할 수 있습니다. 사이트는 이러한 용도의 인증서를 생성하기 위해 WSUS와 통신합니다. 그런 다음, Configuration Manager가 계속해서 클라이언트에 해당 인증서를 배포합니다. 이렇게 반복하면 인증을 만들고 관리하는 데 SCUP 도구를 사용할 필요가 없습니다. 

SCUP 도구의 일반적인 용도에 대한 자세한 내용은 [System Center Updates Publisher](/sccm/sum/tools/updates-publisher)를 참조하세요.

### <a name="prerequisites"></a>전제 조건
- **소프트웨어 업데이트** 그룹에서 **타사 소프트웨어 업데이트 사용** 클라이언트 설정을 사용하고 배포합니다.
- WSUS가 소프트웨어 업데이트 지점과 별도의 서버에 있는 경우 원격 WSUS 서버에서 다음 옵션 중 하나를 수행해야 합니다.
    - Windows에서 원격 레지스트리 서비스 사용  
    or
    - 레지스트리 키 `HKLM\Software\Microsoft\Update Services\Server\Setup`에서 `1` 값으로 **EnableSelfSignedCertificates**라는 새 DWORD를 만듭니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트**를 선택합니다. 최상위 사이트를 선택하고 리본에서 **사이트 구성 요소 구성**을 클릭한 다음, **소프트웨어 업데이트 지점**을 선택합니다.  

2. **타사 업데이트** 탭으로 전환합니다. **타사 소프트웨어 업데이트 사용** 옵션을 선택한 다음, **Configuration Manager가 자동으로 인증서 관리** 옵션을 선택합니다.

3. 타사 소프트웨어 업데이트 카탈로그를 가져오기 위한 일반적인 SCUP 워크플로의 나머지 부분을 계속 진행한 후 클라이언트에 업데이트를 배포합니다.



## <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Windows 10 현재 위치 업그레이드 작업 순서 개선 사항
<!--1358500-->

이제 Windows 10 현재 위치 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스가 실패할 경우, 추가할 권장 작업이 있는 새 그룹이 포함되어 있습니다. 이러한 작업을 수행하면 문제를 더 쉽게 해결할 수 있습니다.

### <a name="new-groups-under-run-actions-on-failure"></a>**실패 시 작업 실행** 아래의 새 그룹
- **로그 수집**: 클라이언트에서 로그를 수집하려면 이 그룹의 단계를 추가합니다. 
    - 일반적으로 로그 파일을 네트워크 공유에 복사합니다. 이 연결을 설정하려면 [네트워크 폴더에 연결](/sccm/osd/understand/task-sequence-steps#BKMK_ConnectToNetworkFolder) 단계를 사용하세요. 
    - 복사 작업을 수행하려면 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 또는 [PowerShell 스크립트 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunPowerShellScript) 단계에서 사용자 지정 스크립트나 유틸리티를 사용합니다.
    - 수집할 파일에는 다음과 같은 로그가 포함될 수 있습니다.  
         `%_SMSTSLogPath%\*.log`   
         `%SystemDrive%\$Windows.~BT\Sources\Panther\setupact.log`  
    - setupact.log 및 기타 Windows 설치 로그에 대한 자세한 내용은 [Windows Setup Log files](/windows/deployment/upgrade/log-files)(Windows 설치 로그 파일)를 참조하세요.
    - Configuration Manager 클라이언트 로그에 대한 자세한 내용은 [Configuration Manager 클라이언트 로그](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs)를 참조하세요.
    - _SMSTSLogPath 및 기타 유용한 변수에 대한 자세한 내용은 [작업 순서 기본 제공 변수](/sccm/osd/understand/task-sequence-built-in-variables)를 참조하세요.

- **진단 도구 실행**: 추가 진단 도구를 실행하려면 이 그룹의 단계를 추가합니다. 실패 후 가능한 한 빨리 시스템에서 추가 정보를 수집하려면 이러한 도구를 자동화해야 합니다.
    - 이러한 도구 중 하나는 Windows [SetupDiag](/windows/deployment/upgrade/setupdiag)입니다. 이 도구는 Windows 10 업그레이드 실패 이유에 대한 세부 정보를 얻는 데 사용할 수 있는 독립 실행형 진단 도구입니다.
         - Configuration Manager에서 도구에 대한 [패키지를 만듭니다](/sccm/apps/deploy-use/packages-and-programs#create-a-package-and-program).
         - 이 작업 순서 그룹에 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계를 추가합니다. 도구를 참조하려면 **패키지** 옵션을 사용하세요. 다음 문자열은 예제 **명령줄**입니다.  
             `SetupDiag.exe /Output:"%_SMSTSLogPath%\SetupDiagResults.log" /Mode:Online`



## <a name="cmtrace-installed-with-client"></a>CMTrace가 클라이언트와 함께 설치됨
<!--1357971-->

이제 CMTrace 로그 보기 도구가 Configuration Manager 클라이언트와 함께 자동으로 설치됩니다. 이 도구는 기본적으로 `%WinDir%\ccm\cmtrace.exe`인 클라이언트 설치 디렉터리에 추가됩니다.

> [!Note]  
> CMTrace는 .log 파일 확장명을 열도록 Windows에 자동으로 등록되지  ‘않습니다’.



## <a name="improvement-to-the-configuration-manager-console"></a>Configuration Manager 콘솔 개선 사항
<!--1358202-->
Configuration Manager 콘솔이 다음과 같이 개선되었습니다.

- 이제 [자산 및 호환성] 아래의 디바이스 목록인 [디바이스]에 기본적으로 현재 로그인한 사용자가 표시됩니다. 이 값은 [클라이언트 상태](/sccm/core/clients/manage/monitor-clients#bkmk_indStatus)만큼 최신 상태입니다. 이 값은 사용자가 로그오프하면 지워지고, 로그온한 사용자가 없으면 값이 비어 있습니다. 

### <a name="known-issues"></a>알려진 문제
[디바이스] 노드에서 또는 [디바이스 컬렉션] 노드 아래의 디바이스 목록을 볼 때 현재 로그온한 사용자 값이 비어 있습니다. 이 문제를 해결하려면 이 [SQL 스크립트](https://gallery.technet.microsoft.com/ConfigMgr-1805-BgbUpdateLiv-306ff46c)를 다운로드하세요. 사이트 데이터베이스 서버에서 sp_BgbUpdateLiveData.sql을 실행한 후 관리 지점에서 smsexec 및 sms_notification_server 서비스를 다시 시작하세요.<!--514471-->



## <a name="improvements-to-console-feedback"></a>콘솔 피드백 개선 사항
<!--1357542-->
이번 릴리스에서는 Configuration Manager 콘솔의 새로운 [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback) 메커니즘이 다음과 같이 개선되었습니다.  

- 이제 피드백 대화 상자에서 선택한 옵션, 메일 주소 등의 이전 설정을 기억합니다.  

- 이제 오프라인 피드백을 지원합니다. 콘솔에서 피드백을 저장한 다음, 인터넷에 연결된 시스템에서 Microsoft에 업로드하세요. `cd.latest\SMSSETUP\Tools\UploadOfflineFeedback\UploadOfflineFeedback.exe`에 있는 새로운 오프라인 피드백 업로더 도구를 사용하세요. 필수 명령줄 옵션 및 사용 가능한 옵션을 보려면 `--help` 옵션을 사용하여 도구를 실행하세요. 연결된 시스템은 **petrol.office.microsoft.com**에 액세스해야 합니다.

### <a name="known-issues"></a>알려진 문제
인터넷에 연결된 머신의 콘솔에서 **웃는 얼굴 보내기** 또는 **찡그린 얼굴 보내기**를 사용하는 경우 “피드백을 보내는 중 오류가 발생했습니다.” 메시지가 반환될 수 있습니다. **자세한 내용**을 클릭하면 다음 텍스트가 표시됩니다. `{"Message":""}`. 이 오류는 백 엔드 피드백 시스템의 응답과 관련된 알려진 문제로 인해 발생합니다. 이 오류를 무시할 수 있습니다. Microsoft는 여전히 피드백을 받았습니다. (자세한 내용에 다른 메시지가 표시되는 경우 오프라인 피드백 옵션을 사용하여 나중에 피드백을 다시 보내 보세요.)



## <a name="improvements-to-pxe-enabled-distribution-points"></a>PXE 사용 배포 지점 개선 사항
<!--1357580-->

이번 릴리스에서는 배포 지점에서 [**Windows 배포 서비스 없이 PXE 응답기 사용**](/sccm/core/get-started/capabilities-in-technical-preview-1802#improvements-to-pxe-enabled-distribution-points) 옵션을 사용할 때 다음과 같이 추가로 개선되었습니다.  

- 이 옵션을 사용하면 배포 지점에서 Windows 방화벽 규칙이 자동으로 생성됨  
- 구성 요소 로깅 기능 개선



## <a name="improvement-to-hardware-inventory-for-large-integer-values"></a>큰 정수 값에 대한 하드웨어 인벤토리 개선 사항
<!--1357880-->
하드웨어 인벤토리에 현재 4,294,967,296(2^32)보다 큰 정수에 대한 제한이 있습니다. 하드 드라이브 크기(바이트)와 같은 특성의 경우 이 제한에 도달할 수 있습니다. 관리 지점에서 이 제한을 초과하는 정수 값을 처리하지 않으므로 값이 데이터베이스에 저장되지 않습니다. 이번 릴리스에서는 이 제한이 18,446,744,073,709,551,616(2^64)으로 증가했습니다. 

전체 디스크 크기와 같이 변경되지 않는 값을 가진 속성의 경우 사이트를 업그레이드한 후 바로 값이 표시되지 않을 수 있습니다. 대부분의 하드웨어 인벤토리는 델타 보고서입니다. 클라이언트는 변경되는 값만 전송합니다. 이 동작을 해결하려면 동일한 클래스에 다른 속성을 추가하세요. 이 작업을 수행하면 클라이언트가 변경된 클래스에서 모든 속성을 업데이트합니다. 



## <a name="improvement-to-wsus-maintenance"></a>WSUS 유지 관리 개선 사항
<!--1357898-->

이제 WSUS 정리 마법사에서 대체 규칙에 따라 만료되거나 대체된 업데이트를 거부합니다. 이러한 규칙은 소프트웨어 업데이트 지점 구성 요소 속성에 정의되어 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트**를 선택합니다. 최상위 사이트를 선택하고 리본에서 **사이트 구성 요소 구성**을 클릭한 다음, **소프트웨어 업데이트 지점**을 선택합니다.  

2. **Supersedence Rules**(대체 규칙) 탭으로 전환합니다. **WSUS 정리 마법사를 실행**하는 옵션을 사용합니다. 원하는 대체 동작을 지정합니다.  

3. WSyncMgr.log 파일을 검토합니다.



## <a name="improvement-to-support-for-cng-certificates"></a>CNG 인증서 지원 개선 사항
<!--1357314-->
이번 릴리스부터 다음과 같은 추가 HTTPS 사용 서버 역할에 [CNG 인증서](/sccm/core/plan-design/network/cng-certificates-overview)를 사용합니다.  
- Configuration Manager 정책 모듈을 사용하는 NDES 서버를 포함한 인증서 등록 지점



## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
