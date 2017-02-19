---
title: "역할 기반 관리의 기본 사항 | Microsoft 문서"
description: "역할 기반 관리를 사용하여 Configuration Manager 및 관리하는 개체에 대한 관리 액세스를 제어합니다."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a2d6c3f-a4e4-4c19-b087-3caada480de9
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: a8cb3c9850b183eec156c37a181c04088b71805e
ms.openlocfilehash: 40837306816639ff8cea8930fec75b05edc5164a


---
# <a name="fundamentals-of-role-based-administration-for-system-center-configuration-manager"></a>System Center Configuration Manager의 역할 기반 관리 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 역할 기반 관리를 사용하여 Configuration Manager를 관리하는 데 필요한 액세스를 보호합니다. 또한 컬렉션, 배포, 사이트 등 관리하는 개체에 대한 액세스를 보호합니다. 이 항목에서 소개하는 개념을 파악하면 [System Center Configuration Manager용 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 수행할 수 있습니다.  

 역할 기반 관리 모델에서는 다음 항목을 사용하여 모든 사이트 및 사이트 설정에 대한 계층 구조 전체의 보안 액세스 설정을 중앙 집중식으로 정의하고 관리합니다.  

-   *보안 역할* - 관리자에게 할당되어 해당 관리자 또는 관리자 그룹에게 다양한 Configuration Manager 개체에 대한 권한을 제공하는 역할입니다. 예를 들어 클라이언트 설정을 만들거나 변경할 권한이 있습니다.  

-   *보안 범위* - 보안 범위에서는 Microsoft Office 2010을 설치하는 응용 프로그램과 같이 관리자가 관리해야 하는 개체의 특정 인스턴스를 그룹화하는 데 사용됩니다.  

-   *컬렉션* - 관리자가 관리할 수 있는 사용자 및 장치 리소스 그룹을 지정하는 데 사용됩니다.  

 보안 역할, 보안 범위 및 컬렉션을 적절히 함께 사용하여 조직의 요구 사항을 충족하는 관리 할당을 구분합니다. 함께 사용할 경우 Configuration Manager에서 사용자가 보고 관리하는 대상인 사용자의 관리 범위를 정의합니다.  

## <a name="benefits-of-role-based-administration"></a>역할 기반 관리의 이점  

-   사이트가 관리 경계로 사용되지 않습니다.  

-   계층 구조의 관리자를 만들면 해당 관리자에게 보안을 한 번만 할당하면 됩니다.  

-   모든 보안 할당이 복제되어 계층 전체에서 사용될 수 있습니다.  

-   일반적인 관리 작업을 할당하는 데 사용되는 기본 제공 보안 역할이 있습니다. 직접 사용자 지정 보안 역할을 만들어 특정 비즈니스 요구 사항을 지원할 수 있습니다.  

-   관리자에게 관리할 수 있는 권한이 있는 개체만 표시됩니다.  

-   관리 보안 작업을 감사할 수 있습니다.  

Configuration Manager에 대해 관리 보안을 디자인하고 구현할 때는 다음 방법에 따라 관리자의 *관리 범위*를 만듭니다.  

