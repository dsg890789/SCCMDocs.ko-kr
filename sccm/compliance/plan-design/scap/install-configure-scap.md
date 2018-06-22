---
title: SCAP(Security Content Automation Protocol) 확장 설치 및 구성
titleSuffix: Configuraton Manager
description: SCAP(Security Content Automation Protocol) 확장 설치 및 구성
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: f53b484b-5123-48f0-be2f-4e30318f3d39
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 891d21b44ed6efca73413a46d0483519b76f9cae
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32336598"
---
# <a name="install-and-configure-the-scap-extensions-for-microsoft-system-center-configuration-manager"></a>Microsoft System Center Configuration Manager용 SCAP 확장 설치 및 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Tip]  
> 이 기능은 기술 미리 보기 버전 1803에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 도입되었습니다. SCAP 확장의 이 시험판 버전은 현재 지원되는 모든 버전의 Configuration Manager 현재 분기 및 LTSB 1606에 설치할 수 있습니다. 설치 파일은 1803 미리 보기부터 cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi에 있습니다.   

필수 구성 요소 인프라를 준비한 후에는 이 프로세스를 실행할 컴퓨터에서 Microsoft System Center Configuration Manager용 SCAP 확장을 설치 및 구성할 수 있습니다.

## <a name="install-scap-extensions-configuration-manager"></a>Configuration Manager용 SCAP 확장 설치

1. ConfigMgr\_Extenstions\_for\_SCAP.msi를 실행하여 도구를 설치합니다.
2. Windows 탐색기에서 **ConfigMgr\_Extensions\_for\_SCAP.msi** 파일을 다운로드한 폴더로 이동한 다음, **ConfigMgr\_Extensions\_for\_SCAP.msi** 파일을 두 번 클릭합니다. 그러면 Microsoft System Center Configuration Manager용 SCAP 확장 설치 마법사가 시작됩니다.

다음 표에 나와 있는 정보를 참조하여 **Microsoft System Center Configuration Manager용 SCAP 확장 설치 마법사**를 완료합니다. 별도로 값을 지정해야 하는 경우가 아니면 마법사의 기본값을 그대로 사용합니다.

**표 1.0** Microsoft System Center Configuration Manager용 SCAP 확장 설치 마법사 프로세스

| 마법사 페이지 이름 | 사용자 작업 |
| --- | --- |
| 시작 및 최종 사용자 사용권 계약 |1. 사용권 계약 검토|
| 시작 및 최종 사용자 사용권 계약|2. **동의함**을 클릭합니다.|
| 시작 및 최종 사용자 사용권 계약|3. **설치**를 클릭합니다.|
| Microsoft System Center Configuration Manager용 SCAP 확장 설치 마법사 완료 |4. **마침**을 클릭합니다.|
 



Microsoft System Center Configuration Manager용 SCAP 확장 설치 마법사는 기본적으로 Configuration Manager 콘솔 설치 폴더에 확장을 설치합니다.



## <a name="download-and-install-the-scap-data-stream-files"></a>SCAP 데이터 스트림 파일 다운로드 및 설치

