---
title: "Windows Embedded 장치에 클라이언트 배포 계획"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에서 Windows Embedded 장치에 클라이언트 배포를 계획합니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 038e61f9-f49d-41d1-9a9f-87bec9e00d5d
caps.latest.revision: "7"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: c4f3d8a9b043707340e56d3ae483ad66ca17dc10
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="planning-for-client-deployment-to-windows-embedded-devices-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows Embedded 장치에 클라이언트 배포 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

<a name="BKMK_DeployClientEmbedded"></a> Windows Embedded 장치에 System Center Configuration Manager 클라이언트가 포함되지 않은 경우 장치가 필요한 종속성을 충족하는 한 모든 클라이언트 설치 방법을 사용할 수 있습니다. Windows Embedded 장치가 쓰기 필터를 지원하는 경우 클라이언트를 설치하기 전에 이러한 필터를 사용하지 않도록 설정하고 클라이언트가 설치되어 사이트에 할당된 후에 다시 사용하도록 설정해야 합니다.  

 필터를 사용하지 않도록 설정할 때 필터 드라이버는 사용하지 않도록 설정하면 안 됩니다. 이러한 드라이버는 일반적으로 컴퓨터를 시작할 때 자동으로 시작됩니다. 드라이버를 사용하지 않도록 설정하면 클라이언트 설치가 차단되거나 쓰기 필터 오케스트레이션을 간섭하게 되어 클라이언트 작업이 실패합니다. 각 쓰기 필터 유형과 연결된 계속 실행되어야 하는 서비스는 다음과 같습니다.  

|쓰기 필터 유형|드라이버|유형|설명|  
|-----------------------|------------|----------|-----------------|  
|EWF|EWF|커널|보호된 볼륨에서 섹터 수준 I/O 리디렉션을 구현합니다.|  
|FBWF|FBWF|파일 시스템|보호된 볼륨에서 파일 수준 I/O 리디렉션을 구현합니다.|  
|UWF|uwfreg|커널|UWF 레지스트리 리디렉터|  
|UWF|uwfs|파일 시스템|UWF 파일 리디렉터|  
|UWF|uwfvol|커널|UWF 볼륨 관리자|  

 쓰기 필터는 소프트웨어를 설치하는 경우와 같은 변경을 수행할 때 Windows Embedded 장치의 운영 체제가 업데이트되는 방식을 제어합니다. 쓰기 필터가 사용하도록 설정되면 운영 체제에 대한 직접적인 변경 없이 이러한 변경 사항이 임시 오버레이로 리디렉션됩니다. 변경 사항이 오버레이에만 기록될 경우 Windows Embedded 장치가 종료될 때 손실됩니다. 그러나 쓰기 필터를 일시적으로 사용하지 않도록 설정하면 변경 사항이 영구적으로 적용되므로 Windows Embedded 장치를 다시 시작할 때마다 변경을 다시 수행하거나 소프트웨어를 다시 설치할 필요가 없습니다. 그러나 쓰기 필터를 일시적으로 사용하지 않도록 설정했다가 다시 사용하도록 설정하려면 한 번 이상 다시 시작이 필요하므로 일반적으로 업무 외 시간에 다시 시작이 이루어지도록 유지 관리 기간을 구성하여 다시 시작이 일어나는 시기를 제어하는 것이 좋습니다.  

 응용 프로그램, 작업 순서, 소프트웨어 업데이트, Endpoint Protection 클라이언트 등과 같은 소프트웨어를 배포할 때 쓰기 필터를 자동으로 비활성화한 후 다시 활성화하는 옵션을 구성할 수 있습니다. 자동 재구성이 사용되는 구성 항목을 포함하는 구성 기준은 예외가 됩니다. 이 시나리오에서 재구성은 항상 오버레이에서 수행되므로 장치가 다시 시작될 때까지만 사용 가능합니다. 재구성은 다음 평가 주기에서 다시 적용되지만 오버레이에만 적용되며 이는 다시 시작 시 삭제됩니다. Configuration Manager에서 수정 변경 내용을 커밋하도록 강제하려면 구성 기준을 배포한 다음 변경 내용을 가능한 한 빨리 커밋하도록 지원하는 다른 소프트웨어 배포를 배포하면 됩니다.  

 쓰기 필터가 사용하지 않도록 설정된 경우 소프트웨어 센터를 사용하여 Windows Embedded 장치에 소프트웨어를 설치할 수 있습니다. 그러나 쓰기 필터가 사용하도록 설정된 경우 설치는 실패하고 Configuration Manager에서 응용 프로그램 설치 권한이 부족하다는 오류 메시지를 표시합니다.  

