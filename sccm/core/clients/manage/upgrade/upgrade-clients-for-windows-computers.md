---
title: "클라이언트 업그레이드 | Microsoft 문서"
description: "System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트 업그레이드"
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6143fd47-48ec-4bca-b53b-5b9b9f067bc3
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 98b8c92e4dad3cef1ed3701b9c0f9111eb9941ea
ms.contentlocale: ko-kr
ms.lasthandoff: 05/05/2017


---
# <a name="how-to-upgrade-clients-for-windows-computers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트를 업그레이드하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 클라이언트 설치 방법 또는 자동 클라이언트 업그레이드 기능을 사용하여 Windows 컴퓨터에서 클라이언트를 업그레이드할 수 있습니다. 다음과 같은 클라이언트 설치 방법이 Windows 컴퓨터에서 클라이언트 소프트웨어를 업그레이드하는 올바른 방법입니다.  

-   그룹 정책 설치  

-   로그온 스크립트 설치  

-   수동 설치  

-   업그레이드 설치  

 클라이언트 설치 방법을 사용하는 클라이언트 업그레이드에 관심이 있는 경우 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)에서 해당 방법 사용에 대해 자세히 알아보세요.

 버전 1610부터 제외 그룹을 지정하여 클라이언트가 업그레이드되지 않도록 제외할 수 있습니다. 자세한 내용은 [Windows 컴퓨터에서 클라이언트 업그레이드를 제외하는 방법](exclude-clients-windows.md)을 참조하세요.  


> [!TIP]  
>  이전 버전의 Configuration Manager\(예: Configuration Manager 2007 또는 System Center 2012 Configuration Manager\)에서 서버 인프라를 업그레이드하는 경우 Configuration Manager 클라이언트를 업그레이드하기 전에 현재 분기 업데이트를 모두 설치하는 등 서버를 업그레이드하는 것이 좋습니다.   최신 현재 분기 업데이트에는 클라이언트의 최신 버전이 포함되어 있으므로 사용하려는 Configuration Manager 업데이트를 모두 설치한 후에 클라이언트 업그레이드를 수행하는 것이 좋습니다.

