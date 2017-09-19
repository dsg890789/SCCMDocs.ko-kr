---
title: "Intune 독립 실행형 또는 하이브리드 MDM 선택 | Microsoft 문서"
description: "Intune과 Configuration Manager를 사용하는 하이브리드 모바일 장치 관리 배포 또는 Intune 독립 실행형 실행 중에서 선택합니다."
ms.custom: na
ms.date: 07/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: "10"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 5c9e80fc5bc3f0629e1c27a4928b8a51cfe1ee7e
ms.sourcegitcommit: 948644072bd158b156f782a4376bcd50fac7c73a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2017
---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Microsoft Intune 독립 실행형 및 System Center Configuration Manager에서 하이브리드 모바일 장치 관리 선택

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 및 MDM(모바일 장치 관리)과 관련하여 가장 자주 묻는 질문 중 하나는 "Intune 및 Configuration Manager를 통합할지(하이브리드 MDM), 아니면 클라우드 전용 구성으로 Intune 독립 실행형을 사용할지"입니다. 해당 질문에 답변하려면 두 가지 옵션을 신중하게 비교해야 합니다.
 
## <a name="intune-standalone"></a>Intune 독립 실행형
Intune 독립 실행형은 Microsoft의 권장되는 배포 토폴로지입니다. Intune 독립 실행형은 전 세계 어디에서나 액세스할 수 있는 웹 콘솔을 사용하여 관리되는 클라우드 전용 MDM 솔루션입니다. Intune 데이터 센터는 북미, 유럽 및 아시아 지역에서 호스트됩니다. Intune은 클라우드 서비스이기 때문에 비교적 짧은 시간 내에 Intune 관리를 장치에 배포할 수 있습니다.

온-프레미스 구성 요소에 대한 종속성이 없기 때문에 일반적으로 고객은 독립 실행형 토폴로지를 더 빠르고 쉽게 배포할 수 있습니다. Intune 독립 실행형은 현재 Microsoft Azure 클라우드 플랫폼에서 실행되며 다음과 같은 여러 고급 기능을 제공합니다.
- 통합 엔터프라이즈 이동성 관리 플랫폼 - Intune, Azure AD Premium 및 Azure Information Protection용으로 Azure Portal의 통합 클라우드 플랫폼 및 관리 환경
- 모바일 장치 관리 - 다양한 모바일 장치 관리 및 정보 보호 기능
- 확장 - 크기 조정을 걱정할 필요 없이 모바일 장치를 배포 및 관리합니다.
- 역할 기반 액세스 제어 - 할당된 역할 및 범위를 기반으로 하여 관리 기능에 대한 액세스를 제한합니다.
- 프로그래밍 방식 액세스(API) - Microsoft Graph API 지원, SDK 및 PowerShell 관리 옵션
- 웹 콘솔 - 최신 웹 브라우저에 대한 지원과 함께 웹 표준에 빌드된 HTML 5 기반 콘솔
- 고급 보고 - 사용자 지정 보고서를 만들 수 있는 기능
- 민첩성 - 간단한 설치 및 새로운 기능을 신속하게 제공


## <a name="hybrid-mdm-with-configuration-manager"></a>Configuration Manager를 지원하는 하이브리드 MDM
하이브리드 MDM은 Intune의 모바일 장치 관리 기능을 Configuration Manager에 통합하는 솔루션입니다. 하이브리드 MDM은 정책, 프로필 및 응용 프로그램을 장치로 전달하는 채널로 Intune을 사용하지만 Configuration Manager 온-프레미스 인프라를 사용하여 콘텐츠를 관리하고 장치를 관리합니다. 하이브리드 구현은 "단일 창" 제어를 제공합니다.  즉 동일한 온-프레미스 인프라 및 관리 콘솔을 사용하여 Intune으로 모바일 장치를 관리하는 동시에 기존의 Configuration Manager 클라이언트로 PC와 서버를 관리할 수 있습니다. 다음과 같은 이유로 하이브리드 MDM을 선택할 수 있습니다.  
- Intune에 등록된 모바일 장치와 동일한 관리 콘솔의 Configuration Manager 클라이언트로 관리되는 장치를 모두 관리하려는 경우
- 모바일 장치로 인증서 제공을 위해 여러 NDES 서버를 사용해야 하는 인프라인 경우
- 여러 Exchange 커넥터가 필요한 인프라인 경우
- S/MIME 암호화 지원이 필요한 경우


## <a name="changing-the-mdm-authority-setting"></a>MDM 기관 설정 변경
MDM 기관 설정을 변경해야 하는 경우 Microsoft 지원에 문의하지 않고 기존의 관리 장치를 등록 취소했다가 다시 등록하지 않고도 변경할 수 있습니다. 자세한 내용은 [MDM 기관 변경](../deploy-use/change-mdm-authority.md)을 참조하세요.

> [!NOTE]    
> MDM 기관을 Intune 독립 실행형으로 변경하려면 Configuration Manager 버전 1610 이상이 있어야 합니다. Configuration Manager의 이전 버전을 사용하는 경우 MDM 기관을 변경할 수는 있지만 Microsoft 기술 지원 및 운영 센터의 도움을 받아야 합니다. 또한 MDM 기관을 변경한 후 모든 장치를 등록 취소했다가 다시 등록해야 합니다.  
