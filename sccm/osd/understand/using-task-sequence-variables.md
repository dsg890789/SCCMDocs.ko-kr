---
title: 작업 순서 변수 사용 방법
titleSuffix: Configuration Manager
description: Configuration Manager 작업 순서에서 변수를 사용하는 방법에 대해 알아봅니다.
ms.date: 08/17/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: bc7de742-9e5c-4a70-945c-df4153a61cc3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63e3ec73fc08946354a7f7b84ac5bb3245cbbd76
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68340297"
---
# <a name="how-to-use-task-sequence-variables-in-configuration-manager"></a>Configuration Manager에서 작업 순서 변수를 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 OS 배포 기능에 있는 작업 순서 엔진에서는 많은 변수를 사용하여 해당 동작을 제어합니다. 다음 작업에 이러한 변수를 사용합니다. 
- 단계에 대한 조건 설정  
- 특정 단계에 대한 동작 변경  
- 더 복잡한 작업을 위한 스크립트에서 사용  


모든 사용 가능한 작업 순서 변수들을 참조하려면 [작업 순서 변수](/sccm/osd/understand/task-sequence-variables)를 참조하세요.



## <a name="bkmk_types"></a> 변수 유형

몇 가지 유형의 변수가 있습니다.  
- [기본 제공](#bkmk_built-in)  
- [작업](#bkmk_action)  
- [사용자 지정](#bkmk_custom)  
- [읽기 전용](#bkmk_read-only)  
- [배열](#bkmk_array)  


### <a name="bkmk_built-in"></a> 기본 제공 변수

기본 제공 변수는 작업 순서가 실행되는 환경에 대한 정보를 제공합니다. 해당 값은 전체 작업 순서 동안 사용할 수 있습니다. 일반적으로 작업 순서 엔진에서는 단계를 실행하기 전에 기본 제공 변수를 초기화합니다. 

예를 들어 **\_SMSTSLogPath**는 Configuration Manager 구성 요소에서 로그 파일을 작성하는 경로를 지정하는 환경 변수입니다. 모든 작업 순서 단계에서 이 환경 변수에 액세스할 수 있습니다. 

작업 순서에서는 각 단계 전에 일부 변수를 평가합니다. 예를 들어 **\_SMSTSCurrentActionName**은 현재 단계의 이름을 나열합니다. 

### <a name="bkmk_action"></a> 동작 변수

작업 순서 동작 변수는 하나의 작업 순서 단계에서 사용하는 구성 설정을 지정합니다. 기본적으로 단계는 실행되기 전에 설정을 초기화합니다. 이러한 설정은 연결된 작업 순서 단계가 실행되는 동안에만 사용할 수 있습니다. 작업 순서는 단계를 실행하기 전에 환경에 동작 변수 값을 추가합니다. 그런 다음 단계가 실행된 후 환경에서 값을 제거합니다.

예를 들어 작업 순서에 **명령줄 실행** 단계를 추가하는 경우, 이 단계는 **시작 위치** 속성을 포함합니다. 작업 순서는 이 속성에 대한 기본값을 **WorkingDirectory** 변수로 저장합니다. 작업 순서는 **명령줄 실행** 단계를 실행하기 전에 이 값을 초기화합니다. 이 단계가 실행되는 동안 **WorkingDirectory** 값에서 **시작 위치** 속성 값에 액세스합니다. 단계가 완료되면 작업 순서가 환경에서 **WorkingDirectory** 변수의 값을 제거합니다. 작업 순서에 또 다른 **명령줄 실행** 단계가 포함되어 있는 경우 작업 순서는 새 **WorkingDirectory** 변수를 초기화합니다. 이때 작업 순서는 변수를 현재 단계에 대한 시작 값으로 설정합니다. 자세한 내용은 [WorkingDirectory](/sccm/osd/understand/task-sequence-variables#WorkingDirectory)를 참조하세요.  

단계가 실행될 때에는 동작 변수의 *기본* 값이 있습니다. *새* 값을 설정하면 작업 순서의 여러 단계에 사용할 수 있습니다. 기본값을 재정의하면 새 값은 환경에 유지되고, 이 새 값은 작업 순서에 있는 다른 단계에 대한 기본값을 재정의합니다. 예를 들어 작업 순서의 첫 번째 단계로서 **작업 순서 변수 설정** 단계를 추가하는 경우, 이 단계는 **WorkingDirectory** 변수를 `C:\`로 설정합니다. 작업 순서의 모든 **명령줄 실행** 단계에서는 새 시작 디렉터리 값을 사용합니다.  

일부 작업 순서 단계는 특정 동작 변수를 *출력*으로 표시합니다. 작업 순서에서 나중에 발생하는 단계에서는 이러한 출력 변수를 읽습니다.

> [!Note]  
> 모든 작업 순서 단계에 작업 변수가 있는 것은 아닙니다. 예를 들어 **BitLocker 사용** 작업과 연결된 변수가 있지만 **BitLocker 사용 안 함** 작업과 연결된 변수는 없습니다.  


### <a name="bkmk_custom"></a> 사용자 지정 변수

이러한 변수는 Configuration Manager가 만들지 않는 변수입니다. 자신만의 변수를 초기화하여 명령줄이나 스크립트에서 조건으로 사용하세요. 

새 작업 순서 변수에 이름을 지정할 때에는 다음 지침을 따르세요.  

- 작업 순서 변수 이름은 문자, 숫자, 밑줄 문자(`_`), 하이픈(`-`)을 포함할 수 있습니다.  

- 작업 순서 변수 이름의 최소 길이는 1자이고 최대 길이 256자입니다.  

- 사용자 정의 변수는 문자(`A-Z` 또는 `a-z`)로 시작되어야 합니다.  

- 사용자 정의 변수 이름은 밑줄 문자로 시작할 수 없습니다. 밑줄 문자 앞에는 읽기 전용 작업 순서 변수만 올 수 있습니다.  

- 작업 순서 변수 이름은 대소문자를 구분하지 않습니다. 예를 들어 `OSDVAR`과 `osdvar`은 같은 작업 순서 변수입니다.  

- 작업 순서 변수 이름은 공백으로 시작하거나 끝날 수 없으며 공백을 포함할 수도 없습니다. 작업 순서는 변수 이름의 시작 부분이나 끝 부분에 있는 공백은 무시합니다.  


만들 수 있는 작업 순서 변수의 수에는 설정된 제한이 없습니다. 그러나 변수의 수는 작업 순서 환경의 크기에 의해 제한됩니다. 작업 순서 환경의 총 크기 제한은 32MB입니다.  


### <a name="bkmk_read-only"></a> 읽기 전용 변수

일부 변수의 값은 읽기 전용이어서 변경할 수 없습니다. 일반적으로 이러한 변수의 이름은 밑줄 문자(\_)로 시작합니다. 작업 순서는 작업 순서 운영에 이 변수를 사용합니다. 읽기 전용 변수는 작업 순서 환경에 표시됩니다. 

이러한 변수는 스크립트나 명령줄에서 유용합니다. 예를 들어, 명령줄을 실행하고 출력을 다른 로그 파일과 함께 **\_SMSTSLogPath**의 로그 파일에 전송합니다.

> [!NOTE]  
>  읽기 전용 작업 순서 변수는 작업 순서의 단계에서 읽을 수는 있지만 설정할 수는 없습니다. 예를 들어, 읽기 전용 변수를 **명령줄 실행** 단계를 위한 명령줄의 일부로 사용할 수 있지만, **작업 순서 변수 설정** 단계를 사용하여 읽기 전용 변수를 설정할 수는 없습니다.  



### <a name="bkmk_array"></a> 배열 변수

작업 순서는 일부 변수를 배열로 저장합니다. 배열의 각 요소는 하나의 개체에 대한 설정을 나타냅니다. 디바이스에 구성할 개체가 두 개 이상 있을 때 이 변수를 사용하세요. 다음 작업 순서 단계에서 배열 변수를 사용합니다.

- [네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings)  

- [디스크 포맷 및 파티션 만들기](task-sequence-steps.md#BKMK_FormatandPartitionDisk)  



## <a name="bkmk_set"></a> 변수 설정 방법

사용자 지정 변수나 읽기 전용이 아닌 변수의 경우, 변수의 값을 초기화하고 설정하는 방법에는 몇 가지가 있습니다.  

- [작업 순서 변수 설정](#bkmk_set-ts-step)  
- [동적 변수 설정](#bkmk_set-dyn-step)  
- [컬렉션 및 장치 변수](#bkmk_set-coll-var)  
- [TSEnvironment COM 개체](#bkmk_set-com)  
- [시작 전 명령](#bkmk_set-prestart)  
- [작업 순서 미디어 마법사](#bkmk_set-media)  


변수를 만들 때와 동일한 방법을 사용하여 환경에서 변수를 삭제합니다. 변수를 삭제하려면 변수 값을 빈 문자열로 설정합니다.  

동일한 순서에 대해 작업 순서 변수를 서로 다른 값으로 설정하는 방법을 결합할 수 있습니다. 예를 들어 작업 순서 편집기를 사용하여 기본값을 설정한 다음, 스크립트를 사용하여 사용자 지정 값을 설정합니다. 

서로 다른 방법으로 동일한 변수를 설정하는 경우 작업 순서 엔진은 다음 순서를 사용합니다.  

1. 먼저 컬렉션 변수를 평가합니다.  

2. 디바이스별 변수가 컬렉션에 설정된 동일한 변수를 재정의합니다.  

3. 어떤 방법으로든 작업 순서 동안 설정한 변수는 컬렉션 변수나 디바이스 변수보다 우선합니다.  


#### <a name="general-limitations-for-task-sequence-variable-values"></a>작업 순서 변수 값에 대한 일반적인 제한 사항  

- 작업 순서 변수 값은 4,000자를 초과할 수 없습니다.  

- 읽기 전용 작업 순서 변수는 변경할 수 없습니다. 읽기 전용 변수의 이름은 밑줄 문자(`_`)로 시작합니다.  

- 작업 순서 변수 값은 값의 용도에 따라 대/소문자를 구분할 수 있습니다. 대부분의 경우 작업 순서 변수 값은 대/소문자를 구분하지 않습니다. 암호를 포함하는 변수는 대/소문자를 구분합니다.  


### <a name="bkmk_set-ts-step"></a> 작업 순서 변수 설정

하나의 값으로 하나의 변수를 설정하려면 작업 순서에서 이 단계를 사용합니다. 

자세한 내용은 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable)을 참조하세요. 


### <a name="bkmk_set-dyn-step"></a> 동적 변수 설정

하나 이상의 작업 순서 변수를 설정하려면 작업 순서에서 이 단계를 사용합니다. 사용할 변수 및 값을 결정하려면 이 단계에서 규칙을 정의합니다. 

자세한 내용은 [동적 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetDynamicVariables)을 참조하세요.


### <a name="bkmk_set-coll-var"></a> 컬렉션 및 장치 변수

컬렉션 또는 특정 디바이스의 속성에 대한 변수를 설정합니다. 

자세한 내용은 [Create task sequence variables for computers and collections](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_CreateTSVariables)\(컴퓨터 및 컬렉션에 대한 작업 순서 변수 만들기\)를 참조하세요.


### <a name="bkmk_set-com"></a> TSEnvironment COM 개체

스크립트에서 변수를 사용하려면 **TSEnvironment** 개체를 사용합니다. 

자세한 내용은 Configuration Manager SDK에서 [How to use variables in a running task sequence](/sccm/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence)\(실행 중인 작업 순서에서 변수를 사용하는 방법\)을 참조하세요.


### <a name="bkmk_set-prestart"></a> 시작 전 명령

시작 전 명령은 사용자가 작업 순서를 선택하기 전에 Windows PE에서 실행되는 스크립트나 실행 파일입니다. 시작 전 명령은 변수를 쿼리하고 사용자에게 정보를 물은 다음, 이 정보를 환경에 저장할 수 있습니다. 시작 전 명령의 변수를 읽고 쓰는 데에는 [TSEnvironment](#bkmk_set-com) COM 개체를 사용합니다. 

자세한 내용은 [작업 순서 미디어에 대한 시작 전 명령](/sccm/osd/understand/prestart-commands-for-task-sequence-media)을 참조하세요.


### <a name="bkmk_set-media"></a> 작업 순서 미디어 마법사

미디어에서 실행되는 작업 순서에 대한 변수를 지정합니다. 미디어를 사용하여 OS를 배포할 경우, 미디어를 만들 때 작업 순서 변수를 추가하고 해당 값을 지정합니다. 변수와 해당 값은 미디어에 저장됩니다.  

> [!NOTE]  
>  작업 순서는 독립 실행형 미디어에 저장됩니다. 그러나 미리 준비된 미디어와 같은 기타 모든 유형의 미디어는 관리 지점에서 작업 순서를 검색합니다.  

미디어에서 작업 순서를 실행할 때 마법사의 **사용자 지정** 페이지에서 변수를 추가할 수 있습니다. 

컬렉션별 또는 컴퓨터별 변수 대신에 미디어 변수를 사용합니다. 작업 순서가 미디어에서 실행되는 경우 컴퓨터별 변수와 컬렉션별 변수가 적용되거나 사용되지 않습니다.  

> [!TIP]  
>  작업 순서는 Configuration Manager 콘솔을 실행하는 컴퓨터의 **CreateTSMedia.log** 파일에 패키지 ID 및 시작 전 명령줄을 기록합니다. 이 로그 파일에는 작업 순서 변수의 값이 포함됩니다. 이 로그 파일을 검토하여 작업 순서 변수의 값을 확인합니다.  

자세한 내용은 [작업 순서 미디어 만들기](/sccm/osd/deploy-use/create-task-sequence-media)를 참조하세요.



## <a name="bkmk_access"></a> 변수에 액세스하는 방법

이전 섹션의 방법 중 하나를 사용하여 변수 및 해당 값을 지정하면 작업 순서에서 사용할 수 있습니다. 예를 들어, 기본 제공 작업 순서 변수의 기본값에 액세스하거나 변수의 값에 대해 단계를 조건부 단계로 만듭니다.  

작업 순서 환경에서 변수 값에 액세스하려면 다음 방법을 사용합니다.
- [단계에서 사용](#bkmk_access-step)  
- [단계 조건](#bkmk_access-condition)  
- [사용자 지정 스크립트](#bkmk_access-script)  
- [Windows 설치 응답 파일](#bkmk_access-answer)  


### <a name="bkmk_access-step"></a> 단계에서 사용

작업 순서 단계에서 설정에 대한 변수 값을 지정하고, 작업 순서 편집기에서 단계를 편집하고 변수 이름을 필드 값을 지정합니다. 변수 이름은 백분율 기호(`%`)로 묶습니다. 

예를 들어, 변수 이름을 **명령줄 실행** 단계의 **명령줄** 필드 일부로 사용합니다. 다음 명령줄은 컴퓨터 이름을 텍스트 파일에 기록합니다. 

`cmd.exe /c %_SMSTSMachineName% > C:\File.txt`


### <a name="bkmk_access-condition"></a> 단계 조건

기본 제공 또는 사용자 지정 작업 순서 변수를 단계 또는 그룹에서 조건의 일부로 사용합니다. 작업 순서는 단계나 그룹을 실행하기 전에 변수 값을 평가합니다.

변수 값을 평가하는 조건을 추가하려면 다음 절차를 수행하세요.  

1. 작업 순서 편집기에서 조건을 추가할 단계 또는 그룹을 선택합니다.  

2. 단계 또는 그룹에 대한 **옵션** 탭으로 전환합니다. **조건 추가**를 클릭하고 **작업 순서 변수**를 선택합니다.  

3. **작업 순서 변수** 대화 상자에서 다음 설정을 지정합니다.  

    - **변수**: 변수 이름. 예: `_SMSTSInWinPE`  

    - **조건**: 변수 값을 평가할 조건. 예: **같음**  

    - **값**: 검사할 변수의 값. 예: `false`  


위의 세 가지 예는 다음과 같이 작업 순서가 Windows PE의 부팅 이미지에서 실행되는지 여부를 테스트하기 위한 일반적인 조건을 형성합니다. 

> **작업 순서 변수** `_SMSTSInWinPE equals "false"`

기존 OS 이미지를 설치하려면 기본 작업 순서 템플릿의 **파일 및 설정 캡처** 그룹에서 이 조건을 확인하세요.


### <a name="bkmk_access-script"></a> 사용자 지정 스크립트

작업 순서가 실행되는 동안 **Microsoft.SMS.TSEnvironment** COM 개체를 사용하여 변수를 읽고 씁니다.

다음 Windows PowerShell 예에서는 **_SMSTSLogPath** 변수를 쿼리하여 현재 로그 위치를 가져옵니다. 또한 스크립트는 사용자 지정 변수를 설정합니다.

```PowerShell
# Create an object to access the task sequence environment
$tsenv = New-Object -ComObject Microsoft.SMS.TSEnvironment

# Query the environment to get an existing variable
# Set a variable for the task sequence log path
$LogPath = $tsenv.Value("_SMSTSLogPath")

# Or, convert all of the variables currently in the environment to PowerShell variables
$tsenv.GetVariables() | % { Set-Variable -Name "$_" -Value "$($tsenv.Value($_))" }

# Write a message to a log file
Write-Output "Hello world!" | Out-File -FilePath "$_SMSTSLogPath\mylog.log" -Encoding "Default" -Append

# Set a custom variable "startTime" to the current time
$tsenv.Value("startTime") = (Get-Date -Format HH:mm:ss) + ".000+000"
```


###  <a name="bkmk_access-answer"></a> Windows 설치 응답 파일

제공한 Windows 설치 응답 파일에는 포함된 작업 순서 변수가 있을 수 있습니다. `%varname%` 형식을 사용하세요. 여기서 *varname*은 변수의 이름입니다. **Windows 및 ConfigMgr 설치** 단계는 실제 변수 값을 변수 이름 문자열로 대체합니다. 이러한 포함된 작업 순서 변수는 unattend.xml 응답 파일의 숫자 전용 필드에 사용할 수 없습니다.

자세한 내용은 [Windows 및 ConfigMgr 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr)을 참조하세요.



## <a name="see-also"></a>참고 항목

- [작업 순서 단계](/sccm/osd/understand/task-sequence-steps)
- [작업 순서 변수](/sccm/osd/understand/task-sequence-variables)
- [작업 자동화에 대한 계획 고려 사항](/sccm/osd/plan-design/planning-considerations-for-automating-tasks)
