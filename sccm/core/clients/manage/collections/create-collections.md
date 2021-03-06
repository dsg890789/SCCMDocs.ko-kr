---
title: 컬렉션 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 컬렉션을 만들어 사용자 및 디바이스 그룹을 더 쉽게 관리할 수 있습니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 1401a35e-4312-4d3b-8ceb-0abbb10d4f05
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3fabbb774b1bf4d6144b59dea75a61207304557f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824472"
---
# <a name="how-to-create-collections-in-configuration-manager"></a>Configuration Manager에서 컬렉션을 만드는 방법

*적용 대상: Configuration Manager(현재 분기)*

컬렉션은 사용자 또는 디바이스의 그룹입니다. 애플리케이션 관리, 준수 설정 배포 또는 소프트웨어 업데이트 설치와 같은 작업에 컬렉션을 사용합니다. 또한 클라이언트 설정 그룹을 관리하는 데 컬렉션을 사용하거나 관리자가 액세스할 수 있는 리소스를 지정하기 위해 역할 기반 관리와 함께 컬렉션을 사용할 수 있습니다. Configuration Manager에는 여러 기본 제공 컬렉션이 포함되어 있습니다. 자세한 내용은 [컬렉션 소개](/sccm/core/clients/manage/collections/introduction-to-collections)를 참조하세요.  

> [!NOTE]  
> 컬렉션에는 사용자 또는 디바이스 중 하나만 포함될 수 있습니다.  


이 문서의 정보는 Configuration Manager에서 컬렉션을 만드는 데 유용할 수 있습니다. 현재 Configuration Manager 사이트 또는 다른 사이트에서 만든 컬렉션을 가져올 수도 있습니다. 컬렉션 내보내기 및 가져오기 방법에 대한 자세한 내용은 [컬렉션 관리 방법](/sccm/core/clients/manage/collections/manage-collections)을 참조하세요.  


## <a name="collection-rules"></a>컬렉션 규칙

Configuration Manager의 컬렉션 구성원을 구성하는 데 사용할 수 있는 여러 유형의 규칙이 있습니다.  


### <a name="direct-rule"></a>직접 규칙

직접 규칙은 컬렉션에 추가할 사용자 또는 컴퓨터를 선택하는 데 사용합니다. 해당 멤버 자격은 리소스를 Configuration Manager에서 제거하지 않을 경우 변경되지 않습니다. 직접 규칙 컬렉션에 리소스를 추가하려면 먼저 Configuration Manager에서 리소스를 검색했거나 리소스를 가져와야 합니다. 직접 규칙 컬렉션은 수동으로 변경해야 하므로 쿼리 규칙 컬렉션보다 관리 오버헤드가 높습니다.


### <a name="query-rule"></a>쿼리 규칙

Configuration Manager에서 일정에 따라 실행하는 쿼리를 기반으로 하는 컬렉션의 멤버 자격을 동적으로 업데이트합니다. 예를 들어 Active Directory Domain Services에서 인적 자원 조직 구성 단위의 멤버인 사용자 컬렉션을 만들 수 있습니다. 이 컬렉션은 새 사용자가 인적 자원 조직 구성 단위에 추가되거나 구성 단위에서 제거될 때 자동으로 업데이트됩니다.

컬렉션을 빌드하는 데 사용할 수 있는 예제 쿼리는 [쿼리 생성 방법](/sccm/core/servers/manage/create-queries)을 참조하세요.


### <a name="device-category-rule"></a>디바이스 범주 규칙

디바이스 범주를 디바이스 컬렉션과 연결하여 더욱 쉽게 디바이스를 관리할 수 있습니다. 

자세한 내용은 [디바이스를 컬렉션으로 자동 범주화](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections)를 참조하세요.<!-- SCCMDocs issue 552 -->


### <a name="include-collection-rule"></a>포함 컬렉션 규칙

Configuration Manager 컬렉션에 다른 컬렉션의 멤버를 포함합니다. 포함된 컬렉션이 변경되면 Configuration Manager에서 일정에 따라 현재 컬렉션의 멤버 자격을 업데이트합니다.

컬렉션에 여러 포함 컬렉션 규칙을 추가할 수 있습니다.


### <a name="exclude-collection-rule"></a>제외 컬렉션 규칙

제외 컬렉션 규칙을 사용하면 한 구성 관리자 컬렉션에서 다른 컬렉션의 구성원을 제외할 수 있습니다. 제외된 컬렉션이 변경되면 Configuration Manager에서 일정에 따라 현재 컬렉션의 멤버 자격을 업데이트합니다.

