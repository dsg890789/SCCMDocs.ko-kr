---
title: SMS 공급자에 대한 계획
titleSuffix: Configuration Manager
description: Configuration Manager의 SMS 공급 기업 사이트 시스템 역할에 대해 알아봅니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d59e5e5bc1dfdf962517b4c364b74aa0df6b650a
ms.sourcegitcommit: 94bf7d5b5beb9628cc1fdfe75451d33b5de26f8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152454"
---
# <a name="plan-for-the-sms-provider"></a>SMS 공급자에 대한 계획 

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 관리하려면 Configuration Manager 콘솔을 사용하여 **SMS 공급 기업**의 인스턴스에 연결합니다. 기본적으로 SMS 공급자는 중앙 관리 사이트나 기본 사이트를 설치할 때 사이트 서버에 설치됩니다. 



##  <a name="BKMK_PlanSMSProv"></a> SMS 공급자 정보  

SMS 공급 기업은 사이트의 Configuration Manager 데이터베이스에 **읽기** 및 **쓰기** 권한을 할당하는 WMI(Windows Management Instrumentation) 공급 기업입니다.  

- 각 중앙 관리 사이트 및 기본 사이트에는 SMS 공급자가 하나 이상 있어야 합니다. 필요에 따라 추가 공급자를 설치할 수 있습니다.  

