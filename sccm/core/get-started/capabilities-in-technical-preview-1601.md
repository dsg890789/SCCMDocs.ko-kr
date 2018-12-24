---
title: 기술 미리 보기 1601의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1601에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: aae1cf2f-2c04-4f68-a03a-f4a925433c09
author: aczechowski
robots: noindex,nofollow
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: f75c27ece3b9a8b490fb136a411a65ac4cbe2129
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32339471"
---
# <a name="capabilities-in-technical-preview-1601-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1601의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1601에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.  

 **Technical Preview의 알려진 문제:**  

-   **클라이언트 업데이트 옵션**을 관리하여 사전 프로덕션 클라이언트를 프로덕션으로 승격하는 경우 해당 확인란에 실제 클라이언트 빌드 번호 대신 클라이언트 버전 0이 표시됩니다. 올바른 사전 프로덕션 클라이언트 버전은 이 옵션 위의 화면에 표시되며, 이 옵션을 선택하면 프로덕션으로 승격되는 클라이언트 버전을 나타냅니다.  

-   Technical Preview 1601로 업데이트하고 사전 프로덕션 컬렉션에서 Configuration Manager 클라이언트를 테스트하도록 선택하는 경우, 컬렉션에 대한 클라이언트 패키지는 업그레이드되지 않습니다. 이 문제는 Technical Preview 1601에서만 발생합니다.  

     이 문제를 해결하려면 다음 중 하나를 수행하세요.  

    -   기본 사이트의 데이터베이스에서 다음 SQL 스크립트를 실행합니다.  

        ```  
        DECLARE @PilotingPkgID NVARCHAR(8)  

        SELECT @PilotingPkgID = PilotingPackageID FROM ClientDeploymentSettings  

        MERGE INTO PkgServers_G AS T  
        USING (  
            SELECT @PilotingPkgID AS PkgID, NALPath, SiteCode, SiteName, SourceSite, RefreshTrigger, UpdateMask, [Action]  
            FROM PkgServers_G WHERE PkgID IN (SELECT UpgradePackageID FROM ClientDeploymentSettings)  
            ) AS S  
        ON T.PkgID = S.PkgID and T.NALPath = S.NALPath  

        WHEN NOT MATCHED THEN  
            INSERT (PkgID, NALPATH, SiteCode, SiteName, SourceSite, LastRefresh, RefreshTrigger, UpdateMask, [Action])  
            VALUES (S.PkgID, S.NALPath, S.SiteCode, S.SiteName, S.SourceSite, GetUTCDate(), S.RefreshTrigger, S.UpdateMask, S.[Action])  
        ;  

        ```  

    -   랩 사이트에 새 배포 지점 사이트 시스템 역할을 추가합니다. 새 배포 지점은 새 클라이언트 패키지를 사용하여 사전 프로덕션 컬렉션을 업그레이드합니다.  

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

##  <a name="bkmk_hybrid1"></a> Microsoft Intune 통합 향상  
1601 기술 미리 보기에서는 다음 기능에 대한 지원이 추가되었습니다.  

### <a name="improvements-to-conditional-access"></a>향상된 조건부 액세스 기능  

