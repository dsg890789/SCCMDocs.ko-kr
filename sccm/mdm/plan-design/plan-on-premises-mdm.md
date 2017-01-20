---
title: "온-프레미스 MDM 계획 | Microsoft 문서"
description: "System Center Configuration Manager에서 모바일 장치를 관리하기 위해 온-프레미스 모바일 장치 관리를 계획합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 0d6479bcc134103e6005159a8ea295a5f359a436
ms.openlocfilehash: cc5b04dc41b13993fca35f202437b71e96bc9cdd


---
# <a name="plan-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 장치 관리에 대한 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

온\-프레미스 모바일 장치 관리를 처리하기 위해 Configuration Manager 인프라를 준비하기 전에 다음과 같은 요구 사항을 고려하세요.

##  <a name="a-namebkmkdevicesa-supported-devices"></a><a name="bkmk_devices"></a> 지원되는 장치  
 온-프레미스 모바일 장치 관리에서 장치 운영 체제에 기본 제공된 관리 기능을 사용하여 모바일 장치를 관리할 수 있습니다.  관리 기능은 OMA(Open Mobile Alliance) DM(장치 관리) 표준을 기준으로 하며 많은 장치 플랫폼은 이 표준을 사용하여 장치를 관리할 수 있도록 합니다.  Configuration Manager 클라이언트에서 관리하도록 요구하는 다른 장치와 구분하기 위해 이러한 장치를 **최신 장치**(설명서 및 Configuration Manager 콘솔 사용자 인터페이스에서)로 지칭합니다.  

 > [!NOTE]  
>  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 장치에 대한 온-프레미스 모바일 장치 관리에서의 등록을 지원합니다.  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team\(Configuration Manager 버전 1602 이상\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise   

##  <a name="a-namebkmkintunea-use-of-the--microsoft-intune-subscription"></a><a name="bkmk_intune"></a> Microsoft Intune 구독의 용도  
 온\-프레미스 모바일 장치 관리를 사용하기 시작하려면 Microsoft Intune을 구독해야 합니다. 구독은 장치 라이선스를 추적하는 데만 필요하며 장치에 대한 관리 정보를 관리하거나 저장하는 데는 사용되지 않습니다. 모든 관리는 온-프레미스 Configuration Manager 인프라를 사용하여 조직의 엔터프라이즈에서 처리됩니다.  

> [!IMPORTANT]  
>  Configuration Manager는 Microsoft Intune과 온-프레미스 Configuration Manager 인프라를 동시에 관리 기관으로 사용할 수 없습니다. 따라서 온-프레미스 관리에 대한 Intune 구독을 설정할 때 Intune 관리를 사용하지 않도록 설정하는 것이 효과적입니다.  

 인터넷에 연결된 장치가 사이트에 있는 경우 Intune 서비스를 사용하여 정책 업데이트에 대한 장치 관리 지점을 확인하도록 장치에 알릴 수 있습니다. 이 Intune의 용도는 인터넷 연결 장치에 대한 알림으로 엄격히 국한됩니다. 인터넷에 연결되지 않은(그리고 Intune에서 연결할 수 없는) 장치는 구성된 폴링 간격에 의존하여 관리 기능에 대한 사이트 시스템 역할을 확인합니다.  

> [!TIP]  
>  필수 사이트 시스템 역할을 설정하기 전에 Intune을 설정하여 사이트 시스템 역할이 작동하는 데 필요한 시간을 최소화하는 것이 좋습니다.  

 Intune 구독 설정 방법에 대한 내용은 [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위해 Microsoft Intune 구독 설정](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)을 참조하세요.  

##  <a name="a-namebkmkrolesa-required-site-system-roles"></a><a name="bkmk_roles"></a> 필수 사이트 시스템 역할  
 온\-프레미스 모바일 장치 관리에는 다음 각 사이트 시스템 역할 중 하나 이상이 필요합니다.  

-   **등록 프록시 지점** : 등록 요청 지원  

-   **등록 지점** : 장치 등록 지원  

-   **장치 관리 지점** : 정책 배달 이 사이트 시스템 역할은 모바일 장치 관리를 허용하도록 구성된 관리 지점 역할이 변형된 것입니다.  

-   **배포 지점** : 콘텐츠 배달용  

-   **서비스 연결 지점** : 방화벽 외부에 장치를 알리기 위해 Intune에 연결  

 조직의 필요에 따라 이러한 사이트 시스템 역할을 단일 사이트 시스템 서버에 설치하거나 서로 다른 서버에 개별적으로 실행할 수 있습니다. 온\-프레미스 모바일 장치 관리에 사용되는 각 사이트 시스템 서버는 신뢰할 수 있는 장치와 통신하기 위한 HTTPS 끝점으로 구성되어야 합니다. 자세한 내용은 [신뢰할 수 있는 필수 통신](#bkmk_trustedComs)항목을 참조하세요.  

 사이트 시스템 역할 계획에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)을 참조하세요.  

 필요한 사이트 시스템 역할을 추가하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 사이트 시스템 역할 설치](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)를 참조하세요.  

