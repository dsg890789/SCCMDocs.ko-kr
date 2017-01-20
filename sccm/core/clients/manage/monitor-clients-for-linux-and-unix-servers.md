---
title: "클라이언트 모니터링 | System Center Configuration Manager | Linux UNIX "
description: "System Center Configuration Manager에서 Linux 및 UNIX 서버의 클라이언트 모니터링"
ms.custom: na
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: 6
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 620c1caf50b4859afc8f32490ab7945df810aefd
ms.openlocfilehash: b2b7c88784eed6fbee6ac1f6348d7d6991df1fbb


---
# <a name="how-to-monitor-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Windows 기반 클라이언트에서 정보를 볼 때와 동일한 방법을 사용하여 System Center Configuration Manager 콘솔에서 Linux 및 UNIX 서버의 정보를 볼 수 있습니다.  

 볼 수 있는 정보는 다음과 같습니다.  

-   Configuration Manager 콘솔 대시보드의 클라이언트 상태 세부 정보  

-   기본 Configuration Manager 보고서의 클라이언트 세부 정보  

-   리소스 탐색기에 인벤토리 세부 정보  

 다음 섹션에서는 리소스 탐색기 및 보고서에서 이러한 세부 정보를 가져오는 방법을 설명합니다.  

##  <a name="a-namebkmkuseresourceexpforlnua-use-resource-explorer-to-view-inventory-for-linux-and-unix-servers"></a><a name="BKMK_UseResourceExpforLnU"></a> 리소스 탐색기를 사용하여 Linux 및 UNIX 서버에 대한 인벤토리 보기  
 
 Configuration Manager 클라이언트에서 하드웨어 인벤토리를 Configuration Manager 사이트로 전송한 후 리소스 탐색기를 사용하여 이 정보를 볼 수 있습니다. Linux 및 UNIX용 Configuration Manager 클라이언트는 인벤토리에 대한 새 클래스나 뷰를 리소스 탐색기에 추가하지 않습니다. Linux 및 UNIX 인벤토리 데이터는 기존 WMI 클래스에 매핑됩니다. 리소스 탐색기를 사용하여 Windows 기반 분류에서 Linux 및 UNIX 서버에 대한 인벤토리 세부 정보를 볼 수 있습니다.  

 예를 들어 Linux 및 UNIX 서버에서 기본적으로 설치된 모든 프로그램 목록을 수집할 수 있습니다. 기본적으로 설치된 프로그램의 예로 Linux의 **.rpms** 또는 Solaris의 **.pkgs** 가 있습니다. Linux 또는 UNIX 클라이언트에서 인벤토리를 전송한 후 Configuration Manager 콘솔의 리소스 탐색기에서 기본적으로 설치된 모든 Linux 또는 UNIX 프로그램 목록을 볼 수 있습니다.  

 리소스 탐색기를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md)을 참조하세요.  

##  <a name="a-namebkmkusereportsforlnua-how-to-use-reports-to-view-information-for-linux-and-unix-servers"></a><a name="BKMK_UseReportsforLnU"></a> 보고서를 사용하여 Linux 및 UNIX 서버에 대한 정보를 보는 방법  
 Configuration Manager 보고서에는 Windows 기반 컴퓨터의 정보와 함께 Linux 및 UNIX 서버의 정보가 포함됩니다. 보고서에 Linux 및 UNIX 데이터를 통합하는 데 필요한 추가 구성은 없습니다.  

 예를 들어 운영 체제 버전 개수라는 보고서를 실행할 경우 다양한 운영 체제 목록과 각 운영 체제를 실행하는 클라이언트 수가 표시됩니다. 보고서는 여러 운영 체제에서 실행되는 다양한 Configuration Manager 클라이언트가 보낸 하드웨어 인벤토리 정보를 기반으로 합니다.  

 Linux 및 UNIX 서버 데이터와 관련된 사용자 지정 보고서를 만들 수도 있습니다. 하드웨어 인벤토리 클래스 **운영 체제** 의 **캡션** 속성은 보고서 쿼리에서 특정 운영 체제를 식별하는 데 사용할 수 있는 유용한 특성입니다.  

 Configuration Manager의 보고서에 대한 자세한 내용은 [System Center Configuration Manager에서 보고](../../../core/servers/manage/reporting.md)를 참조하세요.  



<!--HONumber=Dec16_HO3-->


