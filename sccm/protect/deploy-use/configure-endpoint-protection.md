---
title: "Endpoint Protection 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager의 클라이언트 컴퓨터에서 보안 및 맬웨어를 관리하는 방법을 알아봅니다."
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
ms.openlocfilehash: 5905ab3f63a9956909f3d26136a377ca2f65b71c


---
# <a name="configuring-endpoint-protection-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Endpoint Protection 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

Endpoint Protection을 사용하여 Configuration Manager 클라이언트 컴퓨터에서 보안 및 맬웨어를 관리하려면 먼저 이 항목을 사용하여 설정해야 합니다.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection을 구성하는 방법  
 Configuration Manager의 Endpoint Protection에는 제품의 외부 종속성과 제품 내 종속성이 있습니다.  

### <a name="configure-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection 구성  
Endpoint Protection을 구성하는 작업은 5단계로 구성됩니다.

|단계|세부 정보|
|---|----|
|1단계|[Endpoint Protection 지점 사이트 시스템 역할 만들기](endpoint-protection-site-role.md) - Endpoint Protection 지점 사이트 시스템 역할을 설치합니다. |
|2단계|[Endpoint Protection에 대한 경고 구성](endpoint-configure-alerts.md) - 계층에서 특정 보안 이벤트가 발생할 때 관리자에게 알리도록 Endpoint Protection 경고를 구성합니다.|
|3단계 | [Endpoint Protection 클라이언트용 정의 업데이트 원본 구성](endpoint-definition-updates.md) - 클라이언트 컴퓨터에서 맬웨어 방지 정의를 최신으로 유지하기 위해 사용 가능한 방법을 선택합니다.|
|4단계|[기본 맬웨어 방지 정책 구성 및 사용자 지정 맬웨어 방지 정책 만들기](endpoint-antimalware-policies.md) - 기본 맬웨어 방지 정책은 Endpoint Protection 클라이언트가 설치될 때 적용되고 사용자 지정 정책은 클라이언트 배포 후 60분 이내에 적용됩니다.|
|5단계|[Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성](endpoint-protection-configure-client.md) - 컴퓨터 컬렉션에 배포하도록 Endpoint Protection에 대한 사용자 지정 클라이언트 설정을 구성합니다.|

> [!IMPORTANT]  
>  Windows 10 컴퓨터의 Endpoint Protection을 관리하는 경우 Windows Defender에 대한 맬웨어 정의를 업데이트 및 배포하도록 Configuration Manager를 구성해야 합니다. Windows Defender는 Windows 10에 포함되어 있지만 SCEPInstall은 여전히 설치해야 하고 Endpoint Protection에 대한 사용자 지정 클라이언트 설정(5단계)도 여전히 필요합니다.  



<!--HONumber=Nov16_HO1-->


