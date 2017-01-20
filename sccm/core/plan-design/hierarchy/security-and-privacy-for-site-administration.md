---
title: "사이트 관리 보안 및 개인 정보 | Microsoft 문서"
description: "System Center Configuration Manager에서 사이트 관리에 대한 보안 및 개인 정보를 최적화합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d58176e-abc0-4087-8583-ce70deb4dcf5
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 6ed317d45d90758832d4157985dd95d5e253c6fc
ms.openlocfilehash: aca2169c8f5f855e84ca924ca56f6b64bba80fd6


---
# <a name="security-and-privacy-for-site-administration-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 사이트 관리를 위한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager 사이트 및 계층 구조에 대한 보안 및 개인 정보가 포함되어 있습니다.

##  <a name="a-namebkmksecuritysitesa-security-best-practices-for-site-administration"></a><a name="BKMK_Security_Sites"></a> 사이트 관리에 대한 보안 모범 사례  
 다음 보안 모범 사례를 사용하여 System Center Configuration Manager 사이트 및 계층 구조를 보호할 수 있습니다.  

 **신뢰할 수 있는 원본에서만 설치 프로그램을 실행하고 설치 미디어와 사이트 서버 간 통신 채널을 보호합니다.**  

 원본 파일의 변조를 방지하도록 신뢰할 수 있는 원본에서 설치 프로그램을 실행해야 합니다. 네트워크에 파일을 저장하는 경우 네트워크 위치를 보호합니다.  

 네트워크 위치에서 설치 프로그램을 실행하는 경우 공격자가 네트워크를 통해 전송되는 파일을 변조할 수 없도록 설치 프로그램 파일의 원본위치와 사이트 서버 간에 IPsec 또는 SMB 서명을 사용합니다.  

 또한 설치 다운로더를 사용하여 설치에 필요한 파일을 다운로드하는 경우 이러한 파일이 저장되는 위치와 설치 프로그램을 실행할 때 이 위치의 통신 채널을 보호해야 합니다.  

 **System Center Configuration Manager를 위해 Active Directory 스키마를 확장하고 Active Directory Domain Services에 사이트를 게시합니다.**  

 System Center Configuration Manager를 실행하는 데 스키마 확장이 반드시 필요한 것은 아니지만, 스키마 확장을 사용하면 Configuration Manager 클라이언트와 사이트 서버가 신뢰할 수 있는 원본에서 정보를 검색할 수 있기 때문에 더욱 안전한 환경이 조성됩니다.  

 클라이언트가 트러스트되지 않은 도메인에 있는 경우 클라이언트 도메인에 다음과 같은 사이트 시스템 역할을 배포합니다.  

-   관리 지점  

-   배포 지점  

-   응용 프로그램 카탈로그 웹 사이트 지점  

> [!NOTE]  
>  Configuration Manager용 트러스트된 도메인에는 Kerberos 인증이 필요하므로, 클라이언트가 사이트 서버 포리스트에 양방향 포리스트 트러스트를 갖지 않는 다른 포리스트에 있는 경우 트러스트되지 않은 도메인에 있는 것으로 간주됩니다. 외부 트러스트는 이 용도로 충분하지 않습니다.  

 **IPsec을 사용하여 사이트 시스템 서버와 사이트 간 통신을 보호합니다.**  

 Configuration Manager는 사이트 서버와 SQL Server를 실행하는 컴퓨터 간의 통신을 보호하지만 사이트 시스템 역할과 SQL Server 간의 통신은 Configuration Manager에서 보호되지 않습니다. 사이트 간 통신에 일부 사이트 시스템(등록 지점 및 응용 프로그램 카탈로그 웹 서비스 지점)만 HTTPS를 사용하도록 구성할 수 있습니다.  

 추가 제어 수단을 통해 이러한 서버 간 채널을 보호하지 않을 경우 공격자가 사이트 시스템에 대한 다양한 스푸핑과 가로채기(man-in-the-middle) 공격을 사용할 수 있습니다. Ipsec을 사용할 수 없는 경우 SMB 서명을 사용합니다.  

> [!NOTE]  
>  사이트 서버와 패키지 원본 서버 간의 통신 채널을 보호하는 것이 특히 중요합니다. 이 통신은 SMB를 사용합니다. IPsec을 사용하여 이 통신을 보호할 수 없는 경우 클라이언트에서 파일을 다운로드하여 실행하기 전에 파일이 변조되지 않도록 SMB 서명을 사용하세요.  

 **Configuration Manager에서 사이트 시스템 통신을 위해 만들고 관리하는 보안 그룹을 변경하지 않습니다.**  

 보안 그룹:  

-   **SMS_SiteSystemToSiteServerConnection_MP_&lt;사이트 코드\>**  

-   **SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;사이트 코드\>**  

-   **SMS_SiteSystemToSiteServerConnection_Stat_&lt;사이트 코드\>**  

Configuration Manager에서는 이러한 보안 그룹을 자동으로 만들고 관리합니다. 여기에는 사이트 시스템 역할이 제거될 때 컴퓨터 계정을 제거하는 것이 포함됩니다.  

서비스 연속성과 최소 권한을 갖도록 하려면 이러한 그룹을 수동으로 편집하지 않아야 합니다.  

