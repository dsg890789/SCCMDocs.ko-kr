---
title: "원격 제어 구성 | Microsoft 문서"
description: "System Center Configuration Manager에서 원격 제어를 설정합니다."
ms.custom: na
ms.date: 12/26/2016
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
ms.sourcegitcommit: 9206b82eca02877c30eebf146d42bcca7290eb42
ms.openlocfilehash: 20c28a625adb69f239b9c0e7673e57dd39e8d561


---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 원격 제어 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

 이 절차에서는 원격 제어용 기본 클라이언트 설정을 구성하는 방법에 대해 설명합니다. 이러한 설정은 계층의 모든 컴퓨터에 적용됩니다. 이러한 설정이 일부 컴퓨터에만 적용되도록 하려면 원하는 컴퓨터가 포함된 컬렉션에 사용자 지정 장치 클라이언트 설정을 할당합니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요. 

원격 지원 또는 원격 데스크톱을 사용하려면 Configuration Manager 콘솔을 실행하는 컴퓨터에 설치되고 구성되어야 합니다. 원격 지원 또는 원격 데스크톱을 설치하고 구성하는 방법에 대한 자세한 내용은 Windows 설명서를 참조하세요.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>원격 제어를 사용하도록 설정하고 클라이언트 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **기본** 대화 상자에서 **원격 도구**를 선택합니다.  

6.  원격 제어, 원격 지원 및 원격 데스크톱 클라이언트 설정을 구성합니다. 구성할 수 있는 원격 도구 클라이언트 설정 목록은 [원격 도구](../../../../core/clients/deploy/about-client-settings.md#remote-tools)를 참조하세요.  

    **컴퓨터 에이전트** 클라이언트 설정의 **소프트웨어 센터에 표시되는 조직 이름** 에 대한 값을 구성하여 **ConfigMgr 원격 제어** 대화 상자에 표시되는 회사 이름을 변경할 수 있습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  

#### <a name="enable-keyboard-translation"></a>키보드 변환 사용

Configuration Manager에서는 기본적으로 뷰어의 위치에서 공유자의 위치로 키 위치를 전송합니다. 이로 인해 뷰어와 공유자 간의 키보드 구성이 다를 경우 문제가 발생할 수 있습니다. 예를 들어 영어 키보드를 사용하는 뷰어는 "A"를 입력하지만 공유자의 프랑스어 키보드는 "Q"를 제공합니다. 이제는 뷰어의 키보드에서 공유자에게 문자 자체가 전송되며 뷰어가 입력하려고 했던 내용이 공유자에게 전달되도록 원격 제어를 구성하는 옵션이 제공됩니다.

키보드 변환을 설정하려면 **Configuration Manager 원격 제어**에서 **작업**, **키보드 변환 사용**을 선택하여 키 위치를 전송합니다.

> [!NOTE]
>
> ~!#@$%, 등의 특수 키는 올바르게 변환되지 않습니다.


## <a name="keyboard-shortcuts-for-the-remote-control-viewer"></a>원격 제어 뷰어를 위한 바로 가기 키

|키보드 바로 가기 키|설명|  
|-----------------------|-----------------|  
|Alt+Page Up|실행 중인 프로그램 간에 왼쪽에서 오른쪽으로 전환합니다.|  
|Alt+Page Down|실행 중인 프로그램 간에 오른쪽에서 왼쪽으로 전환합니다.|  
|Alt+Insert|실행중인 프로그램을 열린 순서대로 돌아가며 선택합니다.|  
|Alt+Home|**시작** 메뉴를 표시합니다.|  
|Ctrl+Alt+End|Windows 보안 대화 상자를 표시합니다(Ctrl+Alt+Del).|  
|Alt+Delete|Windows 메뉴를 표시합니다.|  
|Ctrl+Alt+빼기 기호(숫자 키패드의 키)|로컬 컴퓨터의 활성 창을 원격 컴퓨터 클립보드에 복사합니다.|  
|Ctrl+Alt+더하기 기호(숫자 키패드의 키)|전체 로컬 컴퓨터의 창 영역을 원격 컴퓨터 클립보드에 복사합니다.|  



<!--HONumber=Dec16_HO5-->


