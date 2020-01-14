---
title: '사용자가 온-프레미스 MDM에 디바이스를 등록하는 방법 '
titleSuffix: Configuration Manager
description: 사용자가 Configuration Manager에서 온-프레미스 모바일 장치 관리를 사용 하 여 장치를 등록 하는 방법을 이해 합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6821a439e7ee054216a7ca73be027978ed659ae1
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75826495"
---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-configuration-manager"></a>사용자가 Configuration Manager에서 온-프레미스 모바일 장치 관리를 사용 하 여 장치를 등록 하는 방법

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 모바일 장치 관리를 사용 하면 사용자가 등록 권한이 부여 된 경우 (업데이트 된 클라이언트 설정을 통해) 장치를 등록할 수 있으며, 장치에는 신뢰할 수 있는 필수 루트 인증서가 설치 되어 있습니다. 필요한 사이트 시스템 역할을 호스트 하는 서버와 통신 등록을 설정 하는 방법에 대 한 자세한 내용은 [온-프레미스 모바일 장치 관리를 위한 장치 등록 설정](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)을 참조 하세요.  

> [!NOTE]  
>  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 디바이스에 대한 온-프레미스 모바일 디바이스 관리에서의 등록을 지원합니다.  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team\(Configuration Manager 버전 1602 이상\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

다음 작업에서는 온\-프레미스 모바일 디바이스 관리에 대해 컴퓨터 및 디바이스를 등록하고 등록을 확인하는 방법을 설명합니다.  

-   [Windows 10 컴퓨터 등록](#bkmk_enrollDesk)  

-   [Windows 10 모바일 디바이스 등록](#bkmk_enrollMob)  

-   [디바이스 등록 확인](#bkmk_verify)  

##  <a name="bkmk_enrollDesk"></a> Windows 10 컴퓨터 등록  

1.  Windows 10 컴퓨터에서 **설정**으로 이동합니다.  

2.  **계정**을 클릭하고, **회사 액세스**를 클릭합니다.  

3.  회사 액세스의 **회사 또는 학교에 연결**에서, **연결**을 클릭하고, 업무용 메일 주소를 입력하고 **계속**을 클릭합니다.  

4.  등록 프록시 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 입력하고 **계속**을 클릭합니다.  

5.  서비스에 연결 중에서, 업무용 메일 암호를 입력하고 **로그인**을 클릭합니다.  

6.  로그인 정보를 기억하기 위해 **건너뛰기** 를 클릭하면 잠시 후에 디바이스가 연결됩니다.  

##  <a name="bkmk_enrollMob"></a> Windows 10 모바일 디바이스 등록  

1.  Windows 10 모바일 디바이스에서 **설정**으로 이동합니다.  

2.  **계정**을 클릭하고, **회사 액세스**를 클릭합니다.  

3.  **연결**을 클릭합니다.  

4.  업무용 메일 주소 및 등록 프록시 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 입력합니다. **연결**을 클릭합니다.  

5.  다음 화면에서 업무용 메일 주소 및 암호를 입력한 다음 **로그인**을 클릭합니다. 잠시 후 디바이스가 등록됩니다. **완료**를 클릭합니다.  

##  <a name="bkmk_verify"></a> 디바이스 등록 확인  
 Configuration Manager 콘솔에서 디바이스가 성공적으로 등록되었는지 확인할 수 있습니다.  

1.  Configuration Manager 콘솔을 시작합니다.  

2.  마법사를 종료하려면 **자산 및 준수** > **개요** > **디바이스**에 필요한 사이트 시스템 역할 간의 신뢰할 수 있는 통신에 필요합니다. 등록된 디바이스가 목록에 표시됩니다.  
