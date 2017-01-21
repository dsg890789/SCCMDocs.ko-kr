---
title: "멀티캐스트를 사용하여 네트워크를 통해 Windows 배포 | Configuration Manager"
description: "여러 컴퓨터에서 운영 체제 이미지를 동시에 다운로드할 수 있도록 System Center Configuration Manager 환경에서 멀티캐스트를 사용합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: da83037a28194e3bae1e6afe4d4bca1ce43f2bf6


---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 멀티캐스트를 사용하여 네트워크를 통해 Windows 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

멀티캐스트는 여러 클라이언트가 동시에 같은 운영 체제 이미지를 다운로드할 수도 있는 System Center Configuration Manager 환경에서 사용할 수 있는 네트워크 최적화 방법입니다. 멀티캐스트를 사용할 경우 여러 컴퓨터는 배포 지점에서 멀티캐스트되는 운영 체제 이미지를 동시에 다운로드하며 배포 지점은 개별 연결을 통해 데이터 복사본을 각 클라이언트에 전송하지 않습니다.  

 다음 운영 체제 배포 시나리오에서 멀티캐스트를 사용하여 네트워크를 통해 운영 체제를 배포할 수 있습니다.  

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

 운영 체제 배포 시나리오 중 하나의 단계를 완료한 후 다음 섹션을 참조하여 멀티미디어를 지원합니다.  

##  <a name="a-namebkmkconfigurea-configure-a-distribution-point-to-support-multicast"></a><a name="BKMK_Configure"></a> 멀티캐스트를 지원하기 위한 배포 지점 구성  
 운영 체제를 배포할 때 멀티캐스트를 사용하려면 멀티캐스트를 지원하도록 배포 지점을 구성해야 합니다. 자세한 내용은 [멀티캐스트를 지원하도록 배포 지점 구성](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)을 참조하세요.  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>멀티캐스트 배포를 위한 운영 체제 이미지 준비  
 멀티캐스트를 지원하도록 운영 체제 이미지 패키지를 구성하려면 [멀티캐스트 배포를 위한 운영 체제 이미지 준비](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast)를 참조하세요.  

##  <a name="a-namebkmkdeploya-deploy-the-task-sequence"></a><a name="BKMK_Deploy"></a> 작업 순서 배포  
 대상 컬렉션에 운영 체제 배포 자세한 내용은 [Deploy a task sequence](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)항목을 참조하세요.  



<!--HONumber=Nov16_HO1-->


