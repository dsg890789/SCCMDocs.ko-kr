---
title: Technical Preview 1806.2
titleSuffix: Configuration Manager
description: Configuration Manager Technical Preview 버전 1806.2에서 사용할 수 있는 새로운 기능에 대해 알아봅니다.
ms.date: 06/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3af2a69d-30e7-4dce-832d-82b7a1c082f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 13742fcbeefacd2183b26c5083d6f8b3ee0ef60f
ms.sourcegitcommit: d1bf26bcf0d78b37ac7598fab36eb58ca69b1dc5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37067622"
---
# <a name="capabilities-in-technical-preview-18062-for-system-center-configuration-manager"></a>System Center Configuration Manager Technical Preview 1806.2의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 Configuration Manager Technical Preview 버전 1806.2에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 기술 미리 보기 사이트를 업데이트하고 새 기능을 추가할 수 있습니다. 

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

### <a name="ki_sqlncli"></a> 클라이언트가 자동으로 업데이트되지 않음
<!--518760--> 버전 1806.2로 업데이트하면 사이트에서 SQL Native Client도 업데이트하므로 사이트 서버에서 다시 시작이 보류될 수 있습니다. 이러한 지연으로 인해 특정 파일이 업데이트되지 않으며 자동 클라이언트 업그레이드에 영향을 줍니다.