**클라이언트가 글로벌 카탈로그 서버에서 Configuration Manager 정보를 쿼리할 수 없는 경우 신뢰할 수 있는 루트 키 프로비전 프로세스를 관리합니다.**  

클라이언트가 글로벌 카탈로그에서 Configuration Manager 정보를 쿼리할 수 없는 경우 신뢰할 수 있는 루트 키를 사용하여 유효한 관리 지점을 인증해야 합니다. 신뢰할 수 있는 루트 키는 클라이언트 레지스트리에 저장되며 그룹 정책 또는 수동 구성을 사용하여 설정할 수 있습니다.  

클라이언트가 신뢰할 수 있는 루트 키 사본을 갖지 않은 상태에서 관리 지점에 처음으로 연결하는 경우 통신하는 첫 번째 관리 지점을 트러스트합니다. 공격자가 클라이언트를 무단 관리 지점으로 연결시키는 위험을 줄이기 위해 신뢰할 수 있는 루트 키로 클라이언트를 미리 프로비전할 수 있습니다. 자세한 내용은 [Planning for the Trusted Root Key](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK)을 참조하십시오.  

**기본 포트 번호 이외의 번호를 사용합니다.**  

기본 포트 번호 이외의 번호를 사용하면 공격자가 공격을 준비하기 위해 환경을 탐색하기가 더 어려워지므로 보안이 강화될 수 있습니다. 기본 포트 이외의 포트를 사용하려는 경우 Configuration Manager를 설치하기 전에 포트를 계획하고 계층 구조의 모든 사이트에서 일관되게 사용해야 합니다. 클라이언트 요청 포트와 Wake on LAN은 기본 포트 번호 이외의 번호를 사용할 수 있는 예입니다.  

**사이트 시스템에서 역할 구분을 사용합니다.**  

단일 컴퓨터에 모든 사이트 시스템 역할을 설치할 수는 있지만 단일 실패 지점이 생성되므로 프로덕션 네트워크에서는 이 방법이 좀처럼 사용되지 않습니다.  

**공격 프로필을 줄입니다.**  

각 사이트 시스템 역할을 서로 다른 서버에 분리하면 한 사이트 시스템의 취약성에 대한 공격이 다른 사이트 시스템에 대해 사용될 가능성이 줄어듭니다. 대다수 사이트 시스템 역할을 사용하려면 사이트 시스템에 IIS(인터넷 정보 서비스)를 설치해야 하며 이로 인해 공격을 받을 수 있는 취약점이 증가할 수 있습니다. 하드웨어 비용을 줄이기 위해 사이트 시스템 역할을 결합해야 할 경우 IIS 사이트 시스템 역할을 IIS가 필요한 다른 사이트 시스템 역할과만 결합하세요.  

> [!IMPORTANT]  
>  대체 상태 지점 역할은 예외입니다. 이 사이트 시스템 역할은 클라이언트에서 인증되지 않은 데이터를 수락하므로 대체 상태 지점 역할을 다른 Configuration Manager 사이트 시스템 역할에 절대 할당해서는 안 됩니다.  


**Windows Server에 대한 보안 모범 사례를 따르고 모든 사이트 서버에 대해 보안 구성 마법사를 실행합니다.**  

SCW(보안 구성 마법사)를 사용하여 네트워크상의 서버에 적용할 수 있는 보안 정책을 만들 수 있습니다. System Center Configuration Manager 템플릿을 설치하고 나면 SCW에서 Configuration Manager 사이트 시스템 역할, 서비스, 포트 및 응용 프로그램을 인식합니다. 그런 다음 Configuration Manager에 필요한 통신을 허용하고 필요 없는 통신을 차단합니다.  

