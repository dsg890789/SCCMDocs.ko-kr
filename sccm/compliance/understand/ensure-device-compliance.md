---
title: 디바이스 규정 준수를 확인합니다.
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 조직에서 디바이스의 구성 및 호환성을 관리합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 7568c9aa-b99e-4466-bfc8-0301aa376930
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: b3512c9d784f529952d3e6358950acf5bc08f24e
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75818131"
---
# <a name="ensure-device-compliance-with-configuration-manager"></a>Configuration Manager를 사용하여 디바이스 준수를 확인합니다.

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 호환성 설정은 조직에서 디바이스의 구성과 호환성을 관리하는 데 필요한 도구와 리소스를 제공합니다. 다음과 같은 비즈니스 요구 사항을 지원하는 데 도움이 됩니다.  

-   관리하는 Windows PC, Mac 컴퓨터, 서버 및 모바일 디바이스의 구성과 직접 만들었거나 다른 공급업체에서 얻은 모범 사례 구성 비교  

-   권한이 없는 디바이스 구성 식별  

-   규정 정책 및 사내 보안 정책 준수 보고  

-   보안 취약점 식별  

-   기술 지원팀에서 비준수 구성을 식별하여 보고된 인시던트 및 문제의 가능한 원인을 검색하기 위한 정보 제공  

-   자동으로 모바일 디바이스의 일부 비준수 설정 수정  

-   비준수를 보고하는 디바이스가 자동으로 포함되는 컬렉션에 애플리케이션, 패키지 및 프로그램 또는 스크립트를 배포하여 비준수 수정  


## <a name="get-started"></a>시작  
 준수 설정과 준수 설정에 대해 수행할 수 있는 작업에 대한 기본 사항을 알아봅니다.  

 [준수 설정 시작](../../compliance/get-started/get-started-with-compliance-settings.md)  

## <a name="plan-and-design"></a>계획 및 디자인  
 준수 설정을 사용하여 작업을 시작하기 전에 이 항목에 나와 있는 필수 조건을 구현해야 합니다.  

 [준수 설정 계획 및 구성](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

## <a name="common-tasks"></a>일반 작업  
 이 섹션에는 Configuration Manager의 준수 설정을 사용하는 방법을 알아보는 데 유용한 몇 가지 일반적인 시나리오가 있습니다.  

 [준수 관리를 위한 일반 작업](../../compliance/plan-design/common-tasks-for-managing-compliance.md)  

## <a name="remote-connection-profiles"></a>원격 연결 프로필  
 이 구성 항목 유형을 통해 사용자가 도메인에 연결되어 있지 않거나 사용자의 개인용 컴퓨터가 인터넷을 통해 연결된 경우 사용자의 PC가 원격으로 연결하여 컴퓨터 작업을 하도록 구성할 수 있습니다.  

 [원격 연결 프로필 만들기](/sccm/compliance/deploy-use/create-remote-connection-profiles)  

## <a name="user-data-and-profiles"></a>사용자 데이터 및 프로필  
 이 구성 항목에는 Windows 8을 실행하는 컴퓨터에서 계층 구조 내 사용자에 대해 폴더 리디렉션, 오프라인 파일 및 로밍 프로필을 관리할 수 있는 설정이 포함되어 있습니다.  

 [사용자 데이터 및 프로필 구성 항목 만들기](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)  

## <a name="windows-edition-upgrade-policy"></a>Windows 버전 업그레이드 정책  
 버전 업그레이드 정책을 통해 Windows 10 디바이스를 최신 버전으로 자동으로 업그레이드할 수 있습니다. Windows 10 데스크톱 버전을 업그레이드할 제품 키 또는 Windows 10 Mobile 및 Windows 10 Holographic을 실행하는 디바이스를 업그레이드하는 데 사용할 수 있는 라이선스 파일을 지정할 수 있습니다.  

 [버전 업그레이드 정책을 사용하여 Windows 디바이스 업그레이드](/sccm/compliance/deploy-use/upgrade-windows-version)  
