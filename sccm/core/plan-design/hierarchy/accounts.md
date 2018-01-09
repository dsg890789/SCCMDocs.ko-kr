---
title: "사용된 계정"
titleSuffix: Configuraton Manager
description: "System Center Configuration Manager에서 Windows 그룹과 계정을 식별하고 관리합니다."
ms.custom: na
ms.date: 2/9/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72d7b174-f015-498f-a0a7-2161b9929198
caps.latest.revision: "7"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 518be0c1cb4c361d8802ed70779d192725eb8feb
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2018
---
# <a name="accounts-used-in-system-center-configuration-manager"></a>System Center Configuration Manager에 사용된 계정

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 정보를 사용하면 System Center Configuration Manager에서 사용하는 Windows 그룹과 계정, 사용 방법 및 요구 사항을 확인할 수 있습니다.  

## <a name="windows-groups-that-configuration-manager-creates-and-uses"></a>Configuration Manager에서 만들고 사용하는 Windows 그룹  
 Configuration Manager에서는 다음 Windows 그룹이 자동으로 만들어지고 대부분의 경우 자동으로 유지 관리됩니다.  

> [!NOTE]  
>  Configuration Manager에서 도메인 구성원인 컴퓨터에 그룹을 만들면 이 그룹은 로컬 보안 그룹이 됩니다. 컴퓨터가 도메인 컨트롤러인 경우 이 그룹은 도메인의 모든 도메인 컨트롤러 간에 공유되는 도메인 로컬 그룹이 됩니다.  


### <a name="configmgrcollectedfilesaccess"></a>ConfigMgr_CollectedFilesAccess  
Configuration Manager에서는 소프트웨어 인벤토리를 통해 수집한 파일을 볼 수 있는 액세스 권한을 부여하는 데 이 그룹을 사용합니다.  

다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 기본 사이트 서버에 만들어지는 로컬 보안 그룹입니다.<br /><br /> 사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 수동으로 이 그룹을 삭제해야 합니다.|  
|Membership|Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 멤버 자격에는 할당된 보안 역할의 **컬렉션** 보안 개체에 대한 **수집된 파일 보기** 권한이 부여된 관리자가 포함됩니다.|  
|사용 권한|기본적으로 이 그룹에는 사이트 서버의 **Read** 폴더에 대한 **%path%\Microsoft Configuration Manager\sinv.box\FileCol**권한이 있습니다.|  

### <a name="configmgrdviewaccess"></a>ConfigMgr_DViewAccess  
 이 그룹은 Configuration Manager가 사이트 데이터베이스 서버 또는 데이터베이스 복제 서버에 만드는 로컬 보안 그룹입니다. 현재 사용되지는 않지만 나중에 사용하도록 예약되어 있습니다.  

### <a name="configmgr-remote-control-users"></a>ConfigMgr 원격 제어 사용자  
 Configuration Manager 원격 도구에서 이 그룹을 사용하여 각 클라이언트에 할당되는 허용된 뷰어 목록에서 설정한 계정과 그룹을 저장합니다.  

 다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 클라이언트에서 원격 도구를 사용하는 정책을 받을 때 Configuration Manager 클라이언트에 만들어지는 로컬 보안 그룹입니다.<br /><br /> 원격 도구를 클라이언트에 사용하지 않도록 설정한 후에도 이 그룹은 자동으로 제거되지 않습니다. 각 클라이언트 컴퓨터에서 수동으로 삭제해야 합니다.|  
|Membership|기본적으로 이 그룹에는 구성원이 없습니다. 허용된 뷰어 목록에 사용자를 추가하면 해당 사용자가 자동으로 이 그룹에 추가됩니다.<br /><br /> 이 그룹에 직접 사용자 또는 그룹을 추가하지 않고 허용된 뷰어 목록을 사용하여 이 그룹의 멤버 자격을 관리할 수 있습니다.<br /><br /> 관리자는 허용된 뷰어가 되어야 할 뿐 아니라 **컬렉션** 개체에 대한 **원격 제어** 권한도 있어야 합니다. 이 권한은 원격 도구 운영자 보안 역할을 사용하여 할당할 수 있습니다.|  
|사용 권한|기본적으로 이 그룹에는 컴퓨터의 어떠한 위치에 대한 권한도 없습니다. 이 그룹은 허용된 뷰어 목록을 보유하는 데만 사용됩니다.|  

### <a name="sms-admins"></a>SMS Admins  
 Configuration Manager는 이 그룹을 사용하여 WMI(Windows Management Instrumentation)를 통해 SMS 공급자에 대한 액세스 권한을 부여합니다. Configuration Manager 콘솔에서 개체를 보고 변경하려면 SMS 공급자에 대한 액세스 권한이 필요합니다.  

