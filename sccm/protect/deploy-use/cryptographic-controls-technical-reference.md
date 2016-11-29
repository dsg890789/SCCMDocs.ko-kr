---
title: "암호화 제어 기술 참조 | System Center Configuration Manager"
description: "공격을 방지하여 System Center Configuration Manager의 데이터를 읽을 수 없도록 서명 및 암호화하는 방법에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c63dcc5-a1bd-4037-959a-2e6ba0fd1b2c
caps.latest.revision: 6
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 354289f980836f10ebfc770b2408ba02dcb0eecb


---
# <a name="cryptographic-controls-technical-reference"></a>암호화 컨트롤 기술 참조

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager는 서명 및 암호화를 사용하여 Configuration Manager 계층 구조의 장치 관리를 보호합니다. 서명된 데이터가 전송 중에 변경된 경우 무시됩니다. 암호화는 공격자가 네트워크 프로토콜 분석기로 데이터를 읽지 못하도록 방지합니다.  

 Configuration Manager에서 서명에 사용하는 기본 해싱 알고리즘은 SHA-256입니다. 서로 통신하는 두 Configuration Manager 사이트는 SHA-256을 사용하여 통신에 서명합니다. Configuration Manager에서 구현되는 기본 암호화 알고리즘은 3DES입니다. 이 방식은 Configuration Manager 데이터베이스에 데이터를 저장하고 클라이언트 HTTP 통신에 사용됩니다. HTTPS를 통해 클라이언트 통신을 사용할 경우 PKI(공개 키 인프라)를 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../core/plan-design/network/pki-certificate-requirements.md)에 문서화된 최대 해시 알고리즘 및 키 길이를 적용해 RSA 인증서를 사용하도록 구성할 수 있습니다.  

 Configuration Manager는 Windows 기반 운영 체제의 암호화 작업 대부분에서 Windows CryptoAPI 라이브러리 rsaenh.dll의 SHA-2, 3DES 및 AES 및 RSA 알고리즘을 사용합니다.  

