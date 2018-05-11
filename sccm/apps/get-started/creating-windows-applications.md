---
title: Windows 응용 프로그램 만들기
titleSuffix: Configuration Manager
description: Windows 장치용 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 9181c84e-d74f-44ea-9bb9-f7805eb465fc
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 3ac0526d31bb46cce18e096ff1d120eda452c806
ms.sourcegitcommit: 1701943932818e0df1928d9be36ebaf424dd93b7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
---
# <a name="create-windows-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

응용 프로그램을 만들기 위한 다른 System Center Configuration Manager 요구 사항 및 절차 외에도 Windows 장치에 대한 응용 프로그램을 만들어 배포할 때는 다음 사항을 고려해야 합니다.  

## <a name="general-considerations"></a>일반적인 고려 사항  
 Configuration Manager는 다음과 같은 앱 파일 형식의 배포를 지원합니다.  

|장치 유형|지원되는 파일 형식|  
|-----------------|---------------------|  
|Windows RT 및 Windows RT 8.1|\*.appx, \*.appxbundle|  
|Windows 8.1 이상|\*.appx, \*.appxbundle|  



 다음 배포 작업이 지원됩니다.  

|장치 유형|지원되는 작업|  
|-----------------|-----------------------|  
|Windows 8.1 이상|사용 가능, 필수, 제거|  
|Windows RT|사용 가능, 필수, 제거|  

## <a name="support-for-universal-windows-platform-uwp-apps"></a>UWP(유니버설 Windows 플랫폼) 앱 지원  
 Windows 10 장치에서는 LOB(기간 업무) 앱을 설치하기 위한 테스트용 로드 키가 필요하지 않습니다. 그러나 테스트용 로드를 사용하도록 설정하려면 레지스트리 키 **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps**의 값이 1이어야 합니다.  

 이 레지스트리 키를 구성하지 않으면 앱을 처음으로 장치에 배포할 때 Configuration Manager에서 이 값을 자동으로 **1**로 설정하게 됩니다. 이 값을 **0**으로 설정한 경우 Configuration Manager에서 이 값을 자동으로 변경할 수 없고 LOB(기간 업무) 앱의 배포가 실패하게 됩니다.  

 유니버설 Windows 플랫폼 LOB(기간 업무) 앱은 앱을 배포하는 각 장치에서 신뢰할 수 있는 코드 서명 인증서로 서명되어 있어야 합니다. 사내 PKI 인프라의 인증서나 장치에 설치된 타사 공개 루트 인증서의 인증서를 사용할 수 있습니다.  

 Windows 10 Mobile 장치에서 비Symantec 코드 서명 인증서를 사용하여 유니버설 **.appx** 앱에 서명할 수 있습니다. **.xap** 앱 및 Windows 10 Mobile 장치에 설치할 Windows Phone 8.1용으로 작성된 **.appx** 패키지에는 Symantec 코드 서명 인증서를 사용해야 입니다.  

## <a name="deploy-windows-installer-apps-to-enrolled-windows-10-pcs"></a>Windows 10 PC에 등록된 Windows Installer 앱 배포  
 **MDM을 통한 Windows Installer(\*.msi)** 설치 관리자 형식을 사용하면 Windows Installer 기반 앱을 만들어 Windows 10을 실행하는 등록된 PC에 배포할 수 있습니다.  

 이 설치 관리자 유형을 사용하는 경우에 고려해야 하는 사항은 다음과 같습니다.  

-   확장명이 .msi인 파일 하나만 업로드할 수 있습니다.  

-   파일의 제품 코드와 제품 버전을 앱 검색에 사용합니다.  

-   앱의 기본 다시 시작 동작이 사용됩니다. Configuration Manager에서는 이 기능을 제어하지 못합니다.  

-   단일 사용자에 대해 사용자별 MSI 패키지가 설치됩니다.  

-   장치의 모든 사용자에 대해 컴퓨터별 MSI 패키지가 설치됩니다.  

-   각 버전의 MSI 제품 코드가 동일하면 앱 업데이트가 지원됩니다.  
