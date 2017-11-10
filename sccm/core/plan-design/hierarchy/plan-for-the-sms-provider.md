---
title: "SMS 공급자 계획"
titleSuffix: Configuration Manager
description: "SMS 공급자를 사용하여 System Center Configuration Manager를 관리하는 방법에 대해 알아봅니다."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5ee2ebea24fed329a4e5974c67d95c6d854484e2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="plan-for-the-sms-provider-for-system-center-configuration-manager"></a>System Center Configuration Manager용 SMS 공급자에 대한 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 관리하려면 **SMS 공급자**의 인스턴스에 연결하는 Configuration Manager 콘솔을 사용합니다. 기본적으로 SMS 공급자는 중앙 관리 사이트나 기본 사이트를 설치할 때 사이트 서버에 설치됩니다. 


##  <a name="BKMK_PlanSMSProv"></a> SMS 공급자 정보  
 SMS 공급자는 사이트의 Configuration Manager 데이터베이스에 **읽기** 및 **쓰기** 권한을 할당하는 WMI(Windows Management Instrumentation) 공급자입니다.  

-   각 중앙 관리 사이트 및 기본 사이트에는 SMS 공급자가 하나 이상 있어야 합니다. 필요에 따라 추가 공급자를 설치할 수 있습니다.  
-   **SMS Admins** 보안 그룹은 SMS 공급자에 대한 액세스를 제공합니다. Configuration Manager는 사이트 서버와 SMS 공급자 인스턴스를 설치하는 각 컴퓨터에 자동으로 이 그룹을 만듭니다.  

-   보조 사이트에서는 SMS 공급자를 지원하지 않습니다.  


Configuration Manager 관리자는 SMS 공급자를 사용하여 데이터베이스에 저장된 정보에 액세스합니다. 관리자는 이 작업을 위해 Configuration Manager 콘솔, 리소스 탐색기, 도구 및 사용자 지정 스크립트를 사용할 수 있습니다. SMS 공급자는 Configuration Manager 클라이언트와 상호 작용하지 않습니다. Configuration Manager 콘솔에서 사이트에 연결할 때 Configuration Manager 콘솔은 사이트 서버에서 WMI를 쿼리하여 사용할 SMS 공급자의 인스턴스를 찾습니다.  

 SMS 공급자는 Configuration Manager 보안을 적용하는 데 도움이 됩니다. SMS 공급자는 Configuration Manager 콘솔을 실행하는 관리자가 보기 권한이 있다는 정보만 반환합니다.  

> [!IMPORTANT]  
>  사이트에 대한 SMS 공급자를 보유하는 각 컴퓨터가 오프라인 상태인 경우 Configuration Manager 콘솔은 해당 사이트의 데이터베이스에 연결할 수 없습니다.  

 SMS 공급자를 관리하는 방법에 대한 자세한 내용은 [Modify your System Center Configuration Manager infrastructure](../../../core/servers/manage/modify-your-infrastructure.md)(System Center Configuration Manager 인프라 수정)의 [Manage the SMS Provider](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider)(SMS 공급자 관리)를 참조하세요.  

## <a name="prerequisites-to-install-the-sms-provider"></a>SMS 공급자를 설치하기 위한 필수 구성 요소  

 SMS 공급자를 지원하려면  

-   컴퓨터는 사이트 서버 및 사이트 데이터베이스 사이트 시스템과 양방향 트러스트 관계가 있는 도메인에 있어야 합니다.  

-   컴퓨터는 다른 사이트의 사이트 시스템 역할을 보유해서는 안됩니다.  

-   컴퓨터는 어떤 사이트의 SMS 공급자도 보유해서는 안됩니다.  

-   컴퓨터에서 사이트 서버에 대해 지원되는 운영 체제를 실행해야 합니다.  

