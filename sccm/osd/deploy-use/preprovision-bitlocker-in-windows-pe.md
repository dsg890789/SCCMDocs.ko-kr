---
title: "Windows PE에서 BitLocker 사전 프로비전 | Microsoft 문서"
description: "Configuration Manager에서 BitLocker 사전 프로비전 작업을 통해 운영 체제를 배포하기 전에 Windows 사전 설치 환경에서 BitLocker를 사용하도록 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7c94ba0-d709-4129-8077-075a8abaea1c
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: baca498dbc5b8e168852aa3c18ee23a9c483e69c


---
# <a name="preprovision-bitlocker-in-windows-pe-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 Windows PE에서 BitLocker 사전 프로비전

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 **BitLocker 사전 프로비전** 작업 순서 단계를 통해 운영 체제 배포 전에 Windows PE(Windows 사전 설치 환경)에서 BitLocker를 사용하도록 설정할 수 있습니다. 사용된 드라이브 공간만 암호화되므로 암호화 속도가 훨씬 빠릅니다. Windows 설치 프로세스를 실행하기 전에 임의로 생성된 암호화되지 않은 보호기를 포맷된 볼륨에 적용하고 볼륨을 암호화하여 그렇게 할 수 있습니다. Windows 8 및 Windows Server 2012에는 BitLocker를 사전 프로비전하는 기능이 도입되었습니다. 그러나 다음 단계를 따르면 하드 드라이브에서 BitLocker를 사전 프로비전하고 Windows 7을 설치할 수 있습니다. Windows 7 설치가 완료되면 Windows 7 BitLocker 제어판에서 암호화되지 않은 보호기를 사용하는 BitLocker를 지원하지 않으므로 BitLocker 키 보호기를 설정해야 합니다. **BitLocker 사용** 단계를 사용하거나 manage-bde.exe 명령줄 도구를 사용하여 키 보호기를 추가해야 합니다.  

 일반적으로, Windows 7을 설치할 컴퓨터에서 BitLocker를 사전 프로비전하려면 다음 단계를 수행해야 합니다.  

-   Windows PE에서 컴퓨터 다시 시작  

    > [!IMPORTANT]  
    >  BitLocker를 사전 프로비전하려면 Windows PE 4 이상의 부팅 이미지를 사용해야 합니다. Configuration Manager에서 지원되는 Windows PE 버전에 대한 자세한 내용은 [Configuration Manager 외부 종속성](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_ExternalDependencies)을 참조하세요.  

-   하드 드라이브 파티션 및 포맷  

-   의  

-   특정 운영 체제 및 네트워크 설정으로 Windows 7 설치  

-   BitLocker에 키 보호기 추가  

 Configuration Manager에서, BitLocker를 하드 드라이브에서 사전 프로비전하고 Windows 7을 설치하는 권장 방법은 새 작업 순서를 만들고 **작업 순서 만들기 마법사**의 **새 작업 순서 만들기** 페이지에서 **기존 이미지 패키지 설치**를 선택하는 것입니다. 이 마법사는 다음 표에 나열된 작업 순서 단계를 만듭니다.  

> [!NOTE]  
>  마법사에서 설정을 구성한 방법에 따라, 이 작업 순서에서 추가 단계가 포함할 수 있습니다. 예를 들어, 마법사의 **상태 마이그레이션** 페이지에서 **캡처된 Microsoft Windows 설정** 을 선택한 경우 **Windows 설정 캡처** 단계가 추가될 수 있습니다.  

