---
title: "사이트 시스템 역할 옵션 | Microsoft 문서"
description: "별도의 설명이 필요한 Configuration Manager 사이트 역할에 대한 자세한 내용은 이 문서를 참조하세요."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b4db5d86cc0ed020ed176feb2e8f1f9dc51a2280
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="configuration-options-for-site-system-roles-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 사이트 시스템 역할 구성 옵션

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 사이트 시스템 역할의 구성 옵션 대부분은 별도의 설명이 필요 없으며 구성할 때 마법사 또는 대화 상자에서 설명됩니다. 다음 섹션에서는 설정에 추가 정보가 필요할 수 있는 사이트 시스템 역할에 대해 설명합니다.  

##  <a name="BKMK_ApplicationCatalog_Website"></a> 응용 프로그램 카탈로그 웹 사이트 지점  
 응용 프로그램 카탈로그에 대한 응용 프로그램 카탈로그 웹 사이트 지점을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 관리 계획 및 구성](../../../../apps/plan-design/plan-for-and-configure-application-management.md)을 참조하세요.  

 **클라이언트 연결**  

 더 안전한 연결 설정을 사용하고 클라이언트가 인터넷에서 연결하는지 확인하려면 **HTTPS**를 선택합니다. 이 옵션을 사용하려면 클라이언트에 대한 서버 인증과 SSL(Secure Socket Layer)을 통한 데이터 암호화를 위해 PKI 인증서가 서버에 필요합니다. 인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

 서버 인증서 배포 예제와 IIS(인터넷 정보 서비스)에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에서 *IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포* 섹션을 참조하세요.  

 **응용 프로그램 카탈로그 웹 사이트를 신뢰할 수 있는 사이트 영역에 추가**  

 이 메시지는 기본 클라이언트 설정에서 **응용 프로그램 카탈로그 웹 사이트를 Internet Explorer의 신뢰할 수 있는 사이트 영역에 추가** 클라이언트 설정이 현재 설정된 값(**True** 또는 **False**)을 표시합니다. 사용자 지정 클라이언트 설정을 사용하여 이 설정을 구성한 경우에는 이 값을 직접 확인해야 합니다.  

 FQDN(정규화된 도메인 이름)에 대해 이 사이트 시스템이 설정되어 있고 웹 사이트가 Internet Explorer의 신뢰할 수 있는 사이트 영역에 없는 경우 사용자가 응용 프로그램 카탈로그에 연결할 때 자격 증명을 요청하는 메시지가 표시됩니다.  

 **조직 이름**  

 응용 프로그램 카탈로그에 표시되는 이름을 입력합니다. 이 브랜딩 정보를 통해 이 웹 사이트가 신뢰할 수 있는 원본임을 쉽게 확인할 수 있습니다.  

##  <a name="BKMK_ApplicationCatalog_WebService"></a> 응용 프로그램 카탈로그 웹 서비스 지점  
 응용 프로그램 카탈로그에 대한 응용 프로그램 카탈로그 웹 서비스 지점을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 관리 계획 및 구성](../../../../apps/plan-design/plan-for-and-configure-application-management.md)을 참조하세요.  

 **HTTPS**  

 이 응용 프로그램 카탈로그 웹 서비스 지점에 대해 응용 프로그램 카탈로그 웹 사이트 지점을 인증하려면 **HTTPS** 를 선택합니다.  이 옵션을 사용하려면 서버 인증과 SSL을 통한 데이터 암호화를 위한 PKI 인증서가 응용 프로그램 카탈로그 웹 사이트 지점을 실행하는 서버에 있어야 합니다. 인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

 서버 인증서 배포 예제와 IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에서 *IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포* 섹션을 참조하세요.  

##  <a name="BKMK_CertificateRegistrationPoint"></a> 인증서 등록 지점  
 인증서 등록 지점을 설정하는 방법에 대한 자세한 내용은 [인증서 프로필 소개](/sccm/protect/deploy-use/introduction-to-certificate-profiles)를 참조하세요.  

