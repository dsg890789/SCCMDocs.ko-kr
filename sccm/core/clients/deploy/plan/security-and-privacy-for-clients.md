---
title: 클라이언트 보안 및 개인 정보
titleSuffix: Configuration Manager
description: Configuration Manager 클라이언트의 보안 및 개인 정보에 대해 알아봅니다.
ms.date: 07/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: c1d71899-308f-49d5-adfa-3a3ec0163ed8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5c32f1ea08fbeee900dfd30eef0f7ce446c7546f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824846"
---
# <a name="security-and-privacy-for-configuration-manager-clients"></a>Configuration Manager 클라이언트에 대한 보안 및 개인 정보

*적용 대상: Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager 클라이언트의 보안 및 개인 정보에 대해 설명합니다. 또한 [Exchange Server 커넥터](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)에서 관리하는 모바일 디바이스에 대한 정보도 포함됩니다.  


## <a name="BKMK_Security_Clients"></a> 클라이언트에 대한 보안 모범 사례  

Configuration Manager 사이트에서 Configuration Manager 클라이언트를 실행하는 디바이스의 데이터를 허용합니다. 이 동작에는 클라이언트에서 사이트를 공격할 수 있는 위험이 있습니다. 예를 들어 이러한 클라이언트는 잘못된 형식의 인벤토리를 보내거나 사이트 시스템의 오버로드를 시도할 수 있습니다. Configuration Manager 클라이언트는 신뢰할 수 있는 디바이스에만 배포하세요. 또한 다음 보안 모범 사례를 활용하면 허위 디바이스 또는 손상된 디바이스로부터 사이트를 보호하는 데 도움이 됩니다.  

### <a name="use-public-key-infrastructure-pki-certificates-for-client-communications-with-site-systems-that-run-iis"></a>IIS를 실행하는 사이트 시스템과의 클라이언트 통신에 PKI(공개 키 인프라) 인증서 사용  

- 사이트 속성으로 **사이트 시스템 설정** 을 **HTTPS만 사용**으로 구성합니다.  

- `UsePKICert` CCMSetup 속성을 사용하여 클라이언트를 설치합니다.  

- CRL(인증서 해지 목록)을 사용하고 클라이언트 및 통신 서버에서 항상 액세스할 수 있도록 합니다.  

모바일 디바이스 클라이언트 및 일부 인터넷 기반 클라이언트에는 이러한 인증서가 필요합니다. 인트라넷의 모든 클라이언트 연결에 이러한 인증서를 사용하는 것이 좋습니다.  

PKI 인증서 요구 사항 및 Configuration Manager를 보호하는 데 사용되는 방법에 대한 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

### <a name="automatically-approve-client-computers-from-trusted-domains-and-manually-check-and-approve-other-computers"></a>트러스트된 도메인의 클라이언트 컴퓨터 자동으로 승인, 다른 컴퓨터 수동으로 확인 및 승인  

PKI 인증을 사용할 수 없는 경우 승인에서는 Configuration Manager에서 관리하는 것으로 신뢰하는 컴퓨터를 식별합니다. 계층 구조에는 클라이언트 승인을 구성하는 다음과 같은 옵션이 있습니다.  

- 수동
- 신뢰할 수 있는 도메인의 컴퓨터에 대한 자동 승인
- 모든 컴퓨터에 대한 자동 승인  

가장 안전한 승인 방법은 트러스트된 도메인의 구성원인 클라이언트를 자동으로 승인하는 것입니다. 그런 다음, 다른 모든 컴퓨터를 수동으로 확인하고 승인합니다. 신뢰할 수 없는 컴퓨터에서 네트워크에 액세스하지 못하도록 방지하는 다른 액세스 제어 방법이 없는 경우 모든 클라이언트를 자동으로 승인하는 방식은 사용하지 않는 것이 좋습니다.  

컴퓨터를 수동으로 승인하는 방법에 대한 자세한 내용은 [디바이스 노드에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode)를 참조하세요.  

### <a name="dont-rely-on-blocking-to-prevent-clients-from-accessing-the-configuration-manager-hierarchy"></a>클라이언트에서 Configuration Manager 계층 구조에 액세스하지 못하도록 방지하는 데 차단을 사용하지 않음  

차단된 클라이언트는 Configuration Manager 인프라에서 거부됩니다. 클라이언트가 차단되면 사이트 시스템과 통신하여 정책을 다운로드하거나, 인벤토리 데이터를 업로드하거나, 상태 또는 상태 메시지를 보낼 수 없습니다.

차단은 다음 시나리오를 위해 설계되었습니다.

- OS를 클라이언트에 배포할 때 손실되거나 손상된 부팅 미디어를 차단하는 경우
- 모든 사이트 시스템에서 HTTPS 클라이언트 연결을 허용하는 경우

사이트 시스템에서 HTTP 클라이언트 연결을 허용하면 신뢰할 수 없는 컴퓨터로부터 Configuration Manager 계층 구조를 보호하기 위해 차단을 사용하지 마세요. 이 시나리오에서 차단된 클라이언트는 새 자체 서명된 인증서 및 하드웨어 ID를 사용하여 사이트에 다시 조인할 수 있습니다.

인증서 해지는 잠재적으로 손상된 인증서에 대한 기본 방어선입니다. CRL(인증서 해지 목록)은 지원되는 PKI(공개 키 인프라)에서만 사용할 수 있습니다. Configuration Manager에서 클라이언트를 차단하면 계층 구조를 보호하기 위한 이차 방어 수단이 됩니다.  

자세한 내용은 [클라이언트를 차단할지 여부 결정](/sccm/core/clients/deploy/plan/determine-whether-to-block-clients)을 참조하세요.  

