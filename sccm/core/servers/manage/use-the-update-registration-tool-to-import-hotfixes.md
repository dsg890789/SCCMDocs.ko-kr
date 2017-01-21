---
title: "업데이트 등록 도구 | System Center Configuration Manager"
description: "업데이트 등록 도구를 사용하여 수동으로 업데이트를 Configuration Manager 콘솔로 가져오는 시기 및 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cc13635-85d6-4b07-a3ec-c42188bc5c74
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 176c1d7055ae8706b92886d59d8a048dd867c18b


---
# <a name="use-the-update-registration-tool-to-import-hotfixes-to-system-center-configuration-manager"></a>업데이트 등록 도구를 사용하여 System Center Configuration Manager에 핫픽스 가져오기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 일부 업데이트는 Microsoft 클라우드 서비스에서 사용할 수 없으며, 대역 외에서만 가져옵니다. 특정 문제를 해결하는 제한된 릴리스 핫픽스를 예로 들 수 있습니다.   
대역 외 릴리스를 설치해야 하고 업데이트 또는 핫픽스 파일 이름이 **update.exe** 확장명으로 끝나는 경우 **업데이트 등록 도구**를 사용하여 Configuration Manager 콘솔에 업데이트를 수동으로 가져옵니다. 이 도구를 통해 업데이트 패키지를 추출하여 사이트 서버에 전송하고 Configuration Manager 콘솔에 업데이트를 등록할 수 있습니다.  

 핫픽스 파일의 파일 확장명이 **.exe**인 경우(**update.exe** 제외) [핫픽스 설치 관리자를 사용하여 System Center Configuration Manager의 업데이트 설치](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)를 참조하세요.  

> [!NOTE]  
>  이 항목에서는 System Center Configuration Manager를 업데이트하는 핫픽스를 설치하는 방법에 대한 일반적인 지침을 제공합니다. 특정 핫픽스 또는 업데이트에 대한 자세한 내용은 Microsoft 지원에서 해당 KB(기술 자료)를 참조하세요.  

 **업데이트 등록 도구를 사용하기 위한 필수 조건:**  

-   **.update.exe** 확장명으로 끝나는 대역 외 업데이트만 이 도구를 사용하여 설치할 수 있습니다.  

-   이 도구는 Microsoft에서 직접 가져오는 개별 업데이트를 자체 포함합니다.  

-   이 도구는 서비스 연결 지점의 모드에 종속되지 않습니다.  

-   이 도구는 서비스 연결 지점을 호스트하는 컴퓨터에서 실행해야 합니다.  

-   도구가 실행되는 컴퓨터(서비스 연결 지점 컴퓨터)에는 NET Framework 4.52가 설치되어 있어야 합니다.  

-   서비스 연결 지점을 호스트하는(도구가 실행되는) 컴퓨터에서 도구를 실행하는 데 사용할 계정에 **로컬 관리자** 권한이 있어야 합니다.  

-   이 도구를 실행하는 데 사용할 계정에는 서비스 연결 지점을 호스트하는 컴퓨터에서 다음 폴더에 대한 **쓰기** 권한이 있어야 합니다. **&lt;ConfigMgr 설치 디렉터리\>\EasySetupPayload\offline**  

### <a name="to-use-the-update-registration-tool"></a>업데이트 등록 도구를 사용하려면  

1.  서비스 연결 지점을 호스트하는 컴퓨터:  

    -   관리자 권한으로 명령 프롬프트를 열고 **&lt;제품\>-&lt;제품 버전\>-&lt;KB 문서 ID\>-ConfigMgr.Update.exe**가 포함된 위치로 디렉터리를 변경합니다.  

2.  다음 명령을 실행하여 업데이트 등록 도구를 시작합니다.  

    -   **&lt;제품\>-&lt;제품 버전\>-&lt;KB 문서 ID\>-ConfigMgr.Update.exe**  

    핫픽스를 등록하면 콘솔에서 24 시간 내에 새 업데이트로 표시됩니다.  다음 중 하나를 사용하여 프로세스를 가속화할 수 있습니다.  

    -   버전 1511의 경우: Configuration Manager 콘솔에서 **관리 > Cloud Services > 업데이트 및 서비스**로 이동한 후 **즉시 업데이트 검색 프로세스를 시작합니다.**를 선택합니다.  그러면 등록 프로세스가 완료되는 즉시 핫픽스 가져오기를 시작하여 콘솔에서 사용할 수 있도록 합니다.  

    -   버전 1602 이상의 경우: Configuration Manager 콘솔에서 **관리 > Cloud Services > 업데이트 및 서비스**로 이동한 후 **업데이트 확인**을 클릭합니다.  

    업데이트 등록 도구는 로컬 컴퓨터의 .log 파일에 작업을 로깅합니다. 로그 파일은 hotfix.exe 파일과 이름이 같으며 **%SystemRoot%/Temp** 폴더에 기록됩니다.  

     업데이트가 등록된 후 업데이트 등록 도구를 닫을 수 있습니다.  

3.  Configuration Manager 콘솔을 열고 **관리** > **클라우드 서비스** > **업데이트 및 서비스**를 선택합니다. 이제 가져온 핫픽스를 설치할 수 있습니다. 업데이트를 설치하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 콘솔 내 업데이트 설치](../../../core/servers/manage/install-in-console-updates.md)를 참조하세요.  



<!--HONumber=Nov16_HO1-->


