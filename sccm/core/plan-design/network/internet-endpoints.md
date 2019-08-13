---
title: 인터넷 액세스 요구 사항
titleSuffix: Configuration Manager
description: Configuration Manager의 기능이 완벽히 작동하는 데 필요한 인터넷 엔드포인트에 대해 알아봅니다.
ms.date: 08/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: b34fe701-5d05-42be-b965-e3dccc9363ca
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fa7ab85d86a544b3ea0ad22325ddd63e2034982e
ms.sourcegitcommit: c60fdfb9df107c430389b69b08f9670ce5f526c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68860052"
---
# <a name="internet-access-requirements"></a>인터넷 액세스 요구 사항

일부 Configuration Manager 기능이 완벽히 작동하기 위해서는 인터넷 연결이 필요합니다. 조직에서 방화벽 또는 프록시 디바이스를 사용하여 인터넷과의 네트워크 통신을 제한하는 경우 이러한 엔드포인트를 허용해야 합니다.

<!-- SCCMDocs-pr #3403 -->

## <a name="bkmk_scp"></a> 서비스 연결 지점

이러한 구성은 서비스 연결 지점을 호스트하는 컴퓨터 및 해당 컴퓨터와 인터넷 간의 모든 방화벽에 적용됩니다. 둘 다 나가는 포트 **TCP 443**(HTTPS의 경우) 및 나가는 포트 **TCP 80**(HTTP)을 통한 아래 인터넷 위치와의 통신을 허용해야 합니다.

서비스 연결 지점에서는 웹 프록시(인증을 사용하거나 사용하지 않고)를 사용하여 이러한 위치에 액세스할 수 있습니다. 자세한 내용은 [프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support)을 참조하세요.

서비스 연결 지점에 대한 자세한 내용은 [서비스 연결 지점 정보](/sccm/core/servers/deploy/configure/about-the-service-connection-point)를 참조하세요.

