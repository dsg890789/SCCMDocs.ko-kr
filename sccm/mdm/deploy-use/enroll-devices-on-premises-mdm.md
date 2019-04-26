---
title: '디바이스 등록 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위해 디바이스를 등록하는 방법을 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d27e81da4da7caa89988d78a705648c5709cc2c3
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226813"
---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위한 디바이스 등록

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 온-프레미스 모바일 디바이스 관리를 사용하여 컴퓨터 및 디바이스를 관리하려면 Configuration Manager가 관리 작업을 위해 디바이스와 통신할 수 있도록 디바이스가 등록되어 있어야 합니다. Configuration Manager에서는 디바이스 등록을 위한 두 가지 방법을 제공합니다.  

- **사용자 등록** - 이 방법에서는 사용자가 디바이스에서 등록 프로세스를 시작합니다. 사용자 등록이 성공하려면 디바이스에 신뢰할 수 있는 루트 인증서가 설치되어 있어야 하고 등록을 위해 Configuration Manager에서 사용자가 프로비전되어야 합니다.  디바이스를 등록하기 위해 사용자는 회사 자격 증명만 제공하면 되며 관리된 디바이스가 등록됩니다.  

   자세한 내용은 [System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 사용하여 디바이스를 등록하는 방법](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)섹션을 참조하세요.  

- **대량 등록** - 이 방법에서는 디바이스 사용자가 등록을 시작할 필요가 없습니다. 대신 Configuration Manager에서 대량 등록 패키지가 만들어진 다음 디바이스에서 켜지고 열립니다. 패키지를 열면 디바이스를 등록하는 데 필요한 정보가 제공됩니다.  

   자세한 내용은 [System Center Configuration Manager에서 온-프레미스 모바일 디바이스 관리를 사용하여 디바이스를 대량 등록하는 방법](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md)을 참조하세요.  

  > [!NOTE]
  >  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 디바이스에 대한 온-프레미스 모바일 디바이스 관리에서의 등록을 지원합니다.  
  > 
  > - Windows 10 Enterprise  
  >   -   Windows 10 Pro  
  >   -   Windows 10 팀 
  >   -   Windows 10 Mobile  
  >   -   Windows 10 Mobile Enterprise   