##  <a name="a-namebkmktrustedcomsa-required-trusted-communications"></a><a name="bkmk_trustedComs"></a> 신뢰할 수 있는 필수 통신  
 온\-프레미스 모바일 장치 관리에서는 HTTPS 통신을 위해 사이트 시스템 역할이 사용되도록 설정되어야 합니다. 사용자의 필요에 따라 엔터프라이즈 CA(인증 기관)를 사용하여 서버와 장치 간에 신뢰할 수 있는 연결을 설정하거나, 공개적으로 사용 가능한 CA를 사용하여 신뢰할 수 있는 기관이 될 수 있습니다.  어떤 방법을 사용하든 필요한 사이트 시스템 역할을 호스트하는 사이트 시스템 서버에서 IIS를 사용해서 웹 서버 인증서를 구성해야 하며, 해당 서버에 연결해야 하는 장치에 설치된 CA의 루트 인증서가 필요합니다.  

 엔터프라이즈 CA를 사용하여 신뢰할 수 있는 통신을 설정하는 경우 다음 작업을 수행해야 합니다.  

-   CA에서 웹 서버 인증서 템플릿 만들기 및 발급  

-   필요한 사이트 시스템 역할을 호스트하는 각 사이트 시스템 서버에 대한 웹 서버 인증서를 요청합니다.  

-   요청된 웹 서버 인증서를 사용하도록 사이트 시스템 서버의 IIS를 구성합니다.  

 회사 Active Directory 도메인에 가입된 장치의 경우 엔터프라이즈 CA의 루트 인증서가 이미 장치의 신뢰할 수 있는 연결에 사용될 수 있습니다. 즉, 도메인에 가입된 장치(예: 데스크톱 컴퓨터)는 사이트 시스템 서버와의 HTTPS 연결을 위해 자동으로 신뢰됩니다. 그러나 도메인에 가입되지 않은 장치(일반적으로 모바일)에는 필수 루트 인증서가 설치되어 있지 않습니다. 온\-프레미스 모바일 장치 관리를 지원하는 사이트 시스템 서버와 통신하려면 해당 장치에서 루트 인증서를 수동으로 설치해야 합니다.  

 개별 장치에서 사용하기 위해 발급 CA의 루트 인증서를 내보내야 합니다. 루트 인증서 파일을 가져오려는 경우 CA를 사용하여 내보낼 수 있으며, 비슷한 방법으로, CA에서 발급한 웹 서버 인증서를 사용하여 루트를 추출하고 루트 인증서 파일을 만들 수도 있습니다.   그런 다음 장치로 루트 인증서가 배달되어야 합니다.  몇 가지 예제 배달 방법은 다음과 같습니다.  

-   파일 시스템  

-   메일 첨부 파일  

-   메모리 카드  

-   테더링된 장치  

-   클라우드 저장소(예: OneDrive)  

-   NFC(근거리 통신) 연결  

-   바코드 스캐너  

-   OOBE(첫 실행 경험) 프로비저닝 패키지  

 자세한 내용은 [System Center Configuration Manager에서 온-프레미스 모바일 장치 관리를 위해 신뢰할 수 있는 통신에 대한 인증서 설정](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)을 참조하세요.  

##  <a name="a-namebkmkenrollmenta-enrollment-considerations"></a><a name="bkmk_enrollment"></a> 등록 시 고려 사항  
 온\-프레미스 모바일 장치 관리에 대한 장치 등록을 사용하도록 설정하려면 사용자는 등록할 수 있는 권한이 있어야 하고 해당 장치는 필요한 사이트 시스템 역할을 호스트하는 사이트 시스템 서버와 신뢰할 수 있는 통신을 수행할 수 있어야 합니다.  

 사용자에게 등록 권한을 부여하는 작업은 Configuration Manager 클라이언트 설정에서 등록 프로필을 설정하여 수행할 수 있습니다. 기본 클라이언트 설정을 사용하여 검색된 모든 사용자에게 등록 프로필을 푸시하거나 사용자 지정 클라이언트 설정에서 등록 프로필을 설정하고 해당 설정을 하나 이상의 사용자 컬렉션에 푸시할 수 있습니다.  

 사용자 등록 권한이 부여되면 자신의 장치를 등록할 수 있습니다. 등록하려면 사용자 장치에 필요한 사이트 시스템 역할을 호스트하는 사이트 시스템 서버에서 사용되는 웹 서버 인증서를 발급한 CA(인증 기관)의 루트 인증서가 있어야 합니다.  

 사용자가 시작하는 등록 방식 대신, 사용자 개입 없이 장치가 등록되도록 하는 대량 등록 패키지를 설정할 수 있습니다. 이 패키지는 초기에 사용하기 위해 프로비전하거나 장치에서 OOBE 프로세스가 진행된 후에 장치로 전달될 수 있습니다.  

 장치를 설정 및 등록하는 방법에 대한 자세한 내용은 다음을 참조하세요.  

-   [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록 설정](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

-   [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)  



<!--HONumber=Dec16_HO3-->


