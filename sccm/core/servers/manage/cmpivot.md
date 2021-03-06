---
title: 실시간 데이터에 대한 CMPivot
titleSuffix: Configuration Manager
description: Configuration Manager에서 CMPivot을 사용하여 실시간으로 클라이언트를 쿼리하는 방법을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 32e2d6b9-148f-45e2-8083-98c656473f82
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: e7d9062d45d553eb2aa8b83621cecda46a17aa9b
ms.sourcegitcommit: e7583b5e522d01bc8710ec8e0fe3e5f75a281577
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035320"
---
# <a name="cmpivot-for-real-time-data-in-configuration-manager"></a>Configuration Manager에서 실시간 데이터에 대한 CMPivot

<!--1358456-->

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager는 고객이 보고용으로 사용하는 디바이스 데이터의 대규모 중앙 저장소를 항상 제공해왔습니다. 이 사이트는 일반적으로 매주 이 데이터를 수집합니다. 버전 1806부터 CMPivot은 사용자 환경에서 디바이스의 실시간 상태에 액세스할 수 있는 새로운 콘솔 내 유틸리티입니다. 이 유틸리티는 대상 컬렉션에서 현재 연결된 모든 디바이스에 대해 바로 쿼리를 실행하고 결과를 반환합니다. 그러면 도구에서 이 데이터를 필터링하고 그룹화합니다. 온라인 클라이언트에서 실시간 데이터를 제공함으로써 비즈니스 질문에 신속하게 대답하고 문제를 해결하며 보안 인시던트에 응답할 수 있습니다.

