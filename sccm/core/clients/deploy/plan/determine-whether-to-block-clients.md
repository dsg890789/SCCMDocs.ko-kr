---
title: 클라이언트 차단
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 시스템 보안을 위해 클라이언트 액세스를 차단합니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 54ef5fbb-521d-4ca5-a1c5-61e6f538d71e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b01fd7944d8a6ab726712f6ebeb4cb5374896072
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824948"
---
# <a name="determine-whether-to-block-clients-in-configuration-manager"></a>Configuration Manager에서 클라이언트 차단 여부 결정

*적용 대상: Configuration Manager(현재 분기)*

클라이언트 컴퓨터 또는 클라이언트 모바일 디바이스를 더 이상 신뢰할 수 없는 경우 System Center 2012 Configuration Manager 콘솔에서 클라이언트를 차단할 수 있습니다. 차단된 클라이언트는 Configuration Manager 인프라에서 거부되므로 사이트 시스템과 통신하여 정책을 다운로드하거나, 인벤토리 데이터를 업로드하거나, 상태 또는 상태 메시지를 보낼 수 없습니다.  

 보조 사이트 또는 중앙 관리 사이트가 아닌 할당된 사이트에서 클라이언트를 차단 및 차단 해제해야 합니다.  

> [!IMPORTANT]  
>  Configuration Manager에서 클라이언트를 차단하면 Configuration Manager 사이트를 보호하는 데 도움이 되지만, 클라이언트가 HTTP를 사용하여 사이트 시스템과 통신하도록 허용하는 경우 차단된 클라이언트가 새 자체 서명된 인증서와 하드웨어 ID를 사용하여 사이트에 다시 연결할 수 있기 때문에 신뢰할 수 없는 컴퓨터 또는 모바일 디바이스로부터 사이트를 보호하는 데 이 기능에 의존해서는 안 됩니다. 차단 기능은 사이트 시스템이 HTTPS 클라이언트 연결을 수락하며 운영 체제 배포에 사용하는 부팅 미디어가 손실되거나 손상된 경우 해당 부팅 미디어를 차단하는 데 사용하세요.  

 ISV 프록시 인증서를 사용하여 사이트에 액세스하는 클라이언트는 차단할 수 없습니다. ISV 프록시 인증서에 대한 자세한 내용은 Configuration Manager SDK(소프트웨어 개발 키트)를 참조하세요.  

 사이트 시스템이 HTTPS 클라이언트 연결을 수락하고 PKI(공개 키 인프라)가 CRL(인증서 해지 목록)을 지원하는 경우 항상 잠재적으로 손상된 인증서에 대한 일차적인 방어 수단으로 인증서 해지를 고려해야 합니다. Configuration Manager에서 클라이언트를 차단하면 계층 구조를 보호하기 위한 이차 방어 수단이 됩니다.  

##  <a name="BKMK_Block_vs_CRL"></a> 클라이언트 차단에 대한 고려 사항  

-   이 옵션은 HTTP 및 HTTPS 클라이언트 연결에 사용할 수 있지만 클라이언트가 HTTP를 사용하여 사이트 시스템에 연결하는 경우 보안이 제한적입니다.  

-   Configuration Manager 관리자에게는 클라이언트를 차단할 수 있는 권한이 있으며 Configuration Manager 콘솔에서 이 작업이 수행됩니다.  

-   클라이언트 통신은 Configuration Manager 계층 구조에서만 거부됩니다.  

    > [!NOTE]  
    >  동일한 클라이언트가 다른 Configuration Manager 계층 구조에 등록할 수 있습니다.  

-   클라이언트는 Configuration Manager 사이트에서 즉시 차단됩니다.  

-   사이트 시스템을 잠재적으로 손상된 컴퓨터와 모바일 디바이스로부터 보호하는 데 도움이 됩니다.  

## <a name="considerations-for-using-certificate-revocation"></a>인증서 해지 사용에 대한 고려 사항  

-   이 옵션은 공개 키 인프라가 CRL(인증서 해지 목록)을 지원하는 경우 HTTPS Windows 클라이언트 연결에 사용할 수 있습니다.  

     Mac 클라이언트가 항상 CRL 확인을 수행하기 때문에 이 기능을 사용하지 않도록 설정할 수 없습니다.  

     모바일 디바이스 클라이언트는 인증서 해지 목록을 사용하여 사이트 시스템의 인증서를 확인하지 않지만, Configuration Manager에서 해당 인증서를 해지하고 확인할 수 있습니다.  

-   공개 키 인프라 관리자는 인증서를 해지할 수 있는 권한이 있으며, 이 작업은 Configuration Manager 콘솔 외부에서 수행됩니다.  

-   클라이언트 인증서가 필요한 컴퓨터 또는 모바일 디바이스에서 클라이언트 통신이 거부될 수 있습니다.  

-   인증서 해지와 사이트 시스템이 수정된 CRL(인증서 해지 목록)을 다운로드하는 것 사이에 지연이 발생할 수 있습니다.  

-   대다수 PKI 배포에서는 이 지연 시간이 하루 이상일 수 있습니다. 예를 들어 Active Directory 인증서 서비스에서 기본 만료 기간은 전체 CRL의 경우 1주일, 델타 CRL의 경우 1일입니다.  

-   사이트 시스템과 클라이언트를 잠재적으로 손상된 컴퓨터와 모바일 디바이스로부터 보호하는 데 도움이 됩니다.  

    > [!NOTE]  
    >  또한 IIS에서 CTL(인증서 신뢰 목록)을 구성하여 IIS를 실행하는 사이트 시스템을 알 수 없는 클라이언트로부터 보호할 수 있습니다.  
