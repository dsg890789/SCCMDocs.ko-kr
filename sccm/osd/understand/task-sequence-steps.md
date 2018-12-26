---
title: 작업 순서 단계
titleSuffix: Configuration Manager
description: Configuration Manager 작업 순서에 추가할 수 있는 단계를 알아봅니다.
ms.date: 08/17/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 7c888a6f-8e37-4be5-8edb-832b218f266d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bec95b13ecba5ae5238d758ae06566042a95d939
ms.sourcegitcommit: 303d826f45c8fd9a05d8883afc1ca645e56bd576
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269249"
---
# <a name="task-sequence-steps-in-configuration-manager"></a>Configuration Manager의 작업 순서 단계

 *적용 대상: System Center Configuration Manager(현재 분기)*

 Configuration Manager 작업 순서에 추가할 수 있는 작업 순서 단계는 다음과 같습니다. 작업 순서를 편집하는 방법에 대한 자세한 내용은 [작업 순서 편집](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_ModifyTaskSequence)을 참조하세요.  

 다음 설정은 모든 작업 순서 단계에 공통적으로 적용됩니다.

#### <a name="properties-tab"></a>속성 탭
 - **이름**: 작업 순서 편집기에서 이 단계를 설명하는 짧은 이름을 지정해야 합니다. 새 단계를 추가하면 작업 순서 편집기에서 기본적으로 이 이름을 [형식]으로 설정합니다. **이름**의 길이는 50자를 초과할 수 없습니다.  

 - **설명**: 필요에 따라 이 단계에 대한 자세한 정보를 지정합니다. **설명**의 길이는 256자를 초과할 수 없습니다.  


 이 문서의 나머지 부분에서는 각 작업 순서 단계에 대한 **속성** 탭의 다른 설정에 대해 설명합니다.

