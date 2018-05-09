---
title: 콘텐츠 라이브러리
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 배포된 콘텐츠의 전체 크기를 줄이는 데 사용하는 콘텐츠 라이브러리에 대해 알아봅니다.
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: df34c2c8ecb0f906657d1bbc2e49c87a5ff93e15
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="the-content-library-in-system-center-configuration-manager"></a>System Center Configuration Manager의 콘텐츠 라이브러리

*적용 대상: System Center Configuration Manager(현재 분기)*

콘텐츠 라이브러리는 배포하는 콘텐츠의 결합된 본문 전체 크기를 줄이기 위해 System Center Configuration Manager에서 사용하는 콘텐츠의 단일 인스턴스 저장소입니다. 콘텐츠 라이브러리에는 소프트웨어 업데이트, 응용 프로그램, 운영 체제 배포 등을 위한 모든 콘텐츠 파일이 저장됩니다.

 - 콘텐츠 라이브러리의 복사본은 각 **사이트 서버** 및 각 **배포 지점**에서 자동으로 작성 및 유지 관리됩니다.

 - Configuration Manager에서 콘텐츠 파일을 사이트 서버에 다운로드하거나 파일을 배포 지점에 복사하기 전에 Configuration Manager는 각 콘텐츠 파일이 콘텐츠 라이브러리에 이미 있는지 여부를 확인합니다.
 - 콘텐츠 파일을 사용할 수 있는 경우 Configuration Manager에서는 파일을 복사하지 않고 기존 콘텐츠 파일을 응용 프로그램 또는 패키지와 연결합니다.

배포 지점을 설치한 컴퓨터에서 다음을 구성할 수 있습니다.

- 콘텐츠 라이브러리를 만들려는 하나 이상의 디스크 드라이브
- 사용 중인 각 드라이브에 대한 우선 순위

Configuration Manager에서는 콘텐츠 파일을 복사할 때 드라이브에 포함된 공간이 지정된 최소 사용 가능 공간보다 적어질 때까지 우선 순위가 가장 높은 드라이브에 콘텐츠 파일을 복사합니다.
- 배포 지점을 설치하는 동안 드라이브 설정을 구성할 수 있습니다.
- 설치가 완료된 후에는 배포 지점 속성에서 드라이브 설정을 구성할 수 없습니다.


배포 지점에 대한 드라이브 설정을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  


>  [!IMPORTANT]  
>  설치 후에 배포 지점에서 다른 위치로 콘텐츠 라이브러리를 이동하려면 System Center 2012 R2 Configuration Manager Toolkit에 포함된 **콘텐츠 라이브러리 전송 도구**를 사용합니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=279566)에서 이 도구 키트를 다운로드할 수 있습니다.  

## <a name="about-the-content-library-on-the-central-administration-site"></a>중앙 관리 사이트의 콘텐츠 라이브러리 정보  
 기본적으로 Configuration Manager에서는 중앙 관리 사이트가 설치될 때 이 사이트에 콘텐츠 라이브러리를 만듭니다. 콘텐츠 라이브러리는 사용 가능한 디스크 공간이 가장 많은 사이트 서버 드라이브에 배치됩니다. 중앙 관리 사이트에는 배포 지점을 설치할 수 없기 때문에 콘텐츠 라이브러리에 사용하기 위한 드라이브의 우선 순위를 지정할 수 없습니다. 다른 사이트 서버 및 배포 지점의 콘텐츠 라이브러리와 마찬가지로, 콘텐츠 라이브러리가 포함된 드라이브에 사용 가능한 디스크 공간이 부족해지면 콘텐츠 라이브러리가 자동으로 사용 가능한 다음 드라이브에 저장됩니다.  

 Configuration Manager는 다음 경우에 중앙 관리 사이트에서 콘텐츠 라이브러리를 사용합니다.  

-   중앙 관리 사이트에 콘텐츠를 만드는 경우  

-   다른 Configuration Manager 사이트에서 콘텐츠를 마이그레이션하고 중앙 관리 사이트를 해당 콘텐츠를 관리하는 사이트로 할당하는 경우  

> [!NOTE]  
>  기본 사이트에서 콘텐츠를 만든 다음 이를 다른 기본 사이트나 다른 기본 사이트의 보조 사이트에 배포할 경우 중앙 관리 사이트가 일시적으로 해당 콘텐츠를 중앙 관리 사이트의 스케줄러 수신함에 저장하지만 콘텐츠 라이브러리에 콘텐츠를 추가하지는 않습니다.  

 중앙 관리 사이트에서 콘텐츠 라이브러리를 관리하려면 다음 옵션을 사용합니다.  

-   콘텐츠 라이브러리가 특정 드라이브에 설치되지 않도록 하려면 콘텐츠 라이브러리를 만들기 전에 **no_sms_on_drive.sms**라는 빈 파일을 만든 다음 이를 드라이브의 루트 폴더로 복사합니다.  

-   콘텐츠 라이브러리가 만들어진 후에는 System Center 2012 R2 Configuration Manager Toolkit의 **콘텐츠 라이브러리 전송 도구**를 사용하여 콘텐츠 라이브러리의 위치를 관리합니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=279566)에서 이 도구 키트를 다운로드할 수 있습니다.  
