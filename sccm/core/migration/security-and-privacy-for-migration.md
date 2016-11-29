---
title: "보안 및 개인 정보 마이그레이션 | System Center Configuration Manager"
description: "사용자의 System Center Configuration Manager 환경으로 마이그레이션하는 데 대한 보안 모범 사례 및 개인 정보를 확인합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6893fce1-7ad5-4151-9ba9-3096871e8e4a
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 8c47633cfe6a03d881ebd02154ca2ab2e3009b3e


---
# <a name="security-and-privacy-for-migration-to-system-center-configuration-manager"></a>System Center Configuration Manager로의 마이그레이션에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 사용자의 System Center Configuration Manager 환경으로 마이그레이션하는 데 대한 보안 모범 사례 및 개인 정보가 포함되어 있습니다.  

## <a name="security-best-practices-for-migration"></a>마이그레이션에 대한 보안 모범 사례  
 마이그레이션을 위한 다음의 보안 모범 사례를 활용하십시오.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|원본 사이트 SMS 공급자 계정 및 원본 사이트 SQL Server 계정에 사용자 계정이 아닌 컴퓨터 계정을 사용하십시오.|마이그레이션에 사용자 계정을 사용해야 할 경우 마이그레이션을 완료한 후에 계정 세부 정보를 제거하시기 바랍니다.|  
|원본 사이트의 배포 지점에서 대상 사이트의 배포 지점으로 콘텐츠를 마이그레이션할 경우 IPsec을 사용합니다.|마이그레이션된 콘텐츠는 무단 변조의 검색을 위해 해싱되기는 하지만, 데이터가 전송되는 동안 수정될 경우 마이그레이션은 실패합니다.|  
|마이그레이션 작업을 만들 수 있는 관리자를 제한 및 모니터링하십시오.|대상 계층의 데이터베이스의 무결성은 관리자가 원본 계층에서 가져오기 위해 선택하는 데이터의 무결성에 좌우됩니다. 또한 이 관리자는 원본 계층에서 모든 데이터를 읽을 수 있습니다.|  

### <a name="security-issues-for-migration"></a>마이그레이션에 대한 보안 문제  
마이그레이션에는 다음과 같은 보안 문제가 있습니다.  

-   원본 사이트에서 차단된 클라이언트는 해당 클라이언트 레코드가 마이그레이션되기 전에 대상 계층에 성공적으로 할당을 수행할 수도 있습니다.  

     Configuration Manager는 사용자가 마이그레이션하는 클라이언트의 차단 상태를 보존하지만 클라이언트 레코드의 마이그레이션이 완료되기 전에 할당이 발생할 경우 해당 클라이언트는 대상 계층에 성공적으로 할당을 수행할 수 있습니다.  

-   감사 메시지는 마이그레이션되지 않습니다.  

데이터를 원본 사이트에서 대상 사이트로 마이그레이션할 때 원본 계층의 모든 감사 정보는 손실됩니다.  

## <a name="privacy-information-for-migration"></a>마이그레이션에 대한 개인 정보  
 사용자가 원본 인프라에서 확인한 사이트 데이터베이스의 정보가 마이그레이션 과정에서 검색되고 이 데이터는 대상 계층의 데이터베이스에 저장됩니다. System Center Configuration Manager로 원본 사이트 또는 계층에서 검색할 수 있는 정보는 원본 환경에서 사용하도록 설정된 기능과 해당 원본 환경에서 수행된 관리 작업에 따라 다릅니다.  

 보안 및 개인 정보에 대한 자세한 내용은 다음 항목 중 하나를 참조하십시오.  

-   Configuration Manager 2007의 개인 정보에 대한 자세한 내용은 Configuration Manager 2007 문서 라이브러리에서 [Configuration Manager 2007의 보안 및 개인 정보](http://go.microsoft.com/fwlink/p/?LinkId=216450)를 참조하세요.  

-   System Center 2012 Configuration Manager의 개인 정보에 대한 자세한 내용은 System Center 2012 Configuration Manager 문서 라이브러리에서 [System Center 2012 Configuration Manager의 보안 및 개인 정보](https://technet.microsoft.com/library/gg682033.aspx)를 참조하세요.  

-   System Center Configuration Manager의 개인 정보에 대한 자세한 내용은 [System Center Configuration Manager의 보안 및 개인 정보](../../core/plan-design/security/security-and-privacy.md)를 참조하세요.  

지원되는 데이터 중 일부 또는 모두를 원본 사이트에서 대상 계층으로 마이그레이션할 수 있습니다.  

마이그레이션은 기본적으로 활성화되지 않으며 몇 개의 구성 단계를 거쳐야 실행할 수 있습니다. 마이그레이션 정보는 Microsoft로 전송되지 않습니다.  

원본 계층에서 데이터를 마이그레이션하려면 먼저 개인 정보 취급 방침 요구 사항을 검토하십시오.  



<!--HONumber=Nov16_HO1-->


