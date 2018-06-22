---
title: SCAP 준수 설정 가져오기
titleSuffix: Configuraton Manager
description: SCAP 준수 설정을 구성 기준으로 가져와서 결과 내보내기
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 0bdcb018-bac2-4540-b786-6242bac73ff4
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 1f6b1fa0dd0775083eff9925a65509083b3f47d3
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32336615"
---
# <a name="import-the-compliance-settings-compliant-cab-files-into-system-center-configuration-manager"></a>준수 설정을 준수하는 .cab 파일을 System Center Configuration Manager로 가져오기

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Tip]  
> 이 기능은 기술 미리 보기 버전 1803에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 도입되었습니다. SCAP 확장의 이 시험판 버전은 현재 지원되는 모든 버전의 Configuration Manager 현재 분기 및 LTSB 1606에 설치할 수 있습니다. 설치 파일은 1803 미리 보기부터 cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi에 있습니다. 

이 프로세스의 다음 단계에서는 Configuration Manager 콘솔을 사용하여 준수 설정 규격 .cab 파일을 Configuration Manager로 가져옵니다. 이 프로세스의 앞부분에서 만든 .cab 파일을 가져올 때는 Configuration Manager 데이터베이스에 하나 이상의 구성 항목과 구성 기준이 작성됩니다. 프로세스 뒷부분에서는 Configuration Manager에서 각 구성 기준을 컴퓨터 컬렉션에 할당할 수 있습니다.

## <a name="to-import-the-compliance-settings-compliant-cab-files-into-configuration-manager"></a>준수 설정 규격 .cab 파일을 Configuration Manager로 가져오려면

1. **Configuration Manager 콘솔**을 엽니다.
2. **Configuration Manager 콘솔의 탐색 창에서 **자산 및 준수**>  **준수 설정** > **구성 기준**으로 이동합니다.

3. 작업 창에서 **구성 데이터 가져오기**를 클릭하여 구성 데이터 가져오기 마법사를 시작합니다.

1. 아래 표의 정보를 참조하여 **구성 데이터 가져오기 마법사**를 완료합니다. 별도로 지정된 경우가 아니면 기본값을 그대로 사용합니다.



구성 데이터 가져오기 마법사 프로세스

| 마법사 페이지 이름 | 사용자 작업 |
| --- | --- |
| **파일 선택** |1. **추가**를 클릭합니다. </br>열기 대화 상자가 나타납니다.|
||2. **열기** 대화 상자에서 **&lt;규격 cab 출력\_폴더 &gt;** 로 이동합니다. Sces.ScapToDcm.exe 도구를 실행할 때 _compliant cab **출력\_폴더**가 –output 스위치 다음에 지정된 폴더인 경우 **&lt; 규격\_cab&gt;**.cab 파일을 클릭합니다. **규격\_파일**은 이전에 프로세스에서 만든 .cab 파일의 이름입니다. 그런 다음, **열기**를 클릭합니다. </br> Configuration Manager 콘솔 – 보안 경고 대화 상자가 나타납니다.|
||3. **Configuration Manager 콘솔 – 보안 경고** 대화 상자에서 **실행**을 클릭합니다. 파일 선택 페이지에서 가져올 기준 목록에 구성 데이터가 나타납니다.|
||3. **다음**을 클릭합니다.|
| **요약** |5. **다음**을 클릭합니다. |
| **구성 데이터 가져오기 마법사 완료** |6. **닫기**를 클릭합니다. |

새 구성 기준이 Configuration Manager 콘솔의 정보 창에 나타납니다.

>[!IMPORTANT]
> 프로세스 앞부분에서 만든 각 .cab 파일에 대해 이 프로세스를 반복해야 합니다. NVD 웹 사이트에서 다운로드한 XCCDF/DataStream XML 파일에 선택된 각 프로필에 대한 .cab 파일이 있습니다. Microsoft.Sces.ScapToDcm.exe 도구를 실행하면 이 파일을 처리할 수 있습니다.

가져온 구성 기준은 읽기 전용이며 상태는 &#39;사용&#39;이고 초기 배포된 상태는 &#39;아니요&#39;입니다.  &#39;수정한 날짜&#39; 속성은 기준을 가져온 시간을 나타냅니다.  구성 기준의 이름은 XCCDF/DataStream XML의 표시 이름 섹션에서 가져옵니다. 이름은

ABC[XYZ] 규칙을 사용하여 생성됩니다. 여기서 ABC는 XCCDF 벤치마크 ID이고 XYZ는 XCCDF 프로필 ID입니다(프로필을 선택한 경우).



## <a name="assign-configuration-baselines-to-the-computer-collections"></a>컴퓨터 컬렉션에 구성 기준 할당

