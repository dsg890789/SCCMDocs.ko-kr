---
title: 사이트 시스템 역할 옵션
titleSuffix: Configuration Manager
description: 별도의 설명이 필요한 Configuration Manager 사이트 역할에 대한 자세한 내용은 이 문서를 참조하세요.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 4571634ff204ac882abb9dcca9f75291d3dbcf50
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75798927"
---
# <a name="configuration-options-for-site-system-roles-in-configuration-manager"></a>Configuration Manager의 사이트 시스템 역할에 대한 구성 옵션

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 사이트 시스템 역할의 구성 옵션 대부분은 별도의 설명이 필요 없으며 구성할 때 마법사 또는 대화 상자에서 설명됩니다. 다음 섹션에서는 설정에 추가 정보가 필요할 수 있는 사이트 시스템 역할에 대해 설명합니다.  


## <a name="BKMK_ApplicationCatalog_Website"></a> 애플리케이션 카탈로그 웹 사이트 지점  

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터 업데이트된 클라이언트는 사용자가 이용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

애플리케이션 카탈로그 웹 사이트 지점을 설정하는 방법에 대한 자세한 내용은 [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)을 참조하세요.  


## <a name="BKMK_ApplicationCatalog_WebService"></a> 애플리케이션 카탈로그 웹 서비스 지점  

> [!Important]
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터 업데이트된 클라이언트는 사용자가 이용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

애플리케이션 카탈로그 웹 서비스 지점을 설정하는 방법에 대한 자세한 내용은 [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management)을 참조하세요.  


## <a name="BKMK_CertificateRegistrationPoint"></a> 인증서 등록 지점  

인증서 등록 지점을 설정하는 방법에 대한 자세한 내용은 [인증서 프로필 소개](/sccm/protect/deploy-use/introduction-to-certificate-profiles)를 참조하세요.  


## <a name="BKMK_Distribution_Point"></a> 배포 지점  

콘텐츠 배포를 위해 배포 지점을 설정하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  

PXE 배포를 위해 배포 지점을 설정하는 방법에 대한 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.  

멀티캐스트 배포를 위해 배포 지점을 설정하는 방법에 대한 자세한 내용은 [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)를 참조하세요.  

### <a name="install-and-configure-iis-if-required-by-configuration-manager"></a>Configuration Manager에 필요한 경우 IIS 설치 및 구성

IIS가 이미 설치되지 않은 경우 Configuration Manager가 사이트 시스템에 IIS를 설치 및 설정하도록 하려면 이 옵션을 선택합니다. IIS를 모든 배포 지점에 설치하고 이 설정을 선택하여 마법사를 진행해야 합니다.  

### <a name="site-system-installation-account"></a>사이트 시스템 설치 계정

