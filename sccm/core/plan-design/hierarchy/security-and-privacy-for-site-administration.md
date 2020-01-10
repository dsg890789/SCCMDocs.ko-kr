---
title: 사이트 관리 보안 및 개인 정보
titleSuffix: Configuration Manager
description: Configuration Manager에서 사이트 관리를 위한 보안 및 개인 정보 최적화
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1d58176e-abc0-4087-8583-ce70deb4dcf5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fba51730cdf6d293af3d073b346b99916bac6672
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799729"
---
# <a name="security-and-privacy-for-site-administration-in-configuration-manager"></a>Configuration Manager에서 사이트 관리를 위한 보안 및 개인 정보

*적용 대상: Configuration Manager(현재 분기)*

이 문서에는 Configuration Manager 사이트 및 계층 구조에 대한 보안 및 개인 정보가 포함되어 있습니다.

## <a name="BKMK_Security_Sites"></a> 사이트 관리를 위한 보안 지침

다음 지침을 사용하여 Configuration Manager 사이트 및 계층 구조를 보호할 수 있습니다.  

### <a name="run-setup-from-a-trusted-source-and-secure-communication"></a>신뢰할 수 있는 원본에서 설치 프로그램을 실행하고 통신을 보호

원본 파일의 변조를 방지하기 위해 신뢰할 수 있는 소스에서 Configuration Manager 설치 프로그램을 실행합니다. 네트워크에 파일을 저장하는 경우 네트워크 위치를 보호합니다.  

네트워크 위치에서 설치 프로그램을 실행하는 경우 공격자가 네트워크를 통해 전송되는 파일을 변조할 수 없도록 설치 프로그램 파일의 원본 위치와 사이트 서버 간에 IPsec 또는 SMB 서명을 사용합니다.  

설치에 필요한 파일을 설치 다운로더를 사용하여 다운로드하는 경우 이러한 파일이 저장되는 위치를 보호해야 합니다. 또한 설치 프로그램을 실행할 때 이 위치의 통신 채널을 보호합니다.  

### <a name="extend-the-active-directory-schema-and-publish-sites-to-the-domain"></a>Active Directory 스키마 확장 및 도메인에 사이트 게시  

스키마 확장은 Configuration Manager를 실행하는 데 필요하지 않지만 보다 안전한 환경을 만듭니다. 클라이언트와 사이트 서버는 신뢰할 수 있는 원본에서 정보를 검색할 수 있습니다.  

클라이언트가 트러스트되지 않은 도메인에 있는 경우 클라이언트 도메인에 다음과 같은 사이트 시스템 역할을 배포합니다.  

- 관리 지점  

- 배포 지점  

> [!NOTE]  
> Configuration Manager용 트러스트된 도메인에는 Kerberos 인증이 필요하므로, 사이트 서버 포리스트와의 양방향 포리스트 트러스트가 없는 다른 포리스트에 있는 클라이언트는 트러스트되지 않은 도메인에 있는 것으로 간주됩니다. 외부 트러스트는 이 용도로 충분하지 않습니다.  

### <a name="use-ipsec-to-secure-communications"></a>IPsec을 사용하여 통신 보호

Configuration Manager는 SQL Server를 실행하는 컴퓨터와 사이트 서버 간의 통신은 보호하지만 사이트 시스템 역할과 SQL Server 간의 통신은 보호하지 않습니다. 사이트 간 통신에는 HTTPS를 사용하여 일부 사이트 시스템만 구성할 수 있습니다.  

추가 컨트롤을 사용하여 이러한 서버 간 채널을 보호하지 않을 경우 공격자가 사이트 시스템에 대해 다양한 스푸핑 및 중간자(man-in-the-middle) 공격을 사용할 수 있습니다. IPsec을 사용할 수 없는 경우 SMB 서명을 사용합니다.  

> [!Important]  
> 사이트 서버와 패키지 원본 서버 간 통신 채널을 보호합니다. 이 통신은 SMB를 사용합니다. IPsec을 사용하여 이 통신을 보호할 수 없는 경우 클라이언트에서 파일을 다운로드하여 실행하기 전에 파일이 변조되지 않도록 SMB 서명을 사용하세요.  

### <a name="dont-change-the-default-security-groups"></a>기본 보안 그룹은 변경하지 않습니다

Configuration Manager에서 사이트 시스템 통신을 위해 만들고 관리하는 보안 그룹을 변경하지 마세요.

- **SMS_SiteSystemToSiteServerConnection_MP_&lt;사이트 코드\>**  

- **SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;사이트 코드\>**  

- **SMS_SiteSystemToSiteServerConnection_Stat_&lt;사이트 코드\>**  

Configuration Manager에서는 이러한 보안 그룹을 자동으로 만들고 관리합니다. 이 동작에는 사이트 시스템 역할이 제거될 때 컴퓨터 계정을 제거하는 것이 포함됩니다.  

서비스 연속성과 최소 권한을 위해서는 이러한 그룹을 수동으로 편집하지 않아야 합니다.  