> [!NOTE]  
>  관리자의 역할 기반 관리 구성에 따라 Configuration Manager 콘솔을 사용할 때 보고 관리할 수 있는 개체가 결정됩니다.  

 다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 SMS 공급자가 있는 각 컴퓨터에 만들어지는 로컬 보안 그룹입니다.<br /><br /> 사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 수동으로 이 그룹을 삭제해야 합니다.|  
|Membership|Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 계층의 각 관리자와 사이트 서버 컴퓨터 계정이 사이트에 있는 각 SMS 공급자 컴퓨터에 대한 SMS Admins 그룹의 구성원입니다.|  
|사용 권한|SMS Admins 권한은 WMI 컨트롤 MMC 스냅인에서 설정됩니다. 기본적으로 SMS Admins 그룹에는 Root\SMS 네임스페이스에 대한 **Enable Account** 및 **Remote Enable** 권한이 부여됩니다. 인증된 사용자에게는 **Execute Methods**, **Provider Write** 및 **Enable Account** 권한이 있습니다.<br /><br /> 원격 Configuration Manager 콘솔을 사용할 관리자에게는 사이트 서버 컴퓨터와 SMS 공급자 컴퓨터 모두에 대한 원격 활성화 DCOM 권한이 필요합니다. 이러한 권한을 사용자 또는 그룹에 직접 부여하지 않고 SMS Admins에 부여하여 관리를 단순화하는 것이 가장 좋습니다. 자세한 내용은 [Modify your System Center Configuration Manager infrastructure](../../../core/servers/manage/modify-your-infrastructure.md)(System Center Configuration Manager 인프라 수정) 항목의 [Configure DCOM permissions for remote Configuration Manager consoles](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole)(원격 Configuration Manager 콘솔에 대한 DCOM 권한 구성) 섹션을 참조하세요.|  

### <a name="smssitesystemtositeserverconnectionmpltsitecode"></a>SMS_SiteSystemToSiteServerConnection_MP_&lt;sitecode\>  
 사이트 서버에서 원격인 Configuration Manager 관리 지점은 이 그룹을 사용하여 사이트 데이터베이스에 연결합니다. 이 그룹은 사이트 서버 및 사이트 데이터베이스의 수신함 폴더에 대한 액세스 권한을 관리 지점에 제공합니다.  

 다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 SMS 공급자가 있는 각 컴퓨터에 만들어지는 로컬 보안 그룹입니다.<br /><br /> 사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 수동으로 이 그룹을 삭제해야 합니다.|  
|Membership|Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 사이트에 대한 관리 지점이 있는 원격 컴퓨터의 컴퓨터 계정이 멤버 자격에 포함됩니다.|  
|사용 권한|기본적으로 이 그룹에는 사이트 서버의 **%path%\Microsoft Configuration Manager\inboxes** 폴더에 대한 **읽기**, **읽기 및 실행** 및 **폴더 내용 보기** 권한이 있습니다. 이 그룹은 관리 지점에서 클라이언트 데이터를 쓰는 **inboxes** 아래의 하위 폴더에 대한 추가 **쓰기** 권한도 갖습니다.|  

### <a name="smssitesystemtositeserverconnectionsmsprovltsitecode"></a>SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;sitecode\>  
 사이트 서버에서 원격인 Configuration Manager SMS 공급자 컴퓨터는 이 그룹을 사용하여 사이트 서버에 연결합니다.  

 다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 사이트 서버에 만들어지는 로컬 보안 그룹입니다.<br /><br /> 사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 수동으로 이 그룹을 삭제해야 합니다.|  
|Membership|Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 사이트의 SMS 공급자가 설치된 각 원격 컴퓨터에서 사이트 서버에 연결하는 데 사용되는 컴퓨터 계정이나 도메인 사용자 계정이 멤버 자격에 포함됩니다.|  
|사용 권한|기본적으로 이 그룹에는 사이트 서버의 **%path%\Microsoft Configuration Manager\inboxes** 폴더에 대한 **읽기**, **읽기 및 실행** 및 **폴더 내용 보기** 권한이 있습니다. 이 그룹에는 SMS 공급자가 액세스해야 하는 **inboxes** 아래의 하위 폴더에 대한 **쓰기** 및 **수정** 권한이나 **쓰기** 추가 권한이 있습니다.<br /><br /> 이 그룹에는 **%path%\Microsoft Configuration Manager\OSD\boot** 아래의 폴더에 대한 **읽기**, **읽기 및 실행**, **폴더 내용 보기**, **쓰기** 및 **수정** 권한과, 사이트 서버의 **%path%\Microsoft Configuration Manager\OSD\Bin** 아래에 있는 폴더에 대한 **읽기** 권한도 있습니다.|  

### <a name="smssitesystemtositeserverconnectionstatltsitecode"></a>SMS_SiteSystemToSiteServerConnection_Stat_&lt;sitecode\>  
 Configuration Manager 원격 사이트 시스템 컴퓨터의 파일 발송 관리자에서 이 그룹을 사용하여 사이트 서버에 연결합니다.  

 다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 사이트 서버에 만들어지는 로컬 보안 그룹입니다.<br /><br /> 사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 수동으로 이 그룹을 삭제해야 합니다.|  
