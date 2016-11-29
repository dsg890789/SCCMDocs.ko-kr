---
title: "가상화 지원 | System Center Configuration Manager"
description: "가상화 환경에서 System Center Configuration Manager 클라이언트 및 사이트 시스템 역할을 설치하기 위한 요구 사항을 가져옵니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: be32ccee17bc4829888d42dfff3f2818f4fc2810


---
# <a name="support-for-virtualization-environments-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 가상화 환경 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager는 다음 가상 환경에서 가상 컴퓨터로 실행되는 지원 운영 체제에서 클라이언트 및 사이트 시스템 역할을 설치하도록 지원합니다. 가상 컴퓨터 호스트(가상화 환경)가 클라이언트 또는 사이트 서버로 지원되지 않는 경우에도 이러한 설치는 지원됩니다.  

 **예를 들어**Microsoft Hyper-V Server 2012를 사용하여 Windows Server 2012를 실행하는 가상 컴퓨터를 호스트하는 경우 가상 컴퓨터(Windows Server 2012)에는 클라이언트 또는 사이트 시스템 역할을 설치할 수 있지만 호스트(Microsoft Hyper-V Server 2012)에는 설치할 수 없습니다.  

|가상화 환경|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|  

 사용하는 각 가상 컴퓨터는 실제 Configuration Manager 컴퓨터에 사용하는 것과 같은 하드웨어 및 소프트웨어 구성 이상을 충족해야 합니다.  

 서버 가상화 유효성 검사 프로그램 및 이 프로그램의 온라인 가상화 프로그램 지원 정책 마법사를 사용하여 가상화 환경이 Configuration Manager용으로 지원되는지 유효성을 검사할 수 있습니다. 서버 가상화 유효성 검사 프로그램에 대한 자세한 내용은 [Windows Server 가상화 유효성 검사 프로그램](https://www.windowsservercatalog.com/svvp.aspx)을 참조하세요.  

> [!NOTE]  
>  Configuration Manager는 Mac에서 실행되는 가상 PC 또는 가상 서버 게스트 운영 체제를 지원하지 않습니다.  

Configuration Manager는 온라인 상태가 아닌 가상 컴퓨터를 관리할 수 없습니다. 오프라인 가상 컴퓨터 이미지를 업데이트하거나 호스트 컴퓨터에서 Configuration Manager 클라이언트를 사용하여 인벤토리를 수집할 수는 없습니다.  

가상 컴퓨터에 대한 특수 고려 사항은 없습니다. 예를 들어 Configuration Manager는 업데이트가 적용된 가상 컴퓨터의 상태를 저장하지 않고 가상 컴퓨터를 중지했다가 다시 시작하는 경우 가상 컴퓨터에 업데이트를 다시 적용해야 하는지 여부를 확인하지 않을 수 있습니다.  

##  <a name="a-namebkmkazurea-microsoft-azure-virtual-machines"></a><a name="bkmk_Azure"></a> Microsoft Azure 가상 컴퓨터  
 Configuration Manager는 실제 회사 네트워크 내의 온-프레미스에서 실행하는 경우와 마찬가지로 Microsoft Azure의 Virtual Machine에서도 실행할 수 있습니다. 다음 시나리오에서는 Configuration Manager를 Microsoft Azure Virtual Machine과 함께 사용할 수 있습니다.  

-   **시나리오 1:** Microsoft Azure Virtual Machine에서 Configuration Manager를 실행하고 다른 Microsoft Azure Virtual Machine에 설치된 클라이언트를 관리하는 데 사용할 수 있습니다.  

-   **시나리오 2:** Microsoft Azure 가상 컴퓨터에서 Configuration Manager를 실행하고 Microsoft Azure에서 실행되고 있지 않은 클라이언트를 관리하는 데 사용할 수 있습니다.  

-   **시나리오 3:** 적합한 통신용 네트워크 연결을 사용할 수 있는 경우 실제 회사 네트워크에서는 다른 역할을 실행하면서 Microsoft Azure Virtual Machine에서는 다른 Configuration Manager 사이트 시스템 역할을 실행할 수 있습니다.  

실제 회사 네트워크에서 온-프레미스 Configuration Manager를 설치할 때 적용되는 것과 동일한 System Center Configuration Manager 네트워크, 지원되는 구성 및 하드웨어 요구 사항이 Microsoft Azure의 설치에도 적용됩니다.  

> [!IMPORTANT]  
>  Azure 가상 컴퓨터에서 실행되는 Configuration Manager 사이트 및 클라이언트에는 온-프레미스 설치와 같은 라이선스 요구 사항이 적용됩니다.  



<!--HONumber=Nov16_HO1-->


