---
title: 기능 및 특성
titleSuffix: Configuration Manager
description: Configuration Manager의 기본 관리 기능에 대해 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: c50efb804787bb8288e6b1f200cee005ed2d0370
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75802840"
---
# <a name="features-and-capabilities-of-configuration-manager"></a>Configuration Manager의 기능 및 특성

*적용 대상: Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager의 기본 관리 기능에 대해 설명합니다. 각 기능에는 고유한 필수 구성 요소가 있고 각 기능을 사용하는 방식에 따라 Configuration Manager 계층 구조의 디자인과 구현이 달라질 수 있습니다. 예를 들어 계층의 디바이스에 소프트웨어 업데이트를 배포하려는 경우 소프트웨어 업데이트 지점 사이트 시스템 역할이 필요합니다.  

사용자 환경에서 이러한 관리 기능을 지원할 수 있도록 Configuration Manager를 계획하고 설치하는 방법에 대한 자세한 내용은 [Configuration Manager 사용 준비](/sccm/core/plan-design/get-ready)를 참조하세요.  

## <a name="co-management"></a>공동 관리

공동 관리는 기존 Configuration Manager 배포를 Microsoft 365 클라우드에 연결하는 기본적인 방법입니다. 공동 관리를 통해 Configuration Manager와 Microsoft Intune을 모두 사용하여 Windows 10 디바이스를 동시에 관리할 수 있습니다. 공동 관리를 사용하면 조건부 액세스와 같은 새 기능을 추가하여 Configuration Manager의 기존 투자를 클라우드에 연결할 수 있습니다. 자세한 내용은 [공동 관리란?](/sccm/comanage/overview)을 참조하세요.

## <a name="desktop-analytics"></a>Desktop Analytics

Desktop Analytics는 Configuration Manager와 통합되는 클라우드 기반 서비스입니다. 서비스는 Windows 클라이언트의 업데이트 준비 사항에 대해 충분한 정보를 파악한 후 결정하도록 인사이트와 인텔리전스를 제공합니다. Microsoft 클라우드 서비스에 연결된 수백만 대의 디바이스에서 집계된 데이터를 조직의 데이터와 결합합니다. 자세한 내용은 [Desktop Analytics란?](/configmgr/desktop-analytics/overview)을 참조하세요.

## <a name="cloud-attached-management"></a>Cloud-attached 관리

클라우드 관리 게이트웨이, 클라우드 기반 배포 지점 및 Azure Active Directory와 같은 기능을 사용해 인터넷 기반 클라이언트를 관리합니다.

자세한 내용은 다음 아티클을 참조하세요.

