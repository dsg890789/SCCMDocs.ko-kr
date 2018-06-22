---
title: 기술 미리 보기 1803
titleSuffix: Configuration Manager
description: Configuration Manager 기술 미리 보기 버전 1803에서 사용할 수 있는 새 기능에 대해 알아봅니다.
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 56dc4b07-5aa4-43e2-9be8-d26ae5ff5613
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: dc4dc88b2a8fa9ba075fee51e187e02ae55c2cce
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32344520"
---
# <a name="capabilities-in-technical-preview-1803-for-system-center-configuration-manager"></a>System Center Configuration Manager용 기술 미리 보기 1803의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 아티클에서는 Configuration Manager용 기술 미리 보기 버전 1803에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 기술 미리 보기 사이트를 업데이트하고 새 기능을 추가할 수 있습니다. 

이 업데이트를 설치하기 전에 [기술 미리 보기](/sccm/core/get-started/technical-preview) 아티클을 살펴보세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template   
## Known Issues in this Technical Preview:
-   **Issue Name**. Details
    Workaround details.
-->


</br>

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  



 
## <a name="pull-distribution-points-support-cloud-distribution-points-as-source"></a>풀(pull) 배포 지점은 클라우드 배포 지점을 원본으로 지원합니다.  
<!--1321554-->
많은 고객은 WAN을 통해 원본 배포 지점에서 콘텐츠를 다운로드하는 원격 사무실 또는 지사에서 [풀(pull) 배포 지점](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)을 사용합니다. 원격 사무실의 인터넷 연결 속도가 더 빠르거나 WAN 링크에 대한 로드를 줄이려는 경우 이제 Microsoft Azure의 [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)을 원본으로 사용할 수 있습니다. 배포 지점 속성의 **풀(pull) 배포 지점** 탭에 원본을 추가하면 이제 사이트의 모든 클라우드 배포 지점이 사용 가능한 배포 지점으로 나열됩니다. 그렇지 않을 경우 두 사이트 시스템 역할의 동작이 동일하게 유지됩니다. 

### <a name="prerequisites"></a>필수 구성 요소
- 풀(pull) 배포 지점은 인터넷에 액세스할 수 있어야 Microsoft Azure와 통신할 수 있습니다.
- 콘텐츠는 원본 클라우드 배포 지점에 배포되어야 합니다.

