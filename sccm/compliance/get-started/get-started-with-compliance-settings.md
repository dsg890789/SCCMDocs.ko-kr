---
title: "준수 설정 시작"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에서 준수 설정이 작동하는 방법을 알아봅니다. 또한 알아야 할 핵심 개념에 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
caps.latest.revision: "11"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b1171f806d1bda9671fd5817362285a461ee2d44
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 준수 설정 시작

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 구성 항목을 만들기 전에 이 항목을 검토하여 준수 설정의 작동 방식을 이해하고 알아야 할 핵심 개념을 확인해야 합니다.  

## <a name="how-compliance-settings-works"></a>준수 설정의 작동 방식  
 준수 설정을 통해 조직의 서버, 노트북, 데스크톱 컴퓨터 및 모바일 장치의 구성과 준수를 관리할 수 있습니다.  

 구성 항목은 다음 두 가지 주요 범주로 나뉩니다.  

-   **Configuration Manager 클라이언트를 사용하여 관리되는 장치 설정** - 일반적으로 장치를 관리할 수 있도록 하는 Configuration Manager 클라이언트 소프트웨어가 설치된 장치입니다.  

-   **Configuration Manager 클라이언트 없이 관리되는 장치 설정** - 일반적으로 Microsoft Intune 또는 Configuration Manager 온-프레미스 장치 관리로 관리되는 장치입니다.  

## <a name="what-devices-are-supported"></a>지원되는 장치  


|장치 유형|추가 정보|  
|------------|----------------------|  
|Configuration Manager 클라이언트를 사용하여 Windows PC 관리|레지스트리 키, 파일, Active Directory 특성 등의 항목을 평가할 수 있는 사용자 지정 구성 항목을 만들 수 있습니다.<br /><br /> Windows 10 구성 항목 유형을 사용하는 경우 미리 정의된 목록에서 원하는 설정을 선택합니다.|  
|Windows PC(Microsoft Intune에 등록)|미리 정의된 목록에서 원하는 설정을 선택합니다.|  
|iOS 장치(Microsoft Intune에 등록)|미리 정의된 목록에서 원하는 설정을 선택합니다.|  
|Android 장치(Microsoft Intune에 등록)|미리 정의된 목록에서 원하는 설정을 선택합니다.|  
|Windows Phone 장치(Microsoft Intune에 등록)|미리 정의된 목록에서 원하는 설정을 선택합니다.|  
|Mac 컴퓨터(Configuration Manager 클라이언트 포함)|Mac OS X 기본 설정(속성 목록) 값, 스크립트에서 반환된 결과 등의 항목을 평가할 수 있는 사용자 지정 구성 항목을 만들 수 있습니다.|  
|Mac 컴퓨터(Microsoft Intune에 등록)|미리 정의된 목록에서 원하는 설정을 선택합니다.|  

## <a name="what-is-a-configuration-item"></a>구성 항목 정의  
 구성 항목은 다음 정보를 저장하는 컨테이너로 간주할 수 있습니다. 구성하는 정보는 구성 항목 형식에 따라 달라집니다.  

-   **검색 방법 정보** (프로그램 설정만 포함된 Windows 구성 항목의 경우) - 응용 프로그램에 대한 Windows Installer 파일을 검색하거나 사용자 지정 스크립트를 사용하여 응용 프로그램이 설치되었는지를 검색할 수 있습니다.  

-   **설정** - 설정은 클라이언트 장치에서 준수를 평가하는 데 사용되는 비즈니스 또는 기술 조건을 나타냅니다. 참조 컴퓨터에서 기존 설정을 찾거나 새 설정을 구성할 수 있습니다.  

-   **준수 규칙** - 준수 규칙은 구성 항목 설정의 준수를 정의하는 조건을 지정합니다. 설정의 준수를 평가하려면 먼저 하나 이상의 준수 규칙이 있어야 합니다. 일부 설정에서는 비규격으로 발견된 값을 수정할 수 있습니다. 규칙을 선택할 모든 구성 항목에서 새 규칙을 만들거나 기존 설정을 검색할 수 있습니다.  

-   **지원되는 플랫폼** - 구성 항목의 준수를 평가하도록 정의된 장치 플랫폼입니다. 지원되는 플랫폼 목록에 없는 장치에 구성 항목을 배포하면 준수가 평가되지 됩니다.  