-   **System Center Configuration Manager에서 관리되는 PC에 대한 조건부 액세스 지원**  

     이제 System Center Configuration Manager에서 관리되는 PC에 대해 조건부 액세스 정책을 설정할 수 있습니다. Exchange Online 및 SharePoint Online 서비스에 액세스하기 위해 PC는 준수 정책을 준수해야 합니다.  이 새로운 기능을 사용하면 준수 정책을 통해 Azure AD에 PC를 등록하고, Azure AD 등록을 모니터링 및 보고할 수 있습니다.  

    > [!NOTE]  
    >  Windows 10에서는 조건부 액세스가 아직 지원되지 않습니다.  

    다음은 이 기능을 사용하기 위한 필수 구성 요소입니다.  

    -   Azure Active Directory Premium 구독 및 ADFS 동기화  

    -   Microsoft Intune 구독 Microsoft Intune 구독은 Configuration Manager 콘솔에서 구성해야 합니다.  

    -   [Azure AD 자동 등록에 대한 필수 조건](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)  

    이 옵션을 사용하려면 아래에 설명된 특정 규칙을 사용하여 Configuration Manager에서 준수 정책을 만들고, Intune 콘솔에서 조건부 액세스 정책을 설정해야 합니다.  또한 호환 PC에만 액세스를 허용하려면 Windows PC 요구 사항을 **디바이스가 호환되어야 함** 옵션으로 설정해야 합니다. 다음은 System Center Configuration manager에서 관리하는 PC에 적용되는 준수 정책 규칙입니다.  

    -   **Azure ActiveDirectory에서 등록 필요:** 이 규칙은 사용자의 장치가 Azure AD에 연결된 작업 영역인지 확인합니다. 그렇지 않은 경우 장치는 Azure AD에서 자동으로 등록됩니다. 자동 등록은 Windows 8.1에서만 지원됩니다. Windows 7 PC의 경우 자동 등록을 수행하기 위해 MSI를 배포합니다. 자세한 내용은 [여기](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)를 참조하세요.  

    -   **마감일이 다음 기간보다 오래된 필수 업데이트가 모두 설치됨:** 이 규칙은 마감일 및 사용자가 지정한 유예 기간 내에 사용자 장치에 모든 필수 업데이트(**필수 자동 업데이트** 규칙에 지정)가 설치되는지 확인하고 보류 중인 모든 필수 업데이트를 자동으로 설치합니다.  

    -   **BitLocker 드라이브 암호화 필요:** 장치의 기본 드라이브(예: C:\\)가 BitLocker로 암호화되어 있는지 확인합니다. 기본 디바이스에서 Bitlocker 암호화가 사용되도록 설정되지 않으면 메일 및 SharePoint 서비스에 대한 액세스가 차단됩니다.  

    -   **맬웨어 방지 필요:** 맬웨어 방지 프로그램(System Center Endpoint Protection 또는 Windows Defender만)이 사용되도록 설정되고 실행 중인지 확인합니다.  
         사용되도록 설정되지 않았으면 메일 및 SharePoint 서비스에 대한 액세스가 차단됩니다.  

    비준수로 인해 차단된 최종 사용자는 SCCM 소프트웨어 센터에서 호환성 정보를 확인하고 호환성 문제가 해결되면 새로운 정책 평가를 시작합니다.  

