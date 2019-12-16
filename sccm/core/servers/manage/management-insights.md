---
title: 관리 정보
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔에서 지원되는 관리 정보 기능에 대해 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a79f83be-884c-48e6-94d6-ed0a68c22e2f
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 813c8afd46927ddb5b3d3cc621c900ed8e0516d3
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74661263"
---
# <a name="management-insights-in-configuration-manager"></a>Configuration Manager의 관리 인사이트

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 관리 정보는 환경의 현재 상태에 대한 정보를 제공합니다. 이 정보는 사이트 데이터베이스의 데이터 분석을 기반으로 합니다. 이 정보를 통해 환경을 더 잘 이해하고 해당 정보에 기반한 조치를 취할 수 있습니다. <!--1353967-->

## <a name="review-management-insights"></a>관리 정보 검토

규칙을 보려면 계정에 **사이트** 개체에 대한 **읽기** 권한이 필요합니다.

1. Configuration Manager 콘솔을 엽니다.  

2. **관리** 작업 영역으로 이동하여 **관리 인사이트**를 확장하고 **모든 인사이트**를 선택합니다.  

    > [!Note]  
    > 1810 버전부터 **관리 인사이트** 노드를 선택하는 경우 [관리 인사이트 대시보드](#bkmk_insights)가 표시됩니다.  

3. 검토하려는 관리 인사이트 그룹 이름을 엽니다. 리본에서 **인사이트 표시**를 선택합니다.  

다음 네 개의 탭을 검토에 사용할 수 있습니다.

- **모든 규칙**: 선택한 관리 정보 그룹에 대한 규칙의 전체 목록을 제공합니다.  

- **완료**:  아무 조치도 필요하지 않은 규칙을 나열합니다.  

- **진행 중**: 모두는 아니지만 일부 필수 구성 요소가 완료되는 규칙을 보여 줍니다.  

- **작업 필요**: 작업을 수행해야 하는 규칙이 나열됩니다. **자세한 세부 내용**을 선택하여 작업이 필요한 특정 항목을 검색합니다.  

**필수 구성 요소** 창에는 규칙을 실행하는 데 필요한 항목이 나열되어 있습니다.

### <a name="all-rules-and-prerequisites-for-the-cloud-services-group"></a>클라우드 서비스 그룹에 대한 모든 규칙 및 필수 구성 요소

![관리 인사이트 - 클라우드 서비스 그룹에 대한 모든 규칙 및 필수 구성 요소](./media/Management-insights-all-cloud-rules.png)

규칙 세부 정보를 보려면 규칙을 선택한 다음, **자세히**를 선택합니다.

## <a name="operations"></a>작업

관리 정보 규칙은 주별 일정에 따라 해당 적용 가능성을 재평가합니다. 필요 시 규칙을 다시 평가하려면 규칙을 마우스 오른쪽 단추로 클릭하고 **다시 평가**를 선택합니다.

관리 인사이트 규칙에 대한 로그 파일은 사이트 서버의 **SMS_DataEngine.log**입니다.

<!--1357930-->
일부 규칙을 통해 작업을 수행할 수 있습니다. 규칙을 선택하고 **자세히**를 선택한 다음, 사용 가능한 경우 **작업 수행**을 선택합니다.

규칙에 따라 이 작업은 다음 동작 중 하나가 있습니다.  

- 콘솔에서 추가 작업을 수행할 수 있는 노드로 자동으로 이동합니다. 예를 들어, 관리 인사이트에서 클라이언트 설정을 변경하도록 권장하는 경우 작업을 수행하면 클라이언트 설정 노드로 이동합니다. 그런 다음, 기본값 또는 사용자 지정 클라이언트 설정 개체를 수정하여 추가 작업을 수행합니다.  

- 쿼리를 기반으로 하는 필터링된 보기로 이동합니다. 예를 들어, 빈 컬렉션 규칙에 대한 작업을 수행하면 이러한 컬렉션만 컬렉션 목록에 표시됩니다. 그런 다음, 컬렉션 삭제 또는 멤버 관리 규칙 수정과 같은 추가 작업을 수행합니다.  

## <a name="bkmk_insights"></a> 관리 인사이트 대시보드

<!--1357979-->

1810 버전부터 **관리 인사이트** 노드에 그래픽 대시보드가 포함됩니다. 이 대시보드는 규칙 상태의 개요를 표시하므로 진행 상태를 보다 쉽게 표시할 수 있습니다.

보기를 세분화하려면 대시보드 맨 위에서 다음 필터를 사용합니다.

- 완료된 항목 표시
- 선택 사항
- 권장
- 중요

이 대시보드에는 다음과 같은 타일이 있습니다.  

- **관리 인사이트 인덱스**: 관리 인사이트 규칙에 대한 전반적인 진행 상황을 추적합니다. 인덱스는 가중 평균입니다. 중요 규칙이 가장 유용합니다. 이 인덱스는 선택적 규칙에 가장 작은 가중치를 부여합니다.  

- **관리 인사이트 그룹**: 필터를 적용하여 각 그룹에 있는 규칙의 백분율을 표시합니다. 그룹을 선택하여 이 그룹의 특정 규칙으로 드릴다운할 수 있습니다.  

- **관리 인사이트 우선 순위**: 필터를 적용하여 우선 순위별로 규칙의 백분율을 표시합니다.  

- **모든 인사이트**: 우선 순위 및 상태가 포함된 인사이트 테이블입니다. 테이블의 맨 위에서 **필터** 필드를 사용하여 사용 가능한 열 중 하나의 문자열과 일치시킵니다. 대시보드는 다음 순서 대로 테이블을 정렬합니다.

  - 상태: 작업 필요, 완료, 알 수 없음  
  - 우선 순위: 중요, 권장, 선택 사항  
  - 마지막으로 변경한 날짜: 오래된 날짜 우선  

![관리 인사이트 대시보드 스크린샷](media/1357979-management-insights-dashboard.png)

## <a name="groups-and-rules"></a>그룹 및 규칙

규칙은 다음과 같은 관리 인사이트 그룹으로 구성됩니다.

- [애플리케이션](#applications)  
- [클라우드 서비스](#cloud-services)  
- [컬렉션](#collections)  
- [자동 유지 관리](#proactive-maintenance)  
- [Security](#security)  
- [간소화된 관리](#simplified-management)  
- [소프트웨어 센터](#software-center)  
- [Windows 10](#windows-10)  

### <a name="applications"></a>애플리케이션

애플리케이션 관리에 대한 인사이트

- **배포가 없는 애플리케이션**: 사용자 환경에서 활성 배포가 없는 애플리케이션을 나열합니다. 이 규칙을 통해 사용되지 않는 애플리케이션을 찾고 삭제하여 콘솔에 표시된 애플리케이션 목록을 간소화할 수 있습니다. 자세한 내용은 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.  

### <a name="cloud-services"></a>Cloud Services

많은 클라우드 서비스와 통합하여 디바이스의 최신 관리를 사용하도록 설정합니다.

- **공동 관리 준비 상태 평가**: 공동 관리를 사용하는 데 필요한 단계를 이해할 수 있습니다. 이 규칙에는 필수 구성 요소가 있습니다. 자세한 내용은 [공동 관리 개요](/sccm/comanage/overview)를 참조하세요.  

- **Configuration Manager에서 사용하도록 Azure 서비스 구성**: 이 규칙은 Configuration Manager를 Azure AD에 온보딩하여 클라이언트가 Azure AD를 사용하는 사이트를 인증할 수 있게 해줍니다. 자세한 내용은 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요.  

- **디바이스가 하이브리드 Azure Active Directory에 가입하도록 설정**: Azure AD 가입 디바이스를 통해 디바이스가 조직의 보안 및 규정 준수 표준을 충족하도록 보장하면서 사용자가 해당 도메인 자격 증명을 사용하여 로그인할 수 있습니다. 자세한 내용은 [Azure AD 하이브리드 ID 디자인 고려 사항](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview)을 참조하세요.  

- **클라이언트를 최신 Windows 10 버전으로 업데이트**: Windows 10, 1709 버전 이상은 사용자의 컴퓨팅 환경을 향상시키고 현대화합니다. 자세한 내용은 [Windows as a service 채택에 관한 주요 문서](/sccm/core/understand/configuration-manager-and-windows-as-service#key-articles-about-adopting-windows-as-a-service)를 참조하세요.  

### <a name="collections"></a>컬렉션

컬렉션을 정리하고 다시 구성하여 관리를 간소화하는 데 도움이 되는 인사이트입니다.

- **빈 컬렉션**: 사용자 환경에서 멤버가 없는 컬렉션을 나열합니다. 자세한 내용은 [컬렉션을 관리하는 방법](/sccm/core/clients/manage/collections/manage-collections)을 참조하세요.  

버전 1902부터 컬렉션 관리에 대한 권장 사항이 포함된 새로운 규칙이 제공됩니다.<!--3555752--> 이러한 인사이트를 사용하여 관리를 간소화하고 성능을 개선하세요.

- **쿼리 규칙 및 직접 멤버가 없는 컬렉션**: 계층 구조에서 컬렉션 목록을 단순화하려면 이러한 컬렉션을 삭제합니다.  

- **동일한 재평가 시작 시간이 포함된 컬렉션**: 이러한 컬렉션에는 다른 컬렉션과 동일한 재평가 시간이 있습니다. 서로 충돌하지 않도록 재평가 시간을 수정합니다.  

- **2초 간의 쿼리 시간이 포함된 컬렉션**: 이 컬렉션에 대한 쿼리 규칙을 검토합니다. 컬렉션을 수정하거나 삭제하는 것이 좋습니다.

- 다음 규칙에는 사이트에 불필요한 부하를 발생시킬 수 있는 구성이 포함됩니다. 이러한 컬렉션을 검토한 다음, 삭제하거나 규칙 평가를 사용하지 않도록 설정합니다.  

  - **쿼리 규칙 및 증분 업데이트를 사용하지 않도록 설정된 컬렉션**  

  - **쿼리 규칙이 없고 예약 또는 증분 평가에 대해 사용하도록 설정된 컬렉션**  

  - **쿼리 규칙이 없고 전체 평가 일정이 선택된 컬렉션**  

### <a name="proactive-maintenance"></a>자동 유지 관리

<!--1352184-->
이 그룹의 규칙은 구성 관리자 개체의 유지를 통해 방지할 수 있는 잠재적 구성 문제를 강조 표시합니다.

- **할당된 사이트 시스템이 없는 경계 그룹**: 할당된 사이트 시스템이 없으면 경계 그룹은 사이트 할당에만 사용할 수 있습니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups)을 참조하세요.  

- **멤버가 없는 경계 그룹**: 경계 그룹은 멤버가 없는 경우 사이트 할당이나 콘텐츠 조회에 적용할 수 없습니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups)을 참조하세요.  

- **클라이언트에 콘텐츠를 제공하지 않는 배포 지점**: 지난 30일 동안 클라이언트에 콘텐츠를 제공하지 않은 배포 지점입니다. 이 데이터는 클라이언트의 다운로드 기록 보고서를 기반으로 합니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points)을 참조하세요.  

- **WSUS 정리 사용**: 소프트웨어 업데이트 지점 구성 요소 속성에서 WSUS 정리를 실행하는 옵션을 사용하도록 설정했는지 확인합니다. 이 옵션은 WSUS 성능 향상에 도움이 됩니다. 자세한 내용은 [소프트웨어 업데이트 유지 관리](/sccm/sum/deploy-use/software-updates-maintenance)를 참조하세요.  

- **사용되지 않는 부팅 이미지**: PXE 부팅 또는 작업 순서 사용에서 참조되지 않는 부팅 이미지입니다. 자세한 내용은 [부팅 이미지 관리](/sccm/osd/get-started/manage-boot-images)를 참조하세요.  

- **사용되지 않는 구성 항목**: 구성 기준에 속하지 않고 30일보다 오래된 구성 항목입니다. 자세한 내용은 [Create configuration baselines](/sccm/compliance/deploy-use/create-configuration-baselines)(구성 기준 만들기)를 참조하세요.  

- **피어 캐시 원본을 최신 버전의 구성 관리자 클라이언트로 업그레이드**: 피어 캐시 원본으로 사용되지만 1806 이전 클라이언트 버전에서 업그레이드하지 않은 클라이언트를 식별합니다. 1806 이전 클라이언트는 1806 이상 버전을 실행하는 클라이언트의 피어 캐시 원본으로 사용될 수 없습니다. **작업 수행**을 선택하여 클라이언트 목록을 표시하는 디바이스 보기를 엽니다.<!--1358008-->  

### <a name="security"></a>보안

인프라 및 디바이스의 보안 향상에 대한 인사이트입니다.

- **NTLM 대체 사용**이 포함되어 있습니다.<!--4572953--> 버전 1906부터 새 규칙은 사이트에 보안 수준이 낮은 NTLM 인증 대체 방법이 사용되는지 탐지합니다. Configuration Manager 클라이언트를 설치하는 클라이언트 푸시 방법을 사용할 때 사이트에서 Kerberos 상호 인증을 요구할 수 있습니다. 이 개선 사항은 서버와 클라이언트 간의 통신을 보안하는 데 도움이 됩니다. 자세한 내용은 [클라이언트 푸시를 사용하여 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)을 참조하세요.

- **지원되지 않는 맬웨어 방지 클라이언트 버전**: 클라이언트의 10% 초과가 지원되지 않는 System Center Endpoint Protection의 버전을 실행합니다. 자세한 내용은 [Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.  

### <a name="simplified-management"></a>간소화된 관리

사용자 환경의 일상적인 관리를 간소화하는 데 도움이 되는 인사이트입니다.

- **Configuration Manager 업데이트를 위해 사이트를 Microsoft 클라우드에 연결**: 이 규칙은 Configuration Manager 서비스 연결 지점이 지난 7일 이내에 Microsoft 클라우드에 연결되었는지 확인합니다. 이 연결은 정기 업데이트를 위한 콘텐츠를 다운로드하기 위한 것입니다. DMPDownloader.log 및 hman.log를 검토합니다. 자세한 내용은 [Internet access requirements](/sccm/core/plan-design/network/internet-endpoints#bkmk_scp-updates)(인터넷 액세스 요구 사항)를 참조하세요.

- **비 CB 클라이언트 버전**: 현재 분기(CB) 빌드가 아닌 버전을 포함한 모든 클라이언트를 나열합니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients)를 참조하세요.  

- **클라이언트를 지원되는 Windows 10 버전으로 업데이트**: 버전 1902부터, 이 규칙을 실행하면 더 이상 지원되지 않는 Windows 10 버전을 실행하는 클라이언트가 보고됩니다. 서비스 종료일이 임박한(3개월 이내) Windows 10 버전을 사용하는 클라이언트도 보고됩니다.<!--3897268-->  

### <a name="software-center"></a>소프트웨어 센터

소프트웨어 센터 관리에 대한 인사이트입니다.

- **사용자를 애플리케이션 카탈로그 대신 소프트웨어 센터로 직접 연결**: 사용자가 지난 14일 동안 애플리케이션 카탈로그의 애플리케이션을 설치했거나 요청했는지를 확인합니다. 애플리케이션 카탈로그의 기본 기능이 이제는 소프트웨어 센터에 포함됩니다. 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다. 자세한 내용은 [사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures#deprecated-features)을 참조하세요.  

- **새 버전의 Software Center 사용**: 이전 버전의 소프트웨어 센터는 더 이상 지원되지 않습니다. 클라이언트 설정인 **컴퓨터 에이전트** 그룹에 **새 소프트웨어 센터 사용**을 활성화하여 새로운 소프트웨어 센터를 사용하도록 클라이언트를 설정합니다. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#use-new-software-center)를 참조하세요.  

### <a name="software-updates"></a>소프트웨어 업데이트

- **클라이언트 설정이 클라이언트에서 델타 콘텐츠를 다운로드할 수 있도록 구성되어 있지 않습니다.** 사용자 환경에서 동기화되는 일부 소프트웨어 업데이트에 델타 콘텐츠가 포함되어 있습니다. 클라이언트 설정, **클라이언트가 사용 가능한 경우 델타 콘텐츠를 다운할 수 있도록 허용**을 사용하도록 설정합니다. 이 설정을 사용하도록 설정하지 않을 경우 이러한 업데이트를 배포할 때 클라이언트가 필요한 것보다 더 많은 콘텐츠를 불필요하게 다운로드합니다. 자세한 내용은 [클라이언트 설정 - 소프트웨어 업데이트](/sccm/core/clients/deploy/about-client-settings#software-updates)를 참조하세요.

- **소프트웨어 업데이트 제품 범주 ‘Windows 10 버전 1903 이상’ 사용**: Windows 10 버전 1903 이상에 대한 새 소프트웨어 업데이트 제품 범주가 있습니다. Windows 10 업데이트를 동기화하고 Windows 10 버전 1903 이상 클라이언트가 있는 경우 소프트웨어 업데이트 지점 구성 요소 속성에서 **Windows 10, 버전 1903 이상** 제품 범주를 선택합니다. 자세한 내용은 [동기화할 분류 및 제품 구성](/sccm/sum/get-started/configure-classifications-and-products)을 참조하세요.

### <a name="windows-10"></a>Windows 10

Windows 10의 배포 및 서비스와 관련된 정보입니다. Windows 10 관리 정보 그룹은 Windows 7, Windows 8 또는 Windows 8.1을 실행하는 클라이언트의 절반을 초과하는 경우에만 지원됩니다.

- **Windows 원격 분석 및 상업용 ID 키 구성**: 업그레이드 준비에서 데이터를 사용하려면 상업용 ID 키로 구성되고 원격 분석을 사용하도록 디바이스를 설정합니다. Windows 10 디바이스를 **강화된(제한된)** 수준 이상으로 설정합니다. 자세한 내용은 [Windows Analytics로 데이터를 보고하도록 클라이언트 구성](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics)을 참조하세요.  

- **Configuration Manager를 업그레이드 준비에 연결**: Windows 7 지원이 중지되기 전에 업그레이드 준비를 활용하여 Windows 10 배포를 신속하게 처리합니다. 자세한 내용은 [업그레이드 준비 통합](/sccm/core/clients/manage/upgrade/upgrade-analytics)을 참조하세요.  

#### <a name="windows-10-management-insights-rules"></a>Windows 10 관리 인사이트 규칙

![관리 인사이트 - Windows 10에 대한 규칙](./media/Windows-10-insights-group.png)
