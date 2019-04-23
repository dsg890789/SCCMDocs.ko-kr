---
title: Desktop Analytics
titleSuffix: Configuration Manager
description: 데스크톱 분석 서비스의 개요를 Configuration Manager를 통합 합니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: overview
ms.assetid: 38b2bed2-20dd-4ce1-abc0-219343d2c4b8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1229dabb0fedf600f7d57a2a400df87906945ba4
ms.sourcegitcommit: d23ccf7b95e6c2a6b156975194ebbc375cb5e6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124423"
---
# <a name="what-is-desktop-analytics"></a>데스크톱 Analytics 란?

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 Analytics는 Configuration Manager와 통합 하는 클라우드 기반 서비스입니다. 서비스는 통찰력 및 인텔리전스를 Windows 및 Office 클라이언트의 업데이트 준비 상태에 대 한 더 합리적인된 결정을 내릴 수를 제공 합니다. 수백만 대의 Microsoft 클라우드 서비스에 연결 하는 장치에서 집계 된 데이터를 사용 하 여 조직에서 데이터를 결합 합니다. 

데스크톱 분석을 Configuration Manager를 사용 합니다.  

- 조직에서 실행 되는 앱의 인벤토리 생성  

- Windows 10 및 Office 365 ProPlus의 최신 기능 업데이트를 사용 하 여 응용 프로그램 호환성 평가  

- 호환성 문제를 식별 하 고 클라우드 기반의 데이터 정보에 따라 완화 제안 받기  

- 최소한의 장치에서 전체 응용 프로그램 및 드라이버 부동산 나타내는 파일럿 그룹 만들기  

- 파일럿 및 프로덕션 환경에서 관리 하는 장치에 Windows 10 및 Office 365 ProPlus 배포  

![Azure portal에서 데스크톱 분석 홈 페이지의 스크린샷](media/portal-home.png)

> [!Note]  
> 데스크톱 Analytics는 Windows Analytics의 후속입니다. 합니다 *Windows Analytics* 업그레이드 준비, 업데이트 준수 및 장치 상태 서비스에 포함 됩니다. 
> 
> 이러한 기능을 모두 결합 되는 *데스크톱 분석* 서비스입니다. 또한 데스크톱 분석 Configuration Manager와 더 밀접 하 게 통합 하 고 Windows 및 Office를 모두 포함 합니다. 



## <a name="benefits"></a>이점

많은 고객 들을 가져오고 Windows 10 및 Office 365 ProPlus를 사용 하 여 현재 상태 유지를 사용 하 여 문제를 해결 합니다. 주요 과제는 응용 프로그램을 테스트 합니다. 이 프로세스는 일반적으로 수동. IT 관리자 및 응용 프로그램 소유자가 지속적으로 기존 응용 프로그램을 분석 하려면 시간이 오래 걸리는 경우 발생 하는 모든 문제를 해결 합니다. 

데스크톱 분석에는 다음과 같은 이점을 제공합니다.

- **장치 및 소프트웨어 인벤토리**: 앱, 추가 기능, 매크로 및 버전의 Office 및 Windows와 같은 주요 요인의 인벤토리를 제공 합니다.  

- **식별을 파일럿 실행**: 가장 작은 요소 중 가장 넓은 범위를 제공 하는 장치 집합의 id입니다. Windows 및 Office를 업그레이드 및 업데이트의 파일럿을 가장 중요 한 요소에 중점을 둡니다. 더 성공적인 파일럿이 있도록 더 빠르고 자신 있게 프로덕션 환경에서 광범위 한 배포를 진행할 수 있습니다.  

- **문제 식별**: 환경에서 데이터와 함께 집계 된 시장 데이터를 사용 하는 서비스 예측 가능성을 가져오고 Windows 및 Office를 사용 하 여 현재 상태 유지를 발급 합니다. 잠재적인 완화 방법을 제안합니다.  

- **Configuration Manager 통합**: 서비스를 기존 온-프레미스 인프라에 클라우드를 사용합니다. 이 데이터 및 분석을 사용 하 여 배포 하 고 장치에서 Windows 및 Office를 관리 합니다.  



## <a name="prerequisites"></a>필수 구성 요소

