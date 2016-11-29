---
title: "준수 설정 계획 및 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 준수 설정으로 작업하기 위한 필수 조건 및 구성 작업에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ea20b01-676a-4cc2-b328-0098a41b202e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 43bbbacfcd0e873974c517f1cb870ebc4d5e003d


---
# <a name="plan-for-and-configure-compliance-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 준수 설정 계획 및 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 준수 설정 작업을 시작하기 전에 알아야 하는 몇 가지 필수 조건과 수행해야 하는 일부 구성 작업이 있습니다.  

## <a name="prerequisites-for-compliance-settings"></a>준수 설정의 필수 조건  

|필수 구성 요소|추가 정보|  
|------------------|----------------------|  
|준수 평가에 대해 Windows Configuration Manager 클라이언트를 사용하도록 설정하고 구성해야 합니다.|아래를 참조하세요.|  
|보고서를 실행하려면 사이트에 대해 보고를 구성해야 합니다.|[System Center Configuration Manager에서 보고](../../core/servers/manage/reporting.md)|  
|필요한 보안 권한입니다.|**준수 설정 관리자** 보안 역할에는 준수 설정, 사용자 데이터 및 프로필 구성 항목, 원격 연결 프로필 관리에 필요한 권한이 포함됩니다.<br /><br /> [역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)|  

##  <a name="enable-and-configure-compliance-settings-for-windows-pcs-only"></a>준수 설정 사용 및 구성(Windows PC에만 해당)  

이 절차에서는 준수 설정에 대한 기본 클라이언트 설정을 구성하고 계층 구조의 모든 컴퓨터에 적용합니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 사용자 지정 장치 클라이언트 설정을 만들어서 준수 설정을 사용할 컴퓨터가 포함된 컬렉션에 할당합니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

> [!TIP]  
>  다른 장치 유형의 경우 준수 설정을 평가하기 위한 특정 구성이 필요하지 않습니다.  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 설정**을 클릭합니다.  
2.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  
3.  **기본 설정** 대화 상자에서 **준수 설정**을 클릭합니다.  
4.  준수 설정에 대한 다음 클라이언트 설정을 구성합니다.
    - **클라이언트에서 준수 평가 사용** - 클라이언트 장치에서 준수를 평가하려면 **True**로 설정합니다.
    - **준수 평가의 일정** - 클라이언트 장치에서 기본 준수 평가 일정을 수정하려면 **일정**을 클릭합니다.
    - **사용자 데이터 및 프로필 구성 항목** - 사용자 데이터 및 프로필 구성 항목을 Windows 컴퓨터에 배포하려면 이 옵션을 사용하도록 설정합니다. 자세한 내용은 [사용자 데이터 및 프로필 구성 항목 만들기](/sccm/compliance/deploy-use/create-remote-connection-profiles)를 참조하세요.
5. **확인** 을 클릭하여 **기본 설정** 대화 상자를 닫습니다.  

클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다.  



<!--HONumber=Nov16_HO1-->


