---
title: "System Center Configuration Manager 클라이언트로 관리되는 Windows 10 장치에 대한 구성 항목을 만드는 방법 | System Center Configuration Manager"
description: "System Center Configuration Manager Windows 10 구성 항목을 사용하여 Configuration Manager 클라이언트에서 관리되는 Windows 10 컴퓨터에 대한 설정을 관리할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14226fbe-dd07-4432-910b-130790624a4e
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: d5248e7262f758c2de2a1deaf42282d4e77e3e0c


---
# <a name="create-configuration-items-for-windows-10-devices-managed-with-the-system-center-configuration-manager-client"></a>System Center Configuration Manager 클라이언트로 관리되는 Windows 10 장치에 대한 구성 항목 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager **Windows 10** 구성 항목을 사용하여 Configuration Manager 클라이언트에서 관리되는 Windows 10 컴퓨터에 대한 설정을 관리할 수 있습니다.  

> [!IMPORTANT]  
>  이 릴리스에서 **암호** 설정을 Configuration Manager 클라이언트에서 관리되는 장치에 대해 **Windows 10** 형식의 구성 항목 중 일부로 만들었는데 Windows 10 장치에 해당 설정이 아직 존재하지 않거나 구성되지 않은 경우 규격을 준수하는 것으로 잘못 평가합니다.  
>   
>  해결 방법으로, 이러한 장치에 대한 설정을 만들 때 구성 항목 만들기 마법사의 설정 페이지에서 **비규격 설정 재구성** 이 선택되어 있는지 확인합니다. 또한 암호 설정을 포함하는 Windows 10 구성 항목이 포함된 구성 기준을 배포할 때 구성 기준 배포 대화 상자에서 **지원되는 경우 비규격 규칙 재구성** 을 선택합니다. 이 해결 방법을 사용하면 설정이 모니터링되고 비규격 상태로 확인되는 경우 재구성됩니다. 재구성 후에는 **오류** 로 보고할 문제가 발생하지 않는 경우 설정이 **규격**으로 올바르게 보고됩니다.  

## <a name="create-a-windows-10-configuration-item"></a>Windows 10 구성 항목 만들기  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 항목**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **구성 항목 만들기**를 클릭합니다.  

4.  **구성 항목 만들기 마법사** 의 **일반**페이지에서 구성 항목에 대한 이름 및 선택적 설명을 지정합니다.  

5.  **만들려는 구성 항목의 유형 지정**아래에서 **Windows 10**을 선택합니다.  

6.  Configuration Manager 콘솔에서 구성 항목을 검색하고 필터링하기 위해 범주를 만들고 할당하려면 **범주**를 클릭합니다.  

7.  **지원되는 플랫폼** 페이지에서 구성 항목을 평가할 특정 Windows 10 플랫폼을 선택합니다.  

