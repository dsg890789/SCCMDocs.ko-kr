---
title: "Asset Intelligence 보안 및 개인 정보 | Microsoft 문서"
description: "System Center Configuration Manager에서 Asset Intelligence 대한 보안 및 개인 정보를 확인합니다."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0c6f7a0-dcae-4e6d-aa28-35d464d97ff7
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b12054cce52e2b83715a083d78a62e06b5127a2f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Asset Intelligence 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager의 Asset Intelligence에 대한 보안 및 개인 정보가 포함되어 있습니다.  

##  <a name="BKMK_Security_AI"></a> Asset Intelligence에 대한 보안 모범 사례  
 Asset Intelligence를 사용하는 경우 다음 보안 모범 사례를 따르세요.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|라이선스 파일(Microsoft Volume Licensing 파일 또는 일반 라이선스 계정 파일)을 가져올 때 파일 및 통신 채널을 보호합니다.|NTFS 파일 시스템 권한을 사용하여 인증된 사용자만 라이선스 파일에 액세스할 수 있는지 확인하고 SMB(서버 메시지 블록) 서명을 사용하여 가져오기 프로세스 중 데이터가 사이트 서버에 전송될 때 데이터의 무결성을 보장합니다.|  
|최소 권한 원칙을 사용하여 라이선스 파일을 가져올 수 있습니다.|역할 기반 관리를 사용하여 라이선스 파일을 가져오는 관리자에게 Asset Intelligence 관리 권한을 부여합니다. 자산 관리자의 기본 제공 역할에는 이 권한이 포함되어 있습니다.|  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Asset Intelligence에 대한 개인 정보 보호  
 Asset Intelligence는 Configuration Manager의 인벤토리 기능을 확장하여 엔터프라이즈에서 더 높은 수준의 자산 가시성을 제공합니다. Asset Intelligence 정보 수집은 사용하도록 자동 설정되지 않습니다. 하드웨어 인벤토리 보고 클래스를 사용하도록 설정하여 수집된 정보 유형을 수정할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

 Asset Intelligence 정보가 인벤토리 정보와 동일한 방식으로 Configuration Manager 데이터베이스에 저장됩니다. 클라이언트가 HTTPS를 사용하여 관리 지점에 연결하는 경우 데이터가 관리 지점으로 전송되는 동안 상시 암호화됩니다. 클라이언트가 HTTP를 사용하여 연결하는 경우 인벤토리 데이터 전송이 서명되고 암호화되도록 구성할 수 있습니다. 인벤토리 데이터는 데이터베이스에서 암호화된 형식으로 저장되지 않습니다. 사이트 유지 관리 작업 **오래된 인벤토리 기록 삭제** 가 90일 간격으로 해당 정보를 삭제할 때까지 정보가 데이터베이스에서 유지됩니다. 삭제 간격은 필요에 따라 구성할 수 있습니다.  

 Asset Intelligence는 사용자 또는 컴퓨터에 대한 정보나 라이선스 사용량을 Microsoft에 전송하지 않습니다. 분류하기 위해 시스템 센터 온라인 요청을 보내기로 선택할 수 있습니다. 이는 범주화되지 않은 하나 이상의 소프트웨어 타이틀에 태그를 지정하고 이들을 연구 및 분류를 위해 시스템 센터 온라인에 보낸다는 의미입니다. 소프트웨어 타이틀이 업로드되면 Microsoft 연구원은 해당 정보를 파악하고 분류한 후 온라인 서비스를 사용하는 모든 고객이 사용할 수 있도록 만듭니다. System Center Online에 정보를 제출하는 다음 개인 정보 보호가 미치는 영향을 알고 있어야 합니다.  

-   업로드는 System Center Online에 보내기로 선택하는 일반 소프트웨어 타이틀 정보(이름, 게시자 등)에만 적용됩니다. 인벤토리 정보는 업로드로 전송되지 않습니다.  

-   업로드는 자동으로 발생하지 않으며 시스템에서 이 작업을 자동화하도록 설정할 수 없습니다. 각 소프트웨어 타이틀의 업로드는 수동으로 선택하고 승인해야 합니다.  

-   업로드 프로세스는 시작하기 전에 대화 상자에 업로드할 데이터를 정확히 표시합니다.  

-   라이선스 정보는 Microsoft로 전송되지 않습니다. 라이선스 정보는 Configuration Manager 데이터베이스의 별도 영역에 저장되고 Microsoft에 보낼 수 없습니다.  

-   업로드된 소프트웨어 타이틀이 공개된 후에는 지정된 응용 프로그램 및 분류에 대한 정보가 System Center Online Asset Intelligence 카탈로그의 일부가 되므로 다른 카탈로그 고객에게 다운로드됩니다.  

-   소프트웨어 타이틀 원본은 Asset Intelligence 카탈로그에 기록되지 않으므로 다른 고객이 사용할 수 없습니다. 그러나 개인 정보를 포함하는 응용 프로그램 타이틀을 로드하지 않는지 여전히 확인해야 합니다.  

-   업로드된 데이터는 취소할 수 없습니다.  

 Asset Intelligence 데이터 컬렉션을 구성하고 System Center Online에 정보를 제출할지 여부를 결정하려면 먼저 조직의 개인정보취급방침 요구 사항을 고려하세요.  
