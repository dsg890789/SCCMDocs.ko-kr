---
title: "Intune 독립 실행형 또는 하이브리드 MDM 선택 | System Center Configuration Manager"
description: "Intune과 Configuration Manager를 사용하는 하이브리드 모바일 장치 관리 배포 또는 Intune 독립 실행형 실행 중에서 선택합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 2e6ec1b2b822298d4fa6a17e2d7439167b83080a

---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Microsoft Intune 독립 실행형 및 System Center Configuration Manager에서 하이브리드 모바일 장치 관리 선택

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 및 MDM(모바일 장치 관리)과 관련하여 가장 자주 묻는 질문 중 하나는 "Intune 및 Configuration Manager와 함께 하이브리드 MDM을 배포할지 아니면 클라우드 전용 구성으로 Intune 독립 실행형을 사용할지"입니다. 이것은 중요한 결정이며 구현 후에는 쉽게 변경할 수 없습니다.  

 Intune 독립 실행형 배포는 온-프레미스 인프라 없이 웹 콘솔을 통해 관리됩니다. 이 방법은 민첩하고 간단하며 클라우드 우선 방식의 조직에서 많이 사용됩니다.  

 하이브리드 MDM 배포에는 Intune과 Configuration Manager가 필요하며, Configuration Manager 관리자에게 친숙한 도구를 사용하여 관리됩니다. 이 방법은 MDM과 기존 클라이언트의 “단일 창” 관리를 제공하며 대규모 환경으로 확장합니다.  

##  <a name="what-does-intune-standalone-mean"></a>Intune 독립 실행형이란 무슨 의미인가요?  
 Intune의 핵심이 클라우드 서비스입니다. Intune 데이터 센터는 북아메리카, 유럽 및 아시아에 위치하고 있으며 보안 정책, 메일 및 Wi-Fi 프로필, 응용 프로그램, 인벤토리 등을 제공합니다.  

 Intune 독립 실행형 구현 방법을 사용할 경우 온-프레미스 인프라가 필요하지 않습니다. 모든 구성, 관리, 배포 및 보고 작업이 전 세계의 모든 위치에서 액세스할 수 있는 웹 기반 콘솔을 통해 수행됩니다.  

 온-프레미스 커넥터는 Microsoft Exchange와 NDES(네트워크 장치 등록 서비스) 등의 온-프레미스 응용 프로그램을 사용하기 위해 Intune 서비스에 대한 연결을 제공합니다.  

 Intune은 클라우드 서비스이므로 단기간에 구축 및 배포할 수 있습니다.  

##  <a name="what-does-hybrid-mdm-mean"></a>하이브리드 MDM이란 무슨 의미인가요?  
 Configuration Manager 투자를 최대화하려는 조직, 세분화된 제어를 원하는 고객 또는 Intune의 범위 제한을 초과하는 고객에게는 Intune을 사용하여 모바일 장치를 관리하는 하이브리드 구현이 적합합니다.  

 하이브리드 배포를 구현하려면 Microsoft System Center 2012 Configuration Manager SP1 이상이 필요합니다.  

 Intune 서비스는 서비스 연결 지점 사이트 시스템 역할(이전의 Microsoft Intune 커넥터)을 사용하여 Configuration Manager에 연결되며 중앙 관리 또는 Configuration Manager 계층의 기본 사이트에 설치됩니다. Intune 테넌트는 하나의 Configuration Manager 계층에만 연결할 수 있으며 Configuration Manager 계층은 하나의 Intune 테넌트에만 연결할 수 있습니다.  

 하이브리드 MDM 구성에서 Configuration Manager 인프라 온-프레미스에 의해 일부 처리 및 저장소 오버헤드가 수행됩니다. 이러한 효율성 향상을 통해 하이브리드 MDM은 Intune 독립 실행형보다 뛰어난 확장성을 제공합니다.  

 하이브리드 배포에서는 Configuration Manager 관리에 친숙한 도구를 사용할 수 있습니다. 하이브리드 MDM을 구현하면 모바일 장치에서 RBAC(역할 기반 관리 제어), SSRS(SQL Server Reporting Services) 및 컬렉션 멤버 관리 쿼리를 사용하는 복잡한 장치와 사용자 그룹화를 사용할 수 있습니다.  

