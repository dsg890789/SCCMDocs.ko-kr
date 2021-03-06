---
title: 단계별 배포 만들기
titleSuffix: Configuration Manager
description: 단계별 배포를 통해 여러 컬렉션에 대한 소프트웨어의 배포를 자동화합니다.
ms.date: 04/16/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b634ff68-b909-48d2-9e2c-0933486673c5
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 7a4acf706d84eacbf39c672f3c1d9afc77de7ffa
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825424"
---
# <a name="create-phased-deployments-with-configuration-manager"></a>Configuration Manager를 사용하여 단계별 배포 만들기

*적용 대상: Configuration Manager(현재 분기)*

단계별 배포는 여러 컬렉션에 대한 소프트웨어 출시를 자동으로 조정하고 순차적으로 진행합니다. 예를 들어, 파일럿 컬렉션에 소프트웨어를 배포한 다음, 성공 조건에 따라 배포를 자동으로 계속합니다. 기본적으로 두 단계의 단계별 배포를 만들거나 여러 단계를 수동으로 구성합니다. 

다음 개체에 대한 단계적 배포 만들기
- **작업 순서**  
    - 작업 순서의 단계별 배포는 PXE 또는 미디어 설치를 지원하지 않음   
- **애플리케이션**(1806 버전부터 시작) <!--1358147-->  
- **소프트웨어 업데이트**(1810 버전부터 시작) <!--1358146-->  
    - 단계별 배포를 사용하면 자동 배포 규칙을 사용할 수 없음

> [!Tip]  
> 단계별 배포 기능은 버전 1802에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1806 버전부터는 더 이상 시험판 기능이 아닙니다.<!--1356837-->  



## <a name="prerequisites"></a>전제 조건

