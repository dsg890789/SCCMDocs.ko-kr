---
title: 추가 관리 설정
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 추가 관리 설정
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 4877d674-6bbc-4e16-810c-daad70c74daa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 58a61dffbdd9b04d3e872e23f88ddc0ac864f99d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-additional-management-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 추가 관리 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

(선택 사항) 장치가 등록되기 전에 추가 관리를 설정할 수 있습니다. 장치가 등록된 후에 이러한 관리 솔루션을 만들고 배포할 수도 있지만 대부분의 조직에서는 장치가 관리에 추가될 때 배포하려고 합니다.

**구성 항목**을 사용하면 장치 플랫폼에 따라 등록된 장치에서 PIN 요구 또는 암호화 요구 등의 설정을 관리할 수 있습니다.
- [Windows 10 및 Windows 8.1 장치](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Windows Phone 장치](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)
- [iOS 및 Mac 장치](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)
- [Android 및 Samsung KNOX Standard 장치](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)

**응용 프로그램**을 관리 장치에 배포할 수 있습니다.
- [iOS 응용 프로그램](creating-ios-applications.md)
- [Mac 응용 프로그램](../../apps/get-started/creating-mac-computer-applications.md)
- [Windows PC 응용 프로그램](../../apps/get-started/creating-windows-applications.md)
- [Windows Phone 응용 프로그램](creating-windows-phone-applications.md)
- [Android 응용 프로그램](creating-android-applications.md)

**조건부 액세스**를 사용하면 다음을 비롯한 회사 리소스에 대한 액세스를 관리할 수 있습니다.  
- [메일 액세스](manage-email-access.md)
- [SharePoint 액세스](manage-sharepoint-online-access.md)
- [비즈니스용 Skype 액세스](manage-skype-for-business-online-access.md)
- [Dynamic CRM Online](manage-dynamics-crm-online-access.md)

**MFA(다단계 인증)** 를 사용하면 둘 이상의 확인 방법을 요구하여 사용자 로그인 및 트랜잭션에 중요한 두 번째 보안 계층을 추가할 수 있습니다.
이전에는 Intune 등록용으로 MFA를 설정하려면 Intune 콘솔 또는 Configuration Manager 콘솔로 이동해야 했습니다. 이제 [Microsoft Azure Portal](https://manage.windowsazure.com)에 Intune 자격 증명으로 로그인하고 Azure AD를 통해 MFA 설정을 구성합니다. 자세한 내용은 [Microsoft Intune용 다단계 인증](https://aka.ms/mfa_ad)을 참조하세요.

> [!div class="button"]
[< 이전 단계](enable-platform-enrollment.md)  [다음 단계 >](verify-mdm-configuration.md)
