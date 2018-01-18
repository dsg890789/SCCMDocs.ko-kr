---
title: "소프트웨어 인벤토리 구성"
titleSuffix: Configuration Manager
description: "Configuration Manager에서 소프트웨어 인벤토리를 구성하고 소프트웨어 인벤토리의 폴더를 제외합니다."
ms.custom: na
ms.date: 01/03/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f86559de-092a-4ce8-9b43-5d7530e0b763
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: afddcef2caab6e1af0aacdac91366fa430f21d85
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 인벤토리를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 절차에서는 소프트웨어 인벤토리에 대한 기본 클라이언트 설정을 구성하고 계층에 있는 모든 컴퓨터에 적용합니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 사용자 지정 클라이언트 장치 설정을 만들고 컬렉션에 할당합니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.   

## <a name="to-configure-software-inventory"></a>소프트웨어 인벤토리를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **기본 설정** 대화 상자에서 **소프트웨어 인벤토리**를 선택합니다.  

6.  **장치 설정** 목록에서 다음 값을 구성합니다.  

    -   **클라이언트에서 소프트웨어 인벤토리 사용** - 드롭다운 목록에서 **True**를 선택합니다.  

    -   **소프트웨어 인벤토리 및 파일 컬렉션 일정 예약** – 클라이언트가 소프트웨어 인벤토리 및 파일을 수집하는 간격을 구성합니다.   

7.  필요한 클라이언트 설정을 구성합니다. [System Center Configuration Manager의 클라이언트 설정 정보](../../../../core/clients/deploy/about-client-settings.md) 항목의 [소프트웨어 인벤토리](../../../../core/clients/deploy/about-client-settings.md#software-inventory) 섹션에는 클라이언트 설정 목록이 있습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  

 > [!TIP]  
        >   inventoryprovider.log의 오류 코드 80041006은 WMI 공급자에 메모리가 부족하다는 의미입니다. 즉, 공급자에 대한 메모리 할당량 제한에 도달했고 인벤토리 공급자를 계속할 수 없습니다.
이 경우에 인벤토리 항목이 보고되지 않도록 인벤토리 에이전트는 0개 항목을 포함한 보고서를 만듭니다. <br/>
이 오류에 가능한 솔루션은 소프트웨어 인벤토리 컬렉션의 범위를 줄이는 것일 수 있습니다. 인벤토리 범위를 제한한 후에 오류가 발생하는 경우에 [_ProviderHostQuotaConfiguration](https://msdn.microsoft.com/library/aa394671) 클래스에 정의된[ MemoryPerHost](https://blogs.technet.microsoft.com/askperf/2008/09/16/memory-and-handle-quotas-in-the-wmi-provider-service/) 속성이 증가하면 솔루션을 제공할 수 있습니다.

<!--SMS.480648 include WMI Out of memory tip -->


## <a name="to-exclude-folders-from-software-inventory"></a>소프트웨어 인벤토리에서 폴더를 제외하려면  

1.  Notepad.exe를 사용하여 **Skpswi.dat**라는 빈 파일을 만듭니다.  

2.  **Skpswi.dat** 파일을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다. Skpswi.dat 파일에 대한 파일 속성에서 **숨김** 특성을 선택합니다.  

3.  소프트웨어 인벤토리에서 제외하려는 각 클라이언트 하드 드라이브 또는 폴더 구조의 루트에 **Skpswi.dat** 파일을 배치합니다.  

> [!NOTE]  
>  클라이언트 컴퓨터의 드라이브에서 이 파일을 삭제하지 않는 한 소프트웨어 인벤토리가 클라이언트 드라이브를 다시 인벤토리에 포함하지 않습니다.