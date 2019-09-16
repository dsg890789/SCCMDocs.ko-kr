---
title: 앱에 대한 보안 및 개인정보보호
titleSuffix: Configuration Manager
description: Configuration Manager에서 애플리케이션을 관리할 때 보안 및 개인정보보호 대한 지침과 권장 사항입니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6fd16ce6094d9ed25f496995f1efdaff6a8d674
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68535320"
---
# <a name="security-and-privacy-for-application-management-in-configuration-manager"></a>Configuration Manager의 애플리케이션 관리를 위한 보안 및 개인정보보호

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="security-guidance-for-application-management"></a>애플리케이션 관리의 보안 가이드  

### <a name="use-the-software-center-without-the-application-catalog"></a>애플리케이션 카탈로그 없이 소프트웨어 센터 사용

<!--1358309-->

응용 프로그램 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806에서 지원 되지 않습니다. 이 구성은 사용자에게 애플리케이션을 전달하기 위해 필요한 서버 인프라를 줄일 수 있습니다.

버전 1906부터 업데이트 된 클라이언트에서 사용자가 사용할 수 있는 응용 프로그램 배포에 대 한 관리 지점을 자동으로 사용 합니다. 또한 새 응용 프로그램 카탈로그 역할을 설치할 수 없습니다. 2019년 10월 31일 이후 첫 번째 현재 분기 릴리스에서는 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다. 서버 인프라를 줄이면 공격 노출도 줄어듭니다.

인터넷 기반 클라이언트에 대한 지속적이고 안전한 애플리케이션 환경을 제공하려면 Azure Active Directory와 클라우드 관리 게이트웨이를 사용합니다.

자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)을 참조하세요.

### <a name="use-https-with-the-application-catalog"></a>애플리케이션 카탈로그에서 HTTPS 사용

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

HTTPS 연결을 수락하도록 애플리케이션 카탈로그 웹 사이트 지점과 애플리케이션 카탈로그 웹 서비스 지점을 구성합니다. 이 구성을 사용하면 서버가 사용자에게 인증됩니다. 전송된 데이터는 변조 및 보기에서 보호됩니다.

사용자에게 신뢰할 수 있는 웹 사이트에만 연결하도록 주지시켜 소셜 엔지니어링 공격을 방지합니다. 사용자에게 악성 웹 사이트의 위험에 관해 설명합니다.

HTTPS를 사용하지 않는 경우에 브랜딩 구성 옵션을 사용하지 않습니다. 이러한 설정은 ID 증명으로 애플리케이션 카탈로그에서 조직 이름을 보여 줍니다.  


### <a name="use-role-separation"></a>역할 구분 사용

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

별도의 서버에 애플리케이션 카탈로그 웹 사이트 지점 및 애플리케이션 카탈로그 웹 서비스 지점을 설치합니다. 웹 사이트 지점이 손상 된 경우 웹 서비스 지점과는 별개입니다. 이 설계는 구성 관리자 클라이언트 및 인프라를 보호하는 데 도움이 됩니다. 특히 웹 사이트 지점이 인터넷에서 클라이언트 연결을 수락하는 경우 이 구성이 매우 중요합니다. 서버가 공격에 취약해질 수 있습니다.  

### <a name="close-browser-windows"></a>브라우저 창 닫기

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

사용자가 애플리케이션 카탈로그 사용을 마칠 때 브라우저를 닫도록 일러 줍니다. 애플리케이션 카탈로그를 위해 사용하던 브라우저 창에서 외부 웹 사이트를 탐색할 경우 브라우저에서 인트라넷의 신뢰할 수 있는 사이트에 적합한 보안 설정을 계속 사용합니다.  

### <a name="centrally-specify-user-device-affinity"></a>중앙에서 사용자 디바이스 선호도 지정

사용자에게 기본 디바이스를 식별할 수 있도록 허용하는 대신 사용자 디바이스 선호도를 수동으로 지정합니다. 사용량 기준 구성은 사용하도록 설정하지 마세요.

사용자나 디바이스에서 수집되는 정보를 신뢰할 수 있는 정보로 간주해서는 안 됩니다. 신뢰할 수 있는 관리자가 지정하지 않은 사용자 디바이스 선호도를 사용하여 소프트웨어를 배포할 경우 해당 소프트웨어를 받을 권한이 없는 사용자에게 컴퓨터에 소프트웨어가 설치될 수 있습니다.  

