---
title: "클라이언트 배포 모범 사례 | Microsoft 문서"
description: "System Center Configuration Manager의 클라이언트 배포 모범 사례를 확인합니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a933d69c-5feb-4b2b-84e8-56b3b64d5947
caps.latest.revision: "11"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 22f0981022f50d316b2572a720ae3c818daf0d43
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="best-practices-for-client-deployment-in-system-center-configuration-manager"></a>System Center Configuration Manager의 클라이언트 배포 모범 사례

*적용 대상: System Center Configuration Manager(현재 분기)*


## <a name="use-software-update-based-client-installation-for-active-directory-computers"></a>Active Directory 컴퓨터에 소프트웨어 업데이트 기반의 클라이언트 설치 사용  
 이 클라이언트 배포 방법은 기존 Windows 기술을 사용하며, Active Directory 인프라와 통합되고, Configuration Manager에서 구성 작업이 최소화되는 한편, 방화벽에 대해 구성하기 가장 쉽고, 가장 안전합니다. 그룹 정책 구성에 보안 그룹과 WMI 필터링을 사용하여 Configuration Manager 클라이언트를 설치할 컴퓨터를 더욱 유연하게 제어할 수 있습니다.  

 자세한 내용은 [소프트웨어 업데이트 기반 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP)항목을 참조하세요.  

## <a name="extend-the-active-directory-schema-and-publish-the-site-so-that-you-can-run-ccmsetup-without-command-line-options"></a>명령줄 옵션 없이 CCMSetup을 실행할 수 있도록 Active Directory 스키마를 확장하고 사이트 게시  
 Configuration Manager를 위해 Active Directory 스키마를 확장하고 Active Directory Domain Service에 사이트를 게시하면 많은 클라이언트 설치 속성이 Active Directory Domain Service에 게시됩니다. 컴퓨터에서 이러한 클라이언트 설치 속성을 찾을 수 있는 경우 Configuration Manager 클라이언트 배포 시 이러한 속성을 사용할 수 있습니다. 이 정보는 자동으로 생성되므로 수동으로 설치 속성을 입력하는 데 따른 사람의 실수 위험이 없습니다.  

 자세한 내용은 [System Center Configuration Manager에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](../../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md)를 참조하세요.  

## <a name="use-a-phased-rollout-to-manage-cpu-usage"></a>단계적 롤아웃을 사용하여 CPU 사용량 관리  
 단계적 클라이언트 배포를 사용하여 CPU 처리 요구 사항이 사이트 서버에 미치는 영향을 최소화합니다. 업무 시간 동안 기타 서비스에 보다 많은 가용 대역폭을 확보하는 동시에 배포로 인해 사용자의 컴퓨터가 느려지거나 다시 시작해야 할 경우 사용자에게 영향을 주지 않도록 업무 외 시간에 클라이언트를 배포합니다.  

## <a name="enable-automatic-upgrade-after-your-main-client-deployment-has-finished"></a>주 클라이언트 배포가 완료된 후에 자동 업그레이드 사용  
 [자동 클라이언트 업그레이드](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md)는 오프라인 상태여서 기본 클라이언트 설치 방법에서 누락되었을 수도 있는 소수의 클라이언트 컴퓨터를 업그레이드할 때 유용한 방법입니다. 

> [!NOTE]  
>  Configuration Manager의 성능 향상으로 자동 업그레이드를 기본 클라이언트 업그레이드 방법으로 사용할 수 있습니다. 그러나 성능은 클라이언트 수와 같은 계층 인프라에 따라 달라집니다.  


## <a name="use-smsmp-and-fsp-if-you-install-the-client-with-clientmsi-properties"></a>client.msi 속성을 사용하여 클라이언트를 설치하는 경우 SMSMP 및 FSP 사용  
 SMSMP 속성은 클라이언트가 통신하는 초기 관리 지점을 지정하며 Active Directory Domain Services, DNS, WINS와 같은 서비스 위치 솔루션에 대한 종속성을 없앱니다.  

 또한 FSP 속성을 사용하여 대체 상태 지점을 설치하면 클라이언트 설치와 할당을 모니터링하고 통신 문제를 파악할 수 있습니다.  

 이러한 옵션에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

## <a name="install-client-language-packs-before-you-install-the-clients"></a>클라이언트를 설치하기 전에 클라이언트 언어 팩 설치  
클라이언트를 배포하기 전에 클라이언트 언어 팩을 설치하는 것이 좋습니다. 클라이언트를 설치한 후에 추가 언어를 사용하기 위해 [클라이언트 언어 팩](../../../../core/servers/deploy/install/language-packs.md)을 설치할 경우 해당 언어를 사용하려면 먼저 클라이언트를 다시 설치해야 합니다. 모바일 장치 클라이언트의 경우 모바일 장치를 지우고 다시 등록해야 합니다.  