##  <a name="planning-choices-and-intune-deployment-timelines"></a>계획 선택과 Intune 배포 타임라인  
 Intune은 새롭거나 향상된 기능, 확장성, Azure Portal을 통한 새로운 관리 콘솔 환경, Azure Active Directory를 통한 동적 그룹 등을 제공하는 월별 업데이트를 통해 빠르게 발전하고 있습니다. 따라서 모든 디자인 결정 시 제품의 추가 방향을 고려해야 합니다.  

 서비스가 단기, 중기 및 장기 단위로 개발되므로 하이브리드 구성에서 현재 제공하는 여러 가지 고유 기능이 Intune 독립 실행형에 기능적으로 복제됩니다.  

 독립 실행형과 하이브리드 중에서 결정했다면 배포 타임라인을 고려해야 합니다. 고객은 보통 디자인, 빌드, 사용자 승인 테스트 및 파일럿 단계 등 여러 배포 단계를 반복 수행하며 프로덕션 환경에 배포하기 전에 완료하는 데 몇 달이 소요되기도 합니다. 이러한 이유로 Intune 계층 디자인을 선택할 때는 실제 배포가 발생하는 시기와 서비스의 단기, 중기 및 장기적 방향을 고려합니다.  

 Intune 서비스는 계속 발전하고 있으며 우리의 목표는 사용자의 구성 선택 옵션을 간소화하는 것입니다. 앞으로는 기존 클라이언트와 모바일 장치에 대해 단일 관리 콘솔이 필요한 고객만 하이브리드 MDM 환경을 선택하게 될 것입니다.  Microsoft는 단기 및 중기 서비스 업데이트를 제공하여 Azure Portal을 통한 역할 기반의 액세스, 더 심화된 Azure Active Directory 통합을 통한 동적 그룹을 추가하여 확장성을 향상시키기 위해 계속 노력하고 있습니다.  

 마지막으로, 어떤 구성을 선택하든 하이브리드와 독립 실행형 구성 선택 간을 쉽게 이동할 수 있도록 하는 방법도 연구 중입니다. 현재는 MDM 기관을 전환하려면 Microsoft 지원의 수동 작업과 테넌트에서 많은 작업이 필요합니다. 이 작업을 간소화하기 위해 하이브리드와 Intune 독립 실행형이 공존하고 두 관리 유형 간에 사용자를 이동할 수 있어 구성을 선택할 필요가 없도록 하는 것이 우리의 목표입니다.  또한 이 변경은 지원 센터에 문의해야 하는 문제와 장치 등록 취소 및 다시 등록 작업을 제거합니다.  

##  <a name="pros-and-cons-of-intune-standalone"></a>Intune 독립 실행형의 장점 및 단점  

|장점|단점|  
|----------|----------|  
|신속한 빌드 및 배포<br /><br /> 온-프레미스 인프라 없음<br /><br /> 더 빈번한 업데이트 및 기능 릴리스<br /><br /> 학습하는 데 짧게 걸림<br /><br /> 외부에서 사용할 수 있는 관리 콘솔|제한된 보고 기능<br /><br /> 제한된 보안 역할 제한<br /><br /> 외부 도구(예: PowerShell 등) 없음<br /><br /> 제한된 앱 인벤토리<br /><br /> 기본 사용자 및 장치 그룹화 기능<br /><br /> Silverlight 필요|  

##  <a name="pros-and-cons-of-hybrid-mdm"></a>하이브리드 MDM의 장점 및 단점  

|장점|단점|  
|----------|----------|  
|확장성<br /><br /> 고급 도구(예: Configuration Manager 콘솔, PowerShell, 로깅)<br /><br /> RBAC(역할 기반 액세스 제어)<br /><br /> 고급 보고<br /><br /> MDM과 기존 클라이언트를 위한 "단일 창" 관리<br /><br /> 확장된 앱 인벤토리<br /><br /> 고급 사용자 및 장치 그룹화<br /><br /> 여러 Exchange 온-프레미스 및 Exchange Online 커넥터 지원<br /><br /> 여러 NDES/CRP 역할 지원<br /><br /> 장치를 "회사 소유"로 표시 가능<br /><br /> 뛰어난 문제 해결 기능<br /><br /> 구독에 Configuration Manager 사용자 CAL 포함|온-프레미스 복잡성(구성 및 관리)<br /><br /> 학습하는 데 오래 걸림<br /><br /> 업데이트 및 기능 릴리스에 필요한 서비스<br /><br /> 추가 라이선스 요구 사항(예: Windows, SQL Server)|  

