---
title: Windows 10 빠른 업데이트 관리
titleSuffix: Configuration Manager
description: Configuration Manager는 클라이언트에서 다운로드 크기를 줄이고 설치 시간을 단축하는 Windows 10용 빠른 설치 파일을 지원합니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 11/02/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.openlocfilehash: e7daf0de68fcbcd9e05debe67418b99d3974290c
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75818777"
---
# <a name="manage-express-installation-files-for-windows-10-updates"></a>Windows 10 업데이트용 빠른 설치 파일 관리

Configuration Manager는 Windows 10 업데이트용 빠른 설치 파일을 지원합니다. 현재 달의 Windows 10 누적 품질 업데이트와 이전 달의 업데이트 간 변경 사항만 다운로드하도록 클라이언트를 구성합니다. 빠른 설치 파일이 없으면 Configuration Manager 클라이언트는 이전 달의 모든 업데이트를 포함하여 전체 Windows 10 누적 업데이트를 매달 다운로드합니다. 빠른 설치 파일을 사용하면 다운로드 크기가 감소하고 클라이언트에서 설치 시간이 단축됩니다.

Configuration Manager로 업데이트 콘텐츠를 관리하여 Windows 10으로 최신 상태를 유지하는 방법을 알아보려면 [Windows 10 업데이트 배달 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)를 참조하세요.  


> [!IMPORTANT]  
> OS 클라이언트 지원은 Windows 10 버전 1607에서 Windows 업데이트 에이전트의 업데이트로 사용할 수 있습니다. 이 업데이트는 2017년 4월 11일 릴리스된 업데이트에 포함되어 있습니다. 이러한 업데이트에 대한 자세한 내용은 [지원 문서 4015217](https://support.microsoft.com/kb/4015217)을 참조하세요. 이후 업데이트에서는 다운로드 크기를 줄이기 위한 빠른 설치 파일을 사용합니다. Windows 10 이전 버전과 이 업데이트가 설치되지 않은 Windows 10 버전 1607에서는 빠른 설치 파일이 지원되지 않습니다.  


## <a name="enable-the-site-to-download-express-installation-files-for-windows-10-updates"></a>사이트에서 Windows 10 업데이트용 빠른 설치 파일을 다운로드하도록 설정
Windows 10 빠른 설치 파일에 대한 메타데이터 동기화를 시작하려면 소프트웨어 업데이트 지점의 속성에서 사용하도록 설정합니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 중앙 관리 사이트나 독립 실행형 기본 사이트를 선택합니다.  

3. 리본에서 **사이트 구성 요소 구성**을 클릭한 다음, **소프트웨어 업데이트 지점**을 클릭합니다. **업데이트 파일** 탭으로 전환하고 **승인된 모든 업데이트에 대한 전체 파일 및 Windows 10용 빠른 설치 파일 다운로드**를 선택합니다.

> [!NOTE]    
> 빠른 업데이트‘만’ 다운로드하도록 소프트웨어 업데이트 지점 구성 요소를 구성할 수는 없습니다.   사이트는 전체 파일 외에도 빠른 설치 파일을 다운로드합니다. 그러면 콘텐츠 라이브러리에 저장되는 콘텐츠의 양이 증가하고 배포 지점에 배포 및 저장됩니다.

> [!Tip]  
> 디스크에서 파일에 의해 사용되는 실제 공간을 확인하려면 파일의 **디스크 크기** 속성을 확인합니다. 디스크 크기 속성은 크기 값보다 훨씬 더 작아야 합니다. 자세한 내용은 [Windows 10 업데이트 배달 최적화 FAQ](/sccm/sum/deploy-use/optimize-windows-10-update-delivery#bkmk_faq)를 참조하세요.  


## <a name="enable-clients-to-download-and-install-express-installation-files"></a>클라이언트에서 빠른 설치 파일을 다운로드 및 설치할 수 있도록 설정
클라이언트에서 빠른 설치 파일 지원을 사용하려면 클라이언트 설정의 **소프트웨어 업데이트** 그룹에서 빠른 설치 파일을 사용하도록 설정합니다. 이렇게 설정하면 지정한 포트에서 빠른 설치 파일을 다운로드하는 요청을 수신 대기하는 새 HTTP 수신기가 생성됩니다.

> [!NOTE]    
> 클라이언트가 배달 최적화 또는 BITS(Background Intelligent Transfer Service)에서 배포 지점의 빠른 콘텐츠를 다운로드하라는 요청을 수신하는 데 사용하는 로컬 포트입니다. 모든 트래픽이 로컬 컴퓨터에 있으므로 이 포트를 방화벽에서 열지 않아도 됩니다.  

클라이언트에서 이 기능을 사용하도록 설정하는 클라이언트 설정을 배포하면 현재 달의 Windows 10 누적 업데이트와 이전 달의 업데이트 간 델타를 다운로드하려고 시도합니다. 클라이언트는 빠른 설치 파일을 지원하는 Windows 10 버전을 실행해야 합니다.  

1. 소프트웨어 업데이트 지점 구성 요소의 속성에서 빠른 설치 파일 지원을 사용하도록 설정합니다(이전 절차).  

2. Configuration Manager 콘솔에서 **관리** 작업 공간으로 이동하여 **클라이언트 설정**을 선택합니다.  

3. 적절한 클라이언트 설정을 선택하고 리본에서 **속성**을 클릭합니다.  

4. **소프트웨어 업데이트** 그룹을 선택합니다. **클라이언트에서 Express 업데이트 설치 사용** 설정을 **예**로 구성합니다. **Express 업데이트 콘텐츠를 다운로드하는 데 사용할 포트**를 클라이언트의 HTTP 수신기에서 사용되는 포트로 구성합니다.
    - 버전 1902에서 **Express 업데이트에 대 한 콘텐츠를 다운로드 하는 데 사용 되는 포트가** **클라이언트가 델타 콘텐츠에 대 한 요청을 수신 하는 데 사용 하는 포트로**변경 되었습니다.

## <a name="next-steps"></a>다음 단계

[소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)