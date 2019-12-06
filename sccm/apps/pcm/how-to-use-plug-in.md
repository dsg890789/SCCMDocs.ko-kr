---
title: 변환 플러그 인을 사용하는 방법
titleSuffix: Configuration Manager
description: Package Conversion Manager 플러그 인을 사용하여 분석 및 변환 프로세스를 사용자 지정합니다.
ms.date: 08/24/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 83cf156c-36de-483f-a9e6-2e06158f3b20
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d76b43a1918184fea9cc97bb3ed35a57a7c7ada
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62198476"
---
# <a name="how-to-use-the-package-conversion-manager-plug-in"></a>Package Conversion Manager 플러그 인을 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1357861-->

Package Conversion Manager 플러그 인은 분석 및 변환 프로세스를 사용자 지정하는 데 도움이 됩니다. Package Conversion Manager 플러그 인을 사용하려면 사용자 지정 작업을 수행하는 실행 파일이나 스크립트 파일을 작성합니다. 그런 다음, 해당 실행 파일이나 스크립트를 호출하도록 구성 파일, Microsoft.ConfigurationManagement.exe.config를 편집합니다. 스크립트를 작성할 때 가장 흔히 사용되는 언어는 VBScript 또는 PowerShell입니다.

Package Conversion Manager 플러그 인은 패키지마다 한 번씩 실행됩니다. 한 번에 여러 패키지를 분석하거나 변환하는 경우, Package Conversion Manager 플러그 인이 매번 실행됩니다.

> [!NOTE]  
> Configuration Manager 구성 파일의 Package Conversion Manager 요소에 대한 자세한 내용은 [Package Conversion Manager 플러그 인 구성 XML에 대한 기술 참조](/sccm/apps/pcm/plugin-config-xml)를 참고하세요.



## <a name="default-process"></a>기본 프로세스

기본적으로 Package Conversion Manager는 다음 작업을 수행합니다.

1.  Configuration Manager 패키지를 읽습니다.  

2.  패키지에서 애플리케이션을 만들고 기본 특성을 추가합니다.  

3.  애플리케이션을 분석하여 패키지 준비 상태를 확인합니다.  

4.  Package Conversion Manager 작업에 따라 다음 작업 중 하나를 수행합니다.  

    - **분석**: Configuration Manager 콘솔에 패키지 준비 상태를 표시합니다.  

    - **변환**: Configuration Manager 데이터베이스에 애플리케이션을 기록합니다.  


## <a name="plug-in-based-process"></a>플러그 인 기반 프로세스 

플러그 인을 사용하는 경우 Package Conversion Manager는 다음 작업을 수행합니다.

1.  Configuration Manager 패키지를 읽습니다.  

2.  패키지에서 애플리케이션을 만들고 기본 특성을 추가합니다.  

3.  애플리케이션을 XML로 변환합니다. 파일을 디스크에 저장합니다.  

4.  플러그 인 스크립트를 실행하여 애플리케이션 XML을 수정합니다. 자세한 내용은 [Package Conversion Manager 플러그 인 구성 XML에 대한 기술 참조](/sccm/apps/pcm/plugin-config-xml)를 참고하세요.  

5.  애플리케이션 XML을 Configuration Manager 애플리케이션으로 변환합니다.  

6.  애플리케이션을 분석하여 패키지 준비 상태를 확인합니다.  

7.  Package Conversion Manager 작업에 따라 다음 작업 중 하나를 수행합니다.  

    - **분석**: Configuration Manager 콘솔에 패키지 준비 상태를 표시합니다.  

    - **변환**: Configuration Manager 데이터베이스에 애플리케이션을 기록합니다.  



## <a name="see-also"></a>참고 항목

[Package Conversion Manager 플러그 인 구성 XML에 대한 기술 참조](/sccm/apps/pcm/plugin-config-xml)
