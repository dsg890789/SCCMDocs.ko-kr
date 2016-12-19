---
title: "장치 관리의 기본 사항 | Microsoft 문서"
description: "System Center Configuration Manager를 사용하여 장치를 관리하는 방법을 알아봅니다."
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
caps.latest.revision: 6
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 17b36eae97272c408fce20e1f88812dafc984773
ms.openlocfilehash: b907975db5b5ffa6fefef58902319b987e57dca6


---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 장치 관리의 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

넓은 의미에서 볼 때 System Center Configuration Manager는 다음 두 가지 범주의 장치를 관리할 수 있습니다.

**클라이언트**는 Configuration Manager 클라이언트 소프트웨어를 설치하는 워크스테이션, 랩톱, 서버, 모바일 장치 등의 장치입니다. 하드웨어 인벤토리 등의 일부 관리 기능을 사용하려면 이 클라이언트 소프트웨어가 필요합니다.  

**관리되는 장치**는 *클라이언트*를 포함할 수 있지만, 일반적으로 Configuration Manager 클라이언트 소프트웨어를 설치하지 않으며 Microsoft Intune 또는 Configuration Manager의 기본 제공 온-프레미스 모바일 장치 관리를 사용하여 관리하는 모바일 장치를 의미합니다.

클라이언트 유형뿐 아니라 사용자를 기준으로 하여 장치를 그룹화하고 식별할 수도 있습니다.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트를 사용하여 장치 관리

Configuration Manager 클라이언트 소프트웨어를 사용하여 장치를 관리하려면 네트워크의 장치를 검색한 후 해당 장치에 클라이언트 소프트웨어를 배포하거나 새 컴퓨터에 클라이언트 소프트웨어를 수동으로 설치한 후 네트워크에 컴퓨터를 가입할 때 사이트에 가입하도록 해야 합니다. 클라이언트 소프트웨어를 아직 설치하지 않은 장치를 검색하려면 기본 제공 검색 방법 중 하나 이상을 실행합니다. 장치를 검색한 후에는 몇 가지 방법 중 하나를 사용하여 클라이언트 소프트웨어를 설치합니다. 검색에 대한 자세한 내용은 [System Center Configuration Manager에 대한 검색 실행](../../core/servers/deploy/configure/run-discovery.md)을 참조하세요.  

 Configuration Manager 클라이언트 소프트웨어를 실행할 수 있는 장치를 검색한 후 여러 방법 중 하나를 사용하여 소프트웨어를 설치할 수 있습니다. 소프트웨어를 설치하여 클라이언트를 기본 사이트에 할당한 후에는 장치 관리를 시작할 수 있습니다.  일반적인 설치 방법에는 컴퓨터에 '클라이언트 강제 설치', '소프트웨어 업데이트 기반 설치, 그룹 정책 사용, 컴퓨터에 수동 설치, 배포하는 운영 체제 이미지의 일부로 클라이언트 포함 등이 포함됩니다.  

 클라이언트를 설치한 후에 컬렉션을 사용하여 장치 관리의 작업을 간소화할 수 있습니다. 컬렉션은 그룹으로 관리할 수 있도록 만드는 장치나 사용자의 그룹입니다. 예를 들어 Configuration Manager에서 등록한 모든 모바일 장치에 모바일 장치 응용 프로그램을 설치하려 할 수 있습니다. 이 경우 **모든 모바일 장치** 컬렉션을 사용할 수 있습니다.  

 자세한 내용은 다음 항목을 참조하세요.  

-   [System Center Configuration Manager에 대한 장치 관리 솔루션 선택](../../core/plan-design/choose-a-device-management-solution.md)  

