---
title: "인증서 템플릿 권한 계획 | Microsoft 문서"
description: "System Center Configuration Manager에서 사용하는 인증서 템플릿을 구성해야 하는 권한에 대한 계획을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: eab0e09d-b09e-4c14-ab14-c5f87472522e
caps.latest.revision: 5
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 832be8c9fda727804f57e83768cd8799db722c67
ms.lasthandoff: 03/27/2017


---
# <a name="planning-for-certificate-template-permissions-for-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 인증서 프로필에 대한 인증서 템플릿 권한 계획

*적용 대상: System Center Configuration Manager(현재 분기)*


인증서 프로필을 배포할 때 System Center Configuration Manager에서 사용하는 인증서 템플릿의 권한을 구성하는 방법을 계획하는 데 다음 정보를 활용할 수 있습니다.  

## <a name="default-security-permissions-and-considerations"></a>기본 보안 권한 및 고려 사항  
 System Center Configuration Manager에서 사용자 및 장치에 대한 인증서를 요청하는 데 사용하는 인증서 템플릿에 필요한 기본 보안 권한은 다음과 같습니다.  

-   네트워크 장치 등록 서비스 응용 프로그램에서 사용하는 계정의 읽기 및 등록 권한  

-   System Center Configuration Manager 콘솔을 실행하는 계정의 읽기 권한  

 이러한 보안 권한에 대한 자세한 내용은 [인증서 인프라 구성](../deploy-use/certificate-infrastructure.md)을 참조하세요.  

 이 기본 구성을 사용하면 사용자 및 장치가 인증서 템플릿에서 직접 인증서를 요청할 수 없고 모든 요청을 네트워크 장치 등록 서비스에서 시작해야 합니다. 이러한 인증서 템플릿은 인증서 주체에 대해 **요청에서 제공** 으로 구성해야 하기 때문에 이 사항은 중요한 제한입니다. 즉, Rogue 사용자 또는 손상된 장치가 인증서를 요청할 경우 가장의 위험이 있습니다. 기본 구성에서 네트워크 장치 등록 서비스가 이러한 요청을 시작해야 합니다. 그러나 네트워크 장치 등록 서비스를 실행하는 서비스가 손상된 경우 가장의 위험이 남아 있습니다. 이러한 위험을 방지하려면 네트워크 장치 등록 서비스 및 이 역할 서비스를 실행하는 컴퓨터와 관련된 모든 보안 모범 사례를 따르십시오.  

 기본 보안 권한이 비즈니스 요구 사항을 충족하지 못하는 경우 인증서 템플릿에 대한 보안 권한을 구성하는 또 다른 옵션이 있습니다. 사용자 및 컴퓨터에 대해 읽기 및 등록 권한을 추가할 수 있습니다.  

## <a name="adding-read-and-enroll-permissions-for-users-and-computers"></a>사용자 및 컴퓨터에 대해 읽기 및 등록 권한 추가  
 별도의 팀에서 CA(인증 기관) 인프라 팀을 관리하는데 해당 팀에서 사용자에게 사용자 인증서를 요청하는 인증서 프로필을 보내기 전에 System Center Configuration Manager를 통해 사용자가 올바른 Active Directory Domain Services 계정을 보유하는지 확인하는 경우 사용자 및 컴퓨터에 대한 읽기 및 등록 권한 추가가 적절할 수 있습니다. 이 구성에서는 사용자가 포함된 보안 그룹을 하나 이상 지정하고 인증서 템플릿에 대한 읽기 및 등록 권한을 해당 그룹에 부여해야 합니다. 이 시나리오에서는 CA 관리자가 보안 제어를 관리합니다.  

 이와 비슷하게 컴퓨터 계정이 포함된 보안 그룹을 하나 이상 지정하고 해당 그룹에 인증서 템플릿에 대한 읽기 및 등록 권한을 부여할 수 있습니다. 컴퓨터 인증서 프로필을 도메인 멤버인 컴퓨터에 배포하는 경우 해당 컴퓨터의 컴퓨터 계정에 읽기 및 등록 권한을 부여해야 합니다. 컴퓨터가 도메인 멤버가 아닌 경우, 예를 들어 작업 그룹 컴퓨터나 개인 모바일 장치인 경우에는 이러한 권한이 필요하지 않습니다.  

 이 구성에서 추가 보안 제어를 사용하긴 하지만 모범 사례로 권장되지는 않습니다. 장치의 지정된 사용자 또는 소유자가 System Center Configuration Manager와 별도로 인증서를 요청하고 다른 사용자 또는 장치를 가장하는 데 사용되는 인증서 주체 값을 제공할 수 있기 때문입니다.  

 또한 인증서 요청이 수행될 때 인증할 수 없는 계정을 지정하면 기본적으로 인증서 요청이 실패하게 됩니다. 예를 들어 인증서 등록 지점 사이트 시스템 서버가 포함된 포리스트에서 신뢰하지 않는 Active Directory 포리스트에 네트워크 장치 등록 서비스를 실행하는 서버가 있는 경우 인증서 요청이 실패합니다. 도메인 컨트롤러에서 응답이 없어 계정을 인증할 수 없는 경우 인증서 등록 지점을 계속 진행하도록 구성할 수 있습니다. 그러나 이 방법은 보안 모범 사례가 아닙니다.  

 인증서 등록 지점이 계정 권한을 확인하도록 구성되어 있고 도메인 컨트롤러를 사용할 수 있으며 도메인 컨트롤러에서 인증 요청을 거부하면(예: 계정이 잠겨 있거나 삭제된 경우) 인증서 등록 요청에 실패합니다.  

#### <a name="to-check-for-read-and-enroll-permissions-for-users-and-domain-member-computers"></a>사용자 및 도메인 멤버 컴퓨터의 읽기 및 등록 권한을 확인하려면  

1.  인증서 등록 지점을 호스트하는 사이트 시스템 서버에 0 값을 갖는 다음 DWORD 레지스트리 키를 만듭니다. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck  

2.  도메인 컨트롤러에서 응답이 없어 계정을 인증할 수 없고 권한 확인을 무시하려는 경우  

    -   인증서 등록 지점을 호스트하는 사이트 시스템 서버에 1 값을 갖는 다음 DWORD 레지스트리 키를 만듭니다. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied  

3.  발급 CA에서, 인증서 템플릿 속성에 있는 **보안** 탭에서 보안 그룹을 하나 이상 추가하여 사용자 또는 장치 계정에 읽기 및 등록 권한을 부여합니다.  

