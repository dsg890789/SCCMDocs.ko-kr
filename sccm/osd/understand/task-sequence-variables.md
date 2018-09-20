---
title: 작업 순서 변수 참조
titleSuffix: Configuration Manager
description: Configuration Manager 작업 순서를 제어 및 사용자 지정하는 변수에 대해 알아봅니다.
ms.date: 08/17/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 62f15230-d3a6-4afc-abd4-1e07e7ba6c97
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cfecd7441abd206bdff1d2f6618d763a30dddc51
ms.sourcegitcommit: be8c0182db9ef55a948269fcbad7c0f34fd871eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42756265"
---
# <a name="task-sequence-variables-in-configuration-manager"></a>Configuration Manager의 작업 순서 변수

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서는 사전순의 사용 가능한 모든 변수에 대한 참조입니다. 브라우저의 **찾기** 기능(일반적으로 **CTRL** + **F**)을 사용하면 특정 변수를 찾을 수 있습니다. 이렇게 찾은 변수는 특정 단계와 관련이 있는지를 알려줍니다. [작업 순서 단계](/sccm/osd/understand/task-sequence-steps)에 대한 문서에는 각 단계에 사용되는 변수 목록이 포함되어 있습니다. 

자세한 내용은 [Using task sequence variables](/sccm/osd/understand/using-task-sequence-variables)\(작업 순서 변수 사용\)를 참조하세요.



## <a name="bkmk_tsvar"></a> 작업 순서 변수 참조


### <a name="OSDDetectedWinDir"></a> _OSDDetectedWinDir

 Windows PE가 시작될 때 작업 순서가 컴퓨터의 하드 드라이브에서 이전 운영 체제 설치를 검색합니다. Windows 폴더 위치가 이 변수에 저장됩니다. 환경에서 이 값을 검색하도록 작업 순서를 구성하고 이를 사용하여 새 운영 체제 설치에 사용할 동일한 Windows 폴더 위치를 지정할 수 있습니다.


### <a name="OSDDetectedWinDrive"></a> _OSDDetectedWinDrive

 Windows PE가 시작될 때 작업 순서가 컴퓨터의 하드 드라이브에서 이전 운영 체제 설치를 검색합니다. 운영 체제가 설치되어 있는 하드 드라이브 위치가 이 변수에 저장됩니다. 환경에서 이 값을 검색하도록 작업 순서를 구성하고 이를 사용하여 새 운영 체제에 사용할 동일한 하드 드라이브 위치를 지정할 수 있습니다.


### <a name="OSDMigrateUsmtPackageID"></a> _OSDMigrateUsmtPackageID

 ‘[사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState) 단계에 적용됩니다.’

 (입력)

 USMT 파일을 포함할 Configuration Manager 패키지의 패키지 ID를 지정합니다. 이 변수가 필요합니다.


### <a name="OSDMigrateUsmtRestorePackageID"></a> _OSDMigrateUsmtRestorePackageID

 ‘[사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState) 단계에 적용됩니다.’

 (입력)

 USMT 파일을 포함할 Configuration Manager 패키지의 패키지 ID를 지정합니다. 이 변수가 필요합니다.


### <a name="SMSTSAdvertID"></a> _SMSTSAdvertID

 현재 실행 중인 작업 순서 배포의 고유 ID를 저장합니다. Configuration Manager 소프트웨어 배포의 배포 ID와 동일한 형식을 사용합니다. 독립 실행형 미디어에서 작업 순서를 실행 중인 경우에는 이 변수가 정의되지 않습니다.

 #### <a name="example"></a>예
 `ABC20001`


### <a name="SMSTSAssetTag"></a> _SMSTSAssetTag

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터에 대한 자산 태그를 지정합니다.


### <a name="SMSTSBootImageID"></a> _SMSTSBootImageID

 현재 실행 중인 작업 순서가 부팅 이미지 패키지를 참조하는 경우 이 변수가 부팅 이미지 패키지 ID를 저장합니다. 작업 순서가 부팅 이미지 패키지를 참조하지 않는 경우에는 이 변수가 설정되지 않습니다.

 #### <a name="example"></a>예
 `ABC00001`  


### <a name="SMSTSBootUEFI"></a> _SMSTSBootUEFI

 작업 순서에서는 UEFI 모드의 컴퓨터를 발견하는 경우 이 변수를 설정합니다.


### <a name="SMSTSClientGUID"></a> _SMSTSClientGUID

 Configuration Manager 클라이언트 GUID의 값을 저장합니다. 작업 순서가 독립 실행형 미디어에서 실행 중이라면 이 변수가 설정되지 않습니다.

 #### <a name="example"></a>예
 `0a1a9a4b-fc56-44f6-b7cd-c3f8ee37c04c`


### <a name="SMSTSCurrentActionName"></a> _SMSTSCurrentActionName

 현재 실행 중인 작업 순서 단계의 이름을 지정합니다. 이 변수는 작업 순서 관리자가 각 개별 단계를 실행하기 전에 설정됩니다.

 #### <a name="example"></a>예
 `run command line`


### <a name="SMSTSDefaultGateways"></a> _SMSTSDefaultGateways

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터에 사용되는 기본 게이트웨이를 지정합니다.


### <a name="SMSTSDownloadOnDemand"></a> _SMSTSDownloadOnDemand

 현재 작업 순서가 요청 시 다운로드 모드로 실행 중인 경우 이 변수는 `true`입니다. 요청 시 다운로드 모드에서는 작업 순서 관리자가 콘텐츠에 액세스해야 하는 경우에만 콘텐츠를 로컬로 다운로드합니다.


### <a name="SMSTSInWinPE"></a> _SMSTSInWinPE

 현재 작업 순서 단계가 Windows PE에서 실행 중인 경우 이 변수는 `true`입니다. 이 작업 순서 변수를 테스트하여 현재 OS 환경을 확인할 수 있습니다.


### <a name="SMSTSIPAddresses"></a> _SMSTSIPAddresses

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터에 사용되는 IP 주소를 지정합니다.


### <a name="SMSTSLastActionRetCode"></a> _SMSTSLastActionRetCode

 마지막으로 실행된 동작에서 반환 코드를 저장합니다. 이 변수를 다음 단계 실행 여부를 결정하는 조건으로 사용할 수 있습니다.

 #### <a name="example"></a>예
 `0`


### <a name="SMSTSLastActionSucceeded"></a> _SMSTSLastActionSucceeded

 - 마지막 단계가 성공한 경우 이 변수는 `true`입니다.  

 - 마지막 단계가 실패한 경우에는 `false`입니다.  

 - 이 단계가 비활성화되거나 연결된 조건이 **false**로 평가되어 작업 순서에서 마지막 작업을 건너뛴 경우 이 변수가 다시 설정되지 않습니다. 이전 작업에 대한 값을 계속 유지합니다.  

 
### <a name="SMSTSLaunchMode"></a> _SMSTSLaunchMode

 작업 순서가 다음 방법 중 하나를 통해 시작되었음을 지정합니다.  

 - **SMS**: 구성 관리자 클라이언트(예: 소프트웨어 센터에서 시작하는 경우)
 - **UFD**: 레거시 USB 미디어
 - **UFD + FORMAT**: 최신 USB 미디어
 - **CD**: 부팅 가능 CD
 - **DVD**: 부팅 가능 DVD
 - **PXE**: PXE 네트워크 부팅
 - **HD**: 하드 디스크의 미리 준비된 미디어


### <a name="SMSTSLogPath"></a> _SMSTSLogPath

 로그 디렉터리의 전체 경로를 저장합니다. 이 값을 사용하여 작업 순서 단계에서 해당 작업을 로깅하는 위치를 결정합니다. 하드 드라이브를 사용할 수 없는 경우에는 이 값이 설정되지 않습니다.


### <a name="SMSTSMacAddresses"></a> _SMSTSMacAddresses

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터에 사용되는 MAC 주소를 지정합니다.


