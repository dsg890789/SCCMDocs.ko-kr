---
title: 일반적인 준수 관리 작업
titleSuffix: Configuration Manager
description: 몇 가지 일반적인 시나리오를 진행하여Configuration Manager의 준수 설정에 대해 알아봅니다.
ms.date: 05/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 4e345791-74db-41ad-b472-024ce6521daf
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: da92506d291ca24af807db7b4f4b73473359e12f
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70890655"
---
# <a name="common-tasks-for-managing-compliance-on-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 설치된 디바이스의 준수 관리를 위한 일반 작업

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 여러 가지 일반적인 시나리오를 안내 하 여 System Center Configuration Manager 준수 설정을 사용 하는 방법을 소개 합니다.  

 준수 설정에 이미 익숙한 경우 사용할 수 있는 모든 기능에 대한 자세한 설명은 [System Center Configuration Manager 클라이언트로 관리되는 디바이스의 구성 항목](../../compliance/deploy-use/create-configuration-items.md)을 참조하세요.  

 시작 하기 전에 준수 설정 [시작](../../compliance/get-started/get-started-with-compliance-settings.md) 을 읽어 준수 설정에 대 한 몇 가지 기본 사항을 알아보세요. 필요한 필수 구성 요소에 대 한 정보는 [호환성 설정 계획 및 구성](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) 을 참조 하세요.  

## <a name="general-information-for-each-scenario"></a>각 시나리오에 대한 일반 정보  
 각 시나리오에서는 특정 작업을 수행하는 구성 항목을 만듭니다. 구성 항목 만들기 마법사를 열고 시작 하려면 다음 단계를 수행 합니다.  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 항목**을 선택합니다.  

1.  **만들기** 그룹의 **홈** 탭에서 **구성 항목 만들기**를 선택합니다.  

1.  다음 스크린샷에 표시 된 구성 항목 만들기 마법사의 **일반** 페이지에서 구성 항목의 이름과 설명을 지정 합니다. 그런 다음이 문서의 각 시나리오에 대 한 적절 한 구성 항목 유형을 선택 합니다.  

     ![구성 항목 만들기 마법사의 일반 페이지](/sccm/mdm/deploy-use/media/Compliance-Settings-Wizard---1.png)  

## <a name="scenario-disable-bluetooth-on-windows-10-devices"></a>시나리오: Windows 10 장치에서 Bluetooth 사용 안 함

 이 시나리오에서는 보안 부서가 회사 외부에서 중요한 회사 정보를 전송하는 데 디바이스의 Bluetooth 기능을 사용할 수 있다는 사실을 파악했습니다. 최근에 모든 컴퓨터를 Windows 10으로 업그레이드 했습니다. 이러한 장치에서 Bluetooth를 사용 하지 않도록 결정 합니다.  

1. 구성 항목 만들기 마법사의 **일반** 페이지에서 **Windows 10** 구성 항목 유형을 선택하고 **다음**을 클릭합니다.  

2. 마법사의 **지원되는 플랫폼** 에서 모든 Windows 10 플랫폼을 선택합니다.  

3. **장치 설정** 페이지에서 **장치**를 선택 하 고 **다음**을 선택 합니다.  

4. **디바이스** 페이지에서 **Bluetooth** 의 값으로 **허용 안 함**을 선택합니다.  

5. **비호환 설정 재구성** 을 선택하여 모든 Windows 10 디바이스에 변경 내용이 적용되도록 합니다.  

6. 마법사를 완료하여 구성 항목을 만듭니다.  

 이제 [System Center Configuration Manager에서 구성 기준을 만들고 배포하기 위한 일반 작업](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md)의 정보를 참조하여, 만든 구성을 디바이스에 쉽게 배포할 수 있습니다.  

## <a name="scenario-remediate-an-incorrect-registry-value-on-windows-desktop-computers"></a>시나리오: Windows 데스크톱 컴퓨터에서 잘못된 레지스트리 값 수정

> [!NOTE] 
> Configuration Manager 클라이언트를 실행하는 Mac 컴퓨터에서는, 다음과 같이 두 가지 방법으로 준수를 평가할 수 있습니다.  
> - Mac OS X 기본 설정(plist) 파일을 평가합니다.
> - 사용자 지정 스크립트를 사용하고 스크립트에서 반환된 결과를 평가합니다.  
>
>자세한 내용은 [System Center Configuration Manager 클라이언트를 사용하여 관리하는 Mac OS X 디바이스용 구성 항목을 만드는 방법](../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md)을 참조하세요.  

 이 시나리오에서는 관리 하는 일부 Windows 8.1 컴퓨터에서 중요 한 lob (기간 업무) 앱이 제대로 실행 되지 않는다는 것을 알 수 있습니다. 일부 컴퓨터에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1** 이라는 레지스트리 키가 **0** 의 값으로 설정했습니다. LOB(기간 업무) 앱이 제대로 실행되려면 이 값이 **1**로 설정되어 있어야 합니다.  

 이 절차에서는 모니터링하여 잘못된 레지스트리 키 값이 검색되면 이를 자동으로 수정하는 구성 항목을 만듭니다.  

1. 구성 항목 만들기 마법사의 **일반** 페이지에서 **Windows 데스크톱 및 서버(사용자 지정)** 구성 항목 유형을 선택하고 **다음**을 선택합니다.  

2. 마법사의 **지원되는 플랫폼** 페이지에서 **Windows 8.1**을 선택합니다(구성 항목은 영향을 받는 컴퓨터에만 적용됨).  

3. **설정** 페이지에서 **새로 만들기**를 클릭하여 새 설정을 만듭니다.  

4. **설정 만들기** 대화 상자의 **일반** 탭에서 다음을 구성합니다.  

   -   **이름** > **예제 설정**  

   -   **설정 유형** > **레지스트리 값**  

   -   **데이터 형식** > **정수**(값에 숫자만 포함되어 있으므로)  

   -   **하이브** > **HKEY_LOCAL_MACHINE**  

   -   **키** > **SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1**  

   -   **값** > **1** (필수 값)  

5. **설정 만들기** 대화 상자의 **호환성 규칙** 탭에서 **새로 만들기**를 선택 합니다. **규칙 만들기** 대화 상자에서 다음 설정을 구성 합니다.  

   -   **이름** > **예제 규칙**  

   -   **선택한 설정** > 선택한 설정이 **예제 설정**인지 확인합니다.

   -   **규칙 유형** > **값**  

   -   **설정은 다음 규칙을 준수해야 함** > 설정 이름이 올바른지 확인하고 설정 값이 **1**과 같도록 지정하는 옵션을 구성합니다.  

   -   **지원되는 경우 비규격 규칙 재구성** > Configuration Manager가 레지스트리 키 값이 올바르지 않으면 올바른 값으로 재설정하도록 이 확인란을 선택합니다.  

6. 마법사를 완료하여 구성 항목을 만듭니다.  

 이제 [구성 기준 만들기 및 배포에 대한 일반 작업](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) 문서의 내용을 참조하여 만든 구성을 디바이스에 쉽게 배포할 수 있습니다.  

## <a name="next-steps"></a>다음 단계

[구성 기준 만들기 및 배포](/sccm/compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines)
