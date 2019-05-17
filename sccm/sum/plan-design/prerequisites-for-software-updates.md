---
title: 소프트웨어 업데이트에 대한 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 소프트웨어 업데이트에 대한 필수 조건에 대해 알아봅니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 02/02/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.collection: M365-identity-device-management
ms.openlocfilehash: 92e1d0e672d4fc5e6e98f87ba92cec2602f7d240
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65496203"
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager의 소프트웨어 업데이트에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

이 목록에서는 System Center Configuration Manager의 소프트웨어 업데이트에 대한 필수 조건을 나열합니다. 각 필수 구성 요소에 대해 외부 종속성과 내부 종속성이 별도의 표에 표시됩니다.  

## <a name="software-update-dependencies-that-are-external-to-configuration-manager"></a>Configuration Manager 외부인 소프트웨어 업데이트 종속성  
 다음 섹션에는 소프트웨어 업데이트에 대한 외부 종속성이 나열되어 있습니다.  

### <a name="internet-information-services"></a>인터넷 정보 서비스  
 IIS(인터넷 정보 서비스)는 소프트웨어 업데이트 지점, 관리 지점, 배포 지점의 실행을 위해 사이트 시스템 서버에 설치되어야 합니다. 자세한 내용은 [사이트 시스템 역할에 대한 필수 조건](../../core/plan-design/configs/site-and-site-system-prerequisites.md)을 참조하세요.  

### <a name="windows-server-update-services"></a>Windows Server Update Services  
 WSUS(Windows Server Update Services)는 클라이언트에서 소프트웨어 업데이트 동기화 및 소프트웨어 업데이트 적용 가능 여부 검사를 수행하는 데 필요합니다. WSUS 서버는 소프트웨어 업데이트 지점 역할을 만들기 전에 설치해야 합니다. 소프트웨어 업데이트 지점에 대해 다음 버전의 WSUS가 지원됩니다.  

-   WSUS 10.0.14393(Windows Server 2016의 역할)
-   WSUS 10.0.17763(Windows Server 2019의 역할)(Configuration Manager 1810 이상 필요)
-   WSUS 6.2 및 6.3(Windows Server 2012 및 Windows Server 2012 R2의 역할)

>[!NOTE]
>-   버전 1702부터 Windows Server 2008 R2는 소프트웨어 업데이트 지점 역할을 지원하지 않습니다. 자세한 내용은 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers#bkmk_2008r2sp1)를 참조하세요.  

한 사이트에 여러 소프트웨어 업데이트 지점이 있는 경우 모두 동일한 버전의 WSUS를 실행해야 합니다.  

