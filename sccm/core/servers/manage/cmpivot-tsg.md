---
title: CMPivot 문제 해결
titleSuffix: Configuration Manager
description: Configuration Manager에서 CMPivot 문제를 해결하는 방법을 알아봅니다.
ms.date: 10/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 36385bea-f05e-4300-947f-cb3927b3bac5
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ea58a234c6de90b57bee0de6ad04b92b32e6263
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72303876"
---
# <a name="troubleshoot-cmpivot"></a>CMPivot 문제 해결

CMPivot은 사용자 환경에 있는 디바이스의 실시간 상태에 액세스할 수 있는 도구입니다. CMPivot은 대상 컬렉션에 있는 현재 연결된 모든 디바이스에 대해 쿼리를 실행하고 결과를 반환합니다.

경우에 따라 CMPivot 문제를 해결해야 할 수도 있습니다. 예를 들어 클라이언트에서 CMPivot에 보내는 상태 메시지가 손상된 경우 사이트 서버가 메시지를 처리할 수 없습니다. 이 문서에서는 CMPivot에 대한 정보의 흐름을 이해하도록 도와줍니다.

## <a name="bkmk_CMPivot-1902"></a> CMPivot 버전 1902 이상 문제 해결

System Center Configuration Manager 버전 1902 이상에서는 계층 구조의 CAS(중앙 관리 사이트)에서 CMPivot을 실행할 수 있습니다. 기본 사이트는 계속 클라이언트 통신을 처리합니다.