### <a name="dont-run-deployments-from-distribution-points"></a>배포 지점에서 배포를 실행하지 않음

콘텐츠를 배포 지점에서 실행하지 않고 배포 지점에서 다운로드하도록 배포를 구성합니다. 콘텐츠를 배포 지점에서 다운로드하여 로컬로 실행하도록 배포를 구성하면 Configuration Manager 클라이언트가 콘텐츠를 다운로드한 후에 패키지 해시를 확인합니다. 클라이언트는 해당 해시가 정책에 있는 해시와 일치하지 않을 경우 패키지를 삭제합니다.

배포 지점에서 직접 콘텐츠를 실행하도록 배포를 구성할 경우 구성 관리자 클라이언트가 패키지 해시를 확인하지 않습니다. 이 동작은 구성 관리자 클라이언트가 변조된 소프트웨어를 설치할 가능성이 있다는 것을 의미합니다.

배포 지점에서 바로 배포를 실행해야 하는 경우 배포 지점의 패키지에서 NTFS 최소 권한을 사용합니다. 또한 IPsec(인터넷 프로토콜 보안)을 사용하여 클라이언트와 배포 지점 사이, 그리고 배포 지점과 사이트 서버 사이의 채널을 보호합니다.

### <a name="bkmk_interact"></a> 사용자가 관리자 권한 프로세스와 상호 작용하지 못하게 하세요.
  
**관리 권한으로 실행** 또는 **시스템용 설치** 옵션을 사용하도록 설정한 경우 사용자가 애플리케이션과 상호 작용하지 못하게 하세요. 애플리케이션을 구성할 때 **사용자가 프로그램 설치를 보고 사용할 수 있음** 옵션을 설정할 수 있습니다. 이 설정을 사용하면 사용자가 사용자 인터페이스에서 필요한 프롬프트에 응답할 수 있습니다. 또한 **관리 권한으로 실행**되도록 또는 1802 이상 버전에서 **시스템용으로 설치**되도록 애플리케이션을 구성하는 경우 해당 프로그램이 실행되는 컴퓨터에 침입한 공격자가 사용자 인터페이스를 사용하여 클라이언트 컴퓨터에서 권한을 승격시킬 수 있게 됩니다.

관리 자격 증명이 필요한 소프트웨어 배포의 경우에는 설치용 Windows Installer 및 사용자별 상승된 권한을 사용하는 프로그램을 사용하세요. 설치 프로그램은 관리 자격 증명이 없는 사용자의 컨텍스트에서 실행해야 합니다. Windows Installer의 사용자별 상승된 권한을 사용하면 관리자 자격 증명을 요구하는 애플리케이션을 가장 안전하게 배포할 수 있습니다.

### <a name="restrict-whether-users-can-install-software-interactively"></a>사용자가 소프트웨어를 대화형으로 설치할 수 있는지 여부를 제한합니다.

**컴퓨터 에이전트** 그룹에 **설치 권한** 클라이언트 설정을 구성합니다. 이 설정은 소프트웨어 센터에서 소프트웨어를 설치할 수 있는 사용자 유형을 제한 합니다.

예를 들어 **설치 권한** 을 **관리자만**으로 설정하여 사용자 지정 클라이언트 설정을 만듭니다. 서버 컬렉션에 이 클라이언트 설정을 적용합니다. 이 구성은 관리 권한이 없는 사용자가 해당 서버에 소프트웨어를 설치하지 못하도록 합니다.  

### <a name="for-mobile-devices-deploy-only-applications-that-are-signed"></a>모바일 디바이스의 경우 서명된 애플리케이션만 배포합니다.

모바일 디바이스 애플리케이션은 해당 모바일 디바이스가 신뢰하는 CA(인증 기관)에서 코드에 서명한 경우에만 배포합니다.

예:

- VeriSign과 같은 잘 알려진 CA에서 서명한 공급업체의 애플리케이션  

- 내부 CA를 사용하여 Configuration Manager와 별개로 서명한 내부 애플리케이션  

- 애플리케이션 유형을 만들 때 Configuration Manager를 사용하여 서명했고 서명 인증서를 사용하는 내부 애플리케이션

