---
title: "사용자를 대상 컴퓨터에 연결"
titleSuffix: Configuration Manager
description: "운영 체제를 배포할 때 System Center Configuration Manager를 구성하여 사용자와 대상 컴퓨터를 연결합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07c3c6d9-f056-4c4d-bc70-ede5ca933807
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 4c0231057c2ac154b050cc7020eb1fbb4ed93228
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="associate-users-with-a-destination-computer-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 대상 컴퓨터에 사용자 연결

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 사용하여 운영 체제를 배포할 때 운영 체제가 배포된 대상 컴퓨터에 사용자를 연결할 수 있습니다. 이 구성에는 다음 설정이 포함됩니다.  

-   단일 사용자를 대상 컴퓨터의 기본 사용자로 지정합니다.  

-   여러 사용자를 대상 컴퓨터의 기본 사용자로 지정합니다.  

 사용자 장치 선호도는 응용 프로그램을 배포할 때 사용자 중심 관리를 지원합니다. 운영 체제를 설치할 대상 컴퓨터에 사용자를 연결하면 나중에 응용 프로그램을 해당 사용자에게 배포할 수 있으며 응용 프로그램이 대상 컴퓨터에 자동으로 설치됩니다. 그러나 운영 체제를 배포할 때 사용자 장치 선호도에 대한 지원을 구성할 수는 있지만 사용자 장치 선호도를 사용하여 운영 체제를 배포할 수는 없습니다.  

 사용자 장치 선호도에 대한 자세한 내용은 [사용자 장치 선호도를 사용하여 사용자와 장치 연결](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)을 참조하세요.  

## <a name="how-to-specify-a-user-when-you-deploy-operating-systems"></a>운영 체제를 배포할 때 사용자를 지정하는 방법  
 다음 표에는 운영 체제 배포에 사용자 장치 선호도를 통합하기 위해 수행할 수 있는 작업이 나와 있습니다. 사용자 장치 선호도를 PXE 배포, 부팅 가능한 미디어 배포 및 사전 준비된 미디어 배포에 통합할 수 있습니다.  

|작업|추가 정보|  
|------------|----------------------|  
|**SMSTSAssignUsersMode** 변수를 포함하는 작업 순서 만들기|[작업 순서 변수 설정](../../osd/understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable) 작업 순서 단계를 사용하여 작업 순서의 시작 부분에 **SMSTSAssignUsersMode** 변수를 추가합니다. 이 변수는 작업 순서에서 사용자 정보를 처리하는 방법을 지정합니다.<br /><br /> 변수를 다음 값 중 하나로 설정합니다.<br /><br /> <br /><br /> **자동**: 작업 순서에서 자동으로 사용자와 대상 컴퓨터 간의 관계를 만들고 운영 체제를 배포합니다.<br /><br /> **보류 중**: 작업 순서에서 사용자와 대상 컴퓨터 간의 관계를 만들지만 운영 체제를 배포하기 전에 관리자의 승인을 기다립니다.<br /><br /> **사용 안 함**: 작업 순서에서 자동으로 사용자와 대상 컴퓨터를 연결하지 않고 운영 체제 배포를 계속합니다.<br /><br /> <br /><br /> 이 변수는 컴퓨터 또는 컬렉션에 대해서도 설정할 수 있습니다. 기본 제공 변수에 대한 자세한 내용은 [작업 순서 기본 제공 변수](../../osd/understand/task-sequence-built-in-variables.md)를 참조하세요.|  
|사용자 정보를 수집하는 시작 전 명령 만들기|시작 전 명령은 입력란이 있는 VB(Visual Basic) 스크립트일 수도 있고 입력된 사용자 데이터의 유효성을 검사하는 HTA(HTML Application)일 수도 있습니다.<br /><br /> 시작 전 명령은 작업 순서를 실행할 때 사용되는 **SMSTSUdaUsers** 변수를 설정해야 합니다. 이 변수는 컴퓨터, 컬렉션 또는 작업 순서 변수에 대해 설정할 수 있습니다. 여러 사용자를 추가할 때는 *도메인\사용자1, 도메인\사용자2, 도메인\사용자3*형식을 사용합니다.|  
|배포 지점 및 미디어에서 사용자와 대상 컴퓨터를 연결하는 방법 구성|[PXE 부팅 요청을 수락하도록 배포 지점을 구성](https://technet.microsoft.com/library/mt627944\(TechNet.10\).aspx#BKMK_PXEDistributionPoint) 하는 경우 및 작업 순서 미디어 만들기 마법사를 사용하여 [부팅 가능한 미디어](http://technet.microsoft.com/library/mt627921\(TechNet.10\).aspx) 또는 [사전 준비된 미디어](https://technet.microsoft.com/library/mt627922\(TechNet.10\).aspx) 를 만드는 경우, 배포 지점이나 미디어에서 운영 체제가 배포되는 대상 컴퓨터에 사용자를 연결하도록 지원하는 방법을 지정할 수 있습니다.<br /><br /> 사용자 장치 선호도 지원을 구성할 때 사용자 ID의 유효성을 검사하는 기본 제공 방법이 없습니다. 이는 컴퓨터를 프로비전하는 기술 전문가가 사용자 대신 정보를 입력할 때 중요할 수 있습니다. 작업 순서에서 사용자 정보를 처리하는 방법을 설정하고 배포 지점 및 미디어에 대한 이러한 옵션을 구성하면 PXE 부팅이나 특정 미디어 유형에서 시작되는 배포를 제한할 수 있습니다.|  
