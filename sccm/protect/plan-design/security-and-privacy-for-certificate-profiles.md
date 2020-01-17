---
title: 인증서 프로필 보안 및 개인 정보
titleSuffix: Configuration Manager
description: Configuration Manager에서 사용자 및 디바이스의 인증서 프로필 관리에 대한 보안 모범 사례를 알아봅니다.
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 3393db41-900a-44c5-b950-2d46a35a198c
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 4b7db4537965b17cd56cc4d996eec576c2b18965
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75819100"
---
# <a name="security-and-privacy-for-certificate-profiles-in-configuration-manager"></a>Configuration Manager의 인증서 프로필에 대한 보안 및 개인 정보

*적용 대상: Configuration Manager(현재 분기)*


##  <a name="security-best-practices-for-certificate-profiles"></a>인증서 프로필에 대한 보안 모범 사례  
 사용자 및 디바이스에 대한 인증서 프로필을 관리할 때 다음 보안 모범 사례를 따르십시오.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|SSL을 요구하고 클라이언트 인증서를 무시하도록 IIS(인터넷 정보 서비스)의 네트워크 디바이스 등록 서비스 웹 사이트를 구성하는 작업을 비롯하여 네트워크 디바이스 등록 서비스에 대한 보안 모범 사례를 확인하고 따릅니다.|자세한 내용은 TechNet의 Active Directory 인증서 서비스 라이브러리에서 [Network Device Enrollment Service Guidance(네트워크 디바이스 등록 서비스 지침)](https://go.microsoft.com/fwlink/p/?LinkId=309016) 를 참조하세요.|  
|SCEP 인증서 프로필을 구성하는 경우 디바이스 및 인프라가 지원하는 가장 보안 수준이 높은 옵션을 선택합니다.|디바이스와 인프라에 권장되는 모든 보안 모범 사례를 식별하여 구현하고 따르십시오.|  
|사용자에게 기본 디바이스를 식별할 수 있도록 허용하는 대신 사용자 디바이스 선호도를 수동으로 지정합니다. 또한 사용 빈도 기반 구성을 사용하지 않도록 설정합니다.|SCEP 인증서 프로필에서 **사용자 기본 디바이스에 대해서만 인증서 등록 허용** 옵션을 클릭한 경우 사용자 또는 디바이스에서 수집한 정보를 신뢰할 수 있는 정보로 간주해서는 안 됩니다. 이러한 구성이 있는 SCEP 인증서 프로필을 배포하고 신뢰할 수 있는 관리자가 사용자 디바이스 선호도를 지정하지 않은 경우에는 권한이 없는 사용자가 상승된 권한을 받아서 인증용 인증서를 받을 수도 있습니다.<br /><br /> **참고:** 사용량 기반 구성을 사용하도록 설정한 경우 Configuration Manager에서 보호하지 않는 상태 메시지를 사용하여 이 정보가 수집됩니다. 이러한 위협을 완화하려면 클라이언트 컴퓨터와 관리 지점 간에 SMB 서명 또는 IPsec을 사용합니다.|  
|사용자의 읽기 및 등록 권한을 인증서 템플릿에 추가하거나 인증서 등록 지점이 인증서 템플릿 검사를 건너뛰도록 구성하지 마세요.|사용자의 읽기 및 등록 보안 권한을 추가하는 경우 Configuration Manager에서 추가 검사가 지원되고, 인증이 불가능한 경우 이 검사를 건너뛰도록 인증서 등록 지점을 구성할 수 있지만 두 구성 모두 보안 모범 사례는 아닙니다. 자세한 내용은 [인증서 프로필에 대한 인증서 템플릿 권한 계획](../../protect/plan-design/planning-for-certificate-template-permissions.md)을 참조하세요.|  

## <a name="privacy-information-for-certificate-profiles"></a>인증서 프로필의 개인 정보 보호  
 인증서 프로필을 사용하여 루트 CA(인증 기관) 및 클라이언트 인증서를 배포할 수 있으며 프로필이 적용된 후 해당 디바이스가 호환 상태가 되는지 여부를 평가할 수 있습니다. 관리 지점에서 호환성 정보를 사이트 서버로 보내고 Configuration Manager에서 해당 정보를 사이트 데이터베이스에 저장합니다. 호환성 정보에는 주체 이름 및 지문 같은 인증서 속성이 포함됩니다. 디바이스에서 관리 지점으로 정보를 보낼 때 정보가 암호화되지만 사이트 데이터베이스에는 암호화된 형식으로 저장되지 않습니다. 데이터베이스는 사이트 유지 관리 작업, **오래된 구성 관리 데이터 삭제** 에서 기본 간격인 90일 이후에 정보를 삭제할 때까지 정보를 보존합니다. 삭제 간격은 필요에 따라 구성할 수 있습니다. 호환성 정보는 Microsoft로 전송되지 않습니다.  

 인증서 프로필은 Configuration Manager에서 검색을 사용하여 수집한 정보를 사용합니다. 검색에 대한 개인 정보의 자세한 내용은 [Configuration Manager의 보안 및 개인 정보](../../core/plan-design/security/security-and-privacy.md)에서 **검색에 대한 개인 정보** 섹션을 참조하세요.  

> [!NOTE]  
>  사용자 또는 디바이스에 발급된 인증서를 통해 기밀 정보에 대한 액세스가 허용될 수 있습니다.  

 기본적으로 디바이스는 인증서 프로필을 평가하지 않습니다. 또한 인증서 프로필을 구성한 후 사용자 또는 디바이스에 배포해야 합니다.  

 인증서 프로필을 구성하려면 먼저 개인 정보 취급 방침 요구 사항을 검토하십시오.  