### <a name="manage-the-trusted-root-key-provisioning-process"></a>신뢰할 수 있는 루트 키 프로비전 프로세스 관리

클라이언트가 글로벌 카탈로그에서 Configuration Manager 정보를 쿼리할 수 없는 경우 신뢰할 수 있는 루트 키를 사용하여 유효한 관리 지점을 인증해야 합니다. 신뢰할 수 있는 루트 키는 클라이언트 레지스트리에 저장됩니다. 그룹 정책 또는 수동 구성을 사용하여 설정할 수 있습니다.  

클라이언트가 관리 지점에 처음으로 연결하기 전에 신뢰할 수 있는 루트 키 사본이 없는 경우 클라이언트는 통신하는 첫 번째 관리 지점을 신뢰합니다. 공격자가 클라이언트를 무단 관리 지점으로 연결시키는 위험을 줄이기 위해 신뢰할 수 있는 루트 키로 클라이언트를 미리 프로비전할 수 있습니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForRTK)을 참조하세요.  

### <a name="use-non-default-port-numbers"></a>기본 포트 번호 이외의 번호 사용

기본 포트 번호 이외의 번호를 사용하면 추가 보안을 제공할 수 있습니다. 공격자가 공격을 준비하기 위해 환경을 탐색하기가 더 어려워집니다. 기본 포트 이외의 포트를 사용하려는 경우 Configuration Manager를 설치하기 전에 포트를 계획하세요. 계층 구조의 모든 사이트에서 일관되게 사용합니다. 클라이언트 요청 포트와 Wake On LAN은 기본 포트 번호 이외의 번호를 사용할 수 있는 예입니다.  

### <a name="use-role-separation-on-site-systems"></a>사이트 시스템에서 역할 구분 사용

단일 컴퓨터에 모든 사이트 시스템 역할을 설치할 수는 있지만 프로덕션 네트워크에서는 이 방법이 좀처럼 사용되지 않습니다. 단일 실패 지점이 만들어지기 때문입니다.  

### <a name="reduce-the-attack-profile"></a>공격 프로필 축소

각 사이트 시스템 역할을 서로 다른 서버에 분리하면 한 사이트 시스템의 취약성에 대한 공격이 다른 사이트 시스템에 대해 사용될 가능성이 줄어듭니다. 많은 역할은 사이트 시스템에 IIS(인터넷 정보 서비스) 설치가 필요하며 이로 인해 공격에 대한 취약성이 증가할 수 있습니다. 하드웨어 비용을 줄이기 위해 역할을 결합해야 할 경우 IIS 역할을 IIS가 필요한 다른 사이트 시스템 역할과만 결합하세요.  

> [!IMPORTANT]  
> 대체 상태 지점 역할은 예외입니다. 이 사이트 시스템 역할은 클라이언트에서 인증되지 않은 데이터를 수락하므로 대체 상태 지점 역할을 다른 Configuration Manager 사이트 시스템 역할에 할당하지 마세요.  

### <a name="configure-static-ip-addresses-for-site-systems"></a>사이트 시스템의 고정 IP 주소 구성

고정 IP 주소를 사용하면 이름 확인 공격으로부터 보호하기가 더 쉽습니다.  

또한 고정 IP 주소를 사용하면 IPsec 구성이 더 쉽습니다. IPsec 사용은 Configuration Manager에서 사이트 시스템 간 통신을 보호하기 위한 보안 모범 사례입니다.  

### <a name="dont-install-other-applications-on-site-system-servers"></a>사이트 시스템 서버에 다른 애플리케이션을 설치하지 않습니다

사이트 시스템 서버에 다른 애플리케이션을 설치하면 Configuration Manager의 공격에 대한 취약성이 증가합니다. 또한 비호환성 문제가 발생할 위험이 있습니다.  

### <a name="require-signing-and-enable-encryption-as-a-site-option"></a>사이트 옵션으로 서명을 요구하고 암호화를 사용하도록 설정

사이트에 서명 및 암호화 옵션을 사용하도록 설정합니다. 모든 클라이언트가 SHA-256 해시 알고리즘을 지원할 수 있는지 확인한 다음 **SHA-256 필요** 옵션을 사용하도록 설정합니다.  

### <a name="restrict-and-monitor-administrative-users"></a>관리자를 제한하고 모니터합니다.

신뢰하는 사용자에게만 Configuration Manager에 대한 관리 액세스 권한을 부여합니다. 기본 제공 보안 역할을 사용하거나 보안 역할을 사용자 지정하여 최소 권한만 부여합니다. 소프트웨어와 구성을 만들고 수정하고 배포할 수 있는 관리자는 잠재적으로 Configuration Manager 계층 구조의 디바이스를 제어할 수 있습니다.  

정기적으로 관리자 할당과 권한 수준을 감사하여 변경이 필요한지 확인합니다.  

자세한 내용은 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요.  

### <a name="secure-configuration-manager-backups"></a>Configuration Manager 백업 보호

