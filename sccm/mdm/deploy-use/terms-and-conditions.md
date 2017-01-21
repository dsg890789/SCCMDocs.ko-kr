---
title: Terms and Conditions in System Center Configuration Manager
description: "System Center Configuration Manager에서 사용자 그룹에 계약조건을 배포합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d3f9e6b-4d71-4fc4-9b91-47f1bfbd8c70
caps.latest.revision: 9
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: a7b99bed3186ab8ff817ef5f420d7a55d60b1c14


---
# <a name="terms-and-conditions-in-system-center-configuration-manager"></a>Terms and Conditions in System Center Configuration Manager

*적용 대상: System Center Configuration Manager(현재 분기)*

장치 등록, 회사 포털의 작업 리소스 액세스 및 회사 포털 사용 시의 장치와 사용자에 대한 영향을 설명하기 위해 사용자 그룹에 System Center Configuration Manager 계약조건을 배포할 수 있습니다. 사용자는 먼저 사용 약관에 동의해야 회사 포털을 사용하여 작업 등록 및 액세스를 수행할 수 있습니다.  

 ## <a name="working-with-terms-and-conditions-policies-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 사용 약관 정책 사용  
 여러 사용 약관을 만들고 배포할 수 있습니다. 또한 같은 버전의 사용 약관을 여러 언어로 생성한 다음 적합한 그룹에 배포할 수도 있습니다.  

## <a name="to-create-a-terms-and-conditions"></a>사용 약관을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **준수 설정** > **사용 약관**으로 이동합니다.  

2.  **사용 약관 만들기** 를 클릭하여 새 사용 약관을 만듭니다.  

3.  **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름** - Configuration Manager 콘솔에 표시되는 고유 이름  

    -   **설명** - Configuration Manager 콘솔에서 계약조건을 식별하는 데 도움이 되는 자세한 설명  

     그리고 **다음**을 클릭합니다.  

4.  **약관** 페이지에서 다음 정보를 지정합니다.  

    -   **제목** - 회사 포털에서 사용자에게 표시되는 제목  

    -   **약관에 사용할 텍스트** - 회사 포털에서 사용자에게 표시되는 사용 약관  

    -   **사용자가 동의하는 경우 그 의미를 설명하는 텍스트** - 사용 약관 동의와 관련하여 사용자에게 표시되는 레이블입니다. **예**: "계약조건에 동의함"  

     그리고 **다음**을 클릭합니다.  

5.  마법사를 완료하여 새 약관을 만듭니다. 새 약관은 자산 및 준수 작업 영역의 사용 약관 노드에 표시됩니다.  

## <a name="to-deploy-a-terms-and-conditions"></a>사용 약관을 배포하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **준수 설정** > **사용 약관**으로 이동합니다.  

2.  **사용 약관** 목록에서 배포할 항목을 선택한 후 **배포**를 클릭합니다.  

3.  사용 약관을 배포할**컬렉션** 을 **찾아보고**  **확인**을 클릭합니다.  

     대상 장치에서 회사 포털 앱에 액세스하면 배포된 사용 약관이 표시됩니다. 사용자는 해당 약관에 동의해야 회사 리소스에 액세스할 수 있습니다.  

    > [!NOTE]  
    >  사용자가 속하는 여러 사용자 컬렉션에 약관 집합을 배포하면 해당 사용자가 회사 포털을 열면 동일한 약관의 여러 복사본이 표시됩니다. 사용자는 모든 약관을 수락 또는 거절할 수만 있으므로 사용자가 약관을 수락도 하고 거절도 하게 되는 모호한 동의 상태가 될 위험은 없습니다. 사용 약관 동의 보고서에는 사용자의 각 약관이 단일 행에 표시되므로 보고서에 오류가 나타나지 않습니다.  

## <a name="to-monitor-terms-and-conditions"></a>사용 약관을 모니터링하려면  

1.  버전 1602부터, Configuration Manager 콘솔에서 사용 약관 배포를 모니터링할 수 있습니다. Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포**로 이동합니다.  

2.  배포의 목록에서 사용 약관 배포를 선택합니다.  

     요약 영역에는 다음 통계가 표시됩니다.  

    -   **준수** - 사용자가 최신 버전의 사용 약관을 수락했습니다.  

    -   **오류**  

    -   **비준수** - 사용자가 사용 약관의 버전을 수락했지만 최신 버전이 아닙니다.  

    -   **알 수 없음** - 사용자가 등록된 장치가 없는 사용 약관을 비롯하여 사용 약관을 수락하지 않았습니다.  

3.  사용 약관 배포를 선택한 후 **요약 실행** 을 선택하여 개별 사용자의 배포 상태를 확인합니다.  

     배포 상태 화면에서 상태 탭을 선택하여 해당 상태의 사용자를 볼 수 있습니다. **요약 실행** 을 클릭하여 계층 전체에서 데이터를 업데이트할 수 있습니다. 콘솔에서 **새로 고침** 을 클릭하여 데이터를 업데이트합니다.  

## <a name="to-view-a-terms-and-conditions-report"></a>사용 약관 보고서를 보려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **보고** > **보고서**로 이동합니다.  

2.  **사용 약관 수락** 을 선택하고 **실행**을 클릭합니다. 사용 약관 동의 보고서가 열립니다. 보고서에서 사용 약관이 배포되는 각 사용자를 표시합니다. 필드는 다음과 같습니다.  

    -   사용 약관의 이름  

    -   사용자 이름  

    -   수락된 버전  

    -   수락한 날짜  

    -   최신 수락  

## <a name="updates-and-version-control-for-terms-and-conditions"></a>사용 약관 업데이트 및 버전 제어  
 기존 사용 약관을 편집하는 경우 사용 약관을 배포할 때 동작을 선택할 수 있습니다. 다음 절차에 따라 기존 사용 약관을 업데이트할 수 있습니다.  

### <a name="how-to-work-with-multiple-versions-of-terms-and-conditions"></a>여러 버전의 사용 약관을 사용하는 방법  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **준수 설정** > **사용 약관**으로 이동합니다.  

2.  편집할 사용 약관 인스턴스를 선택하고 두 번 클릭하여 엽니다.  

3.  **일반** 또는 **약관** 페이지에서 콘텐츠를 수정하여 필요한 편집을 수행할 수 있습니다.  

4.  **약관** 페이지에서 모든 사용자가 이 새 버전의 사용 약관에 동의해야 하는지, 아니면 신규 사용자에게만 새 버전을 표시할지를 지정합니다.  

     사용 약관을 크게 변경할 때마다 버전 번호를 높이고 동의를 요구하는 것이 좋습니다. 오타를 수정하거나 서식을 변경하는 등의 경우에는 현재 버전 번호를 유지합니다.



<!--HONumber=Nov16_HO1-->