- **SMS Admins** 보안 그룹은 SMS 공급자에 대한 액세스를 제공합니다. Configuration Manager는 사이트 서버와 SMS 공급자 인스턴스를 설치하는 각 컴퓨터에 자동으로 이 그룹을 만듭니다. 자세한 내용은 [SMS 관리자](/sccm/core/plan-design/hierarchy/accounts#sms-admins)를 참조하세요.  

- 보조 사이트에서는 SMS 공급 기업 역할을 지원하지 않습니다.  

Configuration Manager 관리자는 SMS 공급 기업을 사용하여 데이터베이스에 저장된 정보에 액세스합니다. 관리자는 이 작업을 위해 Configuration Manager 콘솔, 리소스 탐색기, 도구 및 사용자 지정 스크립트를 사용할 수 있습니다. SMS 공급 기업은 Configuration Manager 클라이언트와 상호 작용하지 않습니다. Configuration Manager 콘솔은 사이트에 연결할 때 사이트 서버에서 WMI를 쿼리하여 사용할 SMS 공급 기업의 인스턴스를 찾습니다.  

SMS 공급자는 Configuration Manager 보안을 적용하는 데 도움이 됩니다. SMS 공급 기업은 콘솔 사용자에게 보기 권한이 부여됐다는 정보만 반환합니다.  

> [!IMPORTANT]  
>  사이트에 대한 SMS 공급 기업의 각 인스턴스가 오프라인 상태인 경우 Configuration Manager 콘솔은 해당 사이트에 연결할 수 없습니다.  

 SMS 공급 기업을 관리하는 방법에 대한 자세한 내용은 [SMS 공급 기업 관리](/sccm/core/servers/manage/modify-your-infrastructure#BKMK_ManageSMSprovider)를 참조하세요.  



## <a name="installation-prerequisites"></a>설치 필수 구성 요소  

 SMS 공급 기업을 지원하려면 대상 서버가 다음 필수 조건을 충족해야 합니다.  

-   사이트 서버 및 사이트 데이터베이스 사이트 시스템과 양방향 트러스트 관계가 있는 도메인에 있어야 함  

-   다른 사이트의 사이트 시스템 역할을 보유할 수 없습니다.  

-   모든 사이트의 SMS 공급 기업을 보유할 수 없습니다.  

-   지원되는 OS 버전 실행  

-   Windows ADK 구성 요소를 지원하려면 디스크 공간에 650MB 이상의 여유가 있어야 합니다. Windows ADK 및 SMS 공급 기업에 대한 자세한 내용은 [OS 배포 요구 사항](#BKMK_WAIKforSMSProv)을 참조하세요.  



##  <a name="bkmk_location"></a> 위치  

사이트를 설치할 때, 사이트의 첫 번째 SMS 공급자를 자동으로 설치합니다. SMS 공급자에 대해 다음과 같은 지원되는 위치를 지정할 수 있습니다.  

-   사이트 서버  

-   사이트 데이터베이스 서버  

-   [설치 필수 조건](#installation-prerequisites)을 충족하는 다른 서버  


사이트에 대한 각 SMS 공급 기업의 위치를 확인하려면 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장한 다음, **사이트** 노드를 선택합니다.  

2. 목록에서 원하는 사이트를 선택한 다음, 리본에서 **속성**을 선택합니다.  

3. 사이트 **속성**의 **일반** 탭에서 **SMS 공급 기업 위치**를 확인합니다.    


각 SMS 공급자에서 여러 요청의 동시 연결을 지원합니다. 이러한 연결에 대한 제한 사항은 Windows에 사용할 수 있는 서버 연결 수 및 서버에서 연결 요청을 처리하기 위한 사용 가능한 리소스입니다.  

사이트를 설치한 후 사이트 서버에서 Configuration Manager 설치 프로그램을 다시 실행할 수 있습니다. 설치 프로그램을 사용하여 기존 SMS 공급 기업의 위치를 변경하거나 해당 사이트에 추가 SMS 공급 기업을 설치합니다. 컴퓨터 하나당 SMS 기업 하나만 설치합니다. 컴퓨터는 하나를 초과하는 사이트에서 SMS 공급 기업을 호스팅할 수 없습니다.  


### <a name="choosing-a-location"></a>위치 선택 

다음 섹션에서는 지원되는 각 위치마다 SMS 공급 기업을 설치하는 방식의 장단점에 대해 설명합니다.  

#### <a name="configuration-manager-site-server"></a>Configuration Manager 사이트 서버

- **장점:**  

    -   SMS 공급 기업은 사이트 데이터베이스 컴퓨터의 시스템 리소스를 사용하지 않습니다.  

    -   이 위치를 통해 사이트 서버 또는 사이트 데이터베이스 컴퓨터가 아닌 컴퓨터에 배치된 SMS 공급자보다 더 나은 성능을 낼 수 있습니다.  

- **단점:**  

    -   SMS 공급자는 사이트 서버 작업에 전용으로 사용될 수 있는 시스템 및 네트워크 리소스를 사용합니다.  


#### <a name="sql-server-that-hosts-the-site-database"></a>사이트 데이터베이스를 호스팅하는 SQL 서버

- **장점:**  

    -   SMS 공급 기업은 사이트 서버에서 시스템 리소스를 사용하지 않습니다.  

    -   충분한 서버 리소스를 사용할 수 있는 경우 이 위치는 세 위치 중 최상의 성능을 낼 수 있습니다.  

- **단점:**  

    -   SMS 공급자는 사이트 데이터베이스 작업에 전용으로 사용될 수 있는 시스템 및 네트워크 리소스를 사용합니다.  

    -   사이트 데이터베이스가 SQL Server의 클러스터된 인스턴스에서 호스트되는 경우에는 이 위치를 사용할 수 없습니다.  


#### <a name="computer-other-than-the-site-server-or-site-database-server"></a>사이트 서버 또는 사이트 데이터베이스 서버가 아닌 컴퓨터

- **장점:**  

    -   SMS 공급 기업은 사이트 서버 또는 사이트 데이터베이스 시스템 리소스를 사용하지 않습니다.  

    -   이러한 유형의 위치를 사용하면 추가 SMS 공급자를 배포하여 고가용성 연결을 구현할 수 있습니다.  

- **단점:**  

    -   SMS 공급 기업 성능이 축소될 수 있습니다. 이 동작은 사이트 서버 및 사이트 데이터베이스 컴퓨터와 조정하기 위해 필요한 추가 네트워크 활동 때문입니다.  

    -   이 서버는 사이트 데이터베이스 서버 및 Configuration Manager 콘솔이 설치된 모든 컴퓨터에 항상 액세스할 수 있어야 합니다.  

    -   이 위치에서는 원래 다른 서비스에 전용으로 사용될 시스템 리소스를 사용할 수 있습니다.  



## <a name="bkmk_auth"></a> 인증
<!--1357013-->

1810 버전부터 관리자가 Configuration Manager 사이트에 액세스하는 데 필요한 최소 인증 수준을 지정할 수 있습니다. 이 기능은 관리자에게 필요한 수준으로 Windows에 로그인하도록 요구합니다. 이 기능은 SMS 공급 기업에 액세스하는 모든 구성 요소에 적용됩니다. 예를 들어 Configuration Manager 콘솔, SDK 메서드 및 Windows PowerShell cmdlet에 적용됩니다. 


### <a name="configure-authentication"></a>인증 구성

이 설정을 구성하려면 먼저 필요한 인증 수준을 사용하여 Windows에 로그인합니다. 

> [!Important]  
> 이 구성은 계층 구조 범위 설정입니다. 이 설정을 변경하기 전에 모든 Configuration Manager 관리자가 필요한 인증 수준을 사용하여 Windows에 로그인할 수 있는지 확인합니다. 

이 설정을 구성하려면 다음 단계를 사용합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 리본에서 **계층 구조 설정**을 선택합니다.  

3. **인증** 탭으로 전환합니다. 원하는 [인증 수준](#authentication-levels)을 선택한 다음, **확인**을 선택합니다.  

    - 필요한 경우에만 **추가**를 선택하여 특정 사용자 또는 그룹을 제외합니다. 자세한 내용은 [제외](#exclusions)를 참조하세요.  


### <a name="authentication-levels"></a>인증 수준

다음 수준을 사용할 수 있습니다.

- **Windows 인증**: Active Directory 도메인 자격 증명으로 인증해야 합니다. 이 설정은 이전 동작이고 현재 기본 설정입니다. 사이트를 업데이트할 때 인증 수준은 변경되지 않았습니다.  

- **인증서 인증**: 신뢰할 수 있는 PKI 인증 기관에서 발급한 유효한 인증서를 사용하여 인증해야 합니다. Configuration Manager에서는 이 인증서를 구성하지 않았습니다. Configuration Manager는 관리자에게 PKI를 사용하여 Windows에 로그인하도록 요구합니다.  

- **비즈니스용 Windows Hello 인증**: 디바이스에 연결되고 생체 인식 또는 PIN을 사용하는 강력한 2단계 인증을 사용하여 인증해야 합니다. 자세한 내용은 [비즈니스용 Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)를 참조하세요.   


### <a name="exclusions"></a>제외

계층 구조 설정의 **인증** 탭에서 특정 사용자 또는 그룹을 제외할 수도 있습니다. 이 옵션은 신중하게 사용하세요. 예를 들면 특정 사용자가 Configuration Manager 콘솔에 액세스해야 하지만 필요한 수준에서 Windows에 인증할 수 없는 경우입니다. 시스템 계정의 컨텍스트에서 실행되는 자동화 또는 서비스에 필요할 수도 있습니다.



##  <a name="BKMK_SMSProvLanguages"></a> SMS 공급자 언어 정보  

SMS 공급 기업은 사용자가 설치하는 서버의 표시 언어와 독립적으로 작동합니다.  

관리자 또는 Configuration Manager 프로세스에서 SMS 공급 기업을 사용하여 데이터를 요청하는 경우 SMS 공급 기업은 요청하는 컴퓨터의 OS 언어와 일치하는 형식으로 해당 데이터의 반환을 시도합니다.

SMS 공급 기업이 언어와 일치하려는 방법은 간접적입니다. SMS 공급 기업은 정보를 한 언어에서 다른 언어로 변환하지 않습니다. SMS 공급 기업이 Configuration Manager 콘솔에 표시되기 위해 데이터를 반환하는 경우 데이터의 표시 언어는 개체 및 스토리지 유형의 원본에 따라 달라집니다.  

Configuration Manager가 데이터베이스의 개체에 대한 데이터를 저장하는 경우 사용 가능한 언어는 다음 요인에 따라 달라집니다.  

-   Configuration Manager는 다중 언어 지원을 통해 만드는 개체를 저장합니다. 또한 설치 프로그램을 실행하는 경우 사이트에 대해 구성한 언어를 사용하여 개체를 사이트 데이터베이스에 저장합니다. 개체에 대해 해당 언어가 사용 가능한 경우 Configuration Manager 콘솔은 요청하는 컴퓨터의 표시 언어로 이러한 개체를 표시합니다. 콘솔이 표시 언어로 개체를 표시할 수 없는 경우 기본 언어인 영어로 개체를 표시합니다.  

-   Configuration Manager는 해당 개체를 만드는 데 사용된 언어로 관리자가 만드는 개체를 저장합니다. 이 개체는 Configuration Manager 콘솔에 동일한 언어로 표시됩니다. SMS 공급 기업은 이러한 개체를 변환할 수 없으며 해당 개체에는 다중 언어 옵션이 없습니다.  



##  <a name="BKMK_MultiSMSProv"></a> 다중 SMS 공급자 사용  

 사이트 설치가 완료되면 사이트에 대한 추가 SMS 공급자를 설치할 수 있습니다. 추가 SMS 공급 기업을 설치하려면 사이트 서버에서 Configuration Manager 설치 프로그램을 실행합니다. 

다음 조건 중 하나라도 true인 경우 추가 SMS 공급 기업을 설치하는 것이 좋습니다.  

- 다수의 관리자가 동시에 Configuration Manager 콘솔을 사용하고 사이트에 연결해야 합니다.  

- SMS 공급 기업을 자주 호출할 수 있는 Configuration Manager SDK 또는 기타 제품을 사용합니다.  

- SMS 공급 기업의 고가용성을 위한 비즈니스 요구 사항이 있습니다.  

사이트에 여러 SMS 공급 기업을 설치하고 연결 요청이 발생하는 경우 사이트에서 각 새 연결 요청이 설치된 SMS 공급 기업을 사용하도록 무작위로 할당합니다. 특정 연결 세션과 함께 사용할 SMS 공급 기업을 지정할 수 없습니다.  

> [!NOTE]  
>  각 SMS 공급자 위치의 장단점을 고려하세요. 자세한 내용은 [위치](#bkmk_location)를 참조하세요. 각 새 연결에 SMS 공급 기업을 사용하는 이러한 고려 사항과 제어할 수 없는 정보의 균형을 맞춥니다.  

먼저 Configuration Manager 콜솔을 사이트에 연결하는 경우 해당 연결은 사이트 서버의 WMI를 쿼리합니다. 이 쿼리는 콘솔이 사용하는 SMS 공급 기업의 인스턴스를 식별합니다. SMS 공급 기업의 이 특정 인스턴스는 세션이 종료될 때까지 콘솔에 의해 사용 중인 상태로 유지됩니다. SMS 공급 기업 서버를 네트워크에서 사용할 수 없어 세션이 종료되는 경우 사이트에 콘솔을 다시 연결하면 초기 쿼리를 반복합니다. 사용할 수 없는 동일한 SMS 공급 기업 인스턴스를 사이트에서 할당할 수 있습니다. 이 동작이 발생하는 경우 사이트에서 사용 가능한 SMS 공급 기업을 반환할 때까지 콘솔의 다시 연결을 시도합니다.  



##  <a name="BKMK_SMSProvNamespace"></a> SMS 공급자 네임스페이스 정보  

Configuration Manager WMI 스키마는 SMS 공급 기업의 구조를 정의합니다. 스키마 네임스페이스는 SMS 공급자 스키마 내 Configuration Manager 데이터의 위치를 설명합니다. 다음 테이블에서는 SMS 공급 기업이 사용하는 공용 네임스페이스의 일부를 보여줍니다.  

|네임스페이스|설명|  
|---------------|-----------------|  
|`Root\SMS\site_<site code>`|Configuration Manager 콘솔, 리소스 탐색기, Configuration Manager 도구 및 스크립트에 광범위하게 사용되는 SMS 공급자입니다.|  
|`Root\SMS\SMS_ProviderLocation`|사이트의 SMS 공급자 컴퓨터 위치입니다.|  
|`Root\CIMv2`|하드웨어 및 소프트웨어 인벤토리 도중 WMI 네임스페이스 정보가 인벤토리에 저장되는 위치입니다.|  
|`Root\CCM`|Configuration Manager 클라이언트 구성 정책 및 클라이언트 데이터입니다.|  
|`Root\CIMv2\SMS`|인벤토리 클라이언트 에이전트에서 수집하는 인벤토리 보고 클래스의 위치입니다. 클라이언트는 컴퓨터 정책을 평가하는 중에 이러한 설정을 컴파일합니다. 이러한 설정은 컴퓨터에 대한 클라이언트 설정 구성에 따릅니다.|  



##  <a name="BKMK_WAIKforSMSProv"></a> OS 배포 요구 사항

SMS 공급자의 인스턴스를 설치한 컴퓨터에는 지원되는 버전의 Windows ADK가 필요합니다.  

이 요구 사항에 대한 자세한 내용은 [OS 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment#windows-adk-for-windows-10) 및 [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)을 참조하세요.  

OS 배포를 관리하는 경우 Windows ADK를 사용하면 SMS 공급 기업에서 다음과 같은 다양한 작업을 완료할 수 있습니다.  

-   WIM 파일 정보 보기  

-   기존 부팅 이미지에 드라이버 파일 추가  

-   부팅 ISO 파일 만들기  


Windows ADK를 설치하려면 SMS 공급자를 설치하는 각 컴퓨터에 최대 650MB의 사용 가능한 디스크 공간이 필요합니다. 이 많은 디스크 공간은 Configuration Manager가 Windows PE 부팅 이미지를 설치하는 데 필요합니다.  
