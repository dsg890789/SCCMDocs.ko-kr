---
title: "Endpoint Protection 구성 | System Center Configuration Manager"
description: "Windows Defender에 대한 맬웨어 정의를 업데이트하고 배포하도록 Configuration Manager를 설정하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: c13ea976057a4267eb6ed0d5c5852b165de868cb


---

# <a name="configure-endpoint-protection-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Endpoint Protection 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

Endpoint Protection을 사용하여 Configuration Manager 클라이언트 컴퓨터의 보안 및 맬웨어를 관리하려면 먼저 이 항목에 자세히 설명된 구성 단계를 수행해야 합니다.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection을 구성하는 방법  
 Configuration Manager의 Endpoint Protection은 제어에는 외부 종속성과 제품 내 종속성이 있습니다.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection을 구성하는 단계  
 Endpoint Protection을 구성하는 단계, 정보 및 방법에 대한 추가 정보는 다음 표를 참조하세요.  

> [!IMPORTANT]  
>  Windows 10 컴퓨터의 Endpoint Protection을 관리하는 경우 Windows Defender에 대한 맬웨어 정의를 업데이트 및 배포하도록 Configuration Manager를 구성해야 합니다. Windows Defender는 Windows 10에 포함되어 있지만 SCEPInstall은 여전히 설치해야 하고 Endpoint Protection(아래 **5단계**)에 대한 사용자 지정 클라이언트 설정도 여전히 필요합니다.  

|단계|세부 정보|  
|-----------|-------------|  
|**1단계:** Endpoint Protection 지점 사이트 시스템 역할 만들기|Endpoint Protection을 사용하려면 먼저 Endpoint Protection 지점 사이트 시스템 역할을 설치해야 합니다. 하나의 사이트 시스템 서버에만 설치해야 하며, 중앙 관리 사이트 또는 독립 실행형 기본 사이트의 계층 구조 맨 위에 설치해야 합니다. 이 항목의 [1단계: Endpoint Protection 지점 사이트 시스템 역할 만들기](../../protect/deploy-use/configure-endpoint-protection.md#BKMK_Step1)를 참조하세요.|  
|**2단계:** Endpoint Protection에 대한 경고 구성|경고는 맬웨어 감염과 같은 특정 이벤트가 발생할 때 관리자에게 알립니다. **모니터링** 작업 영역의 **경고** 노드에 경고가 표시되거나, 필요에 따라 지정된 사용자에게 메일로 보낼 수 있습니다. [2단계: Endpoint Protection에 대한 경고 구성](../../protect/deploy-use/configure-endpoint-protection.md#BKMK_EPalerts)을 참조하세요.|  
|**3단계:** Endpoint Protection 클라이언트에 대한 정의 업데이트 원본을 구성합니다.|다양한 원본을 사용하여 정의 업데이트를 다운로드하도록 Endpoint Protection을 구성할 수 있습니다. [3단계: Endpoint Protection에 대한 정의 업데이트 구성](../../protect/deploy-use/configure-endpoint-protection.md#BKMK_EPdefs)을 참조하세요.|  
|**4단계:** 기본 맬웨어 방지 정책 구성 및 사용자 지정 맬웨어 방지 정책 만들기|Endpoint Protection 클라이언트가 설치될 때 기본 맬웨어 방지 정책이 적용됩니다. 배포한 사용자 지정 정책은 기본적으로 클라이언트를 배포한 후 60분 내에 적용됩니다. Endpoint Protection 클라이언트를 배포하기 전에 맬웨어 방지 정책을 구성했는지 확인합니다. [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](../../protect/deploy-use/endpoint-antimalware-policies.md)을 참조하세요.|  
|**5단계:** Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성|사용자 지정 클라이언트 설정을 사용하여 계층 구조의 컴퓨터 컬렉션에 대한 Endpoint Protection 설정을 구성할 수 있습니다.<br /><br /> 참고: 계층 구조의 모든 컴퓨터에 적용하려는 경우가 아니면 기본 Endpoint Protection 클라이언트 설정을 구성하지 마세요. 이 항목의 [5단계: Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성](../../protect/deploy-use/configure-endpoint-protection.md#BKMK_EPclient)을 참조하세요.|  



<!--HONumber=Nov16_HO1-->


