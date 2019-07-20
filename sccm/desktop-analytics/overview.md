---
title: Desktop Analytics
titleSuffix: Configuration Manager
description: Configuration Manager와 통합 된 데스크톱 분석 서비스에 대 한 개요입니다.
ms.date: 07/19/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: overview
ms.assetid: 38b2bed2-20dd-4ce1-abc0-219343d2c4b8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 154c142b285c58da714193c964b353dc1e173481
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68339267"
---
# <a name="what-is-desktop-analytics"></a>데스크톱 분석 이란?

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석은 Configuration Manager와 통합 되는 클라우드 기반 서비스입니다. 이 서비스는 Windows 클라이언트의 업데이트 준비에 대 한 더 많은 의사 결정을 내릴 수 있는 통찰력 및 인텔리전스를 제공 합니다. Microsoft 클라우드 서비스에 연결 된 수백만 대의 장치에서 집계 된 데이터를 조직의 데이터와 결합 합니다.

Configuration Manager에서 데스크톱 분석을 사용 하 여 다음을 수행 합니다.  

- 조직에서 실행 중인 앱의 인벤토리 만들기  

- 최신 Windows 10 기능 업데이트를 사용 하 여 앱 호환성 평가  

- 호환성 문제를 확인 하 고 클라우드 사용 데이터 통찰력을 기반으로 완화 제안 받기  

- 최소 장치 집합에서 전체 응용 프로그램 및 드라이버 공간을 나타내는 파일럿 그룹 만들기  

- 파일럿 및 프로덕션 관리 장치에 Windows 10 배포  

![Azure Portal 데스크톱 분석 홈 페이지의 스크린샷](media/portal-home.png)

> [!Note]  
> Desktop Analytics는 Windows Analytics의 후속 작업입니다. *Windows Analytics* 서비스는 업그레이드 준비, 업데이트 준수 및 장치 상태를 포함 합니다.
>
> 이러한 모든 기능은 *데스크톱 분석* 서비스에 결합 됩니다. 데스크톱 분석도 Configuration Manager와 긴밀 하 게 통합 됩니다.



## <a name="benefits"></a>이점

대부분의 고객은 Windows 10을 사용 하 여 최신 상태를 유지 하는 데 문제가 있습니다. 주요 과제는 응용 프로그램을 테스트 하는 것입니다. 이 프로세스는 일반적으로 수동입니다. IT 관리자와 응용 프로그램 소유자가 기존 응용 프로그램을 지속적으로 분석 하는 데는 많은 시간이 소요 됩니다. 그런 다음 발생 하는 모든 문제를 수정 합니다.

데스크톱 분석은 다음과 같은 이점을 제공 합니다.

- **장치 및 소프트웨어 인벤토리**: 앱 및 Windows 버전 등의 주요 요소에 대 한 인벤토리  

- **파일럿 식별**: 가장 광범위 한 요소를 제공 하는 가장 작은 장치 집합의 id입니다. Windows 업그레이드 및 업데이트의 파일럿에 가장 중요 한 요소를 중점적으로 설명 합니다. 파일럿이 더 성공 하도록 하면 프로덕션 환경에서 광범위 하 게 배포할 수 있습니다.  

- **문제 식별**: 서비스는 사용자 환경의 데이터와 함께 집계 된 시장 데이터를 사용 하 여 Windows에 대 한 최신 상태를 유지 하 고 유지 하는 잠재적인 문제를 예측 합니다. 그런 다음 잠재적 완화를 제안 합니다.  

- **Configuration Manager 통합**: 서비스 클라우드-기존 온-프레미스 인프라를 사용 하도록 설정 합니다. 이 데이터 및 분석을 사용 하 여 장치에서 Windows를 배포 하 고 관리 합니다.  



## <a name="prerequisites"></a>필수 구성 요소

데스크톱 분석을 사용 하려면 사용자 환경이 다음과 같은 필수 구성 요소를 충족 하는지 확인 합니다.


### <a name="technical"></a>기술