|Membership|Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 파일 발송 관리자를 실행하는 각 원격 사이트 시스템 컴퓨터에서 사이트 서버에 연결하는 데 사용되는 컴퓨터 계정이나 도메인 사용자 계정이 멤버 자격에 포함됩니다.|  
|사용 권한|기본적으로 이 그룹에는 사이트 서버의 **%path%\Microsoft Configuration Manager\inboxes** 폴더 및 해당 위치 아래의 하위 폴더에 대한 **읽기**, **읽기 및 실행** 및 **폴더 내용 보기** 권한이 있습니다. 이 그룹에는 사이트 서버의 **%path%\Microsoft Configuration Manager\inboxes\statmgr.box** 폴더에 대한 **쓰기** 및 **수정** 추가 권한이 있습니다.|  

### <a name="smssitetositeconnectionltsitecode"></a>SMS_SiteToSiteConnection_&lt;sitecode\>  
 Configuration Manager에서 이 그룹을 사용하여 계층의 사이트 간에 파일 기반 복제를 사용하도록 설정합니다. 이 사이트로 직접 파일을 전송하는 각 원격 사이트에 대한 **파일 복제 계정**으로 설정된 계정이 이 그룹에 포함됩니다.  

 다음 표에는 이 그룹에 대한 추가 세부 정보가 나와 있습니다.  

|세부 정보|추가 정보|  
|------------|----------------------|  
|유형 및 위치|이 그룹은 사이트 서버에 만들어지는 로컬 보안 그룹입니다.|  
|Membership|새 사이트를 다른 사이트의 자식으로 설치하면 Configuration Manager에서 자동으로 새 사이트의 컴퓨터 계정을 부모 사이트 서버의 그룹에 추가합니다. Configuration Manager는 또한 부모 사이트의 컴퓨터 계정을 새 사이트 서버의 그룹에 추가합니다. 파일 기반 전송을 위해 다른 계정을 지정하는 경우 해당 계정을 대상 사이트 서버의 이 그룹에 추가하세요.<br /><br /> 사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 수동으로 이 그룹을 삭제해야 합니다.|  
|사용 권한|기본적으로 이 그룹에는 사이트 서버의 **%path%\Microsoft Configuration Manager\inboxes\despoolr.box\receive** 폴더에 대한 **모든 권한** 이 있습니다.|  

## <a name="accounts-that-configuration-manager-uses"></a>Configuration Manager에서 사용하는 계정  
 Configuration Manager에 대한 다음 계정을 설정할 수 있습니다.  

### <a name="active-directory-group-discovery-account"></a>Active Directory 그룹 검색 계정  
 **Active Directory 그룹 검색 계정**은 Active Directory Domain Services의 지정된 위치에서 로컬, 글로벌 및 유니버설 보안 그룹과 이러한 그룹 내의 멤버 자격, 그리고 배포 그룹 내의 멤버 자격을 검색하는 데 사용됩니다. 배포 그룹은 그룹 리소스로 검색되지 않습니다.  

 이 계정은 검색을 실행하는 사이트 서버의 컴퓨터 계정이나 Windows 사용자 계정 중 하나일 수 있습니다. 이 계정에는 검색을 위해 지정된 Active Directory 위치에 대한 **읽기** 액세스 권한이 있어야 합니다.  

### <a name="active-directory-system-discovery-account"></a>Active Directory 시스템 검색 계정  
 **Active Directory 시스템 검색 계정** 은 Active Directory Domain Services의 지정된 위치에서 컴퓨터를 검색하는 데 사용됩니다.  

 이 계정은 검색을 실행하는 사이트 서버의 컴퓨터 계정이나 Windows 사용자 계정 중 하나일 수 있습니다. 이 계정에는 검색을 위해 지정된 Active Directory 위치에 대한 **읽기** 액세스 권한이 있어야 합니다.  

### <a name="active-directory-user-discovery-account"></a>Active Directory 사용자 검색 계정  
 **Active Directory 사용자 검색 계정** 은 Active Directory Domain Services의 지정된 위치에서 사용자 계정을 검색하는 데 사용됩니다.  

 이 계정은 검색을 실행하는 사이트 서버의 컴퓨터 계정이나 Windows 사용자 계정 중 하나일 수 있습니다. 이 계정에는 검색을 위해 지정된 Active Directory 위치에 대한 **읽기** 액세스 권한이 있어야 합니다.  

### <a name="active-directory-forest-account"></a>Active Directory 포리스트 계정  
 **Active Directory 포리스트 계정**은 Active Directory 포리스트에서 네트워크 인프라를 검색하는 데 사용됩니다. 중앙 관리 사이트와 기본 사이트에서도 포리스트에 대한 Active Directory Domain Services에 사이트 데이터를 게시하는 데 이 계정을 사용합니다.  