#### <a name="workarounds"></a>해결 방법
Configuration Manager를 버전 1806.2로 ‘업데이트하기 전에’ SQL Native Client를 수동으로 업그레이드하여 이 문제를 방지하세요. 자세한 내용은 [SQL Server 2012 Native Client의 최신 서비스 업데이트](https://www.microsoft.com/download/details.aspx?id=50402)를 참조하세요.

사이트를 이미 업데이트한 경우, 자동 클라이언트 업그레이드 및 클라이언트 강제가 작동하지 않습니다. 대부분의 새로운 기능을 완전히 테스트하려면 클라이언트를 업데이트해야 합니다. 다음 프로세스를 사용하여 기술 미리 보기 클라이언트를 수동으로 업데이트하세요.  

1. 사이트 서버에 있는 Configuration Manager 설치 디렉터리의 **CMUClient** 폴더에서 클라이언트 원본 파일을 찾습니다. 예를 들면 `C:\Program Files\Configuration Manager\CMUClient`  

2. 전체 CMUClient 폴더를 클라이언트 장치에 복사합니다. 예를 들면 `C:\Temp\CMUClient`  

    이 위치는 클라이언트에서 액세스할 수 있는 네트워크 공유일 수 있습니다.  

3. 관리자 권한 명령 프롬프트에서 다음 명령줄을 실행합니다. `C:\Temp\CMUClient\ccmsetup.exe /source:C:\Temp\CMUClient`  

기술 미리 보기 버전 1806.2 사이트에 새 클라이언트를 설치하는 경우, 동일한 이 프로세스를 사용하세요. 

> [!Important]  
> 이 시나리오에서는 `/MP` 명령줄 매개 변수를 사용하지 마세요. 이 매개 변수는 `/source`보다 우선 적용되며 ccmsetup이 관리 지점 또는 배포 지점에서 클라이언트 콘텐츠를 다운로드하도록 합니다.
> 
> 명령줄 속성(예: SMSSITECODE 또는 CCMLOGLEVEL)을 사용해도 문제가 없지만 기존 클라이언트를 업그레이드할 때는 필요하지 않습니다. 


### <a name="ki_version"> </a> 버전 1806.2의 Configuration Manager 정보에 버전 1806이 표시됨
<!--518148--> 기술 미리 보기 버전 1806.2로 업그레이드한 후 콘솔의 왼쪽 위 모서리에서 **Configuration Manager 정보** 창을 열면 **버전 1806**이 계속 표시됩니다. 

#### <a name="workaround"></a>해결 방법
**사이트 버전** 속성을 사용하여 1806과1806.2의 차이를 확인하세요.

| 사이트 버전  | Version
|---------|---------|
| 5.0.**8672**.1000 | 1806 |
| 5.0.**8685**.1000 | 1806.2 |
 


</br>

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  


## <a name="bkmk_pod"></a> 단계적 배포 개선 사항

이 릴리스에서는 [단계적 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)의 다음 사항이 개선되었습니다.
- [단계적 배포 상태](#bkmk_pod-monitor)
- [응용 프로그램의 단계적 배포](#bkmk_pod-app)
- [단계적 배포 중 점진적 출시](#bkmk_pod-throttle)


### <a name="bkmk_pod-monitor"></a> 단계적 배포 상태
<!--1358577--> 이제 단계적 배포에서 기본 모니터링 환경을 제공합니다. **모니터링** 작업 영역의 **배포** 노드에서 단계적 배포를 선택한 다음, 리본에서 **단계적 배포 상태**를 클릭합니다.

![두 단계의 상태를 보여 주는 단계적 배포 상태 대시보드](media/1358577-phased-deployment-status.png)

이 대시보드에는 배포의 각 단계에 대해 다음과 같은 정보가 표시됩니다.  

- **총 장치 수**: 이 단계의 대상으로 지정된 장치의 수입니다.  

- **상태**: 이 단계의 현재 상태입니다. 각 단계는 다음 상태 중 하나일 수 있습니다.  

    - **Deployment created**(배포가 생성됨): 단계적 배포에서 이 단계의 컬렉션에 대한 소프트웨어 배포를 만들었습니다. 클라이언트가 이 소프트웨어에서 적극적으로 대상으로 지정됩니다.  

    - **대기 중**: 이전 단계가 배포의 성공 조건에 도달하지 못해 이 단계를 계속 진행합니다.  

    - **일시 중단됨**: 관리자가 배포를 일시 중단했습니다.  

- **진행률**: 클라이언트에서 색으로 구분된 배포 상태입니다. 예를 들어 성공, 진행 중, 오류, 요구 사항에 맞지 않음, 알 수 없음 등이 있습니다. 


#### <a name="known-issue"></a>알려진 문제
단계적 배포 상태 대시보드에서 동일한 단계에 대해 여러 행을 표시할 수 있습니다.<!--518510-->


### <a name="bkmk_pod-app"></a> 응용 프로그램의 단계적 배포
<!--1358147--> 응용 프로그램에 대한 단계적 배포를 만듭니다. 단계적 배포에서는 사용자 지정 가능한 조건 및 그룹에 따라 소프트웨어 출시를 조정하고 순차적으로 진행할 수 있습니다.

Configuration Manager 콘솔에서 **소프트웨어 라이브러리**로 이동하여 **응용 프로그램 관리**를 확장하고 **응용 프로그램**을 선택합니다. 응용 프로그램을 선택한 다음, 리본에서 **단계적 배포 만들기**를 클릭합니다. 

응용 프로그램 단계적 배포의 동작은 작업 순서와 동일합니다. 자세한 내용은 [작업 순서에 대한 단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)를 참조하세요.

#### <a name="prerequisite"></a>필수 구성 요소
단계적 배포를 만들기 전에 응용 프로그램의 콘텐츠를 배포 지점에 배포하세요.<!--518293-->

#### <a name="known-issue"></a>알려진 문제
응용 프로그램에 대한 단계를 수동으로 만들 수 없습니다. 마법사에서 응용 프로그램 배포에 대한 두 단계를 자동으로 만듭니다.


### <a name="bkmk_pod-throttle"></a> 단계적 배포 중 점진적 출시
<!--1358578--> 단계적 배포 중에 각 단계의 출시가 이제 점진적으로 수행됩니다. 이 동작은 배포 문제의 위험을 완화하고 콘텐츠의 클라이언트 배포로 인한 네트워크의 부하를 줄이는 데 도움이 됩니다. 사이트에서는 각 단계에 대한 구성에 따라 점진적으로 소프트웨어를 사용할 수 있도록 합니다. 단계의 모든 클라이언트는 소프트웨어를 사용할 수 있게 되는 시간을 기준으로 최종 기한을 갖게 됩니다. 사용 가능 시간과 최종 기한 사이의 기간은 단계의 모든 클라이언트에 대해 동일합니다. 

단계적 배포를 만들고 단계를 수동으로 구성하면 단계 추가 마법사의 **단계 설정** 페이지 또는 단계적 배포 만들기 마법사의 **설정** 페이지에서 **이 기간(일)에 걸쳐 점진적으로 이 소프트웨어를 사용할 수 있도록 함** 옵션을 구성합니다. 이 설정의 기본값은 **0**이므로 기본적으로 배포가 제한되지 않습니다.

> [!Note]  
> 이 옵션은 현재 작업 순서의 단계적 배포에만 사용할 수 있습니다.  



## <a name="bkmk_msix"></a> 새로운 Windows 앱 패키지 형식에 대한 지원
<!--1357427--> Configuration Manager는 이제 새 Windows 10 앱 패키지(.msix) 및 앱 번들(.msixbundle) 형식의 배포를 지원합니다. 최신 [Windows Insider Preview](https://insider.windows.com/) 빌드는 현재 이러한 새 형식을 지원합니다.

MSIX에 대한 개요는 [A closer look at MSIX](https://blogs.msdn.microsoft.com/sgern/2018/06/18/a-closer-look-at-msix/)(MSIX 자세히 살펴보기)를 참조하세요.

새 MSIX 앱을 만드는 방법은 [MSIX support introduced in Insider Build 17682](https://techcommunity.microsoft.com/t5/MSIX-Blog/MSIX-support-introduced-in-Insider-Build-17682/ba-p/202376)(Insider 빌드 17682에서 도입된 MSIX 지원)를 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
- Windows Insider Preview 빌드 17682 이상을 실행하는 Windows 10 클라이언트
- MSIX 형식의 Windows 앱 패키지

### <a name="try-it-out"></a>기능 직접 사용해 보기
작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 [응용 프로그램을 만듭니다](/sccm/apps/deploy-use/create-applications). 
2. 응용 프로그램 설치 파일 **형식**을 **Windows 앱 패키지(*.appx, *.appxbundle, *.msix, *.msixbundle)**로 선택합니다.
3. 최신 Windows Insider Preview 빌드를 실행하는 클라이언트에 [응용 프로그램을 배포](/sccm/apps/deploy-use/deploy-applications)합니다.



## <a name="bkmk_client-push"> </a> 클라이언트 강제 보안 개선 사항
<!--1358204--> Configuration Manager 클라이언트 설치의 [클라이언트 강제](/sccm/core/clients/deploy/plan/client-installation-methods#client-push-installation) 방법을 사용하면 사이트 서버에서 클라이언트에 대한 원격 연결을 만들어 설치를 시작합니다. 이 릴리스부터 사이트에서 연결을 설정하기 전에 NTLM으로 대체를 허용하지 않아 Kerberos 상호 인증을 요구할 수 있습니다. 이 개선 사항은 서버와 클라이언트 간의 통신을 보안하는 데 도움이 됩니다. 

보안 정책에 따라 사용자 환경에서 이미 이전 NTLM 인증에 비해 Kerberos를 선호하거나 요구할 수 있습니다. 이러한 인증 프로토콜의 보안 고려 사항에 대한 자세한 내용은 [Windows security policy setting to restrict NTLM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-security-restrict-ntlm-outgoing-ntlm-traffic-to-remote-servers#security-considerations)(NTLM을 제한하는 Windows 보안 정책 설정)을 참조하세요.


### <a name="prerequisite"></a>필수 구성 요소

이 기능을 사용하려면 클라이언트가 신뢰할 수 있는 Active Directory 포리스트에 있어야 합니다. Windows의 Kerberos는 상호 인증을 위해 Active Directory를 사용합니다. 


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

사이트를 업그레이드해도 기존 동작은 지속됩니다. 클라이언트 강제 설치 속성을 ‘열면’ 사이트에서 Kerberos 확인을 사용하도록 자동으로 설정합니다. 필요한 경우, 보안 수준이 낮은 NTLM 연결 사용으로 연결 대체를 허용할 수 있지만 권장되지는 않습니다. 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트**를 선택합니다. 대상 사이트를 선택합니다. 리본에서 **클라이언트 설치 설정**을 클릭하고 **클라이언트 강제 설치**를 선택합니다.  

2. 사이트에서 이제 클라이언트 강제에 대해 Kerberos 확인을 사용하도록 설정했습니다. **확인**을 클릭하여 창을 닫습니다.  

3. 사용자 환경에 필요한 경우, 클라이언트 강제 설치 속성 창의 **일반** 탭에서 **Allow connection fallback to NTLM**(NTLM으로 연결 대체 허용) 옵션을 확인합니다. 이 옵션은 기본적으로 사용되지 않습니다. 



## <a name="bkmk_insights"></a> 자동 유지 관리에 대한 관리 인사이트
<!--1352184,et al--> 이 릴리스에서는 추가 관리 인사이트를 사용하여 잠재적인 구성 문제를 강조 표시할 수 있습니다. 새 **자동 유지 관리** 그룹에서 다음 규칙을 검토하세요.  

- **사용되지 않는 구성 항목**: 구성 기준에 속하지 않고 30일보다 오래된 구성 항목입니다.  

- **사용되지 않는 부팅 이미지**: PXE 부팅 또는 작업 순서 사용에서 참조되지 않는 부팅 이미지입니다.  

- **할당된 사이트 시스템이 없는 경계 그룹**: 할당된 사이트 시스템이 없으면 경계 그룹은 사이트 할당에만 사용할 수 있습니다.  

- **Boundary groups with no members**(멤버가 없는 경계 그룹): 경계 그룹은 멤버가 없는 경우 사이트 할당이나 콘텐츠 조회에 적용할 수 없습니다.  

- **클라이언트에 콘텐츠를 제공하지 않는 배포 지점**: 지난 30일 동안 클라이언트에 콘텐츠를 제공하지 않은 배포 지점입니다. 이 데이터는 클라이언트의 다운로드 기록 보고서를 기반으로 합니다.  

- **Expired updates found**(만료된 업데이트 찾음): 만료된 업데이트는 배포에 적용되지 않습니다.   



## <a name="bkmk_comgmt"> </a> 공동 관리하는 장치에 대한 모바일 앱 워크로드 전환
<!--1357892--> 계속 Configuration Manager를 사용하여 Windows 데스크톱 응용 프로그램을 배포하면서 Microsoft Intune으로 모바일 앱을 관리합니다. 최신 앱 워크로드를 전환하려면 공동 관리 속성 페이지로 이동하세요. Configuration Manager에서 슬라이더 막대를 [파일럿] 또는 [모두]로 이동합니다. 

이 워크로드를 전환하면 Intune에서 배포된 사용 가능한 모든 앱을 회사 포털에서 사용할 수 있습니다. Configuration Manager에서 배포하는 앱은 소프트웨어 센터에서 사용할 수 있습니다. 

자세한 내용은 다음 아티클을 참조하세요.  

- [Windows 10 장치에 대한 공동 관리](/sccm/core/clients/manage/co-management-overview)  

- [Microsoft Intune 앱 관리란?](https://docs.microsoft.com/intune/app-management)  



## <a name="bkmk_bgoptions"> </a> 피어 다운로드를 위한 경계 그룹 옵션
<!--1356193--> 이제 경계 그룹에는 사용자 환경에서 콘텐츠 배포를 보다 세밀하게 제어할 수 있는 추가 설정이 포함됩니다. 이 릴리스에서는 다음 옵션을 추가합니다.  

- **Allow peer downloads in this boundary group**(이 경계 그룹에서 피어 다운로드 허용): 이 설정은 기본적으로 사용하도록 설정되어 있습니다. 관리 지점은 피어 원본을 포함하는 콘텐츠 위치 목록을 클라이언트에 제공합니다. <!--This setting also affects applying Group IDs for Delivery Optimization.518268-->  

    이 옵션을 사용하지 않도록 설정해야 하는 두 가지 일반적인 시나리오가 있습니다.  

    - VPN과 같이 지리적으로 분산된 위치의 경계를 포함하는 경계 그룹이 있는 경우. 두 클라이언트가 VPN을 통해 연결되어 동일한 경계 그룹에 있거나 콘텐츠의 피어 공유에 적합하지 않은 완전히 다른 위치에 있을 수 있습니다.  

    - 배포 지점을 참조하지 않는 사이트 할당에 하나의 큰 경계 그룹을 사용하는 경우.  

- **During peer downloads, only use peers within the same subnet**(피어 다운로드 중 동일한 서브넷 내의 피어만 사용): 이 설정은 위의 설정에 따라 달라집니다. 이 옵션을 사용하도록 설정하면 관리 지점은 클라이언트와 동일한 서브넷에 있는 콘텐츠 위치 목록 피어 원본에만 포함됩니다.

    이 옵션을 사용하도록 설정하는 일반적인 시나리오:

    - 콘텐츠 배포를 위한 경계 그룹 설계에 더 작은 다른 경계 그룹과 겹치는 하나의 큰 경계 그룹이 포함됩니다. 이 새 설정을 사용하면 관리 지점이 클라이언트에 제공하는 콘텐츠 원본 목록에 동일한 서브넷의 피어 원본만 포함됩니다.

    - 모든 원격 사무실 위치에 대해 하나의 큰 경계 그룹이 있습니다. 이 옵션을 사용하도록 설정하면 클라이언트는 위치 간에 콘텐츠를 공유하는 대신 원격 사무실 위치에서 서브넷 내의 콘텐츠만 공유합니다.


### <a name="known-issue"></a>알려진 문제
피어 원본 클라이언트에 둘 이상의 IP 주소(IPv4, IPv6 또는 둘 다)가 있는 경우 피어 캐싱이 작동하지 않습니다. **During peer downloads, only use peers within the same subnet**(피어 다운로드 중 동일한 서브넷 내의 피어만 사용) 새 옵션은 피어 원본에 둘 이상의 IP 주소가 있는 경우, 적용되지 않습니다.<!--518661-->   



## <a name="bkmk_3pupdate"> </a> 사용자 지정 카탈로그에 대한 타사 소프트웨어 업데이트 지원
<!--1358714--> 이 릴리스에서는 [UserVoice 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8803711-3rd-party-patching-scup-integration-with-sccm-co)의 결과로서 타사 소프트웨어 업데이트에 대한 지원을 계속 반복합니다. [기술 미리 보기 버전 1806](/sccm/core/get-started/capabilities-in-technical-preview-1806#bkmk-3pupdate)에서는 소프트웨어 공급업체의 등록된 카탈로그인 *파트너 카탈로그*를 지원했습니다. 사용자가 제공하고 Microsoft에 등록되지 않은 카탈로그를 *사용자 지정 카탈로그*라고 합니다. Configuration Manager 콘솔에서 사용자 지정 카탈로그를 추가하세요.  


### <a name="prerequisites"></a>필수 구성 요소 

- [타사 소프트웨어 업데이트](/sccm/core/get-started/capabilities-in-technical-preview-1806#bkmk-3pupdate)를 설정합니다. 1단계: 기능 설정 및 사용을 완료합니다.   

- 디지털 서명된 소프트웨어 업데이트를 포함하는 디지털 서명된 사용자 지정 카탈로그.  

- 관리자는 다음 권한이 필요합니다.  

    - 사이트: 만들기, 수정  


### <a name="try-it-out"></a>기능 직접 사용해 보기

작업을 완료합니다. 그런 다음, [피드백](capabilities-in-technical-preview-1804.md#bkmk_feedback)을 전송하여 작업이 어떻게 진행되었는지 알려주세요.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **소프트웨어 업데이트**를 확장하고 **타사 소프트웨어 업데이트 카탈로그** 노드를 선택합니다. 리본에서 **사용자 지정 카탈로그 추가**를 클릭합니다.  

2. **일반** 페이지에서 다음 세부 정보를 지정합니다.  

    - **다운로드 URL**: 사용자 지정 카탈로그의 유효한 HTTPS 주소입니다.  

    - **게시자**: 카탈로그를 게시하는 조직의 이름입니다.  

    - **이름**: Configuration Manager 콘솔에 표시할 카탈로그의 이름입니다.  

    - **설명**: 카탈로그에 대한 설명입니다.  

    - **지원 URL**(선택 사항): 카탈로그에 대한 도움말을 볼 수 있는 웹 사이트의 유효한 HTTPS 주소입니다.  

    - **지원 담당자**(선택 사항): 카탈로그에 대한 도움을 받을 수 있는 담당자 정보입니다.  

3. 마법사를 완료합니다. 마법사가 구독 취소됨 상태의 새 카탈로그를 추가합니다.  

4. 기존 **카탈로그 구독** 동작을 사용하여 사용자 지정 카탈로그를 구독합니다. 자세한 내용은 [2단계: 타사 카탈로그 구독 및 업데이트 동기화](/sccm/core/get-started/capabilities-in-technical-preview-1806#phase-2-subscribe-to-a-third-party-catalog-and-sync-updates)를 참조하세요.  

> [!Note]  
> 다운로드 URL이 동일한 카탈로그는 추가할 수 없으며 카탈로그 속성을 편집할 수 없습니다. 사용자 지정 카탈로그에 잘못된 속성을 지정한 경우, 다시 추가하기 전에 카탈로그를 삭제하세요.  


#### <a name="unsubscribe-from-a-catalog"></a>카탈로그 구독 취소
카탈로그에서 구독 취소하려면 목록에서 원하는 카탈로그를 선택하고 리본에서 **카탈로그 구독 취소**를 클릭합니다. 카탈로그에서 구독 취소하는 경우 다음 작업 및 동작이 발생합니다. 
- 사이트에서 새 업데이트의 동기화를 중지합니다. 
- 사이트에서 카탈로그 서명 및 업데이트 콘텐츠와 연관된 인증서를 차단합니다. 
- 기존 업데이트는 제거되지 않지만 게시하거나 배포할 수 없습니다.

#### <a name="delete-a-custom-catalog"></a>사용자 지정 카탈로그 삭제
콘솔의 동일한 노드에서 사용자 지정 카탈로그를 삭제합니다. *구독 취소됨* 상태의 사용자 지정 카탈로그를 선택하고 **사용자 지정 카탈로그 삭제**를 클릭합니다. 카탈로그를 이미 구독한 경우, 삭제하기 전에 먼저 구독을 취소하세요. 파트너 카탈로그는 삭제할 수 없습니다. 사용자 지정 카탈로그를 삭제하면 카탈로그 목록에서 제거됩니다. 이 동작은 소프트웨어 업데이트 지점에 게시한 소프트웨어 업데이트에 영향을 주지 않습니다.


### <a name="known-issue"></a>알려진 문제
사용자 지정 카탈로그의 삭제 동작이 회색으로 표시되어 콘솔에서 사용자 지정 카탈로그를 삭제할 수 없습니다. 이 문제를 해결하려면 사이트 서버에서 **wbemtest** 도구를 사용합니다. 이름 또는 다운로드 URL로 삭제하려는 인스턴스에 대한 쿼리(예: `select * from SMS_ISVCatalog where DownloadURL="http://www.contoso.com/catalog.cab"`)입니다. 쿼리 결과 창에서 개체를 선택하고 **삭제**를 클릭합니다.<!--518676-->  



## <a name="bkmk_cloud"></a> 클라우드 관리 기능 개선 사항

이 릴리스에서는 다음 사항이 개선되었습니다.  

- 이제 다음과 같은 기능에서 Azure 미국 정부 클라우드의 사용을 지원합니다.<!--511980-->  

    - [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)를 통해 **클라우드 관리**에 대한 사이트 등록  

    - [Azure Resource Manager를 사용하여 클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager) 배포  

    - [Azure Resource Manager를 사용하여 클라우드 배포 지점](/sccm/core/get-started/capabilities-in-technical-preview-1805#cloud-distribution-point-support-for-azure-resource-manager) 배포  

- 고객이 Windows AutoPilot을 사용하여 온-프레미스 네트워크에 연결된 Azure Active Directory 가입 장치에서 Windows 10을 프로비전하고 있습니다. 이러한 장치에 Configuration Manager 클라이언트를 설치하거나 업그레이드하기 위해 **클라이언트의 익명 연결을 허용**하도록 구성된 클라우드 배포 지점이나 온-프레미스 배포 지점이 필요하지 않습니다. 대신 **Use Configuration Manager-generated certificates for HTTP site systems**(HTTP 사이트 시스템에 Configuration Manager 생성 인증서 사용) 사이트 옵션을 설정하여 클라우드 도메인 가입 클라이언트가 온-프레미스 HTTP 사용 배포 지점과 통신하도록 허용합니다. 자세한 내용은 [개선된 보안 클라이언트 통신](https://docs.microsoft.com/en-us/sccm/core/get-started/capabilities-in-technical-preview-1805#improved-secure-client-communications)을 참조하세요.<!--515854-->  



## <a name="bkmk_report"> </a> 새 소프트웨어 업데이트 준수 보고서
<!--1357775--> 소프트웨어 업데이트 준수에 대한 보고서 보기에는 일반적으로 최근 사이트에 연결하지 않은 클라이언트의 데이터가 포함됩니다. 새 보고서에서는 특정 소프트웨어 업데이트 그룹에 대한 준수 결과를 “정상” 클라이언트별로 필터링할 수 있습니다. 이 보고서에서는 사용자 환경에서 활성 클라이언트의 보다 사실적인 준수 상태를 보여 줍니다. 
 
보고서를 보려면 **모니터링** 작업 영역으로 이동하여 **보고**, **보고서**, **소프트웨어 업데이트 – A 호환성**을 차례로 확장한 다음, **준수 9 - 전체 상태 및 준수**를 선택합니다. **업데이트 그룹**, **컬렉션 이름** 및 **클라이언트 상태**를 지정합니다.

보고서에는 다음과 같은 부분이 포함됩니다.
- **정상인 클라이언트 수 및 총 클라이언트 수**: 이 막대형 차트는 지정된 컬렉션의 총 클라이언트 수에 대해 지정된 기간에 사이트와 통신한 “정상” 상태의 클라이언트를 비교합니다.
- **준수 개요**: 이 원형 차트는 지정된 컬렉션의 활성 클라이언트에 있는 특정 소프트웨어 업데이트 그룹의 전체 준수 상태를 보여 줍니다.
- **상위 5개의 문서 ID별 비준수**: 이 막대형 차트는 지정된 컬렉션의 활성 클라이언트에서 비준수 상태인 지정된 그룹의 소프트웨어 업데이트 상위 5개를 표시합니다.
- 보고서의 맨 아래에는 추가 정보가 포함된 표가 있으며 지정된 그룹의 소프트웨어 업데이트를 나열합니다.



## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
