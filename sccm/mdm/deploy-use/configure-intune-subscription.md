---
title: Intune 구독 구성
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 Intune 구독 구성
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 99de8fe7-560e-401a-8ab2-6d87d091be17
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ec6756e5c180561bef10bba799e3fdba3dcc303
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289064"
---
# <a name="configure-your-intune-subscription-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune을 사용하여 Intune 구독 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

Intune 구독을 사용하면 인터넷을 통해 디바이스를 관리할 수 있습니다. 여기에는 디바이스를 등록할 수 있는 사용자 컬렉션 지정 및 사용자에게 표시되는 정보 정의가 포함됩니다. Intune 구독을 만드는 동안 회사 로고 및 사용자 지정 색 구성표를 사용하여 Intune 회사 포털에 회사 브랜딩을 추가할 수도 있습니다.

Intune 구독은 다음을 수행합니다.

-   서비스 연결 지점이 Intue 서비스에 연결하는 데 필요한 인증서 검색
-   사용자가 모바일 디바이스를 등록할 수 있는 사용자 컬렉션 정의
-   지원할 모바일 플랫폼 정의 및 구성

> [!IMPORTANT]
>  Configuration Manager에서 Microsoft Intune에 대한 구독을 만들면 사이트의 서비스 연결 지점이 "온라인 모드"가 됩니다. [System Center Configuration Manager의 서비스 연결 지점 정보](../../core/servers/deploy/configure/about-the-service-connection-point.md)를 참조하세요.

## <a name="to-create-the-microsoft-intune-subscription"></a>Microsoft Intune 구독을 만들려면

1.  아직 그렇게 하지 않은 경우 [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216)에서 Microsoft Intune 계정을 등록합니다.  Intune 계정을 만든 후에는 Intune 계정에 사용자를 추가하거나 추가 설정 구성을 수행할 필요가 없습니다.

2.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

3.  **관리** 작업 영역에서 **클라우드 서비스**를 확장하고 **Microsoft Intune 구독**을 클릭합니다. **홈** 탭에서 **Microsoft Intune 구독 추가**를 클릭합니다.

![Intune 구독 만들기](../media/mdm-set-intune.png)

4. Microsoft Intune 구독 만들기 마법사의 **소개** 페이지에서 텍스트를 검토하고 **다음**을 클릭합니다.

5. **구독** 페이지에서 **로그인** 을 클릭하고 회사 또는 학교 계정을 사용하여 로그인합니다. **모바일 디바이스 관리 기관 설정** 대화 상자에서 Configuration Manager 콘솔을 통해 Configuration Manager를 사용하는 방법으로만 모바일 디바이스를 관리하려면 확인란을 선택합니다. 구독을 계속하려면 이 옵션을 선택해야 합니다.

   > [!IMPORTANT]
   >  Configuration Manager를 관리 기관으로 선택하는 경우 Microsoft 지원 서비스에 연락하지 않고, 기존의 관리 디바이스를 등록 취소했다가 다시 등록하지 않고도, Configuration Manager 버전 1610 이상 및 Microsoft Intune 버전 1705에서 관리 기관을 Microsoft Intune으로 변경할 수 있습니다. 자세한 내용은 [MDM 기관 변경](/sccm/mdm/deploy-use/change-mdm-authority)을 참조하세요.

6. 개인 정보 취급 방침 링크를 클릭하여 검토하고 **다음**을 클릭합니다.

7. **일반** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.

   - **컬렉션**: 모바일 장치를 등록할 사용자를 포함 하는 사용자 컬렉션을 지정 합니다.

     > [!NOTE]
     >  사용자가 컬렉션에서 제거될 경우 사용자 데이터베이스에서 사용자 레코드가 제거되면 최대 24시간 동안 사용자 디바이스가 계속 관리됩니다.

   - **회사 이름**: 회사 이름을 지정 합니다.

   - **회사 개인 정보 보호 설명서 URL**: 예를 들어 사용자가 회사 포털에서 액세스할 수 있는 링크를 제공 하는 인터넷에서 액세스할 수 있는 링크에 회사 개인 정보를 게시 하는 경우 http://www.contoso.com/CP_privacy.html합니다. 개인 정보 취급 방침 정보에는 사용자가 회사와 공유할 수 있는 정보가 명시될 수 있습니다.

   - **회사 포털에 대 한 색 구성표**: 필요에 따라 회사 포털에 대 한 파란색의 기본 색을 변경 합니다.

   - **Configuration Manager 사이트 코드**: 모바일 장치를 관리할 기본 사이트의 사이트 코드를 지정 합니다.

   > [!NOTE]
   >  사이트 코드를 변경하면 새 등록만 영향을 받으며 기존에 등록된 디바이스는 영향을 받지 않습니다.

8. **회사 연락처 정보** 페이지에서 회사 포털 앱의 **IT 문의** 아래에 표시되는 회사 연락처 정보를 지정합니다. 회사에 대한 연락처 정보를 제공하고 **다음**을 클릭합니다.

9. **회사 로고** 페이지에서 회사 포털에 로고를 표시할지 여부를 선택하고 **다음**을 클릭할 수 있습니다.

10. 마법사를 완료합니다.

> [!div class="button"]
> [< 이전 단계](confirm-dns.md)  [다음 단계 >](terms-and-conditions.md)
