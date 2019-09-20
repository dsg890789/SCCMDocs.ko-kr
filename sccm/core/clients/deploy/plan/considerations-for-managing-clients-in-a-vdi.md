---
title: VDI 클라이언트 관리
titleSuffix: Configuration Manager
description: VDI(가상 데스크톱 인프라)에서 구성 관리자 클라이언트를 관리합니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07df750daf0af7aa82a13c1eef421678d7df8202
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70890329"
---
# <a name="manage-configuration-manager-clients-in-a-virtual-desktop-infrastructure-vdi"></a>VDI(가상 데스크톱 인프라)에서 구성 관리자 클라이언트 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 다음과 같은 VDI(가상 데스크톱 인프라) 시나리오에서 Configuration Manager 클라이언트 설치를 지원합니다.  

- **개인 가상 머신** - 일반적으로 사용자 데이터 및 설정을 세션 간에 가상 머신에서 유지 관리하도록 구성할 때 사용됩니다.  

- **원격 데스크톱 서비스 세션** - 원격 데스크톱 서비스를 통해 서버에서 여러 동시 클라이언트 세션을 호스트할 수 있습니다. 사용자는 세션에 연결한 다음 해당 서버에서 애플리케이션을 실행할 수 있습니다.  

- **풀링된 가상 컴퓨터** - 풀링된 가상 컴퓨터는 세션 간에 지속되지 않습니다. 세션이 종료되면 모든 데이터 및 설정은 삭제됩니다. 풀링된 가상 컴퓨터는 클라이언트 세션을 호스팅하는 Windows Server에서 필수 비즈니스 애플리케이션이 실행될 수 없으므로 원격 데스크톱 서비스를 사용할 수 없는 경우에 유용합니다.  

  다음 표에는 VDI에서 Configuration Manager 클라이언트를 관리하는 데 필요한 고려 사항이 나열되어 있습니다.  

|가상 머신 유형|고려 사항|  
|--------------------------|--------------------|  
|개인 가상 컴퓨터|Configuration Manager는 개인 가상 컴퓨터를 물리적 컴퓨터와 동일하게 처리합니다. Configuration Manager 클라이언트는 가상 머신 이미지에 사전 설치하거나 가상 머신이 프로비전된 후 배포할 수 있습니다.|  
|원격 데스크톱 서비스|개별 원격 데스크톱 세션에서는 Configuration Manager 클라이언트가 설치되지 않습니다. 대신 클라이언트는 원격 데스크톱 서비스 서버에 한 번만 설치됩니다. 원격 데스크톱 서비스 서버에서 모든 Configuration Manager 기능을 사용할 수 있습니다.|  
|풀링된 가상 컴퓨터|풀링된 가상 머신을 해제하면 Configuration Manager를 사용하여 변경한 모든 내용이 손실됩니다.<br /><br /> 가상 머신이 단시간 동안만 작동하므로 하드웨어 인벤토리, 소프트웨어 인벤토리, 소프트웨어 계량과 같은 Configuration Manager 기능에서 반환한 데이터가 요구 사항에 적합하지 않을 수 있습니다. 풀링된 가상 컴퓨터는 인벤토리 작업에서 제외하는 것이 좋습니다.|  

 가상화는 동일한 물리적 컴퓨터에서 여러 Configuration Manager 클라이언트를 실행하도록 지원하므로 많은 클라이언트 작업에는 하드웨어 및 소프트웨어 인벤토리, 맬웨어 방지 검사, 소프트웨어 설치, 소프트웨어 업데이트 검색 등의 예약된 작업을 위해 기본 제공되는 임의 지연 시간이 포함됩니다. 이러한 지연 시간을 통해, Configuration Manager 클라이언트를 실행하는 여러 개의 가상 컴퓨터가 포함된 컴퓨터에 대해 CPU 처리 및 데이터 전송을 분산할 수 있습니다.  

> [!NOTE]  
>  서비스 모드인 Windows Embedded 클라이언트를 제외하고, 가상화된 환경에서 실행 중이지 않은 Configuration Manager 클라이언트에서도 이러한 임의 지연 시간을 활용합니다. 배포된 클라이언트가 여러 개인 경우 이러한 동작은 네트워크 대역폭의 최대 사용을 방지하고 관리 지점 및 사이트 서버와 같은 Configuration Manager 사이트 시스템에서 CPU 처리 요구 사항을 완화하는 데 도움이 됩니다. 지연 간격은 Configuration Manager 기능에 따라 달라집니다.  
>   
>  임의 지연은 다음과 같은 클라이언트 설정을 통해 필수 소프트웨어 업데이트에 대해 기본적으로 사용되지 않습니다. **컴퓨터 에이전트**: **최종 기한 임의 설정 사용 안 함**.
