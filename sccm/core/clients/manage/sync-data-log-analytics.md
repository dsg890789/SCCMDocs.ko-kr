---
title: Log Analytics와 데이터 동기화
titleSuffix: Configuration Manager
description: Configuration Manager의 데이터를 Azure Log Analytics와 동기화합니다.
ms.date: 09/04/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b3ba4c5179069e5443beaf1b7f733c797cfd680
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56156528"
---
#  <a name="sync-data-from-configuration-manager-to-azure-log-analytics"></a>Configuration Manager의 데이터를 Azure Log Analytics와 동기화

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1258052--> **Azure 서비스 마법사**를 사용하여 Configuration Manager에서 Azure Log Analytics 클라우드 서비스로의 연결을 구성할 수 있습니다. 이 연결은 디바이스 컬렉션 데이터를 Log Analytics과 동기화합니다. 

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  

> [!TIP]
> Configuration Manager 1802부터는 Log Analytics 커넥터가 더 이상 시험판 기능이 아닙니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/pre-release-features)을 참조하세요.



## <a name="prerequisites-for-the-log-analytics-connector"></a>Log Analytics 커넥터에 대한 필수 구성 요소

> [!Note]  
> 이 문서는 *Log Analytics 커넥터*(이전의 *OMS 커넥터*)를 참조합니다. 기능 차이는 없습니다. 자세한 내용은 [Azure 관리 - 모니터링](https://docs.microsoft.com/azure/monitoring/#operations-management-suite)을 참조하세요.  

- Configuration Manager에서 Log Analytics 커넥터를 설치하기 전에 권한을 Configuration Manager에 제공해야 합니다. Log Analytics 작업 영역을 포함하는 Azure *리소스 그룹*에 *참가자 액세스 권한*을 부여합니다. 자세한 내용은 [Provide Configuration Manager with permissions to Log Analytics(Configuration Manager에 Log Analytics에 대한 권한 제공)](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#grant-configuration-manager-with-permissions-to-log-analytics)을 참조하세요.  

- Log Analytics 커넥터는 온라인 모드에서 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 호스팅하는 컴퓨터에 설치해야 합니다.  

- 커넥터와 함께 서비스 연결 지점에 설치된 Log Analytics에 대해 Microsoft Monitoring Agent를 설치합니다. 이 에이전트 및 커넥터는 동일한 Log Analytics 작업 영역을 사용하도록 구성합니다. 에이전트 설치에 대한 자세한 정보는 [에이전트 다운로드 및 설치](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent)를 참조하세요.  

- 커넥터와 에이전트를 설치한 후 Configuration Manager 데이터를 사용하도록 Log Analytics를 구성해야 합니다. 자세한 내용은 [Import Configuration Manager collections(Configuration Manager 컬렉션 가져오기)](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections)를 참조하세요.  



## <a name="configure-the-connection-to-log-analytics"></a>Log Analytics에 대한 연결 구성

**Azure 서비스 마법사**를 사용하여 Configuration Manager에서 Azure Log Analytics 클라우드 서비스로의 연결을 구성할 수 있습니다. 이 프로세스의 자세한 내용과 세부 정보는 [Azure 서비스 구성](https://docs.microsoft.com/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요. **OMS 커넥터**에 대한 마법사에서 옵션을 선택하세요. 

> [!Note]  
> 이 문서는 *Log Analytics 커넥터*(이전의 *OMS 커넥터*)를 참조합니다. 기능 차이는 없습니다. 자세한 내용은 [Azure 관리 - 모니터링](https://docs.microsoft.com/azure/monitoring/#operations-management-suite)을 참조하세요.  

다른 모든 절차를 성공적으로 완료한 경우 웹앱을 가져오면 **연결 구성** 화면의 정보가 자동으로 나타납니다. 연결 설정에 대한 정보가 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 대해 나타납니다.

마법사는 사용자가 입력한 정보를 사용하여 Log Analytics 서비스에 연결합니다. 클라우드 서비스와 동기화하려는 디바이스 컬렉션을 선택하고 **추가**를 클릭합니다.


## <a name="verify-the-connector-properties"></a>커넥터 속성 확인

Configuration Manager를 Log Analytics에 연결한 후 추가할 연결 속성을 보거나 컬렉션을 제거합니다. 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다.  

2. Log Analytics 연결을 선택합니다. 리본에서 **속성**을 선택합니다.  

속성 페이지에는 다음과 같은 두 개의 탭이 있습니다.  

#### <a name="azure-active-directory"></a>Azure Active Directory
이 탭에는 다음과 같은 속성이 표시됩니다. 
- **테넌트**  
- **클라이언트 ID**  
- **클라이언트 암호 키 만료**  

클라이언트 암호 키가 만료되었는지도 확인하세요.

#### <a name="connection-properties"></a>연결 속성
이 탭에는 다음과 같은 속성이 표시됩니다. 
- **Azure 구독**  
- **Azure 리소스 그룹**  
- **Log Analytics 작업 영역**  

**디바이스 컬렉션** 목록도 표시합니다. **추가** 및 **제거** 단추를 사용하여 동기화할 컬렉션을 수정합니다.
