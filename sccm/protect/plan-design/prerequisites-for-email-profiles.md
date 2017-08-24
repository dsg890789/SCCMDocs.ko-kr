---
title: "메일 프로필에 대한 필수 조건 | Microsoft 문서"
description: "System Center Configuration Manager의 메일 프로필과 해당 외부 종속성 및 제품 내 종속성에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dccf0b73-43bd-4545-8914-114168ebad36
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 451317db1d7aab888c03d1a099b9ce25311e06d0
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="email-profile-prerequisites"></a>메일 프로필 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 메일 프로필에는 외부 및 제품 내 종속성이 모두 있습니다.  

## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|전자 메일 프로필을 관리하려면 특정 보안 권한이 부여되어야 합니다.|전자 메일 프로필과 같은 회사 리소스 액세스 설정을 관리하려면 다음 보안 권한이 있어야 합니다.<br /><br /> - 메일 프로필에 대한 경고 및 보고서를 보고 관리하려면: **경고** 개체에 대한 **만들기**, **삭제**, **수정**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> - 인증서 프로필을 만들고 관리하려면: **인증서 프로필** 개체에 대한 **작성자 정책**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> - 메일 프로필 배포를 관리하려면: **컬렉션** 개체에 대한 **구성 정책 배포**, **클라이언트 상태 알림 수정**, **읽기** 및 **리소스 읽기** 권한이 필요합니다.<br /><br /> - 모든 구성 정책을 관리하려면: **구성 정책** 개체에 대한 **만들기**, **삭제**, **수정**, **읽기** 및 **보안 범위 설정** 권한이 필요합니다.<br /><br /> - 메일 프로필과 관련된 쿼리를 실행하려면: **쿼리** 개체에 대한 **읽기** 권한이 필요합니다.<br /><br /> - System Center Configuration Manager 콘솔에서 메일 프로필 정보를 보려면: **사이트** 개체에 대한 **읽기** 권한이 필요합니다.<br /><br /> - 메일 프로필에 대한 상태 메시지를 보려면: **상태 메시지** 개체에 대한 **읽기** 권한이 필요합니다.<br /><br /> - 메일 프로필을 만들고 관리하려면: **통신 프로비전 프로필** 개체에 대한 **작성자 정책**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> **회사 리소스 액세스 관리자** 보안 역할에는 System Center Configuration Manager에서 메일 프로필을 관리하는 데 필요한 이와 같은 권한이 포함됩니다. 자세한 내용은 [Configure security in System Center Configuration Manager](../../core/plan-design/security/configure-security.md)항목을 참조하세요.|  
|Active Directory의 메일 특성|사용자의 기본 SMTP 주소를 사용하여 메일 프로필에서 사용자 메일 주소를 생성하려면 Active Directory에서 **메일** 특성을 검색하도록 System Center Configuration Manager 사용자 검색을 구성해야 합니다(기본적으로 구성됨).|  

## <a name="external-dependencies"></a>외부 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|Active Directory의 메일 특성|사용자의 기본 SMTP 주소를 사용하여 메일 프로필에서 사용자 메일 주소를 생성하려면 이 주소가 Active Directory의 **메일** 특성에 있어야 합니다.<br /><br /> 자세한 내용은 Windows Server 설명서를 참조하세요.|
