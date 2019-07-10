---
title: Desktop Analytics
titleSuffix: Configuration Manager
description: 데스크톱 분석 서비스의 개요를 Configuration Manager를 통합 합니다.
ms.date: 06/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: overview
ms.assetid: 38b2bed2-20dd-4ce1-abc0-219343d2c4b8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43a5e1a4bf3283c185d612cc31428a23a4e12061
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67678109"
---
# <a name="what-is-desktop-analytics"></a>데스크톱 Analytics 란?

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 Analytics는 Configuration Manager와 통합 하는 클라우드 기반 서비스입니다. 서비스는 통찰력 및 인텔리전스 Windows 클라이언트의 업데이트 준비 상태에 대 한 더 합리적인된 결정을 내릴 수를 제공 합니다. 수백만 대의 Microsoft 클라우드 서비스에 연결 하는 장치에서 집계 된 데이터를 사용 하 여 조직에서 데이터를 결합 합니다.

데스크톱 분석을 Configuration Manager를 사용 합니다.  

- 조직에서 실행 되는 앱의 인벤토리 생성  

- 최신 Windows 10 기능 업데이트를 사용 하 여 응용 프로그램 호환성 평가  

- 호환성 문제를 식별 하 고 클라우드 기반의 데이터 정보에 따라 완화 제안 받기  

- 최소한의 장치에서 전체 응용 프로그램 및 드라이버 부동산 나타내는 파일럿 그룹 만들기  

- 파일럿 및 프로덕션 환경에서 관리 하는 장치에 Windows 10을 배포 합니다.  

![Azure portal에서 데스크톱 분석 홈 페이지의 스크린샷](media/portal-home.png)

> [!Note]  
> 데스크톱 Analytics는 Windows Analytics의 후속입니다. 합니다 *Windows Analytics* 업그레이드 준비, 업데이트 준수 및 장치 상태 서비스에 포함 됩니다.
>
> 이러한 기능을 모두 결합 되는 *데스크톱 분석* 서비스입니다. 또한 데스크톱 분석 Configuration Manager와 더 밀접 하 게 통합 되어 있습니다.



## <a name="benefits"></a>이점

많은 고객 들을 가져오고 Windows 10을 사용 하 여 현재 상태 유지를 사용 하 여 문제를 해결 합니다. 주요 과제는 응용 프로그램을 테스트 합니다. 이 프로세스는 일반적으로 수동. IT 관리자 및 응용 프로그램 소유자가 지속적으로 기존 응용 프로그램을 분석 하려면 시간이 오래 걸리는 경우 발생 하는 모든 문제를 해결 합니다.

데스크톱 분석에는 다음과 같은 이점을 제공합니다.

- **장치 및 소프트웨어 인벤토리**: 버전의 Windows 앱 등 주요 요인의 인벤토리를 제공 합니다.  

- **식별을 파일럿 실행**: 가장 작은 요소 중 가장 넓은 범위를 제공 하는 장치 집합의 id입니다. Windows 업그레이드 및 업데이트의 파일럿을 가장 중요 한 요소에 중점을 둡니다. 더 성공적인 파일럿이 있도록 더 빠르고 자신 있게 프로덕션 환경에서 광범위 한 배포를 진행할 수 있습니다.  

- **문제 식별**: 환경에서 데이터와 함께 집계 된 시장 데이터를 사용 하는 서비스 예측 가능성을 가져오고 Windows를 사용 하 여 현재 상태 유지를 발급 합니다. 잠재적인 완화 방법을 제안합니다.  

- **Configuration Manager 통합**: 서비스를 기존 온-프레미스 인프라에 클라우드를 사용합니다. 이 데이터 및 분석을 사용 하 여 배포 하 고 Windows 장치에서 관리 합니다.  



## <a name="prerequisites"></a>필수 구성 요소

데스크톱 Analytics를 사용 하려면 사용자 환경에는 다음 필수 조건을 충족 해야 합니다.


### <a name="technical"></a>기술

- 활성 Azure 구독을 사용 하 여 [전역 관리자](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator) 권한  

    - **작업 영역 소유자** 나 **참가자** 권한을 **작업 영역 설정**, 및 다음 역할:  

      - [**데스크톱 분석 관리자** ](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) 역할입니다.

      - [**Analytics 참가자 기록** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#log-analytics-contributor) 하 고 [ **사용자 액세스 관리자** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) 기존 리소스 그룹에 새 작업 영역을 만들거나 기존 작업 영역을 사용 하 여 리소스 그룹.

      - [**소유자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner), 또는 [ **참가자** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) 고 [ **사용자 액세스 관리자** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) 에 대 한 권한을 합니다 새 리소스 그룹에 작업 영역을 만들 구독입니다.  

- 1902 버전의 configuration Manager 업데이트 롤업 (4500571) 이상. 자세한 내용은 [Configuration Manager 업데이트](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)합니다.  

    - **전체 관리자** Configuration Manager의 역할  

- Windows 7, Windows 8.1 또는 Windows 10을 실행 하는 장치  

    - 최신 업데이트를 설치 합니다. 자세한 내용은 [장치 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)합니다.  

    - 장치는 Configuration Manager 클라이언트를 버전 1902 있어야 할 수도 업데이트 롤업 (4500571) 이상. 자세한 내용은 [Configuration Manager 업데이트](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)합니다.  

    > [!Note]  
    > 데스크톱 Analytics는 Windows 10 장기 서비스 채널 (LTSC)에 대 한 업그레이드를 지원 하지 않습니다. 자세한 내용은 [Windows 서비스에 대 한 개요로](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)합니다.
    >
    > 데스크톱 분석 지원 내부에서 업그레이드 시나리오를 가장 하도록 설계 되었습니다. 32 비트에서 64 비트 아키텍처에서와 같은 주요 변경 내용을 확인 해야 하는 경우에 이미징 시나리오를 사용 합니다. 데스크톱 분석 정보는 이러한 클래식 운영 체제 배포 시나리오에서 여전히 중요 하지만 현재 위치 업그레이드 특정 지침은 무시할 수 있습니다. 자세한 내용은 [Configuration Manager를 사용 하 여 엔터프라이즈 운영 체제를 배포 하는 시나리오](/sccm/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems)합니다.

- Windows 진단 데이터입니다. 자세한 내용은 다음 아티클을 참조하세요.  

    - [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)  

    - [데스크톱 분석 개인 정보](/sccm/desktop-analytics/privacy)  

- 네트워크 장치에서 Microsoft 공용 클라우드를 연결 합니다. 자세한 내용은 참조 하세요. [데이터 공유를 사용 하는 방법](/sccm/desktop-analytics/enable-data-sharing)  


### <a name="licensing"></a>라이선스

데스크톱 분석 다음 라이선스 구독 중 하나가 필요합니다.

- Windows 10 Enterprise E3 또는 E5; Microsoft 365 F1, E3 또는 E5  

- Windows 10 Education A3 또는 A5; Microsoft 365 A3 또는 A5  

- Windows VDA E3 또는 E5  




## <a name="next-steps"></a>다음 단계

다음 자습서는 데스크톱 분석 및 Configuration Manager를 사용 하 여 시작 하는 단계별 가이드를 제공 합니다.  

- [파일럿에 Windows 10 배포](/sccm/desktop-analytics/tutorial-windows10)  
