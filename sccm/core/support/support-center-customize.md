---
title: 지원 센터 사용자 지정
titleSuffix: Configuration Manager
description: 지원 센터 구성 파일을 사용자 지정합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a6f7f6b7-9ef3-4ffa-a3cf-d877ac55983b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b100daf91b8bb7c5d4dd5f041c57e7dc9dac390e
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56156783"
---
# <a name="customize-support-center"></a>지원 센터 사용자 지정

*적용 대상: System Center Configuration Manager(현재 분기)*

[지원 센터](/sccm/core/support/support-center) 도구에는 사용자 지정할 수 있는 구성 파일이 포함됩니다. 기본적으로 지원 센터를 설치할 때 이 파일은 다음 경에 있습니다. `C:\Program Files (x86)\Configuration Manager Support Center\ConfigMgrSupportCenter.exe.config` 구성 파일은 프로그램의 동작을 변경합니다.

  - [데이터 수집 사용자 지정:](#bkmk_datacoll) 데이터를 수집하는 동안 포함하는 레지스트리 키 및 WMI 네임스페이스 세트를 편집합니다.  

  - [로그 그룹 사용자 지정](#bkmk_loggroups): 정규식을 사용하여 로그 파일의 새 그룹을 정의합니다. 또한 그룹을 기록할 다른 로그 파일을 추가합니다.  

  - [와일드카드를 사용하여 추가 로그 파일 수집](#bkmk_wildcards): 와일드카드 검색을 사용하여 추가 로그 파일을 수집합니다.  

이렇게 변경하려면 지원 센터를 설치한 클라이언트에서 로컬 관리자 권한이 필요합니다. 메모장 또는 Visual Studio와 같은 XML 편집기 또는 텍스트를 사용하여 이러한 사용자 지정을 확인합니다.

> [!Important]  
> 지원 센터 구성 파일은 XML 형식의 파일입니다. 지원 센터의 작동은 필수입니다. XML 및 정규식을 잘 알고 있는 사용자만 이 파일을 수정하는 것이 좋습니다.  

지원 센터 구성 파일을 사용자 지정하기 전에 원래 백업을 저장합니다. 이 백업을 통해 파일을 편집하는 동안 실수한 경우 원래 지원 센터 기능을 복구할 수 있습니다. 백업을 만들지 않는 경우 지원 센터는 구성 파일을 수정한 후 올바르게 작동하지 않으며 지원 센터를 다시 설치합니다. 또한 지원 센터의 다른 설치에서 구성 파일을 복사할 수 있습니다.



## <a name="bkmk_datacoll"></a> 데이터 수집 사용자 지정

클라이언트에서 데이터 수집을 사용자 지정하려면 `<dataCollectorSettings>` 요소 내에 포함된 XML 요소를 사용하여 지원 센터 구성 파일을 수정합니다.


### <a name="wmi-data-collection"></a>WMI 데이터 수집

`<CcmWmiDataCollector>` 요소는 `<collectionScopes>` 요소를 포함합니다. 지원 센터가 데이터를 수집하는 WMI 네임스페이스를 변경하려면 이 요소를 사용합니다. `<ignoreScopes>` 요소도 포함되어 있습니다. 이 요소를 사용하여 `<collectionScopes>` 요소에 정의된 네임스페이스의 일부에서 데이터 수집을 필터링할 수 있습니다.  
    
#### <a name="example"></a>예
기본 구성 파일은 `root\ccm` 네임스페이스에서 데이터를 수집합니다. `<collectionScopes>`의 `<add/>` 요소에 이 경로도 포함되어 있습니다. 

또한 이 네임스페이스에 대한 `\cimodels`, `\invagt`, `\events` 및 `\policy` 경로에 있는 모든 항목이 무시됩니다. `<ignoreScopes>` 내에 포함된 `<add/>` 요소에 있는 이러한 경로가 포함되어 있습니다.

```XML
<CcmWmiDataCollector>
  <collectionScopes>
    <!-- Collect these namespaces (ignoring the sub-scopes in the ignoreScopes block) -->
    <add key="root\ccm"/>
    <add key="root\cimv2\sms"/>
  </collectionScopes>
  <ignoreScopes>
    <!-- Collecting these namespaces is known to be problematic/unnecessary -->
    <add key="root\ccm\cimodels"/>
    <add key="root\ccm\invagt"/>
    <add key="root\ccm\events"/>
    <!-- Do not collect policy, there's already a separate policy collector.-->
    <add key="root\ccm\policy"/>
  </ignoreScopes>
</CcmWmiDataCollector>
```


### <a name="registry-data-collection"></a>레지스트리 데이터 수집

`<RegistryDataCollector>` 요소는 `<registryKeys>` 요소를 포함합니다. 지원 센터가 `HKEY_LOCAL_MACHINE` 경로에서 수집하는 레지스트리 및 하위 키를 변경하려면 이 요소를 사용합니다. 지원 센터는 다른 루트 레지스트리 경로에서 레지스트리 데이터 수집을 지원하지 않습니다.

#### <a name="example"></a>예
디바이스에 설치된 클래식 프로그램에 대한 레지스트리 키를 수집하려면 다음과 같은 `<add/>` 요소를 `<registryKeys>` 요소에 추가합니다. `<add key="software\\microsoft\\windows\\currentversion\\uninstall"/>`

```XML
<RegistryDataCollector>
  <registryKeys>
    <!-- Registry keys (and all subkeys) to collect -->
    <add key="software\\microsoft\\ccm"/>
    <add key="software\\microsoft\\sms"/>
    <add key="software\\microsoft\\ccmsetup"/>
    <add key="software\\microsoft\\windows\\currentversion\\uninstall"/>
  </registryKeys>
</RegistryDataCollector>
```



## <a name="bkmk_loggroups"></a> 로그 파일 그룹 사용자 지정

지원 센터가 수집하는 로그 파일 및 **로그 그룹** 목록에서 표시되는 방법을 사용자 지정하려면 `<logGroups>` 요소의 요소를 사용합니다. 지원 센터를 시작하는 경우 구성 파일의 이 섹션을 검사합니다. 그런 다음, `<logGroups>` 요소에 포함된 `<add/>` 요소에 있는 각 고유 키 특성 값에 대한 **로그 그룹** 목록에서 그룹을 만듭니다.

  - **구성 요소 로그 그룹**: `<componentLogGroup>` 요소는 키 특성을 사용하여 목록에 표시되는 로그 그룹의 이름을 정의합니다. 또한 정규식(regex)이 포함된 값 특성을 사용합니다. 이 regex를 사용하여 관련된 로그 파일의 세트를 수집합니다.  

  - **정적 로그 그룹:** `<staticLogGroup>` 요소는 키 특성을 사용하여 목록에 표시되는 로그 그룹의 이름을 정의합니다. 또한 로그 파일 이름을 정의하는 값 특성을 사용합니다.  

`<componentLogGroup>` 요소 및 `<staticLogGroup>` 요소 내에서 모두 `<add/>` 요소에 동일한 키 특성 값을 사용하는 경우 지원 센터는 단일 그룹을 만듭니다. 이 그룹에는 동일한 키를 사용하는 두 요소에 의해 정의된 로그 파일이 포함되어 있습니다.

#### <a name="example"></a>예
```XML
<logGroups>
  <componentLogGroup>
    <add key="Application Management" value="^(app.*|ci.*|contentaccess|contenttransfermanager|datatransferservice|dcm.*|execmgr.*|UserAffinity.*|.*Handler$|.*Provider$)"/>
    <add key="Client Registration" value="^(clientregistration|locationservices|ccmmessaging|ccmexec)"/>
    <add key="Inventory" value="^(ccmmessaging|inventoryagent|mtrmgr|swmtrreportgen|virtualapp|mtr.*|filesystemfile)"/>
    <add key="Policy" value="^(ccmmessaging|policyagent_.*|policyevaluator_.*)"/>
    <add key="Software Updates" value="^(ci.*|contentaccess|contenttransfermanager|datatransferservice|dcm.*|update.*|wuahandler|xmlstore|scanagent)"/>
    <add key="Software Distribution" value="^(datatransferservice|execmgr.*|contenttransfermanager|locationservices|contentaccess|filebits)"/>
    <add key="Desired Configuration Management" value="^(ci.*|dcm.*)"/>
    <add key="Operating System Deployment" value="^(ts.*)"/>
  </componentLogGroup>
  <staticLogGroup>
    <add key="Application Management" value="ccmsdkprovider.log"/>
    <add key="Desired Configuration Management" value="ccmsdkprovider.log"/>
    <add key="Software Updates" value="ccmsdkprovider.log"/>
  </staticLogGroup>
</logGroups>
```



## <a name="bkmk_wildcards"></a> 와일드카드를 사용하여 추가 로그 파일 수집

추가 로그 파일을 수집하려면 파일 경로 또는 파일 이름에 와일드카드를 사용합니다. 이러한 와일드카드에는 `%WINDIR%`과 같은 시스템 수준 환경 변수가 포함되어 있지만, `%USERPROFILE%`과 같은 사용자 범위 환경 변수는 제외됩니다. 이러한 비재귀적 로그 파일 검색을 사용하여 추가 로그 파일을 수집하려면 `<add/>` 요소 내에서 `<additionalLogFiles>` 요소를 사용합니다. 

이러한 예제는 지원 센터가 기본 구성 파일에서 이 기능을 사용하는 방법을 보여줍니다.

#### <a name="example-1-collect-all-windows-update-log-files-in-the-windows-directory"></a>예제 1: Windows 디렉터리에서 모든 Windows 업데이트 로그 파일 수집
다음 요소는 Windows 디렉터리에서 이름이 `WindowsUpdate.log`인 모든 파일을 수집합니다. 

`<add key="%WINDIR%\WindowsUpdate.log" />`

#### <a name="example-2-collect-all-log-files-in-the-windows-logs-directory"></a>예제 2: Windows Logs 디렉터리에서 모든 로그 파일 수집
다음 요소는 Windows 로그 디렉터리에서 `.log`로 끝나는 모든 파일을 수집합니다. 

`<add key="%WINDIR%\logs\*.log" />`

#### <a name="full-example-xml"></a>전체 예제 XML
```XML
<CcmLogDataCollector>
  <additionalLogFiles>
    <!-- Collect these additional log files. Can pass in a wildcard for the filename. System variables are also supported. -->
    <!--
    <add key="%WINDIR%\WindowsUpdate.log" />
    <add key="%WINDIR%\logs\*.log" />
    -->
  </additionalLogFiles>
</CcmLogDataCollector>
```
