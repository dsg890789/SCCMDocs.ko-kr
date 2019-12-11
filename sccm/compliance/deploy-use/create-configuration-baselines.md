---
title: 구성 기준 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 컬렉션에 배포할 수 있는 구성 기준을 만듭니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb5d237ed4338c5a9c197bc749c557c542b0b6c4
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74825561"
---
# <a name="create-configuration-baselines-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 구성 기준 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 구성 기준에는 미리 정의된 구성 항목과 필요에 따라 다른 구성 기준이 포함됩니다. 구성 기준을 만든 다음 컬렉션에 배포하여 컬렉션의 디바이스가 구성 기준을 다운로드하고 이를 준수하는지 평가하게 할 수 있습니다.  

## <a name="configuration-baselines"></a>구성 기준

 Configuration Manager의 구성 기준에 특정한 수정 버전의 구성 항목을 포함하거나 항상 최신 버전의 구성 항목을 사용하도록 구성할 수 있습니다. 구성 항목 수정 버전에 대한 자세한 내용은 [구성 데이터에 대한 관리 작업](../../compliance/deploy-use/management-tasks-for-configuration-data.md)을 참조하세요.  

 구성 기준을 만들기 위해 사용할 수 있는 두 가지 방법은 다음과 같습니다.  

- 파일에서 구성 데이터를 가져옵니다. **구성 데이터 가져오기 마법사**를 시작하려면 **자산 및 준수** 작업 영역의 **구성 기준** 노드 또는 **구성 항목** 에서 **구성 데이터 가져오기**를 클릭합니다. 자세한 내용은 [구성 데이터 가져오기](/sccm/compliance/deploy-use/import-configuration-data)를 참조하세요.

- **구성 기준 만들기** 대화 상자를 사용하여 새 구성 기준을 만듭니다.  

## <a name="create-a-configuration-baseline"></a>구성 기준 만들기

**구성 기준 만들기** 대화 상자를 사용하여 구성 기준을 만들려면 다음 절차를 사용합니다.  

1. Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**을 클릭합니다.  

2. **홈** 탭의 **만들기** 그룹에서 **구성 기준 만들기**를 클릭합니다.  

3. **구성 기준 만들기** 대화 상자에 고유한 이름 및 구성 기준에 대한 설명을 입력합니다. 이름은 최대 255자를 사용할 수 있으며 설명은 최대 512자를 사용할 수 있습니다.  

4. **구성 데이터** 목록에는 모든 구성 항목 또는 이 구성 기준에 포함된 구성 기준이 표시됩니다. **추가** 를 클릭하여 목록에 새 구성 항목 또는 구성 기준을 추가합니다. 다음 항목에서 선택할 수 있습니다.  

   - **자산 및 준수**  

   - **소프트웨어 업데이트**  

   - **구성 기준**  
     > [!IMPORTANT]
     > 각 구성 기준에 포함되는 소프트웨어 업데이트 수를 1000개 이내로 제한해야 합니다.
5. **용도 변경** 목록을 사용하여 **구성 데이터** 목록에서 선택한 구성 항목의 동작을 지정합니다. 다음 항목에서 선택할 수 있습니다.  

   -   **필수**: 구성 항목이 클라이언트 디바이스에서 검색되지 않는 경우 구성 기준이 비규격으로 평가됩니다. 검색되는 경우 준수 여부가 평가됩니다.  

   -   **선택 사항**: 구성 항목이 참조하는 애플리케이션이 클라이언트 컴퓨터에 있는 경우 구성 항목만 준수 여부를 평가합니다. 애플리케이션이 없는 경우 구성 기준은 비규격으로 표시되지 않습니다(애플리케이션 구성 항목에만 적용).  

   -   **허용 안 함**: 구성 항목이 클라이언트 컴퓨터에서 검색되는 경우 구성 기준이 비규격으로 평가됩니다(애플리케이션 구성 항목에만 적용).  

   > [!NOTE]
   >  **용도 변경** 목록은 **구성 항목 만들기 마법사** 의 **일반** 페이지에서 **이 구성 항목에 애플리케이션 설정 포함**옵션을 클릭했을 때만 사용 가능합니다.  