보안 구성 마법사는 Microsoft 다운로드 센터에서 다운로드할 수 있는 System Center 2012 Configuration Manager용 도구 키트에 함께 포함되어 있습니다. 링크([System Center 2012 – Configuration Manager 구성 요소 추가 기능 및 확장](http://go.microsoft.com/fwlink/p/?LinkId=251931))를 포함하여 보안 구성 마법사에 대한 항목이 업데이트되었습니다.  

**사이트 시스템에 대한 고정 IP 주소를 구성합니다.**  

고정 IP 주소를 사용하면 이름 확인 공격으로부터 보호하기가 더 쉽습니다.  

또한 고정 IP 주소를 사용하면 Configuration Manager에서 사이트 시스템 간 통신을 보호하기 위한 보안 모범 사례인 IPsec 구성이 더 쉽습니다.  

**사이트 시스템 서버에 기타 응용 프로그램을 설치하지 않습니다.**  

사이트 시스템 서버에 기타 응용 프로그램을 설치하면 Configuration Manager의 공격을 받을 수 있는 취약점이 증가하고 비호환성 문제가 발생할 수 있습니다.  

**사이트 옵션으로 서명을 요구하고 암호화를 사용하도록 설정합니다.**  

사이트에 서명 및 암호화 옵션을 사용하도록 설정합니다. 모든 클라이언트가 SHA-256 해시 알고리즘을 지원할 수 있는지 확인한 다음 **SHA-256 필요**옵션을 사용하도록 설정합니다.  

**Configuration Manager 관리자를 제한하고 모니터링하며, 역할 기반 관리를 사용하여 이러한 사용자에게 필요한 최소 권한을 부여합니다.**  

신뢰할 수 있는 사용자에게만 Configuration Manager에 대한 관리 권한을 부여하고 기본 제공 보안 역할을 사용하거나 보안 역할을 사용자 지정하여 최소 권한만 부여합니다. 응용 프로그램, 작업 순서, 소프트웨어 업데이트, 구성 항목 및 구성 기준을 만들고 수정하고 배포할 수 있는 관리자는 잠재적으로 Configuration Manager 계층 구조의 장치를 제어할 수 있습니다.  

정기적으로 관리자 할당과 권한 수준을 감사하여 변경이 필요한지 확인합니다.  

역할 기반 관리를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 역할 기반 관리 구성](../../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.  

**Configuration Manager 백업을 보호하고 백업 및 복구 시 사용하는 통신 채널을 보호합니다.**  

Configuration Manager를 백업하는 경우 인증서와 공격자가 가장하는 데 사용할 수 있는 기타 중요한 데이터가 백업 정보에 포함됩니다.  

네트워크를 통해 이 데이터를 전송할 때에는 SMB 서명이나 IPsec를 사용하고 백업 위치를 보호합니다.  

**Configuration Manager 콘솔에서 네트워크 위치로 개체를 가져오거나 내보내는 경우 해당 위치와 네트워크 채널을 보호해야 합니다.**  

네트워크 폴더에 액세스할 수 있는 사용자를 제한합니다.  

공격자가 내보낸 데이터를 변조하지 못하도록 네트워크 위치와 사이트 서버 간에, 그리고 Configuration Manager 콘솔을 실행하는 컴퓨터와 사이트 서버 간에 SMB 서명 또는 IPsec를 사용합니다. IPsec를 사용해서 네트워크상의 데이터를 암호화하여 정보 유출을 방지합니다.  

**사이트 시스템이 인증서를 제거하지 못하거나 작동을 멈춘 후에 복원할 수 없는 경우 다른 Configuration Manager 서버에서 이 서버에 대한 Configuration Manager 인증서를 수동으로 제거합니다.**  

처음에 사이트 시스템과 사이트 시스템 역할을 사용하여 설정된 PeerTrust를 제거하려면 다른 사이트 시스템 서버의 **신뢰할 수 있는 사용자** 저장소에서 실패한 서버에 대한 Configuration Manager 인증서를 수동으로 제거합니다. 이는 서버를 다시 포맷하지 않고 다른 목적으로 재사용하는 경우에 특히 중요합니다.  

이러한 인증서에 대한 자세한 내용은 [System Center Configuration Manager에 대한 암호화 제어 기술 참조](../../../protect/deploy-use/cryptographic-controls-technical-reference.md)에서 서버 통신에 대한 암호화 제어 섹션을 참조하세요.  

**인터넷 기반 사이트 시스템이 경계 네트워크와 인트라넷을 서로 연결하도록 구성하지 않습니다.**  

사이트 시스템 서버가 경계 네트워크와 인트라넷에 연결되도록 멀티홈으로 사이트 시스템 서버를 구성해서는 안 됩니다. 이 구성을 사용하면 인터넷 기반 사이트 시스템이 인터넷과 인트라넷에서 클라이언트 연결을 수락할 수 있지만, 경계 네트워크과 인트라넷 사이의 보안 경계가 사라집니다.  

**사이트 시스템 서버가 신뢰할 수 없는 네트워크(예: 경계 네트워크)에 있는 경우 사이트 서버에서 사이트 시스템에 대한 연결을 시작하도록 구성합니다.**  

기본적으로 사이트 시스템은 데이터를 전송하기 위해 사이트 서버에 대한 연결을 시작하며, 신뢰할 수 없는 네트워크에서 신뢰할 수 있는 네트워크로 연결이 시작될 경우 보안 위험이 발생할 수 있습니다. 사이트 시스템이 인터넷에서 연결을 수락하거나 트러스트되지 않은 포리스트에 있는 경우 사이트 시스템 및 사이트 시스템 역할을 설치한 후에 모든 연결이 신뢰할 수 있는 네트워크에서 시작되도록 사이트 시스템 옵션 **이 사이트 시스템의 연결을 시작하려면 사이트 서버 필요** 를 구성합니다.  

**인터넷 기반 클라이언트 관리에 웹 프록시 서버를 사용하는 경우 인증과 함께 종단을 사용하여 SSL에서 SSL로의 브리징을 사용합니다.**  

 프록시 웹 서버에 SSL 종단을 구성하는 경우 인터넷 패킷이 내부 네트워크로 전달되기 전에 검사됩니다. 프록시 웹 서버는 클라이언트에서의 연결을 인증하고 종료한 다음 인터넷 기반 사이트 시스템에 대한 새로운 인증 연결을 개시합니다.  

 Configuration Manager 클라이언트 컴퓨터가 프록시 웹 서버를 사용하여 인터넷 기반 사이트 시스템에 연결하는 경우 클라이언트 ID(클라이언트 GUID)가 패킷 페이로드 내에 안전하게 포함되므로 관리 지점이 프록시 웹 서버를 클라이언트로 간주하지 않습니다. 프록시 웹 서버가 SSL 브리징 요구 사항을 지원하지 않는 경우 SSL 터널링도 지원됩니다. 이 옵션을 사용하면 인터넷의 SSL 패킷이 종단 없이 사이트 시스템에 전달되어 악성 콘텐츠 여부가 검사되지 않으므로 별로 안전하지 않습니다.  

 프록시 웹 서버가 SSL 브리징 요구 사항을 지원할 수 없는 경우 SSL 터널링을 사용할 수 있습니다. 그러나 이 옵션을 사용하면 인터넷의 SSL 패킷이 종단 없이 사이트 시스템에 전달되어 악성 콘텐츠 여부가 검사되지 않으므로 별로 안전하지 않습니다.  

> [!WARNING]  
>  Configuration Manager에서 등록된 모바일 장치는 SSL 브리징을 사용할 수 없으며 SSL 터널링만 사용해야 합니다.  

**사이트에서 소프트웨어를 설치하기 위해 컴퓨터의 절전 모드를 해제하도록 구성하는 경우 사용하는 구성**  

-   기존 절전 모드 해제 패킷을 사용하는 경우 서브넷 지향 브로드캐스트보다는 유니캐스트를 사용합니다.  

-   서브넷 지향 브로드캐스트를 사용해야 할 경우 라우터가 기본 포트 번호가 아닌 번호에서만 사이트 서버의 IP 지향 브로드캐스트에 한해 이를 허용하도록 구성합니다.  

다양한 Wake-on-LAN 기술에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트를 절전 모드에서 해제하는 방식 계획](../../../core/clients/deploy/plan/plan-wake-up-clients.md)을 참조하세요.

**전자 메일 알림을 사용하는 경우 SMTP 메일 서버에 대한 인증된 액세스를 구성합니다.**  

가능하면 인증된 액세스를 지원하는 메일 서버를 사용하고 인증에 사이트 서버의 컴퓨터 계정을 사용합니다. 인증을 위해 사용자 계정을 지정해야 할 경우 최소 권한을 갖는 계정을 사용합니다.  

##  <a name="a-namebkmksecuritysiteservera-security-best-practices-for-the-site-server"></a><a name="BKMK_Security_SiteServer"></a> 사이트 서버에 대한 보안 모범 사례  
 다음 보안 모범 사례를 사용하면 Configuration Manager 사이트 서버를 보호할 수 있습니다.  

 **Configuration Manager를 도메인 컨트롤러 대신 구성원 서버에 설치합니다.**  

 Configuration Manager 사이트 서버 및 사이트 시스템은 도메인 컨트롤러에 설치할 필요가 없습니다. 도메인 컨트롤러에는 도메인 데이터베이스 외에 로컬 SAM(Security Accounts Management) 데이터베이스가 없습니다. 구성원 서버에 Configuration Manager를 설치할 경우 도메인 데이터베이스가 아닌 로컬 SAM 데이터베이스에서 Configuration Manager 계정을 유지 관리할 수 있습니다.  

 이렇게 하면 도메인 컨트롤러에서 공격 노출 영역도 줄일 수 있습니다.  

 **파일을 네트워크를 통해 보조 사이트 서버에 복사하지 않고 보조 사이트를 설치합니다.**  

 설치 프로그램을 실행하고 보조 사이트를 만들 때 부모 사이트에서 보조 사이트로 파일을 복사하는 옵션을 선택하는 대신 네트워크 원본 위치를 사용합니다. 공격 시간을 선택하는 것이 어렵긴 하지만, 네트워크를 통해 파일이 복사될 때 노련한 공격자는 보조 사이트 설치 패키지를 가로챈 후 사용자가 설치하기 전에 파일을 무단 변경할 수도 있습니다. 파일을 전송할 때 IPsec 또는 SMB를 사용하면 이러한 공격을 최소화할 수 있습니다.  

 네트워크를 통해 파일을 복사하는 대신 보조 사이트 서버에서 원본 파일을 미디어에서 로컬 폴더로 복사합니다. 그런 다음 설치 프로그램을 실행하여 보조 사이트를 만들 때 **설치 원본 파일** 페이지에서 **보조 사이트 컴퓨터에서 다음 위치의 원본 파일 사용(가장 안전)**을 선택하고 이 폴더를 지정합니다.  

 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) 항목에서 [보조 사이트 설치](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_secondary)를 참조하세요.  

