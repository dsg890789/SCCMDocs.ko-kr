---

title: "Windows 10에서 비즈니스용 Windows 업데이트와 통합 | Configuration Manager"
description: "비즈니스용 Windows 업데이트를 사용하면 Windows 업데이트 서비스에 연결된 장치에 대해 조직의 Windows 10 기반 장치를 최신 상태로 유지할 수 있습니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: c4c6e50d0e1a34653226369cffdc0bde905398fc


---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Windows 10에서 비즈니스용 Windows 업데이트와 통합

*적용 대상: System Center Configuration Manager(현재 분기)*

조직의 Windows 10 기반 장치를 WU(Windows 업데이트) 서비스에 직접 연결하면 WUfB(비즈니스용 Windows 업데이트)를 통해 최신 보안 방어 및 Windows 기능을 사용하여 이러한 장치를 항상 최신 상태로 유지할 수 있습니다. Configuration Manager에는 WUfB 및 WSUS를 사용하여 소프트웨어 업데이트를 가져오는 Windows 10 컴퓨터를 구분할 수 있는 기능이 있습니다.  

 Configuration Manager 클라이언트가 WUfB 또는 Windows 참가자를 포함하는 WU에서 업데이트를 수신하도록 구성된 경우에는 일부 Configuration Manager 기능을 더 이상 사용할 수 없습니다.  

-   Windows 업데이트 준수 보고:  

    -   Configuration Manager에서 WU에 게시되는 업데이트를 인식할 수 없습니다. WU에서 업데이트를 수신하도록 구성된 Configuration Manager 클라이언트는 해당 업데이트에 대해 Configuration Manager 콘솔에 **알 수 없음**을 표시합니다.  

    -   **알 수 없음** 상태는 WSUS의 검색 상태를 다시 보고하지 않은 클라이언트에만 사용되므로 전체적인 준수 상태 문제를 해결하기 어렵습니다.  이제 WU에서 업데이트를 수신하는 Configuration Manager 클라이언트도 포함됩니다.  

    -   업데이트 준수 상태를 기반으로 하는 조건부 액세스(회사 리소스 대상)는 WU에서 업데이트를 수신하는 클라이언트에 대해 예상대로 작동하지 않습니다. 해당 클라이언트가 Configuration Manager의 준수를 충족하지 않기 때문입니다.  

    -   정의 업데이트 준수는 전체 업데이트 준수 보고의 일부이며 역시 예상대로 작동하지 않습니다.  또한 정의 업데이트 준수는 조건부 액세스 평가의 일부이기도 합니다.  

-   업데이트 준수 상태를 기반으로 하는 Defender에 대한 전체 Endpoint Protection 보고에서는 검색 데이터가 누락되어 정확한 결과를 반환하지 않습니다.  

-   Configuration Manager는 WUfB에 연결하여 업데이트를 받는 클라이언트에 Office, IE, Visual Studio와 같은 Microsoft 업데이트를 배포할 수 없습니다.  

-   Configuration Manager는 WUfB에 연결하여 업데이트를 받는 클라이언트에 WSUS에 게시되고 Configuration Manager를 통해 관리되는 타사 업데이트를 배포할 수 없습니다.  

-   소프트웨어 업데이트 인프라를 사용하는 Configuration Manager 전체 클라이언트 배포는 WUfB에 연결하여 업데이트를 받는 클라이언트에 대해 작동하지 않습니다.  

## <a name="identify-clients-that-use-wufb-for-windows-10-updates"></a>Windows 10 업데이트를 위해 WUfB를 사용하는 클라이언트 식별  
 다음 절차를 사용하여 Windows 10 업데이트 및 업그레이드를 가져오는 데 WUfB를 사용하는 클라이언트를 식별하고, 이러한 클라이언트를 업데이트를 가져오는 데 WSUS를 사용하지 않도록 구성한 후, 클라이언트 에이전트 설정을 배포하여 해당 클라이언트에 소프트웨어 업데이트 워크플로를 사용하지 않도록 설정합니다.  

 **전제 조건**  

-   클라이언트에서 Windows 10 Desktop Pro 또는 Windows 10 Enterprise Edition 버전 1511 이상을 실행합니다.  

-   [비즈니스용 Windows 업데이트](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) 가 배포되어 있으며 클라이언트에서 WUfB를 사용하여 Windows 10 업데이트 및 업그레이드를 가져옵니다.  

#### <a name="to-identify-clients-that-use-wufb"></a>WUfB를 사용하는 클라이언트를 식별하려면 다음을 수행합니다.  

1.  이전에 설정된 경우 Windows 업데이트 에이전트를 사용하지 않도록 설정하여 WSUS에 대한 검사가 이루어지지 않도록 합니다.   
    레지스트리 키 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer**를 설정하여 컴퓨터에서 WSUS에 대해 검사할지 또는 Windows 업데이트에 대해 검사할지 지정할 수 있습니다.  값이 2이면 WSUS에 대해 검사하지 않는 것입니다.  

2.  Configuration Manager 리소스 탐색기의 **Windows 업데이트** 노드 아래에 새 특성 **UseWUServer**가 있습니다.  

3.  업데이트 및 업그레이드를 위해 WUfB를 통해 연결된 모든 컴퓨터에 대해 **UseWUServer** 특성을 기반으로 컬렉션을 만듭니다.  

4.  소프트웨어 업데이트 워크플로를 사용하지 않도록 클라이언트 에이전트 설정을 만들고 이 설정을 WUfB에 직접 연결된 컴퓨터 컬렉션에 배포합니다.  

5.  WUfB를 통해 관리되는 컴퓨터는 준수 상태가 **알 수 없음**으로 표시되며 전체 준수 비율의 일부로 계산되지 않습니다.  



<!--HONumber=Nov16_HO1-->


