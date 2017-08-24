---
title: "콘텐츠 관리 보안 및 개인 정보 | Microsoft 문서"
description: "System Center Configuration Manager에서 콘텐츠 관리에 대한 보안 및 개인 정보를 최적화합니다."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: c4b9d13079c313879c6d43b10867c616fa962668
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-content-management-for-system-center-configuration-manager"></a>System Center Configuration Manager에서 콘텐츠 관리에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager에서 콘텐츠 관리에 대한 보안 및 개인 정보가 포함되어 있습니다. 다음 항목과 함께 읽어 보십시오.  

-   [System Center Configuration Manager에서 응용 프로그램 관리에 대한 보안 및 개인 정보](../../../apps/plan-design/security-and-privacy-for-application-management.md)  

-   [System Center Configuration Manager에서 소프트웨어 업데이트에 대한 보안 및 개인 정보](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

-   [System Center Configuration Manager에서 운영 체제 배포의 보안 및 개인 정보](../../../osd/plan-design/security-and-privacy-for-operating-system-deployment.md)  

##  <a name="BKMK_Security_ContentManagement"></a> 콘텐츠 관리에 대한 보안 모범 사례  
 콘텐츠 관리에 대해서는 다음 보안 모범 사례를 사용하세요.  

 **인트라넷의 배포 지점에 대한 HTTPS와 HTTP 사용의 장단점을 고려**: 대부분의 시나리오에서는 암호화는 가능하지만 권한 부여가 불가능한 HTTPS를 사용할 때보다 HTTP와 권한 부여를 위한 패키지 액세스 계정을 사용할 때 보안이 강화됩니다. 그러나 콘텐츠에 중요한 데이터가 포함되어 있어 전송하는 동안 암호화하려면 HTTPS를 사용하세요.  

-   **배포 지점에 HTTPS를 사용하면** Configuration Manager에서 패키지 액세스 계정을 사용하여 콘텐츠에 대한 액세스 권한을 부여할 수 없지만 네트워크를 통해 콘텐츠를 전송할 때 콘텐츠가 암호화됩니다.  

-   **배포 지점에 HTTP를 사용하면**권한 부여를 위해 패키지 액세스 계정을 사용할 수 있지만 네트워크를 통해 콘텐츠를 전송할 때 콘텐츠가 암호화되지 않습니다.  


**배포 지점에 자체 서명된 인증서가 아니라 PKI 클라이언트 인증 인증서를 사용하는 경우 인증서 파일(.pfx)을 강력한 암호로 보호합니다. 네트워크에 파일을 저장하는 경우 파일을 Configuration Manager로 가져올 때 네트워크 채널 보호**: 배포 지점에서 관리 지점과 통신하기 위해 사용하는 클라이언트 인증 인증서를 가져올 때 암호를 요구하면 인증서를 공격자로부터 보호할 수 있습니다. 공격자가 인증서 파일을 변조하지 못하도록 네트워크 위치와 사이트 서버 사이에 SMB 서명 또는 IPsec을 사용합니다.  

**사이트 서버에서 배포 지점 역할 제거**: 기본적으로 배포 지점은 사이트 서버와 같은 서버에 설치됩니다. 클라이언트는 사이트 서버와 직접 통신할 필요가 없으므로 공격의 여지를 줄이기 위해 배포 지점 역할을 다른 사이트 시스템에 할당하고 해당 사이트 서버에서 제거하세요.  

**패키지 액세스 수준으로 콘텐츠 보호**: 배포 지점 공유에서는 모든 사용자에게 읽기 권한이 허용됩니다. 콘텐츠에 액세스할 수 있는 사용자를 제한하려면 HTTP로 배포 지점을 구성할 때 패키지 액세스 계정을 사용하세요. 패키지 액세스 계정을 지원하지 않는 클라우드 기반 배포 지점에는 이 방법이 적용되지 않습니다. 패키지 액세스 계정에 대한 자세한 내용은 [콘텐츠에 액세스하기 위한 계정 관리](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md)를 참조하세요.


**배포 지점 사이트 시스템 역할을 추가할 때 Configuration Manager에서 IIS를 설치하는 경우 배포 지점 설치가 완료되면 HTTP 리디렉션 또는 IIS 관리 스크립트 및 도구를 제거**: 배포 지점에는 HTTP 리디렉션 또는 IIS 관리 스크립트 및 도구가 필요하지 않습니다. 공격의 여지를 줄이려면 웹 서버(IIS) 역할에 대한 이러한 역할 서비스를 제거하세요.  배포 지점의 웹 서버(IIS) 역할용 역할 서비스에 대한 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.  

**패키지를 만들 때 패키지 액세스 권한을 설정**: 패키지 파일의 액세스 계정을 변경하면 패키지를 재배포할 때만 적용되므로 패키지 액세스 권한은 패키지를 처음 만들 때 신중하게 설정하세요. 패키지가 크거나 많은 배포 지점에 배포된 경우 그리고 콘텐츠 배포를 위한 네트워크 대역폭 용량이 제한된 경우에 특히 중요합니다.  

**사전 준비된 콘텐츠는 압축될 뿐 암호화되지는 않음**: 사전 준비된 콘텐츠는 압축될 뿐 암호화되지는 않습니다. 공격자가 파일을 읽고 수정할 수 있으며, 이러한 파일이 장치에 다운로드될 수 있습니다. Configuration Manager 클라이언트는 변조된 콘텐츠를 거부하지만 다운로드는 계속합니다.  

**사전 준비된 콘텐츠를 가져올 때는 Configuration Manager에서 제공하는 ExtractContent 명령줄 도구(ExtractContent.exe)만 사용하고 Microsoft에서 서명했는지 확인**: 변조 및 권한 상승을 방지하려면 Configuration Manager에서 제공하는 승인된 명령줄 도구만 사용하세요.  

**사이트 서버와 패키지 원본 위치 간 통신 채널의 보안 유지**: 응용 프로그램 및 패키지를 만들 때 사이트 서버와 패키지 원본 위치 간에 IPsec 또는 SMB 서명을 사용하세요. 그러면 공격자가 원본 파일을 변조하지 못합니다.  

**배포 지점 역할이 설치된 후 기본 웹 사이트가 아니라 사용자 지정 웹 사이트를 사용하도록 사이트 구성 옵션을 변경한 경우 기본 가상 디렉터리를 제거**: 기본 웹 사이트에서 사용자 지정 웹 사이트로 전환하는 경우 Configuration Manager는 기존 가상 디렉터리를 제거하지 않습니다. Configuration Manager에서 원래 기본 웹 사이트 아래에 만들었던 가상 디렉터리를 제거하세요.  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**클라우드 기반 배포 지점의 경우 구독 세부 정보와 인증서 보호**: 클라우드 기반 배포 지점을 사용하면 Azure 구독의 사용자 이름 및 암호, Azure 관리 인증서, 클라우드 기반 배포 지점 서비스 인증서 등 중요한 항목을 보호합니다. 인증서를 안전하게 저장하고 클라우드 기반 배포 지점을 구성할 때 네트워크를 통해 찾는 경우 사이트 시스템 서버와 원본 위치 간에 IPsec 또는 SMB 서명을 사용합니다.  

**클라우드 기반 배포 지점: 서비스를 계속 사용할 수 있도록 인증서 만료 날짜 모니터링**: Configuration Manager에서는 클라우드 기반 배포 지점 서비스의 관리를 위해 가져온 인증서의 만료일이 다가와도 경고하지 않습니다. Configuration Manager와 별도로 만료 날짜를 모니터링하고 갱신한 다음 만료 날짜 전에 새 인증서를 가져와야 합니다. 외부 CA(인증 기관)에서 Configuration Manager 클라우드 기반 배포 지점 서비스 인증서를 구입한 경우에는 갱신된 인증서를 받는 데 시간이 더 필요할 수 있으므로 특히 중요합니다.  

 인증서가 만료되면 Cloud Services Manager에서 상태 메시지 ID **9425**를 생성하고 CloudMgr.log 파일에 인증서가 **만료됨 상태**임을 나타내는 항목이 포함되며 만료 날짜도 UTC로 기록됩니다.  

## <a name="security-considerations-for-content-management"></a>콘텐츠 관리에 대한 보안 고려 사항  
콘텐츠 관리를 계획할 때 다음 사항을 고려하세요.  

-   클라이언트에서 콘텐츠가 다운로드될 때까지 유효성 검사를 하지 않습니다.  

     Configuration Manager 클라이언트에서는 해당 클라이언트 캐시에 콘텐츠가 다운로드된 후에만 콘텐츠의 해시에 대한 유효성을 검사합니다. 다운로드할 파일 목록이나 콘텐츠 자체를 공격자가 변조하면 다운로드 프로세스에서 네트워크 대역폭을 많이 사용할 수 있으며, 클라이언트는 잘못된 해시를 발견한 경우에만 콘텐츠를 삭제합니다.  

-   클라우드 기반 배포 지점을 사용하는 경우 콘텐츠에 대한 액세스 권한이 자동으로 해당 기업으로 제한되며, 선택한 사용자나 그룹까지 더 자세히 제한할 수는 없습니다.  

-   클라우드 기반 배포 지점을 사용하는 경우 클라이언트는 관리 지점에서 인증을 받은 다음 Configuration Manager 토큰을 사용하여 클라우드 기반 배포 지점에 액세스합니다. 토큰은 8시간 동안 유효합니다. 즉, 클라이언트를 더 이상 신뢰할 수 없어 차단하면 해당 클라이언트는 이 토큰의 유효 기간이 만료될 때까지 클라우드 기반 배포 지점에서 콘텐츠를 계속 다운로드할 수 있습니다. 이때 클라이언트가 차단되었기 때문에 관리 지점에서 해당 클라이언트에 대해 다른 토큰을 발행하지 않습니다.  

     이 8시간의 기간 내에 차단된 클라이언트가 콘텐츠를 다운로드하지 못하게 하려는 경우 Configuration Manager 콘솔의 **관리** 작업 영역 내 **클라우드** 노드 **계층 구성**에서 클라우드 서비스를 중지할 수 있습니다.  

##  <a name="BKMK_Privacy_ContentManagement"></a> 콘텐츠 관리를 위한 개인 정보  
 Configuration Manager에서는 콘텐츠 파일에 사용자 데이터가 포함되지 않습니다. 관리자가 포함하도록 선택하더라도 포함되지 않습니다.  

 콘텐츠 관리를 구성하기 전에 개인 정보 요구 사항을 고려하세요.  