6. 클라이언트 디바이스에서 준수 여부를 평가하기 위해 특정 또는 최신 수정 버전의 구성 항목을 선택하려면 **수정 버전 변경** 목록을 선택하고, 항상 최신 수정 버전을 사용하려면 **항상 최신 버전 사용** 을 선택합니다. 구성 항목 수정 버전에 대한 자세한 내용은 [구성 데이터에 대한 관리 작업](../../compliance/deploy-use/management-tasks-for-configuration-data.md)을 참조하세요.  

7. 구성 기준에서 구성 항목을 제거하려면 구성 항목을 선택한 다음 **제거**를 클릭합니다.  

8. 버전 1806부터, **공동 관리하는 클라이언트에 대해 항상 이 기준을 적용**할지를 선택합니다. 선택하면 이 기준이 Intune에서 관리하는 클라이언트에도 적용됩니다.  이 예외는 조직에 필요한 설정을 구성하는 데 사용할 수 있지만 Intune에서는 아직 사용할 수 없습니다.

9. 필요에 따라 **범주**를 클릭하여 검색 및 필터링에 대한 기준에 범주를 할당합니다. 

10. **확인** 을 클릭하여 **구성 기준 만들기** 대화 상자를 닫고 구성 기준을 만듭니다.  

>[!NOTE]
> **공동 관리하는 클라이언트에 대해 항상 이 기준 적용** 설정과 같은 기존 기준을 수정하면 기준 콘텐츠 버전이 증가됩니다. 고객은 새 버전을 평가하고 기준 보고를 업데이트해야 합니다.

## <a name="bkmk_CAbaselines"></a> 준수 정책 평가의 일환으로 사용자 지정 구성 기준 포함
<!--3608345-->
*(버전 1910에서 도입됨)*

