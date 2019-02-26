---
title: 하이브리드 MDM에서 마이그레이션
titleSuffix: Configuration Manager
description: 하이브리드 MDM은 사용 되지 않습니다., Intune 독립 실행형은 공동 관리를 위해 필요 합니다.
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
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755365"
---
# <a name="migrate-from-hybrid-mdm-for-co-management"></a>공동 관리를 위해 하이브리드 MDM에서 마이그레이션

하이브리드 모바일 장치 관리 (MDM)에 사용 되지 않는 기능입니다. 1 년 9 월 2019에 하이브리드 MDM 종료를 지원 합니다. 자세한 내용은 [Configuration Manager 및 Microsoft Intune을 사용 하 여 하이브리드 MDM](/sccm/mdm/understand/hybrid-mobile-device-management)합니다.

Intune 독립 실행형 권장된 배포 토폴로지 이며 공동 관리를 위해 필요 합니다. 공동 관리를 사용 하도록 설정 하려는 경우 Intune 독립 실행형 Intune 하이브리드 구성에서 마이그레이션하십시오. 

다음 비디오에서는 Andrew McMurray의 주요 프로그램 관리자 및 선임 제품 마케팅 관리자 Mayunk Jain 설명 및 하이브리드 MDM에서에서 마이그레이션 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Moving-From-Hybrid-MDM-To-Microsoft-Intune/player]



## <a name="how-to-do-it"></a>작업을 수행 하는 방법

Intune 독립 실행형으로 마이그레이션 가장 성공적인 경우 단계적된 접근 방식을 사용 됩니다. 단계별된 마이그레이션을 사용 하 여 이동 하면 사용자 및 장치의 작은 하위 집합 대부분의 사용자 및 장치는 여전히 하이브리드 MDM 사용 하 여 관리 하는 동안 마이그레이션이 성공를 확인 한 후 Intune로 더 많은 리소스를 마이그레이션하기 시작할 수 있습니다.

마이그레이션을 시작 하려면 사용 합니다 [Microsoft Intune 데이터 가져오기 도구](/sccm/mdm/deploy-use/migrate-import-data) 수집 하 고 Configuration Manager에서 Intune 독립 실행형 테 넌 트에서 개체를 다시 만드는 프로세스를 자동화 합니다. 다음으로 사용자의 특정 집합에 대 한 MDM 기관을 변경 하 고 Intune 독립 실행형에서 기능 테스트. 이 확인이 완료 되 면 모든 사용자에 대 한 Intune 독립 실행형으로 MDM 기관을 변경 합니다.

> [!Important]  
> Configuration Manager에서 온-프레미스 조건부 액세스에 사용 하는, 하는 경우이 기능은 현재 Intune 하이브리드가 필요 합니다.  

이 마이그레이션 프로세스에 대 한 자세한 내용은 참조 하세요. [하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형 마이그레이션](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)합니다.



## <a name="case-studies"></a>사례 연구

Microsoft IT 최근에 이동할 130,000 사용자가 Intune 하이브리드에서 Intune 독립 실행형 3 달 동안. 자세한 내용은 [Microsoft 방법을 사용 하 여 조건부 액세스-끝점 영역 1812](https://youtu.be/offk-KH7eIA?t=651)합니다. 이 비디오는 Microsoft 회사 부사장 인 Brad Anderson 및 Microsoft의 최고 정보 보안 책임자는 개인적으로 마이그레이션을 oversaw Bret Arsenault 간의 대화입니다. 

제약 대기업 10,000 명의 사용자가 Intune 하이브리드에서 Intune 독립 실행형 몇 주 내 이동 합니다.

큰 IT 컨설팅 회사 인도에 40,000 사용자를 Intune 하이브리드에서 Intune 독립 실행형 보다 작은 한 달에 마이그레이션됩니다.



## <a name="contact-fasttrack"></a>FastTrack에 문의 하세요

마이그레이션 프로세스에 든 하이브리드 MDM에서에서 도움이 필요한 경우 이동할 [Microsoft FastTrack](https://Microsoft.com/FastTrack/), 로그인 및 지원을 요청 합니다. 

자세한 내용은 [FastTrack에서 도움말을 얻고](/sccm/comanage/quickstart-fasttrack)합니다. 

