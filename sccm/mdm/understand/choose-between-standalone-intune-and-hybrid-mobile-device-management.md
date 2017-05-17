---
title: "Intune 독립 실행형 또는 하이브리드 MDM 선택 | Microsoft 문서"
description: "Intune과 Configuration Manager를 사용하는 하이브리드 모바일 장치 관리 배포 또는 Intune 독립 실행형 실행 중에서 선택합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 84e3896dd05a8c157f4e94625b0eca60aacc11d3
ms.openlocfilehash: 8f2625aadfd0aed92d9922c7e3c0d3d166a78cdd
ms.contentlocale: ko-kr
ms.lasthandoff: 02/25/2017

---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Microsoft Intune 독립 실행형 및 System Center Configuration Manager에서 하이브리드 모바일 장치 관리 선택

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 및 MDM(모바일 장치 관리)과 관련하여 가장 자주 묻는 질문 중 하나는 "Intune 및 Configuration Manager를 통합할지(하이브리드 MDM), 아니면 클라우드 전용 구성으로 Intune 독립 실행형을 사용할지"입니다. 해당 질문에 대답하려면 두 옵션을 신중하게 비교하고 2017년 초에 제공될 Intune 독립 실행형 업데이트를 고려해야 합니다.

## <a name="what-is-intune-standalone"></a>Intune 독립 실행형이란?

Intune 독립 실행형은 온-프레미스 리소스를 포함하지 않고 전 세계 어디에서나 액세스할 수 있는 웹 콘솔을 사용하여 관리되는 클라우드 전용 MDM 솔루션입니다. Intune 데이터 센터는 북미, 유럽 및 아시아 지역에서 호스트됩니다. Intune은 클라우드 서비스이기 때문에 비교적 짧은 시간 내에 Intune 관리를 장치에 배포할 수 있습니다. 조직에서 클라우드로 이동하는 경우에도 Intune 독립 실행형을 선택할 수 있습니다.

## <a name="what-is-hybrid-mdm-with-configuration-manager"></a>Configuration Manager를 지원하는 하이브리드 MDM이란?

하이브리드 MDM은 정책, 프로필 및 응용 프로그램을 장치로 전달하는 채널로 Intune을 사용하지만 Configuration Manager 온-프레미스 인프라를 사용하여 콘텐츠를 저장 및 관리하고 장치를 관리하는 솔루션입니다. 이미 Configuration Manager에 상당한 투자를 했으며 모바일 장치 관리로 확장하려는 경우 하이브리드 MDM을 선택할 수 있습니다. 하이브리드 구현은 동일한 온-프레미스 인프라 및 관리 콘솔을 사용하여 Intune으로 모바일 장치를 관리하는 동시에 기존의 Configuration Manager 클라이언트로 PC와 서버를 관리할 수 있는 "단일 창" 제어를 제공합니다.

## <a name="whats-coming-to-intune-standalone-in-early-2017"></a>2017년 초에 Intune 독립 실행형에 제공되는 기능

독립 실행형과 하이브리드 중에서 선택하는 경우 2017년 초에 Intune 독립 실행형에 제공되는 기능을 고려해야 합니다. 현재 하이브리드 MDM에는 과거 일부 고객이 Intune 독립 실행형 대신 하이브리드 MDM으로 장치 관리를 선택한 이유였던 다음 몇 가지 고급 기능이 있습니다.

-   프로그래밍 방식 액세스(API) - SDK 및 PowerShell 관리 옵션입니다.

-   사용자 지정 보고 - 사용자 지정 보고서를 만듭니다.

-   역할 기반 액세스 제어 - 할당된 역할을 기반으로 하여 관리 기능에 대한 액세스를 제한합니다.

-   확장성 - 100,000대 이상의 모바일 장치에 배포하고 관리합니다.

-   단일 창 - 동일한 콘솔을 사용하여 기존 PC 클라이언트와 Intune에서 관리되는 장치를 둘 다 관리합니다.

현재 Intune 배포 계획을 시작 중이며 파일럿, 수용 테스트 및 배포를 실행할 몇 개월의 기간이 있는 경우 클라우드 서비스에 예정된 업데이트에 더 많은 기능이 포함될 계획이므로 지금 Intune 독립 실행형을 선택하는 것이 좋습니다. 2017년 상반기 동안 Intune 독립 실행형은 Configuration Manager와 하이브리드 배포의 고급 기능을 대부분 제공하는 업데이트를 받게 됩니다. Intune 독립 실행형은 곧 Microsoft Azure 클라우드 플랫폼으로 이동할 예정이며 향상된 확장성, Azure Portal을 통한 역할 기반 액세스, 사용자 지정 보고 및 Azure Graph API를 통한 프로그래밍 방식 액세스를 포함할 것입니다.

하이브리드에서 Intune 독립 실행형으로 전환하거나 독립 실행형에서 하이브리드로 전환할 수 있지만 Microsoft 기술 지원 및 운영 센터의 도움을 받아야 합니다. 또한 관리 기관이 변경된 후 모든 장치의 등록을 취소하고 다시 등록해야 합니다.  Microsoft는 향후 서비스 업데이트에서 구성 전환 경험을 향상시키기 위해 노력하고 있습니다.