> [!NOTE]  
>  보조 사이트에서는 Active Directory에 게시하는 데 항상 보조 사이트 서버 컴퓨터 계정을 사용합니다.  

> [!NOTE]  
>  신뢰할 수 없는 포리스트를 검색하고 게시하려면 Active Directory 포리스트 계정이 글로벌 계정이어야 합니다. 사이트 서버의 컴퓨터 계정을 사용하지 않는 경우 글로벌 계정만 선택할 수 있습니다.  

 이 계정은 네트워크 인프라를 검색할 각 Active Directory 포리스트에 대해 **읽기** 권한이 있어야 합니다.  

 또한, 사이트 데이터를 게시할 각 Active Directory 포리스트의 System Management 컨테이너와 해당 컨테이너의 모든 자식 개체에 대해 **모든 권한** 이 있어야 합니다.  

### <a name="asset-intelligence-synchronization-point-proxy-server-account"></a>Asset Intelligence 동기화 지점 프록시 서버 계정  
 Asset Intelligence 동기화 지점에서는 **Asset Intelligence 동기화 지점 프록시 서버 계정**을 사용하여 프록시 서버를 통하거나 인증된 액세스가 필요한 방화벽을 통해 인터넷에 액세스합니다.  

> [!IMPORTANT]  
>  필요한 프록시 서버나 방화벽에 대해 최소한의 권한이 있는 계정을 지정합니다.  

### <a name="certificate-registration-point-account"></a>인증서 등록 지점 계정  
 **인증서 등록 지점 계정**에서 인증 등록 지점을 Configuration Manager 데이터베이스에 연결합니다. 기본적으로 인증서 등록 지점 서버의 컴퓨터 계정이 사용되지만 대신 사용자 계정을 설정할 수 있습니다. 인증서 등록 지점이 사이트 서버에서 트러스트되지 않은 도메인 안에 있는 경우에는 사용자 계정을 지정해야 합니다. 쓰기 작업은 상태 메시지 시스템에서 처리하므로 이 계정에는 사이트 데이터베이스에 대한 **읽기** 권한만 필요합니다.  

### <a name="capture-operating-system-image-account"></a>운영 체제 이미지 캡처 계정  
 Configuration Manager는 **운영 체제 이미지 캡처 계정**을 사용하여 운영 체제를 배포할 때 캡처된 이미지가 저장된 폴더에 액세스합니다. 이 계정은 **운영 체제 이미지 캡처** 단계를 작업 순서에 추가하는 경우에 필요합니다.  

 이 계정에는 캡처된 이미지가 저장되는 네트워크 공유에 대한 **읽기** 및 **쓰기** 권한이 있어야 합니다.  

 Windows에서 계정 암호가 변경되면 새 암호로 작업 순서를 업데이트해야 합니다. Configuration Manager 클라이언트는 다음에 클라이언트 정책을 다운로드할 때 새 암호를 받습니다.  

 이 계정을 사용하는 경우 필요한 네트워크 리소스에 액세스하고 모든 작업 순서 계정에 사용할 수 있도록 최소 권한이 있는 단일 도메인 사용자 계정을 생성할 수 있습니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 할당하지 마세요.  
>   
>  이 계정에 대해 네트워크 액세스 계정을 사용하지 마세요.  

### <a name="client-push-installation-account"></a>클라이언트 강제 설치 계정  
 **클라이언트 강제 설치 계정**은 클라이언트 강제 설치를 사용하여 클라이언트를 배포하는 경우 컴퓨터에 연결하고 Configuration Manager 클라이언트 소프트웨어를 설치하는 데 사용됩니다. 이 계정이 지정되지 않으면 클라이언트 소프트웨어를 설치하는 데 사이트 서버 계정이 사용됩니다.  

 이 계정은 Configuration Manager 클라이언트 소프트웨어가 설치될 컴퓨터에서 로컬 **관리자** 그룹의 구성원이어야 합니다. 이 계정에는 **도메인 관리자** 권한이 필요하지 않습니다.  

 클라이언트 강제 설치 계정은 하나 이상 지정할 수 있으며, Configuration Manager에서 하나의 계정이 성공할 때까지 차례로 사용됩니다.  

> [!TIP]  
>  대규모 Active Directory 배포에서 계정 업데이트를 더욱 효과적으로 구성하려면 다른 이름으로 새 계정을 만든 다음 이 계정을 Configuration Manager에서 클라이언트 강제 설치 계정의 목록에 추가합니다. 충분한 시간을 두고 Active Directory Domain Services에서 새 계정을 복제할 때까지 기다린 다음 Configuration Manager 및 Active Directory Domain Services에서 이전 계정을 제거합니다.  

> [!IMPORTANT]  
>  이 계정에 로컬 로그인 권한을 부여하지 마세요.  

