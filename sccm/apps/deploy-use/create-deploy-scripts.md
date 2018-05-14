---
title: 스크립트 만들기 및 실행
titleSuffix: Configuration Manager
description: Powershell 스크립트를 만들고 클라이언트 장치에서 실행합니다.
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fcf3bc335efc4c7436842b29d30c67c118ceb05d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1236459-->
System Center Configuration Manager가 PowerShell 스크립트를 실행하는 기능과 통합되었습니다. Powershell은 정교하고 자동화된 스크립트를 만들어 더 큰 커뮤니티에서 이해하고 공유할 수 있는 이점이 있습니다. 스크립트는 소프트웨어를 관리하는 사용자 지정 도구 빌드를 간소화하고 일상적인 작업을 빠르게 수행하므로 더 쉽고 일관되게 대형 작업을 수행할 수 있습니다.  

> [!TIP]  
> 이 기능은 버전 1706에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1802 버전부터 이 기능은 더 이상 시험판 기능이 아닙니다.  


> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  


이 통합 기능을 System Center Configuration Manager에서 사용하면 *스크립트 실행* 기능을 사용하여 다음을 수행할 수 있습니다.

- System Center Configuration Manager에서 사용할 스크립트를 만들고 편집합니다.
- 역할 및 보안 범위를 통해 스크립트 사용을 관리합니다. 
- 컬렉션 또는 개별 온-프레미스 관리 Windows PC에서 스크립트를 실행합니다.
- 클라이언트 장치에서 빠르게 집계된 스크립트 결과를 가져옵니다.
- 스크립트 실행을 모니터링하고 스크립트 출력에서 보고 결과를 봅니다.

>[!WARNING]
>스크립트의 능력을 고려할 때 계획적이고 신중하게 사용해야 합니다. 사용자를 지원하기 위해 안전 장치, 즉 분리된 역할과 범위를 추가로 구축했습니다. 스크립트를 실행하기 전에 스크립트의 정확성을 검사하고 신뢰할 수 있는 원본에서 제공되는지 확인하여 의도하지 않은 스크립트 실행을 방지합니다. 확장된 문자 또는 다른 난독 처리에 유의하고 스크립트 보안에 대한 지식을 습득합니다. [PowerShell 스크립트 보안에 대해 자세히 알아보기](/sccm/apps/deploy-use/learn-script-security)

## <a name="prerequisites"></a>필수 구성 요소

- PowerShell 스크립트를 실행하려면 클라이언트에서 PowerShell 버전 3.0 이상이 실행되고 있어야 합니다. 그러나 실행하는 스크립트에 이후 버전의 PowerShell 기능이 포함되어 있을 경우 스크립트를 실행하는 클라이언트에서 해당 버전의 PowerShell이 실행되고 있어야 합니다.
- Configuration Manager 클라이언트는 스크립트를 실행하려면 1706 릴리스 이상의 클라이언트를 실행하고 있어야 합니다.
- 스크립트를 사용하려면 해당 Configuration Manager 보안 역할의 구성원이어야 합니다.
- 스크립트를 가져오고 작성하려면 **SMS 스크립트**에 대한 **만들기** 권한이 있어야 합니다.
- 스크립트를 승인하거나 거부하려면 **SMS 스크립트**에 대한 **승인** 권한이 있어야 합니다.
- 스크립트를 실행하려면 **컬렉션**에 대한 **스크립트 실행** 권한이 있어야 합니다.