Configuration Manager를 백업하는 경우 인증서와 공격자가 가장하는 데 사용할 수 있는 기타 중요한 데이터가 백업 정보에 포함됩니다.  

네트워크를 통해 이 데이터를 전송할 때에는 SMB 서명이나 IPsec를 사용하고 백업 위치를 보호합니다.  

### <a name="secure-locations-for-exported-objects"></a>내보낸 개체의 위치 보호

Configuration Manager 콘솔에서 네트워크 위치로 개체를 가져오거나 내보낼 때는 항상 해당 위치와 네트워크 채널을 보호하세요.

네트워크 폴더에 액세스할 수 있는 사용자를 제한합니다.  

내보내는 데이터를 공격자가 변조하지 못하도록 네트워크 위치와 사이트 서버 사이에 SMB 서명 또는 IPsec을 사용합니다. 또한 Configuration Manager 콘솔을 실행하는 컴퓨터와 사이트 서버 간 통신을 보호하세요. IPsec를 사용해서 네트워크상의 데이터를 암호화하여 정보 유출을 방지합니다.  

### <a name="manually-remove-certificates-from-failed-servers"></a>오류가 발생한 서버에서 수동으로 인증서 제거

사이트 시스템이 제대로 제거되지 않았거나 작동을 멈춘 후에 복원할 수 없는 경우 다른 Configuration Manager 서버에서 이 서버의 Configuration Manager 인증서를 수동으로 제거합니다.

원래 사이트 시스템과 사이트 시스템 역할을 사용하여 설정된 피어 트러스트를 제거하려면 다른 사이트 시스템 서버의 **신뢰할 수 있는 사용자** 인증서 저장소에서 오류가 발생한 서버의 Configuration Manager 인증서를 수동으로 제거합니다. 이 작업은 서버를 다시 포맷하지 않고 재사용하는 경우에 중요합니다.  

