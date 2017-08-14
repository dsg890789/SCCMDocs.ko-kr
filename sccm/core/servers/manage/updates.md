---
title: "업데이트 | Microsoft 문서"
description: "**업데이트 및 서비스**라는 콘솔 내 서비스 메서드에 대해 알아봅니다. 이 방법을 사용하면 권장 업데이트를 손쉽게 찾아서 업데이트할 수 있습니다."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: 51
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: HT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: d46aca88111d4ee0e96b75ca5a3ec57aa4274d6d
ms.contentlocale: ko-kr
ms.lasthandoff: 07/29/2017

---
# <a name="updates-for-system-center-configuration-manager"></a>System Center Configuration Manager용 업데이트

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 **업데이트 및 서비스**라는 콘솔 내 서비스 메서드를 사용합니다. 이 콘솔 내 메서드는 Configuration Manager 인프라에 대한 권장 업데이트를 손쉽게 찾아서 설치할 수 있도록 합니다. 이 콘솔 내 서비스에는 대역 외 업데이트(예: 고객 환경 특유의 문제를 해결해야 하는 고객을 위한 핫픽스)가 추가로 제공됩니다.  

> [!TIP]  
> System Center Configuration Manager 사이트 및 계층 인프라를 관리할 때 *업그레이드*, *업데이트* 및 *설치*라는 용어는 세 가지 별도의 개념을 설명하는 데 사용됩니다. 각 용어가 어떻게 사용되는지 알아보려면 [업그레이드, 업데이트 및 설치 정보](/sccm/core/understand/upgrade-update-install)를 참조하세요.


 **다음 항목은 System Center Configuration Manager에 대한 다양한 업데이트 형식을 찾아서 설치하는 방법을 이해하는 데 유용합니다.**  

-   [System Center Configuration Manager의 콘솔 내 업데이트 설치](../../../core/servers/manage/install-in-console-updates.md)  