SCAP 준수를 평가하려는 컴퓨터에 대해 적합한 컴퓨터 컬렉션을 만든 후에는 가져온 구성 기준을 할당하여 컴퓨터 컬렉션과 연결할 수 있습니다. 이 섹션에는 Configuration Manager 콘솔을 사용하여 컴퓨터 컬렉션에 구성 기준을 할당하는 방법이 나와 있습니다.

구성 기준을 컴퓨터 컬렉션에 할당하려면

1. **Configuration Manager** **콘솔**을 엽니다.

2. **Configuration Manager 콘솔의 탐색 창에서 **자산 및 준수** > **준수 설정** >** 구성 기준**으로 이동합니다.
3. 탐색 창에서 &lt;**구성\_기준>을 클릭합니다. 여기서 &lt;_구성\_기준&gt;_ 은 컴퓨터 컬렉션에 할당하려는 구성 기준의 이름입니다.

    구성 기준에 대한 구성 항목 목록이 Configuration Manager의 정보 창에 표시됩니다.

4. 작업 창에서 **배포**를 클릭합니다.

5. 아래 표의 정보를 참조하여 **구성 기준** **배포** **대화 상자**에 필요한 사항을 모두 입력합니다. 별도로 지정된 경우가 아니면 기본값을 그대로 사용합니다.

### <a name="deploy-configuration-baseline-dialog-process"></a>구성 기준 배포 대화 상자 프로세스

| 마법사 페이지 이름 | 사용자 작업 |
| --- | --- |
| **컬렉션 선택** | 1. **찾아보기**를 클릭합니다.|
||2. **컬렉션 선택** 대화 상자에서 **장치 컬렉션**을 선택합니다. 그런 다음, **&lt;컴퓨터\_컬렉션&gt;** 을 클릭합니다. 여기서 &lt;_컴퓨터\_컬렉션&gt;_ 은 이전에 프로세스에서 만든 컴퓨터 컬렉션의 이름입니다. **확인**을 클릭합니다.|
| **일정 설정** |3. 조직에 적합한 일정을 선택합니다.|
 
>[!IMPORTANT]
> 각 구성 기준을 할당하려는 각 컴퓨터 컬렉션에 대해 이 프로세스를 반복합니다. 최소한 각 구성 기준을 컴퓨터 컬렉션 하나 이상에 할당합니다.

## <a name="verify-that-the-compliance-data-has-been-collected"></a>준수 데이터가 수집되었는지 확인

준수 데이터를 다시 SCAP 형식으로 내보내기 전에 데이터가 수집되었는지 확인해야 합니다. 구성 기준을 컴퓨터 컬렉션에 할당하고 나면 해당 컬렉션의 각 컴퓨터에 설치된 Configuration Manager 클라이언트가 준수 정보를 자동으로 수집합니다. 이렇게 수집된 준수 정보는 Configuration Manager 데이터베이스에 저장됩니다.

Configuration Manager에서 구성 기준 배포 상태를 보면 Configuration Manager 클라이언트가 적합한 데이터를 수집했는지 확인할 수 있습니다. Configuration Manager에서 적합한 준수 데이터가 수집된 경우 프로세스 뒷부분에서 만들 XCCDF/DataStream 결과 파일의 유효성을 검사하는 데 사용할 수 있으므로 데이터 수집 여부를 반드시 확인해야 합니다.



### <a name="verify-that-the-compliance-data-has-been-collected"></a>준수 데이터가 수집되었는지 확인

1. Configuration Manager 콘솔을 엽니다.
2. Configuration Manager 콘솔의 탐색 창에서 **모니터링** > **배포**로 이동합니다.
3. **기능 유형**을 클릭하여 배포 유형을 정렬한 다음, 목록에서 유형이 **기준**인 항목을 찾습니다.
4. 목록에서 방금 컬렉션에 배포한 &lt;구성\_기준&gt;을 마우스 오른쪽 단추로 클릭하고 **상태 보기**를 클릭합니다.
5. 그런 다음, &lt;구성\_기준&gt; 노드로 이동하여 준수 상태를 확인합니다. 알 수 없는 상태의 컴퓨터가 있으면 해당 컴퓨터에 대해 준수 데이터 수집이 아직 완료되지 않은 것입니다.

### <a name="validate-the-xccdfdatastream-results"></a>XCCDF/Datastream 결과 유효성 검사

1. Configuration Manager 콘솔을 엽니다.
2. Configuration Manager 콘솔의 탐색 창에서 **준수 설정** > **SCAP 대시보드**로 이동합니다.
3. 구성 기준, 할당, SCAP 파일, 데이터 스트림, 벤치마크 및 프로필(있는 경우)을 선택합니다.
4. **보고서 표시**
 ![SCAP 보고서](./media/scap-report.png)를 클릭합니다.