Configuration Manager 보안 역할에 대한 자세한 내용은 다음과 같습니다.</br>
[스크립트 실행에 대한 보안 범위](#BKMK_Scopes)</br>
[스크립트 실행에 대한 보안 역할](#BKMK_ScriptRoles)</br>
[역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration).

## <a name="limitations"></a>제한 사항

스크립트 실행에서 현재 지원하는 항목은 다음과 같습니다.

- 스크립팅 언어: PowerShell
- 매개 변수 형식: 정수, 문자열 및 목록.


>[!WARNING]
>매개 변수를 사용할 때 잠재적인 PowerShell 삽입 공격 위험에 대한 노출 영역이 열리는 것에 유의하십시오. 매개 변수 입력 유효성 검사에 정규식을 사용하거나 미리 정의된 매개 변수를 사용하는 등 완화하고 해결하는 방법에는 여러 가지가 있습니다. 일반적인 모범 사례는 PowerShell 스크립트(암호 없음 등)에 암호를 포함하지 않는 것입니다. [PowerShell 스크립트 보안에 대해 자세히 알아보기](/sccm/apps/deploy-use/learn-script-security) <!--There are external tools available to validate your PowerShell scripts such as the [PowerShell Injection Hunter](https://www.powershellgallery.com/packages/InjectionHunter/1.0.0) tool. -->


## <a name="run-script-authors-and-approvers"></a>스크립트 실행 작성자 및 승인자

스크립트 실행에서는 *스크립트 작성자* 및 *스크립트 승인자*의 개념을 스크립트를 구현하고 실행하기 위한 별도의 역할로 사용합니다. 작성자와 승인자 역할을 분리하면 스크립트 실행이라는 강력한 도구에 대한 중요한 프로세스를 검사할 수 있습니다. 스크립트 만들기나 승인이 아닌 스크립트 실행을 허용하는 추가적인 *스크립트 실행기* 역할이 있습니다. [스크립트에 대한 보안 역할 만들기](#BKMK_ScriptRoles)를 참조합니다.

### <a name="scripts-roles-control"></a>스크립트 역할 제어

기본적으로 사용자는 작성한 스크립트를 승인할 수 없습니다. 스크립트는 강력하고 다양하며 잠재적인 기능을 여러 장치에 배포할 수 있으므로 스크립트를 작성하는 사용자와 스크립트를 승인하는 사용자 간에 역할을 분리할 수 있습니다. 이러한 역할을 통해 감독 없이 스크립트를 실행할 때도 추가적으로 보안을 강화하는 효과를 얻을 수 있습니다. 쉬운 테스트를 위해 보조 승인을 해제할 수 있습니다.

### <a name="approve-or-deny-a-script"></a>스크립트 승인 또는 거부

스크립트는 *스크립트 승인자* 역할을 통해 승인되어야 실행할 수 있습니다. 스크립트를 승인하려면

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. **소프트웨어 라이브러리** 작업 영역에서 **스크립트**를 클릭합니다.
3. **스크립트** 목록에서 승인 또는 거부하려는 스크립트를 선택한 후 **홈** 탭의 **스크립트** 그룹에서 **승인/거부**를 클릭합니다.
4. **스크립트 승인 또는 거부** 대화 상자에서 스크립트에 대한 **승인** 또는 **거부**를 선택합니다. 필요에 따라 이러한 결정에 대한 설명을 입력합니다.  스크립트를 거부하는 경우 클라이언트 장치에서 실행할 수 없습니다. <br>
![스크립트 - 승인](./media/run-scripts/RS-approval.png)
1. 마법사를 완료합니다. **스크립트** 목록에서 **승인 상태** 열이 수행한 작업에 따라 변경됩니다.

### <a name="allow-users-to-approve-their-own-scripts"></a>사용자가 자신의 스크립트를 승인하도록 허용

이 승인은 주로 스크립트 개발의 테스트 단계에 사용됩니다.

1. Configuration Manager 콘솔에서 **관리**를 클릭합니다.
2. **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.
3. 사이트 목록에서 사이트를 선택한 후 **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 클릭합니다.
4. **계층 구조 설정 속성** 대화 상자의 **일반** 탭에서 **스크립트 작성자가 스크립트를 승인하도록 허용 안 함** 확인란을 선택 취소합니다.

>[!IMPORTANT]
>모범 사례에서는 스크립트 작성자가 고유한 스크립트를 승인하도록 허용하지 않아야 합니다. 랩 설정에서만 허용해야 합니다. 프로덕션 환경에서 이 설정을 변경할 때 발생할 수 있는 잠재적인 영향을 신중하게 고려하세요.

## <a name="security-scopes"></a>보안 범위
*(버전 1710에서 도입됨)*  
스크립트 실행은 Configuration Manager의 기존 기능인 보안 범위를 사용하여 사용자 그룹을 나타내는 태그를 할당하여 스크립트 작성 및 실행을 제어합니다. 보안 범위 사용에 대한 자세한 내용은 [System Center Configuration Manager에 대한 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.

## <a name="bkmk_ScriptRoles"></a>스크립트에 대한 보안 역할 만들기
스크립트를 실행하는 데 사용되는 세 가지 보안 역할은 Configuration Manager에서 기본으로 만들어지지 않습니다. 스크립트 실행기, 스크립트 작성자 및 스크립트 승인자 역할을 만들려면 개략적으로 설명된 단계를 수행 합니다.

1. Configuration Manager 콘솔에서 **관리** >**보안** >**보안 역할**로 이동
2. 역할을 마우스 오른쪽 단추로 클릭하고 **복사**를 클릭합니다. 복사하는 역할은 이미 사용 권한이 할당되었습니다. 원하는 사용 권한만 있는지 확인합니다. 
3. 사용자 지정 역할에 **이름** 및 **설명**을 부여합니다. 
4. 보안 역할에 아래에 설명된 사용 권한을 할당합니다.  

### <a name="security-role-permissions"></a>보안 역할 사용 권한  

**역할 이름**: 스크립트 실행기  
- **설명**: 이러한 사용 권한을 통해 이 역할이 다른 역할에 의해 이전에 만들어지고 승인된 스크립트만 실행하도록 설정합니다.  
- **사용 권한:** 다음을 확인하려면 **예**로 설정합니다.  

|범주|사용 권한|시스템 상태|
|---|---|---|
|수집|스크립트 실행|예|
|사이트|읽기|예|
|SMS 스크립트|만들기|예|
|SMS 스크립트|읽기|예|


**역할 이름**: 스크립트 작성자  
- **설명**: 이러한 사용 권한을 통해 이 역할이 스크립트를 작성하도록 설정하지만 승인하거나 실행할 수는 없습니다.  
- **사용 권한:** 다음 사용 권한이 설정되었는지 확인합니다.
 
|범주|사용 권한|시스템 상태|
|---|---|---|
|수집|스크립트 실행|아니요|
|사이트|읽기|예|
|SMS 스크립트|만들기|예|
|SMS 스크립트|읽기|예|
|SMS 스크립트|삭제|예|
|SMS 스크립트|수정|예|


**역할 이름**: 스크립트 승인자  
- **설명**: 이러한 사용 권한을 통해 이 역할이 스크립트를 승인하도록 설정하지만 만들거나 실행할 수는 없습니다.  
- **사용 권한:** 다음 사용 권한이 설정되었는지 확인합니다.  

|범주|사용 권한|시스템 상태|
|---|---|---|
|수집|스크립트 실행|아니요|
|사이트|읽기|예|
|SMS 스크립트|읽기|예|
|SMS 스크립트|승인|예|
|SMS 스크립트|수정|예|

     
**스크립트 작성자 역할에 대한 SMS 스크립트 사용 권한의 예**  

 ![스크립트 작성자 역할에 대한 SMS 스크립트 사용 권한의 예](./media/run-scripts/script_authors_permissions.png)

   

## <a name="create-a-script"></a>스크립트 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. **소프트웨어 라이브러리** 작업 영역에서 **스크립트**를 클릭합니다.
3. **홈** 탭의 **만들기** 그룹에서 **스크립트 만들기**를 클릭합니다.
4. **스크립트 만들기** 마법사의 **스크립트** 페이지에서 다음 설정을 구성합니다.
    - **스크립트 이름** - 스크립트의 이름을 입력합니다. 여러 스크립트를 같은 이름으로 만들 수 있지만 중복된 이름을 사용하면 Configuration Manager 콘솔에서 필요한 스크립트를 찾는 것이 더 어려워집니다.
    - **스크립트 언어** - 현재 PowerShell 스크립트만 지원됩니다.
    - **가져오기** - 콘솔로 PowerShell 스크립트를 가져옵니다. 스크립트는 **스크립트** 필드에 표시됩니다.
    - **지우기** - 스크립트 필드에서 현재 스크립트를 제거합니다.
    - **스크립트** - 현재 가져온 스크립트를 표시합니다. 필요에 따라 이 필드에서 스크립트를 편집할 수 있습니다.
5. 마법사를 완료합니다. 새 스크립트가 **승인 대기 중** 상태로 **스크립트** 목록에 표시됩니다. 클라이언트 장치에서 이 스크립트를 실행하려면 먼저 승인해야 합니다. 

> [!IMPORTANT]
    >스크립트 실행 기능을 사용할 때는 장치 다시 부팅 또는 Configuration Manager 에이전트 다시 시작 스크립트를 사용하지 마세요. 그러면 연속 다시 부팅 상태가 될 수 있습니다. 필요한 경우, Configuration Manager 버전 1710부터는 장치를 다시 시작할 수 있는 클라이언트 알림 기능에 대한 개선 사항이 있습니다. [다시 시작 보류 중 열](/sccm/core/clients/manage/manage-clients#Restart-clients)을 통해 다시 시작해야 하는 장치를 식별할 수 있습니다. 
<!--SMS503978  -->

## <a name="script-parameters"></a>스크립트 매개 변수
*(버전 1710에서 도입됨)*  
스크립트에 매개 변수를 추가하면 작업의 유연성이 향상됩니다. 다음은 *문자열* 및 *정수* 데이터 형식에 대한 스크립트 매개 변수가 있는 스크립트 실행 기능의 현재 기능을 요약한 것입니다. 미리 설정된 값 목록도 사용할 수 있습니다. 스크립트에 지원되지 않는 데이터 형식이 있으면 경고가 발생합니다.

**스크립트 만들기** 대화 상자에서 **스크립트** 아래의 **스크립트 매개 변수**를 클릭합니다.

각 스크립트 매개 변수에는 세부 정보 및 유효성 검사를 추가할 수 있는 자체의 대화 상자가 있습니다.

>[!IMPORTANT]
> 매개 변수 값에는 아포스트로피가 포함될 수 없습니다. </br></br>
> Configuration Manager 버전 1802에 공백이 있는 매개 변수가 스크립트에 제대로 전달되지 않는 알려진 문제가 있습니다. 매개 변수에 공백이 사용되는 경우 매개 변수의 첫 번째 항목만 스크립트에 전달되고 공백 다음의 모든 항목이 전달되지 않습니다. 관리자는 공백을 다른 문자로 대체하고 변환하거나 다른 방법을 사용하여 이 문제를 해결할 수 있습니다.


### <a name="parameter-validation"></a>매개 변수 유효성 검사

스크립트의 각 매개 변수는 **스크립트 매개 변수 속성** 대화 상자를 통해 해당 매개 변수에 대한 유효성 검사를 추가할 수 있습니다. 유효성 검사를 추가한 후에 유효성 검사를 충족하지 않는 매개 변수 값이 입력되면 오류가 발생합니다.

#### <a name="example-firstname"></a>예제: *FirstName*

이 예제에서는 *FirstName* 문자열 매개 변수의 속성을 설정할 수 있습니다.

![스크립트 매개 변수 - 문자열](./media/run-scripts/RS-parameters-string.png)


**스크립트 매개 변수 속성** 대화 상자의 유효성 검사 섹션에서는 다음 필드를 사용할 수 있습니다.

- **최소 길이** - *FirstName* 필드의 최소 문자 수입니다.
- **최대 길이**- *FirstName* 필드의 최대 문자 수입니다.
- **RegEx** - *정규식*의 축약형입니다. 정규식 사용에 대한 자세한 내용은 다음 섹션 *정규식 유효성 검사 사용*을 참조하세요.
- **사용자 지정 오류** - 시스템 유효성 검사 오류 메시지를 대체하는 사용자 지정 오류 메시지를 추가하는 데 유용합니다.

#### <a name="using-regular-expression-validation"></a>정규식 유효성 검사 사용

정규식은 인코딩된 유효성 검사에 대해 문자열을 확인하기 위한 간단한 형식의 프로그래밍입니다. 예를 들어, *RegEx* 필드에 `[^A-Z]`을 지정하여 *FirstName* 필드에 대문자 영문자가 있는지 확인할 수 있습니다.

이 대화 상자의 정규식 처리는 .NET Framework에서 지원합니다. 정규식 사용에 관한 지침은 [.NET Regular Expression](https://docs.microsoft.com/dotnet/standard/base-types/regular-expressions)(.NET 정규식)을 참조하세요. 


## <a name="script-examples"></a>스크립트 예제

다음은 이 기능과 함께 사용할 스크립트를 보여 주는 몇 가지 예제입니다.

### <a name="create-a-new-folder-and-file"></a>새 폴더 및 파일 만들기

이 스크립트는 사용자의 명명 입력에 따라 새 폴더와 폴더 내의 파일을 만듭니다.

``` powershell
Param(
[Parameter(Mandatory=$True)]
[string]$FolderName,
[Parameter(Mandatory=$True)]
[string]$FileName,
)

New-Item $FolderName -type directory
New-Item $FileName -type file
```

### <a name="get-os-version"></a>OS 버전 가져오기

이 스크립트는 WMI를 사용하여 컴퓨터에 OS 버전을 쿼리합니다.

``` powershell
Write-Output (Get-WmiObject -Class Win32_operatingSystem).Caption
```

## <a name="run-a-script"></a>스크립트 실행

스크립트가 승인되면 단일 장치 또는 컬렉션에 대해 실행할 수 있습니다. 스크립트 실행이 시작되면 1시간 후에 시간 초과되는 우선 순위가 높은 시스템을 통해 빠르게 시작됩니다. 스크립트의 결과는 상태 메시지 시스템을 사용하여 반환됩니다.

스크립트의 대상 컬렉션을 선택하려면 다음을 수행합니다.

1. Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.
2. 자산 및 호환성 작업 영역에서 **장치 컬렉션**을 클릭합니다.
3. **장치 컬렉션** 목록에서 스크립트를 실행하려는 장치 컬렉션을 클릭합니다.
4. 원하는 컬렉션을 선택하고 **스크립트 실행**을 클릭합니다.
5. **스크립트 실행** 마법사의 **스크립트** 페이지에서 목록에 있는 스크립트를 선택합니다. 승인된 스크립트만 표시됩니다.
6. **다음**을 클릭하여 마법사를 완료합니다.

>[!IMPORTANT]
>예를 들어 1시간 동안 대상 장치가 꺼져 있어 스크립트가 실행되지 않으면 다시 실행해야 합니다.

### <a name="target-machine-execution"></a>대상 컴퓨터 실행

스크립트가 대상 클라이언트에서 *시스템* 또는 *컴퓨터* 계정으로 실행됩니다. 이 계정은 네트워크 액세스가 제한됩니다. 이에 따라 스크립트를 통한 원격 시스템 및 위치에 대한 모든 액세스가 프로비전되어야 합니다.

## <a name="script-monitoring"></a>스크립트 모니터링

장치 컬렉션에서 스크립트 실행을 시작한 후에는 다음 절차에 따라 작업을 모니터링합니다. 버전 1710부터는 실행되는 스크립트를 실시간으로 모니터링할 수 있으며 지정된 스크립트 실행에 대한 보고서로 돌아갈 수도 있습니다. <br>

![스크립트 모니터 - 스크립트 실행 상태](./media/run-scripts/RS-monitoring-three-bar.png)

1. Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.
2. **모니터링** 작업 영역에서 **스크립트 상태**를 클릭합니다.
3. **스크립트 상태** 목록에서 클라이언트 장치에서 실행한 각 스크립트에 대한 결과를 확인합니다. 스크립트 종료 코드 **0**은 일반적으로 스크립트가 성공적으로 실행되었음을 나타냅니다.
    - Configuration Manager 1802부터 스크립트 출력은 더 나은 표시 환경을 위해 4KB로 잘립니다.  <!--510013-->
      ![스크립트 모니터 - 잘린 스크립트](./media/run-scripts/Script-monitoring-truncated.png) 

## <a name="script-output"></a>스크립트 출력

- Configuration Manager 버전 1802부터 스크립트 출력은 JSON 형식을 사용하여 반환됩니다. 이 형식은 읽기 가능한 스크립트 출력을 일관되게 반환합니다. 
- 알 수 없는 결과를 가져오는 스크립트 또는 클라이언트가 오프라인인 스크립트는 차트 또는 데이터 집합에 표시되지 않습니다. <!--507179-->
- 4KB로 잘리기 때문에 대형 스크립트 출력은 반환하지 마십시오. <!--508488-->
- 스크립트 출력 형식의 일부 기능은 클라이언트의 하위 버전으로 Configuration Manager 버전 1802 이상을 실행하는 경우 사용할 수 없습니다. <!--508487-->
    - Configuration Manager 클라이언트 버전 1802 이전을 사용 중인 경우 문자열 출력을 가져옵니다.
    -  Configuration Manager 클라이언트 버전 1802 이상에서는 JSON 서식을 가져옵니다.
        - 예를 들어 한 클라이언트 버전에서는 TEXT라는 결과가 표시되고, 다른 버전에서는 "TEXT"(큰따옴표로 묶은 출력)라는 결과가 표시될 수 있습니다. 이 결과는 차트에 두 가지 범주로 표시됩니다.
        - 이 문제를 해결해야 할 경우, 두 가지 컬렉션에 대한 스크립트를 실행하는 것이 좋습니다. 1802 이전 버전의 클라이언트가 있는 컬렉션과 1802 이상 버전의 클라이언트가 있는 컬렉션이 이에 해당합니다. 또는 열거형 개체를 스크립트에서 문자열 값으로 변환하여 JSON 형식에서 올바르게 표시할 수 있습니다. 
- 열거형 개체를 스크립트에서 문자열 값으로 변환하여 JSON 형식에서 올바르게 표시되게 합니다. <!--508377--> ![열거형 개체를 문자열 값으로 변환](./media/run-scripts/enum-tostring-JSON.png)



## <a name="see-also"></a>참고 항목

- [System Center Configuration Manager에 대한 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)
- [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)
