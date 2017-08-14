---
title: "업그레이드 준비 | System Center Configuration Manager"
description: "업그레이드 준비를 Configuration Manager와 통합합니다. 관리 콘솔에서 업그레이드 호환성 데이터에 액세스합니다. 업그레이드 또는 수정 대상 장치를 지정합니다."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 7/31/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: HT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: b1f4cd4a6f19a02d2b2dc3f9a841aeeb2a1403dd
ms.contentlocale: ko-kr
ms.lasthandoff: 07/29/2017

---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>업그레이드 준비를 System Center Configuration Manager와 통합

*적용 대상: System Center Configuration Manager(현재 분기)*

업그레이드 준비(이전의 Upgrade Analytics)를 사용하면 Windows 10과의 장치 준비 상태를 평가하고 분석할 수 있습니다. 업그레이드 준비를 Configuration Manager와 통합하면 Configuration Manager 관리 콘솔에서 클라이언트 업그레이드 호환성 데이터에 액세스할 수 있습니다. 장치 목록에서 업그레이드 또는 수정 대상 장치를 지정할 수 있습니다.

업그레이드 준비는 Microsoft OMS(Operations Management Suite)의 솔루션입니다. 업그레이드 준비에 대한 자세한 내용은 [Get started with Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)(업그레이드 준비 시작)를 참조하세요.

## <a name="configure-clients"></a>클라이언트 구성

클라이언트가 업그레이드 준비에 데이터를 제공할 수 있는지 확인하기 위해 수행해야 하는 여러 구성 단계가 있습니다.

-  [조직에서 Windows 원격 분석 구성](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization)에 설명된 대로 클라이언트 원격 분석 설정을 구성합니다.
-  [업그레이드 준비 시작](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)의 *호환성 업데이트 및 관련 기술 자료 배포* 섹션에 설명된 기술 자료를 설치합니다.

    > [!NOTE]
    > 다양한 클라이언트 설치 작업을 자동화하는 스크립트를 다운로드할 수 있습니다. 스크립트에 대한 자세한 내용은 [Get started with Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)(업그레이드 준비 시작)의 *Run the Upgrade Readiness deployment script*(업그레이드 준비 배포 스크립트 실행) 섹션을 참조하세요.

## <a name="connect-to-upgrade-readiness"></a>업그레이드 준비에 연결

### <a name="prerequisites"></a>전제 조건

현재 분기 버전 1706부터 Azure 서비스 마법사를 사용해서 Configuration Manager에서 사용하도록 Azure 서비스를 구성하는 과정을 단순화할 수 있습니다. 이 마법사를 사용 하려면 Azure Web App을 구성해야 합니다. 자세한 내용은 [Azure 서비스 마법사](/sccm/core/servers/deploy/configureazure-services-wizard)를 참조하세요.

### <a name="use-the-azure-wizard-to-create-the-connection"></a>Azure 마법사를 사용하여 연결 만들기

1.  Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장한 후 **Azure 서비스**를 클릭합니다.
2.  **홈** 탭의 **Azure 서비스** 그룹에서 **Azure 서비스 구성**을 클릭합니다.
3.  Azure 서비스 페이지에 이름을 입력합니다. 설명을 입력할 수도 있습니다. 그런 후 **업그레이드 준비 커넥터**를 선택하고 **다음**을 클릭합니다.
4.  앱 페이지에서 Azure 환경을 지정합니다. **찾아보기**를 클릭하여 서버 앱을 설치합니다.
5.  **가져오기**를 클릭하여 Azure의 웹앱에 연결합니다.
    -  **Azure AD 테넌트 이름**을 입력합니다.
    -  **Azure AD 테넌트 ID**를 입력합니다.
    -  **응용 프로그램 이름**을 입력합니다.
    -  **클라이언트 ID**를 입력합니다.
    -  **비밀 키**를 입력합니다.
    -  **비밀 키 만료** 날짜를 선택합니다.
    -  **응용 프로그램 ID URI**의 URL을 입력합니다.
    -  **확인**을 클릭한 후 **확인**을 클릭합니다.

