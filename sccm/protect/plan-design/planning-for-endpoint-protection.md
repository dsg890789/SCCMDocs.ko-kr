---
title: "Endpoint Protection 계획 | Microsoft 문서"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: 16
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 927732150b99bbe362a3ed36976b49a716efc14c


---
# <a name="planning-for-endpoint-protection-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Endpoint Protection 계획

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 Endpoint Protection을 사용하면 Configuration Manager 계층 구조의 클라이언트 컴퓨터에 대한 맬웨어 방지 정책 및 Windows 방화벽 보안을 관리할 수 있습니다.  

> [!IMPORTANT]  
>  Configuration Manager 계층 구조의 클라이언트를 관리하려면 Endpoint Protection 사용을 허가받아야 합니다.  

Configuration Manager에서 Endpoint Protection을 사용하면 다음과 같은 이점이 있습니다.  

-   선택한 컴퓨터 그룹에 대해 맬웨어 방지 정책 및 Windows 방화벽 설정을 구성하고 Windows Defender Advanced Threat Protection을 관리합니다.  

-   Configuration Manager 소프트웨어 업데이트를 통해 최신 맬웨어 방지 정의 파일을 다운로드하여 클라이언트 컴퓨터를 최신 상태로 유지  

-   메일 알림을 보내거나, 콘솔 내 모니터링을 사용하거나, 보고서를 확인하여 클라이언트 컴퓨터에서 맬웨어가 검색되면 관리자에게 알림  

Windows 10 컴퓨터에서는 Endpoint Protection 관리에 대한 추가 클라이언트가 필요하지 않습니다. Windows 8.1 이하 버전의 컴퓨터에서 Endpoint Protection은 Configuration Manager 클라이언트뿐만 아니라 자체 클라이언트를 설치합니다. Endpoint Protection 클라이언트에는 다음과 같은 기능이 있습니다.  

-   맬웨어 및 스파이웨어 검색 및 수정  

-   루트킷 검색 및 수정  

-   중요 취약성 평가와 정의 및 엔진 자동 업데이트  

-   네트워크 검사 시스템을 통해 네트워크 취약성 검색  

-   맬웨어를 Microsoft에 보고하도록 클라우드 보호 서비스와 통합 이 서비스에 가입하면 컴퓨터에서 식별되지 않은 맬웨어가 검색될 때 Windows Defender 또는 Endpoint Protection 클라이언트가 맬웨어 보호 센터에서 최신 정의를 다운로드할 수 있습니다.  

> [!NOTE]  
>  Hyper-V를 실행하는 서버와 지원되는 운영 체제가 있는 게스트 가상 컴퓨터에 Endpoint Protection 클라이언트를 설치할 수 있습니다. 과도한 CPU 사용을 방지하기 위해 Endpoint Protection 작업에는 서비스가 동시에 실행되지 않도록 기본 제공된 임의 지연이 있습니다.  

  또한 Configuration Manager의 Endpoint Protection을 사용하면 Configuration Manager 콘솔에서 Windows 방화벽 설정을 관리할 수 있습니다.  

 [예제 시나리오: System Center Endpoint Protection을 사용하여 System Center Configuration Manager에서 맬웨어로부터 컴퓨터 보호](../deploy-use/scenarios-endpoint-protection.md)에서는 Endpoint Protection 및 Windows 방화벽을 구성하고 관리할 수 있는 방법을 보여 줍니다.  

## <a name="managing-malware-with-endpoint-protection"></a>Endpoint Protection을 사용하여 맬웨어 관리  

Configuration Manager의 Endpoint Protection을 사용하면 Endpoint Protection 클라이언트 구성 설정이 포함된 맬웨어 방지 정책을 만들 수 있습니다. 그런 다음 클라이언트 컴퓨터에 이러한 맬웨어 방지 정책을 배포하고 **모니터링** 작업 영역의 **Endpoint Protection 상태** 노드에서 모니터링하거나 Configuration Manager 보고서를 통해 모니터링할 수 있습니다.  

 추가 정보:  

-   [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책 만들기 및 배포](../deploy-use/endpoint-antimalware-policies.md) - 구성할 수 있는 설정 목록을 사용하여 맬웨어 방지 정책을 만들고 배포하고 모니터링합니다.  

-   [System Center Configuration Manager에서 Endpoint Protection 모니터링](../deploy-use/monitor-endpoint-protection.md) - 작업 보고서, 감염된 클라이언트 컴퓨터 등을 모니터링합니다.   

