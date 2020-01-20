---
title: 버전 2012의 변경 내용
titleSuffix: Configuration Manager
description: Configuration Manger 및 System Center 2012 Configuration Manager의 변경 내용과 새로운 기능을 확인합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3ae68fa6-8b30-45dd-9d12-50bb67cb4a9d
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 10fd2507ac89f14764afcb4847b7f41f4a69ee9e
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76034972"
---
# <a name="whats-changed-from-system-center-2012-configuration-manager"></a>System Center 2012 Configuration Manager의 변경된 내용

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 현재 분기에서는 System Center 2012 Configuration Manager의 중요한 변경 내용이 도입되었습니다. 이 문서에서는 중요한 변경 내용과 Configuration Manager 현재 분기의 기존 기준 버전 1511에 도입된 새로운 기능을 확인합니다. Configuration Manager에 대한 최근 업데이트에서 도입된 변경 내용은 [Configuration Manager 증분 버전의 새로운 기능](/sccm/core/plan-design/changes/whats-new-incremental-versions)을 참조하세요.

> [!NOTE]
> 버전 1910부터, Configuration Manager가 Microsoft Endpoint Manager의 일부가 됩니다. 자세한 내용은 [Microsoft Endpoint Configuration Manager](/configmgr/core/plan-design/changes/whats-new-in-version-1910#bkmk_mem)를 참조하세요.

Configuration Manager의 2015년 12월 릴리스(버전 1511)는 현재 Microsoft Configuration Manager 제품의 초기 릴리스였습니다. 통상적으로 이를 Configuration Manager 현재 분기라고 합니다. ‘현재 분기’는 제품의 증분 업데이트를 지원하는 버전임을 나타냅니다.  또한 이를 통해 Configuration Manager의 이 릴리스와 이전 릴리스를 구분할 수 있습니다.  

Configuration Manager 현재 분기는  

- Configuration Manager 2007, System Center 2012 Configuration Manager 등의 이전 버전과 달리 제품 이름에 연도나 제품 식별자를 사용하지 않습니다.  

- 업데이트 버전이라고도 하는 증분식 제품 내 업데이트를 지원합니다. 초기 릴리스는 버전 1511입니다. 이후 버전은 버전 1910과 같이 콘솔 내 업데이트로 1년에 여러 번 출시됩니다.  

- 기준선 버전을 사용하여 설치됩니다. 1511이 원래 기준선 버전이지만 시간이 지나면서 1902 등의 새 기준선 버전이 릴리스됩니다. 기준 버전을 사용하여 새 Configuration Manager 사이트 및 계층 구조를 설치하거나 System Center 2012 Configuration Manager의 지원되는 버전에서 업그레이드할 수 있습니다.  

## <a name="bkmk_updates"></a> 콘솔 내 업데이트

Configuration Manager는 권장 업데이트를 손쉽게 찾아서 설치할 수 있도록 하는 **업데이트 및 서비스**라는 콘솔 내 서비스 방법을 사용합니다.  

일부 버전은 Configuration Manager 콘솔 내에서 기존 사이트에 대한 업데이트로만 제공됩니다. 이러한 업데이트는 새 Configuration Manager 사이트를 설치하는 데 사용할 수 없습니다. 예를 들어 1910 업데이트는 Configuration Manager 콘솔 내에서만 사용할 수 있습니다. 이는 지원되는 버전의 Configuration Manager를 이미 실행 중인 사이트를 업데이트하는 데 사용됩니다.

주기적으로, 업데이트 버전이 새로운 *기준* 버전으로 릴리스되기도 합니다. 예를 들어, 업데이트 버전 1902 역시 기준 버전입니다. 기준 버전은 새 사이트 또는 계층을 설치하는 데 사용할 수 있습니다. 1802와 같은 오래된 기준 버전으로 시작하지 말고, 가장 최신 버전으로 업그레이드하세요. 항상 최신 기준 버전을 사용하시기 바랍니다.

자세한 내용은 다음 아티클을 참조하세요.

- [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)
- [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)

## <a name="bkmk_servicepoint"></a> 서비스 연결 지점  

Configuration Manager 현재 분기에는 **서비스 연결점**이라는 새로운 사이트 시스템 역할이 포함됩니다.  

- 여러 클라우드 지원 기능을 위한 담당자

- 사이트를 위한 업데이트 다운로드

- 사이트의 진단 및 사용량 현황 데이터를 Microsoft 클라우드로 업로드

이 사이트 시스템 역할은 작업의 온라인 및 오프라인 모드를 모두 지원합니다. 자세한 내용은 [서비스 연결 지점 정보](/sccm/core/servers/deploy/configure/about-the-service-connection-point)를 참조하세요.  

## <a name="bkmk_usage"></a> 진단 및 사용량 현황 데이터

Configuration Manager는 사이트 및 인프라의 진단 및 사용량 현황 데이터를 수집합니다. 이 정보는 서비스 연결 지점을 통해 컴파일되어 Microsoft 클라우드 서비스에 제출됩니다. Configuration Manager는 사용자 환경에 적용되는 업데이트를 다운로드할 때 이 데이터를 필요로 합니다. 서비스 연결점을 설정할 때는 수집되는 데이터의 액세스 수준과 해당 데이터를 자동으로 제출할지(온라인) 아니면 수동으로 제출할지(오프라인) 여부를 지정할 수 있습니다.

자세한 내용은 [진단 및 사용량 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.  

## <a name="bkmk_out"></a> 사용되지 않는 기능  

[Intel AMT(Active Management Technology) 지원 기반 컴퓨터에 대한 기본 지원](#bkmk_AMT)과 같은 일부 기능은 Configuration Manager 콘솔에서 제거됩니다. 네트워크 액세스 보호와 같은 다른 기능은 완전히 제거됩니다. 또한 Windows Vista, Windows Server 2008, SQL Server 2008 등 이전 Microsoft 제품 중 일부는 더 이상 지원되지 않습니다.  

사용되지 않는 기능 목록은 [제거되는 항목과 사용되지 않는 항목](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)을 참조하세요.  

지원되는 제품, 운영 체제 및 구성에 대한 자세한 내용은 [지원되는 구성](/sccm/core/plan-design/configs/supported-configurations)을 참조하세요.  

### <a name="bkmk_AMT"></a> Intel AMT(Active Management Technology) 지원  

Configuration Manager 현재 분기에서 Configuration Manager 콘솔 내의 AMT 기반 컴퓨터에 대한 기본 지원이 제거됩니다. [Microsoft Configuration Manager용 Intel SCS 추가 기능](https://www.intel.com/content/www/us/en/software/setup-configuration-software.html)을 사용하는 경우 AMT 기반 컴퓨터가 완전히 관리되는 상태로 유지됩니다. 추가 기능을 사용하면 AMT를 관리할 최신 기능에 액세스하고 Configuration Manager가 해당 변경 사항을 통합할 수 있을 때까지 도입된 제한 사항을 제거할 수 있습니다.  

Configuration Manager에 대한 통합 AMT 제거에는 대역 외 관리가 포함됩니다. 대역 외 관리 지점 사이트 시스템 역할은 더 이상 사용할 수 없습니다.  

> [!Note]
> System Center 2012 Configuration Manager의 대역 외 관리는 이 변경 사항에 의해 영향을 받지 않습니다.

## <a name="changes-in-functionality"></a>기능 변경 사항

이어지는 섹션에서는 System Center 2012 R2 Configuration Manager와 Configuration Manager 현재 분기 버전 1511 사이의 중대한 기능 변경 사항을 설명합니다. 최신 기능 변경 사항에 대한 자세한 내용은 [증분 버전의 새로운 기능](/configmgr/core/plan-design/changes/whats-new-incremental-versions)을 참조하세요.

### <a name="client-deployment"></a>클라이언트 배포  

Configuration Manager에서는 새로운 소프트웨어로 사이트의 나머지 부분을 업그레이드하기 전에 새 버전의 Configuration Manager 클라이언트를 테스트하는 새로운 기능을 제공합니다. 새로운 클라이언트를 파일럿 실행하는 사전 프로덕션 컬렉션을 설정할 수 있습니다. 사전 프로덕션에서 새로운 클라이언트 소프트웨어에 만족하면 새 버전을 사용하여 사이트의 나머지 부분을 자동으로 업그레이드하도록 클라이언트 수준을 올릴 수 있습니다.  

클라이언트 테스트 방법에 대한 자세한 내용은 [사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](/sccm/core/clients/manage/upgrade/test-client-upgrades)을 참조하세요.  

### <a name="os-deployment"></a>OS 배포  

OS 배포에 대한 다음 변경 내용에 유의하세요.

- 새 작업 순서 만들기 마법사에서 다음 새 작업 순서 유형을 사용할 수 있습니다. **업그레이드 패키지에서 운영 체제 업그레이드**. 이 유형은 Windows 7 또는 Windows 8.1에서 Windows 10으로 컴퓨터를 업그레이드하는 단계를 만듭니다. 자세한 내용은 [최신 버전으로 Windows 업그레이드](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)를 참조하세요.  

- 이제 운영 체제를 배포할 때 Windows PE 피어 캐시를 사용할 수 있습니다. OS를 배포하기 위해 작업 순서를 실행하는 컴퓨터가 배포 지점에서 콘텐츠를 다운로드하는 대신 Windows PE 피어 캐시를 사용하여 피어 캐시 원본에서 콘텐츠를 가져올 수 있습니다. 이 동작은 로컬 배포 지점이 없는 지점 시나리오에서 WAN 트래픽을 최소화하는 데 유용합니다. 자세한 내용은 [WAN 트래픽을 줄이기 위해 Windows PE 피어 캐시 준비](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic)를 참조하세요.  

- 이제 사용자 환경에서 Windows as a Service 상태를 볼 수 있습니다. 또한 서비스 계획을 만들어 배포 링을 구성하고 새 빌드가 릴리스될 때 Windows 10 현재 분기 컴퓨터를 최신 상태로 유지할 수 있습니다. 또한 Windows 10 클라이언트 빌드에 대한 지원이 끝나갈 때 경고를 볼 수 있습니다. 자세한 내용은 [Windows as a Service 관리](/sccm/osd/deploy-use/manage-windows-as-a-service)를 참조하세요.  

### <a name="application-management"></a>애플리케이션 관리  

애플리케이션 관리에 대한 다음 변경 내용에 유의하세요.

- Configuration Manager 이상을 실행 중인 Windows 10 디바이스에 대한 UWP(유니버설 Windows 플랫폼) 앱을 배포할 수 있습니다. 자세한 내용은 [Windows 애플리케이션 만들기](/sccm/apps/get-started/creating-windows-applications)를 참조하세요.  

- 소프트웨어 센터의 외관이 새롭게 바뀌었습니다. 이전에 애플리케이션 카탈로그에만 표시된 사용자가 사용할 수 있는 앱이 이제 애플리케이션 탭 아래 소프트웨어 센터에 표시됩니다. 이 동작으로 사용자가 이러한 배포를 더 쉽게 검색할 수 있고 별도의 애플리케이션 카탈로그를 참조하지 않아도 됩니다. 또한 더는 브라우저에서 Silverlight를 사용하도록 설정할 필요가 없습니다. 자세한 내용은 [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)을 참조하세요.  

- MDM 애플리케이션 유형을 통해 Windows 설치 관리자를 사용하면 Windows Installer 기반 앱을 만들어 Windows 10을 실행하는 등록된 PC에 배포할 수 있습니다. 자세한 내용은 [Windows 애플리케이션 만들기](/sccm/apps/get-started/creating-windows-applications)를 참조하세요.  

- Configuration Manager 2012에서, Windows 스토어에서 앱에 대한 링크를 지정하기 위해 링크를 직접 지정하거나 앱이 설치된 원격 컴퓨터를 찾을 수 있습니다. Configuration Manager 현재 분기에서, 링크를 직접 입력할 수 있지만 참조 컴퓨터를 검색하는 대신 직접 링크를 입력하고, Configuration Manager 콘솔에서 직접 앱의 스토어를 검색할 수 있습니다.  

### <a name="software-updates"></a>소프트웨어 업데이트  

소프트웨어 업데이트에 대한 다음 변경 내용에 유의하세요.

- 이제 Configuration Manager에서는 컴퓨터에 대한 소프트웨어 업데이트 관리 방법 간의 차이를 감지할 수 있습니다. 특히 WUfB(Windows Update for Business)에 연결하는 Windows 10 컴퓨터와 WSUS에 연결된 컴퓨터를 구분할 수 있습니다. 새로운 특성인 **UseWUServer**는 WUfB를 사용하여 컴퓨터를 관리할지 여부를 지정합니다. 컬렉션에서 이 설정을 사용하여 소프트웨어 업데이트 관리에서 이러한 컴퓨터를 제거할 수 있습니다. 자세한 내용은 [Integration with Windows Update for Business in Windows 10](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10)을 참조하십시오.  

- 이제 Configuration Manager 콘솔에서 WSUS 정리 작업을 예약 및 실행할 수 있습니다. **소프트웨어 업데이트 지점 구성 요소** 속성에서 WSUS 정리 작업 실행을 선택하면 다음 소프트웨어 업데이트 동기화에서 실행됩니다. 만료된 소프트웨어 업데이트는 WSUS 서버에서 거부함 상태로 설정되고, 컴퓨터의 Windows 업데이트 에이전트에서는 이 소프트웨어 업데이트를 더는 검색하지 않습니다. 자세한 내용은 [WSUS 정리 작업 예약 및 실행](/sccm/sum/deploy-use/software-updates-maintenance)을 참조하세요.  

### <a name="compliance-settings"></a>호환성 설정  

준수 설정에 대한 다음 변경 내용에 유의하세요.

- Configuration Manager에서는 구성 항목을 만들기 위한 워크플로를 개선합니다. 이제, 구성 항목을 만들고 지원되는 플랫폼을 선택하면 해당 플랫폼과 관련된 설정만 사용할 수 있습니다. [규정 준수 설정 시작](/sccm/compliance/get-started/get-started-with-compliance-settings)을 참조하세요.  

- 이제 **구성 항목 만들기** 마법사를 사용하면 만들려는 구성 항목 유형을 쉽게 선택할 수 있습니다. 또한 새로 추가되거나 업데이트된 구성 항목을 다음에 사용할 수 있습니다.  

    - Configuration Manager 클라이언트를 사용하여 관리되는 Windows 10 디바이스  

    - Configuration Manager 클라이언트를 사용하여 관리되는 Mac OS X 디바이스  

    - Configuration Manager 클라이언트를 사용하여 관리되는 Windows 데스크톱 및 서버 컴퓨터  

    - Configuration Manager 클라이언트 없이 관리되는 Windows 8.1 및 Windows 10 디바이스  

    자세한 내용은 [구성 항목을 만드는 방법](/sccm/compliance/deploy-use/create-configuration-items)을 참조하세요.  

- 구성 관리자 클라이언트를 사용하지 않고 관리되는 Mac OS X 컴퓨터에서 설정을 관리할 수 있도록 지원합니다.

### <a name="on-premises-mobile-device-management"></a>온-프레미스 MDM(모바일 디바이스 관리)  

이제 온-프레미스 Configuration Manager 인프라를 사용하여 모바일 디바이스를 관리할 수 있습니다. 모든 디바이스 및 관리 데이터는 온-프레미스에서 처리되며 Microsoft Intune 또는 기타 클라우드 서비스의 일부가 아닙니다. 이 종류의 디바이스 관리에는 클라이언트 소프트웨어가 필요하지 않습니다. Configuration Manager에서 디바이스 OS에 기본 제공되는 기능을 사용하여 디바이스를 관리합니다.  

자세한 내용은 [온-프레미스 인프라로 모바일 디바이스 관리](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[증분 버전의 새로운 기능](/configmgr/core/plan-design/changes/whats-new-incremental-versions)
