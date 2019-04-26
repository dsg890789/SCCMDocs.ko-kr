---
title: 온-프레미스 MDM 계획
titleSuffix: Configuration Manager
description: Configuration Manager에서 모바일 장치를 관리 하려면 온-프레미스 모바일 장치 관리에 대 한 계획
ms.date: 03/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb9349a8c3f107f2da139148e4476537fe6aa7ed
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287163"
---
# <a name="plan-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

온-프레미스 모바일 장치 관리 (MDM)를 사용 하면 장치 OS에 기본 제공 관리 기능을 사용 하는 모바일 장치를 관리할 수 있습니다. 관리 기능은 OMA(Open Mobile Alliance) DM(디바이스 관리) 표준을 기준으로 하며 많은 디바이스 플랫폼은 이 표준을 사용하여 디바이스를 관리할 수 있도록 합니다. 이러한 장치 라고 *최신 장치* 설명서 및 Configuration Manager 콘솔에서. 이 용어를 관리 하는 Configuration Manager 클라이언트를 필요로 하는 다른 장치에서 해당 구분 합니다.  

온-프레미스 MDM.를 처리 하는 Configuration Manager 인프라를 준비 하기 전에 다음 요구 사항을 검토합니다



## <a name="bkmk_devices"></a> 지원되는 디바이스  

현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 디바이스에 대한 온-프레미스 모바일 디바이스 관리에서의 등록을 지원합니다.  
  
- Windows 10 Enterprise  
- Windows 10 Pro  
- Windows 10 팀   
- Windows 10 Mobile  
- Windows 10 Mobile Enterprise
- Windows 10 IoT Enterprise   



##  <a name="bkmk_intune"></a> Microsoft Intune 구독  

온-프레미스 MDM을 사용 하 여을 시작 하려면 Microsoft Intune 구독을 해야 합니다. 구독은 디바이스 라이선스를 추적하는 데만 필요하며 디바이스에 대한 관리 정보를 관리하거나 저장하는 데는 사용되지 않습니다. 모든 관리 데이터는 온-프레미스 Configuration Manager 인프라를 사용하여 조직에 저장됩니다.  

> [!Note]  
> 1810 버전부터 Intune 연결을 새 온-프레미스 MDM 배포에 필요 하지 않습니다.<!--3607730, fka 1359124--> 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 현재 기존 온-프레미스 MDM 배포에서 Intune 연결을 제거할 수 없습니다. 자세한 내용은 [Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)을 참조하세요.  

사이트에 인터넷 연결을 사용 하 여 장치를 Intune 서비스 정책 업데이트에 대 한 장치 관리 지점을 확인 하도록 장치에 알리기 위해 사용할 수 있습니다. 이 동작에 대 한 인터넷 연결 장치 알림을 엄격 하 게 Intune을 사용합니다. 장치 없이 인터넷 연결과 Intune에서 연결할 수 없는 사이트 시스템 역할 관리 기능을 사용 하 여 체크 구성된 된 폴링 간격에 의존 합니다.  

> [!TIP]  
> 필요한 사이트 시스템 역할을 설정 하기 전에 Intune 구독을 설정 합니다. 이 그러면 역할이 작동 하는 데 필요한 시간을 최소화 합니다.  

Intune 구독을 설정 하는 방법에 대 한 자세한 내용은 [온-프레미스 MDM에 대 한 Microsoft Intune 구독 설정](/sccm/mdm/get-started/set-up-intune-subscription-on-premises-mdm)합니다.  



##  <a name="bkmk_roles"></a> 사이트 시스템 역할  

온-프레미스 MDM 각 다음 사이트 시스템 역할 중 하나 이상이 필요 합니다.  

- **등록 프록시 지점** : 등록 요청 지원  

- **등록 지점** : 디바이스 등록 지원  

- **디바이스 관리 지점** : 정책 배달 이 사이트 시스템 역할은 모바일 디바이스 관리를 허용하도록 구성된 관리 지점 역할이 변형된 것입니다.  

- **배포 지점** : 콘텐츠 배달용  

- **서비스 연결 지점** : 방화벽 외부에 디바이스를 알리기 위해 Intune에 연결  

