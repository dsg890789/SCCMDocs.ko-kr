---
title: MDT 문제 해결
titleSuffix: Microsoft Deployment Toolkit
description: 'Microsoft Deployment Toolkit에 대한 참조 문제 해결 '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 91a7a69a-deac-4b0f-aac9-b7bd187c53fb
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: efb65086878a46bfb3485fdd8b0be6f613225261
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2018
ms.locfileid: "27821017"
---
# <a name="troubleshooting-reference-for-the-microsoft-deployment-toolkit"></a>Microsoft Deployment Toolkit에 대한 참조 문제 해결
 운영 체제 및 응용 프로그램의 배포 및 사용자 상태의 마이그레이션은 적절한 도구와 지침을 갖추더라도 어려운 시도일 수 있습니다. 이 참조는 MDT(Microsoft® Deployment Toolkit) 2013의 일부로서 현재 알려진 문제에 관한 정보, 해당 문제에 대한 가능한 해결 방법 및 문제 해결 지침을 제공합니다.  

> [!NOTE]
>  이 문서에서 *Windows*는 달리 언급이 없는 한 Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2 운영 체제에 적용됩니다. MDT는 ARM 프로세서 기반 버전의 Windows를 지원하지 않습니다. 마찬가지로 *MDT*는 달리 언급이 없는 한 MDT 2013을 의미합니다.  