-   컴퓨터에는 SMS 공급자와 함께 설치되는 Windows ADK(Windows 자동 배포 키트) 구성 요소를 지원할 수 있도록 사용 가능한 디스크 공간이 650MB 이상 있어야 합니다. Windows ADK 및 SMS 공급자에 대한 자세한 내용은 이 항목에서 [SMS 공급자에 대한 운영 체제 배포 요구 사항](#BKMK_WAIKforSMSProv) 섹션을 참조하세요.  

##  <a name="bkmk_location"></a> SMS 공급자 위치  
 사이트를 설치할 때, 사이트의 첫 번째 SMS 공급자를 자동으로 설치합니다. SMS 공급자에 대해 다음과 같은 지원되는 위치를 지정할 수 있습니다.  

-   사이트 서버 컴퓨터  

-   사이트 데이터베이스 컴퓨터  

-   SMS 공급자가 없는 서버급 컴퓨터 또는 다른 사이트의 사이트 시스템 역할  


사이트에 설치된 각 SMS 공급자의 위치를 보려면 사이트 **속성** 대화 상자의 **일반** 탭을 선택합니다.  

 각 SMS 공급자에서 여러 요청의 동시 연결을 지원합니다. 이 연결에 대한 제한 사항은 SMS 공급자 컴퓨터에서 사용할 수 있는 서버 연결 수와 SMS 공급자 컴퓨터에서 연결 요청을 처리하기 위한 가용 리소스입니다.  

 사이트가 설치된 후 사이트 서버에서 다시 설치 프로그램을 실행하여 기존 SMS 공급자의 위치를 변경하거나 해당 사이트에 추가 SMS 공급자를 설치할 수 있습니다. 한 컴퓨터에는 SMS 공급자를 하나만 설치할 수 있고 한 컴퓨터는 둘 이상의 사이트에서 SMS 공급자를 설치할 수 없습니다.  

 다음 내용을 참고하면 지원되는 각 위치마다 SMS 공급자를 설치하는 방식의 장점과 단점을 확인할 수 있습니다.  

 **Configuration Manager 사이트 서버**  

-   **장점:**  

    -   SMS 공급자는 사이트 데이터베이스 컴퓨터의 시스템 리소스를 사용하지 않습니다.  

    -   이 위치를 통해 사이트 서버 또는 사이트 데이터베이스 컴퓨터가 아닌 컴퓨터에 배치된 SMS 공급자보다 더 나은 성능을 낼 수 있습니다.  

-   **단점:**  

    -   SMS 공급자는 사이트 서버 작업에 전용으로 사용될 수 있는 시스템 및 네트워크 리소스를 사용합니다.  


**사이트 데이터베이스를 호스팅하는 SQL Server**  

-   **장점:**  

    -   SMS 공급자는 사이트 서버의 사이트 시스템 리소스를 사용하지 않습니다.  

    -   충분한 서버 리소스를 사용할 수 있는 경우 이 위치는 세 위치 중 최상의 성능을 낼 수 있습니다.  

-   **단점:**  

    -   SMS 공급자는 사이트 데이터베이스 작업에 전용으로 사용될 수 있는 시스템 및 네트워크 리소스를 사용합니다.  

    -   사이트 데이터베이스가 SQL Server의 클러스터된 인스턴스에서 호스트되는 경우에는 이 위치를 사용할 수 없습니다.  


**사이트 서버 또는 사이트 데이터베이스 컴퓨터가 아닌 컴퓨터**  

-   **장점:**  

    -   SMS 공급자는 사이트 서버 또는 사이트 데이터베이스 컴퓨터 리소스를 사용하지 않습니다.  

    -   이러한 유형의 위치를 사용하면 추가 SMS 공급자를 배포하여 고가용성 연결을 구현할 수 있습니다.  

-   **단점:**  

    -   SMS 공급자 성능은 사이트 서버 및 사이트 데이터베이스 컴퓨터와 조정하기 위해 필요한 추가 네트워크 활동으로 인해 감소할 수도 있습니다.  

    -   이 서버는 사이트 데이터베이스 컴퓨터와 Configuration Manager 콘솔이 설치된 모든 컴퓨터에서 항상 액세스할 수 있어야 합니다.  

    -   이 위치에서는 원래 다른 서비스에 전용으로 사용될 시스템 리소스를 사용할 수 있습니다.  

##  <a name="BKMK_SMSProvLanguages"></a> SMS 공급자 언어 정보  
 SMS 공급자는 설치된 컴퓨터의 표시 언어와 독립적으로 작동합니다.  

 관리자 또는 Configuration Manager 프로세스에서 SMS 공급자를 사용하여 데이터를 요청하는 경우 SMS 공급자는 요청하는 컴퓨터의 운영 체제 언어와 일치하는 형식으로 해당 데이터의 반환을 시도합니다.

언어를 일치시키는 방법은 다소 간접적입니다. SMS 공급자는 정보를 한 언어에서 다른 언어로 변역하지 않습니다. 대신 데이터가 Configuration Manager 콘솔에 표시되기 위해 반환될 때 데이터의 표시 언어는 개체 및 저장소 유형의 원본에 따라 달라집니다.  

 개체에 대한 데이터가 데이터베이스에 저장되면 사용 가능한 언어는 다음 사항에 따라 달라집니다.  

-   Configuration Manager에서 만드는 개체는 다중 언어 지원을 통해 데이터베이스에 저장됩니다. 이 개체는 설치 프로그램을 실행할 때 개체가 만들어진 사이트에 구성된 언어를 사용하여 저장됩니다. 이러한 개체는 해당 개체에 대해 해당 언어가 사용 가능한 경우 요청 컴퓨터의 표시 언어로 Configuration Manager 콘솔에 표시됩니다. 개체를 요청하는 컴퓨터의 표시 언어로 표시할 수 없는 경우 이 개체는 기본 언어인 영어로 표시됩니다.  

-   관리자가 만드는 개체는 해당 개체를 만드는 데 사용된 언어로 데이터베이스에 저장됩니다. 이 개체는 Configuration Manager 콘솔에 동일한 언어로 표시됩니다. 이 개체는 SMS 공급자에 의해 번역되지 않으며 다중 언어 옵션을 제공하지 않습니다.  

##  <a name="BKMK_MultiSMSProv"></a> 다중 SMS 공급자 사용  
 사이트 설치가 완료되면 사이트에 대한 추가 SMS 공급자를 설치할 수 있습니다. 추가 SMS 공급자를 설치하려면 사이트 서버에서 Configuration Manager 설치 프로그램을 실행합니다. 다음 조건 중 하나라도 충족할 경우 추가 SMS 공급자를 설치하는 것이 좋습니다.  

-   동시에 Configuration Manager 콘솔을 실행하고 사이트에 연결하는 다수의 관리자가 있습니다.  

-   Configuration Manager SDK 또는 기타 제품을 사용하므로 SMS 공급자를 자주 호출할 가능성이 있습니다.  

-   SMS 공급자의 고가용성을 보장하려 합니다.  


사이트에 여러 SMS 공급자가 설치되고 연결 요청이 발생할 때 사이트에서 각 새 연결 요청이 설치된 SMS 공급자를 사용하도록 무작위로 할당됩니다. 특정 연결 세션과 함께 사용할 SMS 공급자 위치는 지정할 수 없습니다.  

> [!NOTE]  
>  각 SMS 공급자 위치의 장단점을 고려하세요. SMS 공급자를 각 새 연결에 사용할 때마다 이러한 고려 사항과 제어할 수 없는 정보의 균형을 맞추세요.  

예를 들어 Configuration Manager 콘솔을 사이트에 처음 연결할 때 연결 과정에서 사이트 서버의 WMI를 쿼리하여 콘솔이 사용할 SMS 공급자의 인스턴스를 확인합니다. 이러한 특정 SMS 공급자 인스턴스는 해당 Configuration Manager 콘솔 세션이 종료될 때까지 Configuration Manager 콘솔에 의해 사용 중인 상태로 유지됩니다. 네트워크에서 SMS 공급자 컴퓨터를 사용할 수 없게 되어 세션이 종료될 경우, Configuration Manager 콘솔을 다시 연결하면 사이트에서는 단순히 연결할 SMS 공급자 인스턴스 식별 작업을 반복합니다. 이때, 사용할 수 없는 같은 SMS 공급자 컴퓨터가 할당될 수도 있습니다. 이 경우 사용 가능한 SMS 공급자 컴퓨터가 할당될 때까지 Configuration Manager 콘솔을 다시 연결할 수 있습니다.  

##  <a name="BKMK_AboutSMSAdmins"></a> SMS Admins 그룹 정보  
 SMS Admins 그룹으로 SMS 공급자에 대한 관리자 권한을 제공할 수 있습니다. 이 그룹은 사이트가 설치될 때 사이트 서버에, 그리고 SMS 공급자를 설치하는 각 컴퓨터에 자동으로 만들어집니다. SMS Admins 그룹에 대한 추가 정보:  

-   컴퓨터가 구성원 서버인 경우 SMS Admins 그룹은 로컬 그룹으로 만들어집니다.  

-   컴퓨터가 도메인 컨트롤러인 경우 SMS Admins 그룹은 도메인 로컬 그룹으로 만들어집니다.  

-   SMS 공급자가 컴퓨터에서 제거되어도 SMS Admins 그룹은 컴퓨터에서 제거되지 않습니다.  


사용자가 SMS 공급자에 성공적으로 연결하려면 해당 사용자 계정은 SMS Admins 그룹의 구성원이어야 합니다. Configuration Manager 콘솔에 구성하는 각 관리자는 각 사이트 서버의 SMS Admins 그룹과 계층 내 각 SMS 공급자 컴퓨터에 자동으로 추가됩니다. Configuration Manager 콘솔에서 관리자를 삭제하면 이 관리자는 각 사이트 서버의 SMS Admins 그룹과 계층 내 각 SMS 공급자 컴퓨터의 SMS Admins 그룹에서 제거됩니다.  

사용자가 SMS 공급자에 성공적으로 연결하면 해당 사용자가 액세스하거나 관리할 수 있는 Configuration Manager 리소스가 역할 기반 관리를 통해 결정됩니다.  

WMI 컨트롤 MMC 스냅인을 사용하면 SMS Admins 그룹 권한을 보고 구성할 수 있습니다. 기본적으로는 **모든 사용자** 에게 **메서드 실행**, **공급자 쓰기**및 **계정 사용** 권한이 있습니다. SMS 공급자에 연결하는 사용자는 Configuration Manager 콘솔에 정의된 역할 기반 관리 보안 권한에 따라 사이트 데이터베이스의 데이터에 대한 액세스할 수 있는 권한을 부여받습니다. SMS Admins 그룹에는 **Root\SMS** 네임스페이스에 대한 **계정 사용** 및 **원격으로부터 사용 가능** 권한이 명시적으로 부여됩니다.  

> [!NOTE]  
>  원격 Configuration Manager 콘솔을 사용하는 각 관리자에게는 사이트 서버 컴퓨터 및 SMS 공급자 컴퓨터에 대한 원격 활성화 DCOM 권한이 필요합니다. 이 권한은 모든 사용자나 그룹에게 부여할 수 있지만 간편한 관리를 위해 SMS Admins 그룹에게만 부여하는 것이 좋습니다. 자세한 내용은 [Modify your System Center Configuration Manager infrastructure](../../../core/servers/manage/modify-your-infrastructure.md)(System Center Configuration Manager 인프라 수정) 항목의 [Configure DCOM permissions for remote Configuration Manager consoles](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole)(원격 Configuration Manager 콘솔에 대한 DCOM 권한 구성) 섹션을 참조하세요.  


##  <a name="BKMK_SMSProvNamespace"></a> SMS 공급자 네임스페이스 정보  
SMS 공급자의 구조는 WMI 스키마에 의해 정의됩니다. 스키마 네임스페이스는 SMS 공급자 스키마 내 Configuration Manager 데이터의 위치를 설명합니다. 다음 표에서는 SMS 공급자에서 사용되는 공통 네임스페이스 일부를 보여 줍니다.  

|네임스페이스|설명|  
|---------------|-----------------|  
|Root\SMS\site_*&lt;사이트 코드\>*|Configuration Manager 콘솔, 리소스 탐색기, Configuration Manager 도구 및 스크립트에 광범위하게 사용되는 SMS 공급자입니다.|  
|Root\SMS\SMS_ProviderLocation|사이트의 SMS 공급자 컴퓨터 위치입니다.|  
|Root\CIMv2|하드웨어 및 소프트웨어 인벤토리 도중 WMI 네임스페이스 정보가 인벤토리에 저장되는 위치입니다.|  
|Root\CCM|Configuration Manager 클라이언트 구성 정책 및 클라이언트 데이터입니다.|  
|root\CIMv2\SMS|인벤토리 클라이언트 에이전트에서 수집하는 인벤토리 보고 클래스의 위치입니다. 이러한 설정은 컴퓨터 정책 평가 도중 클라이언트에 의해 컴파일되며, 컴퓨터의 클라이언트 설정 구성을 기반으로 합니다.|  

##  <a name="BKMK_WAIKforSMSProv"></a> SMS 공급자에 대한 운영 체제 배포 요구 사항  
SMS 공급자의 인스턴스를 설치하는 컴퓨터에는 사용할 Configuration Manager 버전에서 요구하는 Windows ADK의 필수 버전이 있어야 합니다.  

 -   Configuration Manager 버전 1511에는 Windows ADK의 Windows 10 RTM(10.0.10240) 버전이 필요합니다.  

 -   이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

운영 체제 배포를 관리하는 경우 Windows ADK는 다음과 같은 다양한 작업을 SMS 공급자에서 완료할 수 있도록 허용합니다.  

-   WIM 파일 정보 보기  

-   기존 부팅 이미지에 드라이버 파일 추가  

-   부팅 .ISO 파일 만들기  


Windows ADK를 설치하려면 SMS 공급자를 설치하는 각 컴퓨터에 최대 650MB의 사용 가능한 디스크 공간이 필요합니다. 이 많은 디스크 공간은 Configuration Manager가 Windows PE 부팅 이미지를 설치하는 데 필요합니다.  