> [!NOTE]
> 업그레이드 중에 클라이언트에 대한 사이트를 다시 할당하려는 경우 SMSSITECODE client.msi 속성을 사용하여 새 사이트를 지정할 수 있습니다. SMSSITECODE에 AUTO를 사용하는 경우 SITEREASSIGN=TRUE를 지정하여 업그레이드 중에 자동 사이트 다시 할당도 수행되도록 지정해야 합니다. 자세한 내용은 [SMSSITECODE](../../deploy/about-client-installation-properties.md#smssitecode)를 참조하세요.

## <a name="use-automatic-client-upgrade"></a>자동 클라이언트 업그레이드 사용  
 또한 Configuration Manager에서 Configuration Manager 계층 구조에 할당된 클라이언트가 계층 구조에서 사용되는 버전보다 이전 버전임을 확인할 경우 클라이언트 소프트웨어를 최신 Configuration Manager 클라이언트 버전으로 자동 업그레이드하도록 Configuration Manager를 구성할 수 있습니다. 이 시나리오에는 클라이언트가 Configuration Manager 사이트에 할당을 시도할 때 해당 클라이언트를 최신 버전으로 업그레이드하는 작업이 포함됩니다.  

 다음 시나리오에서 클라이언트는 자동으로 업그레이드될 수 있습니다.  

-   클라이언트 버전이 계층에서 사용 중인 버전보다 낮습니다.  

-   중앙 관리 사이트의 클라이언트에 언어 팩이 설치되어 있고 기존 클라이언트에는 설치되어 있지 않습니다.  

-   계층의 클라이언트 필수 구성 요소가 클라이언트에 설치된 필수 구성 요소와 버전이 다릅니다.  

-   하나 이상의 클라이언트 설치 파일이 다른 버전입니다.  

> [!NOTE]  
>  **사이트 - 클라이언트 정보** 보고서 폴더에서 **클라이언트 버전별 Configuration Manager 클라이언트 수** 보고서를 실행하면 계층 구조에 있는 Configuration Manager 클라이언트의 각기 다른 버전을 확인할 수 있습니다.  

 Configuration Manager는 기본적으로 계층 구조 내 모든 배포 지점에 자동으로 전송되는 업그레이드 패키지를 만듭니다. 중앙 관리 사이트의 클라이언트 패키지를 변경(예: 클라이언트 언어 팩 추가)할 경우 Configuration Manager는 패키지를 자동으로 업데이트하고 이 패키지를 계층 구조 내 모든 배포 지점에 배포합니다. 자동 클라이언트 업그레이드를 사용하도록 설정하면 모든 클라이언트에 새 클라이언트 언어 패키지가 자동으로 설치됩니다.  

> [!NOTE]  
>  Configuration Manager는 Configuration Manager 클라우드 기반 배포 지점에 클라이언트 업그레이드 패키지를 자동으로 보내지 않습니다.  

 계층 구조 전체에서 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 이렇게 하면 관리 오버헤드를 최소화하여 클라이언트가 계속 업데이트됩니다.  

 자동 클라이언트 업그레이드를 구성하려면 다음 절차를 따르세요. 자동 클라이언트 업그레이드는 중앙 관리 사이트에 구성해야 하며 이 구성은 계층 내 모든 클라이언트에 적용됩니다.  

### <a name="to-configure-automatic-client-upgrades"></a>자동 클라이언트 업그레이드를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.  

3.  **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 클릭합니다.  

4.  **계층 구조 설정 속성** 대화 상자의 **클라이언트 업그레이드** 탭에서, 프로덕션 클라이언트의 버전 및 날짜를 검토하고 이 버전이 Windows 컴퓨터를 업그레이드하는 데 사용하려는 버전인지 확인합니다.  필요한 클라이언트 버전이 아닌 경우 사전 프로덕션 클라이언트 수준을 프로덕션으로 올려야 할 수도 있습니다. 자세한 내용은 [System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](../../../../core/clients/manage/upgrade/test-client-upgrades.md)을 참조하세요.  

5.  **프로덕션 클라이언트를 사용하여 계층 구조의 모든 클라이언트 업그레이드** 를 클릭하고 확인 대화 상자에서 **확인** 을 클릭합니다.  

6.  서버에 클라이언트 업그레이드를 적용하지 않으려면 **서버 업그레이드 안 함**을 클릭합니다.  

7.  컴퓨터가 클라이언트 정책을 수신한 후 클라이언트를 업그레이드할 때까지 허용되는 일수를 지정합니다. 클라이언트는 이 일 수가 경과되기 전에 임의의 간격으로 업그레이드됩니다. 이렇게 하면 여러 클라이언트 컴퓨터가 동시에 업그레이드되는 상황을 방지할 수 있습니다.

    > [!NOTE]
    > 클라이언트를 업그레이드하려면 컴퓨터가 실행되고 있어야 합니다. 업그레이드를 받도록 예약된 시간에 컴퓨터가 실행되고 있지 않으면 업그레이드가 발생하지 않습니다. 대신 컴퓨터를 다시 시작할 때 다른 업그레이드가 허용된 시간(일) 내의 임의 시간으로 예약됩니다. 이때 업그레이드할 기간(일)이 만료된 후이면 업그레이드가 컴퓨터를 다시 시작한 후 24시간 내의 임의 시간으로 예약됩니다.
    >     
    > 이 동작으로 인해 업무가 끝나면 정기적으로 종료되는 컴퓨터에서는 임의로 예약된 업그레이드 시간이 정상 근무 시간 내에 없을 경우 업그레이드하는 데 예상보다 오래 걸릴 수 있습니다.

7. 버전 1610부터 클라이언트가 업그레이드되지 않도록 제외하려는 경우 **Exclude specified clients from upgrade**(지정된 클라이언트를 업그레이드에서 제외)를 클릭하고 제외할 컬렉션을 지정합니다.

8.  클라이언트 설치 패키지를 사전 준비된 콘텐츠에 대해 설정된 배포 지점에 복사하려면 **클라이언트 설치 패키지를 사전 준비된 콘텐츠에 대해 설정된 배포 지점에 자동으로 배포**를 클릭합니다.  

9. **확인** 을 클릭하여 설정을 저장하고 **계층 구조 설정 속성** 대화 상자를 닫습니다. 클라이언트는 다음에 정책을 다운로드할 때 이 설정을 수신합니다.

>[!NOTE]
>클라이언트 업그레이드는 사용자가 구성한 Configuration Manager 유지 관리 기간을 준수합니다.

