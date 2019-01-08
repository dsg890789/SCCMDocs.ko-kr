---
title: 기술 미리 보기 1606의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1606에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 134a2f60-811e-4dc9-a8f5-1ce0018c5c12
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 14e982592491ec5e8a10cd3313f748bddac40cff
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53420077"
---
# <a name="capabilities-in-technical-preview-1606-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1606의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1606에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    

**이 Technical Preview의 알려진 문제:**  
*  Technical Preview 1604에서 1605로 업데이트 후 1606으로 업데이트하는 경우 업데이트가 실패하고 다음과 유사한 오류가 **cmupdate.log**에 기록됩니다.

       ERROR: Failed to execute SQL Server command:  ~ ~-- Create site boundary group ~IF  dbo.fnIsCasOrStandalonePrimary() = 1 ~BEGIN ~   PRINT N'Create site boundary group during upgrade' ~   EXEC dbo.spBuildDefaultBoundaryGroups @UserName = N'SYSTEM' ~END          

    이 경우 **업데이트 및 서비스** 노드에서 **업데이트 확인**을 클릭한 다음 업데이트 설치를 **다시 시도**합니다.
    ***

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="dmp_category"></a> 컬렉션으로 디바이스 자동 분류
Microsoft Intune에서 Configuration Manager를 사용하는 경우 디바이스 컬렉션에 디바이스를 자동으로 배치하는 데 사용할 수 있는 디바이스 범주를 만들 수 있습니다. 그런 다음 사용자는 Intune에 디바이스를 등록할 때 디바이스 범주를 선택해야 합니다. 또한 Configuration Manager 콘솔에서 디바이스의 범주를 변경할 수 있습니다.

**중요:** 이 기능은 Microsoft Intune의 **2016년 6월** 릴리스에 작동합니다. 이러한 절차를 시도하기 전에 이 릴리스로 업데이트했는지 확인합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

### <a name="create-a-set-of-device-categories"></a>디바이스 범주 집합 만들기
1.  Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **개요**를 확장한 다음 **디바이스 컬렉션**을 클릭합니다.
2.  **홈** 탭의 **범주** 그룹에서 **디바이스 범주 관리**를 클릭합니다.
3.  **디바이스 범주 관리** 대화 상자에서 범주를 만들거나 편집하거나 제거할 수 있습니다. 새 범주를 만들어 보세요.

### <a name="associate-a-collection-with-a-device-category"></a>컬렉션을 디바이스 범주에 연결
컬렉션을 디바이스 범주에 연결하면 지정하는 범주의 모든 디바이스가 해당 컬렉션에 추가됩니다.
1.  디바이스 컬렉션의 **속성** 대화 상자에서 **규칙 추가** > **디바이스 범주 규칙**을 클릭합니다.
2.  **디바이스 범주 멤버 관리 규칙 만들기** 대화 상자에서 컬렉션의 모든 디바이스에 적용될 범주를 선택합니다.
3.  **디바이스 범주 멤버 관리 규칙 만들기** 대화 상자와 컬렉션 속성 대화 상자를 닫습니다.

### <a name="change-the-category-of-a-device"></a>디바이스의 범주 변경
1.  Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **개요**를 확장한 다음 **디바이스**를 클릭합니다.
2.  **디바이스** 목록에서 디바이스를 선택한 다음 **홈** 탭의 **디바이스** 그룹에서 **범주 변경**을 클릭합니다.
3.  **디바이스 범주 편집** 대화 상자에서 이 디바이스에 적용할 범주를 선택한 다음 **확인**을 클릭합니다.

## <a name="dmp_grace"></a> 필수 애플리케이션 및 소프트웨어 업데이트 배포를 위한 유예 기간 적용

간혹 구성한 마감일 이후에도 필수 애플리케이션 배포 또는 소프트웨어 업데이트를 설치할 수 있는 시간을 사용자에게 더 제공하고 싶을 경우가 있습니다. 컴퓨터가 오랫동안 꺼져 있었거나 많은 애플리케이션 또는 업데이트 배포를 설치해야 할 때 이런 경우가 필요할 수 있습니다.
예를 들어 최종 사용자가 휴가에서 막 돌아온 경우 지연된 애플리케이션 배포를 설치하는 데 너무 오래 기다려야 할 수 있습니다.
이 문제를 해결하기 위해 이제 컬렉션에 Configuration Manager 클라이언트 설정을 배포하여 유예 기간 적용을 정의할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

유예 기간을 구성하려면 다음 작업을 수행합니다.