> [!WARNING]  
>  변경 내용을 커밋하는 Configuration Manager 옵션을 선택하지 않더라도 변경 내용을 커밋하는 다른 소프트웨어 설치 또는 변경 내용이 만들어질 경우 변경 내용이 커밋될 수 있습니다. 이 시나리오에서 새 변경 내용 외에도 원래 변경 내용이 커밋됩니다.  

 Configuration Manager에서 변경 내용을 영구적으로 적용하기 위해 쓰기 필터를 사용하지 않도록 설정하면 로컬 관리자 권한이 있는 사용자만 로그온하고 임베디드 장치를 사용할 수 있습니다. 이 기간 동안 낮은 수준의 권한을 갖는 사용자는 잠깁니다. 또한 해당 컴퓨터는 서비스되고 있으므로 사용할 수 없다는 메시지가 표시됩니다. 이 경우 변경 내용이 영구적으로 적용될 수 있는 상태에 있는 장치를 보호할 수 있습니다. 이러한 서비스 모드 잠금 동작만 고려하더라도 유지 관리 기간은 사용자가 장치에 로그온하지 않는 시간 동안으로 구성해야 합니다.  

 Configuration Manager에서는 다음 유형의 쓰기 필터를 관리할 수 있습니다.  

-   FBWF(파일 기반 쓰기 필터) - 자세한 내용은 [파일 기반 쓰기 필터](http://go.microsoft.com/fwlink/?LinkID=204717)를 참조하세요.  

-   EWF(강화된 쓰기 필터) RAM - 자세한 내용은 [강화된 쓰기 필터](http://go.microsoft.com/fwlink/?LinkId=204718)를 참조하세요.  

-   UWF(통합 쓰기 필터) - 자세한 내용은 [통합 쓰기 필터](http://go.microsoft.com/fwlink/?LinkId=309236)를 참조하세요.  

 Configuration Manager에서는 Windows Embedded 장치가 EWF RAM Reg 모드일 때 쓰기 필터 작업을 지원하지 않습니다.  

> [!IMPORTANT]  
>  선택할 수 있는 경우 효율성과 확장성을 높이기 위해 Configuration Manager에서 FBWF(파일 기반 쓰기 필터)를 사용하는 것이 좋습니다.
>
> **FBWF만 사용하는 장치의 경우:** 장치 다시 시작 시 클라이언트 상태 및 인벤토리 데이터를 보존하려면 다음 예외를 구성합니다.  
>   
>  -   CCMINSTALLDIR\\*.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
>  Windows Embedded 8.0 이상을 실행하는 장치는 와일드카드 문자를 포함하는 제외를 지원하지 않습니다. 이러한 장치에서는 다음 제외를 개별적으로 구성해야 합니다.  
>   
>  -   확장명이 .sdf인 CCMINSTALLDIR의 모든 파일. 일반적으로 다음과 같은 파일이 포함됩니다.  
>   
>     -   UserAffinityStore.sdf  
>     -   InventoryStore.sdf  
>     -   CcmStore.sdf  
>     -   StateMessageStore.sdf  
>     -   CertEnrollmentStore.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
> **FBWF 및 UWF만 사용하는 장치의 경우:** 작업 그룹에서 클라이언트가 관리 지점에 대한 인증을 위해 인증서를 사용하는 경우 클라이언트가 계속 관리 지점과 통신할 수 있도록 개인 키도 제외해야 합니다. 이러한 장치에서는 다음과 같은 예외를 구성합니다.  
>   
>  -   c:\Windows\System32\Microsoft\Protect  
> -   c:\ProgramData\Microsoft\Crypto  
> -   HKEY_LOCAL_MACHINE\Software\Microsoft\SystemCertificates\SMS\Certificates  

 Configuration Manager에서 쓰기 필터를 사용하는 Windows Embedded 장치를 배포하고 관리하는 예제 시나리오를 보려면 [Windows Embedded 장치의 System Center Configuration Manager 클라이언트 배포 및 관리에 대한 예제 시나리오](../../../../core/clients/deploy/example-scenario-for-deploying-and-managing-clients-on-windows-embedded-devices.md)를 참조하세요.  

 Windows Embedded 장치에 대한 이미지를 작성하고 쓰기 필터를 구성하는 방법에 대한 자세한 내용은 관련 Windows Embedded 설명서를 참조하거나 OEM에 문의하세요.  

> [!NOTE]  
>  소프트웨어 배포 및 구성 항목에 대해 해당되는 플랫폼을 선택하면 특정 버전이 아니라 Windows Embedded 제품군이 표시됩니다. 특정 Windows Embedded 버전을 목록 상자 내 옵션에 매핑하려면 다음 목록을 참조하세요.  
>   
>  -   **Windows XP(32비트) 기반 임베디드 운영 체제** 는 다음과 같습니다.  
>   
>      -   Windows XP Embedded  
>     -   Windows Embedded for Point of Service  
>     -   Windows Embedded Standard 2009  
>     -   Windows Embedded POSReady 2009  
> -   **Windows 7(32비트) 기반 임베디드 운영 체제** 는 다음과 같습니다.  
>   
>      -   Windows Embedded Standard 7(32비트)  
>     -   Windows Embedded POSReady 7(32비트)  
>     -   Windows ThinPC  
> -   **Windows 7(64비트) 기반 임베디드 운영 체제** 는 다음과 같습니다.  
>   
>      -   Windows Embedded Standard 7(64비트)  
>     -   Windows Embedded POSReady 7(64비트)