> [!Note]  
> 이 기능은 데이터 저장 및 네트워크 출력에 대한 Azure 구독에 요금을 부과합니다. 자세한 내용은 [클라우드 기반 배포 사용 비용](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#BKMK_CloudDPCost)을 참조하세요.



## <a name="partial-download-support-in-client-peer-cache-to-reduce-wan-utilization"></a>WAN 사용률을 줄이기 위해 클라이언트 피어 캐시에서 부분 다운로드 지원
<!--1357346-->
클라이언트 피어 캐시 원본은 이제 콘텐츠를 여러 부분으로 나눌 수 있습니다. 이러한 부분은 네트워크 전송을 최소화하여 WAN 사용률을 줄입니다. 관리 지점은 콘텐츠 부분의 더 자세한 추적을 제공합니다. 경계 그룹별로 동일한 콘텐츠의 2회 이상 다운로드를 제거하려고 시도합니다. 

### <a name="example-scenario"></a>예제 시나리오 
Contoso는 본사(HQ)와 지사라는 두 경계 그룹이 있는 단일 주 사이트를 운영합니다. 경계 그룹 간에는 30분의 대체 관계가 있습니다. 사이트의 관리 지점 및 배포 지점은 HQ 경계에만 있습니다. 지사 위치에는 로컬 배포 지점이 없습니다. 지사의 네 클라이언트 중 두 개는 피어 캐시 원본으로 구성됩니다. 

![예제 시나리오에 설명된 네트워크 구성의 다이어그램](media/1357346-peer-cache-source-parts.png)

1. 지사의 네 가지 클라이언트 모두에 대한 콘텐츠가 포함된 배포를 대상으로 합니다. 배포 지점에만 콘텐츠를 배포합니다.
2. Client3 및 Client4에는 배포를 위한 로컬 원본이 없습니다. 관리 지점은 클라이언트가 원격 경계 그룹에 대체되기 전에 30분을 대기하도록 지시합니다.
3. Client1(PCS1)은 관리 지점으로 정책을 새로 고치는 첫 번째 피어 캐시 원본입니다. 이 클라이언트는 피어 캐시 원본으로 사용 가능하므로 관리 지점은 이 클라이언트에게 배포 지점에서 A 부분을 즉시 다운로드하도록 지시합니다.  
4. Client2(PCS2)가 관리 지점에 연결되면 A 부분이 이미 진행 중이지만 아직 완료되지 않았으므로 관리 지점은 이 클라이언트에게 배포 지점에서 B 부분을 즉시 다운로드하도록 지시합니다.
5. PCS1은 A 부분의 다운로드가 완료되면 즉시 관리 지점에 알립니다. B 부분이 이미 진행 중이지만 아직 완료되지 않은 경우 관리 지점은 이 클라이언트에게 배포 지점에서 C 부분을 즉시 다운로드하도록 지시합니다.
6. PCS2는 B 부분의 다운로드가 완료되면 즉시 관리 지점에 알립니다. 관리 지점은 이 클라이언트에게 배포 지점에서 D 부분을 다운로드하도록 지시합니다. 
7. PCS1은 C 부분의 다운로드가 완료되면 즉시 관리 지점에 알립니다. 관리 지점은 이 클라이언트에게 원격 배포 지점에서 사용할 수 있는 부분이 더 이상 없음을 알립니다. 관리 지점은 이 클라이언트에게 해당 로컬 피어 PCS2에서 B 부분을 다운로드하도록 지시합니다.
8. 이 프로세스는 두 클라이언트 피어 캐시 원본이 서로의 모든 부분을 다운로드할 때까지 계속됩니다. 관리 지점은 피어 캐시 원본에게 로컬 피어에서 부분을 다운로드하도록 지시하기 전에 원격 배포 지점에서 부분의 우선 순위를 지정합니다. 
9. Client3은 30분 대체 기간이 만료된 후 처음으로 정책을 새로 고칩니다. 이제 관리 지점에 다시 확인하면 관리 지점에서 클라이언트에게 새 로컬 원본을 알려줍니다. WAN을 통해 배포 지점에서 콘텐츠를 전체적으로 다운로드하는 대신 클라이언트 피어 캐시 원본 중 하나에서 콘텐츠를 전체적으로 다운로드합니다. 클라이언트는 로컬 피어 원본의 우선 순위를 지정합니다. 

> [!Note]  
> 클라이언트 피어 캐시 원본 수가 콘텐츠 부분 수보다 큰 경우 관리 지점은 일반 클라이언트처럼 추가 캐시 원본에 대체 대기를 지시합니다. 


### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. 평소와 같이 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups) 및 [피어 캐시 원본](/sccm/core/plan-design/hierarchy/client-peer-cache)을 설정합니다.
2. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트**를 선택합니다. 리본에서 **계층 구조 설정**을 클릭합니다. 
3. **일반** 탭에서 **콘텐츠를 여러 부분으로 분할하도록 클라이언트 피어 캐시 원본을 구성**하는 옵션을 활성화합니다. 
4. 콘텐츠로 필수 배포를 만듭니다.  

   > [!Note]  
   > 이 기능은 클라이언트가 필수 배포 등을 사용하여 백그라운드로 콘텐츠를 다운로드할 때만 작동합니다. 사용자가 소프트웨어 센터에서 사용 가능한 배포를 설치하는 경우와 같은 요청 시 다운로드는 평소와 같이 작동합니다.  

1. 콘텐츠를 여러 부분으로 나누어 다운로드를 처리하는 것을 보려면 피어 캐시 원본의 **ContentTransferManager.log**와 관리 지점의 **MP_Location.log**를 확인합니다.  
 



## <a name="maintenance-windows-in-software-center"></a>소프트웨어 센터의 유지 관리 기간
<!--1358131-->
소프트웨어 센터는 이제 다음 예약된 유지 관리 기간을 표시합니다. 설치 상태 탭에서 보기를 모두에서 예정으로 전환합니다. 시간 범위와 예약된 배포 목록을 표시합니다. 향후 유지 관리 기간이 없으면 목록은 비어 있습니다. 

![설치 상태 탭에서 예정된 배포 목록을 보여주는 소프트웨어 센터](media/1358131-software-center-maintenance-windows.png)


## <a name="custom-tab-for-webpage-in-software-center"></a>소프트웨어 센터의 웹 페이지용 사용자 지정 탭
<!--1358132-->
이제 소프트웨어 센터에서 사용자 지정된 탭을 만들어 웹 페이지를 열 수 있습니다. 이 기능을 사용하면 일관되고 신뢰할 수 있는 방식으로 최종 사용자에게 콘텐츠를 보여줄 수 있습니다.  다음 목록에는 몇 가지 예가 포함되어 있습니다.
- IT 연락처: 조직의 IT 부서에 문의하는 방법에 대한 정보
- IT 지원 센터: 기술 자료 검색 또는 지원 티켓 열기와 같은 IT 셀프 서비스 작업
- 최종 사용자 설명서: 조직의 사용자가 응용 프로그램을 사용하는 방법이나 Windows 10으로 업그레이드하는 방법과 같은 다양한 IT 토픽에 대한 아티클


### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. Configuration Manager 콘솔, **관리** 작업 영역, **클라이언트 설정** 노드에서 **기본 클라이언트 설정** 정책을 엽니다.
2. **소프트웨어 센터** 그룹을 선택합니다.
3. **소프트웨어 센터 설정**에 대해 **사용자 지정**을 클릭합니다.
4. **탭** 탭으로 전환합니다.
5. **소프트웨어 센터용 사용자 지정 탭 지정** 옵션을 사용합니다.
    1. **탭 이름** 텍스트 필드에 이름을 입력합니다. 이 이름은 소프트웨어 센터의 사용자에게 표시됩니다.
    2. **콘텐츠 URL** 텍스트 필드에 유효한 URL을 입력합니다. 이 URL은 사용자가 이 탭을 클릭할 때 소프트웨어 센터가 표시하는 콘텐츠입니다.

> [!Tip]  
> 소프트웨어 센터는 웹 페이지를 렌더링하기 위해 Internet Explorer 구성 요소를 사용합니다.

## <a name="enable-third-party-software-update-support-on-clients"></a>클라이언트에서 타사 소프트웨어 업데이트 지원 사용

이제 타사 소프트웨어 업데이트를 위해 Configuration Manager 클라이언트 구성을 사용할 수 있습니다. SUP 구성 요소 속성에 대해 **타사 소프트웨어 업데이트 사용**을 설정하면 SUP가 타사 업데이트를 위해 WSUS에서 사용하는 서명 인증서를 다운로드합니다. <!--1357605-->

클라이언트 설정에서 **타사 소프트웨어 업데이트 사용**을 선택하면 다음 작업이 수행됩니다. 
- 클라이언트에서 '인트라넷 Microsoft 업데이트 서비스 위치에 대해 서명된 업데이트 허용' 정책을 설정합니다. 
- 클라이언트의 신뢰할 수 있는 게시자 저장소에 서명 인증서를 설치합니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. Configuration Manager 계층의 최상위 사이트에서 **관리** 노드로 이동하여 **사이트 구성**을 확장한 다음, **사이트**를 확장합니다.
2. 최상위 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **사이트 구성 요소 구성**, **소프트웨어 업데이트 지점**을 차례로 선택합니다.
3. **타사 업데이트** 탭을 클릭하고 **타사 소프트웨어 업데이트 사용**을 선택합니다.
4. **클라이언트 설정**을 열고 **소프트웨어 업데이트**에 대한 설정으로 이동합니다.
5. **타사 소프트웨어 업데이트 사용**이 **예**로 설정되었는지 확인합니다.

## <a name="enable-copypaste-of-asset-details-from-monitoring-views"></a>모니터링 보기에서 자산 정보의 복사/붙여넣기 사용
이제 [사용자 음성 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/20234866-allow-us-to-copy-information-out-of-the-asset-det)의 결과로 배포 및 배포 상태 모니터링 보기의 자산 세부 정보 창에서 복사/붙여넣기 기능을 사용할 수 있습니다.  <!--1357552-->

## <a name="scap-extensions"></a>SCAP 확장
SCAP 확장의 시험판 버전은 SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi 아래에 있는 Cd.latest 폴더에 있습니다. SCAP 확장의 이 시험판 버전은 현재 지원되는 모든 버전의 Configuration Manager 현재 분기 및 LTSB 1606에 설치할 수 있습니다. 자세한 내용은 [SCAP(Security Content Automation Protocol) 확장 정보](/sccm/compliance/plan-design/scap/about-scap)를 참조하세요.



## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