### <a name="enrollment-point-connection-account"></a>등록 지점 연결 계정  
 **등록 지점 연결 계정**을 사용하여 등록 지점을 Configuration Manager 사이트 데이터베이스에 연결합니다. 기본값으로 등록 지점의 컴퓨터 계정이 사용되지만 대신 사용자 계정을 설정할 수도 있습니다. 등록 지점이 사이트 서버에서 트러스트되지 않은 도메인 안에 있는 경우에는 사용자 계정을 지정해야 합니다. 이 계정에는 사이트 데이터베이스에 대한 **읽기** 및 **쓰기** 권한이 필요합니다.  

### <a name="exchange-server-connection-account"></a>Exchange Server 연결 계정  
 **Exchange Server 연결 계정** 은 사이트 서버를 지정된 Exchange Server 컴퓨터에 연결하여 Exchange Server에 연결되는 모바일 장치를 검색 및 관리합니다. 이 계정에는 Exchange Server 컴퓨터에 대한 필수 권한을 제공하는 Exchange PowerShell cmdlet이 필요합니다. cmdlet에 대한 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

### <a name="exchange-server-connector-proxy-server-account"></a>Exchange Server 커넥터 프록시 서버 계정  
 Exchange Server 커넥터는 **Exchange Server 커넥터 프록시 서버 계정**을 사용하여 프록시 서버를 통하거나 인증된 액세스가 필요한 방화벽을 통해 인터넷에 액세스합니다.  

> [!IMPORTANT]  
>  필요한 프록시 서버나 방화벽에 대해 최소한의 권한이 있는 계정을 지정합니다.  

### <a name="management-point-connection-account"></a>관리 지점 연결 계정  
 **관리 지점 연결 계정**은 관리 지점을 Configuration Manager 사이트 데이터베이스에 연결하여 클라이언트 관련 정보를 보내고 검색할 수 있도록 하는 데 사용됩니다. 기본값으로 관리 지점의 컴퓨터 계정이 사용되지만 대신 사용자 계정을 설정할 수도 있습니다. 관리 지점이 사이트 서버에서 트러스트되지 않은 도메인 안에 있는 경우에는 사용자 계정을 지정해야 합니다.  

 이 계정은 Microsoft SQL Server를 실행하는 컴퓨터에서 낮은 권한의 로컬 계정으로 만들어야 합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 부여 하지 마세요.  

### <a name="multicast-connection-account"></a>멀티캐스트 연결 계정  
 멀티캐스트용으로 설정된 배포 지점에서는 **멀티캐스트 연결 계정**을 사용하여 사이트 데이터베이스의 정보를 읽습니다. 기본값으로 배포 지점의 컴퓨터 계정이 사용되지만 대신 사용자 계정을 설정할 수도 있습니다. 사이트 데이터베이스가 트러스트되지 않은 포리스트 안에 있는 경우에는 사용자 계정을 지정해야 합니다. 예를 들어 데이터 센터에 사이트 서버 및 사이트 데이터베이스와는 다른 포리스트에 경계 네트워크가 있는 경우, 이 계정을 사용하여 사이트 데이터베이스에서 멀티캐스트 정보를 읽을 수 있습니다.  

 이 계정을 만들려면 Microsoft SQL Server를 실행하는 컴퓨터에서 낮은 권한의 로컬 계정으로 만들어야 합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 부여 하지 마세요.  

### <a name="network-access-account"></a>네트워크 액세스 계정  
 클라이언트 컴퓨터에서는 배포 지점의 콘텐츠에 액세스하는 데 자체 로컬 컴퓨터 계정을 사용할 수 없는 경우에 **네트워크 액세스 계정**을 사용합니다. 그 예로 트러스트되지 않은 도메인의 작업 그룹 클라이언트 및 컴퓨터를 들 수 있습니다. 또한 이 계정은 운영 체제를 설치하는 컴퓨터에 아직 도메인의 컴퓨터 계정이 없을 때 운영 체제 배포 과정에서 사용될 수 있습니다.  

> [!NOTE]  
>  네트워크 액세스 계정은 프로그램을 실행하거나 소프트웨어 업데이트를 설치하거나 작업 순서를 실행하기 위한 보안 컨텍스트로 절대 사용되지 않습니다. 이 계정은 네트워크의 리소스를 액세스하기 위한 목적으로만 사용됩니다.  

 이 계정에 클라이언트가 소프트웨어에 액세스하는 데 필요한 수준으로 콘텐츠에 대한 적절한 최소 권한을 부여합니다. 이 계정에는 패키지 콘텐츠가 저장된 배포 지점 또는 다른 서버에 대한 **네트워크에서 이 컴퓨터 액세스** 권한이 있어야 합니다. 각 사이트에 대해 최대 10개의 네트워크 액세스 계정을 구성할 수 있습니다.  