1.  클라이언트 설정의 **컴퓨터 에이전트** 페이지에서 새 속성, **배포 최종 기한 이후 적용 유예 기간(시간)** 을 **1**시간에서 **120**시간 사이의 값으로 구성합니다.
2.  새 필수 애플리케이션 배포 또는 기존 배포 속성의 **일정** 페이지에서 클라이언트 설정에 정의된 유예 기간까지 **이 배포의 적용을 사용자 기본 설정에 따라 연기** 확인란을 선택합니다.
이 확인란이 선택되고 클라이언트 설정도 배포된 대상 디바이스의 모든 배포에서 유예 기간 적용을 사용합니다.

유예 기간 적용을 구성하고 확인란을 선택하면 애플리케이션 설치 마감일에 도달한 후 사용자가 해당 유예 기간에 구성한 첫 번째 업무 외 시간에서 애플리케이션이 설치됩니다. 하지만 여전히 사용자가 소프트웨어 센터를 열고 언제든지 원하는 애플리케이션을 설치할 수 있습니다. 유예 기간이 만료되면 지연 배포에 대한 일반적인 동작이 적용됩니다.
소프트웨어 업데이트 배포 마법사, 자동 배포 규칙 마법사 및 속성 페이지에 비슷한 옵션이 추가되었습니다.

##  <a name="dmp_devg"></a> Device Guard로 Configuration Manager를 관리되는 설치 프로그램으로 사용

Device Guard는 하드웨어 및 소프트웨어 기능을 사용하여 디바이스에서 실행이 허용되는 사항을 엄격하게 제어하는 Windows 10 기능입니다.

