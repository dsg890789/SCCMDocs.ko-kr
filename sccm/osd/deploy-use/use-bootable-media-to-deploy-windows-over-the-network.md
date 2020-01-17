---
title: 부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포
titleSuffix: Configuration Manager
description: Configuration Manager에서 부팅 가능한 미디어 배포를 사용하면 대상 컴퓨터가 시작될 때 운영 체제를 배포할 수 있습니다.
ms.date: 06/16/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 22a3219cdf0bb09061e57f34e52ca7a061f55a2f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75806155"
---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-configuration-manager"></a>Configuration Manager에서 부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포

*적용 대상: Configuration Manager(현재 분기)*

대상 컴퓨터가 부팅 가능한 미디어 배포를 사용하여 시작될 경우 운영 체제를 배포할 수 있습니다. 미디어에는 작업 순서에 대한 포인터, 운영 체제 이미지 및 네트워크의 기타 필수 콘텐츠가 포함됩니다. 대상 컴퓨터는 시작될 때 포인터에서 참조된 항목을 검색합니다. 부팅 가능한 미디어에 콘텐츠가 없으면 미디어에서 대상을 바꾸지 않고도 업데이트할 수 있습니다.

다음 운영 체제 배포 시나리오에서 멀티캐스트를 사용하여 네트워크를 통해 운영 체제를 배포할 수 있습니다.

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

-   [기존 컴퓨터 바꾸기 및 설정 전송](replace-an-existing-computer-and-transfer-settings.md)  

운영 체제 배포 시나리오 중 하나의 단계를 완료하고 다음 섹션을 사용하여 부팅 가능한 미디어로 운영 체제를 배포합니다.  

## <a name="configure-deployment-settings"></a>배포 설정 구성  
부팅 가능한 미디어를 사용하여 운영 체제 배포 프로세스를 시작할 경우 해당 운영 체제를 미디어에서 사용할 수 있도록 배포를 구성합니다. 소프트웨어 배포 마법사의 **배포 설정** 페이지 또는 배포에 대한 속성의 **배포 설정** 탭에서 이 옵션을 설정할 수 있습니다. **다음에 사용 가능하도록 설정** 설정에 대해 다음 중 하나를 구성합니다.

-   Configuration Manager 클라이언트, 미디어 및 PXE

-   미디어 및 PXE만

-   미디어 및 PXE만(숨김)

## <a name="create-the-bootable-media"></a>부팅 가능한 미디어 만들기
부팅 가능한 미디어가 USB 플래시 드라이브인지 아니면 CD/DVD 세트인지를 지정할 수 있습니다. 미디어를 시작하는 컴퓨터는 부팅 가능한 드라이브로 선택하는 옵션을 지원해야 합니다. 자세한 내용은 [부팅 가능한 미디어 만들기](create-bootable-media.md)를 참조하세요.  

##  <a name="BKMK_Deploy"></a> 부팅 가능한 미디어에서 운영 체제 설치  
컴퓨터에서 부팅 가능한 드라이브에 부팅 가능한 미디어를 삽입한 다음 전원을 켜서 운영 체제를 설치합니다.
