---
title: 기술 미리 보기 1603의 기능
titleSuffix: Configuration Manager
description: Configuration Manager용 Technical Preview 버전 1603에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5f861b72-9f14-4d17-a512-4a79b660abe6
author: aczechowski
ROBOTS: NOINDEX
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: f80c0ca348eb97526aeb571f9f7e1f99cdaa93eb
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75805237"
---
# <a name="capabilities-in-technical-preview-1603-for-configuration-manager"></a>Configuration Manager용 Technical Preview 1603의 기능

*적용 대상: Configuration Manager(기술 미리 보기 분기)*

이 문서에서는 Configuration Manager용 Technical Preview 버전 1603에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 또는 System Center Technical Preview 5를 사용하는 경우 이 버전은 Configuration Manager Technical Preview의 기준선 버전으로 설치됩니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대한 피드백 제공 방법 등에 익숙해져야 합니다.  

 **Technical Preview의 알려진 문제:**  

- 이 릴리스에는 이전에 릴리스된 기능에 대한 업데이트가 포함되어 있지만 새 기능을 제공하지는 않습니다. 따라서는 이전에 1602로 업그레이드하고 1602에 포함된 모든 기능을 사용하도록 설정하는 경우 업데이트 마법사의 기능 페이지가 비어 있게 됩니다.  

- 사이트 서버가 Technical Preview 1603으로 업데이트를 한 후 클라이언트는 버전 1603으로 업데이트될 때까지 모든 원격 제어 기능을 사용할 수 없습니다.  

  **다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

##  <a name="BKMK_SC1603"></a> 소프트웨어 센터 개선  

### <a name="new-tiled-view-for-apps"></a>앱에 대한 바둑판식으로 배열된 새 보기  
 최종 사용자는 이제 소프트웨어 센터의 **애플리케이션** 탭에서 앱 목록과 앱의 바둑판식된 뷰 보기 사이에서 선택할 수 있습니다.  

### <a name="select-multiple-updates-in-software-center"></a>소프트웨어 센터에서 여러 업데이트 선택  
 소프트웨어 센터의 **업데이트** 탭에서 이제 여러 업데이트를 선택하거나 **모두 업데이트**를 선택하여 여러 업데이트를 동시에 설치할 수 있습니다.  

##  <a name="BKMK_RC1603"></a> 원격 제어의 개선 사항  

### <a name="limit-shared-clipboard-access-in-a-remote-control-session"></a>원격 제어 세션에서 공유 클립보드 액세스 제한  
 이제 새 원격 도구 클라이언트 설정 **공유 클립보드 파일 전송 권한에 대해 사용자에게 확인**을 사용하여 원격 제어 세션에서 공유 클립보드에 대한 액세스를 제한할 수 있습니다.  

 이 설정을 사용하도록 설정한 경우 뷰어가 공유 클립보드를 통해 세션에서 로컬 컴퓨터로 파일을 전송하려면 먼저 원격 세션을 공유하는 최종 사용자가 해당 세션의 뷰어에 사용 권한을 부여해야 합니다.  

 그렇게 하면 이전에, 뷰어에 최종 사용자의 컴퓨터에 대한 모든 권한이 부여된 경우 공유 클립보드를 사용하여 최종 사용자에게 완전히 투명한 방식으로 세션에서 로컬 컴퓨터로 파일을 전송할 수 있었던 것처럼 최종 사용자를 위한 보호 계층이 추가됩니다.  

##  <a name="BKMK_RamDiskTFTP"></a> PXE 사용 배포 지점에서 RamDisk TFTP 블록 크기 및 창 크기 사용자 지정  
 1603 Technical Preview에서 PXE 사용 배포 지점에 대한 RamDisk TFTP 블록 크기 및 창 크기를 사용자 지정할 수 있습니다. 네트워크를 사용자 지정한 경우 블록 또는 창 크기가 너무 커서 시간 초과 오류로 인해 부팅 이미지 다운로드가 실패할 수 있습니다. RamDisk TFTP 블록 크기 및 창 크기 사용자 지정을 통해 PXE를 사용하여 특정 네트워크 요구 사항을 충족하는 경우 TFTP 트래픽을 최적화할 수 있습니다.   
환경에서 사용자 지정된 설정을 테스트하여 가장 효율적인 설정을 결정해야 합니다.  

-   **TFTP 블록 크기**: 블록 크기는 서버에서 파일을 다운로드하는 클라이언트로 전송한 데이터 패킷의 크기(RFC 2347에 설명된 대로)입니다. 블록 크기가 클수록 서버가 더 적은 수의 패킷을 전송할 수 있으므로 서버와 클라이언트 간에 더 적은 왕복 지연이 발생합니다. 그러나 큰 블록 크기는 대부분의 PXE 클라이언트 구현에서 지원하지 않는 조각화된 패킷이 됩니다.  

-   **TFTP 창 크기**: TFTP는 전송된 데이터의 각 블록에 대한 승인(ACK) 패킷을 필요로 합니다. 서버는 이전 블록에 대한 ACK 패킷을 받을 때까지 시퀀스의 다음 블록을 전송하지 않습니다. TFTP 창 작업은 창을 채우는 데 드는 데이터 블록 수를 정의할 수 있는 Windows 배포 서비스의 기능입니다. 서버는 창이 채워질 때까지 데이터 블록을 연속적으로 보내면 클라이언트에서 ACK 패킷을 보냅니다. 이 창 크기를 늘리면 클라이언트와 서버 간의 왕복 지연 횟수가 감소되고 부팅 이미지를 다운로드하는 데 필요한 전체 시간이 줄어듭니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

-   PXE 사용 배포 지점에서 RamDisk TFTP 창 크기를 사용자 지정할 수 있습니다.  

-   PXE 사용 배포 지점에서 RamDisk TFTP 블록 크기를 사용자 지정할 수 있습니다.  

### <a name="to-modify-the-ramdisk-tftp-window-size"></a>RamDisk TFTP 창 크기를 수정하려면  

- PXE 사용 배포 지점에 대한 다음 레지스트리 키를 추가하여 RamDisk TFTP 창 크기를 사용자 지정합니다.  

   **위치**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
  이름: RamDiskTFTPWindowSize  

   **형식**: REG_DWORD  

   **값**: &lt;사용자 지정된 창 크기\>  

  기본값은 1입니다(1 데이터 블록이 창을 채움).  

### <a name="to-modify-the-ramdisk-tftp-block-size"></a>RamDisk TFTP 블록 크기를 수정하려면  

- PXE 사용 배포 지점에 대한 다음 레지스트리 키를 추가하여 RamDisk TFTP 창 크기를 사용자 지정합니다.  

   **위치**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
  이름: RamDiskTFTPBlockSize  

   **형식**: REG_DWORD  

   **값**: &lt;사용자 지정된 블록 크기\>  

  기본값은 4096(4k)입니다.  
