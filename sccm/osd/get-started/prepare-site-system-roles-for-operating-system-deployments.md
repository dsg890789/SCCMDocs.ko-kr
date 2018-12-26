---
title: OSD를 위한 사이트 시스템 역할 준비
titleSuffix: Configuration Manager
description: Configuration Manager에서 운영 체제를 배포하기 전에 사이트 시스템 역할 구성
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 0ef5f3ce-b0e4-4775-b5c2-b245e45b4194
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cbfa49dddb19d588a3fe16f042b50af590cf39e8
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39383731"
---
# <a name="prepare-site-system-roles-for-os-deployments-with-configuration-manager"></a>Configuration Manager를 사용하여 OS 배포를 위한 사이트 시스템 역할 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 운영 체제를 배포하려면 먼저 특정 구성과 고려 사항을 요구하는 다음과 같은 사이트 시스템 역할을 준비합니다.



##  <a name="BKMK_DistributionPoints"></a> 배포 지점  

배포 지점 사이트 시스템 역할은 클라이언트가 다운로드할 원본 파일을 호스팅합니다. 애플리케이션, 소프트웨어 업데이트, OS 이미지, 부팅 이미지 및 드라이버 패키지에 대한 콘텐츠입니다. 대역폭, 제한 및 예약 옵션을 사용하여 콘텐츠 배포를 제어합니다.  

컴퓨터에 대한 운영 체제 배포를 지원할 만큼 충분한 배포 지점이 있어야 하고, 계층 구조에서 이러한 배포 지점의 배치를 계획해야 합니다. 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요. 이 아티클에는 OS 배포에 따라 배포 지점을 계획할 때 추가로 고려할 몇 가지 사항이 있습니다.  


###  <a name="BKMK_AdditionalPlanning"></a> 배포 지점을 계획할 때 추가로 고려할 사항  

배포 지점을 계획할 때 추가로 고려할 사항은 다음 항목과 같습니다.  

#### <a name="how-can-i-prevent-unwanted-os-deployments"></a>원치 않는 OS 배포를 방지하는 방법  
Configuration Manager는 컬렉션 내의 다른 대상 컴퓨터와 사이트 서버를 구분하지 않습니다. 사이트 서버가 포함된 컬렉션에 필수 작업 순서를 배포하면 해당 서버는 컬렉션에 있는 다른 컴퓨터와 동일한 방식으로 작업 순서를 실행합니다. OS 배포가 의도한 클라이언트를 포함한 컬렉션을 사용하도록 합니다.  

위험 수준이 높은 작업 순서 배포의 동작을 관리합니다. 위험 수준이 높은 배포는 클라이언트에 자동으로 설치되며 원치 않는 결과가 발생할 수 있습니다. 예를 들어 OS를 배포하는 데 필요한 작업 순서입니다. 위험 수준이 높은 불필요한 배포가 수행될 위험을 줄이려는 경우 배포 확인 설정을 구성합니다. 자세한 내용은 [높은 위험 수준의 배포를 관리하는 설정](/sccm/core/servers/manage/settings-to-manage-high-risk-deployments)을 참조하세요.  

#### <a name="how-many-computers-can-receive-an-os-image-at-one-time-from-a-single-distribution-point"></a>단일 배포 지점에서 한 번에 OS 이미지를 받을 수 있는 컴퓨터 수는 몇 대인가요?  
필요한 배포 지점 수를 예측하려면 다음 변수를 고려합니다.  
- 배포 지점의 처리 속도
- 배포 지점의 디스크 속도
- 네트워크에서 사용 가능한 대역폭
- 이미지 패키지의 크기   
  
예를 들어 다른 서버 리소스 요소를 고려하지 않는 경우 100메가바이트(MB)/초 이더넷 네트워크에서 1시간 안에 4GB의 이미지 패키지를 처리할 수 있는 최대 컴퓨터 수는 11대입니다.  

`100 megabits/sec = 12.5 megabytes/sec = 750 megabytes/min = 45 gigabytes/hour = 11 images @ 4 GB per image`  

