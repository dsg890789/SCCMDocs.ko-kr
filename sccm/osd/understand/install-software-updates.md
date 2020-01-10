---
title: 소프트웨어 업데이트 설치
titleSuffix: Configuration Manager
description: Configuration Manager에서 소프트웨어 업데이트 설치 작업 순서 단계를 사용하는 것과 관련된 권장 사항입니다.
ms.date: 05/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 72d1ccd5-3763-4f88-9273-e1a73e8f4286
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2581214b42216a9f099ceee8e8c06201612902ae
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821140"
---
# <a name="install-software-updates"></a>소프트웨어 업데이트 설치

*적용 대상: Configuration Manager(현재 분기)*

**소프트웨어 업데이트 설치** 단계는 Configuration Manager 작업 순서에서 일반적으로 사용됩니다. OS를 설치하거나 업데이트할 때 이 단계가 소프트웨어 업데이트 구성 요소를 트리거하여 업데이트를 검사하고 배포합니다. 일부 고객의 경우 이 단계에서 긴 시간 제한 지연이나 업데이트 누락 같은 문제가 발생할 수 있습니다. 이 문서의 정보는 이 단계와 관련된 일반적인 문제를 완화하고 문제가 발생한 경우 더 효율적으로 문제를 해결하는 데 도움이 됩니다.

이 단계에 대한 자세한 내용은 [소프트웨어 업데이트 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallSoftwareUpdates)를 참조하세요.



## <a name="recommendations"></a>권장 사항

이 프로세스를 성공적으로 수행하는 데 도움이 되는 권장 사항은 다음과 같습니다.