- [인터넷에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients-internet)
- [Azure AD 계획](/sccm/core/plan-design/security/plan-for-security#bkmk_planazuread)
- [Azure 서비스](/sccm/core/servers/deploy/configure/azure-services-wizard)

## <a name="real-time-management"></a>실시간 관리

CMPivot을 사용하여 온라인 디바이스를 즉시 쿼리한 이후 심층적인 인사이트를 얻기 위해 데이터를 필터링 및 그룹화할 수 있습니다. 또한, Configuration Manager 콘솔을 사용해 Windows PowerShell 스크립트를 관리하고 클라이언트에 배포할 수 있습니다. 자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot) 및 [PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

## <a name="application-management"></a>애플리케이션 관리

애플리케이션을 만들고, 관리하고, 관리자가 관리하는 여러 디바이스에서 배포 및 모니터링하는 데 도움이 됩니다. Configuration Manager 콘솔에서 Office 365를 배포, 업데이트 및 관리할 수 있습니다. 이에 더해, Configuration Manager는 비즈니스용 Microsoft Store와 통합되어 클라우드 기반 앱을 제공합니다. 자세한 내용은 [애플리케이션 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.

## <a name="os-deployment"></a>OS 배포

Windows 10의 현재 위치 업그레이드를 배포하거나 OS 이미지를 캡처 및 배포할 수 있습니다. 이미지 배포에는 PXE, 멀티캐스트 또는 부팅 가능한 미디어를 사용할 수 있습니다. Windows AutoPilot을 사용하여 기존 디바이스를 다시 배포하는 데도 도움이 됩니다. 자세한 내용은 [OS 배포 소개](/sccm/osd/understand/introduction-to-operating-system-deployment)를 참조하세요.  

## <a name="software-updates"></a>소프트웨어 업데이트

조직에서 소프트웨어 업데이트를 관리, 배포 및 모니터링할 수 있습니다. Windows 배당 최적화 및 기타 피어 캐싱 기술과 통합되어 네트워크 사용량을 제어하는 데 도움이 됩니다. 자세한 내용은 [소프트웨어 업데이트 소개](/sccm/sum/understand/software-updates-introduction)를 참조하세요.  

## <a name="company-resource-access"></a>회사 리소스 액세스

원격 위치에 있는 조직의 사용자에게 데이터 및 애플리케이션에 대한 액세스 권한을 부여할 수 있습니다. 이 기능에는 Wi-Fi, VPN, 메일 및 인증서 프로필이 포함됩니다. 자세한 내용은 [데이터 및 사이트 인프라 보호](/sccm/protect/understand/protect-data-and-site-infrastructure)를 참조하세요.

## <a name="compliance-settings"></a>호환성 설정

조직 내 클라이언트 디바이스의 구성 호환성을 평가, 추적 및 재구성하는 데 도움이 됩니다. 또한 준수 설정을 사용하여 관리하는 디바이스에서 다양한 기능 및 보안 설정을 구성할 수 있습니다. 자세한 내용은 [디바이스 준수 확인](/sccm/compliance/understand/ensure-device-compliance)을 참조하세요.  

## <a name="endpoint-protection"></a>Endpoint Protection

조직의 컴퓨터에 보안, 맬웨어 방지, Windows 방화벽 관리 기능을 제공합니다. 여기에는 다음과 같은 Windows Defender 도구 모음의 기능을 사용한 관리 및 통합이 포함됩니다.

- Windows Defender 바이러스 백신
- Microsoft Defender Advanced Threat Protection
- Windows Defender Exploit Guard
- Windows Defender Application Guard
- Windows Defender 애플리케이션 제어
- Windows Defender 방화벽

자세한 내용은 [Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.  

## <a name="inventory"></a>재고

자산을 식별하고 모니터링하는 데 도움이 됩니다.

### <a name="hardware-inventory"></a>하드웨어 인벤토리

조직 내 디바이스의 하드웨어에 대한 자세한 정보를 수집합니다. 자세한 내용은 [하드웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory)를 참조하세요.  

### <a name="software-inventory"></a>소프트웨어 인벤토리

조직 내 클라이언트 컴퓨터에 저장된 파일에 대한 정보를 수집하고 보고합니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.  

### <a name="asset-intelligence"></a>Asset Intelligence

인벤토리 데이터를 수집하고 조직의 소프트웨어 라이선스 사용 현황을 모니터링하는 도구를 제공합니다. 자세한 내용은 [Asset Intelligence 소개](/sccm/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence)를 참조하세요.  

## <a name="on-premises-mobile-device-management"></a>온-프레미스 MDM(모바일 디바이스 관리)

디바이스 플랫폼에 기본 제공되는 온-프레미스 Configuration Manager 인프라 및 관리 기능을 사용하여 디바이스를 등록하고 관리합니다. (일반적인 관리에서는 별도로 설치된 구성 관리자 클라이언트가 사용됩니다.) 이 기능은 현재 Windows 10 Enterprise 및 Windows 10 Mobile 디바이스 관리를 지원합니다. 자세한 내용은 [온-프레미스 인프라로 모바일 디바이스 관리](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)를 참조하세요.  

## <a name="power-management"></a>전원 관리

조직 내 클라이언트 컴퓨터의 전원 소비량을 관리하고 모니터링합니다. 전원 계획을 구성하고, 업무 시간 외에는 Wake-on-LAN을 사용하여 유지 관리를 수행합니다. 자세한 내용은 [전원 관리 소개](/sccm/core/clients/manage/power/introduction-to-power-management)를 참조하세요.  

## <a name="remote-control"></a>원격 제어

Configuration Manager 콘솔에서 클라이언트 컴퓨터를 원격으로 관리하는 도구를 제공합니다. 자세한 내용은 [원격 제어 소개](/sccm/core/clients/manage/remote-control/introduction-to-remote-control)를 참조하세요.  

## <a name="reporting"></a>보고

Configuration Manager 콘솔에서 SQL Server Reporting Services의 고급 보고 기능을 사용할 수 있습니다. 이 기능은 수백 개의 기본 보고서를 제공합니다. 자세한 내용은 [보고 기능 소개](/sccm/core/servers/manage/introduction-to-reporting)를 참조하세요.  

## <a name="software-metering"></a>소프트웨어 계량

구성 관리자 클라이언트에서 소프트웨어 사용량 현황 데이터를 모니터링하고 수집합니다. 이 데이터를 사용하여 소프트웨어가 설치된 후 사용되는지 여부를 확인할 수 있습니다. 자세한 내용은 [소프트웨어 계량을 사용하여 앱 사용 모니터링](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)을 참조하세요.  