|작업 순서 단계|세부 정보|  
|------------------------|-------------|  
|Bitlocker 사용 안 함|이 단계에서는, BitLocker 암호화가 현재 사용되도록 설정된 경우 해당 설정을 사용하지 않도록 지정합니다. 자세한 내용은 [Bitlocker 사용 안 함](../understand/task-sequence-steps.md#BKMK_DisableBitLocker)을 참조하세요.|  
|Windows PE에서 컴퓨터 다시 시작|이 단계에서는 작업 순서에 할당된 부팅 이미지를 실행하여 Windows PE에서 컴퓨터를 다시 시작합니다. BitLocker를 사전 프로비전하려면 Windows PE 4 이상의 부팅 이미지를 사용해야 합니다. 자세한 내용은 [컴퓨터 다시 시작](../understand/task-sequence-steps.md#BKMK_RestartComputer)을 참조하세요.|  
|디스크 0 파티션 – BIOS:<br /><br /> 디스크 0 파티션 – UEFI:|이러한 단계는 BIOS 또는 UEFI를 사용하여 대상 컴퓨터의 지정된 드라이브를 포맷하고 파티션합니다. 이 작업 순서는 대상 컴퓨터가 UEFI 모드에 있음을 검색하면 UEFI를 사용합니다. 자세한 내용은 [디스크 포맷 및 파티션 만들기](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk)를 참조하세요.|  
|의|이 단계는 Windows PE에서 드라이브에 BitLocker를 사용하도록 설정합니다. 사용되는 드라이브 공간만 암호화됩니다. 위의 단계에서 하드 드라이브를 파티셔닝 및 포맷하므로, 어떤 데이터도 없으며 암호화가 신속하게 완료됩니다. 자세한 내용은 [BitLocker 사전 프로비전](../understand/task-sequence-steps.md#BKMK_PreProvisionBitLocker)을 참조하세요.|  
|운영 체제 적용|이 단계에서는 응답 파일을 준비합니다. 응답 파일은 대상 컴퓨터에 운영 체제를 설치하는 데 사용되며 운영 체제 파일이 포함된 파티션의 드라이브 문자로 OSDTargetSystemDrive 작업 순서 변수를 설정합니다. 응답 파일 및 변수는 Windows 및 ConfigMgr 설치 단계에서 운영 체제를 설치하는 데 사용됩니다. 자세한 내용은 [운영 체제 이미지 적용](../understand/task-sequence-steps.md#BKMK_ApplyOperatingSystemImage)을 참조하세요.|  
|Windows 설정 적용|이 단계에서는 응답 파일에 Windows 설정을 추가합니다. 응답 파일은 Windows 및 ConfigMgr 설치 단계에서 운영 체제를 설치하는 데 사용됩니다. 자세한 내용은 [Windows 설정 적용](../understand/task-sequence-steps.md#BKMK_ApplyWindowsSettings)을 참조하세요.|  
|네트워크 설정 적용|이 단계에서는 응답 파일에 메모장 설정을 추가합니다. 응답 파일은 Windows 및 ConfigMgr 설치 단계에서 운영 체제를 설치하는 데 사용됩니다. 자세한 내용은 [네트워크 설정 단계 적용](../understand/task-sequence-steps.md#BKMK_ApplyNetworkSettings)을 참조하세요.|  
|장치 드라이버 적용|이 단계에서는 운영 체제 배포 중에 드라이버가 일치하는지 확인하고 설치합니다. 자세한 내용은 [드라이버 자동 적용](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers)을 참조하세요.|  
|Windows 및 ConfigMgr 설치|이 단계에서는 Windows PE에서 새 운영 체제로 전환을 수행합니다. 이 작업 순서 단계는 임의의 운영 체제 배포 중 필요합니다. Configuration Manager 클라이언트를 새 운영 체제에 설치하고 새 운영 체제에서 작업 순서를 계속 실행하도록 준비합니다. 자세한 내용은 [Windows 및 ConfigMgr 설정](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr)을 참조하세요.|  
|BitLocker 사용|이 단계에서는 하드 드라이브에서 BitLocker를 사용하도록 설정하고 키 보호기를 설정합니다. 하드 드라이브가 BitLocker로 사전 프로비전되었으므로 이 단계는 신속하게 완료됩니다. Windows 7의 경우에는 키 보호기를 추가해야 합니다. 이 단계를 사용하지 않는 경우 manage-bde.exe 명령줄 도구를 사용하여 키 보호기를 설정할 수 있습니다. 자세한 내용은 [BitLocker 사용](../understand/task-sequence-steps.md#BKMK_EnableBitLocker)을 참조하세요.|  



<!--HONumber=Dec16_HO3-->


