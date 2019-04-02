---
title: 하이브리드 MDM에서 마이그레이션
titleSuffix: Configuration Manager
description: 하이브리드 MDM은 사용되지 않으며, 공동 관리를 위해서는 Intune 독립 실행형이 필요합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 456f32d5-8590-499f-a54d-d00618bc61f0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 84625c12c9cac643fe5a895c066632f44ffeacdc
ms.sourcegitcommit: 9aebc20b25cdef0af908918ccfd791f3264a5d94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "56755365"
---
# <a name="migrate-from-hybrid-mdm-for-co-management"></a>공동 관리를 위해 하이브리드 MDM에서 마이그레이션

하이브리드 MDM(모바일 디바이스 관리)은 사용되지 않는 기능입니다. 하이브리드 MDM에 대한 지원은 2019년 9월 1일에 종료됩니다. 자세한 내용은 [Hybrid MDM with Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management)(Configuration Manager 및 Microsoft Intune에서 하이브리드 MDM)을 참조하세요.

Intune 독립 실행형이 권장되는 배포 토폴로지이며 공동 관리를 위해 필요합니다. 공동 관리를 사용하도록 설정하려는 경우 Intune 하이브리드 구성에서 Intune 독립 실행형으로 마이그레이션하세요. 

다음 비디오에서는 수석 프로그램 관리자 Andrew McMurray와 선임 제품 마케팅 관리자 Mayunk Jain이 하이브리드 MDM에서 마이그레이션하는 방법을 설명하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Moving-From-Hybrid-MDM-To-Microsoft-Intune/player]



## <a name="how-to-do-it"></a>방법

단계적 접근 방식을 사용할 경우 Intune 독립 실행형으로 효율적으로 마이그레이션할 수 있습니다. 단계적 마이그레이션에서는 사용자와 디바이스를 대부분 하이브리드 MDM을 통해 계속 관리하면서 작은 하위 집합의 사용자 및 디바이스만 이동합니다. 이 마이그레이션에 성공하면 더 많은 리소스를 Intune으로 마이그레이션하기 시작할 수 있습니다.

마이그레이션을 시작하려면 [Microsoft Intune Data Importer 도구](/sccm/mdm/deploy-use/migrate-import-data)를 사용하여 Intune 독립 실행형 테넌트의 Configuration Manager에서 개체를 다시 만드는 프로세스를 수집하고 자동화합니다. 그런 다음 특정 사용자 집합의 MDM 기관을 변경하고 Intune 독립 실행형에서 기능을 테스트합니다. 이 확인이 완료되면 모든 사용자의 MDM 기관을 Intune 독립 실행형으로 변경합니다.

> [!Important]  
> Configuration Manager에서 온-프레미스 조건부 액세스를 사용하는 경우 현재 이 기능을 사용하려면 Intune 하이브리드가 필요합니다.  

이 마이그레이션 프로세스에 대한 자세한 내용은 [Migrate hybrid MDM users and devices to Intune standalone](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)(하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션)을 참조하세요.



## <a name="case-studies"></a>사례 연구

Microsoft IT가 최근 130,000명 사용자를 Intune 하이브리드에서 Intune 독립 실행형으로 3개월 안에 이동했습니다. 자세한 내용은 [How Microsoft uses Conditional Access - Endpoint Zone 1812](https://youtu.be/offk-KH7eIA?t=651)(Microsoft에서 조건부 액세스를 사용하는 방법 - 엔드포인트 영역 1812)를 참조하세요. 이 비디오에서는 Microsoft 부사장인 Brad Anderson과 Microsoft의 최고 정보 보안 책임자이자 마이그레이션을 직접 감독한 Bret Arsenault가 대화합니다. 

대형 제약회사가 몇 주 내에 10,000명의 사용자를 Intune 하이브리드에서 Intune 독립 실행형으로 이동했습니다.

인도의 대형 IT 컨설팅 회사가 한 달 이내에 40,000명 사용자를 Intune 하이브리드에서 Intune 독립 실행형으로 마이그레이션했습니다.



## <a name="contact-fasttrack"></a>FastTrack에 문의

진행 도중 언제든 하이브리드 MDM에서 마이그레이션 관련 지원이 필요하면 [Microsoft FastTrack](https://Microsoft.com/FastTrack/)으로 이동하여 로그인하고 지원을 요청하세요. 

자세한 내용은 [Get help from FastTrack](/sccm/comanage/quickstart-fasttrack)(FastTrack에서 도움받기)을 참조하세요. 

