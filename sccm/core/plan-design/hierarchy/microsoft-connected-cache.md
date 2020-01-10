---
title: Microsoft 연결된 캐시
titleSuffix: Configuration Manager
description: 배달 최적화를 위해 Configuration Manager 배포 지점을 로컬 캐시 서버로 사용
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c5cb5753-5728-4f81-b830-a6fd1a3e105c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 046dd4bae3270ffaed93982e52ab63e85bf99ead
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799984"
---
# <a name="microsoft-connected-cache-in-configuration-manager"></a>Configuration Manager의 Microsoft Connected Cache

*적용 대상: Configuration Manager(현재 분기)*

<!--3555764-->

버전 1906부터, 배포 지점에 Microsoft Connected Cache 서버를 설치할 수 있습니다. 이 온-프레미스 콘텐츠를 캐시하면 클라이언트들이 전송 최적화 기능을 활용하는 동시에 WAN 링크도 보호할 수 있습니다.

> [!NOTE]
> 버전 1910부터 이 기능을 **Microsoft Connected Cache**라고 합니다. 이전 명칭은 DOINC(전송 최적화 네트워크 내 캐시)였습니다.

이 캐시 서버는 전송 최적화에 의해 다운로드된 콘텐츠에서 주문형 투명 캐시로 작동합니다. 클라이언트 설정을 사용하여 이 서버가 로컬 Configuration Manager 경계 그룹의 멤버에게만 제공되도록 합니다.

이 캐시는 Configuration Manager의 배포 지점 콘텐츠와 분리됩니다. 배포 지점 역할과 동일한 드라이브를 선택하면 콘텐츠를 개별적으로 저장합니다.

> [!Note]  
> Connected Cache 서버는 Windows Server에 설치되는 애플리케이션입니다. 이 애플리케이션은 아직 개발 중입니다.

## <a name="how-it-works"></a>작동 방식

Connected Cache 서버를 사용하도록 클라이언트를 구성하면 클라이언트는 인터넷에서 Microsoft 클라우드 관리형 콘텐츠를 더 이상 요청하지 않습니다. 클라이언트는 배포 지점에 설치된 캐시 서버에서 이 콘텐츠를 요청합니다. 온-프레미스 서버는 ARR(애플리케이션 요청 라우팅)을 위한 IIS 기능을 사용하여 이 콘텐츠를 캐시합니다. 그러면 캐시 서버는 동일한 콘텐츠에 대한 모든 후속 요청에 신속하게 응답할 수 있습니다. Connected Cache 서버를 사용할 수 없거나 콘텐츠가 아직 캐시되지 않은 경우 클라이언트는 인터넷에서 콘텐츠를 다운로드합니다. 클라이언트는 배달 최적화도 사용하므로 네트워크의 피어에서 콘텐츠의 일부를 다운로드합니다.

