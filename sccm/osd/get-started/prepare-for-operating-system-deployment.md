---
title: OS 배포를 위한 준비
titleSuffix: Configuration Manager
description: Configuration Manager에서 운영 체제 배포를 준비하는 방법 알아보기
ms.date: 02/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 8d27e5ac-4f19-4b3d-85c7-fa34eb5d5e7e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e303a7363e0641210cc7c6e436546d864fe0571
ms.sourcegitcommit: ef2960bd91655c741450774e512dd0a9be610625
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56838721"
---
# <a name="prepare-for-os-deployment-in-configuration-manager"></a>Configuration Manager에서 OS 배포 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

운영 체제를 배포하기 전에 Configuration Manager에서 수행해야 하는 몇 가지 작업이 있습니다. OS 배포를 준비하려면 다음 문서를 사용합니다.  

-   [부팅 이미지 관리](manage-boot-images.md)  

-   [OS 이미지 관리](manage-operating-system-images.md)  

-   [OS 업그레이드 패키지 관리](manage-operating-system-upgrade-packages.md)  

-   [드라이버 관리](manage-drivers.md)  

-   [사용자 상태 관리](manage-user-state.md)  

-   [알 수 없는 컴퓨터 배포 준비](prepare-for-unknown-computer-deployments.md)  

-   [사용자를 대상 컴퓨터에 연결](associate-users-with-a-destination-computer.md)  



### <a name="os-image-size"></a>OS 이미지 크기  

OS 이미지는 크기가 큽니다. 예를 들어 Windows 7의 이미지 크기는 3GB 이상입니다. 이미지 크기와 OS를 동시에 배포하는 컴퓨터 수는 네트워크 성능 및 사용 가능한 대역폭에 영향을 줍니다. 네트워크 성능을 테스트해야 합니다. 영향을 테스트하여 이미지 배포로 인한 영향 및 배포를 완료하는 데 걸리는 시간을 더 정확하게 측정하세요. 네트워크 성능에 영향을 주는 Configuration Manager 작업으로는 배포 지점에 이미지 배포, 사이트 간 이미지 배포, 클라이언트로 이미지 다운로드 등이 있습니다.  

또한, OS 이미지를 호스트하는 배포 지점에 충분한 디스크 스토리지 공간을 계획해야 합니다.  

자세한 내용은 [배포 지점을 계획할 때 추가로 고려할 사항](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_AdditionalPlanning)을 참조하세요.


### <a name="client-cache-size"></a>클라이언트 캐시 크기  

BITS(Background Intelligent Transfer Service)를 사용할 수 있는 경우 구성 관리자 클라이언트에서 콘텐츠를 다운로드할 때 자동으로 BITS를 사용합니다. OS를 설치하는 작업 순서를 배포할 때 구성 관리자 클라이언트에서 작업 순서를 실행하기 전에 전체 이미지를 로컬 캐시에 다운로드하도록 배포에 대한 옵션을 설정할 수 있습니다.  

구성 관리자 클라이언트가 OS 이미지를 다운로드해야 하지만 캐시에 충분한 공간이 없는 경우 클라이언트가 해당 캐시에서 공간을 비울 수 있습니다. 캐시의 다른 패키지를 확인하여 가장 오래된 패키지를 삭제하면 이미지를 포함할 충분한 디스크 공간이 확보되는지 판단합니다. 패키지를 삭제해도 충분한 공간이 확보되지 않으면 클라이언트에서 이미지를 다운로드하지 않으며 배포에 실패합니다. 이러한 동작은 캐시에 보관하도록 구성한 대용량 패키지가 캐시에 있는 경우 발생할 수 있습니다. 패키지를 삭제할 경우 캐시의 디스크 공간이 충분히 확보되면 클라이언트에서 패키지를 삭제한 다음 이미지를 캐시에 다운로드합니다.  

구성 관리자 클라이언트의 기본 캐시 크기가 대부분의 OS 이미지 배포에 충분하지 않을 수 있습니다. 클라이언트 캐시에 전체 이미지를 다운로드하려면 배포할 이미지 크기를 포함할 수 있도록 대상 컴퓨터의 클라이언트 캐시 크기를 조정합니다.  

자세한 내용은 [클라이언트 캐시 구성](/sccm/core/clients/manage/manage-clients#BKMK_ClientCache)을 참조하세요.  