### <a name="secure-the-location-of-the-mobile-device-application-signing-certificate"></a>모바일 디바이스 애플리케이션 서명 인증서의 위치 보안

Configuration Manager에서 **애플리케이션 만들기 마법사**를 사용하여 모바일 디바이스 애플리케이션에 서명한 경우 서명 인증서 파일 위치와 통신 채널을 보호해야 합니다. 권한 승격과 메시지 가로채기(man-in-the-middle) 공격을 방지하려면 서명 인증서 파일을 보안 폴더에 저장합니다.

다음 컴퓨터 간에 IPsec을 사용합니다.

- Configuration Manager 콘솔을 실행하는 컴퓨터
- 인증서 서명 파일이 저장된 컴퓨터
- 애플리케이션 원본 파일이 저장된 컴퓨터

또는 **애플리케이션 만들기 마법사**를 실행하기 전에 Configuration Manager와 별개로 애플리케이션에 서명합니다.

### <a name="implement-access-controls"></a>액세스 제어 구현

참조 컴퓨터를 보호하려면 액세스 제어를 구현합니다. 참조 컴퓨터를 찾아 배포 유형에 검색 방법을 구성하는 경우 해당 컴퓨터가 손상되지 않았는지 확인해야 합니다.

### <a name="restrict-and-monitor-administrative-users"></a>관리자를 제한하고 모니터합니다.

다음과 같은 애플리케이션 관리 역할 기반 보안 역할이 부여된 관리자를 제한하고 모니터링합니다.

- **애플리케이션 관리자**
- **애플리케이션 작성자**
- **애플리케이션 배포 관리자**

역할 기반 관리를 구성하는 경우에도 애플리케이션을 만들고 배포하는 관리자는 생각보다 많은 권한을 가질 수 있습니다. 예를 들어 애플리케이션을 만들거나 수정하는 관리자는 해당 보안 범위에 없는 종속된 애플리케이션을 선택할 수 있습니다.

### <a name="configure-app-v-apps-in-virtual-environments-with-the-same-trust-level"></a>동일한 신뢰 수준을 가진 가상 환경에서 App-V 앱 구성

Microsoft App-V(Application Virtualization) 가상 환경을 구성하는 경우 가상 환경에서 동일한 신뢰 수준을 갖는 애플리케이션을 선택합니다. App-V 가상 환경의 애플리케이션은 클립보드와 같은 리소스를 공유할 수 있기 때문에 선택한 애플리케이션들이 동일한 신뢰 수준을 갖도록 가상 환경을 구성해야 합니다.

자세한 내용은 [App-V 가상 환경 만들기](/sccm/apps/deploy-use/create-app-v-virtual-environments)를 참조하세요.

### <a name="make-sure-macos-apps-are-from-a-trustworthy-source"></a>macOS 앱이 신뢰할 수 있는 원본에서 제공되었는지 확인

macOS 디바이스용 애플리케이션을 배포하는 경우 원본 파일이 신뢰할 수 있는 원본으로 만들어졌는지 확인해야 합니다. CMAppUtil 도구는 원본 패키지 서명의 유효성을 검사하지 않습니다. 패키지가 신뢰하는 원본에서 제공되었는지 확인하세요. CMAppUtil 도구는 파일이 변조되었는지 여부를 검색할 수 없습니다.

### <a name="secure-the-cmmac-file-for-macos-apps"></a>macOS 앱용 cmmac 파일 보호

MacOS 컴퓨터용 애플리케이션을 배포하는 경우 **.cmmac** 파일 위치를 보호합니다. CMAppUtil 도구에서 이 파일을 생성하면 Configuration Manager로 가져옵니다. 이 파일은 서명되거나 유효성을 검사하지 않았습니다.

Configuration Manager에 이 파일을 가져올 때 통신 채널을 보호합니다. 이 파일을 변조를 방지하려면 보안 폴더에 저장합니다. 다음 컴퓨터 간에 IPsec을 사용합니다.

- Configuration Manager 콘솔을 실행하는 컴퓨터  
- **.cmmac** 파일을 저장하는 컴퓨터  

### <a name="use-https-for-web-applications"></a>웹 애플리케이션용 HTTPS 사용

웹 애플리케이션 배포 유형을 구성하는 경우 연결을 보호하기 위해 HTTPS를 사용합니다. HTTPS 링크가 아니라 HTTP 링크를 사용하여 웹 애플리케이션을 배포하면 디바이스가 Rogue 서버로 리디렉션될 수 있습니다. 디바이스와 서버 간에 전송되는 데이터가 변조될 수 있습니다.