컬렉션에 여러 제외 컬렉션 규칙을 추가할 수 있습니다. 컬렉션에 포함 컬렉션 및 제외 컬렉션 규칙이 모두 포함되어 있고 충돌이 있다면 제외 컬렉션 규칙이 우선합니다.

#### <a name="example"></a>예제
하나의 포함 컬렉션 규칙과 하나의 제외 컬렉션 규칙이 있는 컬렉션을 만듭니다. 포함 컬렉션 규칙은 Dell 데스크톱의 컬렉션을 위한 것입니다. 제외 컬렉션은 RAM이 4GB보다 작은 컴퓨터의 컬렉션을 위한 것입니다. 새 컬렉션에는 RAM이 4GB 이상인 Dell 데스크톱이 포함되어 있습니다.



## <a name="bkmk_create"></a> 컬렉션 만들기  

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다.  

    - ‘디바이스 컬렉션’을 만들려면 **디바이스 컬렉션** 노드를 선택합니다.  그런 다음, 리본 **홈** 탭의 **만들기** 그룹에서 **디바이스 컬렉션 만들기**를 선택합니다.  

    - ‘사용자 컬렉션’을 만들려면 **사용자 컬렉션** 노드를 선택합니다.  그런 다음, 리본 **홈** 탭의 **만들기** 그룹에서 **사용자 컬렉션 만들기**를 선택합니다.  

2. 마법사의 **일반** 페이지에 **이름** 및 **설명**을 입력합니다. **제한 컬렉션** 섹션에서 **검색**, 제한 컬렉션을 차례로 선택합니다. 만들고 있는 컬렉션에는 제한 컬렉션 구성원만 포함됩니다.  

