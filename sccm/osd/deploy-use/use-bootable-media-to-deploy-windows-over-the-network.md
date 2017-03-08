---
title: "부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포 | Microsoft 문서"
description: "System Center Configuration Manager에서 부팅 가능한 미디어 배포를 사용하면 대상 컴퓨터가 시작될 때 운영 체제를 배포할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: beb730efbe4d9bae7c4c97f4e587c8919bd79049
ms.lasthandoff: 12/16/2016


---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 부팅 가능한 미디어 배포를 사용하면 대상 컴퓨터가 시작될 때 운영 체제를 배포할 수 있습니다. 대상 컴퓨터는 시작될 때 작업 순서, 운영 체제 이미지 및 기타 필요한 콘텐츠를 네트워크에서 검색합니다. 해당 콘텐츠는 미디어에 포함되어 있지 않기 때문에 미디어를 다시 만들지 않고도 콘텐츠를 업데이트할 수 있습니다.  

 다음 운영 체제 배포 시나리오에서 멀티캐스트를 사용하여 네트워크를 통해 운영 체제를 배포할 수 있습니다.  

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

-   [기존 컴퓨터 바꾸기 및 설정 전송](replace-an-existing-computer-and-transfer-settings.md)  

 운영 체제 배포 시나리오 중 하나의 단계를 완료하고 다음 섹션을 사용하여 부팅 가능한 미디어로 운영 체제를 배포합니다.  

## <a name="configure-deployment-settings"></a>배포 설정 구성  
 부팅 가능한 미디어를 사용하여 운영 체제 배포 프로세스를 시작할 경우 해당 운영 체제를 미디어에서 사용할 수 있도록 배포를 구성해야 합니다. 소프트웨어 배포 마법사의 **배포 설정** 페이지 또는 배포에 대한 속성의 **배포 설정** 탭에서 이를 구성할 수 있습니다.  **다음에 사용 가능하도록 설정** 설정에 대해 다음 중 하나를 구성합니다.  

-   **Configuration Manager 클라이언트, 미디어 및 PXE**  

-   **미디어 및 PXE만**  

-   **미디어 및 PXE만(숨김)**  

## <a name="create-the-bootable-media"></a>부팅 가능한 미디어 만들기  
 부팅 가능한 미디어가 USB 플래시 드라이브인지 아니면 CD/DVD 세트인지를 지정할 수 있습니다. 미디어를 시작하는 컴퓨터는 부팅 가능한 드라이브로 선택하는 옵션을 지원해야 합니다. 자세한 내용은 [부팅 가능한 미디어 만들기](create-bootable-media.md)를 참조하세요.  

##  <a name="BKMK_Deploy"></a> 부팅 가능한 미디어에서 운영 체제 설치  
 컴퓨터에서 부팅 가능한 드라이브에 부팅 가능한 미디어를 삽입한 다음 전원을 켜서 운영 체제를 설치합니다.  

