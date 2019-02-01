---
title: 플러그 인 구성 XML
titleSuffix: Configuration Manager
description: Package Conversion Manager 플러그 인 XML 요소에 대한 기술 참조
ms.date: 08/24/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 940cc075-4066-44d5-972a-927c0b0a1143
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 8fda0e2cc2d820904e1fb9ec893c4453fe26bfc2
ms.sourcegitcommit: ef3fdf21180e43afd7af6c8264524711435e426e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54897445"
---
# <a name="technical-reference-for-the-package-conversion-manager-plug-in-configuration-xml"></a>Package Conversion Manager 플러그 인 구성 XML에 대한 기술 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1357861-->

이 문서에서는 Package Conversion Manager 플러그 인 작업을 제어하는 Configuration Manager 구성 파일(Microsoft.ConfigurationManagement.exe.config)의 XML 요소에 대해 설명합니다. 이 플러그 인을 사용하는 방법에 대한 자세한 내용은 [Package Conversion Manager 플러그 인을 사용하는 방법](/sccm/apps/pcm/how-to-use-plug-in)을 참조하세요.



## <a name="xml-configuration-elements"></a>XML 구성 요소

다음 표에서는 Package Conversion Manager 플러그 인과 관련된 Configuration Manager 구성 파일의 XML 요소에 대해 설명합니다.

|요소  |유형  |설명  |
|---------|---------|---------|
|**PcmPlugIn**|문자열|Package Conversion Manager 플러그 인으로 사용할 스크립트나 실행 파일의 이름입니다.|
|**PcmPlugInTimeoutMilliseconds**|정수|Package Conversion Manager 플러그 인 스크립트 또는 실행 파일이 패키지 처리를 완료할 때까지 기다릴 최대 시간(밀리초)입니다.|
|**PcmPluginExitCode**|정수|플러그 인 프로세스에 필요한 종료 코드입니다. 이 값은 프로세스의 성공을 나타냅니다. 기타 모든 코드는 오류로 간주됩니다.|
|**ForceRequirementsExtraction**|부울|자동 변환에서 패키지와 연결된 컬렉션 요구 사항을 사용하도록 허용합니다. 사용할 요구 사항을 결정하는 Package Conversion Manager 플러그 인을 사용할 때만 True로 설정되어야 합니다.|



## <a name="sample-configuration-xml"></a>샘플 구성 파일

이 섹션에서는 Configuration Manager 구성 파일 **Microsoft.ConfigurationManagement.exe.config**의 Package Conversion Manager 구성 XML 요소에 대한 예를 제공합니다. 기본적으로 이 파일은 다음 경로에 있습니다.  
`C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`

샘플에서 Package Conversion Manager와 관련된 요소는 `Microsoft.ConfigurationManagement.UserCentric.Workflow.Properties.Settings` 요소 내에 있습니다.

``` XML
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
...
    </Microsoft.ConfigurationManagement.AdminConsole.Properties.Settings>
    <Microsoft.ConfigurationManagement.UserCentric.Workflow.Properties.Settings>
      <setting name="DecisionVerbosity" serializeAs="String">
        <value>2</value>
      </setting>
      <setting name="PcmPlugIn" serializeAs="String">
        <value>pcmplugin.vbs</value>
      </setting>
      <setting name="PcmPlugInTimeoutMilliseconds" serializeAs="String">
        <value>10000</value>
      </setting>
      <setting name="PcmPluginExitCode" serializeAs="String">
        <value>0</value>
      </setting>
      <setting name="ForceRequirementsExtraction" serializeAs="String">
        <value>True</value >
      </setting>
    </Microsoft.ConfigurationManagement.UserCentric.Workflow.Properties.Settings>
  </applicationSettings>
...
```

