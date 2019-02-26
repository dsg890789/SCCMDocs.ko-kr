---
title: 공동 관리를 사용 하 여 원격 작업
titleSuffix: Configuration Manager
description: Intune에서 공동 관리 장치 원격 작업 실행
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
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755429"
---
# <a name="remote-actions-with-co-management"></a>공동 관리를 사용 하 여 원격 작업

모든 장치를 관리 하는 위치에 상관 없이, 때마다 연결에 연결할 수 있는지 확인 해야 합니다. 각 사용자의 앱 및 데이터를 보호 하면서 생산성을 유지 하는 데 필요한 모든 것에 제공 해야 합니다. Intune에서 지 원하는 장치 동작을 사용 하 여 이러한 중요 한 기능을 원격으로 해결할 수 있습니다.

다음 비디오에서는 Heidi Cheng의 주요 프로그램 관리자 및 선임 프로그램 관리자 Danny Guillory 설명 하 고 공동 관리를 사용 하 여 원격 작업 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Using-Co-Management-to-Execute-Remote-Actions/player]



## <a name="benefits"></a>이점

원격 장치 작업 개인 데이터를 방해 하지 않고 장치에 대 한 관리 제어를 제공 합니다. 이러한 원격 장치 작업을 수행할 수 있습니다. 
- 분실 하거나 도난당 한 장치에서 회사 데이터를 삭제 합니다.  
- 장치 이름 바꾸기  
- 장치를 다시 시작  
- 검토 장치 인벤토리  
- 장치를 원격으로 제어  
- 새로 시작 다시 부팅을 사용 하 여 사전 설치 된 OEM 앱 초기화  
- 모든 Windows 10 장치에서 공장 재설정을 수행  

이러한 함수는 이러한 장치에서 전자 메일 또는 OneDrive에 저장 된 회사 데이터를 보호 하는 중요 하 고 간단한 방법입니다.

