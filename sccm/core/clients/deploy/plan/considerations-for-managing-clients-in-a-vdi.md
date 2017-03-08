---
title: "VDI(가상 데스크톱 인프라) 클라이언트 관리 | Microsoft 문서 "
description: "VDI(가상 데스크톱 인프라)에서 System Center Configuration Manager 클라이언트를 관리합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
caps.latest.revision: 7
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 55c953f312a9fb31e7276dde2fdd59f8183b4e4d
ms.openlocfilehash: 58251f6a4eebac4cba9f3d51f8d0aaad068c3ab8
ms.lasthandoff: 12/16/2016


---
# <a name="considerations-for-managing-system-center-configuration-manager-clients--in-a-virtual-desktop-infrastructure-vdi"></a>VDI(가상 데스크톱 인프라)에서 System Center Configuration Manager 클라이언트를 관리할 때의 고려 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 다음과 같은 VDI(가상 데스크톱 인프라) 시나리오에서 Configuration Manager 클라이언트 설치를 지원합니다.  

-   **개인 가상 컴퓨터** - 일반적으로 사용자 데이터 및 설정을 세션 간에 가상 컴퓨터에서 유지 관리하도록 구성할 때 사용됩니다.  

-   **원격 데스크톱 서비스 세션** - 원격 데스크톱 서비스를 통해 서버에서 여러 동시 클라이언트 세션을 호스트할 수 있습니다. 사용자는 세션에 연결한 다음 해당 서버에서 응용 프로그램을 실행할 수 있습니다.  

-   **풀링된 가상 컴퓨터** - 풀링된 가상 컴퓨터는 세션 간에 지속되지 않습니다. 세션이 종료되면 모든 데이터 및 설정은 삭제됩니다. 풀링된 가상 컴퓨터는 클라이언트 세션을 호스팅하는 Windows Server에서 필수 비즈니스 응용 프로그램이 실행될 수 없으므로 원격 데스크톱 서비스를 사용할 수 없는 경우에 유용합니다.  

 다음 표에는 VDI에서 Configuration Manager 클라이언트를 관리하는 데 필요한 고려 사항이 나열되어 있습니다.  

|가상 컴퓨터 유형|고려 사항|  
|--------------------------|--------------------|  
|개인 가상 컴퓨터|Configuration Manager는 개인 가상 컴퓨터를 물리적 컴퓨터와 동일하게 처리합니다. Configuration Manager 클라이언트는 가상 컴퓨터 이미지에 사전 설치하거나 가상 컴퓨터가 프로비전된 후 배포할 수 있습니다.|  
|원격 데스크톱 서비스|개별 원격 데스크톱 세션에서는 Configuration Manager 클라이언트가 설치되지 않습니다. 대신 클라이언트는 원격 데스크톱 서비스 서버에 한 번만 설치됩니다. 원격 데스크톱 서비스 서버에서 모든 Configuration Manager 기능을 사용할 수 있습니다.|  
|풀링된 가상 컴퓨터|풀링된 가상 컴퓨터를 해제하면 Configuration Manager를 사용하여 변경한 모든 내용이 손실됩니다.<br /><br /> 가상 컴퓨터가 단시간 동안만 작동하므로 하드웨어 인벤토리, 소프트웨어 인벤토리, 소프트웨어 계량과 같은 Configuration Manager 기능에서 반환한 데이터가 요구 사항에 적합하지 않을 수 있습니다. 풀링된 가상 컴퓨터는 인벤토리 작업에서 제외하는 것이 좋습니다.|  

 가상화는 동일한 물리적 컴퓨터에서 여러 Configuration Manager 클라이언트를 실행하도록 지원하므로 많은 클라이언트 작업에는 하드웨어 및 소프트웨어 인벤토리, 맬웨어 방지 검사, 소프트웨어 설치, 소프트웨어 업데이트 검색 등의 예약된 작업을 위해 기본 제공되는 임의 지연 시간이 포함됩니다. 이러한 지연 시간을 통해, Configuration Manager 클라이언트를 실행하는 여러 개의 가상 컴퓨터가 포함된 컴퓨터에 대해 CPU 처리 및 데이터 전송을 분산할 수 있습니다.  

> [!NOTE]  
>  서비스 모드인 Windows Embedded 클라이언트를 제외하고, 가상화된 환경에서 실행 중이지 않은 Configuration Manager 클라이언트에서도 이러한 임의 지연 시간을 활용합니다. 배포된 클라이언트가 여러 개인 경우 이러한 동작은 네트워크 대역폭의 최대 사용을 방지하고 관리 지점 및 사이트 서버와 같은 Configuration Manager 사이트 시스템에서 CPU 처리 요구 사항을 완화하는 데 도움이 됩니다. 지연 간격은 Configuration Manager 기능에 따라 달라집니다.  
>   
>  임의 지연은 **컴퓨터 에이전트**: **최종 기한 임의 설정 사용 안 함**클라이언트 설정을 통해 필수 소프트웨어 업데이트 및 필수 응용 프로그램 배포에 대해 기본적으로 사용되지 않습니다.