-   [보안 역할](#bkmk_Planroles)  

-   [컬렉션](#bkmk_planCol)  

-   [보안 범위](#bkmk_PlanScope)  


 관리 범위는 관리자가 Configuration Manager 콘솔에서 볼 수 있는 개체를 제어하고 해당 개체에 대한 사용자의 권한을 제어합니다. 역할 기반 관리 구성은 계층의 각 사이트에 글로벌 데이터로 복제된 다음 모든 관리 연결에 적용됩니다.  

> [!IMPORTANT]  
>  사이트 간 복제 지연으로 인해 사이트에서 역할 기반 관리의 변경 내용을 수신하지 못할 수 있습니다. 사이트 간 데이터베이스 복제를 모니터링하는 방법에 대한 내용은 [System Center Configuration Manager에서 사이트 간 데이터 전송](../../core/servers/manage/data-transfers-between-sites.md) 항목을 참조하세요.  

##  <a name="a-namebkmkplanrolesa-security-roles"></a><a name="bkmk_Planroles"></a> 보안 역할  
 보안 역할을 사용하여 관리자에게 보안 권한을 부여할 수 있습니다. 보안 역할은 관리자가 관리 작업을 수행할 수 있도록 관리자에게 할당하는 보안 권한을 그룹화한 것입니다. 이러한 보안 권한은 관리자가 수행할 수 있는 관리 작업뿐 아니라 특정 개체 유형에 부여되는 사용 권한을 정의합니다. 보안을 유지하는 가장 좋은 방법으로 최소 사용 권한을 제공하는 보안 역할을 할당하세요.  

 Configuration Manager에는 일반적인 관리 작업 그룹을 지원하는 몇 가지 보안 역할을 기본 제공합니다. 하지만 특정 비즈니스 요구 사항을 지원하도록 사용자만의 보안 역할을 사용자 지정하여 만들 수 있습니다. 기본 제공 보안 역할의 예:  

-   *전체 관리자*: Configuration Manager의 모든 권한을 부여합니다.  

-   *자산 관리자*는 Asset Intelligence 동기화 지점, Asset Intelligence 보고 클래스, 소프트웨어 인벤토리, 하드웨어 인벤토리 및 계량 규칙을 관리할 수 있는 권한을 부여합니다.  

-   *소프트웨어 업데이트 관리자*: 소프트웨어 업데이트를 정의 및 배포할 권한을 부여합니다. 이 역할과 연결된 관리자는 컬렉션, 소프트웨어 업데이트 그룹, 배포 및 템플릿을 만들 수 있습니다.  

> [!TIP]  
>  Configuration Manager 콘솔에서 기본 제공 보안 역할과 사용자가 만든 사용자 지정 보안 역할을 설명과 함께 볼 수 있습니다. 역할을 보려면 **관리** 작업 영역에서 **보안**을 확장하고 **보안 역할**을 선택합니다.  

 각 보안 역할마다 개체 유형별로 다른 사용 권한을 지정합니다. 예를 들어 *응용 프로그램 MMM* 보안 역할에는 응용 프로그램에 대한 승인, 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기/배포 및 보안 범위 설정 권한이 포함됩니다.

 기본 제공 보안 역할의 사용 권한을 변경할 수 없지만 역할을 복사한 후 변경하여 변경 내용을 새로운 사용자 지정 보안 역할로 저장할 수 있습니다. 또한 다른 계층 구조(예: 테스트 네트워크)에서 내보낸 보안 역할을 가져올 수도 있습니다. 보안 역할과 해당 권한을 검토하여 기본 제공 보안 역할을 사용할지, 아니면 사용자 지정 보안 역할을 만들어야 하는지 결정하세요.  

 ### <a name="to-help-you-plan-for-security-roles"></a>보안 역할을 계획하려면  

1.  관리자가 Configuration Manager에서 수행하는 작업을 식별합니다. 이러한 작업으로는 하나 이상의 관리 작업 그룹과 연관될 수 있습니다. 예를 들어 응용 프로그램 및 패키지 배포, 운영 체제 배포, 호환성을 위한 설정 배포, 사이트 및 보안 구성, 감사, 원격 컴퓨터 제어, 인벤토리 데이터 수집 등의 작업이 있습니다.  

2.  이러한 관리 작업을 하나 이상의 기본 제공 보안 역할에 매핑합니다.  

3.  일부 관리자가 여러 보안 역할의 작업을 수행하는 경우 작업을 결합한 새 보안 역할을 만들지 말고 여러 보안 역할을 해당 관리자에게 할당합니다.  

4.  파악한 작업이 기본 제공 보안 역할에 매핑되지 않으면 새 보안 역할을 만들어 테스트합니다.  

역할 기반 관리용 보안 역할을 만들고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md) 항목의 [사용자 지정 보안 역할 만들기](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole) 및 [보안 역할 구성](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)을 참조하세요.  

##  <a name="a-namebkmkplancola-collections"></a><a name="bkmk_planCol"></a> 컬렉션  
 컬렉션은 관리자가 보거나 관리할 수 있는 사용자 및 컴퓨터 리소스를 지정합니다. 예를 들어 응용 프로그램을 배포하거나 원격 제어를 실행하는 관리자의 경우 이러한 리소스를 포함하는 컬렉션에 대한 액세스 권한을 부여하는 보안 역할을 할당받아야 합니다. 사용자 또는 장치의 컬렉션을 선택할 수 있습니다.  

 컬렉션에 대한 자세한 내용은 [System Center Configuration Manager의 컬렉션 소개](../../core/clients/manage/collections/introduction-to-collections.md)를 참조하세요.  

 역할 기반 관리를 구성하기 전에 다음과 같은 이유로 새로운 컬렉션을 만들어야 하는지 확인합니다.  

-   업무별 분할: 예를 들어 서버와 워크스테이션의 컬렉션을 구분할 수 있습니다.  

-   지역적 구분: 예를 들어 북미와 유럽의 컬렉션을 구분할 수 있습니다.  

-   보안 요구 사항 및 비즈니스 프로세스: 예를 들어 프로덕션 컴퓨터와 테스트 컴퓨터의 컬렉션이 구분되어 있습니다.  

-   조직 구조별 구분: 예를 들어 각 사업부별로 컬렉션을 구분할 수 있습니다.  

역할 기반 관리용 컬렉션을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md) 항목의 [보안을 관리하도록 컬렉션 구성](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)을 참조하세요.  

##  <a name="a-namebkmkplanscopea-security-scopes"></a><a name="bkmk_PlanScope"></a> 보안 범위  
 보안 범위를 사용하여 관리자에게 보안 개체에 대한 액세스 권한을 제공할 수 있습니다. 보안 범위는 관리자에게 그룹으로 할당한 보안 개체의 명명된 집합입니다. 모든 보안 개체를 하나 이상의 보안 범위에 할당해야 합니다. Configuration Manager에는 두 개의 기본 제공 보안 범위가 있습니다.  

-   *모든* 기본 제공 보안 범위는 모든 범위에 대한 액세스 권한을 부여합니다. 이 보안 범위에 개체를 할당할 수 없습니다.  

-   *기본값* 기본 제공 보안 범위는 기본적으로 모든 개체에 사용됩니다. Configuration Manager를 처음 설치할 때 모든 개체가 이 보안 범위에 할당됩니다.  

관리자가 보고 관리할 수 있는 개체를 제한하려는 경우 자체 사용자 지정 보안 범위를 만들어 사용해야 합니다. 보안 범위는 계층 구조를 지원하지 않으며 중첩할 수 없습니다. 보안 범위는 다음을 포함하여 하나 이상의 개체 유형을 포함할 수 있습니다.  

-   경고 구독  

-   응용 프로그램  

-   부팅 이미지  

-   경계 그룹  

-   구성 항목  

-   사용자 지정 클라이언트 설정  

-   배포 지점과 배포 지점 그룹  

-   드라이버 패키지  

-   글로벌 조건  

-   마이그레이션 작업  

-   운영 체제 이미지  

-   운영 체제 설치 패키지  

-   패키지  

-   쿼리  

-   사이트  

-   소프트웨어 계량 규칙  

-   소프트웨어 업데이트 그룹  

-   소프트웨어 업데이트 패키지  

-   작업 순서 패키지  

-   Windows CE 장치 설정 항목 및 패키지  

보안 역할로만 보호되기 때문에 보안 범위에 포함할 수 없는 개체도 있습니다. 이러한 개체의 관리 권한은 사용할 수 있는 개체의 하위 집합으로 제한될 수 없습니다. 예를 들어 특정 사이트에만 사용되는 경계 그룹을 만드는 관리자가 있을 수 있습니다. 경계 개체는 보안 범위를 지원할 수 없으므로 이 관리자에게는 해당 사이트에 연결될 수 있는 경계에 대해서만 액세스 권한을 제공하는 보안 범위를 할당할 수 없습니다. 경계 개체가 보안 범위에 연결될 수 없으므로 경계 개체에 대한 액세스 권한을 포함하는 보안 역할을 사용자에게 할당하면 해당 사용자는 계층 내 모든 경계에 액세스할 수 있습니다.  

보안 범위로 제한할 수 없는 개체는 다음과 같습니다.  

-   Active Directory 포리스트  

-   관리자  

-   경고  

-   맬웨어 방지 프로그램 정책  

-   경계  

-   컴퓨터 연결  

-   기본 클라이언트 설정  

-   배포 템플릿  

-   장치 드라이버  

-   Exchange Server 커넥터  

-   사이트-사이트 간 마이그레이션 매핑  

-   모바일 장치 등록 프로필  

-   보안 역할  

-   보안 범위  

-   사이트 주소  

-   사이트 시스템 역할  

-   소프트웨어 타이틀  

-   소프트웨어 업데이트  

-   상태 메시지  

-   사용자 장치 선호도  

별도의 개체 인스턴스에 대한 액세스를 제한해야 하는 경우 보안 범위를 만듭니다. 예를 들면 다음과 같습니다.  

-   테스트 응용 프로그램은 제외하고 프로덕션 응용 프로그램만 볼 수 있는 관리자 그룹이 있는 경우 프로덕션 응용 프로그램에 대해 보안 범위를 만들고, 테스트 응용 프로그램에 대해 다른 보안 범위를 만듭니다.  

-   관리자별로 개체 유형의 일부 인스턴스에 대해 서로 다른 액세스 권한이 필요할 수 있습니다. 예를 들어 한 관리자 그룹에는 특정 소프트웨어 업데이트 그룹에 대해 읽기 권한이 필요하고, 다른 관리자 그룹에는 다른 소프트웨어 업데이트 그룹에 대해 수정 및 삭제 권한이 필요한 경우 해당 소프트웨어 업데이트 그룹에 대해 여러 보안 범위를 만듭니다.  

역할 기반 관리용 보안 범위를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope) 항목의 [개체에 대한 보안 범위 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.  



<!--HONumber=Jan17_HO5-->