-   **상태 증명 서비스를 사용하는 조건부 액세스** 이제 상태 증명 서비스에서 보고되는 장치의 상태를 기준으로, 메일 및 0365 서비스에 대한 액세스를 제한할 수 있습니다.  또한 Intune에서 관리되는 디바이스는 디바이스 상태 보고서에 포함됩니다.  

    상태에 따라 디바이스의 액세스가 허용 또는 차단되어야 하는지를 지정할 수 있는 새 준수 규칙이 Configuration Manager 콘솔에 추가되었습니다.  이 규칙을 만들려면 **준수 정책 만들기 마법사**를 열고 새 규칙을 추가합니다.  상태에 대해 **상태 증명 서비스에서 정상으로 보고됨**을 선택하고 해당 값을 **True**로 설정합니다.  이렇게 하면 정상으로 보고되는 디바이스만 회사 리소스에 액세스할 수 있습니다. 상태 증명 서비스 및 Intune에서 디바이스 상태가 보고되는 방법에 대한 자세한 내용은 [디바이스 상태 증명](#bkmk_devicehealth)을 참조하세요.  

-   **새 준수 정책 설정:** 새로운 준수 정책 설정은 회사 메일 및 SharePoint Services에 액세스하는 데 사용되는 장치에 대해 보안 및 보호를 향상시키는 데 도움이 됩니다.  

    -   **자동 업데이트 필요:** Windows 8.1 이상 장치에서 업데이트의 자동 설치를 허용하도록 요구하고 설치되는 업데이트 클래스를 지정할 수 있습니다.  중요로 표시된 업데이트만 설치하거나 모든 권장 업데이트를 설치하도록 선택할 수 있습니다.  

         자동 업데이트에 대한 규칙을 만들려면 **준수 정책 만들기 마법사**를 열고 새 규칙을 추가합니다.  조건으로 **필수 업데이트 최소 분류**를 선택하고 값을 **없음**, **권장** 및 **중요** 중에서 하나로 설정합니다.  

        -   **없음:** 업데이트가 자동으로 설치되지 않습니다.  

        -   **권장:** 모든 권장 업데이트가 설치됩니다.  

        -   **중요:** 중요로 분류된 업데이트에만 설치됩니다.  

    -   **모바일 장치의 잠금을 해제하는 데 암호 필요:** 이 설정을 **예**로 설정하면 최종 사용자는 장치에 액세스하기 위해 먼저 암호를 입력해야 합니다.  

         모바일 디바이스 잠금 해제를 위한 암호 규칙을 만들려면 **준수 정책 만들기 마법사**를 열고 새 규칙을 추가합니다. 조건으로 **유휴 디바이스의 잠금을 해제하는 데 암호 필요**를 선택하고 해당 값을 **True**로 설정합니다.  

    -   **암호를 요구하기 전까지 비활성 시간(분):** 사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 지정합니다.  

         이 규칙을 만들려면 **준수 정책 만들기 마법사**를 열고 새 규칙을 추가합니다. 조건으로 **암호를 요구하기 전까지 비활성 시간(분)** 을 선택하고 해당 값을 1분, 5분, 15분, 30분, 1시간 중 하나로 설정합니다.  

-   **기본 규칙 재정의 - Intune 등록 및 규격 장치가 Exchange 온-프레미스에 액세스할 수 있도록 항상 허용:**  

     이 옵션을 선택하면 Intune에 등록되어 있고 준수 정책을 준수하는 디바이스는 Exchange 온-프레미스에 액세스할 수 있습니다. 이 규칙은 기본 규칙을 재정의하며, 이것은 기본 규칙을 액세스를 격리 또는 차단하도록 설정하더라도 등록 및 규격 디바이스는 여전히 Exchange 온-프레미스에 액세스할 수 있음을 의미합니다.  
     등록 및 규격 디바이스가 항상 Exchange 온-프레미스를 통해 메일에 액세스할 수 있도록 하려면 이 설정을 사용합니다.  

     이 옵션이 지원되는 플랫폼은 Windows Phone 8 이상, iOS 6 이상입니다. Android 4.0 이상, Samsung KNOX Standard 4.0 이상  

     이 옵션을 사용하려면 Exchange 온-프레미스에 대한 **조건부 액세스 정책 구성 마법사**의 **일반** 페이지로 이동합니다.  

##  <a name="bkmk_clientStatus"></a> 클라이언트 온라인 상태  
Technical Preview 1601부터는 Configuration Manager 콘솔에서 클라이언트가 온라인 상태인지 또는 오프라인 상태인지를 쉽게 알아볼 수 있습니다. 콘솔 디바이스 목록에 업데이트된 아이콘 및 열이 표시되므로 작업 환경의 클라이언트 상태를 평가하여 문제 영역 및 주의해야 할 기타 문제를 파악할 수 있습니다.  

클라이언트가 현재 Configuration Manager 관리 지점 사이트 시스템 역할에 연결되어 있으면 온라인 상태인 것입니다. 관리 지점이 클라이언트에서 ping과 유사한 메시지를 받는 동안은 온라인 상태입니다. 관리 지점에서 5분 정도 메시지를 받지 못하면 클라이언트 상태가 오프라인으로 변경된 것입니다.  

### <a name="icons-for-client-status"></a>클라이언트 상태에 대한 아이콘  

|||  
|-|-|  
|![클라이언트에 대한 온라인 상태 아이콘](media/online-status-icon.png)|클라이언트가 온라인 상태입니다.|  
|![클라이언트에 대한 오프라인 상태 아이콘](media/offline-status-icon.png)|클라이언트가 오프라인 상태입니다.|  
|![클라이언트에 대한 알 수 없는 상태 아이콘](media/unknown-status-icon.png)|클라이언트 상태를 알 수 없습니다.|  

### <a name="prerequisites"></a>필수 구성 요소  
 클라이언트 온라인 상태에는 필수 구성 요소가 없습니다. Configuration Manager Technical Preview 1601이 설치되기만 하면 바로 사용할 수 있습니다.  

### <a name="limitations"></a>제한 사항  
 클라이언트 온라인 상태는 Configuration Manager 클라이언트가 설치된 Windows 컴퓨터에서만 사용할 수 있습니다. Mac 컴퓨터, Linux 또는 UNIX 컴퓨터, 온\-프레미스 모바일 디바이스 관리로 관리되는 디바이스에서는 클라이언트 온라인 상태가 지원되지 않습니다.  

### <a name="to-view-client-online-status"></a>클라이언트의 온라인 상태를 보려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수 > 개요 > 장치**로 이동합니다.  

2.  열 머리글을 마우스 오른쪽 단추로 클릭하고 클라이언트 온라인 상태 필드 중 하나를 클릭하여 디바이스 보기에 추가합니다. 다음과 같은 필드가 제공됩니다.  

    -   **장치 온라인 상태** 는 클라이언트가 현재 온라인 상태인지 또는 오프라인 상태인지를 나타냅니다.  

    -   **마지막 온라인 시간**은 클라이언트 온라인 상태가 오프라인에서 온라인으로 변경되었을 때를 나타냅니다.  

    -   **마지막 오프라인 시간**은 상태가 온라인에서 오프라인으로 변경되었을 때를 나타냅니다.  

 클라이언트 상태에 대한 최근 변경 내용을 보려면 콘솔을 새로 고칩니다.  

##  <a name="bkmk_appmgmt1601"></a> 응용 프로그램 관리 향상  
 1601 기술 미리 보기에서는 다음 기능에 대한 지원이 추가되었습니다.  

### <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS 디바이스용 대량 구매 앱 관리  
 일부 앱 스토어는 회사에서 실행하려는 앱의 라이선스를 여러 개 구입하는 기능을 제공합니다. 이 기능을 사용하면 구입한 앱의 여러 복사본을 추적하는 관리 오버헤드를 줄일 수 있습니다.  

 Configuration Manager는 이제 App Store에서 라이선스 정보를 가져오고 사용한 라이선스 수를 추적하여 이러한 프로그램을 통해 구매한 앱의 관리를 지원합니다.  

 자세한 내용은 [Configuration Manager를 사용하여 대량 구매 프로그램을 통해 구입한 앱 관리](https://technet.microsoft.com/library/mt627954.aspx)를 참조하세요.  

### <a name="ios---app-configuration-for-applicationsbr-hybrid"></a>iOS - 응용 프로그램에 대한 앱 구성<br />하이브리드  
 일부 iOS 응용 프로그램은 응용 프로그램이 연결되어야 하는 서버 또는 데이터베이스와 같은 사전 구성 설정을 지원합니다. Configuration Manager에서는 이제 사용자가 이 정보를 알지 못해도 즉시 앱을 사용할 수 있도록 하는 앱 구성 정책을 디바이스에 배포할 수 있도록 지원합니다. 개발자는 자신의 앱에서 이 기능을 사용하도록 설정해야 합니다.  

 공개적으로 출시된 앱 중 제한된 일부가 현재 사전 구성 설정을 지원합니다. 이러한 설정을 지원하는 비즈니스 앱에 대한 사내 개발 라인을 구축할 수도 있습니다.  

#### <a name="prerequisites-for-this-scenario"></a>이 시나리오의 필수 구성 요소  

-   Configuration Manager에 Microsoft Intune 구독을 미리 추가했어야 합니다.  

-   유효한 Apple APNs 인증서를 Intune 구독에 미리 추가해야 합니다.  

-   응용 프로그램 구성을 지원하는 iOS 응용 프로그램을 미리 배포해야 합니다.  

#### <a name="try-it-out"></a>기능 직접 사용해 보기  
 위에 나온 필수 조건이 충족되면 iOS 배포 유형을 사용하는 Configuration Manager 응용 프로그램을 만들어야 합니다. 사용하는 앱은 응용 프로그램 구성을 지원해야 합니다. 구성할 수 있는 특정 항목(이름/값 쌍)에 대해 알아보려면 응용 프로그램의 공급업체 설명서를 참조하세요.  

 그런 다음 앱을 배포하는 동안 앱 구성 정책을 iOS 배포 유형에 연결합니다. **앱 구성 정책** 노드에서 기존 앱 및 컬렉션을 대상으로 하는 정책을 배포할 수도 있습니다.  

 다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

-   앱 구성을 지원하는 iOS 앱이 있는 경우 앱 공급업체 설명서를 참조하여 응용 프로그램을 구성하기 위해 지정해야 하는 이름/값 쌍을 확인하세요.  

-   **앱 구성 정책 만들기** 마법사를 시작합니다. 마법사의 **iOS 정책** 페이지에서 앱 공급업체 설명서에서 찾은 이름/값 쌍을 추가하거나 필요한 값이 포함된 XML 파일을 가져올 수 있습니다.  

-   **소프트웨어 배포** 마법사의 **앱 구성 정책** 페이지에서 만든 앱 구성 정책을 응용 프로그램의 호환 가능한 배포 유형에 연결합니다.  

##  <a name="bkmk_compliance1601"></a> 향상된 호환성 설정  
 1601 기술 미리 보기에서는 다음 기능에 대한 지원이 추가되었습니다.  

### <a name="microsoft-edge-browser-settings"></a>Microsoft Edge 브라우저 설정  
 Microsoft Edge 브라우저에 대한 새 설정이 **Windows 8.1 및 Windows 10** 구성 항목(설정은 Windows 10 디바이스에만 적용됨)에 추가되었습니다.  

 새 설정을 보려면 **구성 항목 만들기** 마법사의 구성 항목 **디바이스 설정** 페이지에서 **Microsoft Edge**를 선택하세요.  

 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Windows 8.1 및 Windows 10 디바이스에 대한 구성 항목을 만드는 방법](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)을 참조하세요.  

### <a name="compliance-settings-for-windows-10-team-devices"></a>Windows 10 Team 디바이스에 대한 준수 설정  
 이러한 새 준수 설정을 사용하여 Surface Hub 디바이스와 같이 Windows 10 Team이 실행되는 디바이스를 구성합니다.  

 새 설정을 보려면 **구성 항목 만들기** 마법사의 구성 항목 **디바이스 설정** 페이지에서 **Windows 10 Team**을 선택하세요.  

 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Windows 8.1 및 Windows 10 디바이스에 대한 구성 항목을 만드는 방법](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)을 참조하세요.  

### <a name="android---kiosk-mode-for-samsung-knox-standardbr-hybrid"></a>Android - Samsung KNOX Standard용 키오스크 모드<br />하이브리드  
 키오스크 모드에서는 디바이스를 잠가 특정 기능만 작동하도록 허용할 수 있습니다. 예를 들어, 디바이스에서 지정된 관리되는 앱만 실행할 수 있게 하거나 디바이스에서 볼륨 단추를 사용되지 않도록 설정할 수 있습니다. 이러한 설정은 POS 디바이스와 같이 한 가지 기능만 수행하도록 지정된 디바이스 또는 디바이스의 데모 모델에 사용할 수 있습니다. 이러한 설정을 Samsung KNOX Standard 디바이스의 **Windows 8.1 및 Windows 10** 구성 항목에서는 사용할 수 없습니다(해당 설정이 Windows 10 디바이스에만 적용됨).  

 새 설정을 보려면 **구성 항목 만들기** 마법사의 구성 항목 **디바이스 설정** 페이지에서 **키오스크 모드 - Samsung KNOX**를 선택하세요.  

 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Windows 8.1 및 Windows 10 디바이스에 대한 구성 항목을 만드는 방법](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)을 참조하세요.  