-   [System Center Configuration Manager의 서비스 연결 도구 사용](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [업데이트 등록 도구를 사용하여 System Center Configuration Manager에 핫픽스 가져오기](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [핫픽스 설치 관리자를 사용하여 System Center Configuration Manager의 업데이트 설치](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Technical Preview 분기를 사용하는 경우 해당 분기와 관련된 추가 정보는 [System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.


##  <a name="bkmk_Baselines"></a> 기준 및 업데이트 버전  
 System Center Configuration Manager 현재 분기의 첫 번째 릴리스는 버전 1511(기준선 버전)이었습니다. 최신 기준 버전에는 버전 1606 및 1702가 있습니다.

-   새 계층 구조에 새로운 사이트를 설치할 때 최신 기준 버전을 사용합니다.  

-   System Center 2012 Configuration Manager를 업그레이드하려면 기준 버전을 사용합니다. System Center Configuration Manager로 업그레이드 한 후에는 더 이상 기준 버전을 사용하여 최신 상태를 유지할 수 없으며 대신 [콘솔 내 업데이트](/sccm/core/servers/manage/install-in-console-updates)를 사용하여 최신 버전으로 업데이트해야 합니다.  

-   정기적으로 추가 기준 버전이 릴리스됩니다. 최신 기준 버전을 사용하여 새 계층을 설치하면 최신 버전을 제공하는 추가 인프라 업그레이드에 따라 오래된 버전의 Configuration Manager를 설치하는 것을 피할 수 있습니다.  

기준 버전을 설치한 후 콘솔 내 업데이트로 Configuration Manager에 대한 추가 버전을 사용할 수 있습니다. 콘솔 내 업데이트는 최신 버전의 Configuration Manager로 인프라를 업데이트합니다.  

-   최상위 사이트의 버전을 업데이트하기 위해 콘솔 내 업데이트를 설치합니다.  

-   중앙 관리 사이트에 설치하면, 사용자가 구성해 놓은 유지 관리 기간에 의해 차단되지 않는 한, 자식 기본 사이트에 자동으로 설치됩니다.  

-   보조 사이트를 콘솔 내에서 새로운 업데이트 버전으로 수동으로 업데이트합니다.  

업데이트를 설치하면, 해당 버전에 대한 설치 파일이 사이트 서버의 CD.Latest 폴더에 저장됩니다. 이러한 파일에 대한 자세한 내용은 [System Center Configuration Manager의 CD.Latest 폴더](../../../core/servers/manage/the-cd.latest-folder.md)를 참조하세요.  

-   CD.Latest 폴더의 파일은 사이트 복구 중에 사용되며 기준 버전을 더 이상 실행하지 않는 계층 구조 내에 추가적인 사이트를 설치하는 데 사용됩니다.  

-   CD.Latest의 설치 파일을 사용하여 새 계층 구조의 첫 번째 사이트를 설치하거나 System Center 2012 Configuration Manager에서 사이트를 업그레이드할 수 없습니다.  

Configuration Manager에 대한 일부 업데이트는 기존 인프라에 대한 콘솔 내 업데이트 버전과 새 기준 버전이 모두 제공됩니다.  

Configuration Manager의 다음 버전은 기준, 업데이트 또는 두 가지 버전이 모두 제공됩니다.  

|버전 |가용일|[지원 종료 날짜](/sccm/core/servers/manage/current-branch-versions-supported) |기준|콘솔 내 업데이트|  
|-------------|-----------|------------|--------------|------------------------|  
|[1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)<br /><br /> 5.00.8540.1000|2017년 7월 31일|2018년 7월 31일|아니요|예|
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|2017년 3월 27일| 2018년 3월 27일|예|예|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|2016년 11월 18일| 2017년 11월 18일|아니요|예|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|2016년 7월 22일| 2017년 7월 22일|아니요|예|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) 및 1606 핫픽스 롤업(KB3186654) </br></br>5.00.8412.1307*(참고 1)* |2016년 10월 12일| 2017년 10월 12일|예|아니요|
| 1602<br /><br /> 5.00.8355.1000|2016년 3월 11일| 2017년 3월 11일|아니요|예| 
| 1511 <br /><br /> 5.00.8325.1000|2015년 12월 8일| 2016년 12월 8일|예|아니요|  


*(참고 1)* 이 1606 및 1702 기준 미디어는 [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx)(볼륨 라이선스 서비스 센터)에서 Microsoft System Center 2016 또는 System Center Configuration Manager(현재 분기 및 장기 서비스 분기) 릴리스의 일부로 제공됩니다. 예를 들어 VLSC에서 *System Center Config Mgr(현재 분기 및 LTSB)*을 검색할 수 있으며 1606 및 1702 버전 기준 미디어가 반환되고 다운로드할 수 있습니다.

Configuration Manager 사이트의 버전을 확인하려면, 새 사이트와 콘솔 버전이 표시되는 콘솔의 왼쪽 위 모서리에서 **System Center Configuration Manager 정보** 로 이동합니다.  

##  <a name="bkmk_inconsole"></a> 콘솔 내 업데이트 및 서비스  
 현재 분기라고도 하는, 프로덕션이 준비된 System Center Configuration Manager 설치를 사용하는 경우 사용자가 설치하는 대부분의 업데이트는 업데이트 및 서비스 채널을 사용하여 제공됩니다. 이 메서드는 현재 인프라 버전 및 구성에 해당하는 업데이트를 식별하고, 다운로드하고 사용할 수 있게 만들며, Microsoft에서 모든 고객에게 권장하는 업데이트만 포함시킵니다.   
 여기에는 다음이 포함됩니다.  

-   새 버전(예: 버전 1610, 1702 또는 1706)  

-   업데이트(현재 버전에 대한 새로운 기능 포함)

-   핫픽스(사용자의 Configuration Manager 버전에 해당하며 모든 고객이 설치해야 함)

콘솔 내 업데이트는 안정성을 향상시키고, 일반적인 문제를 해결합니다. 모든 고객에게 해당하는 서비스 팩, 누적 업데이트, 핫픽스 및 Microsoft Intune용 확장의 이전 제품 버전에 대한 업데이트 유형을 대체합니다. 이러한 업데이트는 하나 이상의 다음 항목에 적용됩니다.  

-   기본 및 중앙 관리 사이트 서버  

-   사이트 시스템 역할 및 사이트 시스템 서버  

-   SMS 공급자 인스턴스  

-   Configuration Manager 콘솔  

-   Configuration Manager 클라이언트  

Configuration Manager는 서비스 연결 지점 사이트 시스템 역할을 Microsoft 클라우드 서비스 및 다운로드 센터와 동기화할 때 새로운 업데이트를 검색합니다.  

-   서비스 연결 지점이 온라인 모드이면, 사이트는 인프라에 해당하는 새 업데이트를 자동으로 식별하기 위해 Microsoft와 매일 동기화합니다.  업데이트 및 업데이트의 재배포 파일을 다운로드하기 위해 서비스 연결 지점 사이트 시스템 역할을 호스트하는 컴퓨터는 **시스템** 컨텍스트를 사용하여 인터넷 위치 go.microsoft.com 및 download.microsoft.com에 액세스합니다. 서비스 연결 지점이 연결하는 추가 위치에 대한 자세한 내용은 [System Center Configuration Manager의 서비스 연결 지점 정보](../../../core/servers/deploy/configure/about-the-service-connection-point.md)에서 [인터넷 액세스 요구 사항](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls)을 참조하세요.  

-   서비스 연결 지점이 오프라인 모드이면, 서비스 연결 도구를 사용하여 Microsoft 클라우드와 수동으로 동기화합니다. 자세한 내용은 [System Center Configuration Manager의 서비스 연결 도구 사용](../../../core/servers/manage/use-the-service-connection-tool.md)을 참조하세요.  

-   콘솔 내 업데이트는 개별적인 업데이트, 서비스 팩, 새 기능을 독립적으로 찾아서 설치할 필요성을 대체합니다.  

-   사용자가 선택한 콘솔 내 업데이트만 설치하면, 일부 업데이트를 설치할 때 사용하려는 개별적인 기능을 선택할 수 있습니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](../../../core/servers/manage/install-in-console-updates.md#bkmk_options)을 참조하세요.  

콘솔 내 업데이트를 설치하면:  

-   필수 구성 요소 확인이 자동으로 실행됩니다. 설치를 시작하기 전에 이런 확인을 실행할 수도 있습니다.  

-   중앙 관리 사이트(가 있는 경우)와 기본 사이트에 자동으로 설치됩니다. [사이트 서버에 대한 서비스 기간](../../../core/servers/manage/service-windows.md)을 사용하여 각각의 기본 사이트 서버가 인프라를 업데이트하도록 허용할 시기를 제어할 수 있습니다.  

-   사이트 서버 업데이트 후에는, 영향을 받은 모든 사이트 시스템 역할(SMS 공급자 인스턴스 포함)이 자동으로 업데이트됩니다. 사이트에 업데이트가 설치된 후 Configuration Manager 콘솔에서 콘솔 사용자에게 콘솔을 업데이트하라는 메시지를 표시합니다.  

-   업데이트에 Configuration Manager 클라이언트가 포함되어 있으면 프로덕션에 앞서 업데이트를 테스트하거나 모든 클라이언트에 업데이트를 즉시 적용할 수 있는 옵션이 제공됩니다.  

-   기본 사이트가 업데이트된 후에 보조 사이트는 자동으로 업데이트되지 않습니다. 대신에, 사용자가 보조 사이트 업데이트를 시작해야 합니다.  

> [!NOTE]  
>  System Center Configuration Manager(현재 분기) 프로덕션 릴리스, Long-Term Servicing Branch 및 System Center Configuration Manager Technical Preview는 서로 다른 릴리스입니다. 따라서 한 분기에 적용되는 업데이트를 다른 분기에 대한 콘솔 내 업데이트로 사용할 수 없습니다. 사용 가능한 분기에 대한 자세한 내용은 [사용해야 하는 Configuration Manager 분기](/sccm/core/understand/which-branch-should-i-use)를 참조하세요.

##  <a name="bkmk_outofband"></a> 대역 외 핫픽스  
일부 핫픽스는 특정 문제를 처리할 가능성이 제한된 상태로 릴리스되거나, 모든 고객에게 적용할 수 있지만 콘솔 내 메서드를 사용하여 설치할 수 없습니다. 이러한 수정 프로그램은 대역 외로 제공되며 Microsoft 클라우드 서비스에서 찾을 수 없습니다.  

일반적으로, 대역 외 핫픽스는 Microsoft 고객 지원 서비스, 기술 자료 문서 또는 Configuration Manager 배포 문제를 해결하거나 처리하려는 경우 [System Center Configuration Manager 팀 블로그](https://blogs.technet.microsoft.com/configmgrteam)에서 자세히 알아볼 수 있습니다.  

이러한 수정 프로그램은 다음 두 가지 방법 중 한 가지를 사용하여 설치합니다.  

-   **업데이트 등록 도구:** 이 도구는 핫픽스를 Configuration Manager 콘솔로 수동으로 가져옵니다. 그 후에 자동으로 검색되는 콘솔 내 업데이트에서 하듯이 업데이트를 설치할 수 있습니다. 이 메서드는 다음과 같은 파일 이름 구조를 사용하는 업데이트에 사용됩니다. **.update.exe**.  이런 유형의 핫픽스에 대한 전체 파일 이름은 다음과 유사합니다. **&lt;제품\>-&lt;제품 버전\>-&lt;KB 문서 ID\>-ConfigMgr.Update.exe**.  

     자세한 내용은 [업데이트 등록 도구를 사용하여 System Center Configuration Manager에 핫픽스 가져오기](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)를 참조하세요.  

-   **핫픽스 설치 관리자:** 이 도구는 콘솔 내 메서드를 사용하여 설치할 수 없는 핫픽스를 수동으로 설치하는 데 사용됩니다. 이 메서드는 다음과 같은 파일 이름 구조를 사용하는 수정 프로그램에 사용됩니다. **&lt;제품\>-&lt;제품 버전\>-&lt;KB 문서 ID\>-&lt;플랫폼\>-&lt;언어\>.exe**.

     자세한 내용은 [핫픽스 설치 관리자를 사용하여 System Center Configuration Manager의 업데이트 설치](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)를 참조하세요.

