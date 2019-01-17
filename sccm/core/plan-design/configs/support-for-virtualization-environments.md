---
title: 가상화 지원
titleSuffix: Configuration Manager
description: 가상화 환경에서 구성 관리자 클라이언트 및 사이트 시스템 역할을 설치하기 위한 요구 사항입니다.
ms.date: 01/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 792e9e34f67ad0dc2a12df0905578effaf1f79aa
ms.sourcegitcommit: 3f791918c5dd87d8968ae9977d761dd97909398c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54196317"
---
# <a name="support-for-virtualization-environments-with-configuration-manager"></a>Configuration Manager를 사용하여 가상화 환경 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager는 다음 문서의 가상 환경에서 가상 머신으로 실행되는 지원 운영 체제에서 클라이언트 및 사이트 시스템 역할을 설치하도록 지원합니다. 가상 머신 호스트(가상화 환경)가 클라이언트 또는 사이트 서버로 지원되지 않는 경우에도 이러한 설치는 지원됩니다.  

예를 들어 Microsoft Hyper-V Server 2012를 사용하여 Windows Server 2012를 실행하는 가상 머신을 호스트합니다. Windows Server 2012를 실행하는 가상 머신에는 클라이언트 또는 사이트 시스템 역할을 설치할 수 있습니다. Microsoft Hyper-V Server 2012 실행하는 호스트에는 클라이언트를 설치할 수 없습니다.  


## <a name="virtualization-environments"></a>가상화 환경

- Windows Server 2019  
- Windows Server 2016 <sup>[참고 1](#bkmk_note1)</sup>  
- Microsoft Hyper-V Server 2016 <sup>[참고 1](#bkmk_note1)</sup>  
- Windows Server 2012 R2  
- Microsoft Hyper-V Server 2012  
- Windows Server 2012  
- Microsoft Hyper-V Server 2008 R2  
- Windows Server 2008 R2  

#### <a name="bkmk_note1"></a> 참고 1: 중첩된 가상화
Configuration Manager는 Windows Server 2016에 새로 도입된 [중첩 가상화](https://docs.microsoft.com/windows-server/virtualization/hyper-v/What-s-new-in-Hyper-V-on-Windows#BKMK_nested)를 지원하지 않습니다.


### <a name="virtualization-environment-support"></a>가상화 환경 지원

각 가상 컴퓨터는 실제 Configuration Manager 컴퓨터에 사용하는 것보다 크거나 같은 하드웨어 및 소프트웨어 요구 사항이 필요합니다.  

가상화 환경이 Configuration Manager용으로 지원되는지 유효성을 검사하려면 서버 가상화 유효성 검사 프로그램을 사용합니다. 온라인 가상화 프로그램 지원 정책 마법사를 포함합니다. 자세한 내용은 [Windows Server 가상화 유효성 검사 프로그램](https://www.windowsservercatalog.com/svvp.aspx)을 참조하세요.  

> [!NOTE]  
> Configuration Manager는 Mac 컴퓨터에서 실행되는 가상 PC 또는 가상 서버 게스트 운영 체제를 지원하지 않습니다.  

Configuration Manager는 오프라인 상태인 가상 머신을 관리할 수 없습니다. 오프라인 가상 머신 이미지를 업데이트하거나 호스트 컴퓨터에서 구성 관리자 클라이언트를 사용하여 인벤토리를 수집할 수는 없습니다.  

가상 컴퓨터에 대한 특수 고려 사항은 없습니다. 예를 들어 Configuration Manager는 업데이트가 적용된 가상 머신의 상태를 저장하지 않고 가상 머신을 중지했다가 다시 시작하는 경우 가상 머신에 업데이트를 다시 적용해야 하는지 여부를 확인하지 않을 수 있습니다.  



##  <a name="bkmk_Azure"></a> Microsoft Azure 가상 컴퓨터  

Configuration Manager에서는 데이터 센터 내의 온-프레미스에서 실행하는 경우와 마찬가지로 Azure의 가상 머신에서 실행될 수 있습니다. 다음 시나리오에서는 Configuration Manager를 Azure 가상 머신과 함께 사용합니다.  

- **시나리오 1**: Azure 가상 머신에서 Configuration Manager를 실행합니다. 이를 사용하여 다른 Azure 가상 머신의 클라이언트를 관리합니다.  

- **시나리오 2**: Azure 가상 머신에서 Configuration Manager를 실행합니다. 이를 사용하여 Azure에서 실행되지 않는 클라이언트를 관리합니다.  

- **시나리오 3**: Azure 가상 머신에서 다른 Configuration Manager 사이트 시스템 역할을 실행합니다. Azure에 올바르게 연결된 온-프레미스 데이터 센터에서 다른 역할을 실행합니다.  

온-프레미스로 설치할 때 적용되는 것과 동일한 Configuration Manager 네트워크, 지원되는 구성 및 하드웨어 요구 사항이 Azure 가상 머신의 설치에도 적용됩니다.  

자세한 내용은 [Azure의 Configuration Manager](/sccm/core/understand/configuration-manager-on-azure)를 참조하세요.

> [!IMPORTANT]  
> Azure 가상 컴퓨터에서 실행되는 Configuration Manager 사이트 및 클라이언트에는 온-프레미스 설치와 같은 라이선스 요구 사항이 적용됩니다.  