> [!TIP]  
> 서비스 연결 지점이 `go.microsoft.com` 또는 `manage.microsoft.com`에 연결된 경우 Microsoft Intune 서비스를 사용합니다. Baltimore CyberTrust 루트 인증서가 설치되지 않았거나 만료되었거나 서비스 연결 지점에서 손상된 경우, Intune 커넥터에 연결 문제가 발생하는 것으로 알려진 문제가 있습니다. 자세한 내용은 [KB 3187516: Service connection point doesn't download updates](https://support.microsoft.com/help/3187516)(KB 3187516: 서비스 연결 지점에서 업데이트를 다운로드하지 않습니다)를 참조하세요.  

### <a name="a-namebkmk_scp-updates-updates-and-servicing"></a><a name="bkmk_scp-updates"/> 업데이트 및 서비스

이 기능에 대한 자세한 내용은 [Configuration Manager에 대한 업데이트 및 서비스](/sccm/core/servers/manage/updates)를 참조하세요.

> [!Tip]  
> [관리 인사이트](/sccm/core/servers/manage/management-insights) 규칙, **Configuration Manager 업데이트를 위해 사이트를 Microsoft 클라우드에 연결**에 대해 이러한 엔드포인트를 사용하도록 설정합니다.

- `*.akamaiedge.net`  

- `*.akamaitechnologies.com`  

- `*.manage.microsoft.com`  

- `go.microsoft.com`  

- `*.blob.core.windows.net`  

- `download.microsoft.com`  

- `download.windowsupdate.com`  

- `sccmconnected-a01.cloudapp.net`  

- `configmgrbits.azureedge.net`  

### <a name="microsoft-intune"></a>Microsoft Intune

자세한 내용은 [Hybrid MDM with Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management)(Configuration Manager 및 Microsoft Intune에서 하이브리드 MDM)을 참조하세요.

- `*manage.microsoft.com`  

- `https://bspmts.mp.microsoft.com/V`  

- `https://login.microsoftonline.com/{TenantID}`  

### <a name="windows-10-servicing"></a>Windows 10 서비스

이 기능에 대한 자세한 내용은 [Manage Windows as a service](/sccm/osd/deploy-use/manage-windows-as-a-service)(Windows as a Service 관리)를 참조하세요.

- `download.microsoft.com`  

- `https://go.microsoft.com/fwlink/?LinkID=619849`  

- `dl.delivery.mp.microsoft.com`  

### <a name="azure-services"></a>Azure 서비스

이 기능에 대한 자세한 내용은 [Configuration Manager에서 사용하도록 Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요.

- `management.azure.com`  


## <a name="co-management"></a>공동 관리

공동 관리를 위해 Microsoft Intune에 Windows 10 디바이스를 등록하는 경우 이러한 디바이스에서 Intune에 필요한 엔드포인트에 액세스할 수 있는지 확인하세요. 자세한 내용은 [Microsoft Intune에 대한 네트워크 엔드포인트](https://docs.microsoft.com/intune/intune-endpoints)를 참조하세요.


## <a name="bkmk_cloud"></a> Cloud Services

<!-- SCCMDocs-pr #3402 -->

이 섹션에서는 다음 기능을 다룹니다.

- CMG(클라우드 관리 게이트웨이)
- CDP(클라우드 배포 지점)
- Azure AD(Azure Active Directory) 통합
- Azure AD 기반 검색

CMG/CDP 서비스 배포를 위해서는 **서비스 연결 지점**에서 다음에 액세스해야 합니다.

- 특정 Azure 엔드포인트는 환경 및 구성에 따라 다릅니다. Configuration Manager는 이러한 엔드포인트를 사이트 데이터베이스에 저장합니다. SQL Server의 **AzureEnvironments** 테이블에서 Azure 엔드포인트 목록을 쿼리합니다.  

**CMG 연결 지점**에서 다음 서비스 엔드포인트에 액세스해야 합니다.

- ServiceManagementEndpoint: `https://management.core.windows.net/`  

- StorageEndpoint: `blob.core.windows.net` 및 `table.core.windows.net`

**Configuration Manager 콘솔** 및 **클라이언트**에서 Azure AD 토큰 검색:

- ActiveDirectoryEndpoint `https://login.microsoftonline.com/`  

Azure AD 사용자 검색을 위해서는 **서비스 연결 지점**에서 다음에 액세스해야 합니다.

- 1810 이전 버전 Azure AD Graph 엔드포인트 `https://graph.windows.net/`  

- 1902 이상 버전: Microsoft Graph 엔드포인트 `https://graph.microsoft.com/`

CMG(클라우드 관리 지점) 연결 지점 사이트 시스템은 웹 프록시 사용을 지원합니다. 프록시에 대해 이 역할을 구성하는 방법에 대한 자세한 내용은 [프록시 서버 지원](proxy-server-support.md#configure-the-proxy-for-a-site-system-server)을 참조하세요. CMG 연결 지점은 CMG 서비스 엔드포인트에만 연결하면 됩니다. 다른 Azure 엔드포인트에는 액세스할 필요가 없습니다.

CMG에 대한 자세한 내용은 [CMG 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.


## <a name="bkmk_sum"></a> 소프트웨어 업데이트

WSUS 및 자동 업데이트에서 Microsoft Update 클라우드 서비스와 통신할 수 있도록 활성 소프트웨어 업데이트 지점에서 다음 엔드포인트에 액세스하도록 허용합니다.  

- `http://windowsupdate.microsoft.com`  

- `http://*.windowsupdate.microsoft.com`  

- `https://*.windowsupdate.microsoft.com`  

- `http://*.update.microsoft.com`  

- `https://*.update.microsoft.com`  

- `http://*.windowsupdate.com`  

- `http://download.windowsupdate.com`  

- `http://download.microsoft.com`  

- `http://*.download.windowsupdate.com`  

- `http://test.stats.update.microsoft.com`  

- `http://ntservicepack.microsoft.com`  

소프트웨어 업데이트에 대한 자세한 내용은 [소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates)을 참조하세요.

### <a name="intranet-firewall"></a>인트라넷 방화벽

다음과 같은 경우 두 사이트 시스템 간에 있는 방화벽에 엔드포인트를 추가해야 할 수 있습니다.

- 자식 사이트에 소프트웨어 업데이트 지점이 있는 경우
- 사이트에 원격 활성 인터넷 기반 소프트웨어 업데이트 지점이 있는 경우

#### <a name="software-update-point-on-the-child-site"></a>자식 사이트의 소프트웨어 업데이트 지점

- `http://<FQDN for software update point on child site>`  

- `https://<FQDN for software update point on child site>`  

- `http://<FQDN for software update point on parent site>`  

- `https://<FQDN for software update point on parent site>`  


## <a name="manage-office-365"></a>Office 365 관리

Configuration Manager를 사용하여 Office 365를 배포 및 업데이트하는 경우 다음 끝점을 허용합니다.

<!-- SCCMDocs#929 -->

- `officecdn.microsoft.com` - Office 365 클라이언트 업데이트를 위해 소프트웨어 업데이트 지점 동기화

- `config.office.com` - Office 365 배포를 위한 사용자 지정 구성 만들기


## <a name="configuration-manager-console"></a>Configuration Manager 콘솔

Configuration Manager 콘솔을 사용하는 컴퓨터에서는 특정 기능을 사용하기 위해 다음 인터넷 엔드포인트에 액세스해야 합니다.

### <a name="in-console-feedback"></a>콘솔 내 피드백

- `http://petrol.office.microsoft.com`

이 기능에 대한 자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#product-feedback)을 참조하세요.

### <a name="community-workspace-documentation-node"></a>커뮤니티 작업 영역, 설명서 노드

- `https://aka.ms`

- `https://raw.githubusercontent.com`

이 콘솔 노드에 대한 자세한 내용은 [Configuration Manager 콘솔 사용](/sccm/core/servers/manage/admin-console)을 참조하세요.

<!-- 
Community Hub
when in current branch, get details from SCCMDocs-pr #3403 
 -->

### <a name="monitoring-workspace-site-hierarchy-node"></a>모니터링 작업 영역, 사이트 계층 노드

**지리적 보기**를 사용하는 경우 다음 엔드포인트에 대한 액세스를 허용합니다.

- `http://maps.bing.com`


## <a name="desktop-analytics"></a>Desktop Analytics

Desktop Analytics 클라우드 서비스에 필요한 엔드포인트에 대한 자세한 내용은 [Enable data sharing](/sccm/desktop-analytics/enable-data-sharing#endpoints)(데이터 공유 사용)을 참조하세요.


## <a name="microsoft-public-ip-addresses"></a>Microsoft는 공용 IP 주소

Microsoft IP 주소 범위에 대한 자세한 내용은 [Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602)(Microsoft 공용 IP 공간)를 참조하세요. 이러한 주소는 정기적으로 업데이트됩니다. 서비스별로 세분화되어 있지 않고, 이러한 범위의 모든 IP 주소가 사용될 수 있습니다.


## <a name="see-also"></a>참고 항목

- [Configuration Manager에서 사용되는 포트](/sccm/core/plan-design/hierarchy/ports)

- [Configuration Manager의 프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support)