> [!WARNING]  
>  Configuration Manager는 computername$ 계정을 사용하여 콘텐츠를 다운로드하는 데 실패하면 자동으로 네트워크 액세스 계정으로 다시 시도하며, 이는 이전에 시도했으나 실패한 경우에도 마찬가지입니다.  

 임의의 도메인에서 리소스에 대한 필수 액세스를 제공하는 계정을 만듭니다. 네트워크 액세스 계정에는 항상 도메인 이름이 포함되어야 합니다. 통과 보안은 이 계정에 대해 지원되지 않습니다. 여러 도메인에 배포 지점이 있는 경우 트러스트된 도메인에 계정을 만드세요.  

> [!TIP]  
>  계정 잠금을 방지하려면 기존 네트워크 액세스 계정에서 암호를 변경하지 마세요. 대신 새 계정을 만들고 Configuration Manager에서 새 계정을 설정합니다. 모든 클라이언트가 새 계정 정보를 받을 수 있을 만큼 충분한 시간이 지나면 네트워크 공유 폴더에서 이전 계정을 제거하고 계정을 삭제합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 부여 하지 마세요.
>   
>  이 계정에 컴퓨터를 도메인에 가입시킬 수 있는 권한을 부여하지 마세요. 작업 순서 도중에 컴퓨터를 도메인에 가입시켜야 하는 경우 작업 순서 편집기 도메인 가입 계정을 사용하세요.  

### <a name="package-access-account"></a>패키지 액세스 계정  
 **패키지 액세스 계정**을 통해 배포 지점의 패키지 폴더에 액세스할 수 있는 사용자 및 사용자 그룹을 지정할 수 있는 NTFS 권한을 설정합니다. 기본적으로 Configuration Manager에서는 일반 액세스 계정인 **사용자** 및 **관리자**에게만 액세스 권한을 부여합니다. 클라이언트 컴퓨터에 대한 액세스는 추가 Windows 계정 또는 그룹을 사용하여 제어할 수 있습니다. 모바일 장치에서는 항상 패키지 콘텐츠를 익명으로 검색하므로 패키지 액세스 계정을 사용하지 않습니다.  

 기본적으로 Configuration Manager는 배포 지점에 패키지 공유를 만들 때 로컬 **사용자** 그룹에 **읽기** 권한을, 로컬 **관리자** 그룹에는 **모든 권한**을 부여합니다. 필요한 실제 권한은 패키지에 따라 달라집니다. 작업 그룹 또는 트러스트되지 않은 포리스트에 있는 클라이언트는 네트워크 액세스 계정을 사용하여 패키지 콘텐츠에 액세스합니다. 네트워크 액세스 계정에는 패키지에 대한 권한이 있어야 하므로 정의된 패키지 액세스 계정이 사용되어야 합니다.  

 배포 지점에 액세스할 수 있는 도메인의 계정을 사용합니다. 패키지가 만들어진 후 계정을 만들거나 변경하면 해당 패키지를 다시 배포해야 합니다. 패키지를 업데이트해도 패키지에 대한 NTFS 권한은 변경되지 않습니다.  

 사용자 그룹의 멤버 자격에서 자동으로 추가하므로 네트워크 액세스 계정을 패키지 액세스 계정으로 추가해서는 안 됩니다. 패키지 액세스 계정을 네트워크 액세스 계정으로만 제한하면 클라이언트가 패키지를 액세스하지 못하도록 막지 않습니다.  

### <a name="reporting-services-point-account"></a>보고 서비스 지점 계정  
 SQL Server Reporting Services에서는 **보고 서비스 지점 계정**을 사용하여 사이트 데이터베이스의 Configuration Manager 보고서 데이터를 검색합니다. 지정한 Windows 사용자 계정 및 암호는 암호화되어 SQL Server Reporting Services 데이터베이스에 저장됩니다.  

### <a name="remote-tools-permitted-viewer-accounts"></a>원격 도구 허용된 뷰어 계정  
 원격 제어에 대해 **허용된 뷰어** 로 지정한 계정은 클라이언트에서 원격 도구 기능을 사용하도록 허용한 사용자들입니다.  

### <a name="site-system-installation-account"></a>사이트 시스템 설치 계정  
 사이트 서버에서는 **사이트 시스템 설치 계정**을 사용하여 사이트 시스템을 설치, 다시 설치, 제거 및 설정합니다. 사이트 서버를 사용하여 사이트 시스템으로의 연결을 시작하도록 사이트 시스템을 설정하는 경우 사이트 시스템 및 사이트 시스템 역할이 설치된 후 Configuration Manager는 또한 이 계정을 사용하여 사이트 시스템 컴퓨터로부터 데이터를 가져옵니다. 각 사이트 시스템에는 다른 사이트 시스템 설치 계정이 있지만 오직 단일 사이트 시스템 설치 계정만 해당 사이트 시스템의 모든 사이트 시스템 역할을 관리하도록 설정할 수 있습니다.  

 이 계정에는 관리자가 설치 및 설정하는 사이트 시스템에 로컬 관리 권한이 필요합니다. 또한 이 계정에는 관리자가 설치 및 설정하는 사이트 시스템에서 보안 정책의 **네트워크에서 이 컴퓨터 액세스**가 있어야 합니다.  