### <a name="use-the-most-secure-client-installation-methods-that-are-practical-for-your-environment"></a>사용자 환경에 적합한 가장 안전한 클라이언트 설치 방법 사용  

- 도메인 컴퓨터의 경우 그룹 정책 클라이언트 설치 및 소프트웨어 업데이트 기반 클라이언트 설치 방법은 클라이언트 강제 설치보다 더 안전합니다.  

- 액세스 제어 및 변경 제어를 적용하는 경우 이미징 및 수동 설치 방법을 사용합니다.  

- 1806 버전 이상에서는 클라이언트 강제 설치와 함께 Kerberos 상호 인증을 사용합니다.  

모든 클라이언트 설치 방법 중 클라이언트 강제 설치는 자체의 많은 종속성으로 인해 보안이 가장 취약합니다. 이러한 종속성에는 로컬 관리 권한, Admin$ 공유 및 방화벽 예외가 포함됩니다. 이러한 종속성의 수와 유형은 공격 노출 영역을 증가시킵니다.  

1806 버전부터 클라이언트 강제를 사용하는 경우 사이트에서 NTLM으로의 대체를 허용하지 않아 연결을 설정하기 전에 Kerberos 상호 인증을 요구할 수 있습니다. 이 개선 사항은 서버와 클라이언트 간의 통신을 보안하는 데 도움이 됩니다. 자세한 내용은 [클라이언트 푸시를 사용하여 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)을 참조하세요.<!--1358204-->  

다른 클라이언트 설치 방법에 대한 자세한 내용은 [클라이언트 설치 방법](/sccm/core/clients/deploy/plan/client-installation-methods)을 참조하세요.  

가능한 경우 Configuration Manager에서 최소 보안 권한이 필요한 클라이언트 설치 방법을 선택합니다. 보안 역할이 할당된 관리 사용자를 클라이언트 배포 이외의 용도로 사용할 수 있는 권한으로 제한합니다. 예를 들어 자동 클라이언트 업그레이드를 구성하려면 관리 관리자에게 모든 보안 권한을 부여하는 **전체 관리자** 보안 역할이 필요합니다.  

각 클라이언트 설치 방법에 필요한 종속성 및 보안 권한에 대한 자세한 내용은 [컴퓨터 클라이언트에 대한 필수 조건](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#BKMK_prereqs_computers)의 "설치 방법 종속성"을 참조하세요.  

### <a name="if-you-must-use-client-push-installation-take-additional-steps-to-secure-the-client-push-installation-account"></a>클라이언트 강제 설치 사용 시 클라이언트 강제 설치 계정을 보호하기 위한 추가 단계 수행  

이 계정은 Configuration Manager 클라이언트를 설치하는 각 컴퓨터의 로컬 **관리자** 그룹의 구성원이어야 합니다. 클라이언트 강제 설치 계정은 **도메인 관리자** 그룹에 추가하면 안됩니다. 대신 글로벌 그룹을 만든 다음, 해당 글로벌 그룹을 클라이언트의 로컬 **관리자** 그룹에 추가합니다. 클라이언트 강제 설치 계정을 로컬 **관리자** 그룹에 추가하기 위해 [제한된 그룹] 설정을 추가하는 그룹 정책 개체를 만듭니다.  

추가 보안을 위해 각각 제한된 수의 컴퓨터에 대한 관리 액세스 권한이 있는 여러 개의 클라이언트 강제 설치 계정을 만듭니다. 이 경우 하나의 계정이 손상되면 해당 계정에 액세스할 수 있는 클라이언트 컴퓨터만 손상됩니다.  

### <a name="remove-certificates-before-imaging-clients"></a>클라이언트 이미지를 만들기 전에 인증서 제거  

OS 이미지를 사용하여 클라이언트를 배포하는 경우 항상 이미지를 캡처하기 전에 인증서를 제거합니다. 이러한 인증서에는 클라이언트 인증용 PKI 인증서와 자체 서명된 인증서가 포함됩니다. 이러한 인증서를 제거하지 않으면 클라이언트에서 서로를 가장할 수 있습니다. 그러면 각 클라이언트에 대한 데이터를 확인할 수 없습니다.  

자세한 내용은 [운영 체제를 캡처하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system)를 참조하세요.  

### <a name="ensure-that-the-configuration-manager-computer-clients-get-an-authorized-copy-of-these-certificates"></a>Configuration Manager 컴퓨터 클라이언트에서 권한 있는 인증서 복사본을 가져오는지 확인  

#### <a name="the-configuration-manager-trusted-root-key-certificate"></a>Configuration Manager의 신뢰할 수 있는 루트 키 인증서  

다음 두 항목 모두에 해당하면 클라이언트에서 Configuration Manager 신뢰할 수 있는 루트 키를 사용하여 유효한 관리 지점을 인증합니다.  

- Configuration Manager에 대한 Directory 스키마를 확장하지 않았습니다.
- 클라이언트에서 관리 지점과 통신할 때 PKI 인증서를 사용하지 않습니다.  

이 시나리오의 경우 클라이언트에서 신뢰할 수 있는 루트 키를 사용하지 않으면 계층 구조에서 신뢰할 수 있는 관리 지점인지 확인할 방법이 없습니다. 신뢰할 수 있는 루트 키가 없으면 노련한 공격자가 클라이언트를 허위 관리 지점으로 유도할 수 있습니다.  

클라이언트에서 글로벌 카탈로그 또는 PKI 인증서를 사용하여 Configuration Manager 신뢰할 수 있는 루트 키를 다운로드할 수 없는 경우 신뢰할 수 있는 루트 키를 클라이언트에 사전 프로비전합니다. 이 작업을 수행하면 Rogue 관리 지점으로 이동할 수 없습니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForRTK)을 참조하세요.  

