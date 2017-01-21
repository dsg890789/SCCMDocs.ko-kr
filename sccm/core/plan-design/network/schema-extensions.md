---
title: "스키마 확장 | Microsoft 문서"
description: "System Center Configuration Manager를 지원하도록 Active Directory 스키마를 확장합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
translationtype: Human Translation
ms.sourcegitcommit: 6ed317d45d90758832d4157985dd95d5e253c6fc
ms.openlocfilehash: f230b6cbe97b72fee4f5d2e45260e6217ef2cec0


---
# <a name="schema-extensions-for-system-center-configuration-manager"></a>System Center Configuration Manager의 스키마 확장

*적용 대상: System Center Configuration Manager(현재 분기)*

Active Directory 스키마를 확장하여 Configuration Manager를 지원할 수 있습니다. 이 경우 클라이언트가 안전하게 액세스할 수 있는 Active Directory에 중요한 정보를 게시하기 위해 Configuration Manager 사이트에서 사용하는 여러 특성과 새 컨테이너를 추가하도록 포리스트 Active Directory 스키마가 편집됩니다.  이 정보는 클라이언트의 배포 및 구성을 간소화할 수 있으며, 클라이언트가 배포된 콘텐츠를 포함하거나 클라이언트에 다양한 서비스를 제공하는 서버와 같은 사이트 리소스를 찾는 데 도움이 됩니다.  

-   Active Directory 스키마 확장은 필수는 아니지만 권장됩니다.  

