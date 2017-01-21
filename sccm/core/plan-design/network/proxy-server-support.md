---
title: "프록시 서버 지원 | Microsoft 문서"
description: "사이트 시스템 서버와 클라이언트에서 사용하는 프록시 서버에 대한 System Center Configuration Manager 지원에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 6ed317d45d90758832d4157985dd95d5e253c6fc
ms.openlocfilehash: 97f9cc792d1fea20c32f38bc98cbdfb9ba90640d


---
# <a name="proxy-server-support-in-system-center-configuration-manager"></a>System Center Configuration Manager의 프록시 서버 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 사이트 시스템 서버와 클라이언트는 둘 다 프록시 서버를 사용할 수 있습니다.  

## <a name="site-system-servers"></a>사이트 시스템 서버  
사이트 시스템 역할이 인터넷에 연결해야 하는 경우 프록시 서버를 사용하도록 구성할 수 있습니다.  

-   사이트 시스템 서버를 호스트하는 컴퓨터는 해당 컴퓨터의 모든 사이트 시스템 역할에 의해 공유되는 단일 프록시 서버 구성을 지원합니다. 각 역할 또는 역할 인스턴스에 대해 개별 프록시 서버가 필요한 경우 별도의 사이트 시스템 서버에 이러한 역할을 저장해야 합니다.  

-   이미 프록시 서버 구성이 있는 사이트 시스템 서버에 대해 새 프록시 서버 설정을 구성하면 원래 구성을 덮어씁니다.  

-   프록시 연결은 사이트 시스템 역할을 호스트하는 컴퓨터의 **시스템** 계정을 사용합니다.  

다음 사이트 시스템 역할은 인터넷에 연결하며 프록시 서버를 필요로 할 수 있습니다.  한 가지 경우를 제외하고 프록시를 사용할 수 있는 사이트 시스템 역할은 추가 구성 없이 프록시를 사용합니다. 소프트웨어 업데이트 지점은 예외입니다. 다음 목록에는 소프트웨어 업데이트 지점에 필요한 추가 구성에 대한 정보가 포함되어 있습니다.  

**Asset Intelligence 동기화 지점** - 이 사이트 시스템 역할은 Microsoft에 연결되며 Asset Intelligence 동기화 지점을 호스트하는 컴퓨터의 프록시 서버 구성을 사용합니다.  

**클라우드 기반 배포 지점** - 클라우드 기반 배포 지점에 대한 프록시 서버를 구성하려면 클라우드 기반 배포 지점을 관리하는 기본 사이트에서 프록시를 구성합니다.  

이 구성에서 기본 사이트 서버는 다음과 같은 특징이 있습니다.  

-   배포 지점을 프로비전하고 모니터링하며 콘텐츠를 배포하기 위해 Microsoft Azure에 연결할 수 있어야 합니다.  

-   해당 컴퓨터 시스템 계정을 사용하여 연결합니다.  

-   해당 컴퓨터의 기본 웹 브라우저를 사용합니다.  

Microsoft Azure에서 클라우드 기반 배포 지점에 프록시 서버를 구성할 수 없습니다.  

**클라우드 연결점** - 이 사이트 시스템 역할은 Configuration Manager 클라우드 서비스에 연결하여 Configuration Manager의 업데이트된 버전을 다운로드하고 서비스 연결 지점을 호스트하는 컴퓨터에 구성된 프록시 서버를 사용합니다.  

**Exchange Server 커넥터** - 이 사이트 시스템 역할은 Exchange Server에 연결되며 Exchange Server 커넥터를 호스트하는 컴퓨터에 프록시 서버 구성을 사용합니다.  

**서비스 연결 지점** - 이 사이트 시스템 역할은 Microsoft Intune에 연결하여 커넥터를 호스트하는 컴퓨터의 프록시 서버 구성을 사용합니다.  

**소프트웨어 업데이트 지점** - 이 사이트 시스템 역할은 Microsoft 업데이트에 연결하여 패치를 다운로드하고 업데이트에 대한 정보를 동기화할 때 프록시를 사용할 수 있습니다.   
소프트웨어 업데이트 지점을 구성할 때 해당 옵션을 사용하도록 설정하면 소프트웨어 업데이트 지점은 다음 두 옵션에 대해서만 프록시를 사용합니다.  

-   **소프트웨어 업데이트를 동기화하는 경우 프록시 서버 사용**  

-   **자동 배포 규칙을 사용하여 콘텐츠 다운로드 시 프록시 서버 사용** (이 설정은 사용 가능하지만 보조 사이트의 소프트웨어 업데이트 지점에서 사용되지 않음)  

사이트 시스템 역할 추가 마법사의 활성 소프트웨어 업데이트 지점 페이지 또는 소프트웨어 업데이트 지점 구성 요소 속성의 일반 탭에서 프록시 서버 설정을 구성합니다.  

-   프록시 서버 설정은 사이트의 소프트웨어 업데이트 지점에만 연결됩니다.  

-   프록시 서버 옵션은 소프트웨어 업데이트 지점을 호스트하는 사이트 시스템 서버에 대해 구성된 프록시 서버가 이미 있는 경우에만 사용할 수 있습니다.  

> [!NOTE]  
>  자동 배포 규칙을 실행하면 기본적으로 자동 배포 규칙을 만든 서버의 **시스템** 계정을 사용하여 인터넷에 연결하고 소프트웨어 업데이트를 다운로드합니다.  
>   
>  이 계정에 인터넷 액세스 계정이 없으면 소프트웨어 업데이트를 다운로드하지 못하고 ruleengine.log에 다음 항목이 로깅됩니다. **인터넷에서 업데이트를 다운로드하지 못했습니다. 오류 = 12007.**  

#### <a name="to-configure-the-proxy-server-for-a-site-system-server"></a>사이트 시스템 서버에 대해 프록시 서버를 구성하려면  

1.  Configuration Manager 콘솔에서 관리를 클릭하고 사이트 구성을 확장한 다음 서버 및 사이트 시스템 역할을 클릭합니다.  

2.  편집하려는 사이트 시스템 서버를 선택한 다음 세부 정보에서 사이트 시스템을 마우스 오른쪽 단추로 클릭하고 속성을 클릭합니다.  

3.  사이트 시스템 속성에서 프록시 탭을 선택한 다음 이 기본 사이트 서버에 프록시 설정을 구성합니다.  

4.  확인을 클릭하여 새 프록시 서버 구성을 저장합니다.  



<!--HONumber=Dec16_HO3-->


