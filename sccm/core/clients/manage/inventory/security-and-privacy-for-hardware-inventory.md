---
title: "하드웨어 인벤토리 보안 및 개인 정보 | Microsoft 문서"
description: "System Center Configuration Manager에서 하드웨어 인벤토리에 대한 보안 및 개인 정보를 확인합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62e20d86-db6d-4a1f-b14a-905a9de31698
caps.latest.revision: 6
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: b12d4a1592ce4601fa1f0a6cd2a539a3664c0c37


---
# <a name="security-and-privacy-for-hardware-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 하드웨어 인벤토리에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager에서 하드웨어 인벤토리에 대한 보안 및 개인 정보가 포함되어 있습니다.  

##  <a name="a-namebkmksecurityhardwareinventorya-security-best-practices-for-hardware-inventory"></a><a name="BKMK_Security_HardwareInventory"></a> 하드웨어 인벤토리에 대한 보안 모범 사례  
 클라이언트에서 하드웨어 인벤토리 데이터를 수집하는 경우에 대해 다음 보안 모범 사례를 따르세요.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|인벤토리 데이터 서명 및 암호화|클라이언트가 HTTPS를 사용하여 관리 지점과 통신할 때 해당 클라이언트가 전송하는 모든 데이터는 SSL을 사용하여 암호화됩니다. 그러나 클라이언트 컴퓨터가 HTTP를 사용하여 인트라넷의 관리 지점과 통신하는 경우에는 클라이언트 인벤토리 데이터 및 수집된 파일이 서명되지 않고 암호화되지 않은 상태로 전송될 수 있습니다. 사이트가 서명을 요구하고 암호화를 사용하도록 구성되어 있는지 확인합니다. 또한 클라이언트에서 SHA-256 알고리즘을 지원할 수 있는 경우 SHA-256을 요구하는 옵션을 선택합니다.|  
|높은 수준의 보안 환경에서 IDMIF 및 NOIDMIF 파일을 수집하지 않음|IDMIF 및 NOIDMIF 파일 컬렉션을 사용하여 하드웨어 인벤토리 컬렉션을 확장할 수 있습니다. 필요한 경우 Configuration Manager에서는 Configuration Manager 데이터베이스에서 새 테이블을 만들거나 기존 테이블을 수정하여 해당 속성을 IDMIF 및 NOIDMIF 파일에 적용합니다. 그러나 Configuration Manager에서는 IDMIF 및 NOIDMIF 파일이 유효한지 확인하지 않으므로 이러한 파일을 사용하여 변경하지 않으려는 테이블을 변경할 수 있습니다. 잘못된 데이터가 유효한 데이터를 덮어쓸 수 있습니다. 또한 많은 양의 데이터를 추가할 수 있으며 이러한 데이터의 처리로 인해 모든 Configuration Manager 함수에서 지연이 발생할 수 있습니다. 이러한 위험을 완화하려면 하드웨어 인벤토리 클라이언트 설정 **MIF 파일 수집** 을 **없음**으로 구성합니다.|  

### <a name="security-issues-for-hardware-inventory"></a>하드웨어 인벤토리에 대한 보안 문제  
 인벤토리 수집은 잠재적인 취약성을 노출합니다. 공격자는 다음 작업을 수행할 수 있습니다.  

-   잘못된 데이터를 보내면, 소프트웨어 인벤토리 클라이언트 설정을 사용하지 않고 파일 컬렉션을 사용하지 않는 경우에도 관리 지점에서 이를 수락합니다.  

-   단일 파일과 많은 파일에서 너무 많은 양의 데이터를 보내면 서비스 거부를 발생시킬 수도 있습니다.  

-   Configuration Manager로 전송될 때 인벤토리 정보에 액세스합니다.  

 로컬 관리자 권한이 있는 사용자는 정보를 인벤토리 데이터로 보낼 수 있기 때문에 Configuration Manager에서 수집되는 인벤토리 데이터를 신뢰할 수 있는 것으로 간주하지 않는 것이 좋습니다.  

 하드웨어 인벤토리는 클라이언트 설정으로 기본적으로 사용하도록 설정되어 있습니다.  

##  <a name="a-namebkmkprivacyhardwareinventorya-privacy-information-for-hardware-inventory"></a><a name="BKMK_Privacy_HardwareInventory"></a> 하드웨어 인벤토리에 대한 개인 정보  
 하드웨어 인벤토리를 사용하면 Configuration Manager 클라이언트의 레지스트리 및 WMI에 저장된 정보를 검색할 수 있습니다. 소프트웨어 인벤토리를 사용하면 지정된 형식의 파일을 검색하거나 지정된 파일을 클라이언트에서 수집할 수 있습니다. Asset Intelligence는 하드웨어 및 소프트웨어 인벤토리를 확장하고 새 라이선스 관리 기능을 추가하여 인벤토리 기능을 향상시킵니다.  

 하드웨어 인벤토리는 기본적으로 클라이언트 설정으로 사용하도록 설정되어 있으며 선택하는 옵션에 따라 수집되는 WMI 정보가 결정됩니다. 소프트웨어 인벤토리는 기본적으로 사용하도록 설정되어 있지만 파일은 기본적으로 수집되지 않습니다. 사용하도록 설정할 하드웨어 인벤토리 보고 클래스를 선택할 수 있지만 Asset Intelligence 데이터 컬렉션은 자동으로 사용하도록 설정됩니다.  

 인벤토리 정보는 Microsoft로 전송되지 않습니다. 인벤토리 정보는 Configuration Manager 데이터베이스에 저장됩니다. 클라이언트가 HTTPS를 사용하여 관리 지점에 연결하는 경우 사이트에 보내는 인벤토리 데이터는 암호화되어 전송됩니다. 클라이언트가 HTTP를 사용하여 관리 지점에 연결되는 경우 인벤토리 암호화를 사용하도록 설정하는 옵션이 있습니다. 인벤토리 데이터는 데이터베이스에 암호화된 형식으로 저장되지 않습니다. 정보는 90일 간격으로 사이트 유지 관리 작업인 **오래된 인벤토리 기록 삭제** 또는 **오래된 수집 파일 삭제** 에서 삭제될 때까지 데이터베이스에 보존됩니다. 삭제 간격은 필요에 따라 구성할 수 있습니다.  

 하드웨어 인벤토리, 소프트웨어 인벤토리, 파일 컬렉션 또는 Asset Intelligence 데이터 컬렉션을 구성하기 전에 개인 정보 요구 사항을 고려해야 합니다.  



<!--HONumber=Dec16_HO3-->