## <a name="security-issues-for-application-management"></a>애플리케이션 관리의 보안 문제  

- 낮은 권한을 가진 사용자가 클라이언트 컴퓨터에 있는 클라이언트 캐시에서 파일을 복사할 수 있습니다.  

     사용자는 클라이언트 캐시를 읽을 수 있지만 캐시에 쓸 수는 없습니다. 사용자에게 읽기 권한이 있으면 컴퓨터 간에 애플리케이션 설치 파일을 복사할 수 있습니다.  

- 낮은 권한을 가진 사용자가 클라이언트 컴퓨터의 소프트웨어 배포를 기록하는 파일을 변경할 수 있습니다.  

     애플리케이션 기록 정보는 보호되지 않으므로 사용자는 애플리케이션 설치 여부를 보고하는 파일을 변경할 수 있습니다.  

- App-V 패키지는 서명되지 않았습니다.  

     Configuration Manager의 App-V 패키지는 서명을 지원하지 않습니다. 디지털 서명은 콘텐츠의 출처를 신뢰할 수 있는지, 콘텐츠가 전송 중에 변경되지 않았는지 확인합니다. 이 보안 문제를 완화하는 방법은 없습니다. 보안 모범 사례를 따라 신뢰할 수 있는 원본과 보안 위치에서 콘텐츠를 다운로드해야 합니다.  

- 게시된 App-V 애플리케이션을 컴퓨터의 모든 사용자가 설치할 수 있습니다.  

     App-V 애플리케이션이 컴퓨터에 게시되면 해당 컴퓨터에 로그인하는 모든 사용자가 이 애플리케이션을 설치할 수 있습니다. 애플리케이션이 게시된 후에는 애플리케이션을 설치할 수 있는 사용자를 제한할 수 없습니다.  

- 모바일 디바이스에서 회사 포털에 대한 설치 권한을 제한할 수 없습니다.  

     설치 권한을 제한하도록 클라이언트 설정을 구성할 수 있지만, 회사 포털에는 이 설정이 적용되지 않습니다. 이 문제는 권한 상승으로 이어질 수 있습니다. 사용자가 설치가 허용되지 않는 앱을 설치할 수 있습니다.  


## <a name="BKMK_CertificatesSilverlight5"></a> 애플리케이션 카탈로그에 필요한 높은 권한 모드 및 Microsoft Silverlight 5용 인증서  

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

구성 관리자 클라이언트 버전 1710 이상에는 Microsoft Silverlight 5가 필요하며, 사용자가 애플리케이션 카탈로그에서 소프트웨어를 설치하려면 Microsoft Silverlight 5를 높은 권한 모드로 실행해야 합니다. 기본적으로 Silverlight 애플리케이션은 사용자 데이터에 액세스할 수 없도록 부분 신뢰 모드로 실행됩니다. Configuration Manager는 Microsoft Silverlight 5가 클라이언트에 아직 설치되어 있지 않으면 자동으로 설치합니다. 기본적으로 Configuration Manager는 컴퓨터 에이전트의 **Silverlight 애플리케이션의 높은 권한 모드 실행을 허용합니다.** 클라이언트 설정을 **예**로 설정합니다. 이 설정을 사용하면 서명되고 신뢰할 수 있는 Silverlight 애플리케이션에서 높은 권한 모드를 요청할 수 있게 됩니다.  

애플리케이션 카탈로그 웹 사이트 지점 사이트 시스템 역할을 설치하면 클라이언트에서 각 구성 관리자 클라이언트 컴퓨터의 신뢰할 수 있는 게시자 컴퓨터 인증서 저장소에 Microsoft 서명 인증서를 설치합니다. 이 인증서로 서명된 Silverlight 애플리케이션은 높은 권한 모드로 실행되며, 애플리케이션 카탈로그의 소프트웨어를 설치하려는 컴퓨터에서는 이 모드를 사용해야 합니다. Configuration Manager에서는 이 서명 인증서를 자동으로 관리합니다. 서비스 연속성을 위해 이 Microsoft 서명 인증서를 수동으로 삭제하거나 이동하지 마세요.  