-   [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책 및 방화벽 설정 관리](../deploy-use/endpoint-antimalware-firewall.md) - [맬웨어 방지](../deploy-use/endpoint-antimalware-firewall.md#manage-antimalware-policies) 또는 [방화벽](../deploy-use/endpoint-antimalware-firewall.md#manage-windows-firewall-policies), [클라이언트 컴퓨터에서 검색된 맬웨어 수정](../deploy-use/endpoint-antimalware-firewall.md#remediate-detected-malware) 및 기타 작업에 대한 정책 우선 순위를 변경할 수 있습니다.

## <a name="managing-windows-firewall-with-endpoint-protection"></a>Endpoint Protection을 사용하여 Windows 방화벽 관리  
 Configuration Manager의 Endpoint Protection은 클라이언트 컴퓨터에서 Windows 방화벽의 기본 관리 기능을 제공합니다. 각 네트워크 프로필에 대해 다음 설정을 구성할 수 있습니다.  

-   Windows 방화벽을 사용하거나 사용하지 않도록 설정  

-   허용되는 프로그램 목록에 있는 연결을 포함하여 들어오는 연결 차단  

-   Windows 방화벽이 새 프로그램을 차단할 때 사용자에게 알림  

> [!NOTE]  
>  Endpoint Protection은 Windows 방화벽 관리만 지원합니다.  

  Endpoint Protection에 대한 Windows 방화벽 정책을 만들어 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection에 대한 Windows 방화벽 정책을 만들어 배포하는 방법](../deploy-use/create-windows-firewall-policies.md)을 참조하세요.  

## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

Configuration Manager의 1606 버전부터(현재 분기) Endpoint Protection은 Windows Defender ATP(Advanced Threat Protection)를 관리하고 모니터링할 수 있습니다. Windows Defender ATP는 엔터프라이즈에서 네트워크에 대한 고급 공격을 검색하고 조사하고 대응할 수 있도록 하는 새로운 서비스입니다. [Windows Defender Advanced Threat Protection](../deploy-use/windows-defender-advanced-threat-protection.md)을 참조하세요.

## <a name="endpoint-protection-workflow"></a>Endpoint Protection 워크플로  
 다음 다이어그램을 사용하여 Configuration Manager 계층 구조에서 Endpoint Protection을 구현하는 워크플로를 이해합니다.   

 ![Endpoint Protection 워크플로](../media/Endpoint-Protection-Workflow.gif)

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Mac 컴퓨터 및 Linux 서버에 대한 Endpoint Protection 클라이언트  
 System Center 2012에는 Linux 및 Mac 컴퓨터용 Endpoint Protection 클라이언트가 포함되어 있습니다. 이러한 클라이언트에는 Configuration Manager가 제공되지 않습니다. 대신, [Microsoft 볼륨 라이선스 서비스 센터](https://www.microsoft.com/licensing/servicecenter/default.aspx)에서 다음 제품을 다운로드해야 합니다.  

-   Mac용 System Center 2012 Endpoint Protection  

-   Linux용 System Center 2012 Endpoint Protection  

> [!IMPORTANT]  
>  Linux 및 Mac용 Endpoint Protection 설치 파일을 다운로드하려면 Microsoft 볼륨 라이선스 고객이어야 합니다.  

 이러한 제품은 Configuration Manager 콘솔에서 관리할 수 없습니다. 그러나 설치 파일이 포함된 System Center Operations Manager 관리 팩을 사용하면 Operations Manager로 Linux용 클라이언트를 관리할 수 있습니다.  

 Linux 및 Mac 컴퓨터용 Endpoint Protection 클라이언트를 설치 및 관리하는 방법에 대한 자세한 내용은 **설명서** 폴더에 있는 해당 제품의 설명서를 참조하세요.

## <a name="best-practices-for-endpoint-protection-in-configuration-manager"></a>Configuration Manager의 Endpoint Protection 모범 사례  
 System Center 2012 Configuration Manager의 Endpoint Protection에 대한 다음 모범 사례를 사용합니다.  

### <a name="configure-custom-client-settings-for-endpoint-protection"></a>Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성  
 Endpoint Protection에 대한 클라이언트 설정을 구성할 때는 기본 클라이언트 설정을 사용하지 마세요. 기본 클라이언트 설정을 사용하면 계층 구조의 모든 컴퓨터에 설정이 적용됩니다. 대신 사용자 지정 클라이언트 설정을 구성 하 고 컬렉션의 계층 내 컴퓨터에서에서 이러한 설정을 할당 합니다.  

 사용자 지정 클라이언트 설정을 구성할 때 다음을 수행할 수 있습니다.  

-   조직의 다른 부분에 대 한 맬웨어 방지 및 보안 설정을 사용자 지정 합니다.  

-   전체 계층 구조에 배포하기 전에 소규모 컴퓨터 그룹에서 Endpoint Protection 실행 결과를 테스트합니다.  

-   점차 더 많은 클라이언트를 컬렉션에 추가하여 Endpoint Protection 클라이언트 배포를 단계별로 실행합니다.  

### <a name="distributing-definition-updates-by-using-software-updates"></a>소프트웨어 업데이트를 사용 하 여 배포 정의 업데이트  
 Configuration Manager 소프트웨어 업데이트를 사용하여 정의 업데이트를 배포하는 경우 다른 소프트웨어 업데이트가 포함되지 않은 패키지에 정의 업데이트를 포함하는 것이 좋습니다. 이렇게 정의 업데이트 패키지의 크기가 작은 배포 지점에 보다 신속 하 게 복제할 수 있습니다.



<!--HONumber=Dec16_HO3-->