사이트 서버에 설치된 배포 지점의 경우 사이트 서버의 컴퓨터 계정만 사이트 시스템 설치 계정으로 사용할 수 있습니다. 자세한 내용은 [계정](/sccm/core/plan-design/hierarchy/accounts#site-system-installation-account)을 참조하세요.  


## <a name="BKMK_Enrollment_Point"></a> 등록 지점  

등록 지점은 macOS 컴퓨터를 설치하고 온-프레미스 모바일 디바이스 관리를 통해 관리하고 있는 디바이스를 등록하는 데 사용됩니다. 자세한 내용은 다음 아티클을 참조하세요.  

- [Mac에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-macs)  

- [사용자가 온-프레미스 MDM에 디바이스를 등록하는 방법](/sccm/mdm/deploy-use/user-enroll-devices-on-premises-mdm)  

### <a name="allowed-connections"></a>허용된 연결

HTTPS 설정이 자동으로 선택되어 있으며, 이 설정을 사용하려면 등록 프록시 지점에 대한 서버 인증과 SSL을 통한 데이터 암호화를 위한 PKI 인증서가 서버에 있어야 합니다. 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

서버 인증서 배포 예와 IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [IIS를 실행하는 사이트 시스템에 웹 서버 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012) 섹션을 참조하세요.  


## <a name="BKMK_Enrollment_Proxy_Point"></a> 등록 프록시 지점  

모바일 디바이스를 위해 등록 프록시 지점을 설정하는 방법에 대한 자세한 내용은 [온-프레미스 MDM을 사용하여 디바이스를 등록하는 방법](/sccm/mdm/deploy-use/user-enroll-devices-on-premises-mdm)을 참조하세요.  

### <a name="client-connections"></a>클라이언트 연결

HTTPS 설정이 자동으로 선택됩니다. 서버에 다음 PKI 인증서가 필요합니다.

- Configuration Manager로 등록한 모바일 디바이스 및 Mac 컴퓨터에 대한 서버 인증의 경우
- SSL(Secure Sockets Layer)을 통한 데이터 암호화의 경우

인증서 요구 사항에 대한 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

서버 인증서 배포 예와 IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [IIS를 실행하는 사이트 시스템에 웹 서버 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012) 섹션을 참조하세요.  


## <a name="BKMK_Fallback_Status_Point"></a> 대체 상태 지점  

### <a name="number-of-state-messages-and-throttle-interval-in-seconds"></a>상태 메시지 수 및 제한 간격(초)

이러한 옵션에 대한 기본 설정은 10,000개의 상태 메시지 및 3,600초의 제한 간격입니다. 다음 두 조건에 모두 해당하면 설정을 변경해야 할 수도 있습니다.  

- 대체 상태 지점이 인트라넷에서만 연결을 수락함  

- 다수의 컴퓨터에 대한 클라이언트 배포 롤아웃 시 대체 상태 지점을 사용함  

이 시나리오에서는 상태 메시지의 연속 스트림으로 상태 메시지 백로그가 만들어질 수 있으며, 이로 인해 오랜 기간 사이트 서버의 프로세서 사용률이 높아질 수 있습니다. 또한 Configuration Manager 콘솔과 클라이언트 배포 보고서에 클라이언트 배포에 대한 최신 정보가 표시되지 않을 수 있습니다.  

이러한 대체 상태 지점 설정은 클라이언트 배포 시 생성되는 상태 메시지에 대해 설정되며, 인터넷상의 클라이언트가 인터넷 기반 관리 지점에 연결할 수 없는 경우와 같은 클라이언트 통신 문제에 대해서는 설정되지 않습니다. 대체 상태 지점에서 클라이언트 배포 시 생성되는 상태 메시지에만 이러한 설정을 적용할 수는 없기 때문에 대체 상태 지점이 인터넷에서 연결을 수락하는 경우 이러한 설정을 구성하지 마세요.  

구성 관리자 클라이언트가 성공적으로 설치된 각 컴퓨터는 다음 4가지 상태 메시지를 대체 상태 지점에 전송합니다.  

- 클라이언트 배포가 시작되었습니다.  

- 클라이언트 배포에 성공했습니다.  

- 클라이언트 할당이 시작되었습니다.  

- 클라이언트 할당이 성공했습니다.  

구성 관리자 클라이언트를 설치할 수 없거나 할당할 수 없는 컴퓨터에서는 추가 상태 메시지가 전송됩니다.  

예를 들어 20,000대의 컴퓨터에 Configuration Manager 클라이언트를 배포할 경우 80,000개의 상태 메시지가 대체 상태 지점에 전송될 수 있습니다. 기본 제한 구성은 3600초(1시간)마다 10,000개의 상태 메시지를 대체 상태 지점에 전송할 수 있도록 허용하므로 상태 메시지가 대체 상태 지점에 백로깅될 수 있습니다. 또한 대체 상태 지점과 사이트 서버 사이의 가용 네트워크 대역폭과 다수의 상태 메시지를 처리하기 위한 사이트 서버의 처리 능력도 고려해야 합니다.  

이런 문제를 방지하려면 상태 메시지의 수를 늘리고 제한 간격을 줄이는 것이 좋습니다.  

다음 조건 중 하나에 해당하는 경우 대체 상태 지점에 대한 제한 값을 다시 설정합니다.  

- 계산해 볼 때 현재 제한 값이 대체 상태 지점에서 상태 메시지를 처리하는 데 필요한 수준보다 높음  

- 현재 제한 설정으로 인해 사이트 서버의 프로세서 사용률이 높아지는 것으로 확인됩니다.  

대체 상태 지점 제한 설정을 변경하는 것에 따른 결과를 잘 알고 설정을 변경해야 합니다. 예를 들어 제한 설정을 높게 늘릴 경우 사이트 서버의 프로세서 사용률이 높게 증가하여 모든 사이트 작업이 느려질 수 있습니다.  
