---
title: 컬렉션 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 컬렉션을 만들어 사용자 및 장치 그룹을 더 쉽게 관리합니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 1401a35e-4312-4d3b-8ceb-0abbb10d4f05
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 76796cdb56a7106ac709866a9df7c2a08bc6b7bc
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-collections-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 컬렉션을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

컬렉션은 사용자 또는 장치의 그룹입니다. 응용 프로그램 관리, 준수 설정 배포 또는 소프트웨어 업데이트 설치와 같은 작업에 컬렉션을 사용합니다. 또한 클라이언트 설정 그룹을 관리하는 데 컬렉션을 사용하거나 관리자가 액세스할 수 있는 리소스를 지정하기 위해 역할 기반 관리와 함께 컬렉션을 사용할 수 있습니다. Configuration Manager에는 여러 기본 제공 컬렉션이 포함되어 있습니다. 자세한 내용은 [System Center Configuration Manager의 컬렉션 소개](../../../../core/clients/manage/collections/introduction-to-collections.md)를 참조하세요.  

> [!NOTE]  
>  컬렉션에는 사용자 또는 장치 중 하나만 포함될 수 있습니다.  

 다음 표에서는 Configuration Manager의 컬렉션 멤버를 구성하는 데 사용할 수 있는 규칙이 나와 있습니다.  

|멤버 관리 규칙 유형|추가 정보|  
|--------------------------|----------------------|  
|직접 규칙|컬렉션에 추가할 사용자 또는 컴퓨터를 선택하는 데 사용합니다. 이 멤버 자격은 리소스를 Configuration Manager에서 제거하지 않을 경우 변경되지 않습니다. Configuration Manager에서 리소스를 검색했거나 리소스를 가져온 후에만 직접 규칙 컬렉션에 리소스를 추가할 수 있습니다. 직접 규칙 컬렉션은 수동으로 변경해야 하므로 쿼리 규칙 컬렉션보다 관리 오버헤드가 높습니다.|  
|쿼리 규칙|Configuration Manager에서 일정에 따라 실행하는 쿼리를 기반으로 하는 컬렉션의 멤버 자격을 동적으로 업데이트합니다. 예를 들어 Active Directory Domain Services에서 인적 자원 조직 구성 단위의 멤버인 사용자 컬렉션을 만들 수 있습니다. 이 컬렉션은 새 사용자가 인적 자원 조직 구성 단위에 추가되거나 구성 단위에서 제거될 때 자동으로 업데이트됩니다.<br /><br /> 컬렉션을 빌드하는 데 사용할 수 있는 예제 쿼리는 [System Center Configuration Manager에서 쿼리를 만드는 방법](../../../../core/servers/manage/create-queries.md)을 참조하세요.|  
|포함 컬렉션 규칙|Configuration Manager에 다른 컬렉션의 멤버를 포함할 수 있습니다. 현재 컬렉션의 멤버 자격은 포함된 컬렉션이 변경되면 일정에 따라 업데이트됩니다.<br /><br /> 컬렉션에 여러 포함 컬렉션 규칙을 추가할 수 있습니다.<br /> |  
|제외 컬렉션 규칙|제외 컬렉션 규칙을 사용하면 Configuration Manager 컬렉션에서 다른 컬렉션의 멤버를 제외할 수 있습니다. 현재 컬렉션의 멤버 자격은 제외된 컬렉션이 변경되면 일정에 따라 업데이트됩니다.<br /><br /> 컬렉션에 여러 제외 컬렉션 규칙을 추가할 수 있습니다. 컬렉션에 포함 컬렉션 및 제외 컬렉션 규칙이 모두 포함되어 있고 충돌이 있다면 제외 컬렉션 규칙이 우선합니다.<br />              **예제:** 하나의 포함 컬렉션 규칙과 하나의 제외 컬렉션 규칙이 있는 컬렉션을 만듭니다. 포함 컬렉션 규칙은 Dell 데스크톱의 컬렉션을 위한 것입니다. 제외 컬렉션은 RAM이 4GB보다 작은 컴퓨터의 컬렉션을 위한 것입니다. 새 컬렉션에는 RAM이 4GB 이상인 Dell 데스크톱이 포함됩니다.|  

 Configuration Manager에서 컬렉션을 만들려면 다음 절차를 따르세요. 이 사이트나 다른 Configuration Manager 사이트에서 만든 컬렉션을 가져올 수도 있습니다. 컬렉션을 내보내고 가져오는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 관리하는 방법](../../../../core/clients/manage/collections/manage-collections.md)을 참조하세요.  

 Linux 및 UNIX를 실행하는 컴퓨터를 위한 컬렉션을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md)을 참조하세요.  

