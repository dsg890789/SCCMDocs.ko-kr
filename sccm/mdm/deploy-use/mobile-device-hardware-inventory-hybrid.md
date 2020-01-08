---
title: 모바일 디바이스에 대한 하드웨어 인벤토리 구성
titleSuffix: Configuration Manager
description: Microsoft Intune 및 Configuration Manager에서 등록 된 모바일 장치에 대 한 하드웨어 인벤토리를 구성 합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 78a0aecc-f775-451e-aa05-56377ec91b1f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dea53c3d98870d225df860a7b1f2ea7a43741f1
ms.sourcegitcommit: 7f64c5fb3e9fa3dba006af618b1f1ceaf61a99f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75520153"
---
# <a name="how-to-configure-hardware-inventory-for-mobile-devices-enrolled-by-microsoft-intune-and-configuration-manager"></a>Microsoft Intune 및 Configuration Manager에서 등록한 모바일 디바이스의 하드웨어 인벤토리 구성 방법

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager에서 Microsoft Intune 커넥터를 사용하여 iOS, Android 및 Windows 디바이스에 대한 하드웨어 인벤토리를 수집할 수 있습니다. 하드웨어 인벤토리를 구성 하는 방법에 대 한 자세한 내용은 [하드웨어 인벤토리를 확장 하는 방법](../../core/clients/manage/inventory/extend-hardware-inventory.md)을 참조 하세요.  

 Microsoft Intune에 디바이스를 등록하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 모바일 디바이스 관리](https://technet.microsoft.com/library/dn646962.aspx)를 참조하세요.  

## <a name="hardware-inventory-for-mobile-devices"></a>모바일 디바이스에 대한 하드웨어 인벤토리  
 다음 표에는 자주 사용되는 모바일 플랫폼에서 하드웨어 인벤토리의 사용 가능한 인벤토리 클래스가 정리되어 있습니다.  

 **Android**  

|하드웨어 인벤토리 클래스|iOS|  
|------------------------------|---------|  
|이름|Device_ComputerSystem.DeviceName|  
|고유한 디바이스 ID|Device_ComputerSystem.UDID|  
|일련 번호|Device_ComputerSystem.SerialNumber|  
|전자 메일 주소|Device_Email.OwnerEmailAddress|  
|운영 체제 종류|Not applicable|  
|운영 체제 버전|Device_OSInformation.OSVersion|  
|빌드 버전|Not applicable|  
|서비스 팩 주요 버전|Not applicable|  
|서비스 팩 부 버전|Not applicable|  
|운영 체제 언어|Not applicable|  
|총 스토리지 공간|Device_Memory.DeviceCapacity|  
|사용 가능한 스토리지 공간|Device_Memory.AvailableDeviceCapacity|  
|IMEI(International Mobile Equipment Identity)|Device_ComputerSystem.IMEI|  
|MEID(Mobile Equipment Identifier)|Device_ComputerSystem.MEID|  
|제조업체|Not applicable|  
|모델|ModelName|  
|전화번호<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|구독자의 통신사|Device_ComputerSystem.SubscriberCarrierNetwork|  
|셀룰러 기술|Device_ComputerSystem.CellularTechnology|  
|Wi-Fi MAC|Device_WLAN.WiFiMAC|  

 **OWA(Outlook Web Access)**  

> [!NOTE]  
>  **참고:** Android 회사 포털 앱을 사용하는 경우 Android 인벤토리 클래스를 사용할 수 있습니다.  

|하드웨어 인벤토리 클래스|Android|  
|------------------------------|-------------|  
|이름|Not applicable|  
|고유한 디바이스 ID|Not applicable|  
|일련 번호|Device_ComputerSystem.SerialNumber|  
|전자 메일 주소|Not applicable|  
|운영 체제 종류|Device_OSInformation.Platform|  
|운영 체제 버전|Device_OSInformation.Version|  
|빌드 버전|Not applicable|  
|서비스 팩 주요 버전|Not applicable|  
|서비스 팩 부 버전|Not applicable|  
|운영 체제 언어|Not applicable|  
|총 스토리지 공간|Device_Memory.StorageTotal|  
|사용 가능한 스토리지 공간|Device_Memory.StorageFree|  
|IMEI(International Mobile Equipment Identity)|Device_ComputerSystem.IMEI|  
|MEID(Mobile Equipment Identifier)|Not applicable|  
|제조업체|Device_Info.Manufacturer|  
|모델|Device_Info.Model|  
|전화번호<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|구독자의 통신사|Device_ComputerSystem.SubscriberCarrierNetwork|  
|셀룰러 기술|Device_ComputerSystem.CellularTechnology|  
|Wi-Fi MAC|Device_WLAN.WiFiMAC|  

 **Windows Phone 8/8.1**  

|하드웨어 인벤토리 클래스|Windows Phone 8 및 Windows Phone 8.1|  
|------------------------------|-------------------------------------------|  
|이름|Device_ComputerSystem.DeviceName|  
|고유한 디바이스 ID|Device_ComputerSystem.DeviceClientID|  
|일련 번호|Not applicable|  
|전자 메일 주소|Device_Email.OwnerEmailAddress|  
|운영 체제 종류|Device_OSInformation.Platform|  
|운영 체제 버전|Device_ComputerSystem.SoftwareVersion|  
|빌드 버전|Not applicable|  
|서비스 팩 주요 버전|Not applicable|  
|서비스 팩 부 버전|Not applicable|  
|운영 체제 언어|Device_OSInformation.Language|  
|총 스토리지 공간|Not applicable|  
|사용 가능한 스토리지 공간|Not applicable|  
|IMEI(International Mobile Equipment Identity)|Not applicable|  
|MEID(Mobile Equipment Identifier)|Not applicable|  
|제조업체|Device_ComputerSystem.DeviceManufacturer|  
|모델|Device_ComputerSystem.DeviceModel|  
|전화번호<sup>1</sup>|Not applicable|  
|구독자의 통신사|Not applicable|  
|셀룰러 기술|Not applicable|  
|Wi-Fi MAC|Not applicable|  

 **Windows RT**  

|하드웨어 인벤토리 클래스|Windows RT|  
|------------------------------|----------------|  
|이름|Device_ComputerSystem.DeviceName|  
|고유한 디바이스 ID|Device_ComputerSystem.DeviceName|  
|일련 번호|Not applicable|  
|전자 메일 주소|Device_Email.OwnerEmailAddress|  
|운영 체제 종류|CCM_OperatingSystem .SystemType|  
|운영 체제 버전|Win32_OperatingSystem.Version|  
|빌드 버전|Win32_OperatingSystem.BuildNumber|  
|서비스 팩 주요 버전|Win32_OperatingSystem.ServicePackMajorVersion|  
|서비스 팩 부 버전|Win32_OperatingSystem.ServicePackMinorVersion|  
|운영 체제 언어|Not applicable|  
|총 스토리지 공간|Win32_PhysicalMemory.Capacity|  
|사용 가능한 스토리지 공간|Win32_OperatingSystem.FreePhysicalMemory|  
|IMEI(International Mobile Equipment Identity)|Not applicable|  
|MEID(Mobile Equipment Identifier)|Not applicable|  
|제조업체|Win32_ComputerSystem.Manufacturer|  
|모델|Win32_ComputerSystem.Model|  
|전화번호<sup>1</sup>|Not applicable|  
|구독자의 통신사|Not applicable|  
|셀룰러 기술|Not applicable|  
|Wi-Fi MAC|Win32_NetworkAdapter.MACAddress|  

 <sup>1</sup> 전화번호는 마지막 4자리를 제외하고 모두 *로 마스킹됩니다.  

 전화 번호를 수집하는 인벤토리의 경우, 디바이스에 SIM 카드가 삽입되어 있어야 하고 통신 회사에서 해당 SIM에 프로비전한 전화 번호가 있어야 합니다.  