#### <a name="the-site-server-signing-certificate"></a>사이트 서버 서명 인증서  

클라이언트에서 이 인증서를 사용하여 사이트 서버가 관리 지점에서 다운로드한 정책에 서명했는지 확인합니다. 이 인증서는 사이트 서버에서 자체 서명되었으며 Active Directory Domain Services에 게시됩니다.  

클라이언트는 글로벌 카탈로그에서 사이트 서버 서명 인증서를 다운로드할 수 없으면 기본적으로 관리 지점에서 다운로드합니다. 관리 지점이 인터넷과 같은 신뢰할 수 없는 네트워크에 노출되면 사이트 서버 서명 인증서를 클라이언트에 수동으로 설치합니다. 이 작업을 수행하면 손상된 관리 지점에서 변조된 클라이언트 정책을 다운로드할 수 없습니다.  

수동으로 사이트 서버 서명 인증서를 설치하려면 CCMSetup client.msi 속성 **SMSSIGNCERT**를 사용합니다. 자세한 내용은 [클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

### <a name="dont-use-automatic-site-assignment-if-the-client-downloads-the-trusted-root-key-from-the-first-management-point-it-contacts"></a>클라이언트가 연결한 첫 번째 관리 지점에서 신뢰할 수 있는 루트 키를 다운로드하는 경우 자동 사이트 할당 사용 안 함  

새 클라이언트가 Rogue 관리 지점에서 신뢰할 수 있는 루트 키를 다운로드하지 못하도록 방지하려면 다음 시나리오에서 자동 사이트 할당만 사용합니다.  

- 클라이언트에서 Active Directory Domain Services에 게시된 Configuration Manager 사이트 정보에 액세스할 수 있습니다.  

- 클라이언트에 신뢰할 수 있는 루트 키를 사전 프로비전합니다.  

- 엔터프라이즈 인증 기관의 PKI 인증서를 사용하여 클라이언트 및 관리 지점 간의 트러스트를 설정합니다.  

신뢰할 수 있는 루트 키에 대한 자세한 내용은 [신뢰할 수 있는 루트 키 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForRTK)을 참조하세요.  

### <a name="install-client-computers-with-the-ccmsetup-clientmsi-option-smsdirectorylookupnowins"></a>CCMSetup Client.msi 옵션 SMSDIRECTORYLOOKUP=NoWINS를 사용하여 클라이언트 컴퓨터 설치  

클라이언트가 사이트 및 관리 지점을 찾을 수 있는 가장 안전한 서비스 위치 검색 방법은 Active Directory Domain Services를 사용하는 것입니다. 일부 환경에서는 이 방법을 사용할 수 없는 경우도 있습니다. 예를 들어 Configuration Manager에 대한 Active Directory 스키마를 확장할 수 없거나 클라이언트가 신뢰할 수 없는 포리스트 또는 작업 그룹에 있기 때문입니다. 이 방법을 사용할 수 없으면 DNS 게시를 대체 서비스 위치 방법으로 사용합니다. 이 두 가지 방법이 모두 실패하고 관리 지점이 HTTPS 클라이언트 연결에 대해 구성되지 않은 경우 클라이언트에서 WINS 사용으로 대체할 수 있습니다.  

WINS에 게시하는 것은 다른 게시 방법보다 안전하지 않습니다. **SMSDIRECTORYLOOKUP=NoWINS**를 지정하여 클라이언트 컴퓨터에서 WINS 사용으로 대체하지 않도록 구성합니다. 서비스 위치에 WINS를 사용해야 하는 경우 **SMSDIRECTORYLOOKUP=WINSSECURE**를 사용합니다. 이 설정은 기본값입니다. Configuration Manager 신뢰할 수 있는 루트 키를 사용하여 관리 지점의 자체 서명된 인증서의 유효성을 검사합니다.  

> [!NOTE]  
> **SMSDIRECTORYLOOKUP=WINSSECURE**에 대해 클라이언트를 구성하고 WINS에서 관리 지점을 찾으면 클라이언트에서 WMI에 있는 Configuration Manager 신뢰할 수 있는 루트 키의 복사본을 확인합니다.  
>
> 관리 지점 인증서의 서명이 클라이언트의 신뢰할 수 있는 루트 키 복사본과 일치하면 인증서의 유효성이 검사됩니다. 인증서의 유효성이 검사되면 클라이언트에서 WINS를 사용하여 찾은 관리 지점과 통신을 시작합니다.  
>
> 관리 지점 인증서의 서명이 클라이언트의 신뢰할 수 있는 루트 키 복사본과 일치하지 않으면 인증서가 유효하지 않습니다. 이 시나리오의 경우 클라이언트에서 WINS를 사용하여 찾은 관리 지점과 통신하지 않습니다.  

### <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>유지 관리 기간을 중요 소프트웨어 업데이트를 충분히 배포할 수 있을 만큼 설정합니다.  

디바이스 컬렉션에 대한 유지 관리 기간은 Configuration Manager에서 이러한 디바이스에 소프트웨어를 설치할 수 있는 횟수를 제한합니다. 유지 관리 기간을 너무 짧게 구성하면 클라이언트에서 중요한 소프트웨어 업데이트를 설치하지 않을 수 있습니다. 이 동작으로 인해 클라이언트는 소프트웨어 업데이트로 완화되는 모든 공격에 취약하게 됩니다.  

### <a name="take-additional-security-precautions-to-reduce-the-attack-surface-on-windows-embedded-devices-with-write-filters"></a>쓰기 필터가 있는 Windows Embedded 디바이스의 공격 표면을 줄이기 위한 추가 보안 예방 조치 수행  

Windows Embedded 디바이스에서 쓰기 필터를 사용하도록 설정하면 모든 소프트웨어 설치 또는 변경이 오버레이에만 수행됩니다. 이러한 변경은 디바이스를 다시 시작한 후에도 유지되지 않습니다. Configuration Manager를 사용하여 쓰기 필터를 사용하지 않도록 설정하면 이 기간 동안 Embedded 디바이스는 모든 볼륨의 변경에 취약합니다. 이러한 볼륨에는 공유 폴더가 포함됩니다.  

Configuration Manager는 로컬 관리자만 로그인할 수 있도록 이 기간 동안 컴퓨터를 잠급니다. 가능하면 컴퓨터를 보호하기 위해 추가 보안 예방 조치를 수행합니다. 예를 들어 방화벽에 대한 추가 제한을 사용하도록 설정합니다.  

유지 관리 기간을 사용하여 변경을 유지하는 경우 이러한 기간을 신중하게 계획합니다. 쓰기 필터를 사용하지 않도록 설정되는 기간은 최소화하는 한편, 소프트웨어 설치 및 다시 시작을 완료할 수 있을 만큼 충분히 길게 만듭니다.  

### <a name="use-the-latest-client-version-with-software-update-based-client-installation"></a>소프트웨어 업데이트 기반 클라이언트 설치를 통해 최신 클라이언트 버전 사용

소프트웨어 업데이트 기반 클라이언트 설치를 사용하고 사이트에 최신 버전의 클라이언트를 설치하는 경우 게시된 소프트웨어 업데이트를 업데이트합니다. 그런 다음, 클라이언트는 소프트웨어 업데이트 지점에서 최신 버전을 받습니다.  

사이트를 업데이트하면 소프트웨어 업데이트 지점에 게시된 클라이언트 배포용 소프트웨어 업데이트가 자동으로 업데이트되지 않습니다. Configuration Manager 클라이언트를 소프트웨어 업데이트 지점에 다시 게시하고 버전 번호를 업데이트합니다.  

자세한 내용은 [소프트웨어 업데이트 기반 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientSUP)을 참조하세요.  

### <a name="only-suspend-bitlocker-pin-entry-on-trusted-and-restricted-access-devices"></a>신뢰할 수 있고 액세스가 제한된 디바이스에서만 BitLocker PIN 항목 일시 중단  

신뢰할 수 있고 물리적 액세스가 제한된 컴퓨터에 대해서만 **다시 시작 시 BitLocker PIN 항목 일시 중단** 클라이언트 설정을 **항상**으로 구성합니다.

이 클라이언트 설정을 **항상**으로 설정하면 Configuration Manager에서 소프트웨어 설치를 완료할 수 있습니다. 이 동작은 중요 소프트웨어 업데이트를 설치하고 서비스를 다시 시작하는 데 도움이 됩니다. 공격자가 다시 시작 프로세스를 가로채는 경우 컴퓨터 제어를 수행할 수도 있습니다. 이 설정은 컴퓨터를 신뢰하고 컴퓨터에 대한 물리적 액세스가 제한된 경우에만 사용합니다. 예를 들어 이 설정은 데이터 센터의 서버에 적합할 수 있습니다.  

이 클라이언트 설정에 대한 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#suspend-bitlocker-pin-entry-on-restart)를 참조하세요.  

### <a name="dont-bypass-powershell-execution-policy"></a>PowerShell 실행 정책 바이패스 안 함

**PowerShell 실행 정책**에 대한 Configuration Manager 클라이언트 설정을 **바이패스**로 구성하면 Windows에서 서명되지 않은 PowerShell 스크립트를 실행할 수 있습니다. 이 동작을 통해 클라이언트 컴퓨터에서 맬웨어가 실행될 수 있습니다. 조직에서 이 옵션이 필요하면 사용자 지정 클라이언트 설정을 사용합니다. 이 클라이언트 설정은 서명되지 않은 PowerShell 스크립트를 실행해야 하는 클라이언트 컴퓨터에만 할당합니다.  

이 클라이언트 설정에 대한 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#powershell-execution-policy)를 참조하세요.  


## <a name="bkmk_mobile"></a> 모바일 디바이스에 대한 보안 모범 사례  

### <a name="install-the-enrollment-proxy-point-in-a-perimeter-network-and-the-enrollment-point-in-the-intranet"></a>경계 네트워크에 등록 프록시 지점 설치 및 인트라넷에 등록 지점 설치  

Configuration Manager에서 등록한 인터넷 기반 모바일 디바이스의 경우 경계 네트워크에 등록 프록시 지점과 인트라넷에 등록 지점을 설치합니다. 이 역할 구분을 통해 등록 지점을 공격으로부터 보호할 수 있습니다. 공격자가 등록 지점을 손상시키면 인증용 인증서를 얻을 수 있습니다. 또한 모바일 디바이스를 등록한 사용자의 자격 증명을 도용할 수도 있습니다.  

### <a name="configure-the-password-settings-to-help-protect-mobile-devices-from-unauthorized-access"></a>암호 설정을 구성하여 모바일 디바이스에 무단 액세스 방지  

*Configuration Manager에서 등록된 모바일 디바이스의 경우*: 모바일 디바이스 구성 항목을 사용하여 암호 복잡도를 PIN으로 구성합니다. 적어도 기본 최소 암호 길이를 지정합니다.  

*Configuration Manager 클라이언트가 설치되지 않았지만 Exchange Server 커넥터에서 관리되는 모바일 디바이스의 경우*: Exchange Server 커넥터에 대한 **암호 설정**에서 암호 복잡도를 PIN으로 구성합니다. 적어도 기본 최소 암호 길이를 지정합니다.  

### <a name="only-allow-applications-to-run-that-are-signed-by-companies-that-you-trust"></a>신뢰할 수 있는 회사에서 서명한 애플리케이션만 실행하도록 허용  

신뢰할 수 있는 회사에서 서명한 경우에만 애플리케이션을 실행할 수 있도록 하여 인벤토리 정보 및 상태 정보에 대한 무단 변경을 방지하는 데 도움이 됩니다. 디바이스에서 서명되지 않은 파일을 설치하도록 허용하지 않습니다.  

*Configuration Manager에서 등록된 모바일 디바이스의 경우*: 모바일 디바이스 구성 항목을 사용하여 **서명되지 않은 애플리케이션** 보안 설정을 **허용 안 함**으로 구성합니다. **서명되지 않은 파일 설치**를 신뢰할 수 있는 원본으로 구성합니다.  

*Configuration Manager 클라이언트가 설치되지 않았지만 Exchange Server 커넥터에서 관리되는 모바일 디바이스의 경우*: Exchange Server 커넥터에 대한 **애플리케이션 설정**에서 **서명되지 않은 파일 설치** 및 **서명되지 않은 애플리케이션**을 **허용 안 함**으로 구성합니다.  

### <a name="lock-mobile-devices-when-not-in-use"></a>사용하지 않을 때 모바일 디바이스 잠금  

모바일 디바이스를 사용하지 않을 때 잠금으로써 권한 상승 공격을 방지할 수 있습니다.

*Configuration Manager에서 등록된 모바일 디바이스의 경우*: 모바일 디바이스 구성 항목을 사용하여 암호 설정 **다음 유휴 시간 후 모바일 디바이스 잠그기(분)** 를 구성합니다.  

*Configuration Manager 클라이언트가 설치되지 않았지만 Exchange Server 커넥터에서 관리되는 모바일 디바이스의 경우*: Exchange Server 커넥터에 대한 **암호 설정**에서 **다음 유휴 시간 후 모바일 디바이스 잠그기(분)** 를 설정합니다.  

### <a name="restrict-the-users-who-can-enroll-their-mobile-devices"></a>모바일 디바이스를 등록할 수 있는 사용자 제한  

모바일 디바이스를 등록할 수 있는 사용자를 제한하여 권한 상승을 방지합니다. 기본 클라이언트 설정 대신 사용자 지정 클라이언트 설정을 사용하여 권한 있는 사용자만 모바일 디바이스를 등록할 수 있도록 합니다.  

### <a name="user-device-affinity-guidance-for-mobile-devices"></a>모바일 디바이스에 대한 사용자 디바이스 선호도 지침  

Configuration Manager 또는 Microsoft Intune에서 등록된 모바일 디바이스가 있는 사용자에게 애플리케이션을 배포할 수 없는 시나리오는 다음과 같습니다.  

- 둘 이상의 사용자가 모바일 디바이스를 사용합니다.  

- 사용자를 대신하여 관리자가 디바이스를 등록합니다.  

- 사용 중지한 후에 다시 등록하지 않은 디바이스가 다른 사용자에게 양도됩니다.  

디바이스를 등록하면 사용자 디바이스 선호도 관계가 만들어집니다. 이 관계는 등록을 수행하는 사용자를 모바일 디바이스에 매핑합니다. 다른 사용자가 모바일 디바이스를 사용하면 원래 사용자에게 배포된 애플리케이션을 실행할 수 있으며, 이에 따라 권한이 상승할 수 있습니다. 마찬가지로, 관리자가 사용자를 대신하여 모바일 디바이스를 등록하는 경우 해당 사용자에게 배포된 애플리케이션은 모바일 디바이스에 설치되지 않습니다. 대신, 관리자에게 배포된 애플리케이션이 설치될 수 있습니다.  

Windows 컴퓨터에 대한 사용자 디바이스 선호도와 달리, Microsoft Intune에서 등록된 모바일 디바이스에 대한 사용자 디바이스 선호도 정보는 수동으로 정의할 수 없습니다.  

Intune에서 등록된 모바일 디바이스의 소유권을 이전하는 경우 먼저 Intune에서 모바일 디바이스가 사용 중지됩니다. 이 작업은 사용자 디바이스 선호도 관계를 제거합니다. 그런 다음, 현재 사용자에게 디바이스를 다시 등록하도록 요청합니다.  

### <a name="make-sure-that-users-enroll-their-own-mobile-devices-for-microsoft-intune"></a>사용자가 자신의 모바일 디바이스를 Microsoft Intune에 등록했는지 확인  

사용자 디바이스 선호도 관계는 등록 중에 만들어집니다. 이 작업은 등록을 수행하는 사용자를 모바일 디바이스에 매핑합니다. 관리자가 사용자를 대신하여 모바일 디바이스를 등록하는 경우 해당 사용자에게 배포된 애플리케이션은 모바일 디바이스에 설치되지 않습니다. 대신, 관리자에게 배포된 애플리케이션이 설치될 수 있습니다.  

### <a name="protect-the-connection-between-the-configuration-manager-site-server-and-the-exchange-server"></a>Configuration Manager 사이트 서버와 Exchange Server 간의 연결 보호

Exchange Server가 온-프레미스인 경우 IPsec을 사용합니다. 호스팅된 Exchange는 SSL을 사용하여 자동으로 연결을 보호합니다.  

### <a name="use-the-principle-of-least-privileges-for-the-connector"></a>커텍터에 최소 권한의 원칙 적용  

Exchange Server 커넥터에 필요한 최소 cmdlet의 목록은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  


## <a name="bkmk_macs"></a> Mac에 대한 보안 모범 사례  

### <a name="store-and-access-the-client-source-files-from-a-secured-location"></a>보안 위치의 클라이언트 원본 파일 저장 및 액세스  

Configuration Manager는 클라이언트를 Mac 컴퓨터에 설치하거나 등록하기 전에 이러한 클라이언트 원본 파일이 변조되었는지 확인하지 않습니다. 이러한 파일은 신뢰할 수 있는 원본에서 다운로드합니다. 안전하게 저장하고 액세스합니다.  

### <a name="monitor-and-track-the-validity-period-of-the-certificate"></a>인증서 유효 기간 모니터링 및 추적  

무중단 업무를 보장하기 위해 Mac 컴퓨터에 대해 사용하는 인증서의 유효 기간을 모니터링 및 추적합니다. Configuration Manager는 이 인증서의 자동 갱신을 지원하지 않거나 인증서가 곧 만료될 것이라고 경고하지 않습니다. 일반적인 유효 기간은 1년입니다.  

인증서를 갱신하는 방법에 대한 자세한 내용은 [Mac 클라이언트 인증서를 수동으로 갱신](/sccm/core/clients/deploy/deploy-clients-to-macs#renew-the-mac-client-certificate)을 참조하세요.  

### <a name="configure-the-trusted-root-certificate-for-ssl-only"></a>SSL에 대해서만 신뢰할 수 있는 루트 인증서 구성  

권한 상승을 방지하기 위해 신뢰할 수 있는 루트 인증 기관에 대한 인증서를 SSL 프로토콜에 대해서만 신뢰할 수 있도록 구성합니다.

Mac 컴퓨터를 등록하면 Configuration Manager 클라이언트를 관리하는 사용자 인증서가 자동으로 설치됩니다. 이 사용자 인증서의 신뢰 체인에는 신뢰할 수 있는 루트 인증서가 포함됩니다. 이 루트 인증서의 신뢰를 SSL 프로토콜로만 제한하려면 다음 절차를 사용합니다.  

1. Mac 컴퓨터에서 터미널 창을 엽니다.  

2. 다음 명령을 입력합니다. `sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access`  

3. **키 집합 액세스** 대화 상자의 **키 집합** 섹션에서 **시스템**을 클릭합니다. 그런 다음, **범주** 섹션에서 **인증서**를 클릭합니다.  

4. Mac 클라이언트 인증서용 루트 CA 인증서를 찾은 다음, 두 번 클릭합니다.  

5. 루트 CA 인증서의 대화 상자에서 **신뢰** 섹션을 확장하고 다음과 같이 변경합니다.  

    1. **이 인증서를 사용하는 경우**: **항상 신뢰** 설정을 **시스템 기본값 사용**으로 변경합니다.  

    2. **SSL(Secure Sockets Layer)** : **값이 지정되지 않음**을 **항상 신뢰**로 변경합니다.  

6. 대화 상자를 닫습니다. 메시지가 표시되면 관리자의 암호를 입력한 다음, **설정 업데이트**를 클릭합니다.  

이 절차가 완료되면 SSL 프로토콜의 유효성을 검사하는 데에만 루트 인증서가 신뢰됩니다. 이제 이 루트 인증서를 신뢰할 수 없는 다른 프로토콜에는 보안 메일(S/MIME), 확장할 수 있는 인증(EAP) 또는 코드 서명이 있습니다.  

> [!NOTE]  
> Configuration Manager와 별도로 클라이언트 인증서를 설치한 경우에도 이 절차를 사용하세요.


## <a name="BKMK_SecurityIssues_Clients"></a> Configuration Manager 클라이언트에 대한 보안 문제  

다음 보안 문제는 최소화할 수 없습니다.  

### <a name="status-messages-arent-authenticated"></a>상태 메시지가 인증되지 않음

상태 메시지에 대해 인증이 수행되지 않습니다. 관리 지점에서 HTTP 클라이언트 연결을 허용하면 모든 디바이스는 이 관리 지점에 상태 메시지를 보낼 수 있습니다. 관리 지점에서 HTTPS 클라이언트 연결만 허용하는 경우 디바이스에는 유효한 클라이언트 인증 인증서가 있어야 하지만 상태 메시지를 보낼 수도 있습니다. 관리 지점은 클라이언트에서 받은 잘못된 상태 메시지를 삭제합니다.  

이 취약성에 대한 몇 가지 잠재적인 공격은 다음과 같습니다.

- 공격자는 컬렉션에서 상태 메시지 쿼리에 기반한 구성원 자격을 얻기 위해 위조 상태 메시지를 보낼 수 있습니다.
- 모든 클라이언트는 상태 메시지를 대량으로 보냄으로써 관리 지점의 서비스 거부를 시작할 수 있습니다.
- 상태 메시지로 인해 상태 메시지 필터 규칙의 작업이 트리거될 경우 공격자는 상태 메시지 필터 규칙을 트리거할 수 있습니다.
- 공격자는 보고 정보가 부정확하게 렌더링되는 상태 메시지를 보낼 수 있습니다.  

### <a name="policies-can-be-retargeted-to-non-targeted-clients"></a>정책의 대상이 원래 대상이 아닌 클라이언트로 다시 지정될 수 있습니다.  

공격자는 여러 방법을 사용하여 일정한 클라이언트를 대상으로 한 정책이 완전히 다른 클라이언트에 적용되도록 할 수 있습니다. 예를 들어 신뢰할 수 있는 클라이언트의 공격자는 컴퓨터가 속해 있지 않아야 하는 컬렉션에 추가되도록 하는 허위 인벤토리 또는 검색 정보를 보낼 수 있습니다. 그런 다음, 해당 클라이언트에서 해당 컬렉션에 대한 모든 배포를 받습니다.

공격자가 정책을 직접 수정할 수 없도록 하는 컨트롤이 있습니다. 그러나 공격자는 OS를 다시 포맷하고 다시 배포하는 기존 정책을 사용하여 다른 컴퓨터로 보낼 수 있습니다. 이 리디렉션된 정책은 서비스 거부를 만들 수 있습니다. 이러한 공격 유형은 정확한 시간 계산과 Configuration Manager 인프라에 대한 폭넓은 지식을 필요로 합니다.  

### <a name="client-logs-allow-user-access"></a>클라이언트 로그를 통한 사용자 액세스  

모든 클라이언트 로그 파일은 *읽기* 액세스 권한이 있는 **사용자** 그룹과 *쓰기* 액세스 권한이 있는 특수 **대화형** 사용자를 허용합니다. 자세한 정보 로깅을 사용하도록 설정할 경우 공격자는 로그 파일을 읽어 호환성 또는 시스템 취약점에 대한 정보를 찾을 수도 있습니다. 클라이언트가 사용자의 컨텍스트에서 설치하는 소프트웨어와 같은 프로세스는 낮은 수준의 권한이 있는 사용자 계정으로 로그에 기록해야 합니다. 이 동작은 공격자도 낮은 수준의 권한이 있는 계정을 사용하여 로그에 쓸 수 있음을 의미합니다.  

가장 심각한 위험은 공격자가 로그 파일의 정보를 제거할 수 있다는 것입니다. 관리자는 감사 및 침입 탐지에 이 정보가 필요할 수 있습니다.  

### <a name="a-computer-could-be-used-to-obtain-a-certificate-thats-designed-for-mobile-device-enrollment"></a>컴퓨터를 사용하여 모바일 디바이스 등록을 위해 설계된 인증서를 가져올 수 있음  

Configuration Manager는 등록 요청을 처리할 때 컴퓨터가 아닌 모바일 디바이스에서 해당 요청이 시작되었는지 여부를 확인할 수 없습니다. 컴퓨터에서 요청이 시작된 경우에도 Configuration Manager에 등록할 수 있도록 하는 PKI 인증서가 설치될 수 있습니다.

이 시나리오에서 권한 상승 공격을 방지하려면 신뢰할 수 있는 사용자만 자신의 모바일 디바이스를 등록할 수 있도록 허용합니다. 사이트에서 디바이스 등록 활동을 신중하게 모니터링합니다.  

### <a name="a-blocked-client-can-still-send-messages-to-the-management-point"></a>차단된 클라이언트는 관리 지점으로 메시지를 계속 보낼 수 있습니다.

더 이상 신뢰하지 않는 클라이언트를 차단하지만 클라이언트 알림에 대한 네트워크 연결을 설정한 경우 Configuration Manager에서 세션의 연결을 끊지 않습니다. 차단된 클라이언트는 네트워크 연결이 끊어지지 않는 한 관리 지점에 계속 패킷을 보낼 수 있습니다. 이러한 패킷은 작은 연결 유지(keep-alive) 패킷일 뿐입니다. 이 클라이언트는 차단 해제될 때까지 Configuration Manager에서 관리할 수 없습니다.  

### <a name="automatic-client-upgrade-doesnt-verify-the-management-point"></a>자동 클라이언트 업그레이드에서 관리 지점을 확인하지 않음

자동 클라이언트 업그레이드를 사용하면 클라이언트를 관리 지점으로 이동하여 클라이언트 원본 파일을 다운로드할 수 있습니다. 이 시나리오에서 클라이언트는 관리 지점을 신뢰할 수 있는 원본으로 확인하지 않습니다.  

### <a name="when-users-first-enroll-mac-computers-theyre-at-risk-from-dns-spoofing"></a>사용자가 Mac 컴퓨터를 처음 등록하면 DNS 스푸핑으로 인해 발생하는 위험이 있음  

등록 중에 Mac 컴퓨터가 등록 프록시 지점에 연결되면 Mac 컴퓨터에 신뢰할 수 있는 루트 CA 인증서가 이미 없을 가능성이 높습니다. 이 시점에서 Mac 컴퓨터는 서버를 신뢰하지 않고 사용자에게 계속하라는 메시지를 표시합니다. Rogue DNS 서버에서 등록 프록시 지점의 FQDN(정규화된 도메인 이름)을 확인하면 Mac 컴퓨터를 Rogue 등록 프록시 지점으로 연결하여 신뢰할 수 없는 원본의 인증서를 설치할 수 있습니다. 이 위험을 줄이려면 사용 중인 환경에서 DNS 스푸핑을 방지하기 위한 모범 사례를 따르세요.  

### <a name="mac-enrollment-doesnt-limit-certificate-requests"></a>Mac 등록에서 인증서 요청을 제한하지 않음  

사용자는 매번 새 클라이언트 인증서를 요청하여 Mac 컴퓨터를 다시 등록할 수 있습니다. Configuration Manager는 여러 요청을 확인하지 않거나 단일 컴퓨터에서 요청하는 인증서의 수를 제한하지 않습니다. Rogue 사용자는 명령줄 등록 요청을 반복하는 스크립트를 실행할 수 있습니다. 이 공격으로 인해 네트워크 또는 발급 CA(인증 기관)에서 서비스 거부가 발생할 수 있습니다. 이 위험을 줄이려면 발급 CA에서 이런 유형의 의심스러운 동작을 주의 깊게 모니터링하세요. 이 동작 패턴을 보여 주는 컴퓨터는 Configuration Manager 계층 구조에서 즉시 차단합니다.  

### <a name="a-wipe-acknowledgment-doesnt-verify-that-the-device-has-been-successfully-wiped"></a>초기화 승인에서 디바이스가 성공적으로 초기화되었는지 확인하지 않음  

모바일 디바이스에 대한 초기화 작업을 시작하고 Configuration Manager에서 이 초기화를 승인하는 경우 확인은 Configuration Manager는 메시지를 성공적으로 *보냈다*는 것입니다. 디바이스가 요청에 대해 *작동했는지*는 확인하지 않습니다.

Exchange Server 커넥터에서 관리하는 모바일 디바이스의 경우 초기화 승인은 디바이스가 아니라 Exchange에서 명령을 받았음을 확인합니다.  

### <a name="if-you-use-the-options-to-commit-changes-on-windows-embedded-devices-accounts-might-be-locked-out-sooner-than-expected"></a>옵션을 사용하여 Windows Embedded 디바이스에서 변경을 커밋하는 경우 계정이 예상보다 빨리 잠길 수 있음  

Windows Embedded 디바이스가 Windows 7 이전 버전의 OS를 실행 중이고 Configuration Manager에서 쓰기 필터를 사용하지 않도록 설정하는 동안 사용자가 로그인을 시도하는 경우 Windows는 계정을 잠그기 전에 구성된 잘못된 시도 횟수의 절반만 허용합니다.

예를 들어 **계정 잠금 임계값**에 대한 도메인 정책을 6회의 시도로 구성합니다. 사용자가 암호를 3회 잘못 입력하면 계정이 잠깁니다. 이 동작은 서비스 거부를 효과적으로 만듭니다. 이 시나리오에서 사용자가 임베디드 디바이스에 로그인해야 하는 경우 축소된 잠금 임계값에 대한 가능성에 주의합니다.  


## <a name="BKMK_Privacy_Clients"></a> Configuration Manager 클라이언트에 대한 개인 정보  

Configuration Manager 클라이언트를 배포할 때 Configuration Manager 기능에 대한 클라이언트 설정을 사용하도록 설정합니다. 기능을 구성하는 데 사용하는 설정은 Configuration Manager 계층 구조의 모든 클라이언트에 적용할 수 있습니다. 이 동작은 내부 네트워크에 직접 연결되어 있든지, 원격 세션을 통해 연결되어 있든지, 인터넷에 연결되어 있든지 간에 동일합니다.  

클라이언트 정보는 SQL Server의 Configuration Manager 데이터베이스에 저장되며, Microsoft로 전송되지 않습니다. 정보는 90일마다 반복되는 **오래된 검색 데이터 삭제** 사이트 유지 관리 작업으로 삭제될 때까지 데이터베이스에서 유지됩니다. 삭제 간격은 필요에 따라 구성할 수 있습니다. 

요약되거나 집계된 진단 및 사용량 현황 데이터 중 일부는 Microsoft로 전송됩니다. 자세한 내용은 [진단 및 사용량 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.  

Configuration Manager 클라이언트를 구성하기 전에 개인 정보 요구 사항을 고려해야 합니다.  

[Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement)에서 Microsoft의 데이터 수집 및 사용에 대해 자세히 알아볼 수 있습니다.

### <a name="client-status"></a>클라이언트 상태  

Configuration Manager는 클라이언트의 활동을 모니터링합니다. 정기적으로 Configuration Manager 클라이언트를 평가하고, 클라이언트 및 해당 종속성과 관련된 문제를 해결할 수 있습니다. 클라이언트 상태는 기본적으로 사용하도록 설정됩니다. 서버 쪽 메트릭을 사용하여 클라이언트 활동을 확인합니다. 클라이언트 상태는 자체 점검, 수정 및 사이트로의 클라이언트 상태 정보 전송에 대한 클라이언트 쪽 작업을 사용합니다. 클라이언트는 구성한 일정에 따라 자체 점검을 실행합니다. 클라이언트는 Configuration Manager 사이트로 검사 결과를 보냅니다. 이 정보는 전송 도중 암호화됩니다.  

클라이언트 상태 정보는 SQL Server의 Configuration Manager 데이터베이스에 저장되며, Microsoft로 전송되지 않습니다. 정보는 암호화된 형식으로 사이트 데이터베이스에 저장되지 않습니다. 이 정보는 **다음 기간(일) 동안 클라이언트 상태 기록 유지** 클라이언트 상태 설정에 구성된 값에 따라 삭제될 때까지 데이터베이스에서 유지됩니다. 이 설정의 기본값은 31일입니다.  

클라이언트 상태 점검과 함께 Configuration Manager 클라이언트를 설치하기 전에 개인 정보 요구 사항을 고려해야 합니다.  


## <a name="BKMK_Privacy_ExchangeConnector"></a> Exchange Server 커넥터를 사용하여 관리하는 모바일 디바이스에 대한 개인 정보  

Exchange Server 커넥터는 ActiveSync 프로토콜을 사용하여 온-프레미스 또는 호스팅된 Exchange Server에 연결된 디바이스를 찾아서 관리합니다. Exchange Server 커넥터에서 찾은 레코드는 SQL 서버의 Configuration Manager 데이터베이스에 저장됩니다. 정보는 Exchange Server에서 수집되며, 여기에는 모바일 디바이스에서 Exchange Server로 보내는 정보 이외의 다른 추가 정보는 포함되지 않습니다.  

모바일 디바이스 정보는 Microsoft로 전송되지 않으며, SQL 서버의 Configuration Manager 데이터베이스에 저장됩니다. 정보는 90일마다 반복되는 **오래된 검색 데이터 삭제** 사이트 유지 관리 작업으로 삭제될 때까지 데이터베이스에서 유지됩니다. 삭제 간격을 구성합니다.  

Exchange Server 커넥터를 설치하고 구성하기 전에 개인 정보 요구 사항을 고려해야 합니다.  

[Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement)에서 Microsoft의 데이터 수집 및 사용에 대해 자세히 알아볼 수 있습니다.
