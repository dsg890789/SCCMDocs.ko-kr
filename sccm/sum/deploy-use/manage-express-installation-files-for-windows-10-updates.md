---
title: "Windows 10 업데이트에 대한 빠른 설치 파일 관리 | Microsoft 문서"
description: "Configuration Manager는 클라이언트에서 다운로드 크기를 줄이고 설치 시간을 단축하는 Windows 10용 빠른 설치 파일을 지원합니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 459ad5a428102b5e040bec2eaf2a70fc89789dff
ms.lasthandoff: 03/27/2017

---

## <a name="manage-express-installation-files-for-windows-10-updates"></a>Windows 10 업데이트에 대한 빠른 설치 파일 관리
Configuration Manager 버전 1702부터 Configuration Manager는 Windows 10 업데이트에 대한 빠른 설치 파일을 지원합니다. 지원되는 버전의 Windows 10을 사용하는 경우 Configuration Manager 설정을 사용하여 현재 월의 Windows 10 누적 업데이트와 이전 월의 업데이트 간 변경 내용만 다운로드할 수 있습니다. 빠른 설치 파일이 없으면 Configuration Manager는 전체 Windows 10 누적 업데이트(이전 몇 개월의 모든 업데이트 포함)를 매달 다운로드합니다. 빠른 설치 파일을 사용하면 다운로드 크기가 감소하고 클라이언트에서 설치 시간이 단축됩니다.

> [!IMPORTANT]
> Configuration Manager 버전 1702에서 빠른 설치 파일의 사용을 지원하는 설정을 사용할 수 있지만 운영 체제 클라이언트 지원은 Windows 업데이트 에이전트의 업데이트가 설치된 Windows 10 버전 1607에서 사용할 수 있습니다. 이 업데이트는 2017년 4월 11일 릴리스되는 업데이트(화요일 패치)에 포함됩니다. <!--For more information about these updates, see [support article 4015217](http://support.microsoft.com/kb/4015217).--> 이후 업데이트에서는 다운로드 크기를 줄이기 위한 빠른 설치 파일을 사용합니다. 업데이트가 설치되지 않은 Windows 10 버전 1607과 이전 버전에서는 빠른 설치 파일이 지원되지 않습니다.

### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>서버에서 Windows 10 업데이트에 대한 빠른 설치 파일의 다운로드를 사용하도록 설정하려면
Windows 10 빠른 설치 파일에 대한 메타데이터 동기화를 시작하려면 소프트웨어 업데이트 지점 속성에서 사용하도록 설정해야 합니다.
1.    Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동합니다.
2.    중앙 관리 사이트나 독립 실행형 기본 사이트를 선택합니다.
3.    **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성**과 **소프트웨어 업데이트 지점**을 차례로 클릭합니다. **업데이트 파일** 탭에서 **승인된 모든 업데이트에 대한 전체 파일 및 Windows 10용 빠른 설치 파일 다운로드**를 선택합니다.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>클라이언트가 빠른 설치 파일을 다운로드 및 설치할 수 있는 지원을 사용하려면
클라이언트에서 빠른 설치 파일 지원을 사용하려면 클라이언트에서 클라이언트 설정의 소프트웨어 업데이트 섹션을 통해 빠른 설치 파일을 사용하도록 설정해야 합니다. 이렇게 하면 지정한 포트에서 빠른 설치 파일을 다운로드하는 요청을 수신 대기하는 새 HTTP 수신기가 생성됩니다. 클라이언트에 이 기능을 사용하도록 설정하는 클라이언트 설정을 배포하면 현재 월의 Windows 10 누적 업데이트와 이전 월의 업데이트 간 델타 다운로드를 시도합니다(클라이언트에서 빠른 설치 파일을 지원하는 Windows 10 버전을 실행해야 함).
1.    소프트웨어 업데이트 지점 구성 요소 속성에서 빠른 설치 파일 지원을 사용하도록 설정합니다(이전 절차).
2.    Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동합니다.
3.    적절한 클라이언트 설정을 선택한 다음 **홈** 탭에서 **속성**을 클릭합니다.
4.    **소프트웨어 업데이트** 페이지를 선택하고 **클라이언트에서 Express 업데이트 설치 사용** 설정에 대해 **예**를 구성하고 **Express 업데이트 콘텐츠를 다운로드하는 데 사용할 포트**에 대해 클라이언트의 HTTP 수신기에서 사용되는 포트를 구성합니다.