##  <a name="a-namebkmksecuritysqlservera-security-best-practices-for-sql-server"></a><a name="BKMK_Security_SQLServer"></a> SQL Server에 대한 보안 모범 사례  
 Configuration Manager에서는 SQL Server를 백 엔드 데이터베이스로 사용합니다. 데이터베이스 보안이 손상되면 공격자는 Configuration Manager를 무시하고 SQL Server에 직접 액세스하여 Configuration Manager를 통해 공격을 시작할 수 있습니다. SQL Server에 대한 공격은 매우 큰 위험을 유발할 수 있으므로 적절한 방법으로 최소화해야 합니다.  

 다음 보안 모범 사례를 사용하면 Configuration Manager에 대해 SQL Server를 보호할 수 있습니다.  

 **Configuration Manager 사이트 데이터베이스 서버를 사용하여 다른 SQL Server 응용 프로그램을 실행하지 않습니다.**  

 Configuration Manager 사이트 데이터베이스 서버에 대한 액세스를 늘리면 Configuration Manager 데이터의 위험도 늘어납니다. Configuration Manager 사이트 데이터베이스 보안이 손상되면 같은 SQL Server 컴퓨터에 있는 다른 응용 프로그램도 위험해집니다.  

 **Windows 인증을 사용하도록 SQL Server를 구성합니다.**  

 Configuration Manager는 Windows 계정 및 Windows 인증을 사용하여 사이트 데이터베이스에 액세스하지만 SQL Server에서 SQL Server 혼합 모드를 사용하도록 구성할 수도 있습니다. SQL Server 혼합 모드를 사용하면 추가 SQL 로그인이 데이터베이스에 액세스할 수 있지만, 이 방식은 필수가 아니며 공격 노출 영역도 증가시킵니다.  

 **추가 단계에 따라 SQL Server Express를 사용하는 보조 사이트에 최신 소프트웨어 업데이트가 설치되어 있는지 확인하세요.**  

 기본 사이트를 설치할 때 Configuration Manager는 SQL Server Express를 Microsoft 다운로드 센터에서 다운로드하고 해당 파일을 기본 사이트 서버에 복사합니다. 보조 사이트를 설치하면서 SQL Server Express 설치 옵션을 선택하면 Configuration Manager에서는 이전에 다운로드한 버전을 설치하고 새 버전의 제공 여부를 확인하지 않습니다. 보조 사이트에 최신 버전이 설치되었는지 확인하려면 다음 중 하나를 수행하세요.  