##  <a name="BKMK_1"></a> 장치 컬렉션을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **장치 컬렉션**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **장치 컬렉션 만들기**를 선택합니다.  

4.  **일반** 페이지에서는 **이름** 및 **설명**을 제공합니다. 그런 다음 **제한 컬렉션**에서 **찾아보기**를 선택하여 제한 컬렉션을 선택합니다. 컬렉션에는 제한 컬렉션 멤버만 포함됩니다.  

5.  **장치 컬렉션 만들기 마법사**의 **멤버 관리 규칙** 페이지에 있는 **규칙 추가** 목록에서 이 컬렉션에 사용하려는 멤버 관리 규칙의 유형을 선택합니다. 각 컬렉션에 대해 여러 규칙을 구성할 수 있습니다.  

        
##### <a name="to-configure-a-direct-rule"></a>직접 규칙을 구성하려면  

1.  **직접 멤버 관리 규칙 만들기 마법사** 의 **리소스 검색**페이지에서 다음 정보를 지정합니다.  

-   **리소스 클래스**: 검색하여 컬렉션에 추가하려는 리소스의 유형을 선택합니다. 클라이언트 컴퓨터에서 반환된 인벤토리 데이터를 검색하려면 **시스템 리소스** 값에서 선택하거나 알 수 없는 컴퓨터에서 반환된 값에서 선택하려면 **알 수 없는 컴퓨터** 를 선택합니다.  

-   **특성 이름**: 검색할 선택된 리소스 클래스와 연결된 특성을 선택합니다. 예를 들어 NetBIOS 이름으로 컴퓨터를 선택하려는 경우 **리소스 클래스** 목록에서 **시스템 리소스** 를 선택하고 **특성 이름** 목록에서 **NetBIOS 이름** 을 선택합니다.  

-   **사용되지 않음으로 표시된 리소스 제외** - 클라이언트 컴퓨터가 사용되지 않음으로 표시되는 경우 검색 결과에 이 값을 포함하지 마세요.  

-   **Configuration Manager 클라이언트가 설치되지 않은 리소스 제외** - 검색 결과에 표시되지 않습니다.  

-   **값:** 선택한 특성 이름을 검색하려는 값을 입력합니다. 백분율 문자 **%** 를 와일드 카드로 사용할 수 있습니다. 예를 들어 "M"으로 시작하는 NetBIOS 이름을 가진 컴퓨터를 검색하려면 이 필드에 **M%** 를 입력합니다.  

2.  **리소스 선택** 페이지의 **리소스** 목록에서 컬렉션에 추가하려는 리소스를 선택하고 **다음**을 선택합니다.  


##### <a name="to-configure-a-query-rule"></a>쿼리 규칙을 구성하려면  

1.  **쿼리 규칙 속성** 대화 상자에서 다음 정보를 지정합니다.  

-   **이름**: 고유 이름을 지정합니다.  

-   **쿼리 문 가져오기** – 컬렉션에 대한 쿼리 규칙으로 사용할 [Configuration Manager 쿼리](../../../../core/servers/manage/create-queries.md)를 선택할 수 있는 **쿼리 찾아보기** 대화 상자를 엽니다.   

-   **리소스 클래스**: 목록에서 검색하여 컬렉션에 추가하려는 리소스의 유형을 선택합니다. 클라이언트 컴퓨터에서 반환된 인벤토리 데이터를 검색하려면 **시스템 리소스** 값에서 값을 선택하거나 알 수 없는 컴퓨터에서 반환된 값에서 선택하려면 **알 수 없는 컴퓨터** 를 선택합니다.  

-   **쿼리 문 편집** – 컬렉션에 대한 규칙으로 사용할 쿼리를 작성할 수 있는 **쿼리 문 속성** 대화 상자를 엽니다. 쿼리에 대한 자세한 내용은 [System Center Configuration Manager에 대한 쿼리 기술 참조](../../../../core/servers/manage/queries-technical-reference.md)를 참조하세요.  

    
##### <a name="to-configure-an-include-collection-rule"></a>포함 컬렉션 규칙을 구성하려면  

**컬렉션 선택** 대화 상자에서 새 컬렉션에 포함하려는 컬렉션을 선택하고 **확인**을 선택합니다.  

##### <a name="to-configure-an-exclude-collection-rule"></a>제외 컬렉션 규칙을 구성하려면  

**컬렉션 선택** 대화 상자에서 새 컬렉션에서 제외하려는 컬렉션을 선택하고 **확인**을 선택합니다.  

