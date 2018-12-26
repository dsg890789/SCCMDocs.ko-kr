---
title: 사용자와 컴퓨터 연결
titleSuffix: Configuration Manager
description: 운영 체제를 배포할 때 Configuration Manager를 구성하여 사용자와 대상 컴퓨터를 연결합니다.
ms.date: 08/17/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 07c3c6d9-f056-4c4d-bc70-ede5ca933807
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 325b571adbcb2750eaa0b3a856dda753c43634f0
ms.sourcegitcommit: be8c0182db9ef55a948269fcbad7c0f34fd871eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755903"
---
# <a name="associate-users-with-a-destination-computer-in-configuration-manager"></a>Configuration Manager에서 대상 컴퓨터에 사용자 연결

*적용 대상: System Center Configuration Manager(현재 분기)*

 Configuration Manager를 사용하여 운영 체제를 배포할 때 대상 컴퓨터에 사용자를 연결할 수 있습니다. 이 옵션은 대상 컴퓨터의 기본 사용자가 한 명이든 여러 명이든 상관없이 작동합니다.  

 사용자 디바이스 선호도는 응용 프로그램을 배포할 때 사용자 중심 관리를 지원합니다. OS를 설치할 대상 컴퓨터에 사용자를 연결하면 나중에 애플리케이션을 해당 사용자에게 배포할 수 있으며 애플리케이션이 대상 컴퓨터에 자동으로 설치됩니다. 운영 체제를 배포할 때 사용자 디바이스 선호도에 대한 지원을 구성할 수는 있지만 사용자 디바이스 선호도를 사용하여 OS를 배포할 수는 없습니다.  

 사용자 디바이스 선호도에 대한 자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.  

 여러 가지 방법으로 OS 배포에 사용자 디바이스 선호도를 통합할 수 있습니다. 사용자 디바이스 선호도를 PXE 배포, 부팅 가능한 미디어 배포 및 사전 준비된 미디어 배포에 통합할 수 있습니다.  


### <a name="create-a-task-sequence-that-includes-the-smstsassignusersmode-variable"></a>**SMSTSAssignUsersMode** 변수를 포함하는 작업 순서 만들기

 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) 단계를 사용하여 작업 순서의 시작 부분에 **SMSTSAssignUsersMode** 변수를 추가합니다. 이 변수는 작업 순서에서 사용자 정보를 처리하는 방법을 지정합니다.

 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSAssignUsersMode)\(작업 순서 변수\)를 참조하세요.


### <a name="create-a-prestart-command-that-gathers-the-user-information"></a>사용자 정보를 수집하는 시작 전 명령 만들기

 시작 전 명령은 입력란이 있는 VBScript일 수도 있고 입력된 사용자 데이터의 유효성을 검사하는 HTA(HTML 애플리케이션)일 수도 있습니다. 

 시작 전 명령은 작업 순서를 실행할 때 사용되는 **SMSTSUDAUsers** 변수를 설정해야 합니다. 이 변수는 컴퓨터, 컬렉션 또는 작업 순서 변수에 대해 설정할 수 있습니다.

 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSUDAUsers)\(작업 순서 변수\)를 참조하세요.


### <a name="configure-how-distribution-points-and-media-associate-the-user-with-the-destination-computer"></a>배포 지점 및 미디어에서 사용자와 대상 컴퓨터를 연결하는 방법 구성

 배포 지점이나 미디어는 OS가 배포되는 대상 컴퓨터와 사용자의 연결을 지원합니다. 다음 방법 중 하나를 사용합니다. 

 - [PXE 부팅 요청을 수락하도록 배포 지점 구성](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_PXEDistributionPoint)  
 - [부팅 가능한 미디어 만들기](/sccm/osd/deploy-use/create-bootable-media)  
 - [미리 준비된 미디어 만들기](/sccm/osd/deploy-use/create-prestaged-media)  


 사용자 디바이스 선호도 지원을 구성할 때 사용자 ID의 유효성을 검사하는 기본 제공 방법이 없습니다. 이것은 기술 전문가가 컴퓨터를 프로비전하고 사용자 대신 정보를 입력할 때 중요합니다. 작업 순서에서 사용자 정보를 처리하는 방법을 설정하고 배포 지점 및 미디어에 대한 이러한 옵션을 구성하면 PXE 부팅이나 특정 미디어 유형에서 시작되는 배포를 제한할 수 있습니다.