-   보조 사이트를 설치한 후에 보조 사이트 서버에서 Windows Update를 실행합니다.  

-   보조 사이트를 설치하기 전에 보조 사이트 서버를 실행할 컴퓨터에 SQL Server Express를 수동으로 설치하고 최신 버전 및 기타 소프트웨어 업데이트가 설치되었는지 확인합니다. 그런 다음 보조 사이트를 설치하고 기존 SQL Server 인스턴스를 사용하는 옵션을 선택합니다.  

이 사이트와 설치된 모든 SQL Server 버전에 대해 Windows Update를 주기적으로 실행하여 최신 소프트웨어 업데이트가 설치되도록 합니다.  

**SQL Server에 대한 모범 사례 준수**  

사용 중인 SQL Server 버전에 대한 모범 사례를 확인 및 준수합니다. 그러나 Configuration Manager에 대한 다음 요구 사항도 고려해야 합니다.  

-   사이트 서버의 컴퓨터 계정은 SQL Server를 실행하는 컴퓨터에서 관리자 그룹의 구성원이어야 합니다. SQL Server에서 "관리 계정을 명시적으로 프로비전"하는 권장 사항을 따를 경우 사이트 서버에서 설치 프로그램을 실행하는 데 사용할 계정은 SQL 사용자 그룹의 구성원이어야 합니다.  

-   도메인 사용자 계정을 사용하여 SQL Server를 설치하는 경우 사이트 서버 컴퓨터 계정이 Active Directory Domain Services에 게시되는 SPN(서비스 사용자 이름)을 사용하도록 구성되었는지 확인하세요. SPN이 없으면 Kerberos 인증 및 Configuration Manager 설치 프로그램 작업이 실패합니다.  

