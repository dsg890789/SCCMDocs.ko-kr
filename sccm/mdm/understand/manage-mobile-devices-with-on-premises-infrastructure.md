---
title: 온-프레미스 MDM을 사용할 수 없음
titleSuffix: Configuration Manager
description: Configuration Manager에서 장치 관리 솔루션을 온-프레미스 모바일 장치 관리에 대해 알아봅니다
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
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286984"
---
# <a name="on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 온-프레미스 모바일 장치 관리 (MDM)은 장치 운영 체제의 기본 제공 관리 기능에 의존 하는 장치 관리 솔루션입니다. 이 기능은 Open Mobile Alliance (OMA) 장치 관리 (DM) 표준을 기반으로 합니다. 조직의 Configuration Manager 인프라를 사용 하 여 관리 하 고 장치를 유지 합니다. 온-프레미스 MDM 관리 기능을 설정 하려면 Microsoft Intune을 필요 하지만 구독에만 필요 합니다. Intune 정책 변경을 확인 하는 장치에 알리기 위해 시간에 있지만 장치 관리에 대 한 데이터 저장에 사용 되지 않습니다.  

![온\-프레미스 개념](media/On-premises-conceptual.png)  

기본 제공 OMA DM 기능도 사용 하는 Microsoft Intune에서 온-프레미스 MDM 서로 다릅니다. Intune에서 관리 기능이 모든 클라우드 서비스를 통해 제공 됩니다. 온-프레미스 MDM에서 Configuration Manager에서 제공 하는 기존 클라이언트 기반 관리 솔루션과 다릅니다. 유사한 인프라를 기반으로 않지만 관리 하는 장치에서 별도로 설치 된 클라이언트 소프트웨어를 사용 하지 않습니다.  

> [!Note]  
> 1810 버전부터 Intune 연결을 새 온-프레미스 MDM 배포에 필요 하지 않습니다.<!--3607730, fka 1359124--> 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 현재 기존 온-프레미스 MDM 배포에서 Intune 연결을 제거할 수 없습니다. 자세한 내용은 [Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)을 참조하세요.  

다음 표에서 기존 클라이언트 기반 관리를 비교 하 여 온-프레미스 MDM의 장단점을 나열합니다.  

|장점|단점|  
|----------------|-------------------|  
|**간소화된 인프라** - 적은 수의 사이트 시스템 역할이 필요합니다.<br /><br /> **더 쉬워진 유지 관리** -관리 기능에 기본 제공 장치 운영 체제를 새 버전의 클라이언트 소프트웨어가 필요 없는 경우 Configuration Manager 시스템에 새로운 관리 기능을 소개 합니다.<br /><br /> **온-프레미스** - 모든 관리 및 데이터가 온-프레미스로 유지됩니다.|**줄어든 클라이언트 관리 기능** - 오케스트레이션, 소프트웨어 계량, 타사 통합, 작업 순서 또는 소프트웨어 센터 지원이 없습니다.<br /><br /> **장치 지원 제한** -현재 온-프레미스 MDM에서 지 원하는 장치 에서만 Windows 10 및 Windows 10 Mobile 실행 합니다.|  

다음 문서를 계획, 준비 및 온-프레미스 MDM에 대 한 장치를 등록 하 여 정보를 제공 합니다.  

- [온-프레미스 MDM 계획](/sccm/mdm/plan-design/plan-on-premises-mdm)  

    경우 Configuration Manager 인프라를 설정 하 고 계획에서 장치 등록에 대 한 온-프레미스 mdm. 고려해 야 할 사항 알아보기  

- [온-프레미스 MDM에 대 한 준비 단계](/sccm/mdm/get-started/preparation-steps-for-on-premises-mdm)  

    Configuration Manager 온-프레미스 MDM. 준비 Microsoft Intune 구독을 설정, 인증서를 설정, 사이트 시스템 역할 설치 및 장치 등록을 설정 합니다.  

- [온-프레미스 MDM에 대한 디바이스 등록](/sccm/mdm/deploy-use/enroll-devices-on-premises-mdm)  

    등록을 수행하는 방법, 사용자가 자신의 디바이스를 등록하는 방법 그리고 등록 패키지로 디바이스를 대량으로 등록하는 방법에 대해 알아봅니다.  