> [!WARNING]  
> **Silverlight 애플리케이션의 높은 권한 모드 실행을 허용합니다.** 클라이언트 설정을 사용하도록 설정하는 경우 컴퓨터 저장소 또는 사용자 저장소의 신뢰할 수 있는 게시자 인증서 저장소에 있는 인증서로 서명된 모든 Silverlight 애플리케이션을 높은 권한 모드에서 실행할 수 있습니다. 이 클라이언트 설정으로는 Configuration Manager 애플리케이션 카탈로그 또는 컴퓨터 저장소의 신뢰할 수 있는 게시자 인증서 저장소에 대해서만 높은 권한 모드로 애플리케이션을 실행할 수 없습니다. 맬웨어가 신뢰할 수 있는 게시자 저장소에 Rogue 인증서를 추가할 경우 맬웨어가 자체 Silverlight 애플리케이션을 사용하여 높은 권한 모드로 실행될 수 있습니다.  

**Silverlight 애플리케이션의 높은 권한 모드 실행을 허용합니다.** 설정을 **아니요**로 설정해도 클라이언트에서 Microsoft 서명 인증서가 삭제되지 않습니다.  

Silverlight의 신뢰할 수 있는 애플리케이션에 대한 자세한 내용은 [신뢰할 수 있는 애플리케이션](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/ee721083\(v=vs.95\))을 참조하세요.  


## <a name="privacy-information-for-application-management"></a>애플리케이션 관리의 개인 정보 보호  

애플리케이션 관리를 사용하면 계층의 모든 클라이언트에서 애플리케이션, 프로그램 또는 스크립트를 실행할 수 있습니다. Configuration Manager에서는 사용자가 실행하는 애플리케이션, 프로그램 또는 스크립트의 유형이나 이러한 애플리케이션, 프로그램 또는 스크립트에서 전송하는 정보의 유형을 제어하지 않습니다. 애플리케이션 배포 과정에서 Configuration Manager는 클라이언트와 서버 간에 디바이스 및 로그인 계정을 식별하는 정보를 전송할 수 있습니다.  

Configuration Manager에는 소프트웨어 배포 프로세스에 대한 상태 정보가 유지됩니다. 소프트웨어 배포 상태 정보는 클라이언트가 HTTPS를 사용하여 통신할 때를 제외하고 암호화되지 않습니다. 상태 정보는 데이터베이스에 암호화된 형식으로 저장되지 않습니다.  

Configuration Manager 애플리케이션 설치를 사용하여 클라이언트에 소프트웨어를 원격으로, 대화형으로 또는 자동으로 설치하는 경우 해당 소프트웨어의 소프트웨어 사용 조건이 적용될 수 있습니다. 이 소프트웨어 사용 시에는 System Center Configuration Manager의 소프트웨어 사용 조건과는 별도의 사용 조건이 적용됩니다. Configuration Manager를 사용하여 소프트웨어를 배포하기 전에는 항상 소프트웨어 사용 조건을 검토하고 동의해야 합니다.  