[Active Directory 스키마를 확장](https://msdnstage.redmond.corp.microsoft.com/en-US/library/mt345589\(TechNet.10\).aspx)하기 전에 Active Directory Domain Services 및 [Active Directory 스키마 수정](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx)에 대해 잘 알고 있어야 합니다.  

## <a name="considerations-for-extending-the-active-directory-schema-for-configuration-manager"></a>Configuration Manager를 위한 Active Directory 스키마 확장에 대한 고려 사항  

-   System Center Configuration Manager의 Active Directory 스키마 확장은 Configuration Manager 2007 및 Configuration Manager 2012에서 사용된 Active Directory 스키마 확장에서 변경되지 않았습니다. 두 버전의 스키마를 이전에 확장한 경우 스키마를 다시 확장하지 않아도 됩니다.  

-   스키마 확장은 포리스트 전체에 적용되며 취소할 수 없는 일회성 작업입니다.  

-   스키마 확장은 스키마 관리 그룹의 구성원이거나 스키마를 수정할 수 있는 충분한 권한이 위임된 사용자만 수행할 수 있습니다.  

-   Configuration Manager 설치 프로그램을 실행하기 전이나 이후에 스키마를 확장할 수 있지만 사이트 및 계층 구조 설정을 구성하기 전에 확장하는 것이 좋습니다.  이렇게 하면 이후의 많은 구성 단계가 간소화됩니다.  

-   스키마를 확장한 후 Active Directory 글로벌 카탈로그가 포리스트 전체에 복제됩니다. 따라서 복제 트래픽이 다른 네트워크 종속 프로세스에 부정적인 영향을 주지 않는 시간에 스키마를 확장하세요.  

    -   Windows 2000 포리스트에서 스키마를 확장하면 전체 글로벌 카탈로그가 완전히 동기화됩니다.  

    -   Windows 2003 포리스트부터는 새로 추가한 특성만 복제됩니다.  

**Active Directory 스키마를 사용하지 않는 장치 및 클라이언트:**  

-   Exchange Server 커넥터에서 관리하는 모바일 장치  

-   Mac 컴퓨터용 클라이언트  

-   Linux 및 UNIX 서버용 클라이언트  

-   Configuration Manager에서 등록된 모바일 장치  

-   Microsoft Intune에서 등록한 모바일 장치  

-   모바일 장치 레거시 클라이언트  

-   인터넷 전용 클라이언트 관리를 위해 구성된 Windows 클라이언트  

-   Configuration Manager에서 인터넷상에 있는 것으로 감지된 Windows 클라이언트  

## <a name="capabilities-that-benefit-from-extending-the-schema"></a>스키마 확장을 활용하는 기능  
**클라이언트 컴퓨터 설치 및 사이트 할당** - Windows 컴퓨터에 새 클라이언트를 설치할 때 클라이언트는 Active Directory Domain Services에서 설치 속성을 검색합니다.  

-   **해결 방법:** 스키마를 확장하지 않는 경우 다음 옵션 중 하나를 사용하여 클라이언트 설치에 필요한 구성 세부 정보를 제공합니다.  

    -   **클라이언트 강제 설치를 사용합니다**. 클라이언트 설치 방법을 사용하기 전에 모든 필수 구성 요소가 충족되는지 확인합니다. 자세한 내용은 클라이언트 컴퓨터의 필수 조건에서 '설치 방법 종속성' 섹션을 참조하세요.  

    -   CCMSetup 설치 명령줄 속성을 사용하여 **클라이언트를 수동으로 설치**하고 클라이언트 설치 속성을 제공합니다. 여기에는 다음이 포함되어야 합니다.  

        -   클라이언트 설치 중 CCMSetup 명령줄에서 CCMSetup 속성 **/mp:=&lt;관리 지점 이름 컴퓨터 이름\>** 또는 **/source:&lt;클라이언트 원본 파일 경로\>**를 사용하여 컴퓨터가 설치 파일을 다운로드할 수 있는 관리 지점 또는 원본 경로를 지정합니다.  

        -   클라이언트가 사이트에 할당되어 클라이언트 정책과 사이트 설정을 다운로드할 수 있도록 사용할 초기 관리 지점의 목록을 지정합니다. 이를 위해 CCMSetup Client.msi 속성 SMSMP를 사용합니다.  

    -   **DNS 또는 WINS에 관리 지점을 게시** 하고 이 서비스 위치 방법을 사용하도록 클라이언트를 구성합니다.  

**클라이언트와 서버 간 통신에 대한 포트 구성** - 클라이언트는 설치될 때 Active Directory에 저장된 포트 정보를 사용하여 구성됩니다. 나중에 사이트의 클라이언트-서버 통신 포트를 변경하는 경우 클라이언트가 Active Directory Domain Services에서 이 새로운 포트 설정을 가져올 수 있습니다.  

-   **해결 방법:** 스키마를 확장하지 않는 경우 다음 옵션 중 하나를 사용하여 기존 클라이언트에 새 포트 구성을 제공합니다.  

    -   **클라이언트를 다시 설치** 합니다.  

    -   **포트 정보를 업데이트하는 사용자 지정 스크립트를 클라이언트에 배포합니다**. 포트 변경으로 인해 클라이언트가 사이트와 통신할 수 없는 경우 Configuration Manager를 사용하여 이 스크립트를 배포할 수 없습니다. 예를 들어 그룹 정책을 사용할 수 있습니다.  

**콘텐츠 배포 시나리오** - 한 사이트에서 콘텐츠를 만든 후에 계층 구조의 다른 사이트에 콘텐츠를 배포하는 경우 받는 사이트가 서명된 콘텐츠 데이터의 서명을 확인할 수 있어야 합니다. 이를 위해 이 데이터를 만드는 원본 사이트의 공개 키에 대한 액세스가 필요합니다. Configuration Manager의 Active Directory 스키마를 확장하면 계층 구조의 모든 사이트에서 사이트의 공개 키를 사용할 수 있습니다.  

-   **해결 방법:** 스키마를 확장하지 않는 경우 계층 구조 유지 관리 도구인 **preinst.exe**를 사용하여 사이트 간에 보안 키 정보를 교환합니다.  

     예를 들어 기본 사이트에 콘텐츠를 만들고 해당 콘텐츠를 다른 기본 사이트 아래의 보조 사이트에 배포하려는 경우, Active Directory 도메인 스키마를 확장하여 보조 사이트에서 원본 기본 사이트 공개 키를 가져올 수 있도록 하거나, preinst.exe를 사용하여 두 사이트 간에 직접 키를 공유하도록 해야 합니다.  

## <a name="active-directory-attributes-and-classes"></a>Active Directory 특성 및 클래스  
System Center Configuration Manager의 스키마를 확장하는 경우 다음 클래스와 특성이 스키마에 추가되며 해당 Active Directory 포리스트의 모든 Configuration Manager 사이트에서 사용할 수 있습니다.  

-   특성:  

    -   cn=mS-SMS-Assignment-Site-Code  

    -   cn=mS-SMS-Capabilities  

    -   cn=MS-SMS-Default-MP  

    -   cn=mS-SMS-Device-Management-Point  

    -   cn=mS-SMS-Health-State  

    -   cn=MS-SMS-MP-Address  

    -   cn=MS-SMS-MP-Name  

    -   cn=MS-SMS-Ranged-IP-High  

    -   cn=MS-SMS-Ranged-IP-Low  

    -   cn=MS-SMS-Roaming-Boundaries  
        위치:  

    -   cn=MS-SMS-Site-Boundaries  

    -   cn=MS-SMS-Site-Code  

    -   cn=mS-SMS-Source-Forest  

    -   cn=mS-SMS-Version  

-   클래스:  

    -   cn=MS-SMS-Management-Point  

    -   cn=MS-SMS-Roaming-Boundary-Range  

    -   cn=MS-SMS-Server-Locator-Point  

    -   cn=MS-SMS-Site  

> [!NOTE]  
>  스키마 확장에는 이전 버전의 제품에서 유지되었지만 Configuration Manager 2015에서는 사용되지 않는 특성과 클래스가 포함될 수 있습니다. 예를 들면 다음과 같습니다.  
>   
>  -   : cn = SMS 사이트 경계 MS  
> -   Class: cn=MS-SMS-Server-Locator-Point  

System Center Configuration Manager 설치 미디어의 **\SMSSETUP\BIN\x64** 폴더에 있는 **ConfigMgr_ad_schema.LDF** 파일을 보면 위의 목록이 최신 상태인지 확인할 수 있습니다.  



<!--HONumber=Dec16_HO3-->


