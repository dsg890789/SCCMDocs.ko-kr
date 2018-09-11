---
title: Microsoft Intune으로 데이터 가져오기
titleSuffix: Configuration Manager
description: Microsoft Intune으로 Configuration Manager 데이터 가져오기
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 12/05/2017
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: b552391d-abc0-48a2-a429-93605a13a66a
ms.openlocfilehash: 89db0abe9a60e6850ae36e619483e0dcdc3e5360
ms.sourcegitcommit: 316899b08f2ef372993909e08e069f7edfed1d33
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44111147"
---
# <a name="import-configuration-manager-data-to-microsoft-intune"></a>Microsoft Intune으로 Configuration Manager 데이터 가져오기 

*적용 대상: System Center Configuration Manager(현재 분기)*    

클라우드 전용 구성에서 [하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션](migrate-hybridmdm-to-intunesa.md)하는 프로세스에서 권장되는 첫 번째 단계는 Intune 데이터 가져오기 도구를 사용하는 것입니다. 원하는 경우 이 단계를 건너뛰고 [사용자 마이그레이션을 위한 Intune 준비](migrate-prepare-intune.md) 단계로 이동할 수 있습니다. 그러나 이 도구는 다음 단계에서 많은 시간을 절약할 수 있는 다음 기능을 수행합니다. 
1.  Configuration Manager 계층 구조에서 선택한 개체에 대한 데이터를 수집합니다. 
2.  가져오도록 선택할 수 있는 개체에 대한 세부 정보와 일부 개체를 가져올 수 없는 이유에 대한 정보를 제공합니다.
3.  선택한 개체를 Microsoft Intune 테넌트로 가져옵니다. 

데이터 가져오기 도구는 어떤 방식으로든 Configuration Manager 환경을 변경하지 않으므로, 개체를 Intune으로 가져오고, 하이브리드 MDM 장치를 관리되지 않는 상태로 두는 위험이 없이 모든 항목이 예상대로 작동하는지 확인할 수 있습니다. 

## <a name="what-objects-can-this-tool-import"></a>이 도구에서 가져올 수 있는 개체
가져오기 도구는 Configuration Manager에서 다음 개체 형식에 대한 정보를 수집하고, 수집된 개체를 가져올 수 있는지 여부에 대한 정보를 제공합니다. 
- 구성 항목
- 인증서 프로필
- 전자 메일 프로필
- VPN 프로필
- Wi-Fi 프로필
- 규정 준수 정책
- 앱
- 배포

> [!Note]    
> 배포 가져오기는 가져오는 다른 개체 형식에만 유용합니다. 예를 들어 VPN 프로필과 배포를 가져오는 경우 선택한 VPN 프로필에 대한 배포만 가져올 수 있습니다. Intune에서 배포는 할당이라고 합니다. 이전에 가져온 개체에 대한 배포를 가져오려면 해당 개체를 다시 가져오거나 Azure의 Intune에서 수동으로 할당을 만들어야 합니다. 예를 들어 VPN 프로필은 가져오고 배포는 가져오지 않으면, 도구를 다시 실행하고 VPN 프로필 및 배포를 선택하거나 Azure의 Intune에서 수동으로 할당을 만듭니다.  도구를 다시 실행하면 나중에 Azure의 Intune에서 삭제할 수 있는 복제된 개체를 만들 수 있습니다.  

> [!Important]    
> 배포에 대한 컬렉션이 AAD(Azure Active Directory)에 복제된 Active Directory 그룹을 기반으로 하는 경우, 이 도구는 실행될 때 적절한 배포를 선택하면 자동으로 그룹에 마이그레이션된 개체를 대상으로 지정합니다. 더 복잡한 컬렉션 또는 직접 멤버 관리 컬렉션이 있는 경우, AAD에서 해당 컬렉션을 수동으로 다시 만들고 Azure의 Intune에서 수동으로 개체 할당을 대상으로 지정해야 합니다.