- [전역 관리자](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator) 권한이 있는 활성 Azure 구독 [Microsoft 계정은](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts) 지원 되지 않습니다.  

    > [!Important]  
    > 데스크톱 분석은 현재 Office 365 서비스로 제공 되며, Azure AD 테 넌 트에서 Office 365 구독이 필요 합니다. 이는 나중에 필요 하지 않을 수 있습니다.

    - 작업 영역 **소유자** 또는 **참가자** 권한으로 **작업 영역을 설정**하 고 다음 역할을 수행 합니다.  

      - [**데스크톱 분석 관리자**](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) 역할.

      - 리소스 그룹에 대 한 참가자 및 [**사용자 액세스 관리자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) [**Log Analytics**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#log-analytics-contributor) 기존 작업 영역을 사용 하거나 기존 리소스 그룹에서 새 작업 영역을 만들 수 있습니다.

      - 구독에 대 한 [**소유자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner)또는 [**참가자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) 및 [**사용자 액세스 관리자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) 권한으로 새 리소스 그룹에 작업 영역을 만들 수 있습니다.  

- Configuration Manager 업데이트 롤업 (4500571) 이상 버전 1902. 자세한 내용은 [Update Configuration Manager](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)를 참조 하세요.  

    - Configuration Manager의 **전체 관리자** 역할  

    > [!Note]  
    > 데스크톱 분석은 Azure Active Directory (Azure AD) 테 넌 트 및 Configuration Manager 계층 별로 하나의 상용 ID를 지원 합니다. 환경에 여러 계층이 있는 경우 다른 상업적 Id와 Azure AD 테 넌 트를 사용 합니다.<!-- 4958160 -->

- Windows 7, Windows 8.1 또는 Windows 10을 실행 하는 장치  

    - 최신 업데이트를 설치 합니다. 자세한 내용은 [업데이트 장치](/sccm/desktop-analytics/enroll-devices#update-devices)를 참조 하세요.  

    - 또한 장치에는 Configuration Manager 클라이언트, 1902 버전의 업데이트 롤업 (4500571) 이상이 있어야 합니다. 자세한 내용은 [Update Configuration Manager](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)를 참조 하세요.  

    > [!Note]  
    > 데스크톱 분석에서는 Windows 10 LTSC (장기 서비스 채널)로의 업그레이드를 지원 하지 않습니다. 자세한 내용은 [Windows as a service 개요](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)를 참조 하세요.
    >
    > 데스크톱 분석은 현재 위치의 업그레이드 시나리오를 가장 잘 지원 하도록 설계 되었습니다. 32 비트에서 64 비트 아키텍처로와 같이 주요 변경 작업을 수행 해야 하는 경우에는 이미징 시나리오를 사용 합니다. 데스크톱 분석 정보는 이러한 클래식 OS 배포 시나리오에서 여전히 중요 하지만 현재 위치의 업그레이드 관련 지침을 무시할 수 있습니다. 자세한 내용은 [Configuration Manager를 사용 하 여 엔터프라이즈 운영 체제를 배포 하는 시나리오](/sccm/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems)를 참조 하십시오.

- Windows 진단 데이터입니다. 자세한 내용은 다음 문서를 참조하세요.  

    - [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)  

    - [데스크톱 분석 개인 정보](/sccm/desktop-analytics/privacy)  

- 장치에서 Microsoft 공용 클라우드로의 네트워크 연결. 자세한 내용은 [데이터 공유를 사용 하도록 설정 하는 방법](/sccm/desktop-analytics/enable-data-sharing) 을 참조 하세요.  


### <a name="licensing"></a>라이선싱

데스크톱 분석에는 다음 라이선스 구독 중 하나가 필요 합니다.

- Windows 10 Enterprise E3 또는 E5; 또는 Microsoft 365 F1, E3 또는 E5  

- Windows 10 교육 A3 또는 A5 또는 Microsoft 365 A3 또는 A5  

- Windows VDA E3 또는 E5  




## <a name="next-steps"></a>다음 단계

다음 자습서에서는 데스크톱 분석 및 Configuration Manager를 시작 하는 단계별 가이드를 제공 합니다.  

- [파일럿에 Windows 10 배포](/sccm/desktop-analytics/tutorial-windows10)  
