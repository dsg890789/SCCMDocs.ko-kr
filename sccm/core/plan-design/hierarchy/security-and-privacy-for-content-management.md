---
title: 콘텐츠 관리 보안 및 개인 정보
titleSuffix: Configuration Manager
description: Configuration Manager의 콘텐츠 관리를 위한 보안 및 개인 정보를 최적화합니다.
ms.date: 10/26/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f665ea8315266e89e5ed94918823fc1b97becea
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62241710"
---
# <a name="security-and-privacy-for-content-management-in-configuration-manager"></a>Configuration Manager의 콘텐츠 관리를 위한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에는 Configuration Manager의 콘텐츠 관리를 위한 보안 및 개인 정보가 포함되어 있습니다. 



##  <a name="BKMK_Security_ContentManagement"></a> 콘텐츠 관리에 대한 보안 모범 사례  


#### <a name="advantages-and-disadvantages-of-https-or-http-for-intranet-distribution-points"></a>인트라넷 배포 지점에 대한 HTTPS 또는 HTTP의 장단점
인트라넷의 배포 지점에 대해 HTTPS와 HTTP 사용 시의 장단점을 고려합니다. 대부분의 시나리오에서는 암호화는 가능하지만 권한 부여가 불가능한 HTTPS를 사용할 때보다 HTTP와 권한 부여를 위한 패키지 액세스 계정을 사용할 때 보안이 강화됩니다. 그러나 콘텐츠에 중요한 데이터가 포함되어 있어 전송하는 동안 암호화하려면 HTTPS를 사용하세요.  

-   **배포 지점에 HTTPS를 사용하면** Configuration Manager에서 패키지 액세스 계정을 사용하여 콘텐츠에 대한 액세스 권한을 부여할 수 없지만 네트워크를 통해 콘텐츠를 전송할 때 콘텐츠가 암호화됩니다.  

-   **배포 지점에 HTTP를 사용하면** 권한 부여를 위해 패키지 액세스 계정을 사용할 수 있지만 네트워크를 통해 콘텐츠를 전송할 때 콘텐츠가 암호화되지 않습니다.  

버전1806부터 사이트에 **고급 HTTP**를 사용하도록 설정하는 것이 좋습니다. 이 기능을 사용하면 클라이언트가 Azure Active Directory 인증을 사용하여 HTTP 배포 지점과 안전하게 통신할 수 있습니다. 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.

#### <a name="protect-the-client-authentication-certificate-file"></a>클라이언트 인증 인증서 파일 보호
배포 지점에 자체 서명된 인증서가 아니라 PKI 클라이언트 인증 인증서를 사용하는 경우 인증서 파일(.pfx)을 강력한 암호로 보호합니다. 네트워크에 파일을 저장하는 경우 Configuration Manager로 파일을 가져올 때 네트워크 채널의 보안을 유지합니다.

배포 지점에서 관리 지점과 통신하는 데 사용하는 클라이언트 인증 인증서를 가져오기 위해 암호가 필요한 경우 이 구성을 사용하여 공격자로부터 인증서를 보호할 수 있습니다. 공격자가 인증서 파일을 변조하지 못하도록 네트워크 위치와 사이트 서버 사이에 SMB 서명 또는 IPsec을 사용합니다.  

#### <a name="remove-the-distribution-point-role-from-the-site-server"></a>사이트 서버에서 배포 지점 역할 제거
기본적으로 Configuration Manager 설정은 사이트 서버에 배포 지점을 설치합니다. 클라이언트는 사이트 서버와 직접 통신할 필요가 없습니다. 공격의 여지를 줄이기 위해 배포 지점 역할을 다른 사이트 시스템에 할당하고 해당 사이트 서버에서 제거하세요.  