6.  구성 페이지에서 업그레이드 준비에 대한 연결을 지정합니다. 다음 값을 선택합니다.  
    -  Azure 구독
    -  Azure 리소스 그룹
    -  Windows Analytics 작업 영역
8.  **다음**을 클릭합니다. 요약 페이지에서 연결을 검토할 수 있습니다. 

## <a name="complete-upgrade-readiness-tasks"></a>업그레이드 준비 작업 완료  

연결을 만든 후 [업그레이드 준비 시작](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)에 설명된 대로 이러한 작업을 수행합니다.  

1. OMS 작업 영역에 UpgradeReadiness 서비스를 추가합니다.  
2. 상용 ID를 생성합니다.  
3. 업그레이드 준비를 구독합니다.   

## <a name="use-the-upgrade-readiness-deployment-script"></a>업그레이드 준비 배포 스크립트 사용  

다양한 업그레이드 준비 작업을 자동화하고 Microsoft  **배포 스크립트**를 사용하여 데이터 공유 문제를 해결할 수 있습니다.  
업그레이드 준비 배포 스크립트는 다음을 수행합니다.  

- 상용 ID 키 + CommercialDataOptIn + RequestAllAppraiserVersions 키를 설정합니다.  
- 사용자 컴퓨터가 데이터를 Microsoft에 보낼 수 있는지 확인합니다.  
- 컴퓨터에 보류 중인 다시 시작이 있는지 여부를 확인합니다.   
- 최신 버전의 KB 패키지 10.0.x가 설치되어 있는지 확인합니다(10.0.14913 또는 후속 릴리스가 필요함).  
- 사용할 경우 문제 해결을 위해 자세한 정보 표시 모드를 설정합니다.  
- Microsoft에서 조직의 업그레이드 준비 상태를 평가하는 데 필요한 원격 분석 데이터 수집을 시작합니다.  
- 사용하도록 설정된 경우 cmd 창에 스크립트 진행률이 표시됩니다. 이렇게 하면 문제에 대한 정보가 표시되고(각 단계에 대한 성공 또는 실패) 로그 파일에 기록됩니다.  

## <a name="to-run-the-upgrade-readiness-deployment-script"></a>업그레이드 준비 배포 스크립트를 실행하려면  

1. [업그레이드 준비 배포 스크립트](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409)를 다운로드하고 UpgradeReadiness.zip의 압축을 풉니다. **Diagnostics** 폴더의 파일은 문제 해결 모드로 스크립트를 실행하려는 경우에만 필요합니다.  
2. RunConfig.bat에서 다음 매개 변수를 편집합니다.  
- 로그 정보에 대한 저장소 위치. 예: %SystemDrive%\URDiagnostics. 원격 파일 공유 또는 로컬 디렉터리에 로그 정보를 저장할 수 있습니다. 스크립트는 지정된 경로에 대한 로그 파일을 만들 수 없도록 차단될 경우 Windows 디렉터리가 있는 드라이브에 로그 파일을 만듭니다.  
- 상용 ID 키.  
- 기본적으로 스크립트는 로그 정보를 콘솔과 로그 파일 둘 다에 보냅니다. 기본 동작을 변경하려면 다음 옵션 중 하나를 사용합니다.  
    - logMode = 0 콘솔에만 기록  
    - logMode = 1 파일 및 콘솔에 기록  
    - logMode = 2 파일에만 기록  
    - 문제 해결을 위해 **isVerboseLogging**을 **$true**로 설정하여 문제 진단에 도움이 되는 로그 정보를 생성합니다. 기본적으로 **isVerboseLogging**은 **$false**로 설정됩니다. Diagnostics 폴더는 이 모드를 사용할 스크립트와 동일한 디렉터리에 설치되어야 합니다.  
    - 컴퓨터를 다시 시작해야 하는 경우 사용자에게 알립니다. 기본적으로 off로 설정됩니다.  

