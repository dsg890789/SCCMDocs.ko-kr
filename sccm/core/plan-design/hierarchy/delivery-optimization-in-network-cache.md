---
title: 네트워크 캐시의 배달 최적화
titleSuffix: Configuration Manager
description: 배달 최적화를 위해 Configuration Manager 배포 지점을 로컬 캐시 서버로 사용
ms.date: 09/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: c5cb5753-5728-4f81-b830-a6fd1a3e105c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 070f7ec6f99a9de89c155e756989fb3b5fa4a594
ms.sourcegitcommit: 05a984cf94ea43c392701a389c4eb20bd692847c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70922731"
---
# <a name="delivery-optimization-in-network-cache-in-configuration-manager"></a>Configuration Manager의 배달 최적화 네트워크 내 캐시

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--3555764-->

버전 1906부터 배포 지점에 배달 최적화 네트워크 내 캐시(DOINC) 서버를 설치할 수 있습니다. 이 온-프레미스 콘텐츠를 캐시하면 클라이언트들이 전송 최적화 기능을 활용하는 동시에 WAN 링크도 보호할 수 있습니다.

이 캐시 서버는 전송 최적화에 의해 다운로드된 콘텐츠에서 주문형 투명 캐시로 작동합니다. 클라이언트 설정을 사용하여 이 서버가 로컬 Configuration Manager 경계 그룹의 멤버에게만 제공되도록 합니다.

이 캐시는 Configuration Manager의 배포 지점 콘텐츠와 분리됩니다. 배포 지점 역할과 동일한 드라이브를 선택하면 콘텐츠를 개별적으로 저장합니다.

> [!Note]  
> 전송 최적화 네트워크 내 캐시 서버는 아직 개발 중인 Windows Server에 설치된 애플리케이션입니다. 이 기능은 Configuration Manager 콘솔에서 *베타* 레이블로 태그가 지정됩니다.  


## <a name="how-it-works"></a>작동 방식

배달 최적화 네트워크 내 캐시 서버를 사용하도록 클라이언트를 구성하면 클라이언트는 인터넷에서 Microsoft 클라우드 관리형 콘텐츠를 더 이상 요청하지 않습니다. 클라이언트는 배포 지점에 설치된 DOINC 서버에서 이 콘텐츠를 요청합니다. DOINC 서버는 ARR(애플리케이션 요청 라우팅)을 위한 IIS 기능을 사용하여 이 콘텐츠를 캐시합니다. 그러면 캐시 서버는 동일한 콘텐츠에 대한 모든 후속 요청에 신속하게 응답할 수 있습니다. DOINC 서버를 사용할 수 없거나 콘텐츠가 아직 캐시되지 않은 경우 클라이언트는 인터넷에서 콘텐츠를 다운로드합니다. 클라이언트는 배달 최적화도 사용하므로 네트워크의 피어에서 콘텐츠의 일부를 다운로드합니다.

![DOINC 작동 원리 다이어그램](media/3555764-delivery-optimization-in-network-cache.png)

1. 클라이언트는 업데이트를 확인하고 CDN(콘텐츠 배달 네트워크)의 주소를 가져옵니다.

2. Configuration Manager는 캐시 서버 이름을 포함하여 클라이언트에서 배달 최적화(DO) 설정을 구성합니다.

3. 클라이언트 A는 DO 캐시 서버에서 콘텐츠를 요청합니다.

4. 캐시에 콘텐츠가 포함되어 있지 않으면 DO 캐시 서버는 CDN에서 해당 콘텐츠를 가져옵니다.

5. 캐시 서버가 응답하지 않는 경우 클라이언트는 CDN에서 콘텐츠를 다운로드합니다.

6. 클라이언트는 DO를 사용하여 피어에서 콘텐츠의 일부를 가져옵니다.


## <a name="prerequisites-and-limitations"></a>필수 구성 요소 및 제한 사항