## <a name="what-is-a-configuration-baseline"></a>구성 기준 정의  
 평가할 구성 항목과 필요한 준수 수준을 설명하는 설정 및 규칙이 포함된 구성 기준을 정의하면 준수가 평가됩니다. Configuration Manager에서 웹의 Microsoft System Center Configuration Manager 구성 팩에 있는 이 구성 데이터를 Microsoft 및 기타 공급업체에서 정의한 모범 사례로 가져온 다음 Configuration Manager로 가져올 수 있습니다. 또는 새 구성 항목 및 구성 기준을 만들 수 있습니다.  

 구성 기준을 정의한 후 컬렉션을 통해 사용자 및 장치에 배포하고 일정에 따라 설정의 준수를 평가할 수 있습니다. 장치에 여러 개의 구성 기준이 배포될 수 있습니다. 이렇게 하면 높은 수준의 제어를 사용할 수 있습니다.  

 클라이언트 장치는 배포된 각 구성 기준에 대해 준수를 평가하고 상태 메시지 및 상황 메시지를 사용하여 해당 결과를 사이트에 즉시 보고합니다. 클라이언트 장치가 현재 네트워크에 연결되어 있지 않지만 배포된 구성 기준에서 참조된 구성 항목을 다운로드한 경우 구성 기준의 준수가 평가됩니다. 다시 연결하면 준수 정보가 전송됩니다.  

 Configuration Manager 콘솔, **모니터링** 작업 영역의 **배포** 노드에서 구성 기준 평가 준수의 결과를 모니터링하여 비준수의 가장 일반적인 원인, 오류 및 영향받는 사용자와 장치 수를 확인할 수 있습니다. 준수 설정 보고서를 실행하여 준수 또는 비준수 장치, 컴퓨터를 비준수로 만드는 구성 기준의 요소 등의 추가 정보를 찾을 수도 있습니다. Configuration Manager 클라이언트 소프트웨어를 실행하는 Windows 컴퓨터에서 제어판의 **Configuration Manager**에 있는 **구성** 탭을 사용하여 준수 평가 결과를 볼 수도 있습니다.  

## <a name="user-data-and-profiles-configuration-items"></a>사용자 데이터 및 프로필 구성 항목  
 사용자 데이터 및 프로필 구성 항목에는 계층 구조 내 사용자가 Windows 8 이상을 실행하는 컴퓨터에서 폴더 리디렉션, 오프라인 파일 및 로밍 프로필 등을 관리하는 방법을 제어하는 설정이 포함됩니다. 이러한 구성 항목을 사용자 컬렉션에 배포한 다음 Configuration Manager 콘솔의 **모니터링** 노드에서 준수를 모니터링할 수 있습니다. 다른 구성 항목과 달리, 이 구성 항목은 배포 전에 구성 기준에 추가하지 않습니다. **사용자 데이터 및 프로필 구성 항목** 대화 상자에서 직접 배포할 수 있습니다.  

 자세한 내용은 [사용자 데이터 및 프로필 구성 항목 만들기](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)를 참조하세요.  

## <a name="remote-connection-profiles"></a>원격 연결 프로필  
 원격 연결 프로필은 조직에서 원격 연결 설정을 만들어 장치에 배포하고 모니터링하는 데 유용한 도구 및 리소스 집합을 제공합니다. 이러한 설정을 배포하면 최종 사용자가 회사 네트워크에서 자신의 컴퓨터에 연결하기 위해 수행해야 하는 작업이 최소화됩니다.  

자세한 내용은 [원격 연결 프로필 만들기](/sccm/compliance/deploy-use/create-remote-connection-profiles)를 참조하세요.  

## <a name="windows-edition-upgrade"></a>Windows 버전 업그레이드
버전 업그레이드 정책을 사용하면 새 제품 키 또는 라이선스 파일을 제공하여 Windows 10의 특정 버전을 실행하는 장치를 자동으로 최신 버전으로 업그레이드할 수 있습니다.

자세한 내용은 [버전 업그레이드 정책을 사용하여 Windows 장치 업그레이드](/sccm/compliance/deploy-use/upgrade-windows-version)를 참조하세요.
