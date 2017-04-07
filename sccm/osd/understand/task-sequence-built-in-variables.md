---
title: "작업 순서 기본 제공 변수 | Microsoft 문서"
description: "작업 순서 기본 제공 변수는 작업 순서가 실행되고 전체 작업 순서 동안 사용할 수 있는 환경에 대한 정보를 제공합니다."
ms.custom: na
ms.date: 03/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 02bc6bd4-ca53-4e22-8b80-d8ee5fe72567
caps.latest.revision: 15
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: a3e6cca8d58055cc2d54aff3cb70a276fb40e829
ms.lasthandoff: 03/27/2017


---
# <a name="task-sequence-built-in-variables-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 작업 순서 기본 제공 변수

*적용 대상: System Center Configuration Manager(현재 분기)*


 작업 순서 기본 제공 변수는 System Center Configuration Manager에서 제공됩니다. 기본 제공 변수는 작업 순서가 실행 중인 환경에 대한 정보를 제공하며, 전체 작업 순서에서 해당 값을 사용할 수 있습니다. 일반적으로 기본 제공 변수는 작업 순서에서 단계를 실행하기 전에 초기화됩니다. 예를 들어 기본 제공 변수 **_SMSTSLogPath**는 작업 순서가 실행되는 동안 Configuration Manager 구성 요소에서 로그 파일을 작성하는 데 사용하는 경로를 지정하는 환경 변수입니다. 모든 작업 순서 단계에서 이 환경 변수에 액세스할 수 있습니다. 그러나 &#95;SMSTSCurrentActionName과 같은 일부 변수는 각 단계 전에 평가됩니다. 기본 제공 변수 값은 일반적으로 읽기 전용입니다. 이름이 밑줄로 시작하는 기본 제공 변수의 값만 읽기 전용입니다.  

## <a name="task-sequence-built-in-variable-list"></a>작업 순서 기본 제공 변수 목록  
 다음 목록에서는 Configuration Manager에서 사용할 수 있는 기본 제공 변수를 설명합니다.  