-   [System Center Configuration Manager의 클라이언트 설치 방법](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [System Center Configuration Manager의 컬렉션 소개](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>클라이언트 설정  
 Configuration Manager를 처음 설치하면 계층의 모든 클라이언트가 기본 클라이언트 설정을 사용하여 구성됩니다. 기본 클라이언트 설정은 사용자가 변경할 수 있습니다. 이러한 클라이언트 설정에는 장치가 사이트와 통신하는 빈도, 소프트웨어 업데이트 및 기타 관리 작업에 대해 클라이언트를 사용하도록 설정할지 여부, 사용자가 자신의 모바일 장치를 등록하여 Configuration Manager에서 관리할 모바일 장치를 등록할 수 있는지 여부와 같은 구성 옵션이 포함됩니다.  

사용자 지정 클라이언트 설정을 만든 다음 컬렉션에 할당할 수 있습니다.  컬렉션의 멤버는 사용자 지정 설정을 갖도록 구성되며, 지정하는 순서대로(번호 순서대로) 적용된 여러 사용자 지정 클라이언트 설정을 만들 수 있습니다.  충돌하는 설정이 있는 경우 순서 번호가 가장 낮은 설정이 다른 설정을 재정의합니다.  

다음 다이어그램은 사용자 지정 클라이언트 설정을 만들고 적용하는 방법의 예를 보여 줍니다.  

 ![클라이언트 설정](media/ClientSettings.gif)  

 클라이언트 설정에 대한 자세한 내용은 다음을 참조하세요.  
                [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md) 및 [System Center Configuration Manager의 클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)

## <a name="managing-devices-without-the-configuration-manager-client"></a>Configuration Manager 클라이언트 없이 장치 관리  
 Configuration Manager는 클라이언트 소프트웨어를 설치하지 않았으며 Microsoft Intune을 통해 관리되지 않는 일부 장치를 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 온-프레미스 인프라로 모바일 장치 관리](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) 및 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

## <a name="user-based-management"></a>사용자 기반 관리  
 Active Directory Domain Services 사용자의 Configuration Manager 컬렉션입니다. 사용자 컬렉션을 사용할 경우 컬렉션의 멤버가 로그인하는 모든 컴퓨터에 소프트웨어를 설치하고, 배포하는 소프트웨어가 사용자의 기본 장치로 지정된 장치에만 설치되도록 **사용자 장치 선호도**를 구성할 수 있습니다. 사용자는 기본 장치를 하나 이상 사용할 수 있습니다.  

 사용자가 자신의 소프트웨어 배포 환경을 제어할 수 있는 방법 중 하나는 컴퓨터 클라이언트 인터페이스인 **소프트웨어 센터**를 사용하는 것입니다. 소프트웨어 센터는 클라이언트 컴퓨터에 자동으로 설치되며 사용자의 시작 메뉴에서 액세스할 수 있습니다. 소프트웨어 센터를 사용하면 사용자가 자신의 소프트웨어를 관리할 수 있고 다음 작업도 수행할 수 있습니다.  

-   소프트웨어 설치  

-   근무 외 시간에 자동으로 소프트웨어를 설치하도록 예약  

-   Configuration Manager가 자신의 장치에 소프트웨어를 설치할 수 있는 시간을 구성합니다.  

-   Configuration Manager에서 원격 제어를 사용하도록 설정한 경우 원격 제어의 액세스 설정 구성  

-   관리자가 전원 관리 옵션을 사용하도록 설정한 경우 이 옵션 구성  

 소프트웨어 센터의 링크를 사용하면 사용자가 소프트웨어를 탐색, 설치, 요청할 수 있는 **응용 프로그램 카탈로그**에 연결할 수 있습니다. 또한 응용 프로그램 카탈로그를 통해 사용자는 일부 기본 설정을 구성하고, 모바일 장치를 초기화하고, (이 구성을 허용하는 경우) 사용자 장치 선호도 대한 자신의 기본 장치를 지정할 수 있습니다.   

 응용 프로그램 카탈로그는 IIS에서 호스팅하는 웹 사이트이므로 사용자가 브라우저, 인트라넷 또는 인터넷에서도 직접 응용 프로그램 카탈로그에 액세스할 수 있습니다.  



<!--HONumber=Dec16_HO3-->