8.  **장치 설정** 페이지에서 구성하려는 설정 그룹을 선택합니다. 자세한 내용은 이 항목에서 [Windows 10 구성 항목 설정 참조](/sccm/compliance/deploy-use/create-configuration-items-for-windows-10-devices-managed-with-the-client#windows-10-configuration-item-settings-reference)를 참조하고 **다음**을 클릭합니다.  

    > [!TIP]  
    >  원하는 설정이 나열되지 않은 경우 **기본 설정 그룹에 없는 추가 설정 구성 확인란**을 선택합니다.  

9. 각 설정 페이지에서 필요한 설정과 장치에서 준수되지 않는 경우 수정 여부(지원되는 경우)를 구성합니다.  

10. 각 설정 그룹에 대해 구성 항목이 비규격인 것으로 확인되는 경우 Configuration Manager 보고서에서 보고될 심각도를 구성할 수도 있습니다.  

    -   **없음** - 이 준수 규칙에 실패한 장치가 오류 심각도를 보고하지 않습니다.  

    -   **정보** - 이 준수 규칙에 실패한 장치가 **정보**의 오류 심각도를 보고합니다.  

    -   **경고** - 이 준수 규칙에 실패한 장치가 **경고** 오류 심각도를 보고합니다.  

    -   **위험** - 이 준수 규칙에 실패한 장치가 **위험** 오류 심각도를 보고합니다.  

    -   **위험(이벤트 포함)** - 이 준수 규칙에 실패한 장치가 **위험** 오류 심각도를 보고합니다. 또한 이 심각도 수준은 응용 프로그램 이벤트 로그에 Windows 이벤트로 기록됩니다.  

11. **플랫폼 적용 여부 가능성** 페이지에서 이전에 선택한 지원되는 플랫폼과 호환되지 않는 설정을 검토합니다. 뒤로 돌아가서 이러한 설정을 제거하거나 계속할 수 있습니다.  

    > [!TIP]  
    >  지원되지 않는 설정은 준수 여부에 대해 평가되지 않습니다.  

12. 마법사를 완료합니다.  

 **자산 및 준수** 작업 영역의 **구성 항목** 노드에서 새 구성 항목을 볼 수 있습니다.  

##  <a name="windows-10-configuration-item-settings-reference"></a>Windows 10 구성 항목 설정 참조  

### <a name="password"></a>암호  

|설정|세부 정보|  
|-------------|-------------|  
|**장치에 암호 설정 필요**|지원되는 장치에는 암호가 필요합니다.|  
|**최소 암호 길이(문자 수)**|암호의 최소 문자 길이입니다.|  
|**다음 기간 후 암호 만료(일)**|암호를 변경해야 할 때까지의 기간(일)입니다.|  
|**저장한 암호 수**|이전 암호를 다시 사용하지 못하도록 설정합니다.|  
|**다음 로그온 실패 횟수 후 장치 초기화**|이 횟수만큼 로그인에 실패하면 장치를 초기화합니다.|  
|**다음 유휴 시간 후 모바일 장치 잠그기**|장치가 자동으로 잠기기 전에 몇 분 동안 비활성 상태로 있어야 하는지 지정합니다.|  
|**암호 복잡도**|'1234' 등의 PIN을 지정할 수 있는지 아니면 강력한 암호를 입력해야 하는지를 선택합니다.|  

###  <a name="device"></a>장치  

|설정 이름|세부 정보|  
|------------------|-------------|  
|**Bluetooth**|장치에서 Bluetooth 기능을 사용할 수 있습니다.|  

### <a name="cloud"></a>클라우드  

|설정 이름|세부 정보|  
|------------------|-------------|  
|**설정 동기화**|장치 간에 설정을 동기화할 수 있습니다.|  
|**자격 증명 동기화**|장치 간에 자격 증명을 동기화할 수 있습니다.|  
|**유료 네트워크에서 설정 동기화**|인터넷 연결이 유료일 때 설정을 동기화할 수 있습니다.|  

### <a name="roaming"></a>로밍  

|설정 이름|세부 정보|  
|------------------|-------------|  
|**데이터 로밍**|데이터 액세스 시 네트워크 간 로밍이 가능합니다.|  

### <a name="encryption"></a>암호화  

|설정 이름|세부 정보|  
|------------------|-------------|  
|**장치에 파일 암호화**|장치의 파일을 암호화해야 합니다.|  

### <a name="system-security"></a>시스템 보안  

|설정 이름|세부 정보|  
|------------------|-------------|  
|**사용자 계정 컨트롤**|장치에서 Windows 사용자 계정 컨트롤이 작동하는 방법을 구성합니다.<br />예를 들어 사용하지 않도록 설정하거나 알리는 수준을 설정할 수 있습니다.|  
|**네트워크 방화벽**|Windows 방화벽을 사용하거나 사용하지 않도록 설정합니다.|  
|**SmartScreen**|Windows SmartScreen을 사용하거나 사용하지 않도록 설정합니다.|  
|**바이러스 방지**|바이러스 백신 소프트웨어를 설치 및 구성해야 합니다.|  
|**바이러스 방지 서명이 최신임**|장치에서 바이러스 백신 소프트웨어에 대한 서명 파일이 최신이어야 합니다.|  

### <a name="windows-information-protection-formerly-enterprise-data-protection"></a>Windows Information Protection(이전의 엔터프라이즈 데이터 보호)

기업에서 직원 소유 장치가 증가됨에 따라 메일, 소셜 미디어, 공용 클라우드 등의 앱 및 서비스를 통해 실수에 의한 데이터 유출의 위험도 증가하며, 이러한 상황은 기업에서 제어할 수 없습니다. 예를 들면 직원이 자신의 개인 메일 계정에서 최신 엔지니어링 그림을 보내거나 제품 정보를 복사하여 트윗에 붙여넣거나 진행 중인 판매 보고서를 해당 공용 클라우드 저장소에 저장하는 경우가 있습니다.

WIP(Windows Information Protection)를 사용하면 직원 환경을 방해하지 않고 잠재적인 데이터 유출로부터 기업을 보호할 수 있습니다. 또한 WIP를 통해 사용자 환경 또는 다른 앱을 변경하지 않고도 엔터프라이즈 소유 장치와 직원이 직장으로 가져온 개인 장치에서 실수에 의한 데이터 유출로부터 기업을 보호할 수 있습니다.

 Configuration Manager WIP 구성 항목은 WIP, 엔터프라이즈 네트워크 위치, 보호 수준 및 암호화 설정으로 보호되는 앱 목록을 관리합니다.

Configuration Manager로 Windows Information Protection을 구성하는 방법에 대한 자세한 내용은 [WIP(Windows Information Protection)를 사용하여 엔터프라이즈 데이터 보호](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)를 참조하세요.



<!--HONumber=Nov16_HO1-->


