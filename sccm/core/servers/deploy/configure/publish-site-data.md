---
title: "사이트 데이터 게시"
titleSuffix: Configuration Manager
description: "Configuration Manager 사이트를 Active Directory Domain Services에 게시하는 방법을 알아봅니다."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 17cf034f-eaff-43ce-bc8e-917213c1db74
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8969a7a97e11fe0c01999e828578f3748cffa74b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="publish-site-data-for-system-center-configuration-manager"></a>System Center Configuration Manager용으로 사이트 데이터 게시

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Active Directory 스키마를 확장한 후에 Configuration Manager 사이트를 AD DS(Active Directory Domain Services)에 게시할 수 있습니다. 이렇게 하면 Active Directory 컴퓨터를 통해 신뢰할 수 있는 소스에서 사이트 정보를 안전하게 검색할 수 있습니다. 기본 Configuration Manager 기능을 사용하기 위해 사이트 정보를 AD DS에 반드시 게시해야 하는 것은 아니지만, 게시하면 관리 부담을 줄일 수 있습니다.  

-   **사이트를 AD DS에 게시하도록 구성하면** Configuration Manager 클라이언트는 Active Directory 게시를 통해 관리 지점을 자동으로 찾을 수 있습니다. 여기에는 글로벌 카탈로그 서버에 대한 LDAP 쿼리를 사용합니다.  

-   **사이트가 AD DS에 게시되지 않으면**클라이언트는 대체 메커니즘을 통해 기본 관리 지점을 찾아야 합니다.  

클라이언트가 관리 지점을 찾는 방법에 대한 자세한 내용은 [클라이언트가 System Center Configuration Manager에 대한 사이트 리소스 및 서비스를 찾는 방법 이해](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)를 참조하세요.  

## <a name="configure-sites-to-publish-to-ad-ds"></a>AD DS에 게시하도록 사이트 구성  
 대략적인 구성 단계는 다음과 같습니다.  

-   사이트 데이터를 게시할 각 포리스트에서 [System Center Configuration Manager의 Active Directory 스키마를 확장](../../../../core/plan-design/network/extend-the-active-directory-schema.md)해야 합니다. **시스템 관리** 컨테이너도 있어야 합니다.  

-   데이터를 게시할 각 기본 사이트의 컴퓨터 계정에   **시스템 관리** 컨테이너와 모든 자식 개체에 대한 **모든 권한** 을 부여해야 합니다.  

### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-active-directory-forest"></a>Configuration Manager 사이트에서 사이트 정보를 Active Directory 포리스트에 게시할 수 있도록 하려면

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다. 사이트 데이터를 게시할 사이트를 선택합니다. 그런 다음 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

3.  사이트 속성의 **게시** 탭에서 이 사이트의 사이트 데이터를 게시할 대상 포리스트를 선택합니다.  

4.  **확인** 을 클릭하여 구성을 저장합니다.  

### <a name="to-set-up-active-directory-forests-for-publishing"></a>게시를 위한 Active Directory 포리스트를 설정하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **Active Directory 포리스트**를 클릭합니다. 이전에 Active Directory 포리스트 검색을 실행한 경우 검색된 각 포리스트가 결과 창에 표시됩니다. Active Directory 포리스트 검색을 실행하면 로컬 포리스트 및 트러스트된 모든 포리스트가 검색됩니다. 트러스트되지 않은 포리스트만 수동으로 추가해야 합니다.  

    -   이전에 검색된 포리스트를 설정하려면 결과 창에서 포리스트를 선택합니다. 그 후에 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭하여 포리스트 속성을 엽니다. 계속해서 3단계를 진행합니다.  

    -   목록에 없는 새 포리스트를 설정하려면 **홈** 탭의 **만들기** 그룹에서 **포리스트 추가**를 클릭하여 **포리스트 추가** 대화 상자를 엽니다. 계속해서 3단계를 진행합니다.  

3.  **일반** 탭에서 검색할 포리스트의 구성을 완료하고 **Active Directory 포리스트 계정**을 지정합니다.  

    > [!NOTE]  
    >  트러스트되지 않은 포리스트를 검색하고 게시하려면 Active Directory 포리스트 검색에서 글로벌 계정을 사용해야 합니다. 사이트 서버의 컴퓨터 계정을 사용하지 않는 경우 글로벌 계정만 선택할 수 있습니다.  

4.  사이트에서 이 포리스트에 사이트 데이터를 게시할 수 있도록 하려면 **게시** 탭에서 이 포리스트에 게시할 수 있도록 구성을 완료합니다.  

    > [!NOTE]  
    >  사이트에서 포리스트에 게시할 수 있도록 설정한 경우에는 Configuration Manager의 해당 포리스트에 대한 Active Directory 스키마를 확장해야 합니다. Active Directory 포리스트 계정에는 해당 포리스트의 시스템 컨테이너에 대한 모든 권한이 있어야 합니다.  

5.  Active Directory 포리스트 검색을 사용하도록 이 포리스트의 구성을 완료한 후에는 **OK** 를 클릭하여 구성을 저장합니다.  
