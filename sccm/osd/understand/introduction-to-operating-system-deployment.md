---
title: 운영 체제 배포 소개
titleSuffix: Configuration Manager
description: Configuration Manager 환경에 운영 체제를 배포하기 전에 개념을 이해합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: d9a1c545-8301-492c-832f-2c108ff93c77
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d53ab2221e3ee936f9b09592a7c7b383b200c928
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821055"
---
# <a name="introduction-to-operating-system-deployment-in-configuration-manager"></a>Configuration Manager의 운영 체제 배포 소개

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager를 사용하여 다양한 방법으로 운영 체제를 배포할 수 있습니다. 이 섹션의 정보를 사용하여 운영 체제를 배포하고 작업을 자동화하는 방법을 이해합니다. 

##  <a name="BKMK_OSDeploymentProcess"></a> 운영 체제 배포 프로세스  
 Configuration Manager에서는 여러 가지 방법을 사용하여 운영 체제를 배포할 수 있습니다. 사용하는 배포 방법에 관계없이 다음과 같은 여러 작업을 수행해야 합니다.  

-   배포할 부팅 이미지를 시작하거나 운영 체제 이미지를 설치하는 데 필요한 Windows 디바이스 드라이버를 식별합니다.  

-   대상 컴퓨터를 시작하는 데 사용할 부팅 이미지를 식별합니다.  

-   작업 순서를 사용하여 배포할 운영 체제의 이미지를 캡처합니다. 또는 기본 운영 체제 이미지를 사용할 수 있습니다.  

-   배포 지점에 부팅 이미지, 운영 체제 이미지 및 기타 관련 콘텐츠 배포  

-   부팅 이미지와 운영 체제 이미지를 배포하는 작업 순서를 만듭니다.  

-   컴퓨터 컬렉션에 작업 순서를 배포합니다.  

-   배포를 모니터링합니다.  

##  <a name="BKMK_OSDScenarios"></a> 운영 체제 배포 시나리오  
 Configuration Manager에는 사용자 환경 및 운영 체제 설치 용도에 따라 선택할 수 있는 다양한 운영 체제 배포 시나리오가 있습니다.  예를 들어 새 버전의 Windows로 기존 컴퓨터에서 파티션을 만들고 포맷하거나 Windows를 최신 버전으로 업그레이드할 수 있습니다. 요구에 부합하는 배포 방법을 결정하는 데 도움이 되도록 [엔터프라이즈 운영 체제를 배포하는 시나리오](../deploy-use/scenarios-to-deploy-enterprise-operating-systems.md)를 검토하세요.  다음 운영 체제 배포 시나리오 중에서 선택할 수 있습니다.  

-   [최신 버전으로 Windows 업그레이드](../deploy-use/upgrade-windows-to-the-latest-version.md)  

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](../deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](../deploy-use/install-new-windows-version-new-computer-bare-metal.md)  