CAS에서 CMPivot을 실행하는 경우 CMPivot은 고속 메시지 구독 채널을 사용하여 기본 사이트와 통신합니다. CMPivot은 사이트 간 표준 SQL 복제를 사용하지 않습니다. SQL Server 인스턴스 또는 SQL 공급자가 원격이거나 SQL Server Always On을 사용하는 경우 CMPivot에 대해 “더블홉 시나리오”가 제공됩니다. “이중 홉 시나리오”의 제한된 위임을 정의하는 방법에 대한 자세한 내용은 [CMPivot 버전 1902부터 가능](/sccm/core/servers/manage/cmpivot#bkmk_cmpivot1902)을 참조하세요.

>[!IMPORTANT]
> CMPivot의 문제를 해결할 때 자세한 정보를 확인하려면 MP(관리 지점) 및 사이트 서버의 SMS_MESSAGE_PROCESSING_ENGINE에서 자세한 정보 로깅을 사용하도록 설정합니다. 또한 클라이언트의 출력이 80KB보다 큰 경우 MP 및 사이트 서버의 SMS_STATE_SYSTEM 구성 요소에서 자세한 정보 로깅을 사용하도록 설정합니다. 자세한 정보 로깅을 사용하도록 설정하는 방법은 [사이트 서버 로깅 옵션](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_reg-site)을 참조하세요.

### <a name="get-information-from-the-site-server"></a>사이트 서버에서 정보 가져오기

기본적으로 사이트 서버 로그 파일은 `C:\Program Files\Microsoft Configuration Manager\logs`에 있습니다. 이 위치는 비기본 설치 디렉터리를 지정하거나 SMS 공급자 같은 항목을 다른 서버에 오프로드한 경우 달라질 수 있습니다. CAS에서 CMPivot을 실행하는 경우 로그는 기본 사이트 서버에 위치합니다.

`smsprov.log`에서 다음 줄을 찾습니다.

- Configuration Manager 버전 1906:
  <pre><code lang="Log">Auditing: User &ltusername> initiated client operation 145 to collection &ltCollectionId>. </code></pre>

- Configuration Manager 버전 1902:
  <pre><code lang="Log">Type parameter is 135.
  Auditing: User &ltusername> ran script 7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14 with hash dc6c2ad05f1bfda88d880c54121c8b5cea6a394282425a88dd4d8714547dc4a2 on collection &ltCollectionId>. </code></pre>

 `7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14`는 CMPivot의 스크립트 GUID입니다. [CMPivot 감사 상태 메시지](/sccm/core/servers/manage/cmpivot#cmpivot-audit-status-messages)에서 GUID를 확인할 수도 있습니다.

다음으로 CMPivot 창에서 ID를 찾습니다. 이 ID는 `ClientOperationID`입니다.

![ClientOperationID를 강조 표시한 CMPivot 창](media/cmpivot-client-operationid-1902.png)

ClientAction 테이블에서 `TaskID`를 찾습니다. `TaskID`는 ClientAction 테이블의 `UniqueID`에 해당합니다.

``` SQL
select * from ClientAction where ClientOperationId=<id>
```

`BgbServer.log`에서 SQL에서 수집한 `TaskID`를 찾고 `PushID`를 적어 둡니다. `TaskID`가 `TaskGUID`로 레이블이 지정됩니다. 예:

<pre><code lang="Log">Starting to send push task (<b>PushID: 9</b> TaskID: 12 <b>TaskGUID: 9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0</b> TaskType: 15 TaskParam: PFNjcmlwdENvbnRlbnQgU2NyaXB0R3VpZD0nN0RDNkI2RjEtRTdGNi00M0MxL (truncated log entry)
Finished sending push task (<b>PushID: 9</b> TaskID: 12) to 2 clients
</code></pre>

### <a name="client-logs"></a>클라이언트 로그

사이트 서버의 정보를 얻은 후 클라이언트 로그를 확인합니다. 기본적으로 클라이언트 로그는 `C:\Windows\CCM\Logs`에 있습니다.

`CcmNotificationAgent.log`에서 다음 줄과 비슷한 로그 항목을 찾습니다.  

<pre><code lang="Log">Receive task from server with <b>pushid=9</b>, taskid=12, <b>taskguid=9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0</b>, tasktype=15 and taskParam=PFNjcmlwdEhhc2ggU2NyaXB0SGF (truncated log entry)
Send Task response message &ltBgbResponseMessage TimeStamp="2019-09-13T17:29:09Z"><b>&ltPushID>5</b>&lt/PushID>&ltTaskID>4&lt/TaskID>&ltReturnCode>1&lt/ReturnCode>&lt/BgbResponseMessage> successfuly.
 </code></pre>

`Scripts.log`에서 `TaskID`를 확인합니다. 다음 예에서는 `Task ID`  `{9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0}`이 표시됩니다.

<pre><code lang="Log">Sending script state message (fast): <b>{9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0}</b>
Result are sent for ScriptGuid: 7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14 and <b>TaskID: {9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0}</b>
</code></pre>

> [!NOTE]
> `Scripts.log`에 "(fast)"가 표시되지 않는 경우 데이터가 80KB를 초과하기 때문일 수 있습니다. 이 경우 정보가 상태 메시지로 사이트 서버에 전송됩니다. 클라이언트의 `StateMessage.log` 및 사이트 서버의 `Statesys.log`를 사용하세요.

### <a name="review-messages-on-the-site-server"></a>사이트 서버에서 메시지 검토

관리 지점에서 [자세한 정보 로깅](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_reg-client)을 사용하도록 설정한 경우 수신 클라이언트 메시지가 처리되는 방법을 확인할 수 있습니다. `MP_RelayMsgMgr.log`에서 `TaskID`를 찾습니다.

`MP_RelayMsgMgr.log` 예에서 클라이언트의 ID `(GUID:83F67728-2E6D-4E4F-8075-ED035C31B783)`과 `Task ID {9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0}`을 볼 수 있습니다. 메시지 ID는 메시지 처리 엔진으로 전송되기 전에 클라이언트의 응답에 할당됩니다.

<pre><code lang="Log">MessageKey: GUID:83F67728-2E6D-4E4F-8075-ED035C31B783<b>{9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0}</b>
Create message succeeded for <b>message id 22f00adf-181e-4bad-b35e-d18912f39f89</b>
Add message payload succeeded for message id 22f00adf-181e-4bad-b35e-d18912f39f89
Put message succeeded for message id 22f00adf-181e-4bad-b35e-d18912f39f89
CRelayMsgMgrHandler::HandleMessage(): ExecuteTask() succeeded
</code></pre>

`SMS_MESSAGE_PROCESSING_ENGINE.log`에서 [자세한 정보 로깅](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_logoptions)을 사용하도록 설정한 경우 클라이언트 결과가 처리됩니다. `MP_RelayMsgMgr.log`에서 찾은 메시지 ID를 사용하세요. 처리 로그 항목은 다음 예와 비슷합니다.

<pre><code lang="Log">Processing 2 messages with type Instant and IDs <b>22f00adf-181e-4bad-b35e-d18912f39f89[19]</b>, 434d80ae-09d4-4d84-aebf-28a4a29a9852[20]...
Processed 2 messages with type Instant. Failed to process 0 messages. All message IDs <b>22f00adf-181e-4bad-b35e-d18912f39f89[19]</b>, 434d80ae-09d4-4d84-aebf-28a4a29a9852[20]
</code></pre>

> [!TIP]
> 처리 중 예외가 발생하는 경우 다음 SQL 쿼리를 실행하고 예외 열에서 확인하여 검토할 수 있습니다. 처리된 메시지는 더 이상 `MPE_RequestMessages_Instant` 테이블에 표시되지 않습니다.
>
> ```SQL
> select * from MPE_RequestMessages_Instant where MessageID=<ID from SMS_MESSAGE_PROCESSING_ENGINE.log>
> ```

`BgbServer.log`에서 `PushID`를 찾아 보고되거나 실패한 클라이언트 수를 확인합니다.

<pre><code lang="Log">Generated BGB task status report c:\ConfigMgr\inboxes\bgb.box\Bgb5c1db.BTS at 09/16/2019 16:46:39. (<b>PushID: 9</b> ReportedClients: 2 FailedClients: 0)
</code></pre>

`TaskID`를 사용하여 SQL에서 CMPivot에 대한 모니터링 보기를 확인합니다.

``` SQL
select * from vSMS_CMPivotStatus where TaskID='{9A4E59D2-2F5B-4067-A9FA-B99602A3A4A0}'
```

[ ![버전 1902의 문제 해결을 위한 CMPivot SQL 쿼리](media/cmpivot-sql-queries-1902.png)](media/cmpivot-sql-queries-1902.png#lightbox)

## <a name="bkmk_CMPivot-1810"></a> 1810 및 이전 버전의 CMPivot 문제 해결

Configuration Manager 버전 1810 및 이전 버전에서는 사이트 서버가 클라이언트와의 통신을 처리합니다.

### <a name="get-information-from-the-site-server"></a>사이트 서버에서 정보 가져오기

기본적으로 사이트 서버 로그 파일은 `C:\Program Files\Microsoft Configuration Manager\logs`에 있습니다. 이 위치는 비기본 설치 디렉터리를 지정하거나 SMS 공급자 같은 항목을 다른 서버에 오프로드한 경우 달라질 수 있습니다.

`smsprov.log`에서 다음 줄을 찾습니다.

<pre><code lang="Log">Auditing: User <username> initiated client operation 135 to collection &ltCollectionId>.
</code></pre>

CMPivot 창에서 ID를 찾습니다. 이 ID는 `ClientOperationID`입니다.

![ClientOperationID를 강조 표시한 CMPivot 창](media/cmpivot-clientoperationid.png)

ClientAction 테이블에서 `TaskID`를 찾습니다. `TaskID`는 ClientAction 테이블의 `UniqueID`에 해당합니다.

``` SQL
select * from ClientAction where ClientOperationId=<id>
```

`BgbServer.log`에서 SQL에서 수집한 `TaskID`를 찾습니다. `TaskGUID`로 레이블이 지정되어 있습니다. 예:

<pre><code lang="Log">Starting to send push task (PushID: 260 TaskID: 258 TaskGUID: <b>F8C7C37F-B42B-4C0A-B050-2BB44DF1098A</b> TaskType: 15
TaskParam: PFNjcmlwdEhhc2ggU2NyaXB0SGF...truncated...to 5 clients with throttling (strategy: 1 param: 42)
Finished sending push task (PushID: 260 TaskID: 258) to 5 clients
</code></pre>

### <a name="client-logs"></a>클라이언트 로그

사이트 서버의 정보를 얻은 후 클라이언트 로그를 확인합니다. 기본적으로 클라이언트 로그는 `C:\Windows\CCM\Logs`에 있습니다.

`CcmNotificationAgent.log`에서 다음 항목과 비슷한 로그를 찾습니다.  

<pre><code lang="Log"><b>Error! Bookmark not defined.</b>+PFNjcmlwdEhhc2ggU2NyaXB0SGFzaEFsZz0nU0hBMjU2Jz42YzZmNDY0OGYzZjU3M2MyNTQyNWZiNT
g2ZDVjYTIwNzRjNmViZmQ1NTg5MDZlMWI5NDRmYTEzNmFiMDE0ZGNjPC9TY3JpcHRIYXNoPjxTY3Jp (truncated log entry)
</code></pre>

`Scripts.log`에서 `TaskID`를 찾습니다. 다음 예에서는 `Task ID {F8C7C37F-B42B-4C0A-B050-2BB44DF1098A}`가 표시됩니다.

<pre><code lang="Log">Sending script state message: 7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14
State message: Task Id <b>{F8C7C37F-B42B-4C0A-B050-2BB44DF1098A}</b>
</code></pre>

`StateMessage.log`에서 찾습니다. 다음 예에서는 `TaskID`가 `<Param>` 옆의 메시지 아래쪽 근처에 있는 것을 볼 수 있습니다.

``` XML
StateMessage body: <?xml version="1.0" encoding="UTF-16"?>
<Report><ReportHeader><Identification><Machine><ClientInstalled>1</ClientInstalled><ClientType>1
</ClientType><ClientID>GUID:DBAC52C9-57E6-47D7-A8D6-E0A5A64B57E6</ClientID><ClientVersion>5.00.8670.1000</ClientVersion>
<NetBIOSName>R613924</NetBIOSName><CodePage>437</CodePage>
<SystemDefaultLCID>1033</SystemDefaultLCID><Priority>0</Priority></Machine></Identification>
<ReportDetails><ReportContent>State Message Data</ReportContent><ReportType>Full</ReportType>
<Date>20180703184447.673000+000</Date><Version>1.0</Version><Format>1.0</Format>
</ReportDetails></ReportHeader><ReportBody><StateMessage MessageTime="20180703184447.517000+000"><Topic ID="7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14" Type="9003" IDType="0" User="" UserSID=""/><State ID="1" Criticality="0"/>
<StateDetails Type="1"><![CDATA["PAA/AHgAbQBsACAAdgBlAHIAcwBpAG8AbgA9ACIAMQAuADAAIgAgAGUAbgBjAG8AZABpAG4AZwA9ACIAdQB0AGYALQAxADYAIgA/AD4APAByAGUAcwB1AGwAdAAgAFIAZQBzAHUAbAB0AEMAbwBkAGUAPQAiADAAIgA+ADwAZQAgAE4AYQBtAGUAPQAiAEkAbgB0AGUAbAAoAFIAKQAgAFgAZQBvAG4AKABSACkAIABDAFAAVQAgAEUANQAtADIANgA3ADMAIAB2ADQAIABAACAAMgAuADMAMABHAEgAegAiACAATQBhAG4AdQBmAGEAYwB0AHUAcgBlAHIAPQAiAEEAbQBlAHIAaQBjAGEAbgAgAE0AZQBnAGEAdAByAGUAbgBkAHMAIABJAG4AYwAuACIAIABWAGUAcgBzAGkAbwBuAD0AIgBWAFIAVABVAEEATAAgAC0AIAA2ADAAMAAxADcAMAAyACIAIABSAGUAbABlAGEAcwBlAEQAYQB0AGUAPQAiADIAMAAxADcALQAwADYALQAwADIAIAAwADAAOgAwADAAOgAwADAAIgAgAFMAZQByAGkAYQBsAE4AdQBtAGIAZQByAD0AIgAwADAAMAAwAC0AMAAwADEAOAAtADMANgA4ADIALQA0ADcAMAA4AC0ANwA2ADQAMAAtADcANgAwADAALQAzADMAIgAgAFMATQBCAEkATwBTAEIASQBPAFMAVgBlAHIAcwBpAG8AbgA9ACIAMAA5ADAAMAAwADcAIAAiACAALwA+ADwALwByAGUAcwB1AGwAdAA+AA=="~~]]></StateDetails><UserParameters Flags="0" Count="2">
<Param>{F8C7C37F-B42B-4C0A-B050-2BB44DF1098A}</Param><Param>0</Param></UserParameters></StateMessage></ReportBody></Report>

Successfully forwarded State Messages to the MP StateMessage 7/3/2018 11:44:47 AM 5036 (0x13AC)
```

### <a name="review-messages-on-the-site-server"></a>사이트 서버에서 메시지 검토

`statesys.log`를 열어 메시지가 수신되고 처리되는지 확인합니다. 다음 예에서는 `<Param>` 옆의 메시지 아래쪽 근처에서 `TaskID`를 볼 수 있습니다. 이 로그 항목을 보려면 SMS_STATE_SYSTEM 구성 요소에서 [자세한 정보 로깅](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_logoptions)을 사용하도록 설정합니다.

``` XML
CMessageProcessor - the cmdline to DB exec dbo.spProcessStateReport N'?<?xml version="1.0" encoding="UTF-
16"?>~~<Report><ReportHeader><Identification><Machine><ClientInstalled>1</ClientInstalled><ClientType>1
</ClientType><ClientID>GUID:DBAC52C9-57E6-47D7-A8D6-E0A5A64B57E6</ClientID><ClientVersion>5.00.8670.1000</ClientVersion>
<NetBIOSName>R613924</NetBIOSName><CodePage>437</CodePage>
<SystemDefaultLCID>1033</SystemDefaultLCID><Priority>0</Priority></Machine></Identification>
<ReportDetails><ReportContent>State Message Data</ReportContent><ReportType>Full</ReportType>
<Date>20180703184447.673000+000</Date><Version>1.0</Version><Format>1.0</Format>
</ReportDetails></ReportHeader><ReportBody><StateMessage MessageTime="20180703184447.517000+000"><Topic ID="7DC6B6F1-E7F6-43C1-96E0-E1D16BC25C14" Type="9003" IDType="0" User="" UserSID=""/><State ID="1" Criticality="0"/>
<StateDetails Type="1"><![CDATA["PAA/AHgAbQBsACAAdgBlAHIAcwBpAG8AbgA9ACIAMQAuADAAIgAgAGUAbgBjAG8AZABpAG4AZwA9ACIAdQB0AGYALQAxADYAIgA/AD4APAByAGUAcwB1AGwAdAAgAFIAZQBzAHUAbAB0AEMAbwBkAGUAPQAiADAAIgA+ADwAZQAgAE4AYQBtAGUAPQAiAEkAbgB0AGUAbAAoAFIAKQAgAFgAZQBvAG4AKABSACkAIABDAFAAVQAgAEUANQAtADIANgA3ADMAIAB2ADQAIABAACAAMgAuADMAMABHAEgAegAiACAATQBhAG4AdQBmAGEAYwB0AHUAcgBlAHIAPQAiAEEAbQBlAHIAaQBjAGEAbgAgAE0AZQBnAGEAdAByAGUAbgBkAHMAIABJAG4AYwAuACIAIABWAGUAcgBzAGkAbwBuAD0AIgBWAFIAVABVAEEATAAgAC0AIAA2ADAAMAAxADcAMAAyACIAIABSAGUAbABlAGEAcwBlAEQAYQB0AGUAPQAiADIAMAAxADcALQAwADYALQAwADIAIAAwADAAOgAwADAAOgAwADAAIgAgAFMAZQByAGkAYQBsAE4AdQBtAGIAZQByAD0AIgAwADAAMAAwAC0AMAAwADEAOAAtADMANgA4ADIALQA0ADcAMAA4AC0ANwA2ADQAMAAtADcANgAwADAALQAzADMAIgAgAFMATQBCAEkATwBTAEIASQBPAFMAVgBlAHIAcwBpAG8AbgA9ACIAMAA5ADAAMAAwADcAIAAiACAALwA+ADwALwByAGUAcwB1AGwAdAA+AA=="~~]]></StateDetails><UserParameters Flags="0" Count="2">
<Param>{F8C7C37F-B42B-4C0A-B050-2BB44DF1098A}</Param><Param>0</Param></UserParameters></StateMessage></ReportBody></Report>~~'
```

메시지가 처리되지 않았다면 상태 메시지 받은 편지함을 확인합니다. 기본 받은 편지함 위치는 `C:\Program Files\Microsoft Configuration Manager\inboxes\auth\statesys.box\`입니다. 다음 위치에서 파일을 찾습니다.

- 수신 중
- 손상됨
- 프로세스

`TaskID`를 사용하여 SQL에서 CMPivot에 대한 모니터링 보기를 확인합니다.

``` SQL
select * from vSMS_CMPivotStatus where TaskID='{F8C7C37F-B42B-4C0A-B050-2BB44DF1098A}'
```

>[!NOTE]
>버전 1810 이상을 사용하는 클라이언트의 경우, 출력이 80KB보다 크지 않는 한 상태 메시지가 사용되지 않습니다. 이 사례에서 CMPivot의 문제를 해결할 때 MP 및 사이트 서버의 SMS_MESSAGE_PROCESSING_ENGINE에서 자세한 정보 로깅을 사용하도록 설정하면 추가 정보를 얻을 수 있습니다. 자세한 정보 로깅을 사용하도록 설정하는 방법은 [사이트 서버 로깅 옵션](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_reg-site)을 참조하세요.
>
> 문제를 해결하려면 다음 로그를 참조하세요.
>
> - `MP_Relay.log`
> - `SMS_MESSAGE_PROCESSING_ENGINE.log`

## <a name="next-steps"></a>다음 단계

- [CMPivot 사용](/sccm/core/servers/manage/cmpivot)
- [PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)
