---
title: "인터넷에서 클라이언트 설치 및 할당 | Microsoft Docs"
description: "인터넷에서 System Center Configuration Manager 클라이언트를 설치 및 할당합니다."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a44006eb-8650-49f6-94e1-18fa0ca959ee
caps.latest.revision: 14
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: HT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: f604557d208b2dda9dc1c6b4c4d27d896d47695e
ms.contentlocale: ko-kr
ms.lasthandoff: 07/29/2017

---

# <a name="install-and-assign-configuration-manager-clients-from-the-internet-using-azure-ad-for-authentication"></a>인증을 위해 Azure AD를 사용하여 인터넷에서 Configuration Manager 클라이언트 설치 및 할당

Azure AD에서 Configuration Manager 클라우드 서비스를 사용하여 다음 시나리오를 지원할 수 있습니다.

- 인터넷에서 수동으로 Configuration Manager 클라이언트를 설치하고 Configuration Manager 사이트에 할당합니다(클라우드 관리 게이트웨이 사이트 시스템 역할 필요).
- Configuration Manager 사이트에 액세스하려면 Azure AD를 사용하여 인터넷에서 클라이언트를 인증합니다. Azure AD를 사용하면 클라이언트 인증 인증서를 구성하고 사용할 필요가 없습니다.
- 컬렉션 및 기타 Configuration Manager 작업에서 사용하기 위해 사이트로 Azure AD 사용자를 검색합니다.

다음 단계를 사용하여 이 작업을 수행할 수 있습니다.

- **1단계: 클라우드 관리 게이트웨이 설정**
- **2단계: Configuration Manager 클라우드 서비스에서 Azure 서비스 앱 설정**
- **3단계: Azure AD에서 Windows 10 장치를 등록하도록 클라이언트 설정 구성**
- **4단계: Azure Active Directory ID를 사용하여 Configuration Manager 클라이언트 설치 및 등록**


## <a name="before-you-start"></a>시작하기 전에

- Azure AD 테넌트가 있어야 합니다.
- 장치는 Windows 10을 실행해야 하고 Azure AD에 가입되어야 합니다. 클라이언트는 Azure AD에 가입될 수 있을 뿐만 아니라 도메인에도 가입될 수 있습니다.
- 관리 지점 사이트 시스템 역할에 대한 [기존 필수 구성 요소](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) 외에, 이 사이트 시스템 역할을 호스트하는 컴퓨터에서 **ASP.NET 4.5**(및 자동으로 선택되는 기타 옵션)가 사용되도록 설정되어 있는지도 확인해야 합니다.
- Configuration Manager를 클라이언트를 배포하려면
    - HTTPS 모드에 대해 하나 이상의 관리 지점을 구성합니다.
    - 클라우드 관리 게이트웨이를 설정합니다.

## <a name="step-1-set-up-the-cloud-management-gateway"></a>1단계: 클라우드 관리 게이트웨이 설정

클라이언트가 인증서를 사용하지 않고 인터넷에서 Configuration Manager 사이트에 액세스할 수 있도록 클라우드 관리 게이트웨이를 설정합니다. 다음 항목에서 도움말을 찾습니다. 

- [Configuration Manager에서 클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/plan-cloud-management-gateway)
- [Configuration Manager용 클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/setup-cloud-management-gateway)
- [Configuration Manager에서 클라우드 관리 게이트웨이 모니터링](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway)

## <a name="step-2-set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>2단계: Configuration Manager 클라우드 서비스에서 Azure 서비스 앱 설정

이렇게 하면 Configuration Manager 사이트가 Azure AD에 연결되므로 이 섹션의 다른 모든 작업을 위해 반드시 필요합니다. 

Azure AD 사용자 검색은 *클라우드 관리*의 일부로 구성됩니다. 이렇게 하기 위한 절차는 *Configuration Manager에서 사용하도록 Azure 서비스 구성* 항목의 [Configuration Manager에서 사용하기 위해 Azure Web App 만들기](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) 절차 **6**단계에 자세히 나와 있습니다.
    