![Connected Cache의 작동 방식을 보여 주는 다이어그램](media/3555764-microsoft-connected-cache.png)

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

  - IIS [애플리케이션 요청 라우팅](https://docs.microsoft.com/iis/extensions/planning-for-arr/application-request-routing-version-2-overview)(ARR) 기능을 사전 설치하지 마세요. Connected Cache가 ARR을 설치하고 설정을 구성합니다. Microsoft는 Connected Cache의 ARR 구성이 이 기능을 사용하는 서버의 다른 애플리케이션과 충돌하지 않는다고 보장할 수 없습니다.

  - 배포 지점에는 Microsoft 클라우드에 대한 인터넷 액세스가 필요합니다. 특정 URL은 특정 클라우드 사용 콘텐츠에 따라 달라질 수 있습니다. 자세한 내용은 [Internet access requirements](/sccm/core/plan-design/network/internet-endpoints)(인터넷 액세스 요구 사항)를 참조하세요.

- Windows 10 버전 1709 이상을 실행하는 클라이언트

## <a name="enable-connected-cache"></a>Connected Cache 사용 설정

1. Configuration Manager 콘솔에서 **관리** 작업 공간으로 이동하여 **배포 지점** 노드를 선택합니다.

1. *온-프레미스* 배포 지점을 선택한 다음 리본 메뉴에서 **속성**을 선택합니다.

1. 배포 지점 역할의 속성에 있는 **일반** 탭에서 다음 설정을 구성합니다.  

    1. **이 배포 지점을 Microsoft Connected Cache 서버로 사용** 옵션을 선택합니다.  

        사용 조건을 읽고 동의합니다.

    2. **사용할 로컬 드라이브**: 캐시에 사용할 디스크를 선택합니다. **자동**은 기본값이며, 여유 공간이 가장 많은 디스크를 사용합니다.<sup>[참고 1](#bkmk_note1)</sup>  

        > [!Note]  
        > 이 드라이브는 나중에 변경할 수 있습니다. 캐시된 콘텐츠는 새 드라이브에 복사하지 않는 한 손실됩니다.

    3. **디스크 공간**: 예약할 디스크 공간의 크기(GB) 또는 전체 디스크 공간의 백분율을 선택합니다. 이 값은 기본적으로 100GB입니다.

        > [!Note]  
        > 대부분의 고객에게는 기본 캐시 크기면 충분합니다. 나중에 캐시 크기를 조정할 수 있습니다.

    4. **Connected Cache 서버를 사용하지 않을 때 캐시 보존**: 캐시 서버를 제거하고 이 옵션을 사용하는 경우 서버는 디스크에서 캐시 콘텐츠를 유지합니다.  

1. 클라이언트 설정의 **전송 최적화** 그룹에서 설정을 **Configuration Manager에서 관리하는 디바이스를 통해 다운로드된 콘텐츠에 적합한 Microsoft Connected Cache 서버를 사용합니다**로 구성합니다.  

### <a name="bkmk_note1"></a> 참고 1: 드라이브 선택 정보

**자동**을 선택하면 Configuration Manager가 Connected Cache 구성 요소를 설치할 때 **no_sms_on_drive.sms** 파일을 사용합니다. 예를 들어 배포 지점에 `C:\no_sms_on_drive.sms` 파일이 있습니다. C: 드라이브에 가장 많은 여유 공간이 있는 경우에도 Configuration Manager는 캐시를 위해 다른 드라이브를 사용하도록 Connected Cache를 구성합니다.

**no_sms_on_drive.sms** 파일이 이미 있는 특정 드라이브를 선택하면 Configuration Manager는 해당 파일을 무시합니다. 해당 드라이브를 사용하도록 Connected Cache를 구성하는 것은 명시적인 의도입니다. 예를 들어 배포 지점에 `F:\no_sms_on_drive.sms` 파일이 있습니다. **F:** 드라이브를 사용하도록 배포 지점 속성을 명시적으로 구성하면 Configuration Manager는 캐시를 위해 F: 드라이브를 사용하도록 Connected Cache를 구성합니다.

Connected Cache를 설치한 후에 드라이브를 변경하려면:

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

자세한 내용은 [Configuration Manager의 Microsoft Connected Cache 문제 해결](/sccm/core/servers/deploy/configure/troubleshoot-microsoft-connected-cache)을 참조하세요.

## <a name="bkmk_intune"></a> Intune Win32 앱 지원

<!--5032900-->

버전 1910부터, Configuration Manager 배포 지점에서 Microsoft Connected Cache를 사용하도록 설정하면 배포 지점에서 공동 관리 클라이언트로 Microsoft Intune Win32 앱을 제공할 수 있습니다.

### <a name="prerequisites"></a>전제 조건

#### <a name="client"></a>클라이언트

- 클라이언트를 최신 버전으로 업데이트합니다.

- 클라이언트 디바이스에는 4GB 이상의 메모리가 필요합니다.

    > [!TIP]
    > 다음 그룹 정책 설정을 사용합니다. 컴퓨터 구성 > 관리 템플릿 > Windows 구성 요소 > 제공 최적화 > **피어 캐싱(GB)을 사용하도록 설정하려면 최소 RAM 용량(포함)이 필요**합니다.

#### <a name="site"></a>사이트

- 배포 지점에서 Connected Cache를 사용하도록 설정합니다. 자세한 내용은 [Microsoft Connected Cache](/configmgr/core/plan-design/hierarchy/microsoft-connected-cache)를 참조하세요.

- 클라이언트와 Connected Cache 사용 배포 지점은 동일한 경계 그룹에 있어야 합니다.

- [**제공 최적화**](/configmgr/core/clients/deploy/about-client-settings#delivery-optimization) 그룹에서 다음 클라이언트 설정을 사용하도록 설정합니다.

  - **제공 최적화 그룹 ID에 Configuration Manager 경계 그룹 사용**
  - **Configuration Manager에서 관리하는 디바이스를 통해 다운로드된 콘텐츠에 적합한 Microsoft Connected Cache 서버 사용**

- **공동 관리 디바이스용 클라이언트 앱** 시험판 기능을 사용하도록 설정합니다. 자세한 내용은 [시험판 기능](/configmgr/core/servers/manage/pre-release-features)을 참조하세요.

- 공동 관리를 사용하도록 설정하고 **클라이언트 앱** 워크로드를 **Pilot Intune** 또는 **Intune**으로 전환합니다. 자세한 내용은 다음 아티클을 참조하세요.

  - [워크로드 - 클라이언트 앱](/configmgr/comanage/workloads#client-apps)
  - [공동 관리를 활성화하는 방법](/configmgr/comanage/how-to-enable)
  - [워크로드를 Intune으로 전환](/configmgr/comanage/how-to-switch-workloads)

    파일럿에 있는 경우 클라이언트 앱에 대한 파일럿 컬렉션에 클라이언트를 추가합니다.

#### <a name="intune"></a>Intune

- 이 기능은 Intune Win32 앱 유형만 지원합니다.

  - 이 목적을 위해 Intune에서 새 앱을 만들고 할당(배포)합니다. (Intune 버전 1811 이전에 만든 앱은 작동하지 않습니다.) 자세한 내용은 [Intune Win32 앱 관리](https://docs.microsoft.com/intune/apps/apps-win32-app-management)를 참조하세요.

  - 앱의 크기는 100MB 이상이어야 합니다.
  
    > [!TIP]
    > 다음 그룹 정책 설정을 사용합니다. 컴퓨터 구성 > 관리 템플릿 > Windows 구성 요소 > 제공 최적화 > **최소 피어 캐싱 콘텐츠 파일 크기(MB)** .

## <a name="see-also"></a>참고 항목

[배달 최적화를 사용하여 Windows 10 업데이트 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)

[Configuration Manager의 Microsoft Connected Cache 문제 해결](/sccm/core/servers/deploy/configure/troubleshoot-microsoft-connected-cache)