버전 1910부터, 이제 사용자 지정 구성 기준의 평가를 준수 정책 평가 규칙으로 추가할 수 있습니다. 구성 기준을 만들거나 편집하는 경우, **준수 정책 평가의 일부로 이 기준을 평가**할 수 있는 옵션을 사용할 수 있습니다. 준수 정책 규칙을 추가하거나 편집하는 경우, **준수 정책 평가에 구성된 기준 포함**이라는 조건을 사용할 수 있습니다. 공동 관리 되는 장치의 경우 및 전체 준수 상태에 대 한 Configuration Manager 준수 평가 결과를 사용 하도록 Intune을 구성 하는 경우이 정보는 Azure AD로 전송 됩니다. 그런 다음 [Office 365 리소스에 대 한 조건부 액세스](/configmgr/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm#configure-conditional-access)에 사용할 수 있습니다.  

준수 정책 평가의 일환으로 사용자 지정 구성 기준을 포함하려면 다음 작업을 수행합니다.

- [**규정 준수 정책 평가에 구성 된 기준을 포함**](#bkmk_CA)하는 규칙을 사용 하 여 규정 준수 정책을 만들고 사용자 컬렉션에 배포 합니다.
- 장치 컬렉션에 배포 된 구성 기준에서 [**준수 정책 평가의 일부로이 기준 평가**](#bkmk_eval-baseline) 를 선택 합니다.

> [!IMPORTANT]
> 공동 관리 되는 장치를 대상으로 지정 하는 경우 [공동 관리 필수 구성 요소](/configmgr/comanage/overview#prerequisites)를 충족 하는지 확인 합니다.

### <a name="example-evaluation-scenario"></a>예제 평가 시나리오

사용자가 규칙 조건 **준수 정책 평가에 구성된 기준 포함**을 포함하는 준수 정책을 사용하여 대상으로 지정된 컬렉션의 일부인 경우, 사용자 또는 사용자의 디바이스에 배포된 **규정 준수 평가의 일부로 이 기준 평가** 옵션이 선택된 기준이 규정 준수에 대해 평가됩니다. 예:

- `User1`은 `User Collection 1`의 일부입니다.
- `User1`에서 `Device1`을(를) 사용하며, 이는 `Device Collection 1` 및 `Device Collection 2`에 속합니다.
- `Compliance Policy 1`에는 **준수 정책 평가에 구성된 기준 포함** 규칙 조건이 있으며 `User Collection 1`에 배포됩니다.
- `Configuration Baseline 1`에는 **규정 준수 평가의 일부로 이 기준 평가**가 선택되고 `Device Collection 1`에 배포됩니다.
- `Configuration Baseline 2`에는 **규정 준수 평가의 일부로 이 기준 평가**가 선택되고 `Device Collection 2`에 배포됩니다.

이 시나리오에서 `Device1`을(를) 사용하여 `User1`에 대해 `Compliance Policy 1`을(를) 평가하는 경우 `Configuration Baseline 1` 및 `Configuration Baseline 2`도 계산됩니다.

- `User1`에서 `Device2`을(를) 가끔 사용합니다.
- `Device2`은(는) `Device Collection 2` 및 `Device Collection 3`의 멤버입니다.
- `Device Collection 3`에는 `Configuration Baseline 3`이(가) 배포되어 있지만, **규정 준수 평가의 일부로 이 기준 평가**는 선택되지 않습니다.

`User1`에서 `Device2`을(를) 사용하는 경우, `Compliance Policy 1`이(가) 평가할 때 `Configuration Baseline 2`만 평가됩니다.

> [!NOTE]
><!--5582516-->
> 준수 정책이 이전에 클라이언트에서 평가된 적이 없는 새 기준을 평가하는 경우 비준수를 보고할 수 있습니다. 이는 규정 준수를 평가할 때 기준 평가가 아직 실행되고 있는 경우에 발생합니다. 이 문제를 해결하려면 **소프트웨어 센터**에서 **규정 준수 확인**을 클릭합니다.

### <a name="bkmk_CA"></a> 기준 준수 정책 평가 규칙을 사용하여 준수 정책 만들기 및 배포

1. **자산 및 규정 준수** 작업 영역에서, **규정 준수 설정**를 확장하고 **규정 준수 정책** 노드를 선택합니다.
1. f리본에서 **준수 정책 만들기**를 클릭하여 **준수 정책 만들기 마법사**를 엽니다. 자세한 내용은 [디바이스 준수 정책 만들기 및 배포](/sccm/mdm/deploy-use/create-compliance-policy)를 참조하세요.
1. **일반** 페이지에서 **구성 관리자 클라이언트로 관리되는 디바이스의 규정 준수 규칙**을 선택합니다.
   - 준수 정책 평가의 일부로 사용자 지정 구성 기준을 포함하려면 구성 관리자 클라이언트를 사용하여 디바이스를 관리해야 합니다.
1. **지원되는 플랫폼** 페이지에서 플랫폼을 선택합니다.
1. **규칙** 페이지에서 **새로 만들기**를 선택한 다음, **준수 정책 평가에 구성된 기준 포함** 조건을 선택합니다.

   ![준수 정책 평가에 구성된 기준 포함](./media/3608345-create-compliance-policy-rule.png)

1. **확인**과 **다음**을 차례대로 클릭하고 **요약** 페이지로 이동합니다.
1. 선택 사항을 확인하고 **다음**과 **종료**를 차례대로 클릭합니다.
1. **준수 정책** 노드에서 만든 정책을 마우스 오른쪽 단추로 클릭하고, **배포**를 선택합니다.
1. 정책에 관한 컬렉션, 경고 생성 설정 및 규정 준수 평가 일정을 선택합니다.
1. **확인**을 클릭하여 준수 정책을 배포합니다.

### <a name="bkmk_eval-baseline"></a>구성 기준을 선택하고 "준수 정책 평가의 일부로 이 기준 평가" 선택

1. **자산 및 규정 준수** 작업 영역에서 **규정 준수 설정**을 확장하고 **구성 기준**을 클릭합니다.
1. 디바이스 컬렉션에 배포된 기존 기준을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다. 필요한 경우 새 기준선을 만들 수 있습니다.
   - 기준은 사용자 컬렉션이 아니라, 디바이스 컬렉션에 배포해야 합니다.
1. **준수 정책 평가의 일부로 이 기준 평가** 설정을 활성화합니다.
   - **장치 구성** 기관으로 Intune이 있는 공동 관리 장치의 경우 **공동 관리 클라이언트에 대해서도 항상이 기준 적용** 을 선택 해야 합니다.
1. 구성 기준의 변경 내용을 저장하려면 **확인**을 클릭합니다.

   ![구성 기준 속성 대화 상자](./media/3608345-configuration-baseline-properties.png)

### <a name="log-files-for-custom-configuration-baselines-as-part-of-compliance-policy-assessment"></a>준수 정책 평가의 일환으로 사용자 지정 구성 기준에 사용할 로그 파일

- ComplianceHandler.log
- SettingsAgent.log
- DCMAgent.log
- CIAgent.log

## <a name="next-steps"></a>다음 단계

[구성 데이터 가져오기](/sccm/compliance/deploy-use/import-configuration-data)
