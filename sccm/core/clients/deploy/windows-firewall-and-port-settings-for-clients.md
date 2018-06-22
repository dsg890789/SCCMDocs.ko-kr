---
title: Windows 클라이언트 방화벽 및 포트 설정
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 클라이언트에 대한 Windows 방화벽 및 포트 설정을 선택합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: dce4b640-c92f-401a-9873-ce9aa9262014
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 193ee803fd0a6bacf043dbabc6550ef68a4a629a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32337397"
---
# <a name="windows-firewall-and-port-settings-for-clients-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트용 Windows 방화벽 및 포트 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

Windows 방화벽을 실행하는 System Center Configuration Manager의 클라이언트 컴퓨터에서는 보통 해당 사이트와의 통신을 허용하는 예외를 구성해야 합니다. 구성해야 할 예외는 Configuration Manager 클라이언트에서 사용하는 관리 기능에 따라 달라집니다.  

 이러한 관리 기능을 확인하고 Windows 방화벽에서 이러한 예외를 구성하는 방법에 대한 자세한 내용을 보려면 다음 섹션을 참조하십시오.  

##  <a name="BKMK_ModifyingWindowsFirewall"></a> Windows 방화벽에서 허용하는 포트 및 프로그램 수정  
 Windows 방화벽에서 Configuration Manager 클라이언트에 사용할 포트 및 프로그램을 수정하려면 다음 절차를 따르세요.  

#### <a name="to-modify-the-ports-and-programs-permitted-by-windows-firewall"></a>Windows 방화벽에서 허용하는 포트 및 프로그램을 수정하려면  

1.  Windows 방화벽을 실행하는 컴퓨터에서 제어판을 엽니다.  

2.  **Windows 방화벽**을 마우스 오른쪽 단추로 클릭한 후 **열기**를 클릭합니다.  

3.  필요한 예외와 필요한 사용자 지정 프로그램 및 포트를 구성합니다.  

## <a name="programs-and-ports-that-configuration-manager-requires"></a>Configuration Manager에 필요한 프로그램 및 포트  
 다음 Configuration Manager 기능을 사용하려면 Windows 방화벽에서 예외를 구성해야 합니다.  

### <a name="queries"></a>쿼리  
 Windows 방화벽을 실행하는 컴퓨터에서 Configuration Manager 콘솔을 실행하는 경우 쿼리를 처음 실행하면 실패하고 운영 체제에서 statview.exe를 차단 해제할지 묻는 대화 상자가 표시됩니다. statview.exe를 차단 해제하면 이후의 쿼리는 오류 없이 실행됩니다. 쿼리를 실행하기 전에 Windows 방화벽의 **예외** 탭에서 프로그램 및 서비스 목록에 Statview.exe를 수동으로 추가할 수도 있습니다.  

### <a name="client-push-installation"></a>클라이언트 강제 설치  
 클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하려면 Windows 방화벽에서 다음을 예외로 추가합니다.  

-   아웃바운드 및 인바운드: **파일 및 프린터 공유**  

-   인바운드: **WMI(Windows Management Instrumentation)**  

### <a name="client-installation-by-using-group-policy"></a>그룹 정책을 사용하여 클라이언트 설치  
 그룹 정책을 사용하여 Configuration Manager 클라이언트를 설치하려면 Windows 방화벽에서 **파일 및 프린터 공유**를 예외로 추가합니다.  

### <a name="client-requests"></a>클라이언트 요청  
 클라이언트에서 Configuration Manager 사이트 시스템과 통신하도록 하려면 Windows 방화벽에서 다음을 예외로 추가합니다.  

 아웃바운드: TCP 포트 **80** (HTTP 통신용)  

 아웃바운드: TCP 포트 **443** (HTTPS 통신용)  

> [!IMPORTANT]  
>  이러한 포트는 Configuration Manager에서 변경할 수 없는 기본 포트 번호입니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법](../../../core/clients/deploy/configure-client-communication-ports.md)을 참조하세요. 이러한 포트가 기본값에서 변경된 경우 Windows 방화벽에서 일치하는 예외도 구성해야 합니다.  

