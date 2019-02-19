---
title: SCAP 확장 설치 및 구성
titleSuffix: Configuration Manager
description: Configuration Manager용 SCAP(Security Content Automation Protocol) 확장을 설치 및 구성합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: f53b484b-5123-48f0-be2f-4e30318f3d39
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b63894764e45e67ef262e345140e245297a11c87
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56133938"
---
# <a name="install-and-configure-the-scap-extensions-for-configuration-manager"></a>Configuration Manager용 SCAP 확장 설치 및 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

[인프라를 준비](/sccm/compliance/plan-design/scap/about-scap#bkmk_prepare)한 후에는 이 프로세스를 실행할 컴퓨터에서 Configuration Manager용 SCAP 확장을 설치 및 구성할 수 있습니다.



## <a name="bkmk_install"></a> SCAP 확장 설치

설치 파일은 Configuration Manager 사이트 서버의 설치 디렉터리에 있는 다음 경로에 있습니다.  
`cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi`

1. 이 프로세스를 실행하려는 Configuration Manager 콘솔이 있는 컴퓨터에 **ConfigMgrExtensionsforSCAP.msi**를 복사합니다.  

2. Windows 탐색기에서 **ConfigMgrExtensionsforSCAP.msi**를 복사한 폴더로 이동합니다. 파일을 두 번 클릭하고 열어서 Configuration Manager 설치 마법사의 SCAP 확장을 시작합니다.  

3. 사용권 계약을 검토합니다. **동의함**을 클릭한 다음, **설치**를 클릭합니다.  

4. 설치가 완료되면 **마침**을 클릭하여 설치 마법사를 닫습니다.  

설치 마법사는 Configuration Manager 콘솔 설치 폴더에 SCAP 확장을 설치합니다. 기본적으로 콘솔 설치 폴더는 `C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole`입니다.  



## <a name="bkmk_scap-data-stream-files"></a> SCAP 데이터 스트림 파일 다운로드 및 설치

SCAP 확장을 실행하기 전에 NVD(National Vulnerability Database) [다운로드 페이지](https://csrc.nist.gov/Projects/United-States-Government-Configuration-Baseline)에서SCAP 데이터 스트림 파일을 다운로드해야 합니다. 그런 다음, SCAP 확장을 설치한 폴더에 SCAP 데이터 스트림을 복사합니다.

사용자 환경에 따라서는 다운로드 페이지에 나와 있는 SCAP 데이터 스트림 파일 중 일부만 필요할 수도 있습니다.

### <a name="install-the-scap-data-streams"></a>SCAP 데이터 스트림 설치

1. [NVD 웹 사이트](http://nvd.nist.gov/) 를 방문하여 조직에 필요한 SCAP 데이터 스트림을 확인합니다.
NIST에서 게시하는 SCAP 데이터 스트림은 _검사 목록_이라고도 하는 여러 번들로 구성되어 있습니다.  

2. [NVD 웹 사이트](http://nvd.nist.gov/home.cfm)에서 SCAP 데이터 스트림을 다운로드합니다. 데이터 스트림은 파일 이름 확장명이 .zip인 압축 파일에 저장되어 있거나 DataStream XML 파일로 표시되어 있습니다.  

    > [!IMPORTANT]  
    > NVD에서는 확장명이 .xml인 여러 SCAP 데이터 스트림 파일을 다운로드할 수 있습니다. 그러나 SCAP 확장에서는 XCCDF(SCAP1.0 및 1.1)/DataStream(SCAP1.2) 콘텐츠를 포함하는 .xml 파일만 사용할 수 있습니다.  

3. SCAP 확장을 설치한 폴더에 다운로드한 SCAP 데이터 스트림 .zip 파일/DataStream XML 파일을 추출합니다.  



## <a name="bkmk_convert-and-import"></a> SCAP 데이터 스트림 파일을 수동으로 변환하고 가져오기 

SCAP 데이터 스트림을 받은 후에는 데이터 스트림을 가져와서 구성 기준으로 변환할 수 있습니다. NIST에서 게시하는 SCAP 데이터 스트림은 여러 번들로 구성됩니다. NIST의 지침에 따라 환경에서 사용할 번들을 확인합니다. 예를 들어 각 Windows 버전별로 별도의 번들이 있고, 방화벽 구성에 대한 다른 버전별 번들도 있으며, Internet Explorer용 번들도 있습니다. 이 작업을 수행하려면 다음 절차를 따르세요.  

> [!Note]  
> 이 섹션에서는 Configuration Manager 콘솔을 사용하여 데이터 스트림 파일을 변환하고 가져오는 수동 프로세스를 설명합니다. 이 프로세스를 자동화하려면 다음 섹션에서 [SCAP 데이터 스트림 파일을 자동으로 변환하고 가져오기](#bkmk_auto-convert-and-import)를 참조하세요.  

1. 구성 기준 그룹의 리본에서 **SCAP 콘텐츠 가져오기** 마법사를 클릭합니다.

     ![콘솔 리본의 SCAP 콘텐츠 가져오기 단추](./media/import-scap-content.png)

2. SCAP 콘텐츠 옵션을 선택합니다.

      ![가져오기 마법사의 SCAP 콘텐츠 옵션 선택 페이지](./media/import-new-scap-content.png)

3. SCAP 데이터 스트림 파일, XCCDF 및 CPE 사전 파일 또는 Oval 콘텐츠 파일을 선택합니다.

     ![SCAP 데이터 스트림 파일 선택](./media/select-datastream-file.png)

4. SCAP 1.2일 경우 데이터 스트림을 선택합니다. 그런 다음, SCAP 1.x에 대한 벤치마크 및 프로필을 선택합니다. **다음**을 클릭하여 콘텐츠를 변환합니다. 

      ![SCAP 1.2에 대한 벤치마크 및 프로필 선택](./media/select-benchmark-and-profile.png)

      > [!Tip]  
      > 이 마법사 페이지는 **ScapToDcm.exe** 도구와 함께 사용하여 동일한 프로세스를 자동화하는 명령 줄이 표시됩니다.  

5. 가져올 구성 데이터를 확인합니다.

      ![구성 스크린샷 확인](./media/confirm-configuration.png)

6. **다음**을 클릭하여 구성 데이터를 가져옵니다.

      ![가져오기 완료](./media/complete-import.png)



## <a name="bkmk_auto-convert-and-import"></a> SCAP 데이터 스트림 파일을 자동으로 변환하고 가져오기 

### <a name="import-with-the-command-line-tool"></a>명령줄 도구를 사용하여 가져오기

SCAP 데이터 스트림을 가져온 후, **Microsoft.Sces.ScapToDcm.exe** 도구를 사용하여 SCAP 데이터 스트림을 준수 설정 규격 .cab 파일로 변환할 수 있습니다. 그런 다음, Configuration Manager로 .cab 파일을 가져옵니다. Microsoft.Sces.ScapToDcm.exe 도구는 SCAP 데이터 스트림을 Configuration Manager에서 사용할 수 있는 구성 항목 및 구성 기준으로 변환합니다. Microsoft.Sces.ScapToDcm.exe 도구는 SCAP 데이터 스트림을 XML 매니페스트로 변환합니다. 그런 다음, XML 매니페스트를 Configuration Manager로 가져올 수 있는 .cab 파일로 패키징합니다.

> [!Tip]  
> 이전 섹션 수동 프로세스의 4단계는 **ScapToDcm.exe** 도구와 함께 사용하여 동일한 프로세스를 자동화하는 명령 줄을 표시하는 마법사 페이지를 보여줍니다.  


#### <a name="use-microsoftscesscaptodcmexe-to-convert-scap-data-streams-into-cab-files"></a>Microsoft.Sces.ScapToDcm.exe를 사용하여 SCAP 데이터 스트림을 .cab 파일로 변환

명령 프롬프트에서 **AdminConsole\Bin** 폴더로 이동하여 **Microsoft.Sces.ScapToDcm.exe**를 실행합니다. 이 도구는 준수 설정 규격 .cab 파일을 생성하여 Configuration Manager 사이트로 가져옵니다.

   > [!NOTE]  
   > 계정에 출력 폴더에 대한 읽기/쓰기 권한이 있어야 합니다.

**SCAP 1.0/1.1 콘텐츠 사용(USGCB 및 DISA 콘텐츠와 같은 XCCDF XML 파일):**  

`Microsoft.Sces.ScapToDcm.exe –xccdf <xccdf.xml> -cpe <cpe.xml> -out <outputFolder> [-select benchmark/profile] [-log LogFileName]`  

   > [!NOTE]  
   > `–select` 매개 변수를 사용하여 벤치마크/프로필을 지정하지 않으면 도구에서 콘텐츠 파일의 각 벤치 마크에 대한 .cab 파일을 생성합니다.  

**SCAP 1.2 콘텐츠 사용(최신 USGCB 콘텐츠와 같은 DataStream XML 파일):**  

`Microsoft.Sces.ScapToDcm.exe –scap <scapdatastreamfile.xml> -out <outputFolder> [-select datastream/benchmark/profile] [-log LogFileName]`  

   > [!NOTE]  
   > `–select` 매개 변수를 사용하여 데이터 스트림/벤치마크/프로필을 지정하지 않으면 도구에서 콘텐츠 파일의 각 벤치 마크에 대한 .cab 파일을 생성합니다.

**외부 변수가 포함된 단일 OVAL 파일 사용:**  

`Microsoft.Sces.ScapToDcm.exe –oval <singleOvalFile.xml> [-variable <externalVariableFile.xml>] -out <outputFolder> [-log LogFileName]`  

   > [!NOTE]  
   > 외부 변수 파일의 변수 하나에 대해 값이 여러 개 있는 경우 Microsoft.Sces.ScapToDcm.exe 도구는 해당 값을 이 변수의 배열로 취급합니다.  



#### <a name="microsoftscesscaptodcmexe-command-line-parameters"></a>Microsoft.Sces.ScapToDcm.exe 명령줄 매개 변수

| 매개 변수 | 용도 | 필수 |
| --- | --- | --- |
| `-scap [scap data stream file]` | SCAP 데이터 스트림 파일을 지정합니다. | 예(SCAP 1.2 데이터 스트림의 경우 -xccdf 및 -oval/-variable과 함께 사용할 수 없음) |
| `-xccdf [xccdf file]` | XCCDF 파일을 지정합니다. | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| `-cpe [cpe file]` | CPE 파일 지정 | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| `-oval [oval file]` | OVAL 파일 지정 | 예(독립 실행형 OVAL 파일의 경우 -xccdf 및 -scap와 함께 사용할 수 없음) |
| `-variable [oval external variable file]` | OVAL 외부 변수 파일 지정 | 아니요(외부 OVAL 변수 파일이 있는 경우 독립 실행형 OVAL 파일에 대해 선택적으로 사용 가능하며, -xccdf 및 -scap와 함께 사용할 수 없음) |
| `-select [xccdf benchmark/profile]` | SCAP 데이터 스트림 또는 XCCDF 파일에서 XCCDF 벤치마크나 프로필 선택 | 아니요(이 매개 변수는 필수는 아니지만 권장됩니다. 지정하지 않는 경우 포함된 모든 DataStream/벤치마크의 모든 프로필에 대한 cab 파일이 도구에서 생성됩니다.) |
| `-out [output directory]` | DCM cab 파일 출력 위치 지정 | 아니요(지정하지 않는 경우 도구는 변환 없이 콘텐츠만 나열합니다.) |
| `-log [log file]` | 로그 파일 지정 | 아니요(지정하지 않는 경우 Microsoft.Sces.ScapToDcm.log 파일에 로그가 기록됩니다.) |
| `-help` 또는 `-?` | 도구 사용법 출력 | 아니요 |


#### <a name="microsoftscesscaptodcmexe-examples"></a>Microsoft.Sces.ScapToDcm.exe 예

**SCAP 1.2 콘텐츠:**  

`Microsoft.Sces.ScapToDcm.exe –scap scap_gov.nist_USTCB-ie8.xml –out .\mytestfolder –select mySCAPDataStreamID/myBenchMarkID/myProfileID`  

**SCAP 1.0/1.1 콘텐츠:**  

`Microsoft.Sces.ScapToDcm.exe–xccdf scap_gov.nist_Test-WinXP_xccdf.xml –cpe scap_gov.nist_Test-WinXP_cpe.xml –out .\mytestfolder –select XCCDFBenchmarkID/MyProfileID`  

**SCAP OVAL 콘텐츠:**  

`Microsoft.Sces.ScapToDcm.exe –oval myOvalFile.xml –variable myOvalExternalVariableFile.xml –out .\mytestfolder`  


#### <a name="sample-output-from-microsoftscesscaptodcmexe"></a>Microsoft.Sces.ScapToDcm.exe의 샘플 출력

```
  Compliance Settings compliant cab file created:

  Validate the schema of SCAP data stream file C:\24SCAP\BVT_Test_Data_Stream.xml

  Successfully validate the schema of SCAP data stream file C:\24SCAP\BVT_Test_Data_Stream.xml

  Process XCCDF Benchmark xccdf_tst.bvt_benchmark_Windows-F

  Process XCCDF Profile: xccdf_tst.bvt_profile_version_1.0.0.0-BVT Profile #1

  Process OVAL: scap_tst.bvt_comp_Windows-F-oval.xml

  Successfully finished process OVAL: scap_tst.bvt_comp_Windows-F-oval.xml

  Process OVAL: scap_tst.bvt_comp_Windows-F-cpe-oval.xml

  Successfully finished process OVAL: scap_tst.bvt_comp_Windows-F-cpe-oval.xml
   Process SCAP data stream: scap_tst.bvt_datastream_Windows-F.zip
    SCAP Data Stream: [scap_tst.bvt_datastream_Windows-F.zip]

  Version:        [1.2]

  Timestamp:      [2/24/2012]

  Use-case:       [CONFIGURATION]

  CPE Dictionary:  [scap_tst.bvt_comp_Windows-F-cpe-dictionary.xml]

  OVAL:              [Windows-F-cpe-oval.xml]
  Product name:    [National Institute of Standards and Technology]

  Product version: []

  Schema version:  [5.3]

  Timestamp:       [2/24/2012]

  XCCDF Benchmark: [xccdf_tst.bvt_benchmark_Windows-F]

  Version:       [v1.0.0.0]
   Update:        [http://usgcb.nist.gov]

  Timestamp:     [2/24/2012]

  Status:        [accepted]

  Status date:   [2/24/2012]

  Title:         [Ohh New BVT for SCAP 1.2]

 Description:   [My description]

  XCCDF Profile: [xccdf_tst.bvt_profile_version_1.0.0.0]
 
  OVAL:              [Windows-F-oval.xml]

   Product name:    [scaptool]

   Product version: []

   Schema version:  [5.4]

   Timestamp:       [2/24/2012]

  Start SCAP to DCM conversion...

  Processing SCAP data stream: scap_tst.bvt_datastream_Windows-F.zip

  Processing CPE dictionary: scap_tst.bvt_comp_Windows-F-cpe-dictionary.xml

  …

  Generating CI baseline cab file: C:\28\bbt\xccdf_tst.bvt_benchmark_Windows-F[xccdf_tst.bvt_profile_version_1.0.0.0].cab

  Successfully generated CI baseline cab file: C:\28\bbt\xccdf_tst.bvt_benchmark_Windows-F[xccdf_tst.bvt_profile_version_1.0.0.0].cab

  Successfully converted XCCDF profile: xccdf_tst.bvt_profile_version_1.0.0.0 into DCM baseline xccdf_tst.bvt_benchmark_Windows-F[xccdf_tst.bvt_profile_version_1.0.0.0].cab
```


### <a name="import-the-cab-file"></a>.cab 파일 가져오기

이 프로세스의 다음 단계에서는 Configuration Manager 콘솔을 사용하여 Configuration Manager로 준수 설정 규격 .cab 파일을 가져옵니다. 이 프로세스의 앞부분에서 만든 .cab 파일을 가져올 때는 Configuration Manager 데이터베이스에 하나 이상의 구성 항목과 구성 기준이 작성됩니다. 프로세스의 뒷부분에서 디바이스 컬렉션에 구성 기준을 배포할 수 있습니다. 자세한 내용은 [구성 데이터 가져오기](/sccm/compliance/deploy-use/import-configuration-data)를 참조하세요.

이전에 만든 .cab 파일의 위치는 Microsoft.Sces.ScapToDcm.exe 도구의 `–output` 매개 변수로 지정된 폴더입니다.

> [!IMPORTANT]  
> 프로세스 앞부분에서 만든 각 .cab 파일에 대해 이 프로세스를 반복합니다. NVD 웹 사이트에서 다운로드한 XCCDF/DataStreamXML 파일에 선택한 각 프로필에 대한 .cab 파일이 있습니다. Microsoft.Sces.ScapToDcm.exe 도구를 실행하여 이러한 파일을 처리할 수 있습니다.  

가져온 구성 기준은 읽기 전용이며 상태는 *사용*이고 배포된 상태는 *아니요*입니다. **수정한 날짜** 속성은 기준을 가져온 시간을 표시합니다. 구성 기준의 이름은 XCCDF/DataStream XML의 표시 이름 섹션에서 가져옵니다. 이름은 `ABC[XYZ]` 규칙을 사용하여 생성됩니다. 여기서 **ABC**는 XCCDF 벤치마크 ID이고 **XYZ**는 XCCDF 프로필 ID입니다(프로필을 선택한 경우).



## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [SCAP 준수 배포 및 모니터링 및 준수 결과 내보내기](/sccm/compliance/plan-design/scap/deploy-monitor-export)