## <a name="things-to-know-before-you-run-the-tool"></a>도구를 실행하기 전에 알아야 할 사항
- 도구를 실행하더라도 Configuration Manager 환경은 어떤 방식으로든 변경되지 않습니다.
- 먼저 평가판 테넌트를 사용하여 데이터 가져오기 프로세스를 테스트하는 것이 좋습니다. 그런 다음 예상 데이터를 가져왔는지 확인한 후 프로덕션 Intune 테넌트와 동일한 프로세스를 진행할 수 있습니다.
- 데이터 가져오기 도구는 Configuration Manager 데이터를 한 번만 가져옵니다. Configuration Manager 또는 Intune에서 개체를 추적하지 않습니다. 그러나 이전과 동일한 컴퓨터에서 가져오기를 다시 실행하면 이전에 가져온 개체를 알려줍니다. 이 도구에서는 개체가 Intune에 여전히 존재하는지, 아니면 변경되었는지 여부를 확인할 수 없습니다. 데이터를 Intune으로 두 번 이상 가져오면 중복된 개체가 될 수 있습니다.
- 일부 프로필 설정만 가져올 수 있습니다. 예를 들어 키오스크 모드 또는 PFX 설정은 가져올 수 없습니다. 
- 선택한 플랫폼에 적용할 수 없는 설정으로 구성된 Configuration Manager 정책이 있는 경우 이 도구는 가져오는 동안 이러한 설정을 무시할 수 있습니다. 설정이 무시되면 Intune에서 정책을 가져오고 지원할 수 있습니다. 
- 이 도구는 개체를 가져올 수 없는 이유를 제공하려고 합니다. 경우에 따라 개체를 Intune으로 가져오기 전에 Configuration Manager 콘솔로 돌아가서 문제를 해결하고, Configuration Manager 개체 검색을 다시 수행한 다음, 해당 개체를 가져올 수 있습니다. 경우에 따라 Intune에서 이러한 개체를 수동으로 다시 만들어야 할 수도 있습니다.
- 다른 개체에 종속된 일부 프로필이 있습니다. 인증서에 종속된 메일 프로필과 같은 다른 개체에 종속된 프로필을 가져오려면 이전에 같은 컴퓨터에서 같은 사용자로 다른 개체를 가져오지 않은 경우 두 개체를 동시에 가져와야 합니다.  
- 이 도구를 실행한 후에 추가 수동 단계를 수행해야 할 수도 있습니다. 예를 들어 AAD 그룹에 앱과 정책을 대상으로 지정합니다. 

## <a name="prerequisites"></a>필수 구성 요소
- Configuration Manager 버전 1610 이상 - 최상위 사이트를 지정하고, 사이트 계층의 모든 개체에 대한 액세스 권한이 있는 사용자로 도구를 실행하는 것이 좋습니다. 도구를 실행하는 사용자가 액세스할 수 있는 개체만 이 도구에서 검색합니다. 
- 전역 관리자는 다음 ***intunedataimporter.exe -GlobalConsent*** 매개 변수를 사용하여 데이터 가져오기 도구를 처음으로 실행해야 합니다. 그런 다음 전역 관리자 또는 Intune 관리자가 이 도구를 실행할 수 있습니다.  


<!-- ## Objects that cannot be imported
There are some Configuration Manager objects that the importer tool cannot import to Intune. You must manually create these objects in Intune. 
- Collections based on direct membership or that are based on a query. The only collections that are imported are based on a single AD group. For all other collections, you must create the assignment in Intune and add the assignment to the appropriate objects. 
- Profiles <list what we cannot import>
- Policies <??>
- Etc.
-->

## <a name="download-the-data-importer-tool"></a>데이터 가져오기 도구 다운로드
데이터 가져오기 도구는 GitHub의 ConfigMgrTools/Intune-Data-Importer 리포지토리에서 다운로드할 수 있습니다. 다음 절차에 따라 도구를 다운로드합니다.