-   **이 컬렉션에 대한 증분 업데이트 사용** – 전체 컬렉션 평가와 별개로 이전 컬렉션 평가에서 새로 추가되거나 변경된 리소스만 주기적으로 검색 및 업데이트하려면 이 옵션을 선택합니다. 증분 업데이트는 10분 간격으로 발생합니다.  

> [!IMPORTANT]  
>  다음 클래스를 사용하는 쿼리 규칙으로 구성된 컬렉션은 증분 업데이트를 지원하지 않습니다.  
>   
> -   SMS_G_System_CollectedFile  
> -   SMS_G_System_LastSoftwareScan  
> -   SMS_G_System_AppClientState  
> -   SMS_G_System_DCMDeploymentState  
> -   SMS_G_System_DCMDeploymentErrorAssetDetails  
> -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
> -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
> -   SMS_G_User_DCMDeploymentCompliantAssetDetails(사용자 컬렉션 전용)  
> -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails(사용자 컬렉션 전용)  
> -   SMS_G_System_SoftwareUsageData  
> -   SMS_G_System_CI_ComplianceState  
> -   SMS_G_System_EndpointProtectionStatus  
> -   SMS_GH_System_*  
> -   SMS_GEH_System_*  

-   **이 컬렉션에 대한 전체 업데이트 예약** – 컬렉션 멤버 자격에 대한 정규 전체 평가를 예약합니다.  

6.  새 컬렉션을 만드는 마법사를 완료합니다. 새 컬렉션이 **자산 및 준수** 작업 영역의 **장치 컬렉션** 노드에 표시됩니다.  

> [!NOTE]  
>  컬렉션 멤버를 확인하려면 Configuration Manager 콘솔을 새로 고치거나 다시 로드해야 합니다. 그러나 첫 번째 예약된 업데이트 후까지 또는 컬렉션에 대해 **멤버 자격 업데이트**를 수동으로 선택한 경우 멤버가 컬렉션에 표시되지 않습니다. 컬렉션 업데이트를 완료하는 데 몇 분 정도 걸릴 수 있습니다.  

##  <a name="BKMK_2"></a> 사용자 컬렉션을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **사용자 컬렉션**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사용자 컬렉션 만들기**를 선택합니다.  

4.  마법사의 **일반** 페이지에서는 **이름** 및 **설명**을 제공합니다. 그런 다음 **제한 컬렉션**에서 **찾아보기**를 선택하여 제한 컬렉션을 선택합니다. 컬렉션에는 제한 컬렉션 멤버만 포함됩니다.  

5.  **멤버 관리 규칙** 페이지에서 다음을 지정합니다.  

    -   **규칙 추가** 목록에서 이 컬렉션에 대해 사용하려는 멤버 관리 규칙의 유형을 선택합니다. 각 컬렉션에 대해 여러 규칙을 구성할 수 있습니다.  

##### <a name="to-configure-a-direct-rule"></a>직접 규칙을 구성하려면  

1.  **직접 멤버 관리 규칙 만들기** 마법사의 **리소스 검색** 페이지에서 다음을 지정합니다.  

-   **리소스 클래스**: 검색하여 컬렉션에 추가하려는 리소스의 유형을 선택합니다. Configuration Manager에서 수집된 사용자 정보를 검색하도록 **사용자 리소스** 값에서 선택하거나 Configuration Manager에서 수집된 사용자 그룹 정보를 검색하도록 **사용자 그룹 리소스**를 선택합니다.  

-   **특성 이름**: 목록에서 검색할 리소스 클래스와 연결된 특성을 선택합니다. 예를 들어 사용자를 OU(조직 구성 단위) 이름으로 선택하려는 경우 **리소스 클래스** 목록의 **사용자 리소스** 를 선택하고 **특성 이름** 목록의 **사용자 OU 이름** 을 선택합니다.  

-   **값:** 검색하려는 값을 입력합니다. 백분율 문자 **%** 를 와일드 카드로 사용할 수 있습니다. 예를 들어 Contoso OU에서 사용자를 검색하려면 이 필드에 **Contoso**를 입력합니다.  

2.  **리소스 선택** 페이지의 **리소스** 목록에서 컬렉션에 추가하려는 리소스를 선택합니다.  

##### <a name="to-configure-a-query-rule"></a>쿼리 규칙을 구성하려면  

1.  **쿼리 규칙 속성** 대화 상자에 다음을 입력합니다.  

-   **이름**: 고유 이름입니다.  