예를 들어, [잘못된 실행 부채널 취약성을 완화](https://techcommunity.microsoft.com/t5/configuration-manager-blog/additional-guidance-to-mitigate-speculative-execution-side/ba-p/274974)할 때 요구 사항 중 하나는 시스템 BIOS 업데이트입니다. CMPivot을 사용하여 시스템 BIOS 정보를 신속하게 쿼리하고 준수하지 않는 클라이언트를 찾을 수 있습니다.

 > [!Tip]  
 > 일부 보안 소프트웨어는 c:\windows\ccm\scriptstore에서 실행되는 스크립트를 차단할 수 있습니다. 이 기능은 CMPivot 쿼리가 성공적인 실행되지 않도록 막을 수 있습니다. 일부 보안 소프트웨어는 CMPivot PowerShell을 실행할 때 감사 이벤트 또는 경고를 생성할 수도 있습니다.


## <a name="prerequisites"></a>전제 조건

CMPivot을 사용하려면 다음 구성 요소가 필요합니다.

- 대상 디바이스를 Configuration Manager 클라이언트의 최신 버전으로 업그레이드합니다.  

- 대상 클라이언트에는 PowerShell 버전 4가 필요합니다.

- 다음 엔터티에 대한 데이터를 수집하기 위해 대상 클라이언트는 PowerShell 버전 5.0이 필요합니다.  
  - Administrators
  - 연결
  - IPConfig
  - SMBConfig


- CMPivot에 대한 사용 권한:
  - **SMS 스크립트** 개체에 대한 **읽기** 권한
  - **컬렉션**에 대한 **스크립트 실행** 권한
    - 또는, 버전 1906부터 **컬렉션**에서 **CMPivot 실행**을 사용할 수 있습니다.
  - **인벤토리 보고서**에 대한 **읽기** 권한
  - 기본 범위입니다.

>[!NOTE]
> **스크립트 실행**은 **CMPivot 실행** 권한의 상위 집합입니다.
 
## <a name="limitations"></a>제한 사항

- 계층 구조에서 Configuration Manager 콘솔을 CMPivot을 실행하는 *기본 사이트*에 연결합니다. **CMPivot 시작** 작업은 CAS(중앙 관리 사이트)에 연결된 경우 콘솔에 표시되지 않습니다.
  - Configuration Manager 버전 1902부터는 CAS에서 CMPivot을 실행할 수 있습니다. 일부 환경에서는 추가 권한이 필요합니다. 자세한 내용은 [1902 버전부터 CMPivot](#bkmk_cmpivot1902)을 참조하세요.

- CMPivot은 현재 사이트에 연결된 클라이언트에 대한 데이터만을 반환합니다.  

- 컬렉션이 다른 사이트의 디바이스를 포함하는 경우 CMPivot 결과는 현재 사이트의 디바이스에서만 옵니다.  

- 엔터티 속성, 결과에 대한 열 또는 디바이스의 작업을 사용자 지정할 수 없습니다.  

- CMPivot의 하나의 인스턴스만 Configuration Manager 콘솔을 실행하는 컴퓨터에서 동시에 실행할 수 있습니다.  

- 버전 1806에서 **관리자** 엔터티에 대한 쿼리는 그룹 이름이 “Administrators”인 경우에만 작동합니다. 그룹 이름이 현지화된 경우에는 작동하지 않습니다. 예를 들어 프랑스어로 "Administrateurs"인 경우입니다.<!--SCCMDocs issue 759-->  


## <a name="start-cmpivot"></a>CMPivot 시작

1. Configuration Manager 콘솔에서 기본 사이트에 연결합니다. **자산 및 규정 준수** 작업 영역으로 이동하여 **디바이스 컬렉션** 노드를 선택합니다. 대상 컬렉션을 선택하고 리본에서 **CMPivot 시작**을 클릭하여 도구를 시작합니다.  

    > [!Tip]  
    > 이 옵션이 표시되지 않는 경우 다음 구성을 확인합니다.  
    > 
    > - 사이트 관리자로 계정에 필요한 권한이 있는지 확인합니다. 자세한 내용은 [필수 구성 요소](#prerequisites)를 참조하세요.  
    > 
    > - 콘솔을 *기본 사이트*에 연결합니다.  

2. 인터페이스에서 도구 사용에 대한 추가 정보를 제공합니다.  

     - 맨 위에 쿼리 문자열을 수동으로 입력하거나 인라인 문서에서 링크를 클릭합니다.  

     - **엔터티** 중 하나를 클릭하여 쿼리 문자열에 추가합니다.  

     - **표 연산자**, **집계 함수** 및 **스칼라 함수**에 대한 링크를 클릭하면 웹 브라우저에서 언어 참조 문서를 엽니다. CMPivot은 [KQL(Kusto 쿼리 언어)](https://docs.microsoft.com/azure/kusto/query/)을 사용합니다.  

3. CMPivot 창을 열어 두어 클라이언트에서 결과를 봅니다. CMPivot 창을 닫으면 세션이 완료됩니다.  

    > [!Note]  
    > 쿼리가 전송된 경우 클라이언트는 서버에 상태 메시지 응답을 계속 보냅니다.  



## <a name="how-to-use-cmpivot"></a>CMPivot을 사용하는 방법

![CMPivot 창 샘플](media/1358456-cmpivot-sample.png)

CMPivot 창은 다음과 같은 요소를 포함합니다.  

1. CMPivot에서 현재 대상으로 하는 컬렉션은 맨 위의 제목 표시줄 및 창 아래쪽의 상태 표시줄에 있습니다. 예를 들어 위의 스크린샷에서 "PM_Team_Machines"인 경우입니다.  

2. 왼쪽의 창은 클라이언트에서 사용할 수 있는 **엔터티**를 나열합니다. 일부 엔터티는 WMI를 사용하는 반면 다른 엔터티는 PowerShell을 사용하여 클라이언트에서 데이터를 가져옵니다.   

    - 다음 작업에 대한 엔터티를 마우스 오른쪽 단추로 클릭합니다.  

       - **삽입**: 현재 커서 위치에서 쿼리에 엔터티를 추가합니다. 쿼리는 자동으로 실행되지 않습니다. 이 작업은 엔터티를 두 번 클릭할 때 기본값입니다. 쿼리를 작성하는 경우 이 작업을 사용합니다.  

       - **모두 쿼리**: 모든 속성을 포함하여 이 엔터티에 대한 쿼리를 실행합니다. 이 작업을 사용하여 단일 엔터티에 대해 신속하게 쿼리합니다.  

       - **디바이스별 쿼리**: 이 엔터티에 대한 쿼리를 실행하고 결과를 그룹화합니다. 예, `Disk | summarize dcount( Device ) by Name`  

    - 엔터티를 확장하여 각 엔터티에 사용할 수 있는 특정 속성을 봅니다. 속성을 두 번 클릭하여 현재 커서 위치에서 쿼리에 추가합니다.  

3. **홈** 탭은 샘플 쿼리에 대한 링크 및 지원되는 문서를 포함하여 CMPivot에 대한 일반 정보를 표시합니다.  

4. **쿼리** 탭은 쿼리 창, 결과 창 및 상태 표시줄을 표시합니다. 위의 스크린샷 예제에서 쿼리 탭이 선택됩니다.  

5. 쿼리 창은 컬렉션의 클라이언트에서 실행할 쿼리를 작성하거나 입력하는 위치입니다.  

    - CMPivot은 [KQL(Kusto 쿼리 언어)](https://docs.microsoft.com/azure/kusto/query/) 일부를 사용합니다.  

    - 쿼리 창에서 콘텐츠를 잘라내기, 복사 또는 붙여넣습니다.  
    <!-- markdownlint-disable MD038 -->
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

   - 디바이스 이름을 마우스 오른쪽 단추로 클릭하여 디바이스에서 다음 추가 작업을 수행합니다.  

      - **피벗 대상**: 이 디바이스에서 다른 엔터티에 대해 쿼리합니다.  

      - **스크립트 실행**: 스크립트 실행 마법사를 시작하여 이 디바이스에서 기존 PowerShell 스크립트를 실행합니다. 자세한 내용은 [스크립트 실행](/sccm/apps/deploy-use/create-deploy-scripts#run-a-script)을 참조하세요.  

      - **원격 제어**: 이 디바이스에서 Configuration Manager 원격 제어 세션을 시작합니다. 자세한 내용은 [Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법](/sccm/core/clients/manage/remote-control/remotely-administer-a-windows-client-computer)을 참조하세요.  

      - **리소스 탐색기**: 이 디바이스에 대해 Configuration Manager 리소스 탐색기를 시작합니다. 자세한 내용은 [하드웨어 인벤토리 보기](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory) 또는 [소프트웨어 인벤토리 보기](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory)를 참조하세요.  

   - 비 디바이스 셸을 마우스 오른쪽 단추로 클릭하여 다음 추가 작업을 수행합니다.  

     - **복사**: 셀의 텍스트를 클립보드에 복사합니다.  

     - **다음과 함께 디바이스 표시**: 이 속성의 값을 포함하여 디바이스에 대해 쿼리합니다. 예를 들어 `OS` 쿼리의 결과에서, 버전 행의 셀에서 이 옵션을 선택합니다. `OS | summarize countif( (Version == '10.0.17134') ) by Device | where (countif_ > 0)`  

     - **다음 없이 디바이스 표시**: 이 속성의 값 없이 디바이스에 대해 쿼리합니다. 예를 들어 `OS` 쿼리의 결과에서, 버전 행의 셀에서 이 옵션을 선택합니다. `OS | summarize countif( (Version == '10.0.17134') ) by Device | where (countif_ == 0) | project Device`  

     - **Bing으로 검색**: 쿼리 문자열로 이 값을 사용하여 https://www.bing.com 에 대한 기본 웹 브라우저를 시작합니다.  

   - 하이퍼링크 텍스트를 클릭하여 해당 특정 정보에서 보기를 피벗합니다.  

   - 결과 창은 20,000개를 초과하는 행을 표시하지 않습니다. 데이터를 추가 필터링하도록 쿼리를 조정하거나 더 작은 컬렉션에서 CMPivot을 다시 시작합니다.  

7. 상태 표시줄은 다음 정보를 표시합니다(왼쪽에서 오른쪽으로).  

   - 대상 컬렉션에 대한 현재 쿼리의 상태 이 상태는 다음을 포함합니다.  
     - 쿼리를 완료한 활성 클라이언트 수(3)  
     - 총 클라이언트 수(5)  
     - 오프라인 클라이언트 수(2)  
     - 오류를 반환한 모든 클라이언트(0)  

       `Query completed on 3 of 5 clients (2 clients offline and 0 failure)`  

   - 클라이언트 작업의 ID입니다. `id(16780221)`  

   - 현재 컬렉션입니다. `PM_Team_Machines`  

   - 결과 창에서 행의 총 수입니다. 예, `1 objects`  



## <a name="example-scenarios"></a>예제 시나리오

다음 섹션에서는 사용자의 환경에서 CMPivot을 사용하는 방법의 예제를 제공합니다.


### <a name="example-1-stop-a-running-service"></a>예제 1: 실행 중인 서비스 중지

보안 관리자는 회계 부서의 모든 디바이스에서 가능한 빨리 컴퓨터 브라우저 서비스를 중지하고 비활성화하도록 요청합니다. 회계 부서의 모든 디바이스에 대한 컬렉션에서 CMPivot을 시작하고, **서비스** 엔터티에서 **모두 쿼리**를 선택합니다. 

`Service`

결과가 표시되면 **이름** 열을 마우스 오른쪽 단추로 클릭하고 **그룹화 기준**을 선택합니다. 

`Service | summarize dcount( Device ) by Name`

**브라우저** 서비스에 대한 행에서 **dcount_** 열의 하이퍼링크된 숫자를 클릭합니다. 

`Service | where (Name == 'Browser') | summarize count() by Device`

모든 디바이스를 다중 선택하고, 선택 영역을 마우스 오른쪽 단추로 클릭하고, **스크립트 실행**을 선택합니다. 이 작업은 서비스를 중지하고 비활성화하기 위해 기존 스크립트를 실행하는 스크립트 실행 마법사를 시작합니다. CMPivot을 사용하여 스크립트 실행 마법사에서 결과를 보고 모든 활성 컴퓨터에 대한 보안 인시던트에 신속하게 응답합니다. 그런 다음, 구성 기준을 만들도록 후속 조치하여 컬렉션에서 다른 컴퓨터를 수정합니다. 나중에 활성화되기 때문입니다. 

![브라우저 서비스 및 스크립트 실행 작업에 대한 CMPivot 예제](media/cmpivot-example1.png)


### <a name="example-2-proactively-resolve-application-failures"></a>예제 2: 애플리케이션 오류 사전 해결  

작업 유지 관리를 사용하여 사전 대응하려면 일주일에 한 번 관리하는 서버의 컬렉션에 대해 CMPivot을 실행하고, **AppCrash** 엔터티에서 **모두 쿼리**를 선택합니다. **FileName** 열을 마우스 오른쪽 단추로 클릭하고 **오름차순 정렬**을 선택합니다. 하나의 디바이스는 매일 약 03:00의 타임스탬프로 sqlsqm.exe에 대한 7개의 결과를 반환합니다. 행 중 하나에서 파일 이름을 선택하고, 마우스 오른쪽 단추로 선택하고 **Bing으로 검색**을 선택합니다. 웹 브라우저에서 검색 결과를 검색하여 이 문제에 대한 더 많은 정보 및 해결이 있는 Microsoft 지원 문서를 찾습니다. 


### <a name="example-3-bios-version"></a>예제 3: BIOS 버전

[잘못된 실행 부채널 취약성을 완화](https://techcommunity.microsoft.com/t5/configuration-manager-blog/additional-guidance-to-mitigate-speculative-execution-side/ba-p/274974)하기 위해 요구 사항 중 하나는 시스템 BIOS를 업데이트하는 것입니다. **BIOS** 엔터티에 대한 쿼리를 시작합니다. 그런 다음, **버전** 속성별로 **그룹화**합니다. 그런 다음, "LENOVO - 1140"과 같은 특정 값을 마우스 오른쪽 단추로 클릭하고 **다음과 함께 디바이스 표시**를 선택합니다.  

`Bios | summarize countif( (Version == 'LENOVO - 1140') ) by Device | where (countif_ > 0)`


### <a name="example-4-free-disk-space"></a>예제 4: 사용 가능한 디스크 공간

네트워크 파일 서버에 큰 파일을 일시적으로 저장해야 하지만 어떤 파일 서버에 충분한 용량이 있는지 확실하지 않습니다. 파일 서버의 컬렉션에 대해 CMPivot을 시작하고, **디스크** 엔터티를 쿼리합니다. CMPivot에 대한 쿼리를 수정하여 실시간 스토리지 데이터로 활성 서버의 목록을 신속하게 반환합니다.  

`Disk | where (Description == 'Local Fixed Disk') | where isnotnull( FreeSpace ) | order by FreeSpace asc`


## <a name="bkmk_cmpivot"></a> 1810 버전부터 CMPivot
<!--1359068, 3607759-->

Configuration Manager 버전 1810부터 CMPivot에는 다음과 같은 개선 사항이 포함됩니다.

- [CMPivot 유틸리티 및 성능](#bkmk_cmpivot-perf)
- [스칼라 함수](#bkmk_cmpivot-functions)  
- [렌더링 시각화](#bkmk_cmpivot-charts)  
- [하드웨어 인벤토리](#bkmk_cmpivot-hinv)  
- [스칼라 연산자](#bkmk_cmpivot-operators)  
- [쿼리 요약](#bkmk_cmpivot-summary)  
- [감사 상태 메시지](#cmpivot-audit-status-messages)

### <a name="bkmk_cmpivot-perf"></a> CMPivot 유틸리티 및 성능

- CMPivot은 20,000개 행이 아닌 100,000개 셀까지 반환합니다.
  - 엔터티에 5개 열을 의미하는 5개의 속성이 있으면 최대 20,000개 행이 표시됩니다.
  - 10개의 속성을 포함하는 엔터티의 경우 최대 10,000개 행이 표시됩니다.
  - 표시되는 전체 데이터는 100,000개 셀 이하입니다.
- 쿼리 요약 탭에서 실패 또는 오프라인 디바이스 수를 선택한 다음, **컬렉션 만들기** 옵션을 선택합니다. 이 옵션을 사용하면 해당 디바이스에 수정 배포를 쉽게 수행할 수 있습니다.
- 폴더 아이콘을 클릭하여 **즐겨 찾는** 쿼리를 저장합니다.
   ![CMPivot에서 즐겨 찾는 쿼리를 저장하는 예제](media/cmpivot-favorite.png)

- 1810 버전으로 업데이트된 클라이언트는 고속 통신 채널을 통해 사이트에 80KB 미만의 출력을 반환합니다.
  - 이러한 변경으로 인해 스크립트 또는 쿼리 출력 표시 성능이 개선됩니다.
  - 스크립트 또는 쿼리 출력이 80KB보다 큰 경우 클라이언트는 상태 메시지를 통해 데이터를 보냅니다.
  - 클라이언트를 1810 버전으로 업데이트하지 않으면 계속해서 상태 메시지를 표시합니다.

- CMPivot을 시작할 때 다음과 같은 오류가 표시될 수 있습니다.  **호환되지 않는 스크립트 버전 때문에 현재 CMPivot을 사용할 수 없습니다. 계층 구조가 사이트를 업그레이드 하는 중이므로 이 문제가 발생할 수 있습니다. 업그레이드가 완료될 때까지 기다렸다가 다시 시도합니다.**

  - 이 메시지가 표시되면 다음과 같은 의미일 수 있습니다.
    - 보안 범위가 제대로 설정되지 않았습니다.
    - 프로세스에서 업그레이드에 대한 문제가 발생했습니다.
    - 기본 CMPivot 스크립트가 호환되지 않습니다.


### <a name="bkmk_cmpivot-functions"></a> 스칼라 함수
CMPivot에서는 다음 스칼라 함수를 지원합니다.
- **ago()** : 현재 UTC 시계 시간에서 지정된 시간 범위를 뺍니다.  
- **datetime_diff()** : 두 날짜/시간 값 사이에 달력 차이를 계산합니다.  
- **now()** : 현재 UTC 시계 시간을 반환합니다.  
- **bin()** : 값을 지정된 bin 크기의 정수 배수로 내림합니다.  

> [!Note]  
> 날짜/시간 데이터 형식은 인스턴트를 시간으로 나타내며, 일반적으로 하루의 날짜와 시간으로 표현됩니다. 시간 값은 1초 단위로 측정됩니다. 날짜/시간 값은 항상 UTC 표준 시간대입니다. 날짜 시간 리터럴을 항상 ISO 8601 형식으로 표현합니다(예: `yyyy-mm-dd HH:MM:ss`)  

#### <a name="examples"></a>예
- `datetime(2015-12-31 23:59:59.9)`: 특정 날짜 시간 리터럴   
- `now()`: 현재 시간  
- `ago(1d)`: 현재 시간의 하루 이전  


### <a name="bkmk_cmpivot-charts"></a>렌더링 시각화

CMPivot에는 이제 KQL [렌더링 연산자](https://docs.microsoft.com/azure/kusto/query/renderoperator)에 대한 기본 지원이 포함됩니다. 이 지원은 다음과 같습니다.  
- **barchart**: 첫 번째 열은 x축이며, 텍스트, 날짜/시간 또는 숫자일 수 있습니다. 두 번째 열은 숫자여야 하고 가로 줄무늬로 표시됩니다.  
- **columnchart**: barchart와 같이 가로 스트립 대신 세로 줄무늬를 사용합니다.  
- **piechart**: 첫 번째 열은 색깔 축이고 두 번째 열은 숫자입니다.  
- **timechart**: 선 그래프입니다. 첫 번째 열은 x축이며 날짜/시간이어야 합니다. 두 번째 열은 y축입니다.  

#### <a name="example-bar-chart"></a>예제: 가로 막대형 차트
다음 쿼리에서는 가장 최근에 사용된 애플리케이션을 가로 막대형 차트로 렌더링합니다.

``` Kusto
CCMRecentlyUsedApplications
| summarize dcount( Device ) by ProductName
| top 10 by dcount_
| render barchart
```

![CMPivot 가로 막대형 차트 시각화 예제](media/1359068-cmpivot-barchart.png)

#### <a name="example-time-chart"></a>예제: 시간 차트
시간 차트를 렌더링하려면 새 **bin()** 연산자를 사용하여 시간에서 이벤트를 그룹화합니다. 다음 쿼리에서는 최근 7일 동안 디바이스가 시작된 시기를 보여줍니다.

``` Kusto
OperatingSystem
| where LastBootUpTime <= ago(7d)
| summarize count() by bin(LastBootUpTime,1d)
| render timechart
```

![CMPivot 시간 차트 시각화 예제](media/1359068-cmpivot-timechart.png)

#### <a name="example-pie-chart"></a>예제: 원형 차트
다음 쿼리에서는 원형 차트의 모든 OS 버전을 보여줍니다.

``` Kusto
OperatingSystem
| summarize count() by Caption
| render piechart
```

![CMPivot 원형 차트 시각화 예제](media/1359068-cmpivot-piechart.png)


### <a name="bkmk_cmpivot-hinv"></a>하드웨어 인벤토리
CMPivot을 사용하여 모든 하드웨어 인벤토리 클래스를 쿼리합니다. 이러한 클래스에는 하드웨어 인벤토리에 대한 모든 사용자 지정 확장이 포함됩니다. CMPivot은 사이트 데이터베이스에 저장된 최신 하드웨어 인벤토리 검사에서 캐시된 결과를 즉시 반환합니다. 동시에 필요한 경우 온라인 클라이언트의 라이브 데이터로 결과를 업데이트합니다.

결과 테이블 또는 차트의 데이터 색 채도는 라이브 데이터인지 캐시된 데이터인지를 나타냅니다. 예를 들어, 진한 파랑은 온라인 클라이언트의 실시간 데이터입니다. 연한 파랑은 캐시된 데이터입니다.

#### <a name="example"></a>예제

``` Kusto
LogicalDisk
| summarize sum( FreeSpace ) by Device
| order by sum_ desc
| render columnchart
```

![세로 막대형 차트 시각화를 사용한 CMPivot 인벤토리 쿼리 예제](media/1359068-cmpivot-inventory.png)

#### <a name="limitations"></a>제한 사항
- 다음 하드웨어 인벤토리 엔터티가 지원되지 않습니다.  
    - 배열 속성(예: IP 주소)  
    - Real32/Real64 <!--example?-->  
    - 포함된 개체 속성 <!--example?-->  
- 인벤토리 엔터티 이름은 문자로 시작해야 합니다.
- 이름이 같은 인벤토리 엔터티를 만들어 기본 제공 엔터티를 덮어쓸 수 없습니다.  


### <a name="bkmk_cmpivot-operators"></a>스칼라 연산자
CMPivot에는 다음 스칼라 연산자가 포함됩니다.  

> [!Note]  
> - LHS: 연산자의 왼쪽에 대한 문자열  
> - RHS: 연산자의 오른쪽에 대한 문자열  


|연산자|설명|예제(true 발생)|
|--------|-----------|---------------------|
|==|같음|`"aBc" == "aBc"`|
|!=|같지 않음|`"abc" != "ABC"`|
|like|LHS가 RHS에 대한 일치 항목을 포함함|`"FabriKam" like "%Brik%"`|
|!like|LHS가 RHS에 대한 일치 항목을 포함하지 않음|`"Fabrikam" !like "%xyz%"`|
|포함|RHS가 LHS의 하위 시퀀스로 발생함|`"FabriKam" contains "BRik"`|
|!contains|RHS가 LHS에서 발생하지 않음|`"Fabrikam" !contains "xyz"`|
|startswith|RHS가 LHS의 초기 하위 시퀀스임|`"Fabrikam" startswith "fab"`|
|!startswith|RHS가 LHS의 초기 하위 시퀀스가 아님|`"Fabrikam" !startswith "kam"`|
|endswith|RHS가 LHS의 닫는 하위 시퀀스임|`"Fabrikam" endswith "Kam"`|
|!endswith|RHS가 LHS의 닫는 하위 시퀀스가 아님|`"Fabrikam" !endswith "brik"`|


### <a name="bkmk_cmpivot-summary"></a>쿼리 요약

CMPivot 창의 아래쪽에 있는 **쿼리 요약** 탭을 선택합니다. 이 상태를 통해 오프라인 상태인 클라이언트를 식별하거나 오류가 발생할 수 있는 문제를 해결하는 데 도움이 됩니다. 개수 열에서 값을 선택하여 해당 상태인 특정 디바이스 목록을 엽니다. 

예를 들어, 오류 상태인 디바이스 개수를 선택합니다. 특정 오류 메시지가 표시되고 이러한 디바이스 목록을 내보냅니다. 특정 cmdlet을 인식하지 못하는 오류가 발생한 경우 내보낸 디바이스 목록에서 컬렉션을 만들어서 Windows PowerShell 업데이트를 배포합니다.  

### <a name="cmpivot-audit-status-messages"></a>CMPivot 감사 상태 메시지

1810 버전부터는 CMPivot를 실행하는 경우 **MessageID 40805**로 감사 상태 메시지를 생성합니다. **모니터링** > **시스템 상태** > **상태 메시지 쿼리**로 이동하여 상태 메시지를 볼 수 있습니다. **특정 사용자에 대한 모든 감사 상태 메시지**, **특정 사이트에 대한 모든 감사 상태 메시지**를 실행하거나 고유의 상태 메시지 쿼리를 만들 수 있습니다.

메시지에 대해 다음 형식을 사용합니다.

MessageId 40805: &lt;UserName> 사용자는 &lt;Collection-ID> 컬렉션에서 &lt;Script-Hash> 해시를 포함한 &lt;Script-Guid> 스크립트를 실행했습니다.

- 7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14는 CMPivot에 대한 Script-Guid입니다.
- Script-Hash는 클라이언트의 scripts.log 파일에서 확인할 수 있습니다.
- 클라이언트의 스크립트 저장소에 저장된 해시를 확인할 수도 있습니다. 클라이언트의 파일 이름은 &lt;Script-Guid>_&lt;Script-Hash>입니다.
    - 예제 파일 이름: C:\Windows\CCM\ScriptStore\7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14_abc1d23e45678901fabc123d456ce789fa1b2cd3e456789123fab4c56789d0123.ps
   

![CMPivot 감사 상태 메시지 샘플](media/cmpivot-audit-status-message.png)

## <a name="bkmk_cmpivot1902"></a> 1902 버전부터 CMPivot
<!--3610960-->
Configuration Manager 버전 1902부터는 계층 구조의 CAS(중앙 관리 사이트)에서 CMPivot을 실행할 수 있습니다. 기본 사이트는 계속 클라이언트 통신을 처리합니다. 중앙 관리 사이트에서 CMPivot을 실행하는 경우 고속 메시지 구독 채널을 통해 기본 사이트와 통신합니다. 이 통신은 사이트 간 표준 SQL 복제를 따르지 않습니다.

CAS에서 CMPivot을 실행하려면 SQL 또는 공급자가 동일한 머신에 있지 않거나 SQL Always On 구성인 경우 추가 사용 권한이 필요합니다. 이러한 원격 구성을 사용하면 CMPivot에 대해 "더블 홉 시나리오"가 있습니다.

이러한 "더블 홉 시나리오"의 경우 CMPivot를 CAS에서 작동하도록 하기 위해 제한된 위임을 정의할 수 있습니다. 이 구성의 보안 의미를 이해하려면 [Kerberos 제한 위임](https://docs.microsoft.com/windows-server/security/kerberos/kerberos-constrained-delegation-overview) 문서를 참고하세요. CAS와 함께 배치된 SQL 또는 SMS 공급자와 같은 원격 구성이 둘 이상 있는 경우 조합된 권한 설정이 필요합니다. 수행해야 하는 단계는 다음과 같습니다.

### <a name="cas-has-a-remote-sql-server"></a>CAS에 원격 SQL Server 포함

1. 각 기본 사이트의 SQL Server로 이동합니다.
   1. CAS 원격 SQL Server 및 CAS 사이트 서버를 [Configmgr_DviewAccess](/sccm/core/plan-design/hierarchy/accounts#configmgr_dviewaccess) 그룹에 추가합니다.
   ![기본 사이트의 SQL Server에서 Configmgr_DviewAccess 그룹](media/cmpivot-dviewaccess-group.png)
1. Active Directory 사용자 및 컴퓨터로 이동합니다.
   1. 각 기본 사이트 서버에서 **속성**을 마우스 오른쪽 단추로 클릭하고 선택합니다.
      1. 위임 탭에서 세 번째 옵션인 **지정된 서비스에 대한 위임용으로만 이 컴퓨터 트러스트**를 선택합니다. 
      1. **Kerberos 사용 전용**을 선택합니다.
      1. 포트와 인스턴스를 포함한 CAS의 SQL Server 서비스를 추가합니다.
      1. 이러한 변경 내용은 회사 보안 정책을 준수해야 합니다.
   1. CAS 사이트에서 **속성**을 마우스 오른쪽 단추로 클릭하고 선택합니다.
      1. 위임 탭에서 세 번째 옵션인 **지정된 서비스에 대한 위임용으로만 이 컴퓨터 트러스트**를 선택합니다. 
      1. **Kerberos 사용 전용**을 선택합니다.
      1. 포트와 인스턴스를 포함한 기본 사이트의 SQL Server 서비스를 추가합니다.
      1. 이러한 변경 내용은 회사 보안 정책을 준수해야 합니다.

   ![더블 홉에 대한 CMPivot AD 위임 예제](media/cmpivot-ad-delegation.png)

### <a name="cas-has-a-remote-provider"></a>CAS에 원격 공급자 포함

1. 각 기본 사이트의 SQL Server로 이동합니다.
   1. CAS 공급자 머신 계정 및 CAS 사이트 서버를 [Configmgr_DviewAccess](/sccm/core/plan-design/hierarchy/accounts#configmgr_dviewaccess) 그룹에 추가합니다.
1. Active Directory 사용자 및 컴퓨터로 이동합니다.
   1. CAS 공급자 머신을 선택하고, **속성**을 마우스 오른쪽 단추로 클릭하고 선택합니다.
      1. 위임 탭에서 세 번째 옵션인 **지정된 서비스에 대한 위임용으로만 이 컴퓨터 트러스트**를 선택합니다. 
      1. **Kerberos 사용 전용**을 선택합니다.
      1. 포트와 인스턴스를 포함한 기본 사이트의 SQL Server 서비스를 추가합니다.
      1. 이러한 변경 내용은 회사 보안 정책을 준수해야 합니다.
   1. CAS 사이트 서버를 선택하고, **속성**을 마우스 오른쪽 단추로 클릭하고 선택합니다.
      1. 위임 탭에서 세 번째 옵션인 **지정된 서비스에 대한 위임용으로만 이 컴퓨터 트러스트**를 선택합니다. 
      1. **Kerberos 사용 전용**을 선택합니다.
      1. 포트와 인스턴스를 포함한 기본 사이트의 SQL Server 서비스를 추가합니다.
      1. 이러한 변경 내용은 회사 보안 정책을 준수해야 합니다.
1. CAS 원격 공급자 머신을 다시 시작합니다.

### <a name="sql-always-on"></a>SQL Always On

1. 각 기본 사이트의 SQL Server로 이동합니다.
   1. CAS 사이트 서버를 [Configmgr_DviewAccess](/sccm/core/plan-design/hierarchy/accounts#configmgr_dviewaccess) 그룹에 추가합니다.
1. Active Directory 사용자 및 컴퓨터로 이동합니다.
   1. 각 기본 사이트 서버에서 **속성**을 마우스 오른쪽 단추로 클릭하고 선택합니다.
      1. 위임 탭에서 세 번째 옵션인 **지정된 서비스에 대한 위임용으로만 이 컴퓨터 트러스트**를 선택합니다. 
      1. **Kerberos 사용 전용**을 선택합니다.
      1. 포트와 인스턴스를 포함한 SQL 노드에 대한 CAS의 SQL Server 서비스 계정을 추가합니다.
      1. 이러한 변경 내용은 회사 보안 정책을 준수해야 합니다.
   1. CAS 사이트 서버를 선택하고, **속성**을 마우스 오른쪽 단추로 클릭하고 선택합니다.
      1. 위임 탭에서 세 번째 옵션인 **지정된 서비스에 대한 위임용으로만 이 컴퓨터 트러스트**를 선택합니다. 
      1. **Kerberos 사용 전용**을 선택합니다.
      1. 포트와 인스턴스를 포함한 기본 사이트의 SQL Server 서비스를 추가합니다.
      1. 이러한 변경 내용은 회사 보안 정책을 준수해야 합니다.
1. CAS SQL 수신기 이름 및 각 기본 SQL 수신기 이름에 대해 [SPN이 게시](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/listeners-client-connectivity-application-failover?view=sql-server-2017#SPNs)되었는지 확인합니다.
1. 기본 SQL server를 다시 시작합니다.
1. CAS 사이트 서버 및 CAS SQL Server를 다시 시작합니다.

## <a name="bkmk_cmpivot1906"></a> 버전 1906부터의 CMPivot

버전 1906부터 다음 항목이 CMPivot에 추가되었습니다.

- [조인, 추가 연산자, 집계](#bkmk_cmpivot_joins)
- [보안 관리자 역할에 CMPivot 권한 추가](#bkmk_cmpivot_secadmin1906)
- [CMPivot 독립 실행형](#bkmk_standalone)이 **시험판 기능으로 추가되었습니다**

### <a name="bkmk_cmpivot_joins"></a> CMPivot에서 조인, 추가 연산자 및 집계 추가
<!--4054074-->
이제 추가 산술 연산자와 집계뿐 아니라 레지스트리와 파일을 함께 사용하는 것과 같이 쿼리 조인을 추가하는 기능이 생겼습니다. 다음 항목이 추가되었습니다.

#### <a name="table-operators"></a>테이블 연산자

|테이블 연산자| 설명|
|-----|-----|
| [조인](https://docs.microsoft.com/azure/kusto/query/joinoperator)| 두 테이블의 행을 병합하고 동일한 디바이스의 행을 매칭하는 방법으로 새 테이블을 만듭니다.|
|렌더|결과를 그래픽 출력으로 렌더링합니다.|

렌더링 연산자는 CMPivot에 이미 있습니다. 여러 시리즈와 **with** 문에 대한 지원이 추가되었습니다. 자세한 내용은 [예제](#bkmk_cmpivot_examples1906) 섹션과 Kusto의 [조인 연산자](https://docs.microsoft.com/azure/kusto/query/joinoperator) 문서를 참조하세요.

#### <a name="limitations-for-joins"></a>조인의 제한 사항

1. 조인 열은 항상 **디바이스** 필드에서 암시적으로 수행됩니다.
1. 쿼리마다 조인을 5개까지 사용할 수 있습니다.
1. 최대 64개까지 열을 결합할 수 있습니다.

#### <a name="scalar-operators"></a>스칼라 연산자

|연산자| 설명|예제|
|-----|-----|-----|
| + | 추가| `2 + 1, now() + 1d`|
| - |  빼기| `2 - 1, now() - 1d`|
| * | 곱하기| `2 * 2`|
| / | 나누기 | `2 / 1`|
| % | 나머지값 | `2 % 1`

#### <a name="aggregation-functions"></a>집계 함수

|함수| 설명|
|-----|-----|
| percentile()| Expr로 정의한 모집단에 대해 지정된 가장 가까운 백분위수의 추정치를 반환합니다.|
| sumif() | 조건자가 true로 평가되는 Expr의 합계를 반환합니다.|

#### <a name="scalar-functions"></a>스칼라 함수

|함수| 설명|
|-----|-----|
| case()| 조건자 목록을 평가하여 조건자를 충족하는 첫 번째 결과 식을 반환합니다. |
| iff() | 첫 번째 인수를 평가하고 조건자가 true로 평가되는지(두 번째) 아니면 false(세 번째)로 평가되는지 여부에 따라 두 번째 또는 세 번째 인수의 값을 반환합니다.|
 | indexof() | 이 함수는 입력 문자열 내에서 발견된 첫 번째 지정된 문자열의 0부터 시작하는 인덱스를 보고합니다.|
| strcat() | 1~64 사이의 인수를 연결합니다. |
| strlen()| 입력 문자열의 길이(문자 수)를 반환합니다.|
| substring() | 원본 문자열의 어떤 인덱스부터 문자열 끝까지 하위 문자열을 추출합니다. |
| tostring() | 입력을 문자열 작업으로 변환합니다. |

#### <a name="bkmk_cmpivot_examples1906"></a> 예제

- 디바이스, 제조업체, 모델 및 OSVersion 표시:

   ``` Kusto
   ComputerSystem
   | project Device, Manufacturer, Model
   | join (OperatingSystem | project Device, OSVersion=Caption)
   ```

- 디바이스의 부팅 시간 그래프 표시:

   ``` Kusto
   SystemBootData
   | where Device == 'MyDevice'
   | project SystemStartTime, BootDuration, OSStart=EventLogStart, GPDuration, UpdateDuration
   | order by SystemStartTime desc
   | render barchart with (kind=stacked, title='Boot times for MyDevice', ytitle='Time (ms)')
   ```

   ![디바이스의 부팅 시간을 밀리초 단위로 보여주는 누적 가로 막대형 차트](./media/4054074-render-using-with-statement.png)

### <a name="bkmk_cmpivot_secadmin1906"></a> 보안 관리자 역할에 CMPivot 권한 추가
<!--4683130-->

버전 1906부터 다음 권한이 Configuration Manager의 기본 제공 **보안 관리자** 역할에 추가되었습니다.

 - SMS 스크립트 **읽기**
 - 컬렉션에서 **CMPivot 실행**
 - 인벤토리 보고서 **읽기**

>[!NOTE]
> **스크립트 실행**은 **CMPivot 실행** 권한의 상위 집합입니다.
 

### <a name="bkmk_standalone"></a> CMPivot 독립 실행형
<!--3555890, 4619340, 4683130 -->

버전 1906부터 CMPivot을 독립 실행형 앱으로 사용할 수 있습니다. CMPivot 독립 실행형은 [시험판 기능](/sccm/core/servers/manage/pre-release-features#bkmk_table)이며 영어로만 제공됩니다. Configuration Manager 콘솔 외부에서 CMPivot을 실행하여 사용자 환경에 포함된 디바이스의 실시간 상태를 확인할 수 있습니다. 이 변경을 통해 먼저 콘솔을 설치하지 않고도 디바이스에서 CMPivot을 사용할 수 있습니다.

컴퓨터에 콘솔을 설치하지 않은 기술 지원팀 또는 보안 관리자 등의 가상 사용자와 CMPivot 기능을 공유할 수 있습니다. 이러한 다른 가상 사용자는 일반적으로 사용하는 다른 도구와 함께 CMPivot을 사용하여 Configuration Manager를 쿼리할 수 있습니다. 이 풍부한 관리 데이터를 공유하면서 공조하여 여러 역할에서 나타나는 비즈니스 문제를 사전에 해결할 수 있습니다.

#### <a name="install-cmpivot-standalone"></a>CMPivot 독립 실행형 설치

1. CMPivot을 실행하는 데 필요한 사용 권한을 설정합니다. 자세한 내용은 [필수 구성 요소](#prerequisites)를 참조하세요. 권한이 사용자에게 적절한 경우 [보안 관리자 역할](#bkmk_cmpivot_secadmin1906)을 사용할 수도 있습니다.
2. `<site install path>\tools\CMPivot\CMPivot.msi` 경로에서 CMPivot 앱 설치 프로그램을 찾습니다. 이 경로에서 설치 프로그램을 실행하거나 다른 위치로 복사할 수 있습니다.
3. CMPivot 독립 실행형 앱을 실행하면 사이트에 연결하라는 메시지가 표시됩니다. 중앙 관리 또는 기본 사이트 서버의 정규화된 도메인 이름이나 컴퓨터 이름을 지정합니다.
   - CMPivot 독립 실행형을 열 때마다 사이트 서버에 연결하라는 메시지가 표시됩니다.
4. CMPivot을 실행하려는 컬렉션을 찾은 다음 쿼리를 실행합니다.

   ![쿼리를 실행하려는 컬렉션 찾기](./media/3555890-cmpivot-standalone-browse-collection.png)

> [!NOTE]
> 독립 실행형 CMPivot에서는 **스크립트 실행**, **리소스 탐색기**, 웹 검색과 같은 마우스 오른쪽 단추 동작을 사용할 수 없습니다. 독립 실행형 CMPivot의 주된 용도는 Configuration Manager 인프라에 대해 독립적으로 쿼리하는 것입니다. 보안 관리자에게 도움이 되도록, 독립 실행형 CMpivot에는 Microsoft Defender Security Center에 연결하는 기능이 포함되어 있습니다. <!--5605358-->

## <a name="bkmk_cmpivot1910"></a> 버전 1910부터 CMPivot
<!--5410930, 3197353-->
버전 1910부터, CMPivot이 서버의 네트워크 트래픽과 부하를 줄이도록 크게 최적화되었습니다. 이에 더해, 문제 해결 및 헌팅을 지원하기 위해 여러 가지 새로운 엔터티 및 향상된 엔터티 기능이 추가되었습니다. 버전 1910에서 CMPivot에 적용된 변경 사항은 다음과 같습니다.

- [CMPivot 엔진에 대한 최적화](#bkmk_optimization)
- 추가 엔터티 및 향상된 엔터티 기능:
  - Windows 이벤트 로그([WinEvent](#bkmk_WinEvent))
  - 파일 콘텐츠([FileContent](#bkmk_File))
  - 프로세스에 의해 로드된 dll([ProcessModule](#bkmk_ProcessModule))
  - Azure Active Directory 정보([AADStatus](#bkmk_AadStatus))
  - Endpoint Protection 상태([EPStatus](#bkmk_EPStatus))
- [CMPivot 독립 실행형을 사용하는 로컬 디바이스 쿼리 평가](#bkmk_local-eval)
- [그 밖의 향상된 CMPivot 기능](#bkmk_Other)


### <a name="bkmk_optimization"></a> CMPivot 엔진 최적화
<!--3197353-->
1910에서는 서버의 네트워크 트래픽과 부하를 줄이도록 CMPivot이 최적화되었습니다. 이제 다수의 쿼리 작업이 서버가 아닌 클라이언트에서 직접 실행됩니다. 이로 인해 일부 CMPivot 작업은 첫 번째 쿼리로부터 적은 양의 데이터를 반환하게 될 수 있습니다. 자세히 알아보기 위해 데이터를 드릴다운할 경우 클라이언트에서 데이터를 가져오기 위한 새 쿼리가 실행될 수 있습니다. 예를 들어, 이전에는 “summarized count”(개수 요약) 쿼리를 실행할 때 서버에서 다량의 데이터 세트가 반환되었습니다.  다량의 데이터 세트가 반환되면 즉각적인 드릴다운이 가능하긴 했으나, 단지 개수 요약만 필요한 경우가 많았습니다. 1910에서는, 특정 클라이언트를 드릴다운할 경우 사용자가 요청한 추가 데이터를 반환하기 위해 또 다른 데이터 모음이 발생합니다. 이번 변경 사항으로 인해 다수의 클라이언트에 대한 쿼리의 성능과 확장성이 향상됩니다. <!--3197353, 5458337-->

#### <a name="examples"></a>예

CMPivot 최적화는 CMPivot 쿼리를 실행하는 데 필요한 네트워크 및 서버 CPU 부하를 크게 줄여 줍니다. 이러한 최적화를 통해 이제 클라이언트 데이터(기가바이트)를 실시간으로 자세히 살펴볼 수 있습니다. 다음은 이러한 최적화를 보여 주는 쿼리입니다.

- 엔터프라이즈의 모든 클라이언트에서 모든 이벤트 로그를 검색하여 인증 실패를 찾습니다.

   ``` Kusto
   EventLog('Security')
   | where  EventID == 4673
   | summarize count() by Device
   | order by count_ desc
   ```

- 해시로 파일을 검색합니다.

   ``` Kusto
   Device
   | join kind=leftouter ( File('%windir%\\system32\\*.exe')
   | where SHA256Hash == 'A92056D772260B39A876D01552496B2F8B4610A0B1E084952FE1176784E2CE77')
   | project Device, MalwareFound = iif( isnull(FileName), 'No', 'Yes')
   ```

### <a name="bkmk_WinEvent"></a> WinEvent(\<logname>,[\<timespan>])

이 엔터티는 이벤트 로그 및 이벤트 추적 로그 파일에서 이벤트를 가져오는 데 사용됩니다. 엔터티는 Windows 이벤트 로그 기술에 의해 생성되는 이벤트 로그에서 데이터를 가져옵니다. 또한 엔터티는 ETW(Windows용 이벤트 추적)에 의해 생성된 로그 파일에서 이벤트를 가져옵니다. WinEvent는 기본적으로 지난 24시간 이내에 발생한 이벤트를 확인합니다. 그러나 24시간 기본값은 시간 범위을 포함하는 방식으로 재정의할 수 있습니다.

``` Kusto
WinEvent('Microsoft-Windows-HelloForBusiness/Operational', 1d)
| where LevelDisplayName =='Error'
| summarize count() by Device
```

### <a name="bkmk_File"></a> FileContent(\<filename>)

FileContent는 텍스트 파일의 내용을 가져오는 데 사용됩니다.

``` Kusto
FileContent('c:\\windows\\SMSCFG.ini')
| where Content startswith  'SMS Unique Identifier='
| project Device, SMSId= substring(Content,22)
```

### <a name="bkmk_ProcessModule"></a> ProcessModule(\<processname>)  

이 엔터티는 지정된 프로세스에 의해 로드된 모듈(dll)을 열거하는 데 사용됩니다. ProcessModule은 합법적인 프로세스에서 숨겨진 맬웨어를 헌팅할 때 유용합니다.  

``` Kusto
ProcessModule('powershell')
| summarize count() by ModuleName
| order by count_ desc
```

### <a name="bkmk_AadStatus"></a> AadStatus

이 엔터티를 사용하여 디바이스에서 현재 Azure Active Directory ID 정보를 가져올 수 있습니다.

``` Kusto
AadStatus
| project Device, IsAADJoined=iif( isnull(DeviceId),'No','Yes')
| summarize DeviceCount=count() by IsAADJoined
| render piechart
```

### <a name="bkmk_EPStatus"></a> EPStatus

EPStatus는 컴퓨터에 설치된 맬웨어 방지 소프트웨어의 상태를 가져오는 데 사용됩니다.

``` Kusto
EPStatus
| project Device, QuickScanAge=datetime_diff('day',now(),QuickScanEndTime)
| summarize DeviceCount=count() by QuickScanAge
| order by QuickScanAge
| render barchart
```

### <a name="bkmk_local-eval"></a> 독립 실행형 CMPivot을 사용하는 로컬 디바이스 쿼리 평가
<!--3197353-->
Configuration Manager 콘솔 외부에서 CMPivot을 사용하는 경우 Configuration Manager 인프라를 요구 하지 않고 로컬 디바이스만 쿼리할 수 있습니다. 이제 CMPivot Azure Log Analytics 쿼리를 활용하여 로컬 디바이스에서 WMI 정보를 빠르게 확인할 수 있습니다. 이를 통해 더 큰 환경에서 실행하기 전에 CMPivot 쿼리의 유효성을 검사하고 구체화할 수 있습니다. CMPivot 독립 실행형은 [시험판 기능](/sccm/core/servers/manage/pre-release-features#bkmk_table)이며 영어로만 제공됩니다. CMPivot 독립 실행형을 설치하는 방법에 대한 자세한 내용은 [CMPivot 독립 실행형 설치](#install-cmpivot-standalone)를 참조하세요.

#### <a name="known-issues-for-local-device-query-evaluation"></a>로컬 디바이스 쿼리 평가의 알려진 문제

 - **이 PC**에서 사용자에게 액세스 권한이 없는 WMI 엔터티(예: 잠긴 WMI 클래스)에 대해 쿼리를 실행할 경우 CMPivot에서 크래시가 발생할 수 있습니다. 이러한 엔터티를 쿼리하려면 상승된 권한이 있는 계정을 사용하여 CMPivot을 실행하세요. <!--5753242-->
- **이 PC**에서 WMI가 아닌 엔터티를 쿼리할 경우 **잘못된 네임스페이스** 또는 모호한 예외가 발생합니다.
- 독립 실행형 CMPivot을 실행 파일 경로에서 직접 실행하는 대신 시작 메뉴 바로 가기에서 실행하세요. <!--5787962-->

### <a name="bkmk_Other"></a> 기타 향상된 기능

- 새로운 `like` 연산자를 사용하여 정규식 형식 쿼리를 실행할 수 있습니다. 예를 들면 다음과 같습니다.<!--3056858-->
  
   ```kusto
   //Find BIOS manufacture that contains any word like Micro, such as Microsoft
   Bios
   | where Manufacturer like ‘%Micro%’
   ```

- 기본적으로 최근 24시간 동안의 메시지만 확인하도록 **CcmLog()** 및 **EventLog()** 엔터티를 업데이트했습니다. 선택적 시간 범위를 전달하여 이 동작을 재정의할 수 있습니다. 예를 들어 다음 쿼리는 지난 1시간 동안의 이벤트를 확인합니다.

   ```kusto
   CcmLog('Scripts',1h)
   ```

- **File()** 엔터티가 숨겨진 파일 및 시스템 파일에 대한 정보를 수집하도록 업데이트되었으며 MD5 해시를 포함합니다. MD5 해시는 SHA256 해시만큼 정확한 것은 아니지만 대부분의 맬웨어 공지에서 일반적으로 보고되는 해시입니다.  

- 쿼리에 주석을 추가할 수 있습니다.<!-- 5431463 --> 이 동작은 쿼리를 공유하는 경우에 유용합니다. 예를 들면 다음과 같습니다.

    ``` Kusto
    //Get the top ten devices sorted by user
    Device
    | top 10 by UserName
    ```

- CMPivot은 마지막 사이트에 자동으로 연결합니다.<!-- 5420395 --> CMPivot을 시작한 후 필요한 경우 새 사이트에 연결할 수 있습니다.

- **내보내기** 메뉴에서 **클립보드에 대한 쿼리 링크**로 새로운 옵션을 선택합니다.<!-- 5431577 --> 이 작업을 수행하면 링크가 다른 사용자와 공유할 수 있는 클립보드에 복사됩니다. 예를 들면 다음과 같습니다.

    `cmpivot:Ly8gU2FtcGxlIHF1ZXJ5DQpPcGVyYXRpbmdTeXN0ZW0NCnwgc3VtbWFyaXplIGNvdW50KCkgYnkgQ2FwdGlvbg0KfCBvcmRlciBieSBjb3VudF8gYXNjDQp8IHJlbmRlciBiYXJjaGFydA==`

    이 링크는 다음 쿼리를 사용하여 CMPivot 독립 실행형을 엽니다.

    ``` Kusto
    // Sample query
    OperatingSystem
    | summarize count() by Caption
    | order by count_ asc
    | render barchart
    ```

    > [!TIP]
    > 이 링크를 작동하려면 [CMPivot 독립 실행형을 설치합니다](#install-cmpivot-standalone).

- 장치를 Microsoft Defender ATP(Advanced Threat Protection)에 등록한 경우, 쿼리 결과에서 장치를 마우스 오른쪽 단추로 클릭하여 **Microsoft Defender 보안 센터** 온라인 포털을 시작합니다.

### <a name="known-issues-for-cmpivot-in-version-1910"></a>버전 1910 CMPivot의 알려진 문제

- 제한에 도달한 경우 최대 결과 배너가 표시되지 않을 수 있습니다. <!--5431427-->
  - 각 클라이언트는 쿼리당 128KB의 데이터로 제한됩니다.
  - 쿼리 결과가 128KB를 초과할 경우 결과가 잘릴 수 있습니다.
 
## <a name="inside-cmpivot"></a>내부 CMPivot

CMPivot은 Configuration Manager "빠른 채널"을 사용하여 클라이언트에게 쿼리를 보냅니다. 서버에서 클라이언트로의 이 통신 채널은 클라이언트 알림 작업, 클라이언트 상태 및 엔드포인트 보호와 같은 다른 기능에서도 사용됩니다. 클라이언트는 마찬가지로 빠른 상태 메시지 시스템을 통해 결과를 반환합니다. 상태 메시지는 데이터베이스에 임시로 저장됩니다. 클라이언트 알림에 사용된 포트에 대한 자세한 내용은 [포트](/sccm/core/plan-design/hierarchy/ports#BKMK_PortsClient-MP) 문서를 참조하세요.

쿼리 및 결과는 모두 텍스트입니다. 엔터티 **InstallSoftware** 및 **Process**는 가장 큰 결과 집합의 일부를 반환합니다. 성능 테스트 중에 이러한 쿼리에 대한 하나의 클라이언트에서 가장 큰 상태 메시지 파일 크기는 **1KB**보다 작았습니다. 50,000명의 활성 클라이언트를 사용하여 대규모 환경으로 확장하여 이 일회성 쿼리는 네트워크에서 50MB보다 작은 데이터를 생성합니다. 시작 페이지에서 밑줄이 표시된 모든 항목은 클라이언트당 1K 미만인 정보를 반환합니다.

![CMPivot 밑줄이 표시된 엔터티 예제](media/cmpivot-underlined-entities.png)

Configuration Manager 1810부터 CMPivot은 확장된 하드웨어 인벤토리 클래스를 포함한 하드웨어 인벤토리 데이터를 쿼리할 수 있습니다. 이러한 새 엔터티(시작 페이지에서 밑줄이 없는 엔터티)는 지정된 하드웨어 인벤토리 속성에 대해 정의된 데이터의 양에 따라 훨씬 더 큰 데이터 세트를 반환할 수 있습니다. 예를 들어, "InstalledExecutable" 엔터티는 쿼리하는 특정 데이터에 따라 클라이언트당 여러 MB의 데이터를 반환할 수 있습니다. CMPivot을 사용하여 대규모 컬렉션에서 대규모 하드웨어 인벤토리 데이터 세트를 반환하는 경우 시스템의 성능 및 확장성에 주의하세요.

쿼리는 1시간 후 시간 초과됩니다. 예를 들어 컬렉션에 500개의 디바이스가 있고, 450명의 클라이언트는 현재 온라인 상태입니다. 이러한 활성 디바이스는 쿼리를 수신하고 거의 즉시 결과를 반환합니다. CMPivot 창을 열린 상태로 두면 다른 50명의 클라이언트도 온라인 상태가 되므로 쿼리를 수신하고, 결과를 반환합니다. 

## <a name="log-files"></a>로그 파일

 CMPivot 상호 작용은 다음 로그 파일에 기록됩니다.

**서버 쪽:**
- SmsProv.log
- BgbServer.log
- StateSys.log

**클라이언트 쪽:**
- CCMNotificationAgent.log
- Scripts.log
- StateMessage.log

자세한 내용은 [로그 파일](/sccm/core/plan-design/hierarchy/log-files) 및 [CMPivot 문제 해결](/sccm/core/servers/manage/cmpivot-tsg)을 참조하세요.

## <a name="next-steps"></a>다음 단계
 
[CMPivot 문제 해결](/sccm/core/servers/manage/cmpivot-tsg)

[PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)


