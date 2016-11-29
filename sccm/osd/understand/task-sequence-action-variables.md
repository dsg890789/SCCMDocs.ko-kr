---
title: "작업 순서 동작 변수 | Configuration Manager"
description: "네트워크 설정 변수 등의 순서 동작 변수를 사용하여 Configuration Manager 작업 순서의 단일 단계에 대한 구성 설정을 지정할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2269031-0977-4f01-a274-420e00630575
caps.latest.revision: 10
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: cd0e74bff29110f5483c7132ba989d9933e7e223


---
# <a name="task-sequence-action-variables-in-system-center-configuration-manager"></a>System Center Configuration Manager의 작업 순서 동작 변수

*적용 대상: System Center Configuration Manager(현재 분기)*

작업 순서 동작 변수는 System Center Configuration Manager 작업 순서의 단일 단계에서 사용되는 구성 설정을 지정합니다. 기본적으로 작업 순서 단계에서 사용되는 설정은 단계가 실행되기 전에 초기화되고 연결된 작업 순서 단계가 실행되는 동안에만 사용할 수 있습니다. 즉, 작업 순서 변수 설정은 작업 순서 단계가 실행되기 전에 작업 순서 환경에 추가되고, 작업 순서 단계가 실행된 다음 작업 순서 환경에서 값이 제거됩니다.  

## <a name="action-variable-example"></a>작업 변수 예제  
 예를 들어 **명령줄 실행** 작업 순서 단계를 사용하여 명령줄 작업에 대한 시작 디렉터리를 지정할 수 있습니다. 이 단계는 기본값이 **WorkingDirectory** 변수로 작업 순서 환경에 저장된 **시작 위치** 속성을 포함합니다. **WorkingDirectory** 환경 변수는 **명령줄 실행** 작업 순서 동작이 실행되기 전에 초기화됩니다. **명령줄 실행** 단계에서 **시작** 속성을 통해 **WorkingDirectory** 값에 액세스할 수 있습니다. 그런 다음 작업 순서 단계가 완료되면 **WorkingDirectory** 변수의 값이 작업 순서 환경에서 제거됩니다. 순서에 다른 **명령줄 실행** 작업 순서 단계가 포함된 경우 새 **WorkingDirectory** 변수가 초기화되고 해당 작업 순서 단계에 대한 시작 값으로 설정됩니다.  

 작업 순서 단계가 실행되는 동안 작업 순서 동작 설정에 대한 기본값이 있지만 설정하는 새 값을 순서의 여러 단계에서 사용할 수 있습니다. 작업 순서 변수 만들기 방법 중 하나를 사용하여 기본 제공 변수 값을 재정의하는 경우 새 값이 환경에서 유지되고 작업 순서의 다른 단계에 대한 기본값을 재정의합니다. 이전 예제에서 **작업 순서 변수 설정** 단계가 작업 순서의 첫 번째 단계로 추가되고 **WorkingDirectory** 환경 변수를 **C:\\** 값으로 설정하는 경우 작업 순서의 두 **명령줄 실행** 단계에서 모두 새 시작 디렉터리 값을 사용합니다.  

## <a name="action-variables-for-task-sequence-actions"></a>작업 순서 동작에 대한 작업 변수  
 Configuration Manager 작업 순서 변수는 해당 변수에 연결된 작업 순서 동작별로 그룹화됩니다. 다음 링크를 사용하여 특정 작업과 연결된 작업 변수에 대한 정보를 수집합니다. 작업 순서 변수가 작업 순서 동작의 작동 방법을 제어합니다. 작업 순서 동작은 사용자가 입력 변수로 표시한 변수를 읽고 사용합니다. 또는 사용자가 작업 순서 변수 설정 동작이나 TSEnvironment COM 개체를 사용하여 런타임에 변수를 설정할 수 있습니다. 작업 순서 동작만 변수를 출력 변수로 표시하며, 이러한 변수는 작업 순서의 나중에 발생하는 동작에서 읽힙니다.  

> [!NOTE]  
>  일부 작업 순서 동작은 작업 순서 변수 집합에 연결되어 있지 않습니다. 예를 들어 BitLocker 사용 작업과 연결된 변수가 있지만 BitLocker 사용 안 함 작업과 연결된 변수는 없습니다.  

###  <a name="a-namebkmkapplydataimagea-apply-data-image-task-sequence-action-variables"></a><a name="BKMK_ApplyDataImage"></a> 데이터 이미지 적용 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터에 적용되는 WIM 파일의 이미지 및 대상 파티션에서 파일을 삭제할지 여부를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [데이터 이미지 적용 작업 순서 단계](task-sequence-steps.md#BKMK_ApplyDataImage)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDDataImageIndex<br /><br /> (입력)|대상 컴퓨터에 적용되는 이미지의 인덱스 값을 지정합니다.|  
|OSDWipeDestinationPartition<br /><br /> (입력)|대상 파티션에 있는 파일을 삭제할지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  