#### <a name="security-scope"></a>보안 범위
**모든** 보안 범위를 갖지 않는 모든 관리 사용자는 단계별 배포에서 만든 배포를 볼 수 없습니다. 자세한 내용은 [보안 범위](/sccm/core/understand/fundamentals-of-role-based-administration#bkmk_PlanScope)를 참조하세요.

#### <a name="distribute-content"></a>콘텐츠 배포
단계별 배포를 만들기 전에 연결된 콘텐츠를 배포 지점에 배포합니다.<!--518293-->  

- **애플리케이션**: 콘솔에서 대상 애플리케이션을 선택하고 리본에서 **콘텐츠 배포** 작업을 사용합니다. 자세한 내용은 [콘텐츠 배포 및 관리](/sccm/core/servers/deploy/configure/deploy-and-manage-content)를 참조하세요.   

- **작업 순서**: 작업 순서를 만들기 전에 OS 업그레이드 패키지 같은 참조 개체를 만들어야 합니다. 배포를 만들기 전에 이러한 개체를 배포합니다. 각 개체 또는 작업 순서에서 **콘텐츠 배포** 작업을 사용합니다. 모든 참조된 콘텐츠의 상태를 확인하려면 작업 순서를 선택하고 세부 정보 창에서 **참조** 탭으로 전환합니다. 자세한 내용은 [OS 배포 준비](/sccm/osd/get-started/prepare-for-operating-system-deployment)에서 특정 개체 형식을 참조하세요.   

- **소프트웨어 업데이트**: 배포 패키지를 만들어 배포합니다. 소프트웨어 업데이트 다운로드 마법사를 사용합니다. 자세한 내용은 [소프트웨어 업데이트 다운로드](/sccm/sum/deploy-use/download-software-updates)를 참조하세요.  



## <a name="bkmk_settings"></a> 단계 설정

이러한 설정은 단계별 배포에만 적용됩니다. 단계를 만들거나 편집할 때 이러한 설정을 구성하여 단계별 배포 프로세스의 일정과 동작을 제어합니다. 


#### <a name="criteria-for-success-of-the-first-phase"></a>첫 번째 단계의 성공 조건  

- **배포 성공률**: 첫 번째 단계를 성공한 것으로 간주하기 위해 배포가 성공적으로 완료되어야 하는 디바이스의 백분율을 지정합니다. 이 값은 기본적으로 95%입니다. 즉, 이 배포에 대한 95% 디바이스의 준수 상태가 **성공**일 때 사이트에서 첫 번째 단계를 성공한 것으로 간주합니다. 그런 다음, 사이트는 두 번째 단계로 계속 진행하고, 다음 컬렉션에 소프트웨어 배포를 만듭니다.  
- **성공적으로 배포된 디바이스 수**: Configuration Manager 버전 1902에 추가되었습니다. 첫 번째 단계를 성공한 것으로 간주하기 위해 배포가 성공적으로 완료되어야 하는 디바이스의 수를 지정합니다. 이 옵션은 컬렉션의 크기가 변수이고, 다음 단계로 이동하기 전에 성공을 표시하는 특정 수의 디바이스가 있을 때 유용합니다. <!--3555946-->


#### <a name="conditions-for-beginning-second-phase-of-deployment-after-success-of-the-first-phase"></a>첫 번째 단계 성공 후 배포의 두 번째 단계를 시작하기 위한 조건  

- **지연 기간(일) 후 자동으로 이 단계 시작**: 첫 단계 성공 후 두 번째 단계 시작 전까지 대기하는 기간(일)을 선택합니다. 이 값은 기본적으로 1일입니다.  

- **배포의 두 번째 단계를 수동으로 시작**: 사이트는 첫 번째 단계가 성공한 후 자동으로 두 번째 단계를 시작하지 않습니다. 이 옵션을 사용하면 두 번째 단계를 수동으로 시작해야 합니다. 자세한 내용은 [다음 단계로 이동](/sccm/osd/deploy-use/manage-monitor-phased-deployments#bkmk_move)을 참조하세요.  

    > [!Note]  
    > 이 옵션은 애플리케이션의 단계별 배포에 사용할 수 없습니다.  


#### <a name="gradually-make-this-software-available-over-this-period-of-time-in-days"></a>이 기간(일)에 걸쳐 점진적으로 이 소프트웨어를 사용할 수 있도록 함
<!--1358578-->
버전 1806부터 각 단계의 배포가 점진적으로 실행되도록 하려면 이 설정을 구성합니다. 이 동작은 배포 문제의 위험을 완화하고 클라이언트에 대한 콘텐츠의 배포로 인한 네트워크 부하를 줄이는 데 도움이 됩니다. 사이트에서는 각 단계의 구성에 따라 점진적으로 소프트웨어를 사용할 수 있게 합니다. 단계의 모든 클라이언트는 소프트웨어를 사용할 수 있게 되는 시간을 기준으로 최종 기한을 갖게 됩니다. 사용 가능 시간과 최종 기한 사이의 기간은 단계의 모든 클라이언트에 대해 동일합니다. 이 설정의 기본값은 0이므로 기본적으로 배포가 제한되지 않습니다. 30보다 큰 값을 설정하지 마세요.<!--SCCMDocs-pr issue 2767--> 

![성공을 위한 단계적 배포 조건 설정](media/phased-deployment-criteria-for-success.png)

#### <a name="configure-the-deadline-behavior-relative-to-when-the-software-is-made-available"></a>소프트웨어를 사용할 수 있게 되는 시점을 기준으로 최종 기한 동작 구성  

- **가능한 한 빨리 설치 필요**: 디바이스를 대상으로 지정하는 즉시 디바이스에 설치하는 최종 기한을 설정합니다.  

- **이 기간이 지나면 설치 필요**: 디바이스가 대상으로 지정되고 설치가 진행되기까지의 특정 일 수를 설정합니다. 이 값은 기본적으로 7일입니다.   


<!--### Examples
Include a timeline diagram
-->



## <a name="bkmk_auto"></a> 자동으로 기본 두 단계 배포 만들기

1. Configuration Manager 콘솔에서 단계별 배포 만들기 마법사를 시작합니다. 이 작업은 배포하려는 소프트웨어 종류에 따라 다릅니다.  

    - **애플리케이션**(버전 1806 이상에서만): **소프트웨어 라이브러리**로 이동하고 **애플리케이션 관리**를 확장한 다음, **애플리케이션**을 선택합니다. 기존 애플리케이션을 선택한 다음, 리본에서 **단계별 배포 만들기**를 선택합니다.  

    - **소프트웨어 업데이트**(버전 1810 이상에서만): **소프트웨어 라이브러리**로 이동하고 **소프트웨어 업데이트**를 확장한 다음, **모든 소프트웨어 업데이트**를 선택합니다. 하나 이상의 업데이트 하나를 선택한 다음, 리본에서 **단계적 배포 만들기**를 선택합니다.  

        이 작업은 다음 노드에서 소프트웨어 업데이트에 대해 사용할 수 있습니다.  
        - 소프트웨어 업데이트  
            - **모든 소프트웨어 업데이트**  
            - **소프트웨어 업데이트 그룹**   
        - Windows 10 서비스, **모든 Windows 10 업데이트**  
        - Office 365 클라이언트 관리, **Office 365 업데이트**  

    - **작업 순서**: **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장한 다음, **작업 순서**를 선택합니다. 기존 작업 순서를 선택한 다음, 리본에서 **단계별 배포 만들기**를 선택합니다.  

2. **일반** 페이지에서 단계별 배포에 **이름**, **설명**(선택 사항)을 지정하고 **자동으로 기본 두 단계 배포 만들기**를 선택합니다.  

3. **찾아보기**를 선택하고 **첫 번째 컬렉션** 및 **두 번째 컬렉션** 필드 모두에 대해 대상 컬렉션을 선택합니다. 작업 순서 및 소프트웨어의 경우 디바이스 컬렉션에서 선택합니다. 애플리케이션의 경우 사용자 또는 디바이스 컬렉션에서 선택합니다. **다음**을 선택합니다.  

    > [!Important]  
    > 단계별 배포 만들기 마법사는 배포가 잠재적으로 위험성이 높은 경우 사용자에게 알리지 않습니다. 자세한 내용은 [높은 위험 수준의 배포를 관리하는 설정](/sccm/core/servers/manage/settings-to-manage-high-risk-deployments) 및 [작업 순서 배포](/sccm/osd/deploy-use/deploy-a-task-sequence) 시 참고 사항을 참조하세요.  

4. **설정** 페이지에서 각 일정 설정에 하나의 옵션을 선택합니다. 자세한 내용은 [단계 설정](#bkmk_settings)을 참조하세요. 완료되면 **다음**을 선택합니다.  

5. **단계** 페이지에서 마법사가 지정된 컬렉션에 대해 만드는 두 단계를 참조하세요. **다음**을 선택합니다.   

    > [!Note]  
    > 이 섹션에서는 기본 두 단계 배포를 자동으로 만드는 절차를 설명합니다. 마법사를 사용하여 단계별 배포의 단계를 추가, 제거, 다시 정렬, 편집 또는 확인할 수 있습니다. 이러한 추가 작업에 대한 자세한 내용은 [수동으로 구성된 단계를 사용하여 단계별 배포 만들기](#bkmk_manual)를 참조하세요.  

6. **요약** 탭에서 선택 사항을 확인한 후, **다음**을 선택하여 마법사를 완료합니다.  



## <a name="bkmk_manual"></a> 수동으로 구성된 단계를 사용하여 단계별 배포 만들기
<!--1358148--> 

버전 1806부터 작업 순서에 대해 수동으로 구성된 단계를 사용하여 단계별 배포를 만듭니다. 단계별 배포 만들기 마법사의 **단계** 탭에서 최대 10개의 추가 단계를 추가합니다. 

> [!Note]  
> 현재 애플리케이션에 대한 단계를 수동으로 만들 수 없습니다. 마법사에서 애플리케이션 배포에 대한 두 단계를 자동으로 만듭니다.


1. 작업 순서 또는 소프트웨어 업데이트 중 하나에 대해 단계적 배포 만들기 마법사를 시작합니다.  

2. 단계별 배포 만들기 마법사의 **일반** 페이지에서 단계별 배포에 **이름**,**설명**(선택 사항)을 지정하고 **수동으로 모든 단계 구성**을 선택합니다.  

3. 단계별 배포 만들기 마법사의 **단계** 페이지에서 다음 작업을 사용할 수 있습니다.  

    - 배포 단계의 목록을 **필터링**합니다. 대/소문자를 구분하지 않는 순서, 이름 또는 컬렉션 열의 문자열을 입력합니다. 

    - 새 단계 **추가**:  

        1. 단계 추가 마법사의 **일반** 페이지에서 단계의 **이름**을 지정한 다음, 대상 **단계 컬렉션**으로 이동합니다. 이 페이지의 추가 설정은 일반적으로 작업 순서 또는 소프트웨어 업데이트를 배포할 때와 동일합니다.  

        2. 단계 추가 마법사의 **단계 설정** 페이지에서 일정 설정을 구성하고 완료 시 **다음**을 선택합니다. 자세한 내용은 [설정](#bkmk_settings)을 참조하세요.   

            > [!Note]  
            > 단계 설정, **배포 성공률** 또는 **성공적으로 배포된 디바이스 수**(버전 1902 이상)은 첫 번째 단계에서 편집할 수 없습니다. 이 설정은 이전 단계가 있는 단계에만 적용됩니다.  

        3. 단계 추가 마법사의 **사용자 환경** 및 **배포 지점** 페이지의 설정은 일반적으로 작업 순서 또는 소프트웨어 업데이트를 배포할 때와 동일합니다.  

        4. **요약** 페이지에서 설정을 검토한 다음, 단계 추가 마법사를 완료합니다.  

    - **편집**: 이 작업을 수행하면 단계 추가 마법사의 페이지와 동일한 탭이 있는 선택한 단계의 속성 창이 열립니다.  

    - **제거**: 이 작업을 수행하면 선택한 단계가 삭제됩니다.  

       > [!Warning]  
       > 확인 과정은 없으며, 이 작업의 실행을 취소할 방법도 없습니다.  

    - **위로 이동** 또는 **아래로 이동**: 마법사는 사용자가 단계를 추가하는 방법에 따라 순서를 지정합니다. 가장 최근에 추가된 단계는 목록의 마지막에 있습니다. 순서를 변경하려면 단계를 선택한 다음, 이러한 단추를 사용하여 목록에서 단계의 위치를 이동합니다.  

       > [!Important]  
       > 순서를 변경한 후 단계 설정을 검토합니다. 다음 설정이 이 단계별 배포에 대한 요구 사항과 일치하는지 확인합니다.  
       > 
       > - 이전 단계의 성공을 위한 조건  
       > - 이전 단계 성공 후 배포의 이 단계를 시작하기 위한 조건   

5. **다음**을 선택합니다. **요약** 페이지에서 설정을 검토한 다음, 단계별 배포 만들기 마법사를 완료합니다.  


단계별 배포를 만든 후, 해당 속성을 열어 다음과 같이 변경합니다.  

- 기존 단계별 배포에 추가 단계를 **추가**합니다.  

- 단계가 활성화되어 있지 않으면 **편집**, **제거** 또는 위나 아래로 **이동**할 수 있습니다. 활성 단계 앞으로는 이동할 수 없습니다.  

- 단계가 활성화되면 읽기 전용입니다. 편집, 제거하거나 목록에서 위치를 이동할 수 없습니다. 유일한 옵션은 단계의 속성을 **확인**하는 것입니다.  

- 애플리케이션 단계별 배포는 항상 읽기 전용입니다.  



## <a name="next-steps"></a>다음 단계

단계적 배포 관리 및 모니터링
- [애플리케이션](/sccm/osd/deploy-use/manage-monitor-phased-deployments?toc=/sccm/apps/toc.json&bc=/sccm/apps/breadcrumb/toc.json)  
- [소프트웨어 업데이트](/sccm/osd/deploy-use/manage-monitor-phased-deployments?toc=/sccm/sum/toc.json&bc=/sccm/sum/breadcrumb/toc.json)  
- [작업 순서](/sccm/osd/deploy-use/manage-monitor-phased-deployments)  