Device Guard의 수행 작업 및 작동 방법의 자세한 개요는 [이 Technet 문서](https://technet.microsoft.com/itpro/windows/whats-new/device-guard-overview)에서 확인할 수 있습니다.

이 릴리스에서 Configuration Manager는 Device Guard 및 [Windows AppLocker](https://technet.microsoft.com/library/dd723678(v=ws.10).aspx)와 상호 운용할 수 있으므로 Configuration Manager와 함께 배포되는, 관리되는 설치 프로그램의 실행 파일 및 DLL 파일은 자동으로 신뢰할 수 있습니다. 즉, 대상 디바이스에서 실행이 허용됨을 뜻하며 다른 소프트웨어는 다른 AppLocker 규칙에 의해 명시적으로 실행이 허용되지 않는 한 실행할 수 없습니다.  

현재 이 기능은 Configuration Manager 콘솔에서 구성할 수 없습니다. 정책을 구성하려면 각 클라이언트에서 레지스트리 키를 구성하고 클라이언트에서 Windows 서비스를 구성해야 합니다.
이 작업이 완료되면 AppLocker 정책 파일을 구성합니다. 정책 파일을 구성한 후 호환 가능한 클라이언트 디바이스에 배포할 수 있습니다.


모든 AppLocker 정책과 마찬가지로 관리되는 설치 프로그램 규칙이 포함된 정책은 두 가지 모드에서 실행할 수 있습니다.

- 감사 모드 – 애플리케이션의 실행이 차단되지 않았지만 차단되었을 수 있는 모든 애플리케이션이 로그 파일에 보고됩니다(이 기능은 Configuration Manager의 이후 릴리스에서 지원됨).
- 적용 사용 – 애플리케이션 실행이 차단됩니다.

Configuration Manager에서 Device Guard를 사용하는 방법에 대한 추가 정보는 [Enterprise Mobility 및 보안 블로그](https://blogs.technet.microsoft.com/enterprisemobility/2016/06/20/configmgr-as-a-managed-installer-with-win10)에서 확인할 수 있습니다.

추가 참고 자료:

- [Device Guard 소개](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Device Guard 인증 및 규정 준수](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-certification-and-compliance)
- [Device Guard 배포 가이드](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)

  ##  <a name="dmp_onprem"></a> 온-프레미스 모바일 디바이스 관리에 대한 여러 디바이스 관리 지점  
  Technical Preview 1606에서 온\-프레미스 MDM(모바일 디바이스 관리)은 둘 이상의 디바이스 관리 지점을 사용할 수 있도록 등록된 디바이스를 자동으로 구성하는 Windows 10 1주년 업데이트의 새로운 기능을 지원합니다. 이 기능을 통해 디바이스는 사용 중인 디바이스 관리 지점을 사용할 수 없게 되면 다른 디바이스 관리 지점으로 대체할 수 있습니다. 이 기능은 Windows 10 1주년 업데이트가 설치된 PC에서만 작동합니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  

1.  계층에 둘 이상의 디바이스 관리 지점을 설치합니다.  

2.  온\-프레미스 모바일 디바이스 관리를 위한 Windows 10 1주년 업데이트 디바이스를 등록합니다.  

사이트 준비 방법 및 온\-프레미스 모바일 디바이스 관리를 위한 디바이스 등록 방법은 [System Center Configuration Manager의 온-프레미스 인프라로 모바일 디바이스 관리](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md)를 참조하세요.  

## <a name="cloud_proxy"></a>인터넷상의 클라이언트를 관리하기 위한 클라우드 프록시 서비스

클라우드 프록시 서비스는 인터넷에서 Configuration Manager 클라이언트를 관리할 수 있는 간단한 방법을 제공합니다. Microsoft Azure에 배포되고 Azure 구독이 필요한 서비스는 클라우드 프록시 연결점이라는 새 역할을 사용하여 온-프레미스 Configuration Manager 인프라에 연결합니다. 완전히 배포되고 구성된 클라이언트는 내부 개인 네트워크 또는 인터넷에 연결되었는지 여부에 관계없이 온-프레미스 Configuration Manager 사이트 시스템 역할에 액세스할 수 있습니다.

Configuration Manager 콘솔을 사용하여 Azure에 서비스를 배포하고 클라우드 프록시 연결점 역할을 추가하고 클라우드 프록시 트래픽을 허용하도록 사이트 시스템 역할을 구성합니다. 클라우드 프록시 서비스는 현재 관리 지점, 배포 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.

컴퓨터를 인증하고 서비스의 다른 계층 간 통신을 암호화하려면 클라이언트 인증서 및 SSL(Secure Socket Layer) 인증서가 필요합니다. 클라이언트 컴퓨터는 일반적으로 그룹 정책 적용을 통해 클라이언트 인증서를 받습니다. 역할을 호스트하는 사이트 시스템 서버와 클라이언트 간의 트래픽을 암호화하려면 CA에서 사용자 지정 SSL 인증서를 만들어야 합니다. 이러한 두 가지 종류의 인증서 외에 Configuration Manager에서 클라우드 프록시 서비스를 배포할 수 있도록 Azure에 관리 인증서도 설정해야 합니다.  

### <a name="requirements-for-cloud-proxy-service-in-tp-1606"></a>TP 1606의 클라우드 프록시 서비스 요구 사항
- 클라이언트 컴퓨터 및 클라우드 프록시 연결점을 실행하는 사이트 시스템 서버
- 클라이언트 컴퓨터에서 통신 암호화 및 클라우드 프록시 서비스의 ID 인증에 사용되는 내부 CA의 사용자 지정 SSL 인증서
- 클라우드 서비스에 대한 Azure 구독
- Azure에서 Configuration Manager 인증에 사용되는 Azure 관리 인증서

### <a name="limitations-of-cloud-proxy-service-in-tp-1606"></a>TP 1606의 클라우드 프록시 서비스 제한 사항

- 관리 지점, 배포 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.
- 사용자 정책이 지원되지 않습니다.
- Configuration Manager에서 [온-프레미스 모바일 디바이스 관리](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md)와 함께 사용할 수 없습니다.
- Azure의 공용 클라우드 플랫폼에만 지원됩니다.


### <a name="try-it-out"></a>기능 직접 사용해 보기

클라우드 프록시 서비스 배포 프로세스에는 다음 단계가 포함됩니다.

1. 클라우드 프록시 서비스에 대한 사용자 지정 SSL 인증서를 만들고 발급합니다.
1. 클라이언트 인증서의 루트를 내보냅니다.
2. Azure에 관리 인증서를 업로드합니다.
3. Configuration Manager 콘솔에서 클라우드 프록시 서비스를 설정합니다.
4. 클라이언트 인증서 인증을 사용하도록 기본 사이트를 구성합니다.
5. 사이트에 클라우드 프록시 연결점을 추가합니다.
6. 클라우드 프록시 트래픽을 허용하도록 사이트 시스템 역할을 구성합니다.

다음 섹션에서는 이러한 단계를 완료하기 위한 자세한 정보를 제공합니다.

#### <a name="create-a-custom-ssl-certificate"></a>사용자 지정 SSL 인증서 만들기

클라우드 기반 배포 지점에 대해 수행하는 방법과 동일하게 클라우드 프록시 서비스에 대해 사용자 지정 SSL 인증서를 만들 수 있습니다. [클라우드 기반 배포 지점용 서비스 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012)에 대한 지침을 따르되 다음 사항은 다르게 수행합니다.

* 새 인증서 템플릿 설정 시 Configuration Manager 서버에 대해 설정한 보안 그룹에 **읽기** 및 **등록** 권한을 부여합니다.

#### <a name="export-the-client-certificates-root"></a>클라이언트 인증서의 루트 내보내기

네트워크에서 사용되는 클라이언트 인증서의 루트를 내보내는 가장 쉬운 방법은 도메인에 가입된 컴퓨터 중 인증서가 있는 컴퓨터에서 클라이언트 인증서를 열어 해당 인증서를 복사하는 것입니다.

>[!NOTE]
>클라우드 프록시 서비스와 클라우드 프록시 연결점을 호스트하는 사이트 시스템 서버에서 관리하려는 모든 컴퓨터에 클라이언트 인증서가 필요합니다. 이러한 컴퓨터 중 하나에 클라이언트 인증서를 추가해야 하는 경우 [Windows 컴퓨터용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012)를 참조하세요.

1. 실행 창에 **mmc**를 입력하고 Return 키를 누릅니다.
2. 관리 콘솔의 파일 메뉴에서 **스냅인 추가/제거...** 를 클릭합니다.
3. 스냅인 추가 또는 제거 대화 상자에서 **인증서**, **추가 >**, **컴퓨터 계정**, **다음**, **로컬 컴퓨터**를 차례로 클릭한 다음 **마침**을 클릭합니다. **확인** 을 클릭하여 대화 상자를 닫습니다.
4. **인증서 > 개인 > 인증서**로 이동합니다.
5. 컴퓨터에서 클라이언트 인증에 사용할 인증서를 두 번 클릭하고 인증 경로 탭을 클릭하여 루트 인증 기관(경로 상단에 있음)을 두 번 클릭합니다.
6.  세부 정보 탭을 클릭하고 **파일에 복사...** 를 클릭합니다.
7. 기본 인증서 형식을 사용하여 인증서 내보내기 마법사를 완료합니다. 만든 루트 인증서의 이름과 위치를 적어 둡니다. 이후 단계에서 클라우드 프록시 서비스를 구성하는 데 필요합니다.

#### <a name="upload-the-management-certificate-to-azure"></a>Azure에 관리 인증서 업로드

Azure 관리 인증서는 Configuration Manager에서 Azure API에 액세스하고 클라우드 프록시 서비스를 구성하는 데 필요합니다. 관리 인증서를 업로드하는 방법에 대한 자세한 내용 및 지침은 Azure 설명서에서 다음 문서를 참조하세요.
- [Azure Cloud Services 인증서 개요](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)
- [Azure 관리 API Management 인증서 업로드](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

관리 인증서와 연결된 구독 ID를 복사해야 합니다. Configuration Manager 콘솔에서 클라우드 프록시 서비스를 구성하는 데 필요합니다.

#### <a name="set-up-cloud-proxy-service"></a>클라우드 프록시 서비스 설정

1. Configuration Manager 콘솔에서 **관리 > 클라우드 서비스 > 클라우드 프록시 서비스**로 이동합니다.
2. **클라우드 프록시 서비스 만들기**를 클릭합니다.
3. 클라우드 프록시 서비스 만들기 마법사에서 Azure 구독 ID(Azure 관리 포털에서 복사함)를 입력하고, 찾아보기를 클릭하고, Azure 관리 인증서로 업로드하는 데 사용한 인증서 파일을 선택합니다. **다음**을 클릭합니다. 콘솔이 Azure에 연결하는 동안 잠시 기다립니다.
4. 마법사에서 추가 세부 정보를 입력합니다.
    - 사용자 지정 SSL 인증서에서 내보낸 개인 키(.pfx 파일)를 지정합니다.
    - 클라이언트 인증서에서 내보낸 루트 인증서를 지정합니다.
    - 새 인증서 템플릿을 만들 때 사용한 동일한 서비스 이름 FQDN을 지정합니다.
    - CRL 정보를 공개적으로 게시할 경우를 제외하고는 **클라이언트 인증서 해지 확인** 옆의 확인란의 선택을 해제합니다.
    - 완료한 경우 **다음**을 클릭합니다.
5. 설정을 확인하고 **다음**을 클릭합니다. Configuration Manager가 서비스 설정을 시작합니다. 마법사가 완료되면 **닫기**를 클릭할 수 있지만 Azure에서 서비스를 완전히 프로비전하려면 5~15분 정도 걸립니다. 클라우드 프록시 서비스를 새로 설정하기 위해 **상태** 열을 확인하여 서비스가 준비되는 시점을 확인합니다.

#### <a name="configure-primary-site-for-client-certification-authentication"></a>클라이언트 인증서 인증에 대한 기본 사이트를 구성합니다.

1. Configuration Manager 콘솔에서 **관리 > 사이트 구성 > 사이트**로 이동합니다.
2. 클라우드 프록시 서비스를 통해 관리하려는 클라이언트에 대한 기본 사이트를 선택하고 **속성**을 클릭합니다.
3. 기본 사이트 속성 시트의 클라이언트 컴퓨터 통신 탭에서 **사용 가능한 경우 PKI 클라이언트 인증서(클라이언트 인증) 사용** 옆의 확인란을 선택합니다.
4. **클라이언트에서 사이트 시스템에 대한 CRL(인증서 해지 목록) 확인** 옆에 있는 확인란의 선택을 해제해야 합니다. CRL을 공개적으로 게시하는 경우에만 이 옵션이 필요합니다.
5. **확인**을 클릭합니다.

#### <a name="add-the-cloud-proxy-connector-point"></a>클라우드 프록시 연결점 추가

클라우드 프록시 연결점은 클라우드 프록시 서비스와 통신하기 위한 새 사이트 시스템 역할입니다. 클라우드 프록시 연결점을 추가하려면 [System Center Configuration Manager에 대한 사이트 시스템 역할 추가](../../core/servers/deploy/configure/add-site-system-roles.md)의 지침을 따릅니다.

#### <a name="configure-roles-for-cloud-proxy-traffic"></a>클라우드 프록시 트래픽에 대한 역할 구성

클라우드 프록시 서비스 설정의 마지막 단계는 클라우드 프록시 트래픽을 허용하도록 사이트 시스템 역할을 구성하는 것입니다. Tech Preview 1606의 경우 클라우드 프록시 서비스에 대해 관리 지점, 배포 지점 및 소프트웨어 업데이트 지점 역할만 지원됩니다. 각 역할을 별도로 구성해야 합니다.

1. Configuration Manager 콘솔에서 **관리 > 사이트 구성 > 서버 및 사이트 시스템 역할**로 이동합니다.
2. 클라우드 프록시 트래픽에 대해 구성하려는 역할에 대한 사이트 시스템 서버를 클릭합니다.
3. 역할을 클릭한 다음 **속성**을 클릭합니다.
4. 역할 속성 시트의 클라이언트 연결에서 **HTTPS**를 선택하고 **Configuration Manager 클라우드 프록시 트래픽 허용** 옆의 확인란을 선택한 다음 **확인**을 클릭합니다. 나머지 역할에 대해 이 단계를 반복합니다.

#### <a name="check-status-on-a-client-on-the-internet"></a>인터넷상의 클라이언트 상태를 확인합니다.

서비스 및 역할이 완전히 구성된 후 내부 클라이언트는 다음 위치 요청에 대한 클라우드 프록시 서비스의 위치를 가져옵니다. 업데이트된 위치 정보가 있는 클라이언트는 인터넷상의 Configuration Manager와 통신할 수 있습니다. 위치 요청에 대한 폴링 주기는 매 24시간입니다. 정상적으로 예약된 위치 요청을 기다리고 싶지 않으면 컴퓨터에서 SMS 에이전트 호스트 서비스(ccmexec.exe)를 다시 시작하여 요청을 강제로 실시할 수 있습니다.

클라이언트에서 클라우드 프록시 서비스에 대한 새 위치 정보를 얻은 다음 더 이상 내부 개인 네트워크상에는 없지만 인터넷에 액세스된 클라이언트의 상태를 확인합니다. **관리 > 클라우드 서비스 > 클라우드 프록시 서비스**로 이동하고, 목록 창에서 서비스를 선택하고, 세부 정보 창에서 트래픽 정보를 확인하여 클라우드 프록시 서비스의 트래픽을 모니터링할 수도 있습니다.   

## <a name="manage_o365"></a>Configuration Manager에서 Office 365 클라이언트 에이전트 관리  

Technical Preview 1606부터 Configuration Manager 클라이언트 에이전트 설정을 사용하여 그룹 정책 대신 Office 365 클라이언트가 Configuration Manager의 업데이트를 받을 수 있도록 합니다. 이 설정을 구성하고 Office 365 업데이트를 배포한 후 Configuration Manager 클라이언트 에이전트는 Office 365 클라이언트 에이전트와 통신하여 배포 지점에서 Office 365 업데이트를 다운로드하고 설치합니다. Configuration Manager는 또한 클라이언트 에이전트 설정의 인벤토리를 사용합니다.

자세한 내용은 [Manage Office 365 ProPlus updates](https://technet.microsoft.com/library/mt741983.aspx)(Office 365 ProPlus 업데이트 관리)를 참조하세요.

### <a name="set-the-configuration-manager-client-setting-to-manage-the-office-365-client-agent"></a>Office 365 클라이언트 에이전트를 관리하려면 Configuration Manager 클라이언트 설정을 지정합니다.
1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 클릭합니다.
2. 적절한 디바이스 설정을 열어 클라이언트 에이전트를 사용하도록 설정합니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.
3. **소프트웨어 업데이트**를 클릭하고 **Office 365 클라이언트 에이전트 관리 사용** 설정에 대해 **예**를 선택합니다.  


## <a name="osdpreservedriveletter"></a>OSDPreserveDriveLetter 작업 순서 변수는 사용되지 않음
SDPreserveDriveLetter 작업 순서 변수는 작업 순서에서 운영 체제 이미지를 대상 컴퓨터에 적용할 때 해당 이미지의 WIM 파일에서 캡처된 드라이브 문자를 사용할지 결정합니다.
- Technical Preview 1606에서는 이 작업 순서 변수가 사용되지 않았습니다.

기본적으로 운영 체제 배포 시 Windows 설치 프로그램이 이제 사용하기에 가장 적합한 드라이브 문자(일반적으로 C:)를 결정합니다. 다른 드라이브를 사용하도록 지정하려면 운영 체제 적용 작업 순서 단계에서 위치를 변경할 수 있습니다. **이 운영 체제를 적용할 위치를 선택하십시오.** 설정으로 이동하여 **특정 논리 드라이브 문자**를 선택하고 사용하려는 드라이브를 선택합니다. 대상 컴퓨터에서 선택한 문자로 할당된 드라이브여야 합니다. 

## <a name="updatesandservicing"></a>업데이트 및 서비스 노드의 변경 내용
Technical Preview 1606에서는 Configuration Manager 콘솔에서 업데이트 및 서비스에 적용되는 몇 가지 변경 사항이 도입되었습니다.
- **노드 이름 변경:**

    **모니터링** 작업 영역에서 **사이트 서비스 상태** 노드의 이름이 **업데이트 및 서비스 상태**로 변경되었습니다.
- **자세한 설치 상태:**

    이제 사이트에 대한 업데이트 설치 상태를 볼 때 콘솔에 다음 작업에 대한 별도 세부 정보가 표시됩니다.
    - **다운로드**(서비스 연결 지점 사이트 시스템 역할이 설치되어 있는 최상위 계층 사이트에만 적용됨)
    - **복제**
    - **필수 구성 요소 확인**
    - **설치**

  또한 추가 정보를 볼 수 있는 로그 파일을 포함하여 이제 각 단계에 대한 더 자세한 정보를 볼 수 있습니다.  
-   **필수 조건 실패 시 다시 시도하는 새 옵션:**

    **관리** 및 **모니터링** 작업 영역 둘 다에서 **업데이트 및 서비스** 노드에 **필수 조건 경고 무시**라는 리본 단추가 포함됩니다.

    예를 들어 필수 조건 경고를 무시하는 옵션을 사용하지 않고 업데이트를 설치하는 경우(업데이트 마법사 내에서) 해당 업데이트 설치가 **필수 조건 경고** 상태로 중단되면 리본에서 **필수 조건 경고 무시**를 선택할 수 있습니다. 그러면 해당 업데이트 설치의 자동 진행을 트리거한 후 필수 조건 경고를 무시합니다.  



- **업데이트의 명확한 정보:**

    **업데이트 및 서비스** 노드를 볼 때 이제 가장 최근에 설치된 업데이트와 설치 가능한 새 업데이트를 볼 수 있습니다. 이전에 설치된 업데이트를 보려면 리본에 새로 표시된 **기록** 단추를 클릭합니다.  

-   **이름이 변경된 사전 프로덕션 옵션:**

    업데이트 및 서비스 노드에서 **클라이언트 옵션**이라는 이름의 단추가 이제 **사전 프로덕션 클라이언트 수준 올리기**로 변경되었습니다.