이러한 동작에 대 한 자세한 내용은 참조 하세요. [사용 가능한 원격 작업](#available-remote-actions)합니다. 



## <a name="case-studies"></a>사례 연구

Avanade는 글로벌 컨설팅 회사 30,000 직원이 사용 하는 장치를 관리 하려면 원격 작업을 정기적으로 사용 합니다. 에 [최근 블로그 게시물](https://www.microsoft.com/microsoft-365/blog/2018/02/07/the-future-is-on-the-other-side-of-this-bridge/)에 명시 된 Avanade CIO의:

> *Intune 기능에서 즉시이 win 원격 컴퓨터에서 Windows를 다시 설정 하는 기능 이었습니다. 이 항상 모바일 인력의에서 보다 일반적인 분실 하거나 도난당 한 컴퓨터에 대 한 중요 합니다. * 
>  *그렇지 않은 것을 빌드하고 사용자 지정 구성 관리자 패키지에서 유지 관리 하는 기능입니다.*

이러한 원격 작업을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용 가능한 장치 작업](https://docs.microsoft.com/intune/device-management#available-device-actions)합니다.


## <a name="value-proposition"></a>가치 제안

Configuration Manager 장치를 공동 관리 하는 경우 즉시 Configuration Manager 고유 하 게 없는 이러한 함수를 추가 합니다. 이제 Intune에서 지원 되는 모든 원격 작업을 수행할 수 있습니다. 

공동 관리를 사용 하 여 Configuration Manager 장치는 이제 다른 Intune 관리 장치 처럼 합니다. 예를 들어 전체 프로그램이 클라우드에서 같고 인터넷으로 액세스할으로 연결할 수 있습니다. 공동 관리를 사용 하도록 설정 이외의 추가 단계를 수행 하지 않고 이러한 모든 작업을 수행할 수 있습니다.

자동 등록 프로세스를 사용자에 게 투명 하 게 되므로 생산성에 영향을 주지 않습니다. 사용자는 아무 작업도 수행할 필요가 없습니다.


### <a name="available-remote-actions"></a>사용 가능한 원격 작업

Intune에서 이러한 원격 작업을 사용 하면 한 번 [공동 관리를 사용 하도록 설정](/sccm/comanage/how-to-enable) Configuration Manager에서 합니다.

#### <a name="remove-devices"></a>장치 제거
- **사용 중지**: 이 이렇게 관리 되는 앱 및 데이터 제거 (있는 경우), 설정 및 전자 메일 프로필을 해당 장치에 할당 되었습니다. 그러면 장치는 Intune 관리에서 제거 됩니다. 이 프로세스는 다음 발생 시간 장치는 체크 인할 받고 원격 작업 사용 중지 합니다. 사용 중지는 장치에서 사용자의 개인 데이터를 유지합니다.  

- **초기화**: 장치를 공장 기본 설정으로 복원 하는이 작업 합니다. 옵션을 선택 하는 경우 **등록 상태 및 사용자 계정 보존**, 사용자 데이터를 유지 합니다. 그렇지 않으면 드라이브 안전 하 게 지워집니다.  

- **삭제**: Azure portal의 Intune에서 장치를 제거 하려는 경우 특정 장치 창에서 삭제 합니다. 다음에 장치를 체크인할 조직에 저장 된 데이터 제거 됩니다.  

자세한 내용은 [초기화를 사용 하 여 장치를 제거, 사용 중지 또는 수동으로 장치 등록 취소](https://docs.microsoft.com/intune/devices-wipe)합니다.

#### <a name="selective-wipe"></a>선택적 초기화
<!--SCCMDocs issue 973--> 선택 하는 경우는 **앱 선택적 초기화**, 개인 데이터를 제거 하지 않고 회사 앱 데이터를 제거 합니다. 이 작업으로 장치를 보고 될 때 사용 하 여 분실 하거나 도난당 한 합니다. 

자세한 내용은 [Intune 관리 앱에서 회사 데이터만 초기화 하는 방법](https://docs.microsoft.com/intune/apps-selective-wipe)합니다.

#### <a name="sync"></a>동기화
합니다 **동기화** 장치 작업을 수행 하면 선택한 장치가 즉시 체크 인하도록 하 합니다. 장치가 체크 인하면 즉시 받습니다 보류 작업 또는 정책에 할당 했습니다.

이 기능은 즉시의 유효성을 검사 하 고 다음 예약 된 체크 인을 기다리지 않고 할당 한 정책의 문제를 해결 하면 도움이 됩니다.

자세한 내용은 [최신 정책 및 Intune 사용 하 여 작업 하는 장치 동기화](https://docs.microsoft.com/intune/device-sync)합니다.

#### <a name="restart"></a>다시 시작
합니다 **다시 시작** 장치를 다시 시작 장치 작업을 수행 합니다. 이 이렇게 다시 부팅 보류 중 있지만 사용자 작업을 수행 하는 사용할 수 없는 경우에 유용 합니다.

자세한 내용은 [원격으로 Intune에서 장치를 다시 시작](https://docs.microsoft.com/intune/device-restart)합니다.

#### <a name="fresh-start"></a>새로 시작
합니다 **새로 시작** 장치 작업 Windows 10 버전 1703 이상이 실행 하는 장치에 설치 된 모든 앱을 제거 합니다. 새로 시작에 새 장치를 사용 하 여 일반적으로 설치 되는 미리 설치 된 (OEM) 앱을 제거 하는 데 도움이 됩니다.

사용자 데이터를 유지 하지 않으려는 경우 장치의 기본 상태로 복원 합니다. Azure AD에서 등록이 취소 됩니다 하 고 MDM.

앱은 장치의 수에 대 한 표준을 미리 지정 된 경우이 작업에 조건을 충족 하지 않는 것을 제거 합니다.

자세한 내용은 [Intune 사용 하 여 Windows 10 장치를 다시 설정 하려면 사용 하 여 새로 시작](https://docs.microsoft.com/intune/device-fresh-start)합니다. 

#### <a name="remote-control"></a>원격 제어
원격으로 사용 하 여 Intune에서 관리 되는 장치를 관리할 수 있습니다 [TeamViewer](https://www.teamviewer.com/)합니다. TeamViewer는 별도로 획득 하는 제 3 자 프로그램.

자세한 내용은 [Intune 장치 원격 관리를 사용 하 여 TeamViewer](https://docs.microsoft.com/intune/device-profile-android-teamviewer)합니다. 



## <a name="configure"></a>구성

TeamViewer 통해 원격 제어 이외의 Intune에서 이러한 원격 장치 작업을 사용 하려면 추가 설치가 필요 하지 않습니다 하 고 나면 [공동 관리를 사용 하도록 설정](/sccm/comanage/how-to-enable)합니다.

TeamViewer를 사용 하 여 원격 제어에 대 한 자세한 내용은 [Intune 장치 원격 관리를 사용 하 여 TeamViewer](https://docs.microsoft.com/intune/device-profile-android-teamviewer)합니다. 

