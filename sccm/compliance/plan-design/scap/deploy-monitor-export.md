---
title: SCAP 준수 배포 및 모니터
titleSuffix: Configuration Manager
description: SCAP 준수 설정을 구성 기준으로 배포하고, 준수를 모니터하며, 결과를 내보냅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 0bdcb018-bac2-4540-b786-6242bac73ff4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7b59b7414ad2095d053b1121ba936281559aa5e2
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39386004"
---
# <a name="deploy-and-monitor-scap-compliance-in-configuration-manager"></a>Configuration Manager에서 SCAP 준수 배포 및 모니터

*적용 대상: System Center Configuration Manager(현재 분기)*

SCAP 데이터 스트림 파일을 [변환하고 가져온 후에는](/sccm/compliance/plan-design/scap/install-configure-scap#bkmk_convert-and-import) 다음 단계를 참조하세요.  

- 구성 기준을 컬렉션에 [배포](#bkmk_deploy)하여 장치에서 SCAP 준수 평가  

- 대상 클라이언트에서 반환한 준수 데이터 [모니터](#bkmk_monitor)   

- 준수 결과를 SCAP 형식으로 [내보내기](#bkmk_export)  



## <a name="bkmk_deploy"></a>SCAP 구성 기준 배포

먼저 SCAP 준수를 평가하려는 컴퓨터에 장치 컬렉션을 만듭니다. 자세한 내용은 [컬렉션 만들기](/sccm/core/clients/manage/collections/create-collections)를 참조하세요.  

이제 장치 컬렉션에 가져온 구성 기준을 배포할 수 있습니다. 자세한 내용은 [구성 기준 배포 방법](/sccm/compliance/deploy-use/deploy-configuration-baselines)을 참조하세요.  

> [!Tip]  
> 각각의 장치 컬렉션에 배포하려는 각 구성 기준에 대해 이 프로세스를 반복합니다. 최소한 각 구성 기준을 하나 이상의 장치 컬렉션에 할당합니다.



## <a name="bkmk_monitor"></a> SCAP 준수 데이터 모니터 

준수 데이터를 다시 SCAP 형식으로 내보내기 전에 사이트가 데이터를 수집했는지 확인해야 합니다. 구성 기준을 컴퓨터 컬렉션에 배포하고 나면 해당 컬렉션의 각 장치에 설치된 Configuration Manager 클라이언트가 준수 정보를 자동으로 수집합니다. 이렇게 수집된 준수 정보는 Configuration Manager 데이터베이스에 저장됩니다.

Configuration Manager에서 구성 기준 배포 상태를 보면 Configuration Manager 클라이언트가 적합한 데이터를 수집했는지 확인합니다. Configuration Manager에서 적합한 준수 데이터가 수집된 경우 프로세스 뒷부분에서 만들 XCCDF/DataStream 결과 파일의 유효성을 검사하는 데 사용할 수 있으므로 데이터 수집 여부를 반드시 확인해야 합니다.

자세한 내용은 [준수 설정 모니터](/sccm/compliance/deploy-use/monitor-compliance-settings)를 참조하세요.


### <a name="validate-the-xccdfdatastream-results"></a>XCCDF/Datastream 결과 유효성 검사

1. Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동하여 **준수 설정**을 확장하고 **SCAP 대시보드**를 선택합니다.  

2. 구성 기준, 할당, SCAP 파일, 데이터 스트림, 벤치마크 및 프로필(있는 경우)을 선택합니다.  

3. **보고서 표시**
 ![예제 SCAP 보고서](./media/scap-report.png)를 클릭합니다.



## <a name="bkmk_export"></a> 준수 결과를 SCAP 형식으로 내보내기

이 프로세스의 다음 단계에서는 준수 데이터를 SCAP 형식(XML/사람이 읽을 수 있는 형식의 ARF 보고서 파일)으로 내보냅니다. SCAP 확장 내보내기 마법사 및 Microsoft.Sces.DcmToScap.exe 명령줄 도구는 각 구성 기준에 대한 별도의 XCCDF/DataStreamARF 결과 파일을 내보냅니다. 이러한 파일은 Microsoft.Sces.ScapToDcm.exe 도구가 각 구성 기준을 만드는 데 사용하는 각 XCCDF/DataStream 입력 파일에 해당합니다.


### <a name="manually-export-with-the-console-wizard"></a>콘솔 마법사를 사용하여 수동으로 내보내기

> [!Note]  
> 이 섹션에서는 Configuration Manager 콘솔을 사용하여 준수 결과를 내보내는 수동 프로세스를 설명합니다. 이 프로세스를 자동화하려면 다음 섹션의 [명령줄 도구를 사용하여 자동으로 내보내기](#bkmk_auto-export)를 참조하세요.  


1. **SCAP 대시보드** 노드의 마우스 오른쪽 단추로 클릭하여 **SCAP 보고서 내보내기** 마법사를 시작합니다.  
![SCAP 대시보드에서 SCAP 보고서 내보내기 마법사 시작](./media/import-from-scap-dashboard.png)

2. 구성 기준, 할당 및 SCAP 콘텐츠 형식을 선택합니다.  
![기준 선택](./media/select-ci-baseline.png)

3. SCAP 데이터 스트림 파일, XCCDF/CPE 파일 또는 Oval 콘텐츠 및 변수 파일의 위치를 선택합니다.  
![데이터 스트림 선택](./media/export-scap-report-datastream.png)

4. 조직 이름을 지정하고 SCAP 보고서를 내보낼 폴더 위치를 선택합니다.  
 ![데이터 스트림 선택](./media/specify-org-export.png)
   > [!Tip]  
   > 이 마법사 페이지는 **DcmToScap.exe** 도구를 사용하여 동일한 프로세스를 자동화하는 데 사용하게 되는 명령줄을 표시합니다.  

5. 설정을 확인합니다.  
 ![데이터 스트림 선택](./media/confirm-export.png)

6. **다음**을 선택하여 보고서를 내보냅니다. 마법사를 완료합니다.  
 ![내보내기 완료](./media/complete-report-export.png)


### <a name="bkmk_auto-export"></a> 명령줄 도구를 사용하여 자동으로 내보내기

명령 프롬프트를 열고 Configuration Manager **AdminConsole\Bin** 폴더로 이동합니다. 다음 명령줄 예제 중 하나를 사용합니다.  

> [!NOTE]  
> 계정에 Configuration Manager 공급자에 대한 읽기 권한이 있어야 합니다. 명령줄의 `–out` 매개 변수에서 지정한 폴더에 대한 쓰기 권한도 필요합니다.

**SCAP 1.0/1.1 콘텐츠(예: USGCB 및 DISA 콘텐츠)의 경우:**  

`Microsoft.Sces.DcmToScap.exe -baseline BaselineCIID -assignment AssignmentID –xccdf <xccdf.xml> -cpe <cpe.xml>  -select <xccdfBenchmark/profile> -out <outputResultFolder> [-log logFileName]`  

  > [!NOTE]  
  > 콘텐츠에 벤치마크/프로필이 여러 개 있는 경우 `–select` 매개 변수를 사용하여 클라이언트에서 평가한 벤치마크/프로필을 지정해야 합니다.  

**SCAP1.2 콘텐츠(예: 최신 USGCB 콘텐츠)의 경우:**  

`Microsoft.Sces.DcmToScap.exe -baseline BaselineCIID -assignment AssignmentID -select <datastream/xccdfBenchmark/profile> -out <outputResultFolder> [-log logFileName]`  

   > [!NOTE]  
   > 콘텐츠에 데이터 스트림/벤치마크/프로필이 여러 개 있는 경우 `–select` 매개 변수를 사용하여 클라이언트에서 평가한 데이터 스트림/벤치마크/프로필을 지정해야 합니다.  

**외부 변수가 포함된 단일 OVAL 파일의 경우:**  

`Microsoft.Sces.DcmToScap.exe -baseline BaselineCIID -assignment AssignmentID –oval <singleOvalFile.xml> [-variable <externalVariableFile.xml>] -out <outputResultFolder> [-log logFileName]`  

   > [!NOTE]  
   > Microsoft.Sces.DcmToScap.exe는 각 대상 머신에 대해 OVAL 정의 결과 보고서만 생성합니다. ARF 보고서는 생성하지 않습니다.  


#### <a name="how-to-get-the-baselineciid-and-assignmentid"></a>BaselineCIID 및 AssignmentID를 받는 방법

Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동하여 **준수 설정**을 확장하고 **구성 기준**을 선택합니다. `BaselineCIID`는 구성 기준에 대한 식별자(ID)입니다.  
![CI ID와 할당 ID 가져오기](./media/get-to-baselines.png)

원하는 구성 기준을 선택하고 **배포** 탭을 클릭합니다. `AssignmentID`는 장치 컬렉션에 대한 구성 기준 배포의 식별자(ID)입니다. 할당 ID가 표시되지 않으면 열 헤더를 마우스 오른쪽 단추로 클릭하고 **할당 ID**를 선택합니다.  
![CI ID와 할당 ID 가져오기](./media/get-to-baselines.png)


#### <a name="microsoftscesdcmtoscapexe-command-line-parameters"></a>Microsoft.Sces.DcmToScap.exe 명령줄 매개 변수

| 매개 변수 | 용도 | 필수 |
| --- | --- | --- |
| `-baseline [Baseline CI ID]` | 구성 기준 지정 | 예 |
| `-assignment [Assignment ID]` | 구성 기준 배포 지정 | 예 |
| `-organization [organization name]` | 보고서에 표시되는 조직 이름을 지정합니다. 여러 줄에 조직 이름을 지정하려는 경우 `;`을 사용하여 구분할 수 있습니다. | 아니요 |
| `-type [thin/full/fullnosc]` | OVAL 결과 유형을 씬 결과, 전체 결과, 시스템 특성이 없는 전체 결과 중에서 지정합니다. | 아니요(지정하지 않는 경우 기본값인 full이 사용됨) |
| `-scap [scap data stream file]` | SCAP 데이터 스트림 파일을 지정합니다. | 예(SCAP 1.2 데이터 스트림의 경우 -xccdf 및 -oval/-variable과 함께 사용할 수 없음) |
| `-xccdf [xccdf file]` | XCCDF 파일을 지정합니다. | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| `-cpe [cpe file]` | CPE 파일 지정 | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| `-oval [oval file]` | OVAL 파일 지정 | 예(독립 실행형 OVAL 파일의 경우 -xccdf 및 -scap와 함께 사용할 수 없음) |
| `-variable [oval external variable file]` | OVAL 외부 변수 파일 지정 | 아니요(외부 OVAL 변수 파일이 있는 경우 독립 실행형 OVAL 파일에 대해 선택적으로 사용 가능하며, -xccdf 및 -scap와 함께 사용할 수 없음) |
| `-select [xccdf benchmark/profile]` | SCAP 데이터 스트림 또는 XCCDF 파일에서 XCCDF 벤치마크나 프로필 선택 | 예(Configuration Manager 데이터베이스의 해당 DCM 기준에 일치하는지 여부를 확인할 수 있도록 항목을 선택하여 보고서를 생성해야 함) |
| `-out [output directory]` | 준수 설정 cab 파일을 출력할 위치 지정 | 아니요(지정하지 않는 경우 도구는 변환이 수행되지 않으며 콘텐츠만 나열됨) |
| `-log [log file]` | 로그 파일 지정 | 아니요(지정하지 않는 경우 Microsoft.Sces.DcmToScap.log 파일에 로그가 기록됨) |
| `-help` 또는 `-?` | 도구 사용법 출력 | 아니요 |

 > [!TIP]  
 > `-?`, `–h` 또는 `–help` 매개 변수를 지정하여 Microsoft.Sces.DcmToScap.exe 도구의 구문과 매개 변수 목록을 표시할 수 있습니다.

기본적으로 Microsoft.Sces.DcmToScap.exe 도구는 사용자의 자격 증명을 사용하여 Configuration Manager 데이터베이스에 액세스합니다. Microsoft.Sces.DcmToScap.exe 도구를 사용하려면 최소한 Configuration Manager 데이터베이스에 대한 읽기 권한이 필요합니다.

도구 실행 후에는 다음 파일이 있는지 확인합니다. 
- **ARF** 보고서: `_ARF_xxxx.xml_` 및/또는 **알기 쉬운** 보고서: `xxx.txt`
- **Cyberscope** 보고서: `LASR_xxx.xml`
- **ConsumedOval** 보고서: `xx-oval-<machineName>.xml`
- **XCCDF 벤치마크 결과** 보고서: `xccdf_xxx.xml` 



## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [문제 해결](/sccm/compliance/plan-design/scap/troubleshooting-scap)
