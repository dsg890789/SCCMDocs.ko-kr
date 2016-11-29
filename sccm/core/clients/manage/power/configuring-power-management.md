---
title: "전원 관리 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 전원 관리를 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 435c923c-ea30-4dce-8afd-48962ed85502
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: ca1277ba0c2be68a393da930769151e25e997210


---
# <a name="configuring-power-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 전원 관리 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 전원 관리를 사용하려면 먼저 다음 구성 단계를 수행해야 합니다.  

## <a name="enable-and-configure-power-management-client-settings"></a>전원 관리 클라이언트 설정 사용 및 구성  
 이 절차는 전원 관리에 대한 기본 클라이언트 설정을 구성하고 계층의 모든 컴퓨터에 적용됩니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 사용자 지정 장치 클라이언트 설정을 만들어서 전원 관리를 사용할 컴퓨터가 포함된 컬렉션에 할당합니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

#### <a name="to-enable-power-management-and-configure-client-settings"></a>전원 관리를 사용하도록 설정하고 클라이언트 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.  

3.  **기본 클라이언트 설정**을 클릭합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  **기본 클라이언트 설정** 대화 상자에서 **전원 관리**를 클릭합니다.  

6.  전원 관리 클라이언트 설정에 대해 다음 값을 구성합니다.  

    -   **장치의 전원 관리 허용** – 드롭다운 목록에서 **True** 를 선택하여 전원 관리를 사용하도록 설정합니다.  

7.  필요한 클라이언트 설정을 구성합니다. 구성할 수 있는 전원 관리 클라이언트 설정 목록은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../../core/clients/deploy/about-client-settings.md) 항목의 [전원 관리](../../../../core/clients/deploy/about-client-settings.md#BKMK_PowMgmtDeviceSettings) 섹션을 참조하세요.  

8.  **확인** 을 클릭하여 **기본 클라이언트 설정** 대화 상자를 닫습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  

## <a name="exclude-computers-from-power-management"></a>전원 관리에서 컴퓨터를 제외합니다.  
 컴퓨터의 컬렉션이 전원 관리 설정을 받지 않도록 차단할 수 있습니다. 컴퓨터가 전원 관리 설정에서 제외되는 컬렉션의 멤버인 경우 해당 컴퓨터가 전원 관리 설정을 적용하는 다른 컬렉션의 멤버인 경우에도 전원 관리 설정을 적용하지 않습니다.  

 다음과 같은 원인으로 인해 컴퓨터를 전원 관리에서 제외하려 할 수 있습니다.  

-   컴퓨터가 항상 켜져 있어야 하는 비즈니스 요구 사항이 있습니다.  

-   전원 관리 설정을 적용하기를 원하지 않는 컴퓨터의 컨트롤 컬렉션을 만들었습니다.  

-   일부 컴퓨터가 전원 관리 설정을 적용할 수 없습니다.  

-   Windows Server를 실행하는 컴퓨터를 전원 관리에서 제외하려고 합니다.  

> [!NOTE]  
>  **사용자가 전원 관리에서 장치를 제외할 수 있도록 허용** 옵션을 클라이언트 설정에서 구성하면 사용자는 소프트웨어 센터를 사용하여 자신의 컴퓨터를 전원 관리에서 제외할 수 있습니다.  

 전원 관리에서 제외된 컴퓨터를 확인하려면 **제외된 컴퓨터**보고서를 실행합니다. 이 보고서에 대한 자세한 내용은 [System Center Configuration Manager에서 전원 관리를 모니터링하고 계획하는 방법](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md)에서 [제외된 컴퓨터](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Excluded)를 참조하세요.  

> [!IMPORTANT]  
>  Windows XP 또는 Windows Server 2003을 실행하는 컴퓨터에 적용되는 전원 설정은 해당 컴퓨터를 전원 관리에서 제외하는 경우에도 원래 값으로 되돌아가지 않습니다. 이후 버전의 Windows에서는 전원 관리에서 컴퓨터를 제외하면 모든 전원 설정이 원래 값으로 되돌아갑니다. 개별 전원 설정을 원래 값으로 되돌릴 수 없습니다.  

#### <a name="to-exclude-a-collection-of-computers-from-power-management"></a>컴퓨터의 컬렉션을 전원 관리에서 제외하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 호환성** 작업 영역에서 **장치 컬렉션**을 클릭합니다.  

3.  **장치 컬렉션** 목록 중 전원 관리에서 제외할 컬렉션을 선택하고 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

4.  *<컬렉션 이름\>***속성** 대화 상자의 **전원 관리** 탭에서 **이 컬렉션의 컴퓨터에 전원 관리 설정 적용 안 함**을 선택합니다.  

5.  **확인**을 클릭하여 *<컬렉션 이름\>***속성** 대화 상자를 닫고 설정을 저장합니다.  



<!--HONumber=Nov16_HO1-->