> [!IMPORTANT]  
>  SSL 취약성에 대응하기 위한 권장 변경 내용에 대한 내용은 [SSL 취약점 정보](#about-ssl-vulnerabilities)를 참조하세요.  

##  <a name="cryptographic-controls-for-configuration-manager-operations"></a>Configuration Manager 작업에 대한 암호화 컨트롤  
 Configuration Manager에서 PKI 인증서 사용 여부에 관계없이 Configuration Manager의 정보를 서명 및 암호화할 수 있습니다.  

### <a name="policy-signing-and-encryption"></a>정책 서명 및 암호화  
 클라이언트 정책 할당은 자체 서명된 사이트 서버 서명 인증서에 의해 서명되므로, 무단 변경된 정책을 보내는 손상된 관리 지점으로 인해 발생할 수 있는 보안 위험을 사전에 방지할 수 있습니다. 이와 같은 환경에서는 인터넷 통신에 노출되는 관리 지점이 필요하기 때문에 이는 인터넷 기반 클라이언트 관리를 사용하는 경우에 중요합니다.  

 정책은 중요한 데이터가 포함되어 있을 경우 3DES로 암호화됩니다. 중요한 데이터가 포함된 정책은 인증된 클라이언트에만 전송됩니다. 중요한 데이터가 없는 정책은 암호화되지 않습니다.  

 정책은 클라이언트에 저장될 때 DPAPI(Data Protection Application Programming Interface)를 사용하여 암호화됩니다.  

### <a name="policy-hashing"></a>정책 해시  
 Configuration Manager 클라이언트에서 정책을 요청할 때는 먼저 정책 할당을 가져오므로 해당되는 정책을 식별할 수 있습니다. 클라이언트는 그 후에 해당 정책 본문만 요청합니다. 각 정책 할당에는 해당 정책 본문에 대해 계산된 해시가 포함되어 있습니다. 클라이언트는 해당되는 정책 본문을 검색한 다음 본문에 대한 해시를 계산합니다. 다운로드된 정책 본문의 해시가 정책 할당의 해시와 일치하지 않으면 클라이언트는 해당 정책 본문을 삭제합니다.  

 정책에 대한 해시 알고리즘은 SHA-1 및 SHA-256입니다.  

### <a name="content-hashing"></a>콘텐츠 해시  
 사이트 서버의 배포 관리자 서비스는 모든 패키지에 대해 콘텐츠 파일을 해싱합니다. 정책 공급자는 소프트웨어 배포 정책에 해시를 포함합니다. Configuration Manager 클라이언트는 콘텐츠를 다운로드할 때 해시를 로컬로 다시 생성하여 정책에서 제공된 해시와 비교합니다. 해시가 서로 일치하면 콘텐츠는 변경되지 않은 것이므로 클라이언트에 의해 설치됩니다. 콘텐츠 중 한 바이트라도 변경되었으면 해시가 서로 일치하지 않으며 소프트웨어는 설치되지 않습니다. 이러한 검사를 통해 실제 콘텐츠를 정책과 비교해 확인해볼 수 있으므로 올바른 소프트웨어를 설치할 수 있습니다.  

 콘텐츠의 기본 해싱 알고리즘은 SHA-256입니다. 이 기본값을 변경하려면 Configuration Manager SDK(소프트웨어 개발 키트)용 설명서를 참조하세요.  

 모든 장치가 콘텐츠 해싱을 지원하는 것은 아닙니다. 예외는 다음과 같습니다.  

-   App-V 콘텐츠를 스트리밍하는 Windows 클라이언트.  

-   Windows Phone 클라이언트, 그러나 이러한 클라이언트는 신뢰할 수 있는 원본에서 서명된 응용 프로그램의 서명을 확인합니다.  

-   Windows RT 클라이언트, 그러나 이러한 클라이언트는 신뢰할 수 있는 원본에서 서명된 응용 프로그램의 서명을 확인하고 PFN(Package Full Name) 유효성 검사도 사용합니다.  

-   iOS, 그러나 이러한 장치는 신뢰할 수 있는 원본의 개발자 인증서에서 서명된 응용 프로그램의 서명을 확인합니다.  

-   Nokia 클라이언트, 그러나 이러한 클라이언트는 자체 서명된 인증서를 사용하는 응용 프로그램의 서명을 확인합니다. 또는 신뢰할 수 있는 원본의 인증서의 서명과 인증서는 Nokia SIS(Symbian Installation Source) 응용 프로그램을 서명할 수 있습니다.  

-   Android: 그 밖에, 이러한 장치는 응용 프로그램 설치에 서명 유효성 검사를 사용하지 않습니다.  

-   SHA-256을 지원하지 않는 Linux 및 UNIX 버전에서 실행되는 클라이언트. 자세한 내용은 [System Center Configuration Manager에서 Linux 및 UNIX 컴퓨터에 클라이언트 배포 계획](../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md)을 참조하세요.  

### <a name="inventory-signing-and-encryption"></a>인벤토리 서명 및 암호화  
 클라이언트에서 관리 지점에 보내는 인벤토리는 클라이언트가 HTTP 또는 HTTPS 중 어느 방식으로 관리 지점과 통신하는지에 상관없이 장치에서 항상 서명됩니다. HTTP가 사용될 경우 데이터를 암호화하도록 선택할 수 있으며 이는 보안 모범 사례에 해당합니다.  

### <a name="state-migration-encryption"></a>상태 마이그레이션 암호화  
 운영 체제 배포용 상태 마이그레이션 지점에 저장된 데이터는 USMT(사용자 환경 마이그레이션 도구)에서 3DES를 사용하여 항상 암호화됩니다.  

### <a name="encryption-for-multicast-packages-to-deploy-operating-systems"></a>운영 체제 배포용 멀티캐스트 패키지에 대한 암호화  
 모든 운영 체제 배포 패키지의 경우 패키지가 멀티캐스트를 통해 컴퓨터에 전송될 때 암호화를 사용하도록 설정할 수 있습니다. 이때 AES(고급 암호화 표준)의 암호화가 사용됩니다. 암호화를 사용하는 경우 추가 인증서 구성은 필요하지 않습니다. 멀티캐스트 사용 배포 지점은 패키지 암호화를 위한 대칭 키를 자동으로 생성합니다. 각 패키지에는 서로 다른 암호화 키가 있습니다. 이 키는 표준 Windows API를 사용하여 멀티캐스트 사용 배포 지점에 저장됩니다. 클라이언트에서 멀티캐스트 세션에 연결할 경우 PKI가 발급한 클라이언트 인증 인증서(클라이언트가 HTTPS 사용 시) 또는 자체 서명된 인증서(클라이언트가 HTTP 사용 시)로 암호화된 채널을 통해 키 교환이 발생합니다. 클라이언트는 키를 멀티캐스트 세션의 지속 기간 동안만 메모리에 저장합니다.  

### <a name="encryption-for-media-to-deploy-operating-systems"></a>운영 체제 배포용 미디어에 대한 암호화  
 미디어를 사용하여 운영 체제를 배포하고 미디어 보호를 위한 암호를 지정하는 경우 환경 변수는 AES를 사용하여 암호화됩니다. 패키지 및 응용 프로그램 콘텐츠를 포함해 미디어의 다른 데이터는 암호화되지 않습니다.  

### <a name="encryption-for-content-that-is-hosted-on-cloud-based-distribution-points"></a>클라우드 기반 배포 지점에서 호스트되는 콘텐츠에 대한 암호화  
 System Center 2012 Configuration Manager SP1부터는 클라우드 기반 배포 지점을 사용하는 경우 이 배포 지점에 업로드하는 콘텐츠는 키 크기가 256비트인 AES(Advanced Encryption Standard)를 사용하여 암호화됩니다. 콘텐츠는 업데이트할 때마다 다시 암호화됩니다. 클라이언트에서 다운로드하는 콘텐츠는 HTTPS 연결로 암호화 및 보호됩니다.  

### <a name="signing-in-software-updates"></a>소프트웨어 업데이트 서명  
 모든 소프트웨어 업데이트는 무단 변경을 방지하기 위해 신뢰할 수 있는 게시자에서 서명되어야 합니다. 클라이언트 컴퓨터에서 WUA(Windows Update 에이전트)는 카탈로그에서 업데이트를 검색하지만 로컬 컴퓨터의 신뢰할 수 있는 게시자 저장소에서 디지털 인증서를 찾지 못하면 업데이트를 설치하지 않습니다. 자체 서명된 인증서(예: WSUS Publishers Self-signed)가 업데이트 카탈로그를 게시하는 데 사용된 경우, 해당 인증서는 로컬 컴퓨터의 신뢰할 수 있는 루트 인증 기관 인증서 저장소 안에 있어야 유효성이 확인될 수 있습니다. 또한 WUA는 **인트라넷 Microsoft 업데이트 서비스 위치의 서명된 콘텐츠 허용 그룹 정책** 설정이 로컬 컴퓨터에서 사용하도록 설정되어 있는지 확인합니다. 업데이트 게시자로 생성 및 게시된 업데이트를 WUA에서 검색할 수 있으려면 이 정책 설정이 사용하도록 설정되어 있어야 합니다.  

 소프트웨어 업데이트가 System Center 업데이트 게시자에서 게시되면 디지털 인증서는 이 소프트웨어 업데이트가 업데이트 서버에 게시될 때 서명합니다. PKI 인증서를 지정하거나 업데이트 게시자를 구성하면 소프트웨어 업데이트를 서명할 자체 서명된 인증서를 생성할 수 있습니다.  

### <a name="signed-configuration-data-for-compliance-settings"></a>준수 설정을 위한 서명된 구성 데이터  
 사용자가 구성 데이터를 가져오면 Configuration Manager에서 파일의 디지털 서명을 확인합니다. 파일이 서명되지 않았거나 디지털 서명 확인이 실패하면 경고가 생성되고 가져오기를 계속할 것인지 묻는 메시지가 표시됩니다. 파일의 게시자 및 무결성을 명백히 신뢰하는 경우에만 구성 데이터의 가져오기를 계속하세요.  

### <a name="encryption-and-hashing-for-client-notification"></a>클라이언트 알림에 대한 암호화 및 해시  
 클라이언트 알림을 사용하는 경우 모든 통신에서는 TLS를 비롯해 서버 및 클라이언트 운영 체제가 서로 협상할 수 있는 최고 수준의 암호화를 사용합니다. 예를 들어 Windows 7을 실행하는 클라이언트 컴퓨터와 Windows Server 2008 R2를 실행하는 관리 지점은 128비트 AES 암호화를 지원하는 반면, 같은 관리 지점에 대해 Vista를 실행하는 클라이언트 컴퓨터는 3DES 암호화를 통해 하위 수준으로 협상합니다. 클라이언트 알림 중 전송되는 패킷을 해싱할 때 이와 동일한 협상이 발생하며, 이 경우 SHA-1 또는 SHA-2가 사용됩니다.  

##  <a name="certificates-used-by-configuration-manager"></a>Configuration Manager에서 사용되는 인증서  
 Configuration Manager에서 사용될 수 있는 PKI(공개 키 인프라) 인증서의 목록, 특정 요구 사항 또는 제한 사항, 인증서의 사용 방식은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요. 이 목록에는 지원되는 해시 알고리즘 및 키 길이가 포함되어 있습니다. 대부분의 인증서는 SHA-256과 2048비트 키 길이를 지원합니다.  

> [!NOTE]  
>  Configuration Manager에서 사용하는 모든 인증서는 주체 이름 또는 주체 대체 이름에 1바이트 문자만 포함해야 합니다.  

 PKI 인증서는 다음과 같은 시나리오에서 필요합니다.  

-   인터넷상의 Configuration Manager 클라이언트를 관리하는 경우  

-   모바일 장치의 Configuration Manager 클라이언트를 관리하는 경우  

-   Mac 컴퓨터를 관리합니다.  

-   클라우드 기반 배포 지점을 사용합니다.  

-   대역 외 Intel AMT 기반 컴퓨터를 관리합니다.  

 인증, 서명 또는 암호화를 위해 인증서가 필요한 대부분의 다른 Configuration Manager 통신의 경우 Configuration Manager는 사용 가능한 PKI 인증서를 자동으로 사용합니다. PKI 인증서를 사용할 수 없는 경우 Configuration Manager에서 자체 서명된 인증서를 생성합니다.  

 Configuration Manager는 Exchange Server 커넥터를 사용하여 모바일 장치를 관리할 경우에는 PKI 인증서를 사용하지 않습니다.  

### <a name="mobile-device-management-and-pki-certificates"></a>모바일 장치 관리 및 PKI 인증서  
 모바일 장치가 통신사에 의해 잠기지 않은 경우 Configuration Manager 또는 Microsoft Intune을 사용하여 클라이언트 인증서를 요청 및 설치할 수 있습니다. 이 인증서는 모바일 장치의 클라이언트와 Configuration Manager 사이트 시스템 또는 Microsoft Intune 서비스 간의 상호 인증을 제공합니다. 모바일 장치가 잠겨 있으면 Configuration Manager 또는 Intune을 사용하여 인증서를 배포할 수 없습니다.  

 모바일 장치에 대해 하드웨어 인벤토리를 사용하도록 설정하는 경우 Configuration Manager 또는 Microsoft Intune에서도 모바일 장치에 설치된 인증서의 인벤토리를 만듭니다.  

### <a name="out-of-band-management-and-pki-certificates"></a>대역 외 관리 및 PKI 인증서  
 Intel AMT 기반 컴퓨터용 대역 외 관리에서는 두 가지 유형 이상의 PKI 발급 인증서, 즉 AMT 프로비전 인증서 및 웹 서버 인증서를 사용합니다.  

 대역 외 서비스 지점은 AMT 프로비전 인증서를 사용하여 컴퓨터에서 대역 외 관리를 사용하도록 준비합니다. 프로비전될 AMT 기반 컴퓨터는 대역 외 관리 지점에서 제공하는 인증서를 신뢰해야 합니다. 기본적으로 AMT 기반 컴퓨터는 컴퓨터 제조업체에 의해 VeriSign, Go Daddy, Comodo, Starfield 등의 외부 CA(인증 기관)를 사용하도록 구성됩니다. 외부 CA 중 한 곳의 프로비전 인증서를 구입하고 Configuration Manager에서 이 프로비전 인증서를 사용하도록 구성한 경우 AMT 기반 컴퓨터는 해당 프로비전 인증서의 CA를 신뢰하며 프로비전은 올바르게 작동합니다. 그러나, 자신만의 내부 CA를 사용하여 AMT 프로비전 인증서를 발급하는 것이 보안 모범 사례입니다.  

 AMT 기반 컴퓨터는 펌웨어 내에서 웹 서버 구성 요소를 실행하며 해당 웹 서버 구성 요소는 TLS(Transport Layer Security)를 사용하여 대역 외 서비스 지점과 함께 통신 채널을 암호화합니다. AMT BIOS에는 인증서를 수동으로 구성할 수 있는 사용자 인터페이스가 없으므로 요청하는 AMT 기반 컴퓨터의 인증서 요청을 자동으로 승인하는 Microsoft Enterprise 인증 기관이 있어야만 합니다. 요청에서는 요청 형식으로 PKCS#10을 사용하며, 이 형식은 인증서 정보를 AMT 기반 컴퓨터에 전송하는 데 PKCS#7을 사용합니다.  

 AMT 기반 컴퓨터는 자신을 관리하는 컴퓨터에 대해 인증되지만 해당 컴퓨터에는 상응하는 클라이언트 PKI 인증서가 없습니다. 그 대신 이러한 통신에서는 Kerberos 또는 HTTP 다이제스트 인증을 사용합니다. 사용되는 HTTP 다이제스트는 TLS를 통해 암호화됩니다.  

 추가적 유형의 인증서인 802.1X 인증 유선 네트워크 및 무선 네트워크용 선택적 클라이언트 인증서는 대역 외 AMT 기반 컴퓨터를 관리하는 데 필요할 수 있습니다. 클라이언트 인증서는 AMT 기반 컴퓨터에 RADIUS 서버에 대한 인증을 위해 필요할 수 있습니다. RADIUS 서버가 EAP-TLS 인증에 대해 구성된 경우 클라이언트 인증서가 항상 필요합니다. RADIUS 서버가 EAP-TTLS/MSCHAPv2 또는 PEAPv0/EAP-MSCHAPv2에 대해 구성된 경우 RADIUS 구성에서 클라이언트 인증서의 필요 여부를 지정합니다. 이 인증서는 AMT 기반 컴퓨터에서 웹 서버 인증서 요청과 동일한 프로세스를 사용하여 요청됩니다.  

### <a name="operating-system-deployment-and-pki-certificates"></a>운영 체제 배포 및 PKI 인증서  
 Configuration Manager를 사용하여 운영 체제를 배포하고 관리 지점에 HTTPS 클라이언트 연결이 필요한 경우 클라이언트 컴퓨터에도 관리 지점과 통신하기 위한 인증서가 있어야 하며, 이는 작업 순서 미디어 또는 PXE 사용 배포 지점에서 부팅하는 것과 같은 전환 단계에서도 마찬가지입니다. 이러한 시나리오를 지원하려면 PKI 클라이언트 인증 인증서를 만들어 개인 키와 함께 내보낸 다음 사이트 서버 속성으로 가져오고 관리 지점의 신뢰할 수 있는 루트 CA 인증서도 추가해야 합니다.  

 부팅 가능한 미디어를 만들 경우에는 해당 미디어를 만들 때 클라이언트 인증 인증서를 가져오세요. 부팅 가능한 미디어에 암호를 구성하면 작업 순서에 구성된 개인 키 및 기타 중요한 데이터를 보호할 수 있습니다. 부팅 가능한 미디어에서 부팅하는 모든 컴퓨터는 클라이언트 정책 요청과 같은 클라이언트 기능의 필요에 따라 관리 지점에 동일한 인증서를 제공합니다.  

 PXE 부트를 사용할 경우, 클라이언트 인증 인증서를 PXE 사용 배포 지점으로 가져오게 되고 이 PXE 사용 배포 지점에서 부팅하는 모든 클라이언트에 대해 동일한 인증서가 사용됩니다. 보안 모범 사례에 따라 작업 순서 내의 개인 키 및 기타 중요한 데이터를 보호하려면 컴퓨터를 PXE 서비스에 연결하는 사용자는 암호를 입력해야 합니다.  

 이러한 클라이언트 인증 인증서 중 하나라도 손상되면 **보안** 노드의 **관리** 작업 영역에 있는 **인증서** 노드에서 해당 인증서를 차단하세요. 이와 같은 인증서를 관리하려면 **운영 체제 배포 인증서 관리** 권한이 있어야 합니다.  

 운영 체제가 배포되고 Configuration Manager가 설치된 후 클라이언트는 HTTPS 클라이언트 통신을 수행하려면 자체 PKI 클라이언트 인증 인증서가 있어야 합니다.  

### <a name="isv-proxy-solutions-and-pki-certificates"></a>ISV 프록시 솔루션과 PKI 인증서  
 ISV(Independent Software Vendor)는 Configuration Manager를 확장하는 응용 프로그램을 만들 수 있습니다. 예를 들어 ISV는 Macintosh 또는 UNIX 컴퓨터와 같은 비 Windows 클라이언트 플랫폼을 지원하는 확장 프로그램을 만들 수 있습니다. 그러나 사이트 시스템에서 HTTPS 클라이언트 연결을 사용해야 하는 경우 이러한 클라이언트는 사이트와 통신하는 데 PKI 인증서도 사용해야 합니다. Configuration Manager에는 ISV 프록시 클라이언트와 관리 지점이 통신할 수 있도록 ISV 프록시에 인증서를 할당하는 기능이 포함되어 있습니다. ISV 프록시 인증서가 필요한 확장을 사용하는 경우 해당 제품용 설명서를 참조하세요. ISV 프록시 인증서를 만드는 방법에 대한 자세한 내용은 Configuration Manager SDK(Software Developer Kit)를 참조하세요.  

 ISV 인증서가 손상되면 **보안** 노드의 **관리** 작업 영역에 있는 **인증서** 노드에서 해당 인증서를 차단하세요.  

### <a name="asset-intelligence-and-certificates"></a>Asset Intelligence 및 인증서  
 Configuration Manager는 Asset Intelligence 동기화 지점이 Microsoft에 연결하는 데 사용하는 X.509 인증서와 함께 설치됩니다. Configuration Manager에서는 이 인증서를 사용하여 Microsoft 인증서 서비스에서 클라이언트 인증 인증서를 요청합니다. 클라이언트 인증 인증서는 Asset Intelligence 동기화 지점 사이트 시스템 서버에 설치되며 서버를 Microsoft에 대해 인증하는 데 사용됩니다. Configuration Manager에서는 클라이언트 인증 인증서를 사용하여 Asset Intelligence 카탈로그를 다운로드하고 소프트웨어 타이틀을 업로드합니다.  

 이 인증서의 키 길이는 1024비트입니다.  

### <a name="cloud-based-distribution-points-and-certificates"></a>클라우드 기반 배포 지점 및 인증서  
 System Center 2012 Configuration Manager SP1부터는 클라우드 기반 배포 지점에 사용자가 Microsoft Azure에 업로드하는 자체 서명 또는 PKI 관리 인증서가 필요합니다. 이 관리 인증서에는 서버 인증 기능과 2048비트의 인증서 키 길이가 필요합니다. 또한 각 클라우드 기반 배포 지점에 대해 서비스 인증서를 구성해야 하며, 이 인증서는 자체 서명될 수 없지만 역시 서버 인증 기능 및 최소 2048비트의 인증서 키 길이를 포함합니다.  

> [!NOTE]  
>  자체 서명된 관리 인증서는 테스트용으로만 사용되며 프로덕션 네트워크에서는 사용할 수 없습니다.  

 클라이언트에는 클라우드 기반 배포 지점을 사용하기 위한 클라이언트 PKI 인증서가 필요하지 않습니다. 클라이언트는 자체 서명된 인증서나 클라이언트 PKI 인증서를 사용하여 관리에 대한 인증을 받습니다. 그 후 관리 지점은 클라이언트에 Configuration Manager 액세스 토큰을 발급하며, 클라이언트는 이 액세스 토큰을 클라우드 기반 배포 지점에 제공합니다. 토큰은 8시간 동안 유효합니다.  

### <a name="the-microsoft-intune-connector-and-certificates"></a>Microsoft Intune 커넥터 및 인증서  
 Microsoft Intune에서 모바일 장치를 등록할 때 사용자는 Microsoft Intune 커넥터를 만들어 해당 모바일 장치를 Configuration Manager에서 관리할 수 있습니다. 이 커넥터는 클라이언트 인증 기능과 함께 PKI 인증서를 사용하여 Configuration Manager를 Microsoft Intune에 대해 인증하고 SSL을 사용하여 상호 간에 모든 정보를 전송합니다. 인증서 키 크기는 2048비트이며 SHA-1 해시 알고리즘을 사용합니다.  

 커넥터를 설치할 때 테스트용 로드 키를 위한 서명 인증서가 생성되어 사이트 서버에 저장되며, SCEP(Simple Certificate Enrollment Protocol) 챌린지를 암호화하기 위해 암호화 인증서가 생성되어 인증서 등록 지점에 저장됩니다. 또한 이러한 인증서의 키 크기는 2048비트이고 SHA-1 해시 알고리즘을 사용합니다.  

 Intune은 모바일 장치를 등록할 때 PKI 인증서를 해당 모바일 장치에 설치합니다. 이 인증서에는 클라이언트 인증 기능이 있으며 2048비트의 키 크기와 SHA-1 해시 알고리즘이 사용됩니다.  

 이러한 PKI 인증서는 Microsoft Intune에 의해 자동으로 요청, 생성 및 설치됩니다.  

### <a name="crl-checking-for-pki-certificates"></a>PKI 인증서에 대한 CRL 확인  
 PKI CRL(인증서 해지 목록)은 관리 및 처리 부하를 증가시키지만 더욱 안전합니다. 그러나, CRL 확인이 사용하도록 설정되었지만 CRL을 액세스할 수 없는 경우 PKI 연결은 실패합니다. 자세한 내용은 [System Center Configuration Manager의 보안 및 개인 정보](../../core/plan-design/security/security-and-privacy.md)를 참조하세요.  

 CRL(인증서 해지 목록) 확인은 IIS에서 기본값으로 사용 가능하므로 PKI 배포에 CRL을 사용하는 경우 IIS를 실행하는 대부분의 Configuration Manager 사이트 시스템에는 더 이상 구성해야 할 항목이 없습니다. 그러나 CRL 확인에서 소프트웨어 업데이트 파일의 서명을 확인하도록 설정하는 수동 단계가 필요한 소프트웨어 업데이트는 예외입니다.  

 CRL 확인은 HTTPS 클라이언트 연결을 사용하는 클라이언트 컴퓨터에 대해서는 기본값으로 사용 가능합니다. CRL 확인은 대역 외 관리 콘솔을 실행하여 AMT 기반 컴퓨터에 연결하는 경우 기본값으로 사용 가능하지 않으며, 필요하면 이 옵션을 사용하도록 설정할 수 있습니다. Configuration Manager SP1 이상 버전에서는 Mac 컴퓨터의 클라이언트에 대해 CRL 확인을 사용하지 않도록 설정할 수 없습니다.  

 CRL 확인은 Configuration Manager에서 다음 연결에 대해 지원되지 않습니다.  

-   서버 간 연결  

-   Configuration Manager에서 등록된 모바일 장치  

-   Microsoft Intune에서 등록한 모바일 장치  

##  <a name="cryptographic-controls-for-server-communication"></a>서버 통신을 위한 암호화 컨트롤  
 Configuration Manager에서는 서버 통신에 다음과 같은 암호화 컨트롤을 사용합니다.  

### <a name="server-communication-within-a-site"></a>사이트 내 서버 통신  
 각 사이트 시스템 서버에서는 인증서를 사용하여 동일한 Configuration Manager 사이트에 있는 다른 사이트 시스템에 데이터를 전송합니다. 일부 사이트 시스템 역할에서도 인증에 인증서를 사용합니다. 예를 들어 한 서버에 등록 프록시 지점을 설치하고 다른 서버에 등록 지점을 설치하는 경우 두 서버는 이러한 ID 인증서를 사용하여 서로를 인증할 수 있습니다. Configuration Manager에서 이 통신에 인증서를 사용할 때 서버 인증 기능이 있는 사용 가능한 PKI 인증서가 있는 경우 Configuration Manager에서는 자동으로 해당 인증서를 사용하며, 인증서가 없는 경우에는 Configuration Manager에서 자체 서명된 인증서를 생성합니다. 이 자체 서명된 인증서는 서버 인증 기능을 포함하고 SHA-256을 사용하며, 키 길이는 2048비트입니다. Configuration Manager는 사이트 시스템을 신뢰해야 할 수 있는 다른 사이트 시스템 서버의 신뢰할 수 있는 사용자 저장소에 인증서를 복사합니다. 그 후 사이트 시스템은 이러한 인증서와 PeerTrust를 사용하여 서로를 신뢰할 수 있습니다.  

 각 사이트 시스템 서버에 대한 이 인증서 외에, Configuration Manager에서는 대부분의 사이트 시스템 역할에 대해 자체 서명된 인증서를 생성합니다. 한 사이트 안에 사이트 시스템 역할의 인스턴스가 두 개 이상 있을 때 각 인스턴스는 동일한 인증서를 공유합니다. 예를 들어 한 사이트 안에 여러 관리 지점이나 여러 등록 지점이 있을 수 있습니다. 또한 이 자체 서명된 인증서에서는 SHA-256과 2048비트의 키 길이를 사용합니다. 이 인증서는 인증서를 신뢰해야 할 수 있는 사이트 시스템 서버의 신뢰할 수 있는 사용자 저장소에도 복사됩니다. 다음 사이트 시스템 역할에서 이 인증서를 생성합니다.  

-   응용 프로그램 카탈로그 웹 서비스 지점  

-   응용 프로그램 카탈로그 웹 사이트 지점  

-   Asset Intelligence 동기화 지점  

-   인증서 등록 지점  

-   Endpoint Protection 지점  

-   등록 지점  

-   대체 상태 지점  

-   관리 지점  

-   멀티캐스트 사용 배포 지점  

-   대역 외 서비스 지점  

-   보고 서비스 지점  

-   소프트웨어 업데이트 지점  

-   상태 마이그레이션 지점  

-   시스템 상태 검사기 지점  

-   Microsoft Intune 커넥터  

 이 인증서는 Configuration Manager에서 자동으로 관리되며 필요한 경우 자동으로 생성됩니다.  

 또한 Configuration Manager는 클라이언트 인증 인증서를 사용하여 배포 지점에서 관리 지점으로 상태 메시지를 전송합니다. 관리 지점이 HTTPS 클라이언트 연결 전용으로 구성된 경우 PKI 인증서를 사용해야 합니다. 관리 지점에서 HTTP 연결을 허용할 경우, PKI 인증서를 사용하거나 클라이언트 인증 기능이 있고 SHA-256과 2048비트의 키 길이를 사용하는 자체 서명된 인증서를 사용하는 옵션을 선택할 수도 있습니다.  

### <a name="server-communication-between-sites"></a>사이트 간 서버 통신  
 Configuration Manager에서는 데이터베이스 복제 및 파일 기반 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [System Center Configuration Manager에서 끝점 간의 통신](../../core/plan-design/hierarchy/communications-between-endpoints.md)을 참조하세요.  

 Configuration Manager에서는 사이트 간 데이터베이스 복제를 자동으로 구성하며 서버 인증 기능이 있는 PKI 인증서를 사용(사용 가능한 경우)합니다. 이러한 인증서를 사용할 수 없으면 Configuration Manager에서는 서버 인증을 위해 자체 서명된 인증서를 만듭니다. 두 경우 모두에 사이트 간 인증은 PeerTrust를 사용하는 신뢰할 수 있는 사용자 저장소에서 인증서를 사용하여 설정됩니다. 이 인증서 저장소는 Configuration Manager 계층 구조에서 사용되는 SQL Server 컴퓨터만 사이트 간 복제에 참여하도록 설정하는 데 사용됩니다. 기본 사이트 및 중앙 관리 사이트는 구성 변경 내용을 계층 내 모든 사이트에 복제할 수 있는 반면에 보조 사이트는 자체의 부모 사이트에만 구성 변경 내용을 복제할 수 있습니다.  

 사이트 서버는 자동으로 발생하는 보안 키 교환을 사용하여 사이트 간 통신을 설정합니다. 보내는 사이트 서버에서는 해시를 생성하여 자체 개인 키로 서명합니다. 받는 사이트 서버에서는 공개 키를 사용하여 서명을 확인하고 해시를 로컬로 생성된 값과 비교합니다. 해시가 서로 일치하면 받는 사이트에서는 복제된 데이터를 허용합니다. 값이 서로 일치하지 않으면 Configuration Manager에서는 복제된 데이터를 거부합니다.  

 Configuration Manager의 데이터베이스 복제 기능은 SQL Server Service Broker를 사용하여 다음 메커니즘을 통해 사이트 간에 데이터를 전송합니다.  

-   SQL Server 간 연결: 서버 인증에 Windows 자격 증명을 사용하고 1024비트로 자체 서명된 인증서를 통해 AES(Advanced Encryption Standard)를 사용하여 데이터를 서명 및 암호화합니다. 서버 인증 기능이 있는 PKI 인증서를 사용할 수 있으면 이 인증서가 사용됩니다. 인증서는 컴퓨터 인증서 저장소에 대한 개인 저장소 안에 있어야 합니다.  

-   SQL Service Broker: 인증에 2048비트로 자체 서명된 인증서를 사용하고 AES(Advanced Encryption Standard)를 사용하여 데이터를 서명 및 암호화합니다. 인증서는 SQL Server 마스터 데이터베이스 안에 있어야 합니다.  

 파일 기반 복제에서는 SMB(Server Message Block) 프로토콜을 사용하며, 암호화되지 않았지만 중요한 데이터가 포함되지 않은 이 데이터를 SHA-256을 사용하여 서명합니다. 이 데이터를 암호화하려면 IPsec을 사용하면 됩니다. IPsec은 Configuration Manager와는 독립적으로 구현해야 합니다.  

##  <a name="cryptographic-controls-for-clients-that-use-https-communication-to-site-systems"></a>사이트 시스템에 대해 HTTPS 통신을 사용하는 클라이언트를 위한 암호화 컨트롤  
 사이트 시스템 역할에서 클라이언트 연결을 허용할 때 HTTPS 및 HTTP 연결을 허용하거나 HTTPS 연결만 허용하도록 구성할 수 있습니다. 인터넷의 연결을 허용하는 사이트 시스템 역할은 HTTPS를 통한 클라이언트 연결만 허용합니다.  

 HTTPS를 통한 클라이언트 연결은 PKI(공개 키 인프라)와 통합되어 더 높은 수준의 보안을 제공함으로써 클라이언트 및 서버 간 통신을 보호합니다. 그러나 PKI 계획, 배포 및 운영에 대한 완벽한 이해 없이 HTTPS 클라이언트 연결을 구성하면 공격에 취약한 상태가 지속될 수 있습니다. 예를 들어 루트 CA를 보호하지 않으면 공격자가 전체 PKI 인프라의 신뢰를 손상시킬 수 있습니다. 제어 및 보안이 유지되는 프로세스를 통해 PKI 인증서를 배포하고 관리하지 못할 경우, 관리되지 않는 클라이언트가 만들어져 중요한 소프트웨어 업데이트 또는 패키지를 수신하지 못할 수도 있습니다.  

> [!IMPORTANT]  
>  클라이언트 통신에 사용되는 PKI 인증서는 클라이언트 및 일부 사이트 시스템 간의 통신만 보호합니다. 이 인증서는 사이트 서버 및 사이트 시스템 간 또는 사이트 서버 간의 통신 채널을 보호하지 않습니다.  

### <a name="communication-that-is-unencrypted-when-clients-use-https-communication"></a>클라이언트에서 HTTPS 통신을 사용할 때 암호화되지 않은 통신  
 클라이언트에서 HTTPS를 사용하여 사이트 시스템과 통신할 때 이 통신은 일반적으로 SSL을 통해 암호화됩니다. 그러나 다음 상황에서 클라이언트는 암호화를 사용하지 않고 사이트 시스템과 통신합니다.  

-   클라이언트가 인트라넷에서 연결에 실패하고 사이트 시스템에서 구성이 허용될 때 HTTP 사용으로 대체합니다.  

-   다음 사이트 시스템 역할에 대한 통신:  

    -   클라이언트에서 상태 메시지를 대체 상태 지점으로 보냅니다.  

    -   클라이언트에서 PXE 사용 배포 지점으로 PXE 요청을 전송합니다.  

    -   클라이언트에서 알림 데이터를 관리 지점으로 보냅니다.  

 보고 서비스 지점은 클라이언트 통신 모드와는 독립적으로 HTTP 또는 HTTPS를 사용하도록 구성됩니다.  

##  <a name="cryptographic-controls-for-clients-chat-use-http-communication-to-site-systems"></a>사이트 시스템에 대해 HTTP 통신을 사용하는 클라이언트를 위한 암호화 컨트롤  
 클라이언트에서 사이트 시스템 역할에 대해 HTTP 통신을 사용할 때 클라이언트 인증에 PKI 인증서를 사용하거나, Configuration Manager에서 생성하는 자체 서명된 인증서를 사용할 수 있습니다. Configuration Manager에서 자체 서명된 인증서를 생성하는 경우 해당 인증서는 서명 및 암호화를 위한 사용자 지정 개체 식별자를 포함하며 클라이언트를 고유하게 식별하는 데 사용됩니다. Windows Server 2003을 제외하고 지원되는 모든 운영 체제에서, 이와 같이 자체 서명된 인증서는 SHA-256을 사용하며 그 키 길이는 2048비트입니다. Windows Server 2003의 경우 SHA1은 1024비트의 키 길이와 함께 사용됩니다.  

### <a name="operating-system-deployment-and-self-signed-certificates"></a>운영 체제 배포 및 자체 서명된 인증서  
 Configuration Manager를 사용하여 운영 체제를 자체 서명된 인증서와 함께 배포할 경우 클라이언트 컴퓨터에도 관리 지점과 통신하기 위한 인증서가 있어야 하며, 이는 작업 순서 미디어 또는 PXE 사용 배포 지점에서 부팅하는 것과 같은 전환 단계에서도 마찬가지입니다. HTTP 클라이언트 연결에 대한 이런 시나리오를 지원하기 위해 Configuration Manager에서 서명 및 암호화를 위한 사용자 지정 개체 식별자를 포함하는 자체 서명된 인증서를 생성하고 이러한 인증서는 클라이언트를 고유하게 식별하는 데 사용됩니다. Windows Server 2003을 제외하고 지원되는 모든 운영 체제에서, 이와 같이 자체 서명된 인증서는 SHA-256을 사용하며 그 키 길이는 2048비트입니다. Windows Server 2003의 경우 SHA1은 1024비트의 키 길이와 함께 사용됩니다. 자체 서명된 인증서가 손상될 경우, 공격자가 신뢰할 수 있는 클라이언트로 가장하려고 인증서를 악용하는 것을 방지하기 위해 **보안** 노드의 **관리** 작업 영역에 있는 **인증서** 노드에서 해당 인증서를 차단하세요.  

### <a name="client-and-server-authentication"></a>클라이언트 및 서버 인증  
 클라이언트가 HTTP를 통해 연결되는 경우 Active Directory Domain Service 또는 Configuration Manager의 신뢰할 수 있는 루트 키를 사용하여 관리 지점을 인증합니다. 클라이언트에서는 상태 마이그레이션 지점 또는 소프트웨어 업데이트 지점을 비롯한 다른 사이트 시스템 역할을 인증하지 않습니다.  

 관리 지점이 일단 자체 서명된 클라이언트 인증서를 사용하여 클라이언트를 인증하면 이 메커니즘을 통해 모든 컴퓨터가 자체 서명된 인증서를 생성할 수 있기 때문에 최소한의 보안이 구현됩니다. 이 시나리오에서는 클라이언트 식별 프로세스가 승인으로 보강되어야 합니다. 신뢰할 수 있는 컴퓨터만 Configuration Manager에서 자동으로, 또는 관리자가 수동으로 승인해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 끝점 간의 통신](../../core/plan-design/hierarchy/communications-between-endpoints.md)의 승인 섹션을 참조하세요.  

##  <a name="about-ssl-vulnerabilities"></a>SSL 취약점 정보  
 Configuration Manager 서버의 보안을 개선하려면 SSL 3.0은 사용하지 않도록 설정하고, TLS 1.1 및 1.2는 사용하도록 설정하고, TLS 관련 암호 그룹을 다시 정렬하는 것이 좋습니다. 이러한 작업을 수행하는 방법은 [이 KB 문서](https://support.microsoft.com/en-us/kb/245030/)에서 확인할 수 있습니다. 이 작업은 Configuration Manager 기능에 영향을 주지 않습니다.  




<!--HONumber=Nov16_HO1-->


