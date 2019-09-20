---
title: macOS 클라이언트 업그레이드
titleSuffix: Configuration Manager
description: Mac 컴퓨터에서 구성 관리자 클라이언트 업그레이드
ms.date: 09/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 74c60941-5eae-4905-9e58-252bdb39df96
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b887a82afce8cf446494e7b9348a0b8c0718e389
ms.sourcegitcommit: cdf2827fb3f44d7522a9b533c115f910aa9c382a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70902564"
---
# <a name="how-to-upgrade-clients-on-mac-computers-in-configuration-manager"></a>Configuration Manager에서 Mac 컴퓨터의 클라이언트를 업그레이드하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 개략적인 단계를 따라 Configuration Manager 애플리케이션을 사용하여 Mac 컴퓨터용 클라이언트를 업그레이드하세요. Mac 클라이언트 설치 파일을 다운로드하고 공유 네트워크 위치나 Mac 컴퓨터의 로컬 폴더에 복사한 후 사용자에게 수동으로 설치하도록 지시할 수 있습니다.  

> [!NOTE]  
> 이 단계를 수행하기 전에 Mac 컴퓨터가 필수 조건을 충족해야 합니다. [Mac 컴퓨터에 대해 지원되는 운영 체제](/sccm/plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers)를 참조하세요.  

## <a name="download-the-latest-mac-client"></a>최신 Mac 클라이언트 다운로드

Configuration Manager용 Mac 클라이언트는 Configuration Manager 설치 미디어에 제공되지 않습니다. [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=47719)에서 다운로드합니다. Mac 클라이언트 설치 파일은 **ConfigmgrMacClient.msi**라는 Windows Installer 파일에 포함되어 있습니다.  

## <a name="create-the-mac-client-installation-file"></a>Mac 클라이언트 설치 파일 만들기

Windows를 실행하는 컴퓨터에서 **ConfigmgrMacClient.msi**를 실행합니다. 이 설치 관리자는 **Macclient.dmg**라는 Mac 클라이언트 설치 파일의 압축을 풉니다. 기본적으로 다음 폴더에서 이 파일을 찾을 수 있습니다. **C:\Program Files(x86)\Microsoft\System Center 2012 Configuration Manager Mac Client**.  

## <a name="extract-the-client-installation-files"></a>클라이언트 설치 파일 추출

**Macclient.dmg**를 Mac 컴퓨터에 복사합니다. Macclient.dmg 파일을 macOS에 탑재한 후 콘텐츠를 Mac 컴퓨터의 폴더에 복사합니다.  

## <a name="create-a-cmmac-file"></a>.cmmac 파일 만들기

1. Mac 클라이언트 설치 파일의 **Tools** 폴더를 엽니다. **CMAppUtil** 도구를 사용하여 클라이언트 설치 패키지에서 .cmmac 파일을 만듭니다. 이 파일을 사용하여 Configuration Manager 애플리케이션을 만듭니다.  

2. Configuration Manager 콘솔을 실행하는 컴퓨터에서 사용할 수 있는 네트워크 위치로 새 **CMClient.pkg.cmmac** 파일을 복사합니다.  

    자세한 내용은 [Mac 컴퓨터용 애플리케이션을 만들어 배포하기 위한 보충 절차](/sccm/apps/get-started/creating-mac-computer-applications#supplemental-procedures-to-create-and-deploy-applications-for-mac-computers)를 참조하세요.  

## <a name="create-and-deploy-the-app"></a>앱 만들기 및 배포

1. Configuration Manager 콘솔에서 **CMClient.pkg.cmmac** 파일에서 [애플리케이션을 만듭니다](/sccm/apps/get-started/creating-mac-computer-applications).  

2. 계층 구조의 Mac 컴퓨터에 [이 애플리케이션을 배포](/sccm/apps/deploy-use/deploy-applications)합니다.  

## <a name="install-the-updated-client"></a>업데이트된 클라이언트 설치

Mac 컴퓨터의 기존 구성 관리자 클라이언트는 업데이트를 설치할 수 있음을 알리는 메시지를 사용자에게 표시합니다. 클라이언트를 설치한 사용자는 Mac 컴퓨터를 다시 시작해야 합니다.  

컴퓨터를 다시 시작한 후 **컴퓨터 등록** 마법사가 자동으로 실행되어 새 사용자 인증서를 요청합니다.

Configuration Manager 등록을 사용하지 않고 Configuration Manager와 독립적으로 클라이언트 인증서를 설치하는 경우에는 [기존 인증서를 사용하도록 클라이언트 구성](#BKMK_UpgradingClient_MachineEnrollment)을 참조하세요.  

## <a name="BKMK_UpgradingClient_MachineEnrollment"></a> 기존 인증서를 사용하도록 클라이언트 구성

이 절차를 사용하여 컴퓨터 등록 마법사가 실행되는 것을 방지하고 업그레이드된 클라이언트가 기존 클라이언트 인증서를 사용하도록 구성합니다.  

1. Configuration Manager 콘솔에서 **Mac OS X** 형식의 [구성 항목을 만듭니다](/sccm/compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client).  

1. 설정 유형이 **스크립트**인 설정을 이 구성 항목에 추가합니다.  

1. 설정에 다음 스크립트를 추가합니다.  

  ``` Shell
  #!/bin/sh  
  echo "Starting script\n"  
  echo "Changing directory to MAC Client\n"  
  cd /Users/Administrator/Desktop/'MAC Client'/  
  echo "Import root cert\n"  
  /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/Root.pfx -A -k /Library/Keychains/System.Keychain -P ROOT  
  echo "Using openssl to convert pfx to a crt\n"  
  /usr/bin/sudo openssl pkcs12 -in /Users/Administrator/Desktop/'MAC Client'/Root.pfx -out Root1.crt -nokeys -clcerts -passin pass:ROOT  
  echo "Adding trust to root cert\n"  
  /usr/bin/sudo /usr/bin/security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.Keychain Root1.crt  
  echo "Import client cert\n"  
  /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/MacClient.pfx -A -k /Library/Keychains/System.Keychain -P MAC  
  echo "Executing ccmclient with MP\n"  
  sudo ./ccmsetup -MP https://SCCM34387.SCCM34387DOM.NET/omadm/cimhandler.ashx  
  echo "Editing Plist file\n"  
  sudo /usr/libexec/Plistbuddy -c 'Add:SubjectName string CMMAC003L' /Library/'Application Support'/Microsoft/CCM/ccmclient.plist  
  echo "Changing directory to CCM\n"  
  cd /Library/'Application Support'/Microsoft/CCM/  
  echo "Making connection to the server\n"  
  sudo open ./CCMClient  
  echo "Ending Script\n"  
  exit  
  ```  

1. [구성 기준](/sccm/compliance/deploy-use/create-configuration-baselines)에 구성 항목을 추가합니다. 그런 다음, Configuration Manager와 별도로 인증서를 설치할 모든 Mac 컴퓨터에 [해당 구성 기준을 배포](/sccm/compliance/deploy-use/deploy-configuration-baselines)합니다.  