##  <a name="a-namebkmksecurityiisa-security-best-practices-for-site-systems-that-run-iis"></a><a name="BKMK_Security_IIS"></a> IIS를 실행하는 사이트 시스템에 대한 보안 모범 사례  
Configuration Manager의 여러 사이트 시스템 역할에는 IIS가 필요합니다. IIS의 보안을 유지하면 Configuration Manager가 올바르게 작동할 수 있고 보안 공격의 위험도 감소합니다. 적절한 수준에서 IIS가 필요한 서버의 수를 최소화하는 것이 좋습니다. 예를 들어 인터넷 기반 클라이언트 관리를 위한 고가용성 및 네트워크 격리를 고려하여 클라이언트 기반을 지원하는 데 필요한 수만큼만 관리 지점을 실행하세요.  

 다음 보안 모범 사례를 사용하면 IIS를 실행하는 사이트 시스템을 보호할 수 있습니다.  

 **필요하지 않은 IIS 기능을 사용하지 않도록 설정합니다.**  

 설치할 사이트 시스템 역할에 대해 최소 IIS 기능만 설치합니다. 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)을 참조하세요.  

 **HTTPS가 필요하도록 사이트 시스템 역할을 구성합니다.**  

 클라이언트는 HTTPS가 아닌 HTTP를 사용하여 사이트 시스템에 연결할 때 Windows 인증을 사용하며 이 방식은 Kerberos 인증이 아닌 NTLM 인증으로 대체될 수 있습니다. NTLM 인증이 사용되면 클라이언트는 허위 서버에 연결할 수도 있습니다.  

 이러한 보안 모범 사례의 예외로는 배포 지점을 들 수 있습니다. 패키지 액세스 계정은 배포 지점이 HTTPS를 사용하도록 구성된 경우 작동하지 않기 때문입니다. 패키지 액세스 계정은 콘텐츠에 대한 권한 부여를 제공하므로 이를 통해 해당 콘텐츠에 액세스할 수 있는 사용자를 제한할 수 있습니다. 자세한 내용은 [콘텐츠 관리에 대한 보안 모범 사례](../../../core/plan-design/hierarchy/security-and-privacy-for-content-management.md#BKMK_Security_ContentManagement)를 참조하세요.  

**IIS에서 사이트 시스템 역할에 대해 CTL(Certificate Trust List)을 구성합니다.**  

사이트 시스템 역할:  

-   HTTPS에 대해 구성되는 배포 지점입니다.  

-   HTTPS에 대해 구성되고 모바일 장치를 지원하도록 설정되는 관리입니다.  

CTL은 신뢰할 수 있는 루트 인증 기관의 정의된 목록입니다. CTL을 그룹 정책 및 PKI 배포와 함께 사용할 경우 네트워크에 구성된 기존의 신뢰할 수 있는 루트 인증 기관을 보완할 수 있습니다. 이러한 인증 기관의 예로는 Microsoft Windows와 함께 자동으로 설치되거나 Windows 엔터프라이즈 루트 인증 기관을 통해 추가된 인증 기관이 있습니다. 이 경우 IIS에서 CTL이 구성되면 CTL을 통해 그러한 신뢰할 수 있는 루트 인증 기관의 하위 집합이 정의됩니다.  

CTL은 허용되는 클라이언트 인증서를 CTL의 인증 기관 목록에 속한 곳에서 발급된 인증서만으로 제한하므로 이 하위 집합을 통해 보안을 더욱 효과적으로 제어할 수 있습니다. 예를 들어 Windows는 VeriSign 및 Thawte 등과 같은 잘 알려진 여러 타사 인증 기관의 인증서와 함께 제공됩니다. 기본적으로 IIS를 실행하는 컴퓨터는 이러한 유명 인증 기관에 연결되는 인증서를 신뢰합니다. IIS에서 나열된 사이트 시스템 역할에 대해 CTL을 구성하지 않은 경우 이러한 인증 기관에서 발급한 클라이언트 인증서가 포함된 모든 장치는 유효한 Configuration Manager 클라이언트로 승인됩니다. IIS에서 이러한 인증 기관이 포함되지 않은 CTL을 구성하면 인증서가 해당 인증 기관에 연결된 경우 클라이언트 연결은 거부됩니다. 따라서 나열된 사이트 시스템 역할에 대해 Configuration Manager 클라이언트를 승인하려면 IIS에서 Configuration Manager 클라이언트에 사용되는 인증 기관을 지정하는 CTL을 구성해야 합니다.  

> [!NOTE]  
>  IIS에서는 나열된 사이트 시스템 역할에 대해서만 CTL을 구성하면 됩니다. Configuration Manager에서 관리 지점에 대해 사용하는 인증서 발급자 목록은 HTTPS 관리 지점에 연결하는 클라이언트 컴퓨터에 대해 동일한 기능을 제공합니다.  

IIS에서 신뢰할 수 있는 인증 기관의 목록을 구성하는 자세한 방법은 IIS 설명서를 참조하세요.  

**사이트 서버는 IIS를 실행하는 컴퓨터에 설치하지 마십시오.**  

역할 분리는 공격 프로필을 축소시키고 복구 능력을 높이는 데 도움이 됩니다. 또한 사이트 서버의 컴퓨터 계정에는 일반적으로 모든 사이트 시스템 역할(클라이언트 강제 설치를 사용하는 경우 Configuration Manager 클라이언트 포함)에 대한 관리 권한이 있습니다.  

**Configuration Manager에 대해 전용 IIS 서버를 사용합니다.**  

Configuration Manager에서도 사용되는 IIS 서버에 여러 웹 기반 응용 프로그램을 호스트할 수 있지만 이렇게 하면 공격 노출 영역이 크게 늘어날 수 있습니다. 불완전하게 구성된 응용 프로그램으로 인해 공격자가 Configuration Manager 사이트 시스템의 제어 권한을 얻을 수 있고 이 경우 공격자는 계층 구조의 제어 권한까지 얻을 수도 있습니다.  

Configuration Manager 사이트 시스템에서 다른 웹 기반 응용 프로그램을 실행해야 할 경우 Configuration Manager 사이트 시스템에 대한 사용자 지정 웹 사이트를 만드세요.  

**사용자 지정 웹 사이트를 사용합니다.**  

IIS를 실행하는 사이트 시스템의 경우 Configuration Manager에서 IIS용 기본 웹 사이트 대신 사용자 지정 웹 사이트를 사용하도록 구성할 수 있습니다. 사이트 시스템에서 다른 웹 응용 프로그램을 실행하려면 사용자 지정 웹 사이트를 사용해야 합니다. 이 설정은 특정 사이트 시스템에 대한 설정이 아닌 사이트 전체 설정입니다.  

사이트 시스템에서 다른 웹 응용 프로그램을 실행하는 경우 추가 보안을 제공하는 한편 사용자 지정 웹 사이트도 사용해야 합니다.  

**배포 지점 역할이 설치된 후 기본 웹 사이트에서 사용자 지정 웹 사이트로 전환할 경우 기본 가상 디렉터리를 제거하세요.**  

기본 웹 사이트를 사용하지 않고 사용자 지정 웹 사이트를 사용하더라도 Configuration Manager에서 이전 가상 디렉터리를 제거하지는 않습니다. Configuration Manager에서 원래 기본 웹 사이트 아래에 만들었던 가상 디렉터리를 제거하세요.  

예를 들어 배포 지점에 대해 제거할 가상 디렉터리는 다음과 같습니다.  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**IIS 서버에 대한 모범 사례 준수**  

사용 중인 IIS 서버 버전에 대한 모범 사례를 확인 및 준수합니다. 그러나 Configuration Manager에서 특정 사이트 시스템 역할과 관련된 기타 요구 사항도 고려해야 합니다. 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)을 참조하세요.  

