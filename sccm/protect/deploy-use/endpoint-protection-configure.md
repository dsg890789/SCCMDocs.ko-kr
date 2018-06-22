---
title: Endpoint Protection 구성
titleSuffix: Configuration Manager
description: Windows Defender에 대한 맬웨어 정의를 업데이트하고 배포하도록 Configuration Manager를 설정하는 방법을 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9dc5c79588c8d5211139f0614491d80ba7597f49
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347181"
---
# <a name="configure-endpoint-protection"></a>Endpoint Protection 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

Endpoint Protection을 사용하여 Configuration Manager 클라이언트 컴퓨터의 보안 및 맬웨어를 관리하려면 먼저 이 아티클에 자세히 설명된 구성 단계를 수행해야 합니다.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection을 구성하는 방법  
 Configuration Manager의 Endpoint Protection은 제어에는 외부 종속성과 제품 내 종속성이 있습니다.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection을 구성하는 단계  
 Endpoint Protection을 구성하는 단계, 정보 및 방법에 대한 추가 정보는 다음 표를 참조하세요.  

> [!IMPORTANT]  
>  Windows 10 컴퓨터의 Endpoint Protection을 관리하는 경우 Windows Defender에 대한 맬웨어 정의를 업데이트 및 배포하도록 Configuration Manager를 구성해야 합니다. Windows Defender는 Windows 10에 포함되어 있지만 SCEPInstall은 여전히 설치해야 하고 Endpoint Protection(아래 **5단계**)에 대한 사용자 지정 클라이언트 설정도 여전히 필요합니다. </br> </br>
> Configuration Manager 1802부터 Windows 10 장치에 Endpoint Protection 에이전트(SCEPInstall)를 설치할 필요가 없습니다. Windows 10 장치에 이미 설치되어 있는 경우 Configuration Manager는 에이전트를 제거하지 않습니다. 관리자는 1802 클라이언트 버전 이상이 실행 중인 Windows 10 장치에서 Endpoint Protection 에이전트를 제거할 수 있습니다. SCEPInstall.exe는 동일한 컴퓨터의 C:\Windows\ccmsetup 위치에 여전히 있을 수 있지만 새 클라이언트 설치 시 다운로드할 수 없습니다. Endpoint Protection(아래 **5단계**)에 대한 사용자 지정 클라이언트 설정이 필요합니다. <!--503654-->

|단계|세부 정보|  
|-----------|-------------|  
|**1단계:** [Endpoint Protection 지점 사이트 시스템 역할 만들기](endpoint-protection-site-role.md)|Endpoint Protection을 사용하려면 먼저 Endpoint Protection 지점 사이트 시스템 역할을 설치해야 합니다. 하나의 사이트 시스템 서버에만 설치해야 하며, 중앙 관리 사이트 또는 독립 실행형 기본 사이트의 계층 구조 맨 위에 설치해야 합니다. |  
|**2단계:** [Endpoint Protection에 대한 경고 구성](endpoint-configure-alerts.md)|경고는 맬웨어 감염과 같은 특정 이벤트가 발생할 때 관리자에게 알립니다. **모니터링** 작업 영역의 **경고** 노드에 경고가 표시되거나, 필요에 따라 지정된 사용자에게 메일로 보낼 수 있습니다. |  
|**3단계:** [Endpoint Protection 클라이언트에 대한 정의 업데이트 원본 구성](endpoint-definition-updates.md)|다양한 원본을 사용하여 정의 업데이트를 다운로드하도록 Endpoint Protection을 구성할 수 있습니다. |  
|**4단계:** [기본 맬웨어 방지 정책 구성 및 사용자 지정 맬웨어 방지 정책 만들기](endpoint-antimalware-policies.md)|Endpoint Protection 클라이언트가 설치될 때 기본 맬웨어 방지 정책이 적용됩니다. 배포한 사용자 지정 정책은 기본적으로 클라이언트를 배포한 후 60분 내에 적용됩니다. Endpoint Protection 클라이언트를 배포하기 전에 맬웨어 방지 정책을 구성했는지 확인합니다. |  
|**5단계:** [Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성](endpoint-protection-configure-client.md)|사용자 지정 클라이언트 설정을 사용하여 계층 구조의 컴퓨터 컬렉션에 대한 Endpoint Protection 설정을 구성할 수 있습니다.<br /><br /> 참고: 계층 구조의 모든 컴퓨터에 적용하려는 경우가 아니면 기본 Endpoint Protection 클라이언트 설정을 구성하지 마세요. |  
