---
title: Desktop Analytics
titleSuffix: Configuration Manager
description: Configuration Manager와 통합된 Desktop Analytics 서비스의 개요입니다.
ms.date: 10/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: overview
ms.assetid: 38b2bed2-20dd-4ce1-abc0-219343d2c4b8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76fa92c93a290c49c286be3bb1368dfdf8347ef3
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72384981"
---
# <a name="what-is-desktop-analytics"></a>Desktop Analytics란?

Desktop Analytics는 Configuration Manager와 통합되는 클라우드 기반 서비스입니다. 서비스는 Windows 클라이언트의 업데이트 준비 사항에 대해 충분한 정보를 파악한 후 결정하도록 인사이트와 인텔리전스를 제공합니다. Microsoft 클라우드 서비스에 연결된 수백만 대의 디바이스에서 집계된 데이터를 조직의 데이터와 결합합니다.

Configuration Manager에서 Desktop Analytics를 사용하여 다음을 수행합니다.  

- 조직에서 실행 중인 앱의 인벤토리 만들기  

- 최신 Windows 10 기능 업데이트를 사용하여 앱 호환성 평가  

- 호환성 문제를 확인하고 클라우드 사용 데이터 인사이트를 기반으로 완화 제안 받기  

- 최소 디바이스 세트에서 전체 애플리케이션 및 드라이버 공간을 나타내는 파일럿 그룹 만들기  

- 파일럿 및 프로덕션 관리 디바이스에 Windows 10 배포  

![Azure Portal에서 Desktop Analytics 홈 페이지의 스크린샷](media/portal-home.png)

> [!Note]  
> Desktop Analytics는 Windows Analytics의 후속 작업입니다. *Windows Analytics* 서비스에는 업그레이드 준비, 업데이트 준수 및 디바이스 상태가 포함되어 있습니다.
>
> 이러한 모든 기능은 *Desktop Analytics* 서비스에 결합됩니다. 또한 Desktop Analytics는 Configuration Manager와 더욱 긴밀하게 통합되어 있습니다.



## <a name="benefits"></a>이점

대부분의 고객은 Windows 10을 사용하여 현재 상태를 유지하는 데 어려움이 있습니다. 주요 과제는 애플리케이션을 테스트하는 것입니다. 이 프로세스는 일반적으로 수동입니다. IT 관리자와 애플리케이션 소유자가 기존 애플리케이션을 지속적으로 분석하는 데는 많은 시간이 소요됩니다. 그런 다음, 발생하는 모든 문제를 수정합니다.

Desktop Analytics는 다음과 같은 이점을 제공합니다.

- **디바이스 및 소프트웨어 인벤토리**: 앱 및 Windows 버전 등의 주요 요소에 대한 인벤토리  

- **파일럿 식별**: 가장 광범위한 요소를 제공하는 가장 작은 디바이스 세트의 식별입니다. Windows 업그레이드 및 업데이트의 파일럿에 가장 중요한 요소에 중점을 둡니다. 파일럿이 더 성공하도록 하면 프로덕션 환경에서 더 빠르고 자신 있게 광범위하게 배포할 수 있습니다.  

- **문제 식별**: 서비스는 사용자 환경의 데이터와 함께 집계된 시장 데이터를 사용하여 Windows에 대한 현재 상태를 유지하는 데 잠재적인 문제를 예측합니다. 그런 다음, 잠재적 완화를 제안합니다.  

- **Configuration Manager 통합**: 서비스 클라우드는 기존 온-프레미스 인프라를 활성화합니다. 이 데이터 및 분석을 사용하여 디바이스에서 Windows를 배포하고 관리합니다.  



## <a name="prerequisites"></a>필수 구성 요소

Desktop Analytics를 사용하려면 사용자 환경이 다음과 같은 필수 구성 요소를 충족하는지 확인합니다.


### <a name="technical"></a>기술