데스크톱 Analytics를 사용 하려면 사용자 환경에는 다음 필수 조건을 충족 해야 합니다. 


### <a name="technical"></a>기술

- 활성 Azure 구독  
    
    - [**회사 관리자** ](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator) azure에 대 한 사용 권한 **서비스 계약에 동의**를 **구독을 확인 하** 및 **사용자 액세스를 제공 합니다.** 

    - **작업 영역 소유자** 나 **참가자** 권한을 **작업 영역 설정** 및  

        - [**Analytics 참가자 기록** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#log-analytics-contributor) 하 고 [ **사용자 액세스 관리자** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) 기존 리소스 그룹에 새 작업 영역을 만들거나 기존 작업 영역을 사용 하 여 리소스 그룹.

        - [**소유자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner), 또는 [ **참가자** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) 고 [ **사용자 액세스 관리자** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) 에 대 한 권한을 합니다 새 리소스 그룹에 작업 영역을 만들 구독입니다.

- Configuration Manager 1810 업데이트 롤업 4488598 이상 버전. 자세한 내용은 [Configuration Manager 업데이트](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)합니다.  

    - **전체 관리자** Configuration Manager의 역할  

- Windows 7, Windows 8.1 또는 Windows 10을 실행 하는 장치  

    - 최신 업데이트를 설치 합니다. 자세한 내용은 [장치 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)합니다.  

    - 또한 장치는 Configuration Manager 클라이언트를 버전 1810 업데이트 롤업 4486457 이상을 사용 하 여 해야 합니다. 자세한 내용은 [Configuration Manager 업데이트](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)합니다.  

- Windows 진단 데이터입니다. 자세한 내용은 다음 아티클을 참조하세요.  

    - [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)  

    - [데스크톱 분석 개인 정보](/sccm/desktop-analytics/privacy)  

- 네트워크 장치에서 Microsoft 공용 클라우드를 연결 합니다. 자세한 내용은 참조 하세요. [데이터 공유를 사용 하는 방법](/sccm/desktop-analytics/enable-data-sharing)  


### <a name="licensing"></a>라이선스

대부분의 기능은 데스크톱 Analytics에서 모든 추가 라이선스 또는 구독에 필요 하지 않습니다. 올바르게 구성 하는 경우 데스크톱 분석을 사용 하 여 한 Azure 요금이 부과 하지 않습니다. 

Windows 상태 정보에 액세스 하거나 데이터를 내보내려면 추가 라이선스 요구 사항이 있습니다. 다음 구독 중 하나에 없는 경우 계속 설정 하 고 데스크톱 분석을 사용할 수 있지만 Windows 상태 정보를 사용 하거나 데이터를 내보내려면 사용이 허가 되지 않습니다.

- Windows 10 Enterprise 또는 Windows 10 Education: 장치별 활성 Software Assurance를 사용 하 여  

- Windows 10 Enterprise E3 또는 E5: 장치 단위 또는 사용자 단위 구독 (Microsoft 365 F1, E3 또는 E5에 포함)  

- Windows 10 Education A3 또는 A5 (Microsoft 365 Education A3 또는 A5 포함)  

- Windows 가상 데스크톱 액세스 E3 또는 E5: 장치별 사용자 당 구독  

> [!Note]  
> 장치 단위 라이선스에 대 한 라이선스를 사용 하 여 각 장치를 활성화할 필요가 없습니다. 데스크톱 Analytics에 등록 된 장치의 하기만 라이선스가 충분 합니다.  


<!-- 
## Top task
> *Optional*  
> *An effective way to structure your overview article is to create an H2 for the top customer tasks and describe how the product/service helps customers with that task.*  
> *Create a new H2 for each task you list.*  
 -->



## <a name="next-steps"></a>다음 단계

다음 자습서는 데스크톱 분석 및 Configuration Manager를 사용 하 여 시작 하는 단계별 가이드를 제공 합니다.  

- [Office 365를 파일럿 배포](/sccm/desktop-analytics/tutorial-office-365)  

<!-- for future
- [Deploy Windows 10 to a pilot](/sccm/desktop-analytics/tutorial-windows)  
-->
