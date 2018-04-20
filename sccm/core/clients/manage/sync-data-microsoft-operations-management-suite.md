---
title: OMS에 데이터 동기화
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화합니다.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: 9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4ac6d69d07e17946abefdc4f5b7d4a1a73385c44
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
#  <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화합니다.

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1258052-->
**Azure 서비스 마법사**를 사용하여 Configuration Manager에서 OMS(Operations Management Suite) 클라우드 서비스에 대한 연결을 구성할 수 있습니다. 버전 1706부터 마법사는 이 연결을 구성하기 위한 이전 워크플로를 대신합니다. 이전 버전에 대해서는 [Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화(1702 및 이전 버전)](#Sync-data-from-Configuration-Manager-to-the-Microsoft-Operations-Management-Suite-(1702-and-earlier))를 참조하세요.

-   이 마법사는 OMS, 비즈니스용 Microsoft Store, Azure AD(Azure Active Directory)와 같은 Configuration Manager용 클라우드 서비스를 구성하는 데 사용됩니다.  

-   Configuration Manager는 [Log Analytics](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) 또는 [업그레이드 준비](/sccm/core/clients/manage/upgrade/upgrade-analytics)와 같은 기능을 위해 OMS에 연결합니다.


> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  



## <a name="prerequisites-for-the-oms-connector"></a>OMS 커넥터에 대한 필수 구성 요소
OMS에 대한 연결을 구성하기 위한 필수 구성 요소는 [현재 분기 버전 1702에 대해 문서화](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#prerequisites)된 필수 구성 요소에서 달라졌습니다. 이 정보는 여기에도 설명되어 있습니다.  

-   Configuration Manager에서 OMS 커넥터를 설치하기 전에 OMS에 대한 권한을 Configuration Manager에 제공해야 합니다. 특히 OMS Log Analytics 작업 영역을 포함하는 Azure *리소스 그룹*에 *참여자 액세스 권한*을 부여해야 합니다. 이 작업을 수행하는 절차는 Log Analytics 콘텐츠에 설명되어 있습니다. OMS 문서에서 [구성 관리자에 OMS에 대한 사용 권한 제공](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms)을 참조하세요.

-   OMS 커넥터는 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 [온라인 모드](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation)에서 호스트하는 컴퓨터에 설치해야 합니다.

-   OMS 커넥터와 함께 서비스 연결 지점에 설치된 OMS에 대해 Microsoft Monitoring Agent를 설치해야 합니다. Agent 및 OMS 커넥터는 동일한 **OMS 작업 영역**을 사용하도록 구성해야 합니다. 에이전트를 설치하려면 OMS 문서에서 [에이전트 다운로드 및 설치](/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent)를 참조하세요.
-   커넥터와 에이전트를 설치한 후 Configuration Manager 데이터를 사용하도록 OMS를 구성해야 합니다. 이렇게 하려면 OMS 포털에서 [Configuration Manager 컬렉션을 가져옵니다](/azure/log-analytics/log-analytics-sccm#import-collections).

## <a name="use-the-azure-services-wizard-to-configure-the-connection-to-oms"></a>Azure 서비스 마법사를 사용하여 OMS에 대한 연결 구성

1.  콘솔에서 **관리** > **개요** > **클라우드 서비스** > **Azure 서비스**로 이동합니다. 리본의 **홈** 탭에서 **Azure 서비스 구성**을 선택하여 **Azure 서비스 마법사**를 시작합니다.

2.  **Azure 서비스** 페이지에서 Operation Management Suite 클라우드 서비스를 선택합니다. **Azure 서비스 이름**에 이름을 입력하고 원하는 경우 선택적 설명을 입력한 후 **다음**을 클릭합니다.

3.  **앱** 페이지에서 Azure 환경(기술 미리 보기는 공용 클라우드만 지원함)을 지정합니다. 그런 후 **찾아보기**를 클릭하여 서버 앱 창을 엽니다.

4.  웹앱을 선택합니다.

    -   **가져오기**: Azure 구독에 이미 있는 웹앱을 사용하려면 **가져오기**를 클릭합니다. 앱 및 테넌트의 이름을 입력합니다. Configuration Manager에서 사용할 테넌트 ID, 클라이언트 ID 및 Azure 웹앱의 비밀 키를 지정합니다. 정보를 **확인**한 후 **확인**을 클릭하여 계속합니다.   

    > [!NOTE]   
    > 이 미리 보기에서 OMS를 구성하는 경우 OMS는 웹앱에 대해서만 *import* 함수를 지원합니다. 새 웹앱을 만드는 것은 지원되지 않습니다. 마찬가지로 OMS에 대해 기존 앱을 재사용할 수 없습니다.

5.  다른 모든 절차를 성공적으로 완료한 경우 **OMS 연결 구성** 화면의 정보가 이 페이지에 자동으로 나타납니다. 연결 설정에 대한 정보가 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 대해 나타납니다.

6.  마법사는 사용자가 입력한 정보를 사용하여 OMS 서비스에 연결합니다. OMS와 동기화하려는 장치 컬렉션을 선택하고 **추가**를 클릭합니다.

7.  **요약** 화면에서 연결 설정을 확인하고 **다음**을 선택합니다. **진행률** 화면에 연결 상태가 표시되며 **완료**여야 합니다.

8.  마법사가 완료된 후 Configuration Manager 콘솔에는 **Operation Management Suite**가 **클라우드 서비스 유형**으로 표시됩니다.

## <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite-1702-and-earlier"></a>Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화합니다(1702 및 이전 버전).


*적용 대상: System Center Configuration Manager(1702 및 이전 버전)*

Microsoft OMS(Operations Management Suite) 커넥터를 사용하여 System Center Configuration Manager의 데이터(예: 사용자 컬렉션)를 Microsoft Azure의 OMS Log Analytics에 동기화할 수 있습니다. 커넥터를 통해 Configuration Manager 배포의 데이터가 OMS에 표시됩니다.
> [!TIP]
> Configuration Manager 1802부터는 OMS 커넥터가 더 이상 시험판 기능이 아닙니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

버전 1702부터 OMS 커넥터를 사용하여 Microsoft Azure Government 클라우드에 있는 OMS 작업 영역에 연결할 수 있습니다. 이렇게 하려면 OMS 커넥터를 설치하기 전에 구성 파일을 수정해야 합니다. 이 문서에서 [Azure Government 클라우드에서 OMS 커넥터 사용](#fairfaxconfig)을 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
- Configuration Manager에서 OMS 커넥터를 설치하기 전에 OMS에 대한 권한을 Configuration Manager에 제공해야 합니다. 특히 OMS Log Analytics 작업 영역을 포함하는 Azure *리소스 그룹*에 *참여자 액세스 권한*을 부여해야 합니다. 이 작업을 수행하는 절차는 Log Analytics 콘텐츠에 설명되어 있습니다. OMS 문서에서 [구성 관리자에 OMS에 대한 사용 권한 제공](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms)을 참조하세요.

- OMS 커넥터는 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 [온라인 모드](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation)에서 호스트하는 컴퓨터에 설치해야 합니다.

  OMS를 독립 실행형 기본 사이트에 연결했고 중앙 관리 사이트를 환경에 추가할 계획이라면 현재 연결을 삭제하고 새 중앙 관리 사이트에서 커넥터를 다시 구성해야 합니다.

- OMS 커넥터와 함께 서비스 연결 지점에 설치된 OMS에 대해 Microsoft Monitoring Agent를 설치해야 합니다.  Agent 및 OMS 커넥터는 동일한 **OMS 작업 영역**을 사용하도록 구성해야 합니다. 에이전트를 설치하려면 OMS 문서에서 [에이전트 다운로드 및 설치](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent)를 참조하세요.

- 커넥터와 에이전트를 설치한 후 Configuration Manager 데이터를 사용하도록 OMS를 구성해야 합니다.  이렇게 하려면 OMS 포털에서 [Configuration Manager 컬렉션을 가져옵니다](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections).



### <a name="install-the-oms-connector"></a>OMS 커넥터 설치  
1. Configuration Manager 콘솔에서 [시험판 기능을 사용하도록 계층 구조](/sccm/core/servers/manage/pre-release-features)를 구성하고 OMS 커넥터를 사용하도록 설정합니다.  
0
2. 그 다음에 **관리** > **Cloud Services** > **OMS 커넥터**로 이동합니다. 리본에서 [Operations Management Suite에 대한 연결 만들기]를 클릭합니다. 이 단계에서 **Operation Management Suite 연결 마법사**가 열립니다. **다음**을 선택합니다.  


3.  **일반** 페이지에서 다음 정보가 있는지 확인하고 **다음**을 선택합니다.  
  - Configuration Manager를 "웹 응용 프로그램 및/또는 웹 API" 관리 도구로 등록했으며 [이 등록의 클라이언트 ID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)가 있습니다.  
  - Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.  

  - Azure Portal에서 [Configuration Manager에 OMS에 대한 사용 권한 제공](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms)에 설명된 대로 OMS에 액세스할 수 있는 권한을 등록된 웹앱에 제공합니다.  

4.  **Azure Active Directory** 페이지에서 해당 **테넌트**, **클라이언트 ID** 및 **클라이언트 비밀 키**를 제공하여 OMS에 대한 연결 설정을 구성하고 **다음**을 선택합니다.  

5.  **OMS 연결 구성** 페이지에서 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 정보를 입력하여 연결 설정을 제공합니다.  작업 영역은 서비스 연결 지점에 설치된 Microsoft Management Agent에 대해 구성된 작업 영역과 일치해야 합니다.  

6.  **요약** 페이지에서 연결 설정을 확인하고 **다음**을 선택합니다. **진행률** 페이지에 연결 상태가 표시되며 **완료**여야 합니다.

Configuration Manager를 OMS에 연결한 후 컬렉션을 추가하거나 제거하고 OMS 연결의 속성을 볼 수 있습니다.

### <a name="verify-the-oms-connector-properties"></a>OMS 커넥터 속성 확인
1.  Configuration Manager 콘솔에서 **관리** > **Cloud Services**로 이동하고 **OMS 커넥터**를 선택하여 **OMS 연결 페이지**를 선택합니다.
2.  이 페이지에는 다음 두 개의 탭이 있습니다.
  - **Azure Active Directory:** 
  
     이 탭에는 **테넌트**, **클라이언트 ID**, **클라이언트 비밀 키 만료**가 표시되며, 만료된 경우 클라이언트 비밀 키를 확인할 수 있습니다.

  - **OMS 연결 속성:**  

     이 탭에는 **Azure 구독**, **Azure 리소스 그룹**, **Operations Management Suite 작업 영역**과 **Operations Management Suite에서 데이터를 가져올 수 있는 장치 컬렉션 목록**이 표시됩니다. **추가** 및 **제거** 단추를 사용하여 허용되는 컬렉션을 수정합니다.

### <a name="fairfaxconfig"> </a> Azure Government 클라우드에서 OMS 커넥터 사용


1.  Configuration Manager 콘솔이 설치되어 있는 컴퓨터에서 Government 클라우드를 가리키도록 다음 구성 파일을 편집합니다. ***&lt;CM 설치 경로>\AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **편집:**

    설정 이름 *FairFaxArmResourceID*의 값을 "https://management.usgovcloudapi.net/"으로 변경합니다.

   - **원래 값:** &lt;setting name="FairFaxArmResourceId" serializeAs="String">   
      &lt;value>&lt;/value>   
      &lt;/setting>

   - **편집된 값:**     
      &lt;setting name="FairFaxArmResourceId" serializeAs="String"> &lt;value>https://management.usgovcloudapi.net/&lt;/value>  
      &lt;/setting>

  설정 이름 *FairFaxAuthorityResource*의 값을 "https://login.microsoftonline.us/"로 변경합니다.

  - **원래 값:** &lt;setting name="FairFaxAuthorityResource" serializeAs="String">   
    &lt;value>&lt;/value>

    - **편집된 값:** &lt;setting name="FairFaxAuthorityResource" serializeAs="String">   
    &lt;value>https://login.microsoftonline.us/&lt;/value>

2.  두 가지 사항을 변경하고 파일을 저장한 후 동일한 컴퓨터에서 Configuration Manager 콘솔을 다시 시작하고 해당 콘솔을 사용하여 OMS 커넥터를 설치합니다. 커넥터를 설치하려면 [Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)에 제공된 정보를 사용하고 Microsoft Azure Government 클라우드에 있는 **Operations Management Suite 작업 영역**을 선택합니다.

3.  OMS 커넥터가 설치되면 사이트에 연결하는 모든 콘솔에서 Government 클라우드에 대한 연결을 사용할 수 있습니다.