4. **규칙 추가** 목록의 **멤버 관리 규칙** 페이지에서 이 컬렉션에 대해 사용하려는 멤버 관리 규칙의 유형을 선택합니다. 각 컬렉션에 대해 여러 규칙을 구성할 수 있습니다. 각 규칙의 구성은 다릅니다. 각 규칙 구성에 대한 자세한 내용은 이 문서의 다음 섹션을 참조하세요.  
    - [직접 규칙](#bkmk-direct)
    - [쿼리 규칙](#bkmk-query)
    - [디바이스 범주 규칙](#bkmk-category)
    - [포함 컬렉션 규칙](#bkmk-include)
    - [제외 컬렉션 규칙](#bkmk-exclude)

5. 또한 **멤버 관리 규칙** 페이지에서 다음 설정을 검토합니다.

    - **이 컬렉션에 대해 증분 업데이트 사용**: 이 옵션을 선택하면 이전 컬렉션 평가에서 새 리소스 또는 변경된 리소스만 주기적으로 검색하고 업데이트할 수 있습니다. 이 프로세스는 전체 컬렉션 평가와는 관계없습니다. 기본적으로 증분 업데이트는 5분 간격으로 발생합니다.  

        > [!IMPORTANT]  
        >  다음 클래스를 사용하는 쿼리 규칙이 포함된 컬렉션은 증분 업데이트를 지원하지 않습니다.  
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

    - **이 컬렉션에 대한 전체 업데이트 예약**: 컬렉션 멤버 자격에 대한 정규 전체 평가를 예약합니다.  

        버전 1810부터는 컬렉션 평가 동작의 이러한 변경 내용이 사이트 성능을 개선할 수 있습니다.<!--3607726-->  

        - 이전에 쿼리 기반 컬렉션에서 일정을 구성한 경우 사이트는 컬렉션 설정 **이 컬렉션에 대한 전체 업데이트 예약**을 사용하도록 설정했는지 여부에 관계없이 쿼리를 계속 평가합니다. 일정을 완전히 사용하지 않으려면 일정을 **없음**으로 변경해야 했습니다.

            이제 이 설정을 사용하지 않도록 설정하면 사이트가 일정을 지웁니다. 컬렉션 평가 일정을 지정하려면 **이 컬렉션에 대한 전체 업데이트 예약** 옵션을 사용하도록 설정합니다.  

            사이트를 업데이트할 때 일정을 지정한 기존 컬렉션의 경우 사이트는 **이 컬렉션에 대한 전체 업데이트 예약** 옵션을 사용하도록 설정합니다. 이 구성은 사용자의 의도와 다를 수 있지만 사이트를 업데이트하기 전에 계획한 실제 동작이었습니다. 일정에 따라 컬렉션을 평가하는 사이트를 중지하려면 이 옵션을 사용하지 않도록 설정합니다.  

        - **모든 시스템** 같은 기본 제공 컬렉션의 평가를 사용하지 않도록 설정할 수 없지만, 현재 일정을 구성할 수는 있습니다. 이 동작을 사용하면 요구 사항을 충족하는 시간에 이 작업을 사용자 지정할 수 있습니다. 

            > [!TIP]  
            > 기본 제공 컬렉션에서 사용자 지정 일정의 **시간**만 변경하세요. **되풀이 패턴**은 변경하지 마세요. 향후 반복은 특정 되풀이 패턴을 적용할 수 있습니다.  

6. 새 컬렉션을 만드는 마법사를 완료합니다. 새 컬렉션이 **자산 및 준수** 작업 영역의 **디바이스 컬렉션** 노드에 표시됩니다.  

> [!NOTE]  
> 컬렉션 멤버를 확인하려면 Configuration Manager 콘솔을 새로 고치거나 다시 로드해야 합니다. 첫 번째 예약 업데이트가 끝날 때까지는 컬렉션에 표시되지 않습니다. 또한 컬렉션에 대한  **멤버 자격 업데이트**를 수동으로 선택할 수도 있습니다. 컬렉션 업데이트를 완료하는 데 몇 분 정도 걸릴 수 있습니다.  

        
### <a name="bkmk-direct"></a> 직접 규칙 구성  

1. **직접 멤버 관리 규칙 만들기 마법사** 의 **리소스 검색**페이지에서 다음 정보를 지정합니다.  

    - **리소스 클래스**: 목록에서 검색하여 컬렉션에 추가하려는 리소스의 유형을 선택합니다. 예를 들면 다음과 같습니다.
        - **시스템 리소스**: 클라이언트 컴퓨터에서 반환된 인벤토리 데이터를 검색합니다.
        - **알 수 없는 컴퓨터**: 알 수 없는 컴퓨터에서 반환된 값 중에서 선택합니다.
        - **사용자 리소스**: Configuration Manager에서 수집된 사용자 정보를 검색합니다.
        - **사용자 그룹 리소스**: Configuration Manager에서 수집된 사용자 그룹 정보를 검색합니다.

    - **특성 이름**: 검색할 선택된 리소스 클래스와 연결된 특성을 선택합니다. 예를 들면 다음과 같습니다.  

        - NetBIOS 이름으로 컴퓨터를 선택하려는 경우 **리소스 클래스**목록에서 **시스템 리소스**를 선택하고 **특성 이름** 목록에서 **NetBIOS 이름**을 선택합니다.  

        - 사용자를 OU(조직 구성 단위) 이름으로 선택하려는 경우 **리소스 클래스** 목록에서 **사용자 리소스**를 선택하고 **특성 이름** 목록에서 **사용자 OU 이름**을 선택합니다.  

    - **사용되지 않음으로 표시된 리소스 제외**: 클라이언트 컴퓨터가 사용되지 않음으로 표시되는 경우 검색 결과에서 이 값을 포함하지 마세요.  

    - **Configuration Manager 클라이언트가 설치되지 않은 리소스 제외**: 이러한 리소스는 검색 결과에 표시되지 않습니다.  

    - **값**: 선택한 특성 이름을 검색하려면 값을 입력합니다. 백분율 문자(%)를 와일드카드로 사용합니다. 예를 들면 다음과 같습니다.  
        - “M”으로 시작하는 NetBIOS 이름을 가진 컴퓨터를 검색하려면 이 필드에 **M%** 를 입력합니다.  
        - Contoso OU에서 사용자를 검색하려면 이 필드에 **Contoso**를 입력합니다.

2. **리소스 선택** 페이지의 **리소스** 목록에서 컬렉션에 추가하려는 리소스를 선택하고 **다음**을 선택합니다.  


### <a name="bkmk-query"></a> 쿼리 규칙 구성  

**쿼리 규칙 속성** 대화 상자에서 다음 정보를 지정합니다.  

- **이름**: 쿼리의 고유 이름을 지정합니다.  

- **쿼리 문 가져오기**: **쿼리 찾아보기** 대화 상자가 열립니다. 컬렉션에 대한 쿼리 규칙으로 사용할 [Configuration Manager 쿼리](/sccm/core/servers/manage/create-queries)를 선택합니다.   

- **리소스 클래스**: 목록에서 검색하여 컬렉션에 추가하려는 리소스의 유형을 선택합니다. 클라이언트 컴퓨터에서 반환된 인벤토리 데이터를 검색하려면 **시스템 리소스**에서 값을 선택하고, 알 수 없는 컴퓨터에서 반환된 값 중에서 선택하려면 **알 수 없는 컴퓨터**에서 값을 선택합니다.  

- **쿼리 문 편집**: 컬렉션에 대한 규칙으로 사용할 쿼리를 작성할 수 있는 **쿼리 문 속성** 대화 상자가 열립니다. 쿼리에 대한 자세한 내용은 [쿼리 소개](/sccm/core/servers/manage/introduction-to-queries)를 참조하세요.  


### <a name="bkmk-category"></a> 디바이스 범주 규칙

다음 작업은 **디바이스 범주 선택** 창에서 수행할 수 있습니다.

- **만들기**: 이름을 지정하여 새 범주를 만듭니다.
- **이름 바꾸기**: 선택한 범주의 이름을 바꿉니다.
- **삭제**: 하나 이상의 범주를 선택하고 이 작업을 사용하여 목록에서 제거합니다.

자세한 내용은 [디바이스를 컬렉션으로 자동 범주화](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections)를 참조하세요.<!-- SCCMDocs issue 552 -->


### <a name="bkmk-include"></a> 포함 컬렉션 규칙 구성  

**컬렉션 선택** 대화 상자에서 새 컬렉션에 포함하려는 컬렉션을 선택한 다음, **확인**을 선택합니다.  


### <a name="bkmk-exclude"></a> 제외 컬렉션 규칙 구성  

**컬렉션 선택** 대화 상자에서 새 컬렉션에서 제외하려는 컬렉션을 선택한 다음, **확인**을 선택합니다.  



## <a name="bkmk_import"></a> 컬렉션 가져오기  

사이트에서 컬렉션을 내보낼 때 Configuration Manager는 이 컬렉션을 MOF(Managed Object Format) 파일로 저장합니다. 아래 절차를 수행하여 사이트 데이터베이스에 해당 파일을 가져올 수 있습니다. 이 절차를 완료하려면 컬렉션 클래스에 대한 **만들기** 권한이 필요합니다.

> [!IMPORTANT]  
> - 파일이 신뢰할 수 있는 원본에서 가져왔으며 컬렉션 데이터만을 포함하고 변조되지 않았는지 확인하세요.  
> 
> - 사용 중인 동일한 버전의 Configuration Manager를 실행하는 사이트에서 파일을 내보냈는지 확인하세요.  

컬렉션 내보내기에 대한 자세한 내용은 [컬렉션 관리 방법](/sccm/core/clients/manage/collections/manage-collections)을 참조하세요.


1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다. **사용자 컬렉션** 또는 **디바이스 컬렉션** 노드 중 하나를 선택합니다.  

2. 리본 **홈** 탭의 **만들기** 그룹에서 **컬렉션 가져오기**를 선택합니다.  

3. **컬렉션 가져오기 마법사**의 **일반** 페이지에서 **다음**을 선택합니다.  

4. **MOF 파일 이름** 페이지에서 **검색**을 선택합니다. 가져오려는 컬렉션 정보가 포함된 MOF 파일을 찾습니다.  

5. 컬렉션을 가져오는 마법사를 완료합니다. 새 컬렉션이 **자산 및 준수** 작업 영역의 **사용자 컬렉션** 또는 **디바이스 컬렉션** 노드에 표시됩니다. 새로 가져온 컬렉션에 대한 컬렉션 멤버를 확인하려면 Configuration Manager 콘솔을 새로 고치거나 다시 로드합니다.  

## <a name="bkmk_aadcollsync"></a>Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화
*(버전 1906부터 시험판 기능으로 도입)*
<!--3607475-->
> [!NOTE]
> Azure AD(Active Directory) 그룹으로의 컬렉션 멤버 자격 동기화는 버전 1906에 시험판으로 처음 도입된 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features) 문서를 참조하세요.

Azure AD(Active Directory) 그룹에 대한 컬렉션 멤버 자격 동기화를 사용할 수 있습니다. 이 동기화 기능으로 컬렉션 멤버 자격 결과에 따라 Azure AD 그룹 멤버 자격을 만들어 클라우드에서 기존 온-프레미스 그룹화 규칙을 사용할 수 있습니다. 디바이스 컬렉션을 동기화할 수 있습니다. Azure AD 그룹에는 Azure Active Directory 레코드가 있는 디바이스만 반영됩니다. 하이브리드 Azure AD 조인 디바이스와 Azure Active Directory 조인 디바이스가 모두 지원됩니다.

Azure AD 동기화는 5분마다 발생합니다. Configuration Manager에서 Azure AD로의 단방향 프로세스입니다. Azure AD의 변경 내용은 Configuration Manager 컬렉션에 반영되지 않으며 Configuration Manager가 덮어씁니다. 예를 들어 Configuration Manager 컬렉션에 2개의 디바이스가 있고 Azure AD 그룹에 3개의 다른 디바이스가 있다면 동기화 후 Azure AD 그룹에는 5개의 디바이스가 있게 됩니다.


### <a name="prerequisites"></a>전제 조건

- [클라우드 관리](/sccm/core/servers/deploy/configure/azure-services-wizard)
- [Azure Active Directory 사용자 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc)

### <a name="create-a-group-and-set-the-owner-in-azure-ad"></a>Azure AD 내의 그룹 생성 및 소유자 설정

1. [https://portal.azure.com](https://portal.azure.com)으로 이동합니다.
1. **Azure Active Directory** > **그룹** > **모든 그룹**으로 이동합니다.
1. **새 그룹**을 클릭하고 **그룹 이름**과 경우에 따라 **그룹 설명**을 입력합니다.
1. **멤버 자격 유형**이 **할당됨**인지 확인합니다.
1. **소유자**를 선택한 다음 Configuration Manager에 동기화 관계를 만들 ID를 추가합니다.
1. **만들기**를 클릭하여 Azure AD 그룹 생성을 완료합니다.

### <a name="enable-collection-synchronization-for-the-azure-service"></a>Azure 서비스에 대한 컬렉션 동기화 사용

1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **Azure 서비스**로 이동합니다.
1. 그룹을 생성했다면 Azure AD 테넌트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
1. **컬렉션 동기화** 탭에서 **Azure Directory 그룹 동기화 사용** 상자를 선택합니다.
1. **확인**을 클릭하여 설정을 저장합니다.

### <a name="enable-the-collection-to-synchronize"></a>컬렉션 동기화 사용

1. Configuration Manager 콘솔에서 **자산 및 호환성** > **개요** > **디바이스 컬렉션**으로 이동합니다.
1. 동기화할 컬렉션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 
1. **AAD 그룹 동기화** 탭에서 **추가**를 클릭합니다.
1. 드롭다운 메뉴에서 Azure AD 그룹을 만든 **테넌트**를 선택합니다.
1. **이름 시작 문자** 필드에 검색 조건을 입력한 다음 **검색**을 클릭합니다.
  - 로그인하라는 메시지가 표시되면 Azure AD 그룹에 대해 소유자로 지정한 ID를 사용합니다.
1. 대상 그룹을 선택한 다음 **확인**을 클릭하여 그룹을 추가하고 **확인**을 다시 클릭하여 컬렉션의 속성에서 나갑니다.
1. Azure Portal에서 그룹 멤버 자격을 확인하려면 5~7분 정도 기다려야 합니다.
   - 전체 동기화를 시작하려면 컬렉션을 마우스 오른쪽 단추로 클릭한 다음 **멤버 자격 동기화**를 선택합니다.


### <a name="verify-the-azure-ad-group-membership"></a>Azure AD 그룹 멤버 자격 확인

1. [https://portal.azure.com](https://portal.azure.com)으로 이동합니다.
1. **Azure Active Directory** > **그룹** > **모든 그룹**으로 이동합니다.
1. 만들어 놓은 그룹을 찾아 **멤버**를 선택합니다. 
1. 멤버가 Configuration Manager 컬렉션의 멤버를 반영하는지 확인합니다.
   - Azure AD ID가 있는 디바이스만 그룹에 표시됩니다.


![Azure AD로의 컬렉션 동기화](media/3607475-sync-collection-to-azuread.png)

## <a name="bkmk_powershell"></a> PowerShell 사용

PowerShell을 사용하여 컬렉션을 만들고 가져올 수 있습니다. 자세한 내용은 다음을 참조하십시오.

* [New-CMCollection](https://docs.microsoft.com/powershell/module/configurationmanager/new-cmcollection)
* [Set-CMCollection](https://docs.microsoft.com/powershell/module/ConfigurationManager/Set-CMCollection)
* [Import-CMCollection](https://docs.microsoft.com/powershell/module/ConfigurationManager/Import-CMCollection)

## <a name="next-steps"></a>다음 단계

[컬렉션 관리](/sccm/core/clients/manage/collections/manage-collections)