SCAP 확장을 실행하여 SCAP 데이터 스트림 파일을 변환한 다음 준수 설정 기능으로 가져오려면 NVD(National Vulnerability Database) [다운로드 페이지](http://nvd.nist.gov/fdcc/download_fdcc.cfm) 웹 사이트에서 SCAP 데이터 스트림을 다운로드해야 합니다. 그런 다음 SCAP 확장을 설치한 폴더에 SCAP 데이터 스트림을 복사합니다.

사용자 환경에 따라서는 다운로드 페이지에 나와 있는 SCAP 데이터 스트림 파일 중 일부만 필요할 수도 있습니다.

SCAP 데이터 스트림을 설치하려면

1. [NVD 웹 사이트](http://nvd.nist.gov/) 를 방문하여 조직에 필요한 SCAP 데이터 스트림을 확인합니다.
NIST에서 게시하는 SCAP 데이터 스트림은 _검사 목록_이라고도 하는 여러 번들로 구성되어 있습니다.

2. [NVD 웹 사이트](http://nvd.nist.gov/home.cfm)에서 SCAP 데이터 스트림을 다운로드합니다. 데이터 스트림은 파일 이름 확장명이 .zip인 압축 파일에 저장되어 있거나 DataStream XML 파일로 표시되어 있습니다.

    >[!IMPORTANT] 
    >NVD에서는 확장명이 .xml인 여러 SCAP 데이터 스트림 파일을 다운로드할 수 있습니다. 그러나 SCAP 확장에서는 XCCDF(SCAP1.0 및 1.1)/DataStream(SCAP1.2) 콘텐츠를 포함하는 .xml 파일만 사용할 수 있습니다.

3. 다운로드한 SCAP 데이터 스트림 .zip 파일/DataStream XML 파일을 SCAP 확장을 설치한 폴더에 추출합니다.

## <a name="convert-and-import-the-scap-data-stream-files-using-the-import-scap-content-wizard"></a>SCAP 콘텐츠 가져오기 마법사를 사용하여 SCAP 데이터 스트림 파일 변환 및 가져오기

SCAP 데이터 스트림을 받은 후에는 데이터 스트림을 가져와서 구성 기준으로 변환할 수 있습니다. NIST에서 게시하는 SCAP 데이터 스트림은 여러 번들로 구성됩니다. NIST의 지침에 따라 사용자 환경에서 사용할 번들을 확인합니다. 예를 들어 각 Windows 버전별로 별도의 번들이 있고, 방화벽 구성에 대한 다른 버전별 번들도 있으며, Internet Explorer 8.0용 번들도 있습니다. 이 작업을 수행하려면 다음 절차를 따르세요.

### <a name="to-import-the-scap-data-streams-into-configuration-manager"></a>SCAP 데이터 스트림을 Configuration Manager로 가져오려면

1. 구성 기준의 리본에서 SCAP 콘텐츠 가져오기 마법사를 시작합니다.

     ![CI 기준 리본에서 SCAP 콘텐츠 가져오기 마법사 시작 ](./media/import-scap-content.png)

2. 콘텐츠 유형을 선택합니다.

      ![콘텐츠 유형 선택](./media/import-new-scap-content.png)

3. SCAP 데이터 스트림 파일, XCCDF 및 CPE 사전 파일 또는 Oval 콘텐츠 파일을 선택합니다.

     ![SCAP 데이터 스트림 파일 선택](./media/select-datastream-file.png)

4. SCAP 1.2일 경우 데이터 스트림을 선택합니다. 그런 다음, SCAP 1.x에 대한 벤치마크 및 프로필을 선택합니다.  콘텐츠를 변환하려면 **다음**을 선택합니다. 진행률 표시줄이 표시됩니다.

      ![SCAP 1.2에 대한 벤치마크 및 프로필 선택](./media/select-benchmark-and-profile.png)

5. 가져올 구성 데이터를 확인합니다.

      ![구성 스크린샷 확인](./media/confirm-configuration.png)

6. **다음**을 클릭하여 구성 데이터를 가져옵니다.

      ![가져오기 완료](./media/complete-import.png)

## <a name="alternate-method-convert-and-import-the-scap-data-stream-files-using-the-cmd-line-tool"></a>(대체 방법) cmd 명령줄 도구를 사용하여 SCAP 데이터 스트림 파일 변환 및 가져오기

SCAP 데이터 스트림을 가져온 후, Microsoft.Sces.ScapToDcm.exe 도구를 사용하여 SCAP 데이터 스트림을 준수 설정 규격 .cab 파일로 변환할 수 있습니다. 그런 다음, Configuration Manager로 .cab 파일을 가져옵니다. Microsoft.Sces.ScapToDcm.exe 도구는 SCAP 데이터 스트림을 Configuration Manager의 준수 설정 기능을 사용하여 액세스할 수 있는 구성 항목 및 구성 기준으로 변환합니다. Microsoft.Sces.ScapToDcm.exe 도구는 SCAP 데이터 스트림을 XML 매니페스트로 변환합니다. 그런 다음, XML 매니페스트를 Configuration Manager로 가져올 수 있는 .cab 파일로 패키징합니다.

NIST에서 게시하는 SCAP 데이터 스트림은 여러 번들로 구성됩니다. NIST의 지침에 따라 사용자 환경에서 사용할 번들을 확인합니다. 예를 들어 각 Windows 버전별로 별도의 번들이 있고, 방화벽 구성에 대한 다른 버전별 번들도 있으며, Internet Explorer 8.0용 번들도 있습니다. 이 작업을 수행하려면 다음 절차를 따르세요.





## <a name="to-import-the-scap-data-streams-into-configuration-manager"></a>SCAP 데이터 스트림을 Configuration Manager로 가져오려면

1. SCAP 데이터 스트림을 준수 설정 규격 .cab 파일로 변환합니다.
2. Configuration Manager로 .cab 파일을 가져옵니다.

### <a name="convert-the-scap-data-streams-into-compliance-settings-compliant-cab-files"></a>SCAP 데이터 스트림을 준수 설정 규격 .cab 파일로 변환

시스템의 준수 상태를 분석하고 평가하려면 XML 형식의 SCAP 데이터 스트림을 준수 설정 구성 항목 및 구성 기준과 호환되는 XML 매니페스트로 변환해야 합니다. Microsoft.Sces.ScapToDcm.exe 도구는 SCAP 데이터 스트림을 XML 매니페스트로 변환합니다. 그런 다음, XML 매니페스트를 나중에 Configuration Manager로 가져올 수 있는 .cab 파일로 패키징합니다.

#### <a name="to-convert-the-scap-data-streams-into-compliance-settings-compliant-cab-files-using-the-microsoftscesscaptodcmexe-tool"></a>**Microsoft.Sces.ScapToDcm.exe 도구를 사용하여 SCAP 데이터 스트림을 준수 설정 규격 .cab 파일로 변환하려면**

명령 프롬프트에서 AdminConsole\Bin 폴더로 이동하고 Microsoft.Sces.ScapToDcm.exe를 실행하여 준수 설정 규격 cab 파일을 생성한 다음, Configuration Manager 사이트로 가져옵니다.

   >[!NOTE] 
   > 계정에 출력 폴더에 대한 읽기/쓰기 권한이 있어야 합니다.

**SCAP 1.0/1.1 콘텐츠(USGCB 및 DISA 콘텐츠와 같은 XCCDF XML 파일)의 경우:**

 Microsoft.Sces.ScapToDcm.exe –xccdf &lt;xccdf.xml&gt; -cpe &lt;cpe.xml&gt; -out &lt;outputFolder&gt; [-select benchmark/profile] [-log LogFileName]

   >[!NOTE] 
   >-select 매개 변수를 사용하여 벤치마크/프로필을 지정하지 않으면 콘텐츠 파일의 각 벤치마크에 대해 DCM cab 파일이 생성됩니다.

**SCAP1.2 콘텐츠(최신 USGCB 콘텐츠와 같은 DataStream XML 파일)의 경우**

Microsoft.Sces.ScapToDcm.exe –scap &lt;scapdatastreamfile.xml&gt; -out &lt;outputFolder&gt; [-select datastream/benchmark/profile] [-log LogFileName]

   >[!NOTE] 
   > -select 매개 변수를 사용하여 데이터 스트림/벤치마크/프로필을 지정하지 않으면 콘텐츠 파일의 각 벤치마크에 대해 DCM cab 파일이 생성됩니다.

**외부 변수가 포함된 단일 OVAL 파일의 경우:**

Microsoft.Sces.ScapToDcm.exe-oval &lt;singleOvalFile.xml&gt; [-variable &lt;externalVariableFile.xml&gt;] -out &lt;outputFolder&gt; [-log LogFileName]

   >[!NOTE] 
   > 외부 변수 파일의 변수 하나에 대해 값이 여러 개 있는 경우 Microsoft.Sces.ScapToDcm.exe 도구는 이 변수에 대해 값을 배열로 처리합니다.



#### <a name="microsoftscesscaptodcmexe-command-line-parameters"></a>Microsoft.Sces.ScapToDcm.exe. 명령줄 매개 변수

| **매개 변수** | **용도** | **필수** |
| --- | --- | --- |
| -scap [SCAP 데이터 스트림 파일] | SCAP 데이터 스트림 파일을 지정합니다. | 예(SCAP 1.2 데이터 스트림의 경우 -xccdf 및 -oval/-variable과 함께 사용할 수 없음) |
| -xccdf [XCCDF 파일] | XCCDF 파일을 지정합니다. | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| -cpe [cpe 파일] | CPE 파일 지정 | 예(SCAP 1.0/1.1 XCCDF의 경우 -scap 및 -oval/-variable과 함께 사용할 수 없음) |
| -oval [OVAL 파일] | OVAL 파일 지정 | 예(독립 실행형 OVAL 파일의 경우 -xccdf 및 -scap와 함께 사용할 수 없음) |
| -variable [OVAL 외부 변수 파일] | OVAL 외부 변수 파일 지정 | 아니요(외부 OVAL 변수 파일이 있는 경우 독립 실행형 OVAL 파일에 대해 선택적으로 사용 가능하며, -xccdf 및 -scap와 함께 사용할 수 없음) |
| -select [xccdf 벤치마크/프로필] | SCAP 데이터 스트림 또는 XCCDF 파일에서 XCCDF 벤치마크나 프로필 선택 | 아니요(이 스위치를 지정하는 것이 좋습니다. 스위치를 지정하지 않는 경우에는 포함된 모든 DataStream/벤치마크의 모든 프로필에 대해 cab 파일이 생성됩니다. |
| -out [출력 디렉터리] | DCM cab 파일 출력 위치 지정 | 아니요(지정하지 않는 경우 변환이 수행되지 않으며 콘텐츠만 나열됨) |
| -log [로그 파일] | 로그 파일 지정 | 아니요(지정하지 않는 경우 Microsoft.Sces.ScapToDcm.log 파일에 로그가 기록됨) |
| -help/-? | 도구 사용법 출력 | 아니요 |





#### <a name="the-following-command-lines-are-samples-for-the-microsoftscesscaptodcmexe-tool"></a>다음 명령줄은 Microsoft.Sces.ScapToDcm.exe 도구의 샘플입니다.

**SCAP1.2 콘텐츠:**

  Microsoft.Sces.ScapToDcm.exe-scap scap\_gov.nist\_USTCB-ie8.xml –out.\mytestfolder –select mySCAPDataStreamID/myBenchMarkID/myProfileID 

**SCAP1.0/1.1 콘텐츠:**

   Microsoft.Sces.ScapToDcm.exe–xccdf scap\_gov.nist\_Test-WinXP\_xccdf.xml –cpe scap\_gov.nist\_Test-WinXP\_cpe.xml –out.\mytestfolder –select XCCDFBenchmarkID/MyProfileID

**SCAP OVAL 콘텐츠:**

  Microsoft.Sces.ScapToDcm.exe-oval myOvalFile.xml –variable myOvalExternalVariableFile.xml –out.\mytestfolder

**다음과 같은 출력은 Microsoft.Sces.ScapToDcm.exe 도구의 샘플입니다.**

  Compliance Settings compliant cab file created:

  Validate the schema of SCAP data stream file C:\24SCAP\BVT\_Test\_Data\_Stream.xml

  Successfully validate the schema of SCAP data stream file C:\24SCAP\BVT\_Test\_Data\_Stream.xml

  Process XCCDF Benchmark xccdf\_tst.bvt\_benchmark\_Windows-F

  Process XCCDF Profile: xccdf\_tst.bvt\_profile\_version\_1.0.0.0-BVT Profile #1

  Process OVAL: scap\_tst.bvt\_comp\_Windows-F-oval.xml

  Successfully finished process OVAL: scap\_tst.bvt\_comp\_Windows-F-oval.xml

  Process OVAL: scap\_tst.bvt\_comp\_Windows-F-cpe-oval.xml

  Successfully finished process OVAL: scap\_tst.bvt\_comp\_Windows-F-cpe-oval.xml Process SCAP data stream: scap\_tst.bvt\_datastream\_Windows-F.zip SCAP Data Stream: [scap\_tst.bvt\_datastream\_Windows-F.zip]

  Version:        [1.2]

  Timestamp:      [2/24/2012]

  Use-case:       [CONFIGURATION]

  CPE Dictionary:  [scap\_tst.bvt\_comp\_Windows-F-cpe-dictionary.xml]

  OVAL:              [Windows-F-cpe-oval.xml] Product name:    [National Institute of Standards and Technology]

  Product version: []

  Schema version:  [5.3]

  Timestamp:       [2/24/2012]

  XCCDF Benchmark: [xccdf\_tst.bvt\_benchmark\_Windows-F]

  Version:       [v1.0.0.0] Update:        [http://usgcb.nist.gov]

  Timestamp:     [2/24/2012]

  Status:        [accepted]

  Status date:   [2/24/2012]

  Title:         [Ohh New BVT for SCAP 1.2]

 Description:   [My description]

  XCCDF Profile: [xccdf\_tst.bvt\_profile\_version\_1.0.0.0]
 
  OVAL:              [Windows-F-oval.xml]

   Product name:    [scaptool]

   Product version: []

   Schema version:  [5.4]

   Timestamp:       [2/24/2012]

  Start SCAP to DCM conversion...

  Processing SCAP data stream: scap\_tst.bvt\_datastream\_Windows-F.zip

  Processing CPE dictionary: scap\_tst.bvt\_comp\_Windows-F-cpe-dictionary.xml

  …

  Generating CI baseline cab file: C:\28\bbt\xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

  Successfully generated CI baseline cab file: C:\28\bbt\xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

  Successfully converted XCCDF profile: xccdf\_tst.bvt\_profile\_version\_1.0.0.0 into DCM baseline xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [SCAP 준수 설정 가져오기 및 준수 결과 내보내기](/sccm/compliance/plan-design/scap/import-scap-compliance-settings)