이 절차를 완료하면 Configuration Manager 사이트가 Azure AD에 연결되었을 것입니다. 

## <a name="step-3-configure-client-settings-to-register-windows-10-devices-with-azure-ad"></a>3단계: Azure AD에서 Windows 10 장치를 등록하도록 클라이언트 설정 구성

1.  [클라이언트 설정 구성 방법](/sccm/core/clients/deploy/configure-client-settings)의 정보를 사용하여 다음 클라이언트 설정(클라우드 서비스에 있음) 섹션을 구성합니다.
    - **Azure Active Directory에 새 Windows 10 도메인에 연결된 장치를 자동으로 등록** – **예**(기본값) 또는 **아니요**로 설정합니다.
    - **클라이언트가 클라우드 관리 게이트웨이를 사용하도록 설정** – **예**(기본값) 또는 **아니요**로 설정합니다.
2.  필요한 장치 컬렉션에 클라이언트 설정을 배포합니다.

장치가 Azure AD에 연결되어 있는지 확인하려면 명령 프롬프트 창에서 명령 **dsregcmd.exe /status**를 실행합니다. 결과의 **AzureAdjoined** 필드는 장치가 Azure AD에 연결된 경우 **예**를 표시합니다.


## <a name="step-4-install-and-register-the-configuration-manager-client-using-azure-active-directory-identity"></a>4단계: Azure Active Directory ID를 사용하여 Configuration Manager 클라이언트 설치 및 등록

시작 하기 전에 클라이언트를 설치하려는 장치에 클라이언트 설치 원본 파일이 로컬로 저장되어 있는지 확인합니다. 그런 다음 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually)의 지침에 따라 다음 설치 명령줄을 사용합니다. 

**ccmsetup.exe /NoCrlCheck /Source:C:\CLIENT CCMHOSTNAME=SCCMPROXYCONTOSO.CLOUDAPP.NET/CCM_Proxy_ServerAuth/72457598037527932 SMSSiteCode=HEC AADTENANTID=780433B5-E05E-4B7D-BFD1-E8013911E543 AADTENANTNAME=contoso AADCLIENTAPPID= AADRESOURCEURI=https://contososerver**

- **/NoCrlCheck:** 관리 지점 또는 클라우드 관리 게이트웨이에서 비공용 서버 인증서를 사용하는 경우 클라이언트는 CRL 위치를 연결하지 못할 수 있습니다.
- **/Source:** Local folder: 클라이언트 설치 파일의 위치입니다.
- **CCMHOSTNAME:** 인터넷 관리 지점의 이름입니다. 관리되는 클라이언트의 명령 프롬프트에서 **gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate**를 실행하여 이 이름을 찾을 수 있습니다.
- **SMSMP:** 조회 관리 지점의 이름입니다. 관리 지점은 인트라넷에 있을 수 있습니다.
- **SMSSiteCode:** Configuration Manager 사이트의 사이트 코드입니다.
- **AADTENANTID:**, **AADTENANTNAME:** Configuration Manager에 연결된 Azure AD 테넌트의 ID 및 이름입니다. Azure AD에 가입된 장치의 명령 프롬프트에서 dsregcmd.exe /status를 실행하여 찾을 수 있습니다.
- **AADCLIENTAPPID:** Azure AD 클라이언트 앱 ID입니다. 이를 찾으려면 [포털을 사용하여 리소스에 액세스할 수 있는 Azure Active Directory 응용 프로그램 및 서비스 사용자 만들기](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key)를 참조하세요.
- **AADResourceUri:** 등록된 Azure AD 서버 앱의 식별자 URI입니다.


## <a name="next-steps"></a>다음 단계

완료되면 [클라이언트를 계속 모니터링 및 관리](/sccm/core/clients/manage/monitor-clients)할 수 있습니다.

