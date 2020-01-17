---
title: 디바이스 관리 솔루션 선택
titleSuffix: Configuration Manager
description: Configuration Manager에서 PC, 서버 및 디바이스 관리를 위해 제공하는 솔루션에 대해 알아봅니다.
ms.date: 01/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e021a55ede1b65afaa1e260f770f3890d840fb66
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76034875"
---
# <a name="choose-a-device-management-solution-for-configuration-manager"></a>Configuration Manager의 디바이스 관리 솔루션 선택

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager에서는 PC, 서버 및 디바이스를 관리하기 위한 다양한 솔루션을 제공합니다. 조직에 적합한 솔루션을 선택하세요. 관리해야 하는 디바이스 플랫폼과 필요한 관리 기능에 따라 적합한 솔루션을 선택하세요.  

## <a name="overview"></a>개요

이 문서에서는 다음과 같은 네 가지 디바이스 관리 솔루션을 다룹니다. 
- [구성 관리자 클라이언트](#bkmk_sccm)
- [Configuration Manager를 사용한 온-프레미스 MDM(모바일 디바이스 관리)](#bkmk_opmdm)
- [Microsoft Intune을 사용하여 공동 관리](#bkmk_comanage)
- [Microsoft Exchange](#bkmk_opmdm)

이러한 디바이스 관리 솔루션을 단독으로 사용하거나 서로 결합해서 사용할 수 있습니다. 예를 들어 클라이언트 기반 관리 방식을 사용하여 조직의 컴퓨터 및 서버를 관리하고, 또한 공동 관리를 사용하여 인터넷 기반 노트북을 관리할 수 있습니다. 이처럼 여러 관리 방식을 결합하여 사용하면 모든 디바이스 관리 요구를 처리할 수 있습니다.  

또한 이 문서에는 다음 요인을 기준으로 관리 솔루션을 비교하는 표가 두 개 있습니다. 
- [지원되는 플랫폼별 비교](#bkmk_comp1)
- [관리 기능별 비교](#bkmk_comp2)


### <a name="bkmk_sccm"></a> 구성 관리자 클라이언트  

이 옵션을 사용하려면 디바이스에 구성 관리자 클라이언트를 설치해야 합니다. 구성 관리자 클라이언트는 사용자 환경에서 PC, 서버 및 기타 디바이스를 관리하는 대부분의 기능을 제공합니다. 

자세한 내용은 [클라이언트 설치 방법](/sccm/core/clients/deploy/plan/client-installation-methods)을 참조하세요.  


### <a name="bkmk_opmdm"></a> 온-프레미스 MDM  

이 옵션은 Windows 10에 기본 제공되는 디바이스 관리 기능을 사용합니다. 클라이언트 기반 관리만큼 전체 기능을 갖추고 있지는 않지만 온-프레미스 모바일 디바이스 관리는 보다 간단한 관리 방식을 제공합니다. 온-프레미스 모바일 디바이스 관리는 온-프레미스 구성 관리자 리소스를 사용하여 디바이스를 관리합니다.  

자세한 내용은 [온-프레미스 인프라로 모바일 디바이스 관리](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)를 참조하세요.  


### <a name="bkmk_comanage"></a> Microsoft Intune을 사용하여 공동 관리

공동 관리는 기존 Configuration Manager 배포를 Microsoft 365 클라우드에 연결하는 기본적인 방법입니다. 공동 관리를 통해 Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 디바이스를 동시에 관리할 수 있습니다. 공동 관리를 사용하면 새 기능을 추가하여 Configuration Manager의 기존 투자를 클라우드에 연결할 수 있습니다. 

자세한 내용은 [공동 관리란?](/sccm/comanage/overview)을 참조하세요.  


### <a name="bkmk_exchange"></a> Microsoft Exchange  

이 옵션에서는 Exchange Server 커넥터를 사용하여 여러 Exchange 서버를 Configuration Manager에 연결합니다. 이를 통해 Exchange ActiveSync에 연결할 수 있는 디바이스를 중앙 집중식으로 관리합니다. Configuration Manager 콘솔에서 Exchange 모바일 디바이스 관리 기능을 구성할 수 있습니다. 예로는 원격 디바이스 데이터 지움, 여러 Exchange 서버의 설정 제어 등의 기능이 있습니다.

자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  



## <a name="bkmk_comp1"></a> 지원되는 플랫폼별 솔루션 비교  

|플랫폼|Configuration Manager 클라이언트|온-프레미스 MDM을 사용할 수 없음|Configuration Manager와 Exchange|  
|--------|----------------------------|---------------|-----------------------------------|  
|Android| | |예|  
|iOS| | |예|  
|Mac OS X|예| |예|  
|UNIX/Linux|예| |예|  
|Windows 10|예|예|예|  
|Windows 10 Mobile| |예|예|  
|Windows(이전 버전)|예| |예|  
|Windows Server|예| |예|  
|Windows CE|예(모바일 디바이스 레거시 클라이언트 사용)| |예|  
|Windows Embedded|예| | |  
|Windows Mobile| | |예|  

지원되는 플랫폼의 전체 목록은 [Supported operating systems for clients and devices for Configuration Manager](configs/supported-operating-systems-for-clients-and-devices.md)를 참조하세요.

Microsoft는 Intune를 사용하여 Android, iOS 및 Windows 10 모바일 디바이스를 관리하는 것을 권장합니다. 자세한 내용은 [Microsoft Intune이란?](https://docs.microsoft.com/intune/what-is-intune)을 참조하세요.



##  <a name="bkmk_comp2"></a> 관리 기능별 솔루션 비교  

|관리 기능|Configuration Manager 클라이언트|온-프레미스 MDM을 사용할 수 없음|Configuration Manager와 Exchange|  
|--------|----------------------------|---------------|-----------------------------------|  
|모바일 디바이스와 Configuration Manager 간의 PKI(공개 키 인프라)(상호 인증과 SSL을 통한 데이터 전송 암호화)|예|예| |  
|클라이언트 설치|예| | |  
|인터넷을 통한 지원|예| | |  
|검색|예| |예|  
|하드웨어 인벤토리|예|예|예|  
|소프트웨어 인벤토리|예| |예|  
|설정|예|예|예|  
|소프트웨어 배포|예|예| |  
|대체 상태 지점을 사용한 모니터링|예| | |  
|관리 지점에 대한 연결|예|예| |  
|배포 지점에 대한 연결|예|예| |  
|Configuration Manager의 블록|예|예| |  
|Exchange Server(및 Configuration Manager)에서 격리 및 차단| | |예|  
|원격 지우기| |예|예|  


