---
title: 공동 관리를 사용하는 원격 작업
titleSuffix: Configuration Manager
description: Intune에서 공동 관리 디바이스에 대한 원격 작업 실행
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 4a877bed-f6c4-4048-9421-507dc848af5c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4439aa280edaffbb59f8d49ece58e067a729ec91
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62199457"
---
# <a name="remote-actions-with-co-management"></a>공동 관리를 사용하는 원격 작업

관리하는 모든 디바이스가 어디에 있든, 어디서 연결하든 연결할 수 있는지 확인해야 합니다. 또한 각 사용자에게 생산성을 유지하고, 앱과 데이터를 보호하는 데 필요한 모든 기능을 제공해야 합니다. Intune에서 지원하는 디바이스 작업을 사용하면 이러한 중요 기능을 원격으로 해결할 수 있습니다.

다음 비디오에서는 수석 프로그램 관리자 Heidi Cheng과 선임 프로그램 관리자 Danny Guillory가 공동 관리를 사용하는 원격 작업에 관해 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Using-Co-Management-to-Execute-Remote-Actions/player]



## <a name="benefits"></a>이점

원격 디바이스 작업을 사용하면 개인 데이터에 영향을 주지하고 디바이스를 관리 제어할 수 있습니다. 이러한 원격 디바이스 작업을 사용하여 다음을 수행할 수 있습니다. 
- 분실하거나 도난당한 디바이스에서 회사 데이터 삭제  
- 디바이스 이름 바꾸기  
- 디바이스 다시 시작  
- 디바이스 인벤토리 검토  
- 디바이스를 원격으로 제어  
- 새로 시작 다시 부팅을 사용하여 사전 설치된 OEM 앱 초기화  
- 모든 Windows 10 디바이스에서 초기화 수행  

이러한 기능은 이러한 디바이스에서 메일, OneDrive 등에 저장된 데이터를 보호하는 간단하면서도 중요한 방법입니다.