> [!TIP]  
>  여러 도메인 컨트롤러가 있고 이러한 계정이 여러 도메인에서 사용되면 사이트 시스템을 설정하기 전에 계정이 복제되었는지 확인해야 합니다.  
>   
>  각 사이트 시스템에서 관리할 로컬 계정을 지정한 경우 계정이 손상되면 공격자가 입힐 수 있는 손상을 제한할 수 있으므로 이 구성은 도메인 계정을 사용하는 것보다 안전합니다. 하지만 도메인 계정은 관리하기가 더 쉽습니다. 보안과 효과적인 관리 간의 적당한 균형을 고려합니다.  

### <a name="smtp-server-connection-account"></a>SMTP 서버 연결 계정  
 SMTP 서버에 인증된 액세스가 필요한 경우 사이트 서버에서는 **SMTP 서버 연결 계정**을 사용하여 메일 경고를 보냅니다.  

> [!IMPORTANT]  
>  전자 메일을 보낼 수 있는 최소한의 권한이 있는 계정을 지정합니다.  

### <a name="software-update-point-connection-account"></a>소프트웨어 업데이트 지점 연결 계정  
 사이트 서버에서는 다음 두 소프트웨어 업데이트 서비스에 대해 **소프트웨어 업데이트 지점 연결 계정**을 사용합니다.  

-   WSUS(Windows Server Update Services) Configuration Manager - 제품 정의, 분류, 업스트림 설정 등 설정을 설정합니다.  

-   WSUS Synchronization Manager - 업스트림 WSUS 서버 또는 Microsoft Update에 대한 동기화를 요청합니다.  

사이트 시스템 설치 계정은 소프트웨어 업데이트의 구성 요소를 설치하지만 소프트웨어 업데이트 지점에서 소프트웨어 업데이트 관련 기능은 수행할 수 없습니다. 소프트웨어 업데이트 지점이 신뢰할 수 없는 포리스트에 속하기 때문에 이 기능에 대해 사이트 서버 컴퓨터 계정을 사용할 수 없는 경우 사이트 시스템 설치 계정과 함께 이 계정을 지정해야 합니다.  

이 계정은 WSUS가 설치된 컴퓨터에서 로컬 관리자여야 합니다. 또한 로컬 WSUS 관리자 그룹의 일부여야 합니다.  

### <a name="software-update-point-proxy-server-account"></a>소프트웨어 업데이트 지점 프록시 서버 계정  
 소프트웨어 업데이트 지점에서는 **소프트웨어 업데이트 지점 프록시 서버 계정**을 사용하여 인증된 액세스 권한을 필요로 하는 프록시 서버나 방화벽을 통해 인터넷에 액세스합니다.  

> [!IMPORTANT]  
>  필요한 프록시 서버나 방화벽에 대해 최소한의 권한이 있는 계정을 지정합니다.  

### <a name="source-site-account"></a>원본 사이트 계정  
 마이그레이션 프로세스에서는 **원본 사이트 계정**을 사용하여 원본 사이트의 SMS 공급자에 액세스합니다. 마이그레이션 작업용 데이터를 수집할 수 있도록 이 계정에는 원본 사이트에 있는 사이트 개체에 대한 **읽기** 권한이 있어야 합니다.  

 Configuration Manager 2007 배포 지점 또는 공동 배치된 배포 지점이 있는 보조 사이트를 System Center Configuration Manager 배포 지점으로 업그레이드하는 경우, 업그레이드 중에 Configuration Manager 2007 사이트에서 배포 지점을 성공적으로 제거하려면 이 계정에 **Site** 클래스에 대한 **삭제** 권한도 있어야 합니다.  

> [!NOTE]  
>  원본 사이트 계정 및 원본 사이트 데이터베이스 계정은 모두 Configuration Manager 콘솔의 **관리** 작업 영역 **계정** 노드에서 **마이그레이션 관리자**로 식별됩니다.  

### <a name="source-site-database-account"></a>원본 사이트 데이터베이스 계정  
 마이그레이션 프로세스에서는 **원본 사이트 데이터베이스 계정**을 사용하여 원본 사이트의 SQL Server 데이터베이스에 액세스합니다. 원본 사이트의 SQL Server 데이터베이스에서 데이터를 수집할 수 있도록 원본 사이트 데이터베이스 계정에는 원본 사이트의 SQL Server 데이터베이스에 대한 **읽기** 및 **실행** 권한이 있어야 합니다.  

