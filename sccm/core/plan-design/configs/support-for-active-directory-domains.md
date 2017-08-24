---
title: "지원되는 Active Directory 도메인 | Microsoft 문서"
description: "Active Directory 도메인에서 System Center Configuration Manager 사이트 시스템의 멤버 자격에 대한 요구 사항을 가져옵니다."
ms.custom: na
ms.date: 3/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c5a13f8-42d5-4898-b7b6-e594dae8b335
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 2654ab4eaaaf6a4bf3bd7dca9908e7033647dc2c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="supported-active-directory-domains-for-system-center-configuration-manager"></a>System Center Configuration Manager에서 지원되는 Active Directory 도메인

*적용 대상: System Center Configuration Manager(현재 분기)*

모든 System Center Configuration Manager 사이트 시스템은 지원되는 Windows Server Active Directory 도메인의 구성원이어야 합니다. Configuration Manager 클라이언트 컴퓨터는 도메인 구성원 또는 작업 그룹 구성원일 수 있습니다.  

 **요구 사항 및 제한 사항:**  

-   도메인 멤버 자격은 DMZ(Demilitarized Zone) 및 스크린된 서브넷이라고도 하는 경계 네트워크의 인터넷 기반 클라이언트 관리를 지원하는 사이트 시스템에 적용됩니다.  

-   사이트 시스템 역할을 호스트하는 컴퓨터에 대해 다음을 변경할 수는 없습니다.  

    -   도메인 멤버 자격  

    -   도메인 이름  

    -   컴퓨터 이름  

이러한 항목을 변경하기 전에 사이트 시스템 역할을 제거해야 하며 사이트 서버의 경우 사이트도 제거해야 합니다.  

**다음 도메인 기능 수준의 도메인이 지원됩니다.**  
- Windows Server 2016

- Windows Server 2012 R2  

- Windows Server 2012

- Windows Server 2008 R2

- Windows Server 2008  







##  <a name="bkmk_Disjoint"></a> 비연속 네임스페이스  
Configuration Manager에서는 비연속 네임스페이스를 포함하는 도메인에 사이트 시스템과 클라이언트를 설치할 수 있습니다.  

비연속 네임스페이스 시나리오는 컴퓨터의 주 DNS(Domain Name System) 접미사가 해당 컴퓨터가 있는 Active Directory DNS 도메인 이름과 일치하지 않는 시나리오 중 하나입니다. 이와 같이 일치하지 않는 주 DNS 접미사를 사용하는 컴퓨터를 비연속 컴퓨터라고 합니다. 비연속 네임스페이스의 또 다른 시나리오로는 도메인 컨트롤러의 NetBIOS 도메인 이름이 Active Directory DNS 도메인 이름과 일치하지 않는 경우를 들 수 있습니다.  

다음 표에는 비연속 네임스페이스에 대해 지원되는 시나리오가 나와 있습니다.  

|시나리오|추가 정보|  
|--------------|----------------------|  
|**시나리오 1:**<br /><br /> 도메인 컨트롤러의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 다릅니다. 도메인의 구성원인 컴퓨터는 비연속일 수도 있고 비연속이 아닐 수도 있습니다.|이 시나리오에서는 도메인 컨트롤러의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 다릅니다. 이 시나리오에서는 도메인 컨트롤러가 비연속입니다. 사이트 서버와 컴퓨터 등 도메인의 구성원인 컴퓨터는 도메인 컨트롤러의 주 DNS 접미사 또는 Active Directory DNS 도메인 이름과 일치하는 주 DNS 접미사를 사용할 수 있습니다.|  
|**시나리오 2:**<br /><br /> 도메인 컨트롤러는 비연속이 아니더라도 Active Directory 도메인의 구성원 컴퓨터가 비연속입니다.|이 시나리오에서는 도메인 컨트롤러의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 같더라도 사이트 시스템이 설치된 구성원 컴퓨터의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 다릅니다. 이 시나리오에서 도메인 컨트롤러는 비연속이 아니고 구성원 컴퓨터는 비연속입니다. Configuration Manager 클라이언트를 실행하는 구성원 컴퓨터는 비연속 사이트 시스템 서버의 주 DNS 접미사 또는 Active Directory DNS 도메인 이름과 일치하는 주 DNS 접미사를 사용할 수 있습니다.|  

 컴퓨터가 비연속 도메인 컨트롤러에 액세스할 수 있도록 하려면 도메인 개체 컨테이너에서 **msDS-AllowedDNSSuffixes** Active Directory 특성을 변경해야 합니다. 두 DNS 접미사를 모두 특성에 추가해야 합니다.  

 또한 조직 내에 배포된 모든 DNS 네임스페이스가 DNS 접미사 검색 목록에 포함되도록 하려면 비연속 도메인의 각 컴퓨터에 대해 검색 목록을 구성해야 합니다. 도메인 컨트롤러의 주 DNS 접미사, DNS 도메인 이름 및 Configuration Manager가 상호 작용할 수도 있는 다른 서버의 추가 네임스페이스가 네임스페이스 목록에 포함되는지 확인합니다. 그룹 정책 관리 콘솔을 사용하여 **DNS(Domain Name System) 접미사 검색** 목록을 구성할 수 있습니다.  

> [!IMPORTANT]  
>  Configuration Manager에서 컴퓨터를 참조하는 경우 해당 주 DNS 접미사를 사용하여 컴퓨터를 입력합니다. 이 접미사는 Active Directory 도메인에 **dnsHostName** 특성으로 등록되어 있는 정규화된 도메인 이름 및 시스템과 연결된 서비스 사용자 이름과 일치해야 합니다.  

##  <a name="bkmk_SLD"></a> 단일 레이블 도메인  
 Configuration Manager에서는 다음 기준이 충족될 경우 단일 레이블 도메인의 사이트 시스템 및 클라이언트를 지원합니다.  

-   유효한 최상위 도메인이 있는 비연속 DNS 네임스페이스를 사용하여 Active Directory Domain Services의 단일 레이블 도메인을 구성해야 합니다.  

     **예제:** Contoso의 단일 레이블 도메인이 DNS contoso.com에서 비연속 네임스페이스를 포함하도록 구성되어 있습니다. 따라서 Contoso 도메인의 컴퓨터에 대해 Configuration Manager에서 DNS 접미사를 지정할 때는 “Contoso”가 아닌 “Contoso.com”을 지정합니다.  

-   Kerberos 인증을 사용하여 사이트 서버와 시스템 컨텍스트 간의 DCOM(Distributed Component Object Model) 연결을 설정할 수 있어야 합니다.  
