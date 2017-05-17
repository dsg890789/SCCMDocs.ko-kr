---
title: "Active Directory 스키마 게시 | Microsoft 문서"
description: "System Center Configuration Manager에 대한 Active Directory 스키마를 확장하여 클라이언트 배포 및 구성 프로세스를 간소화합니다."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: 17
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 88649111ea3a38c027efb4952211546afd0bf27e
ms.openlocfilehash: 58beef440db8e019a06ce7c4c8eaabc8e85ce954
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-active-directory-for-site-publishing"></a>사이트 게시를 위해 Active Directory 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에 대한 Active Directory 스키마를 확장하는 경우 클라이언트가 쉽게 액세스할 수 있는 안전한 위치에서 주요 정보를 게시하기 위해 Configuration Manager 사이트에서 사용하는 Active Directory에 새로운 구조를 도입합니다.  

온-프레미스 클라이언트를 관리할 때는 Active Directory 스키마가 확장된 Configuration Manager를 사용하는 것이 좋습니다. 확장된 스키마로 클라이언트 배포 및 설정 프로세스를 간소화할 수 있습니다. 확장된 스키마를 사용하면 콘텐츠 서버나 다른 Configuration Manager 사이트 시스템 역할에서 제공하는 추가 서비스와 같은 리소스를 클라이언트에서 효율적으로 찾을 수 있습니다.  

-   Configuration Manager 배포를 제공하는 확장된 스키마를 모르는 경우 [System Center Configuration Manager의 스키마 확장](../../../core/plan-design/network/schema-extensions.md)을 참조하여 적절한 스키마를 결정할 수 있습니다.  

-   확장된 스키마를 사용하지 않는 경우에는 서비스 및 사이트 시스템 서버를 찾기 위한 DNS, WINS 등의 다른 방법을 설정할 수 있습니다. 이러한 서비스 위치 찾기 방법을 사용하는 경우 추가 구성이 필요하므로, 클라이언트가 서비스 위치를 찾을 때 이러한 방법이 기본적으로 사용되지는 않습니다. 자세히 알아보려면 [클라이언트가 System Center Configuration Manager에 대한 사이트 리소스 및 서비스를 찾는 방법 이해](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)를 참조하세요.  

-   Active Directory 스키마가 Configuration Manager 2007 또는 System Center 2012 Configuration Manager에 대해 확장된 경우 더 이상은 확장할 필요가 없습니다. 스키마 확장은 변경되지 않았으며 내부에 이미 포함되어 있기 때문입니다.  

스키마 확장은 모든 포리스트에 대해 한 번만 수행하면 되는 작업입니다. 확장한 후 확장된 Active Directory 스키마를 사용하려면 다음 단계를 수행합니다.  

## <a name="step-1-extend-the-schema"></a>1단계. 스키마 확장  
Configuration Manager의 스키마를 확장하려면:  

-   스키마 관리 보안 그룹의 구성원인 계정을 사용해야 합니다.  

-   스키마 마스터 도메인 컨트롤러에 로그인되어 있어야 합니다.  

-   **extadsch.exe** 도구를 실행하거나 **ConfigMgr_ad_schema.ldf** 파일을 통해 LDIFDE 명령줄 유틸리티를 사용합니다. 도구와 파일 모두 Configuration Manager 설치 미디어의 **SMSSETUP\BIN\X64** 폴더에 있습니다.  

#### <a name="option-a-use-extadschexe"></a>옵션 A: extadsch.exe 사용  

1.  **extadsch.exe** 를 실행하여 Active Directory 스키마에 새 클래스와 특성을 추가합니다.  

    > [!TIP]  
    >  명령줄에서 이 도구를 실행하고 도구가 실행되는 동안 피드백을 확인합니다.  

2.  시스템 드라이브의 루트에 있는 extadsch.log를 검토하여 스키마가 제대로 확장되었는지 확인합니다.  

#### <a name="option-b-use-the-ldif-file"></a>옵션 B: LDIF 파일 사용  