##  <a name="BKMK_Distribution_Point"></a> 배포 지점  
 콘텐츠 배포를 위해 배포 지점을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

 PXE 배포를 위해 배포 지점을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 PXE를 사용하여 네트워크를 통해 Windows 배포](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

 멀티캐스트 배포를 위해 배포 지점을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md)를 참조하세요.  

 **Configuration Manager에 필요한 경우 IIS 설치 및 구성**  
 IIS가 이미 설치되지 않은 경우 Configuration Manager가 사이트 시스템에 IIS를 설치 및 설정하도록 하려면 이 옵션을 선택합니다. IIS를 모든 배포 지점에 설치하고 이 설정을 선택하여 마법사를 진행해야 합니다.  

 **사이트 시스템 설치 계정**  
 사이트 서버에 설치된 배포 지점의 경우 사이트 서버의 컴퓨터 계정만 사이트 시스템 설치 계정으로 사용할 수 있습니다.  

 **자체 서명된 인증서 만들기 또는 PKI 클라이언트 인증서 가져오기**  
 이 인증서는 다음 두 가지 용도로 사용됩니다.  

1.  배포 지점이 상태 메시지를 전송하기 전에 관리 지점에 대해 배포 지점을 인증합니다.  

2.  **클라이언트에 대해 PXE 지원 사용**을 선택할 경우 인증서가 PXE 부팅을 수행하는 컴퓨터로 전송되어 이러한 컴퓨터에서 운영 체제 배포 시 관리 지점에 연결할 수 있습니다.  

사이트의 모든 관리 지점이 HTTP를 사용하도록 설정된 경우 자체 서명된 인증서를 만들고, 관리 지점이 HTTPS를 사용하도록 설정된 경우 PKI 클라이언트 인증서를 가져옵니다.  

인증서를 가져오려면 Configuration Manager에 대한 다음 요구 사항을 따르는 PKI 인증서가 포함된 PKCS #12(공개 키 암호 표준 #12) 파일을 찾습니다.  

-   용도에 클라이언트 인증이 포함되어야 합니다.  

-   개인 키를 내보내도록 설정되어 있어야 합니다.  

인증서 주체 이름이나 SAN(주체 대체 이름)에 대한 특정 요구 사항은 없으며, 여러 배포 지점에 동일한 인증서를 사용할 수 있습니다.  

인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요. 이 인증서의 배포 예제는 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에서 *배포 지점용 클라이언트 인증서 배포* 섹션을 참조하세요.  

**사전 준비된 콘텐츠에 이 배포 지점 사용**  
사전 준비된 콘텐츠에 이 배포 지점을 사용하려면 이 확인란을 선택합니다. 이 확인란을 선택하면 콘텐츠를 배포할 때 배포 동작을 설정할 수 있습니다. 항상 배포 지점에서 콘텐츠를 사전 준비하고 패키지의 초기 콘텐츠를 사전 준비하지만 콘텐츠 업데이트 사항이 없는 경우 일반적인 콘텐츠 배포 프로세스를 사용하도록 선택하거나, 항상 패키지의 콘텐츠에 일반적인 콘텐츠 배포 프로세스를 사용하도록 선택할 수 있습니다.  

**경계 그룹**  
 배포 지점에 경계 그룹을 연결할 수 있습니다. 콘텐츠를 배포하는 동안 클라이언트는 콘텐츠에 대한 원본 위치로 사용할 배포 지점과 연결된 경계 그룹 안에 있어야 합니다.
 - **버전 1610 이전**에서 **콘텐츠에 대한 대체 원본 위치를 사용하도록 허용** 확인란을 선택하면 이러한 경계 그룹 외부에 있는 클라이언트가 다른 배포 지점을 사용할 수 없는 경우 해당 배포 지점을 대체 원본 위치로 사용하게 만들 수 있습니다.
 - **버전 1610부터** **콘텐츠에 대한 대체 원본 위치 허용**을 더 이상 구성할 수 없습니다.  대신, 클라이언트가 추가 경계 그룹에서 유효한 콘텐츠 원본 위치 검색을 시작할 수 있는 경우를 확인하는 경계 그룹 간의 관계를 설정합니다.

##  <a name="BKMK_Enrollment_Point"></a> 등록 지점  
등록 지점은 Mac 컴퓨터를 설치하고 온-프레미스 모바일 장치 관리를 통해 관리하고 있는 장치를 등록하는 데 사용됩니다. 자세한 내용은 다음을 참조하십시오.  