1. [Intune 데이터 가져오기 GitHub 릴리스](https://github.com/ConfigMgrTools/Intune-Data-Importer/releases) 페이지로 이동합니다.
2. 최신 릴리스의 경우 **Microsoft.Intune.Data.Importer.exe**를 클릭합니다.
3. .exe를 저장하고 실행하거나 실행만 한 다음, Intune 데이터 가져오기 도구를 추출할 대상 폴더를 선택합니다.

## <a name="run-the-data-importer-tool"></a>데이터 가져오기 도구 실행
데이터 가져오기 도구의 마법사는 세 가지 주요 단계로 나눌 수 있습니다. 이 섹션에서는 마법사의 각 섹션을 완료하고 Configuration Manager 데이터를 Intune으로 성공적으로 가져오는 데 도움이 되는 정보를 제공합니다. 각 단계는 이전 단계가 끝난 위치에서 계속됩니다.

### <a name="provide-permission-for-the-data-importer-tool-to-access-resources"></a>리소스에 대한 액세스 권한을 데이터 가져오기 도구에 부여
데이터 가져오기 도구를 실행하려면 먼저 전역 관리자 계정을 사용하여 Azure에서 리소스에 액세스하기 위한 데이터 가져오기 도구 권한을 부여해야 합니다. 그런 다음 전역 관리자 또는 Intune 관리자 계정을 사용하여 이 도구를 실행할 수 있습니다.   

1.  전역 관리자는 ***intunedataimporter.exe -GlobalConsent*** 매개 변수를 사용하여 이 도구를 처음으로 실행해야 합니다. 
2. 도구가 시작되면 Azure에서 전역 관리자 역할이 있는 계정을 사용하여 로그인해야 하는 로그인 화면이 표시됩니다. 
3. **수락**을 클릭하여 적절한 권한이 있는 Azure의 Microsoft Graph에서 응용 프로그램을 만들 수 있습니다. 데이터 가져오기 도구에는 개체를 Microsoft Intune으로 가져올 수 있는 이러한 권한이 필요합니다.   

   > [!Important]
   > **수락**을 클릭하면 다음을 수행할 수 있는 권한을 도구에 부여합니다.
   > - 모든 그룹 읽기
   > - 로그인 및 사용자 프로필 읽기
   > - Intune 장치 구성 및 정책 읽기/쓰기
   > - Intune 앱 읽기/쓰기
   > - Intune 역할 기반 관리 제어 정책 읽기/쓰기
   > - Intune 장치 읽기/쓰기
   > - Intune 구성 읽기/쓰기
1. 동의를 수락하면 다른 모든 전역 관리자 또는 Intune 관리자가 이 도구를 실행하여 Configuration Manager에서 Azure의 Intune으로 데이터를 가져올 수 있습니다.    
        
    > [!Note]
    > 전역 관리자가 처음에 동의를 수락하지 않으면, Intune 관리자가 데이터 가져오기 도구를 실행하고 Intune 구독에 로그인한 후에 **이 응용 프로그램에 액세스할 수 없음**이 도구에 표시될 수 있습니다.

### <a name="manually-map-collections-to-azure-ad-groups"></a>Azure AD 그룹에 컬렉션을 수동으로 매핑
데이터 가져오기 도구를 실행하면 이 도구는 단일 AD 그룹을 대상으로 하는 단일 규칙을 사용하여 컬렉션에서 AD 그룹 이름을 추출합니다. Intune에서 할당을 만들면 데이터 가져오기 도구는 AD 그룹과 이름이 같은 Azure AD 그룹을 찾고 있는 경우 해당 Azure AD 그룹에 가져온 개체를 할당합니다. 사용자는 데이터 가져오기 도구가 컬렉션에 대해 찾는 AD 그룹 이름을 재정의할 수 있고 해당 컬렉션에 사용할 Azure AD 그룹을 하나 이상 제공할 수 있습니다. 컬렉션 매핑 파일을 사용하면 통상 데이터 가져오기 도구로는 가져올 수 없는 컬렉션을 Azure AD 그룹에 매핑할 수 있습니다.
#### <a name="find-the-collections-that-cannot-be-imported"></a>가져올 수 없는 컬렉션 찾기
가져올 수 없는 모든 컬렉션 목록을 가져올 수 있으므로 컬렉션 매핑 .csv 파일에 이 컬렉션을 추가할 수 있습니다. 
1. 데이터 가져오기 도구를 실행하고 가져올 개체를 선택합니다. [1단계: Configuration Manager 개체 검색 및 데이터 수집](#phase-1:-discover-configuration-manager-objects-and-collect-data) 및 [2단계: 문제 해결 및 가져올 개체 선택](#phase-2:-resolve-issues-and-select-the-objects-to-import)의 절차에 따라 개체를 검색하고 선택합니다. 그런 다음 **요약** 페이지에서 **세부 정보 내보내기**를 선택하여 가져올 수 없는 개체 및 배포를 비롯해 가져오기 위해 선택한 모든 항목에 대한 세부 정보가 포함된 .csv 파일을 만듭니다. 
2. Microsoft Excel에서 .csv 파일을 열고 **유형** 열의 **배포** 및 **Importable**(가져오기 가능) 열의 **아니요**를 기준으로 데이터를 필터링합니다. 컬렉션 이름 열에는 이러한 배포를 가져올 수 있으려면 컬렉션 매핑 파일에 추가해야 하는 모든 컬렉션이 표시됩니다.

#### <a name="create-the-collection-mapping-file"></a>컬렉션 매핑 파일 만들기
컬렉션 매핑 파일은 CSV(쉼표로 구분된 값) 파일로 첫 번째 열은 구성 관리자 컬렉션 이름이고 두 번째 열은 해당 컬렉션에 사용할 Azure AD 그룹 이름입니다. 단일 구성 관리자 컬렉션에 대해 Azure AD 그룹을 둘 이상 지정하려면 CSV 파일에 해당 컬렉션 이름으로 여러 행을 작성합니다. 다음 예제는 두 개의 컬렉션을 포함하는 CSV 파일입니다. 첫 번째 컬렉션은 단일 Azure AD 그룹에 매핑되고 두 번째 컬렉션은 두 개의 Azure AD 그룹에 매핑됩니다.

![컬렉션 매핑 csv 파일의 예제](..\media\migrate-collectionmapping.png)

#### <a name="start-the-data-importer-tool-using-collection-mapping"></a>컬렉션 매핑을 사용하여 데이터 가져오기 도구 시작
컬렉션 매핑 파일을 사용하려면 *-CollectionMappingFile* 명령줄 매개 변수와 만든 컬렉션 매핑 .csv 파일의 전체 경로를 사용하여 데이터 가져오기 도구를 시작해야 합니다. 예:

```IntuneDataImporter.exe -CollectionMappingFile c:\Users\myuser\Documents\collectionmapping.csv```

> [!Note]
> 데이터 가져오기 도구는 컬렉션 매핑 파일이 로드되었음을 나타내는 어떤 내용도 마법사 페이지에 표시하지 않습니다. 하지만 .csv 파일을 읽은 중 발생한 오류는 모두 표시합니다. 또한 마법사의 **요약** 페이지에서 **배포** 유형을 확인할 수 있습니다. 이 도구는 [가져오기 가능] 열에 **예**를 표시하고 **참고** 열의 개체에 할당할 Azure AD 그룹을 나열합니다.

### <a name="phase-1-discover-configuration-manager-objects-and-collect-data"></a>1단계: Configuration Manager 개체 검색 및 데이터 수집
1단계에서 검색할 개체를 선택한 다음 도구에서 선택한 개체에 대한 정보를 수집하도록 합니다. 
1. 도구를 열고 **시작**을 클릭합니다.  
2. 정보를 읽고 **다음**을 클릭합니다. 
3. 이전에 내보낸 데이터 집합을 가져올지 여부를 선택하거나 가져올 개체 형식을 선택합니다.
   - **이전에 내보낸 데이터 집합 가져오기**: **Import data set exported from a previous run of Intune Data Importer**(Intune 데이터 가져오기 도구의 이전 실행에서 내보낸 데이터 집합 가져오기)를 선택하고 **Exported data folder**(내보낸 데이터 폴더)에 대해 **찾아보기**를 클릭하여 이전에 데이터 가져오기 도구를 사용하여 내보낸 데이터 집합을 선택합니다. 데이터 집합을 가져오는 사용자는 데이터를 내보낸 사용자와 동일해야 합니다. 데이터를 가져온 후에는 마법사의 **요약** 페이지에 개체에 대한 요약이 표시됩니다. 요약이 맞는 것 같으면 [3단계: Intune으로 선택한 개체 가져오기](phase-3:-import-selected-object-to-intune)를 건너뜁니다.
 
      > [!Note]
      > 사이트에서 가져올 개체를 검색 및 선택한 후 마법사의 **Intune에 로그인** 페이지에서 개체를 데이터 집합으로 내보낼 수 있습니다. 그런 다음이 페이지에서 데이터 집합을 가져올 수 있습니다. 데이터 집합은 로그인한 사용자의 Windows 사용자 자격 증명을 사용하여 암호화되므로 데이터 집합을 내보낸 사용자만 도구에서 데이터 집합을 가져올 수 있습니다. 
   - **가져올 개체 형식 선택**: **Select object types to import**(가져올 개체 형식 선택)를 선택하여 가져올 개체 형식을 선택하고 환경에서 개체를 검색합니다. 사이트 및 가져올 개체에 대한 다음 정보를 제공합니다.
      - **사이트 서버 이름**: 개체를 가져올 사이트 서버의 정규화된 도메인 이름을 제공합니다. 도구를 실행하는 사용자가 액세스할 수 있는 개체만 이 도구에서 검색합니다. 일반적으로 최상위 사이트를 지정하고, 사이트 계층의 모든 개체에 대한 액세스 권한이 있는 사용자로 도구를 실행합니다.
      - **사이트 코드**: 사이트 서버에 대한 사이트 코드를 제공 합니다. Configuration Manager 콘솔의 위쪽에서 세 문자로 된 코드를 찾을 수 있습니다.
      - **가져올 개체 형식**: 도구에서 수집할 개체를 선택합니다. **모두 선택**을 선택하여 모든 개체를 선택하거나 개별 개체 형식을 선택할 수 있습니다. 
4.  **다음**을 클릭하여 사이트에서 개체 검색을 시작합니다. 이 도구에는 각 개체 형식에 대한 진행률이 표시됩니다. 
    - 도구에서 선택한 개체 형식에 대한 데이터를 검색하지 못하면 해당 개체 형식에 수행된 진행률 표시줄이 즉시 표시됩니다.
    - 선택하지 않은 개체는 **수집** 데이터 페이지에 표시되지 않습니다. 
    - 수집되지 않았거나 수집 프로세스 중에 취소된 개체에 대해 도구를 다시 실행할 수 있습니다.

### <a name="phase-2-resolve-issues-and-select-the-objects-to-import"></a>2단계: 문제 해결 및 가져올 개체 선택  
2단계에서는 도구에서 찾은 개체를 검토하고, 개체가 Intune으로 가져오지 못하게 하는 문제를 해결하고, 가져올 개체를 선택합니다. 문제를 해결하면 마법사의 **검색 환경** 페이지로 돌아가 개체를 다시 검색합니다. 
5.  **다음**을 클릭하여 수집된 개체를 검토합니다. 항목 선택 페이지는 수집된 각 개체 형식에 대해 사용할 수 있습니다. 
 <!--   > [!Tip]     
    > On each item selection page, you can create a filter to help you find the objects that you want to import. However, take note of the following:
    > - When you are on an item selection page and the view is filtered, the Select all checkboxes only apply to the displayed items. Any hidden objects because of a filter are not included when using the checkboxes.
    > - Objects are always grouped under their parent item even when you sort or filter the objects.
-->
6.  각 항목 선택 페이지에서 [가져오기 가능] 열을 기준으로 개체를 정렬하고, 가져올 수 없는 개체를 검토합니다. [참고] 열에 있는 정보는 도구에서 개체를 가져올 수 없는 이유에 대한 세부 정보를 제공합니다. 
7.  이제 가져올 수 없는 개체에 대한 문제를 해결할지 여부를 결정해야 합니다. 문제를 하나 이상 수정하는 경우 [Configuration Manager에서 데이터 선택] 페이지가 표시될 때까지 [이전]을 클릭하고 데이터를 다시 수집하여 문제가 해결되었는지 확인합니다. 가져올 수 있는 개체에 만족할 때까지 문제를 계속 해결할 수 있습니다. 
8.  각 항목 선택 페이지에서 가져올 개체를 선택합니다. 다음 열이 나열됩니다.
    - **이름**: Configuration Manager 개체의 이름입니다. 
    - **가져오기 가능**: 개체를 가져올 수 있는지 여부를 지정합니다. [가져오기 가능] 열에서 [예]가 있는 개체만 선택할 수 있습니다. 
    - **플랫폼**: 개체에서 지원하는 플랫폼을 지정합니다.
    - **이미 가져온 항목**: 이 컴퓨터의 도구를 사용하여 개체를 이미 가져왔는지 여부를 지정합니다. 
    - **Is superseded**(대체됨)(앱별): 앱이 다른 앱으로 대체되었는지 여부를 지정합니다. 대체된 앱을 표시하려면 페이지 맨 위에 있는 **Show superseded apps**(대체된 앱 표시) 확인란을 선택해야 합니다.
    - **참고**: 개체를 가져올 수 없는 이유에 대한 정보를 제공합니다. **참고** 열에는 일부 개체 형식에 대해 무시된 설정에 대한 정보도 표시하지만, 해당 설정 없이도 개체를 가져올 수 있습니다.
    - **구성 기준**(구성 항목별): 구성 항목과 연결되는 구성 기준을 지정합니다.
    - **필요한 인증서**(프로필 및 정책별): 인증서가 개체와 연결되는지 여부를 지정합니다. 인증서가 개체와 연결되면 인증서도 가져와야 합니다.
9.  가져올 개체를 선택하면 [요약] 페이지에 나열됩니다. 다음과 같은 작업을 수행할 수 있습니다. 
    - **세부 정보 내보내기**: 화면에 표시된 정보가 포함된 .csv 파일을 만듭니다. 가져올 수 없는 개체와 이 개체를 가져올 수 없는 이유도 표시합니다. 이 파일을 레코드로 유지할 수 있습니다. 
    - **오류 데이터 내보내기**: 도구에서 변환하거나 가져올 수 없는 데이터에 대한 정보가 포함된 압축 파일을 내보냅니다. 

### <a name="phase-3-import-selected-objects-to-intune"></a>3단계: Intune으로 선택한 개체 가져오기
3단계에서는 Intune에 로그인하고 선택한 개체를 가져옵니다. 
10. **다음**을 클릭하고 **Intune에 로그인**을 클릭하여 데이터 가져오기에 대한 Intune 테넌트에 로그인하거나 데이터를 내보내도록 선택합니다.

    - **내보내기**: 사이트에서 가져올 개체를 검색 및 선택한 후 개체를 데이터 집합으로 내보낼 수 있습니다. 이렇게 하면 인터넷에 연결되지 않은 컴퓨터에서 개체를 검색하고, 데이터를 내보낸 다음, 인터넷에 연결된 컴퓨터에서 데이터를 가져올 수 있습니다. 데이터 집합은 로그인한 사용자의 Windows 사용자 자격 증명을 사용하여 암호화되므로 데이터 집합을 내보낸 사용자만 도구에서 데이터 집합을 가져올 수 있습니다. 이 옵션을 선택하는 경우 내보낸 데이터의 경로를 선택합니다. 
      1. **Intune에 로그인** 페이지에서 **내보내기**를 클릭합니다. 
      2. **찾아보기**를 클릭하여 내보낼 대상 폴더를 선택합니다. 이 폴더는 비어 있어야 합니다. 
      3. **시작**을 클릭하여 데이터를 내보내고 내보내기가 완료되면 **닫기**를 클릭하여 마법사를 완료하고 데이터 가져오기 도구를 닫습니다.
      4. 인터넷에 액세스할 수 있는 다른 컴퓨터에서 같은 자격 증명을 사용하여 데이터 가져오기 도구를 시작하고 **이전에 내보낸 데이터 집합 가져오기**를 선택합니다. 데이터를 가져오면 마법사의 **Intune에 로그인** 페이지로 이동됩니다. 
    - **Intune에 로그인**: 전역 관리자 또는 Intune 관리자 계정으로 로그인해야 합니다. 로그인하면 가져오기 프로세스가 시작됩니다.
    
      > [!Important]
      > 먼저 평가판 테넌트를 사용하여 데이터 가져오기 프로세스를 테스트하는 것이 좋습니다. 그런 다음 예상 데이터를 가져왔는지 확인한 후 프로덕션 Intune 테넌트와 동일한 프로세스를 진행할 수 있습니다.
12. [진행률] 페이지에서 개체 가져오기에 대한 진행률이 제공됩니다. 가져오기가 완료되면 **다음**을 클릭합니다. 
13. [완료] 페이지에서 가져온 개체가 나열됩니다. 가져오기 프로세스 중에 오류가 발생한 개체에 대한 상태를 확인합니다. 다음과 같은 작업을 수행할 수 있습니다. 
    - **세부 정보 내보내기**: 화면에 표시된 정보가 포함된 .csv 파일을 만듭니다. 이 파일을 레코드로 유지할 수 있습니다. 
    - **오류 데이터 내보내기**: 도구에서 변환하거나 가져올 수 없는 데이터에 대한 정보가 포함된 압축 파일을 내보냅니다.

## <a name="next-steps"></a>다음 단계
데이터를 Intune으로 가져오면 [사용자 마이그레이션을 위한 Intune 준비](migrate-prepare-intune.md) 단계를 수행해야 합니다. 