- 다음 구성을 사용하는 *온-프레미스* 배포 지점:

    - Windows Server 2012, Windows Server 2012 R2, Windows Server 2016 또는 Windows Server 2019 실행

    - 포트 80에서 사용하도록 설정된 기본 웹 사이트

    - IIS [애플리케이션 요청 라우팅](https://docs.microsoft.com/iis/extensions/planning-for-arr/application-request-routing-version-2-overview)(ARR) 기능을 사전 설치하지 마세요. DOINC가 ARR을 설치하고 설정을 구성합니다. Microsoft는 DOINC의 ARR 구성이 이 기능을 사용하는 서버의 다른 애플리케이션과 충돌하지 않는다고 보장할 수 없습니다.

    - 배포 지점에는 Microsoft 클라우드에 대한 인터넷 액세스가 필요합니다. 특정 URL은 특정 클라우드 사용 콘텐츠에 따라 달라질 수 있습니다. 자세한 내용은 [Internet access requirements](/sccm/core/plan-design/network/internet-endpoints)(인터넷 액세스 요구 사항)를 참조하세요.

- Windows 10 버전 1709 이상을 실행하는 클라이언트


## <a name="enable-doinc"></a>DOINC 사용

1. Configuration Manager 콘솔에서 **관리** 작업 공간으로 이동하여 **배포 지점** 노드를 선택합니다.

1. 온-프레미스 배포 지점을 선택한 다음 리본 메뉴에서 **속성**을 선택합니다.

1. 배포 지점 역할의 속성에 있는 **일반** 탭에서 다음 설정을 구성합니다.  

    1. **이 배포 지점을 배달 최적화 네트워크 내 캐시 서버로 사용** 옵션을 사용하도록 설정합니다.  

        사용 조건을 읽고 동의합니다.

    2. **사용할 로컬 드라이브**: 캐시에 사용할 디스크를 선택합니다. **자동**은 기본값이며, 여유 공간이 가장 많은 디스크를 사용합니다.<sup>[참고 1](#bkmk_note1)</sup>  

        > [!Note]  
        > 이 드라이브는 나중에 변경할 수 있습니다. 캐시된 콘텐츠는 새 드라이브에 복사하지 않는 한 손실됩니다.

    3. **디스크 공간**: 예약할 디스크 공간의 크기(GB) 또는 전체 디스크 공간의 백분율을 선택합니다. 이 값은 기본적으로 100GB입니다.

        > [!Note]  
        > 대부분의 고객에게는 기본 캐시 크기면 충분합니다. 나중에 캐시 크기를 조정할 수 있습니다.

    4. **네트워크 내 캐시 서버를 사용하지 않을 때 캐시 보존**: 캐시 서버를 제거하고 이 옵션을 사용하는 경우 서버는 디스크에서 캐시 콘텐츠를 유지합니다.  

1. 클라이언트 설정의 **배달 최적화** 그룹에서 **콘텐츠 다운로드를 위해 배달 최적화 네트워크 내 캐시 서버(베타)를 사용하도록 Configuration Manager에서 관리되는 디바이스를 사용** 설정을 구성합니다.  

### <a name="bkmk_note1"></a> 참고 1: 드라이브 선택 정보

**자동**을 선택하면 Configuration Manager에서는 DOINC 구성 요소를 설치할 때 **no_sms_on_drive.sms** 파일을 사용합니다. 예를 들어 배포 지점에 `C:\no_sms_on_drive.sms` 파일이 있습니다. C: 드라이브에 가장 많은 여유 공간이 있는 경우에도 Configuration Manager는 해당 캐시에 다른 드라이브를 사용하도록 DOINC를 구성합니다.

**no_sms_on_drive.sms** 파일이 이미 있는 특정 드라이브를 선택하면 Configuration Manager는 해당 파일을 무시합니다. 해당 드라이브를 사용하도록 DOINC를 구성하는 것은 명시적 의도입니다. 예를 들어 배포 지점에 `F:\no_sms_on_drive.sms` 파일이 있습니다. **F:** 드라이브를 사용하도록 배포 지점 속성을 명시적으로 구성하면 Configuration Manager는 해당 캐시에 F: 드라이브를 사용하도록 DOINC를 구성합니다.

DOINC가 설치된 후 드라이브를 변경하려면:

- 특정 드라이브 문자를 사용하도록 배포 지점 속성을 수동으로 구성합니다.

- 자동으로 설정된 경우 먼저 **no_sms_on_drive.sms** 파일을 만듭니다. 그런 다음, 구성 변경을 트리거하기 위해 배포 지점 속성을 약간 변경합니다.

## <a name="verify"></a>확인

클라이언트가 클라우드 관리 콘텐츠를 다운로드하는 경우 배포 지점에 설치된 캐시 서버에서 전송 최적화를 사용합니다. 클라우드 관리 콘텐츠에는 다음 형식이 포함됩니다.

- Microsoft 스토어 앱
- 언어와 같은 Windows 주문형 기능
- [비즈니스용 Windows 업데이트 정책](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10)을 사용하는 경우: Windows 10 기능 및 품질 업데이트
- [공동 관리 워크로드](/sccm/comanage/workloads)의 경우:
    - 비즈니스용 Windows 업데이트 Windows 10 기능 및 품질 업데이트
    - Office 간편 실행 앱: Office 앱 및 업데이트
    - 클라이언트 앱: Microsoft 스토어 앱 및 업데이트
    - Endpoint Protection: Windows Defender 정의 업데이트

Windows 10 버전 1809 이상에서는 **Get-DeliveryOptimizationStatus** Windows PowerShell cmdlet을 사용하여 이 동작을 확인합니다. cmdlet 출력에서는 **BytesFromCacheServer** 값을 검토합니다. 자세한 내용은 [배달 최적화 모니터링](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-setup#monitor-delivery-optimization)을 참조하세요.

캐시 서버가 HTTP 오류를 반환하면 전송 최적화 클라이언트는 원본 클라우드로 대체됩니다.

자세한 내용은 [Configuration Manager의 전송 최적화 네트워크 내 캐시 문제 해결](/sccm/core/servers/deploy/configure/troubleshoot-delivery-optimization-in-network-cache)을 참조하세요.

## <a name="see-also"></a>참고 항목

[배달 최적화를 사용하여 Windows 10 업데이트 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)

[Configuration Manager의 전송 최적화 네트워크 내 캐시 문제 해결](/sccm/core/servers/deploy/configure/troubleshoot-delivery-optimization-in-network-cache)