#### <a name="options-tab"></a>옵션 탭  

 - **이 단계 사용 안 함**: 작업 순서가 컴퓨터에서 실행되면 이 단계를 건너뜁니다. 작업 순서 편집기에서 이 단계의 아이콘은 회색으로 표시됩니다.  

 - **오류 발생 시 계속**: 단계를 실행하는 동안 오류가 발생하더라도 작업 순서가 계속됩니다. 자세한 내용은 [작업 자동화에 대한 계획 고려 사항](/sccm/osd/plan-design/planning-considerations-for-automating-tasks#BKMK_TSGroups)을 참조하세요.   

 - **조건 추가**: 작업 순서에서 이러한 조건부 명령문을 평가하여 단계가 실행되는지 확인합니다. 작업 순서 변수를 조건으로 사용하는 예를 알려면 [How to use task sequence variables](/sccm/osd/understand/using-task-sequence-variables#bkmk_access-condition)(작업 순서 변수 사용 방법)를 참조하세요.   


 특정 작업 순서 단계에 대한 아래 섹션에서는 **옵션** 탭의 다른 가능한 설정에 대해 설명합니다.



##  <a name="BKMK_ApplyDataImage"></a> 데이터 이미지 적용   

 이 단계를 사용하여 데이터 이미지를 지정된 대상 파티션에 복사합니다.  

 이 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다. 

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDDataImageIndex](/sccm/osd/understand/task-sequence-variables#OSDDataImageIndex)  
 - [OSDWipeDestinationPartition](/sccm/osd/understand/task-sequence-variables#OSDWipeDestinationPartition)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **데이터 이미지 적용**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="image-package"></a>이미지 패키지  
 **찾아보기**를 클릭하여 이 작업 순서에서 사용되는 **이미지 패키지**를 지정합니다. **패키지 선택** 대화 상자에서 설치할 패키지를 선택합니다. 각 기존 이미지 패키지에 대한 관련 속성 정보는 대화 상자의 아래쪽에 표시됩니다. 드롭다운 목록을 사용하여 선택한 **이미지 패키지** 에서 설치할 **이미지**를 선택합니다.  

 > [!NOTE]  
 >  이 작업 순서 동작은 이미지를 데이터 파일로 처리합니다. 이 동작은 이미지를 OS로 부팅하도록 설정하지 않습니다.  

#### <a name="destination"></a>대상  
 다음 옵션 중 하나를 구성합니다.

 - **사용 가능한 다음 파티션**: 이 작업 순서의 **운영 체제 적용** 또는 **데이터 이미지 적용** 단계가 아직 대상으로 지정하지 않은 다음 순차 파티션을 사용합니다.  

 - **특정 디스크 및 파티션**: **디스크** 번호(0부터 시작) 및 **파티션** 번호(1부터 시작)를 선택합니다.  

 - **특정 논리적 드라이브 문자**: Windows PE에서 파티션에 할당하는 **드라이브 문자**를 지정합니다. 이 드라이브 문자는 새로 배포된 OS에서 할당한 드라이브 문자와 다를 수 있습니다.  

 - **변수에 저장된 논리적 드라이브 문자**: Windows PE에서 파티션에 할당한 드라이브 문자를 포함하는 작업 순서 변수를 지정합니다. 이 변수는 일반적으로 **디스크 포맷 및 파티션 만들기** 작업 순서 단계에 대한 **파티션 속성** 대화 상자의 [고급] 섹션에서 설정됩니다.  

#### <a name="delete-all-content-on-the-partition-before-applying-the-image"></a>이미지를 적용하기 전에 파티션의 모든 내용 삭제  
 이미지를 설치하기 전에 작업 순서에서 대상 파티션의 모든 파일을 삭제하도록 지정합니다. 파티션의 내용을 삭제하지 않고 이 동작을 사용하여 이전에 대상으로 지정된 파티션에 추가 내용을 적용할 수 있습니다.  



##  <a name="BKMK_ApplyDriverPackage"></a> 드라이버 패키지 적용  

 이 단계를 사용하여 드라이버 패키지의 모든 드라이버를 다운로드하고 Windows OS에 설치합니다.

 **드라이버 패키지 적용** 작업 순서 단계를 수행하면 드라이버 패키지의 모든 장치 드라이버를 Windows에서 사용할 수 있습니다. **운영 체제 적용** 단계와 **Windows 및 ConfigMgr 설치** 단계 사이에 이 단계를 추가하여 패키지의 드라이버를 Windows에서 사용할 수 있게 합니다. 일반적으로 **드라이버 패키지 적용** 단계는 **드라이버 자동 적용** 작업 순서 단계 뒤에 배치됩니다. **드라이버 패키지 적용** 작업 순서 단계는 독립 실행형 미디어 배포 시나리오에도 유용합니다.  

 유사한 디바이스 드라이버들을 드라이버 패키지에 넣고 이를 적절한 배포 지점에 배포합니다. 예를 들어 한 제조업체의 모든 드라이버를 드라이버 패키지에 넣습니다. 그런 다음 연결된 컴퓨터에서 액세스할 수 있는 배포 지점에 패키지를 배포합니다.

 **드라이버 패키지 적용** 단계는 독립 실행형 미디어에 유용합니다. 이 단계는 특정 드라이버 집합을 설치하는 데에도 유용합니다. 이러한 유형의 드라이버에는 네트워크 프린터와 같이 Windows 플러그 앤 플레이에서 검색되지 않는 디바이스가 포함됩니다.  

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다. 

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDApplyDriverBootCriticalContentUniqueID](/sccm/osd/understand/task-sequence-variables#OSDApplyDriverBootCriticalContentUniqueID)  
 - [OSDApplyDriverBootCriticalHardwareComponent](/sccm/osd/understand/task-sequence-variables#OSDApplyDriverBootCriticalHardwareComponent)  
 - [OSDApplyDriverBootCriticalID](/sccm/osd/understand/task-sequence-variables#OSDApplyDriverBootCriticalID)  
 - [OSDApplyDriverBootCriticalINFFile](/sccm/osd/understand/task-sequence-variables#OSDApplyDriverBootCriticalINFFile)  
 - [OSDInstallDriversAdditionalOptions](/sccm/osd/understand/task-sequence-variables#OSDInstallDriversAdditionalOptions)<!--516679/2840016-->(버전 1806부터 적용)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **드라이버**를 선택한 다음, **드라이버 패키지 적용**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="driver-package"></a>드라이버 패키지
 필요한 디바이스 드라이버가 포함된 드라이버 패키지를 지정합니다. **찾아보기**를 클릭하여 **패키지 선택** 대화 상자를 시작합니다. 적용할 기존 드라이버 패키지를 선택합니다. 대화 상자 아래쪽에 관련 패키지 속성이 표시됩니다.  

#### <a name="select-the-mass-storage-driver-within-the-package-that-needs-to-be-installed-before-setup-on-pre-windows-vista-operating-systems"></a>패키지 내에서 Windows Vista 이전 운영 체제에 설치하기 전에 설치해야 하는 대용량 저장소 드라이버 선택
 클래식 OS를 설치하는 데 필요한 대용량 저장 장치 드라이버를 지정합니다.  

#### <a name="driver"></a>드라이버
 클래식 OS를 설치하기 전에 설치할 대용량 저장 장치 드라이버 파일을 선택합니다. 지정된 패키지에서 드롭다운 목록이 채워집니다.  

#### <a name="model"></a>모델  
 Windows Vista 이전 OS 배포에 필요한 부팅 필수 디바이스를 지정합니다.  

#### <a name="do-unattended-installation-of-unsigned-drivers-on-version-of-windows-where-this-is-allowed"></a>허용되는 Windows 버전에서 서명되지 않은 드라이버 자동 설치
 이 옵션을 사용하면 Windows에서 디지털 서명이 없는 드라이버를 설치할 수 있습니다.  



##  <a name="BKMK_ApplyNetworkSettings"></a> 네트워크 설정 적용   

 이 단계를 사용하여 대상 컴퓨터에 대한 네트워크 또는 작업 그룹 구성 정보를 지정합니다. 작업 순서는 이러한 값을 적절한 응답 파일에 저장합니다. 이 응답 파일은 Windows 설치 프로그램에서 **Windows 및 ConfigMgr 설치** 동작 중에 사용합니다.  

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다. 

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDAdapter](/sccm/osd/understand/task-sequence-variables#OSDAdapter)  
 - [OSDAdapterCount](/sccm/osd/understand/task-sequence-variables#OSDAdapterCount)  
 - [OSDDNSDomain](/sccm/osd/understand/task-sequence-variables#OSDDNSDomain)  
 - [OSDDNSSuffixSearchOrder](/sccm/osd/understand/task-sequence-variables#OSDDNSSuffixSearchOrder)  
 - [OSDDomainName](/sccm/osd/understand/task-sequence-variables#OSDDomainName)  
 - [OSDDomainOUName](/sccm/osd/understand/task-sequence-variables#OSDDomainOUName)  
 - [OSDEnableTCPIPFiltering](/sccm/osd/understand/task-sequence-variables#OSDEnableTCPIPFiltering)  
 - [OSDJoinAccount](/sccm/osd/understand/task-sequence-variables#OSDJoinAccount)  
 - [OSDJoinPassword](/sccm/osd/understand/task-sequence-variables#OSDJoinPassword)  
 - [OSDWorkgroupName](/sccm/osd/understand/task-sequence-variables#OSDWorkgroupName)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **설정**을 선택한 다음, **네트워크 설정 적용**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="join-a-workgroup"></a>작업 그룹에 가입
 대상 컴퓨터를 지정된 작업 그룹에 가입시키려면 이 옵션을 선택합니다. **작업 그룹** 행에 작업 그룹의 이름을 입력합니다. **네트워크 설정 캡처** 작업 순서 단계에서 캡처하는 값이 이 값을 재정의할 수 있습니다. 

#### <a name="join-a-domain"></a>도메인에 가입
 대상 컴퓨터를 지정된 도메인에 가입시키려면 이 옵션을 선택합니다. `fabricam.com`과 같은 도메인을 지정하거나 찾아봅니다. 조직 구성 단위에 대한 LDAP(Lightweight Directory Access Protocol) 경로를 지정하거나 찾습니다. 예: `LDAP//OU=computers, DC=Fabricam.com, C=com`.  

#### <a name="account"></a>계정
 **설정** 을 클릭하여 컴퓨터를 도메인에 가입시키는 데 필요한 권한이 있는 계정을 지정합니다. **Windows 사용자 계정** 대화 상자에서 사용자 이름을 `Domain\User` 형식으로 입력합니다. 자세한 내용은 [도메인 가입 계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-editor-domain-joining-account)을 참조하세요. 

#### <a name="adapter-settings"></a>어댑터 설정  
 컴퓨터에 있는 각 네트워크 어댑터에 대한 네트워크 구성을 지정합니다. **새로 만들기** 를 클릭하여 **네트워크 설정** 대화 상자를 열고 네트워크 설정을 지정합니다. 
 - **네트워크 설정 캡처** 단계도 사용하는 경우 작업 순서는 이전에 캡처한 설정을 네트워크 어댑터에 적용합니다. 
 - 작업 순서가 이전에 네트워크 설정을 캡처하지 않은 경우 작업 순서는 이 단계에서 사용자가 지정하는 설정을 적용합니다. 
 - 작업 순서는 이러한 설정을 Windows 디바이스 열거 순서의 네트워크 어댑터에 적용합니다.  
 - 작업 순서는 이 단계에서 지정하는 설정을 컴퓨터에 즉시 적용하지 않습니다. 



##  <a name="BKMK_ApplyOperatingSystemImage"></a> 운영 체제 이미지 적용  

 > [!TIP]  
 > Windows 10 버전 1709부터 미디어에는 여러 버전이 포함되어 있습니다. OS 업그레이드 패키지 또는 OS 이미지를 사용하도록 작업 순서를 구성하는 경우 [지원되는 버전](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)을 선택해야 합니다.  

 이 단계를 사용하여 대상 컴퓨터에 OS를 설치합니다. 

 > [!NOTE]  
 >  **Windows 및 ConfigMgr 설치** 단계에서 Windows 설치를 시작 합니다. 

 **운영 체제 적용** 동작이 실행되면 **OSDTargetSystemDrive** 변수가 OS 파일이 포함된 파티션의 드라이브 문자로 설정됩니다.  

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다. 

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDConfigFileName](/sccm/osd/understand/task-sequence-variables#OSDConfigFileName)  
 - [OSDImageIndex](/sccm/osd/understand/task-sequence-variables#OSDImageIndex)  
 - [OSDTargetSystemDrive](/sccm/osd/understand/task-sequence-variables#OSDTargetSystemDrive)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **운영 체제 이미지 적용**을 선택합니다. 

 이 단계는 OS 이미지 또는 OS 업그레이드 패키지를 사용하는지 여부에 따라 작업을 수행합니다.  

#### <a name="os-image-actions"></a>OS 이미지 작업
 OS 이미지를 사용하는 경우 **운영 체제 이미지 적용** 단계에서 수행하는 작업은 다음과 같습니다.  

 1.  **\_SMSTSUserStatePath** 변수로 지정한 폴더의 파일을 제외하고 대상 볼륨의 모든 콘텐츠를 삭제합니다.  

 2.  지정한 대상 파티션에 지정된 .wim 파일의 콘텐츠를 추출합니다.  

 3.  응답 파일을 준비합니다.  

    1.  배포된 OS에 대한 새 기본 Windows 설치 응답 파일(sysprep.inf 또는 unattend.xml)을 만듭니다.  

    2.  사용자가 제공한 응답 파일의 모든 값을 병합합니다.  

 4.  Windows 부팅 로더를 활성 파티션에 복사합니다.  

 5.  새로 설치된 OS를 참조하도록 boot.ini 또는 BCD(부팅 구성 데이터베이스)를 설정합니다.  

#### <a name="os-upgrade-package-actions"></a>OS 업그레이드 패키지 작업
 OS 업그레이드 패키지를 사용하는 경우 **운영 체제 이미지 적용** 단계에서 수행하는 작업은 다음과 같습니다.  

 1.  **\_SMSTSUserStatePath** 변수로 지정한 폴더의 파일을 제외하고 대상 볼륨의 모든 콘텐츠를 삭제합니다.  

 2.  응답 파일을 준비합니다.  

    1.  Configuration Manager에서 만든 표준 값으로 새 응답 파일을 만듭니다.  

    2.  사용자가 제공한 응답 파일의 모든 값을 병합합니다.  


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="apply-operating-system-from-a-captured-image"></a>캡처된 이미지에서 운영 체제를 적용합니다.
 캡처한 OS 이미지를 설치합니다. **찾아보기**를 클릭하여 **패키지 선택** 대화 상자를 엽니다. 그런 다음 설치하려는 기존 이미지 패키지를 선택합니다. 지정된 **이미지 패키지**에 여러 이미지가 연결되어 있는 경우, 드롭다운 목록에서 이 배포에 사용할 연결된 이미지를 선택합니다. 이미지를 클릭하여 각 기존 이미지에 대한 기본 정보를 볼 수 있습니다.  

#### <a name="apply-operating-system-image-from-an-original-installation-source"></a>원래 설치 원본에서 운영 체제 이미지 적용
 원래 설치 원본이기도 한 OS 업그레이드 패키지를 사용하여 OS를 설치합니다. **찾아보기**를 클릭하여 **운영 체제 설치 패키지 선택** 대화 상자를 엽니다. 그런 다음 사용하려는 기존 OS 업그레이드 패키지를 선택합니다. 이미지를 클릭하여 각 기존 이미지 원본에 대한 기본 정보를 볼 수 있습니다. 대화 상자 아래쪽의 결과 창에 관련 이미지 원본 속성이 표시됩니다. 지정된 패키지와 연결된 버전이 여러 개 있는 경우 드롭다운 목록을 사용하여 사용할 **버전**을 선택합니다.  

#### <a name="use-an-unattended-or-sysprep-answer-file-for-a-custom-installation"></a>자동 또는 Sysprep 응답 파일을 사용하여 사용자 지정 설치
 이 옵션을 사용하여 OS 버전 및 설치 방법에 따라 Windows 설치 응답 파일(**unattend.xml**, **unattend.txt**또는 **sysprep.inf**)을 제공할 수 있습니다. 지정한 파일은 Windows 응답 파일에서 지원하는 표준 구성 옵션 중 하나를 포함할 수 있습니다. 예를 들어 기본 Internet Explorer 홈 페이지를 지정할 수 있습니다. 응답 파일이 포함된 패키지 및 패키지의 파일에 대한 연결된 경로를 지정합니다.  

 > [!NOTE]  
 >  제공한 Windows 설치 응답 파일은 `%varname%`(여기서 *varname*은 변수의 이름) 형식의 포함된 작업 순서 변수를 포함할 수 있습니다. **Windows 및 ConfigMgr 설치** 단계는 실제 변수 값을 변수 문자열로 대체합니다. 이러한 포함된 작업 순서 변수는 unattend.xml 응답 파일의 숫자 전용 필드에 사용할 수 없습니다.  

 Windows 설치 응답 파일을 제공하지 않으면 작업 순서에서 응답 파일이 자동으로 생성됩니다.  

#### <a name="destination"></a>대상  
 다음 옵션 중 하나를 구성합니다.  

 - **사용 가능한 다음 파티션**: 이 작업 순서의 **운영 체제 적용** 또는 **데이터 이미지 적용** 단계가 아직 대상으로 지정하지 않은 다음 순차 파티션을 사용합니다.  

 - **특정 디스크 및 파티션**: **디스크** 번호(0부터 시작) 및 **파티션** 번호(1부터 시작)를 선택합니다.  

 - **특정 논리적 드라이브 문자**: Windows PE에서 파티션에 할당한 **드라이브 문자**를 지정합니다. 이 드라이브 문자는 새로 배포된 OS에서 할당한 드라이브 문자와 다를 수 있습니다.  

 - **변수에 저장된 논리적 드라이브 문자**: Windows PE에서 파티션에 할당한 드라이브 문자가 포함된 작업 순서 변수를 지정합니다. 이 변수는 일반적으로 **디스크 포맷 및 파티션 만들기** 작업 순서 단계에 대한 **파티션 속성** 대화 상자의 [고급] 섹션에서 설정됩니다.  


### <a name="options"></a>Options  

 기본 옵션 외에도, 이 작업 순서 단계의 **옵션** 탭에서 다음과 같은 추가 설정을 구성합니다.  

#### <a name="access-content-directly-from-the-distribution-point"></a>배포 지점에서 직접 콘텐츠 액세스
 배포 지점에서 OS 이미지에 직접 액세스하도록 작업 순서를 구성합니다. 예를 들어 운영 체제를 저장소 용량이 제한된 포함된 디바이스에 배포할 때 이 옵션을 사용합니다. 이 옵션을 선택하는 경우 OS 이미지 속성의 **데이터 액세스** 탭에서 패키지 공유 설정도 구성합니다.  

 > [!NOTE]  
 >  이 설정은 **소프트웨어 배포 마법사**의 **배포 지점** 페이지에서 구성한 배포 옵션을 재정의합니다. 이 재정의는 이 단계에서 지정한 OS 이미지에만 적용되며, 모든 작업 순서 콘텐츠에는 적용되지 않습니다.  



##  <a name="BKMK_ApplyWindowsSettings"></a> Windows 설정 적용  

 이 단계를 사용하여 대상 컴퓨터에 대한 Windows 설정을 구성합니다. 작업 순서는 이러한 값을 적절한 응답 파일에 저장합니다. 이 응답 파일은 Windows 설치 프로그램에서 **Windows 및 ConfigMgr 설치** 단계 중에 사용합니다.  

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDComputerName](/sccm/osd/understand/task-sequence-variables#OSDComputerName-input)  
 - [OSDLocalAdminPassword](/sccm/osd/understand/task-sequence-variables#OSDLocalAdminPassword)  
 - [OSDProductKey](/sccm/osd/understand/task-sequence-variables#OSDProductKey)  
 - [OSDRandomAdminPassword](/sccm/osd/understand/task-sequence-variables#OSDRandomAdminPassword)  
 - [OSDRegisteredOrgName](/sccm/osd/understand/task-sequence-variables#OSDRegisteredOrgName-input)  
 - [OSDRegisteredUserName](/sccm/osd/understand/task-sequence-variables#OSDRegisteredUserName)  
 - [OSDServerLicenseConnectionLimit](/sccm/osd/understand/task-sequence-variables#OSDServerLicenseConnectionLimit)  
 - [OSDServerLicenseMode](/sccm/osd/understand/task-sequence-variables#OSDServerLicenseMode)  
 - [OSDTimeZone](/sccm/osd/understand/task-sequence-variables#OSDTimeZone-input)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **설정**을 선택한 다음, **Windows 설정 적용**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="user-name"></a>사용자 이름
 대상 컴퓨터와 연결할 등록된 사용자 이름을 지정합니다. **Windows 설정 캡처** 작업 순서 단계에서 캡처하는 값이 이 값을 재정의할 수 있습니다.  

#### <a name="organization-name"></a>조직 이름
 대상 컴퓨터와 연결할 등록된 조직 이름을 지정합니다. **Windows 설정 캡처** 작업 순서 단계에서 캡처하는 값이 이 값을 재정의할 수 있습니다.  

#### <a name="product-key"></a>제품 키  
 대상 컴퓨터에서 Windows 설치에 사용할 제품 키를 지정합니다.  

#### <a name="server-licensing"></a>서버 라이선싱  
 서버 라이선싱 모드를 지정합니다. 
 - **서버 단위** 또는 **사용자 단위**를 라이선스 모드로 선택합니다.  
 - **서버 단위**를 선택하는 경우 사용권 계약에 따라 허용되는 최대 연결 수도 지정합니다.  
 - 대상 컴퓨터가 서버가 아니거나 라이선싱 모드를 지정하지 않으려면 **지정 안 함**을 선택합니다.   

#### <a name="maximum-connections"></a>최대 연결 수
 사용권 계약에 명시된 대로 이 컴퓨터에 사용할 수 있는 최대 연결 수를 지정합니다.  

#### <a name="randomly-generate-the-local-administrator-password-and-disable-the-account-on-all-supported-platforms-recommended"></a>로컬 관리자 암호를 임의로 생성하고 지원되는 모든 플랫폼에서 계정 사용 안 함(권장)  
 로컬 관리자 암호를 임의로 생성된 문자열로 설정하려면 이 옵션을 선택합니다. 또한 이 옵션은 이 기능을 지원하는 플랫폼에서 로컬 관리자 계정을 사용하지 않도록 설정합니다.  

#### <a name="enable-the-account-and-specify-the-local-administrator-password"></a>계정을 사용하고 로컬 관리자 암호 지정  
 지정된 암호를 사용하여 로컬 관리자 계정을 사용하도록 설정하려면 이 옵션을 선택합니다. **암호** 행에 암호를 입력하고 **암호 확인** 행에 암호를 확인합니다.  

#### <a name="time-zone"></a>표준 시간대
 대상 컴퓨터에서 구성할 표준 시간대를 지정합니다. **Windows 설정 캡처** 작업 순서 단계에서 캡처하는 값이 이 값을 재정의할 수 있습니다.  



##  <a name="BKMK_AutoApplyDrivers"></a> 드라이버 자동 적용  

 이 단계를 사용하여 OS 배포의 일부로 드라이버를 일치시키고 설치합니다.  

 **드라이버 자동 적용** 작업 순서 단계는 다음 동작을 수행합니다.  

 1. 하드웨어를 검사하고 시스템에 있는 모든 디바이스에 대한 플러그 앤 플레이 ID를 찾습니다.  

 2. 디바이스 목록과 해당 플러그 앤 플레이 ID를 관리 지점으로 보냅니다. 관리 지점에서는 각 하드웨어 디바이스의 드라이버 카탈로그에서 호환되는 드라이버 목록을 반환합니다. 목록에는 포함하는 드라이버 패키지와 지정된 드라이버 범주로 태그가 지정된 드라이버에 관계없이 사용하도록 설정된 모든 드라이버가 포함됩니다.  

 3. 작업 순서는 각 하드웨어 디바이스에 가장 적합한 드라이버를 선택합니다. 이 드라이버는 배포된 OS에 적합하며, 액세스할 수 있는 배포 지점에 있습니다.  

 4. 작업 순서는 선택한 드라이버를 배포 지점에서 다운로드하고, 대상 OS에서 이 드라이버를 준비합니다.  

    1. OS 이미지를 사용하는 경우 작업 순서는 드라이버를 OS 드라이버 저장소에 배치합니다.  

    2. OS 업그레이드 패키지를 원래 설치 원본으로 사용하는 경우 작업 순서는 드라이버의 위치를 사용하여 Windows 설치 프로그램을 구성합니다.  

 5.  작업 순서의 **Windows 및 ConfigMgr 설치** 단계에서 Windows 설치 프로그램은 이 단계로 준비된 드라이버를 찾습니다.  


 > [!IMPORTANT]  
 >  독립 실행형 미디어는 **드라이버 자동 적용** 단계를 사용할 수 없습니다. 이 시나리오에서는 작업 순서가 Configuration Manager 사이트에 연결되어 있지 않습니다.  

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다.

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDAutoApplyDriverBestMatch](/sccm/osd/understand/task-sequence-variables#OSDAutoApplyDriverBestMatch)  
 - [OSDAutoApplyDriverCategoryList](/sccm/osd/understand/task-sequence-variables#OSDAutoApplyDriverCategoryList)  
 - [SMSTSDriverRequestConnectTimeOut](/sccm/osd/understand/task-sequence-variables#SMSTSDriverRequestConnectTimeOut)  
 - [SMSTSDriverRequestReceiveTimeOut](/sccm/osd/understand/task-sequence-variables#SMSTSDriverRequestReceiveTimeOut)  
 - [SMSTSDriverRequestResolveTimeOut](/sccm/osd/understand/task-sequence-variables#SMSTSDriverRequestResolveTimeOut)  
 - [SMSTSDriverRequestSendTimeOut](/sccm/osd/understand/task-sequence-variables#SMSTSDriverRequestSendTimeOut)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **드라이버**를 선택한 다음, **드라이버 자동 적용**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="install-only-the-best-matched-compatible-drivers"></a>가장 적합한 호환 드라이버만 설치
 작업 순서 단계가 검색된 각 하드웨어 디바이스에 가장 적합한 드라이버만 설치하도록 지정합니다.  

#### <a name="install-all-compatible-drivers"></a>호환되는 모든 드라이버 설치
 검색된 각 하드웨어 디바이스와 호환되는 모든 드라이버를 설치합니다. 그런 다음 Windows 설치 프로그램에서 가장 적합한 드라이버를 선택합니다. 이 옵션은 더 많은 네트워크 대역폭과 디스크 공간을 사용합니다. 작업 순서에서 더 많은 드라이버를 다운로드함으로써 Windows에서 더 적합한 드라이버를 선택할 수 있습니다.  

#### <a name="consider-drivers-from-all-categories"></a>모든 범주의 드라이버 고려
 사용 가능한 모든 드라이버 범주에서 적절한 디바이스 드라이버를 검색합니다.  

#### <a name="limit-driver-matching-to-only-consider-drivers-in-selected-categories"></a>선택한 범주의 드라이버만 고려하도록 드라이버 일치 제한
 지정한 드라이버 범주에서 적절한 디바이스 드라이버를 검색합니다.  

#### <a name="do-unattended-installation-of-unsigned-drivers-on-versions-of-windows-where-this-is-allowed"></a>허용되는 Windows 버전에서 서명되지 않은 드라이버 자동 설치
 이 옵션을 사용하면 Windows에서 디지털 서명이 없는 드라이버를 설치할 수 있습니다.   

 > [!IMPORTANT]  
 >  이 옵션은 드라이버 서명 정책을 구성할 수 없는 운영 체제에는 적용되지 않습니다.  



##  <a name="BKMK_CaptureNetworkSettings"></a> 네트워크 설정 캡처  

 이 단계를 사용하여 작업 순서를 실행하는 컴퓨터에서 Microsoft 네트워크 설정을 캡처합니다. 작업 순서는 이러한 설정을 작업 순서 변수에 저장합니다. 이러한 설정은 **네트워크 설정 적용** 단계에서 구성한 기본 설정을 재정의합니다.  

 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDMigrateAdapterSettings](/sccm/osd/understand/task-sequence-variables#OSDMigrateAdapterSettings)  
 - [OSDMigrateNetworkMembership](/sccm/osd/understand/task-sequence-variables#OSDMigrateNetworkMembership)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **설정**을 선택한 다음, **네트워크 설정 캡처**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="migrate-domain-and-workgroup-membership"></a>도메인 및 작업 그룹 멤버 자격 마이그레이션 
 대상 컴퓨터의 도메인 및 작업 그룹 멤버 자격 정보를 캡처합니다.  

#### <a name="migrate-network-adapter-configuration"></a>네트워크 어댑터 구성 마이그레이션
 대상 컴퓨터의 네트워크 어댑터 구성을 캡처합니다. 다음 정보가 캡처됩니다. 
 - 전역 네트워크 설정  
 - 어댑터 수  
 - 각 어댑터와 연결된 네트워크 설정: DNS, WINS, IP 및 포트 필터



##  <a name="BKMK_CaptureOperatingSystemImage"></a> 운영 체제 이미지 캡처  

 이 단계는 참조 컴퓨터에서 하나 이상의 이미지를 캡처합니다. 작업 순서는 지정된 네트워크 공유에서 Windows 이미지(.wim) 파일을 만듭니다. 그런 다음 **운영 체제 이미지 패키지 추가** 마법사를 사용하여 이미지 기반 OS 배포를 위한 Configuration Manager로 이 이미지를 가져옵니다.  

 Configuration Manager는 참조 컴퓨터에서 .wim 파일 내의 별도 이미지로 각 볼륨(드라이브)을 캡처합니다. 참조된 컴퓨터에 여러 볼륨이 있는 경우 결과 .wim 파일에 각 볼륨에 대한 별도의 이미지가 포함됩니다. 이 단계는 NTFS 또는 FAT32로 포맷된 볼륨만 캡처합니다. 다른 형식의 볼륨과 USB 볼륨은 건너뜁니다.  

 참조 컴퓨터에 설치된 OS는 Configuration Manager에서 지원되는 Windows 버전이어야 합니다. SysPrep 도구를 사용하여 참조 컴퓨터에서 OS를 준비합니다. 설치된 OS 볼륨과 부팅 볼륨은 동일한 볼륨이어야 합니다.  

 선택한 네트워크 공유에 대한 쓰기 권한이 있는 계정을 지정합니다. OS 이미지 캡처 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#capture-operating-system-image-account)을 참조하세요.

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다. 

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDCaptureAccount](/sccm/osd/understand/task-sequence-variables#OSDCaptureAccount)  
 - [OSDCaptureAccountPassword](/sccm/osd/understand/task-sequence-variables#OSDCaptureAccountPassword)  
 - [OSDCaptureDestination](/sccm/osd/understand/task-sequence-variables#OSDCaptureDestination)  
 - [OSDImageCreator](/sccm/osd/understand/task-sequence-variables#OSDImageCreator)  
 - [OSDImageDescription](/sccm/osd/understand/task-sequence-variables#OSDImageDescription)  
 - [OSDImageVersion](/sccm/osd/understand/task-sequence-variables#OSDImageVersion)  
 - [OSDTargetSystemRoot](/sccm/osd/understand/task-sequence-variables#OSDTargetSystemRoot-input)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **운영 체제 이미지 캡처**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="target"></a>Target  
 Configuration Manager에서 캡처된 OS 이미지를 저장할 때 사용하는 위치의 파일 시스템 경로입니다.  

#### <a name="description"></a>설명  
 이미지 파일에 저장된 캡처된 OS 이미지에 대한 선택적 사용자 정의 설명입니다.  

#### <a name="version"></a>Version  
 캡처된 OS 이미지에 할당할 선택적 사용자 정의 버전 번호입니다. 이 값은 문자와 숫자의 임의 조합일 수 있으며 이미지 파일에 저장됩니다.  

#### <a name="created-by"></a>만든 사람  
 OS 이미지를 만든 사용자의 선택적 이름입니다. 이미지 파일에 저장됩니다.  

#### <a name="capture-operating-system-image-account"></a>운영 체제 이미지 캡처 계정  
 지정된 네트워크 공유에 대한 권한이 있는 Windows 계정을 입력합니다. **설정**을 클릭하여 해당 Windows 계정의 이름을 지정합니다.  



##  <a name="BKMK_CaptureUserState"></a> 사용자 상태 캡처  

 이 단계에서는 USMT(사용자 환경 마이그레이션 도구)를 사용하여 작업 순서를 실행하는 컴퓨터에서 사용자 상태 및 설정을 캡처합니다. 이 작업 순서 단계는 **사용자 상태 복원** 작업 순서 단계와 함께 사용됩니다. 이 단계에서는 항상 Configuration Manager에서 생성 및 관리되는 암호화 키를 사용하여 USMT 상태 저장소를 암호화합니다.  

 운영 체제를 배포할 때 사용자 상태를 관리하는 방법에 대한 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  

 상태 마이그레이션 지점에서 사용자 상태 설정을 저장하거나 복원하려는 경우, **상태 저장소 요청** 및 **상태 저장소 해제** 단계와 함께 이 단계를 사용합니다.  

 이 단계는 가장 일반적으로 사용되는 USMT 옵션의 제한된 하위 집합을 제어합니다. **OSDMigrateAdditionalCaptureOptions** 작업 순서 변수를 사용하여 추가 명령줄 옵션을 지정하세요.  

 이 작업 순서 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [_OSDMigrateUsmtPackageID](/sccm/osd/understand/task-sequence-variables#OSDMigrateUsmtPackageID)  
 - [OSDMigrateAdditionalCaptureOptions](/sccm/osd/understand/task-sequence-variables#OSDMigrateAdditionalCaptureOptions)  
 - [OSDMigrateConfigFiles](/sccm/osd/understand/task-sequence-variables#OSDMigrateConfigFiles)  
 - [OSDMigrateContinueOnLockedFiles](/sccm/osd/understand/task-sequence-variables#OSDMigrateContinueOnLockedFiles)  
 - [OSDMigrateEnableVerboseLogging](/sccm/osd/understand/task-sequence-variables#OSDMigrateEnableVerboseLogging)  
 - [OSDMigrateMode](/sccm/osd/understand/task-sequence-variables#OSDMigrateMode)  
 - [OSDMigrateSkipEncryptedFiles](/sccm/osd/understand/task-sequence-variables#OSDMigrateSkipEncryptedFiles)  
 - [OSDStateStorePath](/sccm/osd/understand/task-sequence-variables#OSDStateStorePath)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **사용자 상태**를 선택한 다음, **사용자 상태 캡처**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="user-state-migration-tool-package"></a>사용자 환경 마이그레이션 도구 패키지
 USMT(사용자 상태 마이그레이션 도구)가 포함된 패키지를 지정합니다. 작업 순서는 이 버전의 USMT를 사용하여 사용자 상태 및 설정을 캡처합니다. 이 패키지에는 프로그램이 필요하지 않습니다. 32비트 또는 64비트 버전의 USMT가 포함된 패키지를 지정합니다. USMT의 아키텍처는 작업 순서에서 상태를 캡처하는 OS의 아키텍처에 따라 달라집니다.  

#### <a name="capture-all-user-profiles-with-standard-options"></a>표준 옵션을 사용하여 모든 사용자 프로필 캡처
 모든 사용자 프로필 정보를 마이그레이션합니다. 이 옵션은 기본값입니다.  

 이 옵션을 선택하지만 **사용자 상태 복원** 단계에서 **로컬 컴퓨터 사용자 프로필 복원**을 선택하지 않으면 작업 순서가 실패합니다. Configuration Manager는 암호를 할당하지 않고는 새 계정을 마이그레이션할 수 없습니다. 

 **새 작업 순서** 마법사의 **기존 이미지 패키지 설치** 옵션을 사용하는 경우, 결과 작업 순서는 기본적으로 **표준 옵션으로 모든 사용자 프로필 캡처**로 설정됩니다. 이 기본 작업 순서는 **로컬 컴퓨터 사용자 프로필 복원** 또는 도메인이 아닌 사용자 계정 옵션을 선택하지 않습니다.  

 **로컬 컴퓨터 사용자 프로필 복원**을 선택하고 마이그레이션할 계정의 암호를 입력합니다. 수동으로 만든 작업 순서에서는 **사용자 상태 복원** 단계에서 이 설정을 확인할 수 있습니다. **새 작업 순서** 마법사에서 만든 작업 순서에서는 **사용자 파일 및 설정 복원** 단계 마법사 페이지에서 이 설정을 확인할 수 있습니다.  

 로컬 사용자 계정이 없는 경우 이 설정이 적용되지 않습니다.  

#### <a name="customize-how-user-profiles-are-captured"></a>사용자 프로필 캡처 방식을 사용자 지정
 마이그레이션할 사용자 지정 프로필 파일을 지정하려면 이 옵션을 선택합니다. **파일** 을 클릭하여 이 단계에서 사용할 USMT의 구성 파일을 선택합니다. 마이그레이션할 사용자 상태 파일을 정의하는 규칙이 포함된 사용자 지정.xml 파일을 지정합니다.  

#### <a name="click-here-to-select-configuration-files"></a>구성 파일을 선택하려면 여기를 클릭하세요.
 USMT 패키지에서 사용자 프로필을 캡처하는 데 사용할 구성 파일을 선택하려면 이 옵션을 선택합니다. **파일** 단추를 클릭하여 **구성 파일** 대화 상자를 시작합니다. 구성 파일을 지정하려면 **파일 이름** 행에 파일 이름을 입력하고 **추가** 단추를 클릭합니다.  

#### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용
 자세한 로그 파일 정보를 생성하려면 이 옵션을 선택합니다. 상태를 캡처할 때 작업 순서는 기본적으로 `%WinDir%\ccm\logs` 작업 순서 로그 폴더에 **ScanState.log** 로그를 생성합니다.   

#### <a name="skip-files-using-encrypted-file-system"></a>EFS(암호화된 파일 시스템)를 사용하는 파일 건너뛰기
 EFS(암호화된 파일 시스템)로 암호화된 파일의 캡처를 건너뛰려면 이 옵션을 사용합니다. 이러한 파일에는 사용자 프로필 파일이 포함됩니다. OS 및 USMT 버전에 따라 복원 후 암호화된 파일을 읽지 못할 수도 있습니다. 자세한 내용은 USMT 설명서를 참조하세요.  

#### <a name="copy-by-using-file-system-access"></a>파일 시스템 액세스를 사용하여 복사
 다음 설정 중 하나를 지정하려면 이 옵션을 선택합니다.  

 - **일부 파일을 캡처할 수 없는 경우 계속**: 일부 파일을 캡처할 수 없는 경우에도 마이그레이션 프로세스를 계속하려면 이 설정을 사용하도록 설정합니다. 이 옵션을 사용하지 않고 파일도 캡처할 수 없다면 이 단계는 실패합니다. 기본적으로 이 옵션은 사용하도록 설정됩니다.  

 - **파일을 복사하지 않고 링크를 사용하여 로컬로 캡처**: NTFS 하드 링크를 사용하여 파일을 캡처하려면 이 설정을 사용하도록 설정합니다.  

     하드 링크를 사용하여 데이터를 마이그레이션하는 방법에 대한 자세한 내용은 [하드 링크 마이그레이션 저장소](https://docs.microsoft.com/windows/deployment/usmt/usmt-hard-link-migration-store)를 참조하세요.  

 - **오프라인 모드 캡처(Windows PE 전용)**: 전체 OS 대신 Windows PE에서 사용자 상태를 캡처하려면 이 설정을 선택합니다.  

#### <a name="capture-by-using-volume-copy-shadow-services-vss"></a>VSS(Volume Copy Shadow) 서비스를 사용하여 캡처
 이 옵션을 사용하면 다른 애플리케이션에 의해 편집이 잠겨 있는 경우에도 파일을 캡처할 수 있습니다.  



##  <a name="BKMK_CaptureWindowsSettings"></a> Windows 설정 캡처  

 이 단계를 사용하여 작업 순서를 실행하는 컴퓨터에서 Windows 설정을 캡처합니다. 작업 순서는 이러한 설정을 작업 순서 변수에 저장합니다. 이러한 캡처된 설정은 **Windows 설정 적용** 단계에서 구성한 기본 설정을 재정의합니다.  

 이 작업 순서 단계는 Windows PE 또는 전체 OS에서 실행됩니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDComputerName](/sccm/osd/understand/task-sequence-variables#OSDComputerName-output)  
 - [OSDMigrateComputerName](/sccm/osd/understand/task-sequence-variables#OSDMigrateComputerName)  
 - [OSDMigrateRegistrationInfo](/sccm/osd/understand/task-sequence-variables#OSDMigrateRegistrationInfo)  
 - [OSDMigrateTimeZone](/sccm/osd/understand/task-sequence-variables#OSDMigrateTimeZone)  
 - [OSDRegisteredOrgName](/sccm/osd/understand/task-sequence-variables#OSDRegisteredOrgName-output)  
 - [OSDTimeZone](/sccm/osd/understand/task-sequence-variables#OSDTimeZone-output)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **설정**을 선택한 다음, **Windows 설정 캡처**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="migrate-computer-name"></a>컴퓨터 이름 마이그레이션
 컴퓨터의 NetBIOS 컴퓨터 이름을 캡처합니다.  

#### <a name="migrate-registered-user-and-organization-names"></a>등록된 사용자와 조직 이름 마이그레이션
 컴퓨터에서 등록된 사용자 및 조직 이름을 캡처합니다.  

#### <a name="migrate-time-zone"></a>표준 시간대 마이그레이션
 컴퓨터에서 표준 시간대 설정을 캡처합니다.  



##  <a name="BKMK_CheckReadiness"></a> 준비 확인  

 이 단계를 사용하여 대상 컴퓨터에서 지정된 배포 필수 조건이 충족되는지 확인합니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **준비 확인**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="ensure-minimum-memory-mb"></a>최소 메모리(MB) 확인
 MB(메가바이트) 단위의 메모리 양이 지정된 크기를 충족하거나 초과하는지 확인합니다. 이 단계는 기본적으로 이 설정을 사용합니다.  

#### <a name="ensure-minimum-processor-speed-mhz"></a>최소 프로세서 속도(MHz) 확인  
 MHz(메가헤르츠) 단위의 프로세서 속도가 지정된 크기를 충족하거나 초과하는지 확인합니다. 이 단계는 기본적으로 이 설정을 사용합니다.  

#### <a name="ensure-minimum-free-disk-space-mb"></a>사용 가능한 최소 디스크 공간(MB) 확인
 MB(메가바이트) 단위의 사용 가능한 디스크 공간이 지정된 크기를 충족하거나 초과하는지 확인합니다.  

#### <a name="ensure-current-os-to-be-refreshed-is"></a>현재 OS 새로 고침 확인
 대상 컴퓨터에 설치된 OS에서 지정된 요구 사항이 충족되는지 확인합니다. 이 단계는 기본적으로 이 설정을 **클라이언트**로 설정합니다.  


### <a name="options"></a>Options

 > [!NOTE]  
 > 이 단계의 **옵션** 탭에서 **오류 발생 시 계속** 설정을 사용하도록 설정하면 준비 검사 결과만 기록됩니다. 검사가 실패하더라도 작업 순서는 중지되지 않습니다.  



##  <a name="BKMK_ConnectToNetworkFolder"></a> 네트워크 폴더에 연결  

 이 단계를 사용하여 공유 네트워크 폴더에 대한 연결을 만듭니다.  

 이 작업 순서 단계는 전체 OS 또는 Windows PE에서 실행됩니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [SMSConnectNetworkFolderAccount](/sccm/osd/understand/task-sequence-variables#SMSConnectNetworkFolderAccount)  
 - [SMSConnectNetworkFolderDriveLetter](/sccm/osd/understand/task-sequence-variables#SMSConnectNetworkFolderDriveLetter)  
 - [SMSConnectNetworkFolderPassword](/sccm/osd/understand/task-sequence-variables#SMSConnectNetworkFolderPassword)  
 - [SMSConnectNetworkFolderPath](/sccm/osd/understand/task-sequence-variables#SMSConnectNetworkFolderPath)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **네트워크 폴더에 연결**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="path"></a>경로  
 **찾아보기**를 클릭하여 네트워크 폴더 경로를 지정합니다. `\\server\share` 형식을 사용합니다.

#### <a name="drive"></a>드라이브  
 이 연결에 할당할 로컬 드라이브 문자를 선택합니다. 

#### <a name="account"></a>계정 
 **설정**을 클릭하여 이 네트워크 폴더에 연결할 수 있는 권한이 있는 사용자 계정을 지정합니다. 작업 순서 네트워크 폴더 연결 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-editor-network-folder-connection-account)을 참조하세요.



##  <a name="BKMK_DisableBitLocker"></a> BitLocker 사용 안 함  

 이 단계를 사용하여 현재 OS 드라이브 또는 특정 드라이브에서 BitLocker 암호화를 사용하지 않도록 설정합니다. 이 동작은 하드 드라이브에서 키 보호기를 일반 텍스트로 표시된 상태로 둡니다. 드라이브의 내용은 해독하지 않습니다. 이 동작은 거의 즉시 완료됩니다.  

 > [!NOTE]  
 >  BitLocker 드라이브 암호화는 디스크 볼륨의 내용에 대한 하위 수준 암호화를 제공합니다.  

 암호화한 드라이브가 여러 개인 경우 OS 드라이브에서 BitLocker를 사용하지 않도록 설정하려면 먼저 원하는 데이터 드라이브에서 BitLocker를 사용하지 않도록 설정하세요.  

 이 단계는 전체 OS에서만 실행됩니다. Windows PE에서는 실행되지 않습니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **디스크**를 선택한 다음, **BitLocker 사용 안 함**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="current-operating-system-drive"></a>현재 운영 체제 드라이브
 현재 OS 드라이브에서 BitLocker를 사용하지 않도록 설정합니다.  

#### <a name="specific-drive"></a>특정 드라이브  
 특정 드라이브에서 BitLocker를 사용하지 않도록 설정합니다. 드롭다운 목록을 사용하여 BitLocker를 사용하지 않도록 설정할 드라이브를 지정할 수 있습니다.  



##  <a name="BKMK_DownloadPackageContent"></a> 패키지 콘텐츠 다운로드  

 이 단계를 사용하여 다음 패키지 유형 중 하나를 다운로드합니다.  

 - OS 이미지  
 - OS 업그레이드 패키지  
 - 드라이버 패키지  
 - 패키지  
 - 부팅 이미지  


 다음 단계는 다음과 같은 시나리오에서 OS를 업그레이드하는 작업 순서에서 잘 작동합니다.  

 - x86 및 x64 플랫폼에서 둘 다 사용 가능한 단일 업그레이드 작업 순서를 사용하는 경우. **업그레이드 준비** 그룹에서 두 개의 **패키지 콘텐츠 다운로드** 단계가 포함됩니다. **옵션** 탭에서 조건을 지정하여 클라이언트 아키텍처를 검색하고 적절한 OS 업그레이드 패키지만 다운로드합니다. 같은 변수를 사용하도록 각 **패키지 콘텐츠 다운로드** 단계를 구성합니다. **운영 체제 업그레이드** 단계에서 미디어 경로에 대한 변수를 사용합니다.  

 - 해당 드라이버 패키지를 동적으로 다운로드하려면 각 드라이버 패키지에 대해 적합한 하드웨어 종류를 검색하는 조건을 포함하는 두 가지 **패키지 콘텐츠 다운로드** 단계를 사용합니다. 같은 변수를 사용하도록 각 **패키지 콘텐츠 다운로드** 단계를 구성합니다. **운영 체제 업그레이드** 단계의 [드라이버] 섹션에서 **준비된 콘텐츠** 값에 대한 변수를 사용합니다.  


 > [!NOTE]    
 > 이 단계가 포함된 작업 순서를 배포하는 경우, 소프트웨어 배포 마법사의 **배포 지점** 페이지에서 **배포 옵션**에 대해 **작업 순서를 시작하기 전에 모든 콘텐츠를 로컬에 다운로드** 또는 **배포 지점에서 직접 콘텐츠 액세스**를 선택하지 않도록 합니다.  

 이 단계는 전체 OS 또는 Windows PE에서 실행됩니다. 구성 관리자 클라이언트 캐시에 패키지를 저장하는 옵션은 Windows PE에서 지원되지 않습니다.

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **소프트웨어**를 선택한 다음, **패키지 콘텐츠 다운로드**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="select-package"></a>패키지 선택  
 다운로드할 패키지를 선택하려면 아이콘을 클릭합니다. 한 패키지를 선택한 후 또 다른 패키지를 선택하려면 아이콘을 다시 클릭합니다.  

#### <a name="place-into-the-following-location"></a>다음 위치에 배치
 다음 위치 중 하나에 패키지를 저장하려면 선택합니다.  

 - **작업 순서 작업 디렉터리**: 이 위치는 작업 순서 캐시라고도 합니다.  

 - **구성 관리자 클라이언트 캐시**: 이 옵션을 사용하여 클라이언트 캐시에 콘텐츠를 저장합니다. 기본적으로 이 경로는 `%WinDir%\ccmcache`입니다.  

 - **사용자 지정 경로**: 작업 순서 엔진이 먼저 패키지를 작업 순서 작업 디렉터리에 다운로드합니다. 그런 다음 콘텐츠를 사용자가 지정한 이 경로로 이동합니다. 작업 순서 엔진은 경로에 패키지 ID를 추가합니다.  

#### <a name="save-path-as-a-variable"></a>변수로 경로 저장
 패키지의 경로를 사용자 지정 작업 순서 변수에 저장하세요. 그런 다음 다른 작업 순서 단계에서 이 변수를 사용합니다. 

 Configuration Manager에서 변수 이름에 숫자 접미사를 추가합니다. 예를 들어 `%MyContent%`라는 변수를 사용자 지정 변수로 지정합니다. 이 변수는 작업 순서에서 이 단계를 위해 참조한 모든 콘텐츠를 저장하는 위치의 루트입니다. 이 콘텐츠에는 여러 패키지가 포함될 수 있습니다. 이 변수를 참조할 때에는 숫자 접미사를 추가하세요. 첫 번째 패키지의 경우 `%MyContent01%`을 참조합니다. **운영 체제 업그레이드**와 같은 후속 단계에서 변수를 참조하는 경우 `%MyContent02%` 또는 `%MyContent03%`를 사용합니다. 여기서 숫자는 **패키지 콘텐츠 다운로드** 단계에서 패키지가 나열되는 순서에 해당합니다.  

#### <a name="if-a-package-download-fails-continue-downloading-other-packages-in-the-list"></a>패키지 다운로드가 실패하면 목록의 다른 패키지를 계속 다운로드합니다.
 작업 순서가 패키지 다운로드에 실패하면 목록에 있는 다음 패키지를 다운로드하기 시작합니다.  



##  <a name="BKMK_EnableBitLocker"></a> BitLocker 사용  

 이 단계를 사용하여 하드 드라이브의 파티션 둘 이상에서 BitLocker 암호화를 사용하도록 설정합니다. 첫 번째 활성 파티션에는 Windows 부트스트랩 코드가 포함되고, 다른 파티션에는 OS가 포함됩니다. 부트스트랩 파티션은 암호화되지 않은 상태로 유지해야 합니다.  

 **BitLocker 사전 프로비전** 단계를 사용하여 Windows PE에서 작업하는 동안 드라이브에서 BitLocker를 사용하도록 설정할 수 있습니다. 자세한 내용은 [BitLocker 사전 프로비전](#BKMK_PreProvisionBitLocker)을 참조하세요.  

 > [!NOTE]  
 >  BitLocker 드라이브 암호화는 디스크 볼륨의 내용에 대한 하위 수준 암호화를 제공합니다.  

 이 단계는 전체 OS에서만 실행됩니다. Windows PE에서는 실행되지 않습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDBitLockerRecoveryPassword](/sccm/osd/understand/task-sequence-variables#OSDBitLockerRecoveryPassword)  
 - [OSDBitLockerStartupKey](/sccm/osd/understand/task-sequence-variables#OSDBitLockerStartupKey)  


 **TPM만** , **TPM과 USB의 시작 키**또는 **TPM 및 PIN**을 지정하는 경우, **BitLocker 사용** 단계를 실행하기 전에 TPM(신뢰할 수 있는 플랫폼 모듈)이 다음과 같은 상태여야 합니다.  
 - 사용  
 - 활성화됨  
 - 소유권 허용  


 이 단계는 나머지 모든 TPM 초기화를 완료합니다. 나머지 단계에서는 실제로 존재하거나 다시 부팅할 필요가 없습니다. **BitLocker 사용** 단계는 필요한 경우 다음의 나머지 TPM 초기화 단계를 투명하게 완료합니다.  
 - 인증 키 쌍 만들기  
 - 소유자 권한 부여 값 및 Active Directory 에스크로 만들기(이 값을 지원하도록 확장해야 함)  
 - 소유권 가져오기  
 - 저장소 루트 키를 만들거나 다시 설정(이미 있지만 호환되지 않는 경우)  

   
 작업 순서에서 **BitLocker 사용** 단계가 드라이브 암호화 프로세스를 완료할 때까지 기다리도록 하려는 경우 **대기** 옵션을 선택합니다. **대기** 옵션을 선택하지 않으면 드라이브 암호화 프로세스가 백그라운드에서 수행됩니다. 작업 순서는 즉시 다음 단계로 진행됩니다.  

 BitLocker는 컴퓨터 시스템(OS와 데이터 드라이브 모두)에서 여러 드라이브를 암호화하는 데 사용될 수 있습니다. 데이터 드라이브를 암호화하려면 먼저 OS 드라이브를 암호화하고 암호화 프로세스를 완료합니다. 이 요구 사항은 OS 드라이브에서 데이터 드라이브에 대한 키 보호기를 저장하기 때문입니다. 동일한 작업 순서에서 OS 및 데이터 드라이브를 암호화하는 경우 OS 드라이브에 대한 **BitLocker 사용** 단계에서 **대기** 옵션을 선택합니다.  

 하드 드라이브가 이미 암호화되었지만 BitLocker를 사용하지 않도록 설정된 경우 **BitLocker 사용** 단계는 키 보호기를 사용하도록 다시 설정하고 신속하게 완료합니다. 이 경우 하드 드라이브를 다시 암호화할 필요가 없습니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **디스크**를 선택한 다음, **BitLocker 사용**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="choose-the-drive-to-encrypt"></a>암호화할 드라이브를 선택하세요.
 암호화할 드라이브를 지정합니다. 현재 OS 드라이브를 암호화하려면 **현재 운영 체제 드라이브**를 선택합니다. 그런 다음 키 관리를 위해 다음 옵션 중 하나를 구성합니다.  

 - **TPM만**: TPM(신뢰할 수 있는 플랫폼 모듈)만 사용하려면 이 옵션을 선택합니다.  

 - **USB의 시작 키만**: USB 플래시 드라이브에 저장된 시작 키를 사용하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 BitLocker 시작 키가 포함된 USB 디바이스가 컴퓨터에 연결될 때까지 BitLocker에서 일반 부팅 프로세스를 잠급니다.  

 - **TPM과 USB의 시작 키**: TPM과 USB 플래시 드라이브에 저장된 시작 키를 사용하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 BitLocker 시작 키가 포함된 USB 디바이스가 컴퓨터에 연결될 때까지 BitLocker에서 일반 부팅 프로세스를 잠급니다.  

 - **TPM 및 PIN**: TPM 및 PIN(개인 식별 번호)을 사용하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 사용자가 PIN을 제공할 때까지 BitLocker에서 일반 부팅 프로세스를 잠급니다.  


 OS 이외의 특정 데이터 드라이브를 암호화하려면 **특정 드라이브**를 선택하세요. 그런 다음 목록에서 드라이브를 선택합니다.  

#### <a name="use-full-disk-encryption"></a>전체 디스크 암호화 사용
 <!--SCCMDocs-pr issue 2671--> 기본적으로 이 단계는 드라이브에서 사용된 공간만 암호화합니다. 이 기본 동작은 더 빠르고 효율적기 때문에 권장됩니다. 버전 1806부터는 조직에 설치 중에 전체 드라이브 암호화가 필요한 경우 이 옵션을 사용하도록 설정합니다. Windows 설치는 전체 드라이브가 암호화될 때까지 대기하는데, 특히 드라이브가 크면 긴 시간이 소요됩니다. 

#### <a name="choose-where-to-create-the-recovery-key"></a>복구 키를 만들 위치 선택
 BitLocker에서 복구 암호를 만들고 Active Directory에서 암호를 에스크로하도록 지정하려면 **Active Directory에서**를 선택합니다. 이 옵션을 사용하는 경우 BitLocker 키 에스크로를 위해 Active Directory를 확장해야 합니다. 그런 다음 BitLocker는 연결된 복구 정보를 Active Directory에 저장할 수 있습니다. 암호를 만들지 않으려면 **복구 키를 만들지 않음**을 선택합니다. 암호를 만드는 것이 좋습니다.  

#### <a name="wait-for-bitlocker-to-complete-the-drive-encryption-process-on-all-drives-before-continuing-task-sequence-execution"></a>작업 순서 실행을 계속하기 전에 BitLocker가 모든 드라이브에서 드라이브 암호화 프로세스를 완료하기까지 기다림
 작업 순서의 다음 단계를 실행하기 전에 BitLocker 드라이브 암호화가 완료되도록 하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 사용자가 컴퓨터에 로그인하기 전에 BitLocker에서 전체 디스크 볼륨을 암호화합니다.  

 대용량 하드 드라이브를 암호화할 때 암호화 프로세스를 완료하는 데 몇 시간이 걸릴 수 있습니다. 이 옵션을 선택하지 않으면 작업 순서를 즉시 진행할 수 있습니다.  



##  <a name="BKMK_FormatandPartitionDisk"></a> 디스크 포맷 및 파티션 만들기  

 이 단계를 사용하여 대상 컴퓨터에서 지정된 디스크를 포맷하고 분할할 수 있습니다.  

 > [!IMPORTANT]  
 >  이 단계에 대해 지정한 모든 설정은 지정된 단일 디스크에 적용됩니다. 대상 컴퓨터의 다른 디스크를 포맷하고 분할하려면 추가 **디스크 포맷 및 파티션 만들기** 단계를 작업 순서에 추가합니다.  

 이 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDDiskIndex](/sccm/osd/understand/task-sequence-variables#OSDDiskIndex)  
 - [OSDGPTBootDisk](/sccm/osd/understand/task-sequence-variables#OSDGPTBootDisk)  
 - [OSDPartitions](/sccm/osd/understand/task-sequence-variables#OSDPartitions)  
 - [OSDPartitionStyle](/sccm/osd/understand/task-sequence-variables#OSDPartitionStyle)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **디스크**를 선택한 다음, **디스크 포맷 및 파티션 만들기**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="disk-number"></a>디스크 번호
 포맷할 디스크의 실제 디스크 번호입니다. 이 번호는 Windows 디스크 열거 순서를 기반으로 합니다.  

#### <a name="disk-type"></a>디스크 유형
 포맷할 디스크의 유형입니다. 드롭다운 목록에서 선택할 수 있는 두 가지 옵션이 있습니다. 
 - **표준(MBR)**: 마스터 부트 레코드  
 - **GPT**: GUID 파티션 테이블  


 > [!NOTE]  
 >  디스크 유형을 **표준(MBR)** 에서 **GPT**로 변경하고 파티션 레이아웃에 확장 파티션이 포함된 경우, 작업 순서는 레이아웃에서 확장 및 논리 파티션을 모두 제거합니다. 작업 순서 편집기에서 디스크 유형을 변경하기 전에 이 동작을 확인하도록 요구하는 메시지가 표시됩니다.  
   
#### <a name="volume"></a>볼륨
 작업 순서에서 만드는 파티션 또는 볼륨에 대한 특정 정보이며, 다음 특성이 포함됩니다.  
 - Name  
 - 남은 디스크 공간  


 새 파티션을 만들려면 **새로 만들기** 를 클릭하여 **파티션 속성** 대화 상자를 시작합니다. 파티션 형식, 크기 및 부팅 파티션인지 여부를 지정합니다. 기존 파티션을 수정하려면 수정할 파티션을 클릭한 다음 **속성** 단추를 클릭합니다. 하드 드라이브 파티션을 구성하는 방법에 대한 자세한 내용은 다음 문서 중 하나를 참조하세요.  

 - [UEFI/GPT 기반 하드 드라이브 파티션](https://docs.microsoft.com/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)  
 - [BIOS/MBR 기반 하드 드라이브 파티션](https://docs.microsoft.com/windows-hardware/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions)  


 파티션을 삭제하려면 파티션을 선택하고 **삭제**를 클릭합니다.  



##  <a name="BKMK_InstallApplication"></a> 응용 프로그램 설치  

 이 단계는 지정된 애플리케이션 또는 작업 순서 변수의 동적 목록으로 정의된 애플리케이션 집합을 설치합니다. 작업 순서에서 이 단계를 실행하면 애플리케이션 설치가 정책 폴링 간격을 기다리지 않고 즉시 시작됩니다.  

 애플리케이션은 다음 조건을 충족해야 합니다.  

 - 애플리케이션의 배포 유형은 **Windows Installer** 또는 **스크립트** 설치 관리자여야 합니다. Windows 앱 패키지(.appx 파일) 배포 유형은 지원되지 않습니다.  

 - 사용자 계정이 아니라 로컬 시스템 계정으로 실행되어야 합니다.  

 - 데스크톱과 상호 작용해서는 안 됩니다. 프로그램이 자동으로 실행되거나 무인 모드로 실행되어야 합니다.  

 - 자체적으로 다시 시작해서는 안 됩니다. 애플리케이션이 표준 재시작 코드 3010을 사용하여 다시 시작을 요청해야 합니다. 이 동작은 이 단계가 다시 시작을 올바르게 처리하도록 합니다. 애플리케이션에서 3010 종료 코드를 반환하면 작업 순서 엔진이 컴퓨터를 다시 시작합니다. 다시 시작 후 작업 순서가 자동으로 계속됩니다.  


 이 단계가 실행되면 애플리케이션에서 해당 배포 유형에 대한 요구 사항 규칙 및 검색 방법의 적용 여부를 확인합니다. 이 확인 결과에 따라 애플리케이션은 적용 가능한 배포 유형을 설치합니다. 배포 유형에 종속성이 포함되어 있으면 종속 배포 유형이 평가되고 이 단계의 일부로 설치됩니다. 독립 실행형 미디어에는 애플리케이션 종속성이 지원되지 않습니다.  

 > [!NOTE]  
 >  다른 애플리케이션을 대체하는 애플리케이션을 설치하려면 대체되는 애플리케이션에 대한 콘텐츠 파일을 사용할 수 있어야 합니다. 그렇지 않으면 이 작업 순서 단계가 실패합니다. 예를 들어 클라이언트 또는 캡처된 이미지에 Microsoft Visio 2010이 설치되어 있을 때 **응용 프로그램 설치** 단계에서 Microsoft Visio 2013을 설치하면, Microsoft Visio 2010(대체되는 응용 프로그램)에 대한 콘텐츠 파일을 배포 지점에서 사용할 수 있어야 합니다. Microsoft Visio가 클라이언트 또는 캡처된 이미지에 전혀 설치되어 있지 않으면, Microsoft Visio 2010 콘텐츠 파일을 확인하지 않고 Microsoft Visio 2013이 설치됩니다.  

 > [!NOTE]  
 > 클라이언트가 위치 서비스에서 관리 지점 목록을 검색하지 못하면, **SMSTSMPListRequestTimeoutEnabled** 및 **SMSTSMPListRequestTimeout** 작업 순서 변수를 사용합니다. 이 변수는 애플리케이션 설치를 다시 시도하기 전까지 작업 순서에서 기다리는 시간(밀리초)을 지정합니다. 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables)\(작업 순서 변수\)를 참조하세요.

 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [_TSAppInstallStatus](/sccm/osd/understand/task-sequence-variables#TSAppInstallStatus)  
 - [SMSTSMPListRequestTimeoutEnabled](/sccm/osd/understand/task-sequence-variables#SMSTSMPListRequestTimeoutEnabled)  
 - [SMSTSMPListRequestTimeout](/sccm/osd/understand/task-sequence-variables#SMSTSMPListRequestTimeout)  
 - [TSErrorOnWarning](/sccm/osd/understand/task-sequence-variables#TSErrorOnWarning)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **소프트웨어**를 선택한 다음, **애플리케이션 설치**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="install-the-following-applications"></a>다음 애플리케이션 설치
 작업 순서는 이러한 애플리케이션을 지정된 순서대로 설치합니다.  

 Configuration Manager는 사용하지 않도록 설정된 애플리케이션 또는 다음 설정이 있는 애플리케이션을 필터링합니다.  

 - 사용자가 로그온했을 때만  
 - 사용자 권한으로 실행  


 이러한 애플리케이션은 **설치할 애플리케이션 선택** 대화 상자에 표시되지 않습니다.

#### <a name="install-applications-according-to-dynamic-variable-list"></a>동적 변수 목록에 따라 애플리케이션 설치
 작업 순서는 이 기본 변수 이름을 사용하여 애플리케이션을 설치합니다. 기본 변수 이름은 컬렉션 또는 컴퓨터에 대해 정의된 작업 순서 변수 집합을 나타냅니다. 이러한 변수는 작업 순서에서 해당 컬렉션 또는 컴퓨터에 대해 설치할 애플리케이션을 지정합니다. 각 변수 이름은 공통 기본 이름과 01부터 시작되는 숫자 접미사로 구성됩니다. 각 변수의 값은 애플리케이션 이름만 포함해야 합니다.  

 작업 순서에서 동적 변수 목록을 사용하여 애플리케이션을 설치하려면, 애플리케이션 **속성**의 **일반** 탭에서 **이 애플리케이션을 배포하는 대신, 애플리케이션 설치 작업 순서 동작으로 설치하도록 허용** 설정을 사용하도록 설정합니다.  

 > [!NOTE]  
 >  독립 실행형 미디어 배포의 경우 동적 변수 목록을 사용하여 애플리케이션을 설치할 수 없습니다.  

 예를 들어 AA01이라는 작업 순서 변수를 사용하여 단일 애플리케이션을 설치하려면 다음 변수를 지정합니다.  

 |변수 이름|변수 값|  
 |-------------------|--------------------|  
 |AA01|Microsoft Office|  

 두 개의 애플리케이션을 설치하려면 다음 변수를 지정합니다.  

 |변수 이름|변수 값|  
 |-------------------|--------------------|  
 |AA01|Microsoft Lync|  
 |AA02|Microsoft Office|  

 다음 조건은 작업 순서에서 설치되는 애플리케이션에 영향을 줍니다.  

 - 변수 값에 애플리케이션의 이름 외에 다른 정보가 포함된 경우. 작업 순서가 애플리케이션을 설치하지 않고 계속됩니다.  

 - 작업 순서가 지정된 기본 이름과 “01” 접미사가 있는 변수를 찾지 못하면 애플리케이션을 설치하지 않습니다.  


 > [!Important]  
 > 이러한 값은 대/소문자를 구분합니다. 예를 들어 “install”은 “Install”과 다릅니다. 값을 변경해야 하는 경우 작업 순서 편집기가 대/소문자 변경을 감지하지 않습니다. 예를 들어 동시에 다른 편집을 수행하세요(예: 단계 설명 수정).<!--509714-->   

#### <a name="if-an-application-fails-continue-installing-other-applications-in-the-list"></a>애플리케이션 설치가 실패할 경우 목록의 다른 애플리케이션 설치 계속
 이 설정은 개별 애플리케이션 설치가 실패할 때 단계가 계속되도록 지정합니다. 이 설정을 지정하면 설치 오류에 관계없이 작업 순서가 계속됩니다. 이 설정을 지정하지 않고 설치가 실패하면 이 단계는 즉시 종료됩니다.  


### <a name="options"></a>Options

 > [!NOTE]  
 > 이 단계의 **옵션** 탭에서 **오류 발생 시 계속**을 선택하면 애플리케이션 설치가 실패하더라도 작업 순서가 계속됩니다. 이 옵션을 사용하지 않으면 작업 순서가 실패하고 나머지 애플리케이션이 설치되지 않습니다.  

 기본 옵션 외에도, 이 작업 순서 단계의 **옵션** 탭에서 다음과 같은 추가 설정을 구성합니다.  

#### <a name="retry-this-step-if-computer-unexpectedly-restarts"></a>컴퓨터가 예기치 않게 다시 시작할 경우 이 단계 다시 시도
 애플리케이션 설치 중 하나가 예기치 않게 컴퓨터를 다시 시작하면 이 단계를 다시 시도합니다. 이 단계는 기본적으로 두 번의 다시 시도가 있는 설정을 사용하도록 설정합니다. 1-5번의 다시 시도를 지정할 수 있습니다.  



##  <a name="BKMK_InstallPackage"></a> 패키지 설치

 이 단계를 사용하여 작업 순서의 일부로 소프트웨어 패키지를 설치합니다. 이 단계가 실행되면 정책 폴링 간격 동안 기다리지 않고 설치가 즉시 시작됩니다.  

 패키지는 다음 조건을 충족해야 합니다.  

 - 사용자 계정이 아니라 로컬 시스템 계정으로 실행해야 합니다.  

 - 데스크톱과 상호 작용해서는 안 됩니다. 프로그램이 자동으로 실행되거나 무인 모드로 실행되어야 합니다.  

 - 자체적으로 다시 시작해서는 안 됩니다. 소프트웨어가 표준 재시작 코드 3010을 사용하여 다시 시작을 요청해야 합니다. 이 동작은 작업 순서에서 다시 시작을 제대로 처리하도록 합니다. 소프트웨어에서 3010 종료 코드를 반환하면 작업 순서 엔진이 컴퓨터를 다시 시작합니다. 다시 시작 후 작업 순서가 자동으로 계속됩니다.  


 **다른 프로그램을 먼저 실행** 옵션을 사용하여 종속 프로그램을 설치하는 프로그램은 OS를 배포할 때 지원되지 않습니다. **다른 프로그램을 먼저 실행** 패키지 옵션을 사용하고 종속 프로그램이 대상 컴퓨터에서 이미 실행된 경우 종속 프로그램이 실행되고 작업 순서가 계속됩니다. 그러나 종속 프로그램이 대상 컴퓨터에서 아직 실행되지 않은 경우 작업 순서 단계가 실패합니다.  

 > [!NOTE]  
 >  중앙 관리 사이트에는 작업 순서 중에 소프트웨어 배포 에이전트를 사용하도록 설정하는 데 필요한 필수 클라이언트 구성 정책이 없습니다. 중앙 관리 사이트의 작업 순서에 대한 독립 실행형 미디어를 만들 때 작업 순서에 **패키지 설치** 단계가 포함된 경우 다음 오류가 CreateTsMedia.log 파일에 나타날 수 있습니다.  
 >   
 >  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`  
 >   
 >  **패키지 설치** 단계가 포함된 독립 실행형 미디어의 경우 소프트웨어 배포 에이전트를 사용하도록 설정된 기본 사이트에서 독립 실행형 미디어를 만듭니다. 또는 **Windows 및 ConfigMgr 설치** 단계 뒤 및 첫 번째 **패키지 설치** 단계 앞에 **명령줄 실행** 단계를 추가합니다. **명령줄 실행** 단계에서는 WMIC 명령을 실행하여 첫 번째 **패키지 설치** 단계 이전에 소프트웨어 배포 에이전트를 사용하도록 설정합니다. **명령줄 실행** 단계에서 다음 명령을 사용합니다.  
 >   
 >  `WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE`  
 >   
 >  독립 실행형 미디어를 만드는 방법은 [독립 실행형 미디어 만들기](/sccm/osd/deploy-use/create-stand-alone-media)를 참조하세요.  


 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **소프트웨어**를 선택한 다음, **패키지 설치**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="install-a-single-software-package"></a>단일 소프트웨어 패키지 설치
 이 설정은 Configuration Manager 소프트웨어 패키지를 지정합니다. 이 단계는 설치가 완료될 때까지 기다립니다.  

#### <a name="install-software-packages-according-to-dynamic-variable-list"></a>동적 변수 목록에 따라 소프트웨어 패키지 설치
 작업 순서는 이 기본 변수 이름을 사용하여 패키지를 설치합니다. 기본 변수 이름은 컬렉션 또는 컴퓨터에 대해 정의된 작업 순서 변수 집합을 나타냅니다. 이러한 변수는 작업 순서에서 해당 컬렉션 또는 컴퓨터에 대해 설치할 패키지를 지정합니다. 각 변수 이름은 공통 기본 이름과 001부터 시작되는 숫자 접미사로 구성됩니다. 각 변수의 값은 콜론으로 구분된 패키지 ID와 소프트웨어 이름을 포함해야 합니다.  

 작업 순서에서 동적 변수 목록을 사용하여 응용 프로그램을 설치하려면, 패키지 **속성**의 **고급** 탭에서 **배포하지 않고 패키지 설치 작업 순서에서 프로그램 설치 허용** 설정을 사용하도록 설정합니다.  

 > [!NOTE]  
 >  독립 실행형 미디어 배포의 경우 동적 변수 목록을 사용하여 소프트웨어 패키지를 설치할 수 없습니다.  

 예를 들어 AA001이라는 작업 순서 변수를 사용하여 단일 소프트웨어 패키지를 설치하려면 다음 변수를 지정합니다.  

 |변수 이름|변수 값|  
 |-------------------|--------------------|  
 |AA001|CEN00054:Install|  

 세 가지 소프트웨어 패키지를 설치하려면 다음 변수를 지정합니다.  

 |변수 이름|변수 값|  
 |-------------------|--------------------|  
 |AA001|CEN00054:Install|  
 |AA002|CEN00107:Install Silent|  
 |AA003|CEN00031:Install|  

 다음 조건은 작업 순서에서 설치되는 패키지에 영향을 줍니다.  

 - 변수 값을 올바른 형식으로 만들지 않았거나 유효한 응용 프로그램 ID 및 이름을 지정하지 않으면 소프트웨어 설치가 실패합니다.  

 - 패키지 ID에 소문자가 포함되어 있으면 소프트웨어 설치가 실패합니다.  

 - 작업 순서가 지정된 기본 이름과 “001” 접미사가 있는 변수를 찾지 못하면 패키지를 설치하지 않습니다. 작업 순서가 계속됩니다.  


 > [!Important]  
 > 이러한 값은 대/소문자를 구분합니다. 예를 들어 “install”은 “Install”과 다릅니다. 값을 변경해야 하는 경우 작업 순서 편집기가 대/소문자 변경을 감지하지 않습니다. 예를 들어 동시에 다른 편집을 수행하세요(예: 단계 설명 수정).<!--509714-->   

#### <a name="if-installation-of-a-software-package-fails-continue-installing-other-packages-in-the-list"></a>소프트웨어 패키지 설치가 실패할 경우 목록의 다른 패키지 설치 계속
 이 설정은 개별 소프트웨어 패키지 설치에 실패한 경우 단계가 계속되도록 지정합니다. 이 설정을 지정하면 설치 오류에 관계없이 작업 순서가 계속됩니다. 이 설정을 지정하지 않고 설치가 실패하면 이 단계는 즉시 종료됩니다.  



##  <a name="BKMK_InstallSoftwareUpdates"></a> 소프트웨어 업데이트 설치  

 이 단계를 사용하여 대상 컴퓨터에 소프트웨어 업데이트를 설치합니다. 이 작업 순서 단계가 실행될 때까지 적용 가능한 소프트웨어 업데이트에 대해 대상 컴퓨터가 평가되지 않습니다. 이 시점에서는 다른 모든 구성 관리자 클라이언트와 마찬가지로 소프트웨어 업데이트에 대해 대상 컴퓨터가 평가됩니다. 이 단계에서 소프트웨어 업데이트를 설치하려면 먼저 대상 컴퓨터가 구성원인 컬렉션에 업데이트를 배포하세요.  

 > [!IMPORTANT]  
 > 최상의 성능을 이용하려면 최신 버전의 Windows 업데이트 에이전트를 설치하는 것이 좋습니다.  

 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다. 

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [SMSInstallUpdateTarget](/sccm/osd/understand/task-sequence-variables#SMSInstallUpdateTarget)  
 - [SMSTSMPListRequestTimeoutEnabled](/sccm/osd/understand/task-sequence-variables#SMSTSMPListRequestTimeoutEnabled)  
 - [SMSTSMPListRequestTimeout](/sccm/osd/understand/task-sequence-variables#SMSTSMPListRequestTimeout)  
 - [SMSTSSoftwareUpdateScanTimeout](/sccm/osd/understand/task-sequence-variables#SMSTSSoftwareUpdateScanTimeout)  
 - [SMSTSWaitForSecondReboot](/sccm/osd/understand/task-sequence-variables#SMSTSWaitForSecondReboot)  


 > [!NOTE]  
 > 클라이언트가 위치 서비스에서 관리 지점 목록을 검색하지 못하면, **SMSTSMPListRequestTimeoutEnabled** 및 **SMSTSMPListRequestTimeout** 변수를 사용합니다. 이 변수는 애플리케이션이나 소프트웨어 업데이트 설치를 다시 시도하기 전까지 작업 순서에서 기다리는 시간(밀리초)을 지정합니다. 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables)\(작업 순서 변수\)를 참조하세요.  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **소프트웨어**를 선택한 다음, **소프트웨어 업데이트 설치**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="required-for-installation---mandatory-software-updates-only"></a>설치에 필요 - 필수 소프트웨어 업데이트만
 관리자가 정의한 설치 최종 기한이 있는 필수 소프트웨어 업데이트를 모두 설치하려면 이 옵션을 선택합니다.  

#### <a name="available-for-installation---all-software-updates"></a>설치에 사용 가능 - 모든 소프트웨어 업데이트
 사용 가능한 모든 소프트웨어 업데이트를 설치하려면 이 옵션을 선택합니다. 먼저 컴퓨터가 구성원인 컬렉션에 이러한 업데이트를 배포하세요. 작업 순서는 사용 가능한 모든 소프트웨어 업데이트를 대상 컴퓨터에 설치합니다.  

#### <a name="evaluate-software-updates-from-cached-scan-results"></a>캐시된 검사 결과에서 소프트웨어 업데이트 평가
 기본적으로 이 단계는 Windows 업데이트 에이전트에서 캐시된 검색 결과를 사용합니다. Windows 업데이트 에이전트가 소프트웨어 업데이트 지점에서 최신 카탈로그를 다운로드하도록 지시하려면 이 옵션을 사용하지 않도록 설정하세요. 작업 순서를 사용하여 [OS 이미지를 캡처하고 만들](/sccm/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system) 때에는 이 옵션을 사용하도록 설정합니다. 이 시나리오에는 많은 수의 소프트웨어 업데이트가 있을 수 있습니다. 

 이러한 업데이트 중 다수에는 종속성이 있습니다. 예를 들어 업데이트 ABC를 먼저 설치해야 업데이트 XYZ가 적절하게 나타납니다. 이 설정을 사용하지 않도록 설정하고 많은 클라이언트에 작업 순서를 배포하면 이러한 클라이언트 모두가 소프트웨어 업데이트 지점에 동시에 연결됩니다. 이 동작으로 인해 업데이트 카탈로그 프로세스 및 다운로드 중에 성능 문제가 발생합니다. 

 대부분의 경우에는 기본 설정을 사용하여 캐시된 검색 결과를 사용하세요. 

 **SMSTSSoftwareUpdateScanTimeout** 변수는 이 단계에서 소프트웨어 업데이트 검색 시간 제한을 제어합니다. 기본값은 30분입니다. 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSSoftwareUpdateScanTimeout)\(작업 순서 변수\)를 참조하세요.


### <a name="options"></a>Options   

 기본 옵션 외에도, 이 작업 순서 단계의 **옵션** 탭에서 다음과 같은 추가 설정을 구성합니다.  

#### <a name="retry-this-step-if-computer-unexpectedly-restarts"></a>컴퓨터가 예기치 않게 다시 시작할 경우 이 단계 다시 시도
 업데이트 중 하나가 예기치 않게 컴퓨터를 다시 시작하면 이 단계를 다시 시도합니다. 이 단계는 기본적으로 두 번의 다시 시도가 있는 설정을 사용하도록 설정합니다. 1-5번의 다시 시도를 지정할 수 있습니다.  

 > [!NOTE]  
 > 이 시나리오에서 컴퓨터가 다시 시작된 후 작업 순서가 일시 중지되는 시간(초)을 지정하려면 **SMSTSWaitForSecondReboot** 변수를 구성합니다. 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSWaitForSecondReboot)\(작업 순서 변수\)를 참조하세요.  



##  <a name="BKMK_JoinDomainorWorkgroup"></a> 도메인 또는 작업 그룹 가입  

 이 단계를 사용하여 대상 컴퓨터를 작업 그룹 또는 도메인에 추가합니다.  

 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDJoinAccount](/sccm/osd/understand/task-sequence-variables#OSDJoinAccount)  
 - [OSDJoinDomainName](/sccm/osd/understand/task-sequence-variables#OSDJoinDomainName)  
 - [OSDJoinDomainOUName](/sccm/osd/understand/task-sequence-variables#OSDJoinDomainOUName)  
 - [OSDJoinPassword](/sccm/osd/understand/task-sequence-variables#OSDJoinPassword)  
 - [OSDJoinSkipReboot](/sccm/osd/understand/task-sequence-variables#OSDJoinSkipReboot)  
 - [OSDJoinType](/sccm/osd/understand/task-sequence-variables#OSDJoinType)  
 - [OSDJoinWorkgroupName](/sccm/osd/understand/task-sequence-variables#OSDJoinWorkgroupName)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **도메인 또는 작업 그룹 가입**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="join-a-workgroup"></a>작업 그룹에 가입
 대상 컴퓨터를 지정된 작업 그룹에 가입시키려면 이 옵션을 선택합니다. 컴퓨터가 현재 도메인의 멤버가 아닌 경우 이 옵션을 선택하면 컴퓨터가 다시 부팅됩니다.  

#### <a name="join-a-domain"></a>도메인에 가입
 대상 컴퓨터를 지정된 도메인에 가입시키려면 이 옵션을 선택합니다.  

 필요한 경우, 가입시킬 컴퓨터의 지정된 도메인에서 OU(조직 구성 단위)를 입력하거나 찾아봅니다. 컴퓨터가 현재 다른 도메인 또는 작업 그룹의 멤버인 경우 이 옵션을 선택하면 컴퓨터가 다시 부팅됩니다. 컴퓨터가 이미 다른 OU의 구성원인 경우 Active Directory Domain Services에서 이 방법을 통해 OU를 변경할 수 없기 때문에 Windows 설치 프로그램은 이 설정을 무시합니다.  

#### <a name="enter-the-account-which-has-permission-to-join-the-domain"></a>도메인에 가입할 수 있는 권한이 있는 계정을 입력하세요.
 **설정**을 클릭하여 도메인에 조인할 권한이 있는 계정에 대한 사용자 이름 및 암호를 입력합니다. 계정을 `Domain\account` 형식으로 입력합니다. 작업 순서 도메인 가입 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-editor-domain-joining-account)을 참조하세요.  



## <a name="BKMK_PrepareConfigMgrClientforCapture"></a> ConfigMgr 클라이언트 캡처 준비  

 이 단계를 사용하여 참조 컴퓨터에서 구성 관리자 클라이언트를 제거하거나 구성합니다. 이 동작은 이미징 프로세스의 일부로 캡처할 컴퓨터를 준비합니다.

 이 단계에서는 주요 정보만 제거하는 것이 아니라 구성 관리자 클라이언트를 완전히 제거합니다. 작업 순서에서 캡처된 OS 이미지를 배포할 때마다 새 구성 관리자 클라이언트가 설치됩니다.  

 > [!Note]  
 >  작업 순서 엔진은 **참조 운영 체제 이미지 만들기 및 캡처** 작업 순서 동안에만 클라이언트를 제거합니다. 작업 순서 엔진은 미디어 캡처 또는 사용자 지정 작업 순서와 같은 다른 캡처 방법에서는 클라이언트를 제거하지 않습니다.  

 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **ConfigMgr 클라이언트 캡처 준비**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에서는 **속성** 탭에 대한 설정이 필요하지 않습니다.



##  <a name="BKMK_PrepareWindowsforCapture"></a> Windows 캡처 준비  

 이 단계를 사용하여 참조 컴퓨터에서 OS 이미지를 캡처할 때 Sysprep 옵션을 지정합니다. 이 단계는 Sysprep을 실행한 다음 컴퓨터를 작업 순서에 지정된 Windows PE 부팅 이미지로 다시 부팅합니다. 참조 컴퓨터가 도메인에 조인되어 있으면 이 동작이 실패합니다.  

 이 단계는 전체 OS에서만 실행됩니다. Windows PE에서는 실행되지 않습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDKeepActivation](/sccm/osd/understand/task-sequence-variables#OSDKeepActivation)  
 - [OSDTargetSystemRoot](/sccm/osd/understand/task-sequence-variables#OSDTargetSystemRoot-output)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **Windows 캡처 준비**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="automatically-build-mass-storage-driver-list"></a>자동으로 대용량 저장소 드라이버 목록 만들기
 Sysprep를 통해 참조 컴퓨터에서 대용량 저장소 드라이버 목록을 자동으로 작성하려면 이 옵션을 선택합니다. 이 옵션을 사용하면 참조 컴퓨터의 sysprep.inf 파일에서 대용량 저장소 드라이버 만들기 옵션이 설정됩니다. 이 설정에 대한 자세한 내용은 Sysprep 설명서를 참조하세요.  

#### <a name="do-not-reset-activation-flag"></a>활성화 플래그 다시 설정 안 함
 Sysprep에서 제품 활성화 플래그를 다시 설정하지 못하도록 하려면 이 옵션을 선택합니다.  

#### <a name="shutdown-the-computer-after-running-this-action"></a>이 작업을 실행한 후 컴퓨터 종료
 <!--SCCMDocs-pr issue 2695--> 버전 1806부터는 이 옵션이 기본값인 다시 시작을 수행하는 대신 컴퓨터를 종료하도록 Sysprep에 지시합니다. 



##  <a name="BKMK_PreProvisionBitLocker"></a> BitLocker 사전 프로비전  

 이 단계를 사용하여 Windows PE에서 드라이브에 BitLocker를 사용하도록 설정합니다. 기본적으로 사용된 드라이브 공간만 암호화되므로 암호화 속도가 훨씬 빠릅니다. OS가 설치된 후 [BitLocker 사용](#BKMK_EnableBitLocker) 단계를 사용하여 키 관리 옵션을 적용합니다.단계를 사용하여 키 관리 옵션을 적용합니다. 

 이 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다.  

 > [!IMPORTANT]  
 >  BitLocker 사전 프로비전에는 Windows 7 이상이 필요합니다. 또한 컴퓨터에는 지원되고 사용하도록 설정된 TPM(신뢰할 수 있는 플랫폼 모듈)이 포함되어 있어야 합니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **디스크**를 선택한 다음, **BitLocker 사전 프로비전**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="apply-bitlocker-to-the-specified-drive"></a>지정한 드라이브에 BitLocker 적용
 BitLocker를 사용하도록 설정할 드라이브를 지정합니다. BitLocker는 드라이브에서 사용된 공간만 암호화합니다.  

#### <a name="use-full-disk-encryption"></a>전체 디스크 암호화 사용
 <!--SCCMDocs-pr issue 2671--> 기본적으로 이 단계는 드라이브에서 사용된 공간만 암호화합니다. 이 기본 동작은 더 빠르고 효율적기 때문에 권장됩니다. 버전 1806부터는 조직에 설치 중에 전체 드라이브 암호화가 필요한 경우 이 옵션을 사용하도록 설정합니다. Windows 설치는 전체 드라이브가 암호화될 때까지 대기하는데, 특히 드라이브가 크면 긴 시간이 소요됩니다. 

#### <a name="skip-this-step-for-computers-that-do-not-have-a-tpm-or-when-tpm-is-not-enabled"></a>컴퓨터에 TPM이 없거나 TPM이 사용되지 않는 경우 이 단계 건너뛰기
 지원되거나 사용하도록 설정된 TPM이 없는 컴퓨터에서 드라이브 암호화를 건너뛰려면 이 옵션을 선택합니다. 예를 들어 OS를 가상 머신에 배포할 때 이 옵션을 사용합니다.  



##  <a name="BKMK_ReleaseStateStore"></a> 상태 저장소 해제  

 이 단계를 사용하여 상태 마이그레이션 지점에 캡처 또는 복원 작업이 완료되었음을 알립니다. **상태 저장소 요청**, **사용자 상태 캡처** 및 **사용자 상태 복원** 단계와 함께 이 단계를 사용합니다. 이러한 단계를 사용하여 상태 마이그레이션 지점과 USMT(사용자 상태 마이그레이션 도구)를 사용하여 사용자 상태 데이터를 마이그레이션합니다.  

 운영 체제를 배포할 때 사용자 상태를 관리하는 방법에 대한 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  

 **상태 저장소 요청** 단계를 사용하여 사용자 상태를 *캡처*하기 위해 상태 마이그레이션 지점에 대한 액세스를 요청하는 경우, 이 단계는 상태 마이그레이션 지점에 캡처 프로세스가 완료되었음을 알립니다. 그런 다음 상태 마이그레이션 지점은 사용자 상태 데이터를 복원에 사용할 수 있는 것으로 표시합니다. 상태 마이그레이션 지점은 복원 컴퓨터에서 읽기 전용으로만 액세스할 수 있도록 사용자 상태 데이터에 대한 액세스 제어 권한을 설정합니다.  

 **상태 저장소 요청** 단계를 사용하여 사용자 상태를 *복원*하기 위해 상태 마이그레이션 지점에 대한 액세스를 요청하는 경우, 이 단계는 상태 마이그레이션 지점에 복원 프로세스가 완료되었음을 알립니다. 그런 다음 상태 마이그레이션 지점은 구성된 데이터 보존 설정을 활성화합니다.  

 > [!IMPORTANT]  
 > **상태 저장소 요청** 및 **상태 저장소 해제** 단계 사이의 모든 단계에 대해 **오류 발생 시 계속** 옵션을 설정하세요. 모든 **상태 저장소 요청** 단계에는 일치하는 **상태 저장소 해제** 단계가 있어야 합니다.  

 이 단계는 전체 OS에서만 실행됩니다. Windows PE에서는 실행되지 않습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDStateStorePath](/sccm/osd/understand/task-sequence-variables#OSDStateStorePath)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **사용자 상태**를 선택한 다음, **사용자 상태 해제**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에서는 **속성** 탭에 대한 설정이 필요하지 않습니다.



##  <a name="BKMK_RequestStateStore"></a> 상태 저장소 요청  

 이 단계를 사용하여 상태를 캡처 또는 복원할 때 상태 마이그레이션 지점에 대한 액세스를 요청합니다.  

 운영 체제를 배포할 때 사용자 상태를 관리하는 방법에 대한 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  

 **상태 저장소 해제**, **사용자 상태 캡처** 및 **사용자 상태 복원** 단계와 함께 이 단계를 사용합니다. 이러한 단계를 사용하여 상태 마이그레이션 지점과 USMT(사용자 상태 마이그레이션 도구)를 사용하여 컴퓨터 상태를 마이그레이션합니다.  

 > [!NOTE]  
 >  새 상태 마이그레이션 지점을 만들 때 최대 1시간 동안 사용자 상태 저장소를 사용할 수 없습니다. 가용성을 촉진하려면 사이트 제어 파일 업데이트를 트리거하도록 상태 마이그레이션 지점에 대한 속성 설정을 조정합니다.  

 이 단계는 오프라인 USMT를 위해 Windows PE 및 전체 OS에서 실행됩니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDStateFallbackToNAA](/sccm/osd/understand/task-sequence-variables#OSDStateFallbackToNAA)  
 - [OSDStateSMPRetryCount](/sccm/osd/understand/task-sequence-variables#OSDStateSMPRetryCount)  
 - [OSDStateSMPRetryTime](/sccm/osd/understand/task-sequence-variables#OSDStateSMPRetryTime)  
 - [OSDStateStorePath](/sccm/osd/understand/task-sequence-variables#OSDStateStorePath)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **사용자 상태**를 선택한 다음, **사용자 상태 요청**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="capture-state-from-the-computer"></a>컴퓨터에서 상태 캡처
 상태 마이그레이션 지점 설정에서 구성된 최소 요구 사항을 충족하는 상태 마이그레이션 지점을 찾습니다. 예: **최대 클라이언트 수** 및 **사용 가능한 최소 디스크 공간** 이 옵션은 상태 마이그레이션 시 충분한 공간을 사용할 수 있도록 보장하지 않습니다. 이 옵션은 컴퓨터에서 사용자 상태 및 설정을 캡처하기 위해 상태 마이그레이션 지점에 대한 액세스를 요청합니다.  

 Configuration Manager 사이트에 여러 활성 상태 마이그레이션 지점이 있는 경우 이 단계에서는 사용 가능한 디스크 공간이 있는 상태 마이그레이션 지점을 찾습니다. 작업 순서는 관리 지점에 상태 마이그레이션 지점 목록을 쿼리한 다음, 최소 요구 사항을 충족하는 항목을 찾을 때까지 각 항목을 평가합니다.  

#### <a name="restore-state-from-another-computer"></a>다른 컴퓨터에서 상태 복원
 이전에 캡처한 사용자 상태 및 설정을 대상 컴퓨터로 복원하기 위해 상태 마이그레이션 지점에 대한 액세스를 요청합니다.  

 여러 상태 마이그레이션 지점이 있는 경우 이 단계는 대상 컴퓨터에 대한 상태가 있는 상태 마이그레이션 지점을 찾습니다.  

#### <a name="number-of-retries"></a>다시 시도 횟수
 이 단계가 실패하기 전에 적절한 상태 마이그레이션 지점을 찾으려고 시도하는 횟수입니다.  

#### <a name="retry-delay-in-seconds"></a>다시 시도 지연 시간(초)
 작업 순서 단계가 다시 시도하기 전에 대기할 시간(초)입니다.  

#### <a name="if-computer-account-fails-to-connect-to-a-state-store-use-the-network-access-account"></a>컴퓨터 계정에서 상태 저장소에 연결하지 못하는 경우 네트워크 액세스 계정 사용
 작업 순서에서 컴퓨터 계정을 사용하여 상태 마이그레이션 지점에 액세스할 수 없는 경우 네트워크 액세스 계정 자격 증명을 사용하여 연결합니다. 다른 컴퓨터가 네트워크 액세스 계정을 사용하여 저장된 상태에 액세스할 수 있기 때문에 이 옵션은 비교적 안전하지 않습니다. 대상 컴퓨터가 도메인에 조인되어 있지 않은 경우 이 옵션이 필요할 수 있습니다.  



##  <a name="BKMK_RestartComputer"></a> 컴퓨터 다시 시작  

 이 단계를 사용하여 작업 순서를 실행하는 컴퓨터를 다시 시작합니다. 다시 시작되면 컴퓨터에서 작업 순서의 다음 단계로 자동으로 계속 진행합니다.  

 이 단계는 전체 OS 또는 Windows PE에서 실행할 수 있습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [SMSRebootMessage](/sccm/osd/understand/task-sequence-variables#SMSRebootMessage)  
 - [SMSRebootTimeout](/sccm/osd/understand/task-sequence-variables#SMSRebootTimeout)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **컴퓨터 다시 시작**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="the-boot-image-assigned-to-this-task-sequence"></a>이 작업 순서에 할당된 부팅 이미지
 대상 컴퓨터에서 작업 순서에 할당된 부팅 이미지를 사용하려면 이 옵션을 선택합니다. 작업 순서는 부팅 이미지를 사용하여 Windows PE에서 후속 단계를 실행합니다.  

#### <a name="the-currently-installed-default-operating-system"></a>현재 설치된 기본 운영 체제
 대상 컴퓨터를 설치된 OS로 다시 부팅하려면 이 옵션을 선택합니다.  

#### <a name="notify-the-user-before-restarting"></a>다시 시작하기 전에 사용자에게 알림
 대상 컴퓨터가 다시 시작되기 전에 사용자에게 알림을 표시하려면 이 옵션을 선택합니다. 이 단계는 기본적으로 이 옵션을 선택합니다.  

#### <a name="notification-message"></a>알림 메시지
 대상 컴퓨터가 다시 시작되기 전에 사용자에게 표시할 알림 메시지를 입력합니다.  

#### <a name="message-display-time-out"></a>메시지 표시 제한 시간
 대상 컴퓨터가 다시 시작되기까지 걸리는 시간(초)을 지정합니다. 기본값은 60초입니다.  



##  <a name="BKMK_RestoreUserState"></a> 사용자 상태 복원  

 이 단계를 사용하여 사용자 상태 및 설정을 대상 컴퓨터에 복원하기 위해 USMT(사용자 상태 마이그레이션 도구)를 시작합니다. 이 단계는 **사용자 상태 캡처** 단계와 함께 사용합니다.  

 운영 체제를 배포할 때 사용자 상태를 관리하는 방법에 대한 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  

 **상태 저장소 요청** 및 **상태 저장소 해제** 단계와 함께 이 단계를 사용하여 상태 마이그레이션 지점이 있는 상태 설정을 저장하거나 복원합니다. 이 옵션은 항상 Configuration Manager에서 생성 및 관리되는 암호화 키를 사용하여 USMT 상태 저장소의 암호를 해독합니다.  

 **사용자 상태 복원** 단계는 가장 일반적으로 사용되는 USMT 옵션의 제한된 하위 집합을 제어합니다. **OSDMigrateAdditionalRestoreOptions** 변수를 사용하여 명령줄 옵션을 추가로 지정합니다.  

 > [!IMPORTANT]  
 >  OS 배포 시나리오와 관련이 없는 용도로 이 단계를 사용하는 경우 **사용자 상태 복원** 단계 바로 다음에 [컴퓨터 다시 시작](#BKMK_RestartComputer) 단계를 추가합니다.  

 이 단계는 전체 OS에서만 실행됩니다. Windows PE에서는 실행되지 않습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [_OSDMigrateUsmtRestorePackageID](/sccm/osd/understand/task-sequence-variables#OSDMigrateUsmtRestorePackageID)  
 - [OSDMigrateAdditionalRestoreOptions](/sccm/osd/understand/task-sequence-variables#OSDMigrateAdditionalRestoreOptions)  
 - [OSDMigrateContinueOnRestore](/sccm/osd/understand/task-sequence-variables#OSDMigrateContinueOnRestore)  
 - [OSDMigrateEnableVerboseLogging](/sccm/osd/understand/task-sequence-variables#OSDMigrateEnableVerboseLogging)  
 - [OSDMigrateLocalAccounts](/sccm/osd/understand/task-sequence-variables#OSDMigrateLocalAccounts)  
 - [OSDMigrateLocalAccountPassword](/sccm/osd/understand/task-sequence-variables#OSDMigrateLocalAccountPassword)  
 - [OSDStateStorePath](/sccm/osd/understand/task-sequence-variables#OSDStateStorePath)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **사용자 상태**를 선택한 다음, **사용자 상태 복원**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="user-state-migration-tool-package"></a>사용자 환경 마이그레이션 도구 패키지
 이 단계에서 사용할 USMT 버전이 포함된 패키지를 지정합니다. 이 패키지에는 프로그램이 필요하지 않습니다. 단계가 실행되면 작업 순서에서 지정된 패키지의 USMT 버전을 사용합니다. 32비트 또는 64비트 버전의 USMT가 포함된 패키지를 지정합니다. USMT의 아키텍처는 작업 순서에서 상태를 복원하는 OS의 아키텍처에 따라 달라집니다. 

#### <a name="restore-all-captured-user-profiles-with-standard-options"></a>캡처된 모든 사용자 프로필을 표준 옵션으로 복원
 캡처된 사용자 프로필을 표준 옵션으로 복원합니다. USMT에서 복원하는 옵션을 사용자 지정하려면 **사용자 프로필 캡처 사용자 지정**을 선택합니다.  

#### <a name="customize-how-user-profiles-are-restored"></a>사용자 프로필 복원 방식을 사용자 지정
 대상 컴퓨터로 복원할 파일을 사용자 지정할 수 있습니다. **파일** 을 클릭하여 USMT 패키지에서 사용자 프로필을 복원하는 데 사용할 구성 파일을 지정합니다. 구성 파일을 추가하려면 **파일 이름** 상자에 파일 이름을 입력하고 **추가**를 클릭합니다. [파일] 창에는 USMT에서 사용하는 구성 파일이 나열됩니다. 지정한 .xml 파일은 USMT에서 복원하는 사용자 파일을 정의합니다.  

#### <a name="restore-local-computer-user-profiles"></a>로컬 컴퓨터 사용자 프로필 복원
 로컬 컴퓨터 사용자 프로필을 복원합니다. 이러한 프로필은 도메인 사용자를 위한 프로필이 아닙니다. 복원된 로컬 사용자 계정에는 새 암호를 할당하세요. USMT가 원래 암호는 마이그레이션할 수 없습니다. **암호** 상자에 새 암호를 입력하고 **암호 확인** 상자에서 암호를 확인합니다.  

#### <a name="continue-if-some-files-cannot-be-restored"></a>일부 파일을 복원할 수 없는 경우 계속
 USMT에서 일부 파일을 복원할 수 없는 경우에도 사용자 상태 및 설정을 계속 복원합니다. 이 단계는 기본적으로 이 옵션을 사용하도록 설정합니다. 이 옵션을 사용하지 않도록 설정하고 USMT에서 파일을 복원하는 동안 오류가 발생하면 이 단계가 즉시 실패합니다. USMT가 모든 파일을 복원하지는 않습니다.   

#### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용
 자세한 로그 파일 정보를 생성하려면 이 옵션을 선택합니다. 상태를 복원할 때 작업 순서는 기본적으로 `%WinDir%\ccm\logs` 작업 순서 로그 폴더에 **Loadstate.log**를 생성합니다.  



##  <a name="BKMK_RunCommandLine"></a> 명령줄 실행  

 이 단계를 사용하여 지정된 명령줄을 실행합니다.  

 이 단계는 전체 OS 또는 Windows PE에서 실행할 수 있습니다.   

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [OSDDoNotLogCommand](/sccm/osd/understand/task-sequence-variables#OSDDoNotLogCommand)(버전 1806부터 적용)<!--1358493-->  
 - [SMSTSDisableWow64Redirection](/sccm/osd/understand/task-sequence-variables#SMSTSDisableWow64Redirection)  
 - [SMSTSRunCommandLineUserName](/sccm/osd/understand/task-sequence-variables#SMSTSRunCommandLineUserName)  
 - [SMSTSRunCommandLinePassword](/sccm/osd/understand/task-sequence-variables#SMSTSRunCommandLinePassword)  
 - [WorkingDirectory](/sccm/osd/understand/task-sequence-variables#WorkingDirectory)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **명령줄 실행**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="command-line"></a>명령줄
 작업 순서가 실행되는 명령줄을 지정합니다. 이 필드는 필수 필드입니다. 파일 이름 확장명을 포함하세요(예: .vbs 및 .exe). 모든 필수 설정 파일 및 명령줄 옵션을 포함합니다.  

 파일 이름 확장명을 지정하지 않는 경우 Configuration Manager에서는 .com, .exe 및 .bat를 사용합니다. 파일 이름에 실행할 수 있는 유형이 아닌 확장명이 있는 경우에는 Configuration Manager에서 로컬 연결을 적용합니다. 예를 들어 명령줄이 readme.gif인 경우 Configuration Manager는 .gif 파일을 열기 위해 대상 컴퓨터에 지정된 애플리케이션을 시작합니다.  

 예제:  

 `setup.exe /a`  

 `cmd.exe /c copy Jan98.dat c:\sales\Jan98.dat`  

 > [!NOTE]  
 >  성공적으로 실행하려면 명령줄 동작 앞에 **cmd.exe /c** 명령을 사용합니다. 이러한 동작의 예로, 출력 리디렉션, 파이핑 및 복사 명령이 있습니다.  

#### <a name="disable-64-bit-file-system-redirection"></a>64비트 파일 시스템 리디렉션 사용 안 함
 기본적으로 64비트 운영 체제는 WOW64 파일 시스템 리디렉터를 사용하여 명령줄을 실행합니다. 이 동작은 32비트 버전의 OS 실행 파일과 라이브러리를 제대로 찾는 것입니다. WOW64 파일 시스템 리디렉터를 사용하지 않도록 설정하려면 이 옵션을 선택합니다. Windows는 OS 실행 파일과 라이브러리의 네이티브 64비트 버전을 사용하여 명령을 실행합니다. 이 옵션은 32비트 OS에서 실행하는 경우 아무런 영향을 주지 않습니다.  

#### <a name="start-in"></a>시작 위치
 프로그램의 실행 가능한 폴더를 지정합니다(최대 127자). 이 폴더는 대상 클라이언트의 절대 경로 또는 패키지가 포함된 배포 지점 폴더의 상대 경로일 수 있습니다. 이 필드는 선택 항목입니다.  

 예제:  

 `c:\officexp`  

 `i386`  

 > [!NOTE]  
 >  **찾아보기** 단추는 로컬 컴퓨터에서 파일과 폴더를 찾습니다. 선택하는 모든 항목이 대상 컴퓨터에 존재해야 합니다. 동일한 위치에 동일한 파일 및 폴더 이름으로 존재해야 합니다.  

#### <a name="package"></a>패키지
 명령줄에서 대상 컴퓨터에 이미 존재하지 않는 파일 또는 프로그램을 지정한 경우 이 옵션을 선택하여 필요한 파일이 포함된 Configuration Manager 패키지를 지정할 수 있습니다. 패키지에는 프로그램이 필요하지 않습니다. 지정한 파일이 대상 컴퓨터에 있는 경우에는 이 옵션이 필요하지 않습니다.  

#### <a name="time-out"></a>시간 제한
 Configuration Manager에서 명령줄을 실행할 수 있는 기간을 나타내는 값을 지정합니다. 이 값은 1분에서 999분 사이일 수 있습니다. 기본값은 15분입니다. 이 옵션은 기본적으로 사용되지 않습니다.  

 > [!IMPORTANT]  
 >  지정된 명령이 성공적으로 완료되기까지 충분한 시간을 허용하지 않는 값을 입력하면 이 단계가 실패합니다. 단계 또는 그룹 조건에 따라 전체 작업 순서가 실패할 수도 있습니다. 시간 제한이 만료되면 Configuration Manager에서 명령줄 프로세스를 종료합니다.  

#### <a name="run-this-step-as-the-following-account"></a>이 단계를 다음 계정으로 실행
 명령줄이 로컬 시스템 계정 이외의 다른 Windows 사용자 계정으로 실행되도록 지정합니다.  

 > [!NOTE]  
 >  OS를 설치한 후 다른 계정으로 간단한 스크립트 또는 명령을 실행하려면 먼저 해당 계정을 컴퓨터에 추가하세요. 또한 Windows Installer와 같이 더 복잡한 프로그램을 실행하려면 Windows 사용자 프로필을 복원해야 할 수 있습니다.  

#### <a name="account"></a>계정
 이 단계에서 명령줄을 실행하는 데 사용하는 Windows 사용자 계정을 지정합니다. 명령줄은 지정된 계정의 권한으로 실행됩니다. **설정** 을 클릭하여 로컬 사용자 또는 도메인 계정을 지정합니다. 작업 순서 실행 계정에 대한 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-run-as-account)을 참조하세요.

 > [!IMPORTANT]  
 >  이 단계에서 사용자 계정을 지정하고 Windows PE에서 실행하면 동작이 실패합니다. Windows PE는 도메인에 조인할 수 없습니다. **smsts.log** 파일은 이 실패를 기록합니다.  



##  <a name="BKMK_RunPowerShellScript"></a> PowerShell 스크립트 실행  

 이 단계를 사용하여 지정된 Windows PowerShell 스크립트를 실행합니다.  

 이 단계는 전체 OS 또는 Windows PE에서 실행할 수 있습니다. Windows PE에서 이 단계를 실행하려면 부팅 이미지에서 PowerShell을 사용하도록 설정합니다. 부팅 이미지에 대한 속성의 **선택적 구성 요소** 탭에서 WinPE-PowerShell 구성 요소를 사용하도록 설정하세요. 부팅 이미지를 수정하는 방법에 대한 자세한 내용은 [부팅 이미지 관리](/sccm/osd/get-started/manage-boot-images)를 참조하세요.  

 > [!NOTE]  
 >  PowerShell은 Windows Embedded 운영 체제에서는 기본적으로 사용되지 않습니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **PowerShell 스크립트 실행**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="package"></a>패키지
 Configuration Manager PowerShell 스크립트가 포함된 패키지를 지정합니다. 하나의 패키지에 여러 PowerShell 스크립트가 포함될 수 있습니다.  

#### <a name="script-name"></a>스크립트 이름
 실행할 PowerShell 스크립트의 이름을 지정합니다. 이 필드는 필수 필드입니다.  

#### <a name="parameters"></a>매개 변수
 PowerShell 스크립트에 전달된 매개 변수를 지정합니다. 이러한 매개 변수는 명령줄의 PowerShell 스크립트 매개 변수와 동일합니다.  

 > [!IMPORTANT]  
 >  Windows PowerShell 명령줄이 아니라 스크립트에서 사용되는 매개 변수를 제공합니다.  
 >   
 >  올바른 매개 변수의 예는 다음과 같습니다.  
 >   
 >  `-MyParameter1 MyValue1 -MyParameter2 MyValue2`  
 >   
 >  잘못된 매개 변수의 예는 다음과 같습니다. 처음 두 항목은 Windows PowerShell 명령줄 매개 변수(**-NoLogo** 및 **-ExecutionPolicy Unrestricted**)입니다. 스크립트는 이러한 매개 변수를 사용하지 않습니다.  
 >   
 >  `-NoLogo -ExecutionPolicy Unrestricted -File MyScript.ps1 -MyParameter1 MyValue1 -MyParameter2 MyValue2`  

#### <a name="powershell-execution-policy"></a>PowerShell 실행 정책
 컴퓨터에서 실행할 수 있는 PowerShell 스크립트(있는 경우)를 결정합니다. 다음 실행 정책 중 하나를 선택합니다.  

 -   **AllSigned**: 신뢰할 수 있는 게시자가 서명한 스크립트만 실행합니다.  

 -   **Undefined**: 모든 실행 정책을 정의하지 않습니다.  

 -   **Bypass**: 모든 구성 파일을 로드하고 모든 스크립트를 실행합니다. 인터넷에서 서명되지 않은 스크립트를 다운로드하는 경우, 스크립트를 실행하기 전에 Windows PowerShell에서 권한을 요청하는 메시지를 표시하지 않습니다.  


 > [!IMPORTANT]  
 >  PowerShell 1.0에서는 정의되지 않음 및 무시 실행 정책을 지원하지 않습니다.  



##  <a name="child-task-sequence"></a> 작업 순서 실행

 > [!Note]  
 > Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능을 사용하려면 먼저 활성화합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.

 Configuration Manager 버전 1710부터 다른 작업 순서를 실행하는 새 단계를 추가할 수 있습니다. 이 단계는 작업 순서 간에 부모-자식 관계를 만듭니다. 자식 작업 순서를 사용하면 재사용 가능한 모듈식 작업 순서를 만들 수 있습니다.

 작업 순서에 자식 작업 순서를 추가할 때는 다음 사항을 고려하세요.  

 - 부모 및 자식 작업 순서는 실제로는 클라이언트가 실행하는 단일 정책으로 결합됩니다.  

 - 전역 환경이 사용됩니다. 부모 작업 순서에서 변수를 설정하고 하위 작업 순서에서 해당 변수를 변경하면 최신 값이 유지됩니다. 자식 작업 순서에서 새 변수를 만들면 나머지 부모 작업 순서에서 사용할 수 있습니다.  

 - 상태 메시지는 단일 작업 순서 작업에 대해 일반적인 방식을 사용할 때마다 전송됩니다.  

 - 작업 순서는 **smsts.log** 파일에 항목을 쓰며 자식 작업 순서가 시작될 때 새 로그 항목이 추가되므로 해당 작업 순서를 쉽게 확인할 수 있습니다.  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **작업 순서 실행**을 선택합니다. 


### <a name="properties"></a>속성

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="select-task-sequence-to-run"></a>실행할 작업 순서 선택
 **찾아보기**를 클릭하여 자식 작업 순서를 선택합니다. **작업 순서 선택** 대화 상자에는 부모 작업 순서가 표시되지 않습니다.



##  <a name="BKMK_SetDynamicVariables"></a> 동적 변수 설정  

 이 단계를 사용하여 다음 동작을 수행합니다.  

 1.  컴퓨터와 해당 환경에서 정보를 수집합니다. 그런 다음 이 정보로 지정된 작업 순서 변수를 설정하세요.  

 2.  정의된 규칙을 평가합니다. True로 평가되는 규칙을 기준으로 작업 순서 변수를 설정하세요.  


 작업 순서에서는 다음 읽기 전용 작업 순서 변수를 자동으로 설정합니다.  
 - [\_SMSTSMake](/sccm/osd/understand/task-sequence-variables#SMSTSMake)  
 - [\_SMSTSModel](/sccm/osd/understand/task-sequence-variables#SMSTSModel)  
 - [\_SMSTSMacAddresses](/sccm/osd/understand/task-sequence-variables#SMSTSMacAddresses)  
 - [\_SMSTSIPAddresses](/sccm/osd/understand/task-sequence-variables#SMSTSIPAddresses)  
 - [\_SMSTSSerialNumber](/sccm/osd/understand/task-sequence-variables#SMSTSSerialNumber)  
 - [\_SMSTSAssetTag](/sccm/osd/understand/task-sequence-variables#SMSTSAssetTag)  
 - [\_SMSTSUUID](/sccm/osd/understand/task-sequence-variables#SMSTSUUID)  


 이 단계는 전체 OS 또는 Windows PE에서 실행할 수 있습니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **동적 변수 설정**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="dynamic-rules-and-variables"></a>동적 규칙 및 변수
 작업 순서에 사용할 동적 변수를 설정하려면 규칙을 추가합니다. 그런 다음 규칙에 지정된 각 변수에 대한 값을 설정합니다. 또한 규칙을 추가하지 않고 하나 이상의 변수를 추가합니다. 규칙을 추가하는 경우 다음 규칙 범주에서 선택할 수 있습니다.  

 - **컴퓨터**: 하드웨어 자산 태그, UUID, 일련 번호 또는 MAC 주소에 대한 값을 평가합니다. 필요에 따라 여러 값을 설정합니다. 값이 true이면 규칙이 true로 평가됩니다. 예를 들어 디바이스 일련 번호가 5892087이고 MAC 주소가 22-A4-5A-13-78-26인 경우 다음 규칙은 true로 평가됩니다.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

 - **위치**: 기본 네트워크 게이트웨이에 대한 값을 평가합니다.  

 - **제조사 및 모델**: 컴퓨터의 제조업체 및 모델에 대한 값을 평가합니다. 규칙이 true로 평가되려면 제조업체와 모델 둘 다 true로 평가되어야 합니다.   

    별표(`*`) 및 물음표(`?`)를 와일드카드 문자로 지정합니다. 별표는 여러 문자를 찾고, 물음표는 단일 문자를 찾습니다. 예를 들어 `DELL*900?` 문자열은 `DELL-ABC-9001`과 `DELL9009`를 모두 찾습니다.  

 - **작업 순서 변수**: 평가할 작업 순서 변수, 조건 및 값을 추가합니다. 변수에 대해 설정된 값이 지정된 조건을 충족하면 규칙이 true로 평가됩니다.  

    true로 평가되는 규칙에 대해 설정할 하나 이상의 변수를 지정하거나, 규칙을 사용하지 않고 변수를 설정합니다. 기존 변수를 선택하거나 사용자 지정 변수를 만듭니다.  

     - **기존 작업 순서 변수**: 기존 작업 순서 변수 목록에서 하나 이상의 변수를 선택합니다. 배열 변수는 선택할 수 없습니다.  

     - **사용자 지정 작업 순서 변수**: 사용자 지정 작업 순서 변수를 정의합니다. 또한 기존 작업 순서 변수를 지정할 수 있습니다. 이 설정은 기존 작업 순서 변수 목록에 배열 변수가 없으므로 **OSDAdapter**와 같은 기존 변수 배열을 지정하는 데 유용합니다.  


 규칙의 변수를 선택한 후에는 각 변수 값을 제공하세요. 규칙이 true로 평가되면 변수가 지정된 값으로 설정됩니다. 각 변수에 대해 **비밀 값** 을 선택하여 변수 값을 숨길 수 있습니다. 기본적으로 일부 기존 변수는 값을 숨깁니다(예: **OSDCaptureAccountPassword** 변수).  

 > [!IMPORTANT]  
 >  Configuration Manager는 **동적 변수 설정** 단계를 사용하여 작업 순서를 가져올 때 **비밀 값**으로 표시된 모든 변수 값을 제거합니다. 작업 순서를 가져온 후 동적 변수 값을 다시 입력합니다.  



##  <a name="BKMK_SetTaskSequenceVariable"></a> 작업 순서 변수 설정  

 이 단계를 사용하여 작업 순서에서 사용되는 변수 값을 설정합니다.  

 이 단계는 전체 OS 또는 Windows PE에서 실행할 수 있습니다. 

 작업 순서 변수는 작업 순서 동작에서 읽으며, 이러한 동작을 지정합니다. 특정 작업 순서 변수 및 사용 방법에 대한 자세한 내용은 다음 문서를 참조하세요.  
 - [작업 순서 변수 사용 방법](/sccm/osd/understand/using-task-sequence-variables)  
 - [작업 순서 변수](/sccm/osd/understand/task-sequence-variables)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **일반**을 선택한 다음, **작업 순서 변수 설정**을 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="task-sequence-variable"></a>작업 순서 변수
 작업 순서 기본 제공 또는 동작 변수의 이름을 지정하거나 사용자 정의 변수 이름을 지정합니다.  

#### <a name="do-not-display-this-value"></a>이 값 표시 안 함
 <!--1358330--> 버전 1806부터 작업 순서 변수에 저장된 중요한 데이터를 마스킹하려면 이 옵션을 사용하도록 설정하세요. 예를 들어 암호를 지정하는 경우입니다. 

#### <a name="value"></a>값  
 작업 순서는 변수를 이 값으로 설정합니다. 이 작업 순서 변수를 `%varname%` 구문을 사용하여 다른 작업 순서 변수의 값으로 설정합니다.  



##  <a name="BKMK_SetupWindowsandConfigMgr"></a> Windows 및 ConfigMgr 설치  

 이 단계를 사용하여 Windows PE에서 새 OS로 전환합니다. 이 작업 순서 단계는 임의의 OS 배포 중 필요합니다. 구성 관리자 클라이언트를 새 OS에 설치하고 새 OS에서 작업 순서를 계속 실행하도록 준비합니다.  

 이 단계는 Windows PE에서만 실행됩니다. 전체 OS에서는 실행되지 않습니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [SMSClientInstallProperties](/sccm/osd/understand/task-sequence-variables#SMSClientInstallProperties)  


 이 단계는 sysprep.inf 또는 unattend.xml 디렉터리 변수(예: `%WINDIR%` 및 `%ProgramFiles%`)를 Windows PE 설치 디렉터리인 `X:\Windows`로 바꿉니다. 작업 순서는 이러한 환경 변수를 사용하여 지정된 변수를 무시합니다.  

 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **Windows 및 ConfigMgr 설치**를 선택합니다. 


### <a name="step-actions"></a>단계 작업

 이 단계에서는 다음 작업을 수행합니다.  

#### <a name="preliminaries-windows-pe"></a>준비 단계: Windows PE  

 1.  unattend.xml 파일의 작업 순서 변수를 대체합니다.  

 2.  구성 관리자 클라이언트가 포함된 패키지를 다운로드합니다. 배포된 이미지에 패키지를 추가합니다.  

#### <a name="set-up-windows"></a>Windows 설치  

 -  이미지 기반 설치  

    1.  이미지에 구성 관리자 클라이언트가 있는 경우 이를 사용하지 않도록 설정합니다. 즉, 구성 관리자 클라이언트 서비스에 대해 자동 시작을 사용하지 않도록 설정합니다.  

    2.  배포된 이미지에서 레지스트리를 업데이트하여 참조 컴퓨터와 동일한 드라이브 문자로 배포된 OS를 시작합니다.  

    3.  배포된 OS로 다시 시작합니다.  

    4.  모든 최종 사용자 상호 작용이 억제되어 있는 이전에 지정한 sysprep.inf 또는 unattend.xml 응답 파일을 사용하여 Windows 최소 설치가 실행됩니다. **네트워크 설정 적용** 단계를 사용하여 도메인에 조인하면 해당 정보가 응답 파일에 있습니다. Windows 최소 설치는 컴퓨터를 도메인에 조인합니다.  

 -  Setup.exe 기반 설치. 일반적인 Windows 설치 프로그램 프로세스를 따르는 Setup.exe를 실행합니다.  

    1.  **운영 체제 적용** 단계에서 지정한 OS 업그레이드 패키지를 하드 디스크 드라이브에 복사합니다.  

    2.  새로 배포된 OS로 다시 시작합니다.  

    3.  모든 사용자 인터페이스 설정이 억제되어 있는 이전에 지정한 sysprep.inf 또는 unattend.xml 응답 파일을 사용하여 Windows 최소 설치가 실행됩니다. **네트워크 설정 적용** 단계를 사용하여 도메인에 조인하면 해당 정보가 응답 파일에 있습니다. Windows 최소 설치는 컴퓨터를 도메인에 조인합니다.  

#### <a name="set-up-the-configuration-manager-client"></a>Configuration Manager 클라이언트 설정  

 1.  Windows 최소 설치가 완료되면 setupcomplete.cmd를 사용하여 작업 순서가 다시 시작됩니다.  

 2.  **Windows 설정 적용** 단계에서 선택한 옵션에 따라 로컬 관리자 계정을 사용하거나 사용하지 않도록 설정합니다.  

 3.  이전에 다운로드한 패키지 및 이 단계에서 지정한 설치 속성을 사용하여 구성 관리자 클라이언트를 설치합니다. 클라이언트는 "프로비전 모드"로 설치됩니다. 이 모드는 클라이언트가 작업 순서가 완료되기 전까지 새 정책 요청을 처리하지 않도록 합니다.  

 4.  클라이언트가 정상적으로 작동할 때까지 기다립니다.  

#### <a name="the-step-completes"></a>단계가 완료됩니다.
 작업 순서는 다음 단계를 계속 실행합니다.  

<!-- Engineering confirmed that the task sequence does nothing with respect to group policy processing.
> [!NOTE]  
>  The **Setup Windows and ConfigMgr** task sequence action is responsible for running Group Policy on the newly installed computer. The Group Policy is applied after the task sequence is finished.  
-->


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="client-package"></a>클라이언트 패키지
 **찾아보기**를 클릭한 다음, 이 단계에서 사용할 구성 관리자 클라이언트 설치 패키지를 선택합니다.  

#### <a name="use-pre-production-client-package-when-available"></a>사용 가능한 경우 사전 프로덕션 클라이언트 패키지를 사용합니다.
 사용할 수 있는 사전 프로덕션 클라이언트 패키지가 있고 컴퓨터가 파일럿 컬렉션의 구성원인 경우, 작업 순서는 프로덕션 클라이언트 패키지 대신 이 패키지를 사용합니다. 사전 프로덕션 클라이언트는 프로덕션 환경에서 테스트하기 위한 최신 버전입니다. **찾아보기**를 클릭한 다음, 이 단계에서 사용할 사전 프로덕션 클라이언트 설치 패키지를 선택합니다.  

#### <a name="installation-properties"></a>설치 속성
 작업 순서 단계에서 사이트 할당 및 기본 구성을 자동으로 지정합니다. 클라이언트를 설치할 때 사용할 모든 추가 설치 속성을 지정하려면 이 필드를 사용하세요. 여러 설치 속성을 입력하려면 공백으로 구분합니다.  

 클라이언트 설치 중에 사용할 명령줄 옵션을 지정하세요. 예를 들어 Microsoft Silverlight 필수 조건을 설치하지 않도록 CCMSetup.exe에 알리려면 `/skipprereq: silverlight.exe`를 입력합니다. CCMSetup.exe의 사용 가능한 명령줄 옵션에 대한 자세한 내용은 [클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  


### <a name="options"></a>Options

 > [!NOTE]  
 > **옵션** 탭에서 **오류 발생 시 계속**을 사용하지 않도록 설정합니다. 이 단계에서 오류가 발생하면 이 설정을 사용할지 여부에 관계없이 작업 순서가 실패합니다.  



##  <a name="BKMK_UpgradeOS"></a> 운영 체제 업그레이드  

 > [!TIP]  
 > Windows 10 버전 1709부터 미디어에는 여러 버전이 포함되어 있습니다. OS 업그레이드 패키지 또는 OS 이미지를 사용하도록 작업 순서를 구성하는 경우 [지원되는 버전](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)을 선택해야 합니다.  

 이 단계를 사용하여 이전 버전의 Windows를 최신 버전의 Windows 10으로 업그레이드합니다.  

 이 작업 순서 단계는 전체 OS에서만 실행되고, Windows PE에서는 실행되지 않습니다.  

 이 단계에 다음 작업 순서 변수를 사용하세요.  
 - [_SMSTSOSUpgradeActionReturnCode](/sccm/osd/understand/task-sequence-variables#SMSTSOSUpgradeActionReturnCode)  
 - [OSDSetupAdditionalUpgradeOptions](/sccm/osd/understand/task-sequence-variables#OSDSetupAdditionalUpgradeOptions)  


 작업 순서 편집기에서 이 단계를 추가하려면 **추가**를 클릭하고, **이미지**를 선택한 다음, **운영 체제 업그레이드**를 선택합니다. 


### <a name="properties"></a>속성  

 이 단계에 대한 **속성** 탭에서 이 섹션에서 설명하는 설정을 구성합니다.  

#### <a name="upgrade-package"></a>패키지 업그레이드
 업그레이드를 위해 사용할 Windows 10 OS 업그레이드 패키지를 지정하려면 이 옵션을 선택합니다.  

#### <a name="source-path"></a>소스 경로
 Windows 설치 프로그램에서 사용하는 Windows 10 미디어에 대한 로컬 또는 네트워크 경로를 지정합니다. 이 설정은 Windows 설치 프로그램의 `/InstallFrom` 명령줄 옵션에 해당합니다. 

 `%MyContentPath%` 또는 `%DPC01%`과 같은 변수를 지정할 수도 있습니다. 원본 경로에 대한 변수를 사용하는 경우 작업 순서의 앞 부분에서 해당 값을 설정하세요. 예를 들어 OS 업그레이드 패키지의 위치에 대한 변수를 지정하려면 [패키지 콘텐츠 다운로드](#BKMK_DownloadPackageContent) 단계를 사용하세요. 그런 다음 이 단계의 원본 경로에 대해 해당 변수를 사용합니다.  

#### <a name="edition"></a>버전
 업그레이드에 사용하기 위해 OS 미디어 내에서 버전을 지정합니다.  

#### <a name="product-key"></a>제품 키
 업그레이드 프로세스에 적용할 제품 키를 지정합니다.  

#### <a name="provide-the-following-driver-content-to-windows-setup-during-upgrade"></a>업그레이드하는 동안 다음 드라이버 콘텐츠를 Windows 설치 프로그램에 제공합니다.
 업그레이드 프로세스 중에 드라이버를 대상 컴퓨터에 추가합니다. 이 설정은 Windows 설치 프로그램의 `/InstallDriver` 명령줄 옵션에 해당합니다. 드라이버는 Windows 10과 호환되어야 합니다. 다음 옵션 중 하나를 지정합니다.  

 - **드라이버 패키지**: **찾아보기** 를 클릭하고 목록에서 기존 드라이버 패키지를 선택합니다.  

 - **준비된 콘텐츠**: 드라이버 패키지의 위치를 지정하려면 이 옵션을 선택합니다. 로컬 폴더, 네트워크 경로 또는 작업 순서 변수를 지정할 수 있습니다. 원본 경로에 대한 변수를 사용하는 경우 작업 순서의 앞 부분에서 해당 값을 설정하세요. 예를 들어 [패키지 콘텐츠 다운로드](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent) 단계를 사용합니다.  

#### <a name="time-out-minutes"></a>시간 제한(분)
 Configuration Manager가 이 단계를 실패하기 전까지의 시간(분)을 지정합니다. 이 옵션은 Windows 설치 프로그램에서 처리를 중지하지만 종료하지 않는 경우에 유용합니다.  

#### <a name="perform-windows-setup-compatibility-scan-without-starting-upgrade"></a>업그레이드를 시작하지 않고 Windows 설치 프로그램 호환성 검사 수행
 업그레이드 프로세스를 시작하지 않고 Windows 설치 프로그램 호환성 검사를 수행합니다. 이 설정은 Windows 설치 프로그램의 `/Compat ScanOnly` 명령줄 옵션에 해당합니다. 이 옵션을 사용하여 전체 OS 업그레이드 패키지를 배포하세요. 

 <!--SCCMDocs-pr issue 2812--> 버전 1806부터는 이 옵션을 사용하도록 설정하는 경우 이 단계에서 구성 관리자 클라이언트가 프로비전 모드에 들어가지 않습니다. Windows 설치 프로그램은 백그라운드에서 자동으로 실행되며 클라이언트는 계속 정상적으로 작동합니다. 

 설치에서 검색 결과로 종료 코드를 반환합니다. 다음 표에서 보다 일반적인 종료 코드 중 일부를 제공합니다.  

 |종료 코드|세부 정보|  
 |-|-|  
 |MOSETUP_E_COMPAT_SCANONLY (0xC1900210)|호환성 문제가 없습니다("성공").|  
 |MOSETUP_E_COMPAT_INSTALLREQ_BLOCK(0xC1900208)|실행 가능한 호환성 문제입니다.|  
 |MOSETUP_E_COMPAT_MIGCHOICE_BLOCK(0xC1900204)|선택한 마이그레이션 선택을 사용할 수 없습니다. 예를 들어 Enterprise에서 Professional로의 업그레이드입니다.|  
 |MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)|Windows 10에 적합하지 않습니다.|  
 |MOSETUP_E_COMPAT_INSTALLDISKSPACE_BLOCK(0xC190020E)|사용 가능한 디스크 공간이 부족합니다.|  

 이 매개 변수에 대한 자세한 내용은 [Windows 설치 프로그램 명령줄 옵션](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-setup-command-line-options#6)을 참조하세요.  

#### <a name="ignore-any-dismissible-compatibility-messages"></a>해제 가능한 호환성 메시지는 무시합니다.
 설치 프로그램이 설치를 완료하고 무시할 수 있는 호환성 메시지를 무시하도록 지정합니다. 이 설정은 Windows 설치 프로그램의 `/Compat IgnoreWarning` 명령줄 옵션에 해당합니다.  

#### <a name="dynamically-update-windows-setup-with-windows-update"></a>Windows 업데이트를 사용하여 동적으로 Windows 설치 프로그램 업데이트
 설치 프로그램에서 동적 업데이트 작업(예: 업데이트 검색, 다운로드 및 설치)을 수행할 수 있도록 설정합니다. 이 설정은 Windows 설치 프로그램의 `/DynamicUpdate` 명령줄 옵션에 해당합니다. 이 설정은 Configuration Manager 소프트웨어 업데이트와 호환되지 않습니다. 독립 실행형 WSUS(Windows Server Update Services) 또는 비즈니스용 Windows 업데이트를 사용하여 업데이트를 관리하는 경우 이 옵션을 사용합니다.  

#### <a name="override-policy-and-use-default-microsoft-update"></a>정책을 무시하고 기본 Microsoft 업데이트 사용
 동적 업데이트 작업을 실행하도록 일시적으로 로컬 정책을 실시간으로 재정의합니다. 컴퓨터는 Windows 업데이트에서 업데이트를 받습니다.
