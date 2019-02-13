---
title: Intune 독립 실행형을 선택 합니다.
titleSuffix: Configuration Manager
description: Intune 독립 실행형을 선택 합니다.
ms.date: 08/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dfbec94ac584442f65826d08c6b7abefc16d375
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56124175"
---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mdm-with-configuration-manager"></a>Configuration Manager를 사용하여 Microsoft Intune 독립 실행형 및 하이브리드 MDM 중에서 선택

*적용 대상: System Center Configuration Manager(현재 분기)*


하이브리드 모바일 장치 관리 (MDM)은 2018 년 8 월 14 일부 터는 [사용 되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)합니다. Azure의 Intune은 Microsoft에서 권장하는 MDM 솔루션입니다.  

자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  


<!--
One of the most commonly asked questions regarding mobile device management (MDM) with Microsoft Intune is "Should I integrate Intune with Configuration Manager (hybrid MDM) or run Intune standalone in the cloud only configuration?" 



 
## Intune standalone

Intune standalone is Microsoft’s recommended deployment topology. Intune standalone is a cloud-only MDM solution that you manage using a web console accessed from anywhere in the world. Intune data centers are hosted in North America, Europe, and Asia. Because Intune is a cloud service, you can quickly deploy Intune management to your devices.

Customers generally find it faster and easier to deploy the standalone topology because there's no dependency for on-premise components. Intune standalone is now on the Microsoft Azure cloud platform and provides many advanced features, such as:  

- Integrated enterprise mobility management platform: An integrated cloud platform and admin experience in Azure portal for Intune, Azure AD Premium, and Azure Information Protection  

- Mobile device management: Rich mobile device management and information protection capabilities  

- Scale: Deploy and manage mobile devices without worrying about scale  

- Role-based access control: Restrict access to administrative functions based on assigned roles and scopes  

- Programmatic access (API): Microsoft Graph API support, and SDK and PowerShell management options  

- Web console: An HTML 5-based console built on web standards with support for most modern web browsers  

- Advanced reporting: Ability to create customized reports  

- Agility: Simple setup and rapid delivery of new capabilities  



## Hybrid MDM with Configuration Manager

> [!Important]  
> As of August 14, 2018, hybrid mobile device management is a [deprecated feature](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). For more information, see [What is hybrid MDM](/sccm/mdm/understand/hybrid-mobile-device-management).  

Hybrid MDM is a solution that integrates Intune's mobile device management capabilities into Configuration Manager. It uses Intune as the delivery channel for policies, profiles, and applications to devices but uses Configuration Manager on-premises infrastructure to administer content and manage the devices. A hybrid implementation gives you "single pane of glass" control. This means you can use the same on-premises infrastructure and administrative console to manage mobile devices with Intune as well as PCs and servers with the traditional Configuration Manager client. 

You may choose hybrid MDM for the following reasons:  

- You want to manage both mobile devices enrolled in Intune and devices managed with the Configuration Manager client from the same administrative console  

- Your infrastructure requires that you have multiple NDES servers for certificate delivery to mobile devices  

- Your infrastructure requires that you have multiple Exchange connectors  

- You require S/MIME encryption support

> [!Note]  
> If you set up hybrid MDM in Configuration Manager for conditional access with on-premises Exchange, users can still access email in Outlook for iOS and Android. This same configuration with Intune standalone blocks email for these clients.<!--Intune bug 2285890-->  



#### <a name="change-the-mdm-authority"></a>MDM 기관 변경

MDM 기관 설정을 변경해야 하는 경우 Microsoft 지원에 문의하지 않고 기존의 관리 디바이스를 등록 취소했다가 다시 등록하지 않고도 변경할 수 있습니다. 자세한 내용은 [MDM 기관을 변경](/sccm/mdm/deploy-use/change-mdm-authority)합니다.