## <a name="prepare-required-pki-certificates-in-advance"></a>필요한 PKI 인증서를 미리 준비  
 인터넷상의 장치, 등록된 모바일 장치 및 Mac 컴퓨터를 관리하려면 사이트 시스템(관리 지점 및 배포 지점)과 클라이언트 장치에 PKI 인증서가 있어야 합니다. 프로덕션 네트워크에서 새 인증서를 사용하기 위한 변경 관리 승인이 필요하고 사이트 시스템 서버를 다시 시작하거나 사용자가 새 그룹 멤버 자격을 위해 로그오프했다가 로그온해야 할 수 있습니다. 또한 보안 권한 복제와 새 인증서 템플릿을 위한 충분한 시간을 고려해야 할 수 있습니다.  

 필요한 PKI 인증서에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

## <a name="before-you-install-clients-configure-any-required-client-settings-and-maintenance-windows"></a>클라이언트를 설치하기 전에 필요한 클라이언트 설정 및 유지 관리 기간 구성  
 클라이언트 설치 전이나 후에 유지 관리 기간과 [클라이언트 설정을 구성](../../../../core/clients/deploy/configure-client-settings.md)할 수 있지만, 클라이언트 설치 후에 즉시 이러한 설정이 사용되도록 클라이언트 설치 전에 필요한 설정을 구성하는 것이 좋습니다. 

 서버 및 Windows Embedded 장치에 대한 유지 관리 기간을 구성하여 중요한 장치의 비즈니스 연속성을 보장합니다. 필요한 소프트웨어 업데이트와 맬웨어 방지 소프트웨어로 인해 업무 시간 중에 컴퓨터가 다시 시작되지 않도록 유지 관리 기간을 구성할 수 있습니다.  

> [!IMPORTANT]  
>  UWF(통합 쓰기 필터)로 보호하려는 Windows 10 컴퓨터의 경우 클라이언트를 설치하기 전에 UWF에 대해 장치를 구성해야 합니다. 이를 통해 Configuration Manager에서 장치가 유지 관리 모드에 있는 동안 사용자가 장치에 로그인하지 못하도록 낮은 권한으로 잠그는 사용자 지정 자격 증명 공급자를 사용하여 클라이언트를 설치할 수 있습니다.  

## <a name="plan-your-user-enrollment-experience-for-mac-computers-and-mobile-devices"></a>Mac 컴퓨터와 모바일 장치에 대한 사용자 등록 환경 계획   
 사용자가 Configuration Manager를 사용하여 자신의 Mac 컴퓨터와 모바일 장치를 등록하는 경우 사용자 환경을 계획합니다. 예를 들어 사용자가 필요한 최소한의 정보만 입력하면 되도록 웹 페이지를 사용하여 설치 및 등록 프로세스를 스크립팅하고, 메일에 포함된 링크로 사용자에게 지침을 보낼 수 있습니다.  

## <a name="use-file-based-write-filters-for-windows-embedded-devices"></a>Windows Embedded 장치에 대한 파일 기반 쓰기 필터 사용 
 EWF(강화된 쓰기 필터)를 사용하는 Windows Embedded 장치는 상태 메시지 재동기화가 이루어질 수 있습니다. EWF를 사용하는 Windows Embedded 장치가 몇 개에 불과한 경우 이러한 재동기화가 눈에 띄지 않지만 델타 인벤토리 대신 전체 인벤토리를 전송하는 것과 같이 정보를 재동기화하는 Windows Embedded 장치가 많을 경우 이로 인해 네트워크 패킷이 크게 증가하고 사이트 서버의 CPU 처리량이 늘어날 수 있습니다.  

 Configuration Manager 클라이언트에서 사용할 쓰기 필터 유형을 선택하는 옵션이 나타나면 네트워크 및 CPU 효율성을 위해 파일 기반 쓰기 필터를 선택하고 장치 다시 시작 사이에 클라이언트 상태와 인벤토리 데이터를 유지하는 예외를 구성합니다. 필터 작성에 대한 자세한 내용은   [System Center Configuration Manager에서 Windows Embedded 장치에 클라이언트 배포 계획](../../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md)항목을 참조하세요.  

 기본 사이트에서 지원할 수 있는 Windows Embedded 클라이언트의 최대 수에 대한 자세한 내용은 [클라이언트 및 장치에 대해 지원되는 운영 체제](../../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)를 참조하세요.  
