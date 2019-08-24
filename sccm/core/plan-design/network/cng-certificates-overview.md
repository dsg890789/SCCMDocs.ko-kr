---
title: CNG 인증서 개요
titleSuffix: Configuration Manager
description: 'Configuration Manager 클라이언트 및 서버에 대한 CNG(Cryptography: Next Generation) 인증서 지원에 대해 알아봅니다.'
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: dba904ae-7c44-46db-ae63-999b9821cb46
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36db15b340a4122d44e60ee5a2a3eec101c16556
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65499382"
---
# <a name="cng-certificates-overview"></a>CNG 인증서 개요
<!-- 1356191 --> 

Configuration Manager는 Cryptography: Next Generation(CNG) 인증서를 지원합니다. Configuration Manager 클라이언트는 CNG KSP(키 스토리지 공급자)의 프라이빗 키와 함께 PKI 클라이언트 인증 인증서를 사용할 수 있습니다. Configuration Manager 클라이언트는 KSP 지원을 통해 PKI 클라이언트 인증 인증서용 TPM KSP와 같은 하드웨어 기반 프라이빗 키를 지원합니다.

## <a name="supported-scenarios"></a>지원되는 시나리오
[CNG(Cryptography API: Next Generation)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) 인증서 템플릿을 사용할 수 있는 시나리오는 다음과 같습니다.

- 클라이언트 등록 및 HTTPS 관리 지점과의 커뮤니케이션   
- HTTPS 배포 지점을 사용하여 소프트웨어 배포 및 애플리케이션 배포   
- 운영 체제 배포  
- 클라이언트 메시지 SDK(최신 업데이트 포함) 및 ISV 프록시   
- 클라우드 관리 게이트웨이 구성  

1802 버전부터는 HTTPS 지원 서버 역할에 CNG 인증서를 사용합니다. <!-- 1357314 -->   
- 관리 지점
- 배포 지점
- 소프트웨어 업데이트 지점
- 상태 마이그레이션 지점     

1806 버전부터는 HTTPS 지원 서버 역할에 CNG 인증서를 사용합니다.

- Configuration Manager 정책 모듈을 사용하는 NDES 서버를 포함한 인증서 등록 지점 <!--1357314-->

> [!NOTE]
> CNG는 이전 버전의 CAPI(Crypto API)와 호환됩니다. 클라이언트에서 CNG 지원을 사용하도록 설정된 경우에도 CAPI 인증서가 계속 지원됩니다.

## <a name="unsupported-scenarios"></a>지원되지 않는 시나리오

다음 시나리오는 현재 지원되지 않습니다.

- 다음 서버 역할은 IIS(인터넷 정보 서비스)의 웹 사이트에 바인딩된 CNG 인증서를 사용하여 HTTPS 모드로 설치된 경우 작동하지 않습니다. 
    - 애플리케이션 카탈로그 웹 서비스
    - 애플리케이션 카탈로그 웹 사이트
    - 등록 지점  
    - 등록 프록시 지점  

- 소프트웨어 센터에서는 사용자 또는 사용자 그룹 컬렉션에 배포된 애플리케이션 및 패키지를 사용 가능한 것으로 표시하지 않습니다.

- CNG 인증서를 사용하여 클라우드 배포 지점을 만듭니다.

- NDES 정책 모듈에서 클라이언트 인증에 CNG 인증서를 사용하는 경우 인증서 등록 지점과의 통신이 실패합니다. 
    - Configuration Manager 버전 1806부터 지원됩니다.

- 작업 순서 미디어를 만들 때 CNG 인증서를 지정하면 마법사가 부팅 가능한 미디어를 만드는 데 실패합니다.
    - Configuration Manager 버전 1806부터 지원됩니다.

## <a name="to-use-cng-certificates"></a>CNG 인증서 사용

CNG 인증서를 사용하려면 CA(인증 기관)가 대상 컴퓨터에 대한 CNG 인증서 서식 파일을 제공해야 합니다. 서식 파일의 세부 사항은 시나리오에 따라 다릅니다. 그러나 다음 특성이 필요합니다.

- **호환성** 탭

    - **인증 기관**은 Windows Server 2008 이상이어야 합니다. (Windows Server 2012 권장)

    - **인증서 수신자**는 Windows Vista/Server 2008 이상이어야 합니다. (Windows 8/Windows Server 2012 권장)

- **암호화** 탭

    - **공급자 범주**는 **주요 스토리지 공급자**여야 합니다. (필수)
    - **요청 시 다음 공급자 중 하나 사용:** 은 **Microsoft 소프트웨어 키 스토리지 공급자**여야 합니다. 

> [!NOTE]
> 사용자 환경 또는 조직의 요구 사항이 다를 수 있습니다. PKI 전문가에게 문의하세요. 고려해야 할 중요한 점은 인증서 CNG를 활용하기 위해 템플릿에서 키 스토리지 공급자를 사용해야 한다는 것입니다.

최상의 결과를 위해 Active Directory 정보에서 제목 이름을 빌드하는 것이 좋습니다. **주체 이름 형식**에 DNS 이름을 사용하고 DNS 이름을 대체 주체 이름에 포함시킵니다. 그렇지 않으면 디바이스가 인증서 프로필에 등록할 때 이 정보를 제공해야 합니다.
