---
title: Endpoint Protection에 대한 Windows 방화벽 정책
titleSuffix: Configuration Manager
description: System Center 2012 Configuration Manager에서 Endpoint Protection에 대한 Windows 방화벽 정책을 만들어 배포하는 방법을 알아봅니다.
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 6ecdfad1-6305-45a8-ae75-3f33b967cb8f
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: b1e8ab5b0e6c45d86a0973093e8b405aa7762f87
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75820239"
---
# <a name="create-and-deploy-windows-firewall-policies-for-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection에 대한 Windows 방화벽 정책을 만들어 배포

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager에서 Endpoint Protection에 대한 방화벽 정책을 사용하면 계층의 클라이언트 컴퓨터에서 기본 Windows 방화벽 구성 및 유지 관리 작업을 수행할 수 있습니다. Windows 방화벽 정책을 사용하여 다음 작업을 수행할 수 있습니다.  

-   Windows 방화벽이 켜져 있는지 여부를 제어합니다.  

-   클라이언트 컴퓨터에 들어오는 연결의 허용 여부를 제어합니다.  

-   Windows 방화벽이 새 프로그램을 차단할 때 사용자에 게 알림을 보내는 지 여부를 제어 합니다.  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Endpoint Protection**을 확장하고 **Windows 방화벽 정책**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **Windows 방화벽 정책 만들기**를 클릭합니다.  

4.  **Windows 방화벽 정책 만들기 마법사** 의 **일반**페이지에서 이 방화벽 정책의 이름과 설명(선택 사항)을 지정하고 **다음**을 클릭합니다.  

5.  마법사의 **프로필 설정** 페이지에서 각 네트워크 프로필에 대해 다음 설정을 구성합니다.  

    > [!IMPORTANT]  
    >  Windows Server 2008 및 Windows Vista 서비스 팩 1을 실행하는 컴퓨터에 Windows 방화벽 정책을 배포하려면 먼저 해당 컴퓨터에 [핫픽스 KB971800](https://go.microsoft.com/fwlink/p/?LinkId=231239) 을 설치해야 합니다.  

    > [!NOTE]  
    >  네트워크 프로필에 대한 자세한 내용은 Windows 설명서를 참조하세요.  

    -   **Windows 방화벽 사용**  

        > [!NOTE]  
        >  **Windows 방화벽 사용** 을 설정하지 않으면 마법사의 이 페이지에서 다른 설정을 사용할 수 없습니다.  

    -   **허용되는 프로그램 목록에 있는 연결을 포함하여 들어오는 모든 연결 차단**  

    -   **Windows 방화벽이 새 프로그램을 차단할 때 사용자에게 알림**  

6.  마법사의 **요약** 페이지에서 수행할 작업을 검토한 후 마법사를 완료합니다.  

7.  새 Windows 방화벽 정책이 **Windows 방화벽 정책** 목록에 표시되는지 확인합니다.  

##  <a name="BKMK_Assign"></a> Windows 방화벽 정책을 배포하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **Endpoint Protection**을 확장하고 **Windows 방화벽 정책**을 클릭합니다.  

3.  **Windows 방화벽 정책** 목록에서 배포할 Windows 방화벽 정책을 선택합니다.  

4.  **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

5.  **Windows 방화벽 정책 배포** 대화 상자에서 Windows 방화벽 정책을 할당할 컬렉션을 지정하고 할당 일정을 지정합니다. Windows 방화벽 정책은 이 일정과 클라이언트의 Windows 방화벽 설정으로 준수를 평가하여 Windows 방화벽 정책에 맞게 다시 구성합니다.  

6.  **확인** 을 클릭하여 **Windows 방화벽 정책 배포** 대화 상자를 닫고 Windows 방화벽 정책을 배포합니다.  

    > [!IMPORTANT]  
    >  컬렉션에 Windows 방화벽 정책을 배포하는 경우 네트워크 사용 초과를 방지하기 위해 2시간에 걸쳐 임의 순서로 컴퓨터에 이 정책을 적용합니다.