> [!NOTE]
>  Microsoft DaRT(Diagnostics and Recovery Toolset)은 시작되지 않거나 불안정한 클라이언트 컴퓨터 문제 해결 및 복구하기 위한 강력한 도구가 포함되어 있습니다. DaRT를 사용하여 충돌의 원인을 확인하고 손실된 파일을 복원하는 등을 할 수 있습니다. Windows 운영 체제를 개발하고 배포하는 경우 DaRT를 문제 해결 도구로 사용할 수도 있습니다. 예를 들어 빌드된 이미지가 올바로 시작하지 못하면 ERD Commander-진단 환경을 사용하여 이미지가 포함된 클라이언트 컴퓨터를 시작할 수 있습니다. 그런 다음, 클라이언트 컴퓨터의 하드 디스크를 탐색하고 이벤트 로그를 확인하고 업데이트를 제거하고 운영 체제 설정을 변경하는 등을 할 수 있습니다. DaRT는 Software Assurance의 Microsoft Desktop Optimization Pack의 구성 요소입니다. DaRT에 대한 자세한 내용은 [http://www.microsoft.com/windows/enterprise/products-and-technologies/mdop/dart.aspx](http://www.microsoft.com/windows/enterprise/products-and-technologies/mdop/dart.aspx)을 참조합니다.  

## <a name="understanding-logs"></a>로그 해석  
 MDT의 효과적인 문제 해결을 시작하기 전에 운영 체제 배포 동안 사용된 많은 .log 파일에 대한 명확한 해석이 있어야 합니다. 어떤 로그 파일이 어떤 실패 조건 및 시간대에 대해 조사하는지 알고 있는 경우 한 때 이해하기 어렵고 난해했던 문제가 명확하고 이해하기 쉽게 될 수 있습니다.  

 MDT 로그 파일 형식은 [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=9257)에서 다운로드 가능한 System Center Configuration Manager 2007 Toolkit V2의 일부인 Trace32에서 읽을 수 있도록 설계됐습니다. 로그는 System Center 2012 Configuration Manager 이상 버전으로 사용할 수 있는 CMTrace(Configuration Manager Trace Log Tool)에서 읽을 수 있습니다. 훨씬 쉽게 오류를 찾게 하기 때문에 로그 파일 읽기가 가능할 때마다 이러한 도구를 사용합니다.  

 이 섹션의 나머지 부분에서는 배포 및 Windows 설치 동안 만든 로그 파일을 자세히 설명합니다. 또한 이 섹션은 문제 해결을 위해 해당 파일을 언제 사용하는지에 대한 예제도 제공합니다.  

### <a name="mdt-logs"></a>MDT 로그  
 각 MDT 스크립트를 실행하는 경우 로그 파일을 자동으로 만듭니다. 이러한 로그 파일의 이름은 스크립트의 이름과 일치합니다. 예를 들어 ZTIGather.wsf는 *ZTIGather.log*라는 로그 파일을 만듭니다. 각 스크립트는 또한 MDT 스크립트가 만드는 로그 파일의 콘텐츠를 집계하는 공통 마스터 로그 파일(BDD.log)을 업데이트합니다. MDT 로그 파일은 배포 프로세스 중에 C:\MININT\SMSOSD\OSDLOGS에 상주합니다. 수행되는 배포 유형에 따라 로그 파일은 %WINDIR%\SMSOSD 또는 %WINDIR%\TEMP\SMSOSD로 배포 완료 시 이동됩니다. LTI(Lite Touch Installation) 배포의 경우 로그는 C:\MININT\SMSOSD\OSDLogs에서 시작합니다. 로그는 작업 시퀀스 처리가 완료되면 %WINDIR%\TEMP\DeploymentLogs에서 끝납니다.  

 MDT는 다음 로그 파일을 만듭니다.  

-   **BDD.log**. 이것은 집계된 MDT 로그 파일로서 Customsettings.ini 파일에서 **SLShare** 속성을 지정하는 경우 배포가 끝날 때 네트워크 위치로 복사됩니다.  

-   **LiteTouch.log**. 이 파일은 LTI 배포 동안 만들어집니다. **/debug:true** 옵션을 지정하지 않는 한 이 파일은 %WINDIR%\TEMP\DeploymentLogs에 상주합니다.  

-   **Scriptname*.log**. 이 파일은 각 MDT 스크립트에서 만듭니다. *Scriptname*은 해당 스크립트의 이름을 나타냅니다.  

-   **SMSTS.log**. 작업 Sequencer에서 만든 이 파일은 모든 작업 Sequencer 트랜잭션을 설명합니다. 배포 시나리오에 따라 이 파일은 %TEMP%, %WINDIR%\System32\ccm\logs 또는 C:\\\_SMSTaskSequence 또는 C:\SMSTSLog에 상주할 수 있습니다.  

-   **Wizard.log**. 배포 마법사는 이 파일을 만들고 업데이트합니다.  

-   **WPEinit.log**. 이 파일은 Windows PE 초기화 프로세스 동안 만들어지며, Windows PE를 시작하는 동안 발생된 오류를 해결하는 데 유용합니다.  

-   **DeploymentWorkbench_*id*.log**. 이 로그 파일은 배포 워크 벤치를 시작할 때 **a /debug**를 지정하는 경우 %temp% 폴더에서 만들어집니다.  

### <a name="configuration-manager-operating-system-deployment-logs"></a>Configuration Manager 운영 체제 배포  
 Microsoft System Center 2012 R2 Configuration Manager에서 만든 운영 체제 배포 로그 파일에 대한 내용은 [Configuration Manager의 로그 파일에 대한 기술 참조](http://technet.microsoft.com/library/hh427342.aspx)를 참조합니다.  

 Windows USMT(사용자 환경 마이그레이션 도구)를 실행하는 경우 MDT는 USMT 로그 파일을 저장할 로깅 옵션을 MDT 로그 파일 위치에 자동으로 추가합니다. 로그 파일 및 만들어지는 시기는 다음과 같습니다.  

-   **USMTEstimate.log**. USMT 요구 사항을 예측하는 경우 만듦  

-   **USMTCapture.log**. 데이터를 캡처할 때 USMT에서 만듦  

-   **USMTRestore.log**. 데이터를 복원할 때 USMT에서 만듦  

 ZeroTouchInstallation.vbs 스크립트는 USMT 진행률 로그 파일에서 오류 및 경고를 자동으로 검색합니다. 스크립트는 다음 요약(*usmt_type*가 **ESTIMATE**, **SCANSTATE** 또는 **LOADSTATE**인 경우, *error_count*가 발견된 오류 총수인 경우 그리고 *warning_count*가 발견된 경고 총수인 경우)을 사용하여 Microsoft System Center Operations Manager에 이벤트 ID 41010을 생성합니다.  

```  
ZTI USMT <usmt_type> reported <error_count> errors and <warning_count> warnings  
```  

 오류 수가 0보다 큰 경우 이 이벤트는 오류 형식입니다. 경고 수가 오류 없이 0보다 큰 경우 이 이벤트는 경고 형식입니다. 그렇지 않은 경우 이 이벤트는 정보 제공 형식입니다.  

## <a name="identifying-error-codes"></a>오류 코드 식별  
표 1에서는 MDT 스크립트가 만드는 오류 코드를 나열하고 각 오류 코드에 대한 설명을 제공합니다. 이러한 오류 코드는 BDD.log 파일에 기록됩니다.  

### <a name="table-1-error-codes-and-their-description"></a>테이블 1. 오류 코드 및 설명  

|**오류 코드**|**설명**|  
|-|-|  
|5201|배포 공유에 연결할 수 없습니다. 배포가 진행되지 않습니다.|  
|5203|배포 공유에 연결할 수 없습니다. 배포가 진행되지 않습니다.|  
|5205|배포 공유에 연결할 수 없습니다. 배포가 진행되지 않습니다.|  
|5206|배포 마법사가 취소되었거나 성공적으로 완료되지 않았습니다. 배포가 진행되지 않습니다.|  
|5207|배포 공유에 연결할 수 없습니다. 배포가 진행되지 않습니다.|  
|5208|**DeploymentType**이 설정되지 않았습니다. **SkipWizard**에 대한 일부 값을 설정해야 합니다.|  
|5208|SMS 작업 Sequencer를 찾을 수 없습니다. 배포가 진행되지 않습니다.|  
|5400|개체 만들기: **설정 *class_instance* = 새로 만들기 *class_name***|  
|5490|MSXML2.DOMDocument를 만듭니다.|  
|5495|MSXML2.DOMDocument.ParseErr.ErrCode를 만듭니다.|  
|5496|LoadControlFile.FindFile: *ConfigFile*|  
|5601|OS guid를 확인합니다: %OSGUID%가 있습니다.|  
|5602|OSGUID를 사용하여 XML을 엽니다: %OSGUID%.|  
|5610|파일을 확인합니다.|  
|5630|파일을 확인합니다: *ImagePath*.|  
|5640|파일을 확인합니다: *ImagePath*.|  
|5641|FindFile: ImageX.exe.|  
|5643|BootSect.exe를 찾습니다.|  
|5650|디렉터리를 확인합니다: *SourcePath*.|  
|5651|디렉터리를 확인합니다: *SourcePath*\Platform.|  
|5652|FindFile: bootsect.exe.|  
|6001|드라이브를 확인합니다.|  
|6002|드라이브를 확인합니다.|  
|6010|TSGUID를 테스트합니다.|  
|6020|Robocopy 반환 값: *값*.|  
|6021|Robocopy 반환 값: *값*.|  
|6101|파일을 확인합니다: *DeployCab*.|  
|6102|DEPLOY.CAB에서 Sysprep 파일을 확장합니다.|  
|6111|Sysprep.exe를 실행합니다.|  
|6121|Sysprep 실행합니다.|  
|6191|Sysprep 완료를 확인하려면 레지스트리에서 **CloneTag**를 테스트합니다.|  
|6192|Sysprep 완료를 확인하려면 레지스트리에서 **SystemSetupInProgress**를 테스트합니다.|  
|6401|권한 있는 DHCP 서버입니다.|  
|6501|컴퓨터 백업이 불가능하면 네트워크 경로(**BackupShare**, **BackupDir**)가 지정되지 않습니다.|  
|6502|오류 - IMAGEX를 찾을 수 없어 백업을 수행할 수 없습니다.|  
|6601|GetObject (... root/wmi:BCDStore).|  
|6602|BCD.OpenStore(*BCDStore*).|  
|6701|구성된 보호기입니다.|  
|6702|이동된 부팅 파일입니다.|  
|6703|BDE 파티션을 만듭니다.|  
|6704|조각 모음 드라이브입니다.|  
|6705|드라이브를 축소합니다.|  
|6706|1 초과 파티션을 테스트합니다.|  
|6707|부팅 파일을 만듭니다.|  
|6708|디스크를 암호화합니다.|  
|6709|MicrosoftVolumeEncryption WMI 공급자에 연결합니다.|  
|6710|디스크 암호화.|  
|6711|**ProtectKeyWithTPM**.|  
|6712|**ProtectKeyWithTPMAndPIN**.|  
|6713|**ProtectKeyWithTPMAndStartupKey**.|  
|6714|외부 키를 파일에 저장합니다.|  
|6715|외부 키로 보호합니다.|  
|6716|외부 키를 파일에 저장합니다.|  
|6717|숫자 암호를 사용하여 키를 보호합니다.|  
|6718|**GetKeyProtectorNumberialP@ssword.**|  
|6718|암호를 파일에 저장합니다.|  
|6719|*PasswordFile*을 엽니다.|  
|6720|드라이브를 암호화합니다.|  
|6721|*DiskPartFile*을 엽니다.|  
|6722|파티션을 만듭니다.|  
|6723|기존 BDE 드라이브를 가져옵니다.|  
|6724|*DiskPartFile*을 엽니다.|  
|6727|*DiskPartFile*을 열려고 시도합니다.|  
|6729|*DiskPartFile* 텍스트 파일을 만듭니다.|  
|6730|**cmd /c DISKPART.EXE /s *DiskPartFile* >> *LogPath*\ZTIMarkActive_diskpart.log 2>&1** 실행|  
|6731|bcdboot.exe를 찾습니다.|  
|6732|Microsoft TPM 공급자에 연결합니다.|  
|6733|공급자 클래스에서 TPM 인스턴스를 가져옵니다.|  
|6734|TPM 인스턴스를 가져옵니다.|  
|6735|TPM을 사용할 수 있는지 확인합니다.|  
|6736|TPM이 활성화됐는지 확인합니다.|  
|6737|TPM을 소유했는지 확인합니다.|  
|6738|TPM 소유권을 허용하는지 확인합니다.|  
|6739|TPM을 사용할 수 있는지 확인합니다.|  
|6740|TPM이 활성화됐는지 확인합니다.|  
|6741|TPM을 소유하고 소유권을 허용하는지 확인합니다.|  
|6741|TPM 소유자 암호 설정|  
|6742|TPM 소유자 P@ssword을 **AdminP@ssword**로 설정합니다.|  
|6743|TPM 소유자 P@ssword을 값으로 설정합니다.|  
|6744|TPM을 사용할 수 있는지 확인합니다.|  
|6745|TPM 소유자를 확인합니다.|  
|6746|인증 키 쌍을 확인합니다.|  
|6747|TPM이 활성화됐는지 확인합니다.|  
|6748|TPM 소유권을 허용하는지 확인합니다.|  
|6749|소유자 p@ssword을 소유자 권한 부여로 변환합니다.|  
|6750|인증 키 쌍을 만듭니다.|  
|6751|소유자 권한 부여를 변경합니다.|  
|6752|**Cmd**를 실행합니다.|  
|6753|TPM의 유효성을 검사합니다.|  
|6754|BDE 인스턴스를 가져옵니다.|  
|6755|TPM을 사용하여 키를 보호합니다.|  
|6756|구성할 이동식 미디어를 확인합니다. **ProtectKeyWithTpmAndStartupKey**.|  
|6757|TPM 및 시작 키를 사용하여 키를 보호합니다.|  
|6758|BDE 핀을 찾습니다.|  
|6759|TPM 및 Pin을 사용하여 키를 보호합니다.|  
|6760|**BDEKeyLocation**에 대한 이동식 미디어를 찾습니다.|  
|6761|외부 키로 보호합니다.|  
|6762|*PasswordFile*에 저장되는 복구 P@ssword입니다.|  
|6764|BitLocker 정책을 구성합니다.|  
|7000|ZTIConfigure.xml을 찾을 수 없어 중단합니다.|  
|7001|무인 AnswerFile을 찾습니다.|  
|7100|오류 - 이 스크립트는 전체 OS에서만 실행해야 합니다.|  
|7101|오류 - DCPromo 응답 파일을 생성하기 위해 충분한 값이 제공되지 않았습니다.|  
|7102|오류 - 새 복제본 DC를 만들기 위한 필수 속성이 지정되지 않았습니다.|  
|7103|오류 - 새 자식 도메인을 만들기 위한 필수 속성이 지정되지 않았습니다.|  
|7104|오류 - 새 포리스트를 만들기 위한 필수 속성이 지정되지 않았습니다.|  
|7105|오류 - 새 포리스트를 만들기 위한 필수 속성이 지정되지 않았습니다.|  
|7200|서비스가 설치되지 않아 DHCP 서버를 구성할 수 없습니다.|  
|7201|범위 세부 정보를 읽을 수 없어 `GetScopeDetails()`이 실패했습니다.|  
|7202|범위를 만드는 데 지정된 값이 충분하지 않습니다.|  
|7203|이 범위에 대한 IP 범위를 설정하기 위해 제공된 값이 충분하지 않습니다.|  
|7204|범위 제외 범위에 대해 지정된 값이 없습니다.|  
|7300|DNS 명령을 실행할 수 없습니다.|  
|7700|새 컴퓨터 시나리오가 아니라 기존 디스크 파티션입니다.|  
|7701|디스크 크기가 시스템 및 BDE 파티션에 충분하지 않습니다. 요구되는 크기는 1.5GB입니다.|  
|7702|디스크 크기가 시스템 및 BDE 파티션에 충분하지 않습니다. 요구되는 크기는 10GB입니다.|  
|7703|DeployRoot은 디스크 # *DiskIndex*에 있습니다. OEM 시나리오 실행: 건너뜁니다.|  
|7704|OEM 시나리오 실행: 건너뜁니다.|  
|7704|확장된 논리 파티션은 BitLocker와 함께 사용할 수 없습니다.|  
|7712|드라이브/*볼륨 드라이브*가 있는지 확인합니다. 형식.|  
|7900|Findfile: Microsoft.BDD.PnpEnum.exe.|  
|7901|**AllDrivers.Exists("*GUID*").**|  
|7904|**AllDrivers.Exists("*GUID*").**|  
|9200|Findfile(PkgMgr.exe).|  
|9601|오류 - ZTITatoo 상태 복원 작업이 전체 OS에서 실행되어야 하므로 중단합니다.|  
|9701|USMT 예상에서 0이 아닌 반환 코드는 *오류*입니다.|  
|9702|사용자 상태 캡처 불가능, 로컬 공간 부족 및 지정된 네트워크 경로(UDShare, UDDir) 없음.|  
|9703|USMT 캡처에서 0이 아닌 반환 코드는 *오류*입니다.|  
|9704|유효한 명령줄 옵션이 지정되지 않았습니다.|  
|9801|오류 - 서버 운영 체제를 실행하는 컴퓨터에 클라이언트 운영 체제를 배포하려고 합니다.|  
|9802|오류 - 클라이언트 운영 체제를 실행하는 컴퓨터에 서버 운영 체제를 배포하려고 합니다.|  
|9803|오류 - 컴퓨터를 업그레이드하기 위한 권한이 없어(OSInstall =*OSInstall*) 중단합니다.|  
|9804|오류 - *메모리* MB의 메모리로는 충분하지 않습니다. 적어도 *메모리* MB의 메모리가 필요합니다.|  
|9805|오류 - *ProcessorSpeed* MHz의 프로세서 속도로는 충분하지 않습니다.  적어도 *ProcessorSpeed* MHz의 프로세서가 필요합니다.|  
|9806|오류 - 부족한 공간을 *드라이브*에서 사용할 수 있습니다. 추가로 *크기*의 MB가 필요합니다.|  
|9807|오류 - 부족한 공간을 *드라이브*에서 사용할 수 있습니다. 추가로 *크기*의 MB가 필요합니다.|  
|9901|ZTIWindowsUpdate 스크립트를 Windows PE에서 실행하지 마십시오.|  
|9902|ZTIWindowsUpdate의 실행과 실패 횟수가 너무 많습니다. 개수 = *개수*.|  
|9903|업데이트된 Windows Update 에이전트를 설치하는 예기치 않은 문제로 반환 코드는 *오류*입니다.|  
|9904|개체를 만들지 못했습니다: **Microsoft.Update.Session**.|  
|9905|개체를 만들지 못했습니다: **Microsoft.Update.UpdateColl**.|  
|9906|중요한 파일 *파일*을 찾지 못해 중단합니다.|  
|10000|개체를 만듭니다: **Set oLTICleanup = New LTICleanup**.|  
|10201|도메인 *도메인*에 가입할 수 없습니다. 설치를 중단합니다.|  
|10203|FindFile(LTISuspend.wsf).|  
|10204|*LTISuspend* 프로그램을 실행합니다.|  
|41024|ImageX를 실행합니다.|  
|52012|모든 마법사 매개 변수가 설정되지 않았습니다.|  

 목록 1은 오류 코드를 찾는 방법을 설명하는 로그 파일에서 발췌를 제공합니다. 이 발췌에서 보고된 오류 코드는 5001입니다.  

 **목록 1입니다. 오류 코드 5001**을 포함하는 SMSTS.log 파일에서 발췌  

```  
.  
.  
.  
The operating system installation failed. Please contact your system administrator for assistance.  

The action "Zero Touch Installation - Validation" failed with exit code 5001  
.  
.  
.  

```  

### <a name="converting-error-codes"></a>오류 코드 변환  
 로그 파일에 있는 많은 오류 코드는 암호화 상태로 되어 있어 실제 오류 조건과 연관성을 찾기 어려워 보입니다. 그러나 다음 프로세스에서는 오류 코드를 변환하고 문제 해결에 도움이 되는 의미 있는 정보를 얻는 방법을 보여줍니다.  

 **문제**: 이미지 캡처가 0x80070040 오류 코드로 실패합니다.  

 **가능한 솔루션 1**: 제시된 오류 코드는 10진수 형식으로 변환해야 하는 16진수 형식으로 되어 있습니다. 이 작업을 수행하려면 공학용 계산기가 필요하며 Windows 운영 체제에 포함된 계산기는 이 작업에 아주 적합합니다.  

 **오류 코드를 변환하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **액세서리**를 가리킨 다음, **계산기**를 클릭합니다.  

2.  **보기** 메뉴에서 **과학적**을 클릭합니다.  

3.  **16진수**를 선택한 다음, 코드의 마지막 4자리(이 경우는 그림 1에 표시된 것처럼 **0040**)를 입력합니다.  

     ![TroubleshootingReference1](media/TroubleshootingReference1.jpg "TroubleshootingReference1")  
그림 1. 오류 변환  

     **그림 1. 오류 변환**  

     계산기는 16진수 모드이므로 앞에 오는 0은 표시되지 않습니다.  

4.  **10진수**를 선택합니다.  

     16진수 값 *40*은 10진수 값 *64*로 변환됩니다.  

5.  명령 프롬프트 창을 열고 **NET HELPMSG 64**을 입력한 다음, ENTER를 누릅니다.  

     **NET HELPMSG** 명령은 숫자 오류 코드를 의미 있는 텍스트로 변환합니다. 여기에 제공된 오류 코드는 "지정된 네트워크 이름을 더 이상 사용할 수 없습니다"로 변환됩니다.  

 이 정보는 네트워킹 문제가 대상 컴퓨터 또는 배포 공유가 상주하는 서버와 대상 컴퓨터 사이에 있을 수 있다고 표시합니다. 이러한 문제는 속도 및 이중 설정에서 일치하지 않거나 제대로 설치되지 않은 네트워크 드라이버를 포함할 수 있습니다.  

 **가능한 솔루션 2:** Microsoft Exchange Server 오류 코드 조회 유틸리티를 사용합니다. 이 명령줄 유틸리티는 오류 코드 변환 지원에 유용합니다. [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=985)에서 다운로드할 수 있습니다.  

### <a name="review-of-sample-logs"></a>샘플 로그 검토  
 MDT는 MDT 배포 프로세스의 문제를 해결하는 데 사용할 수 있는 로그 파일을 만듭니다. 다음 섹션에서는 배포 프로세스 문제 해결을 위해 MDT 로그 파일을 사용하는 방법의 예제를 제공합니다.  

-   [데이터베이스 액세스 실패](#FailuretoAccesstheDatabase)에 설명된 대로 MDT DB(MDT 데이터베이스) 액세스 실패와 관련된 문제  

####  <a name="FailuretoAccesstheDatabase"></a> 데이터베이스 액세스 실패  
 **문제:** 다양한 섹션을 포함한 CustomSettings.ini 파일을 사용한 배포를 실행하고, **우선 순위** 속성을 사용하여 처리될 각 섹션의 우선 순위를 지정하는 동안 오류가 발생합니다. BDD.log는 다음과 같은 오류 메시지를 포함합니다.  

-   ```  
    ERROR - Opening Record Set (Error Number = -2147217911) (Error Description: The SELECT permission was denied on the object 'ComputerAdministrators', database 'AdminDB', schema 'dbo'.)  
    ```  

-   ```  
    ADO error: The SELECT permission was denied on the object 'ComputerAdministrators', database 'AdminDB', schema 'dbo'. (Error #-2147217911; Source: Microsoft OLE DB Provider for SQL Server; SQL State: 42000; NativeError: 229  
    ```  

-   ```  
    ERROR - Unhandled error returned by ZTIGather: Object required (424)  
    ```  

> [!NOTE]
>  명확히 하기 위해 위의 로그 파일 내용을 Trace32 프로그램을 사용하여 볼 수 있는 동안 표시되는 대로 나타냈습니다.  

 **가능한 솔루션:** 로그 파일 샘플의 첫 번째 줄에서 지적한 것처럼 문제는 데이터베이스에 액세스할 수 있는 권한이 거부된 것입니다. 따라서 사용자 ID와 암호를 사용할 수 없기 때문에 스크립트는 데이터베이스에 안전한 연결을 설정할 수 없습니다. 결국 컴퓨터 계정을 사용하여 데이터베이스 액세스를 시도했습니다. 이 문제를 해결하는 가장 쉬운 방법은 모든 사용자에게 데이터베이스 읽기 권한을 부여하는 것입니다.  

## <a name="troubleshooting"></a>문제 해결  
 \-깊이 있는 문제 해결 프로세스를 시작하기 전에 다음 항목을 검토하여 관련 요구 사항이 모두 충족되었는지 확인합니다.  

-   모든 소프트웨어 및 하드웨어 필수 구성 요소가 충족되지 않은 경우 설치 문제가 발생할 수 있습니다.  

### <a name="application-installation"></a>응용 프로그램 설치  
 응용 프로그램 설치 문제에 대한 문제 및 솔루션을 검토합니다.  

-   [차단된 실행 파일](#BlockedExecutables)에 설명된 대로 보안 이유로 차단된 설치 원본 파일  

-   [네트워크 연결 손실](#LostNetworkConnections)에 설명된 것처럼 네트워크 연결의 손실  

-   [2007 Microsoft Office System](#MicrosoftOfficeSystem)에 설명된 대로 2007 Microsoft Office 시스템 또는 관련 파일을 설치하는 동안 발생한 설치 오류 30029  

####  <a name="BlockedExecutables"></a> 차단된 실행 파일  
 **문제:** 설치 원본 파일은 인터넷에서 다운로드하는 경우 하나 이상의 NTFS 파일 시스템 데이터 스트림으로 표시될 가능성이 높습니다. NTFS 데이터 스트림에 대한 자세한 내용은 [파일 스트림](http://msdn2.microsoft.com/library/aa364404\(VS.85\).aspx)을 참조합니다. NTFS 파일 시스템 데이터 스트림의 존재는 **파일 열기 - 보안 경고** 프롬프트가 표시되게 할 수 있습니다. 이 프롬프트에서 **실행**을 클릭할 때까지 설치는 진행되지 않습니다.  

 그림 2에서는 **더 보기** 명령 및 [스트림 유틸리티](http://technet.microsoft.com/sysinternals/bb897440.aspx)를 사용하여 NTFS 파일 시스템 데이터 스트림을 볼 수 있습니다.  

 ![TroubleshootingReference2](media/TroubleshootingReference2.jpg "TroubleshootingReference2")  
그림 2. NTFS 데이터 스트림  

 **그림 2. NTFS 데이터 스트림**  

 **가능한 솔루션 1:** 설치 원본 파일을 마우스 오른쪽 단추로\-클릭한 다음, **속성**을 클릭합니다. **차단 해제**를 클릭한 다음, **확인**을 클릭해 NTFS 파일 시스템 데이터 스트림을 파일에서 제거합니다. 하나 이상의 NTFS 파일 시스템 데이터 스트림의 존재에 따라 차단된 각 설치 원본 파일에 대해 이 프로세스를 반복합니다.  

 **가능한 솔루션 2:** 그림 2에 표시된 REF \_Ref308173670 \\h 대로 스트림 유틸리티를 사용하여 NTFS 파일 시스템 데이터 스트림을 설치 원본 파일에서 제거합니다. 스트림을 유틸리티는 하나 이상의 파일이나 폴더에서 한 번에 NTFS 파일 시스템 데이터 스트림을 제거할 수 있습니다.  

####  <a name="LostNetworkConnections"></a> 손실된 네트워크 연결  
 **문제:** 장치 드라이버를 설치하거나 장치 및 네트워크 구성을 변경하는 경우 설치가 실패할 수 있습니다. 이러한 변경은 네트워크 연결에서의 잘못을 일으켜 설치가 실패하게 만듭니다.  

 **가능한 솔루션:** 설치를 위해 다운로드 및 실행을 사용하는 ZTICacheUtil.vbs 스크립트를 구현합니다. 이 스크립트는 다운로드 및 실행을 사용하는 알림을 조정하도록 설계되었습니다. Configuration Manager 배포 지점이 WebDAV(Web\-based Distributed Authoring and Versioning) 및 BITS를 사용할 수 있는 경우 다운로드는 Background Intelligent Transfer Service\(BITS\)를 사용합니다. 동시에 Configuration Manager를 수정해 먼저 ZTICache.vbs 스크립트를 실행하여 프로그램이 배포 프로세스 동안 자체적으로 삭제되지 않게 확인합니다.  

####  <a name="MicrosoftOfficeSystem"></a> 2007 Microsoft Office System  
 **문제:** 2007 Office system을 배포하고 Windows Installer 패치 \(MSP\) 파일을 포함하는 동안 설치는 오류 코드 30029로 실패할 수 있습니다.  

 ZTIApplications.log에서 추가적인 조사는 다음 메시지를 표시합니다.  

-   ```  
    About to run command: \\Server\Deployment$\Tools\X86\bddrun.exe \\Server\Share\Microsoft\Office\2007\Professional\setup.exe /adminfile \\Server\Share\Microsoft\Office\2007\Professional\file.msp  
    ```  

-   ```  
    ZTI Heartbeat: command has been running for 12 minutes (process ID 1600) Return code from command = 30029  
    ```  

-   ```  
    Application Microsoft Office 2007 Professional returned an unexpected return code: 30029  
    ```  

 **가능한 솔루션 1:** MSP 파일을 업데이트 디렉터리에 재배치한 다음, **\/adminfile** 옵션을 지정하지 않고 setup.exe를 실행합니다. 설치 중 업데이트를 배포하는 방법에 대한 자세한 내용은 [2007 Office system 배포](http://technet.microsoft.com/library/cc303395\(v=Office.12\).aspx)를 참조합니다.  

 **가능한 솔루션 2:** MSP 파일이 **모달 표시 안 함** 확인란을 선택하지 않았는지 확인합니다. 이 설정을 구성 하는 방법에 대 한 자세한 내용은 [2007 Office System 배포 개요](http://technet.microsoft.com/library/bb490141.aspx)를 참조합니다.  

### <a name="autologon"></a>AutoLogon  
 자동 로그온에 대한 문제 및 솔루션을 검토합니다.  

-   [로그온 보안 배너](#LogonSecutiryBanners)에 설명된 대로 로그온 보안 배너 때문에 \(ZTI\) 배포 프로세스에서 LTI 및 Zero Touch 설치 중단  

-   [사용자 자격 증명에 대한 프롬프트](#PromtedforUserCredentials)에 설명된 대로 사용자 자격 증명에 대한 프롬프트 때문에 LTI 및 ZTI 배포 프로세스 중단  

####  <a name="LogonSecutiryBanners"></a> 로그온 보안 배너  
 **문제:** MDT 작업 순서가 대화형 사용자 세션 중 처리되어 대상 컴퓨터가 지정된 관리자 계정을 사용하여 자동으로 로그온할 수 있도록 요구합니다. 그룹 정책 개체 \(GPO\)가 로그온 보안 배너를 적용하는 위치에 있는 경우 보안 배너가 명시된 정책을 사용자가 수용하기를 기다리는 동안 로그온 프로세스를 중단하기 때문에 이 자동 로그온은 계속 진행할 수 없습니다.  

 **가능한 솔루션:** GPO가 특정 조직 구성 단위 \(OU\)에 적용되고 기본 도메인 GPO에 포함되지 않도록 확인합니다. 도메인에 컴퓨터를 추가할 때 로그온 보안 배너를 적용하는 GPO에서 영향을 받지 않는 OU에 추가되도록 지정합니다. 작업 순서 편집기에서 마지막 작업 순서 단계 중 하나로서 원하는 OU에 컴퓨터 계정을 재배치하는 스크립트를 포함합니다.  

> [!NOTE]
>  기존 Active Directory® Domain Services\(AD DS\) 계정을 재사용하는 경우 대상 컴퓨터에 배포하기 전에 사용자가 대상 컴퓨터의 계정을 보안 로그온 배너를 적용하는 GPO에서 영향을 받지 않는 OU에 재배치했는지 확인합니다.  

####  <a name="PromtedforUserCredentials"></a> 사용자 자격 증명에 대한 프롬프트  
 **문제:** 도메인에 가입된 컴퓨터의 이미지를 만들었습니다. 대상 컴퓨터에 새 이미지를 배포하는 동안 자동\-로그온이 발생하지 않아 사용자에게 적절한 자격 증명을 입력하라는 메시지가 표시되기 때문에 배포 프로세스는 중단됩니다. 자격 증명이 제공되고 사용자가 로그온돼 있는 경우 배포 프로세스는 다시 시작합니다.  

 **가능한 솔루션:** 이미지를 캡처할 때 원본 컴퓨터가 도메인에 가입되지 않아야 합니다. 컴퓨터에 도메인에 가입된 경우 문제가 해결되었는지 확인하려면 작업 그룹에 컴퓨터를 가입하고 이미지를 재\-캡처하고 대상 컴퓨터에 배포를 시도합니다.  

### <a name="bios"></a>BIOS  
 **문제:** Intel vPro 기술이 사용된 대상 컴퓨터를 배포하는 동안 중지 오류와 함께 배포가 종료될 수 있습니다. 모든 업데이트된 드라이버가 배포 워크 벤치에 기본\-\-드라이버로서 포함됐다 해도 대상 컴퓨터는 시작되지 않습니다.  

 가능한 솔루션: 대상 컴퓨터의 기본 입\/출력 시스템 \(BIOS\)에서 설정을 검토하여 기본 Serial Advanced Technology Attachment 모드가 AHCI\(Advanced Host Controller Interface\)로 구성되어 있는지 여부를 확인합니다. 그러나 특정 Windows 운영 체제는 기본적으로 AHCI를 지원하지 않습니다.  

### <a name="database-problems"></a>데이터베이스 문제  
 데이터베이스\-관련 문제 및 솔루션을 검토합니다.  

-   [차단된 SQL Server Browser 요청](#BlockedSQLServerBrowserRequests)에 설명된 대로 데이터베이스 서버에 방화벽이 잘못 구성된 결과로 발생한 오류  

-   [명명된 파이프 연결](#NamedPipeConnections)에 설명된 대로 데이터베이스 서버와 연결이 끊어진 결과로 발생한 오류  

####  <a name="BlockedSQLServerBrowserRequests"></a> 차단된 SQL Server Browser 요청  
 **문제:** MDT 배포 프로세스 동안 Microsoft SQL Server® 데이터베이스에서 정보를 검색할 수 있습니다. 그러나 데이터베이스 서버에 잘못 구성된 방화벽과 관련한 오류가 발생할 수 있습니다.  

 **가능한 솔루션:** Windows Server에서 Windows 방화벽을 사용하면 컴퓨터 리소스에 무단 액세스를 방지할 수 있습니다. 그러나 방화벽이 잘못 구성되어 있으면 SQL Server 인스턴스에 연결하려는 시도가 차단될 수 있습니다. 방화벽 뒤에 있는 SQL Server 인스턴스에 액세스하려면 SQL Server를 실행하는 컴퓨터에서 방화벽을 구성합니다. SQL Server용 방화벽 포트 구성에 대한 자세한 내용은 Microsoft 지원 문서, [Windows Server 2008에서 SQL Server용 방화벽 포트를 어떻게 여나요?](http://support.microsoft.com/kb/968872)를 참조 하십시오.  

####  <a name="NamedPipeConnections"></a> 명명된 파이프 연결  
 **문제:** MDT 배포 프로세스 동안 SQL Server 데이터베이스에서 정보를 검색할 수 있습니다. 그러나 끊어진 SQL Server 연결과 관련한 오류가 발생할 수 있습니다. 이러한 오류는 Microsoft SQL Server에서 명명된 파이프 연결을 사용하도록 설정하지 않아 일어날 수 있습니다.  

 **가능한 솔루션:** 이러한 문제를 해결하려면 SQL Server에서 명명된 파이프를 사용하도록 설정합니다. 또한 명명된 파이프를 사용하여 외부 데이터베이스에 연결할 때 필요한 **SQLShare** 속성을 지정합니다. 명명된 파이프를 사용하여 연결할 경우 데이터베이스에 연결하려면 통합 보안을 사용합니다. LTI 배포의 경우 지정하는 사용자 계정이 데이터베이스에 연결됩니다. Configuration Manager를 사용하는 ZTI 배포의 경우 네트워크 액세스 계정이 데이터베이스에 연결됩니다. Windows PE에는 기본적으로 보안 컨텍스트가 없기 때문에 연결하게 될 사용자용 보안 컨텍스트를 설정하려면 데이터베이스 서버에 반드시 네트워크 연결을 해야 합니다.  

 **SQLShare** 속성이 지정하는 네트워크 공유는 서버에 연결할 수단을 제공하여 적절한 보안 컨텍스트를 얻습니다. 공유에 대한 읽기 권한이 있어야 합니다. 연결되는 경우 데이터베이스에 명명된 파이프 연결을 설정할 수 있습니다. **SQLShare** 속성은 필요 없으며 데이터베이스에 TCP\/IP 연결을 할 경우 사용해서도 안 됩니다.  

 사용 중인 SQL Server 버전에 따라 다음 작업을 수행하여 명명된 파이프 연결을 사용하도록 설정합니다.  

-   [SQL Server 2008 R2에서 명명된 파이프 연결을 사용하도록 설정](#EnableNamedPipeConnectionsinSQLServer)에 설명된 대로 SQL Server 2008 R2용 명명된 파이프 연결을 사용하도록 설정합니다.  

-   [SQL Server 2005에서 명명된 파이프 연결을 사용하도록 설정](#EnableNamedPipeConnectionsinSQL)에 설명된 대로 SQL Server 2005용 명명된 파이프 연결을 사용하도록 설정합니다.  

#####  <a name="EnableNamedPipeConnectionsinSQLServer"></a> SQL Server 2008 R2에서 명명된 파이프 연결을 사용하도록 설정  
 SQL Server 2008 R2에서 명명된 파이프 연결을 사용하도록 설정하려면 다음 단계를 수행합니다.  

1.  쿼리할 데이터베이스를 호스팅하는 SQL Server 2008 R2를 실행 중인 컴퓨터에서 **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft SQL Server 2008 R2**을 가리킨 다음, **SQL Server Management Studio**를 클릭합니다.  

2.  **Microsoft SQL Server Management Studio** 콘솔의 **개체 탐색기**에서 ***sql\_서버\_이름***을 마우스 오른쪽 단추\-클릭한 다음, **속성**을 클릭합니다. \(이 속성에서는 *sql\_서버\_이름*이 구성될 SQL Server\)를 실행하는 컴퓨터 이름입니다.  

3.  서버 속성\- ***sql\_서버\_이름*** 대화 상자가 표시됩니다.  

4.  **서버 속성** \- ***sql\_서버\_이름*** 대화 상자의 **페이지 선택**에서 **연결**을 클릭합니다.  

5.  **연결** 페이지에서 **이 서버에 대한 원격 연결 허용** 확인란이 선택됐는지 확인한 다음, **확인**을 클릭합니다.  

6.  Microsoft SQL Server Management Studio 콘솔을 닫습니다.  

7.  쿼리할 데이터베이스를 호스팅하는 SQL Server 2008 R2를 실행 중인 컴퓨터에서 **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft SQL Server 2008 R2**, **Configuration Tools**를 차례로 가리킨 다음, **SQL Server 구성 관리자**를 클릭합니다.  

8.  **Sql Server 구성 관리자** 콘솔에서 SQL Server 구성 관리자 \(로컬\) \/ *sql\_인스턴스*에 대한 SQL Server 네트워크 구성 \/ 프로토콜로 이동합니다. \(이 프로토콜에서는 *sql\_인스턴스*가 SQL Server 인스턴스의 이름으로 구성되게 됩니다\).  

9. 세부 정보 창에서 **명명된 파이프**를 마우스 오른쪽 단추\-클릭한 다음, **사용**을 클릭합니다.  

     변경 내용은 저장되지만 서비스가 중단되었다가 다시 시작될 때까지 적용되지 않는다는 것을 표시하는 경고 대화 상자가 나타납니다.  

10. **경고** 대화 상자에서 **확인**을 클릭합니다.  

11. **Sql Server 구성 관리자** 콘솔에서 SQL Server 구성 관리자 \(로컬\) \/ SQL Server 서비스로 이동합니다.  

12. 세부 정보 창에서 **SQL Server*\(sql\_인스턴스\)***를 마우스 오른쪽\-클릭한 다음, SQL Server 인스턴스의 이름으로 *sql\_인스턴스*가 2단계에서 구성되는\) 경우\( **다시 시작**을 클릭합니다.  

     SQL Server 구성 관리자 진행률 표시줄이 표시되어 서비스를 다시 시작하는 상태를 보여줍니다. 서비스가 다시 시작된 후 진행률 표시줄이 닫힙니다.  

13. SQL Server Configuration Manager 콘솔을 닫습니다.  

 자세한 내용은 [SQL Server 2008에서 원격 연결 사용 방법](http://blogs.msdn.com/b/walzenbach/archive/2010/04/14/how-to-enable-remote-connections-in-sql-server-2008.aspx)을 참조합니다.  

#####  <a name="EnableNamedPipeConnectionsinSQL"></a> SQL Server 2005에서 명명된 파이프 연결을 사용하도록 설정  
 SQL Server 2005에서 명명된 파이프 연결을 사용하도록 설정하려면 다음 단계를 수행합니다.  

1.  쿼리할 데이터베이스를 호스팅하는 SQL Server 2005를 실행 중인 컴퓨터에서 **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft SQL Server 2005**, **Configuration Tools**를 차례로 가리킨 다음, **SQL Server 노출 영역 구성**을 클릭합니다.  

2.  **SQL Server 2005 노출 영역 구성** 대화 상자에서 **서비스 및 연결에 대한 노출 영역 구성**을 클릭합니다.  

3.  *서버\_이름*이 \)SQL Server 2005를 실행하는 컴퓨터의 이름인 \(경우 **서비스 및 연결에 대한 노출 영역 구성 – *서버\_이름*** 대화 상자의 **에서 구성 요소를 선택한 다음, 해당 서비스 및 연결을 구성하고** MSSQLSERVER\\데이터베이스 엔진으로 이동한 다음,  **원격 연결**을 클릭합니다.  

4.  **로컬 및 원격 연결**, **TCP\/IP 및 명명된 파이프 모두 사용**을 차례로 클릭한 다음, **적용**을 클릭합니다.  

5.  *서버\_이름*이 \)SQL Server 2005를 실행하는 컴퓨터의 이름인 \(경우 **서비스 및 연결에 대한 노출 영역 구성 – *서버\_이름*** 대화 상자의 **에서 구성 요소를 선택한 다음, 해당 서비스 및 연결을 구성하고** MSSQLSERVER\\데이터베이스 엔진으로 이동한 다음,  **서비스**를 클릭합니다.  

6.  **중지**를 클릭합니다.  

     MSSQLSERVER 서비스를 중지합니다.  

7.  **시작**을 클릭합니다.  

     MSSQLSERVER 서비스를 시작합니다.  

8.  **확인**을 클릭합니다.  

9. SQL Server 2005 노출 영역 구성을 닫습니다.  

 추가 내용은 Microsoft 지원 문서 [원격 연결을 허용하도록 SQL Server 2005를 구성하는 방법](http://support.microsoft.com/kb/914277) 참조  

### <a name="deployment-scripts"></a>배포 스크립트  
 MDT\-관련 문제 및 솔루션을 검토합니다.  

-   [Credentials_script](#Credentials_script)에 설명된 대로 사용자 자격 증명에 대한 메시지가 표시되고 오류 0x80070035가 나타날 수 있음  

-   [ZTIWindowsUpdate](#ZTIWindowsUpdate)에 설명된 대로 "Wuredist.cab 찾을 수 없음"이란 오류 메시지가 나타남  

####  <a name="Credentials_script"></a> 자격 증명\_스크립트  
 **문제:** 새로 배포 된 컴퓨터의 마지막 시작\- 동안 사용자에게는 사용자 자격 증명을 제공하라는 메시지가 표시되고 네트워크 경로 찾을 수 없음을 나타내는 오류 0x80070035가 발생할 수 있습니다.  

 **가능한 솔루션:** WIM 파일에는 MININT 또는 \_SMSTaskSequence 폴더가 포함되지 않도록 합니다. 이러한 폴더를 삭제하려면 먼저 ImageX 유틸리티를 사용하여 WIM 파일을 탑재한 다음, 폴더를 삭제합니다.  

> [!NOTE]
>  WIM 파일에서 폴더를 삭제하려고 할 때 액세스 거부 오류가 발생하는 경우 명령 프롬프트 창을 열고 WIM 파일에 포함된 이미지의 루트로 전환한 다음, **RD MININT** 및 **RD \_ SMSTaskSequence**를 실행합니다.  

####  <a name="ZTIWindowsUpdate"></a> ZTIWindowsUpdate  
 **문제:** ZTIWindowsUpdate.wsf 스크립트를 사용하여 배포 시 소프트웨어 업데이트를 적용할 경우 이 스크립트는 Microsoft Update 웹 사이트와 직접 통신함으로서 필요한 Windows Update 에이전트 이진 파일을 다운로드 및 설치하고, 적용 가능한 소프트웨어 업데이트를 검색하고, 적용 가능한 소프트웨어 업데이트에 대한 이진 파일을 다운로드한 다음, 다운로드한 이진 파일을 설치할 수 있습니다. 이 프로세스에서는 네트워킹 인프라가 대상 컴퓨터가 Microsoft Update 웹 사이트에 액세스 권한을 얻을 수 있게 구성될 것을 요구합니다.  

 배포 공유가 Windows Update 에이전트 설치 파일을 포함하지 않고, 대상 컴퓨터에 적절한 인터넷 액세스 권한이 없는 경우 ZTIWindowsUpdate.log 및 BDD.log 파일에서 "wuredist.cab 찾을 수 없음"이란 오류가 보고됩니다.  

 **가능한 솔루션:** MDT 문서인 *Toolkit 참조*의 "ZTIWindowsUpdate.wsf" 섹션에 설명된 단계를 수행합니다.  

### <a name="deployment-shares"></a>배포 공유  
 배포 공유 관련 문제 및 솔루션을 검토합니다.  

-   [WIM 파일 업데이트 실패](#FailuretoUpdateWIMFiles)에 설명된 대로 배포 공유를 업데이트할 때 WIM 파일 업데이트가 실패합니다.  

####  <a name="FailuretoUpdateWIMFiles"></a> WIM 파일 업데이트 실패  
 "단순" 환경에서:  

-   MDT는 일반적으로 \(경로에서 항상\) C:\\Windows\\system32에서 WIMGAPI.DLL을 선택합니다. 이 WIMGAPI.DLL의 버전은 운영 체제의 \(빌드\) 버전과 일치해야 합니다.  

-   64\-비트 운영 체제에서 MDT는 항상 x64 WIMGAPI.DLL 파일을 사용하므로 해당 파일만 시스템 경로에 있어야 합니다. 32\-비트 운영 체제에서 MDT는 항상 x86 WIMGAPI.DLL 파일을 사용하므로 해당 파일만 시스템 경로에 있어야 합니다. \(Configuration Manager와 같은 다른 제품은 64\-비트 운영 체제에서도 WIMGAPI.DLL의 32\-비트 버전을 사용하지만 해당 버전을 관리하고 설치합니다.\)  

 **문제:** 배포 공유를 업데이트하려고 시도할 때 사용자는 하나 이상의 .wim 파일 탑재가 실패했다는 통보가 전달됩니다.  

 **가능한 솔루션:** 명령 프롬프트 창을 열고 **WIMGAPI.DLL**을 실행합니다. \(경로 검색으로 찾은 첫 번째 위치\) 목록에서 첫 번째 항목의 경우 **버전** 속성이 설치된 Windows ADK\(Windows 평가 및 배포 키트\)의 빌드와 일치하는지 확인합니다. 또한 속성이 운영 체제 빌드 번호와 일치하는지도 확인합니다.  

### <a name="the-windows-deployment-wizard"></a>Windows 배포 마법사  
 Windows 배포 마법사 관련 문제 및 솔루션을 검토합니다.  

-   [마법사 페이지 건너뛰기 안 됨](#WizardPagesareNotSkipped)에 설명된 대로 Windows 배포 마법사 페이지는 LTI가 마법사 페이지를 건너뛰도록 구성된 경우에도 표시됩니다.  

####  <a name="WizardPagesareNotSkipped"></a> 마법사 페이지 건너뛰기 안 됨  
 **문제:** MDT DB 또는 CustomSettings.ini 파일이 마법사를 건너뛰도록 지정한다고 해도 마법사 페이지가 표시됩니다.  

 **가능한 솔루션:** 제대로 마법사 페이지를 건너뛰려면 적절한 값과 함께 MDT DB 또는 CustomSettings.ini 파일에 적절한 해당 마법사 페이지에서 지정될 모든 속성을 포함합니다. 속성이 건너뛴 마법사 페이지에 대해 부적절하게 구성된 경우 해당 페이지가 표시됩니다. 마법사 페이지를 건너뛰는지 확인할 것을 요구하는 속성에 대한 자세한 내용은 MDT 문서인 *Toolkit 참조*에서 "건너뛴 배포 마법사 페이지에 대한 속성 제공"을 참조합니다.  

### <a name="disks-and-partitioning"></a>디스크 및 분할  
 디스크 분할 문제 및 솔루션을 검토합니다.  

-   [BitLocker 드라이브 암호화](#BitLockerDriveEncryption)에 설명된 대로 BitLocker® 드라이브 암호화 발급  

-   디스크 분할 오류에 설명된 대로 디스크 분할 오류  

-   [논리 및 동적 디스크에 대한 지원](#SupportforLoogicalandDynamicDisks)에 설명된 대로 논리 또는 동적 디스크로 인해 발생하는 컴퓨터 배포 시나리오 새로 고침 중의 실패  

####  <a name="BitLockerDriveEncryption"></a> BitLocker 드라이브 암호화  
 BitLocker 배포에는 적절한 배포를 위한 특정 구성이 필요합니다. 다음의 잠재적인 문제가 대상 컴퓨터의 구성과 관련돼 있을 수 있습니다.  

-   ["읽기 위해 'HKEY_CURRENT_USER\Control Panel\International\LocaleName' 레지스트리 키를 열 수 없습니다"라는 오류로 인한 ZTIBde.wsf 스크립트 실패](#ZTIBde.wsf)에 설명된 대로 ZTI 및 UDI 배포에서 ZTIBde.wsf 스크립트는 "레지스트리 키를 열 수 없습니다. '읽기 위해 ‘HKEY\_CURRENT\_USER\\Control Panel\\International\\LocaleName’ 레지스트리 키를 열 수 없습니다"라는 오류로 인해 실패합니다.  

-   [여러 드라이브 문자로 장치 표시](#DevicesAppearasMultipleDriveLetters)에서 설명된 대로 대상 컴퓨터에서 USB 장치, CD 드라이브, DVD 드라이브 또는 기타 이동식 미디어 장치는 여러 드라이브 문자로 표시됨  

-   [디스크 축소 문제](#ProblemswithShrinkingDisks)에 설명된 대로 대상 컴퓨터의 C 드라이브를 축소하면 비할당된 디스크 공간이 충분히 제공됨  

#####  <a name="ZTIBde.wsf"></a> ZTIBde.wsf 스크립트는 “읽기 위해 ‘HKEY\_CURRENT\_USER\\Control Panel\\International\\LocaleName’ 레지스트리 키를 열 수 없습니다”라는 오류로 인해 실패  
 **문제:** ZTI 또는 UDI에서 대상 컴퓨터에 BitLocker를 배포하는 동안 ZTIBde.wsf 스크립트는 “읽기 위해 ‘HKEY\_CURRENT\_USER\\Control Panel\\International\\LocaleName’ 레지스트리 키를 열 수 없습니다”라는 오류로 인해 실패합니다.  

 **가능한 솔루션:** **UILanguage** 속성에서 로캘을 지정합니다. ZTI 및 UDI에서 ZTIBde.wsf 스크립트는 시스템 컨트롤에서 실행되므로 전체 사용자 프로필이 로드되지 않습니다. ZTIBde.wsf 스크립트가 로캘 정보를 읽으려 할 때 \(사용자 프로필\) 레지스트리가 완전히 로드되지 않았기 때문에 이 정보는 레지스트리에 없습니다. 해결 방법으로 **UILanguage** 속성에서 로캘을 지정합니다.  

#####  <a name="DevicesAppearasMultipleDriveLetters"></a> 여러 드라이브 문자로 장치 표시  
 **문제:** 일부 장치는 분할되는 방법에 따라 여러 논리 드라이브 문자로서 표시할 수 있습니다. 일부 경우에 1.44\-메가바이트\(MB\) 플로피 디스크 드라이브 및 메모리 저장소 드라이브를 에뮬레이트할 수 입니다. 따라서 Windows는 플로피 디스크 에뮬레이션에 대해 동일한 장치 드라이브 문자 A 및 B, 메모리 저장소 드라이브에 대해 F를 할당할 수 있습니다. 기본적으로 MDT 스크립트는 가장 낮은 드라이브 문자, \(이 예제에서는 A\)를 사용합니다.  

 **가능한 솔루션:** Windows 배포 마법사의 **BitLocker 복구 상세 정보 지정** 페이지에서 기본 설정을 재정의합니다. Windows 배포 마법사 요약 페이지에는 BitLocker 복구 정보를 저장하기 위해 선택된 드라이브 문자에 대해 사용자에게 알려주는 경고 메시지가 표시됩니다. 또한 BDD.log 및 ZTIBDE.log 파일은 검색된 이동식 미디어 장치 및 장치가 BitLocker 복구 정보를 저장하기 위해 선택된 것을 기록합니다.  

#####  <a name="ProblemswithShrinkingDisks"></a> 디스크 축소 문제  
 **문제:** BitLocker를 사용하도록 설정하려면 대상 컴퓨터에 할당되지 않은 디스크 공간이 부족합니다. 대상 컴퓨터에 BitLocker를 배포하려면 시스템 볼륨을 만들기 위해 최소 2GB\(기가바이트\)의 할당되지 않은 디스크 공간이 필요합니다. *시스템 볼륨*은 BIOS가 컴퓨터를 부팅한 후 Windows를 로드하는 데 필요한 하드웨어\-특정 파일을 포함하는 볼륨입니다.  

 **가능한 솔루션 1:** 기존 컴퓨터에서 Diskpart 도구를 사용하여 C 드라이브를 축소함으로써 시스템 볼륨을 만들 수 있습니다. 그러나 일부 경우 C 드라이브 내의 조각난 디스크 공간 때문에 Diskpart 도구는 2GB의 할당되지 않은 디스크 공간을 제공할 정도로 충분히 C 드라이브를 축소할 수 없습니다.  

 이 문제에 대한 한 가지 가능한 솔루션은 C 드라이브를 조각 모음하는 것입니다. 그러려면 다음 단계를 수행합니다.  

1.  Diskpart **shrink querymax** 명령을 실행하여 할당될 수 없는 디스크 공간의 최대 크기를 식별합니다.  

2.  1단계에서 반환된 값이 2GB 이하인 경우 C 드라이브에서 불필요한 모든 파일을 지우고 조각 모음합니다.  

3.  Diskpart **shrink querymax** 명령을 다시 실행하여 2GB 초과 디스크 공간을 할당할 수 없는지 확인합니다.  

4.  3단계에서 반환된 값이 여전히 2GB 이하인 경우 다음 작업 중 하나를 수행합니다.  

    -   완전히 최적화되도록 C 드라이브 조각 모음을 여러 차례 수행합니다.  

    -   C 드라이브에 데이터를 백업하고 기존 파티션을 삭제하고 새 파티션을 만든 다음, 데이터를 새 파티션에 복원합니다.  

 **가능한 솔루션 2:** ZTIBDE.wsf 스크립트는 디스크 준비 도구\(bdehdcfg.exe\)를 실행하고 기본적으로 시스템 볼륨 파티션 크기를 2GB로 구성합니다. 필요한 경우 ZTIBDE.wsf 스크립트를 사용자 지정하여 기본값을 변경할 수 있습니다. 그러나 MDT 스크립트 수정은 권장하지 않습니다.  

####  <a name="SupportforLoogicalandDynamicDisks"></a> 논리 및 동적 디스크에 대한 지원  
 **문제:** 컴퓨터 배포 시나리오 새로 고침을 수행할 경우 논리 드라이브 또는 동적 디스크를 사용하는 대상 컴퓨터에 배포할 때 배포 프로세스는 실패할 수 있습니다.  

 **가능한 솔루션:** MDT는 논리 드라이브 또는 동적 디스크에 운영 체제 배포를 지원하지 않습니다.  

### <a name="domain-join"></a>도메인 가입  
 **문제:** 배포 동안 Windows 배포 마법사를 사용하여 자격 증명, 도메인 가입 정보 및 고정 IP 구성을 포함한 대상 컴퓨터에 필요한 모든 정보를 제공할 수 있습니다. 설치가 완료되면 시스템이 도메인에 가입하지 않고 여전히 작업 그룹에 있는 것을 확인할 수 있습니다.  

 **가능한 솔루션:** MDT의 LTI 배포는 운영 체제가 실행되고 나서 고정 IP 정보를 구성합니다. 대상 컴퓨터가 DHCP\(Dynamic Host Configuration Protocol\) 없는 네트워크 세그먼트에 위치한 경우 Unattend.xml에 지정된 자동 도메인 가입은 DHCP가 없으면 실패하게 됩니다.  

 작업 그룹에 가입하려면 Unattend.xml을 구성합니다. 그런 다음, 기본\-제공 **도메인에서 복구** 작업 순서 단계를 사용하여 고정 IP가 적용된 후 도메인에 가입하는 작업 순서에 단계를 추가합니다.  

### <a name="driver-installation"></a>드라이버 설치  
 최상의 사용자 환경을 확인하려면 하드웨어 장치 및 소프트웨어 드라이버 설치가 거의 또는 전혀 사용자 개입 없이 최대한 효율적으로 실행돼야 합니다. Microsoft는 이 목표를 충족하는 설치 패키지를 만들 수 있는 지침 및 도구를 제공합니다. 드라이버 설치에 대한 일반 내용은 [장치 및 드라이버 설치](http://www.microsoft.com/whdc/driver/install/default.mspx)를 참조합니다.  

 장치 드라이버 설치 관련 문제 및 솔루션을 검토합니다.  

-   $OEM$ 대용량 저장 장치 드라이버와 MDT 대용량 저장소 논리 결합에서 설명된 대로 MDT가 있는 $OEM$ 대용량 저장소 드라이버를 사용할 때 발생하는 문제  

-   [SetupAPI.log 사용하여 장치 설치 문제 해결](#TroubleshootDeviceInstallationwithSetupAPI.log)에 설명된 대로 SetupAPI.log를 사용하여 장치 드라이버 설치 문제 해결  

####  <a name="TroubleshootDeviceInstallationwithSetupAPI.log"></a> SetupAPI.log를 사용하여 장치 설치 문제 해결  
 [SetupAPI 로그 파일을 사용한 장치 설치 문제 해결](http://msdn.microsoft.com/windows/hardware/gg463393.aspx) 백서는 Windows 장치 설치 디버깅에 대한 정보를 제공합니다. 특히, 이 백서는 드라이버 개발자 및 테스터용 지침을 제공하여 SetupAPI 로그 파일을 해석합니다.  

 디버깅을 위해 가장 유용한 로그 파일 중 하나는 SetupAPI.log 파일입니다. 이 일반\-텍스트 파일은 SetupAPI가 장치 설치, 서비스 팩 설치 및 업데이트 설치에 대해 기록하는 정보를 유지 관리합니다. 특히, 이 파일은 가장 최근의 Windows 설치부터 주요 시스템 변경 뿐만 아니라 장치 및 드라이버 변경에 대한 기록을 유지 관리합니다. 이 백서에서는 장치 설치 문제를 해결하기 위해 SetupAPI 로그 파일을 사용하는 것에 중점을 두며 서비스 팩 및 업데이트 설치와 관련된 로그 파일 섹션에 대해 설명하지는 않습니다.  

### <a name="new-computer-deployments"></a>새 컴퓨터 배포  
 새 컴퓨터 배포 시나리오에 대한 문제 및 솔루션을 검토합니다.  

-   [PXE 부팅](#PXEBoot)에 설명된 대로 PXE\(Pre\-Boot Execution Environment\)를 사용하여 배포 프로세스를 시작하는 문제  

####  <a name="PXEBoot"></a> PXE 부팅  
 간단히 말해 PXE 프로토콜은 다음과 같이 작동합니다. 클라이언트 컴퓨터는 요청을 PXE 프로토콜을 구현하는 클라이언트 컴퓨터에서 오는 것으로 식별하는 확장을 포함한 DHCP 검색 패킷을 브로드캐스트하여 프로토콜을 시작합니다. 이 확장된 프로토콜을 구현하는 부팅 서버를 사용할 수 있다고 가정할 경우 부팅 서버는 클라이언트에 서비스를 제공할 서버의 IP 주소가 포함된 제안을 보냅니다. 클라이언트는 TFTP(Trivial File Transfer Protocol)를 사용하여 부팅 서버에서 실행 파일을 다운로드합니다. 마지막으로, 클라이언트 컴퓨터는 다운로드된 부트스트랩 프로그램을 실행합니다.  

 이 프로토콜의 초기 단계는 DHCP 메시지의 하위 집합에 편승하여 클라이언트가 \(새 컴퓨터 설치에 대해 실행 파일을 전달하는 서버\)인 부팅 서버를 검색할 수 있습니다. 그렇게 하려면 클라이언트 컴퓨터는 \(예상된 동작\)이기는 하지만 필요하지는 않은, IP 주소를 얻을 기회를 사용할 수 있습니다.  

 이 프로토콜의 두 번째 단계는 클라이언트 컴퓨터와 부팅 서버 사이에서 발생하며 통신에 대한 편리한 형식으로 DHCP 메시지 형식을 사용합니다. 그렇지 않은 경우 이 두 번째 단계는 표준 DHCP 서비스와 관련이 없습니다. 다음 일부 페이지는 PXE 클라이언트 컴퓨터 초기화 동안 단계\-별\-프로세스를 간략하게 설명합니다.  

 레거시 또는 혼합 모드에서 실행되는 Windows 배포 서비스에서 PXE 부팅\-관련 문제 해결에 대한 자세한 내용은 Microsoft 지원 문서 [PXE 클라이언트, DHCP 및 RIS 서버 간 PXE 상호 작용에 대한 설명](http://support.microsoft.com/kb/244036)을 참조합니다.  

 PXE 부팅 문제에 대한 다음 솔루션을 검토합니다.  

-   [Windows 배포 서비스의 Windows PE 로깅 사용 안 함](#DisableWindowsPELogginginWindowsDeploymentServices)에 설명된 대로 SetupAPI.log에 Windows PE 로깅을 사용하지 않도록 설정합니다.  

-   [적절한 DHCP 구성 확인](#EnsuretheProperDHCPConfiguration)에 설명된 대로 올바로 DHCP가 구성되었는지 확인합니다.  

-   [PXE IP 주소 할당 응답 시간 향상](#ImprovePXEIPAddressAssignmentResponseTime)에 설명된 대로 PXE 클라이언트 컴퓨터에 IP 주소 할당을 위한 응답 시간을 향상시킵니다.  

#####  <a name="DisableWindowsPELogginginWindowsDeploymentServices"></a> Windows 배포 서비스에서 Windows PE 로깅 사용하지 않도록 설정  
 권장하는 첫 번째 절차는 setupapi.log에 대한 로깅이 사용되지 않도록 확인하는 것입니다.  

#####  <a name="EnsuretheProperDHCPConfiguration"></a> 적절한 DHCP 구성 확인  
 사용 중인 라우터 모델에 따라 DHCP 브로드캐스트 전달의 특정 라우터 구성은 서브넷\(또는 라우터 인터페이스\) 또는 특정 호스트에 대해 지원될 수 있습니다. DHCP 서버와 Windows 배포 서비스를 실행하는 컴퓨터가 별도 컴퓨터인 경우 DHCP 브로드캐스트를 전달하는 라우터가 DHCP 및 Windows 배포 서비스 서버 모두에서 클라이언트 브로드캐스트를 수신하도록 설계됐는지 확인습니다. 그렇지 않으면 클라이언트 컴퓨터는 해당 원격 부팅 요청에 대한 회신을 받지 않습니다.  

 클라이언트 컴퓨터와 원격 설치 서버 간에 DHCP\-기반 요청 또는 응답을 허용하지 않는 라우터가 있습니까? Windows 배포 서비스 클라이언트 컴퓨터와 Windows 배포 서비스 서버가 별도 서브넷에 있는 경우 Windows 배포 서비스 서버에 DHCP 패킷을 전달하려면 두 시스템 간 라우터를 구성합니다. 이 정렬 작업이 필요한 이유는 Windows 배포 서비스 클라이언트 컴퓨터가 DHCP 브로드캐스트 메시지를 사용하여 Windows 배포 서비스 서버를 검색하기 때문입니다. 라우터에 DHCP 전달을 설정하지 않으면 클라이언트 컴퓨터의 DHCP 브로드캐스트는 Windows 배포 서비스 서버에 도달하지 못합니다. 이 DHCP 전달 프로세스는 라우터 구성 설명서에서 *DHCP 프록시* 또는 *IP 도우미 주소*로 언급되기도 합니다. 특정 라우터에 DHCP 전달 설정에 대한 자세한 내용은 라우터 지침을 참조하세요.  

#####  <a name="ImprovePXEIPAddressAssignmentResponseTime"></a> PXE IP 주소 할당 응답 시간 향상  
 PXE 클라이언트 컴퓨터가 IP 주소를 검색하는 데 시간이 \(15-20초\)로 오래 걸리는 경우 다음 요소를 확인합니다.  

-   대상 컴퓨터의 네트워크 어댑터와 스위치 또는 라우터가 같은 속도\(자동, 중복, 전체 등\)로 설정됩니까?  

-   연결되는 라우터의 IP 도우미 파일에서 Windows 배포 서비스 서버에 대한 IP 주소입니까? IP 도우미 파일에서 IP 주소 목록이 긴 경우 상단 근처의 Windows 배포 서비스 서버에 대한 주소를 이동할 수 있습니까?  

### <a name="restarting-the-deployment-process"></a>배포 프로세스 다시 시작  
 **문제:** 새로운 또는 수정된 작업 순서를 테스트하고 문제를 해결하는 동안 배포 프로세스가 처음부터 다시 시작할 수 있도록 대상 컴퓨터를 다시 시작해야 할 수도 있습니다. MDT가 하드 디스크에 데이터를 기록하여 그 진행 상태를 계속 추적하기 때문에 예기치 않은 결과가 발생할 수 있습니다. 따라서 대상 컴퓨터를 다시 시작하면 MDT가 이전에 다시 시작할 때 중단된 위치에서 다시 시작할 수 있습니다.  

 **가능한 솔루션:** 배포 프로세스를 처음부터 다시 시작하게 하려면 대상 컴퓨터를 다시 시작하기 전에 C:\\MININT 및 C:\\\_SMSTaskSequence 폴더를 삭제합니다.  

### <a name="sysprep"></a>Sysprep  
 Sysprep\-관련 문제 및 솔루션을 검토합니다.  

-   [잘못된 OU의 컴퓨터 계정](#ComputerAccountisintheWrongOU)에 설명된 대로 대상 컴퓨터는 올바른 AD DS OU에 나타나지 않습니다.  

####  <a name="ComputerAccountisintheWrongOU"></a> 잘못된 OU의 컴퓨터 계정  
 **문제:** 대상 컴퓨터가 제대로 도메인에 가입되어 있지만 컴퓨터 계정이 잘못된 OU에 있습니다.  

 **가능한 솔루션 1:** 계정이 대상 컴퓨터에 대해 사전\-존재하는 경우 해당 계정은 원래 OU에 남아 있습니다. 계정을 지정된 OU로 이동하려면 Microsoft Visual Basic® Scripting Edition 등의 자동화 도구를 사용하는 작업 순서 단계를 추가하여 계정을 이동합니다.  

 **가능한 솔루션 2:** 지정된 OU가 올바른 형식이며 존재하는지 확인합니다. 올바른 OU 형식은 `OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`이어야 합니다.  

### <a name="configuration-manager"></a>Configuration Manager  
 **문제:** REF \_Ref308174600 \\h 그림 3에 표시된 오류 메시지는 **자체\-서명된 PXE 인증서 만들기** 옵션을 사용하여 Configuration Manager PXE 서비스 지점을 만들려 하는 경우 표시됩니다.  

 ![TroubleshootingReference3](media/TroubleshootingReference3.jpg "TroubleshootingReference3")  
그림 SEQ 그림 \\\* ARABIC 3. PXE 서비스 지점 오류  

 **그림 SEQ 그림 \\\* ARABIC 3. PXE 서비스 지점 오류**  

 **가능한 솔루션:** PXE 서비스 지점이 구성하는 서버에 이전에 존재했던 경우 PXE 서비스 지점은 자체\-제작된 인증서를 제거할 때 삭제할 수 없습니다. *사용자\_이름*이 이전 구성을 수행했거나 현재 구성을 수행하는 사용자의 이름인 경우 C:\\Documents and Settings\\*user\_name*\\Application Data\\Microsoft\\Crypto\\RSA에서 PXE 인증서 폴더를 삭제합니다. Configuration Manager 콘솔에서 새 사이트 역할 마법사는 폴더를 삭제한 경우 성공적으로 완료해야 합니다.  

### <a name="task-sequences"></a>작업 순서  
 작업 순서 관련 문제 및 솔루션을 검토합니다.  

-   [작업 순서가 성공적으로 완료되지 않았습니다](#TaskSequenceDoesNotFinishSuccessfully)에 설명된 대로 작업 순서가 성공적으로 완료되지 않거나 예기치 않은 동작이 있습니다.  

-   [OEM 작업 순서가 다른 프로세서 아키텍처용으로 만들어진 부팅 이미지에 대해 잘못 표시됩니다](#OEMTaskSequenceIncorrectlyAppearsforBootImage)에 설명된 대로 LTI에서 OEM\(Original equipment manufacturer\) 작업 순서는 반대쪽 프로세서 아키텍처를 사용하여 부팅 이미지에 나열됩니다.  

-   [Windows 배포 마법사의 잘못된 작업 순서 항목(잘못된 OS GUID) 메시지](#BadTaskSequenceItem)에 설명된 대로 Windows 배포 마법사는 "잘못된 작업 순서 항목\(잘못된 OS GUID\)"라는 오류 메시지를 표시합니다.  

-   [네트워크 설정 적용](#ApplyNetworkSettings)에 설명된 대로 네트워크 연결 이름을 구성하는 동안 "네트워크 어댑터에 올바른 이름을 입력하십시오"라는 메시지가 표시됩니다.  

-   [오류 발생 시 계속 사용](#UseContinueonError)에 설명된 대로 부적절한 구성으로 인해 발생할 수 있는 문제는 작업 순서 단계에 대한 오류 구성 설정을 계속 사용합니다.  

####  <a name="TaskSequenceDoesNotFinishSuccessfully"></a> 작업 순서가 성공적으로 완료되지 않음  
 **문제:** 작업 순서가 성공적으로 완료되지 않거나 예기치 않은 동작이 있을 수 있습니다.  

 **가능한 솔루션:** \(LTI용\) **운영 체제 설치** 작업 순서 단계 또는 \(ZTI 및 UDI용\) **운영 체제 이미지 적용** 작업 순서 단계는 작업 순서 단계 만들기가 예기치 않은 결과로 나타난 후 수정됐을 수 있습니다. 예를 들어 작업 순서가 32\-비트 Windows 8.1 이미지를 배포하도록 만들어진 다음, 나중에 **운영 체제 설치** 작업 순서 단계 또는 **운영 체제 이미지 적용** 작업 순서 단계가 64\-비트 Windows 8.1 이미지를 참조하도록 변경된 경우 작업 순서는 성공적으로 실행되지 않을 수 있습니다.  

 다른 운영 체제 이미지를 배포하도록 새 작업 순서를 만드는 것이 좋습니다.  

####  <a name="OEMTaskSequenceIncorrectlyAppearsforBootImage"></a> OEM 작업 순서가 다른 프로세서 아키텍처용으로 만들어진 부팅 이미지에 대해 잘못 표시됨  
 **문제:** LTI OEM 작업 순서 템플릿을 기반으로 한 작업 순서는 다른 프로세서 아키텍처를 사용하여 부팅 이미지에 표시됩니다. 예를 들어 64\-비트 운영 체제를 배포하는 OEM 작업 순서는 32\-비트 부팅 이미지에 표시됩니다.  

 **가능한 솔루션:** LTI에서 OEM 작업 순서는 "플랫폼\-종속"으로 간주되지 않기 때문에 정상적인 동작은 부팅 이미지의 프로세서 아키텍처에 관계 없이 항상 표시될 것입니다.  

####  <a name="BadTaskSequenceItem"></a> Windows 배포 마법사의 잘못된 작업 순서 항목\(잘못된 OS GUID\) 메시지  
 **문제:** Windows 배포 마법사를 실행하는 경우 마법사는 "잘못된 작업 순서 항목\(잘못된 OS GUID\)"라는 오류 메시지를 표시합니다. 운영 체제는 OperatingSystem.xml 파일에는 나열되지만 워크 벤치에는 표시되지 않습니다.  

 **가능한 솔루션:** 원래 운영 체제 원본은 두 개 이상의 WIM 파일이 연결돼 있습니다. 작업 순서와 연결된 SKU는 삭제되지만 운영 체제 원본에 대한 다른 SKU는 여전히 남아 있습니다. 삭제된 SKU를 참조하는 작업 순서가 Windows 배포 마법사의 **해당 컴퓨터에서 실행되는 작업 순서 선택** 마법사 페이지에서 선택되는 경우 **다음**을 클릭한 후 "잘못된 작업 순서 항목\(잘못된 OS GUID\)"라는 오류 메시지가 마법사 페이지에서 표시됩니다.  

 이 문제를 해결하려면 다음 작업 중 하나를 수행합니다.  

-   모든 SKU를 운영 체제 소스에서 제거합니다. Windows 배포 마법사가 정상적으로 동작하고 오류 메시지가 표시되지 않습니다.  

-   다른 운영 체제 이미지를 사용하려면 작업 순서를 변경합니다.  

####  <a name="ApplyNetworkSettings"></a> 네트워크 설정 적용  
 **문제:** 배포 워크 벤치에서 네트워크 연결 이름을 구성하는 경우 유효성 검사 오류가 "네트워크 어댑터에 대해 올바른 이름을 입력하십시오"라는 메시지와 함께 나타납니다.  

 **가능한 솔루션:** 지정된 연결 이름에서 모든 공백 및 잘못된 문자를 제거합니다.  

####  <a name="UseContinueonError"></a> 오류 발생 시 계속 사용  
 MDT 작업 순서가 오류 발생 시 계속되지 않도록 구성되고 해당 작업 순서가 오류를 반환하는 경우 해당 작업 순서 그룹에서 나머지 작업 순서는 모두 건너뜁니다. 그러나 나머지 작업 순서 그룹은 처리됩니다. 다음 사항을 고려합니다.  

 두 개의 작업 순서 그룹을 만들었으며 각 그룹은 두 개 이상의 작업 순서 단계를 포함합니다.  

-   A그룹  

    -   A단계  

    -   B단계  

-   B그룹  

    -   A단계  

    -   B단계  

 A그룹\\A단계가 오류 발생 시 계속하지 않도록 구성된 경우 A그룹\\B단계는 처리되지 않습니다. 그러나 B그룹의 모든 작업 순서 단계는 처리됩니다.  

### <a name="the-user-state-migration-tool"></a>사용자 상태 마이그레이션 도구  
 USMT\-관련 문제 및 솔루션을 검토합니다.  

-   네트워크 공유 폴더에 저장된 문서를 가리키는 바로 가기는 [바탕 화면 바로 가기 누락](#MissingDesktopShortcuts)에 설명된 대로 제대로 복원되지 않을 수 있습니다.  

####  <a name="MissingDesktopShortcuts"></a> 누락된 바탕 화면 바로 가기  
 **문제:** 사용자 데이터를 마이그레이션하기 위해 USMT를 사용하는 경우 네트워크 문서를 가리키는 바로 가기는 복원되지 않을 수 있습니다. 바로 가기는 Scanstate 도중 캡처되지만 Loadstate 도중 대상 컴퓨터에는 절대 복원되지 않습니다.  

 **가능한 솔루션:** 다음 줄에서 MigUser.xml 파일 및 주석을 편집합니다.  

 원본:  

```  
<include> filter='MigXmlHelper.IgnoreIrrelevantLinks()'>  
```  

 수정됨:  

```  
<include> <!-- filter='MigXmlHelper.IgnoreIrrelevantLinks()'> -->  
```  

### <a name="windows-imaging-format-files"></a>Windows 이미징 서식 파일  
 WIM\-관련 문제 및 솔루션을 검토합니다.  

-   [WIM 파일 손상](#CorruptWIMFile)에 설명된 대로 LTI 및 ZTI 배포는 BDD.log 파일에서 WIM 파일 오류로 실패합니다.  

####  <a name="CorruptWIMFile"></a> WIM 파일 손상  
 **문제:** 이미지를 배포할 때 배포는 BDD.log 파일에서 다음 항목으로 인해 실패합니다.  

-   ```  
    The image \\Server\Deployment$\Operating Systems\Windows\version1.wim was not applied successfully by ImageX, rc = 2  
    ```  

-   ```  
    LTIApply COMPLETED.  Return Value = 2  
    ```  

-   ```  
    ZTI ERROR - Non-zero return code by LTIApply, rc = 2  
    ```  

 ImageX를 사용하여 WIM 파일을 탑재함으로써 문제를 조사하면 "데이터가 잘못되었습니다"라는 오류가 발생합니다. 추가 조사는 .wim 파일의 날짜 스탬프가 현재 날짜보다 여러 해 전임을 보여줍니다. 읽기 또는 쓰기 프로세스의 최종 단계에서 .wim 파일이 이전에 닫힌 후 바이러스 검색 프로그램 같은 다른 프로세스가 해당 파일을 열 수 있습니다.  

 **가능한 솔루션:** .wim 파일을 백업 미디어에서 복원합니다.  

### <a name="windows-pe"></a>Windows PE  
 Windows PE 관련 문제 및 솔루션을 검토합니다.  

-   [배포 프로세스가 시작되지 않음-한정된 RAM 또는 무선 네트워크 어댑터](#LimitedRamorWirelessNetworkAdapter)에 설명된 대로 LTI 또는 ZTI 배포 프로세스는 부족한 RAM 또는 무선 네트워크 어댑터 때문에 시작되지 않습니다.  

-   [배포 프로세스가 시작되지 않음-누락된 구성 요소](#MissingComponents)에 설명된 대로 LTI 또는 ZTI 배포 프로세스는 누락된 Windows PE 구성 요소 때문에 시작되지 않습니다.  

-   [배포 프로세스가 시작되지 않음-누락되거나 잘못된 드라이버](#MissingorIncorrectDrivers)에 설명된 대로 LTI 또는 ZTI 배포 프로세스는 누락되거나 잘못된 장치 드라이버 때문에 시작되지 않습니다.  

####  <a name="LimitedRamorWirelessNetworkAdapter"></a> 배포 프로세스 시작되지 않음-한정된 RAM 또는 무선 네트워크 어댑터  
 **문제:** 특정 대상 컴퓨터에 이미지를 배포할 때 Windows PE가 시작하고 **wpeinit**을 실행하고 명령 프롬프트 창을 열지만 실제로 배포 프로세스를 시작하지는 않습니다. 대상 컴퓨터에서 네트워크 드라이브를 매핑하여 문제를 해결하는 것은 네트워크 어댑터 드라이버가 로드되지 않았다는 것을 나타냅니다.  

 **가능한 솔루션 1:** RAM이 충분하지 않아 배포 마법사가 시작되지 않습니다. 대상 컴퓨터에 최소 512MB RAM이 있는지 그리고 공유 비디오 메모리가 512MB 중 64MB를 초과해서 소모하지 않는지 확인합니다.  

 MDT가 지원하는 Windows PE 버전은 RAM이 512MB 이하인 대상 컴퓨터에서는 실행할 수 없습니다.  

 **가능한 솔루션 2:** Windows PE 이미지에 무선 드라이버를 포함하지 마십시오.  

####  <a name="MissingComponents"></a> 배포 프로세스가 시작되지 않음-누락된 구성 요소  
 **문제:** 실패한 배포 문제를 해결하려면 BDD.log 파일을 검토해서 다음 항목을 나열합니다.  

```  
ERROR - Unable to create ADODB.Connection object, impossible to query SQL Server: ActiveX component can't create object (429).  
```  

 **가능한 솔루션:** 이 오류는 Windows PE 이미지가 MDT를 사용하여 만들어지지 않았음을 나타낼 수 있습니다. Configuration Manager를 사용하는 경우 Configuration Manager가 만든 기존 Windows PE 이미지 중 하나를 사용하는 대신 Microsoft 배포 작업 순서 가져오기 마법사를 사용하여 이미지를 만듭니다.  

> [!NOTE]
>  Configuration Manager에서 만든 Windows PE 이미지는 스크립팅, XML 및 WMI(Windows Management Instrumentation)를 지원하는 구성 요소를 포함하지만 Microsoft ADO(ActiveX Data Objects)를 지원하는 구성 요소는 포함하지 않습니다.  

####  <a name="MissingorIncorrectDrivers"></a> 배포 프로세스가 시작되지 않음-누락되거나 잘못된 드라이버  
 **문제:** 특정 대상 컴퓨터에 배포할 때 Windows PE가 시작하고 **wpeinit**을 실행하고 명령 프롬프트 창을 열지만 실제로 배포 프로세스를 시작하지는 않습니다. 대상 컴퓨터에서 네트워크 드라이브를 매핑하여 문제를 해결하는 것은 네트워크 어댑터 드라이버가 로드되지 않았다는 것을 나타냅니다. *X*:\Windows\System32\Inf에 있는 SetupAPI.log 파일의 검토를 통해 Windows PE가 네트워크 어댑터를 구성하는 경우 오류를 발생시키며 그 중 한 오류는 "이 드라이버는 이 플랫폼을 위한 것이 아닙니다"라는 것을 나타냅니다. **기본 드라이버** 목록에서 드라이버가 이미지에 삽입되었습니다.  

 **가능한 솔루션:** Windows PE에 다른 드라이버와 충돌하는 드라이버가 있을 수 있습니다. Deployment Workbench에서 Windows PE 이미지에 대해 설정을 구성하는 경우 네트워크 어댑터와 저장소 드라이버만 포함하는 Windows PE 드라이버 그룹을 만든 다음, Windows PE 드라이버 그룹만 사용하는 배포 공유를 구성합니다.  

## <a name="deployment-process-flow-charts"></a>배포 프로세스 흐름도  
 이 섹션에서는 Configuration Manager를 사용한 LTI 배포 및 ZTI 배포용의 두 가지 MDT 흐름도 집합을 제공합니다. 각 흐름도는 해당 배포 유형 동안 실행된 작업을 보여줍니다.  

 다음을 통해 배포 프로세스 흐름도에 익숙해지십시오.  

-   [LTI 배포 프로세스 흐름도](#LTIDeploymentProcessFlowcharts)에 설명된 대로 LTI 배포 프로세스 흐름도 검토  

-   [ZTI 배포 프로세스 흐름도](#ZTIDevelopmentProcessFlowcharts)에 설명된 대로 ZTI 배포 프로세스 흐름도 검토  

###  <a name="LTIDeploymentProcessFlowcharts"></a> LTI 배포 프로세스 흐름도  
 다음 단계에 대해 흐름도가 제공됩니다.  

-   유효성 검사(그림 4)  

-   상태 캡처(그림 5 및 그림 6)  

-   사전 설치(그림 7, 그림 8 및 그림 9)  

-   설치(그림 10)  

-   사후 설치(그림 11 및 그림 12)  

-   상태 복원(그림 13, 그림 14, 그림 15 및 그림 16)  

 ![TroubleshootingReference4](media/TroubleshootingReference4.jpg "TroubleshootingReference4")  
그림 4. 유효성 검사 단계에 대한 흐름도  

 **그림 4. 유효성 검사 단계에 대한 흐름도**  

 ![TroubleshootingReference5](media/TroubleshootingReference5.jpg "TroubleshootingReference5")  
그림 5. 상태 캡처 단계(1/2)에 대한 흐름도  

 **그림 5. 상태 캡처 단계(1/2)에 대한 흐름도**  

 ![TroubleshootingReference6](media/TroubleshootingReference6.jpg "TroubleshootingReference6")  
그림 6. 상태 캡처 단계(2/2)에 대한 흐름도  

 **그림 6. 상태 캡처 단계(2/2)에 대한 흐름도**  

 ![TroubleshootingReference7](media/TroubleshootingReference7.jpg "TroubleshootingReference7")  
그림 7. 사전 설치 단계(1/3)에 대한 흐름도  

 **그림 7. 사전 설치 단계(1/3)에 대한 흐름도**  

 ![TroubleshootingReference8](media/TroubleshootingReference8.jpg "TroubleshootingReference8")  
그림 8. 사전 설치 단계(2/3)에 대한 흐름도  

 **그림 8. 사전 설치 단계(2/3)에 대한 흐름도**  

 ![TroubleshootingReference9](media/TroubleshootingReference9.jpg "TroubleshootingReference9")  
그림 9. 사전 설치 단계(3/3)에 대한 흐름도  

 **그림 9. 사전 설치 단계(3/3)에 대한 흐름도**  

 ![TroubleshootingReference10](media/TroubleshootingReference10.jpg "TroubleshootingReference10")  
그림 10. 설치 단계에 대한 흐름도  

 **그림 10. 설치 단계에 대한 흐름도**  

 ![TroubleshootingReference11](media/TroubleshootingReference11.jpg "TroubleshootingReference11")  
그림 11. 사후 설치 단계(1/2)에 대한 흐름도  

 **그림 11. 사후 설치 단계(1/2)에 대한 흐름도**  

 ![TroubleshootingReference12](media/TroubleshootingReference12.jpg "TroubleshootingReference12")  
그림 12 사후 설치 단계(2/2)에 대한 흐름도  

 **그림 12 사후 설치 단계(2/2)에 대한 흐름도**  

 ![TroubleshootingReference13](media/TroubleshootingReference13.jpg "TroubleshootingReference13")  
그림 13. 상태 복원 단계(1/4)에 대한 흐름도  

 **그림 13. 상태 복원 단계(1/4)에 대한 흐름도**  

 ![TroubleshootingReference14](media/TroubleshootingReference14.jpg "TroubleshootingReference14")  
그림 14. 상태 복원 단계(2/4)에 대한 흐름도  

 **그림 14. 상태 복원 단계(2/4)에 대한 흐름도**  

 ![TroubleshootingReference15](media/TroubleshootingReference15.jpg "TroubleshootingReference15")  
그림 15. 상태 복원 단계(3/4)에 대한 흐름도  

 **그림 15. 상태 복원 단계(3/4)에 대한 흐름도**  

 ![TroubleshootingReference16](media/TroubleshootingReference16.jpg "TroubleshootingReference16")  
그림 16. 상태 복원 단계(4/4)에 대한 흐름도  

 **그림 16. 상태 복원 단계(4/4)에 대한 흐름도**  

###  <a name="ZTIDevelopmentProcessFlowcharts"></a> ZTI 배포 프로세스 흐름도  
 흐름도는 Configuration Manager를 사용한 ZTI 배포의 다음 단계에 대해 제공됩니다.  

-   초기화(그림 17)  

-   유효성 검사(그림 18)  

-   상태 캡처(그림 19)  

-   사전 설치(그림 20)  

-   설치(그림 21)  

-   사후 설치(그림 22)  

-   상태 복원(그림 23 및 그림 24)  

-   캡처(그림 25)  

 ![TroubleshootingReference17](media/TroubleshootingReference17.jpg "TroubleshootingReference17")  
그림 17. 초기화 단계에 대한 흐름도  

 **그림 17. 초기화 단계에 대한 흐름도**  

 ![TroubleshootingReference18](media/TroubleshootingReference18.jpg "TroubleshootingReference18")  
그림 18. 유효성 검사 단계에 대한 흐름도  

 **그림 18. 유효성 검사 단계에 대한 흐름도**  

 ![TroubleshootingReference19](media/TroubleshootingReference19.jpg "TroubleshootingReference19")  
그림 19. 상태 캡처 단계에 대한 흐름도  

 **그림 19. 상태 캡처 단계에 대한 흐름도**  

 ![TroubleshootingReference20](media/TroubleshootingReference20.jpg "TroubleshootingReference20")  
그림 20. 사전 설치 단계에 대한 흐름도  

 **그림 20. 사전 설치 단계에 대한 흐름도**  

 ![TroubleshootingReference21](media/TroubleshootingReference21.jpg "TroubleshootingReference21")  
그림 21. 설치 단계에 대한 흐름도  

 **그림 21. 설치 단계에 대한 흐름도**  

 ![TroubleshootingReference22](media/TroubleshootingReference22.jpg "TroubleshootingReference22")  
그림 22. 사후 설치 단계에 대한 흐름도  

 **그림 22. 사후 설치 단계에 대한 흐름도**  

 ![TroubleshootingReference23](media/TroubleshootingReference23.jpg "TroubleshootingReference23")  
그림 23. 상태 복원 단계(1/2)에 대한 흐름도  

 **그림 23. 상태 복원 단계(1/2)에 대한 흐름도**  

 ![TroubleshootingReference24](media/TroubleshootingReference24.jpg "TroubleshootingReference24")  
그림 24. 상태 복원 단계(2/2)에 대한 흐름도  

 **그림 24. 상태 복원 단계(2/2)에 대한 흐름도**  

 ![TroubleshootingReference25](media/TroubleshootingReference25.jpg "TroubleshootingReference25")  
그림 25. 캡처 단계에 대한 흐름도  

 **그림 25. 캡처 단계에 대한 흐름도**  

## <a name="finding-additional-help"></a>추가 도움말 찾기  
 다음을 통한 MDT 배포 문제 해결에서 추가 도움말을 찾습니다.  

-   [Microsoft 지원](#MicrosoftSupport)에 설명된 대로 Microsoft 지원에 문의  

-   [인터넷 지원](#InternetSupport)에 설명된 대로 블로그 및 기타 인터넷 리소스를 통해 추가 지원 가져오기  

###  <a name="MicrosoftSupport"></a> Microsoft 지원  
 Microsoft는 Microsoft Deployment Toolkit에 대해 프리미어 및 전문가 수준의 지원을 제공합니다.  

 전문가 수준의 지원: [http://support.microsoft.com/](http://support.microsoft.com/)  

 프리미어 수준의 지원: [https://premier.microsoft.com/](https://premier.microsoft.com/)  

> [!NOTE]
>  지원에 문의하는 경우 MDT 및 특정 버전에 문제가 있는지 확인합니다.  

###  <a name="InternetSupport"></a> 인터넷 지원  
 많은 온라인 소스는 이 참조에서 다룬 것 이외에 MDT에 대한 추가 문제 해결 지원을 제공합니다. 이러한 온라인 소스는 다음과 같습니다.  

-   Microsoft 호스팅 블로그  

    -   [MDT 팀 블로그](http://blogs.technet.com/b/msdeployment/)  

    -   [Configuration Manager 팀 블로그](http://blogs.technet.com/b/configmgrteam/)  

    -   [Michael Niehaus 블로그](http://blogs.technet.com/b/mniehaus/)(Michael Niehaus는 Windows 및 Microsoft Office 배포에 대해 글을 씁니다.)  

-   Microsoft에서 호스팅하는 뉴스 그룹 및 포럼입니다.  

     다음 뉴스 그룹 및 포럼은 Microsoft 직원, 업계 동료 및 Microsoft Valued Professional에서 지원을 받을 수 있습니다.  

    -   [Configuration Manager - 운영 체제 배포](http://social.technet.microsoft.com/Forums/home?forum=configmanagerosd)  

    -   [Windows 8 설치, 설정 및 배포](http://social.technet.microsoft.com/Forums/windows/home?forum=w8itproinstall)  

-   Microsoft 외부에서의 배포 관련 정보 소스입니다.  

    -   [DeployVista.com](http://www.deployvista.com/)  

    -   [myITforum.com](http://www.myitforum.com/)
