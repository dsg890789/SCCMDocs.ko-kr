---
title: "인증서 프로필 필수 조건 | Microsoft 문서"
description: "System Center Configuration Manager의 인증서 프로필과 외부 종속성 및 제품 내 종속성에 대해 알아봅니다."
ms.custom: na
ms.date: 03/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0317fd02-3721-4634-b18b-7c976a4e92bf
caps.latest.revision: 9
author: arob98
ms.author: angrobe
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: fba52ee305fe67418f2fe544bfe94d10467236d0
ms.lasthandoff: 03/29/2017


---
# <a name="prerequisites-for-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 인증서 프로필에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 인증서 프로필에는 외부 종속성과 제품 내 종속성이 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|AD CS(Active Directory 인증서 서비스)를 실행하는 엔터프라이즈 발급 CA(인증 기관)<br /><br /> 인증서를 해지하려면 계층 구조 최상위에 있는 사이트 서버의 컴퓨터 계정에 Configuration Manager의 인증서 프로필에서 사용하는 각 인증서 템플릿에 대해 *인증서 발급 및 관리* 권한이 있어야 합니다. 또는 해당 CA에서 사용하는 모든 인증서 템플릿에 권한을 부여할 수 있도록 인증서 관리자 사용 권한을 부여합니다.<br /><br /> 인증서 요청에 대한 관리자 승인이 지원됩니다. 그러나 인증서를 발급하는 데 사용되는 인증서 템플릿을 인증서 주체에 대한 **요청에서 제공**으로 구성하여 System Center Configuration Manager에서 이 값을 자동으로 제공할 수 있도록 해야 합니다.|Active Directory 인증서 서비스에 대한 자세한 내용은 Windows Server 문서를 참조하세요.<br /><br /> Windows Server 2012: [Active Directory 인증서 서비스 개요](http://go.microsoft.com/fwlink/p/?LinkId=286744)<br /><br /> Windows Server 2008: [Windows Server 2008의 Active Directory 인증서 서비스](http://go.microsoft.com/fwlink/p/?LinkId=115018)|  
|Windows Server 2012 R2에서 실행되는 Active Directory 인증서 서비스의 네트워크 장치 등록 서비스 역할 서비스.<br /><br /> 이 밖에도 다음 지침을 따릅니다.<br /><br /> TCP 443(HTTPS의 경우) 또는 TCP 80(HTTP의 경우) 이외의 포트 번호는 클라이언트와 네트워크 장치 등록 서비스 간의 통신에 지원되지 않습니다.<br /><br /> 네트워크 장치 등록 서비스를 실행하는 서버는 발급 CA와 다른 서버에 있어야 합니다.|System Center Configuration Manager는 Windows Server 2012 R2의 네트워크 장치 등록 서비스와 통신하여 SCEP(단순 인증서 등록 프로토콜) 요청을 생성하고 확인합니다.<br /><br /> 인터넷에서 연결하는 사용자 또는 장치(예: Microsoft Intune에서 관리하는 모바일 장치)에 인증서를 발급할 경우 해당 장치에서 인터넷을 통해 네트워크 장치 등록 서비스를 실행하는 서버에 액세스할 수 있어야 합니다. 예를 들어 경계 네트워크(완충 지역 및 스크린된 서브넷이라고도 함)에 서버를 설치합니다.<br /><br /> 네트워크 장치 등록 서비스를 실행하는 서버와 발급 CA 간에 방화벽이 있으면 두 서버 간의 통신 트래픽(DCOM)을 허용하도록 방화벽을 구성해야 합니다. 또한 이 방화벽 요구 사항은 System Center Configuration Manager 사이트 서버를 실행하는 서버 및 발급 CA에 적용되므로, System Center Configuration Manager에서 인증서를 해지할 수 있습니다.<br /><br /> SSL(보안 모범 사례)이 필요하도록 네트워크 장치 등록 서비스를 구성한 경우 연결 장치에서 CRL(인증서 해지 목록)에 액세스하여 서버 인증서의 유효성을 검사할 수 있어야 합니다.<br /><br /> Windows Server 2012 R2의 네트워크 장치 등록 서비스에 대한 자세한 내용은 [Using a Policy Module with the Network Device Enrollment Service(네트워크 장치 등록 서비스와 함께 정책 모듈 사용)](http://go.microsoft.com/fwlink/p/?LinkId=328657)를 참조하세요.|  
|발급 CA에서 Windows Server 2008 R2를 실행하는 경우 SCEP 갱신 요청을 위해 서버에 핫픽스 필요|발급 CA 컴퓨터에 아직 핫픽스를 설치하지 않은 경우 핫픽스를 설치하세요. 자세한 내용은 Microsoft 기술 자료의 [2483564: NDES를 사용하여 인증서를 관리하는 경우 Windows Server 2008 R2에서 SCEP 인증서에 대한 요청 갱신이 실패함](http://go.microsoft.com/fwlink/?LinkId=311945) 문서를 참조하세요.|  
|PKI 클라이언트 인증 인증서 및 내보낸 루트 CA 인증서|이 인증서는 System Center Configuration Manager에 대해 네트워크 장치 등록 서비스를 실행하는 서버를 인증합니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.|  
|지원되는 장치 운영 체제|iOS, Windows 8.1, Windows RT 8.1, Windows 10 및 Android 운영 체제를 실행하는 장치에 인증서 프로필을 배포할 수 있습니다.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  

|종속성|추가 정보|  
|----------------|----------------------|  
|인증서 등록 지점 사이트 시스템 역할|인증서 프로필을 사용하려면 먼저 인증서 등록 지점 사이트 시스템 역할을 설치해야 합니다. 이 역할은 System Center Configuration Manager 데이터베이스, System Center Configuration Manager 사이트 서버 및 System Center Configuration Manager 정책 모듈과 통신합니다.<br /><br /> 이 사이트 시스템 역할의 시스템 요구 사항 및 계층 내 역할 설치 위치에 대한 자세한 내용은 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md) 항목의 **사이트 시스템 요구 사항** 섹션을 참조하세요.<br /><br /> 네트워크 장치 등록 서비스를 실행하는 동일한 서버에 인증서 등록 지점을 설치하지 않아야 합니다.|  
|Active Directory 인증서 서비스용 네트워크 장치 등록 서비스 역할 서비스를 실행하는 서버에 설치된 System Center Configuration Manager 정책 모듈|인증서 프로필을 배포하려면 System Center Configuration Manager 정책 모듈을 설치해야 합니다. 이 정책 모듈은 System Center Configuration Manager 설치 미디어에서 찾을 수 있습니다.|  
|검색 데이터|인증서 주체 및 주체 대체 이름 값은 System Center Configuration Manager에서 제공하며 검색에서 수집된 정보에서 가져옵니다.<br /><br /> 사용자 인증서: Active Directory 사용자 검색<br /><br /> 컴퓨터 인증서: Active Directory 시스템 검색 및 네트워크 검색|  
|인증서 프로필을 관리하는 특정 보안 권한|회사 리소스 액세스 설정(예: 인증서 프로필, Wi-Fi 프로필 및 VPN 프로필)을 관리하려면 다음과 같은 보안 권한이 있어야 합니다.<br /><br /> 인증서 프로필에 대한 경고 및 보고서를 보고 관리하려면 **경고**개체에 대한 **만들기**, **삭제**, **수정**, **보고서 수정**, **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> 인증서 프로필을 만들고 관리하려면 **인증서 프로필**개체에 대한 **작성자 정책**, **보고서 수정** , **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> Wi-Fi, 인증서 및 VPN 프로필 배포를 관리하려면 **컬렉션**개체에 대한 **구성 정책 배포**, **클라이언트 상태 알림 수정**, **읽기** 및 **리소스 읽기** 권한이 필요합니다.<br /><br /> 모든 구성 정책을 관리하려면 **구성 정책**개체에 대한 **만들기**, **삭제**, **수정** , **읽기** 및 **보안 범위 설정** 권한이 필요합니다.<br /><br /> 인증서 프로필과 관련된 쿼리를 실행하려면 **쿼리** 개체에 대한 **읽기** 권한이 필요합니다.<br /><br /> System Center Configuration Manager 콘솔에서 인증서 프로필 정보를 보려면 **사이트** 개체에 대한 **읽기** 권한이 필요합니다.<br /><br /> 인증서 프로필에 대한 상태 메시지를 보려면 **상태 메시지** 개체에 대한 **읽기** 권한이 필요합니다.<br /><br /> 신뢰할 수 있는 CA 인증서 프로필을 만들고 수정하려면 **신뢰할 수 있는 CA 인증서 프로필**개체에 대한 **작성자 정책**, **보고서 수정** , **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> VPN 프로필을 만들고 관리하려면 **VPN 프로필**개체에 대한 **작성자 정책**, **보고서 수정** , **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> Wi-Fi 프로필을 만들고 관리하려면: **Wi-Fi 프로필**개체에 대한 **작성자 정책**, **보고서 수정** , **읽기** 및 **보고서 실행** 권한이 필요합니다.<br /><br /> **회사 리소스 액세스 관리자** 보안 역할에는 System Center Configuration Manager에서 인증서 프로필을 관리하는 데 필요한 이와 같은 권한이 포함됩니다. 자세한 내용은 [System Center Configuration Manager의 보안 구성](../../core/plan-design/security/configure-security.md) 항목의 **역할 기반 관리 구성** 섹션을 참조하세요.|  