### <a name="client-notification"></a>클라이언트 알림  
 관리자가 Configuration Manager 콘솔에서 클라이언트 작업을 선택하는 경우에 수행해야 할 작업(예: 컴퓨터 정책 다운로드 또는 맬웨어 검색 시작)에 대해 관리 지점에서 클라이언트 컴퓨터에 알리도록 하려면 Windows 방화벽에서 다음을 예외로 추가합니다.  

 아웃바운드: TCP 포트 **10123**  

 이 통신이 성공하지 못하면 Configuration Manager에서 HTTP 또는 HTTPS의 기존 클라이언트와 관리 지점 간 통신을 사용하도록 자동으로 대체됩니다.  

 아웃바운드: TCP 포트 **80** (HTTP 통신용)  

 아웃바운드: TCP 포트 **443** (HTTPS 통신용)  

> [!IMPORTANT]  
>  이러한 포트는 Configuration Manager에서 변경할 수 없는 기본 포트 번호입니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법](../../../core/clients/deploy/configure-client-communication-ports.md)을 참조하세요. 이러한 포트가 기본값에서 변경된 경우 Windows 방화벽에서 일치하는 예외도 구성해야 합니다.  

### <a name="remote-control"></a>원격 제어  
 Configuration Manager 원격 제어를 사용하려면 다음 포트를 허용합니다.  

-   인바운드: TCP 포트**2701**  

### <a name="remote-assistance-and-remote-desktop"></a>원격 지원 및 원격 데스크톱  
 Configuration Manager 콘솔에서 원격 지원을 시작하려면 클라이언트 컴퓨터의 Windows 방화벽에서 허용된 프로그램 및 서비스 목록에 사용자 지정 프로그램 **Helpsvc.exe** 및 인바운드 사용자 지정 포트 TCP **135**를 추가합니다. **원격 지원** 및 **원격 데스크톱**도 허용해야 합니다. 클라이언트 컴퓨터에서 원격 지원을 시작하면 Windows 방화벽에서 **원격 지원** 및 **원격 데스크톱**을 자동으로 구성하고 허용합니다.  

### <a name="wake-up-proxy"></a>절전 모드 해제 프록시  
 절전 모드 해제 프록시 클라이언트 설정을 사용하는 경우 ConfigMgr Wake-up Proxy라는 새 서비스에서 피어 투 피어 프로토콜을 사용하여 서브넷의 다른 컴퓨터가 절전 모드에서 해제되었는지 확인하고 필요한 경우 해당 컴퓨터를 절전 모드에서 해제합니다. 이 통신은 다음 포트를 사용합니다.  

 아웃바운드: UDP 포트 **25536**  

 아웃바운드: UDP 포트 **9**  

 이러한 포트는 Configuration Manager에서 **절전 모드 해제 프록시 포트 번호(UDP)** 및 **Wake On LAN 포트 번호(UDP)** 라는 **전원 관리** 클라이언트 설정을 사용하여 변경할 수 있는 기본 포트 번호입니다. **전원 관리**를 지정하는 경우: **절전 모드 해제 프록시에 대한 Windows 방화벽 예외입니다.** 옵션으로 클라이언트를 설정하면 클라이언트에 대한 Windows 방화벽에서 이러한 포트가 자동으로 구성됩니다. 그러나 클라이언트가 다른 방화벽을 실행하는 경우에는 이러한 포트 번호에 대한 예외를 수동으로 구성해야 합니다.  

 이러한 포트뿐 아니라 절전 모드 해제 프록시 역시 클라이언트 컴퓨터 간에 ICMP(Internet Control Message Protocol) 에코 요청 메시지를 사용합니다. 이 통신은 네트워크의 다른 클라이언트 컴퓨터가 절전 모드에서 해제되었는지 여부를 확인하는 데 사용됩니다. ICMP는 TCP/IP Ping 명령이라고도 합니다.  

 절전 모드 해제 프록시에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트의 절전 모드 해제 계획](../../../core/clients/deploy/plan/plan-wake-up-clients.md)을 참조하세요.  

### <a name="windows-event-viewer-windows-performance-monitor-and-windows-diagnostics"></a>Windows 이벤트 뷰어, Windows 성능 모니터 및 Windows 진단  
 Configuration Manager 콘솔에서 Windows 이벤트 뷰어, Windows 성능 모니터 및 Windows 진단에 액세스하려면 Windows 방화벽에서 **파일 및 프린터 공유**를 예외로 설정합니다.  