지정된 시간 안에 특정 수의 컴퓨터에 OS 배포를 수행해야 하는 경우 이미지를 적절한 수의 배포 지점에 배포합니다.  

#### <a name="can-i-deploy-an-os-to-a-distribution-point"></a>배포 지점에 OS를 배포할 수 있나요?  
배포 지점에 OS를 배포할 수 있지만 다른 배포 지점에서 OS 이미지를 받아야 합니다.  


###  <a name="BKMK_PXEDistributionPoint"></a> PXE 요청을 수락하도록 배포 지점 구성  

PXE 부팅 요청을 만드는 Configuration Manager 클라이언트에 운영 체제를 배포하려면 PXE 요청을 수락하도록 하나 이상의 배포 지점을 구성합니다. 구성하고 나면 배포 지점에서 PXE 부팅 요청에 응답하고 수행해야 할 적절한 배포 작업을 결정합니다. 자세한 내용은 [배포 지점 설치 또는 수정](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  


###  <a name="BKMK_RamDiskTFTP"></a> PXE 사용 배포 지점에서 RamDisk TFTP 블록 및 창 크기 사용자 지정  

PXE 사용 배포 지점의 RamDisk TFTP 블록 및 창 크기를 사용자 지정할 수 있습니다. 네트워크를 사용자 지정한 경우 블록 또는 창 크기가 너무 커서 시간 초과 오류로 부팅 이미지 다운로드가 실패할 수 있습니다. RamDisk TFTP 블록 및 창 크기 사용자 지정을 통해 PXE를 사용하여 특정 네트워크 요구 사항을 충족하는 경우 TFTP 트래픽을 최적화할 수 있습니다. 가장 효율적인 구성을 결정하기 위해 환경에서 사용자 지정된 설정을 테스트합니다.  

-   **TFTP 블록 크기**: 블록 크기는 서버가 파일을 다운로드하는 클라이언트로 전송한 데이터 패킷의 크기입니다. 블록 크기가 클수록 서버가 더 적은 수의 패킷을 전송할 수 있으므로 서버와 클라이언트 간에 더 적은 왕복 지연이 발생합니다. 그러나 큰 블록 크기는 대부분의 PXE 클라이언트 구현에서 지원하지 않는 조각화된 패킷이 됩니다.  

-   **TFTP 창 크기**: TFTP는 전송된 데이터의 각 블록에 대한 승인(ACK) 패킷을 필요로 합니다. 서버는 이전 블록에 대한 ACK 패킷을 받을 때까지 시퀀스의 다음 블록을 전송하지 않습니다. TFTP 창 작업을 사용하면 창을 채우는 데 드는 데이터 블록의 수를 정의할 수 있습니다. 서버는 창이 채워질 때까지 데이터 블록을 연속적으로 보내면 클라이언트에서 ACK 패킷을 보냅니다. 이 창 크기를 늘리면 클라이언트와 서버 간의 왕복 지연 횟수가 감소되고 부팅 이미지를 다운로드하는 데 필요한 전체 시간이 줄어듭니다.  
  

#### <a name="modify-the-ramdisk-tftp-window-size"></a>RamDisk TFTP 창 크기 수정  
RamDisk TFTP 창 크기를 사용자 지정하려면 PXE 사용 배포 지점에 대한 다음 레지스트리 키를 추가합니다.  

- **위치**: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP`  
- **이름**: RamDiskTFTPWindowSize  
- **형식**: REG_DWORD  
- **값**: (사용자 지정된 창 크기)  
    - 기본값은 **1**입니다(하나의 데이터 블록이 창을 채움).  

#### <a name="modify-the-ramdisk-tftp-block-size"></a>RamDisk TFTP 블록 크기 수정  
RamDisk TFTP 창 크기를 사용자 지정하려면 PXE 사용 배포 지점에 대한 다음 레지스트리 키를 추가합니다.  

- **위치**: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP`  
- **이름**: RamDiskTFTPBlockSize  
- **형식**: REG_DWORD  
- **값**: (사용자 지정된 블록 크기)  
    - 기본값은 **4096**입니다.  

> [!Note]  
> Windows 배포 서비스와 Configuration Manager PXE 응답기 서비스는 모두 이러한 TFTP 구성을 지원합니다.  


###  <a name="BKMK_DPMulticast"></a> 멀티캐스트를 지원하도록 배포 지점 구성  

멀티캐스트는 네트워크 최적화 메서드입니다. 여러 클라이언트가 동시에 같은 OS 이미지를 다운로드할 가능성이 있는 경우 배포 지점에서 사용합니다. 멀티캐스트를 사용하는 경우 배포 지점에 의한 멀티캐스트이므로 여러 컴퓨터가 동시에 OS 이미지를 다운로드할 수 있습니다. 멀티캐스트가 아니면 배포 지점은 별도 연결을 통해 각 클라이언트에 데이터의 복사본을 보냅니다. 자세한 내용은 [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)를 참조하세요.  

OS를 배포하기 전에 멀티캐스트를 지원하도록 배포 지점을 구성해야 합니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-multicast)을 참조하세요.



