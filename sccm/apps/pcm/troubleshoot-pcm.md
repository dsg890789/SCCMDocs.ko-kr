---
title: Package Conversion Manager 문제 해결
titleSuffix: Configuration Manager
description: Configuration Manager의 Package Conversion Manager 문제를 해결하는 방법에 대해 알아봅니다.
ms.date: 08/24/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: cb616925-bb94-4b7c-a867-b3d95aef4d5e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e586990d049119c3cb00a61c56a1b84763104309
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56137901"
---
# <a name="troubleshoot-package-conversion-manager"></a>Package Conversion Manager 문제 해결

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1357861-->

이 문서의 정보를 사용하면 Package Conversion Manager를 사용할 때 발생한 문제를 해결하는 데 도움이 됩니다.



## <a name="sms-provider"></a>사이트 데이터베이스

Package Conversion Manager는 SMS 공급자를 사용합니다. 자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.

SMS 공급자가 제대로 작동하지 않으면 Package Conversion Manager를 포함한 Configuration Manager 콘솔이 작동하지 않습니다.



## <a name="package-readiness"></a>패키지 준비

패키지를 애플리케이션으로 변환하기 전에 Package Conversion Manager  **분석** 기능을 사용하여 패키지를 분석합니다. 분석 후 Configuration Manager 콘솔의 **패키지** 노드에 **준비** 열을 추가합니다. 패키지 목록에는 분석된 패키지의 준비 상태가 다음 중 하나로 표시됩니다.

 - **자동**: **변환** 기능을 사용하여 패키지를 바로 변환할 수 있습니다.      

    > [!NOTE]  
    > 자동 변환을 수행해도 WQL 쿼리는 애플리케이션 요구 사항으로 변환되지 않습니다. 이러한 쿼리를 변환하려면 **수정 및 변환** 프로세스를 사용합니다.  

 - **수동**: **수정 및 변환** 기능을 사용하여 패키지를 변환하려면 먼저 패키지에 일부 추가 또는 변경이 있어야 합니다.  

 - **해당 없음**: 패키지가 변환에 적합하지 않습니다. 이러한 패키지의 경우 문제를 해결하거나 계속해서 패키지로 배포할 수 있습니다.  

 - **오류**: 패키지에 오류가 있습니다. 분석하고 변환하려면 먼저 수동으로 이러한 오류를 수정합니다.  

Configuration Manager 콘솔의 **패키지** 노드 세부 정보 창은 준비 문제를 보여 줍니다. 패키지를 선택하고 세부 정보 창에서 **요약** 탭을 선택합니다.



## <a name="log-files"></a>로그 파일

### <a name="enable-logging"></a>로깅 사용

Package Conversion Manager에 대해 로깅을 사용하면 해당 작업, 예외 및 오류를 모두 기록합니다. 

Configuration Manager의 이 구성 요소에 대해 로깅을 사용하려면 **Microsoft.ConfigurationManagement.exe.Config**를 수정합니다. 기본적으로 이 구성 파일은 다음 경로에 있습니다.  
`C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`  

**system.diagnostics** 요소에서 마지막 **sources** 요소 뒤에 다음 **switches** 및 **trace** XML 요소를 삽입합니다.

``` XML
</sources>

    <switches>
      <add name="PcmLogging" value="3"/>
    </switches>
    <trace autoflush="true" indentsize="4">
      <listeners>
        <add name="PcmTraceListener" type="Microsoft.ConfigurationManagement.UserCentric.Logging.RolloverLogTraceListener, Microsoft.ConfigurationManagement.UserCentric.Logging" initializeData="%UserProfile%\AppData\Local\Temp\PcmTrace.log"/>
      </listeners>
    </trace>

</system.diagnostics>
```

이 샘플에서는 **PCMTrace.log** 파일을 사용합니다. 이 로그는 Configuration Manager 콘솔을 실행하는 컴퓨터의 다음 경로에 있습니다.  
`%UserProfile%\AppData\Local\Temp`

세부 정보 수준을 구성하려면 **PcmLogging** 추적 스위치 설정을 변경합니다. 가장 간단한 수준(`1`)부터 가장 자세한 수준(`4`)까지 4가지 세부 정보 수준으로 이 값을 설정합니다.


### <a name="smsprovlog"></a>SMSProv.log

패키지 변환 프로세스 문제 해결과 관련된 정보가 **SMSProv.log** 파일에 있는 경우도 있습니다. 이 파일은 Configuration Manager SMS 공급자의 정보를 캡처합니다.

기본적으로 이 로그 파일은 다음 경로의 Configuration Manager 사이트 서버에 있습니다.  
`C:\Program Files\Microsoft Configuration Manager\Logs`

다음 오류 메시지 중 하나가 표시되면 **SMSProv.log** 파일에 관련 문제 해결 정보가 포함되어 있을 수 있습니다.

- `The SMS Provider reported an error`

- `Generic Failure`

이러한 오류 메시지는 일반적으로 사이트 서버에 오류가 발생했으며 오류 정보가 Configuration Manager 콘솔로 전송되지 않았음을 나타냅니다.

자세한 내용은 [Package Conversion Manager 오류 메시지에 대한 기술 참조](/sccm/apps/pcm/error-messages)를 참고하세요.



## <a name="changing-package-attributes-after-analysis"></a>분석 후 패키지 특성 변경

패키지를 분석하고 준비 상태가 **자동** 또는 **수동**이 된 후 관련 특성을 변경하면 변환 프로세스가 실패할 수 있습니다.

예를 들어, 패키지를 분석하고 준비 상태가 **자동**인데 패키지에 다른 프로그램을 추가하는 경우 패키지 변환에 실패할 수 있습니다.

분석 후 패키지를 변경해야 하는 경우, 분석을 다시 실행한 후 변환하세요. 



## <a name="see-also"></a>참고 항목

[Package Conversion Manager 오류 메시지에 대한 기술 참조](/sccm/apps/pcm/error-messages)