이러한 사이트 시스템 역할은 단일 사이트 시스템 서버에 설치할 수 있습니다 또는 조직의 요구에 따라 서로 다른 서버에 별도로 실행할 수 있습니다. 온-프레미스 MDM에 사용 되는 각 사이트 시스템 서버는 신뢰할 수 있는 장치와 통신 하기 위한 HTTPS 끝점으로 구성 되어야 합니다. 자세한 내용은 [신뢰할 수 있는 필수 통신](#bkmk_trustedComs)항목을 참조하세요.  

사이트 시스템 역할 계획에 대 한 자세한 내용은 참조 하세요. [Configuration Manager 용 사이트 시스템 서버 및 역할에 대 한 계획](/sccm/core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles)합니다.  

필요한 사이트 시스템 역할을 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [온-프레미스 MDM에 대 한 사이트 시스템 역할 설치](/sccm/mdm/get-started/install-site-system-roles-for-on-premises-mdm)합니다.  



##  <a name="bkmk_trustedComs"></a> 신뢰할 수 있는 통신  

온-프레미스 MDM에는 HTTPS 통신에 대해 사용 하도록 사이트 시스템 역할이 필요 합니다. 필요에 따라 서버와 장치 간의 신뢰할 수 있는 연결을 설정 하려면 엔터프라이즈의 CA (인증 기관)를 사용할 수 있습니다. 공개적으로 사용할 수 있는 CA를 사용 하 여 신뢰할 수 있는 기관 수 없습니다. 어느 방법이 든 필요한 사이트 시스템 역할을 호스트 하는 사이트 시스템 서버의 IIS에서 구성할 웹 서버 인증서를 해야 합니다. 해당 서버에 연결 해야 하는 장치에 설치 된 CA의 루트 인증서를 해야 합니다.  

엔터프라이즈의 CA를 사용 하 여 신뢰할 수 있는 통신을 설정 하는 경우에 다음 작업을 수행 합니다.  

- CA에서 웹 서버 인증서 템플릿 만들기 및 발급  

- 필요한 사이트 시스템 역할을 호스트하는 각 사이트 시스템 서버에 대한 웹 서버 인증서를 요청합니다.  

- 요청된 웹 서버 인증서를 사용하도록 사이트 시스템 서버의 IIS를 구성합니다.  

회사 Active Directory 도메인에 가입된 디바이스의 경우 엔터프라이즈 CA의 루트 인증서가 이미 디바이스의 신뢰할 수 있는 연결에 사용될 수 있습니다. 이 동작은 도메인에 가입 된 장치는 사이트 시스템 서버를 사용 하 여 HTTPS 연결에 대 한 자동으로 신뢰할 수 있는 것을 의미 합니다. 그러나 도메인 가입 된 장치 설치 된 필수 루트 인증서를 자동으로 가져오지 않습니다. 온-프레미스 MDM을 지 원하는 사이트 시스템 서버와 통신을 하려면 모바일 장치와 같은 도메인에 가입 되지 않은 장치에 루트 인증서를 수동으로 설치를 해야 합니다.  

개별 장치에서 사용 하기 위해 발급 CA의 루트 인증서를 내보냅니다. 루트 인증서 파일을 가져오려면 CA를 사용 하 여 내보낼 수 있습니다. 다른 방법은 CA에서 발급 한 웹 서버 인증서를 사용 하 여 루트를 추출 하 고 루트 인증서 파일을 만들 것입니다. 그런 다음 루트 인증서를 장치에 배달 되어야 합니다. 몇 가지 예제 배달 방법은 다음과 같습니다.

- 파일 시스템  

- 메일 첨부 파일  

- 메모리 카드  

- 테더링된 디바이스  

- 클라우드 스토리지(예: OneDrive)  

- NFC(근거리 통신) 연결  

- 바코드 스캐너  

- OOBE(첫 실행 경험) 프로비저닝 패키지  

자세한 내용은 참조 하세요. [온-프레미스 MDM에서 신뢰할 수 있는 통신에 대 한 인증서 설정](/sccm/mdm/get-started/set-up-certificates-on-premises-mdm)  



##  <a name="bkmk_enrollment"></a> 장치 등록

온-프레미스 MDM에 대 한 장치 등록을 사용 하도록 설정 하려면
- 사용자가 등록할 수 있는 권한이 부여 해야 합니다. 
- 필요한 역할을 호스트 하는 사이트 시스템 서버를 사용 하 여 장치를 신뢰할 수 있는 통신을 위해 구성 해야 합니다.  

사용자에 게 Configuration Manager 클라이언트 설정에서 등록 프로필을 설정 하 여 장치를 등록할 수 있는 권한을 부여 합니다. 검색 된 모든 사용자에 게 등록 프로필을 적용할 기본 클라이언트 설정을 사용할 수 있습니다. 또한 사용자 지정 클라이언트 설정에서 등록 프로필을 설정 하 고 하나 이상의 사용자 컬렉션에 설정을 푸시할 수 있습니다.  

사용자 권한 부여 후에 자신의 장치를 등록할 수 있습니다. 등록 하려면 사용자의 장치에 필요한 역할을 호스트 하는 사이트 시스템 서버에서 사용 되는 웹 서버 인증서를 발급 한 인증 기관 (CA)의 루트 인증서가 있어야 합니다.  

사용자가 시작한 등록 하는 대신, 대량 등록 패키지를 설정할 수 있습니다. 이 패키지에는 사용자 개입 없이 등록 장치 수 있습니다. 사용 하거나 장치에서 OOBE 프로세스가 진행 한 후 프로 비전 하기 전에 장치에 전달할 수 있습니다.  

설정 및 장치를 등록 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요. 

- [온-프레미스 MDM에 대 한 장치 등록 설정](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm)  

- [온-프레미스 MDM에 대한 디바이스 등록](/sccm/mdm/deploy-use/enroll-devices-on-premises-mdm)  