3. RunConfig.bat에서 매개 변수 편집을 마친 후 관리자 권한으로 스크립트를 실행합니다.  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>Configuration Manager에서 Microsoft 업그레이드 준비 속성 보기  

1.  Configuration Manager 콘솔에서 **클라우드 서비스**로 이동한 다음 **OMS 커넥터**를 선택하여 **OMS 연결 속성** 페이지를 엽니다.  

2.  이 페이지에는 다음 두 개의 탭이 있습니다.
  * **Azure Active Directory** 탭에는 **테넌트**, **클라이언트 ID**, **클라이언트 비밀 키 만료**가 표시되며, 만료된 경우 **클라이언트 비밀 키**를 **확인**할 수 있습니다.
  * **업그레이드 준비** 탭에는 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**이 표시됩니다.

## <a name="view-and-use-the-upgrade-information"></a>업그레이드 정보 보기 및 사용

업그레이드 준비를 Configuration Manager와 통합한 후 클라이언트의 업그레이드 준비 상태 분석을 확인한 다음 작업을 수행할 수 있습니다.

1. Configuration Manager 콘솔에서 **모니터링** > **개요** > **업그레이드 준비**를 선택합니다.
2. 업그레이드 준비 상태 및 원격 분석을 보고 하는 Windows 장치 비율이 포함된 데이터를 검토합니다.
3. 대시보드를 필터링하여 특정 컬렉션의 장치에 대한 데이터를 볼 수 있습니다.
4. 특정 준비 상태의 장치를 보고, 준비된 경우 해당 장치를 업그레이드하거나 작업을 수행하여 준비 상태로 전환할 수 있도록 해당 장치에 대한 동적 컬렉션을 만듭니다.

## <a name="create-a-connection-to-upgrade-readiness-1702-and-earlier"></a>업그레이드 준비에 대한 연결 만들기(1702 및 이전 버전)

Configuration Manager의 1706 분기 전에는 업그레이드 준비에 대한 연결을 만들려면 다음 단계가 필요했습니다.

### <a name="prerequisites"></a>전제 조건

- 연결을 추가하려면 Configuration Manager 환경에서 먼저 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 [온라인 모드](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)로 구성해야 합니다. 사용자 환경에 연결을 추가하면 이 사이트 시스템 역할을 실행하는 컴퓨터에 Microsoft Monitoring Agent도 설치됩니다.
- Configuration Manager를 "웹 응용 프로그램 및/또는 Web API" 관리 도구로 등록하고 [이 등록의 클라이언트 ID](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/)를 받습니다.
- Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.
- Azure Portal에서 [Configuration Manager에 OMS에 대한 사용 권한 제공](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms)에 설명된 대로 OMS에 액세스할 수 있는 권한을 등록된 웹앱에 제공합니다.

    > [!IMPORTANT]
    > OMS에 액세스할 수 있는 권한을 구성하는 경우 **참가자** 역할을 선택하고 등록된 앱의 리소스 그룹에 사용 권한을 할당해야 합니다.

### <a name="create-the-connection"></a>연결 만들기

1.  Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **업그레이드 준비 커넥터** > **Upgrade Analytics에 대한 연결 만들기**를 선택하여 **Upgrade Analytics 연결 추가 마법사**를 시작합니다.
3.  **Azure Active Directory** 화면에서 **테넌트**, **클라이언트 ID** 및 **클라이언트 비밀 키**를 제공하고 **다음**을 선택합니다.
4.  **업그레이드 준비** 화면에서 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 정보를 입력하여 연결 설정을 제공합니다.
5.  **요약** 화면에서 연결 설정을 확인하고 **다음**을 선택합니다.

    > [!NOTE]
    > 계층 구조의 최상위 계층 사이트에 업그레이드 준비를 연결해야 합니다. 업그레이드 준비를 독립 실행형 기본 사이트에 연결한 다음 사용자 환경에 중앙 관리 사이트를 추가하는 경우 OMS 연결을 삭제하고 새 계층 구조 내에서 다시 만들어야 합니다.

