---
title: Updates Publisher 설치
titleSuffix: Configuration Manager
description: 환경에 System Center Updates Publisher 설치
ms.date: 07/03/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: ab5cda93-b67c-4aa5-904d-7b63ce790aa0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cd48e40f594ced5a62e3a65beb43e6dc74e090b
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56122477"
---
# <a name="install-updates-publisher"></a>Updates Publisher 설치

*적용 대상: System Center Updates Publisher*

이 항목의 정보는 사용자 환경에서 사용할 수 있도록 Updates Publisher를 가져오기, 설치 및 설정할 때 참조할 수 있습니다.


## <a name="prerequisites-and-limitations"></a>필수 구성 요소 및 제한 사항
다음 섹션에서는 Updates Publisher를 설치하고 사용하기 위한 요구 사항과 사용 제한 사항 또는 알려진 문제점에 대해 자세히 설명합니다.

### <a name="operating-systems"></a>운영 체제
다음 운영 체제의 64비트 버전에 Updates Publisher를 설치하고 실행합니다. 최소 누적 업데이트 또는 서비스 팩 요구 사항은 없습니다.

-   Windows Server 2016(Standard, Datacenter)
-   Windows Server 2012 R2(Standard, Datacenter)
-   Windows 10(Pro, Education, Pro Education, Enterprise)
-   Windows 8.1(Professional, Enterprise)

### <a name="prerequisites"></a>필수 구성 요소
Updates Publisher를 실행하는 컴퓨터에는 다음이 필요합니다.

-   **64비트 운영 체제**: Updates Publisher를 설치하려면 컴퓨터에서 64비트 운영 체제를 실행해야 합니다.
-   **WSUS 4.0 이상**:
    -   Windows Server에서 이 요구 사항을 충족시키려면 기본 관리 콘솔을 설치합니다.
    -   Windows 10 및 Windows 8.1의 경우 [Windows 운영 체제용 RSAT(원격 서버 관리 도구)](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems)를 설치합니다. 그러면 Updates Publisher를 사용하는 데 필요한 지원(*API 및 PowerShell cmdlet* 및 *사용자 인터페이스 관리 콘솔*)이 설치됩니다.
-   **사용 권한**:
    -   설치: 로컬 관리자
    -   대부분의 작업: 로컬 사용자
    -   게시 또는 WSUS와 관련된 작업: WSUS 서버의 WSUS 관리자 그룹의 멤버입니다.

### <a name="supported-languages"></a>지원되는 언어
Updates Publisher는 영어로만 제공되지만 다른 언어의 업데이트를 관리할 수 있습니다. 언어 지원은 업데이트 게시, 만들기 또는 편집과 같은 작업에 따라 달라집니다.

업데이트를 내보내거나 게시할 때 Updates Publisher는 Updates Publisher가 설치된 컴퓨터의 로캘에 따라 소프트웨어 업데이트의 제목과 설명을 표시합니다.

예를 들어 영어 및 스페인어 제목이 있는 소프트웨어 업데이트를 만듭니다.

-   로캘이 영어인 컴퓨터에서 업데이트를 만들면 기본적으로 제목과 설명이 영어로 표시됩니다.
-   로캘이 스페인어인 컴퓨터로 업데이트를 내보내거나 게시하면 해당 컴퓨터에서 제목과 설명이 스페인어로 표시됩니다.

### <a name="publishing"></a>게시
소프트웨어 업데이트를 게시할 때 소프트웨어 업데이트 이진 파일의 언어를 지정할 수 있습니다. 이진 파일이 언어 중립적임을 지정할 수도 있습니다. 다음 언어가 지원됩니다.

-   아랍어
-   중국어(홍콩 특별 행정구)
-   옵션 대신,
-   중국어(간체)
-   체코어
-   덴마크어
-   네덜란드어
-   영어
-   핀란드어
-   프랑스어
-   독일어
-   그리스어
-   히브리어
-   헝가리어
-   이탈리아어
-   일본어
-   한국어
-   노르웨이어
-   폴란드어
-   포르투갈어
-   포르투갈어(브라질)
-   러시아어
-   스페인어
-   스웨덴어
-   터키어

### <a name="software-update-titles-and-descriptions"></a>소프트웨어 업데이트 제목 및 설명
소프트웨어 업데이트 제목 및 설명에는 다음 언어가 지원됩니다.

-   옵션 대신,
-   중국어(간체)
-   영어
-   프랑스어
-   독일어
-   이탈리아어
-   일본어
-   한국어
-   포르투갈어(브라질)
-   러시아어
-   스페인어



## <a name="install-updates-publisher"></a>Updates Publisher 설치
[Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=55543)에서 System Center Updates Publisher를 설치하기 위한 **UpdatesPubliser.msi**를 다운로드합니다.

Updates Publisher를 설치하려면 *필수 조건*을 충족하는 컴퓨터에서 **UpdatesPublisher.msi**를 실행합니다. 설치 관리자는 Updates Publisher를 실행하는 데 필요한 파일을 포함하는 *&lt;path&gt;\Program Files\Microsoft\UpdatesPublisher* 폴더를 만듭니다.

이 폴더에는 Updates Publisher를 사용하는 데 필요한 모든 파일이 포함되기 때문에, 이 폴더 및 해당 콘텐츠를 새 위치 또는 컴퓨터에 복사한 다음 해당 위치에서 Updates Publisher를 사용할 수 있습니다. 그러나 Updates Publisher를 실행하려면 새로운 위치 또는 컴퓨터가 필수 조건을 충족해야 합니다.

설치가 완료되면 *UpdatesPublisher* 폴더에서 **UpdatesPublisher.exe**를 실행하여 Updates Publisher를 시작합니다.

## <a name="next-steps"></a>다음 단계
 Updates Publisher를 설치한 후에는 Updates Publisher에 대한 [옵션을 구성](updates-publisher-options.md)하는 것이 좋습니다. Updates Publisher의 일부 기능을 사용하려면 일부 옵션을 구성해야 합니다.

 그러나 기본값을 사용하고 업데이트 서버 또는 관리 디바이스에 업데이트를 배포하지 않으려면 [소프트웨어 업데이트 카탈로그 관리](updates-publisher-catalogs.md)로 바로 이동하거나, [소프트웨어 업데이트를 만들고](create-updates-with-updates-publisher.md) 업데이트 카탈로그를 직접 만듭니다.