##  <a name="a-namebkmksecuritymanagementpointa-security-best-practices-for-the-management-point"></a><a name="BKMK_Security_ManagementPoint"></a> 관리 지점에 대한 보안 모범 사례  
 관리 지점은 장치와 Configuration Manager 간의 기본 인터페이스입니다. 관리 지점 및 관리 지점이 실행되는 서버에 대한 공격은 매우 큰 위험을 유발할 수 있으므로 적절한 방법으로 최소화해야 합니다. 적절한 보안 모범 사례를 모두 적용하고 비정상적인 활동을 모니터링하세요.  

 다음 보안 모범 사례를 사용하면 Configuration Manager에서 관리 지점을 보호할 수 있습니다.  

**관리 지점에 Configuration Manager 클라이언트를 설치할 경우 이 클라이언트를 해당 관리 지점의 사이트에 할당합니다.**  

 관리 지점 사이트 시스템에 있는 Configuration Manager 클라이언트가 해당 관리 지점의 사이트가 아닌 다른 사이트에 할당되지 않도록 합니다.  

 이전 버전에서 System Center Configuration Manager로 마이그레이션하는 경우 관리 지점의 클라이언트 소프트웨어를 최대한 빨리 System Center Configuration Manager로 마이그레이션합니다.  

##  <a name="a-namebkmksecurityfspa-security-best-practices-for-the-fallback-status-point"></a><a name="BKMK_Security_FSP"></a> 대체 상태 지점에 대한 보안 모범 사례  
 Configuration Manager에 대체 상태 지점을 설치하는 경우 다음 보안 모범 사례를 따르세요.  

 대체 상태 지점 설치와 관련된 보안 고려 사항에 대한 자세한 내용은 [대체 상태 지점 필요 여부 결정](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md#BKMK_Determine_FSP)을 참조하세요.  

**사이트 시스템에서 다른 사이트 시스템 역할을 실행하지 않고 대체 상태 지점을 도메인 컨트롤러에 설치하지 않습니다.**  

 대체 상태 지점은 모든 컴퓨터의 인증되지 않은 통신을 허용하도록 설계되었기 때문에 이 사이트 시스템 역할을 다른 사이트 시스템 역할과 함께 실행하거나 도메인 컨트롤러에서 실행하면 해당 서버에 대한 위험은 크게 증가합니다.  

**Configuration Manager에서 클라이언트 통신에 대해 PKI 인증서를 사용할 때 클라이언트를 설치하기 전에 대체 상태 지점을 설치합니다.**  

 Configuration Manager 사이트 시스템에서 HTTP 클라이언트 통신을 허용하지 않는 경우 PKI 관련 인증서 문제로 인해 클라이언트가 관리되지 않는다는 사실을 모를 수도 있습니다. 그러나 클라이언트가 대체 상태 지점에 할당된 경우 이러한 인증서 문제는 대체 상태 지점에 의해 보고됩니다.  

 보안상의 이유로, 대체 상태 지점은 설치가 완료된 클라이언트에 할당할 수 없으며 클라이언트 설치 도중에만 할당할 수 있습니다.  

**경계 네트워크에서 대체 상태 지점을 사용하지 마십시오.**  

 대체 상태 지점은 모든 클라이언트의 데이터를 수락하며, 이는 의도된 동작입니다. 경계 네트워크의 대체 상태 지점은 인터넷 기반 클라이언트의 문제를 해결하는 데 도움이 될 수는 있지만, 공개적으로 액세스할 수 있는 네트워크의 인증되지 않은 데이터를 수용하는 경우 사이트 시스템에 발생할 수 있는 위험과 문제 해결의 이점 간의 경중을 따져서 사용 여부를 결정해야 합니다.  

 경계 네트워크나 신뢰할 수 없는 네트워크에 대체 상태 지점을 설치하는 경우 대체 상태 지점이 사이트 서버 연결을 시작하는 기본 설정이 아닌 사이트 서버가 데이터 전송을 시작하도록 구성해야 합니다.  

##  <a name="a-namebkmksecurityissuesclientsa-security-issues-for-site-administration"></a><a name="BKMK_SecurityIssues_Clients"></a> 사이트 관리에 대한 보안 문제  
 Configuration Manager에 대한 다음과 같은 보안 문제를 검토합니다.  

-   Configuration Manager에는 권한 있는 관리자가 Configuration Manager를 사용하여 네트워크를 공격하는 경우 방어할 수 있는 수단이 없습니다. 권한이 없는 관리자는 다음을 포함하여 강도 높은 보안 위험을 유발하거나 다양한 공격을 시작할 수 있습니다.  

    -   소프트웨어 배포를 사용하여 기업 내의 모든 Configuration Manager 클라이언트 컴퓨터에 악성 소프트웨어를 자동으로 설치 및 실행할 수 있습니다.  

    -   원격 제어를 통해 클라이언트 승인 없이 Configuration Manager 클라이언트를 원격 제어할 수 있습니다.  

    -   폴링 간격을 매우 짧게 구성하고 극도로 큰 인벤토리를 구성하여 클라이언트 및 서버에 대해 서비스 거부 공격을 유발할 수 있습니다.  

    -   계층 내의 한 사이트를 사용하여 다른 사이트의 Active Directory 데이터에 데이터를 쓸 수 있습니다.  

    사이트 계층은 보안 경계가 됩니다. 따라서 사이트를 관리 경계로만 설정하는 것이 좋습니다.  

    모든 관리자 작업을 감사하고 감사 로그를 정기적으로 검토해야 합니다. 모든 Configuration Manager 관리자는 고용하기 전에 반드시 배경을 조사해야 하고 고용 조건으로 주기적 재조사를 수행해야 합니다.  

-   등록 지점이 손상되면 공격자는 인증서를 가져와 인증에 사용하고 모바일 장치를 등록한 사용자의 자격 증명을 도용할 수 있습니다.  

    등록 지점은 인증 기관과 통신하여 Active Directory 개체를 만들고 수정하고 삭제할 수 있습니다. 경계 네트워크에는 등록 지점을 절대 설치하면 안 되며 비정상적인 활동을 모니터링해야 합니다.  

-   사용자가 인터넷 기반 클라이언트 관리를 위해 정책을 사용할 수 있도록 허용하는 경우 또는 사용자가 인터넷에 연결된 상태에서 응용 프로그램 카탈로그 웹 사이트 지점을 구성할 수 있도록 허용하는 경우 공격 프로필이 높아집니다.  

    클라이언트 및 서버 간 연결에 PKI 인증서를 사용하는 경우와 함께 이러한 구성을 사용하려면 Windows 인증을 사용해야 합니다. 그러면 Kerberos 대신 NTLM 인증을 사용하도록 대체됩니다. NTLM 인증은 가장 및 재생 공격에 취약합니다. 인터넷에서 사용자를 성공적으로 인증하려면 인터넷 기반 사이트 시스템 서버에서 도메인 컨트롤러로의 연결을 허용해야 합니다.  

-   Admin$ 공유가 사이트 시스템 서버에 필요합니다.  

    Configuration Manager 사이트 서버는 Admin$ 공유를 사용하여 사이트 시스템의 서비스 작업을 연결 및 수행합니다. Admin$ 공유를 사용하지 않도록 설정하거나 제거하세요.  

-   Configuration Manager는 이름 확인 서비스를 사용하여 다른 컴퓨터에 연결하며 이러한 서비스는 스푸핑, 변조, 거부, 정보 노출, 서비스 거부, 권한 상승 등의 보안 공격으로부터 보호하기가 쉽지 않습니다.  

    이름 확인에 사용하는 DNS 및 WINS의 버전에 맞게 보안 모범 사례를 파악하여 따르십시오.  

##  <a name="a-namebkmkprivacycliientsa-privacy-information-for-discovery"></a><a name="BKMK_Privacy_Cliients"></a> 검색으로부터 개인 정보 보호  
 검색을 수행하면 네트워크 리소스에 대해 레코드가 생성되어 System Center Configuration Manager 데이터베이스에 저장됩니다. 검색 데이터 레코드에는 IP 주소, 운영 체제, 컴퓨터 이름 등의 컴퓨터 정보가 포함됩니다. 또한 Active Directory Domain Services에 저장된 정보를 검색하도록 Active Directory 검색 방법을 구성할 수도 있습니다.  

 기본적으로 사용하도록 설정되는 검색 방법은 하트비트 검색뿐이지만 하트비트 방법은 System Center Configuration Manager 클라이언트 소프트웨어가 이미 설치된 컴퓨터만 검색합니다.  

 검색 정보는 Microsoft로 전송되지 않습니다. 검색 정보는 Configuration Manager 데이터베이스에 저장됩니다. 정보는 90일마다 반복되는 사이트 유지 관리 작업인 **오래된 검색 데이터 삭제** 에 의해 삭제될 때까지 데이터베이스에 유지됩니다. 삭제 간격은 필요에 따라 구성할 수 있습니다.  

 추가 검색 방법을 구성하거나 Active Directory 검색을 확장하기 전에 개인 정보 보호 요구 사항을 고려해야 합니다.  



<!--HONumber=Dec16_HO3-->