Configuration Manager에서는 진단 및 사용량 데이터를 수집하며, 이러한 데이터는 Microsoft에서 향후 버전을 개선하기 위해 사용됩니다. 자세한 내용은 [진단 및 사용량 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.

애플리케이션 배포는 기본적으로 이루어지지 않으며 여러 구성 단계가 필요합니다.  

다음 기능은 효율적인 소프트웨어 배포를 돕습니다.

- **사용자 디바이스 선호도**는 사용자를 디바이스에 매핑합니다. Configuration Manager 관리자는 소프트웨어를 사용자에게 배포합니다. 클라이언트는 사용자가 가장 자주 사용하는 하나 이상의 컴퓨터에 소프트웨어를 자동으로 설치합니다.  

- **소프트웨어 센터**는 구성 관리자 클라이언트를 설치할 때 디바이스에 자동으로 설치됩니다. 사용자가 설정을 변경 하 고 소프트웨어 센터에서 소프트웨어를 찾아 설치 합니다.  

- **애플리케이션 카탈로그**는 사용자가 소프트웨어를 설치하도록 요청할 수 있는 웹 사이트입니다.  

    > [!Important]  
    > 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

### <a name="bkmk_privacy-uda"></a>사용자 장치 선호도 개인 정보

- Configuration Manager는 클라이언트 및 관리 지점 사이트 시스템 간에 정보를 전송할 수 있습니다. 이 정보를 통해 컴퓨터와 로그인 계정 및 로그인 계정의 요약된 사용량을 식별할 수 있습니다.  

- 클라이언트가 HTTPS를 사용하여 통신해야 하도록 관리 지점을 구성하지 않는 한, 클라이언트 및 서버 간에 전송되는 정보는 암호화되지 않습니다.  

- 사용자를 디바이스에 매핑하는 데 사용하는 컴퓨터 및 로그인 계정 사용량 정보는 클라이언트 컴퓨터에 저장되고, 관리 지점으로 전송된 후 Configuration Manager 데이터베이스에 저장됩니다. 오래된 정보는 기본적으로 90일 이후에 데이터베이스에서 삭제됩니다. 삭제 동작은 **오래된 사용자 디바이스 선호도 데이터 삭제** 사이트 유지 관리 작업을 설정하여 구성할 수 있습니다.  

- Configuration Manager는 사용자 디바이스 선호도에 대한 상태 정보를 유지 관리합니다. HTTPS를 사용하여 통신하도록 관리 지점의 클라이언트를 구성하지 않는 한, 상태 정보는 전송 도중 암호화되지 않습니다. 상태 정보는 데이터베이스에 암호화된 형식으로 저장되지 않습니다.  

- 사용자 및 디바이스 선호도를 설정하는 데 사용하는 컴퓨터 및 로그인 사용량 정보는 항상 사용하도록 설정되어 있습니다. 사용자 및 관리자가 사용자 디바이스 선호도 정보를 제공할 수도 있습니다.  

### <a name="bkmk_privacy-userex"></a>소프트웨어 센터 개인 정보

- Configuration Manager 관리자는 소프트웨어 센터를 통해 사용자가 실행할 수 있도록 애플리케이션, 프로그램 또는 스크립트를 게시할 수 있습니다. Configuration Manager에서는 카탈로그에 게시되는 프로그램 또는 스크립트의 유형이나 이러한 프로그램 또는 스크립트에서 전송하는 정보의 유형을 제어하지 않습니다.  

- Configuration Manager는 클라이언트 및 관리 지점 간에 정보를 전송할 수 있습니다. 이 정보를 통해 컴퓨터 및 로그인 계정을 식별할 수 있습니다. HTTPS를 사용하여 클라이언트를 연결하도록 관리 지점을 구성하지 않는 한, 클라이언트 및 서버 간에 전송되는 정보는 암호화되지 않습니다.  

- 애플리케이션 승인 요청에 대한 정보는 Configuration Manager 데이터베이스에 저장됩니다. 취소 또는 거부된 요청과 해당 요청 기록 항목은 기본적으로 30일 후에 삭제됩니다. 삭제 동작은 **오래된 애플리케이션 요청 데이터 삭제** 사이트 유지 관리 작업을 설정하여 구성할 수 있습니다. 상태가 승인됨 및 보류 중인 애플리케이션 승인 요청은 삭제되지 않습니다.  

- 소프트웨어 센터는 디바이스에서 Configuration Manager 클라이언트를 설치할 때 자동으로 설치됩니다.  

### <a name="application-catalog-privacy-information"></a>응용 프로그램 카탈로그 개인 정보

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.  

- 애플리케이션 카탈로그는 기본적으로 설치되지 않습니다. 이를 설치하려면 몇 가지 구성 단계가 필요합니다.  

- Configuration Manager 관리자는 애플리케이션 카탈로그를 통해 사용자가 실행할 수 있도록 애플리케이션, 프로그램 또는 스크립트를 게시할 수 있습니다. Configuration Manager에서는 카탈로그에 게시되는 프로그램 또는 스크립트의 유형이나 이러한 프로그램 또는 스크립트에서 전송하는 정보의 유형을 제어하지 않습니다.  

- Configuration Manager는 클라이언트 및 애플리케이션 카탈로그 사이트 시스템 역할 간에 정보를 전송할 수 있습니다. 이 정보를 통해 컴퓨터 및 로그인 계정을 식별할 수 있습니다. HTTPS를 사용하여 클라이언트를 연결하도록 이러한 사이트 시스템 역할을 구성하지 않는 한, 클라이언트 및 서버 간에 전송되는 정보는 암호화되지 않습니다.  
