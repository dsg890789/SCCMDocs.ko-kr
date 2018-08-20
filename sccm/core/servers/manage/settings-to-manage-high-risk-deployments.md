---
title: 높은 위험 수준의 배포 관리
titleSuffix: Configuration Manager
description: 높은 위험 수준의 배포를 만드는 경우 관리자에게 경고하도록 Configuration Manager에서 배포 확인 사이트 설정을 구성하는 방법을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ab2203b948887a94577826573ccdf3376637eca2
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39386024"
---
# <a name="settings-to-manage-high-risk-deployments-for-configuration-manager"></a>Configuration Manager에 대해 위험 수준이 높은 배포를 관리하기 위한 설정

*적용 대상: System Center Configuration Manager(현재 분기)*


Configuration Manager에서 배포 확인 사이트 설정을 구성할 수 있습니다. 이러한 설정은 위험 수준이 높은 작업 순서 배포를 만들면 관리자에게 경고합니다. 위험 수준이 높은 배포는 다음과 같습니다.  

-   자동으로 설치되는 배포  

-   예기치 않은 결과가 발생할 가능성이 있는 배포  

예를 들어 용도가 **필수**이며 운영 체제를 배포하는 작업 순서는 위험 수준이 높은 것으로 간주됩니다.  

위험 수준이 높은 불필요한 배포가 수행될 위험을 줄이려는 경우 다음과 같은 배포 확인 설정에서 크기 제한을 구성할 수 있습니다.  

-   **컬렉션 크기 제한**: 배포를 만들 때 클라이언트가 제한보다 많이 포함된 컬렉션을 숨깁니다.  

     -   **기본 크기**: 배포를 만들 때 이 설정은 배포를 만들 때 클라이언트가 이 제한보다 많이 포함된 컬렉션을 기본적으로 숨깁니다. 이러한 컬렉션은 배포를 만들 때 표시할 수 있지만 기본적으로는 숨겨집니다. 기본값은 **100**입니다. 이 설정을 무시하려면 값으로 **0**을 입력합니다.  

     -   **최대 크기**: 배포를 만들 때 이 설정은 배포를 만들 때 클라이언트가 이 제한보다 많은 컬렉션을 항상 숨깁니다. 기본값은 **0**으로, 이 설정을 무시합니다. **최대 크기** 값은 **기본 크기** 값보다 커야 합니다.  

     **기본 크기**를 100으로 설정하고 **최대 크기**를 1,000으로 설정하는 경우를 예로 들어 보겠습니다. 위험 수준이 높은 배포를 만들 때 **컬렉션 선택** 창에는 클라이언트 수가 100개 미만인 컬렉션만 표시됩니다. **사이트의 최소 크기 구성보다 많은 멤버 수가 포함된 컬렉션 숨기기** 설정의 선택을 취소하면 1,000개 미만의 클라이언트가 포함된 컬렉션이 창에 표시됩니다.  

-   **사이트 시스템 서버를 사용하는 컬렉션**: 대상 컬렉션에 사이트 시스템 역할을 사용하는 컴퓨터가 포함되어 있으면 배포를 차단하거나 배포를 만들기 전에 확인을 요청합니다. 배포가 차단되면 배포를 계속 만들기 위해 배포 확인 기준을 충족하는 다른 컬렉션을 선택합니다.  

> [!NOTE]  
>  위험 수준이 높은 배포는 항상 사용자 지정 컬렉션, 직접 작성하는 컬렉션 및 기본적으로 제공되는 **알 수 없는 컴퓨터** 컬렉션으로 제한됩니다. 위험 수준이 높은 배포를 만드는 경우 **모든 시스템**같은 기본 제공 컬렉션을 선택할 수 없습니다.  

### <a name="configure-deployment-verification-for-a-site"></a>사이트에 대한 배포 확인 구성  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택한 다음, 구성할 기본 사이트를 선택합니다.  

2.  리본 메뉴에서 **속성**을 클릭한 다음, **배포 확인** 탭으로 전환합니다.  

3.  사용하려는 구성을 설정한 후 **확인**을 클릭하여 구성을 저장합니다.  


### <a name="see-also"></a>참고 항목  
 [사이트 및 계층 구조 구성](/sccm/core/servers/deploy/configure/configure-sites-and-hierarchies)
