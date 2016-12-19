---
title: "소프트웨어 인벤토리에서 폴더 제외 | Microsoft 문서"
description: "System Center Configuration Manager의 소프트웨어 인벤토리에서 폴더 제외"
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f86559de-092a-4ce8-9b43-5d7530e0b763
caps.latest.revision: 5
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 6d1aabbde576f01de920468fd3ef372bd23be9df
ms.openlocfilehash: 7850b69cdccb0e897ee71b75255004bdc8d0ae97


---
# <a name="how-to-exclude-folders-from-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager의 소프트웨어 인벤토리에서 폴더를 제외하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

 이 절차에서는 소프트웨어 인벤토리에 대한 기본 클라이언트 설정을 구성하고 계층에 있는 모든 컴퓨터에 적용합니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 사용자 지정 장치 클라이언트 설정을 만들어서 소프트웨어 인벤토리를 사용할 컴퓨터가 포함된 컬렉션에 할당합니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

### <a name="to-configure-software-inventory"></a>소프트웨어 인벤토리를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **기본 설정** 대화 상자에서 **소프트웨어 인벤토리**를 선택합니다.  

6.  **장치 설정** 목록에서 다음 값을 구성합니다.  

    -   **클라이언트에서 소프트웨어 인벤토리 사용** - 드롭다운 목록에서 **True**를 선택합니다.  

    -   **소프트웨어 인벤토리 및 파일 컬렉션 일정 예약** – 클라이언트가 소프트웨어 인벤토리 및 파일을 수집하는 간격을 구성합니다.   

7.  필요한 클라이언트 설정을 구성합니다. 구성할 수 있는 소프트웨어 인벤토리 클라이언트 설정 목록은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../../core/clients/deploy/about-client-settings.md) 항목의 [소프트웨어 인벤토리](../../../../core/clients/deploy/about-client-settings.md#software-inventory) 섹션을 참조하세요.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  



<!--HONumber=Dec16_HO3-->