이러한 작업에 대한 자세한 내용은 [사용 가능한 원격 작업](#available-remote-actions)을 참조하세요. 



## <a name="case-studies"></a>사례 연구

글로벌 컨설팅 회사 Avanade는 정기적으로 원격 작업을 사용하여 30,000여 직원이 사용하는 디바이스를 관리합니다. [최근 블로그 게시물](https://www.microsoft.com/microsoft-365/blog/2018/02/07/the-future-is-on-the-other-side-of-this-bridge/)에서 Avanade의 CIO는 다음과 같이 밝혔습니다.

> *Intune 기능에서 바로 얻을 수 있는 이점은 머신의 Windows를 원격으로 초기화할 수 있다는 것이었습니다. 이 기능은 특히 외근이 잦은 모바일 인력에게 자주 발생하는 머신 분실 또는 도난 사고에 대응하는 데 유용합니다.* 
> *이 기능이 없었다면 사용자 지정 ConfigMgr 패키지를 빌드하고 유지 관리해야 했을 것입니다.*

이러한 원격 작업을 사용하는 방법에 대한 자세한 내용은 [사용 가능한 디바이스 작업](https://docs.microsoft.com/intune/device-management#available-device-actions)을 참조하세요.


## <a name="value-proposition"></a>가치 제안

Configuration Manager 디바이스를 공동 관리하는 경우 Configuration Manager에 기본적으로 없는 이러한 기능이 즉시 추가됩니다. 이제 Intune에서 지원되는 모든 원격 작업을 수행할 수 있습니다. 

공동 관리를 사용하면 Configuration Manager 디바이스가 다른 Intune 관리형 디바이스와 똑같아집니다. 예를 들어 디바이스를 클라우드에서 완전히 사용할 수 있고 인터넷에 연결된 경우 언제든 연결할 수 있습니다. 공동 관리를 사용하도록 설정하는 것 이외에 추가 단계 없이 이러한 작업을 모두 수행할 수 있습니다.

자동 등록 프로세스는 사용자에게 투명하므로 사용자 생산성에 영향을 주지 않습니다. 사용자는 아무 작업도 수행할 필요가 없습니다.


### <a name="available-remote-actions"></a>사용 가능한 원격 작업

Configuration Manager에서 [공동 관리를 사용하도록 설정](/sccm/comanage/how-to-enable)하면 Intune에서 다음 원격 작업을 사용할 수 있습니다.

#### <a name="remove-devices"></a>디바이스 제거
- **사용 중지**: 이 작업은 관리형 앱과 데이터(있는 경우), 설정 및 해당 디바이스에 할당된 메일 프로필을 제거합니다. 그러면 Intune 관리에서 디바이스가 제거됩니다. 이 프로세스는 다음에 디바이스가 체크 인하고 원격 사용 중지 작업을 수신하면 수행됩니다. 사용 중지 기능은 디바이스에서 사용자 개인 데이터는 유지합니다.  

- **초기화**: 이 작업은 디바이스를 공장 기본 설정으로 복원합니다. **등록 상태 및 사용자 계정 보존** 옵션을 선택하는 경우 사용자 데이터는 유지됩니다. 그러지 않으면 드라이브가 완전히 지워집니다.  

- **삭제**: Azure Portal의 Intune에서 디바이스를 제거하려면 특정 디바이스 창에서 삭제합니다. 다음에 디바이스가 체인 인하면 디바이스에 저장된 데이터가 모두 제거됩니다.  

자세한 내용은 [초기화, 사용 중지 또는 수동으로 디바이스 등록을 취소하여 디바이스 제거](https://docs.microsoft.com/intune/devices-wipe)를 참조하세요.

#### <a name="selective-wipe"></a>선택적 초기화
<!--SCCMDocs issue 973-->
**앱 선택적 초기화**를 선택하면 회사 앱 데이터만 제거하고 개인 데이터를 제거하지 않습니다. 이 작업은 디바이스가 분실 또는 도난된 것으로 보고된 경우 사용합니다. 

자세한 내용은 [Intune 관리 앱에서 회사 데이터만 초기화하는 방법](https://docs.microsoft.com/intune/apps-selective-wipe)을 참조하세요.

#### <a name="sync"></a>동기화
**동기화** 디바이스 작업은 Intune을 사용하여 선택한 디바이스를 즉시 체크 인하도록 합니다. 디바이스가 체크 인하면 디바이스에 할당한 보류 중인 작업 또는 정책을 즉시 수신합니다.

이 기능을 사용하면 예정된 다음 체크 인까지 기다리지 않고 할당한 정책을 즉시 유효성 검사하고 문제 해결할 수 있습니다.

자세한 내용은 [디바이스를 동기화하여 Intune에서 최신 정책과 작업 가져오기](https://docs.microsoft.com/intune/device-sync)를 참조하세요.

#### <a name="restart"></a>다시 시작
**다시 시작** 디바이스 작업은 선택한 디바이스를 다시 시작합니다. 이 작업은 보류 중인 다시 부팅이 있지만 사용자가 다시 부팅을 수행할 수 없는 경우 유용합니다.

자세한 내용은 [Intune을 사용하여 원격으로 디바이스 다시 시작](https://docs.microsoft.com/intune/device-restart)을 참조하세요.

#### <a name="fresh-start"></a>새로 시작
**새로 시작** 디바이스 작업은 Windows 10 버전 1703 이상을 실행 중인 디바이스에 설치된 모든 앱을 제거합니다. 새로 시작은 새 디바이스에 일반적으로 설치되는 사전 설치된(OEM) 앱을 제거하는 데 유용합니다.

사용자 데이터를 유지하지 않도록 선택하면 디바이스가 기본 상태로 복원됩니다. Azure AD 및 MDM에서 등록을 취소합니다.

어느 앱을 디바이스에 유지할지를 미리 결정한 기준이 있는 경우 이 작업은 기준에 맞지 않는 앱을 제거합니다.

자세한 내용은 [Intune을 통해 새로 시작 기능을 사용하여 Windows 10 디바이스 재설정](https://docs.microsoft.com/intune/device-fresh-start)을 참조하세요. 

#### <a name="remote-control"></a>원격 제어
Intune에서 관리하는 디바이스를 [TeamViewer](https://www.teamviewer.com/)를 사용하여 원격으로 관리할 수 있습니다. TeamViewer는 별도로 구입하는 타사 프로그램입니다.

자세한 내용은 [TeamViewer를 사용하여 Intune 디바이스 원격 관리](https://docs.microsoft.com/intune/device-profile-android-teamviewer)를 참조하세요. 



## <a name="configure"></a>구성

TeamViewer를 통한 원격 제외 이외에 Intune에서 이러한 원격 디바이스 작업을 사용하려면 [공동 관리를 사용하도록 설정](/sccm/comanage/how-to-enable)하는 것 외에 필요한 추가 설정이 없습니다.

TeamViewer를 사용한 원격 제어에 대한 자세한 내용은 [TeamViewer를 사용하여 Intune 디바이스 원격 관리](https://docs.microsoft.com/intune/device-profile-android-teamviewer)를 참조하세요. 

