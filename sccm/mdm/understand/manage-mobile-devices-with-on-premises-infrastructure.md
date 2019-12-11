---
title: 온-프레미스 MDM을 사용할 수 없음
titleSuffix: Configuration Manager
description: Configuration Manager의 장치 관리 솔루션인 온-프레미스 모바일 장치 관리에 대해 알아봅니다.
ms.date: 03/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49e07a7ebe6ec53d61ea9e2ee3bc941dd8561094
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62286984"
---
# <a name="on-premises-mdm-in-configuration-manager"></a>Configuration Manager의 온-프레미스 MDM

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)은 장치 OS의 기본 제공 관리 기능을 사용 하는 장치 관리 솔루션입니다. 이 기능은 OMA (Open Mobile 동맹) DM (장치 관리) 표준을 기반으로 합니다. 조직의 Configuration Manager 인프라를 사용 하 여 장치를 관리 하 고 유지 관리 합니다. 온-프레미스 MDM은 관리 기능을 설정 하는 Microsoft Intune 필요 하지만 구독에만 필요 합니다. Intune은 장치에서 정책 변경 내용을 체크 인하는 데 도움을 주기 위해 때때로 사용 되지만 장치를 관리 하거나 데이터를 저장 하는 데 사용 되지 않습니다.  

![온\-프레미스 개념](media/On-premises-conceptual.png)  

온-프레미스 MDM은 기본 제공 OMA DM 기능을 사용 하는 Microsoft Intune와 다릅니다. Intune의 모든 관리 기능은 클라우드 서비스를 통해 제공 됩니다. 온-프레미스 MDM은 일반적으로 Configuration Manager에서 제공 하는 클라이언트 기반 관리 솔루션과도 다릅니다. 비슷한 인프라를 사용 하지만 관리 하는 장치에 별도로 설치 된 클라이언트 소프트웨어를 사용 하지 않습니다.  

> [!Note]  
> 버전 1810부터는 Intune 연결이 새로운 온-프레미스 MDM 배포에 더 이상 필요하지 않습니다.<!--3607730, fka 1359124--> 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 현재 기존 온-프레미스 MDM 배포에서 Intune 연결을 제거할 수 없습니다. 자세한 내용은 [Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)을 참조하세요.  

다음 표에서는 기존 클라이언트 기반 관리와 비교 했을 때 온-프레미스 MDM의 장점과 단점을 보여 줍니다.  

|장점|단점|  
|----------------|-------------------|  
|**간소화된 인프라** - 적은 수의 사이트 시스템 역할이 필요합니다.<br /><br /> **더 쉬워진 유지** 관리-관리 기능이 장치 운영 체제에 기본 제공 되므로 새로운 관리 기능이 Configuration Manager 시스템에 도입 되 면 새 버전의 클라이언트 소프트웨어가 필요 하지 않습니다.<br /><br /> **온-프레미스** - 모든 관리 및 데이터가 온-프레미스로 유지됩니다.|**줄어든 클라이언트 관리 기능** - 오케스트레이션, 소프트웨어 계량, 타사 통합, 작업 순서 또는 소프트웨어 센터 지원이 없습니다.<br /><br /> **제한 된 장치 지원** -현재 온-프레미스 MDM은 windows 10 및 Windows 10 Mobile을 실행 하는 장치만 지원 합니다.|  

다음 문서에서는 온-프레미스 MDM에 대 한 장치를 계획, 준비 및 등록 하는 데 사용할 수 있는 정보를 제공 합니다.  

- [온-프레미스 MDM 계획](/sccm/mdm/plan-design/plan-on-premises-mdm)  

    Configuration Manager 인프라를 설정 하 고 온-프레미스 MDM에서 장치 등록을 계획할 때 고려해 야 할 사항에 대해 알아봅니다.  

- [온-프레미스 MDM에 대 한 준비 단계](/sccm/mdm/get-started/preparation-steps-for-on-premises-mdm)  

    온-프레미스 MDM에 대 한 Configuration Manager 준비 합니다. Microsoft Intune 구독을 설정 하 고, 인증서를 설정 하 고, 사이트 시스템 역할을 설치 하 고, 장치 등록을 설정 합니다.  

- [온-프레미스 MDM에 대한 디바이스 등록](/sccm/mdm/deploy-use/enroll-devices-on-premises-mdm)  

    등록을 수행하는 방법, 사용자가 자신의 디바이스를 등록하는 방법 그리고 등록 패키지로 디바이스를 대량으로 등록하는 방법에 대해 알아봅니다.  

