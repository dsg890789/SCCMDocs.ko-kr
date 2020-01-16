---
title: 온-프레미스 MDM을 사용할 수 없음
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)에 대해 알아보기
ms.date: 01/09/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 644b55041ca89a7fefa6d0e316529bdc27197df7
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76032568"
---
# <a name="on-premises-mdm-in-configuration-manager"></a>Configuration Manager의 온-프레미스 MDM

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)은 Windows의 기본 제공 관리 기능을 사용 하는 장치 관리 솔루션입니다. 이 기능은 OMA (Open Mobile 동맹) DM (장치 관리) 표준을 기반으로 합니다. 조직의 Configuration Manager 인프라를 사용 하 여 장치를 관리 하 고 유지 관리 합니다. 조직에서이 기능을 사용 하려면 Microsoft Intune 라이선스를 요구 하지만 클라우드 연결이 필요 하지 않습니다. Configuration Manager은 온-프레미스 사이트 데이터베이스에서 장치에 대 한 모든 데이터를 저장 합니다.

온-프레미스 MDM은 기본 제공 OMA DM 기능을 사용 하는 Microsoft Intune와 다릅니다. Intune의 모든 관리 기능은 클라우드 서비스를 통해 제공 됩니다. 온-프레미스 MDM은 일반적으로 Configuration Manager에서 제공 하는 클라이언트 기반 관리 솔루션과도 다릅니다. 비슷한 인프라를 사용 하지만 관리 하는 장치에 별도로 설치 된 클라이언트 소프트웨어를 사용 하지 않습니다.  

## <a name="comparison"></a>비교

다음 섹션에서는 기존 클라이언트 기반 관리와 비교 했을 때 온-프레미스 MDM의 장단점을 나열 합니다.  

### <a name="advantages"></a>장점

- **간소화 된 인프라**: 더 낮은 사이트 시스템 역할이 필요 합니다.

- **유지 관리 용이**함: 관리 기능이 장치 OS에 기본 제공 되므로 새로운 관리 기능이 사이트에 도입 될 때 새 버전의 Configuration Manager 클라이언트가 필요 하지 않습니다.

- **온-프레미스**: 모든 관리 및 데이터가 온-프레미스로 유지 됩니다.

### <a name="disadvantages"></a>단점

**낮은 클라이언트 관리 기능**: 오케스트레이션, 소프트웨어 계량, 타사 통합, 작업 순서 또는 소프트웨어 센터 지원이 없습니다.

- **제한 된 장치 지원**: 온-프레미스 MDM은 Configuration Manager 클라이언트 만큼의 OS 버전을 지원 하지 않습니다. 자세한 내용은 [클라이언트 및 디바이스에 대해 지원되는 OS 버전](/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS)을 참조하세요.

## <a name="next-step"></a>다음 단계

Configuration Manager 인프라를 설정 하 고 온-프레미스 MDM에서 장치 등록을 계획할 때 고려해 야 할 사항에 대해 알아봅니다.

> [!div class="nextstepaction"]
> [온-프레미스 MDM 계획](/configmgr/mdm/plan-design/plan-on-premises-mdm)  