-   [System Center Configuration Manager에서 Mac에 클라이언트를 배포하는 방법](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

-   [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 사용하여 장치를 등록하는 방법](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

**허용된 연결**  
 HTTPS 설정이 자동으로 선택되어 있으며, 이 설정을 사용하려면 등록 프록시 지점에 대한 서버 인증, 대역 외 서비스 지점에 대한 서버 인증, SSL을 통한 데이터 암호화를 위한 PKI 인증서가 서버에 있어야 합니다. 인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

 서버 인증서 배포 예제와 IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에서 *IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포* 섹션을 참조하세요.  

##  <a name="BKMK_Enrollment_Proxy_Point"></a> 등록 프록시 지점  
모바일 장치를 위해 등록 프록시 지점을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 사용하여 장치를 등록하는 방법](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)을 참조하세요.  

**클라이언트 연결**  
 HTTPS 설정이 자동으로 선택되어 있으며, 이 설정을 사용하려면 Configuration Manager에서 등록한 모바일 장치와 Mac 컴퓨터에 대한 서버 인증과 SSL(Secure Sockets Layer)을 통한 데이터 암호화용 PKI 인증서가 서버에 있어야 합니다. 인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

 서버 인증서 배포 예제와 IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 PKI 인증서의 단계별 배포 예제: Windows Server 2008 인증 기관](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)에서 *IIS를 실행하는 사이트 시스템용 웹 서버 인증서 배포* 섹션을 참조하세요.  

##  <a name="BKMK_Fallback_Status_Point"></a> 대체 상태 지점  
**상태 메시지 수** 및 **제한 간격(초)**  
대부분의 경우 이러한 옵션의 기본 설정(10,000개의 상태 메시지 및 3,600초의 제한 간격)이면 충분하지만, 다음 두 조건에 모두 해당하면 설정을 변경해야 할 수도 있습니다.  

-   대체 상태 지점이 인트라넷에서만 연결을 수락함  

-   다수의 컴퓨터에 대한 클라이언트 배포 롤아웃 시 대체 상태 지점을 사용함  

이 시나리오에서는 상태 메시지의 연속 스트림으로 상태 메시지 백로그가 만들어질 수 있으며, 이로 인해 오랜 기간 사이트 서버의 CPU(중앙 처리 장치) 사용률이 높아질 수 있습니다. 또한 Configuration Manager 콘솔과 클라이언트 배포 보고서에 클라이언트 배포에 대한 최신 정보가 표시되지 않을 수 있습니다.  

이러한 대체 상태 지점 설정은 클라이언트 배포 시 생성되는 상태 메시지에 대해 설정되며, 인터넷상의 클라이언트가 인터넷 기반 관리 지점에 연결할 수 없는 경우와 같은 클라이언트 통신 문제에 대해서는 설정되지 않습니다. 대체 상태 지점에서 클라이언트 배포 시 생성되는 상태 메시지에만 이러한 설정을 적용할 수는 없기 때문에 대체 상태 지점이 인터넷에서 연결을 수락하는 경우 이러한 설정을 구성하지 마십시오.  

System Center 2012 Configuration Manager 클라이언트가 성공적으로 설치된 각 컴퓨터는 다음 4가지 상태 메시지를 대체 상태 지점에 전송합니다.  

-   클라이언트 배포가 시작되었습니다.  

-   클라이언트 배포에 성공했습니다.  

-   클라이언트 할당이 시작되었습니다.  

-   클라이언트 할당이 성공했습니다.  

Configuration Manager 클라이언트를 설치할 수 없거나 할당할 수 없는 컴퓨터에서는 추가 상태 메시지가 전송됩니다.  

예를 들어 20,000대의 컴퓨터에 Configuration Manager 클라이언트를 배포할 경우 80,000개의 상태 메시지가 대체 상태 지점에 전송될 수 있습니다. 기본 제한 구성은 3600초(1시간)마다 10,000개의 상태 메시지를 대체 상태 지점에 전송할 수 있도록 허용하므로 상태 메시지가 대체 상태 지점에 백로깅될 수 있습니다. 또한 대체 상태 지점과 사이트 서버 사이의 가용 네트워크 대역폭과 다수의 상태 메시지를 처리하기 위한 사이트 서버의 처리 능력도 고려해야 합니다.  

이런 문제를 방지하려면 상태 메시지의 수를 늘리고 제한 간격을 줄이는 것이 좋습니다.  

다음 조건 중 하나에 해당하는 경우 대체 상태 지점에 대한 제한 값을 다시 설정합니다.  

-   계산해 볼 때 현재 제한 값이 대체 상태 지점에서 상태 메시지를 처리하는 데 필요한 수준보다 높음  

-   현재 제한 설정으로 인해 사이트 서버의 CPU 사용률이 높아지는 것으로 확인됨  

대체 상태 지점 제한 설정을 변경하는 것에 따른 결과를 잘 알고 설정을 변경해야 합니다. 예를 들어 제한 설정을 높게 늘릴 경우 사이트 서버의 CPU 사용률이 높게 증가하여 모든 사이트 작업이 느려질 수 있습니다.  
