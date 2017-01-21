---
title: "클라이언트 업그레이드 | Mac | System Center Configuration Manager"
description: "System Center Configuration Manager에서 Mac 컴퓨터용 클라이언트를 업그레이드합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74c60941-5eae-4905-9e58-252bdb39df96
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: e2e13d31ccdeba155b4030a78d12b82939394f54


---
# <a name="how-to-upgrade-clients-on-mac-computers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Mac 컴퓨터의 클라이언트를 업그레이드하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 응용 프로그램을 사용하여 Mac 컴퓨터용 클라이언트를 업그레이드하려면 아래에 설명된 개략적인 단계를 따르세요. 또는, Mac 클라이언트 설치 파일을 다운로드하고 공유 네트워크 위치나 Mac 컴퓨터의 로컬 폴더에 복사한 후 사용자에게 수동으로 설치하도록 지시할 수 있습니다.  

> [!NOTE]  
>  이러한 단계를 수행하기 전에 Mac 컴퓨터가 필수 조건을 충족해야 합니다. [Mac 컴퓨터에 대해 지원되는 운영 체제](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mac-computers)를 참조하세요.  

## <a name="step-1-download-the-latest-mac-client-installation-file-from-the-microsoft-download-center"></a>1단계: Microsoft 다운로드 센터에서 최신 Mac 클라이언트 설치 파일 다운로드  
 Configuration Manager용 Mac 클라이언트는 Configuration Manager 설치 미디어에 제공되지 않으므로 Microsoft 다운로드 센터에서 다운로드해야 합니다. Mac 클라이언트 설치 파일은 ConfigmgrMacClient.msi라는 Windows Installer 파일에 포함되어 있습니다.  

 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/p/?LinkId=525184)에서 다운로드할 수 있습니다.  

## <a name="step-2-run-the-downloaded-installation-file-to-create-the-mac-client-installation-file"></a>2단계: 다운로드한 설치 파일을 실행하여 Mac 클라이언트 설치 파일 만들기  
 Windows를 실행하는 컴퓨터에서, 다운로드한 **ConfigmgrMacClient.msi** 를 실행하여 **Macclient.dmg**라는 Mac 클라이언트 설치 파일의 압축을 풉니다. 기본적으로 이 파일의 압축을 풀면 Windows 컴퓨터의 **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client** 폴더에 위치합니다.  

## <a name="step-3-extract-the-client-installation-files"></a>3단계: 클라이언트 설치 파일 추출  
 Macclient.dmg 파일을 네트워크 공유 위치나 Mac 컴퓨터의 로컬 폴더에 복사합니다. 그런 다음 Mac 컴퓨터에서 Macclient.dmg 파일을 탑재하고 연 후 파일을 Mac 컴퓨터의 폴더에 복사합니다.  

## <a name="step-4-create-a-cmmac-file-that-can-be-used-to-create-an-application"></a>4단계: 응용 프로그램을 만드는 데 사용할 수 있는 .cmmac 파일 만들기  

1.  Mac 클라이언트 설치 파일의 **Tools** 폴더에 있는 **CMAppUtil** 도구를 사용하여 클라이언트 설치 패키지로부터 .cmmac 파일을 만듭니다. 이 파일은 Configuration Manager 응용 프로그램을 만드는 데 사용됩니다.  

2.  Configuration Manager 콘솔을 실행하는 컴퓨터에서 사용할 수 있는 위치로 새 **CMClient.pkg.cmmac** 파일을 복사합니다.  

 자세한 내용은 [Mac 컴퓨터용 응용 프로그램을 만들어 배포하기 위한 보충 절차](/sccm/apps/get-started/creating-mac-computer-applications#supplemental-procedures-to-create-and-deploy-applications-for-mac-computers)를 참조하세요.  

## <a name="step-5-create-and-deploy-an-application-containing-the-mac-client-files"></a>**5단계:** Mac 클라이언트 파일을 포함하는 응용 프로그램을 만들어 배포  

1.  Configuration Manager 콘솔에서 클라이언트 설치 파일이 포함된 **CMClient.pkg.cmmac** 파일에서 응용 프로그램을 만듭니다.  

2.  이 응용 프로그램을 계층 내의 Mac 컴퓨터에 배포합니다.  

 자세한 내용은 [System Center Configuration Manager에서 Mac 컴퓨터 응용 프로그램 만들기](../../../../apps/get-started/creating-mac-computer-applications.md)를 참조하세요.  

## <a name="step-6-users-install-the-latest-client"></a>6단계: 사용자가 최신 클라이언트 설치  
 Mac 클라이언트 사용자에게 Configuration Manager 클라이언트의 업데이트를 사용할 수 있으며 설치해야 한다는 메시지가 표시됩니다. 클라이언트를 설치한 사용자는 Mac 컴퓨터를 다시 시작해야 합니다.  

 컴퓨터를 다시 시작한 후 컴퓨터 등록 마법사가 자동으로 실행되어 새 사용자 인증서를 요청합니다.  

 Configuration Manager 등록을 사용하지 않고 Configuration Manager와 독립적으로 클라이언트 인증서를 설치하는 경우에는 [업그레이드된 클라이언트가 기존 인증서를 사용하도록 구성](#BKMK_UpgradingClient_MachineEnrollment)을 참조하세요.  

##  <a name="a-namebkmkupgradingclientmachineenrollmenta-configure-the-upgraded-client-to-use-an-existing-certificate"></a><a name="BKMK_UpgradingClient_MachineEnrollment"></a> Configure the upgraded client to use an existing certificate  
 다음 절차를 실행하여 컴퓨터 등록 마법사가 실행되는 것을 방지하고 업그레이드된 클라이언트가 기존 클라이언트 인증서를 사용하도록 구성합니다.  

-   Configuration Manager 콘솔에서 **Mac OS X** 형식의 구성 항목을 만듭니다.  

-   설정 유형이 **스크립트**인 설정을 이 구성 항목에 추가합니다.  

-   설정에 다음 스크립트를 추가합니다.  

    ```  
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

-   구성 기준에 구성 항목을 추가한 후 Configuration Manager와 별도로 인증서를 설치할 모든 Mac 컴퓨터에 해당 구성 기준을 배포합니다.  

 Mac 컴퓨터에 대한 구성 항목을 만들고 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 클라이언트로 관리되는 Mac OS X 장치에 대한 구성 항목을 만드는 방법](../../../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md) 및 [System Center Configuration Manager에서 구성 기준을 배포하는 방법](../../../../compliance/deploy-use/deploy-configuration-baselines.md)을 참조하세요.  



<!--HONumber=Nov16_HO1-->


