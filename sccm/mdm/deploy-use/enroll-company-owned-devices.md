---
title: '회사 소유 디바이스 등록 '
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 하이브리드 배포를 위해 회사 소유 디바이스를 등록하는 다양한 방법을 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 454908893cd53abf8b566fe3963f7a3303907a72
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821905"
---
# <a name="enroll-company-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Configuration Manager를 사용하는 하이브리드 배포를 위해 회사 소유 디바이스 등록

*적용 대상: Configuration Manager (현재 분기)*

조직이나 회사 소유 디바이스(COD)를 디바이스 및 구입 방법에 따라 다양한 방법으로 관리할 수 있습니다.  

## <a name="enroll-device-enrollment-program-ios-devices"></a>디바이스 등록 프로그램 iOS 디바이스 등록  
 Apple의 장비 등록 프로그램을 통해 구입한 디바이스에 "무선으로" 등록 프로필을 배포합니다. 사용자가 디바이스에서 설정 도우미를 실행하는 경우 디바이스는 Intune에 등록됩니다.  DEP를 통해 등록된 디바이스는 사용자가 등록을 취소할 수 없습니다. [Configuration Manager를 사용하여 하이브리드 배포를 위해 iOS DEP(디바이스 등록 프로그램) 등록](../../mdm/deploy-use/ios-device-enrollment-program-for-hybrid.md)  

## <a name="enroll-ios-devices-with-apple-configurator"></a>Apple Configurator를 사용한 iOS 디바이스 등록  
 이 메서드는 관리자가 iOS 디바이스를 Apple Configurator를 실행하는 Mac 컴퓨터에 USB로 연결하도록 하여 등록을 미리 구성합니다. 그러면 설정 도우미 프로세스를 실행하는 사용자에게 디바이스를 전달하며 회사 또는 학교 자격 증명을 사용하여 디바이스를 구성하고 등록 프로세스를 완료하게 됩니다. [Configuration Manager와 Apple Configurator를 사용하여 iOS 하이브리드 등록](../../mdm/deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)을 참조하세요.  

## <a name="device-enrollment-manager"></a>디바이스 등록 관리자  
 조직에서는 Intune을 사용하여 디바이스 등록 관리자 계정이라는 단일 사용자 계정으로 많은 수의 모바일 디바이스를 관리할 수 있습니다. 디바이스 등록 관리자 계정을 만든 후 해당 계정을 사용하여 관리자가 일반 사용자에게 기본적으로 허용한 표준 디바이스 5개 이상을 등록할 수 있습니다. 디바이스 등록 관리자로 디바이스를 등록하는 방법은 특정 사용자가 사용하지 않는 디바이스에만 적용됩니다. 이러한 디바이스는 예를 들어 POS(Point-Of-Sale) 또는 유틸리티 앱에는 유용하지만 전자 메일 또는 회사 리소스에 액세스해야 하는 사용자에게는 불편합니다. [Configuration Manager와 디바이스 등록 관리자를 사용하여 디바이스 등록](../../mdm/deploy-use/enroll-devices-with-device-enrollment-manager.md)을 참조하세요.  

## <a name="user-affinity-for-managed-devices"></a>관리 디바이스에 대한 사용자 선호도  
 회사 소유 디바이스의 프로필을 구성할 때 관리자는 디바이스로 특정 사용자를 식별하는 *사용자 선호도*를 관리 디바이스가 지원할지 여부를 지정할 수 있습니다. **사용자 선호도**로 구성한 디바이스에서 회사 포털 앱을 설치하고 실행하여 앱을 다운로드하고 디바이스를 관리할 수 있습니다. [Configuration Manager의 하이브리드 관리 디바이스에 대한 사용자 선호도](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md)를 참조하세요.  

## <a name="manage-devices-with-activation-lock"></a>활성화 잠금을 사용한 디바이스 관리  
 Microsoft Intune에서는 iOS 7.1 이상 디바이스용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금은 디바이스에서 나의 iPhone 찾기 앱을 사용할 때 자동으로 사용하도록 설정됩니다. [Configuration Manager를 사용 하 여 iOS 활성화 잠금 관리](../../mdm/deploy-use/manage-ios-activation-lock.md)를 참조 하세요.

 ## <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>IMEI 또는 iOS 일련 번호로 디바이스 미리 선언

해당 IMEI(International station Mobile Equipment Identity) 번호 또는 iOS 일련 번호를 가져와서 회사 소유의 디바이스를 식별할 수 있습니다. 디바이스 IMEI 번호를 포함한 쉼표로 구분된 값(.csv) 파일을 업로드하거나 디바이스 정보를 수동으로 입력할 수 있습니다.  [하드웨어 ID 번호로 디바이스 미리 선언](../../mdm/deploy-use/predeclare-devices-with-hardware-id.md)을 참조하세요.