-   [기존 컴퓨터 바꾸기 및 설정 전송](../deploy-use/replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_OSDMethods"></a> 운영 체제를 배포하는 방법  
 Configuration Manager 클라이언트 컴퓨터에 운영 체제를 배포하는 데 사용할 수 있는 방법에는 여러 가지가 있습니다.  

- **PXE 시작 배포**: PXE 시작 배포를 사용하면 클라이언트 컴퓨터가 네트워크를 통해 배포를 요청합니다. 이 배포 방법에서는 운영 체제 이미지와 Windows PE 부팅 이미지가 PXE 부팅 요청을 수락하도록 구성된 배포 지점으로 전송됩니다. 자세한 내용은 [Configuration Manager에서 PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

- **소프트웨어 센터에서 운영 체제를 사용할 수 있도록 설정**: 운영 체제를 배포하고 소프트웨어 센터에서 사용하도록 설정할 수 있습니다. Configuration Manager 클라이언트는 소프트웨어 센터에서 운영 체제 설치를 시작할 수 있습니다. 자세한 내용은 [기존 컴퓨터 바꾸기 및 설정 전송](../deploy-use/replace-an-existing-computer-and-transfer-settings.md)을 참조하세요.  

- **멀티캐스트 배포**: 멀티캐스트 배포는 각 클라이언트에 별도의 연결을 통해 데이터 복사본을 전송하는 대신 여러 클라이언트에 동시에 데이터를 전송하여 네트워크 대역폭을 절감합니다. 이 배포 방법에서는 운영 체제 이미지가 배포 지점으로 전송됩니다. 그런 다음 클라이언트 컴퓨터가 배포를 요청할 때 이미지를 배포합니다. 자세한 내용은 [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md)를 참조하세요.  

- **부팅 가능한 미디어 배포**: 부팅 가능한 미디어 배포를 사용하면 대상 컴퓨터가 시작될 때 운영 체제를 배포할 수 있습니다. 대상 컴퓨터는 시작될 때 작업 순서, 운영 체제 이미지 및 기타 필요한 콘텐츠를 네트워크에서 검색합니다. 해당 콘텐츠는 미디어에 포함되어 있지 않기 때문에 미디어를 다시 만들지 않고도 콘텐츠를 업데이트할 수 있습니다. 자세한 내용은 [부팅 가능한 미디어 만들기](../deploy-use/create-bootable-media.md)를 참조하세요.  

- **독립 실행형 미디어 배포**: 독립 실행형 미디어 배포를 사용하면 다음 상태에서 운영 체제를 배포할 수 있습니다.  

  - 운영 체제 이미지 또는 기타 대규모 패키지를 네트워크를 통해 복사하는 것이 불가능한 환경  

  - 네트워크 연결이 없거나 대역폭이 낮은 네트워크 연결 환경  

    자세한 내용은 [독립 실행형 미디어 만들기](../deploy-use/create-stand-alone-media.md)를 참조하세요.  

- **사전 준비된 미디어 배포**: 사전 준비된 미디어 배포를 사용하면 완전히 프로비전되지 않은 컴퓨터에 운영 체제를 배포할 수 있습니다. 사전 준비된 미디어는 제조업체가 운영 체제 미설치 컴퓨터에 설치하거나, Configuration Manager 환경에 연결되지 않은 엔터프라이즈 준비 센터에 설치할 수 있는 WIM(Windows Imaging Format) 파일입니다.  

   Configuration Manager 환경에서 이후에 미디어에서 제공된 부팅 이미지를 사용하여 컴퓨터가 시작된 다음 사이트 관리 지점에 연결되어 사용 가능한 작업 순서를 통해 다운로드 프로세스를 완료하게 됩니다. 이 배포 방법에서는 부팅 이미지와 운영 체제 이미지가 이미 대상 컴퓨터에 있으므로 네트워크 트래픽을 줄일 수 있습니다. 사전 준비된 미디어에 포함할 애플리케이션, 패키지 및 드라이버 패키지를 지정할 수 있습니다. 자세한 내용은 [사전 준비된 미디어 만들기](../deploy-use/create-prestaged-media.md)를 참조하세요.  

##  <a name="BKMK_BootImages"></a> 부팅 이미지  
 Configuration Manager의 부팅 이미지는 운영 체제 배포 중에 사용되는 WinPE(Windows PE) 이미지입니다. 부팅 이미지는 Windows 설치용 대상 컴퓨터를 준비하는 제한된 구성 요소 및 서비스가 포함된 최소 운영 체제인 WinPE에서 컴퓨터를 시작하는 데 사용됩니다. Configuration Manager에서 두 개의 부팅 이미지 제공: x86 플랫폼을 지원하는 부팅 이미지와 x64 플랫폼을 지원하는 부팅 이미지의 두 가지 부팅 이미지를 제공합니다. 이러한 이미지는 기본 부팅 이미지로 간주됩니다. 만들어 Configuration Manager에 추가하는 부팅 이미지는 사용자 지정 이미지로 간주됩니다. Configuration Manager 업데이트 시 기본 부팅 이미지가 자동으로 바뀔 수 있습니다. 부팅 이미지에 대한 자세한 내용은 [부팅 이미지 관리](../get-started/manage-boot-images.md)를 참조하세요.  

##  <a name="BKMK_OSImages"></a> 운영 체제 이미지  
 Configuration Manager의 운영 체제 이미지는 WIM(Windows Imaging) 형식 파일으로 저장되며 컴퓨터에 운영 체제를 성공적으로 설치하고 구성하는 데 필요한 참조 파일 및 폴더의 압축된 컬렉션을 나타냅니다. 모든 운영 체제 배포 시나리오에서 운영 체제 이미지를 선택해야 합니다. 기본 운영 체제 이미지를 사용하거나 구성한 참조 컴퓨터에서 운영 체제 이미지를 작성할 수 있습니다. 자세한 내용은 [운영 체제 이미지 관리](../get-started/manage-operating-system-images.md)를 참조하세요.  

##  <a name="BKMK_OSUpgradePackages"></a> 운영 체제 업그레이드 패키지  
 운영 체제 업그레이드 패키지는 운영 체제를 업그레이드하는 데 사용되며 설치 프로그램을 통해 시작된 운영 체제 배포입니다. DVD 또는 탑재된 ISO 파일의 운영 체제 업그레이드 패키지를 Configuration Manager로 가져옵니다. 자세한 내용은 [운영 체제 업그레이드 패키지 관리](../get-started/manage-operating-system-upgrade-packages.md)를 참조하세요.  

##  <a name="BKMK_OSDMedia"></a> 운영 체제를 배포하기 위한 미디어  
 여러 종류의 미디어를 만들어서 운영 체제를 배포하는 데 사용할 수 있습니다. 이러한 미디어로는 운영 체제 이미지를 캡처하는 데 사용되는 미디어 캡처와 운영 체제를 배포하는 데 사용되는 독립 실행형, 사전 준비 및 부팅 가능한 미디어 등이 있습니다. 미디어를 사용하면 Configuration Manager 사이트에 대한 네트워크 연결이 없거나 대역폭이 낮은 네트워크 연결을 사용하는 컴퓨터에 운영 체제를 배포할 수 있습니다. 미디어를 사용하는 방법에 대한 자세한 내용은 [작업 순서 미디어 만들기](../deploy-use/create-task-sequence-media.md)를 참조하세요.  

##  <a name="BKMK_DeviceDrivers"></a> 디바이스 드라이버  
 디바이스 드라이버를 배포 중인 운영 체제 이미지에 포함하지 않고 대상 컴퓨터에 설치할 수 있습니다. Configuration Manager에서는 Configuration Manager로 가져오는 모든 디바이스 드라이버에 대한 참조를 포함하는 드라이버 카탈로그를 제공합니다. 드라이버 카탈로그는 **소프트웨어 라이브러리** 작업 영역에 있으며 **드라이버** 및 **드라이버 패키지**의 두 노드로 구성되어 있습니다. **드라이버** 노드에는 드라이버 카탈로그로 가져온 모든 드라이버가 나열됩니다. 이 노드를 사용하여, 가져온 각 드라이버에 대한 자세한 정보를 검색하고, 드라이버가 속한 드라이버 패키지 또는 부팅 이미지를 변경하고, 드라이버를 사용하거나 사용하지 않도록 설정하는 등 다양한 작업을 수행할 수 있습니다. 자세한 내용은 [드라이버 관리](../get-started/manage-drivers.md)를 참조하세요.  

##  <a name="BKMK_OSDUserState"></a> 사용자 상태 저장 및 복원  
 운영 체제를 배포할 때 대상 컴퓨터에서 사용자 상태를 저장하고 운영 체제를 배포한 후에 사용자 상태를 복원할 수 있습니다. 이 프로세스는 일반적으로 Configuration Manager 클라이언트 컴퓨터에 운영 체제를 설치할 때 사용됩니다.  

 사용자 상태 정보는 작업 순서를 사용하여 캡처 및 복원됩니다. 사용자 상태 정보는 캡처 시 다음 방식 중 하나로 저장될 수 있습니다.  

- 상태 마이그레이션 지점을 구성하여 원격으로 사용자 상태 데이터를 저장할 수 있습니다. 캡처 작업 순서가 데이터를 상태 마이그레이션 지점으로 전송합니다. 그런 다음 운영 체제가 배포된 후에 복원 작업 순서가 데이터를 검색하여 대상 컴퓨터에서 사용자 상태를 복원합니다.  

- 사용자 상태 데이터를 특정 위치에 로컬로 저장할 수 있습니다. 이 시나리오에서는 캡처 작업 순서가 사용자 데이터를 대상 컴퓨터의 특정 위치로 복사합니다. 그런 다음 운영 체제가 배포된 후에 복원 작업 순서가 해당 위치에서 사용자 데이터를 검색합니다.  

- 하드 링크를 지정하여 사용자 데이터를 원래 위치로 복원하는 데 사용할 수 있습니다. 이 시나리오에서는 이전 운영 체제를 제거할 때 드라이브에 사용자 상태 데이터가 유지됩니다. 그런 다음 운영 체제가 배포된 후에 복원 작업 순서가 하드 링크를 사용하여 사용자 상태 데이터를 원래 위치로 복원합니다.  

  자세한 내용은 [사용자 상태 관리](../get-started/manage-user-state.md)를 참조하세요.  

##  <a name="BKMK_UnknownComputer"></a> 알 수 없는 컴퓨터에 배포  
 Configuration Manager에서 관리하지 않는 컴퓨터에 운영 체제를 배포할 수 있습니다. Configuration Manager 데이터베이스에 이러한 컴퓨터의 레코드가 없습니다. 이러한 컴퓨터를 알 수 없는 컴퓨터라고 합니다. 알 수 없는 컴퓨터는 다음과 같습니다.  

- Configuration Manager 클라이언트가 설치되지 않은 컴퓨터  

- Configuration Manager로 가져오지 않은 컴퓨터  

- Configuration Manager에서 검색되지 않은 컴퓨터  

  자세한 내용은 [알 수 없는 컴퓨터 배포 준비](../get-started/prepare-for-unknown-computer-deployments.md)를 참조하세요.  

##  <a name="BKMK_UDA"></a> 사용자와 컴퓨터 연결  
 운영 체제를 배포할 때 사용자 디바이스 선호도 작업을 지원하도록 사용자를 대상 컴퓨터와 연결할 수 있습니다. 사용자를 대상 컴퓨터와 연결하면 관리자가 나중에 사용자와 연결된 컴퓨터에 대한 작업을 수행할 수 있습니다. 예를 들어 특정 사용자의 컴퓨터에 애플리케이션을 배포할 수 있습니다. 그러나 운영 체제를 배포할 때에는 특정 사용자의 컴퓨터에 운영 체제를 배포할 수 없습니다. 자세한 내용은 [사용자를 대상 컴퓨터에 연결](../get-started/associate-users-with-a-destination-computer.md)을 참조하세요.  

##  <a name="BKMK_TaskSequences"></a> 작업 순서를 사용하여 단계 자동화  
 Configuration Manager 환경 내에서 다양한 작업을 수행하는 작업 순서를 만들 수 있습니다. 작업 순서의 각 단계에는 작업 순서의 작업이 정의되어 있습니다. 작업 순서가 실행될 때 각 단계의 작업은 사용자 개입이 필요 없이 명령줄 수준에서 수행됩니다. 다음에 대한 작업 순서를 사용할 수 있습니다.  

-   [운영 체제를 설치하는 작업 순서 만들기](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md)  

-   [비운영 체제 배포에 대한 작업 순서 만들기](../deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)  

-   [운영 체제를 캡처하는 작업 순서 만들기](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)  

-   [사용자 상태를 캡처 및 복원하는 작업 순서 만들기](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)  

-   [사용자 지정 작업 순서 만들기](../deploy-use/create-a-custom-task-sequence.md)  