|기본 제공 변수 이름|설명|  
|-----------------------------|-----------------|  
|_OSDDetectedWinDir|Configuration Manager 버전 1602부터, Windows PE가 시작될 때 작업 순서가 컴퓨터의 하드 드라이브에서 이전 운영 체제 설치를 검색합니다. Windows 폴더 위치가 이 변수에 저장됩니다. 환경에서 이 값을 검색하도록 작업 순서를 구성하고 이를 사용하여 새 운영 체제 설치에 사용할 동일한 Windows 폴더 위치를 지정할 수 있습니다.|  
|_OSDDetectedWinDrive|Configuration Manager 버전 1602부터, Windows PE가 시작될 때 작업 순서가 컴퓨터의 하드 드라이브에서 이전 운영 체제 설치를 검색합니다.  운영 체제가 설치되어 있는 하드 드라이브 위치가 이 변수에 저장됩니다. 환경에서 이 값을 검색하도록 작업 순서를 구성하고 이를 사용하여 새 운영 체제에 사용할 동일한 하드 드라이브 위치를 지정할 수 있습니다.|  
|_SMSTSAdvertID|현재 실행 중인 작업 순서 배포의 고유 ID를 저장합니다. Configuration Manager 소프트웨어 배포의 배포 ID와 동일한 형식을 사용합니다. 독립 실행형 미디어에서 작업 순서를 실행 중인 경우에는 이 변수가 정의되지 않습니다.<br /><br /> 예:<br /><br /> **ABC20001**|  
|_TSAppInstallStatus|응용 프로그램 설치 작업 순서 단계 중에 작업 순서가 응용 프로그램의 설치 상태를 사용하여 _TSAppInstallStatus 변수를 설정합니다. 작업 순서는 이 변수를 다음 값 중 하나로 설정합니다.<br /><br /> 1.  **정의되지 않음**: 응용 프로그램 설치 작업 순서 단계를 실행하지 않은 경우에 설정합니다.<br />2.  **오류**: 응용 프로그램 설치 작업 순서 단계 중에 응용 프로그램 하나 이상이 오류 때문에 실패한 경우에 설정합니다.<br />3.  **경고**: 응용 프로그램 설치 작업 순서 단계 중에 오류는 발생하지 않았지만 요구 사항이 충족되지 않아 하나 이상의 응용 프로그램이나 필수 종속성이 설치되지 않은 경우에 설정됩니다.<br />4.  **성공**: 응용 프로그램 설치 작업 순서 단계 중에 오류 또는 경고가 감지되지 않은 경우에 설정합니다.|  
|_SMSTSBootImageID|부팅 이미지 패키지가 현재 실행 중인 작업 순서와 연결된 경우 Configuration Manager 부팅 이미지 패키지 ID를 저장합니다. 연결된 Configuration Manager 부팅 이미지 패키지가 없는 경우에는 이 변수가 설정되지 않습니다.<br /><br /> 예제:<br /><br /> **ABC00001**|  
|_SMSTSBootUEFI|작업 순서에서는 UEFI 모드의 컴퓨터를 발견한 경우 _SMSTSBootUEFI 변수를 설정합니다.|  
|_SMSTSClientGUID|Configuration Manager 클라이언트 GUID의 값을 저장합니다. 작업 순서가 독립 실행형 미디어에서 실행 중인 경우에는 이 변수가 설정되지 않습니다.<br /><br /> 예:<br /><br /> **0a1a9a4b-fc56-44f6-b7cd-c3f8ee37c04c**|  
|_SMSTSCurrentActionName|현재 실행 중인 작업 순서 단계의 이름을 지정합니다. 이 변수는 작업 순서 관리자가 각 개별 단계를 실행하기 전에 설정됩니다.<br /><br /> 예:<br /><br /> **명령줄 실행**|  
|_SMSTSDownloadOnDemand|현재 작업 순서가 요청 다운로드 모드로 실행되는 경우 **true** 로 설정합니다. 이 경우 작업 순서 관리자는 콘텐츠에 액세스해야 하는 경우에만 콘텐츠를 로컬로 다운로드합니다.|  
|_SMSTSInWinPE|이 변수는 현재 작업 순서 단계가 Windows PE 환경에서 실행되는 경우 **true** 로 설정되고, 그렇지 않으면 **false** 로 설정됩니다. 이 작업 순서 변수를 테스트하여 현재 운영 체제 환경을 확인할 수 있습니다.|  
|_SMSTSLastActionRetCode|마지막으로 실행된 동작에서 반환된 반환 코드를 저장합니다. 이 변수를 다음 단계 실행 여부를 결정하는 조건으로 사용할 수 있습니다.<br /><br /> 예:<br /><br /> **0**|  
|_SMSTSLastActionSucceeded|이 변수는 마지막 동작에 성공한 경우 **true** 로 설정되고, 마지막 동작에 실패한 경우 **false** 로 설정됩니다. 단계가 사용할 수 없도록 설정되거나 관련 조건이 **false**로 평가되어 마지막 동작을 건너뛴 경우에는 이 변수가 다시 설정되지 않습니다. 즉, 이전 동작의 값을 계속 유지합니다.|  
|_SMSTSLaunchMode|작업 순서 시작 방법을 지정합니다. 작업 순서는 다음과 같은 값을 가질 수 있습니다.<br /><br /> -   **SMS** - 작업 순서가 Configuration Manager 클라이언트를 통해 시작되도록 지정합니다.<br />-   **UFD** - 작업 순서가 Windows XP/2003에서 만들어진 USB 미디어를 통해 시작되도록 지정합니다.<br />-   **UFD+FORMAT** - 작업 순서가 Windows Vista 이상에서 만들어진 USB 미디어를 통해 시작되도록 지정합니다.<br />-   **CD** - 작업 순서가 CD를 통해 시작되도록 지정합니다.<br />-   **DVD** - 작업 순서가 DVD를 통해 시작되도록 지정합니다.<br />-   **PXE** - 작업 순서가 PXE에서 시작되도록 지정합니다.<br />-   **HD** - 작업 순서가 하드 디스크에서 시작되도록 지정합니다(사전 준비된 미디어에만 해당).|  
|_SMSTSLogPath|로그 디렉터리의 전체 경로를 저장합니다. 이를 사용하여 동작이 기록된 위치를 확인할 수 있습니다. 하드 드라이브를 사용할 수 없는 경우에는 이 값이 설정되지 않습니다.|  
|_SMSTSMachineName|컴퓨터 이름을 저장하고 지정합니다. 작업 순서에서 모든 상태 메시지를 기록하는데 사용할 컴퓨터의 이름을 저장합니다. 새 운영 체제에서 컴퓨터 이름을 변경하려면 **OSDComputerName** 변수를 사용합니다.<br /><br /> 예:<br /><br /> **ABC**|  
|_SMSTSMDataPath|SMSTSLocalDataDrive 변수에 의해 정의된 경로를 지정합니다. 작업 순서가 시작되기 전에 컬렉션 변수를 설정하는 등의 방법으로 SMSTSLocalDataDrive를 정의한 경우 Configuration Manager에서 작업 순서가 시작된 후 _SMSTSMDataPath 변수를 정의합니다.|  
|_SMSTSMediaType|설치를 초기화하는 데 사용되는 미디어 유형을 지정합니다. 미디어 유형의 예에는 부팅 미디어, 완전한 미디어, PXE, 사전 준비된 미디어 등이 있습니다.|  
|_SMSTSMP|Configuration Manager 관리 지점의 URL 또는 IP 주소를 저장합니다.|  
|_SMSTSMPPort|Configuration Manager 관리 지점의 관리 지점 포트 번호를 저장합니다.<br /><br /> 예제:<br /><br /> **80**|  
|_SMSTSOrgName|작업 순서 진행률 사용자 인터페이스 대화 상자에 표시된 브랜딩 제목 이름을 저장합니다.<br /><br /> 예:<br /><br /> **XYZ 조직**|  
|_SMSTSOSUpgradeActionReturnCode|설정에서 반환된 종료 코드 값을 저장하여 성공 또는 실패를 표시합니다.  이 변수는 작업 순서 단계 운영 체제 업그레이드 작업 순서 단계 중에 설정됩니다. 이 변수는 /Compat Windows 10 설치 프로그램 명령줄 옵션과 함께 사용하면 좋습니다.<br /><br /> 예:<br /><br /> /Compat가 완료되면 실패 또는 성공 종료 코드에 따라 이후 단계에서 조치를 취할 수 있습니다. 성공하면 업그레이드를 시작할 수 있습니다. 또는 업그레이드가 준비되었거나 업그레이드되기 전 조치가 필요한 컴퓨터 컬렉션을 만드는 데 사용할 수 있는 환경에 표식을 설정(예: 파일 추가 또는 레지스트리 키 설정)할 수 있습니다.|  
|_SMSTSPackageID|현재 실행 중인 작업 순서 ID를 저장합니다. 이 ID는 Configuration Manager 소프트웨어 패키지 ID와 동일한 형식을 사용합니다.<br /><br /> 예제:<br /><br /> **HJT00001**|  
|_SMSTSPackageName|현재 실행 중인 작업 시퀀스 이름(작업 순서를 만들 때 Configuration Manager 관리자가 지정)을 저장합니다.<br /><br /> 예제:<br /><br /> **Windows 10 작업 순서 배포**|  
|_SMSTSSetupRollback|운영 체제 설치에서 롤백 작업을 수행할지 여부를 지정합니다. 변수 값은 **true** 또는 **false**일 수 있습니다.|  
|_SMSTSRunFromDP|현재 작업 순서가 배포 지점에서 실행 모드로 실행 중인 경우 **true** 로 설정합니다. 이 경우 작업 순서 관리자가 배포 지점에서 필요한 패키지 공유를 가져옵니다.|  
|_SMSTSSiteCode|Configuration Manager 사이트의 사이트 코드를 저장합니다.<br /><br /> 예제:<br /><br /> **ABC**|  
|_SMSTSType|현재 실행 중인 작업 순서의 유형을 지정합니다. 다음 값을 가질 수 있습니다.<br /><br /> **1** - 일반 작업 순서를 나타냅니다.<br /><br /> **2** - 운영 체제 배포 작업 순서를 나타냅니다.|  
|_SMSTSTimezone|_SMSTSTimezone 변수는 다음 형식(공백 없음)으로 표준 시간대 정보를 저장합니다.<br /><br /> 바이어스, StandardBias, daylightbias-, StandardDate.wYear, wMonth, wDayOfWeek, wDay, wHour, wMinute, wSecond, wMilliseconds, DaylightDate.wYear, wMonth, wDayOfWeek, wDay, wHour, wMinute, wSecond, wMilliseconds, StandardName, DaylightName<br /><br /> 예:<br /><br /> 동부 표준시 미국 및 캐나다의 경우 이 값은 **300,0,-60,0,11,0,1,2,0,0,0,0,3,0,2,2,0,0,0,Eastern Standard Time,Eastern Daylight Time**입니다.|  
|_SMSTSUseCRL|작업 순서에서 SSL(Secure Socket Layer) 인증서를 사용하여 관리 지점과 통신할 때 인증서 해지 목록을 사용하는지 여부를 지정합니다.|  
|_SMSTSUserStarted|작업 순서가 사용자에 의해 시작되는지 여부를 지정합니다. 이 변수는 작업 순서가 소프트웨어 센터에서 시작되는 경우에만 설정됩니다. 예를 들어 **_SMSTSLaunchMode** 가 **SMS**로 설정된 경우가 여기에 해당합니다. 이 변수는 다음 값을 가질 수 있습니다.<br /><br /> -   **true** - 작업 순서가 소프트웨어 센터에서 사용자에 의해 수동으로 시작되도록 지정합니다.<br />-   **false** - 작업 순서가 Configuration Manager 스케줄러에 의해 자동으로 시작되도록 지정합니다.|  
|_SMSTSUseSSL|작업 순서에서 SSL을 사용하여 Configuration Manager 관리 지점과 통신하는지 여부를 지정합니다. 사이트가 기본 모드로 실행되는 경우 이 값은 **true**로 설정됩니다.|  
|_SMSTSWTG|컴퓨터가 Windows To Go 장치로 실행되는지 여부를 지정합니다.|  
|OSDPreserveDriveLetter|Configuration Manager 버전 1606부터 이 작업 순서 변수가 사용되지 않습니다. 기본적으로 운영 체제 배포 시 Windows 설치 프로그램이 사용하기에 가장 적합한 드라이브 문자(일반적으로 C:)를 결정합니다. <br /><br />이전 버전에서는 OSDPreverveDriveLetter 변수가 작업 순서에서 운영 체제 이미지를 대상 컴퓨터에 적용할 때 해당 이미지에서 캡처된 드라이브 문자를 사용할지를 결정합니다. 이 변수 값을 **False** 로 설정하여 **운영 체제 적용** 작업 순서 단계의 **대상** 설정에 지정한 위치를 사용할 수 있습니다. 자세한 내용은 [운영 체제 이미지 적용](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage)을 참조하세요.|  
|OSDSetupAdditionalUpgradeOptions|Configuration Manager 버전 1602부터 이 변수를 사용하여 Windows 설치 프로그램 업그레이드의 추가 옵션을 지정할 수 있습니다.
|SMSTSAssignmentsDownloadInterval|이 변수를 사용하여 정책이 반환되지 않은 마지막 시도 이후 정책을 다운로드하기 위해 클라이언트가 대기하는 시간(초)을 지정합니다. 기본적으로는 클라이언트는 **0** 초를 대기한 후 다시 시도합니다.<br /><br /> 미디어 또는 PXE에서 시작 전 명령을 사용하여 이 변수를 설정할 수 있습니다.|  
|SMSTSAssignmentsDownloadRetry|이 변수를 사용하여 첫 번째 시도에서 정책을 찾지 못한 이후 클라이언트가 정책 다운로드를 시도하는 횟수를 지정합니다. 기본적으로 클라이언트는 **0** 번 다시 시도합니다.<br /><br /> 미디어 또는 PXE에서 시작 전 명령을 사용하여 이 변수를 설정할 수 있습니다.|  
|SMSTSAssignUsersMode|작업 순서에서 사용자를 대상 컴퓨터와 연결하는 방법을 지정합니다. 이 변수를 다음 값 중 하나로 설정합니다.<br /><br /> -   자동: 작업 순서에서 운영 체제를 대상 컴퓨터에 배포할 때 지정된 사용자와 대상 컴퓨터 사이의 관계를 만듭니다.<br />-   보류 중: 작업 순서에서 지정된 사용자와 대상 컴퓨터 간의 관계를 만들지만 관계를 설정하기 전에 관리자의 승인을 기다립니다.<br />-   사용 안 함: 작업 순서에서 운영 체제를 배포할 때 사용자를 대상 컴퓨터와 연결하지 않습니다.|  
|SMSTSDownloadAbortCode|이 변수에는 외부 프로그램 다운로더의 중단 코드 값(SMSTSDownloadProgram 변수에 지정됨)이 포함되어 있습니다. 프로그램이 SMSTSDownloadAbortCode 변수 값과 같은 오류 코드를 반환하면 콘텐츠 다운로드에 실패하고 다른 다운로드 방법이 시도되지 않습니다.
|SMSTSDownloadProgram|이 변수를 사용하면 대체 콘텐츠 공급자(작업 순서를 위한 콘텐츠를 다운로드하는 데 기본 Configuration Manager 다운로더 대신에 사용하는 다운로더 프로그램)를 지정할 수 있습니다. 콘텐츠 다운로드 프로세스의 일부로, 작업 순서는 지정한 다운로더 프로그램에 대한 변수를 확인합니다. 지정된 경우 작업 순서는 해당 프로그램을 실행하여 다운로드를 수행합니다.|  
|SMSTSDownloadRetryCount|이 변수를 사용하면 Configuration Manager가 배포 지점의 콘텐츠를 다운로드하기 위해 시도할 횟수를 지정할 수 있습니다. 기본적으로 클라이언트는 **2** 번 다시 시도합니다.|  
|SMSTSDownloadRetryDelay|이 변수를 사용하면 Configuration Manager가 배포 지점의 콘텐츠를 다시 다운로드하기 전까지 대기하는 시간(초)을 지정할 수 있습니다. 기본적으로는 클라이언트는 **15** 초를 대기한 후 다시 시도합니다.|  
|SMSTSErrorDialogTimeout|작업 순서에서 오류가 발생한 경우 이 변수에 지정된 시간(초)이 지나면 자동으로 해제되는 대화 상자가 표시됩니다. 기본적으로는 대화 상자는 **900** 초(15 분) 후에 자동으로 해제됩니다.|  
|TSErrorOnWarning|이 변수를 사용하여 작업 순서 엔진에서 응용 프로그램 설치 작업 순서 단계 중에 검색된 경고를 오류로 간주하는지 여부를 지정합니다. 요구 사항이 충족되지 않아 하나 이상의 응용 프로그램 또는 필수 종속성이 설치되지 않은 경우에는 작업 순서에서 _TSAppInstallStatus 변수를 **Warning** 으로 설정합니다. TSErrorOnWarning 변수를 **True** 로 설정하면 _TSAppInstallStatus 변수가 Warning으로 설정되고 오류로 처리됩니다. **False** 값이 기본 동작입니다.|  
|SMSTSLanguageFolder|이 변수를 사용하여 언어 중립 부팅 이미지의 언어 표시를 변경할 수 있습니다.|  
|SMSTSLocalDataDrive|작업 순서가 실행되는 동안 임시 파일이 대상 컴퓨터에 저장되는 위치를 지정합니다.<br /><br /> 작업 순서를 시작하기 전에 컬렉션 변수를 설정하는 등의 방법으로 이 변수를 설정해야 합니다. 작업 순서가 시작되면 Configuration Manager에서 _SMSTSMDataPath 변수를 정의합니다.|  
|SMSTSMP|이 변수를 사용하여 Configuration Manager 관리 지점의 URL 또는 IP 주소를 지정합니다.|  
|SMSTSMPListRequestTimeout|이 변수를 사용하여, 위치 서비스에서 관리 지점 목록을 검색하지 못한 후 응용 프로그램 또는 소프트웨어 업데이트 설치를 다시 시도하기 전까지 작업 순서가 대기하는 시간(밀리초)을 지정합니다. 기본적으로 작업 순서는 60,000밀리초(60초)를 대기한 후 단계를 다시 시도하며, 최대 다시 시도 횟수는 3회입니다. 이 변수는 응용 프로그램 설치 및 소프트웨어 업데이트 설치 작업 순서 단계에만 적용됩니다.|  
|SMSTSMPListRequestTimeoutEnabled|클라이언트가 인트라넷에 없는 경우 이 변수를 사용하여 반복된 MPList 요청으로 클라이언트를 새로 고치도록 설정할 수 있습니다. <br />기본적으로 이 변수는 True로 설정됩니다. 클라이언트가 인터넷에 있는 경우에는 불필요한 지연이 발생하지 않도록 이 변수를 False로 설정할 수 있습니다. 이 변수는 응용 프로그램 설치 및 소프트웨어 업데이트 설치 작업 순서 단계에만 적용됩니다.|  
|SMSTSPeerDownload|이 변수를 사용하여 클라이언트가 Windows PE 피어 캐시를 사용할 수 있도록 합니다.<br /><br /> 예:<br /><br /> SMSTSPeerDownload  = **TRUE** 로 설정하면 이 기능을 사용할 수 있습니다.|  
|SMSTSPeerRequestPort|Windows PE 피어 캐시에 대한 이 변수를 사용하여 클라이언트 설정에서 구성된 기본 포트(8004)를 사용하지 않을 때 초기 브로드캐스트에 사용할 사용자 지정 네트워크 포트를 지정합니다.|  
|SMSTSPersistContent|이 변수를 사용하여 작업 순서 캐시에 콘텐츠를 일시적으로 유지할 수 있습니다.|  
|SMSTSPostAction|작업 순서를 완료한 후 실행되는 명령을 지정합니다. 예를 들어 이 변수를 사용하면 작업 순서에서 장치에 운영 체제를 배포한 후 포함된 장치에서 쓰기 필터를 사용할 수 있는 스크립트를 지정할 수 있습니다.|  
|SMSTSPreferredAdvertID|대상 컴퓨터에 지정된 특정 배포를 강제로 실행합니다. 미디어 또는 PXE에서 시작 전 명령을 통해 이를 설정할 수 있습니다. 이 변수를 설정한 경우에는 작업 순서가 모든 필수 배포를 재정의합니다.|  
|SMSTSPreserveContent|이 변수는 배포 후 Configuration Manager 클라이언트 캐시에 보존할 작업 순서의 콘텐츠에 플래그를 지정합니다. 이 변수를 사용하는 것은 SMSTSPersistContent를 사용하는 것과는 다릅니다. SMSTSPersisContent는 작업 시퀀스 기간 동안만 콘텐츠를 보존하며 Configuration Manager 클라이언트 캐시가 아닌 작업 순서 캐시를 사용합니다.<br /><br /> 예제:<br /><br /> SMSTSPreserveContent = **TRUE** 로 설정하면 이 기능을 사용할 수 있습니다.|  
|SMSTSRebootDelay|컴퓨터를 다시 시작하기 전에 대기할 시간(초)을 지정합니다. 이 변수를 0으로 설정하지 않은 경우에는 다시 부팅하기 전에 작업 순서 관리자에 알림 대화 상자가 표시됩니다.<br /><br /> 예:<br /><br /> **0**<br /><br /> **30**|  
|SMSTSRebootMessage|다시 시작이 요청된 경우 종료 대화 상자에 표시할 메시지를 지정합니다. 이 변수를 설정하지 않으면 기본 메시지가 표시됩니다.<br /><br /> 예:<br /><br /> **작업 순서 관리자가 이 컴퓨터를 다시 시작하는 중입니다**.|  
|SMSTSRebootRequested|현재 작업 순서 단계를 완료한 후 다시 시작이 요청됨을 나타냅니다. 다시 시작이 필요한 경우 이 변수를 **true**로 설정하기만 하면 이 작업 순서 단계 후 작업 시퀀스 관리자가 다시 시작됩니다. 작업 순서 단계를 완료하기 위해 다시 시작해야 하는 경우 작업 순서 단계에서 이 작업 순서 변수를 설정해야 합니다. 컴퓨터가 다시 시작되면 다음 작업 순서 단계에서 작업 순서가 계속 실행됩니다.|  
|SMSTSRetryRequested|현재 작업 순서 단계를 완료한 후 다시 시도를 요청합니다. 이 작업 순서 변수를 설정한 경우에는 **SMSTSRebootRequested** 도 **true**로 설정해야 합니다. 컴퓨터가 다시 시작되면 작업 순서 관리자가 동일한 작업 순서 단계를 다시 실행합니다.|  
|SMSTSSoftwareUpdateScanTimeout| [소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates) 작업 순서 단계를 진행하는 동안 소프트웨어 업데이트 검사 시간 제한을 조정할 수 있습니다. 예를 들어 소프트웨어 업데이트 설치가 많은 경우 기본값을 늘릴 수 있습니다. 기본값은 30분입니다. |
|SMSTSUDAUsers|대상 컴퓨터의 기본 사용자를 지정합니다. 다음 형식을 사용하여 사용자를 지정합니다. 여러 사용자를 구분하려면 쉼표(,)를 사용합니다.<br /><br /> 예:<br /><br /> **domain\user1, domain\user2, domain\user3**<br /><br /> 사용자를 대상 컴퓨터와 연결하는 방법에 대한 자세한 내용은 [사용자를 대상 컴퓨터에 연결](../get-started/associate-users-with-a-destination-computer.md)을 참조하세요.|  
|SMSTSWaitForSecondReboot|Configuration Manager 버전 1602부터, 소프트웨어 업데이트 설치에서 두 번의 다시 시작을 요구하는 경우 이 선택적 작업 순서 변수를 사용하여 클라이언트 동작을 제어할 수 있습니다. 소프트웨어 업데이트가 설치되어 다시 시작되는 동작으로 인해 작업 순서에서 오류가 발생하는 것을 방지하려면 이 변수를 [소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates) 단계 전에 설정해야 합니다.<br /><br /> SMSTSWaitForSecondReboot 값을 초 단위로 설정하여 두 번째로 다시 시작해야 할 때 컴퓨터 다시 시작에서 충분한 시간을 허용하는 경우 소프트웨어 업데이트 설치 단계 중 작업 순서가 일시 중지되는 기간을 지정할 수 있습니다. <br />예를 들어 SMSTSWaitForSecondReboot를 600으로 설정하면 다시 시작된 후 추가 작업 순서 단계가 실행되기 전에 작업 순서가 10분간 일시 중지됩니다. 이 변수는 단일 소프트웨어 업데이트 설치 작업 순서 단계에서 수백 개의 소프트웨어 업데이트가 설치되는 경우에 유용합니다.|  

