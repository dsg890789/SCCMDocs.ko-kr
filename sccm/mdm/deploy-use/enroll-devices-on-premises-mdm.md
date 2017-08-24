---
title: "장치 등록 | Microsoft Docs"
description: "System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위해 장치를 등록하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
caps.latest.revision: "6"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 4abaef35969ef1a5340ae8ca8aa5699cd3942642
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 온-프레미스 모바일 장치 관리를 사용하여 컴퓨터 및 장치를 관리하려면 Configuration Manager가 관리 작업을 위해 장치와 통신할 수 있도록 장치가 등록되어 있어야 합니다. Configuration Manager에서는 장치 등록을 위한 두 가지 방법을 제공합니다.  

-   **사용자 등록** - 이 방법에서는 사용자가 장치에서 등록 프로세스를 시작합니다. 사용자 등록이 성공하려면 장치에 신뢰할 수 있는 루트 인증서가 설치되어 있어야 하고 등록을 위해 Configuration Manager에서 사용자가 프로비전되어야 합니다.  장치를 등록하기 위해 사용자는 회사 자격 증명만 제공하면 되며 관리된 장치가 등록됩니다.  

     자세한 내용은 [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 사용하여 장치를 등록하는 방법](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)을 참조하세요.  

-   **대량 등록** - 이 방법에서는 장치 사용자가 등록을 시작할 필요가 없습니다. 대신 Configuration Manager에서 대량 등록 패키지가 만들어진 다음 장치에서 켜지고 열립니다. 패키지를 열면 장치를 등록하는 데 필요한 정보가 제공됩니다.  

     자세한 내용은 [System Center Configuration Manager에서 온-프레미스 모바일 장치 관리를 사용하여 장치를 대량 등록하는 방법](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md)을 참조하세요.  

 > [!NOTE]  
>  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 장치에 대한 온-프레미스 모바일 장치 관리에서의 등록을 지원합니다.  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 팀 
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise   
