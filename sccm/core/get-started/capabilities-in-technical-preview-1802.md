---
title: Technical Preview 1802 | Microsoft Docs
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1802에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4884a2d3-13ce-44e5-88c4-a66dc7ec6014
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 7ff02203efac1802db166fef4a1c5a65d1b72615
ms.sourcegitcommit: ef3fdf21180e43afd7af6c8264524711435e426e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54898531"
---
# <a name="capabilities-in-technical-preview-1802-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1802의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1802에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 

이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 검토하세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template   
## Known Issues in this Technical Preview:
-   **Issue Name**. Details
    Workaround details.
-->
## <a name="known-issues-in-this-technical-preview"></a>이 기술 미리 보기의 알려진 문제
- **수동 모드의 사이트 서버가 있는 경우 새 미리 보기 버전에 대한 업데이트가 실패합니다**. [수동 모드의 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 경우 이 새 미리 보기 버전으로 업데이트하기 전에 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 업데이트를 완료한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.
  <!--sms 489412-->


</br>

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  


## <a name="transition-endpoint-protection-workload-to-intune-using-co-management"></a>공동 관리를 사용하여 Endpoint Protection 워크로드를 Intune으로 전환    
<!-- 1357365 --> 이 릴리스에서는 이제 공동 관리를 사용하도록 설정한 후 Configuration Manager에서 Intune으로 Endpoint Protection 워크로드를 전환할 수 있습니다. Endpoint Protection 워크로드를 전환하려면 공동 관리 속성 페이지로 이동한 다음, 슬라이더 막대를 Configuration Manager에서 **파일럿** 또는 **모두**로 이동합니다. 자세한 내용은 [Windows 10 디바이스의 공동 관리](/sccm/core/clients/manage/co-management-overview)를 참조하세요.


 
## <a name="configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups"></a>Configuration Manager 경계 그룹을 사용하도록 Windows 배달 최적화 구성
<!-- 1324696 --> Configuration Manager 경계 그룹을 사용하여 회사 네트워크 및 원격 사무실에 대한 콘텐츠 배포를 정의하고 규정합니다. [Windows 배달 최적화](/windows/deployment/update/waas-delivery-optimization)는 Windows 10 디바이스 간에 콘텐츠를 공유하는 클라우드 기반의 피어 투 피어 기술입니다. 이 릴리스부터는 피어 간에 콘텐츠를 공유할 때 경계 그룹을 사용하도록 배달 최적화를 구성합니다. 새 클라이언트 설정은 경계 그룹 식별자를 클라이언트의 배달 최적화 그룹 식별자로 적용합니다. 클라이언트는 배달 최적화 클라우드 서비스와 통신할 때 이 식별자를 사용하여 원하는 콘텐츠가 있는 피어를 찾습니다. 

### <a name="prerequisites"></a>필수 구성 요소
- 배달 최적화는 Windows 10 클라이언트에서만 사용할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. Configuration Manager 콘솔, **관리** 작업 영역, **클라이언트 설정** 노드에서 사용자 지정 클라이언트 디바이스 설정 정책을 만듭니다.
2. 새 **배달 최적화** 그룹을 선택합니다.
3. **배달 최적화 그룹 ID에 Configuration Manager 경계 그룹 사용** 설정을 사용하도록 설정합니다.

자세한 내용은 [배달 최적화 옵션](/windows/deployment/update/waas-delivery-optimization#group-id)에서 **그룹** 배달 모드 옵션을 참조하세요.



## <a name="windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway"></a>클라우드 관리 게이트웨이를 통한 Windows 10 현재 위치 업그레이드 작업 순서
<!-- 1357149 -->

이제 Windows 10 [내부 업그레이드 작업 순서](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)에서 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 통해 관리되는 인터넷 기반 클라이언트에 대한 배포를 지원합니다. 이 기능을 사용하면 원격 사용자가 회사 네트워크에 연결할 필요 없이 Windows 10으로 쉽게 업그레이드할 수 있습니다. 

내부 업그레이드 작업 순서에서 참조하는 모든 콘텐츠가 [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)에 배포되었는지 확인합니다. 배포되지 않은 경우 디바이스에서 작업 순서를 실행할 수 없습니다.

업그레이드 작업 순서를 배포하는 경우 다음 설정을 사용합니다.
- 배포의 사용자 환경 탭에 있는 **작업 순서가 인터넷을 통해 클라이언트에 대해 실행되도록 허용**.
- 배포의 배포 지점 탭에 있는 **작업 순서를 시작하기 전에 모든 콘텐츠를 로컬에 다운로드**. **실행 중인 작업 순서에 따라 필요 시 로컬로 콘텐츠 다운로드** 등의 기타 옵션은 이 시나리오에서 작동하지 않습니다. 작업 순서 엔진은 현재 클라우드 배포 지점에서 콘텐츠를 가져올 수 없습니다. 작업 순서를 시작하기 전에 구성 관리자 클라이언트가 클라우드 배포 지점에서 콘텐츠를 다운로드해야 합니다.
- (*선택 사항*) 배포의 일반 탭에 있는 **이 작업 순서에 대한 콘텐츠 사전 다운로드**. 자세한 내용은 [사전 캐시 콘텐츠 구성](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)을 참조하세요.



## <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Windows 10 현재 위치 업그레이드 작업 순서 개선 사항
<!-- 1357425 --> 이제 Windows 10 내부 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스 전후에 추가할 권장 작업이 있는 추가 그룹이 포함되어 있습니다. 이러한 작업은 디바이스를 Windows 10으로 성공적으로 업그레이드한 많은 고객들에게 공통적으로 적용됩니다. 

### <a name="new-groups-under-prepare-for-upgrade"></a>**업그레이드 준비** 중인 새 그룹
- **배터리 확인**: 컴퓨터가 배터리를 사용하는지, 전원에 연결되어 있는지 확인하려면 이 그룹에 단계를 추가합니다. 이 작업에서 배터리 확인을 수행하려면 사용자 지정 스크립트 또는 유틸리티가 필요합니다.
- **네트워크/유선 연결 확인**: 컴퓨터가 네트워크에 연결되어 있고 무선 연결을 사용하지 않는지 여부를 확인하려면 이 그룹에 단계를 추가합니다. 이 작업에서 배터리 확인을 수행하려면 사용자 지정 스크립트 또는 유틸리티가 필요합니다.
- **호환되지 않는 애플리케이션 제거**: 이 Windows 10 버전과 호환되지 않는 애플리케이션을 모두 제거하려면 이 그룹에 단계를 추가합니다. 애플리케이션을 제거하는 방법은 다양합니다. 애플리케이션이 Windows Installer를 사용하는 경우 애플리케이션의 Windows Installer 배포 유형 속성에 있는 **프로그램** 탭의 **제거 프로그램** 명령줄을 복사합니다. 그런 다음, 제거 프로그램 명령줄을 사용하여 이 그룹의 **명령줄 실행** 단계를 추가합니다. 예: </br>`msiexec /x {150031D8-1234-4BA8-9F52-D6E5190D1CBA} /q`</br> 
- **호환되지 않는 드라이버 제거**: 이 Windows 10 버전과 호환되지 않는 드라이버를 모두 제거하려면 이 그룹에 단계를 추가합니다.
- **타사 보안 제거/일시 중단**: 바이러스 백신 소프트웨어와 같은 타사 보안 프로그램을 제거하거나 일시 중단하려면 이 그룹에 단계를 추가합니다.
   - 타사 디스크 암호화 프로그램을 사용하는 경우 **/ReflectDrivers** [명령줄 옵션](/windows-hardware/manufacture/desktop/windows-setup-command-line-options)을 사용하여 Windows 설치 프로그램에 해당 암호화 드라이버를 제공합니다. 이 그룹의 작업 순서에 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계를 추가합니다. 작업 순서 변수를 **OSDSetupAdditionalUpgradeOptions**로 설정합니다. 드라이버 경로를 사용하여 값을 **/ReflectDriver**로 설정합니다. 이 [작업 순서 작업 변수](/sccm/osd/understand/task-sequence-action-variables#upgrade-operating-system)는 작업 순서에서 사용되는 Windows 설치 명령줄을 추가합니다. 이 프로세스에 대한 추가 지침은 소프트웨어 공급업체에 문의하세요.

### <a name="new-groups-under-post-processing"></a>**사후 처리** 아래의 새 그룹
- **설치 기반 드라이버 적용**: 패키지에서 설치 기반 드라이버(.exe)를 설치하려면 이 그룹에 단계를 추가합니다.
- **타사 보안 설치/사용**: 바이러스 백신 소프트웨어와 같은 타사 보안 프로그램을 설치하거나 사용하도록 설정하려면 이 그룹에 단계를 추가합니다. 
- **Windows 기본 앱 및 연결 설정**: Windows 기본 앱과 파일 연결을 설정하려면 이 그룹에 단계를 추가합니다. 먼저 원하는 앱 연결을 사용하여 참조 컴퓨터를 준비합니다. 그런 후에 다음 명령줄을 실행하여 내보냅니다. </br>`dism /online /Export-DefaultAppAssociations:"%UserProfile%\Desktop\DefaultAppAssociations.xml"`</br>패키지에 XML 파일을 추가합니다. 그런 다음, 이 그룹의 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계를 추가합니다. XML 파일이 포함된 패키지를 지정한 후 다음 명령줄을 지정합니다. </br>`dism /online /Import-DefaultAppAssociations:DefaultAppAssocations.xml`</br> 자세한 내용은 [기본 애플리케이션 연결 내보내기 또는 가져오기](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations)을 참조하세요.
- **사용자 지정 및 개인 설정 적용**: 프로그램 그룹 구성 등의 시작 메뉴 사용자 지정을 적용하려면 이 그룹에 단계를 추가합니다. 자세한 내용은 [시작 화면 사용자 지정](/windows-hardware/manufacture/desktop/customize-the-start-screen)을 참조하세요.

### <a name="additional-recommendations"></a>추가 권장 사항
- [Windows 10 업그레이드 오류를 해결](/windows/deployment/upgrade/resolve-windows-10-upgrade-errors)하려면 Windows 설명서를 검토하세요. 이 문서에는 업그레이드 프로세스에 대한 자세한 정보도 포함되어 있습니다.
- 기본 **확인 준비** 단계에서 **사용 가능한 최소 디스크 공간(MB) 확인**을 사용하도록 설정합니다. 32비트 OS 업그레이드 패키지의 경우 이 값을 **16384**(16GB) 이상으로 설정하고, 64비트의 경우 **20480**(20GB) 이상으로 설정합니다. 
- **SMSTSDownloadRetryCount** [기본 제공 작업 순서 변수](/sccm/osd/understand/task-sequence-built-in-variables)를 사용하여 정책 다운로드를 다시 시도합니다. 현재, 클라이언트가 기본적으로 두 번 다시 시도하므로 이 변수는 2로 설정되어 있습니다. 클라이언트가 유선 회사 네트워크 연결을 사용하지 않는 경우 추가로 다시 시도하면 클라이언트가 정책을 가져오는 데 도움이 됩니다. 이 변수를 사용해도 정책을 다운로드할 수 없는 경우 오류가 지연되는 점 이외의 다른 부작용은 없습니다.<!-- 501016 --> 또한 **SMSTSDownloadRetryDelay** 변수를 기본값인 15초에서 늘립니다.
- 인라인 호환성 평가를 수행합니다. 
   - **업그레이드 준비** 그룹의 초기에 두 번째 **운영 체제 업그레이드** 단계를 추가합니다. 이름을 *업그레이드 평가*로 지정합니다. 동일한 업그레이드 패키지를 지정한 후 **업그레이드를 시작하지 않고 Windows 설치 프로그램 호환성 검사 수행** 옵션을 사용하도록 설정합니다. 옵션 탭에서 **오류 발생 시 계속**을 사용하도록 설정합니다. 
   - 이 *업그레이드 평가* 단계 바로 뒤에 **명령줄 실행** 단계를 추가합니다. 다음 명령줄을 지정합니다.</br> `cmd /c exit %_SMSTSOSUpgradeActionReturnCode%`</br>**옵션** 탭에서 다음 조건을 추가합니다. </br>`Task Sequence Variable _SMSTSOSUpgradeActionReturnCode not equals 3247440400` </br>이 반환 코드는 문제없이 호환성 검사에 성공하는 MOSETUP_E_COMPAT_SCANONLY(0xC1900210)에 해당하는 10진 코드입니다. *업그레이드 평가* 단계가 성공하고 이 코드를 반환하는 경우 이 단계를 건너뜁니다. 또는 평가 단계가 다른 반환 코드를 반환하는 경우 이 단계에서 작업 순서가 실패하고 Windows 설치 호환성 검사의 반환 코드가 표시됩니다.
   - 자세한 내용은 [운영 체제 업그레이드](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS)를 참조하세요.
- 이 작업 순서 중에 디바이스를 BIOS에서 UEFI로 변경하려는 경우 [현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)을 참조하세요.

추가 권장 사항이나 제안이 있는 경우 리본의 **홈** 탭에서 **피드백**을 전송하세요.



## <a name="improvements-to-pxe-enabled-distribution-points"></a>PXE 사용 배포 지점 개선 사항
<!-- 1357580 --> Technical Preview 버전 1706에서 처음 도입된 [새 PXE 기능](/sccm/core/get-started/capabilities-in-technical-preview-1706#pxe-network-boot-support-for-ipv6)의 동작을 명확히 나타내기 위해 **IPv6 지원** 옵션의 이름을 바꾸었습니다. 배포 지점 속성의 **PXE** 탭에서 **Windows 배포 서비스 없이 PXE 응답기 사용**을 선택합니다. 

이 옵션은 배포 지점에서 WDS(Windows 배포 서비스)가 필요하지 않은 PXE 응답기를 사용하도록 설정합니다. 이미 PXE를 사용하는 배포 지점에서 이 새로운 옵션을 사용하도록 설정하면 Configuration Manager가 WDS 서비스를 일시 중단합니다. 이 새로운 옵션을 사용하지 않도록 설정하지만 여전히 **클라이언트에 PXE 지원을 사용**하는 경우에는 배포 지점에서 WDS를 다시 사용하도록 설정합니다.

WDS가 필요하지 않으므로 PXE 사용 배포 지점은 Windows Server Core를 포함하여 클라이언트 또는 서버 운영 체제일 수 있습니다. 이 새로운 PXE 응답기 서비스는 계속 IPv6을 지원하므로 원격 사무실에서 PXE 사용 배포 지점의 유연성도 향상됩니다.

> [!NOTE]
> 이 서비스는 Technical Preview 버전 1712의 [클라이언트 기반 PXE 응답기 서비스](/sccm/core/get-started/capabilities-in-technical-preview-1712#client-based-pxe-responder-service)와 동일한 기본 기술을 사용합니다. 이 기능에는 배포 지점 역할의 오버헤드가 필요하지 않습니다.

### <a name="multicast"></a>멀티캐스트
배포 지점 속성의 **멀티캐스트** 탭에서 멀티캐스트를 사용하도록 설정하고 구성하려면 배포 지점이 WDS를 사용해야 합니다. 
- **클라이언트에 PXE 지원을 사용**하고 **멀티캐스트를 통해 여러 클라이언트에 데이터를 동시에 전송하도록 허용**하는 경우에는 **Windows 배포 서비스 없이 PXE 응답기를 사용**할 수 없습니다.
- **클라이언트에 PXE 지원을 사용**하고 **Windows 배포 서비스 없이 PXE 응답기를 사용**하도록 설정하는 경우에는 **멀티캐스트를 통해 여러 클라이언트에 데이터를 동시에 전송하도록 허용**할 수 없습니다.



## <a name="deployment-templates-for-task-sequences"></a>작업 순서에 대한 배포 템플릿
<!-- 1357391 --> 작업 순서에 대한 배포 마법사에서 이제 배포 템플릿을 만들 수 있습니다. 배포 템플릿을 저장하고 기존 작업 순서나 새 작업 순서에 적용하여 배포를 만들 수 있습니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기  
작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다. 

 **새 작업 순서 배포에 대한 배포 템플릿 만들기** <br/> 
1. **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.
2. 작업 순서를 마우스 오른쪽 단추로 클릭하고 **배포**를 선택합니다. 
3. **일반** 탭에 이제 **배포 템플릿 선택** 옵션 한 개가 있습니다. 
4. **소프트웨어 배포 마법사**를 계속 진행하고 작업 순서에 대한 배포 설정을 선택합니다. 
5. **소프트웨어 배포 마법사**의 **요약** 탭에 도달하면 **템플릿으로 저장**을 클릭합니다.
6. 템플릿에 이름을 지정하고 템플릿에 저장할 설정을 선택합니다. 
7. **저장**을 클릭합니다. 이제 **배포 템플릿 선택** 옵션에서 템플릿을 사용할 수 있습니다.



## <a name="product-lifecycle-dashboard"></a>제품 수명 주기 대시보드
<!--1319632--> 새 [제품 수명 주기 대시보드](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard)에는 Configuration Manager로 관리되는 디바이스에 설치된 Microsoft 제품에 대한 Microsoft 제품 수명 주기 정책의 상태가 표시됩니다. 대시보드는 사용자 환경의 Microsoft 제품, 지원 가능성 상태 및 지원 종료 날짜에 대한 정보를 제공합니다. 대시보드를 사용하여 각 제품에 대한 지원 가능성을 파악할 수 있습니다. 

수명 주기 대시보드에 액세스하려면 Configuration Manager 콘솔에서 **자산 및 호환성** >**Asset Intelligence** >**제품 수명 주기**로 이동합니다.



## <a name="improvements-to-reporting"></a>보고 개선 사항
<!--1357653--> [고객 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/32434147-new-builtin-reports-about-windows-10-versions-and)의 결과로, **특정 컬렉션에 대한 Windows 10 서비스 세부 정보**라는 새 보고서가 추가되었습니다. 이 보고서에는 Windows 10 디바이스의 리소스 ID, NetBIOS 이름, OS 이름, OS 릴리스 이름, 빌드, OS 분기 및 서비스 상태가 표시됩니다. 보고서에 액세스하려면 **모니터링** >**보고** >**보고서** >**운영 체제** >**특정 컬렉션에 대한 Windows 10 서비스 세부 정보**로 이동합니다.



## <a name="improvements-to-software-center"></a>소프트웨어 센터 개선
<!--1357592--> [고객 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/13002684-software-center-show-only-available-software-hid)의 결과로, 이제 설치된 애플리케이션을 소프트웨어 센터에서 숨길 수 있습니다. 이 옵션을 사용하도록 설정하면 이미 설치된 애플리케이션이 애플리케이션 탭에 더 이상 표시되지 않습니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기
소프트웨어 센터 클라이언트 설정에서 **소프트웨어 센터에서 설치된 애플리케이션 숨기기** 설정을 사용하도록 설정합니다. 최종 사용자가 애플리케이션을 설치할 때 소프트웨어 센터의 동작을 관찰합니다.



## <a name="improvements-to-run-scripts"></a>스크립트 실행의 향상된 기능
<!--1236459--> 이제 [스크립트 실행](/sccm/apps/deploy-use/create-deploy-scripts) 기능이 JSON 형식을 사용하여 스크립트 출력을 반환합니다. 이 형식은 읽기 가능한 스크립트 출력을 일관되게 반환합니다. 실행하지 못한 스크립트는 출력이 반환되지 않을 수도 있습니다. 



## <a name="boundary-group-fallback-for-management-points"></a>관리 지점에 대한 경계 그룹 대체
<!-- 1324594 --> 이 릴리스부터는 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups) 간의 관리 지점에 대해 대체 관계를 구성할 수 있습니다. 이 동작은 클라이언트에서 사용하는 관리 지점에 대한 제어를 강화합니다. 경계 그룹 속성의 **관계** 탭에 관리 지점에 대한 새 열이 있습니다. 새 대체 경계 그룹을 추가하는 경우 현재 관리 지점의 대체 시간은 항상 0입니다. 이 동작은 사이트 기본 경계 그룹의 **기본 동작**에서도 동일합니다.

이전에는, 보안 네트워크에 보호된 관리 지점이 있을 경우 일반적인 문제가 발생합니다. 기본 회사 네트워크의 클라이언트가 방화벽을 통과해서 이 보호된 관리 지점과 통신할 수 없는 경우에도 해당 지점을 포함하는 정책을 수신합니다. 이 문제를 해결하려면 **대체 안 함** 옵션을 사용하여 클라이언트가 통신할 수 있는 관리 지점으로만 대체하도록 합니다.

사이트를 이 버전으로 업그레이드할 때 Configuration Manager는 모든 비인터넷 연결 관리 지점을 사이트 기본 경계 그룹에 추가합니다. 이 업그레이드 동작은 이전 클라이언트 버전이 관리 지점과 계속 통신할 수 있도록 합니다. 이 기능을 최대한 활용하려면 관리 지점을 원하는 경계 그룹으로 이동합니다.

관리 지점 경계 그룹 대체는 클라이언트 설치(ccmsetup) 중에 동작을 변경하지 않습니다. 명령줄에서 /MP 매개 변수를 사용하여 초기 관리 지점을 지정하지 않을 경우 새 클라이언트는 사용 가능한 관리 지점의 전체 목록을 수신합니다. 초기 부트스트랩 프로세스에서는 클라이언트가 액세스할 수 있는 첫 번째 관리 지점을 사용합니다. 클라이언트가 사이트에 등록하면 이 새로운 동작으로 올바르게 정렬된 관리 지점 목록을 수신합니다. 

### <a name="prerequisites"></a>필수 구성 요소
- [기본 설정 관리 지점](/sccm/core/servers/deploy/configure/boundary-groups#preferred-management-points)을 사용하도록 설정합니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트**를 선택합니다. 리본에서 **계층 구조 설정**을 클릭합니다. **일반** 탭에서 **클라이언트가 경계 그룹에 지정된 관리 지점 사용을 선호**를 사용하도록 설정합니다. 

### <a name="known-issues"></a>알려진 문제
- 운영 체제 배포 프로세스에서 경계 그룹을 인식하지 못합니다.

### <a name="troubleshooting"></a>문제 해결
**LocationServices.log**에 새 항목이 표시됩니다. **Locality** 특성은 다음 상태 중 하나를 식별합니다.
- 0: 알 수 없음
- 1: 지정한 관리 지점이 대체를 위한 사이트 기본 경계 그룹에만 있습니다.
- 2: 지정한 관리 지점이 원격 또는 인접 경계 그룹에 있습니다. 관리 지점이 인접 및 사이트 기본 경계 그룹 둘 다에 있는 경우 위치는 2입니다.
- 3: 지정한 관리 지점이 로컬 또는 현재 경계 그룹에 있습니다. 관리 지점이 현재 경계 그룹뿐 아니라 인접 또는 사이트 기본 경계 그룹에도 있는 경우 위치는 3입니다. 계층 구조 설정에서 기본 관리 지점 설정을 사용하도록 설정하지 않을 경우 위치는 관리 지점이 있는 경계 그룹에 관계없이 항상 3입니다.

클라이언트는 로컬 관리 지점(위치 3), 원격(위치 2), 대체(위치 1) 순으로 사용합니다. 

클라이언트가 10분 내에 5개 오류를 수신하고 현재 경계 그룹의 관리 지점과 통신하지 못할 경우 인접 또는 사이트 기본 경계 그룹의 관리 지점에 연결하려고 합니다. 현재 경계 그룹의 관리 지점이 나중에 다시 온라인 상태가 되면 클라이언트는 다음 새로 고침 주기에 로컬 관리 지점으로 돌아갑니다. 새로 고침 주기는 24시간 또는 Configuration Manager 에이전트 서비스가 다시 시작될 때입니다.



## <a name="improved-support-for-cng-certificates"></a>CNG 인증서에 대한 향상된 지원
<!-- 1357314 --> Configuration Manager(현재 분기) 버전 1710은 [CNG(Cryptography: Next Generation) 인증서](/sccm/core/plan-design/network/cng-certificates-overview)를 지원합니다. 버전 1710은 여러 시나리오에서 클라이언트 인증서 지원을 제한합니다. 

이 기술 미리 보기 릴리스부터는 다음과 같은 HTTPS 사용 서버 역할에 대해 CNG 인증서를 사용합니다.
- 관리 지점
- 배포 지점
- 소프트웨어 업데이트 지점

[지원되지 않는 시나리오](/sccm/core/plan-design/network/cng-certificates-overview#unsupported-scenarios) 목록은 동일합니다.



## <a name="cloud-management-gateway-support-for-azure-resource-manager"></a>Azure Resource Manager에 대한 클라우드 관리 게이트웨이 지원
<!-- 1324735 --> CMG([클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)) 인스턴스를 만들 때 이제 마법사에서 **Azure Resource Manager 배포**를 만들 수 있는 옵션을 제공합니다. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)는 모든 솔루션 리소스를 [리소스 그룹](/azure/azure-resource-manager/resource-group-overview#resource-groups)이라는 단일 엔터티로 관리하기 위한 최신 플랫폼입니다. Azure Resource Manager로 CMG를 배포하는 경우 사이트에서 Azure AD(Azure Active Directory)를 사용하여 필요한 클라우드 리소스를 인증하고 만듭니다. 이 최신 배포에서는 클래식 Azure 관리 인증서가 필요하지 않습니다.  

Azure 관리 인증서를 사용하는 **클래식 서비스 배포** 옵션도 CMG 마법사에서 계속 제공됩니다. 리소스의 배포 및 관리를 간소화하려면 모든 새 CMG 인스턴스에 Azure Resource Manager 배포 모델을 사용하는 것이 좋습니다. 가능한 경우 리소스 관리자를 통해 기존 CMG 인스턴스를 재배포합니다.

Configuration Manager는 기존 클래식 CMG 인스턴스를 Azure Resource Manager 배포 모델로 마이그레이션하지 않습니다. Azure Resource Manager 배포를 사용하여 새 CMG 인스턴스를 만든 후 클래식 CMG 인스턴스를 제거합니다. 

> [!IMPORTANT]
> 이 기능은 Azure CSP(클라우드 서비스 공급자) 지원을 사용하도록 설정하지 않습니다. Azure Resource Manager를 통한 CMG 배포는 CSP가 지원하지 않는 클래식 클라우드 서비스를 계속 사용합니다. 자세한 내용은 [Azure CSP에서 사용 가능한 Azure 서비스](/azure/cloud-solution-provider/overview/azure-csp-available-services)를 참조하세요.  

### <a name="prerequisites"></a>필수 구성 요소
- [Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure)와의 통합. Azure AD 사용자 검색은 필요하지 않습니다.
- Azure 관리 인증서를 제외하고 [클라우드 관리 게이트웨이에 대한 요구 사항](/sccm/core/clients/manage/plan-cloud-management-gateway#requirements-for-cloud-management-gateway)과 동일합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장하고 **클라우드 관리 게이트웨이**를 선택합니다. 리본에서 **클라우드 관리 게이트웨이 만들기**를 클릭합니다. 
2. **일반** 페이지에서 **Azure Resource Manager 배포**를 선택합니다. **로그인**을 클릭하여 Azure 구독 관리자 계정으로 인증합니다. 마법사가 통합 필수 조건 중에 저장된 Azure AD 구독 정보의 나머지 필드를 자동으로 채웁니다. 여러 구독을 소유하고 있는 경우 사용할 구독을 선택합니다. **다음**을 클릭합니다.  
3. **설정** 페이지에서 서버 PKI 인증서 파일을 평소대로 제공합니다. 이 인증서는 Azure의 CMG 서비스 이름을 정의합니다. **지역**을 선택한 다음, **새로 만들기** 또는 **기존 항목 사용** 리소스 그룹 옵션을 선택합니다. 새 리소스 그룹 이름을 입력하거나 드롭다운 목록에서 기존 리소스 그룹을 선택합니다. 
4. 마법사를 완료합니다.

> [!NOTE] 
> 선택된 Azure AD 서버 앱에 대해 Azure가 구독 **참가자** 권한을 할당합니다. 

서비스 연결 지점에서 **cloudmgr.log**를 사용하여 서비스 배포 진행 상황을 모니터링합니다.



## <a name="approve-application-requests-for-users-per-device"></a>장치당 사용자에 대한 애플리케이션 요청 승인
<!-- 1357015 --> 이 릴리스부터는 사용자가 승인이 필요한 애플리케이션을 요청할 때 특정 장치 이름이 요청의 일부로 포함됩니다. 관리자가 요청을 승인하면 사용자는 해당 장치에만 애플리케이션을 설치할 수 있습니다. 사용자가 다른 장치에 애플리케이션을 설치하려면 다른 요청을 제출해야 합니다. 

> [!NOTE]
> 이 기능은 선택 사항입니다. 이 릴리스로 업데이트할 때 업데이트 마법사에서 이 기능을 사용하도록 설정합니다. 또는 나중에 콘솔에서 기능을 사용하도록 설정합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
- 구성 관리자 클라이언트를 최신 버전으로 업그레이드
- [컴퓨터 에이전트](/sccm/core/clients/deploy/about-client-settings#computer-agent) 그룹에서 클라이언트 설정인 **새 소프트웨어 센터 사용** 설정

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. 사용자 컬렉션이 사용할 수 있는 애플리케이션으로 배포합니다.
2. **배포 설정** 페이지에서 다음 옵션을 사용하도록 설정: **관리자가 디바이스에서 이 애플리케이션에 대한 요청을 승인해야 함**.
3. 대상 사용자로, 소프트웨어 센터를 사용하여 애플리케이션에 대한 요청을 제출합니다. 
4. Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리** 아래의 **승인 요청**을 확인합니다. 이제 각 요청에 대한 **디바이스** 열이 목록에 있습니다. 요청에 대한 작업을 수행하는 경우 애플리케이션 요청 대화 상자에 사용자가 요청을 제출한 장치 이름도 포함됩니다.



## <a name="use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices"></a>소프트웨어 센터를 사용하여 Azure AD 조인 장치에서 사용자가 사용할 수 있는 애플리케이션 찾아보기 및 설치
<!-- 1322613 --> 사용자가 사용할 수 있는 애플리케이션으로 배포하는 경우 이제 Azure AD(Azure Active Directory) 장치에서 소프트웨어 센터를 통해 해당 애플리케이션을 찾아보고 설치할 수 있습니다.  

### <a name="prerequisites"></a>필수 구성 요소
- 관리 지점에서 HTTPS 사용
- [Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure)와 사이트 통합
- 사용자 컬렉션이 사용할 수 있는 애플리케이션으로 배포
- [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)에 애플리케이션 콘텐츠 배포
- [컴퓨터 에이전트](/sccm/core/clients/deploy/about-client-settings#computer-agent) 그룹에서 클라이언트 설정인 **새 소프트웨어 센터 사용** 설정
- 클라이언트는 다음과 같아야 합니다. 
   - Windows 10
   - Azure AD 조인(클라우드 도메인 조인이라고도 함)
- 인터넷 기반 클라이언트를 지원하려면
    - [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway) 
    - 클라이언트 설정 사용: [클라이언트 정책](/sccm/core/clients/deploy/about-client-settings#client-policy) 그룹에서 **인터넷 클라이언트의 사용자 정책 요청 사용하도록 설정**
- 회사 네트워크에서 클라이언트를 지원하려면
    - 클라이언트에서 사용하는 경계 그룹에 클라우드 배포 지점을 추가합니다.
    - 클라이언트가 HTTPS 사용 관리 지점의 FQDN(정규화된 도메인 이름)을 확인할 수 있어야 합니다.



## <a name="report-on-windows-autopilot-device-information"></a>Windows AutoPilot 디바이스 정보에 대한 보고서
<!-- 1351442 --> Windows AutoPilot은 새로운 Windows 10 디바이스를 최신 방법으로 온보딩 및 구성하기 위한 솔루션입니다. 자세한 내용은 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)를 참조하세요. 기존 디바이스를 Windows AutoPilot에 등록하는 한 가지 방법은 비즈니스 및 교육용 Microsoft 스토어에 디바이스 정보를 업로드하는 것입니다. 이 정보에는 디바이스 일련 번호, Windows 제품 식별자 및 하드웨어 식별자가 포함됩니다. Configuration Manager를 사용하여 이 디바이스 정보를 수집하고 보고할 수 있습니다. 

### <a name="prerequisites"></a>필수 구성 요소
- 이 디바이스 정보는 Windows 10 버전 1703 이상의 클라이언트에만 적용됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. Configuration Manager 콘솔, **모니터링** 작업 영역에서 **보고** 노드, **보고서**를 차례로 확장하고 **하드웨어 - 일반** 노드를 선택합니다.
2. 새 보고서인 **Windows AutoPilot 디바이스 정보**를 실행하고 결과를 확인합니다. 
3. 보고서 뷰어에서 **내보내기** 아이콘을 클릭하고 **CSV(쉼표로 구분)** 옵션을 선택합니다.
4. 파일을 저장한 후 비즈니스 및 교육용 Microsoft 스토어에 데이터를 업로드합니다. 자세한 내용은 [비즈니스 및 교육용 Microsoft 스토어에 디바이스 추가](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile)를 참조하세요. 



## <a name="improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard"></a>Windows Defender Exploit Guard에 대한 Configuration Manager 정책 개선 사항
<!-- 1356220 --> [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)에 대한 Configuration Manager에 공격 노출 영역 축소 및 제어된 폴더 액세스 구성 요소에 대한 추가 정책 설정을 추가합니다.

**제어된 폴더 액세스에 대한 새 설정**<br/>
제어된 폴더 액세스를 구성하는 경우 다음 두 가지 추가 옵션이 있습니다. **디스크 섹터만 차단** 및 **디스크 섹터만 감사**. 이 두 가지 설정을 사용하면 제어된 폴더 액세스를 부트 섹터에만 사용할 수 있으며, 특정 폴더 또는 기본 보호된 폴더의 보호는 사용되지 않습니다. 

**공격 노출 영역 축소에 대한 새 설정**
- 랜섬웨어로부터 고급 보호 기능을 사용합니다.
- Windows LSASS(Local Security Authority Subsystem)에서 자격 증명 도용을 차단합니다. 
- 전파, 처리 기간 또는 신뢰할 수 있는 목록 조건을 충족하지 않는 한 실행 파일 실행을 차단합니다. 
- USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스를 차단합니다.



## <a name="microsoft-edge-browser-policies"></a>Microsoft Edge 브라우저 정책
<!-- 1357310 --> Windows 10 클라이언트에서 [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) 웹 브라우저를 사용하는 고객의 경우 이제 Configuration Manager 규정 준수 설정 정책을 만들어 여러 Microsoft Edge 설정을 구성할 수 있습니다. 이 정책에는 현재 다음 설정이 포함되어 있습니다.
- **Microsoft Edge 브라우저를 기본값으로 설정**: 웹 브라우저에 대한 Windows 10 기본 앱 설정을 Microsoft Edge로 구성합니다.
- **주소 표시줄 드롭다운 허용**: Windows 10 버전 1703 이상이 필요합니다. 자세한 내용은 [AllowAddressBarDropdown 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowaddressbardropdown)을 참조하세요.
- **Microsoft 브라우저 간 즐겨찾기 동기화 허용**: Windows 10 버전 1703 이상이 필요합니다. 자세한 내용은 [SyncFavoritesBetweenIEAndMicrosoftEdge 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-syncfavoritesbetweenieandmicrosoftedge)을 참조하세요.
- **종료 시 검색 데이터 지우기 허용**: Windows 10 버전 1703 이상이 필요합니다. 자세한 내용은 [ClearBrowsingDataOnExit 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-clearbrowsingdataonexit)을 참조하세요.
- **Do Not Track 헤더 허용**: 자세한 내용은 [AllowDoNotTrack 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack)을 참조하세요.
- **자동 채우기 허용**: 자세한 내용은 [AllowAutofill 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowautofill)을 참조하세요.
- **쿠키 허용**: 자세한 내용은 [AllowCookies 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowcookies)을 참조하세요.
- **팝업 차단 허용**: 자세한 내용은 [AllowPopups 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowpopups)을 참조하세요.
- **주소 표시줄에 검색 제안 허용**: 자세한 내용은 [AllowSearchSuggestionsinAddressBar 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar)을 참조하세요.
- **인트라넷 트래픽을 Internet Explorer에 전송 허용**: 자세한 내용은 [SendIntranetTraffictoInternetExplorer 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-sendintranettraffictointernetexplorer)을 참조하세요.
- **암호 관리자 허용**: 자세한 내용은 [AllowPasswordManager 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)을 참조하세요.
- **개발자 도구 허용**: 자세한 내용은 [AllowDeveloperTools 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowdevelopertools)을 참조하세요.
- **확장 허용**: 자세한 내용은 [AllowExtensions 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowextensions)을 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
- Azure Active Directory 조인 Windows 10 클라이언트 

### <a name="known-issues"></a>알려진 문제
- 이 릴리스에서는 온-프레미스 도메인 조인 디바이스가 이 정책을 적용할 수 없습니다. 이 문제는 하이브리드 도메인 조인 디바이스에도 관련이 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

**정책 만들기**
1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다. **준수 설정**을 확장하고 새 **Microsoft Edge 브라우저 프로필** 노드를 선택합니다. **Microsoft Edge 브라우저 정책 만들기** 리본 옵션을 클릭합니다.
2. 정책의 **이름**을 지정하고 선택적으로 **설명**을 입력한 다음, **다음**을 클릭합니다.
3. **설정** 페이지에서 이 정책에 포함할 설정의 값을 **구성됨**으로 변경하고 **다음**을 클릭합니다.
4. **지원되는 플랫폼** 페이지에서 이 정책이 적용되는 운영 체제 버전 및 아키텍처를 선택하고 **다음**을 클릭합니다. 
5. 마법사를 완료합니다.

**정책 배포**
1. 정책을 선택하고 **배포** 리본 옵션을 클릭합니다.
2. **찾아보기**를 클릭하여 정책을 배포할 사용자 또는 디바이스 컬렉션을 선택합니다. 
3. 필요에 따라 추가 옵션을 선택합니다. 정책이 호환되지 않을 경우 경고를 생성합니다. 클라이언트가 이 정책에 대한 디바이스의 준수를 평가하는 일정을 설정합니다.
4. **확인**을 클릭하여 배포를 만듭니다.

준수 설정 정책과 마찬가지로 클라이언트는 지정된 일정에 따라 설정을 수정합니다. Configuration Manager 콘솔에서 [디바이스 준수를 모니터링하고 보고](/sccm/compliance/deploy-use/monitor-compliance-settings)합니다.



## <a name="report-for-default-browser-counts"></a>기본 브라우저 개수에 대한 보고서
<!-- 1357830 --> 이제 특정 웹 브라우저를 Windows 기본값으로 사용하는 클라이언트 수를 표시하는 새 보고서가 있습니다. 

### <a name="known-issues"></a>알려진 문제
- 보고서를 처음 열 때 개수만 표시되고 BrowserProgID는 표시되지 않습니다. 이 문제를 해결하려면 보고서에 대한 쿼리를 다음 구문으로 편집합니다.  
    `select BrowserProgId00 as BrowserProgId, Count(*) as Count`  
    `from DEFAULT_BROWSER_DATA as dbd`  
    `group by BrowserProgId00`

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.
1. **Configuration Manager** 콘솔, **모니터링** 작업 영역에서 **보고**, **보고서**를 차례로 확장하고 **소프트웨어 - 회사 및 제품**을 선택합니다.
2. **기본 브라우저 개수** 보고서를 실행합니다.

일반적인 BrowserProgID는 다음 참조를 사용합니다.
- **AppXq0fevzme2pys62n3e0fbqa7peapykr8v**: Microsoft Edge
- **IE.HTTP**: Microsoft Internet Explorer
- **ChromeHTML**: Google Chrome
- **OperaStable**: Opera 소프트웨어
- **FirefoxURL-308046B0AF4A39CB**: Mozilla Firefox



## <a name="support-for-windows-10-arm64-devices"></a>Windows 10 ARM64 디바이스 지원
<!-- 1353704 --> 이 릴리스부터는 Windows 10 ARM64 디바이스에서 Configuration Manager 클라이언트가 지원됩니다. 기존 클라이언트 관리 기능도 이러한 새 디바이스에서 작동합니다. 예를 들어 하드웨어 및 소프트웨어 인벤토리, 소프트웨어 업데이트, 애플리케이션 관리 등입니다. 운영 체제 배포는 현재 지원되지 않습니다. 

## <a name="changes-to-phased-deployments"></a>단계별 배포 변경 사항
<!-- 1357405 --> 단계별 배포는 여러 컬렉션에 대한 소프트웨어 출시를 자동으로 조정하고 순차적으로 진행합니다. 이 기술 미리 보기 버전에서는 관리 콘솔의 작업 순서에 대해 단계별 배포 마법사를 완료할 수 있으며 배포가 생성됩니다. 그러나 첫 번째 단계의 성공 조건을 충족한 후 두 번째 단계가 자동으로 시작되지는 않습니다. SQL 문을 사용하여 수동으로 두 번째 단계를 시작할 수 있습니다.   

### <a name="try-it-out"></a>기능 직접 사용해 보기  
  작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.
 
**작업 순서에 대한 단계별 배포 만들기** </br>
1. **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.
2. 기존 작업 순서를 마우스 오른쪽 버튼으로 클릭하고 **단계별 배포 만들기**를 선택합니다. 
3. **일반** 탭에서 단계별 배포에 이름을 지정하고 설명(선택 사항)을 입력한 다음, **자동으로 기본 두 단계 배포 만들기**를 선택합니다. 
4. **첫 번째 컬렉션** 및 **두 번째 컬렉션** 필드를 채웁니다. **다음**을 선택합니다.
5. **설정** 탭에서 각 일정 설정에 대해 하나의 옵션을 선택하고 완료되면 **다음**을 선택합니다. 
6. **단계**  탭에서 필요하면 단계를 편집하고 **다음**을 클릭합니다.
7. **요약** 탭에서 선택을 확인한 후 **다음**을 클릭하여 진행합니다.
8. 첫 번째 단계의 성공 조건에 도달한 경우 지침에 따라 SQL 문을 사용하여 두 번째 단계를 시작합니다.
 
**SQL 문을 사용하여 두 번째 단계 시작**
1. 다음 SQL 쿼리를 사용하여 직접 만든 배포의 PhasedDeploymentID를 확인합니다.<br/> `Select * from PhasedDeployment`
2. 다음 문을 실행하여 프로덕션 단계를 시작합니다.<br/> `UPDATE PhasedDeployment SET EvaluatePhasedDeployment = 1, Action = 3 WHERE PhasedDeploymentID = <Phased Deployment ID>`


## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
