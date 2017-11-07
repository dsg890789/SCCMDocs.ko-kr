---
title: "엔터프라이즈 운영 체제를 배포하는 시나리오"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager를 사용하여 엔터프라이즈 운영 체제를 배포하는 여러 시나리오에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f74fdb86-c7c2-447f-91f6-b42df6370d7f
caps.latest.revision: "11"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d7934c3d757ec0ede6553d9c17b3d36117da3892
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="scenarios-to-deploy-enterprise-operating-systems-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 엔터프라이즈 운영 체제를 배포하는 시나리오

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 운영 체제 배포 시나리오는 System Center Configuration Manager에서 사용할 수 있습니다.  

-   [최신 버전으로 Windows 업그레이드](upgrade-windows-to-the-latest-version.md): 이 시나리오는 현재 Windows 7, Windows 8, Windows 8.1 또는 Windows 10을 실행하는 컴퓨터의 운영 체제를 업그레이드합니다. 이 업그레이드 프로세스에서 컴퓨터의 응용 프로그램, 설정 및 사용자 데이터는 그대로 유지됩니다. Windows ADK 및 이 프로세스는 기존 운영 체제 배포보다 더욱 빠르고 복원력이 뛰어나므로 외부 종속성이 없습니다.  

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md): 이 시나리오에서는 기존 컴퓨터를 파티션으로 나누고 포맷(초기화)한 다음 컴퓨터에 새 운영 체제를 설치합니다. 운영 체제가 설치된 후 설정 및 사용자 데이터를 마이그레이션할 수 있습니다.  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md): 이 시나리오는 새 컴퓨터에 운영 체제를 설치합니다. 이것은 운영 체제를 새로 설치하는 방법이며 설정 또는 사용자 데이터 마이그레이션은 포함되지 않습니다.  

-   [기존 컴퓨터 바꾸기 및 설정 전송](replace-an-existing-computer-and-transfer-settings.md): 이 시나리오는 새 컴퓨터에 운영 체제를 설치합니다. 필요에 따라 이전 컴퓨터의 설정 및 사용자 데이터를 새 컴퓨터로 마이그레이션할 수 있습니다.  

## <a name="things-to-consider-before-you-deploy-operating-system-images"></a>운영 체제 이미지를 배포하기 전에 고려해야 할 사항  
 운영 체제를 배포하기 전에 고려해야 할 사항이 있습니다.  

### <a name="operating-system-image-size"></a>운영 체제 이미지 크기  
 운영 체제 이미지 크기는 매우 클 수 있습니다. 예를 들어 Windows 7의 이미지 크기는 3GB 이상입니다. 운영 체제를 동시에 배포하는 컴퓨터 수와 이미지 크기는 네트워크 성능 및 사용 가능한 대역폭에 영향을 줍니다. 이미지 배포가 줄 수 있는 영향 및 배포를 완료하는 데 걸리는 시간을 더욱 효율적으로 측정할 수 있도록 네트워크 성능을 테스트해야 합니다. 네트워크 성능에 영향을 주는 Configuration Manager 작업에는 배포 지점에 이미지 배포, 특정 사이트의 이미지를 다른 사이트에 배포, Configuration Manager 클라이언트에 이미지 다운로드 등이 있습니다.  

 또한, 운영 체제 이미지를 호스팅하는 배포 지점에 충분한 디스크 저장 공간을 계획해야 합니다.  

### <a name="client-cache-size"></a>클라이언트 캐시 크기  
 BITS(Background Intelligent Transfer Service)를 사용할 수 있는 경우 Configuration Manager 클라이언트에서 콘텐츠를 다운로드할 때 자동으로 BITS를 사용합니다. 운영 체제를 설치하는 작업 순서를 배포할 때 Configuration Manager 클라이언트에서 작업 순서를 실행하기 전에 전체 이미지를 로컬 캐시에 다운로드하도록 배포에 대한 옵션을 설정할 수 있습니다.  

 일반적으로 Configuration Manager 클라이언트에서 운영 체제 이미지(또는 다른 패키지)를 다운로드해야 하지만 캐시에 충분한 공간이 없을 경우 클라이언트가 캐시의 다른 패키지를 확인하고 가장 오래된 패키지의 일부 또는 전부를 삭제하여 이미지를 수용할 디스크 공간을 확보할지 여부를 결정합니다. 패키지를 삭제해도 디스크 공간이 충분히 확보되지 않으면 클라이언트에서 이미지를 다운로드하지 않으며 배포에 실패합니다. 이 시나리오는 캐시에 보관하도록 구성된 대용량 패키지가 캐시에 있는 경우에 발생할 수 있습니다. 패키지를 삭제할 경우 캐시의 디스크 공간이 충분히 확보되면 클라이언트에서 패키지를 삭제한 다음 이미지를 캐시에 다운로드합니다.  

 Configuration Manager 클라이언트의 기본 캐시 크기는 대부분의 운영 체제 이미지 배포에 충분하지 않을 수 있습니다. 클라이언트 캐시에 전체 이미지를 다운로드하려면 배포할 이미지 크기를 포함할 수 있도록 대상 컴퓨터의 Configuration Manager 클라이언트 캐시 크기를 조정해야 합니다.  

 자세한 내용은 [Configure the Client Cache for Configuration Manager Clients](../../core/clients/manage/manage-clients.md#BKMK_ClientCache)항목을 참조하세요.  

## <a name="task-sequence-deployments"></a>작업 순서 배포  
 만들어진 작업 순서는 다음 중 한 가지 방법으로 Configuration Manager 클라이언트 컴퓨터에 운영 체제 이미지를 배포할 수 있습니다.  

-   먼저 배포 지점에서 Configuration Manager 클라이언트 캐시로 이미지와 해당 콘텐츠를 다운로드한 다음 설치합니다.  

-   배포 지점에서 바로 이미지와 해당 콘텐츠를 설치합니다.  

-   배포 지점에서 필요에 따라 이미지와 해당 콘텐츠를 설치합니다.  

 기본적으로 작업 순서에 대한 배포를 만들면 먼저 이미지가 Configuration Manager 클라이언트 캐시로 다운로드된 다음 설치됩니다. 이미지를 실행하기 전에 Configuration Manager 클라이언트 캐시로 이미지를 다운로드하도록 선택한 경우 작업 순서에 하드 드라이브를 다시 분할하는 단계가 포함되어 있으면 하드 드라이브 다시 분할 과정에서 Configuration Manager 클라이언트 캐시의 콘텐츠가 지워지므로 다시 분할 단계가 실패합니다. 작업 순서가 하드 드라이브를 다시 분할해야 하는 경우 작업 순서를 배포할 때 **배포 지점에서 프로그램 실행**  옵션을 사용하여 배포 지점에서 이미지 설치를 실행해야 합니다.  

 자세한 내용은 [Deploy a task sequence](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)항목을 참조하세요.  
