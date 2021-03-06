---
title: App-V 가상 환경 만들기
titleSuffix: Configuration Manager
description: 앱이 데이터를 서로 공유할 수 있도록 Microsoft Application Virtualization을 사용하여 가상 환경을 만듭니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2280218d3d237f91f0db3150dbc2031bad3e1816
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75816006"
---
# <a name="create-app-v-virtual-environments-in-configuration-manager"></a>Configuration Manager에서 App-V 가상 환경을 만들기

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 Microsoft Application Virtualization(App-V) 가상 환경에서는 배포된 가상 애플리케이션이 클라이언트 Windows PC에 있는 동일한 파일 시스템과 레지스트리를 공유할 수 있습니다. 표준 가상 애플리케이션과 달리 이러한 애플리케이션은 서로 데이터를 공유할 수 있습니다. 애플리케이션이 설치되거나 클라이언트에서 다음번에 설치된 애플리케이션을 평가할 때 클라이언트 PC에서 가상 환경이 만들어지거나 수정됩니다. 여러 애플리케이션이 파일시스템 또는 레지스트리 값을 수정하려는 경우 우선 순위가 가장 높은 애플리케이션이 우선권을 가질 수 있도록 이러한 애플리케이션의 순서를 지정할 수 있습니다.  

> [!IMPORTANT]  
>  App-V 가상 환경을 사용하여 보안 보호(예: 맬웨어 차단)를 제공해서는 안 됩니다.  

 Configuration Manager에서 App-V 가상 환경을 만들려면 다음 절차를 따르세요.  

## <a name="create-an-app-v-virtual-environment"></a>App-V 가상 환경 만들기  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **애플리케이션 관리** > **App-V 가상 환경**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **가상 환경 만들기**를 선택합니다.  

4.  **가상 환경 만들기** 대화 상자에서 다음 정보를 입력합니다.  

    -   **이름**.  가상 환경의 고유 이름을 입력합니다(최대 128자).  

    -   **설명**. (선택 사항) 가상 환경에 대한 설명을 입력합니다.  

5.  새 배포 유형을 가상 환경에 추가하려면 **추가**를 선택합니다. 하나 이상의 배포 유형을 추가해야 합니다.  

6.  **애플리케이션 추가** 대화 상자에서 **그룹 이름**(최대 128자)을 지정합니다. 이 이름을 사용하여 가상 환경에 추가하는 애플리케이션 그룹을 참조합니다.  

7.  **추가**를 선택하고 그룹에 추가할 App-V 5 애플리케이션과 배포 유형을 선택한 후에 **확인**을 선택합니다.  

8.  **애플리케이션 추가** 대화 상자에서 **순서 높이기** 또는 **순서 낮추기**를 선택하여, 여러 애플리케이션이 동일한 가상 환경에서 파일 시스템 또는 레지스트리 설정을 수정할 경우에 우선 순위를 가질 애플리케이션을 설정할 수 있습니다.  

9. **가상 환경 만들기** 대화 상자로 돌아가려면 **확인**을 선택합니다.  

10. 그룹 추가를 완료했으면 **확인**을 선택하여 가상 환경을 만듭니다. Configuration Manager 콘솔의 **App-V 가상 환경** 노드에 새 가상 환경이 표시됩니다. App-V 가상 환경 상태 보고서를 사용하여 가상 환경의 상태를 모니터링할 수 있습니다.  

    > [!NOTE]  
    >  애플리케이션이 설치되거나 클라이언트에서 다음번에 설치된 애플리케이션을 평가할 때 클라이언트 PC에서 가상 환경이 추가되거나 수정됩니다.  
