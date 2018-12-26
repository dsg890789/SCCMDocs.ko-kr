---
title: 디바이스 관리의 기본 사항
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 디바이스를 관리하는 방법을 알아봅니다.
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 8d5fe709f403676c36d77e23e3ebe40a66101a44
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32340288"
---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 디바이스 관리의 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

넓은 의미에서 볼 때 System Center Configuration Manager는 다음 두 가지 범주의 디바이스를 관리할 수 있습니다.

-   *클라이언트*는 Configuration Manager 클라이언트 소프트웨어를 설치하는 워크스테이션, 랩톱, 서버, 모바일 장치 등의 장치입니다. 하드웨어 인벤토리 등의 일부 관리 기능을 사용하려면 이 클라이언트 소프트웨어가 필요합니다.  

-   *관리되는 장치*는 *클라이언트*를 포함할 수 있지만 일반적으로 Configuration Manager 클라이언트 소프트웨어가 설치되지 않은 모바일 장치입니다. 이런 디바이스에서는 Intune 또는 Configuration Manager의 기본 제공 온-프레미스 모바일 디바이스 관리를 사용하여 관리합니다.

클라이언트 유형뿐 아니라 사용자를 기준으로 하여 디바이스를 그룹화하고 식별할 수도 있습니다.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트를 사용하여 디바이스 관리

Configuration Manager 클라이언트 소프트웨어를 사용하여 디바이스를 관리하는 방법에는 두 가지가 있습니다. 첫 번째 방법은 네트워크에서 디바이스를 검색한 다음 해당 디바이스에 클라이언트 소프트웨어를 배포하는 것입니다. 다른 방법은 클라이언트 소프트웨어를 새 컴퓨터에 수동으로 설치한 다음 해당 컴퓨터가 네트워크에 연결할 때 사이트에 가입시키는 것입니다. 클라이언트 소프트웨어가 설치되지 않은 디바이스를 검색하려면 기본 제공 검색 방법 중 하나 이상을 실행합니다. 디바이스를 검색한 후에는 몇 가지 방법 중 하나를 사용하여 클라이언트 소프트웨어를 설치합니다. 검색에 대한 자세한 내용은 [System Center Configuration Manager에 대한 검색 실행](../../core/servers/deploy/configure/run-discovery.md)을 참조하세요.  

 Configuration Manager 클라이언트 소프트웨어를 실행할 수 있는 디바이스를 검색한 후 여러 방법 중 하나를 사용하여 소프트웨어를 설치할 수 있습니다. 소프트웨어를 설치하여 클라이언트를 기본 사이트에 할당한 후에는 디바이스 관리를 시작할 수 있습니다.  일반적인 설치 방법은 다음과 같습니다.

 - 클라이언트 강제 설치

 - 소프트웨어 업데이트 기반 설치

 - 그룹 정책

 - 컴퓨터에 수동 설치
 - 배포하는 운영 체제 이미지의 일부로 클라이언트 포함  


 클라이언트를 설치한 후에 컬렉션을 사용하여 디바이스 관리의 작업을 간소화할 수 있습니다. 컬렉션은 그룹으로 관리할 수 있도록 만드는 디바이스나 사용자의 그룹입니다. 예를 들어 Configuration Manager가 등록하는 모든 모바일 디바이스에 모바일 디바이스 응용 프로그램을 설치할 수 있습니다. 이 경우 모든 모바일 디바이스 컬렉션을 사용할 수 있습니다.  

 자세한 내용은 다음 항목을 참조하세요.  

-   [System Center Configuration Manager에 대한 장치 관리 솔루션 선택](../../core/plan-design/choose-a-device-management-solution.md)  

-   [System Center Configuration Manager의 클라이언트 설치 방법](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [System Center Configuration Manager의 컬렉션 소개](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>클라이언트 설정  
 Configuration Manager를 처음 설치하면 계층의 모든 클라이언트가 기본 클라이언트 설정을 사용하여 구성됩니다. 기본 클라이언트 설정은 사용자가 변경할 수 있습니다. 이러한 클라이언트 설정에는 다음 구성 옵션이 포함됩니다.

 -  디바이스가 사이트와 통신하는 빈도

 -  클라이언트가 소프트웨어 업데이트 및 기타 관리 작업에 대해 설정되는지 여부

 -  사용자가 Configuration Manager에서 관리되도록 모바일 디바이스를 등록할 수 있는지 여부  

사용자 지정 클라이언트 설정을 만든 다음 컬렉션에 할당할 수 있습니다.  컬렉션의 멤버는 사용자 지정 설정을 갖도록 구성되며, 지정하는 순서대로(번호 순서대로) 적용된 여러 사용자 지정 클라이언트 설정을 만들 수 있습니다.  충돌하는 설정이 있는 경우 순서 번호가 가장 낮은 설정이 다른 설정을 재정의합니다.  

다음 다이어그램은 사용자 지정 클라이언트 설정을 만들고 적용하는 방법의 예를 보여 줍니다.  

 ![클라이언트 설정](media/ClientSettings.gif)  

 클라이언트 설정에 대한 자세한 내용은 다음을 참조하세요.  
                [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md) 및 [System Center Configuration Manager의 클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)

## <a name="managing-devices-without-the-configuration-manager-client"></a>Configuration Manager 클라이언트 없이 디바이스 관리  
 Configuration Manager는 클라이언트 소프트웨어를 설치하지 않았으며 Intune을 통해 관리되지 않는 일부 디바이스를 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 온-프레미스 인프라로 모바일 디바이스 관리](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) 및 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

## <a name="user-based-management"></a>사용자 기반 관리  
 Configuration Manager는 Active Directory Domain Services 사용자의 컬렉션을 지원합니다. 사용자 컬렉션을 사용하면 컬렉션의 멤버가 사용하는 모든 컴퓨터에 소프트웨어를 설치할 수 있습니다. 배포하는 소프트웨어가 사용자의 기본 디바이스로 지정된 디바이스에만 설치되도록 하려면 사용자 디바이스 선호도를 설정합니다. 사용자는 기본 디바이스를 하나 이상 사용할 수 있습니다.  

 사용자가 소프트웨어 배포 환경을 제어할 수는 방법 중 하나는 **소프트웨어 센터** 클라이언트 인터페이스를 사용하는 것입니다. **소프트웨어 센터**는 클라이언트 컴퓨터에 자동으로 설치되며 **시작** 메뉴에서 실행할 수 있습니다. **소프트웨어 센터**를 사용하면 사용자가 자신의 소프트웨어를 관리하고 다음 작업을 수행할 수 있습니다.  

-   소프트웨어를 설치합니다.  

-   근무 외 시간에 자동으로 소프트웨어를 설치하도록 예약합니다.  

-   Configuration Manager가 디바이스에 소프트웨어를 설치할 수 있는 시간을 구성합니다.  

-   Configuration Manager에서 원격 제어가 설정된 경우 원격 제어의 액세스 설정을 구성합니다.  

-   관리자가 전원 관리 옵션을 설정하는 경우 이 옵션을 구성합니다.  


 **소프트웨어 센터**의 링크를 사용하면 사용자가 소프트웨어를 탐색, 설치, 요청할 수 있는 **응용 프로그램 카탈로그**에 연결할 수 있습니다. **응용 프로그램 카탈로그**는 기본 설정을 구성하고, 모바일 장치를 초기화하고, 설정된 경우 사용자 장치 선호도에 대한 기본 장치를 지정하는 데에도 사용합니다.   

 또한 사용자가 브라우저 인트라넷이나 인터넷 세션을 통해 **애플리케이션 카탈로그**에 액세스할 수도 있습니다.  
