---
title: CMG 보안 및 개인 정보
description: 클라우드 관리 게이트웨이에서 보안 및 개인 정보에 대한 지침과 권장 사항을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 7304730b-b517-4c76-aadd-4cbd157dc971
ms.collection: M365-identity-device-management
ms.openlocfilehash: 013d00fd7c207df45b0f6b7910283c3e8b60b44d
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56137173"
---
# <a name="security-and-privacy-for-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 아티클에는 Configuration Manager CMG(클라우드 관리 게이트웨이)에 대한 보안 및 개인 정보가 포함되어 있습니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.

## <a name="cmg-security-details"></a>CMG 보안 세부 정보
- CMG는 CMG 연결점에서 연결을 허용하고 관리합니다. 인증서 및 연결 ID를 사용하여 상호 SSL 인증을 사용합니다.
- CMG는 다음과 같은 방법으로 클라이언트 요청을 허용하고 전달합니다.
    - PKI 기반 클라이언트 인증 인증서 또는 Azure AD와의 상호 SSL을 사용하여 연결을 사전 인증합니다. 
      - CMG VM 인스턴스에서 IIS는 CMG에 업로드된 신뢰할 수 있는 루트 인증서에 따라 인증서 경로를 확인합니다.
      - 또한 VM 인스턴스에서 IIS를 사용하는 경우 클라이언트 인증서 해지를 확인합니다. 자세한 내용은 [인증서 해지 목록 게시](#bkmk_crl)를 참조하세요.
    - 인증서 신뢰 목록은 클라이언트 인증 인증서의 루트를 확인합니다. 또한 클라이언트에 대한 관리 지점의 경우와 동일한 유효성 검사를 수행합니다. 자세한 내용은 [사이트의 인증서 신뢰 목록에서 항목 검토](#bkmk_ctl)를 참조하세요.
    - 클라이언트 요청(URL)의 유효성을 검사하고 필터링하여 CMG 연결점이 요청을 처리할 수 있는지 확인합니다.  
    - 각 게시 엔드포인트의 콘텐츠 길이를 확인합니다.
    - 라운드 로빈 동작을 사용하여 동일한 사이트의 CMG 연결점 간에 부하를 분산합니다.
- CMG 연결점은 다음과 같은 메서드를 사용합니다.
    - CMG의 모든 VM 인스턴스에 대해 일관된 HTTPS/TCP 연결을 빌드합니다. 1분마다 이러한 연결을 확인하고 유지 관리합니다.
    - 인증서를 사용하여 CMG와 상호 SSL 인증을 사용합니다.
    - URL 매핑을 기반으로 클라이언트 요청을 전달합니다.
    - 연결 상태를 보고하여 콘솔에서 서비스 연결 상태를 표시합니다.
    - 5분마다 엔드포인트 당 트래픽을 보고합니다.

### <a name="configuration-manager-client-facing-roles"></a>Configuration Manager 클라이언트 측 역할
관리 지점 및 소프트웨어 업데이트 지점은 서비스 클라이언트 요청에 대한 IIS의 엔드포인트를 호스팅합니다. CMG는 모든 내부 엔드포인트를 노출하지 않습니다. CMG에 게시된 모든 엔드포인트에는 URL 매핑이 있습니다.
  - 외부 URL은 클라이언트에서 CMG와 통신하기 위해 사용합니다.
  - 내부 URL은 내부 서버에 요청을 전달하는 데 사용되는 CMG 연결 지점입니다.

#### <a name="url-mapping-example"></a>URL 매핑 예제
관리 지점에서 CMG 트래픽을 사용하도록 설정하면 Configuration Manager는 각 관리 지점 서버에 대해 내부 URL 매핑 집합을 만듭니다. 예: ccm_system, ccm_incoming 및 sms_mp 관리 지점 ccm_system 엔드포인트에 대한 외부 URL은 다음과 같습니다.  
`https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System`  
URL은 각 관리 지점에 대해 고유합니다. 그런 다음, Configuration Manager 클라이언트는 CMG 사용 관리 지점 이름을 해당 인터넷 관리 지점 목록에 추가합니다. 이 이름은 다음과 같습니다.  
`<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>`  
사이트는 게시된 외부 URL을 모두 CMG에 자동으로 업로드합니다. 이 동작을 통해 CMG가 URL을 필터링할 수 있습니다. 모든 URL 매핑은 CMG 연결점에 복제됩니다. 그런 다음, 클라이언트 요청의 외부 URL에 따라 내부 서버에 대한 통신을 전달합니다.



## <a name="security-guidance-for-cmg"></a>CMG에 대한 보안 가이드


<a name="bkmk_crl"></a>

### <a name="publish-the-certificate-revocation-list"></a>인증서 해지 목록 게시

인터넷 기반 클라이언트가 액세스하려면 PKI CRL(인증서 해지 목록)을 게시합니다. PKI를 사용하여 CMG을 배포하는 경우 설정 탭에서 **클라이언트 인증서 해지를 확인**하도록 서비스를 구성합니다. 이 설정은 게시된 CRL(인증서 해지 목록)을 사용하도록 서비스를 구성합니다. 자세한 내용은 [PKI 인증서 해지 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForCRLs)을 참조하세요.



<a name="bkmk_ctl"></a>

### <a name="review-entries-in-the-sites-certificate-trust-list"></a>사이트의 인증서 신뢰 목록에서 항목 검토
<!--503739--> 각 Configuration Manager 사이트에는 신뢰할 수 있는 루트 인증 기관 목록인 CTL(인증서 신뢰 목록)이 포함됩니다. 관리 작업 영역으로 이동하여 목록을 보고 수정하고, 사이트 구성을 확장하고, 사이트를 선택합니다. 사이트를 선택하고 리본 메뉴에서 속성을 클릭합니다. 클라이언트 컴퓨터 통신 탭으로 전환한 다음, 신뢰할 수 있는 루트 인증 기관에서 **설정**을 클릭합니다.
 
PKI 클라이언트 인증을 사용하여 CMG가 포함된 사이트에 더 제한적인 CTL을 사용합니다. 그렇지 않은 경우, 관리 지점에 이미 존재하는 신뢰할 수 있는 루트에서 발급한 클라이언트 인증 인증서가 포함된 클라이언트는 자동으로 클라이언트 등록에 승인됩니다.

이 하위 집합에서는 보안을 더욱 제어하는 보안 관리자를 제공합니다. CTL은 CTL의 인증 기관에서 발급한 클라이언트 인증서만을 허용하도록 서버를 제한합니다. 예를 들어 Windows는 VeriSign 및 Thawte 등과 같은 여러 유명한 타사 CA(인증 기관)의 인증서와 함께 제공됩니다. 기본적으로 IIS를 실행하는 컴퓨터는 이러한 유명 CA에 연결되는 인증서를 신뢰합니다. CTL을 사용하여 IIS를 구성하지 않으면 이러한 CA에서 발급한 클라이언트 인증서가 있는 컴퓨터는 유효한 Configuration Manager 클라이언트로 승인됩니다. 이러한 CA가 포함되지 않은 CTL을 사용하여 IIS를 구성하면 인증서가 해당 CA에 연결된 경우 클라이언트 연결은 거부됩니다. 


<!--486209-->


<!-- ## Privacy information for CMG -->


## <a name="next-steps"></a>다음 단계

- [클라우드 관리 게이트웨이에 대한 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 FAQ](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
