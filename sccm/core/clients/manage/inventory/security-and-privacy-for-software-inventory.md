---
title: 소프트웨어 인벤토리 보안 및 개인 정보
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 소프트웨어 인벤토리에 대한 보안 및 개인 정보를 확인합니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 8e68e1fb-a8ec-4543-bb8a-cbbaf184a418
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5fef3c1892c015fcec42197c9af373506d8e426a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32333113"
---
# <a name="security-and-privacy-for-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 인벤토리에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager에서 소프트웨어 인벤토리에 대한 보안 및 개인 정보가 포함되어 있습니다.  

##  <a name="BKMK_Security_HardwareInventory"></a> 소프트웨어 인벤토리에 대한 보안 모범 사례  
 클라이언트에서 소프트웨어 인벤토리 데이터를 수집하는 경우에 대해 다음 보안 모범 사례를 따르세요.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|인벤토리 데이터 서명 및 암호화|클라이언트가 HTTPS를 사용하여 관리 지점과 통신할 때 해당 클라이언트가 전송하는 모든 데이터는 SSL을 사용하여 암호화됩니다. 그러나 클라이언트 컴퓨터가 HTTP를 사용하여 인트라넷의 관리 지점과 통신하는 경우에는 클라이언트 인벤토리 데이터 및 수집된 파일이 서명되지 않고 암호화되지 않은 상태로 전송될 수 있습니다. 사이트가 서명을 요구하고 암호화를 사용하도록 구성되어 있는지 확인합니다. 또한 클라이언트에서 SHA-256 알고리즘을 지원할 수 있는 경우 SHA-256을 요구하는 옵션을 선택합니다.|  
|중요한 파일 또는 중요한 정보를 수집할 때는 파일 컬렉션을 사용하지 마세요.|Configuration Manager 소프트웨어 인벤토리는 레지스트리 또는 보안 계정 데이터베이스와 같은 중요한 시스템 파일의 복사본을 수집하는 기능이 있는 LocalSystem 계정의 모든 권한을 사용합니다. 이러한 파일을 사이트 서버에서 사용할 수 있는 경우 저장된 파일 위치에 대한 리소스 읽기 권한 또는 NTFS 권한을 가진 사람이 콘텐츠를 분석하고 클라이언트에 대한 중요한 세부 정보를 구별하여 보안을 손상시킬 수 있습니다.|  
|클라이언트 컴퓨터에 대한 로컬 관리자 권한 제한|로컬 관리자 권한이 있는 사용자는 잘못된 데이터를 인벤토리 정보로 보낼 수 있습니다.|  

### <a name="security-issues-for-software-inventory"></a>소프트웨어 인벤토리에 대한 보안 문제  
 인벤토리 수집은 잠재적인 취약성을 노출합니다. 공격자는 다음 작업을 수행할 수 있습니다.  

-   잘못된 데이터를 보내면, 소프트웨어 인벤토리 클라이언트 설정을 사용하지 않고 파일 컬렉션을 사용하지 않는 경우에도 관리 지점에서 이를 수락합니다.  

-   단일 파일과 많은 파일에서 너무 많은 양의 데이터를 보내면 서비스 거부를 발생시킬 수도 있습니다.  

-   Configuration Manager로 전송될 때 인벤토리 정보에 액세스합니다.  

 사용자가 이름이 **Skpswi.dat** 인 숨겨진 파일을 만들고 소프트웨어 인벤토리에서 제외하기 위해 클라이언트 하드 드라이브의 루트에 이 파일을 배치할 수 있다는 것을 알고 있다면 해당 컴퓨터에서 소프트웨어 인벤토리 데이터를 수집할 수 없습니다.  

 로컬 관리자 권한이 있는 사용자는 정보를 인벤토리 데이터로 보낼 수 있기 때문에 Configuration Manager에서 수집되는 인벤토리 데이터를 신뢰할 수 있는 것으로 간주하지 않는 것이 좋습니다.  

 소프트웨어 인벤토리는 클라이언트 설정으로 기본적으로 사용하도록 설정되어 있습니다.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> 소프트웨어 인벤토리에 대한 개인 정보  
 하드웨어 인벤토리를 사용하면 Configuration Manager 클라이언트의 레지스트리 및 WMI에 저장된 정보를 검색할 수 있습니다. 소프트웨어 인벤토리를 사용하면 지정된 형식의 파일을 검색하거나 지정된 파일을 클라이언트에서 수집할 수 있습니다. Asset Intelligence는 하드웨어 및 소프트웨어 인벤토리를 확장하고 새 라이선스 관리 기능을 추가하여 인벤토리 기능을 향상시킵니다.  

 하드웨어 인벤토리는 기본적으로 클라이언트 설정으로 사용하도록 설정되어 있으며 선택하는 옵션에 따라 수집되는 WMI 정보가 결정됩니다. 소프트웨어 인벤토리는 기본적으로 사용하도록 설정되어 있지만 파일은 기본적으로 수집되지 않습니다. 사용하도록 설정할 하드웨어 인벤토리 보고 클래스를 선택할 수 있지만 Asset Intelligence 데이터 컬렉션은 자동으로 사용하도록 설정됩니다.  

 인벤토리 정보는 Microsoft로 전송되지 않습니다. 인벤토리 정보는 Configuration Manager 데이터베이스에 저장됩니다. 클라이언트가 HTTPS를 사용하여 관리 지점에 연결하는 경우 사이트에 보내는 인벤토리 데이터는 암호화되어 전송됩니다. 클라이언트가 HTTP를 사용하여 관리 지점에 연결되는 경우 인벤토리 암호화를 사용하도록 설정하는 옵션이 있습니다. 인벤토리 데이터는 데이터베이스에 암호화된 형식으로 저장되지 않습니다. 정보는 90일 간격으로 사이트 유지 관리 작업인 **오래된 인벤토리 기록 삭제** 또는 **오래된 수집 파일 삭제** 에서 삭제될 때까지 데이터베이스에 보존됩니다. 삭제 간격은 필요에 따라 구성할 수 있습니다.  

 하드웨어 인벤토리, 소프트웨어 인벤토리, 파일 컬렉션 또는 Asset Intelligence 데이터 컬렉션을 구성하기 전에 개인 정보 요구 사항을 고려해야 합니다.  