## <a name="export-compliance-results-to-scap-format"></a>준수 결과를 SCAP 형식으로 내보내기

이 프로세스의 다음 작업에서는 준수 설정 준수 데이터를 SCAP 형식(XML/사람이 읽을 수 있는 형식의 ARF 보고서 파일)으로 내보냅니다. SCAP 확장 내보내기 마법사 및 Microsoft.Sces.DcmToScap.exe 도구는 각 준수 설정 구성 기준에 대한 별도의 XCCDF/DataStream ARF 결과 파일을 내보냅니다. 이러한 파일은 Microsoft.Sces.ScapToDcm.exe 도구가 각 준수 설정 구성 기준을 만드는 데 사용하는 각 XCCDF/DataStream 입력 파일에 해당합니다.

### <a name="export-the-compliance-settings-compliance-data-using-the-export-scap-report-wizard"></a>SCAP 보고서 내보내기 마법사를 사용하여 준수 설정 준수 데이터 내보내기

1. SCAP 대시보드의 오른쪽 클릭 메뉴에서 SCAP 보고서 내보내기 마법사를 시작합니다.
![SCAP 대시보드에서 가져오기](./media/import-from-scap-dashboard.png)

2. 구성 기준 및 할당 선택 ![기준 선택](./media/select-ci-baseline.png)

3. SCAP 데이터 스트림 파일, XCCDF/CPE 파일 또는 Oval 콘텐츠 및 변수 파일의 위치를 선택합니다.
![데이터 스트림 선택](./media/export-scap-report-datastream.png)

4. 조직 이름을 지정하고 SCAP 보고서를 내보낼 폴더 위치를 선택합니다.
 ![데이터 스트림 선택](./media/specify-org-export.png)

5. 설정을 확인합니다.
 ![데이터 스트림 선택](./media/confirm-export.png)

6. **다음을 선택하여 보고서를 내보냅니다.  진행률 표시줄 및 완료 페이지가 차례로 나타납니다.
 ![내보내기 완료](./media/complete-report-export.png)



### <a name="alternate-method-export-the-compliance-settings-compliance-data-using-the-microsoftscesdcmtoscapexe-tool"></a>(대체 방법) Microsoft.Sces.DcmToScap.exe 도구를 사용하여 준수 설정 준수 데이터 내보내기

1. 명령 프롬프트에서 AdminConsole\Bin 폴더로 이동하여 다음 표에 나와 있는 명령줄 매개 변수를 입력한 다음, **Enter 키를 누릅니다.

    >[!NOTE] 
    >사용자 계정에 Configuration Manager 공급자에 대한 읽기 권한이 있어야 하며, 명령줄의 -out 매개 변수에 지정된 출력 폴더에 대한 쓰기 권한도 있어야 합니다.

**SCAP 1.0/1.1 콘텐츠(예: USGCB 및 DISA 콘텐츠)의 경우:**

Microsoft.Sces.DcmToScap.exe -baseline BaselineCIID -assignment AssignmentID –xccdf &lt;xccdf.xml&gt; -cpe &lt;cpe.xml&gt;  -select &lt;xccdfBenchmark/profile&gt; -out &lt;outputResultFolder&gt;  [-log logFileName]

  >[!NOTE] 
    >콘텐츠에 벤치마크/프로필이 여러 개 있는 경우 –select 매개 변수를 사용하여 클라이언트에서 평가한 벤치마크/프로필을 지정해야 합니다.

**SCAP1.2 콘텐츠(예: 최신 USGCB 콘텐츠)의 경우:**

Microsoft.Sces.DcmToScap.exe -baseline BaselineCIID -assignment AssignmentID  -select &lt;datastream/xccdfBenchmark/profile&gt; -out &lt;outputResultFolder&gt;  [-log logFileName]

   >[!NOTE] 
   >콘텐츠에 데이터 스트림/벤치마크/프로필이 여러 개 있는 경우 –select 매개 변수를 사용하여 클라이언트에서 평가한 데이터 스트림/벤치마크/프로필을 지정해야 합니다.

**외부 변수가 포함된 단일 OVAL 파일의 경우:**

Microsoft.Sces.DcmToScap.exe -baseline BaselineCIID -assignment AssignmentID –oval &lt;singleOvalFile.xml&gt; [-variable &lt;externalVariableFile.xml&gt;]  -out &lt;outputResultFolder&gt;  [-log logFileName]

   >[!NOTE] 
    >Microsoft.Sces.DcmToScap.exe는 각 대상 컴퓨터에 대해 OVAL 정의 결과 보고서만 생성하며 ARF 보고서는 생성하지 않습니다.