### <a name="SMSTSMachineName"></a> _SMSTSMachineName

 컴퓨터 이름을 저장하고 지정합니다. 작업 순서에서 모든 상태 메시지를 기록하는 데 사용할 컴퓨터의 이름을 저장합니다. 새 OS에서 컴퓨터 이름을 변경하려면 [OSDComputerName](#OSDComputerName) 변수를 사용합니다.


### <a name="SMSTSMake"></a> _SMSTSMake

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터의 제조업체를 지정합니다.


### <a name="SMSTSMDataPath"></a> _SMSTSMDataPath

 [SMSTSLocalDataDrive](#SMSTSLocalDataDrive) 변수에 의해 정의된 경로를 지정합니다. 작업 순서가 시작되기 전에 컬렉션 변수를 설정하는 등의 방법으로 SMSTSLocalDataDrive를 정의한 경우 Configuration Manager에서 작업 순서가 시작된 후 _SMSTSMDataPath 변수를 정의합니다.


### <a name="SMSTSMediaType"></a> _SMSTSMediaType

 설치를 초기화하는 데 사용되는 미디어 유형을 지정합니다. 미디어 유형의 예에는 부팅 미디어, 완전한 미디어, PXE, 사전 준비된 미디어 등이 있습니다.


### <a name="SMSTSModel"></a> _SMSTSModel

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터의 모델을 지정합니다.


### <a name="SMSTSMP"></a> _SMSTSMP

 Configuration Manager 관리 지점의 URL 또는 IP 주소를 저장합니다.


### <a name="SMSTSMPPort"></a> _SMSTSMPPort

 Configuration Manager 관리 지점의 포트 번호를 저장합니다.


### <a name="SMSTSOrgName"></a> _SMSTSOrgName

 작업 순서 진행률 대화 상자에 표시되는 브랜딩 제목 이름을 저장합니다.


### <a name="SMSTSOSUpgradeActionReturnCode"></a> _SMSTSOSUpgradeActionReturnCode

 ‘[운영 체제 업그레이드](task-sequence-steps.md#BKMK_UpgradeOS) 단계에 적용됩니다.’

 Windows 설치 프로그램에서 성공 또는 실패를 나타내기 위해 반환하는 종료 코드 값을 저장합니다. 이 변수는 `/Compat` 명령줄 옵션과 함께 사용하면 좋습니다.

 #### <a name="example"></a>예
 compat 전용 검사가 완료되면 실패 또는 성공 종료 코드에 따라 이후 단계에서 조치를 취하세요. 성공하면 업그레이드를 시작하세요. 또는 하드웨어 인벤토리를 사용하여 수집할 환경에 마커를 설정합니다. 예를 들어 파일을 추가하거나 레지스트리 키를 설정합니다. 이 마커를 사용하여 업그레이드할 준비가 되었거나 업그레이드하기 전에 조치가 필요한 컴퓨터의 컬렉션을 만듭니다.


### <a name="SMSTSPackageID"></a> _SMSTSPackageID

 현재 실행 중인 작업 순서 ID를 저장합니다. 이 ID는 Configuration Manager 패키지 ID와 동일한 형식을 사용합니다. 

 #### <a name="example"></a>예
 `HJT00001`


### <a name="SMSTSPackageName"></a> _SMSTSPackageName

 현재 실행 중인 작업 순서 이름을 저장합니다. 작업 순서를 작성할 때 Configuration Manager 관리자가 이 이름을 지정합니다.

 #### <a name="example"></a>예
 `Deploy Windows 10 task sequence`


### <a name="SMSTSRunFromDP"></a> _SMSTSRunFromDP

 현재 작업 순서가 배포 지점에서 실행 모드로 실행 중인 경우 `true`로 설정하세요. 이 모드는 작업 순서 관리자가 배포 지점으로부터 필요한 패키지 공유를 가져옴을 의미 합니다.


### <a name="SMSTSSerialNumber"></a> _SMSTSSerialNumber

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터의 일련 번호를 지정합니다.


### <a name="SMSTSSetupRollback"></a> _SMSTSSetupRollback

 현재 위치 업그레이드 중에 Windows 설치 프로그램에서 롤백 작업을 수행했는지 여부를 지정합니다. 변수 값은 `true` 또는 `false`일 수 있습니다.


### <a name="SMSTSSiteCode"></a> _SMSTSSiteCode

 Configuration Manager 사이트의 사이트 코드를 저장합니다.

 #### <a name="example"></a>예
 `ABC`


### <a name="SMSTSTimezone"></a> _SMSTSTimezone

 이 변수는 표준 시간대 정보를 다음 형식으로 저장합니다. 

 ```
 Bias,StandardBias,DaylightBias,StandardDate.wYear,wMonth,wDayOfWeek,wDay,wHour,wMinute,wSecond,wMilliseconds,DaylightDate.wYear,wMonth,wDayOfWeek,wDay,wHour,wMinute,wSecond,wMilliseconds,StandardName,DaylightName
 ```

 #### <a name="example"></a>예
 **동부 표준시(미국과 캐나다)** 표준 시간대의 경우: 

 ```
 300,0,-60,0,11,0,1,2,0,0,0,0,3,0,2,2,0,0,0,Eastern Standard Time,Eastern Daylight Time
 ```


### <a name="SMSTSType"></a> _SMSTSType

 현재 실행 중인 작업 순서의 유형을 지정합니다. 다음 값 중 하나일 수 있습니다.  

 - **1**: 일반 작업 순서
 - **2**: OS 배포 작업 순서


### <a name="SMSTSUseCRL"></a> _SMSTSUseCRL

 작업 순서에서 HTTPS를 사용하여 관리 지점과 통신할 때 이 변수는 CRL(인증서 해지 목록)을 사용하는지 여부를 지정합니다.


### <a name="SMSTSUserStarted"></a> _SMSTSUserStarted

 사용자가 작업 순서를 시작했는지 여부를 지정합니다. 이 변수는 작업 순서가 소프트웨어 센터에서 시작되는 경우에만 설정됩니다. 예를 들어 [_SMSTSLaunchMode](#SMSTSLaunchMode)가 `SMS`로 설정된 경우가 여기에 해당합니다. 

 이 변수는 다음 값을 가질 수 있습니다.  

 - `true`: 작업 순서가 소프트웨어 센터에서 사용자에 의해 수동으로 시작되도록 지정합니다.  

 - `false`: 작업 순서가 Configuration Manager 스케줄러에 의해 자동으로 시작되도록 지정합니다.


### <a name="SMSTSUseSSL"></a> _SMSTSUseSSL

 작업 순서에서 SSL을 사용하여 Configuration Manager 관리 지점과 통신하는지 여부를 지정합니다. HTTPS에 대한 사이트 시스템을 구성하는 경우 값은 `true`로 설정됩니다.


### <a name="SMSTSUUID"></a> _SMSTSUUID

 ‘[동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables) 단계에 적용됩니다.’

 컴퓨터의 UUID를 지정합니다.


### <a name="SMSTSWTG"></a> _SMSTSWTG

 컴퓨터가 Windows To Go 장치로 실행되는지 여부를 지정합니다.


### <a name="TSAppInstallStatus"></a> _TSAppInstallStatus

 [응용 프로그램 설치](task-sequence-steps.md#BKMK_InstallApplication) 단계 중에 작업 순서가 응용 프로그램의 설치 상태를 사용하여 이 변수를 설정하며, 다음 값 중 하나를 설정합니다.  

 - **정의되지 않음**: 응용 프로그램 설치 단계가 실행되지 않았습니다.  

 - **오류**: 응용 프로그램 설치 단계 중에 응용 프로그램 하나 이상이 오류 때문에 실패했습니다.  

 - **경고**: 응용 프로그램 설치 단계 중에 오류가 발생하지 않았습니다. 요구 사항이 충족되지 않아 하나 이상의 응용 프로그램 또는 필요한 종속성이 설치되지 않았습니다.  

 - **성공**: 응용 프로그램 설치 단계 중에 감지된 오류 또는 경고가 없습니다.  


### <a name="OSDAdapter"></a> OSDAdapter

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 이 작업 순서 변수는 *배열* 변수입니다. 배열의 각 요소는 컴퓨터에서 단일 네트워크 어댑터에 대한 설정을 나타냅니다. 각 어댑터에 대한 설정은 배열 변수 이름과 0부터 시작하는 네트워크 어댑터 인덱스 및 속성 이름을 결합하여 액세스할 수 있습니다.

 네트워크 설정 적용 단계에서 여러 네트워크 어댑터를 구성할 경우 변수 이름에 인덱스 **1**을 사용하여 ‘두 번째’ 네트워크 어댑터의 속성을 정의합니다. 예를 들어 OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList 및 OSDAdapter1DNSDomain이 있습니다.

 다음 변수 이름을 사용하여 단계가 구성할 ‘첫 번째’ 네트워크 어댑터의 속성을 정의할 수 있습니다.

#### <a name="osdadapter0enabledhcp"></a>OSDAdapter0EnableDHCP
 이 설정은 필수입니다. 가능한 값은 `True` 또는 `False`입니다. 예:

 `true`: 어댑터에 대해 DHCP(Dynamic Host Configuration Protocol)를 사용합니다.

#### <a name="osdadapter0ipaddresslist"></a>OSDAdapter0IPAddressList
 어댑터에 대한 쉼표로 구분된 IP 주소 목록입니다. **EnableDHCP**가 `false`로 설정되지 않으면 이 속성은 무시됩니다. 이 설정은 필수입니다.

#### <a name="osdadapter0subnetmask"></a>OSDAdapter0SubnetMask
 쉼표로 구분된 서브넷 마스크 목록입니다. **EnableDHCP**가 `false`로 설정되지 않으면 이 속성은 무시됩니다. 이 설정은 필수입니다.

#### <a name="osdadapter0gateways"></a>OSDAdapter0Gateways
 쉼표로 구분된 IP 게이트웨이 주소 목록입니다. **EnableDHCP**가 `false`로 설정되지 않으면 이 속성은 무시됩니다. 이 설정은 필수입니다.

#### <a name="osdadapter0dnsdomain"></a>OSDAdapter0DNSDomain
 어댑터에 대한 DNS(Domain Name System) 도메인입니다.

#### <a name="osdadapter0dnsserverlist"></a>OSDAdapter0DNSServerList
 쉼표로 구분된 어댑터에 대한 DNS 서버 목록입니다. 이 설정은 필수입니다.

#### <a name="osdadapter0enablednsregistration"></a>OSDAdapter0EnableDNSRegistration
 DNS에 어댑터에 대한 IP 주소를 등록하려면 `true`로 설정합니다.

#### <a name="osdadapter0enablefulldnsregistration"></a>OSDAdapter0EnableFullDNSRegistration
 DNS에 컴퓨터의 전체 DNS 이름 아래 어댑터에 대한 IP 주소를 등록하려면 `true`로 설정합니다.

#### <a name="osdadapter0enableipprotocolfiltering"></a>OSDAdapter0EnableIPProtocolFiltering
 어댑터에서 IP 프로토콜 필터링을 사용하려면 `true`로 설정합니다.

#### <a name="osdadapter0ipprotocolfilterlist"></a>OSDAdapter0IPProtocolFilterList
 IP를 통해 실행할 수 있는 쉼표로 구분된 프로토콜 목록입니다. **EnableIPProtocolFiltering**이 `false`로 설정된 경우 이 속성은 무시됩니다.

#### <a name="osdadapter0enabletcpfiltering"></a>OSDAdapter0EnableTCPFiltering
 어댑터에 대해 TCP 포트 필터링을 사용하려면 `true`로 설정합니다.

#### <a name="osdadapter0tcpfilterportlist"></a>OSDAdapter0TCPFilterPortList
 TCP에 대해 액세스 권한을 부여할 쉼표로 구분된 포트 목록입니다. **EnableTCPFiltering**이 `false`로 설정된 경우 이 속성은 무시됩니다.

#### <a name="osdadapter0tcpipnetbiosoptions"></a>OSDAdapter0TcpipNetbiosOptions
 NetBIOS over TCP/IP 옵션입니다. 가능한 값은 다음과 같습니다.  

 - `0`: DHCP 서버에서 NetBIOS 설정을 사용합니다.  
 - `1`: NetBIOS over TCP/IP를 사용하도록 설정합니다.  
 - `2`: NetBIOS over TCP/IP를 사용하지 않도록 설정합니다.  

#### <a name="osdadapter0enablewins"></a>OSDAdapter0EnableWINS
 이름 확인에 WINS를 사용하려면 `true`로 설정합니다.

#### <a name="osdadapter0winsserverlist"></a>OSDAdapter0WINSServerList
 쉼표로 구분된 WINS 서버 IP 주소 목록입니다. **EnableWINS**가 `true`로 설정되지 않으면 이 속성은 무시됩니다.

#### <a name="osdadapter0macaddress"></a>OSDAdapter0MacAddress
 설정을 실제 네트워크 어댑터에 연결하기 위해 사용되는 MAC 주소입니다.

#### <a name="osdadapter0name"></a>OSDAdapter0Name
 네트워크 연결 제어판 프로그램에 표시되는 네트워크 연결의 이름입니다. 이름은 0에서 255자 사이입니다.

#### <a name="osdadapter0index"></a>OSDAdapter0Index
 설정의 배열에서 네트워크 어댑터 설정의 인덱스입니다.

#### <a name="example"></a>예
 - **OSDAdapterCount** = `1`  
 - **OSDAdapter0EnableDHCP** = `FALSE`  
 - **OSDAdapter0IPAddressList** = `192.168.0.40`  
 - **OSDAdapter0SubnetMask** = `255.255.255.0`  
 - **OSDAdapter0Gateways** = `192.168.0.1`  
 - **OSDAdapter0DNSSuffix** = `contoso.com`  


### <a name="OSDAdapterCount"></a> OSDAdapterCount

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터에 설치된 네트워크 어댑터의 수를 지정합니다. **OSDAdapterCount** 값을 설정한 경우 각 어댑터의 모든 구성 옵션도 설정하세요. 

 예를 들어 첫 번째 어댑터에 대해 **OSDAdapter0TCPIPNetbiosOptions** 값을 설정하면 해당 어댑터에 대한 모든 값을 구성해야 합니다.

 이 값을 지정하지 않으면 작업 순서에서 **OSDAdapter** 값을 모두 무시합니다.


### <a name="OSDApplyDriverBootCriticalContentUniqueID"></a> OSDApplyDriverBootCriticalContentUniqueID

 ‘[드라이버 패키지 적용](task-sequence-steps.md#BKMK_ApplyDriverPackage) 단계에 적용됩니다.’

 (입력)

 드라이버 패키지에서 설치할 대용량 저장 장치 드라이버의 콘텐츠 ID를 지정합니다. 이 변수를 지정하지 않으면 대용량 저장소 드라이버가 설치되지 않습니다.


### <a name="OSDApplyDriverBootCriticalHardwareComponent"></a> OSDApplyDriverBootCriticalHardwareComponent

 ‘[드라이버 패키지 적용](task-sequence-steps.md#BKMK_ApplyDriverPackage) 단계에 적용됩니다.’

 (입력)

 대용량 저장 장치 드라이버가 설치되었는지 여부를 지정하며 이 변수는 **scsi**여야 합니다.

 [OSDApplyDriverBootCriticalContentUniqueID](#OSDApplyDriverBootCriticalContentUniqueID)가 설정된 경우 이 변수가 필요합니다.


### <a name="OSDApplyDriverBootCriticalID"></a> OSDApplyDriverBootCriticalID

 ‘[드라이버 패키지 적용](task-sequence-steps.md#BKMK_ApplyDriverPackage) 단계에 적용됩니다.’

 (입력)

 설치할 대용량 저장 장치 드라이버의 부팅 필요 ID를 지정합니다. 이 ID는 장치 드라이버의 txtsetup.oem 파일의 **scsi** 섹션에 나열되어 있습니다.

 [OSDApplyDriverBootCriticalContentUniqueID](#OSDApplyDriverBootCriticalContentUniqueID)가 설정된 경우 이 변수가 필요합니다.

### <a name="OSDApplyDriverBootCriticalINFFile"></a> OSDApplyDriverBootCriticalINFFile

 ‘[드라이버 패키지 적용](task-sequence-steps.md#BKMK_ApplyDriverPackage) 단계에 적용됩니다.’

 (입력)

 설치할 대용량 저장소 드라이버의 INF 파일을 지정합니다.

 [OSDApplyDriverBootCriticalContentUniqueID](#OSDApplyDriverBootCriticalContentUniqueID)가 설정된 경우 이 변수가 필요합니다.


### <a name="OSDAutoApplyDriverBestMatch"></a> OSDAutoApplyDriverBestMatch

 ‘[드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers) 단계에 적용됩니다.’

 (입력)

 하드웨어 장치와 호환되는 드라이버 카탈로그의 여러 장치 드라이버가 있는 경우 이 변수는 해당 단계의 동작을 결정합니다. 

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값): 가장 적합한 장치 드라이버만 설치합니다.  

 - `false`: 이 단계에서 호환되는 모든 장치 드라이버를 설치하고, Windows에서 사용하기 가장 적합한 드라이버를 선택합니다.  


### <a name="OSDAutoApplyDriverCategoryList"></a> OSDAutoApplyDriverCategoryList

 ‘[드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers) 단계에 적용됩니다.’

 (입력)

 쉼표로 구분된 드라이버 카탈로그 범주의 고유한 ID 목록입니다. **드라이버 자동 적용** 단계는 지정된 범주 중 하나 이상의 드라이버만 고려합니다. 이 값은 선택 사항이므로 기본적으로 설정되어 있지 않습니다. 사이트에서 **SMS_CategoryInstance** 개체 목록을 열거하여 사용 가능한 범주 ID를 가져옵니다.


### <a name="OSDBitLockerRecoveryPassword"></a> OSDBitLockerRecoveryPassword

 ‘[BitLocker 사용](task-sequence-steps.md#BKMK_EnableBitLocker) 단계에 적용됩니다.’

 (입력)

 임의 복구 암호를 생성하는 대신 **BitLocker 사용** 단계는 지정된 값을 복구 암호로 사용합니다. 값은 유효한 숫자 BitLocker 복구 암호여야 합니다.


### <a name="OSDBitLockerStartupKey"></a> OSDBitLockerStartupKey

 ‘[BitLocker 사용](task-sequence-steps.md#BKMK_EnableBitLocker) 단계에 적용됩니다.’

 (입력)

 키 관리 옵션인 **USB의 시작 키만**에 대해 임의 시작 키를 생성하는 대신 **BitLocker 사용** 단계는 TPM(신뢰할 수 있는 플랫폼 모듈)을 시작 키로 사용합니다. 값은 유효한 256비트 Base64로 인코딩된 BitLocker 시작 키여야 합니다.


### <a name="OSDCaptureAccount"></a> OSDCaptureAccount

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 네트워크 공유에서 캡처된 이미지를 저장([OSDCaptureDestination](#OSDCaptureDestination))할 권한이 있는 Windows 계정 이름을 지정합니다. [OSDCaptureAccountPassword](#OSDCaptureAccountPassword)도 지정합니다.

 OS 이미지 캡처 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#capture-operating-system-image-account)을 참조하세요.


### <a name="OSDCaptureAccountPassword"></a> OSDCaptureAccountPassword

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 네트워크 공유에서 캡처된 이미지를 저장([OSDCaptureDestination](#OSDCaptureDestination))하는 데 사용되는 Windows 계정([OSDCaptureAccount](#OSDCaptureAccount))에 대한 암호를 지정합니다.


### <a name="OSDCaptureDestination"></a> OSDCaptureDestination

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 작업 순서에서 캡처된 OS 이미지를 저장하는 위치를 지정합니다. 디렉터리 이름은 최대 255자까지 가능합니다. 네트워크 공유에서 인증을 요구하는 경우 [OSDCaptureAccount](#OSDCaptureAccount) 및 [OSDCaptureAccountPassword](#OSDCaptureAccountPassword) 변수를 지정합니다.


### <a name="OSDComputerName-input"></a> OSDComputerName(입력)

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 대상 컴퓨터의 이름을 지정합니다.

 #### <a name="example"></a>예
 `%_SMSTSMachineName%`(기본값)


### <a name="OSDComputerName-output"></a> OSDComputerName(출력)

 ‘[Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings) 단계에 적용됩니다.’

 컴퓨터의 NetBIOS 이름으로 설정합니다. [OSDMigrateComputerName](#OSDMigrateComputerName) 변수가 `true`로 설정된 경우에만 이 값이 설정됩니다.


### <a name="OSDConfigFileName"></a> OSDConfigFileName

 ‘[운영 체제 이미지 적용](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 OS 배포 이미지 패키지와 관련된 OS 배포 응답 파일의 파일 이름을 지정합니다.  


### <a name="OSDDataImageIndex"></a> OSDDataImageIndex

 ‘[데이터 이미지 적용](task-sequence-steps.md#BKMK_ApplyDataImage) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터에 적용되는 이미지의 인덱스 값을 지정합니다.


### <a name="OSDDiskIndex"></a> OSDDiskIndex

 ‘[디스크 포맷 및 파티션 만들기](task-sequence-steps.md#BKMK_FormatandPartitionDisk) 단계에 적용됩니다.’

 (입력)

 분할할 실제 디스크 번호를 지정합니다.


### <a name="OSDDNSDomain"></a> OSDDNSDomain

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터에서 사용하는 기본 DNS 서버를 지정합니다.


### <a name="OSDDNSSuffixSearchOrder"></a> OSDDNSSuffixSearchOrder

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터에 대한 DNS 검색 순서를 지정합니다.


### <a name="OSDDomainName"></a> OSDDomainName

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 가입하는 Active Directory 도메인의 이름을 지정합니다. 지정된 값은 유효한 Active Directory Domain Services 도메인 이름이어야 합니다.


### <a name="OSDDomainOUName"></a> OSDDomainOUName

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 가입하는 OU(조직 구성 단위)의 RFC 1779 형식 이름을 지정합니다. 지정하는 경우 값에 전체 경로가 포함되어야 합니다.

 #### <a name="example"></a>예
 `LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com`


### <a name="OSDDoNotLogCommand"></a> OSDDoNotLogCommand
 <!--1358493--> ‘버전 1806에서 시작합니다.’  
 ‘[명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 단계에 적용됩니다.’

 (입력)

 잠재적으로 중요한 데이터가 표시되거나 기록되지 않도록 하려면 이 변수를 `TRUE`로 설정합니다. 이 변수는 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 작업 순서 단계 중 **smsts.log**에서 프로그램 이름을 마스크합니다.   


### <a name="OSDEnableTCPIPFiltering"></a> OSDEnableTCPIPFiltering

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 TCP/IP 필터링이 사용되는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`(기본값)  


### <a name="OSDGPTBootDisk"></a> OSDGPTBootDisk

 ‘[디스크 포맷 및 파티션 만들기](task-sequence-steps.md#BKMK_FormatandPartitionDisk) 단계에 적용됩니다.’

 (입력)

 GPT 하드 디스크에서 EFI 파티션을 만들지 여부를 지정합니다. EFI 기반 컴퓨터는 이 파티션을 시동 디스크로 사용합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`(기본값)


### <a name="OSDImageCreator"></a> OSDImageCreator

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 이미지를 만든 사용자의 선택적 이름입니다. 이 이름은 WIM 파일에 저장됩니다. 사용자 이름은 최대 255자까지 가능합니다.


### <a name="OSDImageDescription"></a> OSDImageDescription

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 캡처된 OS 이미지에 대한 선택적 사용자 정의 설명입니다. 이 설명은 WIM 파일에 저장됩니다. 설명은 최대 255자까지 가능합니다.


### <a name="OSDImageIndex"></a> OSDImageIndex

 ‘[운영 체제 이미지 적용](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터에 적용된 WIM 파일의 이미지 인덱스 값을 지정합니다.


### <a name="OSDImageVersion"></a> OSDImageVersion

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 (입력)

 캡처된 OS 이미지에 할당할 선택적 사용자 정의 버전 번호입니다. 이 버전 번호는 WIM 파일에 저장됩니다. 이 값은 최대 32자의 알파벳 문자 조합일 수 있습니다.


### <a name="OSDInstallDriversAdditionalOptions"></a> OSDInstallDriversAdditionalOptions
<!--516679/2840016--> ‘버전 1806에서 시작합니다.’  
 ‘[드라이버 패키지 적용](/sccm/osd/understand/task-sequence-steps#BKMK_ApplyDriverPackage) 단계에 적용됩니다.’

 (입력)

 드라이버 패키지를 적용할 때 DISM 명령줄에 추가하는 추가 옵션을 지정합니다. 작업 순서에서는 명령줄 옵션을 확인하지 않습니다. 

 이 변수를 사용하려면 **드라이버 패키지 적용** 단계에서 **재귀 옵션을 사용하여 실행 중인 DISM을 통해 드라이버 패키지 설치** 설정을 활성화합니다. 

 자세한 내용은 [Windows 10 DISM Command-Line Options](https://docs.microsoft.com/windows-hardware/manufacture/desktop/deployment-image-servicing-and-management--dism--command-line-options)(Windows 10 DISM 명령줄 옵션)를 참조하세요.


### <a name="OSDJoinAccount"></a> OSDJoinAccount

 ‘다음 단계에 적용합니다.’  
 - [네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings)   
 - [도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup)  


 (입력)

 도메인에 대상 컴퓨터를 추가하는 데 사용되는 도메인 사용자 계정을 지정합니다. 도메인에 가입하는 경우 이 변수가 필요합니다.

 작업 순서 도메인 가입 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-editor-domain-joining-account)을 참조하세요.


### <a name="OSDJoinDomainName"></a> OSDJoinDomainName

 ‘[도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 가입하는 Active Directory 도메인의 이름을 지정합니다. 도메인 이름의 길이는 1-255자 사이여야 합니다.


### <a name="OSDJoinDomainOUName"></a> OSDJoinDomainOUName

 ‘[도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 가입하는 OU(조직 구성 단위)의 RFC 1779 형식 이름을 지정합니다. 지정하는 경우 값에 전체 경로가 포함되어야 합니다. OU 이름의 길이는 0-32,767자 사이여야 합니다. [OSDJoinType](#OSDJoinType) 변수가 `1`(작업 그룹에 가입)로 설정되면 이 값이 설정되지 않습니다.

 #### <a name="example"></a>예
 `LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com`  

  
### <a name="OSDJoinPassword"></a> OSDJoinPassword

 ‘다음 단계에 적용합니다.’  
 - [네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings)  
 - [도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup)  


 (입력)

 Active Directory 도메인에 가입하기 위해 대상 컴퓨터에서 사용하는 [OSDJoinAccount](#OSDJoinAccount)에 대한 암호를 지정합니다. 작업 순서 환경에서 이 변수를 포함하지 않는 경우 Windows 설치 프로그램에서 빈 암호를 시도합니다. [OSDJoinType](#OSDJoinType) 변수가 `0`(도메인에 가입)으로 설정된 경우 이 값이 필요합니다.


### <a name="OSDJoinSkipReboot"></a> OSDJoinSkipReboot

 ‘[도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 도메인 또는 작업 그룹에 가입한 후 다시 시작하기를 건너뛸지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`  


### <a name="OSDJoinType"></a> OSDJoinType

 ‘[도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 Windows 도메인 또는 작업 그룹에 가입하는지 여부를 지정합니다. 

 #### <a name="valid-values"></a>유효한 값
 - `0`: 대상 컴퓨터를 Windows 도메인에 가입합니다.  
 - `1`: 대상 컴퓨터를 작업 그룹에 가입합니다.  


### <a name="OSDJoinWorkgroupName"></a> OSDJoinWorkgroupName

 ‘[도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 가입하는 작업 그룹의 이름을 지정합니다. 작업 그룹 이름은 1-32자 사이여야 합니다.


### <a name="OSDKeepActivation"></a> OSDKeepActivation

 ‘[Windows 캡처 준비](task-sequence-steps.md#BKMK_PrepareWindowsforCapture) 단계에 적용됩니다.’

 (입력)

 Sysprep이 제품 활성화 플래그를 다시 설정하는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`
 - `false`(기본값)


### <a name="OSDLocalAdminPassword"></a> OSDLocalAdminPassword

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 (입력)

 로컬 관리자 계정의 암호를 지정합니다. **로컬 관리자 암호를 임의로 생성하고 지원되는 모든 플랫폼에서 계정 사용 안 함** 옵션을 사용하도록 설정할 경우 이 단계에서 이 변수를 무시합니다. 지정된 값은 1-255자 사이여야 합니다.


### <a name="OSDMigrateAdapterSettings"></a> OSDMigrateAdapterSettings

 ‘[네트워크 설정 캡처](task-sequence-steps.md#BKMK_CaptureNetworkSettings) 단계에 적용됩니다.’

 (입력)

 작업 순서에서 네트워크 어댑터 정보를 캡처할지 여부를 지정합니다. 이 정보에는 TCP/IP, DNS 및 WINS에 대한 구성 설정이 포함됩니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값)
 - `false`


### <a name="OSDMigrateAdditionalCaptureOptions"></a> OSDMigrateAdditionalCaptureOptions

 ‘[사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState) 단계에 적용됩니다.’

 (입력)

 작업 순서에서 사용자 상태를 캡처하는 데 사용하는 추가 USMT(사용자 환경 마이그레이션 도구) 명령줄 옵션을 지정합니다. 이 단계는 작업 순서 편집기에서 이러한 설정을 노출하지 않습니다. 이러한 옵션은 작업 순서에서 ScanState용으로 자동 생성된 USMT 명령줄에 추가하는 문자열로 지정합니다.

 작업 순서를 실행하기 전에 이 작업 순서 변수를 사용하여 지정된 USMT 옵션이 정확성에 대한 유효성이 검사되지 않았습니다.

 사용할 수 있는 옵션에 대한 자세한 내용은 [ScanState Syntax](https://docs.microsoft.com/windows/deployment/usmt/usmt-scanstate-syntax)\(ScanState 구문\)을 참조하세요.


### <a name="OSDMigrateAdditionalRestoreOptions"></a> OSDMigrateAdditionalRestoreOptions

 ‘[사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState) 단계에 적용됩니다.’

 (입력)

 작업 순서에서 사용자 상태를 복원할 때 사용하는 추가 USMT(사용자 환경 마이그레이션 도구) 명령줄 옵션을 지정합니다. 작업 순서에서 LoadState용으로 자동 생성된 USMT 명령줄에 추가하는 문자열로서 추가 옵션을 지정합니다. 

 작업 순서를 실행하기 전에 이 작업 순서 변수를 사용하여 지정된 USMT 옵션이 정확성에 대한 유효성이 검사되지 않았습니다.

 사용할 수 있는 옵션에 대한 자세한 내용은 [LoadState Syntax](https://docs.microsoft.com/windows/deployment/usmt/usmt-loadstate-syntax)\(LoadState 구문\)을 참조하세요.


### <a name="OSDMigrateComputerName"></a> OSDMigrateComputerName

 ‘[Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings) 단계에 적용됩니다.’

 (입력)

 컴퓨터 이름이 마이그레이션되는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값). [OSDComputerName(출력)](#OSDComputerName-output) 변수가 컴퓨터의 NetBIOS 이름으로 설정됩니다.  
 - `false`   


### <a name="OSDMigrateConfigFiles"></a> OSDMigrateConfigFiles

 ‘[사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState) 단계에 적용됩니다.’

 (입력)

 사용자 프로필의 캡처를 제어하기 위해 사용되는 구성 파일을 지정합니다. 이 변수는 [OSDMigrateMode](#OSDMigrateMode)가 `Advanced`로 설정된 경우에만 사용됩니다. 이 쉼표로 구분된 목록 값은 사용자 지정된 사용자 프로필 마이그레이션을 수행하기 위해 설정됩니다.

 #### <a name="example"></a>예
 `miguser.xml,migsys.xml,migapps.xml`  


### <a name="OSDMigrateContinueOnLockedFiles"></a> OSDMigrateContinueOnLockedFiles

 ‘[사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState) 단계에 적용됩니다.’

 (입력)

 USMT에서 일부 파일을 캡처할 수 없는 경우 이 변수는 사용자 상태 캡처가 진행되도록 합니다. 

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값)  
 - `false`   


### <a name="OSDMigrateContinueOnRestore"></a> OSDMigrateContinueOnRestore

 ‘[사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState) 단계에 적용됩니다.’

 (입력)

 USMT에서 일부 파일을 복원할 수 없는 경우에도 프로세스를 계속합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값)  
 - `false`  


### <a name="OSDMigrateEnableVerboseLogging"></a> OSDMigrateEnableVerboseLogging

 ‘다음 단계에 적용합니다.’  
 - [사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState)  
 - [사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState)  


 (입력)

 USMT에 대해 자세한 정보 로깅을 사용합니다. 단계에 이 값이 필요합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`(기본값)  


### <a name="OSDMigrateLocalAccounts"></a> OSDMigrateLocalAccounts

 ‘[사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState) 단계에 적용됩니다.’

 (입력)

 로컬 컴퓨터 계정이 복원되는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`(기본값)  


### <a name="OSDMigrateLocalAccountPassword"></a> OSDMigrateLocalAccountPassword

 ‘[사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState) 단계에 적용됩니다.’

 (입력)

 [OSDMigrateLocalAccounts](#OSDMigrateLocalAccounts) 변수가 `true`인 경우 이 변수는 마이그레이션되는 *모든* 로컬 계정에 할당되는 암호를 포함해야 합니다. USMT는 마이그레이션되는 모든 로컬 계정에 같은 암호를 할당합니다. 이 암호는 임시 암호라고 생각하고 나중에 다른 방법을 사용하여 변경하세요.


### <a name="OSDMigrateMode"></a> OSDMigrateMode

 ‘[사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState) 단계에 적용됩니다.’

 (입력)

 USMT에서 캡처하는 파일을 사용자 지정할 수 있습니다. 

 #### <a name="valid-values"></a>유효한 값
 - `Simple`: 작업 순서에서 표준 USMT 구성 파일만 사용합니다.  

 - `Advanced`: 작업 순서 변수 [OSDMigrateConfigFiles](#OSDMigrateConfigFiles)에서 USMT가 사용하는 구성 파일을 지정합니다.  


### <a name="OSDMigrateNetworkMembership"></a> OSDMigrateNetworkMembership

 ‘[네트워크 설정 캡처](task-sequence-steps.md#BKMK_CaptureNetworkSettings) 단계에 적용됩니다.’

 (입력)

 작업 순서에서 작업 그룹 또는 도메인 멤버 자격 정보를 마이그레이션하는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값)
 - `false`


### <a name="OSDMigrateRegistrationInfo"></a> OSDMigrateRegistrationInfo

 ‘[Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings) 단계에 적용됩니다.’

 (입력)

 단계에서 사용자 및 조직 정보를 마이그레이션하는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값). [OSDRegisteredOrgName(출력)](#OSDRegisteredOrgName-output) 변수가 컴퓨터의 등록된 조직 이름으로 설정됩니다.  
 - `false`   


### <a name="OSDMigrateSkipEncryptedFiles"></a> OSDMigrateSkipEncryptedFiles

 ‘[사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState) 단계에 적용됩니다.’

 (입력)

 암호화된 파일이 캡처되는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`(기본값)  


### <a name="OSDMigrateTimeZone"></a> OSDMigrateTimeZone

 ‘[Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings) 단계에 적용됩니다.’

 (입력)

 컴퓨터의 표준 시간대가 마이그레이션되는지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값). 변수 [OSDTimeZone(출력)](#OSDTimeZone-output)이 컴퓨터의 표준 시간대로 설정됩니다.  
 - `false`   


### <a name="OSDNetworkJoinType"></a> OSDNetworkJoinType

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 Active Directory 도메인 또는 작업 그룹에 가입하는지 여부를 지정합니다.

 #### <a name="value-values"></a>유효한 값
 - `0`: Active Directory 도메인에 가입합니다.  
 - `1`: 작업 그룹에 가입합니다.


### <a name="OSDPartitions"></a> OSDPartitions

 ‘[디스크 포맷 및 파티션 만들기](task-sequence-steps.md#BKMK_FormatandPartitionDisk) 단계에 적용됩니다.’

 (입력)

 이 작업 순서 변수는 파티션 설정의 배열 변수입니다. 배열의 각 요소는 하드 디스크에서 단일 파티션에 대한 설정을 나타냅니다. 각 파티션에 대해 정의된 설정은 배열 변수 이름과 0부터 시작하는 디스크 파티션 번호 및 속성 이름을 결합하여 액세스할 수 있습니다.

다음 변수 이름을 사용하여 이 단계에서 하드 디스크에 만들 ‘첫 번째’ 파티션에 대한 속성을 정의하세요.

 #### <a name="osdpartitions0type"></a>OSDPartitions0Type
 파티션의 유형을 지정합니다. 이 속성은 필수입니다. 유효한 값은 `Primary`, `Extended`, `Logical` 및 `Hidden`입니다.

 #### <a name="osdpartitions0filesystem"></a>OSDPartitions0FileSystem
 파티션을 포맷할 때 사용할 파일 시스템의 유형을 지정합니다. 이 속성은 선택 사항입니다. 파일 시스템을 지정하지 않으면 단계에서 파티션을 포맷하지 않습니다. 유효한 값은 `FAT32` 및 `NTFS`입니다.

 #### <a name="osdpartitions0bootable"></a>OSDPartitions0Bootable
 파티션이 부팅 가능한지 여부를 지정합니다. 이 속성은 필수입니다. 이 값이 MBR 디스크에 대해 `TRUE`로 설정되면 단계에서 이 파티션을 활성 파티션으로 표시합니다.

 #### <a name="osdpartitions0quickformat"></a>OSDPartitions0QuickFormat
 사용되는 포맷 유형을 지정합니다. 이 속성은 필수입니다. 이 값이 `TRUE`로 설정되면 단계에서 빠른 포맷을 수행합니다. 그렇지 않으면 단계에서 전체 포맷을 수행합니다.

 #### <a name="osdpartitions0volumename"></a>OSDPartitions0VolumeName
 포맷될 때 볼륨에 할당되는 이름을 지정합니다. 이 속성은 선택 사항입니다.

 #### <a name="osdpartitions0size"></a>OSDPartitions0Size
 파티션의 크기를 지정합니다. 이 속성은 선택 사항입니다. 이 속성이 지정되지 않은 경우 남아 있는 모든 사용 가능한 공간을 사용하여 파티션이 만들어집니다. 단위는 **OSDPartitions0SizeUnits** 변수로 지정됩니다.

 #### <a name="osdpartitions0sizeunits"></a>OSDPartitions0SizeUnits
 단계에서 이러한 단위를 사용하여 **OSDPartitions0Size** 변수를 해석합니다. 이 속성은 선택 사항입니다. 유효한 값은 `MB`(기본값), `GB` 및 `Percent`입니다.

 #### <a name="osdpartitions0volumelettervariable"></a>OSDPartitions0VolumeLetterVariable
 이 단계에서 파티션을 만들 때 Windows PE에서 항상 사용 가능한 다음 드라이브 문자를 사용합니다. 이 선택적 속성을 사용하여 다른 작업 순서 변수의 이름을 지정할 수 있습니다. 이 단계에서는 이 변수를 사용하여 나중에 참조할 새 드라이브 문자를 저장합니다.

 이 작업 순서 단계를 사용하여 여러 파티션을 정의하는 경우 ‘두 번째’ 파티션에 대한 속성이 변수 이름의 **1** 인덱스를 사용하여 정의됩니다. 예를 들어 **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat** 및 **OSDPartitions1VolumeName**이 있습니다.


### <a name="OSDPartitionStyle"></a> OSDPartitionStyle

 ‘[디스크 포맷 및 파티션 만들기](task-sequence-steps.md#BKMK_FormatandPartitionDisk) 단계에 적용됩니다.’

 (입력)

 디스크를 분할하는 경우 사용할 파티션 스타일을 지정합니다. 

 #### <a name="valid-values"></a>유효한 값
 - `GPT`: GUID 파티션 테이블 스타일을 사용합니다.
 - `MBR`: 마스터 부트 레코드 파티션 스타일을 사용합니다.


### <a name="OSDProductKey"></a> OSDProductKey

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 (입력)

 Windows 제품 키를 지정합니다. 지정된 값은 1-255자 사이여야 합니다.


### <a name="OSDRandomAdminPassword"></a> OSDRandomAdminPassword

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 (입력)

 새 OS에서 로컬 관리자 계정에 대해 임의로 생성된 암호를 지정합니다. 

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값): Windows 설치 프로그램이 대상 컴퓨터에서 로컬 관리자 계정을 사용하지 않도록 설정합니다.  

 - `false`: Windows 설치 프로그램이 대상 컴퓨터에서 로컬 관리자 계정을 사용하도록 설정하고 계정 암호를 [OSDLocalAdminPassword](#OSDLocalAdminPassword) 값으로 설정합니다.  


### <a name="OSDRegisteredOrgName-input"></a> OSDRegisteredOrgName(입력)

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 새 OS에서 등록된 기본 조직 이름을 지정합니다. 지정된 값은 1-255자 사이여야 합니다.


### <a name="OSDRegisteredOrgName-output"></a> OSDRegisteredOrgName(출력)

 ‘[Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings) 단계에 적용됩니다.’

 컴퓨터의 등록된 조직 이름으로 설정됩니다. [OSDMigrateRegistrationInfo](#OSDMigrateRegistrationInfo) 변수가 `true`로 설정된 경우에만 이 값이 설정됩니다.


### <a name="OSDRegisteredUserName"></a> OSDRegisteredUserName

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 (입력)

 새 OS에서 등록된 기본 사용자 이름을 지정합니다. 지정된 값은 1-255자 사이여야 합니다.


### <a name="OSDServerLicenseConnectionLimit"></a> OSDServerLicenseConnectionLimit

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 (입력)

 허용되는 최대 연결 수를 지정합니다. 지정된 숫자는 5에서 9999개 연결 사이의 범위에 있어야 합니다.


### <a name="OSDServerLicenseMode"></a> OSDServerLicenseMode

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 (입력)

 사용되는 Windows Server 라이선스 모드를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `PerSeat`
 - `PerServer`


### <a name="OSDSetupAdditionalUpgradeOptions"></a> OSDSetupAdditionalUpgradeOptions

 ‘[운영 체제 업그레이드](task-sequence-steps.md#BKMK_UpgradeOS) 단계에 적용됩니다.’

 (입력)

 Windows 10 업그레이드 중 Windows 설치 프로그램에 추가된 추가 명령줄 옵션을 지정합니다. 작업 순서에서는 명령줄 옵션을 확인하지 않습니다. 

 자세한 내용은 [Windows 설치 프로그램 명령줄 옵션](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-setup-command-line-options)을 참조하세요.


### <a name="OSDStateFallbackToNAA"></a> OSDStateFallbackToNAA

 ‘[상태 저장소 요청](task-sequence-steps.md#BKMK_RequestStateStore) 단계에 적용됩니다.’

 (입력)

 컴퓨터 계정이 상태 마이그레이션 지점에 연결하지 못한 경우 작업 순서에서 NAA(네트워크 액세스 계정)를 대체로 사용해야 하는지 여부를 지정합니다. 

 네트워크 액세스 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#network-access-account)을 참조하세요.

 #### <a name="valid-values"></a>유효한 값
 - `true`  
 - `false`(기본값)  


### <a name="OSDStateSMPRetryCount"></a> OSDStateSMPRetryCount

 ‘[상태 저장소 요청](task-sequence-steps.md#BKMK_RequestStateStore) 단계에 적용됩니다.’

 (입력)

 이 단계가 실패하기 전에 작업 순서 단계가 상태 마이그레이션 지점을 찾으려고 시도하는 횟수를 지정합니다. 지정된 횟수는 0에서 600 사이여야 합니다.


### <a name="OSDStateSMPRetryTime"></a> OSDStateSMPRetryTime

 ‘[상태 저장소 요청](task-sequence-steps.md#BKMK_RequestStateStore) 단계에 적용됩니다.’

 (입력)

 작업 순서 단계가 다시 시도하기 전에 대기할 시간(초)을 지정합니다. 시간(초)은 최대 30자까지 가능합니다.


### <a name="OSDStateStorePath"></a> OSDStateStorePath

 ‘다음 단계에 적용합니다.’  
 - [사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState)  
 - [상태 저장소 해제](task-sequence-steps.md#BKMK_ReleaseStateStore)  
 - [상태 저장소 요청](task-sequence-steps.md#BKMK_RequestStateStore)  
 - [사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState)  


 (입력)

 작업 순서에서 사용자 상태를 저장하거나 복원하는 폴더의 네트워크 공유 또는 로컬 경로 이름입니다. 기본값은 없습니다.


### <a name="OSDTargetSystemDrive"></a> OSDTargetSystemDrive

 ‘[운영 체제 이미지 적용](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage) 단계에 적용됩니다.’

 (출력)

 이미지가 적용된 후 OS 파일이 포함된 파티션의 드라이브 문자를 지정합니다.


### <a name="OSDTargetSystemRoot-input"></a> OSDTargetSystemRoot (input)

 ‘[운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage) 단계에 적용됩니다.’

 참조 컴퓨터에 설치된 OS의 Windows 디렉터리 경로를 지정합니다. 작업 순서에서는 이 OS를 Configuration Manager에서 캡처할 수 있도록 지원되는 OS로 확인합니다.


### <a name="OSDTargetSystemRoot-output"></a> OSDTargetSystemRoot(출력)

 ‘[Windows 캡처 준비](task-sequence-steps.md#BKMK_PrepareWindowsforCapture) 단계에 적용됩니다.’

 참조 컴퓨터에 설치된 OS의 Windows 디렉터리 경로를 지정합니다. 작업 순서에서는 이 OS를 Configuration Manager에서 캡처할 수 있도록 지원되는 OS로 확인합니다.


### <a name="OSDTimeZone-input"></a> OSDTimeZone(입력)

 ‘[Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings) 단계에 적용됩니다.’

 새 OS에서 사용되는 기본 표준 시간대 설정을 지정합니다.


### <a name="OSDTimeZone-output"></a> OSDTimeZone(출력)

 ‘[Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings) 단계에 적용됩니다.’

 컴퓨터의 표준 시간대로 설정됩니다. [OSDMigrateTimeZone](#OSDMigrateTimeZone) 변수가 `true`로 설정된 경우에만 이 값이 설정됩니다.


### <a name="OSDWipeDestinationPartition"></a> OSDWipeDestinationPartition

 ‘[데이터 이미지 적용](task-sequence-steps.md#BKMK_ApplyDataImage) 단계에 적용됩니다.’

 (입력)

 대상 파티션에 있는 파일을 삭제할지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `true`(기본값)
 - `false`


### <a name="OSDWorkgroupName"></a> OSDWorkgroupName

 ‘[네트워크 설정 적용](task-sequence-steps.md#BKMK_ApplyNetworkSettings) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터가 가입하는 작업 그룹의 이름을 지정합니다.

 이 변수 또는 [OSDDomainName](#OSDDomainName) 변수 중 하나를 지정합니다. 작업 그룹 이름은 최대 32자까지 가능합니다. 


### <a name="SMSClientInstallProperties"></a> SMSClientInstallProperties

 ‘[Windows 및 ConfigMgr 설치](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) 단계에 적용됩니다.’

 (입력)

 구성 관리자 클라이언트를 설치할 때 작업 순서에서 사용하는 클라이언트 설치 속성을 지정합니다.

 자세한 내용은 [클라이언트 설치 매개 변수 및 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.


### <a name="SMSConnectNetworkFolderAccount"></a> SMSConnectNetworkFolderAccount

 ‘[네트워크 폴더에 연결](task-sequence-steps.md#BKMK_ConnectToNetworkFolder) 단계에 적용됩니다.’

 (입력)

 [SMSConnectNetworkFolderPath](#SMSConnectNetworkFolderPath)에서 네트워크 공유에 연결하는 데 사용되는 사용자 계정을 지정합니다. [SMSConnectNetworkFolderPassword](#SMSConnectNetworkFolderPassword) 값을 사용하여 계정 암호를 지정합니다.

 작업 순서 네트워크 폴더 연결 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-editor-network-folder-connection-account)을 참조하세요.


### <a name="SMSConnectNetworkFolderDriveLetter"></a> SMSConnectNetworkFolderDriveLetter

 ‘[네트워크 폴더에 연결](task-sequence-steps.md#BKMK_ConnectToNetworkFolder) 단계에 적용됩니다.’

 (입력)

 연결할 네트워크 드라이브 문자를 지정합니다. 이 값은 선택 사항입니다. 지정하지 않으면 네트워크 연결이 드라이브 문자에 매핑되지 않습니다. 이 값을 지정하는 경우 D에서 Z까지의 범위 값이어야 합니다. X는 Windows PE 단계 중 Windows PE에서 사용하는 드라이브 문자이므로 사용하지 않습니다.

 #### <a name="examples"></a>예
 - `D:`  
 - `E:`  


### <a name="SMSConnectNetworkFolderPassword"></a> SMSConnectNetworkFolderPassword

 ‘[네트워크 폴더에 연결](task-sequence-steps.md#BKMK_ConnectToNetworkFolder) 단계에 적용됩니다.’

 (입력)

 [SMSConnectNetworkFolderPath](#SMSConnectNetworkFolderPath)에서 네트워크 공유에 연결하는 데 사용되는 [SMSConnectNetworkFolderAccount](#SMSConnectNetworkFolderAccount) 암호를 지정합니다. 


### <a name="SMSConnectNetworkFolderPath"></a> SMSConnectNetworkFolderPath

 ‘[네트워크 폴더에 연결](task-sequence-steps.md#BKMK_ConnectToNetworkFolder) 단계에 적용됩니다.’

 (입력)

 연결에 대한 네트워크 경로를 지정합니다. 이 경로를 드라이브 문자에 매핑해야 하는 경우 [SMSConnectNetworkFolderDriveLetter](#SMSConnectNetworkFolderDriveLetter) 값을 사용합니다.

 #### <a name="example"></a>예
 `\\server\share`


### <a name="SMSInstallUpdateTarget"></a> SMSInstallUpdateTarget

 ‘[소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates) 단계에 적용됩니다.’

 (입력)

 모든 업데이트를 설치할지 아니면 필수 업데이트만 설치할지 여부를 지정합니다.

 #### <a name="valid-values"></a>유효한 값
 - `All`  
 - `Mandatory`  


### <a name="SMSRebootMessage"></a> SMSRebootMessage

 ‘[컴퓨터 다시 시작](task-sequence-steps.md#BKMK_RestartComputer) 단계에 적용됩니다.’

 (입력)

 대상 컴퓨터를 다시 시작하기 전에 사용자에게 표시할 메시지를 지정합니다. 이 변수가 설정되지 않은 경우 기본 메시지 텍스트가 표시됩니다. 지정된 메시지는 512자를 초과할 수 없습니다.

 #### <a name="example"></a>예
 `Save your work before the computer restarts.`  


### <a name="SMSRebootTimeout"></a> SMSRebootTimeout

 ‘[컴퓨터 다시 시작](task-sequence-steps.md#BKMK_RestartComputer) 단계에 적용됩니다.’

 (입력)

 컴퓨터가 다시 시작하기 전에 경고가 사용자에게 표시되는 시간(초)을 지정합니다. 

 #### <a name="examples"></a>예
 - `0`(기본값): 다시 부팅 메시지를 표시하지 않습니다.  
 - `60`: 1분 동안 경고를 표시합니다.  


### <a name="SMSTSAssignmentsDownloadInterval"></a> SMSTSAssignmentsDownloadInterval

 정책이 반환되지 않은 마지막 시도 이후 정책을 다운로드하기 위해 클라이언트가 대기하는 시간(초)입니다. 기본적으로는 클라이언트는 **0**초를 대기한 후 다시 시도합니다. 

 미디어 또는 PXE에서 시작 전 명령을 사용하여 이 변수를 설정할 수 있습니다.


### <a name="SMSTSAssignmentsDownloadRetry"></a> SMSTSAssignmentsDownloadRetry

 첫 번째 시도에서 정책을 찾지 못한 이후 클라이언트가 정책 다운로드를 시도하는 횟수입니다. 기본적으로 클라이언트는 **0**회를 다시 시도합니다.

 미디어 또는 PXE에서 시작 전 명령을 사용하여 이 변수를 설정할 수 있습니다.


### <a name="SMSTSAssignUsersMode"></a> SMSTSAssignUsersMode

 작업 순서에서 사용자를 대상 컴퓨터와 연결하는 방법을 지정합니다. 변수를 다음 값 중 하나로 설정합니다.  

 - **자동**: 작업 순서에서 OS를 대상 컴퓨터에 배포할 때 지정된 사용자와 대상 컴퓨터 사이의 관계를 만듭니다.  

 - **보류 중**: 작업 순서에서 지정된 사용자와 대상 컴퓨터 사이의 관계를 만듭니다. 관리자는 해당 관계를 승인하여 설정해야 합니다.  

 - **사용 안 함**: 작업 순서에서 OS를 배포할 때 사용자를 대상 컴퓨터와 연결하지 않습니다.


### <a name="SMSTSDisableStatusRetry"></a> SMSTSDisableStatusRetry
 <!--512358--> 연결이 끊긴 시나리오에서 작업 순서 엔진은 관리 지점으로 상태 메시지를 전송하려고 반복적으로 시도합니다. 이 시나리오에서는 이 동작으로 인해 작업 순서 처리가 지연될 수 있습니다. 

 버전 1802부터 이 변수를 `true`로 설정하면 작업 순서 엔진이 첫 번째 메시지 전송 실패 후 상태 메시지를 다시 전송하려고 시도하지 않습니다. 이 첫 번째 시도에 여러 번의 재시도가 포함합니다.

 작업 순서가 다시 시작되면 이 변수 값이 유지됩니다. 그러나 작업 순서는 초기 상태 메시지를 보내려고 시도합니다. 이 첫 번째 시도에 여러 번의 재시도가 포함합니다. 시도가 성공하면 이 변수 값에 관계없이 작업 순서에서 계속해서 상태를 보냅니다. 상태 전송이 실패하면 작업 순서에서 이 변수 값을 사용합니다.

 > [!NOTE]  
 > [작업 순서 상태 보고](/sccm/core/servers/manage/list-of-reports#task-sequence---deployment-status)에서는 이러한 상태 메시지를 사용하여 각 단계의 진행률, 기록 및 세부 정보를 표시합니다.


### <a name="SMSTSDisableWow64Redirection"></a> SMSTSDisableWow64Redirection

 ‘[명령줄 실행](task-sequence-steps.md#BKMK_RunCommandLine) 단계에 적용됩니다.’

 (입력)

 기본적으로 64비트 OS에서는 작업 순서가 WOW64 파일 시스템 리디렉터를 사용하여 명령줄에서 프로그램을 찾아 실행합니다. 이 동작을 통해 명령은 32비트 버전의 OS 프로그램과 DLL을 찾을 수 있습니다. 이 변수를 `true`로 설정하면 WOW64 파일 시스템 리디렉터가 사용되지 않습니다. 이 명령은 네이티브 64비트 버전의 OS 프로그램과 DLL을 찾습니다. 이 변수는 32비트 OS에서 실행할 때는 아무런 영향이 없습니다.


### <a name="SMSTSDownloadAbortCode"></a> SMSTSDownloadAbortCode

 이 변수에는 외부 프로그램 다운로더의 중단 코드 값이 포함되어 있습니다. 이 프로그램은 [SMSTSDownloadProgram](#SMSTSDownloadProgram) 변수에 지정됩니다. 프로그램이 SMSTSDownloadAbortCode 변수 값과 같은 오류 코드를 반환하면 콘텐츠 다운로드에 실패하고 다른 다운로드 방법이 시도되지 않습니다.


### <a name="SMSTSDownloadProgram"></a> SMSTSDownloadProgram

 이 변수를 사용하여 대체 콘텐츠 공급자(ACP)를 지정합니다. ACP는 콘텐츠를 다운로드하는 데 사용되는 다운로더 프로그램입니다. 작업 순서에서는 기본 Configuration Manager 다운로더 대신 ACP를 사용합니다. 콘텐츠 다운로드 프로세스의 일부로서, 작업 순서에서는 이 변수를 확인합니다. 지정된 경우 작업 순서에서는 콘텐츠를 다운로드하는 프로그램을 실행합니다.


### <a name="SMSTSDownloadRetryCount"></a> SMSTSDownloadRetryCount

 Configuration Manager가 배포 지점의 콘텐츠를 다운로드하기 위해 시도할 횟수입니다. 기본적으로 클라이언트는 **2**회를 다시 시도합니다.


### <a name="SMSTSDownloadRetryDelay"></a> SMSTSDownloadRetryDelay

 Configuration Manager가 배포 지점의 콘텐츠를 다시 다운로드하기 전까지 대기하는 시간(초)입니다. 기본적으로는 클라이언트는 **15**초를 대기한 후 다시 시도합니다.


### <a name="SMSTSDriverRequestConnectTimeOut"></a> SMSTSDriverRequestConnectTimeOut

 ‘[드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers) 단계에 적용됩니다.’

 드라이버 카탈로그를 요청할 경우 이 변수는 작업 순서가 HTTP 서버 연결을 기다리는 시간(초)입니다. 연결이 시간 제한 설정보다 오래 걸리면 작업 순서가 요청을 취소합니다. 시간 제한은 **60**초로 기본 설정됩니다.


### <a name="SMSTSDriverRequestReceiveTimeOut"></a> SMSTSDriverRequestReceiveTimeOut

 ‘[드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers) 단계에 적용됩니다.’

 드라이버 카탈로그를 요청할 경우 이 변수는 작업 순서가 응답을 기다리는 시간(초)입니다. 연결이 시간 제한 설정보다 오래 걸리면 작업 순서가 요청을 취소합니다. 시간 제한은 **480**초로 기본 설정됩니다.


### <a name="SMSTSDriverRequestResolveTimeOut"></a> SMSTSDriverRequestResolveTimeOut

 ‘[드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers) 단계에 적용됩니다.’

 드라이버 카탈로그를 요청할 경우 이 변수는 작업 순서가 HTTP 이름 확인을 기다리는 시간(초)입니다. 연결이 시간 제한 설정보다 오래 걸리면 작업 순서가 요청을 취소합니다. 시간 제한은 **60**초로 기본 설정됩니다.


### <a name="SMSTSDriverRequestSendTimeOut"></a> SMSTSDriverRequestSendTimeOut

 ‘[드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers) 단계에 적용됩니다.’

 드라이버 카탈로그에 대한 요청을 보낼 경우 이 변수는 작업 순서가 요청을 보내기 위해 기다리는 시간(초)입니다. 요청이 시간 제한 설정보다 오래 걸리면 작업 순서가 요청을 취소합니다. 시간 제한은 **60**초로 기본 설정됩니다.


### <a name="SMSTSErrorDialogTimeout"></a> SMSTSErrorDialogTimeout

 작업 순서에서 오류가 발생할 경우 오류가 포함된 대화 상자가 표시됩니다. 이 변수에 지정된 시간(초)이 지나면 작업 순서에서 이 대화 상자를 자동으로 해제합니다. 기본적으로 이 값은 **900**초(15분)입니다.


### <a name="SMSTSLanguageFolder"></a> SMSTSLanguageFolder

 이 변수를 사용하여 언어 중립 부팅 이미지의 언어 표시를 변경할 수 있습니다.


### <a name="SMSTSLocalDataDrive"></a> SMSTSLocalDataDrive

 작업 순서가 실행되는 동안 대상 컴퓨터에서 임시 파일이 저장되는 위치를 지정합니다.

 작업 순서를 시작하기 전에 컬렉션 변수를 설정하는 등의 방법으로 이 변수를 설정합니다. 작업 순서가 시작되면 Configuration Manager에서 [_SMSTSMDataPath](#SMSTSMDataPath) 변수를 정의합니다.


### <a name="SMSTSMP"></a> SMSTSMP

 이 변수를 사용하여 Configuration Manager 관리 지점의 URL 또는 IP 주소를 지정합니다.


### <a name="SMSTSMPListRequestTimeoutEnabled"></a> SMSTSMPListRequestTimeoutEnabled

 ‘다음 단계에 적용합니다.’  
 - [응용 프로그램 설치](task-sequence-steps.md#BKMK_InstallApplication)  
 - [소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates)  


 (입력) 

 클라이언트가 인트라넷에 없는 경우 이 변수를 사용하여 반복된 MPList 요청으로 클라이언트를 새로 고치도록 설정할 수 있습니다. 기본적으로 이 변수는 `True`로 설정됩니다. 

 클라이언트가 인터넷에 있는 경우에는 불필요한 지연이 발생하지 않도록 이 변수를 `False`로 설정할 수 있습니다. 


### <a name="SMSTSMPListRequestTimeout"></a> SMSTSMPListRequestTimeout

 ‘다음 단계에 적용합니다.’  
 - [응용 프로그램 설치](task-sequence-steps.md#BKMK_InstallApplication)  
 - [소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates)  


 (입력) 

 작업 순서가 위치 서비스에서 관리 지점 목록(MPList)을 검색하지 못하는 경우 이 변수는 이 단계를 다시 시도하기 전까지 작업 순서가 대기하는 시간(밀리초)을 지정합니다. 기본적으로 작업 순서는 `60000`밀리초(60초)를 대기한 후 단계를 다시 시도합니다. 최대 세 번까지 다시 시도합니다.


### <a name="SMSTSPeerDownload"></a> SMSTSPeerDownload

 이 변수를 사용하여 클라이언트가 Windows PE 피어 캐시를 사용할 수 있도록 합니다. 이 변수를 `true`로 설정하면 이 기능을 사용할 수 있습니다.


### <a name="SMSTSPeerRequestPort"></a> SMSTSPeerRequestPort

 Windows PE 피어 캐시가 초기 브로드캐스트에 사용하는 사용자 지정 네트워크 포트입니다. 클라이언트 설정에 구성된 기본 포트는 **8004**입니다.


### <a name="SMSTSPersistContent"></a> SMSTSPersistContent

 이 변수를 사용하여 작업 순서 캐시에 콘텐츠를 일시적으로 유지할 수 있습니다. 이 변수는 작업 순서가 완료된 후 구성 관리자 클라이언트 캐시에 콘텐츠를 유지 관리하는 [SMSTSPreserveContent](#SMSTSPreserveContent)와 다릅니다. SMSTSPersistContent는 작업 순서 캐시를 사용하고, SMSTSPreserveContent는 Configuration Manager 클라이언트 캐시를 사용합니다. 


### <a name="SMSTSPostAction"></a> SMSTSPostAction

 작업 순서를 완료한 후 실행되는 명령을 지정합니다. 예를 들어 작업 순서에서 장치에 OS를 배포한 후 포함된 장치에서 쓰기 필터를 사용할 수 있는 스크립트를 지정합니다.


### <a name="SMSTSPreferredAdvertID"></a> SMSTSPreferredAdvertID

 작업 순서가 대상 컴퓨터에 지정된 특정 배포를 강제로 실행하도록 합니다. 미디어 또는 PXE에서 시작 전 명령을 통해 이 변수를 설정할 수 있습니다. 이 변수를 설정한 경우에는 작업 순서가 모든 필수 배포를 재정의합니다.


### <a name="SMSTSPreserveContent"></a> SMSTSPreserveContent

 이 변수는 배포 후 구성 관리자 클라이언트 캐시에 보존할 작업 순서의 콘텐츠에 플래그를 지정합니다. 이 변수는 작업 순서의 기간에 대한 콘텐츠만 유지하는 [SMSTSPersistContent](#SMSTSPersistContent)와 다릅니다. SMSTSPersistContent는 작업 순서 캐시를 사용하고, SMSTSPreserveContent는 Configuration Manager 클라이언트 캐시를 사용합니다. 이 기능을 사용하려면 SMSTSPreserveContent를 `true`로 설정합니다.


### <a name="SMSTSRebootDelay"></a> SMSTSRebootDelay

 컴퓨터를 다시 시작하기 전에 대기할 시간(초)을 지정합니다. 이 변수가 0일 경우 다시 부팅하기 전에 작업 순서 관리자가 알림 대화 상자를 표시하지 않습니다.

 #### <a name="example"></a>예
 - `0`: 알림을 표시하지 않습니다.  

 - `60`: 1분 동안 알림을 표시합니다.  


### <a name="SMSTSRebootMessage"></a> SMSTSRebootMessage

 다시 시작 알림 대화 상자에 표시할 메시지를 지정합니다. 이 변수를 설정하지 않으면 기본 메시지가 표시됩니다.

 #### <a name="example"></a>예
 `The task sequence is restarting this computer`


### <a name="SMSTSRebootRequested"></a> SMSTSRebootRequested

 현재 작업 순서 단계를 완료한 후 다시 시작이 요청됨을 나타냅니다. 다시 시작이 필요한 경우 이 변수를 `true`로 설정하세요. 그러면 이 작업 순서 단계가 수행된 후에 컴퓨터가 다시 시작됩니다. 작업 순서 단계에서 작업을 완료하기 위해 컴퓨터를 다시 시작해야 하는 경우 이 변수를 설정합니다. 컴퓨터가 다시 시작되면 다음 작업 순서 단계에서 작업 순서가 계속 실행됩니다.


### <a name="SMSTSRetryRequested"></a> SMSTSRetryRequested

 현재 작업 순서 단계를 완료한 후 다시 시도를 요청합니다. 이 작업 순서 변수를 설정한 경우에는 [SMSTSRebootRequested](#SMSTSRebootRequested)도 `true`로 설정하세요. 컴퓨터가 다시 시작되면 작업 순서 관리자가 동일한 작업 순서 단계를 다시 실행합니다.


### <a name="SMSTSRunCommandLineUserName"></a> SMSTSRunCommandLineUserName

 ‘[명령줄 실행](task-sequence-steps.md#BKMK_RunCommandLine) 단계에 적용됩니다.’

 (입력)

 명령줄을 실행할 계정을 지정합니다. 값은 양식 사용자 이름 또는 도메인\사용자 이름의 문자열입니다. [SMSTSRunCommandLinePassword](#SMSTSRunCommandLinePassword) 변수를 사용하여 계정 암호를 지정하세요.

 작업 순서 실행 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-run-as-account)을 참조하세요.


### <a name="SMSTSRunCommandLinePassword"></a> SMSTSRunCommandLinePassword

 ‘[명령줄 실행](task-sequence-steps.md#BKMK_RunCommandLine) 단계에 적용됩니다.’

 (입력)

 [SMSTSRunCommandLineUserName](#SMSTSRunCommandLineUserName) 변수에서 지정한 계정의 암호를 지정합니다.


### <a name="SMSTSSoftwareUpdateScanTimeout"></a> SMSTSSoftwareUpdateScanTimeout

 ‘[소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates) 단계에 적용됩니다.’

 (입력)

 이 단계에서 소프트웨어 업데이트 검사에 대한 제한 시간을 제어합니다. 예를 들어 검사 중에 여러 업데이트가 예상되는 경우 값을 높이세요. 기본값은 `1800`초(30분)입니다. 변수 값은 초 단위로 설정됩니다.


### <a name="SMSTSUDAUsers"></a> SMSTSUDAUsers

 `<DomainName>\<UserName>` 형식을 사용하여 대상 컴퓨터의 기본 사용자를 지정합니다. 여러 사용자를 구분하려면 쉼표(`,`)를 사용합니다. 자세한 내용은 [사용자를 대상 컴퓨터에 연결](/sccm/osd/get-started/associate-users-with-a-destination-computer)을 참조하세요.

 #### <a name="example"></a>예
 `contoso\jqpublic, contoso\megb, contoso\janedoh`


### <a name="SMSTSWaitForSecondReboot"></a> SMSTSWaitForSecondReboot

 ‘[소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates) 단계에 적용됩니다.’

 (입력)

 소프트웨어 업데이트 설치에서 두 번의 다시 시작을 요구하는 경우 이 선택적 작업 순서 변수를 사용하여 클라이언트 동작을 제어할 수 있습니다. 소프트웨어 업데이트 설치의 두 번째 다시 시작 때문에 작업 순서가 실패하는 것을 방지하려면 이 단계 전에 이 변수를 설정합니다.

 컴퓨터가 다시 시작될 때 이 단계에서 작업 순서가 일시 중지되는 시간을 지정하려면 SMSTSWaitForSecondReboot 값을 초 단위로 설정합니다. 두 번째 다시 시작이 있을 경우 충분한 시간을 허용합니다. 

예를 들어 SMSTSWaitForSecondReboot를 `600`으로 설정하면 다시 시작된 후 추가 단계가 실행되기 전에 작업 순서가 10분간 일시 중지됩니다. 이 변수는 단일 소프트웨어 업데이트 설치 작업 순서 단계에서 수백 개의 소프트웨어 업데이트를 설치하는 경우에 유용합니다.


### <a name="TSDisableProgressUI"></a> TSDisableProgressUI
 <!-- 1354291 --> 작업 순서가 최종 사용자에게 진행률을 표시하는 시기를 제어하려면 이 변수를 사용하세요. 다른 시간에 진행률을 숨기거나 표시하려면 이 변수를 작업 순서에 여러 번 설정합니다.  

 - `true`: 작업 순서 진행률을 숨깁니다.  

 - `false`: 작업 순서 진행률을 표시합니다.  


### <a name="TSErrorOnWarning"></a> TSErrorOnWarning 

 ‘[응용 프로그램 설치](task-sequence-steps.md#BKMK_InstallApplication) 단계에 적용됩니다.’

 (입력) 

 작업 순서 엔진이 이 단계에서 감지된 경고를 오류로 간주할지 여부를 지정합니다. 요구 사항이 충족되지 않아 하나 이상의 응용 프로그램 또는 필수 종속성이 설치되지 않은 경우에는 작업 순서에서 [_TSAppInstallStatus](#TSAppInstallStatus) 변수를 `Warning`으로 설정합니다. 이 변수를 `True`로 설정하고 작업 순서에서 **_TSAppInstallStatus**를 `Warning`으로 설정하면 오류가 발생합니다. `False` 값이 기본 동작입니다.


### <a name="WorkingDirectory"></a> WorkingDirectory

 ‘[명령줄 실행](task-sequence-steps.md#BKMK_RunCommandLine) 단계에 적용됩니다.’

 (입력)

 명령줄 동작에 대한 시작 디렉터리를 지정합니다. 지정된 디렉터리 이름은 255자를 초과할 수 없습니다.

 #### <a name="examples"></a>예
 - `C:\`  
 - `%SystemRoot%`  



## <a name="deprecated-variables"></a>사용되지 않는 변수

다음 변수는 사용되지 않습니다.

- **OSDAllowUnsignedDriver**: Windows Vista 이상 운영 체제를 배포하는 경우에는 사용되지 않습니다.
- **OSDBuildStorageDriverList**: Windows XP 및 Windows Server 2003에만 적용됩니다.
- **OSDDiskpartBiosCompatibilityMode**: Windows XP 또는 Windows Server 2003을 배포할 때만 필요합니다.
- **OSDInstallEditionIndex**: Windows Vista 이후에는 필요하지 않습니다.
- **OSDPreserveDriveLetter**: 자세한 내용은 [OSDPreserveDriveLetter](#OSDPreserveDriveLetter)를 참조하세요.

### <a name="osdpreservedriveletter"></a>OSDPreserveDriveLetter

 > [!Important]
 > 이 작업 순서 변수는 사용되지 않습니다. 
 >
 > 기본적으로 OS 배포 시 Windows 설치 프로그램이 사용하기에 가장 적합한 드라이브 문자(일반적으로 C:)를 결정합니다. 

 ‘이전 동작’은 이미지를 적용할 때 OSDPreverveDriveLetter 변수가 작업 순서에서 이미지 파일(.WIM)에 캡처된 드라이브 문자를 사용할지 결정하는 것이었습니다. 이 변수 값을 `false`로 설정하여 **운영 체제 적용** 작업 순서 단계의 **대상** 설정에 지정한 위치를 사용할 수 있습니다. 자세한 내용은 [OS 이미지 적용](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage)을 참조하세요.



## <a name="see-also"></a>참고 항목

- [작업 순서 단계](/sccm/osd/understand/task-sequence-steps)
- [Using task sequence variables](/sccm/osd/understand/using-task-sequence-variables)\(작업 순서 변수 사용\)
- [작업 자동화에 대한 계획 고려 사항](/sccm/osd/plan-design/planning-considerations-for-automating-tasks)
