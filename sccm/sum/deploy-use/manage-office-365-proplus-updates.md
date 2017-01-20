---
title: "Office 365 ProPlus 업데이트 관리 | Microsoft 문서"
description: "Configuration Manager는 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버와 동기화하여 업데이트를 클라이언트에 배포할 수 있게 합니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
translationtype: Human Translation
ms.sourcegitcommit: 5415bfa0ac4af14891a9445cdeab6a4509fffc38
ms.openlocfilehash: 630ccdf7b7f45a88586c9ab530c164985267bec9

---

# <a name="manage-office-365-proplus-updates-with-configuration-manager"></a>Configuration Manager를 사용하여 Office 365 ProPlus 업데이트 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 버전 1602부터, Configuration Manager에서 소프트웨어 업데이트 관리 워크플로를 사용하여 Office 365 클라이언트 업데이트를 관리할 수 있습니다. Microsoft에서 새 Office 365 클라이언트 업데이트를 Office CDN(Content Delivery Network)에 게시하면 Microsoft에서 업데이트 패키지도 WSUS(Windows Server Update Services)에 게시합니다. Configuration Manager에서 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버로 동기화한 후에 업데이트를 클라이언트에 배포할 수 있습니다.

## <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드  
Configuration Manager 버전 1610부터 Configuration Manager 콘솔에서 Office 365 클라이언트 관리 대시보드를 사용할 수 있습니다. 대시보드를 보려면 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.

<!--- >[!NOTE]
>In the **What's New** workspace in the Configuration Manager console, the new dashboard is incorrectly named **Office 365 Servicing dashboard**. --->

대시보드는 다음에 대한 차트를 표시합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널     
자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://technet.microsoft.com/library/mt455210.aspx)를 참조하세요.
<!--- - Automatic deployment rules with Office 365 apps (have Office 365 Client selected in the set of available products). --->

<!---You can take the following actions on the dashboard:
- --->

대시보드 맨 위에 있는 **컬렉션** 드롭다운 설정을 사용하여 특정 컬렉션 멤버별로 대시보드 데이터를 필터링합니다.

<!---
 On the upper-right side of the dashboard, click **Office 365 Installer** to start the Office 365 Client Installation Wizard to deploy Office 365 apps to clients. For details, see [Deploy Office 365 apps to clients](#deploy-office-365-apps-to-clients).
- On the middle-right side of the dashboard, click **Create an ADR** to open the Automatic Deployment Rule Wizard to create a new automatic deployment rule (ADR). To create an ADR for Office 365 apps, select **Office 365 Client** when you choose the product. For more information, see [Automatically deploy software updates](/sccm/sum/deploy-use/automatically-deploy-software-updates).
- On the lower-right side of the dashboard, click **Create Client Agent Settings** to open Client Agent settings. For more information, see [About client settings](/sccm/core/clients/deploy/about-client-settings).
--->

#### <a name="to-deploy-office-365-updates-with-configuration-manager"></a>Configuration Manager를 사용하여 Office 365 업데이트를 배포하려면
Configuration Manager를 사용하여 Office 365 업데이트를 배포하려면 다음 단계를 따르세요.

1.  항목의 **Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 요구 사항** 섹션에서 Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 [요구 사항을 확인](https://technet.microsoft.com/library/mt628083.aspx)합니다.  

2.  [소프트웨어 업데이트 지점을 구성](../get-started/configure-classifications-and-products.md)하여 Office 365 클라이언트 업데이트를 동기화합니다. 분류에 대한 **업데이트**를 설정하고 제품에 대한 **Office 365 클라이언트**를 선택합니다. Office 365 클라이언트 제품을 선택할 수 있으려면 먼저 소프트웨어 업데이트를 한 번 이상 동기화해야 할 수도 있습니다. **업데이트** 분류를 사용하도록 소프트웨어 업데이트 지점을 구성한 후 소프트웨어 업데이트를 동기화해야 합니다.  

3.  Office 365 클라이언트가 Configuration Manager에서 업데이트를 받을 수 있도록 합니다. 이렇게 하려면 Configuration Manager 클라이언트 설정을 사용하거나 그룹 정책을 사용합니다. 다음 방법 중 하나를 통해 클라이언트를 사용하도록 설정합니다.  
    - 방법 1: Configuration Manager 버전 1606부터, Configuration Manager 클라이언트 설정을 사용하여 Office 365 클라이언트 에이전트를 관리할 수 있습니다. 이 설정을 구성하고 Office 365 업데이트를 배포한 후 Configuration Manager 클라이언트 에이전트는 Office 365 클라이언트 에이전트와 통신하여 배포 지점에서 Office 365 업데이트를 다운로드하고 설치합니다. Configuration Manager는 Office 365 ProPlus 클라이언트 설정의 인벤토리를 사용합니다.
      1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 클릭합니다.  

      2.  적절한 장치 설정을 열어 클라이언트 에이전트를 사용하도록 설정합니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

      3.  **소프트웨어 업데이트**를 클릭하고 **Office 365 클라이언트 에이전트 관리 사용** 설정에 대해 **예**를 선택합니다.  

    - 방법 2: Office 배포 도구 또는 그룹 정책을 사용하여 [Office 365 클라이언트가 Configuration Manager에서 업데이트를 받을 수 있도록 설정](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient)합니다.  

4. 클라이언트에 [Office 365 업데이트를 배포](deploy-software-updates.md)합니다.  

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->



<!--HONumber=Dec16_HO3-->