-   **쿼리 문 가져오기** – 컬렉션에 대한 쿼리 규칙으로 사용할 [Configuration Manager 쿼리](../../../../core/servers/manage/queries-technical-reference.md)를 선택할 수 있는 **쿼리 찾아보기** 대화 상자를 엽니다.  

-   **리소스 클래스**: 검색하여 컬렉션에 추가하려는 리소스의 유형을 선택합니다. Configuration Manager에서 수집된 사용자 정보를 검색하도록 **사용자 리소스** 값에서 선택하거나 Configuration Manager에서 수집된 사용자 그룹 정보를 검색하도록 **사용자 그룹 리소스**를 선택합니다.  

-   **쿼리 문 편집** – 컬렉션에 대한 규칙으로 사용할 [쿼리를 작성](../../../../core/servers/manage/queries-technical-reference.md)할 수 있는 **쿼리 문 속성** 대화 상자를 엽니다.  

##### <a name="to-configure-an-include-collection-rule"></a>포함 컬렉션 규칙을 구성하려면  

**컬렉션 선택** 대화 상자에서 새 컬렉션에 포함하려는 컬렉션을 선택하고 **확인**을 선택합니다.  

##### <a name="to-configure-an-exclude-collection-rule"></a>제외 컬렉션 규칙을 구성하려면  

**컬렉션 선택** 대화 상자에서 새 컬렉션에서 제외하려는 컬렉션을 선택하고 **확인**을 선택합니다.  


-   **이 컬렉션에 대한 증분 업데이트 사용** – 전체 컬렉션 평가와 별개로 이전 컬렉션 평가에서 새로 추가되거나 변경된 리소스만 주기적으로 검색 및 업데이트하려면 이 옵션을 선택합니다. 증분 업데이트는 10분 간격으로 발생합니다.  

> [!IMPORTANT]  
>  다음 클래스를 사용하는 쿼리 규칙으로 구성된 컬렉션은 증분 업데이트를 지원하지 않습니다.  
>   
> -   SMS_G_System_CollectedFile  
> -   SMS_G_System_LastSoftwareScan  
> -   SMS_G_System_AppClientState  
> -   SMS_G_System_DCMDeploymentState  
> -   SMS_G_System_DCMDeploymentErrorAssetDetails  
> -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
> -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
> -   SMS_G_User_DCMDeploymentCompliantAssetDetails(사용자 컬렉션 전용)  
> -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails(사용자 컬렉션 전용)  
> -   SMS_G_System_SoftwareUsageData  
> -   SMS_G_System_CI_ComplianceState  
> -   SMS_G_System_EndpointProtectionStatus  
> -   SMS_GH_System_*  
> -   SMS_GEH_System_*  

-   **이 컬렉션에 대한 전체 업데이트 예약** – 컬렉션 멤버 자격에 대한 정규 전체 평가를 예약합니다.  

6.  마법사를 완료합니다. 새 컬렉션이 **자산 및 준수** 작업 영역의 **사용자 컬렉션** 노드에 표시됩니다.  

> [!NOTE]  
>  컬렉션 멤버를 확인하려면 Configuration Manager 콘솔을 새로 고치거나 다시 로드해야 합니다. 그러나 첫 번째 예약된 업데이트 후 또는 컬렉션에 대해 **멤버 자격 업데이트** 를 수동으로 선택할 때까지는 멤버가 컬렉션에 표시되지 않습니다. 컬렉션 업데이트를 완료하는 데 몇 분 정도 걸릴 수 있습니다.  

##  <a name="BKMK_3"></a> 컬렉션을 가져오려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **사용자 컬렉션** 또는 **장치 컬렉션**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **컬렉션 가져오기**를 선택합니다.  

4.  **컬렉션 가져오기 마법사**의 **일반** 페이지에서 **다음**을 선택합니다.  

5.  **MOF 파일 이름** 페이지에서 **찾아보기**를 선택한 다음 가져오려는 컬렉션 정보가 포함된 MOF 파일을 찾습니다.  

    > [!NOTE]  
    >  가져올 파일은 이와 동일한 버전의 Configuration Manager를 실행하는 사이트에서 내보냈어야 합니다. 컬렉션을 내보내는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 관리하는 방법](../../../../core/clients/manage/collections/manage-collections.md)을 참조하세요.  

6.  컬렉션을 가져오는 마법사를 완료합니다. 새 컬렉션이 **자산 및 준수** 작업 영역의 **사용자 컬렉션** 또는 **장치 컬렉션** 노드에 표시됩니다. 새로 가져온 컬렉션에 대한 컬렉션 멤버를 확인하려면 Configuration Manager 콘솔을 새로 고치거나 다시 로드합니다.  
