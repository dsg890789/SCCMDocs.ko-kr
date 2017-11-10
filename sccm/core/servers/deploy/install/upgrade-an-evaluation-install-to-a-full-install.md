---
title: "평가판 설치 업그레이드"
titleSuffix: Configuration Manager
description: "평가판 설치를 System Center Configuration Manager 전체 설치로 업그레이드하는 방법을 알아봅니다."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a32f5a3-9917-434f-9811-106170f404be
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 942ac0a1d7681cb1efb06ff477a27a7c5c57654b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="upgrade-an-evaluation-installation-of-system-center-configuration-manager-to-a-full-installation"></a>평가판 설치를 System Center Configuration Manager 전체 설치로 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 평가판으로 설치하는 경우 180일이 지나면 Configuration Manager 콘솔은 설치 프로그램의 **사이트 유지 관리** 페이지에서 제품을 정품 인증할 때까지 읽기 전용 상태가 됩니다. 180일 기간 전이나 후에 언제든지 평가판 설치를 전체 설치로 업그레이드하는 옵션이 있습니다.  

> [!NOTE]  
>  Configuration Manager 콘솔을 Configuration Manager 평가판 설치에 연결하는 경우 콘솔의 제목 표시줄에는 평가판 설치가 만료되기까지 남은 기간(일)이 표시됩니다. 일 수는 자동으로 새로 고쳐지지 않으며 사이트에 새로 연결할 때에만 업데이트됩니다.  

 평가판 설치를 실행하는 다음 사이트를 업그레이드할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  

보조 사이트는 평가판 설치로 처리되지 않으므로 기본 부모 사이트를 전체 설치로 업그레이드한 후에 보조 사이트를 수정할 필요가 없습니다.  

평가판을 라이선스 버전으로 업그레이드하기 위한 사전 요구 사항:  

-   업그레이드 중에 사용할 유효한 제품이 있어야 합니다.  
-   계정에 사이트가 설치된 컴퓨터에 대한 **관리자** 권한이 있어야 합니다.  

### <a name="to-upgrade-an-evaluation-version-of-configuration-manager-to-a-licensed-version"></a>Configuration Manager의 평가판을 라이선스 버전으로 업그레이드하려면  

1.  사이트 서버의 Configuration Manager 설치 폴더(**%path%\BIN\X64**)에서 **Setup.exe**(Configuration Manager 설치 프로그램)를 찾아서 실행합니다. 설치 미디어에서 설치 프로그램을 실행하면 사이트 유지 관리 옵션이 제공되지 않으므로 사이트 서버에 있는 설치 프로그램의 복사본은 Configuration Manager 폴더에서 실행해야 합니다.  
2.  **시작하기 전에** 페이지에서 **다음**을 선택합니다.  
3.  **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 선택합니다.  
4.  **사이트 유지 관리** 페이지에서 **평가판을 라이선스 버전으로 업그레이드합니다.**를 선택하고 유효한 제품 키를 입력한 후 **다음**을 선택합니다.  
5.  **Microsoft 소프트웨어 사용 조건** 페이지에서 사용 조건을 읽고 동의한 후 **다음**을 선택합니다.  
6.  **구성** 페이지에서 **닫기** 를 선택하여 마법사를 완료합니다.  

    > [!NOTE]  
    >  Configuration Manager 콘솔이 업그레이드하는 사이트에 계속 연결되어 있는 경우 해당 사이트를 콘솔에 다시 연결할 때까지는 콘솔의 제목 표시줄에 사이트가 아직 평가판이라고 표시될 수 있습니다.  
