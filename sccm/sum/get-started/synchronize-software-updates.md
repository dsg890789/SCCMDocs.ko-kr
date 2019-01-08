---
title: 소프트웨어 업데이트 동기화 관리
titleSuffix: Configuration Manager
description: 소프트웨어 업데이트 동기화를 예약하고, 수동으로 소프트웨어 업데이트 동기화를 시작하고, 소프트웨어 업데이트 동기화를 모니터링하려면 다음 단계를 따르세요.
author: aczechowski
ms.date: 12/20/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: ea8698c4-9df5-4cf5-8b62-ab93115b4769
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 0fd176984316dc040568deda3ceb339f2ef0eb3c
ms.sourcegitcommit: 81e3666c41eb976cc7651854042dafe219e2e467
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747112"
---
#  <a name="BKMK_SUMSync"></a> 소프트웨어 업데이트 동기화

*적용 대상: System Center Configuration Manager(현재 분기)*

 Configuration Manager의 소프트웨어 업데이트 동기화는 구성한 기준을 충족하는 소프트웨어 업데이트 메타데이터를 검색하는 프로세스입니다. 여기에는 특정 제품, 분류 및 언어가 포함됩니다. 일반적으로 중앙 관리 사이트나 독립 실행형 기본 사이트의 소프트웨어 업데이트 지점은 Microsoft 업데이트에서 메타데이터를 검색합니다. 그런 다음 최상위 사이트에서 다른 사이트에 동기화 요청을 보냅니다. 사이트가 상위 사이트에서 동기화 요청을 받으면 사이트의 소프트웨어 업데이트 지점이 해당 업스트림 [동기화 원본](../plan-design/plan-for-software-updates.md#BKMK_SyncSource)에서 소프트웨어 업데이트 메타데이터를 검색합니다. 소프트웨어 업데이트 동기화 프로세스에 대한 자세한 내용은 [소프트웨어 업데이트 동기화](../understand/software-updates-introduction.md#BKMK_Synchronization)를 참조하세요.

소프트웨어 업데이트 동기화는 최상위 사이트의 소프트웨어 업데이트 지점에 대한 속성에서 일정에 따라 실행되도록 구성합니다. 동기화 일정이 구성되면 일반적으로 정상 작업의 일부로 일정을 변경하지 않습니다. 그러나 필요한 경우 소프트웨어 업데이트 동기화를 수동으로 시작할 수 있습니다.

  > [!NOTE]  
  >  소프트웨어 업데이트를 동기화하려면 소프트웨어 업데이트 지점을 해당 업스트림 동기화 원본에 연결해야 합니다. 업스트림 동기화 원본에서 소프트웨어 업데이트 지점의 연결이 끊어진 경우 내보내기 및 가져오기 방법을 사용하여 소프트웨어 업데이트를 동기화할 수 있습니다. 자세한 내용은 [연결이 끊긴 소프트웨어 업데이트 지점에서 소프트웨어 업데이트 동기화](synchronize-software-updates-disconnected.md)를 참조하세요.  

## <a name="schedule-software-updates-synchronization"></a>소프트웨어 업데이트 동기화 예약
소프트웨어 업데이트 동기화 일정을 구성하면 최상위 소프트웨어 업데이트 지점에서 예약된 날짜와 시간에 Microsoft 업데이트와 동기화를 시작합니다. 사용자 지정 일정을 사용하면 WSUS(Windows Server Update Services) 서버, 사이트 서버 및 네트워크에 대한 요청이 많지 않은 날짜 및 시간에 소프트웨어 업데이트를 동기화할 수 있습니다. 예를 들어 매주 오전 2시에 소프트웨어 업데이트가 동기화되도록 일정을 설정할 수 있습니다. 예약된 동기화를 수행하는 동안에는 마지막으로 예약되었던 동기화 이후 소프트웨어 업데이트 메타데이터에 적용된 모든 변경 내용이 사이트 데이터베이스에 삽입됩니다. 여기에는 새 소프트웨어 업데이트 메타데이터 또는 수정되거나 제거되거나 이제는 만료된 메타데이터가 포함됩니다.

소프트웨어 업데이트 동기화를 예약하려면 최상위 사이트에서 다음 절차를 수행하세요.  

#### <a name="to-schedule-software-updates-synchronization"></a>소프트웨어 업데이트 동기화를 예약하려면  

  1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

  2.  관리 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.  

  3.  결과 창에서 중앙 관리 사이트 또는 독립 실행형 기본 사이트를 클릭합니다.  

  4.  **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성**을 확장한 후 **소프트웨어 업데이트 지점**을 클릭합니다.  

  5.  소프트웨어 업데이트 지점 구성 요소 속성 대화 상자에서 **일정에 따라 동기화 사용**을 선택한 다음 동기화 일정을 지정합니다.  

## <a name="manually-start-software-updates-synchronization"></a>수동으로 소프트웨어 업데이트 동기화 시작
Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에 있는 **모든 소프트웨어 업데이트** 노드를 사용하여 최상위 사이트에서 수동으로 소프트웨어 업데이트 동기화를 시작할 수 있습니다.  

소프트웨어 업데이트 동기화를 수동으로 시작하려면 최상위 사이트에서 다음 절차를 수행하세요.  

#### <a name="to-manually-start-software-updates-synchronization"></a>수동으로 소프트웨어 업데이트 동기화를 시작하려면  

1. 중앙 관리 사이트 또는 독립 실행형 기본 사이트에 연결된 Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2. 소프트웨어 라이브러리 작업 영역에서 **소프트웨어 업데이트** 를 확장한 다음 **모든 소프트웨어 업데이트** 또는 **소프트웨어 업데이트 그룹**을 클릭합니다.  

3. **홈** 탭의 **만들기** 그룹에서 **소프트웨어 업데이트 동기화**를 클릭합니다. 대화 상자에서 **예** 를 클릭하여 동기화 프로세스를 시작할 것임을 확인합니다.  

   소프트웨어 업데이트 지점에서 동기화 프로세스를 시작한 후에 Configuration Manager 콘솔에서 계층 구조의 모든 소프트웨어 업데이트 지점에 대한 동기화 프로세스를 모니터링할 수 있습니다. 소프트웨어 업데이트 동기화 프로세스를 모니터링하려면 다음 절차를 수행하세요.  


## <a name="monitor-software-updates-synchronization"></a>소프트웨어 업데이트 동기화 모니터링
동기화 프로세스를 시작한 후에는 Configuration Manager 콘솔에서 계층 구조의 모든 소프트웨어 업데이트 지점에 대해 동기화 프로세스를 모니터링할 수 있습니다. 소프트웨어 업데이트 동기화 프로세스를 모니터링하려면 다음 절차를 따르세요. 동기화 프로세스를 포함하여 소프트웨어 업데이트를 모니터링하는 방법에 대한 자세한 내용은 [소프트웨어 업데이트 모니터링](../deploy-use/monitor-software-updates.md)을 참조하세요.

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>소프트웨어 업데이트 동기화 프로세스를 모니터링하려면  

1. Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2. **모니터링** 작업 영역에서 **소프트웨어 업데이트 지점 동기화 상태**를 클릭합니다.  

   Configuration Manager 계층 구조의 소프트웨어 업데이트 지점이 결과 창에 표시됩니다. 이 보기에서 모든 소프트웨어 업데이트 지점의 동기화 상태를 모니터링할 수 있습니다. 동기화 프로세스에 대한 세부 정보를 보려면 각 사이트 서버의 <*Configuration Manager 설치 경로*>\Logs에 있는 wsyncmgr.log 파일을 검토하면 됩니다.  

## <a name="import-updates-from-the-microsoft-update-catalog"></a>Microsoft 업데이트 카탈로그에서 업데이트 가져오기

최상위 소프트웨어 업데이트 지점은 WSUS를 사용하여 소프트웨어 업데이트에 대한 정보를 Microsoft에서 Configuration Manager로 가져옵니다. 경우에 따라 선택한 제품 및 분류에 대해 WSUS로 자동으로 동기화되지 않지만 [Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com)에서 사용할 수 있는 업데이트가 필요할 수 있습니다. WSUS로 자동으로 동기화되지 않는 업데이트는 일반적으로 매우 특정한 문제를 해결하기 위한 것입니다. 일반적으로 카탈로그에서 업데이트를 사용할 수 있는 경우 WSUS로 가져올 수 있습니다. 그런 다음, 이를 Configuration Manager로 동기화하고 다른 업데이트와 마찬가지로 배포할 수 있습니다.

### <a name="to-import-an-update-from-the-microsoft-update-catalog"></a>Microsoft 업데이트 카탈로그에서 업데이트를 가져오려면

1. WSUS 관리 콘솔을 열고 SCCM 계층 구조의 최상위 WSUS 서버에 연결합니다. 
   - Internet Explorer가 컴퓨터의 기본 웹 브라우저가 아닌 경우 일시적으로 기본값으로 설정합니다.
2. **업데이트**를 클릭하거나 WSUS 서버의 이름을 클릭합니다. 
3. **작업** 창에서 [Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com)에 대한 브라우저 창을 여는 **업데이트 가져오기...** 를 선택합니다.
   ![WSUS 콘솔에서 업데이트 가져오기 선택](media/wsus-console-import-updates.png)
4. 메시지가 표시되면 Microsoft 업데이트 카탈로그 ActiveX 컨트롤을 설치합니다. 업데이트를 WSUS로 가져오려면 컨트롤을 설치해야 합니다. 
5. 브라우저 창에서 원하는 업데이트를 검색합니다. 바구니에 추가하려면 **추가*** 단추를 클릭합니다.
6. **바구니 보기**를 클릭합니다. **Windows Server Update Services로 직접 가져오기** 옵션이 선택되어 있는지 확인합니다. 그런 다음, **가져오기**를 클릭합니다.
    ![카탈로그에서 WSUS로 업데이트 가져오기](./media/import-catalog-update-into-wsus.png)
7. 가져오기가 완료되면 브라우저 창에서 **닫기**를 클릭합니다.
     - 필요한 경우 기본 브라우저를 다시 설정합니다.
8. Configuration Manager 소프트웨어 업데이트 지점을 동기화합니다.


## <a name="next-steps"></a>다음 단계
처음으로 소프트웨어 업데이트를 동기화한 후 또는 새 분류나 제품을 사용할 수 있게 되면 [새 분류 및 제품을 구성](configure-classifications-and-products.md)하여 소프트웨어 업데이트를 새 기준과 동기화해야 합니다.

소프트웨어 업데이트를 필요한 기준과 동기화한 후 [소프트웨어 업데이트에 대한 설정을 관리](manage-settings-for-software-updates.md)합니다.  
