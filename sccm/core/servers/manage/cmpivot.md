---
title: 실시간 데이터에 대한 CMPivot
titleSuffix: Configuration Manager
description: Configuration Manager에서 CMPivot을 사용하여 실시간으로 클라이언트를 쿼리하는 방법을 알아봅니다.
ms.date: 08/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 32e2d6b9-148f-45e2-8083-98c656473f82
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2e0f74790437b34d1c5cd5dc00767ec782a51b45
ms.sourcegitcommit: fe279229a90fdc8cddbb13c7ffdbbb22af0e25ef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47229299"
---
# <a name="cmpivot-for-real-time-data-in-configuration-manager"></a>Configuration Manager에서 실시간 데이터에 대한 CMPivot

<!--1358456-->

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager는 고객이 보고용으로 사용하는 장치 데이터의 대규모 중앙 저장소를 항상 제공해왔습니다. 이 사이트는 일반적으로 매주 이 데이터를 수집합니다. 버전 1806부터 CMPivot은 사용자 환경에서 장치의 실시간 상태에 액세스할 수 있는 새로운 콘솔 내 유틸리티입니다. 이 유틸리티는 대상 컬렉션에서 현재 연결된 모든 장치에 대해 바로 쿼리를 실행하고 결과를 반환합니다. 그러면 도구에서 이 데이터를 필터링하고 그룹화합니다. 온라인 클라이언트에서 실시간 데이터를 제공함으로써 비즈니스 질문에 신속하게 대답하고 문제를 해결하며 보안 인시던트에 응답할 수 있습니다.