1.  **ConfigMgr_ad_schema.ldf** 파일을 편집하여 확장할 Active Directory 루트 도메인을 정의합니다.  

    -   이 파일에서 **DC=x**라는 텍스트의 모든 인스턴스를 확장할 도메인의 전체 이름으로 바꾸어야 합니다.  

    -   예를 들어 확장할 도메인의 전체 이름이 widgets.microsoft.com이라면 파일에서 DC=x의 모든 인스턴스를 **DC=widgets, DC=microsoft, DC=com**으로 바꿉니다.  

2.  LDIFDE 명령줄 유틸리티를 사용하여 **ConfigMgr_ad_schema.ldf** 파일의 내용을 Active Directory Domain Services로 가져옵니다.  

    -   예를 들어 다음 명령줄은 스키마 확장을 Active Directory Domain Services로 가져오고, 자세한 정보 로깅을 켜고, 가져오기 프로세스 중에 로그 파일을 만듭니다. **ldifde -i -f ConfigMgr_ad_schema.ldf -v -j &lt;로그 파일을 저장할 위치\>**  

3.  스키마가 제대로 확장되었는지 확인하려면, 이전 단계에서 사용한 명령줄에서 작성된 로그 파일을 검토합니다.  

## <a name="step-2--create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>2단계.  시스템 관리 컨테이너를 만들고 컨테이너에 사이트 권한 부여  
 스키마를 확장한 후 AD DS(Active Directory Domain Services)에서 **시스템 관리**라는 컨테이너를 만들어야 합니다.  

-   Active Directory에 데이터를 게시할 기본 또는 보조 사이트가 포함된 각 도메인에 이 컨테이너를 한 번 만듭니다.  

-   각 컨테이너에 대해, 해당 도메인에 데이터를 게시하는 각 기본 및 보조 사이트 서버의 컴퓨터 계정에 권한을 부여합니다. 각 계정에는 컨테이너에 대해 **모든 권한**(**적용 대상** 고급 권한이 **이 개체 및 모든 하위 개체**임)이 있어야 합니다.  

#### <a name="to-add-the-container"></a>컨테이너를 추가하려면  

1.  Active Directory Domain Services의 **시스템** 컨테이너에 대해 **모든 자식 개체 만들기** 권한이 있는 계정을 사용합니다.  

2.  **ADSI 편집**(adsiedit.msc)을 실행하고 사이트 서버의 도메인에 연결합니다.  

3.  컨테이너를 만듭니다.  

    -   **도메인** &lt;컴퓨터의 정규화된 도메인 이름\>, &lt;고유 이름\>을 차례로 확장한 다음 **CN=System**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**, **개체**를 차례로 선택합니다.  

    -   **개체 만들기** 대화 상자에서 **컨테이너**를 선택한 후 **다음**을 선택합니다.  

    -   **값** 상자에 **System Management**를 입력하고 **다음**을 선택합니다.  

4.  권한을 할당합니다.  

    > [!NOTE]  
    >  원하는 경우 Active Directory 사용자 및 컴퓨터 관리 도구(dsa.msc)와 같은 다른 도구를 사용하여 컨테이너에 대한 권한을 추가할 수 있습니다.  

    -   **CN=System Management**를 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.  

    -   **보안** 탭을 선택하고 **추가**를 선택한 다음 **모든 권한**이 있는 사이트 서버 컴퓨터 계정을 추가합니다.  

    -   **고급**을 선택하고 사이트 서버의 컴퓨터 계정을 선택한 다음 **편집**을 선택합니다.  

    -   **적용 대상** 목록에서 **이 개체 및 모든 하위 개체**를 선택합니다.  

5.  **확인**을 선택하여 콘솔을 닫고 구성을 저장합니다.  

## <a name="step-3-set-up-sites-to-publish-to-active-directory-domain-services"></a>3단계: 사이트를 Active Directory Domain Services에 게시하도록 설정  
 컨테이너를 설정하고 권한을 부여했으며 Configuration Manager 기본 사이트를 설치한 후에는 Active Directory에 데이터를 게시하도록 해당 사이트를 설정할 수 있습니다.  

 게시에 대한 자세한 내용은 [System Center Configuration Manager용으로 사이트 데이터 게시](../../../core/servers/deploy/configure/publish-site-data.md)를 참조하세요.  