###  <a name="a-namebkmkapplydriverpackagea-apply-driver-package-task-sequence-action-variables"></a><a name="BKMK_ApplyDriverPackage"></a> 드라이버 패키지 적용 작업 순서 동작 변수  
 이 동작에 대한 변수는 대용량 저장소 드라이버의 설치에 대한 정보 및 서명되지 않은 드라이버를 설치할지 여부를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [드라이버 패키지 적용](task-sequence-steps.md#BKMK_ApplyDriverPackage)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDApplyDriverBootCriticalContentUniqueID<br /><br /> (입력)|드라이버 패키지에서 설치할 대용량 저장 장치 드라이버의 콘텐츠 ID를 지정합니다. 지정하지 않으면 대용량 저장소 드라이버가 설치되지 않습니다.|  
|OSDApplyDriverBootCriticalINFFile<br /><br /> (입력)|설치할 대용량 저장소 드라이버의 INF 파일을 지정합니다.<br /><br /> <br /><br /> OSDApplyDriverBootCriticalContentUniqueID가 설정된 경우 이 작업 순서 변수가 필요합니다.|  
|OSDApplyDriverBootCriticalHardwareComponent<br /><br /> (입력)|대용량 저장 장치 드라이버가 설치되었는지 여부를 지정하며 **scsi**여야 합니다.<br /><br /> <br /><br /> OSDApplyDriverBootCriticalContentUniqueID가 설정된 경우 이 작업 순서 변수가 필요합니다.|  
|OSDApplyDriverBootCriticalID<br /><br /> (입력)|설치할 대용량 저장 장치 드라이버의 부팅 필요 ID를 지정합니다. 이 ID는 장치 드라이버의 txtsetup.oem 파일의 "**scsi**" 섹션에 나열되어 있습니다.<br /><br /> <br /><br /> OSDApplyDriverBootCriticalContentUniqueID가 설정된 경우 이 작업 순서 변수가 필요합니다.|  
|OSDAllowUnsignedDriver<br /><br /> (입력)|Windows가 서명되지 않은 장치 드라이버를 설치할 수 있도록 구성할지 여부를 지정합니다. Windows Vista 이상 운영 체제를 배포하는 경우에는 이 작업 순서 변수가 사용되지 않습니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  

###  <a name="a-namebkmkapplynetworksettingsa-apply-network-settings-task-sequence-action-variables"></a><a name="BKMK_ApplyNetworkSettings"></a> 네트워크 설정 적용 작업 순서 동작 변수  
 이 동작에 대한 변수는 컴퓨터의 네트워크 어댑터에 대한 설정, 도메인 설정 및 작업 그룹 설정과 같은 대상 컴퓨터에 대한 네트워크 설정을 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [네트워크 설정 적용 단계](task-sequence-steps.md#BKMK_ApplyNetworkSettings)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDAdapter<br /><br /> (입력)|이 작업 순서 변수는 배열 변수입니다. 배열의 각 요소는 컴퓨터에서 단일 네트워크 어댑터에 대한 설정을 나타냅니다. 각 어댑터에 대해 정의된 설정은 배열 변수 이름과 0부터 시작하는 네트워크 어댑터 인덱스 및 속성 이름을 결합하여 액세스할 수 있습니다.<br /><br /> <br /><br /> 여러 네트워크 어댑터가 이 작업 순서 동작으로 구성될 경우 두 번째 네트워크에 대한 속성이 변수 이름의 해당 인덱스를 사용하여 정의됩니다. 예를 들어 OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList, OSDAdapter1DNSDomain, OSDAdapter1WINSServerList, OSDAdapter1EnableWINS 등입니다.<br /><br /> <br /><br /> 예를 들어 다음 변수 이름을 사용하여 이 작업 순서 동작에 의해 구성될 첫 번째 네트워크 어댑터의 속성을 정의할 수 있습니다.<br /><br /> <ul><li>**OSDAdapter0EnableDHCP** – 어댑터에 대해 DHCP(Dynamic Host Configuration Protocol)를 사용하려면 true로 설정합니다.<br />    이 설정은 필수입니다. 사용 가능한 값은 True 또는 False입니다.</li><li>**OSDAdapter0IPAddressList** – 쉼표로 구분된 어댑터에 대한 IP 주소 목록입니다. **EnableDHCP** 가 **false**로 설정되지 않으면 이 속성은 무시됩니다.<br />    이 설정은 필수입니다.</li><li>**OSDAdapter0SubnetMask** – 쉼표로 구분된 서브넷 마스크 목록입니다. **EnableDHCP** 가 **false**로 설정되지 않으면 이 속성은 무시됩니다.<br />    이 설정은 필수입니다.</li><li>**OSDAdapter0Gateways** – 쉼표로 구분된 IP 게이트웨이 주소 목록입니다. **EnableDHCP** 가 **false**로 설정되지 않으면 이 속성은 무시됩니다.<br />    이 설정은 필수입니다.</li><li>**OSDAdapter0DNSDomain** - 어댑터에 대한 DNS(Domain Name System) 도메인입니다.</li><li>**OSDAdapter0DNSServerList** – 쉼표로 구분된 어댑터에 대한 DNS 서버 목록입니다.<br />    이 설정은 필수입니다.</li><li>**OSDAdapter0EnableDNSRegistration** - DNS에 어댑터에 대한 IP 주소를 등록하려면 **true**로 설정합니다.</li><li>**OSDAdapter0EnableFullDNSRegistration** - DNS에 컴퓨터의 전체 DNS 이름 아래 어댑터에 대한 IP 주소를 등록하려면 **true**로 설정합니다.</li><li>**OSDAdapter0EnableIPProtocolFiltering** - 어댑터에서 IP 프로토콜 필터링을 사용하려면 **true**로 설정합니다.</li><li>**OSDAdapter0IPProtocolFilterList** – IP를 통해 실행할 수 있는 쉼표로 구분된 프로토콜 목록입니다. **EnableIPProtocolFiltering** 이 **false**로 설정된 경우 이 속성은 무시됩니다.</li><li>**OSDAdapter0EnableTCPFiltering** - 어댑터에 대해 TCP 포트 필터링을 사용하려면 **true**로 설정합니다.</li><li>**OSDAdapter0TCPFilterPortList** – TCP에 대해 액세스 권한을 부여할 쉼표로 구분된 포트 목록입니다. **EnableTCPFiltering** 이 **false**로 설정된 경우 이 속성은 무시됩니다.</li><li>**OSDAdapter0TcpipNetbiosOptions** – NetBIOS over TCP/IP에 대한 옵션입니다. 가능한 값은 다음과 같습니다.<br /><br /> <ul><li>0은 DHCP 서버에서 NetBIOS 설정을 사용합니다.</li><li>1은 NetBIOS over TCP/IP를 사용하도록 설정합니다.</li><li>2는 NetBIOS over TCP/IP를 사용하지 않도록 설정합니다.</li></ul></li><li>**OSDAdapter0EnableWINS** - 이름 확인에 WINS를 사용하려면 **true**로 설정합니다.</li><li>**OSDAdapter0WINSServerList** – 쉼표로 구분된 WINS 서버 IP 주소 목록입니다. **EnableWINS** 가 **true**로 설정되지 않으면 이 속성은 무시됩니다.</li><li>**OSDAdapter0MacAddress** – 설정을 실제 네트워크 어댑터에 연결하기 위해 사용되는 MAC(미디어 액세스 컨트롤러) 주소입니다.</li><li>**OSDAdapter0Name** – 네트워크 연결 제어판 프로그램에 표시되는 네트워크 연결의 이름입니다. 이름은 0에서 255자 사이입니다.</li><li>**OSDAdapter0Index** - 설정의 배열에서 네트워크 어댑터 설정의 인덱스입니다.<br /><br />     OSDAdapterCount=1<br />    OSDAdapter0EnableDHCP=FALSE<br />    OSDAdapter0IPAddressList=192.168.0.40<br />    OSDAdapter0SubnetMask=255.255.255.0<br />    OSDAdapter0Gateways=192.168.0.1<br />    OSDAdapter0DNSSuffix=contoso.com</li></ul>|  
|OSDAdapterCount<br /><br /> (입력)|대상 컴퓨터에 설치된 네트워크 어댑터의 수를 지정합니다. **OSDAdapterCount** 값이 설정된 경우 각 어댑터의 모든 구성 옵션이 설정되어야 합니다. 예를 들어 특정 어댑터에 대해 **OSDAdapterTCPIPNetbiosOptions** 값을 설정하면 해당 어댑터에 대한 모든 값도 구성되어야 합니다.<br /><br /> <br /><br /> 이 값을 지정하지 않으면 모든 **OSDAdapter** 값이 무시됩니다.|  
|OSDDNSDomain<br /><br /> (입력)|대상 컴퓨터에서 사용하는 기본 DNS 서버를 지정합니다.|  
|OSDDomainName<br /><br /> (입력)|대상 컴퓨터가 가입하는 Windows 도메인의 이름을 지정합니다. 지정된 값은 유효한 Active Directory Domain Services 도메인 이름이어야 합니다.|  
|OSDDomainOUName<br /><br /> (입력)|대상 컴퓨터가 가입하는 OU(조직 구성 단위)의 RFC 1779 형식 이름을 지정합니다. 지정하는 경우 값에 전체 경로가 포함되어야 합니다.<br /><br /> 예:<br /><br /> **LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com**|  
|OSDEnableTCPIPFiltering<br /><br /> (입력)|TCP/IP 필터링이 사용되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDJoinAccount<br /><br /> (입력)|Windows 도메인에 대상 컴퓨터를 추가하는 데 사용되는 네트워크 계정을 지정합니다.|  
|OSDJoinPassword<br /><br /> (입력)|Windows 도메인에 대상 컴퓨터를 추가하는 데 사용되는 네트워크 암호를 지정합니다.|  
|OSDNetworkJoinType<br /><br /> (입력)|대상 컴퓨터가 Windows 도메인 또는 작업 그룹에 가입하는지 여부를 지정합니다.<br /><br /> **"0"** 은 대상 컴퓨터가 Windows 도메인에 가입한다는 것을 나타냅니다. **"1"** 은 컴퓨터가 작업 그룹에 가입한다는 것을 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"0"**<br /><br /> **"1"**|  
|OSDDNSSuffixSearchOrder<br /><br /> (입력)|대상 컴퓨터에 대한 DNS 검색 순서를 지정합니다.|  
|OSDWorkgroupName<br /><br /> (입력)|대상 컴퓨터가 가입하는 작업 그룹의 이름을 지정합니다.<br /><br /> 이 값 또는 **OSDDomainName** 값 중 하나를 지정해야 합니다. 작업 그룹 이름은 최대 32자까지 가능합니다.<br /><br /> 예:<br /><br /> **"Accounting"**|  

###  <a name="a-namebkmkapplyoperatingsystema-apply-operating-system-image-task-sequence-action-variables"></a><a name="BKMK_ApplyOperatingSystem"></a> 운영 체제 이미지 적용 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터에 설치할 운영 체제에 대한 설정을 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [운영 체제 이미지 적용](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDConfigFileName<br /><br /> (입력)|운영 체제 배포 패키지와 관련된 운영 체제 배포 응답 파일의 파일 이름을 지정합니다.|  
|OSDImageIndex<br /><br /> (입력)|대상 컴퓨터에 적용된 WIM 파일의 이미지 인덱스 값을 지정합니다.|  
|OSDInstallEditionIndex<br /><br /> (입력)|설치되는 Windows Vista 또는 운영 체제의 버전을 지정합니다. 버전이 지정되지 않으면 Windows 설치 프로그램에서 참조된 제품 키를 사용하여 설치할 버전을 결정합니다.<br /><br /> 다음 조건에 해당하는 경우 영(0) 값만 사용합니다.<br /><br /> - Windows Vista 이전 운영 체제를 설치하고 있습니다.<br />- Windows Vista 이상의 볼륨 라이선스 버전을 설치하고 있고 제품 키를 지정하지 않았습니다.<br /><br /> 유효한 값은<br /><br /> **"0"** (기본값)|  
|OSDTargetSystemDrive(출력)|운영 체제 파일이 포함된 파티션의 드라이브 문자를 지정합니다.|  

###  <a name="a-namebkmkapplywindowssettingsa-apply-windows-settings-task-sequence-action-variables"></a><a name="BKMK_ApplyWindowsSettings"></a> Windows 설정 적용 작업 순서 동작 변수  
 이 동작에 대한 변수는 컴퓨터 이름, Windows 제품 키, 등록된 사용자 및 조직, 로컬 관리자 암호와 같은 대상 컴퓨터에 대한 Windows 설정을 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [Windows 설정 적용](task-sequence-steps.md#BKMK_ApplyWindowsSettings)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDComputerName<br /><br /> (입력)|대상 컴퓨터의 이름을 지정합니다.<br /><br /> 예:<br /><br /> **"%_SMSTSMachineName%"** (기본값)|  
|OSDProductKey<br /><br /> (입력)|Windows 제품 키를 지정합니다. 지정된 값은 1-255자 사이여야 합니다.|  
|OSDRegisteredUserName<br /><br /> (입력)|새 운영 체제에서 등록된 기본 사용자 이름을 지정합니다. 지정된 값은 1-255자 사이여야 합니다.|  
|OSDRegisteredOrgName<br /><br /> (입력)|새 운영 체제에서 등록된 기본 조직 이름을 지정합니다. 지정된 값은 1-255자 사이여야 합니다.|  
|OSDTimeZone<br /><br /> (입력)|새 운영 체제에서 사용되는 기본 표준 시간대 설정을 지정합니다.|  
|OSDServerLicenseMode<br /><br /> (입력)|사용되는 Windows Server 라이선스 모드를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"PerSeat"**<br /><br /> **"PerServer"**|  
|OSDServerLicenseConnectionLimit<br /><br /> (입력)|허용되는 최대 연결 수를 지정합니다. 지정된 숫자는 5에서 9999개 연결 사이의 범위에 있어야 합니다.|  
|OSDRandomAdminPassword<br /><br /> (입력)|새 운영 체제에서 관리자 계정에 대해 임의로 생성된 암호를 지정합니다. **true**로 설정되면 대상 컴퓨터에서 로컬 관리자 계정이 사용되지 않도록 설정됩니다. **false**로 설정되면 대상 컴퓨터에서 로컬 관리자 계정이 사용되도록 설정되고 로컬 관리자 계정 암호에 **OSDLocalAdminPassword** 변수의 값이 할당됩니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  
|OSDLocalAdminPassword<br /><br /> (입력)|로컬 관리자 암호를 지정합니다. **로컬 관리자 암호를 임의로 생성하고 지원되는 모든 플랫폼에서 계정 사용 안 함** 옵션이 사용되도록 설정된 경우 이 값은 무시됩니다. 지정된 값은 1-255자 사이여야 합니다.|  

###  <a name="a-namebkmkautoapplydriversa-auto-apply-drivers-task-sequence-action-variables"></a><a name="BKMK_AutoApplyDrivers"></a> 드라이버 자동 적용 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터에 설치되는 Windows 드라이버 및 서명되지 않은 드라이버가 설치되는지 여부를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [드라이버 자동 적용](task-sequence-steps.md#BKMK_AutoApplyDrivers)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDAutoApplyDriverCategoryList<br /><br /> (입력)|쉼표로 구분된 드라이버 카탈로그 범주의 고유한 ID 목록입니다. 지정된 경우 **드라이버 자동 적용** 작업 순서 동작에서 드라이버를 설치할 때 이러한 범주 중 적어도 하나에 속한 드라이버만 고려합니다. 이 값은 선택 사항이므로 기본적으로 설정되어 있지 않습니다. 사용 가능한 범주 ID는 사이트에서 **SMS_CategoryInstance** 개체 목록을 열거하여 가져올 수 있습니다.|  
|OSDAllowUnsignedDriver<br /><br /> (입력)|서명되지 않은 장치 드라이버를 설치할 수 있도록 Windows를 구성할지 여부를 지정합니다. Windows Vista 이상 운영 체제를 배포하는 경우에는 이 작업 순서 변수가 사용되지 않습니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDAutoApplyDriverBestMatch<br /><br /> (입력)|하드웨어 장치와 호환되는 드라이버 카탈로그의 여러 장치 드라이버가 있는 경우 작업 순서 동작이 수행하는 작업을 지정합니다. **"true"**로 설정된 경우 가장 적합한 장치 드라이버만 설치됩니다.  **false**인 경우 호환되는 모든 장치 드라이버가 설치되고 운영 체제가 가장 사용하기 적합한 드라이버를 선택합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  

###  <a name="a-namebkmkcapturenetworksettingsa-capture-network-settings-task-sequence-action-variables"></a><a name="BKMK_CaptureNetworkSettings"></a> 네트워크 설정 캡처 작업 순서 동작 변수  
 이 동작에 대한 변수는 네트워크 어댑터 설정(TCP/IP, DNS 및 WINS) 구성 정보가 캡처되는지 여부 및 작업 그룹 또는 도메인 멤버 자격 정보가 운영 체제 배포 중에 마이그레이션되는지 여부를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [네트워크 설정 캡처](task-sequence-steps.md#BKMK_CaptureNetworkSettings)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDMigrateAdapterSettings<br /><br /> (입력)|네트워크 어댑터 설정(TCP/IP, DNS 및 WINS) 구성 정보가 캡처되는지 여부를 지정합니다.<br /><br /> 예:<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  
|OSDMigrateNetworkMembership<br /><br /> (입력)|작업 그룹 또는 도메인 멤버 자격 정보가 운영 체제 배포 중에 마이그레이션되는지 여부를 지정합니다.<br /><br /> 예:<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  

###  <a name="a-namebkmkcaptureoperatingsystemimagea-capture-operating-system-image-task-sequence-action-variables"></a><a name="BKMK_CaptureOperatingSystemImage"></a> 운영 체제 이미지 캡처 작업 순서 동작 변수  
 이 동작에 대한 변수는 이미지가 저장되는 위치, 이미지를 만든 사람 및 이미지에 대한 설명과 같이 캡처되는 운영 체제 이미지에 대한 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [운영 체제 이미지 캡처](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDCaptureAccount<br /><br /> (입력)|네트워크 공유에서 캡처된 이미지를 저장할 권한이 있는 Windows 계정 이름을 지정합니다.|  
|OSDCaptureAccountPassword<br /><br /> (입력)|네트워크 공유에서 캡처된 이미지를 저장하는 데 사용되는 Windows 계정에 대한 암호를 지정합니다.|  
|OSDCaptureDestination<br /><br /> (입력)|캡처된 운영 체제 이미지가 저장되는 위치를 지정합니다. 디렉터리 이름은 최대 255자까지 가능합니다.|  
|OSDImageCreator<br /><br /> (입력)|이미지를 만든 사용자의 선택적 이름입니다. 이 이름은 WIM 파일에 저장됩니다. 사용자 이름은 최대 255자까지 가능합니다.|  
|OSDImageDescription<br /><br /> (입력)|캡처된 운영 체제 이미지에 대한 선택적 사용자 정의 설명입니다. 이 설명은 WIM 파일에 저장됩니다. 설명은 최대 255자까지 가능합니다.|  
|OSDImageVersion<br /><br /> (입력)|캡처된 운영 체제 이미지에 할당할 선택적 사용자 정의 버전 번호입니다. 이 버전 번호는 WIM 파일에 저장됩니다. 이 값은 최대 32자의 문자 조합일 수 있습니다.|  
|OSDTargetSystemRoot<br /><br /> (입력)|참조 컴퓨터에 설치된 운영 체제의 Windows 디렉터리 경로를 지정합니다. 이 운영 체제는 Configuration Manager에서 캡처를 위해 지원되는 운영 체제로 확인됩니다.|  

###  <a name="a-namebkmkcaptureuserstatea-capture-user-state-task-sequence-action-variables"></a><a name="BKMK_CaptureUserState"></a> 사용자 상태 캡처 작업 순서 동작 변수  
 이 동작에 대한 변수는 사용자 상태가 저장되는 폴더, USMT에 대한 명령줄 옵션, 사용자 프로필의 캡처를 제어하는 데 사용되는 구성 파일과 같이 USMT(사용자 환경 마이그레이션 도구)에서 사용되는 정보를 지정합니다.  이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [사용자 상태 캡처](task-sequence-steps.md#BKMK_CaptureUserState)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (입력)|사용자 상태가 저장되는 폴더의 로컬 경로 이름 또는 UNC입니다. 기본값이 없습니다.|  
|OSDMigrateAdditionalCaptureOptions<br /><br /> (입력)|사용자 상태를 캡처할 때 사용되지만 Configuration Manager 사용자 인터페이스에는 노출되지 않는 USMT(사용자 환경 마이그레이션 도구) 명령줄 옵션을 지정합니다. 추가 옵션은 자동으로 생성된 USMT 명령줄에 추가된 문자열 형식으로 지정됩니다.<br /><br /> <br /><br /> 작업 순서를 실행하기 전에 이 작업 순서 변수를 사용하여 지정된 USMT 옵션이 정확성에 대한 유효성이 검사되지 않았습니다.|  
|OSDMigrateMode<br /><br /> (입력)|USMT에서 캡처되는 파일을 사용자 지정할 수 있습니다. 이 변수가 "Simple"로 설정된 경우 표준 USMT 구성 파일만 사용됩니다. 이 변수가 "Advanced"로 설정된 경우 작업 순서 변수 OSDMigrateConfigFiles에서 USMT가 사용하는 구성 파일을 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"Simple"**<br /><br /> **"Advanced"**|  
|OSDMigrateConfigFiles<br /><br /> (입력)|사용자 프로필의 캡처를 제어하기 위해 사용되는 구성 파일을 지정합니다. 이 변수는 OSDMigrateMode가 "Advanced"로 설정된 경우에만 사용됩니다. 이 쉼표로 구분된 목록 값은 사용자 지정된 사용자 프로필 마이그레이션을 수행하기 위해 설정됩니다.<br /><br /> 예: miguser.xml,migsys.xml,migapps.xml|  
|OSDMigrateContinueOnLockedFiles<br /><br /> (입력)|일부 파일을 캡처할 수 없는 경우 계속하려면 사용자 상태 캡처를 허용합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (입력)|USMT에 대해 자세한 정보 로깅을 사용합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDMigrateSkipEncryptedFiles<br /><br /> (입력)|암호화된 파일이 캡처되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|_OSDMigrateUsmtPackageID<br /><br /> (입력)|USMT 파일을 포함할 Configuration Manager 패키지의 패키지 ID를 지정합니다. 이 변수가 필요합니다.|  

###  <a name="a-namebkmkcapturewindowssettingsa-capture-windows-settings-task-sequence-action-variables"></a><a name="BKMK_CaptureWindowsSettings"></a> Windows 설정 캡처 작업 순서 동작 변수  
 이 동작에 대한 변수는 컴퓨터의 이름, 등록 조직 이름 및 표준 시간대 정보와 같이 특정 Windows 설정이 대상 컴퓨터로 마이그레이션되는지 여부를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [Windows 설정 캡처](task-sequence-steps.md#BKMK_CaptureWindowsSettings)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDMigrateComputerName<br /><br /> (입력)|컴퓨터 이름이 마이그레이션되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**<br /><br /> 값이 "true"이면 OSDComputerName 변수가 컴퓨터의 NetBIOS 이름으로 설정됩니다.|  
|OSDComputerName<br /><br /> (출력)|컴퓨터의 NetBIOS 이름으로 설정합니다. OSDMigrateComputerName 변수가 "true"로 설정된 경우에만 이 값이 설정됩니다.|  
|OSDMigrateRegistrationInfo<br /><br /> (입력)|컴퓨터 사용자 및 조직 정보가 마이그레이션되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**<br /><br /> 값이 "true"이면 OSDRegisteredOrgName 변수가 컴퓨터의 등록된 조직 이름으로 설정됩니다.|  
|OSDRegisteredOrgName<br /><br /> (출력)|컴퓨터의 등록된 조직 이름으로 설정됩니다. OSDMigrateRegistrationInfo 변수가 "true"로 설정된 경우에만 이 값이 설정됩니다.|  
|OSDMigrateTimeZone<br /><br /> (입력)|컴퓨터의 표준 시간대가 마이그레이션되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**<br /><br /> 값이 "true"이면 변수 OSDTimeZone이 컴퓨터의 표준 시간대로 설정됩니다.|  
|OSDTimeZone<br /><br /> (출력)|컴퓨터의 표준 시간대로 설정됩니다. OSDMigrateTimeZone 변수가 "true"로 설정된 경우에만 이 값이 설정됩니다.|  

###  <a name="a-namebkmkconnecttonetworkfoldera-connect-to-network-folder-task-sequence-action-variables"></a><a name="BKMK_ConnecttoNetworkFolder"></a> 네트워크 폴더에 연결 작업 순서 동작 변수  
 이 동작에 대한 변수는 사용되는 계정 및 네트워크 폴더에 연결할 암호, 폴더의 드라이브 문자 및 폴더에 대한 경로와 같이 네트워크의 폴더에 대한 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [네트워크 폴더에 연결](task-sequence-steps.md#BKMK_ConnectToNetworkFolder)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|SMSConnectNetworkFolderAccount<br /><br /> (입력)|네트워크 공유에 연결하는 데 사용되는 관리자 계정을 지정합니다.|  
|SMSConnectNetworkFolderDriveLetter<br /><br /> (입력)|연결할 네트워크 드라이브 문자를 지정합니다. 이 값은 선택 사항입니다. 지정하지 않으면 네트워크 연결이 드라이브 문자에 매핑되지 않습니다. 이 값을 지정하는 경우 D:에서 Z: 범위에 있는 값이어야 합니다.  또한 X:는 Windows PE 단계 중 Windows PE에서 사용하는 드라이브 문자이므로 사용하지 마세요.<br /><br /> 예:<br /><br /> **"D:"**<br /><br /> **"E:"**|  
|SMSConnectNetworkFolderPassword<br /><br /> (입력)|네트워크 공유에 연결하는 데 사용되는 네트워크 암호를 지정합니다.|  
|SMSConnectNetworkFolderPath<br /><br /> (입력)|연결에 대한 네트워크 경로를 지정합니다.<br /><br /> 예제:<br /><br /> **"\\\servername\sharename"**|  

###  <a name="a-namebkmkconvertdiska-convert-disk-to-dynamic-task-sequence-action-variables"></a><a name="BKMK_ConvertDisk"></a> 동적 디스크로 변환 작업 순서 동작 변수  
 이 동작에 대한 변수는 기본에서 동적 디스크로 변환할 실제 디스크의 수를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [동적 디스크로 변환](task-sequence-steps.md#BKMK_ConvertDisktoDynamic)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDConvertDiskIndex<br /><br /> (입력)|변환되는 실제 디스크 번호를 지정합니다.|  

###  <a name="a-namebkmkenablebitlockera-enable-bitlocker-task-sequence-action-variables"></a><a name="BKMK_EnableBitLocker"></a> BitLocker 사용 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터에서 BitLocker를 사용하도록 설정하기 위해 사용되는 복구 암호 및 시작 키 옵션을 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [BitLocker 사용](task-sequence-steps.md#BKMK_EnableBitLocker)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDBitLockerRecoveryPassword<br /><br /> (입력)|임의 복구 암호를 생성하는 대신 **BitLocker 사용** 작업 순서 동작은 지정된 값을 복구 암호로 사용합니다. 값은 유효한 숫자 BitLocker 복구 암호여야 합니다.|  
|OSDBitLockerStartupKey<br /><br /> (입력)|키 관리 옵션인 **USB의 시작 키만**에 대해 임의 시작 키를 생성하는 대신 **BitLocker 사용** 작업 순서 동작은 TPM(신뢰할 수 있는 플랫폼 모듈)을 시작 키로 사용합니다. 값은 유효한 256비트 Base64로 인코딩된 BitLocker 시작 키여야 합니다.|  

###  <a name="a-namebkmkformatpartitiondiska-format-and-partition-disk-task-sequence-action-variables"></a><a name="BKMK_FormatPartitionDisk"></a> 디스크 포맷 및 파티션 만들기 작업 순서 동작 변수  
 이 동작에 대한 변수는 디스크 번호 및 파티션 설정의 배열과 같이 실제 디스크의 포맷 및 분할에 대한 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [디스크 포맷 및 파티션 만들기](task-sequence-steps.md#BKMK_FormatandPartitionDisk)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDDiskIndex<br /><br /> (입력)|분할할 실제 디스크 번호를 지정합니다.|  
|OSDDiskpartBiosCompatibilityMode<br /><br /> (입력)|특정 유형의 BIOS와의 호환성을 위해 하드 디스크를 분할할 때 캐시 정렬 최적화를 사용하지 않을지 여부를 지정합니다. 이 설정은 Windows XP 또는 Windows Server 2003 운영 체제를 배포할 때 필요할 수 있습니다. 자세한 내용은 Microsoft 기술 자료의 [문서 931760](http://go.microsoft.com/fwlink/?LinkId=134081) 및 [문서 931761](http://go.microsoft.com/fwlink/?LinkId=134082) 을 참조하세요.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDGPTBootDisk<br /><br /> (입력)|EFI 기반 컴퓨터의 시작 디스크로 사용할 수 있도록 GPT 하드 디스크에서 EFI 파티션을 만들지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDPartitions<br /><br /> (입력)|파티션 설정의 배열을 지정합니다. 작업 순서 환경에서 배열 변수에 액세스하려면 SDK 항목을 참조하세요.<br /><br /> 이 작업 순서 변수는 배열 변수입니다. 배열의 각 요소는 하드 디스크에서 단일 파티션에 대한 설정을 나타냅니다. 각 파티션에 대해 정의된 설정은 배열 변수 이름과 0부터 시작하는 디스크 파티션 번호 및 속성 이름을 결합하여 액세스할 수 있습니다.<br /><br /> 예를 들어 다음 변수 이름을 사용하여 이 작업 순서 동작으로 하드 디스크에 만들어질 첫 번째 파티션에 대한 속성을 정의할 수 있습니다.<br /><br /> - **OSDPartitions0Type** - 파티션 유형을 지정합니다. 필수 속성입니다. 유효한 값은 "**Primary**", "**Extended**", "**Logical**" 및 "**Hidden**"입니다.<br />-   **OSDPartitions0FileSystem** - 파티션을 포맷할 때 사용할 파일 시스템의 유형을 지정합니다. 선택적 속성입니다. 파일 시스템이 지정되지 않으면 파티션이 포맷되지 않습니다. 유효한 값은 "**FAT32**" 및 "**NTFS**"입니다.<br />-   **OSDPartitions0Bootable** - 파티션이 부팅 가능한지 여부를 지정합니다. 필수 속성입니다. 이 값이 MBR 디스크에 대해 "**TRUE**"로 설정되면 활성 파티션이 됩니다.<br />-   **OSDPartitions0QuickFormat** - 사용되는 포맷 유형을 지정합니다. 필수 속성입니다. 이 값이 "**TRUE**"로 설정되면 빠른 포맷이 수행되고 그렇지 않으면 전체 포맷이 수행됩니다.<br />-   **OSDPartitions0VolumeName** - 포맷될 때 볼륨에 할당되는 이름을 지정합니다. 이는 선택적 속성입니다.<br />-   **OSDPartitions0Size** - 파티션의 크기를 지정합니다. 단위는 **OSDPartitions0SizeUnits** 변수로 지정됩니다. 이는 선택적 속성입니다. 이 속성이 지정되지 않은 경우 남아 있는 모든 사용 가능한 공간을 사용하여 파티션이 만들어집니다.<br />-   **OSDPartitions0SizeUnits** - **OSDPartitions0Size** 작업 순서 변수를 해석할 때 사용될 단위를 지정합니다. 이는 선택적 속성입니다. 유효한 값은 "**MB**"(기본값), "**GB**" 및 "**Percent**"입니다.<br />-   **OSDPartitions0VolumeLetterVariable** - 파티션이 만들어질 때 Windows PE에서 항상 사용 가능한 다음 드라이브 문자를 사용합니다. 이 선택적 속성을 사용하여 나중에 참조하기 위해 새 드라이브 문자를 저장하는 데 사용할 다른 작업 순서 변수의 이름을 지정합니다.<br /><br /> <br /><br /> 이 작업 순서 동작으로 여러 파티션이 정의될 경우 두 번째 파티션에 대한 속성은 변수 이름의 해당 인덱스를 사용하여 정의할 수 있습니다. 예를 들어 **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat**, **OSDPartitions1VolumeName** 등입니다.|  
|OSDPartitionStyle<br /><br /> (입력)|디스크를 분할하는 경우 사용할 파티션 스타일을 지정합니다. "**MBR**"은 마스터 부팅 레코드 파티션 스타일을 나타내고 "**GPT**"는 GUID 파티션 테이블 스타일을 나타냅니다.<br /><br /> 유효한 값은<br /><br /> **"GPT"**<br /><br /> **"MBR"**|  

###  <a name="a-namebkmkinstallsoftwareupdatesa-install-software-updates-task-sequence-action-variables"></a><a name="BKMK_InstallSoftwareUpdates"></a> 소프트웨어 업데이트 설치 작업 순서 동작 변수  
 이 동작에 대한 변수는 모든 업데이트를 설치할지 아니면 필수 업데이트만 설치할지 여부를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [소프트웨어 업데이트 설치](task-sequence-steps.md#BKMK_InstallSoftwareUpdates)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름<br /><br /> (입력)|설명|  
|----------------------------------------|-----------------|  
|SMSInstallUpdateTarget<br /><br /> (입력)|모든 업데이트를 설치할지 아니면 필수 업데이트만 설치할지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"모두"**<br /><br /> **"필수"**|  

###  <a name="a-namebkmkjoindomainworkgroupa-join-domain-or-workgroup-task-sequence-action-variables"></a><a name="BKMK_JoinDomainWorkgroup"></a> 도메인 또는 작업 그룹 가입 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터를 Windows 도메인 또는 작업 그룹에 가입하기 위해 필요한 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [도메인 또는 작업 그룹 가입](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDJoinAccount<br /><br /> (입력)|Windows 도메인에 가입하기 위해 대상 컴퓨터에서 사용되는 계정을 지정합니다. 도메인에 가입하는 경우 이 변수가 필요합니다.|  
|OSDJoinDomainName<br /><br /> (입력)|대상 컴퓨터가 가입하는 Windows 도메인의 이름을 지정합니다. Windows 도메인 이름의 길이는 1-255자 사이여야 합니다.|  
|OSDJoinDomainOUName<br /><br /> (입력)|대상 컴퓨터가 가입하는 OU(조직 구성 단위)의 RFC 1779 형식 이름을 지정합니다. 지정하는 경우 값에 전체 경로가 포함되어야 합니다. Windows 도메인 OU 이름의 길이는 0에서 32,767자 사이여야 합니다. **OSDJoinType** 변수가 "1"(작업 그룹에 가입)로 설정되면 이 값이 설정되지 않습니다.<br /><br /> 예:<br /><br /> **LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com**|  
|OSDJoinPassword<br /><br /> (입력)|Windows 도메인에 가입하기 위해 대상 컴퓨터에서 사용되는 네트워크 암호를 지정합니다. 변수를 지정하지 않으면 빈 암호가 시도됩니다. **OSDJoinType** 변수가 "**0**"(도메인에 가입)으로 설정된 경우 이 값이 필요합니다.|  
|OSDJoinSkipReboot<br /><br /> (입력)|대상 컴퓨터가 도메인 또는 작업 그룹에 가입한 후 다시 시작하기를 건너뛸지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"**|  
|OSDJoinType<br /><br /> (입력)|대상 컴퓨터가 Windows 도메인 또는 작업 그룹에 가입하는지 여부를 지정합니다. 대상 컴퓨터를 Windows 도메인에 가입하려면 "**0**"을 지정합니다. 대상 컴퓨터를 작업 그룹에 가입하려면 "**1**"을 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"0"**<br /><br /> **"1"**|  
|OSDJoinWorkgroupName<br /><br /> (입력)|대상 컴퓨터가 가입하는 작업 그룹의 이름을 지정합니다. 작업 그룹 이름은 1-32자 사이여야 합니다.<br /><br /> 예:<br /><br /> **"Accounting"**|  

###  <a name="a-namebkmkpreparewindowscapturea-prepare-windows-for-capture-task-sequence-action-variables"></a><a name="BKMK_PrepareWindowsCapture"></a> Windows 캡처 준비 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터에서 Windows 운영 체제를 캡처하는 데 사용되는 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [ConfigMgr 클라이언트 캡처 준비](task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDBuildStorageDriverList<br /><br /> (입력)|Sysprep이 대용량 저장 장치 드라이버 목록을 작성하는지 여부를 지정합니다. 이 설정은 Windows XP 및 Windows Server 2003에만 적용됩니다. sysprep.inf의 [SysprepMassStorage] 섹션을 캡처할 이미지에서 지원하는 모든 대용량 저장소 드라이버의 정보로 채웁니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDKeepActivation<br /><br /> (입력)|Sysprep이 제품 활성화 플래그를 다시 설정하는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDTargetSystemRoot<br /><br /> (출력)|참조 컴퓨터에 설치된 운영 체제의 Windows 디렉터리 경로를 지정합니다. 이 운영 체제는 Configuration Manager에서 캡처를 위해 지원되는 운영 체제로 확인됩니다.|  

###  <a name="a-namebkmkreleasestatestorea-release-state-store-sequence-action-variables"></a><a name="BKMK_ReleaseStateStore"></a> 상태 저장소 해제 순서 동작 변수  
 이 동작에 대한 변수는 저장된 사용자 상태를 해제하는 데 사용되는 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [상태 저장소 해제](task-sequence-steps.md#BKMK_ReleaseStateStore)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (입력)|사용자 상태가 복원되는 위치의 로컬 경로 이름 또는 UNC입니다. 이 값은 **사용자 상태 캡처** 작업 순서 동작 및 **사용자 상태 복원** 작업 순서 동작 둘 다에서 사용됩니다.|  

###  <a name="a-namebkmkrequeststatea-request-state-store-task-sequence-action-variables"></a><a name="BKMK_RequestState"></a> 상태 저장소 요청 작업 순서 동작 변수  
 이 동작에 대한 변수는 사용자 데이터가 저장되는 상태 마이그레이션 지점에 있는 폴더와 같이 저장된 사용자 상태를 요청하는 데 사용되는 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [상태 저장소 해제](../../osd/understand/task-sequence-steps.md#BKMK_ReleaseStateStore)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDStateFallbackToNAA<br /><br /> (입력)|컴퓨터 계정이 상태 마이그레이션 지점에 연결되지 못하는 경우 네트워크 액세스 계정이 대체 계정으로 사용되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDStateSMPRetryCount<br /><br /> (입력)|이 단계가 실패하기 전에 작업 순서 단계가 상태 마이그레이션 지점을 찾으려고 시도하는 횟수를 지정합니다. 지정된 횟수는 0에서 600 사이여야 합니다.|  
|OSDStateSMPRetryTime<br /><br /> (입력)|작업 순서 단계가 다시 시도하기 전에 대기할 시간(초)을 지정합니다. 시간(초)은 최대 30자까지 가능합니다.|  
|OSDStateStorePath<br /><br /> (출력)|사용자 상태가 저장되는 상태 마이그레이션 지점의 폴더에 대한 UNC 경로입니다.|  

###  <a name="a-namebkmkrestartcomputera-restart-computer-task-sequence-action-variables"></a><a name="BKMK_RestartComputer"></a> 컴퓨터 다시 시작 작업 순서 동작 변수  
 이 동작에 대한 변수는 대상 컴퓨터를 다시 시작하는 데 사용되는 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [컴퓨터 다시 시작](task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|SMSRebootMessage<br /><br /> (입력)|대상 컴퓨터를 다시 시작하기 전에 사용자에게 표시할 메시지를 지정합니다. 이 변수가 설정되지 않은 경우 기본 메시지 텍스트가 표시됩니다. 지정된 메시지는 512자를 초과할 수 없습니다.<br /><br /> 예제:<br /><br /> - "이 컴퓨터가 다시 시작됩니다. 작업을 저장하세요."|  
|SMSRebootTimeout<br /><br /> (입력)|컴퓨터가 다시 시작하기 전에 경고가 사용자에게 표시되는 시간(초)을 지정합니다. 다시 부팅 메시지를 표시하지 않으려면 0초를 지정합니다.<br /><br /> 예:<br /><br /> **"0"** (기본값)<br /><br /> **"5"**<br /><br /> **"10"**|  

###  <a name="a-namebkmkrestoreuserstatea-restore-user-state-task-sequence-action-variables"></a><a name="BKMK_RestoreUserState"></a> 사용자 상태 복원 작업 순서 동작 변수  
 이 동작에 대한 변수는 사용자 상태가 복원되는 폴더의 경로 이름 및 로컬 컴퓨터 계정이 복원되는지 여부와 같은 대상 컴퓨터의 사용자 상태를 복원하는 데 사용되는 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [사용자 상태 복원](task-sequence-steps.md#BKMK_RestoreUserState)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (입력)|사용자 상태가 복원되는 폴더의 로컬 경로 이름 또는 UNC입니다.|  
|OSDMigrateContinueOnRestore<br /><br /> (입력)|일부 파일을 복원할 수 없는 경우에도 사용자 상태 복원이 계속되도록 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"** (기본값)<br /><br /> **"false"**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (입력)|USMT 도구에 대해 자세한 정보 로깅을 사용합니다. 이 값은 동작에서 필요하며 "true" 또는 "false"로 설정되어야 합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDMigrateLocalAccounts<br /><br /> (입력)|로컬 컴퓨터 계정이 복원되는지 여부를 지정합니다.<br /><br /> 유효한 값은<br /><br /> **"true"**<br /><br /> **"false"** (기본값)|  
|OSDMigrateLocalAccountPassword<br /><br /> (입력)|**OSDMigrateLocalAccounts** 변수가 "true"인 경우 이 변수는 마이그레이션되는 모든 로컬 계정에 할당되는 암호를 포함해야 합니다. 동일한 암호가 마이그레이션된 모든 로컬 계정에 할당되었기 때문에 Configuration Manager 운영 체제 배포가 아닌 일부 방법으로 나중에 변경되는 임시 암호로 간주됩니다.|  
|OSDMigrateAdditionalRestoreOptions<br /><br /> (입력)|사용자 상태를 복원할 때 사용되는 추가 USMT(사용자 환경 마이그레이션 도구) 명령줄 옵션을 지정합니다. 추가 옵션은 자동으로 생성된 USMT 명령줄에 추가된 문자열 형식으로 지정됩니다. 작업 순서를 실행하기 전에 이 작업 순서 변수를 사용하여 지정된 USMT 옵션이 정확성에 대한 유효성이 검사되지 않았습니다.|  
|_OSDMigrateUsmtRestorePackageID<br /><br /> (입력)|USMT 파일을 포함할 Configuration Manager 패키지의 패키지 ID를 지정합니다. 이 변수가 필요합니다.|  

###  <a name="a-namebkmkruncommanda-run-command-line-task-sequence-action-variables"></a><a name="BKMK_RunCommand"></a> 명령줄 실행 작업 순서 동작 변수  
 이 동작에 대한 변수는 명령이 실행되는 작업 디렉터리와 같이 명령줄에서 명령을 실행하는 데 사용되는 정보를 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [명령줄 실행](task-sequence-steps.md#BKMK_RunCommandLine)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름|설명|  
|--------------------------|-----------------|  
|SMSTSDisableWow64Redirection<br /><br /> (입력)|기본적으로 64비트 운영 체제에서 실행하는 경우 운영 체제 프로그램과 DLL의 32비트 버전을 찾을 수 있도록 WOW64 파일 시스템 리디렉터를 사용하여 명령줄의 프로그램을 찾아서 실행합니다. 이 변수를 "true"로 설정하면 WOW64 파일 시스템 리디렉터가 사용하지 않도록 설정되므로 운영 체제 프로그램과 DLL의 네이티브 64비트 버전을 찾을 수 있습니다. 이 변수는 32비트 운영 체제에서 실행할 때는 아무런 영향이 없습니다.|  
|시작 위치<br /><br /> (입력)|명령줄 동작에 대한 시작 디렉터리를 지정합니다. 지정된 디렉터리 이름은 255자를 초과할 수 없습니다.<br /><br /> 예제:<br /><br /> -   **"C:\\"**<br />-   **"%SystemRoot%"**|  
|SMSTSRunCommandLineUserName<br /><br /> (입력)|명령줄을 실행할 계정을 지정합니다. 값은 양식 사용자 이름 또는 도메인\사용자 이름의 문자열입니다.|  
|SMSTSRunCommandLinePassword<br /><br /> (입력)|SMSTSRunCommandLineUserName 변수에서 지정한 계정의 암호를 지정합니다.|  

### <a name="set-dynamic-variables"></a>동적 변수 설정  
 이 작업에 대한 변수는 동적 변수 설정 작업 순서 단계를 추가하면 자동으로 설정됩니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [동적 변수 설정](task-sequence-steps.md#BKMK_SetDynamicVariables)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름<br /><br /> (입력)|설명|  
|----------------------------------------|-----------------|  
|_SMSTSMake|컴퓨터의 제조업체를 지정합니다.|  
|_SMSTSModel|컴퓨터의 모델을 지정합니다.|  
|_SMSTSMacAddresses|컴퓨터에 사용되는 MAC 주소를 지정합니다.|  
|_SMSTSIPAddresses|컴퓨터에 사용되는 IP 주소를 지정합니다.|  
|_SMSTSSerialNumber|컴퓨터의 일련 번호를 지정합니다.|  
|_SMSTSAssetTag|컴퓨터에 대한 자산 태그를 지정합니다.|  
|_SMSTSUUID|컴퓨터의 UUID를 지정합니다.|  
|_SMSTSDefaultGateways|컴퓨터에 사용되는 기본 게이트웨이를 지정합니다.|  

###  <a name="a-namebkmksetupwindowsa-setup-windows-and-configmgr-task-sequence-action-variables"></a><a name="BKMK_SetupWindows"></a> Windows 및 ConfigMgr 설정 작업 순서 동작 변수  
 이 동작에 대한 변수는 Configuration Manager 클라이언트를 설치할 때 사용되는 클라이언트 설치 속성을 지정합니다. 이러한 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [Windows 및 ConfigMgr 설정](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr)을 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름<br /><br /> (입력)|설명|  
|----------------------------------------|-----------------|  
|SMSClientInstallProperties<br /><br /> (입력)|Configuration Manager 클라이언트를 설치할 때 사용되는 클라이언트 설치 속성을 지정합니다.|  

### <a name="upgrade-operating-system"></a>운영 체제 업그레이드  
 이 동작에 대한 변수는 Windows 10 업그레이드를 위한 설치 프로그램에 추가된 Configuration Manager 콘솔에서 사용할 수 없는 추가 명령줄 옵션을 지정합니다. 이 변수와 관련된 작업 순서 단계에 대한 자세한 내용은 [운영 체제 업그레이드](task-sequence-steps.md#BKMK_UpgradeOS)를 참조하세요.  

#### <a name="details"></a>세부 정보  

|작업 변수 이름<br /><br /> (입력)|설명|  
|----------------------------------------|-----------------|  
|OSDSetupAdditionalUpgradeOptions<br /><br /> (입력)|Windows 10 업그레이드 중 설치 프로그램에 추가된 추가 명령줄 옵션을 지정합니다. 명령줄 옵션은 확인되지 않습니다. 따라서 입력하는 옵션이 정확한지 확인합니다.<br /><br /> 자세한 내용은 [Windows 설치 프로그램 명령줄 옵션](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx)을 참조하세요.|  



<!--HONumber=Nov16_HO1-->