##  <a name="BKMK_StateMigrationPoints"></a> 상태 마이그레이션 지점  

상태 마이그레이션 지점에서는 USMT가 한 컴퓨터에서 캡처한 다음, 다른 컴퓨터에서 복원한 사용자 상태 데이터를 저장합니다. 그러나 대상 컴퓨터에서 Windows를 새로 고치는 배포와 같이 동일한 컴퓨터에서 OS 배포에 대한 사용자 설정을 캡처하는 경우에는 하드 링크를 사용하여 동일한 컴퓨터에 데이터를 저장할지 여부를 선택하거나 상태 마이그레이션 지점을 사용할 수 있습니다. 일부 컴퓨터 배포에 대해 상태 저장소를 만들 경우 Configuration Manager에서 이 상태 저장소와 대상 컴퓨터 간에 자동으로 연결을 만듭니다. 상태 마이그레이션 지점을 계획할 경우 다음 요소를 고려하세요.    


### <a name="user-state-size"></a>사용자 상태 크기  

사용자 상태의 크기는 상태 마이그레이션 지점의 디스크 저장소와 마이그레이션 중 네트워크 성능에 직접적인 영향을 미칩니다. 사용자 상태의 크기와 마이그레이션할 컴퓨터의 수를 적절히 고려해야 합니다. 또한 컴퓨터에서 어떤 설정을 마이그레이션할지 고려해야 합니다. 예를 들어 **내 문서** 폴더가 이미 서버에 백업되어 있는 경우 이미지 배포의 일부로 마이그레이션할 필요가 없습니다. 불필요한 마이그레이션을 생략하면 사용자 상태의 전체 크기를 줄이고 네트워크 성능과 상태 마이그레이션 지점의 디스크 저장소에 미칠 수 있는 영향을 감소시킵니다.  


### <a name="user-state-migration-tool"></a>사용자 상태 마이그레이션 도구  

운영 체제를 배포하는 동안 사용자 상태를 캡처 및 복원하려면 USMT 원본 파일을 가리키는 USMT(사용자 상태 마이그레이션 도구) 패키지를 사용합니다. Configuration Manager는 Configuration Manager 콘솔의 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **패키지**에서 이 패키지를 자동으로 만듭니다. Configuration Manager는 USMT 10을 사용하여 하나의 OS에서 사용자 상태 캡처한 다음, 다른 OS로 복원합니다. Windows 10용 Windows ADK(Assessment and Deployment Kit)에는 USMT 10이 포함됩니다.