> [!WARNING]  
>  소프트웨어 업데이트 분류 **업그레이드**는 WSUS 4.0부터 지원됩니다. 새로운 분류를 동기화하고 Windows 10 서비스 계획에서 Windows 10 컴퓨터를 평가하는 기능을 얻기 전에 소프트웨어 업데이트 지점 및 사이트 서버에 WSUS용 [핫픽스 3095113](https://support.microsoft.com/kb/3095113) 을 반드시 설치해야 합니다. 이 핫픽스를 통해 Windows Server 2012 기반 서버 또는 Windows Server 2012 R2 기반 서버의 WSUS에서 Windows 10용 기능 업그레이드를 동기화하고 배포할 수 있습니다. 자세한 내용은 [Windows as a Service 관리](../../osd/deploy-use/manage-windows-as-a-service.md)를 참조하세요.  
>   
>  [핫픽스 3095113](https://support.microsoft.com/kb/3095113)을 설치하기 전에 **업그레이드** 분류와 소프트웨어 업데이트를 동기화하는 경우 [KB 3095113을 설치하기 전에 업그레이드 범주 동기화에서 복구](#BKMK_RecoverUpgrades)를 참조하세요.  

### <a name="wsus-administration-console"></a>WSUS 관리 콘솔  
 소프트웨어 업데이트 지점이 원격 사이트 시스템 서버에 있고 WSUS가 Configuration Manager 사이트 서버에 아직 설치되지 않은 경우 이 사이트 서버에 WSUS 관리 콘솔이 필요합니다.  

> [!IMPORTANT]  
> 사이트 서버의 WSUS 버전은 소프트웨어 업데이트 지점에서 실행 중인 WSUS 버전과 같아야 합니다.
>
> WSUS 관리 콘솔을 사용하여 WSUS 설정을 구성하지 마세요. Configuration Manager는 소프트웨어 업데이트 지점에서 실행 중인 WSUS의 인스턴스에 연결하고 적합한 설정을 구성합니다.  



### <a name="windows-update-agent"></a>Windows Update 에이전트  
 WSUS 서버에 연결할 수 있도록 클라이언트에 WUA(Windows Update 에이전트) 클라이언트가 필요합니다. WUA는 호환성을 검사해야 하는 소프트웨어 업데이트의 목록을 검색합니다.  

 Configuration Manager를 설치하면 최신 버전의 WUA가 다운로드됩니다. 그런 다음, Configuration Manager 클라이언트가 설치될 때 필요한 경우 WUA가 업그레이드됩니다. 그러나 이 설치가 실패하면 다른 방법을 사용하여 WUA를 업그레이드해야 합니다.  

## <a name="software-update-dependencies-that-are-internal-to-configuration-manager"></a>Configuration Manager 내부인 소프트웨어 업데이트 종속성  
 다음 섹션에는 Configuration Manager의 소프트웨어 업데이트에 대한 내부 종속성이 나열되어 있습니다.  

### <a name="management-points"></a>관리 지점  
 관리 지점은 클라이언트 컴퓨터와 Configuration Manager 사이트 간에 정보를 전송합니다. 관리 지점은 소프트웨어 업데이트에 필요합니다.  

### <a name="software-update-points"></a>소프트웨어 업데이트 지점  
 Configuration Manager에서 소프트웨어 업데이트를 배포하려면 WSUS 서버에 소프트웨어 업데이트 지점을 설치해야 합니다. 자세한 내용은 [소프트웨어 업데이트 지점 설치 및 구성](../get-started/install-a-software-update-point.md)을 참조하세요.

### <a name="distribution-points"></a>배포 지점  
 소프트웨어 업데이트에 대한 콘텐츠를 저장하려면 배포 지점이 필요합니다. 배포 지점을 설치하고 콘텐츠를 관리하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

### <a name="client-settings-for-software-updates"></a>소프트웨어 업데이트를 위한 클라이언트 설정  
 기본적으로 소프트웨어 업데이트는 클라이언트에 대해 사용하도록 설정됩니다. 그러나 클라이언트에서 소프트웨어 업데이트에 대한 호환성을 평가하는 방법과 시점을 제어하고 소프트웨어 업데이트가 설치되는 방식을 제어하는 다른 설정도 있습니다.  

 자세한 내용은 다음 아티클을 참조하세요.  

-   [소프트웨어 업데이트를 위한 클라이언트 설정](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings)   

-   [소프트웨어 업데이트 클라이언트 설정](../../core/clients/deploy/about-client-settings.md#software-updates)  

### <a name="reporting-services-points"></a>보고 서비스 지점  
 보고 서비스 지점 사이트 시스템 역할에서는 소프트웨어 업데이트에 대한 보고서를 표시할 수 있습니다. 이 역할은 선택 사항이지만 사용하는 것이 좋습니다. 보고 서비스 지점을 만드는 방법에 대한 자세한 내용은 [보고 구성](../../core/servers/manage/configuring-reporting.md)을 참조하세요.  

##  <a name="BKMK_RecoverUpgrades"></a> KB 3095113을 설치하기 전에 업그레이드 범주 동기화에서 복구  
 **업그레이드** 분류를 동기화하기 전에 소프트웨어 업데이트 지점 및 사이트 서버에 WSUS용 [핫픽스 3095113](https://support.microsoft.com/kb/3095113)을 설치해야 합니다. **업그레이드** 분류를 사용하도록 설정할 때 핫픽스가 설치되어 있지 않으면 연결된 패키지를 제대로 다운로드하여 배포할 수 없는 경우에도 WSUS에서 Windows 10 빌드 1511 기능 업그레이드를 표시합니다. 
 
 먼저 [핫픽스 3095113](https://support.microsoft.com/kb/3095113)을 설치하지 않고 업그레이드를 동기화하는 경우 WSUS 데이터베이스(SUSDB) 업그레이드가 사용할 수 없는 데이터로 채워집니다. 이러한 데이터는 업그레이드를 제대로 배포하기 위해 지워야 합니다. 이 문제를 해결하려면 다음 절차를 따르세요.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>KB 3095113을 설치하기 전에 업그레이드 분류 동기화에서 복구하려면  

1.  **업그레이드** 분류가 있는 소프트웨어 업데이트를 삭제합니다. 다음 샘플 스크립트와 유사한 PowerShell 스크립트를 사용할 수 있습니다.  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  다음 단계로 진행하기 전에 Configuration Manager 계층 구조의 모든 소프트웨어 업데이트 지점에서 스크립트를 실행해야 합니다.  

     **업그레이드** 분류가 포함된 대량 소프트웨어 업데이트를 삭제하기 위해 텍스트 파일에서 여러 GUID를 읽도록 PowerShell 스크립트를 수정할 수 있습니다.  

2.  소프트웨어 업데이트 지점 구성요 소 조건에서 **업그레이드** 분류의 선택을 해제합니다. (자세한 내용은 [분류 및 제품 구성](../get-started/configure-classifications-and-products.md)을 참조하세요.) 그런 다음, 소프트웨어 업데이트 동기화를 시작합니다. (자세한 내용은 [소프트웨어 업데이트 동기화](../get-started/synchronize-software-updates.md)를 참조하세요.)  

3.  소프트웨어 업데이트 지점과 사이트 서버에서 WSUS에 [핫픽스 3095113](https://support.microsoft.com/kb/3095113) 을 반드시 설치해야 합니다.  

4.  소프트웨어 업데이트 지점 구성 요소 속성에서 **업그레이드** 분류를 선택합니다. (자세한 내용은 [분류 및 제품 구성](../get-started/configure-classifications-and-products.md)을 참조하세요.) 그런 다음, 소프트웨어 업데이트 동기화를 시작합니다. (자세한 내용은 [소프트웨어 업데이트 동기화](../get-started/synchronize-software-updates.md)를 참조하세요.)  

## <a name="next-steps"></a>다음 단계
[소프트웨어 업데이트 관리 준비](../get-started/prepare-for-software-updates-management.md)
