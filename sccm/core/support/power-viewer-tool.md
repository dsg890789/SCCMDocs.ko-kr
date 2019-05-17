---
title: 전원 뷰어 도구
titleSuffix: Configuration Manager
description: 전원 뷰어 도구를 사용하여 Configuration Manager 클라이언트에서 전원 관리 기능의 상태를 봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8143e3bf-d6bd-4c69-aec1-e6989cf2ecd9
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09b1cf553aaa5fd75dbf0f7500246263a9bed7a6
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65500825"
---
# <a name="power-viewer-tool"></a>전원 뷰어 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

전원 뷰어 도구는 [Configuration Manager 도구](/sccm/core/support/tools) 중 하나입니다. 이를 사용하여 Configuration Manager 클라이언트에서 전원 관리 기능의 상태를 봅니다.

관리자 권한으로 **PowerVwr.exe**를 실행합니다. 도구가 시작되면 **전원 구성** 탭에 로컬 컴퓨터의 전원 기능 및 전원 설정을 표시합니다. 

원격 컴퓨터의 전원 관리 데이터를 보려면:  

1. **파일** 메뉴로 이동하고, **연결**을 클릭합니다. 

2. 필요한 경우 **컴퓨터** 이름, **사용자 이름** 및 **암호**를 입력합니다. 

전원 뷰어에는 세 개의 탭이 있습니다.  

- **전원 구성**: 대상 컴퓨터의 전원 기능 및 전원 설정을 봅니다.  

- **일별 작업**: 다음 정보를 포함하는 클라이언트의 일별 작업 차트를 봅니다.  

    - **컴퓨터 켜기**: 하루의 컴퓨터 전원 상태입니다. 절전 모드는 전원 끄기로 간주됩니다.  

    - **모니터 켜기**: 하루의 모니터 켜기 또는 끄기 상태입니다.  

    - **사용자 작업**: 하루의 사용자 작업 정보입니다.  

- **전원 이벤트**: 모든 일별 전원 이벤트를 봅니다. 클라이언트는 오전 12시에 이러한 이벤트를 요약합니다. 이 요약에서는 일별 작업 차트에 대한 데이터를 생성합니다.  