USMT 10에 대한 여러 마이그레이션 시나리오 설명은 Windows 설명서에서 [일반적인 마이그레이션 시나리오](https://docs.microsoft.com/windows/deployment/usmt/usmt-common-migration-scenarios)를 참조하세요.  


### <a name="retention-policy"></a>보존 정책  

상태 마이그레이션 지점을 구성할 때 여기에 저장되는 사용자 상태 데이터를 유지할 기간을 지정합니다. 상태 마이그레이션 지점에 데이터를 보존하는 기간은 다음 두 가지 고려 사항에 따라 달라집니다.  

-   저장된 데이터가 디스크 저장소에 미치는 영향  

-   데이터를 다시 마이그레이션할 경우에 대비해 일정 기간 데이터를 보존해야 하는 잠재적 요구 사항  
  
  
상태 마이그레이션은 데이터 캡처 및 데이터 복원이라는 두 단계로 진행됩니다. 데이터를 캡처하면 사용자 상태 데이터가 수집되어 상태 마이그레이션 지점에 저장됩니다. 데이터를 복원하면 사용자 상태 데이터가 상태 마이그레이션 지점에서 검색되어 대상 컴퓨터에 기록된 다음 **상태 저장소 해제** 작업 순서 단계에서 저장된 데이터를 해제합니다. 데이터가 해제되면 보존 타이머가 시작됩니다. 마이그레이션된 데이터를 즉시 삭제하는 옵션을 선택하면 사용자 상태 데이터는 해제되는 즉시 삭제됩니다. 데이터를 일정 기간 동안 보존하는 옵션을 선택하면 상태 데이터는 해제되고 나서 해당 기간이 경과할 때 삭제됩니다. 보존 기간을 길게 설정할수록 더 많은 디스크 공간이 필요해집니다.  


### <a name="select-drive-to-store-user-state-migration-data"></a>사용자 상태 마이그레이션 데이터를 저장할 드라이브 선택  

상태 마이그레이션 지점을 구성할 때 서버에서 사용자 상태 마이그레이션 데이터를 저장할 드라이브를 지정합니다. 이 경우 고정 드라이브 목록에서 드라이브를 선택해야 합니다. 그러나 이러한 드라이브 중 일부는 CD 드라이브나 비네트워크 공유 드라이브와 같이 쓰기 불가능한 드라이브일 수도 있습니다. 일부 드라이브 문자는 컴퓨터의 어떤 드라이브에도 매핑되지 않을 수 있습니다. 상태 마이그레이션 지점을 구성할 경우 쓰기 가능한 공유 드라이브를 지정합니다.  


### <a name="configure-a-state-migration-point"></a>상태 마이그레이션 지점 구성  

다음 방법을 사용하여 사용자 상태 데이터를 저장하도록 상태 마이그레이션 지점을 구성합니다.  

-   **사이트 시스템 서버 만들기 마법사** 를 사용하여 상태 마이그레이션 지점을 위한 새 사이트 시스템 서버를 만듭니다.  

-   **사이트 시스템 역할 추가 마법사** 를 사용하여 기존 서버에 상태 마이그레이션 지점을 추가합니다.  

이러한 마법사를 사용하는 경우 상태 마이그레이션 지점에 대한 다음 정보를 제공해야 합니다.  

-   사용자 상태 데이터를 저장하는 폴더  

-   상태 마이그레이션 지점에 데이터를 저장할 수 있는 최대 클라이언트 수  

-   상태 마이그레이션 지점이 사용자 상태 데이터를 저장하는 데 사용할 수 있는 최소 공간  

-   역할에 대한 삭제 정책. 사용자 상태 데이터가 컴퓨터에서 복원되고 나서 즉시 또는 특정 일수 후에 데이터를 삭제하도록 지정합니다.  

-   상태 마이그레이션 지점이 사용자 상태 데이터를 복원하는 요청에만 응답하도록 할지 여부. 이 옵션을 사용하면 상태 마이그레이션 지점을 사용하여 사용자 상태 데이터를 저장할 수 없습니다.  

사이트 시스템 역할을 설치하는 단계는 [사이트 시스템 역할 추가](/sccm/core/servers/deploy/configure/add-site-system-roles)를 참조하세요.  
