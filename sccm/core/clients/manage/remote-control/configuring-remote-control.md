---
title: "원격 제어 구성 | Microsoft 문서"
description: "System Center Configuration Manager에서 원격 제어를 설정합니다."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: dudeso
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
ms.sourcegitcommit: 88828e68bc4aff216e83807ea8288c7d42c60cbd
ms.openlocfilehash: cbfa9dc6cb37518c0a561700272cc882b0041350


---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 원격 제어 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

 이 절차는 원격 제어에 대한 기본 클라이언트 설정 구성에 대해 설명하며 계층의 모든 컴퓨터에 적용됩니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 사용자 지정 장치 클라이언트 설정을 만들어서 원격 제어 세션에서 사용할 컴퓨터가 포함된 컬렉션에 할당합니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요. 

원격 지원 또는 원격 데스크톱을 사용하려면 Configuration Manager 콘솔을 실행하는 컴퓨터에 설치되고 구성되어야 합니다. 원격 지원 또는 원격 데스크톱을 설치하고 구성하는 방법에 대한 자세한 내용은 Windows 설명서를 참조하세요.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>원격 제어를 사용하도록 설정하고 클라이언트 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **기본** 대화 상자에서 **원격 도구**를 선택합니다.  

6.  원격 제어, 원격 지원 및 원격 데스크톱 클라이언트 설정을 구성합니다. 구성할 수 있는 원격 도구 클라이언트 설정 목록은 [원격 도구](../../../../core/clients/deploy/about-client-settings.md#remote-tools)를 참조하세요.  

    **컴퓨터 에이전트** 클라이언트 설정의 **소프트웨어 센터에 표시되는 조직 이름** 에 대한 값을 구성하여 **ConfigMgr 원격 제어** 대화 상자에 표시되는 회사 이름을 변경할 수 있습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  



<!--HONumber=Dec16_HO1-->


