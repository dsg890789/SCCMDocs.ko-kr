---
title: "새 버전 1702 | Microsoft 문서"
description: "System Center Configuration Manager 버전 1702에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409e26e1-7716-4f1d-a0ee-34feabf20792
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: a2954b3c6f9a09b7246347e780c4cfc49ba39ca1
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1702-of-system-center-configuration-manager"></a>System Center Configuration Manager 버전 1702의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 현재 분기의 업데이트 1702는 버전 1602, 1606 또는 1610을 실행하는 이전에 설치된 사이트에 대한 콘솔 내 업데이트로 제공됩니다. 새 배포를 설치할 때 이를 기준선 버전으로 사용할 수도 있습니다.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용해야 합니다.  
>  다음에 대해 자세히 알아보세요.    
>   - [새 사이트 설치](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [사이트에 업데이트 설치](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

다음 섹션에서는 Configuration Manager 버전 1702에 도입된 변경 내용 및 새로운 기능에 대한 세부 정보를 제공합니다.  

## <a name="deprecated-features-and-operating-systems"></a>사용되지 않는 기능 및 운영 체제
[제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/removed-and-deprecated-features)에서 구현되기 전의 지원 변경 내용을 알아보세요.

버전 1702에서는 다음 제품이 지원되지 않습니다.
- **SQL Server 2008 R2** - 사이트 데이터베이스 서버에 지원되지 않습니다. 지원 중단은 2015년 7월 10일에 [처음 발표](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database)되었습니다. 1702 이전 버전의 Configuration Manager를 사용하는 경우 이 버전의 SQL Server가 계속 지원됩니다.
- **Windows Server 2008 R2** - 사이트 시스템 서버 및 대부분의 사이트 시스템 역할에 지원되지 않습니다. 지원 중단은 2015년 7월 10일에 [처음 발표](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems)되었습니다. 1702 이전 버전의 Configuration Manager를 사용하는 경우 이 버전의 Windows가 계속 지원됩니다.  
- **Windows Server 2008** - 사이트 시스템 서버 및 대부분의 사이트 시스템 역할에 지원되지 않습니다. 지원 중단은 2015년 7월 10일에 [처음 발표](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems)되었습니다.
- **Windows XP Embedded** - 클라이언트 운영 체제로 지원되지 않습니다. 지원 중단은 2015년 7월 10일에 [처음 발표](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems)되었습니다. 1702 이전 버전의 Configuration Manager를 사용하는 경우 이 버전의 Windows가 계속 지원됩니다.




## <a name="site-infrastructure"></a>사이트 인프라

### <a name="improvements-for-in-console-search"></a>콘솔 내 검색의 향상된 기능
다음은 Configuration Manager 콘솔의 검색 사용에 대한 향상된 기능입니다.
 - **개체 경로:**  
  이제 많은 개체가 **개체 경로**라는 열을 지원합니다.  이 열을 검색하고 표시 결과에 포함하는 경우 각 개체의 경로를 볼 수 있습니다. 예를 들어 응용 프로그램 노드에서 앱 검색을 실행하고 하위 노드도 검색하는 경우 결과 창의 *개체 경로* 열에 반환된 각 개체의 경로가 표시됩니다.   

- **검색 텍스트 보존:**  
  검색 텍스트 상자에 텍스트를 입력한 후 하위 노드 및 현재 노드 검색 간을 전환하는 경우 입력한 텍스트가 이제 보존되어 다시 입력하지 않고 새 검색에 사용할 수 있습니다.

- **하위 노드 검색 결정 보존:**  
 이제 *현재 노드* 또는 *모든 하위 노드* 검색에 대해 선택한 옵션이 작업하는 노드를 변경할 때 유지됩니다. 이 새로운 동작으로 인해 콘솔 내에서 이동할 때 지속적으로 이 결정을 다시 설정할 필요가 없습니다. 기본적으로 콘솔을 열 때 옵션은 현재 노드만 검색입니다.


### <a name="send-feedback-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 피드백 보내기

 콘솔 내 피드백 옵션을 사용하여 개발 팀에게 직접 피드백을 보낼 수 있습니다.

 **피드백** 옵션은 다음 위치에서 찾을 수 있습니다.
 -  리본에서 각 노드의 홈 탭 맨 왼쪽  
    ![리본](./media/feedback-home.png)

 -  콘솔에서 아무 개체나 마우스 오른쪽 단추로 클릭할 때   
     ![마우스 오른쪽 단추 클릭 옵션](./media/feedback-option.png)   

 **피드백**을 선택하면 브라우저에서 [Configuration Manager UserVoice 피드백 웹 사이트](https://go.microsoft.com/fwlink/?linkid=617029)가 열립니다.


###  <a name="changes-for-updates-and-servicing"></a>업데이트 및 서비스의 변경 내용
다음은 업데이트 및 서비스의 변경 내용입니다.

- **노드 위치**   
  버전 1702를 설치한 후 **업데이트 및 서비스** 노드는 **관리** 아래 최상위 노드로 표시됩니다. 더 이상 **Cloud Services** 아래 자식 노드가 아닙니다.

- **새 업데이트 상태**  
  콘솔에서 사용 가능한 업데이트를 보면 두 가지 새로운 상태가 있습니다.  
  - **설치 가능** - 다운로드되어 설치할 준비가 된 업데이트입니다.
  - **다운로드 준비 완료**  - 이 업데이트를 사용할 수 있지만 다운로드되지 않았습니다. 이 업데이트를 다운로드할 수 있지만 더 최근 업데이트로 대체되었습니다.


- **보다 간단한 업데이트 선택**  
  다음에 인프라에 둘 이상의 업데이트를 사용할 수 있는 경우 최신 업데이트만 다운로드됩니다. 예를 들어 현재 사이트 버전이 사용할 수 있는 가장 최근 버전보다 두 버전 이상 이전인 경우 가장 최근 업데이트 버전만 자동으로 다운로드됩니다.  

  가장 최근 버전이 아닌 경우에도 다른 사용 가능한 업데이트를 다운로드하여 설치할 수 있습니다. 이전 업데이트를 다운로드하면 업데이트가 최신 버전으로 바뀌었다는 경고를 받게 됩니다. *다운로드 가능*한 업데이트를 다운로드하려면 콘솔에서 업데이트를 선택하고 **다운로드**를 클릭합니다.

- **이전 업데이트 정리 개선**   
  사이트 서버의 'EasySetupPayload' 폴더에서 불필요한 다운로드를 삭제하는 자동 정리 기능이 추가되었습니다. 이 기능은 버전 1702에 추가되었으므로 업데이트 롤업이나 이후 업데이트 버전 같은 후속 업데이트를 설치한 후 정리가 시작됩니다.  


### <a name="data-warehouse-service-point"></a>데이터 웨어하우스 서비스 지점
 데이터 웨어하우스 서비스 지점을 사용하여 Configuration Manager 배포에 대한 장기 기록 데이터를 저장하고 보고할 수 있습니다.

 데이터 웨어하우스는 최대 2TB의 데이터를 지원하며 변경 내용 추적을 위한 타임스탬프가 있습니다. 데이터 저장은 Configuration Manager 사이트 데이터베이스에서 데이터 웨어하우스 데이터베이스로의 자동화된 동기화를 통해 수행됩니다. 이 정보는 보고 서비스 지점에서 액세스할 수 있습니다.

 자세한 내용은 [데이터 웨어하우스 서비스 지점](/sccm/core/servers/manage/data-warehouse)을 참조하세요.


### <a name="peer-cache-improvements"></a>피어 캐시 개선
 버전 1702부터 피어 캐시 원본 컴퓨터가 다음 조건 중 하나라도 충족할 경우 피어 캐시 원본 컴퓨터는 콘텐츠 요청을 거부합니다.  
  -  배터리 부족 모드에 있는 경우
  -  콘텐츠를 요청 시 CPU 로드가 80%를 초과하는 경우
  -  디스크 I/O에 10을 초과하는 *AvgDiskQueueLength*가 있는 경우
  -  컴퓨터에 대한 연결을 더 이상 사용할 수 없는 경우   
자세한 내용은 [Configuration Manager 클라이언트용 피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)에서 **피어 캐시 원본에 대한 제한된 액세스**를 참조하세요.   

또한 세 가지 새로운 보고서가 보고 지점에 추가되었습니다. 이러한 보고서를 사용하여 관련된 경계 그룹 및 콘텐츠와 같은 거부된 콘텐츠 요청에 대한 자세한 정보를 이해할 수 있습니다. 피어 캐시 항목에서 [모니터링](/sccm/core/plan-design/hierarchy/client-peer-cache#monitoring)을 참조하세요.

### <a name="content-library-cleanup-tool"></a>콘텐츠 라이브러리 정리 도구
 [콘텐츠 라이브러리 정리 도구](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool)를 사용하여 해당 콘텐츠가 더 이상 응용 프로그램과 연결되지 않을 경우 배포 지점에서 콘텐츠를 제거합니다.


### <a name="use-the-oms-connector-with-the-azure-government-cloud"></a>Azure Government 클라우드에서 OMS 커넥터 사용
OMS 커넥터를 사용하여 Microsoft Azure Government 클라우드에 있는 OMS Log Analytics에 연결할 수 있습니다. 이렇게 하려면 커넥터가 Government 클라우드에서 작동할 수 있도록 OMS 커넥터를 설치하기 전에 구성 파일을 수정해야 합니다. 자세한 내용은 [Azure Government 클라우드에서 OMS 커넥터 사용](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig)을 참조하세요.

### <a name="software-update-points-are-added-to-boundary-groups"></a>소프트웨어 업데이트 지점이 경계 그룹에 추가됨
버전 1702부터 클라이언트는 경계 그룹을 사용하여 새 소프트웨어 업데이트 지점을 찾고 더 이상 현재 지점에 액세스할 수 없는 경우 새 소프트웨어 업데이트 지점을 대체하고 찾습니다. 클라이언트가 찾을 수 있는 서버를 제어하기 위해 개별 소프트웨어 업데이트 지점을 다른 경계 그룹에 추가할 수 있습니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups) 항목에서 [소프트웨어 업데이트 지점](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)을 참조하세요.


<!-- ## Migration  -->

<!-- ## Client management  -->

## <a name="compliance-settings"></a>호환성 설정

### <a name="new-compliance-settings-for-ios"></a>iOS에 대한 새 준수 설정

Microsoft Intune에서 제공하는 설정과 일치하도록 iOS 장치에 대한 많은 새로운 설정을 추가했습니다.
모든 사용 가능한 설정 목록은 [Intune으로 관리되는 iOS 및 Mac OS X 장치에 대한 구성 항목 만들기](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)를 참조하세요.


## <a name="application-management"></a>응용 프로그램 관리

### <a name="improved-support-for-windows-store-for-business-apps"></a>비즈니스용 Windows 스토어 앱에 대한 지원 향상

이제 온라인에서 사용이 허가된 앱을 비즈니스용 Windows 스토어에서 Configuration Manager 클라이언트를 통해 관리하는 Windows 10 PC로 배포할 수 있습니다.
자세한 내용은 [비즈니스용 Windows 스토어에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)를 참조하세요.

### <a name="check-for-running-executable-files-before-installing-an-application"></a>응용 프로그램을 설치하기 전에 실행 중인 실행 파일 확인

이제 배포 유형의 **속성** 대화 상자에 있는 **설치 동작** 탭에서 배포 유형의 설치를 차단하는 실행 파일(실행 중일 경우)을 하나 이상 지정할 수 있습니다. 사용자가 실행 중인 실행 파일을 닫아야(또는 필수 용도의 배포를 위해 자동으로 닫힐 수 있음) 배포 유형을 설치할 수 있습니다.

응용 프로그램이 **사용 가능**으로 배포된 경우 최종 사용자가 응용 프로그램을 설치하려고 하면 지정된 실행 중인 실행 파일을 닫아야 설치를 계속할 수 있다는 메시지가 표시됩니다.

응용 프로그램이 **필수**로 배포되었으며 **배포 유형 속성 대화 상자의 설치 동작 탭에 지정한 모든 실행 중인 실행 파일 자동으로 닫기** 옵션이 선택된 경우 응용 프로그램 설치 최종 기한에 도달하면 지정된 실행 파일이 자동으로 닫힌다고 알리는 대화 상자가 표시됩니다.

### <a name="app-management-improvements-for-hybrid-mdm"></a>하이브리드 MDM에 대한 앱 관리 개선

- [장치 컬렉션에 대량 구매한 iOS 앱 배포](#deploy-volume-purchased-ios-apps-to-device-collections)
- [교육용 iOS Volume Purchase Program에 대한 지원](#support-for-ios-volume-purchase-program-for-education)
- [여러 대량 Volume Purchase Program 토큰에 대한 지원](#support-for-multiple-volume-purchase-program-tokens)


## <a name="operating-system-deployment"></a>운영 체제 배포

### <a name="expire-stand-alone-media"></a>독립 실행형 미디어 만료
독립 실행형 미디어를 만드는 경우 미디어에 선택적 시작 및 만료 날짜를 설정하는 새 옵션이 있습니다. 이러한 설정은 기본적으로 사용되지 않습니다. 독립 실행형 미디어를 실행하기 전에 날짜가 컴퓨터의 시스템 시간과 비교됩니다. 시스템 시간이 시작 시간보다 이전이거나 만료 시간보다 이후이면 독립 실행형 미디어가 시작되지 않습니다. New-CMStandaloneMedia PowerShell cmdlet을 사용하여 이러한 옵션을 사용할 수도 있습니다. 자세한 내용은 [독립 실행형 미디어 만들기](/sccm/osd/deploy-use/create-stand-alone-media)를 참조하세요.

### <a name="package-id-displayed-in-task-sequence-steps"></a>작업 순서 단계에서 지연된 패키지 ID
이제 패키지, 드라이버 패키지, 운영 체제 이미지, 부팅 이미지 또는 운영 체제 업그레이드 패키지를 참조하는 모든 작업 순서 단계에 참조된 개체의 패키지 ID가 표시됩니다. 응용 프로그램을 참조하는 작업 순서 단계에 개체 ID가 표시됩니다.

### <a name="support-for-additional-content-in-stand-alone-media"></a>독립 실행형 미디어의 추가 콘텐츠 지원
이제 독립 실행형 미디어에서 추가 콘텐츠가 지원됩니다. 작업 순서에서 참조된 다른 콘텐츠와 함께 미디어에 스테이징할 추가 패키지, 드라이버 패키지 및 응용 프로그램을 선택할 수 있습니다. 이전에는 작업 순서에서 참조된 콘텐츠만 독립 실행형 미디어에 스테이징되었습니다. 자세한 내용은 [독립 실행형 미디어 만들기](/sccm/osd/deploy-use/create-stand-alone-media)를 참조하세요.

### <a name="hardware-inventory-collects-uefi-information"></a>하드웨어 인벤토리를 통해 UEFI 정보 수집
새 하드웨어 인벤토리 클래스(**SMS_Firmware**) 및 속성(**UEFI**)을 사용하여 컴퓨터를 UEFI 모드로 시작할지 여부를 결정할 수 있습니다. 컴퓨터를 UEFI 모드로 시작하는 경우 **UEFI** 속성을 **TRUE**로 설정합니다. 하드웨어 인벤토리에서 기본적으로 사용됩니다. 하드웨어 인벤토리에 대한 자세한 내용은 [하드웨어 인벤토리를 구성하는 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.

### <a name="improvements-to-software-center-warning-messages-for-high-impact-task-sequences"></a>영향력이 큰 작업 순서에 대한 소프트웨어 센터 경고 메시지 개선
이 릴리스에는 영향력이 큰 배포 작업 순서에 대한 소프트웨어 센터 경고 메시지와 관련해서 다음과 같은 개선 사항이 포함되어 있습니다.

- 이제 작업 순서 속성에서 비운영 체제 작업 순서를 비롯한 모든 작업 순서를 높은 위험 수준 배포로 구성할 수 있습니다. 특정 조건을 충족하는 작업 순서는 자동으로 모두 강력한 작업 순서로 정의됩니다. 자세한 내용은 [위험 수준이 높은 배포 관리](/sccm/protect/understand/settings-to-manage-high-risk-deployments)를 참조하세요.
- 작업 순서 속성에서 기본 알림 메시지를 사용하거나 강력한 배포에 대한 고유한 사용자 지정 알림 메시지를 만들 수 있습니다.
- 작업 순서 속성에서 다시 시작을 필수로 설정, 작업 순서의 다운로드 크기 및 예상 실행 시간을 포함하는 소프트웨어 센터 속성을 구성할 수 있습니다.
- 이제 현재 위치 업그레이드에 대한 강력한 배포 기본 메시지에 앱, 데이터 및 설정이 자동으로 마이그레이션된다고 표시됩니다. 이전에는 모든 운영 체제 설치에 대한 기본 메시지에 모든 앱, 데이터 및 설정이 손실된다고 표시되었으며, 이는 현재 위치 업그레이드에 적용되지 않습니다.

자세한 내용은 [강력한 작업 순서 설정 구성](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)을 참조하세요.

### <a name="return-to-previous-page-when-a-task-sequence-fails"></a>작업 순서가 실패할 경우 이전 페이지로 돌아가기
이제 작업 순서를 실행하고 오류가 발생할 때 이전 페이지로 돌아갈 수 있습니다. 이 릴리스 이전에는 오류가 발생할 경우 작업 순서를 다시 시작해야 했습니다. 예를 들어 다음 시나리오에서 **이전** 단추를 사용할 수 있습니다.

- Windows PE에서 컴퓨터를 시작할 경우 작업 순서가 제공되기 전에 작업 순서 부트스트랩 대화 상자가 표시될 수 있습니다. 이 시나리오에서 다음을 클릭하면 사용 가능한 작업 순서가 없다는 메시지와 함께 작업 순서의 최종 페이지가 표시됩니다. 이제 **이전**을 클릭하여 사용 가능한 작업 순서를 다시 검색할 수 있습니다. 작업 순서를 사용할 수 있을 때까지 이 프로세스를 반복할 수 있습니다.
- 작업 순서를 실행하지만 배포 지점에서 종속 콘텐츠 패키지를 아직 사용할 수 없는 경우 작업 순서가 실패합니다. 이제 누락된 콘텐츠를 배포하거나(아직 배포되지 않은 경우) 배포 지점에서 콘텐츠를 사용할 수 있을 때까지 기다린 다음 **이전**을 클릭하여 작업 순서에서 콘텐츠를 다시 검색하도록 할 수 있습니다.

### <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>사용 가능한 배포 및 작업 순서에 대한 사전 캐시 콘텐츠
버전 1702부터 작업 순서의 사용 가능한 배포에 대해 사전 캐시 콘텐츠를 사용할 수 있습니다. 사전 캐시 콘텐츠를 사용하면 클라이언트가 배포를 받는 즉시 해당 콘텐츠만 다운로드할 수 있습니다. 따라서 사용자가 소프트웨어 센터에서 **설치**를 클릭할 때 콘텐츠가 준비되어 있으며, 콘텐츠가 로컬 하드 드라이브에 있으므로 설치가 신속하게 시작됩니다. 자세한 내용은 [사전 캐시 콘텐츠 구성](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)을 참조하세요.

### <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환
Windows 10 크리에이터 업데이트에서는 UEFI 사용 하드웨어에 맞게 하드 디스크를 다시 분할하는 프로세스를 자동화하는 간단한 변환 도구를 소개하고 Windows 7에서 Windows 10으로의 현재 위치 업그레이드 프로세스에 변환 도구를 통합합니다. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구 및 운영 체제 업그레이드 작업 순서와 이 도구를 결합하면 Windows 10 크리에이터 업데이트로의 현재 위치 업그레이드 중에 BIOS에서 UEFI로 컴퓨터를 변환할 수 있습니다. 자세한 내용은 [BIOS-UEFI 변환을 관리하는 작업 순서 단계](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)를 참조하세요.

### <a name="improvements-to-the-install-applications-task-sequence-step"></a>응용 프로그램 설치 작업 순서 단계의 향상된 기능
이 버전에는 다음과 같은 향상된 기능이 추가되었습니다.
- **응용 프로그램 설치** 작업 순서 단계에서 설치할 수 있는 최대 응용 프로그램 수가 99개까지 증가했습니다. 이전의 최대 개수는 응용 프로그램 9개였습니다.
- 작업 순서 편집기에서 **응용 프로그램 설치** 작업 순서 단계에 응용 프로그램을 추가하는 경우 이제 **설치할 응용 프로그램 선택** 창에서 여러 응용 프로그램을 선택할 수 있습니다.

### <a name="improvements-to-the-auto-apply-driver-task-sequence"></a>드라이버 자동 적용 작업 순서의 향상된 기능
이제 새 작업 순서 변수를 사용하여 HTTP 카탈로그 요청 시 드라이버 자동 적용 작업 순서 단계에 대한 시간 제한 값을 구성할 수 있습니다. 다음 변수와 기본값(초)을 사용할 수 있습니다.
   - SMSTSDriverRequestResolveTimeOut  
     기본값: 60
   - SMSTSDriverRequestConnectTimeOut  
     기본값: 60
   - SMSTSDriverRequestSendTimeOut  
     기본값: 60
   - SMSTSDriverRequestReceiveTimeOut  
     기본값: 480

### <a name="windows-10-adk-tracked-by-build-version"></a>Windows 10 ADK가 빌드 버전별로 추적됨
이제 Windows 10 ADK가 빌드 버전별로 추적되므로 Windows 10 부팅 이미지를 사용자 지정할 때 환경에서 더 많은 지원이 제공됩니다. 예를 들어 사이트에서 Windows 10 버전 1607용 Windows ADK를 사용하는 경우 버전 10.0.14393인 부팅 이미지만 콘솔에서 사용자 지정할 수 있습니다. WinPE 버전을 사용자 지정하는 방법에 대한 자세한 내용은 [부팅 이미지 사용자 지정](/sccm/osd/get-started/customize-boot-images)을 참조하세요.

### <a name="default-boot-image-source-path-can-no-longer-be-changed"></a>기본 부팅 이미지 원본 경로를 더 이상 변경할 수 없음
기본 부팅 이미지가 Configuration Manager에서 관리되며, 더 이상 Configuration Manager 콘솔이나 Configuration Manager SDK를 사용하여 기본 부팅 이미지 원본 경로를 변경할 수 없습니다. 사용자 지정 부팅 이미지에 대한 사용자 지정 원본 경로는 계속 구성할 수 있습니다.

### <a name="default-boot-images-are-regenerated-after-upgrading-configuration-manager-to-a-new-version"></a>Configuration Manager를 새 버전으로 업그레이드한 후 기본 부팅 이미지가 다시 생성됨
이 릴리스부터 Windows ADK 버전을 업그레이드한 다음 업데이트 및 설치를 사용하여 최신 버전의 Configuration Manager를 설치하면 Configuration Manager가 기본 부팅 이미지를 다시 생성합니다. 여기에는 업데이트된 Windows ADK의 새 Window PE 버전, 새 Configuration Manager 클라이언트 버전, 드라이버, 사용자 지정 등이 포함됩니다. 사용자 지정 부팅 이미지는 수정되지 않습니다. 자세한 내용은 [부팅 이미지 관리](/sccm/osd/get-started/manage-boot-images#BKMK_BootImageDefault)를 참조하세요.

## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="deploy-office-365-apps-to-clients"></a>클라이언트에 Office 365 앱 배포
버전 1702부터 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 설정을 구성할 수 있는 Office 365 설치 관리자를 시작하고, Office CDN(Content Delivery Network)에서 파일을 다운로드하고, 파일을 Configuration Manager의 응용 프로그램으로 배포할 수 있습니다. 자세한 내용은 [Office 365 ProPlus 업데이트 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)를 참조하세요.

> [!IMPORTANT]
> Configuration Manager의 Office 365 응용 프로그램 마법사를 사용하여 만들고 배포하는 Office 365 앱은 **Office 365 클라이언트 에이전트 관리 사용** 소프트웨어 업데이트 클라이언트 에이전트 설정을 사용할 때까지 Configuration Manager에서 자동으로 관리되지 않습니다. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings)를 참조하세요.

### <a name="manage-express-installation-files-for-windows-10-updates"></a>Windows 10 업데이트에 대한 빠른 설치 파일 관리
버전 1702부터 Configuration Manager는 Windows 10 업데이트에 대한 빠른 설치 파일을 지원합니다. 지원되는 버전의 Windows 10을 사용하는 경우 Configuration Manager 설정을 사용하여 현재 월의 Windows 10 누적 업데이트와 이전 월의 업데이트 간 변경 내용만 다운로드할 수 있습니다. 빠른 설치 파일이 없으면 Configuration Manager는 전체 Windows 10 누적 업데이트(이전 몇 개월의 모든 업데이트 포함)를 매달 다운로드합니다. 빠른 설치 파일을 사용하면 다운로드 크기가 감소하고 클라이언트에서 설치 시간이 단축됩니다. 자세한 내용은 [Windows 10 업데이트에 대한 빠른 설치 파일 관리](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)를 참조하세요.


<!-- ## Reporting  -->

<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>모바일 장치 관리

### <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android 및 iOS 버전은 하이브리드 MDM 만들기 마법사에서 대상 지정이 가능하지 않음

하이브리드 MDM(모바일 장치 관리)에 대한 버전 1702부터 Intune 관리 장치에 대한 새 정책 및 프로필을 만들 때 특정 버전의 Android 및 iOS를 대상으로 지정할 필요가 없습니다. 대신 다음 장치 유형 중 하나를 선택합니다.

- Android
- Samsung KNOX Standard 4.0 이상
- iPhone
- iPad

이 변경 내용은 다음 항목을 만들기 위한 마법사에 영향을 줍니다.

- 구성 항목
- 규정 준수 정책
- 인증서 프로필
- 전자 메일 프로필
- VPN 프로필
- Wi-Fi 프로필

이러한 변경으로 인해 하이브리드 배포에서 새 Configuration Manager 릴리스나 확장 없이 새 Android 및 iOS 버전을 더 빠르게 지원할 수 있습니다. Intune 독립 실행형에서 새 버전이 지원되게 되면 사용자는 모바일 장치를 해당 버전으로 업그레이드할 수 있습니다.

이전 버전의 Configuration Manager에서 업그레이드할 때 문제를 방지하려면 이러한 항목의 속성 페이지에서 모바일 운영 체제 버전을 계속 사용할 수 있습니다. 특정 버전을 대상으로 지정해야 하는 경우 새 항목을 만든 다음 새로 만든 항목의 속성 페이지에서 대상 버전을 지정할 수 있습니다.

### <a name="android-for-work-support"></a>Android for Work 지원
1702부터 이제 Microsoft Intune을 통한 하이브리드 모바일 장치 관리에서 Android for Work 장치 등록 및 관리를 지원합니다. 관리되는 Android for Work 장치 지침:

- [Android for Work 장치 등록](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)
- [Android for Work 앱 승인 및 배포](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Android for Work에 대한 구성 항목 만들기](/sccm/mdm/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-for-work-configuration-items)
- [Android for Work 장치에서 선택적 초기화](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)
- [Android for Work 메일 프로필](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Android for Work 준수 정책](/sccm/mdm/deploy-use/create-compliance-policy)


### <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>장치 컬렉션에 대량 구매한 iOS 앱 배포

이제 사용이 허가된 앱을 사용자 및 장치에 배포할 수 있습니다. 장치 라이선싱을 지원하는 앱 기능에 따라 앱 배포 시 다음과 같이 적절한 라이선스가 청구됩니다.

|||||
|-|-|-|-|
|Configuration Manager 버전|앱이 장치 라이선싱을 지원하나요?|배포 컬렉션 유형|청구된 라이선스|
|1702 이전|예|사용자|사용자 라이선스|
|1702 이전|아니요|사용자|사용자 라이선스|
|1702 이전|예|장치|사용자 라이선스|
|1702 이전|아니요|장치|사용자 라이선스|
|1702 이상|예|사용자|사용자 라이선스|
|1702 이상|아니요|사용자|사용자 라이선스|
|1702 이상|예|장치|장치 라이선스|
|1702 이상|아니요|장치|사용자 라이선스|

대량 구매한 iOS 앱에 대한 자세한 내용은 [대량 구매한 iOS 앱 관리](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)를 참조하세요.

### <a name="support-for-ios-volume-purchase-program-for-education"></a>교육용 iOS Volume Purchase Program에 대한 지원

이제 교육용 iOS Volume Purchase Program에서 구매한 앱을 배포하고 추적할 수도 있습니다.
대량 구매한 iOS 앱에 대한 자세한 내용은 [대량 구매한 iOS 앱 관리](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)를 참조하세요.

### <a name="support-for-multiple-volume-purchase-program-tokens"></a>여러 대량 Volume Purchase Program 토큰에 대한 지원

이제 여러 Apple Volume Purchase Program 토큰을 Configuration Manager와 연결할 수 있습니다.
대량 구매한 iOS 앱에 대한 자세한 내용은 [대량 구매한 iOS 앱 관리](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)를 참조하세요.

### <a name="support-for-line-of-business-apps-in-windows-store-for-business"></a>비즈니스용 Windows 스토어의 LOB(기간 업무) 앱 지원

이제 비즈니스용 Windows 스토어에서 사용자 지정 LOB(기간 업무) 앱을 동기화할 수 있습니다.

### <a name="conditional-access-device-compliance-policy-improvements"></a>조건부 액세스 장치 준수 정책 개선

새 장치 준수 정책 규칙을 사용하면 사용자가 비규격 앱 목록에 포함된 앱을 사용하는 경우 조건부 액세스를 지원하는 회사 리소스에 대한 액세스를 차단할 수 있습니다. 비규격 앱 목록은 관리자가 새 준수 규칙 **설치할 수 없는 앱**을 추가할 때 정의할 수 있습니다. 이 규칙을 사용하려면 관리자가 비규격 목록에 앱을 추가할 때 **앱 이름**, **앱 ID** 및 **앱 게시자**(선택 사항)를 입력해야 합니다. 이 설정은 iOS 및 Android 장치에만 적용됩니다.

또한 이렇게 하면 조직에서 보안되지 않은 앱을 통한 데이터 누출을 완화하고 특정 앱을 통한 과도한 데이터 사용을 방지할 수 있습니다.

- 자세한 내용은 [장치 준수 정책의 작동 방식](/sccm/mdm/deploy-use/device-compliance-policies)을 참조하세요.
- 자세한 내용은 [장치 준수 정책을 만드는 방법](/sccm/mdm/deploy-use/create-compliance-policy)을 참조하세요.

### <a name="new-mobile-threat-defense-monitoring-tools"></a>새로운 Mobile Threat Defense 모니터링 도구

버전 1702부터 Mobile Threat Defense 서비스 공급자를 통해 준수 상태를 모니터링하는 새로운 방법이 있습니다.

- [Mobile Threat Defense 준수를 모니터링하는 방법](https://docs.microsoft.com/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance)을 자세히 알아보세요.

## <a name="protect-devices"></a>장치 보호

### <a name="detect-outdated-antimalware-client-versions"></a>오래된 맬웨어 방지 클라이언트 버전 감지
버전 1702부터 Endpoint Protection 클라이언트가 오래되지 않았는지 확인하도록 경고를 구성할 수 있습니다. 자세한 내용은 [오래된 맬웨어 클라이언트에 대한 경고](/sccm/protect/deploy-use/endpoint-configure-alerts#detect-outdated-antimalware-client-versions)를 참조하세요.

### <a name="device-health-attestation-updates"></a>장치 상태 증명 업데이트
이제 관리 지점에서 온-프레미스 클라이언트에 대한 장치 상태 증명 서비스를 구성하고 관리할 수 있습니다. 자세한 내용은 [상태 증명](/sccm/core/servers/manage/health-attestation)을 참조하세요.

### <a name="certificate-profiles-for-windows-hello-for-business"></a>비즈니스용 Windows Hello 인증서 프로필

인증서를 비즈니스용 Windows Hello 키 컨테이너에 저장하려고 하고 인증서 프로필에 스마트 카드 로그온 EKU를 사용하는 경우 인증서가 제대로 유효성이 검사되었는지 확인하려면 키 등록에 대해 사용 권한을 구성해야 합니다.
자세한 내용은 [비즈니스용 Windows Hello 설정](/sccm/protect/deploy-use/windows-hello-for-business-settings)을 참조하세요.

### <a name="new-windows-hello-for-business-notification-for-end-users"></a>최종 사용자에 대한 새 비즈니스용 Windows Hello 알림
새 Windows 10 알림은 비즈니스용 Windows Hello 설치를 완료하기 위해 추가 작업(예: PIN 설정)을 수행해야 한다고 최종 사용자에게 알립니다.

