---
title: 사용된 계정
titleSuffix: Configuration Manager
description: Configuration Manager에서 사용되는 Windows 그룹, 계정 및 SQL 개체를 식별하고 관리합니다.
ms.date: 05/01/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 72d7b174-f015-498f-a0a7-2161b9929198
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b9f4f95916a2d547f89cab7dac838b7fe68fb30
ms.sourcegitcommit: f531d0a622f220739710b2fe6644ea58d024064a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65933455"
---
# <a name="accounts-used-in-configuration-manager"></a>Configuration Manager에서 사용되는 계정

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 정보를 사용하여 Configuration Manager에서 사용되는 Windows 그룹, 계정, SQL 개체와 사용 방법 및 요구 사항을 식별합니다.  

- [Configuration Manager에서 만들고 사용하는 Windows 그룹](#bkmk_groups)  
    - [ConfigMgr_CollectedFilesAccess](#configmgr_collectedfilesaccess)  
    - [ConfigMgr_DViewAccess](#configmgr_dviewaccess)  
    - [ConfigMgr 원격 제어 사용자](#configmgr-remote-control-users)  
    - [SMS Admins](#sms-admins)  
    - [SMS_SiteSystemToSiteServerConnection_MP_&lt;sitecode\>](#bkmk_remotemp)  
    - [SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;sitecode\>](#bkmk_remoteprov)  
    - [SMS_SiteSystemToSiteServerConnection_Stat_&lt;sitecode\>](#bkmk_remotestat)  
    - [SMS_SiteToSiteConnection_&lt;sitecode\>](#bkmk_filerepl)  

- [Configuration Manager에서 사용하는 계정](#bkmk_accounts)
    - [Active Directory 그룹 검색 계정](#active-directory-group-discovery-account)  
    - [Active Directory 시스템 검색 계정](#active-directory-system-discovery-account)  
    - [Active Directory 사용자 검색 계정](#active-directory-user-discovery-account)  
    - [Active Directory 포리스트 계정](#active-directory-forest-account)  
    - [인증서 등록 지점 계정](#certificate-registration-point-account)  
    - [OS 이미지 캡처 계정](#capture-os-image-account)  
    - [클라이언트 강제 설치 계정](#client-push-installation-account)  
    - [등록 지점 연결 계정](#enrollment-point-connection-account)  
    - [Exchange Server 연결 계정](#exchange-server-connection-account)  
    - [관리 지점 연결 계정](#management-point-connection-account)  
    - [멀티캐스트 연결 계정](#multicast-connection-account)  
    - [네트워크 액세스 계정](#network-access-account)  
    - [패키지 액세스 계정](#package-access-account)  
    - [보고 서비스 지점 계정](#reporting-services-point-account)  
    - [원격 도구 허용된 뷰어 계정](#remote-tools-permitted-viewer-accounts)  
    - [사이트 설치 계정](#site-installation-account)
    - [사이트 시스템 설치 계정](#site-system-installation-account)  
    - [사이트 시스템 프록시 서버 계정](#site-system-proxy-server-account)  
    - [SMTP 서버 연결 계정](#smtp-server-connection-account)  
    - [소프트웨어 업데이트 지점 연결 계정](#software-update-point-connection-account)  
    - [원본 사이트 계정](#source-site-account)  
    - [원본 사이트 데이터베이스 계정](#source-site-database-account)  
    - [작업 순서 도메인 조인 계정](#task-sequence-domain-join-account)  
    - [작업 순서 네트워크 폴더 연결 계정](#task-sequence-network-folder-connection-account)  
    - [작업 순서 실행 계정](#task-sequence-run-as-account)  

- [Configuration Manager가 SQL에서 사용하는 사용자 개체](#bkmk_sqlobjects)
    - [smsdbuser_ReadOnly](#smsdbuser_ReadOnly)
    - [smsdbuser_ReadWrite](#smsdbuser_ReadWrite)
    - [smsdbuser_ReportSchema](#smsdbuser_ReportSchema)

## <a name="bkmk_groups"></a> Configuration Manager에서 만들고 사용하는 Windows 그룹  

 Configuration Manager에서는 다음 Windows 그룹이 자동으로 만들어지고 대부분의 경우 자동으로 유지 관리됩니다.  

> [!NOTE]  
>  Configuration Manager에서 도메인 구성원인 컴퓨터에 그룹을 만들면 이 그룹은 로컬 보안 그룹이 됩니다. 컴퓨터가 도메인 컨트롤러인 경우 그룹은 도메인 로컬 그룹입니다. 이 유형의 그룹은 도메인의 모든 도메인 컨트롤러 간에 공유됩니다.  


### <a name="configmgr_collectedfilesaccess"></a> ConfigMgr_CollectedFilesAccess

Configuration Manager에서는 소프트웨어 인벤토리를 통해 수집한 파일을 볼 수 있는 액세스 권한을 부여하는 데 이 그룹을 사용합니다.  

자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 기본 사이트 서버에 만들어지는 로컬 보안 그룹입니다.

사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 사이트를 제거한 후 수동으로 삭제합니다.

#### <a name="membership"></a>Membership
Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 멤버 자격에는 할당된 보안 역할의 **컬렉션** 보안 개체에 대한 **수집된 파일 보기** 권한이 부여된 관리자가 포함됩니다.

#### <a name="permissions"></a>사용 권한
기본적으로 이 그룹에는 사이트 서버의 `C:\Program Files\Microsoft Configuration Manager\sinv.box\FileCol` 폴더에 대한 **읽기** 권한이 있습니다.  


### <a name="configmgr_dviewaccess"></a>ConfigMgr_DViewAccess  

 이 그룹은 Configuration Manager가 자식 기본 사이트의 사이트 데이터베이스 서버 또는 데이터베이스 복제 서버에 만드는 로컬 보안 그룹입니다. 이 사이트는 계층 구조 내 사이트 간 데이터베이스 복제를 위한 분산 보기를 사용할 때 이를 생성합니다. 여기에는 중앙 관리 사이트의 사이트 서버 및 SQL Server 컴퓨터 계정이 포함됩니다.

 자세한 내용은 [사이트 간 데이터 전송](/sccm/core/servers/manage/data-transfers-between-sites)을 참조하세요.


### <a name="configmgr-remote-control-users"></a>ConfigMgr 원격 제어 사용자  

 Configuration Manager 원격 도구에서 이 그룹을 사용하여 **허용된 뷰어** 목록에 설정된 계정과 그룹을 저장합니다. 사이트에서 이 목록을 각 클라이언트에 할당합니다.  

자세한 내용은 [원격 제어 소개](/sccm/core/clients/manage/remote-control/introduction-to-remote-control)를 참조하세요.

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 클라이언트에서 원격 도구를 사용하는 정책을 받을 때 Configuration Manager 클라이언트에 만들어지는 로컬 보안 그룹입니다.

원격 도구를 클라이언트에 사용하지 않도록 설정한 후에도 이 그룹은 자동으로 제거되지 않습니다. 원격 도구를 해제한 후 수동으로 삭제합니다.

#### <a name="membership"></a>Membership
기본적으로 이 그룹에는 구성원이 없습니다. **허용된 뷰어** 목록에 사용자를 추가하면 해당 사용자가 자동으로 이 그룹에 추가됩니다.

이 그룹의 멤버 자격을 관리하려면 이 그룹에 직접 사용자 또는 그룹을 추가하지 않고 **허용된 뷰어** 목록을 사용합니다.

관리자는 허용된 뷰어가 되어야 할 뿐 아니라 **컬렉션** 개체에 대한 **원격 제어** 권한도 있어야 합니다. 이 권한은 **원격 도구 운영자** 보안 역할을 사용하여 할당합니다.  

#### <a name="permissions"></a>사용 권한
기본적으로 이 그룹에는 컴퓨터의 어떠한 위치에 대한 권한도 없습니다. 이 그룹은 **허용된 뷰어** 목록을 보유하는 데만 사용됩니다.  


### <a name="sms-admins"></a>SMS Admins  

 Configuration Manager는 이 그룹을 사용하여 WMI를 통해 SMS 공급자에 대한 액세스 권한을 부여합니다. Configuration Manager 콘솔에서 개체를 보고 변경하려면 SMS 공급자에 대한 액세스 권한이 필요합니다.  

> [!NOTE]  
>  관리자의 역할 기반 관리 구성에 따라 Configuration Manager 콘솔을 사용할 때 보고 관리할 수 있는 개체가 결정됩니다.  

자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 SMS 공급자가 있는 각 컴퓨터에 만들어지는 로컬 보안 그룹입니다. 

사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 사이트를 제거한 후 수동으로 삭제합니다.

#### <a name="membership"></a>Membership
Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 계층의 각 관리자와 사이트 서버 컴퓨터 계정이 사이트에 있는 각 SMS 공급자 컴퓨터에 대한 **SMS Admins** 그룹의 구성원입니다.

#### <a name="permissions"></a>사용 권한
**WMI 컨트롤** MMC 스냅인에서 SMS Admins 그룹의 권한을 볼 수 있습니다. 기본적으로 이 그룹에는 `Root\SMS` WMI 네임스페이스에 대한 **계정 사용** 및 **원격 사용** 권한이 부여됩니다. 인증된 사용자에게는 **Execute Methods**, **Provider Write** 및 **Enable Account** 권한이 있습니다.

원격 Configuration Manager 콘솔을 사용하는 경우 사이트 서버 컴퓨터와 SMS 공급자 모두에 대한 **원격 활성화** DCOM 권한을 구성합니다. 이러한 권한을 **SMS Admins** 그룹에 부여합니다. 이 작업은 사용자 또는 그룹에 이러한 권한을 직접 부여하는 대신 관리를 간소화합니다. 자세한 내용은 [원격 Configuration Manager 콘솔에 대한 DCOM 권한 구성](/sccm/core/servers/manage/modify-your-infrastructure#BKMK_ConfigDCOMforRemoteConsole)을 참조하세요. 


### <a name="bkmk_remotemp"></a> SMS_SiteSystemToSiteServerConnection_MP_&lt;sitecode\>  
 
사이트 서버와 원격 위치에 있는 관리 지점은 이 그룹을 사용하여 사이트 데이터베이스에 연결합니다. 이 그룹은 사이트 서버 및 사이트 데이터베이스의 수신함 폴더에 대한 액세스 권한을 관리 지점에 제공합니다.  

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 SMS 공급자가 있는 각 컴퓨터에 만들어지는 로컬 보안 그룹입니다.

사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 사이트를 제거한 후 수동으로 삭제합니다.

#### <a name="membership"></a>Membership
Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 사이트에 대한 관리 지점이 있는 원격 컴퓨터의 컴퓨터 계정이 멤버 자격에 포함됩니다.

#### <a name="permissions"></a>사용 권한
기본적으로 이 그룹에는 사이트 서버의 `C:\Program Files\Microsoft Configuration Manager\inboxes` 폴더에 대한 **읽기**, **읽기 및 실행** 및 **폴더 콘텐츠 나열** 권한이 있습니다. 이 그룹에는 관리 지점에서 클라이언트 데이터를 쓰는 **inboxes** 아래의 하위 폴더에 대한 추가 **쓰기** 권한이 있습니다.


### <a name="bkmk_remoteprov"></a> SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;sitecode\>  
 
원격 SMS 공급자 컴퓨터는 이 그룹을 사용하여 사이트 서버에 연결합니다.  

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 사이트 서버에 만들어지는 로컬 보안 그룹입니다.

사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 사이트를 제거한 후 수동으로 삭제합니다.

#### <a name="membership"></a>Membership
Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 멤버 자격에는 컴퓨터 계정 또는 도메인 사용자 계정이 포함됩니다. 이 계정을 사용하여 각 원격 SMS 공급자에서 사이트 서버에 연결합니다.

#### <a name="permissions"></a>사용 권한
기본적으로 이 그룹에는 사이트 서버의 `C:\Program Files\Microsoft Configuration Manager\inboxes` 폴더에 대한 **읽기**, **읽기 및 실행** 및 **폴더 콘텐츠 나열** 권한이 있습니다. 이 그룹에는 수신함 아래의 하위 폴더에 대해 추가적인 **쓰기** 및 **수정** 권한이 있습니다. SMS 공급자에게는 이러한 폴더에 대한 액세스 권한이 필요합니다.

이 그룹에는 `C:\Program Files\Microsoft Configuration Manager\OSD\Bin` 아래 사이트 서버의 하위 폴더에 대한 **읽기** 권한도 있습니다. 

`C:\Program Files\Microsoft Configuration Manager\OSD\boot` 아래의 하위 폴더에 대한 다음 사용 권한도 있습니다.
- **읽기**  
- **읽기 및 실행**  
- **폴더 콘텐츠 나열**  
- **쓰기**  
- **수정**   


### <a name="bkmk_remotestat"></a> SMS_SiteSystemToSiteServerConnection_Stat_&lt;sitecode\>  

Configuration Manager 원격 사이트 시스템 컴퓨터의 파일 발송 관리자 구성 요소에서 이 그룹을 사용하여 사이트 서버에 연결합니다.  

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 사이트 서버에 만들어지는 로컬 보안 그룹입니다.

사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 사이트를 제거한 후 수동으로 삭제합니다.

#### <a name="membership"></a>Membership
Configuration Manager는 자동으로 그룹 멤버 자격을 관리합니다. 기본적으로 멤버 자격에는 컴퓨터 계정 또는 도메인 사용자 계정이 포함됩니다. 이 계정을 사용하여 파일 발송 관리자를 실행하는 각 원격 사이트 시스템에서 사이트 서버에 연결합니다.

#### <a name="permissions"></a>사용 권한
기본적으로 이 그룹에는 사이트 서버의 `C:\Program Files\Microsoft Configuration Manager\inboxes` 폴더 및 하위 폴더에 대한 **읽기**, **읽기 및 실행** 및 **폴더 콘텐츠 나열** 권한이 있습니다. 

이 그룹에는 사이트 서버의 `C:\Program Files\Microsoft Configuration Manager\inboxes\statmgr.box` 폴더에 대해 추가적인 **쓰기** 및 **수정** 권한이 있습니다.


### <a name="bkmk_filerepl"></a> SMS_SiteToSiteConnection_&lt;sitecode\>  
 Configuration Manager에서 이 그룹을 사용하여 계층의 사이트 간에 파일 기반 복제를 사용하도록 설정합니다. 이 사이트로 직접 파일을 전송하는 각 원격 사이트에 대한 **파일 복제 계정**으로 설정된 계정이 이 그룹에 포함됩니다.  

#### <a name="type-and-location"></a>유형 및 위치
이 그룹은 사이트 서버에 만들어지는 로컬 보안 그룹입니다.

#### <a name="membership"></a>Membership
새 사이트를 다른 사이트의 자식으로 설치하면 Configuration Manager에서 자동으로 새 사이트 서버의 컴퓨터 계정을 부모 사이트 서버의 해당 그룹에 추가합니다. Configuration Manager는 또한 부모 사이트의 컴퓨터 계정을 새 사이트 서버의 그룹에 추가합니다. 파일 기반 전송을 위해 다른 계정을 지정하는 경우 해당 계정을 대상 사이트 서버의 이 그룹에 추가하세요.

사이트를 제거해도 이 그룹은 자동으로 제거되지 않습니다. 사이트를 제거한 후 수동으로 삭제합니다.

#### <a name="permissions"></a>사용 권한
기본적으로 이 그룹에는 `C:\Program Files\Microsoft Configuration Manager\inboxes\despoolr.box\receive` 폴더에 대한 **전체 제어** 권한이 있습니다.



## <a name="bkmk_accounts"></a> Configuration Manager에서 사용하는 계정  

 Configuration Manager에 대한 다음 계정을 설정할 수 있습니다.  


### <a name="active-directory-group-discovery-account"></a>Active Directory 그룹 검색 계정  

 사이트에서는 **Active Directory 그룹 검색 계정**을 사용하여 사용자가 지정한 Active Directory Domain Services의 위치에서 다음 개체를 검색합니다.
- 로컬, 글로벌 및 유니버설 보안 그룹
- 이러한 그룹 내의 멤버 자격
- 배포 그룹 내의 멤버 자격
   - 배포 그룹이 그룹 리소스로 검색되지 않습니다.

  이 계정은 검색을 실행하는 사이트 서버의 컴퓨터 계정이나 Windows 사용자 계정 중 하나일 수 있습니다. 검색을 위해 지정한 Active Directory 위치에 대한 **읽기** 액세스 권한이 있어야 합니다.  

  자세한 내용은 [Active Directory 그룹 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutGroup)을 참조하세요.


### <a name="active-directory-system-discovery-account"></a>Active Directory 시스템 검색 계정  

 사이트에서는 **Active Directory 시스템 검색 계정**을 사용하여 사용자가 지정한 Active Directory Domain Services의 위치에서 컴퓨터를 검색합니다.  

 이 계정은 검색을 실행하는 사이트 서버의 컴퓨터 계정이나 Windows 사용자 계정 중 하나일 수 있습니다. 검색을 위해 지정한 Active Directory 위치에 대한 **읽기** 액세스 권한이 있어야 합니다.  

 자세한 내용은 [Active Directory 시스템 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutSystem)을 참조하세요.


### <a name="active-directory-user-discovery-account"></a>Active Directory 사용자 검색 계정  
 
 사이트에서는 **Active Directory 사용자 검색 계정**을 사용하여 사용자가 지정한 Active Directory Domain Services의 위치에서 사용자 계정을 검색합니다.  

 이 계정은 검색을 실행하는 사이트 서버의 컴퓨터 계정이나 Windows 사용자 계정 중 하나일 수 있습니다. 검색을 위해 지정한 Active Directory 위치에 대한 **읽기** 액세스 권한이 있어야 합니다.  

 자세한 내용은 [Active Directory 사용자 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser)을 참조하세요. 


### <a name="active-directory-forest-account"></a>Active Directory 포리스트 계정  

 사이트에서는 **Active Directory 포리스트 계정**을 사용하여 Active Directory 포리스트에서 네트워크 인프라를 검색합니다. 중앙 관리 사이트와 기본 사이트에서도 포리스트에 대한 Active Directory Domain Services에 사이트 데이터를 게시하는 데 이 계정을 사용합니다.  

 > [!NOTE]  
 >  보조 사이트에서는 Active Directory에 게시하는 데 항상 보조 사이트 서버 컴퓨터 계정을 사용합니다.  

 신뢰할 수 없는 포리스트를 검색하고 게시하려면 Active Directory 포리스트 계정이 글로벌 계정이어야 합니다. 사이트 서버의 컴퓨터 계정을 사용하지 않는 경우 글로벌 계정만 선택할 수 있습니다.  

 이 계정은 네트워크 인프라를 검색할 각 Active Directory 포리스트에 대해 **읽기** 권한이 있어야 합니다.  

 이 계정에는 사이트 데이터를 게시할 각 Active Directory 포리스트의 **System Management 컨테이너**와 해당 컨테이너의 모든 자식 개체에 대해 **전체 제어** 권한이 있어야 합니다. 자세한 내용은 [사이트 게시를 위해 Active Directory 준비](/sccm/core/plan-design/network/extend-the-active-directory-schema)를 참조하세요.  

 자세한 내용은 [Active Directory 포리스트 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutForest)을 참조하세요.


### <a name="certificate-registration-point-account"></a>인증서 등록 지점 계정  

 인증서 등록 지점은 **인증서 등록 지점 계정**을 사용하여 Configuration Manager 데이터베이스에 연결합니다. 기본적으로 해당 컴퓨터 계정을 사용하지만 사용자 계정을 대신 구성할 수 있습니다. 인증서 등록 지점이 사이트 서버에서 신뢰할 수 없는 도메인에 있는 경우 사용자 계정을 지정해야 합니다. 쓰기 작업은 상태 메시지 시스템에서 처리하므로 이 계정에는 사이트 데이터베이스에 대한 **읽기** 권한만 필요합니다.  

 자세한 내용은 [인증서 프로필 소개](/sccm/protect/deploy-use/introduction-to-certificate-profiles)를 참조하세요.


### <a name="capture-os-image-account"></a>OS 이미지 캡처 계정  

 OS 이미지를 캡처할 때 Configuration Manager는 **OS 이미지 캡처 계정**을 사용하여 캡처된 이미지를 저장하는 폴더에 액세스합니다. **OS 이미지 캡처** 단계를 작업 순서에 추가하는 경우 이 계정이 필요합니다.  

 계정에는 캡처된 이미지를 저장하는 네트워크 공유에 대한 **읽기** 및 **쓰기** 권한이 있어야 합니다.  

 Windows에서 계정의 암호를 변경하는 경우 작업 순서를 새 암호로 업데이트합니다. Configuration Manager 클라이언트는 다음에 클라이언트 정책을 다운로드할 때 새 암호를 받습니다.  

 이 계정을 사용해야 하는 경우 하나의 도메인 사용자 계정을 만듭니다. 필요한 네트워크 리소스에 액세스할 수 있는 최소한의 권한을 부여하고 모든 캡처 작업 순서에 사용합니다.  

 > [!IMPORTANT]  
 >  이 계정에 대화형 로그인 권한을 할당하지 마세요.  
 >   
 >  이 계정에 네트워크 액세스 계정을 사용하지 마세요.  

 자세한 내용은 [OS를 캡처하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system)를 참조하세요.


### <a name="client-push-installation-account"></a>클라이언트 강제 설치 계정  

 클라이언트 강제 설치 방법을 사용하여 클라이언트를 배포할 때 사이트에서 **클라이언트 강제 설치 계정**을 사용하여 컴퓨터에 연결하고 Configuration Manager 클라이언트 소프트웨어를 설치합니다. 이 계정을 지정하지 않으면 사이트 서버가 컴퓨터 계정을 사용하려고 시도합니다.  

 이 계정은 대상 클라이언트 컴퓨터에서 로컬 **관리자** 그룹의 구성원이어야 합니다. 이 계정에는 **도메인 관리자** 권한이 필요하지 않습니다.  

 둘 이상의 클라이언트 강제 설치 계정을 지정할 수 있습니다. Configuration Manager는 성공할 때까지 해당 계정을 차례대로 시도합니다.  

> [!TIP]  
>  대규모 Active Directory 환경에서 이 계정을 변경해야 하는 경우 다음 프로세스를 사용하여 이 계정 업데이트를 보다 효과적으로 조정합니다. 
> 1. 다른 이름으로 새 계정 만들기   
> 2. Configuration Manager의 클라이언트 강제 설치 계정 목록에 새 계정 추가  
> 3. Active Directory Domain Services가 새 계정을 복제할 때까지 대기  
> 4. 그런 다음, Configuration Manager 및 Active Directory Domain Services에서 이전 계정 제거  

> [!IMPORTANT]  
>  이 계정에 로컬 로그인 권한을 부여하지 마세요.  

 자세한 내용은 [클라이언트 강제 설치](/sccm/core/clients/deploy/plan/client-installation-methods#client-push-installation)를 참조하세요.


### <a name="enrollment-point-connection-account"></a>등록 지점 연결 계정  

 등록 지점은 **등록 지점 연결 계정**을 사용하여 Configuration Manager 사이트 데이터베이스에 연결합니다. 기본적으로 해당 컴퓨터 계정을 사용하지만 사용자 계정을 대신 구성할 수 있습니다. 등록 지점이 사이트 서버에서 신뢰할 수 없는 도메인에 있는 경우에는 사용자 계정을 지정해야 합니다. 이 계정에는 사이트 데이터베이스에 대한 **읽기** 및 **쓰기** 권한이 필요합니다.  

 자세한 내용은 [온-프레임스 MDM에 대한 사이트 시스템 역할 설치](/sccm/mdm/get-started/install-site-system-roles-for-on-premises-mdm)를 참조하세요.


### <a name="exchange-server-connection-account"></a>Exchange Server 연결 계정  

 사이트 서버는 **Exchange Server 연결 계정**을 사용하여 지정된 Exchange Server에 연결합니다. 이 연결을 통해 Exchange Server에 연결하는 모바일 디바이스를 찾고 관리합니다. 이 계정에는 Exchange Server 컴퓨터에 대한 필수 권한을 제공하는 Exchange PowerShell cmdlet이 필요합니다. cmdlet에 대한 자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  


### <a name="management-point-connection-account"></a>관리 지점 연결 계정  

 관리 지점은 **관리 지점 연결 계정**을 사용하여 Configuration Manager 사이트 데이터베이스에 연결합니다. 이 연결을 통해 클라이언트에 대한 정보를 보내고 검색합니다. 관리 지점은 기본적으로 해당 컴퓨터 계정을 사용하지만 사용자 계정을 대신 구성할 수 있습니다. 관리 지점이 사이트 서버에서 신뢰할 수 없는 도메인에 있는 경우에는 사용자 계정을 지정해야 합니다.  

 이 계정은 Microsoft SQL Server를 실행하는 컴퓨터에서 낮은 권한의 로컬 계정으로 만들어야 합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 부여하지 마세요.  


### <a name="multicast-connection-account"></a>멀티캐스트 연결 계정  

 멀티캐스트 지원 배포 지점에서는 **멀티캐스트 연결 계정**을 사용하여 사이트 데이터베이스에서 정보를 읽습니다. 서버는 기본적으로 해당 컴퓨터 계정을 사용하지만 사용자 계정을 대신 구성할 수 있습니다. 사이트 데이터베이스가 신뢰할 수 없는 포리스트에 있는 경우에는 사용자 계정을 지정해야 합니다. 예를 들어 데이터 센터에 사이트 서버 및 사이트 데이터베이스와는 다른 포리스트에 경계 네트워크가 있는 경우, 이 계정을 사용하여 사이트 데이터베이스에서 멀티캐스트 정보를 읽습니다.  

 이 계정이 필요한 경우 Microsoft SQL Server를 실행하는 컴퓨터에서 낮은 권한의 로컬 계정으로 만들어야 합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 부여하지 마세요.  

 자세한 내용은 [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)를 참조하세요.


### <a name="network-access-account"></a>네트워크 액세스 계정  

 클라이언트 컴퓨터에서는 배포 지점의 콘텐츠에 액세스하는 데 자체 로컬 컴퓨터 계정을 사용할 수 없는 경우에 **네트워크 액세스 계정**을 사용합니다. 대부분 신뢰할 수 없는 도메인의 작업 그룹 클라이언트 및 컴퓨터에 적용됩니다. 이 계정은 OS 배포 중에 OS를 설치하는 컴퓨터에 도메인의 컴퓨터 계정이 아직 없을 때에도 사용됩니다.  

> [!Important]  
>  네트워크 액세스 계정은 프로그램을 실행, 소프트웨어 업데이트 설치 또는 작업 순서를 실행하기 위한 보안 컨텍스트로 절대 사용되지 않습니다. 이 계정은 네트워크의 리소스를 액세스하기 위한 목적으로만 사용됩니다.  

 Configuration Manager 클라이언트는 먼저 해당 컴퓨터 계정을 사용하여 콘텐츠를 다운로드하려고 시도합니다. 실패하면 자동으로 네트워크 액세스 계정을 시도합니다.  

 버전 1806부터는 작업 그룹 또는 Azure AD 조인 클라이언트가 네트워크 액세스 계정 없이도 배포 지점에서 콘텐츠에 안전하게 액세스할 수 있습니다. 이 동작에는 부팅 미디어, PXE 또는 소프트웨어 센터에서 실행되는 작업 순서가 있는 OS 배포 시나리오가 포함됩니다. 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.<!--1358228,1358278-->

 > [!Note]  
 > **고급 HTTP**를 사용하도록 설정하여 네트워크 액세스 계정이 필요하지 않은 경우 배포 지점이 Windows Server 2008 R2 SP1 이상을 실행해야 합니다. <!--SCCMDocs-pr issue #2696-->
>  
> 이 기능을 사용하기 전에 클라이언트를 1806 버전으로 업그레이드하세요. **고급 HTTP** 연결만 허용하는 경우 이전 클라이언트는 이 메서드를 사용하여 인증할 수 없으므로, 배포 지점에서 클라이언트 업그레이드 패키지를 다운로드할 수 없습니다. <!--vso2841213-->   

#### <a name="permissions"></a>사용 권한

 이 계정에 클라이언트가 소프트웨어에 액세스하는 데 필요한 수준으로 콘텐츠에 대한 적절한 최소 권한을 부여합니다. 이 계정은 배포 지점에 대해 **네트워크에서 이 컴퓨터 액세스** 권한을 가지고 있어야 합니다. 각 사이트에 최대 10개의 네트워크 액세스 계정을 구성할 수 있습니다.  

 도메인에서 리소스에 액세스하는 데 필요한 권한이 있는 계정을 만듭니다. 네트워크 액세스 계정에는 항상 도메인 이름이 포함되어야 합니다. 이 계정에는 통과 보안이 지원되지 않습니다. 여러 도메인에 배포 지점이 있는 경우 트러스트된 도메인에 계정을 만드세요.  

> [!TIP]  
> 계정 잠금을 방지하려면 기존 네트워크 액세스 계정의 암호를 변경하지 마세요. 대신 새 계정을 만들고 Configuration Manager에서 새 계정을 설정합니다. 모든 클라이언트가 새 계정 정보를 받을 수 있을 만큼 충분한 시간이 지나면 네트워크 공유 폴더에서 이전 계정을 제거하고 계정을 삭제합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 부여하지 마세요.  
>   
>  이 계정에 컴퓨터를 도메인에 조인시킬 수 있는 권한을 부여하지 마세요. 작업 순서 중에 컴퓨터를 도메인에 조인시켜야 하는 경우 [작업 순서 도메인 조인 계정](#task-sequence-domain-join-account)을 사용하세요.  

#### <a name="configure-the-network-access-account"></a>네트워크 액세스 계정 구성  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 그런 다음, 사이트를 선택합니다.  

2.  리본 메뉴의 **설정** 그룹에서 **사이트 구성 요소 구성**을 선택하고 **소프트웨어 배포**를 선택합니다.  

3.  **네트워크 액세스 계정** 탭을 선택합니다. 하나 이상의 계정을 설정하고 **확인**을 선택합니다.  


### <a name="package-access-account"></a>패키지 액세스 계정  

 **패키지 액세스 계정**을 통해 NTFS 권한을 설정하여 배포 지점의 패키지 콘텐츠에 액세스할 수 있는 사용자 및 사용자 그룹을 지정할 수 있습니다. 기본적으로 Configuration Manager에서는 일반 액세스 계정인 **사용자** 및 **관리자**에게만 액세스 권한을 부여합니다. 클라이언트 컴퓨터에 대한 액세스는 추가 Windows 계정 또는 그룹을 사용하여 제어할 수 있습니다. 모바일 디바이스에서는 항상 패키지 콘텐츠를 익명으로 검색하므로 패키지 액세스 계정을 사용하지 않습니다.  

 기본적으로 Configuration Manager는 콘텐츠 파일을 배포 지점에 복사할 때 로컬 **사용자** 그룹에 **읽기** 액세스 권한을, 로컬 **관리자** 그룹에는 **전체 제어** 권한을 부여합니다. 필요한 실제 권한은 패키지에 따라 다릅니다. 작업 그룹 또는 신뢰할 수 없는 포리스트에 클라이언트가 있는 경우 해당 클라이언트는 네트워크 액세스 계정을 사용하여 패키지 콘텐츠에 액세스합니다. 정의된 액세스 권한을 사용하여 네트워크 액세스 계정에 패키지에 대한 사용 권한이 있는지 확인합니다.  

 배포 지점에 액세스할 수 있는 도메인의 계정을 사용합니다. 패키지를 만든 후 계정을 생성하거나 수정하는 경우 패키지를 다시 배포해야 합니다. 패키지를 업데이트해도 패키지에 대한 NTFS 권한은 변경되지 않습니다.  

 **사용자** 그룹의 멤버 자격이 자동으로 추가하므로 네트워크 액세스 계정을 패키지 액세스 계정으로 추가할 필요는 없습니다. 패키지 액세스 계정을 네트워크 액세스 계정으로만 제한해도 클라이언트가 패키지에 액세스하지 못합니다.  

#### <a name="manage-package-access-accounts"></a>패키지 액세스 계정 관리  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 선택합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 액세스 계정을 관리할 콘텐츠 유형을 결정하고 제공 된 단계를 수행합니다.  

    -   **애플리케이션**: **애플리케이션 관리**를 확장하고 **애플리케이션**을 선택한 다음, 액세스 계정을 관리할 애플리케이션을 선택합니다.  

    -   **패키지**: **애플리케이션 관리**를 확장하고 **패키지**를 선택한 다음, 액세스 계정을 관리할 패키지를 선택합니다.  

    -   **소프트웨어 업데이트 배포 패키지**: **소프트웨어 업데이트**를 확장하고 **배포 패키지**를 선택한 다음, 액세스 계정을 관리할 배포 패키지를 선택합니다.  

    -   **드라이버 패키지**: **운영 체제**를 확장하고 **드라이버 패키지**를 선택한 다음, 액세스 계정을 관리할 드라이버 패키지를 선택합니다.  

    -   **OS 이미지**: **운영 체제**를 확장하고 **운영 체제 이미지**를 선택한 다음, 액세스 계정을 관리할 운영 체제 이미지를 선택합니다.  

    -   **OS 업그레이드 패키지**: **운영 체제**를 확장하고 **운영 체제 업그레이드 패키지**를 선택한 다음, 액세스 계정을 관리할 OS 업그레이드 패키지를 선택합니다.  

    -   **부팅 이미지**: **운영 체제**를 확장하고 **부팅 이미지**를 선택한 다음, 액세스 계정을 관리할 부팅 이미지를 선택합니다.  

3.  선택한 개체를 마우스 오른쪽 단추로 클릭한 후에 **액세스 계정 관리**를 선택합니다.  

4.  **계정 추가** 대화 상자에서 콘텐츠에 대한 액세스를 부여할 계정 유형을 지정한 다음 해당 계정과 연결된 액세스 권한을 지정합니다.  

    > [!NOTE]  
    >  계정에 사용자 이름을 추가하는 경우 Configuration Manager에서 해당 이름의 로컬 사용자 계정과 도메인 사용자 계정을 모두 찾으면 Configuration Manager에서 도메인 사용자 계정에 대한 액세스 권한을 설정합니다.  


### <a name="reporting-services-point-account"></a>보고 서비스 지점 계정  
 
 SQL Server Reporting Services에서는 **보고 서비스 지점 계정**을 사용하여 사이트 데이터베이스에서 Configuration Manager 보고서의 데이터를 검색합니다. 지정한 Windows 사용자 계정 및 암호는 암호화되어 SQL Server Reporting Services 데이터베이스에 저장됩니다.  

 > [!NOTE]  
 > 지정한 계정에는 SQL Reporting Services 데이터베이스를 호스팅하는 컴퓨터에 대한 **로컬로 로그온** 권한이 있어야 합니다.

 자세한 내용은 [보고 기능 소개](/sccm/core/servers/manage/introduction-to-reporting)를 참조하세요.


### <a name="remote-tools-permitted-viewer-accounts"></a>원격 도구 허용된 뷰어 계정  

 원격 제어에 대해 **허용된 뷰어** 로 지정한 계정은 클라이언트에서 원격 도구 기능을 사용하도록 허용한 사용자들입니다.  

자세한 내용은 [원격 제어 소개](/sccm/core/clients/manage/remote-control/introduction-to-remote-control)를 참조하세요.


### <a name="site-installation-account"></a>사이트 설치 계정
<!--SCCMDocs issue #572-->
도메인 사용자 계정을 사용하여 Configuration Manager 설치 프로그램을 실행하고 새 사이트를 설치할 서버에 로그인합니다.

이 계정에는 다음 권한이 필요합니다.  

- 다음 서버의**관리자**:
    - 사이트 서버  
    - 사이트 데이터베이스를 호스팅하는 각 서버  
    - 사이트에 대한 SMS 공급자의 각 인스턴스  

- 사이트 데이터베이스를 호스트하는 SQL Server 인스턴스에 대한**Sysadmin** 권한  

Configuration Manager 설치 프로그램은 이 계정을 [SMS Admins](#sms-admins) 그룹에 자동으로 추가합니다.

설치 후 이 계정은 Configuration Manager 콘솔에 대한 권한을 가진 유일한 사용자입니다. 이 계정을 제거해야 하는 경우 먼저 다른 사용자에게 해당 권한을 추가해야 합니다.

중앙 관리 사이트를 포함하도록 독립 실행형 사이트를 확장하는 경우, 이 계정에는 독립 실행형 기본 사이트의 **전체 관리자** 또는 **인프라 관리자** 역할 기반 관리 권한이 필요합니다.


### <a name="site-system-installation-account"></a>사이트 시스템 설치 계정  

 사이트 서버에서는 **사이트 시스템 설치 계정**을 사용하여 사이트 시스템을 설치, 다시 설치, 제거 및 설정합니다. 사이트 서버가 이 사이트 시스템에 대한 연결을 시작하도록 사이트 시스템을 설정하는 경우, Configuration Manager도 이 계정을 사용하여 사이트 시스템과 모든 역할을 설치한 후 사이트 시스템에서 데이터를 끌어옵니다. 각 사이트 시스템마다 다른 설치 계정이 있을 수 있지만 단일 설치 계정만 설정하여 해당 사이트 시스템의 모든 역할을 관리할 수 있습니다.  

 이 계정에는 대상 사이트 시스템에 대한 로컬 관리 권한이 필요합니다. 또한 이 계정은 대상 사이트 시스템의 보안 정책에 **네트워크에서 이 컴퓨터에 액세스**가 허용되어 있어야 합니다.  

 > [!TIP]  
 >  여러 도메인 컨트롤러가 있고 이러한 계정이 여러 도메인에서 사용되는 경우, 사이트 시스템을 설정하기 전에 Active Directory에서 이러한 계정을 복제했는지 확인합니다.  
 >   
 >  관리할 각 사이트 시스템에 로컬 계정을 지정하면 이 구성은 도메인 계정을 사용하는 것보다 안전합니다. 계정이 도용될 경우 공격자가 입힐 수 있는 피해를 제한합니다. 하지만 도메인 계정은 관리하기가 더 쉽습니다. 보안과 효과적인 관리 간의 적당한 균형을 고려합니다.  


### <a name="site-system-proxy-server-account"></a>사이트 시스템 프록시 서버 계정
<!--SCCMDocs issue #648-->
 다음 사이트 시스템 역할은 **사이트 시스템 프록시 서버 계정**을 사용하여 인증된 액세스 권한이 필요한 프록시 서버 또는 방화벽을 통해 인터넷에 액세스합니다.

- Asset Intelligence 동기화 지점
- Exchange Server 커넥터
- 서비스 연결 지점
- 소프트웨어 업데이트 지점

> [!IMPORTANT]  
>  필요한 프록시 서버나 방화벽에 대해 최소한의 권한이 있는 계정을 지정합니다.  

 자세한 내용은 [프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support)을 참조하세요.


### <a name="smtp-server-connection-account"></a>SMTP 서버 연결 계정  

 SMTP 서버에 인증된 액세스가 필요한 경우 사이트 서버에서는 **SMTP 서버 연결 계정**을 사용하여 이메일 경고를 보냅니다.  

> [!IMPORTANT]  
>  전자 메일을 보낼 수 있는 최소한의 권한이 있는 계정을 지정합니다.  

 자세한 내용은 [경고 및 상태 시스템 사용](/sccm/core/servers/manage/use-alerts-and-the-status-system)을 참조하세요.


### <a name="software-update-point-connection-account"></a>소프트웨어 업데이트 지점 연결 계정  

 사이트 서버에서는 다음 두 소프트웨어 업데이트 서비스에 대해 **소프트웨어 업데이트 지점 연결 계정**을 사용합니다.  

-   WSUS(Windows Server Update Services) - 제품 정의, 분류 및 업스트림 설정과 같은 설정을 설치합니다.  

-   WSUS Synchronization Manager - 업스트림 WSUS 서버 또는 Microsoft Update에 대한 동기화를 요청합니다.  

[사이트 시스템 설치 계정](#site-system-installation-account)은 소프트웨어 업데이트의 구성 요소를 설치할 수 있지만 소프트웨어 업데이트 지점에서는 소프트웨어 업데이트 관련 기능을 수행할 수 없습니다. 소프트웨어 업데이트 지점이 신뢰할 수 없는 포리스트에 있기 때문에 이 기능에 사이트 서버 컴퓨터 계정을 사용할 수 없는 경우 사이트 시스템 설치 계정 외에 이 계정을 지정해야 합니다.  

이 계정은 WSUS를 설치하는 컴퓨터의 로컬 관리자여야 합니다. 또한 로컬 **WSUS 관리자** 그룹의 일부여야 합니다.  

자세한 내용은 [소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates)을 참조하세요.


### <a name="source-site-account"></a>원본 사이트 계정  

 마이그레이션 프로세스에서는 **원본 사이트 계정**을 사용하여 원본 사이트의 SMS 공급자에 액세스합니다. 마이그레이션 작업용 데이터를 수집할 수 있도록 이 계정에는 원본 사이트에 있는 사이트 개체에 대한 **읽기** 권한이 있어야 합니다.  

 Configuration Manager 2007 배포 지점 또는 공동 배치된 배포 지점이 있는 보조 사이트가 있는 경우, Configuration Manager(현재 분기) 배포 지점으로 업그레이드할 때 이 계정에 **사이트** 클래스에 대한 **삭제** 권한도 있어야 합니다. 이 사용 권한은 업그레이드 중에 Configuration Manager 2007 사이트에서 배포 지점을 성공적으로 제거하기 위한 것입니다.  

> [!NOTE]  
>  원본 사이트 계정 및 [원본 사이트 데이터베이스 계정](#source-site-database-account)은 모두 Configuration Manager 콘솔의 **관리** 작업 영역 **계정** 노드에서 **마이그레이션 관리자**로 식별됩니다.  

 자세한 내용은 [계층 구조 간에 데이터 마이그레이션](https://docs.microsoft.com/sccm/core/migration/migrate-data-between-hierarchies)을 참조하세요.


### <a name="source-site-database-account"></a>원본 사이트 데이터베이스 계정  

 마이그레이션 프로세스에서는 **원본 사이트 데이터베이스 계정**을 사용하여 원본 사이트의 SQL Server 데이터베이스에 액세스합니다. 원본 사이트의 SQL Server 데이터베이스에서 데이터를 수집할 수 있도록 원본 사이트 데이터베이스 계정에는 원본 사이트의 SQL Server 데이터베이스에 대한 **읽기** 및 **실행** 권한이 있어야 합니다.  

 Configuration Manager(현재 분기) 컴퓨터 계정을 사용하는 경우 이 계정이 다음 사항을 모두 충족하는지 확인합니다.  
   
 - Configuration Manager 2007 사이트와 동일한 도메인에 있는 **Distributed COM Users** 보안 그룹의 구성원입니다.  
 - **SMS Admins** 보안 그룹의 구성원입니다.  
 - 모든 Configuration Manager 2007 개체에 대한 **읽기** 권한이 있습니다.  

> [!NOTE]  
>  원본 사이트 계정 및 [원본 사이트 데이터베이스 계정](#source-site-database-account)은 모두 Configuration Manager 콘솔의 **관리** 작업 영역 **계정** 노드에서 **마이그레이션 관리자**로 식별됩니다.  

 자세한 내용은 [계층 구조 간에 데이터 마이그레이션](https://docs.microsoft.com/sccm/core/migration/migrate-data-between-hierarchies)을 참조하세요.


### <a name="task-sequence-domain-join-account"></a>작업 순서 도메인 조인 계정 

 Windows 설치 프로그램은 **작업 순서 도메인 조인 계정**을 사용하여 새롭게 이미징된 컴퓨터를 도메인에 조인시킵니다. 이 계정은 **도메인 조인** 옵션을 사용하는 [도메인 또는 작업 그룹 조인](/sccm/osd/understand/task-sequence-steps#BKMK_JoinDomainorWorkgroup) 작업 순서 단계에서 필요합니다. 이 계정은 [네트워크 설정 적용](/sccm/osd/understand/task-sequence-steps#BKMK_ApplyNetworkSettings) 단계를 통해 설정할 수도 있지만 필수는 아닙니다.  

 이 계정에는 대상 도메인에 대한 **도메인 조인** 권한이 필요합니다.  

> [!TIP]  
>  도메인을 조인할 수 있는 최소 권한으로 도메인 사용자 계정을 하나 만들고 모든 작업 순서에 사용합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 할당하지 마세요.  
>   
>  이 계정에 네트워크 액세스 계정을 사용하지 마세요.  


### <a name="task-sequence-network-folder-connection-account"></a>작업 순서 네트워크 폴더 연결 계정  

 작업 순서 엔진에서는 **작업 순서 네트워크 폴더 연결 계정**을 사용하여 네트워크의 공유 폴더에 연결합니다. 이 계정은 [네트워크 폴더에 연결](/sccm/osd/understand/task-sequence-steps#BKMK_ConnectToNetworkFolder) 작업 순서 단계에 필요합니다.  

 이 계정에는 지정된 공유 폴더에 액세스할 수 있는 권한이 필요합니다. 도메인 사용자 계정이어야 합니다.  

> [!TIP]  
>  필요한 네트워크 리소스에 액세스할 수 있는 최소 권한이 있는 단일 도메인 사용자 계정을 생성하고 모든 작업 순서에 사용합니다.  

> [!IMPORTANT]  
>  이 계정에 대화형 로그인 권한을 할당하지 마세요.  
>   
>  이 계정에 네트워크 액세스 계정을 사용하지 마세요.  


### <a name="task-sequence-run-as-account"></a>작업 순서 실행 계정  

 작업 순서 엔진에서는 **작업 순서 실행 계정**을 사용하여 로컬 시스템 계정 이외의 자격 증명으로 명령줄을 실행합니다. 이 계정은 **이 단계를 다음 계정으로 실행** 옵션을 사용하는 [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) 작업 순서 단계에서 필요합니다.  

 작업 순서에 지정된 명령줄을 실행하는 데 필요한 최소 권한을 가지도록 계정을 설정합니다. 계정에는 대화형 로그인 권한이 필요합니다. 일반적으로 소프트웨어를 설치하고 네트워크 리소스에 액세스할 수 있는 권한이 있어야 합니다.  

> [!IMPORTANT]  
>  이 계정에 네트워크 액세스 계정을 사용하지 마세요.  
>   
>  계정을 도메인 관리자 계정으로 만들면 안 됩니다.  
>   
>  이 계정에 대해 로밍 프로필을 설정하면 안 됩니다. 작업 순서가 실행되는 경우 계정에 대한 로밍 프로필을 다운로드합니다. 이렇게 하면 프로필이 로컬 컴퓨터의 액세스에 대해 취약해집니다.  
>   
>  계정 범위를 제한해야 합니다. 예를 들어 작업 순서별로 다른 작업 순서 계정을 만듭니다. 그러면, 한 계정이 도용될 경우 해당 계정에 액세스할 수 있는 클라이언트 컴퓨터만 도용됩니다.  
>   
>  명령줄에 컴퓨터에 대한 관리 액세스 권한이 필요한 경우 작업 순서를 실행하는 모든 컴퓨터에서 이 계정에 대해서만 로컬 관리자 계정을 만드는 것이 좋습니다. 더 이상 필요하지 않으면 계정을 삭제합니다.  


## <a name="bkmk_sqlobjects"></a> Configuration Manager가 SQL에서 사용하는 사용자 개체 
<!--SCCMDocs issue #1160-->
Configuration Manager는 다음과 같은 사용자 개체를 SQL에서 자동으로 만들고 유지 관리합니다.  이러한 개체는 Configuration Manager 데이터베이스 내의 보안/사용자 아래에 있습니다.  

> [!IMPORTANT]  
>  이러한 개체를 수정하거나 제거하면 Configuration Manager 환경 내에서 급격한 문제가 발생할 수 있습니다.  이러한 개체는 변경하지 않는 것이 좋습니다.


### <a name="smsdbuserreadonly"></a>smsdbuser_ReadOnly

이 개체는 읽기 전용 컨텍스트에서 쿼리를 실행하는 데 사용됩니다.  이 개체는 여러 저장 프로시저에서 사용됩니다.


### <a name="smsdbuserreadwrite"></a>smsdbuser_ReadWrite

이 개체는 동적 SQL 문에 대한 사용 권한을 제공하는 데 사용됩니다.


### <a name="smsdbuserreportschema"></a>smsdbuser_ReportSchema

이 개체는 SQL Reporting 실행에 사용됩니다.  이 함수에는 저장 프로시저 spSRExecQuery가 함께 사용됩니다.
