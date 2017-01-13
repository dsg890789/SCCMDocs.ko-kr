---
title: "System Center Configuration Manager에 대한 장치 관리 솔루션 선택 | Microsoft 문서"
description: "System Center Configuration Manager에서 PC, 서버 및 장치 관리를 위해 제공하는 솔루션에 대해 알아봅니다."
ms.custom: na
ms.date: 12/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: 14
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: d56b2a8090dd798bceda63e29df6c6ff4a4afe4e
ms.openlocfilehash: 792d9b03904193c1c302c2f8373448a44887ed9c


---
# <a name="choose-a-device-management-solution-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 장치 관리 솔루션 선택

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager(ConfgMgr, SCCM이라고도 함)에서는 PC, 서버 및 장치를 관리하기 위한 다양한 솔루션을 제공합니다. 관리해야 하는 장치 플랫폼 및 필요한 관리 기능에 따라 적합한 솔루션을 선택할 수 있습니다.  


##  <a name="overview-of-device-management-solutions"></a>장치 관리 솔루션의 개요  
 이 문서에서는 Configuration Manager 클라이언트 응용 프로그램, 온-프레미스 Configuration Manager 인프라, Microsoft Intune 및 Exchange의 네 가지 장치 관리 솔루션을 다룹니다. 이 문서의 마지막에는 각각 [지원되는 모바일 장치 플랫폼](#compare-device-management-solutions-based-on-supported-mobile-device-platforms)과 [관리 기능](#compare-mobile-device-management-solutions-based-on-management-functionality)을 기준으로 하여 관리 솔루션을 비교하는 2개 표가 나와 있습니다.


###  <a name="manage-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트를 사용하여 장치 관리  

장치에 Configuration Manager 클라이언트 응용 프로그램을 설치해야 하는 이 옵션은 PC, 서버 및 사용자 환경의 기타 장치를 관리하기 위한 기능을 가장 많이 제공합니다. 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 방법](/sccm/core/client/deploy/plan/client-installation-methods)을 참조하세요.  

###  <a name="manage-devices-with-on-premises-configuration-manager-infrastructure"></a>온-프레미스 Configuration Manager 인프라를 사용하여 장치 관리  

이 옵션은 일부 장치 플랫폼의 운영 체제에 기본 제공되는 장치 관리 기능을 사용합니다. 클라이언트 기반 관리만큼 전체 기능을 갖추고 있지는 않지만 온-프레미스 모바일 장치 관리는 온-프레미스 Configuration Manager 리소스를 사용하여 장치에 연결하고 관리하는 보다 가벼운 관리 방식을 제공합니다. 이 옵션은 현재 Windows 10 PC 및 Windows 10 Mobile 장치에 대해서만 지원됩니다.  

자세한 내용은 [System Center Configuration Manager의 온-프레미스 인프라로 모바일 장치 관리](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md)를 참조하세요.  

###  <a name="manage-devices-with-microsoft-intune-hybrid"></a>Microsoft Intune을 사용하여 장치 관리(하이브리드)  

이 옵션에서는 Configuration Manager 온-프레미스 리소스를 사용하는 대신 Microsoft Intune을 사용하여 장치를 등록하고 관리합니다. Intune에서 장치를 관리하지만 Configuration Manager 콘솔에서 관리 태스크에 액세스합니다. 이 옵션은 Windows 10 Mobile, Windows Phone, iOS, Mac OS X, Android 등 모든 주요 모바일 장치 운영 체제를 지원합니다. 또한 조직의 Windows 8.1 및 Windows 10 컴퓨터를 관리하는 기능을 제공합니다.  

자세한 내용은 [System Center Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 장치 관리)](../../mdm/understand/hybrid-mobile-device-management.md)을 참조하세요.  

###  <a name="manage-devices-with-microsoft-exchange"></a>Microsoft Exchange를 사용하여 장치 관리  

이 옵션에서는 Exchange Server 커넥터를 사용하여 여러 Exchange 서버를 Configuration Manager에 연결합니다. 이를 통해 Exchange ActiveSync에 연결할 수 있는 장치를 중앙 집중식으로 관리합니다. Configuration Manager 콘솔에서 여러 Exchange 서버에 대한 설정 제어 및 원격 장치 초기화와 같은 Exchange 모바일 장치 관리 기능을 구성할 수 있습니다.  

자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

이러한 장치 관리 솔루션을 단독으로 사용하거나 서로 결합해서 사용할 수 있습니다. 예를 들어 클라이언트 기반 관리 방식을 사용하여 조직의 컴퓨터 및 서버를 관리하는 동시에 Intune을 사용하여 모바일 장치를 관리할 수 있습니다. 이처럼 여러 관리 방식을 결합하여 사용하면 Configuration Manager 콘솔에서 모든 장치 관리 요구를 처리할 수 있습니다.  

## <a name="compare-device-management-solutions-based-on-supported-mobile-device-platforms"></a>지원되는 모바일 장치 플랫폼을 기준으로 장치 관리 솔루션 비교  

|플랫폼|Configuration Manager 클라이언트 사용|Configuration Manager 통합 Microsoft Intune(하이브리드)|온\-프레미스 모바일 장치 관리|Configuration Manager와 Exchange|  
|--------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Android||예||예|  
|iOS||예||예|  
|Mac OS X|예|||예|  
|UNIX/Linux|예|||예|  
|Windows 10|예|예|예|예|  
|Windows 10 Mobile||예|예|예|  
|Windows(이전 버전)|예|예||예|  
|Windows CE|예(모바일 장치 레거시 클라이언트 사용)|||예|  
|Windows Embedded|예||||  
|Windows Phone||예||예|  
|Windows Server|예|||예|  

 지원되는 플랫폼의 전체 목록은 [Supported operating systems for clients and devices for System Center Configuration Manager](configs\supported-operating-systems-for-clients-and-devices.md)(System Center Configuration Manager용 클라이언트 및 장치에 대해 지원되는 운영 체제)를 참조하세요.

##  <a name="a-namebkmkcomp2a-compare-mobile-device-management-solutions-based-on-management-functionality"></a><a name="bkmk_comp2"></a> 관리 기능을 기준으로 모바일 장치 관리 솔루션 비교  

|관리 기능|Configuration Manager 클라이언트 사용|Configuration Manager 통합 Microsoft Intune(하이브리드)|온\-프레미스 모바일 장치 관리|Configuration Manager와 Exchange|  
|------------------------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|모바일 장치와 Configuration Manager 간의 PKI(공개 키 인프라)(상호 인증과 SSL을 통한 데이터 전송 암호화)|예|예|예||  
|클라이언트 설치|예||||  
|인터넷을 통한 지원|예||||  
|검색|예|||예|  
|하드웨어 인벤토리|예|예|예|예|  
|소프트웨어 인벤토리|예|||예|  
|설정|예|예|예|예|  
|소프트웨어 배포|예|예|예||  
|대체 상태 지점을 사용한 모니터링|예||||  
|관리 지점에 대한 연결|예||예||  
|배포 지점에 대한 연결|예|예|예||  
|Configuration Manager의 블록|예|예|예||  
|Exchange Server(및 Configuration Manager)에서 격리 및 차단||||예|  
|원격 지우기| |예|예|예|  



<!--HONumber=Jan17_HO1-->


