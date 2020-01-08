---
title: '디바이스 등록 '
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 모바일 장치 관리를 위해 장치를 등록 하는 방법에 대해 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33574ae84920b8a9abb10a5b82f822d15acddc58
ms.sourcegitcommit: 7f64c5fb3e9fa3dba006af618b1f1ceaf61a99f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75520884"
---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 모바일 장치 관리를 위한 장치 등록

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 모바일 장치 관리를 사용 하 여 컴퓨터 및 장치를 관리 하려면 Configuration Manager에서 관리 작업을 위해 장치와 통신할 수 있도록 장치를 등록 해야 합니다. Configuration Manager에서는 디바이스 등록을 위한 두 가지 방법을 제공합니다.  

- **사용자 등록** - 이 방법에서는 사용자가 디바이스에서 등록 프로세스를 시작합니다. 사용자 등록이 성공하려면 디바이스에 신뢰할 수 있는 루트 인증서가 설치되어 있어야 하고 등록을 위해 Configuration Manager에서 사용자가 프로비전되어야 합니다.  디바이스를 등록하기 위해 사용자는 회사 자격 증명만 제공하면 되며 관리된 디바이스가 등록됩니다.  

   자세한 내용은 [사용자가 온-프레미스 모바일 장치 관리를 사용 하 여 장치를 등록 하는 방법](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md) 을 참조 하세요.  

- **대량 등록** - 이 방법에서는 디바이스 사용자가 등록을 시작할 필요가 없습니다. 대신 Configuration Manager에서 대량 등록 패키지가 만들어진 다음 디바이스에서 켜지고 열립니다. 패키지를 열면 디바이스를 등록하는 데 필요한 정보가 제공됩니다.  

   자세한 내용은 [온-프레미스 모바일 장치 관리를 사용 하 여 장치를 대량 등록 하는 방법](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md) 을 참조 하세요.  

  > [!NOTE]
  >  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 디바이스에 대한 온-프레미스 모바일 디바이스 관리에서의 등록을 지원합니다.  
  > 
  > - Windows 10 Enterprise  
  >   -   Windows 10 Pro  
  >   -   Windows 10 팀 
  >   -   Windows 10 Mobile  
  >   -   Windows 10 Mobile Enterprise   