## <a name="ports-used-during-configuration-manager-client-deployment"></a>Configuration Manager 클라이언트 배포 시 사용되는 포트  
 다음 표에는 클라이언트 설치 프로세스 중에 사용되는 포트가 나와 있습니다.  

> [!IMPORTANT]  
>  사이트 시스템 서버와 클라이언트 컴퓨터 간에 방화벽이 있는 경우 방화벽에서 사용자가 선택한 클라이언트 설치 방법에 필요한 포트에 대해 트래픽이 허용되는지 여부를 확인합니다. 예를 들어 방화벽은 보통 SMB(서버 메시지 블록)와 RCP(원격 프로시저 호출)를 차단하므로 클라이언트 강제 설치를 수행할 수 없습니다. 이 시나리오에서는 수동 설치(CCMSetup.exe 실행)나 그룹 정책 기반 클라이언트 설치 등 다른 클라이언트 설치 방법을 사용합니다. 이러한 대체 클라이언트 설치 방법에는 SMB나 RPC가 필요하지 않습니다.  

 클라이언트 컴퓨터에서 Windows 방화벽을 구성하는 방법에 대한 자세한 내용은 [Windows 방화벽에서 허용하는 포트 및 프로그램 수정](#BKMK_ModifyingWindowsFirewall)섹션을 참조하십시오.  

### <a name="ports-that-are-used-for-all-installation-methods"></a>모든 설치 방법에 사용되는 포트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|클라이언트에 대체 상태 지점이 할당된 경우 클라이언트 컴퓨터에서 대체 상태 지점으로의 HTTP(Hypertext Transfer Protocol)|--|80(참고 1 참조, **대체 포트 사용 가능**)|  

### <a name="ports-that-are-used-with-client-push-installation"></a>클라이언트 강제 설치에 사용되는 포트  
 클라이언트 강제 설치에는 다음 표에 나열된 포트뿐 아니라, 네트워크에서 클라이언트 컴퓨터를 사용할 수 있는지 여부를 확인하기 위해 사이트 서버에서 클라이언트 컴퓨터로의 ICMP(Internet Control Message Protocol) 에코 요청 메시지도 사용됩니다. ICMP는 TCP/IP Ping 명령이라고도 합니다. ICMP에는 UDP 또는 TCP 프로토콜 번호가 없으므로 다음 표에는 나와 있지 않습니다. 그러나 방화벽과 같이 연결을 방해하는 네트워크 장치가 있으면 ICMP 트래픽을 허용해야 클라이언트 강제 설치에 성공합니다.  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|사이트 서버와 클라이언트 컴퓨터 간의 SMB(서버 메시지 블록)|--|445|  
|사이트 서버와 클라이언트 컴퓨터 간의 RPC 끝점 매퍼|135|135|  
|사이트 서버와 클라이언트 컴퓨터 간의 RPC 동적 포트|--|동적|  
|HTTP를 통해 연결된 경우 클라이언트 컴퓨터에서 관리 지점으로의 HTTP(Hypertext Transfer Protocol)|--|80(참고 1 참조, **대체 포트 사용 가능**)|  
|HTTPS를 통해 연결된 경우 클라이언트 컴퓨터에서 관리 지점으로의 HTTPS(Secure Hypertext Transfer Protocol)|--|443(참고 1 참조, **대체 포트 사용 가능**)|  

### <a name="ports-that-are-used-with-software-update-point-based-installation"></a>소프트웨어 업데이트 지점 기반 설치에 사용되는 포트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|클라이언트 컴퓨터에서 소프트웨어 업데이트 지점으로의 HTTP(Hypertext Transfer Protocol)|--|80 또는 8530 (참고 2 참조, **Windows Server Update Services**)|  
|클라이언트 컴퓨터에서 소프트웨어 업데이트 지점으로의 HTTPS(Secure Hypertext Transfer Protocol)|--|443 또는 8531 (참고 2 참조, **Windows Server Update Services**)|  
|CCMSetup 명령줄 속성 **/source:&lt;경로\>** 를 지정하는 경우 원본 서버와 클라이언트 컴퓨터 간의 SMB(서버 메시지 블록)|--|445|  

### <a name="ports-that-are-used-with-group-policy-based-installation"></a>그룹 정책 기반 설치에 사용되는 포트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP를 통해 연결된 경우 클라이언트 컴퓨터에서 관리 지점으로의 HTTP(Hypertext Transfer Protocol)|--|80(참고 1 참조, **대체 포트 사용 가능**)|  
|HTTPS를 통해 연결된 경우 클라이언트 컴퓨터에서 관리 지점으로의 HTTPS(Secure Hypertext Transfer Protocol)|--|443(참고 1 참조, **대체 포트 사용 가능**)|  
|CCMSetup 명령줄 속성 **/source:&lt;경로\>** 를 지정하는 경우 원본 서버와 클라이언트 컴퓨터 간의 SMB(서버 메시지 블록)|--|445|  

### <a name="ports-that-are-used-with-manual-installation-and-logon-script-based-installation"></a>수동 설치 및 로그온 스크립트 기반 설치에 사용되는 포트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|클라이언트 컴퓨터와 CCMSetup.exe를 실행하는 네트워크 공유 간의 SMB(서버 메시지 블록)<br /><br /> Configuration Manager를 설치할 때 클라이언트 설치 원본 파일이 복사되어 관리 지점의 *&lt;설치 경로\>* \Client 폴더에서 자동으로 공유됩니다. 그러나 네트워크의 어떤 컴퓨터에나 이러한 파일을 복사하고 새 공유를 만들 수 있습니다. 또는 CCMSetup.exe를 로컬에서 실행(예: 이동식 미디어 사용)하여 이 네트워크 트래픽을 제거할 수 있습니다.|--|445|  
|HTTP(Hypertext Transfer Protocol)를 통해 연결되었고 CCMSetup 명령줄 속성 **/source:&lt;경로\>** 를 지정하지 않은 경우 클라이언트 컴퓨터에서 관리 지점으로의 HTTP|--|80(참고 1 참조, **대체 포트 사용 가능**)|  
|HTTPS(Secure Hypertext Transfer Protocol)를 통해 연결되었고 CCMSetup 명령줄 속성 **/source:&lt;경로\>** 를 지정하지 않은 경우 클라이언트 컴퓨터에서 관리 지점으로의 HTTPS|--|443(참고 1 참조, **대체 포트 사용 가능**)|  
|CCMSetup 명령줄 속성 **/source:&lt;경로\>** 를 지정하는 경우 원본 서버와 클라이언트 컴퓨터 간의 SMB(서버 메시지 블록)|--|445|  

### <a name="ports-that-are-used-with-software-distribution-based-installation"></a>소프트웨어 배포 기반 설치에 사용되는 포트  

|설명|UDP|TCP|  
|-----------------|---------|---------|  
|배포 지점과 클라이언트 컴퓨터 간의 SMB(서버 메시지 블록)|--|445|  
|HTTP를 통해 연결된 경우 클라이언트에서 배포 지점으로의 HTTP(Hypertext Transfer Protocol)|--|80(참고 1 참조, **대체 포트 사용 가능**)|  
|HTTPS를 통해 연결된 경우 클라이언트에서 배포 지점으로의 HTTPS(Secure Hypertext Transfer Protocol)|--|443(참고 1 참조, **대체 포트 사용 가능**)|  

## <a name="notes"></a>참고  
 **1 대체 포트 사용 가능** Configuration Manager에서 이 값의 대체 포트를 정의할 수 있습니다. 사용자 지정 포트를 정의한 경우 IPsec 정책이나 방화벽 구성을 위한 IP 필터 정보를 정의할 때 해당 사용자 지정 포트를 대체합니다.  

 **2 Windows Server Update Services** 기본 웹 사이트(포트 80)나 사용자 지정 웹 사이트(포트 8530)에 WSUS(Windows Server Update Service)를 설치할 수 있습니다.  

 설치 후에 포트를 변경할 수 있습니다. 사이트 계층 전체에 같은 포트 번호를 사용할 필요가 없습니다.  

 HTTP 포트가 80이면 HTTPS 포트는 443이어야 합니다.  

 HTTP 포트가 80 이외인 경우 HTTPS 포트는 해당 번호보다 1 이상 커야 합니다. 예를 들어 8530 및 8531입니다.
