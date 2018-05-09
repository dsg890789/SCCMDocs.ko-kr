---
title: 팩터리 또는 로컬 저장소에 OEM에 대한 이미지 만들기
titleSuffix: Configuration Manager
description: 사전 준비된 미디어 배포를 사용하면 완전히 프로비전되지 않은 컴퓨터에 운영 체제를 배포하는 동안 네트워크 트래픽을 줄일 수 있습니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: a7d3df90-062d-4d57-9e9d-e137d3e7cd7f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0c8cf0af19017f4acfd95bcd01f8226229c05a14
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="create-an-image-for-an-oem-in-factory-or-a-local-depot-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 팩터리 또는 로컬 저장소에 OEM에 대한 이미지 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 사전 준비된 미디어 배포를 사용하면 완전히 프로비전되지 않은 컴퓨터에 운영 체제를 배포할 수 있습니다. 사전 준비된 미디어는 제조업체(OEM)가 운영 체제 미설치 컴퓨터에 설치하거나, Configuration Manager 환경에 연결되지 않은 엔터프라이즈 준비 센터에 설치할 수 있는 WIM(Windows Imaging Format) 파일입니다. Configuration Manager 환경에서 이후에 미디어에서 제공된 부팅 이미지를 사용하여 컴퓨터가 시작되고, 사전 준비된 미디어가 올바른지 해시 확인이 실행된 다음, 컴퓨터가 사이트 관리 지점에 연결되어 사용 가능한 작업 순서를 통해 다운로드 프로세스를 완료하게 됩니다.


이 배포 방법에서는 부팅 이미지와 운영 체제 이미지가 이미 대상 컴퓨터에 있으므로 네트워크 트래픽을 줄일 수 있습니다. 사전 준비된 미디어에 포함할 응용 프로그램, 패키지 및 드라이버 패키지를 지정할 수 있습니다. 운영 체제가 컴퓨터에 설치된 후 응용 프로그램, 패키지 및 드라이버 패키지에 대한 로컬 작업 순서 캐시를 먼저 확인하고 콘텐츠를 찾을 수 없거나 콘텐츠가 수정된 경우 사전 준비된 미디어에 구성된 배포 지점에서 콘텐츠를 다운로드한 다음 설치합니다.  

 다음 운영 체제 배포 시나리오에 대해 사전 준비된 미디어를 사용할 수 있습니다.  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

-   [기존 컴퓨터 바꾸기 및 설정 전송](replace-an-existing-computer-and-transfer-settings.md)  

 운영 체제 배포 시나리오 중 하나의 단계를 완료한 후 다음 섹션을 사용하여 사전 준비된 미디어를 준비하고 만듭니다.  

## <a name="configure-deployment-settings"></a>배포 설정 구성  
 사전 준비된 미디어를 사용하여 운영 체제 배포 프로세스를 시작할 경우 해당 운영 체제를 미디어에서 사용할 수 있도록 배포를 구성해야 합니다. 소프트웨어 배포 마법사의 **배포 설정** 페이지 또는 배포에 대한 속성의 **배포 설정** 탭에서 이를 구성할 수 있습니다.  **다음에 사용 가능하도록 설정** 설정에 대해 다음 중 하나를 구성합니다.  

-   **Configuration Manager 클라이언트, 미디어 및 PXE**  

-   **미디어 및 PXE만**  

-   **미디어 및 PXE만(숨김)**  

## <a name="create-the-prestaged-media"></a>사전 준비된 미디어 만들기  
 OEM 또는 로컬 저장소로 보낼 사전 준비된 미디어 파일을 만듭니다. 자세한 내용은 [System Center Configuration Manager에서 사전 준비된 미디어 만들기](create-prestaged-media.md)를 참조하세요.  

## <a name="send-the-prestaged-media-file-to-the-oem-or-local-depot"></a>사전 준비된 미디어 파일을 OEM 또는 로컬 저장소로 보냅니다.  
 OEM 또는 로컬 저장소로 미디어를 보내 컴퓨터를 사전 준비합니다. 사전 준비된 미디어 파일은 컴퓨터의 포맷된 하드 디스크에 적용됩니다.  

## <a name="start-the-computer-to-install-the-operating-system"></a>컴퓨터를 시작하여 운영 체제 설치  
 사전 준비된 미디어 파일은 컴퓨터에 적용됩니다. 컴퓨터를 처음 시작하면 운영 체제 설치 프로세스가 시작됩니다.  