- [글로벌 관리자](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#company-administrator-permissions) 사용 권한이 있는 활성 Azure 구독 [Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts)은 지원되지 않습니다.  

    > [!Important]  
    > Desktop Analytics에서는 현재 Azure AD 테넌트에 Office 365 서비스를 배포해야 합니다. 이는 나중에 필요하지 않습니다.

    - **작업 영역을 설정**하는 **작업 영역 소유자** 또는 **기여자** 및 다음 역할:  

      - [**Desktop Analytics 관리자**](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) 역할

      - 기존 리소스 그룹에서 기존 작업 영역을 사용하거나 새 작업 영역을 만드는 리소스 그룹의 [**Log Analytics 기여자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#log-analytics-contributor) 및 [**사용자 액세스 관리자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator)

      - 새 리소스 그룹에서 작업 영역을 만드는 구독의 [**소유자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) 또는 [**기여자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) 및 [**사용자 액세스 관리자**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) 권한  

- Configuration Manager, 버전 1902, 업데이트 롤업(4500571) 이상 자세한 내용은 [Configuration Manager 업데이트](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)를 참조하세요.  

    - Configuration Manager에서 [**전체 관리자**](/sccm/core/understand/fundamentals-of-role-based-administration#bkmk_Planroles) 역할  

    > [!Note]  
    > Desktop Analytics는 Azure AD(Azure Active Directory) 테넌트 및 Configuration Manager 계층별로 하나의 상업용 ID를 지원합니다. 환경에 여러 계층이 있는 경우 다른 상업적 ID와 Azure AD 테넌트를 사용합니다.<!-- 4958160 -->

- Windows 7, Windows 8.1 또는 Windows 10을 실행하는 디바이스  

    - 최신 업데이트를 설치합니다. 자세한 내용은 [디바이스 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)를 참조하세요.  

    - 또한 디바이스에는 Configuration Manager 클라이언트, 1902 버전의 업데이트 롤업(4500571) 이상이 있어야 합니다. 자세한 내용은 [Configuration Manager 업데이트](/sccm/desktop-analytics/connect-configmgr#bkmk_hotfix)를 참조하세요.  

    > [!Note]  
    > Desktop Analytics에서는 Windows 10 LTSC(장기 서비스 채널)로의 업그레이드를 지원하지 않습니다. 자세한 내용은 [Windows as a Service 개요](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)를 참조하세요.
    >
    > Desktop Analytics는 현재 위치 업그레이드 시나리오를 가장 잘 지원하도록 설계되었습니다. 32비트에서 64비트 아키텍처로와 같이 주요 변경 작업을 수행해야 하는 경우에는 이미징 시나리오를 사용합니다. Desktop Analytics 인사이트는 이러한 클래식 OS 배포 시나리오에서 여전히 중요하지만 현재 위치 업그레이드 관련 지침을 무시할 수 있습니다. 자세한 내용은 [Configuration Manager를 사용하여 엔터프라이즈 운영 체제를 배포하는 여러 시나리오](/sccm/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems)를 참조하세요.

- Windows 진단 데이터 자세한 내용은 다음 아티클을 참조하세요.  

    - [진단 데이터 수준](/sccm/desktop-analytics/enable-data-sharing#diagnostic-data-levels)  

    - [Desktop Analytics 개인 정보](/sccm/desktop-analytics/privacy)  

- 디바이스에서 Microsoft 퍼블릭 클라우드로의 네트워크 연결 자세한 내용은 [데이터 공유를 사용하도록 설정하는 방법](/sccm/desktop-analytics/enable-data-sharing)을 참조하세요.  

> [!Important]   
> Microsoft는 사용자의 개인 정보에 대한 제어를 제공하는 도구와 리소스를 제공하기 위해 노력하고 있습니다. 따라서 Microsoft는 유럽 국가(EEA 및 스위스)에 있는 디바이스에서 다음 데이터를 수집하지 않습니다.
>
> - Windows 8.1 디바이스의 Windows 진단 데이터
> - Windows 7용 앱 사용량 현황 데이터

### <a name="licensing-and-costs"></a>라이선스 및 비용

Desktop Analytics에 등록된 디바이스는 사용이 허가된 사용자만 사용할 수 있습니다.

- Windows 10 Enterprise E3 또는 E5(Microsoft 365 F1, E3 또는 E5에 포함됨)

- Windows 10 Education A3 또는 A5(Microsoft 365 A3 또는 A5에 포함됨)

- Windows Virtual Desktop Access E3 또는 E5  

라이선스 구독 비용 외에도 Desktop Analytics 사용에 대한 추가 비용은 없습니다. Azure Log Analytics 내에서 Desktop Analytics는 "등급 0"입니다. 이 등급은 선택한 Azure Log Analytics 가격 책정 계층에 관계 없이 데이터 제한과 비용에서 제외된 것을 의미합니다. Azure Log Analytics 가격 책정 계층에 대한 자세한 내용은 [가격 책정 - Log Analytics](https://azure.microsoft.com/pricing/details/monitor/)를 참조하세요.

- 하루에 수집되는 데이터의 양에 대한 한도가 있는 무료 계층을 사용하는 경우 Desktop Analytics 데이터는 이 한도에 포함되지 않습니다. 디바이스에서 모든 Desktop Analytics 데이터를 수집할 수 있으며, 다른 원본에서 추가 데이터를 수집하는 데 사용할 수 있는 전체 한도가 있습니다.

- 수집된 데이터의 GB당 요금이 청구되는 유료 계층을 사용하는 경우 Desktop Analytics 데이터에 대해 요금이 청구되지 않습니다. 모든 Desktop Analytics 데이터를 디바이스에서 수집할 수 있으며 비용은 발생하지 않습니다.

> [!Note]  
> Azure Log Analytics 계획마다 데이터 보존 기간이 다릅니다. Desktop Analytics는 작업 영역의 데이터 보존 정책을 상속합니다. 작업 영역이 무료 요금제인 경우 Desktop Analytics는 작업 영역에서 수집된 "일별 스냅샷"의 최근 30일을 유지합니다.


## <a name="next-steps"></a>다음 단계

다음 자습서에서는 Desktop Analytics 및 Configuration Manager를 시작하는 단계별 가이드를 제공합니다.  

- [파일럿에 Windows 10 배포](/sccm/desktop-analytics/tutorial-windows10)  
