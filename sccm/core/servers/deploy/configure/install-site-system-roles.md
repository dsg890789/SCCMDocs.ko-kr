---
title: "사이트 시스템 역할 설치 | System Center Configuration Manager"
description: "마법사를 사용하여 사이트의 기존 또는 새 사이트 시스템 서버에 사이트 시스템 역할을 추가할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 780ef516ddc641d53e1d2d4a5f559795cfd22cbb

---
# <a name="install-site-system-roles-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 사이트 시스템 역할 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 콘솔에는 사이트 시스템 역할을 설치하는 데 사용할 수 있는 두 가지 마법사가 있습니다.  

-   **사이트 시스템 역할 추가 마법사**: 사이트의 기존 사이트 시스템 서버에 사이트 시스템 역할을 추가하려면 이 마법사를 사용합니다.  

-   **사이트 시스템 서버 만들기 마법사**: 새 서버를 사이트 시스템 서버로 지정한 다음 이 서버에 사이트 시스템 역할을 하나 이상 설치하려면 이 마법사를 사용합니다. 이 마법사는 첫 페이지에서 사용할 서버 이름과 사이트 시스템 역할을 추가할 사이트를 지정해야 하는 점을 제외하고 **사이트 시스템 역할 추가 마법사**와 같습니다.  

원격 컴퓨터(SMS 공급자의 인스턴스 포함)에 사이트 시스템 역할을 설치하면 원격 컴퓨터의 컴퓨터 계정이 사이트 서버의 로컬 그룹에 추가됩니다. 사이트가 도메인 컨트롤러에 설치된 경우 사이트 서버의 그룹은 로컬 그룹이 아니라 도메인 그룹이고, 사이트 시스템 역할 컴퓨터를 다시 시작하거나 원격 컴퓨터 계정([System Center Configuration Manager에서 사용되는 계정](../../../../core/plan-design/hierarchy/accounts.md))의 Kerberos 티켓을 새로 고칠 때까지 원격 사이트 시스템 역할이 작동하지 않습니다.  

사이트 시스템 역할을 설치하기 직전에 Configuration Manager는 대상 컴퓨터가 선택한 사이트 시스템 역할에 대한 필수 조건을 충족하는지 확인합니다. 사이트 시스템 역할 설치:  

-   기본적으로 Configuration Manager에서 사이트 시스템 역할을 설치할 때 사용 가능한 첫 번째 NTFS 포맷의 디스크 드라이브(디스크 여유 공간이 가장 큼)에 설치 파일이 설치됩니다. Configuration Manager가 특정 드라이브에 설치되지 않도록 하려면 사이트 시스템 서버를 설치하기 전에 **no_sms_on_drive.sms**라는 빈 파일을 만들고 드라이브의 루트 폴더에 복사합니다.  

-   Configuration Manager에서 **사이트 시스템 설치 계정**을 사용하여 사이트 시스템 역할을 설치합니다. 적절한 마법사를 실행하여 새 사이트 시스템 서버를 만들거나 기존 사이트 시스템 서버에 사이트 시스템 역할을 추가할 때 이 계정을 지정합니다. 기본적으로 이 계정은 사이트 서버 컴퓨터의 로컬 시스템 계정이지만, 사이트 시스템 설치 계정으로 사용할 도메인 사용자 계정을 지정할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에 사용된 계정](../../../../core/plan-design/hierarchy/accounts.md) 항목에서 사이트 시스템 설치 계정을 참조하세요.  

##  <a name="a-namebkmkinstalla-to-install-site-system-roles-on-an-existing-site-system-server"></a><a name="bkmk_Install"></a> 기존 사이트 시스템 서버에 사이트 시스템 역할을 설치하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭한 다음 새 사이트 시스템 역할에 사용할 서버를 선택합니다.  

3.  **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가**를 클릭합니다.  

4.  **일반** 페이지에서 설정을 검토한 후 **다음**을 클릭합니다.  

    > [!TIP]  
    >  인터넷에서 사이트 시스템 역할에 액세스하려면 인터넷 FQDN을 지정해야 합니다.  

5.  이 사이트 시스템 서버에서 실행하는 사이트 시스템 역할을 사용하려면 프록시 서버를 인터넷의 위치에 연결해야 하는 경우 **프록시** 페이지에서 프록시 서버의 설정을 지정하고 **다음**을 클릭합니다.  

6.  **시스템 역할 선택** 페이지에서 추가할 사이트 시스템 역할을 선택하고 **다음**을 클릭합니다.  

7.  마법사를 완료합니다.  

> [!TIP]  
>  Windows PowerShell cmdlet인 New-CMSiteSystemServer는 이 절차와 동일한 기능을 수행합니다. 자세한 내용은 System Center 2012 Configuration Manager SP1 Cmdlet 참조 문서에서 [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414)를 참조하세요.  

## <a name="to-install-site-system-roles-on-a-new-site-system-server"></a>새 사이트 시스템 서버에 사이트 시스템 역할을 설치하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 클릭합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다.  

    > [!TIP]  
    >  인터넷에서 새 사이트 시스템 역할에 액세스하려면 인터넷 FQDN을 지정해야 합니다.  

5.  이 사이트 시스템 서버에서 실행하는 사이트 시스템 역할을 사용하려면 프록시 서버를 인터넷의 위치에 연결해야 하는 경우 **프록시** 페이지에서 프록시 서버의 설정을 지정하고 **다음**을 클릭합니다.  

6.  **시스템 역할 선택** 페이지에서 추가할 사이트 시스템 역할을 선택하고 **다음**을 클릭합니다.  

7.  마법사를 완료합니다.  

> [!TIP]  
>  Windows PowerShell cmdlet인 New-CMSiteSystemServer는 이 절차와 동일한 기능을 수행합니다. 자세한 내용은 System Center 2012 Configuration Manager SP1 Cmdlet 참조 문서에서 [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414)를 참조하세요.  



<!--HONumber=Nov16_HO1-->