> [!NOTE]  
>  System Center Configuration Manager 컴퓨터 계정을 사용하는 경우 이 계정은 다음의 모든 사항이 충족되어야 합니다.  
>   
> -   Configuration Manager 2007 사이트가 있는 도메인에서 보안 그룹 **Distributed COM Users**의 구성원이어야 합니다.  
> -   **SMS Admins** 보안 그룹의 구성원이어야 합니다.  
> -   모든 Configuration Manager 2007 개체에 대한 **읽기** 권한이 있습니다.  

> [!NOTE]  
>  원본 사이트 계정 및 원본 사이트 데이터베이스 계정은 모두 Configuration Manager 콘솔의 **관리** 작업 영역 **계정** 노드에서 **마이그레이션 관리자**로 식별됩니다.  

### <a name="task-sequence-editor-domain-joining-account"></a>작업 순서 편집기 도메인 가입 계정  
 **작업 순서 편집기 도메인 가입 계정** 은 새롭게 생성된 컴퓨터 이미지를 도메인에 가입시키는 작업 순서에 사용됩니다. **도메인 또는 작업 그룹 가입** 단계를 작업 순서에 추가하고 **도메인 가입**을 선택하는 경우 이 계정이 필요합니다. 또한 **네트워크 설정 적용** 단계를 작업 순서에 추가하는 경우 이 계정이 설정되지만 반드시 필요한 것은 아닙니다.  

 이 계정에는 컴퓨터가 가입할 도메인에 **도메인 가입** 권한이 필요합니다.  

> [!TIP]  
>  작업 순서를 실행하기 위해 이 계정이 필요한 경우 필요한 네트워크 리소스에 액세스하고 모든 작업 순서 계정에 사용할 수 있도록 최소 권한이 있는 단일 도메인 사용자 계정을 생성할 수 있습니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 할당하지 마세요.  
>   
>  이 계정에 대해 네트워크 액세스 계정을 사용하지 마세요.  

### <a name="task-sequence-editor-network-folder-connection-account"></a>작업 순서 편집기 네트워크 폴더 연결 계정  
 작업 순서에서는 **작업 순서 편집기 네트워크 폴더 연결 계정**을 사용하여 네트워크의 공유 폴더에 연결합니다. 이 계정은 **네트워크 폴더에 연결** 단계를 작업 순서에 추가하는 경우 필요합니다.  

 이 계정에는 지정된 공유 폴더에 액세스할 수 있는 권한이 필요합니다. 이 계정은 사용자 도메인 계정이어야 합니다.  

> [!TIP]  
>  작업 순서를 실행하기 위해 이 계정이 필요한 경우 필요한 네트워크 리소스에 액세스하고 모든 작업 순서 계정에 사용할 수 있도록 최소 권한이 있는 단일 도메인 사용자 계정을 생성할 수 있습니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 할당하지 마세요.  
>   
>  이 계정에 대해 네트워크 액세스 계정을 사용하지 마세요.  

### <a name="task-sequence-run-as-account"></a>작업 순서 실행 계정  
 **작업 순서 실행 계정** 은 작업 순서의 명령줄을 실행하는 데 사용되며, 작업 순서 실행 계정으로는 로컬 시스템 계정 이외의 자격 증명이 사용됩니다. 이 계정은 **명령줄 실행** 단계를 작업 순서에 추가하되 관리 컴퓨터에서 로컬 시스템 계정 권한으로 작업 순서가 실행되기를 원하지 않는 경우에 필요합니다.  

 작업 순서에 지정된 명령줄을 실행하는 데 필요한 최소 사용 권한이 있는 계정을 설정해야 합니다. 계정에는 대화형 로그인 권한이 필요하며 주로 소프트웨어를 설치하고 네트워크 리소스에 액세스할 수 있는 권한이 있어야 합니다.  

> [!IMPORTANT]  
>  이 계정에 대해 네트워크 액세스 계정을 사용하지 마세요.  
>   
>  계정을 도메인 관리자 계정으로 만들면 안 됩니다.  
>   
>  이 계정에 대해 로밍 프로필을 설정하면 안 됩니다. 작업 순서가 실행되는 경우 계정에 대한 로밍 프로필을 다운로드합니다. 이렇게 하면 프로필이 로컬 컴퓨터의 액세스에 대해 취약해집니다.  
>   
>  계정 범위를 제한해야 합니다. 예를 들어 각 작업 순서마다 서로 다른 작업 순서 실행 계정을 만들어, 한 계정이 손상되는 경우 해당 계정에 액세스하는 클라이언트 컴퓨터만 손상되도록 할 수 있습니다.  
>   
>  컴퓨터에서 명령줄에 관리 권한이 필요한 경우에는 작업 순서를 실행할 모든 컴퓨터에 작업 순서 실행 계정 전용으로 사용할 로컬 관리자 계정을 만드는 것이 좋습니다. 계정이 더 이상 필요하지 않은 경우 즉시 삭제합니다.  