자세한 내용은 [서버 통신을 위한 암호화 컨트롤](/sccm/core/plan-design/security/cryptographic-controls-technical-reference#cryptographic-controls-for-server-communication)을 참조하세요.  

### <a name="dont-configure-internet-based-site-systems-to-bridge-the-perimeter-network"></a>인터넷 기반 사이트 시스템이 경계 네트워크에 연결되도록 구성하지 않습니다

경계 네트워크와 인트라넷에 연결되도록 사이트 시스템 서버를 멀티홈으로 구성해서는 안 됩니다. 이 구성을 사용하면 인터넷 기반 사이트 시스템이 인터넷과 인트라넷의 클라이언트 연결을 수락할 수 있지만 경계 네트워크와 인트라넷 사이의 보안 경계가 사라집니다.  

### <a name="configure-the-site-server-to-initiate-connections-to-perimeter-networks"></a>경계 네트워크에 대한 연결을 시작하도록 사이트 서버 구성

사이트 시스템 서버가 경계 네트워크와 같이 신뢰할 수 없는 네트워크에 있는 경우 사이트 시스템에 대한 연결을 시작하도록 사이트 서버를 구성합니다.

기본적으로 사이트 시스템은 데이터를 전송하기 위해 사이트 서버에 대한 연결을 시작합니다. 신뢰할 수 없는 네트워크에서 신뢰할 수 있는 네트워크로 연결이 시작되는 경우 이 구성은 보안상 위험할 수 있습니다. 사이트 시스템이 인터넷으로부터 연결을 수락하거나 트러스트되지 않은 포리스트에 있는 경우 사이트 시스템의 **이 사이트 시스템의 연결을 시작하려면 사이트 서버 필요** 옵션을 구성합니다. 사이트 시스템과 모든 역할을 설치한 후에는 신뢰할 수 있는 네트워크에서 사이트 서버에 의해 모든 연결이 시작됩니다.  

### <a name="use-ssl-bridging-and-termination-with-authentication"></a>인증과 함께 SSL 브리징 및 종료 사용

인터넷 기반 클라이언트 관리에 웹 프록시 서버를 사용하는 경우 인증과 함께 종료를 사용하여 SSL에 대한 SSL 브리징을 사용합니다.

프록시 웹 서버에서 SSL 종료를 구성하면 인터넷 패킷은 내부 네트워크로 전달되기 전에 검사됩니다. 프록시 웹 서버는 클라이언트에서의 연결을 인증하고 종료한 다음, 인터넷 기반 사이트 시스템에 대한 새로운 인증 연결을 엽니다.  

Configuration Manager 클라이언트 컴퓨터가 프록시 웹 서버를 사용하여 인터넷 기반 사이트 시스템에 연결하는 경우 클라이언트 ID(GUID)가 패킷 페이로드 내에 안전하게 포함됩니다. 그러면 관리 지점은 프록시 웹 서버를 클라이언트로 간주하지 않습니다.

프록시 웹 서버가 SSL 브리징 요구 사항을 지원할 수 없는 경우 SSL 터널링도 지원됩니다. 이 옵션은 보안 수준이 낮습니다. 인터넷의 SSL 패킷은 종료 없이 사이트 시스템에 전달됩니다. 그러면 패킷에서 악성 콘텐츠를 검사할 수 없습니다.  

> [!WARNING]  
> Configuration Manager가 등록한 모바일 디바이스는 SSL 브리징을 사용할 수 없습니다. SSL 터널링만 사용해야 합니다.  

### <a name="configurations-to-use-if-you-configure-the-site-to-wake-up-computers-to-install-software"></a>소프트웨어 설치를 위해 컴퓨터의 절전 모드를 해제하도록 사이트를 구성하는 경우 사용하는 구성

- 기존 절전 모드 해제 패킷을 사용하는 경우 서브넷 지향 브로드캐스트보다는 유니캐스트를 사용합니다.  

- 서브넷 지향 브로드캐스트를 사용해야 할 경우 라우터가 기본 포트 번호가 아닌 번호에서만 사이트 서버의 IP 지향 브로드캐스트에 한해 이를 허용하도록 구성합니다.  

다양한 Wake On LAN 기술에 대한 자세한 내용은 [클라이언트를 절전 모드에서 해제하는 방식 계획](/sccm/core/clients/deploy/plan/plan-wake-up-clients)을 참조하세요.

### <a name="if-you-use-email-notification-configure-authenticated-access-to-the-smtp-mail-server"></a>전자 메일 알림을 사용 시 SMTP 메일 서버에 대한 인증된 액세스 구성

가능하면 항상 인증된 액세스를 지원하는 메일 서버를 사용합니다. 사이트 서버의 컴퓨터 계정을 인증에 사용합니다. 인증을 위해 사용자 계정을 지정해야 할 경우 최소 권한을 갖는 계정을 사용합니다.  


## <a name="BKMK_Security_SiteServer"></a> 사이트 서버의 보안 지침

다음 지침을 사용하여 Configuration Manager 사이트 서버를 보호할 수 있습니다.  

### <a name="install-configuration-manager-on-a-member-server-instead-of-a-domain-controller"></a>Configuration Manager를 도메인 컨트롤러 대신 구성원 서버에 설치

Configuration Manager 사이트 서버 및 사이트 시스템은 도메인 컨트롤러에 설치할 필요가 없습니다. 도메인 컨트롤러에는 도메인 데이터베이스 외에 로컬 SAM(Security Accounts Management) 데이터베이스가 없습니다. 구성원 서버에 Configuration Manager를 설치할 경우 도메인 데이터베이스가 아닌 로컬 SAM 데이터베이스에서 Configuration Manager 계정을 유지 관리할 수 있습니다.  

이렇게 하면 도메인 컨트롤러에서 공격 노출 영역도 줄일 수 있습니다.  

### <a name="install-secondary-sites-without-copying-the-files-over-the-network"></a>네트워크를 통해 파일을 복사하지 않고 보조 사이트 설치

설치 프로그램을 실행하고 보조 사이트를 만들 때 상위 사이트에서 보조 사이트로 파일을 복사하는 옵션을 선택하지 마세요. 네트워크 원본 위치도 사용하지 않습니다. 네트워크를 통해 파일을 복사하면 노련한 공격자는 보조 사이트 설치 패키지를 가로챈 후 설치 전에 파일을 무단 변경할 수도 있습니다. 이 공격의 시간을 선택하기는 어렵습니다. 파일을 전송할 때 IPsec 또는 SMB를 사용하면 이러한 공격을 최소화할 수 있습니다.  

네트워크를 통해 파일을 복사하는 대신 보조 사이트 서버에서 원본 파일을 미디어 폴더에서 로컬 폴더로 복사합니다. 그런 다음 설치 프로그램을 실행하여 보조 사이트를 만들 때 **설치 원본 파일** 페이지에서 **보조 사이트 컴퓨터에서 다음 위치의 원본 파일 사용(가장 안전)** 을 선택하고 이 폴더를 지정합니다.  

자세한 내용은 [보조 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary)를 참조하세요.

### <a name="site-role-installation-inherits-permissions-from-drive-root"></a>사이트 역할 설치는 드라이브 루트에서 사용 권한을 상속

<!-- SCCMDocs#1380 -->
서버에 첫 번째 사이트 시스템 역할을 설치하기 전에 시스템 드라이브 사용 권한을 적절히 구성합니다. 예를 들어 `C:\SMS_CCM`은 `C:\`에서 사용 권한을 상속합니다. 드라이브의 루트가 적절히 보호되지 않을 경우 낮은 권한의 사용자가 Configuration Manager 폴더의 콘텐츠에 액세스하거나 콘텐츠를 수정할 수 있습니다.


## <a name="BKMK_Security_SQLServer"></a> SQL Server 보안 가이드

Configuration Manager에서는 SQL Server를 백 엔드 데이터베이스로 사용합니다. 데이터베이스가 손상되면 공격자가 Configuration Manager를 우회할 수 있습니다. 공격자는 SQL Server에 직접 액세스하는 경우 Configuration Manager를 통해 공격을 시작할 수 있습니다. SQL Server에 대한 공격을 큰 위험으로 간주하고 적절한 방법으로 완화하세요.  

다음 보안 지침을 사용하여 Configuration Manager의 SQL Server를 보호할 수 있습니다.  

### <a name="dont-use-the-configuration-manager-site-database-server-to-run-other-sql-server-applications"></a>Configuration Manager 사이트 데이터베이스 서버를 사용하여 다른 SQL Server 애플리케이션을 실행하지 않습니다

Configuration Manager 사이트 데이터베이스 서버에 대한 액세스를 늘리면 Configuration Manager 데이터의 위험도 늘어납니다. Configuration Manager 사이트 데이터베이스 보안이 손상되면 같은 SQL Server 컴퓨터에 있는 다른 애플리케이션도 위험해집니다.  

### <a name="configure-sql-server-to-use-windows-authentication"></a>Windows 인증을 사용하도록 SQL Server를 구성합니다

Configuration Manager는 Windows 계정 및 Windows 인증을 사용하여 사이트 데이터베이스에 액세스하지만 SQL Server 혼합 모드를 사용하도록 SQL Server를 구성할 수도 있습니다. SQL Server 혼합 모드는 데이터베이스에 액세스할 수 있는 추가 SQL 로그인을 허용합니다. 이 구성은 필요하지 않으며 공격에 대한 취약성을 늘립니다.  

### <a name="update-sql-server-express-at-secondary-sites"></a>보조 사이트에서 SQL Server Express 업데이트

기본 사이트를 설치할 때 Configuration Manager는 SQL Server Express를 Microsoft 다운로드 센터에서 다운로드합니다. 그런 다음 기본 사이트 서버에 파일을 복사 합니다. 보조 사이트를 설치하면서 SQL Server Express를 설치하는 옵션을 선택하면 Configuration Manager는 이전에 다운로드한 버전을 설치합니다. 새 버전을 사용할 수 있는지 여부는 확인하지 않습니다. 보조 사이트에 최신 버전이 설치되도록 하려면 다음 작업 중 하나를 수행하세요.  

- 보조 사이트를 설치한 후 보조 사이트 서버에서 Windows 업데이트를 실행합니다.  

- 보조 사이트를 설치하기 전에 보조 사이트 서버에 SQL Server Express를 수동으로 설치합니다. 최신 버전과 모든 소프트웨어 업데이트를 설치해야 합니다. 그런 다음 보조 사이트를 설치하고 기존 SQL Server 인스턴스를 사용하는 옵션을 선택합니다.  

설치된 모든 버전의 SQL Server에 대해 Windows 업데이트를 정기적으로 실행합니다. 이 방법을 사용하면 최신 소프트웨어 업데이트를 적용할 수 있습니다.  

### <a name="follow-general-guidance-for-sql-server"></a>SQL Server에 대한 일반적인 지침에 따릅니다

사용 중인 SQL Server 버전에 대한 일반적인 지침을 확인하고 따릅니다. 그러나 Configuration Manager에 대한 다음 요구 사항도 고려해야 합니다.  

- 사이트 서버의 컴퓨터 계정은 SQL Server를 실행하는 컴퓨터에서 관리자 그룹의 구성원이어야 합니다. SQL Server에서 "관리자 계정을 명시적으로 프로비전"하는 권장 사항을 따를 경우 사이트 서버에서 설치 프로그램을 실행하는 데 사용할 계정은 SQL 사용자 그룹의 구성원이어야 합니다.  

- 도메인 사용자 계정을 사용하여 SQL Server를 설치하는 경우 사이트 서버 컴퓨터 계정이 Active Directory Domain Services에 게시되는 SPN(서비스 사용자 이름)을 사용하도록 구성되었는지 확인하세요. SPN이 없으면 Kerberos 인증 및 Configuration Manager 설치에 실패합니다.  


## <a name="BKMK_Security_IIS"></a> IIS를 실행하는 사이트 시스템 보안 지침

Configuration Manager의 여러 사이트 시스템 역할에는 IIS가 필요합니다. IIS 보안을 설정하면 Configuration Manager가 올바르게 작동할 수 있고 보안 공격의 위험도 감소합니다. 적절한 경우 IIS가 필요한 서버 수를 최소화합니다. 예를 들어 인터넷 기반 클라이언트 관리를 위한 고가용성 및 네트워크 격리를 고려하여 클라이언트 기반을 지원하는 데 필요한 수만큼만 관리 지점을 실행하세요.  

다음 지침을 사용하여 IIS를 실행하는 사이트 시스템을 보호할 수 있습니다.  

### <a name="disable-iis-functions-that-you-dont-require"></a>필요하지 않은 IIS 기능을 사용하지 않도록 설정합니다

설치할 사이트 시스템 역할에 대해 최소 IIS 기능만 설치합니다. 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.  

### <a name="configure-the-site-system-roles-to-require-https"></a>HTTPS가 필요하도록 사이트 시스템 역할을 구성합니다

클라이언트가 HTTPS 대신 HTTP를 사용하여 사이트 시스템에 연결하는 경우 Windows 인증을 사용합니다. 이 동작은 Kerberos 인증 대신 NTLM 인증을 사용하는 것으로 변경될 수 있습니다. NTLM 인증이 사용되면 클라이언트는 허위 서버에 연결할 수도 있습니다.  

배포 지점은 이 지침의 예외가 될 수 있습니다. 배포 지점이 HTTPS에 대해 구성된 경우 패키지 액세스 계정이 작동하지 않습니다. 패키지 액세스 계정은 콘텐츠에 대한 권한 부여를 제공하므로 이를 통해 해당 콘텐츠에 액세스할 수 있는 사용자를 제한할 수 있습니다. 자세한 내용은 [콘텐츠 관리에 대한 보안 모범 사례](/sccm/core/plan-design/hierarchy/security-and-privacy-for-content-management#BKMK_Security_ContentManagement)를 참조하세요.  

### <a name="configure-a-certificate-trust-list-ctl-in-iis-for-site-system-roles"></a>IIS에서 사이트 시스템 역할에 대해 CTL(Certificate Trust List) 구성

사이트 시스템 역할:  

- HTTPS에 대해 구성하는 배포 지점  

- HTTPS에 대해 구성하고 모바일 디바이스를 지원하도록 설정하는 관리 지점

CTL은 신뢰할 수 있는 루트 인증 기관(CA)의 정의된 목록입니다. CTL을 그룹 정책 및 PKI (공개 키 인프라) 배포와 함께 사용하면 네트워크에 구성된 기존의 신뢰할 수 있는 루트 CA를 보완할 수 있습니다. Microsoft Windows와 함께 자동으로 설치되거나 Windows 엔터프라이즈 루트 CA를 통해 추가되는 CA가 그 예입니다. IIS에서 CTL이 구성되면 이러한 신뢰할 수 있는 루트 CA의 하위 집합이 정의됩니다.  

이 하위 집합을 통해 보안을 더욱 효율적으로 제어할 수 있습니다. CTL은 허용되는 클라이언트 인증서를 CTL의 CA 목록에서 발급한 인증서만으로 제한합니다. 예를 들어 Windows는 VeriSign과 Thawte 등 잘 알려진 여러 타사 CA 인증서와 함께 제공됩니다.

기본적으로 IIS를 실행하는 컴퓨터는 이러한 유명 CA에 연결되는 인증서를 신뢰합니다. 나열된 사이트 시스템 역할의 CTL로 IIS를 구성하지 않으면 사이트는 이러한 CA에서 발급한 인증서가 있는 모든 디바이스를 유효한 클라이언트로 승인합니다. 이러한 CA가 포함되지 않은 CTL을 사용하여 IIS를 구성하면 인증서가 해당 CA에 연결된 경우 사이트는 클라이언트 연결을 거부합니다. Configuration Manager 클라이언트가 나열된 사이트 시스템 역할에 대해 승인되려면 Configuration Manager 클라이언트가 사용하는 CA를 지정하는 CTL로 IIS를 구성해야 합니다.  

> [!NOTE]  
> 나열된 사이트 시스템 역할에 대해서만 IIS에서 CTL을 구성하면 됩니다. Configuration Manager가 관리 지점에 대해 사용하는 인증서 발급자 목록은 HTTPS 관리 지점에 연결하는 클라이언트 컴퓨터에 대해 동일한 기능을 제공합니다.  

IIS에서 신뢰할 수 있는 CA 목록을 구성하는 자세한 방법은 IIS 설명서를 참조하세요.  

### <a name="dont-put-the-site-server-on-a-computer-with-iis"></a>사이트 서버는 IIS를 실행하는 컴퓨터에 설치하지 않습니다

역할 분리는 공격 프로필을 축소시키고 복구 능력을 높이는 데 도움이 됩니다. 사이트 서버의 컴퓨터 계정에는 일반적으로 모든 사이트 시스템 역할에 대한 관리자 권한이 있습니다. 클라이언트 강제 설치를 사용 하는 경우 Configuration Manager 클라이언트에 대해서도 이러한 권한이 있을 수 있습니다.  

### <a name="use-dedicated-iis-servers-for-configuration-manager"></a>Configuration Manager에 전용 IIS 서버 사용

Configuration Manager에서도 사용되는 IIS 서버에 여러 웹 기반 애플리케이션을 호스트할 수 있지만 이렇게 하면 공격 노출 영역이 크게 늘어날 수 있습니다. 잘못 구성된 애플리케이션으로 인해 공격자가 Configuration Manager 사이트 시스템의 제어 권한을 얻을 수 있습니다. 이러한 침해로 인해 공격자가 계층 구조에 대한 제어 권한을 얻을 수 있습니다.  

Configuration Manager 사이트 시스템에서 다른 웹 기반 애플리케이션을 실행해야 할 경우 Configuration Manager 사이트 시스템에 대한 사용자 지정 웹 사이트를 만드세요.  

### <a name="use-a-custom-website"></a>사용자 지정 웹 사이트 사용

IIS를 실행하는 사이트 시스템의 경우 기본 웹 사이트 대신 사용자 지정 웹 사이트를 사용하도록 Configuration Manager를 구성합니다. 사이트 시스템에서 다른 웹 애플리케이션을 실행해야 하는 경우 사용자 지정 웹 사이트를 사용해야 합니다. 이 설정은 특정 사이트 시스템에 대한 설정이 아닌 사이트 전체 설정입니다.  

### <a name="when-you-use-custom-websites-remove-the-default-virtual-directories"></a>사용자 지정 웹 사이트를 사용하는 경우 기본 가상 디렉터리 제거

기본 웹 사이트 사용에서 사용자 지정 웹 사이트 사용으로 변경해도 Configuration Manager는 이전 가상 디렉터리를 제거하지 않습니다. Configuration Manager에서 원래 기본 웹 사이트 아래에 만들었던 가상 디렉터리를 제거하세요.  

예를 들어 배포 지점의 다음 가상 디렉터리를 제거하세요.  

- SMS_DP_SMSPKG$  

- SMS_DP_SMSSIG$  

- NOCERT_SMS_DP_SMSPKG$  

- NOCERT_SMS_DP_SMSSIG$  

### <a name="follow-iis-server-security-guidance"></a>IIS 서버 보안 지침 따르기

사용 중인 IIS Server 버전에 대한 일반적인 지침을 확인하고 따릅니다. 특정 사이트 시스템 역할에 대한 Configuration Manager의 모든 요구 사항을 고려해야 합니다. 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.  


## <a name="BKMK_Security_ManagementPoint"></a> 관리 지점 보안 지침

관리 지점은 디바이스와 Configuration Manager 간의 기본 인터페이스입니다. 관리 지점 및 관리 지점이 실행되는 서버에 대한 공격은 큰 위험으로 간주하고 적절히 완화합니다. 적절한 보안 지침을 모두 적용하고 비정상적인 활동을 모니터하세요.  

다음 지침을 사용하면 Configuration Manager에서 관리 지점을 보호할 수 있습니다.  

### <a name="assign-the-client-on-a-management-point-to-the-same-site"></a>관리 지점의 클라이언트를 동일한 사이트에 할당

관리 지점에 있는 Configuration Manager 클라이언트가 해당 관리 지점의 사이트가 아닌 다른 사이트에 할당되지 않도록 합니다.  

이전 버전에서 Configuration Manager 현재 분기로 마이그레이션하는 경우 관리 지점의 클라이언트를 최대한 빨리 새 사이트로 마이그레이션합니다.  


## <a name="BKMK_Security_FSP"></a> 대체 상태 지점 보안 지침

Configuration Manager에 대체 상태 지점을 설치하는 경우 다음 보안 지침을 따르세요.

대체 상태 지점 설치와 관련된 보안 고려 사항에 대한 자세한 내용은 [대체 상태 지점 필요 여부 결정](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#fallback-status-point)을 참조하세요.  

### <a name="dont-run-any-other-roles-on-the-same-site-system"></a>같은 사이트 시스템에서 다른 역할을 실행하지 않습니다

대체 상태 지점은 모든 컴퓨터의 인증되지 않은 통신을 허용하도록 설계되었습니다. 다른 역할이나 도메인 컨트롤러를 사용하여이 사이트 시스템 역할을 실행하는 경우 해당 서버의 위험이 크게 늘어납니다.  

### <a name="install-the-fallback-status-point-before-you-install-clients-with-pki-certificates"></a>PKI 인증서를 사용하여 클라이언트를 설치하기 전에 대체 상태 지점 설치

Configuration Manager 사이트 시스템에서 HTTP 클라이언트 통신을 허용하지 않는 경우 PKI 관련 인증서 문제로 인해 클라이언트가 관리되지 않는다는 사실을 모를 수도 있습니다. 클라이언트를 대체 상태 지점에 할당하면 클라이언트가 대체 상태 지점을 통해 이러한 인증서 문제를 보고합니다.  

보안상의 이유로 대체 상태 지점은 설치가 완료된 클라이언트에 할당할 수 없습니다. 클라이언트 설치 중에만 이 역할을 할당할 수 있습니다.  

### <a name="avoid-using-the-fallback-status-point-in-the-perimeter-network"></a>경계 네트워크에서 대체 상태 지점을 사용하지 않습니다

대체 상태 지점은 모든 클라이언트의 데이터를 수락하며, 이는 의도된 동작입니다. 경계 네트워크의 대체 상태 지점은 인터넷 기반 클라이언트 문제 해결에 도움이 될 수 있지만 공개적으로 액세스할 수 있는 네트워크에서 인증되지 않은 데이터를 수용하는 사이트 시스템에 발생할 수 있는 위험과 문제 해결의 이점의 경중을 따져야 합니다.  

경계 네트워크 또는 신뢰할 수 없는 네트워크에 대체 상태 지점을 설치하는 경우 데이터 전송을 시작하도록 사이트 서버를 구성합니다. 대체 상태 지점이 사이트 서버에 대한 연결을 시작하도록 허용하는 기본 설정을 사용하지 마세요.  


## <a name="BKMK_SecurityIssues_Clients"></a> 사이트 관리에 대한 보안 문제

Configuration Manager에 대한 다음과 같은 보안 문제를 검토합니다.  

- Configuration Manager에는 권한 있는 관리자가 Configuration Manager를 사용하여 네트워크를 공격하는 경우 방어할 수 있는 수단이 없습니다. 권한이 없는 관리자는 보안 위험이 높습니다. 이러한 사용자는 다음 전략을 포함한 여러 공격을 시작할 수 있습니다.  

    - 소프트웨어 배포를 사용하여 조직 내의 모든 Configuration Manager 클라이언트 컴퓨터에 악성 소프트웨어를 자동으로 설치 및 실행할 수 있습니다.  

    - 클라이언트 승인 없이 Configuration Manager 클라이언트를 원격 제어할 수 있습니다.  

    - 빠른 폴링 간격과 엄청난 양의 인벤토리를 구성할 수 있습니다. 이 작업은 클라이언트와 서버에 대한 서비스 거부 공격을 만듭니다.  

    - 계층 내의 한 사이트를 사용하여 다른 사이트의 Active Directory 데이터에 데이터를 쓸 수 있습니다.  

    사이트 계층 구조가 보안 경계가 됩니다. 사이트는 관리 경계로만 고려합니다.  

    모든 관리자 작업을 감사하고 감사 로그를 정기적으로 검토해야 합니다. 모든 Configuration Manager 관리자는 고용 전에 신원 조사를 거쳐야 합니다. 고용 조건으로 주기적 재조사가 필요합니다.  

- 등록 지점이 손상되면 공격자가 인증용 인증서를 얻을 수 있습니다. 공격자는 모바일 디바이스를 등록한 사용자의 자격 증명을 도용할 수 있습니다.  

    등록 지점은 CA와 통신합니다. 등록 지점은 Active Directory 개체를 만들고 수정하고 삭제할 수 있습니다. 경계 네트워크에는 등록 지점을 절대 설치하면 안 됩니다. 항상 비정상적인 활동을 모니터링하세요.  

- 인터넷 기반 클라이언트 관리를 위한 사용자 정책을 허용하면 공격 프로필이 늘어납니다.  

    클라이언트-서버 연결에 PKI 인증서를 사용하는 것 외에 이러한 구성에는 Windows 인증이 필요합니다. 이 동작은 Kerberos 인증 대신 NTLM 인증을 사용하는 것으로 변경될 수 있습니다. NTLM 인증은 가장 및 재생 공격에 취약합니다. 인터넷에서 사용자를 성공적으로 인증하려면 인터넷 기반 사이트 시스템에서 도메인 컨트롤러로의 연결을 허용해야 합니다.  

- **Admin$** 공유가 사이트 시스템 서버에 필요합니다.  

    Configuration Manager 사이트 서버는 Admin$ 공유를 사용하여 사이트 시스템에 연결하고 사이트 시스템에서 서비스 작업을 수행합니다. 이 공유를 사용하지 않도록 설정하거나 제거하지 마세요.  

- Configuration Manager는 이름 확인 서비스를 사용하여 다른 컴퓨터에 연결합니다. 이러한 서비스는 다음과 같은 보안 공격으로부터 보호하기 어렵습니다.
    - 스푸핑
    - 변조
    - 거부
    - 정보 공개
    - 서비스 거부
    - 권한 상승

    이름 확인에 사용하는 DNS 버전의 보안 지침을 확인하고 따르세요.  

## <a name="BKMK_Privacy_Cliients"></a> 검색으로부터 개인 정보 보호

검색을 수행하면 네트워크 리소스의 레코드가 생성되어 Configuration Manager 데이터베이스에 저장됩니다. 검색 데이터 레코드에는 IP 주소, OS 버전, 컴퓨터 이름 등의 컴퓨터 정보가 포함되어 있습니다. 또한 조직이 Active Directory Domain Services에 저장하는 정보를 반환하도록 Active Directory 검색 방법을 구성할 수도 있습니다.  

Configuration Manager에서 기본적으로 사용하도록 설정하는 검색 방법은 하트비트 검색뿐입니다. 이 방법은 Configuration Manager 클라이언트 소프트웨어가 이미 설치된 컴퓨터만 검색합니다.  

검색 정보는 Microsoft로 직접 전송되지 않습니다. Configuration Manager 데이터베이스에 저장됩니다. Configuration Manager는 데이터를 삭제할 때까지 데이터베이스에 정보를 보관합니다. 이 프로세스는 사이트 유지 관리 작업 **오래된 검색 데이터 삭제**에 의해 90일마다 수행됩니다.  
