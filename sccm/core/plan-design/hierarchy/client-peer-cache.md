---
title: "클라이언트 피어 캐시 | System Center Configuration Manager"
description: "System Center Configuration Manager를 사용하여 콘텐츠를 배포할 때는 클라이언트 콘텐츠 원본 위치에 대해 피어 캐시를 사용합니다."
ms.custom: na
ms.date: 2/13/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 6aaa833c1301cf82f7d8df3bc13f0a6936fc6e9d
ms.openlocfilehash: 96b3a72a7beb31396813ae468ae3eeacc845b582

---
# <a name="peer-cache-for-configuration-manager-clients"></a>Configuration Manager 클라이언트용 피어 캐시

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 버전 1610부터는 **피어 캐시**를 사용하여 원격 위치의 클라이언트에 대한 콘텐츠 배포를 관리할 수 있습니다. 피어 캐시는 클라이언트가 로컬 캐시의 콘텐츠를 다른 클라이언트와 직접 공유할 수 있도록 하는 기본 제공 Configuration Manager 솔루션입니다.   

> [!TIP]  
> 버전 1610의 경우 피어 캐시 및 클라이언트 데이터 원본 대시보드는 시험판 기능입니다. 이러한 기능을 사용하도록 설정하려면 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease)을 참조하세요.

 -     클라이언트 설정을 사용하여 클라이언트가 피어 캐시를 사용하도록 설정합니다.
 -     콘텐츠를 공유하려면 두 피어 캐시 클라이언트가 모두 콘텐츠를 검색하는 클라이언트의 현재 경계 그룹 구성원이어야 합니다. 클라이언트가 대체 기능을 사용해 인접 경계 그룹의 콘텐츠를 검색할 때 인접 경계 그룹의 피어 캐시 클라이언트는 사용 가능한 콘텐츠 원본 위치 풀에 포함되지 않습니다. 현재 및 인접 경계 그룹에 대한 자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups)을 참조하세요.
 - 피어 캐시에 사용하도록 설정되어 있지는 않지만 피어 캐시 사용 클라이언트가 있는 현재 경계 그룹에 포함되는 클라이언트는 피어 캐시 사용 클라이언트에서 콘텐츠를 가져올 수 있습니다.  
 - Configuration Manager 클라이언트의 캐시에 저장된 모든 유형의 콘텐츠를 피어 캐시를 사용하여 다른 클라이언트에 제공할 수 있습니다.
 -    피어 캐시는 BranchCache와 같은 다른 솔루션의 사용을 대체하지는 않지만 함께 사용하는 경우 배포 지점과 같은 기존 콘텐츠 배포 솔루션을 확장할 수 있는 더 많은 옵션을 제공할 수 있습니다. 피어 캐시는 BranchCache를 사용하지 않는 사용자 지정 솔루션이므로 Windows BranchCache를 사용하도록 설정하거나 사용하지 않더라도 계속 작동합니다.

피어 캐시를 사용하도록 설정된 클라이언트 설정을 컬렉션에 배포하고 나면 해당 컬렉션의 멤버가 동일 경계 그룹에서 다른 클라이언트의 피어 콘텐츠 원본 역할을 할 수 있습니다.
 -    피어 콘텐츠 원본으로 작동하는 클라이언트는 사용할 수 있는 캐시된 콘텐츠 목록을 해당 관리 지점에 제출합니다.
 -    그러면 해당 경계 그룹의 다음 클라이언트가 이 콘텐츠를 요청할 때 해당 콘텐츠를 보유하고 있는 각 피어 캐시 원본이 사용 가능한 콘텐츠 원본으로 반환되며, 해당 경계 그룹의 배포 지점 및 기타 콘텐츠 원본 위치도 함께 반환됩니다.
 -    정상 작동 프로세스에서 콘텐츠를 검색하는 클라이언트는 제공된 원본 풀에서 콘텐츠 원본 하나를 선택한 다음 해당 콘텐츠를 가져오려고 합니다.

> [!NOTE]
> 콘텐츠를 인접 경계 그룹에서 가져오려는 대체 방식이 사용되는 경우 인접 경계 그룹의 피어 캐시 콘텐츠 원본 위치는 클라이언트의 사용 가능한 콘텐츠 원본 위치 풀에 추가되지 않습니다.  

모든 클라이언트가 피어 캐시에 참여하도록 할 수는 있지만, 피어 캐시 원본으로 사용하기에 가장 적합한 클라이언트만 선택하는 것이 가장 좋습니다.  클라이언트의 섀시 종류, 디스크 공간, 네트워크 연결 등에 따라 클라이언트의 적합성을 평가할 수 있습니다. 피어 캐시에 사용하기에 가장 적합한 클라이언트를 선택하는 데 도움이 되는 자세한 내용은 [Microsoft 컨설턴트의 블로그](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/)를 참조하세요.

클라이언트 데이터 원본 대시보드를 확인하면 피어 캐시 사용법을 쉽게 파악할 수 있습니다. [클라이언트 데이터 원본 대시보드](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)를 참조하세요.


## <a name="requirements-and-considerations-for-peer-cache"></a>피어 캐시에 대한 요구 사항 및 고려 사항
- 피어 캐시는 Configuration Manager 클라이언트로 지원되는 모든 Windows 운영 체제에서 지원됩니다. Windows가 아닌 운영 체제는 피어 캐시에 대해 지원되지 않습니다.

- 각 클라이언트의 캐시 폴더에 대해 **모든 권한**을 가진 **네트워크 액세스 계정**으로 사이트를 구성해야 합니다. 기본적으로 이 폴더는 ***%windir%\ccmcache***입니다.

- 클라이언트는 현재 경계 그룹에 포함되어 있는 피어 캐시 클라이언트의 콘텐츠만 전송할 수 있습니다.

-     피어 캐시 콘텐츠 원본의 현재 경계는 해당 클라이언트의 마지막 하드웨어 인벤토리 제출에 따라 결정되므로, 다른 경계 그룹에 있는 네트워크 위치로 로밍하는 클라이언트는 피어 캐시에서 이전 경계 그룹의 구성원으로 계속 간주될 수 있습니다. 이 경우 직접적으로 속해 있는 네트워크 위치에 있지 않은 피어 캐시 콘텐츠 원본이 클라이언트에 제공될 수 있습니다. 따라서 이러한 구성을 사용할 가능성이 높은 클라이언트는 피어 캐시 원본으로 참여하지 않도록 제외하는 것이 좋습니다.

## <a name="to-configure-client-peer-cache-client-settings"></a>클라이언트 피어 캐시 클라이언트 설정을 구성하려면
1.    Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동한 다음 사용할 장치 클라이언트 설정 개체를 엽니다. 기본 클라이언트 설정 개체를 수정할 수도 있습니다.
2.    사용 가능한 설정 목록에서 **클라이언트 캐시 설정**을 선택합니다.
3.    **콘텐츠를 공유하도록 정품 OS에서 Configuration Manager 클라이언트 사용**을 **예**로 설정합니다.
4.    다음 설정을 구성하여 피어 캐시에 사용하려는 포트를 정의합니다.  
  -  **초기 네트워크 브로드캐스트를 위한 포트**
  -  **클라이언트 피어 통신에 대하여 HTTPS 사용**
  -  **피어에서 콘텐츠를 다운로드하기 위한 포트(HTTP/HTTPS)**

피어 캐시를 사용하도록 설정한 각 컴퓨터에서 Windows 방화벽을 사용하고 있는 경우 Configuration Manager는 여기서 구성하는 포트 사용을 허용하도록 방화벽을 구성합니다.



<!--HONumber=Feb17_HO2-->