- [오프라인 설치 사용](#use-offline-servicing)
- [단일 인덱스](#single-index)
- [이미지 크기 줄이기](#bkmk_resetbase)

### <a name="use-offline-servicing"></a>오프라인 설치 사용

Configuration Manager를 사용하여 정기적으로 이미지 파일에 적용 가능한 소프트웨어 업데이트를 설치하세요. 이렇게 하면 작업 순서 진행 중 설치해야 하는 업데이트의 수가 줄어듭니다.

자세한 내용은 [이미지에 소프트웨어 업데이트 적용](/sccm/osd/get-started/manage-operating-system-images#BKMK_OSImagesApplyUpdates)을 참조하세요.

### <a name="single-index"></a>단일 인덱스

여러 이미지 파일에는 다양한 버전의 Windows와 같은 여러 인덱스가 포함되어 있습니다. 필요한 이미지 파일을 단일 인덱스로 줄이세요. 이렇게 하면 소프트웨어 업데이트를 이미지에 적용하는 데 걸리는 시간이 줄어듭니다. 단일 인덱스를 사용해야 이미지 크기를 줄이기 위한 다음 권장 사항도 따를 수 있습니다.

버전 1902부터 OS 이미지를 사이트에 추가할 때 이 프로세스를 자동화합니다. 자세한 내용은 [OS 이미지 추가](/sccm/osd/get-started/manage-operating-system-images#BKMK_AddOSImages)를 참조하세요.<!--3719699-->

### <a name="bkmk_resetbase"></a> 이미지 크기 줄이기

이미지에 소프트웨어 업데이트를 적용하는 경우 모든 대체된 업데이트를 제거하여 출력을 최적화할 수 있습니다. 다음과 같이 DISM 명령줄 도구를 사용하세요.

``` Command
dism /Mount-Image /ImageFile:C:\Data\install.wim /MountDir:C:\Mountdir
dism /Image:C:\Mountdir /Cleanup-Image /StartComponentCleanup /ResetBase
dism /Unmount-Image /MountDir:C:\Mountdir /Commit  
```

버전 1902부터 이 프로세스를 자동화하는 새로운 옵션이 있습니다. 자세한 내용은 [최적화된 서비스 이미지](/sccm/osd/get-started/manage-operating-system-images#bkmk_resetbase)를 참조하세요.<!--3555951-->


## <a name="image-engineering-decisions"></a>이미지 엔지니어링 의사 결정

이미징 프로세스를 설계하는 경우 다음과 같이 소프트웨어 업데이트 설치에 영향을 줄 수 있는 몇 가지 옵션이 있습니다.

- [주기적으로 이미지 다시 캡처](#bkmk_goldimage)  
- [오프라인 설치 사용](#bkmk_offline)  
- [기본 이미지만 사용](#bkmk_installwim)

### <a name="bkmk_goldimage"></a> 주기적으로 이미지 다시 캡처

정기적인 일정에 따라 사용자 지정 OS 이미지를 캡처하는 자동화된 프로세스가 있습니다. 이 캡처 작업 순서에서는 최신 소프트웨어 업데이트를 설치합니다. 해당 업데이트로는 누적 업데이트, 비누적 업데이트, SSU(서비스 스택 업데이트) 같은 기타 중요 업데이트가 있습니다. 배포 작업 순서에서는 캡처 이후 추가 업데이트를 설치합니다.

이 프로세스에 대한 자세한 내용은 [OS를 캡처하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system)를 참조하세요.

#### <a name="advantages"></a>장점

- 배포 시 클라이언트당 적용할 업데이트 수가 적어지므로 배포하는 동안 시간 및 대역폭이 절약됩니다.
- 다시 시작이 발생할 염려가 있는 업데이트 수가 적어집니다.
- 이미지가 조직에 맞게 사용자 지정됩니다.
- 배포 시 변수 개수가 적어집니다.

#### <a name="disadvantages"></a>단점

- 대부분 자동화되어 있긴 하지만 이미지를 만들고 캡처하는 시간이 걸립니다.
- 배포 지점에 이미지를 배포하는 데 걸리는 시간이 늘어나 활성 배포에 대한 중단으로 간주될 수 있습니다.
- 사전 프로덕션 환경을 통해 테스트하는 시간이 OS 패치 주기보다 길어져 업데이트된 이미지가 관련이 없어질 수 있습니다.


### <a name="bkmk_offline"></a> 오프라인 설치 사용

Configuration Manager가 이미지에 소프트웨어 업데이트를 적용하도록 예약합니다.

자세한 내용은 [이미지에 소프트웨어 업데이트 적용](/sccm/osd/get-started/manage-operating-system-images#BKMK_OSImagesApplyUpdates)을 참조하세요.

#### <a name="advantages"></a>장점

- 배포 시 클라이언트당 적용할 업데이트 수가 적어지므로 배포하는 동안 시간 및 대역폭이 절약됩니다.
- 다시 시작이 발생할 염려가 있는 업데이트 수가 적어집니다.
- 사이트에서 설치 프로세스를 예약할 수 있습니다.

#### <a name="disadvantages"></a>단점

- 업데이트를 수동으로 선택해야 합니다.
- 배포 지점에 이미지를 배포하는 데 걸리는 시간이 늘어납니다.
- CBS 기반 업데이트만 지원합니다. Office 업데이트는 적용할 수 없습니다.

> [!Tip]  
> PowerShell을 사용하여 소프트웨어 업데이트 선택을 자동화할 수 있습니다. [Get-CMSoftwareUpdate](https://docs.microsoft.com/powershell/module/configurationmanager/get-cmsoftwareupdate?view=sccm-ps) cmdlet을 사용하여 업데이트 목록을 가져오세요. 그런 다음, [New-CMOperatingSystemImageUpdateSchedule](https://docs.microsoft.com/powershell/module/configurationmanager/new-cmoperatingsystemimageupdateschedule?view=sccm-ps) cmdlet을 사용하여 오프라인 설치 일정을 만드세요. 다음 예는 이 작업을 자동화하는 한 가지 방법을 보여 줍니다.
>
> ```PowerShell
> # Get the OS image
> $Win10Image = Get-CMOperatingSystemImage -Name "Windows 10 Enterprise"
>
> # Get the latest cumulative update for Windows 10 1809
> $OSBuild = "1809"
> $LatestUpdate = Get-CMSoftwareUpdate -Fast | Where {$_.LocalizedDisplayName -Like "*Cumulative Update for Windows 10 Version $OSBuild for x64*" -and $_.LocalizedDisplayName -notlike "*Dynamic*"} | Sort-Object ArticleID -Descending | Select -First 1
> Write-Host "Latest update for Windows 10 build" $OSBuild "is" $LatestUpdate.LocalizedDisplayName
>
> # Create a new update schedule to apply the latest update
> New-CMOperatingSystemImageUpdateSchedule -Name $Win10Image.Name -SoftwareUpdate $LatestUpdate -RunNow -ContinueOnError $True
> ```


### <a name="bkmk_installwim"></a> 기본 이미지만 사용

배포 작업 순서에서 기본 Windows install.wim 이미지 파일을 사용합니다.

#### <a name="advantages"></a>장점

- 알려진 좋은 원본이므로 이미지 손상 문제가 발생할 위험이 줄어듭니다.
- 이미지를 수정하지 않을 수 있습니다.

#### <a name="disadvantages"></a>단점

- 배포 중 업데이트 볼륨이 클 수 있습니다.
- 모든 디바이스의 배포 시간이 늘어납니다.
- 필요한 사용자 지정이 포함되지 않아 작업 순서 단계를 추가로 사용자 지정해야 할 수 있습니다.



## <a name="flowchart"></a>순서도

다음 순서도 다이어그램은 소프트웨어 업데이트 설치 단계가 작업 순서에 포함된 경우의 프로세스를 보여 줍니다.

[전체 화면 크기로 다이어그램 보기](media/ts-step-install-software-updates.svg)

![소프트웨어 업데이트 설치 작업 순서 단계의 순서도 다이어그램](media/ts-step-install-software-updates.svg)  

1. **클라이언트에서 프로세스 시작**: 클라이언트에서 실행되는 작업 순서에 소프트웨어 업데이트 설치 단계가 포함됩니다.
2. **정책 컴파일 및 평가**: 클라이언트는 모든 소프트웨어 업데이트 정책을 WMI RequestedConfigs 네임스페이스로 컴파일합니다. (CIAgent.log)
3. ‘이 인스턴스가 처음 호출되었습니까?’   
    1. **예**: **전체 검사**로 이동  
    2. **아니요**: ‘단계가 [캐시된 검사 결과에서 소프트웨어 업데이트 평가](/sccm/osd/understand/task-sequence-steps#evaluate-software-updates-from-cached-scan-results) 옵션을 사용하여 구성되었습니까?’ 
        1. **예**: **캐시된 결과에서 검사**로 이동
        2. **아니요**: **전체 검사**로 이동
4. 검사 프로세스: 전체 검사 또는 캐시된 결과에서 검사를 모니터링 프로세스와 병렬로 진행합니다.
    1. **전체 검사**: 작업 순서 엔진이 업데이트 검사 API를 통해 소프트웨어 업데이트 에이전트를 호출하여 ‘전체’ 검사를 수행합니다.  (WUAHandler.log, ScanAgent.log)  
        1. **SUM 에이전트 검사 - 전체**: WSUS 실행 소프트웨어 업데이트 지점과 통신하는 WUA(Windows 업데이트 에이전트)를 통한 일반 검사 프로세스입니다. 모든 적용 가능한 업데이트를 로컬 업데이트 저장소에 추가합니다. (WindowsUpdate.log, UpdateStore.log)
    2. **캐시된 결과에서 검색**: 작업 순서 엔진이 업데이트 검사 API를 통해 소프트웨어 업데이트 에이전트를 호출하여 캐시된 메타데이터에 대해 검사합니다. (WUAHandler.log, ScanAgent.log)
        1. **SUM 에이전트 검사 - 캐시됨**: WUA(Windows 업데이트 에이전트)는 로컬 업데이트 저장소에 이미 캐시된 업데이트에 대해 검사합니다. (WindowsUpdate.log, UpdateStore.log)
    3. **검사 타이머 시작**: 작업 순서 엔진이 타이머를 시작하고 대기합니다. (이 프로세스는 캐시된 결과 프로세스에서 검사 또는 전체 검사와 병렬로 진행됩니다.)
        1. **모니터링**: 작업 순서 엔진이 SUM 에이전트의 상태를 모니터링합니다.
        2. ‘SUM 에이전트의 응답은 무엇입니까?’ 
            - **진행 중**: 타이머가 작업 순서 변수 [SMSTSSoftwareUpdateScanTimeout](/sccm/osd/understand/task-sequence-variables#SMSTSSoftwareUpdateScanTimeout)의 값에 도달했습니까? (기본 1시간)
                - **예**: 단계가 실패합니다.
                - **아니요**: **모니터링**으로 이동
            - **실패**: 단계가 실패합니다.
            - **완료**: **업데이트 목록 열거**로 이동
5. **업데이트 목록 열거**: SUM 에이전트는 검사에서 반환하는 업데이트 목록을 열거하여 사용할 수 있는 업데이트 또는 필수 업데이트를 판별합니다.
6. ‘검사 결과 목록에 업데이트가 있습니까?’ 
    - **예**: **업데이트 설치**로 이동
    - **아니요**: 설치할 업데이트가 없으면 단계가 완료됩니다.
7. 배포 프로세스: 업데이트 설치 프로세스는 배포 모니터링 프로세스와 병렬로 진행됩니다.
    1. **업데이트 설치**: 작업 순서 엔진이 업데이트 배포 API를 통해 SUM 에이전트를 호출하여 모든 사용할 수 있는 업데이트를 설치하거나 필수 업데이트만 설치합니다. 이 동작은 단계 구성에서 **설치 필수 - 필수 소프트웨어 업데이트만**을 선택하는지 **설치 가능 - 모든 소프트웨어 업데이트**를 선택하는지에 따라 달라집니다. [SMSInstallUpdateTarget](/sccm/osd/understand/task-sequence-variables#SMSInstallUpdateTarget) 변수를 사용하여 이 동작을 지정할 수도 있습니다.
        1. **SUM 에이전트 설치**: 표준 콘텐츠 다운로드가 포함된, 기존의 캐시된 업데이트 목록을 사용하는 일반 설치 프로세스입니다. WUA(Windows 업데이트 에이전트)를 통해 업데이트를 설치합니다. (UpdatesDeployment.log, UpdatesHandler.log, WuaHandler.log, WindowsUpdate.log)
    2. **배포 타이머 시작 및 진행률 표시**: 작업 순서 엔진이 설치 타이머를 시작하고, TS 진행률 UI에 10% 간격으로 하위 진행률을 표시하고, 대기합니다.
        1. **모니터링**: 작업 순서 엔진이 SUM 에이전트의 상태를 폴링합니다.
        2. ‘SUM 에이전트의 응답은 무엇입니까?’ 
            - **진행 중**: ‘설치 프로세스가 8시간 동안 비활성 상태였습니까?’ 
                - **예**: 단계가 실패합니다.
                - **아니요**: **모니터링**으로 이동
            - **실패**: 단계가 실패합니다.
            - **완료**: ‘단계가 **캐시된 검사 결과에서 소프트웨어 업데이트 평가** 옵션을 사용하여 구성되었습니까?’로 이동 


### <a name="timeouts"></a>시간 제한

다이어그램에는 이 단계에 적용되는 두 개의 시간 제한 변수가 포함되어 있습니다. 이 프로세스에 영향을 줄 수 있는 다른 구성 요소에는 다른 표준 타이머가 있습니다.

- 업데이트 검사 시간 제한: 1시간(smsts.log)  
- 위치 요청 시간 제한: 1시간(LocationServices.log, CAS.log)  
- 콘텐츠 다운로드 시간 제한: 1시간(DTS.log)  
- 비활성 배포 지점 시간 제한: 1시간(LocationServices.log, CAS.log)  
- 총 설치 비활성 시간 제한: 8시간(smsts.log)  



## <a name="troubleshooting"></a>문제 해결

다음 리소스 및 추가 정보를 사용하면 이 단계와 관련된 문제를 해결하는 데 도움이 됩니다.

- 소프트웨어 업데이트 배포 대상은 작업 순서 배포와 동일한 컬렉션으로 지정해야 합니다.  

- 소프트웨어 업데이트 지점은 경계 그룹에 포함되어야 합니다. 자세한 내용은 [Microsoft 지원 문서](https://support.microsoft.com/help/4041012/1702-clients-do-not-get-software-updates-from-configuration-manager)를 참조하세요.  

- 소프트웨어 업데이트 관리 프로세스 문제를 해결하는 데 도움을 받으려면 [소프트웨어 업데이트 관리 문제 해결](https://support.microsoft.com/help/10680/software-update-management-troubleshooting-in-configuration-manager)을 참조하세요.  

- 전체 성능을 높이려면 소프트웨어 업데이트 카탈로그의 크기를 줄이세요. 예를 들면 다음과 같습니다.  

    - 불필요한 분류, 제품 및 언어를 제거합니다. 자세한 내용은 [동기화할 분류 및 제품 구성](/sccm/sum/get-started/configure-classifications-and-products)을 참조하세요.  

    - 사이트 데이터베이스 인덱스를 다시 작성하고 통계를 다시 빌드합니다. 자세한 내용은 [Configuration Manager Perf and Scale Guidance Whitepaper](https://gallery.technet.microsoft.com/Configuration-Manager-ba55428e)\(Configuration Manager 성능 및 크기 조정 지침 백서\)를 참조하세요.  

    - 불필요한 업데이트를 거부합니다. 예를 들어 다음과 같습니다.
        - 대체(버전 1810부터는 Configuration Manager에서 사용자를 위해 이 작업을 수행합니다. 자세한 내용은 [1810 버전부터 시작하는 WSUS 정리 동작](/sccm/sum/deploy-use/software-updates-maintenance#wsus-cleanup-behavior-starting-in-version-1810)을 참조하세요.)
        - Itanium
        - 베타
        - 다음 버전
        - ARM
        - 배포하지 않는 Windows 버전
