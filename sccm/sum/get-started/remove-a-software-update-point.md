---
title: 소프트웨어 업데이트 지점 제거
titleSuffix: Configuration Manager
description: 이 절차에 따라 Configuration Manager 콘솔에서 사이트의 소프트웨어 업데이트 지점 사이트 시스템 역할을 제거할 수 있습니다.
author: aczechowski
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 2486375c-d4a2-4cf2-9124-9bee02bbf173
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 585077c44b13d79da55e8ab140fd93998b8371c1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353572"
---
#  <a name="BKMK_RemoveSUP"></a> 소프트웨어 업데이트 지점 사이트 시스템 역할 제거  

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 콘솔에서 사이트의 소프트웨어 업데이트 지점 사이트 시스템 역할을 제거할 수 있습니다. 목록에서 소프트웨어 업데이트 지점을 제거하도록 클라이언트 정책이 업데이트됩니다. 사이트에서 마지막 소프트웨어 업데이트 지점을 제거하면 소프트웨어 업데이트 지점 목록에 소프트웨어 업데이트 지점이 포함되어 있지 않으므로 사실상 사이트에서 소프트웨어 업데이트가 사용되지 않습니다. 기본 사이트에 소프트웨어 업데이트 지점이 둘 이상인 경우 동기화 원본으로 구성된 소프트웨어 업데이트 지점을 제거하면 사이트에서 새 동기화 원본으로 사용할 다른 소프트웨어 업데이트 지점을 선택해야 합니다.  

> [!NOTE]  
>  사이트 시스템에서 소프트웨어 업데이트 지점 사이트 역할을 제거할 경우 소프트웨어 업데이트 지점 사이트 역할을 다시 설치하기 전에 최소 15분 이상 기다리십시오.  

 소프트웨어 업데이트 지점을 제거하려면 다음 절차를 수행하세요.  

#### <a name="to-remove-the-software-update-point"></a>소프트웨어 업데이트 지점을 제거하려면  

1.  **Configuration Manager** 콘솔에서 **관리**를 클릭합니다.  

2.  관리 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.  

3.  소프트웨어 업데이트 지점을 제거할 사이트 시스템 서버를 선택하고 **사이트 시스템 역할**에서 **소프트웨어 업데이트 지점**을 선택합니다.  

4.  **사이트 역할** 탭의 **사이트 역할** 그룹에서 **역할 제거**를 클릭합니다. 소프트웨어 업데이트 지점을 제거하도록 확인하거나 사이트에서 다른 소프트웨어 업데이트 지점에 대한 새 동기화 원본을 선택합니다.  
