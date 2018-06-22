---
title: 온-프레미스 MDM(모바일 장치 관리)
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 장치 관리 솔루션인 온-프레미스 모바일 장치 관리에 대해 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ac0e4426b2025a88f126f9cc0b2e57f5a5313740
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347402"
---
# <a name="on-premises-mobile-device-management-mdm-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 MDM(모바일 장치 관리)

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 온\-프레미스 모바일 장치 관리는 엔터프라이즈의 Configuration Manager 인프라를 사용하여 장치를 관리하고 유지 관리하는 동안 장치 운영 체제(Open Mobile Alliance Device Management 또는 OMA DM 표준을 기반으로 함)의 기본 제공 관리 기능을 사용하는 장치 관리 솔루션입니다. 온\-프레미스 모바일 장치 관리를 사용하려면 Microsoft Intune에서 관리 기능을 설정해야 하지만 구독에 대해서만(및 때때로 정책 변경 내용을 확인하도록 장치에 알리기 위해) 필요하고 장치를 관리하거나 장치에 대한 데이터를 저장하는 데 사용되지 않습니다.  

 ![온\-프레미스 개념](media/On-premises-conceptual.png)  

 온\-프레미스 모바일 장치 관리는 기본 제공 OMA DM 기능도 사용하지만 모든 관리 기능이 클라우드 서비스를 통해 제공되는 Microsoft Intune과 다릅니다.  또한 온\-프레미스 모바일 장치 관리는 유사한 엔터프라이즈 인프라를 사용하지만 관리 컴퓨터 및 관리되는 장치에 설치되어 있는 클라이언트 소프트웨어를 개별적으로 사용하지 않는다는 점에서 Configuration Manager에서 제공하는 기존 클라이언트 기반 관리 솔루션과도 다릅니다.  

 아래 표에는 기존 클라이언트 기반 관리와 비교했을 때 온\-프레미스 모바일 장치 관리의 장점 및 단점이 나와 있습니다.  

|장점|단점|  
|----------------|-------------------|  
|**간소화된 인프라** - 적은 수의 사이트 시스템 역할이 필요합니다.<br /><br /> **더 쉬워진 유지 관리** - 관리 기능이 장치 운영 체제에 기본 제공되므로 새로운 관리 기능이 Configuration Manager 시스템에 도입되면 새 버전의 클라이언트 소프트웨어가 필요하지 않습니다.<br /><br /> **온-프레미스** - 모든 관리 및 데이터가 온-프레미스로 유지됩니다.|**줄어든 클라이언트 관리 기능** - 오케스트레이션, 소프트웨어 계량, 타사 통합, 작업 순서 또는 소프트웨어 센터 지원이 없습니다.<br /><br /> **장치 지원 제한** - 현재 온\-프레미스 모바일 장치 관리에서는 Windows 10 및 Windows 10 Mobile을 실행하는 장치만 지원합니다.|  

 다음 항목에서는 온\-프레미스 모바일 장치 관리를 위해 장치를 계획, 준비 및 등록하는 데 사용할 수 있는 정보를 제공합니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 장치 관리에 대한 계획](../plan-design/plan-on-premises-mdm.md)  

     온\-프레미스 모바일 장치 관리에서 Configuration Manager 인프라를 설정하고 장치 등록을 계획할 때 고려해야 할 사항을 알아봅니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 준비 단계](../get-started/preparation-steps-for-on-premises-mdm.md)  

     Microsoft Intune 구독을 설정하고, 인증서를 설정하고, 사이트 시스템 역할을 설치하고, 장치 등록을 설정하여 온\-프레미스 모바일 장치 관리를 위해 Configuration Manager 시스템을 준비하는 방법을 알아봅니다.  

-   [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록](../deploy-use/enroll-devices-on-premises-mdm.md)  

     등록을 수행하는 방법, 사용자가 자신의 장치를 등록하는 방법 그리고 등록 패키지로 장치를 대량으로 등록하는 방법에 대해 알아봅니다.  