예를 들어, [잘못된 실행 부채널 취약성을 완화](https://blogs.technet.microsoft.com/configurationmgr/2018/01/08/additional-guidance-to-mitigate-speculative-execution-side-channel-vulnerabilities/)할 때 요구 사항 중 하나는 시스템 BIOS 업데이트입니다. CMPivot을 사용하여 시스템 BIOS 정보를 신속하게 쿼리하고 준수하지 않는 클라이언트를 찾을 수 있습니다.



## <a name="prerequisites"></a>필수 구성 요소

CMPivot을 사용하려면 다음 구성 요소가 필요합니다.

- 대상 장치를 Configuration Manager 클라이언트의 최신 버전으로 업그레이드합니다.  

- Configuration Manager 관리자는 **SMS 스크립트** 개체에서 **읽기** 권한 및 **컬렉션** 개체에서 **스크립트 실행** 권한이 필요합니다. **스크립트 실행기** 역할에는 이러한 권한이 있습니다. 자세한 내용은 [스크립트의 보안 역할](/sccm/apps/deploy-use/create-deploy-scripts#bkmk_ScriptRoles)을 참조하세요.  

- 다음 엔터티에 대한 데이터를 수집하기 위해 대상 클라이언트는 PowerShell 버전 5.0이 필요합니다.  
    - 관리자
    - 연결
    - IPConfig
    - SMBConfig 



## <a name="limitations"></a>제한 사항

- 계층 구조에서 Configuration Manager 콘솔을 CMPivot을 실행하는 *기본 사이트*에 연결합니다. **CMPivot 시작** 작업은 중앙 관리 사이트에 연결된 경우 콘솔에 표시되지 않습니다.  

- CMPivot은 현재 사이트에 연결된 클라이언트에 대한 데이터만을 반환합니다.  

- 컬렉션이 다른 사이트의 장치를 포함하는 경우 CMPivot 결과는 현재 사이트의 장치에서만 옵니다.  

- 엔터티 속성, 결과에 대한 열 또는 장치의 작업을 사용자 지정할 수 없습니다.  

- CMPivot의 하나의 인스턴스만 Configuration Manager 콘솔을 실행하는 컴퓨터에서 동시에 실행할 수 있습니다.  

- 버전 1806에서 **관리자** 엔터티에 대한 쿼리는 그룹 이름이 “Administrators”인 경우에만 작동합니다. 그룹 이름이 현지화된 경우에는 작동하지 않습니다. 예를 들어 프랑스어로 “Administrateurs”인 경우에는 작동하지 않습니다.<!--SCCMDocs issue 759-->  



## <a name="start-cmpivot"></a>CMPivot 시작

1. Configuration Manager 콘솔에서 기본 사이트에 연결합니다. **자산 및 규정 준수** 작업 영역으로 이동하여 **장치 컬렉션** 노드를 선택합니다. 대상 컬렉션을 선택하고 리본에서 **CMPivot 시작**을 클릭하여 도구를 시작합니다.  

    > [!Tip]  
    > 이 옵션이 표시되지 않는 경우 다음 구성을 확인합니다.  
    > 
    > - 사이트 관리자로 계정에 필요한 권한이 있는지 확인합니다. 자세한 내용은 [필수 구성 요소](#prerequisites)를 참조하세요.  
    > 
    > - 콘솔을 *기본 사이트*에 연결합니다.  

2. 인터페이스에서 도구 사용에 대한 추가 정보를 제공합니다.  

     - 맨 위에 쿼리 문자열을 수동으로 입력하거나 인라인 문서에서 링크를 클릭합니다.  

     - **엔터티** 중 하나를 클릭하여 쿼리 문자열에 추가합니다.  

     - **표 연산자**, **집계 함수** 및 **스칼라 함수**에 대한 링크를 클릭하면 웹 브라우저에서 언어 참조 문서를 엽니다. CMPivot은 [Azure Log Analytics](https://docs.microsoft.com/azure/kusto/query/)와 동일한 쿼리 언어를 사용합니다.  

3. CMPivot 창을 열어 두어 클라이언트에서 결과를 봅니다. CMPivot 창을 닫으면 세션이 완료됩니다.  

    > [!Note]  
    > 쿼리가 전송된 경우 클라이언트는 서버에 상태 메시지 응답을 계속 보냅니다.  



## <a name="how-to-use-cmpivot"></a>CMPivot을 사용하는 방법

![CMPivot 창 샘플](media/1358456-cmpivot-sample.png)

CMPivot 창은 다음과 같은 요소를 포함합니다.  

1. CMPivot에서 현재 대상으로 하는 컬렉션은 맨 위의 제목 표시줄 및 창 아래쪽의 상태 표시줄에 있습니다. 예를 들어 위의 스크린샷에서 **모든 시스템**입니다.  

2. 왼쪽의 창은 클라이언트에서 사용할 수 있는 **엔터티**를 나열합니다. 일부 엔터티는 WMI를 사용하는 반면 다른 엔터티는 PowerShell을 사용하여 클라이언트에서 데이터를 가져옵니다.   

    - 다음 작업에 대한 엔터티를 마우스 오른쪽 단추로 클릭합니다.  

       - **삽입**: 현재 커서 위치에서 쿼리에 엔터티를 추가합니다. 쿼리는 자동으로 실행되지 않습니다. 이 작업은 엔터티를 두 번 클릭할 때 기본값입니다. 쿼리를 작성하는 경우 이 작업을 사용합니다.  

       - **모두 쿼리**: 모든 속성을 포함하여 이 엔터티에 대한 쿼리를 실행합니다. 이 작업을 사용하여 단일 엔터티에 대해 신속하게 쿼리합니다.  

       - **장치별 쿼리**: 이 엔터티에 대한 쿼리를 실행하고 결과를 그룹화합니다. 예를 들면 `Disk | summarize dcount( Device ) by Name`  

    - 엔터티를 확장하여 각 엔터티에 사용할 수 있는 특정 속성을 봅니다. 속성을 두 번 클릭하여 현재 커서 위치에서 쿼리에 추가합니다.  

3. **홈** 탭은 샘플 쿼리에 대한 링크 및 지원되는 문서를 포함하여 CMPivot에 대한 일반 정보를 표시합니다.  

4. **쿼리** 탭은 쿼리 창, 결과 창 및 상태 표시줄을 표시합니다. 위의 스크린샷 예제에서 쿼리 탭이 선택됩니다.  

5. 쿼리 창은 컬렉션의 클라이언트에서 실행할 쿼리를 작성하거나 입력하는 위치입니다.  

    - CMPivot은 [Azure Log Analytics](https://docs.microsoft.com/azure/kusto/query/)와 동일한 쿼리 언어의 하위 집합을 사용합니다.  

    - 쿼리 창에서 콘텐츠를 잘라내기, 복사 또는 붙여넣습니다.  

    - 기본적으로 이 창에서는 IntelliSense를 사용합니다. 예를 들어 `D` 입력을 시작하는 경우 IntelliSense는 해당 문자로 시작하는 모든 엔터티를 제안합니다. 옵션을 선택하고 탭 키를 눌러 삽입합니다. 파이프 문자 및 공백 `| `을 입력하면, IntelliSense에서 모든 테이블 연산자를 제안합니다. `summarize`를 삽입하고 공백을 입력하면, IntelliSense에서 모든 집계 함수를 제안합니다. 이러한 연산자 및 함수에 대한 자세한 내용은 CMPivot에서 **홈** 탭을 클릭합니다.  

    - 쿼리 창은 또한 다음 옵션을 제공합니다.  

        - 쿼리를 실행합니다.  

        - 쿼리의 기록 목록에서 뒤나 앞으로 이동합니다.  

        - 직접 멤버 자격 컬렉션을 만듭니다.  

        - CSV 또는 클립보드로 쿼리 결과를 내보냅니다.  

6. 결과 창은 쿼리에 대한 활성 클라이언트에서 반환한 데이터를 표시합니다.  

    - 사용 가능한 열은 엔터티 및 쿼리에 따라 달라집니다.  

    - 열 이름을 클릭하여 해당 속성으로 결과를 정렬합니다.  

    - 열 이름을 마우스 오른쪽 단추로 클릭하여 해당 열의 동일한 정보로 결과를 그룹화하거나 결과를 정렬합니다.  

    - 장치 이름을 마우스 오른쪽 단추로 클릭하여 장치에서 다음 추가 작업을 수행합니다.  

       - **피벗 대상**: 이 장치에서 다른 엔터티에 대해 쿼리합니다.  

       - **스크립트 실행**: 스크립트 실행 마법사를 시작하여 이 장치에서 기존 PowerShell 스크립트를 실행합니다. 자세한 내용은 [스크립트 실행](/sccm/apps/deploy-use/create-deploy-scripts#run-a-script)을 참조하세요.  

       - **원격 제어**:이 장치에서 Configuration Manager 원격 제어 세션을 시작합니다. 자세한 내용은 [Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법](/sccm/core/clients/manage/remote-control/remotely-administer-a-windows-client-computer)을 참조하세요.  

       - **리소스 탐색기**: 이 장치에 대한 Configuration Manager 리소스 탐색기를 시작합니다. 자세한 내용은 [하드웨어 인벤토리 보기](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory) 또는 [소프트웨어 인벤토리 보기](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory)를 참조하세요.  

    - 비 장치 셸을 마우스 오른쪽 단추로 클릭하여 다음 추가 작업을 수행합니다.  

       - **복사**: 셀의 텍스트를 클립보드에 복사합니다.  

       - **다음과 함께 장치 표시**: 이 속성에 대한 이 값을 사용하여 장치에 대해 쿼리합니다. 예를 들어 `OS` 쿼리의 결과에서, 버전 행의 셀에서 이 옵션을 선택합니다. `OS | summarize countif( (Version == '10.0.17134') ) by Device | where (countif_ > 0)`  

       - **다음 없이 장치 표시**: 이 속성에 대한 이 값 없이 장치에 대해 쿼리합니다. 예를 들어 `OS` 쿼리의 결과에서, 버전 행의 셀에서 이 옵션을 선택합니다. `OS | summarize countif( (Version == '10.0.17134') ) by Device | where (countif_ == 0) | project Device`  

       - **Bing으로 검색**: 쿼리 문자열로 이 값을 사용하여 www.bing.com에 대한 기본 웹 브라우저를 시작합니다.  

    - 하이퍼링크 텍스트를 클릭하여 해당 특정 정보에서 보기를 피벗합니다.  

    - 결과 창은 20,000개를 초과하는 행을 표시하지 않습니다. 데이터를 추가 필터링하도록 쿼리를 조정하거나 더 작은 컬렉션에서 CMPivot을 다시 시작합니다.  

7. 상태 표시줄은 다음 정보를 표시합니다(왼쪽에서 오른쪽으로).  

    - 대상 컬렉션에 대한 현재 쿼리의 상태 이 상태는 다음을 포함합니다.  
        - 쿼리를 완료한 활성 클라이언트 수(3)  
        - 총 클라이언트 수(5)  
        - 오프라인 클라이언트 수(2)  
        - 오류를 반환한 모든 클라이언트(0)  

        예를 들면 다음과 같습니다. `Query completed on 3 of 5 clients (2 clients offline and 0 failure)`  

    - 클라이언트 작업의 ID입니다. 예를 들면 다음과 같습니다. `id(16780221)`  

    - 현재 컬렉션입니다. 예를 들면 다음과 같습니다. `PM_Team_Machines`  

    - 결과 창에서 행의 총 수입니다. 예를 들면 `1 objects`  



## <a name="example-scenarios"></a>예제 시나리오

다음 섹션에서는 사용자의 환경에서 CMPivot을 사용하는 방법의 예제를 제공합니다.


### <a name="example-1-stop-a-running-service"></a>예제 1: 실행 중인 서비스 중지

보안 관리자는 회계 부서의 모든 장치에서 가능한 빨리 컴퓨터 브라우저 서비스를 중지하고 비활성화하도록 요청합니다. 회계 부서의 모든 장치에 대한 컬렉션에서 CMPivot을 시작하고, **서비스** 엔터티에서 **모두 쿼리**를 선택합니다. 

`Service`

결과가 표시되면 **이름** 열을 마우스 오른쪽 단추로 클릭하고 **그룹화 기준**을 선택합니다. 

`Service | summarize dcount( Device ) by Name`

**브라우저** 서비스에 대한 행에서 **dcount_** 열의 하이퍼링크된 숫자를 클릭합니다. 

`Service | where (Name == 'Browser') | summarize count() by Device`

모든 장치를 다중 선택하고, 선택 영역을 마우스 오른쪽 단추로 클릭하고, **스크립트 실행**을 선택합니다. 이 작업은 서비스를 중지하고 비활성화하기 위해 기존 스크립트를 실행하는 스크립트 실행 마법사를 시작합니다. CMPivot을 사용하여 스크립트 실행 마법사에서 결과를 보고 모든 활성 컴퓨터에 대한 보안 인시던트에 신속하게 응답합니다. 그런 다음, 구성 기준을 만들도록 후속 조치하여 컬렉션에서 다른 컴퓨터를 수정합니다. 나중에 활성화되기 때문입니다. 

![브라우저 서비스 및 스크립트 실행 작업에 대한 CMPivot 예제](media/cmpivot-example1.png)


### <a name="example-2-proactively-resolve-application-failures"></a>예제 2: 응용 프로그램 오류 사전 해결  

작업 유지 관리를 사용하여 사전 대응하려면 일주일에 한 번 관리하는 서버의 컬렉션에 대해 CMPivot을 실행하고, **AppCrash** 엔터티에서 **모두 쿼리**를 선택합니다. **FileName** 열을 마우스 오른쪽 단추로 클릭하고 **오름차순 정렬**을 선택합니다. 하나의 장치는 매일 약 03:00의 타임스탬프로 sqlsqm.exe에 대한 7개의 결과를 반환합니다. 행 중 하나에서 파일 이름을 선택하고, 마우스 오른쪽 단추로 선택하고 **Bing으로 검색**을 선택합니다. 웹 브라우저에서 검색 결과를 검색하여 이 문제에 대한 더 많은 정보 및 해결이 있는 Microsoft 지원 문서를 찾습니다. 


### <a name="example-3-bios-version"></a>예제 3: BIOS 버전

[잘못된 실행 부채널 취약성을 완화](https://blogs.technet.microsoft.com/configurationmgr/2018/01/08/additional-guidance-to-mitigate-speculative-execution-side-channel-vulnerabilities/)하기 위해 요구 사항 중 하나는 시스템 BIOS를 업데이트하는 것입니다. **BIOS** 엔터티에 대한 쿼리를 시작합니다. 그런 다음, **버전** 속성별로 **그룹화**합니다. 그런 다음, "LENOVO - 1140"과 같은 특정 값을 마우스 오른쪽 단추로 클릭하고 **다음과 함께 장치 표시**를 선택합니다.  

`Bios | summarize countif( (Version == 'LENOVO - 1140') ) by Device | where (countif_ > 0)`


### <a name="example-4-free-disk-space"></a>예제 4: 사용 가능한 디스크 공간

네트워크 파일 서버에 큰 파일을 일시적으로 저장해야 하지만 어떤 파일 서버에 충분한 용량이 있는지 확실하지 않습니다. 파일 서버의 컬렉션에 대해 CMPivot을 시작하고, **디스크** 엔터티를 쿼리합니다. CMPivot에 대한 쿼리를 수정하여 실시간 저장소 데이터로 활성 서버의 목록을 신속하게 반환합니다.  

`Disk | where (Description == 'Local Fixed Disk') | where isnotnull( FreeSpace ) | order by FreeSpace asc`



## <a name="inside-cmpivot"></a>내부 CMPivot

CMPivot은 Configuration Manager "빠른 채널"을 사용하여 클라이언트에게 쿼리를 보냅니다. 서버에서 클라이언트로의 이 통신 채널은 클라이언트 알림 작업, 클라이언트 상태 및 엔드포인트 보호와 같은 다른 기능에서도 사용됩니다. 클라이언트는 마찬가지로 빠른 상태 메시지 시스템을 통해 결과를 반환합니다. 상태 메시지는 데이터베이스에 임시로 저장됩니다. 

쿼리 및 결과는 모두 텍스트입니다. 엔터티 **InstallSoftware** 및 **Process**는 가장 큰 결과 집합의 일부를 반환합니다. 성능 테스트 중에 이러한 쿼리에 대한 하나의 클라이언트에서 가장 큰 상태 메시지 파일 크기는 **1KB**보다 작았습니다. 50,000명의 활성 클라이언트를 사용하여 대규모 환경으로 확장하여 이 일회성 쿼리는 네트워크에서 50MB보다 작은 데이터를 생성합니다.  

쿼리는 1시간 후 시간 초과됩니다. 예를 들어 컬렉션에 500개의 장치가 있고, 450명의 클라이언트는 현재 온라인 상태입니다. 이러한 활성 장치는 쿼리를 수신하고 거의 즉시 결과를 반환합니다. CMPivot 창을 열린 상태로 두면 다른 50명의 클라이언트도 온라인 상태가 되므로 쿼리를 수신하고, 결과를 반환합니다. 

>[!TIP]
> CMPivot 상호 작용은 다음 로그 파일에 로깅됩니다.
>
> **서버 쪽:**
> - SmsProv.log
> - bgbServer.log
> - StateSys.log
>
> **클라이언트 쪽:**
> - CCMNotificationAgent.log
> - Scripts.log
> - StateMessage.log
>
> 자세한 내용은 [로그 파일](/sccm/core/plan-design/hierarchy/log-files)을 참조하세요.


## <a name="see-also"></a>참고 항목
[PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)