#### <a name="secure-content-at-the-package-access-level"></a>패키지 액세스 수준으로 콘텐츠 보호
배포 지점 공유를 통해 모든 사용자에게 읽기 액세스 권한을 허용합니다. 콘텐츠에 액세스할 수 있는 사용자를 제한하려면 HTTP로 배포 지점을 구성할 때 패키지 액세스 계정을 사용하세요. 이 구성은 패키지 액세스 계정을 지원하지 않는 클라우드 배포 지점에는 적용되지 않습니다. 자세한 내용은 [패키지 액세스 계정](/sccm/core/plan-design/hierarchy/accounts#package-access-account)을 참조하세요.

#### <a name="configure-iis-on-the-distribution-point-role"></a>배포 지점 역할에 IIS 구성
배포 지점 사이트 시스템 역할을 추가할 때 Configuration Manager에서 IIS를 설치하는 경우 배포 지점 설치가 완료되면 HTTP 리디렉션 또는 IIS 관리 스크립트 및 도구를 제거합니다. 배포 지점에는 HTTP 리디렉션 또는 IIS 관리 스크립트 및 도구가 필요하지 않습니다. 공격의 여지를 줄이려면 웹 서버 역할에 대한 이러한 역할 서비스를 제거하세요.  배포 지점의 웹 서버 역할용 역할 서비스에 대한 자세한 내용은 [사이트 및 사이트 시스템 필수 구성 요소](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)를 참조하세요.  

#### <a name="set-package-access-permissions-when-you-create-the-package"></a>패키지를 만들 때 패키지 액세스 권한을 설정합니다.
패키지 파일의 액세스 계정을 변경하면 패키지를 재배포할 때만 적용되므로 패키지 액세스 권한은 패키지를 처음 만들 때 신중하게 설정하십시오. 이 구성은 패키지가 크거나 많은 배포 지점에 배포되거나 콘텐츠 배포를 위한 네트워크 대역폭 용량이 제한된 경우에 중요합니다.  

#### <a name="implement-access-controls-to-protect-media-that-contains-prestaged-content"></a>사전 준비된 콘텐츠가 포함된 미디어를 보호하기 위해 액세스 제어를 구현합니다.
사전 준비된 콘텐츠는 압축될 뿐 암호화되지는 않습니다. 공격자는 디바이스에 다운로드한 파일을 읽고 수정할 수 있습니다. Configuration Manager 클라이언트는 변조된 콘텐츠를 거부하지만 여전히 다운로드합니다.  

#### <a name="import-prestaged-content-with-extractcontent"></a>ExtractContent를 사용하여 사전 준비된 콘텐츠 가져오기
ExtractContent.exe 명령줄 도구를 사용하여 사전 준비된 콘텐츠만 가져옵니다. 변조 및 권한 상승을 방지하려면 Configuration Manager와 함께 제공되는 승인된 명령줄 도구만 사용합니다.  

#### <a name="secure-the-communication-channel-between-the-site-server-and-the-package-source-location"></a>사이트 서버와 패키지 원본 위치 간 통신 채널의 보안을 유지합니다.
애플리케이션 및 패키지를 만들 때 사이트 서버와 패키지 원본 위치 간에 IPsec 또는 SMB 서명을 사용합니다. 이 구성은 공격자가 원본 파일을 변조하지 못하도록 합니다.  

#### <a name="remove-default-virtual-directories-for-custom-website-with-the-distribution-point-role"></a>배포 지점 역할을 사용하여 사용자 지정 웹 사이트의 기본 가상 디렉터리 제거
배포 지점 역할을 설치한 후 기본 웹 사이트가 아닌 사용자 지정 웹 사이트를 사용하도록 사이트 구성 옵션을 변경하는 경우 기본 가상 디렉터리를 제거합니다. 기본 웹 사이트에서 사용자 지정 웹 사이트로 전환하면 Configuration Manager에서 이전 가상 디렉터리를 제거하지 않습니다. Configuration Manager에서 원래 기본 웹 사이트 아래에 생성한 다음 가상 디렉터리를 제거합니다.  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  


#### <a name="for-cloud-distribution-points-protect-your-azure-subscription-details-and-certificates"></a>클라우드 배포 지점의 경우 Azure 구독 세부 정보 및 인증서 보호
클라우드 배포 지점을 사용하는 경우 다음과 같은 중요한 항목을 보호합니다.
- Azure 구독의 사용자 이름 및 암호
- Azure 관리 인증서 
- 클라우드 배포 지점 서비스 인증서

인증서를 안전하게 저장합니다. 클라우드 배포 지점을 구성할 때 네트워크를 통해 찾는 경우 사이트 시스템 서버와 원본 위치 간에 IPsec 또는 SMB 서명을 사용합니다.  

#### <a name="for-service-continuity-monitor-the-expiry-date-of-the-cloud-distribution-point-certificates"></a>서비스 연속성을 위해 클라우드 배포 지점 인증서의 만료 날짜 모니터링
Configuration Manager에서는 클라우드 배포 지점에 가져온 인증서가 곧 만료될 예정이어도 경고하지 않습니다. Configuration Manager와 별도로 만료 날짜를 모니터링하세요. 만료 날짜 전에 갱신한 다음, 새 인증서를 가져와야 합니다. 이 작업이 중요한 이유는 외부 공용 공급자로부터 서버 인증 인증서를 받는 경우, 갱신된 인증서를 획득하는 데 추가 시간이 필요할 수 있기 때문입니다.  

 인증서 중 하나가 만료되면 Cloud Services Manager가 상태 메시지 ID **9425**를 생성합니다. CloudMgr.log 파일에는 인증서가 **만료된 상태**임을 나타내는 항목이 포함되어 있으며 만료 날짜도 UTC에 기록됩니다.  



## <a name="security-considerations-for-content-management"></a>콘텐츠 관리에 대한 보안 고려 사항  

콘텐츠 관리를 계획할 때는 다음 사항을 고려합니다.  

-   클라이언트는 다운로드가 완료될 때까지 콘텐츠 유효성 검사를 수행하지 않습니다.  

     Configuration Manager 클라이언트는 해당 클라이언트 캐시에 콘텐츠가 다운로드된 후에만 콘텐츠의 해시에 대한 유효성을 검사합니다. 다운로드할 파일 목록이나 콘텐츠 자체를 공격자가 변조하면 다운로드 프로세스에서 네트워크 대역폭을 많이 사용할 수 있으며, 클라이언트는 잘못된 해시를 발견한 경우에만 콘텐츠를 삭제합니다.  

-   클라우드 배포 지점을 사용하면 콘텐츠에 대한 액세스가 자동으로 엔터프라이즈로 제한됩니다. 선택한 사용자 또는 그룹으로 더 이상 제한할 수 없습니다.  

-   클라우드 배포 지점을 사용하는 경우 클라이언트는 관리 지점에서 인증을 받은 다음, Configuration Manager 토큰을 사용하여 클라우드 배포 지점에 액세스합니다. 토큰은 8시간 동안 유효합니다. 이 동작을 수행하면 클라이언트를 더 이상 신뢰할 수 없어 차단하는 경우 이 토큰의 유효 기간이 만료될 때까지 클라우드 배포 지점에서 콘텐츠를 계속 다운로드할 수 있습니다. 이때 클라이언트가 차단되었기 때문에 관리 지점에서 해당 클라이언트에 대해 다른 토큰을 발행하지 않습니다.  

     차단된 클라이언트가 이 8시간 이내에 콘텐츠를 다운로드하지 않도록 하려면 클라우드 서비스를 중지하세요. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **클라우드 배포 지점** 노드를 선택합니다.  



##  <a name="BKMK_Privacy_ContentManagement"></a> 콘텐츠 관리를 위한 개인 정보  

 관리자가 이 작업을 수행하도록 선택할 수 있지만 Configuration Manager에서는 콘텐츠 파일에 사용자 데이터를 포함하지 않습니다.  



## <a name="see-also"></a>참고 항목

- [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)  

- [애플리케이션 관리에 대한 보안 및 개인 정보](/sccm/apps/plan-design/security-and-privacy-for-application-management)  

- [소프트웨어 업데이트에 대한 보안 및 개인 정보](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

- [OS 배포를 위한 보안 및 개인정보](/sccm/osd/plan-design/security-and-privacy-for-operating-system-deployment)  
