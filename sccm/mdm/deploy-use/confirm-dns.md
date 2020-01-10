---
title: 도메인 이름 요구 사항 확인
titleSuffix: Configuration Manager
description: Configuration Manager를 사용 하 여 도메인 이름 요구 사항을 확인 합니다.
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 522c2e82-20eb-4f38-859b-d55640b24e32
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c5b10095e153bbd13493f1c24c8bb1fc563a147f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75822075"
---
# <a name="confirm-domain-name-requirements-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager 및 Microsoft Intune를 사용 하 여 도메인 이름 요구 사항 확인

*적용 대상: Configuration Manager (현재 분기)*

필요한 경우 다음 단계를 수행하여 Configuration Manager 외부 종속성을 충족합니다.

1. 디바이스를 등록하려면 각 사용자에게 Intune 라이선스가 할당되어야 합니다. Intune 라이선스를 사용자에 연결하려면 각 사용자에게 공개적으로 확인할 수 있는 UPN(사용자 계정 이름)(예: johndoe@contoso.com 또는 Azure Active Directory에 구성된 대체 로그인 ID)이 있어야 합니다. 대체 로그인 ID를 구성하면 해당 UPN이 NetBIOS 형식(예: CONTOSO\johndoe)인 사용자도 메일 주소를 사용하여 로그인할 수 있습니다.

   - 회사에서 공개적으로 확인할 수 있는 UPN(즉, johndoe@contoso.com)을 사용하는 경우에는 추가 구성이 필요하지 않습니다.
   - 회사에서 확인할 수 없는 UPN(즉, CONTOSO\johndoe)을 사용하는 경우 [Azure Active Directory에서 대체 ID를 구성](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync)해야 합니다.

2. AD FS(Active Directory Federated Services)를 배포 및 구성합니다. (선택적)

    Single Sign-On을 설정하면 사용자가 회사 자격 증명에 로그인하여 Intune의 서비스에 액세스할 수 있습니다.

    자세한 내용은 다음 항목을 참조하세요.
   -   [Single Sign-On 준비](https://go.microsoft.com/fwlink/?LinkID=271124)
   -   [Single Sign-On을 사용할 AD FS 2.0 계획 및 배포](https://go.microsoft.com/fwlink/?LinkID=271125)

3. 디렉터리 동기화 배포 및 구성

    디렉터리 동기화를 사용하면 동기화된 사용자 계정으로 Intune을 채울 수 있습니다. 동기화된 사용자 계정 및 보안 그룹은 Intune에 추가됩니다. 디렉터리 동기화를 사용하도록 설정하지 않으면 Configuration Manager MDM with Microsoft Intune을 설정할 때 보통 디바이스에서 등록할 수 없습니다.

    자세한 내용은 Active Directory 문서 라이브러리의 [디렉터리 통합](https://go.microsoft.com/fwlink/?LinkID=271120) 을 참조하세요.

4. 선택 사항이며 권장되지 않는 단계: ADFS(Active Directory Federation Services)를 사용하지 않을 경우 사용자의 Microsoft Online 암호를 다시 설정합니다.

    AD FS를 사용하지 않을 경우 각 사용자의 Microsoft Online 암호를 설정해야 합니다.

> [!div class="button"]
> [이전 단계 <](create-mdm-collection.md)  [다음 단계 >](configure-intune-subscription.md)
