---
title: "원격 제어 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 원격 제어를 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
caps.latest.revision: 4
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: aea35afe970e20bc2b22f9ae3f413a3c735caae1


---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 원격 제어 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 원격 제어를 사용하려면 다음 구성 단계를 수행해야 합니다.  

## <a name="how-to-enable-remote-control-and-configure-client-settings"></a>원격 제어를 사용하도록 설정하고 클라이언트 설정을 구성하는 방법  
 이 절차는 원격 제어에 대한 기본 클라이언트 설정 구성에 대해 설명하며 계층의 모든 컴퓨터에 적용됩니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 사용자 지정 장치 클라이언트 설정을 만들어서 원격 제어 세션에서 사용할 컴퓨터가 포함된 컬렉션에 할당합니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>원격 제어를 사용하도록 설정하고 클라이언트 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.  

3.  **기본 클라이언트 설정**을 클릭합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  **기본**  대화 상자에서 **원격 도구**를 클릭합니다.  

6.  필요한 원격 제어, 원격 지원 및 원격 데스크톱 클라이언트 설정을 구성합니다. 구성할 수 있는 원격 도구 클라이언트 설정 목록은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../../core/clients/deploy/about-client-settings.md) 항목의 [원격 도구](../../../../core/clients/deploy/about-client-settings.md#BKMK_RemoteToolsDeviceSettings) 섹션을 참조하세요.  

    > [!NOTE]  
    >  **컴퓨터 에이전트** 클라이언트 설정의 **소프트웨어 센터에 표시되는 조직 이름** 에 대한 값을 구성하여 **ConfigMgr 원격 제어** 대화 상자에 표시되는 회사 이름을 변경할 수 있습니다.  

    > [!IMPORTANT]  
    >  원격 지원 또는 원격 데스크톱을 사용하려면 Configuration Manager 콘솔을 실행하는 컴퓨터에 설치되고 구성되어야 합니다. 원격 지원 또는 원격 데스크톱을 설치하고 구성하는 방법에 대한 자세한 내용은 Windows 설명서를 참조하세요.  

7.  **확인** 을 클릭하여 **기본 설정** 대화 상자를 닫습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  



<!--HONumber=Nov16_HO1-->