#### <a name="how-to-get-baseline-ci-id-and-assignment-id"></a>기준 CI ID와 할당 ID를 가져오는 방법

관리 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**으로 이동합니다. CI ID는 구성 기준 CI ID입니다.

![CI ID와 할당 ID 가져오기](./media/get-to-baselines.png)

원하는 구성 기준을 선택하고 배포 탭을 클릭하여 할당 ID가 표시되지 않으면, 열 머리글을 마우스 오른쪽 단추로 클릭하고 할당 ID를 클릭하여 이를 사용하도록 설정합니다.
![CI ID와 할당 ID 가져오기](./media/get-to-baselines.png)


#### <a name="microsoftscesdcmtoscapexe-command-line-parameters"></a>Microsoft.Sces.DcmToScap.exe 명령줄 매개 변수

| **매개 변수** | **용도** | **필수** |
| --- | --- | --- |
| -baseline [기준 CI ID] | 구성 기준 지정 | 예 |
| -assignment [할당 ID] | 구성 기준 배포 지정 | 예 |
| -organization [조직 이름] | 보고서에 표시되는 조직 이름을 지정합니다. 여러 줄에 조직 이름을 지정하려는 경우 &#39;;&#39;를 사용하여 구분할 수 있습니다. | 아니요 |
| -type [thin/full/fullnosc] | OVAL 결과 유형을 씬 결과, 전체 결과, 시스템 특성이 없는 전체 결과 중에서 지정합니다. | 아니요(지정하지 않는 경우 기본값인 full이 사용됨) |
| -scap [SCAP 데이터 스트림 파일] | SCAP 데이터 스트림 파일을 지정합니다. | 예(SCAP 1.2 데이터 스트림의 경우 -xccdf 및 -oval/-variable과 함께 사용할 수 없음) |
| -xccdf [XCCDF 파일] | XCCDF 파일을 지정합니다. | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| -cpe [cpe 파일] | CPE 파일 지정 | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| -oval [OVAL 파일] | OVAL 파일 지정 | 예(독립 실행형 OVAL 파일의 경우 -xccdf 및 -scap와 함께 사용할 수 없음) |
| -variable [OVAL 외부 변수 파일] | OVAL 외부 변수 파일 지정 | 아니요(외부 OVAL 변수 파일이 있는 경우 독립 실행형 OVAL 파일에 대해 선택적으로 사용 가능. -xccdf 및 -scap와 함께 사용할 수 없음) |
| -select [xccdf 벤치마크/프로필] | SCAP 데이터 스트림 또는 XCCDF 파일에서 XCCDF 벤치마크나 프로필 선택 | 예(Configuration Manager 데이터베이스의 해당 DCM 기준에 일치하는지 여부를 확인할 수 있도록 항목을 선택하여 보고서를 생성해야 함) |
| -out [출력 디렉터리] | 준수 설정 cab 파일을 출력할 위치 지정 | 아니요(지정하지 않는 경우 도구는 변환이 수행되지 않으며 콘텐츠만 나열됨) |
| -log [로그 파일] | 로그 파일 지정 | 아니요(지정하지 않는 경우 Microsoft.Sces.DcmToScap.log 파일에 로그가 기록됨) |
| -help/-? | 도구 사용법 출력 | 아니요 |



 >[!TIP] 
 >-?, –h 또는 –help 매개 변수를 지정하여 Microsoft.Sces.DcmToScap.exe 도구의 구문과 매개 변수 목록을 표시할 수 있습니다.

기본적으로 Microsoft.Sces.DcmToScap.exe 도구는 사용자의 자격 증명을 사용하여 Configuration Manager 데이터베이스에 액세스합니다. Microsoft.Sces.DcmToScap.exe 도구를 사용하려면 최소한 Configuration Manager 데이터베이스에 대한 읽기 권한이 필요합니다.

해당 **ARF** 보고서(_ARF\_xxxx.xml_) 및/또는 **인간이 읽을 수 있는** 보고서(xxx.txt), **Cyberscope** 보고서(LASR\_xxx.xml), **ConsumedOval** 보고서(xx-oval-&lt;machineName&gt;.xml), **XCCDF 벤치 마크 결과** 보고서(xccdf\_xxx.xml) 파일이 있는지 확인한 후 명령줄에 exit를 입력한 다음, **ENTER**를 눌러 명령 프롬프트를 종료합니다.

## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [문제 해결](/sccm/compliance/plan-design/scap/troubleshooting-scap)