##  <a name="planning-decisions"></a>계획 결정  
 ![하이브리드&#45;결정](../../mdm/understand/media/hybrid-decisions.png)  

|단계|결정|
|-|-|  
|<img src="media/hybrid-1.png" style="min-width:32px">|**몇 개의 장치를 관리할 계획인가요?**<br /><br /> Intune 독립 실행형은 최대 50,000개의 장치를 지원합니다. 하이브리드 MDM은 최대 300,000개의 장치를 지원합니다.<br /><br /> 대규모의 독립 실행형 또는 하이브리드 MDM을 배포하려는 경우 Microsoft 계정 팀에 문의하는 것이 좋습니다. Microsoft 계정 팀에서 규모와 제한에 대해 논의할 수 있는 Intune 전문가를 배정할 것입니다.|  
|![하이브리드&#45;2](../../mdm/understand/media/hybrid-2.png)|**세분화된 액세스 제어(RBAC)가 필요한가요?**<br /><br /> RBAC(역할 기반 액세스 제어)가 System Center 2012 Configuration Manager에 추가되었습니다. RBAC를 사용하면 Configuration Manager 관리자가 복잡한 권한 집합을 디자인 및 배포하고, Configuration Manager 개체 및 기능에 대한 관리 액세스를 제한할 수 있습니다.<br /><br /> Intune 독립 실행형은 두 개의 관리자 역할(모든 권한 및 읽기 전용 권한)만 제공합니다.<br /><br /> 조직에서 특정 관리 범위를 특정 사용자, 장치, 기능 또는 개체로 제한해야 하는 경우 Configuration Manager와 RBAC가 필요합니다.<br /><br /> 조직의 관리 팀이 소규모이기 때문에 액세스 제어를 복잡하게 세분화할 필요가 없는 경우 Intune과 기본 보안 역할을 사용하는 것이 가장 적합합니다.|  
|![하이브리드&#45;3](../../mdm/understand/media/hybrid-3.png)|**고급 보고 기능이 필요한가요?**<br /><br /> 하이브리드 MDM 및 Configuration Manager를 사용하면 SSRS(SQL Server Reporting Services)를 사용하는 고급 보고 기능이 제공됩니다. Configuration Manager는 34개의 기본 제공 MDM 보고서 및 400개 이상의 표준 Configuration Manager 보고서와 함께 제공됩니다. 또한 SSRS는 관리자 및 비즈니스 분석가가 자체적으로 사용자 지정 보고서를 작성할 수 있는 기능을 제공합니다. 또한 오케스트레이션 도구와 같은 외부 도구를 통해 Configuration Manager 데이터베이스를 쿼리하여 사용자 지정 경고와 같은 특정 기능을 제공할 수 있습니다. Configuration Manager에서 보고서를 실행할 때 모든 보고서에 기존의 PC 인벤토리 등의 비MDM 데이터를 모바일 장치 인벤토리와 함께 포함할 수 있습니다.<br /><br /> Intune 독립 실행형에서는 9개의 보고서를 제공합니다. 이러한 보고서는 사용자 지정할 수 없으며 제한된 입력 변수를 제공합니다. 보고서를 인쇄하거나 CSV 또는 HTML로 내보낼 수 있습니다.<br /><br /> 조직에 고급 보고 기능이 필요하고 SSRS를 관리할 수 있는 지식 및 대역폭을 갖추고 있는 경우 하이브리드 MDM이 가장 적합합니다.<br /><br /> 조직에서 간편한 보고 엔진과 미리 정의된 보고서를 사용하려는 경우 Intune 독립 실행형의 보고 기능으로 충분합니다.|  
|![하이브리드&#45;4](../../mdm/understand/media/hybrid-4.png)|**인터넷 액세스 없이 Windows 10 장치를 관리하고 계신가요?**<br /><br /> Configuration Manager(현재 분기)에서는 온-프레미스 인프라를 사용하는 MDM 채널을 통해서만 Windows 10 장치를 관리할 수 있습니다.<br /><br /> 온\-프레미스 모바일 장치 관리 기능은 인터넷에 액세스할 수 없는 클라이언트의 MDM 관리를 허용하기 위해 디자인되었으며 주로 단일 사용 장치(키오스크 장치 등) 및 IoT 장치를 대상으로 합니다.<br /><br /> Intune 독립 실행형은 클라우드 전용 접근 방식을 사용하므로 관리되는 모든 장치가 인터넷에 액세스할 수 있어야 합니다. 조직에서 온\-프레미스 모바일 장치 관리를 통해 Windows 10 장치를 관리하려는 경우 하이브리드 MDM 구성이 필요합니다. 온\-프레미스 모바일 장치 관리에서는 인터넷과 인트라넷 모바일 장치의 동시 관리를 지원하지 않습니다.|  
|![하이브리드&#45;5](../../mdm/understand/media/hybrid-5.png)|**전체 앱 인벤토리가 필요한가요?**<br /><br /> 기본적으로 Intune 독립 실행형은 Intune이 관리하고 배포하는 앱에 대한 앱 인벤토리만 수집합니다. 즉, Intune 회사 포털 밖의 사용자가 설치한 테스트용으로 로드된 앱에 대한 정보는 인벤토리 보고서에 포함되지 않습니다.<br /><br /> 하이브리드 MDM 및 Configuration Manager를 사용하면 관리자가 특정 장치를 "회사 소유"로 지정할 수 있습니다. 장치가 회사 소유 장치로 설정된 경우 확장된 앱 인벤토리가 수집되어 장치 전체 앱 목록에 대한 액세스를 제공합니다.<br /><br /> 관리 장치에서 개인적으로 설치된 앱에 대한 정보가 필요한 조직에는 하이브리드 MDM이 필요합니다. 이 선택에 따라 결정하기 전에 최종 사용자의 개인 정보에 대한 영향을 고려해야 합니다.|  
|![하이브리드&#45;6](../../mdm/understand/media/hybrid-6.png)|**기존의 팻 클라이언트 방식으로 PC를 관리하고 싶으신가요?**<br /><br /> 하이브리드 MDM이 독립 실행형 구성에 비해 나은 점은 "단일 창" 관리입니다. 이는 조직에서 하나의 관리 도구, 즉 Configuration Manager 콘솔을 사용하여 전체 데스크톱 컴퓨터, 서버 및 모바일 장치를 관리할 수 있다는 의미입니다. 또한 Configuration Manager 클라이언트를 사용하여 하드웨어 및 소프트웨어 인벤토리, 소프트웨어 업데이트 관리, 소프트웨어 배포 및 운영 체제 배포 등의 고급 관리 기능을 비모바일 장치에 대해 사용할 수 있습니다.<br /><br /> 조직에서 기존 Windows, Linux/UNIX 및 Mac 클라이언트를 관리하려는 경우 Configuration Manager가 가장 적합한 관리 플랫폼입니다.<br /><br /> 또한 Intune 독립 실행형은 Intune PC 관리 클라이언트를 사용하는 기존 PC 관리(Windows 7, 8.1 및 10)를 제공합니다. 하드웨어 인벤토리, Windows 업데이트, Endpoint Protection 및 간단한 소프트웨어 배포 등의 기본 PC 관리를 제공합니다. Configuration Manager에서는 클라이언트가 작동하지 않으므로 Intune 독립 실행형 및 하이브리드 MDM 배포 모두에서 사용할 수 있습니다.|  
|![하이브리드&#45;7](../../mdm/understand/media/hybrid-7.png)|**온-프레미스 인프라를 관리할 계획이신가요?**<br /><br /> 온-프레미스 인프라를 사용할 경우 관리 오버헤드와 복잡성이 증가합니다. Configuration Manager는 해당 인프라를 관리하기 위한 많은 지식, 경험 및 투자가 필요한 제품입니다.<br /><br /> 하이브리드 MDM에는 최소한 데이터베이스 역할, 보고 서비스 역할 및 서비스 연결 지점 역할이 있는 단일 Configuration Manager 기본 사이트가 필요합니다. 기존 PC 관리가 필요한 경우 관리 지점, 배포 지점, 소프트웨어 업데이트 지점 및 응용 프로그램 카탈로그 역할도 필요할 수 있습니다. 인증서 배포, Mac 관리 및 Endpoint Protection과 같은 고급 기능을 사용할 경우 더 많은 역할 및 복잡성이 추가됩니다.<br /><br /> Configuration Manager 계층에는 상태 및 기능에 대한 많은 관리가 필요합니다.<br /><br /> Configuration Manager 계층의 오버헤드를 원하지 않는 경우 Intune 독립 실행형 배포를 사용하는 것이 좋습니다.|  
|![하이브리드&#45;8](../../mdm/understand/media/hybrid-8.png)|**외부 도구가 필요한가요?**<br /><br /> Configuration Manager는 뛰어난 엔터프라이즈급 제품으로서 콘솔을 사용하지 않고 서비스를 조작할 수 있는 여러 가지 방법을 제공합니다. 하이브리드 MDM 배포를 사용하면 관리자가 Configuration Manager SDK 또는 PowerShell을 사용하여 프로그래밍 방식으로 모바일 장치를 관리할 수 있습니다. 또한 관리자가 System Center Orchestrator, PowerBI 및 다양한 타사 추가 기능 등의 도구를 사용할 수 있습니다.<br /><br /> Intune 독립 실행형 배포에서 모든 관리는 Silverlight 콘솔을 통해 수행해야 하며 외부 도구는 사용할 수 없습니다.|  
|![하이브리드&#45;9](../../mdm/understand/media/hybrid-9.png)|**신속한 MDM 기능 업데이트가 필요한가요?**<br /><br /> Configuration Manager(현재 분기)는 빠른 업데이트 서비스 및 기능을 제공하지만 Intune과 같은 클라우드 서비스의 개발로 인해 프로덕션 배포 기간이 더욱 단축됩니다.<br /><br /> Intune 독립 실행형에는 일반적으로 하이브리드 MDM 배포보다 먼저 새 기능이 추가됩니다.<br /><br /> 조직에서 최신 기술을 사용하고 싶은 경우 Intune 독립 실행형이 가장 신속하게 최신 MDM 기능을 제공합니다.|



<!--HONumber=Nov16_HO1-->


