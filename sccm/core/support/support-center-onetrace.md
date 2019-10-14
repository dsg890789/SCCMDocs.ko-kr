---
title: 지원 센터 OneTrace(미리 보기)
titleSuffix: Configuration Manager
description: OneTrace는 CMTrace보다 향상된 지원 센터가 포함된 새로운 로그 뷰어입니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 4cde43d1-9b09-4601-b389-0776de451b4e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0e90a06b956c39cb7a473af87cdfca0f722122ff
ms.sourcegitcommit: cb813496467a5191237d853a6126ea534c12d2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172636"
---
# <a name="support-center-onetrace-preview"></a>지원 센터 OneTrace(미리 보기)

<!--3555962-->

버전 1906부터는 OneTrace가 지원 센터의 새 로그 뷰어입니다. CMTrace와 비슷하게 작동하며 다음과 같이 향상되었습니다.

- 탭 형식 보기
- 도킹 가능한 창
- 향상된 검색 기능
- 로그 보기를 종료하지 않고 필터 사용 가능
- 스크롤바 힌트로 오류가 있는 클러스터를 신속하게 파악
- 신속한 대용량 파일 로그 열기

![OneTrace 로그 뷰어 스크린샷](media/3555962-onetrace.png)

OneTrace는 다음과 같은 여러 로그 파일 형식에 사용할 수 있습니다.

- Configuration Manager 클라이언트 로그
- Configuration Manager 서버 로그
- 상태 메시지
- Windows 10의 Windows 업데이트 ETW 로그 파일
- Windows 7 및 Windows 8.1의 Windows 업데이트 로그 파일

## <a name="prerequisites"></a>필수 구성 요소

- .NET Framework 버전 4.6 이상

## <a name="install"></a>설치

OneTrace는 지원 센터와 설치됩니다. `cd.latest\SMSSETUP\Tools\SupportCenter\SupportCenterInstaller.msi` 경로에서 사이트 서버의 지원 센터 설치 관리자를 찾습니다.

기본적으로 OneTrace 애플리케이션은 `"C:\Program Files (x86)\Configuration Manager Support Center\CMPowerLogViewer.exe`에 설치됩니다.

> [!Note]  
> 지원 센터 및 OneTrace는 WPF(Windows Presentation Foundation)를 사용합니다. 이 구성 요소는 Windows PE에서 사용할 수 없습니다. 계속 작업 순서 배포를 통해 부트 이미지에서 CMTrace를 사용합니다.  

## <a name="see-also"></a>참고 항목

- [지원 센터 로그 뷰어](/sccm/core/support/support-center-ui-reference#bkmk_log-viewer)

- [CMTrace](/sccm/core/support/cmtrace)
